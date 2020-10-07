---
title: Transactierapporten Billable API's
seo-title: Transactierapporten Billable API's
description: Lijst met alle API's die als transacties worden beschouwd
seo-description: Lijst met alle API's die als transacties worden beschouwd
uuid: d2f38ae4-75df-426f-af34-52ae6fb324f3
topic-tags: forms-manager
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 929a298d-7f22-487f-bf7d-8ab2556d0d81
docset: aem65
translation-type: tm+mt
source-git-commit: 13016df927448d93af86899f746199e1815fdfe7
workflow-type: tm+mt
source-wordcount: '1963'
ht-degree: 1%

---


# Transactierapporten Billable API&#39;s{#transaction-reports-billable-apis}

AEM Forms biedt verschillende API&#39;s voor het verzenden van formulieren, het verwerken van documenten en het weergeven van documenten. Sommige API&#39;s worden beschouwd als transacties en andere zijn gratis. Dit document verstrekt een lijst van alle APIs die als transacties in een transactierapport worden rekenschap gegeven. Hier volgen enkele veelvoorkomende scenario&#39;s waarbij een factureerbare API wordt gebruikt:

* Een adaptief formulier, HTML5-formulier en formulierset verzenden
* Een afdruk- of webversie van een interactieve communicatie renderen
* Een document omzetten van de ene naar de andere indeling
* Een dynamisch PDF-document afvlakken
* Een recorddocument genereren
* Een interactief PDF-document samenvoegen met een ander PDF-document
* De stappen van de taakstap toewijzen en de documentservices van AEM Workflows gebruiken
* Het adaptieve formulier gebruiken in een adaptief formulier

Factuur-API&#39;s zijn niet geschikt voor het aantal pagina&#39;s, de lengte van een document of formulier of de uiteindelijke indeling van het gerenderde document. In een transactierapport worden de transacties in twee categorieën verdeeld: Gerenderde documenten en Forms verzonden.

* **Forms verzonden:** Wanneer gegevens worden verzonden vanuit elk type formulier dat met AEM Forms is gemaakt en de gegevens worden verzonden naar een opslagplaats of database voor gegevensopslag, wordt dit beschouwd als een verzending. Het verzenden van bijvoorbeeld een adaptief formulier, HTML5-formulier, PDF forms en formulierset worden beschouwd als verzonden formulieren. Elk formulier in een formulierset wordt beschouwd als een verzending. Als een formulierset bijvoorbeeld 5 formulieren heeft, telt de service voor transactierapportage deze als 5 verzendingen wanneer de formulierset wordt verzonden.

* **Gerenderde documenten:** Het genereren van een document door een sjabloon en gegevens te combineren, een document digitaal te ondertekenen of te certificeren, met behulp van een factureerbare API&#39;s voor documentservices of door een document van de ene naar de andere indeling te converteren, wordt beschouwd als documenten die worden gerenderd.

>[!NOTE]
>
>De gebruikersinterface voor transactierapporten bevat drie categorieën: Forms verzonden, gerenderde documenten en verwerkte documenten. Zowel gerenderde documenten als verwerkte documenten worden geboekt als gerenderde documenten.

## Billable Document Services API&#39;s {#billable-document-services-apis}

### PDF-service genereren {#generate-pdf-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschrijving</td>
   <td>Categorie Transactieverslag</td>
   <td>Aanvullende informatie</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#createPDF-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">createPDF</a></td>
   <td>Maakt Adobe PDF van ondersteunde bestandstypen.</td>
   <td>Verwerkte documenten</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#createPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">createPDF2</a></td>
   <td>Maakt Adobe PDF van ondersteunde bestandstypen.</td>
   <td>Verwerkte documenten</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#exportPDF-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">exportPDF</a></td>
   <td>Converteert Adobe PDF naar ondersteunde bestandstypen. </td>
   <td>Verwerkte documenten<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#exportPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">exportPDF2</a></td>
   <td>Converteert Adobe PDF naar ondersteunde bestandstypen. </td>
   <td>Verwerkte documenten<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#exportPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">exportPDF3</a></td>
   <td>Converteert Adobe PDF naar ondersteunde bestandstypen. </td>
   <td>Verwerkte documenten<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-3/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#htmlFileToPdf-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-">htmlFileToPdf</a></td>
   <td><p>Hiermee maakt u een PDF van HTML-pagina's.</p> </td>
   <td>Verwerkte documenten<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#htmlToPdf-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">htmlToPdf</a></td>
   <td>Hiermee maakt u een PDF van URL's die naar een HTML-pagina verwijzen.</td>
   <td>Verwerkte documenten<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#htmlToPdf2-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">htmlToPdf2</a></td>
   <td>Hiermee maakt u een PDF van URL's die naar een HTML-pagina verwijzen.</td>
   <td>Verwerkte documenten<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#optimizePDF-com.adobe.aemfd.docmanager.Document-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">optimizePDF</a></td>
   <td>Hiermee wordt PDF geoptimaliseerd om de bestandsgrootte te reduceren door overbodige metagegevens te verwijderen zonder dat dit van invloed is op de kwaliteit.</td>
   <td>Verwerkte documenten<br /> </td>
   <td> </td>
  </tr>
 </tbody>
</table>

### Distiller Service {#distiller-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschrijving</td>
   <td>Categorie Transactieverslag</td>
   <td>Aanvullende informatie</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/DistillerService.html#createPDF-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">createPDF</a><br /> </td>
   <td>Maakt Adobe PDF van ondersteunde bestandstypen.</td>
   <td>Verwerkte documenten</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/DistillerService.html#createPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">createPDF2</a></td>
   <td>Maakt Adobe PDF van ondersteunde bestandstypen.</td>
   <td>Verwerkte documenten</td>
   <td> </td>
  </tr>
 </tbody>
</table>

### Document of Record Service (DoR-service) {#document-of-record-service-dor-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschrijving</td>
   <td>Categorie Transactieverslag</td>
   <td>Aanvullende informatie</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/aemds/guide/addon/dor/DoRService.html#render-com.adobe.aemds.guide.addon.dor.DoROptions-" target="_blank">renderen</a></td>
   <td>Roept de opgegeven rendermethode aan om een document met een record te genereren met behulp van opgegeven parameters.</td>
   <td>Verwerkte documenten</td>
   <td> </td>
  </tr>
 </tbody>
</table>

### Uitvoerservice {#output-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschrijving</td>
   <td>Categorie Transactieverslag</td>
   <td>Aanvullende informatie</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/output/api/OutputService.html#generatePDFOutput-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-com.adobe.fd.output.api.PDFOutputOptions-" target="_blank">generatePDFOutput</a></td>
   <td>Hiermee voegt u gegevens en sjablonen samen om een PDF-document te maken.</td>
   <td>Verwerkte documenten</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/output/api/OutputService.html#generatePDFOutput-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.fd.output.api.PDFOutputOptions-" target="_blank">generatePDFOutput</a></td>
   <td>Hiermee voegt u gegevens en sjablonen samen om een PDF-document te maken.</td>
   <td>Verwerkte documenten</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/output/api/OutputService.html#generatePDFOutputBatch-java.util.Map-java.util.Map-com.adobe.fd.output.api.PDFOutputOptions-com.adobe.fd.output.api.BatchOptions-" target="_blank">generatePDFOutputBatch</a></td>
   <td>Hiermee voegt u gegevens en sjablonen samen om een set PDF-documenten te maken.</td>
   <td>Verwerkte documenten</td>
   <td> De generatePDFOutputBatch-API combineert een formuliersjabloon met een record en genereert een PDF. Wanneer u een batch records verwerkt, telt de service voor transactierapportage elke record als een afzonderlijke PDF-uitvoering. <br> Met de markering <a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/output/api/BatchOptions.html#getGenerateManyFiles--">getGenerateManyFiles</a> kunt u meerdere uitvoeringen combineren tot één PDF-bestand. Ongeacht de status van de vlag telt de service elke record als een afzonderlijke PDF-uitvoering. </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/output/api/OutputService.html#generatePrintedOutput-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-com.adobe.fd.output.api.PrintedOutputOptions-" target="_blank">generatePrintedOutput</a></td>
   <td>XDP- en PDF-documenten worden geconverteerd naar de bestandsindelingen PostScript (PS), Printer Command Language (PCL) en ZPL. </td>
   <td>Verwerkte documenten</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/output/api/OutputService.html#generatePrintedOutput-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.fd.output.api.PrintedOutputOptions-" target="_blank">generatePrintedOutput</a></td>
   <td>XDP- en PDF-documenten worden geconverteerd naar de bestandsindelingen PostScript (PS), Printer Command Language (PCL) en ZPL. </td>
   <td>Verwerkte documenten</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/output/api/OutputService.html#generatePrintedOutputBatch-java.util.Map-java.util.Map-com.adobe.fd.output.api.PrintedOutputOptions-com.adobe.fd.output.api.BatchOptions-" target="_blank">generatePrintedOutputBatch</a></td>
   <td>Hiermee converteert u een set XDP- en PDF-documenten naar een set PostScript- (PS), Printer Command Language (PCL)- en ZPL-bestandsindelingen. </td>
   <td>Verwerkte documenten</td>
   <td> De generatePDFOutputBatch-API combineert een formuliersjabloon met een record en genereert een PDF. Wanneer u een batch records verwerkt, telt de service voor transactierapportage elke record als een afzonderlijke PDF-uitvoering. <br> Met de markering <a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/output/api/BatchOptions.html#getGenerateManyFiles--">getGenerateManyFiles</a> kunt u meerdere uitvoeringen combineren tot één PDF-bestand. Ongeacht de status van de vlag telt de service elke record als een afzonderlijke PDF-uitvoering. </td>
  </tr>
 </tbody>
</table>

### Forms Service {#forms-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschrijving</td>
   <td>Categorie Transactieverslag</td>
   <td>Aanvullende informatie</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/forms/api/FormsService.html#renderPDFForm-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.fd.forms.api.PDFFormRenderOptions-" target="_blank">renderPDFForm</a></td>
   <td>Hiermee maakt u PDF-formulier van XDP-sjablonen. De XP-sjablonen worden gemaakt in Forms Designer.</td>
   <td>Verwerkte documenten</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/forms/api/FormsService.html#exportData-com.adobe.aemfd.docmanager.Document-com.adobe.fd.forms.api.DataFormat-" target="_blank">exportData</a></td>
   <td>Hiermee worden gegevens geëxtraheerd uit een PDF-formulier of XDP-sjablonen</td>
   <td>Verwerkte documenten</td>
   <td> </td>
  </tr>
 </tbody>
</table>

### PDF-service converteren {#convert-pdf-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschrijving</td>
   <td>Categorie Transactieverslag</td>
   <td>Aanvullende informatie</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/cpdf/api/ConvertPdfService.html#toImage-com.adobe.aemfd.docmanager.Document-com.adobe.fd.cpdf.api.ToImageOptionsSpec-" target="_blank">toImage</a></td>
   <td>Hiermee wordt een PDF-document geconverteerd naar een lijst met afbeeldingsdocumenten. Ondersteunde afbeeldingsindelingen zijn JPEG, JPEG2K, PNG en TIFF.</td>
   <td>Verwerkte documenten</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/cpdf/api/ConvertPdfService.html#toImage-com.adobe.aemfd.docmanager.Document-com.adobe.fd.cpdf.api.ToImageOptionsSpec-" target="_blank">naarPS</a></td>
   <td>Hiermee converteert u een effen PDF-bestand naar PostScript-indeling met de opties die zijn opgegeven in de optiespecc.</td>
   <td>Verwerkte documenten</td>
   <td> </td>
  </tr>
 </tbody>
</table>

### Barcoded Forms Service {#barcoded-forms-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschrijving</td>
   <td>Categorie Transactieverslag</td>
   <td>Aanvullende informatie</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/bcf/api/BarcodedFormsService.html#decode-com.adobe.aemfd.docmanager.Document-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-com.adobe.fd.bcf.api.CharSet-" target="_blank">decoderen</a></td>
   <td>Decodeert alle streepjescodes in een object Document en retourneert een object org.w3c.dom.Document dat gegevens bevat die uit de streepjescode zijn opgehaald.</td>
   <td>Verwerkte documenten</td>
   <td> </td>
  </tr>
 </tbody>
</table>

### Assembler-service {#assembler-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschrijving</td>
   <td>Categorie Transactieverslag</td>
   <td>Aanvullende informatie</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-3/forms/javadocs/com/adobe/fd/assembler/service/AssemblerService.html#invoke-com.adobe.aemfd.docmanager.Document-java.util.Map-com.adobe.fd.assembler.client.AssemblerOptionSpec-">oproepen</a></td>
   <td>Voert het gespecificeerde document DDX uit en keert een <a href="https://helpx.adobe.com/experience-manager/6-3/forms/javadocs/com/adobe/fd/assembler/client/AssemblerResult.html">voorwerp AssemblerResult</a> terug die de resulterende documenten bevat. </td>
   <td>Verwerkte documenten</td>
   <td>De volgende transacties worden niet administratief verwerkt als transacties:
    <ul>
     <li>Pakketten of portfolio maken</li>
     <li>Meerdere XDP's vastleggen </li>
    </ul> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/assembler/service/AssemblerService.html#invoke-com.adobe.aemfd.docmanager.Document-java.util.Map-com.adobe.fd.assembler.client.AssemblerOptionSpec-" target="_blank">oproepen</a></td>
   <td>Voert het gespecificeerde document DDX uit en keert een <a href="https://helpx.adobe.com/experience-manager/6-3/forms/javadocs/com/adobe/fd/assembler/client/AssemblerResult.html">voorwerp AssemblerResult</a> terug die de resulterende documenten bevat. </td>
   <td>Verwerkte documenten</td>
   <td>Alle invoerbestandsindelingen die worden ondersteund door de services PDF Generator, Forms en Output, Assembler, ondersteunen al deze indelingen als uitvoerbestandsindelingen. </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/assembler/service/AssemblerService.html#toPDFA-com.adobe.aemfd.docmanager.Document-com.adobe.fd.assembler.client.PDFAConversionOptionSpec-">toPDFA</a></td>
   <td>Hiermee wordt een opgegeven document geconverteerd naar PDF/A met de opgegeven opties.</td>
   <td>Verwerkte documenten</td>
   <td> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>* De invoke API van de assemblageservice kan intern een factureerbare API van een andere service oproepen, afhankelijk van de invoer. De aanroepAPI kan dus worden beschouwd als geen, enkele of meerdere transacties. Het aantal transacties dat wordt geteld, is afhankelijk van de invoer en de interne API&#39;s die worden aangeroepen.
>* Eén PDF-document dat met de assembleerservice wordt gemaakt, kan worden beschouwd als geen, één of meerdere transacties. Het aantal transacties dat wordt geteld, is afhankelijk van de geleverde DDX-code.

>



### PDF-hulpprogramma  {#pdf-utility-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschrijving</td>
   <td>Categorie Transactieverslag</td>
   <td>Aanvullende informatie</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/pdfutility/services/PDFUtilityService.html#convertPDFtoXDP-com.adobe.aemfd.docmanager.Document-" target="_blank">convertPDFtoXDP</a></td>
   <td>Hiermee converteert u een PDF-document naar een XDP-bestand. Een PDF-document kan alleen met succes worden geconverteerd naar een XDP-bestand als het PDF-document een XFA-stroom bevat in het AcroForm-woordenboek.</td>
   <td>Verwerkte documenten</td>
   <td> </td>
  </tr>
 </tbody>
</table>

## Billable Data Capture API&#39;s {#billable-data-capture-apis}

Alle verzendgebeurtenissen van adaptieve formulieren, HTML5 Forms en formulierset worden als transacties verwerkt. Het verzenden van een PDF-formulier wordt standaard niet als een transactie beschouwd. Gebruik de opgegeven [transactierecorder-API](record-transaction-custom-implementation.md) om een PDF forms-verzending op te nemen als een transactie.

### Adaptieve Forms {#adaptive-forms}

<table>
 <tbody>
  <tr>
   <td><p>Hoofdletters gebruiken</p> </td>
   <td>Beschrijving</td>
   <td>Categorie Transactieverslag</td>
   <td>Aanvullende informatie</td>
  </tr>
  <tr>
   <td>Een adaptief formulier indienen</td>
   <td>Hiermee wordt een adaptief formulier verzonden voor een geconfigureerde verzendactie. </td>
   <td>Forms verzonden</td>
   <td>
    <ul>
     <li>Een of twee transacties worden verwerkt met geslaagde verzendingen. Het aantal transacties dat wordt meegeteld, is afhankelijk van het type verzendactie dat wordt gebruikt voor verzending. U verzendt bijvoorbeeld een PDF via e-mail voor het verzenden van een actierekening voor twee tellingen van transacties. Eén transactie voor het verzenden van formulieren en een andere voor PDF die is gegenereerd met de service Document of Record (DOR). </li>
     <li>Met het adaptieve formulier in een adaptief formulier (adaptief formulierformaat) wordt slechts één transactie verwerkt. U kunt een willekeurig aantal adaptieve formulieren in een adaptief formulier gebruiken.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

### HTML5 Forms {#html-forms}

<table>
 <tbody>
  <tr>
   <td><p>Hoofdletters gebruiken</p> </td>
   <td>Beschrijving </td>
   <td>Categorie Transactieverslag</td>
   <td>Aanvullende informatie</td>
  </tr>
  <tr>
   <td>Een HTML5-formulier verzenden</td>
   <td>Hiermee wordt een HTML5-formulier verzonden voor het verzenden van de URL die in het formulier is geconfigureerd.</td>
   <td>Forms verzonden</td>
   <td> </td>
  </tr>
 </tbody>
</table>

### Formulierset {#form-set}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschrijving</td>
   <td>Categorie Transactieverslag</td>
   <td>Aanvullende informatie</td>
  </tr>
  <tr>
   <td>Een formulierset verzenden</td>
   <td>Hiermee verzendt u het formulier dat is ingesteld op de URL voor verzending die in de formulierset is geconfigureerd.</td>
   <td>Forms verzonden</td>
   <td>
    <ul>
     <li>Met het adaptieve formulier in een adaptief formulier (adaptief formulierformaat) wordt slechts één transactie verwerkt. U kunt een willekeurig aantal adaptieve formulieren in een adaptief formulier gebruiken.</li>
     <li>Elk formulier in een HTML5 Forms-formulierset wordt als een afzonderlijke transactie verwerkt. </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## Billable Interactive Communication en Form-centric AEM Workflows op OSGi API&#39;s {#billable-interactive-communication-and-form-centric-aem-workflows-on-osgi-apis}

Wijs taak en de stappen van de documentdiensten van vorm-centric AEM Workflows op OSGi en alle vertoningen van interactieve mededeling toe en zijn rekenschap gegeven als transacties. Het voorvertonen van een interactieve mededeling over de auteursinstantie en het voorvertonen op publiceer instantie gebruikend de UI van de Agent worden niet rekenschap gegeven als transacties. Als een workflowstap een transactie verwerkt en de workflow niet wordt voltooid, wordt het aantal transacties niet teruggedraaid.

### Interactieve communicatie - Webkanaal {#interactive-communication-web-channel}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschrijving</td>
   <td>Categorie Transactieverslag</td>
   <td>Aanvullende informatie</td>
  </tr>
  <tr>
   <td>Een webkanaal renderen</td>
   <td>Hiermee opent u de webversie van een interactieve communicatie.</td>
   <td>Gerenderde documenten</td>
   <td>
    <div>
    </div> </td>
  </tr>
 </tbody>
</table>

### Interactieve communicatie - Afdrukkanaal {#interactive-communication-print-channel}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschrijving</td>
   <td>Categorie Transactieverslag</td>
   <td>Aanvullende informatie</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/ccm/channels/print/api/model/PrintChannel.html" target="_blank">renderen</a> (converteren naar PDF)</td>
   <td>Genereert de PDF-versie van een interactieve communicatie.</td>
   <td>Gerenderde documenten</td>
   <td>
    <div>
    </div> </td>
  </tr>
 </tbody>
</table>

### Form-centric AEM Workflows op OSGi  {#form-centric-aem-workflows-on-osgi}

<table>
 <tbody>
  <tr>
   <td><p>Hoofdletters gebruiken</p> </td>
   <td>Categorie Transactieverslag</td>
   <td>Aanvullende informatie</td>
  </tr>
  <tr>
   <td>Een taakstap toewijzen verzenden</td>
   <td>Forms verzonden</td>
   <td>
    <div>
    </div> </td>
  </tr>
  <tr>
   <td>Een startpunt voor een workflowtoepassing indienen </td>
   <td>Forms verzonden</td>
   <td> </td>
  </tr>
  <tr>
   <td>Het voorleggen van een interactieve mededeling (het Kanaal van de Druk van de Agent UI aan een werkschema</td>
   <td>Gerenderde documenten</td>
   <td> </td>
  </tr>
 </tbody>
</table>

## Infactureerbare API&#39;s opnemen als transacties voor aangepaste code {#recording-billable-apis-as-transactions-for-custom-code}

Handelingen als het verzenden van een PDF-formulier, het gebruik van de gebruikersinterface van de Agent voor het weergeven van een interactieve communicatie, het gebruik van niet-standaardformulierverzending en aangepaste implementaties worden niet als transacties beschouwd. AEM Forms biedt een API om dergelijke handelingen op te nemen, zoals transacties. U kunt API van uw douaneimplementaties roepen om een transactie [te](/help/forms/using/record-transaction-custom-implementation.md)registreren.

## Verwante artikelen {#related-articles}

* [Overzicht van transactierapporten](../../forms/using/transaction-reports-overview.md)
* [Transactierapporten weergeven en begrijpen](../../forms/using/viewing-and-understanding-transaction-reports.md)
* [Een transactie opnemen voor aangepaste implementaties](/help/forms/using/record-transaction-custom-implementation.md)

