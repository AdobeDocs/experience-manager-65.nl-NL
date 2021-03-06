---
title: Distiller Service Java API QuickStart (SOAP)
seo-title: Distiller Service Java API QuickStart (SOAP)
description: Distiller Service Java API QuickStart (SOAP)
uuid: 7781f074-cea4-4109-892b-118cfad4ec36
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
discoiquuid: 59dd61d1-c6b1-4bea-b666-4aa7897384a1
role: Developer
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---


# Distiller Service Java API Quick Start (SOAP) {#distiller-service-java-api-quickstart-soap}

Java API Quick Start (SOAP) is beschikbaar voor de Distiller┬«-service:

[Snel starten (SOAP-modus): Een PostScript-bestand converteren naar een PDF-document met de Java API](distiller-service-java-api-quick.md#quick-start-soap-mode-converting-a-postscript-file-to-a-pdf-document-using-the-java-api)

AEM Forms-bewerkingen kunnen worden uitgevoerd met behulp van de sterk getypte AEM Forms-API en de verbindingsmodus moet worden ingesteld op SOAP.

>[!NOTE]
>
>De snelle Beginnen die in Programmering met AEM vormen worden gevestigd zijn gebaseerd op de Server die van Forms op de Server van de Toepassing JBoss en het werkende systeem van Microsoft Windows wordt opgesteld. Als u echter een ander besturingssysteem gebruikt, zoals UNIX, vervangt u Windows-specifieke paden door paden die door het desbetreffende besturingssysteem worden ondersteund. Als u een andere J2EE-toepassingsserver gebruikt, moet u ook geldige verbindingseigenschappen opgeven. Zie [Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

## Snel starten (SOAP-modus): Een PostScript-bestand converteren naar een PDF-document met de Java API {#quick-start-soap-mode-converting-a-postscript-file-to-a-pdf-document-using-the-java-api}

In het volgende codevoorbeeld wordt een PostScript-bestand met de naam *Loan.ps* geconverteerd naar een PDF-bestand met de naam *Loan.pdf*. (Zie [PostScript converteren naar PDF-documenten](/help/forms/developing/converting-postscript-pdf-documents.md#converting-postscript-to-pdf-documents).)

```java
ÔÇë/*
ÔÇë    * This Java Quick Start uses the SOAP mode and contains the following JAR files
ÔÇë    * in the class path:
ÔÇë    * 1. adobe-distiller-client.jar
ÔÇë    * 2. adobe-livecycle-client.jar
ÔÇë    * 3. adobe-usermanager-client.jar
ÔÇë    * 4. adobe-utilities.jar
ÔÇë    * 5. jboss-client.jar (use a different JAR file if the forms server is not deployed
ÔÇë    * on JBoss)
ÔÇë    * 6. activation.jar (required for SOAP mode)
ÔÇë    * 7. axis.jar (required for SOAP mode)
ÔÇë    * 8. commons-codec-1.3.jar (required for SOAP mode)
ÔÇë    * 9.  commons-collections-3.1.jar  (required for SOAP mode)
ÔÇë    * 10. commons-discovery.jar (required for SOAP mode)
ÔÇë    * 11. commons-logging.jar (required for SOAP mode)
ÔÇë    * 12. dom3-xml-apis-2.5.0.jar (required for SOAP mode)
ÔÇë    * 13. jaxen-1.1-beta-9.jar (required for SOAP mode)
ÔÇë    * 14. jaxrpc.jar (required for SOAP mode)
ÔÇë    * 15. log4j.jar (required for SOAP mode)
ÔÇë    * 16. mail.jar (required for SOAP mode)
ÔÇë    * 17. saaj.jar (required for SOAP mode)
ÔÇë    * 18. wsdl4j.jar (required for SOAP mode)
ÔÇë    * 19. xalan.jar (required for SOAP mode)
ÔÇë    * 20. xbean.jar (required for SOAP mode)
ÔÇë    * 21. xercesImpl.jar (required for SOAP mode)
ÔÇë    *
ÔÇë    * These JAR files are located in the following path:
ÔÇë    * <install directory>/sdk/client-libs/common
ÔÇë    *
ÔÇë    * The adobe-utilities.jar file is located in the following path:
ÔÇë    * <install directory>/sdk/client-libs/jboss
ÔÇë    *
ÔÇë    * The jboss-client.jar file is located in the following path:
ÔÇë    * <install directory>/jboss/bin/client
ÔÇë    *
ÔÇë    * SOAP required JAR files are located in the following path:
ÔÇë    * <install directory>/sdk/client-libs/thirdparty
ÔÇë    *
ÔÇë    * If you want to invoke a remote forms server instance and there is a
ÔÇë    * firewall between the client application and the server, then it is
ÔÇë    * recommended that you use the SOAP mode. When using the SOAP mode,
ÔÇë    * you have to include these additional JAR files
ÔÇë    *
ÔÇë    * For information about the SOAP
ÔÇë    * mode, see "Setting connection properties" in Programming
ÔÇë    * with AEM Forms
ÔÇë    */

ÔÇëimport java.io.File;
ÔÇëimport java.io.FileInputStream;
ÔÇëimport java.util.Properties;
ÔÇëimport com.adobe.livecycle.generatepdf.client.CreatePDFResult;
ÔÇëimport com.adobe.idp.Document;
ÔÇëimport com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
ÔÇëimport com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
ÔÇëimport com.adobe.livecycle.distiller.client.DistillerServiceClient;

ÔÇëpublic class JavaAPICreatePDFSoap {

ÔÇë    public static void main(String[] args)
ÔÇë    {
ÔÇë        try
ÔÇë        {
ÔÇë        //Set connection properties required to invoke AEM Forms using SOAP mode
ÔÇë        Properties connectionProps = new Properties();
ÔÇë        connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://'[server]:[port]'");
ÔÇë        connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
ÔÇë        connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
ÔÇë        connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
ÔÇë        connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");

ÔÇë        // Create a ServiceClientFactory instance
ÔÇë        ServiceClientFactory factory = ServiceClientFactory.createInstance(connectionProps);

ÔÇë        DistillerServiceClient disClient = new DistillerServiceClient(factory );

ÔÇë        // Get a PS file document to convert to a PDF document and populate a com.adobe.idp.Document object
ÔÇë        String inputFileName = "C:\\Adobe\Loan.ps";
ÔÇë        FileInputStream fileInputStream = new FileInputStream(inputFileName);
ÔÇë        Document inDoc = new Document(fileInputStream);

ÔÇë        //Set run-time options
ÔÇë        String adobePDFSettings = "Standard";
ÔÇë         String securitySettings = "No Security";

ÔÇë         //Convert a PS  file into a PDF file
ÔÇë        CreatePDFResult result = new CreatePDFResult();
ÔÇë        result = disClient.createPDF(
ÔÇë                inDoc,
ÔÇë                inputFileName,
ÔÇë                     adobePDFSettings,
ÔÇë                securitySettings,
ÔÇë                null,
ÔÇë                null
ÔÇë            );

ÔÇë         //Get the newly created document
ÔÇë         Document createdDocument = result.getCreatedDocument();

ÔÇë         //Save the PDF file
ÔÇë        createdDocument.copyToFile(new File("C:\\Adobe\Loan.pdf"));
ÔÇë        }
ÔÇë        catch (Exception e) {
ÔÇë            e.printStackTrace();
ÔÇë        }
ÔÇë    }
ÔÇë}
```
