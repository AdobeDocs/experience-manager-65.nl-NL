---
title: Documenten doorgeven aan FormsService
description: Geef een com.adobe.idp.Document-object dat het formulierontwerp bevat door aan de Forms-service. Het formulierontwerp wordt door de Forms-service weergegeven in het object com.adobe.idp.Document.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: 29c7ebda-407a-464b-a9db-054163f5b737
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services,APIs & Integrations
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '1677'
ht-degree: 0%

---

# Documenten doorgeven aan de Forms-service {#passing-documents-to-the-formsservice}

**de Steekproeven en de voorbeelden in dit document zijn slechts voor AEM Forms op milieu JEE.**

De AEM Forms-service rendert interactieve PDF forms naar clientapparaten, meestal webbrowsers, om informatie van gebruikers te verzamelen. Een interactief PDF-formulier is gebaseerd op een formulierontwerp dat gewoonlijk als een XDP-bestand wordt opgeslagen en in Designer wordt gemaakt. Vanaf AEM Forms kunt u een `com.adobe.idp.Document` -object met het formulierontwerp doorgeven aan de Forms-service. De Forms-service geeft het formulierontwerp vervolgens weer in het `com.adobe.idp.Document` -object.

Een voordeel van het doorgeven van een `com.adobe.idp.Document` -object aan de Forms-service is dat andere servicebewerkingen een `com.adobe.idp.Document` -instantie retourneren. U kunt dus een `com.adobe.idp.Document` -instantie ophalen uit een andere servicebewerking en deze renderen. Stel bijvoorbeeld dat een XDP-bestand wordt opgeslagen in een knooppunt Content Services (afgekeurd) met de naam `/Company Home/Form Designs` , zoals in de volgende afbeelding wordt getoond.

U kunt Loan.xdp via programmacode ophalen uit Content Services (afgekeurd) (afgekeurd) en het XDP-bestand doorgeven aan de Forms-service binnen een `com.adobe.idp.Document` -object.

>[!NOTE]
>
>Voor meer informatie over de dienst van Forms, zie [&#x200B; Verwijzing van de Diensten voor AEM Forms &#x200B;](https://www.adobe.com/go/learn_aemforms_services_63).

## Overzicht van de stappen {#summary-of-steps}

Als u een document dat is verkregen van Content Services (afgekeurd) (afgekeurd) wilt doorgeven aan de Forms-service, voert u de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak een Forms en een Document Management Client API-object.
1. Haal het formulierontwerp op bij Inhoudsservices (afgekeurd).
1. Het interactieve PDF-formulier weergeven.
1. Voer een handeling uit met de gegevensstroom van het formulier.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, neemt u de proxybestanden op.

**creeer een Forms en een voorwerp van de Cliënt API van het Beheer van het Document**

Voordat u een API-bewerking voor Forms-services programmatisch kunt uitvoeren, maakt u een Forms Client API-object. Omdat met deze workflow een XDP-bestand wordt opgehaald van Content Services (afgekeurd), maakt u ook een Document Management API-object.

**wint het vormontwerp van de (Vervangen) Diensten van de Inhoud terug**

Haal het XDP-bestand op van Content Services (afgekeurd) met de Java- of webservice-API. Het XDP-bestand wordt geretourneerd binnen een `com.adobe.idp.Document` -instantie (of een `BLOB` -instantie als u webservices gebruikt). Vervolgens kunt u de instantie `com.adobe.idp.Document` doorgeven aan de Forms-service.

**geef een interactieve vorm van PDF** terug

Als u een interactief formulier wilt genereren, geeft u het exemplaar `com.adobe.idp.Document` dat door Content Services (afgekeurd) is geretourneerd, door aan de Forms-service.

>[!NOTE]
>
>U kunt een `com.adobe.idp.Document` met het formulierontwerp doorgeven aan de Forms-service. Twee nieuwe methoden met de naam `renderPDFForm2` en `renderHTMLForm2` accepteren een `com.adobe.idp.Document` -object dat een formulierontwerp bevat.

**voer een actie met de stroom van vormgegevens uit**

Afhankelijk van het type clienttoepassing kunt u het formulier naar een clientwebbrowser schrijven of het formulier opslaan als een PDF-bestand. Een webtoepassing schrijft het formulier doorgaans naar een webbrowser. Een bureaubladtoepassing slaat het formulier echter doorgaans op als een PDF-bestand.

**zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Forms Service API Quick Start](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

## Documenten doorgeven aan de Forms-service met de Java API {#pass-documents-to-the-forms-service-using-the-java-api}

Geef een document door dat is verkregen van Content Services (afgekeurd) met de Forms-service en Content Services (afgekeurd) API (Java):

1. Projectbestanden opnemen

   Neem JAR-bestanden voor clients, zoals adobe-forms-client.jar en adobe-contentservices-client.jar, op in het klassenpad van uw Java-project.

1. Een Forms en een Document Management Client API-object maken

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat. (Zie [&#x200B; Plaatsende verbindingseigenschappen &#x200B;](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Maak een `FormsServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.
   * Maak een `DocumentManagementServiceClientImpl` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Het formulierontwerp ophalen van Content Services (afgekeurd)

   Roep de methode `retrieveContent` van het object `DocumentManagementServiceClientImpl` aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de opslaglocatie opgeeft waar de inhoud wordt toegevoegd. De standaardopslag is `SpacesStore`. Deze waarde is een verplichte parameter.
   * Een tekenreekswaarde die het volledig gekwalificeerde pad opgeeft van de inhoud die moet worden opgehaald (bijvoorbeeld `/Company Home/Form Designs/Loan.xdp` ). Deze waarde is een verplichte parameter.
   * Een tekenreekswaarde die de versie opgeeft. Deze waarde is een optionele parameter en u kunt een lege tekenreeks doorgeven. In dit geval wordt de laatste versie opgehaald.

   De methode `retrieveContent` retourneert een `CRCResult` -object dat het XDP-bestand bevat. Haal een `com.adobe.idp.Document` -instantie op door de methode `CRCResult` object `getDocument` aan te roepen.

1. Een interactief PDF-formulier renderen

   Roep de methode `renderPDFForm2` van het object `FormsServiceClient` aan en geef de volgende waarden door:

   * Een `com.adobe.idp.Document` -object dat het formulierontwerp bevat dat is opgehaald uit Content Services (afgekeurd).
   * Een `com.adobe.idp.Document` -object dat gegevens bevat die met het formulier moeten worden samengevoegd. Wanneer u geen gegevens wilt samenvoegen, geeft u een leeg `com.adobe.idp.Document` -object door.
   * Een `PDFFormRenderSpec` -object dat uitvoeringsopties opslaat. Deze waarde is een optionele parameter en u kunt `null` opgeven als u geen runtime-opties wilt opgeven.
   * Een `URLSpec` -object dat URI-waarden bevat. Deze waarde is een optionele parameter en u kunt `null` opgeven.
   * Een `java.util.HashMap` -object dat bestandsbijlagen opslaat. Deze waarde is een optionele parameter en u kunt `null` opgeven als u geen bestanden aan het formulier wilt koppelen.

   De methode `renderPDFForm` retourneert een `FormsResult` -object dat een formuliergegevensstroom bevat die naar de webbrowser van de client moet worden geschreven.

1. Een handeling uitvoeren met de gegevensstroom van het formulier

   * Maak een `com.adobe.idp.Document` -object door de methode `FormsResult` object &#39;s `getOutputContent` aan te roepen.
   * Haal het inhoudstype van het object `com.adobe.idp.Document` op door de methode `getContentType` ervan aan te roepen.
   * Stel het inhoudstype van het `javax.servlet.http.HttpServletResponse` -object in door de methode `setContentType` ervan aan te roepen en het inhoudstype van het `com.adobe.idp.Document` -object door te geven.
   * Maak een `javax.servlet.ServletOutputStream` -object dat wordt gebruikt om de formuliergegevensstroom naar de webbrowser van de client te schrijven door de methode `javax.servlet.http.HttpServletResponse` object `getOutputStream` aan te roepen.
   * Maak een `java.io.InputStream` -object door de methode `com.adobe.idp.Document` object `getInputStream` aan te roepen.
   * Maak een bytearray en vul deze met de formuliergegevensstroom door de methode `read` van het object `InputStream` aan te roepen. Geef de bytearray door als een argument.
   * Roep de methode `write` van het object `javax.servlet.ServletOutputStream` aan om de gegevensstroom van het formulier naar de webbrowser van de client te verzenden. Geef de bytearray door aan de methode `write` .

**zie ook**

[Snel starten (SOAP modus): documenten doorgeven aan de Forms-service met behulp van de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-passing-documents-to-the-forms-service-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Documenten doorgeven aan de Forms-service met de API voor webservices {#pass-documents-to-the-forms-service-using-the-web-service-api}

Geef een document door dat is verkregen van Content Services (afgekeurd) met de Forms-service en Content Services (afgekeurd) API (webservice):

1. Projectbestanden opnemen

   Creeer een Microsoft .NET project dat MTOM gebruikt. Omdat deze cliënttoepassing de twee diensten van AEM Forms aanhaalt, creeer twee de dienstverwijzingen. Gebruik de volgende WSDL-definitie voor de serviceverwijzing die aan de Forms-service is gekoppeld: `http://localhost:8080/soap/services/FormsService?WSDL&lc_version=9.0.1` .

   Gebruik de volgende WSDL-definitie voor de serviceverwijzing die is gekoppeld aan de Document Management-service: `http://localhost:8080/soap/services/DocumentManagementService?WSDL&lc_version=9.0.1` .

   Omdat het gegevenstype `BLOB` veel wordt gebruikt voor beide serviceverwijzingen, kunt u het gegevenstype van `BLOB` volledig kwalificeren wanneer u het gebruikt. In de bijbehorende webservice quick start zijn alle `BLOB` -instanties volledig gekwalificeerd.

   >[!NOTE]
   >
   >Vervang `localhost` met het IP adres van de server die AEM Forms ontvangt.

1. Een Forms en een Document Management Client API-object maken

   * Maak een `FormsServiceClient` -object met de standaardconstructor.
   * Maak een `FormsServiceClient.Endpoint.Address` -object met de `System.ServiceModel.EndpointAddress` -constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/FormsService?WSDL` ). U hoeft het attribuut `lc_version` niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Maak een `System.ServiceModel.BasicHttpBinding` -object door de waarde van het `FormsServiceClient.Endpoint.Binding` -veld op te halen. De geretourneerde waarde wordt gecast naar `BasicHttpBinding` .
   * Stel het veld `MessageEncoding` van het `System.ServiceModel.BasicHttpBinding` -object in op `WSMessageEncoding.Mtom` . Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld `FormsServiceClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de bijbehorende wachtwoordwaarde toe aan het veld `FormsServiceClient.ClientCredentials.UserName.Password` .
      * Wijs de constante waarde `HttpClientCredentialType.Basic` toe aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType` .

   * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` toe aan het veld `BasicHttpBindingSecurity.Security.Mode` .

   >[!NOTE]
   >
   >Herhaal deze stappen voor de `DocumentManagementServiceClient` de dienstcliënt.

1. Het formulierontwerp ophalen van Content Services (afgekeurd)

   Haal inhoud op door de methode `retrieveContent` van het object `DocumentManagementServiceClient` aan te roepen en de volgende waarden door te geven:

   * Een tekenreekswaarde die de opslaglocatie opgeeft waar de inhoud wordt toegevoegd. De standaardopslag is `SpacesStore`. Deze waarde is een verplichte parameter.
   * Een tekenreekswaarde die het volledig gekwalificeerde pad opgeeft van de inhoud die moet worden opgehaald (bijvoorbeeld `/Company Home/Form Designs/Loan.xdp` ). Deze waarde is een verplichte parameter.
   * Een tekenreekswaarde die de versie opgeeft. Deze waarde is een optionele parameter en u kunt een lege tekenreeks doorgeven. In dit geval wordt de laatste versie opgehaald.
   * Een parameter van de koordoutput die doorbladert verbindingswaarde opslaat.
   * Een `BLOB` uitvoerparameter die de inhoud opslaat. U kunt deze uitvoerparameter gebruiken om de inhoud op te halen.
   * Een `ServiceReference1.MyMapOf_xsd_string_To_xsd_anyType` uitvoerparameter die inhoudskenmerken opslaat.
   * Een `CRCResult` uitvoerparameter. In plaats van dit object te gebruiken, kunt u de uitvoerparameter `BLOB` gebruiken om de inhoud op te halen.

1. Een interactief PDF-formulier renderen

   Roep de methode `renderPDFForm2` van het object `FormsServiceClient` aan en geef de volgende waarden door:

   * Een `BLOB` -object dat het formulierontwerp bevat dat is opgehaald uit Content Services (afgekeurd).
   * Een `BLOB` -object dat gegevens bevat die met het formulier moeten worden samengevoegd. Wanneer u geen gegevens wilt samenvoegen, geeft u een leeg `BLOB` -object door.
   * Een `PDFFormRenderSpec` -object dat uitvoeringsopties opslaat. Deze waarde is een optionele parameter en u kunt `null` opgeven als u geen runtime-opties wilt opgeven.
   * Een `URLSpec` -object dat URI-waarden bevat. Deze waarde is een optionele parameter en u kunt `null` opgeven.
   * Een `Map` -object dat bestandsbijlagen opslaat. Deze waarde is een optionele parameter en u kunt `null` opgeven als u geen bestanden aan het formulier wilt koppelen.
   * Een lange uitvoerparameter die wordt gebruikt om het aantal pagina&#39;s op te slaan.
   * Een tekenreeks-uitvoerparameter die wordt gebruikt om de waarde van de landinstelling op te slaan.
   * Een `FormsResult` -uitvoerparameter die wordt gebruikt om het interactieve PDF-formulier op te slaan `.`

   De methode `renderPDFForm2` retourneert een `FormsResult` -object dat het interactieve PDF-formulier bevat.

1. Een handeling uitvoeren met de gegevensstroom van het formulier

   * Maak een `BLOB` -object dat formuliergegevens bevat door de waarde van het veld `FormsResult` object `outputContent` op te halen.
   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die staat voor de bestandslocatie van het interactieve PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud wordt opgeslagen van het `BLOB` -object dat is opgehaald van het `FormsResult` -object. Vul de bytearray met de waarde van het gegevenslid `MTOM` van het object `BLOB` .
   * Maak een `System.IO.BinaryWriter` -object door de constructor ervan aan te roepen en het `System.IO.FileStream` -object door te geven.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door de methode `Write` van het object `System.IO.BinaryWriter` aan te roepen en de bytearray door te geven.

**zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
