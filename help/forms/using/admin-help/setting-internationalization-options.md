---
title: internationalisatieopties instellen
seo-title: internationalisatieopties instellen
description: Leer hoe u de landinstelling opgeeft die wordt gebruikt om formulieren te genereren en hoe u de tekenset opgeeft die wordt gebruikt om de uitvoerstream te coderen.
seo-description: Leer hoe u de landinstelling opgeeft die wordt gebruikt om formulieren te genereren en hoe u de tekenset opgeeft die wordt gebruikt om de uitvoerstream te coderen.
uuid: bb77f5f3-634f-4285-9b10-c4dd40085e69
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: e845d13f-bef2-442d-af9a-4f92d7616a46
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 1%

---


# Internationalisatieopties instellen{#setting-internationalization-options}

## De landinstelling opgeven waarmee formulieren worden gegenereerd {#specify-the-locale-used-to-render-forms}

U kunt de landinstelling opgeven die wordt gebruikt bij het weergeven van een PDF-formulier. De velden op een PDF-formulier gebruiken de opgegeven landinstelling om gegevens weer te geven. Als de landinstelling bijvoorbeeld is ingesteld op Duits, worden in het formulier numerieke waarden gebruikt voor decimale scheidingstekens uit Duitsland. De landinstelling wordt ook gebruikt om validatieberichten te verzenden naar clientapparaten, zoals webbrowsers, als onderdeel van HTML-transformaties.

1. Klik in de beheerconsole op Services > Forms.
1. Selecteer onder Internationalisatie in de lijst Taal de landinstelling die wordt gebruikt om een formulier te genereren. De standaardwaarde is Engels (Verenigde Staten).
1. Klik op Opslaan.

## Geef de tekenset op die wordt gebruikt om de uitvoerstream te coderen {#specify-the-character-set-used-to-encode-the-output-stream}

1. Selecteer onder Internationalisatie een tekenset in de lijst Tekenset. Deze instelling is afhankelijk van de gebruikte API, renderHTMLForm of renderPDFForm. Als u een andere tekenset dan de vermelde wilt opgeven, selecteert u Aangepast en geeft u een coderingswaarde op in het vak dat wordt weergegeven.

   Voor HTML-transformaties ondersteunen AEM formulieren tekencoderingswaarden die zijn gedefinieerd in het `java.nio.charset`-pakket. Als sFormPreference PDFForm is, worden alleen specifieke tekensets ondersteund. De tekenset moet een geldige canonieke naam zijn. De standaardwaarde is ISO-8859-1.

1. Klik op Opslaan.

