---
title: HTML Forms renderen met aangepaste CSS-bestanden
description: Gebruik de Forms-service om te verwijzen naar aangepaste CSS-bestanden om HTML-formulieren te genereren als reactie op een HTTP-aanvraag van een webbrowser. U kunt een HTML-formulier weergeven dat een CSS-bestand gebruikt met de API voor Java API en Web Service.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: 5fa385a7-f030-4c0c-8938-0991d02ef361
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services,APIs & Integrations
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '1682'
ht-degree: 0%

---

# HTML Forms renderen met aangepaste CSS-bestanden {#rendering-html-forms-using-custom-css-files}

**de Steekproeven en de voorbeelden in dit document zijn slechts voor AEM Forms op milieu JEE.**

De Forms-service geeft HTML-formulieren weer als reactie op een HTTP-aanvraag van een webbrowser. Bij het weergeven van een HTML-formulier kan de Forms-service verwijzen naar een aangepast CSS-bestand. U kunt een aangepast CSS-bestand maken dat voldoet aan uw zakelijke vereisten en u kunt naar dat CSS-bestand verwijzen wanneer u de Forms-service gebruikt om HTML-formulieren te genereren.

De Forms-service parseert het aangepaste CSS-bestand ongemerkt. De Forms-service rapporteert dus geen fouten die kunnen worden aangetroffen als het aangepaste CSS-bestand niet voldoet aan CSS-standaarden. In dit geval negeert de Forms-service de stijl en gaat deze verder met de resterende stijlen in het CSS-bestand.

In de volgende lijst worden stijlen weergegeven die in een aangepast CSS-bestand worden ondersteund:

* **het niveau van de Klasse selecteur-stijl paren**: Als aanwezig in een douaneCSS dossier, worden de selecteurs die in de vorm van de HTML als klassenstijlen worden gebruikt. Ongebruikte klassenstijlen worden genegeerd.
* **herkenningsteken niveau selecteur-stijl paren**: Alle herkenningstekenstijlen worden gebruikt als zij in de vorm van HTML worden gebruikt.
* **het niveau van het Element selecteur-stijl paren**: Alle elementenstijlen worden gebruikt als zij in de vorm van de HTML worden gebruikt.
* **Prioriteit van de Stijl**: De prioriteit van de stijl (als belangrijk) wordt gesteund en kan in een douaneCSS dossier worden gebruikt.
* **Type van Media**: Één of meerdere selecteur-stijl paren kunnen in @media stijl worden verpakt om het media type te bepalen. De Forms-service controleert niet of het opgegeven mediatype wordt ondersteund. Het mediatype dat is opgegeven in het aangepaste CSS-bestand wordt samengevoegd in het HTML-formulier.

U kunt een voorbeeld-CSS-bestand ophalen met de FormsIVS-toepassing. Upload het formulier, selecteer het op de pagina Formulierontwerp testen en klik op CSS genereren. U hoeft het transformatietype HTML niet in te stellen voordat u op de knop klikt. Selecteer vervolgens Opslaan. U kunt dit CSS-bestand bewerken om aan uw zakelijke vereisten te voldoen.

>[!NOTE]
>
>Voordat u een HTML-formulier rendert dat een aangepast CSS-bestand gebruikt, is het belangrijk dat u goed begrijpt hoe HTML-formulieren worden weergegeven. (Zie [ teruggevend Forms als HTML ](/help/forms/developing/rendering-forms-html.md).)

>[!NOTE]
>
>Voor meer informatie over de dienst van Forms, zie [ Verwijzing van de Diensten voor AEM Forms ](https://www.adobe.com/go/learn_aemforms_services_63).

## Overzicht van de stappen {#summary-of-steps}

Voer de volgende taken uit om een HTML-formulier te genereren dat een CSS-bestand gebruikt:

1. Inclusief projectbestanden.
1. Maak een Forms Java API-object.
1. Verwijs naar het CSS-bestand.
1. Een HTML-formulier weergeven.
1. Schrijf de gegevensstroom van het formulier naar de webbrowser van de client.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**creeer een voorwerp van Forms Java API**

Voordat u een door de Forms-service ondersteunde bewerking programmatisch kunt uitvoeren, moet u een Forms-clientobject maken.

**Verwijzing het CSS dossier**

Als u een HTML-formulier wilt genereren waarin een aangepast CSS-bestand wordt gebruikt, moet u controleren of u naar een bestaand CSS-bestand verwijst.

**geef een vorm van HTML** terug

Als u een HTML-formulier wilt genereren, geeft u een formulierontwerp op dat in Designer is gemaakt en als XDP-bestand is opgeslagen. Selecteer een transformatietype HTML. U kunt bijvoorbeeld het transformatietype HTML opgeven waarmee een dynamische HTML wordt weergegeven voor Internet Explorer 5.0 of hoger.

Voor het weergeven van een HTML-formulier zijn ook waarden vereist, zoals URI-waarden die nodig zijn om andere formuliertypen te genereren.

**schrijf de stroom van vormgegevens aan cliëntWeb browser**

Wanneer de Forms-service een HTML-formulier weergeeft, wordt een formuliergegevensstroom geretourneerd die u naar de webbrowser van de client moet schrijven om het HTML-formulier zichtbaar te maken voor de gebruiker.

**zie ook**

[Een HTML-formulier weergeven dat een CSS-bestand gebruikt met de Java API](#render-an-html-form-that-uses-a-css-file-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Forms Service API Quick Start](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Interactieve PDF forms renderen](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Forms renderen als HTML](/help/forms/developing/rendering-forms-html.md)

[Webtoepassingen maken die Forms renderen](/help/forms/developing/creating-web-applications-renders-forms.md)

## Een HTML-formulier weergeven dat een CSS-bestand gebruikt met de Java API {#render-an-html-form-that-uses-a-css-file-using-the-java-api}

Een HTML-formulier renderen dat een aangepast CSS-bestand gebruikt met de Forms API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-forms-client.jar, op in het klassepad van uw Java-project.

1. Een Forms Java API-object maken

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `FormsServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Verwijzen naar het CSS-bestand

   * Maak een `HTMLRenderSpec` -object met behulp van de constructor.
   * Als u het HTML-formulier wilt renderen dat een aangepast CSS-bestand gebruikt, roept u de methode `setCustomCSSURI` van het object `HTMLRenderSpec` aan en geeft u een tekenreekswaarde door die de locatie en naam van het CSS-bestand opgeeft.

1. Een HTML-formulier renderen

   Roep de methode `(Deprecated) (Deprecated) renderHTMLForm` van het object `FormsServiceClient` aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u verwijst naar een formulierontwerp dat deel uitmaakt van een Forms-toepassing, moet u het volledige pad opgeven, bijvoorbeeld `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp` .
   * Een `TransformTo` opsommingswaarde die het voorkeurstype HTML aangeeft. Als u bijvoorbeeld een HTML-formulier wilt genereren dat compatibel is met dynamic HTML voor Internet Explorer 5.0 of hoger, geeft u `TransformTo.MSDHTML` op.
   * Een `com.adobe.idp.Document` -object dat gegevens bevat die met het formulier moeten worden samengevoegd. Wanneer u geen gegevens wilt samenvoegen, geeft u een leeg `com.adobe.idp.Document` -object door.
   * Het `HTMLRenderSpec` -object dat HTML-runtime-opties opslaat.
   * Een tekenreekswaarde die de headerwaarde `HTTP_USER_AGENT` opgeeft, zoals `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)` .
   * Een `URLSpec` -object dat URI-waarden opslaat die vereist zijn om een HTML-formulier te genereren.
   * Een `java.util.HashMap` -object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt `null` opgeven als u geen bestanden aan het formulier wilt koppelen.

   De methode `(Deprecated) renderHTMLForm` retourneert een `FormsResult` -object dat een formuliergegevensstroom bevat die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Maak een `com.adobe.idp.Document` -object door de methode `FormsResult` object `getOutputContent` aan te roepen.
   * Haal het inhoudstype van het object `com.adobe.idp.Document` op door de methode `getContentType` ervan aan te roepen.
   * Stel het inhoudstype van het `javax.servlet.http.HttpServletResponse` -object in door de methode `setContentType` ervan aan te roepen en het inhoudstype van het `com.adobe.idp.Document` -object door te geven.
   * Maak een `javax.servlet.ServletOutputStream` -object dat wordt gebruikt om de formuliergegevensstroom naar de webbrowser van de client te schrijven door de methode `javax.servlet.h\ttp.HttpServletResponse` object `getOutputStream` aan te roepen.
   * Maak een `java.io.InputStream` -object door de methode `com.adobe.idp.Document` object `getInputStream` aan te roepen.
   * Maak een bytearray en vul deze met de formuliergegevensstroom door de methode `read` van het object `InputStream` aan te roepen en de bytearray als een argument door te geven.
   * Roep de methode `write` van het object `javax.servlet.ServletOutputStream` aan om de gegevensstroom van het formulier naar de webbrowser van de client te verzenden. Geef de bytearray door aan de methode `write` .

**zie ook**

[HTML Forms renderen met aangepaste CSS-bestanden](#rendering-html-forms-using-custom-css-files)

[Snel starten (SOAP modus): een HTML-formulier weergeven dat een CSS-bestand gebruikt met de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-an-html-form-that-uses-a-css-file-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Een HTML-formulier renderen dat een CSS-bestand gebruikt met de webservice-API {#render-an-html-form-that-uses-a-css-file-using-the-web-service-api}

Een HTML-formulier renderen dat een aangepast CSS-bestand gebruikt met de Forms API (webservice):

1. Projectbestanden opnemen

   * Maak Java-proxyklassen die gebruikmaken van de Forms-service WSDL.
   * Neem de Java-proxyklassen op in het klassenpad.

1. Een Forms Java API-object maken

   Maak een `FormsService` -object en stel de verificatiewaarden in.

1. Verwijzen naar het CSS-bestand

   * Maak een `HTMLRenderSpec` -object met behulp van de constructor.
   * Als u het HTML-formulier wilt renderen dat een aangepast CSS-bestand gebruikt, roept u de methode `setCustomCSSURI` van het object `HTMLRenderSpec` aan en geeft u een tekenreekswaarde door die de locatie en naam van het CSS-bestand opgeeft.

1. Een HTML-formulier renderen

   Roep de methode `(Deprecated) renderHTMLForm` van het object `FormsService` aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u verwijst naar een formulierontwerp dat deel uitmaakt van een Forms-toepassing, moet u het volledige pad opgeven, bijvoorbeeld `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp` .
   * Een `TransformTo` opsommingswaarde die het voorkeurstype HTML aangeeft. Als u bijvoorbeeld een HTML-formulier wilt genereren dat compatibel is met dynamic HTML voor Internet Explorer 5.0 of hoger, geeft u `TransformTo.MSDHTML` op.
   * Een `BLOB` -object dat gegevens bevat die met het formulier moeten worden samengevoegd. Geef `null` door als u geen gegevens wilt samenvoegen. (Zie [ Prepopulating Forms met Stroombare Lay-outs ](/help/forms/developing/prepopulating-forms-flowable-layouts.md).)
   * Het `HTMLRenderSpec` -object dat HTML-runtime-opties opslaat.
   * Een tekenreekswaarde die de headerwaarde `HTTP_USER_AGENT` opgeeft, zoals `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)` . U kunt een lege tekenreeks doorgeven als u deze waarde niet wilt instellen.
   * Een `URLSpec` -object dat URI-waarden opslaat die vereist zijn om een HTML-formulier te genereren.
   * Een `java.util.HashMap` -object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt `null` opgeven als u geen bestanden aan het formulier wilt koppelen.
   * Een leeg `com.adobe.idp.services.holders.BLOBHolder` -object dat door de methode `(Deprecated) renderHTMLForm` wordt gevuld. Met deze parameterwaarde wordt het gerenderde formulier opgeslagen.
   * Een leeg `com.adobe.idp.services.holders.BLOBHolder` -object dat door de methode `(Deprecated) renderHTMLForm` wordt gevuld. In deze parameter worden de XML-uitvoergegevens opgeslagen.
   * Een leeg `javax.xml.rpc.holders.LongHolder` -object dat door de methode `(Deprecated) renderHTMLForm` wordt gevuld. In dit argument wordt het aantal pagina&#39;s in het formulier opgeslagen.
   * Een leeg `javax.xml.rpc.holders.StringHolder` -object dat door de methode `(Deprecated) renderHTMLForm` wordt gevuld. In dit argument wordt de waarde van de landinstelling opgeslagen.
   * Een leeg `javax.xml.rpc.holders.StringHolder` -object dat door de methode `(Deprecated) renderHTMLForm` wordt gevuld. In dit argument wordt de gebruikte HTML-renderwaarde opgeslagen.
   * Een leeg `com.adobe.idp.services.holders.FormsResultHolder` -object dat de resultaten van deze bewerking bevat.

   Met de methode `(Deprecated) renderHTMLForm` wordt het `com.adobe.idp.services.holders.FormsResultHolder` -object dat als laatste argumentwaarde wordt doorgegeven, gevuld met een formuliergegevensstroom die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Maak een `FormResult` -object door de waarde van het gegevenslid van het `com.adobe.idp.services.holders.FormsResultHolder` object `value` op te halen.
   * Maak een `BLOB` -object dat formuliergegevens bevat door de methode `FormsResult` object `getOutputContent` aan te roepen.
   * Haal het inhoudstype van het object `BLOB` op door de methode `getContentType` ervan aan te roepen.
   * Stel het inhoudstype van het `javax.servlet.http.HttpServletResponse` -object in door de methode `setContentType` ervan aan te roepen en het inhoudstype van het `BLOB` -object door te geven.
   * Maak een `javax.servlet.ServletOutputStream` -object dat wordt gebruikt om de formuliergegevensstroom naar de webbrowser van de client te schrijven door de methode `javax.servlet.http.HttpServletResponse` object `getOutputStream` aan te roepen.
   * Maak een bytearray en vul deze door de methode `getBinaryData` van het object `BLOB` aan te roepen. Hierdoor wordt de inhoud van het `FormsResult` -object toegewezen aan de bytearray.
   * Roep de methode `write` van het object `javax.servlet.http.HttpServletResponse` aan om de gegevensstroom van het formulier naar de webbrowser van de client te verzenden. Geef de bytearray door aan de methode `write` .

**zie ook**

[HTML Forms renderen met aangepaste CSS-bestanden](#rendering-html-forms-using-custom-css-files)

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
