---
title: Werken met PDF-hulpprogramma's
seo-title: Werken met PDF-hulpprogramma's
description: Met de service PDF-hulpprogramma's kunt u converteren tussen PDF- en XDP-bestandsindelingen, PDF-documenteigenschappen instellen en ophalen en XMP metagegevens bewerken.
seo-description: Met de service PDF-hulpprogramma's kunt u converteren tussen PDF- en XDP-bestandsindelingen, PDF-documenteigenschappen instellen en ophalen en XMP metagegevens bewerken.
uuid: a2ea2359-c547-4f1b-b6ca-f276f816e36a
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: d816bf2e-5236-4084-b7c4-c32b72cdff97
translation-type: tm+mt
source-git-commit: 07889ead2ae402b5fb738ca08c7efe076ef33e44
workflow-type: tm+mt
source-wordcount: '2592'
ht-degree: 0%

---


# Werken met PDF-hulpprogramma&#39;s {#working-with-pdf-utilities}

**Informatie over de PDF-hulpprogramma&#39;s**

De service PDF-hulpprogramma&#39;s kan converteren tussen PDF- en XDP-bestandsindelingen, PDF-documenteigenschappen instellen en ophalen en XMP metagegevens bewerken. Voordat u bijvoorbeeld een PDF-document naar een andere indeling converteert, is het handig om de eigenschappen te controleren om te bepalen welke servicebewerking moet worden aangeroepen voor de conversie.

U kunt deze taken uitvoeren met de service PDF-hulpprogramma&#39;s:

* Converteer PDF-documenten naar XDP-documenten.
* XDP-documenten converteren naar PDF-documenten. (Zie [XDP-documenten converteren naar PDF-documenten](pdf-utilities.md#converting-xdp-documents-into-pdf-documents).)
* Eigenschappen PDF-document ophalen. (Zie [Eigenschappen PDF-document ophalen](pdf-utilities.md#retrieving-pdf-document-properties).)
* Sla een PDF-document op en optimaliseer het voor snelle webweergave. (Zie [Opslagmodi voor PDF-documenten instellen](pdf-utilities.md#setting-pdf-document-save-modes).)

>[!NOTE]
>
>Zie [Referentiehandleiding voor services voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63) voor meer informatie over de service PDF-hulpprogramma&#39;s.

## PDF-documenten converteren naar XDP-documenten {#converting-pdf-documents-into-xdp-documents}

Met de PDF-hulpprogramma&#39;s Java en API&#39;s voor webservices kunt u PDF-documenten programmatisch converteren naar XDP-documenten.

>[!NOTE]
>
>Zie [Referentiehandleiding voor services voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63) voor meer informatie over de service PDF-hulpprogramma&#39;s.

### Overzicht van stappen {#summary-of-steps}

Voer de volgende stappen uit om een PDF-document te converteren naar een XDP-document:

1. Inclusief projectbestanden.
1. Maak een PDFUtilityService-client.
1. Roep de conversiebewerking PDF naar XDP aan.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**Een PDFUtilityService-client maken**

Voordat u een bewerking met PDF-hulpprogramma&#39;s programmatisch kunt uitvoeren, moet u een PDFUtilityService-client maken. Met Java API, wordt dit verwezenlijkt door een `PDFUtilityServiceClient` voorwerp te creëren. Met de webservice-API wordt dit bereikt door een `PDFUtilityServiceService`-object te gebruiken.

**De conversiebewerking PDF naar XDP aanroepen**

Nadat u de serviceclient hebt gemaakt, kunt u de conversiebewerking PDF naar XDP uitvoeren.

**Zie ook**

[PDF-documenten converteren naar XDP-documenten met de Java API](pdf-utilities.md#convert-pdf-documents-into-xdp-documents-using-the-java-api)

[PDF-documenten converteren naar XDP-documenten met de webservice-API](pdf-utilities.md#convert-pdf-documents-into-xdp-documents-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### PDF-documenten converteren naar XDP-documenten met de Java API {#convert-pdf-documents-into-xdp-documents-using-the-java-api}

PDF-documenten converteren naar XDP-documenten met de API voor PDF-hulpprogramma&#39;s (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-pdfutility-client.jar, op in het klassenpad van uw Java-project.

1. Een PDFUtilityService-client maken

   Maak een `PDFUtilityServiceClient`-object door de constructor ervan te gebruiken en een `ServiceClientFactory`-object door te geven dat verbindingseigenschappen bevat.

1. De conversiebewerking PDF naar XDP aanroepen

   Als u de conversie wilt uitvoeren, roept u de methode `convertPDFtoXDP` van het object `PDFUtilityServiceClient` aan en geeft u een object `com.adobe.idp.Document` dat het PDF-bestand vertegenwoordigt door. De methode retourneert een `com.adobe.idp.Document`-object dat het nieuwe XDP-bestand vertegenwoordigt.

**Zie ook**

[PDF-documenten converteren naar XDP-documenten](pdf-utilities.md#converting-pdf-documents-into-xdp-documents)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### PDF-documenten converteren naar XDP-documenten met de webservice-API {#convert-pdf-documents-into-xdp-documents-using-the-web-service-api}

Converteer PDF-documenten naar XDP-documenten met de PDF Utilities API (webservice):

1. Projectbestanden opnemen

   * Creeer een de cliëntassemblage van Microsoft .NET die het dossier van WSDL van de dienst van het Nut PDF gebruikt.
   * Verwijs naar de cliëntassemblage van Microsoft .NET.

1. Een PDFUtilityService-client maken

   Maak een `PDFUtilityServiceService`-object met de constructor van de proxyklasse.

1. De conversiebewerking PDF naar XDP aanroepen

   Roep de methode `PDFUtilityServiceService` van het object `convertPDFtoXDP` aan en geef een object `BLOB` dat het PDF-bestand vertegenwoordigt door. De methode retourneert een `BLOB`-object dat het nieuwe XDP-bestand vertegenwoordigt.

**Zie ook**

[PDF-documenten converteren naar XDP-documenten](pdf-utilities.md#converting-pdf-documents-into-xdp-documents)

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Creërend een .NET cliëntassemblage die het coderen Base64 gebruikt](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## XDP-documenten converteren naar PDF-documenten {#converting-xdp-documents-into-pdf-documents}

Met de PDF Utilities Java en de webservice-API&#39;s kunt u XDP-documenten programmatisch converteren naar PDF-documenten.

>[!NOTE]
>
>Zie [Referentiehandleiding voor services voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63) voor meer informatie over de service PDF-hulpprogramma&#39;s.

### Overzicht van stappen {#summary_of_steps-1}

Voer de volgende stappen uit om een XDP-document te converteren naar een PDF-document:

1. Inclusief projectbestanden.
1. Maak een PDFUtilityService-client.
1. Roep de conversiebewerking XDP naar PDF aan.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**Een PDFUtilityService-client maken**

Voordat u een bewerking met PDF-hulpprogramma&#39;s programmatisch kunt uitvoeren, moet u een PDFUtilityService-client maken. Met Java API, wordt dit verwezenlijkt door een `PDFUtilityServiceClient` voorwerp te creëren. Met de webservice-API wordt dit bereikt door een `PDFUtilityServiceService`-object te gebruiken.

**De conversiebewerking XDP naar PDF aanroepen**

Nadat u de serviceclient hebt gemaakt, kunt u de conversiebewerking XDP naar PDF uitvoeren.

**Zie ook**

[XDP-documenten converteren naar PDF-documenten met de Java API](pdf-utilities.md#convert-xdp-documents-into-pdf-documents-using-the-java-api)

[XDP-documenten converteren naar PDF-documenten met de webservice-API](pdf-utilities.md#converting-xdp-documents-into-pdf-documents-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### XDP-documenten converteren naar PDF-documenten met de Java API {#convert-xdp-documents-into-pdf-documents-using-the-java-api}

XDP-documenten converteren naar PDF-documenten met de PDF Utilities API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-pdfutility-client.jar, op in het klassenpad van uw Java-project.

1. Een PDFUtilityService-client maken

   Maak een `PDFUtilityServiceClient`-object door de constructor ervan te gebruiken en een `ServiceClientFactory`-object door te geven dat verbindingseigenschappen bevat.

1. De conversiebewerking XDP naar PDF aanroepen

   Als u de conversie wilt uitvoeren, roept u de methode `convertXDPtoPDF` van het object `PDFUtilityServiceClient` aan en geeft u een object `com.adobe.idp.Document` dat het XDP-bestand vertegenwoordigt door. De methode retourneert een `com.adobe.idp.Document`-object dat het zojuist gemaakte PDF-bestand vertegenwoordigt.

**Zie ook**

[XDP-documenten converteren naar PDF-documenten](pdf-utilities.md#converting-xdp-documents-into-pdf-documents)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### XDP-documenten converteren naar PDF-documenten met de webservice-API {#converting-xdp-documents-into-pdf-documents-using-the-web-service-api}

XDP-documenten converteren naar PDF-documenten met behulp van de PDF Utilities API (webservice-API):

1. Projectbestanden opnemen

   * Creeer een de cliëntassemblage van Microsoft .NET die het dossier van WSDL van de dienst van het Nut PDF gebruikt.
   * Verwijs naar de cliëntassemblage van Microsoft .NET.

1. Een PDFUtilityService-client maken

   Maak een `PDFUtilityServiceService`-object met de constructor van de proxyklasse.

1. De conversiebewerking XDP naar PDF aanroepen

   Als u de conversie wilt uitvoeren, roept u de methode `convertXDPtoPDF` van het object `PDFUtilityServiceService` aan en geeft u een object `BLOB` dat het XDP-bestand vertegenwoordigt door. De methode retourneert een `BLOB`-object dat het zojuist gemaakte PDF-bestand vertegenwoordigt.

**Zie ook**

[XDP-documenten converteren naar PDF-documenten](pdf-utilities.md#converting-xdp-documents-into-pdf-documents)

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Creërend een .NET cliëntassemblage die het coderen Base64 gebruikt](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## Eigenschappen PDF-document {#retrieving-pdf-document-properties} ophalen

Met de PDF Utilities Java en de webservice-API&#39;s kunt u PDF-documenteigenschappen programmatisch ophalen, bijvoorbeeld of het document een invulbaar formulier is of de minimaal vereiste Acrobat-versie om het document te lezen.

>[!NOTE]
>
>Zie [Referentiehandleiding voor services voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63) voor meer informatie over de service PDF-hulpprogramma&#39;s.

### Overzicht van stappen {#summary_of_steps-2}

Voer de volgende stappen uit om PDF-documenteigenschappen op te halen:

1. Inclusief projectbestanden.
1. Maak een PDFUtilityService-client.
1. Roep de ophaalbewerking voor eigenschappen aan.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**Een PDFUtilityService-client maken**

Voordat u een bewerking met PDF-hulpprogramma&#39;s programmatisch kunt uitvoeren, moet u een PDFUtilityService-client maken. Met Java API, wordt dit verwezenlijkt door een `PDFUtilityServiceClient` voorwerp te creëren. Met de webservice-API wordt dit gedaan met behulp van een `PDFUtilityServiceService`-object.

**Ophaalbewerking voor eigenschappen aanroepen**

Nadat u de de dienstcliënt creeert, kunt u de eigenschappen terugwinningsverrichting aanhalen.

**Zie ook**

[Eigenschappen van PDF-documenten ophalen met de Java API](pdf-utilities.md#retrieve-pdf-document-properties-using-the-java-api)

[Eigenschappen van PDF-documenten ophalen met de webservice-API](pdf-utilities.md#retrieve-pdf-document-properties-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Eigenschappen van PDF-documenten ophalen met de Java API {#retrieve-pdf-document-properties-using-the-java-api}

U kunt de eigenschappen van PDF-documenten ophalen met de API voor PDF-hulpprogramma&#39;s (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-pdfutility-client.jar, op in het klassenpad van uw Java-project.

1. Een PDFUtilityService-client maken

   Maak een `PDFUtilityServiceClient`-object door de constructor ervan te gebruiken en een `ServiceClientFactory`-object door te geven dat verbindingseigenschappen bevat.

1. Ophaalbewerking voor eigenschappen aanroepen

   Als u de conversie wilt uitvoeren, roept u de methode `getPDFProperties` van het object `PDFUtilityServiceClient` op en geeft u het volgende door:

   * Een `com.adobe.idp.Document`-object dat het PDF-document vertegenwoordigt.
   * Een object `PDFPropertiesOptionSpec` dat de eigenschappen bevat die moeten worden geëvalueerd.

   De methode retourneert een `PDFPropertiesResult`-object dat de resultaten van de query bevat.

**Zie ook**

[Eigenschappen PDF-document ophalen](pdf-utilities.md#retrieving-pdf-document-properties)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Eigenschappen van PDF-documenten ophalen met de webservice-API {#retrieve-pdf-document-properties-using-the-web-service-api}

U kunt de eigenschappen van PDF-documenten ophalen met de API voor de PDF-hulpprogramma&#39;s:

1. Projectbestanden opnemen

   * Creeer een de cliëntassemblage van Microsoft .NET die het dossier van WSDL van de dienst van het Nut PDF gebruikt.
   * Verwijs naar de cliëntassemblage van Microsoft .NET.

1. Een PDFUtilityService-client maken

   Maak een `PDFUtilityServiceService`-object met de constructor van de proxyklasse.

1. Ophaalbewerking voor eigenschappen aanroepen

   Als u de conversie wilt uitvoeren, roept u de methode `getPDFProperties` van het object `PDFUtilityServiceService` op en geeft u het volgende door:

   * Een `BLOB`-object dat het PDF-document vertegenwoordigt.
   * Een object `PDFPropertiesOptionSpec` dat de eigenschappen bevat die moeten worden geëvalueerd.

   De methode retourneert een `PDFPropertiesResult`-object dat de resultaten van de query bevat.

**Zie ook**

[Eigenschappen PDF-document ophalen](pdf-utilities.md#retrieving-pdf-document-properties)

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Creërend een .NET cliëntassemblage die het coderen Base64 gebruikt](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## Modi voor het opslaan van PDF-documenten instellen {#setting-pdf-document-save-modes}

Met de Java- en webservice-API&#39;s van de PDF-hulpprogramma&#39;s kunt u een opslagmodus voor een PDF-document programmatisch instellen. Als u een opslagmodus instelt met de service PDF-hulpprogramma&#39;s, stelt de service PDF-hulpprogramma&#39;s alleen de opslagmodus in en wordt het PDF-document niet daadwerkelijk opgeslagen. Het PDF-document wordt opgeslagen wanneer het wordt doorgegeven aan een andere servicebewerking. U kunt bijvoorbeeld de service PDF-hulpprogramma&#39;s gebruiken om een specifieke opslagmodus in te stellen en deze door te geven aan de coderingsservice, waarbij het PDF-document daadwerkelijk wordt opgeslagen en versleuteld.

>[!NOTE]
>
>Zie [Referentiehandleiding voor services voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63) voor meer informatie over de service PDF-hulpprogramma&#39;s.

### Overzicht van stappen {#summary_of_steps-3}

Voer de volgende stappen uit om de opslagoptie voor PDF-documenten in te stellen:

1. Inclusief projectbestanden.
1. Maak een PDFUtilityService-client.
1. Stel de opslagmodus in.
1. Roep de opslagbewerking aan.
1. Geef het PDF-document door aan een andere bewerking.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**Een PDFUtilityService-client maken**

Voordat u een bewerking met PDF-hulpprogramma&#39;s programmatisch kunt uitvoeren, moet u een PDFUtilityService-client maken. Met Java API, wordt dit verwezenlijkt door een `PDFUtilityServiceClient` voorwerp te creëren. Met de webservice-API wordt dit gedaan met behulp van een `PDFUtilityServiceService`-object.

**De modus Opslaan instellen**

U kunt een van de volgende opslagopties kiezen:

* `INCREMENTAL`: Opslaan in stappen om de tijd die nodig is om te besparen te verkorten
* `FAST_WEB_VIEW`: opslaan voor snelle webweergave
* `FULL`: Opslaan met een volledige opslagruimte (zonder optimalisaties)

**Opslaan van stijlbewerking aanroepen**

Nadat u de de dienstcliënt creeert, kunt u de eigenschappen terugwinningsverrichting aanhalen.

**Het PDF-document doorgeven aan een andere AEM Forms-bewerking**

Nadat de service PDF-hulpprogramma&#39;s de opgegeven opslagmodus heeft ingesteld, geeft u het PDF-document door aan een andere AEM Forms-bewerking. Nadat het PDF-document door die bewerking is geretourneerd, wordt het in de opgegeven modus opgeslagen. Als u bijvoorbeeld de service PDF-hulpprogramma&#39;s gebruikt om de modus `FAST_WEB_VIEW` in te stellen en het PDF-document vervolgens doorgeeft aan de bewerking `encryptUsingPassword` van de coderingsservice, wordt het geretourneerde PDF-document versleuteld met een wachtwoord en opgeslagen in de modus `FAST_WEB_VIEW`.

>[!NOTE]
>
>Met Snel starten dat aan deze sectie is gekoppeld, stelt u de modus `FAST_WEB_VIEW` in en geeft u het PDF-document vervolgens door aan de bewerking `encryptUsingPassword` van de coderingsservice.

**Zie ook**

[Opties voor het opslaan van PDF-documenten instellen met de Java API](pdf-utilities.md#set-pdf-document-save-options-using-the-java-api)

[Opslagopties voor PDF-documenten instellen met de webservice-API](pdf-utilities.md#set-pdf-document-save-options-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[PDF-documenten versleutelen met een wachtwoord](/help/forms/developing/encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password)

### Opties voor het opslaan van PDF-documenten instellen met de Java API {#set-pdf-document-save-options-using-the-java-api}

Stel de opslagopties voor PDF-documenten in met de API voor PDF-hulpprogramma&#39;s (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-pdfutility-client.jar, op in het klassenpad van uw Java-project.

1. Een PDFUtilityService-client maken

   Maak een `PDFUtilityServiceClient`-object door de constructor ervan te gebruiken en een `ServiceClientFactory`-object door te geven dat verbindingseigenschappen bevat.

1. De modus Opslaan instellen

   * Maak een `PDFUtilitySaveMode`-object met de constructor ervan.
   * Stel de opslagmodus in door de methode `setSaveStyle` van het object `PDFUtilitySaveMode` aan te roepen en een tekenreekswaarde door te geven die de opslagmodus aangeeft. Als u bijvoorbeeld wilt opslaan voor snelle webweergave, geeft u `FAST_WEB_VIEW` door.

1. Opslaan van stijlbewerking aanroepen

   Roep de methode `setSaveMode` van het object `PDFUtilityServiceClient` aan en geef de volgende waarden door:

   * Een `com.adobe.idp.Document`-object dat het PDF-document vertegenwoordigt.
   * Een `PDFUtilitySaveMode`-object dat de opslagstijl bevat die moet worden gebruikt.
   * Een Booleaanse waarde die wordt gebruikt om te bepalen of vorige instellingen moeten worden overschreven.

   De methode retourneert een `com.adobe.idp.Document`-object dat is opgemaakt met de opgegeven opslagstijl.

1. Het PDF-document doorgeven aan een andere AEM Forms-bewerking

   * Geef het geretourneerde `com.adobe.idp.Document`-object door aan een andere AEM Forms-bewerking.

**Zie ook**

[Modus PDF-document opslaan instellen](pdf-utilities.md#setting-pdf-document-save-modes)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Opties voor het opslaan van PDF-documenten instellen met de webservice-API {#set-pdf-document-save-options-using-the-web-service-api}

Stel de opslagopties voor PDF-documenten in met behulp van het AP PDF-hulpprogramma (webservice):

1. Projectbestanden opnemen

   * Creeer een de cliëntassemblage van Microsoft .NET die het dossier van WSDL van de dienst van het Nut PDF gebruikt.
   * Verwijs naar de cliëntassemblage van Microsoft .NET.

1. Een PDFUtilityService-client maken

   Maak een `PDFUtilityServiceService`-object met de constructor van de proxyklasse.

1. De modus Opslaan instellen

   * Maak een `PDFUtilitySaveMode`-object met de constructor ervan.
   * Stel de opslagmodus in door een tekenreekswaarde toe te wijzen aan de methode `PDFUtilitySaveMode` van het object waarmee de opslagmodus wordt opgegeven. `saveStyle` Als u bijvoorbeeld wilt opslaan voor snelle webweergave, geeft u `FAST_WEB_VIEW` op.

1. Opslaan van stijlbewerking aanroepen

   Roep de methode `setSaveMode` van het object `PDFUtilityServiceService` aan en geef de volgende waarden door:

   * Een `BLOB`-object dat het PDF-document vertegenwoordigt.
   * Een `PDFUtilitySaveMode`-object dat de opslagstijl bevat die moet worden gebruikt.
   * Een Booleaanse waarde die wordt gebruikt om te bepalen of vorige instellingen moeten worden overschreven.

   De methode retourneert een `BLOB`-object dat is opgemaakt met de opgegeven opslagstijl. U kunt dat object vervolgens opslaan als een PDF-document.

1. Het PDF-document doorgeven aan een andere Forms-bewerking

   * Geef het geretourneerde `BLOB`-object door aan een andere AEM Forms-bewerking.

**Zie ook**

[Modus PDF-document opslaan instellen](pdf-utilities.md#setting-pdf-document-save-modes)

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Creërend een .NET cliëntassemblage die het coderen Base64 gebruikt](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## PDF-documenten {#sanitizing-pdf-documents} ontsmetten

U kunt de PDF-hulpprogramma&#39;s van Java gebruiken om PDF-documenten programmatisch te converteren naar XDP-documenten.

>[!NOTE]
>
>Zie [Referentiehandleiding voor services voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63) voor meer informatie over de service PDF-hulpprogramma&#39;s.

### Overzicht van stappen {#summary_of_steps-4}

Voer de volgende stappen uit om het PDF-document te ontsmetten:

1. Inclusief projectbestanden.
1. Maak een PDFUtilityService-client.
1. Roep de ontsmettingsbewerking aan.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Neem de benodigde JAR-bestanden op als u een clienttoepassing met Java wilt maken.

**Een PDFUtilityService-client maken**

Alvorens u een ontsmettingsverrichting programmatically kunt uitvoeren, moet u een cliënt PDFUtilityService tot stand brengen. Met Java API, wordt dit verwezenlijkt door een `PDFUtilityServiceClient` voorwerp te creëren.

**De conversiebewerking PDF naar XDP aanroepen**

Nadat u de de dienstcliënt creeert, kunt u de ontsmettingsverrichting aanhalen.

**Zie ook**

[PDF-documenten converteren naar XDP-documenten met de Java API](pdf-utilities.md#convert-pdf-documents-into-xdp-documents-using-the-java-api)

[PDF-documenten converteren naar XDP-documenten met de webservice-API](pdf-utilities.md#convert-pdf-documents-into-xdp-documents-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### PDF-documenten ontsmetten met de Java API {#sanitize-pdf-documents-using-the-java-api}

Documenten ontsmetten met de API voor PDF-hulpprogramma&#39;s (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-pdfutility-client.jar, op in het klassenpad van uw Java-project.

1. Een PDFUtilityService-client maken

   Maak een `PDFUtilityServiceClient`-object door de constructor ervan te gebruiken en een `ServiceClientFactory`-object door te geven dat verbindingseigenschappen bevat.

1. De conversiebewerking PDF naar XDP aanroepen

   Als u de conversie wilt uitvoeren, roept u de methode `convertPDFtoXDP` van het object `PDFUtilityServiceClient` aan en geeft u een object `com.adobe.idp.Document` dat het PDF-bestand vertegenwoordigt door. De methode retourneert een `com.adobe.idp.Document`-object dat het nieuwe XDP-bestand vertegenwoordigt.

**Zie ook**

[PDF-documenten ontsmetten](/help/forms/developing/pdf-utilities-service-java-api.md#quick-start-soap-mode-sanitizing-pdf-documents)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)
