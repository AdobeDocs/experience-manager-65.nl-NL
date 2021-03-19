---
title: Forms renderen op waarde
seo-title: Forms renderen op waarde
description: Met de Forms API (Java) kunt u een formulier op waarde weergeven met de API voor Java API en Web Service.
seo-description: Met de Forms API (Java) kunt u een formulier op waarde weergeven met de API voor Java API en Web Service.
uuid: b932cc54-662f-40ae-94e0-20ac82845f3b
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: ddbb2b82-4c57-4845-a5be-2435902d312b
role: Developer
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1863'
ht-degree: 0%

---


# Forms renderen op waarde {#rendering-forms-by-value}

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

Een formulierontwerp dat in Designer is gemaakt, wordt meestal doorgegeven via de Forms-service. Formulierontwerpen kunnen groot zijn en daarom is het efficiënter om ze door te geven als verwijzing, zodat het niet nodig is om bytes in het formulierontwerp op waarde te rangschikken. De Forms-service kan het formulierontwerp ook in cache plaatsen, zodat het formulierontwerp niet voortdurend hoeft te worden gelezen wanneer het in cache wordt geplaatst.

Als een formulierontwerp een UUID-kenmerk bevat, wordt het in de cache opgeslagen. De UUID-waarde is uniek voor alle formulierontwerpen en wordt gebruikt om een formulier op unieke wijze te identificeren. Als u een formulier op waarde weergeeft, mag het formulier alleen in de cache worden geplaatst wanneer het herhaaldelijk wordt gebruikt. Als het formulier echter niet herhaaldelijk wordt gebruikt en uniek moet zijn, kunt u voorkomen dat het formulier in cache wordt geplaatst met behulp van cacheopties die zijn ingesteld met de AEM Forms API.

De Forms-service kan ook de locatie van gekoppelde inhoud in het formulierontwerp oplossen. Bijvoorbeeld: gekoppelde afbeeldingen waarnaar in het formulierontwerp wordt verwezen, zijn relatieve URL&#39;s. Gekoppelde inhoud wordt altijd verondersteld relatief te zijn ten opzichte van de locatie van het formulierontwerp. Daarom is het oplossen van gekoppelde inhoud een kwestie van het bepalen van zijn plaats door de relatieve weg op de absolute plaats van het vormontwerp toe te passen.

In plaats van een formulierontwerp door te geven als referentie, kunt u een formulierontwerp op waarde doorgeven. Het doorgeven van een formulierontwerp op basis van waarde is efficiënt wanneer een formulierontwerp dynamisch wordt gemaakt. Dat wil zeggen, wanneer een clienttoepassing de XML genereert die tijdens runtime een formulierontwerp maakt. In dit geval wordt een formulierontwerp niet opgeslagen in een fysieke opslagplaats, omdat het in het geheugen wordt opgeslagen. Als u tijdens de runtime dynamisch een formulierontwerp maakt en dit op waarde doorgeeft, kunt u het formulier in cache plaatsen en de prestaties van de Forms-service verbeteren.

**Beperkingen bij het doorgeven van een formulier op waarde**

De volgende beperkingen zijn van toepassing wanneer een formulierontwerp wordt doorgegeven als waarde:

* Het formulierontwerp kan geen relatieve gekoppelde inhoud bevatten. Alle afbeeldingen en fragmenten moeten in het formulierontwerp worden ingesloten of absoluut worden vermeld.
* Berekeningen aan de serverzijde kunnen niet worden uitgevoerd nadat het formulier is gegenereerd. Als het formulier wordt teruggestuurd naar de Forms-service, worden de gegevens opgehaald en geretourneerd zonder berekeningen aan de serverzijde.
* Omdat HTML gekoppelde afbeeldingen alleen tijdens runtime kan gebruiken, is het niet mogelijk om HTML met ingesloten afbeeldingen te genereren. De reden hiervoor is dat de Forms-service ingesloten afbeeldingen met HTML ondersteunt door de afbeeldingen op te halen uit een formulierontwerp waarnaar wordt verwezen. Omdat een formulierontwerp dat op waarde wordt doorgegeven, geen locatie heeft waarnaar wordt verwezen, kunnen ingesloten afbeeldingen niet worden geëxtraheerd wanneer de HTML-pagina wordt weergegeven. Daarom moeten afbeeldingsverwijzingen absolute paden zijn die in HTML moeten worden gerenderd.

>[!NOTE]
>
>Hoewel u verschillende typen formulieren op waarde kunt weergeven (bijvoorbeeld HTML-formulieren of formulieren die gebruiksrechten bevatten), wordt in deze sectie de rendering van interactieve PDF forms besproken.

>[!NOTE]
>
>Zie [Referentiehandleiding voor services voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63) voor meer informatie over de Forms-service.

## Overzicht van stappen {#summary-of-steps}

Voer de volgende stappen uit om een formulier op waarde te genereren:

1. Inclusief projectbestanden.
1. Maak een Forms Client API-object.
1. Verwijs naar het formulierontwerp.
1. Een formulier op waarde weergeven.
1. Schrijf de gegevensstroom van het formulier naar de webbrowser van de client.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**Een Forms Client API-object maken**

Voordat u gegevens via programmacode kunt importeren in een PDF-formulier met client-API, moet u een client voor gegevensintegratie maken. Wanneer u een serviceclient maakt, definieert u verbindingsinstellingen die vereist zijn om een service aan te roepen.

**Verwijzen naar het formulierontwerp**

Wanneer u een formulier op waarde weergeeft, moet u een `com.adobe.idp.Document`-object maken dat het formulierontwerp bevat dat moet worden weergegeven. U kunt verwijzen naar een bestaand XDP-bestand of u kunt bij uitvoering dynamisch een formulierontwerp maken en een `com.adobe.idp.Document` vullen met die gegevens.

>[!NOTE]
>
>Deze sectie en de bijbehorende snelstartverwijzingen verwijzen naar een bestaand XDP-bestand.

**Een formulier op waarde weergeven**

Als u een formulier op waarde wilt weergeven, geeft u een `com.adobe.idp.Document`-exemplaar met het formulierontwerp door aan de parameter `inDataDoc` van de rendermethode (dit kan een van de rendermethoden van het object `FormsServiceClient` zijn, zoals `renderPDFForm`, `(Deprecated) renderHTMLForm`, enzovoort). Deze parameterwaarde is gewoonlijk gereserveerd voor gegevens die met het formulier worden samengevoegd. Op dezelfde manier geeft u een lege tekenreekswaarde door aan de parameter `formQuery`. Normaal gesproken vereist deze parameter een tekenreekswaarde die de naam van het formulierontwerp opgeeft.

>[!NOTE]
>
>Als u gegevens in het formulier wilt weergeven, moeten de gegevens worden opgegeven in het element `xfa:datasets`. Ga voor informatie over XFA-architectuur naar [https://partners.adobe.com/public/developer/xml/index_arch.html](https://partners.adobe.com/public/developer/xml/index_arch.html).

**De formuliergegevensstroom naar de webbrowser van de client schrijven**

Wanneer de Forms-service een formulier op waarde weergeeft, wordt een formuliergegevensstroom geretourneerd die u naar de webbrowser van de client moet schrijven. Wanneer het formulier naar de webbrowser van de client wordt geschreven, is het zichtbaar voor de gebruiker.

**Zie ook**

[Een formulier op waarde weergeven met de Java API](#render-a-form-by-value-using-the-java-api)

[Een formulier op waarde weergeven met de API voor webservices](#render-a-form-by-value-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Forms Service API Quick Start](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Documenten doorgeven aan de Forms-service](/help/forms/developing/passing-documents-forms-service.md)

[Webtoepassingen maken die Forms renderen](/help/forms/developing/creating-web-applications-renders-forms.md)

## Een formulier op waarde weergeven met de Java-API {#render-a-form-by-value-using-the-java-api}

Een formulier op waarde weergeven met de Forms API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-forms-client.jar, op in het klassenpad van uw Java-project.

1. Een Forms Client API-object maken

   * Maak een `ServiceClientFactory`-object dat verbindingseigenschappen bevat.
   * Maak een `FormsServiceClient`-object door de constructor ervan te gebruiken en het object `ServiceClientFactory` door te geven.

1. Verwijzen naar het formulierontwerp

   * Maak een `java.io.FileInputStream`-object dat het formulierontwerp vertegenwoordigt dat moet worden gerenderd met de constructor ervan en geef een tekenreekswaarde door die de locatie van het XDP-bestand aangeeft.
   * Maak een `com.adobe.idp.Document`-object door de constructor ervan te gebruiken en het object `java.io.FileInputStream` door te geven.

1. Een formulier op waarde weergeven

   Roep de methode `renderPDFForm` van het object `FormsServiceClient` aan en geef de volgende waarden door:

   * Een lege tekenreekswaarde. (Normaal gesproken vereist deze parameter een tekenreekswaarde die de naam van het formulierontwerp aangeeft.)
   * Een `com.adobe.idp.Document`-object dat het formulierontwerp bevat. Normaal gesproken is deze parameterwaarde gereserveerd voor gegevens die met het formulier worden samengevoegd.
   * Een `PDFFormRenderSpec`-object dat uitvoeringsopties opslaat. Dit is een optionele parameter en u kunt `null` specificeren als u runtime geen opties wilt specificeren.
   * Een object `URLSpec` dat URI-waarden bevat die door de Forms-service worden vereist.
   * Een `java.util.HashMap`-object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt `null` opgeven als u geen bestanden aan het formulier wilt koppelen.

   De methode `renderPDFForm` retourneert een `FormsResult`-object dat een formuliergegevensstroom bevat die naar de webbrowser van de client kan worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Maak een `com.adobe.idp.Document`-object door de methode `getOutputContent` van het object aan te roepen.`FormsResult`
   * Hiermee wordt het inhoudstype van het object `com.adobe.idp.Document` opgehaald door de methode `getContentType` ervan aan te roepen.
   * Stel het inhoudstype van het object `javax.servlet.http.HttpServletResponse` in door de methode `setContentType` ervan aan te roepen en het inhoudstype van het object `com.adobe.idp.Document` door te geven.
   * Maak een `javax.servlet.ServletOutputStream`-object dat wordt gebruikt om de formuliergegevensstroom naar de webbrowser van de client te schrijven door de methode `javax.servlet.http.HttpServletResponse` van het object `getOutputStream` aan te roepen.
   * Maak een `java.io.InputStream`-object door de methode `getInputStream` van het object `com.adobe.idp.Document` aan te roepen.
   * Maak een bytearray en wijs de grootte van het object `InputStream` toe. Roep de methode `InputStream` van het object `available` aan om de grootte van het object `InputStream` te verkrijgen.
   * Vul de bytearray met de formuliergegevensstroom door de methode `read`van het object `InputStream` aan te roepen en de bytearray als een argument door te geven.
   * Roep de methode `javax.servlet.ServletOutputStream` van het object `write` aan om de gegevensstroom van het formulier naar de webbrowser van de client te verzenden. Geef de bytearray door aan de methode `write`.

**Zie ook**

[Forms renderen op waarde](/help/forms/developing/rendering-forms.md)

[Snel starten (SOAP-modus): Renderen op waarde met de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-by-value-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Een formulier op waarde weergeven met de API {#render-a-form-by-value-using-the-web-service-api} voor webservices

Een formulier op waarde weergeven met de Forms API (webservice):

1. Projectbestanden opnemen

   * Maak Java-proxyklassen die gebruikmaken van de Forms-service WSDL.
   * Neem de Java-proxyklassen op in het klassepad.

1. Een Forms Client API-object maken

   Maak een `FormsService`-object en stel de verificatiewaarden in.

1. Verwijzen naar het formulierontwerp

   * Maak een `java.io.FileInputStream`-object met de constructor ervan. Geef een tekenreekswaarde door die de locatie van het XDP-bestand aangeeft.
   * Maak een `BLOB`-object met de constructor ervan. Met het object `BLOB` wordt een PDF-document opgeslagen dat met een wachtwoord is versleuteld.
   * Maak een bytearray waarin de inhoud van het object `java.io.FileInputStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de grootte van het object `java.io.FileInputStream` op te halen met de methode `available`.
   * Vul de bytearray met streamgegevens door de methode `read` van het object `java.io.FileInputStream` aan te roepen en de bytearray door te geven.
   * Vul het object `BLOB` door de methode `setBinaryData` ervan aan te roepen en de bytearray door te geven.

1. Een formulier op waarde weergeven

   Roep de methode `renderPDFForm` van het object `FormsService` aan en geef de volgende waarden door:

   * Een lege tekenreekswaarde. (Normaal gesproken vereist deze parameter een tekenreekswaarde die de naam van het formulierontwerp aangeeft.)
   * Een `BLOB`-object dat het formulierontwerp bevat. Normaal gesproken is deze parameterwaarde gereserveerd voor gegevens die met het formulier worden samengevoegd.
   * Een `PDFFormRenderSpec`-object dat uitvoeringsopties opslaat. Dit is een optionele parameter en u kunt `null` specificeren als u runtime geen opties wilt specificeren.
   * Een object `URLSpec` dat URI-waarden bevat die door de Forms-service worden vereist.
   * Een `java.util.HashMap`-object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt `null` opgeven als u geen bestanden aan het formulier wilt koppelen.
   * Een leeg object `com.adobe.idp.services.holders.BLOBHolder` dat door de methode is gevuld. Hiermee slaat u het gerenderde PDF-formulier op.
   * Een leeg object `javax.xml.rpc.holders.LongHolder` dat door de methode is gevuld. (In dit argument wordt het aantal pagina&#39;s in het formulier opgeslagen.)
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

[Forms renderen op waarde](#rendering-forms-by-value)

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
