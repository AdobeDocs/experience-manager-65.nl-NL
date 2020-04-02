---
title: Formulieren renderen op waarde
seo-title: Formulieren renderen op waarde
description: 'null'
seo-description: 'null'
uuid: b932cc54-662f-40ae-94e0-20ac82845f3b
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: ddbb2b82-4c57-4845-a5be-2435902d312b
translation-type: tm+mt
source-git-commit: 66bfd6870b4c09dc2ca1b66058e0b9e040a71507

---


# Formulieren renderen op waarde {#rendering-forms-by-value}

Een formulierontwerp dat in Designer is gemaakt, wordt meestal doorgegeven via de service Formulieren. Formulierontwerpen kunnen groot zijn en daarom is het efficiënter om ze door te geven als verwijzing, zodat het niet nodig is om bytes in het formulierontwerp op waarde te rangschikken. De service Forms kan het formulierontwerp ook in cache plaatsen, zodat het formulierontwerp niet voortdurend hoeft te worden gelezen wanneer het in cache wordt geplaatst.

Als een formulierontwerp een UUID-kenmerk bevat, wordt het in de cache opgeslagen. De UUID-waarde is uniek voor alle formulierontwerpen en wordt gebruikt om een formulier op unieke wijze te identificeren. Als u een formulier op waarde weergeeft, mag het formulier alleen in de cache worden geplaatst wanneer het herhaaldelijk wordt gebruikt. Als het formulier echter niet herhaaldelijk wordt gebruikt en uniek moet zijn, kunt u voorkomen dat het formulier in cache wordt geplaatst met behulp van cacheopties die zijn ingesteld met de API voor AEM-formulieren.

De service Forms kan ook de locatie van gekoppelde inhoud in het formulierontwerp oplossen. Bijvoorbeeld: gekoppelde afbeeldingen waarnaar in het formulierontwerp wordt verwezen, zijn relatieve URL&#39;s. Gekoppelde inhoud wordt altijd verondersteld relatief te zijn ten opzichte van de locatie van het formulierontwerp. Daarom is het oplossen van gekoppelde inhoud een kwestie van het bepalen van zijn plaats door de relatieve weg op de absolute plaats van het vormontwerp toe te passen.

In plaats van een formulierontwerp door te geven als referentie, kunt u een formulierontwerp op waarde doorgeven. Het doorgeven van een formulierontwerp op basis van waarde is efficiënt wanneer een formulierontwerp dynamisch wordt gemaakt. Dat wil zeggen, wanneer een clienttoepassing de XML genereert die tijdens runtime een formulierontwerp maakt. In dit geval wordt een formulierontwerp niet opgeslagen in een fysieke opslagplaats, omdat het in het geheugen wordt opgeslagen. Wanneer u tijdens de runtime dynamisch een formulierontwerp maakt en dit op waarde doorgeeft, kunt u het formulier in cache plaatsen en de prestaties van de service Forms verbeteren.

**Beperkingen bij het doorgeven van een formulier op waarde**

De volgende beperkingen zijn van toepassing wanneer een formulierontwerp wordt doorgegeven als waarde:

* Het formulierontwerp kan geen relatieve gekoppelde inhoud bevatten. Alle afbeeldingen en fragmenten moeten in het formulierontwerp worden ingesloten of absoluut worden vermeld.
* Berekeningen aan de serverzijde kunnen niet worden uitgevoerd nadat het formulier is gegenereerd. Als het formulier wordt teruggestuurd naar de service Forms, worden de gegevens opgehaald en geretourneerd zonder berekeningen aan de serverzijde.
* Omdat HTML gekoppelde afbeeldingen alleen tijdens runtime kan gebruiken, is het niet mogelijk om HTML met ingesloten afbeeldingen te genereren. De reden hiervoor is dat de service Forms ingesloten afbeeldingen met HTML ondersteunt door de afbeeldingen op te halen uit een formulierontwerp waarnaar wordt verwezen. Omdat een formulierontwerp dat via waarde wordt doorgegeven, geen locatie waarnaar wordt verwezen, kunnen ingesloten afbeeldingen niet worden geëxtraheerd wanneer de HTML-pagina wordt weergegeven. Daarom moeten afbeeldingsverwijzingen absolute paden zijn die in HTML moeten worden gerenderd.

>[!NOTE]
>
>Hoewel u verschillende typen formulieren op waarde kunt weergeven (bijvoorbeeld HTML-formulieren of formulieren met gebruiksrechten), wordt in deze sectie de rendering van interactieve PDF-formulieren besproken.

>[!NOTE]
>
>Voor meer informatie over de dienst van Vormen, zie de Verwijzing van de [Diensten voor Vormen](https://www.adobe.com/go/learn_aemforms_services_63)AEM.

## Overzicht van de stappen {#summary-of-steps}

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

Wanneer u een formulier op waarde weergeeft, moet u een `com.adobe.idp.Document` object maken dat het te genereren formulierontwerp bevat. U kunt verwijzen naar een bestaand XDP-bestand of u kunt tijdens runtime dynamisch een formulierontwerp maken en een bestand vullen `com.adobe.idp.Document` met die gegevens.

>[!NOTE]
>
>Deze sectie en de bijbehorende snelstartverwijzingen verwijzen naar een bestaand XDP-bestand.

**Een formulier op waarde weergeven**

Als u een formulier op waarde wilt weergeven, geeft u een `com.adobe.idp.Document` exemplaar met het formulierontwerp door aan de `inDataDoc` parameter van de rendermethode (dit kan elke rendermethode van het `FormsServiceClient` object zijn, zoals `renderPDFForm`, `(Deprecated) renderHTMLForm`enzovoort). Deze parameterwaarde is gewoonlijk gereserveerd voor gegevens die met het formulier worden samengevoegd. Geef op dezelfde manier een lege tekenreekswaarde door aan de `formQuery` parameter. Normaal gesproken vereist deze parameter een tekenreekswaarde die de naam van het formulierontwerp opgeeft.

>[!NOTE]
>
>Als u gegevens in het formulier wilt weergeven, moeten de gegevens in het `xfa:datasets` element worden opgegeven. Ga voor informatie over XFA-architectuur naar [https://partners.adobe.com/public/developer/xml/index_arch.html](https://partners.adobe.com/public/developer/xml/index_arch.html).

**De formuliergegevensstroom naar de webbrowser van de client schrijven**

Wanneer de service Forms een formulier op waarde weergeeft, wordt een formuliergegevensstroom geretourneerd die u naar de webbrowser van de client moet schrijven. Wanneer het formulier naar de webbrowser van de client wordt geschreven, is het zichtbaar voor de gebruiker.

**Zie ook**

[Een formulier op waarde weergeven met de Java API](#render-a-form-by-value-using-the-java-api)

[Een formulier op waarde weergeven met de API voor webservices](#render-a-form-by-value-using-the-web-service-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Forms Service API, snel aan de slag](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Documenten doorgeven aan de Forms Service](/help/forms/developing/passing-documents-forms-service.md)

[Webtoepassingen maken die formulieren renderen](/help/forms/developing/creating-web-applications-renders-forms.md)

## Een formulier op waarde weergeven met de Java API {#render-a-form-by-value-using-the-java-api}

Een formulier op waarde weergeven met de API voor formulieren (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-forms-client.jar, op in het klassenpad van uw Java-project.

1. Een Forms Client API-object maken

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `FormsServiceClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Verwijzen naar het formulierontwerp

   * Maak een `java.io.FileInputStream` object dat staat voor het formulierontwerp dat moet worden gegenereerd met de constructor ervan en geef een tekenreekswaarde door die de locatie van het XDP-bestand aangeeft.
   * Maak een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en het `java.io.FileInputStream` object door te geven.

1. Een formulier op waarde weergeven

   Roep de methode van het `FormsServiceClient` `renderPDFForm` object aan en geef de volgende waarden door:

   * Een lege tekenreekswaarde. (Normaal gesproken vereist deze parameter een tekenreekswaarde die de naam van het formulierontwerp aangeeft.)
   * Een `com.adobe.idp.Document` object dat het formulierontwerp bevat. Normaal gesproken is deze parameterwaarde gereserveerd voor gegevens die met het formulier worden samengevoegd.
   * Een `PDFFormRenderSpec` object dat uitvoeringsopties opslaat. Dit is een optionele parameter en u kunt opgeven `null` of u geen runtime-opties wilt opgeven.
   * Een `URLSpec` object dat URI-waarden bevat die door de service Forms worden vereist.
   * Een `java.util.HashMap` object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt opgeven `null` of u geen bestanden aan het formulier wilt koppelen.
   De `renderPDFForm` methode retourneert een `FormsResult` object dat een formuliergegevensstroom bevat die naar de webbrowser van de client kan worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Maak een `com.adobe.idp.Document` object door de `FormsResult` methode van het `getOutputContent` object aan te roepen.
   * Haal het inhoudstype van het `com.adobe.idp.Document` object op door de `getContentType` methode ervan aan te roepen.
   * Stel het inhoudstype van het `javax.servlet.http.HttpServletResponse` object in door de bijbehorende `setContentType` methode op te roepen en het inhoudstype van het `com.adobe.idp.Document` object door te geven.
   * Maak een `javax.servlet.ServletOutputStream` object dat wordt gebruikt om de gegevensstroom van het formulier naar de webbrowser van de client te schrijven door de `javax.servlet.http.HttpServletResponse` methode van het `getOutputStream` object aan te roepen.
   * Maak een `java.io.InputStream` object door de `com.adobe.idp.Document` methode van het `getInputStream` object aan te roepen.
   * Maak een bytearray en wijs de grootte van het `InputStream` object toe. Roep de `InputStream` methode van het `available` object aan om de grootte van het `InputStream` object te verkrijgen.
   * Vul de bytearray met de formuliergegevensstroom door de `InputStream` `read`methode van het object aan te roepen en de bytearray als een argument door te geven.
   * Roep de `javax.servlet.ServletOutputStream` methode van het `write` object aan om de formuliergegevensstroom naar de webbrowser van de client te verzenden. Geef de bytearray door aan de `write` methode.

**Zie ook**

[Formulieren renderen op waarde](/help/forms/developing/rendering-forms.md)

[Snel starten (SOAP-modus): Renderen op waarde met de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-by-value-using-the-java-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Een formulier op waarde weergeven met de API voor webservices {#render-a-form-by-value-using-the-web-service-api}

Een formulier op waarde weergeven met de API voor formulieren (webservice):

1. Projectbestanden opnemen

   * Maak Java-proxyklassen die de Forms service WSDL gebruiken.
   * Neem de Java-proxyklassen op in het klassepad.

1. Een Forms Client API-object maken

   Maak een `FormsService` object en stel verificatiewaarden in.

1. Verwijzen naar het formulierontwerp

   * Maak een `java.io.FileInputStream` object met de constructor ervan. Geef een tekenreekswaarde door die de locatie van het XDP-bestand aangeeft.
   * Maak een `BLOB` object met de constructor ervan. Met dit `BLOB` object wordt een PDF-document opgeslagen dat met een wachtwoord is versleuteld.
   * Maak een bytearray waarin de inhoud van het `java.io.FileInputStream` object wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de grootte van het `java.io.FileInputStream` object op te halen met de `available` methode.
   * Vul de bytearray met streamgegevens door de methode van het `java.io.FileInputStream` `read` object aan te roepen en de bytearray door te geven.
   * Vul het `BLOB` `setBinaryData` object door de methode ervan aan te roepen en de bytearray door te geven.

1. Een formulier op waarde weergeven

   Roep de methode van het `FormsService` `renderPDFForm` object aan en geef de volgende waarden door:

   * Een lege tekenreekswaarde. (Normaal gesproken vereist deze parameter een tekenreekswaarde die de naam van het formulierontwerp aangeeft.)
   * Een `BLOB` object dat het formulierontwerp bevat. Normaal gesproken is deze parameterwaarde gereserveerd voor gegevens die met het formulier worden samengevoegd.
   * Een `PDFFormRenderSpec` object dat uitvoeringsopties opslaat. Dit is een optionele parameter en u kunt opgeven `null` of u geen runtime-opties wilt opgeven.
   * Een `URLSpec` object dat URI-waarden bevat die door de service Forms worden vereist.
   * Een `java.util.HashMap` object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt opgeven `null` of u geen bestanden aan het formulier wilt koppelen.
   * Een leeg `com.adobe.idp.services.holders.BLOBHolder` object dat door de methode wordt gevuld. Hiermee slaat u het gerenderde PDF-formulier op.
   * Een leeg `javax.xml.rpc.holders.LongHolder` object dat door de methode wordt gevuld. (In dit argument wordt het aantal pagina&#39;s in het formulier opgeslagen.)
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

[Formulieren renderen op waarde](#rendering-forms-by-value)

[AEM-formulieren aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
