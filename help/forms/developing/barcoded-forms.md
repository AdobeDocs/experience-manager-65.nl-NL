---
title: Werken met formulieren met streepjescodes
seo-title: Werken met formulieren met streepjescodes
description: Gegevens decoderen uit een PDF-formulier of een afbeelding die een streepjescode bevat met de Java API en Web Service API.
seo-description: Gegevens decoderen uit een PDF-formulier of een afbeelding die een streepjescode bevat met de Java API en Web Service API.
uuid: e56c3c94-384d-401f-b418-dd34cdc57eda
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: eb28ac30-265c-4611-8247-1f4bc826f254
translation-type: tm+mt
source-git-commit: 07889ead2ae402b5fb738ca08c7efe076ef33e44
workflow-type: tm+mt
source-wordcount: '1931'
ht-degree: 0%

---


# Werken met formulieren met streepjescodes {#working-with-barcoded-forms}

## Over de service voor gestreepte formulieren {#about-the-barcoded-forms-service}

De service voor streepjescodes automatiseert het vastleggen van gegevens van invulformulieren en integreert vastgelegde informatie in de belangrijkste IT-systemen van een organisatie.

Met de service voor streepjescodes kunt u eendimensionale en tweedimensionale streepjescodes toevoegen aan interactieve PDF forms. U kunt de gecodeerde formulieren vervolgens publiceren naar een website of ze via e-mail of cd verspreiden. Wanneer een gebruiker een formulier met streepjescodes invult in Adobe Reader, Acrobat Professional of Acrobat Standard, wordt de streepjescode automatisch bijgewerkt om de door de gebruiker opgegeven formuliergegevens te coderen. De gebruiker kan het formulier elektronisch verzenden of afdrukken naar papier en het verzenden per post, fax of hand. U kunt de gebruiker-geleverde gegevens als deel van een geautomatiseerde werkschema later halen, verpletterend de gegevens onder goedkeuringsprocessen en bedrijfssystemen.

Zie [Referentiehandleiding voor services voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63) voor meer informatie over de service voor streepjescodes.

## Gecodeerde formuliergegevens decoderen {#decoding-barcoded-form-data}

U kunt de API van de service voor streepjesgecodeerde formulieren gebruiken om gegevens te decoderen van een PDF-formulier of een afbeelding die een streepjescode bevat. Formuliergegevens decoderen betekent gegevens extraheren die zich in de streepjescode bevinden. Voordat gegevens uit een PDF-formulier (of afbeelding) kunnen worden gedecodeerd, moet een gebruiker het formulier vullen met gegevens.

>[!NOTE]
>
>Zie [Referentiehandleiding voor services voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63) voor meer informatie over de service voor streepjescodes.

### Overzicht van stappen {#summary-of-steps}

Voer de volgende stappen uit om gegevens van een PDF-formulier te decoderen:

1. Inclusief projectbestanden.
1. Maak een gestreepte formClient API-object.
1. Een PDF-formulier ophalen dat gecodeerde gegevens bevat.
1. De gegevens decoderen uit een PDF-formulier.
1. Zet de gegevens om in een XML-gegevensbron.
1. De gedecodeerde gegevens verwerken.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-barcodedforms-client.jar
* adobe-utilities.jar (Vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* xercesImpl.jar (bevindt zich in &lt;install directory>/Adobe/Adobe_Experience_Manager_forms/sdk/client-libs\thirdParty)

Als AEM Forms wordt geïmplementeerd op een ondersteunde J2EE-toepassingsserver die geen JBOSS is, moet u adobe-utilities.jar en jbossall-client.jar vervangen door JAR-bestanden die specifiek zijn voor de J2EE-toepassingsserver waarop AEM Forms wordt geïmplementeerd. Zie [Including AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files) voor informatie over de locatie van alle AEM Forms JAR-bestanden.

**Een gestreepte API-object voor formulieren maken**

Voordat u via programmacode een bewerking met een service voor streepjescodes kunt uitvoeren, moet u een Forms-serviceclient met streepjescodes maken. Als u de Java API gebruikt, maakt u een `BarcodedFormsServiceClient`-object. Als u de API voor webservice voor gestreepte formulieren gebruikt, maakt u een `BarcodedFormsServiceService`-object.

**Een PDF-formulier ophalen dat gecodeerde gegevens bevat**

U moet een PDF-formulier verkrijgen dat een streepjescode bevat die is gevuld met gebruikersgegevens.

**De gegevens decoderen uit het PDF-formulier**

Nadat u een PDF-formulier (of afbeelding) met een streepjescode hebt ontvangen, kunt u gegevens decoderen. De service Barcoded Forms ondersteunt de volgende typen streepjescodes:

* PDF417-streepjescodes.
* Streepjescodes gegevensmatrix.
* Streepjescodes van QR-code.
* Codabar-streepjescodes.
* Code 128 streepjescodes.
* Code 39 streepjescodes.
* EAN-13-streepjescodes.
* EAN-8 streepjescodes.

Invoer van tekensets als hexadecimale invoer in de decode-API houdt in dat de inhoud van de streepjescode wordt gecodeerd als een hexadecimale tekenreeks. Als UTF-8 bijvoorbeeld is opgegeven als tekencodering in het formulier en Hex is opgegeven in de decoderingsbewerking, wordt de inhoud van de streepjescode gecodeerd als een hexadecimale tekenreeks in het element &lt; `xb:content`> in de gedecodeerde uitvoer. U kunt deze hexadecimale waarde omzetten om de oorspronkelijke inhoud op te halen door toepassingslogica in uw cliënttoepassing te creëren.

**De gegevens converteren naar een XML-gegevensbron**

Nadat u formuliergegevens hebt gedecodeerd, kunt u deze converteren naar XDP- of XFDF-gegevens. Stel bijvoorbeeld dat u de gegevens in een ander formulier wilt importeren. Als u de gegevens wilt importeren in een XFA-formulier, moet u de gegevens converteren naar XDP-gegevens. Zie [Formuliergegevens importeren](/help/forms/developing/importing-exporting-data.md#importing-form-data) voor meer informatie.

**De gedecodeerde gegevens verwerken**

U kunt de omgezette gegevens verwerken om aan uw bedrijfsvereisten te voldoen. Nadat u de gegevens hebt gedecodeerd en geconverteerd, kunt u deze bijvoorbeeld opslaan in een bestand, opslaan in een ondernemingsdatabase, een ander formulier invullen, enzovoort. In deze sectie wordt besproken hoe de geconverteerde gegevens als een XML-bestand moeten worden opgeslagen.

>[!NOTE]
>
>De service voor gecodeerde formulieren decodeert geen streepjescodegegevens als het regelscheidingsteken en het veldscheidingsteken dezelfde waarde hebben

**Zie ook**

[Gecodeerde formuliergegevens decoderen met de Java API](barcoded-forms.md#decode-barcoded-form-data-using-the-java-api)

[Gecodeerde formuliergegevens decoderen met de webservice-API](barcoded-forms.md#decode-barcoded-form-data-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Gecodeerde formuliergegevens decoderen met de Java API {#decode-barcoded-form-data-using-the-java-api}

Formuliergegevens decoderen met de API voor streepjescodes (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden op in het klassenpad van uw Java-project.

1. Een gestreepte API-object voor formulieren maken

   Maak een `BarcodedFormsServiceClient`-object door de constructor ervan te gebruiken en een `ServiceClientFactory`-object door te geven dat verbindingseigenschappen bevat.

1. Een PDF-formulier ophalen dat gecodeerde gegevens bevat

   * Maak een `java.io.FileInputStream`-object dat het PDF-formulier met gecodeerde gegevens vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het PDF-document aangeeft.
   * Maak een `com.adobe.idp.Document`-object door de constructor ervan te gebruiken en het object `java.io.FileInputStream` door te geven.

1. De gegevens decoderen uit het PDF-formulier

   Decodeer de formuliergegevens door de methode `BarcodedFormsServiceClient` van het object `decode` aan te roepen en de volgende waarden door te geven:

   * Het object `com.adobe.idp.Document` dat het PDF-formulier bevat.
   * Een object `java.lang.Boolean` dat opgeeft of een PDF417-streepjescode moet worden gedecodeerd.
   * Een object `java.lang.Boolean` dat opgeeft of een streepjescode voor een gegevensmatrix moet worden gedecodeerd.
   * Een object `java.lang.Boolean` dat opgeeft of een streepjescode voor QR-code moet worden gedecodeerd.
   * Een object `java.lang.Boolean` dat opgeeft of een streepjescode van het type codabar moet worden gedecodeerd.
   * Een object `java.lang.Boolean` dat opgeeft of code 128-streepjescode moet worden gedecodeerd.
   * Een object `java.lang.Boolean` dat opgeeft of een code 39-streepjescode moet worden gedecodeerd.
   * Een object `java.lang.Boolean` dat opgeeft of een EAN-13-streepjescode moet worden gedecodeerd.
   * Een object `java.lang.Boolean` dat opgeeft of een EAN-8-streepjescode moet worden gedecodeerd.
   * Een `com.adobe.livecycle.barcodedforms.CharSet`-opsommingswaarde die de coderingswaarde voor de tekenset opgeeft die in de streepjescode wordt gebruikt.

   De methode `decode` retourneert een `org.w3c.dom.Document`-object dat gedecodeerde formuliergegevens bevat.

1. De gegevens converteren naar een XML-gegevensbron

   Zet de gedecodeerde gegevens om in XDP- of XFDF-gegevens door de methode `extractToXML` van het object `BarcodedFormsServiceClient` aan te roepen en de volgende waarden door te geven:

   * Het `org.w3c.dom.Document`-object dat gedecodeerde gegevens bevat (gebruik de geretourneerde waarde van de methode `decode`).
   * Een `com.adobe.livecycle.barcodedforms.Delimiter` opsommingswaarde die het lijnscheidingsteken specificeert. U wordt aangeraden `Delimiter.Carriage_Return` op te geven.
   * Een `com.adobe.livecycle.barcodedforms.Delimiter` opsommingswaarde die het gebiedsscheidingsteken specificeert. Geef bijvoorbeeld `Delimiter.Tab` op.
   * Een `com.adobe.livecycle.barcodedforms.XMLFormat`-opsommingswaarde die aangeeft of de streepjescodegegevens moeten worden omgezet in XDP- of XFDF XML-gegevens. Geef bijvoorbeeld `XMLFormat.XDP` op om de gegevens om te zetten in XDP-gegevens.

   >[!NOTE]
   >
   >Geef niet dezelfde waarden op voor de parameters voor regelscheidingsteken en veldscheidingsteken.

   De methode `extractToXML` retourneert een `java.util.List`-object waarbij elk element een `org.w3c.dom.Document`-object is. Er is een afzonderlijk element voor elke streepjescode die zich op het formulier bevindt. Als er vier streepjescodes op het formulier staan, bevat het geretourneerde `java.util.List`-object vier elementen.

1. De gedecodeerde gegevens verwerken

   * Doorloop het object `java.util.List` om elk object `org.w3c.dom.Document` in de lijst op te halen.
   * Zet voor elk element in de lijst het `org.w3c.dom.Document`-object om in een `com.adobe.idp.Document`-object. (De toepassingslogica die een object `org.w3c.dom.Document` omzet in een object `com.adobe.idp.Document` wordt weergegeven in het decoderen van gecodeerde formuliergegevens met behulp van het Java API-voorbeeld).
   * Sla de XML-gegevens op als een XML-bestand door het `com.adobe.idp.Document`-object `copyToFile` aan te roepen en een File-object door te geven dat het XML-bestand vertegenwoordigt.

**Zie ook**

[Snel starten (SOAP-modus): Gecodeerde formuliergegevens decoderen met de Java API](/help/forms/developing/barcoded-forms-service-java-api.md#quick-start-soap-mode-decoding-barcoded-form-data-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Gecodeerde formuliergegevens decoderen met de API {#decode-barcoded-form-data-using-the-web-service-api} van de webservice

Formuliergegevens decoderen met de API voor gecodeerde formulieren (webservice):

1. Projectbestanden opnemen

   * Creeer een de cliëntassemblage van Microsoft .NET die de streepjescoded dienst WSDL verbruikt. Zie [AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding) voor meer informatie.
   * Verwijs naar de cliëntassemblage van Microsoft .NET. Voor informatie, zie &quot;Verwijzen van de .NET cliëntassemblage&quot;in [het Aanhalen van AEM Forms gebruikend Base64 het coderen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).

1. Een gestreepte API-object voor formulieren maken

   Gebruikend de de cliëntassemblage van Microsoft .NET die de streepjescoded dienst WSDL gebruikt, creeer een `BarcodedFormsServiceService` voorwerp door zijn standaardaannemer aan te halen.

1. Een PDF-formulier ophalen dat gecodeerde gegevens bevat

   * Maak een `BLOB`-object met de constructor ervan. Met het object `BLOB` wordt een PDF-document met een streepjescode opgeslagen.
   * Maak een `System.IO.FileStream`-object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `System.IO.FileStream` van het object `Length` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het object `BLOB` door de eigenschap `binaryData` ervan toe te wijzen met de inhoud van de bytearray.

1. De gegevens decoderen uit het PDF-formulier

   Decodeer de formuliergegevens door de methode `BarcodedFormsServiceService` van het object `decode` aan te roepen en de volgende waarden door te geven:

   * Het object `BLOB` dat het PDF-formulier bevat.
   * Een object `Boolean` dat opgeeft of een PDF417-streepjescode moet worden gedecodeerd.
   * Een object `Boolean` dat opgeeft of een streepjescode voor een gegevensmatrix moet worden gedecodeerd.
   * Een object `Boolean` dat opgeeft of een streepjescode voor QR-code moet worden gedecodeerd.
   * Een object `Boolean` dat opgeeft of een streepjescode van het type codabar moet worden gedecodeerd.
   * Een object `Boolean` dat opgeeft of code 128-streepjescode moet worden gedecodeerd.
   * Een object `Bolean` dat opgeeft of een code 39-streepjescode moet worden gedecodeerd.
   * Een object `Boolean` dat opgeeft of een EAN-13-streepjescode moet worden gedecodeerd.
   * Een object `Boolean` dat opgeeft of een EAN-8-streepjescode moet worden gedecodeerd.
   * Een `CharSet`-opsommingswaarde die de coderingswaarde voor de tekenset opgeeft die in de streepjescode wordt gebruikt.

   De methode `decode` retourneert een tekenreekswaarde die gedecodeerde formuliergegevens bevat.

1. De gegevens converteren naar een XML-gegevensbron

   Zet de gedecodeerde gegevens om in XDP- of XFDF-gegevens door de methode `extractToXML` van het object `BarcodedFormsServiceService` aan te roepen en de volgende waarden door te geven:

   * Een tekenreekswaarde die gedecodeerde gegevens bevat (gebruik de geretourneerde waarde van de methode `decode`).
   * Een `Delimiter` opsommingswaarde die het lijnscheidingsteken specificeert. U wordt aangeraden `Delimiter.Carriage_Return` op te geven.
   * Een `Delimiter` opsommingswaarde die het gebiedsscheidingsteken specificeert. Geef bijvoorbeeld `Delimiter.Tab` op.
   * Een `XMLFormat`-opsommingswaarde die aangeeft of de streepjescodegegevens moeten worden omgezet in XDP- of XFDF XML-gegevens. Geef bijvoorbeeld `XMLFormat.XDP` op om de gegevens om te zetten in XDP-gegevens.

   >[!NOTE]
   >
   >Geef niet dezelfde waarden op voor de parameters voor regelscheidingsteken en veldscheidingsteken.

   De `extractToXML` methode keert een `Object` serie terug waar elk element een `BLOB` instantie is. Er is een afzonderlijk element voor elke streepjescode die zich op het formulier bevindt. Dat wil zeggen dat als er vier streepjescodes op het formulier staan, de geretourneerde `Object`-array vier elementen bevat.

1. De gedecodeerde gegevens verwerken

   * Maak een `System.IO.FileStream`-object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het beveiligde PDF-document vertegenwoordigt.
   * Maak een bytearray met de gegevensinhoud van het object `BLOB` dat door de methode `encryptPDFUsingPassword` is geretourneerd. Vul de bytearray met de waarde van het `BLOB`-gegevenslid van het object `binaryData`.
   * Maak een `System.IO.BinaryWriter`-object door de constructor ervan aan te roepen en het object `System.IO.FileStream` door te geven.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door de methode `Write` van het object `System.IO.BinaryWriter` aan te roepen en de bytearray door te geven.

**Zie ook**

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
