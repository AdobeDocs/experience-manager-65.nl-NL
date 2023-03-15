---
title: "IBM DB2-database: Opdrachten uitvoeren voor regelmatig onderhoud"
seo-title: "IBM DB2 database: Running commands for regular maintenance"
description: Dit document bevat een lijst met IBM DB2-opdrachten die worden aanbevolen voor regelmatig onderhoud van de database met AEM formulieren.
seo-description: This document lists IBM DB2 commands that are recommended for regular maintenance of your AEM forms database.
uuid: 235d59df-b9b9-4770-8b7d-00713701c3c2
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: a62b68b4-7735-49b1-8938-f0d9e4c4a051
exl-id: 7a4281e7-1544-473a-a471-e9a4c2819a58
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# IBM DB2-database: Opdrachten uitvoeren voor regelmatig onderhoud {#ibm-db-database-running-commands-for-regular-maintenance}

De volgende IBM DB2-opdrachten worden aanbevolen voor regelmatig onderhoud van de database met AEM formulieren. Voor gedetailleerde informatie over onderhoud en prestaties het stemmen voor uw gegevensbestand DB2, zie *IBM DB2 Administration Guide*.

* **runframes:** Dit bevel werkt statistieken bij die de fysieke kenmerken van een gegevensbestandlijst, samen met zijn bijbehorende indexen beschrijven. Dynamische SQL-instructies die door AEM formulieren worden gegenereerd, gebruiken automatisch deze bijgewerkte statistieken, maar statische SQL-instructies die in een database zijn gemaakt, vereisen dat de `db2rbind` ook worden uitgevoerd.
* **db2rbind:** Deze opdracht koppelt alle pakketten in de database. Gebruik deze opdracht nadat u de opdracht `runstats` nut om alle pakketten in het gegevensbestand opnieuw te bevestigen.
* **reorg tabel of index:** Dit bevel controleert of een reorganisatie van sommige lijsten en indexen wordt vereist.

   Aangezien uw gegevensbestanden groeien en veranderen, is het opnieuw berekenen van lijststatistieken kritiek aan het verbeteren van gegevensbestandprestaties en zou regelmatig moeten worden gedaan. Deze opdrachten kunnen handmatig worden uitgevoerd met behulp van scripts of met behulp van een uitsnijdtaak.

>[!NOTE]
>
>Voordat u het dialoogvenster `runstats` , moet de database gegevens bevatten en moet ten minste één directorysynchronisatie zijn uitgevoerd.

Voor een kleine database, bijvoorbeeld voor 10.000 gebruikers of 2.500 groepen, is het voldoende om de `runstats` gebruiken om de synchronisatietijdstippen te verminderen.

Voor grotere databases, zoals voor 100.000 gebruikers of 10.000 groepen, voert u de `reorg` gebruiken voordat u de opdracht `runstats` gebruiken.

## De opdracht runtime gebruiken in uw AEM-formulierdatabase {#use-the-runstats-command-on-your-aem-forms-database}

Voer de `runstats` gebruiken in de volgende AEM formulierdatabasetabellen en -indexen.

>[!NOTE]
>
>De `runstats` bevel moet slechts tijdens de eerste gegevensbestandsynchronisatie in werking worden gesteld. Tijdens dat proces moet het echter twee keer worden uitgevoerd: eenmaal tijdens de synchronisatie van gebruikers en groepen en vervolgens tijdens de synchronisatie van groepsleden. Zorg ervoor dat het script volledig wordt uitgevoerd wanneer u het uitvoert.

Raadpleeg de documentatie van de fabrikant van de database voor de juiste syntaxis en het juiste gebruik. Onder, `<schema>` wordt gebruikt om het schema aan te duiden dat aan uw DB2 gebruikersnaam wordt geassocieerd. Als u een eenvoudige installatie standaardDB2 hebt, is dit de naam van het gegevensbestandschema.

```sql
     TABLE <schema>.EDCPRINCIPALGROUPENTITY
 
     TABLE <schema>.EDCPRINCIPALGRPCTMNTENTITY
 
     TABLE <schema>.EDCPRINCIPALENTITY
 
     TABLE <schema>.EDCPRINCIPALUSERENTITY
 
     TABLE <schema>.EDCPRINCIPALEMAILALIASENTITY
 
     TABLE <schema>.EDCPRINCIPALENTITY FOR INDEXES ALL
 
     TABLE <schema>.EDCPRINCIPALEMAILALIASENTITY FOR INDEXES ALL
 
     TABLE <schema>.EDCPRINCIPALUSERENTITY FOR INDEXES ALL
 
     TABLE <schema>.EDCPRINCIPALGROUPENTITY FOR INDEXES ALL
 
     TABLE <schema>.EDCPRINCIPALGRPCTMNTENTITY FOR INDEXES ALL
```

## Voer de opdracht reorg uit op de database van uw AEM formulieren {#run-the-reorg-command-on-your-aem-forms-database}

Voer de `reorg` gebruiken in de volgende AEM formulierdatabasetabellen en -indexen. Raadpleeg de documentatie van de fabrikant van de database voor de juiste syntaxis en het juiste gebruik.

```sql
     TABLE <schema>.EDCPRINCIPALGROUPENTITY
 
     TABLE <schema>.EDCPRINCIPALGRPCTMNTENTITY
 
     TABLE <schema>.EDCPRINCIPALENTITY
 
     TABLE <schema>.EDCPRINCIPALUSERENTITY
 
     TABLE <schema>.EDCPRINCIPALEMAILALIASENTITY
 
     INDEXES ALL FOR TABLE <schema>.EDCPRINCIPALENTITY
 
     INDEXES ALL FOR TABLE <schema>.EDCPRINCIPALEMAILALIASENTITY
 
     INDEXES ALL FOR TABLE <schema>.EDCPRINCIPALUSERENTITY
 
     INDEXES ALL FOR TABLE <schema>.EDCPRINCIPALGROUPENTITY
 
     INDEXES ALL FOR TABLE <schema>.EDCPRINCIPALGRPCTMNTENTITY
```
