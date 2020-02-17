---
title: AEM-formulieren configureren voor het verzenden van formuliergegevens naar AEM Forms on JEE-processen
seo-title: AEM-formulieren configureren voor het verzenden van formuliergegevens naar AEM Forms on JEE-processen
description: Met AEM Forms kunt u adaptieve formulieren met AEM Forms integreren in JEE-processen voor de verwerking van formuliergegevens.
seo-description: Met AEM Forms kunt u adaptieve formulieren met AEM Forms integreren in JEE-processen voor de verwerking van formuliergegevens.
uuid: 71a894d7-7c0a-43a6-afe5-40c4a15c66d6
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
discoiquuid: ff97424d-b384-4149-9a3c-b4f00aaa1def
docset: aem65
translation-type: tm+mt
source-git-commit: 8e724af4d69cb859537dd088119aaca652ea3931

---


# AEM-formulieren configureren voor het verzenden van formuliergegevens naar AEM Forms on JEE-processen{#configuring-aem-forms-to-submit-form-data-to-an-aem-forms-on-jee-process}

Adaptieve formulieren ondersteunen het verzenden van gegevens naar een AEM Forms on JEE-proces voor verdere verwerking. Hiermee kunt u een AEM Forms op JEE-proces activeren met de gegevens die beschikbaar zijn in het verzonden formulier. Voer de volgende stappen uit om uw AEM Forms-instantie in staat te stellen een adaptief formulier naar AEM Forms on JEE-proces te verzenden:

## Uw AEM Forms-server configureren {#configure-your-aem-forms-server}

Voer de volgende stappen uit om uw AEM-formulierserver in staat te stellen gegevens naar een AEM-formulier op de JEE-server te verzenden:

1. Ga naar AEM webconfiguratieconsole op https://[*host*]:[*poort*]/systeem/console/configMgr.

1. Zoek en klik op de **Adobe LiveCycle Client SDK Configuration** -component.
1. Klik hierop om de URL van de configuratieserver, de gebruikersnaam en het wachtwoord voor de AEM-formulieren op de JEE-server te bewerken.
1. Controleer de instellingen en klik op **Opslaan**.

![Configuratie van de Adobe LiveCycle Client SDK](assets/clientsdkconfiguration.jpg)

## Gegevens toewijzen aan procesvelden {#map-data-with-process-fields}

Nadat uw AEM-formulieren zijn geconfigureerd, wijst u de XML-gegevens en bijlagen van het verzonden formulier toe aan de velden in het AEM Forms on JEE-proces. Dit doet u als volgt:

1. Klik in de AEM-webconfiguratieconsole om de configuratie van de **Guide LiveCycle Process Locator en Invoker** te bewerken.
1. Geef de volgende parameters op:

   * **Naam van de parameter** data xml (verplicht): Geef het XML-eigenschappenbestand op van het AEM Forms on JEE-proces dat de verzonden gegevens moet verwerken. The default value is **dataxml**.

   * **Naam van de parameter** voor bestandsbijlagen (optioneel): Geef de lijst op met documentobjecten die het AEM Forms on JEE-proces moet verwerken. The default value is **fileAttachmentsList**.

1. Controleer de instellingen en klik op **Opslaan**.

![Geleider LiveCycle Process Locator en Invoker](assets/test3.jpg)

Als deze optie eenmaal is geconfigureerd, wordt bij de verzendactie Verzenden naar Forms Workflow een lijst weergegeven met de AEM-formulieren op JEE-serverprocessen die de opgegeven XML-gegevensparameter bevatten.
