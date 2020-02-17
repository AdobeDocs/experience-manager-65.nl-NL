---
title: De prestaties van de Forms Service optimaliseren
seo-title: De prestaties van de Forms Service optimaliseren
description: 'null'
seo-description: 'null'
uuid: 9040c09a-e5d0-432b-b1c5-ad46ab57c4fc
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 9f883483-b81e-42c6-a4a1-eb499dd112e7
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# De prestaties van de Forms Service optimaliseren {#optimizing-the-performance-of-theforms-service}

## De prestaties van de Forms Service optimaliseren {#optimizing-the-performance-of-the-forms-service}

Bij het weergeven van een formulier kunt u runtime-opties instellen die de prestaties van de Forms-service optimaliseren. Een andere taak die u kunt uitvoeren om de prestaties van de service Forms te verbeteren, is het opslaan van XDP-bestanden in de opslagplaats. In deze sectie wordt echter niet beschreven hoe deze taak moet worden uitgevoerd. (Zie Een service [aanroepen met een Java-clientbibliotheek](/help/forms/developing/invoking-aem-forms-using-java.md#invoking-a-service-using-a-java-client-library).)

>[!NOTE]
>
>Voor meer informatie over de dienst van Vormen, zie de Verwijzing van de [Diensten voor Vormen](https://www.adobe.com/go/learn_aemforms_services_63)AEM.

### Overzicht van de stappen {#summary-of-steps}

Voer de volgende taken uit om de prestaties van de Forms-service te optimaliseren tijdens het genereren van een formulier:

1. Inclusief projectbestanden.
1. Maak een Forms Client API-object.
1. Stel opties voor de uitvoeringstijd in.
1. Het formulier weergeven.
1. Schrijf de gegevensstroom van het formulier naar de webbrowser van de client.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**Een Forms Client API-object maken**

Voordat u een API-bewerking voor Forms-service programmatisch kunt uitvoeren, moet u een Forms-service-client maken. Als u de Java API gebruikt, maakt u een `FormsServiceClient` object. Als u de API voor webservices van Forms gebruikt, maakt u een `FormsService` object.

**Opties voor het uitvoeren van de prestaties instellen**

U kunt de volgende opties voor de uitvoeringstijd instellen om de prestaties van de service Forms te verbeteren:

* **Formulier in cache plaatsen**: U kunt een formulier dat als PDF is gegenereerd, in de cache van de server plaatsen. Elk formulier wordt in de cache geplaatst nadat het voor het eerst wordt gegenereerd. Als het formulier in de cache vervolgens wordt gerenderd en het nieuwer is dan de tijdstempel van het formulierontwerp, wordt het formulier opgehaald uit de cache. Door formulieren in cache te plaatsen, verbetert u de prestaties van de Forms-service, omdat het formulierontwerp niet hoeft op te halen uit een opslagplaats.
* Het kan langer duren om formulierhulplijnen (afgekeurd) te renderen dan andere transformatietypen. U wordt aangeraden hulplijnen (afgekeurd) in cache te plaatsen om de prestaties te verbeteren.
* **Standalone optie**: Als u niet wilt dat de service Forms berekeningen op de server uitvoert, kunt u de optie Standalone instellen op `true`, zodat formulieren zonder statusinformatie worden gegenereerd. Statusinformatie is nodig als u een interactief formulier wilt genereren voor een eindgebruiker die vervolgens gegevens in het formulier invoert en het formulier terugstuurt naar de service Forms. De service Forms voert vervolgens een berekening uit en geeft het formulier weer aan de gebruiker met de resultaten die in het formulier worden weergegeven. Als een formulier zonder statusinformatie wordt teruggestuurd naar de service Forms, zijn alleen de XML-gegevens beschikbaar en worden geen berekeningen op de server uitgevoerd.
* **Gelijkmatig gemaakte PDF**: Een gelineariseerd PDF-bestand is zo geordend dat efficiënte incrementele toegang in een netwerkomgeving mogelijk is. Het PDF-bestand is in alle opzichten een geldige PDF en is compatibel met alle bestaande viewers en andere PDF-toepassingen. Een gelineariseerde PDF kan dus worden weergegeven terwijl deze nog wordt gedownload.
* Deze optie verbetert de prestaties niet wanneer een PDF-formulier op de client wordt weergegeven.
* **GuideRSL, optie**: Hiermee schakelt u het genereren van een formulierhulplijn (afgekeurd) in met gezamenlijke bibliotheken bij uitvoering. Dit betekent dat de eerste aanvraag een kleiner SWF-bestand en grotere gedeelde bibliotheken downloadt die in de cache van de browser zijn opgeslagen. Zie RSL in de Flex-documentatie voor meer informatie.
* U kunt de prestaties van de service Forms ook verbeteren door een formulier op de client te genereren. (Zie Formulieren [renderen op de client](/help/forms/developing/rendering-forms-client.md).)

**Het formulier renderen**

Als u het formulier wilt genereren nadat u prestatieopties hebt ingesteld, gebruikt u dezelfde toepassingslogica als voor het weergeven van een formulier zonder prestatieopties.

**De formuliergegevensstroom naar de webbrowser van de client schrijven**

Nadat een formulier is gerenderd door de Forms-service, wordt een formuliergegevensstroom geretourneerd die u moet schrijven naar de webbrowser van de client. Wanneer het formulier naar de webbrowser van de client wordt geschreven, is het zichtbaar voor de gebruiker.

**Zie ook**

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Forms Service API, snel aan de slag](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Interactieve PDF-formulieren renderen](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Formulieren weergeven als HTML](/help/forms/developing/rendering-forms-html.md)

[Webtoepassingen maken die formulieren renderen](/help/forms/developing/creating-web-applications-renders-forms.md)

### De prestaties optimaliseren met de Java API {#optimize-the-performance-using-the-java-api}

Een formulier met geoptimaliseerde prestaties renderen met de Forms API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-forms-client.jar, op in het klassenpad van uw Java-project.

1. Een Forms Client API-object maken

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `FormsServiceClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Opties voor het uitvoeren van de prestaties instellen

   * Maak een `PDFFormRenderSpec` object met de constructor ervan.
   * Stel de optie voor de cache van het formulier in door de methode van het `PDFFormRenderSpec` object aan te roepen en door te geven `setCacheEnabled` `true`.
   * Stel de optie Lineair in door de methode van het `PDFFormRenderSpec` `setLinearizedPDF` object aan te roepen en door te geven `true.`

1. Het formulier renderen

   Roep de methode van het `FormsServiceClient` `renderPDFForm` object aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie.
   * Een `com.adobe.idp.Document` object dat gegevens bevat die met het formulier moeten worden samengevoegd. Geef een leeg `com.adobe.idp.Document` object door als u geen gegevens wilt samenvoegen.
   * Een `PDFFormRenderSpec` object dat uitvoeringsopties opslaat om de prestaties te verbeteren.
   * Een `URLSpec` object dat URI-waarden bevat die door de service Forms worden vereist.
   * Een `java.util.HashMap` object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt opgeven `null` of u geen bestanden aan het formulier wilt koppelen.
   De `renderPDFForm` methode retourneert een `FormsResult` object dat een formuliergegevensstroom bevat die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Maak een `javax.servlet.ServletOutputStream` object dat wordt gebruikt om een formuliergegevensstroom naar de webbrowser van de client te verzenden.
   * Maak een `com.adobe.idp.Document` object door de `FormsResult` methode van het `getOutputContent` object aan te roepen.
   * Maak een `java.io.InputStream` object door de `com.adobe.idp.Document` methode van het `getInputStream` object aan te roepen.
   * Maak een bytearray en vul deze met de formuliergegevensstroom door de `InputStream` `read`methode van het object aan te roepen en de bytearray als een argument door te geven.
   * Roep de `javax.servlet.ServletOutputStream` methode van het `write` object aan om de formuliergegevensstroom naar de webbrowser van de client te verzenden. Geef de bytearray door aan de `write` methode.

**Zie ook**

[Snel starten (SOAP-modus): Prestaties optimaliseren met de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-optimizing-performance-using-the-java-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### De prestaties optimaliseren met de webservice-API {#optimize-the-performance-using-the-web-service-api}

Een formulier met geoptimaliseerde prestaties renderen met de Forms API (webservice):

1. Projectbestanden opnemen

   * Maak Java-proxyklassen die de Forms service WSDL gebruiken.
   * Neem de Java-proxyklassen op in het klassepad.

1. Een Forms Client API-object maken

   Maak een `FormsService` object en stel verificatiewaarden in.

1. Opties voor het uitvoeren van de prestaties instellen

   * Maak een `PDFFormRenderSpec` object met de constructor ervan.
   * Stel de optie voor de cache van het formulier in door de methode van het `PDFFormRenderSpec` `setCacheEnabled` object aan te roepen en waar door te geven.
   * Stel de zelfstandige optie in door de methode van het `PDFFormRenderSpec` `setStandAlone` object aan te roepen en waar door te geven.
   * Stel de lineaire optie in door de methode van het `PDFFormRenderSpec` `setLinearizedPDF` object aan te roepen en waar door te geven.

1. Het formulier renderen

   Roep de methode van het `FormsService` `renderPDFForm` object aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie.
   * Een `BLOB` object dat gegevens bevat die met het formulier moeten worden samengevoegd. Geef door als u geen gegevens wilt samenvoegen. `null`
   * Een `PDFFormRenderSpecc` object dat uitvoeringsopties opslaat.
   * Een `URLSpec` object dat URI-waarden bevat die door de service Forms worden vereist.
   * Een `java.util.HashMap` object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt opgeven `null` of u geen bestanden aan het formulier wilt koppelen.
   * Een leeg `com.adobe.idp.services.holders.BLOBHolder` object dat door de methode wordt gevuld. Hiermee slaat u het gerenderde PDF-formulier op.
   * Een leeg `javax.xml.rpc.holders.LongHolder` object dat door de methode wordt gevuld. (In dit argument wordt het aantal pagina&#39;s in het formulier opgeslagen).
   * Een leeg `javax.xml.rpc.holders.StringHolder` object dat door de methode wordt gevuld. (In dit argument wordt de waarde van de landinstelling opgeslagen.)
   * Een leeg `com.adobe.idp.services.holders.FormsResultHolder` object dat de resultaten van deze bewerking zal bevatten.
   De `renderPDFForm` methode vult het `com.adobe.idp.services.holders.FormsResultHolder` object dat als laatste argumentwaarde wordt doorgegeven, met een formuliergegevensstroom die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Maak een `FormResult` object door de waarde van het `com.adobe.idp.services.holders.FormsResultHolder` `value` gegevenslid van het object op te halen.
   * Maak een `javax.servlet.ServletOutputStream` object dat wordt gebruikt om een formuliergegevensstroom naar de webbrowser van de client te verzenden.
   * Maak een `BLOB` object dat formuliergegevens bevat door de `FormsResult` methode van het `getOutputContent` object aan te roepen.
   * Maak een bytearray en vul deze door de `BLOB` methode van het `getBinaryData` object aan te roepen. Hierdoor wordt de inhoud van het `FormsResult` object toegewezen aan de bytearray.
   * Roep de `javax.servlet.http.HttpServletResponse` methode van het `write` object aan om de formuliergegevensstroom naar de webbrowser van de client te verzenden. Geef de bytearray door aan de `write` methode.

**Zie ook**

[AEM-formulieren aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
