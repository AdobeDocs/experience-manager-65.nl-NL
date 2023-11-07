---
title: Uitvoerservice
seo-title: Output Service
description: Beschrijft de Dienst van de Output, die deel van AEM Diensten van het Document uitmaakt
seo-description: Describes Output Service, which is part of AEM Document Services
uuid: edddef59-b43c-486f-8734-3f97961ecf4d
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
discoiquuid: 51ab91ff-c0c0-4165-ae02-f306e45eea03
docset: aem65
exl-id: 1b62e1c1-428d-4c0f-98a8-486f319fa581
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 0%

---

# Uitvoerservice{#output-service}

## Overzicht {#overview}

De dienst van de output is de dienst OSGi die deel van AEM Diensten van het Document uitmaakt. De uitvoerservice ondersteunt verschillende uitvoerindelingen en functies voor het ontwerpen van uitvoer van AEM Forms Designer. De uitvoerservice kan XFA-sjablonen en XML-gegevens converteren om afdrukdocumenten in verschillende indelingen te genereren.

Met uitvoerservice kunt u toepassingen maken waarmee u:

* Definitieve formulierdocumenten genereren door sjabloonbestanden te vullen met XML-gegevens.
* Uitvoerformulieren genereren in verschillende indelingen, waaronder niet-interactieve PDF-, PostScript-, PCL- en ZPL-afdrukstromen.
* Afdruk-PDF genereren op basis van XFA-formulier-PDF.
* Genereer bulksgewijs PDF-, PostScript-, PCL- en ZPL-documenten door meerdere gegevenssets samen te voegen met de meegeleverde sjablonen.

>[!NOTE]
>
>De uitvoerservice is een 32-bits toepassing. In Microsoft Windows mag een 32-bits toepassing maximaal 2 GB geheugen gebruiken. De limiet geldt ook voor de uitvoerservice.

## Niet-interactieve formulierdocumenten maken {#creating-non-interactive-form-documents}

![usingoutput_modified](assets/usingoutput_modified.png)

Gewoonlijk maakt u sjablonen met AEM Forms Designer. De `generatePDFOutput` en `generatePrintedOutput` Met API&#39;s van de Output-service kunt u deze sjablonen rechtstreeks converteren naar verschillende indelingen, zoals PDF, PostScript, ZPL en PCL.

De `generatePDFOutput` bewerking genereert PDF terwijl de `generatePrintedOutput` Deze bewerking genereert PostScript-, ZPL- en PCL-indelingen. De eerste parameter van beide bewerkingen accepteert de naam van het sjabloonbestand (bijvoorbeeld `ExpenseClaim.xdp`) of een object Document dat de sjabloon bevat. Wanneer u de naam van het sjabloonbestand opgeeft, geeft u ook de hoofdmap van de inhoud op als het pad naar de map die de sjabloon bevat. U kunt de hoofdmap van de inhoud opgeven met de `PDFOutputOptions` of de `PrintedOutputOptions` parameter. Zie Javadoc voor meer informatie over andere opties die u met deze parameters kunt opgeven.

De tweede parameter accepteert een XML-document dat met de sjabloon wordt samengevoegd tijdens het genereren van het uitvoerdocument.

De `generatePDFOutput` Deze bewerking kan ook een op XFA gebaseerd PDF-formulier accepteren als invoer en een niet-interactieve versie van het PDF-formulier retourneren als uitvoer.

## Niet-interactieve formulierdocumenten genereren {#generating-non-interactive-form-documents}

Overweeg een scenario waar u één of meerdere malplaatjes en veelvoudige verslagen van de gegevens van XML voor elke malplaatje hebt.

Gebruik de `generatePDFOutputBatch` en `generatePrintedOutputBatch` bewerkingen van de uitvoerservice om een afdrukdocument voor elke record te genereren.

U kunt de records ook in één document combineren. Beide bewerkingen hebben vier parameters.

De eerste parameter is een Kaart die een willekeurige tekenreeks als sleutel en de naam van het sjabloonbestand als waarde bevat.

De tweede parameter is een andere map waarvan de waarde een object Document is dat XML-gegevens bevat. De sleutel is het zelfde als dat u voor de eerste parameter specificeert.

De derde parameter voor `generatePDFOutputBatch` of `generatePrintedOutputBatch` is van type `PDFOutputOptions` of `PrintedOutputOptions` respectievelijk.

De parametertypen zijn hetzelfde als de typen parameters voor de parameter `generatePDFOutput` en `generatePrintedOutput` en hebben hetzelfde effect.

De vierde parameter is van het type `BatchOptions`, die u gebruikt om op te geven of voor elke record een afzonderlijk bestand kan worden gegenereerd. De standaardwaarde van deze parameter is false.

Beide `generatePrintedOutputBatch` en `generatePDFOutputBatch` Hiermee wordt een waarde van het type geretourneerd `BatchResult`. De waarde bevat een lijst met gegenereerde documenten. Het bevat ook een metagegevensdocument in XML-indeling dat informatie bevat die betrekking heeft op elk document dat wordt gegenereerd.
