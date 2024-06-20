---
title: Forms renderen als HTML
description: Gebruik de Forms-service om formulieren als HTML te genereren in reactie op een HTTP-aanvraag van een webbrowser. U kunt de Java&trade-, API- en webservice-API gebruiken om formulieren te genereren als HTML.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: e6887e45-a472-41d4-9620-c56fd5b72b4c
solution: Experience Manager, Experience Manager Forms
source-git-commit: 872e2de411f51b5f0b26a2ff47cb49f01313d39f
workflow-type: tm+mt
source-wordcount: '4099'
ht-degree: 0%

---

# Forms renderen als HTML {#rendering-forms-as-html}

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

De Forms-service geeft formulieren als HTML weer in reactie op een HTTP-aanvraag van een webbrowser. Een voordeel van het weergeven van een formulier als HTML is dat de computer waarop de webbrowser van de client zich bevindt geen Adobe Reader, Acrobat of Flash Player vereist (voor formulierhulplijnen (afgekeurd)).

Als u een formulier wilt weergeven als HTML, moet het formulierontwerp worden opgeslagen als een XDP-bestand. Een formulierontwerp dat is opgeslagen als een PDF-bestand, kan niet worden weergegeven als HTML. Houd rekening met de volgende criteria wanneer u een formulierontwerp ontwikkelt in Designer dat wordt weergegeven als HTML:

* Gebruik niet de randeigenschappen van een object om lijnen, vakken of rasters op het formulier te tekenen. In sommige browsers worden randen mogelijk niet precies zo weergegeven als in een voorvertoning. Objecten kunnen gelaagd worden weergegeven of kunnen andere objecten van hun verwachte positie wegduwen.
* U kunt lijnen, rechthoeken en cirkels gebruiken om de achtergrond te definiëren.
* Teken tekst iets groter dan nodig lijkt om ruimte te maken voor de tekst. In sommige webbrowsers wordt de tekst niet leesbaar weergegeven.

>[!NOTE]
>
>Als u een formulier met TIFF-afbeeldingen weergeeft met de opdracht `FormServiceClient` object `(Deprecated) renderHTMLForm` en `renderHTMLForm2` de TIFF-afbeeldingen niet zichtbaar zijn in het weergegeven HTML-formulier dat wordt weergegeven in Internet Explorer- of Mozilla Firefox-browsers. Deze browsers bieden geen native ondersteuning voor TIFF-afbeeldingen.

## HTML pagina&#39;s {#html-pages}

Wanneer een formulierontwerp wordt weergegeven als een HTML-formulier, wordt elk subformulier op het tweede niveau weergegeven als een HTML-pagina (deelvenster). U kunt de hiërarchie van een subformulier weergeven in Designer. Onderliggende subformulieren die tot het basissubformulier behoren (de standaardnaam van een basissubformulier is form1), zijn de deelvenstersubformulieren. In het volgende voorbeeld worden de subformulieren van een formulierontwerp weergegeven.

```java
     form1
         Master Pages
         PanelSubform1
             NestedDynamicSubform
                 TextEdit1
         PanelSubform2
             TextEdit1
         PanelSubform3
             TextEdit1
         PanelSubform4
             TextEdit1
```

Wanneer formulierontwerpen worden weergegeven als HTML-formulieren, blijven de deelvensters beperkt tot een bepaald paginaformaat. Als u dynamische subformulieren hebt, moeten deze in het deelvenstersubformulier worden genest. Dynamische subformulieren kunnen worden uitgebreid tot een oneindig aantal HTML-pagina&#39;s.

Wanneer een formulier wordt weergegeven als een HTML-formulier, hebben paginaformaten (vereist voor paginering van formulieren die worden weergegeven als PDF) geen betekenis. Omdat een formulier met een stroombare indeling kan worden uitgebreid tot een oneindig aantal HTML-pagina&#39;s, is het belangrijk dat u geen voetteksten op de basispagina plaatst. Een voettekst onder het inhoudsgebied op een basispagina kan HTML-inhoud overschrijven die voorbij een paginagrens loopt.

U moet expliciet van deelvenster naar deelvenster gaan met de opdracht `xfa.host.pageUp` en `xfa.host.pageDown` methoden. U wijzigt pagina&#39;s door een formulier naar de Forms-service te verzenden en het formulier door de Forms-service terug te sturen naar het clientapparaat, meestal een webbrowser.

>[!NOTE]
>
>Het proces waarbij een formulier naar de Forms-service wordt verzonden en het formulier vervolgens door de Forms-service naar het clientapparaat wordt teruggestuurd, wordt ook wel &#39;round tripping data&#39; naar de server genoemd.

>[!NOTE]
>
>Als u de weergave van de knop HTML Digital Signature op een HTML-formulier wilt aanpassen, moet u de volgende eigenschappen wijzigen in het bestand fscdigsig.css (in het bestand adobe-forms-ds.ear > adobe-forms-ds.war):

**`.fsc-ds-ssb`**: Dit stijlblad is van toepassing als er een leeg tekenveld is.

**`.fsc-ds-ssv`**: Dit stijlblad is van toepassing als er een geldig handtekeningveld is.

**`.fsc-ds-ssc`**: Dit stijlblad is van toepassing als er een geldig handtekeningveld is maar er gegevens zijn gewijzigd.

**`.fsc-ds-ssi`**: Dit stijlblad is van toepassing als er een ongeldig handtekeningveld is.

**`.fsc-ds-popup-bg`**: Deze stijlbladeigenschap wordt niet gebruikt.

**.`fsc-ds-popup-btn`**: Deze stijlbladeigenschap wordt niet gebruikt.

## Scripts uitvoeren {#running-scripts}

Een auteur van een formulier geeft aan of een script op de server of de client wordt uitgevoerd. De Forms-service maakt een gedistribueerde, gebeurtenisverwerkingsomgeving voor de uitvoering van formulierintelligentie die tussen de client en de server kan worden gedistribueerd met behulp van de `runAt` kenmerk. Voor informatie over dit kenmerk of het maken van scripts in formulierontwerpen raadpleegt u [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63)

De Forms-service kan scripts uitvoeren terwijl het formulier wordt gegenereerd. Hierdoor kunt u een formulier vooraf invullen met gegevens door verbinding te maken met een database of met webservices die mogelijk niet beschikbaar zijn op de client. U kunt ook knoppen instellen `Click` gebeurtenis die op de server moet worden uitgevoerd zodat de client gegevens voor retournering naar de server doorvoert. Hierdoor kan de client scripts uitvoeren waarvoor mogelijk serverbronnen nodig zijn, zoals een ondernemingsdatabase, terwijl een gebruiker communiceert met een formulier. Voor HTML-formulieren kunnen formele scripts alleen op de server worden uitgevoerd. Als gevolg hiervan moet u deze scripts markeren om te worden uitgevoerd `server` of `both`.

U kunt formulieren ontwerpen die tussen pagina&#39;s (deelvensters) bewegen door `xfa.host.pageUp` en `xfa.host.pageDown` methoden. Dit script wordt in de knop geplaatst `Click` en de `runAt` kenmerk is ingesteld op `Both`. De reden die u kiest `Both` is zo dat Adobe Reader of Acrobat (voor formulieren die worden weergegeven als PDF) pagina&#39;s kan wijzigen zonder naar de server te gaan. HTML-formulieren kunnen pagina&#39;s wijzigen door gegevens naar de server af te snijden. Een formulier wordt dus naar de Forms-service verzonden en een formulier wordt als HTML weergegeven met de nieuwe pagina.

U wordt aangeraden scriptvariabelen en formuliervelden niet dezelfde namen te geven, zoals item. Sommige webbrowsers, zoals Internet Explorer, initialiseren een variabele met dezelfde naam als een formulierveld, waardoor een scriptfout optreedt. Het is een goede gewoonte om formuliervelden en scriptvariabelen verschillende namen te geven.

Bij het weergeven van HTML-formulieren die zowel paginanavigatiefuncties als formulierscripts bevatten (bijvoorbeeld, neem aan dat een script veldgegevens ophaalt uit een database telkens wanneer het formulier wordt gegenereerd), moet u ervoor zorgen dat het formulierscript de gebeurtenis form:calculate heeft in plaats van de gebeurtenis form:readyevent.

Formulierscripts in de gebeurtenis form:ready worden slechts eenmaal uitgevoerd tijdens de eerste weergave van het formulier en worden niet uitgevoerd voor volgende opvragingen van pagina&#39;s. De gebeurtenis form:calculate wordt daarentegen uitgevoerd voor elke paginanavigatie waarin het formulier wordt gegenereerd.

>[!NOTE]
>
Op een formulier met meerdere pagina&#39;s blijven wijzigingen die door JavaScript in een pagina zijn aangebracht, niet behouden als u naar een andere pagina gaat.

U kunt aangepaste scripts aanroepen voordat u een formulier verzendt. Deze functie werkt op alle beschikbare browsers. Deze kan echter alleen worden gebruikt wanneer gebruikers het HTML-formulier met de bijbehorende `Output Type` eigenschap ingesteld op `Form Body`. Het werkt niet als de `Output Type` is `Full HTML`. Zie Formulieren configureren in de Help voor het beheer voor stappen om deze functie te configureren.

Definieer eerst een callback-functie die wordt aangeroepen voordat het formulier wordt verzonden, waarbij de naam van de functie `_user_onsubmit`. Er wordt aangenomen dat de functie geen uitzondering genereert of dat de uitzondering wordt genegeerd als dit het geval is. Het wordt aangeraden de JavaScript-functie in de kopsectie van de HTML te plaatsen, maar u kunt deze functie overal vóór het einde van de scripttags declareren die ook scripttags bevatten `xfasubset.js`.

Wanneer de formserver een XDP teruggeeft die een drop-down lijst bevat, naast het creëren van de drop-down lijst, leidt het ook tot twee verborgen tekstgebieden. In deze tekstvelden worden de gegevens van de vervolgkeuzelijst opgeslagen (in de ene tekstveld wordt de weergavenaam van de opties opgeslagen en in de andere tekstveld wordt de waarde voor de opties opgeslagen). Elke keer dat een gebruiker het formulier verzendt, worden dus de volledige gegevens van de vervolgkeuzelijst verzonden. Ervan uitgaande dat u niet zoveel gegevens elke keer wilt verzenden, kunt u een aangepast script schrijven om dat uit te schakelen. De naam van de vervolgkeuzelijst is bijvoorbeeld `drpOrderedByStateProv` en de subformulierkoptekst wordt ingepakt. De naam van het HTML-invoerelement wordt `header[0].drpOrderedByStateProv[0]`. De naam van de verborgen velden waarin de gegevens van het vervolgkeuzemenu worden opgeslagen en verzonden, heeft de volgende namen: `header[0].drpOrderedByStateProv_DISPLAYITEMS_[0] header[0].drpOrderedByStateProv_VALUEITEMS_[0]`

U kunt deze invoerelementen op de volgende manier uitschakelen als u de gegevens niet wilt posten. `var __CUSTOM_SCRIPTS_VERSION = 1; //enabling the feature function _user_onsubmit() { var elems = document.getElementsByName("header[0].drpOrderedByStateProv_DISPLAYITEMS_[0]"); elems[0].disabled = true; elems = document.getElementsByName("header[0].drpOrderedByStateProv_VALUEITEMS_[0]"); elems[0].disabled = true; }`

```java
header[0].drpOrderedByStateProv_DISPLAYITEMS_[0] header[0].drpOrderedByStateProv_VALUEITEMS_[0]
```

```java
var __CUSTOM_SCRIPTS_VERSION = 1; //enabling the feature
    function _user_onsubmit() {
    var elems = document.getElementsByName("header[0].drpOrderedByStateProv_DISPLAYITEMS_[0]");
    elems[0].disabled = true;
    elems = document.getElementsByName("header[0].drpOrderedByStateProv_VALUEITEMS_[0]");
    elems[0].disabled = true;
    }
```

## XFA-subsets {#xfa-subsets}

Wanneer u formulierontwerpen maakt die moeten worden gerenderd als HTML, moet u het script beperken tot de XFA-subset voor scripts in JavaScript-taal.

Scripts die op de client worden uitgevoerd of op zowel de client als de server worden uitgevoerd, moeten binnen de XFA-subset worden geschreven. Scripts die op de server worden uitgevoerd, kunnen het volledige XFA-scriptmodel gebruiken en ook FormCalc gebruiken. Voor informatie over het gebruik van JavaScript raadpleegt u [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63).

Wanneer scripts op de client worden uitgevoerd, kan alleen het huidige deelvenster dat wordt weergegeven, een script gebruiken. U kunt bijvoorbeeld geen script uitvoeren op velden in deelvenster A wanneer deelvenster B wordt weergegeven. Wanneer scripts op de server worden uitgevoerd, zijn alle deelvensters toegankelijk.

Wees voorzichtig bij het gebruik van SOM-expressies (Scripting Object Model) in scripts die op de client worden uitgevoerd. Alleen een vereenvoudigde subset van SOM-expressies wordt ondersteund door scripts die op de client worden uitgevoerd.

## Gebeurtenistiming {#event-timing}

De XFA-subset definieert de XFA-gebeurtenissen die zijn toegewezen aan HTML-gebeurtenissen. Er is een klein verschil in gedrag met betrekking tot de timing van de gebeurtenissen calculate and validate. In een webbrowser wordt een volledige gebeurtenis calculate uitgevoerd wanneer u een veld verlaat. Gebeurtenissen berekenen worden niet automatisch uitgevoerd wanneer u een wijziging in een veldwaarde aanbrengt. U kunt een Calculate-gebeurtenis afdwingen door de `xfa.form.execCalculate` methode.

In een webbrowser worden validatiegebeurtenissen alleen uitgevoerd wanneer een veld wordt gesloten of een formulier wordt verzonden. U kunt een validatiegebeurtenis afdwingen met de opdracht `xfa.form.execValidate` methode.

Forms die wordt weergegeven in een webbrowser (in tegenstelling tot Adobe Reader of Acrobat), voldoet aan de XFA null-test (fouten of waarschuwingen) voor verplichte velden.

* Als de null-test een fout veroorzaakt en u een veld verlaat zonder een waarde op te geven, wordt een berichtvenster weergegeven en wordt u naar het veld verplaatst nadat u op OK hebt geklikt.
* Als een null-test een waarschuwing produceert en u een veld verlaat zonder een waarde op te geven, wordt u gevraagd op OK of Annuleren te klikken. U kunt dan doorgaan zonder een waarde op te geven of terug te keren naar het veld om een waarde in te voeren.

Voor meer informatie over een ongeldige test, zie [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63).

## Formulierknoppen {#form-buttons}

Als u op een knop Verzenden klikt, worden formuliergegevens naar de Forms-service verzonden en wordt het einde van de formulierverwerking aangegeven. De `preSubmit` -gebeurtenis kan zo worden ingesteld dat deze op de client of server wordt uitgevoerd. De `preSubmit` De gebeurtenis wordt uitgevoerd voordat het formulier wordt verzonden als dit is geconfigureerd om op de client te worden uitgevoerd. Anders wordt de `preSubmit` De gebeurtenis wordt tijdens het verzenden van het formulier op de server uitgevoerd. Voor meer informatie over de `preSubmit` gebeurtenis, zie [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63).

Als er aan een knop geen clientscript is gekoppeld, worden gegevens naar de server verzonden, worden berekeningen op de server uitgevoerd en wordt het HTML-formulier opnieuw gegenereerd. Als een knop een clientscript bevat, worden er geen gegevens naar de server verzonden en wordt het clientscript in de webbrowser uitgevoerd.

## HTML 4.0 webbrowser {#html-4-0-web-browser}

Een webbrowser die alleen HTML 4.0 ondersteunt, kan het scriptmodel van de XFA-subset voor client-side niet ondersteunen. Wanneer u een formulierontwerp maakt dat zowel in HTML 4.0 als in MSDHTML of CSS2HTML werkt, wordt een script dat is gemarkeerd om op de client te worden uitgevoerd, daadwerkelijk op de server uitgevoerd. Stel dat een gebruiker op een knop klikt die zich op een formulier bevindt dat in een webbrowser van HTML 4.0 wordt weergegeven. In dit geval worden de formuliergegevens verzonden naar de server waar het clientscript wordt uitgevoerd.

U wordt aangeraden de formulierlogica in Calculate-gebeurtenissen te plaatsen, die op de server in HTML 4.0 en op de client voor MSDHTML of CSS2HTML worden uitgevoerd.

## Presentatiewijzigingen behouden {#maintaining-presentation-changes}

Bij het schakelen tussen HTML-pagina&#39;s (deelvensters) blijft alleen de status van de gegevens behouden. Instellingen zoals achtergrondkleur of verplichte veldinstellingen blijven niet behouden (als deze afwijken van de oorspronkelijke instellingen). Als u de presentatiestatus wilt behouden, moet u (gewoonlijk verborgen) velden maken die de presentatiestatus van velden aangeven. Als u een script toevoegt aan de `Calculate` Als u de presentatie wijzigt op basis van verborgen veldwaarden, kunt u de presentatiestatus behouden wanneer u heen en weer gaat tussen HTML pagina&#39;s (deelvensters).

In het volgende script wordt het `fillColor` van een veld op basis van de waarde van `hiddenField`. Stel dat dit script zich in een veld bevindt `Calculate` gebeurtenis.

```java
     If (hiddenField.rawValue == 1)
         this.fillColor = "255,0,0"
     else
         this.fillColor = "0,255,0"
```

>[!NOTE]
>
Statische objecten worden niet weergegeven in een gerenderde HTML-vorm wanneer ze in een tabelcel zijn genest. Een cirkel en rechthoek die in een tabelcel zijn genest, worden bijvoorbeeld niet weergegeven in een HTML-formulier voor renderen. Dezelfde statische objecten worden echter correct weergegeven wanneer deze zich buiten de tabel bevinden.

## HTML-formulieren digitaal ondertekenen {#digitally-signing-html-forms}

U kunt geen HTML-formulier ondertekenen dat een digitaal handtekeningveld bevat als het formulier wordt weergegeven als een van de volgende HTML-transformaties:

* AHTML
* HTML4
* StaticHTML
* NoScriptXHTML

Zie voor informatie over het digitaal ondertekenen van een document [Documenten digitaal ondertekenen en certificeren](/help/forms/developing/digitally-signing-certifying-documents.md)

## Een XHTML-formulier dat voldoet aan toegankelijkheidsrichtlijnen weergeven {#rendering-an-accessibility-guidelines-compliant-xhtml-form}

U kunt een volledig HTML formulier weergeven dat voldoet aan toegankelijkheidsrichtlijnen. Het formulier wordt dus gegenereerd binnen volledige HTML-tags, in tegenstelling tot het HTML-formulier dat wordt weergegeven binnen body-tags (geen volledige HTML-pagina).

## Formuliergegevens valideren {#validating-form-data}

Het wordt aanbevolen om het gebruik van validatieregels voor formuliervelden te beperken bij het weergeven van het formulier als een HTML-formulier. Sommige validatieregels worden mogelijk niet ondersteund voor HTML-formulieren. Wanneer bijvoorbeeld een validatiepatroon van DD-MM-JJJJ wordt toegepast op een `Date/Time` veld in een formulierontwerp dat wordt weergegeven als een HTML-formulier, werkt het niet correct, zelfs als de datum op de juiste wijze wordt ingevoerd. Dit validatiepatroon werkt echter goed voor formulieren die worden weergegeven als PDF.

>[!NOTE]
>
Voor meer informatie over de Forms-service raadpleegt u [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Overzicht van de stappen {#summary-of-steps}

Voer de volgende stappen uit om een HTML-formulier te genereren:

1. Inclusief projectbestanden.
1. Maak een Forms Client API-object.
1. Stel HTML-uitvoeringsopties in.
1. Een HTML-formulier weergeven.
1. Schrijf de gegevensstroom van het formulier naar de webbrowser van de client.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**Een Forms Client API-object maken**

Voordat u gegevens via programmacode kunt importeren in een PDF formClient-API, moet u een service-client voor de integratie van formuliergegevens maken. Wanneer u een serviceclient maakt, definieert u verbindingsinstellingen die vereist zijn om een service aan te roepen.

**Opties voor HTML bij uitvoering instellen**

U stelt HTML-uitvoeringsopties in wanneer u een HTML-formulier weergeeft. U kunt bijvoorbeeld een werkbalk toevoegen aan een HTML-formulier, zodat gebruikers bestandsbijlagen kunnen selecteren op de clientcomputer of bestandsbijlagen kunnen ophalen die met het HTML-formulier worden gegenereerd. Een werkbalk HTML is standaard uitgeschakeld. Als u een werkbalk wilt toevoegen aan een HTML-formulier, moet u via programmacode uitvoeringsopties instellen. Een werkbalk HTML bestaat standaard uit de volgende knoppen:

* `Home`: Hiermee wordt een koppeling naar de hoofdmap van de toepassing geboden.
* `Upload`: Hiermee wordt een gebruikersinterface weergegeven voor het selecteren van bestanden die u wilt bijvoegen bij het huidige formulier.
* `Download`: Biedt een gebruikersinterface voor het weergeven van de bijgevoegde bestanden.

Wanneer een werkbalk HTML op een HTML-formulier wordt weergegeven, kan een gebruiker maximaal tien bestanden selecteren die samen met de formuliergegevens moeten worden verzonden. Nadat de bestanden zijn verzonden, kan de Forms-service de bestanden ophalen.

Bij het weergeven van een formulier als HTML kunt u een gebruikersagent-waarde opgeven. Een gebruiker-agent waarde verstrekt browser en systeeminformatie. Dit is een optionele waarde en u kunt een lege tekenreekswaarde doorgeven. De weergave van een HTML-formulier met behulp van de Java API Quick start laat zien hoe u een gebruikersagent-waarde ophaalt en gebruikt om een formulier te genereren als HTML.

HTTP-URL&#39;s waarnaar formuliergegevens worden verzonden, kunnen worden opgegeven door de doel-URL in te stellen met de Forms Service Client API of kunnen worden opgegeven in de knop Verzenden in het XDP-formulierontwerp. Als het doel-URL is opgegeven in het formulierontwerp, moet u geen waarde instellen met de Forms Service Client API.

>[!NOTE]
>
Het weergeven van een HTML-formulier met een werkbalk is optioneel.

>[!NOTE]
>
Als u een AHTML-formulier genereert, wordt u aangeraden geen werkbalk aan het formulier toe te voegen.

**Een HTML-formulier renderen**

Als u een HTML-formulier wilt genereren, geeft u een formulierontwerp op dat in Designer is gemaakt en als XDP-bestand is opgeslagen. Selecteer een transformatietype HTML. U kunt bijvoorbeeld het transformatietype HTML opgeven waarmee een dynamische HTML wordt weergegeven voor Internet Explorer 5.0 of hoger.

Voor het weergeven van een HTML-formulier zijn ook waarden vereist, zoals URI-waarden die vereist zijn om andere formuliertypen te genereren.

**De formuliergegevensstroom naar de webbrowser van de client schrijven**

Wanneer de Forms-service een HTML-formulier weergeeft, wordt een formuliergegevensstroom geretourneerd die u naar de webbrowser van de client moet schrijven. Wanneer het formulier naar de clientwebbrowser wordt geschreven, is het HTML-formulier zichtbaar voor de gebruiker.

**Zie ook**

[Een formulier weergeven als HTML met de Java API](#render-a-form-as-html-using-the-java-api)

[Een formulier als HTML weergeven met de API voor webservices](#render-a-form-as-html-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Forms Service API Quick Start](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Interactieve PDF forms renderen](/help/forms/developing/rendering-interactive-pdf-forms.md)

[HTML Forms renderen met aangepaste werkbalken](/help/forms/developing/rendering-html-forms-custom-toolbars.md)

[Webtoepassingen maken die Forms renderen](/help/forms/developing/creating-web-applications-renders-forms.md)

## Een formulier weergeven als HTML met de Java API {#render-a-form-as-html-using-the-java-api}

Een HTML-formulier renderen met de Forms API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-forms-client.jar, op in het klassepad van uw Java-project.

1. Een Forms Client API-object maken

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `FormsServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Opties voor HTML bij uitvoering instellen

   * Een `HTMLRenderSpec` object met behulp van de constructor.
   * Als u een HTML-formulier wilt weergeven met een werkbalk, roept u de opdracht `HTMLRenderSpec` object `setHTMLToolbar` methode en een `HTMLToolbar` enum value. Als u bijvoorbeeld een verticale werkbalk HTML wilt weergeven, geeft u door `HTMLToolbar.Vertical`.
   * Als u de landinstellingswaarde voor het HTML-formulier wilt instellen, roept u de `HTMLRenderSpec` object `setLocale` en geeft een tekenreekswaarde door die de waarde van de landinstelling opgeeft. (Dit is een optionele instelling.)
   * Als u het HTML-formulier wilt weergeven binnen volledige HTML-tags, roept u de opdracht `HTMLRenderSpec` object `setOutputType` methode en doorgeven `OutputType.FullHTMLTags`. (Dit is een optionele instelling.)

   >[!NOTE]
   >
   Forms wordt niet gerenderd in HTML als de `StandAlone` optie is `true` en de `ApplicationWebRoot` verwijst naar een andere server dan de J2EE-toepassingsserver die als host fungeert voor AEM Forms (de `ApplicationWebRoot` waarde wordt opgegeven met behulp van de `URLSpec` object dat wordt doorgegeven aan het `FormsServiceClient` object `(Deprecated) renderHTMLForm` methode). Wanneer de `ApplicationWebRoot` is een andere server van de server die als host fungeert voor AEM Forms, moet de waarde van de URI van de webhoofdmap in de beheerconsole worden ingesteld als de URI-waarde van de webtoepassing van het formulier. U doet dit door u aan te melden bij de beheerconsole, op Services > Forms te klikken en de Web Root URI in te stellen als https://server-name:port/FormServer. Sla vervolgens uw instellingen op.

1. Een HTML-formulier renderen

   De `FormsServiceClient` object `(Deprecated) renderHTMLForm` en geeft de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u naar een formulierontwerp verwijst dat deel uitmaakt van een Forms-toepassing, moet u het volledige pad opgeven, zoals `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `TransformTo` Enum value that specifies the HTML preferences type. Als u bijvoorbeeld een HTML-formulier wilt genereren dat compatibel is met dynamic HTML voor Internet Explorer 5.0 of hoger, geeft u `TransformTo.MSDHTML`.
   * A `com.adobe.idp.Document` object dat gegevens bevat die met het formulier moeten worden samengevoegd. Als u geen gegevens wilt samenvoegen, geeft u een lege waarde door `com.adobe.idp.Document` object.
   * De `HTMLRenderSpec` -object waarin HTML-runtime-opties zijn opgeslagen.
   * Een tekenreekswaarde die de `HTTP_USER_AGENT` koptekstwaarde, bijvoorbeeld `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
   * A `URLSpec` object dat URI-waarden opslaat die vereist zijn om een HTML-formulier te genereren.
   * A `java.util.HashMap` object waarin bestandsbijlagen zijn opgeslagen. Dit is een optionele parameter en u kunt `null` als u geen bestanden aan het formulier wilt koppelen.

   De `(Deprecated) renderHTMLForm` methode retourneert een `FormsResult` object dat een formuliergegevensstroom bevat die naar de webbrowser van de client kan worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Een `com.adobe.idp.Document` door het object aan te roepen `FormsResult` object `getOutputContent` methode.
   * Hiermee wordt het inhoudstype van het dialoogvenster `com.adobe.idp.Document` object aanroepen `getContentType` methode.
   * Stel de `javax.servlet.http.HttpServletResponse` inhoudstype van object aanroepen `setContentType` en geeft u het inhoudstype van de `com.adobe.idp.Document` object.
   * Een `javax.servlet.ServletOutputStream` object dat wordt gebruikt om de formuliergegevensstroom naar de webbrowser van de client te schrijven door het aanroepen van de `javax.servlet.http.HttpServletResponse` object `getOutputStream` methode.
   * Een `java.io.InputStream` door het object aan te roepen `com.adobe.idp.Document` object `getInputStream` methode.
   * Maak een bytearray en vul deze met de formuliergegevensstroom door de `InputStream` object `read` en de bytearray doorgeven als een argument.
   * De `javax.servlet.ServletOutputStream` object `write` methode om de formuliergegevensstroom naar de webbrowser van de client te verzenden. Geef de bytearray door aan de `write` methode.

**Zie ook**

[Forms renderen als HTML](#rendering-forms-as-html)

[Snel starten (SOAP modus): Een HTML-formulier weergeven met de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-an-html-form-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Een formulier als HTML weergeven met de API voor webservices {#render-a-form-as-html-using-the-web-service-api}

Een HTML-formulier renderen met de Forms API (webservice):

1. Projectbestanden opnemen

   * Maak Java-proxyklassen die gebruikmaken van de Forms-service WSDL.
   * Neem de Java-proxyklassen op in het klassepad.

1. Een Forms Client API-object maken

   Een `FormsService` -object en stel verificatiewaarden in.

1. Opties voor HTML bij uitvoering instellen

   * Een `HTMLRenderSpec` object met behulp van de constructor.
   * Als u een HTML-formulier wilt weergeven met een werkbalk, roept u de opdracht `HTMLRenderSpec` object `setHTMLToolbar` methode en een `HTMLToolbar` enum value. Als u bijvoorbeeld een verticale werkbalk HTML wilt weergeven, geeft u door `HTMLToolbar.Vertical`.
   * Als u de landinstellingswaarde voor het HTML-formulier wilt instellen, roept u de `HTMLRenderSpec` object `setLocale` en geeft een tekenreekswaarde door die de waarde van de landinstelling opgeeft. Zie voor meer informatie [AEM Forms API-naslag](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).
   * Als u het HTML-formulier wilt weergeven binnen volledige HTML-tags, roept u de opdracht `HTMLRenderSpec` object `setOutputType` methode en doorgeven `OutputType.FullHTMLTags`.

   >[!NOTE]
   >
   Forms wordt niet gerenderd in HTML als de `StandAlone` optie is `true` en de `ApplicationWebRoot` verwijst naar een andere server dan de J2EE-toepassingsserver die als host fungeert voor AEM Forms (de `ApplicationWebRoot` waarde wordt opgegeven met behulp van de `URLSpec` object dat wordt doorgegeven aan het `FormsServiceClient` object `(Deprecated) renderHTMLForm` methode). Wanneer de `ApplicationWebRoot` is een andere server van de server die als host fungeert voor AEM Forms, moet de waarde van de URI van de webhoofdmap in de beheerconsole worden ingesteld als de URI-waarde van de webtoepassing van het formulier. U doet dit door u aan te melden bij de beheerconsole, op Services > Forms te klikken en de Web Root URI in te stellen als https://server-name:port/FormServer. Sla vervolgens uw instellingen op.

1. Een HTML-formulier renderen

   De `FormsService` object `(Deprecated) renderHTMLForm` en geeft de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u naar een formulierontwerp verwijst dat deel uitmaakt van een Forms-toepassing, moet u het volledige pad opgeven, zoals `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `TransformTo` Enum value that specifies the HTML preferences type. Als u bijvoorbeeld een HTML-formulier wilt genereren dat compatibel is met dynamic HTML voor Internet Explorer 5.0 of hoger, geeft u `TransformTo.MSDHTML`.
   * A `BLOB` object dat gegevens bevat die met het formulier moeten worden samengevoegd. Als u geen gegevens wilt samenvoegen, geeft u `null`. (Zie [Forms vooraf vullen met stroombare indelingen](/help/forms/developing/prepopulating-forms-flowable-layouts.md#prepopulating-forms-with-flowable-layouts).)
   * De `HTMLRenderSpec` -object waarin HTML-runtime-opties zijn opgeslagen.
   * Een tekenreekswaarde die de `HTTP_USER_AGENT` koptekstwaarde, bijvoorbeeld `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`. U kunt een lege tekenreeks doorgeven als u deze waarde niet wilt instellen.
   * A `URLSpec` object dat URI-waarden opslaat die vereist zijn om een HTML-formulier te genereren. (Zie [URI-waarden opgeven](/help/forms/developing/rendering-interactive-pdf-forms.md).)
   * A `java.util.HashMap` object waarin bestandsbijlagen zijn opgeslagen. Dit is een optionele parameter en u kunt `null` als u geen bestanden aan het formulier wilt koppelen. (Zie [Bestanden aan het formulier koppelen](/help/forms/developing/rendering-interactive-pdf-forms.md).)
   * Een leeg `com.adobe.idp.services.holders.BLOBHolder` object dat door de methode wordt gevuld. Met deze parameterwaarde wordt het gerenderde formulier opgeslagen.
   * Een leeg `com.adobe.idp.services.holders.BLOBHolder` object dat door de methode wordt gevuld. In deze parameter worden de XML-uitvoergegevens opgeslagen.
   * Een leeg `javax.xml.rpc.holders.LongHolder` object dat door de methode wordt gevuld. In dit argument wordt het aantal pagina&#39;s in het formulier opgeslagen.
   * Een leeg `javax.xml.rpc.holders.StringHolder` object dat door de methode wordt gevuld. In dit argument wordt de waarde van de landinstelling opgeslagen.
   * Een leeg `javax.xml.rpc.holders.StringHolder` object dat door de methode wordt gevuld. In dit argument wordt de gebruikte HTML-renderwaarde opgeslagen.
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

[Forms renderen als HTML](#rendering-forms-as-html)

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
