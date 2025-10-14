---
title: Forms renderen op de client
description: Optimaliseer de levering van PDF-inhoud en verbeter de capaciteit van de Forms-service om netwerkbelasting af te handelen met behulp van de renderingmogelijkheden aan de clientzijde van Acrobat of Adobe Reader
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: e485980d-f200-46b7-9284-c9996003aa47
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services,APIs & Integrations
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '1690'
ht-degree: 0%

---

# Forms renderen op de client {#rendering-forms-at-the-client}

**de Steekproeven en de voorbeelden in dit document zijn slechts voor AEM Forms op milieu JEE.**

## Forms renderen op de client {#rendering-forms-at-the-client-inner}

U kunt de levering van PDF-inhoud optimaliseren en de mogelijkheid van de Forms-service om netwerkbelasting te verwerken verbeteren door de renderingmogelijkheden aan de clientzijde van Acrobat of Adobe Reader te gebruiken. Dit proces wordt het weergeven van een formulier op de client genoemd. Als u een formulier op de client wilt genereren, moet het clientapparaat (meestal een webbrowser) Acrobat 7.0 of Adobe Reader 7.0 of hoger gebruiken.

Wijzigingen in een formulier die het resultaat zijn van scriptuitvoering op de server, worden niet weerspiegeld in een formulier dat op de client wordt weergegeven, tenzij het basissubformulier het kenmerk `restoreState` bevat dat is ingesteld op `auto` . Voor meer informatie over dit attribuut, zie [&#x200B; Forms Designer.](https://www.adobe.com/go/learn_aemforms_designer_63)

>[!NOTE]
>
>Voor meer informatie over de dienst van Forms, zie [&#x200B; Verwijzing van de Diensten voor AEM Forms &#x200B;](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary-of-steps}

Als u een formulier op de client wilt genereren, voert u de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak een Forms Client API-object.
1. Opties voor renderen tijdens runtime van client instellen.
1. Een formulier weergeven op de client.
1. Schrijf het formulier naar de webbrowser van de client.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**creeer een voorwerp van Forms Cliënt API**

Voordat u programmatisch een client-API-bewerking voor Forms-services kunt uitvoeren, moet u een Forms-serviceclient maken. Maak een `FormsServiceClient` -object als u de Java API gebruikt. Maak een `FormsService` -object als u de Forms-API voor webservices gebruikt.

**plaats cliënt die runtime opties teruggeven**

Stel de optie voor het renderen van de client in om een formulier op de client te genereren door de optie voor `RenderAtClient` runtime in te stellen op `true` . Dit leidt ertoe dat het formulier wordt afgeleverd aan het clientapparaat waar het wordt gegenereerd. Als de waarde `RenderAtClient` `auto` (de standaardwaarde) is, bepaalt het formulierontwerp of het formulier op de client wordt gegenereerd. Het formulierontwerp moet een formulierontwerp met een stroombare indeling zijn.

Een optionele uitvoeringsoptie die u kunt instellen, is de optie `SeedPDF` . Met de optie `SeedPDF` wordt de container PDF (zaaddocument) gecombineerd met het formulierontwerp en de XML-gegevens. Zowel het formulierontwerp als de XML-gegevens worden geleverd aan Acrobat of Adobe Reader, waar het formulier wordt gegenereerd. De optie `SeedPDF` kan worden gebruikt wanneer de clientcomputer geen fonts heeft die in het formulier worden gebruikt, bijvoorbeeld wanneer een eindgebruiker geen licentie heeft voor het gebruik van een font dat de eigenaar van het formulier mag gebruiken.

U kunt Designer gebruiken om een eenvoudig dynamisch PDF-bestand te maken dat u kunt gebruiken als PDF-bestand. De volgende stappen zijn vereist om deze taak uit te voeren:

1. Bepaal of u lettertypen in het zaadbestand wilt insluiten. Het zaadbestand moet aanvullende fonts bevatten die zijn vereist voor het PDF-formulier dat wordt gegenereerd. Wanneer u lettertypen insluit in het zaadbestand PDF, moet u ervoor zorgen dat u geen licentieovereenkomsten voor lettertypen schendt. In Designer kunt u bepalen of u lettertypen wettelijk kunt insluiten. Als er bij het opslaan fonts zijn die u niet in het formulier kunt insluiten, geeft Designer een bericht weer met de fonts die u niet kunt insluiten. Dit bericht wordt niet weergegeven in Designer voor statische PDF-documenten.
1. Als u het zaadbestand in Designer maakt, is het raadzaam ten minste een tekstveld toe te voegen dat een bericht bevat. Het bericht moet worden gericht aan gebruikers van eerdere versies van Adobe Reader en aangeven dat ze Acrobat 7.0 of hoger of Adobe Reader 7.0 of hoger nodig hebben om het document te kunnen bekijken.
1. Sla het zaadbestand op als een dynamisch PDF-PDF-bestand met de extensie van het PDF-bestand.

>[!NOTE]
>
>U hoeft de PDF runtime-optie voor het genereren van een formulier op de client niet te definiëren. Als u geen PDF opgeeft, maakt de Forms-service een shell-pdf die geen COS-objecten bevat maar wel een PDF-omloop met daarin de daadwerkelijke XDP-inhoud ingesloten. In de stappen in deze sectie wordt de PDF-runtime-optie voor zaaizaad niet ingesteld. Zie de handleiding Adobe PDF Reference voor informatie over COS-objecten.

**geeft een vorm bij de cliënt terug**

Als u een formulier op de client wilt genereren, moet u ervoor zorgen dat de renderopties voor de client in de toepassingslogica zijn opgenomen om een formulier te genereren.

**schrijf de stroom van vormgegevens aan cliëntWeb browser**

De Forms-service maakt een formuliergegevensstroom die u naar de webbrowser van de client moet schrijven. Als het formulier wordt geschreven naar de webbrowser van de client, wordt het gegenereerd door Acrobat 7.0 of Adobe Reader 7.0 of hoger en is het zichtbaar voor de gebruiker.

**zie ook**

[Een formulier op de client renderen met de Java API](#render-a-form-at-the-client-using-the-java-api)

[Een formulier op de client renderen met de API voor webservices](#render-a-form-at-the-client-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Forms Service API Quick Start](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Documenten doorgeven aan de Forms-service](/help/forms/developing/passing-documents-forms-service.md)

[Webtoepassingen maken die Forms renderen](/help/forms/developing/creating-web-applications-renders-forms.md)

### Een formulier op de client renderen met de Java API {#render-a-form-at-the-client-using-the-java-api}

Een formulier op de client renderen met de Forms API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-forms-client.jar, op in het klassenpad van uw Java-project.

1. Een Forms Client API-object maken

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `FormsServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Opties voor renderen tijdens runtime van client instellen

   * Maak een `PDFFormRenderSpec` -object met behulp van de constructor.
   * Stel de optie `RenderAtClient` runtime in door de methode `PDFFormRenderSpec` object `setRenderAtClient` aan te roepen en de opsommingswaarde `RenderAtClient.Yes` door te geven.

1. Een formulier weergeven op de client

   Roep de methode `renderPDFForm` van het object `FormsServiceClient` aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u verwijst naar een formulierontwerp dat deel uitmaakt van een AEM Forms-toepassing, moet u het volledige pad opgeven, bijvoorbeeld `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp` .
   * Een `com.adobe.idp.Document` -object dat gegevens bevat die met het formulier moeten worden samengevoegd. Wanneer u geen gegevens wilt samenvoegen, geeft u een leeg `com.adobe.idp.Document` -object door.
   * Een `PDFFormRenderSpec` -object dat uitvoeringsopties opslaat die vereist zijn om een formulier op de client te genereren.
   * Een `URLSpec` -object dat URI-waarden bevat die door de Forms-service worden vereist om een formulier te genereren.
   * Een `java.util.HashMap` -object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt `null` opgeven als u geen bestanden aan het formulier wilt koppelen.

   De methode `renderPDFForm` retourneert een `FormsResult` -object dat een formuliergegevensstroom bevat die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Maak een `com.adobe.idp.Document` -object door de methode `FormsResult` object &#39;s `getOutputContent` aan te roepen.
   * Haal het inhoudstype van het object `com.adobe.idp.Document` op door de methode `getContentType` ervan aan te roepen.
   * Stel het inhoudstype van het `javax.servlet.http.HttpServletResponse` -object in door de methode `setContentType` ervan aan te roepen en het inhoudstype van het `com.adobe.idp.Document` -object door te geven.
   * Maak een `javax.servlet.ServletOutputStream` -object dat wordt gebruikt om de formuliergegevensstroom naar de webbrowser van de client te schrijven door de methode `javax.servlet.http.HttpServletResponse` object `getOutputStream` aan te roepen.
   * Maak een `java.io.InputStream` -object door de methode `com.adobe.idp.Document` object `getInputStream` aan te roepen.
   * Maak een bytearray en vul deze met de formuliergegevensstroom door de methode `read` van het object `InputStream` aan te roepen en de bytearray als een argument door te geven.
   * Roep de methode `write` van het object `javax.servlet.ServletOutputStream` aan om de gegevensstroom van het formulier naar de webbrowser van de client te verzenden. Geef de bytearray door aan de methode `write` .

**zie ook**

[Snel starten (SOAP modus): Een formulier op de client genereren met de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-a-form-at-the-client-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een formulier op de client renderen met de API voor webservices {#render-a-form-at-the-client-using-the-web-service-api}

Een formulier op de client renderen met de Forms API (webservice):

1. Projectbestanden opnemen

   * Maak Java-proxyklassen die gebruikmaken van de Forms-service WSDL.
   * Neem de Java-proxyklassen op in het klassepad.

1. Een Forms Client API-object maken

   Maak een `FormsService` -object en stel de verificatiewaarden in.

1. Opties voor renderen tijdens runtime van client instellen

   * Maak een `PDFFormRenderSpec` -object met behulp van de constructor.
   * Stel de optie `RenderAtClient` runtime in door de methode `PDFFormRenderSpec` object `setRenderAtClient` aan te roepen en de tekenreekswaarde `RenderAtClient.Yes` door te geven.

1. Een formulier weergeven op de client

   Roep de methode `renderPDFForm` van het object `FormsService` aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u verwijst naar een formulierontwerp dat deel uitmaakt van een Forms-toepassing, moet u het volledige pad opgeven, bijvoorbeeld `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp` .
   * Een `BLOB` -object dat gegevens bevat die met het formulier moeten worden samengevoegd. Geef `null` door als u geen gegevens wilt samenvoegen. (Zie [&#x200B; Prepopulating Forms met Stroombare Lay-outs &#x200B;](/help/forms/developing/prepopulating-forms-flowable-layouts.md).)
   * Een `PDFFormRenderSpec` -object dat uitvoeringsopties opslaat die vereist zijn om een formulier op de client te genereren.
   * Een `URLSpec` -object dat URI-waarden bevat die door de Forms-service worden vereist.
   * Een `java.util.HashMap` -object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt `null` opgeven als u geen bestanden aan het formulier wilt koppelen.
   * Een leeg `com.adobe.idp.services.holders.BLOBHolder` -object dat door de methode wordt gevuld. Met deze parameter wordt het weergegeven PDF-formulier opgeslagen.
   * Een leeg `javax.xml.rpc.holders.LongHolder` -object dat door de methode wordt gevuld. (In dit argument wordt het aantal pagina&#39;s in het formulier opgeslagen).
   * Een leeg `javax.xml.rpc.holders.StringHolder` -object dat door de methode wordt gevuld. (In dit argument wordt de waarde van de landinstelling opgeslagen.)
   * Een leeg `com.adobe.idp.services.holders.FormsResultHolder` -object dat de resultaten van deze bewerking bevat.

   Met de methode `renderPDFForm` wordt het `com.adobe.idp.services.holders.FormsResultHolder` -object dat als laatste argumentwaarde wordt doorgegeven, gevuld met een formuliergegevensstroom die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Maak een `FormResult` -object door de waarde van het gegevenslid van het `com.adobe.idp.services.holders.FormsResultHolder` object `value` op te halen.
   * Maak een `BLOB` -object dat formuliergegevens bevat door de methode `FormsResult` object `getOutputContent` aan te roepen.
   * Haal het inhoudstype van het object `BLOB` op door de methode `getContentType` ervan aan te roepen.
   * Stel het inhoudstype van het `javax.servlet.http.HttpServletResponse` -object in door de methode `setContentType` ervan aan te roepen en het inhoudstype van het `BLOB` -object door te geven.
   * Maak een `javax.servlet.ServletOutputStream` -object dat wordt gebruikt om de formuliergegevensstroom naar de webbrowser van de client te schrijven door de methode `javax.servlet.http.HttpServletResponse` object `getOutputStream` aan te roepen.
   * Maak een bytearray en vul deze door de methode `getBinaryData` van het object `BLOB` aan te roepen. Hierdoor wordt de inhoud van het `FormsResult` -object toegewezen aan de bytearray.
   * Roep de methode `write` van het object `javax.servlet.http.HttpServletResponse` aan om de gegevensstroom van het formulier naar de webbrowser van de client te verzenden. Geef de bytearray door aan de methode `write` .

**zie ook**

[Forms renderen op de client](#rendering-forms-at-the-client)

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
