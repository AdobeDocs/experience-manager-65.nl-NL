---
title: 'Microsoft SQL Server-database: de configuratie verfijnen'
description: Leer hoe u de configuratie van uw Microsoft SQL gegevensbestand van de Server kunt verfijnen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.5/FORMS, SG_AEMFORMS
exl-id: 9c570827-86e2-47d5-b8ae-66c0767bff2e
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 0%

---

# Microsoft SQL Server-database: de configuratie verfijnen {#microsoft-sql-server-database-fine-tuning-the-configuration}

U zou de standaardconfiguratiemontages moeten veranderen wanneer het gebruiken van de Server van Microsoft SQL. Klik met de rechtermuisknop op de lokale server in Oracle Enterprise Manager om het dialoogvenster met eigenschappen te openen.

## Geheugeninstellingen {#memory-settings}

Wijzig de minimale geheugentoewijzing in een zo groot mogelijk aantal. Als de database op een aparte computer wordt uitgevoerd, gebruikt u al het geheugen. Bij de standaardinstellingen wordt geen agressief geheugen toegewezen, waardoor de prestaties in vrijwel elke database worden belemmerd. U zou het meest agressief moeten zijn in het toewijzen van geheugen op productiemachines.

## Processorinstellingen {#processor-settings}

Wijzig de bewerkermontages en, het belangrijkst, selecteer de Prioriteit van de Server van de Verhoging SQL op de controledoos van Vensters zodat de server zoveel mogelijk cycli gebruikt. De instelling NT-vezels gebruiken is minder belangrijk, maar u kunt deze ook selecteren.

## Database-instellingen {#database-settings}

Wijzig de database-instellingen. De belangrijkste instelling is Herstelinterval, dat de maximale tijd opgeeft die moet worden gewacht op herstel na een crash. De standaardinstelling is één minuut. Als u een hogere waarde gebruikt, van 5 tot 15 minuten, verbetert u de prestaties omdat de server hierdoor meer tijd krijgt om wijzigingen te schrijven van het databaselogbestand naar de databasebestanden.

>[!NOTE]
>
>Deze instelling brengt het transactiegedrag niet in gevaar, omdat alleen de lengte van het opnieuw afspelen van het logbestand wordt gewijzigd die bij het opstarten moet worden uitgevoerd.

Stel de grootte voor de toegewezen ruimte voor zowel het logbestand als het gegevensbestand in op een veel grotere ruimte dan de oorspronkelijke database. Bedenk hoeveel de database over een jaar kan groeien. In het ideale geval worden het logbestand en de gegevensbestanden aaneengesloten toegewezen, zodat de gegevens niet over de gehele schijf worden gefragmenteerd.
