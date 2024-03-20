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
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1677'
ht-degree: 0%

---

# Documenten doorgeven aan de Forms-service {#passing-documents-to-the-formsservice}

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

De AEM Forms-service rendert interactieve PDF forms naar clientapparaten, meestal webbrowsers, om informatie van gebruikers te verzamelen. Een interactief PDF-formulier is gebaseerd op een formulierontwerp dat gewoonlijk als een XDP-bestand wordt opgeslagen en in Designer wordt gemaakt. Vanaf AEM Forms kunt u een `com.adobe.idp.Document` object dat het formulierontwerp bevat voor de Forms-service. De Forms-service geeft het formulierontwerp vervolgens weer in het dialoogvenster `com.adobe.idp.Document` object.

Een voordeel van het doorgeven van een `com.adobe.idp.Document` object voor de Forms-service is dat andere servicebewerkingen een `com.adobe.idp.Document` -instantie. Dat wil zeggen dat je een `com.adobe.idp.Document` instantie van een andere servicebewerking en rendert u deze. Stel dat een XDP-bestand wordt opgeslagen in een knooppunt Content Services (afgekeurd) genaamd `/Company Home/Form Designs`, zoals in de volgende afbeelding wordt getoond.

U kunt Loan.xdp programmatically terugwinnen van (afgekeurd) de Diensten van de Inhoud (en het XDP dossier tot de dienst van Forms binnen overgaan `com.adobe.idp.Document` object.

>[!NOTE]
>
>Voor meer informatie over de Forms-service raadpleegt u [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Overzicht van de stappen {#summary-of-steps}

Als u een document dat is verkregen van Content Services (afgekeurd) (afgekeurd) wilt doorgeven aan de Forms-service, voert u de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak een Forms en een Document Management Client API-object.
1. Haal het formulierontwerp op bij Inhoudsservices (afgekeurd).
1. Het interactieve PDF-formulier weergeven.
1. Voer een handeling uit met de gegevensstroom van het formulier.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, neemt u de proxybestanden op.

**Een Forms en een Document Management Client API-object maken**

Voordat u een API-bewerking voor Forms-services programmatisch kunt uitvoeren, maakt u een Forms Client API-object. Omdat met deze workflow een XDP-bestand wordt opgehaald van Content Services (afgekeurd), maakt u ook een Document Management API-object.

**Het formulierontwerp ophalen van Content Services (afgekeurd)**

Haal het XDP-bestand op van Content Services (afgekeurd) met de Java- of webservice-API. Het XDP-bestand wordt geretourneerd binnen een `com.adobe.idp.Document` instantie (of een `BLOB` -instantie als u webservices gebruikt). U kunt dan de `com.adobe.idp.Document` naar de Forms-service.

**Een interactief PDF-formulier renderen**

Als u een interactief formulier wilt genereren, geeft u het `com.adobe.idp.Document` instantie die is geretourneerd van Content Services (afgekeurd) aan de Forms-service.

>[!NOTE]
>
>U kunt een `com.adobe.idp.Document` die het formulierontwerp voor de Forms-service bevat. Twee nieuwe methoden met naam `renderPDFForm2` en `renderHTMLForm2` accepteren `com.adobe.idp.Document` object dat een formulierontwerp bevat.

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

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat. (Zie [Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Een `FormsServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.
   * Een `DocumentManagementServiceClientImpl` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Het formulierontwerp ophalen van Content Services (afgekeurd)

   De `DocumentManagementServiceClientImpl` object `retrieveContent` en geeft de volgende waarden door:

   * Een tekenreekswaarde die de opslaglocatie opgeeft waar de inhoud wordt toegevoegd. De standaardopslag is `SpacesStore`. Deze waarde is een verplichte parameter.
   * Een tekenreekswaarde die het volledig gekwalificeerde pad opgeeft van de inhoud die moet worden opgehaald (bijvoorbeeld `/Company Home/Form Designs/Loan.xdp`). Deze waarde is een verplichte parameter.
   * Een tekenreekswaarde die de versie opgeeft. Deze waarde is een optionele parameter en u kunt een lege tekenreeks doorgeven. In dit geval wordt de laatste versie opgehaald.

   De `retrieveContent` methode retourneert een `CRCResult` object dat het XDP-bestand bevat. Vraag een `com.adobe.idp.Document` instantie door de `CRCResult` object `getDocument` methode.

1. Een interactief PDF-formulier renderen

   De `FormsServiceClient` object `renderPDFForm2` en geeft de volgende waarden door:

   * A `com.adobe.idp.Document` object dat het formulierontwerp bevat dat is opgehaald uit Content Services (afgekeurd).
   * A `com.adobe.idp.Document` object dat gegevens bevat die met het formulier moeten worden samengevoegd. Als u geen gegevens wilt samenvoegen, geeft u een lege waarde door `com.adobe.idp.Document` object.
   * A `PDFFormRenderSpec` -object dat uitvoeringsopties opslaat. Deze waarde is een optionele parameter en u kunt `null` als u geen runtime opties wilt opgeven.
   * A `URLSpec` object dat URI-waarden bevat. Deze waarde is een optionele parameter en u kunt `null`.
   * A `java.util.HashMap` object waarin bestandsbijlagen zijn opgeslagen. Deze waarde is een optionele parameter en u kunt `null` als u geen bestanden aan het formulier wilt koppelen.

   De `renderPDFForm` methode retourneert een `FormsResult` object dat een formuliergegevensstroom bevat die naar de webbrowser van de client moet worden geschreven.

1. Een handeling uitvoeren met de gegevensstroom van het formulier

   * Een `com.adobe.idp.Document` door het object aan te roepen `FormsResult` object &#39;s `getOutputContent` methode.
   * Hiermee wordt het inhoudstype van het dialoogvenster `com.adobe.idp.Document` object aanroepen `getContentType` methode.
   * Stel de `javax.servlet.http.HttpServletResponse` inhoudstype van object door het aan te roepen `setContentType` en geeft u het inhoudstype van de `com.adobe.idp.Document` object.
   * Een `javax.servlet.ServletOutputStream` object dat wordt gebruikt om de formuliergegevensstroom naar de webbrowser van de client te schrijven door het aanroepen van de `javax.servlet.http.HttpServletResponse` object `getOutputStream` methode.
   * Een `java.io.InputStream` door het object aan te roepen `com.adobe.idp.Document` object `getInputStream` methode.
   * Maak een bytearray en vul deze met de formuliergegevensstroom door de `InputStream` object `read` methode. Geef de bytearray door als een argument.
   * De `javax.servlet.ServletOutputStream` object `write` methode om de formuliergegevensstroom naar de webbrowser van de client te verzenden. Geef de bytearray door aan de `write` methode.

**Zie ook**

[Snel starten (SOAP-modus): documenten doorgeven aan de Forms-service met behulp van de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-passing-documents-to-the-forms-service-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Documenten doorgeven aan de Forms-service met de API voor webservices {#pass-documents-to-the-forms-service-using-the-web-service-api}

Geef een document door dat is verkregen van Content Services (afgekeurd) met de Forms-service en Content Services (afgekeurd) API (webservice):

1. Projectbestanden opnemen

   Creeer een Microsoft .NET project dat MTOM gebruikt. Omdat deze cliënttoepassing de twee diensten van AEM Forms aanhaalt, creeer twee de dienstverwijzingen. Gebruik de volgende definitie van WSDL voor de de dienstverwijzing verbonden aan de dienst van Forms: `http://localhost:8080/soap/services/FormsService?WSDL&lc_version=9.0.1`.

   Gebruik de volgende definitie WSDL voor de de dienstverwijzing verbonden aan de dienst van het Beheer van het Document: `http://localhost:8080/soap/services/DocumentManagementService?WSDL&lc_version=9.0.1`.

   Omdat de `BLOB` het gegevenstype is gemeenschappelijk voor beide de dienstverwijzingen, kwalificeer volledig `BLOB` gegevenstype bij gebruik ervan. In de bijbehorende webservice kunt u snel aan de slag met `BLOB` exemplaren zijn volledig gekwalificeerd.

   >[!NOTE]
   >
   >Vervangen `localhost`met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Een Forms en een Document Management Client API-object maken

   * Een `FormsServiceClient` object met de standaardconstructor.
   * Een `FormsServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/FormsService?WSDL`). U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `FormsServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `FormsServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `FormsServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.

   * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

   >[!NOTE]
   >
   >Herhaal deze stappen voor de `DocumentManagementServiceClient`serviceclient.

1. Het formulierontwerp ophalen van Content Services (afgekeurd)

   Inhoud ophalen door de `DocumentManagementServiceClient` object `retrieveContent` en geeft de volgende waarden door:

   * Een tekenreekswaarde die de opslaglocatie opgeeft waar de inhoud wordt toegevoegd. De standaardopslag is `SpacesStore`. Deze waarde is een verplichte parameter.
   * Een tekenreekswaarde die het volledig gekwalificeerde pad opgeeft van de inhoud die moet worden opgehaald (bijvoorbeeld `/Company Home/Form Designs/Loan.xdp`). Deze waarde is een verplichte parameter.
   * Een tekenreekswaarde die de versie opgeeft. Deze waarde is een optionele parameter en u kunt een lege tekenreeks doorgeven. In dit geval wordt de laatste versie opgehaald.
   * Een parameter van de koordoutput die doorbladert verbindingswaarde opslaat.
   * A `BLOB` uitvoerparameter die de inhoud opslaat. U kunt deze uitvoerparameter gebruiken om de inhoud op te halen.
   * A `ServiceReference1.MyMapOf_xsd_string_To_xsd_anyType` uitvoerparameter die inhoudskenmerken opslaat.
   * A `CRCResult` uitvoerparameter. In plaats van dit object te gebruiken, kunt u de opdracht `BLOB` uitvoerparameter om de inhoud te verkrijgen.

1. Een interactief PDF-formulier renderen

   De `FormsServiceClient` object `renderPDFForm2` en geeft de volgende waarden door:

   * A `BLOB` object dat het formulierontwerp bevat dat is opgehaald uit Content Services (afgekeurd).
   * A `BLOB` object dat gegevens bevat die met het formulier moeten worden samengevoegd. Als u geen gegevens wilt samenvoegen, geeft u een lege waarde door `BLOB` object.
   * A `PDFFormRenderSpec` -object dat uitvoeringsopties opslaat. Deze waarde is een optionele parameter en u kunt `null` als u geen runtime opties wilt opgeven.
   * A `URLSpec` object dat URI-waarden bevat. Deze waarde is een optionele parameter en u kunt `null`.
   * A `Map` object waarin bestandsbijlagen zijn opgeslagen. Deze waarde is een optionele parameter en u kunt `null` als u geen bestanden aan het formulier wilt koppelen.
   * Een lange uitvoerparameter die wordt gebruikt om het aantal pagina&#39;s op te slaan.
   * Een tekenreeks-uitvoerparameter die wordt gebruikt om de waarde van de landinstelling op te slaan.
   * A `FormsResult` uitvoerparameter die wordt gebruikt om het interactieve PDF-formulier op te slaan `.`

   De `renderPDFForm2` methode retourneert een `FormsResult` object dat het interactieve PDF-formulier bevat.

1. Een handeling uitvoeren met de gegevensstroom van het formulier

   * Een `BLOB` object dat formuliergegevens bevat door de waarde van de `FormsResult` object `outputContent` veld.
   * Een `System.IO.FileStream` object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die staat voor de bestandslocatie van het interactieve PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van de `BLOB` object opgehaald uit het `FormsResult` object. Vul de bytearray met de waarde van de `BLOB` object `MTOM` lid.
   * Een `System.IO.BinaryWriter` object door de constructor aan te roepen en de `System.IO.FileStream` object.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door het `System.IO.BinaryWriter` object `Write` en geeft u de bytearray door.

**Zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
