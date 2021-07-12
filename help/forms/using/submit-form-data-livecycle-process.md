---
title: AEM Forms configureren voor het verzenden van formuliergegevens naar een AEM Forms tijdens JEE-proces
seo-title: AEM Forms configureren voor het verzenden van formuliergegevens naar een AEM Forms tijdens JEE-proces
description: Met AEM Forms kunt u adaptieve formulieren integreren met AEM Forms op JEE-processen voor de verwerking van formuliergegevens.
seo-description: Met AEM Forms kunt u adaptieve formulieren integreren met AEM Forms op JEE-processen voor de verwerking van formuliergegevens.
uuid: 71a894d7-7c0a-43a6-afe5-40c4a15c66d6
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
discoiquuid: ff97424d-b384-4149-9a3c-b4f00aaa1def
docset: aem65
role: Admin
exl-id: 025a3314-8b9d-48e1-a74f-ea0c933e21e3
source-git-commit: 603518dbe3d842a08900ac40651919c55392b573
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# AEM Forms configureren voor het verzenden van formuliergegevens naar een AEM Forms tijdens JEE-proces{#configuring-aem-forms-to-submit-form-data-to-an-aem-forms-on-jee-process}

Adaptieve formulieren ondersteunen het verzenden van gegevens naar een AEM Forms on JEE-proces voor verdere verwerking. Hiermee kunt u een AEM Forms op JEE-proces activeren met de gegevens die beschikbaar zijn in het verzonden formulier. Voer de volgende stappen uit om uw AEM Forms-exemplaar in staat te stellen een adaptief formulier naar AEM Forms te verzenden bij JEE-proces:

## AEM Forms-server configureren {#configure-your-aem-forms-server}

Voer de volgende stappen uit om uw AEM formulierserver in staat te stellen gegevens naar een AEM Forms op de JEE-server te verzenden:

1. Ga naar AEM webconfiguratieconsole op https://[*host*]:[*port*]/system/console/configMgr.

1. Zoek en klik op de **Adobe LiveCycle client SDK Configuration**-component.
1. Klik hierop om de URL van de configuratieserver, de gebruikersnaam en het wachtwoord voor de AEM Forms op de JEE-server te bewerken.
1. Controleer de instellingen en klik op **Opslaan**.

![Adobe LiveCycle Client SDK-configuratie](assets/clientsdkconfiguration.jpg)

## Gegevens toewijzen aan procesvelden {#map-data-with-process-fields}

Nadat uw AEM Forms is geconfigureerd, wijst u de XML-gegevens en bijlagen van het verzonden formulier toe aan de velden in het AEM Forms on JEE-proces. Dit doet u als volgt:

1. In de AEM console van de Webconfiguratie, klik om de **Locator van het Proces van de LiveCycle van de Gids en Invoker** configuratie uit te geven.
1. Geef de volgende parameters op:

   * **Naam van de parameter**  data xml (verplicht): Geef het XML-eigenschappenbestand op van het AEM Forms on JEE-proces dat de verzonden gegevens moet verwerken. De standaardwaarde is **dataxml**.

   * **Naam van de parameter**  voor bestandsbijlagen (optioneel): Geef de lijst op met documentobjecten die het AEM Forms on JEE-proces moet verwerken. De standaardwaarde is **fileAttachmentsList**.

1. Controleer de instellingen en klik op **Opslaan**.

![Geleider LiveCycle Process Locator en Invoker](assets/test3.jpg)

Zodra gevormd, legt de Verzenden aan Forms Workflow actie een lijst voor van AEM Forms op JEE serverprocessen die de gespecificeerde gegevens xml parameter bevatten.
