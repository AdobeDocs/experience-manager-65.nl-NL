---
title: Validatieberichten configureren
description: Leer hoe u opgeeft hoe validatieberichten worden weergegeven en waar deze zich bevinden ten opzichte van het formulier dat wordt geretourneerd in de webbrowser.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 14314383-5228-4904-98c1-586f48a1142c
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Validatieberichten configureren {#configuring-validation-messages}

Voor formulieren die als HTML worden gegenereerd, worden validatiefouten voor formulieren weergegeven die optreden voor de gebruiker. U kunt de weergave van validatieberichten aanpassen. Afhankelijk van de locatie waar de validatieberichten worden weergegeven, kunt u ook de locatie van het bericht in het formulier en de grootte van de framerand bepalen.

## Opgeven hoe validatieberichten worden weergegeven {#specify-how-validation-messages-are-displayed}

1. Klik in de beheerconsole op Services > Formulieren.
1. Selecteer onder Uitvoer validatie in de lijst Rapportage een van de volgende opties:

   **vakje van het Bericht:** om bevestigingsberichten in een afzonderlijk dialoogvakje te tonen.

   **Kader:** om bevestigingsberichten binnen een kader van het zelfde venster te tonen.

   **Geen Kader:** om bevestigingsberichten in het zelfde venster te tonen. Dit is de standaardwaarde.

   **Via API (met gegevens):** om de bevestigingsberichten door API (met gegevens) terug te keren. De validatieberichten worden niet op het scherm weergegeven.

   **Via API (met vorm):** om de bevestigingsberichten door API (met de vorm) terug te keren. De validatieberichten worden niet op het scherm weergegeven.

   **niets:** om bevestigingsberichten niet te tonen.

1. Klik op Opslaan.

## De locatie van validatieberichten opgeven ten opzichte van het formulier dat wordt geretourneerd in de webbrowser {#specify-the-location-of-validation-messages-relative-to-the-form-returned-in-the-web-browser}

Wanneer Rapportage is ingesteld op Frame of Geen frame, kunt u de locatie van validatieberichten opgeven.

1. Selecteer onder Uitvoer validatie in de lijst Positie een van de volgende opties:

   **Linker:** om bevestigingsberichten op de linkerkant van Webbrowser te tonen.

   **juist:** om bevestigingsberichten op de rechterkant van Webbrowser te tonen.

   **Hoogste**: Om bevestigingsberichten bij de bovenkant van Webbrowser te tonen. Dit is de standaardwaarde.

   **Onder**: Om bevestigingsberichten bij de bodem van Webbrowser te tonen.

1. Klik op Opslaan.

## De grootte van de framerand opgeven {#specify-the-frame-border-size}

Wanneer Rapportage is ingesteld op Frame, kunt u de grootte van de framerand opgeven.

1. Typ onder Uitvoer validatie in het vak Randgrootte de grootte van de framerand, in pixels.

   De randgrootte moet gelijk zijn aan of groter zijn dan 0. De standaardwaarde is 1.

1. Klik op Opslaan.
