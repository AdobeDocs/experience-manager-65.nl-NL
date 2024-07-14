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

* [ Tagging API ](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/tagging/package-summary.html)

Dat heeft invloed op de

* [Kader voor tags](/help/sites-developing/framework.md)

Zie voor gerelateerde informatie over labelen:

* [ Beherend Markeringen ](/help/sites-administering/tags.md) voor informatie over het creëren van en het leiden van markeringen, en waarop inhoudsmarkeringen zijn toegepast.
* [ Gebruikend Markeringen ](/help/sites-authoring/tags.md) voor informatie over het etiketteren van inhoud.

## Overzicht van de API voor tags {#overview-of-the-tagging-api}

De implementatie van het [ etiketterende kader ](/help/sites-developing/framework.md) in AEM staat beheer van markeringen en markeringsinhoud toe gebruikend JCR API. De TagManager zorgt ervoor dat tags die zijn ingevoerd als waarden voor de eigenschap `cq:tags` string array niet worden gedupliceerd, de tag-id&#39;s die verwijzen naar niet-bestaande tags, worden verwijderd en de tag-id&#39;s voor verplaatste of samengevoegde tags worden bijgewerkt. TagManager gebruikt een JCR-observatielistener die onjuiste wijzigingen retourneert. De belangrijkste klassen zijn in het [ com.day.cq.tagging ](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/index.html?com/day/cq/tagging/package-summary.html) pakket:

* JcrTagManagerFactory - retourneert een op JCR gebaseerde implementatie van een `TagManager` . Dit is de referentie-implementatie van de API voor labelen.
* `TagManager` - Hiermee kunt u tags oplossen en maken op basis van paden en namen.
* `Tag` - definieert het tagobject.

### Een op JCR gebaseerde tagbeheer ophalen {#getting-a-jcr-based-tagmanager}

Als u een instantie TagManager wilt ophalen, moet u een JCR `Session` hebben en `getTagManager(Session)` aanroepen:

```java
@Reference
JcrTagManagerFactory jcrTagManagerFactory;

TagManager tagManager = jcrTagManagerFactory.getTagManager(session);
```

In de typische context van het Verkopen, kunt u aan a `TagManager` van `ResourceResolver` ook aanpassen:

```java
TagManager tagManager = resourceResolver.adaptTo(TagManager.class);
```

### Een tagobject ophalen {#retrieving-a-tag-object}

Een `Tag` kan via `TagManager` worden opgehaald door een bestaande tag op te lossen of een bestaande tag te maken:

```java
Tag tag = tagManager.resolve("my/tag"); // for existing tags

Tag tag = tagManager.createTag("my/tag"); // for new tags
```

Voor de op JCR gebaseerde implementatie, die `Tags` op JCR `Nodes` in kaart brengt, kunt u het mechanisme van `adaptTo` van Sling direct gebruiken als u de bron hebt (bijvoorbeeld, zoals `/content/cq:tags/default/my/tag`):

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
>Rechtstreeks aanpassen van `Node` naar `Tag` is niet mogelijk, omdat `Node` de methode Sling `Adaptable.adaptTo(Class)` niet implementeert.

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
>De geldige `RangeIterator` die moet worden gebruikt is:
>
>`com.day.cq.commons.RangeIterator`

### Tags verwijderen {#deleting-tags}

```java
tagManager.deleteTag(tag);
```

### Codes dupliceren {#replicating-tags}

Het is mogelijk om de replicatieservice ( `Replicator`) met labels te gebruiken omdat de labels van het type `nt:hierarchyNode` zijn:

```java
replicator.replicate(session, replicationActionType, tagPath);
```

## Tags aan de clientzijde {#tagging-on-the-client-side}

De formulierwidget `CQ.tagging.TagInputField` is bestemd voor het invoeren van codes. Deze bevat een pop-upmenu waarin u een keuze kunt maken uit bestaande tags, waaronder automatisch aanvullen en een groot aantal andere functies. Het xtype is `tags` .

## De opschoonfunctie voor tags {#the-tag-garbage-collector}

De opschoonfunctie voor tags is een service op de achtergrond die verborgen en ongebruikte tags opruimt. Verborgen en ongebruikte tags zijn tags onder `/content/cq:tags` die een eigenschap `cq:movedTo` hebben en niet worden gebruikt op een inhoudsknooppunt. Het aantal tags is nul. Door dit luie verwijderingsproces te gebruiken, hoeft het inhoudsknooppunt (de eigenschap `cq:tags` ) niet te worden bijgewerkt als onderdeel van de verplaatsings- of samenvoegbewerking. De verwijzingen in de eigenschap `cq:tags` worden automatisch bijgewerkt wanneer de eigenschap `cq:tags` wordt bijgewerkt, bijvoorbeeld via het dialoogvenster met pagina-eigenschappen.

De opschoonfunctie voor tags wordt standaard eenmaal per dag uitgevoerd. U kunt het vormen bij:

```xml
http://localhost:4502/system/console/configMgr/com.day.cq.tagging.impl.TagGarbageCollector
```

## Zoeken naar tags en taglijst {#tag-search-and-tag-listing}

De zoekopdracht naar tags en het tagoverzicht werkt als volgt:

* De zoekopdracht naar TagID zoekt naar tags waarvoor de eigenschap `cq:movedTo` is ingesteld op TagID en gaat vervolgens door de `cq:movedTo` TagID&#39;s.

* Bij het zoeken naar tagtitel worden alleen de tags doorzocht die geen eigenschap `cq:movedTo` hebben.

## Tags in verschillende talen {#tags-in-different-languages}

Zoals die in de documentatie voor het beheer van markeringen wordt beschreven, in de sectie [ het Leiden Markeringen in Verschillende Talen ](/help/sites-administering/tags.md#managing-tags-in-different-languages), kan een markering `title` in verschillende talen worden bepaald. Vervolgens wordt een taalgevoelige eigenschap toegevoegd aan het tagknooppunt. Deze eigenschap heeft de notatie `jcr:title.<locale>` , bijvoorbeeld `jcr:title.fr` voor de Franse vertaling. De `<locale>` moet een tekenreeks met de landinstelling ISO met kleine letters zijn en &quot;_&quot; gebruiken in plaats van &quot;-&quot;, bijvoorbeeld: `de_ch` .

Wanneer de **Dieren** markering aan de **Producten** pagina wordt toegevoegd, wordt de waarde `stockphotography:animals` toegevoegd aan het bezit `cq:tags` van de knoop /content/geometrixx/en/products/jcr:content. Er wordt naar de vertaling verwezen vanuit het tagknooppunt.

De server-side API heeft gelokaliseerde `title` -gerelateerde methoden:

* [ com.day.cq.tagging.Tag ](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/index.html?com/day/cq/tagging/Tag.html)

   * getLocalizedTitle(Locale locale)
   * getLocalizedTitlePaths()
   * getLocalizedTitles()
   * getTitle(landinstelling)
   * getTitlePath(landinstelling)

* [ com.day.cq.tagging.TagManager ](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/index.html?com/day/cq/tagging/TagManager.html)

   * canCreateTagByTitle(String tagTitlePath, landinstelling)
   * createTagByTitle(String tagTitlePath, landinstelling)
   * resolveByTitle(String tagTitlePath, landinstelling)

In AEM kan de taal worden verkregen via de paginataal of via de taal van de gebruiker:

* om de paginataal in JSP terug te winnen:

   * `currentPage.getLanguage(false)`

* om de gebruikerstaal in JSP terug te winnen:

   * `slingRequest.getLocale()`

`currentPage` en `slingRequest` zijn beschikbaar in JSP door [ &lt;cq:definedObjects> ](/help/sites-developing/taglib.md) markering.

Voor het etiketteren, hangt de localisatie van de context als markering `titles` in de paginataal, in de gebruikerstaal, of in een andere taal kan worden getoond.

### Een nieuwe taal toevoegen aan het dialoogvenster Tag bewerken {#adding-a-new-language-to-the-edit-tag-dialog}

De volgende procedure beschrijft hoe te om een taal (Fins) aan de **markering toe te voegen geeft** dialoog uit:

1. In **CRXDE**, geef het multi-waardebezit `languages` van de knoop `/content/cq:tags` uit.

1. Voeg `fi_fi` toe - die de Finse landinstelling vertegenwoordigt - en sla de wijzigingen op.

De nieuwe taal (Fins) is nu beschikbaar in de markeringsdialoog van de paginaeigenschappen en in **uitgeeft de dialoog van de Markering** wanneer het uitgeven van een markering in de **Tags** console.

>[!NOTE]
>
>De nieuwe taal moet een van de AEM erkende talen zijn. Dit wil zeggen dat de code beschikbaar moet zijn als een knooppunt onder `/libs/wcm/core/resources/languages` .

>[!CAUTION]
>
>Door de codering van inhoud die verwant is aan kant-en-klare inhoud te installeren via een officieel updatepakket (zoals Service Packs, Security Service Packs, Extended Feature Packs, Cumulative Feature Packs, patches en dergelijke), wordt de eigenschap languages van het knooppunt `/content/cq:tags` opnieuw ingesteld op de standaardinstelling. Daarom is het noodzakelijk om het uit de eigenschappen vóór installatie toe te voegen.
