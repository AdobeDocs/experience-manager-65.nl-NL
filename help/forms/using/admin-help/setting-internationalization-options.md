---
title: internationalisatieopties instellen
description: Leer hoe u de landinstelling opgeeft die wordt gebruikt om formulieren te genereren en hoe u de tekenset opgeeft die wordt gebruikt om de uitvoerstream te coderen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 6cf82c2b-29f0-49d5-a138-99d7801d5a28
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 6a9806d8f40f711a610c130c63d9ab9b2460d075
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# internationalisatieopties instellen{#setting-internationalization-options}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

## De landinstelling voor het genereren van formulieren opgeven {#specify-the-locale-used-to-render-forms}

U kunt de landinstelling opgeven die wordt gebruikt bij het weergeven van een PDF-formulier. De velden op een PDF-formulier gebruiken de opgegeven landinstelling om gegevens weer te geven. Als de landinstelling bijvoorbeeld is ingesteld op Duits, worden in het formulier numerieke waarden gebruikt voor decimale scheidingstekens uit Duitsland. De landinstelling wordt ook gebruikt om validatieberichten naar clientapparaten, zoals webbrowsers, te verzenden als onderdeel van HTML-transformaties.

1. Klik in de beheerconsole op Services > Forms.
1. Selecteer onder Internationalisatie in de lijst Taal de landinstelling die wordt gebruikt om een formulier te genereren. De standaardwaarde is Engels (Verenigde Staten).
1. Klik op Opslaan.

## Geef de tekenset op die wordt gebruikt om de uitvoerstream te coderen {#specify-the-character-set-used-to-encode-the-output-stream}

1. Selecteer onder Internationalisatie een tekenset in de lijst Tekenset. Deze instelling is afhankelijk van de gebruikte API, renderHTMLForm of renderPDFForm. Als u een andere tekenset dan de vermelde wilt opgeven, selecteert u Aangepast en geeft u een coderingswaarde op in het vak dat wordt weergegeven.

   Voor HTML-transformaties ondersteunen AEM formulieren tekencoderingswaarden die zijn gedefinieerd in het `java.nio.charset` -pakket. Als sFormPreference PDFForm is, worden alleen specifieke tekensets ondersteund. De tekenset moet een geldige canonieke naam zijn. De standaardwaarde is ISO-8859-1.

1. Klik op Opslaan.
