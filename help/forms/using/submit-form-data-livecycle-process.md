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
feature: Adaptive Forms
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# AEM Forms configureren om formuliergegevens via JEE naar een AEM formulier te verzenden{#configuring-aem-forms-to-submit-form-data-to-an-aem-forms-on-jee-process}

Adaptieve formulieren ondersteunen het verzenden van gegevens naar AEM Forms over JEE-processen voor verdere verwerking. Hiermee kunt u een AEM Forms on JEE-proces activeren met de gegevens die beschikbaar zijn in het verzonden formulier. Voer de volgende stappen uit zodat u uw AEM Forms-exemplaar kunt inschakelen om een adaptief formulier naar AEM Forms te verzenden tijdens het JEE-proces:

## AEM Forms-server configureren {#configure-your-aem-forms-server}

Voer de volgende stappen uit zodat u uw AEM Forms Server kunt inschakelen om gegevens naar een AEM Forms op de JEE-server te verzenden:

1. Ga naar AEM console van de Webconfiguratie in https:// [*gastheer*]:[*haven*]/system/console/configMgr.

1. Bepaal en klik de **component van de Configuratie van SDK van de Cliënt van het LiveCycle van de Adobe**.
1. Klik hierop om de URL van de configuratieserver, de gebruikersnaam en het wachtwoord voor de AEM Forms op de JEE-server te bewerken.
1. Herzie de montages en klik **sparen**.

![&#x200B; de configuratie van SDK van de Cliënt van het LiveCycle van de Adobe &#x200B;](assets/clientsdkconfiguration.jpg)

## Gegevens toewijzen aan procesvelden {#map-data-with-process-fields}

Nadat u AEM Forms hebt geconfigureerd, wijst u de XML-gegevens en bijlagen van het verzonden formulier toe aan de velden in het AEM Forms on JEE-proces. Ga als volgt te werk:

1. In de AEM console van de Webconfiguratie, klik om de **Locator van het Proces van het LiveCycle van de Gids en de Configuratie van de Invoker** uit te geven.
1. Geef de volgende parameters op:

   * **Naam van de gegevensxml parameter** (verplicht): specificeer het het bezitsdossier van XML van AEM Forms op proces JEE dat de voorgelegde gegevens moet verwerken. De standaardwaarde is dataxml **&#x200B;**.

   * **Naam van de parameter van dossiergehechtheid** (facultatief): specificeer de lijst van documentvoorwerpen die AEM Forms op JEE proces moet verwerken. De standaardwaarde is **fileAttachmentsList**.

1. Herzie de montages en klik **sparen**.

![&#x200B; Locator en Invoker van het Proces van de Gids LiveCycle &#x200B;](assets/test3.jpg)

Zodra gevormd, legt de Verzenden aan Forms Workflow actie een lijst voor van AEM Forms op JEE serverprocessen die de gespecificeerde gegevens xml parameter bevatten.
