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
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '8133'
ht-degree: 0%

---

# PDF-documenten versleutelen en ontsleutelen {#encrypting-and-decrypting-pdf-documents}

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

**Over de coderingsservice**

Met de coderingsservice kunt u documenten versleutelen en decoderen. Wanneer een document wordt versleuteld, wordt de inhoud ervan onleesbaar. Een geautoriseerde gebruiker kan het document decoderen om toegang tot de inhoud te krijgen. Als een PDF-document met een wachtwoord is versleuteld, moet de gebruiker het wachtwoord voor openen opgeven voordat het document in Adobe Reader of Adobe Acrobat kan worden weergegeven. Als een PDF-document met een certificaat is versleuteld, moet de gebruiker het PDF-document decoderen met de openbare sleutel die overeenkomt met het certificaat (de persoonlijke sleutel) waarmee het PDF-document is versleuteld.

U kunt deze taken uitvoeren met behulp van de coderingsservice:

* Codeer een PDF-document met een wachtwoord. (Zie [PDF-documenten versleutelen met een wachtwoord](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password).)
* Codeer een PDF-document met een certificaat. (Zie [PDF-documenten versleutelen met certificaten](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-certificates).)
* Verwijder op wachtwoord gebaseerde versleuteling uit een PDF-document. (Zie [Wachtwoordversleuteling verwijderen](encrypting-decrypting-pdf-documents.md#removing-password-encryption).)
* Verwijder op een certificaat gebaseerde versleuteling uit een PDF-document. (Zie [Versleuteling op basis van een certificaat verwijderen](encrypting-decrypting-pdf-documents.md#removing-certificate-based-encryption).)
* Ontgrendel het document van de PDF zodat andere de dienstverrichtingen kunnen worden uitgevoerd. Nadat een met een wachtwoord gecodeerd PDF-document bijvoorbeeld is ontgrendeld, kunt u er een digitale handtekening op toepassen. (Zie [Versleutelde PDF-documenten ontgrendelen](encrypting-decrypting-pdf-documents.md#unlocking-encrypted-pdf-documents).)
* Bepaal het versleutelingstype van een beveiligd PDF-document. (Zie [Type codering bepalen](encrypting-decrypting-pdf-documents.md#determining-encryption-type).)

>[!NOTE]
>
>Voor meer informatie over de dienst van de Encryptie, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## PDF-documenten versleutelen met een wachtwoord {#encrypting-pdf-documents-with-a-password}

Wanneer u een PDF-document versleutelt met een wachtwoord, moet een gebruiker het wachtwoord opgeven om het PDF-document te openen in Adobe Reader of Acrobat. Voordat een andere AEM Forms-bewerking, zoals het digitaal ondertekenen van het PDF-document, op het document kan worden uitgevoerd, moet een met wachtwoord gecodeerd PDF-document worden ontgrendeld.

>[!NOTE]
>
>Als u een gecodeerd PDF-document uploadt naar de AEM Forms-opslagplaats, kan het PDF-document niet worden gedecodeerd en de XDP-inhoud niet worden uitgepakt. U wordt aangeraden een document niet te coderen voordat u het uploadt naar de AEM Forms-opslagplaats. (Zie [Bronnen schrijven](/help/forms/developing/aem-forms-repository.md#writing-resources).)

>[!NOTE]
>
>Voor meer informatie over de dienst van de Encryptie, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary-of-steps}

Voer de volgende stappen uit om een PDF-document met een wachtwoord te coderen:

1. Inclusief projectbestanden.
1. Maak een Encryption Client API-object.
1. Een PDF-document ophalen om te versleutelen.
1. Stel opties voor codering tijdens runtime in.
1. Voeg het wachtwoord toe.
1. Sla het gecodeerde PDF-document op als een PDF-bestand.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

**Een Encryption Client API-object maken**

Om programmatically een de dienstverrichting van de Encryptie uit te voeren, moet u een de dienstcliënt van de Encryptie tot stand brengen.

**Een PDF-document ophalen om te versleutelen**

Verkrijg een niet-gecodeerd document van de PDF om het document met een wachtwoord te coderen. Als u probeert een PDF-document te beveiligen dat al is versleuteld, veroorzaakt u een uitzondering.

**Opties voor codering tijdens runtime instellen**

Als u een PDF-document met een wachtwoord wilt versleutelen, geeft u vier waarden op, waaronder twee wachtwoordwaarden. Het eerste wachtwoord wordt gebruikt om het PDF-document te versleutelen en moet worden opgegeven bij het openen van het PDF-document. De tweede wachtwoordwaarde, die de hoofdwachtwoordwaarde wordt genoemd, wordt gebruikt om encryptie uit het document van de PDF te verwijderen. Wachtwoordwaarden zijn hoofdlettergevoelig en deze twee wachtwoordwaarden kunnen niet dezelfde waarden zijn.

Geef de bronnen voor het PDF-document op die u wilt versleutelen. U kunt het volledige document van de PDF, alles behalve de meta-gegevens van het document, of enkel de gehechtheid van het document coderen. Als u alleen de bijlagen van het document versleutelt, wordt een gebruiker om een wachtwoord gevraagd wanneer hij of zij de bestandsbijlagen wil openen.

Wanneer u een PDF-document versleutelt, kunt u machtigingen opgeven die aan het beveiligde document zijn gekoppeld. Door machtigingen op te geven, kunt u de handelingen beheren die een gebruiker die een met een wachtwoord gecodeerd PDF-document opent, mag uitvoeren. Als u bijvoorbeeld met succes formuliergegevens wilt extraheren, moet u de volgende machtigingen instellen:

* PASSWORD_EDIT_ADD
* WACHTWOORD_EDIT_MODIFY

>[!NOTE]
>
>Machtigingen worden opgegeven als `PasswordEncryptionPermission` opsommingswaarden.

**Het wachtwoord toevoegen**

Nadat u een onbeveiligd PDF-document hebt opgehaald en waarden voor de codering hebt ingesteld, kunt u een wachtwoord toevoegen aan het PDF-document.

**Het gecodeerde PDF-document opslaan als een PDF-bestand**

U kunt het met een wachtwoord gecodeerde PDF-document opslaan als een PDF-bestand.

**Zie ook**

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

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `EncryptionServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Een PDF-document ophalen om te versleutelen.

   * Een `java.io.FileInputStream` -object dat het PDF-document vertegenwoordigt dat moet worden gecodeerd met de constructor ervan en dat een tekenreekswaarde doorgeeft die de locatie van het PDF-document aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. Stel opties voor codering tijdens runtime in.

   * Een `PasswordEncryptionOptionSpec` object door de constructor ervan aan te roepen.
   * Geef de bronnen van het PDF-document op die u wilt versleutelen door het `PasswordEncryptionOptionSpec` object `setEncryptOption` methode en een `PasswordEncryptionOption` opsommingswaarde waarmee de documentbronnen worden opgegeven die moeten worden gecodeerd. Als u bijvoorbeeld het gehele PDF-document wilt versleutelen, inclusief de metagegevens en de bijlagen, geeft u `PasswordEncryptionOption.ALL`.
   * Een `java.util.List` object dat de versleutelingsmachtigingen opslaat met de `ArrayList` constructor.
   * Geef een machtiging op door de opdracht `java.util.List` object &#39;s `add` en het overgaan van een opsommingswaarde die aan de toestemming beantwoordt die u wilt plaatsen. Als u bijvoorbeeld de machtiging wilt instellen waarmee een gebruiker gegevens in het PDF-document kan kopiëren, geeft u `PasswordEncryptionPermission.PASSWORD_EDIT_COPY`. (Herhaal deze stap voor elke machtiging die moet worden ingesteld).
   * Geef de compatibiliteitsoptie voor Acrobat op door de `PasswordEncryptionOptionSpec` object `setCompatability` methode en het overgaan van een opsommingswaarde die het de verenigbaarheidsniveau van Acrobat specificeert. U kunt bijvoorbeeld `PasswordEncryptionCompatability.ACRO_7`.
   * Geef de wachtwoordwaarde op waarmee een gebruiker het gecodeerde PDF-document kan openen door het `PasswordEncryptionOptionSpec` object `setDocumentOpenPassword` methode en het overgaan van een koordwaarde die het open wachtwoord vertegenwoordigt.
   * Geef de waarde van het hoofdwachtwoord op waarmee een gebruiker de codering uit het PDF-document kan verwijderen door het `PasswordEncryptionOptionSpec` object `setPermissionPassword` methode en het overgaan van een koordwaarde die het hoofdwachtwoord vertegenwoordigt.

1. Voeg het wachtwoord toe.

   Codeer het PDF-document door het `EncryptionServiceClient` object `encryptPDFUsingPassword` en geeft de volgende waarden door:

   * De `com.adobe.idp.Document` -object dat het PDF-document bevat dat met het wachtwoord moet worden gecodeerd.
   * De `PasswordEncryptionOptionSpec` object dat opties voor codering tijdens runtime bevat.

   De `encryptPDFUsingPassword` methode retourneert een `com.adobe.idp.Document` object dat een met wachtwoord gecodeerd PDF-document bevat.

1. Sla het gecodeerde PDF-document op als een PDF-bestand.

   * Een `java.io.File` en zorg dat de bestandsextensie .pdf is.
   * De `com.adobe.idp.Document` object `copyToFile` methode om de inhoud van de `com.adobe.idp.Document` naar het bestand. Zorg ervoor dat u de `com.adobe.idp.Document` object dat is geretourneerd door de `encryptPDFUsingPassword` methode.

**Zie ook**

[Overzicht van de stappen](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[Snel starten (SOAP-modus): Een PDF-document versleutelen met de Java API](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-encrypting-a-pdf-document-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een PDF-document versleutelen met de API voor webservices {#encrypting-a-pdf-document-using-the-web-service-api}

Codeer een PDF-document met een wachtwoord met behulp van de API voor versleuteling (webservice):

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Encryption Client API-object.

   * Een `EncryptionServiceClient` object met de standaardconstructor.
   * Een `EncryptionServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/EncryptionService?WSDL`.) U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `EncryptionServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `EncryptionServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `EncryptionServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Een PDF-document ophalen om te versleutelen.

   * Een `BLOB` object met behulp van de constructor. De `BLOB` wordt gebruikt om een PDF-document op te slaan dat met een wachtwoord is versleuteld.
   * Een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het te coderen PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door de inhoud van de bytearray toe te wijzen aan de `BLOB` object `MTOM` lid.

1. Stel opties voor codering tijdens runtime in.

   * Een `PasswordEncryptionOptionSpec` object met behulp van de constructor.
   * Geef de bronnen voor het PDF-document op die u wilt versleutelen door een `PasswordEncryptionOption` opsommingswaarde voor de `PasswordEncryptionOptionSpec` object `encryptOption` lid. Om de volledige PDF, met inbegrip van zijn meta-gegevens en zijn gehechtheid te coderen, wijs `PasswordEncryptionOption.ALL` aan dit gegevenslid.
   * Geef de compatibiliteitsoptie voor Acrobat op door een `PasswordEncryptionCompatability` opsommingswaarde voor de `PasswordEncryptionOptionSpec` object `compatability` lid. Wijs bijvoorbeeld `PasswordEncryptionCompatability.ACRO_7` aan dit gegevenslid.
   * Geef de wachtwoordwaarde op waarmee een gebruiker het gecodeerde PDF-document kan openen door een tekenreekswaarde toe te wijzen die het geopende wachtwoord vertegenwoordigt voor de `PasswordEncryptionOptionSpec` object `documentOpenPassword` lid.
   * Geef de wachtwoordwaarde op waarmee een gebruiker versleuteling uit het PDF-document kan verwijderen door een tekenreekswaarde toe te wijzen die het hoofdwachtwoord vertegenwoordigt voor de `PasswordEncryptionOptionSpec` object `permissionPassword` lid.

1. Voeg het wachtwoord toe.

   Codeer het PDF-document door het `EncryptionServiceClient` object `encryptPDFUsingPassword` en geeft de volgende waarden door:

   * De `BLOB` -object dat het PDF-document bevat dat met het wachtwoord moet worden gecodeerd.
   * De `PasswordEncryptionOptionSpec` object dat opties voor codering tijdens runtime bevat.

   De `encryptPDFUsingPassword` methode retourneert een `BLOB` object dat een met wachtwoord gecodeerd PDF-document bevat.

1. Sla het gecodeerde PDF-document op als een PDF-bestand.

   * Een `System.IO.FileStream` door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het beveiligde PDF-document vertegenwoordigt.
   * Maak een bytearray waarin de gegevensinhoud van de `BLOB` object dat is geretourneerd door de `encryptPDFUsingPassword` methode. Vul de bytearray met de waarde van de `BLOB` object `MTOM` lid.
   * Een `System.IO.BinaryWriter` object door de constructor aan te roepen en de `System.IO.FileStream` object.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door het `System.IO.BinaryWriter` object `Write` en geeft u de bytearray door.

**Zie ook**

[Overzicht van de stappen](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## PDF-documenten versleutelen met certificaten {#encrypting-pdf-documents-with-certificates}

Met codering op basis van certificaten kunt u een document voor specifieke ontvangers versleutelen met behulp van technologie voor openbare sleutels. Verschillende ontvangers kunnen verschillende machtigingen voor het document krijgen. Veel aspecten van versleuteling worden mogelijk gemaakt door de technologie van de openbare sleutel. Een algoritme wordt gebruikt om twee grote aantallen te produceren, die als worden bekend *toetsen*, die de volgende eigenschappen hebben:

* Eén sleutel wordt gebruikt om een set gegevens te coderen. Vervolgens kan alleen de andere sleutel worden gebruikt om de gegevens te decoderen.
* Het is onmogelijk om de ene sleutel van de andere te onderscheiden.

Een van de toetsen fungeert als de persoonlijke sleutel van een gebruiker. Het is belangrijk dat alleen de gebruiker toegang heeft tot deze sleutel. De andere sleutel is de openbare sleutel van de gebruiker, die met anderen kan worden gedeeld.

Een certificaat met een openbare sleutel bevat de openbare sleutel van een gebruiker en identificeert informatie. De indeling X.509 wordt gebruikt voor het opslaan van certificaten. Certificaten worden doorgaans uitgegeven en digitaal ondertekend door een certificeringsinstantie (CA), een erkende entiteit die een zekere mate van vertrouwen biedt in de geldigheid van het certificaat. Certificaten hebben een vervaldatum waarna ze niet meer geldig zijn. Bovendien bevatten de certificaatintrekkingslijsten (CRL&#39;s) informatie over certificaten die vóór de vervaldatum zijn ingetrokken. CRL&#39;s worden periodiek gepubliceerd door certificeringsinstanties. De intrekkingsstatus van een certificaat kan ook via het online certificaatstatusprotocol (OCSP) via het netwerk worden opgehaald.

>[!NOTE]
>
>Als u een gecodeerd PDF-document uploadt naar de AEM Forms-opslagplaats, kan het PDF-document niet worden gedecodeerd en de XDP-inhoud niet worden uitgepakt. U wordt aangeraden een document niet te coderen voordat u het uploadt naar de AEM Forms-opslagplaats. (Zie [Bronnen schrijven](/help/forms/developing/aem-forms-repository.md#writing-resources).)

>[!NOTE]
>
>Voordat u een PDF-document kunt versleutelen met een certificaat, moet u ervoor zorgen dat u het certificaat toevoegt aan AEM Forms. Een certificaat wordt toegevoegd gebruikend beleidsconsole of programmatically gebruikend de Manager API van het Vertrouwen. (Zie [Referenties importeren met de Betrouwbaarheidsbeheer-API](/help/forms/developing/credentials.md#importing-credentials-by-using-the-trust-manager-api).)

>[!NOTE]
>
>Voor meer informatie over de dienst van de Encryptie, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-1}

Voer de volgende stappen uit om een PDF-document te versleutelen met een certificaat:

1. Inclusief projectbestanden.
1. Maak een Encryption Client API-object.
1. Een PDF-document ophalen om te versleutelen.
1. Verwijs naar het certificaat.
1. Stel opties voor codering tijdens runtime in.
1. Maak een met een certificaat gecodeerd PDF-document.
1. Sla het gecodeerde PDF-document op als een PDF-bestand.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)

**Een Encryption Client API-object maken**

Om programmatically een de dienstverrichting van de Encryptie uit te voeren, moet u een de dienstcliënt van de Encryptie tot stand brengen. Als u de Java Encryption Service API gebruikt, maakt u een `EncrytionServiceClient` object. Als u de webservice-API gebruikt, maakt u een `EncryptionServiceService` object.

**Een PDF-document ophalen om te versleutelen**

Vraag een niet-gecodeerd PDF-document aan om te versleutelen. Als u probeert een PDF-document te beveiligen dat al is versleuteld, wordt een uitzondering gegenereerd.

**Verwijzing naar het certificaat**

Als u een PDF-document wilt versleutelen met een certificaat, verwijst u naar een certificaat dat wordt gebruikt om een PDF-document te versleutelen. Het certificaat is een .cer-bestand, een .crt-bestand of een .pem-bestand. Een PKCS#12-bestand wordt gebruikt voor het opslaan van persoonlijke sleutels met de bijbehorende certificaten.

Wanneer u een PDF-document versleutelt met een certificaat, geeft u de machtigingen op die aan het beveiligde document zijn gekoppeld. Door machtigingen op te geven, kunt u de handelingen beheren die een gebruiker die een met een certificaat gecodeerd PDF-document opent, kan uitvoeren.

**Opties voor codering tijdens runtime instellen**

Geef de bronnen voor het PDF-document op die u wilt versleutelen. U kunt het volledige document van de PDF, alles behalve de meta-gegevens van het document, of slechts de gehechtheid van het document coderen.

**Een met een certificaat gecodeerd PDF-document maken**

Nadat u een onbeveiligd PDF-document hebt opgehaald, naar het certificaat verwijst en uitvoeringsopties hebt ingesteld, kunt u een met een certificaat gecodeerd PDF-document maken. Nadat het PDF-document is versleuteld, hebt u de bijbehorende openbare sleutel nodig om het te decoderen.

**Het gecodeerde PDF-document opslaan als een PDF-bestand**

U kunt het gecodeerde PDF-document opslaan als een PDF-bestand.

**Zie ook**

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

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `EncryptionServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Een PDF-document ophalen om te versleutelen.

   * Een `java.io.FileInputStream` -object dat het PDF-document vertegenwoordigt dat moet worden gecodeerd met de constructor ervan en dat een tekenreekswaarde doorgeeft die de locatie van het PDF-document aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. Verwijs naar het certificaat.

   * Een `java.util.List` object dat machtigingsinformatie opslaat met de constructor ervan.
   * Geef de machtigingen voor het versleutelde document op door de opdracht `java.util.List` object `add` methode en een `CertificateEncryptionPermissions` opsommingswaarde die de machtigingen vertegenwoordigt die zijn verleend aan de gebruiker die het beveiligde PDF-document opent. Als u bijvoorbeeld alle machtigingen wilt opgeven, geeft u `CertificateEncryptionPermissions.PKI_ALL_PERM`.
   * Een `Recipient` object met behulp van de constructor.
   * Een `java.io.FileInputStream` -object dat staat voor het certificaat dat wordt gebruikt om het PDF-document te versleutelen met de constructor ervan en door een tekenreekswaarde door te geven die de locatie van het certificaat aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object dat het certificaat vertegenwoordigt.
   * De `Recipient` object `setX509Cert` en geeft de `com.adobe.idp.Document` object dat het certificaat bevat. (Daarnaast worden de `Recipient`-object kan als certificaatbron een alias voor een Truststore-certificaat of LDAP-URL hebben.)
   * Een `CertificateEncryptionIdentity` object dat machtiging- en certificaatinformatie opslaat met de constructor ervan.
   * De `CertificateEncryptionIdentity` object `setPerms` en geeft de `java.util.List` object dat machtigingsgegevens opslaat.
   * De `CertificateEncryptionIdentity` object `setRecipient` en geeft de `Recipient` object dat certificaatgegevens opslaat.
   * Een `java.util.List` object dat certificaatinformatie opslaat met de constructor ervan.
   * De `java.util.List` voegt methode toe en geeft de `CertificateEncryptionIdentity` object. (Dit `java.util.List` object wordt als parameter doorgegeven aan de `encryptPDFUsingCertificates` methode.)

1. Stel opties voor codering tijdens runtime in.

   * Een `CertificateEncryptionOptionSpec` object door de constructor ervan aan te roepen.
   * Geef de bronnen van het PDF-document op die u wilt versleutelen door het `CertificateEncryptionOptionSpec` object `setOption` methode en een `CertificateEncryptionOption` opsommingswaarde waarmee de documentbronnen worden opgegeven die moeten worden gecodeerd. Als u bijvoorbeeld het gehele PDF-document wilt versleutelen, inclusief de metagegevens en de bijlagen, geeft u `CertificateEncryptionOption.ALL`.
   * Geef de compatibiliteitsoptie voor Acrobat op door de `CertificateEncryptionOptionSpec` object `setCompat` methode en een `CertificateEncryptionCompatibility` opsommingswaarde die het Acrobat-compatibiliteitsniveau opgeeft. U kunt bijvoorbeeld `CertificateEncryptionCompatibility.ACRO_7`.

1. Maak een met een certificaat gecodeerd PDF-document.

   Codeer het PDF-document met een certificaat door het `EncryptionServiceClient` object `encryptPDFUsingCertificates` en geeft de volgende waarden door:

   * De `com.adobe.idp.Document` -object dat het te coderen PDF-document bevat.
   * De `java.util.List` object dat certificaatgegevens opslaat.
   * De `CertificateEncryptionOptionSpec` object dat opties voor codering tijdens runtime bevat.

   De `encryptPDFUsingCertificates` methode retourneert een `com.adobe.idp.Document` -object dat een met een certificaat gecodeerd PDF-document bevat.

1. Sla het gecodeerde PDF-document op als een PDF-bestand.

   * Een `java.io.File` en zorg ervoor dat de bestandsnaamextensie .pdf is.
   * De `com.adobe.idp.Document` object `copyToFile` methode om de inhoud van de `com.adobe.idp.Document` naar het bestand. Zorg ervoor dat u de `com.adobe.idp.Document` object dat is geretourneerd door de `encryptPDFUsingCertificates` methode.

**Zie ook**

[Overzicht van de stappen](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[Snel starten (SOAP-modus): Een PDF-document versleutelen met een certificaat met de Java API](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-encrypting-a-pdf-document-with-a-certificate-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een PDF-document versleutelen met een certificaat met de webservice-API {#encrypt-a-pdf-document-with-a-certificate-using-the-web-service-api}

Codeer een PDF-document met een certificaat met behulp van de API voor versleuteling (webservice):

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Encryption Client API-object.

   * Een `EncryptionServiceClient` object met de standaardconstructor.
   * Een `EncryptionServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/EncryptionService?WSDL`.) U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `EncryptionServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `EncryptionServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `EncryptionServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Een PDF-document ophalen om te versleutelen.

   * Een `BLOB` object met behulp van de constructor. De `BLOB` wordt gebruikt om een PDF-document op te slaan dat met een certificaat is versleuteld.
   * Een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het te coderen PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` eigenschap met de inhoud van de bytearray.

1. Verwijs naar het certificaat.

   * Een `Recipient` object met behulp van de constructor. In dit object worden certificaatgegevens opgeslagen.
   * Een `BLOB` object met behulp van de constructor. Dit `BLOB` -object het certificaat opslaan waarmee het PDF-document wordt versleuteld.
   * Een `System.IO.FileStream` door de constructor aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het certificaat en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door de inhoud van de bytearray toe te wijzen aan de `BLOB` object `MTOM` lid.
   * Wijs het `BLOB` object waarin het certificaat is opgeslagen in het `Recipient` object `x509Cert` lid.
   * Een `CertificateEncryptionIdentity` object dat certificaatinformatie opslaat met de constructor ervan.
   * Wijs het `Recipient` object waarin het certificaat is opgeslagen in het `CertificateEncryptionIdentity`het gegevenslid van de ontvanger van het object.
   * Een `Object` array en wijs de `CertificateEncryptionIdentity` object naar het eerste element van het dialoogvenster `Object` array. Dit `Object` array wordt als parameter doorgegeven aan de `encryptPDFUsingCertificates` methode.

1. Stel opties voor codering tijdens runtime in.

   * Een `CertificateEncryptionOptionSpec` object met behulp van de constructor.
   * Geef de bronnen voor het PDF-document op die u wilt versleutelen door een `CertificateEncryptionOption` opsommingswaarde voor de `CertificateEncryptionOptionSpec` object `option` lid. Om het volledige document van de PDF, met inbegrip van zijn meta-gegevens en zijn gehechtheid te coderen, wijs `CertificateEncryptionOption.ALL` aan dit gegevenslid.
   * Geef de compatibiliteitsoptie voor Acrobat op door een `CertificateEncryptionCompatibility` opsommingswaarde voor de `CertificateEncryptionOptionSpec` object `compat` lid. Wijs bijvoorbeeld `CertificateEncryptionCompatibility.ACRO_7` aan dit gegevenslid.

1. Maak een met een certificaat gecodeerd PDF-document.

   Codeer het PDF-document met een certificaat door het `EncryptionServiceService` object `encryptPDFUsingCertificates` en geeft de volgende waarden door:

   * De `BLOB` -object dat het te coderen PDF-document bevat.
   * De `Object` array die certificaatgegevens opslaat.
   * De `CertificateEncryptionOptionSpec` object dat opties voor codering tijdens runtime bevat.

   De `encryptPDFUsingCertificates` methode retourneert een `BLOB` -object dat een met een certificaat gecodeerd PDF-document bevat.

1. Sla het gecodeerde PDF-document op als een PDF-bestand.

   * Een `System.IO.FileStream` door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het beveiligde PDF-document vertegenwoordigt.
   * Maak een bytearray waarin de gegevensinhoud van de `BLOB` object dat is geretourneerd door de `encryptPDFUsingCertificates` methode. Vul de bytearray met de waarde van de `BLOB` object `binaryData` lid.
   * Een `System.IO.BinaryWriter` object door de constructor aan te roepen en de `System.IO.FileStream` object.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door het `System.IO.BinaryWriter` object `Write` en geeft u de bytearray door.

**Zie ook**

[Overzicht van de stappen](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Versleuteling op basis van een certificaat verwijderen {#removing-certificate-based-encryption}

Op een certificaat gebaseerde versleuteling kan uit een PDF-document worden verwijderd, zodat gebruikers het PDF-document in Adobe Reader of Acrobat kunnen openen. Als u versleuteling wilt verwijderen uit een PDF-document dat is versleuteld met een certificaat, moet naar een openbare sleutel worden verwezen. Nadat de versleuteling is verwijderd uit een PDF-document, is het niet meer beveiligd.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Encryptie, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-2}

Voer de volgende stappen uit om op een certificaat gebaseerde versleuteling te verwijderen uit een PDF-document:

1. Inclusief projectbestanden.
1. Maak een versleutelingsserviceclient.
1. Hiermee wordt het gecodeerde PDF-document opgehaald.
1. Versleuteling verwijderen.
1. Sla het PDF-document op als een PDF-bestand.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)

**Een versleutelingsserviceclient maken**

Om programmatically een de dienstverrichting van de Encryptie uit te voeren, moet u een de dienstcliënt van de Encryptie tot stand brengen. Als u de Java Encryption Service API gebruikt, maakt u een `EncrytionServiceClient` object. Als u de webservice-API gebruikt, maakt u een `EncryptionServiceService` object.

**Het versleutelde PDF-document ophalen**

Vraag een gecodeerd PDF-document aan om versleuteling op basis van certificaten te verwijderen. Als u probeert versleuteling te verwijderen uit een niet-versleuteld PDF-document, wordt een uitzondering gegenereerd. Op dezelfde manier wordt een uitzondering gegenereerd als u probeert versleuteling op basis van een certificaat te verwijderen uit een met een wachtwoord gecodeerd document.

**Codering verwijderen**

Als u versleutelde PDF-documenten wilt versleutelen op basis van een certificaat, hebt u zowel een versleuteld PDF-document als de persoonlijke sleutel nodig die overeenkomt met de sleutel waarmee het PDF-document is versleuteld. De aliaswaarde van de persoonlijke sleutel wordt opgegeven wanneer op een certificaat gebaseerde versleuteling wordt verwijderd uit een versleuteld PDF-document. Voor informatie over de openbare sleutel raadpleegt u [PDF-documenten versleutelen met certificaten](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-certificates).

>[!NOTE]
>
>Een persoonlijke sleutel wordt opgeslagen in de AEM Forms Trust Store. Wanneer een certificaat daar wordt geplaatst, wordt een aliaswaarde gespecificeerd.

**Het PDF-document opslaan**

Nadat op een certificaat gebaseerde versleuteling is verwijderd uit een versleuteld PDF-document, kunt u het PDF-document opslaan als een PDF-bestand. Gebruikers kunnen het PDF-document openen in Adobe Reader of Acrobat.

**Zie ook**

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

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `EncryptionServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Hiermee wordt het gecodeerde PDF-document opgehaald.

   * Een `java.io.FileInputStream` een object dat het gecodeerde PDF-document vertegenwoordigt met de constructor ervan en een tekenreekswaarde doorgeeft die de locatie van het gecodeerde PDF-document aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. Versleuteling verwijderen.

   Verwijder op certificaat-gebaseerde encryptie uit het document van de PDF door aan te halen `EncryptionServiceClient` object `removePDFCertificateSecurity` en geeft de volgende waarden door:

   * De `com.adobe.idp.Document` object dat het gecodeerde PDF-document bevat.
   * Een tekenreekswaarde die de aliasnaam van de persoonlijke sleutel opgeeft die overeenkomt met de sleutel die wordt gebruikt om het PDF-document te versleutelen.

   De `removePDFCertificateSecurity` methode retourneert een `com.adobe.idp.Document` object dat een onbeveiligd PDF-document bevat.

1. Sla het PDF-document op.

   * Een `java.io.File` en zorg dat de bestandsextensie .pdf is.
   * De `com.adobe.idp.Document` object `copyToFile` methode om de inhoud van de `Document` naar het bestand. Zorg ervoor dat u de `com.adobe.idp.Document` object dat is geretourneerd door de `removePDFCredentialSecurity` methode.

**Zie ook**

[Overzicht van de stappen](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[Snel starten (SOAP-modus): codering op basis van een certificaat verwijderen met de Java API](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-removing-certificate-based-encryption-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Op certificaten gebaseerde versleuteling verwijderen met de webservice-API {#remove-certificate-based-encryption-using-the-web-service-api}

Verwijder op een certificaat gebaseerde codering met de API voor codering (webservice):

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een versleutelingsserviceclient.

   * Een `EncryptionServiceClient` object met de standaardconstructor.
   * Een `EncryptionServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/EncryptionService?WSDL`.) U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `EncryptionServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `EncryptionServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `EncryptionServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Hiermee wordt het gecodeerde PDF-document opgehaald.

   * Een `BLOB` object met behulp van de constructor. De `BLOB` wordt gebruikt om het versleutelde PDF-document op te slaan.
   * Een `System.IO.FileStream` door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het gecodeerde PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door de inhoud van de bytearray toe te wijzen aan de `BLOB` object `MTOM` lid.

1. Versleuteling verwijderen.

   De `EncryptionServiceClient` object `removePDFCertificateSecurity` en geeft de volgende waarden door:

   * De `BLOB` object dat bestandsstreamgegevens bevat die een gecodeerd PDF-document vertegenwoordigen.
   * Een tekenreekswaarde die de aliasnaam van de openbare sleutel opgeeft die overeenkomt met de persoonlijke sleutel die wordt gebruikt om het PDF-document te versleutelen.

   De `removePDFCredentialSecurity` methode retourneert een `BLOB` object dat een onbeveiligd PDF-document bevat.

1. Sla het PDF-document op.

   * Een `System.IO.FileStream` door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het onbeveiligde PDF-document vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van de `BLOB` object dat is geretourneerd door de `removePDFPasswordSecurity` methode. Vul de bytearray met de waarde van de `BLOB` object `MTOM` lid.
   * Een `System.IO.BinaryWriter` object door de constructor aan te roepen en de `System.IO.FileStream` object.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door het `System.IO.BinaryWriter` object `Write` en geeft u de bytearray door.

**Zie ook**

[Overzicht van de stappen](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Wachtwoordversleuteling verwijderen {#removing-password-encryption}

Op wachtwoord gebaseerde versleuteling kan uit een PDF-document worden verwijderd, zodat gebruikers het PDF-document in Adobe Reader of Acrobat kunnen openen zonder een wachtwoord op te geven. Nadat op een wachtwoord gebaseerde versleuteling is verwijderd uit een PDF-document, is het document niet meer beveiligd.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Encryptie, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-3}

Voer de volgende stappen uit om op een wachtwoord gebaseerde versleuteling te verwijderen uit een PDF-document:

1. Projectbestanden opnemen
1. Maak een versleutelingsserviceclient.
1. Hiermee wordt het gecodeerde PDF-document opgehaald.
1. Verwijder het wachtwoord.
1. Sla het PDF-document op als een PDF-bestand.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

**Een versleutelingsserviceclient maken**

Om programmatically een de dienstverrichting van de Encryptie uit te voeren, moet u een de dienstcliënt van de Encryptie tot stand brengen. Als u de Java Encryption Service API gebruikt, maakt u een `EncrytionServiceClient` object. Als u de webservice-API gebruikt, maakt u een `EncryptionServiceService` object.

**Het versleutelde PDF-document ophalen**

Vraag een gecodeerd PDF-document aan om op wachtwoord gebaseerde versleuteling te verwijderen. Als u probeert versleuteling te verwijderen uit een niet-versleuteld PDF-document, wordt een uitzondering gegenereerd.

**Het wachtwoord verwijderen**

Om op wachtwoord-gebaseerde encryptie uit een gecodeerd document van de PDF te verwijderen, vereist u zowel een gecodeerd document van de PDF als een hoofdwachtwoordwaarde die wordt gebruikt om encryptie uit het document van de PDF te verwijderen. Het wachtwoord waarmee een met wachtwoord gecodeerd PDF-document wordt geopend, kan niet worden gebruikt om versleuteling te verwijderen. Er wordt een hoofdwachtwoord opgegeven wanneer het PDF-document met een wachtwoord is versleuteld. (Zie [PDF-documenten versleutelen met een wachtwoord](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password).)

**Het PDF-document opslaan**

Nadat de coderingsservice op wachtwoord gebaseerde codering uit een PDF-document heeft verwijderd, kunt u het PDF-document opslaan als een PDF-bestand. Gebruikers kunnen het PDF-document openen in Adobe Reader of Acrobat zonder een wachtwoord op te geven.

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[API voor coderingsservice - Snel aan de slag](/help/forms/developing/encryption-service-java-api-quick.md#encryption-service-java-api-quick-start-soap)

[PDF-documenten versleutelen met een wachtwoord](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password)

### Op wachtwoorden gebaseerde codering verwijderen met de Java API {#remove-password-based-encryption-using-the-java-api}

Verwijder op wachtwoord gebaseerde codering uit een PDF-document met de API voor codering (Java):

1. Inclusief projectbestanden.

   Neem JAR-bestanden van de client, zoals adobe-encryption-client.jar, op in het klassenpad van uw Java-project.

1. Maak een versleutelingsserviceclient.

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `EncryptionServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Hiermee wordt het gecodeerde PDF-document opgehaald.

   * Een `java.io.FileInputStream` een object dat het gecodeerde PDF-document vertegenwoordigt met de constructor ervan en een tekenreekswaarde doorgeeft die de locatie van het PDF-document aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. Verwijder het wachtwoord.

   Verwijder op wachtwoord-gebaseerde encryptie uit het document van de PDF door aan te halen `EncryptionServiceClient` object `removePDFPasswordSecurity` en geeft de volgende waarden door:

   * A `com.adobe.idp.Document` object dat het gecodeerde PDF-document bevat.
   * Een tekenreekswaarde die de hoofdwachtwoordwaarde opgeeft die wordt gebruikt om versleuteling te verwijderen uit het PDF-document.

   De `removePDFPasswordSecurity` methode retourneert een `com.adobe.idp.Document` object dat een onbeveiligd PDF-document bevat.

1. Sla het PDF-document op.

   * Een `java.io.File` en zorg ervoor dat de bestandsnaamextensie .pdf is.
   * De `com.adobe.idp.Document` object `copyToFile` methode om de inhoud van de `Document` naar het bestand. Zorg ervoor dat u de `Document` object dat is geretourneerd door de `removePDFPasswordSecurity` methode.

**Zie ook**

[Snel starten (SOAP-modus): codering op basis van wachtwoord verwijderen met de Java API](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-removing-password-based-encryption-using-the-java-api)

### Op wachtwoorden gebaseerde codering verwijderen met de webservice-API {#remove-password-based-encryption-using-the-web-service-api}

Verwijder op wachtwoord gebaseerde codering met de API voor codering (webservice):

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een versleutelingsserviceclient.

   * Een `EncryptionServiceClient` object met de standaardconstructor.
   * Een `EncryptionServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/EncryptionService?WSDL`.) U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `EncryptionServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `EncryptionServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `EncryptionServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Hiermee wordt het gecodeerde PDF-document opgehaald.

   * Een `BLOB` object met behulp van de constructor. De `BLOB` wordt gebruikt om een met wachtwoord gecodeerd PDF-document op te slaan.
   * Een `System.IO.FileStream` door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het gecodeerde PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door de inhoud van de bytearray toe te wijzen aan de `BLOB` object `MTOM` lid.

1. Verwijder het wachtwoord.

   De `EncryptionServiceService` object `removePDFPasswordSecurity` en geeft de volgende waarden door:

   * De `BLOB` object dat bestandsstreamgegevens bevat die een gecodeerd PDF-document vertegenwoordigen.
   * Een tekenreekswaarde die de wachtwoordwaarde opgeeft die wordt gebruikt om versleuteling te verwijderen uit het PDF-document. Deze waarde wordt opgegeven wanneer het PDF-document met een wachtwoord wordt gecodeerd.

   De `removePDFPasswordSecurity` methode retourneert een `BLOB` object dat een onbeveiligd PDF-document bevat.

1. Sla het PDF-document op.

   * Een `System.IO.FileStream` door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het onbeveiligde PDF-document vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van de `BLOB` object dat is geretourneerd door de `removePDFPasswordSecurity` methode. Vul de bytearray met de waarde van de `BLOB` object `MTOM` lid.
   * Een `System.IO.BinaryWriter` object door de constructor aan te roepen en de `System.IO.FileStream` object.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door het `System.IO.BinaryWriter` object `Write` en geeft u de bytearray door.

**Zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Versleutelde PDF-documenten ontgrendelen {#unlocking-encrypted-pdf-documents}

Een met wachtwoord gecodeerd of met een certificaat gecodeerd PDF-document moet worden ontgrendeld voordat een andere AEM Forms-bewerking kan worden uitgevoerd. Als u een bewerking probeert uit te voeren op een gecodeerd PDF-document, wordt een uitzondering gegenereerd. Nadat u een gecodeerd PDF-document hebt ontgrendeld, kunt u er een of meer bewerkingen op uitvoeren. Deze bewerkingen kunnen tot andere services behoren, zoals de Acrobat Reader DC Extension Service.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Encryptie, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-4}

Voer de volgende stappen uit om een gecodeerd PDF-document te ontgrendelen:

1. Inclusief projectbestanden.
1. Maak een versleutelingsserviceclient.
1. Hiermee wordt het gecodeerde PDF-document opgehaald.
1. Ontgrendel het document.
1. Voer een AEM Forms-bewerking uit.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)

**Een versleutelingsserviceclient maken**

Om programmatically een de dienstverrichting van de Encryptie uit te voeren, moet u een de dienstcliënt van de Encryptie tot stand brengen. Als u de Java Encryption Service API gebruikt, maakt u een `EncrytionServiceClient` object. Als u de webservice-API gebruikt, maakt u een `EncryptionServiceService` object.

**Het versleutelde PDF-document ophalen**

Vraag een versleuteld PDF-document aan om dit te ontgrendelen. Als u probeert een PDF-document te ontgrendelen dat niet is versleuteld, wordt een uitzondering gegenereerd.

**Het document ontgrendelen**

Als u een met een wachtwoord gecodeerd PDF-document wilt ontgrendelen, hebt u zowel een versleuteld PDF-document als een wachtwoordwaarde nodig om een met een wachtwoord gecodeerd PDF-document te openen. Deze waarde wordt opgegeven wanneer het PDF-document met een wachtwoord wordt gecodeerd. (Zie [PDF-documenten versleutelen met een wachtwoord](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password).)

Als u een met een certificaat gecodeerd PDF-document wilt ontgrendelen, hebt u zowel een versleuteld PDF-document als de aliaswaarde van de openbare sleutel nodig die overeenkomt met de persoonlijke sleutel waarmee het PDF-document is versleuteld.

**AEM Forms-bewerkingen uitvoeren**

Nadat een gecodeerd PDF-document is ontgrendeld, kunt u er een andere servicebewerking op uitvoeren, zoals gebruiksrechten op toepassen. Deze bewerking behoort tot de Acrobat Reader DC Extensions-service.

**Zie ook**

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

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `EncryptionServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Hiermee wordt het gecodeerde PDF-document opgehaald.

   * Een `java.io.FileInputStream` een object dat het gecodeerde PDF-document vertegenwoordigt met de constructor ervan en een tekenreekswaarde doorgeeft die de locatie van het gecodeerde PDF-document aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. Ontgrendel het document.

   Een versleuteld PDF-document ontgrendelen door het `EncryptionServiceClient` object `unlockPDFUsingPassword` of `unlockPDFUsingCredential` methode.

   Als u een PDF-document wilt ontgrendelen dat met een wachtwoord is versleuteld, roept u de opdracht `unlockPDFUsingPassword` en geeft de volgende waarden door:

   * A `com.adobe.idp.Document` -object dat het met wachtwoord gecodeerde PDF-document bevat.
   * Een tekenreekswaarde die de wachtwoordwaarde opgeeft waarmee een met wachtwoord gecodeerd PDF-document wordt geopend. Deze waarde wordt opgegeven wanneer het PDF-document met een wachtwoord wordt gecodeerd.

   Als u een PDF-document wilt ontgrendelen dat met een certificaat is versleuteld, roept u de opdracht `unlockPDFUsingCredential` en geeft de volgende waarden door:

   * A `com.adobe.idp.Document` -object dat het met een certificaat gecodeerde PDF-document bevat.
   * Een tekenreekswaarde die de aliasnaam van de openbare sleutel opgeeft die overeenkomt met de persoonlijke sleutel die wordt gebruikt om het PDF-document te versleutelen.

   De `unlockPDFUsingPassword` en `unlockPDFUsingCredential` methoden retourneren beide een `com.adobe.idp.Document` -object dat u doorgeeft aan een andere AEM Forms Java-methode om een bewerking uit te voeren.

1. Voer een AEM Forms-bewerking uit.

   Voer een AEM Forms-bewerking uit op het ontgrendelde PDF-document om aan uw zakelijke vereisten te voldoen. Als u bijvoorbeeld gebruiksrechten wilt toepassen op een ontgrendeld PDF-document, geeft u de opdracht `com.adobe.idp.Document` object dat door een van de `unlockPDFUsingPassword` of `unlockPDFUsingCredential` aan de `ReaderExtensionsServiceClient` object `applyUsageRights` methode.

**Zie ook**

[Overzicht van de stappen](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[Snel starten (SOAP-modus): Een gecodeerd PDF-document ontgrendelen met de Java API](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-unlocking-an-encrypted-pdf-document-using-the-java-api) (SOAP-modus)

[Gebruiksrechten toepassen op PDF-documenten](/help/forms/developing/assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een gecodeerd PDF-document ontgrendelen met de webservice-API {#unlock-an-encrypted-pdf-document-using-the-web-service-api}

Een gecodeerd PDF-document ontgrendelen met de API voor versleuteling (webservice):

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een versleutelingsserviceclient.

   * Een `EncryptionServiceClient` object met de standaardconstructor.
   * Een `EncryptionServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/EncryptionService?WSDL`.) U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `EncryptionServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `EncryptionServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `EncryptionServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Een versleuteld PDF-document ophalen.

   * Een `BLOB` object met behulp van de constructor.
   * Een `System.IO.FileStream` door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het gecodeerde PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door de inhoud van de bytearray toe te wijzen aan de `BLOB` object `MTOM` lid.

1. Ontgrendel het document.

   Een versleuteld PDF-document ontgrendelen door het `EncryptionServiceClient` object `unlockPDFUsingPassword` of `unlockPDFUsingCredential` methode.

   Als u een PDF-document wilt ontgrendelen dat met een wachtwoord is versleuteld, roept u de opdracht `unlockPDFUsingPassword` en geeft de volgende waarden door:

   * A `BLOB` -object dat het met wachtwoord gecodeerde PDF-document bevat.
   * Een tekenreekswaarde die de wachtwoordwaarde opgeeft waarmee een met wachtwoord gecodeerd PDF-document wordt geopend. Deze waarde wordt opgegeven wanneer het PDF-document met een wachtwoord wordt gecodeerd.

   Als u een PDF-document wilt ontgrendelen dat met een certificaat is versleuteld, roept u de opdracht `unlockPDFUsingCredential` en geeft de volgende waarden door:

   * A `BLOB` -object dat het met een certificaat gecodeerde PDF-document bevat.
   * Een tekenreekswaarde die de aliasnaam van de openbare sleutel opgeeft die overeenkomt met de persoonlijke sleutel die wordt gebruikt om het PDF-document te versleutelen.

   De `unlockPDFUsingPassword` en `unlockPDFUsingCredential` methoden retourneren beide een `com.adobe.idp.Document` -object dat u doorgeeft aan een andere AEM Forms-methode om een bewerking uit te voeren.

1. Voer een AEM Forms-bewerking uit.

   Voer een AEM Forms-bewerking uit op het ontgrendelde PDF-document om aan uw zakelijke vereisten te voldoen. Als u bijvoorbeeld gebruiksrechten wilt toepassen op het ontgrendelde PDF-document, geeft u de opdracht `BLOB` object dat door een van de `unlockPDFUsingPassword` of `unlockPDFUsingCredential` aan de `ReaderExtensionsServiceClient` object `applyUsageRights` methode.

**Zie ook**

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
>Voor meer informatie over de dienst van de Encryptie, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-5}

Ga als volgt te werk om te bepalen welk type codering een PDF-document beveiligt:

1. Inclusief projectbestanden.
1. Maak een versleutelingsserviceclient.
1. Hiermee wordt het gecodeerde PDF-document opgehaald.
1. Bepaal het versleutelingstype.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)

**Een serviceclient maken**

Om programmatically een de dienstverrichting van de Encryptie uit te voeren, moet u een de dienstcliënt van de Encryptie tot stand brengen. Als u de Java Encryption Service API gebruikt, maakt u een `EncrytionServiceClient` object. Als u de webservice-API gebruikt, maakt u een `EncryptionServiceService` object.

**Het versleutelde PDF-document ophalen**

Vraag een PDF-document aan om het type codering te bepalen dat deze beveiligt.

**Het versleutelingstype bepalen**

U kunt bepalen welk type versleuteling een PDF-document beveiligt. Als het PDF-document niet is beveiligd, geeft de coderingsservice aan dat het PDF-document niet is beveiligd.

**Zie ook**

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

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `EncryptionServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Hiermee wordt het gecodeerde PDF-document opgehaald.

   * Een `java.io.FileInputStream` -object dat het PDF-document vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het PDF-document aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. Bepaal het versleutelingstype.

   * Bepaal het encryptietype door het roepen van `EncryptionServiceClient` object `getPDFEncryption` en het doorgeven van de `com.adobe.idp.Document` object dat het PDF-document bevat. Deze methode retourneert een `EncryptionTypeResult` object.
   * De `EncryptionTypeResult` object `getEncryptionType` methode. Deze methode retourneert een `EncryptionType` enum waarde die het encryptietype specificeert. Als het PDF-document bijvoorbeeld is beveiligd met op een wachtwoord gebaseerde codering, retourneert deze methode `EncryptionType.PASSWORD`.

**Zie ook**

[Overzicht van de stappen](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[Snel starten (SOAP-modus): Coderingstype bepalen met de Java API](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-determining-encryption-type-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Het versleutelingstype bepalen met de webservice-API {#determine-the-encryption-type-using-the-web-service-api}

Bepaal het type codering waarmee een PDF-document wordt beveiligd met de API voor versleuteling (webservice):

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een serviceclient.

   * Een `EncryptionServiceClient` object met de standaardconstructor.
   * Een `EncryptionServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/EncryptionService?WSDL`.) U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `EncryptionServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `EncryptionServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `EncryptionServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Hiermee wordt het gecodeerde PDF-document opgehaald.

   * Een `BLOB` object met behulp van de constructor.
   * Een `System.IO.FileStream` door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het gecodeerde PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door de inhoud van de bytearray toe te wijzen aan de `BLOB` object `MTOM` lid.

1. Bepaal het versleutelingstype.

   * De `EncryptionServiceClient` object `getPDFEncryption` en geeft de `BLOB` object dat het PDF-document bevat. Deze methode retourneert een `EncryptionTypeResult` object.
   * Hiermee wordt de waarde van de opdracht `EncryptionTypeResult` object `encryptionType` gegevensmethode. Als het PDF-document bijvoorbeeld is beveiligd met codering op basis van een wachtwoord, is de waarde van dit gegevenslid `EncryptionType.PASSWORD`.

**Zie ook**

[Overzicht van de stappen](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
