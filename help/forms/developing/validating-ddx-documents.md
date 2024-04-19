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
source-git-commit: a28883778c5e8fb90cbbd0291ded17059ab2ba7e
workflow-type: tm+mt
source-wordcount: '1507'
ht-degree: 0%

---

# DDX-documenten valideren {#validating-ddx-documents}

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

U kunt een DX- document programmatically bevestigen dat door de dienst van de Assembler wordt gebruikt. Met andere woorden, met de API van de Assembler-service kunt u bepalen of een DDX-document geldig is of niet. Als u bijvoorbeeld een upgrade hebt uitgevoerd van een eerdere AEM Forms-versie en u wilt controleren of uw DDX-document geldig is, kunt u dit valideren met de API voor de Assembler-service.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Assembler, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Voor meer informatie over een DDX-document raadpleegt u [De Verwijzing van de AssemblerDienst en DDX](https://www.adobe.com/go/learn_aemforms_ddx_63).

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
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

als AEM Forms wordt geïmplementeerd op een andere ondersteunde J2EE-toepassingsserver dan JBoss, moet u de bestanden adobe-utilities.jar en jbossall-client.jar vervangen door JAR-bestanden die specifiek zijn voor de J2EE-toepassingsserver waarop AEM Forms is geïmplementeerd.

**Een PDF Assembler-client maken**

Alvorens u programmatically een verrichting van de Assembler kunt uitvoeren, moet u een de dienstcliënt van de Assembler tot stand brengen.

**Verwijzen naar een bestaand DDX-document**

Als u een DDX-document wilt valideren, moet u naar een bestaand DDX-document verwijzen.

**Stel runtime-opties in om het DDX-document te valideren**

Wanneer het bevestigen van een DX- document, moet u specifieke runtime opties plaatsen die de dienst van de Assembler opdragen om het DX- document te bevestigen in plaats van het uit te voeren. Ook, kunt u de hoeveelheid informatie verhogen die de dienst van de Assembler aan het logboekdossier schrijft.

**De validatie uitvoeren**

Nadat u de de dienstcliënt van de Assembler creeert, van verwijzingen het DX- document, en vastgestelde runtime opties, kunt u aanhalen `invokeDDX` bewerking om het DDX-document te valideren. Wanneer u het DDX-document valideert, kunt u `null` als de kaartparameter (deze parameter slaat gewoonlijk PDF documenten op die de Assembler vereist om de verrichting(en) uit te voeren die in het DX- document wordt gespecificeerd).

Als de validatie mislukt, wordt een uitzondering gegenereerd en bevat het logbestand details die verklaren waarom het DDX-document ongeldig is, kunnen worden verkregen uit het dialoogvenster `OperationException` -instantie. Zodra voorbij het basisontleden van XML en schema het controleren, dan wordt de bevestiging tegen de specificatie DDX uitgevoerd. Alle fouten die in het DDX-document staan, worden opgegeven in het logbestand.

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

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `AssemblerServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Verwijs naar een bestaand DDX-document.

   * Een `java.io.FileInputStream` een object dat het DDX-document vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het DDX-bestand aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. Stel uitvoeringsopties in om het DDX-document te valideren.

   * Een `AssemblerOptionSpec` object dat uitvoeringsopties opslaat met de constructor ervan.
   * Plaats de runtime optie die de dienst van de Assembler opdraagt om het DX- document te bevestigen door het te roepen `AssemblerOptionSpec` methode setValidateOnly van object en doorgeven `true`.
   * Plaats de hoeveelheid informatie die de dienst van de Assembler aan het logboekdossier schrijft door te roepen `AssemblerOptionSpec` object `getLogLevel` en het doorgeven van een tekenreekswaarde voldoet aan uw vereisten. Wanneer u een DDX-document valideert, wilt u meer informatie naar het logbestand dat u helpt bij het validatieproces. Hierdoor kunt u de waarde doorgeven `FINE` of `FINER`.

1. Voer de validatie uit.

   De `AssemblerServiceClient` object `invokeDDX` en geeft de volgende waarden door:

   * A `com.adobe.idp.Document` object dat het DDX-document vertegenwoordigt.
   * De waarde `null` voor het java.io.Map-object waarin gewoonlijk PDF-documenten worden opgeslagen.
   * A `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` -object dat de runtime-opties opgeeft.

   De `invokeDDX` methode retourneert een `AssemblerResult` object dat informatie bevat die aangeeft of het DDX-document geldig is.

1. Sla de validatieresultaten op in een logbestand.

   * Een `java.io.File` -object en zorg ervoor dat de bestandsnaamextensie .xml is.
   * De `AssemblerResult` object `getJobLog` methode. Deze methode retourneert een `com.adobe.idp.Document` instantie die validatiegegevens bevat.
   * De `com.adobe.idp.Document` object `copyToFile` methode om de inhoud van de `com.adobe.idp.Document` naar het bestand.

   >[!NOTE]
   >
   >Als het DDX-document ongeldig is, `OperationException` wordt gegenereerd. Binnen de catch-instructie kunt u de instructie `OperationException` object `getJobLog` methode.

**Zie ook**

[DDX-documenten valideren](#validating-ddx-documents)

[Snel starten (SOAP-modus): DDX-documenten valideren met de Java API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-validating-ddx-documents-using-the-java-api) (SOAP-modus)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Een DDX-document valideren met de webservice-API {#validate-a-ddx-document-using-the-web-service-api}

Valideer een DDX-document met behulp van de API (webservice) voor vergaderingsservice:

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervang localhost door het IP-adres van de Forms Server.

1. Maak een PDF Assembler-client.

   * Een `AssemblerServiceClient` object met de standaardconstructor.
   * Een `AssemblerServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `AssemblerServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `AssemblerServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `AssemblerServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Verwijs naar een bestaand DDX-document.

   * Een `BLOB` object met behulp van de constructor. De `BLOB` wordt gebruikt om het DDX-document op te slaan.
   * Een `System.IO.FileStream` door de constructor aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het DDX-document en de modus voor het openen van het bestand in vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` eigenschap met de inhoud van de bytearray.

1. Stel uitvoeringsopties in om het DDX-document te valideren.

   * Een `AssemblerOptionSpec` object dat uitvoeringsopties opslaat met de constructor ervan.
   * Plaats de runtime optie die de dienst van de Assembler opdraagt om het Dx- document te bevestigen door de waarde waar aan toe te wijzen `AssemblerOptionSpec` object `validateOnly` lid.
   * Stel de hoeveelheid informatie in die de Assembler-service naar het logbestand schrijft door een tekenreekswaarde toe te wijzen aan de `AssemblerOptionSpec` object `logLevel` lid. methode Bij het valideren van een DDX-document wilt u meer informatie naar het logbestand schrijven dat u helpt bij het validatieproces. Hierdoor kunt u de waarde opgeven `FINE` of `FINER`. Voor informatie over de runtime opties die u kunt plaatsen, zie `AssemblerOptionSpec` klasseverwijzing in [AEM Forms API-naslag](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Voer de validatie uit.

   De `AssemblerServiceClient` object `invokeDDX` en geeft de volgende waarden door:

   * A `BLOB` object dat het DDX-document vertegenwoordigt.
   * De waarde `null` voor de `Map` object waarin gewoonlijk PDF-documenten worden opgeslagen.
   * An `AssemblerOptionSpec` -object dat uitvoeringsopties opgeeft.

   De `invokeDDX` methode retourneert een `AssemblerResult` object dat informatie bevat die aangeeft of het DDX-document geldig is.

1. Sla de validatieresultaten op in een logbestand.

   * Een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het logbestand en de modus voor het openen van het bestand vertegenwoordigt. Controleer of de bestandsnaamextensie .xml is.
   * Een `BLOB` object dat logboekgegevens opslaat door de waarde van de `AssemblerResult` object `jobLog` lid.
   * Maak een bytearray waarin de inhoud van de `BLOB` object. Vul de bytearray met de waarde van de `BLOB` object `MTOM` veld.
   * Een `System.IO.BinaryWriter` object door de constructor aan te roepen en de `System.IO.FileStream` object.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door het `System.IO.BinaryWriter` object `Write` en geeft u de bytearray door.

   >[!NOTE]
   >
   >Als het DDX-document ongeldig is, `OperationException` wordt gegenereerd. Binnen de catch-instructie kunt u de waarde van de instructie `OperationException` object `jobLog` lid.

**Zie ook**

[DDX-documenten valideren](#validating-ddx-documents)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
