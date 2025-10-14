---
title: DDX-documenten valideren
description: Valideer een DDX-document programmatically met de Java API en de Web Service API.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: 1f5a2cf3-ef6b-45b4-8fa8-b300e492fee1
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services,APIs & Integrations
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '1507'
ht-degree: 0%

---

# DDX-documenten valideren {#validating-ddx-documents}

**de Steekproeven en de voorbeelden in dit document zijn slechts voor AEM Forms op milieu JEE.**

U kunt een DX- document programmatically bevestigen dat door de dienst van de Assembler wordt gebruikt. Met andere woorden, met de API van de Assembler-service kunt u bepalen of een DDX-document geldig is of niet. Als u bijvoorbeeld een upgrade hebt uitgevoerd van een eerdere AEM Forms-versie en u wilt controleren of uw DDX-document geldig is, kunt u dit valideren met de API voor de Assembler-service.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Assembler, zie [&#x200B; Verwijzing van de Diensten voor AEM Forms &#x200B;](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Voor meer informatie over een document DDX, zie [&#x200B; de Dienst van de Assembler en de Verwijzing DDX &#x200B;](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Overzicht van de stappen {#summary-of-steps}

Voer de volgende taken uit om een DDX-document te valideren:

1. Inclusief projectbestanden.
1. Maak een Assembler-client.
1. Verwijs naar een bestaand DDX-document.
1. Stel uitvoeringsopties in om het DDX-document te valideren.
1. Voer de validatie uit.
1. Sla de validatieresultaten op in een logbestand.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

als AEM Forms wordt geïmplementeerd op een andere ondersteunde J2EE-toepassingsserver dan JBoss, moet u de bestanden adobe-utilities.jar en jbossall-client.jar vervangen door JAR-bestanden die specifiek zijn voor de J2EE-toepassingsserver waarop AEM Forms is geïmplementeerd.

**creeer een cliënt van de Assembler van de PDF**

Alvorens u programmatically een verrichting van de Assembler kunt uitvoeren, moet u een de dienstcliënt van de Assembler tot stand brengen.

**Verwijzing een bestaand document DDX**

Als u een DDX-document wilt valideren, moet u naar een bestaand DDX-document verwijzen.

**plaats runtime opties om het DDX- document** te bevestigen

Wanneer het bevestigen van een DX- document, moet u specifieke runtime opties plaatsen die de dienst van de Assembler opdragen om het DX- document te bevestigen in plaats van het uit te voeren. Ook, kunt u de hoeveelheid informatie verhogen die de dienst van de Assembler aan het logboekdossier schrijft.

**voer de bevestiging** uit

Nadat u de de dienstcliënt van de Assembler creeert, van verwijzingen het DX- document, en vastgestelde runtime opties, kunt u de `invokeDDX` verrichting aanhalen om het DX- document te bevestigen. Wanneer u het DDX-document valideert, kunt u `null` als kaartparameter doorgeven (in deze parameter worden gewoonlijk PDF-documenten opgeslagen die de Assembler nodig heeft om de bewerking(en) uit te voeren die in het DDX-document is opgegeven).

Als de validatie mislukt, wordt een uitzondering gegenereerd en bevat het logbestand details die verklaren waarom het DDX-document ongeldig is, kunnen worden opgehaald uit de instantie `OperationException` . Zodra voorbij het basisontleden van XML en schema het controleren, dan wordt de bevestiging tegen de specificatie DDX uitgevoerd. Alle fouten die in het DDX-document staan, worden opgegeven in het logbestand.

**sparen de bevestigingsresultaten in een logboekdossier**

De dienst van de Assembler keert de bevestigingsresultaten terug die u aan een het logboekdossier van XML kunt schrijven. De hoeveelheid detail die de dienst van de Assembler aan het logboekdossier schrijft hangt van de runtime optie af die u plaatst.

**zie ook**

[Een DDX-document valideren met de Java API](#validate-a-ddx-document-using-the-java-api)

[Een DDX-document valideren met de webservice-API](#validate-a-ddx-document-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[PDF-documenten programmatisch samenstellen](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Een DDX-document valideren met de Java API {#validate-a-ddx-document-using-the-java-api}

Valideer een DDX-document met behulp van de API voor vergaderingsservice (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-assembler-client.jar, op in het klassenpad van uw Java-project.

1. Maak een PDF Assembler-client.

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `AssemblerServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Verwijs naar een bestaand DDX-document.

   * Maak een `java.io.FileInputStream` -object dat het DDX-document vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het DDX-bestand aangeeft.
   * Maak een `com.adobe.idp.Document` -object door de constructor ervan te gebruiken en het `java.io.FileInputStream` -object door te geven.

1. Stel uitvoeringsopties in om het DDX-document te valideren.

   * Maak een `AssemblerOptionSpec` -object dat uitvoeringsopties opslaat met behulp van de bijbehorende constructor.
   * Stel de runtime-optie in die de Assembler-service opgeeft het DDX-document te valideren door de methode setValidateOnly van het `AssemblerOptionSpec` -object aan te roepen en door te geven `true` .
   * Stel de hoeveelheid informatie in die de Assembler-service naar het logbestand schrijft door de methode `getLogLevel` van het `AssemblerOptionSpec` -object aan te roepen en een tekenreekswaarde door te geven, voldoet aan uw vereisten. Wanneer u een DDX-document valideert, wilt u meer informatie naar het logbestand dat u helpt bij het validatieproces. Hierdoor kunt u de waarde `FINE` of `FINER` doorgeven.

1. Voer de validatie uit.

   Roep de methode `invokeDDX` van het object `AssemblerServiceClient` aan en geef de volgende waarden door:

   * Een `com.adobe.idp.Document` -object dat het DDX-document vertegenwoordigt.
   * De waarde `null` voor het object java.io.Map waarin gewoonlijk PDF-documenten worden opgeslagen.
   * Een `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` -object dat de runtime-opties opgeeft.

   De methode `invokeDDX` retourneert een `AssemblerResult` -object dat informatie bevat die opgeeft of het DDX-document geldig is.

1. Sla de validatieresultaten op in een logbestand.

   * Maak een `java.io.File` -object en controleer of de bestandsnaamextensie .xml is.
   * Roep de methode `getJobLog` van het object `AssemblerResult` aan. Deze methode retourneert een `com.adobe.idp.Document` -instantie die validatiegegevens bevat.
   * Roep de methode `copyToFile` van het object `com.adobe.idp.Document` aan om de inhoud van het object `com.adobe.idp.Document` naar het bestand te kopiëren.

   >[!NOTE]
   >
   >Als het DDX-document ongeldig is, wordt een `OperationException` gegenereerd. Binnen de instructie catch kunt u de methode `getJobLog` van het object `OperationException` aanroepen.

**zie ook**

[DDX-documenten valideren](#validating-ddx-documents)

[&#x200B; Snel Begin (SOAP wijze): Het bevestigen van DX documenten gebruikend Java API &#x200B;](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-validating-ddx-documents-using-the-java-api) (SOAP wijze)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Een DDX-document valideren met de webservice-API {#validate-a-ddx-document-using-the-web-service-api}

Valideer een DDX-document met behulp van de API (webservice) voor vergaderingsservice:

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Gebruik de volgende WSDL-definitie: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1` .

   >[!NOTE]
   >
   >Vervang localhost door het IP-adres van de Forms Server.

1. Maak een PDF Assembler-client.

   * Maak een `AssemblerServiceClient` -object met de standaardconstructor.
   * Maak een `AssemblerServiceClient.Endpoint.Address` -object met de `System.ServiceModel.EndpointAddress` -constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/AssemblerService?blob=mtom` ). U hoeft het attribuut `lc_version` niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.
   * Maak een `System.ServiceModel.BasicHttpBinding` -object door de waarde van het `AssemblerServiceClient.Endpoint.Binding` -veld op te halen. De geretourneerde waarde wordt gecast naar `BasicHttpBinding` .
   * Stel het veld `MessageEncoding` van het `System.ServiceModel.BasicHttpBinding` -object in op `WSMessageEncoding.Mtom` . Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld `AssemblerServiceClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de bijbehorende wachtwoordwaarde toe aan het veld `AssemblerServiceClient.ClientCredentials.UserName.Password` .
      * Wijs de constante waarde `HttpClientCredentialType.Basic` toe aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType` .
      * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` toe aan het veld `BasicHttpBindingSecurity.Security.Mode` .

1. Verwijs naar een bestaand DDX-document.

   * Maak een `BLOB` -object met behulp van de constructor. Het `BLOB` -object wordt gebruikt om het DDX-document op te slaan.
   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het DDX-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `Length` van het object `System.IO.FileStream` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het object `BLOB` door de eigenschap `MTOM` ervan toe te wijzen met de inhoud van de bytearray.

1. Stel uitvoeringsopties in om het DDX-document te valideren.

   * Maak een `AssemblerOptionSpec` -object dat uitvoeringsopties opslaat met behulp van de bijbehorende constructor.
   * Stel de runtime-optie in die de Assembler-service opgeeft het DDX-document te valideren door de waarde true toe te wijzen aan het `validateOnly` -gegevenslid van het `AssemblerOptionSpec` -object.
   * Stel de hoeveelheid informatie in die de Assembler-service naar het logbestand schrijft door een tekenreekswaarde toe te wijzen aan het `logLevel` -gegevenslid van het `AssemblerOptionSpec` -object. methode Bij het valideren van een DDX-document wilt u meer informatie naar het logbestand schrijven dat u helpt bij het validatieproces. Hierdoor kunt u de waarde `FINE` of `FINER` opgeven. Voor informatie over de runtime opties die u kunt plaatsen, zie de `AssemblerOptionSpec` klassenverwijzing in [&#x200B; AEM Forms API Verwijzing &#x200B;](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Voer de validatie uit.

   Roep de methode `invokeDDX` van het object `AssemblerServiceClient` aan en geef de volgende waarden door:

   * Een `BLOB` -object dat het DDX-document vertegenwoordigt.
   * De waarde `null` voor het `Map` -object waarin gewoonlijk PDF-documenten worden opgeslagen.
   * Een `AssemblerOptionSpec` -object dat uitvoeringsopties opgeeft.

   De methode `invokeDDX` retourneert een `AssemblerResult` -object dat informatie bevat die opgeeft of het DDX-document geldig is.

1. Sla de validatieresultaten op in een logbestand.

   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het logbestand en de modus voor het openen van het bestand vertegenwoordigt. Controleer of de bestandsnaamextensie .xml is.
   * Maak een `BLOB` -object dat logboekgegevens opslaat door de waarde van het gegevenslid van het `AssemblerResult` object `jobLog` op te halen.
   * Maak een bytearray waarin de inhoud van het object `BLOB` wordt opgeslagen. Vul de bytearray met de waarde van het veld `MTOM` van het object `BLOB` .
   * Maak een `System.IO.BinaryWriter` -object door de constructor ervan aan te roepen en het `System.IO.FileStream` -object door te geven.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door de methode `Write` van het object `System.IO.BinaryWriter` aan te roepen en de bytearray door te geven.

   >[!NOTE]
   >
   >Als het DDX-document ongeldig is, wordt een `OperationException` gegenereerd. Binnen de catch-instructie kunt u de waarde van het `jobLog` -lid van het `OperationException` -object ophalen.

**zie ook**

[DDX-documenten valideren](#validating-ddx-documents)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
