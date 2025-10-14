---
title: Forms renderen op waarde
description: Met de Forms API (Java) kunt u een formulier op waarde weergeven met de API voor Java API en Web Service.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: a3a6a06d-ec90-4147-a5f0-e776a086ee12
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services,APIs & Integrations
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '1822'
ht-degree: 0%

---

# Forms renderen op waarde {#rendering-forms-by-value}

**de Steekproeven en de voorbeelden in dit document zijn slechts voor AEM Forms op milieu JEE.**

Een formulierontwerp dat in Designer is gemaakt, wordt doorgaans doorgegeven via de Forms-service. Formulierontwerpen kunnen groot zijn en daarom is het efficiënter om ze door te geven als verwijzing, zodat het niet nodig is om bytes in het formulierontwerp op waarde te rangschikken. De Forms-service kan het formulierontwerp ook in cache plaatsen, zodat het formulierontwerp niet voortdurend hoeft te worden gelezen wanneer het in cache wordt geplaatst.

Als een formulierontwerp een UUID-kenmerk bevat, wordt het in de cache opgeslagen. De UUID-waarde is uniek voor alle formulierontwerpen en wordt gebruikt om een formulier op unieke wijze te identificeren. Als u een formulier op waarde weergeeft, mag het formulier alleen in de cache worden geplaatst wanneer het herhaaldelijk wordt gebruikt. Als het formulier echter niet herhaaldelijk wordt gebruikt en uniek moet zijn, kunt u voorkomen dat het formulier in cache wordt geplaatst met behulp van cacheopties die zijn ingesteld met de AEM Forms API.

De Forms-service kan ook de locatie van gekoppelde inhoud in het formulierontwerp oplossen. Bijvoorbeeld: gekoppelde afbeeldingen waarnaar in het formulierontwerp wordt verwezen, zijn relatieve URL&#39;s. Gekoppelde inhoud wordt altijd verondersteld relatief te zijn ten opzichte van de locatie van het formulierontwerp. Daarom is het oplossen van gekoppelde inhoud een kwestie van het bepalen van zijn plaats door de relatieve weg op de absolute plaats van het vormontwerp toe te passen.

In plaats van een formulierontwerp door te geven als referentie, kunt u een formulierontwerp op waarde doorgeven. Het doorgeven van een formulierontwerp op waarde is efficiënt wanneer een formulierontwerp dynamisch wordt gemaakt, dat wil zeggen wanneer een clienttoepassing de XML genereert die tijdens runtime een formulierontwerp maakt. In dit geval wordt een formulierontwerp niet opgeslagen in een fysieke opslagplaats, omdat het in het geheugen wordt opgeslagen. Als u tijdens de runtime dynamisch een formulierontwerp maakt en dit op waarde doorgeeft, kunt u het formulier in cache plaatsen en de prestaties van de Forms-service verbeteren.

**Beperkingen van het overgaan van een vorm door waarde**

De volgende beperkingen zijn van toepassing wanneer een formulierontwerp wordt doorgegeven als waarde:

* Er kan geen relatieve gekoppelde inhoud in het formulierontwerp voorkomen. Alle afbeeldingen en fragmenten moeten in het formulierontwerp worden ingesloten of absoluut worden vermeld.
* Berekeningen aan de serverzijde kunnen niet worden uitgevoerd nadat het formulier is gegenereerd. Als het formulier wordt teruggestuurd naar de Forms-service, worden de gegevens opgehaald en geretourneerd zonder berekeningen aan de serverzijde.
* Omdat HTML gekoppelde afbeeldingen alleen tijdens runtime kan gebruiken, is het niet mogelijk om HTML met ingesloten afbeeldingen te genereren. De reden hiervoor is dat de Forms-service ingesloten afbeeldingen met HTML ondersteunt door de afbeeldingen op te halen uit een formulierontwerp waarnaar wordt verwezen. Omdat een formulierontwerp dat via waarde wordt doorgegeven, geen locatie waarnaar wordt verwezen, kunnen ingesloten afbeeldingen niet worden uitgepakt wanneer de pagina HTML wordt weergegeven. Daarom moeten afbeeldingsverwijzingen absolute paden zijn die moeten worden gerenderd in HTML.

>[!NOTE]
>
>Hoewel u verschillende typen formulieren op waarde kunt weergeven (bijvoorbeeld HTML-formulieren of formulieren die gebruiksrechten bevatten), wordt in deze sectie de rendering van interactieve PDF forms besproken.

>[!NOTE]
>
>Voor meer informatie over de dienst van Forms, zie [&#x200B; Verwijzing van de Diensten voor AEM Forms &#x200B;](https://www.adobe.com/go/learn_aemforms_services_63).

## Overzicht van de stappen {#summary-of-steps}

Voer de volgende stappen uit om een formulier op waarde te genereren:

1. Inclusief projectbestanden.
1. Maak een Forms Client API-object.
1. Verwijs naar het formulierontwerp.
1. Een formulier op waarde weergeven.
1. Schrijf de gegevensstroom van het formulier naar de webbrowser van de client.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**creeer een voorwerp van Forms Cliënt API**

Voordat u via programmacode gegevens kunt importeren in een PDF formulier-client-API, moet u een Data Integration-service-client maken. Wanneer u een serviceclient maakt, definieert u verbindingsinstellingen die vereist zijn om een service aan te roepen.

**Verwijzing het vormontwerp**

Wanneer u een formulier op waarde weergeeft, moet u een `com.adobe.idp.Document` -object maken dat het formulierontwerp bevat dat moet worden gegenereerd. U kunt verwijzen naar een bestaand XDP-bestand of u kunt bij uitvoering dynamisch een formulierontwerp maken en een `com.adobe.idp.Document` vullen met die gegevens.

>[!NOTE]
>
>Deze sectie en de bijbehorende snelstartverwijzingen verwijzen naar een bestaand XDP-bestand.

**geeft een vorm door waarde terug**

Als u een formulier op waarde wilt weergeven, geeft u een `com.adobe.idp.Document` -instantie met het formulierontwerp door aan de `inDataDoc` -parameter van de rendermethode (dit kan elke rendermethode van het `FormsServiceClient` -object zijn, zoals `renderPDFForm` , `(Deprecated) renderHTMLForm` , enzovoort). Deze parameterwaarde is gewoonlijk gereserveerd voor gegevens die met het formulier worden samengevoegd. Geef op dezelfde manier een lege tekenreekswaarde door aan de parameter `formQuery` . Normaal gesproken vereist deze parameter een tekenreekswaarde die de naam van het formulierontwerp opgeeft.

>[!NOTE]
>
>Als u gegevens in het formulier wilt weergeven, moeten de gegevens worden opgegeven in het element `xfa:datasets` . Voor informatie over architectuur XFA, ga naar [&#x200B; https://www.pdfa.org/norm-refs/XFA-3_3.pdf &#x200B;](https://www.pdfa.org/norm-refs/XFA-3_3.pdf).

**schrijf de stroom van vormgegevens aan cliëntWeb browser**

Wanneer de Forms-service een formulier op waarde weergeeft, wordt een formuliergegevensstroom geretourneerd die u naar de webbrowser van de client moet schrijven. Wanneer het formulier naar de webbrowser van de client wordt geschreven, is het zichtbaar voor de gebruiker.

**zie ook**

[Een formulier op waarde weergeven met de Java API](#render-a-form-by-value-using-the-java-api)

[Een formulier op waarde weergeven met de API voor webservices](#render-a-form-by-value-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Forms Service API Quick Start](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Documenten doorgeven aan de Forms-service](/help/forms/developing/passing-documents-forms-service.md)

[Webtoepassingen maken die Forms renderen](/help/forms/developing/creating-web-applications-renders-forms.md)

## Een formulier op waarde weergeven met de Java API {#render-a-form-by-value-using-the-java-api}

Een formulier op waarde weergeven met de Forms API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-forms-client.jar, op in het klassepad van uw Java-project.

1. Een Forms Client API-object maken

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `FormsServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Verwijzen naar het formulierontwerp

   * Maak een `java.io.FileInputStream` -object dat het formulierontwerp vertegenwoordigt dat moet worden gegenereerd met de constructor ervan en geef een tekenreekswaarde door die de locatie van het XDP-bestand aangeeft.
   * Maak een `com.adobe.idp.Document` -object door de constructor ervan te gebruiken en het `java.io.FileInputStream` -object door te geven.

1. Een formulier op waarde weergeven

   Roep de methode `renderPDFForm` van het object `FormsServiceClient` aan en geef de volgende waarden door:

   * Een lege tekenreeks. (Normaal gesproken vereist deze parameter een tekenreekswaarde die de naam van het formulierontwerp aangeeft.)
   * Een `com.adobe.idp.Document` -object dat het formulierontwerp bevat. Normaal gesproken is deze parameterwaarde gereserveerd voor gegevens die met het formulier worden samengevoegd.
   * Een `PDFFormRenderSpec` -object dat uitvoeringsopties opslaat. Dit is een optionele parameter en u kunt `null` opgeven als u geen runtime-opties wilt opgeven.
   * Een `URLSpec` -object dat URI-waarden bevat die door de Forms-service worden vereist.
   * Een `java.util.HashMap` -object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt `null` opgeven als u geen bestanden aan het formulier wilt koppelen.

   De methode `renderPDFForm` retourneert een `FormsResult` -object dat een formuliergegevensstroom bevat die naar de webbrowser van de client kan worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Maak een `com.adobe.idp.Document` -object door de methode `FormsResult` object `getOutputContent` aan te roepen.
   * Haal het inhoudstype van het object `com.adobe.idp.Document` op door de methode `getContentType` ervan aan te roepen.
   * Stel het inhoudstype van het `javax.servlet.http.HttpServletResponse` -object in door de methode `setContentType` ervan aan te roepen en het inhoudstype van het `com.adobe.idp.Document` -object door te geven.
   * Maak een `javax.servlet.ServletOutputStream` -object dat wordt gebruikt om de formuliergegevensstroom naar de webbrowser van de client te schrijven door de methode `javax.servlet.http.HttpServletResponse` object `getOutputStream` aan te roepen.
   * Maak een `java.io.InputStream` -object door de methode `com.adobe.idp.Document` object `getInputStream` aan te roepen.
   * Maak een bytearray en wijs de grootte van het `InputStream` -object toe. Roep de methode `available` van het object `InputStream` aan om de grootte van het object `InputStream` te verkrijgen.
   * Vul de bytearray met de gegevensstroom van het formulier door de methode `read` van het object `InputStream` aan te roepen en de bytearray als een argument door te geven.
   * Roep de methode `write` van het object `javax.servlet.ServletOutputStream` aan om de gegevensstroom van het formulier naar de webbrowser van de client te verzenden. Geef de bytearray door aan de methode `write` .

**zie ook**

[Forms renderen op waarde](/help/forms/developing/rendering-forms.md)

[Snel starten (SOAP modus): renderen op waarde met de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-by-value-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Een formulier op waarde weergeven met de API voor webservices {#render-a-form-by-value-using-the-web-service-api}

Een formulier op waarde weergeven met de Forms API (webservice):

1. Projectbestanden opnemen

   * Maak Java-proxyklassen die gebruikmaken van de Forms-service WSDL.
   * Neem de Java-proxyklassen op in het klassepad.

1. Een Forms Client API-object maken

   Maak een `FormsService` -object en stel de verificatiewaarden in.

1. Verwijzen naar het formulierontwerp

   * Maak een `java.io.FileInputStream` -object met behulp van de constructor. Geef een tekenreekswaarde door die de locatie van het XDP-bestand aangeeft.
   * Maak een `BLOB` -object met behulp van de constructor. Het `BLOB` -object wordt gebruikt om een PDF-document op te slaan dat met een wachtwoord is versleuteld.
   * Maak een bytearray waarin de inhoud van het object `java.io.FileInputStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de grootte van het object `java.io.FileInputStream` op te halen met de methode `available` .
   * Vul de bytearray met streamgegevens door de methode `read` van het object `java.io.FileInputStream` aan te roepen en de bytearray door te geven.
   * Vul het object `BLOB` door de methode `setBinaryData` ervan aan te roepen en de bytearray door te geven.

1. Een formulier op waarde weergeven

   Roep de methode `renderPDFForm` van het object `FormsService` aan en geef de volgende waarden door:

   * Een lege tekenreeks. (Normaal gesproken vereist deze parameter een tekenreekswaarde die de naam van het formulierontwerp aangeeft.)
   * Een `BLOB` -object dat het formulierontwerp bevat. Normaal gesproken is deze parameterwaarde gereserveerd voor gegevens die met het formulier worden samengevoegd.
   * Een `PDFFormRenderSpec` -object dat uitvoeringsopties opslaat. Dit is een optionele parameter en u kunt `null` opgeven als u geen runtime-opties wilt opgeven.
   * Een `URLSpec` -object dat URI-waarden bevat die door de Forms-service worden vereist.
   * Een `java.util.HashMap` -object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt `null` opgeven als u geen bestanden aan het formulier wilt koppelen.
   * Een leeg `com.adobe.idp.services.holders.BLOBHolder` -object dat door de methode wordt gevuld. Hiermee slaat u het gerenderde PDF formulier op.
   * Een leeg `javax.xml.rpc.holders.LongHolder` -object dat door de methode wordt gevuld. (In dit argument wordt het aantal pagina&#39;s in het formulier opgeslagen.)
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

[Forms renderen op waarde](#rendering-forms-by-value)

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
