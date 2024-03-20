---
title: Een document namens een andere gebruiker Protect
description: Leer hoe u Java&trade voor beveiliging van AEM Forms-documenten kunt gebruiken; SDK biedt API's voor een gebruikersaccount om een document te beveiligen namens een andere gebruiker.
geptopics: SG_AEMFORMS/categories/working_with_document_security
feature: Document Security
exl-id: e5c80569-d3c0-4358-9b91-b98a64d1c004
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# Een document namens een andere gebruiker Protect {#protect-a-document-on-behalf-of-another-user}

AEM Forms Document Security Java™ SDK biedt API&#39;s waarmee een gebruikersaccount een document namens een andere gebruiker kan beveiligen zonder dat de machtigingen voor het bewerken van het document zijn verkregen. U kunt de API&#39;s in een workflowproces of programmatisch als documentservice gebruiken. De nieuwe API&#39;s zijn:

* **protectDocumentUse** de API van ProtectDocument zodat kunt u een beleid op een document namens toepassen

  een andere gebruikersaccount. Rechten van de gebruikersaccount die worden gebruikt om het beleid toe te passen, blijven beperkt tot het beschermen van het document. Het recht om het document te openen en weer te geven, wordt niet bereikt. RMSecureDocumentResult protectDocument(Document inDoc, String documentName, String policySetName, String policyName, RMLocale locale, boolean bExactMatchForNames)

* **createLicenseUse** De CreateLicense API zodat u een licentie voor een beleid kunt maken namens een andere gebruikersaccount. PublishLicenseDTO createLicense(String policyId, String documentName, boolean logSecureDocEvent)
* **protectDocumentWithCoverPageUse** de ProtectDocumentWithCoverPage API zodat kunt u een beleid toepassen en een omslagpagina toevoegen aan een document namens een andere gebruiker. Rechten van de gebruikersaccount die worden gebruikt om het beleid toe te passen, blijven beperkt tot het beschermen van het document. Het recht om het document te openen en weer te geven, wordt niet bereikt. RMSecureDocumentResult protectDocumentWithCoverPage(Document inDoc, String documentName, String policySetName, String policyName, Document coverDoc, boolean bExactMatchForNames)

## De API&#39;s gebruiken om een document te beveiligen namens een andere gebruiker {#using-the-apis-to-protect-a-document-on-behalf-of-another-user}

Ga als volgt te werk, zodat u een document namens een andere gebruiker kunt beveiligen zonder de machtigingen voor het bewerken van het document te verkrijgen:

1. Maak een beleidsset. Beleidsset1.
1. Maak een beleid in de nieuwe beleidsset. Bijvoorbeeld, Policy1 in PolicySet1.
1. Creeer een gebruiker met de Eindgebruiker van het Rights Management van de rol. Bijvoorbeeld Gebruiker1. Verstrek de toestemmingen om documenten te bekijken die gebruikend Beleid1 aan de pas gecreëerde gebruiker worden beschermd.
1. Maak een rol. Bijvoorbeeld Rol1. Verstrek de Dienst aanhaalt toestemming aan de pas gecreëerde rol. Maak een gebruiker met de nieuwe rol. Bijvoorbeeld User2. U kunt User2 of een beheerder gebruiken om de verbinding van SDK tot stand te brengen en de dienst te roepen protectDocument.

   Nu kunt u de volgende voorbeeldcode uitvoeren om een document te beveiligen zonder dat u machtigingen hebt om het document te bewerken voor de gebruiker die het document beveiligt:

   ```java
   import java.io.File;
   import java.io.FileInputStream;
   import java.io.FileNotFoundException;
   import java.io.FileOutputStream;
   import java.io.IOException;
   import java.io.InputStream;
   import java.util.Properties;
   
   import com.adobe.edc.common.dto.PublishLicenseDTO;
   import com.adobe.edc.sdk.SDKException;
   import com.adobe.idp.Document;
   import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
   import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
   import com.adobe.livecycle.rightsmanagement.RMSecureDocumentResult;
   import com.adobe.livecycle.rightsmanagement.client.DocumentManager;
   import com.adobe.livecycle.rightsmanagement.client.RightsManagementClient;
   import com.adobe.livecycle.rightsmanagement.client.RightsManagementClient2;
   
   public class PublishAsProtectAPI {
   
   private static final String unprotectedFileName = "C:\\unprotected.pdf";
   private static final String protectedFileName = "C:\\protect.pdf";
   private static final String coverFileName = "C:\\CoverPage.pdf";
   private static final String POLICY_ID = "2EF66008-5E2D-1034-9B06-00000A292C18"; 
   
   public static void main(String[] args) {
   
   try {
   
   Properties connectionProps = new Properties();
   connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT,"http://localhost:8080");
   connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
   connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
   connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME,"administrator");
   connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD,"password");
   
   // Create a ServiceClientFactory instance
   ServiceClientFactory factory = ServiceClientFactory.createInstance(connectionProps);
   testProtectDocument(factory);
   testProtectDocumentWithCoverPage(factory);
   testProtectDocumentJavaPPL(factory);
   
   } 
   catch (Exception ex) {
   ex.printStackTrace(); }
   }
   
   private static void testProtectDocument(ServiceClientFactory factory) throws FileNotFoundException, SDKException {
   // Create a RightsManagementClient object
   RightsManagementClient rmClient = new RightsManagementClient(factory);
   // Create a Document Manager object
   DocumentManager documentManager = rmClient.getDocumentManager();
   //Reference a policy-protected PDF document from which to remove a policy
   FileInputStream is = new FileInputStream(unprotectedFileName);
   Document inPDF = new Document(is);
   long startTime = System.currentTimeMillis();
   //Remove a policy from the policy-protected PDF document
   RMSecureDocumentResult securePDF = documentManager.protectDocument(inPDF, "test", "newPolicySet", "latest", "DefaultDom", "administrator", null, true);
   System.out.println("Total Time taken for protectDocument = " + (System.currentTimeMillis() - startTime));
   //Save the unsecured PDF document
   File myFile = new File(protectedFileName);
   securePDF.getProtectedDoc().copyToFile(myFile);
   }
   
   private static void testProtectDocumentWithCoverPage(ServiceClientFactory factory) throws FileNotFoundException, SDKException {
   // Create a RightsManagementClient object
   RightsManagementClient rmClient = new RightsManagementClient(factory);
   // Create a Document Manager object
   DocumentManager documentManager = rmClient.getDocumentManager();
   //Reference a policy-protected PDF document from which to remove a policy
   FileInputStream is = new FileInputStream(unprotectedFileName);
   Document inPDF = new Document(is);
   FileInputStream coverIS = new FileInputStream(coverFileName);
   Document inCoverPDF = new Document(coverIS);
   long startTime = System.currentTimeMillis();
   //Remove a policy from the policy-protected PDF document
   RMSecureDocumentResult securePDF = documentManager.protectDocumentWithCoverPage(inPDF, "test", "newPolicySet", "latestPolicy", inCoverPDF, true);
   System.out.println("Total Time taken for Page0ProtectDocument = " + (System.currentTimeMillis() - startTime));
   //Save the unsecured PDF document
   File myFile = new File(protectedFileName);
   securePDF.getProtectedDoc().copyToFile(myFile);
   }
   
   private static PublishLicenseDTO testProtectDocumentJavaPPL (ServiceClientFactory factory) throws SDKException, FileNotFoundException, IOException {
   // Create a RightsManagementClient object
   RightsManagementClient2 rmClient2 = new RightsManagementClient2(factory);
   // Create a Document Manager object
   DocumentManager documentManager = rmClient2.getDocumentManager();
   long startTime = System.currentTimeMillis();
   PublishLicenseDTO license = documentManager.createLicense(POLICY_ID, "Out.pdf", true);
   System.out.println("Create License totalTime = " + (System.currentTimeMillis() - startTime));
   startTime = System.currentTimeMillis();
   // Reference a PDF document to which a policy is applied
   InputStream inputFileStream = new FileInputStream(unprotectedFileName);
   // Apply a policy to the PDF document
   InputStream protectPDF = rmClient2.getRightsManagementEncryptionService().protectDocument(inputFileStream, license);
   // Save the policy-protected PDF document
   File myFile = new File(protectedFileName);
   // write the inputStream to a FileOutputStream
   FileOutputStream outputStream = new FileOutputStream(myFile);
   int read = 0;
   byte[] bytes = new byte[1024];
   while ((read = protectPDF.read(bytes)) != -1) {
   outputStream.write(bytes, 0, read);
   }
   System.out.println("protectPDFDocument totalTime = " + (System.currentTimeMillis() - startTime));
   outputStream.close();
   inputFileStream.close();
   System.out.println("Document Protected Successfully");
   return license;
   }
   }
   ```
