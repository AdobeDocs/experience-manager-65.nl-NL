---
title: Transactierapporten Billable-API's voor AEM Forms op JEE.
description: Lijst met alle API's die worden beschouwd als transacties voor AEM Forms op JEE.
topic-tags: forms-manager
feature: Transaction Reports
exl-id: dbb22369-c0a2-4cf6-b01b-096b4de13a14
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '803'
ht-degree: 0%

---

# Transactierapportage Billable API&#39;s voor AEM Forms op JEE {#transaction-reports-billable-apis}

AEM Forms on JEE biedt verschillende API&#39;s voor het verzenden, verwerken en renderen van documenten. Sommige API&#39;s worden beschouwd als transacties en andere kunnen gratis worden gebruikt. Dit document bevat een lijst met alle API&#39;s die worden beschouwd als transacties. Hier volgen enkele veelvoorkomende scenario&#39;s waarbij een factureerbare API wordt gebruikt:

* Een document omzetten van de ene naar de andere indeling
* Een dynamisch PDF-document afvlakken
* Een interactief PDF-document samenvoegen met een ander PDF-document

Factuur-API&#39;s zijn niet geschikt voor het aantal pagina&#39;s, de lengte van een document of formulier of de uiteindelijke indeling van het gerenderde document.
<!--

* **Forms Submitted:** When data is submitted from any type of form created with AEM Forms and the data is submitted to any data storage repository or database is considered form submission. For example, submitting an HTML5 Form, PDF Forms are accounted as forms submitted. Each form in a form set is considered a submission. For example, if a form set has 5 forms, when the form set is submitted, transaction reporting service counts it as 5 submissions.

* **Documents Rendered:** Generating a document by combining a template and data, digitally signing or certifying a document, using a billable document services API for document services, or converting a document from one format to another are accounted as documents rendered.

-->

Hieronder ziet u de lijst met JEE-factureerbare API&#39;s. De lijst met [factureerbare API&#39;s voor AEM Forms op OSGi](/help/forms/using/transaction-reports-billable-apis.md).

## Billable Document Services API&#39;s {#billable-document-services-apis}

### PDF-service genereren {#generate-pdf-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschrijving</td>
   <td>Categorie Transactieverslag</td>
  </tr>
   <tr>
   <td><a>CreatePDF</a></td>
   <td>Maakt Adobe PDF voor ondersteunde bestandstypen.</td>
   <td>Conversie<br /> </td>
  </tr>
  <tr>
   <td><a>CreatePDF3</a></td>
   <td>Maakt Adobe PDF voor ondersteunde bestandstypen. </td>
   <td>Conversie<br /> </td>
  </tr>
  <tr>
   <td><a> HtmlToPDF</a></td>
   <td>Hiermee converteert u het HTML-bestand naar Adobe PDF. </td>
   <td>Conversie<br /> </td>
  </tr>
  <tr>
   <td><a>ExportPDF</a></td>
   <td>Hiermee exporteert u PDF naar ondersteunde bestandstypen. </td>
   <td>Conversie<br /> </td>
  </tr>
  <tr>
   <td><a>ExportPDF2</a></td>
   <td><p>Hiermee exporteert u PDF naar ondersteunde bestandstypen.</p> </td>
   <td>Conversie<br /> </td>
  </tr>
  <tr>
   <td><a>ExportPDF3</a></td>
   <td>Hiermee exporteert u PDF naar ondersteunde bestandstypen.</td>
   <td>Conversie<br /> </td>
  </tr>
  <tr>
   <td><a>HtmlFileToPDF</a></td>
   <td>Hiermee wordt het HTML-bestand omgezet in PDF.</td>
   <td>Conversie<br /> </td>
  </tr>
  <tr>
   <td><a>HtmlToPDF2</a></td>
   <td>Hiermee wordt het HTML-bestand omgezet in PDF.</td>
   <td>Conversie<br /> </td>
  </tr>
  <tr>
   <td><a>PDF optimaliseren</a></td>
   <td>Hiermee optimaliseert u PDF om de bestandsgrootte te beperken door overbodige metagegevens uit te knippen zonder dat dit van invloed is op de kwaliteit.</td>
   <td>Conversie<br /> </td>
  </tr>
 </tbody>
</table>

### DocAssurance Service {#DocAssurance-Service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschrijving</td>
   <td>Categorie Transactieverslag</td>
  </tr>
  <tr>
   <td><a>Ondertekenen/certificeren</a><br /> </td>
   <td>Met deze API kunt u uw document beveiligen. Met de API kunt u een PDF-document ondertekenen en certificeren.</td>
   <td>Conversie</td>
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
  </tr>
  <tr>
  <tr>
   <td><a>CreatePDF</a></td>
   <td>Maakt Adobe PDF van ondersteunde bestandstypen.</td>
   <td>Conversie</td>
  </tr>
  <tr>
   <td><a>CreatePDF2</a></td>
   <td>Maakt Adobe PDF van ondersteunde bestandstypen.</td>
   <td>Conversie</td>
  </tr>
 </tbody>
</table>

<!--

### Document of Record Service (DoR Service) {#document-of-record-service-dor-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/aemds/guide/addon/dor/DoRService.html#render-com.adobe.aemds.guide.addon.dor.DoROptions-" target="_blank">render</a></td>
   <td>Invokes the specified render method to generate a document of record using provided parameters.</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
 </tbody>
</table>

-->

### Uitvoerservice {#output-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschrijving</td>
   <td>Categorie Transactieverslag</td>
  </tr>
  <tr>
   <td><a>generateOutput</a></td>
   <td>Hiermee voegt u gegevens en sjablonen samen om een PDF-document te maken.</td>
   <td>Gerenderde documenten</td>
  </tr>
  <tr>
   <td><a>generatePDFOutput</a></td>
   <td>Hiermee voegt u gegevens en sjablonen samen om een PDF-document te maken.</td>
   <td>Gerenderde documenten</td>
  </tr>
  <tr>
   <td><a>generatePDFOutput2</a></td>
   <td>Hiermee voegt u gegevens en sjablonen samen om een PDF-document te maken.</td>
   <td>Gerenderde documenten</td>
  </tr>
  <tr>
   <td><a>generatePrintedOutput</a></td>
   <td>XDP- en PDF-documenten worden omgezet in de bestandsindelingen PostScript (PS), Printer Command Language (PCL) en ZPL. </td>
   <td>Gerenderde documenten</td>
  </tr>
  <tr>
   <td><a>generatePrintedOutput2</a></td>
   <td>XDP- en PDF-documenten worden omgezet in de bestandsindelingen PostScript (PS), Printer Command Language (PCL) en ZPL. </td>
   <td>Gerenderde documenten</td>
  </tr>
  <tr>
   <td><a>transformPDF</a></td>
   <td>Hiermee converteert u een set XDP- en PDF-documenten naar een set PostScript- (PS), Printer Command Language (PCL)- en ZPL-bestandsindelingen. </td>
   <td>Documenten converteren</td>
  </tr>
 </tbody>
</table>

<!-- ### Forms Service {#forms-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/forms/api/FormsService.html#renderPDFForm-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.fd.forms.api.PDFFormRenderOptions-" target="_blank">renderPDFForm</a></td>
   <td>Renders PDF Form from XDP templates. The XDP templates are created in Forms Designer.</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/forms/api/FormsService.html#exportData-com.adobe.aemfd.docmanager.Document-com.adobe.fd.forms.api.DataFormat-" target="_blank">exportData</a></td>
   <td>Extracts data from a PDF Form or XDP templates</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
 </tbody>
</table>

-->

### PDF-service converteren {#convert-pdf-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschrijving</td>
   <td>Categorie Transactieverslag</td>
  </tr>
  <tr>
   <td><a>toImage2</a></td>
   <td>Hiermee wordt een PDF-document omgezet in een lijst met afbeeldingsdocumenten. Ondersteunde afbeeldingsindelingen zijn JPEG, JPEG, 2K, PNG en TIFF.</td>
   <td>Documenten converteren</td>
  </tr>
  <tr>
   <td><a>naarPS2</a></td>
   <td>Zet een Flat PDF-bestand om in PostScript-indeling met de opties die zijn opgegeven in de optiespecc.</td>
   <td>Documenten converteren</td>
  </tr>
  <tr>
   <td><a>toSWF</a></td>
   <td>Zet een Flat-PDF-bestand om in de SWF-indeling met behulp van de opties die zijn opgegeven in de optiesspecificatie.</td>
   <td>Documenten converteren</td>
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
  </tr>
  <tr>
   <td><a>decoderen</a></td>
   <td>Decodeert alle streepjescodes in een object Document en retourneert een object org.w3c.dom.Document dat gegevens bevat die uit de streepjescode zijn opgehaald.</td>
   <td>Documenten converteren</td>
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
  </tr>
  <tr>
   <td><a>oproepen</a></td>
   <td>Voert het gespecificeerde document DDX uit en keert een voorwerp AssemblerResult terug die de resulterende documenten bevat. </td>
   <td>Documenten converteren</td>
  </tr>
  <tr>
   <td><a>invokeDDX</a></td>
   <td>Voert het gespecificeerde document DDX uit en keert een voorwerp AssemblerResult terug die de resulterende documenten bevat. </td>
   <td>Documenten converteren</td>
  </tr>
  <tr>
   <td><a>invokeOneDocument</a></td>
   <td>Zet een opgegeven document om in PDF/A met de opgegeven opties.</td>
   <td>Documenten converteren</td>
  </tr>
  <tr>
   <td><a>invokeDDXOneDocument</a></td>
   <td>Zet een opgegeven document om in PDF/A met de opgegeven opties.</td>
   <td>Documenten converteren</td>
  </tr>
  <tr>
   <td><a>toPDFA</a></td>
   <td>Zet een opgegeven document om in PDF/A met de opgegeven opties.</td>
   <td>Documenten converteren</td>
  </tr>
 </tbody>
</table>

Het gebruik van de API voor aanroepen wordt als een transactie geteld wanneer u een of meer van de volgende bewerkingen uitvoert:
1. Conversie van niet-PDF-indelingen naar PDF-indelingen. Bijvoorbeeld de conversie van XDP-indeling naar PDF-indeling.<!-- catering to both interactive and non-interactive forms of communication, and the conversion from Word to PDF.-->
1. Omzetten van PDF-indeling naar PDF/A-indeling.
1. Conversie van PDF-indeling naar niet-PDF-indeling. Voorbeelden hiervan zijn de transformatie van de indeling PDF naar Afbeelding of de conversie van de indeling PDF naar tekst.

>[!NOTE]
>
>* De invoke API van de assemblageservice kan intern een factureerbare API van een andere service oproepen, afhankelijk van de invoer. Dus de `invoke API` kan administratief worden verwerkt als geen, enkele of meerdere transacties. Het aantal transacties dat wordt geteld, is afhankelijk van de invoer en de interne API&#39;s die worden aangeroepen.
>* Eén PDF-document dat is gemaakt met montagedienst, zoals `invoke` en `invokeDDX`, kan administratief worden verwerkt als geen, enkele of meerdere transacties. Het aantal getelde transacties is afhankelijk van de geleverde <!--DDX--> code.

<!--
### PDF Utility Service  {#pdf-utility-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td><a>convertPDFtoXDP</a></td>
   <td>Converts a PDF document into an XDP file. For a PDF document to be successfully converted to an XDP file, the PDF document must contain an XFA stream in the AcroForm dictionary.</td>
   <td>Documents Conversion</td>
   <td> </td>
  </tr>
 </tbody>
</table>

-->

## Billable Data Capture API&#39;s {#billable-data-capture-apis}

<!--All the submission events of Forms, HTML5 Forms, and form set are accounted as transactions. By default, submission of a PDF Form is not accounted as a transaction. Use the provided [transaction recorder API](record-transaction-custom-implementation.md) to record a PDF Forms submission as a transaction.-->

<!--
### Adaptive Forms {#adaptive-forms}

<table>
 <tbody>
  <tr>
   <td><p>Use Case</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td>Submitting an adaptive form</td>
   <td>Submits an adaptive form to configured submit action. </td>
   <td>Forms Submitted</td>
   <td>
    <ul>
     <li>Successful submissions account for single or two transactions. The number of transactions counted depends upon the type of submit action used for submission. For example, sending PDF through email submit action accounts for two counts of transactions. One transaction for form submission and another for PDF generated using the Document of Record (DOR) service. </li>
     <li>Using the adaptive form within an adaptive form (Adaptive form formset) accounts only single transaction. You can have any number of adaptive forms within an adaptive form.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

-->

<!--### HTML5 Forms {#html-forms}

<table>
 <tbody>
  <tr>
   <td><p>Use Case</p> </td>
   <td>Description </td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td>Submitting an HTML5 Form</td>
   <td>Submits an HTML5 Form to submit URL configured in the form.</td>
   <td>Forms Submitted</td>
   <td> </td>
  </tr>
 </tbody>
</table>

-->

### Forms {#form-set}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschrijving</td>
   <td>Categorie Transactieverslag</td>
  </tr>
  <tr>
   <td>exportData</td>
   <td>Hiermee verzendt u het formulier.</td>
   <td>Forms verzonden</td>
  </tr>
  <tr>
   <td>exportData2</td>
   <td>Hiermee verzendt u het formulier.</td>
   <td>Forms verzonden</td>
  </tr>
  <tr>
   <td>renderForm</td>
   <td>Hiermee verzendt u het formulier.</td>
   <td>Forms gerenderd</td>
  </tr>
  <tr>
   <td>renderHTMLForm</td>
   <td>Hiermee verzendt u het formulier.</td>
   <td>Forms gerenderd</td>
  </tr>
  <tr>
   <td>renderHTMLForm2</td>
   <td>Hiermee verzendt u het formulier.</td>
   <td>Forms gerenderd</td>
  </tr>
  <tr>
   <td>renderPDFForm</td>
   <td>Hiermee verzendt u het formulier.</td>
   <td>Forms gerenderd</td>
  </tr>
  <tr>
   <td>renderPDFForm2</td>
   <td>Hiermee verzendt u het formulier.</td>
   <td>Forms gerenderd</td>
  </tr>
  <tr>
   <td>renderPDFFormWithUsageRights</td>
   <td>Hiermee verzendt u het formulier.</td>
   <td>Forms gerenderd</td>
  </tr>
 </tbody>
</table>

<!-- ## Billable Interactive Communication and Form-centric AEM Workflows on OSGi APIs {#billable-interactive-communication-and-form-centric-aem-workflows-on-osgi-apis}

Assign task and document services steps of Form-centric AEM Workflows on OSGi and all the renditions of interactive communication and are accounted as transactions. Previewing an interactive communication on the author instance and previewing on the publish instance using Agent UI are not accounted as transactions. If a workflow step accounts a transaction and the workflow fails to complete, the transaction count is not reversed.

<!--

### Interactive Communication - Web Channel {#interactive-communication-web-channel}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td>Rendering a web channel</td>
   <td>Opens the web version of an interactive communication.</td>
   <td>Documents Rendered</td>
   <td>
    <div>
    </div> </td>
  </tr>
 </tbody>
</table>

### Interactive Communication - Print Channel {#interactive-communication-print-channel}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/ccm/channels/print/api/model/PrintChannel.html" target="_blank">render</a> (convert to PDF)</td>
   <td>Generates the PDF version of an interactive communication.</td>
   <td>Documents Rendered</td>
   <td>
    <div>
    </div> </td>
  </tr>
 </tbody>
</table>

-->


<!--
### Form-centric AEM Workflows on OSGi  {#form-centric-aem-workflows-on-osgi}

<table>
 <tbody>
  <tr>
   <td><p>Use case</p> </td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td>Submitting an Assign Task step</td>
   <td>Forms Submitted</td>
   <td>
    <div>
    </div> </td>
  </tr>
  <tr>
   <td>Submitting a workflow application startpoint </td>
   <td>Forms Submitted</td>
   <td> </td>
  </tr>
  <tr>
   <td>Submitting an interactive communication (Print Channel) from the Agent UI to a workflow</td>
   <td>Documents Rendered</td>
   <td> </td>
  </tr>
 </tbody>
</table>

-->


<!--

WILL ADD THIS ONE - 

## Recording billable APIs as transactions for custom code {#recording-billable-apis-as-transactions-for-custom-code}

Actions like submitting a PDF Form, using Agent UI to preview an interactive communication, using non-standard form submission, and custom implementations are not accounted as transactions. AEM Forms provides an API to record such actions as transactions. You can call the API from your custom implementations to [record a transaction](/help/forms/using/record-transaction-custom-implementation.md).

## Related Articles {#related-articles}

* [Transaction Reports Overview](../../forms/using/transaction-reports-overview.md)
* [Viewing and Understanding a Transaction Reports](../../forms/using/viewing-and-understanding-transaction-reports.md)
* [Record a transaction for custom implementations](/help/forms/using/record-transaction-custom-implementation.md)

-->

## Verwante artikelen

* [Transactierapport inschakelen en weergeven voor AEM Forms op JEE](/help/forms/using/transaction-report-overview-jee.md)
* [Een transactie voor aangepaste component-API&#39;s voor AEM Forms opnemen in JEE](/help/forms/using/record-transaction-custom-component-jee.md)
