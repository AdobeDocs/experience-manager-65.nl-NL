---
title: Forms renderen op de client
seo-title: Rendering Forms at the Client
description: Optimaliseer de levering van PDF-inhoud en verbeter de capaciteit van de Forms-service om netwerkbelasting af te handelen met behulp van de renderingmogelijkheden aan de clientzijde van Acrobat of Adobe Reader
seo-description: Optimize the delivery of PDF content and improve the Forms service’s ability to handle network load by using the client-side rendering capability of Acrobat or Adobe Reader
uuid: 09bcc23d-28b0-473a-87f1-bc17e87620f4
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 08d36e9f-cafc-478e-9781-8fc29ac6262e
role: Developer
exl-id: e485980d-f200-46b7-9284-c9996003aa47
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1698'
ht-degree: 0%

---

# Forms renderen op de client {#rendering-forms-at-the-client}

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

## Forms renderen op de client {#rendering-forms-at-the-client-inner}

U kunt de levering van PDF-inhoud optimaliseren en de mogelijkheid van de Forms-service om netwerkbelasting te verwerken verbeteren door de renderingmogelijkheden aan de clientzijde van Acrobat of Adobe Reader te gebruiken. Dit proces wordt een formulier op de client weergegeven. Als u een formulier op de client wilt genereren, moet het clientapparaat (meestal een webbrowser) Acrobat 7.0 of Adobe Reader 7.0 of hoger gebruiken.

Wijzigingen in een formulier die het resultaat zijn van scriptuitvoering op de server, worden niet weerspiegeld in een formulier dat op de client wordt gegenereerd, tenzij het basissubformulier het `restoreState` kenmerk dat is ingesteld op `auto`. Zie voor meer informatie over dit kenmerk [Forms Designer.](https://www.adobe.com/go/learn_aemforms_designer_63)

>[!NOTE]
>
>Ga voor meer informatie over de Forms-service naar [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

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

Voordat u programmatisch een client-API-bewerking voor Forms-services kunt uitvoeren, moet u een Forms-serviceclient maken. Als u de Java API gebruikt, maakt u een `FormsServiceClient` object. Als u de Forms-webservice-API gebruikt, maakt u een `FormsService` object.

**Opties voor renderen tijdens runtime van client instellen**

U moet de optie voor het renderen van de client zo instellen dat een formulier op de client wordt gegenereerd door de instelling van de optie `RenderAtClient` runtime-optie voor `true`. Dit leidt ertoe dat het formulier wordt afgeleverd aan het clientapparaat waar het wordt gegenereerd. Indien `RenderAtClient` is `auto` (de standaardwaarde) bepaalt het formulierontwerp of het formulier op de client wordt gegenereerd. Het formulierontwerp moet een formulierontwerp met een stroombare indeling zijn.

Een optionele uitvoeringsoptie die u kunt instellen, is de `SeedPDF` optie. De `SeedPDF` Deze optie combineert de container PDF (zaaddocument) met het formulierontwerp en de XML-gegevens. Zowel het formulierontwerp als de XML-gegevens worden geleverd aan Acrobat of Adobe Reader, waar het formulier wordt gegenereerd. De `SeedPDF` Deze optie kan worden gebruikt wanneer de clientcomputer geen fonts heeft die in het formulier worden gebruikt, bijvoorbeeld wanneer een eindgebruiker geen licentie heeft voor het gebruik van een font dat de eigenaar van het formulier mag gebruiken.

U kunt Designer gebruiken om een eenvoudig dynamisch PDF-bestand te maken dat u kunt gebruiken als een PDF-bestand. De volgende stappen zijn vereist om deze taak uit te voeren:

1. Bepaal of u lettertypen in het PDF-bestand voor zaaizaad wilt insluiten. Het zaadbestand moet aanvullende fonts bevatten die zijn vereist voor het PDF-formulier dat wordt gegenereerd. Wanneer u lettertypen insluit in het zaadbestand PDF, moet u ervoor zorgen dat u geen licentieovereenkomsten voor lettertypen schendt. In Designer kunt u bepalen of u fonts wettelijk kunt insluiten. Als er fonts zijn die u niet in het formulier kunt insluiten wanneer u het opslaat, wordt in Designer een bericht weergegeven met de fonts die u niet kunt insluiten. Dit bericht wordt niet weergegeven in Designer voor statische PDF-documenten.
1. Als u het zaadbestand in Designer maakt, wordt u geadviseerd ten minste een tekstveld toe te voegen dat een bericht bevat. Het bericht moet worden gericht aan gebruikers van eerdere versies van Adobe Reader en aangeven dat ze Acrobat 7.0 of hoger of Adobe Reader 7.0 of hoger nodig hebben om het document te kunnen bekijken.
1. Sla het zaadbestand op als een dynamisch PDF-PDF-bestand met de extensie van het PDF-bestand.

>[!NOTE]
>
>U hoeft de PDF runtime-optie voor het genereren van een formulier op de client niet te definiëren. Als u geen PDF opgeeft, maakt de Forms-service een shell-pdf die geen COS-objecten bevat maar wel een PDF-omloop met daarin de daadwerkelijke XDP-inhoud ingesloten. In de stappen in deze sectie wordt de PDF-runtime-optie voor zaaizaad niet ingesteld. Zie de handleiding Adobe PDF Reference voor informatie over COS-objecten.

**Een formulier weergeven op de client**

Als u een formulier op de client wilt genereren, moet u ervoor zorgen dat de renderopties voor de client in de toepassingslogica zijn opgenomen om een formulier te genereren.

**De formuliergegevensstroom naar de webbrowser van de client schrijven**

De Forms-service maakt een formuliergegevensstroom die u naar de webbrowser van de client moet schrijven. Als het formulier wordt geschreven naar de webbrowser van de client, wordt het gegenereerd door Acrobat 7.0 of Adobe Reader 7.0 of hoger en is het zichtbaar voor de gebruiker.

**Zie ook**

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

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `FormsServiceClient` object door de constructor ervan te gebruiken en door te geven `ServiceClientFactory` object.

1. Opties voor renderen tijdens runtime van client instellen

   * Een `PDFFormRenderSpec` object met behulp van de constructor.
   * Stel de `RenderAtClient` runtime-optie door het aanroepen van de `PDFFormRenderSpec` object `setRenderAtClient` methode en het doorgeven van de opsommingswaarde `RenderAtClient.Yes`.

1. Een formulier weergeven op de client

   De `FormsServiceClient` object `renderPDFForm` en geeft de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u naar een formulierontwerp verwijst dat deel uitmaakt van een AEM Forms-toepassing, moet u het volledige pad opgeven, zoals `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `com.adobe.idp.Document` object dat gegevens bevat die met het formulier moeten worden samengevoegd. Als u geen gegevens wilt samenvoegen, geeft u een lege waarde door `com.adobe.idp.Document` object.
   * A `PDFFormRenderSpec` -object dat uitvoeringsopties opslaat die vereist zijn om een formulier op de client te genereren.
   * A `URLSpec` object dat URI-waarden bevat die door de Forms-service worden vereist om een formulier te genereren.
   * A `java.util.HashMap` object waarin bestandsbijlagen zijn opgeslagen. Dit is een optionele parameter en u kunt `null` als u geen bestanden aan het formulier wilt koppelen.

   De `renderPDFForm` methode retourneert een `FormsResult` object dat een formuliergegevensstroom bevat die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Een `com.adobe.idp.Document` door het object aan te roepen `FormsResult` object &#39;s `getOutputContent` methode.
   * Hiermee wordt het inhoudstype van het dialoogvenster `com.adobe.idp.Document` object aanroepen `getContentType` methode.
   * Stel de `javax.servlet.http.HttpServletResponse` inhoudstype van object aanroepen `setContentType` en geeft u het inhoudstype van het dialoogvenster door `com.adobe.idp.Document` object.
   * Een `javax.servlet.ServletOutputStream` object dat wordt gebruikt om de formuliergegevensstroom naar de webbrowser van de client te schrijven door het aanroepen van de `javax.servlet.http.HttpServletResponse` object `getOutputStream` methode.
   * Een `java.io.InputStream` door het object aan te roepen `com.adobe.idp.Document` object `getInputStream` methode.
   * Maak een bytearray en vul deze met de formuliergegevensstroom door de `InputStream` object `read` en de bytearray doorgeven als een argument.
   * De `javax.servlet.ServletOutputStream` object `write` methode om de formuliergegevensstroom naar de webbrowser van de client te verzenden. Geef de bytearray door aan de `write` methode.

**Zie ook**

[Snel starten (SOAP-modus): Een formulier weergeven op de client met de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-a-form-at-the-client-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een formulier op de client renderen met de API voor webservices {#render-a-form-at-the-client-using-the-web-service-api}

Een formulier op de client renderen met de Forms API (webservice):

1. Projectbestanden opnemen

   * Maak Java-proxyklassen die gebruikmaken van de Forms-service WSDL.
   * Neem de Java-proxyklassen op in het klassepad.

1. Een Forms Client API-object maken

   Een `FormsService` -object en stel verificatiewaarden in.

1. Opties voor renderen tijdens runtime van client instellen

   * Een `PDFFormRenderSpec` object met behulp van de constructor.
   * Stel de `RenderAtClient` runtime-optie door het aanroepen van de `PDFFormRenderSpec` object `setRenderAtClient` methode en het doorgeven van de tekenreekswaarde `RenderAtClient.Yes`.

1. Een formulier weergeven op de client

   De `FormsService` object `renderPDFForm` en geeft de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u naar een formulierontwerp verwijst dat deel uitmaakt van een Forms-toepassing, moet u het volledige pad opgeven, zoals `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `BLOB` object dat gegevens bevat die met het formulier moeten worden samengevoegd. Als u geen gegevens wilt samenvoegen, geeft u door `null`. (Zie [Forms vooraf vullen met stroombare indelingen](/help/forms/developing/prepopulating-forms-flowable-layouts.md).)
   * A `PDFFormRenderSpec` -object dat uitvoeringsopties opslaat die vereist zijn om een formulier op de client te genereren.
   * A `URLSpec` object dat URI-waarden bevat die door de Forms-service worden vereist.
   * A `java.util.HashMap` object waarin bestandsbijlagen zijn opgeslagen. Dit is een optionele parameter en u kunt `null` als u geen bestanden aan het formulier wilt koppelen.
   * Een leeg `com.adobe.idp.services.holders.BLOBHolder` object dat door de methode wordt gevuld. Deze parameter wordt gebruikt om het weergegeven PDF formulier op te slaan.
   * Een leeg `javax.xml.rpc.holders.LongHolder` object dat door de methode wordt gevuld. (In dit argument wordt het aantal pagina&#39;s in het formulier opgeslagen).
   * Een leeg `javax.xml.rpc.holders.StringHolder` object dat door de methode wordt gevuld. (In dit argument wordt de waarde van de landinstelling opgeslagen.)
   * Een leeg `com.adobe.idp.services.holders.FormsResultHolder` -object dat de resultaten van deze bewerking bevat.

   De `renderPDFForm` wordt de `com.adobe.idp.services.holders.FormsResultHolder` object dat wordt doorgegeven als de laatste argumentwaarde met een formuliergegevensstroom die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Een `FormResult` object door de waarde van het object op te halen `com.adobe.idp.services.holders.FormsResultHolder` object `value` lid.
   * Een `BLOB` object dat formuliergegevens bevat door het `FormsResult` object `getOutputContent` methode.
   * Hiermee wordt het inhoudstype van het dialoogvenster `BLOB` object aanroepen `getContentType` methode.
   * Stel de `javax.servlet.http.HttpServletResponse` inhoudstype van object aanroepen `setContentType` en geeft u het inhoudstype van het dialoogvenster door `BLOB` object.
   * Een `javax.servlet.ServletOutputStream` object dat wordt gebruikt om de formuliergegevensstroom naar de webbrowser van de client te schrijven door het aanroepen van de `javax.servlet.http.HttpServletResponse` object `getOutputStream` methode.
   * Maak een bytearray en vul deze door het `BLOB` object `getBinaryData` methode. Deze taak wijst de inhoud van toe `FormsResult` object naar de bytearray.
   * De `javax.servlet.http.HttpServletResponse` object `write` methode om de formuliergegevensstroom naar de webbrowser van de client te verzenden. Geef de bytearray door aan de `write` methode.

**Zie ook**

[Forms renderen op de client](#rendering-forms-at-the-client)

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
