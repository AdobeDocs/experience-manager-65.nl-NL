---
title: Tags maken in een AEM toepassing
seo-title: Tags maken in een AEM toepassing
description: Programmaticaal werken met tags of tags uitbreiden binnen een aangepaste AEM.
seo-description: Programmaticaal werken met tags of tags uitbreiden binnen een aangepaste AEM.
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


# Tags maken in een AEM toepassing{#building-tagging-into-an-aem-application}

Voor het programmatisch werken met tags of het uitbreiden van tags binnen een aangepaste AEM toepassing, wordt op deze pagina het gebruik van de

* [Tags-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/tagging/package-summary.html)

die met de

* [Kader voor tags](/help/sites-developing/framework.md)

Zie voor gerelateerde informatie over labelen:

* [Beheer van ](/help/sites-administering/tags.md) tags voor informatie over het maken en beheren van tags en over de inhoudstags die zijn toegepast.
* [Tags gebruiken ](/help/sites-authoring/tags.md) voor informatie over het labelen van inhoud.

## Overzicht van de API voor labelen {#overview-of-the-tagging-api}

De implementatie van het [tagging framework](/help/sites-developing/framework.md) in AEM maakt het beheer van tags en tag-inhoud met behulp van de JCR API mogelijk. De TagManager zorgt ervoor dat tags die zijn ingevoerd als waarden voor de eigenschap van de `cq:tags`-tekenreeksarray niet worden gedupliceerd. De tagID&#39;s die verwijzen naar niet-bestaande tags, worden verwijderd en de tagID&#39;s voor verplaatste of samengevoegde tags worden bijgewerkt. TagManager gebruikt een JCR-observatielistener die onjuiste wijzigingen retourneert. De hoofdklassen bevinden zich in het [com.day.cq.tagging](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/tagging/package-summary.html) pakket:

* JcrTagManagerFactory - retourneert een op JCR gebaseerde implementatie van een `TagManager`. Dit is de referentie-implementatie van de API voor labelen.
* `TagManager` - Hiermee kunt u tags oplossen en maken op basis van paden en namen.
* `Tag` - definieert het labelobject.

### Een op JCR gebaseerde tagbeheer ophalen {#getting-a-jcr-based-tagmanager}

Om een instantie TagManager terug te winnen, moet u JCR `Session` hebben en `getTagManager(Session)` roepen:

```java
@Reference
JcrTagManagerFactory jcrTagManagerFactory;

TagManager tagManager = jcrTagManagerFactory.getTagManager(session);
```

In de typische het Verkopen context kunt u aan `TagManager` van `ResourceResolver` ook aanpassen:

```java
TagManager tagManager = resourceResolver.adaptTo(TagManager.class);
```

### Een tagobject {#retrieving-a-tag-object} ophalen

Een `Tag` kan door `TagManager` worden teruggewonnen, of het oplossen van een bestaande markering of het creëren van nieuwe:

```java
Tag tag = tagManager.resolve("my/tag"); // for existing tags

Tag tag = tagManager.createTag("my/tag"); // for new tags
```

Voor de op JCR-Gebaseerde implementatie, die `Tags` op JCR `Nodes` in kaart brengt, kunt u het mechanisme van Sling direct gebruiken `adaptTo` als u het middel (b.v. zoals `/content/cq:tags/default/my/tag`) hebt:

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
>Directe aanpassing van `Node` aan `Tag` is niet mogelijk, omdat `Node` de methode Sling `Adaptable.adaptTo(Class)` niet implementeert.

### Labels {#getting-and-setting-tags} ophalen en instellen

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
>De geldige `RangeIterator` is:
>
>`com.day.cq.commons.RangeIterator`

### Labels {#deleting-tags} verwijderen

```java
tagManager.deleteTag(tag);
```

### Codes {#replicating-tags} dupliceren

Het is mogelijk om de replicatieservice ( `Replicator`) met markeringen te gebruiken omdat de markeringen van type `nt:hierarchyNode` zijn:

```java
replicator.replicate(session, replicationActionType, tagPath);
```

## Tags toevoegen aan de clientzijde {#tagging-on-the-client-side}

`CQ.tagging.TagInputField` is een formulierwidget voor het invoeren van codes. Deze bevat een pop-upmenu waarin u een keuze kunt maken uit bestaande tags, waaronder automatisch aanvullen en een groot aantal andere functies. Zijn xtype is `tags`.

## De opschoonfunctie voor tags {#the-tag-garbage-collector}

De opschoonfunctie voor tags is een service op de achtergrond die verborgen en ongebruikte tags opruimt. Verborgen en ongebruikte tags zijn tags onder `/content/cq:tags` die een eigenschap `cq:movedTo` hebben en niet worden gebruikt op een inhoudsknooppunt. Ze hebben een getal van nul. Door dit lazy schrappingsproces te gebruiken, moet de inhoudsknoop (d.w.z. het `cq:tags` bezit) niet als deel van de beweging of de fusieverrichting worden bijgewerkt. De verwijzingen in het `cq:tags` bezit worden automatisch bijgewerkt wanneer `cq:tags` bezit wordt bijgewerkt, bijvoorbeeld door de dialoog van de pagina eigenschappen.

De opschoonfunctie voor tags wordt standaard eenmaal per dag uitgevoerd. Dit kan worden gevormd bij:

```xml
http://localhost:4502/system/console/configMgr/com.day.cq.tagging.impl.TagGarbageCollector
```

## Tag zoeken en taglijst {#tag-search-and-tag-listing}

De zoekopdracht naar tags en het tagoverzicht werkt als volgt:

* De zoekopdracht naar TagID zoekt naar de tags waarvan de eigenschap `cq:movedTo` is ingesteld op TagID en doorloopt de tag-id&#39;s `cq:movedTo`.

* Bij het zoeken naar tagtitel worden alleen de tags doorzocht die geen eigenschap `cq:movedTo` hebben.

## Tags in verschillende talen {#tags-in-different-languages}

Zoals beschreven in de documentatie voor het beheer van labels, kunt u in de sectie [Tags beheren in verschillende talen](/help/sites-administering/tags.md#managing-tags-in-different-languages) een tag `title`definiëren in verschillende talen. Vervolgens wordt een taalgevoelige eigenschap toegevoegd aan het tagknooppunt. Deze eigenschap heeft de notatie `jcr:title.<locale>`, bijvoorbeeld `jcr:title.fr` voor de Franse vertaling. `<locale>` moet een tekenreeks zijn met een kleine ISO-landinstelling en moet &quot;_&quot; in plaats van &quot;-&quot; gebruiken, bijvoorbeeld:  `de_ch`.

Wanneer de tag **Dieren** wordt toegevoegd aan de pagina **Producten**, wordt de waarde `stockphotography:animals` toegevoegd aan de eigenschap `cq:tags` van het knooppunt /content/geometrixx/en/products/jcr:content. Er wordt naar de vertaling verwezen vanuit het tagknooppunt.

De server-side API heeft gelokaliseerde `title` verwante methodes:

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

In AEM kan de taal worden verkregen via de paginataal of via de taal van de gebruiker:

* om de paginataal in JSP terug te winnen:

   * `currentPage.getLanguage(false)`

* om de gebruikerstaal in JSP terug te winnen:

   * `slingRequest.getLocale()`

`currentPage` en  `slingRequest` zijn beschikbaar in een JSP via de  [&lt;cq:definedobjects>](/help/sites-developing/taglib.md) tag.

Bij het labelen hangt de lokalisatie af van de context, aangezien tag `titles`kan worden weergegeven in de paginataal, in de gebruikerstaal of in een andere taal.

### Een nieuwe taal toevoegen aan het dialoogvenster Tag bewerken {#adding-a-new-language-to-the-edit-tag-dialog}

In de volgende procedure wordt beschreven hoe u een nieuwe taal (Fins) kunt toevoegen aan het dialoogvenster **Tag Edit**:

1. Bewerk in **CRXDE** de eigenschap multi-value `languages` van het knooppunt `/content/cq:tags`.

1. Voeg `fi_fi` - die de Finse scène vertegenwoordigt - toe en sla de veranderingen op.

De nieuwe taal (Fins) is nu beschikbaar in het tagdialoogvenster van de pagina-eigenschappen en in het dialoogvenster **Tag bewerken** wanneer u een tag bewerkt in de console **Tags toevoegen**.

>[!NOTE]
>
>De nieuwe taal moet een van de AEM erkende talen zijn, d.w.z. het moet beschikbaar zijn als een knooppunt onder `/libs/wcm/core/resources/languages`.

