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

**de Steekproeven en de voorbeelden in dit document zijn slechts voor AEM Forms op milieu JEE.**

## De service voor streepjescodes {#about-the-barcoded-forms-service}

De service voor streepjescodes automatiseert het vastleggen van gegevens van invulformulieren en integreert vastgelegde informatie in de belangrijkste IT-systemen van een organisatie.

Met de service voor streepjescodes kunt u eendimensionale en tweedimensionale streepjescodes toevoegen aan interactieve PDF forms. Vervolgens kunt u de formulieren met streepjescodes publiceren naar een website of deze via e-mail of cd verspreiden. Wanneer een gebruiker een formulier met streepjescodes invult in Adobe Reader, Acrobat Professional of Acrobat Standard, wordt de streepjescode automatisch bijgewerkt om de door de gebruiker opgegeven formuliergegevens te coderen. De gebruiker kan het formulier elektronisch verzenden of afdrukken naar papier en het verzenden per post, fax of hand. U kunt de gebruiker-geleverde gegevens als deel van een geautomatiseerde werkschema later halen, verpletterend de gegevens onder goedkeuringsprocessen en bedrijfssystemen.

Voor meer informatie over de streepjescoded vormendienst, zie [ Verwijzing van de Diensten voor AEM Forms ](https://www.adobe.com/go/learn_aemforms_services_63).

## Gecodeerde formuliergegevens decoderen {#decoding-barcoded-form-data}

U kunt de API van de service voor gecodeerde formulieren gebruiken om gegevens te decoderen van een PDF-formulier of een afbeelding die een streepjescode bevat. Formuliergegevens decoderen houdt in dat gegevens uit de streepjescode worden geëxtraheerd. Voordat gegevens kunnen worden gedecodeerd vanuit een PDF-formulier (of afbeelding), moet een gebruiker het formulier vullen met gegevens.

>[!NOTE]
>
>Voor meer informatie over de streepjescoded vormendienst, zie [ Verwijzing van de Diensten voor AEM Forms ](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary-of-steps}

Voer de volgende stappen uit om gegevens van een PDF-formulier te decoderen:

1. Inclusief projectbestanden.
1. Maak een gestreepte formClient API-object.
1. Hiermee wordt een PDF-formulier opgehaald dat gecodeerde gegevens bevat.
1. De gegevens decoderen uit een PDF-formulier.
1. Zet de gegevens om in een XML-gegevensbron.
1. De gedecodeerde gegevens verwerken.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-barcodedforms-client.jar
* adobe-utilities.jar (Vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* xercesImpl.jar (in &lt;install directory>/Adobe/Adobe_Experience_Manager_forms/sdk/client-libs\thirdParty)

Als AEM Forms wordt geïmplementeerd op een ondersteunde J2EE-toepassingsserver die geen JBOSS is, moet u adobe-utilities.jar en jbossall-client.jar vervangen door JAR-bestanden die specifiek zijn voor de J2EE-toepassingsserver waarop AEM Forms wordt geïmplementeerd. Voor informatie over de plaats van alle dossiers van AEM Forms JAR, zie [ Inclusief de bibliotheekdossiers van AEM Forms Java ](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**creeer een streepjescoded voorwerp van de cliënt API van vormen**

Voordat u via programmacode een bewerking met een service voor streepjescodes kunt uitvoeren, moet u een Forms-serviceclient met streepjescodes maken. Maak een `BarcodedFormsServiceClient` -object als u de Java API gebruikt. Als u de API voor webservices voor streepjescodes gebruikt, maakt u een `BarcodedFormsServiceService` -object.

**krijg een vorm van PDF die streepjescoded gegevens** bevat

Vraag een PDF-formulier aan dat een streepjescode bevat die is gevuld met gebruikersgegevens.

**decodeer de gegevens van de vorm van PDF**

Nadat u een PDF-formulier (of afbeelding) hebt ontvangen dat een streepjescode bevat, kunt u gegevens decoderen. De service Barcoded Forms ondersteunt de volgende typen streepjescodes:

* PDF417-streepjescodes.
* Streepjescodes gegevensmatrix.
* Streepjescodes van QR-code.
* Codabar-streepjescodes.
* Code 128 streepjescodes.
* Code 39 streepjescodes.
* EAN-13-streepjescodes.
* EAN-8 streepjescodes.

Invoer van tekensets als hexadecimale invoer in de decode-API houdt in dat de inhoud van de streepjescode wordt gecodeerd als een hexadecimale tekenreeks. Als UTF-8 bijvoorbeeld is opgegeven als tekencodering in het formulier en Hex is opgegeven in de decoderingsbewerking, wordt de inhoud van de streepjescode gecodeerd als een hexadecimale tekenreeks in het element &lt; `xb:content`> in de gedecodeerde uitvoer. U kunt deze hexadecimale waarde omzetten om de oorspronkelijke inhoud op te halen door toepassingslogica in uw cliënttoepassing te creëren.

**zet de gegevens in een gegevensbron van XML** om

Nadat u formuliergegevens hebt gedecodeerd, kunt u deze converteren naar XDP- of XFDF-gegevens. Stel bijvoorbeeld dat u de gegevens in een ander formulier wilt importeren. Als u de gegevens wilt importeren in een XFA-formulier, moet u de gegevens converteren naar XDP-gegevens. Voor informatie, zie [ het Invoeren van de Gegevens van de Vorm ](/help/forms/developing/importing-exporting-data.md#importing-form-data).

**Proces de gedecodeerde gegevens**

U kunt de omgezette gegevens verwerken om aan uw bedrijfsvereisten te voldoen. Nadat u de gegevens hebt gedecodeerd en geconverteerd, kunt u deze bijvoorbeeld opslaan in een bestand, opslaan in een ondernemingsdatabase, een ander formulier invullen, enzovoort. In deze sectie wordt besproken hoe de geconverteerde gegevens als een XML-bestand moeten worden opgeslagen.

>[!NOTE]
>
>De service voor gecodeerde formulieren decodeert geen streepjescodegegevens als het regelscheidingsteken en het veldscheidingsteken dezelfde waarde hebben

**zie ook**

[Gecodeerde formuliergegevens decoderen met de Java API](barcoded-forms.md#decode-barcoded-form-data-using-the-java-api)

[Gecodeerde formuliergegevens decoderen met de webservice-API](barcoded-forms.md#decode-barcoded-form-data-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Gecodeerde formuliergegevens decoderen met de Java API {#decode-barcoded-form-data-using-the-java-api}

Formuliergegevens decoderen met de API voor streepjescodes (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden op in het klassenpad van uw Java-project.

1. Een gestreepte API-object voor formulieren maken

   Maak een `BarcodedFormsServiceClient` -object door de constructor ervan te gebruiken en een `ServiceClientFactory` -object door te geven dat verbindingseigenschappen bevat.

1. Een PDF-formulier ophalen dat gecodeerde gegevens bevat

   * Maak een `java.io.FileInputStream` -object dat het PDF-formulier vertegenwoordigt dat gecodeerde gegevens bevat, door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het PDF-document opgeeft.
   * Maak een `com.adobe.idp.Document` -object door de constructor ervan te gebruiken en het `java.io.FileInputStream` -object door te geven.

1. De gegevens decoderen uit het PDF-formulier

   Decodeer de formuliergegevens door de methode `decode` van het object `BarcodedFormsServiceClient` aan te roepen en de volgende waarden door te geven:

   * Het `com.adobe.idp.Document` -object dat het PDF-formulier bevat.
   * Een `java.lang.Boolean` -object dat opgeeft of een PDF417-streepjescode moet worden gedecodeerd.
   * Een `java.lang.Boolean` -object dat opgeeft of een streepjescode voor een gegevensmatrix moet worden gedecodeerd.
   * Een `java.lang.Boolean` -object dat opgeeft of een streepjescode voor QR-code moet worden gedecodeerd.
   * Een `java.lang.Boolean` -object dat opgeeft of een streepjescode van het type codabar moet worden gedecodeerd.
   * Een `java.lang.Boolean` -object dat opgeeft of een code 128-streepjescode moet worden gedecodeerd.
   * Een `java.lang.Boolean` -object dat opgeeft of een code 39-streepjescode moet worden gedecodeerd.
   * Een `java.lang.Boolean` -object dat opgeeft of een EAN-13-streepjescode moet worden gedecodeerd.
   * Een `java.lang.Boolean` -object dat opgeeft of een EAN-8-streepjescode moet worden gedecodeerd.
   * Een opsommingswaarde `com.adobe.livecycle.barcodedforms.CharSet` die de coderingswaarde voor de tekenset opgeeft die in de streepjescode wordt gebruikt.

   De methode `decode` retourneert een `org.w3c.dom.Document` -object dat gedecodeerde formuliergegevens bevat.

1. De gegevens converteren naar een XML-gegevensbron

   Zet de gedecodeerde gegevens om in XDP- of XFDF-gegevens door de methode `extractToXML` van het object `BarcodedFormsServiceClient` aan te roepen en de volgende waarden door te geven:

   * Het `org.w3c.dom.Document` -object dat gedecodeerde gegevens bevat (gebruik de geretourneerde waarde van de methode `decode` ).
   * Een opsommingswaarde `com.adobe.livecycle.barcodedforms.Delimiter` die het regelscheidingsteken opgeeft. Het wordt aanbevolen `Delimiter.Carriage_Return` op te geven.
   * Een opsommingswaarde `com.adobe.livecycle.barcodedforms.Delimiter` die het veldscheidingsteken opgeeft. Geef bijvoorbeeld `Delimiter.Tab` op.
   * Een opsommingswaarde `com.adobe.livecycle.barcodedforms.XMLFormat` die aangeeft of de streepjescodegegevens moeten worden omgezet in XDP- of XFDF XML-gegevens. Geef bijvoorbeeld `XMLFormat.XDP` op om de gegevens te converteren naar XDP-gegevens.

   >[!NOTE]
   >
   >Geef niet dezelfde waarden op voor de parameters voor regelscheidingsteken en veldscheidingsteken.

   De methode `extractToXML` retourneert een `java.util.List` -object waar elk element een `org.w3c.dom.Document` -object is. Er is een afzonderlijk element voor elke streepjescode die zich op het formulier bevindt. Als het formulier vier streepjescodes bevat, bevat het geretourneerde `java.util.List` -object vier elementen.

1. De gedecodeerde gegevens verwerken

   * Doorloop het `java.util.List` -object om elk `org.w3c.dom.Document` -object in de lijst op te halen.
   * Zet voor elk element in de lijst het object `org.w3c.dom.Document` om in een object `com.adobe.idp.Document` . (De toepassingslogica die een `org.w3c.dom.Document` -object omzet in een `com.adobe.idp.Document` -object, wordt weergegeven in de streepjescode-formuliergegevens decoderen met behulp van het Java API-voorbeeld).
   * Sla de XML-gegevens op als een XML-bestand door het object `com.adobe.idp.Document` `copyToFile` aan te roepen en een object File door te geven dat het XML-bestand vertegenwoordigt.

**zie ook**

[Snel starten (SOAP modus): gecodeerde formuliergegevens decoderen met de Java API](/help/forms/developing/barcoded-forms-service-java-api.md#quick-start-soap-mode-decoding-barcoded-form-data-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Gecodeerde formuliergegevens decoderen met de webservice-API {#decode-barcoded-form-data-using-the-web-service-api}

Formuliergegevens decoderen met de API voor gecodeerde formulieren (webservice):

1. Projectbestanden opnemen

   * Creeer een de cliëntassemblage van Microsoft .NET die de streepjescoded dienst WSDL gebruikt. Voor informatie, zie [ het Aanhalen van AEM Forms gebruikend het coderen Base64 ](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).
   * Verwijs naar de Microsoft .NET cliëntassemblage. Voor informatie, zie &quot;Verwijzen van de .NET cliëntassemblage&quot;in [ het Aanhalen van AEM Forms gebruikend Base64 het coderen ](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).

1. Een gestreepte API-object voor formulieren maken

   Gebruikend de de cliëntassemblage van Microsoft .NET die de streepjescoded dienst WSDL gebruikt, creeer een `BarcodedFormsServiceService` voorwerp door zijn standaardaannemer aan te halen.

1. Een PDF-formulier ophalen dat gecodeerde gegevens bevat

   * Maak een `BLOB` -object met behulp van de constructor. Het `BLOB` -object wordt gebruikt om een PDF-document op te slaan dat een streepjescode bevat.
   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `Length` van het object `System.IO.FileStream` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het object `BLOB` door de eigenschap `binaryData` ervan toe te wijzen met de inhoud van de bytearray.

1. De gegevens decoderen uit het PDF-formulier

   Decodeer de formuliergegevens door de methode `decode` van het object `BarcodedFormsServiceService` aan te roepen en de volgende waarden door te geven:

   * Het `BLOB` -object dat het PDF-formulier bevat.
   * Een `Boolean` -object dat opgeeft of een PDF417-streepjescode moet worden gedecodeerd.
   * Een `Boolean` -object dat opgeeft of een streepjescode voor een gegevensmatrix moet worden gedecodeerd.
   * Een `Boolean` -object dat opgeeft of een streepjescode voor QR-code moet worden gedecodeerd.
   * Een `Boolean` -object dat opgeeft of een streepjescode van het type codabar moet worden gedecodeerd.
   * Een `Boolean` -object dat opgeeft of een code 128-streepjescode moet worden gedecodeerd.
   * Een `Bolean` -object dat opgeeft of een code 39-streepjescode moet worden gedecodeerd.
   * Een `Boolean` -object dat opgeeft of een EAN-13-streepjescode moet worden gedecodeerd.
   * Een `Boolean` -object dat opgeeft of een EAN-8-streepjescode moet worden gedecodeerd.
   * Een opsommingswaarde `CharSet` die de coderingswaarde voor de tekenset opgeeft die in de streepjescode wordt gebruikt.

   De methode `decode` retourneert een tekenreekswaarde die gedecodeerde formuliergegevens bevat.

1. De gegevens converteren naar een XML-gegevensbron

   Zet de gedecodeerde gegevens om in XDP- of XFDF-gegevens door de methode `extractToXML` van het object `BarcodedFormsServiceService` aan te roepen en de volgende waarden door te geven:

   * Een tekenreekswaarde die gedecodeerde gegevens bevat (gebruik de geretourneerde waarde van de methode `decode` ).
   * Een opsommingswaarde `Delimiter` die het regelscheidingsteken opgeeft. Het wordt aanbevolen `Delimiter.Carriage_Return` op te geven.
   * Een opsommingswaarde `Delimiter` die het veldscheidingsteken opgeeft. Geef bijvoorbeeld `Delimiter.Tab` op.
   * Een opsommingswaarde `XMLFormat` die aangeeft of de streepjescodegegevens moeten worden omgezet in XDP- of XFDF XML-gegevens. Geef bijvoorbeeld `XMLFormat.XDP` op om de gegevens te converteren naar XDP-gegevens.

   >[!NOTE]
   >
   >Geef niet dezelfde waarden op voor de parameters voor regelscheidingsteken en veldscheidingsteken.

   De methode `extractToXML` retourneert een `Object` -array waarbij elk element een `BLOB` -instantie is. Er is een afzonderlijk element voor elke streepjescode die zich op het formulier bevindt. Als er vier streepjescodes op het formulier staan, staan er vier elementen in de geretourneerde `Object` -array.

1. De gedecodeerde gegevens verwerken

   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het beveiligde PDF-document vertegenwoordigt.
   * Maak een bytearray waarin de gegevensinhoud wordt opgeslagen van het object `BLOB` dat door de methode `encryptPDFUsingPassword` is geretourneerd. Vul de bytearray met de waarde van het gegevenslid `binaryData` van het object `BLOB` .
   * Maak een `System.IO.BinaryWriter` -object door de constructor ervan aan te roepen en het `System.IO.FileStream` -object door te geven.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door de methode `Write` van het object `System.IO.BinaryWriter` aan te roepen en de bytearray door te geven.

**zie ook**

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
