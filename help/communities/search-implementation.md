---
title: Essentiële zoekopdrachten
seo-title: Essentiële zoekopdrachten
description: Zoeken in gemeenschappen
seo-description: Zoeken in gemeenschappen
uuid: 5f35a033-2069-499e-9cdb-db25781312f0
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 300aa9f3-596f-42bc-8d46-e535f2bc4379
translation-type: tm+mt
source-git-commit: 9a4ae73c08657195da2741cccdb196bd7f7142c9
workflow-type: tm+mt
source-wordcount: '1189'
ht-degree: 3%

---


# Essentiële elementen zoeken {#search-essentials}

## Overzicht {#overview}

De zoekfunctie is een essentieel onderdeel van AEM Communities. Naast de mogelijkheden van [AEM platform search](../../help/sites-deploying/queries-and-indexing.md) biedt AEM Communities de [UGC search API](#ugc-search-api) voor het zoeken naar door de gebruiker gegenereerde inhoud (UGC). UGC heeft unieke eigenschappen omdat deze afzonderlijk van andere AEM inhoud en gebruikersgegevens wordt ingevoerd en opgeslagen.

Voor Gemeenschappen zijn de twee dingen die over het algemeen worden doorzocht:

* Inhoud geplaatst door leden van de gemeenschap

   * Gebruikt de UGC-zoekAPI van AEM-gemeenschappen.

* Gebruikers en gebruikersgroepen (gebruikersgegevens)

   * Gebruikt de zoekmogelijkheden van het AEM platform.

Deze sectie van de documentatie is van belang voor ontwikkelaars die douanecomponenten creëren die tot UGC leiden of leiden.

## Beveiligings- en schaduwknooppunten {#security-and-shadow-nodes}

Voor een douanecomponent, is het noodzakelijk om [SocialResourceUtilities](socialutils.md#socialresourceutilities-package) methodes te gebruiken. De hulpprogrammamethoden die tot UGC leiden en naar UGC zoeken zullen de vereiste [schaduwknopen](srp.md#about-shadow-nodes-in-jcr) vestigen en verzekeren het lid de correcte toestemmingen voor het verzoek heeft.

Wat niet door de nut SRP wordt beheerd zijn eigenschappen met betrekking tot matiging.

Zie [SRP en de Hoofdzaak UGC](srp-and-ugc.md) voor informatie betreffende nutsmethodes die worden gebruikt om tot UGC en ACL schaduwknopen toegang te hebben.

## UGC-zoekAPI {#ugc-search-api}

[UGC gemeenschappelijk store](working-with-srp.md) wordt verstrekt door één van een verscheidenheid van leveranciers van opslagmiddelen (SRPs), elk misschien verschillend van een verschillende inheemse vraagtaal. Daarom zou de douanecode, ongeacht SRP gekozen, methodes van [UGC API pakket](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/ugc/api/package-summary.html) (*com.adobe.cq.social.ugc.api*) moeten gebruiken die de vraagtaal aangewezen voor gekozen SRP zal aanhalen.

### ASRP-zoekopdrachten {#asrp-searches}

Voor [ASRP](asrp.md), wordt UGC opgeslagen in de wolk van Adobe. Hoewel UGC niet zichtbaar is in CRX, is [moderation](moderate-ugc.md) beschikbaar bij zowel de auteur als de publicatiemilieu&#39;s. Het gebruik van [UGC onderzoek API](#ugc-search-api) werkt voor ASRP het zelfde als voor andere SRPs.

De hulpmiddelen bestaan momenteel niet voor het beheren van de onderzoeken van ASRP.

Wanneer u aangepaste eigenschappen maakt die doorzoekbaar zijn, moet u de [naamgevingsvereisten](#naming-of-custom-properties) in acht nemen.

### MSRP Zoekopdrachten {#msrp-searches}

Voor [MSRP](msrp.md), wordt UGC opgeslagen in MongoDB die wordt gevormd om Solr voor het zoeken te gebruiken. UGC is niet zichtbaar in CRX, maar [moderatie](moderate-ugc.md) is beschikbaar in zowel auteur als publicatiemilieu&#39;s.

Wat MSRP en Solr betreft:

* Ingesloten Solr voor het AEM platform wordt niet gebruikt voor MSRP.
* Als het gebruiken van verre Solr voor het AEM platform, kan het met MSRP worden gedeeld, maar zij zouden verschillende inzamelingen moeten gebruiken.
* Solr kan voor standaardonderzoek of voor meertalige onderzoek (MLS) worden gevormd.
* Voor configuratiedetails, zie [Solr Configuratie](msrp.md#solr-configuration) voor MSRP.

Voor aangepaste zoekfuncties moet u de [UGC-zoekAPI](#ugc-search-api) gebruiken.

Wanneer u aangepaste eigenschappen maakt die doorzoekbaar zijn, moet u de [naamgevingsvereisten](#naming-of-custom-properties) in acht nemen.

### JSRP-zoekopdrachten {#jsrp-searches}

Voor [JSRP](jsrp.md), wordt UGC opgeslagen in [Oak](../../help/sites-deploying/platform.md) en is zichtbaar slechts in de bewaarplaats van de AEM auteur of publicatieinstantie waarop het werd ingegaan.

Aangezien UGC typisch in het publicatiemilieu, voor multi-uitgeversproductiesystemen is ingegaan, is het noodzakelijk om [te vormen publicatiecluster](topologies.md), niet publicatielandbouwbedrijf, zodat de ingegane inhoud van alle uitgevers zichtbaar is.

Voor JSRP, zal UGC ingegaan in het publicatiemilieu nooit in het auteursmilieu zichtbaar zijn. Alle [moderatie](moderate-ugc.md)-taken worden dus uitgevoerd in de publicatieomgeving.

Voor aangepaste zoekfuncties moet u de [UGC-zoekAPI](#ugc-search-api) gebruiken.

#### Oak-indexering {#oak-indexing}

Terwijl de indexen van het Eak niet automatisch voor het AEM platformonderzoek worden gecreeerd, zijn zij met ingang van AEM 6.2 toegevoegd voor AEM Communities om prestaties te verbeteren en steun voor paginering te verlenen wanneer het voorstellen van UGC onderzoeksresultaten.

Als aangepaste eigenschappen in gebruik zijn en zoekacties traag zijn, moeten aanvullende indexen worden gemaakt voor de aangepaste eigenschappen om deze beter te laten presteren. Om draagbaarheid te handhaven, houd aan [noemende vereisten ](#naming-of-custom-properties) wanneer het creëren van douaneeigenschappen die doorzoekbaar zijn.

Als u bestaande indexen wilt wijzigen of aangepaste indexen wilt maken, raadpleegt u [Vragen en indexeren](../../help/sites-deploying/queries-and-indexing.md).

De [Indexbeheer van de eik](https://adobe-consulting-services.github.io/acs-aem-commons/features/oak-index-manager.html) is beschikbaar bij ACS AEM Commons. Het voorziet in:

* Een weergave van bestaande indexen.
* De mogelijkheid om opnieuw indexeren te starten.

Als u de bestaande eik-indexen in [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md) wilt weergeven, is de locatie:

* `/oak:index/socialLucene`

![social-lucene](assets/social-lucene.png)

## Eigenschappen van Geïndexeerde zoekopdracht {#indexed-search-properties}

### Standaardzoekeigenschappen {#default-search-properties}

Hieronder vindt u een aantal van de doorzoekbare eigenschappen die worden gebruikt voor verschillende functies van de Gemeenschappen:

| **Eigenschap** | **Gegevenstype** |
|---|---|
| isFlagged | *Boolean* |
| isSpam | *Boolean* |
| read | *Boolean* |
| invloed | *Boolean* |
| bijlagen | *Boolean* |
| sentiment | *Lang* |
| gemarkeerd | *Boolean* |
| added | *Date* |
| modifiedDate | *Datum* |
| state | *Tekenreeks* |
| userIdentifier | *Tekenreeks* |
| antwoorden | *Lang* |
| jcr:titel | *Tekenreeks* |
| jcr:beschrijving | *Tekenreeks* |
| sling:resourceType | *Tekenreeks* |
| allowThreadedReply | *Boolean* |
| isDraft | *Boolean* |
| publishDate | *Datum* |
| publishJobId | *Tekenreeks* |
| beantwoord | *Boolean* |
| chosenanswer | *Boolean* |
| tag | *Tekenreeks* |
| cq:Tag | *Tekenreeks* |
| maker_display_name | *Tekenreeks* |
| location_t | *Tekenreeks* |
| parentPath | *Tekenreeks* |
| parentTitle | *Tekenreeks* |

### Naam van aangepaste eigenschappen {#naming-of-custom-properties}

Wanneer u aangepaste eigenschappen toevoegt, zodat die eigenschappen zichtbaar zijn voor sorteren en zoeken die zijn gemaakt met de [UGC-zoekAPI](#ugc-search-api), is het *required* om een achtervoegsel aan de eigenschapnaam toe te voegen.

Het achtervoegsel is voor vraagtalen die een schema gebruiken:

* Het identificeert de eigenschap als doorzoekbaar.
* Het identificeert het gegevenstype.

Solr is een voorbeeld van een vraagtaal die een schema gebruikt.

| **Achtervoegsel** | **Gegevenstype** |
|---|---|
| _b | *Boolean* |
| _dt | *Kalender* |
| _d | *Dubbel* |
| _tl | *Lang* |
| _s | *Tekenreeks* |
| _t | *Tekst* |

**Opmerkingen:**

* ** Textis a tokenized string,  ** String is not. Gebruik *Tekst* voor vage (meer als dit) onderzoeken.

* Voeg voor typen met meerdere waarden &quot;s&quot; toe aan het achtervoegsel, bijvoorbeeld:

   * `viewDate_dt`: single date, eigenschap
   * `viewDates_dts`: list of dates, eigenschap

## Filters {#filters}

Componenten die het [opmerkingssysteem](essentials-comments.md) bevatten ondersteunen de toevoeging van de filterparameter aan hun eindpunten.

De filtersyntaxis voor AND en OR logica wordt als volgt uitgedrukt (getoond alvorens URL wordt gecodeerd):

* U kunt als volgt één filterparam met door komma&#39;s gescheiden waarden opgeven OF gebruiken:

   * `filter=name eq 'Jennifer',name eq 'Jen'`

* Meerdere filterparams opgeven EN gebruiken:

   * `filter = name eq 'Jackson'&filter=message eq 'testing'`

De standaardimplementatie van [de component van het Onderzoek](search.md) gebruikt deze syntaxis zoals die in URL kan worden gezien die de pagina van de Resultaten van het Onderzoek in [Communautaire gids](components-guide.md) opent. Blader naar [http://localhost:4503/content/community-components/en/search.html](http://localhost:4503/content/community-components/en/search.html) om te experimenteren.

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

* Juist: forumcomponent
   * `/content/community-components/en/forum/jcr:content/content/forum.social.json`
* Onjuist: forumpagina
   * `/content/community-components/en/forum.social.json`

## SRP-gereedschappen {#srp-tools}

Er is een project Adobe Marketing Cloud GitHub dat bevat:

[AEM Communities SRP Tools](https://github.com/Adobe-Marketing-Cloud/aem-communities-srp-tools)

Deze opslagplaats bevat hulpmiddelen voor het beheren van gegevens in SRP.

Momenteel, is er één servlet die de capaciteit verstrekt om al UGC van om het even welk SRP te schrappen.

Bijvoorbeeld, om al UGC in ASRP te schrappen:

```shell
curl -X POST http://localhost:4502/services/social/srp/cleanup?path=/content/usergenerated/asi/cloud -uadmin:admin
```

## Problemen oplossen {#troubleshooting}

### Solr Query {#solr-query}

Om problemen met een Solr vraag problemen op te lossen, laat het registreren DEBUG voor toe

`com.adobe.cq.social.srp.impl.SocialSolrConnector`.

De daadwerkelijke Solr vraag zal URL worden getoond die in zuivert logboek wordt gecodeerd:

Zoekopdracht voor solderen is: `sort=timestamp+desc&bl=en&pl=en&start=0&rows=10 &q=%2Btitle_t:(hello)+%2Bprovider_id:\/content/usergenerated/asi/mongo/content/+%2Bresource_type_s:&df=provider_id&trf=verbatim&fq={!cost%3D100}report_suite:mongo`

De waarde van de parameter `q` is de vraag. Zodra het coderen URL wordt gedecodeerd, kan de vraag tot het Solr hulpmiddel van de Vraag Admin voor verdere het zuiveren worden overgegaan.

## Gerelateerde bronnen {#related-resources}

* [Community Content Storage](working-with-srp.md)  - Bespreekt de beschikbare SRP-keuzes voor een UGC-algemeen archief.
* [Overzicht](srp.md)  van Storage Resource Provider - Inleiding en overzicht van het opslaggebruik.
* [Toegang tot UGC met SRP](accessing-ugc-with-srp.md)  - Coderingsrichtlijnen.
* [SocialUtils Refactoring](socialutils.md)  - de methodes van het Nut voor SRP die SocialUtils vervangen.
* [Componenten](search.md)  met zoekresultaten - UGC-zoekfunctie toevoegen aan een sjabloon.

