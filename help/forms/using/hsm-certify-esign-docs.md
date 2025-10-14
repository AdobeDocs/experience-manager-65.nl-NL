---
title: Met HSM documenten digitaal ondertekenen of certificeren
description: Gebruik HSM-server of eToken-apparaat om PDF-documenten te ondertekenen/certificeren.
contentOwner: vishgupt
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
feature: Document Services
exl-id: 62adca19-8ed0-48b3-b7eb-9dbc3d8f96c6
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '684'
ht-degree: 0%

---

# Met HSM documenten digitaal ondertekenen of certificeren {#use-hsm-to-digitally-sign-or-certify-documents}

Hardwarebeveiligingsmodules (HSM) en -netwerken zijn speciale, geharde en tamperresistente computerapparaten die zijn ontworpen voor het veilig beheren, verwerken en opslaan van digitale sleutels. Deze apparaten zijn direct verbonden met een computer of een netwerkserver.

Adobe Experience Manager Forms kan referenties gebruiken die zijn opgeslagen op een HSM of token om serverzijdige digitale handtekeningen elektronisch te ondertekenen of toe te passen op een document. Een HSM- of token-apparaat gebruiken met AEM Forms:

1. [&#x200B; laat de dienst DocAssurance &#x200B;](#configuredocassurance) toe.
1. [&#x200B; creeer een alias voor HSM of token apparaat in de Console van het AEM Web &#x200B;](#configuredeviceinaemconsole).
1. [&#x200B; gebruik de Dienst DocAssurance APIs om de documenten met digitale sleutels te ondertekenen of te certificeren die op het apparaat &#x200B;](#programatically) worden opgeslagen.

## Voordat u HSM configureert of de apparaten instelt met AEM Forms {#configurehsmetoken}

* Installeer het [&#x200B; toe:voegen-op &#x200B;](https://helpx.adobe.com/nl/aem-forms/kb/aem-forms-releases.html) pakket van AEM Forms.
* Installeer en configureer HSM of installeer de clientsoftware op dezelfde computer als de AEM. De cliëntsoftware wordt vereist om met HSM en apparaten te communiceren.

## De DocAssurance-service inschakelen {#configuredocassurance}

De dienst DocAssurance is standaard niet ingeschakeld. Voer de volgende stappen uit om de service in te schakelen:

1. Stop de instantie Auteur van uw AEM Forms-omgeving.

1. Open het [ AEM_root ] \crx-quickstart\conf\sling.properties- dossier uit te geven.

   >[!NOTE]
   >
   >Als u het [ AEM_root ] \crx-quickstart\bin\start.bat- dossier hebt gebruikt om de AEM instantie te beginnen, dan open [ AEM_root ] \ crx-quickstart \ sling.properties- dossier voor het uitgeven.

1. Voeg de volgende eigenschappen toe of vervang de volgende eigenschappen aan het bestand sling.properties:

   ```shell
   sling.bootdelegation.sun=sun.*,com.sun.*,sun.misc.*
   sling.bootdelegation.ibm=com.ibm.xml.*,com.ibm.*
   sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*  
   ```

1. Sla het bestand sling.properties op en sluit het.
1. Start de AEM opnieuw.

>[!NOTE]
>
> Het wordt aanbevolen de SDK opnieuw te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM ontwikkelomgeving.

<!--

## Set up certificates for Reader extensions {#set-up-certificates-for-reader-extensions}

Perform the following steps to setup certificates:

1. Log in to AEM Author instance as an administrator.

1. Click **Adobe Experience Manager** on Global Navigation Bar. Go to **Tools** &gt;  **Security** &gt;  **Users**.
1. Click the **name** field of the user account. The **Edit User Settings** page opens.
1. On the AEM Author instance, certificates reside in a KeyStore. If you have not created a KeyStore earlier, click **Create KeyStore** and set a new password for the KeyStore. If the server already contains a KeyStore, skip this step.

1. On the **Edit User Settings** page, click **Manage KeyStore**.

1. On KeyStore Management dialog, expand the **Add Private Key from Key Store file** option and provide an alias. The alias is used to perform the Reader Extensions operation.
1. To upload the certificate file, click **Select Key Store File** and upload a `.pfx` file.
1. Add the **Key Store Password**,**Private Key Password**, and **Private Key Alias** that is associated with the certificate to the respective fields. Click **Submit**.

   >[!NOTE]
   >
   >To determine the **Private Key Alias** of a certificate, you can use the Java keytool command: `keytool -list -v -keystore [keystore-file] -storetype pkcs12`

   >[!NOTE]
   >
   >In the **Key Store Password** and **Private Key Password** fields, specify the password provided with the certificate file.

>[!NOTE]
>
>For AEM Forms on OSGi, to verify the signed PDF, the root certificate installed in the Trust Store.

>[!NOTE]
>
>On moving to production environment, replace your evaluation credentials with production credentials. Ensure that you delete your old Reader Extensions credentials, before updating an expired or evaluations credential.

-->


## Een alias voor het apparaat maken {#configuredeviceinaemconsole}

De alias bevat alle parameters die een HSM of token vereist. Voer de onderstaande instructies uit om een alias te maken voor elke HSM of voor de token-referentie die door eSign of Digital Signatures wordt gebruikt:

1. Open de AEM console. De standaard-URL van de AEM is https://&lt;host>:&lt;port>/system/console/configMgr
1. Open de **Dienst van de Configuratie van de Credentials HSM** en specificeer waarden voor de volgende gebieden:

   * **Referentie Alias**: Specificeer een koord dat wordt gebruikt om alias te identificeren. Deze waarde wordt gebruikt als een eigenschap voor bepaalde bewerkingen met digitale handtekeningen, zoals de bewerking Handtekeningveld ondertekenen.
   * **Weg DLL**: Specificeer de weg van uw HSM of vastgestelde cliëntbibliotheek op de server. Bijvoorbeeld `C:\Program Files\LunaSA\cryptoki.dll` . In een gegroepeerde omgeving moet u ervoor zorgen dat alle servers in de cluster een identiek pad gebruiken.
   * **Punt HSM**: Specificeer het wachtwoord dat wordt vereist om tot de apparatensleutel toegang te hebben.
   * **Identiteitskaart van de Slot HSM**: Specificeer een groef herkenningsteken van type geheel. De groef ID wordt geplaatst op een cliënt-door-cliënt basis. Het wordt gebruikt om de groef op HSM te identificeren die de privé sleutel voor teken/certificatie bevat.

   >[!NOTE]
   >
   >Geef tijdens het configureren van Etoken een numerieke waarde op voor het veld Id van HSM-sleuf. Er is een numerieke waarde vereist om de handtekeningbewerkingen te laten werken.

   * **Certificaat SHA1**: Specificeer de waarde SHA1 (duimdruk) van het openbare zeer belangrijke (.cer) dossier voor de referentie die u gebruikt. Zorg ervoor dat er geen spaties worden gebruikt in de SHA1-waarde.
   * **Type van Apparaat HSM**: Selecteer de fabrikant van HSM (Luna of andere) of Symbolisch apparaat.

   Klik **sparen**. De beveiligingsmodule voor hardware is geconfigureerd voor AEM Forms. U kunt nu de beveiligingsmodule voor hardware in AEM Forms gebruiken om documenten te ondertekenen of te certificeren.

## Gebruik de DocAssurance Service-API&#39;s om een document te ondertekenen of certificeren met digitale sleutels die op het apparaat zijn opgeslagen  {#programatically}

In de volgende voorbeeldcode wordt een HSM-document gebruikt of geactiveerd om een document te ondertekenen of certificeren.

```java
/*************************************************************************
 *
 * ADOBE CONFIDENTIAL
 * ___________________
 *
 * Copyright 2014 Adobe Systems Incorporated
 * All Rights Reserved.
 *
 * NOTICE:  All information contained herein is, and remains
 * the property of Adobe Systems Incorporated and its suppliers,
 * if any.  The intellectual and technical concepts contained
 * herein are proprietary to Adobe Systems Incorporated and its
 * suppliers and are protected by trade secret or copyright law.
 * Dissemination of this information or reproduction of this material
 * is strictly forbidden unless prior written permission is obtained
 * from Adobe Systems Incorporated.
 **************************************************************************/
package com.adobe.docassurance.samples;

import java.io.ByteArrayInputStream;
import java.io.IOException;
import java.io.InputStream;

import javax.jcr.Binary;
import javax.jcr.Node;
import javax.jcr.RepositoryException;
import javax.jcr.Session;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.Service;
import org.apache.sling.api.resource.ResourceResolver;
import org.apache.sling.jcr.api.SlingRepository;
import org.apache.sling.jcr.resource.JcrResourceResolverFactory;

import com.adobe.aemfd.docmanager.Document;
import com.adobe.fd.docassurance.client.api.DocAssuranceException;
import com.adobe.fd.docassurance.client.api.DocAssuranceService;
import com.adobe.fd.docassurance.client.api.DocAssuranceServiceOperationTypes;
import com.adobe.fd.docassurance.client.api.SignatureOptions;
import com.adobe.fd.signatures.client.types.exceptions.InvalidArgumentException;
import com.adobe.fd.signatures.pdf.inputs.CredentialContext;
import com.adobe.fd.signatures.pdf.inputs.DSSPreferences;
import com.adobe.fd.signatures.pdf.inputs.DSSPreferencesImpl;
import com.adobe.fd.signatures.pdf.inputs.PDFSignatureAppearenceOptions;
import com.adobe.fd.signatures.pdf.inputs.UnlockOptions;
import com.adobe.fd.signatures.pdf.inputs.PDFSignatureAppearenceOptions.PDFSignatureAppearanceType;
import com.adobe.fd.signatures.pdf.inputs.PDFSignatureAppearenceOptions.TextDirection;
import com.adobe.fd.signatures.pki.client.types.common.HashAlgorithm;
import com.adobe.fd.signatures.pki.client.types.common.RevocationCheckStyle;
import com.adobe.fd.signatures.pki.client.types.prefs.CRLPreferences;
import com.adobe.fd.signatures.pki.client.types.prefs.CRLPreferencesImpl;
import com.adobe.fd.signatures.pki.client.types.prefs.GeneralPreferencesImpl;
import com.adobe.fd.signatures.pki.client.types.prefs.PKIPreferences;
import com.adobe.fd.signatures.pki.client.types.prefs.PKIPreferencesImpl;
import com.adobe.fd.signatures.pki.client.types.prefs.PathValidationPreferences;
import com.adobe.fd.signatures.pki.client.types.prefs.PathValidationPreferencesImpl;

/**
 * Digital signatures can be applied to PDF documents to provide a level of security. Digital signatures, like handwritten signatures, provide a means by which signers
 * identify themselves and make statements about a document. The technology used to digitally sign documents helps to ensure that both the signer and recipients are clear
 * about what was signed and confident that the document was not altered since it was signed.
 *
 * PDF documents are signed by means of public-key technology. A signer has two keys: a public key and a private key. The private key is stored in a user's credential that
 * must be available at the time of signing. The public key is stored in the user's certificate that must be available to recipients to validate the signature. Information
 * about revoked certificates is found in certificate revocation lists (CRLs) and Online Certificate Status Protocol (OCSP) responses distributed by Certificate Authorities (CAs).
 * The time of signing can be obtained from a trusted source known as a Timestamping Authority.
 *
 * The following Java code example digitally signs a PDF document that is based on a PDF file.
 * The alias that is specified for the security credential is secure, and revocation checking is performed.
 * Because no CRL or OCSP server information is specified, the server information is obtained from the certificate used to
 * digitally sign the PDF document
 *
 * PreRequisites - Digital certificate for signing the document has to be uploaded on Granite Key Store
 */

@Component
@Service(value=Sign.class)
public class Sign{
 @Reference
 private DocAssuranceService docAssuranceService;

 @Reference
    private SlingRepository slingRepository;

 @Reference
    private JcrResourceResolverFactory jcrResourceResolverFactory ;

 /**
  *
  * @param inputFile - path to the pdf document stored at JCR node
  * @param outputFile - path to the pdf document where the output needs to be stored
  * @throws IOException
  * @throws RepositoryException
  * @throws InvalidArgumentException
  * @throws DocAssuranceException
  */
 public void signExtend(String inputFile, String outputFile, String alias) throws IOException, RepositoryException, InvalidArgumentException, DocAssuranceException{

  Document inDoc = new Document(inputFile);
  Document outDoc = null;

  Session adminSession = null;
        ResourceResolver resourceResolver = null;
        try {

          /** resourceResolver with admin privileges to be passed to SignatureServiceAPI and Reader Extensions
          the resource resolver for signature options has to be corresponding to the user who has the signing certificate in his granite key store
          the resource resolver for signature options has to be corresponding to the user who has the credential for reader extension in his granite key store
          here we are using the same resource resolver
          */
          adminSession = slingRepository.loginAdministrative(null);
             resourceResolver = jcrResourceResolverFactory.getResourceResolver(adminSession);

             //retrieve specifications for each of the services, you may pass null if you do not want to use that service
             //as we do not want encryption in this case, passing null for Encryption Options
             //for encrypted document pass Unlock Options - see the method getUnlockOptions() below
    outDoc = docAssuranceService.secureDocument(inDoc, null, getSignatureOptions(alias,resourceResolver),null,null);
        }
  catch(Exception e){
   e.printStackTrace();
  }
        finally{
            /**
             * always close the PDFDocument object after your processing is done.
             */
            if(inDoc != null){
                inDoc.close();
            }
            if(adminSession != null && adminSession.isLive()){
                if(resourceResolver != null){
                    resourceResolver.close();
                }
                adminSession.logout();
            }
        }

        //flush the output document contents to JCR Node
  flush(outDoc, outputFile);

 }

 /**
  *
  * @param rr resource resolver corresponding to the user with the access to signing credential for the
  * given alias "allcertificatesanypolicytest11ee_new" in this case
  * @return SignatureOptions
  */
 private SignatureOptions getSignatureOptions(String alias, ResourceResolver rr){

  //create an instance of SignatureOptions
  SignatureOptions signatureOptions = SignatureOptions.getInstance();

  //set the operation you want to perform - SIGN/CERTIFY
  signatureOptions.setOperationType(DocAssuranceServiceOperationTypes.SIGN);

  //field to sign
  String fieldName = "Signature1" ;

        //Hash Algo to be used to compute digest the PDF document
        HashAlgorithm algo = HashAlgorithm.SHA384;

        //Reason for signing/certifying
        String reason = "Test Reason";

        //location of the signer
        String location = "Test Location";

        //contact info of the signer
        String contactInfo = "Test Contact";

        //Create a PDFSignatureAppearanceOptions object
        //and show date information
        PDFSignatureAppearenceOptions appOptions = new PDFSignatureAppearenceOptions(
                PDFSignatureAppearanceType.NAME, null, 1.0d, null, true, true,
                true, true, true, true, true, TextDirection.AUTO);

        signatureOptions.setSignatureFieldName(fieldName);
        signatureOptions.setAlgo(algo);
        signatureOptions.setContactInfo(contactInfo);
        signatureOptions.setLocation(location);
        signatureOptions.setSigAppearence(appOptions);
        signatureOptions.setReason(reason);
        signatureOptions.setDssPref(getDSSPreferences(rr));
        signatureOptions.setCredential(new CredentialContext(alias, rr, true));
  return signatureOptions;
 }

 private DSSPreferences getDSSPreferences(ResourceResolver rr){
  //sets the DSS Preferences
        DSSPreferencesImpl prefs = DSSPreferencesImpl.getInstance();
        prefs.setPKIPreferences(getPKIPreferences());
        GeneralPreferencesImpl gp = (GeneralPreferencesImpl) prefs.getPKIPreferences().getGeneralPreferences();
        gp.setDisableCache(true);
        return prefs;
    }

    private PKIPreferences getPKIPreferences(){
     //sets the PKI Preferences
        PKIPreferences pkiPref = new PKIPreferencesImpl();
        pkiPref.setCRLPreferences(getCRLPreferences());
        pkiPref.setPathPreferences(getPathValidationPreferences());
        return pkiPref;
    }

    private CRLPreferences getCRLPreferences(){
        //specifies the CRL Preferences
        CRLPreferencesImpl crlPrefs = new CRLPreferencesImpl();
        crlPrefs.setRevocationCheck(RevocationCheckStyle.CheckIfAvailable);
        crlPrefs.setGoOnline(true);
        return crlPrefs;
    }

    private PathValidationPreferences getPathValidationPreferences(){
     //sets the path validation preferences
        PathValidationPreferencesImpl pathPref = new PathValidationPreferencesImpl();
        pathPref.setDoValidation(false);
        return pathPref;

    }

    /**
     * sets Unlock Options for encrypted PDF
     */
    private UnlockOptions getUnlockOptions(){
        UnlockOptions unlockOptions = new UnlockOptions();
        //sets the Open Password for password encrypted PDF
        unlockOptions.setPassword("OpenPassword");

        //for Certificate Encrypted Document, set the alias of the credential uploaded in the user's key store
        //and corresponding resource resolver

        return unlockOptions;

    }
    /**
     * This method copies the data from {@code Document}, to the specified file at the given resourcePath.
     * @param doc
     * @param resourcePath
     * @throws IOException
     */
    private void flush(Document doc, String resourcePath) throws IOException {
   //extracts the byte data from Document
   byte[] output = doc.getInlineData();
   Binary opBin;
   Session adminSession = null;
      try {
         adminSession = slingRepository.loginAdministrative(null);

         //get access to the specific node
         //here we are assuming that node exists
           Node node = adminSession.getNode(resourcePath);

           //convert byte[] to Binary
           opBin = adminSession.getValueFactory().createBinary((InputStream)new ByteArrayInputStream(output));

           //set the Binary data value to node's jcr:data
           node.getNode("jcr:content").getProperty("jcr:data").setValue(opBin);
      } catch (RepositoryException e) {

      }
      finally{

       if(adminSession != null && adminSession.isLive()){
        try {
      adminSession.save();
      adminSession.logout();
     } catch (RepositoryException e) {

     }

             }
      }

  }
}
```

Als u van AEM 6.0 Vorm of AEM 6.1 Forms hebt bevorderd, en u de dienst DocAssurance in de vorige versie gebruikte, dan:

* Om de dienst DocAssurance zonder een HSM te gebruiken of apparaat te sluiten, gebruik blijven gebruikend de bestaande code.
* Als u de DocAssurance-service wilt gebruiken met een HSM- of token-apparaat, vervangt u de bestaande CredentialContext-objectcode door de API hieronder.

```java
/**
  *
  * @param credentialAlias alias of the PKI Credential stored in CQ Key Store or
  * the alias of the HSM Credential configured using HSM Credentials Configuration Service.
  * @param resourceResolver corresponding to the user with the access to the key store and trust store.
  * @param isHSMCredential if the alias is corresponding to HSM Credential.
  */
 public CredentialContext(String credentialAlias, ResourceResolver resourceResolver, boolean isHSMCredential);
```

Voor gedetailleerde informatie over APIs en steekproefcode van de dienst DocAssurance, zie [&#x200B; Programmatiatically Gebruikend AEM de Diensten van het Document &#x200B;](/help/forms/using/aem-document-services-programmatically.md).
