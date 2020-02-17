---
title: SRP - Opslag van communautaire inhoud
seo-title: SRP - Opslag van communautaire inhoud
description: Vanaf AEM Communities 6.1 wordt door gebruikers gegenereerde inhoud (UGC) opgeslagen in één gemeenschappelijke opslag die wordt geleverd door een opslagresource provider (SRP)
seo-description: Vanaf AEM Communities 6.1 wordt door gebruikers gegenereerde inhoud (UGC) opgeslagen in één gemeenschappelijke opslag die wordt geleverd door een opslagresource provider (SRP)
uuid: d45e03c4-378b-4510-a6a0-d48c8cb879d9
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 6f13b21a-f4ef-4889-9b8e-4da3f846fa35
docset: aem65
translation-type: tm+mt
source-git-commit: 70e6f2d8366456e5091b7b775dc40914948921ab

---


# SRP - Opslag van communautaire inhoud{#srp-community-content-storage}

## Inleiding {#introduction}

Vanaf AEM Communities 6.1 wordt door de gebruiker gegenereerde inhoud (UGC) opgeslagen in één gemeenschappelijke opslag die wordt geleverd door een opslagresource provider (SRP). Er zijn verscheidene opties SRP waarvan te kiezen, zoals ASRP, MSRP, en JSRP.

In tegenstelling tot eerdere versies, is er geen omgekeerde/voorwaartse replicatie van UGC over instanties AEM. In plaats daarvan maakt SRP UGC direct toegankelijk voor creeer, lees, update, en schrapt (CRUD) verrichtingen van alle auteur en publiceer instanties, met een uitzondering voor JSRP.

Na zijn de [kenmerken van elke optie](#characteristics-of-srp-options)SRP, die cruciale informatie voor het besluitvormingsproces wanneer het kiezen van aangewezen SRP en [onderliggende plaatsing](/help/communities/topologies.md)is.

Voor details betreffende het gebruik van SRP voor UGC, zie het Overzicht [van de Leverancier van het Middel van de](/help/communities/srp.md)Opslag.

>[!NOTE]
>
>SRP is slechts op communautaire inhoud van toepassing. Het heeft geen invloed op de locatie waar de site-inhoud wordt opgeslagen ([knooppuntopslag](/help/sites-deploying/data-store-config.md)) en heeft geen invloed op de veilige verwerking van gebruikersregistratie, gebruikersprofielen en gebruikersgroepen tussen AEM-instanties (zie ook Gebruikersgegevens [](#managing-user-data)beheren).

>[!CAUTION]
>
>Vanaf AEM 6.1 wordt [UGC nooit gerepliceerd](#ugc-never-replicated).
>
>Wanneer de plaatsing geen gemeenschappelijke opslag, zoals de standaardtopologie [JSRP](/help/communities/topologies.md#jsrp) omvat, zal UGC slechts op AEM zichtbaar zijn publiceert of auteursinstantie waarop het was ingegaan. Alleen als de topologie een publicatiecluster bevat, is de UGC zichtbaar op elke publicatieinstantie.

## Kenmerken van SRP-opties {#characteristics-of-srp-options}

[ASRP - Adobe Storage Resource Provider](/help/communities/asrp.md)Met deze optie wordt de UGC extern voortgezet in een cloudservice die wordt gehost en beheerd door Adobe. Het vereist een aanvullende licentie en samenwerking met een accountvertegenwoordiger om de rekening voor die specifieke licentie te verstrekken. ASRP vereist:

* Een gekoppelde cloudservice die door Adobe wordt geleverd en ondersteund voor het opslaan van community-inhoud.
* Keuze van een datacenter in een specifieke geografie (VS, EMEA, APAC).

* Alle programmatic toegang tot UGC is door SRP API.

ASRP is geschikt:

* voor TarMK, publicatiebedrijf.
* wanneer er geen intentie is om te investeren in lokale opslag.

>[!NOTE]
>
>Er geldt een limiet voor het uploaden van bijlagen naar posten (of opmerkingen) in ASRP. Dit is 50 MB.

[MSRP - de Leverancier](/help/communities/msrp.md)van het Middel van de Opslag MongoDB met deze optie, wordt UGC voortgeduurd direct in een lokale instantie MongoDB.

MSRP vereist:

* Een lokale, gelicentieerde installatie van MongoDB om inhoud van de gebruikersgemeenschap op te slaan.
* Een lokale installatie van Apache Solr.
* Alle programmatic toegang tot UGC is door SRP API.

ASRP is geschikt:

* Voor bestaande TarMK publiceert landbouwbedrijf.
* Voor een MongoMK- of RdbMK-cluster.
* Wanneer er grote hoeveelheden community-inhoud worden verwacht.

[DSRP - de Relationele Leverancier](/help/communities/dsrp.md)van het Middel van de Opslag van het Gegevensbestand met deze optie, wordt UGC voortgeduurd direct in een lokale MySQL gegevensbestandinstantie.

DSRP vereist:

* Een lokale installatie van MySQL om inhoud van de gemeenschap op te slaan.
* Een lokale installatie van Apache Solr.
* Alle programmatic toegang tot UGC is door SRP API.

DSRP is geschikt:

* Voor bestaande TarMK publiceert landbouwbedrijf.
* Voor een MongoMK- of RdbMK-cluster.
* Wanneer er grote hoeveelheden community-inhoud worden verwacht.

[JSRP - JCR Storage Resource Provider](/help/communities/jsrp.md)Met de standaardoptie is er geen algemeen archief. De UGC wordt alleen gecontinueerd in dezelfde JCR-opslagruimte als de AEM-instantie waarin deze is ingevoerd.

JSRP:

* Hiermee wordt community-inhoud opgeslagen in de JCR-opslagruimte van de AEM-auteur of -publicatieinstantie waarnaar deze is gepost.
* Vereist alle programmatic toegang tot UGC door SRP API zijn.
* Vereist een publicatiecluster als meer dan één publiceer instantie wordt opgesteld (er is geen replicatiemechanisme onder publiceer instanties in een landbouwbedrijf TarMK).
* De matiging wordt uitgevoerd slechts in het publicatiemilieu (er is geen omgekeerd/voorwaarts replicatiemechanisme tussen auteur en publiceert).
* Is het beste voor ontwikkeling, demonstraties, en opleiding.

## SRP configureren {#configuring-srp}

Het specificeren van de standaard opslagoptie, die op de onderliggende plaatsing wordt gebaseerd, wordt gemaakt door de console [van de Configuratie van de](/help/communities/srp-config.md)Opslag.

Voor configuratiedetails van elke optie, zie:

* [ASRP - Adobe Storage Resource Provider](/help/communities/asrp.md)
* [MSRP - MongoDB Storage Resource Provider](/help/communities/msrp.md)
* [DSRP - Relational Database Storage Resource Provider](/help/communities/dsrp.md)
* [JSRP - JCR Storage Resource Provider](/help/communities/jsrp.md)

Als er geen opslagoptie actief is geselecteerd, wordt JSRP standaard ingeschakeld.

## Additional Information {#additional-information}

### UGC nooit gerepliceerd {#ugc-never-replicated}

In de auteursomgeving, creeert een auteur pagina inhoud en herhaalt het aan het publicatiemilieu. Wanneer een pagina een interactieve functie voor AEM-gemeenschappen bevat, zoals opmerkingen, revisies, forums, blogs of QnA, resulteert de interactie van leden (die zijn aangemeld bij sitebezoekers) op een publicatie-instantie in door gebruikers gegenereerde inhoud (UGC) die is ingevoerd in de publicatieomgeving.

Eerder werd deze community-inhoud omgekeerd gerepliceerd naar auteur-instanties en van de auteur gerepliceerd naar publicatie-instanties. Het was problematisch om consistentie tussen AEM instanties met omgekeerde en voorwaartse replicatie te handhaven.

Vanaf AEM Communities 6.1 is de behoefte aan replicatie van UGC geëlimineerd door gedeelde opslag voor UGC te gebruiken, zoals hierboven beschreven.

Terwijl site-inhoud wordt gerepliceerd, wordt UGC nooit gerepliceerd.

### Gebruikersgegevens beheren {#managing-user-data}

Ook van belang voor CommunityIes zijn [*gebruikers *,* gebruikersgroepen *, en* gebruikersprofielen *](/help/communities/users.md). Deze op gebruiker betrekking hebbende gegevens, wanneer gecreeerd en bijgewerkt in publicatiemilieu, moeten aan andere publicatieinstanties ter beschikking worden gesteld wanneer de topologie een[publicatielandbouwbedrijf](/help/sites-deploying/recommended-deploys.md#tarmk-farm)is.

Vanaf AEM Communities 6.1 worden gebruikersgerelateerde gegevens gesynchroniseerd met Sling Distribution in plaats van replicatie. Ga voor meer informatie naar [Gebruikerssynchronisatie](/help/communities/sync.md).

### Opwaarderen naar AEM-gemeenschappen 6.5 {#upgrading-to-aem-communities}

Als bij de upgrade naar AEM 6.5-gemeenschappen bestaande UGC behouden moet blijven, moeten stappen worden gezet afhankelijk van het feit of de AEM 5.6.1- of AEM 6.0-community gebruikmaakte van Adobe on-demand opslag of on-premise opslag van UGC.

Ga voor meer informatie naar [Upgrade naar AEM Communities 6.5](/help/communities/upgrade.md).
