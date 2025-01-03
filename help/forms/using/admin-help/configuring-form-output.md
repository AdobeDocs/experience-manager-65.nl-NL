---
title: Formulieruitvoer configureren
description: Leer hoe u formulieruitvoer configureert. Gebruik de aangepaste scripts voordat u het formulier verzendt om de formulieruitvoer te configureren en de functie in te schakelen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: d739806c-ce72-40fd-b304-3262a0988d96
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 6a9806d8f40f711a610c130c63d9ab9b2460d075
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# Formulieruitvoer configureren{#configuring-form-output}

## Geef het type HTML-uitvoer op dat wordt geretourneerd aan de webbrowser {#specify-the-type-of-html-output-returned-to-the-web-browser}

1. Klik in de beheerconsole op Services > Formulieren.
1. Selecteer onder Uitvoer formulier in de lijst Uitvoertype een van de volgende opties:

   **Volledige HTML:** om de vorm binnen volledige HTML markeringen (een volledige HTML pagina) terug te geven. Dit is de standaardwaarde.

   **het lichaam van de Vorm:** om de vorm binnen `<BODY>` markeringen (niet een volledige pagina van de HTML terug te geven).

1. Klik op Opslaan.

## De locatie opgeven waar PDF-inhoud wordt gerenderd {#specify-the-location-where-pdf-content-is-rendered}

1. Selecteer onder Formulieruitvoer in de lijst Renderen op een van de volgende opties:

   **Cliënt:** om PDF forms binnen Adobe Acrobat of Adobe Reader terug te geven. Rendering op de client verbetert de prestaties van AEM formulieren en is alleen van toepassing op PDFForm-transformatie.

   **Server:** om PDF forms op de toepassingsserver terug te geven.

   **Auto:** om de vorm van de PDF in de plaats terug te geven die door de `dynamicRender` configuratiewaarde van het XDP dossier wordt gespecificeerd. Dit is de standaardwaarde.

1. Klik op Opslaan.

## Aanroeping van aangepaste scripts configureren voordat het formulier wordt verzonden {#configuring-invocation-of-custom-scripts-before-form-submit}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

Voer de volgende stappen uit om de functie in te schakelen:

1. Aanmelden bij de beheerconsole.
1. Ga naar **Diensten** > **vormen**.
1. Geef het uitvoertype op als Formulierhoofdtekst.
1. Sla de instellingen op.
1. Declareer een variabele van JavaScript, __CUSTOM_SCRIPTS_VERSION, in de hoofdsectie van de code van de HTML en plaats zijn waarde aan 1.

   >[!NOTE]
   >
   >*om de eigenschap onbruikbaar te maken, kunt u de variabele van JavaScript verwijderen of zijn waarde plaatsen aan 0.*
