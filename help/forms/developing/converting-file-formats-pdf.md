---
title: Converteren tussen bestandsindelingen en PDF
seo-title: Converteren tussen bestandsindelingen en PDF
description: 'null'
seo-description: 'null'
uuid: f72ad603-c996-4d48-9bfc-bed7bf776af6
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 180cac3f-6378-42bc-9a47-60f9f08a7103
translation-type: tm+mt
source-git-commit: f9389a06f9c2cd720919486765cee76257f272c3

---


# Converteren tussen bestandsindelingen en PDF {#converting-between-file-formatsand-pdf}

**De PDF-service genereren**

Met de service PDF genereren worden oorspronkelijke bestandsindelingen geconverteerd naar PDF. Ook wordt PDF geconverteerd naar andere bestandsindelingen en wordt de grootte van PDF-documenten geoptimaliseerd.

De service PDF genereren gebruikt native toepassingen om de volgende bestandsindelingen te converteren naar PDF. Tenzij anders aangegeven, worden alleen de Duitse, Franse, Engelse en Japanse versies van deze toepassingen ondersteund. *Vensters wijst slechts* op steun voor slechts Vensters Server® 2003 en de Server 2008 van Vensters.

* Microsoft Office 2003 en 2007 voor de conversie van DOC, DOCX, RTF, TXT, XLS, XLSX, PPT, PPTX, VSD, MPP, MPPX, XPS en PUB (alleen Windows)

>[!NOTE]
>
>Acrobat® 9.2 of hoger is vereist voor het converteren van de Microsoft XPS-indeling naar PDF.

* Autodesk AutoCAD 2005, 2006, 2007, 2008 en 2009 om DWF, DWG en DXW om te zetten (alleen in het Engels)
* Corel WordPerfect 12 en X4 voor conversie van WPD, QPW, SHW (alleen in het Engels)
* OpenOffice 2.0, 2.4, 3.0.1 en 3.1 voor het converteren van ODT, ODS, ODP, ODF, ODF, SXW, SXC, SXD, DOC, DOCX, RTF, TXT, XLS, XLSX, PPT, PPTX, VSD, MPP, MPPX en PUB

>[!NOTE]
>
>De service PDF genereren biedt geen ondersteuning voor de 64-bits versies van OpenOffice.

* Adobe Photoshop® CS2 voor het omzetten van PSD (alleen Windows)

>[!NOTE]
>
>Photoshop CS3 en CS4 worden niet ondersteund omdat deze geen ondersteuning bieden voor Windows Server 2003 of Windows Server 2008.

* Adobe FrameMaker® 7.2 en 8 om FM (Vensters slechts) om te zetten
* Adobe PageMaker® 7.0 om PMD, PM6, P65, en PM (Vensters slechts) om te zetten
* Native indelingen die worden ondersteund door toepassingen van derden (hiervoor moet specifieke instellingsbestanden voor de toepassing worden ontwikkeld) (alleen Windows)

De service PDF genereren converteert de volgende op standaarden gebaseerde bestandsindelingen naar PDF.

* Video-indelingen: SWF, FLV (alleen Windows)
* Afbeeldingsindelingen: JPEG, JPG, JP2, J2Kí, JPC, J2C, GIF, BMP, TIFF, TIF, PNG, JPF
* HTML (Windows, Sun™ Solaris™ en Linux®)

De service PDF genereren converteert PDF naar de volgende bestandsindelingen (alleen Windows):

* EPS (Encapsulated PostScript)
* HTML 3.2
* HTML 4.01 met CSS 1.0
* DOC (Microsoft Word-indeling)
* RTF
* Tekst (zowel toegankelijk als onbewerkt)
* XML
* PDF/A-1a die alleen de DeviceRGB-kleurruimte gebruikt
* PDF/A-1b die alleen de DeviceRGB-kleurruimte gebruikt

Voor de service PDF genereren moet u de volgende beheertaken uitvoeren:

* De vereiste native toepassingen installeren op de computer die als host fungeert voor AEM-formulieren
* Installeer Adobe Acrobat Professional of Acrobat Pro Extended 9.2 op de computer die als host fungeert voor AEM-formulieren
* Instellingstaken na de installatie uitvoeren

Deze taken worden beschreven in AEM-formulieren installeren en implementeren met JBoss Turnkey.

U kunt deze taken uitvoeren met de service PDF genereren:

* Converteren van eigen bestandsindelingen naar PDF.
* HTML-documenten converteren naar PDF-documenten.
* PDF-documenten converteren naar bestandsindelingen.

>[!NOTE]
>
>Zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63)voor meer informatie over de service PDF genereren.

## Word-documenten converteren naar PDF-documenten {#converting-word-documents-to-pdf-documents}

In deze sectie wordt beschreven hoe u met de API voor genereren een Microsoft Word-document programmatisch kunt converteren naar een PDF-document.

>[!NOTE]
>
>Zie Ondersteuning [voor extra eigen bestandsindelingen](converting-file-formats-pdf.md#adding-support-for-additional-native-file-formats)toevoegen voor meer informatie over extra bestandsindelingen.

>[!NOTE]
>
>Zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63)voor meer informatie over de service PDF genereren.

### Overzicht van de stappen {#summary-of-steps}

Als u een Microsoft Word-document naar een PDF-document wilt converteren, voert u de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak een Generate PDF client.
1. Haal het bestand op dat u naar een PDF-document wilt converteren.
1. Converteer het bestand naar een PDF-document.
1. Haal de resultaten op.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**Een PDF-client genereren**

Voordat u met programmacode een bewerking PDF genereren kunt uitvoeren, maakt u een serviceclient PDF genereren. Als u de Java API gebruikt, maakt u een `GeneratePdfServiceClient` object. Als u de webservice-API gebruikt, maakt u een `GeneratePDFServiceService` object.

**Het bestand dat naar een PDF-document moet worden geconverteerd, ophalen**

Haal het Microsoft Word-document op dat u wilt converteren naar een PDF-document.

**Het bestand converteren naar een PDF-document**

Nadat u de Generate de dienstcliënt van PDF creeert, kunt u de `createPDF2` methode aanhalen. Deze methode heeft informatie nodig over het document dat moet worden geconverteerd, inclusief de bestandsextensie.

**De resultaten ophalen**

Nadat het bestand is geconverteerd naar een PDF-document, kunt u de resultaten ophalen. Nadat u bijvoorbeeld een Word-bestand naar een PDF-document hebt geconverteerd, kunt u het PDF-document ophalen en opslaan.

**Zie ook**

[Word-documenten converteren naar PDF-documenten met de Java API](converting-file-formats-pdf.md#convert-word-documents-to-pdf-documents-using-the-java-api)

[Word-documenten converteren naar PDF-documenten met de webservice-API](converting-file-formats-pdf.md#convert-word-documents-to-pdf-documents-using-the-web-service-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Snelle start voor PDF-service-API genereren](/help/forms/developing/generate-pdf-service-java-api.md#generate-pdf-service-java-api-quick-start-soap)

### Word-documenten converteren naar PDF-documenten met de Java API {#convert-word-documents-to-pdf-documents-using-the-java-api}

Converteer een Microsoft Word-document naar een PDF-document met de Generate PDF API (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-generatepdf-client.jar, op in het klassenpad van uw Java-project.

1. Maak een Generate PDF client.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `GeneratePdfServiceClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Haal het bestand op dat u naar een PDF-document wilt converteren.

   * Maak een `java.io.FileInputStream` object dat staat voor het Word-bestand dat u wilt converteren met behulp van de constructor. Geef een tekenreekswaarde door die de bestandslocatie opgeeft.
   * Maak een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en het `java.io.FileInputStream` object door te geven.

1. Converteer het bestand naar een PDF-document.

   Converteer het bestand naar een PDF-document door de methode van het `GeneratePdfServiceClient` `createPDF2` object aan te roepen en de volgende waarden door te geven:

   * Een `com.adobe.idp.Document` object dat staat voor het bestand dat moet worden omgezet.
   * Een `java.lang.String` object dat de bestandsextensie bevat.
   * Een `java.lang.String` object dat de instellingen voor het bestandstype bevat die moeten worden gebruikt bij de conversie. Instellingen voor bestandstypen bieden conversie-instellingen voor verschillende bestandstypen, zoals .doc of .xls.
   * Een `java.lang.String` object dat de naam bevat van de te gebruiken PDF-instellingen. U kunt bijvoorbeeld opgeven `Standard`.
   * Een `java.lang.String` object dat de naam bevat van de beveiligingsinstellingen die moeten worden gebruikt.
   * Een optioneel `com.adobe.idp.Document` object dat de instellingen bevat die moeten worden toegepast tijdens het genereren van het PDF-document.
   * Een optioneel `com.adobe.idp.Document` object dat metagegevens bevat die op het PDF-document moeten worden toegepast.
   De `createPDF2` methode retourneert een `CreatePDFResult` object dat het nieuwe PDF-document en logboekgegevens bevat. Het logbestand bevat doorgaans fout- of waarschuwingsberichten die worden gegenereerd door de conversieaanvraag.

1. Haal de resultaten op.

   Voer de volgende handelingen uit om het PDF-document te verkrijgen:

   * Roep de `CreatePDFResult` methode van het `getCreatedDocument` object aan, die een `com.adobe.idp.Document` object retourneert.
   * Roep de `com.adobe.idp.Document` methode van het `copyToFile` object aan om het PDF-document te extraheren van het object dat u in de vorige stap hebt gemaakt.
   Als u de `createPDF2` methode hebt gebruikt om het logdocument op te halen (niet van toepassing op HTML-conversies), voert u de volgende handelingen uit:

   * Roep de `CreatePDFResult` methode van het `getLogDocument` object aan. Hiermee wordt een `com.adobe.idp.Document` object geretourneerd.
   * Roep de `com.adobe.idp.Document` methode van het `copyToFile` object aan om het logdocument te extraheren.


**Zie ook**

[Overzicht van de stappen](converting-file-formats-pdf.md#summary-of-steps)

[Snel starten (SOAP-modus): Een Microsoft Word-document converteren naar een PDF-document met de Java API](/help/forms/developing/generate-pdf-service-java-api.md#quick-start-soap-mode-converting-a-microsoft-word-document-to-a-pdf-document-using-the-java-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Word-documenten converteren naar PDF-documenten met de webservice-API {#convert-word-documents-to-pdf-documents-using-the-web-service-api}

Converteer een Microsoft Word-document naar een PDF-document met de API (webservice) voor genereren van PDF:

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/GeneratePDFService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Generate PDF client.

   * Maak een `GeneratePDFServiceClient` object met de standaardconstructor.
   * Maak een `GeneratePDFServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/GeneratePDFService?blob=mtom`.) U hoeft het `lc_version` kenmerk niet te gebruiken. Geef dit echter op `?blob=mtom`.
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `GeneratePDFServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het veld `GeneratePDFServiceClient.ClientCredentials.UserName.UserName`.
      * Wijs de bijbehorende wachtwoordwaarde aan het veld toe `GeneratePDFServiceClient.ClientCredentials.UserName.Password`.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Haal het bestand op dat u naar een PDF-document wilt converteren.

   * Maak een `BLOB` object met de constructor ervan. Het `BLOB` object wordt gebruikt om het bestand op te slaan dat u naar een PDF-document wilt converteren.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die de bestandslocatie vertegenwoordigt van het bestand dat moet worden omgezet en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de methode van het `System.IO.FileStream` `Read` object aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` object door de inhoud van de bytearray aan de `MTOM` eigenschap toe te wijzen.

1. Converteer het bestand naar een PDF-document.

   Converteer het bestand naar een PDF-document door de methode van het `GeneratePDFServiceService` `CreatePDF2` object aan te roepen en de volgende waarden door te geven:

   * Een `BLOB` object dat het te converteren bestand vertegenwoordigt.
   * Een tekenreeks die de bestandsextensie bevat.
   * Een `java.lang.String` object dat de instellingen voor het bestandstype bevat die moeten worden gebruikt bij de conversie. Instellingen voor bestandstypen bieden conversie-instellingen voor verschillende bestandstypen, zoals .doc of .xls.
   * Een tekenreeksobject dat de te gebruiken PDF-instellingen bevat. U kunt opgeven `Standard`.
   * Een tekenreeksobject dat de beveiligingsinstellingen bevat die moeten worden gebruikt. U kunt opgeven `No Security`.
   * Een optioneel `BLOB` object dat de instellingen bevat die moeten worden toegepast tijdens het genereren van het PDF-document.
   * Een optioneel `BLOB` object dat metagegevens bevat die op het PDF-document moeten worden toegepast.
   * Een uitvoerparameter van type `BLOB` die door de `CreatePDF2` methode wordt bevolkt. De `CreatePDF2` methode vult dit object met het omgezette document. (Deze parameterwaarde is alleen vereist voor aanroepen van een webservice.)
   * Een uitvoerparameter van type `BLOB` die door de `CreatePDF2` methode wordt bevolkt. De `CreatePDF2` methode vult dit object met het logdocument. (Deze parameterwaarde is alleen vereist voor aanroepen van een webservice.)

1. Haal de resultaten op.

   * Haal het geconverteerde PDF-document op door het `BLOB` veld van het `MTOM` object toe te wijzen aan een bytearray. De bytearray vertegenwoordigt het geconverteerde PDF-document. Zorg ervoor dat u het `BLOB` object gebruikt als uitvoerparameter voor de `createPDF2` methode.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het geconverteerde PDF-document vertegenwoordigt.
   * Maak een `System.IO.BinaryWriter` object door de constructor ervan aan te roepen en het `System.IO.FileStream` object door te geven.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door de methode van het `System.IO.BinaryWriter` `Write` object aan te roepen en de bytearray door te geven.

**Zie ook**

[Overzicht van de stappen](converting-file-formats-pdf.md#summary-of-steps)

[AEM-formulieren aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM-formulieren aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## HTML-documenten converteren naar PDF-documenten {#converting-html-documents-to-pdf-documents}

In deze sectie wordt beschreven hoe u met de API voor genereren van PDF HTML-documenten programmatisch kunt converteren naar PDF-documenten.

>[!NOTE]
>
>Zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63)voor meer informatie over de service PDF genereren.

### Overzicht van de stappen {#summary_of_steps-1}

Voer de volgende taken uit om een HTML-document te converteren naar een PDF-document:

1. Inclusief projectbestanden.
1. Maak een Generate PDF client.
1. Haal de HTML-inhoud op die u naar een PDF-document wilt converteren.
1. Zet de HTML-inhoud om in een PDF-document.
1. Haal de resultaten op.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**Een PDF-client genereren**

Voordat u met programmacode een bewerking PDF genereren kunt uitvoeren, moet u een serviceclient PDF genereren maken. Als u de Java API gebruikt, maakt u een `GeneratePdfServiceClient` object. Als u de webservice-API gebruikt, maakt u een `GeneratePDFServiceService`.

**De HTML-inhoud ophalen die naar een PDF-document moet worden geconverteerd**

Verwijs naar HTML-inhoud die u naar een PDF-document wilt converteren. U kunt verwijzen naar HTML-inhoud, zoals een HTML-bestand of HTML-inhoud die toegankelijk is via een URL.

**De HTML-inhoud converteren naar een PDF-document**

Nadat u de serviceclient hebt gemaakt, kunt u de juiste bewerking voor het maken van PDF&#39;s uitvoeren. Voor deze bewerking is informatie nodig over het document dat moet worden geconverteerd, inclusief het pad naar het doeldocument.

**De resultaten ophalen**

Nadat de HTML-inhoud is geconverteerd naar een PDF-document, kunt u de resultaten ophalen en het PDF-document opslaan.

**Zie ook**

[HTML-inhoud converteren naar een PDF-document met de Java API](converting-file-formats-pdf.md#convert-html-content-to-a-pdf-document-using-the-java-api)

[HTML-inhoud converteren naar een PDF-document met de webservice-API](converting-file-formats-pdf.md#convert-html-content-to-a-pdf-document-using-the-web-service-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Snelle start voor PDF-service-API genereren](/help/forms/developing/generate-pdf-service-java-api.md#generate-pdf-service-java-api-quick-start-soap)

### HTML-inhoud converteren naar een PDF-document met de Java API {#convert-html-content-to-a-pdf-document-using-the-java-api}

Een HTML-document converteren naar een PDF-document met de Generate PDF API (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-generatepdf-client.jar, op in het klassenpad van uw Java-project.

1. Maak een Generate PDF client.

   Maak een `GeneratePdfServiceClient` object door de constructor ervan te gebruiken en een `ServiceClientFactory` object door te geven dat verbindingseigenschappen bevat.

1. Haal de HTML-inhoud op die u naar een PDF-document wilt converteren.

   Haal HTML-inhoud op door een tekenreeksvariabele te maken en een URL toe te wijzen die naar HTML-inhoud wijst.

1. Zet de HTML-inhoud om in een PDF-document.

   Roep de methode van het `GeneratePdfServiceClient` `htmlToPDF2` object aan en geef de volgende waarden door:

   * Een `java.lang.String` object dat de URL bevat van het te converteren HTML-bestand.
   * Een `java.lang.String` object dat de instellingen voor het bestandstype bevat die moeten worden gebruikt bij de conversie. Instellingen voor bestandstypen kunnen spinningsniveaus bevatten.
   * Een `java.lang.String` object dat de naam bevat van de beveiligingsinstellingen die moeten worden gebruikt.
   * Een optioneel `com.adobe.idp.Document` object dat de instellingen bevat die moeten worden toegepast tijdens het genereren van het PDF-document. Als deze informatie niet wordt verstrekt, worden de montages automatisch gekozen gebaseerd op de vorige drie parameters.
   * Een optioneel `com.adobe.idp.Document` object dat metagegevens bevat die op het PDF-document moeten worden toegepast.

1. Haal de resultaten op.

   De `htmlToPDF2` methode retourneert een `HtmlToPdfResult` object dat het nieuwe PDF-document bevat dat is gegenereerd. Voer de volgende handelingen uit om het nieuwe PDF-document te verkrijgen:

   * Roep de `HtmlToPdfResult` methode van het `getCreatedDocument` object aan. Hiermee wordt een `com.adobe.idp.Document` object geretourneerd.
   * Roep de `com.adobe.idp.Document` methode van het `copyToFile` object aan om het PDF-document te extraheren van het object dat u in de vorige stap hebt gemaakt.

**Zie ook**

[HTML-documenten converteren naar PDF-documenten](converting-file-formats-pdf.md#converting-html-documents-to-pdf-documents)

[Snel starten (SOAP-modus): HTML-inhoud converteren naar een PDF-document met de Java API](/help/forms/developing/generate-pdf-service-java-api.md#quick-start-soap-mode-converting-html-content-to-a-pdf-document-using-the-java-api)

[Snel starten (SOAP-modus): HTML-inhoud converteren naar een PDF-document met de Java API](/help/forms/developing/generate-pdf-service-java-api.md#quick-start-soap-mode-converting-html-content-to-a-pdf-document-using-the-java-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### HTML-inhoud converteren naar een PDF-document met de webservice-API {#convert-html-content-to-a-pdf-document-using-the-web-service-api}

HTML-inhoud converteren naar een PDF-document met de functie PDF API genereren (webservice):

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/GeneratePDFService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Generate PDF client.

   * Maak een `GeneratePDFServiceClient` object met de standaardconstructor.
   * Maak een `GeneratePDFServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/GeneratePDFService?blob=mtom`.) U hoeft het `lc_version` kenmerk niet te gebruiken. Geef dit echter op `?blob=mtom`.
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `GeneratePDFServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het veld `GeneratePDFServiceClient.ClientCredentials.UserName.UserName`.
      * Wijs de bijbehorende wachtwoordwaarde aan het veld toe `GeneratePDFServiceClient.ClientCredentials.UserName.Password`.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Haal de HTML-inhoud op die u naar een PDF-document wilt converteren.

   Haal HTML-inhoud op door een tekenreeksvariabele te maken en een URL toe te wijzen die naar HTML-inhoud wijst.

1. Zet de HTML-inhoud om in een PDF-document.

   Converteer de HTML-inhoud naar een PDF-document door de methode van het `GeneratePDFServiceService` `HtmlToPDF2` object aan te roepen en geef de volgende waarden door:

   * Een tekenreeks die de HTML-inhoud bevat die moet worden omgezet.
   * Een `java.lang.String` object dat de instellingen voor het bestandstype bevat die moeten worden gebruikt bij de conversie.
   * Een tekenreeksobject dat de beveiligingsinstellingen bevat die moeten worden gebruikt.
   * Een optioneel `BLOB` object dat de instellingen bevat die moeten worden toegepast tijdens het genereren van het PDF-document.
   * Een optioneel `BLOB` object dat metagegevens bevat die op het PDF-document moeten worden toegepast.
   * Een uitvoerparameter van type `BLOB` die door de `CreatePDF2` methode wordt bevolkt. De `CreatePDF2` methode vult dit object met het omgezette document. (Deze parameterwaarde is alleen vereist voor aanroepen van een webservice.)

1. Haal de resultaten op.

   * Haal het geconverteerde PDF-document op door het `BLOB` veld van het `MTOM` object toe te wijzen aan een bytearray. De bytearray vertegenwoordigt het geconverteerde PDF-document. Zorg ervoor dat u het `BLOB` object gebruikt als uitvoerparameter voor de `HtmlToPDF2` methode.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het geconverteerde PDF-document vertegenwoordigt.
   * Maak een `System.IO.BinaryWriter` object door de constructor ervan aan te roepen en het `System.IO.FileStream` object door te geven.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door de methode van het `System.IO.BinaryWriter` `Write` object aan te roepen en de bytearray door te geven.

**Zie ook**

[HTML-documenten converteren naar PDF-documenten](converting-file-formats-pdf.md#converting-html-documents-to-pdf-documents)

[AEM-formulieren aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM-formulieren aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## PDF-documenten converteren naar niet-afbeeldingsindelingen {#converting-pdf-documents-to-non-image-formats}

In deze sectie wordt beschreven hoe u met de API voor het genereren van PDF Java en de webservice-API een PDF-document programmatisch kunt converteren naar een RTF-bestand. Dit is een voorbeeld van een niet-afbeeldingsindeling. Andere indelingen die geen afbeeldingen bevatten, zijn HTML, tekst, DOC en EPS. Wanneer u een PDF-document converteert naar RTF, moet u ervoor zorgen dat het PDF-document geen formulierelementen bevat, zoals een verzendknop. Formulierelementen worden niet geconverteerd.

>[!NOTE]
>
>Zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63)voor meer informatie over de service PDF genereren.

### Overzicht van de stappen {#summary_of_steps-2}

Voer de volgende stappen uit om een PDF-document te converteren naar een van de ondersteunde typen:

1. Inclusief projectbestanden.
1. Maak een Generate PDF client.
1. Hiermee haalt u het te converteren PDF-document op.
1. Converteer het PDF-document.
1. Sla het geconverteerde bestand op.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**Een PDF-client genereren**

Voordat u met programmacode een bewerking PDF genereren kunt uitvoeren, moet u een serviceclient PDF genereren maken. Als u de Java API gebruikt, maakt u een `GeneratePdfServiceClient` object. Als u de webservice-API gebruikt, maakt u een `GeneratePDFServiceService` object.

**Het te converteren PDF-document ophalen**

Haal het PDF-document op dat u wilt converteren naar een andere indeling dan afbeeldingen.

**Het PDF-document converteren**

Nadat u de serviceclient hebt gemaakt, kunt u de PDF-exportbewerking activeren. Voor deze bewerking is informatie nodig over het document dat moet worden geconverteerd, inclusief het pad naar het doeldocument.

**Het omgezette bestand opslaan**

Sla het geconverteerde bestand op. Als u bijvoorbeeld een PDF-document converteert naar een RTF-bestand, slaat u het geconverteerde document op in een RTF-bestand.

**Zie ook**

[Een PDF-document converteren naar een RTF-bestand met de Java API](converting-file-formats-pdf.md#convert-a-pdf-document-to-a-rtf-file-using-the-java-api)

[Een PDF-document converteren naar een RTF-bestand met de webservice-API](converting-file-formats-pdf.md#convert-a-pdf-document-to-a-rtf-file-using-the-web-service-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Snelle start voor PDF-service-API genereren](/help/forms/developing/generate-pdf-service-java-api.md#generate-pdf-service-java-api-quick-start-soap)

### Een PDF-document converteren naar een RTF-bestand met de Java API {#convert-a-pdf-document-to-a-rtf-file-using-the-java-api}

Een PDF-document converteren naar een RTF-bestand met de Generate PDF API (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-generatepdf-client.jar, op in het klassenpad van uw Java-project.

1. Maak een Generate PDF client.

   Maak een `GeneratePdfServiceClient` object door de constructor ervan te gebruiken en een `ServiceClientFactory` object door te geven dat verbindingseigenschappen bevat.

1. Hiermee haalt u het te converteren PDF-document op.

   * Maak een `java.io.FileInputStream` object dat staat voor het PDF-document dat u wilt converteren met behulp van de constructor. Geef een tekenreekswaarde door die de locatie van het PDF-document aangeeft.
   * Maak een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en het `java.io.FileInputStream` object door te geven.

1. Converteer het PDF-document.

   Roep de methode van het `GeneratePdfServiceClient` `exportPDF2` object aan en geef de volgende waarden door:

   * Een `com.adobe.idp.Document` object dat staat voor het PDF-bestand dat moet worden geconverteerd.
   * Een `java.lang.String` object dat de naam bevat van het bestand dat moet worden omgezet.
   * Een `java.lang.String` object met de naam van de Adobe PDF-instellingen.
   * Een `ConvertPDFFormatType` object dat het doelbestandstype voor de conversie opgeeft.
   * Een optioneel `com.adobe.idp.Document` object dat de instellingen bevat die moeten worden toegepast tijdens het genereren van het PDF-document.
   De `exportPDF2` methode retourneert een `ExportPDFResult` object dat het omgezette bestand bevat.

1. Converteer het PDF-document.

   Voer de volgende handelingen uit om het nieuwe bestand te verkrijgen:

   * Roep de `ExportPDFResult` methode van het `getConvertedDocument` object aan. Hiermee wordt een `com.adobe.idp.Document` object geretourneerd.
   * Roep de `com.adobe.idp.Document` methode van het `copyToFile` object aan om het nieuwe document te extraheren.

**Zie ook**

[Overzicht van de stappen](converting-file-formats-pdf.md#summary-of-steps)

[Snel starten (SOAP-modus): HTML-inhoud converteren naar een PDF-document met de Java API](/help/forms/developing/generate-pdf-service-java-api.md#quick-start-soap-mode-converting-html-content-to-a-pdf-document-using-the-java-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een PDF-document converteren naar een RTF-bestand met de webservice-API {#convert-a-pdf-document-to-a-rtf-file-using-the-web-service-api}

Een PDF-document converteren naar een RTF-bestand met de API (webservice) voor genereren van PDF:

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/GeneratePDFService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Generate PDFf client.

   * Maak een `GeneratePDFServiceClient` object met de standaardconstructor.
   * Maak een `GeneratePDFServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/GeneratePDFService?blob=mtom`.) U hoeft het `lc_version` kenmerk niet te gebruiken. Geef dit echter op `?blob=mtom`.
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `GeneratePDFServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het veld `GeneratePDFServiceClient.ClientCredentials.UserName.UserName`.
      * Wijs de bijbehorende wachtwoordwaarde aan het veld toe `GeneratePDFServiceClient.ClientCredentials.UserName.Password`.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Hiermee haalt u het te converteren PDF-document op.

   * Maak een `BLOB` object met de constructor ervan. Met dit `BLOB` object wordt een geconverteerd PDF-document opgeslagen.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de methode van het `System.IO.FileStream` `Read` object aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` object door de inhoud van de bytearray aan de `MTOM` eigenschap toe te wijzen.

1. Converteer het PDF-document.

   Roep de methode van het `GeneratePDFServiceServiceWse` `ExportPDF2` object aan en geef de volgende waarden door:

   * Een `BLOB` object dat staat voor het PDF-bestand dat moet worden geconverteerd.
   * Een tekenreeks die de padnaam bevat van het bestand dat moet worden omgezet.
   * Een `java.lang.String` object dat de bestandslocatie opgeeft.
   * Een tekenreeksobject dat het doelbestandstype voor de conversie opgeeft. Geef `RTF`op.
   * Een optioneel `BLOB` object dat de instellingen bevat die moeten worden toegepast tijdens het genereren van het PDF-document.
   * Een uitvoerparameter van type `BLOB` die door de `ExportPDF2` methode wordt bevolkt. De `ExportPDF2` methode vult dit object met het omgezette document. (Deze parameterwaarde is alleen vereist voor aanroepen van een webservice.)

1. Sla het geconverteerde bestand op.

   * Haal het omgezette RTF-document op door het `BLOB` `MTOM` objectveld aan een bytearray toe te wijzen. De bytearray vertegenwoordigt het omgezette RTF-document. Zorg ervoor dat u het `BLOB` object gebruikt als uitvoerparameter voor de `ExportPDF2` methode.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die de locatie van het RTF-bestand vertegenwoordigt.
   * Maak een `System.IO.BinaryWriter` object door de constructor ervan aan te roepen en het `System.IO.FileStream` object door te geven.
   * Schrijf de inhoud van de bytearray naar een RTF-bestand door de methode van het `System.IO.BinaryWriter` `Write` object aan te roepen en de bytearray door te geven.

**Zie ook**

[Overzicht van de stappen](converting-file-formats-pdf.md#summary-of-steps)

[AEM-formulieren aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM-formulieren aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Ondersteuning toevoegen voor extra eigen bestandsindelingen {#adding-support-for-additional-native-file-formats}

In deze sectie wordt uitgelegd hoe u ondersteuning voor extra eigen bestandsindelingen kunt toevoegen. Het biedt een overzicht van de interactie tussen de service PDF genereren en de native toepassingen die deze service gebruikt om native bestandsindelingen te converteren naar PDF.

In dit gedeelte wordt ook het volgende uitgelegd:

* De reactie van de service PDF genereren wijzigen op de native toepassingen die dit product al gebruikt om native bestandsindelingen te converteren naar PDF
* De interactie tussen de service PDF genereren, de component PDF-service Application Monitor (AppMon) genereren en native toepassingen, zoals Microsoft Word
* De rollen die de grammen van XML in die interactie spelen

### Componentinteracties {#component-interactions}

De service PDF genereren converteert oorspronkelijke bestandsindelingen door de toepassing aan te roepen die is gekoppeld aan de bestandsindeling en vervolgens te communiceren met de toepassing om het document af te drukken met de standaardprinter. De standaardprinter moet zijn ingesteld als Adobe PDF-printer.

In deze illustratie worden de componenten en stuurprogramma&#39;s weergegeven die zijn betrokken bij native toepassingsondersteuning. Ook worden de XML-grammen genoemd die de interacties beïnvloeden.

Interacties van componenten voor conversie van native bestanden

In dit document wordt de term *native toepassing* gebruikt om aan te geven welke toepassing wordt gebruikt om een native bestandsindeling te maken, zoals Microsoft Word.

*AppMon* is een ondernemingscomponent die met een inheemse toepassing op dezelfde manier interactie aangaat als een gebruiker door de dialoogdozen zou navigeren die door die toepassing worden voorgesteld. De grammars van XML die door AppMon worden gebruikt om een toepassing, zoals Microsoft Word, op te dragen om een dossier te openen en te drukken impliceren deze opeenvolgende taken:

1. Het bestand openen door Bestand > Openen te selecteren
1. Ervoor zorgen dat het dialoogvenster Openen wordt weergegeven; zo niet, de fout afhandelen
1. Bestandsnaam opgeven in het veld Bestandsnaam en vervolgens op de knop Openen klikken
1. Ervoor zorgen dat het bestand daadwerkelijk wordt geopend
1. Het dialoogvenster Afdrukken openen door Bestand > Afdrukken te selecteren
1. Het dialoogvenster Afdrukken wordt weergegeven

AppMon gebruikt standaard Win32 APIs om met derdetoepassingen in wisselwerking te staan om gebeurtenissen over te brengen UI zoals zeer belangrijke slagen en muiskliks, die nuttig is om deze toepassingen te controleren om PDF dossiers van hen te produceren.

Vanwege een beperking met deze Win32 APIs, kan AppMon deze gebeurtenissen UI aan sommige specifieke soorten vensters, zoals floating menu-bars (die in sommige toepassingen zoals TextPad worden gevonden), en bepaalde soorten dialogen niet verzenden de waarvan inhoud niet kan worden teruggewonnen gebruikend Win32 APIs.

Een zwevende menubalk kan gemakkelijk visueel worden geïdentificeerd. het is echter mogelijk dat de speciale soorten dialogen niet door visuele inspectie kunnen worden geïdentificeerd . U zou een derdetoepassing zoals Microsoft Spy++ (deel van de Microsoft Visuele C++ ontwikkelomgeving) of zijn gelijkwaardige WinID (die gratis van kosten van [https://www.dennisbabkin.com/php/download.php?what=WinID](https://www.dennisbabkin.com/php/download.php?what=WinID)kan worden gedownload) vereisen om een dialoog te onderzoeken om te bepalen als AppMon met het gebruikend standaardWin32 APIs zou kunnen in wisselwerking staan.

Als WinID de dialooginhoud zoals tekst, subvensters, vensterklasse ID, etc. kan halen, dan zou AppMon het zelfde ook kunnen doen.

In deze tabel wordt het type informatie weergegeven dat wordt gebruikt bij het afdrukken van eigen bestandsindelingen.

<table>
 <thead>
  <tr>
   <th><p>Het type Informatie</p></th>
   <th><p>Beschrijving</p></th>
   <th><p>Items die betrekking hebben op native bestanden wijzigen/maken </p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>Administratieve instellingen </p></td>
   <td><p>Hier vindt u PDF-instellingen, beveiligingsinstellingen en instellingen voor het bestandstype. </p><p>Instellingen voor bestandstypen koppelen bestandsextensies aan de corresponderende native toepassingen. Instellingen voor bestandstypen geven ook instellingen voor native toepassingen op die worden gebruikt om eigen bestanden af te drukken. </p></td>
   <td><p>Als u instellingen voor een reeds ondersteunde native toepassing wilt wijzigen, stelt de systeembeheerder de instellingen voor bestandstypen in de beheerconsole in. </p><p>Als u ondersteuning voor een nieuwe eigen bestandsindeling wilt toevoegen, moet u het bestand handmatig bewerken. (Zie Ondersteuning <a href="converting-file-formats-pdf.md#adding-or-modifying-support-for-a-native-file-format">toevoegen of wijzigen voor een eigen bestandsindeling</a>.) </p></td>
  </tr>
  <tr>
   <td><p>Script </p></td>
   <td><p>Hiermee geeft u interacties op tussen de service PDF genereren en een native toepassing. Dergelijke interacties leiden de toepassing doorgaans om een bestand af te drukken naar het Adobe PDF-stuurprogramma. </p><p>Het script bevat instructies die de oorspronkelijke toepassing de opdracht geven specifieke dialoogvensters te openen en die specifieke reacties bieden op velden en knoppen in die dialoogvensters. </p></td>
   <td><p>De service PDF genereren bevat scriptbestanden voor alle ondersteunde native toepassingen. U kunt deze bestanden wijzigen met een XML-bewerkingstoepassing.</p><p>Als u ondersteuning voor een nieuwe native toepassing wilt toevoegen, moet u een nieuw scriptbestand maken. (Zie Een XML-bestand met een extra dialoogvenster <a href="converting-file-formats-pdf.md#creating-or-modifying-an-additional-dialog-xml-file-for-a-native-application">maken of wijzigen voor een native toepassing</a>.) </p></td>
  </tr>
  <tr>
   <td><p>Instructies in het dialoogvenster Algemeen </p></td>
   <td><p>Hiermee geeft u op hoe moet worden gereageerd op dialoogvensters die in meerdere toepassingen worden gebruikt. Dergelijke dialoogvensters worden gegenereerd door besturingssystemen, helpertoepassingen (zoals PDFMaker) en stuurprogramma's. </p><p>Het bestand dat deze informatie bevat, is appmon.global.en_US.xml.</p></td>
   <td><p>Wijzig dit bestand niet. </p></td>
  </tr>
  <tr>
   <td><p>Instructies in het dialoogvenster Toepassingsspecifiek</p></td>
   <td><p>Geeft aan hoe moet worden gereageerd op toepassingsspecifieke dialoogvensters. </p><p>Het bestand dat deze informatie bevat, is appmon.<i>`[appname]'</i>.dialog.<i>`[locale]'</i>.xml (bijvoorbeeld appmon.word.en_US.xml).</p></td>
   <td><p>Wijzig dit bestand niet. </p><p>Zie <a href="converting-file-formats-pdf.md#creating_or_modifying_an_additional_dialog_xml_file_for_a_native_application">Een XML-bestand voor een native toepassing maken of wijzigen als u dialoogvensterinstructies voor een nieuwe native toepassing</a>wilt toevoegen.</p></td>
  </tr>
  <tr>
   <td><p>Aanvullende toepassingsspecifieke dialoogvensterinstructies </p></td>
   <td><p>Hiermee geeft u overschrijvingen en toevoegingen aan de instructies in het specifieke dialoogvenster voor de toepassing op. De sectie bevat een voorbeeld van dergelijke informatie. </p><p>Het bestand dat deze informatie bevat, is appmon.<i>`[appname]'</i>.adding.<i>`[locale]'</i>.xml. Een voorbeeld is appmon.adding.nl_NL.xml.</p></td>
   <td><p>Bestanden van dit type kunnen worden gemaakt en gewijzigd met behulp van een XML-bewerkingstoepassing. (Zie Een XML-bestand met een extra dialoogvenster <a href="converting-file-formats-pdf.md#creating-or-modifying-an-additional-dialog-xml-file-for-a-native-application">maken of wijzigen voor een native toepassing</a>.) </p><p><strong>Belangrijk</strong>: U moet extra toepassingsspecifieke dialoogvakinstructies voor elke inheemse toepassing creëren uw server zal steunen. </p></td>
  </tr>
 </tbody>
</table>

### Over het script en het dialoogvenster in XML-bestanden {#about-the-script-and-dialog-xml-files}

In XML-scriptbestanden wordt de service PDF genereren gebruikt om door de dialoogvensters van toepassingen te navigeren, net zoals een gebruiker door de dialoogvensters van de toepassing zou navigeren. ScriptXML-bestanden zorgen er ook voor dat de service PDF genereren reageert op dialoogvensters door handelingen uit te voeren zoals het indrukken van knoppen, het selecteren of deselecteren van selectievakjes of het selecteren van menu-items.

Dialoogbestanden in XML-bestanden reageren daarentegen gewoon op dialoogvensters met dezelfde typen handelingen als in XML-scriptbestanden.

#### Dialoogvenster en terminologie van vensterelementen {#dialog-box-and-window-element-terminology}

Deze sectie en de volgende sectie gebruiken verschillende terminologie voor dialoogvakjes en de componenten die zij, afhankelijk van het perspectief bevatten dat wordt beschreven. De componenten van dialoogvensters zijn punten zoals knopen, gebieden, en combovakjes.

Wanneer deze sectie en de volgende sectie dialoogvensters en hun componenten vanuit het perspectief van een gebruiker beschrijven, worden termen zoals *dialoogdoos*, *knoop*, *gebied*, en *combodoos* gebruikt.

Wanneer deze sectie en de volgende sectie dialoogvensters en hun componenten vanuit het perspectief van hun interne vertegenwoordiging beschrijven, wordt de term *vensterelement* gebruikt. De interne representatie van vensterelementen is een hiërarchie, waarbij elke instantie van een vensterelement wordt aangeduid met labels. De instantie van het vensterelement beschrijft ook zijn fysieke kenmerken en gedrag.

Vanuit het perspectief van de gebruiker vertonen de dialoogvensters en hun componenten verschillende gedragingen, waarbij bepaalde elementen van dialoogvensters verborgen zijn totdat ze worden geactiveerd. Vanuit het perspectief van de interne vertegenwoordiging, bestaat zulk een kwestie van gedrag niet. De interne representatie van een dialoogvenster ziet er bijvoorbeeld hetzelfde uit als de componenten die het bevat, met als uitzondering dat de componenten in het dialoogvenster zijn genest.

Deze sectie beschrijft de elementen van XML die AppMon van instructies voorzien. Deze elementen hebben namen zoals het `dialog` element en het `window` element. In dit document wordt een font met vaste spatiëring gebruikt om XML-elementen te onderscheiden. Het `dialog` element identificeert een dialoogdoos die een het manuscriptdossier van XML kan veroorzaken om, of opzettelijk of onbedoeld worden getoond. Het `window` element identificeert een vensterelement (dialoogvenster of de componenten van een dialoogvenster).

#### Hiërarchie {#hierarchy}

Dit diagram toont de hiërarchie van manuscript en dialoogXML. Een script-XML-bestand voldoet aan het script.xsd-schema, dat (in XML-zin) het window.xsd-schema bevat. Op dezelfde manier voldoet een dialoogXML- dossier aan het dialogs.xsd schema, dat ook het window.xsd schema omvat.

![as_as_xml_hiërarchie](assets/as_as_xml_hierarchy.png)

Hiërarchie van script en dialoogvenster XML

#### Script XML-bestanden {#script-xml-files}

Een *script-XML-bestand* geeft een reeks stappen aan die de native toepassing de opdracht geven naar bepaalde vensterelementen te navigeren en vervolgens reacties op die elementen te leveren. De meeste reacties zijn tekst of toetsaanslagen die overeenkomen met de invoer die een gebruiker zou invoeren in een veld, keuzelijst met invoervak of knop in het bijbehorende dialoogvenster.

Met de ondersteuning van de service PDF genereren voor XML-scriptbestanden wordt beoogd een native toepassing te laten afdrukken. ScriptXML-bestanden kunnen echter worden gebruikt om elke taak uit te voeren die een gebruiker kan uitvoeren bij het werken met de dialoogvensters van de native toepassing.

De stappen in een script-XML-bestand worden in de juiste volgorde uitgevoerd, zonder dat er sprake is van vertakking. De enige voorwaardelijke test die wordt ondersteund, is for time-out/retry. Hiermee wordt een script beëindigd als een stap niet binnen een bepaalde periode en na een bepaald aantal keren is voltooid.

Naast stappen die opeenvolgend zijn, worden de instructies binnen een stap ook uitgevoerd in volgorde. U moet ervoor zorgen dat de stappen en de instructies de orde weerspiegelen waarin een gebruiker die zelfde stappen zou uitvoeren.

Elke stap in een XML-scriptbestand identificeert het vensterelement dat wordt weergegeven als de instructies van de stap correct zijn uitgevoerd. Als tijdens het uitvoeren van een scriptstap een onverwacht dialoogvenster wordt weergegeven, zoekt de dienst PDF genereren de XML-bestanden van het dialoogvenster zoals beschreven in de volgende sectie.

#### Dialoogvenster XML-bestanden {#dialog-xml-files}

Wanneer u native toepassingen uitvoert, worden verschillende dialoogvensters weergegeven, ongeacht of de native toepassingen zich in een zichtbare of onzichtbare modus bevinden. De dialoogvensters kunnen worden gegenereerd door het besturingssysteem of door de toepassing zelf. Wanneer native toepassingen worden uitgevoerd onder controle van de Generate PDF service, worden de dialoogvensters van het systeem en de native toepassing weergegeven in een onzichtbaar venster.

In een XML-bestand *van het* dialoogvenster wordt aangegeven hoe de service PDF genereren reageert op dialoogvensters van het systeem of de oorspronkelijke toepassing. Met de XML-bestanden in het dialoogvenster Genereren kan de service PDF genereren reageren op dialoogvensters die niet worden gevraagd, zodat het conversieproces wordt vergemakkelijkt.

Wanneer het systeem of de native toepassing een dialoogvenster weergeeft dat niet wordt afgehandeld door het XML-scriptbestand dat momenteel wordt uitgevoerd, worden de XML-bestanden van het dialoogvenster Genereren in deze volgorde doorzocht, en wordt gestopt wanneer er een overeenkomst wordt gevonden:

* appmon.`[appname]`.additional.`[locale]`.xml
* appmon.`[appname]`.`[locale]`.xml (wijzig dit bestand niet.)
* appmon.global.`[locale]`.xml (wijzig dit bestand niet.)

Als bij de service PDF genereren een overeenkomst wordt gevonden voor het dialoogvenster, wordt dit verwijderd door het de toetsaanslag of andere actie te verzenden die voor het dialoogvenster is opgegeven. Als in de instructies voor het dialoogvenster een afbreekbericht wordt opgegeven, wordt de taak die momenteel wordt uitgevoerd door de service PDF genereren beëindigd en wordt een foutbericht gegenereerd. Zo&#39;n afbreekbericht zou in het `abortMessage` element in de grammatica van manuscriptXML worden gespecificeerd.

Als in de service PDF genereren een dialoogvenster wordt weergegeven dat niet wordt beschreven in eerder vermelde bestanden, neemt de service PDF genereren het bijschrift van het dialoogvenster op in het logbestandsitem. De taak die momenteel wordt uitgevoerd, wordt uiteindelijk uitgerekt. Vervolgens kunt u de informatie in het logbestand gebruiken om nieuwe instructies samen te stellen in het XML-bestand van het extra dialoogvenster voor de oorspronkelijke toepassing.

### Ondersteuning voor een eigen bestandsindeling toevoegen of wijzigen {#adding-or-modifying-support-for-a-native-file-format}

In deze sectie worden de taken beschreven die u moet uitvoeren om andere native bestandsindelingen te ondersteunen of om ondersteuning voor een reeds ondersteunde native bestandsindeling te wijzigen.

Voordat u ondersteuning kunt toevoegen of wijzigen, moet u de volgende taken uitvoeren.

#### Een gereedschap kiezen voor het identificeren van vensterelementen {#choosing-a-tool-for-identifying-window-elements}

De dialoog en de dossiers van manuscriptXML vereisen u om het vensterelement (dialoogdoos, gebied, of andere component van de dialoog) te identificeren waaraan uw dialoog of manuscriptelement antwoordt. Nadat een script bijvoorbeeld een menu voor een native toepassing heeft aangeroepen, moet het script het vensterelement in dat menu identificeren waarop toetsaanslagen of een handeling moeten worden toegepast.

U kunt een dialoogvenster gemakkelijk herkennen aan het bijschrift dat wordt weergegeven in de titelbalk. Nochtans, moet u een hulpmiddel zoals Microsoft Spy++ gebruiken om laag-vlakke vensterelementen te identificeren. De vensterelementen op een lager niveau kunnen worden geïdentificeerd aan de hand van verschillende kenmerken, die niet voor de hand liggen. Bovendien kan elke native toepassing het vensterelement anders identificeren. Dientengevolge, zijn er veelvoudige manieren om een vensterelement te identificeren. Hier volgt de voorgestelde volgorde voor het overwegen van de identificatie van vensterelementen:

1. Bijschrift zelf als dit uniek is
1. Besturings-id die al dan niet uniek is voor een bepaald dialoogvenster
1. Klassenaam, die al dan niet uniek is

Om het even welke één of een combinatie van deze drie attributen kunnen worden gebruikt om een venster te identificeren.

Als de kenmerken een bijschrift niet identificeren, kunt u in plaats daarvan een vensterelement identificeren door de index ervan ten opzichte van het bovenliggende element te gebruiken. Een *index* geeft de positie van het vensterelement ten opzichte van de elementen van het venster op hetzelfde niveau aan. Indexen zijn vaak de enige manier om keuzelijsten met invoervak te identificeren.

Wees op de hoogte van deze problemen:

* Microsoft Spy++ geeft bijschriften weer met behulp van een en-teken (&amp;) om de hot key van het bijschrift te identificeren. Zo wordt bijvoorbeeld in Spry+ het bijschrift voor één dialoogvenster Afdrukken weergegeven als `Pri&nt`, wat aangeeft dat de sneltoets *n* is. Titels van bijschriften in script- en dialoogvenster-XML-bestanden moeten ampersands weglaten.
* Sommige bijschriften bevatten regeleinden. Met de service PDF genereren kunnen geen regeleinden worden geïdentificeerd. Als een bijschrift een regeleinde bevat, neemt u genoeg van het bijschrift op om het te onderscheiden van de andere menu-items en gebruikt u vervolgens reguliere expressies voor het weggelaten deel. Een voorbeeld is ( `^Long caption title$`).]. (Zie Reguliere expressies [gebruiken in bijschriftkenmerken](converting-file-formats-pdf.md#using-regular-expressions-in-caption-attributes).)
* Gebruik tekeneenheden (ook wel escape-reeksen genoemd) voor gereserveerde XML-tekens. Gebruik bijvoorbeeld `&` voor ampersanden `<` en `>` voor kleiner dan en groter dan symbolen, `&apos;` voor apostroffen en `&quot;` voor aanhalingstekens.

Als u aan dialoog of manuscriptdossiers van XML van plan bent te werken, zou u de toepassing Microsoft Spy++ moeten installeren.

#### Het verpakken van dialoogvenster- en scriptbestanden opheffen {#unpackaging-the-dialog-and-script-files}

Het dialoogvenster- en scriptbestand bevinden zich in het bestand appmondata.jar. Voordat u een van deze bestanden kunt wijzigen of nieuwe script- of dialoogbestanden kunt toevoegen, moet u het pakket van dit JAR-bestand opheffen. Stel dat u ondersteuning wilt toevoegen voor de toepassing EditPlus. U maakt twee XML-bestanden met de namen appmon.editplus.script.en_US.xml en appmon.editplus.script.adding.nl_NL.xml. Deze XML-scripts moeten op twee locaties aan het bestand adobe-appmondata.jar worden toegevoegd, zoals hieronder wordt aangegeven:

* adobe-livecycle-native-jreliëf-x86_win32.ear > adobe-Native2PDFSvc.war\WEB-INF\lib > adobe-native.jar > Native2PDFSvc-native.jar\bin > adobe-appmondata.jar\com\adobe\appmon. Het bestand adobe-livecycle-native-jreliëf-x86_win32.ear bevindt zich in de exportmap op `[AEM forms install directory]\configurationManager`. (Als AEM Forms wordt geïmplementeerd op een andere J2EE-toepassingsserver, vervangt u het bestand adobe-livecycle-native-jreliëf-x86_win32.ear door het EAR-bestand dat overeenkomt met uw J2EE-toepassingsserver.)
* adobe-generatepdf-dsc.jar > adobe-appmondata.jar\com\adobe\appmon (het bestand adobe-appmondata.jar bevindt zich in het bestand adobe-generatepdf-dsc.jar). Het bestand adobe-generatepdf-dsc.jar bevindt zich in de `[AEM forms install directory]\deploy` map.

Nadat u deze XML-bestanden aan het bestand adobe-appmondata.jar hebt toegevoegd, moet u de component GeneratePDF opnieuw gebruiken. Voer de volgende taken uit om XML-bestanden voor dialoog en script toe te voegen aan het bestand adobe-appmondata.jar:

1. Open met een hulpprogramma zoals WinZip of WinRAR het bestand adobe-livecycle-native-jreliëf-x86_win32.earfile > adobe-Native2PDFSvc.war\WEB-INF\lib > adobe-native.jar > Native2PDFSvc-native.jar\bin > adobe-appmondata.jar.
1. Voeg het dialoogvenster- en scriptbestand XML toe aan het bestand appmondata.jar of wijzig bestaande XML-bestanden in dit bestand. (Zie Een script-XML-bestand [maken of wijzigen voor een native](converting-file-formats-pdf.md#creating-or-modifying-a-script-xml-file-for-a-native-application)toepassing en een extra dialoogvenster-XML-bestand [maken of wijzigen voor een native toepassing](converting-file-formats-pdf.md#creating-or-modifying-an-additional-dialog-xml-file-for-a-native-application).)
1. Open adobe-generatepdf-dsc.jar > adobe-appmondata.jar met een hulpprogramma zoals WinZip of WinRAR.
1. Voeg het dialoogvenster- en scriptbestand XML toe aan het bestand appmondata.jar of wijzig bestaande XML-bestanden in dit bestand. (Zie Een script-XML-bestand [maken of wijzigen voor een native](converting-file-formats-pdf.md#creating-or-modifying-a-script-xml-file-for-a-native-application)toepassing en een extra dialoogvenster-XML-bestand [maken of wijzigen voor een native toepassing](converting-file-formats-pdf.md#creating-or-modifying-an-additional-dialog-xml-file-for-a-native-application).) Nadat u de XML-bestanden aan het bestand adobe-appmondata.jar hebt toegevoegd, plaatst u het nieuwe bestand adobe-appmondata.jar in het bestand adobe-generatepdf-dsc.jar.
1. Als u ondersteuning hebt toegevoegd voor een extra eigen bestandsindeling, maakt u een systeemomgevingsvariabele die het pad van de toepassing aangeeft (zie Een omgevingsvariabele [maken om de oorspronkelijke toepassing](converting-file-formats-pdf.md#creating-an-environment-variable-to-locate-the-native-application)te vinden).

**De component GeneratePDF opnieuw implementeren**

1. Meld u aan bij Workbench.
1. Selecteer **Venster** > Weergaven **tonen** > **Componenten**. Met deze actie voegt u de weergave Componenten toe aan Workbench.
1. Klik met de rechtermuisknop op de component GeneratePDF en selecteer vervolgens **Component** stoppen.
1. Wanneer de component is gestopt, klikt u met de rechtermuisknop en selecteert u Component verwijderen om deze te verwijderen.
1. Klik met de rechtermuisknop op het pictogram **Componenten** en selecteer Component **** installeren.
1. Blader naar het gewijzigde bestand adobe-generatepdf-dsc.jar, selecteer dit bestand en klik op Openen. Naast de component GeneratePDF wordt een rood vierkantje weergegeven.
1. Breid de component GeneratePDF uit, selecteer de beschrijvers van de Dienst, en klik dan GeneratePDFService met de rechtermuisknop aan en selecteer de Dienst activeren.
1. Voer in het dialoogvenster voor configuratie dat wordt weergegeven de toepasselijke configuratiewaarden in. Als u deze waarden leeg laat, worden standaardconfiguratiewaarden gebruikt.
1. Klik met de rechtermuisknop op GeneratePDF en selecteer Component starten.
1. Breid Actieve Diensten uit. Er verschijnt een groene pijl naast de servicenaam als deze wordt uitgevoerd. Anders, is de dienst in een tegengehouden staat.
1. Als de dienst in een tegengehouden staat is, klik de de dienstnaam met de rechtermuisknop aan en selecteer de Dienst van het Begin.

### Een XML-scriptbestand voor een native toepassing maken of wijzigen {#creating-or-modifying-a-script-xml-file-for-a-native-application}

Als u bestanden wilt doorsturen naar een nieuwe oorspronkelijke toepassing, moet u een XML-scriptbestand voor die toepassing maken. Als u de manier wilt wijzigen waarop de service PDF genereren werkt met een native toepassing die al wordt ondersteund, moet u het script voor die toepassing wijzigen.

Het script bevat instructies die door de vensterelementen van de native toepassing navigeren en die specifieke reacties op die elementen leveren. Het bestand dat deze informatie bevat, is `appmon.`[toepassingsnaam]&quot; `.script.`[landinstelling]`.xml`. Een voorbeeld is appmon.notepad.script.en_US.xml.

#### Stappen identificeren die het script moet uitvoeren {#identifying-steps-the-script-must-execute}

Bepaal in de native toepassing door welke vensterelementen u moet navigeren en welke reacties u moet uitvoeren om het document af te drukken. Let op de dialoogvensters die het resultaat zijn van reacties. De stappen zijn vergelijkbaar met de volgende stappen:

1. Selecteer Bestand > Openen
1. Geef het pad op en klik op Openen.
1. Selecteer Bestand > Afdrukken op de menubalk.
1. Geef de vereiste eigenschappen voor de printer op.
1. Selecteer Afdrukken en wacht tot het dialoogvenster Opslaan als wordt weergegeven. De service PDF genereren heeft het dialoogvenster Opslaan als nodig om de bestemming voor het PDF-bestand op te geven.

#### Dialoogvensters identificeren die zijn opgegeven in bijschriftkenmerken {#identifying-the-dialogs-specified-in-caption-attributes}

Gebruik Microsoft Spy++ om de identiteiten van de eigenschappen van het vensterelement in de inheemse toepassing te verkrijgen. U moet over deze identiteiten beschikken om scripts te schrijven.

#### Reguliere expressies gebruiken in bijschriftkenmerken {#using-regular-expressions-in-caption-attributes}

U kunt reguliere expressies gebruiken in bijschriftspecificaties. De service PDF genereren gebruikt de `java.util.regex.Matcher` klasse om reguliere expressies te ondersteunen. Dit hulpprogramma ondersteunt de reguliere expressies die worden beschreven in `java.util.regex.Pattern`. (Ga naar de website van Java op [https://java.sun.com/j2se/1.4.2/docs/api/java/util/regex/Pattern.html](https://java.sun.com/j2se/1.4.2/docs/api/java/util/regex/Pattern.html).)

**Reguliere expressie die de bestandsnaam bevat die aan Kladblok is toegevoegd in de banner Kladblok**

```as3
 <!-- The regular expression ".*Notepad" means any number of non-terminating characters followed by Notepad. -->
 <step>
     <expectedWindow>
         <window caption=".*Notepad"/>
     </expectedWindow>
 </step>
```

**Reguliere expressie die een onderscheid maakt tussen Afdrukken en Afdrukinstellingen**

```as3
 <!-- This regular expression differentiates the Print dialog box from the Print Setup dialog box. The "^" specifies the beginning of the line, and the "$" specifies the end of the line. -->
 <windowList>
     <window controlID="0x01" caption="^Print$" action="press"/>
 </windowList>
```

#### De elementen window en windowList ordenen {#ordering-the-window-and-windowlist-elements}

U dient de volgende elementen te ordenen `window` en `windowList` te bepalen:

* Wanneer meerdere `window` elementen als onderliggende elementen in een `windowList` of `dialog` element worden weergegeven, ordent u die `window` elementen in aflopende volgorde, waarbij de lengte van de `caption` namen de positie in de volgorde aangeeft.
* Wanneer meerdere `windowList` elementen in een `window` element voorkomen, moet u die `windowList` elementen in aflopende volgorde ordenen, waarbij de lengte van de `caption` kenmerken van het eerste `indexes/`element de positie in de volgorde aangeeft.

**Vensterelementen in een dialoogvenster ordenen**

```as3
 <!-- The caption attribute in the following window element is 40 characters long. It is the longest caption in this example, so its parent window element appears before the others. -->
 <window caption="Unexpected Failure in DebugActiveProcess">
     <…>
 </window>

 <!-- Caption length is 33 characters. -->
 <window caption="Adobe Acrobat - License Agreement">
     <…>
 </window>

 <!-- Caption length is 33 characters. -->
 <window caption="Microsoft Visual.*Runtime Library">
     <…>
 </window>

 <!-- The caption attribute in the following window element is 28 characters long. It is the shortest caption in this example, so its parent window element appears after the others. -->
 <window caption="Adobe Acrobat - Registration">
     <…>
 </window>
```

**Vensterelementen binnen een windowList-element ordenen**

```as3
 <!-- The caption attribute in the following indexes element is 56 characters long. It is the longest caption in this example, so its parent window element appears before the others. -->
 <windowList>
     <window caption="Can&apos;t exit design mode because.* cannot be created"/>
     <window className="Button" caption="OK" action="press"/>
 </windowList>
 <windowList>
     <window caption="Do you want to continue loading the project?"/>
     <window className="Button" caption="No" action="press"/>
 </windowList>
 <windowList>
     <window caption="The macros in this project are disabled"/>
     <window className="Button" caption="OK" action="press"/>
 </windowList>
```

### Een XML-bestand voor een extra dialoogvenster maken of wijzigen voor een native toepassing {#creating-or-modifying-an-additional-dialog-xml-file-for-a-native-application}

Als u een script maakt voor een native toepassing die voorheen niet werd ondersteund, moet u ook een extra XML-bestand voor het dialoogvenster voor die toepassing maken. Elke native toepassing die door AppMon wordt gebruikt, mag slechts één extra XML-bestand voor het dialoogvenster hebben. Het XML-bestand van het extra dialoogvenster is vereist, zelfs als er geen ongewenste dialoogvensters worden verwacht. Het aanvullende dialoogvenster moet ten minste één `window` element bevatten, zelfs als dat `window` element slechts een tijdelijke aanduiding is.

>[!NOTE]
>
>In dit verband betekent de term &quot;aanvullend&quot; de inhoud van het bestand `appmon.[applicationname].addition.[locale]`.xml. Met een dergelijk bestand worden overschrijvingen en toevoegingen aan het XML-bestand van het dialoogvenster opgegeven.

U kunt ook het XML-bestand met aanvullende dialoogvensters wijzigen voor een native toepassing voor de volgende doeleinden:

* Het XML-bestand van het dialoogvenster negeren voor een toepassing met een andere reactie
* Een antwoord toevoegen aan een dialoogvenster dat niet wordt geactiveerd in het XML-bestand van het dialoogvenster voor die toepassing

De bestandsnaam die een extra dialogXML-bestand aangeeft, is `appmon.[appname].addition.[locale].xml`. Een voorbeeld is appmon.excel.extension.nl_NL.xml.

De naam van het XML-bestand van het extra dialoogvenster moet de indeling gebruiken `appmon.[applicationname].addition.[locale].xml`, waarbij de *toepassingsnaam* exact moet overeenkomen met de toepassingsnaam die in het XML-configuratiebestand en in het script wordt gebruikt.

>[!NOTE]
>
>Geen van de generische toepassingen die in het configuratiebestand native2pdfconfig.xml zijn opgegeven, hebben een primair XML-bestand voor de dialoog. In de sectie Ondersteuning voor een eigen bestandsindeling [toevoegen of wijzigen](converting-file-formats-pdf.md#adding-or-modifying-support-for-a-native-file-format) worden dergelijke specificaties beschreven.

U moet `windowList` elementen ordenen die als onderliggende elementen in een `window` element worden weergegeven. (Zie [De elementen](converting-file-formats-pdf.md#ordering-the-window-and-windowlist-elements)window en windowList ordenen.)

### Het algemene dialoogvenster-XML-bestand wijzigen {#modifying-the-general-dialog-xml-file}

U kunt het algemene dialoogvenster-XML-bestand aanpassen om te reageren op dialoogvensters die door het systeem worden gegenereerd of om te reageren op dialoogvensters die door meerdere toepassingen worden gebruikt.

#### Een filetype-item toevoegen in het XML-configuratiebestand {#adding-a-filetype-entry-in-the-xml-configuration-file}

In deze procedure wordt uitgelegd hoe u het configuratiebestand van de service PDF genereren kunt bijwerken en zo bestandstypen aan native toepassingen kunt koppelen. Om dit configuratiedossier bij te werken, moet u beleidsconsole gebruiken om de configuratiegegevens naar een dossier uit te voeren. De standaardbestandsnaam voor de configuratiegegevens is native2pdfconfig.xml.

**Het configuratiebestand van de PDF-service genereren bijwerken**

1. Selecteer **Home** > **Services** > **Adobe PDF Generator** > **Configuration Files**, en selecteer vervolgens **Export Configuration**.
1. Wijzig zo nodig het `filetype-settings` element in het bestand native2pdfconfig.xml.
1. Selecteer **Home** > **Services** > **Adobe PDF Generator** >**Configuration Files** en selecteer vervolgens **Import Configuration**. De configuratiegegevens worden geïmporteerd in de service PDF genereren en vervangen de vorige instellingen.

>[!NOTE]
>
>De naam van de toepassing wordt opgegeven als de waarde van het `GenericApp` attribuut van het `name` element. Deze waarde moet exact overeenkomen met de corresponderende naam die is opgegeven in het script dat u voor die toepassing ontwikkelt. Op dezelfde manier moet het `GenericApp` kenmerk van het `displayName` element exact overeenkomen met het bijschrift van het corresponderende `expectedWindow` venster van het script. Deze gelijkwaardigheid wordt geëvalueerd nadat eventuele reguliere expressies in de `displayName` kenmerken of `caption` kenmerken zijn omgezet.

In dit voorbeeld zijn de standaardconfiguratiegegevens van de Generate PDF-service gewijzigd om op te geven dat Kladblok (niet Microsoft Word) moet worden gebruikt voor het verwerken van bestanden met de bestandsextensie .txt. Vóór deze wijziging is Microsoft Word opgegeven als de oorspronkelijke toepassing die dergelijke bestanden moet verwerken.

**Wijzigingen voor het sturen van tekstbestanden naar Kladblok (native2pdfconfig.xml)**

```as3
 <filetype-settings>

 <!-- Some native app file types were omitted for brevity. -->
 <!-- The following GenericApp element specifies Notepad as the native application that should be used to process files that have a txt file name extension. -->
             <GenericApp
                 extensions="txt"
                 name="Notepad" displayName=".*Notepad"/>
             <GenericApp
                 extensions="wpd"
                 name="WordPerfect" displayName="Corel WordPerfect"/>
             <GenericApp extensions="pmd,pm6,p65,pm"
                 name="PageMaker" displayName="Adobe PageMaker"/>
             <GenericApp extensions="fm"
                 name="FrameMaker" displayName="Adobe FrameMaker"/>
             <GenericApp extensions="psd"
                 name="Photoshop" displayName="Adobe Photoshop"/>
         </settings>
     </filetype-settings>
```

#### Een omgevingsvariabele maken om de oorspronkelijke toepassing te vinden {#creating-an-environment-variable-to-locate-the-native-application}

Maak een omgevingsvariabele die de locatie opgeeft van het uitvoerbare bestand van de native toepassing. De variabele moet de indeling gebruiken `[applicationname]_PATH`, waarbij de *toepassingsnaam* exact moet overeenkomen met de toepassingsnaam in het XML-configuratiebestand en in het script, en waarbij het pad het pad naar het uitvoerbare bestand bevat met dubbele aanhalingstekens. Een voorbeeld van een dergelijke omgevingsvariabele is `Photoshop_PATH`.

Nadat u de nieuwe omgevingsvariabele hebt gemaakt, moet u de server opnieuw opstarten waarop de Genereren PDF-service is geïmplementeerd.

**Een systeemvariabele maken in de Windows XP-omgeving**

1. Selecteer **Configuratiescherm > Systeem**.
1. Klik in het dialoogvenster Systeemeigenschappen op het tabblad **Geavanceerd** en klik vervolgens op **Omgevingsvariabelen**.
1. Klik onder Systeemvariabelen in het dialoogvenster Omgevingsvariabelen op **Nieuw**.
1. Typ in het dialoogvenster Nieuwe systeemvariabele in het vak Naam **** variabele een naam die de indeling gebruikt `[applicationname]_PATH`.
1. Typ in het vak **Waarde** variabele het volledige pad en de bestandsnaam van het uitvoerbare bestand van de toepassing en klik op **OK**. For example, type: `c:\windows\Notepad.exe`
1. Klik in het dialoogvenster Omgevingsvariabelen op **OK**.

**Een systeemvariabele maken via de opdrachtregel**

1. Typ in een opdrachtregelvenster de definitie van de variabele met deze notatie:

   ```as3
            [applicationname]_PATH=[Full path name]
   ```

   For example, type: `NotePad_PATH=C:\WINDOWS\NOTEPAD.EXE`

1. Begin een nieuwe herinnering van de bevellijn voor de systeemvariabele om van kracht te worden.

#### XML-bestanden {#xml-files}

AEM Forms bevat voorbeeld-XML-bestanden die ervoor zorgen dat de Generate PDF-service Kladblok gebruikt om bestanden met de bestandsnaamextensie .txt te verwerken. Deze code is opgenomen in deze sectie. Daarnaast moet u de andere wijzigingen aanbrengen die in deze sectie worden beschreven.

#### XML-bestand van extra dialoogvenster {#additional-dialog-xml-file}

Dit voorbeeld bevat de extra dialoogdozen voor de toepassing van de Blocnote. Deze dialoogvensters kunnen een aanvulling zijn op de dialoogvensters die zijn opgegeven in de service PDF genereren.

**Kladblok dialoogvensters (appmon.notepad.adding.nl_NL.xml)**

```as3
 <dialogs app="Notepad" locale="en_US" version="7.0" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="dialogs.xsd">
     <window caption="Caption Title">
         <windowList>
             <window className="Button" caption="OK" action="press"/>
         </windowList>
     </window>
 </dialogs>
```

#### Script XML-bestand {#script-xml-file}

In dit voorbeeld wordt aangegeven hoe de service PDF genereren moet werken met Kladblok om bestanden af te drukken met de Adobe PDF-printer.

**XML-bestand met toetsenblok (appmon.notepad.script.nl_NL.xml)**

```as3
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<!--
*
* ADOBE CONFIDENTIAL
* ___________________
* Copyright 2004 - 2005 Adobe Systems Incorporated
* All Rights Reserved.
*
* NOTICE:  All information contained herein is, and remains
* the property of Adobe Systems Incorporated and its suppliers,
* if any.  The intellectual and technical concepts contained
* herein are proprietary to Adobe Systems Incorporated and its
* suppliers and may be covered by U.S. and Foreign Patents,
* patents in process, and are protected by trade secret or copyright law.
* Dissemination of this information or reproduction of this material
* is strictly forbidden unless prior written permission is obtained
* from Adobe Systems Incorporated.
*-->

<!-- This file automates printing of text files via notepad to Adobe PDF printer. In order to see the complete hierarchy we recommend using the Microsoft Spy++ which details the properties of windows necessary to write scripts. In this sample there are total of eight steps-->

<application name="Notepad" version="9.0" locale="en_US" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="scripts.xsd">

    <!-- In this step we wait for the application window to appear -->
    <step>
        <expectedWindow>
            <window caption=".*Notepad"/>
        </expectedWindow>
    </step>

    <!-- In this step, we acquire the application window and send File->Open menu bar, menu item commands and the expectation is the windows Open dialog-->
    <step>
        <acquiredWindow>
            <window caption=".*Notepad">
                <virtualInput>
                    <menuBar>
                        <selection>
                            <name>File</name>
                        </selection>
                        <selection>
                            <name>Open...</name>
                        </selection>
                    </menuBar>
                </virtualInput>
            </window>
        </acquiredWindow>
        <expectedWindow>
            <window caption="Open"/>
        </expectedWindow>
    </step>

    <!-- In this step, we acquire the Open window and then select the 'Edit' widget and input the source path followed by clicking on the 'Open' button . The expectation of this 'action' is that the Open dialog will disappear -->
    <step>
        <acquiredWindow>
            <window caption="Open">
                <windowList>
                    <window className="ComboBoxEx32">
                        <windowList>
                            <window className="ComboBox">
                                <windowList>
                                <window className="Edit" action="inputSourcePath"/>
                                </windowList>
                            </window>
                        </windowList>
                    </window>
                </windowList>
                <windowList>
                    <window className="Button" caption="Open" action="press"/>
                </windowList>
            </window>
        </acquiredWindow>
        <expectedWindow>
            <window caption="Open" action="disappear"/>
        </expectedWindow>
        <pause value="30"/>
    </step>

    <!-- In this step, we acquire the application window and send File->Print menu bar, menu item commands and the expectation is the windows Print dialog-->
    <step>
        <acquiredWindow>
            <window caption=".*Notepad">
                <virtualInput>
                    <menuBar>
                        <selection>
                            <name>File</name>
                        </selection>
                        <selection>
                            <name>Print...</name>
                        </selection>
                    </menuBar>
                </virtualInput>
            </window>
        </acquiredWindow>
        <expectedWindow>
            <window caption="Print">
        </window>
        </expectedWindow>
    </step>

    <!-- In this step, we acquire the Print dialog and click on the 'Preferences' button and the expected window in this case is the dialog with the caption '"Printing Preferences' -->
    <step>
        <acquiredWindow>
            <window caption="Print">
                <windowList>
                    <window caption="General">
                        <windowList>
                            <window className="Button" caption="Preferences" action="press"/>
                        </windowList>
                    </window>
                </windowList>
            </window>
        </acquiredWindow>
        <expectedWindow>
            <window caption="Printing Preferences"/>
        </expectedWindow>
    </step>

    <!-- In this step, we acquire the dialog "Printing Preferences' and select the combo box which is the 10th child of window with caption '"Adobe PDF Settings' and select the first index. (Note: All indeces start with 0.) Besides this we uncheck the box which  has the caption '"View Adobe PDF results' and we click on the button OK. The expectation is that 'Printing Preferences' dialog disappears. -->
    <step>
        <acquiredWindow>
            <window caption="Printing Preferences">
                <windowList>
                    <window caption="Adobe PDF Settings">
                        <windowList>
                            <window className="Button" caption="View Adobe PDF results" action="uncheck"/>
                        </windowList>
                        <windowList>
                            <window className="Button" caption="Ask to Replace existing PDF file" action="uncheck"/>
                        </windowList>
                    </window>
                </windowList>
                <windowList>
                    <window className="Button" caption="OK" action="press"/>
                </windowList>
            </window>
        </acquiredWindow>
        <expectedWindow>
            <window caption="Printing Preferences" action="disappear"/>
        </expectedWindow>
    </step>

    <!-- In this step, we acquire the 'Print' dialog and click on the Print button. The expectation is that the dialog with caption 'Print' disappears. In this case we use the regular expression '^Print$' for specifying the caption given there could be multiple dialogs with caption that includes the word Print. -->
    <step>
        <acquiredWindow>
            <window caption="Print">
                <windowList>
                    <window caption="General"/>
                    <window className="Button" caption="^Print$" action="press"/>
                </windowList>
            </window>
        </acquiredWindow>
        <expectedWindow>
            <window caption="Print" action="disappear"/>
        </expectedWindow>
    </step>
    <step>
        <expectedWindow>
            <window caption="Save PDF File As"/>
        </expectedWindow>
    </step>
    <!-- Finally in this step, we acquire the dialog with caption "Save PDF File As" and in the Edit widget type the destination path for the output PDF file and click on the Save button. The expectation is that the dialog disappears-->
    <step>
        <acquiredWindow>
            <window caption="Save PDF File As">
                <windowList>
                    <window className="Edit" action="inputDestinationPath"/>
                </windowList>
                <windowList>
                    <window className="Button" caption="Save" action="press"/>
                </windowList>
            </window>
        </acquiredWindow>
        <expectedWindow>
            <window caption="Save PDF File As" action="disappear"/>
        </expectedWindow>
    </step>

    <!-- We can always set a retry count or a maximum time for a step. In case we surpass these limitations, PDF Generator generates this abort message and terminates processing. -->
    <abortMessage msg="15078"/>
</application>
```

