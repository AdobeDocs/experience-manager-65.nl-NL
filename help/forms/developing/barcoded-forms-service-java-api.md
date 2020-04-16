---
title: Java APIQuick Start (SOAP) Barcoded Forms Service
seo-title: Java APIQuick Start (SOAP) Barcoded Forms Service
description: 'null'
seo-description: 'null'
uuid: a6739695-ee0b-4480-8cef-0f91a72deaad
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
discoiquuid: 245b9cc4-5837-4a22-b5f4-a1d4c5d66918
translation-type: tm+mt
source-git-commit: f9389a06f9c2cd720919486765cee76257f272c3

---


# Barcoded Forms Service Java API Quick Start (SOAP) {#barcoded-forms-service-java-apiquick-start-soap}

Java API Quick Start (SOAP) is beschikbaar voor de service Barcoded Forms:

[Snel starten (SOAP-modus): Gecodeerde formuliergegevens decoderen met de Java API](barcoded-forms-service-java-api.md#quick-start-soap-mode-decoding-barcoded-form-data-using-the-java-api)

De verrichtingen van de Vormen van AEM kunnen worden uitgevoerd gebruikend sterk-getypte API van Vormen AEM en de verbindingswijze zou aan ZEEP moeten worden geplaatst.

>[!NOTE]
>
>Quick Start die in Programming with AEM vormen wordt gevestigd is gebaseerd op de Server die van Vormen op de Server van de Toepassing JBoss en het werkende systeem van Microsoft Windows wordt opgesteld. Als u echter een ander besturingssysteem gebruikt, zoals UNIX, vervangt u Windows-specifieke paden door paden die door het desbetreffende besturingssysteem worden ondersteund. Als u een andere J2EE-toepassingsserver gebruikt, moet u ook geldige verbindingseigenschappen opgeven. Zie Verbindingseigenschappen [instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

## Snel starten (SOAP-modus): Gecodeerde formuliergegevens decoderen met de Java API {#quick-start-soap-mode-decoding-barcoded-form-data-using-the-java-api}

De volgende Java-code decodeert formuliergegevens die zich bevinden in een PDF-formulier dat is opgeslagen als Loan.pdf. De gedecodeerde gegevens worden opgeslagen als een XML-bestand met de naam extractedData.xml. In dit codevoorbeeld wordt een `org.w3c.dom.Document` object geconverteerd naar een `com.adobe.idp.Document` object. (Zie [Gecodeerde formuliergegevens](/help/forms/developing/barcoded-forms.md#decoding-barcoded-form-data)decoderen.)

```as3
 /*
     * This Java Quick Start uses the SOAP mode and contains the following JAR files
     * in the class path:
     * 1. adobe-barcodedforms-client.jar
     * 2. adobe-livecycle-client.jar
     * 3. adobe-usermanager-client.jar
     * 4. adobe-utilities.jar
     * 5. jboss-client.jar (use a different JAR file if the forms server is not deployed
     * on JBoss)
     * 6. activation.jar (required for SOAP mode)
     * 7. axis.jar (required for SOAP mode)
     * 8. commons-codec-1.3.jar (required for SOAP mode)
     * 9.  commons-collections-3.1.jar  (required for SOAP mode)
     * 10. commons-discovery.jar (required for SOAP mode)
     * 11. commons-logging.jar (required for SOAP mode)
     * 12. dom3-xml-apis-2.5.0.jar (required for SOAP mode)
     * 13. jaxen-1.1-beta-9.jar (required for SOAP mode)
     * 14. jaxrpc.jar (required for SOAP mode)
     * 15. log4j.jar (required for SOAP mode)
     * 16. mail.jar (required for SOAP mode)
     * 17. saaj.jar (required for SOAP mode)
     * 18. wsdl4j.jar (required for SOAP mode)
     * 19. xalan.jar (required for SOAP mode)
     * 20. xbean.jar (required for SOAP mode)
     * 21. xercesImpl.jar (required for SOAP mode)
     *
     * These JAR files are located in the following path:
     * <install directory>/sdk/client-libs/common
     *
     * The adobe-utilities.jar file is located in the following path:
     * <install directory>/sdk/client-libs/jboss
     *
     * The jboss-client.jar file is located in the following path:
     * <install directory>/jboss/bin/client
     *
     * SOAP required JAR files are located in the following path:
     * <install directory>/sdk/client-libs/thirdparty
     *
     * If you want to invoke a remote forms server instance and there is a
     * firewall between the client application and the server, then it is
     * recommended that you use the SOAP mode. When using the SOAP mode,
     * you have to include these additional JAR files
     *
     * For information about the SOAP
     * mode, see "Setting connection properties" in Programming
     * with AEM Forms
     */
 import java.io.*;
 import java.util.Iterator;
 import java.util.List;
 import java.util.Properties;
 import javax.xml.transform.*;
 import javax.xml.transform.dom.DOMSource;
 import javax.xml.transform.stream.StreamResult;
 import com.adobe.livecycle.barcodedforms.CharSet;
 import com.adobe.livecycle.barcodedforms.Delimiter ;
 import com.adobe.livecycle.barcodedforms.XMLFormat ;
 import com.adobe.idp.Document;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
 import com.adobe.livecycle.barcodedforms.client.*;
 
 public class DecodeFormDataSOAP {
 
     public static void main(String[] args) {
 
     try
         {
         //Set connection properties required to invoke AEM Forms
         Properties connectionProps = new Properties();
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://'[server]:[port]'");
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
         connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
 
         //Create a ServiceClientFactory object
         ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps);
         BarcodedFormsServiceClient barClient = new BarcodedFormsServiceClient(myFactory);
 
         //Specify a PDF document to convert to a XDP file
         FileInputStream fileInputStream = new FileInputStream("C:\\Adobe\LoanBarForms.pdf");
         Document inDoc = new Document (fileInputStream);
 
         java.lang.Boolean myFalse = new java.lang.Boolean(false);
         java.lang.Boolean myTrue = new java.lang.Boolean(true);
 
         //Decode barcoded form data
         org.w3c.dom.Document decodeXML = barClient.decode(
             inDoc,
             myTrue,
             myFalse,
             myFalse,
             myFalse,
             myFalse,
             myFalse,
             myFalse,
             myFalse,
             CharSet.UTF_8);
 
         //Convert the decoded data to XDP data
         List extractedData = barClient.extractToXML(
             decodeXML,
             Delimiter.Carriage_Return,
             Delimiter.Tab,
             XMLFormat.XDP);
 
         //Create an Iterator object and iterate through
         //the List object
         Iterator iter = extractedData.iterator();
         int i = 0 ;
 
         while (iter.hasNext()) {
 
             //Get the org.w3c.dom.Document object in each element
             org.w3c.dom.Document myDom = (org.w3c.dom.Document)iter.next();
 
             //Convert the org.w3c.dom.Document object to a
             //com.adobe.idp.Document object
             com.adobe.idp.Document myDocument = convertDOM(decodeXML);
 
             //Save the XML data to extractedData.xml
             File myFile = new File("C:\\Adobe\extractedData"+i+".xml");
 
             myDocument.copyToFile(myFile);
             i++;
             }
         }
     catch(Exception e)
         {
             e.printStackTrace();
         }
     }
 
 
     //This user-defined method converts an org.w3c.dom.Document to a
     //com.adobe.idp.Document object
     public static com.adobe.idp.Document convertDOM(org.w3c.dom.Document doc)
         {
 
             byte[] mybytes = null ;
         com.adobe.idp.Document myDocument = null;
         try
             {
 
             //Create a Java Transformer object
          TransformerFactory transFact = TransformerFactory.newInstance();
          Transformer transForm = transFact.newTransformer();
 
          //Create a Java ByteArrayOutputStream object
          ByteArrayOutputStream myOutStream = new ByteArrayOutputStream();
 
         //Create a Java Source object
          Source myInput = new DOMSource(doc);
 
         //Create a Java Result object
          Result myOutput = new StreamResult(myOutStream);
 
         //Populate the Java ByteArrayOutputStream object
          transForm.transform(myInput,myOutput);
 
         //Get the size of the ByteArrayOutputStream buffer
          int myByteSize = myOutStream.size();
 
         //Allocate myByteSize to the byte array
         mybytes = new byte[myByteSize];
 
         //Copy the content to the byte array
         mybytes = myOutStream.toByteArray();
         com.adobe.idp.Document myDoc = new com.adobe.idp.Document(mybytes);
 
          myDocument = myDoc ;
          }
 
         catch(Exception ee)
         {
             ee.printStackTrace();
         }
 
     return myDocument;
       }
 }
```

>[!NOTE]
>
>Wanneer u zowel een `org.w3c.dom.Document` object als een `com.adobe.idp.Document` object in dezelfde toepassingslogica gebruikt, is het een goede gewoonte om beide objecten volledig te kwalificeren.

