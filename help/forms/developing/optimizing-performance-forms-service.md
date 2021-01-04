---
title: De prestaties van de Forms Service optimaliseren
seo-title: De prestaties van de Forms Service optimaliseren
description: Stel uitvoeringsopties in bij het weergeven van een formulier en sla XDP-bestanden op in de opslagplaats om de prestaties van de Forms-service te optimaliseren.
seo-description: Stel uitvoeringsopties in bij het weergeven van een formulier en sla XDP-bestanden op in de opslagplaats om de prestaties van de Forms-service te optimaliseren.
uuid: 9040c09a-e5d0-432b-b1c5-ad46ab57c4fc
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 9f883483-b81e-42c6-a4a1-eb499dd112e7
translation-type: tm+mt
source-git-commit: 07889ead2ae402b5fb738ca08c7efe076ef33e44
workflow-type: tm+mt
source-wordcount: '1445'
ht-degree: 0%

---


# De prestaties van de Forms-service optimaliseren {#optimizing-the-performance-of-theforms-service}

## De prestaties van de Forms-service optimaliseren {#optimizing-the-performance-of-the-forms-service}

Bij het weergeven van een formulier kunt u uitvoeringsopties instellen die de prestaties van de Forms-service optimaliseren. Een andere taak die u kunt uitvoeren om de prestaties van de Forms-service te verbeteren, is het opslaan van XDP-bestanden in de opslagplaats. In deze sectie wordt echter niet beschreven hoe deze taak moet worden uitgevoerd. (Zie [Een service aanroepen met een Java-clientbibliotheek](/help/forms/developing/invoking-aem-forms-using-java.md#invoking-a-service-using-a-java-client-library).)

>[!NOTE]
>
>Zie [Referentiehandleiding voor services voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63) voor meer informatie over de Forms-service.

### Overzicht van stappen {#summary-of-steps}

Voer de volgende taken uit om de prestaties van de Forms-service te optimaliseren tijdens het genereren van een formulier:

1. Inclusief projectbestanden.
1. Maak een Forms Client API-object.
1. Stel opties voor de uitvoeringstijd in.
1. Het formulier weergeven.
1. Schrijf de gegevensstroom van het formulier naar de webbrowser van de client.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**Een Forms Client API-object maken**

Voordat u programmatisch een client-API-bewerking voor Forms-services kunt uitvoeren, moet u een Forms-serviceclient maken. Als u de Java API gebruikt, maakt u een `FormsServiceClient`-object. Als u de Forms-API voor webservices gebruikt, maakt u een `FormsService`-object.

**Opties voor het uitvoeren van de prestaties instellen**

U kunt de volgende uitvoeringsopties voor de prestaties instellen om de prestaties van de Forms-service te verbeteren:

* **Formulier in cache plaatsen**: U kunt een formulier dat als PDF is gegenereerd, in de cache van de server plaatsen. Elk formulier wordt in de cache geplaatst nadat het voor het eerst wordt gegenereerd. Als het formulier in de cache vervolgens wordt gerenderd en het nieuwer is dan de tijdstempel van het formulierontwerp, wordt het formulier opgehaald uit de cache. Door formulieren in cache te plaatsen, verbetert u de prestaties van de Forms-service, omdat het formulierontwerp niet hoeft op te halen uit een opslagplaats.
* Het kan langer duren om formulierhulplijnen (afgekeurd) te renderen dan andere transformatietypen. U wordt aangeraden hulplijnen (afgekeurd) in cache te plaatsen om de prestaties te verbeteren.
* **Standalone optie**: Als u niet wilt dat de Forms-service serverberekeningen uitvoert, kunt u de optie Standalone instellen op  `true`, wat ertoe leidt dat formulieren zonder statusinformatie worden gegenereerd. Statusinformatie is nodig als u een interactief formulier wilt genereren voor een eindgebruiker die vervolgens gegevens in het formulier invoert en het formulier terugstuurt naar de Forms-service. De Forms-service voert vervolgens een berekeningsbewerking uit en geeft het formulier weer aan de gebruiker met de resultaten die in het formulier worden weergegeven. Als een formulier zonder statusinformatie wordt teruggestuurd naar de Forms-service, zijn alleen de XML-gegevens beschikbaar en worden geen berekeningen op de server uitgevoerd.
* **Gelijkmatig gemaakte PDF**: Een gelineariseerd PDF-bestand is zo geordend dat efficiënte incrementele toegang in een netwerkomgeving mogelijk is. Het PDF-bestand is in alle opzichten een geldige PDF en is compatibel met alle bestaande viewers en andere PDF-toepassingen. Een gelineariseerde PDF kan dus worden weergegeven terwijl deze nog wordt gedownload.
* Deze optie verbetert de prestaties niet wanneer een PDF-formulier op de client wordt weergegeven.
* **GuideRSL, optie**: Hiermee schakelt u het genereren van een formulierhulplijn (afgekeurd) in met gezamenlijke bibliotheken bij uitvoering. Dit betekent dat de eerste aanvraag een kleiner SWF-bestand en grotere gedeelde bibliotheken downloadt die in de cache van de browser zijn opgeslagen. Zie RSL in de documentatie van Flex voor meer informatie.
* U kunt ook de prestaties van de Forms-service verbeteren door een formulier op de client te genereren. (Zie [Forms renderen op de client](/help/forms/developing/rendering-forms-client.md).)

**Het formulier renderen**

Als u het formulier wilt genereren nadat u prestatieopties hebt ingesteld, gebruikt u dezelfde toepassingslogica als voor het weergeven van een formulier zonder prestatieopties.

**De formuliergegevensstroom naar de webbrowser van de client schrijven**

Nadat de Forms-service een formulier heeft gegenereerd, wordt een formuliergegevensstroom geretourneerd die u moet schrijven naar de webbrowser van de client. Wanneer het formulier naar de webbrowser van de client wordt geschreven, is het zichtbaar voor de gebruiker.

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Forms Service API Quick Start](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Interactieve PDF forms renderen](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Forms renderen als HTML](/help/forms/developing/rendering-forms-html.md)

[Webtoepassingen maken die Forms renderen](/help/forms/developing/creating-web-applications-renders-forms.md)

### Prestaties optimaliseren met de Java API {#optimize-the-performance-using-the-java-api}

Een formulier met optimale prestaties renderen met de Forms API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-forms-client.jar, op in het klassenpad van uw Java-project.

1. Een Forms Client API-object maken

   * Maak een `ServiceClientFactory`-object dat verbindingseigenschappen bevat.
   * Maak een `FormsServiceClient`-object door de constructor ervan te gebruiken en het object `ServiceClientFactory` door te geven.

1. Opties voor het uitvoeren van de prestaties instellen

   * Maak een `PDFFormRenderSpec`-object met de constructor ervan.
   * Stel de optie voor de cache van het formulier in door de methode `setCacheEnabled` van het object `PDFFormRenderSpec` aan te roepen en `true` door te geven.
   * Stel de lineaire optie in door de methode `PDFFormRenderSpec` van het object `setLinearizedPDF` aan te roepen en `true.` door te geven

1. Het formulier renderen

   Roep de methode `renderPDFForm` van het object `FormsServiceClient` aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie.
   * Een object `com.adobe.idp.Document` dat gegevens bevat die met het formulier moeten worden samengevoegd. Als u geen gegevens wilt samenvoegen, geeft u een leeg `com.adobe.idp.Document`-object door.
   * Een `PDFFormRenderSpec`-object dat uitvoeringsopties opslaat om de prestaties te verbeteren.
   * Een object `URLSpec` dat URI-waarden bevat die door de Forms-service worden vereist.
   * Een `java.util.HashMap`-object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt `null` opgeven als u geen bestanden aan het formulier wilt koppelen.

   De methode `renderPDFForm` retourneert een `FormsResult`-object dat een formuliergegevensstroom bevat die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Maak een `javax.servlet.ServletOutputStream`-object dat wordt gebruikt om een formuliergegevensstroom naar de webbrowser van de client te verzenden.
   * Maak een `com.adobe.idp.Document`-object door de methode `getOutputContent` van het object aan te roepen.`FormsResult`
   * Maak een `java.io.InputStream`-object door de methode `getInputStream` van het object `com.adobe.idp.Document` aan te roepen.
   * Maak een bytearray en vul deze met de formuliergegevensstroom door de methode `read`van het object `InputStream` aan te roepen en de bytearray als een argument door te geven.
   * Roep de methode `javax.servlet.ServletOutputStream` van het object `write` aan om de gegevensstroom van het formulier naar de webbrowser van de client te verzenden. Geef de bytearray door aan de methode `write`.

**Zie ook**

[Snel starten (SOAP-modus): Prestaties optimaliseren met de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-optimizing-performance-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### De prestaties optimaliseren met de webservice-API {#optimize-the-performance-using-the-web-service-api}

Een formulier met optimale prestaties renderen met de Forms API (webservice):

1. Projectbestanden opnemen

   * Maak Java-proxyklassen die gebruikmaken van de Forms-service WSDL.
   * Neem de Java-proxyklassen op in het klassepad.

1. Een Forms Client API-object maken

   Maak een `FormsService`-object en stel de verificatiewaarden in.

1. Opties voor het uitvoeren van de prestaties instellen

   * Maak een `PDFFormRenderSpec`-object met de constructor ervan.
   * Stel de optie voor de cache van het formulier in door de methode `setCacheEnabled` van het object `PDFFormRenderSpec` aan te roepen en waar door te geven.
   * Stel de zelfstandige optie in door de methode `setStandAlone` van het object `PDFFormRenderSpec` aan te roepen en waar door te geven.
   * Stel de lineaire optie in door de methode `PDFFormRenderSpec` van het object `setLinearizedPDF` aan te roepen en waar door te geven.

1. Het formulier renderen

   Roep de methode `renderPDFForm` van het object `FormsService` aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie.
   * Een object `BLOB` dat gegevens bevat die met het formulier moeten worden samengevoegd. Als u geen gegevens wilt samenvoegen, geeft u `null` door.
   * Een `PDFFormRenderSpecc`-object dat uitvoeringsopties opslaat.
   * Een object `URLSpec` dat URI-waarden bevat die door de Forms-service worden vereist.
   * Een `java.util.HashMap`-object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt `null` opgeven als u geen bestanden aan het formulier wilt koppelen.
   * Een leeg object `com.adobe.idp.services.holders.BLOBHolder` dat door de methode is gevuld. Hiermee slaat u het gerenderde PDF-formulier op.
   * Een leeg object `javax.xml.rpc.holders.LongHolder` dat door de methode is gevuld. (In dit argument wordt het aantal pagina&#39;s in het formulier opgeslagen).
   * Een leeg object `javax.xml.rpc.holders.StringHolder` dat door de methode is gevuld. (In dit argument wordt de waarde van de landinstelling opgeslagen.)
   * Een leeg `com.adobe.idp.services.holders.FormsResultHolder`-object dat de resultaten van deze bewerking zal bevatten.

   Met de methode `renderPDFForm` wordt het object `com.adobe.idp.services.holders.FormsResultHolder` dat als laatste argumentwaarde is doorgegeven, gevuld met een formuliergegevensstroom die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Maak een `FormResult`-object door de waarde op te halen van het `com.adobe.idp.services.holders.FormsResultHolder`-gegevenslid van het object.`value`
   * Maak een `javax.servlet.ServletOutputStream`-object dat wordt gebruikt om een formuliergegevensstroom naar de webbrowser van de client te verzenden.
   * Maak een `BLOB`-object dat formuliergegevens bevat door de methode `getOutputContent` van het object `FormsResult` aan te roepen.
   * Maak een bytearray en vul deze door de methode `getBinaryData` van het object `BLOB` aan te roepen. Deze taak wijst de inhoud van het `FormsResult` voorwerp aan de byteserie toe.
   * Roep de methode `javax.servlet.http.HttpServletResponse` van het object `write` aan om de gegevensstroom van het formulier naar de webbrowser van de client te verzenden. Geef de bytearray door aan de methode `write`.

**Zie ook**

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
