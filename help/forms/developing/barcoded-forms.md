---
title: Werken met formulieren met streepjescodes
description: Decodeer gegevens van een PDF-formulier of een afbeelding die een streepjescode bevat met behulp van de Java API en Web Service API.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: dd32808e-b773-48a2-90e1-7a277d349493
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,APIs & Integrations,Barcoded Forms
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '1911'
ht-degree: 0%

---

# Werken met formulieren met streepjescodes {#working-with-barcoded-forms}

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

## De service voor streepjescodes {#about-the-barcoded-forms-service}

De service voor streepjescodes automatiseert het vastleggen van gegevens van invulformulieren en integreert vastgelegde informatie in de belangrijkste IT-systemen van een organisatie.

Met de service voor streepjescodes kunt u eendimensionale en tweedimensionale streepjescodes toevoegen aan interactieve PDF forms. Vervolgens kunt u de formulieren met streepjescodes publiceren naar een website of deze via e-mail of cd verspreiden. Wanneer een gebruiker een formulier met streepjescodes invult in Adobe Reader, Acrobat Professional of Acrobat Standard, wordt de streepjescode automatisch bijgewerkt om de door de gebruiker opgegeven formuliergegevens te coderen. De gebruiker kan het formulier elektronisch verzenden of afdrukken naar papier en het verzenden per post, fax of hand. U kunt de gebruiker-geleverde gegevens als deel van een geautomatiseerde werkschema later halen, verpletterend de gegevens onder goedkeuringsprocessen en bedrijfssystemen.

Voor meer informatie over de service voor streepjescodes raadpleegt u [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Gecodeerde formuliergegevens decoderen {#decoding-barcoded-form-data}

U kunt de API van de service voor gecodeerde formulieren gebruiken om gegevens te decoderen van een PDF-formulier of een afbeelding die een streepjescode bevat. Formuliergegevens decoderen houdt in dat gegevens uit de streepjescode worden geëxtraheerd. Voordat gegevens kunnen worden gedecodeerd vanuit een PDF-formulier (of afbeelding), moet een gebruiker het formulier vullen met gegevens.

>[!NOTE]
>
>Voor meer informatie over de service voor streepjescodes raadpleegt u [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary-of-steps}

Voer de volgende stappen uit om gegevens van een PDF-formulier te decoderen:

1. Inclusief projectbestanden.
1. Maak een gestreepte formClient API-object.
1. Hiermee wordt een PDF-formulier opgehaald dat gecodeerde gegevens bevat.
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
* xercesImpl.jar (in &lt;install directory=&quot;&quot;>/Adobe/Adobe_Experience_Manager_forms/sdk/client-libs\thirdparty)

Als AEM Forms wordt geïmplementeerd op een ondersteunde J2EE-toepassingsserver die geen JBOSS is, moet u adobe-utilities.jar en jbossall-client.jar vervangen door JAR-bestanden die specifiek zijn voor de J2EE-toepassingsserver waarop AEM Forms wordt geïmplementeerd. Voor informatie over de locatie van alle AEM Forms JAR-bestanden raadpleegt u [Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Een gestreepte API-object voor formulieren maken**

Voordat u via programmacode een bewerking met een service voor streepjescodes kunt uitvoeren, moet u een Forms-serviceclient met streepjescodes maken. Als u de Java API gebruikt, maakt u een `BarcodedFormsServiceClient` object. Als u de API voor webservices voor streepjescodes gebruikt, maakt u een `BarcodedFormsServiceService` object.

**Een PDF-formulier ophalen dat gecodeerde gegevens bevat**

Vraag een PDF-formulier aan dat een streepjescode bevat die is gevuld met gebruikersgegevens.

**De gegevens decoderen uit het PDF-formulier**

Nadat u een PDF-formulier (of afbeelding) hebt ontvangen dat een streepjescode bevat, kunt u gegevens decoderen. De service Barcoded Forms ondersteunt de volgende typen streepjescodes:

* PDF417-streepjescodes.
* Streepjescodes gegevensmatrix.
* Streepjescodes van QR-code.
* Codabar-streepjescodes.
* Code 128 streepjescodes.
* Code 39 streepjescodes.
* EAN-13-streepjescodes.
* EAN-8 streepjescodes.

Invoer van tekensets als hexadecimale invoer in de decode-API houdt in dat de inhoud van de streepjescode wordt gecodeerd als een hexadecimale tekenreeks. Als UTF-8 bijvoorbeeld is opgegeven als tekencodering in het formulier en Hex is opgegeven in de decoderingsbewerking, wordt de inhoud van de streepjescode gecodeerd als een hexadecimale tekenreeks in de &lt; `xb:content`>-element in de gedecodeerde uitvoer. U kunt deze hexadecimale waarde omzetten om de oorspronkelijke inhoud op te halen door toepassingslogica in uw cliënttoepassing te creëren.

**De gegevens converteren naar een XML-gegevensbron**

Nadat u formuliergegevens hebt gedecodeerd, kunt u deze converteren naar XDP- of XFDF-gegevens. Stel bijvoorbeeld dat u de gegevens in een ander formulier wilt importeren. Als u de gegevens wilt importeren in een XFA-formulier, moet u de gegevens converteren naar XDP-gegevens. Zie voor meer informatie [Formuliergegevens importeren](/help/forms/developing/importing-exporting-data.md#importing-form-data).

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

   Een `BarcodedFormsServiceClient` object door de constructor ervan te gebruiken en een `ServiceClientFactory` object dat verbindingseigenschappen bevat.

1. Een PDF-formulier ophalen dat gecodeerde gegevens bevat

   * Een `java.io.FileInputStream` object dat het PDF-formulier vertegenwoordigt dat gecodeerde gegevens met streepjescodes bevat, door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het PDF-document aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. De gegevens decoderen uit het PDF-formulier

   De formuliergegevens decoderen door de `BarcodedFormsServiceClient` object `decode` en geeft de volgende waarden door:

   * De `com.adobe.idp.Document` object dat het PDF-formulier bevat.
   * A `java.lang.Boolean` object dat aangeeft of een PDF417-streepjescode moet worden gedecodeerd.
   * A `java.lang.Boolean` object dat aangeeft of een streepjescode voor een gegevensmatrix moet worden gedecodeerd.
   * A `java.lang.Boolean` object dat aangeeft of een streepjescode voor QR-code moet worden gedecodeerd.
   * A `java.lang.Boolean` een object dat aangeeft of een streepjescode voor een codabar moet worden gedecodeerd.
   * A `java.lang.Boolean` object dat aangeeft of een code 128-streepjescode moet worden gedecodeerd.
   * A `java.lang.Boolean` object dat aangeeft of een code 39-streepjescode moet worden gedecodeerd.
   * A `java.lang.Boolean` object dat aangeeft of een EAN-13-streepjescode moet worden gedecodeerd.
   * A `java.lang.Boolean` object dat aangeeft of een EAN-8-streepjescode moet worden gedecodeerd.
   * A `com.adobe.livecycle.barcodedforms.CharSet` opsommingswaarde die de coderingswaarde van de tekenset opgeeft die in de streepjescode wordt gebruikt.

   De `decode` methode retourneert een `org.w3c.dom.Document` object dat gedecodeerde formuliergegevens bevat.

1. De gegevens converteren naar een XML-gegevensbron

   De gedecodeerde gegevens converteren naar XDP- of XFDF-gegevens door het `BarcodedFormsServiceClient` object `extractToXML` en geeft de volgende waarden door:

   * De `org.w3c.dom.Document` object dat gedecodeerde gegevens bevat (gebruik de `decode` geretourneerde waarde van methode).
   * A `com.adobe.livecycle.barcodedforms.Delimiter` opsommingswaarde die het regelscheidingsteken aangeeft. U wordt aangeraden `Delimiter.Carriage_Return`.
   * A `com.adobe.livecycle.barcodedforms.Delimiter` opsommingswaarde die het veldscheidingsteken aangeeft. Geef bijvoorbeeld `Delimiter.Tab`.
   * A `com.adobe.livecycle.barcodedforms.XMLFormat` opsommingswaarde die aangeeft of de streepjescodegegevens moeten worden omgezet in XDP- of XFDF XML-gegevens. Geef bijvoorbeeld `XMLFormat.XDP` om de gegevens om te zetten in XDP-gegevens.

   >[!NOTE]
   >
   >Geef niet dezelfde waarden op voor de parameters voor regelscheidingsteken en veldscheidingsteken.

   De `extractToXML` methode retourneert een `java.util.List` object waarbij elk element een `org.w3c.dom.Document` object. Er is een afzonderlijk element voor elke streepjescode die zich op het formulier bevindt. Als er vier streepjescodes op het formulier staan, staan er vier elementen in het teruggestuurde formulier `java.util.List` object.

1. De gedecodeerde gegevens verwerken

   * Doorlopen `java.util.List` object om elk op te halen `org.w3c.dom.Document` -object in de lijst.
   * Voor elk element in de lijst converteert u de `org.w3c.dom.Document` object naar een `com.adobe.idp.Document` object. (De toepassingslogica die een `org.w3c.dom.Document` object in een `com.adobe.idp.Document` -object wordt weergegeven in de formuliergegevens met streepjescode decoderen met behulp van het Java API-voorbeeld).
   * Sla de XML-gegevens op als een XML-bestand door het `com.adobe.idp.Document` object `copyToFile`en geeft u een File-object door dat het XML-bestand vertegenwoordigt.

**Zie ook**

[Snel starten (SOAP modus): gecodeerde formuliergegevens decoderen met de Java API](/help/forms/developing/barcoded-forms-service-java-api.md#quick-start-soap-mode-decoding-barcoded-form-data-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Gecodeerde formuliergegevens decoderen met de webservice-API {#decode-barcoded-form-data-using-the-web-service-api}

Formuliergegevens decoderen met de API voor gecodeerde formulieren (webservice):

1. Projectbestanden opnemen

   * Creeer een de cliëntassemblage van Microsoft .NET die de streepjescoded dienst WSDL gebruikt. Zie voor meer informatie [AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).
   * Verwijs naar de Microsoft .NET cliëntassemblage. Voor informatie, zie &quot;Verwijzen van de .NET cliëntassemblage&quot;in [AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).

1. Een gestreepte API-object voor formulieren maken

   Het gebruiken van de de cliëntassemblage van Microsoft .NET die de streepjescoded dienst WSDL gebruikt, creeer een `BarcodedFormsServiceService` object door de standaardconstructor aan te roepen.

1. Een PDF-formulier ophalen dat gecodeerde gegevens bevat

   * Een `BLOB` object met behulp van de constructor. De `BLOB` wordt gebruikt om een PDF-document op te slaan dat een streepjescode bevat.
   * Een `System.IO.FileStream` door de constructor aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door het toe te wijzen `binaryData` eigenschap met de inhoud van de bytearray.

1. De gegevens decoderen uit het PDF-formulier

   De formuliergegevens decoderen door de `BarcodedFormsServiceService` object `decode` en geeft de volgende waarden door:

   * De `BLOB` object dat het PDF-formulier bevat.
   * A `Boolean` object dat aangeeft of een PDF417-streepjescode moet worden gedecodeerd.
   * A `Boolean` object dat aangeeft of een streepjescode voor een gegevensmatrix moet worden gedecodeerd.
   * A `Boolean` object dat aangeeft of een streepjescode voor QR-code moet worden gedecodeerd.
   * A `Boolean` een object dat aangeeft of een streepjescode voor een codabar moet worden gedecodeerd.
   * A `Boolean` object dat aangeeft of een code 128-streepjescode moet worden gedecodeerd.
   * A `Bolean` object dat aangeeft of een code 39-streepjescode moet worden gedecodeerd.
   * A `Boolean` object dat aangeeft of een EAN-13-streepjescode moet worden gedecodeerd.
   * A `Boolean` object dat aangeeft of een EAN-8-streepjescode moet worden gedecodeerd.
   * A `CharSet` opsommingswaarde die de coderingswaarde van de tekenset opgeeft die in de streepjescode wordt gebruikt.

   De `decode` Deze methode retourneert een tekenreekswaarde die gedecodeerde formuliergegevens bevat.

1. De gegevens converteren naar een XML-gegevensbron

   De gedecodeerde gegevens converteren naar XDP- of XFDF-gegevens door het `BarcodedFormsServiceService` object `extractToXML` en geeft de volgende waarden door:

   * Een tekenreekswaarde die gedecodeerde gegevens bevat (gebruik de optie `decode` geretourneerde waarde van methode).
   * A `Delimiter` opsommingswaarde die het regelscheidingsteken aangeeft. U wordt aangeraden `Delimiter.Carriage_Return`.
   * A `Delimiter` opsommingswaarde die het veldscheidingsteken aangeeft. Geef bijvoorbeeld `Delimiter.Tab`.
   * A `XMLFormat` opsommingswaarde die aangeeft of de streepjescodegegevens moeten worden omgezet in XDP- of XFDF XML-gegevens. Geef bijvoorbeeld `XMLFormat.XDP` om de gegevens om te zetten in XDP-gegevens.

   >[!NOTE]
   >
   >Geef niet dezelfde waarden op voor de parameters voor regelscheidingsteken en veldscheidingsteken.

   De `extractToXML` methode retourneert een `Object` array waarbij elk element een `BLOB` -instantie. Er is een afzonderlijk element voor elke streepjescode die zich op het formulier bevindt. Als er vier streepjescodes op het formulier staan, staan er vier elementen in het teruggestuurde formulier `Object` array.

1. De gedecodeerde gegevens verwerken

   * Een `System.IO.FileStream` door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het beveiligde PDF-document vertegenwoordigt.
   * Maak een bytearray waarin de gegevensinhoud van de `BLOB` object dat is geretourneerd door de `encryptPDFUsingPassword` methode. Vul de bytearray met de waarde van de `BLOB` object `binaryData` lid.
   * Een `System.IO.BinaryWriter` object door de constructor aan te roepen en de `System.IO.FileStream` object.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door het `System.IO.BinaryWriter` object `Write` en geeft u de bytearray door.

**Zie ook**

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
