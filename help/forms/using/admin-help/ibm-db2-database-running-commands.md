---
title: 'IBM DB2-database: opdrachten voor regelmatig onderhoud uitvoeren'
description: Dit document bevat een lijst met IBM DB2-opdrachten die worden aanbevolen voor regelmatig onderhoud van de database met AEM formulieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 7a4281e7-1544-473a-a471-e9a4c2819a58
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# IBM DB2-database: opdrachten voor regelmatig onderhoud uitvoeren {#ibm-db-database-running-commands-for-regular-maintenance}

De volgende IBM DB2-opdrachten worden aanbevolen voor regelmatig onderhoud van de database met AEM formulieren. Voor gedetailleerde informatie over onderhoud en prestaties het stemmen voor uw gegevensbestand DB2, zie {de Gids van het Beleid van IBM DB2 van 0} *.*

* **loopstaten:** Dit bevel werkt statistieken bij die de fysieke kenmerken van een gegevensbestandlijst, samen met zijn bijbehorende indexen beschrijven. Dynamische SQL-instructies die door AEM formulieren worden gegenereerd, gebruiken automatisch deze bijgewerkte statistieken, maar statische SQL-instructies die in een database zijn gemaakt, vereisen dat de opdracht `db2rbind` ook wordt uitgevoerd.
* **db2rbind:** Dit bevel bindt alle pakketten in het gegevensbestand opnieuw. Gebruik deze opdracht nadat u het hulpprogramma `runstats` hebt uitgevoerd om alle pakketten in de database opnieuw te valideren.
* **reorg lijst of index:** Dit bevel controleert of een reorganisatie van sommige lijsten en indexen wordt vereist.

  Aangezien uw gegevensbestanden groeien en veranderen, is het opnieuw berekenen van lijststatistieken kritiek aan het verbeteren van gegevensbestandprestaties en zou regelmatig moeten worden gedaan. Deze opdrachten kunnen handmatig worden uitgevoerd met behulp van scripts of met behulp van een uitsnijdtaak.

>[!NOTE]
>
>Voordat u de opdracht `runstats` uitvoert, moet de database gegevens bevatten en moet ten minste één directorysynchronisatie zijn uitgevoerd.

Voor een kleine database, zoals voor 10.000 gebruikers of 2.500 groepen, is het voldoende om de opdracht `runstats` aan te roepen om de synchronisatietijdstippen te beperken.

Voor grotere databases, zoals voor 100.000 gebruikers of 10.000 groepen, voert u de opdracht `reorg` uit voordat u de opdracht `runstats` uitvoert.

## De opdracht runtime gebruiken in uw AEM-formulierdatabase {#use-the-runstats-command-on-your-aem-forms-database}

Voer de opdracht `runstats` uit op de volgende AEM formulierdatabasetabellen en -indexen.

>[!NOTE]
>
>De opdracht `runstats` moet alleen worden uitgevoerd tijdens de eerste databasesynchronisatie. Nochtans, moet het tweemaal tijdens dat proces in werking worden gesteld: eens tijdens de synchronisatie van Gebruikers en Groepen en dan tijdens de synchronisatie van de Leden van de Groep. Zorg ervoor dat het script volledig wordt uitgevoerd wanneer u het uitvoert.

Raadpleeg de documentatie van de fabrikant van de database voor de juiste syntaxis en het juiste gebruik. Hieronder wordt `<schema>` gebruikt om het schema aan te geven dat aan uw DB2-gebruikersnaam is gekoppeld. Als u een eenvoudige installatie standaardDB2 hebt, is dit de naam van het gegevensbestandschema.

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
