---
title: Een PDF-document dempen met de API voor webservices
description: Een PDF-document dempen met de API voor vergaderingsservice
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/programmatically_disassembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
role: Developer
exl-id: de2f90ad-5dea-40a0-8c6d-d6b08228310d
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '718'
ht-degree: 0%

---

# Een PDF-document dempen met de webservice-API {#disassemble-a-pdf-document-usingthe-web-service-api}

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

U kunt een PDF-document desassembleren met de API (webservice) van de Assembler-service:

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt wanneer het plaatsen van een de dienstverwijzing: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

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
   * Een `System.IO.FileStream` object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die staat voor de bestandslocatie van het DDX-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` eigenschap met de inhoud van de bytearray.

1. Verwijs naar een document van de PDF om te demonteren.

   * Een `BLOB` object met behulp van de constructor. De `BLOB` wordt gebruikt om het invoerdocument PDF op te slaan. Dit `BLOB` object wordt doorgegeven aan de `invokeOneDocument` als argument.
   * Een `System.IO.FileStream` door de constructor aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het invoerdocument PDF en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` veld de inhoud van de bytearray.
   * Een `MyMapOf_xsd_string_To_xsd_anyType` object. Dit verzamelingsobject wordt gebruikt om de PDF op te slaan die moet worden gedemonteerd.
   * Een `MyMapOf_xsd_string_To_xsd_anyType_Item` object.
   * Wijs een tekenreekswaarde toe die de sleutelnaam vertegenwoordigt aan de `MyMapOf_xsd_string_To_xsd_anyType_Item` object `key` veld. Deze waarde moet overeenkomen met de waarde van het PDF-bronelement dat is opgegeven in het DDX-document.
   * Wijs het `BLOB` object waarin het PDF-document is opgeslagen in het `MyMapOf_xsd_string_To_xsd_anyType_Item` object `value` veld.
   * Voeg de `MyMapOf_xsd_string_To_xsd_anyType_Item` aan `MyMapOf_xsd_string_To_xsd_anyType` object. De `MyMapOf_xsd_string_To_xsd_anyType` object&quot; `Add` en geeft de `MyMapOf_xsd_string_To_xsd_anyType` object.

1. Stel runtime-opties in.

   * Een `AssemblerOptionSpec` object dat uitvoeringsopties opslaat met de constructor ervan.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een waarde toe te wijzen aan een gegevenslid dat tot de `AssemblerOptionSpec` object. Bijvoorbeeld, om de dienst van de Assembler op te dragen om een baan te blijven verwerken wanneer een fout voorkomt, wijs toe `false` aan de `AssemblerOptionSpec` object `failOnError` veld.

1. Haal het PDF-document uit elkaar.

   De `AssemblerServiceClient` object `invokeDDX` en geeft de volgende waarden door:

   * A `BLOB` object dat staat voor het DDX-document dat het PDF-document demonteert
   * De `MyMapOf_xsd_string_To_xsd_anyType` object dat het te demonteren PDF-document bevat
   * An `AssemblerOptionSpec` object dat uitvoeringsopties opgeeft

   De `invokeDDX` methode retourneert een `AssemblerResult` -object dat de taakresultaten en eventuele uitzonderingen bevat die zijn opgetreden.

1. Sla de gedemonteerde PDF-documenten op.

   Voer de volgende handelingen uit om de nieuwe PDF-documenten te verkrijgen:

   * Toegang krijgen tot de `AssemblerResult` object `documents` veld, dat een `Map` -object dat de gedemonteerde PDF-documenten bevat.
   * Doorlopen `Map` om elk resulterend document te verkrijgen. Dan, giet dat serielid `value` een `BLOB`.
   * Extraheer de binaire gegevens die het document van de PDF door tot zijn toegang te hebben vertegenwoordigen `BLOB` object `MTOM` eigenschap. Hiermee wordt een array met bytes geretourneerd die u naar een PDF-bestand kunt schrijven.

**Zie ook**

[PDF-documenten programmatisch demonteren](/help/forms/developing/programmatically-disassembling-pdf-documents.md#programmatically-disassembling-pdf-documents)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
