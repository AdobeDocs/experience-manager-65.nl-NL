---
title: Formulieren weergeven op basis van fragmenten
seo-title: Formulieren weergeven op basis van fragmenten
description: 'null'
seo-description: 'null'
uuid: 9c9a730d-f970-41f8-afed-4e6b6d3d393d
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: a65c5303-0ebd-43a9-a777-401042d8fcad
translation-type: tm+mt
source-git-commit: 413af4ef9bc3652e05da78d622183bcf20a8bee7

---


# Formulieren weergeven op basis van fragmenten {#rendering-forms-based-on-fragments}

## Formulieren weergeven op basis van fragmenten {#rendering-forms-based-on-fragments-inner}

Met de service Forms kunt u formulieren genereren op basis van fragmenten die u maakt met Designer. Een *fragment* is een herbruikbaar onderdeel van een formulier en wordt opgeslagen als een afzonderlijk XDP-bestand dat in meerdere formulierontwerpen kan worden ingevoegd. Een fragment kan bijvoorbeeld een adresblok of juridische tekst bevatten.

Met fragmenten kunt u het maken en beheren van grote aantallen formulieren vereenvoudigen en versnellen. Wanneer u een nieuw formulier maakt, voegt u een verwijzing in naar het gewenste fragment en het fragment wordt in het formulier weergegeven. De fragmentverwijzing bevat een subformulier dat naar het fysieke XDP-bestand wijst. Zie [Forms Designer voor informatie over het maken van formulierontwerpen op basis van fragmenten](https://www.adobe.com/go/learn_aemforms_designer_63)

Een fragment kan meerdere subformulieren bevatten die zijn ondergebracht in een gekozen subformulierset. De gekozen subformuliersets bepalen de weergave van subformulieren op basis van de gegevensstroom van een gegevensverbinding. U gebruikt voorwaardelijke instructies om te bepalen welk subformulier in de set in het resulterende formulier wordt weergegeven. Elk subformulier in een set kan bijvoorbeeld informatie voor een bepaalde geografische locatie bevatten en het weergegeven subformulier kan worden bepaald op basis van de locatie van de gebruiker.

A *script fragment* contains reusable JavaScript functions or values that are stored separately from any particular object, such as a date parser or a web service invocation. Deze fragmenten omvatten een enkel scriptobject dat als onderliggend element van variabelen in het palet Hiërarchie voorkomt. Fragmenten kunnen niet worden gemaakt op basis van scripts die eigenschappen zijn van andere objecten, zoals gebeurtenisscripts als valideren, berekenen of initialiseren.

Hier volgen enkele voordelen van het gebruik van fragmenten:

* **Inhoud opnieuw gebruiken**: Met fragmenten kunt u inhoud hergebruiken in meerdere formulierontwerpen. Als u bepaalde inhoud van dezelfde inhoud in meerdere formulieren wilt gebruiken, is het sneller en eenvoudiger om een fragment te gebruiken dan om de inhoud te kopiëren of opnieuw te maken. Fragmenten voor onderdelen die vaak voorkomen in een formulierontwerp, zorgen ook voor een consistente inhoud en weergave in alle formulieren die ernaar verwijzen.
* **Algemene updates**: Met fragmenten kunt u globale wijzigingen in meerdere formulieren slechts eenmaal aanbrengen, in één bestand. U kunt de inhoud, scriptobjecten, gegevensbindingen, lay-out of stijlen in een fragment wijzigen en alle XDP-formulieren die naar het fragment verwijzen, weerspiegelen de wijzigingen.
* Een gemeenschappelijk element in vele formulieren kan bijvoorbeeld een adresblok zijn dat een vervolgkeuzelijstobject voor het land bevat. Als u de waarden voor het vervolgkeuzelijstobject moet bijwerken, moet u vele formulieren openen om de wijzigingen aan te brengen. Als u het adresblok in een fragment opneemt, hoeft u slechts één fragmentbestand te openen om de wijzigingen aan te brengen.
* Als u een fragment in een PDF-formulier wilt bijwerken, moet u het formulier opnieuw opslaan in Designer.
* **Gedeeld formulier maken**: Met fragmenten kunt u de aanmaak van formulieren delen met verschillende bronnen. Formulierontwikkelaars met ervaring in het schrijven van scripts of andere geavanceerde functies van Designer, kunnen fragmenten maken en delen en zo de voordelen benutten van scripts en dynamische eigenschappen. Formulierontwerpers kunnen die fragmenten gebruiken voor de indeling van formulierontwerpen en ervoor zorgen dat alle onderdelen van een formulier een consistente weergave en functionaliteit hebben in meerdere formulieren die door meerdere mensen zijn ontworpen.

### Een formulierontwerp samenstellen dat is samengesteld met fragmenten {#assembling-a-form-design-assembled-using-fragments}

U kunt een formulierontwerp samenstellen om aan de service Forms door te geven op basis van meerdere fragmenten. Als u meerdere fragmenten wilt samenstellen, gebruikt u de Assembler-service. Zie PDF-documenten [](/help/forms/developing/creating-document-output-streams.md#creating-pdf-documents-using-fragments)maken met behulp van fragmenten voor een voorbeeld van het gebruik van de service Samenstellen om een formulierontwerp te maken dat wordt gebruikt door andere Forms-services (de service Uitvoer). In plaats van de service Uitvoer te gebruiken, kunt u dezelfde workflow uitvoeren met de service Formulieren.

Wanneer u de Assembler-service gebruikt, geeft u een formulierontwerp door dat is samengesteld met fragmenten. Het formulierontwerp dat is gemaakt, verwijst niet naar andere fragmenten. In dit onderwerp wordt daarentegen het doorgeven van een formulierontwerp besproken dat naar andere fragmenten verwijst naar de service Forms. Het formulierontwerp is echter niet samengesteld door Assembler. Het is gemaakt in Designer.

>[!NOTE]
>
>Voor meer informatie over de dienst van Vormen, zie de Verwijzing van de [Diensten voor Vormen](https://www.adobe.com/go/learn_aemforms_services_63)AEM.

>[!NOTE]
>
>Voor informatie over het creëren van een web-based toepassing die vormen teruggeeft die op fragmenten worden gebaseerd, zie het [Creëren van de Toepassingen van het Web die Vormen](/help/forms/developing/creating-web-applications-renders-forms.md)teruggeven.

### Overzicht van de stappen {#summary-of-steps}

Als u een formulier wilt genereren op basis van fragmenten, voert u de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak een Forms Client API-object.
1. Geef URI-waarden op.
1. Het formulier weergeven.
1. Schrijf de gegevensstroom van het formulier naar de webbrowser van de client.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**Een Forms Client API-object maken**

Voordat u een API-bewerking voor Forms-service programmatisch kunt uitvoeren, moet u een Forms-service-client maken.

**URI-waarden opgeven**

Als u een formulier wilt genereren op basis van fragmenten, moet u ervoor zorgen dat de Forms-service zowel het formulier als de fragmenten (de XDP-bestanden) kan vinden waarnaar het formulierontwerp verwijst. Stel bijvoorbeeld dat het formulier de naam PO.xdp heeft en dat in dit formulier twee fragmenten worden gebruikt: FooterUS.xdp en FooterCanada.xdp. In dit geval moet de Forms-service alle drie XDP-bestanden kunnen vinden.

U kunt een formulier en de bijbehorende fragmenten ordenen door het formulier op één locatie en de fragmenten op een andere locatie te plaatsen, of u kunt alle XDP-bestanden op dezelfde locatie plaatsen. In deze sectie wordt ervan uitgegaan dat alle XDP-bestanden zich in de opslagplaats van AEM Forms bevinden. Zie Bronnen [schrijven voor informatie over het plaatsen van XDP-bestanden in de opslagplaats van AEM-formulieren](/help/forms/developing/aem-forms-repository.md#writing-resources).

Bij het genereren van een formulier op basis van fragmenten moet u alleen naar het formulier zelf verwijzen en niet naar de fragmenten. U moet bijvoorbeeld naar PO.xdp verwijzen en niet naar FooterUS.xdp of FooterCanada.xdp. Plaats de fragmenten op een locatie waar de Forms-service ze kan vinden.

**Het formulier renderen**

Een formulier dat is gebaseerd op fragmenten, kan op dezelfde manier worden gegenereerd als niet-gefragmenteerde formulieren. U kunt het formulier dus weergeven als PDF-, HTML- of formulierhulplijnen (afgekeurd). In het voorbeeld in deze sectie wordt een formulier dat is gebaseerd op fragmenten, weergegeven als een interactief PDF-formulier. (Zie Interactieve PDF-formulieren [renderen](/help/forms/developing/rendering-interactive-pdf-forms.md).)

**De formuliergegevensstroom naar de webbrowser van de client schrijven**

Wanneer de service Forms een formulier genereert, wordt een formuliergegevensstroom geretourneerd die u naar de webbrowser van de client moet schrijven. Wanneer het formulier naar de webbrowser van de client wordt geschreven, is het zichtbaar voor de gebruiker.

**Zie ook**

[Formulieren weergeven op basis van fragmenten met de Java API](#render-forms-based-on-fragments-using-the-java-api)

[Formulieren renderen op basis van fragmenten met de webservice-API](#render-forms-based-on-fragments-using-the-web-service-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Forms Service API, snel aan de slag](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Interactieve PDF-formulieren renderen](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Webtoepassingen maken die formulieren renderen](/help/forms/developing/creating-web-applications-renders-forms.md)

### Formulieren weergeven op basis van fragmenten met de Java API {#render-forms-based-on-fragments-using-the-java-api}

Een formulier genereren op basis van fragmenten met de API voor formulieren (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-forms-client.jar, op in het klassenpad van uw Java-project.

1. Een Forms Client API-object maken

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `FormsServiceClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. URI-waarden opgeven

   * Maak een `URLSpec` object dat URI-waarden opslaat met de constructor ervan.
   * Roep de `URLSpec` methode van het `setApplicationWebRoot` object aan en geef een tekenreekswaarde door die de hoofdmap van de toepassing vertegenwoordigt.
   * Roep de `URLSpec` methode van het `setContentRootURI` object aan en geef een tekenreekswaarde door die de URI-waarde van de inhoudshoofdmap opgeeft. Zorg ervoor dat het formulierontwerp en de fragmenten zich in de URI van de inhoudsbasis bevinden. Als niet, werpt de dienst van Vormen een uitzondering. Geef een verwijzing op naar de gegevensopslagruimte `repository://`.
   * Roep de `URLSpec` methode van het `setTargetURL` object aan en geef een tekenreekswaarde door die de doel-URL-waarde opgeeft waarnaar formuliergegevens worden gepost. Als u de doel-URL in het formulierontwerp definieert, kunt u een lege tekenreeks doorgeven. U kunt ook de URL opgeven waarnaar een formulier wordt verzonden om berekeningen uit te voeren.

1. Het formulier renderen

   Roep de methode van het `FormsServiceClient` `renderPDFForm` object aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u verwijst naar een formulierontwerp dat deel uitmaakt van een Forms-toepassing, moet u controleren of u het volledige pad opgeeft, bijvoorbeeld `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Een `com.adobe.idp.Document` object dat gegevens bevat die met het formulier moeten worden samengevoegd. Geef een leeg `com.adobe.idp.Document` object door als u geen gegevens wilt samenvoegen.
   * Een `PDFFormRenderSpec` object dat uitvoeringsopties opslaat.
   * Een `URLSpec` object dat URI-waarden bevat die vereist zijn voor de Forms-service om een formulier te genereren op basis van fragmenten.
   * Een `java.util.HashMap` object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt opgeven `null` of u geen bestanden aan het formulier wilt koppelen.
   De `renderPDFForm` methode retourneert een `FormsResult` object dat een formuliergegevensstroom bevat die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Maak een `com.adobe.idp.Document` object door de `FormsResult` methode van het `getOutputContent` object aan te roepen.
   * Haal het inhoudstype van het `com.adobe.idp.Document` object op door de `getContentType` methode ervan aan te roepen.
   * Stel het inhoudstype van het `javax.servlet.http.HttpServletResponse` object in door de bijbehorende `setContentType` methode op te roepen en het inhoudstype van het `com.adobe.idp.Document` object door te geven.
   * Maak een `javax.servlet.ServletOutputStream` object dat wordt gebruikt om de gegevensstroom van het formulier naar de webbrowser van de client te schrijven door de `javax.servlet.http.HttpServletResponse` methode van het `getOutputStream` object aan te roepen.
   * Maak een `java.io.InputStream` object door de `com.adobe.idp.Document` methode van het `getInputStream` object aan te roepen.
   * Maak een bytearray die deze met de formuliergegevensstroom vult door de `InputStream` `read`methode van het object aan te roepen en de bytearray als een argument door te geven.
   * Roep de `javax.servlet.ServletOutputStream` methode van het `write` object aan om de formuliergegevensstroom naar de webbrowser van de client te verzenden. Geef de bytearray door aan de `write` methode.

**Zie ook**

[Formulieren weergeven op basis van fragmenten](#rendering-forms-based-on-fragments)

[Snel starten (SOAP-modus): Een formulier weergeven op basis van fragmenten met de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-a-form-based-on-fragments-using-the-java-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Formulieren renderen op basis van fragmenten met de webservice-API {#render-forms-based-on-fragments-using-the-web-service-api}

Een formulier genereren op basis van fragmenten met de API voor formulieren (webservice):

1. Projectbestanden opnemen

   * Maak Java-proxyklassen die de Forms service WSDL gebruiken.
   * Neem de Java-proxyklassen op in het klassepad.

1. Een Forms Client API-object maken

   Maak een `FormsService` object en stel verificatiewaarden in.

1. URI-waarden opgeven

   * Maak een `URLSpec` object dat URI-waarden opslaat met de constructor ervan.
   * Roep de `URLSpec` methode van het `setApplicationWebRoot` object aan en geef een tekenreekswaarde door die de hoofdmap van de toepassing vertegenwoordigt.
   * Roep de `URLSpec` methode van het `setContentRootURI` object aan en geef een tekenreekswaarde door die de URI-waarde van de inhoudshoofdmap opgeeft. Zorg ervoor dat het formulierontwerp zich in de URI van de inhoudsbasis bevindt. Als niet, werpt de dienst van Vormen een uitzondering. Geef een verwijzing op naar de gegevensopslagruimte `repository://`.
   * Roep de `URLSpec` methode van het `setTargetURL` object aan en geef een tekenreekswaarde door die de doel-URL-waarde opgeeft waarnaar formuliergegevens worden gepost. Als u de doel-URL in het formulierontwerp definieert, kunt u een lege tekenreeks doorgeven. U kunt ook de URL opgeven waarnaar een formulier wordt verzonden om berekeningen uit te voeren.

1. Het formulier renderen

   Roep de methode van het `FormsService` `renderPDFForm` object aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u verwijst naar een formulierontwerp dat deel uitmaakt van een Forms-toepassing, moet u controleren of u het volledige pad opgeeft, bijvoorbeeld `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Een `BLOB` object dat gegevens bevat die met het formulier moeten worden samengevoegd. Geef door als u geen gegevens wilt samenvoegen. `null`
   * Een `PDFFormRenderSpec` object dat uitvoeringsopties opslaat. De optie Gecodeerde PDF kan niet worden ingesteld als het invoerdocument een PDF-document is. Als het invoerbestand een XDP-bestand is, kunt u de optie Gecodeerde PDF instellen.
   * Een `URLSpec` object dat URI-waarden bevat die door de service Forms worden vereist.
   * Een `java.util.HashMap` object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt opgeven `null` of u geen bestanden aan het formulier wilt koppelen.
   * Een leeg `com.adobe.idp.services.holders.BLOBHolder` object dat door de methode wordt gevuld. Met deze parameter wordt het gegenereerde formulier opgeslagen.
   * Een leeg `javax.xml.rpc.holders.LongHolder` object dat door de methode wordt gevuld. In dit argument wordt het aantal pagina&#39;s in het formulier opgeslagen.
   * Een leeg `javax.xml.rpc.holders.StringHolder` object dat door de methode wordt gevuld. In dit argument wordt de waarde van de landinstelling opgeslagen.
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

[Formulieren weergeven op basis van fragmenten](#rendering-forms-based-on-fragments)

[AEM-formulieren aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
