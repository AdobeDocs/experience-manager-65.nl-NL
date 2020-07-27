---
title: ConvertPDF-service
seo-title: ConvertPDF-service
description: Gebruik de AEM Forms ConvertPDF-service om PDF-documenten te converteren naar PostScript- of afbeeldingsbestanden.
seo-description: Gebruik de AEM Forms ConvertPDF-service om PDF-documenten te converteren naar PostScript- of afbeeldingsbestanden.
uuid: 7fa94c8c-485b-4a77-bcd3-ed716e3cf316
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
discoiquuid: 5ec4f0ec-a9fd-4571-9b9a-278f4622c028
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---


# ConvertPDF-service {#convertpdf-service}

## Overzicht {#overview}

Met de service PDF converteren worden PDF-documenten geconverteerd naar PostScript- of afbeeldingsbestanden (JPEG, JPEG 2000, PNG en TIFF). Het converteren van een PDF-document naar PostScript is handig voor afdrukken op basis van een server zonder toezicht op elke PostScript-printer. Het converteren van een PDF-document naar een TIFF-bestand met meerdere pagina&#39;s is handig bij het archiveren van documenten in inhoudsbeheersystemen die geen PDF-documenten ondersteunen.

U kunt het volgende doen met de service PDF converteren:

* Converteer PDF-documenten naar PostScript. Bij het converteren naar PostScript kunt u het brondocument met de conversiebewerking opgeven en of het document moet worden omgezet in PostScript-niveau 2 of 3. Het PDF-document dat u naar een PostScript-bestand converteert, moet niet-interactief zijn.
* Converteer PDF-documenten naar JPEG-, JPEG 2000-, PNG- en TIFF-afbeeldingsindelingen. Wanneer u naar een van deze afbeeldingsindelingen converteert, kunt u met de conversiebewerking het brondocument en een specificatie voor afbeeldingsopties opgeven. De specificatie bevat verschillende voorkeuren, zoals de indeling voor het omzetten van afbeeldingen, de afbeeldingsresolutie en kleurconversie.

## Eigenschappen van de service configureren   {#properties}

Met de **AEMFD ConvertPDF-service** in AEM-console kunt u eigenschappen voor deze service configureren. De standaard-URL van de AEM-console is `https://[host]:'port'/system/console/configMgr`.

## De service gebruiken {#using-the-service}

De service ConvertPDF biedt de volgende twee API&#39;s:

* **[naarPS](https://helpx.adobe.com/experience-manager/6-3/forms/javadocs/com/adobe/fd/cpdf/api/ConvertPdfService.html#toPS)**: Hiermee converteert u een PDF-document naar een PostScript-bestand.

* **[toImage](https://helpx.adobe.com/experience-manager/6-3/forms/javadocs/com/adobe/fd/cpdf/api/ConvertPdfService.html#toImage)**: Hiermee converteert u een PDF-document naar een afbeeldingsbestand. Ondersteunde afbeeldingsindelingen zijn JPEG, JPEG2000, PNG en TIFF.

### ToPS-API gebruiken met een JSP of Servlets {#using-tops-api-with-a-jsp-or-servlets}

```jsp
<%@ page import="java.util.List, java.io.File,

                com.adobe.fd.cpdf.api.ConvertPdfService,
                com.adobe.fd.cpdf.api.ToPSOptionsSpec,
                com.adobe.fd.cpdf.api.enumeration.PSLevel,

                com.adobe.aemfd.docmanager.Document" %><%
%><%@taglib prefix="sling" uri="https://sling.apache.org/taglibs/sling/1.0" %><%
%><sling:defineObjects/><%

 // Get reference to ConvertPdfService OSGi service.
 // Within an OSGi bundle @Reference annotation
 // can be used to retrieve service reference

 ConvertPdfService cpdfService = sling.getService(ConvertPdfService.class);

 // path to input document in AEM repository
 // please replace this with path to your document
String documentPath = "/content/dam/formsanddocuments/ExpenseClaimFlat.pdf";

 // Create a Docmanager Document object for
 // the flat PDF file which needs to be converted
 // to PostScript

 Document inputPDF = new Document(documentPath);

 // options object to pass to toPS API
 ToPSOptionsSpec toPSOptions = new ToPSOptionsSpec();

 // mandatory option to pass, sets PostScript langauge
 toPSOptions.setPsLevel(PSLevel.LEVEL_3);

 // invoke toPS method to convert inputPDF to PostScript
 Document convertedPS = cpdfService.toPS(inputPDF, toPSOptions);

 // save converted PostScript file to disk
 convertedPS.copyToFile(new File("C:/temp/out.ps"));

%>
```

### ToImage-API gebruiken met een JSP of Servlets {#using-toimage-api-with-a-jsp-or-servlets}

```jsp
<%@ page import="java.util.List, java.io.File,

                com.adobe.fd.cpdf.api.ConvertPdfService,
                com.adobe.fd.cpdf.api.ToImageOptionsSpec,
                com.adobe.fd.cpdf.api.enumeration.ImageConvertFormat,

                com.adobe.aemfd.docmanager.Document" %><%
%><%@taglib prefix="sling" uri="https://sling.apache.org/taglibs/sling/1.0" %><%
%><sling:defineObjects/><%

 // Get reference to ConvertPdfService OSGi service.
 // Within an OSGi bundle @Reference annotation
 // can be used to retrieve service reference

 ConvertPdfService cpdfService = sling.getService(ConvertPdfService.class);

 // path to input document in AEM repository
 // please replace this with path to your document
 String documentPath = "/content/dam/formsanddocuments/ExpenseClaimFlat.pdf";

 // Create a Docmanager Document object for
 // the flat PDF file which needs to be converted
 // to image

 Document inputPDF = new Document(documentPath);

 // options object to pass to toImage API
 ToImageOptionsSpec toImageOptions = new ToImageOptionsSpec();

 // mandatory option to pass, image format
 toImageOptions.setImageConvertFormat(ImageConvertFormat.JPEG);

 // invoke toImage method to convert inputPDF to Image
 List<Document> convertedImages = cpdfService.toImage(inputPDF, toImageOptions);

 // save converted image files to disk
 for(int i=0;i<convertedImages.size();i++){
     Document pageImage = convertedImages.get(i);
     pageImage.copyToFile(new File("C:/temp/out_"+(i+1)+".jpeg"));
 }

%>
```

### ConvertPDF Service gebruiken met AEM-workflows {#using-convertpdf-service-with-aem-workflows}

Het uitvoeren van de ConvertPDF-service vanuit een workflow lijkt op het uitvoeren vanuit JSP/Servlet.

Het enige verschil is bij het runnen van de dienst van JSP/Servlet het documentvoorwerp wint automatisch een geval van voorwerp ResourceResolver van het voorwerp ResourceResolverHelper terug. Dit automatische mechanisme werkt niet wanneer de code vanuit een workflow wordt aangeroepen. Voor een workflow geeft u expliciet een instantie van het object ResourceResolver door aan de klasseconstructor Document. Vervolgens gebruikt het object Document het aangeboden ResourceResolver-object om inhoud uit de opslagruimte te lezen.

In het volgende voorbeeldworkflowproces wordt het invoerdocument geconverteerd naar een PostScript-document. De code wordt geschreven in ECMAScript en het document wordt overgegaan als werkschemalading:

```javascript
/*
 * Imports
 */
var ConvertPdfService = Packages.com.adobe.fd.cpdf.api.ConvertPdfService;
var ToPSOptionsSpec = Packages.com.adobe.fd.cpdf.api.ToPSOptionsSpec;
var PSLevel = Packages.com.adobe.fd.cpdf.api.enumeration.PSLevel;
var Document = Packages.com.adobe.aemfd.docmanager.Document;
var File = Packages.java.io.File;
var ResourceResolverFactory = Packages.org.apache.sling.api.resource.ResourceResolverFactory;

// get reference to ConvertPdfService
var cpdfService = sling.getService(ConvertPdfService);

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

// options object to be passed to toPS operation
var toPSOptions = new ToPSOptionsSpec();

// Set PostScript Language Three
toPSOptions.setPsLevel(PSLevel.LEVEL_3);

// invoke toPS operation to convert inputDocument to PS
var convertedPS = cpdfService.toPS(inputDocument, toPSOptions);

// save converted PostScript file to disk
convertedPS.copyToFile(new File("C:/temp/out.ps"));
```

