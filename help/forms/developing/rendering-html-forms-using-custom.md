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
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1682'
ht-degree: 0%

---

# HTML Forms renderen met aangepaste CSS-bestanden {#rendering-html-forms-using-custom-css-files}

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

De Forms-service geeft HTML-formulieren weer als reactie op een HTTP-aanvraag van een webbrowser. Bij het weergeven van een HTML-formulier kan de Forms-service verwijzen naar een aangepast CSS-bestand. U kunt een aangepast CSS-bestand maken dat voldoet aan uw zakelijke vereisten en u kunt naar dat CSS-bestand verwijzen wanneer u de Forms-service gebruikt om HTML-formulieren te genereren.

De Forms-service parseert het aangepaste CSS-bestand ongemerkt. De Forms-service rapporteert dus geen fouten die kunnen worden aangetroffen als het aangepaste CSS-bestand niet voldoet aan CSS-standaarden. In dit geval negeert de Forms-service de stijl en gaat deze verder met de resterende stijlen in het CSS-bestand.

In de volgende lijst worden stijlen weergegeven die in een aangepast CSS-bestand worden ondersteund:

* **Selector-stijlparen op klasseniveau**: Indien aanwezig in een aangepast CSS-bestand, worden kiezers gebruikt die in het HTML-formulier als klassenstijlen worden gebruikt. Ongebruikte klassenstijlen worden genegeerd.
* **Selector-stijlparen op niveau van id**: Alle id-stijlen worden gebruikt als deze in het HTML-formulier worden gebruikt.
* **Paren op elementniveau met selectorstijl**: Alle elementstijlen worden gebruikt als deze in het HTML-formulier worden gebruikt.
* **Stijlprioriteit**: Stijlprioriteit (zoals belangrijk) wordt ondersteund en kan worden gebruikt in een aangepast CSS-bestand.
* **Mediatype**: Een of meer paren in selectorstijl kunnen worden opgenomen in @media-stijl om het mediatype te definiëren. De Forms-service controleert niet of het opgegeven mediatype wordt ondersteund. Het mediatype dat is opgegeven in het aangepaste CSS-bestand wordt samengevoegd in het HTML-formulier.

U kunt een voorbeeld-CSS-bestand ophalen met de FormsIVS-toepassing. Upload het formulier, selecteer het op de pagina Formulierontwerp testen en klik op CSS genereren. U hoeft het transformatietype HTML niet in te stellen voordat u op de knop klikt. Selecteer vervolgens Opslaan. U kunt dit CSS-bestand bewerken om aan uw zakelijke vereisten te voldoen.

>[!NOTE]
>
>Voordat u een HTML-formulier rendert dat een aangepast CSS-bestand gebruikt, is het belangrijk dat u goed begrijpt hoe HTML-formulieren worden weergegeven. (Zie [Forms renderen als HTML](/help/forms/developing/rendering-forms-html.md).)

>[!NOTE]
>
>Voor meer informatie over de Forms-service raadpleegt u [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Overzicht van de stappen {#summary-of-steps}

Voer de volgende taken uit om een HTML-formulier te genereren dat een CSS-bestand gebruikt:

1. Inclusief projectbestanden.
1. Maak een Forms Java API-object.
1. Verwijs naar het CSS-bestand.
1. Een HTML-formulier weergeven.
1. Schrijf de gegevensstroom van het formulier naar de webbrowser van de client.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**Een Forms Java API-object maken**

Voordat u een door de Forms-service ondersteunde bewerking programmatisch kunt uitvoeren, moet u een Forms-clientobject maken.

**Verwijzen naar het CSS-bestand**

Als u een HTML-formulier wilt genereren waarin een aangepast CSS-bestand wordt gebruikt, moet u controleren of u naar een bestaand CSS-bestand verwijst.

**Een HTML-formulier renderen**

Als u een HTML-formulier wilt genereren, geeft u een formulierontwerp op dat in Designer is gemaakt en als XDP-bestand is opgeslagen. Selecteer een transformatietype HTML. U kunt bijvoorbeeld het transformatietype HTML opgeven waarmee een dynamische HTML wordt weergegeven voor Internet Explorer 5.0 of hoger.

Voor het weergeven van een HTML-formulier zijn ook waarden vereist, zoals URI-waarden die nodig zijn om andere formuliertypen te genereren.

**De formuliergegevensstroom naar de webbrowser van de client schrijven**

Wanneer de Forms-service een HTML-formulier weergeeft, wordt een formuliergegevensstroom geretourneerd die u naar de webbrowser van de client moet schrijven om het HTML-formulier zichtbaar te maken voor de gebruiker.

**Zie ook**

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

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `FormsServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Verwijzen naar het CSS-bestand

   * Een `HTMLRenderSpec` object met behulp van de constructor.
   * Als u het HTML-formulier wilt genereren waarin een aangepast CSS-bestand wordt gebruikt, roept u de `HTMLRenderSpec` object `setCustomCSSURI` en geeft een tekenreekswaarde door die de locatie en naam van het CSS-bestand opgeeft.

1. Een HTML-formulier renderen

   De `FormsServiceClient` object `(Deprecated) (Deprecated) renderHTMLForm` en geeft de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u naar een formulierontwerp verwijst dat deel uitmaakt van een Forms-toepassing, moet u het volledige pad opgeven, zoals `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `TransformTo` Enum value that specifies the HTML preferences type. Als u bijvoorbeeld een HTML-formulier wilt genereren dat compatibel is met dynamic HTML voor Internet Explorer 5.0 of hoger, geeft u `TransformTo.MSDHTML`.
   * A `com.adobe.idp.Document` object dat gegevens bevat die met het formulier moeten worden samengevoegd. Als u geen gegevens wilt samenvoegen, geeft u een lege waarde door `com.adobe.idp.Document` object.
   * De `HTMLRenderSpec` -object waarin HTML-runtime-opties zijn opgeslagen.
   * Een tekenreekswaarde die de `HTTP_USER_AGENT` koptekstwaarde, zoals `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
   * A `URLSpec` object dat URI-waarden opslaat die vereist zijn om een HTML-formulier te genereren.
   * A `java.util.HashMap` object waarin bestandsbijlagen zijn opgeslagen. Dit is een optionele parameter en u kunt `null` als u geen bestanden aan het formulier wilt koppelen.

   De `(Deprecated) renderHTMLForm` methode retourneert een `FormsResult` object dat een formuliergegevensstroom bevat die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Een `com.adobe.idp.Document` door het object aan te roepen `FormsResult` object `getOutputContent` methode.
   * Hiermee wordt het inhoudstype van het dialoogvenster `com.adobe.idp.Document` object aanroepen `getContentType` methode.
   * Stel de `javax.servlet.http.HttpServletResponse` inhoudstype van object aanroepen `setContentType` en geeft u het inhoudstype van de `com.adobe.idp.Document` object.
   * Een `javax.servlet.ServletOutputStream` object dat wordt gebruikt om de formuliergegevensstroom naar de webbrowser van de client te schrijven door het aanroepen van de `javax.servlet.h\ttp.HttpServletResponse` object `getOutputStream` methode.
   * Een `java.io.InputStream` door het object aan te roepen `com.adobe.idp.Document` object `getInputStream` methode.
   * Maak een bytearray en vul deze met de formuliergegevensstroom door de `InputStream` object `read` en de bytearray doorgeven als een argument.
   * De `javax.servlet.ServletOutputStream` object `write` methode om de formuliergegevensstroom naar de webbrowser van de client te verzenden. Geef de bytearray door aan de `write` methode.

**Zie ook**

[HTML Forms renderen met aangepaste CSS-bestanden](#rendering-html-forms-using-custom-css-files)

[Snel starten (SOAP-modus): een HTML-formulier weergeven dat een CSS-bestand gebruikt met de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-an-html-form-that-uses-a-css-file-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Een HTML-formulier renderen dat een CSS-bestand gebruikt met de webservice-API {#render-an-html-form-that-uses-a-css-file-using-the-web-service-api}

Een HTML-formulier renderen dat een aangepast CSS-bestand gebruikt met de Forms API (webservice):

1. Projectbestanden opnemen

   * Maak Java-proxyklassen die gebruikmaken van de Forms-service WSDL.
   * Neem de Java-proxyklassen op in het klassenpad.

1. Een Forms Java API-object maken

   Een `FormsService` -object en stel verificatiewaarden in.

1. Verwijzen naar het CSS-bestand

   * Een `HTMLRenderSpec` object met behulp van de constructor.
   * Als u het HTML-formulier wilt genereren waarin een aangepast CSS-bestand wordt gebruikt, roept u de `HTMLRenderSpec` object `setCustomCSSURI` en geeft een tekenreekswaarde door die de locatie en naam van het CSS-bestand opgeeft.

1. Een HTML-formulier renderen

   De `FormsService` object `(Deprecated) renderHTMLForm` en geeft de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u naar een formulierontwerp verwijst dat deel uitmaakt van een Forms-toepassing, moet u het volledige pad opgeven, zoals `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `TransformTo` Enum value that specifies the HTML preferences type. Als u bijvoorbeeld een HTML-formulier wilt genereren dat compatibel is met dynamic HTML voor Internet Explorer 5.0 of hoger, geeft u `TransformTo.MSDHTML`.
   * A `BLOB` object dat gegevens bevat die met het formulier moeten worden samengevoegd. Als u geen gegevens wilt samenvoegen, geeft u `null`. (Zie [Forms vooraf vullen met stroombare indelingen](/help/forms/developing/prepopulating-forms-flowable-layouts.md).)
   * De `HTMLRenderSpec` -object waarin HTML-runtime-opties zijn opgeslagen.
   * Een tekenreekswaarde die de `HTTP_USER_AGENT` koptekstwaarde, zoals `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`. U kunt een lege tekenreeks doorgeven als u deze waarde niet wilt instellen.
   * A `URLSpec` object dat URI-waarden opslaat die vereist zijn om een HTML-formulier te genereren.
   * A `java.util.HashMap` object waarin bestandsbijlagen zijn opgeslagen. Dit is een optionele parameter en u kunt `null` als u geen bestanden aan het formulier wilt koppelen.
   * Een leeg `com.adobe.idp.services.holders.BLOBHolder` object dat wordt gevuld door het `(Deprecated) renderHTMLForm` methode. Met deze parameterwaarde wordt het gerenderde formulier opgeslagen.
   * Een leeg `com.adobe.idp.services.holders.BLOBHolder` object dat wordt gevuld door het `(Deprecated) renderHTMLForm` methode. In deze parameter worden de XML-uitvoergegevens opgeslagen.
   * Een leeg `javax.xml.rpc.holders.LongHolder` object dat wordt gevuld door het `(Deprecated) renderHTMLForm` methode. In dit argument wordt het aantal pagina&#39;s in het formulier opgeslagen.
   * Een leeg `javax.xml.rpc.holders.StringHolder` object dat wordt gevuld door het `(Deprecated) renderHTMLForm` methode. In dit argument wordt de waarde van de landinstelling opgeslagen.
   * Een leeg `javax.xml.rpc.holders.StringHolder` object dat wordt gevuld door het `(Deprecated) renderHTMLForm` methode. In dit argument wordt de gebruikte HTML-renderwaarde opgeslagen.
   * Een leeg `com.adobe.idp.services.holders.FormsResultHolder` -object dat de resultaten van deze bewerking zal bevatten.

   De `(Deprecated) renderHTMLForm` wordt de `com.adobe.idp.services.holders.FormsResultHolder` object dat wordt doorgegeven als de laatste argumentwaarde met een formuliergegevensstroom die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Een `FormResult` object door de waarde van het object op te halen `com.adobe.idp.services.holders.FormsResultHolder` object `value` lid.
   * Een `BLOB` object dat formuliergegevens bevat door het `FormsResult` object `getOutputContent` methode.
   * Hiermee wordt het inhoudstype van het dialoogvenster `BLOB` object aanroepen `getContentType` methode.
   * Stel de `javax.servlet.http.HttpServletResponse` inhoudstype van object aanroepen `setContentType` en geeft u het inhoudstype van de `BLOB` object.
   * Een `javax.servlet.ServletOutputStream` object dat wordt gebruikt om de formuliergegevensstroom naar de webbrowser van de client te schrijven door het aanroepen van de `javax.servlet.http.HttpServletResponse` object `getOutputStream` methode.
   * Maak een bytearray en vul deze door het `BLOB` object `getBinaryData` methode. Deze taak wijst de inhoud van toe `FormsResult` object naar de bytearray.
   * De `javax.servlet.http.HttpServletResponse` object `write` methode om de formuliergegevensstroom naar de webbrowser van de client te verzenden. Geef de bytearray door aan de `write` methode.

**Zie ook**

[HTML Forms renderen met aangepaste CSS-bestanden](#rendering-html-forms-using-custom-css-files)

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
