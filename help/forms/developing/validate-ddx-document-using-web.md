---
title: Een DDX-document valideren met de webservice-API
seo-title: Een DDX-document valideren met de webservice-API
description: 'null'
seo-description: 'null'
uuid: f6125746-6138-4e46-a1c4-fb24fd7399c5
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/validating_ddx_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: a6fe91ab-3aa0-4b3d-87c0-6cf69a2c4cc4
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Een DDX-document valideren met de webservice-API {#validate-a-ddx-document-using-theweb-service-api}

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

[DDX-documenten valideren](/help/forms/developing/validating-ddx-documents.md#validating-ddx-documents)

[AEM-formulieren aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
