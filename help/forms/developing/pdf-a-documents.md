---
title: Werken met PDF/A-documenten
description: Gebruik de DocConverter-service om te bepalen of een PDF-document een PDF/A-document is en om PDF-documenten om te zetten in PDF/A-documenten.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: 966c3554-25df-4467-866e-11c43cc15b58
solution: Experience Manager, Experience Manager Forms
source-git-commit: 872e2de411f51b5f0b26a2ff47cb49f01313d39f
workflow-type: tm+mt
source-wordcount: '2331'
ht-degree: 0%

---

# Werken met PDF/A-documenten {#working-with-pdf-a-documents}

**Informatie over de DocConverter-service**

De DocConverter-service kan PDF-documenten omzetten in PDA/A-documenten. U kunt deze taken uitvoeren met deze service:

* PDF-documenten converteren naar PDF/A-documenten. (Zie [Documenten converteren naar PDF/A-documenten](pdf-a-documents.md#converting-documents-to-pdf-a-documents).)
* Bepaal of PDF-documenten PDF/A-documenten zijn. (Zie [Programmaticaal bepalen van PDF/A-compatibiliteit](pdf-a-documents.md#programmatically-determining-pdf-a-compliancy).)

>[!NOTE]
>
>Voor meer informatie over de dienst DocConverter, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Documenten converteren naar PDF/A-documenten {#converting-documents-to-pdf-a-documents}

Met de DocConverter-service kunt u een PDF-document omzetten in een PDF/A-document. Omdat PDF/A een archiefindeling is voor langdurige bewaring van de inhoud van het document, worden alle lettertypen ingesloten en wordt het bestand niet gecomprimeerd. Een PDF/A-document is daarom doorgaans groter dan een standaard PDF-document. Een PDF/A-document bevat ook geen audio- en video-inhoud. Voordat u een PDF-document omzet in een PDF/A-document, moet u controleren of het PDF-document geen PDF/A-document is.

De PDF/A-1-specificatie bestaat uit twee conformiteitsniveaus, namelijk A en B. Het belangrijkste verschil tussen beide is de logische structuur (toegankelijkheid) die niet vereist is voor compatibiliteitsniveau B. Ongeacht het compatibiliteitsniveau, dicteert PDF/A-1 dat alle lettertypen zijn ingesloten in het gegenereerde PDF/A-document. Op dit moment wordt alleen PDF/A-1b ondersteund voor validatie (en conversie).

Hoewel PDF/A de standaard is voor het archiveren van PDF-documenten, is het niet verplicht dat PDF/A wordt gebruikt voor archivering als een standaard PDF-document voldoet aan de eisen van uw bedrijf. Het doel van de PDF/A-standaard is een PDF-bestand te maken dat is bedoeld voor archiverings- en documentbewaardoeleinden op lange termijn.

>[!NOTE]
>
>Voor meer informatie over de dienst DocConverter, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary-of-steps}

Voer de volgende stappen uit om een PDF-document om te zetten in een PDF/A-document:

1. Inclusief projectbestanden.
1. Een DocConvert-client maken
1. Verwijzen naar een PDF-document dat moet worden omgezet in een PDF/A-document.
1. Trackinggegevens instellen.
1. Converteer het document.
1. Sla het PDF/A-document op.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-docconverter-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)

Voor informatie over de locatie van deze JAR-bestanden raadpleegt u [Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Een DocConvert-client maken**

Voordat u een DocConverter-bewerking programmatisch kunt uitvoeren, moet u een DocConverter-client maken. Als u de Java API gebruikt, maakt u een `DocConverterServiceClient` object. Als u de DocConverter-webservice-API gebruikt, maakt u een `DocConverterServiceService` object.

**Verwijzen naar een PDF-document dat moet worden omgezet in een PDF/A-document**

Hiermee wordt een PDF-document opgehaald dat naar een PDF/A-document moet worden geconverteerd. Als u probeert een PDF-document, zoals een Acrobat-formulier, om te zetten in een PDF/A-document, veroorzaakt u een uitzondering.

**Trackinggegevens instellen**

U kunt een runtime optie instellen die bepaalt hoeveel informatie tijdens het conversieproces wordt bijgehouden. Namelijk kunt u negen verschillende niveaus plaatsen die hoeveel informatie specificeren de dienst DocConverter volgt wanneer het een document van de PDF in een document PDF/A omzet.

**Het document converteren**

Nadat u de DocConverter dienstcliënt creeert, verwijs het document van de PDF om te zetten en de runtime optie te plaatsen die specificeert hoeveel informatie wordt gevolgd, kunt u het document van de PDF in een PDF/A- document omzetten.

**Het PDF/A-document opslaan**

U kunt het PDF/A-document opslaan als een PDF-bestand.

**Zie ook**

[Documenten converteren naar PDF/A-documenten met de Java API](pdf-a-documents.md#convert-documents-to-pdf-a-documents-using-the-java-api)

[Documenten converteren naar PDF/A-documenten met de API voor webservices](pdf-a-documents.md#convert-documents-to-pdf-a-documents-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Programmaticaal bepalen van PDF/A-compatibiliteit](pdf-a-documents.md#programmatically-determining-pdf-a-compliancy)

### Documenten converteren naar PDF/A-documenten met de Java API {#convert-documents-to-pdf-a-documents-using-the-java-api}

Een PDF-document converteren naar een PDF/A-document met de Java API:

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-docconverter-client.jar, op in het klassenpad van uw Java-project.

1. Een DocConvert-client maken

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `DocConverterServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Verwijzen naar een PDF-document dat moet worden omgezet in een PDF/A-document

   * Een `java.io.FileInputStream` object dat staat voor het PDF-document dat moet worden geconverteerd met de constructor ervan en dat een tekenreekswaarde doorgeeft die de locatie van het PDF-bestand aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. Trackinggegevens instellen

   * Een `PDFAConversionOptionSpec` object met behulp van de constructor.
   * Stel het niveau voor het bijhouden van gegevens in door het `PDFAConversionOptionSpec` object `setLogLevel` methode en het overgaan van een koordwaarde die het volgende niveau specificeert. Geef bijvoorbeeld de waarde door `FINE`. Voor informatie over de verschillende waarden raadpleegt u de `setLogLevel` in de [AEM Forms API-naslag](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Het document converteren

   Zet het PDF-document om in een PDF/A-document door het `DocConverterServiceClient` object `toPDFA` en geeft de volgende waarden door:

   * De `com.adobe.idp.Document` object dat het te converteren PDF-document bevat
   * De `PDFAConversionOptionSpec` object dat trackinggegevens opgeeft

   De `toPDFA` methode retourneert een `PDFAConversionResult` object dat het PDF/A-document bevat.

1. Het PDF/A-document opslaan

   * Haal het PDF/A-document op door het `PDFAConversionResult` object `getPDFA` methode. Deze methode retourneert een `com.adobe.idp.Document` object dat staat voor het PDF/A-document.
   * Een `java.io.File` object dat het PDF/A-bestand vertegenwoordigt. Controleer of de bestandsnaamextensie .pdf is.
   * Het bestand vullen met PDF/A-gegevens door het `com.adobe.idp.Document` object `copyToFile` en het doorgeven van de `java.io.File` object.

**Zie ook**

[Werken met PDF/A-documenten](pdf-a-documents.md#working-with-pdf-a-documents)

[Snel starten (SOAP modus): Een document converteren naar een PDF/A-document met de Java API](/help/forms/developing/docconverter-service-java-api-quick.md#quick-start-soap-mode-converting-a-document-to-a-pdf-a-document-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Documenten converteren naar PDF/A-documenten met de API voor webservices {#convert-documents-to-pdf-a-documents-using-the-web-service-api}

Een PDF-document converteren naar een PDF/A-document met de DocConverter-API (webservice):

1. Projectbestanden opnemen

   * Creeer een Microsoft .NET cliëntassemblage die DocConverter WSDL verbruikt.
   * Verwijs naar de Microsoft .NET cliëntassemblage.

1. Een DocConvert-client maken

   * Gebruikend de de cliëntassemblage van Microsoft .NET, creeer een `DocConverterServiceService` object door de standaardconstructor aan te roepen.
   * Stel de `DocConverterServiceService` object `Credentials` lid met gegevens `System.Net.NetworkCredential` waarde die de gebruikersnaam en wachtwoordwaarde specificeert.

1. Verwijzen naar een PDF-document dat moet worden omgezet in een PDF/A-document

   * Een `BLOB` object met behulp van de constructor. De `BLOB` wordt gebruikt om het PDF-document op te slaan dat wordt geconverteerd naar een PDF/A-document.
   * Een `System.IO.FileStream` door de constructor aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het PDF-document en de modus voor het openen van het bestand in vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door het toe te wijzen `binaryData` eigenschap met de inhoud van de bytearray.

1. Trackinggegevens instellen

   * Een `PDFAConversionOptionSpec` object met behulp van de constructor.
   * Stel het niveau voor het bijhouden van gegevens in door een waarde toe te wijzen die het niveau voor bijhouden opgeeft voor de `PDFAConversionOptionSpec` object `logLevel` lid. Wijs bijvoorbeeld de waarde toe `FINE` aan dit gegevenslid.

1. Het document converteren

   Zet het PDF-document om in een PDF/A-document door het `DocConverterServiceService` object `toPDFA` en geeft de volgende waarden door:

   * De `BLOB` object dat het te converteren PDF-document bevat
   * De `PDFAConversionOptionSpec` object dat trackinggegevens opgeeft

   De `toPDFA` methode retourneert een `PDFAConversionResult` object dat het PDF/A-document bevat.

1. Het PDF/A-document opslaan

   * Een `BLOB` object dat het PDF/A-document opslaat door de waarde van het `PDFAConversionResult` object `PDFADocument` lid.
   * Maak een bytearray waarin de inhoud van de `BLOB` object dat is geretourneerd met het gereedschap `PDFAConversionResult` object. Vul de bytearray met de waarde van de `BLOB` object `binaryData` lid.
   * Een `System.IO.FileStream` door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het PDF/A-document vertegenwoordigt.
   * Een `System.IO.BinaryWriter` object door de constructor aan te roepen en de `System.IO.FileStream` object.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door het `System.IO.BinaryWriter` object `Write` en geeft u de bytearray door.

**Zie ook**

[Werken met PDF/A-documenten](pdf-a-documents.md#working-with-pdf-a-documents)

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Creërend een .NET cliëntassemblage die het coderen Base64 gebruikt](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## Programmaticaal bepalen van PDF/A-compatibiliteit {#programmatically-determining-pdf-a-compliancy}

U kunt de dienst DocConverter gebruiken om te bepalen of een document van de PDF PDF/A-Volgzaam is. Zie voor informatie over een PDF/A-document en hoe u een PDF-document kunt omzetten in een PDF/A-document [Documenten converteren naar PDF/A-documenten](pdf-a-documents.md#converting-documents-to-pdf-a-documents).

>[!NOTE]
>
>Voor meer informatie over de dienst DocConverter, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-1}

Voer de volgende stappen uit om de PDF/A-compatibiliteit te bepalen:

1. Inclusief projectbestanden.
1. Een DocConvert-client maken
1. Verwijs naar een document van PDF dat wordt gebruikt om PDF/A conformiteit te bepalen.
1. Stel runtime-opties in.
1. Haal informatie op over het PDF-document.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-docconverter-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)

Voor informatie over de locatie van deze JAR-bestanden raadpleegt u [Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Een DocConvert-client maken**

Voordat u een DocConverter-bewerking programmatisch kunt uitvoeren, moet u een DocConverter-client maken. Als u de Java API gebruikt, maakt u een `DocConverterServiceClient` object. Als u de DocConverter-webservice-API gebruikt, maakt u een `DocConverterServiceService` object.

**Verwijzen naar een PDF-document dat wordt gebruikt om de PDF/A-compatibiliteit te bepalen**

Er moet naar een PDF-document worden verwezen en dat document moet worden doorgegeven aan de DocConverter-service om te bepalen of het PDF-document compatibel is met PDF/A.

**Uitvoeringsopties instellen**

U kunt een runtime optie instellen die bepaalt hoeveel informatie tijdens het conversieproces wordt bijgehouden. Dat wil zeggen, u kunt negen verschillende niveaus instellen die aangeven hoeveel informatie de DocConverter-service bijhoudt wanneer een PDF-document wordt geconverteerd naar een PDF/A-document.

**Informatie ophalen over het PDF-document**

Nadat u de DocConverter dienstcliënt creeert, van verwijzingen het document van de PDF, en de runtime opties plaatst, kunt u bepalen of het document van de PDF een PDF/A-Volgzaam document is.

**Zie ook**

[PDF/A-compatibiliteit bepalen met de Java API](pdf-a-documents.md#determine-pdf-a-compliancy-using-the-java-api)

[PDF/A-compatibiliteit bepalen met de webservice-API](pdf-a-documents.md#determine-pdf-a-compliancy-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### PDF/A-compatibiliteit bepalen met de Java API {#determine-pdf-a-compliancy-using-the-java-api}

Bepaal de PDF/A-compatibiliteit met de Java API:

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-docconverter-client.jar, op in het klassenpad van uw Java-project.

1. Een DocConvert-client maken

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `DocConverterServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Verwijzen naar een PDF-document dat wordt gebruikt om de PDF/A-compatibiliteit te bepalen

   * Een `java.io.FileInputStream` object dat staat voor het PDF-document dat moet worden geconverteerd met de constructor ervan en dat een tekenreekswaarde doorgeeft die de locatie van het PDF-bestand aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. Uitvoeringsopties instellen

   * Een `PDFAValidationOptionSpec` object met behulp van de constructor.
   * Stel het compatibiliteitsniveau in door de `PDFAValidationOptionSpec` object `setCompliance` methode en doorgeven `PDFAValidationOptionSpec.Compliance.PDFA_1B`.
   * Stel het niveau voor het bijhouden van gegevens in door het `PDFAValidationOptionSpec` object `setLogLevel` methode en het overgaan van een koordwaarde die het volgende niveau specificeert. Geef bijvoorbeeld de waarde door `FINE`. Voor informatie over de verschillende waarden raadpleegt u de `setLogLevel` in de [AEM Forms API-naslag](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Informatie ophalen over het PDF-document

   Bepaal PDF/A-conformiteit door de `DocConverterServiceClient` object `isPDFA` en geeft de volgende waarden door:

   * De `com.adobe.idp.Document` object dat het PDF-document bevat.
   * De `PDFAValidationOptionSpec` -object dat uitvoeringsopties opgeeft.

   De `isPDFA` methode retourneert een `PDFAValidationResult` object dat de resultaten van deze bewerking bevat.

**Zie ook**

[Werken met PDF/A-documenten](pdf-a-documents.md#working-with-pdf-a-documents)

[Snel starten (SOAP modus): PDF/A-compatibiliteit bepalen met de Java API](/help/forms/developing/docconverter-service-java-api-quick.md#quick-start-soap-mode-determining-pdf-a-compliancy-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### PDF/A-compatibiliteit bepalen met de webservice-API {#determine-pdf-a-compliancy-using-the-web-service-api}

Bepaal PDF/A-compatibiliteit met de webservice-API:

1. Projectbestanden opnemen

   * Creeer een Microsoft .NET cliëntassemblage die DocConverter WSDL verbruikt.
   * Verwijs naar de Microsoft .NET cliëntassemblage.

1. Een DocConvert-client maken

   * Gebruikend de de cliëntassemblage van Microsoft .NET, creeer een `DocConverterServiceService` object door de standaardconstructor aan te roepen.
   * Stel de `DocConverterServiceService` object `Credentials` lid met gegevens `System.Net.NetworkCredential` waarde die de gebruikersnaam en wachtwoordwaarde specificeert.

1. Verwijzen naar een PDF-document dat wordt gebruikt om de PDF/A-compatibiliteit te bepalen

   * Een `BLOB` object met behulp van de constructor. De `BLOB` wordt gebruikt om het PDF-document op te slaan dat wordt geconverteerd naar een PDF/A-document.
   * Een `System.IO.FileStream` door de constructor aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het PDF-document en de modus voor het openen van het bestand in vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door het toe te wijzen `binaryData` eigenschap met de inhoud van de bytearray.

1. Uitvoeringsopties instellen

   * Een `PDFAValidationOptionSpec` object met behulp van de constructor.
   * Stel het compatibiliteitsniveau in door de `PDFAValidationOptionSpec` object `compliance` gegevenslid met de waarde `PDFAConversionOptionSpec_Compliance.PDFA_1B`.
   * Stel het niveau voor het bijhouden van de gegevens in door het `PDFAValidationOptionSpec` object `resultLevel` gegevenslid met de waarde `PDFAValidationOptionSpec_ResultLevel.DETAILED`.

1. Informatie ophalen over het PDF-document

   Bepaal PDF/A-conformiteit door de `DocConverterServiceService` object `isPDFA` en geeft de volgende waarden door:

   * De `BLOB` object dat het PDF-document bevat.
   * De `PDFAValidationOptionSpec` object dat uitvoeringsopties bevat.

   De `isPDFA` methode retourneert een `PDFAValidationResult` object dat de resultaten van deze bewerking bevat.

**Zie ook**

[Werken met PDF/A-documenten](pdf-a-documents.md#working-with-pdf-a-documents)

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Creërend een .NET cliëntassemblage die het coderen Base64 gebruikt](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)
