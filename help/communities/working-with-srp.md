---
title: SRP - Opslag van communautaire inhoud
description: Vanaf AEM Communities 6.1 wordt door de gebruiker gegenereerde inhoud (UGC) opgeslagen in één gemeenschappelijke opslagplaats die wordt geleverd door een opslagprovider (SRP)
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
docset: aem65
role: Admin
exl-id: e29aae44-67be-43d2-8004-c986412d9e63
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '906'
ht-degree: 0%

---

# SRP - Opslag van communautaire inhoud {#srp-community-content-storage}

## Inleiding {#introduction}

Vanaf AEM Communities 6.1 wordt door de gebruiker gegenereerde inhoud (UGC) opgeslagen in één gemeenschappelijke opslagplaats die wordt geleverd door een opslagbronprovider (SRP). Er zijn verscheidene opties SRP waarvan te kiezen, zoals ASRP, MSRP, en JSRP.

In tegenstelling tot vroegere versies, is er geen omgekeerde/voorwaartse replicatie van UGC over AEM instanties. In plaats daarvan maakt SRP UGC direct toegankelijk voor creeer, lees, update, en schrapt (CRUD) verrichtingen van alle auteur en publiceer instanties, met een uitzondering voor JSRP.

Hieronder vindt u de [kenmerken van elke SRP-optie](#characteristics-of-srp-options), die van cruciaal belang is voor het besluitvormingsproces bij de keuze van het passende SRP en [onderliggende implementatie](/help/communities/topologies.md).

Voor details betreffende het gebruik van SRP voor UGC, zie [Overzicht opslagbronprovider](/help/communities/srp.md).

>[!NOTE]
>
>SRP is slechts op communautaire inhoud van toepassing. Het heeft geen invloed op de opslaglocatie van de site ([knooppuntopslag](/help/sites-deploying/data-store-config.md)) en heeft geen invloed op de veilige verwerking van gebruikersregistratie, gebruikersprofielen en gebruikersgroepen tussen AEM instanties (zie ook [Gebruikersgegevens beheren](#managing-user-data)).

>[!CAUTION]
>
>Vanaf AEM 6.1 [UGC wordt nooit herhaald](#ugc-never-replicated).
>
>Wanneer de plaatsing geen gemeenschappelijke opslag, zoals het gebrek omvat [JSRP](/help/communities/topologies.md#jsrp) topologie, zal UGC slechts op AEM publiceren of auteursinstantie zichtbaar zijn waarop het was ingegaan. Alleen als de topologie een publicatiecluster bevat, is de UGC zichtbaar op elke publicatieinstantie.

## Kenmerken van SRP-opties {#characteristics-of-srp-options}

[ASRP - Adobe Storage Resource Provider](/help/communities/asrp.md)

Met deze optie, wordt UGC voortgeduurd ver in een wolkendienst die door Adobe wordt ontvangen en wordt beheerd. Het vereist een aanvullende licentie en samenwerking met een accountvertegenwoordiger om de rekening voor die specifieke licentie te verstrekken. ASRP vereist:

* Een gekoppelde cloudservice die wordt geleverd en ondersteund door de Adobe voor het opslaan van community-inhoud.
* Keuze van een datacenter in een specifieke geografie (VS, EMEA, APAC).

* Alle programmatic toegang tot UGC is door SRP API.

ASRP is geschikt:

* Voor TarMK publiceert landbouwbedrijf.
* Als er geen intent is om in lokale opslag te investeren.

>[!NOTE]
>
>Er geldt een limiet voor het uploaden van bijlagen naar posten (of opmerkingen) in ASRP. Dit is 50 MB.

[MSRP - MongoDB Storage Resource Provider](/help/communities/msrp.md)

Met deze optie wordt de UGC direct in een lokale MongoDB-instantie voortgezet.

MSRP vereist:

* Een lokale, gelicentieerde installatie van MongoDB om inhoud van de gebruikersgemeenschap op te slaan.
* Een lokale installatie van Apache Solr.
* Alle programmatic toegang tot UGC is door SRP API.

ASRP is geschikt:

* Voor bestaande TarMK publiceert landbouwbedrijf.
* Voor een MongoMK- of RdbMK-cluster
* Wanneer er grote hoeveelheden community-inhoud worden verwacht.

[DSRP - Relational Database Storage Resource Provider](/help/communities/dsrp.md)

Met deze optie, wordt UGC voortgeduurd direct in een lokale MySQL gegevensbestandinstantie.

DSRP vereist:

* Een lokale installatie van MySQL om inhoud van de gemeenschap op te slaan.
* Een lokale installatie van Apache Solr.
* Alle programmatic toegang tot UGC is door SRP API.

DSRP is geschikt:

* Voor bestaande TarMK publiceert landbouwbedrijf.
* Voor een MongoMK- of RdbMK-cluster
* Wanneer er grote hoeveelheden community-inhoud worden verwacht.

[JSRP - JCR Storage Resource Provider](/help/communities/jsrp.md)

Met de standaardoptie, is er geen gemeenschappelijke opslag. De UGC wordt alleen gecontinueerd in dezelfde JCR-opslagruimte als de AEM instantie waarin deze is ingevoerd.

JSRP:

* Hiermee wordt community-inhoud opgeslagen in de JCR-opslagruimte van de AEM auteur of publicatie-instantie waarnaar deze is gepost.
* Vereist alle programmatic toegang tot UGC door SRP API zijn.
* Vereist een publicatiecluster als meer dan één publiceer instantie wordt opgesteld (er is geen replicatiemechanisme onder publiceer instanties in een landbouwbedrijf TarMK).
* De matiging wordt uitgevoerd slechts in het publicatiemilieu (er is geen omgekeerd/voorwaarts replicatiemechanisme tussen auteur en publiceert).
* Is het beste voor ontwikkeling, demonstraties, en opleiding.

## SRP configureren {#configuring-srp}

Het specificeren van de standaard opslagoptie, die op de onderliggende plaatsing wordt gebaseerd, wordt gemaakt door [Opslagconfiguratieconsole](/help/communities/srp-config.md).

Zie voor configuratiegegevens van elke optie:

* [ASRP - Adobe Storage Resource Provider](/help/communities/asrp.md)
* [MSRP - MongoDB Storage Resource Provider](/help/communities/msrp.md)
* [DSRP - Relational Database Storage Resource Provider](/help/communities/dsrp.md)
* [JSRP - JCR Storage Resource Provider](/help/communities/jsrp.md)

Als er geen opslagoptie actief is geselecteerd, wordt JSRP standaard ingeschakeld.

## Aanvullende informatie {#additional-information}

### UGC nooit gerepliceerd {#ugc-never-replicated}

In de auteursomgeving, creeert een auteur pagina inhoud en herhaalt het aan het publicatiemilieu. Wanneer een pagina een interactieve AEM Communities-functie bevat, zoals opmerkingen, revisies, forum, blog of QnA, resulteert de interactie door leden (aangemeld bij sitebezoekers) op een publicatie-instantie in door gebruikers gegenereerde inhoud (UGC) die wordt ingevoerd in de publicatieomgeving.

Eerder werd deze community-inhoud omgekeerd gerepliceerd naar auteur-instanties en van de auteur gerepliceerd naar publicatie-instanties. Het was problematisch om consistentie tussen AEM instanties met omgekeerde en voorwaartse replicatie te handhaven.

Vanaf AEM Communities 6.1 is de behoefte aan replicatie van UGC geëlimineerd door gedeelde opslag voor UGC te gebruiken, zoals hierboven beschreven.

Terwijl site-inhoud wordt gerepliceerd, wordt UGC nooit gerepliceerd.

### Gebruikersgegevens beheren {#managing-user-data}

Ook van belang voor de Gemeenschap [*gebruikers*, *gebruikersgroepen*, en *gebruikersprofielen*](/help/communities/users.md). Deze op gebruiker betrekking hebbende gegevens, wanneer gecreeerd en bijgewerkt in publicatiemilieu, moeten ter beschikking worden gesteld aan andere publicatieinstanties wanneer de topologie een is [publicatiebedrijf](/help/sites-deploying/recommended-deploys.md#tarmk-farm).

Vanaf AEM Communities 6.1 worden gebruikersgerelateerde gegevens gesynchroniseerd met behulp van Verschuivende distributie in plaats van replicatie. Voor meer informatie gaat u naar [Gebruikerssynchronisatie](/help/communities/sync.md).

### Upgrade uitvoeren naar AEM Communities 6.5 {#upgrading-to-aem-communities}

Als bij de upgrade naar AEM 6.5-gemeenschappen de reeds bestaande UGC moet worden gehandhaafd, moeten stappen worden gezet afhankelijk van het feit of de AEM 5.6.1- of AEM 6.0-gemeenschap gebruikmaakte van Adobe-opslag op aanvraag of opslag op locatie van UGC.

Ga voor meer informatie naar [Upgrade uitvoeren naar AEM Communities 6.5](/help/communities/upgrade.md).
