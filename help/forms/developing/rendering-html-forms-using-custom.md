---
title: HTML Forms renderen met aangepaste CSS-bestanden
seo-title: HTML Forms renderen met aangepaste CSS-bestanden
description: 'null'
seo-description: 'null'
uuid: a44e96f1-001d-48a2-8c96-15cb9d0c71b3
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 8fe7c072-7df0-44b7-92d0-bf39dc1e688a
translation-type: tm+mt
source-git-commit: fcbe1d860410e215cb7c438f94579e0b14d262a5
workflow-type: tm+mt
source-wordcount: '1640'
ht-degree: 0%

---


# HTML Forms renderen met aangepaste CSS-bestanden {#rendering-html-forms-using-custom-css-files}

De Forms-service geeft HTML-formulieren weer als reactie op een HTTP-aanvraag van een webbrowser. Bij het weergeven van een HTML-formulier kan de Forms-service verwijzen naar een aangepast CSS-bestand. U kunt een aangepast CSS-bestand maken dat voldoet aan uw zakelijke vereisten en naar dat CSS-bestand verwijzen wanneer u de Forms-service gebruikt om HTML-formulieren te genereren.

De Forms-service parseert het aangepaste CSS-bestand ongemerkt. De Forms-service rapporteert dus geen fouten die kunnen worden aangetroffen als het aangepaste CSS-bestand niet voldoet aan CSS-standaarden. In dit geval negeert de Forms-service de stijl en gaat deze verder met de resterende stijlen in het CSS-bestand.

In de volgende lijst worden stijlen weergegeven die in een aangepast CSS-bestand worden ondersteund:

* **Selector-stijlparen** op klasseniveau: Indien aanwezig in een aangepast CSS-bestand, worden in het HTML-formulier als klassenstijlen gebruikte kiezers gebruikt. Ongebruikte klassenstijlen worden genegeerd.
* **Selector-stijlparen** op herkenningsniveau: Alle id-stijlen worden gebruikt als deze in het HTML-formulier worden gebruikt.
* **Selector-stijlparen** op elementniveau: Alle elementstijlen worden gebruikt als ze in het HTML-formulier worden gebruikt.
* **Stijlprioriteit**: Stijlprioriteit (zoals belangrijk) wordt ondersteund en kan worden gebruikt in een aangepast CSS-bestand.
* **Mediatype**: Een of meer combinaties in selectorstijl kunnen in @media-stijl worden opgenomen om het mediatype te definiëren. De Forms-service controleert niet of het opgegeven mediatype wordt ondersteund. Het mediatype dat is opgegeven in het aangepaste CSS-bestand wordt samengevoegd in het HTML-formulier.

U kunt een voorbeeld-CSS-bestand ophalen met de FormsIVS-toepassing. Upload het formulier, selecteer het op de pagina Formulierontwerp testen en klik op CSS genereren. U hoeft het transformatietype voor HTML niet in te stellen voordat u op de knop klikt. Selecteer vervolgens Opslaan. U kunt dit CSS-bestand bewerken om aan uw zakelijke vereisten te voldoen.

>[!NOTE]
>
>Voordat u een HTML-formulier rendert dat gebruikmaakt van een aangepast CSS-bestand, is het belangrijk dat u goed begrijpt hoe HTML-formulieren worden weergegeven. (Zie [Forms renderen als HTML](/help/forms/developing/rendering-forms-html.md).)

>[!NOTE]
>
>Zie [Referentiehandleiding voor services voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63) voor meer informatie over de Forms-service.

## Overzicht van stappen {#summary-of-steps}

Voer de volgende taken uit om een HTML-formulier te genereren dat een CSS-bestand gebruikt:

1. Inclusief projectbestanden.
1. Maak een Forms Java API-object.
1. Verwijs naar het CSS-bestand.
1. Een HTML-formulier renderen.
1. Schrijf de gegevensstroom van het formulier naar de webbrowser van de client.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**Een Forms Java API-object maken**

Voordat u een door de Forms-service ondersteunde bewerking programmatisch kunt uitvoeren, moet u een Forms-clientobject maken.

**Verwijzen naar het CSS-bestand**

Als u een HTML-formulier wilt genereren waarin een aangepast CSS-bestand wordt gebruikt, moet u controleren of u naar een bestaand CSS-bestand verwijst.

**Een HTML-formulier renderen**

Als u een HTML-formulier wilt genereren, moet u een formulierontwerp opgeven dat in Designer is gemaakt en als XDP-bestand is opgeslagen. U moet ook een transformatietype voor HTML selecteren. U kunt bijvoorbeeld het transformatietype HTML opgeven dat een dynamische HTML voor Internet Explorer 5.0 of hoger rendert.

Voor het weergeven van een HTML-formulier zijn ook waarden vereist, zoals URI-waarden die nodig zijn om andere formuliertypen te genereren.

**De formuliergegevensstroom naar de webbrowser van de client schrijven**

Wanneer de Forms-service een HTML-formulier genereert, wordt een formuliergegevensstroom geretourneerd die u naar de webbrowser van de client moet schrijven om het HTML-formulier zichtbaar te maken voor de gebruiker.

**Zie ook**

[Een HTML-formulier renderen dat een CSS-bestand gebruikt met de Java API](#render-an-html-form-that-uses-a-css-file-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Forms Service API Quick Start](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Interactieve PDF forms renderen](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Forms renderen als HTML](/help/forms/developing/rendering-forms-html.md)

[Webtoepassingen maken die Forms renderen](/help/forms/developing/creating-web-applications-renders-forms.md)

## Een HTML-formulier weergeven dat een CSS-bestand gebruikt met de Java API {#render-an-html-form-that-uses-a-css-file-using-the-java-api}

Een HTML-formulier renderen dat een aangepast CSS-bestand gebruikt met de Forms API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-forms-client.jar, op in het klassenpad van uw Java-project.

1. Een Forms Java API-object maken

   * Maak een `ServiceClientFactory`-object dat verbindingseigenschappen bevat.
   * Maak een `FormsServiceClient`-object door de constructor ervan te gebruiken en het object `ServiceClientFactory` door te geven.

1. Verwijzen naar het CSS-bestand

   * Maak een `HTMLRenderSpec`-object met de constructor ervan.
   * Als u het HTML-formulier wilt renderen dat een aangepast CSS-bestand gebruikt, roept u de methode `setCustomCSSURI` van het object `HTMLRenderSpec` aan en geeft u een tekenreekswaarde door die de locatie en naam van het CSS-bestand opgeeft.

1. Een HTML-formulier renderen

   Roep de methode `(Deprecated) (Deprecated) renderHTMLForm` van het object `FormsServiceClient` aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u naar een formulierontwerp verwijst dat deel uitmaakt van een Forms-toepassing, moet u het volledige pad opgeven, bijvoorbeeld `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Een opsommingswaarde `TransformTo` die het HTML-voorkeurstype aangeeft. Als u bijvoorbeeld een HTML-formulier wilt genereren dat compatibel is met dynamische HTML voor Internet Explorer 5.0 of hoger, geeft u `TransformTo.MSDHTML` op.
   * Een object `com.adobe.idp.Document` dat gegevens bevat die met het formulier moeten worden samengevoegd. Als u geen gegevens wilt samenvoegen, geeft u een leeg `com.adobe.idp.Document`-object door.
   * Het `HTMLRenderSpec`-object waarin de HTML-runtime-opties zijn opgeslagen.
   * Een tekenreekswaarde die de koptekstwaarde `HTTP_USER_AGENT` opgeeft, zoals `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
   * Een object `URLSpec` dat URI-waarden opslaat die vereist zijn om een HTML-formulier te genereren.
   * Een `java.util.HashMap`-object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt `null` opgeven als u geen bestanden aan het formulier wilt koppelen.

   De methode `(Deprecated) renderHTMLForm` retourneert een `FormsResult`-object dat een formuliergegevensstroom bevat die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Maak een `com.adobe.idp.Document`-object door de methode `getOutputContent` van het object aan te roepen.`FormsResult`
   * Hiermee wordt het inhoudstype van het object `com.adobe.idp.Document` opgehaald door de methode `getContentType` ervan aan te roepen.
   * Stel het inhoudstype van het object `javax.servlet.http.HttpServletResponse` in door de methode `setContentType` ervan aan te roepen en het inhoudstype van het object `com.adobe.idp.Document` door te geven.
   * Maak een `javax.servlet.ServletOutputStream`-object dat wordt gebruikt om de formuliergegevensstroom naar de webbrowser van de client te schrijven door de methode `javax.servlet.h\ttp.HttpServletResponse` van het object `getOutputStream` aan te roepen.
   * Maak een `java.io.InputStream`-object door de methode `getInputStream` van het object `com.adobe.idp.Document` aan te roepen.
   * Maak een bytearray en vul deze met de formuliergegevensstroom door de methode `read` van het object `InputStream` aan te roepen en de bytearray als een argument door te geven.
   * Roep de methode `javax.servlet.ServletOutputStream` van het object `write` aan om de gegevensstroom van het formulier naar de webbrowser van de client te verzenden. Geef de bytearray door aan de methode `write`.

**Zie ook**

[HTML Forms renderen met aangepaste CSS-bestanden](#rendering-html-forms-using-custom-css-files)

[Snel starten (SOAP-modus): HTML-formulieren renderen die een CSS-bestand gebruiken met de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-an-html-form-that-uses-a-css-file-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Een HTML-formulier renderen dat een CSS-bestand gebruikt met de webservice-API {#render-an-html-form-that-uses-a-css-file-using-the-web-service-api}

Een HTML-formulier renderen dat een aangepast CSS-bestand gebruikt met de Forms API (webservice):

1. Projectbestanden opnemen

   * Maak Java-proxyklassen die gebruikmaken van de Forms-service WSDL.
   * Neem de Java-proxyklassen op in het klassenpad.

1. Een Forms Java API-object maken

   Maak een `FormsService`-object en stel de verificatiewaarden in.

1. Verwijzen naar het CSS-bestand

   * Maak een `HTMLRenderSpec`-object met de constructor ervan.
   * Als u het HTML-formulier wilt renderen dat een aangepast CSS-bestand gebruikt, roept u de methode `setCustomCSSURI` van het object `HTMLRenderSpec` aan en geeft u een tekenreekswaarde door die de locatie en naam van het CSS-bestand opgeeft.

1. Een HTML-formulier renderen

   Roep de methode `(Deprecated) renderHTMLForm` van het object `FormsService` aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u naar een formulierontwerp verwijst dat deel uitmaakt van een Forms-toepassing, moet u het volledige pad opgeven, bijvoorbeeld `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Een opsommingswaarde `TransformTo` die het HTML-voorkeurstype aangeeft. Als u bijvoorbeeld een HTML-formulier wilt genereren dat compatibel is met dynamische HTML voor Internet Explorer 5.0 of hoger, geeft u `TransformTo.MSDHTML` op.
   * Een object `BLOB` dat gegevens bevat die met het formulier moeten worden samengevoegd. Als u geen gegevens wilt samenvoegen, geeft u `null` door. (Zie [Forms vooraf vullen met stroombare layouts](/help/forms/developing/prepopulating-forms-flowable-layouts.md).)
   * Het `HTMLRenderSpec`-object waarin de HTML-runtime-opties zijn opgeslagen.
   * Een tekenreekswaarde die de koptekstwaarde `HTTP_USER_AGENT` opgeeft, zoals `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`. U kunt een lege tekenreeks doorgeven als u deze waarde niet wilt instellen.
   * Een object `URLSpec` dat URI-waarden opslaat die vereist zijn om een HTML-formulier te genereren.
   * Een `java.util.HashMap`-object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt `null` opgeven als u geen bestanden aan het formulier wilt koppelen.
   * Een leeg object `com.adobe.idp.services.holders.BLOBHolder` dat wordt gevuld door de methode `(Deprecated) renderHTMLForm`. Met deze parameterwaarde wordt het gerenderde formulier opgeslagen.
   * Een leeg object `com.adobe.idp.services.holders.BLOBHolder` dat wordt gevuld door de methode `(Deprecated) renderHTMLForm`. In deze parameter worden de XML-uitvoergegevens opgeslagen.
   * Een leeg object `javax.xml.rpc.holders.LongHolder` dat wordt gevuld door de methode `(Deprecated) renderHTMLForm`. In dit argument wordt het aantal pagina&#39;s in het formulier opgeslagen.
   * Een leeg object `javax.xml.rpc.holders.StringHolder` dat wordt gevuld door de methode `(Deprecated) renderHTMLForm`. In dit argument wordt de waarde van de landinstelling opgeslagen.
   * Een leeg object `javax.xml.rpc.holders.StringHolder` dat wordt gevuld door de methode `(Deprecated) renderHTMLForm`. In dit argument wordt de gebruikte HTML-renderwaarde opgeslagen.
   * Een leeg `com.adobe.idp.services.holders.FormsResultHolder`-object dat de resultaten van deze bewerking zal bevatten.

   Met de methode `(Deprecated) renderHTMLForm` wordt het object `com.adobe.idp.services.holders.FormsResultHolder` dat als laatste argumentwaarde is doorgegeven, gevuld met een formuliergegevensstroom die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Maak een `FormResult`-object door de waarde op te halen van het `com.adobe.idp.services.holders.FormsResultHolder`-gegevenslid van het object.`value`
   * Maak een `BLOB`-object dat formuliergegevens bevat door de methode `getOutputContent` van het object `FormsResult` aan te roepen.
   * Hiermee wordt het inhoudstype van het object `BLOB` opgehaald door de methode `getContentType` ervan aan te roepen.
   * Stel het inhoudstype van het object `javax.servlet.http.HttpServletResponse` in door de methode `setContentType` ervan aan te roepen en het inhoudstype van het object `BLOB` door te geven.
   * Maak een `javax.servlet.ServletOutputStream`-object dat wordt gebruikt om de formuliergegevensstroom naar de webbrowser van de client te schrijven door de methode `javax.servlet.http.HttpServletResponse` van het object `getOutputStream` aan te roepen.
   * Maak een bytearray en vul deze door de methode `getBinaryData` van het object `BLOB` aan te roepen. Deze taak wijst de inhoud van het `FormsResult` voorwerp aan de byteserie toe.
   * Roep de methode `javax.servlet.http.HttpServletResponse` van het object `write` aan om de gegevensstroom van het formulier naar de webbrowser van de client te verzenden. Geef de bytearray door aan de methode `write`.

**Zie ook**

[HTML Forms renderen met aangepaste CSS-bestanden](#rendering-html-forms-using-custom-css-files)

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
