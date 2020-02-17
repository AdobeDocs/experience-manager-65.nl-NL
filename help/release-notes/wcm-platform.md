---
title: AEM Foundation & Repository
description: Opmerkingen bij de release specifiek voor Adobe Experience Manager 6.3 AEM Platform en Repository.
uuid: 70626eda-c514-44bd-9f28-ff7abdc22f53
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
discoiquuid: 66ecf4c5-6d0f-4586-880d-7d1c8a5a5614
docset: aem65
translation-type: tm+mt
source-git-commit: 4dc4a518c212555b7833ac27de02087a403d3517

---


# AEM Foundation &amp; Repository{#aem-foundation-repository}

## Lijst met wijzigingen {#list-of-changes}

### Bewaarplaats {#repository}

* De basis voor Adobe Experience Manager 6.5 is gebaseerd op bijgewerkte versies van het op OSGi gebaseerde framework (Apache Sling en Apache Felix) en de Java Content Repository: Apache Jackrabbit Oak 1.10.2.
* Zie [Apache Jackrabbit Oak Jira v. 1.10.0](https://archive.apache.org/dist/jackrabbit/oak/1.10.0/RELEASE-NOTES.txt), [Apache Jackrabbit Oak Jira v. 1.10.1](https://archive.apache.org/dist/jackrabbit/oak/1.10.1/RELEASE-NOTES.txt) en [Apache Jackrabbit Oak Jira v. 1.10.2](https://archive.apache.org/dist/jackrabbit/oak/1.10.2/RELEASE-NOTES.txt) voor een volledig overzicht van de opgeloste problemen.

>[!CAUTION]
>
>* De nieuwe versie van de Oak Segment Tar aanwezig sinds AEM 6.3 vereist een repository migratie. Deze stap is verplicht als u een upgrade uitvoert van een oudere versie van TarMK of als u de nieuwe segmentmarkering wilt overschakelen van een ander type persistentie. Raadpleeg de veelgestelde vragen over het migreren naar [eiken segment voor meer informatie over de voordelen van de nieuwe segmentmarkering](/help/sites-deploying/revision-cleanup.md#migrating-to-oak-segment-tar).
>



### Java-ondersteuning {#java-support}

* Nieuwe ondersteuning voor Java 11 en de reeds ondersteunde Java 8
* Overschrijf voor optimale prestaties de standaard GC-waarden met andere waarden. Zie de sectie [Installeren en bijwerken](/help/sites-deploying/custom-standalone-install.md) voor meer informatie.
* Updates voor Java 11- en Java 8-onderhoud worden door Adobe gedistribueerd voor gebruik door klanten in AEM-gerelateerde projecten, indien deze niet openbaar zijn via Oracle

### OSGI {#osgi}

* Toegevoegde OSGi Promises en de nutsbibliotheken van de Converter

### Projecten en workflows {#projects-and-workflows}

* De nieuwe die redacteur van het Model van het Werkschema in 6.4 wordt geïntroduceerd is verbeterd om meer verrichtingen zoals het Exemplaar en te publiceren, veranderlijke steun in de stappen van het Werkschema en verbeterde OF en EN splits te omvatten.

### Zoeken {#searching}

* Zoeken in eiken ondersteunt nu dynamische facetten. Zo toont de filterrail in de zoekopdracht naar elementen de geschatte hoeveelheid resultaten.
* QueryBuilder is uitgebreid om resultaten met dynamische facetten te bieden

### Beveiliging {#security}

* Vervaldatum wachtwoord toegevoegd voor gebruiker van beheerder.

### Gebruikersinterface {#user-interface}

Er zijn verschillende verbeteringen aangebracht in de interface om deze productiever en gebruiksvriendelijker te maken.

* AEM 6.5 introduceert nieuwe UI van het Beheer van Toestemmingen voor Gebruikers en Groepen die het gemakkelijker maakt om de volledige reeks voorrechten en beperkingen te bekijken en te vormen zonder de behoefte om naar CRXDE te gaan.
* Met Kolomweergaven worden nu ook alleen items geladen die zichtbaar zijn op het scherm en worden alleen meer items geladen wanneer de gebruiker begint met schuiven. De lijst- en kaartweergave heeft dat al gedaan sinds 6.0 (verbeterd in 6.4)
* Kolomweergaven bevatten nu, indien van toepassing, de workflowstatus voor pagina&#39;s/middelen
* De actie Alles selecteren is een snelle manier om een handeling uit te voeren met alle pagina&#39;s/middelen in dezelfde map
* Met de actie Alles selecteren wordt geprobeerd de handeling op alle pagina&#39;s/elementen uit te voeren, niet alleen op wat is geladen. Er wordt een waarschuwingsvenster weergegeven als de handeling niet is bijgewerkt om Bulkhandelingen af te handelen

>[!CAUTION]
>
>* Adobe is niet van plan verdere verbeteringen aan te brengen in de klassieke gebruikersinterface. AEM 6.5 heeft de Klassieke inbegrepen UI, en de klanten die van vroegere versies bevorderen kunnen het blijven gebruiken zoals is. Merk op dat Klassieke UI volledig gesteund terwijl wordt afgekeurd [Lees meer](/help/sites-deploying/ui-recommendations.md).
>



### Upgrade {#upgrade}

* De upgradeprocedure blijft grotendeels hetzelfde in paragraaf 6.5.
* We blijven de functies Achterwaartse compatibiliteit, Complexiteitsbeoordeling upgraden en Duurzame upgrades ondersteunen die in 6.4 zijn geïntroduceerd. Waar nodig zijn op deze gebieden versiespecifieke wijzigingen aangebracht.
* Het verpakken van de Detector van het Patroon is vereenvoudigd, en er zal één pakket zijn die verbeteringen aan 6.5 voor de beschikbare bronversies evalueren.
* Raadpleeg de [upgradedocumentatie](/help/sites-deploying/upgrade.md) voor meer informatie over de upgradeprocedure.

### Webserver {#web-server}

* Bij de distributie van QuickStart wordt Eclipse Jetty 9.4.15 gebruikt als servletengine (AEM 6.4 geleverd met 9.3.22)

