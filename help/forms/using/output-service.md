---
title: Uitvoerservice
seo-title: Uitvoerservice
description: Beschrijft de Dienst van de Output, die deel van AEM Diensten van het Document uitmaakt
seo-description: Beschrijft de Dienst van de Output, die deel van AEM Diensten van het Document uitmaakt
uuid: edddef59-b43c-486f-8734-3f97961ecf4d
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
discoiquuid: 51ab91ff-c0c0-4165-ae02-f306e45eea03
docset: aem65
translation-type: tm+mt
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---


# Uitvoerservice{#output-service}

## Overzicht {#overview}

De dienst van de output is de dienst OSGi die deel van AEM Diensten van het Document uitmaakt. De uitvoerservice ondersteunt verschillende uitvoerindelingen en functies voor het ontwerpen van uitvoer van AEM Forms Designer. De uitvoerservice kan XFA-sjablonen en XML-gegevens converteren om afdrukdocumenten in verschillende indelingen te genereren.

Met uitvoerservice kunt u toepassingen maken waarmee u:

* Definitieve formulierdocumenten genereren door sjabloonbestanden te vullen met XML-gegevens.
* Uitvoerformulieren genereren in verschillende indelingen, waaronder niet-interactieve PDF-, PostScript-, PCL- en ZPL-afdrukstromen.
* Afdruk-PDF&#39;s genereren op basis van XFA-formulier-PDF&#39;s.
* Genereer bulksgewijs PDF-, PostScript-, PCL- en ZPL-documenten door meerdere gegevenssets samen te voegen met de meegeleverde sjablonen.

>[!NOTE]
>
>De uitvoerservice is een 32-bits toepassing. In Microsoft Windows mag een 32-bits toepassing maximaal 2 GB geheugen gebruiken. De limiet geldt ook voor de uitvoerservice.

## Niet-interactieve formulierdocumenten maken {#creating-non-interactive-form-documents}

![usingoutput_modified](assets/usingoutput_modified.png)

Gewoonlijk maakt u sjablonen met AEM Forms Designer. Met de API&#39;s `generatePDFOutput` en `generatePrintedOutput` van de Output-service kunt u deze sjablonen rechtstreeks converteren naar verschillende indelingen, zoals PDF, PostScript, ZPL en PCL.

Met de bewerking `generatePDFOutput` worden PDF&#39;s gegenereerd, terwijl met de bewerking `generatePrintedOutput` PostScript-, ZPL- en PCL-indelingen worden gegenereerd. De eerste parameter van beide bewerkingen accepteert de naam van het sjabloonbestand (bijvoorbeeld `ExpenseClaim.xdp`) of een object Document dat de sjabloon bevat. Wanneer u de naam van het sjabloonbestand opgeeft, geeft u ook de hoofdmap van de inhoud op als het pad naar de map die de sjabloon bevat. U kunt de hoofdmap van de inhoud opgeven met de parameter `PDFOutputOptions` of `PrintedOutputOptions`. Zie Javadoc voor meer informatie over andere opties die u met deze parameters kunt opgeven.

De tweede parameter accepteert een XML-document dat met de sjabloon wordt samengevoegd tijdens het genereren van het uitvoerdocument.

Met de bewerking `generatePDFOutput` kunt u ook een op XFA gebaseerd PDF-formulier accepteren als invoer en een niet-interactieve versie van het PDF-formulier retourneren als uitvoer.

## Niet-interactieve formulierdocumenten genereren {#generating-non-interactive-form-documents}

Overweeg een scenario waar u één of meerdere malplaatjes en veelvoudige verslagen van de gegevens van XML voor elke malplaatje hebt.

Gebruik de bewerkingen `generatePDFOutputBatch` en `generatePrintedOutputBatch` van de service Uitvoer om een afdrukdocument te genereren voor elke record.

U kunt de records ook in één document combineren. Beide bewerkingen hebben vier parameters.

De eerste parameter is een Kaart die een willekeurige tekenreeks als sleutel en de naam van het sjabloonbestand als waarde bevat.

De tweede parameter is een andere map waarvan de waarde een object Document is dat XML-gegevens bevat. De sleutel is het zelfde als dat u voor de eerste parameter specificeert.

De derde parameter voor `generatePDFOutputBatch` of `generatePrintedOutputBatch` is van respectievelijk type `PDFOutputOptions` of `PrintedOutputOptions`.

De parametertypes zijn het zelfde als types van de parameters voor `generatePDFOutput` en `generatePrintedOutput` verrichtingen en hebben het zelfde effect.

De vierde parameter is van het type `BatchOptions`, dat u gebruikt om op te geven of een afzonderlijk bestand voor elke record kan worden gegenereerd. De standaardwaarde van deze parameter is false.

Zowel `generatePrintedOutputBatch` als `generatePDFOutputBatch` retourneren een waarde van het type `BatchResult`. De waarde bevat een lijst met gegenereerde documenten. Het bevat ook een metagegevensdocument in XML-indeling dat informatie bevat die betrekking heeft op elk document dat wordt gegenereerd.
