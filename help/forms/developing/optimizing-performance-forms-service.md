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
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1424'
ht-degree: 0%

---

# De prestaties van de Forms-service optimaliseren {#optimizing-the-performance-of-theforms-service}

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

## De prestaties van de Forms-service optimaliseren {#optimizing-the-performance-of-the-forms-service}

Bij het weergeven van een formulier kunt u uitvoeringsopties instellen die de prestaties van de Forms-service optimaliseren. Een andere taak die u kunt uitvoeren om de prestaties van de Forms-service te verbeteren, is het opslaan van XDP-bestanden in de opslagplaats. In deze sectie wordt echter niet beschreven hoe deze taak moet worden uitgevoerd. (Zie [Een service aanroepen met een Java-clientbibliotheek](/help/forms/developing/invoking-aem-forms-using-java.md#invoking-a-service-using-a-java-client-library).)

>[!NOTE]
>
>Voor meer informatie over de Forms-service raadpleegt u [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary-of-steps}

Voer de volgende taken uit om de prestaties van de Forms-service te optimaliseren tijdens het genereren van een formulier:

1. Inclusief projectbestanden.
1. Maak een Forms Client API-object.
1. Stel opties voor het uitvoeren van de prestaties in.
1. Het formulier weergeven.
1. Schrijf de gegevensstroom van het formulier naar de webbrowser van de client.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**Een Forms Client API-object maken**

Voordat u programmatisch een client-API-bewerking voor Forms-services kunt uitvoeren, moet u een Forms-serviceclient maken. Als u de Java API gebruikt, maakt u een `FormsServiceClient` object. Als u de Forms-webservice-API gebruikt, maakt u een `FormsService` object.

**Opties voor het uitvoeren van de prestaties instellen**

U kunt de volgende uitvoeringsopties voor de prestaties instellen om de prestaties van de Forms-service te verbeteren:

* **Formulier in cache plaatsen**: U kunt een formulier dat als PDF wordt weergegeven, in de cache van de server in cache plaatsen. Elk formulier wordt in de cache geplaatst nadat het voor het eerst wordt gegenereerd. Als het formulier in de cache vervolgens wordt gerenderd en het nieuwer is dan de tijdstempel van het formulierontwerp, wordt het formulier opgehaald uit de cache. Door formulieren in cache te plaatsen, verbetert u de prestaties van de Forms-service, omdat het formulierontwerp niet hoeft op te halen uit een opslagplaats.
* Het kan langer duren om formulierhulplijnen (afgekeurd) te renderen dan andere transformatietypen. U wordt aangeraden hulplijnen (afgekeurd) in cache te plaatsen om de prestaties te verbeteren.
* **Standalone, optie**: Als u niet wilt dat de Forms-service serverberekeningen uitvoert, kunt u de optie Standalone instellen op `true`, wat ertoe leidt dat formulieren worden gegenereerd zonder statusinformatie. Statusinformatie is nodig als u een interactief formulier wilt genereren voor een eindgebruiker die vervolgens gegevens in het formulier invoert en het formulier terugstuurt naar de Forms-service. De Forms-service voert vervolgens een berekeningsbewerking uit en geeft het formulier weer aan de gebruiker met de resultaten die in het formulier worden weergegeven. Als een formulier zonder statusinformatie wordt teruggestuurd naar de Forms-service, zijn alleen de XML-gegevens beschikbaar en worden geen berekeningen op de server uitgevoerd.
* **Lineaire PDF**: Een gelineariseerd PDF-bestand is geordend om efficiënte incrementele toegang in een netwerkomgeving mogelijk te maken. Het PDF-bestand is in alle opzichten geldig PDF en is compatibel met alle bestaande viewers en andere PDF-toepassingen. Een gelineariseerde PDF kan dus worden weergegeven terwijl het bestand nog wordt gedownload.
* Deze optie verbetert de prestaties niet wanneer een PDF-formulier op de client wordt gegenereerd.
* **GuideRSL, optie**: Schakelt het genereren van (afgekeurde) formulierhulplijnen in via gezamenlijke bibliotheken bij uitvoering. Dit betekent het eerste verzoek een kleiner SWF-bestand zal downloaden, plus grotere gedeelde bibliotheken die in het browsercache zijn opgeslagen. Zie RSL in de documentatie van Flex voor meer informatie.
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

### De prestaties optimaliseren met de Java API {#optimize-the-performance-using-the-java-api}

Een formulier met optimale prestaties renderen met de Forms API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-forms-client.jar, op in het klassenpad van uw Java-project.

1. Een Forms Client API-object maken

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `FormsServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Opties voor het uitvoeren van de prestaties instellen

   * Een `PDFFormRenderSpec` object met behulp van de constructor.
   * Stel de optie voor de cache van het formulier in door de `PDFFormRenderSpec` object `setCacheEnabled` methode en doorgeven `true`.
   * Stel de optie Gelineariseerd in door de `PDFFormRenderSpec` object `setLinearizedPDF` methode en doorgeven `true.`

1. Het formulier renderen

   De `FormsServiceClient` object `renderPDFForm` en geeft de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie.
   * A `com.adobe.idp.Document` object dat gegevens bevat die met het formulier moeten worden samengevoegd. Als u geen gegevens wilt samenvoegen, geeft u een lege waarde door `com.adobe.idp.Document` object.
   * A `PDFFormRenderSpec` -object dat uitvoeringsopties opslaat om de prestaties te verbeteren.
   * A `URLSpec` object dat URI-waarden bevat die door de Forms-service worden vereist.
   * A `java.util.HashMap` object waarin bestandsbijlagen zijn opgeslagen. Dit is een optionele parameter en u kunt `null` als u geen bestanden aan het formulier wilt koppelen.

   De `renderPDFForm` methode retourneert een `FormsResult` object dat een formuliergegevensstroom bevat die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Een `javax.servlet.ServletOutputStream` object dat wordt gebruikt om een formuliergegevensstroom naar de webbrowser van de client te verzenden.
   * Een `com.adobe.idp.Document` door het object aan te roepen `FormsResult` object &#39;s `getOutputContent` methode.
   * Een `java.io.InputStream` door het object aan te roepen `com.adobe.idp.Document` object `getInputStream` methode.
   * Maak een bytearray en vul deze met de formuliergegevensstroom door de `InputStream` object `read`en de bytearray doorgeven als een argument.
   * De `javax.servlet.ServletOutputStream` object `write` methode om de formuliergegevensstroom naar de webbrowser van de client te verzenden. Geef de bytearray door aan de `write` methode.

**Zie ook**

[Snel starten (SOAP-modus): Prestaties optimaliseren met behulp van de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-optimizing-performance-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### De prestaties optimaliseren met de webservice-API {#optimize-the-performance-using-the-web-service-api}

Een formulier met optimale prestaties renderen met de Forms API (webservice):

1. Projectbestanden opnemen

   * Maak Java-proxyklassen die gebruikmaken van de Forms-service WSDL.
   * Neem de Java-proxyklassen op in het klassepad.

1. Een Forms Client API-object maken

   Een `FormsService` -object en stel verificatiewaarden in.

1. Opties voor het uitvoeren van de prestaties instellen

   * Een `PDFFormRenderSpec` object met behulp van de constructor.
   * Stel de optie voor de cache van het formulier in door de `PDFFormRenderSpec` object `setCacheEnabled` en waar doorgeven.
   * Stel de zelfstandige optie in door de `PDFFormRenderSpec` object `setStandAlone` en waar doorgeven.
   * Stel de optie Gelineariseerd in door de `PDFFormRenderSpec` object `setLinearizedPDF` en waar doorgeven.

1. Het formulier renderen

   De `FormsService` object `renderPDFForm` en geeft de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie.
   * A `BLOB` object dat gegevens bevat die met het formulier moeten worden samengevoegd. Als u geen gegevens wilt samenvoegen, geeft u `null`.
   * A `PDFFormRenderSpecc` -object dat uitvoeringsopties opslaat.
   * A `URLSpec` object dat URI-waarden bevat die door de Forms-service worden vereist.
   * A `java.util.HashMap` object waarin bestandsbijlagen zijn opgeslagen. Dit is een optionele parameter en u kunt `null` als u geen bestanden aan het formulier wilt koppelen.
   * Een leeg `com.adobe.idp.services.holders.BLOBHolder` object dat door de methode wordt gevuld. Hiermee slaat u het gerenderde PDF formulier op.
   * Een leeg `javax.xml.rpc.holders.LongHolder` object dat door de methode wordt gevuld. (In dit argument wordt het aantal pagina&#39;s in het formulier opgeslagen).
   * Een leeg `javax.xml.rpc.holders.StringHolder` object dat door de methode wordt gevuld. (In dit argument wordt de waarde van de landinstelling opgeslagen.)
   * Een leeg `com.adobe.idp.services.holders.FormsResultHolder` -object dat de resultaten van deze bewerking zal bevatten.

   De `renderPDFForm` wordt de `com.adobe.idp.services.holders.FormsResultHolder` object dat wordt doorgegeven als de laatste argumentwaarde met een formuliergegevensstroom die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Een `FormResult` object door de waarde van het object op te halen `com.adobe.idp.services.holders.FormsResultHolder` object `value` lid.
   * Een `javax.servlet.ServletOutputStream` object dat wordt gebruikt om een formuliergegevensstroom naar de webbrowser van de client te verzenden.
   * Een `BLOB` object dat formuliergegevens bevat door het `FormsResult` object `getOutputContent` methode.
   * Maak een bytearray en vul deze door het `BLOB` object `getBinaryData` methode. Deze taak wijst de inhoud van toe `FormsResult` object naar de bytearray.
   * De `javax.servlet.http.HttpServletResponse` object `write` methode om de formuliergegevensstroom naar de webbrowser van de client te verzenden. Geef de bytearray door aan de `write` methode.

**Zie ook**

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
