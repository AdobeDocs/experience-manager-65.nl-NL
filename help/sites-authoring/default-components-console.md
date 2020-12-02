---
title: Onderdelenconsole
seo-title: Onderdelenconsole
description: 'null'
seo-description: 'null'
uuid: a4e34d81-7875-4e26-8b48-4473e2905c37
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: b657f95d-7be3-4409-a31b-d47fb2bfa550
docset: aem65
translation-type: tm+mt
source-git-commit: 4dc4a518c212555b7833ac27de02087a403d3517
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 23%

---


# Onderdelenconsole{#components-console}

Met de componentenconsole kunt u door alle componenten bladeren die voor uw instantie zijn gedefinieerd en sleutelinformatie voor elke component bekijken.

U kunt deze openen via **Gereedschappen ->** **Algemeen ->** **Componenten**. In de console zijn de kaart- en de lijstweergave beschikbaar. Omdat er geen boomstructuur voor componenten is, is de kolomweergave niet beschikbaar.

![screen-shot_2019-03-05at113145](assets/screen-shot_2019-03-05at113145.png)

>[!NOTE]
>
>In de componentconsole worden alle componenten in het systeem weergegeven. In de [Componentbrowser](/help/sites-authoring/author-environment-tools.md#components-browser) worden componenten weergegeven die beschikbaar zijn voor auteurs en worden componentgroepen verborgen die met een punt ( `.`) beginnen.

## Zoeken {#searching}

Met het pictogram **Alleen content** (linksboven) kunt u het deelvenster **Zoeken** openen om de componenten te zoeken en/of te filteren:

![screen-shot_2019-03-05at113251](assets/screen-shot_2019-03-05at113251.png)

### Componentdetails {#component-details}

Als u details over een bepaalde component wilt weergeven, tikt u op de gewenste bron of klikt u op deze. Drie tabbladen bieden:

* **Eigenschappen**

   ![screen_shot_2018-03-27at165847](assets/screen_shot_2018-03-27at165847.png)

   Op het tabblad Eigenschappen kunt u het volgende doen:

   * De algemene eigenschappen van de component weergeven.
   * Bekijk hoe het pictogram of de afkorting [is gedefinieerd](/help/sites-developing/components-basics.md#component-icon-in-touch-ui) voor de component.

      * Als u op de bron van het pictogram klikt, gaat u naar die component.
   * Bekijk **Resourcetype** en **Resourcesupertype** (indien gedefinieerd) voor de component.

      * Als u op het Super Type van Middel klikt, gaat u naar die component.
   >[!NOTE]
   >
   >Omdat `/apps` niet bewerkbaar is bij uitvoering, is de Componentenconsole alleen-lezen.

* **Beleid**

   ![chlimage_1-169](assets/chlimage_1-169.png)

* **Live-gebruik**

   ![chlimage_1-170](assets/chlimage_1-170.png)

   >[!CAUTION]
   >
   >Vanwege de aard van de informatie die voor deze weergave wordt verzameld, kan het enige tijd duren voordat deze wordt gesorteerd of weergegeven.

* **Documentatie**

   Als de ontwikkelaar [documentatie voor de component](/help/sites-developing/developing-components.md#documenting-your-component) heeft verstrekt, zal het op **Documentatie** tabel verschijnen. Als er geen documentatie beschikbaar is, zal **Documentatie** tabel niet worden getoond.

   ![chlimage_1-171](assets/chlimage_1-171.png)

