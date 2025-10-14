---
title: Documentbeheerservice (afgekeurd)Java API Snel starten (SOAP)
description: Documentbeheerservice (afgekeurd)Java API Snel starten (SOAP)
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
role: Developer
exl-id: 38a90957-bdde-4f38-9edd-c59522e5f525
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,APIs & Integrations,AEM Forms on JEE
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 0%

---

# Documentbeheerservice (verouderd) Java API Snel starten (SOAP) {#document-management-service-deprecated-java-api-quick-start-soap}

De volgende snelstarthandleidingen zijn beschikbaar voor de service Documentbeheer (afgekeurd).

>[!NOTE]
>
>Vanaf 5 augustus 2011 migreert Adobe Content Services ES-klanten naar de Adobe Digital Enterprise Platform Experience Services. Het product roadmap voor klanten die de Diensten van de Inhoud gebruiken is naar de nieuwe Diensten van de Ervaring van ADEP - Kern over te gaan, die een inheemse Bewaarplaats van de Inhoud omvat die op de moderne, modulaire architectuur van CRX wordt voortgebouwd, die tijdens de aanschaf van de Software van de Adobe van Dag wordt verworven.

[Snel starten (SOAP modus): Sites voor inhoudsservices maken met de Java API](document-management-service-deprecated-java.md#quick-start-soap-mode-create-content-services-spaces-using-the-java-api-deprecated)

[Snel starten (SOAP modus): Inhoud van inhoudsservices verwijderen met de Java API](document-management-service-deprecated-java.md#quick-start-soap-mode-delete-content-services-content-using-the-java-api-deprecated)

[Snel starten (SOAP modus): Inhoud toevoegen aan Content Services met de Java API](document-management-service-deprecated-java.md#quick-start-soap-mode-add-content-to-content-services-using-the-java-api-deprecated)

[Snel starten (SOAP modus): inhoud ophalen van Content Services met de Java API](document-management-service-deprecated-java.md#quick-start-soap-mode-retrieve-content-from-content-services-using-the-java-api-deprecated)

[Snel starten (SOAP modus): Inhoud van inhoudsservices verplaatsen met de Java API](document-management-service-deprecated-java.md#quick-start-soap-mode-move-content-services-content-using-the-java-api-deprecated)

[Snel starten (SOAP modus): Inhoud weergeven met de Java API](document-management-service-deprecated-java.md#quick-start-soap-mode-list-content-services-content-using-the-java-api-deprecated)

[Snel starten (SOAP modus): Inhoud zoeken met de Java API-inhoud](document-management-service-deprecated-java.md#quick-start-soap-mode-search-content-services-content-using-the-java-api-deprecated)

[Snel starten (SOAP modus): Machtigingen voor inhoudsservices instellen met de Java API](document-management-service-deprecated-java.md#quick-start-soap-mode-setting-content-services-permissions-using-the-java-api-deprecated)

AEM Forms-bewerkingen kunnen worden uitgevoerd met de API met sterke typen voor AEM Forms en de verbindingsmodus moet zijn ingesteld op SOAP.

>[!NOTE]
>
>De snelle aanvang in Programmering met AEM vormen is gebaseerd op de Server die van Forms op JBoss en het werkende systeem van Vensters wordt opgesteld. Als u echter een ander besturingssysteem gebruikt, zoals UNIX, vervangt u vensterspecifieke paden door paden die worden ondersteund door het desbetreffende besturingssysteem. Als u een andere J2EE-toepassingsserver gebruikt, moet u ook geldige verbindingseigenschappen opgeven. Zie [&#x200B; Plaatsende verbindingseigenschappen &#x200B;](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

## Snel starten (SOAP modus): Sites voor inhoudsservices maken met de Java API (afgekeurd) {#quick-start-soap-mode-create-content-services-spaces-using-the-java-api-deprecated}

Het volgende codevoorbeeld van Java leidt tot een nieuwe ruimte genoemd *Folder van de Test* in het Huis van het Bedrijf. De identificatiewaarde van de nieuwe ruimte wordt geschreven aan de console.

```java
 /*
     * This Java Quick Start uses the SOAP mode and contains the following JAR files
     * in the class path:
     * 1. adobe-contentservices-client.jar
     * 2. adobe-livecycle-client.jar
     * 3. adobe-usermanager-client.jar
     * 4. adobe-utilities.jar
     * 5. jboss-client.jar (use a different JAR file if the Forms Server is not deployed
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
     * These JAR files are in the following path:
     * <install directory>/sdk/client-libs/common
     *
     * The adobe-utilities.jar file is in the following path:
     * <install directory>/sdk/client-libs/jboss
     *
     * The jboss-client.jar file is in the following path:
     * <install directory>/jboss/bin/client
     *
     * SOAP required JAR files are in the following path:
     * <install directory>/sdk/client-libs/thirdparty
     *
     * If you want to invoke a remote Forms Server instance and there is a
     * firewall between the client application and the server, then it is
     * recommended that you use the SOAP mode. When using the SOAP mode,
     * you have to include these additional JAR files
     *
     * For information about the SOAP
     * mode, see "Setting connection properties" in Programming
     * with AEM Forms
     */
 import java.util.*;
 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
 import com.adobe.livecycle.contentservices.client.impl.DocumentManagementServiceClientImpl;
 
 public class CreateNewSpaceSoap {
 
     public static void main(String[] args) {
 
         try{
 
             //Set connection properties required to invoke AEM Forms using SOAP mode
             Properties connectionProps = new Properties();
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://'[server]:[port]'");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
 
             //Create a ServiceClientFactory object
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps);
 
             //Create a DocumentManagementServiceClientImpl object
             DocumentManagementServiceClientImpl    docManager = new DocumentManagementServiceClientImpl(myFactory);
 
             //Specify the name of the store and node
             String storeName ="SpacesStore";
             String nodeName = "/Company Home/Test Directory" ;
 
             //Create a space
             String spaceId = docManager.createSpace(storeName,nodeName);
             System.out.println("The identifier value of the new space is " +spaceId);
         }
 
         catch(Exception e)
         {
             e.printStackTrace();
         }
     }
 }
 
```

## Snel starten (SOAP modus): Inhoud van inhoudsservices verwijderen met de Java API (afgekeurd) {#quick-start-soap-mode-delete-content-services-content-using-the-java-api-deprecated}

Het volgende de codevoorbeeld van Java schrapt een ruimte genoemd /Company Huis/de Folder van de Test.

```java
 /*
     * This Java Quick Start uses the SOAP mode and contains the following JAR files
     * in the class path:
     * 1. adobe-contentservices-client.jar
     * 2. adobe-livecycle-client.jar
     * 3. adobe-usermanager-client.jar
     * 4. adobe-utilities.jar
     * 5. jboss-client.jar (use a different JAR file if the Forms Server is not deployed
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
     * These JAR files are in the following path:
     * <install directory>/sdk/client-libs/common
     *
     * The adobe-utilities.jar file is in the following path:
     * <install directory>/sdk/client-libs/jboss
     *
     * The jboss-client.jar file is in the following path:
     * <install directory>/jboss/bin/client
     *
     * SOAP required JAR files are in the following path:
     * <install directory>/sdk/client-libs/thirdparty
     *
     * If you want to invoke a remote Forms Server instance and there is a
     * firewall between the client application and the server, then it is
     * recommended that you use the SOAP mode. When using the SOAP mode,
     * you have to include these additional JAR files
     *
     * For information about the SOAP
     * mode, see "Setting connection properties" in Programming
     * with AEM Forms
     */
 import java.util.*;
 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
 import com.adobe.livecycle.contentservices.client.impl.DocumentManagementServiceClientImpl;
 
 public class DeleteContentSoap {
 
     public static void main(String[] args) {
 
         try{
 
             //Set connection properties required to invoke AEM Forms using SOAP mode
             Properties connectionProps = new Properties();
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://'[server]:[port]'");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
 
             //Create a ServiceClientFactory object
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps);
 
             //Create a DocumentManagementServiceClientImpl object
             DocumentManagementServiceClientImpl    docManager = new DocumentManagementServiceClientImpl(myFactory);
 
             //Specify the name of the store and node
             String storeName ="SpacesStore";
             String nodeName = "/Company Home/Test Directory" ;
 
             //Delete the content from /Company Home/Test Directory
             Boolean ans = docManager.deleteContent(storeName, nodeName);
 
             if (ans == true)
                 System.out.println("The content was successfully deleted");
             else
                 System.out.println("The content was not deleted");
             }
 
         catch(Exception e)
         {
             e.printStackTrace();
         }
     }
 }
 
```

## Snel starten (SOAP modus): Inhoud toevoegen aan Content Services met de Java API (afgekeurd) {#quick-start-soap-mode-add-content-to-content-services-using-the-java-api-deprecated}

Het volgende de codevoorbeeld van Java voegt een PDF dossier genoemd *MortgaugeForm.pdf* aan een omslag genoemd /Company Huis/de Folder van de Test toe. De auteur- en beschrijvingskenmerken worden ingesteld. De identificatiewaarde van de nieuwe inhoud wordt geschreven aan de console.

```java
 /*
     * This Java Quick Start uses the SOAP mode and contains the following JAR files
     * in the class path:
     * 1. adobe-contentservices-client.jar
     * 2. adobe-livecycle-client.jar
     * 3. adobe-usermanager-client.jar
     * 4. adobe-utilities.jar
     * 5. jboss-client.jar (use a different JAR file if the Forms Server is not deployed
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
     * These JAR files are in the following path:
     * <install directory>/sdk/client-libs/common
     *
     * The adobe-utilities.jar file is in the following path:
     * <install directory>/sdk/client-libs/jboss
     *
     * The jboss-client.jar file is in the following path:
     * <install directory>/jboss/bin/client
     *
     * SOAP required JAR files are in the following path:
     * <install directory>/sdk/client-libs/thirdparty
     *
     * If you want to invoke a remote Forms Server instance and there is a
     * firewall between the client application and the server, then it is
     * recommended that you use the SOAP mode. When using the SOAP mode,
     * you have to include these additional JAR files
     *
     * For information about the SOAP
     * mode, see "Setting connection properties" in Programming
     * with AEM Forms
     */
 import java.io.File;
 import java.util.*;
 import com.adobe.idp.Document;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
 import com.adobe.livecycle.contentservices.client.CRCResult;
 import com.adobe.livecycle.contentservices.client.impl.DocumentManagementServiceClientImpl;
 import com.adobe.livecycle.contentservices.client.impl.UpdateVersionType;
 
 public class AddContentSoap {
 
     public static void main(String[] args) {
 
         try{
 
             //Set connection properties required to invoke AEM Forms using SOAP mode
             Properties connectionProps = new Properties();
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://'[server]:[port]'");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
 
             //Create a ServiceClientFactory object
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps);
 
             //Create a DocumentManagementServiceClientImpl object
             DocumentManagementServiceClientImpl    docManager = new DocumentManagementServiceClientImpl(myFactory);
 
             //Specify the store and node name
             String storeName ="SpacesStore";
             String nodeName = "/Company Home/Test Directory" ;
 
             //Retrieve the document to store in /Company Home/Test Directory
             Document content =  new Document(new File("C:\\Adobe\MortgageForm.pdf"), false);
 
             //Create a MAP instance to store attributes
             Map<String,Object> inputs = new HashMap<String,Object>();
 
             //Specify attributes that belong to the new content
             String creator = "{https://www.alfresco.org/model/content/1.0}creator";
             String description = "{https://www.alfresco.org/model/content/1.0}description";
 
             inputs.put(creator,"Tony Blue");
             inputs.put(description,"A mortgage application form");
 
             //Store MortgageForm.pdf in /Company Home/Test Directory
             CRCResult result = docManager.storeContent(storeName,
                      nodeName,
                     "MortgageForm.pdf",
                     "{https://www.alfresco.org/model/content/1.0}content",
                     content,
                     "UTF-8",
                     UpdateVersionType.INCREMENT_MAJOR_VERSION,
                     null,
                     inputs);
 
             //Get the identifier value of the new content
             String id = result.getNodeUuid();
             System.out.println("The identifier value of the new content is "+id);
     }
 
         catch(Exception e)
         {
             e.printStackTrace();
         }
     }
 }
 
```

## Snel starten (SOAP modus): inhoud ophalen van Content Services met de Java API (afgekeurd) {#quick-start-soap-mode-retrieve-content-from-content-services-using-the-java-api-deprecated}

Het volgende de codevoorbeeld van Java wint een PDF dossier genoemd *MortgaugeForm.pdf* van /Company Huis terug. Het dossier van PDF wordt bewaard aan het lokale dossiersysteem en wordt genoemd *UpdatedMortgaugeForm.pdf*.

```java
 /*
     * This Java Quick Start uses the SOAP mode and contains the following JAR files
     * in the class path:
     * 1. adobe-contentservices-client.jar
     * 2. adobe-livecycle-client.jar
     * 3. adobe-usermanager-client.jar
     * 4. adobe-utilities.jar
     * 5. jboss-client.jar (use a different JAR file if the Forms Server is not deployed
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
     * These JAR files are in the following path:
     * <install directory>/sdk/client-libs/common
     *
     * The adobe-utilities.jar file is in the following path:
     * <install directory>/sdk/client-libs/jboss
     *
     * The jboss-client.jar file is in the following path:
     * <install directory>/jboss/bin/client
     *
     * SOAP required JAR files are in the following path:
     * <install directory>/sdk/client-libs/thirdparty
     *
     * If you want to invoke a remote Forms Server instance and there is a
     * firewall between the client application and the server, then it is
     * recommended that you use the SOAP mode. When using the SOAP mode,
     * you have to include these additional JAR files
     *
     * For information about the SOAP
     * mode, see "Setting connection properties" in Programming
     * with AEM Forms
     */
 import java.io.File;
 import java.util.*;
 
 import com.adobe.idp.Document;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
 import com.adobe.livecycle.contentservices.client.CRCResult;
 import com.adobe.livecycle.contentservices.client.impl.DocumentManagementServiceClientImpl;
 
 public class RetrieveContentSoap {
 
     public static void main(String[] args) {
 
         try{
             //Set connection properties required to invoke AEM Forms using SOAP mode
             Properties connectionProps = new Properties();
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://'[server]:[port]'");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
 
             //Create a ServiceClientFactory object
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps);
 
             //Create a DocumentManagementServiceClientImpl object
             DocumentManagementServiceClientImpl    docManager = new DocumentManagementServiceClientImpl(myFactory);
 
             //Specify the name of the store and the content to retrieve
                String storeName = "SpacesStore";
                String nodeName  = "/Company Home/MortgageForm.pdf";
 
                //Retrieve /Company Home/MortgageForm.pdf
                CRCResult content = docManager.retrieveContent(
                      storeName,
                      nodeName,
                      "");
 
                //Write the PDF file to the local file system
                File myFile = new File("C:\\Adobe\UpdatedMortgageForm.pdf");
                Document doc =content.getDocument();
                doc.copyToFile(myFile);
          }
 
         catch(Exception e)
         {
             e.printStackTrace();
         }
     }
 }
 
 
```

## Snel starten (SOAP modus): Inhoud van inhoudsservices verplaatsen met de Java API (afgekeurd) {#quick-start-soap-mode-move-content-services-content-using-the-java-api-deprecated}

Het volgende codevoorbeeld van Java beweegt een PDF dossier genoemd *MortgaugeForm.pdf* van /Company Huis/de Folder van de Test aan /Company Huis. De identificatiewaarde van de verplaatste inhoud wordt geschreven aan de console.

```java
 /*
     * This Java Quick Start uses the SOAP mode and contains the following JAR files
     * in the class path:
     * 1. adobe-contentservices-client.jar
     * 2. adobe-livecycle-client.jar
     * 3. adobe-usermanager-client.jar
     * 4. adobe-utilities.jar
     * 5. jboss-client.jar (use a different JAR file if the Forms Server is not deployed
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
     * These JAR files are in the following path:
     * <install directory>/sdk/client-libs/common
     *
     * The adobe-utilities.jar file is in the following path:
     * <install directory>/sdk/client-libs/jboss
     *
     * The jboss-client.jar file is in the following path:
     * <install directory>/jboss/bin/client
     *
     * SOAP required JAR files are in the following path:
     * <install directory>/sdk/client-libs/thirdparty
     *
     * If you want to invoke a remote Forms Server instance and there is a
     * firewall between the client application and the server, then it is
     * recommended that you use the SOAP mode. When using the SOAP mode,
     * you have to include these additional JAR files
     *
     * For information about the SOAP
     * mode, see "Setting connection properties" in Programming
     * with AEM Forms
     */
 import java.util.*;
 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
 import com.adobe.livecycle.contentservices.client.impl.DocumentManagementServiceClientImpl;
 
 public class MoveContentSoap {
 
     public static void main(String[] args) {
 
         try{
 
             //Set connection properties required to invoke AEM Forms using SOAP mode
             Properties connectionProps = new Properties();
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://'[server]:[port]'");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
 
             //Create a ServiceClientFactory object
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps);
 
 
             //Create a DocumentManagementServiceClientImpl object
             DocumentManagementServiceClientImpl    docManager = new DocumentManagementServiceClientImpl(myFactory);
 
             //Specify the name of the store and the content to move
                String storeName = "SpacesStore";
                String nodeName = "/Company Home/Test Directory/MortgageForm.pdf";
                String newSpace = "/Company Home";
 
                //Move the content from /Company Home/Test Directory
                //to /Company Home and display the identifier value of the
                //moved content
                String contentID = docManager.moveContent(storeName, nodeName, newSpace);
                System.out.println("The identifier value of the moved content is "+contentID);
         }
 
         catch(Exception e)
         {
             e.printStackTrace();
         }
     }
 }
 
 
```

## Snel starten (SOAP modus): Inhoud weergeven met de Java API (afgekeurd) {#quick-start-soap-mode-list-content-services-content-using-the-java-api-deprecated}

Het volgende de codevoorbeeld van Java maakt een lijst van inhoud die in /Company Huis is. Elk knooppunttype en knooppuntnaam wordt getoond.

```java
 /*
     * This Java Quick Start uses the SOAP mode and contains the following JAR files
     * in the class path:
     * 1. adobe-contentservices-client.jar
     * 2. adobe-livecycle-client.jar
     * 3. adobe-usermanager-client.jar
     * 4. adobe-utilities.jar
     * 5. jboss-client.jar (use a different JAR file if the Forms Server is not deployed
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
     * These JAR files are in the following path:
     * <install directory>/sdk/client-libs/common
     *
     * The adobe-utilities.jar file is in the following path:
     * <install directory>/sdk/client-libs/jboss
     *
     * The jboss-client.jar file is in the following path:
     * <install directory>/jboss/bin/client
     *
     * SOAP required JAR files are in the following path:
     * <install directory>/sdk/client-libs/thirdparty
     *
     * If you want to invoke a remote Forms Server instance and there is a
     * firewall between the client application and the server, then it is
     * recommended that you use the SOAP mode. When using the SOAP mode,
     * you have to include these additional JAR files
     *
     * For information about the SOAP
     * mode, see "Setting connection properties" in Programming
     * with AEM Forms
     */
 import java.util.*;
 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
 import com.adobe.livecycle.contentservices.client.CRCResult;
 import com.adobe.livecycle.contentservices.client.impl.DocumentManagementServiceClientImpl;
 
 public class ListingContentSoap {
 
     public static void main(String[] args) {
 
         try{
 
             //Set connection properties required to invoke AEM Forms using SOAP mode
             Properties connectionProps = new Properties();
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://'[server]:[port]'");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
 
             //Create a ServiceClientFactory object
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps);
 
             //Create a DocumentManagementServiceClientImpl object
             DocumentManagementServiceClientImpl    docManager = new DocumentManagementServiceClientImpl(myFactory);
 
             //Specify the name of the store and the space
                String storeName = "SpacesStore";
                String nodeName  = "/Company Home";
 
               //List the contents of /Company Home
               List<CRCResult> allImages = docManager.getSpaceContents(
                      storeName,
                      nodeName,
                      false);
 
              //Create an Iterator object and iterate through
              //the List object
              Iterator iter = allImages.iterator();
              int i = 0 ;
              while (iter.hasNext()) {
 
                  //Get the node content type and name
                  CRCResult sinContent = (CRCResult)iter.next();
                  String nodeType =  sinContent.getNodeType();
                  String name = sinContent.getNodeName();
                  System.out.println("The node type is "+nodeType  +". The node name is "+name);
              }
         }
 
         catch(Exception e)
         {
             e.printStackTrace();
         }
     }
 }
 
 
```

## Snel starten (SOAP modus): Inhoud zoeken met de Java API (Verouderd) {#quick-start-soap-mode-search-content-services-content-using-the-java-api-deprecated}

De volgende code van Java zoekt /Company Huis naar een document dat de tekst MortgaugeForm bevat. De submappen worden ook doorzocht.

```java
 /*
     * This Java Quick Start uses the SOAP mode and contains the following JAR files
     * in the class path:
     * 1. adobe-contentservices-client.jar
     * 2. adobe-livecycle-client.jar
     * 3. adobe-usermanager-client.jar
     * 4. adobe-utilities.jar
     * 5. jboss-client.jar (use a different JAR file if the Forms Server is not deployed
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
     * These JAR files are in the following path:
     * <install directory>/sdk/client-libs/common
     *
     * The adobe-utilities.jar file is in the following path:
     * <install directory>/sdk/client-libs/jboss
     *
     * The jboss-client.jar file is in the following path:
     * <install directory>/jboss/bin/client
     *
     * SOAP required JAR files are in the following path:
     * <install directory>/sdk/client-libs/thirdparty
     *
     * If you want to invoke a remote Forms Server instance and there is a
     * firewall between the client application and the server, then it is
     * recommended that you use the SOAP mode. When using the SOAP mode,
     * you have to include these additional JAR files
     *
     * For information about the SOAP
     * mode, see "Setting connection properties" in Programming
     * with AEM Forms
     */
 import java.util.*;
 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
 import com.adobe.livecycle.contentservices.client.ResultSet;
 import com.adobe.livecycle.contentservices.client.impl.DocumentManagementServiceClientImpl;
 import com.adobe.livecycle.contentservices.client.impl.QueryImpl;
 import com.adobe.livecycle.contentservices.client.impl.StatementImpl;
 
 public class SearchSpaceSoap {
 
     public static void main(String[] args) {
 
         try{
             //Set connection properties required to invoke AEM Forms using SOAP mode
             Properties connectionProps = new Properties();
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://'[server]:[port]'");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
 
             //Create a ServiceClientFactory object
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps);
 
             //Create a DocumentManagementServiceClientImpl object
             DocumentManagementServiceClientImpl    docManager = new DocumentManagementServiceClientImpl(myFactory);
 
             //Specify the name of the store and node
             String path ="/Company Home";
              String storeName = "SpacesStore";
 
             //Create a Query expression
             QueryImpl qImpl = new QueryImpl();
             String myName = "{https://www.alfresco.org/model/content/1.0}name";
             StatementImpl statement = new StatementImpl(myName, StatementImpl.OPERATOR_CONTAINS, "MortgageForm" );
             qImpl.addStatement(statement);
 
             //Perform the search for a document that contains the text MortgageForm
             ResultSet rs = docManager.searchRepository(storeName, path, true, qImpl, 200);
             long resultSize = rs.getResultSize();
 
             //Determine if the document is in Content space
             if (resultSize > 0)
             {
                 System.out.println("MortgageForm is in the Repository");
             }
         }
     catch(Exception e)
         {
             e.printStackTrace();
         }
     }
 }
 
 
```

## Snel starten (SOAP modus): Machtigingen voor inhoudsservices instellen met de Java API (afgekeurd) {#quick-start-soap-mode-setting-content-services-permissions-using-the-java-api-deprecated}

In het volgende Java-codevoorbeeld wordt een machtiging ingesteld voor een gebruiker met de naam tony blue. Het opgegeven domein is het standaarddomein. De machtiging Consumer wordt opgegeven en het knooppunt is `/Company Home/Test Directory` .

```java
 /*
     * This Java Quick Start uses the SOAP mode and contains the following JAR files
     * in the class path:
     * 1. adobe-contentservices-client.jar
     * 2. adobe-livecycle-client.jar
     * 3. adobe-usermanager-client.jar
     * 4. adobe-utilities.jar
     * 5. jboss-client.jar (use a different JAR file if the Forms Server is not deployed
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
     * These JAR files are in the following path:
     * <install directory>/sdk/client-libs/common
     *
     * The adobe-utilities.jar file is in the following path:
     * <install directory>/sdk/client-libs/jboss
     *
     * The jboss-client.jar file is in the following path:
     * <install directory>/jboss/bin/client
     *
     * SOAP required JAR files are in the following path:
     * <install directory>/sdk/client-libs/thirdparty
     *
     * If you want to invoke a remote Forms Server instance and there is a
     * firewall between the client application and the server, then it is
     * recommended that you use the SOAP mode. When using the SOAP mode,
     * you have to include these additional JAR files
     *
     * For information about the SOAP
     * mode, see "Setting connection properties" in Programming
     * with AEM Forms
     */
 
 import java.util.*;
 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
 import com.adobe.livecycle.contentservices.client.impl.DocumentManagementServiceClientImpl;
 import com.adobe.livecycle.contentservices.client.impl.ContentAccessPermission;
 
 public class SetPermissionsSoap {
 
     public static void main(String[] args) {
 
         try{
 
             //Set connection properties required to invoke AEM Forms using SOAP mode
             Properties connectionProps = new Properties();
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://'[server]:[port]'");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
 
             //Create a ServiceClientFactory object
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps);
 
             //Create a DocumentManagementServiceClientImpl object
             DocumentManagementServiceClientImpl    docManager = new DocumentManagementServiceClientImpl(myFactory);
 
             //Specify the store and node name
             String storeName ="SpacesStore";
             String nodeName = "/Company Home/Test Directory/";
 
              //Create a permission
             ContentAccessPermission permission = new ContentAccessPermission();
             permission.setAuthority("tblue/DefaultDom");
             permission.setIsAllowed(false);
             permission.setPermission("Consumer");
 
             //Create a collection to hold the values
             List<ContentAccessPermission> permissionList = new ArrayList<ContentAccessPermission>();
             permissionList.add(0,permission);
 
             //Set the permission
             docManager.writePermissions(storeName,
                      nodeName,
                      permissionList,
                     false);
     }
 
         catch(Exception e)
         {
             e.printStackTrace();
         }
     }
 }
 
```

## Snel starten (SOAP modus): Koppelingen maken met de Java API (afgekeurd) {#quick-start-soap-mode-creating-associations-using-the-java-api-deprecated}

De volgende Java-code maakt een koppeling naar een XML-gegevensbestand en een PDF-formulier. Dit type koppeling heeft de naam LinkedBy.In het PDF-document moet de koppelbare eigenschap zijn toegepast.

```java
 /*
     * This Java Quick Start uses the SOAP mode and contains the following JAR files
     * in the class path:
     * 1. adobe-contentservices-client.jar
     * 2. adobe-livecycle-client.jar
     * 3. adobe-usermanager-client.jar
     * 4. adobe-utilities.jar
     * 5. jboss-client.jar (use a different JAR file if the Forms Server is not deployed
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
     * These JAR files are in the following path:
     * <install directory>/sdk/client-libs/common
     *
     * The adobe-utilities.jar file is in the following path:
     * <install directory>/sdk/client-libs/jboss
     *
     * The jboss-client.jar file is in the following path:
     * <install directory>/jboss/bin/client
     *
     * SOAP required JAR files are in the following path:
     * <install directory>/sdk/client-libs/thirdparty
     *
     * If you want to invoke a remote Forms Server instance and there is a
     * firewall between the client application and the server, then it is
     * recommended that you use the SOAP mode. When using the SOAP mode,
     * you have to include these additional JAR files
     *
     * For information about the SOAP
     * mode, see "Setting connection properties" in Programming
     * with AEM Forms
     */
 import java.util.*;
 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
 import com.adobe.livecycle.contentservices.client.impl.DocumentManagementServiceClientImpl;
 
 public class CreateAssociationsSoap {
 
     public static void main(String[] args) {
 
         try{
 
             //Set connection properties required to invoke AEM Forms using SOAP mode
             Properties connectionProps = new Properties();
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://'[server]:[port]'");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
 
             //Create a ServiceClientFactory object
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps);
 
             //Create a DocumentManagementServiceClientImpl object
             DocumentManagementServiceClientImpl    docManager = new DocumentManagementServiceClientImpl(myFactory);
 
             //Specify the input values
             String storeName ="SpacesStore";
             String associationType = "{https://www.adobe.com/lc/datacapture/1.0}linkedBy";
             String aspect = "{https://www.adobe.com/lc/datacapture/1.0}linkable";
             String parentPath= "/Company Home/MortgageForm.pdf";
             String childPath= "/Company Home/Loan.xml";
 
             //Set the linkable aspect to MortgageForm.pdf
             List<String> aspectList = new ArrayList();
             aspectList.add(aspect);
 
             //Create an attribute map
             Map<String,Object> inputs = new HashMap<String,Object>();
 
             //Specify attributes that belong to the new content
             String creator = "{https://www.alfresco.org/model/content/1.0}creator";
             String description = "{https://www.alfresco.org/model/content/1.0}description";
 
             inputs.put(creator,"Tony Blue");
             inputs.put(description,"Link the PDF document to loan data");
 
             //Set the aspects
             docManager.setContentAttributes(storeName,parentPath,aspectList,inputs);
 
             //Create an association between MortgageForm.pdf and Loan.xml
             docManager.createAssociation(storeName,
                     associationType,
                     parentPath,
                     childPath);
         }
 
         catch(Exception e)
         {
             e.printStackTrace();
         }
     }
 
```
