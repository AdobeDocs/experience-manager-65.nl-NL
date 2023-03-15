---
title: Adaptieve sjabloonrendering
seo-title: Adaptive Template Rendering
description: Adaptieve sjabloonrendering
seo-description: null
uuid: 97226ae1-e42a-40ae-a5e0-886cd77559d8
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: f5cb0e98-0d6e-4f14-9b94-df1a9d8cbe5b
exl-id: 58cac3b1-b7cd-44b2-b89b-f5ee8811c198
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# Adaptieve sjabloonrendering{#adaptive-template-rendering}

De adaptieve sjabloonrendering biedt een manier om een pagina met variaties te beheren. Oorspronkelijk handig om verschillende HTML-uitvoer voor mobiele apparaten te leveren (bijvoorbeeld functielefoon versus smartphone), is deze functie nuttig wanneer ervaringen moeten worden geleverd aan verschillende apparaten die verschillende markeringen of HTML-uitvoer nodig hebben.

## Overzicht {#overview}

De malplaatjes worden over het algemeen gebouwd rond een ontvankelijk net, en de pagina&#39;s die op deze malplaatjes worden gecreeerd volledig ontvankelijk zijn, die automatisch aan viewport van het cliëntapparaat aanpassen. Met behulp van de werkbalk Emulator in de pagina-editor kunnen auteurs lay-outs richten op specifieke apparaten.

Het is ook mogelijk om sjablonen in te stellen ter ondersteuning van adaptieve rendering. Wanneer apparaatgroepen correct zijn geconfigureerd, wordt de pagina weergegeven met een andere kiezer in de URL wanneer een apparaat wordt geselecteerd in de emulatormodus. Met behulp van een kiezer kan een specifieke pagina-rendering rechtstreeks via de URL worden aangeroepen.

Onthoud dat u apparaatgroepen instelt:

* Elk apparaat moet in minstens één apparatengroep zijn.
* Een apparaat kan zich in meerdere apparaatgroepen bevinden.
* Omdat apparaten zich in meerdere apparaatgroepen kunnen bevinden, kunnen kiezers worden gecombineerd.
* De combinatie van kiezers wordt van boven naar beneden geëvalueerd, aangezien ze in de opslagplaats blijven bestaan.

>[!NOTE]
>
>De apparaatgroep **Responsieve apparaten** zal nooit een kiezer hebben omdat apparaten die herkend worden als ondersteuning voor een responsief ontwerp, verondersteld worden geen adaptieve lay-out te hebben

## Configuratie {#configuration}

Aangepaste renderingkiezers kunnen worden geconfigureerd voor bestaande apparaatgroepen of voor [groepen die u zelf hebt gemaakt.](/help/sites-developing/mobile.md#device-groups)

Voor dit voorbeeld gaan we de bestaande apparaatgroep configureren **Slimme telefoons** om een aangepaste renderingkiezer als onderdeel van de **Experience Page** template in We.Retail.

1. Bewerk de apparaatgroep waarvoor een adaptieve kiezer nodig is in `http://localhost:4502/miscadmin#/etc/mobile/groups`

   De optie instellen **Emulator uitschakelen** en opslaan.

   ![chlimage_1-157](assets/chlimage_1-157.png)

1. De kiezer is beschikbaar voor de **Blackberry** en **iPhone 4** voorzien de apparatengroep **Slimme telefoon** wordt in de volgende stappen toegevoegd aan de sjabloon- en paginastructuren.

   ![chlimage_1-158](assets/chlimage_1-158.png)

1. Gebruikend CRX DE Lite, sta de apparatengroep toe die op uw malplaatje wordt gebruikt door het aan het multi-waardebezit van het koord toe te voegen `cq:deviceGroups` over de structuur van de sjabloon.

   `/conf/<your-site>/settings/wcm/templates/<your-template>/structure/jcr:content`

   Als we bijvoorbeeld de apparaatgroep Slimme telefoon willen toevoegen:

   `/conf/we-retail/settings/wcm/templates/experience-page/structure/jcr:content`

   ![chlimage_1-159](assets/chlimage_1-159.png)

1. Gebruikend CRX DE Lite, sta de apparatengroep toe om op uw plaats worden gebruikt door het aan het multi-waardebezit van het koord toe te voegen `cq:deviceGroups` op de structuur van uw site.

   `/content/<your-site>/jcr:content`

   Als we bijvoorbeeld de **Slimme telefoon** apparaatgroep:

   `/content/we-retail/jcr:content`

   ![chlimage_1-160](assets/chlimage_1-160.png)

Nu wanneer u de [emulator](/help/sites-authoring/responsive-layout.md#layout-definitions-device-emulation-and-breakpoints) in de pagina-editor (bijvoorbeeld wanneer [de lay-out wijzigen](/help/sites-authoring/responsive-layout.md)) en u kiest een apparaat van de geconfigureerde apparaatgroep, wordt de pagina weergegeven met een kiezer als onderdeel van de URL.

In ons voorbeeld, wanneer het uitgeven van een pagina die op **Experience Page** sjabloon, en iPhone 4 kiezen in de emulator, wordt de pagina weergegeven inclusief de kiezer als `arctic-surfing-in-lofoten.smart.html` in plaats van `arctic-surfing-in-lofoten.html`

De pagina kan ook rechtstreeks worden aangeroepen met deze kiezer.

![chlimage_1-161](assets/chlimage_1-161.png)
