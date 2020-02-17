---
title: PDF-documenten maken met verzonden XML-gegevens
seo-title: PDF-documenten maken met verzonden XML-gegevens
description: 'null'
seo-description: 'null'
uuid: 2676c614-8988-451b-ac7c-bd07731a3f5f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 62490230-a24e-419d-95bb-c0bb04a03f96
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# PDF-documenten maken met verzonden XML-gegevens {#creating-pdf-documents-with-submittedxml-data}

## PDF-documenten maken met verzonden XML-gegevens {#creating-pdf-documents-with-submitted-xml-data}

Webtoepassingen waarmee gebruikers interactieve formulieren kunnen invullen, vereisen dat de gegevens worden teruggestuurd naar de server. Met de Forms-service kunt u de formuliergegevens ophalen die de gebruiker in een interactief formulier heeft ingevoerd. Vervolgens kunt u de formuliergegevens doorgeven aan een andere AEM Forms-servicebewerking en een PDF-document maken met behulp van de gegevens.

>[!NOTE]
>
>Voordat u deze inhoud leest, is het raadzaam dat u goed begrijpt hoe ingediende formulieren moeten worden verwerkt. Concepten zoals de relatie tussen een formulierontwerp en verzonden XML-gegevens worden behandeld in Ingediende formulieren verwerken.

Overweeg de volgende workflow met drie services van AEM Forms:

* Een gebruiker verzendt XML-gegevens vanuit een webtoepassing naar de service Forms.
* De service Forms wordt gebruikt om het verzonden formulier te verwerken en formuliervelden te extraheren. Formuliergegevens kunnen worden verwerkt. De gegevens kunnen bijvoorbeeld naar een ondernemingsdatabase worden verzonden.
* Formuliergegevens worden naar de service Uitvoer verzonden om een niet-interactief PDF-document te maken.
* Het niet-interactieve PDF-document wordt opgeslagen in Content Services (afgekeurd).

Het volgende diagram biedt een visuele weergave van deze workflow.

![cd_cd_finsrv_architectuur_xml_pdf1](assets/cd_cd_finsrv_architecture_xml_pdf1.png)

Nadat de gebruiker het formulier vanuit de webbrowser van de client heeft verzonden, wordt het niet-interactieve PDF-document opgeslagen in Content Services (afgekeurd). In de volgende afbeelding ziet u een PDF-document dat is opgeslagen in Content Services (afgekeurd).

![cd_cd_cs_gui](assets/cd_cd_cs_gui.png)

### Overzicht van de stappen {#summary-of-steps}

Als u een niet-interactief PDF-document wilt maken met verzonden XML-gegevens en wilt opslaan in het PDF-document in Content Services (afgekeurd), voert u de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak objecten Formulieren, Uitvoer en Documentbeheer.
1. Haal formuliergegevens op met de service Forms.
1. Maak een niet-interactief PDF-document met de uitvoerservice.
1. Sla het PDF-formulier op in Inhoudsservices (afgekeurd) met behulp van de Document Management-service.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**Formulieren, uitvoer en Document Management-objecten maken**

Voordat u een API-bewerking voor Forms-service programmatisch kunt uitvoeren, maakt u een API-object voor Forms Client. Op dezelfde manier kunt u zowel een Output Client API-object als een Document Management Client API-object maken, omdat bij deze workflow de services voor Output en documentbeheer worden aangeroepen.

**Formuliergegevens ophalen met de service Forms**

Haal formuliergegevens op die naar de service Forms zijn verzonden. U kunt verzonden gegevens verwerken om aan uw bedrijfsvereisten te voldoen. U kunt bijvoorbeeld formuliergegevens opslaan in een ondernemingsdatabase. Als u echter een niet-interactief PDF-document wilt maken, worden de formuliergegevens doorgegeven aan de uitvoerservice.

**Maak een niet-interactief PDF-document met de uitvoerservice.**

Met de service Uitvoer kunt u een niet-interactief PDF-document maken dat is gebaseerd op een formulierontwerp en XML-formuliergegevens. In de workflow worden de formuliergegevens opgehaald uit de service Forms.

**Sla het PDF-formulier op in Inhoudsservices (afgekeurd) met behulp van de Document Management-service**

Gebruik de service-API voor documentbeheer om een PDF-document op te slaan in Content Services (afgekeurd).

**Zie ook**

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Forms Service API, snel aan de slag](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

### Een PDF-document maken met verzonden XML-gegevens met de Java API {#create-a-pdf-document-with-submitted-xml-data-using-the-java-api}

Maak een PDF-document met verzonden XML-gegevens met behulp van de API voor formulieren, uitvoer en documentbeheer (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden op, zoals adobe-forms-client.jar, adobe-output-client.jar en adobe-contentservices-client.jar in het klassenpad van uw Java-project.

1. Formulieren, uitvoer en Document Management-objecten maken

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `FormsServiceClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.
   * Maak een `OutputClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.
   * Maak een `DocumentManagementServiceClientImpl` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Formuliergegevens ophalen met de service Forms

   * Roep de methode van het `FormsServiceClient` `processFormSubmission` object aan en geef de volgende waarden door:

      * Het `com.adobe.idp.Document` object dat de formuliergegevens bevat.
      * Een tekenreekswaarde die omgevingsvariabelen opgeeft, inclusief alle relevante HTTP-headers. Geef het inhoudstype op dat moet worden afgehandeld door een of meer waarden voor de `CONTENT_TYPE` omgevingsvariabele op te geven. Als u bijvoorbeeld XML-gegevens wilt verwerken, geeft u de volgende tekenreekswaarde op voor deze parameter: `CONTENT_TYPE=text/xml`.
      * Een tekenreekswaarde die de `HTTP_USER_AGENT` koptekstwaarde opgeeft, zoals `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
      * Een `RenderOptionsSpec` object dat uitvoeringsopties opslaat.
      De `processFormSubmission` methode retourneert een `FormsResult` object dat de resultaten van het verzenden van het formulier bevat.

   * Bepaal of de service Forms klaar is met het verwerken van de formuliergegevens door de `FormsResult` `getAction` methode van het object aan te roepen. Als deze methode de waarde retourneert `0`, kunnen de gegevens worden verwerkt.
   * Haal formuliergegevens op door een `com.adobe.idp.Document` object te maken door de `FormsResult` methode van het `getOutputContent` object aan te roepen. (Dit object bevat formuliergegevens die naar de service Uitvoer kunnen worden verzonden.)
   * Maak een `java.io.InputStream` object door de `java.io.DataInputStream` constructor aan te roepen en het `com.adobe.idp.Document` object door te geven.
   * Maak een `org.w3c.dom.DocumentBuilderFactory` object door de `org.w3c.dom.DocumentBuilderFactory` methode van het statische `newInstance` object aan te roepen.
   * Maak een `org.w3c.dom.DocumentBuilder` object door de `org.w3c.dom.DocumentBuilderFactory` methode van het `newDocumentBuilder` object aan te roepen.
   * Maak een `org.w3c.dom.Document` object door de methode van het `org.w3c.dom.DocumentBuilder` object aan te roepen `parse` en het `java.io.InputStream` object door te geven.
   * Hiermee wordt de waarde van elk knooppunt in het XML-document opgehaald. U kunt deze taak uitvoeren door een aangepaste methode te maken die twee parameters accepteert: het `org.w3c.dom.Document` object en de naam van het knooppunt waarvan u de waarde wilt ophalen. Deze methode retourneert een tekenreekswaarde die de waarde van het knooppunt vertegenwoordigt. In het codevoorbeeld dat dit proces volgt, wordt deze douanemethode geroepen `getNodeText`. De hoofdtekst van deze methode wordt weergegeven.


1. Maak een niet-interactief PDF-document met de uitvoerservice.

   Maak een PDF-document door de methode van het `OutputClient` `generatePDFOutput` object aan te roepen en de volgende waarden door te geven:

   * Een `TransformationFormat` opsommingswaarde. Geef op om een PDF-document te genereren. `TransformationFormat.PDF`
   * Een tekenreekswaarde waarmee de naam van het formulierontwerp wordt opgegeven. Zorg ervoor dat het formulierontwerp compatibel is met de formuliergegevens die zijn opgehaald uit de service Forms.
   * Een tekenreekswaarde die de hoofdmap van de inhoud opgeeft waar het formulierontwerp zich bevindt.
   * Een `PDFOutputOptionsSpec` object dat PDF-runtime-opties bevat.
   * Een `RenderOptionsSpec` object dat renderingopties bevat.
   * Het `com.adobe.idp.Document` object dat de XML-gegevensbron bevat die gegevens bevat die met het formulierontwerp moeten worden samengevoegd. Controleer of dit object is geretourneerd door de `FormsResult` methode van het `getOutputContent` object.
   * De `generatePDFOutput` methode retourneert een `OutputResult` object dat de resultaten van de bewerking bevat.
   * Haal het niet-interactieve PDF-document op door de `OutputResult` methode van het `getGeneratedDoc` object aan te roepen. Deze methode retourneert een `com.adobe.idp.Document` instantie die het niet-interactieve PDF-document vertegenwoordigt.

1. Het PDF-formulier opslaan in Content Services (afgekeurd) met behulp van de Document Management-service

   Voeg de inhoud toe door de methode van het `DocumentManagementServiceClientImpl` `storeContent` object aan te roepen en de volgende waarden door te geven:

   * Een tekenreekswaarde die de opslaglocatie opgeeft waar de inhoud wordt toegevoegd. De standaardopslag is `SpacesStore`. Deze waarde is een verplichte parameter.
   * Een tekenreekswaarde die het volledig gekwalificeerde pad opgeeft van de ruimte waar de inhoud wordt toegevoegd (bijvoorbeeld `/Company Home/Test Directory`). Deze waarde is een verplichte parameter.
   * De knooppuntnaam die de nieuwe inhoud vertegenwoordigt (bijvoorbeeld, `MortgageForm.pdf`). Deze waarde is een verplichte parameter.
   * Een tekenreekswaarde die het type knooppunt opgeeft. Geef op om nieuwe inhoud toe te voegen, zoals een PDF-bestand `{https://www.alfresco.org/model/content/1.0}content`. Deze waarde is een verplichte parameter.
   * Een `com.adobe.idp.Document` object dat de inhoud vertegenwoordigt. Deze waarde is een verplichte parameter.
   * Een tekenreekswaarde die de coderingswaarde opgeeft (bijvoorbeeld `UTF-8`). Deze waarde is een verplichte parameter.
   * Een `UpdateVersionType` opsommingswaarde die aangeeft hoe versiegegevens moeten worden verwerkt (bijvoorbeeld `UpdateVersionType.INCREMENT_MAJOR_VERSION` om de versie van de inhoud te verhogen). ) Deze waarde is een verplichte parameter.
   * Een `java.util.List` instantie die aspecten met betrekking tot de inhoud opgeeft. Deze waarde is een optionele parameter en u kunt deze opgeven `null`.
   * Een `java.util.Map` object dat inhoudskenmerken opslaat.
   De `storeContent` methode retourneert een `CRCResult` object dat de inhoud beschrijft. Met behulp van een `CRCResult` object kunt u bijvoorbeeld de unieke id-waarde van de inhoud verkrijgen. Als u deze taak wilt uitvoeren, roept u de `CRCResult` methode van het `getNodeUuid` object aan.

**Zie ook**

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)
