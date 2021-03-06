---
title: JavaAPI Quick Start (SOAP), service voor integratie van formuliergegevens
seo-title: JavaAPI Quick Start (SOAP), service voor integratie van formuliergegevens
description: Met de service Formuliergegevensintegratie kunt u gegevens in een PDF-formulier importeren en gegevens uit een PDF-formulier exporteren met de Java API.
seo-description: Met de service Formuliergegevensintegratie kunt u gegevens in een PDF-formulier importeren en gegevens uit een PDF-formulier exporteren met de Java API.
uuid: bde8e83d-56d3-4331-a025-82b327c219b7
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
discoiquuid: 91b738ec-aa00-4f05-bf42-2574ced8d993
role: Developer
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---


# Java API Quick Start (SOAP) {#form-data-integration-service-javaapi-quick-start-soap}

De volgende Snelle Beginnen zijn beschikbaar voor de dienst van de Integratie van de Gegevens van de Vorm.

[Snel starten (SOAP-modus): Formuliergegevens importeren met de Java API](form-data-integration-service-java.md#quick-start-soap-mode-importing-form-data-using-the-java-api)

[Snel starten (SOAP-modus): Formuliergegevens exporteren met de Java API](form-data-integration-service-java.md#quick-start-soap-mode-exporting-form-data-using-the-java-api)

AEM Forms-bewerkingen kunnen worden uitgevoerd met behulp van de sterk getypte AEM Forms-API en de verbindingsmodus moet worden ingesteld op SOAP.

>[!NOTE]
>
>De snelle Begin die in Programmering met AEM vormen wordt gevestigd is gebaseerd op de Server die van Forms op de Server van de Toepassing JBoss en het werkende systeem van Microsoft Windows wordt opgesteld. Als u echter een ander besturingssysteem gebruikt, zoals UNIX, vervangt u Windows-specifieke paden door paden die door het desbetreffende besturingssysteem worden ondersteund. Als u een andere J2EE-toepassingsserver gebruikt, moet u ook geldige verbindingseigenschappen opgeven. Zie [Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

## Snel starten (SOAP-modus): Formuliergegevens importeren met de Java API {#quick-start-soap-mode-importing-form-data-using-the-java-api}

In het volgende Java-codevoorbeeld worden gegevens ge??mporteerd in een PDF-formulier. De gegevens bevinden zich in een XML-bestand met de naam *Loan_data.xml* en het PDF-formulier wordt opgeslagen als een PDF-bestand met de naam *ResultLoanForm.pdf*. (Zie [Formuliergegevens importeren](/help/forms/developing/importing-exporting-data.md#importing-form-data).)

```java
???/*
???    * This Java Quick Start uses the SOAP mode and contains the following JAR files
???    * in the class path:
???    * 1. adobe-formdataintegration-client.jar
???    * 2. adobe-livecycle-client.jar
???    * 3. adobe-usermanager-client.jar
???    * 4. adobe-utilities.jar
???    * 5. jboss-client.jar (use a different JAR file if the forms server is not deployed
???    * on JBoss)
???    * 6. activation.jar (required for SOAP mode)
???    * 7. axis.jar (required for SOAP mode)
???    * 8. commons-codec-1.3.jar (required for SOAP mode)
???    * 9.  commons-collections-3.1.jar  (required for SOAP mode)
???    * 10. commons-discovery.jar (required for SOAP mode)
???    * 11. commons-logging.jar (required for SOAP mode)
???    * 12. dom3-xml-apis-2.5.0.jar (required for SOAP mode)
???    * 13. jaxen-1.1-beta-9.jar (required for SOAP mode)
???    * 14. jaxrpc.jar (required for SOAP mode)
???    * 15. log4j.jar (required for SOAP mode)
???    * 16. mail.jar (required for SOAP mode)
???    * 17. saaj.jar (required for SOAP mode)
???    * 18. wsdl4j.jar (required for SOAP mode)
???    * 19. xalan.jar (required for SOAP mode)
???    * 20. xbean.jar (required for SOAP mode)
???    * 21. xercesImpl.jar (required for SOAP mode)
???    *
???    * These JAR files are located in the following path:
???    * <install directory>/sdk/client-libs/common
???    *
???    * The adobe-utilities.jar file is located in the following path:
???    * <install directory>/sdk/client-libs/jboss
???    *
???    * The jboss-client.jar file is located in the following path:
???    * <install directory>/jboss/bin/client
???    *
???    * SOAP required JAR files are located in the following path:
???    * <install directory>/sdk/client-libs/thirdparty
???    *
???    * If you want to invoke a remote forms server instance and there is a
???    * firewall between the client application and the server, then it is
???    * recommended that you use the SOAP mode. When using the SOAP mode,
???    * you have to include these additional JAR files
???    *
???    * For information about the SOAP
???    * mode, see "Setting connection properties" in Programming
???    * with AEM Forms
???    */
???import java.util.*;
???import java.io.File;
???import java.io.FileInputStream;
???import com.adobe.idp.Document;
???import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
???import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
???import com.adobe.livecycle.formdataintegration.client.*;
???
???public class ImportDataSOAP {
???
???    public static void main(String[] args) {
???
???        try{
???            //Set connection properties required to invoke AEM Forms using SOAP mode
???            Properties connectionProps = new Properties();
???            connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://'[server]:[port]'");
???            connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
???            connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
???            connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
???            connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
???
???             //Create a ServiceClientFactory object
???             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps);
???
???            //Create a FormDataIntegrationClient object
???            FormDataIntegrationClient dataClient = new FormDataIntegrationClient(myFactory);
???
???            //Import XDP XML data into an XFA PDF document
???            //Reference an XFA PDF form
???            FileInputStream inputStream = new FileInputStream("C:\\Adobe\Loan.pdf");
???            Document inputPDF = new Document(inputStream);
???
???            FileInputStream dataInput = new FileInputStream("C:\\Adobe\Loan_data.xml");
???            Document inputDataFile = new Document(dataInput);
???
???            //Import data into the form
???            Document resultPDF = dataClient.importData(inputPDF,inputDataFile);
???
???            //Save the PDF file
???            File resultFile = new File("C:\\Adobe\ResultLoanForm.pdf");
???            resultPDF.copyToFile(resultFile);
???
???        }catch (Exception e) {
???             e.printStackTrace();
???        }
???      }
???    }
???
```

## Snel starten (SOAP-modus): Formuliergegevens exporteren met de Java API {#quick-start-soap-mode-exporting-form-data-using-the-java-api}

In het volgende Java-codevoorbeeld worden gegevens uit een PDF-formulier ge??xporteerd. De formuliergegevens worden opgeslagen als een XML-bestand met de naam *Loan_data.xml*. (Zie [Formuliergegevens exporteren](/help/forms/developing/importing-exporting-data.md#exporting-form-data).)

```java
???/*
???    * This Java Quick Start uses the SOAP mode and contains the following JAR files
???    * in the class path:
???    * 1. adobe-formdataintegration-client.jar
???    * 2. adobe-livecycle-client.jar
???    * 3. adobe-usermanager-client.jar
???    * 4. adobe-utilities.jar
???    * 5. jboss-client.jar (use a different JAR file if the forms server is not deployed
???    * on JBoss)
???    * 6. activation.jar (required for SOAP mode)
???    * 7. axis.jar (required for SOAP mode)
???    * 8. commons-codec-1.3.jar (required for SOAP mode)
???    * 9.  commons-collections-3.1.jar  (required for SOAP mode)
???    * 10. commons-discovery.jar (required for SOAP mode)
???    * 11. commons-logging.jar (required for SOAP mode)
???    * 12. dom3-xml-apis-2.5.0.jar (required for SOAP mode)
???    * 13. jaxen-1.1-beta-9.jar (required for SOAP mode)
???    * 14. jaxrpc.jar (required for SOAP mode)
???    * 15. log4j.jar (required for SOAP mode)
???    * 16. mail.jar (required for SOAP mode)
???    * 17. saaj.jar (required for SOAP mode)
???    * 18. wsdl4j.jar (required for SOAP mode)
???    * 19. xalan.jar (required for SOAP mode)
???    * 20. xbean.jar (required for SOAP mode)
???    * 21. xercesImpl.jar (required for SOAP mode)
???    *
???    * These JAR files are located in the following path:
???    * <install directory>/sdk/client-libs/common
???    *
???    * The adobe-utilities.jar file is located in the following path:
???    * <install directory>/sdk/client-libs/jboss
???    *
???    * The jboss-client.jar file is located in the following path:
???    * <install directory>/jboss/bin/client
???    *
???    * SOAP required JAR files are located in the following path:
???    * <install directory>/sdk/client-libs/thirdparty
???    *
???    * If you want to invoke a remote forms server instance and there is a
???    * firewall between the client application and the server, then it is
???    * recommended that you use the SOAP mode. When using the SOAP mode,
???    * you have to include these additional JAR files
???    *
???    * For information about the SOAP
???    * mode, see "Setting connection properties" in Programming
???    * with AEM Forms
???    */
???import java.util.*;
???import java.io.File;
???import java.io.FileInputStream;
???import com.adobe.idp.Document;
???import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
???import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
???import com.adobe.livecycle.formdataintegration.client.*;
???
???public class ExportDataSOAP {
???
???    public static void main(String[] args) {
???
???    try{
???        //Set connection properties required to invoke AEM Forms using SOAP mode
???        Properties connectionProps = new Properties();
???        connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://'[server]:[port]'");
???        connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
???        connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
???        connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
???        connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
???
???         //Create a ServiceClientFactory object
???         ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps);
???
???         //Create a FormDataIntegrationClient object
???         FormDataIntegrationClient dataClient = new FormDataIntegrationClient(myFactory);
???
???         //Reference a PDF form from which to export data
???         FileInputStream fileInputStream2 = new FileInputStream("C:\\Adobe\LoanForm.pdf");
???         Document inputPDF = new Document(fileInputStream2);
???
???         //Export data from the form
???         Document resultPDF = dataClient.exportData(inputPDF);
???
???         //Save the exported form data as an XML file
???         File resultFile = new File("C:\\Adobe\Loan_data.xml");
???         resultPDF.copyToFile(resultFile);
???
???    }catch (Exception e) {
???             e.printStackTrace();
???        }
???    }
???}
```

