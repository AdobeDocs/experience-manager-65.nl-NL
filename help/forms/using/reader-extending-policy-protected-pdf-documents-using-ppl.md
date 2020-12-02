---
title: Reader PDF-documenten die met een beleid zijn beveiligd, uitbreiden met de Portable Protection Library
seo-title: Reader PDF-documenten die met een beleid zijn beveiligd, uitbreiden met de Portable Protection Library
description: Met extensies voor Readers kunnen interactieve functies in Adobe PDF-documenten worden ingeschakeld via Acrobat Reader. Met de Portable Protection Library (PPL) kunt u de met DRM beveiligde PDF-documenten uitbreiden.
seo-description: Met extensies voor Readers kunnen interactieve functies in Adobe PDF-documenten worden ingeschakeld via Acrobat Reader. Met de Portable Protection Library (PPL) kunt u de met DRM beveiligde PDF-documenten uitbreiden.
uuid: 0da17641-d24c-43c2-b918-8b5abe1e5473
contentOwner: khsingh
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
discoiquuid: 83ca522e-d16e-4196-9aa7-84f85de8dee2
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '833'
ht-degree: 0%

---


# Reader PDF-documenten die met een beleid zijn beveiligd, uitbreiden met de Portable Protection Library {#reader-extending-policy-protected-pdf-documents-using-portable-protection-library}

U moet vertrouwd zijn met concepten documentbeveiliging, reader-extensie en de programmeertaal Java om het document met beveiligingsbeleid te kunnen uitbreiden voor PDF-documenten die met een beveiligingsbeleid zijn beveiligd.

Met documentbeveiliging kunt u de toegang van specifieke PDF-documenten beperken tot alleen geautoriseerde gebruikers. U kunt ook bepalen hoe een ontvanger een beveiligd document kan gebruiken. U kunt bijvoorbeeld opgeven of ontvangers tekst van een document dat met een beveiligingsbeleid is beveiligd, kunnen afdrukken, kopiëren of bewerken. Voor meer informatie over documentveiligheid, zie [over documentveiligheid](/help/forms/using/admin-help/document-security.md).

Met Reader-extensies kunt u interactieve functies in Adobe PDF-documenten inschakelen via Acrobat Reader. Deze interactieve functies zijn normaal alleen beschikbaar via Adobe Acrobat Professional en Standard. Zie [Adobe Experience Manager Forms DocAssurance-service ](/help/forms/using/overview-aem-document-services.md)**** voor meer informatie over de interactieve functies die Reader-extensie kan inschakelen.

U kunt de draagbare beveiligingsbibliotheek gebruiken om beleid toe te passen op het document zonder dat u documenten hoeft te lezen via het netwerk. Slechts reizen de veiligheidsgeloofsbrieven en bescherming-beleid details over het netwerk. Het document zelf laat de client nooit over en het beveiligingsbeleid wordt lokaal op de client toegepast.

## Reader voor het uitbreiden van met beveiligingsbeleid beveiligde PDF-documenten {#reader-extending-document-security-policy-protected-pdf-documents}

De documenten die met een beleid zijn beveiligd, zijn versleutelde documenten. U kunt standaard API&#39;s voor leesextensies niet gebruiken om gebruiksrechten van PDF-documenten die met een beleid zijn beveiligd, toe te passen, te verwijderen en op te halen. Alleen de service Reader Extensions van de Portable Protection Library biedt API&#39;s voor het toepassen, verwijderen en ophalen van gebruiksrechten voor PDF-documenten die met beveiligingsbeleid zijn beveiligd.

### Reader Extensions-service {#reader-extensions-service}

De lezer-extensieservice voegt gebruiksrechten toe aan een PDF-document dat met een beleid is beveiligd. Functies die normaal niet beschikbaar zijn wanneer een PDF-document wordt geopend met Adobe Acrobat-Reader, worden geactiveerd. Het heeft ook APIs om gebruiksrechten van een beleid-beschermd document te verwijderen en terug te winnen.

De service Reader Extensions biedt volledige ondersteuning voor PDF-documenten die zijn gebaseerd op PDF-standaard 1.6 en hoger. Behalve Acrobat Reader hebben gebruikers van derden geen extra software of plug-ins nodig om de met een beleid beveiligde PDF-documenten te kunnen gebruiken.

U kunt de volgende taken met de dienst van de Uitbreidingen van de Reader uitvoeren:

* Gebruiksrechten toepassen op een PDF-document dat met een beleid is beveiligd.
* Gebruiksrechten van een met een beleid beveiligd PDF-document verwijderen.
* Haal gebruiksrechten op die zijn toegepast op een PDF-document dat met een beleid is beveiligd.

### Gebruiksrechten toepassen op een met beveiligingsbeleid beveiligd PDF-document {#apply-usage-rights-to-a-document-security-policy-protected-pdf-document}

Met de `applyUsageRights`Java API kunt u gebruiksrechten toepassen op PDF-documenten die met een beleid zijn beveiligd. Gebruiksrechten hebben betrekking op functionaliteit die standaard beschikbaar is in Acrobat, maar niet in Adobe Reader, zoals de mogelijkheid om opmerkingen toe te voegen aan een formulier of formuliervelden in te vullen en het formulier op te slaan. PDF-documenten waarop gebruiksrechten zijn toegepast, worden documenten met ingeschakelde rechten genoemd. Een gebruiker die een document met ingeschakelde rechten opent in Adobe Reader, kan bewerkingen uitvoeren die zijn ingeschakeld voor dat specifieke document.

**Syntaxis:** `InputStream applyUsageRights(InputStream inputFile, File certFile, String credentialPassword, UsageRights usageRights)`

<table>
 <tbody>
  <tr>
   <td><p><strong>Parameter</strong></p> </td>
   <td><p><strong>Beschrijving</strong></p> </td>
  </tr>
  <tr>
   <td><p>inputFile</p> </td>
   <td><p>Geef InputStream op die het PDF-document vertegenwoordigt waarop gebruiksrechten moeten worden toegepast. U kunt documenten met een beveiliging tegen LiveCycle Rights Management of AEM Forms-documenten gebruiken.</p> </td>
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
   <td><p>Hiermee wordt een object van het type <a href="https://help.adobe.com/en_US/livecycle/11.0/ProgramLC/javadoc/com/adobe/livecycle/readerextensions/client/UsageRights.html" target="_blank">UsageRights</a> opgegeven. Het object usageRights vertegenwoordigt individuele rechten die kunnen worden toegepast op een PDF-document dat met een beleid is beveiligd.</p> </td>
  </tr>
 </tbody>
</table>

### Haal gebruiksrechten op die zijn toegepast op een PDF-document dat met een beleid is beveiligd.   {#retrieve-usage-rights-applied-to-a-policy-protected-pdf-document-nbsp}

U kunt de `getDocumentUsageRights`Java API gebruiken om de gebruiksrechten van de reader-extensie op te halen die zijn toegepast op een PDF-document dat met een beleid is beveiligd. Door informatie op te halen over gebruiksrechten, kunt u meer weten over de functies die de extensie van de lezer heeft ingeschakeld voor het PDF-document dat met een beleid is beveiligd.

**Syntaxis:** `public GetUsageRightsResult getDocumentUsageRights(InputStream inDoc)`

<table>
 <tbody>
  <tr>
   <td><p><strong>Parameter</strong></p> </td>
   <td><p><strong>Beschrijving</strong></p> </td>
  </tr>
  <tr>
   <td><p>inDoc</p> </td>
   <td><p>Geef InputStream op die staat voor het PDF-document waaruit gebruiksrechten moeten worden opgehaald. U kunt documenten met een beveiliging tegen LiveCycle Rights Management of AEM Forms-documenten gebruiken.</p> </td>
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

System.out.println("UsageRights applied successfully to the document. ”);
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

Met de `removeUsageRights`Java API kunt u gebruiksrechten verwijderen uit een document dat met een beleid is beveiligd. U moet gebruiksrechten verwijderen uit een PDF-document dat met een beleid is beveiligd, om andere AEM Forms-bewerkingen op het document uit te voeren. U moet bijvoorbeeld een PDF-document digitaal ondertekenen (of certificeren) voordat u gebruiksrechten instelt. Als u bewerkingen wilt uitvoeren op een document dat met een beleid is beveiligd, moet u daarom gebruiksrechten verwijderen uit het PDF-document, de andere bewerkingen uitvoeren, zoals het digitaal ondertekenen van het document, en vervolgens gebruiksrechten opnieuw toepassen op het document.

**Syntaxis:** `InputStream removeUsageRights(InputStream inputFile)`

<table>
 <tbody>
  <tr>
   <td><p><strong>Parameter</strong></p> </td>
   <td><p><strong>Beschrijving</strong></p> </td>
  </tr>
  <tr>
   <td><p> </p> <p>inputFile</p> </td>
   <td>Geef InputStream op die staat voor het PDF-document waaruit gebruikersrechten<br /> moeten worden verwijderd. U kunt documenten met een beveiliging tegen LiveCycle Rights Management of AEM Forms-documenten gebruiken.</td>
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
System.out.println("RE rights removed successfully from the document.”);
outputStream.close();
inputFileStream.close();
```

