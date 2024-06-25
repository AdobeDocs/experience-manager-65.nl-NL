---
title: Reader voor het uitbreiden van met beleid beveiligde PDF-documenten met behulp van Portable Protection Library
description: Met extensies voor Readers kunnen interactieve functies in Adobe PDF-documenten worden ingeschakeld via Acrobat Reader. Met de Portable Protection Library (PPL) kunt u de met DRM beveiligde PDF-documenten uitbreiden.
contentOwner: khsingh
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
feature: Document Security,Reader Extensions
exl-id: fe5d83e8-5e36-4146-a20a-dab2213055e2
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 0%

---

# Reader voor het uitbreiden van met beleid beveiligde PDF-documenten met behulp van Portable Protection Library {#reader-extending-policy-protected-pdf-documents-using-portable-protection-library}

Houd u vertrouwd met concepten als documentbeveiliging, Reader-extensie en de programmeertaal Java om de documenten die met beveiligingsbeleid zijn beveiligd, door het document uit te breiden met PDF.

Met documentbeveiliging kunt u de toegang van specifieke PDF-documenten beperken tot alleen geautoriseerde gebruikers. U kunt ook bepalen hoe een ontvanger een beveiligd document kan gebruiken. U kunt bijvoorbeeld opgeven of ontvangers tekst van een document dat met een beveiligingsbeleid is beveiligd, kunnen afdrukken, kopiëren of bewerken. Ga voor meer informatie over documentbeveiliging naar [over documentbeveiliging](/help/forms/using/admin-help/document-security.md).

Met Reader-extensies kunt u interactieve functies in Adobe PDF-documenten inschakelen via Acrobat Reader. Deze interactieve functies zijn normaal alleen beschikbaar via Adobe Acrobat Professional en Standard. Ga voor meer informatie over de interactieve functies die Reader Extension kan inschakelen naar [Adobe Experience Manager Forms DocAssurance-service ](/help/forms/using/overview-aem-document-services.md)**.**

U kunt de draagbare beveiligingsbibliotheek gebruiken om beleid toe te passen op het document zonder dat u documenten hoeft te lezen via het netwerk. Slechts reizen de veiligheidsgeloofsbrieven en bescherming-beleid details over het netwerk. Het document zelf laat de client nooit over en het beveiligingsbeleid wordt lokaal op de client toegepast.

## Reader documenten uitbreiden die met beveiligingsbeleid zijn beveiligd, PDF {#reader-extending-document-security-policy-protected-pdf-documents}

De documenten die met een beleid zijn beveiligd, zijn versleutelde documenten. U kunt standaard reader-extensie-API&#39;s niet gebruiken om gebruiksrechten van door een beleid beveiligde PDF-documenten toe te passen, te verwijderen en op te halen. Alleen de service Reader Extensions van de Portable Protection Library biedt API&#39;s voor het toepassen, verwijderen en ophalen van gebruiksrechten van PDF-documenten die met beveiligingsbeleid zijn beveiligd.

### Reader Extensions-service {#reader-extensions-service}

De lezer-extensieservice voegt gebruiksrechten toe aan een met een beleid beveiligd PDF-document en activeert functies die normaal niet beschikbaar zijn wanneer een PDF-document wordt geopend met Adobe Acrobat Reader. Het heeft ook APIs om gebruiksrechten van een beleid-beschermd document te verwijderen en terug te winnen.

De dienst van de Uitbreidingen van de Reader steunt volledig PDF documenten die op PDF norm 1.6 en later worden gebaseerd. Behalve Acrobat Reader hebben gebruikers van derden geen extra software of plug-ins nodig om de documenten met beveiliging tegen PDF te kunnen gebruiken.

U kunt de volgende taken met de dienst van de Uitbreidingen van de Reader uitvoeren:

* Pas gebruiksrechten toe op een met beleid beveiligd PDF-document.
* Verwijder gebruiksrechten van een met een beleid beveiligd PDF-document.
* Hiermee worden gebruiksrechten opgehaald die zijn toegepast op een met beleid beveiligd PDF-document.

### Gebruiksrechten toepassen op een met beveiligingsbeleid beveiligd PDF-document {#apply-usage-rights-to-a-document-security-policy-protected-pdf-document}

U kunt de `applyUsageRights`Java API om gebruiksrechten toe te passen op met beleid beveiligde PDF-documenten. Gebruiksrechten hebben betrekking op functionaliteit die standaard beschikbaar is in Acrobat, maar niet in Adobe Reader, zoals de mogelijkheid om opmerkingen toe te voegen aan een formulier of formuliervelden in te vullen en het formulier op te slaan. PDF-documenten waarop gebruiksrechten zijn toegepast, worden documenten met ingeschakelde rechten genoemd. Een gebruiker die een document met ingeschakelde rechten opent in Adobe Reader, kan bewerkingen uitvoeren die zijn ingeschakeld voor dat specifieke document.

**Syntaxis:** `InputStream applyUsageRights(InputStream inputFile, File certFile, String credentialPassword, UsageRights usageRights)`

<table>
 <tbody>
  <tr>
   <td><p><strong>Parameter</strong></p> </td>
   <td><p><strong>Beschrijving</strong></p> </td>
  </tr>
  <tr>
   <td><p>inputFile</p> </td>
   <td><p>Geef InputStream op die het PDF-document vertegenwoordigt waarop gebruiksrechten moeten worden toegepast. U kunt documenten die met LiveCycle Rights Management of AEM Forms-documentbeveiliging zijn beveiligd, gebruiken.</p> </td>
  </tr>
  <tr>
   <td><p>certFile</p> </td>
   <td><p>Geef een File-object op dat een .jks-bestand vertegenwoordigt. Het .jks-bestand is een sleutelarchiefbestand. Het verwijst naar een certificaat dat gebruiksrechten toekent.</p> </td>
  </tr>
  <tr>
   <td><p>credentialPassword</p> </td>
   <td><p>Geef het wachtwoord van het sleutelarchief op. </p> </td>
  </tr>
  <tr>
   <td><p>usageRights</p> </td>
   <td><p>Hiermee wordt een object van het type opgegeven <a href="https://help.adobe.com/en_US/livecycle/11.0/ProgramLC/javadoc/com/adobe/livecycle/readerextensions/client/UsageRights.html" target="_blank">UsageRights</a>. Het object usageRights vertegenwoordigt individuele rechten die kunnen worden toegepast op een met een beleid beveiligd PDF-document.</p> </td>
  </tr>
 </tbody>
</table>

### Hiermee worden gebruiksrechten opgehaald die zijn toegepast op een met beleid beveiligd PDF-document.   {#retrieve-usage-rights-applied-to-a-policy-protected-pdf-document-nbsp}

U kunt de `getDocumentUsageRights`Java API om de gebruiksrechten voor de reader-extensie op te halen die zijn toegepast op een met een beleid beveiligd PDF-document. Door informatie over gebruiksrechten op te halen, kunt u meer weten over de functies die de extensie van de lezer heeft ingeschakeld voor het document PDF dat met een beleid is beveiligd.

**Syntaxis:** `public GetUsageRightsResult getDocumentUsageRights(InputStream inDoc)`

<table>
 <tbody>
  <tr>
   <td><p><strong>Parameter</strong></p> </td>
   <td><p><strong>Beschrijving</strong></p> </td>
  </tr>
  <tr>
   <td><p>inDoc</p> </td>
   <td><p>Geef InputStream op die het PDF-document vertegenwoordigt waaruit gebruiksrechten moeten worden opgehaald. U kunt documenten die met LiveCycle Rights Management of AEM Forms-documentbeveiliging zijn beveiligd, gebruiken.</p> </td>
  </tr>
 </tbody>
</table>

#### Codevoorbeeld {#code-sample}

```java
//Create a ServiceClientFactory instance
ServiceClientFactory factory = ServiceClientFactory.createInstance(connectionProps);
//Create a RightsManagementClient object
RightsManagementClient2 rmClient2= new RightsManagementClient2(factory);

String inputFileName = "C:\\Sample\\protected.pdf"; //Input file can be RM protected or unprotected pdf file
File certFile = new File("C:\\Sample\\cert.jks"); //RE certificate file
String password = "password"; //password for RE certificate
UsageRights usageRights = getUsageRights(true,true,false,false,true,true,false,false,false,false,true);

//RE rights to be applied on the file : FormFillIn, FormDataImportExport, SubmitStandalone, OnlineForms, DynamicFormField, DynamicFormPages, BarcodeDecoding, DigitalSignatures, Comments, CommentsOnline, EmbeddedFiles

InputStream inputFileStream = new FileInputStream(inputFileName);
InputStream output = rmClient2.getRightsManagementReaderExtensionService().applyUsageRights(inputFileStream, certFile, credentialPassword, rights);

String outputFileName = "C:\\Sample\\ReAdded.pdf";
//Save the PDF document
File myFile = new File(outputFileName);
FileOutputStream outputStream = new FileOutputStream(myFile);

int read = 0;
byte[] bytes = new byte[1024];

while ((read = output.read(bytes)) != -1) {

    outputStream.write(bytes, 0, read);
}

System.out.println("UsageRights applied successfully to the document. ");
 outputStream.close();
inputFileStream.close();

//Get Usage Rights for the output pdf document
InputStream fileWithRe = new FileInputStream(myFile);

GetUsageRightsResult usageRights = rmClient2.getRightsManagementReaderExtensionService().getDocumentUsageRights(fileWithRe);

UsageRights rights = usageRights.getRights();
String right1 = rights1.toString();
System.out.println("RE rights for the file are :\n"+right1);
 fileWithRe.close();
```

### Gebruiksrechten van een met een beleid beveiligd PDF-document verwijderen {#remove-usage-rights-of-a-policy-protected-pdf-document}

U kunt de `removeUsageRights`Java API om gebruiksrechten te verwijderen uit een document dat met een beleid is beveiligd. U moet gebruiksrechten verwijderen uit een document met een door een beleid beveiligde PDF om andere AEM Forms-bewerkingen uit te voeren op het document. U moet bijvoorbeeld een PDF-document digitaal ondertekenen (of certificeren) voordat u gebruiksrechten instelt. Daarom als u verrichtingen op een beleid-beschermd document wilt uitvoeren, moet u gebruiksrechten uit het document van de PDF verwijderen, de andere verrichtingen uitvoeren, zoals digitaal het ondertekenen van het document, en dan gebruiksrechten op het document opnieuw toepassen.

**Syntaxis:** `InputStream removeUsageRights(InputStream inputFile)`

<table>
 <tbody>
  <tr>
   <td><p><strong>Parameter</strong></p> </td>
   <td><p><strong>Beschrijving</strong></p> </td>
  </tr>
  <tr>
   <td><p> </p> <p>inputFile</p> </td>
   <td>InputStream opgeven die het PDF-document vertegenwoordigt waarvan het gebruik<br /> de rechten moeten worden geschrapt . U kunt documenten die met LiveCycle Rights Management of AEM Forms-documentbeveiliging zijn beveiligd, gebruiken.</td>
  </tr>
 </tbody>
</table>

#### Codevoorbeeld {#code-sample-1}

```java
//Create a ServiceClientFactory instance
ServiceClientFactory factory = ServiceClientFactory.createInstance(connectionProps);
//Create a RightsManagementClient object
RightsManagementClient2 rmClient2= new RightsManagementClient2(factory);

String inputFileName = "C:\\Sample\\fileWithRe.pdf"; //Input file can be RM protected or unprotected pdf file
InputStream inputFileStream = new FileInputStream(inputFileName);

InputStream fileStream = rmClient2.getRightsManagementReaderExtensionService().removeUsageRights(inputFileStream);

String outputFileName = "C:\\Sample\\ReRemoveded.pdf";
//Save the PDF document
File myFile = new File(outputFileName);
FileOutputStream outputStream = new FileOutputStream(myFile);

int read = 0;
byte[] bytes = new byte[1024];

while ((read = fileStream.read(bytes)) != -1) {

    outputStream.write(bytes, 0, read);
}
System.out.println("RE rights removed successfully from the document.");
outputStream.close();
inputFileStream.close();
```
