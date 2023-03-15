---
title: Onderdelenconsole
seo-title: Components Console
description: Onderdelenconsole
seo-description: null
uuid: a4e34d81-7875-4e26-8b48-4473e2905c37
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: b657f95d-7be3-4409-a31b-d47fb2bfa550
docset: aem65
exl-id: d79107b9-dfa4-4e80-870e-0b7ea72f0bc7
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 22%

---

# Onderdelenconsole{#components-console}

Met de componentenconsole kunt u door alle componenten bladeren die voor uw instantie zijn gedefinieerd en sleutelinformatie voor elke component bekijken.

U kunt deze openen via **Gereedschappen ->** **Algemeen ->** **Componenten**. In de console zijn de kaart- en de lijstweergave beschikbaar. Omdat er geen boomstructuur voor componenten is, is de kolomweergave niet beschikbaar.

![screen-shot_2019-03-05at113145](assets/screen-shot_2019-03-05at113145.png)

>[!NOTE]
>
>In de componentconsole worden alle componenten in het systeem weergegeven. De [Componentbrowser](/help/sites-authoring/author-environment-tools.md#components-browser) toont componenten die aan auteurs beschikbaar zijn en verbergt om het even welke componentengroepen die met een periode beginnen ( `.`).

## Zoeken {#searching}

Met het pictogram **Alleen content** (linksboven) kunt u het deelvenster **Zoeken** openen om de componenten te zoeken en/of te filteren:

![screen-shot_2019-03-05at113251](assets/screen-shot_2019-03-05at113251.png)

### Componentdetails {#component-details}

Als u details over een bepaalde component wilt weergeven, tikt u op de gewenste bron of klikt u op deze. Drie tabbladen bieden:

* **Eigenschappen**

   ![screen_shot_2018-03-27at165847](assets/screen_shot_2018-03-27at165847.png)

   Op het tabblad Eigenschappen kunt u het volgende doen:

   * De algemene eigenschappen van de component weergeven.
   * Weergeven hoe de [pictogram of afkorting is gedefinieerd](/help/sites-developing/components-basics.md#component-icon-in-touch-ui) voor de component.

      * Als u op de bron van het pictogram klikt, gaat u naar die component.
   * De weergave van **Type bron** en **Super Type resource** (indien gedefinieerd) voor de component.

      * Als u op het Super Type van Middel klikt, gaat u naar die component.
   >[!NOTE]
   >
   >Omdat `/apps` kan tijdens runtime niet worden bewerkt, is de Componentenconsole alleen-lezen.

* **Beleid**

   ![chlimage_1-169](assets/chlimage_1-169.png)

* **Live-gebruik**

   ![chlimage_1-170](assets/chlimage_1-170.png)

   >[!CAUTION]
   >
   >Vanwege de aard van de informatie die voor deze weergave wordt verzameld, kan het enige tijd duren voordat deze wordt gesorteerd of weergegeven.

* **Documentatie**

   Als de ontwikkelaar [documentatie voor de component](/help/sites-developing/developing-components.md#documenting-your-component), verschijnt het op de **Documentatie** tab. Als er geen documentatie beschikbaar is, **Documentatie** wordt niet weergegeven.

   ![chlimage_1-171](assets/chlimage_1-171.png)
