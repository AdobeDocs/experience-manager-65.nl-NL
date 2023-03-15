---
title: Essentiële zoekopdrachten
seo-title: Search Essentials
description: Zoeken in gemeenschappen
seo-description: Search in Communities
uuid: 5f35a033-2069-499e-9cdb-db25781312f0
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 300aa9f3-596f-42bc-8d46-e535f2bc4379
exl-id: 8af5ee58-19d7-47b6-b45d-e88006703a5d
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1184'
ht-degree: 3%

---

# Essentiële zoekopdrachten {#search-essentials}

## Overzicht {#overview}

De zoekfunctie is een essentieel onderdeel van AEM Communities. Naast de [AEM zoeken](../../help/sites-deploying/queries-and-indexing.md) mogelijkheden biedt AEM Communities [UGC-zoekAPI](#ugc-search-api) voor het zoeken van door gebruikers gegenereerde inhoud (UGC). UGC heeft unieke eigenschappen omdat deze afzonderlijk van andere AEM inhoud en gebruikersgegevens wordt ingevoerd en opgeslagen.

Voor Gemeenschappen zijn de twee dingen die over het algemeen worden doorzocht:

* Inhoud geplaatst door leden van de gemeenschap

   * Gebruikt de UGC-zoekAPI van AEM-gemeenschappen.

* Gebruikers en gebruikersgroepen (gebruikersgegevens)

   * Gebruikt de zoekmogelijkheden van het AEM platform.

Deze sectie van de documentatie is van belang voor ontwikkelaars die douanecomponenten creëren die tot UGC leiden of leiden.

## Beveiligings- en schaduwknooppunten {#security-and-shadow-nodes}

Voor een aangepaste component moet u de opdracht [SocialResourceUtilities](socialutils.md#socialresourceutilities-package) methoden. De nutsmethodes die tot en onderzoek naar UGC leiden zullen de vereiste vestigen [schaduwknooppunten](srp.md#about-shadow-nodes-in-jcr) en ervoor zorgen dat het lid de juiste machtigingen voor het verzoek heeft.

Wat niet door de nut SRP wordt beheerd zijn eigenschappen met betrekking tot matiging.

Zie [SRP en UGC Essentials](srp-and-ugc.md) voor informatie betreffende nutsmethodes die worden gebruikt om tot UGC en ACL schaduwknopen toegang te hebben.

## UGC-zoekAPI {#ugc-search-api}

De [UGC Common Store](working-with-srp.md) wordt verstrekt door één van een verscheidenheid van opslagmiddelleveranciers (SRPs), elk misschien verschillend inheemse vraagtaal. Daarom, ongeacht het gekozen SRP, zou de douanecode methodes van moeten gebruiken [UGC API-pakket](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/ugc/api/package-summary.html) (*com.adobe.cq.social.ugc.api*) die de vraagtaal aangewezen voor gekozen SRP zal aanhalen.

### ASRP-zoekopdrachten {#asrp-searches}

Voor [ASRP](asrp.md), wordt UGC opgeslagen in de Adobe-cloud. Hoewel UGC niet zichtbaar is in CRX, [matiging](moderate-ugc.md) is beschikbaar in zowel de auteur- als de publicatieomgeving. Het gebruik van de [UGC-zoekAPI](#ugc-search-api) werkt voor ASRP het zelfde als voor andere SRPs.

De hulpmiddelen bestaan momenteel niet voor het beheren van de onderzoeken van ASRP.

Wanneer u aangepaste eigenschappen maakt die doorzoekbaar zijn, moet u zich aan de [naamgevingsvereisten](#naming-of-custom-properties).

### MSRP-zoekopdrachten {#msrp-searches}

Voor [MSRP](msrp.md), wordt UGC opgeslagen in MongoDB wordt gevormd om Solr voor het zoeken te gebruiken. UGC is niet zichtbaar in CRX, maar [matiging](moderate-ugc.md) is beschikbaar in zowel de auteur- als de publicatieomgeving.

Wat MSRP en Solr betreft:

* Ingesloten Solr voor het AEM platform wordt niet gebruikt voor MSRP.
* Als het gebruiken van verre Solr voor het AEM platform, kan het met MSRP worden gedeeld, maar zij zouden verschillende inzamelingen moeten gebruiken.
* Solr kan voor standaardonderzoek of voor meertalige onderzoek (MLS) worden gevormd.
* Voor configuratiedetails, zie [Solr-configuratie](msrp.md#solr-configuration) voor MSRP.

Voor aangepaste zoekfuncties moet u de opdracht [UGC-zoekAPI](#ugc-search-api).

Wanneer u aangepaste eigenschappen maakt die doorzoekbaar zijn, moet u zich aan de [naamgevingsvereisten](#naming-of-custom-properties).

### JSRP-zoekopdrachten {#jsrp-searches}

Voor [JSRP](jsrp.md), UGC wordt opgeslagen in [Eik](../../help/sites-deploying/platform.md) en is alleen zichtbaar in de gegevensopslagruimte van de AEM auteur of het publicatieexemplaar waarop het is ingevoerd.

Aangezien UGC typisch in het publicatiemilieu, voor multi-uitgeversproductiesystemen is ingegaan, is het noodzakelijk om een [publicatiecluster](topologies.md), niet een publicatiecentrum, zodat de ingevoerde inhoud zichtbaar is voor alle uitgevers.

Voor JSRP, zal UGC ingegaan in het publicatiemilieu nooit in het auteursmilieu zichtbaar zijn. Aldus [matiging](moderate-ugc.md) taken vinden plaats in de publicatieomgeving.

Voor aangepaste zoekfuncties moet u de opdracht [UGC-zoekAPI](#ugc-search-api).

#### Oak-indexering {#oak-indexing}

Terwijl de indexen van het Eak niet automatisch voor het AEM platformonderzoek worden gecreeerd, zijn zij met ingang van AEM 6.2 toegevoegd voor AEM Communities om prestaties te verbeteren en steun voor paginering te verlenen wanneer het voorstellen van UGC onderzoeksresultaten.

Als aangepaste eigenschappen in gebruik zijn en zoekacties traag zijn, moeten aanvullende indexen worden gemaakt voor de aangepaste eigenschappen om deze beter te laten presteren. Om draagbaarheid te behouden, dient u zich aan de [naamgevingsvereisten](#naming-of-custom-properties) wanneer u aangepaste eigenschappen maakt die doorzoekbaar zijn.

Als u bestaande indexen wilt wijzigen of aangepaste indexen wilt maken, raadpleegt u [Oak-query&#39;s en indexering](../../help/sites-deploying/queries-and-indexing.md).

De [Indexbeheer voor onak](https://adobe-consulting-services.github.io/acs-aem-commons/features/oak-index-manager.html) is beschikbaar bij ACS AEM Commons. Het voorziet in:

* Een weergave van bestaande indexen.
* De mogelijkheid om opnieuw indexeren te starten.

Bestaande eiken-indexen weergeven in [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md), is de locatie:

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
| modifiedDate | *Date* |
| state | *Tekenreeks* |
| userIdentifier | *Tekenreeks* |
| antwoorden | *Lang* |
| jcr:titel | *Tekenreeks* |
| jcr:beschrijving | *Tekenreeks* |
| sling:resourceType | *Tekenreeks* |
| allowThreadedReply | *Boolean* |
| isDraft | *Boolean* |
| publishDate | *Date* |
| publishJobId | *Tekenreeks* |
| beantwoord | *Boolean* |
| chosenanswer | *Boolean* |
| tag | *Tekenreeks* |
| cq:Tag | *Tekenreeks* |
| maker_display_name | *Tekenreeks* |
| location_t | *Tekenreeks* |
| parentPath | *Tekenreeks* |
| parentTitle | *Tekenreeks* |

### Naamgeving van aangepaste eigenschappen {#naming-of-custom-properties}

Wanneer u aangepaste eigenschappen toevoegt, zodat deze eigenschappen zichtbaar zijn voor sorteren en zoeken die zijn gemaakt met de opdracht [UGC-zoekAPI](#ugc-search-api)is *vereist* om een achtervoegsel aan de bezitsnaam toe te voegen.

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

* *Tekst* een getokeniseerde tekenreeks is, *String* is niet. Gebruiken *Tekst* voor vage (meer als dit) zoekopdrachten.

* Voeg voor typen met meerdere waarden &quot;s&quot; toe aan het achtervoegsel, bijvoorbeeld:

   * `viewDate_dt`: single date, eigenschap
   * `viewDates_dts`: list of dates, eigenschap

## Filters {#filters}

Onderdelen die de [opmerkingssysteem](essentials-comments.md) ondersteunen de filterparameter als aanvulling op de eindpunten.

De filtersyntaxis voor AND en OR logica wordt als volgt uitgedrukt (getoond alvorens URL wordt gecodeerd):

* U kunt als volgt één filterparam met door komma&#39;s gescheiden waarden opgeven OF gebruiken:

   * `filter=name eq 'Jennifer',name eq 'Jen'`

* Meerdere filterparams opgeven EN gebruiken:

   * `filter = name eq 'Jackson'&filter=message eq 'testing'`

De standaardimplementatie van de [component Zoeken](search.md) gebruikt deze syntaxis zoals u kunt zien in de URL waarmee de pagina Zoekresultaten wordt geopend in het dialoogvenster [Community Components Guide](components-guide.md). Als u wilt experimenteren, bladert u naar [http://localhost:4503/content/community-components/en/search.html](http://localhost:4503/content/community-components/en/search.html).

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

## SRP {#srp-tools}

Er is een project Adobe Marketing Cloud GitHub dat bevat:

[AEM Communities SRP Tools](https://github.com/Adobe-Marketing-Cloud/aem-communities-srp-tools)

Deze opslagplaats bevat hulpmiddelen voor het beheren van gegevens in SRP.

Momenteel, is er één servlet die de capaciteit verstrekt om al UGC van om het even welk SRP te schrappen.

Bijvoorbeeld, om al UGC in ASRP te schrappen:

```shell
curl -X POST http://localhost:4502/services/social/srp/cleanup?path=/content/usergenerated/asi/cloud -uadmin:admin
```

## Problemen oplossen {#troubleshooting}

### Solr-query {#solr-query}

Om problemen met een Solr vraag problemen op te lossen, laat het registreren DEBUG voor toe

`com.adobe.cq.social.srp.impl.SocialSolrConnector`.

De daadwerkelijke Solr vraag zal URL worden getoond die in zuivert logboek wordt gecodeerd:

Zoekopdracht voor solderen is: `sort=timestamp+desc&bl=en&pl=en&start=0&rows=10 &q=%2Btitle_t:(hello)+%2Bprovider_id:\/content/usergenerated/asi/mongo/content/+%2Bresource_type_s:&df=provider_id&trf=verbatim&fq={!cost%3D100}report_suite:mongo`

De waarde van de `q` parameter is de query. Zodra het coderen URL wordt gedecodeerd, kan de vraag tot het Solr hulpmiddel van de Vraag Admin voor verdere het zuiveren worden overgegaan.

## Gerelateerde bronnen {#related-resources}

* [Opslag van communautaire inhoud](working-with-srp.md) - Bespreekt de beschikbare keuzen SRP voor een gemeenschappelijke opslag UGC.
* [Overzicht opslagbronprovider](srp.md) - Inleiding en overzicht van het gebruik van de opslagplaats.
* [Toegang tot UGC met SRP](accessing-ugc-with-srp.md) - Coderingsrichtsnoeren.
* [SocialUtils Refactoring](socialutils.md) - Hulpprogrammamethoden voor SRP die SocialUtils vervangen.
* [Componenten met zoekresultaten](search.md) - UGC-zoekfunctie toevoegen aan een sjabloon.
