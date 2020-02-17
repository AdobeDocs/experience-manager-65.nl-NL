---
title: Documenten doorgeven aan FormsService
seo-title: Documenten doorgeven aan FormsService
description: 'null'
seo-description: 'null'
uuid: 841e97f3-ebb8-4340-81a9-b6db11f0ec82
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: e23de3c3-f8a0-459f-801e-a0942fb1c6aa
translation-type: tm+mt
source-git-commit: 7cbe3e94eddb81925072f68388649befbb027e6d

---


# Documenten doorgeven aan de Forms Service {#passing-documents-to-the-formsservice}

Met de AEM Forms-service worden interactieve PDF-formulieren weergegeven op clientapparaten, meestal webbrowsers, om informatie van gebruikers te verzamelen. Een interactief PDF-formulier is gebaseerd op een formulierontwerp dat gewoonlijk als een XDP-bestand wordt opgeslagen en in Designer wordt gemaakt. Vanaf AEM Forms kunt u een `com.adobe.idp.Document` object met het formulierontwerp doorgeven aan de service Forms. De service Forms geeft vervolgens het formulierontwerp weer dat zich in het `com.adobe.idp.Document` object bevindt.

Een voordeel van het doorgeven van een `com.adobe.idp.Document` object aan de service Forms is dat andere servicebewerkingen een `com.adobe.idp.Document` instantie retourneren. Dat wil zeggen dat u een `com.adobe.idp.Document` instantie van een andere servicebewerking kunt ophalen en renderen. Stel bijvoorbeeld dat een XDP-bestand wordt opgeslagen in een knooppunt Content Services (afgekeurd) met de naam `/Company Home/Form Designs`, zoals in de volgende afbeelding wordt getoond.

U kunt Loan.xdp programmatically terugwinnen van (afgekeurd) (van de Diensten van de Inhoud) en het XDP dossier tot de dienst van Vormen binnen een `com.adobe.idp.Document` voorwerp overgaan.

>[!NOTE]
>
>Voor meer informatie over de dienst van Vormen, zie de Verwijzing van de [Diensten voor Vormen](https://www.adobe.com/go/learn_aemforms_services_63)AEM.

## Overzicht van de stappen {#summary-of-steps}

Als u een document dat is verkregen van Content Services (afgekeurd) (afgekeurd) wilt doorgeven aan de service Forms, voert u de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak een Forms en een Document Management Client API-object.
1. Haal het formulierontwerp op bij Inhoudsservices (afgekeurd).
1. Het interactieve PDF-formulier renderen.
1. Voer een handeling uit met de gegevensstroom van het formulier.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, neemt u de proxybestanden op.

**Een Forms en een Document Management Client API-object maken**

Voordat u een API-bewerking voor Forms-service programmatisch kunt uitvoeren, maakt u een API-object voor Forms Client. Omdat met deze workflow een XDP-bestand wordt opgehaald van Content Services (afgekeurd), maakt u ook een Document Management API-object.

**Het formulierontwerp ophalen van Content Services (afgekeurd)**

Haal het XDP-bestand op van Content Services (afgekeurd) met behulp van de Java- of webservice-API. Het XDP-bestand wordt geretourneerd binnen een `com.adobe.idp.Document` instantie (of een `BLOB` instantie als u webservices gebruikt). U kunt het `com.adobe.idp.Document` exemplaar dan aan de dienst van Vormen overgaan.

**Een interactief PDF-formulier renderen**

Als u een interactief formulier wilt genereren, geeft u het exemplaar dat door Content Services (afgekeurd) is geretourneerd, door aan de service Forms. `com.adobe.idp.Document`

>[!NOTE]
>
>U kunt een formulier met het formulierontwerp doorgeven aan de service Forms. `com.adobe.idp.Document` Twee nieuwe methoden noemen `renderPDFForm2` en `renderHTMLForm2` accepteren een `com.adobe.idp.Document` object dat een formulierontwerp bevat.

**Een handeling uitvoeren met de gegevensstroom van het formulier**

Afhankelijk van het type clienttoepassing kunt u het formulier naar een clientwebbrowser schrijven of het formulier opslaan als een PDF-bestand. Een webtoepassing schrijft het formulier doorgaans naar een webbrowser. Een bureaubladtoepassing slaat het formulier echter doorgaans op als een PDF-bestand.

**Zie ook**

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Forms Service API, snel aan de slag](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

## Documenten doorgeven aan de Forms Service met de Java API {#pass-documents-to-the-forms-service-using-the-java-api}

Geef een document dat is verkregen van Content Services (afgekeurd) door gebruik te maken van de Forms service en Content Services (afgekeurd) API (Java):

1. Projectbestanden opnemen

   Neem JAR-bestanden voor clients, zoals adobe-forms-client.jar en adobe-contentservices-client.jar, op in het klassenpad van uw Java-project.

1. Een Forms en een Document Management Client API-object maken

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat. (Zie Verbindingseigenschappen [instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Maak een `FormsServiceClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.
   * Maak een `DocumentManagementServiceClientImpl` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Het formulierontwerp ophalen van Content Services (afgekeurd)

   Roep de methode van het `DocumentManagementServiceClientImpl` `retrieveContent` object aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de opslaglocatie opgeeft waar de inhoud wordt toegevoegd. De standaardopslag is `SpacesStore`. Deze waarde is een verplichte parameter.
   * Een tekenreekswaarde die het volledig gekwalificeerde pad opgeeft van de inhoud die moet worden opgehaald (bijvoorbeeld `/Company Home/Form Designs/Loan.xdp`). Deze waarde is een verplichte parameter.
   * Een tekenreekswaarde die de versie opgeeft. Deze waarde is een optionele parameter en u kunt een lege tekenreeks doorgeven. In dit geval wordt de laatste versie opgehaald.
   De `retrieveContent` methode retourneert een `CRCResult` object dat het XDP-bestand bevat. Haal een `com.adobe.idp.Document` instantie op door de `CRCResult` methode van het `getDocument` object aan te roepen.

1. Een interactief PDF-formulier renderen

   Roep de methode van het `FormsServiceClient` `renderPDFForm2` object aan en geef de volgende waarden door:

   * Een `com.adobe.idp.Document` object dat het formulierontwerp bevat dat is opgehaald uit Content Services (afgekeurd).
   * Een `com.adobe.idp.Document` object dat gegevens bevat die met het formulier moeten worden samengevoegd. Geef een leeg `com.adobe.idp.Document` object door als u geen gegevens wilt samenvoegen.
   * Een `PDFFormRenderSpec` object dat uitvoeringsopties opslaat. Deze waarde is een optionele parameter en u kunt opgeven `null` of u geen runtime-opties wilt opgeven.
   * Een `URLSpec` object dat URI-waarden bevat. Deze waarde is een optionele parameter en u kunt deze opgeven `null`.
   * Een `java.util.HashMap` object dat bestandsbijlagen opslaat. Deze waarde is een optionele parameter en u kunt opgeven `null` of u geen bestanden aan het formulier wilt koppelen.
   De `renderPDFForm` methode retourneert een `FormsResult` object dat een formuliergegevensstroom bevat die naar de webbrowser van de client moet worden geschreven.

1. Een handeling uitvoeren met de gegevensstroom van het formulier

   * Maak een `com.adobe.idp.Document` object door de `FormsResult` methode van het `getOutputContent` object aan te roepen.
   * Haal het inhoudstype van het `com.adobe.idp.Document` object op door de `getContentType` methode ervan aan te roepen.
   * Stel het inhoudstype van het `javax.servlet.http.HttpServletResponse` object in door de bijbehorende `setContentType` methode op te roepen en het inhoudstype van het `com.adobe.idp.Document` object door te geven.
   * Maak een `javax.servlet.ServletOutputStream` object dat wordt gebruikt om de gegevensstroom van het formulier naar de webbrowser van de client te schrijven door de `javax.servlet.http.HttpServletResponse` methode van het `getOutputStream` object aan te roepen.
   * Maak een `java.io.InputStream` object door de `com.adobe.idp.Document` methode van het `getInputStream` object aan te roepen.
   * Maak een bytearray en vul deze met de formuliergegevensstroom door de `InputStream` `read` methode van het object aan te roepen. Geef de bytearray door als een argument.
   * Roep de `javax.servlet.ServletOutputStream` methode van het `write` object aan om de formuliergegevensstroom naar de webbrowser van de client te verzenden. Geef de bytearray door aan de `write` methode.

**Zie ook**

[Snel starten (SOAP-modus): Documenten doorgeven aan de Forms Service met de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-passing-documents-to-the-forms-service-using-the-java-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Documenten doorgeven aan de Forms Service met behulp van de webservice-API {#pass-documents-to-the-forms-service-using-the-web-service-api}

Geef een document dat is verkregen van Content Services (afgekeurd) door gebruik te maken van de Forms service en Content Services (afgekeurd) API (webservice):

1. Projectbestanden opnemen

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Omdat deze cliënttoepassing de twee diensten van Vormen AEM aanhaalt, creeer twee de dienstverwijzingen. Gebruik de volgende definitie van WSDL voor de de dienstverwijzing verbonden aan de dienst van Vormen: `http://localhost:8080/soap/services/FormsService?WSDL&lc_version=9.0.1`.

   Gebruik de volgende definitie WSDL voor de de dienstverwijzing verbonden aan de dienst van het Beheer van het Document: `http://localhost:8080/soap/services/DocumentManagementService?WSDL&lc_version=9.0.1`.

   Omdat het `BLOB` gegevenstype gemeenschappelijk voor beide de dienstverwijzingen is, kwalificeer volledig het `BLOB` gegevenstype wanneer het gebruiken van het. In de overeenkomstige webservice quick start zijn alle `BLOB` instanties volledig gekwalificeerd.

   >[!NOTE]
   >
   >Vervangen `localhost`door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Een Forms en een Document Management Client API-object maken

   * Maak een `FormsServiceClient` object met de standaardconstructor.
   * Maak een `FormsServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde door die de WSDL opgeeft voor de service AEM Forms (bijvoorbeeld `http://localhost:8080/soap/services/FormsService?WSDL`). U hoeft het `lc_version` kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `FormsServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het veld `FormsServiceClient.ClientCredentials.UserName.UserName`.
      * Wijs de bijbehorende wachtwoordwaarde aan het veld toe `FormsServiceClient.ClientCredentials.UserName.Password`.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode`.
   >[!NOTE]
   >
   >Herhaal deze stappen voor de `DocumentManagementServiceClient`dienstcliënt.

1. Het formulierontwerp ophalen van Content Services (afgekeurd)

   Haal inhoud op door de methode van het `DocumentManagementServiceClient` object aan te roepen `retrieveContent` en de volgende waarden door te geven:

   * Een tekenreekswaarde die de opslaglocatie opgeeft waar de inhoud wordt toegevoegd. De standaardopslag is `SpacesStore`. Deze waarde is een verplichte parameter.
   * Een tekenreekswaarde die het volledig gekwalificeerde pad opgeeft van de inhoud die moet worden opgehaald (bijvoorbeeld `/Company Home/Form Designs/Loan.xdp`). Deze waarde is een verplichte parameter.
   * Een tekenreekswaarde die de versie opgeeft. Deze waarde is een optionele parameter en u kunt een lege tekenreeks doorgeven. In dit geval wordt de laatste versie opgehaald.
   * Een parameter van de koordoutput die doorbladert verbindingswaarde opslaat.
   * Een `BLOB` uitvoerparameter die de inhoud opslaat. U kunt deze uitvoerparameter gebruiken om de inhoud op te halen.
   * Een `ServiceReference1.MyMapOf_xsd_string_To_xsd_anyType` uitvoerparameter die inhoudskenmerken opslaat.
   * Een `CRCResult` uitvoerparameter. In plaats van dit object te gebruiken, kunt u de `BLOB` uitvoerparameter gebruiken om de inhoud op te halen.

1. Een interactief PDF-formulier renderen

   Roep de methode van het `FormsServiceClient` `renderPDFForm2` object aan en geef de volgende waarden door:

   * Een `BLOB` object dat het formulierontwerp bevat dat is opgehaald uit Content Services (afgekeurd).
   * Een `BLOB` object dat gegevens bevat die met het formulier moeten worden samengevoegd. Geef een leeg `BLOB` object door als u geen gegevens wilt samenvoegen.
   * Een `PDFFormRenderSpec` object dat uitvoeringsopties opslaat. Deze waarde is een optionele parameter en u kunt opgeven `null` of u geen runtime-opties wilt opgeven.
   * Een `URLSpec` object dat URI-waarden bevat. Deze waarde is een optionele parameter en u kunt deze opgeven `null`.
   * Een `Map` object dat bestandsbijlagen opslaat. Deze waarde is een optionele parameter en u kunt opgeven `null` of u geen bestanden aan het formulier wilt koppelen.
   * Een lange uitvoerparameter die wordt gebruikt om het aantal pagina&#39;s op te slaan.
   * Een tekenreeks-uitvoerparameter die wordt gebruikt om de waarde van de landinstelling op te slaan.
   * Een `FormsResult` uitvoerparameter die wordt gebruikt om het interactieve PDF-formulier op te slaan `.`
   De `renderPDFForm2` methode retourneert een `FormsResult` object dat het interactieve PDF-formulier bevat.

1. Een handeling uitvoeren met de gegevensstroom van het formulier

   * Maak een `BLOB` object dat formuliergegevens bevat door de waarde van het `FormsResult` veld van het `outputContent` object op te halen.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die staat voor de bestandslocatie van het interactieve PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud wordt opgeslagen van het `BLOB` object dat van het `FormsResult` object is opgehaald. Vul de bytearray met de waarde van het `BLOB` `MTOM` gegevenslid van het object.
   * Maak een `System.IO.BinaryWriter` object door de constructor ervan aan te roepen en het `System.IO.FileStream` object door te geven.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door de methode van het `System.IO.BinaryWriter` `Write` object aan te roepen en de bytearray door te geven.

**Zie ook**

[AEM-formulieren aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
