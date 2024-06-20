---
title: Forms renderen op basis van fragmenten
description: Met de Forms-service kunt u formulieren genereren die zijn gebaseerd op fragmenten die zijn gemaakt met Designer.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: febf5350-3fc5-48c0-8bc5-198daff15936
solution: Experience Manager, Experience Manager Forms
source-git-commit: 872e2de411f51b5f0b26a2ff47cb49f01313d39f
workflow-type: tm+mt
source-wordcount: '2189'
ht-degree: 0%

---

# Forms renderen op basis van fragmenten {#rendering-forms-based-on-fragments}

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

## Forms renderen op basis van fragmenten {#rendering-forms-based-on-fragments-inner}

De Forms-service kan formulieren weergeven die zijn gebaseerd op fragmenten die u met Designer maakt. A *fragment* is een herbruikbaar onderdeel van een formulier en wordt opgeslagen als een afzonderlijk XDP-bestand dat in meerdere formulierontwerpen kan worden ingevoegd. Een fragment kan bijvoorbeeld een adresblok of juridische tekst bevatten.

Met fragmenten kunt u het maken en onderhouden van grote aantallen formulieren vereenvoudigen en versnellen. Bij het maken van een formulier voegt u een verwijzing in naar het gewenste fragment en het fragment wordt in het formulier weergegeven. De fragmentverwijzing bevat een subformulier dat naar het fysieke XDP-bestand verwijst. Zie voor informatie over het maken van formulierontwerpen op basis van fragmenten [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63)

Een fragment kan meerdere subformulieren bevatten die zijn ondergebracht in een gekozen subformulierset. De gekozen subformuliersets bepalen de weergave van subformulieren op basis van de gegevensstroom van een gegevensverbinding. U gebruikt voorwaardelijke instructies om te bepalen welk subformulier uit de set wordt weergegeven in het geleverde formulier. Elk subformulier in een set kan bijvoorbeeld informatie voor een bepaalde geografische locatie bevatten en het weergegeven subformulier kan worden bepaald op basis van de locatie van de gebruiker.

A *scriptfragment* bevat herbruikbare JavaScript-functies of waarden die afzonderlijk van een bepaald object worden opgeslagen, zoals datumparsering of aanroep van een webservice. Deze fragmenten bestaan uit één scriptobject dat als onderliggend element van variabelen in het palet Hiërarchie wordt weergegeven. Fragmenten kunnen niet worden gemaakt op basis van scripts die eigenschappen zijn van andere objecten, zoals gebeurtenisscripts zoals validate, calculate of initialize.

Hier volgen enkele voordelen van het gebruik van fragmenten:

* **Inhoud opnieuw gebruiken**: Met fragmenten kunt u inhoud hergebruiken in meerdere formulierontwerpen. Als u bepaalde inhoud van dezelfde inhoud in meerdere formulieren wilt gebruiken, is het sneller en eenvoudiger om een fragment te gebruiken dan om de inhoud te kopiëren of opnieuw te maken. Het gebruik van fragmenten zorgt er ook voor dat de vaak gebruikte onderdelen van een formulierontwerp dezelfde inhoud en weergave hebben in alle formulieren die ernaar verwijzen.
* **Algemene updates**: Met fragmenten kunt u in één bestand globale wijzigingen in meerdere formulieren slechts eenmaal doorvoeren. U kunt de inhoud, scriptobjecten, gegevensbindingen, lay-out of stijlen in een fragment wijzigen en alle XDP-formulieren die naar het fragment verwijzen, weerspiegelen de wijzigingen.
* Een gemeenschappelijk element in vele formulieren kan bijvoorbeeld een adresblok zijn dat een vervolgkeuzelijstobject voor het land bevat. Als u de waarden voor het vervolgkeuzelijstobject moet bijwerken, moet u vele formulieren openen om de wijzigingen aan te brengen. Als u het adresblok in een fragment opneemt, hoeft u slechts één fragmentbestand te openen om de wijzigingen aan te brengen.
* Als u een fragment in een PDF-formulier wilt bijwerken, moet u het formulier opnieuw opslaan in Designer.
* **Gedeeld formulier maken**: U kunt fragmenten gebruiken om de aanmaak van formulieren te delen met verschillende bronnen. Formulierontwikkelaars met ervaring in het schrijven van scripts of andere geavanceerde functies van Designer kunnen fragmenten ontwikkelen en delen die gebruikmaken van scripts en dynamische eigenschappen. Formulierontwerpers kunnen deze fragmenten gebruiken om formulierontwerpen op te maken en ervoor te zorgen dat alle onderdelen van een formulier een consistente weergave en functionaliteit hebben in meerdere formulieren die door meerdere personen zijn ontworpen.

### Een formulierontwerp samenstellen dat is samengesteld met fragmenten {#assembling-a-form-design-assembled-using-fragments}

U kunt een formulierontwerp samenstellen om aan de Forms-service door te geven op basis van meerdere fragmenten. Als u meerdere fragmenten wilt samenstellen, gebruikt u de Assembler-service. Als u een voorbeeld wilt zien van het gebruik van de Assemble-service voor het maken van een formulierontwerp dat wordt gebruikt door een andere Forms-service (de Output-service), raadpleegt u [PDF-documenten maken met behulp van fragmenten](/help/forms/developing/creating-document-output-streams.md#creating-pdf-documents-using-fragments). In plaats van de service Uitvoer te gebruiken, kunt u dezelfde workflow uitvoeren met de Forms-service.

Wanneer u de Assembler-service gebruikt, geeft u een formulierontwerp door dat is samengesteld met fragmenten. Het formulierontwerp dat is gemaakt, verwijst niet naar andere fragmenten. In dit onderwerp wordt daarentegen het doorgeven van een formulierontwerp besproken dat naar andere fragmenten verwijst naar de Forms-service. Het formulierontwerp is echter niet samengesteld door Assembler. Het is gemaakt in Designer.

>[!NOTE]
>
>Voor meer informatie over de Forms-service raadpleegt u [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Voor informatie over het maken van een webtoepassing die formulieren weergeeft op basis van fragmenten raadpleegt u [Webtoepassingen maken die Forms renderen](/help/forms/developing/creating-web-applications-renders-forms.md).

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

Voordat u programmatisch een client-API-bewerking voor Forms-services kunt uitvoeren, moet u een Forms-serviceclient maken.

**URI-waarden opgeven**

Als u een formulier wilt genereren op basis van fragmenten, moet u ervoor zorgen dat de Forms-service zowel het formulier als de fragmenten (de XDP-bestanden) kan vinden waarnaar het formulierontwerp verwijst. Stel bijvoorbeeld dat het formulier de naam PO.xdp heeft en dat dit formulier twee fragmenten gebruikt: FooterUS.xdp en FooterCanada.xdp. In dit geval moet de Forms-service alle drie XDP-bestanden kunnen vinden.

U kunt een formulier en de bijbehorende fragmenten ordenen door het formulier op één locatie en de fragmenten op een andere locatie te plaatsen, of u kunt alle XDP-bestanden op dezelfde locatie plaatsen. In deze sectie wordt ervan uitgegaan dat alle XDP-bestanden zich in de AEM Forms-opslagplaats bevinden. Zie voor informatie over het plaatsen van XDP-bestanden in de AEM Forms-opslagplaats [Bronnen schrijven](/help/forms/developing/aem-forms-repository.md#writing-resources).

Bij het genereren van een formulier op basis van fragmenten moet u alleen naar het formulier zelf verwijzen en niet naar de fragmenten. U moet bijvoorbeeld naar PO.xdp verwijzen en niet naar FooterUS.xdp of FooterCanada.xdp. Plaats de fragmenten op een locatie waar de Forms-service ze kan vinden.

**Het formulier renderen**

Een formulier dat is gebaseerd op fragmenten, kan op dezelfde manier worden gegenereerd als niet-gefragmenteerde formulieren. U kunt het formulier dus weergeven als PDF-, HTML- of formulierhulplijnen (afgekeurd). In het voorbeeld in deze sectie wordt een formulier op basis van fragmenten weergegeven als een interactief PDF-formulier. (Zie [Interactieve PDF forms renderen](/help/forms/developing/rendering-interactive-pdf-forms.md).)

**De formuliergegevensstroom naar de webbrowser van de client schrijven**

Wanneer de Forms-service een formulier genereert, wordt een formuliergegevensstroom geretourneerd die u naar de webbrowser van de client moet schrijven. Wanneer het formulier naar de webbrowser van de client wordt geschreven, is het zichtbaar voor de gebruiker.

**Zie ook**

[Formulieren weergeven op basis van fragmenten met de Java API](#render-forms-based-on-fragments-using-the-java-api)

[Formulieren renderen op basis van fragmenten met de webservice-API](#render-forms-based-on-fragments-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Forms Service API Quick Start](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Interactieve PDF forms renderen](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Webtoepassingen maken die Forms renderen](/help/forms/developing/creating-web-applications-renders-forms.md)

### Formulieren weergeven op basis van fragmenten met de Java API {#render-forms-based-on-fragments-using-the-java-api}

Een formulier renderen op basis van fragmenten met de Forms API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-forms-client.jar, op in het klassenpad van uw Java-project.

1. Een Forms Client API-object maken

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `FormsServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. URI-waarden opgeven

   * Een `URLSpec` object dat URI-waarden opslaat met de constructor ervan.
   * De `URLSpec` object `setApplicationWebRoot` en geeft een tekenreekswaarde door die de hoofdmap van de toepassing vertegenwoordigt.
   * De `URLSpec` object `setContentRootURI` methode en geef een tekenreekswaarde door die de URI-waarde van de inhoudsbasis opgeeft. Zorg ervoor dat het formulierontwerp en de fragmenten zich in de URI van de basisinhoud bevinden. Als niet, werpt de dienst van Forms een uitzondering. Als u naar de gegevensopslagruimte wilt verwijzen, geeft u `repository://`.
   * De `URLSpec` object `setTargetURL` en geeft een tekenreekswaarde door die de doel-URL-waarde opgeeft waarnaar formuliergegevens worden gepost. Als u de doel-URL in het formulierontwerp definieert, kunt u een lege tekenreeks doorgeven. U kunt ook de URL opgeven waarnaar een formulier wordt verzonden om berekeningen uit te voeren.

1. Het formulier renderen

   De `FormsServiceClient` object `renderPDFForm` en geeft de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u naar een formulierontwerp verwijst dat deel uitmaakt van een Forms-toepassing, moet u het volledige pad opgeven, zoals `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `com.adobe.idp.Document` object dat gegevens bevat die met het formulier moeten worden samengevoegd. Als u geen gegevens wilt samenvoegen, geeft u een lege waarde door `com.adobe.idp.Document` object.
   * A `PDFFormRenderSpec` -object dat uitvoeringsopties opslaat.
   * A `URLSpec` object dat URI-waarden bevat die door de Forms-service worden vereist om een formulier te genereren op basis van fragmenten.
   * A `java.util.HashMap` object waarin bestandsbijlagen zijn opgeslagen. Dit is een optionele parameter en u kunt `null` als u geen bestanden aan het formulier wilt koppelen.

   De `renderPDFForm` methode retourneert een `FormsResult` object dat een formuliergegevensstroom bevat die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Een `com.adobe.idp.Document` door het object aan te roepen `FormsResult` object &#39;s `getOutputContent` methode.
   * Hiermee wordt het inhoudstype van het dialoogvenster `com.adobe.idp.Document` object aanroepen `getContentType` methode.
   * Stel de `javax.servlet.http.HttpServletResponse` inhoudstype van object door het aan te roepen `setContentType` en geeft u het inhoudstype van de `com.adobe.idp.Document` object.
   * Een `javax.servlet.ServletOutputStream` object dat wordt gebruikt om de formuliergegevensstroom naar de webbrowser van de client te schrijven door het aanroepen van de `javax.servlet.http.HttpServletResponse` object `getOutputStream` methode.
   * Een `java.io.InputStream` door het object aan te roepen `com.adobe.idp.Document` object `getInputStream` methode.
   * Maak een bytearray die deze met de formuliergegevensstroom vult door de `InputStream` object `read`en de bytearray doorgeven als een argument.
   * De `javax.servlet.ServletOutputStream` object `write` methode om de formuliergegevensstroom naar de webbrowser van de client te verzenden. Geef de bytearray door aan de `write` methode.

**Zie ook**

[Forms renderen op basis van fragmenten](#rendering-forms-based-on-fragments)

[Snel starten (SOAP modus): Een formulier genereren op basis van fragmenten met de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-a-form-based-on-fragments-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Formulieren renderen op basis van fragmenten met de webservice-API {#render-forms-based-on-fragments-using-the-web-service-api}

Een formulier weergeven op basis van fragmenten met de Forms API (webservice):

1. Projectbestanden opnemen

   * Maak Java-proxyklassen die gebruikmaken van de Forms-service WSDL.
   * Neem de Java-proxyklassen op in het klassepad.

1. Een Forms Client API-object maken

   Een `FormsService` -object en stel verificatiewaarden in.

1. URI-waarden opgeven

   * Een `URLSpec` object dat URI-waarden opslaat met de constructor ervan.
   * De `URLSpec` object `setApplicationWebRoot` en geeft een tekenreekswaarde door die de hoofdmap van de toepassing vertegenwoordigt.
   * De `URLSpec` object `setContentRootURI` methode en geef een tekenreekswaarde door die de URI-waarde van de inhoudsbasis opgeeft. Zorg ervoor dat het formulierontwerp zich in de URI van de inhoudsbasis bevindt. Als niet, werpt de dienst van Forms een uitzondering. Als u naar de gegevensopslagruimte wilt verwijzen, geeft u `repository://`.
   * De `URLSpec` object `setTargetURL` en geeft een tekenreekswaarde door die de doel-URL-waarde opgeeft waarnaar formuliergegevens worden gepost. Als u de doel-URL in het formulierontwerp definieert, kunt u een lege tekenreeks doorgeven. U kunt ook de URL opgeven waarnaar een formulier wordt verzonden om berekeningen uit te voeren.

1. Het formulier renderen

   De `FormsService` object `renderPDFForm` en geeft de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u naar een formulierontwerp verwijst dat deel uitmaakt van een Forms-toepassing, moet u het volledige pad opgeven, zoals `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `BLOB` object dat gegevens bevat die met het formulier moeten worden samengevoegd. Als u geen gegevens wilt samenvoegen, geeft u `null`.
   * A `PDFFormRenderSpec` -object dat uitvoeringsopties opslaat. De optie Gelabelde PDF kan niet worden ingesteld als het invoerdocument een PDF-document is. Als het invoerbestand een XDP-bestand is, kunt u de optie voor gecodeerde PDF instellen.
   * A `URLSpec` object dat URI-waarden bevat die door de Forms-service worden vereist.
   * A `java.util.HashMap` object waarin bestandsbijlagen zijn opgeslagen. Dit is een optionele parameter en u kunt `null` als u geen bestanden aan het formulier wilt koppelen.
   * Een leeg `com.adobe.idp.services.holders.BLOBHolder` object dat door de methode wordt gevuld. Deze parameter wordt gebruikt om het weergegeven formulier op te slaan.
   * Een leeg `javax.xml.rpc.holders.LongHolder` object dat door de methode wordt gevuld. In dit argument wordt het aantal pagina&#39;s in het formulier opgeslagen.
   * Een leeg `javax.xml.rpc.holders.StringHolder` object dat door de methode wordt gevuld. In dit argument wordt de waarde van de landinstelling opgeslagen.
   * Een leeg `com.adobe.idp.services.holders.FormsResultHolder` -object dat de resultaten van deze bewerking zal bevatten.

   De `renderPDFForm` wordt de `com.adobe.idp.services.holders.FormsResultHolder` object dat wordt doorgegeven als de laatste argumentwaarde met een formuliergegevensstroom die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Een `FormResult` object door de waarde van het object op te halen `com.adobe.idp.services.holders.FormsResultHolder` object `value` lid.
   * Een `BLOB` object dat formuliergegevens bevat door het `FormsResult` object `getOutputContent` methode.
   * Hiermee wordt het inhoudstype van het dialoogvenster `BLOB` object aanroepen `getContentType` methode.
   * Stel de `javax.servlet.http.HttpServletResponse` inhoudstype van object door het aan te roepen `setContentType` en geeft u het inhoudstype van de `BLOB` object.
   * Een `javax.servlet.ServletOutputStream` object dat wordt gebruikt om de formuliergegevensstroom naar de webbrowser van de client te schrijven door het aanroepen van de `javax.servlet.http.HttpServletResponse` object `getOutputStream` methode.
   * Maak een bytearray en vul deze door het `BLOB` object `getBinaryData` methode. Deze taak wijst de inhoud van toe `FormsResult` object naar de bytearray.
   * De `javax.servlet.http.HttpServletResponse` object `write` methode om de formuliergegevensstroom naar de webbrowser van de client te verzenden. Geef de bytearray door aan de `write` methode.

**Zie ook**

[Forms renderen op basis van fragmenten](#rendering-forms-based-on-fragments)

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
