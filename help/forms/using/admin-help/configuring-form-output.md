---
title: Formulieruitvoer configureren
description: Leer hoe u formulieruitvoer configureert. Gebruik de aangepaste scripts voordat u het formulier verzendt om de formulieruitvoer te configureren en de functie in te schakelen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: d739806c-ce72-40fd-b304-3262a0988d96
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 0%

---

# Formulieruitvoer configureren{#configuring-form-output}

## Geef het type HTML-uitvoer op dat wordt geretourneerd aan de webbrowser {#specify-the-type-of-html-output-returned-to-the-web-browser}

1. Klik in de beheerconsole op Services > Formulieren.
1. Selecteer onder Uitvoer formulier in de lijst Uitvoertype een van de volgende opties:

   **Volledige HTML:** Het formulier weergeven binnen volledige HTML-tags (een volledige HTML-pagina). Dit is de standaardwaarde.

   **Hoofdtekst van formulier:** Het formulier weergeven binnen `<BODY>` -tags (geen volledige HTML-pagina).

1. Klik op Opslaan.

## De locatie opgeven waar PDF-inhoud wordt gerenderd {#specify-the-location-where-pdf-content-is-rendered}

1. Selecteer onder Formulieruitvoer in de lijst Renderen op een van de volgende opties:

   **Client:** PDF forms renderen in Adobe Acrobat of Adobe Reader. Rendering op de client verbetert de prestaties van AEM formulieren en is alleen van toepassing op PDFForm-transformatie.

   **Server:** PDF forms renderen op de toepassingsserver.

   **Automatisch:** Het PDF-formulier weergeven op de locatie die door de `dynamicRender` configuratiewaarde van het XDP-bestand. Dit is de standaardwaarde.

1. Klik op Opslaan.

## Aanroeping van aangepaste scripts configureren voordat het formulier wordt verzonden {#configuring-invocation-of-custom-scripts-before-form-submit}

Voer de volgende stappen uit om de functie in te schakelen:

1. Aanmelden bij de beheerconsole.
1. Ga naar **Services** > **formulieren**.
1. Geef het uitvoertype op als Formulierhoofdtekst.
1. Sla de instellingen op.
1. Declareer een variabele JavaScript, __CUSTOM_SCRIPTS_VERSION, in de kopsectie van de code van de HTML en plaats zijn waarde aan 1.

   >[!NOTE]
   >
   >*Als u de functie wilt uitschakelen, kunt u de JavaScript-variabele verwijderen of de waarde ervan instellen op 0.*
