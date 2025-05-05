---
title: De prestaties van de Forms Service optimaliseren
description: Stel uitvoeringsopties in bij het weergeven van een formulier en sla XDP-bestanden op in de opslagplaats om de prestaties van de Forms-service te optimaliseren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: 5a746c6c-bf6e-4b25-ba7c-a35edb1f55f3
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services,APIs & Integrations
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '1424'
ht-degree: 0%

---

# De prestaties van de Forms-service optimaliseren {#optimizing-the-performance-of-theforms-service}

**de Steekproeven en de voorbeelden in dit document zijn slechts voor AEM Forms op milieu JEE.**

## De prestaties van de Forms-service optimaliseren {#optimizing-the-performance-of-the-forms-service}

Bij het weergeven van een formulier kunt u uitvoeringsopties instellen die de prestaties van de Forms-service optimaliseren. Een andere taak die u kunt uitvoeren om de prestaties van de Forms-service te verbeteren, is het opslaan van XDP-bestanden in de opslagplaats. In deze sectie wordt echter niet beschreven hoe deze taak moet worden uitgevoerd. (Zie [ het Aanhalen van de dienst gebruikend een de cliëntbibliotheek van Java ](/help/forms/developing/invoking-aem-forms-using-java.md#invoking-a-service-using-a-java-client-library).)

>[!NOTE]
>
>Voor meer informatie over de dienst van Forms, zie [ Verwijzing van de Diensten voor AEM Forms ](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary-of-steps}

Voer de volgende taken uit om de prestaties van de Forms-service te optimaliseren tijdens het genereren van een formulier:

1. Inclusief projectbestanden.
1. Maak een Forms Client API-object.
1. Stel opties voor het uitvoeren van de prestaties in.
1. Het formulier weergeven.
1. Schrijf de gegevensstroom van het formulier naar de webbrowser van de client.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**creeer een voorwerp van Forms Cliënt API**

Voordat u programmatisch een client-API-bewerking voor Forms-services kunt uitvoeren, moet u een Forms-serviceclient maken. Maak een `FormsServiceClient` -object als u de Java API gebruikt. Maak een `FormsService` -object als u de Forms-API voor webservices gebruikt.

**plaats prestaties runtime opties**

U kunt de volgende uitvoeringsopties voor de prestaties instellen om de prestaties van de Forms-service te verbeteren:

* **vorm caching**: U kunt een vorm in het voorgeheugen onderbrengen die als PDF in het servergeheime voorgeheugen wordt teruggegeven. Elk formulier wordt in de cache geplaatst nadat het voor het eerst wordt gegenereerd. Als het formulier in de cache vervolgens wordt gerenderd en het nieuwer is dan de tijdstempel van het formulierontwerp, wordt het formulier opgehaald uit de cache. Door formulieren in cache te plaatsen, verbetert u de prestaties van de Forms-service, omdat het formulierontwerp niet hoeft op te halen uit een opslagplaats.
* Het kan langer duren om formulierhulplijnen (afgekeurd) te renderen dan andere transformatietypen. U wordt aangeraden hulplijnen (afgekeurd) in cache te plaatsen om de prestaties te verbeteren.
* **Standalone optie**: Als u de dienst van Forms niet vereist om server-zijberekeningen uit te voeren, kunt u de Standalone optie plaatsen aan `true`, die in vormen zonder staatsinformatie resulteert. Statusinformatie is nodig als u een interactief formulier wilt genereren voor een eindgebruiker die vervolgens gegevens in het formulier invoert en het formulier terugstuurt naar de Forms-service. De Forms-service voert vervolgens een berekeningsbewerking uit en geeft het formulier weer aan de gebruiker met de resultaten die in het formulier worden weergegeven. Als een formulier zonder statusinformatie wordt teruggestuurd naar de Forms-service, zijn alleen de XML-gegevens beschikbaar en worden geen berekeningen op de server uitgevoerd.
* **Gelineariseerde PDF**: Een gelineariseerd dossier van PDF wordt georganiseerd om efficiënte stijgende toegang in een netwerkmilieu toe te laten. Het PDF-bestand is in alle opzichten geldig PDF en is compatibel met alle bestaande viewers en andere PDF-toepassingen. Een gelineariseerde PDF kan dus worden weergegeven terwijl het bestand nog wordt gedownload.
* Deze optie verbetert de prestaties niet wanneer een PDF-formulier op de client wordt gegenereerd.
* **GuideRSL optie**: Laat (afgekeurde) generatie van de vormengids gebruikend runtime gedeelde bibliotheken toe. Dit betekent het eerste verzoek een kleiner SWF-bestand zal downloaden, plus grotere gedeelde bibliotheken die in het browsercache zijn opgeslagen. Zie RSL in de documentatie van Flex voor meer informatie.
* U kunt ook de prestaties van de Forms-service verbeteren door een formulier op de client te genereren. (Zie [ teruggevend Forms bij de Cliënt ](/help/forms/developing/rendering-forms-client.md).)

**geef de vorm** terug

Als u het formulier wilt genereren nadat u prestatieopties hebt ingesteld, gebruikt u dezelfde toepassingslogica als voor het weergeven van een formulier zonder prestatieopties.

**schrijf de stroom van vormgegevens aan cliëntWeb browser**

Nadat de Forms-service een formulier heeft gegenereerd, wordt een formuliergegevensstroom geretourneerd die u moet schrijven naar de webbrowser van de client. Wanneer het formulier naar de webbrowser van de client wordt geschreven, is het zichtbaar voor de gebruiker.

**zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Forms Service API Quick Start](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Interactieve PDF forms renderen](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Forms renderen als HTML](/help/forms/developing/rendering-forms-html.md)

[Webtoepassingen maken die Forms renderen](/help/forms/developing/creating-web-applications-renders-forms.md)

### De prestaties optimaliseren met de Java API {#optimize-the-performance-using-the-java-api}

Een formulier met optimale prestaties renderen met de Forms API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-forms-client.jar, op in het klassenpad van uw Java-project.

1. Een Forms Client API-object maken

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `FormsServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Opties voor het uitvoeren van de prestaties instellen

   * Maak een `PDFFormRenderSpec` -object met behulp van de constructor.
   * Stel de optie voor de cache van het formulier in door de methode `setCacheEnabled` van het object `PDFFormRenderSpec` aan te roepen en door te geven `true` .
   * Stel de optie Lineair in door de methode `setLinearizedPDF` van het object `PDFFormRenderSpec` aan te roepen en door te geven `true.`

1. Het formulier renderen

   Roep de methode `renderPDFForm` van het object `FormsServiceClient` aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie.
   * Een `com.adobe.idp.Document` -object dat gegevens bevat die met het formulier moeten worden samengevoegd. Wanneer u geen gegevens wilt samenvoegen, geeft u een leeg `com.adobe.idp.Document` -object door.
   * Een `PDFFormRenderSpec` -object dat uitvoeringsopties opslaat om de prestaties te verbeteren.
   * Een `URLSpec` -object dat URI-waarden bevat die door de Forms-service worden vereist.
   * Een `java.util.HashMap` -object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt `null` opgeven als u geen bestanden aan het formulier wilt koppelen.

   De methode `renderPDFForm` retourneert een `FormsResult` -object dat een formuliergegevensstroom bevat die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Maak een `javax.servlet.ServletOutputStream` -object dat wordt gebruikt om een formuliergegevensstroom naar de webbrowser van de client te verzenden.
   * Maak een `com.adobe.idp.Document` -object door de methode `FormsResult` object &#39;s `getOutputContent` aan te roepen.
   * Maak een `java.io.InputStream` -object door de methode `com.adobe.idp.Document` object `getInputStream` aan te roepen.
   * Creeer een byteserie en bevolk het met de stroom van vormgegevens door de `read` methode van objecten `InputStream` aan te halen &lbrace;en de byteserie als argument over te gaan.
   * Roep de methode `write` van het object `javax.servlet.ServletOutputStream` aan om de gegevensstroom van het formulier naar de webbrowser van de client te verzenden. Geef de bytearray door aan de methode `write` .

**zie ook**

[Snel starten (SOAP modus): Prestaties optimaliseren met de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-optimizing-performance-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### De prestaties optimaliseren met de webservice-API {#optimize-the-performance-using-the-web-service-api}

Een formulier met optimale prestaties renderen met de Forms API (webservice):

1. Projectbestanden opnemen

   * Maak Java-proxyklassen die gebruikmaken van de Forms-service WSDL.
   * Neem de Java-proxyklassen op in het klassepad.

1. Een Forms Client API-object maken

   Maak een `FormsService` -object en stel de verificatiewaarden in.

1. Opties voor het uitvoeren van de prestaties instellen

   * Maak een `PDFFormRenderSpec` -object met behulp van de constructor.
   * Stel de optie voor de cache van het formulier in door de methode `setCacheEnabled` van het object `PDFFormRenderSpec` aan te roepen en waar door te geven.
   * Stel de zelfstandige optie in door de methode `setStandAlone` van het object `PDFFormRenderSpec` aan te roepen en door te geven waar.
   * Stel de lineaire optie in door de methode `setLinearizedPDF` van het object `PDFFormRenderSpec` aan te roepen en waar door te geven.

1. Het formulier renderen

   Roep de methode `renderPDFForm` van het object `FormsService` aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie.
   * Een `BLOB` -object dat gegevens bevat die met het formulier moeten worden samengevoegd. Geef `null` door als u geen gegevens wilt samenvoegen.
   * Een `PDFFormRenderSpecc` -object dat uitvoeringsopties opslaat.
   * Een `URLSpec` -object dat URI-waarden bevat die door de Forms-service worden vereist.
   * Een `java.util.HashMap` -object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt `null` opgeven als u geen bestanden aan het formulier wilt koppelen.
   * Een leeg `com.adobe.idp.services.holders.BLOBHolder` -object dat door de methode wordt gevuld. Hiermee slaat u het gerenderde PDF formulier op.
   * Een leeg `javax.xml.rpc.holders.LongHolder` -object dat door de methode wordt gevuld. (In dit argument wordt het aantal pagina&#39;s in het formulier opgeslagen).
   * Een leeg `javax.xml.rpc.holders.StringHolder` -object dat door de methode wordt gevuld. (In dit argument wordt de waarde van de landinstelling opgeslagen.)
   * Een leeg `com.adobe.idp.services.holders.FormsResultHolder` -object dat de resultaten van deze bewerking bevat.

   Met de methode `renderPDFForm` wordt het `com.adobe.idp.services.holders.FormsResultHolder` -object dat als laatste argumentwaarde wordt doorgegeven, gevuld met een formuliergegevensstroom die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Maak een `FormResult` -object door de waarde van het gegevenslid van het `com.adobe.idp.services.holders.FormsResultHolder` object `value` op te halen.
   * Maak een `javax.servlet.ServletOutputStream` -object dat wordt gebruikt om een formuliergegevensstroom naar de webbrowser van de client te verzenden.
   * Maak een `BLOB` -object dat formuliergegevens bevat door de methode `FormsResult` object `getOutputContent` aan te roepen.
   * Maak een bytearray en vul deze door de methode `getBinaryData` van het object `BLOB` aan te roepen. Hierdoor wordt de inhoud van het `FormsResult` -object toegewezen aan de bytearray.
   * Roep de methode `write` van het object `javax.servlet.http.HttpServletResponse` aan om de gegevensstroom van het formulier naar de webbrowser van de client te verzenden. Geef de bytearray door aan de methode `write` .

**zie ook**

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
