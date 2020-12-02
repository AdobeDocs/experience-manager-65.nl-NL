---
title: Werken met PDF/A-documenten
seo-title: Werken met PDF/A-documenten
description: 'null'
seo-description: 'null'
uuid: c258d253-068a-4412-955a-21d8a4792d6f
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 1e6cc554-aef1-463c-906b-634b80a27917
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '2342'
ht-degree: 0%

---


# Werken met PDF/A-documenten {#working-with-pdf-a-documents}

**Over de DocConverter-service**

De DocConverter-service kan PDF-documenten converteren naar PDF/A-documenten. U kunt deze taken uitvoeren met deze service:

* Converteer PDF-documenten naar PDF/A-documenten. (Zie [Documenten converteren naar PDF/A-documenten](pdf-a-documents.md#converting-documents-to-pdf-a-documents).)
* Bepaal of PDF-documenten PDF/A-documenten zijn. (Zie [Programmaticaal PDF/A-compatibiliteit bepalen](pdf-a-documents.md#programmatically-determining-pdf-a-compliancy).)

>[!NOTE]
>
>Voor meer informatie over de dienst DocConverter, zie [de Verwijzing van de Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Documenten converteren naar PDF/A-documenten {#converting-documents-to-pdf-a-documents}

Met de DocConverter-service kunt u een PDF-document converteren naar een PDF/A-document. Omdat PDF/A een archiefindeling is voor langdurige bewaring van de inhoud van het document, worden alle fonts ingesloten en wordt het bestand niet gecomprimeerd. Een PDF/A-document is daarom doorgaans groter dan een standaard PDF-document. Een PDF/A-document bevat ook geen audio- en video-inhoud. Voordat u een PDF-document converteert naar een PDF/A-document, moet u controleren of het PDF-document geen PDF/A-document is.

De PDF/A-1-specificatie bestaat uit twee conformiteitsniveaus, namelijk A en B. Het grootste verschil tussen beide is de logische structuur (toegankelijkheid) die niet vereist is voor niveau B. PDF/A-1 schrijft voor dat alle fonts in het gegenereerde PDF/A-document worden ingesloten, ongeacht het compatibiliteitsniveau. Momenteel wordt alleen PDF/A-1b ondersteund voor validatie (en conversie).

Hoewel PDF/A de standaard is voor het archiveren van PDF-documenten, is het niet verplicht dat PDF/A wordt gebruikt voor archivering als een standaard PDF-document voldoet aan de vereisten van uw bedrijf. Het doel van de PDF/A-standaard is het maken van een PDF-bestand dat is bedoeld voor archiveringsdoeleinden op lange termijn en voor het bewaren van documenten.

>[!NOTE]
>
>Voor meer informatie over de dienst DocConverter, zie [de Verwijzing van de Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van stappen {#summary-of-steps}

Voer de volgende stappen uit om een PDF-document te converteren naar een PDF/A-document:

1. Inclusief projectbestanden.
1. Een DocConvert-client maken
1. Verwijzen naar een PDF-document dat moet worden geconverteerd naar een PDF/A-document.
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

Zie [Including AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files) voor informatie over de locatie van deze JAR-bestanden.

**Een DocConvert-client maken**

Voordat u een DocConverter-bewerking programmatisch kunt uitvoeren, moet u een DocConverter-client maken. Als u de Java API gebruikt, maakt u een `DocConverterServiceClient`-object. Als u de DocConverter-webservice-API gebruikt, maakt u een `DocConverterServiceService`-object.

**Verwijzen naar een PDF-document dat moet worden geconverteerd naar een PDF/A-document**

Een PDF-document ophalen voor conversie naar een PDF/A-document. Als u probeert een PDF-document, zoals een Acrobat-formulier, te converteren naar een PDF/A-document, veroorzaakt u een uitzondering.

**Trackinggegevens instellen**

U kunt een runtime optie instellen die bepaalt hoeveel informatie tijdens het conversieproces wordt bijgehouden. Met andere woorden, u kunt negen verschillende niveaus instellen die aangeven hoeveel informatie de DocConverter-service bijhoudt wanneer een PDF-document wordt geconverteerd naar een PDF/A-document.

**Het document converteren**

Nadat u de DocConverter-serviceclient hebt gemaakt, verwijst u naar het PDF-document dat u wilt converteren en stelt u de runtime-optie in die aangeeft hoeveel gegevens worden bijgehouden, en kunt u het PDF-document converteren naar een PDF/A-document.

**Het PDF/A-document opslaan**

U kunt het PDF/A-document opslaan als een PDF-bestand.

**Zie ook**

[Documenten converteren naar PDF/A-documenten met de Java API](pdf-a-documents.md#convert-documents-to-pdf-a-documents-using-the-java-api)

[Documenten converteren naar PDF/A-documenten met de webservice-API](pdf-a-documents.md#convert-documents-to-pdf-a-documents-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[PDF/A-compatibiliteit programmatisch bepalen](pdf-a-documents.md#programmatically-determining-pdf-a-compliancy)

### Documenten converteren naar PDF/A-documenten met de Java API {#convert-documents-to-pdf-a-documents-using-the-java-api}

Een PDF-document converteren naar een PDF/A-document met behulp van de Java API:

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-docconverter-client.jar, op in het klassenpad van uw Java-project.

1. Een DocConvert-client maken

   * Maak een `ServiceClientFactory`-object dat verbindingseigenschappen bevat.
   * Maak een `DocConverterServiceClient`-object door de constructor ervan te gebruiken en het object `ServiceClientFactory` door te geven.

1. Verwijzen naar een PDF-document dat moet worden geconverteerd naar een PDF/A-document

   * Maak een `java.io.FileInputStream`-object dat het te converteren PDF-document vertegenwoordigt met de constructor ervan en geef een tekenreekswaarde door die de locatie van het PDF-bestand aangeeft.
   * Maak een `com.adobe.idp.Document`-object door de constructor ervan te gebruiken en het object `java.io.FileInputStream` door te geven.

1. Trackinggegevens instellen

   * Maak een `PDFAConversionOptionSpec`-object met de constructor ervan.
   * Stel het niveau voor het bijhouden van gegevens in door de methode `setLogLevel` van het object `PDFAConversionOptionSpec` aan te roepen en een tekenreekswaarde door te geven die het niveau voor bijhouden opgeeft. Geef bijvoorbeeld de waarde `FINE` door. Zie de `setLogLevel`-methode in de [AEM Forms API-naslaggids](https://www.adobe.com/go/learn_aemforms_javadocs_63_en) voor informatie over de verschillende waarden.

1. Het document converteren

   Converteer het PDF-document naar een PDF/A-document door de methode `toPDFA` van het object `DocConverterServiceClient` aan te roepen en de volgende waarden door te geven:

   * Het `com.adobe.idp.Document`-object dat het te converteren PDF-document bevat
   * Het `PDFAConversionOptionSpec`-object dat de volgende informatie opgeeft

   De methode `toPDFA` retourneert een `PDFAConversionResult`-object dat het PDF/A-document bevat.

1. Het PDF/A-document opslaan

   * Haal het PDF/A-document op door de methode `PDFAConversionResult` van het object `getPDFA` aan te roepen. Deze methode retourneert een `com.adobe.idp.Document`-object dat het PDF/A-document vertegenwoordigt.
   * Maak een `java.io.File`-object dat het PDF/A-bestand vertegenwoordigt. Controleer of de bestandsnaamextensie .pdf is.
   * Vul het bestand met PDF/A-gegevens door de methode `copyToFile` van het object `com.adobe.idp.Document` aan te roepen en het object `java.io.File` door te geven.

**Zie ook**

[Werken met PDF/A-documenten](pdf-a-documents.md#working-with-pdf-a-documents)

[Snel starten (SOAP-modus): Een document converteren naar een PDF/A-document met de Java API](/help/forms/developing/docconverter-service-java-api-quick.md#quick-start-soap-mode-converting-a-document-to-a-pdf-a-document-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Documenten converteren naar PDF/A-documenten met de API {#convert-documents-to-pdf-a-documents-using-the-web-service-api} voor webservices

Een PDF-document converteren naar een PDF/A-document met de DocConverter-API (webservice):

1. Projectbestanden opnemen

   * Creeer een de cliëntassemblage van Microsoft .NET die DocConverter WSDL verbruikt.
   * Verwijs naar de cliëntassemblage van Microsoft .NET.

1. Een DocConvert-client maken

   * Gebruikend de de cliëntassemblage van Microsoft .NET, creeer een `DocConverterServiceService` voorwerp door zijn standaardaannemer aan te halen.
   * Stel het `DocConverterServiceService`-gegevenslid van het `Credentials`-object in met een `System.Net.NetworkCredential`-waarde die de gebruikersnaam en het wachtwoord opgeeft.

1. Verwijzen naar een PDF-document dat moet worden geconverteerd naar een PDF/A-document

   * Maak een `BLOB`-object met de constructor ervan. Met het object `BLOB` wordt het PDF-document opgeslagen dat is geconverteerd naar een PDF/A-document.
   * Maak een `System.IO.FileStream`-object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het PDF-document en de modus voor het openen van het bestand in vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `System.IO.FileStream` van het object `Length` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het object `BLOB` door de eigenschap `binaryData` ervan toe te wijzen met de inhoud van de bytearray.

1. Trackinggegevens instellen

   * Maak een `PDFAConversionOptionSpec`-object met de constructor ervan.
   * Stel het niveau voor het bijhouden van de gegevens in door een waarde toe te wijzen die het niveau voor het bijhouden van de gegevens opgeeft voor het `PDFAConversionOptionSpec`-gegevenslid van het object. `logLevel` Wijs bijvoorbeeld de waarde `FINE` toe aan dit gegevenslid.

1. Het document converteren

   Converteer het PDF-document naar een PDF/A-document door de methode `toPDFA` van het object `DocConverterServiceService` aan te roepen en de volgende waarden door te geven:

   * Het `BLOB`-object dat het te converteren PDF-document bevat
   * Het `PDFAConversionOptionSpec`-object dat de volgende informatie opgeeft

   De methode `toPDFA` retourneert een `PDFAConversionResult`-object dat het PDF/A-document bevat.

1. Het PDF/A-document opslaan

   * Maak een `BLOB`-object dat het PDF/A-document opslaat door de waarde op te halen van het `PDFAConversionResult`-gegevenslid van het object.`PDFADocument`
   * Maak een bytearray die de inhoud opslaat van het `BLOB`-object dat is geretourneerd met het object `PDFAConversionResult`. Vul de bytearray met de waarde van het `BLOB`-gegevenslid van het object `binaryData`.
   * Maak een `System.IO.FileStream`-object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het PDF/A-document vertegenwoordigt.
   * Maak een `System.IO.BinaryWriter`-object door de constructor ervan aan te roepen en het object `System.IO.FileStream` door te geven.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door de methode `Write` van het object `System.IO.BinaryWriter` aan te roepen en de bytearray door te geven.

**Zie ook**

[Werken met PDF/A-documenten](pdf-a-documents.md#working-with-pdf-a-documents)

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Creërend een .NET cliëntassemblage die het coderen Base64 gebruikt](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## PDF/A-compatibiliteit programmatisch bepalen {#programmatically-determining-pdf-a-compliancy}

Met de DocConverter-service kunt u bepalen of een PDF-document compatibel is met PDF/A. Zie [Documenten converteren naar PDF/A-documenten](pdf-a-documents.md#converting-documents-to-pdf-a-documents) voor informatie over een PDF/A-document en hoe u een PDF-document converteert naar een PDF/A-document.

>[!NOTE]
>
>Voor meer informatie over de dienst DocConverter, zie [de Verwijzing van de Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van stappen {#summary_of_steps-1}

Voer de volgende stappen uit om te bepalen of een PDF/A-bestand compatibel is:

1. Inclusief projectbestanden.
1. Een DocConvert-client maken
1. Verwijs naar een PDF-document dat wordt gebruikt om de compatibiliteit met PDF/A te bepalen.
1. Stel runtime-opties in.
1. Informatie over het PDF-document ophalen.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-docconverter-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)

Zie [Including AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files) voor informatie over de locatie van deze JAR-bestanden.

**Een DocConvert-client maken**

Voordat u een DocConverter-bewerking programmatisch kunt uitvoeren, moet u een DocConverter-client maken. Als u de Java API gebruikt, maakt u een `DocConverterServiceClient`-object. Als u de DocConverter-webservice-API gebruikt, maakt u een `DocConverterServiceService`-object.

**Verwijzen naar een PDF-document dat wordt gebruikt om de compatibiliteit met PDF/A te bepalen**

Er moet naar een PDF-document worden verwezen en dat document moet worden doorgegeven aan de DocConverter-service om te bepalen of het PDF-document compatibel is met PDF/A.

**Uitvoeringsopties instellen**

U kunt een runtime optie instellen die bepaalt hoeveel informatie tijdens het conversieproces wordt bijgehouden. Met andere woorden, u kunt negen verschillende niveaus instellen om op te geven hoeveel informatie de DocConverter-service bijhoudt wanneer een PDF-document wordt geconverteerd naar een PDF/A-document.

**Informatie over het PDF-document ophalen**

Nadat u de DocConverter-serviceclient hebt gemaakt, het PDF-document hebt geraadpleegd en de runtime-opties hebt ingesteld, kunt u bepalen of het PDF-document compatibel is met PDF/A.

**Zie ook**

[PDF/A-compatibiliteit bepalen met de Java API](pdf-a-documents.md#determine-pdf-a-compliancy-using-the-java-api)

[PDF/A-compatibiliteit bepalen met de webservice-API](pdf-a-documents.md#determine-pdf-a-compliancy-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### PDF/A-compatibiliteit bepalen met de Java API {#determine-pdf-a-compliancy-using-the-java-api}

PDF/A-compatibiliteit bepalen met de Java API:

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-docconverter-client.jar, op in het klassenpad van uw Java-project.

1. Een DocConvert-client maken

   * Maak een `ServiceClientFactory`-object dat verbindingseigenschappen bevat.
   * Maak een `DocConverterServiceClient`-object door de constructor ervan te gebruiken en het object `ServiceClientFactory` door te geven.

1. Verwijzen naar een PDF-document dat wordt gebruikt om de compatibiliteit met PDF/A te bepalen

   * Maak een `java.io.FileInputStream`-object dat het te converteren PDF-document vertegenwoordigt met de constructor ervan en geef een tekenreekswaarde door die de locatie van het PDF-bestand aangeeft.
   * Maak een `com.adobe.idp.Document`-object door de constructor ervan te gebruiken en het object `java.io.FileInputStream` door te geven.

1. Uitvoeringsopties instellen

   * Maak een `PDFAValidationOptionSpec`-object met de constructor ervan.
   * Stel het compatibiliteitsniveau in door de methode `setCompliance` van het object `PDFAValidationOptionSpec` aan te roepen en `PDFAValidationOptionSpec.Compliance.PDFA_1B` door te geven.
   * Stel het niveau voor het bijhouden van gegevens in door de methode `setLogLevel` van het object `PDFAValidationOptionSpec` aan te roepen en een tekenreekswaarde door te geven die het niveau voor bijhouden opgeeft. Geef bijvoorbeeld de waarde `FINE` door. Zie de `setLogLevel`-methode in de [AEM Forms API-naslaggids](https://www.adobe.com/go/learn_aemforms_javadocs_63_en) voor informatie over de verschillende waarden.

1. Informatie over het PDF-document ophalen

   Bepaal de compatibiliteit PDF/A door de methode `DocConverterServiceClient` van het object `isPDFA` aan te roepen en de volgende waarden door te geven:

   * Het `com.adobe.idp.Document`-object dat het PDF-document bevat.
   * Het `PDFAValidationOptionSpec`-object dat uitvoeringsopties opgeeft.

   De methode `isPDFA` retourneert een `PDFAValidationResult`-object dat de resultaten van deze bewerking bevat.

**Zie ook**

[Werken met PDF/A-documenten](pdf-a-documents.md#working-with-pdf-a-documents)

[Snel starten (SOAP-modus): PDF/A-compatibiliteit bepalen met de Java API](/help/forms/developing/docconverter-service-java-api-quick.md#quick-start-soap-mode-determining-pdf-a-compliancy-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### PDF/A-compatibiliteit bepalen met de webservice-API {#determine-pdf-a-compliancy-using-the-web-service-api}

Bepaal PDF/A-compatibiliteit met de webservice-API:

1. Projectbestanden opnemen

   * Creeer een de cliëntassemblage van Microsoft .NET die DocConverter WSDL verbruikt.
   * Verwijs naar de cliëntassemblage van Microsoft .NET.

1. Een DocConvert-client maken

   * Gebruikend de de cliëntassemblage van Microsoft .NET, creeer een `DocConverterServiceService` voorwerp door zijn standaardaannemer aan te halen.
   * Stel het `DocConverterServiceService`-gegevenslid van het `Credentials`-object in met een `System.Net.NetworkCredential`-waarde die de gebruikersnaam en het wachtwoord opgeeft.

1. Verwijzen naar een PDF-document dat wordt gebruikt om de compatibiliteit met PDF/A te bepalen

   * Maak een `BLOB`-object met de constructor ervan. Met het object `BLOB` wordt het PDF-document opgeslagen dat is geconverteerd naar een PDF/A-document.
   * Maak een `System.IO.FileStream`-object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het PDF-document en de modus voor het openen van het bestand in vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `System.IO.FileStream` van het object `Length` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het object `BLOB` door de eigenschap `binaryData` ervan toe te wijzen met de inhoud van de bytearray.

1. Uitvoeringsopties instellen

   * Maak een `PDFAValidationOptionSpec`-object met de constructor ervan.
   * Stel het compatibiliteitsniveau in door het `PDFAValidationOptionSpec`-gegevenslid van het object `compliance` toe te wijzen aan de waarde `PDFAConversionOptionSpec_Compliance.PDFA_1B`.
   * Stel het niveau voor het bijhouden van gegevens in door het `PDFAValidationOptionSpec`-gegevenslid van het object `resultLevel` toe te wijzen aan de waarde `PDFAValidationOptionSpec_ResultLevel.DETAILED`.

1. Informatie over het PDF-document ophalen

   Bepaal de compatibiliteit PDF/A door de methode `DocConverterServiceService` van het object `isPDFA` aan te roepen en de volgende waarden door te geven:

   * Het `BLOB`-object dat het PDF-document bevat.
   * Het `PDFAValidationOptionSpec`-object dat uitvoeringsopties bevat.

   De methode `isPDFA` retourneert een `PDFAValidationResult`-object dat de resultaten van deze bewerking bevat.

**Zie ook**

[Werken met PDF/A-documenten](pdf-a-documents.md#working-with-pdf-a-documents)

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Creërend een .NET cliëntassemblage die het coderen Base64 gebruikt](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)
