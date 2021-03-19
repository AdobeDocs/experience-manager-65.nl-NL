---
title: DDX-documenten valideren
seo-title: DDX-documenten valideren
description: Valideer een DDX-document programmatically met de Java API en de Web Service API.
seo-description: Valideer een DDX-document programmatically met de Java API en de Web Service API.
uuid: da668170-d2e9-4fff-aef5-432a856bd0bd
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 693859b0-a0c3-43f1-95c0-be48a90d7d8d
role: Developer
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1544'
ht-degree: 0%

---


# DDX-documenten {#validating-ddx-documents} valideren

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

U kunt een DX- document programmatically bevestigen dat door de dienst van de Assembler wordt gebruikt. Met andere woorden, met de API van de Assembler-service kunt u bepalen of een DDX-document geldig is of niet. Als u bijvoorbeeld een upgrade hebt uitgevoerd van een eerdere AEM Forms-versie en u wilt controleren of uw DDX-document geldig is, kunt u dit valideren met de API voor de Assembler-service.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Assembler, zie [de Verwijzing van de Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Voor meer informatie over een DX- document, zie [de Dienst van de Assembler en DX Verwijzing](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Overzicht van stappen {#summary-of-steps}

Voer de volgende taken uit om een DDX-document te valideren:

1. Inclusief projectbestanden.
1. Maak een Assembler-client.
1. Verwijs naar een bestaand DDX-document.
1. Stel uitvoeringsopties in om het DDX-document te valideren.
1. Voer de validatie uit.
1. Sla de validatieresultaten op in een logbestand.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

als AEM Forms wordt geïmplementeerd op een andere ondersteunde J2EE-toepassingsserver dan JBoss, moet u de bestanden adobe-utilities.jar en jbossall-client.jar vervangen door JAR-bestanden die specifiek zijn voor de J2EE-toepassingsserver waarop AEM Forms is geïmplementeerd.

**Een PDF Assembler-client maken**

Alvorens u programmatically een verrichting van de Assembler kunt uitvoeren, moet u een de dienstcliënt van de Assembler tot stand brengen.

**Verwijzen naar een bestaand DDX-document**

Als u een DDX-document wilt valideren, moet u naar een bestaand DDX-document verwijzen.

**Stel runtime-opties in om het DDX-document te valideren**

Wanneer het bevestigen van een DX- document, moet u specifieke runtime opties plaatsen die de dienst van de Assembler opdragen om het DX- document te bevestigen in plaats van het uit te voeren. Ook, kunt u de hoeveelheid informatie verhogen die de dienst van de Assembler aan het logboekdossier schrijft.

**De validatie uitvoeren**

Nadat u de de dienstcliënt van de Assembler creeert, van verwijzingen het DX- document, en vastgestelde runtime opties, kunt u `invokeDDX` verrichting aanhalen om het DX- document te bevestigen. Wanneer u het DDX-document valideert, kunt u `null` als kaartparameter doorgeven (in deze parameter worden gewoonlijk PDF-documenten opgeslagen die de Assembler nodig heeft om de bewerking(en) uit te voeren die in het DDX-document is opgegeven).

Als de bevestiging ontbreekt, wordt een uitzondering geworpen en het logboekdossier bevat details die verklaren waarom het DX- document ongeldig is kan uit `OperationException` instantie worden verkregen. Zodra voorbij het basisontleden van XML en schema het controleren, dan wordt de bevestiging tegen de specificatie DDX uitgevoerd. Alle fouten die zich in het DDX-document bevinden, worden opgegeven in het logbestand.

**De validatieresultaten opslaan in een logbestand**

De dienst van de Assembler keert de bevestigingsresultaten terug die u aan een het logboekdossier van XML kunt schrijven. De hoeveelheid detail die de dienst van de Assembler aan het logboekdossier schrijft hangt van de runtime optie af die u plaatst.

**Zie ook**

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

   * Maak een `ServiceClientFactory`-object dat verbindingseigenschappen bevat.
   * Maak een `AssemblerServiceClient`-object door de constructor ervan te gebruiken en het object `ServiceClientFactory` door te geven.

1. Verwijs naar een bestaand DDX-document.

   * Maak een `java.io.FileInputStream`-object dat het DDX-document vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het DDX-bestand aangeeft.
   * Maak een `com.adobe.idp.Document`-object door de constructor ervan te gebruiken en het object `java.io.FileInputStream` door te geven.

1. Stel uitvoeringsopties in om het DDX-document te valideren.

   * Maak een `AssemblerOptionSpec`-object dat uitvoeringsopties opslaat met de constructor ervan.
   * Plaats de runtime optie die de dienst van de Assembler opdraagt om het DX- document te bevestigen door de methode setValidateOnly van het `AssemblerOptionSpec` voorwerp aan te halen en `true` over te gaan.
   * Stel de hoeveelheid informatie in die de Assembler-service naar het logbestand schrijft door de methode `getLogLevel` van het object `AssemblerOptionSpec` aan te roepen en een tekenreekswaarde door te geven die aan uw vereisten voldoet. Wanneer u een DDX-document valideert, wilt u meer informatie naar het logbestand dat u helpt bij het validatieproces. Hierdoor kunt u de waarde `FINE` of `FINER` doorgeven.

1. Voer de validatie uit.

   Roep de methode `invokeDDX` van het object `AssemblerServiceClient` aan en geef de volgende waarden door:

   * Een `com.adobe.idp.Document`-object dat het DDX-document vertegenwoordigt.
   * De waarde `null` voor het object java.io.Map dat gewoonlijk PDF-documenten opslaat.
   * Een `com.adobe.livecycle.assembler.client.AssemblerOptionSpec`-object dat de runtime-opties opgeeft.

   De methode `invokeDDX` retourneert een `AssemblerResult`-object dat informatie bevat die opgeeft of het DDX-document geldig is.

1. Sla de validatieresultaten op in een logbestand.

   * Maak een `java.io.File`-object en zorg dat de bestandsnaamextensie .xml is.
   * Roep de methode `AssemblerResult` van het object `getJobLog` aan. Deze methode retourneert een `com.adobe.idp.Document`-instantie die validatiegegevens bevat.
   * Roep de methode `com.adobe.idp.Document` van het object `copyToFile` aan om de inhoud van het object `com.adobe.idp.Document` naar het bestand te kopiëren.

   >[!NOTE]
   >
   >Als het DDX-document ongeldig is, wordt een `OperationException` gegenereerd. Binnen de catch-instructie kunt u de methode `getJobLog` van het object `OperationException` aanroepen.

**Zie ook**

[DDX-documenten valideren](#validating-ddx-documents)

[Snel starten (SOAP-modus): DDX-documenten valideren met de Java API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-validating-ddx-documents-using-the-java-api)  (SOAP-modus)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Een DDX-document valideren met de webservice-API {#validate-a-ddx-document-using-the-web-service-api}

Valideer een DDX-document met behulp van de API (webservice) voor vergaderingsservice:

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervang localhost door het IP-adres van de formulierserver.

1. Maak een PDF Assembler-client.

   * Maak een `AssemblerServiceClient`-object met de standaardconstructor.
   * Maak een `AssemblerServiceClient.Endpoint.Address`-object met de constructor `System.ServiceModel.EndpointAddress`. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). U hoeft het `lc_version`-kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.
   * Maak een `System.ServiceModel.BasicHttpBinding`-object door de waarde van het veld `AssemblerServiceClient.Endpoint.Binding` op te halen. Cast de terugkeerwaarde aan `BasicHttpBinding`.
   * Stel het veld `System.ServiceModel.BasicHttpBinding` van het object `MessageEncoding` in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor het AEM aan het veld `AssemblerServiceClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de overeenkomstige wachtwoordwaarde aan het gebied `AssemblerServiceClient.ClientCredentials.UserName.Password` toe.
      * Wijs de constante waarde `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType` toe.
      * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode` toe.

1. Verwijs naar een bestaand DDX-document.

   * Maak een `BLOB`-object met de constructor ervan. Het object `BLOB` wordt gebruikt om het DDX-document op te slaan.
   * Maak een `System.IO.FileStream`-object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het DDX-document en de modus voor het openen van het bestand in vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `System.IO.FileStream` van het object `Length` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het object `BLOB` door de eigenschap `MTOM` ervan toe te wijzen met de inhoud van de bytearray.

1. Stel uitvoeringsopties in om het DDX-document te valideren.

   * Maak een `AssemblerOptionSpec`-object dat uitvoeringsopties opslaat met de constructor ervan.
   * Plaats de runtime optie die de dienst van de Assembler opdraagt om het DX- document te bevestigen door de waarde waar aan het `AssemblerOptionSpec` gegevenslid van het voorwerp `validateOnly` toe te wijzen.
   * Stel de hoeveelheid informatie in die de Assembler-service naar het logbestand schrijft door een tekenreekswaarde toe te wijzen aan het `AssemblerOptionSpec`-gegevenslid van het `logLevel`-object. methode Bij het valideren van een DDX-document wilt u meer informatie naar het logbestand schrijven dat u helpt bij het validatieproces. Hierdoor kunt u de waarde `FINE` of `FINER` opgeven. Zie de `AssemblerOptionSpec`-klasseverwijzing in [AEM Forms API Reference](https://www.adobe.com/go/learn_aemforms_javadocs_63_en) voor informatie over de runtime-opties die u kunt instellen.

1. Voer de validatie uit.

   Roep de methode `invokeDDX` van het object `AssemblerServiceClient` aan en geef de volgende waarden door:

   * Een `BLOB`-object dat het DDX-document vertegenwoordigt.
   * De waarde `null` voor het `Map`-object dat gewoonlijk PDF-documenten opslaat.
   * Een `AssemblerOptionSpec`-object dat uitvoeringsopties opgeeft.

   De methode `invokeDDX` retourneert een `AssemblerResult`-object dat informatie bevat die opgeeft of het DDX-document geldig is.

1. Sla de validatieresultaten op in een logbestand.

   * Maak een `System.IO.FileStream`-object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het logbestand en de modus voor het openen van het bestand vertegenwoordigt. Controleer of de bestandsnaamextensie .xml is.
   * Maak een `BLOB`-object dat logboekgegevens opslaat door de waarde van het `AssemblerResult`-gegevenslid van het object op te halen.`jobLog`
   * Maak een bytearray waarin de inhoud van het object `BLOB` wordt opgeslagen. Vul de bytearray met de waarde van het veld `BLOB` van het object `MTOM`.
   * Maak een `System.IO.BinaryWriter`-object door de constructor ervan aan te roepen en het object `System.IO.FileStream` door te geven.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door de methode `Write` van het object `System.IO.BinaryWriter` aan te roepen en de bytearray door te geven.

   >[!NOTE]
   >
   >Als het DDX-document ongeldig is, wordt een `OperationException` gegenereerd. Binnen de catch-instructie kunt u de waarde van het `OperationException`-lid van het object ophalen.`jobLog`

**Zie ook**

[DDX-documenten valideren](#validating-ddx-documents)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
