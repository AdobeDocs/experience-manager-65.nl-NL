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
feature: Adaptive Forms,Document Services,APIs & Integrations
source-git-commit: 4df88fc37b86b6ff3b3a9b788c91b61e2aa7b07f
workflow-type: tm+mt
source-wordcount: '2347'
ht-degree: 0%

---

# Werken met PDF/A-documenten {#working-with-pdf-a-documents}

**Ongeveer de Dienst DocConverter**

De DocConverter-service kan PDF-documenten omzetten in PDA/A-documenten. U kunt deze taken uitvoeren met deze service:

* PDF-documenten converteren naar PDF/A-documenten. (Zie [ Omzettend Documenten in Documenten PDF/A ](pdf-a-documents.md#converting-documents-to-pdf-a-documents).)
* Bepaal of PDF-documenten PDF/A-documenten zijn. (Zie [ programmatically het bepalen van PDF/A Complichtigheid ](pdf-a-documents.md#programmatically-determining-pdf-a-compliancy).)

>[!NOTE]
>
>Voor meer informatie over de dienst DocConverter, zie [ Verwijzing van de Diensten voor AEM Forms ](https://www.adobe.com/go/learn_aemforms_services_63).

## Documenten converteren naar PDF/A-documenten {#converting-documents-to-pdf-a-documents}

Met de DocConverter-service kunt u een PDF-document omzetten in een PDF/A-document. Omdat PDF/A een archiefindeling is voor langdurige bewaring van de inhoud van het document, worden alle lettertypen ingesloten en wordt het bestand niet gecomprimeerd. Een PDF/A-document is daarom doorgaans groter dan een standaard PDF-document. Een PDF/A-document bevat ook geen audio- en video-inhoud. Voordat u een PDF-document omzet in een PDF/A-document, moet u controleren of het PDF-document geen PDF/A-document is.

De PDF/A-1-specificatie bestaat uit twee conformiteitsniveaus, namelijk A en B. Het belangrijkste verschil tussen beide is de logische structuur (toegankelijkheid) die niet vereist is voor compatibiliteitsniveau B. Ongeacht het compatibiliteitsniveau, dicteert PDF/A-1 dat alle lettertypen zijn ingesloten in het gegenereerde PDF/A-document. Op dit moment wordt alleen PDF/A-1b ondersteund voor validatie (en conversie).

Hoewel PDF/A de standaard is voor het archiveren van PDF-documenten, is het niet verplicht dat PDF/A wordt gebruikt voor archivering als een standaard PDF-document voldoet aan de eisen van uw bedrijf. Het doel van de PDF/A-standaard is een PDF-bestand te maken dat is bedoeld voor archiverings- en documentbewaardoeleinden op lange termijn.

De ondersteunde PDF/A-compatibiliteitsnormen omvatten PDF/A-1a, 1b, 2a, 2b, 3a en 3b.

>[!NOTE]
>
>Voor meer informatie over de dienst DocConverter, zie [ Verwijzing van de Diensten voor AEM Forms ](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary-of-steps}

Voer de volgende stappen uit om een PDF-document om te zetten in een PDF/A-document:

1. Inclusief projectbestanden.
1. Een DocConvert-client maken
1. Verwijzen naar een PDF-document dat moet worden omgezet in een PDF/A-document.
1. Trackinggegevens instellen.
1. Converteer het document.
1. Sla het PDF/A-document op.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-docconverter-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)

Voor informatie over de plaats van deze JAR dossiers, zie [ Inclusief de bibliotheekdossiers van AEM Forms Java ](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**creeer een cliënt DocConvert**

Voordat u een DocConverter-bewerking programmatisch kunt uitvoeren, moet u een DocConverter-client maken. Maak een `DocConverterServiceClient` -object als u de Java API gebruikt. Maak een `DocConverterServiceService` -object als u de DocConverter-webservice-API gebruikt.

**Verwijzing een document van PDF om in een document van PDF te zetten/A**

Hiermee wordt een PDF-document opgehaald dat naar een PDF/A-document moet worden geconverteerd. Als u probeert een PDF-document, zoals een Acrobat-formulier, om te zetten in een PDF/A-document, veroorzaakt u een uitzondering.

**plaats het volgen informatie**

U kunt een runtime optie instellen die bepaalt hoeveel informatie tijdens het conversieproces wordt bijgehouden. Namelijk kunt u negen verschillende niveaus plaatsen die hoeveel informatie specificeren de dienst DocConverter volgt wanneer het een document van de PDF in een document PDF/A omzet.

**zet het document** om

Nadat u de DocConverter dienstcliënt creeert, verwijs het document van de PDF om te zetten en de runtime optie te plaatsen die specificeert hoeveel informatie wordt gevolgd, kunt u het document van de PDF in een PDF/A- document omzetten.

**sparen het PDF/A- document**

U kunt het PDF/A-document opslaan als een PDF-bestand.

**zie ook**

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

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `DocConverterServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Verwijzen naar een PDF-document dat moet worden omgezet in een PDF/A-document

   * Maak een `java.io.FileInputStream` -object dat het te converteren PDF-document vertegenwoordigt met behulp van de constructor en geef een tekenreekswaarde door die de locatie van het PDF-bestand aangeeft.
   * Maak een `com.adobe.idp.Document` -object door de constructor ervan te gebruiken en het `java.io.FileInputStream` -object door te geven.

1. Trackinggegevens instellen

   * Maak een `PDFAConversionOptionSpec` -object met behulp van de constructor.
   * Stel het niveau voor het bijhouden van gegevens in door de methode van het `PDFAConversionOptionSpec` -object `setLogLevel` aan te roepen en een tekenreekswaarde door te geven die het niveau voor bijhouden opgeeft. Geef bijvoorbeeld de waarde `FINE` door. Voor informatie over de verschillende waarden, zie de `setLogLevel` methode in de [ AEM Forms API Verwijzing ](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Het document converteren

   Zet het PDF-document om in een PDF/A-document door de methode `toPDFA` van het object `DocConverterServiceClient` aan te roepen en de volgende waarden door te geven:

   * Het `com.adobe.idp.Document` -object dat het om te zetten PDF-document bevat
   * Het `PDFAConversionOptionSpec` -object dat trackinginformatie opgeeft

   De methode `toPDFA` retourneert een `PDFAConversionResult` -object dat het PDF/A-document bevat.

1. Het PDF/A-document opslaan

   * Haal het PDF/A-document op door de methode `getPDFA` van het object `PDFAConversionResult` aan te roepen. Deze methode retourneert een `com.adobe.idp.Document` -object dat het PDF/A-document vertegenwoordigt.
   * Maak een `java.io.File` -object dat het PDF/A-bestand vertegenwoordigt. Controleer of de bestandsnaamextensie .pdf is.
   * Vul het bestand met PDF/A-gegevens door de methode `copyToFile` van het object `com.adobe.idp.Document` aan te roepen en het object `java.io.File` door te geven.

**zie ook**

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

   * Gebruikend de Microsoft .NET cliëntassemblage, creeer een `DocConverterServiceService` voorwerp door zijn standaardaannemer aan te halen.
   * Stel het gegevenslid `Credentials` van het `DocConverterServiceService` -object in met een `System.Net.NetworkCredential` -waarde die de gebruikersnaam en het wachtwoord opgeeft.

1. Verwijzen naar een PDF-document dat moet worden omgezet in een PDF/A-document

   * Maak een `BLOB` -object met behulp van de constructor. Met het `BLOB` -object wordt het PDF-document opgeslagen dat wordt geconverteerd naar een PDF/A-document.
   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `Length` van het object `System.IO.FileStream` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het object `BLOB` door de eigenschap `binaryData` ervan toe te wijzen met de inhoud van de bytearray.

1. Trackinggegevens instellen

   * Maak een `PDFAConversionOptionSpec` -object met behulp van de constructor.
   * Stel het niveau voor het bijhouden van gegevens in door een waarde toe te wijzen die het niveau voor bijhouden van gegevens opgeeft voor het gegevenslid `logLevel` van het `PDFAConversionOptionSpec` -object. Wijs bijvoorbeeld de waarde `FINE` toe aan dit gegevenslid.

1. Het document converteren

   Zet het PDF-document om in een PDF/A-document door de methode `toPDFA` van het object `DocConverterServiceService` aan te roepen en de volgende waarden door te geven:

   * Het `BLOB` -object dat het om te zetten PDF-document bevat
   * Het `PDFAConversionOptionSpec` -object dat trackinginformatie opgeeft

   De methode `toPDFA` retourneert een `PDFAConversionResult` -object dat het PDF/A-document bevat.

1. Het PDF/A-document opslaan

   * Maak een `BLOB` -object dat het PDF/A-document opslaat door de waarde van het gegevenslid van het `PDFAConversionResult` object `PDFADocument` op te halen.
   * Maak een bytearray die de inhoud opslaat van het `BLOB` -object dat met het `PDFAConversionResult` -object is geretourneerd. Vul de bytearray met de waarde van het gegevenslid `binaryData` van het object `BLOB` .
   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het PDF/A-document vertegenwoordigt.
   * Maak een `System.IO.BinaryWriter` -object door de constructor ervan aan te roepen en het `System.IO.FileStream` -object door te geven.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door de methode `Write` van het object `System.IO.BinaryWriter` aan te roepen en de bytearray door te geven.

**zie ook**

[Werken met PDF/A-documenten](pdf-a-documents.md#working-with-pdf-a-documents)

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Creërend een .NET cliëntassemblage die het coderen Base64 gebruikt](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## Programmaticaal bepalen van PDF/A-compatibiliteit {#programmatically-determining-pdf-a-compliancy}

U kunt de dienst DocConverter gebruiken om te bepalen of een document van de PDF PDF/A-Volgzaam is. Voor informatie over een PDF/A- document en hoe te om een document van de PDF in een document van PDF/A om te zetten, zie [ Converterend Documenten in Documenten PDF/A ](pdf-a-documents.md#converting-documents-to-pdf-a-documents).

>[!NOTE]
>
>Voor meer informatie over de dienst DocConverter, zie [ Verwijzing van de Diensten voor AEM Forms ](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-1}

Voer de volgende stappen uit om de PDF/A-compatibiliteit te bepalen:

1. Inclusief projectbestanden.
1. Een DocConvert-client maken
1. Verwijs naar een document van PDF dat wordt gebruikt om PDF/A conformiteit te bepalen.
1. Stel runtime-opties in.
1. Haal informatie op over het PDF-document.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-docconverter-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)

Voor informatie over de plaats van deze JAR dossiers, zie [ Inclusief de bibliotheekdossiers van AEM Forms Java ](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**creeer een cliënt DocConvert**

Voordat u een DocConverter-bewerking programmatisch kunt uitvoeren, moet u een DocConverter-client maken. Maak een `DocConverterServiceClient` -object als u de Java API gebruikt. Maak een `DocConverterServiceService` -object als u de DocConverter-webservice-API gebruikt.

**Verwijzing een document van PDF dat wordt gebruikt om PDF/A compliantie** te bepalen

Er moet naar een PDF-document worden verwezen en dat document moet worden doorgegeven aan de DocConverter-service om te bepalen of het PDF-document compatibel is met PDF/A.

**vastgestelde runtime opties**

U kunt een runtime optie instellen die bepaalt hoeveel informatie tijdens het conversieproces wordt bijgehouden. Dat wil zeggen, u kunt negen verschillende niveaus instellen die aangeven hoeveel informatie de DocConverter-service bijhoudt wanneer een PDF-document wordt geconverteerd naar een PDF/A-document.

**wint informatie over het document van PDF** terug

Nadat u de DocConverter dienstcliënt creeert, van verwijzingen het document van de PDF, en de runtime opties plaatst, kunt u bepalen of het document van de PDF een PDF/A-Volgzaam document is.

**zie ook**

[PDF/A-compatibiliteit bepalen met de Java API](pdf-a-documents.md#determine-pdf-a-compliancy-using-the-java-api)

[PDF/A-compatibiliteit bepalen met de webservice-API](pdf-a-documents.md#determine-pdf-a-compliancy-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### PDF/A-compatibiliteit bepalen met de Java API {#determine-pdf-a-compliancy-using-the-java-api}

Bepaal de PDF/A-compatibiliteit met de Java API:

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-docconverter-client.jar, op in het klassenpad van uw Java-project.

1. Een DocConvert-client maken

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `DocConverterServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Verwijzen naar een PDF-document dat wordt gebruikt om de PDF/A-compatibiliteit te bepalen

   * Maak een `java.io.FileInputStream` -object dat het te converteren PDF-document vertegenwoordigt met behulp van de constructor en geef een tekenreekswaarde door die de locatie van het PDF-bestand aangeeft.
   * Maak een `com.adobe.idp.Document` -object door de constructor ervan te gebruiken en het `java.io.FileInputStream` -object door te geven.

1. Uitvoeringsopties instellen

   * Maak een `PDFAValidationOptionSpec` -object met behulp van de constructor.
   * Stel het compatibiliteitsniveau in door de methode `setCompliance` van het object `PDFAValidationOptionSpec` aan te roepen en door te geven `PDFAValidationOptionSpec.Compliance.PDFA_1B` .
   * Stel het niveau voor het bijhouden van gegevens in door de methode van het `PDFAValidationOptionSpec` -object `setLogLevel` aan te roepen en een tekenreekswaarde door te geven die het niveau voor bijhouden opgeeft. Geef bijvoorbeeld de waarde `FINE` door. Voor informatie over de verschillende waarden, zie de `setLogLevel` methode in de [ AEM Forms API Verwijzing ](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Informatie ophalen over het PDF-document

   Bepaal de compatibiliteit PDF/A door de methode `isPDFA` van het object `DocConverterServiceClient` aan te roepen en de volgende waarden door te geven:

   * Het `com.adobe.idp.Document` -object dat het PDF-document bevat.
   * Het `PDFAValidationOptionSpec` -object dat uitvoeringsopties opgeeft.

   De methode `isPDFA` retourneert een `PDFAValidationResult` -object dat de resultaten van deze bewerking bevat.

**zie ook**

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

   * Gebruikend de Microsoft .NET cliëntassemblage, creeer een `DocConverterServiceService` voorwerp door zijn standaardaannemer aan te halen.
   * Stel het gegevenslid `Credentials` van het `DocConverterServiceService` -object in met een `System.Net.NetworkCredential` -waarde die de gebruikersnaam en het wachtwoord opgeeft.

1. Verwijzen naar een PDF-document dat wordt gebruikt om de PDF/A-compatibiliteit te bepalen

   * Maak een `BLOB` -object met behulp van de constructor. Met het `BLOB` -object wordt het PDF-document opgeslagen dat wordt geconverteerd naar een PDF/A-document.
   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `Length` van het object `System.IO.FileStream` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het object `BLOB` door de eigenschap `binaryData` ervan toe te wijzen met de inhoud van de bytearray.

1. Uitvoeringsopties instellen

   * Maak een `PDFAValidationOptionSpec` -object met behulp van de constructor.
   * Stel het compatibiliteitsniveau in door het gegevenslid `compliance` van het `PDFAValidationOptionSpec` -object toe te wijzen aan de waarde `PDFAConversionOptionSpec_Compliance.PDFA_1B` .
   * Stel het niveau voor het bijhouden van gegevens in door het gegevenslid `resultLevel` van het `PDFAValidationOptionSpec` -object aan de waarde `PDFAValidationOptionSpec_ResultLevel.DETAILED` toe te wijzen.

1. Informatie ophalen over het PDF-document

   Bepaal de compatibiliteit PDF/A door de methode `isPDFA` van het object `DocConverterServiceService` aan te roepen en de volgende waarden door te geven:

   * Het `BLOB` -object dat het PDF-document bevat.
   * Het `PDFAValidationOptionSpec` -object dat uitvoeringsopties bevat.

   De methode `isPDFA` retourneert een `PDFAValidationResult` -object dat de resultaten van deze bewerking bevat.

**zie ook**

[Werken met PDF/A-documenten](pdf-a-documents.md#working-with-pdf-a-documents)

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Creërend een .NET cliëntassemblage die het coderen Base64 gebruikt](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)
