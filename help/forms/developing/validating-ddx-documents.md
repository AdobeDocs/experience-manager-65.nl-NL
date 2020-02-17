---
title: DDX-documenten valideren
seo-title: DDX-documenten valideren
description: 'null'
seo-description: 'null'
uuid: da668170-d2e9-4fff-aef5-432a856bd0bd
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 693859b0-a0c3-43f1-95c0-be48a90d7d8d
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# DDX-documenten valideren {#validating-ddx-documents}

U kunt een DX- document programmatically bevestigen dat door de dienst van de Assembler wordt gebruikt. Met andere woorden, met de API van de Assembler-service kunt u bepalen of een DDX-document geldig is of niet. Als u bijvoorbeeld een upgrade hebt uitgevoerd van een eerdere versie van AEM Forms en u wilt controleren of uw DDX-document geldig is, kunt u deze valideren met de API van de Assembler-service.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Assembler, zie de Verwijzing van de [Diensten voor Vormen](https://www.adobe.com/go/learn_aemforms_services_63)AEM.

>[!NOTE]
>
>Voor meer informatie over een DX- document, zie de Dienst van de [Assembler en de Verwijzing](https://www.adobe.com/go/learn_aemforms_ddx_63)DDX.

## Overzicht van de stappen {#summary-of-steps}

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
* jbossall-client.jar (vereist als AEM-formulieren worden geïmplementeerd op JBoss)

als AEM Forms wordt geïmplementeerd op een andere ondersteunde J2EE-toepassingsserver dan JBoss, moet u de bestanden adobe-utilities.jar en jbossall-client.jar vervangen door JAR-bestanden die specifiek zijn voor de J2EE-toepassingsserver waarop AEM Forms wordt geïmplementeerd.

**Een PDF Assembler-client maken**

Alvorens u programmatically een verrichting van de Assembler kunt uitvoeren, moet u een de dienstcliënt van de Assembler tot stand brengen.

**Verwijzen naar een bestaand DDX-document**

Als u een DDX-document wilt valideren, moet u naar een bestaand DDX-document verwijzen.

**Stel runtime-opties in om het DDX-document te valideren**

Wanneer het bevestigen van een Dx- document, moet u specifieke runtime opties plaatsen die de dienst van de Assembler opdragen om het Dx- document in plaats van het uit te voeren te bevestigen. Ook, kunt u de hoeveelheid informatie verhogen die de dienst van de Assembler aan het logboekdossier schrijft.

**De validatie uitvoeren**

Nadat u de de dienstcliënt van de Assembler creeert, van verwijzingen het DX- document, en vastgestelde runtime opties, kunt u de `invokeDDX` verrichting aanhalen om het DX- document te bevestigen. Bij het valideren van het DDX-document kunt u `null` als kaartparameter doorgeven (in deze parameter worden gewoonlijk PDF-documenten opgeslagen die de Assembler nodig heeft om de bewerking(en) uit te voeren die in het DDX-document is opgegeven).

Als de validatie mislukt, wordt een uitzondering gegenereerd en bevat het logbestand details die verklaren waarom het DDX-document ongeldig is, kunnen worden opgehaald uit de `OperationException` instantie. Zodra voorbij het basisontleden van XML en schema het controleren, dan wordt de bevestiging tegen de specificatie DDX uitgevoerd. Alle fouten die zich in het DDX-document bevinden, worden opgegeven in het logbestand.

**De validatieresultaten opslaan in een logbestand**

De dienst van de Assembler keert de bevestigingsresultaten terug die u aan een het logboekdossier van XML kunt schrijven. De hoeveelheid detail die de dienst van de Assembler aan het logboekdossier schrijft hangt van de runtime optie af die u plaatst.

**Zie ook**

[Een DDX-document valideren met de Java API](#validate-a-ddx-document-using-the-java-api)

[Een DDX-document valideren met de webservice-API](#validate-a-ddx-document-using-the-web-service-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[PDF-documenten programmatisch samenstellen](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Een DDX-document valideren met de Java API {#validate-a-ddx-document-using-the-java-api}

Valideer een DDX-document met behulp van de API voor vergaderingsservice (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-assembler-client.jar, op in het klassenpad van uw Java-project.

1. Maak een PDF Assembler-client.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `AssemblerServiceClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Verwijs naar een bestaand DDX-document.

   * Maak een `java.io.FileInputStream` object dat het DDX-document vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het DDX-bestand aangeeft.
   * Maak een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en het `java.io.FileInputStream` object door te geven.

1. Stel uitvoeringsopties in om het DDX-document te valideren.

   * Maak een `AssemblerOptionSpec` object dat uitvoeringsopties opslaat met de constructor ervan.
   * Plaats de runtime optie die de dienst van de Assembler opdraagt om het DX- document te bevestigen door de methode setValidateOnly van het `AssemblerOptionSpec` voorwerp aan te halen en over te gaan `true`.
   * Stel de hoeveelheid informatie in die de Assembler-service naar het logbestand schrijft door de methode van het `AssemblerOptionSpec` `getLogLevel` object aan te roepen en een tekenreekswaarde door te geven, aan uw vereisten voldoet. Wanneer u een DDX-document valideert, wilt u meer informatie naar het logbestand dat u helpt bij het validatieproces. Hierdoor kunt u de waarde `FINE` of `FINER`.

1. Voer de validatie uit.

   Roep de methode van het `AssemblerServiceClient` `invokeDDX` object aan en geef de volgende waarden door:

   * Een `com.adobe.idp.Document` object dat het DDX-document vertegenwoordigt.
   * De waarde `null` voor het object java.io.Map waarin gewoonlijk PDF-documenten worden opgeslagen.
   * Een `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` object dat de runtime-opties opgeeft.
   De `invokeDDX` methode retourneert een `AssemblerResult` object dat informatie bevat die opgeeft of het DDX-document geldig is.

1. Sla de validatieresultaten op in een logbestand.

   * Maak een `java.io.File` object en zorg dat de bestandsnaamextensie .xml is.
   * Roep de `AssemblerResult` methode van het `getJobLog` object aan. Deze methode retourneert een `com.adobe.idp.Document` instantie die validatiegegevens bevat.
   * Roep de `com.adobe.idp.Document` methode van het `copyToFile` object aan om de inhoud van het `com.adobe.idp.Document` object naar het bestand te kopiëren.
   >[!NOTE]
   >
   >Als het DDX-document ongeldig is, `OperationException` wordt er een gegenereerd. Binnen de catch-instructie kunt u de `OperationException` methode van het `getJobLog` object aanroepen.

**Zie ook**

[DDX-documenten valideren](#validating-ddx-documents)

[Snel starten (SOAP-modus): DDX-documenten valideren met de Java API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-validating-ddx-documents-using-the-java-api) (SOAP-modus)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Een DDX-document valideren met de webservice-API {#validate-a-ddx-document-using-the-web-service-api}

Valideer een DDX-document met behulp van de API (webservice) voor vergaderingsservice:

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervang localhost door het IP-adres van de formulierserver.

1. Maak een PDF Assembler-client.

   * Maak een `AssemblerServiceClient` object met de standaardconstructor.
   * Maak een `AssemblerServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde door die de WSDL opgeeft voor de service AEM Forms (bijvoorbeeld `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). U hoeft het `lc_version` kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `AssemblerServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het veld `AssemblerServiceClient.ClientCredentials.UserName.UserName`.
      * Wijs de bijbehorende wachtwoordwaarde aan het veld toe `AssemblerServiceClient.ClientCredentials.UserName.Password`.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Verwijs naar een bestaand DDX-document.

   * Maak een `BLOB` object met de constructor ervan. Het `BLOB` object wordt gebruikt om het DDX-document op te slaan.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het DDX-document en de modus voor het openen van het bestand in vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de methode van het `System.IO.FileStream` `Read` object aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` object door de `MTOM` eigenschap ervan toe te wijzen met de inhoud van de bytearray.

1. Stel uitvoeringsopties in om het DDX-document te valideren.

   * Maak een `AssemblerOptionSpec` object dat uitvoeringsopties opslaat met de constructor ervan.
   * Plaats de runtime optie die de dienst van de Assembler opdraagt om het Dx- document te bevestigen door de waarde waar aan het de `AssemblerOptionSpec` gegevenslid van het `validateOnly` voorwerp toe te wijzen.
   * Stel de hoeveelheid informatie in die de Assembler-service naar het logbestand schrijft door een tekenreekswaarde toe te wijzen aan het `AssemblerOptionSpec` gegevenslid van het `logLevel` object. methode Bij het valideren van een DDX-document wilt u meer informatie naar het logbestand schrijven dat u helpt bij het validatieproces. Dit betekent dat u de waarde `FINE` of `FINER`. Zie de `AssemblerOptionSpec` klasseverwijzing in de API-naslaggids voor [AEM-formulieren voor informatie over de runtime-opties die u kunt instellen](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Voer de validatie uit.

   Roep de methode van het `AssemblerServiceClient` `invokeDDX` object aan en geef de volgende waarden door:

   * Een `BLOB` object dat het DDX-document vertegenwoordigt.
   * De waarde `null` voor het `Map` object waarin gewoonlijk PDF-documenten worden opgeslagen.
   * Een `AssemblerOptionSpec` object dat uitvoeringsopties opgeeft.
   De `invokeDDX` methode retourneert een `AssemblerResult` object dat informatie bevat die opgeeft of het DDX-document geldig is.

1. Sla de validatieresultaten op in een logbestand.

   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het logbestand en de modus waarin het bestand moet worden geopend. Controleer of de bestandsnaamextensie .xml is.
   * Maak een `BLOB` object dat logboekgegevens opslaat door de waarde van het gegevenslid van het `AssemblerResult` `jobLog` object op te halen.
   * Maak een bytearray waarin de inhoud van het `BLOB` object wordt opgeslagen. Vul de bytearray met de waarde van het `BLOB` veld van het `MTOM` object.
   * Maak een `System.IO.BinaryWriter` object door de constructor ervan aan te roepen en het `System.IO.FileStream` object door te geven.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door de methode van het `System.IO.BinaryWriter` `Write` object aan te roepen en de bytearray door te geven.
   >[!NOTE]
   >
   >Als het DDX-document ongeldig is, `OperationException` wordt er een gegenereerd. Binnen de catch-instructie kunt u de waarde van het `OperationException` lid van het `jobLog` object ophalen.

**Zie ook**

[DDX-documenten valideren](#validating-ddx-documents)

[AEM-formulieren aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
