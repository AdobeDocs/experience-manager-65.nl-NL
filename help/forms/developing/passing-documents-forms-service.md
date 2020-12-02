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
workflow-type: tm+mt
source-wordcount: '1652'
ht-degree: 0%

---


# Documenten doorgeven aan de Forms-service {#passing-documents-to-the-formsservice}

De AEM Forms-service rendert interactieve PDF forms naar clientapparaten, meestal webbrowsers, om informatie van gebruikers te verzamelen. Een interactief PDF-formulier is gebaseerd op een formulierontwerp dat gewoonlijk als een XDP-bestand wordt opgeslagen en in Designer wordt gemaakt. Vanaf AEM Forms kunt u een `com.adobe.idp.Document`-object met het formulierontwerp doorgeven aan de Forms-service. De Forms-service geeft vervolgens het formulierontwerp weer dat zich in het object `com.adobe.idp.Document` bevindt.

Een voordeel van het doorgeven van een `com.adobe.idp.Document`-object aan de Forms-service is dat andere servicebewerkingen een `com.adobe.idp.Document`-instantie retourneren. Dat wil zeggen dat u een `com.adobe.idp.Document` instantie kunt ophalen van een andere servicebewerking en deze kunt renderen. Stel dat een XDP-bestand wordt opgeslagen in een knooppunt Content Services (afgekeurd) met de naam `/Company Home/Form Designs`, zoals in de volgende afbeelding wordt getoond.

U kunt Loan.xdp programmatically terugwinnen van (afgekeurd) (van de Inhoud) en het XDP dossier tot de dienst van Forms binnen een `com.adobe.idp.Document` voorwerp overgaan.

>[!NOTE]
>
>Zie [Referentiehandleiding voor services voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63) voor meer informatie over de Forms-service.

## Overzicht van stappen {#summary-of-steps}

Als u een document dat is verkregen van Content Services (afgekeurd) (afgekeurd) wilt doorgeven aan de Forms-service, voert u de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak een Forms en een Document Management Client API-object.
1. Haal het formulierontwerp op bij Inhoudsservices (afgekeurd).
1. Het interactieve PDF-formulier renderen.
1. Voer een handeling uit met de gegevensstroom van het formulier.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, neemt u de proxybestanden op.

**Een Forms en een Document Management Client API-object maken**

Voordat u een API-bewerking voor Forms-services programmatisch kunt uitvoeren, maakt u een Forms Client API-object. Omdat met deze workflow een XDP-bestand wordt opgehaald van Content Services (afgekeurd), maakt u ook een Document Management API-object.

**Het formulierontwerp ophalen van Content Services (afgekeurd)**

Haal het XDP-bestand op van Content Services (afgekeurd) met behulp van de Java- of webservice-API. Het XDP-bestand wordt geretourneerd binnen een `com.adobe.idp.Document`-instantie (of een `BLOB`-instantie als u webservices gebruikt). Vervolgens kunt u de instantie `com.adobe.idp.Document` doorgeven aan de Forms-service.

**Een interactief PDF-formulier renderen**

Als u een interactief formulier wilt genereren, geeft u het exemplaar `com.adobe.idp.Document` dat is geretourneerd van Content Services (afgekeurd), door aan de Forms-service.

>[!NOTE]
>
>U kunt een `com.adobe.idp.Document` met het formulierontwerp doorgeven aan de Forms-service. Twee nieuwe methoden met de naam `renderPDFForm2` en `renderHTMLForm2` accepteren een `com.adobe.idp.Document`-object dat een formulierontwerp bevat.

**Een handeling uitvoeren met de gegevensstroom van het formulier**

Afhankelijk van het type clienttoepassing kunt u het formulier naar een clientwebbrowser schrijven of het formulier opslaan als een PDF-bestand. Een webtoepassing schrijft het formulier doorgaans naar een webbrowser. Een bureaubladtoepassing slaat het formulier echter doorgaans op als een PDF-bestand.

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Forms Service API Quick Start](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

## Documenten doorgeven aan de Forms-service met de Java API {#pass-documents-to-the-forms-service-using-the-java-api}

Geef een document door dat is verkregen van Content Services (afgekeurd) met de Forms-service en Content Services (afgekeurd) API (Java):

1. Projectbestanden opnemen

   Neem JAR-bestanden voor clients, zoals adobe-forms-client.jar en adobe-contentservices-client.jar, op in het klassenpad van uw Java-project.

1. Een Forms en een Document Management Client API-object maken

   * Maak een `ServiceClientFactory`-object dat verbindingseigenschappen bevat. (Zie [Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Maak een `FormsServiceClient`-object door de constructor ervan te gebruiken en het object `ServiceClientFactory` door te geven.
   * Maak een `DocumentManagementServiceClientImpl`-object door de constructor ervan te gebruiken en het object `ServiceClientFactory` door te geven.

1. Het formulierontwerp ophalen van Content Services (afgekeurd)

   Roep de methode `retrieveContent` van het object `DocumentManagementServiceClientImpl` aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de opslaglocatie opgeeft waar de inhoud wordt toegevoegd. De standaardopslag is `SpacesStore`. Deze waarde is een verplichte parameter.
   * Een tekenreekswaarde die het volledig gekwalificeerde pad opgeeft van de inhoud die moet worden opgehaald (bijvoorbeeld `/Company Home/Form Designs/Loan.xdp`). Deze waarde is een verplichte parameter.
   * Een tekenreekswaarde die de versie opgeeft. Deze waarde is een optionele parameter en u kunt een lege tekenreeks doorgeven. In dit geval wordt de laatste versie opgehaald.

   De methode `retrieveContent` retourneert een `CRCResult`-object dat het XDP-bestand bevat. Verkrijg een `com.adobe.idp.Document` instantie door de `CRCResult` methode van het voorwerp `getDocument` aan te halen.

1. Een interactief PDF-formulier renderen

   Roep de methode `renderPDFForm2` van het object `FormsServiceClient` aan en geef de volgende waarden door:

   * Een `com.adobe.idp.Document`-object dat het formulierontwerp bevat dat is opgehaald uit Content Services (afgekeurd).
   * Een object `com.adobe.idp.Document` dat gegevens bevat die met het formulier moeten worden samengevoegd. Als u geen gegevens wilt samenvoegen, geeft u een leeg `com.adobe.idp.Document`-object door.
   * Een `PDFFormRenderSpec`-object dat uitvoeringsopties opslaat. Deze waarde is een optionele parameter en u kunt `null` opgeven als u geen runtime-opties wilt opgeven.
   * Een object `URLSpec` dat URI-waarden bevat. Deze waarde is een optionele parameter en u kunt `null` opgeven.
   * Een `java.util.HashMap`-object dat bestandsbijlagen opslaat. Deze waarde is een optionele parameter en u kunt `null` opgeven als u geen bestanden aan het formulier wilt koppelen.

   De methode `renderPDFForm` retourneert een `FormsResult`-object dat een formuliergegevensstroom bevat die naar de webbrowser van de client moet worden geschreven.

1. Een handeling uitvoeren met de gegevensstroom van het formulier

   * Maak een `com.adobe.idp.Document`-object door de methode `getOutputContent` van het object aan te roepen.`FormsResult`
   * Hiermee wordt het inhoudstype van het object `com.adobe.idp.Document` opgehaald door de methode `getContentType` ervan aan te roepen.
   * Stel het inhoudstype van het object `javax.servlet.http.HttpServletResponse` in door de methode `setContentType` ervan aan te roepen en het inhoudstype van het object `com.adobe.idp.Document` door te geven.
   * Maak een `javax.servlet.ServletOutputStream`-object dat wordt gebruikt om de formuliergegevensstroom naar de webbrowser van de client te schrijven door de methode `javax.servlet.http.HttpServletResponse` van het object `getOutputStream` aan te roepen.
   * Maak een `java.io.InputStream`-object door de methode `getInputStream` van het object `com.adobe.idp.Document` aan te roepen.
   * Maak een bytearray en vul deze met de formuliergegevensstroom door de methode `read` van het object `InputStream` aan te roepen. Geef de bytearray door als een argument.
   * Roep de methode `javax.servlet.ServletOutputStream` van het object `write` aan om de gegevensstroom van het formulier naar de webbrowser van de client te verzenden. Geef de bytearray door aan de methode `write`.

**Zie ook**

[Snel starten (SOAP-modus): Documenten doorgeven aan de Forms-service met de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-passing-documents-to-the-forms-service-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Documenten doorgeven aan de Forms-service met de API {#pass-documents-to-the-forms-service-using-the-web-service-api} voor webservices

Geef een document door dat is verkregen van Content Services (afgekeurd) met de Forms-service en Content Services (afgekeurd) API (webservice):

1. Projectbestanden opnemen

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Omdat deze cliënttoepassing de twee diensten van AEM Forms aanhaalt, creeer twee de dienstverwijzingen. Gebruik de volgende definitie van WSDL voor de de dienstverwijzing verbonden aan de dienst van Forms: `http://localhost:8080/soap/services/FormsService?WSDL&lc_version=9.0.1`.

   Gebruik de volgende definitie WSDL voor de de dienstverwijzing verbonden aan de dienst van het Beheer van het Document: `http://localhost:8080/soap/services/DocumentManagementService?WSDL&lc_version=9.0.1`.

   Omdat het gegevenstype `BLOB` gemeenschappelijk is voor beide serviceverwijzingen, moet u het gegevenstype `BLOB` volledig kwalificeren wanneer u het gebruikt. In de overeenkomstige webservice quick start zijn alle `BLOB`-instanties volledig gekwalificeerd.

   >[!NOTE]
   >
   >Vervang `localhost`door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Een Forms en een Document Management Client API-object maken

   * Maak een `FormsServiceClient`-object met de standaardconstructor.
   * Maak een `FormsServiceClient.Endpoint.Address`-object met de constructor `System.ServiceModel.EndpointAddress`. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/FormsService?WSDL`). U hoeft het `lc_version`-kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Maak een `System.ServiceModel.BasicHttpBinding`-object door de waarde van het veld `FormsServiceClient.Endpoint.Binding` op te halen. Cast de terugkeerwaarde aan `BasicHttpBinding`.
   * Stel het veld `System.ServiceModel.BasicHttpBinding` van het object `MessageEncoding` in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor het AEM aan het veld `FormsServiceClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de overeenkomstige wachtwoordwaarde aan het gebied `FormsServiceClient.ClientCredentials.UserName.Password` toe.
      * Wijs de constante waarde `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType` toe.
   * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode` toe.

   >[!NOTE]
   >
   >Herhaal deze stappen voor de `DocumentManagementServiceClient`serviceclient.

1. Het formulierontwerp ophalen van Content Services (afgekeurd)

   Haal inhoud op door de methode `DocumentManagementServiceClient` van het object `retrieveContent` aan te roepen en de volgende waarden door te geven:

   * Een tekenreekswaarde die de opslaglocatie opgeeft waar de inhoud wordt toegevoegd. De standaardopslag is `SpacesStore`. Deze waarde is een verplichte parameter.
   * Een tekenreekswaarde die het volledig gekwalificeerde pad opgeeft van de inhoud die moet worden opgehaald (bijvoorbeeld `/Company Home/Form Designs/Loan.xdp`). Deze waarde is een verplichte parameter.
   * Een tekenreekswaarde die de versie opgeeft. Deze waarde is een optionele parameter en u kunt een lege tekenreeks doorgeven. In dit geval wordt de laatste versie opgehaald.
   * Een parameter van de koordoutput die doorbladert verbindingswaarde opslaat.
   * Een `BLOB` uitvoerparameter die de inhoud opslaat. U kunt deze uitvoerparameter gebruiken om de inhoud op te halen.
   * Een `ServiceReference1.MyMapOf_xsd_string_To_xsd_anyType`-uitvoerparameter die inhoudskenmerken opslaat.
   * A `CRCResult` outputparameter. In plaats van dit object te gebruiken, kunt u de uitvoerparameter `BLOB` gebruiken om de inhoud op te halen.

1. Een interactief PDF-formulier renderen

   Roep de methode `renderPDFForm2` van het object `FormsServiceClient` aan en geef de volgende waarden door:

   * Een `BLOB`-object dat het formulierontwerp bevat dat is opgehaald uit Content Services (afgekeurd).
   * Een object `BLOB` dat gegevens bevat die met het formulier moeten worden samengevoegd. Als u geen gegevens wilt samenvoegen, geeft u een leeg `BLOB`-object door.
   * Een `PDFFormRenderSpec`-object dat uitvoeringsopties opslaat. Deze waarde is een optionele parameter en u kunt `null` opgeven als u geen runtime-opties wilt opgeven.
   * Een object `URLSpec` dat URI-waarden bevat. Deze waarde is een optionele parameter en u kunt `null` opgeven.
   * Een `Map`-object dat bestandsbijlagen opslaat. Deze waarde is een optionele parameter en u kunt `null` opgeven als u geen bestanden aan het formulier wilt koppelen.
   * Een lange uitvoerparameter die wordt gebruikt om het aantal pagina&#39;s op te slaan.
   * Een tekenreeks-uitvoerparameter die wordt gebruikt om de waarde van de landinstelling op te slaan.
   * Een `FormsResult`-uitvoerparameter die wordt gebruikt om het interactieve PDF-formulier `.` op te slaan

   De methode `renderPDFForm2` retourneert een `FormsResult`-object dat het interactieve PDF-formulier bevat.

1. Een handeling uitvoeren met de gegevensstroom van het formulier

   * Maak een `BLOB`-object dat formuliergegevens bevat door de waarde op te halen van het `FormsResult`-veld van het `outputContent`-object.
   * Maak een `System.IO.FileStream`-object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die staat voor de bestandslocatie van het interactieve PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud wordt opgeslagen van het `BLOB`-object dat is opgehaald uit het `FormsResult`-object. Vul de bytearray met de waarde van het `BLOB`-gegevenslid van het object `MTOM`.
   * Maak een `System.IO.BinaryWriter`-object door de constructor ervan aan te roepen en het object `System.IO.FileStream` door te geven.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door de methode `Write` van het object `System.IO.BinaryWriter` aan te roepen en de bytearray door te geven.

**Zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
