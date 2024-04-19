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
source-git-commit: a28883778c5e8fb90cbbd0291ded17059ab2ba7e
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

In dit DDX-document worden de `DocumentInformation` het element draagt de dienst van de Assembler op om informatie over het document van de inputPDF terug te keren. Binnen de `DocumentInformation` element, de `PDFAValidation` het element draagt de dienst van de Assembler op om erop te wijzen of het document van de inputPDF PDF/A-volgzaam is.

De Assembler-service retourneert informatie die aangeeft of het invoerdocument met de PDF PDF/A-compatibel is in een XML-document dat een `PDFAConformance` element. Als het invoerdocument voldoet aan de PDF/A-standaard, wordt de waarde van de PDF `PDFAConformance` element `isCompliant` kenmerk is `true`. Als het PDF-document niet voldoet aan de PDF/A-standaard, wordt de waarde `PDFAConformance` element `isCompliant` kenmerk is `false`.

>[!NOTE]
>
>Omdat het DDX-document dat in deze sectie is opgegeven een `DocumentInformation` -element, retourneert de Assembler-service XML-gegevens in plaats van een PDF-document. Met andere woorden, de Assembler-service kan een PDF-document niet samenstellen of demonteren. Er wordt informatie over het invoerdocument in een XML-document geretourneerd.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Assembler, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Voor meer informatie over een DDX-document raadpleegt u [De Verwijzing van de AssemblerDienst en DDX](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Overzicht van de stappen {#summary-of-steps}

Om te bepalen of een document van PDF PDF/A-Volgzaam is, voer de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak een PDF Assembler-client.
1. Verwijs naar een bestaand DDX-document.
1. Verwijs naar een document van PDF dat wordt gebruikt om PDF/A conformiteit te bepalen.
1. Stel runtime-opties in.
1. Haal informatie op over het PDF-document.
1. Sla het geretourneerde XML-document op.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

als AEM Forms wordt geïmplementeerd op een andere ondersteunde J2EE-toepassingsserver dan JBoss, moet u de bestanden adobe-utilities.jar en jbossall-client.jar vervangen door JAR-bestanden die specifiek zijn voor de J2EE-toepassingsserver waarop AEM Forms is geïmplementeerd. Voor informatie over de locatie van alle AEM Forms JAR-bestanden raadpleegt u [Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Een PDF Assembler-client maken**

Alvorens u programmatically een verrichting van de Assembler kunt uitvoeren, moet u een de dienstcliënt van de Assembler tot stand brengen.

**Verwijzen naar een bestaand DDX-document**

Er moet naar een DDX-document worden verwezen om een Assembler-servicebewerking uit te voeren. Om te bepalen of een document van de inputPDF PDF/A-Volgzaam is, zorg ervoor dat het DDX- document bevat `PDFAValidation` element binnen een `DocumentInformation` element. De `PDFAValidation` het element draagt de dienst van de Assembler op om een document van XML terug te keren dat specificeert of het document van de input PDF PDF/A-volgzaam is.

**Verwijzen naar een PDF-document dat wordt gebruikt om de PDF/A-compatibiliteit te bepalen**

Er moet naar een PDF-document worden verwezen en dat document moet worden doorgegeven aan de Assembler-service om te bepalen of het PDF-document compatibel is met PDF/A.

**Uitvoeringsopties instellen**

U kunt runtime opties plaatsen die het gedrag van de dienst van de Assembler controleren terwijl het een baan uitvoert. U kunt bijvoorbeeld een optie instellen die de Assembler-service de opdracht geeft door te gaan met het verwerken van een taak als er een fout optreedt. Voor informatie over de runtime opties die u kunt plaatsen, zie `AssemblerOptionSpec` klasseverwijzing in [AEM Forms API-naslag](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Informatie ophalen over het PDF-document**

Nadat u de de dienstcliënt van de Assembler creeert, van verwijzingen het DX- document, van verwijzingen een interactief document van de PDF, en vastgestelde runtime opties, kunt u aanhalen `invokeDDX` -bewerking. Omdat het DDX-document de `DocumentInformation` -element, retourneert de Assembler-service XML-gegevens in plaats van een PDF-document.

**Het geretourneerde XML-document opslaan**

Het XML-document dat door de Assembler-service wordt geretourneerd, geeft aan of het invoer-PDF-document voldoet aan de PDF/A-standaard. Als het invoerdocument bijvoorbeeld niet voldoet aan de PDF/A-standaard, retourneert de Assembler-service een XML-document dat het volgende PDF-element bevat:

```xml
 <PDFAConformance isCompliant="false" compliance="PDF/A-1b" resultLevel="Detailed" ignoreUnusedResources="true" allowCertificationSignatures="true">
```

Sla het XML-document op als een XML-bestand, zodat u het bestand kunt openen en de resultaten kunt bekijken.

**Zie ook**

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

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `AssemblerServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Verwijs naar een bestaand DDX-document.

   * Een `java.io.FileInputStream` een object dat het DDX-document vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het DDX-bestand aangeeft. Om te bepalen of het document van de PDF PDF/A-Volgzaam is, zorg ervoor dat het DX- document bevat `PDFAValidation` element dat zich binnen een `DocumentInformation` element.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. Verwijs naar een document van PDF dat wordt gebruikt om PDF/A conformiteit te bepalen.

   * Een `java.io.FileInputStream` object door de constructor ervan te gebruiken en de locatie door te geven van een PDF-document dat wordt gebruikt om de PDF/A-compatibiliteit te bepalen.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object dat het PDF-document bevat.
   * Een `java.util.Map` object dat wordt gebruikt om het invoerdocument PDF op te slaan met een `HashMap` constructor.
   * Een item toevoegen aan de `java.util.Map` object aanroepen `put` en het doorgeven van de volgende argumenten:

      * Een tekenreekswaarde die de sleutelnaam vertegenwoordigt. Deze waarde moet overeenkomen met de waarde van het bronelement dat is opgegeven in het DDX-document. De waarde van het bronelement in het DDX-document dat in deze sectie wordt geïntroduceerd, is bijvoorbeeld Loan.pdf.
      * A `com.adobe.idp.Document` -object dat het invoerdocument PDF bevat.

1. Stel runtime-opties in.

   * Een `AssemblerOptionSpec` object dat uitvoeringsopties opslaat met de constructor ervan.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een methode aan te roepen die tot de `AssemblerOptionSpec` object. Bijvoorbeeld, om de dienst van de Assembler op te dragen om een baan te blijven verwerken wanneer een fout voorkomt, haalt het `AssemblerOptionSpec` object `setFailOnError` methode en doorgeven `false`.

1. Haal informatie op over het PDF-document.

   De `AssemblerServiceClient` object `invokeDDX` en geeft de volgende vereiste waarden door:

   * A `com.adobe.idp.Document` object dat staat voor het te gebruiken DDX-document
   * A `java.util.Map` object dat het invoerbestand PDF bevat dat wordt gebruikt om de PDF/A-compatibiliteit te bepalen
   * A `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` object dat de runtime-opties opgeeft

   De `invokeDDX` methode retourneert een `com.adobe.livecycle.assembler.client.AssemblerResult` object dat XML-gegevens bevat die aangeven of het invoer-PDF-document compatibel is met PDF/A.

1. Sla het geretourneerde XML-document op.

   Voer de volgende handelingen uit om XML-gegevens te verkrijgen die opgeven of het invoer-PDF-document een PDF/A-document is:

   * De `AssemblerResult` object `getDocuments` methode. Dit retourneert een `java.util.Map` object.
   * Doorlopen `java.util.Map` object tot u het resultaat hebt gevonden `com.adobe.idp.Document` object.
   * De `com.adobe.idp.Document` object `copyToFile` methode om het XML-document te extraheren. Zorg ervoor dat u de XML-gegevens opslaat als een XML-bestand.

**Zie ook**

[Snel starten (SOAP-modus): bepalen of een document PDF/A-compatibel is met de Java API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-determining-whether-a-document-is-pdf-a-compliant-using-the-java-api) (SOAP-modus)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Bepalen of een document compatibel is met PDF/A met de webservice-API {#determine-whether-a-document-is-pdf-a-compliant-using-the-web-service-api}

Bepaal of een document van PDF PDF/A-Volgzaam door de Dienst API van de Assembler (Webdienst) te gebruiken is:

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een PDF Assembler-client.

   * Een `AssemblerServiceClient` object met de standaardconstructor.
   * Een `AssemblerServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
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
   * Vul de `BLOB` object door het toe te wijzen `MTOM` veld met de inhoud van de bytearray.

1. Verwijs naar een document van PDF dat wordt gebruikt om PDF/A conformiteit te bepalen.

   * Een `BLOB` object met behulp van de constructor. De `BLOB` wordt gebruikt om het invoerdocument PDF op te slaan.
   * Een `System.IO.FileStream` door de constructor aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het invoerdocument PDF en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` eigenschap met de inhoud van de bytearray.
   * Een `MyMapOf_xsd_string_To_xsd_anyType` object. Dit verzamelingsobject wordt gebruikt om het PDF-document op te slaan.
   * Een `MyMapOf_xsd_string_To_xsd_anyType_Item` object.
   * Wijs een tekenreekswaarde toe die de sleutelnaam vertegenwoordigt aan de `MyMapOf_xsd_string_To_xsd_anyType_Item` object `key` veld. Deze waarde moet overeenkomen met de waarde van het PDF-bronelement dat is opgegeven in het DDX-document.
   * Wijs het `BLOB` object waarin het PDF-document is opgeslagen in het `MyMapOf_xsd_string_To_xsd_anyType_Item` object `value` veld.
   * Voeg de `MyMapOf_xsd_string_To_xsd_anyType_Item` aan `MyMapOf_xsd_string_To_xsd_anyType` object. De `MyMapOf_xsd_string_To_xsd_anyType` object&#39; `Add` en geeft de `MyMapOf_xsd_string_To_xsd_anyType` object.

1. Stel runtime-opties in.

   * Een `AssemblerOptionSpec` object dat uitvoeringsopties opslaat met de constructor ervan.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een waarde toe te wijzen aan een gegevenslid dat tot de `AssemblerOptionSpec` object. Bijvoorbeeld, om de dienst van de Assembler op te dragen om een baan te blijven verwerken wanneer een fout voorkomt, wijs toe `false` aan de `AssemblerOptionSpec` object `failOnError` lid.

1. Haal informatie op over het PDF-document.

   De `AssemblerServiceService` object `invoke` en geeft de volgende waarden door:

   * A `BLOB` object dat het DDX-document vertegenwoordigt.
   * De `MyMapOf_xsd_string_To_xsd_anyType` -object dat het invoerdocument PDF bevat. Zijn sleutels moeten de namen van de PDF brondossiers aanpassen, en zijn waarden moeten zijn `BLOB` -object dat overeenkomt met het invoerbestand PDF.
   * An `AssemblerOptionSpec` -object dat uitvoeringsopties opgeeft.

   De `invoke` methode retourneert een `AssemblerResult` object dat XML-gegevens bevat die opgeven of het invoer-PDF-document een PDF/A-document is.

1. Sla het geretourneerde XML-document op.

   Voer de volgende handelingen uit om XML-gegevens te verkrijgen die opgeven of het invoer-PDF-document een PDF/A-document is:

   * Toegang krijgen tot de `AssemblerResult` object `documents` veld, dat een `Map` -object dat de XML-gegevens bevat die aangeven of het invoer-PDF-document een PDF/A-document is.
   * Doorlopen `Map` om elk resulterend document te verkrijgen. Dan, giet de waarde van dat serielid aan een `BLOB`.
   * Extraheer de binaire gegevens die de gegevens van XML door tot zijn toegang te hebben vertegenwoordigen vertegenwoordigen `BLOB` object `MTOM` veld. In dit veld wordt een array met bytes opgeslagen waarnaar u kunt schrijven als een XML-bestand.

**Zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
