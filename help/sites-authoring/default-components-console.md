---
title: Componentenconsole
description: De console van Componenten laat u door alle componenten doorbladeren die voor uw instantie worden bepaald en zeer belangrijke informatie voor elke component bekijken.
exl-id: d79107b9-dfa4-4e80-870e-0b7ea72f0bc7
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User,Admin,Architect,Developer
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 15%

---

# Componentenconsole{#components-console}

De console van Componenten laat u door alle componenten doorbladeren die voor uw instantie worden bepaald en zeer belangrijke informatie voor elke component bekijken.

Het kan worden benaderd van **Gereedschappen >** **Algemeen >** **Componenten**. In de console zijn de kaart- en de lijstweergave beschikbaar. Omdat er geen boomstructuur voor componenten is, is de kolomweergave niet beschikbaar.

![screen-shot_2019-03-05at113145](assets/screen-shot_2019-03-05at113145.png)

>[!NOTE]
>
>In de componentconsole worden alle componenten in het systeem weergegeven. De [Componentbrowser](/help/sites-authoring/author-environment-tools.md#components-browser) toont componenten die aan auteurs beschikbaar zijn en verbergt om het even welke componentengroepen die met een periode beginnen ( `.`).

## Zoeken {#searching}

Met het pictogram **Alleen content** (linksboven) kunt u het deelvenster **Zoeken** openen om de componenten te zoeken en/of te filteren:

![screen-shot_2019-03-05at113251](assets/screen-shot_2019-03-05at113251.png)

### Componentdetails {#component-details}

Klik op de gewenste bron om details over een specifieke component weer te geven. Drie tabbladen bieden:

* **Eigenschappen**

  ![screen_shot_2018-03-27at165847](assets/screen_shot_2018-03-27at165847.png)

  Op het tabblad Eigenschappen kunt u het volgende doen:

   * De algemene eigenschappen van de component weergeven.
   * Weergeven hoe de [pictogram of afkorting is gedefinieerd](/help/sites-developing/components-basics.md#component-icon-in-touch-ui) voor de component.

      * Als u op de bron van het pictogram klikt, gaat u naar die component.

   * De weergave **Resourcetype** en **Super Type resource** (indien gedefinieerd) voor de component.

      * Als u op het Super Type van Middel klikt, gaat u naar die component.

  >[!NOTE]
  >
  >Omdat `/apps` kan tijdens runtime niet worden bewerkt, is de Componentenconsole alleen-lezen.

* **Beleid**

  ![Beleid](assets/chlimage_1-169.png)

* **Live-gebruik**

  ![Live-gebruik](assets/chlimage_1-170.png)

  >[!CAUTION]
  >
  >Vanwege de aard van de informatie die voor deze weergave wordt verzameld, kan het enige tijd duren voordat deze wordt gesorteerd of weergegeven.

* **Documentatie**

  Als de ontwikkelaar [documentatie voor de component](/help/sites-developing/developing-components.md#documenting-your-component), wordt het weergegeven op de **Documentatie** tab. Als er geen documentatie beschikbaar is, **Documentatie** wordt niet weergegeven.

  ![Documentatie](assets/chlimage_1-171.png)
