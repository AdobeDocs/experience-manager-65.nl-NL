---
title: Formulieren weergeven op de client
seo-title: Formulieren weergeven op de client
description: 'null'
seo-description: 'null'
uuid: 09bcc23d-28b0-473a-87f1-bc17e87620f4
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 08d36e9f-cafc-478e-9781-8fc29ac6262e
translation-type: tm+mt
source-git-commit: ab401a8007f6ea85c0e52169091ce7a38b3dbe5c

---


# Formulieren weergeven op de client {#rendering-forms-at-the-client}

## Formulieren weergeven op de client {#rendering-forms-at-the-client-inner}

U kunt de levering van PDF-inhoud optimaliseren en de mogelijkheid van de Forms-service om netwerkbelasting te verwerken verbeteren door de renderfunctie op de client van Acrobat of Adobe Reader te gebruiken. Dit proces wordt een formulier op de client weergegeven. Als u een formulier op de client wilt genereren, moet het clientapparaat (meestal een webbrowser) Acrobat 7.0 of Adobe Reader 7.0 of hoger gebruiken.

Wijzigingen in een formulier die het resultaat zijn van scriptuitvoering op de server, worden niet weerspiegeld in een formulier dat op de client wordt gegenereerd, tenzij het basissubformulier het `restoreState` kenmerk bevat dat is ingesteld op `auto`. Zie [Formulierontwerper voor meer informatie over dit kenmerk.](https://www.adobe.com/go/learn_aemforms_designer_63)

>[!NOTE]
>
>Voor meer informatie over de dienst van Vormen, zie de Verwijzing van de [Diensten voor Vormen](https://www.adobe.com/go/learn_aemforms_services_63)AEM.

### Overzicht van de stappen {#summary-of-steps}

Voer de volgende taken uit om een formulier op de client te genereren:

1. Inclusief projectbestanden.
1. Maak een Forms Client API-object.
1. Opties voor renderen tijdens runtime van client instellen.
1. Een formulier weergeven op de client.
1. Schrijf het formulier naar de webbrowser van de client.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**Een Forms Client API-object maken**

Voordat u een API-bewerking voor Forms-service programmatisch kunt uitvoeren, moet u een Forms-service-client maken. Als u de Java API gebruikt, maakt u een `FormsServiceClient` object. Als u de API voor webservices van Forms gebruikt, maakt u een `FormsService` object.

**Opties voor renderen tijdens runtime van client instellen**

U moet de optie voor het renderen van de client zo instellen dat een formulier op de client wordt gegenereerd door de optie voor `RenderAtClient` runtime in te stellen op `true`. Dit leidt ertoe dat het formulier wordt afgeleverd aan het clientapparaat waar het wordt gegenereerd. Als dit `RenderAtClient` `auto` het geval is (de standaardwaarde), bepaalt het formulierontwerp of het formulier op de client wordt gegenereerd. Het formulierontwerp moet een formulierontwerp met een stroombare indeling zijn.

Een optionele uitvoeringsoptie die u kunt instellen, is de `SeedPDF` optie. Met deze `SeedPDF` optie wordt de PDF-container (PDF-document met zaad) gecombineerd met het formulierontwerp en de XML-gegevens. Zowel het formulierontwerp als de XML-gegevens worden geleverd aan Acrobat of Adobe Reader, waar het formulier wordt gegenereerd. De `SeedPDF` optie kan worden gebruikt wanneer de clientcomputer geen fonts heeft die in het formulier worden gebruikt, bijvoorbeeld wanneer een eindgebruiker geen licentie heeft voor het gebruik van een font dat de eigenaar van het formulier mag gebruiken.

U kunt Designer gebruiken om een eenvoudig dynamisch PDF-bestand te maken dat u als PDF-bestand met zaad kunt gebruiken. De volgende stappen zijn vereist om deze taak uit te voeren:

1. Bepaal of u fonts in het PDF-bestand met zaad wilt insluiten. Het PDF-bestand met het zaadbestand moet aanvullende fonts bevatten die vereist zijn voor het formulier dat wordt gegenereerd. Wanneer u lettertypen insluit in het PDF-bestand voor het zaadbestand, moet u ervoor zorgen dat u geen licentieovereenkomsten voor lettertypen schendt. In Designer kunt u bepalen of u fonts wettelijk kunt insluiten. Als er fonts zijn die u niet in het formulier kunt insluiten wanneer u het opslaat, wordt in Designer een bericht weergegeven met de fonts die u niet kunt insluiten. Dit bericht wordt niet weergegeven in Designer voor statische PDF-documenten.
1. Als u het PDF-zaadbestand maakt in Designer, wordt u geadviseerd ten minste een tekstveld toe te voegen dat een bericht bevat. Het bericht moet worden gericht aan gebruikers van eerdere versies van Adobe Reader en aangeven dat zij Acrobat 7.0 of hoger of Adobe Reader 7.0 of hoger nodig hebben om het document te kunnen bekijken.
1. Sla het PDF-zaadbestand op als een dynamisch PDF-bestand met de bestandsnaamextensie PDF.

>[!NOTE]
>
>U hoeft de optie PDF-runtime voor het genereren van een formulier op de client niet te definiëren. Als u geen PDF-zaadbestand opgeeft, maakt de Forms-service een shell-pdf die geen COS-objecten bevat maar wel een PDF-omslag met daarin de daadwerkelijke XDP-inhoud ingesloten. Met de stappen in deze sectie wordt de optie voor het uitvoeren van de PDF-zaadbewerking niet ingesteld. Zie de handleiding Adobe PDF Reference voor informatie over COS-objecten.

**Een formulier weergeven op de client**

Als u een formulier op de client wilt genereren, moet u ervoor zorgen dat de renderopties voor de client in de toepassingslogica zijn opgenomen om een formulier te genereren.

**De formuliergegevensstroom naar de webbrowser van de client schrijven**

De service Forms maakt een formuliergegevensstroom die u naar de webbrowser van de client moet schrijven. Als het formulier wordt geschreven naar de webbrowser van de client, wordt het gegenereerd door Acrobat 7.0 of Adobe Reader 7.0 of hoger en is het zichtbaar voor de gebruiker.

**Zie ook**

[Een formulier op de client renderen met de Java API](#render-a-form-at-the-client-using-the-java-api)

[Een formulier op de client renderen met de API voor webservices](#render-a-form-at-the-client-using-the-web-service-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Forms Service API, snel aan de slag](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Documenten doorgeven aan de Forms Service](/help/forms/developing/passing-documents-forms-service.md)

[Webtoepassingen maken die formulieren renderen](/help/forms/developing/creating-web-applications-renders-forms.md)

### Een formulier op de client renderen met de Java API {#render-a-form-at-the-client-using-the-java-api}

Een formulier op de client renderen met de API voor formulieren (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-forms-client.jar, op in het klassenpad van uw Java-project.

1. Een Forms Client API-object maken

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `FormsServiceClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Opties voor renderen tijdens runtime van client instellen

   * Maak een `PDFFormRenderSpec` object met de constructor ervan.
   * Stel de `RenderAtClient` runtime-optie in door de methode van het `PDFFormRenderSpec` object aan te roepen en de opsommingswaarde door te geven `setRenderAtClient` `RenderAtClient.Yes`.

1. Een formulier weergeven op de client

   Roep de methode van het `FormsServiceClient` `renderPDFForm` object aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u verwijst naar een formulierontwerp dat deel uitmaakt van een AEM Forms-toepassing, moet u controleren of u het volledige pad opgeeft, bijvoorbeeld `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Een `com.adobe.idp.Document` object dat gegevens bevat die met het formulier moeten worden samengevoegd. Geef een leeg `com.adobe.idp.Document` object door als u geen gegevens wilt samenvoegen.
   * Een `PDFFormRenderSpec` object dat uitvoeringsopties opslaat die vereist zijn om een formulier op de client te genereren.
   * Een `URLSpec` object dat URI-waarden bevat die vereist zijn voor de Forms-service om een formulier te genereren.
   * Een `java.util.HashMap` object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt opgeven `null` of u geen bestanden aan het formulier wilt koppelen.
   De `renderPDFForm` methode retourneert een `FormsResult` object dat een formuliergegevensstroom bevat die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Maak een `com.adobe.idp.Document` object door de `FormsResult` methode van het `getOutputContent` object aan te roepen.
   * Haal het inhoudstype van het `com.adobe.idp.Document` object op door de `getContentType` methode ervan aan te roepen.
   * Stel het inhoudstype van het `javax.servlet.http.HttpServletResponse` object in door de bijbehorende `setContentType` methode op te roepen en het inhoudstype van het `com.adobe.idp.Document` object door te geven.
   * Maak een `javax.servlet.ServletOutputStream` object dat wordt gebruikt om de gegevensstroom van het formulier naar de webbrowser van de client te schrijven door de `javax.servlet.http.HttpServletResponse` methode van het `getOutputStream` object aan te roepen.
   * Maak een `java.io.InputStream` object door de `com.adobe.idp.Document` methode van het `getInputStream` object aan te roepen.
   * Maak een bytearray en vul deze met de formuliergegevensstroom door de methode van het `InputStream` `read` object aan te roepen en de bytearray als een argument door te geven.
   * Roep de `javax.servlet.ServletOutputStream` methode van het `write` object aan om de formuliergegevensstroom naar de webbrowser van de client te verzenden. Geef de bytearray door aan de `write` methode.

**Zie ook**

[Snel starten (SOAP-modus): Een formulier weergeven op de client met de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-a-form-at-the-client-using-the-java-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een formulier op de client renderen met de API voor webservices {#render-a-form-at-the-client-using-the-web-service-api}

Een formulier op de client renderen met de API voor formulieren (webservice):

1. Projectbestanden opnemen

   * Maak Java-proxyklassen die de Forms service WSDL gebruiken.
   * Neem de Java-proxyklassen op in het klassepad.

1. Een Forms Client API-object maken

   Maak een `FormsService` object en stel verificatiewaarden in.

1. Opties voor renderen tijdens runtime van client instellen

   * Maak een `PDFFormRenderSpec` object met de constructor ervan.
   * Stel de `RenderAtClient` runtime-optie in door de methode van het `PDFFormRenderSpec` object aan te roepen en de tekenreekswaarde door te geven `setRenderAtClient` `RenderAtClient.Yes`.

1. Een formulier weergeven op de client

   Roep de methode van het `FormsService` `renderPDFForm` object aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u verwijst naar een formulierontwerp dat deel uitmaakt van een Forms-toepassing, moet u controleren of u het volledige pad opgeeft, bijvoorbeeld `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Een `BLOB` object dat gegevens bevat die met het formulier moeten worden samengevoegd. Geef door als u geen gegevens wilt samenvoegen. `null` (Zie Formulieren [vooraf invullen met stroombare indelingen](/help/forms/developing/prepopulating-forms-flowable-layouts.md).)
   * Een `PDFFormRenderSpec` object dat uitvoeringsopties opslaat die vereist zijn om een formulier op de client te genereren.
   * Een `URLSpec` object dat URI-waarden bevat die door de service Forms worden vereist.
   * Een `java.util.HashMap` object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt opgeven `null` of u geen bestanden aan het formulier wilt koppelen.
   * Een leeg `com.adobe.idp.services.holders.BLOBHolder` object dat door de methode wordt gevuld. Met deze parameter wordt het gerenderde PDF-formulier opgeslagen.
   * Een leeg `javax.xml.rpc.holders.LongHolder` object dat door de methode wordt gevuld. (In dit argument wordt het aantal pagina&#39;s in het formulier opgeslagen).
   * Een leeg `javax.xml.rpc.holders.StringHolder` object dat door de methode wordt gevuld. (In dit argument wordt de waarde van de landinstelling opgeslagen.)
   * Een leeg `com.adobe.idp.services.holders.FormsResultHolder` object dat de resultaten van deze bewerking zal bevatten.
   De `renderPDFForm` methode vult het `com.adobe.idp.services.holders.FormsResultHolder` object dat als laatste argumentwaarde wordt doorgegeven, met een formuliergegevensstroom die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Maak een `FormResult` object door de waarde van het `com.adobe.idp.services.holders.FormsResultHolder` `value` gegevenslid van het object op te halen.
   * Maak een `BLOB` object dat formuliergegevens bevat door de `FormsResult` methode van het `getOutputContent` object aan te roepen.
   * Haal het inhoudstype van het `BLOB` object op door de `getContentType` methode ervan aan te roepen.
   * Stel het inhoudstype van het `javax.servlet.http.HttpServletResponse` object in door de bijbehorende `setContentType` methode op te roepen en het inhoudstype van het `BLOB` object door te geven.
   * Maak een `javax.servlet.ServletOutputStream` object dat wordt gebruikt om de gegevensstroom van het formulier naar de webbrowser van de client te schrijven door de `javax.servlet.http.HttpServletResponse` methode van het `getOutputStream` object aan te roepen.
   * Maak een bytearray en vul deze door de `BLOB` methode van het `getBinaryData` object aan te roepen. Hierdoor wordt de inhoud van het `FormsResult` object toegewezen aan de bytearray.
   * Roep de `javax.servlet.http.HttpServletResponse` methode van het `write` object aan om de formuliergegevensstroom naar de webbrowser van de client te verzenden. Geef de bytearray door aan de `write` methode.

**Zie ook**

[Formulieren weergeven op de client](#rendering-forms-at-the-client)

[AEM-formulieren aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
