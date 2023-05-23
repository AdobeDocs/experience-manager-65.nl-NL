---
title: Validatieberichten configureren
seo-title: Configuring validation messages
description: Leer hoe u opgeeft hoe validatieberichten worden weergegeven en waar deze zich bevinden ten opzichte van het formulier dat wordt geretourneerd in de webbrowser.
seo-description: Learn how to specify how validation messages are displayed and their location relative to the form returned in the web browser.
uuid: f6bff4fa-f90f-4135-ae40-7ab3d3613122
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 5f2f8129-e45e-4f3f-ae30-c09330d0e152
exl-id: 14314383-5228-4904-98c1-586f48a1142c
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# Validatieberichten configureren {#configuring-validation-messages}

Voor formulieren die als HTML worden weergegeven, worden validatiefouten voor formulieren weergegeven die optreden voor de gebruiker. U kunt de weergave van validatieberichten aanpassen. Afhankelijk van waar de validatieberichten worden weergegeven, kunt u ook de locatie van het bericht in het formulier en de grootte van de framerand bepalen.

## Opgeven hoe validatieberichten worden weergegeven {#specify-how-validation-messages-are-displayed}

1. Klik in de beheerconsole op Services > Formulieren.
1. Selecteer onder Uitvoer validatie in de lijst Rapportage een van de volgende opties:

   **Berichtvenster:** Validatieberichten weergeven in een afzonderlijk dialoogvenster.

   **Frame:** Validatieberichten weergeven in een kader van hetzelfde venster.

   **Geen kader:** Validatieberichten weergeven in hetzelfde venster. Dit is de standaardwaarde.

   **Via API (met gegevens):** De validatieberichten retourneren via de API (met gegevens). De validatieberichten worden niet op het scherm weergegeven.

   **Via API (met formulier):** De validatieberichten retourneren via de API (met het formulier). De validatieberichten worden niet op het scherm weergegeven.

   **Geen:** Validatieberichten niet weergeven.

1. Klik op Opslaan.

## De locatie van validatieberichten opgeven ten opzichte van het formulier dat wordt geretourneerd in de webbrowser {#specify-the-location-of-validation-messages-relative-to-the-form-returned-in-the-web-browser}

Wanneer Rapportage is ingesteld op Frame of Geen frame, kunt u de locatie van validatieberichten opgeven.

1. Selecteer onder Uitvoer validatie in de lijst Positie een van de volgende opties:

   **Links:** Validatieberichten links in de webbrowser weergeven.

   **Rechts:** Validatieberichten weergeven aan de rechterkant van de webbrowser.

   **Boven**: Validatieberichten boven aan de webbrowser weergeven. Dit is de standaardwaarde.

   **Onder**: Validatieberichten onder aan de webbrowser weergeven.

1. Klik op Opslaan.

## De grootte van de framerand opgeven {#specify-the-frame-border-size}

Wanneer Rapportage is ingesteld op Frame, kunt u de grootte van de framerand opgeven.

1. Typ onder Uitvoer validatie in het vak Randgrootte de grootte van de framerand, in pixels.

   De randgrootte moet gelijk zijn aan of groter zijn dan 0. De standaardwaarde is 1.

1. Klik op Opslaan.
