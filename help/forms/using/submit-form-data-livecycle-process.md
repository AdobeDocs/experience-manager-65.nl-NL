---
title: AEM Forms configureren voor het verzenden van gegevens naar een AEM Forms on JEE-proces
description: Aangepaste formulieren integreren met AEM Forms in JEE-processen voor de verwerking van formuliergegevens.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
docset: aem65
role: Admin, User, Developer
exl-id: 025a3314-8b9d-48e1-a74f-ea0c933e21e3
solution: Experience Manager, Experience Manager Forms
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# AEM Forms configureren om formuliergegevens via JEE naar een AEM formulier te verzenden{#configuring-aem-forms-to-submit-form-data-to-an-aem-forms-on-jee-process}

Adaptieve formulieren ondersteunen het verzenden van gegevens naar AEM Forms over JEE-processen voor verdere verwerking. Hiermee kunt u een AEM Forms on JEE-proces activeren met de gegevens die beschikbaar zijn in het verzonden formulier. Voer de volgende stappen uit zodat u uw AEM Forms-exemplaar kunt inschakelen om een adaptief formulier naar AEM Forms te verzenden tijdens het JEE-proces:

## AEM Forms-server configureren {#configure-your-aem-forms-server}

Voer de volgende stappen uit zodat u uw AEM Forms Server kunt inschakelen om gegevens naar een AEM Forms op de JEE-server te verzenden:

1. Ga naar AEM webconfiguratieconsole op https://[*host*]:[*poort*]/system/console/configMgr.

1. Ga naar de **Adobe LiveCycle client SDK Configuration** component.
1. Klik hierop om de URL van de configuratieserver, de gebruikersnaam en het wachtwoord voor de AEM Forms op de JEE-server te bewerken.
1. Controleer de instellingen en klik op **Opslaan**.

![Adobe LiveCycle client SDK configuratie](assets/clientsdkconfiguration.jpg)

## Gegevens toewijzen aan procesvelden {#map-data-with-process-fields}

Nadat u AEM Forms hebt geconfigureerd, wijst u de XML-gegevens en bijlagen van het verzonden formulier toe aan de velden in het AEM Forms on JEE-proces. Ga als volgt te werk:

1. Klik in de AEM webconfiguratieconsole om de **Locator en aanroeper van procesprocessen voor hulplijnen** configuratie.
1. Geef de volgende parameters op:

   * **Naam van de parameter data xml** (verplicht): geef het XML-eigenschappenbestand op van het AEM Forms on JEE-proces dat de verzonden gegevens moet verwerken. De standaardwaarde is **dataxml**.

   * **Naam van de parameter voor bestandsbijlagen** (optioneel): geef de lijst op met documentobjecten die het AEM Forms on JEE-proces moet verwerken. De standaardwaarde is **fileAttachmentsList**.

1. Controleer de instellingen en klik op **Opslaan**.

![Locator en aanroeper van procesprocessen voor hulplijnen](assets/test3.jpg)

Zodra gevormd, legt de Verzenden aan Forms Workflow actie een lijst voor van AEM Forms op JEE serverprocessen die de gespecificeerde gegevens xml parameter bevatten.
