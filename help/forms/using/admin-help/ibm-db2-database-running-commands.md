---
title: '"IBM DB2-database: Opdrachten uitvoeren voor regelmatig onderhoud"'
seo-title: '"IBM DB2-database: Opdrachten uitvoeren voor regelmatig onderhoud"'
description: Dit document bevat een lijst met IBM DB2-opdrachten die worden aanbevolen voor regelmatig onderhoud van de database met AEM formulieren.
seo-description: Dit document bevat een lijst met IBM DB2-opdrachten die worden aanbevolen voor regelmatig onderhoud van de database met AEM formulieren.
uuid: 235d59df-b9b9-4770-8b7d-00713701c3c2
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: a62b68b4-7735-49b1-8938-f0d9e4c4a051
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---


# IBM DB2-database: Opdrachten uitvoeren voor normaal onderhoud {#ibm-db-database-running-commands-for-regular-maintenance}

De volgende IBM DB2-opdrachten worden aanbevolen voor regelmatig onderhoud van de database met AEM formulieren. Zie *IBM DB2 Administration Guide* voor gedetailleerde informatie over het afstemmen van onderhoud en prestaties voor uw DB2-database.

* **runstats:** Dit bevel werkt statistieken bij die de fysieke kenmerken van een gegevensbestandlijst, samen met zijn bijbehorende indexen beschrijven. Dynamische SQL-instructies die door AEM formulieren worden gegenereerd, gebruiken automatisch deze bijgewerkte statistieken, maar statische SQL-instructies die in een database zijn gemaakt, vereisen dat de opdracht `db2rbind` ook wordt uitgevoerd.
* **db2rbind:** Deze opdracht koppelt alle pakketten in de database opnieuw. Gebruik deze opdracht nadat u het hulpprogramma `runstats` hebt uitgevoerd om alle pakketten in de database opnieuw te valideren.
* **reorg tabel of index:** deze opdracht controleert of een reorganisatie van sommige tabellen en indexen vereist is.

   Aangezien uw gegevensbestanden groeien en veranderen, is het opnieuw berekenen van lijststatistieken kritiek aan het verbeteren van gegevensbestandprestaties en zou regelmatig moeten worden gedaan. Deze opdrachten kunnen handmatig worden uitgevoerd met behulp van scripts of met behulp van een uitsnijdtaak.

>[!NOTE]
>
>Voordat u de opdracht `runstats` uitvoert, moet de database gegevens bevatten en moet ten minste één directorysynchronisatie zijn uitgevoerd.

Voor een klein gegevensbestand, zoals voor 10.000 gebruikers of 2.500 groepen, is het voldoende om `runstats` bevel aan te halen om de synchronisatietijdopties te verminderen.

Voor grotere gegevensbestanden, zoals voor 100.000 gebruikers of 10.000 groepen, stel `reorg` bevel in werking alvorens u `runstats` bevel in werking stelt.

## Gebruik het bevel van runtime op uw AEM vormengegevensbestand {#use-the-runstats-command-on-your-aem-forms-database}

Voer de opdracht `runstats` uit op de volgende AEM formulierdatabasetabellen en -indexen.

>[!NOTE]
>
>Het `runstats` bevel moet slechts tijdens de eerste gegevensbestandsynchronisatie worden in werking gesteld. Tijdens dat proces moet het echter twee keer worden uitgevoerd: eenmaal tijdens de synchronisatie van gebruikers en groepen en vervolgens tijdens de synchronisatie van groepsleden. Zorg ervoor dat het script volledig wordt uitgevoerd wanneer u het uitvoert.

Raadpleeg de documentatie van de fabrikant van de database voor de juiste syntaxis en het juiste gebruik. Hieronder, wordt `<schema>` gebruikt om het schema aan te duiden dat met uw DB2 gebruikersnaam wordt geassocieerd. Als u een eenvoudige installatie standaardDB2 hebt, is dit de naam van het gegevensbestandschema.

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

## Voer de opdracht reorg uit op de AEM formulierdatabase {#run-the-reorg-command-on-your-aem-forms-database}

Voer de opdracht `reorg` uit op de volgende AEM formulierdatabasetabellen en -indexen. Raadpleeg de documentatie van de fabrikant van de database voor de juiste syntaxis en het juiste gebruik.

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

