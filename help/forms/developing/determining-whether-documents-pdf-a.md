---
title: Bepalen of documenten PDF/A-compatibel zijn
seo-title: Bepalen of documenten PDF/A-compatibel zijn
description: Gebruik de Assembler-service om te bepalen of een PDF-document compatibel is met PDF/A met de API voor Java API en Web Service.
seo-description: Gebruik de Assembler-service om te bepalen of een PDF-document compatibel is met PDF/A met de API voor Java API en Web Service.
uuid: 4e9d8c8f-2153-411b-9c4b-2d14b3c8f4bb
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: c429d6e1-7847-43c8-bf75-cb0078dbb9d5
role: Developer
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '2110'
ht-degree: 0%

---


# Bepalen of documenten PDF/A-compatibel zijn {#determining-whether-documents-are-pdf-a-compliant}

Met de Assembler-service kunt u bepalen of een PDF-document compatibel is met PDF/A. Een PDF/A-document bestaat als een archiefindeling die is bedoeld voor het op lange termijn bewaren van de inhoud van het document. De lettertypen worden ingesloten in het document en het bestand wordt niet gecomprimeerd. Een PDF/A-document is daarom doorgaans groter dan een standaard PDF-document. Een PDF/A-document bevat ook geen audio- en video-inhoud.

De PDF/A-1-specificatie bestaat uit twee conformiteitsniveaus, namelijk A en B. Het grootste verschil tussen de twee niveaus is de logische structuur (toegankelijkheid) die niet vereist is voor niveau B. PDF/A-1 schrijft voor dat alle fonts in het gegenereerde PDF/A-document worden ingesloten, ongeacht het compatibiliteitsniveau. Momenteel wordt alleen PDF/A-1b ondersteund voor validatie (en conversie).

Voor deze bespreking, veronderstel dat het volgende DDX- document wordt gebruikt.

```xml
 <?xml version="1.0" encoding="UTF-8"?>
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
         <DocumentInformation source="Loan.pdf" result="Loan_result.xml">
         <PDFAValidation compliance="PDF/A-1b" resultLevel="Detailed"                       ignoreUnusedResources="true" allowCertificationSignatures="true" />
     </DocumentInformation>
 </DDX>
```

Binnen dit DDX-document geeft het element `DocumentInformation` de Assembler-service de opdracht om informatie over het invoer-PDF-document te retourneren. In het `DocumentInformation`-element geeft het `PDFAValidation`-element de Assembler-service de opdracht aan te geven of het PDF-invoerdocument PDF/A-compatibel is.

De Assembler-service geeft informatie die aangeeft of het invoer-PDF-document PDF/A-compatibel is in een XML-document dat een element `PDFAConformance` bevat. Als het invoer-PDF-document PDF/A-compatibel is, is de waarde van het `PDFAConformance`-kenmerk van het element `isCompliant` `true`. Als het PDF-document niet PDF/A-compatibel is, is de waarde van het `PDFAConformance`-kenmerk van het element `isCompliant` `false`.

>[!NOTE]
>
>Omdat het DDX-document dat in deze sectie wordt opgegeven een `DocumentInformation`-element bevat, retourneert de Assembler-service XML-gegevens in plaats van een PDF-document. Met andere woorden, de Assembler-service kan een PDF-document niet samenstellen of demonteren. wordt informatie over het invoer-PDF-document in een XML-document geretourneerd.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Assembler, zie [de Verwijzing van de Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Voor meer informatie over een DX- document, zie [de Dienst van de Assembler en DX Verwijzing](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Overzicht van stappen {#summary-of-steps}

Voer de volgende taken uit om te bepalen of een PDF-document compatibel is met PDF/A:

1. Inclusief projectbestanden.
1. Maak een PDF Assembler-client.
1. Verwijs naar een bestaand DDX-document.
1. Verwijs naar een PDF-document dat wordt gebruikt om de compatibiliteit met PDF/A te bepalen.
1. Stel runtime-opties in.
1. Informatie over het PDF-document ophalen.
1. Sla het geretourneerde XML-document op.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

als AEM Forms wordt geïmplementeerd op een andere ondersteunde J2EE-toepassingsserver dan JBoss, moet u de bestanden adobe-utilities.jar en jbossall-client.jar vervangen door JAR-bestanden die specifiek zijn voor de J2EE-toepassingsserver waarop AEM Forms is geïmplementeerd. Zie [Including AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files) voor informatie over de locatie van alle AEM Forms JAR-bestanden.

**Een PDF Assembler-client maken**

Alvorens u programmatically een verrichting van de Assembler kunt uitvoeren, moet u een de dienstcliënt van de Assembler tot stand brengen.

**Verwijzen naar een bestaand DDX-document**

Er moet naar een DDX-document worden verwezen om een Assembler-servicebewerking uit te voeren. Om te bepalen of een invoer-PDF-document PDF/A-compatibel is, moet u ervoor zorgen dat het DDX-document het element `PDFAValidation` in een element `DocumentInformation` bevat. Het element `PDFAValidation` instrueert de Assembler-service een XML-document te retourneren dat aangeeft of het invoer-PDF-document compatibel is met PDF/A.

**Verwijzen naar een PDF-document dat wordt gebruikt om de compatibiliteit met PDF/A te bepalen**

Er moet naar een PDF-document worden verwezen en dat document moet worden doorgegeven aan de Assembler-service om te bepalen of het PDF-document compatibel is met PDF/A.

**Uitvoeringsopties instellen**

U kunt runtime opties plaatsen die het gedrag van de dienst van de Assembler controleren terwijl het een baan uitvoert. U kunt bijvoorbeeld een optie instellen die de Assembler-service de opdracht geeft door te gaan met het verwerken van een taak als er een fout optreedt. Zie de `AssemblerOptionSpec`-klasseverwijzing in [AEM Forms API Reference](https://www.adobe.com/go/learn_aemforms_javadocs_63_en) voor informatie over de runtime-opties die u kunt instellen.

**Informatie over het PDF-document ophalen**

Nadat u de Assembler-serviceclient hebt gemaakt, naar het DDX-document verwijst, naar een interactief PDF-document verwijst en runtime-opties hebt ingesteld, kunt u de `invokeDDX`-bewerking activeren. Omdat het DDX-document het element `DocumentInformation` bevat, retourneert de Assembler-service XML-gegevens in plaats van een PDF-document.

**Het geretourneerde XML-document opslaan**

In het XML-document dat door de Assembler-service wordt geretourneerd, wordt aangegeven of het invoer-PDF-document compatibel is met PDF/A. Als het PDF-invoerdocument bijvoorbeeld niet PDF/A-compatibel is, retourneert de Assembler-service een XML-document dat het volgende element bevat:

```xml
 <PDFAConformance isCompliant="false" compliance="PDF/A-1b" resultLevel="Detailed" ignoreUnusedResources="true" allowCertificationSignatures="true">
```

Sla het XML-document op als een XML-bestand zodat u het bestand kunt openen en de resultaten kunt bekijken.

**Zie ook**

[Bepalen of een document compatibel is met PDF/A met de Java API](/help/forms/developing/determining-whether-documents-pdf-a.md#determine-whether-a-document-is-pdf-a-compliant-using-the-java-api)

[Bepalen of een document PDF/A-compatibel is met de webservice-API](/help/forms/developing/determining-whether-documents-pdf-a.md#determine-whether-a-document-is-pdf-a-compliant-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[PDF-documenten programmatisch samenstellen](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Bepalen of een document PDF/A-compatibel is met de Java API {#determine-whether-a-document-is-pdf-a-compliant-using-the-java-api}

Bepaal of een PDF-document PDF/A-compatibel is met de API (Java) voor vergaderingsservice:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-assembler-client.jar, op in het klassenpad van uw Java-project.

1. Maak een PDF Assembler-client.

   * Maak een `ServiceClientFactory`-object dat verbindingseigenschappen bevat.
   * Maak een `AssemblerServiceClient`-object door de constructor ervan te gebruiken en het object `ServiceClientFactory` door te geven.

1. Verwijs naar een bestaand DDX-document.

   * Maak een `java.io.FileInputStream`-object dat het DDX-document vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het DDX-bestand aangeeft. Als u wilt bepalen of het PDF-document compatibel is met PDF/A, controleert u of het DDX-document het element `PDFAValidation` bevat dat zich in een element `DocumentInformation` bevindt.
   * Maak een `com.adobe.idp.Document`-object door de constructor ervan te gebruiken en het object `java.io.FileInputStream` door te geven.

1. Verwijs naar een PDF-document dat wordt gebruikt om de compatibiliteit met PDF/A te bepalen.

   * Maak een `java.io.FileInputStream`-object door de constructor ervan te gebruiken en de locatie door te geven van een PDF-document dat wordt gebruikt om de compatibiliteit met PDF/A te bepalen.
   * Maak een `com.adobe.idp.Document`-object door de constructor ervan te gebruiken en het object `java.io.FileInputStream` met het PDF-document door te geven.
   * Maak een `java.util.Map`-object dat wordt gebruikt om het invoer-PDF-document op te slaan met behulp van een `HashMap`-constructor.
   * Voeg een item aan het object `java.util.Map` toe door de methode `put` ervan aan te roepen en de volgende argumenten door te geven:

      * Een tekenreekswaarde die de sleutelnaam vertegenwoordigt. Deze waarde moet overeenkomen met de waarde van het bronelement dat is opgegeven in het DDX-document. De waarde van het bronelement in het DDX-document dat in deze sectie wordt geïntroduceerd, is bijvoorbeeld Loan.pdf.
      * Een `com.adobe.idp.Document`-object dat het invoer-PDF-document bevat.

1. Stel runtime-opties in.

   * Maak een `AssemblerOptionSpec`-object dat uitvoeringsopties opslaat met de constructor ervan.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een methode aan te roepen die tot het object `AssemblerOptionSpec` behoort. Bijvoorbeeld, om de dienst van de Assembler op te dragen om een baan te blijven verwerken wanneer een fout voorkomt, haalt de `AssemblerOptionSpec` methode `setFailOnError` van objecten aan en gaat `false` over.

1. Informatie over het PDF-document ophalen.

   Roep de methode `invokeDDX` van het object `AssemblerServiceClient` aan en geef de volgende vereiste waarden door:

   * Een `com.adobe.idp.Document`-object dat het te gebruiken DDX-document vertegenwoordigt
   * Een `java.util.Map`-object dat het invoer-PDF-bestand bevat dat wordt gebruikt om de compatibiliteit met PDF/A te bepalen
   * Een `com.adobe.livecycle.assembler.client.AssemblerOptionSpec`-object dat de runtime-opties opgeeft

   De methode `invokeDDX` retourneert een `com.adobe.livecycle.assembler.client.AssemblerResult`-object dat XML-gegevens bevat die aangeven of het invoer-PDF-document compatibel is met PDF/A.

1. Sla het geretourneerde XML-document op.

   Voer de volgende handelingen uit om XML-gegevens te verkrijgen die aangeven of het invoer-PDF-document een PDF/A-document is:

   * Roep de methode `AssemblerResult` van het object `getDocuments` aan. Dit retourneert een `java.util.Map`-object.
   * Doorloop het object `java.util.Map` totdat u het resulterende object `com.adobe.idp.Document` hebt gevonden.
   * Roep de methode `com.adobe.idp.Document` van het object `copyToFile` aan om het XML-document te extraheren. Zorg ervoor dat u de XML-gegevens opslaat als een XML-bestand.

**Zie ook**

[Snel starten (SOAP-modus): Bepalen of een document compatibel is met PDF/A met behulp van de Java API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-determining-whether-a-document-is-pdf-a-compliant-using-the-java-api)  (SOAP-modus)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Bepaal of een document PDF/A-compatibel is met de webservice-API {#determine-whether-a-document-is-pdf-a-compliant-using-the-web-service-api}

Bepaal of een PDF-document PDF/A-compatibel is met behulp van de API (webservice) van de Assembler Service:

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervang `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een PDF Assembler-client.

   * Maak een `AssemblerServiceClient`-object met de standaardconstructor.
   * Maak een `AssemblerServiceClient.Endpoint.Address`-object met de constructor `System.ServiceModel.EndpointAddress`. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). U hoeft het `lc_version`-kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
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
   * Vul het `BLOB`-object door het `MTOM`-veld toe te wijzen met de inhoud van de bytearray.

1. Verwijs naar een PDF-document dat wordt gebruikt om de compatibiliteit met PDF/A te bepalen.

   * Maak een `BLOB`-object met de constructor ervan. Met het object `BLOB` wordt het invoer-PDF-document opgeslagen.
   * Maak een `System.IO.FileStream`-object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het invoer-PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `System.IO.FileStream` van het object `Length` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het object `BLOB` door de eigenschap `MTOM` ervan toe te wijzen met de inhoud van de bytearray.
   * Maak een `MyMapOf_xsd_string_To_xsd_anyType`-object. Dit verzamelingsobject wordt gebruikt om het PDF-document op te slaan.
   * Maak een `MyMapOf_xsd_string_To_xsd_anyType_Item`-object.
   * Wijs een tekenreekswaarde toe die de toetsnaam vertegenwoordigt aan het veld `key` van het `MyMapOf_xsd_string_To_xsd_anyType_Item`-object. Deze waarde moet overeenkomen met de waarde van het PDF-bronelement dat is opgegeven in het DDX-document.
   * Wijs het `BLOB`-object toe dat het PDF-document opslaat in het veld `MyMapOf_xsd_string_To_xsd_anyType_Item` van het `value`-object.
   * Voeg het object `MyMapOf_xsd_string_To_xsd_anyType_Item` toe aan het object `MyMapOf_xsd_string_To_xsd_anyType`. Roep `MyMapOf_xsd_string_To_xsd_anyType` object&#39; `Add` methode aan en geef het object `MyMapOf_xsd_string_To_xsd_anyType` door.

1. Stel runtime-opties in.

   * Maak een `AssemblerOptionSpec`-object dat uitvoeringsopties opslaat met de constructor ervan.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een waarde toe te wijzen aan een gegevenslid dat tot het object `AssemblerOptionSpec` behoort. Bijvoorbeeld, om de dienst van de Assembler op te dragen om een baan te blijven verwerken wanneer een fout voorkomt, wijs `false` aan `AssemblerOptionSpec` het gegevenslid van `failOnError` van het voorwerp toe.

1. Informatie over het PDF-document ophalen.

   Roep de methode `invoke` van het object `AssemblerServiceService` aan en geef de volgende waarden door:

   * Een `BLOB`-object dat het DDX-document vertegenwoordigt.
   * Het `MyMapOf_xsd_string_To_xsd_anyType`-object dat het invoer-PDF-document bevat. De sleutels ervan moeten overeenkomen met de namen van de PDF-bronbestanden en de waarden ervan moeten overeenkomen met het `BLOB`-object dat overeenkomt met het invoer-PDF-bestand.
   * Een `AssemblerOptionSpec`-object dat uitvoeringsopties opgeeft.

   De methode `invoke` retourneert een `AssemblerResult`-object dat XML-gegevens bevat die opgeven of het invoer-PDF-document een PDF/A-document is.

1. Sla het geretourneerde XML-document op.

   Voer de volgende handelingen uit om XML-gegevens te verkrijgen die aangeven of het invoer-PDF-document een PDF/A-document is:

   * Open het veld `AssemblerResult` van het object `documents`. Dit is een object `Map` dat de XML-gegevens bevat die aangeven of het invoer-PDF-document een PDF/A-document is.
   * Doorloop het object `Map` om elk resulterend document te verkrijgen. Vervolgens cast u de waarde van dat arraylid naar een `BLOB`.
   * Extraheer de binaire gegevens die de XML-gegevens vertegenwoordigen door het veld `MTOM` van het object te openen. `BLOB` In dit veld wordt een array met bytes opgeslagen waarnaar u kunt schrijven als een XML-bestand.

**Zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
