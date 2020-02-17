---
title: Werken met PDF-hulpprogramma's
seo-title: Werken met PDF-hulpprogramma's
description: 'null'
seo-description: 'null'
uuid: a2ea2359-c547-4f1b-b6ca-f276f816e36a
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: d816bf2e-5236-4084-b7c4-c32b72cdff97
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Werken met PDF-hulpprogramma&#39;s {#working-with-pdf-utilities}

**Informatie over de PDF-hulpprogramma&#39;s**

De service PDF-hulpprogramma&#39;s kan converteren tussen PDF- en XDP-bestandsindelingen, PDF-documenteigenschappen instellen en ophalen en XMP-metagegevens bewerken. Voordat u bijvoorbeeld een PDF-document naar een andere indeling converteert, is het handig om de eigenschappen te controleren om te bepalen welke servicebewerking moet worden aangeroepen voor de conversie.

U kunt deze taken uitvoeren met de service PDF-hulpprogramma&#39;s:

* Converteer PDF-documenten naar XDP-documenten.
* XDP-documenten converteren naar PDF-documenten. (Zie XDP-documenten [converteren naar PDF-documenten](pdf-utilities.md#converting-xdp-documents-into-pdf-documents).)
* Eigenschappen PDF-document ophalen. (Zie Eigenschappen [PDF-document](pdf-utilities.md#retrieving-pdf-document-properties)ophalen.)
* Sla een PDF-document op en optimaliseer het voor snelle webweergave. (Zie [Opslagmodi](pdf-utilities.md#setting-pdf-document-save-modes)voor PDF-documenten instellen.)

>[!NOTE]
>
>Zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63)voor meer informatie over de service PDF-hulpprogramma&#39;s.

## PDF-documenten converteren naar XDP-documenten {#converting-pdf-documents-into-xdp-documents}

Met de PDF-hulpprogramma&#39;s Java en API&#39;s voor webservices kunt u PDF-documenten programmatisch converteren naar XDP-documenten.

>[!NOTE]
>
>Zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63)voor meer informatie over de service PDF-hulpprogramma&#39;s.

### Overzicht van de stappen {#summary-of-steps}

Voer de volgende stappen uit om een PDF-document te converteren naar een XDP-document:

1. Inclusief projectbestanden.
1. Maak een PDFUtilityService-client.
1. Roep de conversiebewerking PDF naar XDP aan.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**Een PDFUtilityService-client maken**

Voordat u een bewerking met PDF-hulpprogramma&#39;s programmatisch kunt uitvoeren, moet u een PDFUtilityService-client maken. Met de Java API wordt dit bereikt door een `PDFUtilityServiceClient` object te maken. Met de webservice-API wordt dit bereikt door een `PDFUtilityServiceService` object te gebruiken.

**De conversiebewerking PDF naar XDP aanroepen**

Nadat u de serviceclient hebt gemaakt, kunt u de conversiebewerking PDF naar XDP uitvoeren.

**Zie ook**

[PDF-documenten converteren naar XDP-documenten met de Java API](pdf-utilities.md#convert-pdf-documents-into-xdp-documents-using-the-java-api)

[PDF-documenten converteren naar XDP-documenten met de webservice-API](pdf-utilities.md#convert-pdf-documents-into-xdp-documents-using-the-web-service-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### PDF-documenten converteren naar XDP-documenten met de Java API {#convert-pdf-documents-into-xdp-documents-using-the-java-api}

PDF-documenten converteren naar XDP-documenten met de API voor PDF-hulpprogramma&#39;s (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-pdfutility-client.jar, op in het klassenpad van uw Java-project.

1. Een PDFUtilityService-client maken

   Maak een `PDFUtilityServiceClient` object door de constructor ervan te gebruiken en een `ServiceClientFactory` object door te geven dat verbindingseigenschappen bevat.

1. De conversiebewerking PDF naar XDP aanroepen

   Als u de conversie wilt uitvoeren, roept u de `PDFUtilityServiceClient` methode van het object aan en geeft u een `convertPDFtoXDP` `com.adobe.idp.Document` object door dat het PDF-bestand vertegenwoordigt. De methode retourneert een `com.adobe.idp.Document` object dat het nieuwe XDP-bestand vertegenwoordigt.

**Zie ook**

[PDF-documenten converteren naar XDP-documenten](pdf-utilities.md#converting-pdf-documents-into-xdp-documents)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### PDF-documenten converteren naar XDP-documenten met de webservice-API {#convert-pdf-documents-into-xdp-documents-using-the-web-service-api}

Converteer PDF-documenten naar XDP-documenten met de PDF Utilities API (webservice):

1. Projectbestanden opnemen

   * Creeer een de cliëntassemblage van Microsoft .NET die het dossier van WSDL van de dienst van het Nut PDF gebruikt.
   * Verwijs naar de cliëntassemblage van Microsoft .NET.

1. Een PDFUtilityService-client maken

   Maak een `PDFUtilityServiceService` object met de constructor van de proxyklasse.

1. De conversiebewerking PDF naar XDP aanroepen

   Roep de `PDFUtilityServiceService` methode van het `convertPDFtoXDP` object aan en geef een `BLOB` object dat het PDF-bestand vertegenwoordigt door. De methode retourneert een `BLOB` object dat het nieuwe XDP-bestand vertegenwoordigt.

**Zie ook**

[PDF-documenten converteren naar XDP-documenten](pdf-utilities.md#converting-pdf-documents-into-xdp-documents)

[AEM-formulieren aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Creërend een .NET cliëntassemblage die het coderen Base64 gebruikt](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## XDP-documenten converteren naar PDF-documenten {#converting-xdp-documents-into-pdf-documents}

Met de PDF Utilities Java en de webservice-API&#39;s kunt u XDP-documenten programmatisch converteren naar PDF-documenten.

>[!NOTE]
>
>Zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63)voor meer informatie over de service PDF-hulpprogramma&#39;s.

### Overzicht van de stappen {#summary_of_steps-1}

Voer de volgende stappen uit om een XDP-document te converteren naar een PDF-document:

1. Inclusief projectbestanden.
1. Maak een PDFUtilityService-client.
1. Roep de conversiebewerking XDP naar PDF aan.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**Een PDFUtilityService-client maken**

Voordat u een bewerking met PDF-hulpprogramma&#39;s programmatisch kunt uitvoeren, moet u een PDFUtilityService-client maken. Met de Java API wordt dit bereikt door een `PDFUtilityServiceClient` object te maken. Met de webservice-API wordt dit bereikt door een `PDFUtilityServiceService` object te gebruiken.

**De conversiebewerking XDP naar PDF aanroepen**

Nadat u de serviceclient hebt gemaakt, kunt u de conversiebewerking XDP naar PDF uitvoeren.

**Zie ook**

[XDP-documenten converteren naar PDF-documenten met de Java API](pdf-utilities.md#convert-xdp-documents-into-pdf-documents-using-the-java-api)

[XDP-documenten converteren naar PDF-documenten met de webservice-API](pdf-utilities.md#converting-xdp-documents-into-pdf-documents-using-the-web-service-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### XDP-documenten converteren naar PDF-documenten met de Java API {#convert-xdp-documents-into-pdf-documents-using-the-java-api}

XDP-documenten converteren naar PDF-documenten met de PDF Utilities API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-pdfutility-client.jar, op in het klassenpad van uw Java-project.

1. Een PDFUtilityService-client maken

   Maak een `PDFUtilityServiceClient` object door de constructor ervan te gebruiken en een `ServiceClientFactory` object door te geven dat verbindingseigenschappen bevat.

1. De conversiebewerking XDP naar PDF aanroepen

   Als u de conversie wilt uitvoeren, roept u de `PDFUtilityServiceClient` methode van het object aan en geeft u een `convertXDPtoPDF` `com.adobe.idp.Document` object door dat het XDP-bestand vertegenwoordigt. De methode retourneert een `com.adobe.idp.Document` object dat het nieuwe PDF-bestand vertegenwoordigt.

**Zie ook**

[XDP-documenten converteren naar PDF-documenten](pdf-utilities.md#converting-xdp-documents-into-pdf-documents)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### XDP-documenten converteren naar PDF-documenten met de webservice-API {#converting-xdp-documents-into-pdf-documents-using-the-web-service-api}

XDP-documenten converteren naar PDF-documenten met behulp van de PDF Utilities API (webservice-API):

1. Projectbestanden opnemen

   * Creeer een de cliëntassemblage van Microsoft .NET die het dossier van WSDL van de dienst van het Nut PDF gebruikt.
   * Verwijs naar de cliëntassemblage van Microsoft .NET.

1. Een PDFUtilityService-client maken

   Maak een `PDFUtilityServiceService` object met de constructor van de proxyklasse.

1. De conversiebewerking XDP naar PDF aanroepen

   Als u de conversie wilt uitvoeren, roept u de `PDFUtilityServiceService` methode van het object aan en geeft u een `convertXDPtoPDF` `BLOB` object door dat het XDP-bestand vertegenwoordigt. De methode retourneert een `BLOB` object dat het nieuwe PDF-bestand vertegenwoordigt.

**Zie ook**

[XDP-documenten converteren naar PDF-documenten](pdf-utilities.md#converting-xdp-documents-into-pdf-documents)

[AEM-formulieren aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Creërend een .NET cliëntassemblage die het coderen Base64 gebruikt](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## Eigenschappen PDF-document ophalen {#retrieving-pdf-document-properties}

Met de PDF-hulpprogramma&#39;s Java en API&#39;s voor webservices kunt u PDF-documenteigenschappen programmatisch ophalen, bijvoorbeeld of het document een invulbaar formulier is of de minimale Acrobat-versie die is vereist om het document te lezen.

>[!NOTE]
>
>Zie [Services Reference for AEM Forms voor meer informatie over de service PDF-hulpprogramma&#39;s](https://www.adobe.com/go/learn_aemforms_services_63)

### Overzicht van de stappen {#summary_of_steps-2}

Voer de volgende stappen uit om PDF-documenteigenschappen op te halen:

1. Inclusief projectbestanden.
1. Maak een PDFUtilityService-client.
1. Roep de ophaalbewerking voor eigenschappen aan.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**Een PDFUtilityService-client maken**

Voordat u een bewerking met PDF-hulpprogramma&#39;s programmatisch kunt uitvoeren, moet u een PDFUtilityService-client maken. Met de Java API wordt dit bereikt door een `PDFUtilityServiceClient` object te maken. Met de webservice-API wordt dit gedaan met behulp van een `PDFUtilityServiceService` object.

**Ophaalbewerking voor eigenschappen aanroepen**

Nadat u de de dienstcliënt creeert, kunt u de eigenschappen terugwinningsverrichting aanhalen.

**Zie ook**

[Eigenschappen van PDF-documenten ophalen met de Java API](pdf-utilities.md#retrieve-pdf-document-properties-using-the-java-api)

[Eigenschappen van PDF-documenten ophalen met de webservice-API](pdf-utilities.md#retrieve-pdf-document-properties-using-the-web-service-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Eigenschappen van PDF-documenten ophalen met de Java API {#retrieve-pdf-document-properties-using-the-java-api}

U kunt de eigenschappen van PDF-documenten ophalen met de API voor PDF-hulpprogramma&#39;s (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-pdfutility-client.jar, op in het klassenpad van uw Java-project.

1. Een PDFUtilityService-client maken

   Maak een `PDFUtilityServiceClient` object door de constructor ervan te gebruiken en een `ServiceClientFactory` object door te geven dat verbindingseigenschappen bevat.

1. Ophaalbewerking voor eigenschappen aanroepen

   Als u de conversie wilt uitvoeren, roept u de methode van het `PDFUtilityServiceClient` object aan en geeft u de volgende `getPDFProperties` methode door:

   * Een `com.adobe.idp.Document` object dat staat voor het PDF-document.
   * Een `PDFPropertiesOptionSpec` object dat de eigenschappen bevat die moeten worden geëvalueerd.
   De methode retourneert een `PDFPropertiesResult` object dat de resultaten van de query bevat.

**Zie ook**

[Eigenschappen PDF-document ophalen](pdf-utilities.md#retrieving-pdf-document-properties)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Eigenschappen van PDF-documenten ophalen met de webservice-API {#retrieve-pdf-document-properties-using-the-web-service-api}

U kunt de eigenschappen van PDF-documenten ophalen met de API voor de PDF-hulpprogramma&#39;s:

1. Projectbestanden opnemen

   * Creeer een de cliëntassemblage van Microsoft .NET die het dossier van WSDL van de dienst van het Nut PDF gebruikt.
   * Verwijs naar de cliëntassemblage van Microsoft .NET.

1. Een PDFUtilityService-client maken

   Maak een `PDFUtilityServiceService` object met de constructor van de proxyklasse.

1. Ophaalbewerking voor eigenschappen aanroepen

   Als u de conversie wilt uitvoeren, roept u de methode van het `PDFUtilityServiceService` object aan en geeft u de volgende `getPDFProperties` methode door:

   * Een `BLOB` object dat staat voor het PDF-document.
   * Een `PDFPropertiesOptionSpec` object dat de eigenschappen bevat die moeten worden geëvalueerd.
   De methode retourneert een `PDFPropertiesResult` object dat de resultaten van de query bevat.

**Zie ook**

[Eigenschappen PDF-document ophalen](pdf-utilities.md#retrieving-pdf-document-properties)

[AEM-formulieren aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Creërend een .NET cliëntassemblage die het coderen Base64 gebruikt](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## Modus PDF-document opslaan instellen {#setting-pdf-document-save-modes}

Met de Java- en webservice-API&#39;s van de PDF-hulpprogramma&#39;s kunt u een opslagmodus voor een PDF-document programmatisch instellen. Als u een opslagmodus instelt met de service PDF-hulpprogramma&#39;s, stelt de service PDF-hulpprogramma&#39;s alleen de opslagmodus in en wordt het PDF-document niet daadwerkelijk opgeslagen. Het PDF-document wordt opgeslagen wanneer het wordt doorgegeven aan een andere servicebewerking. U kunt bijvoorbeeld de service PDF-hulpprogramma&#39;s gebruiken om een specifieke opslagmodus in te stellen en deze door te geven aan de coderingsservice, waarbij het PDF-document daadwerkelijk wordt opgeslagen en versleuteld.

>[!NOTE]
>
>Zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63)voor meer informatie over de service PDF-hulpprogramma&#39;s.

### Overzicht van de stappen {#summary_of_steps-3}

Voer de volgende stappen uit om de opslagoptie voor PDF-documenten in te stellen:

1. Inclusief projectbestanden.
1. Maak een PDFUtilityService-client.
1. Stel de opslagmodus in.
1. Roep de opslagbewerking aan.
1. Geef het PDF-document door aan een andere bewerking.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**Een PDFUtilityService-client maken**

Voordat u een bewerking met PDF-hulpprogramma&#39;s programmatisch kunt uitvoeren, moet u een PDFUtilityService-client maken. Met de Java API wordt dit bereikt door een `PDFUtilityServiceClient` object te maken. Met de webservice-API wordt dit gedaan met behulp van een `PDFUtilityServiceService` object.

**De modus Opslaan instellen**

U kunt een van de volgende opslagopties kiezen:

* `INCREMENTAL`: Opslaan in stappen om de tijd die nodig is om te besparen te verkorten
* `FAST_WEB_VIEW`: opslaan voor snelle webweergave
* `FULL`: Opslaan met een volledige opslagruimte (zonder optimalisaties)

**Opslaan van stijlbewerking aanroepen**

Nadat u de de dienstcliënt creeert, kunt u de eigenschappen terugwinningsverrichting aanhalen.

**Het PDF-document doorgeven aan een andere bewerking in AEM Forms**

Nadat de service PDF-hulpprogramma&#39;s de opgegeven opslagmodus heeft ingesteld, geeft u het PDF-document door aan een andere bewerking voor AEM-formulieren. Nadat het PDF-document door die bewerking is geretourneerd, wordt het in de opgegeven modus opgeslagen. Als u bijvoorbeeld de service PDF-hulpprogramma&#39;s gebruikt om de `FAST_WEB_VIEW` modus in te stellen en het PDF-document vervolgens doorgeeft aan de `encryptUsingPassword` bewerking van de coderingsservice, wordt het geretourneerde PDF-document versleuteld met een wachtwoord en opgeslagen in de `FAST_WEB_VIEW` modus.

>[!NOTE]
>
>Met Snel starten die aan deze sectie is gekoppeld, stelt u de `FAST_WEB_VIEW` modus in en geeft u het PDF-document door aan de `encryptUsingPassword` bewerking van de coderingsservice.

**Zie ook**

[Opties voor het opslaan van PDF-documenten instellen met de Java API](pdf-utilities.md#set-pdf-document-save-options-using-the-java-api)

[Opslagopties voor PDF-documenten instellen met de webservice-API](pdf-utilities.md#set-pdf-document-save-options-using-the-web-service-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[PDF-documenten versleutelen met een wachtwoord](/help/forms/developing/encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password)

### Opties voor het opslaan van PDF-documenten instellen met de Java API {#set-pdf-document-save-options-using-the-java-api}

Stel de opslagopties voor PDF-documenten in met de API voor PDF-hulpprogramma&#39;s (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-pdfutility-client.jar, op in het klassenpad van uw Java-project.

1. Een PDFUtilityService-client maken

   Maak een `PDFUtilityServiceClient` object door de constructor ervan te gebruiken en een `ServiceClientFactory` object door te geven dat verbindingseigenschappen bevat.

1. De modus Opslaan instellen

   * Maak een `PDFUtilitySaveMode` object met de constructor ervan.
   * Stel de opslagmodus in door de methode van het `PDFUtilitySaveMode` `setSaveStyle` object aan te roepen en een tekenreekswaarde door te geven die de opslagmodus aangeeft. Als u bijvoorbeeld wilt opslaan voor snelle webweergave, geeft u door `FAST_WEB_VIEW`.

1. Opslaan van stijlbewerking aanroepen

   Roep de methode van het `PDFUtilityServiceClient` `setSaveMode` object aan en geef de volgende waarden door:

   * Een `com.adobe.idp.Document` object dat staat voor het PDF-document.
   * Een `PDFUtilitySaveMode` object dat de stijl Opslaan bevat die moet worden gebruikt.
   * Een Booleaanse waarde die wordt gebruikt om te bepalen of vorige instellingen moeten worden overschreven.
   De methode retourneert een `com.adobe.idp.Document` object dat is opgemaakt met de opgegeven opslagstijl.

1. Het PDF-document doorgeven aan een andere bewerking in AEM Forms

   * Geef het geretourneerde `com.adobe.idp.Document` object door aan een andere bewerking in AEM Forms.

**Zie ook**

[Modus PDF-document opslaan instellen](pdf-utilities.md#setting-pdf-document-save-modes)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Opslagopties voor PDF-documenten instellen met de webservice-API {#set-pdf-document-save-options-using-the-web-service-api}

Stel de opslagopties voor PDF-documenten in met behulp van het AP PDF-hulpprogramma (webservice):

1. Projectbestanden opnemen

   * Creeer een de cliëntassemblage van Microsoft .NET die het dossier van WSDL van de dienst van het Nut PDF gebruikt.
   * Verwijs naar de cliëntassemblage van Microsoft .NET.

1. Een PDFUtilityService-client maken

   Maak een `PDFUtilityServiceService` object met de constructor van de proxyklasse.

1. De modus Opslaan instellen

   * Maak een `PDFUtilitySaveMode` object met de constructor ervan.
   * Stel de opslagmodus in door een tekenreekswaarde toe te wijzen aan de methode van het `PDFUtilitySaveMode` `saveStyle` object die de opslagmodus opgeeft. Als u bijvoorbeeld wilt opslaan voor snelle webweergave, geeft u op `FAST_WEB_VIEW`.

1. Opslaan van stijlbewerking aanroepen

   Roep de methode van het `PDFUtilityServiceService` `setSaveMode` object aan en geef de volgende waarden door:

   * Een `BLOB` object dat staat voor het PDF-document.
   * Een `PDFUtilitySaveMode` object dat de stijl Opslaan bevat die moet worden gebruikt.
   * Een Booleaanse waarde die wordt gebruikt om te bepalen of vorige instellingen moeten worden overschreven.
   De methode retourneert een `BLOB` object dat is opgemaakt met de opgegeven opslagstijl. U kunt dat object vervolgens opslaan als een PDF-document.

1. Het PDF-document doorgeven aan een andere formulierbewerking

   * Geef het geretourneerde `BLOB` object door aan een andere bewerking in AEM Forms.

**Zie ook**

[Modus PDF-document opslaan instellen](pdf-utilities.md#setting-pdf-document-save-modes)

[AEM-formulieren aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Creërend een .NET cliëntassemblage die het coderen Base64 gebruikt](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## PDF-documenten ontsmetten {#sanitizing-pdf-documents}

U kunt de PDF-hulpprogramma&#39;s van Java gebruiken om PDF-documenten programmatisch te converteren naar XDP-documenten.

>[!NOTE]
>
>Zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63)voor meer informatie over de service PDF-hulpprogramma&#39;s.

### Overzicht van de stappen {#summary_of_steps-4}

Voer de volgende stappen uit om het PDF-document te ontsmetten:

1. Inclusief projectbestanden.
1. Maak een PDFUtilityService-client.
1. Roep de ontsmettingsbewerking aan.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Neem de benodigde JAR-bestanden op als u een clienttoepassing met Java wilt maken.

**Een PDFUtilityService-client maken**

Alvorens u een ontsmettingsverrichting programmatically kunt uitvoeren, moet u een cliënt PDFUtilityService tot stand brengen. Met de Java API wordt dit bereikt door een `PDFUtilityServiceClient` object te maken.

**De conversiebewerking PDF naar XDP aanroepen**

Nadat u de de dienstcliënt creeert, kunt u de ontsmettingsverrichting aanhalen.

**Zie ook**

[PDF-documenten converteren naar XDP-documenten met de Java API](pdf-utilities.md#convert-pdf-documents-into-xdp-documents-using-the-java-api)

[PDF-documenten converteren naar XDP-documenten met de webservice-API](pdf-utilities.md#convert-pdf-documents-into-xdp-documents-using-the-web-service-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### PDF-documenten ontsmetten met de Java API {#sanitize-pdf-documents-using-the-java-api}

Documenten ontsmetten met de API voor PDF-hulpprogramma&#39;s (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-pdfutility-client.jar, op in het klassenpad van uw Java-project.

1. Een PDFUtilityService-client maken

   Maak een `PDFUtilityServiceClient` object door de constructor ervan te gebruiken en een `ServiceClientFactory` object door te geven dat verbindingseigenschappen bevat.

1. De conversiebewerking PDF naar XDP aanroepen

   Als u de conversie wilt uitvoeren, roept u de `PDFUtilityServiceClient` methode van het object aan en geeft u een `convertPDFtoXDP` `com.adobe.idp.Document` object door dat het PDF-bestand vertegenwoordigt. De methode retourneert een `com.adobe.idp.Document` object dat het nieuwe XDP-bestand vertegenwoordigt.

**Zie ook**

[PDF-documenten ontsmetten](/help/forms/developing/pdf-utilities-service-java-api.md#quick-start-soap-mode-sanitizing-pdf-documents)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)
