---
title: AEM Stichting en gegevensopslagruimte
description: Release-aantekeningen voor Adobe Experience Manager-platform en -opslagplaats.
translation-type: tm+mt
source-git-commit: 8d60e064ab50f24016c049c8d5d0fceb784c99a3
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---


# AEM Stichting en opslagplaats {#aem-foundation-repository}

## Lijst met wijzigingen {#list-of-changes}

### Bewaarplaats {#repository}

* De basis voor Adobe Experience Manager 6.5 is gebaseerd op de bijgewerkte versies van het op OSGi gebaseerde framework (Apache Sling en Apache Felix) en de Java Content Repository: Apache Jackrabbit Oak 1.10.2.
* Zie [Apache Jackrabbit Oak Jira v. 1.10.0](https://archive.apache.org/dist/jackrabbit/oak/1.10.0/RELEASE-NOTES.txt), [Apache Jackrabbit Oak Jira v. 1.10.1](https://archive.apache.org/dist/jackrabbit/oak/1.10.1/RELEASE-NOTES.txt) en [Apache Jackrabbit Oak Jira v. 1.10.2](https://archive.apache.org/dist/jackrabbit/oak/1.10.2/RELEASE-NOTES.txt).

>[!CAUTION]
>
>De nieuwe versie van de Oak Segment Tar aanwezig sinds AEM 6.3 vereist een repository migratie. Deze stap is verplicht als u een upgrade uitvoert van een oudere versie van TarMK of als u de nieuwe segmentmarkering wilt overschakelen van een ander type persistentie. Voor meer informatie over wat de voordelen van de nieuwe Tar van het Segment zijn, zie [Migrating to Oak Segment Tar FAQ](/help/sites-deploying/revision-cleanup.md#migrating-to-oak-segment-tar).

### Java-ondersteuning {#java-support}

* Nieuwe ondersteuning voor Java 11 en de reeds ondersteunde Java 8.
* Overschrijf voor optimale prestaties de standaard GC-waarden met andere waarden. Zie de sectie [Installeren en bijwerken](/help/sites-deploying/custom-standalone-install.md) voor meer informatie.
* Java 11- en Java 8-onderhoudsupdates worden door Adobe gedistribueerd voor gebruik door klanten in AEM gerelateerde projecten, wanneer deze niet openbaar beschikbaar zijn in Oracle.

### OSGI {#osgi}

* Toegevoegde OSGi Promises en de nutsbibliotheken van de Converter.

### Projecten en workflows {#projects-and-workflows}

* De nieuwe die redacteur van het Model van het Werkschema in 6.4 wordt geïntroduceerd is verbeterd om meer verrichtingen zoals het Exemplaar en te publiceren, veranderlijke steun in de stappen van het Werkschema en verbeterde `OR` en `AND` splits te omvatten.

### Zoeken {#searching}

* Zoeken in eiken ondersteunt nu dynamische facetten. Zo toont de filterrail in de zoekopdracht naar elementen de geschatte hoeveelheid resultaten.
* QueryBuilder is uitgebreid om resultaten met dynamische facetten te bieden.

### Beveiliging {#security}

* Vervaldatum wachtwoord toegevoegd voor gebruiker van beheerder.

### Gebruikersinterface {#user-interface}

Er zijn verschillende verbeteringen aangebracht in de interface om deze productiever en gebruiksvriendelijker te maken.

* AEM 6.5 introduceert nieuwe UI van het Beheer van Toestemmingen voor Gebruikers en Groepen die het gemakkelijker maakt om de volledige reeks voorrechten en beperkingen te bekijken en te vormen zonder de behoefte om naar CRXDE te gaan.
* Met Kolomweergaven worden nu ook alleen items geladen die zichtbaar zijn op het scherm en worden alleen meer items geladen wanneer de gebruiker begint met schuiven. De lijst- en kaartweergave heeft dat al gedaan sinds 6.0 (verbeterd in 6.4).
* Kolomweergaven bevatten nu, indien van toepassing, de workflowstatus voor pagina&#39;s/middelen.
* Met de handeling Alles selecteren kunt u snel een handeling uitvoeren waarbij alle pagina&#39;s/middelen in dezelfde map staan.
* Met de handeling Alles selecteren wordt geprobeerd de handeling op alle pagina&#39;s/elementen uit te voeren, niet alleen op wat is geladen. Als de actie niet wordt bevorderd om Bulk Acties te behandelen, wordt een waarschuwing getoond.

>[!CAUTION]
>
>Adobe zal geen verdere verhogingen aan Klassieke UI maken. Experience Manager 6.5 omvat Klassieke UI voor achterwaartse verenigbaarheid. Klassieke UI blijft volledig gesteund terwijl wordt afgekeurd [lees meer](/help/sites-deploying/ui-recommendations.md).

### Upgrade {#upgrade}

* De upgradeprocedure blijft grotendeels hetzelfde in paragraaf 6.5.
* We blijven de functies Achterwaartse compatibiliteit, Complexiteitsbeoordeling upgraden en Duurzame upgrades ondersteunen die in 6.4 zijn geïntroduceerd. Waar nodig zijn op deze gebieden versiespecifieke wijzigingen aangebracht.
* Het verpakken van de Detector van het Patroon is vereenvoudigd, en er zal één pakket zijn die verbeteringen aan 6.5 voor de beschikbare bronversies evalueren.
* Voor details over verbeteringsprocedure, zie [verbeteringsdocumentatie](/help/sites-deploying/upgrade.md).

### Webserver {#web-server}

* Bij de distributie van QuickStart wordt Eclipse Jetty 9.4.15 gebruikt als servletengine (AEM 6.4 geleverd bij 9.3.22).
