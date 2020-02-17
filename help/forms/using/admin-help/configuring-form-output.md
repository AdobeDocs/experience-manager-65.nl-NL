---
title: Formulieruitvoer configureren
seo-title: Formulieruitvoer configureren
description: Leer hoe u formulieruitvoer configureert.
seo-description: Leer hoe u formulieruitvoer configureert.
uuid: 70aad14e-c845-4ef3-a751-ad8860d5d505
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 17c9b69a-3c6f-47e3-a828-841bb90eba8b
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Formulieruitvoer configureren{#configuring-form-output}

## Het type HTML-uitvoer opgeven dat wordt geretourneerd aan de webbrowser {#specify-the-type-of-html-output-returned-to-the-web-browser}

1. Klik in de beheerconsole op Services > Formulieren.
1. Selecteer onder Uitvoer formulier in de lijst Uitvoertype een van de volgende opties:

   **** Volledige HTML: Het formulier weergeven binnen volledige HTML-tags (een volledige HTML-pagina). Dit is de standaardwaarde.

   **** Hoofdtekst van formulier: Het formulier weergeven binnen `<BODY>` -codes (geen volledige HTML-pagina).

1. Klik op Opslaan.

## De locatie opgeven waar PDF-inhoud wordt gerenderd {#specify-the-location-where-pdf-content-is-rendered}

1. Selecteer onder Formulieruitvoer in de lijst Renderen op een van de volgende opties:

   **** Client: PDF-formulieren renderen in Adobe Acrobat of Adobe Reader. Rendering op de client verbetert de prestaties van AEM-formulieren en is alleen van toepassing op PDFForm-transformatie.

   **** Server: PDF-formulieren genereren op de toepassingsserver.

   **** Automatisch: Het PDF-formulier weergeven op de locatie die is opgegeven door de `dynamicRender` configuratiewaarde van het XDP-bestand. Dit is de standaardwaarde.

1. Klik op Opslaan.

## Aanroepen van aangepaste scripts configureren voordat het formulier wordt verzonden {#configuring-invocation-of-custom-scripts-before-form-submit}

Voer de volgende stappen uit om de functie in te schakelen:

1. Meld u aan bij de beheerconsole.
1. Ga naar **Services** > **Formulieren**.
1. Geef het uitvoertype op als Formulierhoofdtekst.
1. Sla de instellingen op.
1. Declareer een JavaScript-variabele, __CUSTOM_SCRIPTS_VERSION, in de kopsectie van de HTML-code en stel de waarde ervan in op 1.

   >[!NOTE]
   >
   >*Als u de functie wilt uitschakelen, kunt u de JavaScript-variabele verwijderen of de waarde ervan instellen op 0.*

