---
title: Programmaticaal AEM Document Services gebruiken
seo-title: Programmaticaal AEM Document Services gebruiken
description: Leer hoe u API's van Document Services gebruikt om PDF-documenten digitaal te ondertekenen, te versleutelen en te genereren.
seo-description: Leer hoe u API's van Document Services gebruikt om PDF-documenten digitaal te ondertekenen, te versleutelen en te genereren.
uuid: bf5ee197-4daf-4a64-8b6d-2c0d1f232b1c
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
discoiquuid: 32118d3b-54d0-4283-b489-780bdcbfc8d2
translation-type: tm+mt
source-git-commit: f9389a06f9c2cd720919486765cee76257f272c3

---


# Programmaticaal AEM Document Services gebruiken {#using-aem-document-services-programmatically}

Clientklassen die zijn vereist om Maven Projecten te bouwen met AEM Document Services zijn beschikbaar in de [AEM Forms Client SDK](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) jar. Voor informatie rond beproefde projecten, zie [hoe te om uw AEM- project te bouwen gebruikend Maven](/help/sites-developing/ht-projects-maven.md).

>[!NOTE]
>
>Alvorens de dienst DocAssurance APIs te gebruiken, [vorm de dienst](/help/forms/using/install-configure-document-services.md)DocAssurance.

## DocAssurance Service {#docassurance-service}

De dienst DocAssurance omvat de volgende diensten:

* Handtekeningenservice
* Coderingsservice
* Reader Extension Service

U kunt de volgende verrichtingen uitvoeren gebruikend de dienst DocAssurance:

* [Onzichtbare handtekening toevoegen](/help/forms/using/aem-document-services-programmatically.md#p-adding-an-invisible-signature-field-p)

* [Handtekeningveld toevoegen](/help/forms/using/aem-document-services-programmatically.md#p-adding-a-signature-field-nbsp-p)
* [Tijdstempel document toepassen](/help/forms/using/aem-document-services-programmatically.md#apply-document-timestamp)

* [Handtekening ophalen](/help/forms/using/aem-document-services-programmatically.md#p-getting-signature-p)
* [Veld voor handtekening ophalen](/help/forms/using/aem-document-services-programmatically.md#p-getting-signature-field-list-nbsp-p)
* [Handtekeningvelden wijzigen](/help/forms/using/aem-document-services-programmatically.md#p-modifying-signature-fields-nbsp-p)

* [Veilig document](/help/forms/using/aem-document-services-programmatically.md#p-securing-documents-p)

* [Rechten van referentie-gebruik ophalen](/help/forms/using/aem-document-services-programmatically.md#p-getting-credential-usage-rights-p)

* [Rechten voor documentgebruik ophalen](/help/forms/using/aem-document-services-programmatically.md#p-getting-document-usage-rights-p)

* [Gebruiksrechten verwijderen](/help/forms/using/aem-document-services-programmatically.md#p-removing-usage-rights-p)
* [Digitale handtekeningen verifiëren](/help/forms/using/aem-document-services-programmatically.md#p-verifying-digital-signatures-p)
* [Meerdere digitale handtekeningen verifiëren](/help/forms/using/aem-document-services-programmatically.md#p-verifying-multiple-digital-signatures-p)
* [Digitale handtekeningen verwijderen](/help/forms/using/aem-document-services-programmatically.md#p-removing-digital-signatures-p)

* [Certificeringshandtekeningveld ophalen](/help/forms/using/aem-document-services-programmatically.md#p-getting-certifying-signature-field-p)
* [PDF-versleutelingstype ophalen](/help/forms/using/aem-document-services-programmatically.md#p-getting-pdf-encryption-type-p)
* [Wachtwoordversleuteling verwijderen](/help/forms/using/aem-document-services-programmatically.md#p-removing-password-encryption-from-pdf-p)

* [Certificaatversleuteling verwijderen](/help/forms/using/aem-document-services-programmatically.md#p-removing-certificate-encryption-p)

>[!NOTE]
>
>Al deze services gebruiken het object Document als invoerparameter waarvoor de Javadoc-code kan worden gevonden op de URL [https://helpx.adobe.com/experience-manager/6-3/forms/javadocs/index.html](https://helpx.adobe.com/experience-manager/6-3/forms/javadocs/index.html)

### Een onzichtbaar handtekeningveld toevoegen {#adding-an-invisible-signature-field}

Digitale handtekeningen worden weergegeven in handtekeningvelden. Dit zijn formuliervelden met een grafische weergave van de handtekening. Handtekeningvelden kunnen zichtbaar of onzichtbaar zijn. Ondertekenaars kunnen een bestaand handtekeningveld gebruiken of een handtekeningveld programmatisch toevoegen. In beide gevallen moet het handtekeningveld bestaan voordat een PDF-document kan worden ondertekend. U kunt een handtekeningveld programmatisch toevoegen met de Java API of de API van de Signature-service van de Java-API. U kunt meerdere handtekeningvelden toevoegen aan een PDF-document. Elke handtekeningveldnaam moet echter uniek zijn.

**Syntaxis**: `addInvisibleSignatureField(Document inDoc, String signatureFieldName, FieldMDPOptionSpec fieldMDPOptionsSpec, PDFSeedValueOptionSpec seedValueOptionsSpec, UnlockOptions unlockOptions)`

**Invoerparameters**

<table>
 <tbody>
  <tr>
   <th>Parameters</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td><code>inDoc</code></td>
   <td>Document-object met PDF.<br /> </td>
  </tr>
  <tr>
   <td><code>signatureFieldName</code> </td>
   <td>De naam van het handtekeningveld. Deze parameter is verplicht en kan niet null als waarde hebben.<br /> </td>
  </tr>
  <tr>
   <td><code>fieldMDPOptionsSpec</code></td>
   <td>Een <code>FieldMDPOptionSpec</code> object dat aangeeft welke PDF-documentvelden zijn vergrendeld nadat het handtekeningveld is ondertekend. Deze parameter is optioneel en kan de waarde null accepteren.</td>
  </tr>
  <tr>
   <td><code>seedValueOptionsSpec</code></td>
   <td>Een <code>SeedValueOptions</code> object dat de verschillende zaadwaarden voor het veld opgeeft. T Deze parameter is optioneel en kan de waarde null accepteren.<span class="acrolinxCursorMarker"></span></td>
  </tr>
  <tr>
   <td><code>unlockOptions</code></td>
   <td>Omvat de parameters die nodig zijn om een gecodeerd bestand te ontgrendelen. Deze parameter is alleen vereist voor de gecodeerde bestanden.</td>
  </tr>
 </tbody>
</table>

Hier volgt een voorbeeld van een Java-code waarmee een onzichtbaar handtekeningveld wordt toegevoegd aan een PDF-document.

```
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

import java.io.File;
import java.io.IOException;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.Service;

import com.adobe.aemfd.docmanager.Document;
import com.adobe.fd.docassurance.client.api.DocAssuranceException;
import com.adobe.fd.docassurance.client.api.DocAssuranceService;
import com.adobe.fd.signatures.client.types.PositionRectangle;
import com.adobe.fd.signatures.client.types.exceptions.DuplicateSignatureFieldException;
import com.adobe.fd.signatures.client.types.exceptions.InvalidArgumentException;
import com.adobe.fd.signatures.client.types.exceptions.PDFOperationException;
import com.adobe.fd.signatures.client.types.exceptions.PermissionsException;
import com.adobe.fd.signatures.client.types.exceptions.SignaturesBaseException;
import com.adobe.fd.signatures.pdf.inputs.UnlockOptions;

/**
 * Digital signatures appear in signature fields, which are form fields that contain a graphic representation of the signature.
 * Signature fields can be visible or invisible. Signers can use a pre existing signature field, or a signature field can be
 * programmatically added. In either case, the signature field must exist before a PDF document can be signed.
 * You can programmatically add a signature field by using the Signature service Java API or Signature web service API.
 * You can add more than one signature field to a PDF document; however, each signature field name must be unique.
 *
 * The following Java code example adds an invisible signature field named SignatureField1 to a PDF document.
 */

@Component
@Service(value=AddInvisibleSignatureField.class)
public class AddInvisibleSignatureField {

 @Reference
 private DocAssuranceService docAssuranceService;

 /**
  *
  * @param inputFile - path to an pdf document stored at disk
  * @param outputFile - path where the output file has to be saved
  * @throws SignaturesBaseException
  * @throws DuplicateSignatureFieldException
  * @throws PermissionsException
  * @throws PDFOperationException
  * @throws InvalidArgumentException
  * @throws DocAssuranceException
  *
  */
 public void addInvisibleSignatureField(String inputFile, String outputFile) throws InvalidArgumentException, PDFOperationException, PermissionsException, DuplicateSignatureFieldException, SignaturesBaseException, DocAssuranceException {

  File inFile = new File(inputFile);
  Document inDoc = new Document(inFile);

  File outFile = new File(outputFile);
  Document outDoc = null;

        //Specify the name of the signature field
        String fieldName = "SignatureField1";

        //Create a  PositionRectangle object that specifies
        //the signature fields location
        PositionRectangle post = new  PositionRectangle(193,47,133,12);

        //Specify the page number that will contain the signature field
        java.lang.Integer pageNum = new java.lang.Integer(1);

        //Add a signature field to the PDF document
        try {
   outDoc = docAssuranceService.addInvisibleSignatureField(
       inDoc,
       fieldName,
       null,
       null,
       null);
  } catch (Exception e1) {
   // TODO Auto-generated catch block
   e1.printStackTrace();
  } // for an encrypted PDF input, pass unlock options

        //save the outDoc
        try {
   outDoc.copyToFile(outFile);
  } catch (IOException e) {
   // TODO Auto-generated catch block
   e.printStackTrace();
  }
 }

 /**
  *
  * UnlockOptions to be passed to addSignatureField() API to add a signature field in an encrypted pdf document.
  */
 private UnlockOptions getUnlockOptions(){
        UnlockOptions unlockOptions = new UnlockOptions();
        //sets the Open Password for password encrypted PDF
        unlockOptions.setPassword("OpenPassword");

        //for Certificate Encrypted Document, set the alias of the credential uploaded in the user's key store
        //and corresponding resource resolver

        return unlockOptions;

    }
}
```

U kunt ook de [](https://en.wikipedia.org/wiki/CAdES_%28computing%29)CAdES-specificatie gebruiken voor het ondertekenen van documenten. Gebruik de volgende voorbeeldcode om ondertekeningsindeling in te stellen op [CAdES.](https://en.wikipedia.org/wiki/CAdES_%28computing%29)

```java
SigningFormat signingFormat = SigningFormat.CAdES;
sigAppearence.setSigningFormat(signingFormat);
signOptions.setSigAppearence(sigAppearence);
```

### Een handtekeningveld toevoegen {#adding-a-signature-field-nbsp}

U kunt een handtekeningveld programmatisch toevoegen met de Java API of de API van de Signature-service van de Java-API. U kunt meerdere handtekeningvelden toevoegen aan een PDF-document. Elke handtekeningveldnaam moet echter uniek zijn.

**Syntaxis**:

```
public Document addSignatureField(Document inDoc,
 String signatureFieldName,
 Integer pageNo,
 PositionRectangle positionRectangle,
 FieldMDPOptionSpec fieldMDPOptionsSpec,
 PDFSeedValueOptionSpec seedValueOptionsSpec, UnlockOptions unlockOptions)
```

**Invoerparameters**

<table>
 <tbody>
  <tr>
   <th>Parameters</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td><code>inDoc</code></td>
   <td>Document, object dat PDF bevat</td>
  </tr>
  <tr>
   <td><code>signatureFieldName</code></td>
   <td>Naam van het handtekeningveld. Deze parameter is verplicht en kan geen null-waarde accepteren.</td>
  </tr>
  <tr>
   <td><code>pageNumber</code></td>
   <td>Het paginanummer waarop het handtekeningveld wordt toegevoegd. Geldige waarden zijn 1 tot het aantal pagina's in het document. Deze parameter is verplicht en kan geen null-waarde accepteren.<br /> </td>
  </tr>
  <tr>
   <td><code>positionRectangle</code></td>
   <td>A <code>PositionRectangle object</code> that specifies the position for the signature field. Deze parameter is verplicht en kan geen null-waarde accepteren. Als de opgegeven rechthoek zich niet ten minste gedeeltelijk in het uitsnijdvak van de opgegeven pagina bevindt, <code>InvalidArgumentException</code> wordt een object gegenereerd. Bovendien kan noch de hoogte noch de breedte van de opgegeven rechthoek 0 of negatief zijn. De coördinaten Y linksonder X of Y linksonder kunnen 0 of groter maar niet negatief zijn en zijn relatief ten opzichte van het uitsnijdvak van de pagina.</td>
  </tr>
  <tr>
   <td><code>fieldMDPOptionsSpec</code></td>
   <td>Een <code>FieldMDPOptionSpec</code> object dat aangeeft welke PDF-documentvelden zijn vergrendeld nadat het handtekeningveld is ondertekend. Dit is een optionele parameter en kan null zijn.</td>
  </tr>
  <tr>
   <td><code>seedValueOptionsSpec</code></td>
   <td>Een <code>SeedValueOptions</code> object dat de verschillende zaadwaarden voor het veld opgeeft. Dit is een optionele parameter en kan null zijn.</td>
  </tr>
  <tr>
   <td><code>unlockOptions</code></td>
   <td>Bevat de parameters die nodig zijn om een gecodeerd bestand te ontgrendelen. Deze parameter is alleen vereist voor de gecodeerde bestanden.</td>
  </tr>
 </tbody>
</table>

Hier volgt een voorbeeld van een Java-code waarmee een handtekeningveld wordt toegevoegd aan een PDF-document.

```java
/*************************************************************************
 *
-------------------------------------------------------------
*ADOBE SYSTEMS INCORPORATED
*Copyright 2014 Adobe Systems Incorporated
*All Rights Reserved.

*NOTICE:  Adobe permits you to use, modify, and distribute this file in accordance with the
*terms of the Adobe license agreement accompanying it.  If you have received this file from a
*source other than Adobe, then your use, modification, or distribution of it requires the prior
*written permission of Adobe.
-------------------------------------------------------------------------------------------------

 **************************************************************************/
package com.adobe.docassurance.samples;

import java.io.File;
import java.io.IOException;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.Service;

import com.adobe.aemfd.docmanager.Document;
import com.adobe.fd.docassurance.client.api.DocAssuranceException;
import com.adobe.fd.docassurance.client.api.DocAssuranceService;
import com.adobe.fd.signatures.client.types.PositionRectangle;
import com.adobe.fd.signatures.client.types.exceptions.DuplicateSignatureFieldException;
import com.adobe.fd.signatures.client.types.exceptions.InvalidArgumentException;
import com.adobe.fd.signatures.client.types.exceptions.PDFOperationException;
import com.adobe.fd.signatures.client.types.exceptions.PermissionsException;
import com.adobe.fd.signatures.client.types.exceptions.SignaturesBaseException;
import com.adobe.fd.signatures.pdf.inputs.UnlockOptions;

/**
 * Digital signatures appear in signature fields, which are form fields that contain a graphic representation of the signature.
 * Signature fields can be visible or invisible. Signers can use a pre existing signature field, or a signature field can be
 * programmatically added. In either case, the signature field must exist before a PDF document can be signed.
 * You can programmatically add a signature field by using the Signature service Java API or Signature web service API.
 * You can add more than one signature field to a PDF document; however, each signature field name must be unique.
 *
 * The following Java code example adds a signature field named SignatureField1 to a PDF document.
 */

@Component
@Service(value=AddSignatureField.class)
public class AddSignatureField {

 @Reference
 private DocAssuranceService docAssuranceService;

 /**
  *
  * @param inputFile - path to an pdf document stored at disk
  * @param outputFile - path where the output file has to be saved
  * @throws SignaturesBaseException
  * @throws DuplicateSignatureFieldException
  * @throws PermissionsException
  * @throws PDFOperationException
  * @throws InvalidArgumentException
  * @throws DocAssuranceException
  *
  */
 public void addSignatureField(String inputFile, String outputFile) throws InvalidArgumentException, PDFOperationException, PermissionsException, DuplicateSignatureFieldException, SignaturesBaseException, DocAssuranceException {

  File inFile = new File(inputFile);
  Document inDoc = new Document(inFile);

  File outFile = new File(outputFile);
  Document outDoc = null;

        //Specify the name of the signature field
        String fieldName = "SignatureField1";

        //Create a  PositionRectangle object that specifies
        //the signature fields location
        PositionRectangle post = new  PositionRectangle(193,47,133,12);

        //Specify the page number that will contain the signature field
        java.lang.Integer pageNum = new java.lang.Integer(1);

        //Add a signature field to the PDF document
        try {
   outDoc = docAssuranceService.addSignatureField(
       inDoc,
       fieldName,
       pageNum,
       post,
       null,
       null,
       null);
  } catch (Exception e1) {
   // TODO Auto-generated catch block
   e1.printStackTrace();
  } // for an encrypted PDF input, pass unlock options

        //save the outDoc
        try {
   outDoc.copyToFile(outFile);
  } catch (IOException e) {
   // TODO Auto-generated catch block
   e.printStackTrace();
  }
 }

 /**
  *
  * UnlockOptions to be passed to addSignatureField() API to add a signature field in an encrypted pdf document.
  */
 private UnlockOptions getUnlockOptions(){
        UnlockOptions unlockOptions = new UnlockOptions();
        //sets the Open Password for password encrypted PDF
        unlockOptions.setPassword("OpenPassword");

        //for Certificate Encrypted Document, set the alias of the credential uploaded in the user's key store
        //and corresponding resource resolver

        return unlockOptions;

    }
}
```

### Tijdstempel document toepassen {#apply-document-timestamp}

U kunt een document programmatisch stempelen volgens [PAdES 4](https://en.wikipedia.org/wiki/PAdES) specificaties. U kunt ook de [CAdES](https://en.wikipedia.org/wiki/CAdES_%28computing%29) -specificatie gebruiken voor aan transacties gerelateerde documenten.

**Syntaxis**: `applyDocumentTimeStamp(Document doc, VerificationTime verificationTime, ValidationPreferences dssPrefs, ResourceResolver resourceResolver, UnlockOptions unlockOptions)`

**Invoerparameters**

<table>
 <tbody>
  <tr>
   <th>Parameters</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td><code>doc</code> </td>
   <td>Document-object met PDF.<br /> </td>
  </tr>
  <tr>
   <td><code>VerificationTime</code></td>
   <td>Het tijdstip waarop de handtekening moet worden gevalideerd<br /> </td>
  </tr>
  <tr>
   <td><code>ValidationPreferences</code> </td>
   <td>Voorkeuren voor het besturen van validatieconfiguraties.</td>
  </tr>
  <tr>
   <td><code>ResourceResolver</code></td>
   <td>Resourceoplosser voor de graniet Trust Store.</td>
  </tr>
  <tr>
   <td><code>UnlockOptions</code></td>
   <td>Bevat de parameters die nodig zijn om een gecodeerd bestand te ontgrendelen. Dit is alleen vereist als het bestand is versleuteld.</td>
  </tr>
 </tbody>
</table>

Met de volgende codevoorbeelden wordt een tijdstempel toegevoegd aan een document volgens [PAdES 4](https://en.wikipedia.org/wiki/PAdES).

```java
package com.adobe.signatures.test;

import java.io.File;

import javax.jcr.Session;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Service;
import org.apache.sling.api.resource.ResourceResolver;
import org.apache.sling.jcr.api.SlingRepository;
import org.apache.sling.jcr.resource.JcrResourceResolverFactory;

import com.adobe.aemfd.docmanager.Document;
import com.adobe.fd.docassurance.client.api.DocAssuranceService;
import com.adobe.fd.signatures.client.types.VerificationTime;
import com.adobe.fd.signatures.pdf.inputs.ValidationPreferences;
import com.adobe.fd.signatures.pdf.inputs.ValidationPreferencesImpl;
import com.adobe.fd.signatures.pki.client.types.common.RevocationCheckStyle;
import com.adobe.fd.signatures.pki.client.types.prefs.CRLPreferences;
import com.adobe.fd.signatures.pki.client.types.prefs.CRLPreferencesImpl;
import com.adobe.fd.signatures.pki.client.types.prefs.OCSPPreferencesImpl;
import com.adobe.fd.signatures.pki.client.types.prefs.PKIPreferences;
import com.adobe.fd.signatures.pki.client.types.prefs.PKIPreferencesImpl;
import com.adobe.fd.signatures.pki.client.types.prefs.PathValidationPreferences;
import com.adobe.fd.signatures.pki.client.types.prefs.PathValidationPreferencesImpl;
import com.adobe.fd.signatures.pki.client.types.prefs.TSPPreferences;
import com.adobe.fd.signatures.pki.client.types.prefs.TSPPreferencesImpl;

 @Component
 @Service(value=Test.class)
 public class Test {

     @Reference
     private DocAssuranceService docAssuranceService;

     @Reference
     private SlingRepository slingRepository;

     @Reference
     private JcrResourceResolverFactory jcrResourceResolverFactory ;

     /**
      *
      * @param inputFile - path to the pdf document stored at disk
      * @param outputFile - path to the pdf document where the output needs to be stored
      * @throws Exception
      */
     public void TimeStamp(String inputFile, String outputFile) throws Exception{

         File inFile = new File(inputFile);
         Document inDoc = new Document(inFile);

         File outFile = new File(outputFile);
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

              VerificationTime verificationTime = getVerificationTimeForPades();
              ValidationPreferences dssPrefs = getValidationPreferences();

              //retrieve specifications for each of the services, you may pass null if you don't want to use that service
              //for encrypted document pass Unlock Options - see the method getUnlockOptions() below
               outDoc = docAssuranceService.applyDocumentTimeStamp(inDoc, verificationTime, dssPrefs, resourceResolver, null);
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

         outDoc.copyToFile(outFile);

     }

  public  VerificationTime getVerificationTimeForPades(){

         return VerificationTime.SECURE_TIME_ELSE_CURRENT_TIME;

     }

 /**
       * sets ValidationPreferences
       */
      private static ValidationPreferences getValidationPreferences(){

         ValidationPreferencesImpl prefs = new ValidationPreferencesImpl();
         prefs.setPKIPreferences(getPKIPreferences());

         //set the unlock options for processing an encrypted pdf document, do not set if the input doc is unprotected

         return prefs;

     }

   /**
       * sets PKIPreferences
       */
     private static PKIPreferences getPKIPreferences(){
         PKIPreferences pkiPref = new PKIPreferencesImpl();
         pkiPref.setCRLPreferences(getCRLPreferences());
         pkiPref.setPathPreferences(getPathValidationPreferences());
         pkiPref.setOCSPPreferences(getOCSPPref());
         pkiPref.setTSPPreferences(getTspPref());
         return pkiPref;
     }

   /**
      * sets CRL Preferences
      */
     private static CRLPreferences getCRLPreferences(){

         CRLPreferencesImpl crlPrefs = new CRLPreferencesImpl();
         crlPrefs.setRevocationCheck(RevocationCheckStyle.BestEffort);
         crlPrefs.setGoOnline(true);
         return crlPrefs;
     }

     /**
      *
      * sets PathValidationPreferences
      */
     private static PathValidationPreferences getPathValidationPreferences(){
         PathValidationPreferencesImpl pathPref = new PathValidationPreferencesImpl();
         pathPref.setDoValidation(true);
         return pathPref;

     }

   public static TSPPreferences getTspPref(){
   TSPPreferencesImpl tspPrefs=new TSPPreferencesImpl();
   char pass[]=new char[9];

   tspPrefs.setTspServerURL("TSPPrefs_ServerURL");
   tspPrefs.setUsername("TSPPrefs_Username");
   tspPrefs.setPassword(pass);
   tspPrefs.setSize(10240);
   return tspPrefs;
   }

     private static OCSPPreferencesImpl getOCSPPref(){
         OCSPPreferencesImpl ocsp = new OCSPPreferencesImpl();
         ocsp.setRevocationCheck(RevocationCheckStyle.BestEffort);
         return ocsp;
     }

}
```

### Handtekening ophalen {#getting-signature}

U kunt de namen ophalen van alle handtekeningvelden in een PDF-document dat u wilt ondertekenen of certificeren. Als u niet zeker weet welke namen van handtekeningvelden zich in een PDF-document bevinden of als u de namen wilt verifiëren, haalt u de namen via programmacode op. De service Handtekening retourneert de volledig gekwalificeerde naam van het handtekeningveld, zoals `form1[0].grantApplication[0].page1[0].SignatureField1[0]`.

**Syntaxis**: `getSignature(Document doc, String signatureFieldName, UnlockOptions unlockOptions)`

**Invoerparameters**

<table>
 <tbody>
  <tr>
   <th>Parameters</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td><code>doc</code> </td>
   <td>Document-object met PDF.<br /> </td>
  </tr>
  <tr>
   <td><code>signatureFieldName</code></td>
   <td>De naam van het handtekeningveld dat een handtekening bevat. Geef de volledig gekwalificeerde naam van het handtekeningveld op. Als u een PDF-document gebruikt dat is gebaseerd op een XFA-formulier, kan de gedeeltelijke naam van het handtekeningveld worden gebruikt. U kunt bijvoorbeeld <code>form1[0].#subform[1].SignatureField3[3]</code> opgeven als <code>SignatureField3[3]</code>.</td>
  </tr>
  <tr>
   <td><code>UnlockOptions</code></td>
   <td>Bevat de parameters die nodig zijn om een gecodeerd bestand te ontgrendelen. Dit is alleen vereist als het bestand is versleuteld.</td>
  </tr>
 </tbody>
</table>

In het volgende Java-codevoorbeeld worden de handtekeninggegevens opgehaald van het opgegeven handtekeningveld in een PDF-document.

```
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

import java.io.File;
import java.util.Iterator;
import java.util.List;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.Service;

import com.adobe.aemfd.docmanager.Document;
import com.adobe.fd.docassurance.client.api.DocAssuranceService;
import com.adobe.fd.signatures.client.types.PDFSignatureField;
import com.adobe.fd.signatures.client.types.exceptions.DuplicateSignatureFieldException;
import com.adobe.fd.signatures.client.types.exceptions.InvalidArgumentException;
import com.adobe.fd.signatures.client.types.exceptions.PDFOperationException;
import com.adobe.fd.signatures.client.types.exceptions.PermissionsException;
import com.adobe.fd.signatures.client.types.exceptions.SignaturesBaseException;
import com.adobe.fd.signatures.pdf.inputs.UnlockOptions;
import com.adobe.fd.signatures.client.types.PDFSignature;

/**
 * You can retrieve the names of all signature fields that are located in a PDF document that you want to sign or certify.
 * If you are unsure of the signature field names that are located in a PDF document or you want to verify the names, you can
 * programmatically retrieve them. The Signature service returns the fully qualified name of the signature field, such as
 * form1[0].grantApplication[0].page1[0].SignatureField1[0].
 *
 * The following Java code example retrieves the Signature Info for the given signature field located in a PDF document.
 */

@Component
@Service(value=GetSignature.class)
public class GetSignature {

 @Reference
 private DocAssuranceService docAssuranceService;

 /**
  *
  * @param inputFile - path to the pdf document stored at disk
  * @throws SignaturesBaseException
  * @throws DuplicateSignatureFieldException
  * @throws PermissionsException
  * @throws PDFOperationException
  * @throws InvalidArgumentException
  *
  */
 public void GetSignature(String inputFile) throws Exception {

  File inFile = new File(inputFile);
  Document inDoc = new Document(inFile);

  //Retrieve signature data for a given signature field.
  //for encrypted document pass Unlock Options - see the method getUnlockOptions() below
        PDFSignature pdfSignature = docAssuranceService.getSignature(inDoc,"fieldName",null);

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
}
```

### Lijst met handtekeningvelden ophalen {#getting-signature-field-list-nbsp}

U kunt de namen ophalen van alle handtekeningvelden in een PDF-document dat u wilt ondertekenen of certificeren. Als u niet zeker weet wat de namen van handtekeningvelden zijn in een PDF-document, kunt u deze via programmacode ophalen en verifiëren. De service Handtekening retourneert de volledig gekwalificeerde naam van het handtekeningveld, zoals `form1[0].grantApplication[0].page1[0].SignatureField1[0]`.

**Syntaxis**: `public List <PDFSignatureField> getSignatureFieldList (Document inDoc, UnlockOptions unlockOptions)`

**Invoerparameters**

| Parameters | Beschrijving |
|---|---|
| `inDoc` | Document, object dat PDF bevat |
| `unlockOptions` | Bevat de parameters die nodig zijn om een gecodeerd bestand te ontgrendelen. Dit is alleen vereist als het bestand is versleuteld. |

In het volgende Java-codevoorbeeld worden de namen opgehaald van handtekeningvelden in een PDF-document.

```java
/*************************************************************************
 *
 *
-------------------------------------------------------------
*ADOBE SYSTEMS INCORPORATED
*Copyright 2014 Adobe Systems Incorporated
*All Rights Reserved.

*NOTICE:  Adobe permits you to use, modify, and distribute this file in accordance with the
*terms of the Adobe license agreement accompanying it.  If you have received this file from a
*source other than Adobe, then your use, modification, or distribution of it requires the prior
*written permission of Adobe.
-------------------------------------------------------------------------------------------------
**************************************************************************/
package com.adobe.docassurance.samples;

import java.io.File;
import java.util.Iterator;
import java.util.List;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.Service;

import com.adobe.aemfd.docmanager.Document;
import com.adobe.fd.docassurance.client.api.DocAssuranceService;
import com.adobe.fd.signatures.client.types.PDFSignatureField;
import com.adobe.fd.signatures.client.types.exceptions.DuplicateSignatureFieldException;
import com.adobe.fd.signatures.client.types.exceptions.InvalidArgumentException;
import com.adobe.fd.signatures.client.types.exceptions.PDFOperationException;
import com.adobe.fd.signatures.client.types.exceptions.PermissionsException;
import com.adobe.fd.signatures.client.types.exceptions.SignaturesBaseException;
import com.adobe.fd.signatures.pdf.inputs.UnlockOptions;

/**
 * You can retrieve the names of all signature fields that are located in a PDF document that you want to sign or certify.
 * If you are unsure of the signature field names that are located in a PDF document or you want to verify the names, you can
 * programmatically retrieve them. The Signature service returns the fully qualified name of the signature field, such as
 * form1[0].grantApplication[0].page1[0].SignatureField1[0].
 *
 * The following Java code example retrieves the names of signature fields located in a PDF document.
 */

@Component
@Service(value=GetSignatureFields.class)
public class GetSignatureFields {

 @Reference
 private DocAssuranceService docAssuranceService;

 /**
  *
  * @param inputFile - path to the pdf document stored at disk
  * @throws SignaturesBaseException
  * @throws DuplicateSignatureFieldException
  * @throws PermissionsException
  * @throws PDFOperationException
  * @throws InvalidArgumentException
  *
  */
 public void getSignatureFields(String inputFile) throws Exception {

  File inFile = new File(inputFile);
  Document inDoc = new Document(inFile);

  //Retrieve the name of the document's signature fields
  //for encrypted document pass Unlock Options - see the method getUnlockOptions() below
        List fieldNames = docAssuranceService.getSignatureFieldList(inDoc,null);

        //Obtain the name of each signature field by iterating through the
        //List object
        Iterator iter = fieldNames.iterator();
        int i = 0 ;
        String fieldName="";
        while (iter.hasNext()) {
            PDFSignatureField signatureField = (PDFSignatureField)iter.next();
            fieldName = signatureField.getName();
            System.out.println("The name of the signature field is " +fieldName);
            i++;
        }
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
}
```

### Handtekeningvelden wijzigen {#modifying-signature-fields-nbsp}

U kunt handtekeningvelden in een PDF-document wijzigen. Als u een handtekeningveld wijzigt, moet u de vergrendelingswoordenboekwaarden van het handtekeningveld of de waarden van het zaadwaardewoordenboek bewerken.

Een veldvergrendelingswoordenboek geeft een lijst op met velden die zijn vergrendeld wanneer het handtekeningveld wordt ondertekend. Een vergrendeld veld voorkomt dat gebruikers het veld kunnen bewerken. Een zaadwaardewoordenboek bevat beperkende informatie die wordt gebruikt op het moment dat de handtekening wordt toegepast. U kunt bijvoorbeeld machtigingen wijzigen die de acties bepalen die kunnen plaatsvinden zonder een handtekening ongeldig te maken.

Door een bestaand handtekeningveld te wijzigen, kunt u het PDF-document bewerken in overeenstemming met veranderende zakelijke vereisten. Voor een nieuwe bedrijfsvereiste moeten bijvoorbeeld alle documentvelden worden vergrendeld nadat het document is ondertekend.

**Syntaxis**: `public Document modifySignatureField(Document inDoc, String signatureFieldName, PDFSignatureFieldProperties pdfSignatureFieldProperties, UnlockOptions unlockOptions)`

**Invoerparameters**

<table>
 <tbody>
  <tr>
   <th>Parameters</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td><code>inDoc</code></td>
   <td>Document, object dat PDF bevat</td>
  </tr>
  <tr>
   <td><code>signatureFieldName</code></td>
   <td>De naam van het handtekeningveld. Deze parameter is verplicht en kan geen null-waarde accepteren.<br /> </td>
  </tr>
  <tr>
   <td><code>pdfSignatureFieldProperties</code></td>
   <td>Object dat informatie opgeeft over de <code>PDFSeedValueOptionSpec</code> en de <code>FieldMDPOptionSpec</code> waarden van het handtekeningveld.</td>
  </tr>
  <tr>
   <td><code>unlockOptions</code></td>
   <td>Bevat de parameters die nodig zijn om een gecodeerd bestand te ontgrendelen. Dit is alleen vereist als het bestand is versleuteld.</td>
  </tr>
 </tbody>
</table>

In het volgende Java-codevoorbeeld wordt een handtekeningveld gewijzigd door alle velden in het formulier te vergrendelen wanneer een handtekening wordt toegepast op het handtekeningveld.

```java
/*************************************************************************
 *

-------------------------------------------------------------
*ADOBE SYSTEMS INCORPORATED
*Copyright 2014 Adobe Systems Incorporated
*All Rights Reserved.

*NOTICE:  Adobe permits you to use, modify, and distribute this file in accordance with the
*terms of the Adobe license agreement accompanying it.  If you have received this file from a
*source other than Adobe, then your use, modification, or distribution of it requires the prior
*written permission of Adobe.
-------------------------------------------------------------------------------------------------

 **************************************************************************/
package com.adobe.docassurance.samples;

import java.io.File;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.Service;

import com.adobe.aemfd.docmanager.Document;
import com.adobe.fd.docassurance.client.api.DocAssuranceException;
import com.adobe.fd.docassurance.client.api.DocAssuranceService;
import com.adobe.fd.signatures.client.types.FieldMDPAction;
import com.adobe.fd.signatures.client.types.FieldMDPOptionSpec;
import com.adobe.fd.signatures.client.types.MDPPermissions;
import com.adobe.fd.signatures.client.types.PDFSeedValueOptionSpec;
import com.adobe.fd.signatures.client.types.PDFSignatureFieldProperties;
import com.adobe.fd.signatures.client.types.PositionRectangle;
import com.adobe.fd.signatures.client.types.exceptions.DuplicateSignatureFieldException;
import com.adobe.fd.signatures.client.types.exceptions.InvalidArgumentException;
import com.adobe.fd.signatures.client.types.exceptions.MissingSignatureFieldException;
import com.adobe.fd.signatures.client.types.exceptions.PDFOperationException;
import com.adobe.fd.signatures.client.types.exceptions.PermissionsException;
import com.adobe.fd.signatures.client.types.exceptions.SignatureFieldSignedException;
import com.adobe.fd.signatures.client.types.exceptions.SignaturesBaseException;
import com.adobe.fd.signatures.client.types.exceptions.SignaturesOtherException;
import com.adobe.fd.signatures.pdf.inputs.UnlockOptions;

/**
 * You can modify signature fields that are located in a PDF document by using the Java API and web service API. Modifying a signature field involves
 * manipulating its signature field lock dictionary values or seed value dictionary values.
 * A field lock dictionary specifies a list of fields that are locked when the signature field is signed. A locked field prevents users from making
 * changes to the field. A seed value dictionary contains constraining information that is used at the time the signature is applied.
 * For example, you can change permissions that control the actions that can occur without invalidating a signature.
 * By modifying an existing signature field, you can make changes to the PDF document to reflect changing business requirements. For example,
 * a new business requirement may require locking all document fields after the document is signed.
 * This section explains how to modify a signature field by amending both field lock dictionary and seed value dictionary values.
 * Changes made to the signature field lock dictionary result in all fields in the PDF document being locked when a signature field is signed.
 * Changes made to the seed value dictionary prohibit specific types of changes to the document.
 *
 * The following Java code example modifies a signature field named SignatureField1 by locking all fields in the form when a signature is applied to the signature field and ensuring that no changes are allowed.
 * After the Signature service returns the PDF document that contains the modified signature field
 */

@Component
@Service(value=ModifySignatureField.class)
public class ModifySignatureField {

 @Reference
 private DocAssuranceService docAssuranceService;

 /**
  *
  * @param inputFile - path to the pdf document stored at disk
  * @param outFile - path where the output file has to be saved
  *
  *
  */
 public void modifySignatureField(String inputFile, String outFile) throws Exception {

  File inFile = new File(inputFile);
  Document inDoc = new Document(inFile);

  //Specify the name of the signature field
        String fieldName = "SignatureField1";

        //Create a PDFSignatureFieldProperties
        PDFSignatureFieldProperties fieldProperties = new PDFSignatureFieldProperties();

         //Create a PDFSeedValueOptionSpec object that stores
         //seed value dictionary information.
         PDFSeedValueOptionSpec seedOptionsSpec = new PDFSeedValueOptionSpec();

         //Disallow changes to the PDF document. Any change to the document invalidates
         //the signature
         seedOptionsSpec.setMdpValue(MDPPermissions.NoChanges);

         //Create a FieldMDPOptionSpec object that stores
         //signature field lock dictionary information.
         FieldMDPOptionSpec fieldMDPOptionsSpec = new FieldMDPOptionSpec();

         //Lock all fields in the PDF document
         fieldMDPOptionsSpec.setAction(FieldMDPAction.ALL);

         //Set dictionary information
         fieldProperties.setSeedValue(seedOptionsSpec);
         fieldProperties.setFieldMDP(fieldMDPOptionsSpec);

         //Modify the signature field
         //for encrypted document pass Unlock Options - see the method getUnlockOptions() below
         Document modSignatureField =  docAssuranceService.modifySignatureField(inDoc,fieldName,fieldProperties,null);

        //save the modSignatureField
         modSignatureField.copyToFile(new File(outFile));
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
}
```

### PDF-documenten certificeren {#certifying-pdf-documents-nbsp}

U kunt een PDF-document beveiligen door het te certificeren met een bepaald type handtekening, een zogenaamde gecertificeerde handtekening. Een gecertificeerde handtekening wordt op de volgende manieren onderscheiden van een digitale handtekening:

* Dit moet de eerste handtekening zijn die op het PDF-document wordt toegepast. Met andere woorden, wanneer de gecertificeerde handtekening wordt toegepast, moeten andere handtekeningvelden in het document niet-ondertekend zijn. Er is slechts één gecertificeerde handtekening toegestaan in een PDF-document. Als u een PDF-document wilt ondertekenen en certificeren, moet u het certificeren voordat u het ondertekent. Nadat u een PDF-document hebt gecertificeerd, kunt u digitale extra handtekeningvelden ondertekenen.
* De auteur of maker van het document kan opgeven dat het document op bepaalde manieren kan worden gewijzigd zonder de gecertificeerde handtekening ongeldig te maken. Het document kan bijvoorbeeld het invullen van formulieren of het plaatsen van opmerkingen toestaan. Als de auteur aangeeft dat een bepaalde wijziging niet is toegestaan, beperkt Acrobat gebruikers om het document op die manier te wijzigen. Als dergelijke wijzigingen worden aangebracht, is de gecertificeerde handtekening ongeldig. Bovendien wordt in Acrobat een waarschuwing weergegeven wanneer een gebruiker het document opent. (Bij niet-gecertificeerde handtekeningen zijn wijzigingen niet mogelijk en maken normale bewerkingsbewerkingen de oorspronkelijke handtekening niet ongeldig.)
* Op het moment van ondertekening wordt het document gescand op specifieke typen inhoud die de inhoud van een document dubbelzinnig of misleidend kunnen maken. Een annotatie kan bijvoorbeeld bepaalde tekst op een pagina verbergen die belangrijk is voor het begrijpen van wat wordt gecertificeerd. Over deze inhoud kan een toelichting (wettelijke verklaring) worden gegeven.

**Syntaxis**:

```
secureDocument(Document inDoc, EncryptionOptions encryptionOptions,
 SignatureOptions signatureOptions, ReaderExtensionOptions readerExtensionOptions, UnlockOptions unlockOptions)
```

**Invoerparameters**

<table>
 <tbody>
  <tr>
   <th>Parameters</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td><code>inDoc</code> </td>
   <td>PDF-document voor documentinvoer<br /> </td>
  </tr>
  <tr>
   <td><code>encryptionOptions</code> </td>
   <td>Bevat de argumenten die vereist zijn voor het versleutelen van een PDF-document<br /> </td>
  </tr>
  <tr>
   <td><code>signatureOptions</code></td>
   <td>Bevat de opties die vereist zijn voor het ondertekenen/certificeren van een PDF-document</td>
  </tr>
  <tr>
   <td><code>readerExtensionOptions</code></td>
   <td>Bevat de opties die vereist zijn voor Reader Extended van een PDF-document</td>
  </tr>
  <tr>
   <td><code>unlockOptions</code></td>
   <td>Bevat de parameters die vereist zijn om een gecodeerd bestand te ontgrendelen. Dit is alleen vereist als het bestand gecodeerd is.<br /> </td>
  </tr>
 </tbody>
</table>

In het volgende codevoorbeeld wordt een PDF-document gecertificeerd dat is gebaseerd op een PDF-bestand.

```java
/*************************************************************************

-------------------------------------------------------------
*ADOBE SYSTEMS INCORPORATED
*Copyright 2014 Adobe Systems Incorporated
*All Rights Reserved.

*NOTICE:  Adobe permits you to use, modify, and distribute this file in accordance with the
*terms of the Adobe license agreement accompanying it.  If you have received this file from a
*source other than Adobe, then your use, modification, or distribution of it requires the prior
*written permission of Adobe.
-------------------------------------------------------------------------------------------------

 **************************************************************************/
package com.adobe.docassurance.samples;

import java.io.File;
import java.io.IOException;

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
import com.adobe.fd.signatures.client.types.MDPPermissions;
import com.adobe.fd.signatures.client.types.exceptions.InvalidArgumentException;
import com.adobe.fd.signatures.pdf.inputs.CredentialContext;
import com.adobe.fd.signatures.pdf.inputs.DSSPreferences;
import com.adobe.fd.signatures.pdf.inputs.DSSPreferencesImpl;
import com.adobe.fd.signatures.pdf.inputs.PDFSignatureAppearenceOptions;
import com.adobe.fd.signatures.pdf.inputs.PDFSignatureAppearenceOptions.PDFSignatureAppearanceType;
import com.adobe.fd.signatures.pdf.inputs.PDFSignatureAppearenceOptions.TextDirection;
import com.adobe.fd.signatures.pdf.inputs.UnlockOptions;
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
 * You can secure a PDF document by certifying it with a particular type of signature called a certified signature.
 * A certified signature is distinguished from a digital signature in these ways:
 *
 * It must be the first signature applied to the PDF document; that is, at the time the certified signature is applied, any other signature fields in the document must be unsigned.
 * Only one certified signature is permitted in a PDF document. If you want to sign and certify a PDF document, you must certify it before signing it.
 * After you certify a PDF document, you can digitally sign additional signature fields.
 *
 * The author or originator of the document can specify that the document can be modified in certain ways without invalidating the certified signature. For example,
 * the document may permit filling in forms or commenting. If the author specifies that a certain modification is not permitted, Acrobat restricts users from modifying the document
 * in that way. If such modifications are made, such as by using another application, the certified signature is invalid and Acrobat issues a warning when a user opens the document.
 * (With non-certified signatures, modifications are not prevented, and normal editing operations do not invalidate the original signature.)
 *
 * At the time of signing, the document is scanned for specific types of content that could make the contents of a document ambiguous or misleading. For example, an annotation could
 * obscure some text on a page that is important for understanding what is being certified. An explanation (legal attestation) can be provided about such content.
 * You can programmatically certify PDF documents by using the Signature service Java API or the Signature web service API. When certifying a PDF document, you must reference a security
 * credential that exists in the Credential service.
 *
 * Note: When certifying and signing the same PDF document, if the certify signature is not trusted, a yellow triangle appears next to the first sign signature when you open the PDF document in Acrobat or Adobe Reader.
 * The certifying signature must be trusted to avoid this situation.
 *
 * The following Java code example certifies a PDF document that is based on a PDF file.
 *
 * PreRequisites - Digital certificate for certifying the document has to be uploaded on AEM Key Store.
 *
 */

@Component
@Service(value=Certify.class)
public class Certify {

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
 public void certify(String inputFile, String outputFile) throws IOException, RepositoryException, InvalidArgumentException, DocAssuranceException{

  File inFile = new File(inputFile);
  Document inDoc = new Document(inFile);

  File outFile = new File(outputFile);
  Document outDoc = null;

  Session adminSession = null;
        ResourceResolver resourceResolver = null;
        try {

          /** resourceResolver to be passed to SignatureServiceAPI and Reader Extensions
          the resource resolver for signature options has to be corresponding to the user who has the signing certificate in his granite key store
          the resource resolver for signature options has to be corresponding to the user who has the credential for reader extension in his granite key store
          here we are using the same resource resolver
          */
          adminSession = slingRepository.loginAdministrative(null);
             resourceResolver = jcrResourceResolverFactory.getResourceResolver(adminSession);

             //retrieve specifications for each of the services, you may pass null if you don't want to use that service
             //we are not extending the reader in this case, so passing null
             //for encrypted document pass Unlock Options - see the method getUnlockOptions() below
    try {
    outDoc = docAssuranceService.secureDocument(inDoc, null, getCertificationOptions(resourceResolver), null,null);
   } catch (Exception e) {
    // TODO Auto-generated catch block
    e.printStackTrace();
   }

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

        outDoc.copyToFile(outFile);

 }

 /**
  *
  * @param rr resource resolver corresponding to the user with the access to signing credential for the
  * given alias "allcertificatesanypolicytest11ee_new" in this case
  * @return SignatureOptions
  */
 private SignatureOptions getCertificationOptions(ResourceResolver rr){

  //create an instance of SignatureOptions
  SignatureOptions signatureOptions = SignatureOptions.getInstance();

  //set the operation you want to perform - SIGN/CERTIFY
  signatureOptions.setOperationType(DocAssuranceServiceOperationTypes.CERTIFY);

  //signature field to certify, pass null if invisible signature field
  String fieldName = "Signature1" ;

  //alias of the private credential uploaded on the Key Store
        String alias = "allcertificatesanypolicytest11ee_new";

        //Hash Algo to be used to compute digest the PDF document
        HashAlgorithm algo = HashAlgorithm.SHA256;

        //Reason for signing/certifying
        String reason = "Reason";

        //location of the signer
        String location = "Location";

        //contact info of the signer
        String contactInfo = "Contact Info";

        //DocMDP Permissions associated with certification
        MDPPermissions mdpPermissions = MDPPermissions.valueOf("FormChanges");

        //Create a PDFSignatureAppearanceOptions object
        //and show date information
        PDFSignatureAppearenceOptions appOptions = new PDFSignatureAppearenceOptions(
                PDFSignatureAppearanceType.NAME, null, 1.0d, null, true, true,
                true, true, false, true, true, TextDirection.AUTO);
        signatureOptions.setLockCertifyingField(true);
        signatureOptions.setSignatureFieldName(fieldName);
        signatureOptions.setAlgo(algo);
        signatureOptions.setContactInfo(contactInfo);
        signatureOptions.setLocation(location);
        signatureOptions.setSigAppearence(appOptions);
        signatureOptions.setReason(reason);
        signatureOptions.setDssPref(getDSSPreferences(rr));
        signatureOptions.setCredential(new CredentialContext(alias, rr));
        signatureOptions.setMdpPermissions(mdpPermissions);
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

}
```

### Documenten beveiligen {#securing-documents}

Met SecureDocument kunt u een PDF-document versleutelen, ondertekenen/certificeren en in een bepaalde volgorde uitbreiden, afzonderlijk of in een willekeurige combinatie. Om tot om het even welk van deze functionaliteit toegang te hebben, ga het overeenkomstige argument over. Indien null, wordt aangenomen dat de specifieke verwerking niet vereist is.

**PDF-documenten versleutelen met een wachtwoord**

Wanneer u een PDF-document versleutelt met een wachtwoord, moet de gebruiker het wachtwoord opgeven om het PDF-document te openen in Adobe Reader of Acrobat. Voordat het document door een andere bewerking in AEM Forms Document Services wordt gebruikt, moet een PDF-document met een wachtwoord worden ontgrendeld.

**PDF-documenten versleutelen met certificaten**

Met codering op basis van certificaten kunt u een document coderen voor specifieke ontvangers met behulp van technologie voor openbare sleutels.

Verschillende ontvangers kunnen verschillende machtigingen voor het document krijgen. Veel aspecten van versleuteling worden mogelijk gemaakt door de technologie van de openbare sleutel.

Een algoritme wordt gebruikt om twee grote aantallen te produceren, die als sleutels worden bekend die de volgende eigenschappen hebben:

* Eén sleutel wordt gebruikt om een set gegevens te coderen. Later, slechts kan de andere sleutel worden gebruikt om de gegevens te decrypteren.
* Het is onmogelijk om de ene sleutel van de andere te onderscheiden.
* Een van de toetsen fungeert als de persoonlijke sleutel van een gebruiker. Het is belangrijk dat alleen de gebruiker toegang heeft tot deze sleutel.
* De andere sleutel is de openbare sleutel van de gebruiker, die met anderen kan worden gedeeld.

Een certificaat met een openbare sleutel bevat de openbare sleutel van een gebruiker en identificeert informatie. De indeling X.509 wordt gebruikt voor het opslaan van certificaten. Certificaten worden doorgaans uitgegeven en digitaal ondertekend door een certificeringsinstantie (CA), een erkende entiteit die een zekere mate van vertrouwen biedt in de geldigheid van het certificaat. Certificaten hebben een vervaldatum waarna ze niet meer geldig zijn.

Bovendien bevatten de certificaatintrekkingslijsten (CRL&#39;s) informatie over certificaten die vóór de vervaldatum zijn ingetrokken. CRL&#39;s worden periodiek gepubliceerd door certificeringsinstanties. De intrekkingsstatus van een certificaat kan ook via het online certificaatstatusprotocol (OCSP) via het netwerk worden opgehaald.

>[!NOTE]
>
>Voordat u een PDF-document kunt versleutelen met een certificaat, moet u ervoor zorgen dat u het certificaat toevoegt aan de AEM Trust Store.

**Gebruiksrechten toepassen op PDF-documenten**

U kunt gebruiksrechten toepassen op PDF-documenten met de Java Client API en webservice van Reader Extensions. Gebruiksrechten hebben betrekking op functionaliteit die standaard beschikbaar is in Acrobat, maar niet in Adobe Reader, zoals de mogelijkheid om opmerkingen toe te voegen aan een formulier of formuliervelden in te vullen en het formulier op te slaan. PDF-documenten waarop gebruiksrechten zijn toegepast, worden documenten met ingeschakelde rechten genoemd. Een gebruiker die een document met ingeschakelde rechten opent in Adobe Reader, kan bewerkingen uitvoeren die zijn ingeschakeld voor dat specifieke document.

Voordat u Reader kunt gebruiken om een PDF-document met een certificaat uit te breiden, moet u ervoor zorgen dat u het certificaat toevoegt aan het AEM-sleutelarchief.

**PDF-documenten digitaal ondertekenen**

Digitale handtekeningen kunnen op PDF-documenten worden toegepast om een beveiligingsniveau te bieden. Digitale handtekeningen bieden, net als handgeschreven handtekeningen, een manier waarop ondertekenaars zichzelf identificeren en instructies over een document maken.

De technologie die wordt gebruikt om documenten digitaal te ondertekenen, helpt ervoor te zorgen dat zowel de ondertekenaar als de ontvangers duidelijk zijn over wat is ondertekend en er zeker van zijn dat het document niet is gewijzigd sinds het werd ondertekend.

PDF-documenten worden ondertekend met behulp van openbare-sleuteltechnologie. Een ondertekenaar heeft twee toetsen: een openbare sleutel en een persoonlijke sleutel. De persoonlijke sleutel wordt opgeslagen in de referentie van een gebruiker die beschikbaar moet zijn op het moment van ondertekening.

De openbare sleutel wordt opgeslagen in het certificaat van de gebruiker dat beschikbaar moet zijn aan ontvangers om de handtekening te valideren. Informatie over ingetrokken certificaten vindt u in de certificaatintrekkingslijsten (CRL&#39;s) en de online certificaatstatusprotocollen (OCSP&#39;s) die door de certificeringsinstanties (CA&#39;s) worden verspreid. De tijd van het ondertekenen kan van een vertrouwde op bron worden verkregen die als Tijdstempelinstantie wordt bekend.

>[!NOTE]
>
>Voordat u een PDF-document digitaal kunt ondertekenen, moet u ervoor zorgen dat u de referentie toevoegt in het AEM-sleutelarchief. De referentie is de persoonlijke sleutel die wordt gebruikt voor ondertekening.

>[!NOTE]
>
>AEM Forms ondersteunt ook *[CAdES](https://en.wikipedia.org/wiki/CAdES_%28computing%29)*-specificaties voor het digitaal ondertekenen van PDF-documenten.

**PDF-documenten certificeren**

U kunt een PDF-document beveiligen door het te certificeren met een bepaald type handtekening, een zogenaamde gecertificeerde handtekening. Een gecertificeerde handtekening wordt op de volgende manieren onderscheiden van een digitale handtekening:

Dit moet de eerste handtekening zijn die op het PDF-document wordt toegepast. Dit betekent dat op het moment dat de gecertificeerde handtekening wordt toegepast, alle andere handtekeningvelden in het document niet-ondertekend moeten zijn.

Er is slechts één gecertificeerde handtekening toegestaan in een PDF-document. Als u een PDF-document wilt ondertekenen en certificeren, moet u het certificeren voordat u het ondertekent.

Nadat u een PDF-document hebt gecertificeerd, kunt u digitale extra handtekeningvelden ondertekenen.

De auteur of maker van het document kan opgeven dat het document op bepaalde manieren kan worden gewijzigd zonder de gecertificeerde handtekening ongeldig te maken.

Het document kan bijvoorbeeld het invullen van formulieren of het plaatsen van opmerkingen toestaan. Als de auteur aangeeft dat een bepaalde wijziging niet is toegestaan,

Acrobat beperkt gebruikers om het document op die manier te wijzigen. Als dergelijke wijzigingen worden aangebracht, bijvoorbeeld door een andere toepassing te gebruiken, is de gecertificeerde handtekening ongeldig en geeft Acrobat een waarschuwing wanneer een gebruiker het document opent. (Bij niet-gecertificeerde handtekeningen zijn wijzigingen niet mogelijk en maken normale bewerkingsbewerkingen de oorspronkelijke handtekening niet ongeldig.)

Op het moment van ondertekening wordt het document gescand op specifieke typen inhoud die de inhoud van een document dubbelzinnig of misleidend kunnen maken.

Een annotatie kan bijvoorbeeld bepaalde tekst op een pagina verbergen die belangrijk is voor het begrijpen van wat wordt gecertificeerd. Over deze inhoud kan een toelichting (wettelijke verklaring) worden gegeven.

>[!NOTE]
>
>Voordat u een PDF-document digitaal kunt ondertekenen, moet u ervoor zorgen dat u de referentie toevoegt in het AEM-sleutelarchief. De referentie is de persoonlijke sleutel die wordt gebruikt voor ondertekening.

**Syntaxis**:

```
secureDocument(Document inDoc,
 EncryptionOptions encryptionOptions,
 SignatureOptions signatureOptions,
 ReaderExtensionOptions readerExtensionOptions,
 UnlockOptions unlockOptions)
```

**Invoerparameters**

<table>
 <tbody>
  <tr>
   <th>Parameters</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td><code>inDoc</code> </td>
   <td>PDF-document voor documentinvoer<br /> </td>
  </tr>
  <tr>
   <td><code>encryptionOptions</code> </td>
   <td>Bevat de argumenten die vereist zijn voor het versleutelen van een PDF-document<br /> </td>
  </tr>
  <tr>
   <td><code>signatureOptions</code></td>
   <td>Bevat de opties die vereist zijn voor het ondertekenen/certificeren van een PDF-document</td>
  </tr>
  <tr>
   <td><code>readerExtensionOptions</code></td>
   <td>Bevat de opties die vereist zijn voor Reader om een PDF-document uit te breiden</td>
  </tr>
  <tr>
   <td><code>unlockOptions</code></td>
   <td>Bevat de parameters die vereist zijn om een gecodeerd bestand te ontgrendelen. Dit is alleen vereist als het bestand gecodeerd is.<br /> </td>
  </tr>
 </tbody>
</table>

**Voorbeeld 1**: In dit voorbeeld wordt wachtwoordversleuteling uitgevoerd ter certificering van een handtekeningveld en Reader Extending the PDF document.

```
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

import java.io.File;
import java.util.ArrayList;
import java.util.List;

import javax.jcr.Session;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.Service;
import org.apache.sling.api.resource.ResourceResolver;
import org.apache.sling.jcr.api.SlingRepository;
import org.apache.sling.jcr.resource.JcrResourceResolverFactory;

import com.adobe.aemfd.docmanager.Document;
import com.adobe.fd.docassurance.client.api.DocAssuranceService;
import com.adobe.fd.docassurance.client.api.DocAssuranceServiceOperationTypes;
import com.adobe.fd.docassurance.client.api.EncryptionOptions;
import com.adobe.fd.docassurance.client.api.ReaderExtensionOptions;
import com.adobe.fd.docassurance.client.api.SignatureOptions;
import com.adobe.fd.encryption.client.PasswordEncryptionCompatability;
import com.adobe.fd.encryption.client.PasswordEncryptionOption;
import com.adobe.fd.encryption.client.PasswordEncryptionOptionSpec;
import com.adobe.fd.encryption.client.PasswordEncryptionPermission;
import com.adobe.fd.readerextensions.client.ReaderExtensionsOptionSpec;
import com.adobe.fd.readerextensions.client.UsageRights;
import com.adobe.fd.signatures.client.types.MDPPermissions;
import com.adobe.fd.signatures.pdf.inputs.CredentialContext;
import com.adobe.fd.signatures.pdf.inputs.DSSPreferences;
import com.adobe.fd.signatures.pdf.inputs.DSSPreferencesImpl;
import com.adobe.fd.signatures.pdf.inputs.PDFSignatureAppearenceOptions;
import com.adobe.fd.signatures.pdf.inputs.PDFSignatureAppearenceOptions.PDFSignatureAppearanceType;
import com.adobe.fd.signatures.pdf.inputs.PDFSignatureAppearenceOptions.TextDirection;
import com.adobe.fd.signatures.pdf.inputs.UnlockOptions;
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
 *
 * This class provides a sample code to use {@code DocAssuranceService} to carry out
 * password encryption, certifying a signature field and reader extending the pdf document.
 *
 * PreRequisites - Digital certificate for signing the document has to be uploaded on Granite Key Store
 * Digital certificate for reader extending the document has to be uploaded on Granite Key Store
 */

@Component
@Service(value=PassEncryptCertifyExtend.class)
public class PassEncryptCertifyExtend {

 @Reference
 private DocAssuranceService docAssuranceService;

 @Reference
    private SlingRepository slingRepository;

 @Reference
    private JcrResourceResolverFactory jcrResourceResolverFactory ;

 /**
  *
  * @param inputFile - path to the pdf document stored at disk
  * @param outputFile - path to the pdf document where the output needs to be stored
  * @throws Exception
  */
 public void SecureDocument(String inputFile, String outputFile) throws Exception{

  File inFile = new File(inputFile);
  Document inDoc = new Document(inFile);

  File outFile = new File(outputFile);
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
             //for encrypted document pass Unlock Options - see the method getUnlockOptions() below
    outDoc = docAssuranceService.secureDocument(inDoc, getPassEncryptionOptions(), getCertificationOptions(resourceResolver), getReaderExtensionOptions(resourceResolver),null);
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

        outDoc.copyToFile(outFile);

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
  * @return EncryptionOptions for password encrypting the document.
  *
  */
 private EncryptionOptions getPassEncryptionOptions(){

  //Create an instance of EncryptionOptions
  EncryptionOptions encryptionOptions = EncryptionOptions.getInstance();

  //Create a PasswordEncryptionOptionSpec object that stores encryption run-time values
        PasswordEncryptionOptionSpec passSpec = new PasswordEncryptionOptionSpec();

        //Specify the PDF document resource to encrypt
        passSpec.setEncryptOption(PasswordEncryptionOption.ALL);

        //Specify the permission associated with the password
        //These permissions enable data to be extracted from a password
        //protected PDF form
        List<PasswordEncryptionPermission> encrypPermissions = new ArrayList<PasswordEncryptionPermission>();
        encrypPermissions.add(PasswordEncryptionPermission.PASSWORD_EDIT_ADD);
        encrypPermissions.add(PasswordEncryptionPermission.PASSWORD_EDIT_MODIFY);
        passSpec.setPermissionsRequested(encrypPermissions);

        //Specify the Acrobat version
        passSpec.setCompatability(PasswordEncryptionCompatability.ACRO_7);

        //Specify the password values
        passSpec.setDocumentOpenPassword("OpenPassword");
        passSpec.setPermissionPassword("PermissionPassword");

        //Set the encryption type to Password Encryption
  encryptionOptions.setEncryptionType(DocAssuranceServiceOperationTypes.ENCRYPT_WITH_PASSWORD);
        encryptionOptions.setPasswordEncryptionOptionSpec(passSpec);

     return encryptionOptions;
 }

 /**
  *
  * @param resourceResolver corresponding to the user with the access to Reader Extension credential
  * for the given alias -"production" in this case
  * @return
  */
 private ReaderExtensionOptions getReaderExtensionOptions(ResourceResolver resourceResolver){

  //Create an instance of ReaderExtensionOptions
  ReaderExtensionOptions reOptions = ReaderExtensionOptions.getInstance();

  //Create instance for UsageRights to be enabled in the reader
  UsageRights uRights = new UsageRights();
  //enabling comments in the PDF Reader
  uRights.setEnabledComments(true);
  //setting ReaderExtensionsOptionSpec in the reOptions
  reOptions.setReOptions(new ReaderExtensionsOptionSpec(uRights, "Enable commenting in PDF"));
  //alias of the credential to be used for extending the PDF Reader
  reOptions.setCredentialAlias("production");
  //corresponding to the user with the access to Reader Extension credential
  reOptions.setResourceResolver(resourceResolver);

  return reOptions;
 }

 /**
  *
  * @param rr resource resolver corresponding to the user with the access to signing credential for the
  * given alias "allcertificatesanypolicytest11ee_new" in this case
  * @return SignatureOptions
  */
 private SignatureOptions getCertificationOptions(ResourceResolver rr){

  //create an instance of SignatureOptions
  SignatureOptions signatureOptions = SignatureOptions.getInstance();

  //set the operation you want to perform - SIGN/CERTIFY
  signatureOptions.setOperationType(DocAssuranceServiceOperationTypes.CERTIFY);

  //signature field to certify, pass null if invisible signature field
  String fieldName = "Signature1" ;

  //alias of the private credential uploaded on the Key Store
        String alias = "allcertificatesanypolicytest11ee_new";

        //Hash Algo to be used to compute digest the PDF document
        HashAlgorithm algo = HashAlgorithm.SHA384;

        //Reason for signing/certifying
        String reason = "Test Reason";

        //location of the signer
        String location = "Test Location";

        //contact info of the signer
        String contactInfo = "Test Contact";

        //DocMDP Permissions associated with certification
        MDPPermissions mdpPermissions = MDPPermissions.valueOf("FormChanges");

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
        signatureOptions.setCredential(new CredentialContext(alias, rr));
        signatureOptions.setMdpPermissions(mdpPermissions);
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

}
```

**Voorbeeld 2**: Dit voorbeeld wordt gebruikt voor het uitvoeren van PKI-versleuteling, het ondertekenen van een handtekeningveld en Reader Extending the PDF document.

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
import java.io.File;
import java.io.IOException;
import java.io.InputStream;
import java.util.ArrayList;
import java.util.List;

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
import com.adobe.fd.docassurance.client.api.EncryptionOptions;
import com.adobe.fd.docassurance.client.api.ReaderExtensionOptions;
import com.adobe.fd.docassurance.client.api.SignatureOptions;
import com.adobe.fd.encryption.client.CertificateEncryptionCompatibility;
import com.adobe.fd.encryption.client.CertificateEncryptionIdentity;
import com.adobe.fd.encryption.client.CertificateEncryptionOption;
import com.adobe.fd.encryption.client.CertificateEncryptionOptionSpec;
import com.adobe.fd.encryption.client.CertificateEncryptionPermissions;
import com.adobe.fd.encryption.client.Recipient;
import com.adobe.fd.readerextensions.client.ReaderExtensionsOptionSpec;
import com.adobe.fd.readerextensions.client.UsageRights;
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
 *
 * This class provides a sample code to use {@code DocAssuranceService} to carry out
 * certificate encryption, signing a signature field and reader extending the pdf document.
 *
 * PreRequisites - Digital certificate for encrypting the document has to be uploaded on Granite Trust Store
       Digital certificate for signing the document has to be uploaded on Granite Key Store
 * Digital certificate for reader extending the document has to be uploaded on Granite Key Store
 */

@Component
@Service(value=PassEncryptSignExtend.class)
public class PassEncryptSignExtend {

 @Reference
 private DocAssuranceService docAssuranceService;

 @Reference
    private SlingRepository slingRepository;

 @Reference
    private JcrResourceResolverFactory jcrResourceResolverFactory ;

 /**
  *
  * @param inputFile - path to the pdf document stored at disk
  * @param outputFile - path to the pdf document where the output needs to be stored
  * @throws Exception
  */
 public void CertEncryptSignReaderExtend(String inputFile, String outputFile) throws Exception{

  File inFile = new File(inputFile);
  Document inDoc = new Document(inFile);

  File outFile = new File(outputFile);
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
             //for encrypted document pass Unlock Options - see the method getUnlockOptions() below
    outDoc = docAssuranceService.secureDocument(inDoc, getCertEncryptionOptions(), getSignatureOptions(resourceResolver), getReaderExtensionOptions(resourceResolver),null);
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

        outDoc.copyToFile(outFile);

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
  * @return EncryptionOptions for password encrypting the document.
  *
  */
 private EncryptionOptions getCertEncryptionOptions(){

  //Create an instance of EncryptionOptions
  EncryptionOptions encryptionOptions = EncryptionOptions.getInstance();

        //Set the encryption type to Certificate Encryption
  encryptionOptions.setEncryptionType(DocAssuranceServiceOperationTypes.ENCRYPT_WITH_CERTIFCATE);

  //Set the List that stores PKI information
  List<CertificateEncryptionIdentity> pkiIdentities = new ArrayList<CertificateEncryptionIdentity>();

  //Set the Permission List
  List<CertificateEncryptionPermissions> permList = new ArrayList<CertificateEncryptionPermissions>();
  permList.add(CertificateEncryptionPermissions.PKI_ALL_PERM) ;

  //Create a Recipient object to store certificate information
  Recipient recipient = new Recipient();

  //Specify the alias of the public certificate present in the trust store that is used to encrypt the document
  recipient.setX509Cert("alias");
  /*
   * An alternative to add a certificate is by providing the alias
   * of the certificate stored in AEM trust store.
   * recipient.setAlias(alias);
   */

  //Create an EncryptionIdentity object
  CertificateEncryptionIdentity encryptionId = new CertificateEncryptionIdentity();
  encryptionId.setPerms(permList);
  encryptionId.setRecipient(recipient);

  //Add the EncryptionIdentity to the list
  pkiIdentities.add(encryptionId);

  //Set encryption run-time options
  CertificateEncryptionOptionSpec certOptionsSpec = new CertificateEncryptionOptionSpec();
  certOptionsSpec.setOption(CertificateEncryptionOption.ALL);
  certOptionsSpec.setCompat(CertificateEncryptionCompatibility.ACRO_9);

  //Set the certificate encryption option
  encryptionOptions.setCertOptionSpec(certOptionsSpec)

  //Set the PKI Identities in encryption Options
        encryptionOptions.setPkiIdentities(pkiIdentities);

     return encryptionOptions;
 }

 /**
  *
  * @param resourceResolver corresponding to the user with the access to Reader Extension credential
  * for the given alias -"production" in this case
  * @return
  */
 private ReaderExtensionOptions getReaderExtensionOptions(ResourceResolver resourceResolver){

  //Create an instance of ReaderExtensionOptions
  ReaderExtensionOptions reOptions = ReaderExtensionOptions.getInstance();

  //Create instance for UsageRights to be enabled in the reader
  UsageRights uRights = new UsageRights();
  //enabling comments in the PDF Reader
  uRights.setEnabledComments(true);
  //setting ReaderExtensionsOptionSpec in the reOptions
  reOptions.setReOptions(new ReaderExtensionsOptionSpec(uRights, "Enable commenting in PDF"));
  //alias of the credential to be used for extending the PDF Reader
  reOptions.setCredentialAlias("production");
  //corresponding to the user with the access to Reader Extension credential
  reOptions.setResourceResolver(resourceResolver);

  return reOptions;
 }

 /**
  *
  * @param rr resource resolver corresponding to the user with the access to signing credential for the
  * given alias "allcertificatesanypolicytest11ee_new" in this case
  * @return SignatureOptions
  */
 private SignatureOptions getSignatureOptions(ResourceResolver rr){

  //create an instance of SignatureOptions
  SignatureOptions signatureOptions = SignatureOptions.getInstance();

  //set the operation you want to perform - SIGN/CERTIFY
  signatureOptions.setOperationType(DocAssuranceServiceOperationTypes.SIGN);

  //field to sign
  String fieldName = "Signature1" ;

  //alias of the private credential uploaded on the Key Store
        String alias = "allcertificatesanypolicytest11ee_new";

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
        signatureOptions.setCredential(new CredentialContext(alias, rr));
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

}
```

Als het volgende foutbericht wordt weergegeven tijdens het uitbreiden van een PDF-document door een lezer:

```xml
org.apache.sling.engine.impl.SlingRequestProcessorImpl service: Uncaught Throwable java.lang.ThreadDeath: null at com.adobe.internal.pdftoolkit.services.javascript.GibsonContextFactory.observeInstructionCount(GibsonContextFactory.java:138)
```

Dit betekent dat de Reader Extension-service de JavaScripts die in het document worden gebruikt, niet kan uitvoeren binnen het gedefinieerde time-outinterval.

Het time-outinterval dat is gedefinieerd voor de JavaScripts in het PDF-document, beheren met:

```xml
ReaderExtensionsOptionSpec optionSpec = new ReaderExtensionsOptionSpec(usageRights, message);
optionSpec.setJsScriptExecutionTimeoutInterval(100);
```

waarbij 100 verwijst naar het time-outinterval dat is gedefinieerd voor de uitvoering van JavaScripts (in seconden). Stel de juiste waarde in voor het time-outinterval.

### Rechten voor gebruik van referenties ophalen {#getting-credential-usage-rights}

Als u informatie over gebruiksrechten wilt ophalen van de referentie die door de opgegeven gegevens is opgegeven, roept u deze API aan vanuit de `credentialAlias``SecureDocument` API.

**Syntaxis**: `getCredentialUsageRights(String credentialAlias, ResourceResolver resourceResolver)`

**Invoerparameters**

<table>
 <tbody>
  <tr>
   <th>Parameters</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td><code>credentialAlias</code> </td>
   <td>De <code>credentialAlias</code> waarde die de referentie opgeeft.<br /> </td>
  </tr>
  <tr>
   <td><code>credentialPassword</code> </td>
   <td>Het wachtwoord van de referentie als de referentie gecodeerd is, null moet worden gebruikt als de referentie niet gecodeerd is.<br /> </td>
  </tr>
 </tbody>
</table>

In het volgende voorbeeld wordt informatie over gebruiksrechten opgehaald voor de opgegeven referentie.

```java
/*************************************************************************
 *
 * ADOBE CONFIDENTIAL
 * __________________
 *
 * Copyright 2014 Adobe Systems Incorporated
 * All Rights Reserved.
 *
 * NOTICE:  All information contained herein is, and remains
 * the property of Adobe Systems Incorporated and its suppliers,
 * if any.  The intellectual and technical concepts contained
 * herein are proprietary to Adobe Systems Incorporated and its
 * suppliers and may be covered by U.S. and Foreign Patents,
 * patents in process, and are protected by trade secret or copyright law.
 * Dissemination of this information or reproduction of this material
 * is strictly forbidden unless prior written permission is obtained
 * from Adobe Systems Incorporated.
 **************************************************************************/
package com.adobe.fd.readerextensions.samples;

import java.io.File;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.Service;
import org.apache.sling.api.resource.ResourceResolverFactory;

import com.adobe.aemfd.docmanager.Document;
import com.adobe.fd.docassurance.client.api.DocAssuranceService;
import com.adobe.fd.docassurance.client.api.ReaderExtensionOptions;
import com.adobe.fd.readerextensions.client.GetUsageRightsResult;
import com.adobe.fd.readerextensions.client.ReaderExtensionsOptionSpec;
import com.adobe.fd.readerextensions.client.UsageRights;
import com.adobe.fd.signatures.pdf.inputs.UnlockOptions;

/**
 *
 */
@Component(metatype = true, immediate = true, label = "ReaderExtensionsSampleService")
@Service(value = ReaderExtensionsSampleService.class)
public class ReaderExtensionsSampleService {

 @Reference(referenceInterface=DocAssuranceService.class)
 private DocAssuranceService docAssuranceService;

 @Reference(referenceInterface=ResourceResolverFactory.class)
 private ResourceResolverFactory resourceResolverFactory;
public void getCredentialUsageRights() {
  try {

   GetUsageRightsResult usageRightsResult = docAssuranceService.getCredentialUsageRights("production",
     resourceResolverFactory.getAdministrativeResourceResolver(null));

   System.out.println("Credential usage Rights are as follows");
   System.out.println(usageRightsResult.toString());

  } catch (Exception e) {
   e.printStackTrace();
  }
 }
}
```

### Rechten voor documentgebruik ophalen {#getting-document-usage-rights}

Als u informatie over gebruiksrechten voor een bepaald document wilt ophalen, roept u deze API aan vanuit de `docAssuranceService`API.

**Syntaxis**: `getDocumentUsageRights(Document inDocument, UnlockOptions unlockOptions)`

**Invoerparameters**

<table>
 <tbody>
  <tr>
   <th>Parameters</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td><code>inDocument</code> </td>
   <td>Het document waarin gebruiksrechtengegevens moeten worden opgehaald van<br /> </td>
  </tr>
 </tbody>
</table>

Deze volgende voorbeeldcode retourneert de gebruiksrechteninformatie voor een document.

```java
/*************************************************************************
 *
 * ADOBE CONFIDENTIAL
 * __________________
 *
 * Copyright 2014 Adobe Systems Incorporated
 * All Rights Reserved.
 *
 * NOTICE:  All information contained herein is, and remains
 * the property of Adobe Systems Incorporated and its suppliers,
 * if any.  The intellectual and technical concepts contained
 * herein are proprietary to Adobe Systems Incorporated and its
 * suppliers and may be covered by U.S. and Foreign Patents,
 * patents in process, and are protected by trade secret or copyright law.
 * Dissemination of this information or reproduction of this material
 * is strictly forbidden unless prior written permission is obtained
 * from Adobe Systems Incorporated.
 **************************************************************************/
package com.adobe.fd.readerextensions.samples;

import java.io.File;
import java.util.HashMap;
import java.util.Map;

import javax.jcr.SimpleCredentials;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.Service;
import org.apache.sling.api.resource.LoginException;
import org.apache.sling.api.resource.ResourceResolver;
import org.apache.sling.api.resource.ResourceResolverFactory;
import org.apache.sling.jcr.resource.JcrResourceConstants;

import com.adobe.aemfd.docmanager.Document;
import com.adobe.fd.docassurance.client.api.DocAssuranceService;
import com.adobe.fd.docassurance.client.api.ReaderExtensionOptions;
import com.adobe.fd.readerextensions.client.GetUsageRightsResult;
import com.adobe.fd.readerextensions.client.ReaderExtensionsOptionSpec;
import com.adobe.fd.readerextensions.client.UsageRights;
import com.adobe.fd.signatures.pdf.inputs.UnlockOptions;

@Component(metatype = true, immediate = true, label = "ReaderExtensionsSampleService")
@Service(value = ReaderExtensionsSampleService.class)
public class ReaderExtensionsSampleService {

 @Reference(referenceInterface=DocAssuranceService.class)
 private DocAssuranceService docAssuranceService;

 @Reference(referenceInterface=ResourceResolverFactory.class)
private ResourceResolverFactory resourceResolverFactory;

public void getDocumentUsageRights() {
  Document inputDocument = null;
  try {
   //Name of the input file on which usage rights is to be applied.
   String inputFileName = "C:/RETest/input/GetUsageRightsInfo/02_fromAcrobat7.0.8_Acro700_UB8_BS_signed_commenting.pdf";

   //Document to be input to Doc Assurance Service
   inputDocument = new Document(new File(inputFileName));

   //Unlock options to unlock the document if some kind of security is set on it.
   //Currently set to null because input document has no security.
   UnlockOptions unlockOptions = null;

   GetUsageRightsResult usageRightsResult = docAssuranceService.getDocumentUsageRights(inputDocument, unlockOptions);

   System.out.println("Document usage Rights are as follows");
   System.out.println(usageRightsResult.toString());

  } catch (Exception e) {
   e.printStackTrace();
  } finally {
//   if (inputDocument != null) {
//    inputDocument.dispose(); //dispose off the document.
//   }
  }
}

/**
  * Resource resolver of the user in whose keystore Reader Extensions Certificate is installed.
  * @param resourceResolverFactory
  * @return
  * @throws LoginException
  */
 public ResourceResolver getResourceResolver() throws LoginException{
  Map<String,Object> authInfo = new HashMap<String,Object>();
  //Username and password of the user in whose keystore Reader Extensions Certificate is installed
  SimpleCredentials credentials = new SimpleCredentials("username"/*UserName*/, "password"/*Password*/.toCharArray());
  authInfo.put(JcrResourceConstants.AUTHENTICATION_INFO_CREDENTIALS,credentials);
  return resourceResolverFactory.getResourceResolver(authInfo);
}

}
```

### Gebruiksrechten verwijderen {#removing-usage-rights}

U kunt de gebruiksrechten voor een document verwijderen door de `removeUsageRights`API vanuit de `docAssuranceService`API aan te roepen.

**Invoerparameters**

<table>
 <tbody>
  <tr>
   <th>Parameters</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td><code>inDocument</code> </td>
   <td>Het document waaruit gebruiksrechten moeten worden verwijderd.<br /> </td>
  </tr>
  <tr>
   <td><code>unlockOptions</code> </td>
   <td>Bevat de parameters die nodig zijn om een gecodeerd bestand te ontgrendelen. Dit is alleen vereist als het bestand is versleuteld.<br /> </td>
  </tr>
 </tbody>
</table>

In het volgende voorbeeld worden de gebruiksrechten voor een bepaald document verwijderd.

```java
/*************************************************************************
 *
 * ADOBE CONFIDENTIAL
 * __________________
 *
 * Copyright 2014 Adobe Systems Incorporated
 * All Rights Reserved.
 *
 * NOTICE:  All information contained herein is, and remains
 * the property of Adobe Systems Incorporated and its suppliers,
 * if any.  The intellectual and technical concepts contained
 * herein are proprietary to Adobe Systems Incorporated and its
 * suppliers and may be covered by U.S. and Foreign Patents,
 * patents in process, and are protected by trade secret or copyright law.
 * Dissemination of this information or reproduction of this material
 * is strictly forbidden unless prior written permission is obtained
 * from Adobe Systems Incorporated.
 **************************************************************************/
package com.adobe.fd.readerextensions.samples;

import java.io.File;
import java.util.HashMap;
import java.util.Map;

import javax.jcr.SimpleCredentials;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.Service;
import org.apache.sling.api.resource.LoginException;
import org.apache.sling.api.resource.ResourceResolver;
import org.apache.sling.api.resource.ResourceResolverFactory;
import org.apache.sling.jcr.resource.JcrResourceConstants;

import com.adobe.aemfd.docmanager.Document;
import com.adobe.fd.docassurance.client.api.DocAssuranceService;
import com.adobe.fd.docassurance.client.api.ReaderExtensionOptions;
import com.adobe.fd.readerextensions.client.GetUsageRightsResult;
import com.adobe.fd.readerextensions.client.ReaderExtensionsOptionSpec;
import com.adobe.fd.readerextensions.client.UsageRights;
import com.adobe.fd.signatures.pdf.inputs.UnlockOptions;

@Component(metatype = true, immediate = true, label = "ReaderExtensionsSampleService")
@Service(value = ReaderExtensionsSampleService.class)
public class ReaderExtensionsSampleService {

 @Reference(referenceInterface=DocAssuranceService.class)
 private DocAssuranceService docAssuranceService;

 @Reference(referenceInterface=ResourceResolverFactory.class)
private ResourceResolverFactory resourceResolverFactory;

public void removeDocumentUsageRights() {
  Document inputDocument = null;
  Document outDocument = null;
  try {
   //Name of the input file on which usage rights is to be applied.
   String inputFileName = "C:/RETest/input/RemoveUsageRights/01_Ubiquitized_50-267_PDF1.5_UB2_Rights.pdf";

   //Name of the output file where result will be saved.
   String outputFileName = "C:/RETest/output/samples/removeUsageRightsOutput.pdf";

   //Document to be input to Doc Assurance Service
   inputDocument = new Document(new File(inputFileName));

   //Unlock options to unlock the document if some kind of security is set on it.
   //Currently set to null because input document has no security.
   UnlockOptions unlockOptions = null;

   //Specify null encryption options and signatures options.
   //If requirement is also to encrypt and sign the document then, corresponding options can also be specified.
   outDocument = docAssuranceService.removeUsageRights(inputDocument, unlockOptions);

   File outputdir = new File("C:/RETest/output/samples");
   outputdir.mkdirs();

   outDocument.copyToFile(new File(outputFileName));
  } catch (Exception e) {
   e.printStackTrace();
  }
}

/**
  * Resource resolver of the user in whose keystore Reader Extensions Certificate is installed.
  * @param resourceResolverFactory
  * @return
  * @throws LoginException
  */
 public ResourceResolver getResourceResolver() throws LoginException{
  Map<String,Object> authInfo = new HashMap<String,Object>();
  //Username and password of the user in whose keystore Reader Extensions Certificate is installed
  SimpleCredentials credentials = new SimpleCredentials("username"/*UserName*/, "password"/*Password*/.toCharArray());
  authInfo.put(JcrResourceConstants.AUTHENTICATION_INFO_CREDENTIALS,credentials);
  return resourceResolverFactory.getResourceResolver(authInfo);
}

}
```

#### Digitale handtekeningen verifiëren {#verifying-digital-signatures}

Digitale handtekeningen kunnen worden geverifieerd om ervoor te zorgen dat een ondertekend PDF-document niet is gewijzigd en dat de digitale handtekening geldig is. Wanneer u een digitale handtekening verifieert, kunt u de status van de handtekening en de eigenschappen van de handtekening controleren, zoals de identiteit van de ondertekenaar. Voordat u een digitale handtekening vertrouwt, is het raadzaam deze te controleren. Wanneer u een digitale handtekening verifieert, verwijst u naar een PDF-document dat een digitale handtekening bevat.

**Syntaxis**: `verify( inDoc, signatureFieldName, revocationCheckStyle, verificationTime, dssPrefs, ResourceResolver resourceResolver)`

**Invoerparameters**

<table>
 <tbody>
  <tr>
   <th>Parameters</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td><code>inDoc</code> </td>
   <td>Document, object dat PDF bevat<br /> </td>
  </tr>
  <tr>
   <td><code class="code">signatureField
      Name</code> </td>
   <td>De naam van het handtekeningveld dat moet worden gevalideerd. volledige of gedeeltelijke naam kan worden gegeven<br /> </td>
  </tr>
  <tr>
   <td><code>revocationCheckStyle</code></td>
   <td>De optie voor het controleren van de intrekking van certificaten die tijdens de validatie zijn aangetroffen</td>
  </tr>
  <tr>
   <td><code>verificationTime</code></td>
   <td>Het tijdstip waarop de handtekening moet worden gevalideerd</td>
  </tr>
  <tr>
   <td><code>dssPrefs</code></td>
   <td>Voorkeuren voor het besturen van verschillende validatieconfiguraties. Voor een versleuteld document stelt u ontgrendelingsopties in met <code>setUnlockOptions()</code></td>
  </tr>
  <tr>
   <td><code>resourceResolver</code></td>
   <td>Resourceoplosser voor de graniet Trust Store</td>
  </tr>
 </tbody>
</table>

Deze voorbeeldcode gebruikt `DocAssuranceService` om een handtekeningveld in een versleuteld PDF-document te verifiëren.

```java
/*************************************************************************
 *
-------------------------------------------------------------
*ADOBE SYSTEMS INCORPORATED
*Copyright 2014 Adobe Systems Incorporated
*All Rights Reserved.

*NOTICE:  Adobe permits you to use, modify, and distribute this file in accordance with the
*terms of the Adobe license agreement accompanying it.  If you have received this file from a
*source other than Adobe, then your use, modification, or distribution of it requires the prior
*written permission of Adobe.
-------------------------------------------------------------------------------------------------

 **************************************************************************/
package com.adobe.docassurance.samples;

import java.io.File;
import java.io.IOException;

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
import com.adobe.fd.signatures.client.types.IdentityInformation;
import com.adobe.fd.signatures.client.types.IdentityStatus;
import com.adobe.fd.signatures.client.types.PDFSignatureType;
import com.adobe.fd.signatures.client.types.PDFSignatureVerificationInfo;
import com.adobe.fd.signatures.client.types.SignatureProperties;
import com.adobe.fd.signatures.client.types.SignatureStatus;
import com.adobe.fd.signatures.client.types.SignatureType;
import com.adobe.fd.signatures.client.types.VerificationTime;
import com.adobe.fd.signatures.client.types.exceptions.InvalidArgumentException;
import com.adobe.fd.signatures.pdf.inputs.UnlockOptions;
import com.adobe.fd.signatures.pdf.inputs.ValidationPreferences;
import com.adobe.fd.signatures.pdf.inputs.ValidationPreferencesImpl;
import com.adobe.fd.signatures.pki.client.types.common.RevocationCheckStyle;
import com.adobe.fd.signatures.pki.client.types.prefs.CRLPreferences;
import com.adobe.fd.signatures.pki.client.types.prefs.CRLPreferencesImpl;
import com.adobe.fd.signatures.pki.client.types.prefs.OCSPPreferencesImpl;
import com.adobe.fd.signatures.pki.client.types.prefs.PKIPreferences;
import com.adobe.fd.signatures.pki.client.types.prefs.PKIPreferencesImpl;
import com.adobe.fd.signatures.pki.client.types.prefs.PathValidationPreferences;
import com.adobe.fd.signatures.pki.client.types.prefs.PathValidationPreferencesImpl;
import com.adobe.fd.signatures.pki.client.types.prefs.TSPPreferences;
import com.adobe.fd.signatures.pki.client.types.prefs.TSPPreferencesImpl;

/**
 *
 * This class provides a sample code to use {@code DocAssuranceService} to carry out
 * verification of a signature field in an already Encrypted PDF Document
 *
 * Digital signatures can be verified to ensure that a signed PDF document was not modified and that the digital signature is valid.
 * When verifying a digital signature, you can check the signature's status and the signature's properties, such as the signer's identity.
 * Before trusting a digital signature, it is recommended that you verify it. When verifying a digital signature, reference a PDF document
 * that contains a digital signature.
 *
 * For unprotected document, you are not required to set UnlockOptions in ValidationPreferences
 * PreRequisites - The certificate chain upto the Root Certificate should be uploaded on CQ trust Store
 */

@Component
@Service(value=VerifyFieldEncryptedPDF.class)
public class VerifyFieldEncryptedPDF {

 @Reference
 private DocAssuranceService docAssuranceService;

 @Reference
    private SlingRepository slingRepository;

 @Reference
    private JcrResourceResolverFactory jcrResourceResolverFactory ;

 /**
  *
  * @param inputFile - path to an encrypted pdf document stored at JCR node
  * @throws IOException
  * @throws RepositoryException
  * @throws InvalidArgumentException
  * @throws DocAssuranceException
  */
 public void verifyFieldEncryptedPDF(String inputFile,String fieldName) throws IOException, RepositoryException, InvalidArgumentException, DocAssuranceException{

  File inFile = new File(inputFile);
  Document inDoc = new Document(inFile);

  Session adminSession = null;
        ResourceResolver resourceResolver = null;
        try {

         //the resource resolver has to be corresponding to the user who has access to CQ Trust Store
          adminSession = slingRepository.loginAdministrative(null);
             resourceResolver = jcrResourceResolverFactory.getResourceResolver(adminSession);

           //Specify the name of the signature field

             RevocationCheckStyle revocationCheckStyle = RevocationCheckStyle.AlwaysCheck;
             VerificationTime verificationTime = VerificationTime.CURRENT_TIME;
             ValidationPreferences dssPrefs = getValidationPreferences();

             //Verify the digital signature
             PDFSignatureVerificationInfo  signInfo = docAssuranceService.verify(
                 inDoc,
                 fieldName,
                 revocationCheckStyle,
                 verificationTime,
                 dssPrefs,
                 resourceResolver);

             //Get the Signature Status
             SignatureStatus sigStatus = signInfo.getStatus();
             String myStatus="";

             //Determine the status of the signature
             if (sigStatus == SignatureStatus.DynamicFormSignatureUnknown)
                 myStatus = "The signatures located in the dynamic PDF form are unknown";
             else if (sigStatus == SignatureStatus.DocumentSignatureUnknown)
                 myStatus = "The signatures located in the PDF document are unknown";
             else if (sigStatus == SignatureStatus.CertifiedDynamicFormSignatureTamper)
                 myStatus = "The signatures located in a certified PDF form are valid";
             else if (sigStatus == SignatureStatus.SignedDynamicFormSignatureTamper)
                 myStatus = "The signatures located in a signed dynamic PDF form are valid";
             else if (sigStatus == SignatureStatus.CertifiedDocumentSignatureTamper)
                 myStatus = "The signatures located in a certified PDF document are valid";
             else if (sigStatus == SignatureStatus.SignedDocumentSignatureTamper)
                 myStatus = "The signatures located in a signed PDF document are valid";
             else if (sigStatus == SignatureStatus.SignatureFormatError)
                 myStatus = "The format of a signature in a signed document is invalid";
             else if (sigStatus == SignatureStatus.DynamicFormSigNoChanges)
                 myStatus = "No changes were made to the signed dynamic PDF form";
             else if (sigStatus == SignatureStatus.DocumentSigNoChanges)
                 myStatus = "No changes were made to the signed PDF document";
             else if (sigStatus == SignatureStatus.DynamicFormCertificationSigNoChanges)
                 myStatus = "No changes were made to the certified dynamic PDF form";
             else if (sigStatus == SignatureStatus.DocumentCertificationSigNoChanges)
                 myStatus = "No changes were made to the certified PDF document";
             else if (sigStatus == SignatureStatus.DocSigWithChanges)
                 myStatus = "There were changes to a signed PDF document";
            else if (sigStatus == SignatureStatus.CertificationSigWithChanges)
                 myStatus = "There were changes made to the PDF document.";

             //Get the signature type
             SignatureType sigType = signInfo.getSignatureType();
             String myType = "";

             if (sigType.getType() == PDFSignatureType.AUTHORSIG)
                    myType="Certification";
             else if(sigType.getType() == PDFSignatureType.RECIPIENTSIG)
                    myType="Recipient";

             //Get the identity of the signer
             IdentityInformation signerId = signInfo.getSigner();
             String signerMsg = "";

            if (signerId.getStatus() == IdentityStatus.UNKNOWN)
                signerMsg = "Identity Unknown";
            else if (signerId.getStatus() == IdentityStatus.TRUSTED)
                signerMsg = "Identity Trusted";
            else if (signerId.getStatus() == IdentityStatus.NOTTRUSTED)
                signerMsg = "Identity Not Trusted";

            //Get the Signature properties returned by the Signature service
            SignatureProperties sigProps = signInfo.getSignatureProps();
            String signerName =  sigProps.getSignerName();

           System.out.println("The status of the signature is: "+myStatus +". The signer identity is "+signerMsg +". The signature type is "+myType +". The name of the signer is "+signerName+".");
           }
           catch (Exception ee)
           {
               ee.printStackTrace();
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

 }

 /**
   * sets ValidationPreferences
   */
  private static ValidationPreferences getValidationPreferences(){

        ValidationPreferencesImpl prefs = new ValidationPreferencesImpl();
        prefs.setPKIPreferences(getPKIPreferences());

        //set the unlock options for processing an encrypted pdf document, do not set if the input doc is unprotected
        prefs.setUnlockOptions(getUnlockOptions());
        return prefs;

    }

  /**
   * sets PKIPreferences
   */
    private static PKIPreferences getPKIPreferences(){
        PKIPreferences pkiPref = new PKIPreferencesImpl();
        pkiPref.setCRLPreferences(getCRLPreferences());
        pkiPref.setPathPreferences(getPathValidationPreferences());
        pkiPref.setOCSPPreferences(getOCSPPref());
        pkiPref.setTSPPreferences(getTspPref());
        return pkiPref;
    }

    private static TSPPreferences getTspPref(){
     TSPPreferencesImpl tsp = new TSPPreferencesImpl();
     tsp.setRevocationCheck(RevocationCheckStyle.BestEffort);
     return tsp;
    }
    private static OCSPPreferencesImpl getOCSPPref(){
     OCSPPreferencesImpl ocsp = new OCSPPreferencesImpl();
     ocsp.setRevocationCheck(RevocationCheckStyle.BestEffort);
     return ocsp;
    }
    /**
     * sets CRL Preferences
     */
    private static CRLPreferences getCRLPreferences(){

        CRLPreferencesImpl crlPrefs = new CRLPreferencesImpl();
        crlPrefs.setRevocationCheck(RevocationCheckStyle.BestEffort);
        crlPrefs.setGoOnline(true);
        return crlPrefs;
    }

    /**
     *
     * sets PathValidationPreferences
     */
    private static PathValidationPreferences getPathValidationPreferences(){
        PathValidationPreferencesImpl pathPref = new PathValidationPreferencesImpl();
        pathPref.setDoValidation(true);
        return pathPref;

    }

    /**
     * sets Unlock Options for encrypted PDF
     */
    private static UnlockOptions getUnlockOptions(){
        UnlockOptions unlockOptions = new UnlockOptions();
        //sets the Open Password for password encrypted PDF
        unlockOptions.setPassword("OpenPassword");

        //for Certificate Encrypted Document, set the alias of the credential uploaded in the user's key store
        //and corresponding resource resolver

        return unlockOptions;

    }

}
```

### Meerdere digitale handtekeningen verifiëren {#verifying-multiple-digital-signatures}

Met AEM kunt u digitale handtekeningen in PDF-documenten verifiëren. Een PDF-document kan meerdere digitale handtekeningen bevatten als het is onderworpen aan een bedrijfsproces waarvoor handtekeningen van meerdere ondertekenaars vereist zijn. Een financiële transactie vereist bijvoorbeeld handtekeningen van zowel de leningfunctionaris als de beheerder. U kunt de API van de handtekeningenservice gebruiken om alle handtekeningen in het PDF-document te verifiëren. Wanneer u meerdere digitale handtekeningen controleert, kunt u de status en eigenschappen van elke handtekening controleren. Voordat u een digitale handtekening vertrouwt, raadt Adobe u aan deze te verifiëren.

**Syntaxis**: `verifyDocument(Document doc, RevocationCheckStyle revocationCheckStyle, VerificationTime verificationTime, ValidationPreferences prefStore, ResourceResolver resourceResolver)`

**Invoerparameters**

<table>
 <tbody>
  <tr>
   <th>Parameters</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td><code>inDoc</code> </td>
   <td>Document, object dat PDF bevat<br /> </td>
  </tr>
  <tr>
   <td><code>revocationCheckStyle</code></td>
   <td>De optie voor het controleren van de intrekking van certificaten die tijdens de validatie zijn aangetroffen</td>
  </tr>
  <tr>
   <td><code>verificationTime</code></td>
   <td>Het tijdstip waarop de handtekening moet worden gevalideerd</td>
  </tr>
  <tr>
   <td><code>dssPrefs</code></td>
   <td>Voorkeuren voor het besturen van verschillende validatieconfiguraties. Voor een versleuteld document stelt u ontgrendelingsopties in met <code>setUnlockOptions()</code></td>
  </tr>
  <tr>
   <td><code>resourceResolver</code></td>
   <td>Resourceoplosser voor de graniet Trust Store</td>
  </tr>
 </tbody>
</table>

De volgende voorbeeldcode gebruikt DocAssuranceService om de handtekeningvelden in een reeds gecodeerd PDF-document te verifiëren.

```java
/*************************************************************************
 *
  *
-------------------------------------------------------------
*ADOBE SYSTEMS INCORPORATED
*Copyright 2014 Adobe Systems Incorporated
*All Rights Reserved.

*NOTICE:  Adobe permits you to use, modify, and distribute this file in accordance with the
*terms of the Adobe license agreement accompanying it.  If you have received this file from a
*source other than Adobe, then your use, modification, or distribution of it requires the prior
*written permission of Adobe.
-------------------------------------------------------------------------------------------------

 **************************************************************************/
package com.adobe.docassurance.samples;

import java.io.File;
import java.io.IOException;
import java.util.Iterator;
import java.util.List;

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
import com.adobe.fd.signatures.client.types.PDFDocumentVerificationInfo;
import com.adobe.fd.signatures.client.types.PDFSignatureType;
import com.adobe.fd.signatures.client.types.PDFSignatureVerificationInfo;
import com.adobe.fd.signatures.client.types.SignatureProperties;
import com.adobe.fd.signatures.client.types.SignatureStatus;
import com.adobe.fd.signatures.client.types.SignatureType;
import com.adobe.fd.signatures.client.types.VerificationTime;
import com.adobe.fd.signatures.client.types.exceptions.InvalidArgumentException;
import com.adobe.fd.signatures.pdf.inputs.UnlockOptions;
import com.adobe.fd.signatures.pdf.inputs.ValidationPreferences;
import com.adobe.fd.signatures.pdf.inputs.ValidationPreferencesImpl;
import com.adobe.fd.signatures.pki.client.types.common.RevocationCheckStyle;
import com.adobe.fd.signatures.pki.client.types.prefs.CRLPreferences;
import com.adobe.fd.signatures.pki.client.types.prefs.CRLPreferencesImpl;
import com.adobe.fd.signatures.pki.client.types.prefs.PKIPreferences;
import com.adobe.fd.signatures.pki.client.types.prefs.PKIPreferencesImpl;
import com.adobe.fd.signatures.pki.client.types.prefs.PathValidationPreferences;
import com.adobe.fd.signatures.pki.client.types.prefs.PathValidationPreferencesImpl;

/**
 *
 * This class provides a sample code to use {@code DocAssuranceService} to carry out
 * verification of all the signature fields in an already Encrypted PDF Document
 *
 * Assume that a PDF document contains multiple digital signatures as a result of a business process that requires signatures from multiple
 * signers. For example, consider a financial transaction that requires both a loan officer's and a manager's signature. You can use the
 * Signature service Java API or web service API to verify all signatures within the PDF document. When verifying multiple digital signatures,
 * you can check the status and properties of each signature. Before you trust a digital signature, it is recommended that you verify it. It
 * is recommended that you are familiar with verifying a single digital signature.
 *
 * For unprotected document, you are not required to set UnlockOptions in ValidationPreferences
 * PreRequisites - The certificate chain upto the Root Certificate should be uploaded on CQ trust Store
 */

@Component
@Service(value=VerifyEncryptedPDFDoc.class)
public class VerifyEncryptedPDFDoc {

 @Reference
 private DocAssuranceService docAssuranceService;

 @Reference
    private SlingRepository slingRepository;

 @Reference
    private JcrResourceResolverFactory jcrResourceResolverFactory ;

 /**
  *
  * @param inputFile - path to an encrypted pdf document stored at JCR node
  * @throws IOException
  * @throws RepositoryException
  * @throws InvalidArgumentException
  * @throws DocAssuranceException
  */
 public void verifyEncryptedPDFDoc(String inputFile) throws IOException, RepositoryException, InvalidArgumentException, DocAssuranceException{

  File inFile = new File(inputFile);
  Document inDoc = new Document(inFile);

  Session adminSession = null;
        ResourceResolver resourceResolver = null;
        try {

          //the resource resolver has to be corresponding to the user who has access to CQ Trust Store
          adminSession = slingRepository.loginAdministrative(null);
             resourceResolver = jcrResourceResolverFactory.getResourceResolver(adminSession);

             RevocationCheckStyle revocationCheckStyle = RevocationCheckStyle.CheckIfAvailable;
             VerificationTime verificationTime = VerificationTime.CURRENT_TIME;
             ValidationPreferences dssPrefs = getValidationPreferences();

             //Verify the digital signature
             PDFDocumentVerificationInfo  docInfo = docAssuranceService.verifyDocument(
                 inDoc,
                 revocationCheckStyle,
                 verificationTime,
                 dssPrefs,
                 resourceResolver);

             //Get a list of all signatures that are located in the PDF document
             List allSignatures = docInfo.getVerificationInfos();

           //Create an Iterator object and iterate through
           //the List object
           Iterator<PDFSignatureVerificationInfo> iter = allSignatures.iterator();

           while (iter.hasNext()) {
                  PDFSignatureVerificationInfo signInfo = (PDFSignatureVerificationInfo)iter.next();

                  //Get the Signature Status
                     SignatureStatus sigStatus = signInfo.getStatus();
                     String myStatus="";

                   //Determine the status of the signature
                     if (sigStatus == SignatureStatus.DynamicFormSignatureUnknown)
                         myStatus = "The signatures located in the dynamic PDF form are unknown";
                     else if (sigStatus == SignatureStatus.DocumentSignatureUnknown)
                         myStatus = "The signatures located in the PDF document are unknown";
                     else if (sigStatus == SignatureStatus.CertifiedDynamicFormSignatureTamper)
                         myStatus = "The signatures located in a certified PDF form are valid";
                     else if (sigStatus == SignatureStatus.SignedDynamicFormSignatureTamper)
                         myStatus = "The signatures located in a signed dynamic PDF form are valid";
                     else if (sigStatus == SignatureStatus.CertifiedDocumentSignatureTamper)
                         myStatus = "The signatures located in a certified PDF document are valid";
                     else if (sigStatus == SignatureStatus.SignedDocumentSignatureTamper)
                         myStatus = "The signatures located in a signed PDF document are valid";
                     else if (sigStatus == SignatureStatus.SignatureFormatError)
                         myStatus = "The format of a signature in a signed document is invalid";
                     else if (sigStatus == SignatureStatus.DynamicFormSigNoChanges)
                         myStatus = "No changes were made to the signed dynamic PDF form";
                     else if (sigStatus == SignatureStatus.DocumentSigNoChanges)
                         myStatus = "No changes were made to the signed PDF document";
                     else if (sigStatus == SignatureStatus.DynamicFormCertificationSigNoChanges)
                         myStatus = "No changes were made to the certified dynamic PDF form";
                     else if (sigStatus == SignatureStatus.DocumentCertificationSigNoChanges)
                         myStatus = "No changes were made to the certified PDF document";
                     else if (sigStatus == SignatureStatus.DocSigWithChanges)
                         myStatus = "There were changes to a signed PDF document";
                    else if (sigStatus == SignatureStatus.CertificationSigWithChanges)
                         myStatus = "There were changes made to the PDF document.";

                     //Get the signature type
                    SignatureType sigType = signInfo.getSignatureType();
                    String myType = "";

                    if (sigType.getType() == PDFSignatureType.AUTHORSIG)
                        myType="Certification";
                    else if(sigType.getType() == PDFSignatureType.RECIPIENTSIG)
                        myType="Recipient";

                    //Get the Signature properties returned by the Signature service
                    SignatureProperties sigProps = signInfo.getSignatureProps();
                    String signerName =  sigProps.getSignerName();

                   System.out.println("The status of the signature is: "+myStatus +". The signature type is "+myType +". The name of the signer is "+signerName+".");
               }
           }
           catch (Exception ee)
           {
               ee.printStackTrace();
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

 }

 /**
   * sets ValidationPreferences
   */
  private static ValidationPreferences getValidationPreferences(){

        ValidationPreferencesImpl prefs = new ValidationPreferencesImpl();
        prefs.setPKIPreferences(getPKIPreferences());

        //set the unlock options for processing an encrypted pdf document, do not set if the document is unprotected
        prefs.setUnlockOptions(getUnlockOptions());
        return prefs;

    }

  /**
   * sets PKIPreferences
   */
    private static PKIPreferences getPKIPreferences(){
        PKIPreferences pkiPref = new PKIPreferencesImpl();
        pkiPref.setCRLPreferences(getCRLPreferences());
        pkiPref.setPathPreferences(getPathValidationPreferences());
        return pkiPref;
    }

    /**
     * sets CRL Preferences
     */
    private static CRLPreferences getCRLPreferences(){

        CRLPreferencesImpl crlPrefs = new CRLPreferencesImpl();
        crlPrefs.setRevocationCheck(RevocationCheckStyle.CheckIfAvailable);
        crlPrefs.setGoOnline(true);
        return crlPrefs;
    }

    /**
     *
     * sets PathValidationPreferences
     */
    private static PathValidationPreferences getPathValidationPreferences(){
        PathValidationPreferencesImpl pathPref = new PathValidationPreferencesImpl();
        pathPref.setDoValidation(false);
        return pathPref;

    }

    /**
     * sets Unlock Options for encrypted PDF
     */
    private static UnlockOptions getUnlockOptions(){
        UnlockOptions unlockOptions = new UnlockOptions();
        //sets the Open Password for password encrypted PDF
        unlockOptions.setPassword("OpenPassword");

        //for Certificate Encrypted Document, set the alias of the credential uploaded in the user's key store
        //and corresponding resource resolver

        return unlockOptions;

    }

}
```

### Digitale handtekeningen verwijderen {#removing-digital-signatures}

U kunt een nieuwe digitale handtekening alleen op een handtekeningveld toepassen nadat u de vorige digitale handtekening hebt verwijderd. U kunt een digitale handtekening niet overschrijven. Als u probeert een digitale handtekening toe te passen op een handtekeningveld dat al een handtekening bevat, treedt een uitzondering op.

**Syntaxis**: `clearSignatureField(Document inDoc, String signatureFieldName, UnlockOptions unlockOptions)`

**Invoerparameters**

<table>
 <tbody>
  <tr>
   <th>Parameters</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td><code>inDoc</code> </td>
   <td>Document, object dat PDF bevat<br /> </td>
  </tr>
  <tr>
   <td><code>signatureFieldName</code></td>
   <td>De naam van het handtekeningveld<br /> </td>
  </tr>
  <tr>
   <td><code>unlockOptions</code> </td>
   <td>Bevat de parameters die vereist zijn om een gecodeerd bestand te ontgrendelen. Dit is alleen vereist als het bestand is versleuteld<br /> </td>
  </tr>
 </tbody>
</table>

In het volgende Java-codevoorbeeld wordt een digitale handtekening uit een handtekeningveld verwijderd.

```java
/*************************************************************************
 *
  *
-------------------------------------------------------------
*ADOBE SYSTEMS INCORPORATED
*Copyright 2014 Adobe Systems Incorporated
*All Rights Reserved.

*NOTICE:  Adobe permits you to use, modify, and distribute this file in accordance with the
*terms of the Adobe license agreement accompanying it.  If you have received this file
*from a source other than Adobe, then your use, modification, or distribution of it requires
*the prior written permission of Adobe.
-------------------------------------------------------------------------------------------------

 **************************************************************************/
package com.adobe.docassurance.samples;

import java.io.File;
import java.io.IOException;

import javax.jcr.RepositoryException;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.Service;

import com.adobe.aemfd.docmanager.Document;
import com.adobe.fd.docassurance.client.api.DocAssuranceException;
import com.adobe.fd.docassurance.client.api.DocAssuranceService;
import com.adobe.fd.signatures.client.types.exceptions.InvalidArgumentException;
import com.adobe.fd.signatures.client.types.exceptions.PDFOperationException;
import com.adobe.fd.signatures.client.types.exceptions.PermissionsException;
import com.adobe.fd.signatures.client.types.exceptions.SignaturesOtherException;
import com.adobe.fd.signatures.pdf.inputs.UnlockOptions;

/**
 * Digital signatures must be removed from a signature field before a newer digital signature can be applied.
 * A digital signature cannot be overwritten.
 * If you attempt to apply a digital signature to a signature field that contains a signature, an exception occurs
 *
 *The following Java code example removes a digital signature from a signature field named SignatureField1.
 *The name of the PDF file that contain the signature field is LoanSigned.pdf
 */

@Component
@Service(value=ClearSignatureField.class)
public class ClearSignatureField {

 @Reference
 private DocAssuranceService docAssuranceService;
 /**
  *
  * @param inputFile - path to an encrypted pdf document stored at disk
  * @param outFile - path where the output file has to be saved
  * @throws Exception
  */
 public void clearSignatureField(String inputFile, String outFile) throws Exception{

  File inFile = new File(inputFile);
  Document inDoc = new Document(inFile);

        //Specify the name of the signature field
        String fieldName = "SignatureField1";

        //Clear the signature field
        //for encrypted document pass Unlock Options - see the method getUnlockOptions() below
        Document outPDF = docAssuranceService.clearSignatureField(inDoc,fieldName,null);

        //save the outPDF
        outPDF.copyToFile(new File(outFile));
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
}
```

### Handtekeningveld voor certificering wordt opgehaald {#getting-certifying-signature-field}

U kunt de namen ophalen van alle handtekeningvelden in een PDF-document dat u wilt ondertekenen of certificeren. Als u niet zeker weet welke namen van handtekeningvelden zich in een PDF-document bevinden of als u de namen wilt verifiëren, kunt u deze via programmacode ophalen. De service Handtekening retourneert de volledig gekwalificeerde naam van het handtekeningveld, zoals `form1[0].grantApplication[0].page1[0].SignatureField1[0]`.

**Syntaxis**: `getCertifyingSignatureField(Document inDoc, UnlockOptions unlockOptions)`

**Invoerparameters**

<table>
 <tbody>
  <tr>
   <th>Parameters</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td><code>inDoc</code> </td>
   <td>Document-object met PDF.<br /> </td>
  </tr>
  <tr>
   <td><code>UnlockOptions</code></td>
   <td>UnlockOptions bevat de parameters die nodig zijn om een gecodeerd bestand te ontgrendelen. Dit is alleen vereist als het bestand is versleuteld.</td>
  </tr>
 </tbody>
</table>

In het volgende Java-codevoorbeeld wordt het handtekeningveld opgehaald dat is gebruikt om het document te certificeren.

```
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

import java.io.File;
import java.util.Iterator;
import java.util.List;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.Service;

import com.adobe.aemfd.docmanager.Document;
import com.adobe.fd.docassurance.client.api.DocAssuranceService;
import com.adobe.fd.signatures.client.types.PDFSignatureField;
import com.adobe.fd.signatures.client.types.exceptions.DuplicateSignatureFieldException;
import com.adobe.fd.signatures.client.types.exceptions.InvalidArgumentException;
import com.adobe.fd.signatures.client.types.exceptions.PDFOperationException;
import com.adobe.fd.signatures.client.types.exceptions.PermissionsException;
import com.adobe.fd.signatures.client.types.exceptions.SignaturesBaseException;
import com.adobe.fd.signatures.pdf.inputs.UnlockOptions;

/**
 * You can retrieve the names of all signature fields that are located in a PDF document that you want to sign or certify.
 * If you are unsure of the signature field names that are located in a PDF document or you want to verify the names, you can
 * programmatically retrieve them. The Signature service returns the fully qualified name of the signature field, such as
 * form1[0].grantApplication[0].page1[0].SignatureField1[0].
 *
 * The following Java code example retrieves the ignature field that was used to certify the document.
 */

@Component
@Service(value=GetCertifyingSignatureField.class)
public class GetCertifyingSignatureField {

 @Reference
 private DocAssuranceService docAssuranceService;

 /**
  *
  * @param inputFile - path to the pdf document stored at disk
  * @throws SignaturesBaseException
  * @throws DuplicateSignatureFieldException
  * @throws PermissionsException
  * @throws PDFOperationException
  * @throws InvalidArgumentException
  *
  */
 public void getCertifyingSignatureField(String inputFile) throws Exception {

  File inFile = new File(inputFile);
  Document inDoc = new Document(inFile);

  //Retrieve signature data for a given signature field.
  //for encrypted document pass Unlock Options - see the method getUnlockOptions() below
        PDFSignatureField pdfSignature = docAssuranceService.getCertifyingSignatureField(inDoc,null);

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
}
```

### PDF-coderingstype ophalen {#getting-pdf-encryption-type}

U kunt de namen ophalen van alle handtekeningvelden in een PDF-document dat u wilt ondertekenen of certificeren. Als u niet zeker weet welke namen van handtekeningvelden zich in een PDF-document bevinden of als u de namen wilt verifiëren, kunt u deze via programmacode ophalen. De service Handtekening retourneert de volledig gekwalificeerde naam van het handtekeningveld, bijvoorbeeld `asform1[0].grantApplication[0].page1[0].SignatureField1[0]`.

**Syntaxis**: `void getPDFEncryption(Document inDoc)`

**Invoerparameters**

<table>
 <tbody>
  <tr>
   <th>Parameters</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td><code>inDoc</code> </td>
   <td>Een document dat als invoer wordt opgegeven. Het kan al dan niet versleuteld zijn.<br /> </td>
  </tr>
 </tbody>
</table>

In het volgende Java-codevoorbeeld worden de handtekeninggegevens opgehaald van het handtekeningveld in een PDF-document.

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

import java.io.File;
import java.util.Iterator;
import java.util.List;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.Service;

import com.adobe.aemfd.docmanager.Document;
import com.adobe.fd.docassurance.client.api.DocAssuranceService;
import com.adobe.fd.signatures.client.types.PDFSignatureField;
import com.adobe.fd.signatures.client.types.exceptions.DuplicateSignatureFieldException;
import com.adobe.fd.signatures.client.types.exceptions.InvalidArgumentException;
import com.adobe.fd.signatures.client.types.exceptions.PDFOperationException;
import com.adobe.fd.signatures.client.types.exceptions.PermissionsException;
import com.adobe.fd.signatures.client.types.exceptions.SignaturesBaseException;
import com.adobe.fd.signatures.pdf.inputs.UnlockOptions;
import com.adobe.fd.encryption.client.EncryptionTypeResult;

/**
 * You can retrieve the names of all signature fields that are located in a PDF document that you want to sign or certify.
 * If you are unsure of the signature field names that are located in a PDF document or you want to verify the names, you can
 * programmatically retrieve them. The Signature service returns the fully qualified name of the signature field, such as
 * form1[0].grantApplication[0].page1[0].SignatureField1[0].
 *
 * The following Java code example retrieves the Signature Info for the given signature field located in a PDF document.
 */

@Component
@Service(value=GetPDFEncryption.class)
public class GetPDFEncryption {

 @Reference
 private DocAssuranceService docAssuranceService;

 /**
  *
  * @param inputFile - path to the pdf document stored at disk
  * @throws SignaturesBaseException
  * @throws DuplicateSignatureFieldException
  * @throws PermissionsException
  * @throws PDFOperationException
  * @throws InvalidArgumentException
  *
  */
 public void getPDFEncryption(String inputFile) throws Exception {

  File inFile = new File(inputFile);
  Document inDoc = new Document(inFile);

  //Retrieve signature data for a given signature field.
  //for encrypted document pass Unlock Options - see the method getUnlockOptions() below
        EncryptionTypeResult encryptionTypeResult = docAssuranceService.getPDFEncryption(inDoc);

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
}
```

### Wachtwoordversleuteling verwijderen uit PDF {#removing-password-encryption-from-pdf}

Verwijder op wachtwoorden gebaseerde versleuteling uit een PDF-document zodat gebruikers het PDF-document in Adobe Reader of Acrobat kunnen openen zonder een wachtwoord op te geven. Nadat u op een wachtwoord gebaseerde versleuteling uit een PDF-document hebt verwijderd, is het document niet meer beveiligd.

**Syntaxis**: `Document removePDFPasswordSecurity (Document inDoc,String password)`

**Invoerparameters**

<table>
 <tbody>
  <tr>
   <th>Parameters</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td><code>inDoc</code> </td>
   <td>Document opgegeven als invoer. Het bestand moet met een wachtwoord zijn beveiligd.<br /> </td>
  </tr>
  <tr>
   <td><code>password</code> </td>
   <td>Een document openen of wachtwoord voor machtigingen dat moet worden gebruikt voor het verwijderen van beveiliging uit het document.<br /> </td>
  </tr>
 </tbody>
</table>

In het volgende codevoorbeeld wordt op een wachtwoord gebaseerde codering verwijderd uit een PDF-document.

```java
package com.adobe.docassurance.samples;

import java.io.File;
import java.io.FileNotFoundException;
import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.Service;
import org.apache.sling.jcr.api.SlingRepository;

import com.adobe.aemfd.docmanager.Document;
import com.adobe.fd.docassurance.client.api.DocAssuranceService;

/**
 * The following Java code example removes password-based encryption from a PDF document.
 * The master password value used to remove password-based encryption is PermissionPassword
 *
 */
@Component(enabled=true,immediate=true)
@Service(value=RemovePasswordEncryption.class)
public class RemovePasswordEncryption {

 // Create reference for DocAssuranceService
 @Reference
 private DocAssuranceService docAssuranceService;

 @Reference
    private SlingRepository slingRepository;

 /**
  * The below sample code demonstrates removing password encryption from a PDF using AEM EncryptionService.
  *
  * @param inFilePath  path of the input PDF File
  * Path Example for Files stored at hardDisk = "C:/temp/test.pdf"
  *
  * @param outFilePath path where the output PDF File needs to be saved
  * Path Example for Files stored at hardDisk = "C:/temp/test_out.pdf"
  * @throws Exception
  */
 public void removePasswordEncryption(String inputFile, String outputFile) throws Exception {

  File inFile = new File(inputFile);
  Document inDoc = new Document(inFile);

  File outFile = new File(outputFile);
  Document outDoc = null;

     try{

      String password = "PermissionPassword"; //master password with which the pdf was encrypted
                //in case if the pdf is encrypted only with user password, specify the
                //user password
      //Remove password-based encryption from the PDF document
      outDoc = docAssuranceService.removePDFPasswordSecurity(inDoc,password);

     }finally{
                /**
                 * always close the PDFDocument object after your processing is done.
                 */
                if(inDoc != null){
                    inDoc.close();
                }

        }

        outDoc.copyToFile(outFile);

 }

}
```

### Certificaatversleuteling verwijderen {#removing-certificate-encryption}

U kunt versleuteling op basis van certificaten verwijderen uit een PDF-document, zodat gebruikers het PDF-document kunnen openen in Adobe Reader of Acrobat. Als u versleuteling wilt verwijderen uit een PDF-document dat is versleuteld met een certificaat, verwijst u naar een persoonlijke sleutel. Nadat u de versleuteling uit een PDF-document hebt verwijderd, is deze niet meer beveiligd.

**Syntaxis**: `removePDFCertificateSecurity(Document inDoc, String alias, ResourceResolver resourceResolver)`

**Invoerparameters**

<table>
 <tbody>
  <tr>
   <th>Parameters</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td><code>inDoc</code> </td>
   <td>Een object Document dat het met een certificaat gecodeerde PDF-document vertegenwoordigt.<br /> </td>
  </tr>
  <tr>
   <td><code>alias</code> </td>
   <td>De alias die overeenkomt met de sleutel in het Granite Trust Store die wordt gebruikt om op een certificaat gebaseerde versleuteling uit het PDF-document te verwijderen.<br /> </td>
  </tr>
  <tr>
   <td><code>ResourceResolver</code></td>
   <td>ResourceResolver om tot de belangrijkste opslag van de bepaalde gebruiker toegang te hebben om de Credentials te halen.</td>
  </tr>
 </tbody>
</table>

In het volgende Java-codevoorbeeld wordt versleuteling op basis van een certificaat verwijderd uit een PDF-document.

```java
package com.adobe.docassurance.samples;

import java.io.File;

import javax.jcr.Session;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.Service;
import org.apache.sling.api.resource.ResourceResolver;
import org.apache.sling.jcr.api.SlingRepository;
import org.apache.sling.jcr.resource.JcrResourceResolverFactory;

import com.adobe.aemfd.docmanager.Document;
import com.adobe.fd.docassurance.client.api.DocAssuranceService;

/**
 * The following Java code example removes certificate-based encryption from a PDF document
 *
 */
@Component(enabled=true,immediate=true)
@Service(value=RemovePKIEncryption.class)
public class RemovePKIEncryption {

 // Create reference for docAssuranceServiceInterface
 @Reference
 private DocAssuranceService docAssuranceService;

 @Reference
    private SlingRepository slingRepository;

 @Reference
    private JcrResourceResolverFactory jcrResourceResolverFactory ;

 /**
  * The below sample code demonstrates encrypting PDF with Password using AEM docAssuranceService.
  *
  * @param inFilePath  path of the input PDF File
  * Path Example for Files stored at hardDisk = "C:/temp/test.pdf"
  *
  * @param outFilePath path where the output PDF File needs to be saved
  * Path Example for Files stored at hardDisk = "C:/temp/test_Encrypted.pdf"
  *
  * @throws Exception
  */
 public void removePKIEncryption(String inputFile, String outputFile) throws Exception {

  File inFile = new File(inputFile);
  Document inDoc = new Document(inFile);

  File outFile = new File(outputFile);
  Document outDoc = null;

        Session adminSession = null;
        ResourceResolver resourceResolver = null;
        try{
    adminSession = slingRepository.loginAdministrative(null);
    resourceResolver = jcrResourceResolverFactory.getResourceResolver(adminSession);

    //Remove certificate-based encryption from the PDF document
    /**
     * Here the alias("encryption") of the private credential stored in the keystore of the
     * user has been provided with the user's resource resolver
     */
    outDoc = docAssuranceService.removePDFCertificateSecurity(inDoc, "encryption",resourceResolver);

        }catch(Exception e){

         // TODO Auto-generated catch block
        }finally{
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

        outDoc.copyToFile(outFile);
 }

 }
```

## Uitvoerservice {#output-service}

De uitvoerservice biedt API&#39;s waarmee een XDP-bestand kan worden gerenderd in de indelingen .pdf, .pcl, .zpl en .ps. De service ondersteunt de volgende API&#39;s:

* **[generatePDFOutput](/help/forms/using/aem-document-services-programmatically.md#p-generatepdfoutput-p):**Hiermee wordt een PDF-document gegenereerd door een formulierontwerp samen te voegen met gegevens die als letterlijke waarden zijn opgeslagen op een netwerklocatie, lokaal bestandssysteem of HTTP-locatie.

* **[generatePDFOutput](/help/forms/using/aem-document-services-programmatically.md#p-generatepdfoutput-p):**Hiermee wordt een PDF-document gegenereerd door een formulierontwerp samen te voegen met gegevens die in een toepassing zijn opgeslagen.
* **[generatePDFOutputBatch](/help/forms/using/aem-document-services-programmatically.md#p-generatepdfoutputbatch-p):**Hiermee voegt u een formulierontwerp samen met gegevens om een PDF-document te maken. Hiermee genereert u desgewenst een metagegevensbestand voor elke record of slaat u de uitvoer op in een PDF-bestand.
* **[generatePrintedOutput](/help/forms/using/aem-document-services-programmatically.md#p-generateprintedoutput-p):**Hiermee genereert u een PCL-, PostScript- of ZPL-uitvoer van een formulierontwerp en een gegevensbestand dat is opgeslagen op een netwerklocatie, lokaal bestandssysteem of HTTP-locatie als letterlijke waarden.

* **[generatePrintedOutput](/help/forms/using/aem-document-services-programmatically.md#p-generateprintedoutput-p):**Hiermee genereert u een PCL-, PostScript- en ZPL-uitvoer van een formulierontwerp en gegevensbestand dat in een toepassing is opgeslagen.

### generatePDFOutput {#generatepdfoutput}

Met de API generatePDFOutput wordt een PDF-document gegenereerd door een formulierontwerp met gegevens samen te voegen. Hiermee genereert u desgewenst een metagegevensbestand voor elke record of slaat u de uitvoer op in een PDF-bestand. Gebruik de API generatePDFOutput voor de formulierontwerpen of gegevens die zijn opgeslagen op een netwerklocatie, lokaal bestandssysteem of HTTP-locatie als letterlijke waarden. Als het formulierontwerp en de XML-gegevens in een toepassing worden opgeslagen, gebruikt u de API [generatePDFOutput](/help/forms/using/aem-document-services-programmatically.md#p-generatepdfoutput-p) .

**Syntaxis:** `Document generatePDFOutput(String uriOrFileName, Document data, PDFOutputOptions options);`

#### Invoerparameters {#input-parameters}

<table>
 <tbody>
  <tr>
   <th>Parameters</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td>uriOrFileName</td>
   <td>Hiermee geeft u het pad en de naam van het invoerbestand op. Het bestand kan van het type PDF of XDP zijn. Als alleen de bestandsnaam wordt opgegeven, wordt het bestand gelezen ten opzichte van de inhoudRoot die in de opties is opgegeven.</td>
  </tr>
  <tr>
   <td>gegevens</td>
   <td>Een XML-bestand dat de gegevens bevat die met het PDF-document zijn samengevoegd.<br /> </td>
  </tr>
  <tr>
   <td>opties</td>
   <td>Geeft waarden op voor de variabelen contentRoot, locale, AcrobatVersion, linearzedPDF en taggedPDF. De parameter options accepteert object van het type PDFOutputOptions. <br /> </td>
  </tr>
 </tbody>
</table>

In het volgende voorbeeld van Java-code wordt een PDF-document gegenereerd door een formulierontwerp samen te voegen met gegevens die zijn opgeslagen in een XML-bestand.

```java
@Reference private OutputService outputService;

private File generatePDFOutput(String contentRoot,File inputXML,String templateStr,String acrobatVersion,String tagged,String linearized, String locale) {

String outputFolder="C:/Output";

Document doc=null;

try {

        PDFOutputOptions option = new PDFOutputOptions();         option.setContentRoot(contentRoot);         if(acrobatVersion.equalsIgnoreCase("Acrobat_10"))

        {

            option.setAcrobatVersion(com.adobe.fd.output.api.AcrobatVersion.Acrobat_10);

        } else if(acrobatVersion.equalsIgnoreCase("Acrobat_10_1")) {

            option.setAcrobatVersion(com.adobe.fd.output.api.AcrobatVersion.Acrobat_10_1);

        } else if(acrobatVersion.equalsIgnoreCase("Acrobat_11")) {             option.setAcrobatVersion(com.adobe.fd.output.api.AcrobatVersion.Acrobat_11);

        }

        if (tagged.equalsIgnoreCase("true") ) {

            option.setTaggedPDF(true );

        }

        if (linearized.equalsIgnoreCase("true") ) {

            option.setTaggedPDF(true );

        }

        if(locale!=null)

        {

            option.setLocale(locale);

        }

        InputStream in = new FileInputStream(inputXML);

        doc = outputService.generatePDFOutput(templateStr,new Document(in),option);         File toSave = new File(outputFolder+"Output.pdf");

        doc.copyToFile(toSave);

        return toSave;

    } catch (OutputServiceException e) {

         e.printStackTrace();

    }catch (FileNotFoundException e) {

         e.printStackTrace();

    } catch (IOException e) {

         e.printStackTrace();

    }finally{

                doc.dispose();

    }

    return null;

}
```

### generatePDFOutput {#generatepdfoutput-1}

Met de API generatePDFOutput wordt een PDF-document gegenereerd door een formulierontwerp met gegevens samen te voegen. U kunt desgewenst een metagegevensbestand genereren voor elke record of de uitvoer opslaan in een PDF-bestand. Gebruik de API generatePrintedOutput voor de formulierontwerpen of gegevens die in een toepassing zijn opgeslagen. Als het formulierontwerp en de XML-gegevens als letterlijke waarden zijn opgeslagen op een netwerklocatie, lokaal of op een HTTP-locatie, gebruikt u de [generatePDFOutput](/help/forms/using/aem-document-services-programmatically.md#p-generatepdfoutput-p) -API.

**Syntaxis:** `Document generatePDFOutput(Document inputdocument, Document data, PDFOutputOptions options)`

#### Invoerparameter {#input-parameter}

<table>
 <tbody>
  <tr>
   <th>Parameters</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td>Inputdocument<br /> </td>
   <td>Hiermee geeft u het pad en de naam van het invoerbestand op. Het bestand kan van het type PDF of XDP zijn. Als alleen de bestandsnaam wordt opgegeven, wordt het bestand gelezen ten opzichte van de inhoudRoot die in de opties is opgegeven. <br /> </td>
  </tr>
  <tr>
   <td>gegevens</td>
   <td>Een XML-bestand dat de gegevens bevat die met het PDF-document zijn samengevoegd.<br /> </td>
  </tr>
  <tr>
   <td>opties</td>
   <td>Geeft waarden op voor de variabelen contentRoot, locale, AcrobatVersion, linearzedPDF en taggedPDF. De parameter options accepteert object van het type PDFOutputOptions.</td>
  </tr>
 </tbody>
</table>

In het volgende voorbeeld van Java-code wordt een PDF-document gegenereerd door een formulierontwerp samen te voegen met gegevens die zijn opgeslagen in een XML-bestand.

```java
@Reference private OutputService outputService;

private File generatePDFOutput2(String contentRoot, File inputXML, File templateStr, String acrobatVersion, String tagged, String linearized, String locale) {

String outputFolder="C:/Output";

Document doc=null;

     try {

            PDFOutputOptions option = new PDFOutputOptions();             option.setContentRoot(contentRoot);
            if(locale!=null)

            {

                option.setLocale(locale);

            }

            if(acrobatVersion.equalsIgnoreCase("Acrobat_10"))

            {

                option.setAcrobatVersion(com.adobe.fd.output.api.AcrobatVersion.Acrobat_10);

            } else if(acrobatVersion.equalsIgnoreCase("Acrobat_10_1")) {                 option.setAcrobatVersion(com.adobe.fd.output.api.AcrobatVersion.Acrobat_10_1);

            } else if(acrobatVersion.equalsIgnoreCase("Acrobat_11")) {                 option.setAcrobatVersion(com.adobe.fd.output.api.AcrobatVersion.Acrobat_11);

            }

            if (tagged.equalsIgnoreCase("true") ) {

                option.setTaggedPDF(true );

            }

            if (linearized.equalsIgnoreCase("true") ) {

                option.setTaggedPDF(true );

            }

            InputStream inputXMLStream = new FileInputStream(inputXML);

            InputStream templateStream = new FileInputStream(templateStr);;

            doc = outputService.generatePDFOutput(new Document(templateStream),new             Document(inputXMLStream),option);

                     File toSave = new File(outputFolder,"Output.pdf");

                     doc.copyToFile(toSave);

                    return toSave;

                } catch (OutputServiceException e) {

                         e.printStackTrace();

               }catch (FileNotFoundException e) {

                          e.printStackTrace();

               } catch (IOException e) {

                          e.printStackTrace();

               }finally{

                            doc.dispose();

              }

                return null;

}
```

### generatePDFOutputBatch {#generatepdfoutputbatch}

Hiermee voegt u een formulierontwerp samen met gegevens om een PDF-document te maken. Hiermee genereert u desgewenst een metagegevensbestand voor elke record of slaat u de uitvoer op in een PDF-bestand. Gebruik de API generatePDFOutputBatch voor formulierontwerpen of gegevens die als letterlijke waarden zijn opgeslagen op een netwerklocatie, een lokaal bestandssysteem of een HTTP-locatie.

**Syntaxis:** `BatchResult generatePDFOutputBatch(Map templates, Map data, PDFOutputOptions options, BatchOptions batchOptions);`

#### Invoerparameters {#input-parameters-1}

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td>templates<br /> </td>
   <td>Geeft de map met sleutel- en sjabloonbestandsnaam op.<br /> </td>
  </tr>
  <tr>
   <td>gegevens</td>
   <td>Geeft de Kaart van sleutel- en gegevensdocument aan. Als de sleutel niet ongeldig is, dan wordt het gegevensdocument teruggegeven met malplaatje voor overeenkomstige die sleutel in de malplaatjesKaart wordt gespecificeerd. </td>
  </tr>
  <tr>
   <td>opties</td>
   <td>Geeft waarden op voor de variabelen contentRoot, locale, AcrobatVersion, linearzedPDF en taggedPDF. De parameter options accepteert object van het type PDFOutputOptions.</td>
  </tr>
  <tr>
   <td>batchOptions</td>
   <td>Specifies the value of the variable <code>generateManyFiles</code>. Stel de markering generateManyFiles in om meerdere bestanden te genereren. De parameter options accepteert object van het type BatchOptions.</td>
  </tr>
 </tbody>
</table>

In het volgende Java-codevoorbeeld worden PDF-documenten gegenereerd door een formulierontwerp samen te voegen met gegevens die zijn opgeslagen in een XML-bestand.

```java
private ArrayList generatePDFBatch(String contentRoot,String multipleFiles) {

String outputFolder="C:/Output";

    try {

        PDFOutputOptions option = new PDFOutputOptions();         option.setContentRoot(contentRoot);

        Map templates = new LinkedHashMap();

        Map data = new LinkedHashMap();

        String template1 = "PurchaseOrder.xdp"; String template2 = "CardApp.xdp";         templates.put(template1.substring(0, template1.indexOf(".xdp")),template1);         templates.put(template1.substring(0, template2.indexOf(".xdp")),template2);

        File inputXML1 = new File("c:/InputFolder/PurchaseOrder.xml");

        File inputXML2 = new File("c:/InputFolder/CardApp.xml");

        InputStream in1 = new FileInputStream(inputXML1);

        InputStream in2 = new FileInputStream(inputXML2);

        data.put(template1.substring(0, template1.indexOf(".xdp")),new         Document((in1))); data.put(template1.substring(0,         template1.indexOf(".xdp")),new Document((in2))); BatchOptions bo = new         BatchOptions(); BatchResult ret=null;         if(multipleFiles.equalsIgnoreCase("true"))

        {

            bo.setGenerateManyFiles(true);

            ret = outputService.generatePDFOutputBatch(templates, data, option, bo);

        } else {

            ret = outputService.generatePDFOutputBatch(templates, data, option, new             BatchOptions());

        }

        ArrayList outputs = new ArrayList();

        int counter=0;

        if(ret.getMetaDataDoc() !=null ){

        File toSave = new File(outputFolder+"Output.xml");

        ret.getMetaDataDoc().copyToFile(toSave);

        outputs.add(toSave);

        List<Document> list = ret.getGeneratedDocs();

        for(Document doc:list){

        File toSave = new File(outputFolder,"Output"+"_"+counter+".pdf");         doc.copyToFile(toSave);                    outputs.add(toSave);

        counter++;

        doc.dispose();

        }

        return outputs;

       } catch (OutputServiceException e) {

            e.printStackTrace();

       }catch (FileNotFoundException e) {

            e.printStackTrace();

       }catch (IOException e) {

            e.printStackTrace();

       }

       return null;

}
```

### generatePrintedOutput {#generateprintedoutput}

Hiermee genereert u een PCL-, PostScript- en ZPL-uitvoer van een formulierontwerp en gegevensbestand. Het gegevensbestand wordt samengevoegd met het formulierontwerp en voor afdrukken opgemaakt. U kunt de uitvoer rechtstreeks naar een printer verzenden of als bestand opslaan. Gebruik de API generatePrintedOutput voor de formulierontwerpen of gegevens die in een toepassing zijn opgeslagen.

**Syntaxis:** `Document generatePrintedOutput(String uriOrFileName, Document data, PrintedOutputOptions);`

#### Invoerparameters {#input-parameters-2}

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td>uriOrFileName<br /> </td>
   <td>Hiermee geeft u het pad en de naam van het invoerbestand op. Als alleen de bestandsnaam wordt opgegeven, wordt het bestand gelezen ten opzichte van de inhoudRoot die in de opties is opgegeven. Het bestand kan van het type PDF of XDP zijn.<br /> </td>
  </tr>
  <tr>
   <td>gegevens</td>
   <td>Een XML-bestand dat gegevens bevat die worden samengevoegd met PDF-documenten.<br /> </td>
  </tr>
  <tr>
   <td>opties</td>
   <td>Geeft waarden op voor de variabelen contentRoot, locale, AcrobatVersion, linearzedPDF en taggedPDF. De parameter options accepteert object van het type PrintedOutputOptions.<br /> </td>
  </tr>
 </tbody>
</table>

In het volgende Java-codevoorbeeld worden PCL-, PostScript- en ZPL-uitvoer gegenereerd op basis van een formulierontwerp en gegevens. Het uitvoertype is afhankelijk van de waarde die aan de `printConfig`parameter wordt doorgegeven.

```java
@Reference private OutputService outputService;

private File generatePrintedOutput(String contentRoot,File inputXML,String templateStr,String printConfig) {

String outputFolder="C:/Output";

Document doc=null;

    try {

            PrintedOutputOptions options = new PrintedOutputOptions();                           options.setContentRoot(contentRoot);

            if(printConfig.equalsIgnoreCase("ps"))

            {

                options.setPrintConfig(PrintConfig.PS_PLAIN);

            }else if(printConfig.equalsIgnoreCase("pcl")) {

                            options.setPrintConfig(PrintConfig.HP_PCL_5e);

                     }else if(printConfig.equalsIgnoreCase("zpl")) {                                                                       options.setPrintConfig(PrintConfig.ZPL300);

            }

            InputStream in = new FileInputStream(inputXML);

            doc = outputService.generatePrintedOutput(templateStr,new             Document(in),options);

            in.close();

            File toSave = new File(outputFolder,"Output"+"."+printConfig);             doc.copyToFile(toSave);

            return  toSave;

        } catch (OutputServiceException e) {

             e.printStackTrace();

        }catch (FileNotFoundException e) {

             e.printStackTrace();

        }catch (IOException e) {

             e.printStackTrace();

        }finally{

             doc.dispose();

        }

        return null;

}
```

### generatePrintedOutput {#generateprintedoutput-1}

Hiermee genereert u een PCL-, PostScript- en ZPL-uitvoer op basis van een formulierontwerp en een gegevensbestand. Het gegevensbestand wordt samengevoegd met het formulierontwerp en voor afdrukken opgemaakt. De uitvoer kan rechtstreeks naar een printer worden verzonden of als bestand worden opgeslagen. Gebruik de API generatePrintedOutput voor de formulierontwerpen of gegevens die in een toepassing zijn opgeslagen.

**Syntaxis:** `Document generatePrintedOutput(Document inputdocument, Document data, PrintedOutputOptions);`

#### Invoerparameters {#input-parameters-3}

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td>Inputdocument<br /> </td>
   <td>Hiermee geeft u het pad en de naam van het invoerbestand op. Als alleen de bestandsnaam wordt opgegeven, wordt het bestand gelezen ten opzichte van de inhoudRoot die in de opties is opgegeven. Het bestand kan van het type XDP zijn. </td>
  </tr>
  <tr>
   <td>gegevens</td>
   <td>Een XML-bestand dat gegevens bevat die worden samengevoegd met PDF-documenten.<br /> </td>
  </tr>
  <tr>
   <td>opties</td>
   <td>Dit object wordt gebruikt om de waarden van contentRoot, locale, printConfig, copies en paginationOverride in te stellen. De parameter options accepteert object van het type PrintedOutputOptions.<br /> </td>
  </tr>
 </tbody>
</table>

In het volgende Java-codevoorbeeld worden PCL-, PostScript- en ZPL-uitvoer gegenereerd op basis van een formulierontwerp en gegevens. Het uitvoertype is afhankelijk van de waarde die aan de `printConfig`parameter wordt doorgegeven.

```java
@Reference private OutputService outputService;

private File generatePrintedOutput2(File  inputXML,File templateStr,String printConfig) {

String outputFolder="C:/Output";

Document doc=null;

       try {

            PrintedOutputOptions options = new PrintedOutputOptions();             if(printConfig.equalsIgnoreCase("ps"))

            {

                options.setPrintConfig(PrintConfig.PS_PLAIN);

            }else if(printConfig.equalsIgnoreCase("pcl")) {                                   options.setPrintConfig(PrintConfig.HP_PCL_5e);

            }else if(printConfig.equalsIgnoreCase("zpl")) {                                                                       options.setPrintConfig(PrintConfig.ZPL300);

                             }

            InputStream inputXMlStream = new FileInputStream(inputXML);

            InputStream templateStream = new FileInputStream(templateStr); doc =             outputService.generatePrintedOutput(new Document(templateStream),new             Document(inputXMlStream),options);

            File toSave = new File(outputFolder,"Output"+"."+printConfig);             doc.copyToFile(toSave);

            return toSave;

            } catch (OutputServiceException e) {

                e.printStackTrace();

            }catch (FileNotFoundException e) {

                e.printStackTrace();

            } catch (IOException e) {

                e.printStackTrace();

            }finally{

                doc.dispose();

            }

            return null;

}
```

### generatePrintedOutputBatch {#generateprintedoutputbatch}

Hiermee genereert u een document met de PS-, PCL- en ZPL-indeling door een formulierontwerp samen te voegen met gegevens. U kunt desgewenst een metagegevensbestand genereren voor elke record of de uitvoer opslaan in een PDF-bestand. Gebruik de API generatePrintedOutputBatch voor de formulierontwerpen of gegevens die zijn opgeslagen op een netwerklocatie, een lokaal bestandssysteem of een HTTP-locatie als letterlijke waarden.

**Syntaxis`:`**`BatchResult generatePrintedOutputBatch(Map templates, Map data, PrintedOutputOptions options, BatchOptions batchOptions);`

#### Invoerparameters {#input-parameters-4}

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td>templates<br /> </td>
   <td>Hiermee geeft u de kaart van de bestandsnaam van de toets en de sjabloon op.<br /> </td>
  </tr>
  <tr>
   <td>gegevens</td>
   <td>Hiermee geeft u een kaart van sleutel- en gegevensdocument op. Als de sleutel niet ongeldig is, dan wordt het gegevensdocument teruggegeven met malplaatje voor overeenkomstige sleutel in de malplaatjesKaart.<br /> </td>
  </tr>
  <tr>
   <td>opties</td>
   <td>Hiermee wordt het object opgegeven van het type PrintedOutputOptions. Dit object wordt gebruikt om de waarden van contentRoot, locale, printConfig, copies, paginationOverride in te stellen.<br /> </td>
  </tr>
  <tr>
   <td>batchOptions</td>
   <td>Specifies value of variable generateManyFiles. Stel de markering generateManyFiles in om meerdere bestanden te genereren. De parameter options accepteert object van het type BatchOptions.<br /> </td>
  </tr>
 </tbody>
</table>

In het volgende Java-codevoorbeeld worden PCL-, PostScript- en ZPL-uitvoer in batch gegenereerd op basis van meerdere sjablonen en gegevensbestanden voor formulierontwerp. Het uitvoertype is afhankelijk van de waarde die aan de `printConfig`parameter wordt doorgegeven.

```java
@Reference private OutputService outputService;

private ArrayList generatePrintedOutputBatch(String contentRoot,String multipleFiles,String printConfig) {

String outputFolder="C:/Output";

        try {

                PrintedOutputOptions option = new PrintedOutputOptions();                 option.setContentRoot(contentRoot);

                Map templates = new LinkedHashMap();

                Map data = new LinkedHashMap();

                String template1 = "PurchaseOrder.xdp";

                String template2 = "CardApp.xdp";

                templates.put(template1.substring(0,                 template1.indexOf(".xdp")),template1);                 templates.put(template1.substring(0,                 template2.indexOf(".xdp")),template2);

                File inputXML1 = new                                   File("c:/InputFolder/PurchaseOrder.xml");

                File inputXML2 = new File("c:/InputFolder/CardApp.xml");

                InputStream in1 = new FileInputStream(inputXML1);

                InputStream in2 = new FileInputStream(inputXML2);                  data.put(template1.substring(0,                     template1.indexOf(".xdp")),new Document((in1)));

                 data.put(template2.substring(0,                     template2.indexOf(".xdp")),new Document((in2)));

                 if(printConfig.equalsIgnoreCase("ps"))

                 {

                    option.setPrintConfig(PrintConfig.PS_PLAIN);

                 } else if(printConfig.equalsIgnoreCase("pcl"))

                 {

                    option.setPrintConfig(PrintConfig.HP_PCL_5e);

                 } else if(printConfig.equalsIgnoreCase("zpl")){

                                         option.setPrintConfig(PrintConfig.ZPL300);

                 }

                 option.setContentRoot(contentRoot);

                 BatchOptions bo = new BatchOptions();

                 BatchResult ret =                             outputService.generatePrintedOutputBatch(temp                                    lates, data, option, new                                                     BatchOptions());

                 ArrayList outputs = new ArrayList();

                 int counter=0;

                 if(ret.getMetaDataDoc() !=null ){

                 File toSave = new File(outputFolder,"Output"+".xml");                    ret.getMetaDataDoc().copyToFile(toSave);

                 outputs.add(toSave);

                 List<Document> list = ret.getGeneratedDocs();

                 for(Document doc:list){

                 File toSave = new                                                               File(outputFolder,"Output"+"_"+counter+".                                        "+printConfig);                                    doc.copyToFile(toSave);

                 outputs.add(toSave);

                 counter++;

                 doc.dispose();

                 }

                 return outputs;

          }

            catch (OutputServiceException e) {

                e.printStackTrace();

          }catch (FileNotFoundException e) {

                e.printStackTrace();

          } catch (IOException e) {

                e.printStackTrace();

          }

            return null;

  }
```

## Forms Service {#forms-service}

De service Forms biedt API&#39;s voor het importeren en exporteren van gegevens van en naar een interactief PDF-formulier. Een interactief PDF-formulier is een PDF-document dat een of meer velden bevat die worden gebruikt voor het weergeven en verzamelen van informatie van gebruikers. De service ondersteunt de volgende API&#39;s:

* **[exportData](/help/forms/using/aem-document-services-programmatically.md#p-exportdata-p):**Hiermee exporteert u gegevens uit een PDF-formulier.
* **[importData](/help/forms/using/aem-document-services-programmatically.md#p-importdata-p):**Hiermee importeert u gegevens in een interactief PDF-formulier.

### exportData {#exportdata}

Hiermee exporteert u formuliergegevens uit een interactief PDF-formulier in XML- en XDP-indeling.

**Syntaxis:** `Document exportData(Document xdpOrPdf, DataFormat dataFormat)`

#### Invoerparameters {#input-parameters-5}

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td>xdpOrPdf<br /> </td>
   <td>Hiermee wordt een documentobject opgegeven dat een XDP- of PDF-bestand bevat. </td>
  </tr>
  <tr>
   <td>dataFormat<br /> </td>
   <td>Hiermee geeft u de indeling op waarin gegevens worden geëxporteerd. De variabele accepteert variabele van het type enum (XDP, XmlData, Auto).<br /> </td>
  </tr>
 </tbody>
</table>

Met het volgende voorbeeld van Java-code exporteert u formuliergegevens uit een interactief PDF-formulier in XML- en XDP-indeling.

#### Voorbeeld {#sample}

```java
@Reference private FormsService formsService;
private File exportData(String  dataFormat, File  inDoc) {

String outputFolder="C:/Output";

InputStream in; Document doc=null;

try {

        in = new FileInputStream(inDoc);

        if(dataFormat.equalsIgnoreCase("xml"))

        {

          doc=formsService.exportData(new Document(in),                                       DataFormat.XmlData);

        }

        else if(dataFormat.equalsIgnoreCase("xdp")) {

        doc =formsService.exportData(new Document(in),                       DataFormat.XDP);

        }

        File toSave = new File(outputFolder,"Output"+"."+dataFormat);

        doc.copyToFile(toSave);

        return toSave;

    } catch (FormsServiceException e) {

       e.printStackTrace();

    }catch (FileNotFoundException e) {

       e.printStackTrace();

    } catch (IOException e) {

       e.printStackTrace();

    }finally{

        doc.dispose();

    }

    return null;

 }
```

### importData {#importdata}

Hiermee importeert u formuliergegevens in een interactief PDF-formulier.

**Syntaxis:** `Document importData(Document PDF, Document data)`

#### Invoerparameters {#input-parameters-6}

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td>PDF<br /> </td>
   <td>Hiermee wordt een documentobject opgegeven dat PDF-bestanden bevat. </td>
  </tr>
  <tr>
   <td>Data<br /> </td>
   <td>Een XML-bestand dat gegevens in XML-indeling bevat.</td>
  </tr>
 </tbody>
</table>

In het volgende Java-codevoorbeeld worden formuliergegevens geïmporteerd in een interactief PDF-formulier.

#### Voorbeeld {#sample-1}

```java
@Reference private FormsService formsService

private File importData(File inDoc, File inXML)

{

 String outputFolder="C:/Output";

 Document doc=null;

 try {

        InputStream in = new FileInputStream(inDoc);

        InputStream in2 = new FileInputStream(inXML);

        doc=formsService.importData(new Document(in), new Document(in2));

        File toSave = new File(outputFolder,"Output.pdf");

        doc.copyToFile(toSave);

    } catch (FormsServiceException e) {

         e.printStackTrace();

    }catch (FileNotFoundException e) {

         e.printStackTrace();

    } catch (IOException e) {

         e.printStackTrace();

    }finally{

        doc.dispose();

    }

    return null;

}
```

## PDF Generator-service {#pdfgeneratorservice}

De service PDF Generator biedt API&#39;s waarmee native bestandsindelingen naar PDF kunnen worden geconverteerd. Ook wordt PDF geconverteerd naar andere bestandsindelingen en wordt de grootte van PDF-documenten geoptimaliseerd.

### GeneratePDFService {#generatepdfservice}

De GeneratePDFService verstrekt APIs om diverse dossierformaten zoals .doc, .docx, .ppt, .pptx, .xls, .xlsx, .odp, .odt, .ods, (Vervangen).swf, .jpg, .bmp, .tif, .png, .html, en vele andere dossierformaten in PDF om te zetten. Het biedt ook API&#39;s om PDF naar verschillende bestandsindelingen te exporteren en PDF&#39;s te optimaliseren. De service ondersteunt de volgende API&#39;s:

* **createPDF**: Hiermee converteert u een ondersteund bestandstype naar een PDF-document. Bestandsindelingen zoals Microsoft Word, Microsoft PowerPoint, Microsoft Excel en Microsoft Project worden ondersteund. Naast deze toepassingen kan elk generiek PDF-bestand van derden dat het toepassingstype genereert, ook in de API worden aangesloten.
* **exportPDF**: Hiermee wordt een PDF-document geconverteerd naar een ondersteund bestandstype. De methode accepteert een PDF als invoer en exporteert de inhoud van de PDF in de opgegeven bestandsindeling. U kunt een PDF-document exporteren in Encapsulated PostScript( eps), HTML 3.2( htm, html), HTML 4.01 met CSS 1.0( htm, html), JPEG( jpg, jpeg, jpe), JPEG2000( jpf, jpx, jp2, j2k, j2c, jpc), Microsoft), Word-document ( doc, docx) Microsoft Excel-werkboek( xlsx), Microsoft PowerPoint-presentatie( pptx), PNG( png), PostScript( ps), Rich Text Format( rtf), Text(Accessible)( txt), Text(Plain)( txt) TIFF( tif, tiff), XML 1.0( xml), PDF/A-1a (sRGB), PDF/A-1b, PDF/A-2a(sRGB), PDF/A-2b(sRGB), PDF/A-3a(sRGB), PDF/A-3b(sRGB). U kunt ook [aangepaste Preflight-profielen](https://helpx.adobe.com/acrobat/using/preflight-profiles-acrobat-pro.html) opgeven voor de PDF-uitvoer.

* **PDF** optimaliseren: Hiermee optimaliseert u het PDF-document en converteert u een PDF-document van het ene naar het andere type. De methode accepteert een PDF-document als invoer.
* **htmlToPdf2**: Hiermee converteert u een HTML-pagina naar een PDF-document. De URL van de HTML-pagina wordt als invoer geaccepteerd.

>[!NOTE]
>
>De HTMLtoPDF-API is verouderd voor AEM Forms-server die wordt uitgevoerd op het AIX-besturingssysteem.

#### PDF Generator-API beschikbaar voor Microsoft Windows en Linux {#pdf-generator-api-available-on-microsoft-windows-and-linux}

<table>
 <tbody>
  <tr>
   <td><strong>API</strong></td>
   <td><p><strong>Microsoft Windows </strong></p> </td>
   <td><strong>Linux </strong></td>
  </tr>
  <tr>
   <td>createPDF</td>
   <td><strong>✓</strong></td>
   <td><strong>✓</strong></td>
  </tr>
  <tr>
   <td>htmlToPDF</td>
   <td><strong>✓</strong></td>
   <td><strong>✓</strong></td>
  </tr>
   <td>optimaliserenPDF</td>
   <td><strong>✓</strong></td>
   <td>✖</td>
  </tr>
  <tr>
   <td>exportPDF</td>
   <td><strong>✓</strong></td>
   <td>✖</td>
  </tr>
  <tr>
   <td>OCR PDF (doorzoekbare PDF)</td>
   <td><strong>✓</strong></td>
   <td>✖</td>
  </tr>
 </tbody>
</table>

#### createPDF {#createpdf}

De createPDF API converteert een ondersteund bestandstype naar een PDF-document. Het steunt diverse dossierformaten zoals Microsoft Word, Microsoft PowerPoint, Microsoft Excel, en Project van Microsoft. Naast deze toepassingen kan elk generiek PDF-bestand van derden dat het toepassingstype genereert, ook in de API worden aangesloten.

Voor de conversie zijn slechts enkele parameters verplicht. Een invoerdocument is een verplichte parameter. U kunt de beveiligingsmachtigingen, PDF-uitvoerinstellingen en metagegevens later toepassen op het PDF-uitvoerdocument.

De service createPDF retourneert een Java.util.Map met resultaten. De kaarttoetsen zijn:

* ConvertedDoc: Het bevat het nieuwe PDF-document.
* LogDoc: Het bevat het logbestand.

De service createPDF genereert de volgende uitzonderingen:

* ConversionException
* InvalidParameterException
* FileFormatNotSupportedException

**Syntaxis:** `Map createPDF(Document inputDoc, String inputFilename, String fileTypeSettings, String pdfSettings, String securitySettings, Document settingsDoc, Document xmpDoc) throws InvalidParameterException, ConversionException, FileFormatNotSupportedException;`

#### Invoerparameters {#input-parameters-7}

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td>inputDoc<br /> </td>
   <td>Hiermee wordt een documentobject opgegeven. Het documentobject bevat het invoerbestand. Maak een com.adobe.adobe.aemfd.docmanager.Document-object via het invoerdocument. Het is een verplichte parameter.</td>
  </tr>
  <tr>
   <td>inputFileName<br /> </td>
   <td>De naam van het invoerbestand en de extensie. Het is een verplichte parameter.<br /> </td>
  </tr>
  <tr>
   <td>fileTypeSettings</td>
   <td>Het is een optionele parameter.</td>
  </tr>
  <tr>
   <td>pdfSettings</td>
   <td><p>PDF-uitvoer voor het geconverteerde document. U kunt alleen de volgende instellingen toepassen:</p>
    <ul>
     <li>Hoge_kwaliteit_Afdrukken<br /> </li>
     <li>PDFA1b_2005_RGB<br /> </li>
     <li>PDFA1b_2005_CMYK<br /> </li>
     <li>PDFX1a_2001<br /> </li>
     <li>PDFX3_2002<br /> </li>
     <li>Press_Quality<br /> </li>
     <li>Kleinste_Bestand_Grootte</li>
    </ul> <p>Het is een optionele parameter.<br /> </p> </td>
  </tr>
  <tr>
   <td>securitySettings</td>
   <td><p>Beveiligingsinstellingen voor het geconverteerde document. U kunt de volgende instellingen toepassen:</p>
    <ul>
     <li>Geen beveiliging</li>
     <li>Wachtwoordbeveiliging<br /> </li>
     <li>Certificaatbeveiliging<br /> </li>
     <li>Adobe-beleidsserver</li>
    </ul> <p>Het is een optionele parameter.</p> </td>
  </tr>
  <tr>
   <td>settingsDoc</td>
   <td>Het bestand bevat de instellingen die zijn toegepast tijdens het genereren van het PDF-document (zoals PDF-document optimaliseren voor webweergave) en instellingen die zijn toegepast nadat het PDF-document is gemaakt (zoals Weergave bij openen en Beveiliging). Het is een optionele parameter.<br /> </td>
  </tr>
  <tr>
   <td>xmpDoc </td>
   <td>Het bestand bevat metagegevens die zijn toegepast op het gegenereerde PDF-document. Deze parameter is optioneel.<br /> </td>
  </tr>
 </tbody>
</table>

Met de volgende Java-code wordt een document van ondersteund bestandstype geconverteerd naar een PDF-document.

```java
@Reference GeneratePDFService generatePdfService;
File createPDF(File inputFile, String inputFilename, String fileTypeSettings, String pdfSettings, String securitySettings, File settingsFile, File xmpFile) throws Exception
{
 Transaction tx = OSGiUtils.getTransactionManager().getTransaction();
 // Begin transaction
 if (tx == null)
 OSGiUtils.getTransactionManager().begin();
 String outputFolder="C:/Output"
 Document convertedDoc = null;
 Document inDoc = null;
 Document settingsDoc = null;
 Document xmpDoc = null;
 try
 {
  inDoc = new Document(inputFile);
  if(inputFilename == null || inputFilename.trim().equals("")) {
   throw new Exception("Input file name cannot be null");
  }
  if(inputFileExtension.lastIndexOf('.') == -1) {
   throw new Exception("Input file should have an extension");
  }
  if(settingsFile != null && settingsFile.exists() && settingsFile.isFile())
  settingsDoc = new Document(settingsFile);
  if(xmpFile != null && xmpFile.exists() && xmpFile.isFile())
  xmpDoc = new Document(xmpFile);
  Map result = generatePdfService.createPDF(inDoc, inputFilename, fileTypeSettings, pdfSettings, securitySettings, settingsDoc, xmpDoc);
  convertedDoc = (Document)result.get("ConvertedDoc");
  OSGiUtils.getTransactionManager().commit();
  File outputFile = new File(outputFolder,"Output.pdf");
  doc.copyToFile(outputFile);
  return outputFile;
 }
 catch (Exception e)
 {
  if (OSGiUtils.getTransactionManager().getTransaction() != null)
  OSGiUtils.getTransactionManager().rollback();
  throw e;
 }
 finally {
  if (convertedDoc != null) {
   convertedDoc.dispose();
   convertedDoc = null;
  }
  if (inDoc != null) {
   inDoc.dispose();
   inDoc = null;
  }
  if (settingsDoc != null) {
   settingsDoc.dispose();
   settingsDoc = null;
  }
  if (xmpDoc != null) {
   xmpDoc.dispose();
   xmpDoc = null;
  }
 }
}
```

#### exportPDF {#exportpdf}

Hiermee wordt een PDF-document geconverteerd naar een ondersteund bestandstype. De methode accepteert een PDF als invoer en exporteert de inhoud van de PDF in de opgegeven bestandsindeling.

De service createPDF retourneert een Java.util.Map met resultaten. De kaarttoetsen zijn:

* ConvertedDoc: Het bevat het uitvoerdocument.

De service createPDF genereert de volgende uitzonderingen:

* ConversionException
* InvalidParameterException
* FileFormatNotSupportedException

**Syntaxis:**

```
Map exportPDF(Document inputDoc, String inputFileName, String formatType, Document settingsDoc) throws ConversionException, InvalidParameterException, FileFormatNotSupportedException;
```

#### Invoerparameters {#input-parameters-8}

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td>inputDoc<br /> </td>
   <td>Hiermee geeft u het document op dat u wilt converteren. </td>
  </tr>
  <tr>
   <td>inputFileName<br /> </td>
   <td>De naam van het bestand en de extensie.<br /> </td>
  </tr>
  <tr>
   <td>formatType</td>
   <td>De indeling van het uitvoerbestand voor de exportPDF API.<br /> </td>
  </tr>
  <tr>
   <td>settingsDoc </td>
   <td>Het bestand bevat de configuraties die moeten worden toegepast tijdens het genereren van het uitvoerdocument. Over het algemeen is het een XML-bestand.</td>
  </tr>
 </tbody>
</table>

In het volgende Java-codevoorbeeld wordt een PDF-document geconverteerd naar het opgegeven bestandstype.

```java
(tx == null)
OSGiUtils.getTransactionManager().begin();
String outputFolder="C:/Output"
Document convertedDoc = null;
Document inDoc = null;
Document settingsDoc = null;
try
{
 inDoc = new Document(inputFile);
 if(inputFileName == null || inputFileName.trim().equals("")) {
  throw new Exception("Input file name cannot be null");
 }
 if(inputFileExtension.lastIndexOf('.') == -1) {
  throw new Exception("Input file should have an extension");
 }
 if(settingsFile != null && settingsFile.exists() && settingsFile.isFile())
 settingsDoc = new Document(settingsFile);
 Map result = generatePdfService.exportPDF(inDoc, inputFileName, formatType, settingsDoc);
 convertedDoc = (Document)result.get("ConvertedDoc");
 OSGiUtils.getTransactionManager().commit();
 File outputFile = new File(outputFolder,"OutputFile");
 doc.copyToFile(outputFile);
 return outputFile;
}
catch (Exception e)
{
 if (OSGiUtils.getTransactionManager().getTransaction() != null)
 OSGiUtils.getTransactionManager().rollback();
 throw e;
}
finally {
 if (convertedDoc != null) {
  convertedDoc.dispose();
  convertedDoc = null;
 }
 if (inDoc != null) {
  inDoc.dispose();
  inDoc = null;
 }
 if (settingsDoc != null) {
  settingsDoc.dispose();
  settingsDoc = null;
 }
}
}
```

#### optimaliserenPDF {#optimizepdf}

Met de API OptimizePDF worden PDF-bestanden geoptimaliseerd door de grootte ervan te verkleinen. Het resultaat van deze conversie zijn PDF-bestanden die mogelijk kleiner zijn dan de oorspronkelijke versie. Met deze bewerking worden PDF-documenten ook geconverteerd naar de PDF-versie die is opgegeven in de optimalisatieparameters. Hiermee wordt het OptimizePDFResult-object geretourneerd dat geoptimaliseerde PDF bevat.

De service createPDF genereert de volgende uitzonderingen:

* ConversionException
* InvalidParameterException
* FileFormatNotSupportedException

**Syntaxis:**

```
OptimizePDFResult optimizePDF(Document inputDoc, String fileTypeSettings, Document settingsDoc) throws ConversionException, InvalidParameterException, FileFormatNotSupportedException;
```

#### Invoerparameters {#input-parameters-9}

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td>inputDoc<br /> </td>
   <td>Hiermee geeft u het invoerdocument op. Het is een verplichte parameter.</td>
  </tr>
  <tr>
   <td>fileTypeSettings<br /> </td>
   <td>Het is een optionele parameter.<br /> </td>
  </tr>
  <tr>
   <td>settingsDoc </td>
   <td>Het bestand bevat de instellingen die zijn toegepast tijdens het genereren van het PDF-document (zoals PDF-document optimaliseren voor webweergave) en instellingen die zijn toegepast nadat het PDF-document is gemaakt (zoals Weergave bij openen en Beveiliging). Het is een optionele parameter.<br /> </td>
  </tr>
 </tbody>
</table>

In het volgende Java-codevoorbeeld wordt het invoer-PDF-bestand geoptimaliseerd door de grootte ervan te beperken.

```java
@Reference GeneratePDFService generatePdfService;
File optimizePDF(File inputFile, String fileTypeSettings, File settingsFile) throws Exception
{
 Transaction tx = OSGiUtils.getTransactionManager().getTransaction();
 // Begin transaction
 if (tx == null)
 OSGiUtils.getTransactionManager().begin();
 String outputFolder="C:/Output"
 Document convertedDoc = null;
 Document inDoc = null;
 Document settingsDoc = null;
 try
 {
  inDoc = new Document(inputFile);
  if(settingsFile != null && settingsFile.exists() && settingsFile.isFile())
  settingsDoc = new Document(settingsFile);
  OptimizePDFResult result = generatePdfService.optimizePDF(inDoc, fileTypeSettings, settingsDoc);
  convertedDoc = result.getConvertedDocument();
  OSGiUtils.getTransactionManager().commit();
  File outputFile = new File(outputFolder,"Output.pdf");
  doc.copyToFile(outputFile);
  return outputFile;
 }
 catch (Exception e)
 {
  if (OSGiUtils.getTransactionManager().getTransaction() != null)
  OSGiUtils.getTransactionManager().rollback();
  throw e;
 }
 finally {
  if (convertedDoc != null) {
   convertedDoc.dispose();
   convertedDoc = null;
  }
  if (inDoc != null) {
   inDoc.dispose();
   inDoc = null;
  }
  if (settingsDoc != null) {
   settingsDoc.dispose();
   settingsDoc = null;
  }
 }
}
```

#### htmlToPdf2 {#htmltopdf}

Hiermee converteert u een HTML-pagina naar een PDF-document. De URL van de HTML-pagina wordt als invoer geaccepteerd.

De htmlToPdf2-service retourneert een HtmlToPdfResult-object. U kunt de geconverteerde PDF verkrijgen via result.getConvertedDocument().

De htmlToPdf2 service genereert de volgende uitzonderingen:

* ConversionException
* InvalidParameterException
* FileFormatNotSupportedException

**Syntaxis:**

```
HtmlToPdfResult htmlToPdf2(String inputUrl, String fileTypeSettingsName, String securitySettingsName, Document settingsDoc, Document xmpDoc) throws ConversionException, InvalidParameterException, FileFormatNotSupportedException;
```

#### Invoerparameters {#input-parameters-10}

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td>inputDoc<br /> </td>
   <td>Hiermee geeft u het invoerdocument op. Het is een verplichte parameter.</td>
  </tr>
  <tr>
   <td>fileTypeSettings<br /> </td>
   <td>Het is een optionele parameter.<br /> </td>
  </tr>
  <tr>
   <td>settingsDoc </td>
   <td>Het bestand bevat de instellingen die zijn toegepast tijdens het genereren van het PDF-document (zoals PDF-document optimaliseren voor webweergave) en instellingen die zijn toegepast nadat het PDF-document is gemaakt (zoals Weergave bij openen en Beveiliging). Het is een optionele parameter.<br /> </td>
  </tr>
 </tbody>
</table>

In het volgende Java-codevoorbeeld wordt een HTML-pagina geconverteerd naar een PDF-document.

```java
Reference GeneratePDFService generatePdfService;
File htmlToPdf(String inputUrl, String fileTypeSettingsName, String securitySettingsName, File settingsFile, File xmpFile) throws Exception
{
 Transaction tx = OSGiUtils.getTransactionManager().getTransaction();
 // Begin transaction
 if (tx == null)
 OSGiUtils.getTransactionManager().begin();
 String outputFolder="C:/Output"
 Document convertedDoc = null;
 Document settingsDoc = null;
 Document xmpDoc = null;
 try
 {
  if(settingsFile != null && settingsFile.exists() && settingsFile.isFile())
  settingsDoc = new Document(settingsFile);
  if(xmpFile != null && xmpFile.exists() && xmpFile.isFile())
  xmpDoc = new Document(xmpFile);
  HtmlToPdfResult result = generatePdfService.htmlToPdf2(inputURL, fileTypeSettingsName, securitySettingsName, settingsDoc, xmpDoc);;
  convertedDoc = result.getConvertedDocument();
  OSGiUtils.getTransactionManager().commit();
  File outputFile = new File(outputFolder,"Output.pdf");
  doc.copyToFile(outputFile);
  return outputFile;
 }
 catch (Exception e)
 {
  if (OSGiUtils.getTransactionManager().getTransaction() != null)
  OSGiUtils.getTransactionManager().rollback();
  throw e;
 }
 finally {
  if (convertedDoc != null) {
   convertedDoc.dispose();
   convertedDoc = null;
  }
  if (xmpDoc != null) {
   xmpDoc.dispose();
   xmpDoc = null;
  }
  if (settingsDoc != null) {
   settingsDoc.dispose();
   settingsDoc = null;
  }
 }
}
```

### DistillerService {#distillerservice}

De service Distiller converteert PostScript, Encapsulated PostScript (EPS) en PRN-bestanden (printertekst) naar PDF-bestanden. De Distiller-service wordt vaak gebruikt om grote hoeveelheden gedrukte documenten om te zetten in elektronische documenten, zoals facturen en instructies. Door documenten naar PDF te converteren, kunnen bedrijven hun klanten ook een papieren versie en een elektronische versie van een document sturen. De ondersteunde bestandsindelingen zijn .ps, .eps en .prn. De service ondersteunt de volgende API:

De service createPDF retourneert een Java.util.Map met resultaten. De kaarttoetsen zijn:

* ConvertedDoc: Het bevat het nieuwe PDF-document.
* LogDoc: Het bevat het logbestand.

De service createPDF genereert de volgende uitzonderingen:

* ConversionException
* InvalidParameterException
* FileFormatNotSupportedException

#### createPDF {#createpdf-1}

Hiermee converteert u de ondersteunde indelingen naar PDF-documenten. De methode accepteert bestanden met de indelingen .ps, .eps en .prn als invoer. U kunt specifieke beveiligingsmachtigingen, uitvoerinstellingen en metagegevens toepassen op het PDF-uitvoerdocument.

**Syntaxis:**

```
Map createPDF(Document inputDoc, String inputFileName, String pdfSettings, String securitySettings, Document settingsDoc, Document xmpDoc) throws ConversionException, InvalidParameterException, FileFormatNotSupportedException;
```

#### Invoerparameters {#input-parameters-11}

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td>inputDoc<br /> </td>
   <td>Hiermee geeft u het invoerdocument op. Het is een verplichte parameter.</td>
  </tr>
  <tr>
   <td>inputFileName</td>
   <td>Hier geeft u de volledige naam van het invoerbestand op, samen met de extensie van het bestand. Het is een verplichte parameter.</td>
  </tr>
  <tr>
   <td>pdfSettings</td>
   <td><p>PDF-uitvoerinstellingen voor het geconverteerde document. U kunt alleen de volgende instellingen toepassen:</p>
    <ul>
     <li>Hoge_kwaliteit_Afdrukken<br /> </li>
     <li>PDFA1b_2005_RGB<br /> </li>
     <li>PDFA1b_2005_CMYK<br /> </li>
     <li>PDFX1a_2001<br /> </li>
     <li>PDFX3_2002<br /> </li>
     <li>Press_Quality<br /> </li>
     <li>Kleinste_Bestand_Grootte</li>
    </ul> <p>Het is een optionele parameter.</p> </td>
  </tr>
  <tr>
   <td>securitySettings</td>
   <td><p>Beveiligingsinstellingen voor het geconverteerde document. U kunt de volgende instellingen toepassen:</p>
    <ul>
     <li>Geen beveiliging</li>
     <li>Wachtwoordbeveiliging<br /> </li>
     <li>Certificaatbeveiliging<br /> </li>
     <li>Adobe-beleidsserver</li>
    </ul> <p>Het is een optionele parameter.</p> </td>
  </tr>
  <tr>
   <td>settingsDoc </td>
   <td>Het bestand bevat de instellingen die zijn toegepast tijdens het genereren van het PDF-document (zoals PDF-document optimaliseren voor webweergave) en instellingen die zijn toegepast nadat het PDF-document is gemaakt (zoals Weergave bij openen en Beveiliging). Het is een optionele parameter.<br /> </td>
  </tr>
  <tr>
   <td>xmpDoc </td>
   <td>Het bestand bevat metagegevens voor het gegenereerde PDF-document. Het is een optionele parameter.</td>
  </tr>
 </tbody>
</table>

In het volgende Java-codevoorbeeld worden invoerbestanden van het type PostScript (PS), Encapsulated PostScript (EPS) en printertekstbestanden (PRN) geconverteerd naar PDF-bestanden.

```java
@Reference DistillerService distillerService;
File createPDF(File inputFile, String inputFilename, String pdfSettings, String securitySettings, File settingsFile, File xmpFile) throws Exception
{
 Transaction tx = OSGiUtils.getTransactionManager().getTransaction();
 // Begin transaction
 if (tx == null)
 OSGiUtils.getTransactionManager().begin();
 String outputFolder="C:/Output"
 Document convertedDoc = null;
 Document inDoc = null;
 Document settingsDoc = null;
 Document xmpDoc = null;
 try
 {
  inDoc = new Document(inputFile);
  if(inputFilename == null || inputFilename.trim().equals("")) {
   throw new Exception("Input file name cannot be null");
  }
  if(inputFileExtension.lastIndexOf('.') == -1) {
   throw new Exception("Input file should have an extension");
  }
  if(settingsFile != null && settingsFile.exists() && settingsFile.isFile())
  settingsDoc = new Document(settingsFile);
  if(xmpFile != null && xmpFile.exists() && xmpFile.isFile())
  xmpDoc = new Document(xmpFile);
  Map result = distillerService.createPDF(inDoc, inputFilename, pdfSettings, securitySettings, settingsDoc, xmpDoc);
  convertedDoc = (Document)result.get("ConvertedDoc");
  OSGiUtils.getTransactionManager().commit();
  File outputFile = new File(outputFolder,"Output.pdf");
  doc.copyToFile(outputFile);
  return outputFile;
 }
 catch (Exception e)
 {
  if (OSGiUtils.getTransactionManager().getTransaction() != null)
  OSGiUtils.getTransactionManager().rollback();
  throw e;
 }
 finally {
  if (convertedDoc != null) {
   convertedDoc.dispose();
   convertedDoc = null;
  }
  if (inDoc != null) {
   inDoc.dispose();
   inDoc = null;
  }
  if (settingsDoc != null) {
   settingsDoc.dispose();
   settingsDoc = null;
  }
  if (xmpDoc != null) {
   xmpDoc.dispose();
   xmpDoc = null;
  }
 }
}
```

