---
title: Uitvoerservice
seo-title: Uitvoerservice
description: Beschrijft de Dienst van de Output, die deel van de Diensten van het Document van AEM uitmaakt
seo-description: Beschrijft de Dienst van de Output, die deel van de Diensten van het Document van AEM uitmaakt
uuid: edddef59-b43c-486f-8734-3f97961ecf4d
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
discoiquuid: 51ab91ff-c0c0-4165-ae02-f306e45eea03
docset: aem65
translation-type: tm+mt
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65

---


# Uitvoerservice{#output-service}

## Overzicht {#overview}

De dienst van de output is de dienst OSGi die deel van de Diensten van het Document AEM uitmaakt. De uitvoerservice ondersteunt verschillende uitvoerindelingen en functies voor het uitvoerontwerp van AEM Forms Designer. De uitvoerservice kan XFA-sjablonen en XML-gegevens converteren om afdrukdocumenten in verschillende indelingen te genereren.

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

Gewoonlijk maakt u sjablonen met AEM Forms Designer. Met de API&#39;s `generatePDFOutput` en `generatePrintedOutput` API&#39;s van de Output-service kunt u deze sjablonen rechtstreeks converteren naar verschillende indelingen, zoals PDF, PostScript, ZPL en PCL.

De `generatePDFOutput` bewerking genereert PDF&#39;s, terwijl de `generatePrintedOutput` bewerking PostScript-, ZPL- en PCL-indelingen genereert. De eerste parameter van beide bewerkingen accepteert de naam van het sjabloonbestand (bijvoorbeeld `ExpenseClaim.xdp`) of een object Document dat de sjabloon bevat. Wanneer u de naam van het sjabloonbestand opgeeft, geeft u ook de hoofdmap van de inhoud op als het pad naar de map die de sjabloon bevat. U kunt de hoofdmap van de inhoud opgeven met behulp van de parameter `PDFOutputOptions` of de `PrintedOutputOptions` parameter. Zie Javadoc voor meer informatie over andere opties die u met deze parameters kunt opgeven.

De tweede parameter accepteert een XML-document dat met de sjabloon wordt samengevoegd tijdens het genereren van het uitvoerdocument.

De `generatePDFOutput` bewerking kan ook een op XFA gebaseerd PDF-formulier accepteren als invoer en een niet-interactieve versie van het PDF-formulier retourneren als uitvoer.

## Niet-interactieve formulierdocumenten genereren {#generating-non-interactive-form-documents}

Overweeg een scenario waar u één of meerdere malplaatjes en veelvoudige verslagen van de gegevens van XML voor elke malplaatje hebt.

Gebruik de `generatePDFOutputBatch` en `generatePrintedOutputBatch` bewerkingen van de service Uitvoer om voor elke record een afdrukdocument te genereren.

U kunt de records ook in één document combineren. Beide bewerkingen hebben vier parameters.

De eerste parameter is een Kaart die een willekeurige tekenreeks als sleutel en de naam van het sjabloonbestand als waarde bevat.

De tweede parameter is een andere map waarvan de waarde een object Document is dat XML-gegevens bevat. De sleutel is het zelfde als dat u voor de eerste parameter specificeert.

De derde parameter voor `generatePDFOutputBatch` of `generatePrintedOutputBatch` is van het type `PDFOutputOptions` of `PrintedOutputOptions` .

De parametertypen zijn hetzelfde als typen parameters voor de parameters `generatePDFOutput` `generatePrintedOutput` en bewerkingen en hebben hetzelfde effect.

De vierde parameter is van het type `BatchOptions`, dat u gebruikt om op te geven of een afzonderlijk bestand voor elke record kan worden gegenereerd. De standaardwaarde van deze parameter is false.

Zowel `generatePrintedOutputBatch` als `generatePDFOutputBatch` retourneert een waarde van het type `BatchResult`. De waarde bevat een lijst met gegenereerde documenten. Het bevat ook een metagegevensdocument in XML-indeling dat informatie bevat die betrekking heeft op elk document dat wordt gegenereerd.
