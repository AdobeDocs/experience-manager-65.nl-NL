---
title: Barcoded Forms Service
seo-title: AEM Forms Barcoded Forms Service gebruiken
description: 'Met AEM Forms Barcoded Forms kunt u gegevens ophalen uit elektronische afbeeldingen van streepjescodes. '
seo-description: 'Met AEM Forms Barcoded Forms kunt u gegevens ophalen uit elektronische afbeeldingen van streepjescodes. '
uuid: b044a788-0e4a-4718-b71a-bd846933d51b
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
discoiquuid: d431c4cb-e4be-41a5-8085-42393d4d468c
docset: aem65
translation-type: tm+mt
source-git-commit: 317fadfe48724270e59644d2ed9a90fbee95cf9f

---


# Barcoded Forms Service{#barcoded-forms-service}

## Overzicht {#overview}

De service Barcoded Forms extraheert gegevens uit elektronische afbeeldingen van streepjescodes. De service accepteert TIFF- en PDF-bestanden die een of meer streepjescodes bevatten als invoer en extraheert de streepjescodegegevens. Streepjescodegegevens kunnen op verschillende manieren worden opgemaakt, zoals XML, tekenreeks met scheidingstekens of elke aangepaste indeling die met JavaScript is gemaakt.

De service Barcoded Forms ondersteunt de volgende **tweedimensionale (2D)** symbolen die worden geleverd als gescande TIFF- of PDF-documenten:

* PDF417
* Gegevensmatrix
* QR-code

De service ondersteunt ook de volgende **eendimensionale** symbolen die worden geleverd als gescande TIFF- of PDF-documenten:

* Codabar
* Code 128
* Code 3 of 9
* EAN13
* EAN8

Met de service Barcoded Forms kunt u de volgende taken uitvoeren:

* Hiermee extraheert u streepjescodegegevens uit streepjescodeafbeeldingen (TIFF of PDF). De gegevens worden opgeslagen als tekst met scheidingstekens.
* Zet afgebakende tekstgegevens om in XML (XDP of XFDF). XML-gegevens kunnen gemakkelijker worden geparseerd dan tekst met scheidingstekens. Gegevens in XDP- of XFDF-indeling kunnen ook worden gebruikt als invoer voor andere services in AEM Forms.

Voor elke streepjescode in een afbeelding zoekt de service Barcoded Forms de streepjescode, decodeert deze en extraheert de gegevens. De service retourneert de streepjescodegegevens (waarbij indien nodig eenheidcodering wordt gebruikt) in een inhoudselement van een XML-document. De volgende gescande TIFF-afbeelding van een formulier bevat bijvoorbeeld twee streepjescodes:

![voorbeeld](assets/example.png)

De service Barcoded Forms retourneert het volgende XML-document na het decoderen van de streepjescodes:

```xml
<?xml version="1.0" encoding="UTF-8" ?>  
<xb:scanned_image xmlns:xb="https://decoder.barcodedforms.adobe.com/xmlbeans"     path="tiff" version="1.0"> 
    <xb:decode> 
        <xb:date>2007-05-11T15:07:49.965-04:00</xb:date>  
        <xb:host_name>myhost.adobe.com</xb:host_name>  
        <xb:status type="success"> 
            <xb:message />  
        </xb:status> 
    </xb:decode> 
    <xb:barcode id="1"> 
        <xb:header symbology="pdf417"> 
            <xb:location page_no="1"> 
                <xb:coordinates> 
                    <xb:point x="0.119526625" y="0.60945123" />  
                    <xb:point x="0.44457594" y="0.60945123" />  
                    <xb:point x="0.44457594" y="0.78445125" />  
                    <xb:point x="0.119526625" y="0.78445125" />  
                </xb:coordinates> 
            </xb:location> 
        </xb:header> 
        <xb:body> 
            <xb:content encoding="utf-8">t_SID t_FirstName t_MiddleName t_LastName t_nFirstName t_nMiddleName t_nLastName 90210 Patti Y Penne Patti P Prosciutto</xb:content>  
        </xb:body> 
    </xb:barcode> 
    <xb:barcode id="2"> 
        <xb:header symbology="pdf417"> 
            <xb:location page_no="1"> 
                <xb:coordinates> 
                    <xb:point x="0.119526625" y="0.825" />  
                    <xb:point x="0.44457594" y="0.825" />  
                    <xb:point x="0.44457594" y="0.9167683" />  
                    <xb:point x="0.119526625" y="0.9167683" />  
                </xb:coordinates> 
            </xb:location> 
         </xb:header> 
        <xb:body> 
            <xb:content encoding="utf-8">t_FormType t_FormVersion ChangeName 20061128</xb:content>  
         </xb:body> 
    </xb:barcode> 
</xb:scanned_image>
```

## Overwegingen voor de dienst {#considerations}

### Workflows die formulieren met streepjescodes gebruiken {#workflows-that-use-barcoded-forms}

Formulierauteurs maken met Designer interactieve formulieren met streepjescodes. (Zie [Help bij](https://www.adobe.com/go/learn_aemforms_designer_63)Designer.) Wanneer een gebruiker een formulier met streepjescodes invult in Adobe Reader of Acrobat, wordt de streepjescode automatisch bijgewerkt om de formuliergegevens te coderen.

De service Barcoded Forms is handig voor het converteren van gegevens op papier naar elektronische indeling. Wanneer bijvoorbeeld een formulier met streepjescodes wordt gevuld en afgedrukt, kan de afgedrukte kopie worden gescand en worden gebruikt als invoer voor de service Barcoded Forms.

De gecontroleerde omslageindpunten worden typisch gebruikt om toepassingen te beginnen die de Barcoded dienst van Vormen gebruiken. Zo kunnen documentscanners TIFF- of PDF-afbeeldingen van formulieren met streepjescodes opslaan in een controlemap. Het gecontroleerde omslageindpunt gaat de beelden tot de dienst voor het decoderen over.

### Aanbevolen indelingen voor codering en decodering {#recommended-encoding-and-decoding-formats}

Auteurs van gecodeerde formulieren met streepjescodes wordt aangeraden een eenvoudige, gescheiden indeling (zoals door tabs gescheiden indeling) te gebruiken bij het coderen van gegevens in streepjescodes. Vermijd ook het gebruik van Enter als veldscheidingsteken. Designer biedt een selectie van gescheiden coderingen die automatisch JavaScript-script genereren om streepjescodes te coderen. De gedecodeerde gegevens hebben de veldnamen op de eerste regel en hun waarden op de tweede regel, met tabs tussen elk veld.

Geef bij het decoderen van streepjescodes het teken op dat wordt gebruikt om velden te scheiden. Het voor decodering opgegeven teken moet hetzelfde teken zijn als dat is gebruikt voor het coderen van de streepjescode. Als u bijvoorbeeld de aanbevolen tabgescheiden indeling gebruikt, moet de bewerking Extraheren naar XML de standaardwaarde van Tab gebruiken voor het veldscheidingsteken.

### Door de gebruiker opgegeven tekensets {#user-specified-character-sets}

Wanneer formulierauteurs met Designer streepjescodeobjecten aan hun formulieren toevoegen, kunnen ze een tekencodering opgeven. De erkende coderingen zijn UTF-8, ISO-8859-1, ISO-8859-2, ISO-8859-7, Shift-JIS, KSC-5601, Big-Five, GB-2312, UTF-16. Standaard worden alle gegevens in streepjescodes gecodeerd als UTF-8.

Bij het decoderen van streepjescodes kunt u opgeven welke codering voor tekensets moet worden gebruikt. Als u wilt garanderen dat alle gegevens correct worden gedecodeerd, geeft u dezelfde tekenset op als de auteur van het formulier heeft opgegeven bij het ontwerp van het formulier.

### API-beperkingen {#api-limitations}

Wanneer u BCF APIs gebruikt, overweeg de volgende beperkingen:

* Dynamische formulieren worden niet ondersteund.
* Interactieve formulieren worden niet correct gedecodeerd, tenzij ze worden afgevlakt.
* 1-D-streepjescodes mogen alleen alfanumerieke waarden bevatten (mits ondersteund). 1-D-streepjescodes die speciale symbolen bevatten, worden niet gedecodeerd.

### Andere beperkingen {#other-limitations}

Overweeg ook de volgende beperkingen wanneer u de service Barcoded Forms gebruikt:

* De service biedt volledige ondersteuning voor AcroForms en statische formulieren met 2D-streepjescodes die zijn opgeslagen met Adobe Reader of Acrobat. Voor 1D-streepjescodes voegt u het formulier echter samen of levert u het als gescand PDF- of TIFF-document.
* Dynamische XFA-formulieren worden niet volledig ondersteund. Als u 1D- en 2D-streepjescodes op de juiste manier wilt decoderen in een dynamisch formulier, voegt u het formulier samen of geeft u het op als gescand PDF- of TIFF-document.

Bovendien kan de service elke streepjescode decoderen die ondersteunde symbolen gebruikt als de bovenstaande beperkingen worden nageleefd. Raadpleeg de Help bij [Designer voor meer informatie over het maken van interactieve formulieren met streepjescodes](https://www.adobe.com/go/learn_aemforms_designer_63).

## Eigenschappen van de service configureren {#configureproperties}

Met de **AEMFD Barcoded Forms Service** in AEM Console kunt u eigenschappen voor deze service configureren. De standaard-URL van de AEM-console is `https://[host]:'port'/system/console/configMgr`.

## De service gebruiken {#using}

Barcoded Forms Service biedt de volgende twee API&#39;s:

* **[decoderen](https://helpx.adobe.com/experience-manager/6-3/forms/javadocs/com/adobe/fd/bcf/api/BarcodedFormsService.html#decode)**: Hiermee worden alle streepjescodes gedecodeerd die beschikbaar zijn in een PDF-invoerdocument of TIFF-afbeelding. Er wordt een ander XML-document geretourneerd dat gegevens bevat die zijn opgehaald uit alle streepjescodes die beschikbaar zijn in het invoerdocument of de afbeelding.

* **[extractToXML](https://helpx.adobe.com/experience-manager/6-3/forms/javadocs/com/adobe/fd/bcf/api/BarcodedFormsService.html#decode)**: Gegevens die zijn gedecodeerd met de decoder-API converteren naar XML-gegevens. Deze XML-gegevens kunnen worden samengevoegd met een XFA-formulier. Er wordt een lijst met XML-documenten geretourneerd, één voor elke streepjescode.

### De Dienst BCF met JSP of Servlets gebruiken {#using-bcf-service-with-a-jsp-or-servlets}

De volgende voorbeeldcode decodeert een streepjescode in een document en slaat de uitvoer-XML op de schijf op.

```java
<%@ page import="java.util.List,
                com.adobe.fd.bcf.api.BarcodedFormsService,
                com.adobe.fd.bcf.api.CharSet,
                com.adobe.fd.bcf.api.Delimiter,
                com.adobe.fd.bcf.api.XMLFormat,
                com.adobe.aemfd.docmanager.Document,
                javax.xml.transform.Transformer,
                javax.xml.transform.TransformerFactory,
                java.io.StringWriter,
                javax.xml.transform.stream.StreamResult,
                javax.xml.transform.dom.DOMSource,
                javax.servlet.jsp.JspWriter,
                org.apache.commons.lang.StringEscapeUtils" %><%
%><%@taglib prefix="sling" uri="https://sling.apache.org/taglibs/sling/1.0" %><%
%><sling:defineObjects/><%

 // Get reference to BarcodedForms OSGi service.
 // Within an OSGi bundle @Reference annotation 
 // can be used to retrieve service reference

 BarcodedFormsService bcfService = sling.getService(BarcodedFormsService.class);

 // Path to image containing barcodes in AEM repository. 
 // Replace this with path to image in your repository
 String documentPath = "/content/dam/TestImage-010.tif";

 // Create a Docmanager Document object for 
 // the tiff file containing barcode
 // Please see Docmanager Document javadoc for
 // more details
 Document inputDoc = new Document(documentPath);

 // Invoke decode operation of barcoded forms service 
 // Second parameter is set to true to decode PDF417 barcode symbology
 // Please see javadoc for details of parameters

 org.w3c.dom.Document result = bcfService.decode(inputDoc, // Input Document Object
                                                    true, 
                                                    false,  
                                                    false,
                                                    false,
                                                    false,
                                                    false,
                                                    false,
                                                    false,
                                                    CharSet.UTF_8);// use UTF-8 character encoding 

 out.println("<h2> Output Returned from decode operation </h2>");
 printDoc(result,out);

 // Invoke extractToXML to convert Carriage 
 // return / Tab delimited data to XML 

 List<org.w3c.dom.Document> listResult = bcfService.extractToXML(result, // w3c document from the output of decode operation
                                                                    Delimiter.Carriage_Return, // Lines are separated using "\r"
                                                                    Delimiter.Tab, // Fields are separated using "\t" 
                                                                    XMLFormat.XDP); // wraps generated XML in <xdp:xdp> packet

 out.println("<h2> Output returned from extractToXML </h2>");
 printDoc(listResult.get(0),out);

%><%!

 // helper function to convert w3c document to string

 String convertToString(org.w3c.dom.Document inputDoc) throws Exception {
   TransformerFactory tf = TransformerFactory.newInstance();
   Transformer tr = tf.newTransformer();
   StringWriter sw = new StringWriter();
   StreamResult sr = new StreamResult(sw);
   tr.transform(new DOMSource(inputDoc), sr);
   return sw.toString();
 }

 // helper function to render XML to response

 void printDoc(org.w3c.dom.Document inputDoc,JspWriter out) throws Exception {
   String escapedString = StringEscapeUtils.escapeHtml(convertToString(inputDoc));
   out.println(escapedString);
 }

%>
```

### De BCF-service gebruiken met AEM Workflows {#using-the-bcf-service-with-aem-workflows}

Het runnen van de Barcoded dienst van Vormen van een werkschema is gelijkaardig aan het runnen van de dienst van JSP/Servlet. Het enige verschil is bij het runnen van de dienst van JSP/Servlet het documentvoorwerp wint automatisch een geval van voorwerp ResourceResolver van het voorwerp ResourceResolverHelper terug. Dit automatische mechanisme werkt niet wanneer de code vanuit een workflow wordt aangeroepen.

Voor een workflow geeft u expliciet een instantie van het object ResourceResolver door aan de klasseconstructor Document. Vervolgens gebruikt het object Document het aangeboden ResourceResolver-object om inhoud uit de opslagruimte te lezen.

Het volgende voorbeeldwerkstroomproces decodeert een streepjescode in een document en slaat het resultaat op schijf op. De code wordt geschreven in ECMAScript en het document wordt overgegaan als werkschemalading:

```
/*
 * Imports 
 */
var BarcodedFormsService = Packages.com.adobe.fd.bcf.api.BarcodedFormsService;
var CharSet = Packages.com.adobe.fd.bcf.api.CharSet;

var Document = Packages.com.adobe.aemfd.docmanager.Document;
var File = Packages.java.io.File;
var FileOutputStream = Packages.java.io.FileOutputStream;
var TransformerFactory = Packages.javax.xml.transform.TransformerFactory;
var Transformer = Packages.javax.xml.transform.Transformer;
var StreamResult = Packages.javax.xml.transform.stream.StreamResult;
var DOMSource = Packages.javax.xml.transform.dom.DOMSource;

var ResourceResolverFactory = Packages.org.apache.sling.api.resource.ResourceResolverFactory;

// get reference to BarcodedFormsService
var bcfService = sling.getService(BarcodedFormsService);

/*
 * workflow payload and path to it
 */
var payload = graniteWorkItem.getWorkflowData().getPayload();
var payload_path = payload.toString();

/* Create resource resolver using current session 
 * this resource resolver needs to be passed to Document
 * object constructor when file is to be read from 
 * crx repository. 
 */

/* get ResourceResolverFactory service reference , used 
 * to construct resource resolver
 */
var resourceResolverFactory = sling.getService(ResourceResolverFactory);

var authInfo = {
    "user.jcr.session":graniteWorkflowSession.getSession()
};

var resourceResolver = resourceResolverFactory.getResourceResolver(authInfo);

// Create Document object from payload_path 
var inputDocument = new Document(payload_path, resourceResolver);

// invoke decode operation to decode barcodes in inputDocument
var decodedBarcode = bcfService.decode(inputDocument, true, false, false, false, false, false, false, false, CharSet.UTF_8);

// save decoded barcode data to disk
saveW3CDocument(decodedBarcode, "C:/temp/decoded.xml");

/*
 * Helper function to save W3C Document
 * to a file on disk
 */
function saveW3CDocument(inputDoc, filePath) {
   var tf = TransformerFactory.newInstance();
   var tr = tf.newTransformer();
   var os = new FileOutputStream(filePath);
   var sr = new StreamResult(os);
   tr.transform(new DOMSource(inputDoc), sr);
   os.close();
}
```

