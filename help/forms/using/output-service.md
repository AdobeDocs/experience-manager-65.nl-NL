---
title: Uitvoerservice
description: Beschrijft de Dienst van de Output, die deel van AEM Diensten van het Document uitmaakt
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
docset: aem65
feature: Document Services,Output Service
exl-id: 82b0293a-711f-4769-9b11-b4cff4fec021
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 0%

---

# Uitvoerservice{#output-service}

## Overzicht {#overview}

De dienst van de output is de dienst OSGi die deel van AEM Diensten van het Document uitmaakt. De uitvoerservice ondersteunt verschillende uitvoerindelingen en functies voor uitvoerontwerp van AEM Forms Designer. De uitvoerservice kan XFA-sjablonen en XML-gegevens converteren om afdrukdocumenten in verschillende indelingen te genereren.

Met uitvoerservice kunt u toepassingen maken waarmee u:

* Definitieve formulierdocumenten genereren door sjabloonbestanden te vullen met XML-gegevens.
* Uitvoerformulieren genereren in verschillende indelingen, waaronder niet-interactieve PDF-, PostScript-, PCL- en ZPL-afdrukstromen.
* Afdruk-PDF genereren op basis van XFA-formulier-PDF.
* Genereer PDF-, PostScript-, PCL- en ZPL-documenten in bulk door meerdere gegevenssets samen te voegen met de meegeleverde sjablonen.

>[!NOTE]
>
>De uitvoerservice is een 32-bits toepassing. In Microsoft Windows mag een 32-bits toepassing maximaal 2 GB geheugen gebruiken. De limiet geldt ook voor de uitvoerservice.

## Niet-interactieve formulierdocumenten maken {#creating-non-interactive-form-documents}

![&#x200B; gebruikend output_modified &#x200B;](assets/usingoutput_modified.png)

Gewoonlijk maakt u sjablonen met AEM Forms Designer. Met de API&#39;s `generatePDFOutput` en `generatePrintedOutput` van de Output-service kunt u deze sjablonen rechtstreeks converteren naar verschillende indelingen, zoals PDF, PostScript, ZPL en PCL.

Met de bewerking `generatePDFOutput` worden PDF gegenereerd, terwijl met de bewerking `generatePrintedOutput` PostScript-, ZPL- en PCL-indelingen worden gegenereerd. De eerste parameter van beide bewerkingen accepteert de naam van het sjabloonbestand (bijvoorbeeld `ExpenseClaim.xdp` ) of een object Document dat de sjabloon bevat. Wanneer u de naam van het sjabloonbestand opgeeft, geeft u ook de hoofdmap van de inhoud op als het pad naar de map die de sjabloon bevat. U kunt de hoofdmap van de inhoud opgeven met de parameter `PDFOutputOptions` of `PrintedOutputOptions` . Zie Javadoc voor meer informatie over andere opties die u met deze parameters kunt opgeven.

De tweede parameter accepteert een XML-document dat met de sjabloon wordt samengevoegd tijdens het genereren van het uitvoerdocument.

De bewerking `generatePDFOutput` kan ook een op XFA gebaseerd PDF-formulier accepteren als invoer en een niet-interactieve versie van het PDF-formulier retourneren als uitvoer.

## Niet-interactieve formulierdocumenten genereren {#generating-non-interactive-form-documents}

Overweeg een scenario waar u één of meerdere malplaatjes en veelvoudige verslagen van de gegevens van XML voor elke malplaatje hebt.

Gebruik de bewerkingen `generatePDFOutputBatch` en `generatePrintedOutputBatch` van de service Uitvoer om een afdrukdocument te genereren voor elke record.

U kunt de records ook in één document combineren. Beide bewerkingen hebben vier parameters.

De eerste parameter is een Kaart die een willekeurige tekenreeks als sleutel en de naam van het sjabloonbestand als waarde bevat.

De tweede parameter is een andere map waarvan de waarde een object Document is dat XML-gegevens bevat. De sleutel is het zelfde als dat u voor de eerste parameter specificeert.

De derde parameter voor `generatePDFOutputBatch` of `generatePrintedOutputBatch` is van het type `PDFOutputOptions` respectievelijk `PrintedOutputOptions` .

De parametertypen zijn hetzelfde als typen parameters voor de bewerkingen `generatePDFOutput` en `generatePrintedOutput` en hebben hetzelfde effect.

De vierde parameter is van het type `BatchOptions` , dat u gebruikt om op te geven of een afzonderlijk bestand voor elke record kan worden gegenereerd. De standaardwaarde van deze parameter is false.

Zowel `generatePrintedOutputBatch` als `generatePDFOutputBatch` retourneren een waarde van het type `BatchResult` . De waarde bevat een lijst met gegenereerde documenten. Het bevat ook een metagegevensdocument in XML-indeling dat informatie bevat die betrekking heeft op elk document dat wordt gegenereerd.
