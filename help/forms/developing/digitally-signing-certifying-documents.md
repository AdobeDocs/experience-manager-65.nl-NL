---
title: Documenten digitaal ondertekenen en certificeren
description: Met de handtekeningservice kunt u digitale handtekeningvelden toevoegen aan en verwijderen uit een PDF-document, de namen van handtekeningvelden in een PDF-document ophalen, handtekeningvelden wijzigen, PDF-documenten digitaal ondertekenen, PDF-documenten certificeren, digitale handtekeningen in een PDF-document valideren, alle digitale handtekeningen in een PDF-document valideren en een digitale handtekening uit een handtekeningveld verwijderen.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: c200f345-40ab-46fd-b6ed-f3af0a23796b
source-git-commit: d195ac80ee59439bab5b1219a2c1f16e93e3d22b
workflow-type: tm+mt
source-wordcount: '16917'
ht-degree: 0%

---

# Documenten digitaal ondertekenen en certificeren {#digitally-signing-and-certifying-documents}

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

**Informatie over de Handtekeningenservice**

Met de service Handtekening kunt u de beveiliging en privacy beschermen van Adobe PDF-documenten die door uw organisatie worden gedistribueerd en ontvangen. Deze service gebruikt digitale handtekeningen en certificering om ervoor te zorgen dat alleen de beoogde ontvangers documenten kunnen wijzigen. Omdat beveiligingsfuncties op het document zelf worden toegepast, blijft het document gedurende de gehele levenscyclus beveiligd en beheerd. Een document blijft veilig buiten de firewall, wanneer het offline wordt gedownload en wanneer het terug naar uw organisatie wordt verzonden.

>[!NOTE]
>
>U kunt een aangepaste handtekening-handler maken voor de handtekeningservice die wordt aangeroepen wanneer bepaalde bewerkingen worden aangeroepen, zoals het ondertekenen van een PDF-document.

**Namen van handtekeningvelden**

Voor sommige bewerkingen van de handtekeningservice moet u de naam opgeven van het handtekeningveld waarop een bewerking wordt uitgevoerd. Als u bijvoorbeeld een PDF-document ondertekent, geeft u de naam op van het handtekeningveld dat u wilt ondertekenen. aannemen dat de volledige naam van een handtekeningveld is `form1[0].Form1[0].SignatureField1[0]`. U kunt `SignatureField1[0]` in plaats van `form1[0].Form1[0].SignatureField1[0]`.

Soms ondertekent de handtekeningservice door een conflict (of voert een andere bewerking uit waarvoor de naam van het handtekeningveld vereist is) het verkeerde veld. Dit conflict is het resultaat van de naam `SignatureField1[0]` op twee of meer plaatsen in hetzelfde PDF-document worden weergegeven. Neem bijvoorbeeld een PDF-document dat twee handtekeningvelden bevat met de naam `form1[0].Form1[0].SignatureField1[0]` en `form1[0].Form1[0].SubForm1[0].SignatureField1[0]` en geeft u `SignatureField1[0]`. In dit geval ondertekent de ondertekeningsservice het eerste handtekeningveld dat wordt gevonden terwijl alle handtekeningvelden in het document worden doorlopen.

Als er meerdere handtekeningvelden in een PDF-document staan, is het raadzaam de volledige namen van de handtekeningvelden op te geven. Dat wil zeggen, specificeer `form1[0].Form1[0].SignatureField1[0]`in plaats van `SignatureField1[0]`.

U kunt deze taken uitvoeren met de service Handtekening:

* Digitale handtekeningvelden toevoegen aan en verwijderen uit een PDF-document. (Zie [Handtekeningvelden toevoegen](digitally-signing-certifying-documents.md#adding-signature-fields).)
* Haal de namen van handtekeningvelden op in een PDF-document. (Zie [Namen van handtekeningvelden ophalen](digitally-signing-certifying-documents.md#retrieving-signature-field-names).)
* Handtekeningvelden wijzigen. (Zie [Handtekeningvelden wijzigen](digitally-signing-certifying-documents.md#modifying-signature-fields).)
* PDF-documenten digitaal ondertekenen. (Zie [PDF-documenten digitaal ondertekenen](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents).)
* PDF-documenten certificeren. (Zie [PDF-documenten certificeren](digitally-signing-certifying-documents.md#certifying-pdf-documents).)
* Digitale handtekeningen valideren in een PDF-document. (Zie [Digitale handtekeningen verifiëren](digitally-signing-certifying-documents.md#verifying-digital-signatures).)
* Alle digitale handtekeningen in een PDF-document valideren. (Zie [Meerdere digitale handtekeningen controleren](digitally-signing-certifying-documents.md#verifying-digital-signatures).)
* Een digitale handtekening verwijderen uit een handtekeningveld. (Zie [Digitale handtekeningen verwijderen](digitally-signing-certifying-documents.md#removing-digital-signatures).)

>[!NOTE]
>
>Voor meer informatie over de service Handtekening raadpleegt u [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63)..

## Handtekeningvelden toevoegen {#adding-signature-fields}

Digitale handtekeningen worden weergegeven in handtekeningvelden. Dit zijn formuliervelden die een grafische weergave van de handtekening bevatten. Handtekeningvelden kunnen zichtbaar of onzichtbaar zijn. Ondertekenaars kunnen een bestaand handtekeningveld gebruiken of een handtekeningveld programmatisch toevoegen. In beide gevallen moet het handtekeningveld bestaan voordat een PDF-document kan worden ondertekend.

U kunt een handtekeningveld programmatisch toevoegen met de Java API of de API van de Signature-service van de Java-API. U kunt meerdere handtekeningvelden toevoegen aan een PDF-document. Elke handtekeningveldnaam moet echter uniek zijn.

>[!NOTE]
>
>Bij sommige documenttypen voor PDF kunt u geen handtekeningveld programmatisch toevoegen. Zie voor meer informatie over de service Handtekening en het toevoegen van handtekeningvelden [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary-of-steps}

Als u een handtekeningveld wilt toevoegen aan een PDF-document, voert u de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak een handtekeningclient.
1. Hiermee wordt een PDF-document opgehaald waaraan een handtekeningveld wordt toegevoegd.
1. Voeg een handtekeningveld toe.
1. Sla het PDF-document op als een PDF-bestand.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

**Een handtekeningclient maken**

Voordat u programmatically een verrichting van de dienst van de Handtekening kunt uitvoeren, moet u een cliënt van de dienst van de Handtekening tot stand brengen.

**Een PDF-document ophalen waaraan een handtekeningveld wordt toegevoegd**

Vraag een PDF-document op waaraan een handtekeningveld is toegevoegd.

**Een handtekeningveld toevoegen**

Als u een handtekeningveld aan een PDF-document wilt toevoegen, geeft u coördinaatwaarden op die de locatie van het handtekeningveld aangeven. (Als u een onzichtbaar handtekeningveld toevoegt, zijn deze waarden niet vereist.) U kunt ook opgeven welke velden in het PDF-document worden vergrendeld nadat een handtekening is toegepast op het handtekeningveld.

**Het PDF-document opslaan als een PDF-bestand**

Nadat de handtekeningservice een handtekeningveld aan het PDF-document heeft toegevoegd, kunt u het document opslaan als een PDF-bestand zodat gebruikers het kunnen openen in Acrobat of Adobe Reader.

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[PDF-documenten digitaal ondertekenen](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)

### Handtekeningvelden toevoegen met de Java API {#add-signature-fields-using-the-java-api}

Voeg een handtekeningveld toe met de handtekening-API (Java):

1. Projectbestanden opnemen

   Neem JAR-bestanden van de client, zoals adobe-signatures-client.jar, op in het klassepad van uw Java-project.

1. Een handtekeningclient maken

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `SignatureServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Een PDF-document ophalen waaraan een handtekeningveld wordt toegevoegd

   * Een `java.io.FileInputStream` object dat het PDF-document vertegenwoordigt waaraan een handtekeningveld wordt toegevoegd door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het PDF-document aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. Een handtekeningveld toevoegen

   * Een `PositionRectangle` object dat de locatie van het handtekeningveld aangeeft met de constructor ervan. Geef binnen de constructor coördinaatwaarden op.
   * Maak indien gewenst een `FieldMDPOptions` object dat aangeeft welke velden zijn vergrendeld wanneer een digitale handtekening wordt toegepast op het handtekeningveld.
   * Voeg een handtekeningveld toe aan een PDF-document door het `SignatureServiceClient` object `addSignatureField` en geeft de volgende waarden door:

      * A `com.adobe.idp`. `Document` object dat staat voor het PDF-document waaraan een handtekeningveld wordt toegevoegd.
      * Een tekenreekswaarde die de naam van het handtekeningveld opgeeft.
      * A `java.lang.Integer` waarde die staat voor het paginanummer waaraan een handtekeningveld wordt toegevoegd.
      * A `PositionRectangle` object dat de locatie van het handtekeningveld aangeeft.
      * A `FieldMDPOptions` object dat velden in het PDF-document opgeeft die zijn vergrendeld nadat een digitale handtekening is toegepast op het handtekeningveld. Deze parameterwaarde is optioneel en u kunt deze doorgeven `null`.

   * A `PDFSeedValueOptions` -object dat verschillende runtimewaarden opgeeft. Deze parameterwaarde is optioneel en u kunt deze doorgeven `null`.

     De `addSignatureField` methode retourneert een `com.adobe.idp`. `Document` object dat staat voor een PDF-document dat een handtekeningveld bevat.

   >[!NOTE]
   >
   >U kunt de `SignatureServiceClient` object `addInvisibleSignatureField` methode om een onzichtbaar handtekeningveld toe te voegen.

1. Het PDF-document opslaan als een PDF-bestand

   * Een `java.io.File` en zorg dat de bestandsextensie .pdf is.
   * De `com.adobe.idp`. `Document` object `copyToFile` methode om de inhoud van de `Document` naar het bestand. Zorg ervoor dat u de `com.adobe.idp`. `Document` object dat is geretourneerd door de `addSignatureField` methode.

**Zie ook**

[Handtekeningenservice-API - Snel starten](/help/forms/developing/signature-service-java-api-quick.md#signature-service-java-api-quick-start-soap)

### Handtekeningvelden toevoegen met de webservice-API {#add-signature-fields-using-the-web-service-api}

Een handtekeningveld toevoegen met de handtekening-API (webservice):

1. Projectbestanden opnemen

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Een handtekeningclient maken

   * Een `SignatureServiceClient` object met de standaardconstructor.
   * Een `SignatureServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/SignatureService?WSDL`). U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `SignatureServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `SignatureServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `SignatureServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Een PDF-document ophalen waaraan een handtekeningveld wordt toegevoegd

   * Een `BLOB` object met behulp van de constructor. De `BLOB` wordt gebruikt om het PDF-document op te slaan dat een handtekeningveld zal bevatten.
   * Een `System.IO.FileStream` door de constructor aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` eigenschap met de inhoud van de bytearray.

1. Een handtekeningveld toevoegen

   Voeg een handtekeningveld toe aan het PDF-document door het `SignatureServiceClient` object `addSignatureField` en geeft de volgende waarden door:

   * A `BLOB` object dat staat voor het PDF-document waaraan een handtekeningveld wordt toegevoegd.
   * Een tekenreekswaarde die de naam van het handtekeningveld aangeeft.
   * Een geheel getal dat staat voor het paginanummer waaraan een handtekeningveld wordt toegevoegd.
   * A `PositionRect` object dat de locatie van het handtekeningveld aangeeft.
   * A `FieldMDPOptions` object dat velden in het PDF-document opgeeft die zijn vergrendeld nadat een digitale handtekening is toegepast op het handtekeningveld. Deze parameterwaarde is optioneel en u kunt deze doorgeven `null`.
   * A `PDFSeedValueOptions` -object dat verschillende runtimewaarden opgeeft. Deze parameterwaarde is optioneel en u kunt deze doorgeven `null`.

   De `addSignatureField` methode retourneert een `BLOB` object dat staat voor een PDF-document dat een handtekeningveld bevat.

1. Het PDF-document opslaan als een PDF-bestand

   * Een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het PDF-document dat het handtekeningveld en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van de `BLOB` object dat is geretourneerd door de `addSignatureField` methode. Vul de bytearray met de waarde van de `BLOB` object `binaryData` lid.
   * Een `System.IO.BinaryWriter` object door de constructor aan te roepen en de `System.IO.FileStream` object.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door het `System.IO.BinaryWriter` object `Write` en geeft u de bytearray door.

**Zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Namen van handtekeningvelden ophalen {#retrieving-signature-field-names}

U kunt de namen ophalen van alle handtekeningvelden in een PDF-document dat u wilt ondertekenen of certificeren. Als u niet zeker weet welke namen van handtekeningvelden zich in een PDF-document bevinden of als u de namen wilt verifiëren, kunt u deze via programmacode ophalen. De service Handtekening retourneert de volledig gekwalificeerde naam van het handtekeningveld, zoals `form1[0].grantApplication[0].page1[0].SignatureField1[0]`.

>[!NOTE]
>
>Voor meer informatie over de service Handtekening raadpleegt u [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63)

### Overzicht van de stappen {#summary_of_steps-1}

Voer de volgende taken uit om de namen van handtekeningvelden op te halen:

1. Inclusief projectbestanden.
1. Maak een handtekeningclient.
1. Hiermee wordt het PDF-document opgehaald dat handtekeningvelden bevat.
1. Haal de namen van de handtekeningvelden op.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

Voor informatie over de locatie van deze JAR-bestanden raadpleegt u [Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Een handtekeningclient maken**

Voordat u programmatically een verrichting van de dienst van de Handtekening kunt uitvoeren, moet u een cliënt van de dienst van de Handtekening tot stand brengen.

**Hiermee wordt het PDF-document opgehaald dat handtekeningvelden bevat**

Haal een PDF-document op dat handtekeningvelden bevat.

**De namen van handtekeningvelden ophalen**

U kunt namen van handtekeningvelden ophalen nadat u een PDF-document hebt opgehaald dat een of meer handtekeningvelden bevat.

**Zie ook**

[Namen van handtekeningvelden ophalen met de Java API](digitally-signing-certifying-documents.md#retrieve-signature-field-names-using-the-java-api)

[Handtekeningveld ophalen met de webservice-API](digitally-signing-certifying-documents.md#retrieve-signature-field-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Handtekeningvelden toevoegen](digitally-signing-certifying-documents.md#adding-signature-fields)

### Namen van handtekeningvelden ophalen met de Java API {#retrieve-signature-field-names-using-the-java-api}

Namen van handtekeningvelden ophalen met de handtekening-API (Java):

1. Projectbestanden opnemen

   Neem JAR-bestanden van de client, zoals adobe-signatures-client.jar, op in het klassepad van uw Java-project.

1. Een handtekeningclient maken

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `SignatureServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Hiermee wordt het PDF-document opgehaald dat handtekeningvelden bevat

   * Een `java.io.FileInputStream` -object dat staat voor het PDF-document dat handtekeningvelden bevat, door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het PDF-document aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. De namen van handtekeningvelden ophalen

   * Haal de namen van de handtekeningvelden op door het `SignatureServiceClient` object `getSignatureFieldList` en het doorgeven van de `com.adobe.idp.Document` object dat het PDF-document bevat dat handtekeningvelden bevat. Deze methode retourneert een `java.util.List` object, waarin elk element een `PDFSignatureField` object. Met dit object kunt u aanvullende informatie verkrijgen over een handtekeningveld, bijvoorbeeld of dit zichtbaar is.
   * Doorlopen `java.util.List` -object om te bepalen of er namen van handtekeningvelden zijn. Voor elk handtekeningveld in het PDF-document kunt u een apart veld aanvragen `PDFSignatureField` object. Als u de naam van het handtekeningveld wilt opvragen, roept u het `PDFSignatureField` object `getName` methode. Deze methode retourneert een tekenreekswaarde die de naam van het handtekeningveld opgeeft.

**Zie ook**

[Namen van handtekeningvelden ophalen](digitally-signing-certifying-documents.md#retrieving-signature-field-names)

[Snel starten (SOAP-modus): namen van handtekeningvelden ophalen met de Java API](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-retrieving-signature-field-names-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Handtekeningveld ophalen met de webservice-API {#retrieve-signature-field-using-the-web-service-api}

Namen van handtekeningvelden ophalen met de handtekening-API (webservice):

1. Projectbestanden opnemen

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Een handtekeningclient maken

   * Een `SignatureServiceClient` object met de standaardconstructor.
   * Een `SignatureServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/SignatureService?WSDL`). U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `SignatureServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `SignatureServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `SignatureServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Hiermee wordt het PDF-document opgehaald dat handtekeningvelden bevat

   * Een `BLOB` object met behulp van de constructor. De `BLOB` wordt gebruikt om het PDF-document op te slaan dat handtekeningvelden bevat.
   * Een `System.IO.FileStream` door de constructor aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` veld de inhoud van de bytearray.

1. De namen van handtekeningvelden ophalen

   * Haal de namen van handtekeningvelden op door deze aan te roepen `SignatureServiceClient` object `getSignatureFieldList` en het doorgeven van de `BLOB` object dat het PDF-document bevat dat handtekeningvelden bevat. Deze methode retourneert een `MyArrayOfPDFSignatureField` verzamelingsobject waarin elk element een `PDFSignatureField` object.
   * Doorlopen `MyArrayOfPDFSignatureField` object om te bepalen of er namen van handtekeningvelden zijn. Voor elk handtekeningveld in het PDF-document kunt u een `PDFSignatureField` object. Als u de naam van het handtekeningveld wilt opvragen, roept u het `PDFSignatureField` object `getName` methode. Deze methode retourneert een tekenreekswaarde die de naam van het handtekeningveld opgeeft.

**Zie ook**

[Namen van handtekeningvelden ophalen](digitally-signing-certifying-documents.md#retrieving-signature-field-names)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Handtekeningvelden wijzigen {#modifying-signature-fields}

U kunt handtekeningvelden in een PDF-document wijzigen met de Java API en de webservice-API. Als u een handtekeningveld wijzigt, moet u de vergrendelingswoordenboekwaarden van het handtekeningveld of de waarden van het zaadwaardewoordenboek bewerken.

A *veldvergrendelingswoordenboek* Hiermee geeft u een lijst op met velden die zijn vergrendeld wanneer het handtekeningveld wordt ondertekend. Een vergrendeld veld voorkomt dat gebruikers wijzigingen in het veld aanbrengen. A *zaadwaardewoordenboek* bevat beperkende informatie die wordt gebruikt op het moment dat de handtekening wordt toegepast. U kunt bijvoorbeeld machtigingen wijzigen die de acties bepalen die kunnen plaatsvinden zonder een handtekening ongeldig te maken.

Door een bestaand handtekeningveld te wijzigen, kunt u het PDF-document aanpassen aan veranderende zakelijke vereisten. Voor een nieuwe bedrijfsvereiste moeten bijvoorbeeld mogelijk alle documentvelden worden vergrendeld nadat het document is ondertekend.

In deze sectie wordt uitgelegd hoe u een handtekeningveld kunt wijzigen door de woordenboekwaarden voor veldvergrendeling en zaadwaarden te wijzigen. Als u wijzigingen aanbrengt in het vergrendelingswoordenboek van het handtekeningveld, worden alle velden in het PDF-document vergrendeld wanneer een handtekeningveld wordt ondertekend. Wijzigingen in het woordenboek voor zaadwaarden staan bepaalde typen wijzigingen in het document niet toe.

>[!NOTE]
>
>Zie voor meer informatie over de service Handtekening en het wijzigen van handtekeningvelden [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-2}

Voer de volgende taken uit om handtekeningvelden in een PDF-document te wijzigen:

1. Inclusief projectbestanden.
1. Maak een handtekeningclient.
1. Hiermee wordt het PDF-document opgehaald dat het handtekeningveld bevat dat u wilt wijzigen.
1. Stel woordenboekwaarden in.
1. Wijzig het handtekeningveld.
1. Sla het PDF-document op als een PDF-bestand.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

Voor informatie over de locatie van deze JAR-bestanden raadpleegt u [Inclusief Java-bibliotheekbestanden voor LiveCycles](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Een handtekeningclient maken**

Voordat u programmatically een verrichting van de dienst van de Handtekening kunt uitvoeren, moet u een cliënt van de dienst van de Handtekening tot stand brengen.

**Hiermee wordt het PDF-document opgehaald dat het handtekeningveld bevat dat moet worden gewijzigd**

Hiermee wordt een PDF-document opgehaald dat het handtekeningveld bevat dat u wilt wijzigen.

**Woordenboekwaarden instellen**

Als u een handtekeningveld wilt wijzigen, wijst u waarden toe aan het bijbehorende veldvergrendelingswoordenboek of het bijbehorende zaadwaardewoordenboek. Als u woordenboekwaarden voor handtekeningvelden opgeeft, moet u PDF-documentvelden opgeven die zijn vergrendeld wanneer het handtekeningveld wordt ondertekend. (In deze sectie wordt besproken hoe u alle velden kunt vergrendelen.)

U kunt de volgende zaadwaardewoordenboekwaarden instellen:

* **Revisiecontrole**: Geeft aan of intrekkingscontrole wordt uitgevoerd wanneer een handtekening wordt toegepast op het handtekeningveld.
* **Certificaatopties**: Wijst waarden toe aan het certificaatzaadwaardewoordenboek. Voordat u certificaatopties opgeeft, is het raadzaam bekend te raken met een certificaatzaadwaardewoordenboek. (Zie [PDF-referentie](https://www.adobe.com/devnet/acrobat/pdfs/pdf_reference_1-7.pdf).)
* **Opties voor overzicht**: Hiermee wijst u samenvattingsalgoritmen toe die worden gebruikt voor ondertekening. Geldige waarden zijn SHA1, SHA256, SHA384, SHA512 en RIPEMD160.
* **Filter**: Geeft het filter op dat wordt gebruikt met het handtekeningveld. U kunt bijvoorbeeld het filter Adobe.PPKLite gebruiken. (Zie [PDF-referentie](https://www.adobe.com/devnet/acrobat/pdfs/pdf_reference_1-7.pdf).)
* **Vlagopties**: Geeft de markeringswaarden aan die aan dit handtekeningveld zijn gekoppeld. De waarde 1 houdt in dat een ondertekenaar alleen de opgegeven waarden voor het item moet gebruiken. De waarde 0 houdt in dat andere waarden zijn toegestaan. Hier zijn de posities van het Beetje:

   * **1(Filter):** De handtekening-handler die moet worden gebruikt om het handtekeningveld te ondertekenen
   * **2 (SubFilter):** Een array met namen die aangeven welke coderingen acceptabel zijn voor ondertekening
   * **3 (V)**: Het minimaal vereiste versienummer van de handtekening-handler dat moet worden gebruikt om het handtekeningveld te ondertekenen
   * **4 (Redenen):** Een array met tekenreeksen die mogelijke redenen voor het ondertekenen van een document opgeven
   * **5 (PDFLegalWarnings):** Een array van tekenreeksen die mogelijke juridische attestaties opgeven

* **Juridische verklaringen**: Wanneer een document wordt gecertificeerd, wordt het automatisch gescand op specifieke typen inhoud die de zichtbare inhoud van een document dubbelzinnig of misleidend kunnen maken. Een annotatie kan bijvoorbeeld tekst die belangrijk is voor het begrijpen van wat wordt gecertificeerd, onduidelijk maken. Tijdens het scanproces worden waarschuwingen gegenereerd die de aanwezigheid van dit type inhoud aangeven. Het verstrekt ook een extra verklaring van de inhoud die waarschuwingen kan hebben veroorzaakt.
* **Machtigingen**: Geeft machtigingen op die kunnen worden gebruikt voor een PDF-document zonder de handtekening ongeldig te maken.
* **Redenen**: Geeft aan waarom dit document moet worden ondertekend.
* **Tijdstempel**: Geeft opties voor tijdstempeling op. U kunt bijvoorbeeld de URL instellen van de gebruikte tijdstempelserver.
* **Versie**: Geeft het minimale versienummer op van de handtekening-handler die moet worden gebruikt om het handtekeningveld te ondertekenen.

**Het handtekeningveld wijzigen**

Nadat u een client voor de handtekeningenservice hebt gemaakt, kunt u het PDF-document ophalen dat het handtekeningveld bevat dat u wilt wijzigen en woordenboekwaarden instellen. Vervolgens kunt u de handtekeningservice de opdracht geven het handtekeningveld te wijzigen. De handtekeningservice retourneert vervolgens een PDF-document dat het gewijzigde handtekeningveld bevat. Dit heeft geen invloed op het oorspronkelijke PDF-document.

**Het PDF-document opslaan als een PDF-bestand**

Sla het PDF-document met het gewijzigde handtekeningveld op als een PDF-bestand zodat gebruikers het kunnen openen in Acrobat of Adobe Reader.

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Handtekeningenservice-API - Snel starten](/help/forms/developing/signature-service-java-api-quick.md#signature-service-java-api-quick-start-soap)

[PDF-documenten digitaal ondertekenen](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)

### Handtekeningvelden wijzigen met de Java API {#modify-signature-fields-using-the-java-api}

Wijzig een handtekeningveld met de handtekening-API (Java):

1. Projectbestanden opnemen

   Neem JAR-bestanden van de client, zoals adobe-signatures-client.jar, op in het klassepad van uw Java-project.

1. Een handtekeningclient maken

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `SignatureServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Hiermee wordt het PDF-document opgehaald dat het handtekeningveld bevat dat moet worden gewijzigd

   * Een `java.io.FileInputStream` object dat staat voor het PDF-document dat het handtekeningveld bevat dat moet worden gewijzigd met de constructor ervan en dat een tekenreekswaarde doorgeeft die de locatie van het PDF-document aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. Woordenboekwaarden instellen

   * Een `PDFSignatureFieldProperties` object met behulp van de constructor. A `PDFSignatureFieldProperties` In dit object worden het handtekeningveld vergrendelingswoordenboek en de zaadwaardewoordenboekgegevens opgeslagen.
   * Een `PDFSeedValueOptionSpec` object met behulp van de constructor. Met dit object kunt u woordenboekwaarden voor zaadwaarden instellen.
   * Wijzigingen in het PDF-document niet toestaan door het aanroepen van de `PDFSeedValueOptionSpec` object `setMdpValue` en het doorgeven van de `MDPPermissions.NoChanges` opsommingswaarde.
   * Een `FieldMDPOptionSpec` object met behulp van de constructor. Met dit object kunt u woordenboekwaarden voor handtekeningveldvergrendeling instellen.
   * Vergrendel alle velden in het PDF-document door het `FieldMDPOptionSpec` object `setMdpValue` en het doorgeven van de `FieldMDPAction.ALL` opsommingswaarde.
   * Stel de woordenboekgegevens voor zaadwaarden in door de `PDFSignatureFieldProperties` object `setSeedValue` en het doorgeven van de `PDFSeedValueOptionSpec` object.
   * Vergrendelingswoordenboekgegevens voor handtekeningvelden instellen door het `PDFSignatureFieldProperties`object `setFieldMDP` en het doorgeven van de `FieldMDPOptionSpec` object.

   >[!NOTE]
   >
   >Als u alle waarden wilt zien die u kunt instellen in het zaadwaardewoordenboek, raadpleegt u de `PDFSeedValueOptionSpec` klasseverwijzing. (Zie [AEM Forms API-naslag](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).)

1. Het handtekeningveld wijzigen

   Wijzig het handtekeningveld door het `SignatureServiceClient` object `modifySignatureField` en geeft de volgende waarden door:

   * De `com.adobe.idp.Document` object waarin het PDF-document is opgeslagen dat het handtekeningveld bevat dat moet worden gewijzigd
   * Een tekenreekswaarde die de naam van het handtekeningveld opgeeft
   * De `PDFSignatureFieldProperties` object dat woordenboekwoordenlijst voor handtekeningvelden en zaadwaardewoordenboekgegevens opslaat

   De `modifySignatureField` methode retourneert een `com.adobe.idp.Document` object dat een PDF-document opslaat dat het gewijzigde handtekeningveld bevat.

1. Het PDF-document opslaan als een PDF-bestand

   * Een `java.io.File` en zorg ervoor dat de bestandsnaamextensie .pdf is.
   * De `com.adobe.idp.Document` object `copyToFile` methode om de inhoud van de `com.adobe.idp.Document` naar het bestand. Zorg ervoor dat u de `com.adobe.idp.Document` het object dat `modifySignatureField` geretourneerde methode.

### Handtekeningvelden wijzigen met de webservice-API {#modify-signature-fields-using-the-web-service-api}

Wijzig een handtekeningveld met de handtekening-API (webservice):

1. Projectbestanden opnemen

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Een handtekeningclient maken

   * Een `SignatureServiceClient` object met de standaardconstructor.
   * Een `SignatureServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/SignatureService?WSDL`). U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `SignatureServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `SignatureServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `SignatureServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Hiermee wordt het PDF-document opgehaald dat het handtekeningveld bevat dat moet worden gewijzigd

   * Een `BLOB` object met behulp van de constructor. De `BLOB` wordt gebruikt om het PDF-document op te slaan dat het handtekeningveld bevat dat moet worden gewijzigd.
   * Een `System.IO.FileStream` door de constructor aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` geeft de inhoud van de bytearray op.

1. Woordenboekwaarden instellen

   * Een `PDFSignatureFieldProperties` object met behulp van de constructor. In dit object worden het handtekeningveldvergrendelingswoordenboek en de zaadwaardewoordenboekgegevens opgeslagen.
   * Een `PDFSeedValueOptionSpec` object met behulp van de constructor. Met dit object kunt u woordenboekwaarden voor zaadwaarden instellen.
   * Wijzigingen in het PDF-document negeren door de opdracht `MDPPermissions.NoChanges` opsommingswaarde voor de `PDFSeedValueOptionSpec` object `mdpValue` lid.
   * Een `FieldMDPOptionSpec` object met behulp van de constructor. Met dit object kunt u woordenboekwaarden voor handtekeningveldvergrendeling instellen.
   * Vergrendel alle velden in het PDF-document door de opdracht `FieldMDPAction.ALL` opsommingswaarde voor de `FieldMDPOptionSpec` object `mdpValue` lid.
   * U kunt woordenboekgegevens voor zaadwaarden instellen door de opdracht `PDFSeedValueOptionSpec` aan `PDFSignatureFieldProperties` object `seedValue` lid.
   * Vergrendelingswoordenboekgegevens voor handtekeningvelden instellen door de opdracht `FieldMDPOptionSpec` aan `PDFSignatureFieldProperties` object `fieldMDP` lid.

   >[!NOTE]
   >
   >Als u alle waarden wilt zien die u kunt instellen in het zaadwaardewoordenboek, raadpleegt u de `PDFSeedValueOptionSpec` klasseverwijzing. (Zie [AEM Forms API-naslag](https://www.adobe.com/go/learn_aemforms_javadocs_63_en)).

1. Het handtekeningveld wijzigen

   Wijzig het handtekeningveld door het `SignatureServiceClient` object `modifySignatureField` en geeft de volgende waarden door:

   * De `BLOB` object waarin het PDF-document is opgeslagen dat het handtekeningveld bevat dat moet worden gewijzigd
   * Een tekenreekswaarde die de naam van het handtekeningveld opgeeft
   * De `PDFSignatureFieldProperties` object dat woordenboekwoordenlijst voor handtekeningvelden en zaadwaardewoordenboekgegevens opslaat

   De `modifySignatureField` methode retourneert een `BLOB` object dat een PDF-document opslaat dat het gewijzigde handtekeningveld bevat.

1. Het PDF-document opslaan als een PDF-bestand

   * Een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het PDF-document dat het handtekeningveld zal bevatten, en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van de `BLOB` het object dat `addSignatureField` methode retourneert. Vul de bytearray met de waarde van de `BLOB` object `MTOM` lid.
   * Een `System.IO.BinaryWriter` object door de constructor aan te roepen en de `System.IO.FileStream` object.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door het `System.IO.BinaryWriter` object `Write` en geeft u de bytearray door.

**Zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## PDF-documenten digitaal ondertekenen {#digitally-signing-pdf-documents}

Digitale handtekeningen kunnen op PDF-documenten worden toegepast om een beveiligingsniveau te bieden. Digitale handtekeningen bieden, net als handgeschreven handtekeningen, een manier waarop ondertekenaars zichzelf identificeren en instructies over een document maken. De technologie die wordt gebruikt om documenten digitaal te ondertekenen, helpt ervoor te zorgen dat zowel de ondertekenaar als de ontvangers duidelijk zijn over wat is ondertekend en er zeker van zijn dat het document niet is gewijzigd sinds het werd ondertekend.

De documenten van PDF worden ondertekend door middel van openbare-sleuteltechnologie. Een ondertekenaar heeft twee sleutels: een openbare sleutel en een persoonlijke sleutel. De persoonlijke sleutel wordt opgeslagen in de referentie van een gebruiker die beschikbaar moet zijn op het moment van ondertekening. De openbare sleutel wordt opgeslagen in het certificaat van de gebruiker dat beschikbaar moet zijn aan ontvangers om de handtekening te valideren. Informatie over ingetrokken certificaten vindt u in de certificaatintrekkingslijsten (CRL&#39;s) en de online certificaatstatusprotocollen (OCSP&#39;s) die door de certificeringsinstanties (CA&#39;s) worden verspreid. De tijd van het ondertekenen kan van een vertrouwde op bron worden verkregen die als Tijdstempelinstantie wordt bekend.

>[!NOTE]
>
>Voordat u een PDF-document digitaal kunt ondertekenen, moet u ervoor zorgen dat u het certificaat aan AEM Forms toevoegt. Een certificaat wordt toegevoegd gebruikend beleidsconsole of programmatically gebruikend de Manager API van het Vertrouwen. (Zie [Referenties importeren met de Betrouwbaarheidsbeheer-API](/help/forms/developing/credentials.md#importing-credentials-by-using-the-trust-manager-api).)

U kunt PDF-documenten programmatisch digitaal ondertekenen. Bij het digitaal ondertekenen van een PDF-document moet u verwijzen naar een beveiligingsreferentie die in AEM Forms bestaat. De referentie is de persoonlijke sleutel die wordt gebruikt voor ondertekening.

De handtekeningservice voert de volgende stappen uit wanneer een PDF-document wordt ondertekend:

1. De dienst van de Handtekening wint de referentie van Truststore terug door de alias over te gaan die in het verzoek wordt gespecificeerd.
1. De Truststore zoekt naar de opgegeven referentie.
1. De referentie wordt geretourneerd aan de service Handtekening en wordt gebruikt om het document te ondertekenen. De referentie wordt ook in de cache geplaatst bij de alias voor toekomstige aanvragen.

Voor informatie over de behandeling van de veiligheidsreferentie, zie *AEM Forms installeren en implementeren* handleiding voor uw toepassingsserver.

>[!NOTE]
>
>Er zijn verschillen tussen ondertekenings- en certificeringsdocumenten. (Zie [PDF-documenten certificeren](digitally-signing-certifying-documents.md#certifying-pdf-documents).)

>[!NOTE]
>
>Niet alle PDF-documenten ondersteunen ondertekening. Voor meer informatie over de service Handtekening en het digitaal ondertekenen van documenten raadpleegt u [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>De handtekeningservice ondersteunt geen XDP-bestanden met ingesloten PDF-gegevens als invoer voor een bewerking, zoals certificering van een document. Deze handeling leidt ertoe dat de handtekeningservice een `PDFOperationException`. Om dit probleem op te lossen, zet het XDP-bestand om in een PDF-bestand met behulp van de service Hulpprogramma&#39;s voor PDF en geeft u het geconverteerde PDF-bestand vervolgens door aan een handtekeningservice-bewerking. (Zie [Werken met hulpprogramma&#39;s voor PDF](/help/forms/developing/pdf-utilities.md#working-with-pdf-utilities).)

**Kipher nShield HSM-referentie**

Wanneer u een Cipher nShield HSM-referentie gebruikt om een PDF-document te ondertekenen of certificeren, kan de nieuwe referentie pas worden gebruikt als de J2EE-toepassingsserver waarop AEM Forms is geïmplementeerd, opnieuw is gestart. U kunt echter een configuratiewaarde instellen, wat resulteert in het ondertekenen of certificeren van de bewerking zonder de J2EE-toepassingsserver opnieuw te starten.

U kunt de volgende configuratiewaarde toevoegen in het cknfastrc-bestand, dat zich bevindt op /opt/nfast/cknfastrc (of c:\nfast\cknfastrc):

```shell
    CKNFAST_ASSUME_SINGLE_PROCESS=0
```

Nadat u deze configuratiewaarde aan het cknfastrc dossier toevoegt, kan de nieuwe referentie worden gebruikt zonder de J2EE toepassingsserver opnieuw te beginnen.

    >[!OPMERKING]
    >
    > U wordt aangeraden de SDK opnieuw te starten met de opdracht Ctrl + C. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM ontwikkelomgeving.

**De handtekening wordt niet vertrouwd**

Als bij het certificeren en ondertekenen van hetzelfde PDF-document de certificerende handtekening niet wordt vertrouwd, wordt bij het openen van het PDF-document in Acrobat of Adobe Reader een geel driehoekje weergegeven naast de eerste handtekening. De handtekening voor certificering moet worden vertrouwd om deze situatie te voorkomen.

**Documenten ondertekenen die op XFA gebaseerde formulieren zijn**

Als u probeert een XFA-formulier te ondertekenen met de API van de handtekeningenservice, ontbreken de gegevens mogelijk in het dialoogvenster `View` `Signed` `Version` in Acrobat. Neem bijvoorbeeld de volgende workflow:

* Met behulp van een XDP-bestand dat is gemaakt met Designer, voegt u een formulierontwerp samen dat een handtekeningveld en XML-gegevens bevat die formuliergegevens bevatten. Met de Forms-service kunt u een interactief PDF-document genereren.
* U ondertekent het PDF-document met de API van de handtekeningenservice.

### Overzicht van de stappen {#summary_of_steps-3}

Voer de volgende taken uit om een PDF-document digitaal te ondertekenen:

1. Inclusief projectbestanden.
1. Maak een handtekeningenservice-client.
1. Hiermee wordt het PDF-document ter ondertekening aangeboden.
1. Onderteken het PDF-document.
1. Sla het ondertekende PDF-document op als een PDF-bestand.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

**Een Signatures-client maken**

Voordat u programmatically een verrichting van de dienst van de Handtekening kunt uitvoeren, moet u een cliënt van de dienst van de Handtekening tot stand brengen.

**Het PDF-document laten ondertekenen**

Als u een PDF-document wilt ondertekenen, moet u een PDF-document verkrijgen dat een handtekeningveld bevat. Als een PDF-document geen handtekeningveld bevat, kan het niet worden ondertekend. Een handtekeningveld kan worden toegevoegd met Designer of programmatisch.

**Het PDF-document ondertekenen**

Bij het ondertekenen van een PDF-document kunt u uitvoeringsopties instellen die door de service Handtekening worden gebruikt. U kunt de volgende opties instellen:

* Weergaveopties
* Intrekkingscontrole
* Waarden voor tijdstempels

U stelt weergaveopties in met een `PDFSignatureAppearanceOptionSpec` object. U kunt bijvoorbeeld de datum in een handtekening weergeven door de `PDFSignatureAppearanceOptionSpec` object `setShowDate` methode en doorgeven `true`.

U kunt ook opgeven of een intrekkingscontrole moet worden uitgevoerd die bepaalt of het certificaat dat wordt gebruikt om een PDF-document digitaal te ondertekenen, is ingetrokken. Als u de intrekkingscontrole wilt uitvoeren, kunt u een van de volgende waarden opgeven:

* **NoCheck**: Niet controleren op intrekking uitvoeren.
* **BestEfficit**: Probeer altijd te controleren op intrekking van alle certificaten in de keten. Als er problemen optreden bij de controle, wordt de intrekking als geldig beschouwd. Als er een fout optreedt, moet u ervan uitgaan dat het certificaat niet is ingetrokken.
* **CheckIfAvailable:** Controleer of alle certificaten in de keten zijn ingetrokken als er informatie over intrekking beschikbaar is. Als er problemen optreden bij de controle, wordt aangenomen dat de intrekking ongeldig is. Als er een fout optreedt, gaat u ervan uit dat het certificaat is ingetrokken en ongeldig is. (Dit is de standaardwaarde.)
* **Altijd controleren**: Controleer of alle certificaten in de keten zijn ingetrokken. Als er geen intrekkingsinformatie aanwezig is in een certificaat, wordt aangenomen dat de intrekking ongeldig is.

Als u een intrekkingscontrole wilt uitvoeren op een certificaat, kunt u een URL naar een server met een certificaatintrekkingslijst (CRL) opgeven met een `CRLOptionSpec` object. Als u echter een intrekkingscontrole wilt uitvoeren en u geen URL opgeeft naar een CRL-server, verkrijgt de ondertekeningsservice de URL van het certificaat.

In plaats van een CRL-server te gebruiken, kunt u een OCSP-server (online certificate Status Protocol) gebruiken bij het controleren van intrekkingen. Doorgaans wordt de intrekkingscontrole sneller uitgevoerd wanneer een OCSP-server wordt gebruikt in tegenstelling tot een CRL-server. (Zie &quot;Online Certificate Status Protocol&quot; op [https://tools.ietf.org/html/rfc2560](https://tools.ietf.org/html/rfc2560).)

U kunt de de serverorde plaatsen CRL en OCSP die de dienst van de Ondertekening gebruikend de Toepassingen en de Diensten van de Adobe gebruikt. Bijvoorbeeld, als de server OCSP eerst in de Toepassingen en de Diensten van de Adobe wordt geplaatst, dan wordt de server OCSP gecontroleerd, die door de server CRL wordt gevolgd. (Zie &quot;Certificaten en gegevens beheren met Betrouwbaarheidsopslag&quot; in de Help van AAC).

Als u opgeeft dat u de intrekkingscontrole niet wilt uitvoeren, controleert de service Handtekening niet of het certificaat dat is gebruikt om een document te ondertekenen of te certificeren, is ingetrokken. Dat wil zeggen dat CRL- en OCSP-serverinformatie wordt genegeerd.

>[!NOTE]
>
>Hoewel een CRL- of OCSP-server in het certificaat kan worden opgegeven, kunt u de in het certificaat opgegeven URL overschrijven met een `CRLOptionSpec` en `OCSPOptionSpec` object. Als u bijvoorbeeld de CRL-server wilt overschrijven, kunt u de opdracht `CRLOptionSpec` object `setLocalURI` methode.

Tijdstempel verwijst naar het proces waarbij de tijd wordt bijgehouden waarop een ondertekend of gecertificeerd document is gewijzigd. Nadat een document is ondertekend, mag het niet meer worden gewijzigd, zelfs niet door de eigenaar van het document. Met tijdstempels kunt u de geldigheid van een ondertekend of gecertificeerd document afdwingen. U kunt opties voor tijdstempels instellen met een `TSPOptionSpec` object. U kunt bijvoorbeeld de URL van een server met een tijdstempelprovider (TSP) opgeven.

>[!NOTE]
>
>Doorloop in de secties Java en webservice en de bijbehorende snelle start, wordt de intrekkingscontrole gebruikt. Omdat er geen CRL- of OCSP-serverinformatie is opgegeven, wordt de serverinformatie opgehaald uit het certificaat dat wordt gebruikt om het PDF-document digitaal te ondertekenen.

Als u een PDF-document wilt ondertekenen, kunt u de volledig gekwalificeerde naam opgeven van het handtekeningveld dat de digitale handtekening bevat, zoals `form1[0].#subform[1].SignatureField3[3]`. Bij gebruik van een XFA-formulierveld kan ook de gedeeltelijke naam van het handtekeningveld worden gebruikt: `SignatureField3[3]`.

U moet ook verwijzen naar een beveiligingsreferentie om een PDF-document digitaal te ondertekenen. Als u naar een beveiligingsreferentie wilt verwijzen, geeft u een alias op. De alias is een verwijzing naar een werkelijke referentie die kan voorkomen in een PKCS#12-bestand (met de extensie .pfx) of een hardwarebeveiligingsmodule (HSM). Voor informatie over de veiligheidsreferentie raadpleegt u de *AEM Forms installeren en implementeren* handleiding voor uw toepassingsserver.

**Ondertekend PDF-document opslaan**

Nadat de handtekeningservice het PDF-document digitaal heeft ondertekend, kunt u het opslaan als een PDF-bestand zodat gebruikers het kunnen openen in Acrobat of Adobe Reader.

**Zie ook**

[PDF-documenten digitaal ondertekenen met de Java API](digitally-signing-certifying-documents.md#digitally-sign-pdf-documents-using-the-java-api)

[PDF-documenten digitaal ondertekenen met de API voor webservices](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Handtekeningvelden toevoegen](digitally-signing-certifying-documents.md#adding-signature-fields)

[Namen van handtekeningvelden ophalen](digitally-signing-certifying-documents.md#retrieving-signature-field-names)

### PDF-documenten digitaal ondertekenen met de Java API {#digitally-sign-pdf-documents-using-the-java-api}

Een PDF-document digitaal ondertekenen met de handtekening-API (Java):

1. Projectbestanden opnemen

   Neem JAR-bestanden van de client, zoals adobe-signatures-client.jar, op in het klassepad van uw Java-project.

1. Een Signatures-client maken

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `SignatureServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Het PDF-document laten ondertekenen

   * Een `java.io.FileInputStream` object dat staat voor het PDF-document dat digitaal moet worden ondertekend met de constructor ervan en dat een tekenreekswaarde doorgeeft die de locatie van het PDF-document aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. Het PDF-document ondertekenen

   Onderteken het PDF-document door het `SignatureServiceClient` object `sign` en geeft de volgende waarden door:

   * A `com.adobe.idp.Document` object dat staat voor het PDF-document dat moet worden ondertekend.
   * Een tekenreekswaarde die de naam vertegenwoordigt van het handtekeningveld dat de digitale handtekening zal bevatten.
   * A `Credential` object dat de referentie vertegenwoordigt die wordt gebruikt om het PDF-document digitaal te ondertekenen. Een `Credential` door het object aan te roepen `Credential` statisch object `getInstance` methode en het overgaan van een koordwaarde die de aliaswaarde specificeert die aan de veiligheidsreferentie beantwoordt.
   * A `HashAlgorithm` object dat een statisch gegevenslid opgeeft dat het hash-algoritme vertegenwoordigt dat moet worden gebruikt om het PDF-document te digest. U kunt bijvoorbeeld `HashAlgorithm.SHA1` om het algoritme SHA1 te gebruiken.
   * Een tekenreekswaarde die de reden vertegenwoordigt waarom het PDF-document digitaal is ondertekend.
   * Een tekenreekswaarde die de contactgegevens van de ondertekenaar vertegenwoordigt.
   * A `PDFSignatureAppearanceOptions` -object dat de weergave van de digitale handtekening bepaalt. U kunt dit object bijvoorbeeld gebruiken om een aangepast logo toe te voegen aan een digitale handtekening.
   * A `java.lang.Boolean` object dat aangeeft of de intrekkingscontrole op het certificaat van de ondertekenaar moet worden uitgevoerd.
   * An `OCSPOptionSpec` -object dat voorkeuren voor ondersteuning van het online certificaatstatusprotocol (OCSP) opslaat. Als de intrekkingscontrole niet is uitgevoerd, wordt deze parameter niet gebruikt en kunt u opgeven `null`.
   * A `CRLPreferences` -object waarin voorkeuren voor certificaatintrekkingslijsten (CRL) zijn opgeslagen. Als de intrekkingscontrole niet is uitgevoerd, wordt deze parameter niet gebruikt en kunt u opgeven `null`.
   * A `TSPPreferences` -object dat voorkeuren opslaat voor ondersteuning van tijdstempelleveranciers (TSP). Deze parameter is optioneel en kan `null`. Zie voor meer informatie [AEM Forms API-naslag](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

   De `sign` methode retourneert een `com.adobe.idp.Document` object dat staat voor het ondertekende PDF-document.

1. Ondertekend PDF-document opslaan

   * Een `java.io.File` en zorg dat de bestandsextensie .pdf is.
   * De `com.adobe.idp.Document` object `copyToFile` methode en doorgeven `java.io.File`om de inhoud van de `Document` naar het bestand. Zorg ervoor dat u de `com.adobe.idp.Document` object dat is geretourneerd door de `sign` methode.

**Zie ook**

[PDF-documenten digitaal ondertekenen](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)

[Snel starten (SOAP-modus): een PDF-document digitaal ondertekenen met de Java API](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-digitally-signing-a-pdf-document-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### PDF-documenten digitaal ondertekenen met de API voor webservices {#digitally-signing-pdf-documents-using-the-web-service-api}

U kunt als volgt een PDF-document digitaal ondertekenen met de handtekening-API (webservice):

1. Projectbestanden opnemen

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Een Signatures-client maken

   * Een `SignatureServiceClient` object met de standaardconstructor.
   * Een `SignatureServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/SignatureService?WSDL`). U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `SignatureServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `SignatureServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `SignatureServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Het PDF-document laten ondertekenen

   * Een `BLOB` object met behulp van de constructor. De `BLOB` wordt gebruikt om een ondertekend PDF-document op te slaan.
   * Een `System.IO.FileStream` door de constructor aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het PDF-document dat moet worden ondertekend, en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` geeft de inhoud van de bytearray op.

1. Het PDF-document ondertekenen

   Onderteken het PDF-document door het `SignatureServiceClient` object `sign` en geeft de volgende waarden door:

   * A `BLOB` object dat staat voor het PDF-document dat moet worden ondertekend.
   * Een tekenreekswaarde die de naam vertegenwoordigt van het handtekeningveld dat de digitale handtekening zal bevatten.
   * A `Credential` object dat de referentie vertegenwoordigt die wordt gebruikt om het PDF-document digitaal te ondertekenen. Een `Credential` object door de constructor ervan te gebruiken en de alias op te geven door een waarde aan het object toe te wijzen `Credential` object `alias` eigenschap.
   * A `HashAlgorithm` object dat een statisch gegevenslid opgeeft dat het hash-algoritme vertegenwoordigt dat moet worden gebruikt om het PDF-document te digest. U kunt bijvoorbeeld `HashAlgorithm.SHA1` om het algoritme SHA1 te gebruiken.
   * Een Booleaanse waarde die opgeeft of het hash-algoritme wordt gebruikt.
   * Een tekenreekswaarde die de reden vertegenwoordigt waarom het PDF-document digitaal is ondertekend.
   * Een tekenreekswaarde die de locatie van de ondertekenaar vertegenwoordigt.
   * Een tekenreekswaarde die de contactgegevens van de ondertekenaar vertegenwoordigt.
   * A `PDFSignatureAppearanceOptions` -object dat de weergave van de digitale handtekening bepaalt. U kunt dit object bijvoorbeeld gebruiken om een aangepast logo toe te voegen aan een digitale handtekening.
   * A `System.Boolean` object dat aangeeft of de intrekkingscontrole op het certificaat van de ondertekenaar moet worden uitgevoerd. Als deze intrekkingscontrole is uitgevoerd, wordt deze ingesloten in de handtekening. De standaardwaarde is `false`.
   * An `OCSPOptionSpec` -object dat voorkeuren voor ondersteuning van het online certificaatstatusprotocol (OCSP) opslaat. Als de intrekkingscontrole niet is uitgevoerd, wordt deze parameter niet gebruikt en kunt u opgeven `null`. Zie voor informatie over dit object [AEM Forms API-naslag](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).
   * A `CRLPreferences` -object waarin voorkeuren voor certificaatintrekkingslijsten (CRL) zijn opgeslagen. Als de intrekkingscontrole niet is uitgevoerd, wordt deze parameter niet gebruikt en kunt u opgeven `null`.
   * A `TSPPreferences` -object dat voorkeuren opslaat voor ondersteuning van tijdstempelleveranciers (TSP). Deze parameter is optioneel en kan `null`.

   De `sign` methode retourneert een `BLOB` object dat staat voor het ondertekende PDF-document.

1. Ondertekend PDF-document opslaan

   * Een `System.IO.FileStream` object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die staat voor de bestandslocatie van het ondertekende PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van de `BLOB` object dat is geretourneerd door de `sign` methode. Vul de bytearray met de waarde van de `BLOB` object `MTOM` lid.
   * Een `System.IO.BinaryWriter` object door de constructor aan te roepen en de `System.IO.FileStream` object.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door het `System.IO.BinaryWriter` object `Write` en geeft u de bytearray door.

**Zie ook**

[PDF-documenten digitaal ondertekenen](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Interactieve Forms digitaal ondertekenen {#digitally-signing-interactive-forms}

U kunt een interactief formulier ondertekenen dat door de Forms-service wordt gemaakt. Neem bijvoorbeeld de volgende workflow:

* U voegt een op XFA gebaseerd PDF formulier dat is gemaakt met Designer samen met formuliergegevens in een XML-document met behulp van de Forms-service. Op de Forms-server wordt een interactief formulier weergegeven.
* U ondertekent het interactieve formulier met de API van de handtekeningenservice.

Het resultaat is een digitaal ondertekend interactief PDF-formulier. Wanneer u een PDF-formulier ondertekent dat is gebaseerd op een XFA-formulier, moet u ervoor zorgen dat u het PDF-bestand opslaat als een Adobe statisch PDF-formulier. Als u een PDF-formulier probeert te ondertekenen dat is opgeslagen als een Adobe dynamisch PDF-formulier, treedt een uitzondering op. Zorg ervoor dat het formulier een handtekeningveld bevat omdat u het formulier ondertekent dat door de Forms-service wordt geretourneerd.

>[!NOTE]
>
>Voordat u een interactief formulier digitaal kunt ondertekenen, moet u ervoor zorgen dat u het certificaat aan AEM Forms toevoegt. Een certificaat wordt toegevoegd gebruikend beleidsconsole of programmatically gebruikend de Manager API van het Vertrouwen. (Zie [Referenties importeren met de Betrouwbaarheidsbeheer-API](/help/forms/developing/credentials.md#importing-credentials-by-using-the-trust-manager-api).)

Wanneer u de Forms Service API gebruikt, stelt u de `GenerateServerAppearance` runtime-optie voor `true`. Met deze uitvoeringsoptie blijft de weergave van het formulier dat op de server wordt gegenereerd geldig wanneer het in Acrobat of Adobe Reader wordt geopend. Het wordt aanbevolen deze uitvoeringsoptie in te stellen wanneer u een interactief formulier genereert ter ondertekening met de Forms API.

>[!NOTE]
>
>Voordat u interactieve Forms voor digitaal ondertekenen leest, is het raadzaam bekend te zijn met het ondertekenen van PDF-documenten. (Zie [PDF-documenten digitaal ondertekenen](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents).)

### Overzicht van de stappen {#summary_of_steps-4}

Voer de volgende taken uit om een interactief formulier dat de Forms-service retourneert, digitaal te ondertekenen:

1. Inclusief projectbestanden.
1. Maak een Forms- en Signatures-client.
1. Vraag het interactieve formulier aan met de Forms-service.
1. Onderteken het interactieve formulier.
1. Sla het ondertekende PDF-document op als een PDF-bestand.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-forms-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

Voor informatie over de locatie van deze JAR-bestanden raadpleegt u [Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Een Forms- en Signatures-client maken**

Omdat bij deze workflow zowel de Forms- als de Signature-services worden aangeroepen, kunt u zowel een Forms-serviceclient als een Signature Service-client maken.

**Het interactieve formulier ophalen met de Forms-service**

U kunt de Forms-service gebruiken om het interactieve PDF-formulier ter ondertekening te verkrijgen. Vanaf AEM Forms kunt u een `com.adobe.idp.Document` object maken voor de Forms-service die het formulier bevat dat moet worden gegenereerd. Deze methode heet: `renderPDFForm2`. Deze methode retourneert een `com.adobe.idp.Document` object dat het te ondertekenen formulier bevat. U kunt dit doorgeven `com.adobe.idp.Document` -instantie naar de service Handtekening.

Op dezelfde manier kunt u als u webservices gebruikt, de `BLOB` -instantie die de Forms-service terugstuurt naar de handtekeningservice.

>[!NOTE]
>
>De snelle start die wordt gekoppeld aan de sectie Digitaal ondertekenen van interactieve Forms roept het `renderPDFForm2` methode.

**Het interactieve formulier ondertekenen**

Bij het ondertekenen van een PDF-document kunt u uitvoeringsopties instellen die door de handtekeningservice worden gebruikt. U kunt de volgende opties instellen:

* Weergaveopties
* Intrekkingscontrole
* Waarden voor tijdstempels

U stelt weergaveopties in met een `PDFSignatureAppearanceOptionSpec` object. U kunt bijvoorbeeld de datum in een handtekening weergeven door de `PDFSignatureAppearanceOptionSpec` object `setShowDate` methode en doorgeven `true`.

**Ondertekend PDF-document opslaan**

Nadat de handtekeningservice het PDF-document digitaal heeft ondertekend, kunt u het opslaan als een PDF-bestand. Het PDF-bestand kan worden geopend in Acrobat of Adobe Reader.

**Zie ook**

[Een interactief formulier digitaal ondertekenen met de Java API](digitally-signing-certifying-documents.md#digitally-sign-an-interactive-form-using-the-java-api)

[Een interactief formulier digitaal ondertekenen met de webservice-API](digitally-signing-certifying-documents.md#digitally-sign-an-interactive-form-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[PDF-documenten digitaal ondertekenen](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)

[Interactieve PDF forms renderen](/help/forms/developing/rendering-forms.md#rendering-interactive-pdf-forms)

### Een interactief formulier digitaal ondertekenen met de Java API {#digitally-sign-an-interactive-form-using-the-java-api}

Een interactief formulier digitaal ondertekenen met de API voor Forms en handtekening (Java):

1. Projectbestanden opnemen

   Neem JAR-bestanden voor clients, zoals adobe-signatures-client.jar en adobe-forms-client.jar, op in het klassepad van uw Java-project.

1. Een Forms- en Signatures-client maken

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `SignatureServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.
   * Een `FormsServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Het interactieve formulier ophalen met de Forms-service

   * Een `java.io.FileInputStream` object dat staat voor het PDF-document dat aan de Forms-service moet worden doorgegeven met behulp van de constructor. Geef een tekenreekswaarde door die de locatie van het PDF-document aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.
   * Een `java.io.FileInputStream` object dat staat voor het XML-document dat formuliergegevens bevat die met behulp van de constructor aan de Forms-service moeten worden doorgegeven. Geef een tekenreekswaarde door die de locatie van het XML-bestand aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.
   * Een `PDFFormRenderSpec` -object dat wordt gebruikt om uitvoeringsopties in te stellen. De `PDFFormRenderSpec` object `setGenerateServerAppearance` methode en doorgeven `true`.
   * De `FormsServiceClient` object `renderPDFForm2` en geeft de volgende waarden door:

      * A `com.adobe.idp.Document` object dat het PDF-formulier bevat dat moet worden gegenereerd.
      * A `com.adobe.idp.Document` object dat gegevens bevat die met het formulier moeten worden samengevoegd.
      * A `PDFFormRenderSpec` -object dat uitvoeringsopties opslaat.
      * A `URLSpec` object dat URI-waarden bevat die door de Forms-service worden vereist. U kunt `null` voor deze parameterwaarde.
      * A `java.util.HashMap` object waarin bestandsbijlagen zijn opgeslagen. Dit is een optionele parameter en u kunt `null` als u geen bestanden aan het formulier wilt koppelen.

     De `renderPDFForm2` methode retourneert een `FormsResult` object dat een formuliergegevensstroom bevat

   * Haal het PDF-formulier op door het `FormsResult` object `getOutputContent` methode. Deze methode retourneert een `com.adobe.idp.Document` object dat het interactieve formulier vertegenwoordigt.

1. Het interactieve formulier ondertekenen

   Onderteken het PDF-document door het `SignatureServiceClient` object `sign` en geeft de volgende waarden door:

   * A `com.adobe.idp.Document` object dat staat voor het PDF-document dat moet worden ondertekend. Zorg ervoor dat dit object het `com.adobe.idp.Document` object dat is verkregen van de Forms-service.
   * Een tekenreekswaarde die de naam vertegenwoordigt van het handtekeningveld dat wordt ondertekend.
   * A `Credential` object dat de referentie vertegenwoordigt die wordt gebruikt om het PDF-document digitaal te ondertekenen. Een `Credential` door het object aan te roepen `Credential` statisch object `getInstance` methode. Geef een tekenreekswaarde door die de aliaswaarde opgeeft die overeenkomt met de beveiligingsreferentie.
   * A `HashAlgorithm` object dat een statisch gegevenslid opgeeft dat het hash-algoritme vertegenwoordigt dat moet worden gebruikt om het PDF-document te digest. U kunt bijvoorbeeld `HashAlgorithm.SHA1` om het algoritme SHA1 te gebruiken.
   * Een tekenreekswaarde die de reden vertegenwoordigt waarom het PDF-document digitaal is ondertekend.
   * Een tekenreekswaarde die de contactgegevens van de ondertekenaar vertegenwoordigt.
   * A `PDFSignatureAppearanceOptions` -object dat de weergave van de digitale handtekening bepaalt. U kunt dit object bijvoorbeeld gebruiken om een aangepast logo toe te voegen aan een digitale handtekening.
   * A `java.lang.Boolean` object dat aangeeft of de intrekkingscontrole op het certificaat van de ondertekenaar moet worden uitgevoerd.
   * An `OCSPPreferences` -object dat voorkeuren voor ondersteuning van het online certificaatstatusprotocol (OCSP) opslaat. Als de intrekkingscontrole niet is uitgevoerd, wordt deze parameter niet gebruikt en kunt u opgeven `null`.
   * A `CRLPreferences` -object waarin voorkeuren voor certificaatintrekkingslijsten (CRL) zijn opgeslagen. Als de intrekkingscontrole niet is uitgevoerd, wordt deze parameter niet gebruikt en kunt u opgeven `null`.
   * A `TSPPreferences` -object dat voorkeuren opslaat voor ondersteuning van tijdstempelleveranciers (TSP). Deze parameter is optioneel en kan `null`.

   De `sign` methode retourneert een `com.adobe.idp.Document` object dat staat voor het ondertekende PDF-document.

1. Ondertekend PDF-document opslaan

   * Een `java.io.File` en controleer of de bestandsnaamextensie .pdf is.
   * De `com.adobe.idp.Document` object `copyToFile` methode en doorgeven `java.io.File`om de inhoud van de `Document` naar het bestand. Zorg ervoor dat u de `com.adobe.idp.Document` het object dat `sign` geretourneerde methode.

**Zie ook**

[Interactieve Forms digitaal ondertekenen](digitally-signing-certifying-documents.md#digitally-signing-interactive-forms)

[Snel starten (SOAP-modus): een PDF-document digitaal ondertekenen met de Java API](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-digitally-signing-a-pdf-document-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een interactief formulier digitaal ondertekenen met de webservice-API {#digitally-sign-an-interactive-form-using-the-web-service-api}

Een interactief formulier digitaal ondertekenen met de API voor Forms en handtekening (webservice):

1. Projectbestanden opnemen

   Creeer een Microsoft .NET project dat MTOM gebruikt. Omdat deze cliënttoepassing de twee diensten van AEM Forms aanhaalt, creeer twee de dienstverwijzingen. Gebruik de volgende definitie WSDL voor de de dienstverwijzing verbonden aan de dienst van de Handtekening: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   Gebruik de volgende definitie van WSDL voor de de dienstverwijzing verbonden aan de dienst van Forms: `http://localhost:8080/soap/services/FormsService?WSDL&lc_version=9.0.1`.

   Omdat de `BLOB` het gegevenstype is gemeenschappelijk voor beide de dienstverwijzingen, kwalificeer volledig `BLOB` gegevenstype bij gebruik ervan. In de bijbehorende webservice kunt u snel aan de slag met `BLOB` exemplaren zijn volledig gekwalificeerd.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Een Forms- en Signatures-client maken

   * Een `SignatureServiceClient` object met de standaardconstructor.
   * Een `SignatureServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/SignatureService?WSDL`). U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `SignatureServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `SignatureServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `SignatureServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.

   * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

   >[!NOTE]
   >
   >Herhaal deze stappen voor de Forms service client.

1. Het interactieve formulier ophalen met de Forms-service

   * Een `BLOB` object met behulp van de constructor. De `BLOB` wordt gebruikt om een ondertekend PDF-document op te slaan.
   * Een `System.IO.FileStream` door de constructor aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het PDF-document dat moet worden ondertekend, en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` geeft de inhoud van de bytearray op.
   * Een `BLOB` object met behulp van de constructor. De `BLOB` wordt gebruikt om formuliergegevens op te slaan.
   * Een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het XML-bestand dat formuliergegevens bevat, en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` geeft de inhoud van de bytearray op.
   * Een `PDFFormRenderSpec` -object dat wordt gebruikt om uitvoeringsopties in te stellen. De waarde toewijzen `true` aan de `PDFFormRenderSpec` object `generateServerAppearance` veld.
   * De `FormsServiceClient` object `renderPDFForm2` en geeft de volgende waarden door:

      * A `BLOB` object dat het PDF-formulier bevat dat moet worden gegenereerd.
      * A `BLOB` object dat gegevens bevat die met het formulier moeten worden samengevoegd.
      * A `PDFFormRenderSpec` -object dat uitvoeringsopties opslaat.
      * A `URLSpec` object dat URI-waarden bevat die door de Forms-service worden vereist. U kunt `null` voor deze parameterwaarde.
      * A `java.util.HashMap` object waarin bestandsbijlagen zijn opgeslagen. Dit is een optionele parameter en u kunt `null` als u geen bestanden aan het formulier wilt koppelen.
      * Een lange uitvoerparameter die wordt gebruikt om het aantal pagina&#39;s in het formulier op te slaan.
      * Een tekenreeks-uitvoerparameter die wordt gebruikt voor de landinstellingswaarde.
      * A `FormResult` waarde die een uitvoerparameter is die wordt gebruikt om het interactieve formulier op te slaan.

   * Het PDF-formulier ophalen door het `FormsResult` object `outputContent` veld. In dit veld wordt een `BLOB` object dat het interactieve formulier vertegenwoordigt.

1. Het interactieve formulier ondertekenen

   Onderteken het PDF-document door het `SignatureServiceClient` object `sign` en geeft de volgende waarden door:

   * A `BLOB` object dat staat voor het PDF-document dat moet worden ondertekend. Gebruik de `BLOB` -instantie geretourneerd door de Forms-service.
   * Een tekenreekswaarde die de naam vertegenwoordigt van het handtekeningveld dat wordt ondertekend.
   * A `Credential` object dat de referentie vertegenwoordigt die wordt gebruikt om het PDF-document digitaal te ondertekenen. Een `Credential` object door de constructor ervan te gebruiken en de alias op te geven door een waarde aan het object toe te wijzen `Credential` object `alias` eigenschap.
   * A `HashAlgorithm` object dat een statisch gegevenslid opgeeft dat het hash-algoritme vertegenwoordigt dat moet worden gebruikt om het PDF-document te digest. U kunt bijvoorbeeld `HashAlgorithm.SHA1` om het algoritme SHA1 te gebruiken.
   * Een Booleaanse waarde die opgeeft of het hash-algoritme wordt gebruikt.
   * Een tekenreekswaarde die de reden vertegenwoordigt waarom het PDF-document digitaal is ondertekend.
   * Een tekenreekswaarde die de locatie van de ondertekenaar vertegenwoordigt.
   * Een tekenreekswaarde die de contactgegevens van de ondertekenaar vertegenwoordigt.
   * A `PDFSignatureAppearanceOptions` -object dat de weergave van de digitale handtekening bepaalt. U kunt dit object bijvoorbeeld gebruiken om een aangepast logo toe te voegen aan een digitale handtekening.
   * A `System.Boolean` object dat aangeeft of de intrekkingscontrole op het certificaat van de ondertekenaar moet worden uitgevoerd. Als deze intrekkingscontrole is uitgevoerd, wordt deze ingesloten in de handtekening. De standaardwaarde is `false`.
   * An `OCSPPreferences` -object dat voorkeuren voor ondersteuning van het online certificaatstatusprotocol (OCSP) opslaat. Als de intrekkingscontrole niet is uitgevoerd, wordt deze parameter niet gebruikt en kunt u opgeven `null`. Zie voor informatie over dit object [AEM Forms API-naslag](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).
   * A `CRLPreferences` -object waarin voorkeuren voor certificaatintrekkingslijsten (CRL) zijn opgeslagen. Als de intrekkingscontrole niet is uitgevoerd, wordt deze parameter niet gebruikt en kunt u opgeven `null`.
   * A `TSPPreferences` -object dat voorkeuren opslaat voor ondersteuning van tijdstempelleveranciers (TSP). Deze parameter is optioneel en kan `null`.

   De `sign` methode retourneert een `BLOB` object dat staat voor het ondertekende PDF-document.

1. Ondertekend PDF-document opslaan

   * Een `System.IO.FileStream` object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die staat voor de bestandslocatie van het ondertekende PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van de `BLOB` object dat is geretourneerd door de `sign` methode. Vul de bytearray met de waarde van de `BLOB` object `MTOM` lid.
   * Een `System.IO.BinaryWriter` object door de constructor aan te roepen en de `System.IO.FileStream` object.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door het `System.IO.BinaryWriter` object `Write` en geeft u de bytearray door.

**Zie ook**

[Interactieve Forms digitaal ondertekenen](digitally-signing-certifying-documents.md#digitally-signing-interactive-forms)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## PDF-documenten certificeren {#certifying-pdf-documents}

U kunt een PDF-document beveiligen door het te certificeren met een bepaald type handtekening, een zogenaamde gecertificeerde handtekening. Een gecertificeerde handtekening wordt op de volgende manieren onderscheiden van een digitale handtekening:

* Dit moet de eerste handtekening zijn die op het PDF-document wordt toegepast. Dit betekent dat op het moment dat de gecertificeerde handtekening wordt toegepast, alle andere handtekeningvelden in het document niet-ondertekend moeten zijn. Er is slechts één gecertificeerde handtekening toegestaan in een PDF-document. Als u een PDF-document wilt ondertekenen en certificeren, moet u het certificeren voordat u het ondertekent. Nadat u een PDF-document hebt gecertificeerd, kunt u digitale extra handtekeningvelden ondertekenen.
* De auteur of maker van het document kan opgeven dat het document op bepaalde manieren kan worden gewijzigd zonder de gecertificeerde handtekening ongeldig te maken. Het document kan bijvoorbeeld het invullen van formulieren of het plaatsen van opmerkingen toestaan. Als de auteur aangeeft dat een bepaalde wijziging niet is toegestaan, beperkt Acrobat gebruikers het document op die manier te wijzigen. Als dergelijke wijzigingen worden aangebracht, bijvoorbeeld door een andere toepassing te gebruiken, is de gecertificeerde handtekening ongeldig en geeft Acrobat een waarschuwing wanneer een gebruiker het document opent. (Bij niet-gecertificeerde handtekeningen zijn wijzigingen niet mogelijk en maken normale bewerkingsbewerkingen de oorspronkelijke handtekening niet ongeldig.)
* Op het moment van ondertekening wordt het document gescand op specifieke typen inhoud die de inhoud van een document dubbelzinnig of misleidend kunnen maken. Een annotatie kan bijvoorbeeld bepaalde tekst op een pagina verbergen die belangrijk is voor het begrijpen van wat wordt gecertificeerd. Over deze inhoud kan een toelichting (wettelijke verklaring) worden gegeven.

U kunt PDF-documenten programmatisch certificeren met de Java API voor de handtekeningenservice of de API voor de handtekeningwebservice. Wanneer u een PDF-document certificeert, moet u verwijzen naar een beveiligingsreferentie in de Credential-service. Voor informatie over de veiligheidsreferentie raadpleegt u de *AEM Forms installeren en implementeren* handleiding voor uw toepassingsserver.

>[!NOTE]
>
>Als bij het certificeren en ondertekenen van hetzelfde PDF-document de certificaatondertekening niet wordt vertrouwd, wordt naast de eerste handtekening een geel driehoekje weergegeven wanneer u het PDF-document opent in Acrobat of Adobe Reader. De handtekening voor certificering moet worden vertrouwd om deze situatie te voorkomen.

>[!NOTE]
>
>Wanneer u een Cipher nShield HSM-referentie gebruikt om een PDF-document te ondertekenen of certificeren, kan de nieuwe referentie pas worden gebruikt als de J2EE-toepassingsserver waarop AEM Forms is geïmplementeerd, opnieuw is gestart. U kunt echter een configuratiewaarde instellen, wat resulteert in het ondertekenen of certificeren van de bewerking zonder de J2EE-toepassingsserver opnieuw te starten.

U kunt de volgende configuratiewaarde toevoegen in het cknfastrc-bestand, dat zich bevindt op /opt/nfast/cknfastrc (of c:\nfast\cknfastrc):

```shell
    CKNFAST_ASSUME_SINGLE_PROCESS=0
```

Nadat u deze configuratiewaarde aan het cknfastrc dossier toevoegt, kan de nieuwe referentie worden gebruikt zonder de J2EE toepassingsserver opnieuw te beginnen.

>[!NOTE]
>
>Ga voor meer informatie over de service Handtekening en certificering van een document naar [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-5}

Voer de volgende taken uit om een PDF-document te certificeren:

1. Inclusief projectbestanden.
1. Maak een handtekeningclient.
1. Laat het PDF-document certificeren.
1. Certificeer het PDF-document.
1. Sla het gecertificeerde PDF-document op als een PDF-bestand.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

Voor informatie over de locatie van deze JAR-bestanden raadpleegt u [Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Een handtekeningclient maken**

Voordat u een handtekeningbewerking programmatisch kunt uitvoeren, moet u een handtekeningclient maken.

**Laat het PDF-document certificeren**

Als u een PDF-document wilt certificeren, moet u een PDF-document verkrijgen dat een handtekeningveld bevat. Als een PDF-document geen handtekeningveld bevat, kan het niet worden gecertificeerd. Een handtekeningveld kan worden toegevoegd met Designer of programmatisch. Voor informatie over het programmatically toevoegen van een handtekeningsgebied, zie [Handtekeningvelden toevoegen](digitally-signing-certifying-documents.md#adding-signature-fields).

**Het PDF-document certificeren**

Als u een PDF-document wilt certificeren, hebt u de volgende invoerwaarden nodig die door de service Handtekening worden gebruikt voor de certificering van een PDF-document:

* **PDF-document**: Een PDF-document dat een handtekeningveld bevat. Dit is een formulierveld dat een grafische weergave van de gecertificeerde handtekening bevat. Een PDF-document moet een handtekeningveld bevatten voordat het kan worden gecertificeerd. Een handtekeningveld kan worden toegevoegd met Designer of programmatisch. (Zie [Handtekeningvelden toevoegen](digitally-signing-certifying-documents.md#adding-signature-fields).)
* **Naam van handtekeningveld**: De volledig gekwalificeerde naam van het handtekeningveld dat is gecertificeerd. De volgende waarde is een voorbeeld: `form1[0].#subform[1].SignatureField3[3]`. Bij gebruik van een XFA-formulierveld kan ook de gedeeltelijke naam van het handtekeningveld worden gebruikt: `SignatureField3[3]`. Als een null-waarde wordt doorgegeven voor de veldnaam, wordt dynamisch een onzichtbaar handtekeningveld gemaakt en gecertificeerd.
* **Beveiligingsreferentie**: Een referentie die wordt gebruikt om het PDF-document te certificeren. Deze veiligheidsreferentie bevat een wachtwoord en een alias, die een alias moeten aanpassen die in de referentie verschijnt die binnen de Credential dienst wordt gevestigd. De alias is een verwijzing naar een werkelijke referentie die kan voorkomen in een PKCS#12-bestand (met de extensie .pfx) of een hardwarebeveiligingsmodule (HSM).
* **Hash-algoritme**: Een hash-algoritme voor de samenvatting van het PDF-document.
* **Reden voor ondertekening**: Een waarde die wordt weergegeven in Acrobat of Adobe Reader, zodat andere gebruikers weten waarom het PDF-document is gecertificeerd.
* **Locatie van de ondertekenaar**: De locatie van de ondertekenaar die door de referentie wordt opgegeven.
* **Contactgegevens**: Contactgegevens, zoals adres en telefoonnummer, van de ondertekenaar.
* **Machtigingsgegevens**: Machtigingen die de handelingen bepalen die een eindgebruiker op een document kan uitvoeren zonder dat de gecertificeerde handtekening ongeldig wordt. U kunt bijvoorbeeld de machtiging zo instellen dat elke wijziging in het PDF-document ertoe leidt dat de gecertificeerde handtekening ongeldig wordt.
* **Rechtsgrond**: Wanneer een document wordt gecertificeerd, wordt het automatisch gescand op specifieke typen inhoud die de inhoud van een document dubbelzinnig of misleidend kunnen maken. Een annotatie kan bijvoorbeeld bepaalde tekst op een pagina verbergen die belangrijk is voor het begrijpen van wat wordt gecertificeerd. Tijdens het scanproces worden waarschuwingen over dit type inhoud gegenereerd. Deze waarde biedt een aanvullende uitleg van de inhoud die waarschuwingen heeft gegenereerd.
* **Weergaveopties**: Opties die de weergave van de gecertificeerde handtekening bepalen. De gecertificeerde handtekening kan bijvoorbeeld datumgegevens weergeven.
* **Intrekkingscontrole**: Deze waarde geeft aan of de intrekkingscontrole is uitgevoerd voor het certificaat van de ondertekenaar. De standaardinstelling van `false` betekent dat de intrekkingscontrole niet is uitgevoerd.
* **OCSP-instellingen**: Instellingen voor ondersteuning van het online certificaatstatusprotocol (OCSP), dat informatie bevat over de status van de referentie die wordt gebruikt voor de certificering van het PDF-document. U kunt bijvoorbeeld de URL van de server opgeven die informatie bevat over de referentie die u gebruikt om u aan te melden bij het PDF-document.
* **CRL-instellingen**: Instellingen voor voorkeuren voor certificaatintrekkingslijst (CRL) als de intrekkingscontrole is uitgevoerd. U kunt bijvoorbeeld opgeven om altijd te controleren of een referentie is ingetrokken.
* **Tijdstempel**: Instellingen die tijdstempelinformatie definiëren die wordt toegepast op de gecertificeerde handtekening. Een tijdstempel geeft aan dat specifieke gegevens voor een bepaald tijdstip zijn vastgesteld. Deze kennis draagt bij tot het opbouwen van een vertrouwensrelatie tussen de ondertekenaar en de verificateur.

**Het gecertificeerde PDF-document opslaan als een PDF-bestand**

Nadat de handtekeningservice het PDF-document heeft gecertificeerd, kunt u het opslaan als een PDF-bestand zodat gebruikers het kunnen openen in Acrobat of Adobe Reader.

**Zie ook**

[PDF-documenten certificeren met de Java API](digitally-signing-certifying-documents.md#certify-pdf-documents-using-the-java-api)

[PDF-documenten certificeren met de webservice-API](digitally-signing-certifying-documents.md#certify-pdf-documents-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Handtekeningvelden toevoegen](digitally-signing-certifying-documents.md#adding-signature-fields)

### PDF-documenten certificeren met de Java API {#certify-pdf-documents-using-the-java-api}

Een PDF-document certificeren met de handtekening-API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-signatures-client.jar, op in het klassepad van uw Java-project.

1. Een handtekeningclient maken

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `SignatureServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Laat het PDF-document certificeren

   * Een `java.io.FileInputStream` -object dat staat voor het PDF-document dat moet worden gecertificeerd door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het PDF-document aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. Het PDF-document certificeren

   Certificeer het document van de PDF door te roepen `SignatureServiceClient` object `certify` en geeft de volgende waarden door:

   * De `com.adobe.idp.Document` -object dat het te certificeren PDF-document vertegenwoordigt.
   * Een tekenreekswaarde die de naam vertegenwoordigt van het handtekeningveld dat de handtekening zal bevatten.
   * A `Credential` -object dat de referentie vertegenwoordigt die wordt gebruikt voor de certificering van het PDF-document. Een `Credential` door het object aan te roepen `Credential` statisch object `getInstance` methode en het overgaan van een koordwaarde die de aliaswaarde specificeert die aan de veiligheidsreferentie beantwoordt.
   * A `HashAlgorithm` object dat een statisch gegevenslid opgeeft dat het hash-algoritme vertegenwoordigt dat wordt gebruikt om het PDF-document te verteren. U kunt bijvoorbeeld `HashAlgorithm.SHA1` om het algoritme SHA1 te gebruiken.
   * Een tekenreekswaarde die de reden vertegenwoordigt waarom het PDF-document is gecertificeerd.
   * Een tekenreekswaarde die de contactgegevens van de ondertekenaar vertegenwoordigt.
   * A `MDPPermissions` -object dat handelingen opgeeft die kunnen worden uitgevoerd op het PDF-document dat de handtekening ongeldig maakt.
   * A `PDFSignatureAppearanceOptions` -object dat de weergave van de gecertificeerde handtekening bepaalt. Wijzig desgewenst de weergave van de handtekening door een methode aan te roepen, zoals `setShowDate`.
   * Een tekenreekswaarde die een uitleg geeft van welke handelingen de handtekening ongeldig maken.
   * A `java.lang.Boolean` object dat aangeeft of de intrekkingscontrole op het certificaat van de ondertekenaar moet worden uitgevoerd. Als deze intrekkingscontrole is uitgevoerd, wordt deze ingesloten in de handtekening. De standaardwaarde is `false`.
   * A `java.lang.Boolean` object dat aangeeft of het handtekeningveld dat wordt gecertificeerd, is vergrendeld. Als het veld is vergrendeld, wordt het handtekeningveld gemarkeerd als alleen-lezen, kunnen de eigenschappen ervan niet worden gewijzigd en kan het niet worden gewist door iedereen die niet de vereiste machtigingen heeft. De standaardwaarde is `false`.
   * An `OCSPPreferences` -object dat voorkeuren voor ondersteuning van het online certificaatstatusprotocol (OCSP) opslaat. Als de intrekkingscontrole niet is uitgevoerd, wordt deze parameter niet gebruikt en kunt u opgeven `null`. Zie voor informatie over dit object [AEM Forms API-naslag](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).
   * A `CRLPreferences` -object waarin voorkeuren voor certificaatintrekkingslijsten (CRL) zijn opgeslagen. Als de intrekkingscontrole niet is uitgevoerd, wordt deze parameter niet gebruikt en kunt u opgeven `null`.
   * A `TSPPreferences` -object dat voorkeuren opslaat voor ondersteuning van tijdstempelleveranciers (TSP). Nadat u bijvoorbeeld een `TSPPreferences` -object, kunt u de URL van de TSP-server instellen door de `TSPPreferences` object `setTspServerURL` methode. Deze parameter is optioneel en kan `null`. Zie voor meer informatie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

   De `certify` methode retourneert een `com.adobe.idp.Document` object dat staat voor het gecertificeerde PDF-document.

1. Het gecertificeerde PDF-document opslaan als een PDF-bestand

   * Een `java.io.File` en zorg dat de bestandsextensie .pdf is.
   * De `com.adobe.idp.Document` object `copyToFile` methode om de inhoud van de `com.adobe.idp.Document` naar het bestand.

**Zie ook**

[PDF-documenten certificeren](digitally-signing-certifying-documents.md#certifying-pdf-documents)

[Snel starten (SOAP-modus): Een PDF-document certificeren met de Java API](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-certifying-a-pdf-document-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### PDF-documenten certificeren met de webservice-API {#certify-pdf-documents-using-the-web-service-api}

Certificeer een PDF-document met de handtekening-API (webservice):

1. Projectbestanden opnemen

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Een handtekeningclient maken

   * Een `SignatureServiceClient` object met de standaardconstructor.
   * Een `SignatureServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/SignatureService?WSDL`). U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `SignatureServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `SignatureServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `SignatureServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Laat het PDF-document certificeren

   * Een `BLOB` object met behulp van de constructor. De `BLOB` wordt gebruikt om een gecertificeerd PDF-document op te slaan.
   * Een `System.IO.FileStream` door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het te certificeren PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` data member de inhoud van de bytearray.

1. Het PDF-document certificeren

   Certificeer het document van de PDF door te roepen `SignatureServiceClient` object `certify` en geeft de volgende waarden door:

   * De `BLOB` -object dat het te certificeren PDF-document vertegenwoordigt.
   * Een tekenreekswaarde die de naam vertegenwoordigt van het handtekeningveld dat de handtekening zal bevatten.
   * A `Credential` -object dat de referentie vertegenwoordigt die wordt gebruikt voor de certificering van het PDF-document. Een `Credential` object met behulp van de constructor en geef de alias op door een waarde toe te wijzen aan de `Credential` object `alias` eigenschap.
   * A `HashAlgorithm` object dat een statisch gegevenslid opgeeft dat het hash-algoritme vertegenwoordigt dat wordt gebruikt om het PDF-document te verteren. U kunt bijvoorbeeld `HashAlgorithm.SHA1` om het algoritme SHA1 te gebruiken.
   * Een Booleaanse waarde die opgeeft of het hash-algoritme wordt gebruikt.
   * Een tekenreekswaarde die de reden vertegenwoordigt waarom het PDF-document is gecertificeerd.
   * Een tekenreekswaarde die de locatie van de ondertekenaar vertegenwoordigt.
   * Een tekenreekswaarde die de contactgegevens van de ondertekenaar vertegenwoordigt.
   * An `MDPPermissions` Het lid met statische gegevens van het object dat handelingen opgeeft die kunnen worden uitgevoerd op het PDF-document waardoor de handtekening ongeldig wordt.
   * Een Booleaanse waarde die aangeeft of de `MDPPermissions` object dat als vorige parameterwaarde is doorgegeven.
   * Een tekenreekswaarde die aangeeft welke handelingen de handtekening ongeldig maken.
   * A `PDFSignatureAppearanceOptions` -object dat de weergave van de gecertificeerde handtekening bepaalt. Een `PDFSignatureAppearanceOptions` object met behulp van de constructor. U kunt de weergave van de handtekening wijzigen door een van de gegevensleden in te stellen.
   * A `System.Boolean` object dat aangeeft of de intrekkingscontrole op het certificaat van de ondertekenaar moet worden uitgevoerd. Als deze intrekkingscontrole is uitgevoerd, wordt deze ingesloten in de handtekening. De standaardwaarde is `false`.
   * A `System.Boolean` object dat aangeeft of het handtekeningveld dat wordt gecertificeerd, is vergrendeld. Als het veld is vergrendeld, wordt het handtekeningveld gemarkeerd als alleen-lezen, kunnen de eigenschappen ervan niet worden gewijzigd en kan het niet worden gewist door iedereen die niet de vereiste machtigingen heeft. De standaardwaarde is `false`.
   * A `System.Boolean` object dat opgeeft of het handtekeningveld vergrendeld is. Dat wil zeggen, als je doorgeeft `true` naar de vorige parameter, dan pas `true` naar deze parameter.
   * An `OCSPPreferences` -object dat voorkeuren voor ondersteuning van het online certificaatstatusprotocol (OCSP) opslaat. Hiermee wordt informatie gegeven over de status van de referentie die wordt gebruikt voor de certificering van het PDF-document. Als de intrekkingscontrole niet is uitgevoerd, wordt deze parameter niet gebruikt en kunt u opgeven `null`.
   * A `CRLPreferences` -object waarin voorkeuren voor certificaatintrekkingslijsten (CRL) zijn opgeslagen. Als de intrekkingscontrole niet is uitgevoerd, wordt deze parameter niet gebruikt en kunt u opgeven `null`.
   * A `TSPPreferences` -object dat voorkeuren opslaat voor ondersteuning van tijdstempelleveranciers (TSP). Nadat u bijvoorbeeld een `TSPPreferences` -object, kunt u de URL van de TSP instellen door de `TSPPreferences` object `tspServerURL` lid. Deze parameter is optioneel en kan `null`.

   De `certify` methode retourneert een `BLOB` object dat staat voor het gecertificeerde PDF-document.

1. Het gecertificeerde PDF-document opslaan als een PDF-bestand

   * Een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het PDF-document dat het gecertificeerde PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van de `BLOB` object dat is geretourneerd door de `certify` methode. Vul de bytearray met de waarde van de `BLOB` object `binaryData` lid.
   * Een `System.IO.BinaryWriter` object door de constructor aan te roepen en de `System.IO.FileStream` object.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door het `System.IO.BinaryWriter` object `Write` en geeft u de bytearray door.

**Zie ook**

[PDF-documenten certificeren](digitally-signing-certifying-documents.md#certifying-pdf-documents)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Digitale handtekeningen verifiëren {#verifying-digital-signatures}

Digitale handtekeningen kunnen worden geverifieerd om ervoor te zorgen dat een ondertekend PDF-document niet is gewijzigd en dat de digitale handtekening geldig is. Wanneer u een digitale handtekening verifieert, kunt u de status van de handtekening en de eigenschappen van de handtekening controleren, zoals de identiteit van de ondertekenaar. Voordat u een digitale handtekening vertrouwt, is het raadzaam deze te controleren. Wanneer u een digitale handtekening verifieert, verwijst u naar een PDF-document dat een digitale handtekening bevat.

Stel dat de identiteit van de ondertekenaar onbekend is. Wanneer u het PDF-document opent in Acrobat, wordt in een waarschuwingsbericht aangegeven dat de identiteit van de ondertekenaar onbekend is, zoals in de volgende afbeelding wordt getoond.

![vd_vd_verivrog](assets/vd_vd_verifysig.png)

Op dezelfde manier kunt u, wanneer u programmatisch een digitale handtekening verifieert, de status van de identiteit van de ondertekenaar bepalen. Als u bijvoorbeeld de digitale handtekening verifieert in het document dat in de vorige illustratie wordt weergegeven, resulteert dit in het feit dat de identiteit van de ondertekenaar onbekend is.

>[!NOTE]
>
>Ga voor meer informatie over de service Handtekening en de verificatie van digitale handtekeningen naar [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-6}

Voer de volgende taken uit om een digitale handtekening te verifiëren:

1. Inclusief projectbestanden.
1. Maak een handtekeningclient.
1. Hiermee wordt het PDF-document opgehaald dat de te verifiëren handtekening bevat.
1. Stel PKI-runtime-opties in.
1. Controleer de digitale handtekening.
1. Bepaal de status van de handtekening.
1. Bepaal de identiteit van de ondertekenaar.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, neemt u de proxybestanden op.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

Voor informatie over de locatie van deze JAR-bestanden raadpleegt u [Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Een handtekeningclient maken**

Voordat u via programmacode een bewerking in de handtekeningenservice uitvoert, moet u een client voor de handtekeningenservice maken.

**Hiermee wordt het PDF-document opgehaald dat de handtekening bevat die moet worden geverifieerd**

Als u een PDF-document digitaal wilt ondertekenen of certificeren met een handtekening, vraagt u een PDF-document op dat een handtekening bevat.

**PKI-runtime-opties instellen**

Stel de volgende PKI-runtimeopties in die de handtekeningservice gebruikt bij het controleren van handtekeningen in een PDF-document:

* Verificatietijd
* Intrekkingscontrole
* Waarden voor tijdstempels

Als onderdeel van het instellen van deze opties kunt u een verificatietijd opgeven. U kunt bijvoorbeeld de huidige tijd selecteren (de tijd op de computer van de validator), die aangeeft dat de huidige tijd moet worden gebruikt. Voor informatie over de verschillende tijdwaarden raadpleegt u de `VerificationTime` opsommingswaarde in [AEM Forms API-naslag](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

U kunt ook opgeven of de intrekkingscontrole moet worden uitgevoerd tijdens het verificatieproces. U kunt bijvoorbeeld een intrekkingscontrole uitvoeren om te bepalen of het certificaat wordt ingetrokken. Zie voor meer informatie over de opties voor intrekkingscontrole de `RevocationCheckStyle` opsommingswaarde in [AEM Forms API-naslag](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

Als u intrekkingscontrole wilt uitvoeren op een certificaat, geeft u een URL op naar een server met een certificaatintrekkingslijst (CRL) met behulp van een `CRLOptionSpec` object. Als u echter geen URL opgeeft naar de CRL-server, verkrijgt de handtekeningservice de URL van het certificaat.

In plaats van een CRL-server te gebruiken, kunt u een OCSP-server (online certificate Status Protocol) gebruiken bij het controleren van intrekkingen. Wanneer u een OCSP-server gebruikt in tegenstelling tot een CRL-server, wordt de intrekkingscontrole meestal sneller uitgevoerd. (Zie [Online Certificate Status Protocol](https://tools.ietf.org/html/rfc2560).)

U kunt de de serverorde plaatsen CRL en OCSP die de dienst van de Ondertekening door de Toepassingen en de Diensten van de Adobe te gebruiken gebruikt. Bijvoorbeeld, als de server OCSP eerst in de Toepassingen en de Diensten van de Adobe wordt geplaatst, dan wordt de server OCSP gecontroleerd, die door de server CRL wordt gevolgd.

Als u de intrekkingscontrole niet uitvoert, controleert de service Handtekening niet of het certificaat is ingetrokken. Dat wil zeggen dat CRL- en OCSP-serverinformatie wordt genegeerd.

>[!NOTE]
>
>U kunt de in het certificaat opgegeven URL overschrijven met een `CRLOptionSpec` en `OCSPOptionSpec` object. Als u bijvoorbeeld de CRL-server wilt overschrijven, kunt u de opdracht `CRLOptionSpec` object `setLocalURI` methode.

Tijdstempel is het proces waarbij de tijd wordt bijgehouden waarop een ondertekend of gecertificeerd document is gewijzigd. Nadat een document is ondertekend, kan niemand het wijzigen. Met tijdstempels kunt u de geldigheid van een ondertekend of gecertificeerd document afdwingen. U kunt opties voor tijdstempels instellen met een `TSPOptionSpec` object. U kunt bijvoorbeeld de URL van een server met een tijdstempelprovider (TSP) opgeven.

>[!NOTE]
>
>In Java en de Webdienst begint snel, wordt de controletijd geplaatst aan `VerificationTime.CURRENT_TIME` en de intrekkingscontrole is ingesteld op `RevocationCheckStyle.BestEffort`. Omdat er geen CRL- of OCSP-serverinformatie is opgegeven, wordt de serverinformatie opgehaald uit het certificaat.

**De digitale handtekening verifiëren**

Als u een handtekening wilt verifiëren, geeft u de volledig gekwalificeerde naam op van het handtekeningveld dat de handtekening bevat, zoals `form1[0].#subform[1].SignatureField3[3]`. Wanneer u een XFA-formulierveld gebruikt, kunt u ook de gedeeltelijke naam van het handtekeningveld gebruiken: `SignatureField3`.

De service Handtekening beperkt standaard de tijd die een document na de validatietijd kan worden ondertekend tot 65 minuten. Als een gebruiker probeert een handtekening op het huidige tijdstip te verifiëren en de ondertekeningstijd later is dan de huidige tijd en binnen 65 minuten, genereert de handtekeningservice geen verificatiefout.

>[!NOTE]
>
>Voor andere waarden die u nodig hebt voor het verifiëren van een handtekening, raadpleegt u [AEM Forms API-naslag](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**De status van de handtekening bepalen**

Als onderdeel van de verificatie van een digitale handtekening, kunt u de status van de handtekening controleren.

**De identiteit van de ondertekenaar bepalen**

U kunt de identiteit van de ondertekenaar bepalen. Dit kan een van de volgende waarden zijn:

* **Onbekend**: Deze ondertekenaar is onbekend omdat de verificatie van de ondertekenaar niet kan worden uitgevoerd.
* **Ververtrouwd**: Deze ondertekenaar wordt vertrouwd.
* **Niet vertrouwd**: Deze ondertekenaar wordt niet vertrouwd.

**Zie ook**

[Digitale handtekeningen verifiëren met de Java API](#verify-digital-signatures-using-the-java-api)

[Digitale handtekeningen verifiëren met de webservice-API](#verify-digital-signatures-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Digitale handtekeningen verifiëren met de Java API {#verify-digital-signatures-using-the-java-api}

Verifieer een digitale handtekening met de API van de Handtekeningenservice (Java):

1. Projectbestanden opnemen

   Neem JAR-bestanden van de client, zoals adobe-signatures-client.jar, op in het klassepad van uw Java-project.

1. Een handtekeningclient maken

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `SignatureServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Hiermee wordt het PDF-document opgehaald dat de handtekening bevat die moet worden geverifieerd

   * Een `java.io.FileInputStream` object dat staat voor het PDF-document dat de handtekening bevat die moet worden geverifieerd met behulp van de constructor ervan. Geef een tekenreekswaarde door die de locatie van het PDF-document aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. PKI-runtime-opties instellen

   * Een `PKIOptions` object met behulp van de constructor.
   * Stel de verificatietijd in door de `PKIOptions` object `setVerificationTime` methode en een `VerificationTime` opsommingswaarde die de verificatietijd opgeeft.
   * De optie voor intrekkingscontrole instellen door een aanroep te maken `PKIOptions` object `setRevocationCheckStyle` methode en een `RevocationCheckStyle` opsommingswaarde die aangeeft of een intrekkingscontrole moet worden uitgevoerd.

1. De digitale handtekening verifiëren

   Verifieer de handtekening door de `SignatureServiceClient` object `verify2` en geeft de volgende waarden door:

   * A `com.adobe.idp.Document` object dat een digitaal ondertekend of gecertificeerd PDF-document bevat.
   * Een tekenreekswaarde die staat voor de naam van het handtekeningveld dat de te controleren handtekening bevat.
   * A `PKIOptions` object dat PKI-runtimeopties bevat.
   * A `VerifySPIOptions` instantie die SPI-informatie bevat. U kunt `null` voor deze parameter.

   De `verify2` methode retourneert een `PDFSignatureVerificationInfo` object dat informatie bevat die kan worden gebruikt om de digitale handtekening te verifiëren.

1. De status van de handtekening bepalen

   * De status van de handtekening bepalen door de `PDFSignatureVerificationInfo` object `getStatus` methode. Deze methode retourneert een `SignatureStatus` object dat de status van de handtekening aangeeft. Als een ondertekend PDF-document bijvoorbeeld niet wordt gewijzigd, retourneert deze methode `SignatureStatus.DocumentSigNoChanges`.

1. De identiteit van de ondertekenaar bepalen

   * Bepaal de identiteit van de ondertekenaar door de `PDFSignatureVerificationInfo` object `getSigner` methode. Deze methode retourneert een `IdentityInformation` object.
   * De `IdentityInformation` object `getStatus` methode om de identiteit van de ondertekenaar te bepalen. Deze methode retourneert een `IdentityStatus` opsommingswaarde die de identiteit opgeeft. Als de ondertekenaar bijvoorbeeld wordt vertrouwd, retourneert deze methode `IdentityStatus.TRUSTED`.

**Zie ook**

[Digitale handtekeningen verifiëren](#verify-digital-signatures-using-the-java-api)

[Snel starten (SOAP-modus): een digitale handtekening verifiëren met de Java API](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-verifying-a-digital-signature-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Digitale handtekeningen verifiëren met de webservice-API {#verify-digital-signatures-using-the-web-service-api}

Verifieer een digitale handtekening met behulp van de Signature Service API (webservice):

1. Projectbestanden opnemen

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Een handtekeningclient maken

   * Een `SignatureServiceClient` object met de standaardconstructor.
   * Een `SignatureServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/SignatureService?WSDL`). U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `SignatureServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `SignatureServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `SignatureServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Hiermee wordt het PDF-document opgehaald dat de handtekening bevat die moet worden geverifieerd

   * Een `BLOB` object met behulp van de constructor. De `BLOB` wordt gebruikt om een PDF-document op te slaan dat een digitale of gecertificeerde handtekening bevat die moet worden geverifieerd.
   * Een `System.IO.FileStream` object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die staat voor de bestandslocatie van het ondertekende PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` methode. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` geeft de inhoud van de bytearray op.

1. PKI-runtime-opties instellen

   * Een `PKIOptions` object met behulp van de constructor.
   * Stel de verificatietijd in door de `PKIOptions` object `verificationTime` lid van de gegevens `VerificationTime` opsommingswaarde die de verificatietijd opgeeft.
   * Stel de optie voor intrekkingscontrole in door de optie `PKIOptions` object `revocationCheckStyle` lid van de gegevens `RevocationCheckStyle` opsommingswaarde die aangeeft of een intrekkingscontrole moet worden uitgevoerd.

1. De digitale handtekening verifiëren

   Verifieer de handtekening door de `SignatureServiceClient` object `verify2` en geeft de volgende waarden door:

   * De `BLOB` object dat een digitaal ondertekend of gecertificeerd PDF-document bevat.
   * Een tekenreekswaarde die staat voor de naam van het handtekeningveld dat de te controleren handtekening bevat.
   * A `PKIOptions` object dat PKI-runtimeopties bevat.
   * A `VerifySPIOptions` instantie die SPI-informatie bevat. U kunt `null` voor deze parameter.

   De `verify2` methode retourneert een `PDFSignatureVerificationInfo` object dat informatie bevat die kan worden gebruikt om de digitale handtekening te verifiëren.

1. De status van de handtekening bepalen

   De status van de handtekening bepalen door de waarde van de `PDFSignatureVerificationInfo` object `status` lid. Dit gegevenslid slaat een `SignatureStatus` object dat de status van de handtekening aangeeft. Als bijvoorbeeld een ondertekend PDF-document wordt gewijzigd, wordt `status` gegevenslid slaat de waarde op `SignatureStatus.DocumentSigNoChanges`.

1. De identiteit van de ondertekenaar bepalen

   * Bepaal de identiteit van de ondertekenaar door de waarde van het dialoogvenster op te halen `PDFSignatureVerificationInfo` object `signer` lid. Dit lid retourneert een `IdentityInformation` object.
   * De `IdentityInformation` object `status` lid van gegevens om de identiteit van de ondertekenaar te bepalen. Dit gegevenslid retourneert een `IdentityStatus` opsommingswaarde die de identiteit opgeeft. Als de ondertekenaar bijvoorbeeld wordt vertrouwd, retourneert dit lid `IdentityStatus.TRUSTED`.

**Zie ook**

[Digitale handtekeningen verifiëren](#verify-digital-signatures-using-the-java-api)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Meerdere digitale handtekeningen controleren {#verifying-multiple-digital-signatures}

AEM Forms biedt de mogelijkheid om alle digitale handtekeningen in een PDF-document te verifiëren. Stel dat een PDF-document meerdere digitale handtekeningen bevat als resultaat van een bedrijfsproces waarvoor handtekeningen van meerdere ondertekenaars nodig zijn. Neem bijvoorbeeld een financiële transactie waarvoor zowel de handtekening van een medewerker als die van een manager is vereist. Met de Java API of de webservice-API van de handtekeningenservice kunt u alle handtekeningen in het PDF-document verifiëren. Wanneer u meerdere digitale handtekeningen controleert, kunt u de status en eigenschappen van elke handtekening controleren. Voordat u een digitale handtekening vertrouwt, is het raadzaam deze te verifiëren. U wordt aangeraden bekend te zijn met het controleren van één digitale handtekening.

>[!NOTE]
>
>Ga voor meer informatie over de service Handtekening en de verificatie van digitale handtekeningen naar [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-7}

Voer de volgende taken uit om meerdere digitale handtekeningen te verifiëren:

1. Inclusief projectbestanden.
1. Maak een handtekeningclient.
1. Hiermee wordt het PDF-document opgehaald dat de handtekeningen bevat die moeten worden geverifieerd.
1. Stel PKI-runtime-opties in.
1. Alle digitale handtekeningen ophalen.
1. Alle handtekeningen doorlopen.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, neemt u de proxybestanden op.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

Voor informatie over de locatie van deze JAR-bestanden raadpleegt u [Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Een handtekeningclient maken**

Voordat u via programmacode een bewerking in de handtekeningenservice uitvoert, moet u een client voor de handtekeningenservice maken.

**Hiermee wordt het PDF-document opgehaald dat de handtekeningen bevat die moeten worden gecontroleerd**

Als u een PDF-document digitaal wilt ondertekenen of certificeren met een handtekening, vraagt u een PDF-document op dat een handtekening bevat.

**PKI-runtime-opties instellen**

Stel de volgende PKI-runtimeopties in die de handtekeningservice gebruikt bij het controleren van alle handtekeningen in een PDF-document:

* Verificatietijd
* Intrekkingscontrole
* Waarden voor tijdstempels

Als onderdeel van het instellen van deze opties kunt u een verificatietijd opgeven. U kunt bijvoorbeeld de huidige tijd selecteren (de tijd op de computer van de validator), die aangeeft dat de huidige tijd moet worden gebruikt. Voor informatie over de verschillende tijdwaarden raadpleegt u de `VerificationTime` opsommingswaarde in [AEM Forms API-naslag](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

U kunt ook opgeven of de intrekkingscontrole moet worden uitgevoerd tijdens het verificatieproces. U kunt bijvoorbeeld een intrekkingscontrole uitvoeren om te bepalen of het certificaat wordt ingetrokken. Zie voor meer informatie over de opties voor intrekkingscontrole de `RevocationCheckStyle` opsommingswaarde in [AEM Forms API-naslag](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

Als u intrekkingscontrole wilt uitvoeren op een certificaat, geeft u een URL op naar een server met een certificaatintrekkingslijst (CRL) met behulp van een `CRLOptionSpec` object. Als u echter geen URL opgeeft naar een CRL-server, verkrijgt de handtekeningservice de URL van het certificaat.

In plaats van een CRL-server te gebruiken, kunt u een OCSP-server (online certificate Status Protocol) gebruiken bij het controleren van intrekkingen. Wanneer u een OCSP-server gebruikt in plaats van een CRL-server, wordt de intrekkingscontrole meestal sneller uitgevoerd. (Zie [Online Certificate Status Protocol](https://tools.ietf.org/html/rfc2560).)

U kunt de de serverorde plaatsen CRL en OCSP die de dienst van de Ondertekening door de Toepassingen en de Diensten van de Adobe te gebruiken gebruikt. Bijvoorbeeld, als de OCSP server eerst in de Toepassingen en de Diensten van de Adobe wordt geplaatst, wordt de server OCSP gecontroleerd, die door de server CRL wordt gevolgd.

Als u de intrekkingscontrole niet uitvoert, controleert de service Handtekening niet of het certificaat is ingetrokken. Dat wil zeggen dat CRL- en OCSP-serverinformatie wordt genegeerd.

>[!NOTE]
>
>U kunt de in het certificaat opgegeven URL overschrijven met een `CRLOptionSpec` en `OCSPOptionSpec` object. Als u bijvoorbeeld de CRL-server wilt overschrijven, kunt u de opdracht `CRLOptionSpec` object `setLocalURI` methode.

Tijdstempel is het proces waarbij de tijd wordt bijgehouden waarop een ondertekend of gecertificeerd document is gewijzigd. Nadat een document is ondertekend, kan niemand het wijzigen. Met tijdstempels kunt u de geldigheid van een ondertekend of gecertificeerd document afdwingen. U kunt opties voor tijdstempels instellen met een `TSPOptionSpec` object. U kunt bijvoorbeeld de URL van een server met een tijdstempelprovider (TSP) opgeven.

>[!NOTE]
>
>In Java en de Webdienst begint snel, wordt de controletijd geplaatst aan `VerificationTime.CURRENT_TIME` en de intrekkingscontrole is ingesteld op `RevocationCheckStyle.BestEffort`. Omdat er geen CRL- of OCSP-serverinformatie is opgegeven, wordt de serverinformatie opgehaald uit het certificaat.

**Alle digitale handtekeningen ophalen**

Als u alle digitale handtekeningen in een PDF-document wilt verifiëren, haalt u de digitale handtekeningen op uit het PDF-document. Alle handtekeningen worden geretourneerd in een lijst. Controleer als onderdeel van de verificatie van een digitale handtekening de status van de handtekening.

>[!NOTE]
>
>In tegenstelling tot wanneer u één digitale handtekening verifieert en u meerdere handtekeningen verifieert, hoeft u de naam van het handtekeningveld niet op te geven.

**Alle handtekeningen doorlopen**

Doorloop elke handtekening. Dat wil zeggen dat voor elke handtekening de digitale handtekening wordt geverifieerd en dat de identiteit van de ondertekenaar en de status van elke handtekening worden gecontroleerd. (Zie [Digitale handtekeningen verifiëren](#verify-digital-signatures-using-the-java-api).)

>[!NOTE]
>
>U hoeft niet alle handtekeningen te doorlopen als de vereiste het hele document is.

**Zie ook**

[Meerdere digitale handtekeningen verifiëren met de Java API](#verify-digital-signatures-using-the-java-api)

[Meerdere digitale handtekeningen verifiëren met de webservice-API](#verify-digital-signatures-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Meerdere digitale handtekeningen verifiëren met de Java API {#verify-multiple-digital-signatures-using-the-java-api}

Verifieer meerdere digitale handtekeningen met de API voor handtekeningenservice (Java):

1. Projectbestanden opnemen

   Neem JAR-bestanden van de client, zoals adobe-signatures-client.jar, op in het klassepad van uw Java-project.

1. Een handtekeningclient maken

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `SignatureServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Hiermee wordt het PDF-document opgehaald dat de handtekeningen bevat die moeten worden gecontroleerd

   * Een `java.io.FileInputStream` object dat staat voor het PDF-document dat meerdere digitale handtekeningen bevat die moeten worden geverifieerd met behulp van de constructor ervan. Geef een tekenreekswaarde door die de locatie van het PDF-document aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. PKI-runtime-opties instellen

   * Een `PKIOptions` object met behulp van de constructor.
   * Stel de verificatietijd in door de `PKIOptions` object `setVerificationTime` methode en een `VerificationTime` opsommingswaarde die de verificatietijd opgeeft.
   * De optie voor intrekkingscontrole instellen door een aanroep te maken `PKIOptions` object `setRevocationCheckStyle` methode en een `RevocationCheckStyle` opsommingswaarde die aangeeft of een intrekkingscontrole moet worden uitgevoerd.

1. Alle digitale handtekeningen ophalen

   De `SignatureServiceClient` object `verifyPDFDocument` en geeft de volgende waarden door:

   * A `com.adobe.idp.Document` object dat een PDF-document bevat dat meerdere digitale handtekeningen bevat.
   * A `PKIOptions` object dat PKI-runtimeopties bevat.
   * A `VerifySPIOptions` instantie die SPI-informatie bevat. U kunt `null` voor deze parameter.

   De `verifyPDFDocument` methode retourneert een `PDFDocumentVerificationInfo` object dat informatie bevat over alle digitale handtekeningen in het PDF-document.

1. Alle handtekeningen doorlopen

   * Alle handtekeningen doorlopen door het aanroepen van de `PDFDocumentVerificationInfo` object `getVerificationInfos` methode. Deze methode retourneert een `java.util.List` object waarbij elk element een `PDFSignatureVerificationInfo` object. Een `java.util.Iterator` -object om de lijst met handtekeningen te doorlopen.
   * Met de `PDFSignatureVerificationInfo` -object, kunt u taken uitvoeren zoals het bepalen van de status van de handtekening door het aanroepen van de `PDFSignatureVerificationInfo` object `getStatus` methode. Deze methode retourneert een `SignatureStatus` object waarvan het lid van het type statische gegevens u op de hoogte stelt van de status van de handtekening. Als de handtekening bijvoorbeeld onbekend is, wordt deze methode geretourneerd `SignatureStatus.DocumentSignatureUnknown`.

**Zie ook**

[Meerdere digitale handtekeningen controleren](#verifying-multiple-digital-signatures)

[Snel starten (SOAP-modus): meerdere digitale handtekeningen controleren met de Java API](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-verifying-multiple-digital-signatures-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Digitale handtekeningen verifiëren](#verify-digital-signatures-using-the-java-api)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Meerdere digitale handtekeningen verifiëren met de webservice-API {#verifying-multiple-digital-signatures-using-the-web-service-api}

Verifieer veelvoudige digitale handtekeningen door de Dienst API van de Handtekening (Webdienst te gebruiken):

1. Projectbestanden opnemen

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Een handtekeningclient maken

   * Een `SignatureServiceClient` object met de standaardconstructor.
   * Een `SignatureServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/SignatureService?WSDL`). U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `SignatureServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `SignatureServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `SignatureServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Hiermee wordt het PDF-document opgehaald dat de handtekeningen bevat die moeten worden gecontroleerd

   * Een `BLOB` object met behulp van de constructor. De `BLOB` Hiermee wordt een PDF-document opgeslagen dat meerdere digitale handtekeningen bevat die moeten worden geverifieerd.
   * Een `System.IO.FileStream` object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die staat voor de bestandslocatie van het PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` methode. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` geeft de inhoud van de bytearray op.

1. PKI-runtime-opties instellen

   * Een `PKIOptions` object met behulp van de constructor.
   * Stel de verificatietijd in door de `PKIOptions` object `verificationTime` lid van de gegevens `VerificationTime` opsommingswaarde die de verificatietijd opgeeft.
   * Stel de optie voor intrekkingscontrole in door de optie `PKIOptions` object `revocationCheckStyle` lid van de gegevens `RevocationCheckStyle` opsommingswaarde die aangeeft of een intrekkingscontrole moet worden uitgevoerd.

1. Alle digitale handtekeningen ophalen

   De `SignatureServiceClient` object `verifyPDFDocument` en geeft de volgende waarden door:

   * A `BLOB` object dat een PDF-document bevat dat meerdere digitale handtekeningen bevat.
   * A `PKIOptions` object dat PKI-runtimeopties bevat.
   * A `VerifySPIOptions` instantie die SPI-informatie bevat. U kunt null opgeven voor deze parameter.

   De `verifyPDFDocument` methode retourneert een `PDFDocumentVerificationInfo` object dat informatie bevat over alle digitale handtekeningen in het PDF-document.

1. Alle handtekeningen doorlopen

   * Alle handtekeningen doorlopen door de `PDFDocumentVerificationInfo` object `verificationInfos` lid. Dit gegevenslid retourneert een `Object` array waarbij elk element een `PDFSignatureVerificationInfo` object.
   * Met de `PDFSignatureVerificationInfo` -object, kunt u taken uitvoeren zoals het bepalen van de status van de handtekening door de `PDFSignatureVerificationInfo` object `status` lid. Dit gegevenslid retourneert een `SignatureStatus` object waarvan het lid van het type statische gegevens u op de hoogte stelt van de status van de handtekening. Als de handtekening bijvoorbeeld onbekend is, wordt deze methode geretourneerd `SignatureStatus.DocumentSignatureUnknown`.

**Zie ook**

[Meerdere digitale handtekeningen controleren](#verifying-multiple-digital-signatures)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Digitale handtekeningen verwijderen {#removing-digital-signatures}

Digitale handtekeningen moeten uit een handtekeningveld worden verwijderd voordat een nieuwere digitale handtekening kan worden toegepast. Een digitale handtekening kan niet worden overschreven. Als u probeert een digitale handtekening toe te passen op een handtekeningveld dat een handtekening bevat, treedt een uitzondering op.

>[!NOTE]
>
>Voor meer informatie over de service Handtekening raadpleegt u [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-8}

Als u een digitale handtekening uit een handtekeningveld wilt verwijderen, voert u de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak een handtekeningclient.
1. Hiermee wordt het PDF-document opgehaald dat een handtekening bevat die u wilt verwijderen.
1. Verwijder de digitale handtekening uit het handtekeningveld.
1. Sla het PDF-document op als een PDF-bestand.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

Voor informatie over de locatie van deze JAR-bestanden raadpleegt u [Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Een handtekeningclient maken**

Voordat u programmatically een verrichting van de dienst van de Handtekening kunt uitvoeren, moet u een cliënt van de dienst van de Handtekening tot stand brengen.

**Het PDF-document ophalen dat een handtekening bevat die moet worden verwijderd**

Als u een handtekening uit een PDF-document wilt verwijderen, moet u een PDF-document met een handtekening verkrijgen.

**De digitale handtekening verwijderen uit het handtekeningveld**

Als u een digitale handtekening uit een PDF-document wilt verwijderen, moet u de naam opgeven van het handtekeningveld dat de digitale handtekening bevat. Bovendien moet u toestemming hebben om de digitale handtekening te verwijderen. Anders treedt een uitzondering op.

**Het PDF-document opslaan als een PDF-bestand**

Nadat de handtekeningservice een digitale handtekening uit een handtekeningveld heeft verwijderd, kunt u het PDF-document opslaan als een PDF-bestand, zodat gebruikers het kunnen openen in Acrobat of Adobe Reader.

**Zie ook**

[Digitale handtekeningen verwijderen met de Java API](digitally-signing-certifying-documents.md#remove-digital-signatures-using-the-java-api)

[Digitale handtekeningen verwijderen met de webservice-API](digitally-signing-certifying-documents.md#remove-digital-signatures-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Handtekeningvelden toevoegen](digitally-signing-certifying-documents.md#adding-signature-fields)

### Digitale handtekeningen verwijderen met de Java API {#remove-digital-signatures-using-the-java-api}

Een digitale handtekening verwijderen met de handtekening-API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-signatures-client.jar, op in het klassepad van uw Java-project.

1. Maak een handtekeningclient.

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `SignatureServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Het PDF-document ophalen dat een handtekening bevat die moet worden verwijderd

   * Een `java.io.FileInputStream` object dat staat voor het PDF-document dat de handtekening bevat die moet worden verwijderd met behulp van de constructor ervan en die een tekenreekswaarde doorgeeft die de locatie van het PDF-document aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. De digitale handtekening verwijderen uit het handtekeningveld

   Een digitale handtekening uit een handtekeningveld verwijderen door het `SignatureServiceClient` object `clearSignatureField` en geeft de volgende waarden door:

   * A `com.adobe.idp.Document` object dat staat voor het PDF-document dat de te verwijderen handtekening bevat.
   * Een tekenreekswaarde die de naam aangeeft van het handtekeningveld dat de digitale handtekening bevat.

   De `clearSignatureField` methode retourneert een `com.adobe.idp.Document` object dat staat voor het PDF-document waaruit de digitale handtekening is verwijderd.

1. Het PDF-document opslaan als een PDF-bestand

   * Een `java.io.File` en zorg dat de bestandsextensie .pdf is.
   * De `com.adobe.idp.Document` object `copyToFile` methode. Geef de `java.io.File` object om de inhoud van het `com.adobe.idp.Document` naar het bestand. Zorg ervoor dat u de `Document` object dat is geretourneerd door de `clearSignatureField` methode.

**Zie ook**

[Digitale handtekeningen verwijderen](digitally-signing-certifying-documents.md#removing-digital-signatures)

[Snel starten (SOAP-modus): een digitale handtekening verwijderen met de Java API](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-removing-a-digital-signature-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Digitale handtekeningen verwijderen met de webservice-API {#remove-digital-signatures-using-the-web-service-api}

Een digitale handtekening verwijderen met de handtekening-API (webservice):

1. Projectbestanden opnemen

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Een handtekeningclient maken

   * Een `SignatureServiceClient` object met de standaardconstructor.
   * Een `SignatureServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/SignatureService?WSDL`). U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `SignatureServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `SignatureServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `SignatureServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Het PDF-document ophalen dat een handtekening bevat die moet worden verwijderd

   * Een `BLOB` object met behulp van de constructor. De `BLOB` wordt gebruikt om een PDF-document op te slaan dat een digitale handtekening bevat die moet worden verwijderd.
   * Een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het ondertekende PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` methode. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` eigenschap met de inhoud van de bytearray.

1. De digitale handtekening verwijderen uit het handtekeningveld

   Verwijder de digitale handtekening door de `SignatureServiceClient` object `clearSignatureField` en geeft de volgende waarden door:

   * A `BLOB` object dat het ondertekende PDF-document bevat.
   * Een tekenreekswaarde die de naam vertegenwoordigt van het handtekeningveld dat de digitale handtekening bevat die moet worden verwijderd.

   De `clearSignatureField` methode retourneert een `BLOB` object dat staat voor het PDF-document waaruit de digitale handtekening is verwijderd.

1. Het PDF-document opslaan als een PDF-bestand

   * Een `System.IO.FileStream` door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het PDF-document dat een leeg handtekeningveld bevat en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van de `BLOB` object dat is geretourneerd door de `sign` methode. Vul de bytearray met de waarde van de `BLOB` object `MTOM` lid.
   * Een `System.IO.BinaryWriter` object door de constructor aan te roepen en de `System.IO.FileStream` object.
   * Schrijf de inhoud van de bytearray naar het PDF-bestand door het `System.IO.BinaryWriter` object `Write` en geeft u de bytearray door.

**Zie ook**

[Digitale handtekeningen verwijderen](digitally-signing-certifying-documents.md#removing-digital-signatures)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
