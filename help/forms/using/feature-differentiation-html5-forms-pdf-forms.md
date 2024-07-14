---
title: Verschil tussen HTML5-formulieren en PDF forms
description: Meer informatie over de functieverschillen tussen HTML5-formulieren en PDF forms.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
docset: aem65
feature: HTML5 Forms,Mobile Forms
exl-id: 3150f95f-7150-4eee-b5a9-121422dec2a1
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 1%

---

# Verschil tussen HTML5-formulieren en PDF forms {#feature-differentiation-between-html-forms-and-pdf-forms}

In de volgende tabel wordt de ondersteuning aangegeven die wordt geboden voor HTML5-formulieren en -PDF forms:

<table>
 <tbody>
  <tr>
   <th>Functie</th>
   <th>HTML5 Forms</th>
   <th>PDF</th>
  </tr>
  <tr>
   <td>Streepjescodes <br /> </td>
   <td>Niet beschikbaar op gebruikersinterfaceniveau. </td>
   <td>Ondersteund</td>
  </tr>
  <tr>
   <td>Handtekeningveld <br /> </td>
   <td><strong> Digitale Handtekeningen </strong> worden niet gesteund maar een nieuw <strong> Krabbelt gebied van de Handtekening </strong> wordt toegevoegd voor papier als handtekeningen. Men kan hun handtekening op de vorm krabbelen gebruikend het </strong> gebied van de Handtekening van 0} Krabbelen. <strong> De handtekening wordt als een afbeelding op het formulier opgeslagen. U kunt geolocatieinformatie op het <strong> Krabbelen </strong> gebied van de Handtekening bewaren.</td>
   <td>Het gebied van de handtekening beschikbaar voor <strong> Digitale Handtekeningen </strong>.</td>
  </tr>
  <tr>
   <td>Gegevenssamenvoeging</td>
   <td>Ondersteund</td>
   <td>Ondersteund</td>
  </tr>
  <tr>
   <td>Afbeeldingen</td>
   <td>Het schema Data URI wordt gebruikt om afbeeldingen weer te geven. Alle moderne versies van browsers ondersteunen dit schema, maar er zijn verschillen in de reeks afbeeldingsindelingen die elke browser ondersteunt.<br /> </td>
   <td>De indelingen .gif, .png, .jpeg, .bmp en .tiff worden ondersteund.</td>
  </tr>
  <tr>
   <td>Paginering <br /> </td>
   <td><p>Een HTML5-formulier is verdeeld in deelvensters en vakken, zodat het er net zo uitziet als PDF forms. De grootte van de pagina wordt dynamisch berekend. Als alle inhoud van een pagina in een HTML5-formulier wordt verwijderd of gemarkeerd als verborgen, wordt de lege pagina verborgen. Er wordt geen lege ruimte (lege ruimte) weergegeven tussen pagina's boven en onder de lege pagina.</p> <p>Als gegevens worden samengevoegd of scripts inhoud aan een pagina toevoegen, wordt de lengte van de pagina aangepast aan de nieuwe inhoud. Er worden geen nieuwe pagina's aan het formulier toegevoegd voor de nieuwe inhoud. </p> <p><strong> Nota:</strong> wanneer alle inhoud van een pagina in een vorm HTML5 wordt geschrapt of verborgen duidelijk, blijft de lege pagina (lege ruimte) zichtbaar tussen eerste en tweede pagina maar niet tussen andere pagina's.</p> </td>
   <td>Paginering in PDF is afhankelijk van samengevoegde gegevensinhoud of van gebruikersinhoud en het aantal pagina's wordt op basis daarvan verhoogd/verlaagd.</td>
  </tr>
  <tr>
   <td>Kopteksten/voetteksten </td>
   <td>Ondersteund. <br /> <br /> Omdat mobiele HTML5-formulieren geen ondersteuning bieden voor pagina-einden, worden kop- en voetteksten slechts eenmaal weergegeven. U kunt ze echter instellen in de indeling, zodat ze op meerdere plaatsen in de voorvertoning van mobiele formulieren worden weergegeven.<br /> </td>
   <td>Ondersteund.</td>
  </tr>
  <tr>
   <td>Aangepaste widgets</td>
   <td>U kunt widgets aanpassen om de gebruikerservaring op mobiele apparaten te verbeteren.<br /> </td>
   <td>Alle widgets zijn vergrendeld en er kan geen aangepaste widget worden aangesloten.<br /> </td>
  </tr>
  <tr>
   <td>XFA Script API</td>
   <td>Ondersteunt de meestgebruikte XFA-scriptconstructies. Voor een gedetailleerde lijst van gesteunde concepten, zie <a href="/help/forms/using/scripting-support.md"> scripting steun </a>.</td>
   <td>Ondersteunt alle XFA-scriptconstructies.</td>
  </tr>
  <tr>
   <td>Acrobat Script API's </td>
   <td>HTML5-formulieren ondersteunen veelgebruikte API's. Voor details, zie <a href="/help/forms/using/scripting-support.md"> scripting steun </a>.</td>
   <td>Als het PDF-bestand wordt geopend in Acrobat of Reader, worden ook alle script-API's van Acrobat ondersteund.</td>
  </tr>
  <tr>
   <td>Ondersteuning voor talen van rechts naar links </td>
   <td>Ondersteund</td>
   <td>Ondersteund</td>
  </tr>
 </tbody>
</table>

<!--Follow the best practices to enable a form template for HTML5 renditions and ensure that the behavior and appearance of HTML5 forms and XFA-based PDF is consistent. For detailed list of best practices, see [Best practices to design an HTML5 form.](/help/forms/using/best-practices-design-html5-forms.md)-->
