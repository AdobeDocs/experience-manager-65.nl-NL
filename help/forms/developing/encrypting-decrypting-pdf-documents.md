---
title: PDF-documenten versleutelen en ontsleutelen
description: Met de coderingsservice kunt u documenten versleutelen en ontsleutelen. De de diensttaken van de Encryptie omvatten het coderen van een document van de PDF met een wachtwoord, het coderen van een document van de PDF met een certificaat, het verwijderen van op wachtwoord-gebaseerde encryptie uit een document van de PDF, het verwijderen van op certificaat-gebaseerde encryptie uit een document van de PDF, het ontgrendelen van het document van de PDF zodat andere de dienstverrichtingen kunnen worden uitgevoerd, en het bepalen van het encryptietype van een beveiligd PDF.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: d3cbca7f-9277-4d61-b198-abf4bb008f15
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services,APIs & Integrations
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '8133'
ht-degree: 0%

---

# PDF-documenten versleutelen en ontsleutelen {#encrypting-and-decrypting-pdf-documents}

**de Steekproeven en de voorbeelden in dit document zijn slechts voor AEM Forms op milieu JEE.**

**Ongeveer de Dienst van de Encryptie**

Met de coderingsservice kunt u documenten versleutelen en decoderen. Wanneer een document wordt versleuteld, wordt de inhoud ervan onleesbaar. Een geautoriseerde gebruiker kan het document decoderen om toegang tot de inhoud te krijgen. Als een PDF-document met een wachtwoord is versleuteld, moet de gebruiker het wachtwoord voor openen opgeven voordat het document in Adobe Reader of Adobe Acrobat kan worden weergegeven. Als een PDF-document met een certificaat is versleuteld, moet de gebruiker het PDF-document decoderen met de openbare sleutel die overeenkomt met het certificaat (de persoonlijke sleutel) waarmee het PDF-document is versleuteld.

U kunt deze taken uitvoeren met behulp van de coderingsservice:

* Codeer een PDF-document met een wachtwoord. (Zie [&#x200B; Coderend de Documenten van PDF met een Wachtwoord &#x200B;](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password).)
* Codeer een PDF-document met een certificaat. (Zie [&#x200B; Coderend de Documenten van PDF met Certificaten &#x200B;](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-certificates).)
* Verwijder op wachtwoord gebaseerde versleuteling uit een PDF-document. (Zie [&#x200B; het Verwijderen van de Encryptie van het Wachtwoord &#x200B;](encrypting-decrypting-pdf-documents.md#removing-password-encryption).)
* Verwijder op een certificaat gebaseerde versleuteling uit een PDF-document. (Zie [&#x200B; het Verwijderen van Certificaat Gebaseerde Encryptie &#x200B;](encrypting-decrypting-pdf-documents.md#removing-certificate-based-encryption).)
* Ontgrendel het document van de PDF zodat andere de dienstverrichtingen kunnen worden uitgevoerd. Nadat een met een wachtwoord gecodeerd PDF-document bijvoorbeeld is ontgrendeld, kunt u er een digitale handtekening op toepassen. (Zie [&#x200B; ontgrendelen de Gecodeerde Documenten van PDF &#x200B;](encrypting-decrypting-pdf-documents.md#unlocking-encrypted-pdf-documents).)
* Bepaal het versleutelingstype van een beveiligd PDF-document. (Zie [&#x200B; Bepalend Type van Encryptie &#x200B;](encrypting-decrypting-pdf-documents.md#determining-encryption-type).)

>[!NOTE]
>
>Voor meer informatie over de dienst van de Encryptie, zie [&#x200B; Verwijzing van de Diensten voor AEM Forms &#x200B;](https://www.adobe.com/go/learn_aemforms_services_63).

## PDF-documenten versleutelen met een wachtwoord {#encrypting-pdf-documents-with-a-password}

Wanneer u een PDF-document versleutelt met een wachtwoord, moet een gebruiker het wachtwoord opgeven om het PDF-document te openen in Adobe Reader of Acrobat. Voordat een andere AEM Forms-bewerking, zoals het digitaal ondertekenen van het PDF-document, op het document kan worden uitgevoerd, moet een met wachtwoord gecodeerd PDF-document worden ontgrendeld.

>[!NOTE]
>
>Als u een gecodeerd PDF-document uploadt naar de AEM Forms-opslagplaats, kan het PDF-document niet worden gedecodeerd en de XDP-inhoud niet worden uitgepakt. U wordt aangeraden een document niet te coderen voordat u het uploadt naar de AEM Forms-opslagplaats. (Zie [&#x200B; schrijvend Middelen &#x200B;](/help/forms/developing/aem-forms-repository.md#writing-resources).)

>[!NOTE]
>
>Voor meer informatie over de dienst van de Encryptie, zie [&#x200B; Verwijzing van de Diensten voor AEM Forms &#x200B;](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary-of-steps}

Voer de volgende stappen uit om een PDF-document met een wachtwoord te coderen:

1. Inclusief projectbestanden.
1. Maak een Encryption Client API-object.
1. Een PDF-document ophalen om te versleutelen.
1. Stel opties voor codering tijdens runtime in.
1. Voeg het wachtwoord toe.
1. Sla het gecodeerde PDF-document op als een PDF-bestand.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

**creeer een voorwerp van de Cliënt van de Encryptie API**

Om programmatically een de dienstverrichting van de Encryptie uit te voeren, moet u een de dienstcliënt van de Encryptie tot stand brengen.

**krijg een te coderen document van PDF**

Verkrijg een niet-gecodeerd document van de PDF om het document met een wachtwoord te coderen. Als u probeert een PDF-document te beveiligen dat al is versleuteld, veroorzaakt u een uitzondering.

**vastgestelde encryptie runtime opties**

Als u een PDF-document met een wachtwoord wilt versleutelen, geeft u vier waarden op, waaronder twee wachtwoordwaarden. Het eerste wachtwoord wordt gebruikt om het PDF-document te versleutelen en moet worden opgegeven bij het openen van het PDF-document. De tweede wachtwoordwaarde, die de hoofdwachtwoordwaarde wordt genoemd, wordt gebruikt om encryptie uit het document van de PDF te verwijderen. Wachtwoordwaarden zijn hoofdlettergevoelig en deze twee wachtwoordwaarden kunnen niet dezelfde waarden zijn.

Geef de bronnen voor het PDF-document op die u wilt versleutelen. U kunt het volledige document van de PDF, alles behalve de meta-gegevens van het document, of enkel de gehechtheid van het document coderen. Als u alleen de bijlagen van het document versleutelt, wordt een gebruiker om een wachtwoord gevraagd wanneer hij of zij de bestandsbijlagen wil openen.

Wanneer u een PDF-document versleutelt, kunt u machtigingen opgeven die aan het beveiligde document zijn gekoppeld. Door machtigingen op te geven, kunt u de handelingen beheren die een gebruiker die een met een wachtwoord gecodeerd PDF-document opent, mag uitvoeren. Als u bijvoorbeeld met succes formuliergegevens wilt extraheren, moet u de volgende machtigingen instellen:

* PASSWORD_EDIT_ADD
* WACHTWOORD_EDIT_MODIFY

>[!NOTE]
>
>Machtigingen worden opgegeven als `PasswordEncryptionPermission` opsommingswaarden.

**voeg het wachtwoord** toe

Nadat u een onbeveiligd PDF-document hebt opgehaald en waarden voor de codering hebt ingesteld, kunt u een wachtwoord toevoegen aan het PDF-document.

**sparen het gecodeerde document van PDF als dossier van PDF**

U kunt het met een wachtwoord gecodeerde PDF-document opslaan als een PDF-bestand.

**zie ook**

[Een PDF-document versleutelen met de Java API](encrypting-decrypting-pdf-documents.md#encrypt-a-pdf-document-using-the-java-api)

[Een PDF-document versleutelen met de API voor webservices](encrypting-decrypting-pdf-documents.md#encrypting-a-pdf-document-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[API voor coderingsservice - Snel aan de slag](/help/forms/developing/encryption-service-java-api-quick.md#encryption-service-java-api-quick-start-soap)

[PDF-documenten versleutelen met certificaten](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-certificates)

### Een PDF-document versleutelen met de Java API {#encrypt-a-pdf-document-using-the-java-api}

Codeer een PDF-document met een wachtwoord met behulp van de API voor versleuteling (Java):

1. Inclusief projectbestanden.

   Neem JAR-bestanden van de client, zoals adobe-encryption-client.jar, op in het klassenpad van uw Java-project.

1. Maak een versleutelingsclient-API.

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `EncryptionServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Een PDF-document ophalen om te versleutelen.

   * Maak een `java.io.FileInputStream` -object dat staat voor het PDF-document dat moet worden gecodeerd met de constructor ervan en geef een tekenreekswaarde door die de locatie van het PDF-document aangeeft.
   * Maak een `com.adobe.idp.Document` -object door de constructor ervan te gebruiken en het `java.io.FileInputStream` -object door te geven.

1. Stel opties voor codering tijdens runtime in.

   * Maak een `PasswordEncryptionOptionSpec` -object door de constructor ervan aan te roepen.
   * Geef de bronnen van het PDF-document op die moeten worden gecodeerd door de methode `setEncryptOption` van het `PasswordEncryptionOptionSpec` -object aan te roepen en een opsommingswaarde `PasswordEncryptionOption` door te geven die de documentbronnen aangeeft die moeten worden gecodeerd. Als u bijvoorbeeld het gehele PDF-document wilt versleutelen, inclusief de metagegevens en de bijlagen, geeft u `PasswordEncryptionOption.ALL` op.
   * Maak een `java.util.List` -object dat de versleutelingsmachtigingen opslaat met de `ArrayList` -constructor.
   * Geef een machtiging op door de methode `add` van het object `java.util.List` aan te roepen en een opsommingswaarde door te geven die overeenkomt met de machtiging die u wilt instellen. Als u bijvoorbeeld de machtiging wilt instellen waarmee een gebruiker gegevens in het PDF-document kan kopiëren, geeft u `PasswordEncryptionPermission.PASSWORD_EDIT_COPY` op. (Herhaal deze stap voor elke machtiging die moet worden ingesteld).
   * Geef de Acrobat-compatibiliteitsoptie op door de methode `setCompatability` van het `PasswordEncryptionOptionSpec` -object op te roepen en een opsommingswaarde door te geven die het Acrobat-compatibiliteitsniveau opgeeft. U kunt bijvoorbeeld `PasswordEncryptionCompatability.ACRO_7` opgeven.
   * Geef de wachtwoordwaarde op waarmee een gebruiker het gecodeerde PDF-document kan openen door de methode `setDocumentOpenPassword` van het object `PasswordEncryptionOptionSpec` aan te roepen en een tekenreekswaarde door te geven die het open wachtwoord vertegenwoordigt.
   * Geef de waarde van het hoofdwachtwoord op waarmee een gebruiker de versleuteling uit het PDF-document kan verwijderen door de methode `setPermissionPassword` van het object `PasswordEncryptionOptionSpec` aan te roepen en een tekenreekswaarde door te geven die het hoofdwachtwoord vertegenwoordigt.

1. Voeg het wachtwoord toe.

   Codeer het PDF-document door de methode `encryptPDFUsingPassword` van het object `EncryptionServiceClient` aan te roepen en de volgende waarden door te geven:

   * Het `com.adobe.idp.Document` -object dat het PDF-document bevat dat met het wachtwoord moet worden gecodeerd.
   * Het `PasswordEncryptionOptionSpec` -object dat opties voor codering tijdens runtime bevat.

   De methode `encryptPDFUsingPassword` retourneert een `com.adobe.idp.Document` -object dat een met een wachtwoord gecodeerd PDF-document bevat.

1. Sla het gecodeerde PDF-document op als een PDF-bestand.

   * Maak een `java.io.File` -object en controleer of de bestandsextensie .pdf is.
   * Roep de methode `copyToFile` van het object `com.adobe.idp.Document` aan om de inhoud van het object `com.adobe.idp.Document` naar het bestand te kopiëren. Gebruik het object `com.adobe.idp.Document` dat door de methode `encryptPDFUsingPassword` is geretourneerd.

**zie ook**

[Overzicht van de stappen](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[Snel starten (SOAP modus): Een PDF-document versleutelen met de Java API](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-encrypting-a-pdf-document-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)


[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een PDF-document versleutelen met de API voor webservices {#encrypting-a-pdf-document-using-the-web-service-api}

Codeer een PDF-document met een wachtwoord met behulp van de API voor versleuteling (webservice):

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Gebruik de volgende WSDL-definitie: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1` .

   >[!NOTE]
   >
   >Vervang `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Encryption Client API-object.

   * Maak een `EncryptionServiceClient` -object met de standaardconstructor.
   * Maak een `EncryptionServiceClient.Endpoint.Address` -object met de `System.ServiceModel.EndpointAddress` -constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/EncryptionService?WSDL` .) U hoeft het attribuut `lc_version` niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Maak een `System.ServiceModel.BasicHttpBinding` -object door de waarde van het `EncryptionServiceClient.Endpoint.Binding` -veld op te halen. De geretourneerde waarde wordt gecast naar `BasicHttpBinding` .
   * Stel het veld `MessageEncoding` van het `System.ServiceModel.BasicHttpBinding` -object in op `WSMessageEncoding.Mtom` . Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld `EncryptionServiceClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de bijbehorende wachtwoordwaarde toe aan het veld `EncryptionServiceClient.ClientCredentials.UserName.Password` .
      * Wijs de constante waarde `HttpClientCredentialType.Basic` toe aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType` .
      * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` toe aan het veld `BasicHttpBindingSecurity.Security.Mode` .

1. Een PDF-document ophalen om te versleutelen.

   * Maak een `BLOB` -object met behulp van de constructor. Het `BLOB` -object wordt gebruikt om een PDF-document op te slaan dat met een wachtwoord is versleuteld.
   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het te coderen PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `Length` van het object `System.IO.FileStream` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` -object door de inhoud van de bytearray toe te wijzen aan het gegevenslid van het `BLOB` object `MTOM` .

1. Stel opties voor codering tijdens runtime in.

   * Maak een `PasswordEncryptionOptionSpec` -object met behulp van de constructor.
   * Geef de PDF-documentbronnen op die moeten worden gecodeerd door een `PasswordEncryptionOption` -opsommingswaarde toe te wijzen aan het gegevenslid van het `PasswordEncryptionOptionSpec` object `encryptOption` . Als u de volledige PDF wilt coderen, inclusief de metagegevens en de bijlagen, wijst u `PasswordEncryptionOption.ALL` toe aan dit gegevenslid.
   * Geef de compatibiliteitsoptie Acrobat op door een opsommingswaarde `PasswordEncryptionCompatability` toe te wijzen aan het gegevenslid van het `PasswordEncryptionOptionSpec` object `compatability` . Wijs bijvoorbeeld `PasswordEncryptionCompatability.ACRO_7` toe aan dit gegevenslid.
   * Geef de wachtwoordwaarde op waarmee een gebruiker het gecodeerde PDF-document kan openen door een tekenreekswaarde toe te wijzen die het open wachtwoord vertegenwoordigt voor het `documentOpenPassword` -gegevenslid van het `PasswordEncryptionOptionSpec` -object.
   * Geef de wachtwoordwaarde op waarmee een gebruiker versleuteling uit het PDF-document kan verwijderen door een tekenreekswaarde toe te wijzen die het hoofdwachtwoord vertegenwoordigt aan het `permissionPassword` -gegevenslid van het `PasswordEncryptionOptionSpec` -object.

1. Voeg het wachtwoord toe.

   Codeer het PDF-document door de methode `encryptPDFUsingPassword` van het object `EncryptionServiceClient` aan te roepen en de volgende waarden door te geven:

   * Het `BLOB` -object dat het PDF-document bevat dat met het wachtwoord moet worden gecodeerd.
   * Het `PasswordEncryptionOptionSpec` -object dat opties voor codering tijdens runtime bevat.

   De methode `encryptPDFUsingPassword` retourneert een `BLOB` -object dat een met een wachtwoord gecodeerd PDF-document bevat.

1. Sla het gecodeerde PDF-document op als een PDF-bestand.

   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het beveiligde PDF-document vertegenwoordigt.
   * Maak een bytearray waarin de gegevensinhoud wordt opgeslagen van het object `BLOB` dat door de methode `encryptPDFUsingPassword` is geretourneerd. Vul de bytearray met de waarde van het gegevenslid `MTOM` van het object `BLOB` .
   * Maak een `System.IO.BinaryWriter` -object door de constructor ervan aan te roepen en het `System.IO.FileStream` -object door te geven.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door de methode `Write` van het object `System.IO.BinaryWriter` aan te roepen en de bytearray door te geven.

**zie ook**

[Overzicht van de stappen](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## PDF-documenten versleutelen met certificaten {#encrypting-pdf-documents-with-certificates}

Met codering op basis van certificaten kunt u een document voor specifieke ontvangers versleutelen met behulp van technologie voor openbare sleutels. Verschillende ontvangers kunnen verschillende machtigingen voor het document krijgen. Veel aspecten van versleuteling worden mogelijk gemaakt door de technologie van de openbare sleutel. Een algoritme wordt gebruikt om twee grote aantallen te produceren, die als *sleutels* worden bekend, die de volgende eigenschappen hebben:

* Eén sleutel wordt gebruikt om een set gegevens te coderen. Vervolgens kan alleen de andere sleutel worden gebruikt om de gegevens te decoderen.
* Het is onmogelijk om de ene sleutel van de andere te onderscheiden.

Een van de toetsen fungeert als de persoonlijke sleutel van een gebruiker. Het is belangrijk dat alleen de gebruiker toegang heeft tot deze sleutel. De andere sleutel is de openbare sleutel van de gebruiker, die met anderen kan worden gedeeld.

Een certificaat met een openbare sleutel bevat de openbare sleutel van een gebruiker en identificeert informatie. De indeling X.509 wordt gebruikt voor het opslaan van certificaten. Certificaten worden doorgaans uitgegeven en digitaal ondertekend door een certificeringsinstantie (CA), een erkende entiteit die een zekere mate van vertrouwen biedt in de geldigheid van het certificaat. Certificaten hebben een vervaldatum waarna ze niet meer geldig zijn. Bovendien bevatten de certificaatintrekkingslijsten (CRL&#39;s) informatie over certificaten die vóór de vervaldatum zijn ingetrokken. CRL&#39;s worden periodiek gepubliceerd door certificeringsinstanties. De intrekkingsstatus van een certificaat kan ook via het online certificaatstatusprotocol (OCSP) via het netwerk worden opgehaald.

>[!NOTE]
>
>Als u een gecodeerd PDF-document uploadt naar de AEM Forms-opslagplaats, kan het PDF-document niet worden gedecodeerd en de XDP-inhoud niet worden uitgepakt. U wordt aangeraden een document niet te coderen voordat u het uploadt naar de AEM Forms-opslagplaats. (Zie [&#x200B; schrijvend Middelen &#x200B;](/help/forms/developing/aem-forms-repository.md#writing-resources).)

>[!NOTE]
>
>Voordat u een PDF-document kunt versleutelen met een certificaat, moet u ervoor zorgen dat u het certificaat toevoegt aan AEM Forms. Een certificaat wordt toegevoegd gebruikend beleidsconsole of programmatically gebruikend de Manager API van het Vertrouwen. (Zie [&#x200B; het Invoeren Referenties door de Manager API van het Vertrouwen te gebruiken &#x200B;](/help/forms/developing/credentials.md#importing-credentials-by-using-the-trust-manager-api).)

>[!NOTE]
>
>Voor meer informatie over de dienst van de Encryptie, zie [&#x200B; Verwijzing van de Diensten voor AEM Forms &#x200B;](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-1}

Voer de volgende stappen uit om een PDF-document te versleutelen met een certificaat:

1. Inclusief projectbestanden.
1. Maak een Encryption Client API-object.
1. Een PDF-document ophalen om te versleutelen.
1. Verwijs naar het certificaat.
1. Stel opties voor codering tijdens runtime in.
1. Maak een met een certificaat gecodeerd PDF-document.
1. Sla het gecodeerde PDF-document op als een PDF-bestand.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)

**creeer een voorwerp van de Cliënt van de Encryptie API**

Om programmatically een de dienstverrichting van de Encryptie uit te voeren, moet u een de dienstcliënt van de Encryptie tot stand brengen. Als u de Java Encryption Service API gebruikt, maakt u een `EncrytionServiceClient` -object. Als u de webservice-API gebruikt, maakt u een `EncryptionServiceService` -object.

**krijg een te coderen document van PDF**

Vraag een niet-gecodeerd PDF-document aan om te versleutelen. Als u probeert een PDF-document te beveiligen dat al is versleuteld, wordt een uitzondering gegenereerd.

**Verwijzing het certificaat**

Als u een PDF-document wilt versleutelen met een certificaat, verwijst u naar een certificaat dat wordt gebruikt om een PDF-document te versleutelen. Het certificaat is een .cer-bestand, een .crt-bestand of een .pem-bestand. Een PKCS#12-bestand wordt gebruikt voor het opslaan van persoonlijke sleutels met de bijbehorende certificaten.

Wanneer u een PDF-document versleutelt met een certificaat, geeft u de machtigingen op die aan het beveiligde document zijn gekoppeld. Door machtigingen op te geven, kunt u de handelingen beheren die een gebruiker die een met een certificaat gecodeerd PDF-document opent, kan uitvoeren.

**vastgestelde encryptie runtime opties**

Geef de bronnen voor het PDF-document op die u wilt versleutelen. U kunt het volledige document van de PDF, alles behalve de meta-gegevens van het document, of slechts de gehechtheid van het document coderen.

**creeer een certificaat-gecodeerd document van de PDF**

Nadat u een onbeveiligd PDF-document hebt opgehaald, naar het certificaat verwijst en uitvoeringsopties hebt ingesteld, kunt u een met een certificaat gecodeerd PDF-document maken. Nadat het PDF-document is versleuteld, hebt u de bijbehorende openbare sleutel nodig om het te decoderen.

**sparen het gecodeerde document van PDF als dossier van PDF**

U kunt het gecodeerde PDF-document opslaan als een PDF-bestand.

**zie ook**

[Een PDF-document versleutelen met een certificaat met de Java API](encrypting-decrypting-pdf-documents.md#encrypt-a-pdf-document-with-a-certificate-using-the-java-api)

[Een PDF-document versleutelen met een certificaat met de webservice-API](encrypting-decrypting-pdf-documents.md#encrypt-a-pdf-document-with-a-certificate-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[API voor coderingsservice - Snel aan de slag](/help/forms/developing/encryption-service-java-api-quick.md#encryption-service-java-api-quick-start-soap)

[PDF-documenten versleutelen met een wachtwoord](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password)

### Een PDF-document versleutelen met een certificaat met de Java API {#encrypt-a-pdf-document-with-a-certificate-using-the-java-api}

Codeer een PDF-document met een certificaat met behulp van de API voor versleuteling (Java):

1. Inclusief projectbestanden.

   Neem JAR-bestanden van de client, zoals adobe-encryption-client.jar, op in het klassenpad van uw Java-project.

1. Maak een Encryption Client API-object.

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `EncryptionServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Een PDF-document ophalen om te versleutelen.

   * Maak een `java.io.FileInputStream` -object dat staat voor het PDF-document dat moet worden gecodeerd met de constructor ervan en geef een tekenreekswaarde door die de locatie van het PDF-document aangeeft.
   * Maak een `com.adobe.idp.Document` -object door de constructor ervan te gebruiken en het `java.io.FileInputStream` -object door te geven.

1. Verwijs naar het certificaat.

   * Maak een `java.util.List` -object dat machtigingsinformatie opslaat met de constructor ervan.
   * Geef de machtigingen op die aan het gecodeerde document zijn gekoppeld door de methode `add` van het object `java.util.List` aan te roepen en een opsommingswaarde `CertificateEncryptionPermissions` door te geven die de machtigingen vertegenwoordigt die zijn verleend aan de gebruiker die het beveiligde PDF-document opent. Wanneer u bijvoorbeeld alle machtigingen wilt opgeven, geeft u `CertificateEncryptionPermissions.PKI_ALL_PERM` door.
   * Maak een `Recipient` -object met behulp van de constructor.
   * Maak een `java.io.FileInputStream` -object dat het certificaat vertegenwoordigt dat wordt gebruikt om het PDF-document te versleutelen met behulp van de constructor ervan en door het doorgeven van een tekenreekswaarde die de locatie van het certificaat opgeeft.
   * Maak een `com.adobe.idp.Document` -object met behulp van de constructor en geef het `java.io.FileInputStream` -object door dat het certificaat vertegenwoordigt.
   * Roep de methode `setX509Cert` van het object `Recipient` aan en geef het object `com.adobe.idp.Document` met het certificaat door. (Bovendien kan het `Recipient` voorwerp een alias van het Certificaat van Truststore of LDAP URL als certificaatbron hebben.)
   * Maak een `CertificateEncryptionIdentity` -object dat machtiging- en certificaatgegevens opslaat met de constructor ervan.
   * Roep de methode `setPerms` van het `CertificateEncryptionIdentity` -object aan en geef het `java.util.List` -object door dat machtigingsgegevens opslaat.
   * Roep de methode `setRecipient` van het object `CertificateEncryptionIdentity` aan en geef het object `Recipient` door waarin certificaatgegevens zijn opgeslagen.
   * Maak een `java.util.List` -object dat certificaatinformatie opslaat met behulp van de constructor.
   * Roep de methode add van het object `java.util.List` aan en geef het object `CertificateEncryptionIdentity` door. (Dit `java.util.List` -object wordt als een parameter aan de methode `encryptPDFUsingCertificates` doorgegeven.)

1. Stel opties voor codering tijdens runtime in.

   * Maak een `CertificateEncryptionOptionSpec` -object door de constructor ervan aan te roepen.
   * Geef de bronnen van het PDF-document op die moeten worden gecodeerd door de methode `setOption` van het `CertificateEncryptionOptionSpec` -object aan te roepen en een opsommingswaarde `CertificateEncryptionOption` door te geven die de documentbronnen aangeeft die moeten worden gecodeerd. Als u bijvoorbeeld het gehele PDF-document wilt versleutelen, inclusief de metagegevens en de bijlagen, geeft u `CertificateEncryptionOption.ALL` op.
   * Geef de compatibiliteitsoptie Acrobat op door de methode `setCompat` van het `CertificateEncryptionOptionSpec` -object op te roepen en een opsommingswaarde `CertificateEncryptionCompatibility` door te geven die het Acrobat-compatibiliteitsniveau opgeeft. U kunt bijvoorbeeld `CertificateEncryptionCompatibility.ACRO_7` opgeven.

1. Maak een met een certificaat gecodeerd PDF-document.

   Codeer het PDF-document met een certificaat door de methode `encryptPDFUsingCertificates` van het object `EncryptionServiceClient` aan te roepen en de volgende waarden door te geven:

   * Het `com.adobe.idp.Document` -object dat het te coderen PDF-document bevat.
   * Het `java.util.List` -object dat certificaatinformatie opslaat.
   * Het `CertificateEncryptionOptionSpec` -object dat opties voor codering tijdens runtime bevat.

   De methode `encryptPDFUsingCertificates` retourneert een `com.adobe.idp.Document` -object dat een met een certificaat gecodeerd PDF-document bevat.

1. Sla het gecodeerde PDF-document op als een PDF-bestand.

   * Maak een `java.io.File` -object en controleer of de bestandsnaamextensie .pdf is.
   * Roep de methode `copyToFile` van het object `com.adobe.idp.Document` aan om de inhoud van het object `com.adobe.idp.Document` naar het bestand te kopiëren. Gebruik het object `com.adobe.idp.Document` dat door de methode `encryptPDFUsingCertificates` is geretourneerd.

**zie ook**

[Overzicht van de stappen](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[Snel starten (SOAP modus): Een PDF-document coderen met een certificaat met de Java API](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-encrypting-a-pdf-document-with-a-certificate-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een PDF-document versleutelen met een certificaat met de webservice-API {#encrypt-a-pdf-document-with-a-certificate-using-the-web-service-api}

Codeer een PDF-document met een certificaat met behulp van de API voor versleuteling (webservice):

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Gebruik de volgende WSDL-definitie: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1` .

   >[!NOTE]
   >
   >Vervang `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Encryption Client API-object.

   * Maak een `EncryptionServiceClient` -object met de standaardconstructor.
   * Maak een `EncryptionServiceClient.Endpoint.Address` -object met de `System.ServiceModel.EndpointAddress` -constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/EncryptionService?WSDL` .) U hoeft het attribuut `lc_version` niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Maak een `System.ServiceModel.BasicHttpBinding` -object door de waarde van het `EncryptionServiceClient.Endpoint.Binding` -veld op te halen. De geretourneerde waarde wordt gecast naar `BasicHttpBinding` .
   * Stel het veld `MessageEncoding` van het `System.ServiceModel.BasicHttpBinding` -object in op `WSMessageEncoding.Mtom` . Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld `EncryptionServiceClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de bijbehorende wachtwoordwaarde toe aan het veld `EncryptionServiceClient.ClientCredentials.UserName.Password` .
      * Wijs de constante waarde `HttpClientCredentialType.Basic` toe aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType` .
      * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` toe aan het veld `BasicHttpBindingSecurity.Security.Mode` .

1. Een PDF-document ophalen om te versleutelen.

   * Maak een `BLOB` -object met behulp van de constructor. Het `BLOB` -object wordt gebruikt om een PDF-document op te slaan dat met een certificaat is versleuteld.
   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het te coderen PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `Length` van het object `System.IO.FileStream` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het object `BLOB` door de eigenschap `MTOM` ervan toe te wijzen met de inhoud van de bytearray.

1. Verwijs naar het certificaat.

   * Maak een `Recipient` -object met behulp van de constructor. In dit object worden certificaatgegevens opgeslagen.
   * Maak een `BLOB` -object met behulp van de constructor. In dit `BLOB` -object wordt het certificaat opgeslagen waarmee het PDF-document wordt versleuteld.
   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het certificaat en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `Length` van het object `System.IO.FileStream` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` -object door de inhoud van de bytearray toe te wijzen aan het gegevenslid van het `BLOB` object `MTOM` .
   * Wijs het `BLOB` -object toe dat het certificaat opslaat naar het gegevenslid van het `Recipient` object `x509Cert` .
   * Maak een `CertificateEncryptionIdentity` -object dat certificaatinformatie opslaat met behulp van de constructor.
   * Wijs het `Recipient` voorwerp toe dat het certificaat aan het `CertificateEncryptionIdentity` ontvankelijke gegevenslid van objecten &lbrace;opslaat.
   * Maak een array `Object` en wijs het object `CertificateEncryptionIdentity` toe aan het eerste element van de array `Object` . Deze `Object` -array wordt als een parameter aan de `encryptPDFUsingCertificates` -methode doorgegeven.

1. Stel opties voor codering tijdens runtime in.

   * Maak een `CertificateEncryptionOptionSpec` -object met behulp van de constructor.
   * Geef de PDF-documentbronnen op die moeten worden gecodeerd door een `CertificateEncryptionOption` -opsommingswaarde toe te wijzen aan het gegevenslid van het `CertificateEncryptionOptionSpec` object `option` . Als u het gehele PDF-document wilt versleutelen, inclusief de metagegevens en de bijlagen, wijst u `CertificateEncryptionOption.ALL` toe aan dit gegevenslid.
   * Geef de compatibiliteitsoptie Acrobat op door een opsommingswaarde `CertificateEncryptionCompatibility` toe te wijzen aan het gegevenslid van het `CertificateEncryptionOptionSpec` object `compat` . Wijs bijvoorbeeld `CertificateEncryptionCompatibility.ACRO_7` toe aan dit gegevenslid.

1. Maak een met een certificaat gecodeerd PDF-document.

   Codeer het PDF-document met een certificaat door de methode `encryptPDFUsingCertificates` van het object `EncryptionServiceService` aan te roepen en de volgende waarden door te geven:

   * Het `BLOB` -object dat het te coderen PDF-document bevat.
   * De array `Object` die certificaatinformatie opslaat.
   * Het `CertificateEncryptionOptionSpec` -object dat opties voor codering tijdens runtime bevat.

   De methode `encryptPDFUsingCertificates` retourneert een `BLOB` -object dat een met een certificaat gecodeerd PDF-document bevat.

1. Sla het gecodeerde PDF-document op als een PDF-bestand.

   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het beveiligde PDF-document vertegenwoordigt.
   * Maak een bytearray waarin de gegevensinhoud wordt opgeslagen van het object `BLOB` dat door de methode `encryptPDFUsingCertificates` is geretourneerd. Vul de bytearray met de waarde van het gegevenslid `binaryData` van het object `BLOB` .
   * Maak een `System.IO.BinaryWriter` -object door de constructor ervan aan te roepen en het `System.IO.FileStream` -object door te geven.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door de methode `Write` van het object `System.IO.BinaryWriter` aan te roepen en de bytearray door te geven.

**zie ook**

[Overzicht van de stappen](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Versleuteling op basis van een certificaat verwijderen {#removing-certificate-based-encryption}

Op een certificaat gebaseerde versleuteling kan uit een PDF-document worden verwijderd, zodat gebruikers het PDF-document in Adobe Reader of Acrobat kunnen openen. Als u versleuteling wilt verwijderen uit een PDF-document dat is versleuteld met een certificaat, moet naar een openbare sleutel worden verwezen. Nadat de versleuteling is verwijderd uit een PDF-document, is het niet meer beveiligd.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Encryptie, zie [&#x200B; Verwijzing van de Diensten voor AEM Forms &#x200B;](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-2}

Voer de volgende stappen uit om op een certificaat gebaseerde versleuteling te verwijderen uit een PDF-document:

1. Inclusief projectbestanden.
1. Maak een versleutelingsserviceclient.
1. Hiermee wordt het gecodeerde PDF-document opgehaald.
1. Versleuteling verwijderen.
1. Sla het PDF-document op als een PDF-bestand.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)

**creeer een cliënt van de encryptiedienst**

Om programmatically een de dienstverrichting van de Encryptie uit te voeren, moet u een de dienstcliënt van de Encryptie tot stand brengen. Als u de Java Encryption Service API gebruikt, maakt u een `EncrytionServiceClient` -object. Als u de webservice-API gebruikt, maakt u een `EncryptionServiceService` -object.

**krijgt het gecodeerde document van de PDF**

Vraag een gecodeerd PDF-document aan om versleuteling op basis van certificaten te verwijderen. Als u probeert versleuteling te verwijderen uit een niet-versleuteld PDF-document, wordt een uitzondering gegenereerd. Op dezelfde manier wordt een uitzondering gegenereerd als u probeert versleuteling op basis van een certificaat te verwijderen uit een met een wachtwoord gecodeerd document.

**verwijdert encryptie**

Als u versleutelde PDF-documenten wilt versleutelen op basis van een certificaat, hebt u zowel een versleuteld PDF-document als de persoonlijke sleutel nodig die overeenkomt met de sleutel waarmee het PDF-document is versleuteld. De aliaswaarde van de persoonlijke sleutel wordt opgegeven wanneer op een certificaat gebaseerde versleuteling wordt verwijderd uit een versleuteld PDF-document. Voor informatie over de openbare sleutel, zie [&#x200B; het Coderen van de Documenten van PDF met Certificaten &#x200B;](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-certificates).

>[!NOTE]
>
>Een persoonlijke sleutel wordt opgeslagen in de AEM Forms Trust Store. Wanneer een certificaat daar wordt geplaatst, wordt een aliaswaarde gespecificeerd.

**sparen het document van de PDF**

Nadat op een certificaat gebaseerde versleuteling is verwijderd uit een versleuteld PDF-document, kunt u het PDF-document opslaan als een PDF-bestand. Gebruikers kunnen het PDF-document openen in Adobe Reader of Acrobat.

**zie ook**

[Op certificaten gebaseerde codering verwijderen met de Java API](encrypting-decrypting-pdf-documents.md#remove-certificate-based-encryption-using-the-java-api)

[Op certificaten gebaseerde versleuteling verwijderen met de webservice-API](encrypting-decrypting-pdf-documents.md#remove-certificate-based-encryption-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[API voor coderingsservice - Snel aan de slag](/help/forms/developing/encryption-service-java-api-quick.md#encryption-service-java-api-quick-start-soap)

### Op certificaten gebaseerde codering verwijderen met de Java API {#remove-certificate-based-encryption-using-the-java-api}

Verwijder op een certificaat gebaseerde versleuteling uit een PDF-document met de API voor versleuteling (Java):

1. Inclusief projectbestanden.

   Neem JAR-bestanden van de client, zoals adobe-encryption-client.jar, op in het klassenpad van uw Java-project.

1. Maak een versleutelingsserviceclient.

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `EncryptionServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Hiermee wordt het gecodeerde PDF-document opgehaald.

   * Maak een `java.io.FileInputStream` -object dat het gecodeerde PDF-document vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het gecodeerde PDF-document aangeeft.
   * Maak een `com.adobe.idp.Document` -object door de constructor ervan te gebruiken en het `java.io.FileInputStream` -object door te geven.

1. Versleuteling verwijderen.

   Verwijder op een certificaat gebaseerde versleuteling uit het PDF-document door de methode `removePDFCertificateSecurity` van het object `EncryptionServiceClient` aan te roepen en de volgende waarden door te geven:

   * Het `com.adobe.idp.Document` -object dat het gecodeerde PDF-document bevat.
   * Een tekenreekswaarde die de aliasnaam van de persoonlijke sleutel opgeeft die overeenkomt met de sleutel die wordt gebruikt om het PDF-document te versleutelen.

   De methode `removePDFCertificateSecurity` retourneert een `com.adobe.idp.Document` -object dat een onbeveiligd PDF-document bevat.

1. Sla het PDF-document op.

   * Maak een `java.io.File` -object en controleer of de bestandsextensie .pdf is.
   * Roep de methode `copyToFile` van het object `com.adobe.idp.Document` aan om de inhoud van het object `Document` naar het bestand te kopiëren. Gebruik het object `com.adobe.idp.Document` dat door de methode `removePDFCredentialSecurity` is geretourneerd.

**zie ook**

[Overzicht van de stappen](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[Snel starten (SOAP modus): codering op basis van een certificaat verwijderen met de Java API](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-removing-certificate-based-encryption-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Op certificaten gebaseerde versleuteling verwijderen met de webservice-API {#remove-certificate-based-encryption-using-the-web-service-api}

Verwijder op een certificaat gebaseerde codering met de API voor codering (webservice):

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Gebruik de volgende WSDL-definitie: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1` .

   >[!NOTE]
   >
   >Vervang `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een versleutelingsserviceclient.

   * Maak een `EncryptionServiceClient` -object met de standaardconstructor.
   * Maak een `EncryptionServiceClient.Endpoint.Address` -object met de `System.ServiceModel.EndpointAddress` -constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/EncryptionService?WSDL` .) U hoeft het attribuut `lc_version` niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Maak een `System.ServiceModel.BasicHttpBinding` -object door de waarde van het `EncryptionServiceClient.Endpoint.Binding` -veld op te halen. De geretourneerde waarde wordt gecast naar `BasicHttpBinding` .
   * Stel het veld `MessageEncoding` van het `System.ServiceModel.BasicHttpBinding` -object in op `WSMessageEncoding.Mtom` . Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld `EncryptionServiceClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de bijbehorende wachtwoordwaarde toe aan het veld `EncryptionServiceClient.ClientCredentials.UserName.Password` .
      * Wijs de constante waarde `HttpClientCredentialType.Basic` toe aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType` .
      * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` toe aan het veld `BasicHttpBindingSecurity.Security.Mode` .

1. Hiermee wordt het gecodeerde PDF-document opgehaald.

   * Maak een `BLOB` -object met behulp van de constructor. Het `BLOB` -object wordt gebruikt om het gecodeerde PDF-document op te slaan.
   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het gecodeerde PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `Length` van het object `System.IO.FileStream` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` -object door de inhoud van de bytearray toe te wijzen aan het gegevenslid van het `BLOB` object `MTOM` .

1. Versleuteling verwijderen.

   Roep de methode `removePDFCertificateSecurity` van het object `EncryptionServiceClient` aan en geef de volgende waarden door:

   * Het `BLOB` -object dat bestandsstreamgegevens bevat die een gecodeerd PDF-document vertegenwoordigen.
   * Een tekenreekswaarde die de aliasnaam van de openbare sleutel opgeeft die overeenkomt met de persoonlijke sleutel die wordt gebruikt om het PDF-document te versleutelen.

   De methode `removePDFCredentialSecurity` retourneert een `BLOB` -object dat een onbeveiligd PDF-document bevat.

1. Sla het PDF-document op.

   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het onbeveiligde PDF-document vertegenwoordigt.
   * Maak een bytearray waarin de inhoud wordt opgeslagen van het `BLOB` -object dat door de methode `removePDFPasswordSecurity` is geretourneerd. Vul de bytearray met de waarde van het gegevenslid `MTOM` van het object `BLOB` .
   * Maak een `System.IO.BinaryWriter` -object door de constructor ervan aan te roepen en het `System.IO.FileStream` -object door te geven.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door de methode `Write` van het object `System.IO.BinaryWriter` aan te roepen en de bytearray door te geven.

**zie ook**

[Overzicht van de stappen](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Wachtwoordversleuteling verwijderen {#removing-password-encryption}

Op wachtwoord gebaseerde versleuteling kan uit een PDF-document worden verwijderd, zodat gebruikers het PDF-document in Adobe Reader of Acrobat kunnen openen zonder een wachtwoord op te geven. Nadat op een wachtwoord gebaseerde versleuteling is verwijderd uit een PDF-document, is het document niet meer beveiligd.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Encryptie, zie [&#x200B; Verwijzing van de Diensten voor AEM Forms &#x200B;](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-3}

Voer de volgende stappen uit om op een wachtwoord gebaseerde versleuteling te verwijderen uit een PDF-document:

1. Projectbestanden opnemen
1. Maak een versleutelingsserviceclient.
1. Hiermee wordt het gecodeerde PDF-document opgehaald.
1. Verwijder het wachtwoord.
1. Sla het PDF-document op als een PDF-bestand.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

**creeer een cliënt van de encryptiedienst**

Om programmatically een de dienstverrichting van de Encryptie uit te voeren, moet u een de dienstcliënt van de Encryptie tot stand brengen. Als u de Java Encryption Service API gebruikt, maakt u een `EncrytionServiceClient` -object. Als u de webservice-API gebruikt, maakt u een `EncryptionServiceService` -object.

**krijgt het gecodeerde document van de PDF**

Vraag een gecodeerd PDF-document aan om op wachtwoord gebaseerde versleuteling te verwijderen. Als u probeert versleuteling te verwijderen uit een niet-versleuteld PDF-document, wordt een uitzondering gegenereerd.

**verwijder het wachtwoord**

Om op wachtwoord-gebaseerde encryptie uit een gecodeerd document van de PDF te verwijderen, vereist u zowel een gecodeerd document van de PDF als een hoofdwachtwoordwaarde die wordt gebruikt om encryptie uit het document van de PDF te verwijderen. Het wachtwoord waarmee een met wachtwoord gecodeerd PDF-document wordt geopend, kan niet worden gebruikt om versleuteling te verwijderen. Er wordt een hoofdwachtwoord opgegeven wanneer het PDF-document met een wachtwoord is versleuteld. (Zie [&#x200B; Coderend de Documenten van PDF met een Wachtwoord &#x200B;](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password).)

**sparen het document van de PDF**

Nadat de coderingsservice op wachtwoord gebaseerde codering uit een PDF-document heeft verwijderd, kunt u het PDF-document opslaan als een PDF-bestand. Gebruikers kunnen het PDF-document openen in Adobe Reader of Acrobat zonder een wachtwoord op te geven.

**zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[API voor coderingsservice - Snel aan de slag](/help/forms/developing/encryption-service-java-api-quick.md#encryption-service-java-api-quick-start-soap)

[PDF-documenten versleutelen met een wachtwoord](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password)

### Op wachtwoorden gebaseerde codering verwijderen met de Java API {#remove-password-based-encryption-using-the-java-api}

Verwijder op wachtwoord gebaseerde codering uit een PDF-document met de API voor codering (Java):

1. Inclusief projectbestanden.

   Neem JAR-bestanden van de client, zoals adobe-encryption-client.jar, op in het klassenpad van uw Java-project.

1. Maak een versleutelingsserviceclient.

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `EncryptionServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Hiermee wordt het gecodeerde PDF-document opgehaald.

   * Maak een `java.io.FileInputStream` -object dat het gecodeerde PDF-document vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het PDF-document aangeeft.
   * Maak een `com.adobe.idp.Document` -object door de constructor ervan te gebruiken en het `java.io.FileInputStream` -object door te geven.

1. Verwijder het wachtwoord.

   Verwijder op wachtwoord gebaseerde codering uit het PDF-document door de methode `removePDFPasswordSecurity` van het object `EncryptionServiceClient` aan te roepen en de volgende waarden door te geven:

   * Een `com.adobe.idp.Document` -object dat het gecodeerde PDF-document bevat.
   * Een tekenreekswaarde die de hoofdwachtwoordwaarde opgeeft die wordt gebruikt om versleuteling te verwijderen uit het PDF-document.

   De methode `removePDFPasswordSecurity` retourneert een `com.adobe.idp.Document` -object dat een onbeveiligd PDF-document bevat.

1. Sla het PDF-document op.

   * Maak een `java.io.File` -object en controleer of de bestandsnaamextensie .pdf is.
   * Roep de methode `copyToFile` van het object `com.adobe.idp.Document` aan om de inhoud van het object `Document` naar het bestand te kopiëren. Gebruik het object `Document` dat door de methode `removePDFPasswordSecurity` is geretourneerd.

**zie ook**

[Snel starten (SOAP modus): codering op basis van wachtwoord verwijderen met de Java API](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-removing-password-based-encryption-using-the-java-api)

### Op wachtwoorden gebaseerde codering verwijderen met de webservice-API {#remove-password-based-encryption-using-the-web-service-api}

Verwijder op wachtwoord gebaseerde codering met de API voor codering (webservice):

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Gebruik de volgende WSDL-definitie: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1` .

   >[!NOTE]
   >
   >Vervang `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een versleutelingsserviceclient.

   * Maak een `EncryptionServiceClient` -object met de standaardconstructor.
   * Maak een `EncryptionServiceClient.Endpoint.Address` -object met de `System.ServiceModel.EndpointAddress` -constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/EncryptionService?WSDL` .) U hoeft het attribuut `lc_version` niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Maak een `System.ServiceModel.BasicHttpBinding` -object door de waarde van het `EncryptionServiceClient.Endpoint.Binding` -veld op te halen. De geretourneerde waarde wordt gecast naar `BasicHttpBinding` .
   * Stel het veld `MessageEncoding` van het `System.ServiceModel.BasicHttpBinding` -object in op `WSMessageEncoding.Mtom` . Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld `EncryptionServiceClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de bijbehorende wachtwoordwaarde toe aan het veld `EncryptionServiceClient.ClientCredentials.UserName.Password` .
      * Wijs de constante waarde `HttpClientCredentialType.Basic` toe aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType` .
      * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` toe aan het veld `BasicHttpBindingSecurity.Security.Mode` .

1. Hiermee wordt het gecodeerde PDF-document opgehaald.

   * Maak een `BLOB` -object met behulp van de constructor. Het `BLOB` -object wordt gebruikt om een met een wachtwoord gecodeerd PDF-document op te slaan.
   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het gecodeerde PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `Length` van het object `System.IO.FileStream` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` -object door de inhoud van de bytearray toe te wijzen aan het gegevenslid van het `BLOB` object `MTOM` .

1. Verwijder het wachtwoord.

   Roep de methode `removePDFPasswordSecurity` van het object `EncryptionServiceService` aan en geef de volgende waarden door:

   * Het `BLOB` -object dat bestandsstreamgegevens bevat die een gecodeerd PDF-document vertegenwoordigen.
   * Een tekenreekswaarde die de wachtwoordwaarde opgeeft die wordt gebruikt om versleuteling te verwijderen uit het PDF-document. Deze waarde wordt opgegeven wanneer het PDF-document met een wachtwoord wordt gecodeerd.

   De methode `removePDFPasswordSecurity` retourneert een `BLOB` -object dat een onbeveiligd PDF-document bevat.

1. Sla het PDF-document op.

   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het onbeveiligde PDF-document vertegenwoordigt.
   * Maak een bytearray waarin de inhoud wordt opgeslagen van het `BLOB` -object dat door de methode `removePDFPasswordSecurity` is geretourneerd. Vul de bytearray met de waarde van het gegevenslid `MTOM` van het object `BLOB` .
   * Maak een `System.IO.BinaryWriter` -object door de constructor ervan aan te roepen en het `System.IO.FileStream` -object door te geven.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door de methode `Write` van het object `System.IO.BinaryWriter` aan te roepen en de bytearray door te geven.

**zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Versleutelde PDF-documenten ontgrendelen {#unlocking-encrypted-pdf-documents}

Een met wachtwoord gecodeerd of met een certificaat gecodeerd PDF-document moet worden ontgrendeld voordat een andere AEM Forms-bewerking kan worden uitgevoerd. Als u een bewerking probeert uit te voeren op een gecodeerd PDF-document, wordt een uitzondering gegenereerd. Nadat u een gecodeerd PDF-document hebt ontgrendeld, kunt u er een of meer bewerkingen op uitvoeren. Deze bewerkingen kunnen tot andere services behoren, zoals de Acrobat Reader DC Extension Service.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Encryptie, zie [&#x200B; Verwijzing van de Diensten voor AEM Forms &#x200B;](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-4}

Voer de volgende stappen uit om een gecodeerd PDF-document te ontgrendelen:

1. Inclusief projectbestanden.
1. Maak een versleutelingsserviceclient.
1. Hiermee wordt het gecodeerde PDF-document opgehaald.
1. Ontgrendel het document.
1. Voer een AEM Forms-bewerking uit.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)

**creeer een cliënt van de encryptiedienst**

Om programmatically een de dienstverrichting van de Encryptie uit te voeren, moet u een de dienstcliënt van de Encryptie tot stand brengen. Als u de Java Encryption Service API gebruikt, maakt u een `EncrytionServiceClient` -object. Als u de webservice-API gebruikt, maakt u een `EncryptionServiceService` -object.

**krijgt het gecodeerde document van de PDF**

Vraag een versleuteld PDF-document aan om dit te ontgrendelen. Als u probeert een PDF-document te ontgrendelen dat niet is versleuteld, wordt een uitzondering gegenereerd.

**ontgrendel het document**

Als u een met een wachtwoord gecodeerd PDF-document wilt ontgrendelen, hebt u zowel een versleuteld PDF-document als een wachtwoordwaarde nodig om een met een wachtwoord gecodeerd PDF-document te openen. Deze waarde wordt opgegeven wanneer het PDF-document met een wachtwoord wordt gecodeerd. (Zie [&#x200B; Coderend de Documenten van PDF met een Wachtwoord &#x200B;](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password).)

Als u een met een certificaat gecodeerd PDF-document wilt ontgrendelen, hebt u zowel een versleuteld PDF-document als de aliaswaarde van de openbare sleutel nodig die overeenkomt met de persoonlijke sleutel waarmee het PDF-document is versleuteld.

**voer een verrichting van AEM Forms uit**

Nadat een gecodeerd PDF-document is ontgrendeld, kunt u er een andere servicebewerking op uitvoeren, zoals gebruiksrechten op toepassen. Deze bewerking behoort tot de Acrobat Reader DC Extensions-service.

**zie ook**

[Een versleuteld PDF-document ontgrendelen met de Java API](encrypting-decrypting-pdf-documents.md#unlock-an-encrypted-pdf-document-using-the-java-api)

[Een gecodeerd PDF-document ontgrendelen met de webservice-API](encrypting-decrypting-pdf-documents.md#unlock-an-encrypted-pdf-document-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[API voor coderingsservice - Snel aan de slag](/help/forms/developing/encryption-service-java-api-quick.md#encryption-service-java-api-quick-start-soap)

### Een versleuteld PDF-document ontgrendelen met de Java API {#unlock-an-encrypted-pdf-document-using-the-java-api}

Een gecodeerd PDF-document ontgrendelen met de API voor versleuteling (Java):

1. Inclusief projectbestanden.

   Neem JAR-bestanden van de client, zoals adobe-encryption-client.jar, op in het klassenpad van uw Java-project.

1. Maak een versleutelingsserviceclient.

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `EncryptionServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Hiermee wordt het gecodeerde PDF-document opgehaald.

   * Maak een `java.io.FileInputStream` -object dat het gecodeerde PDF-document vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het gecodeerde PDF-document aangeeft.
   * Maak een `com.adobe.idp.Document` -object door de constructor ervan te gebruiken en het `java.io.FileInputStream` -object door te geven.

1. Ontgrendel het document.

   Ontgrendel een gecodeerd PDF-document door de methode `unlockPDFUsingPassword` of `unlockPDFUsingCredential` van het `EncryptionServiceClient` -object aan te roepen.

   Als u een PDF-document wilt ontgrendelen dat met een wachtwoord is versleuteld, roept u de methode `unlockPDFUsingPassword` aan en geeft u de volgende waarden door:

   * Een `com.adobe.idp.Document` -object dat het met een wachtwoord gecodeerde PDF-document bevat.
   * Een tekenreekswaarde die de wachtwoordwaarde opgeeft waarmee een met wachtwoord gecodeerd PDF-document wordt geopend. Deze waarde wordt opgegeven wanneer het PDF-document met een wachtwoord wordt gecodeerd.

   Als u een met een certificaat gecodeerd PDF-document wilt ontgrendelen, roept u de methode `unlockPDFUsingCredential` aan en geeft u de volgende waarden door:

   * Een `com.adobe.idp.Document` -object dat het met een certificaat gecodeerde PDF-document bevat.
   * Een tekenreekswaarde die de aliasnaam van de openbare sleutel opgeeft die overeenkomt met de persoonlijke sleutel die wordt gebruikt om het PDF-document te versleutelen.

   De methoden `unlockPDFUsingPassword` en `unlockPDFUsingCredential` retourneren beide een `com.adobe.idp.Document` -object dat u doorgeeft aan een andere AEM Forms Java-methode om een bewerking uit te voeren.

1. Voer een AEM Forms-bewerking uit.

   Voer een AEM Forms-bewerking uit op het ontgrendelde PDF-document om aan uw zakelijke vereisten te voldoen. Als u bijvoorbeeld gebruiksrechten wilt toepassen op een ontgrendeld PDF-document, geeft u het `com.adobe.idp.Document` -object dat door de methode `unlockPDFUsingPassword` of `unlockPDFUsingCredential` is geretourneerd, door aan de methode `ReaderExtensionsServiceClient` object `applyUsageRights` .

**zie ook**

[Overzicht van de stappen](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[&#x200B; Snel Begin (SOAP wijze): Het ontgrendelen van een gecodeerd document van de PDF gebruikend Java API &#x200B;](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-unlocking-an-encrypted-pdf-document-using-the-java-api) (SOAP wijze)

[Gebruiksrechten toepassen op PDF-documenten](/help/forms/developing/assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een gecodeerd PDF-document ontgrendelen met de webservice-API {#unlock-an-encrypted-pdf-document-using-the-web-service-api}

Een gecodeerd PDF-document ontgrendelen met de API voor versleuteling (webservice):

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Gebruik de volgende WSDL-definitie: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1` .

   >[!NOTE]
   >
   >Vervang `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een versleutelingsserviceclient.

   * Maak een `EncryptionServiceClient` -object met de standaardconstructor.
   * Maak een `EncryptionServiceClient.Endpoint.Address` -object met de `System.ServiceModel.EndpointAddress` -constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/EncryptionService?WSDL` .) U hoeft het attribuut `lc_version` niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Maak een `System.ServiceModel.BasicHttpBinding` -object door de waarde van het `EncryptionServiceClient.Endpoint.Binding` -veld op te halen. De geretourneerde waarde wordt gecast naar `BasicHttpBinding` .
   * Stel het veld `MessageEncoding` van het `System.ServiceModel.BasicHttpBinding` -object in op `WSMessageEncoding.Mtom` . Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld `EncryptionServiceClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de bijbehorende wachtwoordwaarde toe aan het veld `EncryptionServiceClient.ClientCredentials.UserName.Password` .
      * Wijs de constante waarde `HttpClientCredentialType.Basic` toe aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType` .
      * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` toe aan het veld `BasicHttpBindingSecurity.Security.Mode` .

1. Een versleuteld PDF-document ophalen.

   * Maak een `BLOB` -object met behulp van de constructor.
   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het gecodeerde PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `Length` van het object `System.IO.FileStream` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` -object door de inhoud van de bytearray toe te wijzen aan het gegevenslid van het `BLOB` object `MTOM` .

1. Ontgrendel het document.

   Ontgrendel een gecodeerd PDF-document door de methode `unlockPDFUsingPassword` of `unlockPDFUsingCredential` van het `EncryptionServiceClient` -object aan te roepen.

   Als u een PDF-document wilt ontgrendelen dat met een wachtwoord is versleuteld, roept u de methode `unlockPDFUsingPassword` aan en geeft u de volgende waarden door:

   * Een `BLOB` -object dat het met een wachtwoord gecodeerde PDF-document bevat.
   * Een tekenreekswaarde die de wachtwoordwaarde opgeeft waarmee een met wachtwoord gecodeerd PDF-document wordt geopend. Deze waarde wordt opgegeven wanneer het PDF-document met een wachtwoord wordt gecodeerd.

   Als u een met een certificaat gecodeerd PDF-document wilt ontgrendelen, roept u de methode `unlockPDFUsingCredential` aan en geeft u de volgende waarden door:

   * Een `BLOB` -object dat het met een certificaat gecodeerde PDF-document bevat.
   * Een tekenreekswaarde die de aliasnaam van de openbare sleutel opgeeft die overeenkomt met de persoonlijke sleutel die wordt gebruikt om het PDF-document te versleutelen.

   De methoden `unlockPDFUsingPassword` en `unlockPDFUsingCredential` retourneren beide een `com.adobe.idp.Document` -object dat u doorgeeft aan een andere AEM Forms-methode om een bewerking uit te voeren.

1. Voer een AEM Forms-bewerking uit.

   Voer een AEM Forms-bewerking uit op het ontgrendelde PDF-document om aan uw zakelijke vereisten te voldoen. Als u bijvoorbeeld gebruiksrechten wilt toepassen op het ontgrendelde PDF-document, geeft u het `BLOB` -object dat door de methode `unlockPDFUsingPassword` of `unlockPDFUsingCredential` is geretourneerd, door aan de methode `ReaderExtensionsServiceClient` object `applyUsageRights` .

**zie ook**

[Overzicht van de stappen](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Type codering bepalen {#determining-encryption-type}

U kunt programmatically het type van encryptie bepalen die een document van PDF door de Dienst API van de Encryptie van Java of de Dienst API van de Encryptie van de Webdienst te gebruiken beschermt. Soms is het nodig dynamisch te bepalen of een PDF-document is versleuteld en, zo ja, het versleutelingstype. U kunt bijvoorbeeld bepalen of een PDF-document is beveiligd met op een wachtwoord gebaseerde codering of met een beleid voor Rights Managementen.

Een PDF-document kan worden beveiligd door de volgende coderingstypen:

* Codering op basis van wachtwoord
* Op een certificaat gebaseerde codering
* Een beleid dat door de dienst van het Rights Management wordt gecreeerd
* Een ander type codering

>[!NOTE]
>
>Voor meer informatie over de dienst van de Encryptie, zie [&#x200B; Verwijzing van de Diensten voor AEM Forms &#x200B;](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-5}

Ga als volgt te werk om te bepalen welk type codering een PDF-document beveiligt:

1. Inclusief projectbestanden.
1. Maak een versleutelingsserviceclient.
1. Hiermee wordt het gecodeerde PDF-document opgehaald.
1. Bepaal het versleutelingstype.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)

**creeer een de dienstcliënt**

Om programmatically een de dienstverrichting van de Encryptie uit te voeren, moet u een de dienstcliënt van de Encryptie tot stand brengen. Als u de Java Encryption Service API gebruikt, maakt u een `EncrytionServiceClient` -object. Als u de webservice-API gebruikt, maakt u een `EncryptionServiceService` -object.

**krijgt het gecodeerde document van de PDF**

Vraag een PDF-document aan om het type codering te bepalen dat deze beveiligt.

**bepaal het encryptietype**

U kunt bepalen welk type versleuteling een PDF-document beveiligt. Als het PDF-document niet is beveiligd, geeft de coderingsservice aan dat het PDF-document niet is beveiligd.

**zie ook**

[Het versleutelingstype bepalen met de Java API](encrypting-decrypting-pdf-documents.md#determine-the-encryption-type-using-the-java-api)

[Het versleutelingstype bepalen met de webservice-API](encrypting-decrypting-pdf-documents.md#determine-the-encryption-type-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[API voor coderingsservice - Snel aan de slag](/help/forms/developing/encryption-service-java-api-quick.md#encryption-service-java-api-quick-start-soap)

[Documenten beveiligen met beleid](/help/forms/developing/protecting-documents-policies.md#protecting-documents-with-policies)

### Het versleutelingstype bepalen met de Java API {#determine-the-encryption-type-using-the-java-api}

Bepaal het type codering waarmee een PDF-document wordt beveiligd met de API voor versleuteling (Java):

1. Inclusief projectbestanden.

   Neem JAR-bestanden van de client, zoals adobe-encryption-client.jar, op in het klassenpad van uw Java-project.

1. Maak een serviceclient.

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `EncryptionServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Hiermee wordt het gecodeerde PDF-document opgehaald.

   * Maak een `java.io.FileInputStream` -object dat het PDF-document vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het PDF-document aangeeft.
   * Maak een `com.adobe.idp.Document` -object door de constructor ervan te gebruiken en het `java.io.FileInputStream` -object door te geven.

1. Bepaal het versleutelingstype.

   * Bepaal het versleutelingstype door de methode `getPDFEncryption` van het object `EncryptionServiceClient` aan te roepen en het object `com.adobe.idp.Document` door te geven dat het PDF-document bevat. Deze methode retourneert een `EncryptionTypeResult` -object.
   * Roep de methode `getEncryptionType` van het object `EncryptionTypeResult` aan. Deze methode retourneert een `EncryptionType` enum-waarde die het versleutelingstype opgeeft. Als het PDF-document bijvoorbeeld is beveiligd met op een wachtwoord gebaseerde codering, retourneert deze methode `EncryptionType.PASSWORD` .

**zie ook**

[Overzicht van de stappen](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[Snel starten (SOAP modus): Coderingstype bepalen met de Java API](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-determining-encryption-type-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Het versleutelingstype bepalen met de webservice-API {#determine-the-encryption-type-using-the-web-service-api}

Bepaal het type codering waarmee een PDF-document wordt beveiligd met de API voor versleuteling (webservice):

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Gebruik de volgende WSDL-definitie: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1` .

   >[!NOTE]
   >
   >Vervang `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een serviceclient.

   * Maak een `EncryptionServiceClient` -object met de standaardconstructor.
   * Maak een `EncryptionServiceClient.Endpoint.Address` -object met de `System.ServiceModel.EndpointAddress` -constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/EncryptionService?WSDL` .) U hoeft het attribuut `lc_version` niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Maak een `System.ServiceModel.BasicHttpBinding` -object door de waarde van het `EncryptionServiceClient.Endpoint.Binding` -veld op te halen. De geretourneerde waarde wordt gecast naar `BasicHttpBinding` .
   * Stel het veld `MessageEncoding` van het `System.ServiceModel.BasicHttpBinding` -object in op `WSMessageEncoding.Mtom` . Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld `EncryptionServiceClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de bijbehorende wachtwoordwaarde toe aan het veld `EncryptionServiceClient.ClientCredentials.UserName.Password` .
      * Wijs de constante waarde `HttpClientCredentialType.Basic` toe aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType` .
      * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` toe aan het veld `BasicHttpBindingSecurity.Security.Mode` .

1. Hiermee wordt het gecodeerde PDF-document opgehaald.

   * Maak een `BLOB` -object met behulp van de constructor.
   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het gecodeerde PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `Length` van het object `System.IO.FileStream` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` -object door de inhoud van de bytearray toe te wijzen aan het gegevenslid van het `BLOB` object `MTOM` .

1. Bepaal het versleutelingstype.

   * Roep de methode `getPDFEncryption` van het `EncryptionServiceClient` -object aan en geef het `BLOB` -object dat het PDF-document bevat door. Deze methode retourneert een `EncryptionTypeResult` -object.
   * Hiermee wordt de waarde van de gegevensmethode `encryptionType` van het `EncryptionTypeResult` -object opgehaald. Als het PDF-document bijvoorbeeld is beveiligd met op een wachtwoord gebaseerde codering, is de waarde van dit gegevenslid `EncryptionType.PASSWORD` .

**zie ook**

[Overzicht van de stappen](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
