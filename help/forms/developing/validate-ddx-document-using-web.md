---
title: Een DDX-document valideren met de webservice-API
seo-title: Validate a DDX document using theweb service API
description: Gebruik de API van de Dienst van de Assembler om een DX- document te bevestigen.
seo-description: Use the Assembler Service API to validate a DDX document.
uuid: f6125746-6138-4e46-a1c4-fb24fd7399c5
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/validating_ddx_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: a6fe91ab-3aa0-4b3d-87c0-6cf69a2c4cc4
role: Developer
exl-id: 069e5b10-ab93-4492-a70d-6a0d462105a6
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 0%

---

# Een DDX-document valideren met de webservice-API {#validate-a-ddx-document-using-theweb-service-api}

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

Valideer een DDX-document met behulp van de API (webservice) voor vergaderingsservice:

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervang localhost door het IP-adres van de formulierserver.

1. Maak een PDF Assembler-client.

   * Een `AssemblerServiceClient` object met de standaardconstructor.
   * Een `AssemblerServiceClient.Endpoint.Address` object gebruiken `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `AssemblerServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `AssemblerServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `AssemblerServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Verwijs naar een bestaand DDX-document.

   * Een `BLOB` object met behulp van de constructor. De `BLOB` wordt gebruikt om het DDX-document op te slaan.
   * Een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het DDX-document en de modus voor het openen van het bestand in vertegenwoordigt.
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

[DDX-documenten valideren](/help/forms/developing/validating-ddx-documents.md#validating-ddx-documents)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
