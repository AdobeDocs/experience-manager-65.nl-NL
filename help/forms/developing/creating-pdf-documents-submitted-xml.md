---
title: PDF-documenten maken met verzonden XML-gegevens
seo-title: PDF-documenten maken met verzonden XML-gegevens
description: Gebruik de Forms-service om de formuliergegevens op te halen die de gebruiker in een interactief formulier heeft ingevoerd. Geef de formuliergegevens door aan een andere AEM Forms-servicebewerking en maak een PDF-document met de gegevens.
seo-description: Gebruik de Forms-service om de formuliergegevens op te halen die de gebruiker in een interactief formulier heeft ingevoerd. Geef de formuliergegevens door aan een andere AEM Forms-servicebewerking en maak een PDF-document met de gegevens.
uuid: 2676c614-8988-451b-ac7c-bd07731a3f5f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 62490230-a24e-419d-95bb-c0bb04a03f96
translation-type: tm+mt
source-git-commit: 9cf46a26d2aa2e41b924a4de89cf8ab5fdeeefc6
workflow-type: tm+mt
source-wordcount: '1361'
ht-degree: 0%

---


# PDF-documenten maken met verzonden XML-gegevens {#creating-pdf-documents-with-submittedxml-data}

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

## PDF-documenten maken met verzonden XML-gegevens {#creating-pdf-documents-with-submitted-xml-data}

Webtoepassingen waarmee gebruikers interactieve formulieren kunnen invullen, vereisen dat de gegevens worden teruggestuurd naar de server. Met de Forms-service kunt u de formuliergegevens ophalen die de gebruiker in een interactief formulier heeft ingevoerd. Vervolgens kunt u de formuliergegevens doorgeven aan een andere AEM Forms-servicebewerking en een PDF-document maken met behulp van de gegevens.

>[!NOTE]
>
>Voordat u deze inhoud leest, is het raadzaam dat u goed begrijpt hoe ingediende formulieren moeten worden verwerkt. Concepten zoals de relatie tussen een formulierontwerp en de verzonden XML-gegevens worden behandeld in de handling van verzonden Forms.

Overweeg de volgende workflow met drie AEM Forms-services:

* Een gebruiker verzendt XML-gegevens vanuit een webtoepassing naar de Forms-service.
* De Forms-service wordt gebruikt om het verzonden formulier te verwerken en formuliervelden te extraheren. Formuliergegevens kunnen worden verwerkt. De gegevens kunnen bijvoorbeeld naar een ondernemingsdatabase worden verzonden.
* Formuliergegevens worden naar de service Uitvoer verzonden om een niet-interactief PDF-document te maken.
* Het niet-interactieve PDF-document wordt opgeslagen in Content Services (afgekeurd).

Het volgende diagram biedt een visuele weergave van deze workflow.

![cd_cd_finsrv_architectuur_xml_pdf1](assets/cd_cd_finsrv_architecture_xml_pdf1.png)

Nadat de gebruiker het formulier vanuit de webbrowser van de client heeft verzonden, wordt het niet-interactieve PDF-document opgeslagen in Content Services (afgekeurd). In de volgende afbeelding ziet u een PDF-document dat is opgeslagen in Content Services (afgekeurd).

![cd_cd_cs_gui](assets/cd_cd_cs_gui.png)

### Overzicht van stappen {#summary-of-steps}

Als u een niet-interactief PDF-document wilt maken met verzonden XML-gegevens en wilt opslaan in het PDF-document in Content Services (afgekeurd), voert u de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak Forms-, Output- en Document Management-objecten.
1. Haal formuliergegevens op met de Forms-service.
1. Maak een niet-interactief PDF-document met de uitvoerservice.
1. Sla het PDF-formulier op in Inhoudsservices (afgekeurd) met behulp van de Document Management-service.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**Forms-, Output- en Document Management-objecten maken**

Voordat u een API-bewerking voor Forms-services programmatisch kunt uitvoeren, maakt u een Forms Client API-object. Op dezelfde manier kunt u zowel een Output Client API-object als een Document Management Client API-object maken, omdat bij deze workflow de services voor Output en documentbeheer worden aangeroepen.

**Formuliergegevens ophalen met de Forms-service**

Haal formuliergegevens op die zijn verzonden naar de Forms-service. U kunt verzonden gegevens verwerken om aan uw bedrijfsvereisten te voldoen. U kunt bijvoorbeeld formuliergegevens opslaan in een ondernemingsdatabase. Als u echter een niet-interactief PDF-document wilt maken, worden de formuliergegevens doorgegeven aan de uitvoerservice.

**Maak een niet-interactief PDF-document met de uitvoerservice.**

Met de service Uitvoer kunt u een niet-interactief PDF-document maken dat is gebaseerd op een formulierontwerp en XML-formuliergegevens. In de workflow worden de formuliergegevens opgehaald uit de Forms-service.

**Sla het PDF-formulier op in Inhoudsservices (afgekeurd) met behulp van de Document Management-service**

Gebruik de service-API voor documentbeheer om een PDF-document op te slaan in Content Services (afgekeurd).

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Forms Service API Quick Start](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

### Een PDF-document maken met verzonden XML-gegevens met de Java API {#create-a-pdf-document-with-submitted-xml-data-using-the-java-api}

Maak een PDF-document met verzonden XML-gegevens met de API voor Forms, Output en Documentbeheer (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden op, zoals adobe-forms-client.jar, adobe-output-client.jar en adobe-contentservices-client.jar in het klassenpad van uw Java-project.

1. Forms-, Output- en Document Management-objecten maken

   * Maak een `ServiceClientFactory`-object dat verbindingseigenschappen bevat.
   * Maak een `FormsServiceClient`-object door de constructor ervan te gebruiken en het object `ServiceClientFactory` door te geven.
   * Maak een `OutputClient`-object door de constructor ervan te gebruiken en het object `ServiceClientFactory` door te geven.
   * Maak een `DocumentManagementServiceClientImpl`-object door de constructor ervan te gebruiken en het object `ServiceClientFactory` door te geven.

1. Formuliergegevens ophalen met de Forms-service

   * Roep de methode `processFormSubmission` van het object `FormsServiceClient` aan en geef de volgende waarden door:

      * Het object `com.adobe.idp.Document` dat de formuliergegevens bevat.
      * Een tekenreekswaarde die omgevingsvariabelen opgeeft, inclusief alle relevante HTTP-headers. Geef het inhoudstype op dat moet worden afgehandeld door een of meer waarden op te geven voor de omgevingsvariabele `CONTENT_TYPE`. Als u bijvoorbeeld XML-gegevens wilt verwerken, geeft u de volgende tekenreekswaarde op voor deze parameter: `CONTENT_TYPE=text/xml`.
      * Een tekenreekswaarde die de koptekstwaarde `HTTP_USER_AGENT` opgeeft, zoals `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
      * Een `RenderOptionsSpec`-object dat uitvoeringsopties opslaat.

      De methode `processFormSubmission` retourneert een `FormsResult`-object dat de resultaten van het verzenden van het formulier bevat.

   * Bepaal of de Forms-service de formuliergegevens heeft verwerkt door de methode `getAction` van het object `FormsResult` aan te roepen. Als deze methode de waarde `0` retourneert, zijn de gegevens klaar om te worden verwerkt.
   * Haal formuliergegevens op door een `com.adobe.idp.Document`-object te maken door de methode `getOutputContent` van het object aan te roepen. `FormsResult` (Dit object bevat formuliergegevens die naar de service Uitvoer kunnen worden verzonden.)
   * Maak een `java.io.InputStream`-object door de constructor `java.io.DataInputStream` aan te roepen en het object `com.adobe.idp.Document` door te geven.
   * Maak een `org.w3c.dom.DocumentBuilderFactory`-object door de methode `newInstance` van het statische object aan te roepen.`org.w3c.dom.DocumentBuilderFactory`
   * Maak een `org.w3c.dom.DocumentBuilder`-object door de methode `newDocumentBuilder` van het object `org.w3c.dom.DocumentBuilderFactory` aan te roepen.
   * Maak een `org.w3c.dom.Document`-object door de methode `parse` van het object `org.w3c.dom.DocumentBuilder` aan te roepen en het object `java.io.InputStream` door te geven.
   * Hiermee wordt de waarde van elk knooppunt in het XML-document opgehaald. U kunt deze taak uitvoeren door een aangepaste methode te maken die twee parameters accepteert: het object `org.w3c.dom.Document` en de naam van het knooppunt waarvan u de waarde wilt ophalen. Deze methode retourneert een tekenreekswaarde die de waarde van het knooppunt vertegenwoordigt. In het codevoorbeeld dat dit proces volgt, wordt deze douanemethode genoemd `getNodeText`. De hoofdtekst van deze methode wordt weergegeven.


1. Maak een niet-interactief PDF-document met de uitvoerservice.

   Maak een PDF-document door de methode `generatePDFOutput` van het object `OutputClient` aan te roepen en de volgende waarden door te geven:

   * A `TransformationFormat` enum value. Als u een PDF-document wilt genereren, geeft u `TransformationFormat.PDF` op.
   * Een tekenreekswaarde waarmee de naam van het formulierontwerp wordt opgegeven. Zorg ervoor dat het formulierontwerp compatibel is met de formuliergegevens die zijn opgehaald van de Forms-service.
   * Een tekenreekswaarde die de hoofdmap van de inhoud opgeeft waar het formulierontwerp zich bevindt.
   * Een `PDFOutputOptionsSpec`-object dat PDF-runtime-opties bevat.
   * Een `RenderOptionsSpec`-object dat renderingopties bevat.
   * Het object `com.adobe.idp.Document` dat de XML-gegevensbron bevat die gegevens bevat die met het formulierontwerp moeten worden samengevoegd. Zorg ervoor dat dit object is geretourneerd door de methode `getOutputContent` van het object.`FormsResult`
   * De methode `generatePDFOutput` retourneert een `OutputResult`-object dat de resultaten van de bewerking bevat.
   * Haal het niet-interactieve PDF-document op door de methode `OutputResult` van het object `getGeneratedDoc` aan te roepen. Deze methode retourneert een `com.adobe.idp.Document`-instantie die het niet-interactieve PDF-document vertegenwoordigt.

1. Het PDF-formulier opslaan in Content Services (afgekeurd) met behulp van de Document Management-service

   Voeg de inhoud toe door de methode `DocumentManagementServiceClientImpl` van het object `storeContent` aan te roepen en de volgende waarden door te geven:

   * Een tekenreekswaarde die de opslaglocatie opgeeft waar de inhoud wordt toegevoegd. De standaardopslag is `SpacesStore`. Deze waarde is een verplichte parameter.
   * Een tekenreekswaarde die het volledig gekwalificeerde pad opgeeft van de ruimte waar de inhoud wordt toegevoegd (bijvoorbeeld `/Company Home/Test Directory`). Deze waarde is een verplichte parameter.
   * De knooppuntnaam die de nieuwe inhoud vertegenwoordigt (bijvoorbeeld `MortgageForm.pdf`). Deze waarde is een verplichte parameter.
   * Een tekenreekswaarde die het type knooppunt opgeeft. Als u nieuwe inhoud wilt toevoegen, zoals een PDF-bestand, geeft u `{https://www.alfresco.org/model/content/1.0}content` op. Deze waarde is een verplichte parameter.
   * Een `com.adobe.idp.Document`-object dat de inhoud vertegenwoordigt. Deze waarde is een verplichte parameter.
   * Een tekenreekswaarde die de coderingswaarde opgeeft (bijvoorbeeld `UTF-8`). Deze waarde is een verplichte parameter.
   * Een `UpdateVersionType` opsommingswaarde die aangeeft hoe versiegegevens moeten worden verwerkt (bijvoorbeeld `UpdateVersionType.INCREMENT_MAJOR_VERSION` om de inhoudsversie te verhogen. ) Deze waarde is een verplichte parameter.
   * Een `java.util.List`-instantie die aspecten met betrekking tot de inhoud opgeeft. Deze waarde is een optionele parameter en u kunt `null` specificeren.
   * Een `java.util.Map`-object dat inhoudskenmerken opslaat.

   De methode `storeContent` retourneert een `CRCResult`-object dat de inhoud beschrijft. Met behulp van een `CRCResult`-object kunt u bijvoorbeeld de unieke id-waarde van de inhoud ophalen. Als u deze taak wilt uitvoeren, roept u de methode `getNodeUuid` van het object `CRCResult` aan.

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)
