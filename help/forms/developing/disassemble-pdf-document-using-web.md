---
title: Een PDF-document deassembleren met de webservice-API
seo-title: Een PDF-document deassembleren met de webservice-API
description: 'null'
seo-description: 'null'
uuid: d6283dc5-e333-49d0-abde-1d390662f4fe
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/programmatically_disassembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 49584fb4-8c3a-4d73-acd6-0879a67f6093
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Een PDF-document deassembleren met de webservice-API {#disassemble-a-pdf-document-usingthe-web-service-api}

U kunt een PDF-document desassembleren met de API (webservice) voor de Assembler-service:

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt wanneer het plaatsen van een de dienstverwijzing: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

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
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die staat voor de bestandslocatie van het DDX-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de methode van het `System.IO.FileStream` `Read` object aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` object door de `MTOM` eigenschap ervan toe te wijzen met de inhoud van de bytearray.

1. Verwijs naar een PDF-document dat u wilt demonteren.

   * Maak een `BLOB` object met de constructor ervan. Het `BLOB` object wordt gebruikt om het invoer-PDF-document op te slaan. Dit `BLOB` object wordt als een argument `invokeOneDocument` aan het object doorgegeven.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het invoer-PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de methode van het `System.IO.FileStream` `Read` object aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` object door het `MTOM` veld ervan de inhoud van de bytearray toe te wijzen.
   * Create a `MyMapOf_xsd_string_To_xsd_anyType` object. Met dit verzamelingsobject wordt de PDF opgeslagen om te demonteren.
   * Create a `MyMapOf_xsd_string_To_xsd_anyType_Item` object.
   * Wijs een tekenreekswaarde toe die de sleutelnaam vertegenwoordigt aan het `MyMapOf_xsd_string_To_xsd_anyType_Item` veld van het `key` object. Deze waarde moet overeenkomen met de waarde van het PDF-bronelement dat is opgegeven in het DDX-document.
   * Wijs het `BLOB` object waarin het PDF-document is opgeslagen, toe aan het `MyMapOf_xsd_string_To_xsd_anyType_Item` veld van het `value` object.
   * Voeg het `MyMapOf_xsd_string_To_xsd_anyType_Item` object toe aan het `MyMapOf_xsd_string_To_xsd_anyType` object. Roep de methode van het `MyMapOf_xsd_string_To_xsd_anyType` object aan `Add` en geef het `MyMapOf_xsd_string_To_xsd_anyType` object door.

1. Stel runtime-opties in.

   * Maak een `AssemblerOptionSpec` object dat uitvoeringsopties opslaat met de constructor ervan.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een waarde toe te wijzen aan een gegevenslid dat tot het `AssemblerOptionSpec` object behoort. Als u bijvoorbeeld de Assembler-service wilt instrueren een taak te blijven verwerken wanneer een fout optreedt, wijst u `false` de taak toe aan het `AssemblerOptionSpec` veld van het `failOnError` object.

1. Het PDF-document demonteren.

   Roep de methode van het `AssemblerServiceClient` `invokeDDX` object aan en geef de volgende waarden door:

   * Een `BLOB` object dat staat voor het DDX-document dat het PDF-document demonteert
   * Het `MyMapOf_xsd_string_To_xsd_anyType` object dat het PDF-document bevat dat moet worden gedeassembleerd
   * Een `AssemblerOptionSpec` object dat uitvoeringsopties opgeeft
   De `invokeDDX` methode retourneert een `AssemblerResult` object dat de taakresultaten en eventuele uitzonderingen bevat die zich hebben voorgedaan.

1. Sla de gedemonteerde PDF-documenten op.

   Voer de volgende handelingen uit om de nieuwe PDF-documenten te verkrijgen:

   * Open het `AssemblerResult` veld van het `documents` object. Dit is een `Map` object dat de gedemonteerde PDF-documenten bevat.
   * Doorloop het `Map` object om elk resulterend document te verkrijgen. Dan, giet dat serielid `value` aan een `BLOB`.
   * Pak de binaire gegevens die het PDF-document vertegenwoordigen, uit door de `BLOB` eigenschap van het `MTOM` object te openen. Hiermee wordt een array met bytes geretourneerd die u naar een PDF-bestand kunt schrijven.

**Zie ook**

[PDF-documenten programmatisch demonteren](/help/forms/developing/programmatically-disassembling-pdf-documents.md#programmatically-disassembling-pdf-documents)

[AEM-formulieren aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
