---
title: Bepalen of documenten PDF/A-compatibel zijn
description: Gebruik de dienst van de Assembler om te bepalen als een document van de PDF PDF/A-Volgzaam gebruikend Java API en de Dienst API van het Web is.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: 096fd2ac-616f-484a-b093-9d98b2f87093
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services,APIs & Integrations
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '2065'
ht-degree: 0%

---

# Bepalen of documenten PDF/A-compatibel zijn {#determining-whether-documents-are-pdf-a-compliant}

U kunt bepalen of een document van PDF PDF/A-Volgzaam is door de dienst van de Assembler te gebruiken. Een PDF/A-document bestaat als een archiefindeling die bedoeld is voor het op lange termijn bewaren van de inhoud van het document. De lettertypen worden ingesloten in het document en het bestand wordt niet gecomprimeerd. Een PDF/A-document is daarom doorgaans groter dan een standaard PDF-document. Een PDF/A-document bevat ook geen audio- en video-inhoud.

De PDF/A-1-specificatie bestaat uit twee conformiteitsniveaus, namelijk A en B. Het grootste verschil tussen de twee niveaus is de logische structuur (toegankelijkheid) ondersteuning, die niet vereist is voor compatibiliteitsniveau B. Ongeacht het compatibiliteitsniveau, dicteert PDF/A-1 dat alle lettertypen zijn ingesloten in het gegenereerde PDF/A-document. Op dit moment wordt alleen PDF/A-1b ondersteund voor validatie (en conversie).

Voor deze bespreking, veronderstel dat het volgende DDX- document wordt gebruikt.

```xml
 <?xml version="1.0" encoding="UTF-8"?>
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
         <DocumentInformation source="Loan.pdf" result="Loan_result.xml">
         <PDFAValidation compliance="PDF/A-1b" resultLevel="Detailed"                       ignoreUnusedResources="true" allowCertificationSignatures="true" />
     </DocumentInformation>
 </DDX>
```

Binnen dit DDX-document geeft het `DocumentInformation` -element de Assembler-service de opdracht om informatie over het invoerdocument PDF te retourneren. Binnen het `DocumentInformation` -element geeft het `PDFAValidation` -element de Assembler-service de opdracht aan te geven of het PDF-invoerdocument voldoet aan PDF/A.

De Assembler-service retourneert informatie die aangeeft of het invoer-PDF-document voldoet aan de PDF/A-standaard in een XML-document dat een `PDFAConformance` -element bevat. Als het invoerdocument PDF PDF/A-compatibel is, is de waarde van het `isCompliant` -kenmerk van het `PDFAConformance` -element `true` . Als het PDF-document niet PDF/A-compatibel is, is de waarde van het `isCompliant` -kenmerk van het `PDFAConformance` -element `false` .

>[!NOTE]
>
>Omdat het DDX-document dat in deze sectie is opgegeven, een `DocumentInformation` -element bevat, retourneert de Assembler-service XML-gegevens in plaats van een PDF-document. Met andere woorden, de Assembler-service kan een PDF-document niet samenstellen of demonteren. Er wordt informatie over het invoerdocument in een XML-document geretourneerd.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Assembler, zie [&#x200B; Verwijzing van de Diensten voor AEM Forms &#x200B;](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Voor meer informatie over een document DDX, zie [&#x200B; de Dienst van de Assembler en de Verwijzing DDX &#x200B;](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Overzicht van de stappen {#summary-of-steps}

Om te bepalen of een document van PDF PDF/A-Volgzaam is, voer de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak een PDF Assembler-client.
1. Verwijs naar een bestaand DDX-document.
1. Verwijs naar een document van PDF dat wordt gebruikt om PDF/A conformiteit te bepalen.
1. Stel runtime-opties in.
1. Haal informatie op over het PDF-document.
1. Sla het geretourneerde XML-document op.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

als AEM Forms wordt geïmplementeerd op een andere ondersteunde J2EE-toepassingsserver dan JBoss, moet u de bestanden adobe-utilities.jar en jbossall-client.jar vervangen door JAR-bestanden die specifiek zijn voor de J2EE-toepassingsserver waarop AEM Forms is geïmplementeerd. Voor informatie over de plaats van alle dossiers van AEM Forms JAR, zie [&#x200B; Inclusief de bibliotheekdossiers van AEM Forms Java &#x200B;](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**creeer een cliënt van de Assembler van de PDF**

Alvorens u programmatically een verrichting van de Assembler kunt uitvoeren, moet u een de dienstcliënt van de Assembler tot stand brengen.

**Verwijzing een bestaand document DDX**

Er moet naar een DDX-document worden verwezen om een Assembler-servicebewerking uit te voeren. Als u wilt bepalen of een invoerdocument voldoet aan de PDF/A-standaard, controleert u of het DDX-document het `PDFAValidation` -element bevat binnen een `DocumentInformation` -element. Het element `PDFAValidation` geeft de Assembler-service de opdracht een XML-document te retourneren dat opgeeft of het invoerdocument PDF PDF/A-compatibel is.

**Verwijzing een document van PDF dat wordt gebruikt om PDF/A compliantie** te bepalen

Er moet naar een PDF-document worden verwezen en dat document moet worden doorgegeven aan de Assembler-service om te bepalen of het PDF-document compatibel is met PDF/A.

**vastgestelde runtime opties**

U kunt runtime opties plaatsen die het gedrag van de dienst van de Assembler controleren terwijl het een baan uitvoert. U kunt bijvoorbeeld een optie instellen die de Assembler-service de opdracht geeft door te gaan met het verwerken van een taak als er een fout optreedt. Voor informatie over de runtime opties die u kunt plaatsen, zie de `AssemblerOptionSpec` klassenverwijzing in [&#x200B; AEM Forms API Verwijzing &#x200B;](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**wint informatie over het document van PDF** terug

Nadat u de de dienstcliënt van de Assembler creeert, van verwijzingen het DX- document, van verwijzingen een interactief document van de PDF, en vastgestelde runtime opties, kunt u de `invokeDDX` verrichting aanhalen. Omdat het DDX-document het `DocumentInformation` -element bevat, retourneert de Assembler-service XML-gegevens in plaats van een PDF-document.

**sparen het teruggekeerde document van XML**

Het XML-document dat door de Assembler-service wordt geretourneerd, geeft aan of het invoer-PDF-document voldoet aan de PDF/A-standaard. Als het invoerdocument bijvoorbeeld niet voldoet aan de PDF/A-standaard, retourneert de Assembler-service een XML-document dat het volgende PDF-element bevat:

```xml
 <PDFAConformance isCompliant="false" compliance="PDF/A-1b" resultLevel="Detailed" ignoreUnusedResources="true" allowCertificationSignatures="true">
```

Sla het XML-document op als een XML-bestand, zodat u het bestand kunt openen en de resultaten kunt bekijken.

**zie ook**

[Bepalen of een document compatibel is met PDF/A met de Java API](/help/forms/developing/determining-whether-documents-pdf-a.md#determine-whether-a-document-is-pdf-a-compliant-using-the-java-api)

[Bepalen of een document compatibel is met PDF/A met de webservice-API](/help/forms/developing/determining-whether-documents-pdf-a.md#determine-whether-a-document-is-pdf-a-compliant-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[PDF-documenten programmatisch samenstellen](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Bepalen of een document compatibel is met PDF/A met de Java API {#determine-whether-a-document-is-pdf-a-compliant-using-the-java-api}

Bepaal of een document van de PDF PDF/A-Volgzaam door de Dienst API van de Assembler (Java) te gebruiken is:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-assembler-client.jar, op in het klassenpad van uw Java-project.

1. Maak een PDF Assembler-client.

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `AssemblerServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Verwijs naar een bestaand DDX-document.

   * Maak een `java.io.FileInputStream` -object dat het DDX-document vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het DDX-bestand aangeeft. Als u wilt bepalen of het PDF-document compatibel is met PDF/A, controleert u of het DDX-document het `PDFAValidation` -element bevat dat zich in een `DocumentInformation` -element bevindt.
   * Maak een `com.adobe.idp.Document` -object door de constructor ervan te gebruiken en het `java.io.FileInputStream` -object door te geven.

1. Verwijs naar een document van PDF dat wordt gebruikt om PDF/A conformiteit te bepalen.

   * Maak een `java.io.FileInputStream` -object door de constructor ervan te gebruiken en de locatie door te geven van een PDF-document dat wordt gebruikt om de conformiteit met PDF/A te bepalen.
   * Maak een `com.adobe.idp.Document` -object met behulp van de constructor en geef het `java.io.FileInputStream` -object door dat het PDF-document bevat.
   * Maak een `java.util.Map` -object dat wordt gebruikt om het invoer-PDF-document op te slaan met behulp van een `HashMap` -constructor.
   * Voeg een item aan het object `java.util.Map` toe door de methode `put` ervan aan te roepen en de volgende argumenten door te geven:

      * Een tekenreekswaarde die de sleutelnaam vertegenwoordigt. Deze waarde moet overeenkomen met de waarde van het bronelement dat is opgegeven in het DDX-document. De waarde van het bronelement in het DDX-document dat in deze sectie wordt geïntroduceerd, is bijvoorbeeld Loan.pdf.
      * Een `com.adobe.idp.Document` -object dat het invoerdocument PDF bevat.

1. Stel runtime-opties in.

   * Maak een `AssemblerOptionSpec` -object dat uitvoeringsopties opslaat met behulp van de bijbehorende constructor.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een methode aan te roepen die tot het `AssemblerOptionSpec` -object behoort. Als u bijvoorbeeld wilt dat de Assembler-service een taak blijft verwerken wanneer een fout optreedt, roept u de methode `setFailOnError` van het object `AssemblerOptionSpec` aan en geeft u deze door `false` .

1. Haal informatie op over het PDF-document.

   Roep de methode `invokeDDX` van het object `AssemblerServiceClient` aan en geef de volgende vereiste waarden door:

   * Een `com.adobe.idp.Document` -object dat het te gebruiken DDX-document vertegenwoordigt
   * Een `java.util.Map` -object dat het invoerbestand PDF bevat dat wordt gebruikt om de PDF/A-compatibiliteit te bepalen
   * Een `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` -object dat de runtime-opties opgeeft

   De methode `invokeDDX` retourneert een `com.adobe.livecycle.assembler.client.AssemblerResult` -object dat XML-gegevens bevat die opgeven of het invoerdocument compatibel is met PDF/A.

1. Sla het geretourneerde XML-document op.

   Voer de volgende handelingen uit om XML-gegevens te verkrijgen die opgeven of het invoer-PDF-document een PDF/A-document is:

   * Roep de methode `getDocuments` van het object `AssemblerResult` aan. Hiermee wordt een `java.util.Map` -object geretourneerd.
   * Doorloop het `java.util.Map` -object totdat u het resulterende `com.adobe.idp.Document` -object vindt.
   * Roep de methode `copyToFile` van het object `com.adobe.idp.Document` aan om het XML-document te extraheren. Zorg ervoor dat u de XML-gegevens opslaat als een XML-bestand.

**zie ook**

[&#x200B; Snel Begin (SOAP wijze): Bepalend of een document volgzaam PDF/A gebruikend Java API &#x200B;](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-determining-whether-a-document-is-pdf-a-compliant-using-the-java-api) (SOAP wijze) is

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Bepalen of een document compatibel is met PDF/A met de webservice-API {#determine-whether-a-document-is-pdf-a-compliant-using-the-web-service-api}

Bepaal of een document van PDF PDF/A-Volgzaam door de Dienst API van de Assembler (Webdienst) te gebruiken is:

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Gebruik de volgende WSDL-definitie: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1` .

   >[!NOTE]
   >
   >Vervang `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een PDF Assembler-client.

   * Maak een `AssemblerServiceClient` -object met de standaardconstructor.
   * Maak een `AssemblerServiceClient.Endpoint.Address` -object met de `System.ServiceModel.EndpointAddress` -constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/AssemblerService?blob=mtom` ). U hoeft het attribuut `lc_version` niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
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
   * Vul het `BLOB` -object door het `MTOM` -veld ervan toe te wijzen met de inhoud van de bytearray.

1. Verwijs naar een document van PDF dat wordt gebruikt om PDF/A conformiteit te bepalen.

   * Maak een `BLOB` -object met behulp van de constructor. Het `BLOB` -object wordt gebruikt om het invoer-PDF-document op te slaan.
   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het PDF-invoerdocument en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `Length` van het object `System.IO.FileStream` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het object `BLOB` door de eigenschap `MTOM` ervan toe te wijzen met de inhoud van de bytearray.
   * Maak een `MyMapOf_xsd_string_To_xsd_anyType` -object. Dit verzamelingsobject wordt gebruikt om het PDF-document op te slaan.
   * Maak een `MyMapOf_xsd_string_To_xsd_anyType_Item` -object.
   * Wijs een tekenreekswaarde toe die de sleutelnaam vertegenwoordigt aan het veld `key` van het `MyMapOf_xsd_string_To_xsd_anyType_Item` -object. Deze waarde moet overeenkomen met de waarde van het PDF-bronelement dat is opgegeven in het DDX-document.
   * Wijs het `BLOB` -object toe dat het PDF-document opslaat in het veld `MyMapOf_xsd_string_To_xsd_anyType_Item` object `value` .
   * Voeg het object `MyMapOf_xsd_string_To_xsd_anyType_Item` toe aan het object `MyMapOf_xsd_string_To_xsd_anyType` . Roep de methode `MyMapOf_xsd_string_To_xsd_anyType` object&#39; `Add` aan en geef het object `MyMapOf_xsd_string_To_xsd_anyType` door.

1. Stel runtime-opties in.

   * Maak een `AssemblerOptionSpec` -object dat uitvoeringsopties opslaat met behulp van de bijbehorende constructor.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een waarde toe te wijzen aan een gegevenslid dat tot het `AssemblerOptionSpec` -object behoort. Als u bijvoorbeeld de Assembler-service wilt instrueren een taak te blijven verwerken wanneer een fout optreedt, wijst u `false` toe aan het gegevenslid van het `AssemblerOptionSpec` object `failOnError` .

1. Haal informatie op over het PDF-document.

   Roep de methode `invoke` van het object `AssemblerServiceService` aan en geef de volgende waarden door:

   * Een `BLOB` -object dat het DDX-document vertegenwoordigt.
   * Het `MyMapOf_xsd_string_To_xsd_anyType` -object dat het invoerdocument PDF bevat. De sleutels ervan moeten overeenkomen met de namen van de bronbestanden van de PDF en de waarden ervan moeten het `BLOB` -object zijn dat overeenkomt met het invoerbestand van de PDF.
   * Een `AssemblerOptionSpec` -object dat uitvoeringsopties opgeeft.

   De methode `invoke` retourneert een `AssemblerResult` -object dat XML-gegevens bevat die opgeven of het invoer-PDF-document een PDF/A-document is.

1. Sla het geretourneerde XML-document op.

   Voer de volgende handelingen uit om XML-gegevens te verkrijgen die opgeven of het invoer-PDF-document een PDF/A-document is:

   * Open het veld `documents` van het `AssemblerResult` -object (een `Map` -object dat de XML-gegevens bevat die opgeven of het invoer-PDF-document een PDF/A-document is).
   * Doorloop het `Map` -object om elk resulterend document te verkrijgen. Vervolgens cast u de waarde van dat arraylid naar een `BLOB` .
   * Haal de binaire gegevens die de XML-gegevens vertegenwoordigen uit het veld `MTOM` van het object `BLOB` . In dit veld wordt een array met bytes opgeslagen waarnaar u kunt schrijven als een XML-bestand.

**zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
