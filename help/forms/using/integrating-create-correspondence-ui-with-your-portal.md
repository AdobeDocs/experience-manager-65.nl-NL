---
title: De interface Correspondentie maken integreren met uw aangepaste portal
seo-title: De interface Correspondentie maken integreren met uw aangepaste portal
description: Leer hoe u het maken van correspondentie-UI kunt integreren met uw aangepaste portal
seo-description: Leer hoe u het maken van correspondentie-UI kunt integreren met uw aangepaste portal
uuid: 68ef5bf2-b271-4c44-8840-6c495069164d
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
discoiquuid: 0d3bb98e-7139-4d8e-b110-6ebd11debda1
docset: aem65
feature: Correspondence Management
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 3%

---


# Integratie van de interface Correspondentie maken met uw aangepaste portal{#integrating-create-correspondence-ui-with-your-custom-portal}

## Overzicht {#overview}

In dit artikel wordt beschreven hoe u de Correspondentieoplossing maken kunt integreren met uw omgeving.

## Oproepen op basis van URL {#url-based-invocation}

U kunt de toepassing Correspondentie maken aanroepen vanuit een aangepast portaal door de URL voor te bereiden met de volgende aanvraagparameters:

* de id voor de lettersjabloon (met de parameter cmLetterId).

* de URL naar de XML-gegevens die van de gewenste gegevensbron worden opgehaald (met de parameter cmDataUrl).

Het aangepaste portaal bereidt bijvoorbeeld de URL voor als\
`https://'[server]:[port]'/[contextPath]/aem/forms/createcorrespondence.html?random=[timestamp]&cmLetterId=[letter identifier]&cmDataUrl=[data URL]`, wat de href zou kunnen zijn van een link op het portaal.

>[!NOTE]
>
>Op deze manier aanroepen is niet veilig omdat de noodzakelijke parameters als een verzoek van de GET worden doorgegeven, door het zelfde (duidelijk zichtbare) in URL toegankelijk te maken.

>[!NOTE]
>
>Voordat u de toepassing Correspondentie maken aanroept, slaat u de gegevens op en uploadt u deze om de interface Correspondentie maken op de opgegeven dataURL aan te roepen. Dit zou of van het douaneportaal zelf of door een ander achtereindeproces kunnen worden gedaan.

## Inline op gegevens gebaseerde aanroep {#inline-data-based-invocation}

Een andere (en veiligere) manier om de Create toepassing van de Correspondentie te roepen zou kunnen zijn eenvoudig URL op https://&#39;[server]:[port]&#39;/[contextPath]/aem/forms/createcorrespondence.html te raken, terwijl het verzenden van de parameters en de gegevens om de Create toepassing van de Correspondentie als een verzoek van de POST te roepen (hen verbergen van de eindgebruiker). Dit betekent ook dat u nu de XML-gegevens voor de toepassing Correspondentie maken inline kunt doorgeven (als onderdeel van hetzelfde verzoek, met de parameter cmData), wat niet mogelijk/ideaal was in de vorige aanpak.

### Parameters voor het opgeven van de letter {#parameters-for-specifying-letter}

| **Naam** | **Type** | **Beschrijving** |
|---|---|---|
| cmLetterInstanceId | Tekenreeks | De id voor de letter-instantie. |
| cmLetterId | Tekenreeks | De naam van de Letter-sjabloon. |

De volgorde van parameters in de tabel geeft de voorkeur aan parameters die worden gebruikt voor het laden van de letter.

### Parameters om de XML-gegevensbron {#parameters-for-specifying-the-xml-data-source} op te geven

<table>
 <tbody>
  <tr>
   <td><strong>Naam</strong></td> 
   <td><strong>Type</strong></td> 
   <td><strong>Beschrijving</strong></td> 
  </tr>
  <tr>
   <td>cmDataUrl<br /> </td> 
   <td>URL</td> 
   <td>XML-gegevens uit een bronbestand met basisprotocollen zoals cq, ftp, http of file.<br /> </td> 
  </tr>
  <tr>
   <td>cmLetterInstanceId</td> 
   <td>Tekenreeks</td> 
   <td>XML-gegevens gebruiken die beschikbaar zijn in Letter Instance.</td> 
  </tr>
  <tr>
   <td>cmUseTestData</td> 
   <td>Boolean</td> 
   <td>De testgegevens in het gegevenswoordenboek opnieuw gebruiken.</td> 
  </tr>
 </tbody>
</table>

De volgorde van parameters in de tabel geeft de voorkeur aan parameters die worden gebruikt voor het laden van de XML-gegevens.

### Andere parameters {#other-parameters}

<table>
 <tbody>
  <tr>
   <td><strong>Naam</strong></td> 
   <td><strong>Type</strong></td> 
   <td><strong>Beschrijving</strong></td> 
  </tr>
  <tr>
   <td>cmPreview<br /> </td> 
   <td>Boolean</td> 
   <td>True to open the letter in preview mode<br /> </td> 
  </tr>
  <tr>
   <td>Willekeurig</td> 
   <td>Tijdstempel</td> 
   <td>Oplossen van cacheproblemen met de browser.</td> 
  </tr>
 </tbody>
</table>

Als u het http- of cq-protocol voor cmDataURL gebruikt, moet de URL van http/cq anoniem toegankelijk zijn.
