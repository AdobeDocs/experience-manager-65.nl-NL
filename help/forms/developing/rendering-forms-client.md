---
title: Forms renderen op de client
seo-title: Forms renderen op de client
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
workflow-type: tm+mt
source-wordcount: '1664'
ht-degree: 0%

---


# Forms renderen op de client {#rendering-forms-at-the-client}

## Forms renderen op de client {#rendering-forms-at-the-client-inner}

U kunt de levering van PDF-inhoud optimaliseren en het vermogen van de Forms-service om netwerkbelasting te verwerken verbeteren door de renderingmogelijkheden op de client van Acrobat of Adobe Reader te gebruiken. Dit proces wordt een formulier op de client weergegeven. Als u een formulier op de client wilt genereren, moet het clientapparaat (meestal een webbrowser) Acrobat 7.0 of Adobe Reader 7.0 of hoger gebruiken.

Wijzigingen in een formulier die het resultaat zijn van scriptuitvoering op de server worden niet weerspiegeld in een formulier dat op de client wordt weergegeven, tenzij het basissubformulier het kenmerk `restoreState` bevat dat is ingesteld op `auto`. Zie [Forms Designer ](https://www.adobe.com/go/learn_aemforms_designer_63) voor meer informatie over dit kenmerk.

>[!NOTE]
>
>Zie [Referentiehandleiding voor services voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63) voor meer informatie over de Forms-service.

### Overzicht van stappen {#summary-of-steps}

Voer de volgende taken uit om een formulier op de client te genereren:

1. Inclusief projectbestanden.
1. Maak een Forms Client API-object.
1. Opties voor renderen tijdens runtime van client instellen.
1. Een formulier weergeven op de client.
1. Schrijf het formulier naar de webbrowser van de client.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**Een Forms Client API-object maken**

Voordat u programmatisch een client-API-bewerking voor Forms-services kunt uitvoeren, moet u een Forms-serviceclient maken. Als u de Java API gebruikt, maakt u een `FormsServiceClient`-object. Als u de Forms-API voor webservices gebruikt, maakt u een `FormsService`-object.

**Opties voor renderen tijdens runtime van client instellen**

U moet de runtime-optie voor de rendering van clients instellen om een formulier op de client te genereren door de runtimeoptie `RenderAtClient` in te stellen op `true`. Dit leidt ertoe dat het formulier wordt afgeleverd aan het clientapparaat waar het wordt gegenereerd. Als `RenderAtClient` `auto` (de standaardwaarde) is, bepaalt het formulierontwerp of het formulier op de client wordt gegenereerd. Het formulierontwerp moet een formulierontwerp met een stroombare indeling zijn.

Een optionele uitvoeringsoptie die u kunt instellen, is de optie `SeedPDF`. Met de optie `SeedPDF` wordt de PDF-container (PDF-zaaddocument) gecombineerd met het formulierontwerp en de XML-gegevens. Zowel het formulierontwerp als de XML-gegevens worden geleverd aan Acrobat of Adobe Reader, waar het formulier wordt gegenereerd. De optie `SeedPDF` kan worden gebruikt wanneer de clientcomputer geen fonts heeft die in het formulier worden gebruikt, bijvoorbeeld wanneer een eindgebruiker geen licentie heeft voor het gebruik van een font dat de eigenaar van het formulier mag gebruiken.

U kunt Designer gebruiken om een eenvoudig dynamisch PDF-bestand te maken dat u als PDF-bestand met zaad kunt gebruiken. De volgende stappen zijn vereist om deze taak uit te voeren:

1. Bepaal of u fonts in het PDF-bestand met zaad wilt insluiten. Het PDF-bestand met het zaadbestand moet aanvullende fonts bevatten die vereist zijn voor het formulier dat wordt gegenereerd. Wanneer u lettertypen insluit in het PDF-bestand voor het zaadbestand, moet u ervoor zorgen dat u geen licentieovereenkomsten voor lettertypen schendt. In Designer kunt u bepalen of u fonts wettelijk kunt insluiten. Als er fonts zijn die u niet in het formulier kunt insluiten wanneer u het opslaat, wordt in Designer een bericht weergegeven met de fonts die u niet kunt insluiten. Dit bericht wordt niet weergegeven in Designer voor statische PDF-documenten.
1. Als u het PDF-zaadbestand maakt in Designer, wordt u geadviseerd ten minste een tekstveld toe te voegen dat een bericht bevat. Het bericht moet worden gericht aan gebruikers van eerdere versies van Adobe Reader en aangeven dat ze Acrobat 7.0 of hoger of Adobe Reader 7.0 of hoger nodig hebben om het document te kunnen bekijken.
1. Sla het PDF-zaadbestand op als een dynamisch PDF-bestand met de bestandsnaamextensie PDF.

>[!NOTE]
>
>U hoeft de optie PDF-runtime voor het genereren van een formulier op de client niet te definiëren. Als u geen PDF-bestand voor een zaadbestand opgeeft, maakt de Forms-service een shell-pdf die geen COS-objecten bevat maar wel een PDF-omslag met daarin de daadwerkelijke XDP-inhoud ingesloten. Met de stappen in deze sectie wordt de optie voor het uitvoeren van de PDF-zaadbewerking niet ingesteld. Zie de handleiding Adobe PDF Reference voor informatie over COS-objecten.

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

   * Maak een `ServiceClientFactory`-object dat verbindingseigenschappen bevat.
   * Maak een `FormsServiceClient`-object door de constructor ervan te gebruiken en het object `ServiceClientFactory` door te geven.

1. Opties voor renderen tijdens runtime van client instellen

   * Maak een `PDFFormRenderSpec`-object met de constructor ervan.
   * Stel de uitvoeringsoptie `RenderAtClient` in door de methode `setRenderAtClient` van het object `PDFFormRenderSpec` aan te roepen en de opsommingswaarde `RenderAtClient.Yes` door te geven.

1. Een formulier weergeven op de client

   Roep de methode `renderPDFForm` van het object `FormsServiceClient` aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u naar een formulierontwerp verwijst dat deel uitmaakt van een AEM Forms-toepassing, moet u het volledige pad opgeven, bijvoorbeeld `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Een object `com.adobe.idp.Document` dat gegevens bevat die met het formulier moeten worden samengevoegd. Als u geen gegevens wilt samenvoegen, geeft u een leeg `com.adobe.idp.Document`-object door.
   * Een `PDFFormRenderSpec`-object dat uitvoeringsopties opslaat die vereist zijn om een formulier op de client te genereren.
   * Een object `URLSpec` dat URI-waarden bevat die door de Forms-service zijn vereist om een formulier te genereren.
   * Een `java.util.HashMap`-object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt `null` opgeven als u geen bestanden aan het formulier wilt koppelen.

   De methode `renderPDFForm` retourneert een `FormsResult`-object dat een formuliergegevensstroom bevat die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Maak een `com.adobe.idp.Document`-object door de methode `getOutputContent` van het object aan te roepen.`FormsResult`
   * Hiermee wordt het inhoudstype van het object `com.adobe.idp.Document` opgehaald door de methode `getContentType` ervan aan te roepen.
   * Stel het inhoudstype van het object `javax.servlet.http.HttpServletResponse` in door de methode `setContentType` ervan aan te roepen en het inhoudstype van het object `com.adobe.idp.Document` door te geven.
   * Maak een `javax.servlet.ServletOutputStream`-object dat wordt gebruikt om de formuliergegevensstroom naar de webbrowser van de client te schrijven door de methode `javax.servlet.http.HttpServletResponse` van het object `getOutputStream` aan te roepen.
   * Maak een `java.io.InputStream`-object door de methode `getInputStream` van het object `com.adobe.idp.Document` aan te roepen.
   * Maak een bytearray en vul deze met de formuliergegevensstroom door de methode `read` van het object `InputStream` aan te roepen en de bytearray als een argument door te geven.
   * Roep de methode `javax.servlet.ServletOutputStream` van het object `write` aan om de gegevensstroom van het formulier naar de webbrowser van de client te verzenden. Geef de bytearray door aan de methode `write`.

**Zie ook**

[Snel starten (SOAP-modus): Een formulier weergeven op de client met de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-a-form-at-the-client-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een formulier op de client renderen met de webservice-API {#render-a-form-at-the-client-using-the-web-service-api}

Een formulier op de client renderen met de Forms API (webservice):

1. Projectbestanden opnemen

   * Maak Java-proxyklassen die gebruikmaken van de Forms-service WSDL.
   * Neem de Java-proxyklassen op in het klassepad.

1. Een Forms Client API-object maken

   Maak een `FormsService`-object en stel de verificatiewaarden in.

1. Opties voor renderen tijdens runtime van client instellen

   * Maak een `PDFFormRenderSpec`-object met de constructor ervan.
   * Stel de runtimeoptie `RenderAtClient` in door de methode `setRenderAtClient` van het object `PDFFormRenderSpec` aan te roepen en de tekenreekswaarde `RenderAtClient.Yes` door te geven.

1. Een formulier weergeven op de client

   Roep de methode `renderPDFForm` van het object `FormsService` aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u naar een formulierontwerp verwijst dat deel uitmaakt van een Forms-toepassing, moet u het volledige pad opgeven, bijvoorbeeld `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Een object `BLOB` dat gegevens bevat die met het formulier moeten worden samengevoegd. Als u geen gegevens wilt samenvoegen, geeft u `null` door. (Zie [Forms vooraf vullen met stroombare layouts](/help/forms/developing/prepopulating-forms-flowable-layouts.md).)
   * Een `PDFFormRenderSpec`-object dat uitvoeringsopties opslaat die vereist zijn om een formulier op de client te genereren.
   * Een object `URLSpec` dat URI-waarden bevat die door de Forms-service worden vereist.
   * Een `java.util.HashMap`-object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt `null` opgeven als u geen bestanden aan het formulier wilt koppelen.
   * Een leeg object `com.adobe.idp.services.holders.BLOBHolder` dat door de methode is gevuld. Met deze parameter wordt het gerenderde PDF-formulier opgeslagen.
   * Een leeg object `javax.xml.rpc.holders.LongHolder` dat door de methode is gevuld. (In dit argument wordt het aantal pagina&#39;s in het formulier opgeslagen).
   * Een leeg object `javax.xml.rpc.holders.StringHolder` dat door de methode is gevuld. (In dit argument wordt de waarde van de landinstelling opgeslagen.)
   * Een leeg `com.adobe.idp.services.holders.FormsResultHolder`-object dat de resultaten van deze bewerking zal bevatten.

   Met de methode `renderPDFForm` wordt het object `com.adobe.idp.services.holders.FormsResultHolder` dat als laatste argumentwaarde is doorgegeven, gevuld met een formuliergegevensstroom die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Maak een `FormResult`-object door de waarde op te halen van het `com.adobe.idp.services.holders.FormsResultHolder`-gegevenslid van het object.`value`
   * Maak een `BLOB`-object dat formuliergegevens bevat door de methode `getOutputContent` van het object `FormsResult` aan te roepen.
   * Hiermee wordt het inhoudstype van het object `BLOB` opgehaald door de methode `getContentType` ervan aan te roepen.
   * Stel het inhoudstype van het object `javax.servlet.http.HttpServletResponse` in door de methode `setContentType` ervan aan te roepen en het inhoudstype van het object `BLOB` door te geven.
   * Maak een `javax.servlet.ServletOutputStream`-object dat wordt gebruikt om de formuliergegevensstroom naar de webbrowser van de client te schrijven door de methode `javax.servlet.http.HttpServletResponse` van het object `getOutputStream` aan te roepen.
   * Maak een bytearray en vul deze door de methode `getBinaryData` van het object `BLOB` aan te roepen. Deze taak wijst de inhoud van het `FormsResult` voorwerp aan de byteserie toe.
   * Roep de methode `javax.servlet.http.HttpServletResponse` van het object `write` aan om de gegevensstroom van het formulier naar de webbrowser van de client te verzenden. Geef de bytearray door aan de methode `write`.

**Zie ook**

[Forms renderen op de client](#rendering-forms-at-the-client)

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
