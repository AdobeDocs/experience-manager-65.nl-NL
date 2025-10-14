---
title: Documenten digitaal ondertekenen en certificeren
description: Met de handtekeningservice kunt u digitale handtekeningvelden toevoegen aan en verwijderen uit een PDF-document, de namen van handtekeningvelden in een PDF-document ophalen, handtekeningvelden wijzigen, PDF-documenten digitaal ondertekenen, PDF-documenten certificeren, digitale handtekeningen in een PDF-document valideren, alle digitale handtekeningen in een PDF-document valideren en een digitale handtekening uit een handtekeningveld verwijderen.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: c200f345-40ab-46fd-b6ed-f3af0a23796b
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services,APIs & Integrations
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '16917'
ht-degree: 0%

---

# Documenten digitaal ondertekenen en certificeren {#digitally-signing-and-certifying-documents}

**de Steekproeven en de voorbeelden in dit document zijn slechts voor AEM Forms op milieu JEE.**

**Ongeveer de Dienst van de Handtekening**

Met de service Handtekening kunt u de beveiliging en privacy beschermen van Adobe PDF-documenten die door uw organisatie worden gedistribueerd en ontvangen. Deze service gebruikt digitale handtekeningen en certificering om ervoor te zorgen dat alleen de beoogde ontvangers documenten kunnen wijzigen. Omdat beveiligingsfuncties op het document zelf worden toegepast, blijft het document gedurende de gehele levenscyclus beveiligd en beheerd. Een document blijft veilig buiten de firewall, wanneer het offline wordt gedownload en wanneer het terug naar uw organisatie wordt verzonden.

>[!NOTE]
>
>U kunt een aangepaste handtekening-handler maken voor de handtekeningservice die wordt aangeroepen wanneer bepaalde bewerkingen worden aangeroepen, zoals het ondertekenen van een PDF-document.

**de gebiedsnamen van de Handtekening**

Voor sommige bewerkingen van de handtekeningservice moet u de naam opgeven van het handtekeningveld waarop een bewerking wordt uitgevoerd. Als u bijvoorbeeld een PDF-document ondertekent, geeft u de naam op van het handtekeningveld dat u wilt ondertekenen. Stel dat de volledige naam van een handtekeningveld `form1[0].Form1[0].SignatureField1[0]` is. U kunt `SignatureField1[0]` opgeven in plaats van `form1[0].Form1[0].SignatureField1[0]` .

Soms ondertekent de handtekeningservice door een conflict (of voert een andere bewerking uit waarvoor de naam van het handtekeningveld vereist is) het verkeerde veld. Dit conflict is het resultaat van de naam `SignatureField1[0]` die op twee of meer plaatsen in hetzelfde PDF-document wordt weergegeven. Neem bijvoorbeeld een PDF-document dat twee handtekeningvelden bevat met de naam `form1[0].Form1[0].SignatureField1[0]` en `form1[0].Form1[0].SubForm1[0].SignatureField1[0]` en u geeft `SignatureField1[0]` op. In dit geval ondertekent de ondertekeningsservice het eerste handtekeningveld dat wordt gevonden terwijl alle handtekeningvelden in het document worden doorlopen.

Als er meerdere handtekeningvelden in een PDF-document staan, is het raadzaam de volledige namen van de handtekeningvelden op te geven. Dat wil zeggen, geef `form1[0].Form1[0].SignatureField1[0]` op in plaats van `SignatureField1[0]` .

U kunt deze taken uitvoeren met de service Handtekening:

* Digitale handtekeningvelden toevoegen aan en verwijderen uit een PDF-document. (Zie [&#x200B; Toevoegend de Gebieden van de Handtekening &#x200B;](digitally-signing-certifying-documents.md#adding-signature-fields).)
* Haal de namen van handtekeningvelden op in een PDF-document. (Zie [&#x200B; het Terugwinnen van de Namen van het Gebied van de Handtekening &#x200B;](digitally-signing-certifying-documents.md#retrieving-signature-field-names).)
* Handtekeningvelden wijzigen. (Zie [&#x200B; Wijzend de Gebieden van de Handtekening &#x200B;](digitally-signing-certifying-documents.md#modifying-signature-fields).)
* PDF-documenten digitaal ondertekenen. (Zie [&#x200B; digitaal het Ondertekenen van de Documenten van PDF &#x200B;](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents).)
* PDF-documenten certificeren. (Zie [&#x200B; Certificerend de Documenten van PDF &#x200B;](digitally-signing-certifying-documents.md#certifying-pdf-documents).)
* Digitale handtekeningen valideren in een PDF-document. (Zie [&#x200B; Verifying Digital Signatures &#x200B;](digitally-signing-certifying-documents.md#verifying-digital-signatures).)
* Alle digitale handtekeningen in een PDF-document valideren. (Zie [&#x200B; Verifying Multiple Digital Signatures &#x200B;](digitally-signing-certifying-documents.md#verifying-digital-signatures).)
* Een digitale handtekening verwijderen uit een handtekeningveld. (Zie [&#x200B; het Verwijderen van Digitale Handtekeningen &#x200B;](digitally-signing-certifying-documents.md#removing-digital-signatures).)

>[!NOTE]
>
>Voor meer informatie over de dienst van de Handtekening, zie [&#x200B; Verwijzing van de Diensten voor AEM Forms &#x200B;](https://www.adobe.com/go/learn_aemforms_services_63).

## Handtekeningvelden toevoegen {#adding-signature-fields}

Digitale handtekeningen worden weergegeven in handtekeningvelden. Dit zijn formuliervelden die een grafische weergave van de handtekening bevatten. Handtekeningvelden kunnen zichtbaar of onzichtbaar zijn. Ondertekenaars kunnen een bestaand handtekeningveld gebruiken of een handtekeningveld programmatisch toevoegen. In beide gevallen moet het handtekeningveld bestaan voordat een PDF-document kan worden ondertekend.

U kunt een handtekeningveld programmatisch toevoegen met de Java API of de API van de Signature-service van de Java-API. U kunt meerdere handtekeningvelden toevoegen aan een PDF-document. Elke handtekeningveldnaam moet echter uniek zijn.

>[!NOTE]
>
>Bij sommige documenttypen voor PDF kunt u geen handtekeningveld programmatisch toevoegen. Voor meer informatie over de dienst van de Handtekening en het toevoegen van handtekeningsgebieden, zie [&#x200B; Verwijzing van de Diensten voor AEM Forms &#x200B;](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary-of-steps}

Als u een handtekeningveld wilt toevoegen aan een PDF-document, voert u de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak een handtekeningclient.
1. Hiermee wordt een PDF-document opgehaald waaraan een handtekeningveld wordt toegevoegd.
1. Voeg een handtekeningveld toe.
1. Sla het PDF-document op als een PDF-bestand.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

**creeer een cliënt van de Handtekening**

Voordat u programmatically een verrichting van de dienst van de Handtekening kunt uitvoeren, moet u een cliënt van de dienst van de Handtekening tot stand brengen.

**krijg een document van de PDF waaraan een handtekeningsgebied wordt toegevoegd**

Vraag een PDF-document op waaraan een handtekeningveld is toegevoegd.

**voeg een handtekeningsgebied** toe

Als u een handtekeningveld aan een PDF-document wilt toevoegen, geeft u coördinaatwaarden op die de locatie van het handtekeningveld aangeven. (Als u een onzichtbaar handtekeningveld toevoegt, zijn deze waarden niet vereist.) U kunt ook opgeven welke velden in het PDF-document worden vergrendeld nadat een handtekening is toegepast op het handtekeningveld.

**sparen het document van de PDF als dossier van PDF**

Nadat de handtekeningservice een handtekeningveld aan het PDF-document heeft toegevoegd, kunt u het document opslaan als een PDF-bestand zodat gebruikers het kunnen openen in Acrobat of Adobe Reader.

**zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[PDF-documenten digitaal ondertekenen](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)

### Handtekeningvelden toevoegen met de Java API {#add-signature-fields-using-the-java-api}

Voeg een handtekeningveld toe met de handtekening-API (Java):

1. Projectbestanden opnemen

   Neem JAR-bestanden van de client, zoals adobe-signatures-client.jar, op in het klassepad van uw Java-project.

1. Een handtekeningclient maken

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `SignatureServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Een PDF-document ophalen waaraan een handtekeningveld wordt toegevoegd

   * Maak een `java.io.FileInputStream` -object dat het PDF-document vertegenwoordigt waaraan een handtekeningveld wordt toegevoegd door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het PDF-document aangeeft.
   * Maak een `com.adobe.idp.Document` -object door de constructor ervan te gebruiken en het `java.io.FileInputStream` -object door te geven.

1. Een handtekeningveld toevoegen

   * Maak een `PositionRectangle` -object dat de locatie van het handtekeningveld opgeeft met behulp van de constructor. Geef binnen de constructor coördinaatwaarden op.
   * Maak desgewenst een `FieldMDPOptions` -object dat de velden opgeeft die zijn vergrendeld wanneer een digitale handtekening wordt toegepast op het handtekeningveld.
   * Voeg een handtekeningveld toe aan een PDF-document door de methode `addSignatureField` van het object `SignatureServiceClient` aan te roepen en de volgende waarden door te geven:

      * A `com.adobe.idp`. `Document` -object dat staat voor het PDF-document waaraan een handtekeningveld wordt toegevoegd.
      * Een tekenreekswaarde die de naam van het handtekeningveld opgeeft.
      * Een `java.lang.Integer` -waarde die staat voor het paginanummer waaraan een handtekeningveld wordt toegevoegd.
      * Een `PositionRectangle` -object dat de locatie van het handtekeningveld opgeeft.
      * Een `FieldMDPOptions` -object dat velden in het PDF-document opgeeft die worden vergrendeld nadat een digitale handtekening is toegepast op het handtekeningveld. Deze parameterwaarde is optioneel en u kunt `null` doorgeven.

   * Een `PDFSeedValueOptions` -object dat verschillende runtimewaarden opgeeft. Deze parameterwaarde is optioneel en u kunt `null` doorgeven.

     De methode `addSignatureField` retourneert een `com.adobe.idp` . `Document` die een PDF-document vertegenwoordigt dat een handtekeningveld bevat.

   >[!NOTE]
   >
   >U kunt de methode `addInvisibleSignatureField` van het `SignatureServiceClient` -object aanroepen om een onzichtbaar handtekeningveld toe te voegen.

1. Het PDF-document opslaan als een PDF-bestand

   * Maak een `java.io.File` -object en controleer of de bestandsextensie .pdf is.
   * Roep `com.adobe.idp` aan. De methode `copyToFile` van het object `Document` om de inhoud van het object `Document` naar het bestand te kopiëren. Zorg ervoor dat u `com.adobe.idp` gebruikt. `Document` die door de methode `addSignatureField` is geretourneerd.

**zie ook**

[Handtekeningenservice-API - Snel starten](/help/forms/developing/signature-service-java-api-quick.md#signature-service-java-api-quick-start-soap)

### Handtekeningvelden toevoegen met de webservice-API {#add-signature-fields-using-the-web-service-api}

Een handtekeningveld toevoegen met de handtekening-API (webservice):

1. Projectbestanden opnemen

   Creeer een Microsoft .NET project dat MTOM gebruikt. Gebruik de volgende WSDL-definitie: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1` .

   >[!NOTE]
   >
   >Vervang `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Een handtekeningclient maken

   * Maak een `SignatureServiceClient` -object met de standaardconstructor.
   * Maak een `SignatureServiceClient.Endpoint.Address` -object met de `System.ServiceModel.EndpointAddress` -constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/SignatureService?WSDL` ). U hoeft het attribuut `lc_version` niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Maak een `System.ServiceModel.BasicHttpBinding` -object door de waarde van het `SignatureServiceClient.Endpoint.Binding` -veld op te halen. De geretourneerde waarde wordt gecast naar `BasicHttpBinding` .
   * Stel het veld `MessageEncoding` van het `System.ServiceModel.BasicHttpBinding` -object in op `WSMessageEncoding.Mtom` . Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld `SignatureServiceClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de bijbehorende wachtwoordwaarde toe aan het veld `SignatureServiceClient.ClientCredentials.UserName.Password` .
      * Wijs de constante waarde `HttpClientCredentialType.Basic` toe aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType` .
      * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` toe aan het veld `BasicHttpBindingSecurity.Security.Mode` .

1. Een PDF-document ophalen waaraan een handtekeningveld wordt toegevoegd

   * Maak een `BLOB` -object met behulp van de constructor. Het `BLOB` -object wordt gebruikt om het PDF-document op te slaan dat een handtekeningveld bevat.
   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `Length` van het object `System.IO.FileStream` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het object `BLOB` door de eigenschap `MTOM` ervan toe te wijzen met de inhoud van de bytearray.

1. Een handtekeningveld toevoegen

   Voeg een handtekeningveld toe aan het PDF-document door de methode `addSignatureField` van het object `SignatureServiceClient` aan te roepen en de volgende waarden door te geven:

   * Een `BLOB` -object dat staat voor het PDF-document waaraan een handtekeningveld wordt toegevoegd.
   * Een tekenreekswaarde die de naam van het handtekeningveld aangeeft.
   * Een geheel getal dat staat voor het paginanummer waaraan een handtekeningveld wordt toegevoegd.
   * Een `PositionRect` -object dat de locatie van het handtekeningveld opgeeft.
   * Een `FieldMDPOptions` -object dat velden in het PDF-document opgeeft die worden vergrendeld nadat een digitale handtekening is toegepast op het handtekeningveld. Deze parameterwaarde is optioneel en u kunt `null` doorgeven.
   * Een `PDFSeedValueOptions` -object dat verschillende runtimewaarden opgeeft. Deze parameterwaarde is optioneel en u kunt `null` doorgeven.

   De methode `addSignatureField` retourneert een `BLOB` -object dat een PDF-document vertegenwoordigt dat een handtekeningveld bevat.

1. Het PDF-document opslaan als een PDF-bestand

   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het PDF-document dat het handtekeningveld en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud wordt opgeslagen van het `BLOB` -object dat door de methode `addSignatureField` is geretourneerd. Vul de bytearray met de waarde van het gegevenslid `binaryData` van het object `BLOB` .
   * Maak een `System.IO.BinaryWriter` -object door de constructor ervan aan te roepen en het `System.IO.FileStream` -object door te geven.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door de methode `Write` van het object `System.IO.BinaryWriter` aan te roepen en de bytearray door te geven.

**zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Namen van handtekeningvelden ophalen {#retrieving-signature-field-names}

U kunt de namen ophalen van alle handtekeningvelden in een PDF-document dat u wilt ondertekenen of certificeren. Als u niet zeker weet welke namen van handtekeningvelden zich in een PDF-document bevinden of als u de namen wilt verifiëren, kunt u deze via programmacode ophalen. De service Handtekening retourneert de volledig gekwalificeerde naam van het handtekeningveld, zoals `form1[0].grantApplication[0].page1[0].SignatureField1[0]` .

>[!NOTE]
>
>Voor meer informatie over de dienst van de Handtekening, zie [&#x200B; Verwijzing van de Diensten voor AEM Forms &#x200B;](https://www.adobe.com/go/learn_aemforms_services_63)

### Overzicht van de stappen {#summary_of_steps-1}

Voer de volgende taken uit om de namen van handtekeningvelden op te halen:

1. Inclusief projectbestanden.
1. Maak een handtekeningclient.
1. Hiermee wordt het PDF-document opgehaald dat handtekeningvelden bevat.
1. Haal de namen van de handtekeningvelden op.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

Voor informatie over de plaats van deze JAR dossiers, zie [&#x200B; Inclusief de bibliotheekdossiers van AEM Forms Java &#x200B;](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**creeer een cliënt van de Handtekening**

Voordat u programmatically een verrichting van de dienst van de Handtekening kunt uitvoeren, moet u een cliënt van de dienst van de Handtekening tot stand brengen.

**krijgt het document van de PDF dat handtekeningsgebieden** bevat

Haal een PDF-document op dat handtekeningvelden bevat.

**wint de namen van het handtekeningsgebied** terug

U kunt namen van handtekeningvelden ophalen nadat u een PDF-document hebt opgehaald dat een of meer handtekeningvelden bevat.

**zie ook**

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

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `SignatureServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Hiermee wordt het PDF-document opgehaald dat handtekeningvelden bevat

   * Maak een `java.io.FileInputStream` -object dat staat voor het PDF-document dat handtekeningvelden bevat door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het PDF-document aangeeft.
   * Maak een `com.adobe.idp.Document` -object door de constructor ervan te gebruiken en het `java.io.FileInputStream` -object door te geven.

1. De namen van handtekeningvelden ophalen

   * Haal de namen van handtekeningvelden op door de methode `getSignatureFieldList` van het object `SignatureServiceClient` aan te roepen en het object `com.adobe.idp.Document` door te geven dat het PDF-document bevat dat handtekeningvelden bevat. Deze methode retourneert een `java.util.List` -object, waarin elk element een `PDFSignatureField` -object bevat. Met dit object kunt u aanvullende informatie verkrijgen over een handtekeningveld, bijvoorbeeld of dit zichtbaar is.
   * Doorloop het `java.util.List` -object om te bepalen of er namen voor handtekeningvelden zijn. Voor elk handtekeningveld in het PDF-document kunt u een apart `PDFSignatureField` -object ophalen. Als u de naam van het handtekeningveld wilt verkrijgen, roept u de methode `getName` van het object `PDFSignatureField` aan. Deze methode retourneert een tekenreekswaarde die de naam van het handtekeningveld opgeeft.

**zie ook**

[Namen van handtekeningvelden ophalen](digitally-signing-certifying-documents.md#retrieving-signature-field-names)

[Snel starten (SOAP modus): namen van handtekeningvelden ophalen met de Java API](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-retrieving-signature-field-names-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Handtekeningveld ophalen met de webservice-API {#retrieve-signature-field-using-the-web-service-api}

Namen van handtekeningvelden ophalen met de handtekening-API (webservice):

1. Projectbestanden opnemen

   Creeer een Microsoft .NET project dat MTOM gebruikt. Gebruik de volgende WSDL-definitie: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1` .

   >[!NOTE]
   >
   >Vervang `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Een handtekeningclient maken

   * Maak een `SignatureServiceClient` -object met de standaardconstructor.
   * Maak een `SignatureServiceClient.Endpoint.Address` -object met de `System.ServiceModel.EndpointAddress` -constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/SignatureService?WSDL` ). U hoeft het attribuut `lc_version` niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Maak een `System.ServiceModel.BasicHttpBinding` -object door de waarde van het `SignatureServiceClient.Endpoint.Binding` -veld op te halen. De geretourneerde waarde wordt gecast naar `BasicHttpBinding` .
   * Stel het veld `MessageEncoding` van het `System.ServiceModel.BasicHttpBinding` -object in op `WSMessageEncoding.Mtom` . Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld `SignatureServiceClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de bijbehorende wachtwoordwaarde toe aan het veld `SignatureServiceClient.ClientCredentials.UserName.Password` .
      * Wijs de constante waarde `HttpClientCredentialType.Basic` toe aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType` .
      * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` toe aan het veld `BasicHttpBindingSecurity.Security.Mode` .

1. Hiermee wordt het PDF-document opgehaald dat handtekeningvelden bevat

   * Maak een `BLOB` -object met behulp van de constructor. Het `BLOB` -object wordt gebruikt om het PDF-document op te slaan dat handtekeningvelden bevat.
   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `Length` van het object `System.IO.FileStream` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` -object door het `MTOM` -veld ervan de inhoud van de bytearray toe te wijzen.

1. De namen van handtekeningvelden ophalen

   * Haal de namen van handtekeningvelden op door de methode `getSignatureFieldList` van het `SignatureServiceClient` -object aan te roepen en het `BLOB` -object door te geven dat het PDF-document bevat dat handtekeningvelden bevat. Deze methode retourneert een `MyArrayOfPDFSignatureField` -verzamelingsobject waarin elk element een `PDFSignatureField` -object bevat.
   * Doorloop het `MyArrayOfPDFSignatureField` -object om te bepalen of er namen voor handtekeningvelden zijn. Voor elk handtekeningveld in het PDF-document kunt u een `PDFSignatureField` -object ophalen. Als u de naam van het handtekeningveld wilt verkrijgen, roept u de methode `getName` van het object `PDFSignatureField` aan. Deze methode retourneert een tekenreekswaarde die de naam van het handtekeningveld opgeeft.

**zie ook**

[Namen van handtekeningvelden ophalen](digitally-signing-certifying-documents.md#retrieving-signature-field-names)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Handtekeningvelden wijzigen {#modifying-signature-fields}

U kunt handtekeningvelden in een PDF-document wijzigen met de Java API en de webservice-API. Als u een handtekeningveld wijzigt, moet u de vergrendelingswoordenboekwaarden van het handtekeningveld of de waarden van het zaadwaardewoordenboek bewerken.

Het woordenboek van het a *gebiedsslot* specificeert een lijst van gebieden die worden gesloten wanneer het handtekeningsgebied wordt ondertekend. Een vergrendeld veld voorkomt dat gebruikers wijzigingen in het veld aanbrengen. A *zaadwaardewoordenboek* bevat het beperken van informatie die op het tijdstip wordt gebruikt de handtekening wordt toegepast. U kunt bijvoorbeeld machtigingen wijzigen die de acties bepalen die kunnen plaatsvinden zonder een handtekening ongeldig te maken.

Door een bestaand handtekeningveld te wijzigen, kunt u het PDF-document aanpassen aan veranderende zakelijke vereisten. Voor een nieuwe bedrijfsvereiste moeten bijvoorbeeld mogelijk alle documentvelden worden vergrendeld nadat het document is ondertekend.

In deze sectie wordt uitgelegd hoe u een handtekeningveld kunt wijzigen door de woordenboekwaarden voor veldvergrendeling en zaadwaarden te wijzigen. Als u wijzigingen aanbrengt in het vergrendelingswoordenboek van het handtekeningveld, worden alle velden in het PDF-document vergrendeld wanneer een handtekeningveld wordt ondertekend. Wijzigingen in het woordenboek voor zaadwaarden staan bepaalde typen wijzigingen in het document niet toe.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Handtekening en het wijzigen van handtekeningsgebieden, zie [&#x200B; Verwijzing van de Diensten voor AEM Forms &#x200B;](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-2}

Voer de volgende taken uit om handtekeningvelden in een PDF-document te wijzigen:

1. Inclusief projectbestanden.
1. Maak een handtekeningclient.
1. Hiermee wordt het PDF-document opgehaald dat het handtekeningveld bevat dat u wilt wijzigen.
1. Stel woordenboekwaarden in.
1. Wijzig het handtekeningveld.
1. Sla het PDF-document op als een PDF-bestand.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

Voor informatie over de plaats van deze JAR dossiers, zie [&#x200B; Including de bibliotheekdossiers van Java van de LiveCycle &#x200B;](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**creeer een cliënt van de Handtekening**

Voordat u programmatically een verrichting van de dienst van de Handtekening kunt uitvoeren, moet u een cliënt van de dienst van de Handtekening tot stand brengen.

**krijgt het document van de PDF dat het handtekeningsgebied bevat om te wijzigen**

Hiermee wordt een PDF-document opgehaald dat het handtekeningveld bevat dat u wilt wijzigen.

**vastgestelde woordenboekwaarden**

Als u een handtekeningveld wilt wijzigen, wijst u waarden toe aan het bijbehorende veldvergrendelingswoordenboek of het bijbehorende zaadwaardewoordenboek. Als u woordenboekwaarden voor handtekeningvelden opgeeft, moet u PDF-documentvelden opgeven die zijn vergrendeld wanneer het handtekeningveld wordt ondertekend. (In deze sectie wordt besproken hoe u alle velden kunt vergrendelen.)

U kunt de volgende zaadwaardewoordenboekwaarden instellen:

* **Controle van de Herziening**: Specificeert of de herroepingscontrole wordt uitgevoerd wanneer een handtekening op het handtekeningsgebied wordt toegepast.
* **opties van het Certificaat**: Wijst waarden aan het woordenboek van de certificaatzaadwaarde toe. Voordat u certificaatopties opgeeft, is het raadzaam bekend te raken met een certificaatzaadwaardewoordenboek. (Zie [&#x200B; Verwijzing van de PDF &#x200B;](https://www.adobe.com/devnet/acrobat/pdfs/pdf_reference_1-7.pdf).)
* **de opties van de Samenvatting**: Wijst samenvattingsalgoritmen toe die voor het ondertekenen worden gebruikt. Geldige waarden zijn SHA1, SHA256, SHA384, SHA512 en RIPEMD160.
* **Filter**: Specificeert de filter die met het handtekeningsgebied wordt gebruikt. U kunt bijvoorbeeld het filter Adobe.PPKLite gebruiken. (Zie [&#x200B; Verwijzing van de PDF &#x200B;](https://www.adobe.com/devnet/acrobat/pdfs/pdf_reference_1-7.pdf).)
* **de opties van de Vlag**: Specificeert de vlagwaarden die met dit handtekeningsgebied worden geassocieerd. De waarde 1 houdt in dat een ondertekenaar alleen de opgegeven waarden voor het item moet gebruiken. De waarde 0 houdt in dat andere waarden zijn toegestaan. Hier zijn de posities van het Beetje:

   * **1 (Filter):** De handtekeningsmanager die moet worden gebruikt om het handtekeningsgebied te ondertekenen
   * **2 (SubFilter):** een serie van namen die op aanvaardbare te gebruiken coderingen wijzen wanneer het ondertekenen
   * **3 (V)**: Het minimum vereiste versieaantal van de handtekeningsmanager dat moet worden gebruikt om het handtekeningsgebied te ondertekenen
   * **4 (Redenen):** een serie van koorden die mogelijke redenen specificeren om een document te ondertekenen
   * **5 (PDFLegalWarnings):** een serie van koorden die mogelijke wettelijke verklaringen specificeren

* **Juridische verklaringen**: Wanneer een document wordt verklaard, wordt het automatisch gescand voor specifieke soorten inhoud die de zichtbare inhoud van een document ambigu of misleidend kunnen maken. Een annotatie kan bijvoorbeeld tekst die belangrijk is voor het begrijpen van wat wordt gecertificeerd, onduidelijk maken. Tijdens het scanproces worden waarschuwingen gegenereerd die de aanwezigheid van dit type inhoud aangeven. Het verstrekt ook een extra verklaring van de inhoud die waarschuwingen kan hebben veroorzaakt.
* **Toestemmingen**: Specificeert toestemmingen die op een document van de PDF kunnen worden gebruikt zonder de handtekening ongeldig te maken.
* **Redenen**: Specificeert redenen waarom dit document moet worden ondertekend.
* **de stempel van de Tijd**: Specificeert tijd-stempelt opties. U kunt bijvoorbeeld de URL instellen van de gebruikte tijdstempelserver.
* **Versie**: Specificeert het minimumversieaantal van de handtekeningsmanager dat moet worden gebruikt om het handtekeningsgebied te ondertekenen.

**wijzig het handtekeningsgebied**

Nadat u een client voor de handtekeningenservice hebt gemaakt, kunt u het PDF-document ophalen dat het handtekeningveld bevat dat u wilt wijzigen en woordenboekwaarden instellen. Vervolgens kunt u de handtekeningservice de opdracht geven het handtekeningveld te wijzigen. De handtekeningservice retourneert vervolgens een PDF-document dat het gewijzigde handtekeningveld bevat. Dit heeft geen invloed op het oorspronkelijke PDF-document.

**sparen het document van de PDF als dossier van PDF**

Sla het PDF-document met het gewijzigde handtekeningveld op als een PDF-bestand zodat gebruikers het kunnen openen in Acrobat of Adobe Reader.

**zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Handtekeningenservice-API - Snel starten](/help/forms/developing/signature-service-java-api-quick.md#signature-service-java-api-quick-start-soap)

[PDF-documenten digitaal ondertekenen](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)

### Handtekeningvelden wijzigen met de Java API {#modify-signature-fields-using-the-java-api}

Wijzig een handtekeningveld met de handtekening-API (Java):

1. Projectbestanden opnemen

   Neem JAR-bestanden van de client, zoals adobe-signatures-client.jar, op in het klassepad van uw Java-project.

1. Een handtekeningclient maken

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `SignatureServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Hiermee wordt het PDF-document opgehaald dat het handtekeningveld bevat dat moet worden gewijzigd

   * Maak een `java.io.FileInputStream` -object dat staat voor het PDF-document dat het handtekeningveld bevat dat moet worden gewijzigd met de constructor ervan en geef een tekenreekswaarde door die de locatie van het PDF-document aangeeft.
   * Maak een `com.adobe.idp.Document` -object door de constructor ervan te gebruiken en het `java.io.FileInputStream` -object door te geven.

1. Woordenboekwaarden instellen

   * Maak een `PDFSignatureFieldProperties` -object met behulp van de constructor. In een `PDFSignatureFieldProperties` -object worden het handtekeningveldvergrendelingswoordenboek en de zaadwaardewoordenboekgegevens opgeslagen.
   * Maak een `PDFSeedValueOptionSpec` -object met behulp van de constructor. Met dit object kunt u woordenboekwaarden voor zaadwaarden instellen.
   * Wijzigingen in het PDF-document niet toestaan door de methode `setMdpValue` van het `PDFSeedValueOptionSpec` -object aan te roepen en de opsommingswaarde `MDPPermissions.NoChanges` door te geven.
   * Maak een `FieldMDPOptionSpec` -object met behulp van de constructor. Met dit object kunt u woordenboekwaarden voor handtekeningveldvergrendeling instellen.
   * Vergrendel alle velden in het PDF-document door de methode `setMdpValue` van het `FieldMDPOptionSpec` -object aan te roepen en de opsommingswaarde `FieldMDPAction.ALL` door te geven.
   * Stel de zaadwaardewoordenboekgegevens in door de methode `setSeedValue` van het object `PDFSignatureFieldProperties` aan te roepen en het object `PDFSeedValueOptionSpec` door te geven.
   * Stel de vergrendelingswoordenboekgegevens voor handtekeningvelden in door de methode `setFieldMDP` van het object `PDFSignatureFieldProperties` aan te roepen en het object `FieldMDPOptionSpec` door te geven.

   >[!NOTE]
   >
   >Zie de klasseverwijzing van `PDFSeedValueOptionSpec` voor informatie over alle waarden in het zaadwaardewoordenboek die u kunt instellen. (Zie [&#x200B; AEM Forms API Verwijzing &#x200B;](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).)

1. Het handtekeningveld wijzigen

   Wijzig het handtekeningveld door de methode `modifySignatureField` van het object `SignatureServiceClient` aan te roepen en de volgende waarden door te geven:

   * Het `com.adobe.idp.Document` -object dat het PDF-document opslaat dat het handtekeningveld bevat dat moet worden gewijzigd
   * Een tekenreekswaarde die de naam van het handtekeningveld opgeeft
   * Het `PDFSignatureFieldProperties` -object dat het handtekeningveld vergrendelingswoordenboek en de zaadwaardewoordenboekgegevens opslaat

   De methode `modifySignatureField` retourneert een `com.adobe.idp.Document` -object dat een PDF-document opslaat dat het gewijzigde handtekeningveld bevat.

1. Het PDF-document opslaan als een PDF-bestand

   * Maak een `java.io.File` -object en controleer of de bestandsnaamextensie .pdf is.
   * Roep de methode `copyToFile` van het object `com.adobe.idp.Document` aan om de inhoud van het object `com.adobe.idp.Document` naar het bestand te kopiëren. Zorg ervoor dat u het object `com.adobe.idp.Document` gebruikt dat de methode `modifySignatureField` heeft geretourneerd.

### Handtekeningvelden wijzigen met de webservice-API {#modify-signature-fields-using-the-web-service-api}

Wijzig een handtekeningveld met de handtekening-API (webservice):

1. Projectbestanden opnemen

   Creeer een Microsoft .NET project dat MTOM gebruikt. Gebruik de volgende WSDL-definitie: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1` .

   >[!NOTE]
   >
   >Vervang `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Een handtekeningclient maken

   * Maak een `SignatureServiceClient` -object met de standaardconstructor.
   * Maak een `SignatureServiceClient.Endpoint.Address` -object met de `System.ServiceModel.EndpointAddress` -constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/SignatureService?WSDL` ). U hoeft het attribuut `lc_version` niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Maak een `System.ServiceModel.BasicHttpBinding` -object door de waarde van het `SignatureServiceClient.Endpoint.Binding` -veld op te halen. De geretourneerde waarde wordt gecast naar `BasicHttpBinding` .
   * Stel het veld `MessageEncoding` van het `System.ServiceModel.BasicHttpBinding` -object in op `WSMessageEncoding.Mtom` . Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld `SignatureServiceClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de bijbehorende wachtwoordwaarde toe aan het veld `SignatureServiceClient.ClientCredentials.UserName.Password` .
      * Wijs de constante waarde `HttpClientCredentialType.Basic` toe aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType` .
      * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` toe aan het veld `BasicHttpBindingSecurity.Security.Mode` .

1. Hiermee wordt het PDF-document opgehaald dat het handtekeningveld bevat dat moet worden gewijzigd

   * Maak een `BLOB` -object met behulp van de constructor. Met het `BLOB` -object wordt het PDF-document opgeslagen dat het handtekeningveld bevat dat moet worden gewijzigd.
   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `Length` van het object `System.IO.FileStream` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het object `BLOB` door de eigenschap `MTOM` ervan toe te wijzen aan de inhoud van de bytearray.

1. Woordenboekwaarden instellen

   * Maak een `PDFSignatureFieldProperties` -object met behulp van de constructor. In dit object worden het handtekeningveldvergrendelingswoordenboek en de zaadwaardewoordenboekgegevens opgeslagen.
   * Maak een `PDFSeedValueOptionSpec` -object met behulp van de constructor. Met dit object kunt u woordenboekwaarden voor zaadwaarden instellen.
   * Wijzigingen in het PDF-document niet toestaan door de opsommingswaarde `MDPPermissions.NoChanges` toe te wijzen aan het gegevenslid van het `PDFSeedValueOptionSpec` object `mdpValue` .
   * Maak een `FieldMDPOptionSpec` -object met behulp van de constructor. Met dit object kunt u woordenboekwaarden voor handtekeningveldvergrendeling instellen.
   * Vergrendel alle velden in het PDF-document door de opsommingswaarde `FieldMDPAction.ALL` toe te wijzen aan het gegevenslid van het `FieldMDPOptionSpec` object `mdpValue` .
   * Stel zaadwaardewoordenboekgegevens in door het `PDFSeedValueOptionSpec` -object toe te wijzen aan het gegevenslid van het `PDFSignatureFieldProperties` object `seedValue` .
   * Stel de vergrendelingswoordenboekgegevens voor handtekeningvelden in door het `FieldMDPOptionSpec` -object toe te wijzen aan het gegevenslid van het `PDFSignatureFieldProperties` object `fieldMDP` .

   >[!NOTE]
   >
   >Zie de klasseverwijzing van `PDFSeedValueOptionSpec` voor informatie over alle waarden in het zaadwaardewoordenboek die u kunt instellen. (Zie [&#x200B; AEM Forms API Verwijzing &#x200B;](https://www.adobe.com/go/learn_aemforms_javadocs_63_en)).

1. Het handtekeningveld wijzigen

   Wijzig het handtekeningveld door de methode `modifySignatureField` van het object `SignatureServiceClient` aan te roepen en de volgende waarden door te geven:

   * Het `BLOB` -object dat het PDF-document opslaat dat het handtekeningveld bevat dat moet worden gewijzigd
   * Een tekenreekswaarde die de naam van het handtekeningveld opgeeft
   * Het `PDFSignatureFieldProperties` -object dat het handtekeningveld vergrendelingswoordenboek en de zaadwaardewoordenboekgegevens opslaat

   De methode `modifySignatureField` retourneert een `BLOB` -object dat een PDF-document opslaat dat het gewijzigde handtekeningveld bevat.

1. Het PDF-document opslaan als een PDF-bestand

   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het PDF-document dat het handtekeningveld bevat, en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud wordt opgeslagen van het object `BLOB` dat door de methode `addSignatureField` wordt geretourneerd. Vul de bytearray met de waarde van het gegevenslid `MTOM` van het object `BLOB` .
   * Maak een `System.IO.BinaryWriter` -object door de constructor ervan aan te roepen en het `System.IO.FileStream` -object door te geven.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door de methode `Write` van het object `System.IO.BinaryWriter` aan te roepen en de bytearray door te geven.

**zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## PDF-documenten digitaal ondertekenen {#digitally-signing-pdf-documents}

Digitale handtekeningen kunnen op PDF-documenten worden toegepast om een beveiligingsniveau te bieden. Digitale handtekeningen bieden, net als handgeschreven handtekeningen, een manier waarop ondertekenaars zichzelf identificeren en instructies over een document maken. De technologie die wordt gebruikt om documenten digitaal te ondertekenen, helpt ervoor te zorgen dat zowel de ondertekenaar als de ontvangers duidelijk zijn over wat is ondertekend en er zeker van zijn dat het document niet is gewijzigd sinds het werd ondertekend.

De documenten van PDF worden ondertekend door middel van openbare-sleuteltechnologie. Een ondertekenaar heeft twee sleutels: een openbare sleutel en een persoonlijke sleutel. De persoonlijke sleutel wordt opgeslagen in de referentie van een gebruiker die beschikbaar moet zijn op het moment van ondertekening. De openbare sleutel wordt opgeslagen in het certificaat van de gebruiker dat beschikbaar moet zijn aan ontvangers om de handtekening te valideren. Informatie over ingetrokken certificaten vindt u in de certificaatintrekkingslijsten (CRL&#39;s) en de online certificaatstatusprotocollen (OCSP&#39;s) die door de certificeringsinstanties (CA&#39;s) worden verspreid. De tijd van het ondertekenen kan van een vertrouwde op bron worden verkregen die als Tijdstempelinstantie wordt bekend.

>[!NOTE]
>
>Voordat u een PDF-document digitaal kunt ondertekenen, moet u ervoor zorgen dat u het certificaat aan AEM Forms toevoegt. Een certificaat wordt toegevoegd gebruikend beleidsconsole of programmatically gebruikend de Manager API van het Vertrouwen. (Zie [&#x200B; het Invoeren Referenties door de Manager API van het Vertrouwen te gebruiken &#x200B;](/help/forms/developing/credentials.md#importing-credentials-by-using-the-trust-manager-api).)

U kunt PDF-documenten programmatisch digitaal ondertekenen. Bij het digitaal ondertekenen van een PDF-document moet u verwijzen naar een beveiligingsreferentie die in AEM Forms bestaat. De referentie is de persoonlijke sleutel die wordt gebruikt voor ondertekening.

De handtekeningservice voert de volgende stappen uit wanneer een PDF-document wordt ondertekend:

1. De dienst van de Handtekening wint de referentie van Truststore terug door de alias over te gaan die in het verzoek wordt gespecificeerd.
1. De Truststore zoekt naar de opgegeven referentie.
1. De referentie wordt geretourneerd aan de service Handtekening en wordt gebruikt om het document te ondertekenen. De referentie wordt ook in de cache geplaatst bij de alias voor toekomstige aanvragen.

Voor informatie over de behandeling van de veiligheidsreferentie, zie *het Installeren van en het Opstellen van de gids van AEM Forms* voor uw toepassingsserver.

>[!NOTE]
>
>Er zijn verschillen tussen ondertekenings- en certificeringsdocumenten. (Zie [&#x200B; Certificerend de Documenten van PDF &#x200B;](digitally-signing-certifying-documents.md#certifying-pdf-documents).)

>[!NOTE]
>
>Niet alle PDF-documenten ondersteunen ondertekening. Voor meer informatie over de dienst van de Handtekening en digitaal het ondertekenen van documenten, zie [&#x200B; Verwijzing van de Diensten voor AEM Forms &#x200B;](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>De handtekeningservice ondersteunt geen XDP-bestanden met ingesloten PDF-gegevens als invoer voor een bewerking, zoals certificering van een document. Deze actie leidt ertoe dat de handtekeningservice een `PDFOperationException` genereert. Om dit probleem op te lossen, zet het XDP-bestand om in een PDF-bestand met behulp van de service Hulpprogramma&#39;s voor PDF en geeft u het geconverteerde PDF-bestand vervolgens door aan een handtekeningservice-bewerking. (Zie [&#x200B; Werkend met Hulpmiddelen van de PDF &#x200B;](/help/forms/developing/pdf-utilities.md#working-with-pdf-utilities).)

**nCipher nShield HSM credential**

Wanneer u een Cipher nShield HSM-referentie gebruikt om een PDF-document te ondertekenen of certificeren, kan de nieuwe referentie pas worden gebruikt als de J2EE-toepassingsserver waarop AEM Forms is geïmplementeerd, opnieuw is gestart. U kunt echter een configuratiewaarde instellen, wat resulteert in het ondertekenen of certificeren van de bewerking zonder de J2EE-toepassingsserver opnieuw te starten.

U kunt de volgende configuratiewaarde toevoegen in het cknfastrc-bestand, dat zich bevindt op /opt/nfast/cknfastrc (of c:\nfast\cknfastrc):

```shell
    CKNFAST_ASSUME_SINGLE_PROCESS=0
```

Nadat u deze configuratiewaarde aan het cknfastrc dossier toevoegt, kan de nieuwe referentie worden gebruikt zonder de J2EE toepassingsserver opnieuw te beginnen.

    >[!NOTE] 
    > 
    > het wordt geadviseerd om &quot;CTRL + C&quot;bevel te gebruiken om SDK opnieuw te beginnen. Het opnieuw beginnen van de AEM SDK gebruikend alternatieve methodes, bijvoorbeeld, het tegenhouden van processen van Java, kan tot inconsistenties in de AEM ontwikkelomgeving leiden.

**de handtekening wordt niet vertrouwd op**

Als bij het certificeren en ondertekenen van hetzelfde PDF-document de certificerende handtekening niet wordt vertrouwd, wordt bij het openen van het PDF-document in Acrobat of Adobe Reader een geel driehoekje weergegeven naast de eerste handtekening. De handtekening voor certificering moet worden vertrouwd om deze situatie te voorkomen.

**het Ondertekenen documenten die op XFA gebaseerde vormen** zijn

Als u probeert een XFA-formulier te ondertekenen met de API van de handtekeningenservice, ontbreken de gegevens mogelijk in de `View` `Signed` `Version` in Acrobat. Neem bijvoorbeeld de volgende workflow:

* Met behulp van een XDP-bestand dat met Designer is gemaakt, voegt u een formulierontwerp samen dat een handtekeningveld en XML-gegevens bevat die formuliergegevens bevatten. Met de Forms-service kunt u een interactief PDF-document genereren.
* U ondertekent het PDF-document met de API van de handtekeningenservice.

### Overzicht van de stappen {#summary_of_steps-3}

Voer de volgende taken uit om een PDF-document digitaal te ondertekenen:

1. Inclusief projectbestanden.
1. Maak een handtekeningenservice-client.
1. Hiermee wordt het PDF-document ter ondertekening aangeboden.
1. Onderteken het PDF-document.
1. Sla het ondertekende PDF-document op als een PDF-bestand.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

**creeer een cliënt van Handtekeningen**

Voordat u programmatically een verrichting van de dienst van de Handtekening kunt uitvoeren, moet u een cliënt van de dienst van de Handtekening tot stand brengen.

**krijg het document van de PDF om te ondertekenen**

Als u een PDF-document wilt ondertekenen, moet u een PDF-document verkrijgen dat een handtekeningveld bevat. Als een PDF-document geen handtekeningveld bevat, kan het niet worden ondertekend. Een handtekeningveld kan worden toegevoegd met Designer of via programmacode.

**teken het document van de PDF**

Bij het ondertekenen van een PDF-document kunt u uitvoeringsopties instellen die door de service Handtekening worden gebruikt. U kunt de volgende opties instellen:

* Weergaveopties
* Intrekkingscontrole
* Waarden voor tijdstempels

U stelt vormgevingsopties in met een `PDFSignatureAppearanceOptionSpec` -object. U kunt bijvoorbeeld de datum binnen een handtekening weergeven door de methode `setShowDate` van het object `PDFSignatureAppearanceOptionSpec` aan te roepen en door te geven `true` .

U kunt ook opgeven of een intrekkingscontrole moet worden uitgevoerd die bepaalt of het certificaat dat wordt gebruikt om een PDF-document digitaal te ondertekenen, is ingetrokken. Als u de intrekkingscontrole wilt uitvoeren, kunt u een van de volgende waarden opgeven:

* **NoCheck**: Voer geen controle op intrekking uit.
* **BesteEfficiëntie**: Probeer altijd om intrekking van alle certificaten in de ketting te controleren. Als er problemen optreden bij de controle, wordt de intrekking als geldig beschouwd. Als er een fout optreedt, moet u ervan uitgaan dat het certificaat niet is ingetrokken.
* **CheckIfAvailable:** Controle voor intrekking van alle certificaten in de keten als de intrekkingsinformatie beschikbaar is. Als er problemen optreden bij de controle, wordt aangenomen dat de intrekking ongeldig is. Als er een fout optreedt, gaat u ervan uit dat het certificaat is ingetrokken en ongeldig is. (Dit is de standaardwaarde.)
* **alwaysCheck**: Controle voor intrekking van alle certificaten in de ketting. Als er geen intrekkingsinformatie aanwezig is in een certificaat, wordt aangenomen dat de intrekking ongeldig is.

Als u de intrekkingscontrole op een certificaat wilt uitvoeren, kunt u een URL naar een server met een certificaatintrekkingslijst (CRL) opgeven met behulp van een `CRLOptionSpec` -object. Als u echter een intrekkingscontrole wilt uitvoeren en u geen URL opgeeft naar een CRL-server, verkrijgt de ondertekeningsservice de URL van het certificaat.

In plaats van een CRL-server te gebruiken, kunt u een OCSP-server (online certificate Status Protocol) gebruiken bij het controleren van intrekkingen. Doorgaans wordt de intrekkingscontrole sneller uitgevoerd wanneer een OCSP-server wordt gebruikt in tegenstelling tot een CRL-server. (Zie &quot;Online Protocol van de Status van het Certificaat&quot;in [&#x200B; https://tools.ietf.org/html/rfc2560 &#x200B;](https://tools.ietf.org/html/rfc2560).)

U kunt de de serverorde plaatsen CRL en OCSP die de dienst van de Ondertekening gebruikend de Toepassingen en de Diensten van de Adobe gebruikt. Bijvoorbeeld, als de server OCSP eerst in de Toepassingen en de Diensten van de Adobe wordt geplaatst, dan wordt de server OCSP gecontroleerd, die door de server CRL wordt gevolgd. (Zie &quot;Certificaten en gegevens beheren met Betrouwbaarheidsopslag&quot; in de Help van AAC).

Als u opgeeft dat u de intrekkingscontrole niet wilt uitvoeren, controleert de service Handtekening niet of het certificaat dat is gebruikt om een document te ondertekenen of te certificeren, is ingetrokken. Dat wil zeggen dat CRL- en OCSP-serverinformatie wordt genegeerd.

>[!NOTE]
>
>Hoewel een CRL of een OCSP-server in het certificaat kan worden opgegeven, kunt u de URL die in het certificaat is opgegeven, overschrijven met een `CRLOptionSpec` - en `OCSPOptionSpec` -object. Als u bijvoorbeeld de CRL-server wilt overschrijven, kunt u de methode `setLocalURI` van het object `CRLOptionSpec` aanroepen.

Tijdstempel verwijst naar het proces waarbij de tijd wordt bijgehouden waarop een ondertekend of gecertificeerd document is gewijzigd. Nadat een document is ondertekend, mag het niet meer worden gewijzigd, zelfs niet door de eigenaar van het document. Met tijdstempels kunt u de geldigheid van een ondertekend of gecertificeerd document afdwingen. U kunt opties voor tijdstempels instellen met een `TSPOptionSpec` -object. U kunt bijvoorbeeld de URL van een server met een tijdstempelprovider (TSP) opgeven.

>[!NOTE]
>
>Doorloop in de secties Java en webservice en de bijbehorende snelle start, wordt de intrekkingscontrole gebruikt. Omdat er geen CRL- of OCSP-serverinformatie is opgegeven, wordt de serverinformatie opgehaald uit het certificaat dat wordt gebruikt om het PDF-document digitaal te ondertekenen.

Als u een PDF-document wilt ondertekenen, kunt u de volledig gekwalificeerde naam opgeven van het handtekeningveld dat de digitale handtekening zal bevatten, zoals `form1[0].#subform[1].SignatureField3[3]` . Wanneer u een XFA-formulierveld gebruikt, kunt u ook de gedeeltelijke naam van het handtekeningveld gebruiken: `SignatureField3[3]` .

U moet ook verwijzen naar een beveiligingsreferentie om een PDF-document digitaal te ondertekenen. Als u naar een beveiligingsreferentie wilt verwijzen, geeft u een alias op. De alias is een verwijzing naar een werkelijke referentie die kan voorkomen in een PKCS#12-bestand (met de extensie .pfx) of een hardwarebeveiligingsmodule (HSM). Voor informatie over de veiligheidsreferentie, zie *het Installeren van en het Opstellen van de gids van AEM Forms* voor uw toepassingsserver.

**sparen het ondertekende document van PDF**

Nadat de handtekeningservice het PDF-document digitaal heeft ondertekend, kunt u het opslaan als een PDF-bestand zodat gebruikers het kunnen openen in Acrobat of Adobe Reader.

**zie ook**

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

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `SignatureServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Het PDF-document laten ondertekenen

   * Maak een `java.io.FileInputStream` -object dat het PDF-document vertegenwoordigt dat digitaal moet worden ondertekend met de constructor ervan en geef een tekenreekswaarde door die de locatie van het PDF-document aangeeft.
   * Maak een `com.adobe.idp.Document` -object door de constructor ervan te gebruiken en het `java.io.FileInputStream` -object door te geven.

1. Het PDF-document ondertekenen

   Onderteken het PDF-document door de methode `sign` van het `SignatureServiceClient` -object aan te roepen en de volgende waarden door te geven:

   * Een `com.adobe.idp.Document` -object dat staat voor het PDF-document dat moet worden ondertekend.
   * Een tekenreekswaarde die de naam vertegenwoordigt van het handtekeningveld dat de digitale handtekening zal bevatten.
   * Een `Credential` -object dat de referentie vertegenwoordigt die wordt gebruikt om het PDF-document digitaal te ondertekenen. Maak een `Credential` -object door de statische methode van het `Credential` object `getInstance` aan te roepen en een tekenreekswaarde door te geven die de aliaswaarde opgeeft die overeenkomt met de beveiligingsreferentie.
   * Een `HashAlgorithm` -object dat een statisch gegevenslid opgeeft dat het hash-algoritme vertegenwoordigt dat moet worden gebruikt om het PDF-document te digest. U kunt bijvoorbeeld `HashAlgorithm.SHA1` opgeven om het algoritme SHA1 te gebruiken.
   * Een tekenreekswaarde die de reden vertegenwoordigt waarom het PDF-document digitaal is ondertekend.
   * Een tekenreekswaarde die de contactgegevens van de ondertekenaar vertegenwoordigt.
   * Een `PDFSignatureAppearanceOptions` -object dat de weergave van de digitale handtekening bepaalt. U kunt dit object bijvoorbeeld gebruiken om een aangepast logo toe te voegen aan een digitale handtekening.
   * Een `java.lang.Boolean` -object dat aangeeft of een intrekkingscontrole moet worden uitgevoerd op het certificaat van de ondertekenaar.
   * Een `OCSPOptionSpec` -object dat voorkeuren voor ondersteuning van het online certificaatstatusprotocol (OCSP) opslaat. Als de intrekkingscontrole niet is uitgevoerd, wordt deze parameter niet gebruikt en kunt u `null` opgeven.
   * Een `CRLPreferences` -object dat voorkeuren voor certificaatintrekkingslijsten (CRL) opslaat. Als de intrekkingscontrole niet is uitgevoerd, wordt deze parameter niet gebruikt en kunt u `null` opgeven.
   * Een `TSPPreferences` -object dat voorkeuren voor ondersteuning van een tijdstempelprovider (TSP) opslaat. Deze parameter is optioneel en kan `null` zijn. Voor meer informatie, zie [&#x200B; AEM Forms API Verwijzing &#x200B;](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

   De methode `sign` retourneert een `com.adobe.idp.Document` -object dat het ondertekende PDF-document vertegenwoordigt.

1. Ondertekend PDF-document opslaan

   * Maak een `java.io.File` -object en controleer of de bestandsextensie .pdf is.
   * Roep de methode `copyToFile` van het object `com.adobe.idp.Document` aan en geef `java.io.File` door om de inhoud van het object `Document` naar het bestand te kopiëren. Gebruik het object `com.adobe.idp.Document` dat door de methode `sign` is geretourneerd.

**zie ook**

[PDF-documenten digitaal ondertekenen](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)

[Snel starten (SOAP modus): een PDF-document digitaal ondertekenen met de Java API](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-digitally-signing-a-pdf-document-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### PDF-documenten digitaal ondertekenen met de API voor webservices {#digitally-signing-pdf-documents-using-the-web-service-api}

U kunt als volgt een PDF-document digitaal ondertekenen met de handtekening-API (webservice):

1. Projectbestanden opnemen

   Creeer een Microsoft .NET project dat MTOM gebruikt. Gebruik de volgende WSDL-definitie: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1` .

   >[!NOTE]
   >
   >Vervang `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Een Signatures-client maken

   * Maak een `SignatureServiceClient` -object met de standaardconstructor.
   * Maak een `SignatureServiceClient.Endpoint.Address` -object met de `System.ServiceModel.EndpointAddress` -constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/SignatureService?WSDL` ). U hoeft het attribuut `lc_version` niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Maak een `System.ServiceModel.BasicHttpBinding` -object door de waarde van het `SignatureServiceClient.Endpoint.Binding` -veld op te halen. De geretourneerde waarde wordt gecast naar `BasicHttpBinding` .
   * Stel het veld `MessageEncoding` van het `System.ServiceModel.BasicHttpBinding` -object in op `WSMessageEncoding.Mtom` . Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld `SignatureServiceClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de bijbehorende wachtwoordwaarde toe aan het veld `SignatureServiceClient.ClientCredentials.UserName.Password` .
      * Wijs de constante waarde `HttpClientCredentialType.Basic` toe aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType` .
      * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` toe aan het veld `BasicHttpBindingSecurity.Security.Mode` .

1. Het PDF-document laten ondertekenen

   * Maak een `BLOB` -object met behulp van de constructor. Met het `BLOB` -object wordt een ondertekend PDF-document opgeslagen.
   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het te ondertekenen PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `Length` van het object `System.IO.FileStream` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het object `BLOB` door de eigenschap `MTOM` ervan toe te wijzen aan de inhoud van de bytearray.

1. Het PDF-document ondertekenen

   Onderteken het PDF-document door de methode `sign` van het `SignatureServiceClient` -object aan te roepen en de volgende waarden door te geven:

   * Een `BLOB` -object dat staat voor het PDF-document dat moet worden ondertekend.
   * Een tekenreekswaarde die de naam vertegenwoordigt van het handtekeningveld dat de digitale handtekening zal bevatten.
   * Een `Credential` -object dat de referentie vertegenwoordigt die wordt gebruikt om het PDF-document digitaal te ondertekenen. Maak een `Credential` -object met behulp van de constructor en geef de alias op door een waarde toe te wijzen aan de eigenschap `Credential` object `alias` .
   * Een `HashAlgorithm` -object dat een statisch gegevenslid opgeeft dat het hash-algoritme vertegenwoordigt dat moet worden gebruikt om het PDF-document te digest. U kunt bijvoorbeeld `HashAlgorithm.SHA1` opgeven om het algoritme SHA1 te gebruiken.
   * Een Booleaanse waarde die opgeeft of het hash-algoritme wordt gebruikt.
   * Een tekenreekswaarde die de reden vertegenwoordigt waarom het PDF-document digitaal is ondertekend.
   * Een tekenreekswaarde die de locatie van de ondertekenaar vertegenwoordigt.
   * Een tekenreekswaarde die de contactgegevens van de ondertekenaar vertegenwoordigt.
   * Een `PDFSignatureAppearanceOptions` -object dat de weergave van de digitale handtekening bepaalt. U kunt dit object bijvoorbeeld gebruiken om een aangepast logo toe te voegen aan een digitale handtekening.
   * Een `System.Boolean` -object dat aangeeft of een intrekkingscontrole moet worden uitgevoerd op het certificaat van de ondertekenaar. Als deze intrekkingscontrole is uitgevoerd, wordt deze ingesloten in de handtekening. De standaardwaarde is `false` .
   * Een `OCSPOptionSpec` -object dat voorkeuren voor ondersteuning van het online certificaatstatusprotocol (OCSP) opslaat. Als de intrekkingscontrole niet is uitgevoerd, wordt deze parameter niet gebruikt en kunt u `null` opgeven. Voor informatie over dit voorwerp, zie [&#x200B; AEM Forms API Verwijzing &#x200B;](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).
   * Een `CRLPreferences` -object dat voorkeuren voor certificaatintrekkingslijsten (CRL) opslaat. Als de intrekkingscontrole niet is uitgevoerd, wordt deze parameter niet gebruikt en kunt u `null` opgeven.
   * Een `TSPPreferences` -object dat voorkeuren voor ondersteuning van een tijdstempelprovider (TSP) opslaat. Deze parameter is optioneel en kan `null` zijn.

   De methode `sign` retourneert een `BLOB` -object dat het ondertekende PDF-document vertegenwoordigt.

1. Ondertekend PDF-document opslaan

   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die staat voor de bestandslocatie van het ondertekende PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud wordt opgeslagen van het `BLOB` -object dat door de methode `sign` is geretourneerd. Vul de bytearray met de waarde van het gegevenslid `MTOM` van het object `BLOB` .
   * Maak een `System.IO.BinaryWriter` -object door de constructor ervan aan te roepen en het `System.IO.FileStream` -object door te geven.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door de methode `Write` van het object `System.IO.BinaryWriter` aan te roepen en de bytearray door te geven.

**zie ook**

[PDF-documenten digitaal ondertekenen](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Interactieve Forms digitaal ondertekenen {#digitally-signing-interactive-forms}

U kunt een interactief formulier ondertekenen dat door de Forms-service wordt gemaakt. Neem bijvoorbeeld de volgende workflow:

* U voegt een op XFA gebaseerd PDF formulier dat is gemaakt met Designer samen en formuliergegevens in een XML-document met de Forms-service. Op de Forms-server wordt een interactief formulier weergegeven.
* U ondertekent het interactieve formulier met de API van de handtekeningenservice.

Het resultaat is een digitaal ondertekend interactief PDF-formulier. Wanneer u een PDF-formulier ondertekent dat is gebaseerd op een XFA-formulier, moet u ervoor zorgen dat u het PDF-bestand opslaat als een Adobe statisch PDF-formulier. Als u een PDF-formulier probeert te ondertekenen dat is opgeslagen als een Adobe dynamisch PDF-formulier, treedt een uitzondering op. Zorg ervoor dat het formulier een handtekeningveld bevat omdat u het formulier ondertekent dat door de Forms-service wordt geretourneerd.

>[!NOTE]
>
>Voordat u een interactief formulier digitaal kunt ondertekenen, moet u ervoor zorgen dat u het certificaat aan AEM Forms toevoegt. Een certificaat wordt toegevoegd gebruikend beleidsconsole of programmatically gebruikend de Manager API van het Vertrouwen. (Zie [&#x200B; het Invoeren Referenties door de Manager API van het Vertrouwen te gebruiken &#x200B;](/help/forms/developing/credentials.md#importing-credentials-by-using-the-trust-manager-api).)

Wanneer u de Forms Service API gebruikt, stelt u de runtime-optie `GenerateServerAppearance` in op `true` . Met deze uitvoeringsoptie blijft de weergave van het formulier dat op de server wordt gegenereerd geldig wanneer het in Acrobat of Adobe Reader wordt geopend. Het wordt aanbevolen deze uitvoeringsoptie in te stellen wanneer u een interactief formulier genereert ter ondertekening met de Forms API.

>[!NOTE]
>
>Voordat u interactieve Forms voor digitaal ondertekenen leest, is het raadzaam bekend te zijn met het ondertekenen van PDF-documenten. (Zie [&#x200B; digitaal het Ondertekenen van de Documenten van PDF &#x200B;](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents).)

### Overzicht van de stappen {#summary_of_steps-4}

Voer de volgende taken uit om een interactief formulier dat de Forms-service retourneert, digitaal te ondertekenen:

1. Inclusief projectbestanden.
1. Maak een Forms- en Signatures-client.
1. Vraag het interactieve formulier aan met de Forms-service.
1. Onderteken het interactieve formulier.
1. Sla het ondertekende PDF-document op als een PDF-bestand.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-forms-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

Voor informatie over de plaats van deze JAR dossiers, zie [&#x200B; Inclusief de bibliotheekdossiers van AEM Forms Java &#x200B;](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**creeer een Forms en de cliënt van Handtekeningen**

Omdat bij deze workflow zowel de Forms- als de Signature-services worden aangeroepen, kunt u zowel een Forms-serviceclient als een Signature Service-client maken.

**verkrijg de interactieve vorm gebruikend de dienst van Forms**

U kunt de Forms-service gebruiken om het interactieve PDF-formulier ter ondertekening te verkrijgen. Vanaf AEM Forms kunt u een `com.adobe.idp.Document` -object doorgeven aan de Forms-service die het formulier bevat dat moet worden gegenereerd. De naam van deze methode is `renderPDFForm2` . Deze methode retourneert een `com.adobe.idp.Document` -object dat het formulier bevat dat moet worden ondertekend. U kunt deze `com.adobe.idp.Document` -instantie doorgeven aan de service Handtekening.

Op dezelfde manier kunt u als u webservices gebruikt, de `BLOB` -instantie doorgeven die door de Forms-service wordt geretourneerd aan de service Handtekening.

>[!NOTE]
>
>De snelle start die wordt gekoppeld aan de sectie Digitaal ondertekenen van interactieve Forms roept de methode `renderPDFForm2` aan.

**teken de interactieve vorm**

Bij het ondertekenen van een PDF-document kunt u uitvoeringsopties instellen die door de handtekeningservice worden gebruikt. U kunt de volgende opties instellen:

* Weergaveopties
* Intrekkingscontrole
* Waarden voor tijdstempels

U stelt vormgevingsopties in met een `PDFSignatureAppearanceOptionSpec` -object. U kunt bijvoorbeeld de datum binnen een handtekening weergeven door de methode `setShowDate` van het object `PDFSignatureAppearanceOptionSpec` aan te roepen en door te geven `true` .

**sparen het ondertekende document van PDF**

Nadat de handtekeningservice het PDF-document digitaal heeft ondertekend, kunt u het opslaan als een PDF-bestand. Het PDF-bestand kan worden geopend in Acrobat of Adobe Reader.

**zie ook**

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

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `SignatureServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.
   * Maak een `FormsServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Het interactieve formulier ophalen met de Forms-service

   * Maak een `java.io.FileInputStream` -object dat staat voor het PDF-document dat aan de Forms-service moet worden doorgegeven met behulp van de constructor. Geef een tekenreekswaarde door die de locatie van het PDF-document aangeeft.
   * Maak een `com.adobe.idp.Document` -object door de constructor ervan te gebruiken en het `java.io.FileInputStream` -object door te geven.
   * Maak een `java.io.FileInputStream` -object dat staat voor het XML-document dat formuliergegevens bevat die met behulp van de constructor aan de Forms-service moeten worden doorgegeven. Geef een tekenreekswaarde door die de locatie van het XML-bestand aangeeft.
   * Maak een `com.adobe.idp.Document` -object door de constructor ervan te gebruiken en het `java.io.FileInputStream` -object door te geven.
   * Maak een `PDFFormRenderSpec` -object dat wordt gebruikt om uitvoeringsopties in te stellen. Roep de methode `setGenerateServerAppearance` van het object `PDFFormRenderSpec` aan en geef `true` door.
   * Roep de methode `renderPDFForm2` van het object `FormsServiceClient` aan en geef de volgende waarden door:

      * Een `com.adobe.idp.Document` -object dat het PDF-formulier bevat dat moet worden gegenereerd.
      * Een `com.adobe.idp.Document` -object dat gegevens bevat die met het formulier moeten worden samengevoegd.
      * Een `PDFFormRenderSpec` -object dat uitvoeringsopties opslaat.
      * Een `URLSpec` -object dat URI-waarden bevat die door de Forms-service worden vereist. U kunt `null` voor deze parameterwaarde specificeren.
      * Een `java.util.HashMap` -object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt `null` opgeven als u geen bestanden aan het formulier wilt koppelen.

     De methode `renderPDFForm2` retourneert een `FormsResult` -object dat een formuliergegevensstroom bevat

   * Haal het PDF-formulier op door de methode `getOutputContent` van het object `FormsResult` aan te roepen. Deze methode retourneert een `com.adobe.idp.Document` -object dat het interactieve formulier vertegenwoordigt.

1. Het interactieve formulier ondertekenen

   Onderteken het PDF-document door de methode `sign` van het `SignatureServiceClient` -object aan te roepen en de volgende waarden door te geven:

   * Een `com.adobe.idp.Document` -object dat staat voor het PDF-document dat moet worden ondertekend. Zorg ervoor dat dit object het `com.adobe.idp.Document` -object is dat is verkregen van de Forms-service.
   * Een tekenreekswaarde die de naam vertegenwoordigt van het handtekeningveld dat wordt ondertekend.
   * Een `Credential` -object dat de referentie vertegenwoordigt die wordt gebruikt om het PDF-document digitaal te ondertekenen. Maak een `Credential` -object door de statische methode `Credential` van het object `getInstance` aan te roepen. Geef een tekenreekswaarde door die de aliaswaarde opgeeft die overeenkomt met de beveiligingsreferentie.
   * Een `HashAlgorithm` -object dat een statisch gegevenslid opgeeft dat het hash-algoritme vertegenwoordigt dat moet worden gebruikt om het PDF-document te digest. U kunt bijvoorbeeld `HashAlgorithm.SHA1` opgeven om het algoritme SHA1 te gebruiken.
   * Een tekenreekswaarde die de reden vertegenwoordigt waarom het PDF-document digitaal is ondertekend.
   * Een tekenreekswaarde die de contactgegevens van de ondertekenaar vertegenwoordigt.
   * Een `PDFSignatureAppearanceOptions` -object dat de weergave van de digitale handtekening bepaalt. U kunt dit object bijvoorbeeld gebruiken om een aangepast logo toe te voegen aan een digitale handtekening.
   * Een `java.lang.Boolean` -object dat aangeeft of een intrekkingscontrole moet worden uitgevoerd op het certificaat van de ondertekenaar.
   * Een `OCSPPreferences` -object dat voorkeuren voor ondersteuning van het online certificaatstatusprotocol (OCSP) opslaat. Als de intrekkingscontrole niet is uitgevoerd, wordt deze parameter niet gebruikt en kunt u `null` opgeven.
   * Een `CRLPreferences` -object dat voorkeuren voor certificaatintrekkingslijsten (CRL) opslaat. Als de intrekkingscontrole niet is uitgevoerd, wordt deze parameter niet gebruikt en kunt u `null` opgeven.
   * Een `TSPPreferences` -object dat voorkeuren voor ondersteuning van een tijdstempelprovider (TSP) opslaat. Deze parameter is optioneel en kan `null` zijn.

   De methode `sign` retourneert een `com.adobe.idp.Document` -object dat het ondertekende PDF-document vertegenwoordigt.

1. Ondertekend PDF-document opslaan

   * Maak een `java.io.File` -object en controleer of de bestandsnaamextensie .pdf is.
   * Roep de methode `copyToFile` van het object `com.adobe.idp.Document` aan en geef `java.io.File` door om de inhoud van het object `Document` naar het bestand te kopiëren. Zorg ervoor dat u het object `com.adobe.idp.Document` gebruikt dat de methode `sign` heeft geretourneerd.

**zie ook**

[Interactieve Forms digitaal ondertekenen](digitally-signing-certifying-documents.md#digitally-signing-interactive-forms)

[Snel starten (SOAP modus): een PDF-document digitaal ondertekenen met de Java API](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-digitally-signing-a-pdf-document-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een interactief formulier digitaal ondertekenen met de webservice-API {#digitally-sign-an-interactive-form-using-the-web-service-api}

Een interactief formulier digitaal ondertekenen met de API voor Forms en handtekening (webservice):

1. Projectbestanden opnemen

   Creeer een Microsoft .NET project dat MTOM gebruikt. Omdat deze cliënttoepassing de twee diensten van AEM Forms aanhaalt, creeer twee de dienstverwijzingen. Gebruik de volgende WSDL-definitie voor de serviceverwijzing die is gekoppeld aan de service Handtekening: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1` .

   Gebruik de volgende WSDL-definitie voor de serviceverwijzing die aan de Forms-service is gekoppeld: `http://localhost:8080/soap/services/FormsService?WSDL&lc_version=9.0.1` .

   Omdat het gegevenstype `BLOB` veel wordt gebruikt voor beide serviceverwijzingen, kunt u het gegevenstype van `BLOB` volledig kwalificeren wanneer u het gebruikt. In de bijbehorende webservice quick start zijn alle `BLOB` -instanties volledig gekwalificeerd.

   >[!NOTE]
   >
   >Vervang `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Een Forms- en Signatures-client maken

   * Maak een `SignatureServiceClient` -object met de standaardconstructor.
   * Maak een `SignatureServiceClient.Endpoint.Address` -object met de `System.ServiceModel.EndpointAddress` -constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/SignatureService?WSDL` ). U hoeft het attribuut `lc_version` niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Maak een `System.ServiceModel.BasicHttpBinding` -object door de waarde van het `SignatureServiceClient.Endpoint.Binding` -veld op te halen. De geretourneerde waarde wordt gecast naar `BasicHttpBinding` .
   * Stel het veld `MessageEncoding` van het `System.ServiceModel.BasicHttpBinding` -object in op `WSMessageEncoding.Mtom` . Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld `SignatureServiceClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de bijbehorende wachtwoordwaarde toe aan het veld `SignatureServiceClient.ClientCredentials.UserName.Password` .
      * Wijs de constante waarde `HttpClientCredentialType.Basic` toe aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType` .

   * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` toe aan het veld `BasicHttpBindingSecurity.Security.Mode` .

   >[!NOTE]
   >
   >Herhaal deze stappen voor de Forms service client.

1. Het interactieve formulier ophalen met de Forms-service

   * Maak een `BLOB` -object met behulp van de constructor. Met het `BLOB` -object wordt een ondertekend PDF-document opgeslagen.
   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het te ondertekenen PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `Length` van het object `System.IO.FileStream` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het object `BLOB` door de eigenschap `MTOM` ervan toe te wijzen aan de inhoud van de bytearray.
   * Maak een `BLOB` -object met behulp van de constructor. Het `BLOB` -object wordt gebruikt om formuliergegevens op te slaan.
   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het XML-bestand dat formuliergegevens bevat, en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `Length` van het object `System.IO.FileStream` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het object `BLOB` door de eigenschap `MTOM` ervan toe te wijzen aan de inhoud van de bytearray.
   * Maak een `PDFFormRenderSpec` -object dat wordt gebruikt om uitvoeringsopties in te stellen. Wijs de waarde `true` toe aan het veld `PDFFormRenderSpec` object `generateServerAppearance` .
   * Roep de methode `renderPDFForm2` van het object `FormsServiceClient` aan en geef de volgende waarden door:

      * Een `BLOB` -object dat het PDF-formulier bevat dat moet worden gegenereerd.
      * Een `BLOB` -object dat gegevens bevat die met het formulier moeten worden samengevoegd.
      * Een `PDFFormRenderSpec` -object dat uitvoeringsopties opslaat.
      * Een `URLSpec` -object dat URI-waarden bevat die door de Forms-service worden vereist. U kunt `null` voor deze parameterwaarde specificeren.
      * Een `java.util.HashMap` -object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt `null` opgeven als u geen bestanden aan het formulier wilt koppelen.
      * Een lange uitvoerparameter die wordt gebruikt om het aantal pagina&#39;s in het formulier op te slaan.
      * Een tekenreeks-uitvoerparameter die wordt gebruikt voor de landinstellingswaarde.
      * Een `FormResult` -waarde die een uitvoerparameter is die wordt gebruikt om het interactieve formulier op te slaan.

   * Haal het PDF-formulier op door het veld `outputContent` van het `FormsResult` -object op te halen. In dit veld wordt een `BLOB` -object opgeslagen dat het interactieve formulier vertegenwoordigt.

1. Het interactieve formulier ondertekenen

   Onderteken het PDF-document door de methode `sign` van het `SignatureServiceClient` -object aan te roepen en de volgende waarden door te geven:

   * Een `BLOB` -object dat staat voor het PDF-document dat moet worden ondertekend. Gebruik de `BLOB` -instantie die door de Forms-service wordt geretourneerd.
   * Een tekenreekswaarde die de naam vertegenwoordigt van het handtekeningveld dat wordt ondertekend.
   * Een `Credential` -object dat de referentie vertegenwoordigt die wordt gebruikt om het PDF-document digitaal te ondertekenen. Maak een `Credential` -object met behulp van de constructor en geef de alias op door een waarde toe te wijzen aan de eigenschap `Credential` object `alias` .
   * Een `HashAlgorithm` -object dat een statisch gegevenslid opgeeft dat het hash-algoritme vertegenwoordigt dat moet worden gebruikt om het PDF-document te digest. U kunt bijvoorbeeld `HashAlgorithm.SHA1` opgeven om het algoritme SHA1 te gebruiken.
   * Een Booleaanse waarde die opgeeft of het hash-algoritme wordt gebruikt.
   * Een tekenreekswaarde die de reden vertegenwoordigt waarom het PDF-document digitaal is ondertekend.
   * Een tekenreekswaarde die de locatie van de ondertekenaar vertegenwoordigt.
   * Een tekenreekswaarde die de contactgegevens van de ondertekenaar vertegenwoordigt.
   * Een `PDFSignatureAppearanceOptions` -object dat de weergave van de digitale handtekening bepaalt. U kunt dit object bijvoorbeeld gebruiken om een aangepast logo toe te voegen aan een digitale handtekening.
   * Een `System.Boolean` -object dat aangeeft of een intrekkingscontrole moet worden uitgevoerd op het certificaat van de ondertekenaar. Als deze intrekkingscontrole is uitgevoerd, wordt deze ingesloten in de handtekening. De standaardwaarde is `false` .
   * Een `OCSPPreferences` -object dat voorkeuren voor ondersteuning van het online certificaatstatusprotocol (OCSP) opslaat. Als de intrekkingscontrole niet is uitgevoerd, wordt deze parameter niet gebruikt en kunt u `null` opgeven. Voor informatie over dit voorwerp, zie [&#x200B; AEM Forms API Verwijzing &#x200B;](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).
   * Een `CRLPreferences` -object dat voorkeuren voor certificaatintrekkingslijsten (CRL) opslaat. Als de intrekkingscontrole niet is uitgevoerd, wordt deze parameter niet gebruikt en kunt u `null` opgeven.
   * Een `TSPPreferences` -object dat voorkeuren voor ondersteuning van een tijdstempelprovider (TSP) opslaat. Deze parameter is optioneel en kan `null` zijn.

   De methode `sign` retourneert een `BLOB` -object dat het ondertekende PDF-document vertegenwoordigt.

1. Ondertekend PDF-document opslaan

   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die staat voor de bestandslocatie van het ondertekende PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud wordt opgeslagen van het `BLOB` -object dat door de methode `sign` is geretourneerd. Vul de bytearray met de waarde van het gegevenslid `MTOM` van het object `BLOB` .
   * Maak een `System.IO.BinaryWriter` -object door de constructor ervan aan te roepen en het `System.IO.FileStream` -object door te geven.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door de methode `Write` van het object `System.IO.BinaryWriter` aan te roepen en de bytearray door te geven.

**zie ook**

[Interactieve Forms digitaal ondertekenen](digitally-signing-certifying-documents.md#digitally-signing-interactive-forms)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## PDF-documenten certificeren {#certifying-pdf-documents}

U kunt een PDF-document beveiligen door het te certificeren met een bepaald type handtekening, een zogenaamde gecertificeerde handtekening. Een gecertificeerde handtekening wordt op de volgende manieren onderscheiden van een digitale handtekening:

* Dit moet de eerste handtekening zijn die op het PDF-document wordt toegepast. Dit betekent dat op het moment dat de gecertificeerde handtekening wordt toegepast, alle andere handtekeningvelden in het document niet-ondertekend moeten zijn. Er is slechts één gecertificeerde handtekening toegestaan in een PDF-document. Als u een PDF-document wilt ondertekenen en certificeren, moet u het certificeren voordat u het ondertekent. Nadat u een PDF-document hebt gecertificeerd, kunt u digitale extra handtekeningvelden ondertekenen.
* De auteur of maker van het document kan opgeven dat het document op bepaalde manieren kan worden gewijzigd zonder de gecertificeerde handtekening ongeldig te maken. Het document kan bijvoorbeeld het invullen van formulieren of het plaatsen van opmerkingen toestaan. Als de auteur aangeeft dat een bepaalde wijziging niet is toegestaan, beperkt Acrobat gebruikers het document op die manier te wijzigen. Als dergelijke wijzigingen worden aangebracht, bijvoorbeeld door een andere toepassing te gebruiken, is de gecertificeerde handtekening ongeldig en geeft Acrobat een waarschuwing wanneer een gebruiker het document opent. (Bij niet-gecertificeerde handtekeningen zijn wijzigingen niet mogelijk en maken normale bewerkingsbewerkingen de oorspronkelijke handtekening niet ongeldig.)
* Op het moment van ondertekening wordt het document gescand op specifieke typen inhoud die de inhoud van een document dubbelzinnig of misleidend kunnen maken. Een annotatie kan bijvoorbeeld bepaalde tekst op een pagina verbergen die belangrijk is voor het begrijpen van wat wordt gecertificeerd. Over deze inhoud kan een toelichting (wettelijke verklaring) worden gegeven.

U kunt PDF-documenten programmatisch certificeren met de Java API voor de handtekeningenservice of de API voor de handtekeningwebservice. Wanneer u een PDF-document certificeert, moet u verwijzen naar een beveiligingsreferentie in de Credential-service. Voor informatie over de veiligheidsreferentie, zie *het Installeren van en het Opstellen van de gids van AEM Forms* voor uw toepassingsserver.

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
>Voor meer informatie over de dienst van de Handtekening en het certificeren van een document, zie [&#x200B; Verwijzing van de Diensten voor AEM Forms &#x200B;](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-5}

Voer de volgende taken uit om een PDF-document te certificeren:

1. Inclusief projectbestanden.
1. Maak een handtekeningclient.
1. Laat het PDF-document certificeren.
1. Certificeer het PDF-document.
1. Sla het gecertificeerde PDF-document op als een PDF-bestand.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

Voor informatie over de plaats van deze JAR dossiers, zie [&#x200B; Inclusief de bibliotheekdossiers van AEM Forms Java &#x200B;](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**creeer een cliënt van de Handtekening**

Voordat u een handtekeningbewerking programmatisch kunt uitvoeren, moet u een handtekeningclient maken.

**krijg het document van de PDF om te verklaren**

Als u een PDF-document wilt certificeren, moet u een PDF-document verkrijgen dat een handtekeningveld bevat. Als een PDF-document geen handtekeningveld bevat, kan het niet worden gecertificeerd. Een handtekeningveld kan worden toegevoegd met Designer of via programmacode. Voor informatie over programmatically het toevoegen van een handtekeningsgebied, zie [&#x200B; Toevoegend de Gebieden van de Handtekening &#x200B;](digitally-signing-certifying-documents.md#adding-signature-fields).

**certificeer het document van de PDF**

Als u een PDF-document wilt certificeren, hebt u de volgende invoerwaarden nodig die door de service Handtekening worden gebruikt voor de certificering van een PDF-document:

* **PDF document**: Een document van de PDF dat een handtekeningsgebied bevat, dat een vormgebied is dat een grafische vertegenwoordiging van de verklaarde handtekening bevat. Een PDF-document moet een handtekeningveld bevatten voordat het kan worden gecertificeerd. Een handtekeningveld kan worden toegevoegd met Designer of via programmacode. (Zie [&#x200B; Toevoegend de Gebieden van de Handtekening &#x200B;](digitally-signing-certifying-documents.md#adding-signature-fields).)
* **het gebiedsnaam van de Handtekening**: Volledig - gekwalificeerde naam van het handtekeningsgebied dat wordt verklaard. De volgende waarde is een voorbeeld: `form1[0].#subform[1].SignatureField3[3]` . Wanneer u een XFA-formulierveld gebruikt, kunt u ook de gedeeltelijke naam van het handtekeningveld gebruiken: `SignatureField3[3]` . Als een null-waarde wordt doorgegeven voor de veldnaam, wordt dynamisch een onzichtbaar handtekeningveld gemaakt en gecertificeerd.
* **de referentie van de Veiligheid**: Een referentie die wordt gebruikt om het document van de PDF te certificeren. Deze veiligheidsreferentie bevat een wachtwoord en een alias, die een alias moeten aanpassen die in de referentie verschijnt die binnen de Credential dienst wordt gevestigd. De alias is een verwijzing naar een werkelijke referentie die kan voorkomen in een PKCS#12-bestand (met de extensie .pfx) of een hardwarebeveiligingsmodule (HSM).
* **algoritme van de Hash**: Een knoeiboelalgoritme om het document van de PDF te gebruiken te mengen.
* **Reden voor het ondertekenen**: Een waarde die in Acrobat of Adobe Reader wordt getoond zodat andere gebruikers de reden kennen waarom het document van de PDF werd verklaard.
* **Plaats van de ondertekenaar**: De plaats van de ondertekenaar die door de referentie wordt gespecificeerd.
* **de informatie van het Contact**: De informatie van het contact, zoals adres en telefoonnummer, van de ondertekenaar.
* **informatie van de Toestemming**: Toestemmingen die de acties controleren die een eindgebruiker op een document kan uitvoeren zonder de verklaarde handtekening te veroorzaken ongeldig te zijn. U kunt bijvoorbeeld de machtiging zo instellen dat elke wijziging in het PDF-document ertoe leidt dat de gecertificeerde handtekening ongeldig wordt.
* **wettelijke verklaring**: Wanneer een document wordt verklaard, wordt het automatisch gescand voor specifieke soorten inhoud die de inhoud van een document ambigu of misleidend zouden kunnen maken. Een annotatie kan bijvoorbeeld bepaalde tekst op een pagina verbergen die belangrijk is voor het begrijpen van wat wordt gecertificeerd. Tijdens het scanproces worden waarschuwingen over dit type inhoud gegenereerd. Deze waarde biedt een aanvullende uitleg van de inhoud die waarschuwingen heeft gegenereerd.
* **de opties van de Vormgeving**: Opties die de verschijning van de verklaarde handtekening controleren. De gecertificeerde handtekening kan bijvoorbeeld datumgegevens weergeven.
* **Revocation het controleren**: Deze waarde specificeert of de herroeping het controleren voor het certificaat van de ondertekenaar wordt gedaan. De standaardinstelling van `false` betekent dat de intrekkingscontrole niet is uitgevoerd.
* **OCSP montages**: Montages voor Online steun van de Status van het Certificaat van het Protocol (OCSP), die informatie over de status van de referentie verstrekt die wordt gebruikt om het document van de PDF te certificeren. U kunt bijvoorbeeld de URL van de server opgeven die informatie bevat over de referentie die u gebruikt om u aan te melden bij het PDF-document.
* **montages CRL**: Montages voor de voorkeur van de certificaatintrekkingslijst (CRL) als de herroepingscontrole wordt gedaan. U kunt bijvoorbeeld opgeven om altijd te controleren of een referentie is ingetrokken.
* **Tijd het stempelen**: Montages die tijd het stempelen informatie bepalen die op de verklaarde handtekening wordt toegepast. Een tijdstempel geeft aan dat specifieke gegevens voor een bepaald tijdstip zijn vastgesteld. Deze kennis draagt bij tot het opbouwen van een vertrouwensrelatie tussen de ondertekenaar en de verificateur.

**sparen het verklaarde document van PDF als dossier van PDF**

Nadat de handtekeningservice het PDF-document heeft gecertificeerd, kunt u het opslaan als een PDF-bestand zodat gebruikers het kunnen openen in Acrobat of Adobe Reader.

**zie ook**

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

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `SignatureServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Laat het PDF-document certificeren

   * Maak een `java.io.FileInputStream` -object dat staat voor het PDF-document dat moet worden gecertificeerd met de constructor ervan en geef een tekenreekswaarde door die de locatie van het PDF-document aangeeft.
   * Maak een `com.adobe.idp.Document` -object door de constructor ervan te gebruiken en het `java.io.FileInputStream` -object door te geven.

1. Het PDF-document certificeren

   Certificeer het PDF-document door de methode `certify` van het `SignatureServiceClient` -object aan te roepen en de volgende waarden door te geven:

   * Het `com.adobe.idp.Document` -object dat het te certificeren PDF-document vertegenwoordigt.
   * Een tekenreekswaarde die de naam vertegenwoordigt van het handtekeningveld dat de handtekening zal bevatten.
   * Een `Credential` -object dat de referentie vertegenwoordigt die wordt gebruikt om het PDF-document te certificeren. Maak een `Credential` -object door de statische methode van het `Credential` object `getInstance` aan te roepen en een tekenreekswaarde door te geven die de aliaswaarde opgeeft die overeenkomt met de beveiligingsreferentie.
   * Een `HashAlgorithm` -object dat een statisch gegevenslid opgeeft dat het hash-algoritme vertegenwoordigt dat wordt gebruikt om het PDF-document te digest. U kunt bijvoorbeeld `HashAlgorithm.SHA1` opgeven om het algoritme SHA1 te gebruiken.
   * Een tekenreekswaarde die de reden vertegenwoordigt waarom het PDF-document is gecertificeerd.
   * Een tekenreekswaarde die de contactgegevens van de ondertekenaar vertegenwoordigt.
   * Een `MDPPermissions` -object dat handelingen opgeeft die kunnen worden uitgevoerd op het PDF-document dat de handtekening ongeldig maakt.
   * Een `PDFSignatureAppearanceOptions` -object dat de weergave van de gecertificeerde handtekening bepaalt. Wijzig desgewenst de weergave van de handtekening door een methode aan te roepen, zoals `setShowDate` .
   * Een tekenreekswaarde die een uitleg geeft van welke handelingen de handtekening ongeldig maken.
   * Een `java.lang.Boolean` -object dat aangeeft of een intrekkingscontrole moet worden uitgevoerd op het certificaat van de ondertekenaar. Als deze intrekkingscontrole is uitgevoerd, wordt deze ingesloten in de handtekening. De standaardwaarde is `false` .
   * Een `java.lang.Boolean` -object dat opgeeft of het handtekeningveld dat wordt gecertificeerd, is vergrendeld. Als het veld is vergrendeld, wordt het handtekeningveld gemarkeerd als alleen-lezen, kunnen de eigenschappen ervan niet worden gewijzigd en kan het niet worden gewist door iedereen die niet de vereiste machtigingen heeft. De standaardwaarde is `false` .
   * Een `OCSPPreferences` -object dat voorkeuren voor ondersteuning van het online certificaatstatusprotocol (OCSP) opslaat. Als de intrekkingscontrole niet is uitgevoerd, wordt deze parameter niet gebruikt en kunt u `null` opgeven. Voor informatie over dit voorwerp, zie [&#x200B; AEM Forms API Verwijzing &#x200B;](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).
   * Een `CRLPreferences` -object dat voorkeuren voor certificaatintrekkingslijsten (CRL) opslaat. Als de intrekkingscontrole niet is uitgevoerd, wordt deze parameter niet gebruikt en kunt u `null` opgeven.
   * Een `TSPPreferences` -object dat voorkeuren voor ondersteuning van een tijdstempelprovider (TSP) opslaat. Nadat u bijvoorbeeld een `TSPPreferences` -object hebt gemaakt, kunt u de URL van de TSP-server instellen door de methode `TSPPreferences` object `setTspServerURL` aan te roepen. Deze parameter is optioneel en kan `null` zijn. Voor meer informatie, zie [&#x200B; Verwijzing van de Diensten voor AEM Forms &#x200B;](https://www.adobe.com/go/learn_aemforms_services_63).

   De methode `certify` retourneert een `com.adobe.idp.Document` -object dat het gecertificeerde PDF-document vertegenwoordigt.

1. Het gecertificeerde PDF-document opslaan als een PDF-bestand

   * Maak een `java.io.File` -object en controleer of de bestandsextensie .pdf is.
   * Roep de methode `copyToFile` van het object `com.adobe.idp.Document` aan om de inhoud van het object `com.adobe.idp.Document` naar het bestand te kopiëren.

**zie ook**

[PDF-documenten certificeren](digitally-signing-certifying-documents.md#certifying-pdf-documents)

[Snel starten (SOAP modus): Een PDF-document certificeren met de Java API](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-certifying-a-pdf-document-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### PDF-documenten certificeren met de webservice-API {#certify-pdf-documents-using-the-web-service-api}

Certificeer een PDF-document met de handtekening-API (webservice):

1. Projectbestanden opnemen

   Creeer een Microsoft .NET project dat MTOM gebruikt. Gebruik de volgende WSDL-definitie: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1` .

   >[!NOTE]
   >
   >Vervang `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Een handtekeningclient maken

   * Maak een `SignatureServiceClient` -object met de standaardconstructor.
   * Maak een `SignatureServiceClient.Endpoint.Address` -object met de `System.ServiceModel.EndpointAddress` -constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/SignatureService?WSDL` ). U hoeft het attribuut `lc_version` niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Maak een `System.ServiceModel.BasicHttpBinding` -object door de waarde van het `SignatureServiceClient.Endpoint.Binding` -veld op te halen. De geretourneerde waarde wordt gecast naar `BasicHttpBinding` .
   * Stel het veld `MessageEncoding` van het `System.ServiceModel.BasicHttpBinding` -object in op `WSMessageEncoding.Mtom` . Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld `SignatureServiceClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de bijbehorende wachtwoordwaarde toe aan het veld `SignatureServiceClient.ClientCredentials.UserName.Password` .
      * Wijs de constante waarde `HttpClientCredentialType.Basic` toe aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType` .
      * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` toe aan het veld `BasicHttpBindingSecurity.Security.Mode` .

1. Laat het PDF-document certificeren

   * Maak een `BLOB` -object met behulp van de constructor. Met het `BLOB` -object wordt een gecertificeerd PDF-document opgeslagen.
   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het te certificeren PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `Length` van het object `System.IO.FileStream` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` -object door het `MTOM` -gegevenslid ervan toe te wijzen aan de inhoud van de bytearray.

1. Het PDF-document certificeren

   Certificeer het PDF-document door de methode `certify` van het `SignatureServiceClient` -object aan te roepen en de volgende waarden door te geven:

   * Het `BLOB` -object dat het te certificeren PDF-document vertegenwoordigt.
   * Een tekenreekswaarde die de naam vertegenwoordigt van het handtekeningveld dat de handtekening zal bevatten.
   * Een `Credential` -object dat de referentie vertegenwoordigt die wordt gebruikt om het PDF-document te certificeren. Maak een `Credential` -object met behulp van de constructor en geef de alias op door een waarde toe te wijzen aan de eigenschap `Credential` object `alias` .
   * Een `HashAlgorithm` -object dat een statisch gegevenslid opgeeft dat het hash-algoritme vertegenwoordigt dat wordt gebruikt om het PDF-document te digest. U kunt bijvoorbeeld `HashAlgorithm.SHA1` opgeven om het algoritme SHA1 te gebruiken.
   * Een Booleaanse waarde die opgeeft of het hash-algoritme wordt gebruikt.
   * Een tekenreekswaarde die de reden vertegenwoordigt waarom het PDF-document is gecertificeerd.
   * Een tekenreekswaarde die de locatie van de ondertekenaar vertegenwoordigt.
   * Een tekenreekswaarde die de contactgegevens van de ondertekenaar vertegenwoordigt.
   * Een `MDPPermissions` -objectlid met statische gegevens dat handelingen opgeeft die kunnen worden uitgevoerd op het PDF-document waardoor de handtekening ongeldig wordt gemaakt.
   * Een Booleaanse waarde die opgeeft of het object `MDPPermissions` moet worden gebruikt dat als de vorige parameterwaarde is doorgegeven.
   * Een tekenreekswaarde die aangeeft welke handelingen de handtekening ongeldig maken.
   * Een `PDFSignatureAppearanceOptions` -object dat de weergave van de gecertificeerde handtekening bepaalt. Maak een `PDFSignatureAppearanceOptions` -object met behulp van de constructor. U kunt de weergave van de handtekening wijzigen door een van de gegevensleden in te stellen.
   * Een `System.Boolean` -object dat aangeeft of een intrekkingscontrole moet worden uitgevoerd op het certificaat van de ondertekenaar. Als deze intrekkingscontrole is uitgevoerd, wordt deze ingesloten in de handtekening. De standaardwaarde is `false` .
   * Een `System.Boolean` -object dat opgeeft of het handtekeningveld dat wordt gecertificeerd, is vergrendeld. Als het veld is vergrendeld, wordt het handtekeningveld gemarkeerd als alleen-lezen, kunnen de eigenschappen ervan niet worden gewijzigd en kan het niet worden gewist door iedereen die niet de vereiste machtigingen heeft. De standaardwaarde is `false` .
   * Een `System.Boolean` -object dat opgeeft of het handtekeningveld is vergrendeld. Wanneer u `true` doorgeeft aan de vorige parameter, geeft u `true` door aan deze parameter.
   * Een `OCSPPreferences` -object dat voorkeuren voor ondersteuning van het online certificaatstatusprotocol (OCSP) opslaat. Hiermee wordt informatie gegeven over de status van de referentie die wordt gebruikt om het PDF-document te certificeren. Als de intrekkingscontrole niet is uitgevoerd, wordt deze parameter niet gebruikt en kunt u `null` opgeven.
   * Een `CRLPreferences` -object dat voorkeuren voor certificaatintrekkingslijsten (CRL) opslaat. Als de intrekkingscontrole niet is uitgevoerd, wordt deze parameter niet gebruikt en kunt u `null` opgeven.
   * Een `TSPPreferences` -object dat voorkeuren voor ondersteuning van een tijdstempelprovider (TSP) opslaat. Nadat u bijvoorbeeld een `TSPPreferences` -object hebt gemaakt, kunt u de URL van de TSP instellen door het gegevenslid van het `TSPPreferences` object `tspServerURL` in te stellen. Deze parameter is optioneel en kan `null` zijn.

   De methode `certify` retourneert een `BLOB` -object dat het gecertificeerde PDF-document vertegenwoordigt.

1. Het gecertificeerde PDF-document opslaan als een PDF-bestand

   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het PDF-document dat het gecertificeerde PDF-document zal bevatten en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud wordt opgeslagen van het `BLOB` -object dat door de methode `certify` is geretourneerd. Vul de bytearray met de waarde van het gegevenslid `binaryData` van het object `BLOB` .
   * Maak een `System.IO.BinaryWriter` -object door de constructor ervan aan te roepen en het `System.IO.FileStream` -object door te geven.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door de methode `Write` van het object `System.IO.BinaryWriter` aan te roepen en de bytearray door te geven.

**zie ook**

[PDF-documenten certificeren](digitally-signing-certifying-documents.md#certifying-pdf-documents)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Digitale handtekeningen verifiëren {#verifying-digital-signatures}

Digitale handtekeningen kunnen worden geverifieerd om ervoor te zorgen dat een ondertekend PDF-document niet is gewijzigd en dat de digitale handtekening geldig is. Wanneer u een digitale handtekening verifieert, kunt u de status van de handtekening en de eigenschappen van de handtekening controleren, zoals de identiteit van de ondertekenaar. Voordat u een digitale handtekening vertrouwt, is het raadzaam deze te controleren. Wanneer u een digitale handtekening verifieert, verwijst u naar een PDF-document dat een digitale handtekening bevat.

Stel dat de identiteit van de ondertekenaar onbekend is. Wanneer u het PDF-document opent in Acrobat, wordt in een waarschuwingsbericht aangegeven dat de identiteit van de ondertekenaar onbekend is, zoals in de volgende afbeelding wordt getoond.

![&#x200B; vd_vd_verivrog &#x200B;](assets/vd_vd_verifysig.png)

Op dezelfde manier kunt u, wanneer u programmatisch een digitale handtekening verifieert, de status van de identiteit van de ondertekenaar bepalen. Als u bijvoorbeeld de digitale handtekening verifieert in het document dat in de vorige illustratie wordt weergegeven, resulteert dit in het feit dat de identiteit van de ondertekenaar onbekend is.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Handtekening en het verifiëren van digitale handtekeningen, zie [&#x200B; Verwijzing van de Diensten voor AEM Forms &#x200B;](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-6}

Voer de volgende taken uit om een digitale handtekening te verifiëren:

1. Inclusief projectbestanden.
1. Maak een handtekeningclient.
1. Hiermee wordt het PDF-document opgehaald dat de te verifiëren handtekening bevat.
1. Stel PKI-runtime-opties in.
1. Controleer de digitale handtekening.
1. Bepaal de status van de handtekening.
1. Bepaal de identiteit van de ondertekenaar.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, neemt u de proxybestanden op.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

Voor informatie over de plaats van deze JAR dossiers, zie [&#x200B; Inclusief de bibliotheekdossiers van AEM Forms Java &#x200B;](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**creeer een cliënt van de Handtekening**

Voordat u via programmacode een bewerking in de handtekeningenservice uitvoert, moet u een client voor de handtekeningenservice maken.

**krijgt het document van de PDF dat de te verifiëren handtekening bevat**

Als u een PDF-document digitaal wilt ondertekenen of certificeren met een handtekening, vraagt u een PDF-document op dat een handtekening bevat.

**vastgestelde PKI runtime opties**

Stel de volgende PKI-runtimeopties in die de handtekeningservice gebruikt bij het controleren van handtekeningen in een PDF-document:

* Verificatietijd
* Intrekkingscontrole
* Waarden voor tijdstempels

Als onderdeel van het instellen van deze opties kunt u een verificatietijd opgeven. U kunt bijvoorbeeld de huidige tijd selecteren (de tijd op de computer van de validator), die aangeeft dat de huidige tijd moet worden gebruikt. Voor informatie over de verschillende tijdwaarden, zie de `VerificationTime` opsommingswaarde in [&#x200B; AEM Forms API Verwijzing &#x200B;](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

U kunt ook opgeven of de intrekkingscontrole moet worden uitgevoerd tijdens het verificatieproces. U kunt bijvoorbeeld een intrekkingscontrole uitvoeren om te bepalen of het certificaat wordt ingetrokken. Voor informatie over de herroeping-controlerende opties, zie de `RevocationCheckStyle` opsommingswaarde in [&#x200B; AEM Forms API Verwijzing &#x200B;](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

Als u intrekkingscontrole wilt uitvoeren op een certificaat, geeft u een URL op naar een server met een certificaatintrekkingslijst (CRL) met behulp van een `CRLOptionSpec` -object. Als u echter geen URL opgeeft naar de CRL-server, verkrijgt de handtekeningservice de URL van het certificaat.

In plaats van een CRL-server te gebruiken, kunt u een OCSP-server (online certificate Status Protocol) gebruiken bij het controleren van intrekkingen. Wanneer u een OCSP-server gebruikt in tegenstelling tot een CRL-server, wordt de intrekkingscontrole meestal sneller uitgevoerd. (Zie [&#x200B; Online Protocol van de Status van het Certificaat &#x200B;](https://tools.ietf.org/html/rfc2560).)

U kunt de de serverorde plaatsen CRL en OCSP die de dienst van de Ondertekening door de Toepassingen en de Diensten van de Adobe te gebruiken gebruikt. Bijvoorbeeld, als de server OCSP eerst in de Toepassingen en de Diensten van de Adobe wordt geplaatst, dan wordt de server OCSP gecontroleerd, die door de server CRL wordt gevolgd.

Als u de intrekkingscontrole niet uitvoert, controleert de service Handtekening niet of het certificaat is ingetrokken. Dat wil zeggen dat CRL- en OCSP-serverinformatie wordt genegeerd.

>[!NOTE]
>
>U kunt de URL die in het certificaat is opgegeven, overschrijven met een object `CRLOptionSpec` en `OCSPOptionSpec` . Als u bijvoorbeeld de CRL-server wilt overschrijven, kunt u de methode `setLocalURI` van het object `CRLOptionSpec` aanroepen.

Tijdstempel is het proces waarbij de tijd wordt bijgehouden waarop een ondertekend of gecertificeerd document is gewijzigd. Nadat een document is ondertekend, kan niemand het wijzigen. Met tijdstempels kunt u de geldigheid van een ondertekend of gecertificeerd document afdwingen. U kunt opties voor tijdstempels instellen met een `TSPOptionSpec` -object. U kunt bijvoorbeeld de URL van een server met een tijdstempelprovider (TSP) opgeven.

>[!NOTE]
>
>In Java en de webservice wordt snel gestart, wordt de verificatietijd ingesteld op `VerificationTime.CURRENT_TIME` en wordt de intrekkingscontrole ingesteld op `RevocationCheckStyle.BestEffort` . Omdat er geen CRL- of OCSP-serverinformatie is opgegeven, wordt de serverinformatie opgehaald uit het certificaat.

**verifieer de digitale handtekening**

Als u een handtekening wilt verifiëren, geeft u de volledig gekwalificeerde naam op van het handtekeningveld dat de handtekening bevat, bijvoorbeeld `form1[0].#subform[1].SignatureField3[3]` . Wanneer u een XFA-formulierveld gebruikt, kunt u ook de gedeeltelijke naam van het handtekeningveld gebruiken: `SignatureField3` .

De service Handtekening beperkt standaard de tijd die een document na de validatietijd kan worden ondertekend tot 65 minuten. Als een gebruiker probeert een handtekening op het huidige tijdstip te verifiëren en de ondertekeningstijd later is dan de huidige tijd en binnen 65 minuten, genereert de handtekeningservice geen verificatiefout.

>[!NOTE]
>
>Voor andere waarden die u wanneer het verifiëren van een handtekening vereist, zie [&#x200B; AEM Forms API Verwijzing &#x200B;](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**bepaal het statuut van de handtekening**

Als onderdeel van de verificatie van een digitale handtekening, kunt u de status van de handtekening controleren.

**bepaalt de identiteit van de ondertekenaar**

U kunt de identiteit van de ondertekenaar bepalen. Dit kan een van de volgende waarden zijn:

* **Onbekend**: Deze ondertekenaar is onbekend omdat de ondertekenaarverificatie niet kan worden uitgevoerd.
* **Vertrouwd**: Deze ondertekenaar wordt vertrouwd.
* **niet vertrouwd op**: Deze ondertekenaar wordt niet vertrouwd.

**zie ook**

[Digitale handtekeningen verifiëren met de Java API](#verify-digital-signatures-using-the-java-api)

[Digitale handtekeningen verifiëren met de webservice-API](#verify-digital-signatures-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Digitale handtekeningen verifiëren met de Java API {#verify-digital-signatures-using-the-java-api}

Verifieer een digitale handtekening met de API van de Handtekeningenservice (Java):

1. Projectbestanden opnemen

   Neem JAR-bestanden van de client, zoals adobe-signatures-client.jar, op in het klassepad van uw Java-project.

1. Een handtekeningclient maken

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `SignatureServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Hiermee wordt het PDF-document opgehaald dat de handtekening bevat die moet worden geverifieerd

   * Maak een `java.io.FileInputStream` -object dat staat voor het PDF-document dat de handtekening bevat die moet worden geverifieerd met behulp van de constructor ervan. Geef een tekenreekswaarde door die de locatie van het PDF-document aangeeft.
   * Maak een `com.adobe.idp.Document` -object door de constructor ervan te gebruiken en het `java.io.FileInputStream` -object door te geven.

1. PKI-runtime-opties instellen

   * Maak een `PKIOptions` -object met behulp van de constructor.
   * Stel de verificatietijd in door de methode `setVerificationTime` van het object `PKIOptions` aan te roepen en een opsommingswaarde `VerificationTime` door te geven die de verificatietijd opgeeft.
   * Stel de optie voor intrekkingscontrole in door de methode `setRevocationCheckStyle` van het object `PKIOptions` aan te roepen en een opsommingswaarde `RevocationCheckStyle` door te geven die aangeeft of een intrekkingscontrole moet worden uitgevoerd.

1. De digitale handtekening verifiëren

   Verifieer de handtekening door de methode `verify2` van het object `SignatureServiceClient` aan te roepen en de volgende waarden door te geven:

   * Een `com.adobe.idp.Document` -object dat een digitaal ondertekend of gecertificeerd PDF-document bevat.
   * Een tekenreekswaarde die staat voor de naam van het handtekeningveld dat de te controleren handtekening bevat.
   * Een `PKIOptions` -object dat PKI-runtime-opties bevat.
   * Een `VerifySPIOptions` -instantie die SPI-informatie bevat. U kunt `null` voor deze parameter opgeven.

   De methode `verify2` retourneert een `PDFSignatureVerificationInfo` -object dat informatie bevat die kan worden gebruikt om de digitale handtekening te verifiëren.

1. De status van de handtekening bepalen

   * Bepaal de status van de handtekening door de methode `getStatus` van het object `PDFSignatureVerificationInfo` aan te roepen. Deze methode retourneert een `SignatureStatus` -object dat de status van de handtekening opgeeft. Als een ondertekend PDF-document bijvoorbeeld niet wordt gewijzigd, retourneert deze methode `SignatureStatus.DocumentSigNoChanges` .

1. De identiteit van de ondertekenaar bepalen

   * Bepaal de identiteit van de ondertekenaar door de methode `getSigner` van het object `PDFSignatureVerificationInfo` aan te roepen. Deze methode retourneert een `IdentityInformation` -object.
   * Roep de methode `getStatus` van het `IdentityInformation` -object aan om de identiteit van de ondertekenaar te bepalen. Deze methode retourneert een opsommingswaarde `IdentityStatus` die de identiteit opgeeft. Als de ondertekenaar bijvoorbeeld wordt vertrouwd, retourneert deze methode `IdentityStatus.TRUSTED` .

**zie ook**

[Digitale handtekeningen verifiëren](#verify-digital-signatures-using-the-java-api)

[Snel starten (SOAP modus): een digitale handtekening controleren met de Java API](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-verifying-a-digital-signature-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Digitale handtekeningen verifiëren met de webservice-API {#verify-digital-signatures-using-the-web-service-api}

Verifieer een digitale handtekening met behulp van de Signature Service API (webservice):

1. Projectbestanden opnemen

   Creeer een Microsoft .NET project dat MTOM gebruikt. Gebruik de volgende WSDL-definitie: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1` .

   >[!NOTE]
   >
   >Vervang `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Een handtekeningclient maken

   * Maak een `SignatureServiceClient` -object met de standaardconstructor.
   * Maak een `SignatureServiceClient.Endpoint.Address` -object met de `System.ServiceModel.EndpointAddress` -constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/SignatureService?WSDL` ). U hoeft het attribuut `lc_version` niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Maak een `System.ServiceModel.BasicHttpBinding` -object door de waarde van het `SignatureServiceClient.Endpoint.Binding` -veld op te halen. De geretourneerde waarde wordt gecast naar `BasicHttpBinding` .
   * Stel het veld `MessageEncoding` van het `System.ServiceModel.BasicHttpBinding` -object in op `WSMessageEncoding.Mtom` . Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld `SignatureServiceClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de bijbehorende wachtwoordwaarde toe aan het veld `SignatureServiceClient.ClientCredentials.UserName.Password` .
      * Wijs de constante waarde `HttpClientCredentialType.Basic` toe aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType` .
      * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` toe aan het veld `BasicHttpBindingSecurity.Security.Mode` .

1. Hiermee wordt het PDF-document opgehaald dat de handtekening bevat die moet worden geverifieerd

   * Maak een `BLOB` -object met behulp van de constructor. Het `BLOB` -object wordt gebruikt om een PDF-document op te slaan dat een digitale of gecertificeerde handtekening bevat die moet worden geverifieerd.
   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die staat voor de bestandslocatie van het ondertekende PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `Length` van het object `System.IO.FileStream` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul het object `BLOB` door de eigenschap `MTOM` ervan toe te wijzen aan de inhoud van de bytearray.

1. PKI-runtime-opties instellen

   * Maak een `PKIOptions` -object met behulp van de constructor.
   * Stel de verificatietijd in door de opsommingswaarde `verificationTime` data member `VerificationTime` van het `PKIOptions` -object toe te wijzen die de verificatietijd opgeeft.
   * Stel de optie voor intrekkingscontrole in door de opsommingswaarde `revocationCheckStyle` data member `RevocationCheckStyle` van het `PKIOptions` -object toe te wijzen die aangeeft of een intrekkingscontrole moet worden uitgevoerd.

1. De digitale handtekening verifiëren

   Verifieer de handtekening door de methode `verify2` van het object `SignatureServiceClient` aan te roepen en de volgende waarden door te geven:

   * Het `BLOB` -object dat een digitaal ondertekend of gecertificeerd PDF-document bevat.
   * Een tekenreekswaarde die staat voor de naam van het handtekeningveld dat de te controleren handtekening bevat.
   * Een `PKIOptions` -object dat PKI-runtime-opties bevat.
   * Een `VerifySPIOptions` -instantie die SPI-informatie bevat. U kunt `null` voor deze parameter opgeven.

   De methode `verify2` retourneert een `PDFSignatureVerificationInfo` -object dat informatie bevat die kan worden gebruikt om de digitale handtekening te verifiëren.

1. De status van de handtekening bepalen

   Bepaal de status van de handtekening door de waarde van het gegevenslid `status` van het `PDFSignatureVerificationInfo` -object op te halen. Dit gegevenslid slaat een `SignatureStatus` -object op dat de status van de handtekening opgeeft. Als bijvoorbeeld een ondertekend PDF-document wordt gewijzigd, slaat het `status` -gegevenslid de waarde `SignatureStatus.DocumentSigNoChanges` op.

1. De identiteit van de ondertekenaar bepalen

   * Bepaal de identiteit van de ondertekenaar door de waarde van het gegevenslid `signer` van het `PDFSignatureVerificationInfo` -object op te halen. Dit lid retourneert een `IdentityInformation` -object.
   * Haal het gegevenslid `status` van het `IdentityInformation` -object op om de identiteit van de ondertekenaar te bepalen. Dit gegevenslid retourneert een `IdentityStatus` opsommingswaarde die de identiteit opgeeft. Als de ondertekenaar bijvoorbeeld wordt vertrouwd, retourneert dit lid `IdentityStatus.TRUSTED` .

**zie ook**

[Digitale handtekeningen verifiëren](#verify-digital-signatures-using-the-java-api)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Meerdere digitale handtekeningen controleren {#verifying-multiple-digital-signatures}

AEM Forms biedt de mogelijkheid om alle digitale handtekeningen in een PDF-document te verifiëren. Stel dat een PDF-document meerdere digitale handtekeningen bevat als resultaat van een bedrijfsproces waarvoor handtekeningen van meerdere ondertekenaars nodig zijn. Neem bijvoorbeeld een financiële transactie waarvoor zowel de handtekening van een medewerker als die van een manager is vereist. Met de Java API of de webservice-API van de handtekeningenservice kunt u alle handtekeningen in het PDF-document verifiëren. Wanneer u meerdere digitale handtekeningen controleert, kunt u de status en eigenschappen van elke handtekening controleren. Voordat u een digitale handtekening vertrouwt, is het raadzaam deze te verifiëren. U wordt aangeraden bekend te zijn met het controleren van één digitale handtekening.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Handtekening en het verifiëren van digitale handtekeningen, zie [&#x200B; Verwijzing van de Diensten voor AEM Forms &#x200B;](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-7}

Voer de volgende taken uit om meerdere digitale handtekeningen te verifiëren:

1. Inclusief projectbestanden.
1. Maak een handtekeningclient.
1. Hiermee wordt het PDF-document opgehaald dat de handtekeningen bevat die moeten worden geverifieerd.
1. Stel PKI-runtime-opties in.
1. Alle digitale handtekeningen ophalen.
1. Alle handtekeningen doorlopen.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, neemt u de proxybestanden op.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

Voor informatie over de plaats van deze JAR dossiers, zie [&#x200B; Inclusief de bibliotheekdossiers van AEM Forms Java &#x200B;](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**creeer een cliënt van de Handtekening**

Voordat u via programmacode een bewerking in de handtekeningenservice uitvoert, moet u een client voor de handtekeningenservice maken.

**krijgt het document van de PDF dat de handtekeningen bevat om te verifiëren**

Als u een PDF-document digitaal wilt ondertekenen of certificeren met een handtekening, vraagt u een PDF-document op dat een handtekening bevat.

**Vastgestelde PKI runtime opties**

Stel de volgende PKI-runtimeopties in die de handtekeningservice gebruikt bij het controleren van alle handtekeningen in een PDF-document:

* Verificatietijd
* Intrekkingscontrole
* Waarden voor tijdstempels

Als onderdeel van het instellen van deze opties kunt u een verificatietijd opgeven. U kunt bijvoorbeeld de huidige tijd selecteren (de tijd op de computer van de validator), die aangeeft dat de huidige tijd moet worden gebruikt. Voor informatie over de verschillende tijdwaarden, zie de `VerificationTime` opsommingswaarde in [&#x200B; AEM Forms API Verwijzing &#x200B;](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

U kunt ook opgeven of de intrekkingscontrole moet worden uitgevoerd tijdens het verificatieproces. U kunt bijvoorbeeld een intrekkingscontrole uitvoeren om te bepalen of het certificaat wordt ingetrokken. Voor informatie over de herroeping-controlerende opties, zie de `RevocationCheckStyle` opsommingswaarde in [&#x200B; AEM Forms API Verwijzing &#x200B;](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

Als u intrekkingscontrole wilt uitvoeren op een certificaat, geeft u een URL op naar een server met een certificaatintrekkingslijst (CRL) met behulp van een `CRLOptionSpec` -object. Als u echter geen URL opgeeft naar een CRL-server, verkrijgt de handtekeningservice de URL van het certificaat.

In plaats van een CRL-server te gebruiken, kunt u een OCSP-server (online certificate Status Protocol) gebruiken bij het controleren van intrekkingen. Wanneer u een OCSP-server gebruikt in plaats van een CRL-server, wordt de intrekkingscontrole meestal sneller uitgevoerd. (Zie [&#x200B; Online Protocol van de Status van het Certificaat &#x200B;](https://tools.ietf.org/html/rfc2560).)

U kunt de de serverorde plaatsen CRL en OCSP die de dienst van de Ondertekening door de Toepassingen en de Diensten van de Adobe te gebruiken gebruikt. Bijvoorbeeld, als de OCSP server eerst in de Toepassingen en de Diensten van de Adobe wordt geplaatst, wordt de server OCSP gecontroleerd, die door de server CRL wordt gevolgd.

Als u de intrekkingscontrole niet uitvoert, controleert de service Handtekening niet of het certificaat is ingetrokken. Dat wil zeggen dat CRL- en OCSP-serverinformatie wordt genegeerd.

>[!NOTE]
>
>U kunt de URL die in het certificaat is opgegeven, overschrijven met een object `CRLOptionSpec` en `OCSPOptionSpec` . Als u bijvoorbeeld de CRL-server wilt overschrijven, kunt u de methode `setLocalURI` van het object `CRLOptionSpec` aanroepen.

Tijdstempel is het proces waarbij de tijd wordt bijgehouden waarop een ondertekend of gecertificeerd document is gewijzigd. Nadat een document is ondertekend, kan niemand het wijzigen. Met tijdstempels kunt u de geldigheid van een ondertekend of gecertificeerd document afdwingen. U kunt opties voor tijdstempels instellen met een `TSPOptionSpec` -object. U kunt bijvoorbeeld de URL van een server met een tijdstempelprovider (TSP) opgeven.

>[!NOTE]
>
>In Java en de webservice wordt snel gestart, wordt de verificatietijd ingesteld op `VerificationTime.CURRENT_TIME` en wordt de intrekkingscontrole ingesteld op `RevocationCheckStyle.BestEffort` . Omdat er geen CRL- of OCSP-serverinformatie is opgegeven, wordt de serverinformatie opgehaald uit het certificaat.

**wint alle digitale handtekeningen** terug

Als u alle digitale handtekeningen in een PDF-document wilt verifiëren, haalt u de digitale handtekeningen op uit het PDF-document. Alle handtekeningen worden geretourneerd in een lijst. Controleer als onderdeel van de verificatie van een digitale handtekening de status van de handtekening.

>[!NOTE]
>
>In tegenstelling tot wanneer u één digitale handtekening verifieert en u meerdere handtekeningen verifieert, hoeft u de naam van het handtekeningveld niet op te geven.

**Interactief door alle handtekeningen**

Doorloop elke handtekening. Dat wil zeggen dat voor elke handtekening de digitale handtekening wordt geverifieerd en dat de identiteit van de ondertekenaar en de status van elke handtekening worden gecontroleerd. (Zie [&#x200B; Verifying Digital Signatures &#x200B;](#verify-digital-signatures-using-the-java-api).)

>[!NOTE]
>
>U hoeft niet alle handtekeningen te doorlopen als de vereiste het hele document is.

**zie ook**

[Meerdere digitale handtekeningen verifiëren met de Java API](#verify-digital-signatures-using-the-java-api)

[Meerdere digitale handtekeningen verifiëren met de webservice-API](#verify-digital-signatures-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Meerdere digitale handtekeningen verifiëren met de Java API {#verify-multiple-digital-signatures-using-the-java-api}

Verifieer meerdere digitale handtekeningen met de API voor handtekeningenservice (Java):

1. Projectbestanden opnemen

   Neem JAR-bestanden van de client, zoals adobe-signatures-client.jar, op in het klassepad van uw Java-project.

1. Een handtekeningclient maken

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `SignatureServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Hiermee wordt het PDF-document opgehaald dat de handtekeningen bevat die moeten worden gecontroleerd

   * Maak een `java.io.FileInputStream` -object dat het PDF-document vertegenwoordigt dat meerdere digitale handtekeningen bevat die u met de constructor ervan kunt controleren. Geef een tekenreekswaarde door die de locatie van het PDF-document aangeeft.
   * Maak een `com.adobe.idp.Document` -object door de constructor ervan te gebruiken en het `java.io.FileInputStream` -object door te geven.

1. PKI-runtime-opties instellen

   * Maak een `PKIOptions` -object met behulp van de constructor.
   * Stel de verificatietijd in door de methode `setVerificationTime` van het object `PKIOptions` aan te roepen en een opsommingswaarde `VerificationTime` door te geven die de verificatietijd opgeeft.
   * Stel de optie voor intrekkingscontrole in door de methode `setRevocationCheckStyle` van het object `PKIOptions` aan te roepen en een opsommingswaarde `RevocationCheckStyle` door te geven die aangeeft of een intrekkingscontrole moet worden uitgevoerd.

1. Alle digitale handtekeningen ophalen

   Roep de methode `verifyPDFDocument` van het object `SignatureServiceClient` aan en geef de volgende waarden door:

   * Een `com.adobe.idp.Document` -object dat een PDF-document bevat dat meerdere digitale handtekeningen bevat.
   * Een `PKIOptions` -object dat PKI-runtime-opties bevat.
   * Een `VerifySPIOptions` -instantie die SPI-informatie bevat. U kunt `null` voor deze parameter opgeven.

   De methode `verifyPDFDocument` retourneert een `PDFDocumentVerificationInfo` -object dat informatie bevat over alle digitale handtekeningen in het PDF-document.

1. Alle handtekeningen doorlopen

   * Doorloop alle handtekeningen door de methode `getVerificationInfos` van het object `PDFDocumentVerificationInfo` aan te roepen. Deze methode retourneert een `java.util.List` -object waarbij elk element een `PDFSignatureVerificationInfo` -object is. Gebruik een `java.util.Iterator` -object om de lijst met handtekeningen te doorlopen.
   * Met behulp van het `PDFSignatureVerificationInfo` -object kunt u taken uitvoeren zoals het bepalen van de status van de handtekening door de methode `PDFSignatureVerificationInfo` object `getStatus` aan te roepen. Deze methode retourneert een `SignatureStatus` -object waarvan het lid met statische gegevens u op de hoogte stelt van de status van de handtekening. Als de handtekening bijvoorbeeld onbekend is, retourneert deze methode `SignatureStatus.DocumentSignatureUnknown` .

**zie ook**

[Meerdere digitale handtekeningen controleren](#verifying-multiple-digital-signatures)

[Snel starten (SOAP modus): meerdere digitale handtekeningen controleren met de Java API](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-verifying-multiple-digital-signatures-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Digitale handtekeningen verifiëren](#verify-digital-signatures-using-the-java-api)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Meerdere digitale handtekeningen verifiëren met de webservice-API {#verifying-multiple-digital-signatures-using-the-web-service-api}

Verifieer veelvoudige digitale handtekeningen door de Dienst API van de Handtekening (Webdienst te gebruiken):

1. Projectbestanden opnemen

   Creeer een Microsoft .NET project dat MTOM gebruikt. Gebruik de volgende WSDL-definitie: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1` .

   >[!NOTE]
   >
   >Vervang `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Een handtekeningclient maken

   * Maak een `SignatureServiceClient` -object met de standaardconstructor.
   * Maak een `SignatureServiceClient.Endpoint.Address` -object met de `System.ServiceModel.EndpointAddress` -constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/SignatureService?WSDL` ). U hoeft het attribuut `lc_version` niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Maak een `System.ServiceModel.BasicHttpBinding` -object door de waarde van het `SignatureServiceClient.Endpoint.Binding` -veld op te halen. De geretourneerde waarde wordt gecast naar `BasicHttpBinding` .
   * Stel het veld `MessageEncoding` van het `System.ServiceModel.BasicHttpBinding` -object in op `WSMessageEncoding.Mtom` . Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld `SignatureServiceClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de bijbehorende wachtwoordwaarde toe aan het veld `SignatureServiceClient.ClientCredentials.UserName.Password` .
      * Wijs de constante waarde `HttpClientCredentialType.Basic` toe aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType` .
      * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` toe aan het veld `BasicHttpBindingSecurity.Security.Mode` .

1. Hiermee wordt het PDF-document opgehaald dat de handtekeningen bevat die moeten worden gecontroleerd

   * Maak een `BLOB` -object met behulp van de constructor. In het `BLOB` -object wordt een PDF-document opgeslagen dat meerdere digitale handtekeningen bevat om te controleren.
   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die staat voor de bestandslocatie van het PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `Length` van het object `System.IO.FileStream` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul het object `BLOB` door de eigenschap `MTOM` ervan toe te wijzen aan de inhoud van de bytearray.

1. PKI-runtime-opties instellen

   * Maak een `PKIOptions` -object met behulp van de constructor.
   * Stel de verificatietijd in door de opsommingswaarde `verificationTime` data member `VerificationTime` van het `PKIOptions` -object toe te wijzen die de verificatietijd opgeeft.
   * Stel de optie voor intrekkingscontrole in door het gegevenslid van het `revocationCheckStyle` data member `RevocationCheckStyle` -object een opsommingswaarde toe te wijzen die aangeeft of een intrekkingscontrole moet worden uitgevoerd.`PKIOptions`

1. Alle digitale handtekeningen ophalen

   Roep de methode `verifyPDFDocument` van het object `SignatureServiceClient` aan en geef de volgende waarden door:

   * Een `BLOB` -object dat een PDF-document bevat dat meerdere digitale handtekeningen bevat.
   * Een `PKIOptions` -object dat PKI-runtime-opties bevat.
   * Een `VerifySPIOptions` -instantie die SPI-informatie bevat. U kunt null opgeven voor deze parameter.

   De methode `verifyPDFDocument` retourneert een `PDFDocumentVerificationInfo` -object dat informatie bevat over alle digitale handtekeningen in het PDF-document.

1. Alle handtekeningen doorlopen

   * Doorloop alle handtekeningen door het gegevenslid `verificationInfos` van het object `PDFDocumentVerificationInfo` op te halen. Dit gegevenslid retourneert een `Object` -array waarbij elk element een `PDFSignatureVerificationInfo` -object is.
   * Met het `PDFSignatureVerificationInfo` -object kunt u taken uitvoeren zoals het bepalen van de status van de handtekening door het gegevenslid van het `PDFSignatureVerificationInfo` object `status` op te halen. Dit gegevenslid retourneert een `SignatureStatus` -object waarvan het lid met statische gegevens u op de hoogte stelt van de status van de handtekening. Als de handtekening bijvoorbeeld onbekend is, retourneert deze methode `SignatureStatus.DocumentSignatureUnknown` .

**zie ook**

[Meerdere digitale handtekeningen controleren](#verifying-multiple-digital-signatures)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Digitale handtekeningen verwijderen {#removing-digital-signatures}

Digitale handtekeningen moeten uit een handtekeningveld worden verwijderd voordat een nieuwere digitale handtekening kan worden toegepast. Een digitale handtekening kan niet worden overschreven. Als u probeert een digitale handtekening toe te passen op een handtekeningveld dat een handtekening bevat, treedt een uitzondering op.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Handtekening, zie [&#x200B; Verwijzing van de Diensten voor AEM Forms &#x200B;](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-8}

Als u een digitale handtekening uit een handtekeningveld wilt verwijderen, voert u de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak een handtekeningclient.
1. Hiermee wordt het PDF-document opgehaald dat een handtekening bevat die u wilt verwijderen.
1. Verwijder de digitale handtekening uit het handtekeningveld.
1. Sla het PDF-document op als een PDF-bestand.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

Voor informatie over de plaats van deze JAR dossiers, zie [&#x200B; Inclusief de bibliotheekdossiers van AEM Forms Java &#x200B;](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**creeer een cliënt van de Handtekening**

Voordat u programmatically een verrichting van de dienst van de Handtekening kunt uitvoeren, moet u een cliënt van de dienst van de Handtekening tot stand brengen.

**krijgt het document van de PDF dat een handtekening bevat om te verwijderen**

Als u een handtekening uit een PDF-document wilt verwijderen, moet u een PDF-document met een handtekening verkrijgen.

**verwijder de digitale handtekening uit het handtekeningsgebied**

Als u een digitale handtekening uit een PDF-document wilt verwijderen, moet u de naam opgeven van het handtekeningveld dat de digitale handtekening bevat. Bovendien moet u toestemming hebben om de digitale handtekening te verwijderen. Anders treedt een uitzondering op.

**sparen het document van de PDF als dossier van PDF**

Nadat de handtekeningservice een digitale handtekening uit een handtekeningveld heeft verwijderd, kunt u het PDF-document opslaan als een PDF-bestand, zodat gebruikers het kunnen openen in Acrobat of Adobe Reader.

**zie ook**

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

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `SignatureServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Het PDF-document ophalen dat een handtekening bevat die moet worden verwijderd

   * Maak een `java.io.FileInputStream` -object dat staat voor het PDF-document dat de handtekening bevat die moet worden verwijderd met behulp van de constructor ervan en geef een tekenreekswaarde door die de locatie van het PDF-document aangeeft.
   * Maak een `com.adobe.idp.Document` -object door de constructor ervan te gebruiken en het `java.io.FileInputStream` -object door te geven.

1. De digitale handtekening verwijderen uit het handtekeningveld

   Verwijder een digitale handtekening uit een handtekeningveld door de methode `clearSignatureField` van het object `SignatureServiceClient` aan te roepen en de volgende waarden door te geven:

   * Een `com.adobe.idp.Document` -object dat staat voor het PDF-document dat de te verwijderen handtekening bevat.
   * Een tekenreekswaarde die de naam aangeeft van het handtekeningveld dat de digitale handtekening bevat.

   De methode `clearSignatureField` retourneert een `com.adobe.idp.Document` -object dat het PDF-document vertegenwoordigt waaruit de digitale handtekening is verwijderd.

1. Het PDF-document opslaan als een PDF-bestand

   * Maak een `java.io.File` -object en controleer of de bestandsextensie .pdf is.
   * Roep de methode `copyToFile` van het object `com.adobe.idp.Document` aan. Geef het object `java.io.File` door om de inhoud van het object `com.adobe.idp.Document` naar het bestand te kopiëren. Gebruik het object `Document` dat door de methode `clearSignatureField` is geretourneerd.

**zie ook**

[Digitale handtekeningen verwijderen](digitally-signing-certifying-documents.md#removing-digital-signatures)

[Snel starten (SOAP modus): een digitale handtekening verwijderen met de Java API](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-removing-a-digital-signature-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Digitale handtekeningen verwijderen met de webservice-API {#remove-digital-signatures-using-the-web-service-api}

Een digitale handtekening verwijderen met de handtekening-API (webservice):

1. Projectbestanden opnemen

   Creeer een Microsoft .NET project dat MTOM gebruikt. Gebruik de volgende WSDL-definitie: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1` .

   >[!NOTE]
   >
   >Vervang `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Een handtekeningclient maken

   * Maak een `SignatureServiceClient` -object met de standaardconstructor.
   * Maak een `SignatureServiceClient.Endpoint.Address` -object met de `System.ServiceModel.EndpointAddress` -constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/SignatureService?WSDL` ). U hoeft het attribuut `lc_version` niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Maak een `System.ServiceModel.BasicHttpBinding` -object door de waarde van het `SignatureServiceClient.Endpoint.Binding` -veld op te halen. De geretourneerde waarde wordt gecast naar `BasicHttpBinding` .
   * Stel het veld `MessageEncoding` van het `System.ServiceModel.BasicHttpBinding` -object in op `WSMessageEncoding.Mtom` . Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld `SignatureServiceClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de bijbehorende wachtwoordwaarde toe aan het veld `SignatureServiceClient.ClientCredentials.UserName.Password` .
      * Wijs de constante waarde `HttpClientCredentialType.Basic` toe aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType` .
      * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` toe aan het veld `BasicHttpBindingSecurity.Security.Mode` .

1. Het PDF-document ophalen dat een handtekening bevat die moet worden verwijderd

   * Maak een `BLOB` -object met behulp van de constructor. Met het `BLOB` -object wordt een PDF-document opgeslagen dat een digitale handtekening bevat die moet worden verwijderd.
   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het ondertekende PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `Length` van het object `System.IO.FileStream` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul het object `BLOB` door de eigenschap `MTOM` ervan toe te wijzen met de inhoud van de bytearray.

1. De digitale handtekening verwijderen uit het handtekeningveld

   Verwijder de digitale handtekening door de methode `clearSignatureField` van het object `SignatureServiceClient` aan te roepen en de volgende waarden door te geven:

   * Een `BLOB` -object dat het ondertekende PDF-document bevat.
   * Een tekenreekswaarde die de naam vertegenwoordigt van het handtekeningveld dat de digitale handtekening bevat die moet worden verwijderd.

   De methode `clearSignatureField` retourneert een `BLOB` -object dat het PDF-document vertegenwoordigt waaruit de digitale handtekening is verwijderd.

1. Het PDF-document opslaan als een PDF-bestand

   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het PDF-document dat een leeg handtekeningveld bevat en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud wordt opgeslagen van het `BLOB` -object dat door de methode `sign` is geretourneerd. Vul de bytearray met de waarde van het gegevenslid `MTOM` van het object `BLOB` .
   * Maak een `System.IO.BinaryWriter` -object door de constructor ervan aan te roepen en het `System.IO.FileStream` -object door te geven.
   * Schrijf de inhoud van de bytearray naar het PDF-bestand door de methode `Write` van het object `System.IO.BinaryWriter` aan te roepen en de bytearray door te geven.

**zie ook**

[Digitale handtekeningen verwijderen](digitally-signing-certifying-documents.md#removing-digital-signatures)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
