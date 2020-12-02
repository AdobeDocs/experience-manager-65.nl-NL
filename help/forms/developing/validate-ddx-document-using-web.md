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
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 0%

---


# Een DDX-document valideren met de webservice-API {#validate-a-ddx-document-using-theweb-service-api}

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
   * Maak een `BLOB`-object dat logboekgegevens opslaat door de waarde op te halen van het `AssemblerResult`-gegevenslid van het object.`jobLog`
   * Maak een bytearray waarin de inhoud van het object `BLOB` wordt opgeslagen. Vul de bytearray met de waarde van het veld `BLOB` van het object `MTOM`.
   * Maak een `System.IO.BinaryWriter`-object door de constructor ervan aan te roepen en het object `System.IO.FileStream` door te geven.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door de methode `Write` van het object `System.IO.BinaryWriter` aan te roepen en de bytearray door te geven.

   >[!NOTE]
   >
   >Als het DDX-document ongeldig is, wordt een `OperationException` gegenereerd. Binnen de catch-instructie kunt u de waarde van het `OperationException`-lid van het object ophalen.`jobLog`

**Zie ook**

[DDX-documenten valideren](/help/forms/developing/validating-ddx-documents.md#validating-ddx-documents)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
