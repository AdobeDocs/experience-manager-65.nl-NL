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
feature: Adaptive Forms,Document Services,APIs & Integrations
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '2189'
ht-degree: 0%

---

# Forms renderen op basis van fragmenten {#rendering-forms-based-on-fragments}

**de Steekproeven en de voorbeelden in dit document zijn slechts voor AEM Forms op milieu JEE.**

## Forms renderen op basis van fragmenten {#rendering-forms-based-on-fragments-inner}

De Forms-service kan formulieren weergeven die zijn gebaseerd op fragmenten die u met Designer maakt. A *fragment* is een herbruikbaar deel van een vorm en opgeslagen als afzonderlijk XDP dossier dat in veelvoudige vormontwerpen kan worden opgenomen. Een fragment kan bijvoorbeeld een adresblok of juridische tekst bevatten.

Met fragmenten kunt u het maken en onderhouden van grote aantallen formulieren vereenvoudigen en versnellen. Bij het maken van een formulier voegt u een verwijzing in naar het gewenste fragment en het fragment wordt in het formulier weergegeven. De fragmentverwijzing bevat een subformulier dat naar het fysieke XDP-bestand verwijst. Voor informatie over het creëren van vormontwerpen die op fragmenten worden gebaseerd, zie [&#x200B; Forms Designer &#x200B;](https://www.adobe.com/go/learn_aemforms_designer_63)

Een fragment kan meerdere subformulieren bevatten die zijn ondergebracht in een gekozen subformulierset. De gekozen subformuliersets bepalen de weergave van subformulieren op basis van de gegevensstroom van een gegevensverbinding. U gebruikt voorwaardelijke instructies om te bepalen welk subformulier uit de set wordt weergegeven in het geleverde formulier. Elk subformulier in een set kan bijvoorbeeld informatie voor een bepaalde geografische locatie bevatten en het weergegeven subformulier kan worden bepaald op basis van de locatie van de gebruiker.

A *manuscriptfragment* bevat herbruikbare functies of waarden van JavaScript die gescheiden van om het even welk bepaald voorwerp, zoals een datumparser of een aanroeping van de Webdienst worden opgeslagen. Deze fragmenten bestaan uit één scriptobject dat als onderliggend element van variabelen in het palet Hiërarchie wordt weergegeven. Fragmenten kunnen niet worden gemaakt op basis van scripts die eigenschappen zijn van andere objecten, zoals gebeurtenisscripts zoals validate, calculate of initialize.

Hier volgen enkele voordelen van het gebruik van fragmenten:

* **Inhoud hergebruikt**: U kunt fragmenten gebruiken om inhoud in veelvoudige vormontwerpen opnieuw te gebruiken. Als u bepaalde inhoud van dezelfde inhoud in meerdere formulieren wilt gebruiken, is het sneller en eenvoudiger om een fragment te gebruiken dan om de inhoud te kopiëren of opnieuw te maken. Het gebruik van fragmenten zorgt er ook voor dat de vaak gebruikte onderdelen van een formulierontwerp dezelfde inhoud en weergave hebben in alle formulieren die ernaar verwijzen.
* **Globale updates**: U kunt fragmenten gebruiken om globale veranderingen in veelvoudige vormen slechts eenmaal, in één dossier aan te brengen. U kunt de inhoud, scriptobjecten, gegevensbindingen, lay-out of stijlen in een fragment wijzigen en alle XDP-formulieren die naar het fragment verwijzen, weerspiegelen de wijzigingen.
* Een gemeenschappelijk element in vele formulieren kan bijvoorbeeld een adresblok zijn dat een vervolgkeuzelijstobject voor het land bevat. Als u de waarden voor het vervolgkeuzelijstobject moet bijwerken, moet u vele formulieren openen om de wijzigingen aan te brengen. Als u het adresblok in een fragment opneemt, hoeft u slechts één fragmentbestand te openen om de wijzigingen aan te brengen.
* Als u een fragment in een PDF-formulier wilt bijwerken, moet u het formulier opnieuw opslaan in Designer.
* **Gedeelde vormverwezenlijking**: U kunt fragmenten gebruiken om de verwezenlijking van vormen onder verscheidene middelen te delen. Formulierontwikkelaars met ervaring in het schrijven van scripts of andere geavanceerde functies van Designer kunnen fragmenten ontwikkelen en delen die gebruikmaken van scripts en dynamische eigenschappen. Formulierontwerpers kunnen deze fragmenten gebruiken om formulierontwerpen op te maken en ervoor te zorgen dat alle onderdelen van een formulier een consistente weergave en functionaliteit hebben in meerdere formulieren die door meerdere personen zijn ontworpen.

### Een formulierontwerp samenstellen dat is samengesteld met fragmenten {#assembling-a-form-design-assembled-using-fragments}

U kunt een formulierontwerp samenstellen om aan de Forms-service door te geven op basis van meerdere fragmenten. Als u meerdere fragmenten wilt samenstellen, gebruikt u de Assembler-service. Om een voorbeeld te zien van het gebruiken van de dienst van de Assemblage om een vormontwerp tot stand te brengen dat door een andere diensten van Forms (de dienst van de Output) wordt gebruikt, zie [&#x200B; Creërend de Documenten van de PDF gebruikend Fragments &#x200B;](/help/forms/developing/creating-document-output-streams.md#creating-pdf-documents-using-fragments). In plaats van de service Uitvoer te gebruiken, kunt u dezelfde workflow uitvoeren met de Forms-service.

Wanneer u de Assembler-service gebruikt, geeft u een formulierontwerp door dat is samengesteld met fragmenten. Het formulierontwerp dat is gemaakt, verwijst niet naar andere fragmenten. In dit onderwerp wordt daarentegen het doorgeven van een formulierontwerp besproken dat naar andere fragmenten verwijst naar de Forms-service. Het formulierontwerp is echter niet samengesteld door Assembler. Het is gemaakt in Designer.

>[!NOTE]
>
>Voor meer informatie over de dienst van Forms, zie [&#x200B; Verwijzing van de Diensten voor AEM Forms &#x200B;](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Voor informatie over het creëren van een web-based toepassing die vormen teruggeeft die op fragmenten worden gebaseerd, zie [&#x200B; Creërend de Toepassingen van het Web die Forms &#x200B;](/help/forms/developing/creating-web-applications-renders-forms.md) teruggeven.

### Overzicht van de stappen {#summary-of-steps}

Als u een formulier wilt genereren op basis van fragmenten, voert u de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak een Forms Client API-object.
1. Geef URI-waarden op.
1. Het formulier weergeven.
1. Schrijf de gegevensstroom van het formulier naar de webbrowser van de client.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**creeer een voorwerp van Forms Cliënt API**

Voordat u programmatisch een client-API-bewerking voor Forms-services kunt uitvoeren, moet u een Forms-serviceclient maken.

**specificeer de waarden van URI**

Als u een formulier wilt genereren op basis van fragmenten, moet u ervoor zorgen dat de Forms-service zowel het formulier als de fragmenten (de XDP-bestanden) kan vinden waarnaar het formulierontwerp verwijst. Stel bijvoorbeeld dat het formulier de naam PO.xdp heeft en dat dit formulier twee fragmenten gebruikt: FooterUS.xdp en FooterCanada.xdp. In dit geval moet de Forms-service alle drie XDP-bestanden kunnen vinden.

U kunt een formulier en de bijbehorende fragmenten ordenen door het formulier op één locatie en de fragmenten op een andere locatie te plaatsen, of u kunt alle XDP-bestanden op dezelfde locatie plaatsen. In deze sectie wordt ervan uitgegaan dat alle XDP-bestanden zich in de AEM Forms-opslagplaats bevinden. Voor informatie over het plaatsen van XDP dossiers in de bewaarplaats van AEM Forms, zie [&#x200B; het Schrijven Middelen &#x200B;](/help/forms/developing/aem-forms-repository.md#writing-resources).

Bij het genereren van een formulier op basis van fragmenten moet u alleen naar het formulier zelf verwijzen en niet naar de fragmenten. U moet bijvoorbeeld naar PO.xdp verwijzen en niet naar FooterUS.xdp of FooterCanada.xdp. Plaats de fragmenten op een locatie waar de Forms-service ze kan vinden.

**geef de vorm** terug

Een formulier dat is gebaseerd op fragmenten, kan op dezelfde manier worden gegenereerd als niet-gefragmenteerde formulieren. U kunt het formulier dus weergeven als PDF-, HTML- of formulierhulplijnen (afgekeurd). In het voorbeeld in deze sectie wordt een formulier op basis van fragmenten weergegeven als een interactief PDF-formulier. (Zie [&#x200B; teruggevend Interactieve PDF forms &#x200B;](/help/forms/developing/rendering-interactive-pdf-forms.md).)

**schrijf de stroom van vormgegevens aan cliëntWeb browser**

Wanneer de Forms-service een formulier genereert, wordt een formuliergegevensstroom geretourneerd die u naar de webbrowser van de client moet schrijven. Wanneer het formulier naar de webbrowser van de client wordt geschreven, is het zichtbaar voor de gebruiker.

**zie ook**

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

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `FormsServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. URI-waarden opgeven

   * Maak een `URLSpec` -object dat URI-waarden opslaat met behulp van de constructor.
   * Roep de methode `setApplicationWebRoot` van het object `URLSpec` aan en geef een tekenreekswaarde door die de hoofdmap van de toepassing vertegenwoordigt.
   * Roep de methode `setContentRootURI` van het `URLSpec` -object aan en geef een tekenreekswaarde door die de URI-waarde van de inhoudsbasis opgeeft. Zorg ervoor dat het formulierontwerp en de fragmenten zich in de URI van de basisinhoud bevinden. Als niet, werpt de dienst van Forms een uitzondering. Geef `repository://` op om naar de gegevensopslagruimte te verwijzen.
   * Roep de methode `setTargetURL` van het object `URLSpec` aan en geef een tekenreekswaarde door die de doel-URL-waarde opgeeft waarnaar de formuliergegevens worden gepost. Als u de doel-URL in het formulierontwerp definieert, kunt u een lege tekenreeks doorgeven. U kunt ook de URL opgeven waarnaar een formulier wordt verzonden om berekeningen uit te voeren.

1. Het formulier renderen

   Roep de methode `renderPDFForm` van het object `FormsServiceClient` aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u verwijst naar een formulierontwerp dat deel uitmaakt van een Forms-toepassing, moet u het volledige pad opgeven, bijvoorbeeld `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp` .
   * Een `com.adobe.idp.Document` -object dat gegevens bevat die met het formulier moeten worden samengevoegd. Wanneer u geen gegevens wilt samenvoegen, geeft u een leeg `com.adobe.idp.Document` -object door.
   * Een `PDFFormRenderSpec` -object dat uitvoeringsopties opslaat.
   * Een `URLSpec` -object dat URI-waarden bevat die door de Forms-service worden vereist om een formulier te genereren op basis van fragmenten.
   * Een `java.util.HashMap` -object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt `null` opgeven als u geen bestanden aan het formulier wilt koppelen.

   De methode `renderPDFForm` retourneert een `FormsResult` -object dat een formuliergegevensstroom bevat die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Maak een `com.adobe.idp.Document` -object door de methode `FormsResult` object &#39;s `getOutputContent` aan te roepen.
   * Haal het inhoudstype van het object `com.adobe.idp.Document` op door de methode `getContentType` ervan aan te roepen.
   * Stel het inhoudstype van het `javax.servlet.http.HttpServletResponse` -object in door de methode `setContentType` ervan aan te roepen en het inhoudstype van het `com.adobe.idp.Document` -object door te geven.
   * Maak een `javax.servlet.ServletOutputStream` -object dat wordt gebruikt om de formuliergegevensstroom naar de webbrowser van de client te schrijven door de methode `javax.servlet.http.HttpServletResponse` object `getOutputStream` aan te roepen.
   * Maak een `java.io.InputStream` -object door de methode `com.adobe.idp.Document` object `getInputStream` aan te roepen.
   * Creeer een byteserie bevolkt het met de stroom van vormgegevens door de `read` methode van objecten `InputStream` aan te roepen en de byteserie als argument over te gaan.
   * Roep de methode `write` van het object `javax.servlet.ServletOutputStream` aan om de gegevensstroom van het formulier naar de webbrowser van de client te verzenden. Geef de bytearray door aan de methode `write` .

**zie ook**

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

   Maak een `FormsService` -object en stel de verificatiewaarden in.

1. URI-waarden opgeven

   * Maak een `URLSpec` -object waarin URI-waarden worden opgeslagen met behulp van de constructor.
   * Roep de methode `setApplicationWebRoot` van het object `URLSpec` aan en geef een tekenreekswaarde door die de hoofdmap van de toepassing vertegenwoordigt.
   * Roep de methode `setContentRootURI` van het `URLSpec` -object aan en geef een tekenreekswaarde door die de URI-waarde van de inhoudsbasis opgeeft. Zorg ervoor dat het formulierontwerp zich in de URI van de inhoudsbasis bevindt. Als niet, werpt de dienst van Forms een uitzondering. Geef `repository://` op om naar de gegevensopslagruimte te verwijzen.
   * Roep de methode `setTargetURL` van het object `URLSpec` aan en geef een tekenreekswaarde door die de doel-URL-waarde opgeeft waarnaar de formuliergegevens worden gepost. Als u de doel-URL in het formulierontwerp definieert, kunt u een lege tekenreeks doorgeven. U kunt ook de URL opgeven waarnaar een formulier wordt verzonden om berekeningen uit te voeren.

1. Het formulier renderen

   Roep de methode `renderPDFForm` van het object `FormsService` aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u verwijst naar een formulierontwerp dat deel uitmaakt van een Forms-toepassing, moet u het volledige pad opgeven, bijvoorbeeld `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp` .
   * Een `BLOB` -object dat gegevens bevat die met het formulier moeten worden samengevoegd. Geef `null` door als u geen gegevens wilt samenvoegen.
   * Een `PDFFormRenderSpec` -object dat uitvoeringsopties opslaat. De optie Gelabelde PDF kan niet worden ingesteld als het invoerdocument een PDF-document is. Als het invoerbestand een XDP-bestand is, kunt u de optie voor gecodeerde PDF instellen.
   * Een `URLSpec` -object dat URI-waarden bevat die door de Forms-service worden vereist.
   * Een `java.util.HashMap` -object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt `null` opgeven als u geen bestanden aan het formulier wilt koppelen.
   * Een leeg `com.adobe.idp.services.holders.BLOBHolder` -object dat door de methode wordt gevuld. Deze parameter wordt gebruikt om het weergegeven formulier op te slaan.
   * Een leeg `javax.xml.rpc.holders.LongHolder` -object dat door de methode wordt gevuld. In dit argument wordt het aantal pagina&#39;s in het formulier opgeslagen.
   * Een leeg `javax.xml.rpc.holders.StringHolder` -object dat door de methode wordt gevuld. In dit argument wordt de waarde van de landinstelling opgeslagen.
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

[Forms renderen op basis van fragmenten](#rendering-forms-based-on-fragments)

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
