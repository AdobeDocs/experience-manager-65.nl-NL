---
title: Met HSM documenten digitaal ondertekenen of certificeren
seo-title: Met HSM kunt u elektronisch ondertekende documenten certificeren
description: Gebruik HSM- of token-apparaten om elektronisch ondertekende documenten te certificeren
seo-description: Gebruik HSM- of token-apparaten om elektronisch ondertekende documenten te certificeren
uuid: bbe057c1-6150-41f9-9c82-4979d31d305d
contentOwner: vishgupt
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
discoiquuid: 536bcba4-b754-4799-b0d2-88960cc4c44a
translation-type: tm+mt
source-git-commit: 35b2c9c8c79b3cc3d81e0b92ea17cd7d599fa7ee
workflow-type: tm+mt
source-wordcount: '1010'
ht-degree: 0%

---


# Met HSM documenten digitaal ondertekenen of certificeren {#use-hsm-to-digitally-sign-or-certify-documents}

Hardwarebeveiligingsmodules (HSM) en -netwerken zijn speciale, geharde en tamperresistente computerapparaten die zijn ontworpen voor het veilig beheren, verwerken en opslaan van digitale sleutels. Deze apparaten zijn direct verbonden met een computer of een netwerkserver.

Adobe Experience Manager Forms kan referenties gebruiken die zijn opgeslagen op een HSM of token om serverzijdige digitale handtekeningen elektronisch te ondertekenen of toe te passen op een document. Een HSM- of token-apparaat gebruiken met AEM Forms:

1. Schakel de DocAssurance-service in.
1. Certificaten instellen voor extensie Reader.
1. Maak een alias voor het HSM- of token-apparaat in AEM webconsole.
1. Gebruik de DocAssurance Service-API&#39;s om de documenten te ondertekenen of certificeren met digitale sleutels die op het apparaat zijn opgeslagen.

## Voordat u HSM configureert of de apparaten instelt met AEM Forms {#configurehsmetoken}

* Installeer het [AEM Forms-add-on](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) -pakket.
* HSM installeren en configureren of clientsoftware installeren op dezelfde computer als AEM server. De cliëntsoftware wordt vereist om met HSM en apparaten te communiceren.
* (Alleen Microsoft Windows) Stel de omgevingsvariabele JAVA_HOME_32 zo in dat deze naar de map verwijst waar de 32-bits versie van Java 8 Development Kit (JDK 8) is geïnstalleerd. Het standaardpad van de map is C:\Program Files(x86)\Java\jdk&lt;version>
* (Alleen AEM Forms op OSGi) Installeer het basiscertificaat in de vertrouwde opslag. Het is vereist om de ondertekende PDF te controleren

>[!NOTE]
>
>In Microsoft Windows worden alleen 32-bits LunaSA- of EToken-clients ondersteund.

## De DocAssurance-service inschakelen {#configuredocassurance}

De dienst DocAssurance is standaard niet ingeschakeld. Voer de volgende stappen uit om de service in te schakelen:

1. Stop de instantie Auteur van uw AEM Forms-omgeving.

1. Open het bestand [AEM_root]\crx-quickstart\conf\sling.properties om te bewerken.

   >[!NOTE]
   >
   >Als u het bestand [AEM_root]\crx-quickstart\bin\start.bat hebt gebruikt om de AEM instantie te starten, opent u het bestand [AEM_root]\crx-quickstart\sling.properties.

1. Voeg de volgende eigenschappen toe of vervang de volgende eigenschappen aan het bestand sling.properties:

   ```shell
   sling.bootdelegation.sun=sun.*,com.sun.*,sun.misc.*
   sling.bootdelegation.ibm=com.ibm.xml.*,com.ibm.*
   sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*  
   ```

1. Sla het bestand sling.properties op en sluit het.
1. Start de AEM opnieuw.

## Certificaten instellen voor extensies van Readers {#set-up-certificates-for-reader-extensions}

Voer de volgende stappen uit om certificaten in te stellen:

1. Meld u als beheerder aan bij de AEM-auteur-instantie.

1. **Klik op Adobe-Experience Manager** op de algemene navigatiebalk. Ga naar **Gereedschappen** > **Beveiliging** > **Gebruikers**.
1. Klik op het veld **Naam** van de gebruikersaccount. De pagina Gebruikersinstellingen **** bewerken wordt geopend.
1. Voor de instantie van de Auteur AEM, verblijven de certificaten in een KeyStore. Als u nog niet eerder een KeyStore hebt gemaakt, klikt u op **Create KeyStore** en stelt u een nieuw wachtwoord in voor de KeyStore. Als de server al een KeyStore bevat, slaat u deze stap over.

1. Klik op de pagina Gebruikersinstellingen **** bewerken op KeyStore **** beheren.

1. Vouw in het dialoogvenster KeyStore Management de optie Persoonlijke sleutel **toevoegen uit sleutelarchiefbestand** uit en geef een alias op. De alias wordt gebruikt om de bewerking Reader Extensions uit te voeren.
1. Als u het certificaatbestand wilt uploaden, klikt u op Bestand **sleutelarchief** selecteren en uploadt u een `.pfx` bestand.
1. Voeg het **Sleutelwachtwoord** van de Opslag, het Wachtwoord **van de** Persoonlijke Sleutel, en de Alias **van de** Persoonlijke Sleutel toe die met het certificaat aan de respectieve gebieden wordt geassocieerd. Klik op **Verzenden**.

   >[!NOTE]
   >
   >Als u de alias **** Persoonlijke sleutel van een certificaat wilt bepalen, gebruikt u de Java-opdracht Keytool: `keytool -list -v -keystore [keystore-file] -storetype pkcs12`

   >[!NOTE]
   >
   >Geef in de velden Wachtwoord **sleutelarchief en Wachtwoord** **** persoonlijke sleutel het wachtwoord op dat bij het certificaatbestand wordt geleverd.

>[!NOTE]
>
>Voor AEM Forms op OSGi wordt het basiscertificaat geïnstalleerd in het Trust Store om de ondertekende PDF te verifiëren.

>[!NOTE]
>
>Vervang bij de overgang naar de productieomgeving uw evaluatiegegevens door productiegegevens. Zorg ervoor dat u uw oude geloofsbrieven van de Uitbreidingen van de Reader schrapt, alvorens een verlopen of evaluatiereferentie bij te werken.

## Een alias voor het apparaat maken {#configuredeviceinaemconsole}

De alias bevat alle parameters die een HSM of token vereist. Voer de onderstaande instructies uit om een alias te maken voor elke HSM of voor de token-referentie die door eSign of Digital Signatures wordt gebruikt:

1. Open AEM console. De standaard-URL van AEM console is https://&lt;host>:&lt;port>/system/console/configMgr
1. Open de **HSM Credentials Configuration Service** en geef waarden op voor de volgende velden:

   * **Alias** referentie: Geef een tekenreeks op die wordt gebruikt om de alias te identificeren. Deze waarde wordt gebruikt als een eigenschap voor bepaalde bewerkingen met digitale handtekeningen, zoals de bewerking Handtekeningveld ondertekenen.
   * **DLL-pad**: Geef het volledig gekwalificeerde pad van uw HSM- of toepassingsclientbibliotheek op de server op. Bijvoorbeeld C:\Program Files\LunaSA\cryptoki.dll. In een gegroepeerde omgeving moet dit pad identiek zijn voor alle servers in de cluster.
   * **HSM-punt**: Geef het wachtwoord op dat nodig is voor toegang tot de apparaattoets.
   * **HSM-sleuf-id**: Geef een sleuf-id op van het type geheel getal. De sleuf-id wordt per client ingesteld. Als u een tweede machine aan een verschillende verdeling (bijvoorbeeld, HSMPART2 op het zelfde apparaat HSM) registreert, dan wordt groef 1 geassocieerd met de verdeling HSMPART2 voor de cliënt.

   >[!NOTE]
   >
   >Geef tijdens het configureren van Etoken een numerieke waarde op voor het veld Id van HSM-sleuf. Er is een numerieke waarde vereist om de handtekeningbewerkingen te laten werken.

   * **Certificaat SHA1**: Geef SHA1-waarde (miniafdruk) van het bestand met de openbare sleutel (.cer) op voor de referentie die u gebruikt. Zorg ervoor dat er geen spaties worden gebruikt in de SHA1-waarde. Als u een fysiek certificaat gebruikt, is dit niet verplicht.
   * **Type** HSM-apparaat: Selecteer de fabrikant van de HSM (Luna of andere) of het Symbolische apparaat.

   Click **Save**. De beveiligingsmodule voor hardware is geconfigureerd voor AEM Forms. U kunt nu de beveiligingsmodule voor hardware in AEM Forms gebruiken om documenten te ondertekenen of te certificeren.

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

             //retrieve specifications for each of the services, you may pass null if you don't want to use that service
             //as we don't want encryption in this case, passing null for Encryption Options
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

* Om de dienst DocAssurance zonder een HSM te gebruiken of apparaat te sluiten, gebruik het bestaande code.
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

Voor gedetailleerde informatie over APIs en steekproefcode van de dienst DocAssurance, zie Programmatiatically het [Gebruiken van AEM Diensten van het Document](/help/forms/using/aem-document-services-programmatically.md).
