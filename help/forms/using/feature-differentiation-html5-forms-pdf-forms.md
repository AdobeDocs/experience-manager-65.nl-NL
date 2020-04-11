---
title: Verschil tussen functies in HTML5-formulieren en PDF-formulieren
seo-title: Verschil tussen functies in HTML5-formulieren en PDF-formulieren
description: Functie wordt ondersteund in HTML5-formulieren en PDF-formulieren
seo-description: Functie wordt ondersteund in HTML5-formulieren en PDF-formulieren
uuid: 6ddee197-d108-4897-9976-77d115a06504
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: bdd97c20-d1f2-4898-9862-1a6a8071be88
docset: aem65
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317

---


# Verschil tussen functies in HTML5-formulieren en PDF-formulieren {#feature-differentiation-between-html-forms-and-pdf-forms}

In de volgende tabel vindt u ondersteuning voor functies die worden geboden voor HTML5-formulieren en PDF-formulieren:

<table>
 <tbody>
  <tr>
   <th>Functie</th>
   <th>HTML5-formulieren</th>
   <th>PDF</th>
  </tr>
  <tr>
   <td>Streepjescodes<br /> </td>
   <td>Niet beschikbaar op gebruikersinterfaceniveau. </td>
   <td>Ondersteund</td>
  </tr>
  <tr>
   <td>Handtekeningveld<br /> </td>
   <td><strong>Digitale handtekeningen</strong> worden niet ondersteund, maar er wordt een nieuw veld <strong>Krabbelhandtekening</strong> toegevoegd voor handtekeningen die lijken op papier. U kunt de handtekening op het formulier krabbelen met het veld <strong>Krabbelhandtekening</strong> . De handtekening wordt als een afbeelding op het formulier opgeslagen. U kunt gegevens over de geolocatie opslaan in het veld <strong>Krabbelhandtekening</strong> .</td>
   <td>Handtekeningveld beschikbaar voor <strong>digitale handtekeningen</strong>.</td>
  </tr>
  <tr>
   <td>Gegevenssamenvoeging</td>
   <td>Ondersteund</td>
   <td>Ondersteund</td>
  </tr>
  <tr>
   <td>Afbeeldingen</td>
   <td>Het schema Data URI wordt gebruikt om afbeeldingen weer te geven. In alle moderne versies van browsers wordt dit schema ondersteund, maar de afbeeldingsindelingen die in elke browser worden ondersteund, verschillen van elkaar.<br /> </td>
   <td>De indelingen .gif, .png, .jpeg, .bmp en .tiff worden ondersteund.</td>
  </tr>
  <tr>
   <td>Paginering<br /> </td>
   <td><p>Een HTML5-formulier wordt opgedeeld in deelvensters en vakken zodat het er net zo uitziet als PDF-formulieren. De grootte van de pagina wordt dynamisch berekend. Als alle inhoud van een pagina in een HTML5-formulier is verwijderd of gemarkeerd als verborgen, wordt de lege pagina verborgen en wordt er geen lege ruimte (spatie) weergegeven tussen pagina's boven en onder de lege pagina.</p> <p>Als gegevens worden samengevoegd of scripts inhoud aan een pagina toevoegen, wordt de lengte van de pagina aangepast aan de nieuwe inhoud. Er worden geen nieuwe pagina's aan het formulier toegevoegd voor de nieuwe inhoud. </p> <p><strong>Opmerking:</strong> Wanneer alle inhoud van een pagina in een HTML5-formulier verborgen wordt verwijderd of gemarkeerd, blijft de lege pagina (lege ruimte) zichtbaar tussen de eerste en de tweede pagina, maar niet tussen andere pagina's.</p> </td>
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
   <td>Ondersteunt de meestgebruikte XFA-scriptconstructies. Zie <a href="/help/forms/using/scripting-support.md">Scriptondersteuning</a>voor een gedetailleerde lijst met ondersteunde constructies.</td>
   <td>Ondersteunt alle XFA-scriptconstructies.</td>
  </tr>
  <tr>
   <td>Acrobat Script API's </td>
   <td>HTML5-formulieren ondersteunen veelgebruikte API's. Zie <a href="/help/forms/using/scripting-support.md">Scriptondersteuning</a>voor meer informatie.</td>
   <td>Als het PDF-bestand wordt geopend in Acrobat of Reader, worden ook alle script-API's van Acrobat ondersteund.</td>
  </tr>
  <tr>
   <td>Ondersteuning voor talen die van rechts naar links worden geschreven </td>
   <td>Ondersteund</td>
   <td>Ondersteund</td>
  </tr>
 </tbody>
</table>

<!--Follow the best practices to enable a form template for HTML5 renditions and ensure that the behavior and appearance of HTML5 forms and XFA-based PDF is consistent. For detailed list of best practices, see [Best practices to design an HTML5 form.](/help/forms/using/best-practices-design-html5-forms.md)-->
