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
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1822'
ht-degree: 0%

---

# Forms renderen op waarde {#rendering-forms-by-value}

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

Een formulierontwerp dat in Designer is gemaakt, wordt meestal doorgegeven via de Forms-service. Formulierontwerpen kunnen groot zijn en daarom is het efficiënter om ze door te geven als verwijzing, zodat het niet nodig is om bytes in het formulierontwerp op waarde te rangschikken. De Forms-service kan het formulierontwerp ook in cache plaatsen, zodat het formulierontwerp niet voortdurend hoeft te worden gelezen wanneer het in cache wordt geplaatst.

Als een formulierontwerp een UUID-kenmerk bevat, wordt het in de cache opgeslagen. De UUID-waarde is uniek voor alle formulierontwerpen en wordt gebruikt om een formulier op unieke wijze te identificeren. Als u een formulier op waarde weergeeft, mag het formulier alleen in de cache worden geplaatst wanneer het herhaaldelijk wordt gebruikt. Als het formulier echter niet herhaaldelijk wordt gebruikt en uniek moet zijn, kunt u voorkomen dat het formulier in cache wordt geplaatst met behulp van cacheopties die zijn ingesteld met de AEM Forms API.

De Forms-service kan ook de locatie van gekoppelde inhoud in het formulierontwerp oplossen. Bijvoorbeeld: gekoppelde afbeeldingen waarnaar in het formulierontwerp wordt verwezen, zijn relatieve URL&#39;s. Gekoppelde inhoud wordt altijd verondersteld relatief te zijn ten opzichte van de locatie van het formulierontwerp. Daarom is het oplossen van gekoppelde inhoud een kwestie van het bepalen van zijn plaats door de relatieve weg op de absolute plaats van het vormontwerp toe te passen.

In plaats van een formulierontwerp door te geven als referentie, kunt u een formulierontwerp op waarde doorgeven. Het doorgeven van een formulierontwerp op waarde is efficiënt wanneer een formulierontwerp dynamisch wordt gemaakt, dat wil zeggen wanneer een clienttoepassing de XML genereert die tijdens runtime een formulierontwerp maakt. In dit geval wordt een formulierontwerp niet opgeslagen in een fysieke opslagplaats, omdat het in het geheugen wordt opgeslagen. Als u tijdens de runtime dynamisch een formulierontwerp maakt en dit op waarde doorgeeft, kunt u het formulier in cache plaatsen en de prestaties van de Forms-service verbeteren.

**Beperkingen bij het doorgeven van een formulier op waarde**

De volgende beperkingen zijn van toepassing wanneer een formulierontwerp wordt doorgegeven als waarde:

* Er kan geen relatieve gekoppelde inhoud in het formulierontwerp voorkomen. Alle afbeeldingen en fragmenten moeten in het formulierontwerp worden ingesloten of absoluut worden vermeld.
* Berekeningen aan de serverzijde kunnen niet worden uitgevoerd nadat het formulier is gegenereerd. Als het formulier wordt teruggestuurd naar de Forms-service, worden de gegevens opgehaald en geretourneerd zonder berekeningen aan de serverzijde.
* Omdat HTML gekoppelde afbeeldingen alleen tijdens runtime kan gebruiken, is het niet mogelijk om HTML met ingesloten afbeeldingen te genereren. De reden hiervoor is dat de Forms-service ingesloten afbeeldingen met HTML ondersteunt door de afbeeldingen op te halen uit een formulierontwerp waarnaar wordt verwezen. Omdat een formulierontwerp dat via waarde wordt doorgegeven, geen locatie waarnaar wordt verwezen, kunnen ingesloten afbeeldingen niet worden uitgepakt wanneer de pagina HTML wordt weergegeven. Daarom moeten afbeeldingsverwijzingen absolute paden zijn die moeten worden gerenderd in HTML.

>[!NOTE]
>
>Hoewel u verschillende typen formulieren op waarde kunt weergeven (bijvoorbeeld HTML-formulieren of formulieren die gebruiksrechten bevatten), wordt in deze sectie de rendering van interactieve PDF forms besproken.

>[!NOTE]
>
>Voor meer informatie over de Forms-service raadpleegt u [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

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

Voordat u via programmacode gegevens kunt importeren in een PDF formulier-client-API, moet u een Data Integration-service-client maken. Wanneer u een serviceclient maakt, definieert u verbindingsinstellingen die vereist zijn om een service aan te roepen.

**Verwijzen naar het formulierontwerp**

Wanneer u een formulier op waarde weergeeft, moet u een `com.adobe.idp.Document` object dat het formulierontwerp bevat dat moet worden weergegeven. U kunt verwijzen naar een bestaand XDP-bestand of u kunt tijdens runtime dynamisch een formulierontwerp maken en een `com.adobe.idp.Document` met die gegevens.

>[!NOTE]
>
>Deze sectie en de bijbehorende snelstartverwijzingen verwijzen naar een bestaand XDP-bestand.

**Een formulier op waarde weergeven**

Als u een formulier op waarde wilt weergeven, geeft u een `com.adobe.idp.Document` instantie die het formulierontwerp bevat voor de rendermethode `inDataDoc` parameter (kan elk van de `FormsServiceClient` rendermethoden van object, zoals `renderPDFForm`, `(Deprecated) renderHTMLForm`, enzovoort). Deze parameterwaarde is gewoonlijk gereserveerd voor gegevens die met het formulier worden samengevoegd. Geef op dezelfde manier een lege tekenreekswaarde door aan de `formQuery` parameter. Normaal gesproken vereist deze parameter een tekenreekswaarde die de naam van het formulierontwerp opgeeft.

>[!NOTE]
>
>Als u gegevens in het formulier wilt weergeven, moeten de gegevens worden opgegeven in het dialoogvenster `xfa:datasets` element. Ga voor informatie over XFA-architectuur naar [https://www.pdfa.org/norm-refs/XFA-3_3.pdf](https://www.pdfa.org/norm-refs/XFA-3_3.pdf).

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

## Een formulier op waarde weergeven met de Java API {#render-a-form-by-value-using-the-java-api}

Een formulier op waarde weergeven met de Forms API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-forms-client.jar, op in het klassepad van uw Java-project.

1. Een Forms Client API-object maken

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `FormsServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Verwijzen naar het formulierontwerp

   * Een `java.io.FileInputStream` object dat staat voor het formulierontwerp dat moet worden gegenereerd met de constructor ervan en dat een tekenreekswaarde doorgeeft die de locatie van het XDP-bestand aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. Een formulier op waarde weergeven

   De `FormsServiceClient` object `renderPDFForm` en geeft de volgende waarden door:

   * Een lege tekenreeks. (Normaal gesproken vereist deze parameter een tekenreekswaarde die de naam van het formulierontwerp aangeeft.)
   * A `com.adobe.idp.Document` object dat het formulierontwerp bevat. Normaal gesproken is deze parameterwaarde gereserveerd voor gegevens die met het formulier worden samengevoegd.
   * A `PDFFormRenderSpec` -object dat uitvoeringsopties opslaat. Dit is een optionele parameter en u kunt `null` als u geen runtime opties wilt opgeven.
   * A `URLSpec` object dat URI-waarden bevat die door de Forms-service worden vereist.
   * A `java.util.HashMap` object waarin bestandsbijlagen zijn opgeslagen. Dit is een optionele parameter en u kunt `null` als u geen bestanden aan het formulier wilt koppelen.

   De `renderPDFForm` methode retourneert een `FormsResult` object dat een formuliergegevensstroom bevat die naar de webbrowser van de client kan worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Een `com.adobe.idp.Document` door het object aan te roepen `FormsResult` object `getOutputContent` methode.
   * Hiermee wordt het inhoudstype van het dialoogvenster `com.adobe.idp.Document` object aanroepen `getContentType` methode.
   * Stel de `javax.servlet.http.HttpServletResponse` inhoudstype van object aanroepen `setContentType` en geeft u het inhoudstype van de `com.adobe.idp.Document` object.
   * Een `javax.servlet.ServletOutputStream` object dat wordt gebruikt om de formuliergegevensstroom naar de webbrowser van de client te schrijven door het aanroepen van de `javax.servlet.http.HttpServletResponse` object `getOutputStream` methode.
   * Een `java.io.InputStream` door het object aan te roepen `com.adobe.idp.Document` object `getInputStream` methode.
   * Maak een bytearray en wijs de grootte van de array toe `InputStream` object. De `InputStream` object `available` om de grootte van de `InputStream` object.
   * Vul de bytearray met de formuliergegevensstroom door de `InputStream` object `read`en de bytearray doorgeven als een argument.
   * De `javax.servlet.ServletOutputStream` object `write` methode om de formuliergegevensstroom naar de webbrowser van de client te verzenden. Geef de bytearray door aan de `write` methode.

**Zie ook**

[Forms renderen op waarde](/help/forms/developing/rendering-forms.md)

[Snel starten (SOAP-modus): renderen op waarde met behulp van de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-by-value-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Een formulier op waarde weergeven met de API voor webservices {#render-a-form-by-value-using-the-web-service-api}

Een formulier op waarde weergeven met de Forms API (webservice):

1. Projectbestanden opnemen

   * Maak Java-proxyklassen die gebruikmaken van de Forms-service WSDL.
   * Neem de Java-proxyklassen op in het klassepad.

1. Een Forms Client API-object maken

   Een `FormsService` -object en stel verificatiewaarden in.

1. Verwijzen naar het formulierontwerp

   * Een `java.io.FileInputStream` object met behulp van de constructor. Geef een tekenreekswaarde door die de locatie van het XDP-bestand aangeeft.
   * Een `BLOB` object met behulp van de constructor. De `BLOB` wordt gebruikt om een PDF-document op te slaan dat met een wachtwoord is versleuteld.
   * Maak een bytearray waarin de inhoud van de `java.io.FileInputStream` object. U kunt de grootte van de bytearray bepalen door de `java.io.FileInputStream` objectgrootte met behulp van `available` methode.
   * De bytearray vullen met streamgegevens door de `java.io.FileInputStream` object `read` en geeft u de bytearray door.
   * Vul de `BLOB` object aanroepen `setBinaryData` en geeft u de bytearray door.

1. Een formulier op waarde weergeven

   De `FormsService` object `renderPDFForm` en geeft de volgende waarden door:

   * Een lege tekenreeks. (Normaal gesproken vereist deze parameter een tekenreekswaarde die de naam van het formulierontwerp aangeeft.)
   * A `BLOB` object dat het formulierontwerp bevat. Normaal gesproken is deze parameterwaarde gereserveerd voor gegevens die met het formulier worden samengevoegd.
   * A `PDFFormRenderSpec` -object dat uitvoeringsopties opslaat. Dit is een optionele parameter en u kunt `null` als u geen runtime opties wilt opgeven.
   * A `URLSpec` object dat URI-waarden bevat die door de Forms-service worden vereist.
   * A `java.util.HashMap` object waarin bestandsbijlagen zijn opgeslagen. Dit is een optionele parameter en u kunt `null` als u geen bestanden aan het formulier wilt koppelen.
   * Een leeg `com.adobe.idp.services.holders.BLOBHolder` object dat door de methode wordt gevuld. Hiermee slaat u het gerenderde PDF formulier op.
   * Een leeg `javax.xml.rpc.holders.LongHolder` object dat door de methode wordt gevuld. (In dit argument wordt het aantal pagina&#39;s in het formulier opgeslagen.)
   * Een leeg `javax.xml.rpc.holders.StringHolder` object dat door de methode wordt gevuld. (In dit argument wordt de waarde van de landinstelling opgeslagen.)
   * Een leeg `com.adobe.idp.services.holders.FormsResultHolder` -object dat de resultaten van deze bewerking zal bevatten.

   De `renderPDFForm` wordt de `com.adobe.idp.services.holders.FormsResultHolder` object dat wordt doorgegeven als de laatste argumentwaarde met een formuliergegevensstroom die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Een `FormResult` object door de waarde van het object op te halen `com.adobe.idp.services.holders.FormsResultHolder` object `value` lid.
   * Een `BLOB` object dat formuliergegevens bevat door het `FormsResult` object `getOutputContent` methode.
   * Hiermee wordt het inhoudstype van het dialoogvenster `BLOB` object aanroepen `getContentType` methode.
   * Stel de `javax.servlet.http.HttpServletResponse` inhoudstype van object aanroepen `setContentType` en geeft u het inhoudstype van de `BLOB` object.
   * Een `javax.servlet.ServletOutputStream` object dat wordt gebruikt om de formuliergegevensstroom naar de webbrowser van de client te schrijven door het aanroepen van de `javax.servlet.http.HttpServletResponse` object `getOutputStream` methode.
   * Maak een bytearray en vul deze door het `BLOB` object `getBinaryData` methode. Deze taak wijst de inhoud van toe `FormsResult` object naar de bytearray.
   * De `javax.servlet.http.HttpServletResponse` object `write` methode om de formuliergegevensstroom naar de webbrowser van de client te verzenden. Geef de bytearray door aan de `write` methode.

**Zie ook**

[Forms renderen op waarde](#rendering-forms-by-value)

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
