---
title: Essentiële zoekopdrachten
description: Meer weten over de zoekfunctie die essentieel is voor AEM Communities? De gemeenschappen verstrekken ook onderzoek API voor gebruiker-geproduceerde inhoud.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 8af5ee58-19d7-47b6-b45d-e88006703a5d
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1158'
ht-degree: 0%

---

# Essentiële zoekopdrachten {#search-essentials}

## Overzicht {#overview}

De zoekfunctie is een essentieel onderdeel van de AEM van Adobe Experience Manager. Naast [ AEM platformonderzoek ](../../help/sites-deploying/queries-and-indexing.md) mogelijkheden, verstrekt AEM Communities [ het onderzoekAPI van UGC ](#ugc-search-api) voor het zoeken van user-generated inhoud (UGC). UGC heeft unieke eigenschappen omdat deze afzonderlijk van andere AEM inhoud en gebruikersgegevens wordt ingevoerd en opgeslagen.

Voor de Gemeenschappen zijn de twee dingen die over het algemeen worden doorzocht:

* Inhoud geplaatst door leden van de gemeenschap

   * Er wordt gebruikgemaakt van de UGC-zoekAPI van AEM Communities.

* Gebruikers en gebruikersgroepen (gebruikersgegevens)

   * Er worden zoekmogelijkheden voor AEM platform gebruikt.

Deze sectie van de documentatie is van belang voor ontwikkelaars die douanecomponenten creëren die tot UGC leiden of leiden.

## Beveiligings- en schaduwknooppunten {#security-and-shadow-nodes}

Voor een douanecomponent, is het noodzakelijk om [ te gebruiken SocialResourceUtilities ](socialutils.md#socialresourceutilities-package) methodes. De nutsmethodes die tot stand brengen en naar UGC zoeken vestigen de vereiste [ schaduwknopen ](srp.md#about-shadow-nodes-in-jcr) en zorgen ervoor dat het lid de correcte toestemmingen voor het verzoek heeft.

Wat niet door de nut SRP wordt beheerd zijn eigenschappen met betrekking tot matiging.

Zie [ Hoofdzaak SRP en UGC ](srp-and-ugc.md) voor informatie betreffende nutsmethodes die worden gebruikt om tot UGC en ACL schaduwknopen toegang te hebben.

## UGC-zoekAPI {#ugc-search-api}

De [ gemeenschappelijke opslag UGC ](working-with-srp.md) wordt verstrekt door één van diverse leveranciers van het opslagmiddel (SRPs), elk misschien hebbend een verschillende inheemse vraagtaal. Daarom ongeacht SRP gekozen, zou de douanecode methodes van het [ UGC API pakket ](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/ugc/api/package-summary.html) (*com.adobe.cq.social.ugc.api*) moeten gebruiken die de vraagtaal aangewezen voor gekozen SRP aanhaalt.

### ASRP-zoekopdrachten {#asrp-searches}

Voor [ ASRP ](asrp.md), wordt UGC opgeslagen in de wolk van de Adobe. Terwijl UGC niet zichtbaar in CRX is, [ matiging ](moderate-ugc.md) is beschikbaar bij zowel de auteur als de milieu&#39;s van Publish. Het gebruik van het [ UGC onderzoek API ](#ugc-search-api) werkt voor ASRP het zelfde als voor andere SRPs.

De hulpmiddelen bestaan momenteel niet voor het beheren van de onderzoeken van ASRP.

Wanneer het creëren van douaneeigenschappen die doorzoekbaar zijn, is het noodzakelijk om aan [ het noemen vereisten ](#naming-of-custom-properties) te houden.

### MSRP-zoekopdrachten {#msrp-searches}

Voor [ MSRP ](msrp.md), wordt UGC opgeslagen in MongoDB die wordt gevormd om Solr voor het zoeken te gebruiken. UGC is niet zichtbaar in CRX, maar [ de matiging ](moderate-ugc.md) is beschikbaar bij zowel de auteur als de milieu&#39;s van Publish.

Wat MSRP en Solr betreft:

* Ingesloten Solr voor het AEM platform wordt niet gebruikt voor MSRP.
* Als het gebruiken van verre Solr voor het AEM platform, kan het met MSRP worden gedeeld, maar zij zouden verschillende inzamelingen moeten gebruiken.
* Solr kan voor standaardonderzoek of voor meertalige onderzoek (MLS) worden gevormd.
* Voor configuratiedetails, zie ](msrp.md#solr-configuration) Configuratie 0} Solr voor MSRP.[

De het onderzoekseigenschappen van de douane zouden het [ UGC onderzoek API ](#ugc-search-api) moeten gebruiken.

Wanneer het creëren van douaneeigenschappen die doorzoekbaar zijn, is het noodzakelijk om aan [ het noemen vereisten ](#naming-of-custom-properties) te houden.

### JSRP-zoekopdrachten {#jsrp-searches}

Voor [ JSRP ](jsrp.md), wordt UGC opgeslagen in [ Oak ](../../help/sites-deploying/platform.md) en is zichtbaar slechts in de bewaarplaats van de AEM Author of de instantie van Publish waarop het was ingegaan.

Aangezien UGC typisch in het milieu van Publish, voor multi-uitgeversproductiesystemen is ingegaan, is het noodzakelijk om a [ te vormen publiceer cluster ](topologies.md), niet publiceer landbouwbedrijf, zodat de ingegane inhoud van alle uitgevers zichtbaar is.

Voor JSRP is UGC die in de Publish-omgeving wordt ingevoerd, nooit zichtbaar in de auteursomgeving. Daarom vinden alle [ matigings ](moderate-ugc.md) taken plaats in het milieu van Publish.

De het onderzoekseigenschappen van de douane zouden het [ UGC onderzoek API ](#ugc-search-api) moeten gebruiken.

#### Oak-indexering {#oak-indexing}

Hoewel Oak-indexen niet automatisch worden gemaakt voor het zoeken naar AEM platform, zijn ze vanaf AEM 6.2 toegevoegd voor AEM Communities om de prestaties te verbeteren en paginering te ondersteunen bij het weergeven van UGC-zoekresultaten.

Als aangepaste eigenschappen in gebruik zijn en zoekacties traag zijn, moeten aanvullende indexen worden gemaakt om de aangepaste eigenschappen beter te laten presteren. Om portabiliteit te handhaven, houd aan [ het noemen vereisten ](#naming-of-custom-properties) wanneer het creëren van douaneeigenschappen die doorzoekbaar zijn.

Om bestaande indexen te wijzigen of douaneindexen tot stand te brengen, zie [ Vragen van Oak en het Indexeren ](../../help/sites-deploying/queries-and-indexing.md).

De [ Manager van de Index van Oak ](https://adobe-consulting-services.github.io/acs-aem-commons/features/oak-index-manager.html) is beschikbaar bij ACS AEM Commons. Het voorziet in:

* Een weergave van bestaande indexen.
* De mogelijkheid om opnieuw indexeren te starten.

Om de bestaande indexen van Oak in [ CRXDE Lite ](../../help/sites-developing/developing-with-crxde-lite.md) te bekijken, is de plaats:

* `/oak:index/socialLucene`

![ sociaal-lucene ](assets/social-lucene.png)

## Eigenschappen van Geïndexeerde zoekopdracht {#indexed-search-properties}

### Standaardeigenschappen voor zoeken {#default-search-properties}

Hieronder volgt een aantal van de doorzoekbare eigenschappen die worden gebruikt voor verschillende functies van de Gemeenschappen:

| **Bezit** | **Type van Gegevens** |
|---|---|
| isFlagged | *Van Boole* |
| isSpam | *Van Boole* |
| lezen | *Van Boole* |
| invloed | *Van Boole* |
| bijlagen | *Van Boole* |
| sentiment | *Lang* |
| gemarkeerd | *Van Boole* |
| added | *Datum* |
| modifiedDate | *Datum* |
| state | *Koord* |
| userIdentifier | *Koord* |
| antwoorden | *Lang* |
| jcr:titel | *Koord* |
| jcr:beschrijving | *Koord* |
| sling:resourceType | *Koord* |
| allowThreadedReply | *Van Boole* |
| isDraft | *Van Boole* |
| publishDate | *Datum* |
| publishJobId | *Koord* |
| beantwoord | *Van Boole* |
| chosenanswer | *Van Boole* |
| tag | *Koord* |
| cq:Tag | *Koord* |
| maker_display_name | *Koord* |
| location_t | *Koord* |
| parentPath | *Koord* |
| parentTitle | *Koord* |

### Naamgeving van aangepaste eigenschappen {#naming-of-custom-properties}

Wanneer het toevoegen van douaneeigenschappen, voor die eigenschappen zichtbaar zijn om te sorteren en onderzoeken die met het [ UGC onderzoek API ](#ugc-search-api) worden gecreeerd, wordt het *vereist* om een achtervoegsel aan de bezitsnaam toe te voegen.

Het achtervoegsel is voor vraagtalen die een schema gebruiken:

* Het identificeert de eigenschap als doorzoekbaar.
* Het identificeert het gegevenstype.

Solr is een voorbeeld van een vraagtaal die een schema gebruikt.

| **Achtervoegsel** | **Type van Gegevens** |
|---|---|
| _b | *Van Boole* |
| _dt | *Kalender* |
| _d | *tweemaal* |
| _tl | *Lang* |
| _s | *Koord* |
| _t | *Tekst* |

**Nota&#39;s:**

* *Tekst* is een samengevat koord, *Koord* is niet. Het gebruik *Tekst* voor vage (meer als dit) onderzoeken.

* Voeg voor typen met meerdere waarden &#39;s&#39; toe aan het achtervoegsel, bijvoorbeeld:

   * `viewDate_dt`: eigenschap single date
   * `viewDates_dts`: list of dates, eigenschap

## Filters {#filters}

De componenten, die het [ commentaarsysteem ](essentials-comments.md) omvatten, steunen de filterparameter naast hun eindpunten.

De filtersyntaxis voor AND en OR logica wordt als volgt uitgedrukt (getoond alvorens URL wordt gecodeerd):

* U kunt als volgt één filterparam met door komma&#39;s gescheiden waarden opgeven of gebruiken:

   * `filter=name eq 'Jennifer',name eq 'Jen'`

* Meerdere filterparams opgeven EN gebruiken:

   * `filter = name eq 'Jackson'&filter=message eq 'testing'`

De standaardimplementatie van de [ component van het Onderzoek ](search.md) gebruikt deze syntaxis zoals in URL kan worden gezien die de pagina van de Resultaten van het Onderzoek in de [ Communautaire gids van Componenten ](components-guide.md) opent. Om te experimenteren, doorblader aan [ http://localhost:4503/content/community-components/en/search.html ](http://localhost:4503/content/community-components/en/search.html).

Filteroperatoren zijn:

| EQ | equals |
|---|---|
| NE | niet gelijk aan |
| LT | minder dan |
| LTE | kleiner dan of gelijk aan |
| GE | groter dan |
| GTE | groter dan of gelijk aan |
| LIKE | vage match |

Het is belangrijk dat de URL verwijst naar de communautaire component (bron) en niet naar de pagina waarop de component is geplaatst:

* Correct: forumcomponent
   * `/content/community-components/en/forum/jcr:content/content/forum.social.json`
* Onjuist: forumpagina
   * `/content/community-components/en/forum.social.json`

## SRP {#srp-tools}

Er is een project Adobe Experience Cloud GitHub dat bevat:

[ AEM Communities SRP Hulpmiddelen ](https://github.com/Adobe-Marketing-Cloud/aem-communities-srp-tools)

Deze opslagplaats bevat hulpmiddelen voor het beheren van gegevens in SRP.

Momenteel, is er één servlet die al UGC van om het even welk SRP kan schrappen.

Bijvoorbeeld, om al UGC in ASRP te schrappen:

```shell
curl -X POST http://localhost:4502/services/social/srp/cleanup?path=/content/usergenerated/asi/cloud -uadmin:admin
```

## Problemen oplossen {#troubleshooting}

### Solr-query {#solr-query}

Om problemen met een Solr vraag problemen op te lossen, laat het registreren DEBUG voor toe

`com.adobe.cq.social.srp.impl.SocialSolrConnector`.

De daadwerkelijke Solr vraag wordt getoond URL die in zuivert logboek wordt gecodeerd:

Op te slaan query is: `sort=timestamp+desc&bl=en&pl=en&start=0&rows=10 &q=%2Btitle_t:(hello)+%2Bprovider_id:\/content/usergenerated/asi/mongo/content/+%2Bresource_type_s:&df=provider_id&trf=verbatim&fq={!cost%3D100}report_suite:mongo`

De waarde van de parameter `q` is de query. Zodra het coderen URL wordt gedecodeerd, kan de vraag tot het Solr hulpmiddel van de Vraag Admin voor verdere het zuiveren worden overgegaan.

## Gerelateerde bronnen {#related-resources}

* [ Communautaire Opslag van de Inhoud ](working-with-srp.md) - Bespreekt de beschikbare keuzen SRP voor een gemeenschappelijke opslag UGC.
* [ Overzicht van de Leverancier van het Middel van de Opslag ](srp.md) - Inleiding en overzicht van het opslagruimtegebruik.
* [ die tot UGC met SRP ](accessing-ugc-with-srp.md) toegang hebben - de richtlijnen van de Codering.
* [ SocialUtils Refactoring ](socialutils.md) - de methodes van het Nut voor SRP die SocialeUtils vervangen.
* [ Onderzoek en de componenten van Resultaten van het Onderzoek ](search.md) - Toevoegend UGC onderzoekseigenschap aan een malplaatje.
