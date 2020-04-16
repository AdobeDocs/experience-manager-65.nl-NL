---
title: PDF-documenten versleutelen en ontsleutelen
seo-title: PDF-documenten versleutelen en ontsleutelen
description: 'null'
seo-description: 'null'
uuid: 4e4e2716-c21f-4bfe-ae7a-7e91442414ef
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 5e4bda3a-5648-4c0f-b2f8-bdbebb88f537
translation-type: tm+mt
source-git-commit: f9389a06f9c2cd720919486765cee76257f272c3

---


# PDF-documenten versleutelen en ontsleutelen {#encrypting-and-decrypting-pdf-documents}

**Over de coderingsservice**

Met de coderingsservice kunt u documenten versleutelen en decoderen. Wanneer een document wordt versleuteld, wordt de inhoud ervan onleesbaar. Een geautoriseerde gebruiker kan het document decoderen om toegang tot de inhoud te krijgen. Als een PDF-document is versleuteld met een wachtwoord, moet de gebruiker het wachtwoord voor openen opgeven voordat het document kan worden weergegeven in Adobe Reader of Adobe Acrobat. Als een PDF-document met een certificaat is versleuteld, moet de gebruiker het PDF-document decoderen met de openbare sleutel die overeenkomt met het certificaat (persoonlijke sleutel) dat is gebruikt om het PDF-document te versleutelen.

U kunt deze taken uitvoeren met behulp van de coderingsservice:

* Codeer een PDF-document met een wachtwoord. (Zie PDF-documenten [versleutelen met een wachtwoord](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password).)
* Codeer een PDF-document met een certificaat. (Zie PDF-documenten [versleutelen met certificaten](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-certificates).)
* Verwijder op wachtwoord gebaseerde versleuteling uit een PDF-document. (Zie [Wachtwoordversleuteling](encrypting-decrypting-pdf-documents.md#removing-password-encryption)verwijderen.)
* Op een certificaat gebaseerde versleuteling verwijderen uit een PDF-document. (Zie Op certificaat gebaseerde codering [verwijderen](encrypting-decrypting-pdf-documents.md#removing-certificate-based-encryption).)
* Ontgrendel het PDF-document zodat andere servicebewerkingen kunnen worden uitgevoerd. Nadat bijvoorbeeld een PDF-document met wachtwoordcodering is ontgrendeld, kunt u er een digitale handtekening op toepassen. (Zie Gecodeerde PDF-documenten [ontgrendelen](encrypting-decrypting-pdf-documents.md#unlocking-encrypted-pdf-documents).)
* Bepaal het versleutelingstype van een beveiligd PDF-document. (Zie [Coderingstype](encrypting-decrypting-pdf-documents.md#determining-encryption-type)bepalen.)

>[!NOTE]
>
>Voor meer informatie over de dienst van de Encryptie, zie de Verwijzing van de [Diensten voor Vormen](https://www.adobe.com/go/learn_aemforms_services_63)AEM.

## PDF-documenten versleutelen met een wachtwoord {#encrypting-pdf-documents-with-a-password}

Wanneer u een PDF-document versleutelt met een wachtwoord, moet de gebruiker het wachtwoord opgeven om het PDF-document te openen in Adobe Reader of Acrobat. Voordat een andere bewerking in AEM Forms, zoals het digitaal ondertekenen van het PDF-document, op het document kan worden uitgevoerd, moet een met wachtwoord gecodeerd PDF-document worden ontgrendeld.

>[!NOTE]
>
>Als u een gecodeerd PDF-document uploadt naar de opslagplaats van AEM Forms, kan het PDF-document niet worden gedecodeerd en de XDP-inhoud niet worden uitgepakt. U wordt aangeraden een document niet te versleutelen voordat u het uploadt naar de opslagplaats van AEM Forms. (Zie Bronnen [schrijven](/help/forms/developing/aem-forms-repository.md#writing-resources).)

>[!NOTE]
>
>Voor meer informatie over de dienst van de Encryptie, zie de Verwijzing van de [Diensten voor Vormen](https://www.adobe.com/go/learn_aemforms_services_63)AEM.

### Overzicht van de stappen {#summary-of-steps}

Voer de volgende stappen uit om een PDF-document met een wachtwoord te coderen:

1. Inclusief projectbestanden.
1. Maak een Encryption Client API-object.
1. Een PDF-document ophalen om te versleutelen.
1. Stel opties voor codering tijdens runtime in.
1. Voeg het wachtwoord toe.
1. Sla het versleutelde PDF-document op als een PDF-bestand.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM-formulieren worden geïmplementeerd op JBoss)

**Een Encryption Client API-object maken**

Om programmatically een de dienstverrichting van de Encryptie uit te voeren, moet u een de dienstcliënt van de Encryptie tot stand brengen.

**Een PDF-document ophalen om te versleutelen**

U moet een niet-versleuteld PDF-document verkrijgen om het document met een wachtwoord te versleutelen. Als u probeert een PDF-document te beveiligen dat al is versleuteld, veroorzaakt u een uitzondering.

**Opties voor codering tijdens runtime instellen**

Als u een PDF-document met een wachtwoord wilt versleutelen, geeft u vier waarden op, waaronder twee wachtwoordwaarden. Het eerste wachtwoord wordt gebruikt om het PDF-document te versleutelen en moet worden opgegeven bij het openen van het PDF-document. De tweede wachtwoordwaarde, de hoofdwachtwoordwaarde, wordt gebruikt om versleuteling uit het PDF-document te verwijderen. Wachtwoordwaarden zijn hoofdlettergevoelig en deze twee wachtwoordwaarden kunnen niet dezelfde waarden zijn.

U moet opgeven welke PDF-documentbronnen u wilt versleutelen. U kunt het gehele PDF-document versleutelen, met uitzondering van de metagegevens van het document of alleen de bijlagen van het document. Als u alleen de bijlagen van het document versleutelt, wordt een gebruiker om een wachtwoord gevraagd wanneer hij of zij toegang probeert te krijgen tot de bestandsbijlagen.

Bij het versleutelen van een PDF-document kunt u machtigingen opgeven die aan het beveiligde document zijn gekoppeld. Door machtigingen op te geven, kunt u de handelingen beheren die een gebruiker die een PDF-document met een wachtwoord opent, mag uitvoeren. Als u bijvoorbeeld met succes formuliergegevens wilt extraheren, moet u de volgende machtigingen instellen:

* PASSWORD_EDIT_ADD
* WACHTWOORD_EDIT_MODIFY

>[!NOTE]
>
>Machtigingen worden opgegeven als `PasswordEncryptionPermission` opsommingswaarden.

**Het wachtwoord toevoegen**

Nadat u een onbeveiligd PDF-document hebt opgehaald en waarden voor de codering hebt ingesteld, kunt u een wachtwoord aan het PDF-document toevoegen.

**Het versleutelde PDF-document opslaan als een PDF-bestand**

U kunt het met een wachtwoord gecodeerde PDF-document opslaan als een PDF-bestand.

**Zie ook**

[Een PDF-document versleutelen met de Java API](encrypting-decrypting-pdf-documents.md#encrypt-a-pdf-document-using-the-java-api)

[Een PDF-document versleutelen met de webservice-API](encrypting-decrypting-pdf-documents.md#encrypting-a-pdf-document-using-the-web-service-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[API voor coderingsservice - Snel aan de slag](/help/forms/developing/encryption-service-java-api-quick.md#encryption-service-java-api-quick-start-soap)

[PDF-documenten versleutelen met certificaten](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-certificates)

### Een PDF-document versleutelen met de Java API {#encrypt-a-pdf-document-using-the-java-api}

Codeer een PDF-document met een wachtwoord met behulp van de API voor versleuteling (Java):

1. Inclusief projectbestanden.

   Neem JAR-bestanden van de client, zoals adobe-encryption-client.jar, op in het klassenpad van uw Java-project.

1. Maak een versleutelingsclient-API.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `EncryptionServiceClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Een PDF-document ophalen om te versleutelen.

   * Maak een `java.io.FileInputStream` object dat staat voor het PDF-document dat moet worden versleuteld met de constructor ervan en geef een tekenreekswaarde door die de locatie van het PDF-document aangeeft.
   * Maak een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en het `java.io.FileInputStream` object door te geven.

1. Stel opties voor codering tijdens runtime in.

   * Maak een `PasswordEncryptionOptionSpec` object door de constructor ervan aan te roepen.
   * Geef de bronnen van het PDF-document op die u wilt versleutelen door de methode van het `PasswordEncryptionOptionSpec` object aan te roepen en een `setEncryptOption` `PasswordEncryptionOption` opsommingswaarde door te geven die de documentbronnen aangeeft die u wilt versleutelen. Als u bijvoorbeeld het gehele PDF-document wilt versleutelen, inclusief de metagegevens en de bijlagen, geeft u op `PasswordEncryptionOption.ALL`.
   * Maak een `java.util.List` object dat de versleutelingsmachtigingen opslaat met de `ArrayList` constructor.
   * Geef een machtiging op door de methode van het `java.util.List` `add` object aan te roepen en een opsommingswaarde door te geven die overeenkomt met de machtiging die u wilt instellen. Als u bijvoorbeeld de machtiging wilt instellen waarmee een gebruiker gegevens in het PDF-document kan kopiëren, geeft u op `PasswordEncryptionPermission.PASSWORD_EDIT_COPY`. (Herhaal deze stap voor elke machtiging die moet worden ingesteld).
   * Geef de compatibiliteitsoptie Acrobat op door de methode van het `PasswordEncryptionOptionSpec` `setCompatability` object aan te roepen en een opsommingswaarde door te geven die het compatibiliteitsniveau van Acrobat opgeeft. U kunt bijvoorbeeld opgeven `PasswordEncryptionCompatability.ACRO_7`.
   * Geef de wachtwoordwaarde op waarmee een gebruiker het gecodeerde PDF-document kan openen door de methode van het `PasswordEncryptionOptionSpec` `setDocumentOpenPassword` object aan te roepen en een tekenreekswaarde door te geven die het open wachtwoord vertegenwoordigt.
   * Geef de waarde van het hoofdwachtwoord op waarmee een gebruiker versleuteling uit het PDF-document kan verwijderen door de methode van het `PasswordEncryptionOptionSpec` `setPermissionPassword` object aan te roepen en een tekenreekswaarde door te geven die het hoofdwachtwoord vertegenwoordigt.

1. Voeg het wachtwoord toe.

   Codeer het PDF-document door de methode van het `EncryptionServiceClient` `encryptPDFUsingPassword` object aan te roepen en de volgende waarden door te geven:

   * Het `com.adobe.idp.Document` object dat het PDF-document bevat dat met het wachtwoord moet worden gecodeerd.
   * Het `PasswordEncryptionOptionSpec` object dat opties voor codering tijdens runtime bevat.
   De `encryptPDFUsingPassword` methode retourneert een `com.adobe.idp.Document` object dat een PDF-document met een wachtwoord bevat.

1. Sla het versleutelde PDF-document op als een PDF-bestand.

   * Maak een `java.io.File` object en zorg dat de bestandsextensie .pdf is.
   * Roep de `com.adobe.idp.Document` methode van het `copyToFile` object aan om de inhoud van het `com.adobe.idp.Document` object naar het bestand te kopiëren. Zorg ervoor dat u het `com.adobe.idp.Document` object gebruikt dat door de `encryptPDFUsingPassword` methode is geretourneerd.

**Zie ook**

[Overzicht van de stappen](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[Snel starten (SOAP-modus): Een PDF-document versleutelen met de Java API](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-encrypting-a-pdf-document-using-the-java-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een PDF-document versleutelen met de webservice-API {#encrypting-a-pdf-document-using-the-web-service-api}

Codeer een PDF-document met een wachtwoord met de API voor versleuteling (webservice):

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Encryption Client API-object.

   * Maak een `EncryptionServiceClient` object met de standaardconstructor.
   * Maak een `EncryptionServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/EncryptionService?WSDL`.) U hoeft het `lc_version` kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `EncryptionServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het veld `EncryptionServiceClient.ClientCredentials.UserName.UserName`.
      * Wijs de bijbehorende wachtwoordwaarde aan het veld toe `EncryptionServiceClient.ClientCredentials.UserName.Password`.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Een PDF-document ophalen om te versleutelen.

   * Maak een `BLOB` object met de constructor ervan. Met dit `BLOB` object wordt een PDF-document opgeslagen dat met een wachtwoord is versleuteld.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het PDF-document dat moet worden versleuteld en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de methode van het `System.IO.FileStream` `Read` object aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` object door de inhoud van de bytearray toe te wijzen aan het gegevenslid van het `BLOB` object `MTOM` .

1. Stel opties voor codering tijdens runtime in.

   * Maak een `PasswordEncryptionOptionSpec` object met de constructor ervan.
   * Geef de bronnen van het PDF-document op die u wilt versleutelen door een `PasswordEncryptionOption` opsommingswaarde toe te wijzen aan het `PasswordEncryptionOptionSpec` gegevenslid van het `encryptOption` object. Als u de volledige PDF wilt versleutelen, inclusief de metagegevens en de bijlagen, wijst u `PasswordEncryptionOption.ALL` dit gegevenslid toe.
   * Geef de compatibiliteitsoptie Acrobat op door een `PasswordEncryptionCompatability` opsommingswaarde toe te wijzen aan het `PasswordEncryptionOptionSpec` gegevenslid van het `compatability` object. Wijs bijvoorbeeld toe `PasswordEncryptionCompatability.ACRO_7` aan dit gegevenslid.
   * Geef de wachtwoordwaarde op waarmee een gebruiker het gecodeerde PDF-document kan openen door een tekenreekswaarde toe te wijzen die het geopende wachtwoord vertegenwoordigt voor het `PasswordEncryptionOptionSpec` gegevenslid van het `documentOpenPassword` object.
   * Geef de wachtwoordwaarde op waarmee een gebruiker versleuteling uit het PDF-document kan verwijderen door een tekenreekswaarde toe te wijzen die het hoofdwachtwoord vertegenwoordigt aan het `PasswordEncryptionOptionSpec` gegevenslid van het `permissionPassword` object.

1. Voeg het wachtwoord toe.

   Codeer het PDF-document door de methode van het `EncryptionServiceClient` `encryptPDFUsingPassword` object aan te roepen en de volgende waarden door te geven:

   * Het `BLOB` object dat het PDF-document bevat dat met het wachtwoord moet worden gecodeerd.
   * Het `PasswordEncryptionOptionSpec` object dat opties voor codering tijdens runtime bevat.
   De `encryptPDFUsingPassword` methode retourneert een `BLOB` object dat een PDF-document met een wachtwoord bevat.

1. Sla het versleutelde PDF-document op als een PDF-bestand.

   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het beveiligde PDF-document vertegenwoordigt.
   * Maak een bytearray met de gegevensinhoud van het `BLOB` object dat door de `encryptPDFUsingPassword` methode is geretourneerd. Vul de bytearray met de waarde van het `BLOB` `MTOM` gegevenslid van het object.
   * Maak een `System.IO.BinaryWriter` object door de constructor ervan aan te roepen en het `System.IO.FileStream` object door te geven.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door de methode van het `System.IO.BinaryWriter` `Write` object aan te roepen en de bytearray door te geven.

**Zie ook**

[Overzicht van de stappen](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[AEM-formulieren aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM-formulieren aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## PDF-documenten versleutelen met certificaten {#encrypting-pdf-documents-with-certificates}

Met codering op basis van certificaten kunt u een document voor specifieke ontvangers versleutelen met behulp van technologie voor openbare sleutels. Verschillende ontvangers kunnen verschillende machtigingen voor het document krijgen. Veel aspecten van versleuteling worden mogelijk gemaakt door de technologie van de openbare sleutel. Een algoritme wordt gebruikt om twee grote aantallen te produceren, die als *sleutels* worden bekend, die de volgende eigenschappen hebben:

* Eén sleutel wordt gebruikt om een set gegevens te coderen. Vervolgens kan alleen de andere sleutel worden gebruikt om de gegevens te decoderen.
* Het is onmogelijk om de ene sleutel van de andere te onderscheiden.

Een van de toetsen fungeert als de persoonlijke sleutel van een gebruiker. Het is belangrijk dat alleen de gebruiker toegang heeft tot deze sleutel. De andere sleutel is de openbare sleutel van de gebruiker, die met anderen kan worden gedeeld.

Een certificaat met een openbare sleutel bevat de openbare sleutel van een gebruiker en identificeert informatie. De indeling X.509 wordt gebruikt voor het opslaan van certificaten. Certificaten worden doorgaans uitgegeven en digitaal ondertekend door een certificeringsinstantie (CA), een erkende entiteit die een zekere mate van vertrouwen biedt in de geldigheid van het certificaat. Certificaten hebben een vervaldatum waarna ze niet meer geldig zijn. Bovendien bevatten de certificaatintrekkingslijsten (CRL&#39;s) informatie over certificaten die vóór de vervaldatum zijn ingetrokken. CRL&#39;s worden periodiek gepubliceerd door certificeringsinstanties. De intrekkingsstatus van een certificaat kan ook via het online certificaatstatusprotocol (OCSP) via het netwerk worden opgehaald.

>[!NOTE]
>
>Als u een gecodeerd PDF-document uploadt naar de opslagplaats van AEM Forms, kan het PDF-document niet worden gedecodeerd en de XDP-inhoud niet worden uitgepakt. U wordt aangeraden een document niet te versleutelen voordat u het uploadt naar de opslagplaats van AEM Forms. (Zie Bronnen [schrijven](/help/forms/developing/aem-forms-repository.md#writing-resources).)

>[!NOTE]
>
>Voordat u een PDF-document kunt versleutelen met een certificaat, moet u ervoor zorgen dat u het certificaat toevoegt aan AEM-formulieren. Een certificaat wordt toegevoegd gebruikend beleidsconsole of programmatically gebruikend de Manager API van het Vertrouwen. (Zie [Referenties importeren met de Betrouwbaarheidsbeheer-API](/help/forms/developing/credentials.md#importing-credentials-by-using-the-trust-manager-api).)

>[!NOTE]
>
>Voor meer informatie over de dienst van de Encryptie, zie de Verwijzing van de [Diensten voor Vormen](https://www.adobe.com/go/learn_aemforms_services_63)AEM.

### Overzicht van de stappen {#summary_of_steps-1}

Voer de volgende stappen uit om een PDF-document te versleutelen met een certificaat:

1. Inclusief projectbestanden.
1. Maak een Encryption Client API-object.
1. Een PDF-document ophalen om te versleutelen.
1. Verwijs naar het certificaat.
1. Stel opties voor codering tijdens runtime in.
1. Maak een met een certificaat gecodeerd PDF-document.
1. Sla het versleutelde PDF-document op als een PDF-bestand.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)
* jbossall-client.jar (vereist als AEM-formulieren worden geïmplementeerd op JBoss Application Server)

**Een Encryption Client API-object maken**

Om programmatically een de dienstverrichting van de Encryptie uit te voeren, moet u een de dienstcliënt van de Encryptie tot stand brengen. Als u de Java Encryption Service API gebruikt, maakt u een `EncrytionServiceClient` object. Maak een `EncryptionServiceService` object als u de API van de webservice Encryption Service gebruikt.

**Een PDF-document ophalen om te versleutelen**

U moet een niet-versleuteld PDF-document verkrijgen om te versleutelen. Als u probeert een PDF-document te beveiligen dat al is versleuteld, wordt een uitzondering gegenereerd.

**Verwijzing naar het certificaat**

Als u een PDF-document met een certificaat wilt versleutelen, verwijst u naar een certificaat dat wordt gebruikt om een PDF-document te versleutelen. Het certificaat is een .cer-bestand, een .crt-bestand of een .pem-bestand. Een PKCS#12-bestand wordt gebruikt voor het opslaan van persoonlijke sleutels met de bijbehorende certificaten.

Wanneer u een PDF-document versleutelt met een certificaat, geeft u de machtigingen op die aan het beveiligde document zijn gekoppeld. Door machtigingen op te geven, kunt u de handelingen beheren die een gebruiker die een met een certificaat gecodeerd PDF-document opent, kan uitvoeren.

**Opties voor codering tijdens runtime instellen**

Geef de bronnen voor het PDF-document op die u wilt versleutelen. U kunt het gehele PDF-document versleutelen, met uitzondering van de metagegevens van het document of alleen de bijlagen van het document.

**Een met een certificaat gecodeerd PDF-document maken**

Nadat u een onbeveiligd PDF-document hebt opgehaald, naar het certificaat hebt verwezen en uitvoeropties hebt ingesteld, kunt u een met een certificaat gecodeerd PDF-document maken. Nadat het PDF-document is versleuteld, hebt u de bijbehorende openbare sleutel nodig om het te decoderen.

**Het versleutelde PDF-document opslaan als een PDF-bestand**

U kunt het versleutelde PDF-document opslaan als een PDF-bestand.

**Zie ook**

[Een PDF-document versleutelen met een certificaat met de Java API](encrypting-decrypting-pdf-documents.md#encrypt-a-pdf-document-with-a-certificate-using-the-java-api)

[Een PDF-document versleutelen met een certificaat met de webservice-API](encrypting-decrypting-pdf-documents.md#encrypt-a-pdf-document-with-a-certificate-using-the-web-service-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[API voor coderingsservice - Snel aan de slag](/help/forms/developing/encryption-service-java-api-quick.md#encryption-service-java-api-quick-start-soap)

[PDF-documenten versleutelen met een wachtwoord](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password)

### Een PDF-document versleutelen met een certificaat met de Java API {#encrypt-a-pdf-document-with-a-certificate-using-the-java-api}

Codeer een PDF-document met een certificaat met behulp van de API voor versleuteling (Java):

1. Inclusief projectbestanden.

   Neem JAR-bestanden van de client, zoals adobe-encryption-client.jar, op in het klassenpad van uw Java-project.

1. Maak een Encryption Client API-object.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `EncryptionServiceClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Een PDF-document ophalen om te versleutelen.

   * Maak een `java.io.FileInputStream` object dat staat voor het PDF-document dat moet worden versleuteld met de constructor ervan en geef een tekenreekswaarde door die de locatie van het PDF-document aangeeft.
   * Maak een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en het `java.io.FileInputStream` object door te geven.

1. Verwijs naar het certificaat.

   * Maak een `java.util.List` object dat machtigingsinformatie opslaat met de constructor ervan.
   * Geef de machtigingen voor het versleutelde document op door de methode van het `java.util.List` object aan te roepen en een `add` `CertificateEncryptionPermissions` opsommingswaarde door te geven die de machtigingen vertegenwoordigt die zijn verleend aan de gebruiker die het beveiligde PDF-document opent. Als u bijvoorbeeld alle machtigingen wilt opgeven, geeft u door `CertificateEncryptionPermissions.PKI_ALL_PERM`.
   * Maak een `Recipient` object met de constructor ervan.
   * Maak een `java.io.FileInputStream` object dat staat voor het certificaat dat wordt gebruikt om het PDF-document te versleutelen met de constructor ervan en geef een tekenreekswaarde door die de locatie van het certificaat opgeeft.
   * Maak een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en het `java.io.FileInputStream` object dat het certificaat vertegenwoordigt door te geven.
   * Roep de `Recipient` methode van het `setX509Cert` object aan en geef het `com.adobe.idp.Document` object met het certificaat door. (Bovendien kan het `Recipient`object een Truststore-certificaatalias of LDAP-URL hebben als certificaatbron.)
   * Maak een `CertificateEncryptionIdentity` object dat machtiging- en certificaatgegevens opslaat met de constructor ervan.
   * Roep de `CertificateEncryptionIdentity` methode van het `setPerms` object aan en geef het `java.util.List` object door dat machtigingsgegevens opslaat.
   * Roep de `CertificateEncryptionIdentity` methode van het `setRecipient` object aan en geef het `Recipient` object door dat certificaatgegevens opslaat.
   * Maak een `java.util.List` object dat certificaatinformatie opslaat met de constructor ervan.
   * Roep de methode add van het `java.util.List` object aan en geef het `CertificateEncryptionIdentity` object door. (Dit `java.util.List` object wordt als een parameter aan de `encryptPDFUsingCertificates` methode doorgegeven.)

1. Stel opties voor codering tijdens runtime in.

   * Maak een `CertificateEncryptionOptionSpec` object door de constructor ervan aan te roepen.
   * Geef de bronnen van het PDF-document op die u wilt versleutelen door de methode van het `CertificateEncryptionOptionSpec` object aan te roepen en een `setOption` `CertificateEncryptionOption` opsommingswaarde door te geven die de documentbronnen aangeeft die u wilt versleutelen. Als u bijvoorbeeld het gehele PDF-document wilt versleutelen, inclusief de metagegevens en de bijlagen, geeft u op `CertificateEncryptionOption.ALL`.
   * Geef de compatibiliteitsoptie Acrobat op door de methode van het `CertificateEncryptionOptionSpec` object aan te roepen en een `setCompat` `CertificateEncryptionCompatibility` opsommingswaarde door te geven die het compatibiliteitsniveau van Acrobat aangeeft. U kunt bijvoorbeeld opgeven `CertificateEncryptionCompatibility.ACRO_7`.

1. Maak een met een certificaat gecodeerd PDF-document.

   Codeer het PDF-document met een certificaat door de methode van het `EncryptionServiceClient` `encryptPDFUsingCertificates` object aan te roepen en de volgende waarden door te geven:

   * Het `com.adobe.idp.Document` object dat het te versleutelen PDF-document bevat.
   * Het `java.util.List` object dat certificaatgegevens opslaat.
   * Het `CertificateEncryptionOptionSpec` object dat opties voor codering tijdens runtime bevat.
   De `encryptPDFUsingCertificates` methode retourneert een `com.adobe.idp.Document` object dat een met een certificaat gecodeerd PDF-document bevat.

1. Sla het versleutelde PDF-document op als een PDF-bestand.

   * Maak een `java.io.File` object en zorg dat de bestandsnaamextensie .pdf is.
   * Roep de `com.adobe.idp.Document` methode van het `copyToFile` object aan om de inhoud van het `com.adobe.idp.Document` object naar het bestand te kopiëren. Zorg ervoor dat u het `com.adobe.idp.Document` object gebruikt dat door de `encryptPDFUsingCertificates` methode is geretourneerd.

**Zie ook**

[Overzicht van de stappen](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[Snel starten (SOAP-modus): Een PDF-document versleutelen met een certificaat met de Java API](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-encrypting-a-pdf-document-with-a-certificate-using-the-java-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een PDF-document versleutelen met een certificaat met de webservice-API {#encrypt-a-pdf-document-with-a-certificate-using-the-web-service-api}

Codeer een PDF-document met een certificaat met behulp van de API voor versleuteling (webservice):

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Encryption Client API-object.

   * Maak een `EncryptionServiceClient` object met de standaardconstructor.
   * Maak een `EncryptionServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/EncryptionService?WSDL`.) U hoeft het `lc_version` kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `EncryptionServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het veld `EncryptionServiceClient.ClientCredentials.UserName.UserName`.
      * Wijs de bijbehorende wachtwoordwaarde aan het veld toe `EncryptionServiceClient.ClientCredentials.UserName.Password`.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Een PDF-document ophalen om te versleutelen.

   * Maak een `BLOB` object met de constructor ervan. Met dit `BLOB` object wordt een PDF-document opgeslagen dat met een certificaat is versleuteld.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het PDF-document dat moet worden versleuteld en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de methode van het `System.IO.FileStream` `Read` object aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` object door de `MTOM` eigenschap ervan toe te wijzen met de inhoud van de bytearray.

1. Verwijs naar het certificaat.

   * Maak een `Recipient` object met de constructor ervan. In dit object worden certificaatgegevens opgeslagen.
   * Maak een `BLOB` object met de constructor ervan. In dit `BLOB` object wordt het certificaat opgeslagen waarmee het PDF-document wordt versleuteld.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het certificaat en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de methode van het `System.IO.FileStream` `Read` object aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` object door de inhoud van de bytearray toe te wijzen aan het gegevenslid van het `BLOB` object `MTOM` .
   * Wijs het `BLOB` object dat het certificaat opslaat toe aan het `Recipient` gegevenslid van het `x509Cert` object.
   * Maak een `CertificateEncryptionIdentity` object dat certificaatinformatie opslaat met de constructor ervan.
   * Wijs het `Recipient` object toe dat het certificaat opslaat aan het gegevenslid van de ontvanger van het `CertificateEncryptionIdentity`object.
   * Maak een `Object` array en wijs het `CertificateEncryptionIdentity` object toe aan het eerste element van de `Object` array. Deze `Object` array wordt als parameter aan de `encryptPDFUsingCertificates` methode doorgegeven.

1. Stel opties voor codering tijdens runtime in.

   * Maak een `CertificateEncryptionOptionSpec` object met de constructor ervan.
   * Geef de bronnen van het PDF-document op die u wilt versleutelen door een `CertificateEncryptionOption` opsommingswaarde toe te wijzen aan het `CertificateEncryptionOptionSpec` gegevenslid van het `option` object. Als u het gehele PDF-document wilt versleutelen, inclusief de metagegevens en de bijlagen, wijst u `CertificateEncryptionOption.ALL` dit gegevenslid toe.
   * Geef de compatibiliteitsoptie Acrobat op door een `CertificateEncryptionCompatibility` opsommingswaarde toe te wijzen aan het `CertificateEncryptionOptionSpec` gegevenslid van het `compat` object. Wijs bijvoorbeeld toe `CertificateEncryptionCompatibility.ACRO_7` aan dit gegevenslid.

1. Maak een met een certificaat gecodeerd PDF-document.

   Codeer het PDF-document met een certificaat door de methode van het `EncryptionServiceService` `encryptPDFUsingCertificates` object aan te roepen en de volgende waarden door te geven:

   * Het `BLOB` object dat het te versleutelen PDF-document bevat.
   * De `Object` array die certificaatinformatie opslaat.
   * Het `CertificateEncryptionOptionSpec` object dat opties voor codering tijdens runtime bevat.
   De `encryptPDFUsingCertificates` methode retourneert een `BLOB` object dat een met een certificaat gecodeerd PDF-document bevat.

1. Sla het versleutelde PDF-document op als een PDF-bestand.

   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het beveiligde PDF-document vertegenwoordigt.
   * Maak een bytearray met de gegevensinhoud van het `BLOB` object dat door de `encryptPDFUsingCertificates` methode is geretourneerd. Vul de bytearray met de waarde van het `BLOB` `binaryData` gegevenslid van het object.
   * Maak een `System.IO.BinaryWriter` object door de constructor ervan aan te roepen en het `System.IO.FileStream` object door te geven.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door de methode van het `System.IO.BinaryWriter` `Write` object aan te roepen en de bytearray door te geven.

**Zie ook**

[Overzicht van de stappen](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[AEM-formulieren aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM-formulieren aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Versleuteling op basis van een certificaat verwijderen {#removing-certificate-based-encryption}

Op certificaten gebaseerde versleuteling kan uit een PDF-document worden verwijderd, zodat gebruikers het PDF-document kunnen openen in Adobe Reader of Acrobat. Als u versleuteling wilt verwijderen uit een PDF-document dat is versleuteld met een certificaat, moet naar een openbare sleutel worden verwezen. Nadat de versleuteling is verwijderd uit een PDF-document, is het niet meer beveiligd.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Encryptie, zie de Verwijzing van de [Diensten voor Vormen](https://www.adobe.com/go/learn_aemforms_services_63)AEM.

### Overzicht van de stappen {#summary_of_steps-2}

Voer de volgende stappen uit om op een certificaat gebaseerde versleuteling te verwijderen uit een PDF-document:

1. Inclusief projectbestanden.
1. Maak een versleutelingsserviceclient.
1. Hiermee wordt het versleutelde PDF-document opgehaald.
1. Versleuteling verwijderen.
1. Sla het PDF-document op als een PDF-bestand.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)
* jbossall-client.jar (vereist als AEM-formulieren worden geïmplementeerd op JBoss Application Server)

**Een coderingsserviceclient maken**

Om programmatically een de dienstverrichting van de Encryptie uit te voeren, moet u een de dienstcliënt van de Encryptie tot stand brengen. Als u de Java Encryption Service API gebruikt, maakt u een `EncrytionServiceClient` object. Maak een `EncryptionServiceService` object als u de API van de webservice Encryption Service gebruikt.

**Het versleutelde PDF-document ophalen**

U moet een versleuteld PDF-document verkrijgen om op een certificaat gebaseerde versleuteling te verwijderen. Als u probeert versleuteling te verwijderen uit een PDF-document dat niet is versleuteld, wordt een uitzondering gegenereerd. Op dezelfde manier wordt een uitzondering gegenereerd als u probeert versleuteling op basis van een certificaat te verwijderen uit een met een wachtwoord gecodeerd document.

**Codering verwijderen**

Als u op een certificaat gebaseerde versleuteling wilt verwijderen uit een versleuteld PDF-document, hebt u zowel een versleuteld PDF-document als de persoonlijke sleutel nodig die overeenkomt met de sleutel waarmee het PDF-document is versleuteld. De aliaswaarde van de persoonlijke sleutel wordt opgegeven wanneer op een certificaat gebaseerde versleuteling uit een versleuteld PDF-document wordt verwijderd. Zie PDF-documenten [versleutelen met certificaten](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-certificates)voor informatie over de openbare sleutel.

>[!NOTE]
>
>Een persoonlijke sleutel wordt opgeslagen in het vertrouwde archief van AEM Forms. Wanneer een certificaat daar wordt geplaatst, wordt een aliaswaarde gespecificeerd.

**Het PDF-document opslaan**

Nadat op een certificaat gebaseerde versleuteling is verwijderd uit een versleuteld PDF-document, kunt u het PDF-document opslaan als een PDF-bestand. Gebruikers kunnen het PDF-document openen in Adobe Reader of Acrobat.

**Zie ook**

[Op certificaten gebaseerde codering verwijderen met de Java API](encrypting-decrypting-pdf-documents.md#remove-certificate-based-encryption-using-the-java-api)

[Op certificaten gebaseerde versleuteling verwijderen met de webservice-API](encrypting-decrypting-pdf-documents.md#remove-certificate-based-encryption-using-the-web-service-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[API voor coderingsservice - Snel aan de slag](/help/forms/developing/encryption-service-java-api-quick.md#encryption-service-java-api-quick-start-soap)

### Op certificaten gebaseerde codering verwijderen met de Java API {#remove-certificate-based-encryption-using-the-java-api}

Op een certificaat gebaseerde versleuteling verwijderen uit een PDF-document met de API voor versleuteling (Java):

1. Inclusief projectbestanden.

   Neem JAR-bestanden van de client, zoals adobe-encryption-client.jar, op in het klassenpad van uw Java-project.

1. Maak een versleutelingsserviceclient.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `EncryptionServiceClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Hiermee wordt het versleutelde PDF-document opgehaald.

   * Maak een `java.io.FileInputStream` object dat het versleutelde PDF-document vertegenwoordigt met behulp van de constructor en geef een tekenreekswaarde door die de locatie van het versleutelde PDF-document aangeeft.
   * Maak een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en het `java.io.FileInputStream` object door te geven.

1. Versleuteling verwijderen.

   Verwijder op een certificaat gebaseerde versleuteling uit het PDF-document door de methode van het `EncryptionServiceClient` `removePDFCertificateSecurity` object aan te roepen en de volgende waarden door te geven:

   * Het `com.adobe.idp.Document` object dat het versleutelde PDF-document bevat.
   * Een tekenreekswaarde die de aliasnaam van de persoonlijke sleutel opgeeft die overeenkomt met de sleutel die wordt gebruikt om het PDF-document te versleutelen.
   De `removePDFCertificateSecurity` methode retourneert een `com.adobe.idp.Document` object dat een onbeveiligd PDF-document bevat.

1. Sla het PDF-document op.

   * Maak een `java.io.File` object en zorg dat de bestandsextensie .pdf is.
   * Roep de `com.adobe.idp.Document` methode van het `copyToFile` object aan om de inhoud van het `Document` object naar het bestand te kopiëren. Zorg ervoor dat u het `com.adobe.idp.Document` object gebruikt dat door de `removePDFCredentialSecurity` methode is geretourneerd.

**Zie ook**

[Overzicht van de stappen](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[Snel starten (SOAP-modus): Op certificaten gebaseerde codering verwijderen met de Java API](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-removing-certificate-based-encryption-using-the-java-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Op certificaten gebaseerde versleuteling verwijderen met de webservice-API {#remove-certificate-based-encryption-using-the-web-service-api}

Verwijder op een certificaat gebaseerde codering met de API voor codering (webservice):

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een versleutelingsserviceclient.

   * Maak een `EncryptionServiceClient` object met de standaardconstructor.
   * Maak een `EncryptionServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/EncryptionService?WSDL`.) U hoeft het `lc_version` kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `EncryptionServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het veld `EncryptionServiceClient.ClientCredentials.UserName.UserName`.
      * Wijs de bijbehorende wachtwoordwaarde aan het veld toe `EncryptionServiceClient.ClientCredentials.UserName.Password`.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Hiermee wordt het versleutelde PDF-document opgehaald.

   * Maak een `BLOB` object met de constructor ervan. Het `BLOB` object wordt gebruikt om het versleutelde PDF-document op te slaan.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het gecodeerde PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de methode van het `System.IO.FileStream` `Read` object aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` object door de inhoud van de bytearray toe te wijzen aan het gegevenslid van het `BLOB` object `MTOM` .

1. Versleuteling verwijderen.

   Roep de methode van het `EncryptionServiceClient` `removePDFCertificateSecurity` object aan en geef de volgende waarden door:

   * Het `BLOB` object dat bestandsstreamgegevens bevat die een gecodeerd PDF-document vertegenwoordigen.
   * Een tekenreekswaarde die de aliasnaam van de openbare sleutel opgeeft die overeenkomt met de persoonlijke sleutel die wordt gebruikt om het PDF-document te versleutelen.
   De `removePDFCredentialSecurity` methode retourneert een `BLOB` object dat een onbeveiligd PDF-document bevat.

1. Sla het PDF-document op.

   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het onbeveiligde PDF-document vertegenwoordigt.
   * Maak een bytearray waarin de inhoud wordt opgeslagen van het `BLOB` object dat door de `removePDFPasswordSecurity` methode is geretourneerd. Vul de bytearray met de waarde van het `BLOB` `MTOM` gegevenslid van het object.
   * Maak een `System.IO.BinaryWriter` object door de constructor ervan aan te roepen en het `System.IO.FileStream` object door te geven.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door de methode van het `System.IO.BinaryWriter` `Write` object aan te roepen en de bytearray door te geven.

**Zie ook**

[Overzicht van de stappen](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[AEM-formulieren aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM-formulieren aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Wachtwoordversleuteling verwijderen {#removing-password-encryption}

Op wachtwoorden gebaseerde versleuteling kan uit een PDF-document worden verwijderd, zodat gebruikers het PDF-document in Adobe Reader of Acrobat kunnen openen zonder een wachtwoord op te geven. Nadat op een wachtwoord gebaseerde versleuteling is verwijderd uit een PDF-document, is het document niet meer beveiligd.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Encryptie, zie de Verwijzing van de [Diensten voor Vormen](https://www.adobe.com/go/learn_aemforms_services_63)AEM.

### Overzicht van de stappen {#summary_of_steps-3}

Voer de volgende stappen uit om op een wachtwoord gebaseerde codering uit een PDF-document te verwijderen:

1. Projectbestanden opnemen
1. Maak een versleutelingsserviceclient.
1. Hiermee wordt het versleutelde PDF-document opgehaald.
1. Verwijder het wachtwoord.
1. Sla het PDF-document op als een PDF-bestand.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM-formulieren worden geïmplementeerd op JBoss)

**Een coderingsserviceclient maken**

Om programmatically een de dienstverrichting van de Encryptie uit te voeren, moet u een de dienstcliënt van de Encryptie tot stand brengen. Als u de Java Encryption Service API gebruikt, maakt u een `EncrytionServiceClient` object. Maak een `EncryptionServiceService` object als u de API van de webservice Encryption Service gebruikt.

**Het versleutelde PDF-document ophalen**

U moet een versleuteld PDF-document verkrijgen om op een wachtwoord gebaseerde versleuteling te verwijderen. Als u probeert versleuteling te verwijderen uit een PDF-document dat niet is versleuteld, wordt een uitzondering gegenereerd.

**Het wachtwoord verwijderen**

Als u op wachtwoorden gebaseerde versleuteling uit een versleuteld PDF-document wilt verwijderen, hebt u zowel een versleuteld PDF-document als een hoofdwachtwoordwaarde nodig waarmee de versleuteling uit het PDF-document wordt verwijderd. Het wachtwoord waarmee een PDF-document met een wachtwoord wordt geopend, kan niet worden gebruikt om versleuteling te verwijderen. Er wordt een hoofdwachtwoord opgegeven wanneer het PDF-document met een wachtwoord is versleuteld. (Zie PDF-documenten [versleutelen met een wachtwoord](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password).)

**Het PDF-document opslaan**

Nadat de coderingsservice op wachtwoord gebaseerde codering uit een PDF-document heeft verwijderd, kunt u het PDF-document opslaan als een PDF-bestand. Gebruikers kunnen het PDF-document openen in Adobe Reader of Acrobat zonder een wachtwoord op te geven.

**Zie ook**

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[API voor coderingsservice - Snel aan de slag](/help/forms/developing/encryption-service-java-api-quick.md#encryption-service-java-api-quick-start-soap)

[PDF-documenten versleutelen met een wachtwoord](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password)

### Op wachtwoorden gebaseerde codering verwijderen met de Java API {#remove-password-based-encryption-using-the-java-api}

Verwijder op wachtwoord gebaseerde codering uit een PDF-document met de API voor codering (Java):

1. Inclusief projectbestanden.

   Neem JAR-bestanden van de client, zoals adobe-encryption-client.jar, op in het klassenpad van uw Java-project.

1. Maak een versleutelingsserviceclient.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `EncryptionServiceClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Hiermee wordt het versleutelde PDF-document opgehaald.

   * Maak een `java.io.FileInputStream` object dat het gecodeerde PDF-document vertegenwoordigt met de constructor ervan en geef een tekenreekswaarde door die de locatie van het PDF-document aangeeft.
   * Maak een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en het `java.io.FileInputStream` object door te geven.

1. Verwijder het wachtwoord.

   Verwijder op wachtwoord gebaseerde codering uit het PDF-document door de methode van het `EncryptionServiceClient` `removePDFPasswordSecurity` object aan te roepen en de volgende waarden door te geven:

   * Een `com.adobe.idp.Document` object dat het gecodeerde PDF-document bevat.
   * Een tekenreekswaarde die de waarde van het hoofdwachtwoord opgeeft waarmee de versleuteling uit het PDF-document wordt verwijderd.
   De `removePDFPasswordSecurity` methode retourneert een `com.adobe.idp.Document` object dat een onbeveiligd PDF-document bevat.

1. Sla het PDF-document op.

   * Maak een `java.io.File` object en zorg dat de bestandsnaamextensie .pdf is.
   * Roep de `com.adobe.idp.Document` methode van het `copyToFile` object aan om de inhoud van het `Document` object naar het bestand te kopiëren. Zorg ervoor dat u het `Document` object gebruikt dat door de `removePDFPasswordSecurity` methode is geretourneerd.

**Zie ook**

[Snel starten (SOAP-modus): Op wachtwoorden gebaseerde codering verwijderen met de Java API](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-removing-password-based-encryption-using-the-java-api)

### Op wachtwoorden gebaseerde codering verwijderen met de webservice-API {#remove-password-based-encryption-using-the-web-service-api}

Verwijder op wachtwoord gebaseerde codering met de API voor codering (webservice):

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een versleutelingsserviceclient.

   * Maak een `EncryptionServiceClient` object met de standaardconstructor.
   * Maak een `EncryptionServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/EncryptionService?WSDL`.) U hoeft het `lc_version` kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `EncryptionServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het veld `EncryptionServiceClient.ClientCredentials.UserName.UserName`.
      * Wijs de bijbehorende wachtwoordwaarde aan het veld toe `EncryptionServiceClient.ClientCredentials.UserName.Password`.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Hiermee wordt het versleutelde PDF-document opgehaald.

   * Maak een `BLOB` object met de constructor ervan. Het `BLOB` object wordt gebruikt om een PDF-document met wachtwoordcodering op te slaan.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het gecodeerde PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de methode van het `System.IO.FileStream` `Read` object aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` object door de inhoud van de bytearray toe te wijzen aan het gegevenslid van het `BLOB` object `MTOM` .

1. Verwijder het wachtwoord.

   Roep de methode van het `EncryptionServiceService` `removePDFPasswordSecurity` object aan en geef de volgende waarden door:

   * Het `BLOB` object dat bestandsstreamgegevens bevat die een gecodeerd PDF-document vertegenwoordigen.
   * Een tekenreekswaarde die de wachtwoordwaarde opgeeft die wordt gebruikt om versleuteling te verwijderen uit het PDF-document. Deze waarde wordt opgegeven wanneer het PDF-document met een wachtwoord wordt versleuteld.
   De `removePDFPasswordSecurity` methode retourneert een `BLOB` object dat een onbeveiligd PDF-document bevat.

1. Sla het PDF-document op.

   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het onbeveiligde PDF-document vertegenwoordigt.
   * Maak een bytearray waarin de inhoud wordt opgeslagen van het `BLOB` object dat door de `removePDFPasswordSecurity` methode is geretourneerd. Vul de bytearray met de waarde van het `BLOB` `MTOM` gegevenslid van het object.
   * Maak een `System.IO.BinaryWriter` object door de constructor ervan aan te roepen en het `System.IO.FileStream` object door te geven.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door de methode van het `System.IO.BinaryWriter` `Write` object aan te roepen en de bytearray door te geven.

**Zie ook**

[AEM-formulieren aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM-formulieren aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Versleutelde PDF-documenten ontgrendelen {#unlocking-encrypted-pdf-documents}

Een PDF-document met een wachtwoord of versleuteling met een certificaat moet worden ontgrendeld voordat een andere bewerking in AEM Forms kan worden uitgevoerd. Als u een bewerking probeert uit te voeren op een versleuteld PDF-document, wordt een uitzondering gegenereerd. Nadat u een versleuteld PDF-document hebt ontgrendeld, kunt u er een of meer bewerkingen op uitvoeren. Deze bewerkingen kunnen tot andere services behoren, zoals de Acrobat Reader DC extensions Service.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Encryptie, zie de Verwijzing van de [Diensten voor Vormen](https://www.adobe.com/go/learn_aemforms_services_63)AEM.

### Overzicht van de stappen {#summary_of_steps-4}

Voer de volgende stappen uit om een versleuteld PDF-document te ontgrendelen:

1. Inclusief projectbestanden.
1. Maak een versleutelingsserviceclient.
1. Hiermee wordt het versleutelde PDF-document opgehaald.
1. Ontgrendel het document.
1. Voer de bewerking AEM Forms uit.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)
* jbossall-client.jar (vereist als AEM-formulieren worden geïmplementeerd op JBoss Application Server)

**Een coderingsserviceclient maken**

Om programmatically een de dienstverrichting van de Encryptie uit te voeren, moet u een de dienstcliënt van de Encryptie tot stand brengen. Als u de Java Encryption Service API gebruikt, maakt u een `EncrytionServiceClient` object. Maak een `EncryptionServiceService` object als u de API van de webservice Encryption Service gebruikt.

**Het versleutelde PDF-document ophalen**

U moet een versleuteld PDF-document verkrijgen om het te ontgrendelen. Als u probeert een PDF-document te ontgrendelen dat niet is versleuteld, wordt een uitzondering gegenereerd.

**Het document ontgrendelen**

Als u een PDF-document met wachtwoordversleuteling wilt ontgrendelen, hebt u zowel een versleuteld PDF-document als een wachtwoordwaarde nodig om een PDF-document met wachtwoordversleuteling te openen. Deze waarde wordt opgegeven wanneer het PDF-document met een wachtwoord wordt versleuteld. (Zie PDF-documenten [versleutelen met een wachtwoord](encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password).)

Als u een met een certificaat gecodeerd PDF-document wilt ontgrendelen, hebt u zowel een versleuteld PDF-document als de alias van de openbare sleutel nodig die overeenkomt met de persoonlijke sleutel waarmee het PDF-document is versleuteld.

**Een bewerking in AEM Forms uitvoeren**

Nadat een versleuteld PDF-document is ontgrendeld, kunt u er een andere servicebewerking op uitvoeren, zoals gebruiksrechten op toepassen. Deze bewerking behoort tot de Acrobat Reader DC Extensions-service.

**Zie ook**

[Een versleuteld PDF-document ontgrendelen met de Java API](encrypting-decrypting-pdf-documents.md#unlock-an-encrypted-pdf-document-using-the-java-api)

[Een versleuteld PDF-document ontgrendelen met de webservice-API](encrypting-decrypting-pdf-documents.md#unlock-an-encrypted-pdf-document-using-the-web-service-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[API voor coderingsservice - Snel aan de slag](/help/forms/developing/encryption-service-java-api-quick.md#encryption-service-java-api-quick-start-soap)

### Een versleuteld PDF-document ontgrendelen met de Java API {#unlock-an-encrypted-pdf-document-using-the-java-api}

Een versleuteld PDF-document ontgrendelen met de API voor versleuteling (Java):

1. Inclusief projectbestanden.

   Neem JAR-bestanden van de client, zoals adobe-encryption-client.jar, op in het klassenpad van uw Java-project.

1. Maak een versleutelingsserviceclient.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `EncryptionServiceClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Hiermee wordt het versleutelde PDF-document opgehaald.

   * Maak een `java.io.FileInputStream` object dat het versleutelde PDF-document vertegenwoordigt met behulp van de constructor en geef een tekenreekswaarde door die de locatie van het versleutelde PDF-document aangeeft.
   * Maak een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en het `java.io.FileInputStream` object door te geven.

1. Ontgrendel het document.

   U kunt een versleuteld PDF-document ontgrendelen door de methode `EncryptionServiceClient` of de methode van het `unlockPDFUsingPassword` `unlockPDFUsingCredential` object aan te roepen.

   Als u een PDF-document wilt ontgrendelen dat met een wachtwoord is versleuteld, roept u de `unlockPDFUsingPassword` methode op en geeft u de volgende waarden door:

   * Een `com.adobe.idp.Document` object dat het PDF-document met een wachtwoord bevat.
   * Een tekenreekswaarde die de wachtwoordwaarde opgeeft waarmee een PDF-document met een wachtwoord wordt geopend. Deze waarde wordt opgegeven wanneer het PDF-document met een wachtwoord wordt versleuteld.
   Als u een PDF-document wilt ontgrendelen dat met een certificaat is versleuteld, roept u de `unlockPDFUsingCredential` methode op en geeft u de volgende waarden door:

   * Een `com.adobe.idp.Document` object dat het met een certificaat gecodeerde PDF-document bevat.
   * Een tekenreekswaarde die de aliasnaam opgeeft van de openbare sleutel die overeenkomt met de persoonlijke sleutel die wordt gebruikt om het PDF-document te versleutelen.
   De methoden `unlockPDFUsingPassword` en `unlockPDFUsingCredential` retourneren beide een `com.adobe.idp.Document` object dat u doorgeeft aan een andere Java-methode voor AEM-formulieren om een bewerking uit te voeren.

1. Voer de bewerking AEM Forms uit.

   Voer de bewerking AEM Forms uit op het ontgrendelde PDF-document om aan uw zakelijke vereisten te voldoen. Als u bijvoorbeeld gebruiksrechten wilt toepassen op een niet-vergrendeld PDF-document, geeft u het `com.adobe.idp.Document` object dat is geretourneerd door de methode `unlockPDFUsingPassword` of `unlockPDFUsingCredential` de methode door aan de `ReaderExtensionsServiceClient` methode van het `applyUsageRights` object.

**Zie ook**

[Overzicht van de stappen](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[Snel starten (SOAP-modus): Een versleuteld PDF-document ontgrendelen met de Java API](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-unlocking-an-encrypted-pdf-document-using-the-java-api) (SOAP-modus)

[Gebruiksrechten toepassen op PDF-documenten](/help/forms/developing/assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een versleuteld PDF-document ontgrendelen met de webservice-API {#unlock-an-encrypted-pdf-document-using-the-web-service-api}

Een versleuteld PDF-document ontgrendelen met de API voor versleuteling (webservice):

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een versleutelingsserviceclient.

   * Maak een `EncryptionServiceClient` object met de standaardconstructor.
   * Maak een `EncryptionServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/EncryptionService?WSDL`.) U hoeft het `lc_version` kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `EncryptionServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het veld `EncryptionServiceClient.ClientCredentials.UserName.UserName`.
      * Wijs de bijbehorende wachtwoordwaarde aan het veld toe `EncryptionServiceClient.ClientCredentials.UserName.Password`.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Hiermee wordt een versleuteld PDF-document opgehaald.

   * Maak een `BLOB` object met de constructor ervan.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het gecodeerde PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de methode van het `System.IO.FileStream` `Read` object aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` object door de inhoud van de bytearray toe te wijzen aan het gegevenslid van het `BLOB` object `MTOM` .

1. Ontgrendel het document.

   U kunt een versleuteld PDF-document ontgrendelen door de methode `EncryptionServiceClient` of de methode van het `unlockPDFUsingPassword` `unlockPDFUsingCredential` object aan te roepen.

   Als u een PDF-document wilt ontgrendelen dat met een wachtwoord is versleuteld, roept u de `unlockPDFUsingPassword` methode op en geeft u de volgende waarden door:

   * Een `BLOB` object dat het PDF-document met een wachtwoord bevat.
   * Een tekenreekswaarde die de wachtwoordwaarde opgeeft waarmee een PDF-document met een wachtwoord wordt geopend. Deze waarde wordt opgegeven wanneer het PDF-document met een wachtwoord wordt versleuteld.
   Als u een PDF-document wilt ontgrendelen dat met een certificaat is versleuteld, roept u de `unlockPDFUsingCredential` methode op en geeft u de volgende waarden door:

   * Een `BLOB` object dat het met een certificaat gecodeerde PDF-document bevat.
   * Een tekenreekswaarde die de aliasnaam van de openbare sleutel opgeeft die overeenkomt met de persoonlijke sleutel die wordt gebruikt om het PDF-document te versleutelen.
   De methoden `unlockPDFUsingPassword` en `unlockPDFUsingCredential` retourneren beide een `com.adobe.idp.Document` object dat u doorgeeft aan een andere methode van AEM Forms om een bewerking uit te voeren.

1. Voer de bewerking AEM Forms uit.

   Voer de bewerking AEM Forms uit op het ontgrendelde PDF-document om aan uw zakelijke vereisten te voldoen. Als u bijvoorbeeld gebruiksrechten wilt toepassen op het ontgrendelde PDF-document, geeft u het `BLOB` object dat is geretourneerd door de methode `unlockPDFUsingPassword` of `unlockPDFUsingCredential` de methode door aan de `ReaderExtensionsServiceClient` methode van het `applyUsageRights` object.

**Zie ook**

[Overzicht van de stappen](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[AEM-formulieren aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM-formulieren aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Type codering bepalen {#determining-encryption-type}

U kunt programmatisch bepalen welk type versleuteling een PDF-document beveiligt met de Java Encryption Service API of de webservice Encryption Service API. Soms is het nodig dynamisch te bepalen of een PDF-document is versleuteld en, zo ja, het versleutelingstype. U kunt bijvoorbeeld bepalen of een PDF-document is beveiligd met op een wachtwoord gebaseerde codering of met een beleid voor rechtenbeheer.

Een PDF-document kan worden beveiligd door de volgende coderingstypen:

* Codering op basis van wachtwoord
* Op een certificaat gebaseerde codering
* Een beleid dat door de dienst van het Beheer van Rechten wordt gecreeerd
* Een ander type codering

>[!NOTE]
>
>Voor meer informatie over de dienst van de Encryptie, zie de Verwijzing van de [Diensten voor Vormen](https://www.adobe.com/go/learn_aemforms_services_63)AEM.

### Overzicht van de stappen {#summary_of_steps-5}

Ga als volgt te werk om te bepalen welk type versleuteling een PDF-document beveiligt:

1. Inclusief projectbestanden.
1. Maak een versleutelingsserviceclient.
1. Hiermee wordt het versleutelde PDF-document opgehaald.
1. Bepaal het versleutelingstype.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-encryption-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)
* jbossall-client.jar (vereist als AEM-formulieren worden geïmplementeerd op JBoss Application Server)

**Een serviceclient maken**

Om programmatically een de dienstverrichting van de Encryptie uit te voeren, moet u een de dienstcliënt van de Encryptie tot stand brengen. Als u de Java Encryption Service API gebruikt, maakt u een `EncrytionServiceClient` object. Maak een `EncryptionServiceService` object als u de API van de webservice Encryption Service gebruikt.

**Het versleutelde PDF-document ophalen**

U moet een PDF-document aanschaffen om te bepalen welk type versleuteling het document beveiligt.

**Het versleutelingstype bepalen**

U kunt bepalen welk type versleuteling een PDF-document beveiligt. Als het PDF-document niet is beveiligd, geeft de coderingsservice aan dat het PDF-document niet is beveiligd.

**Zie ook**

[Het versleutelingstype bepalen met de Java API](encrypting-decrypting-pdf-documents.md#determine-the-encryption-type-using-the-java-api)

[Het versleutelingstype bepalen met de webservice-API](encrypting-decrypting-pdf-documents.md#determine-the-encryption-type-using-the-web-service-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[API voor coderingsservice - Snel aan de slag](/help/forms/developing/encryption-service-java-api-quick.md#encryption-service-java-api-quick-start-soap)

[Documenten beveiligen met beleid](/help/forms/developing/protecting-documents-policies.md#protecting-documents-with-policies)

### Het versleutelingstype bepalen met de Java API {#determine-the-encryption-type-using-the-java-api}

Bepaal het type versleuteling waarmee een PDF-document wordt beveiligd met de API voor versleuteling (Java):

1. Inclusief projectbestanden.

   Neem JAR-bestanden van de client, zoals adobe-encryption-client.jar, op in het klassenpad van uw Java-project.

1. Maak een serviceclient.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `EncryptionServiceClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Hiermee wordt het versleutelde PDF-document opgehaald.

   * Maak een `java.io.FileInputStream` object dat het PDF-document vertegenwoordigt met behulp van de constructor en geef een tekenreekswaarde door die de locatie van het PDF-document aangeeft.
   * Maak een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en het `java.io.FileInputStream` object door te geven.

1. Bepaal het versleutelingstype.

   * Bepaal het versleutelingstype door de methode van het `EncryptionServiceClient` object aan te roepen en het `getPDFEncryption` `com.adobe.idp.Document` object dat het PDF-document bevat door te geven. Deze methode retourneert een `EncryptionTypeResult` object.
   * Roep de `EncryptionTypeResult` methode van het `getEncryptionType` object aan. Deze methode retourneert een `EncryptionType` opsommingswaarde die het type codering opgeeft. Als het PDF-document bijvoorbeeld is beveiligd met codering op basis van een wachtwoord, wordt deze methode geretourneerd `EncryptionType.PASSWORD`.

**Zie ook**

[Overzicht van de stappen](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[Snel starten (SOAP-modus): Coderingstype bepalen met de Java API](/help/forms/developing/encryption-service-java-api-quick.md#quick-start-soap-mode-determining-encryption-type-using-the-java-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Het versleutelingstype bepalen met de webservice-API {#determine-the-encryption-type-using-the-web-service-api}

Bepaal het type versleuteling waarmee een PDF-document wordt beveiligd met de API voor versleuteling (webservice):

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/EncryptionService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een serviceclient.

   * Maak een `EncryptionServiceClient` object met de standaardconstructor.
   * Maak een `EncryptionServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/EncryptionService?WSDL`.) U hoeft het `lc_version` kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `EncryptionServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het veld `EncryptionServiceClient.ClientCredentials.UserName.UserName`.
      * Wijs de bijbehorende wachtwoordwaarde aan het veld toe `EncryptionServiceClient.ClientCredentials.UserName.Password`.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Hiermee wordt het versleutelde PDF-document opgehaald.

   * Maak een `BLOB` object met de constructor ervan.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het gecodeerde PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de methode van het `System.IO.FileStream` `Read` object aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` object door de inhoud van de bytearray toe te wijzen aan het gegevenslid van het `BLOB` object `MTOM` .

1. Bepaal het versleutelingstype.

   * Roep de `EncryptionServiceClient` methode van het `getPDFEncryption` object aan en geef het `BLOB` object met het PDF-document door. Deze methode retourneert een `EncryptionTypeResult` object.
   * Hiermee wordt de waarde van de `EncryptionTypeResult` gegevensmethode van het `encryptionType` object opgehaald. Als het PDF-document bijvoorbeeld is beveiligd met codering op basis van een wachtwoord, is de waarde van dit gegevenslid `EncryptionType.PASSWORD`.

**Zie ook**

[Overzicht van de stappen](encrypting-decrypting-pdf-documents.md#summary-of-steps)

[AEM-formulieren aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM-formulieren aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)