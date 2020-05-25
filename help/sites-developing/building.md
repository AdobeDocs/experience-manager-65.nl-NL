---
title: Tags maken in een AEM-toepassing
seo-title: Tags maken in een AEM-toepassing
description: Programmaticaal werken met tags of tags uitbreiden binnen een aangepaste AEM-toepassing
seo-description: Programmaticaal werken met tags of tags uitbreiden binnen een aangepaste AEM-toepassing
uuid: 0549552e-0d51-4162-b418-babf4ceee046
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: 032aea1f-0105-4299-8d32-ba6bee78437f
translation-type: tm+mt
source-git-commit: 1493b301ecf4c25f785495e11ead352de600ddb7
workflow-type: tm+mt
source-wordcount: '893'
ht-degree: 0%

---


# Tags maken in een AEM-toepassing{#building-tagging-into-an-aem-application}

Voor programmatisch werken met tags of het uitbreiden van tags binnen een aangepaste AEM-toepassing, wordt op deze pagina het gebruik van de

* [Tags-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/tagging/package-summary.html)

die met de

* [Kader voor tags](/help/sites-developing/framework.md)

Zie voor gerelateerde informatie over labelen:

* [Tags](/help/sites-administering/tags.md) beheren voor informatie over het maken en beheren van tags en over de inhoudstags die zijn toegepast.
* [Tags](/help/sites-authoring/tags.md) gebruiken voor informatie over het labelen van inhoud.

## Overzicht van de API voor tags {#overview-of-the-tagging-api}

Met de implementatie van het [coderingsframework](/help/sites-developing/framework.md) in AEM kunt u tags en code-inhoud beheren met behulp van de JCR API. De TagManager zorgt ervoor dat tags die zijn ingevoerd als waarden voor de eigenschap `cq:tags` string array, niet worden gedupliceerd, de tag-id&#39;s die verwijzen naar niet-bestaande tags, worden verwijderd en de tag-id&#39;s voor verplaatste of samengevoegde tags worden bijgewerkt. TagManager gebruikt een JCR-observatielistener die onjuiste wijzigingen retourneert. De belangrijkste klassen bevinden zich in het [com.day.cq.tagging](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/tagging/package-summary.html) pakket:

* JcrTagManagerFactory - retourneert een op JCR gebaseerde implementatie van een `TagManager`. Dit is de referentie-implementatie van de API voor labelen.
* `TagManager` - Hiermee kunt u tags oplossen en maken op basis van paden en namen.
* `Tag` - definieert het labelobject.

### Een op JCR gebaseerde tagbeheer ophalen {#getting-a-jcr-based-tagmanager}

Om een instantie TagManager terug te winnen, moet u JCR hebben `Session` en roepen `getTagManager(Session)`:

```java
@Reference
JcrTagManagerFactory jcrTagManagerFactory;

TagManager tagManager = jcrTagManagerFactory.getTagManager(session);
```

In de typische context van het Verkopen kunt u zich aan een `TagManager` van `ResourceResolver`:

```java
TagManager tagManager = resourceResolver.adaptTo(TagManager.class);
```

### Een tagobject ophalen {#retrieving-a-tag-object}

U `Tag` kunt een bestaande tag opvragen `TagManager`door een nieuwe tag te maken:

```java
Tag tag = tagManager.resolve("my/tag"); // for existing tags

Tag tag = tagManager.createTag("my/tag"); // for new tags
```

Voor de op JCR-Gebaseerde implementatie, die kaarten `Tags` op JCR `Nodes`, kunt u het `adaptTo` mechanisme van Sling direct gebruiken als u het middel (b.v. `/content/cq:tags/default/my/tag`) hebt:

```java
Tag tag = resource.adaptTo(Tag.class);
```

Terwijl een markering slechts *from *a middel (geen knoop) mag worden omgezet, kan een markering *to *both een knoop en een middel worden omgezet:

```java
Node node = tag.adaptTo(Node.class);
Resource node = tag.adaptTo(Resource.class);
```

>[!NOTE]
>
>Directe aanpassing van `Node` aan `Tag` is niet mogelijk, omdat `Node` de methode Sling niet wordt geïmplementeerd `Adaptable.adaptTo(Class)` .

### Labels ophalen en instellen {#getting-and-setting-tags}

```java
// Getting the tags of a Resource:
Tag[] tags = tagManager.getTags(resource);

// Setting tags to a Resource:
tagManager.setTags(resource, tags);
```

### Zoeken naar tags {#searching-for-tags}

```java
// Searching for the Resource objects that are tagged with the tag object:
Iterator<Resource> it = tag.find();

// Retrieving the usage count of the tag object:
long count = tag.getCount();

// Searching for the Resource objects that are tagged with the tagID String:
 RangeIterator<Resource> it = tagManager.find(tagID);
```

>[!NOTE]
>
>De geldige waarden `RangeIterator` zijn:
>
>`com.day.cq.commons.RangeIterator`

### Tags verwijderen {#deleting-tags}

```java
tagManager.deleteTag(tag);
```

### Codes dupliceren {#replicating-tags}

Het is mogelijk om de replicatieservice ( `Replicator`) met markeringen te gebruiken omdat de markeringen van type zijn `nt:hierarchyNode`:

```java
replicator.replicate(session, replicationActionType, tagPath);
```

## Tags aan de clientzijde {#tagging-on-the-client-side}

`CQ.tagging.TagInputField` is een formulierwidget voor het invoeren van codes. Deze bevat een pop-upmenu waarin u een keuze kunt maken uit bestaande tags, waaronder automatisch aanvullen en een groot aantal andere functies. Zijn xtype is `tags`.

## De opschoonfunctie voor tags {#the-tag-garbage-collector}

De opschoonfunctie voor tags is een service op de achtergrond die verborgen en ongebruikte tags opruimt. Verborgen en ongebruikte tags zijn onderliggende tags `/content/cq:tags` die een `cq:movedTo` eigenschap hebben en niet worden gebruikt op een inhoudsknooppunt. Het aantal is nul. Door dit lazy schrappingsproces te gebruiken, moet de inhoudsknoop (d.w.z. het `cq:tags` bezit) niet als deel van de beweging of de fusieverrichting worden bijgewerkt. De verwijzingen in het `cq:tags` bezit worden automatisch bijgewerkt wanneer het `cq:tags` bezit wordt bijgewerkt, bijvoorbeeld door de dialoog van de pagina eigenschappen.

De opschoonfunctie voor tags wordt standaard eenmaal per dag uitgevoerd. Dit kan worden gevormd bij:

```xml
http://localhost:4502/system/console/configMgr/com.day.cq.tagging.impl.TagGarbageCollector
```

## Zoeken en taglijst {#tag-search-and-tag-listing}

De zoekopdracht naar tags en het tagoverzicht werkt als volgt:

* De zoekopdracht naar TagID zoekt naar de tags waarvoor de eigenschap is `cq:movedTo` ingesteld op TagID en doorloopt de `cq:movedTo` tagID&#39;s.

* De zoekopdracht naar tagtitel doorzoekt alleen de tags zonder `cq:movedTo` eigenschap.

## Tags in verschillende talen {#tags-in-different-languages}

Zoals beschreven in de documentatie voor het beheer van labels, [kunt u in de sectie Tags](/help/sites-administering/tags.md#managing-tags-in-different-languages)beheren in verschillende talen `title`een tag definiëren in verschillende talen. Vervolgens wordt een taalgevoelige eigenschap toegevoegd aan het tagknooppunt. Deze eigenschap heeft de indeling `jcr:title.<locale>`, bijvoorbeeld `jcr:title.fr` voor de Franse vertaling. `<locale>` moet een tekenreeks zijn met een kleine ISO-landinstelling en moet &quot;_&quot; in plaats van &quot;-&quot; gebruiken, bijvoorbeeld: `de_ch`.

Wanneer de tag **Dieren** wordt toegevoegd aan de pagina **Producten** , `stockphotography:animals` wordt de waarde toegevoegd aan de eigenschap `cq:tags` van het knooppunt /content/geometrixx/nl/products/jcr:content. Er wordt naar de vertaling verwezen vanuit het tagknooppunt.

De server-side API heeft gelokaliseerde `title`gerelateerde methoden:

* [com.day.cq.tagging.Tag](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/tagging/Tag.html)

   * getLocalizedTitle(Locale locale)
   * getLocalizedTitlePaths()
   * getLocalizedTitles()
   * getTitle(landinstelling van landinstelling)
   * getTitlePath(landinstelling)

* [com.day.cq.tagging.TagManager](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/tagging/TagManager.html)

   * canCreateTagByTitle(String tagTitlePath, landinstelling)
   * createTagByTitle(String tagTitlePath, landinstelling)
   * resolveByTitle(String tagTitlePath, landinstelling)

In AEM, kan de taal of van de paginaal worden verkregen of:

* om de paginataal in JSP terug te winnen:

   * `currentPage.getLanguage(false)`

* om de gebruikerstaal in JSP terug te winnen:

   * `slingRequest.getLocale()`

`currentPage` en `slingRequest` zijn beschikbaar in een JSP via de tag [&lt;cq:definedObjects>](/help/sites-developing/taglib.md) .

Bij het labelen hangt de lokalisatie af van de context, aangezien de tag `titles`kan worden weergegeven in de paginataal, in de gebruikerstaal of in een andere taal.

### Een nieuwe taal toevoegen aan het dialoogvenster Tag bewerken {#adding-a-new-language-to-the-edit-tag-dialog}

In de volgende procedure wordt beschreven hoe u een nieuwe taal (Fins) kunt toevoegen aan het dialoogvenster **Tags bewerken** :

1. Bewerk in **CRXDE** de eigenschap voor meerdere waarden `languages` van het knooppunt `/content/cq:tags`.

1. Voeg toe `fi_fi` - die de Finse landinstelling vertegenwoordigt - en sla de wijzigingen op.

De nieuwe taal (Fins) is nu beschikbaar in het tagdialoogvenster van de pagina-eigenschappen en in het dialoogvenster Tag **** bewerken wanneer u een tag bewerkt in de **tagconsole** .

>[!NOTE]
>
>De nieuwe taal moet een van de erkende talen van AEM zijn, d.w.z. het moet beschikbaar zijn als hieronder knooppunt `/libs/wcm/core/resources/languages`.

