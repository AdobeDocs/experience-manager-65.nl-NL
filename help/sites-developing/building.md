---
title: Tags maken in een AEM toepassing
description: Programmaticaal werken met tags of tags uitbreiden binnen een aangepaste AEM.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
feature: Developing,Tagging
exl-id: d885520d-d0ed-45fa-8511-faa2495d667a
solution: Experience Manager, Experience Manager Sites
role: Developer
source-git-commit: 305227eff3c0d6414a5ae74bcf3a74309dccdd13
workflow-type: tm+mt
source-wordcount: '868'
ht-degree: 0%

---

# Tags maken in een AEM toepassing{#building-tagging-into-an-aem-application}

Voor het programmatisch werken met tags of het uitbreiden van tags binnen een aangepaste AEM toepassing, wordt op deze pagina het gebruik van de optie

* [Tags-API](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/tagging/package-summary.html)

Dat heeft invloed op de

* [Kader voor tags](/help/sites-developing/framework.md)

Zie voor gerelateerde informatie over labelen:

* [Tags beheren](/help/sites-administering/tags.md) voor informatie over het maken en beheren van tags en waarop inhoudstags zijn toegepast.
* [Tags gebruiken](/help/sites-authoring/tags.md) voor informatie over het labelen van inhoud.

## Overzicht van de API voor tags {#overview-of-the-tagging-api}

De uitvoering van de [coderingskader](/help/sites-developing/framework.md) in AEM staat het beheer van tags en tag-inhoud met behulp van de JCR API toe. De tagmanager zorgt ervoor dat tags die als waarden zijn ingevoerd in het dialoogvenster `cq:tags` De eigenschap van de tekenreeksarray wordt niet gedupliceerd. TagID&#39;s die naar niet-bestaande tags verwijzen, worden verwijderd en TagID&#39;s voor verplaatste of samengevoegde tags worden bijgewerkt. TagManager gebruikt een JCR-observatielistener die onjuiste wijzigingen retourneert. De hoofdklassen bevinden zich in de [com.day.cq.tagging](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/index.html?com/day/cq/tagging/package-summary.html) pakket:

* JcrTagManagerFactory - retourneert een op JCR gebaseerde implementatie van een `TagManager`. Dit is de referentie-implementatie van de API voor labelen.
* `TagManager` - Hiermee kunt u tags oplossen en maken op basis van paden en namen.
* `Tag` - definieert het labelobject.

### Een op JCR gebaseerde tagbeheer ophalen {#getting-a-jcr-based-tagmanager}

U moet een JCR hebben om een instantie TagManager op te halen `Session` en te bellen `getTagManager(Session)`:

```java
@Reference
JcrTagManagerFactory jcrTagManagerFactory;

TagManager tagManager = jcrTagManagerFactory.getTagManager(session);
```

In de standaardcontext voor verkopen kunt u zich ook aanpassen aan een `TagManager` van de `ResourceResolver`:

```java
TagManager tagManager = resourceResolver.adaptTo(TagManager.class);
```

### Een tagobject ophalen {#retrieving-a-tag-object}

A `Tag` kan worden opgehaald via de `TagManager`door een bestaande tag op te lossen of een bestaande tag te maken:

```java
Tag tag = tagManager.resolve("my/tag"); // for existing tags

Tag tag = tagManager.createTag("my/tag"); // for new tags
```

Voor de op JCR gebaseerde implementatie, die kaarten `Tags` op JCR `Nodes`, kunt u rechtstreeks gebruikmaken van de `adaptTo` mechanisme als u de bron hebt (bijvoorbeeld `/content/cq:tags/default/my/tag`):

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
>Rechtstreeks aanpassen van `Node` tot `Tag` is niet mogelijk, omdat `Node` implementeert Sling niet `Adaptable.adaptTo(Class)` methode.

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
>De geldige `RangeIterator` te gebruiken is:
>
>`com.day.cq.commons.RangeIterator`

### Tags verwijderen {#deleting-tags}

```java
tagManager.deleteTag(tag);
```

### Codes dupliceren {#replicating-tags}

Het is mogelijk om de replicatiedienst te gebruiken ( `Replicator`) met tags omdat tags van het type zijn `nt:hierarchyNode`:

```java
replicator.replicate(session, replicationActionType, tagPath);
```

## Tags aan de clientzijde {#tagging-on-the-client-side}

De formulierwidget `CQ.tagging.TagInputField` is bestemd voor het invoeren van tags. Deze bevat een pop-upmenu waarin u een keuze kunt maken uit bestaande tags, waaronder automatisch aanvullen en een groot aantal andere functies. Het xtype is `tags`.

## De opschoonfunctie voor tags {#the-tag-garbage-collector}

De opschoonfunctie voor tags is een service op de achtergrond die verborgen en ongebruikte tags opruimt. Verborgen en ongebruikte tags zijn onderliggende codes `/content/cq:tags` die een `cq:movedTo` eigenschap en worden niet gebruikt op een inhoudsknooppunt. Het getal is nul. Door dit lazy schrappingsproces te gebruiken, de inhoudknoop (namelijk `cq:tags` eigenschap) hoeft niet te worden bijgewerkt als onderdeel van de verplaatsings- of samenvoegbewerking. De verwijzingen in de `cq:tags` eigenschap wordt automatisch bijgewerkt wanneer de `cq:tags` Deze eigenschap wordt bijvoorbeeld bijgewerkt via het dialoogvenster Pagina-eigenschappen.

De opschoonfunctie voor tags wordt standaard eenmaal per dag uitgevoerd. U kunt het vormen bij:

```xml
http://localhost:4502/system/console/configMgr/com.day.cq.tagging.impl.TagGarbageCollector
```

## Zoeken naar tags en taglijst {#tag-search-and-tag-listing}

De zoekopdracht naar tags en het tagoverzicht werkt als volgt:

* De zoekopdracht naar TagID zoekt naar de tags met de eigenschap `cq:movedTo` ingesteld op TagID en doorloopt de `cq:movedTo` TagID&#39;s.

* De zoekopdracht naar tagtitel doorzoekt alleen de tags zonder een `cq:movedTo` eigenschap.

## Tags in verschillende talen {#tags-in-different-languages}

Zoals beschreven in de documentatie voor het beheer van tags, in de sectie [Tags beheren in verschillende talen](/help/sites-administering/tags.md#managing-tags-in-different-languages), een tag `title`kunnen in verschillende talen worden gedefinieerd. Vervolgens wordt een taalgevoelige eigenschap toegevoegd aan het tagknooppunt. Deze eigenschap heeft de indeling `jcr:title.<locale>`, bijvoorbeeld `jcr:title.fr` voor de Franse vertaling. De `<locale>` moet een tekenreeks zijn met een kleine ISO-landinstelling en moet &quot;_&quot; in plaats van &quot;-&quot; gebruiken, bijvoorbeeld: `de_ch`.

Wanneer de **Dieren** -tag wordt toegevoegd aan de **Producten** pagina, de waarde `stockphotography:animals` wordt toegevoegd aan de eigenschap `cq:tags` van het knooppunt /content/geometrixx/nl/products/jcr:content. Er wordt naar de vertaling verwezen vanuit het tagknooppunt.

De server-side API heeft gelokaliseerd `title`-gerelateerde methoden:

* [com.day.cq.tagging.Tag](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/index.html?com/day/cq/tagging/Tag.html)

   * getLocalizedTitle(Locale locale)
   * getLocalizedTitlePaths()
   * getLocalizedTitles()
   * getTitle(landinstelling)
   * getTitlePath(landinstelling)

* [com.day.cq.tagging.TagManager](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/index.html?com/day/cq/tagging/TagManager.html)

   * canCreateTagByTitle(String tagTitlePath, landinstelling)
   * createTagByTitle(String tagTitlePath, landinstelling)
   * resolveByTitle(String tagTitlePath, landinstelling)

In AEM kan de taal worden verkregen via de paginataal of via de taal van de gebruiker:

* om de paginataal in JSP terug te winnen:

   * `currentPage.getLanguage(false)`

* om de gebruikerstaal in JSP terug te winnen:

   * `slingRequest.getLocale()`

De `currentPage` en `slingRequest` zijn beschikbaar in een JSP via [&lt;cq:definedobjects>](/help/sites-developing/taglib.md) -tag.

Bij het labelen is lokalisatie afhankelijk van de context als tag `titles`kan worden weergegeven in de paginataal, in de gebruikerstaal of in een andere taal.

### Een nieuwe taal toevoegen aan het dialoogvenster Tag bewerken {#adding-a-new-language-to-the-edit-tag-dialog}

De volgende procedure beschrijft hoe u een taal (Fins) aan de **Tag bewerken** dialoogvenster:

1. In **CRXDE**, bewerkt u de eigenschap voor meerdere waarden `languages` van het knooppunt `/content/cq:tags`.

1. Toevoegen `fi_fi` - die staat voor de Finse landinstelling - en sla de wijzigingen op.

De nieuwe taal (Fins) is nu beschikbaar in het tagdialoogvenster van de pagina-eigenschappen en in het dialoogvenster **Tag bewerken** wanneer u een tag bewerkt in het dialoogvenster **Tags** console.

>[!NOTE]
>
>De nieuwe taal moet een van de AEM erkende talen zijn. Dit wil zeggen dat het bestand beschikbaar moet zijn als een hieronder opgegeven knooppunt `/libs/wcm/core/resources/languages`.

>[!CAUTION]
>
>De taaleigenschap van het deelvenster `/content/cq:tags` node to default. Daarom is het noodzakelijk om het uit de eigenschappen vóór installatie toe te voegen.
