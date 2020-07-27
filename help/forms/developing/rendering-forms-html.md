---
title: Formulieren weergeven als HTML
seo-title: Formulieren weergeven als HTML
description: 'null'
seo-description: 'null'
uuid: bd8edb6f-333b-4ceb-9877-618f5377f56f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 669ede46-ea55-444b-a23f-23a86e5aff8e
translation-type: tm+mt
source-git-commit: c74d9e86727f2deda62b8d1eb105b28ef4b6d184
workflow-type: tm+mt
source-wordcount: '4108'
ht-degree: 1%

---


# Formulieren weergeven als HTML {#rendering-forms-as-html}

De service Forms geeft formulieren als HTML weer in reactie op een HTTP-aanvraag van een webbrowser. Een voordeel van het weergeven van een formulier als HTML is dat de computer waarop de webbrowser van de client zich bevindt, geen Adobe Reader, Acrobat of Flash Player vereist (voor formulierhulplijnen (afgekeurd)).

Als u een formulier wilt weergeven als HTML, moet het formulierontwerp worden opgeslagen als een XDP-bestand. Een formulierontwerp dat is opgeslagen als een PDF-bestand, kan niet worden weergegeven als HTML. Houd rekening met de volgende criteria wanneer u een formulierontwerp ontwikkelt in Designer dat wordt weergegeven als HTML:

* Gebruik niet de randeigenschappen van een object om lijnen, vakken of rasters op een formulier te tekenen. In sommige browsers worden randen mogelijk niet zo weergegeven zoals ze in de voorbeeldweergave van te zien zijn. Objecten kunnen gelaagd worden weergegeven of ze kunnen andere objecten van hun verwachte positie afduwen.
* U kunt lijnen, rechthoeken en cirkels gebruiken om de achtergrond te definiëren.
* Teken tekst iets groter dan nodig lijkt om ruimte te maken voor de tekst. In sommige webbrowsers wordt de tekst niet leesbaar weergegeven.

>[!NOTE]
>
>Als u een formulier met TIFF-afbeeldingen weergeeft met behulp van de methoden `FormServiceClient` en de methoden van het `(Deprecated) renderHTMLForm` `renderHTMLForm2` object, zijn de TIFF-afbeeldingen niet zichtbaar in het weergegeven HTML-formulier dat wordt weergegeven in Internet Explorer- of Mozilla Firefox-browsers. Deze browsers bieden geen native ondersteuning voor TIFF-afbeeldingen.

## HTML-pagina&#39;s {#html-pages}

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

Wanneer formulierontwerpen worden weergegeven als HTML-formulieren, blijven de deelvensters beperkt tot een bepaald paginaformaat. Als u dynamische subformulieren hebt, moeten deze in het deelvenstersubformulier worden genest. Dynamische subformulieren kunnen worden uitgebreid naar een oneindig aantal HTML-pagina&#39;s.

Wanneer een formulier wordt weergegeven als een HTML-formulier, hebben paginaformaten (vereist voor paginering van formulieren die worden weergegeven als PDF) geen betekenis. Omdat een formulier met een stroombare indeling kan worden uitgebreid naar een oneindig aantal HTML-pagina&#39;s, is het belangrijk dat u geen voetteksten op de master pagina plaatst. Een voettekst onder het inhoudsgebied op een master pagina kan HTML-inhoud overschrijven die voorbij een paginagrens loopt.

U moet expliciet van deelvenster naar deelvenster gaan met de methoden `xfa.host.pageUp` en `xfa.host.pageDown` methoden. U kunt pagina&#39;s wijzigen door een formulier naar de service Forms te verzenden en het formulier weer terug te sturen naar het clientapparaat, meestal een webbrowser.

>[!NOTE]
>
>Het proces waarbij een formulier naar de service Forms wordt verzonden en vervolgens het formulier door de service Forms naar het clientapparaat wordt teruggestuurd, wordt ook wel &#39;round tripping data&#39;-gegevens naar de server genoemd.

>[!NOTE]
>
>Als u de weergave van de knop Digitale HTML-handtekening op een HTML-formulier wilt aanpassen, moet u de volgende eigenschappen wijzigen in het bestand fscdigsig.css (in het bestand adobe-forms-ds.ear > adobe-forms-ds.war):

**.fsc-ds-ssb**: Dit stijlblad is van toepassing in het geval van een leeg tekenveld.

**.fsc-ds-ssv**: Dit stijlblad is van toepassing in het geval van een geldig tekenveld.

**.fsc-ds-ssc**: Dit stijlblad is van toepassing in het geval van een geldig handtekeningveld, maar er zijn gegevens gewijzigd.

**.fsc-ds-ssi**: Dit stijlblad is van toepassing in het geval van een ongeldig handtekeningveld.

**.fsc-ds-popup-bg**: Deze stijlbladeigenschap wordt niet gebruikt.

**.fsc-ds-popup-btn**: Deze stijlbladeigenschap wordt niet gebruikt.

## Scripts uitvoeren {#running-scripts}

Een auteur van een formulier geeft aan of een script op de server of de client wordt uitgevoerd. De dienst van Vormen leidt tot een verdeelde, gebeurtenisverwerkingsmilieu voor uitvoering van vormintelligentie die tussen de cliënt en de server door de `runAt` attributen te gebruiken kan worden verdeeld. Zie [Forms Designer voor meer informatie over dit kenmerk of over het maken van scripts in formulierontwerpen](https://www.adobe.com/go/learn_aemforms_designer_63)

De Forms-service kan scripts uitvoeren terwijl het formulier wordt gegenereerd. Hierdoor kunt u een formulier vooraf invullen met gegevens door verbinding te maken met een database of met webservices die mogelijk niet beschikbaar zijn op de client. U kunt de `Click` gebeurtenis van een knoop ook plaatsen om op de server te lopen zodat de cliënt reisgegevens aan de server zal afronden. Hierdoor kan de client scripts uitvoeren waarvoor mogelijk serverbronnen nodig zijn, zoals een ondernemingsdatabase, terwijl een gebruiker communiceert met een formulier. Voor HTML-formulieren kunnen formele scripts alleen op de server worden uitgevoerd. Als gevolg hiervan moet u deze scripts markeren om te worden uitgevoerd bij `server` of `both`.

U kunt formulieren ontwerpen die tussen pagina&#39;s (deelvensters) bewegen door ze aan te roepen `xfa.host.pageUp` en `xfa.host.pageDown` methoden te gebruiken. Dit script wordt in de `Click` gebeurtenis van een knop geplaatst en het `runAt` kenmerk wordt ingesteld op `Both`. De reden die u kiest, `Both` is dat Adobe Reader of Acrobat (voor formulieren die als PDF worden gerenderd) pagina&#39;s kan wijzigen zonder naar de server te gaan en dat HTML-formulieren pagina&#39;s kunnen wijzigen door gegevens naar de server af te snijden. Een formulier wordt dus naar de service Forms verzonden en een formulier wordt als HTML weergegeven met de nieuwe pagina.

U wordt aangeraden scriptvariabelen en formuliervelden niet dezelfde namen te geven, zoals item. Sommige webbrowsers, zoals Internet Explorer, initialiseren een variabele met dezelfde naam als een formulierveld, waardoor een scriptfout optreedt. Het is een goede gewoonte om formuliervelden en scriptvariabelen verschillende namen te geven.

Wanneer u HTML-formulieren weergeeft die zowel paginanavigatiefunctionaliteit als formulierscripts bevatten (neem bijvoorbeeld aan dat met een script veldgegevens worden opgehaald uit een database telkens wanneer het formulier wordt gegenereerd), moet u ervoor zorgen dat het formulierscript zich in de gebeurtenis form:calculate bevindt in plaats van in de gebeurtenis form:readyevent.

Formulierscripts die zich in de gebeurtenis form:ready bevinden, worden slechts eenmaal uitgevoerd tijdens de eerste weergave van het formulier en worden niet uitgevoerd voor volgende opvragingen van pagina&#39;s. De gebeurtenis form:calculate wordt daarentegen uitgevoerd voor elke paginanavigatie waarin het formulier wordt gegenereerd.

>[!NOTE]
Op een formulier met meerdere pagina&#39;s blijven wijzigingen die door JavaScript in een pagina zijn aangebracht, niet behouden als u naar een andere pagina gaat.

U kunt aangepaste scripts aanroepen voordat u een formulier verzendt. Deze functie werkt op alle beschikbare browsers. Deze kan echter alleen worden gebruikt wanneer gebruikers het HTML-formulier weergeven waarvan de `Output Type` eigenschap is ingesteld op `Form Body`. Het zal niet werken wanneer het `Output Type` is `Full HTML`. Zie Formulieren configureren in de Help voor het beheer voor stappen om deze functie te configureren.

U moet eerst een callback-functie definiëren die wordt aangeroepen voordat u het formulier verzendt, waarbij de naam van de functie `_user_onsubmit`is. Er wordt aangenomen dat de functie geen uitzondering genereert of dat de uitzondering wordt genegeerd als dit het geval is. Het wordt aanbevolen de JavaScript-functie in de kopsectie van de HTML te plaatsen. nochtans, kunt u het overal vóór het eind van de manuscriptmarkeringen verklaren die omvatten `xfasubset.js`.

Wanneer de formserver een XDP teruggeeft die een drop-down lijst bevat, naast het creëren van de drop-down lijst, leidt het ook tot twee verborgen tekstgebieden. In deze tekstvelden worden de gegevens van de vervolgkeuzelijst opgeslagen (in de ene tekstveld wordt de weergavenaam van de opties opgeslagen en in de andere tekstveld wordt de waarde voor de opties opgeslagen). Daarom wordt elke keer dat een gebruiker het formulier verzendt, het volledige gegeven van de vervolgkeuzelijst verzonden. Ervan uitgaande dat u niet zoveel gegevens elke keer wilt verzenden, kunt u een aangepast script schrijven om dat uit te schakelen. Bijvoorbeeld: De naam van de vervolgkeuzelijst wordt weergegeven `drpOrderedByStateProv` en onderaan de koptekst van het subformulier geplaatst. De naam van het HTML-invoerelement wordt gewijzigd `header[0].drpOrderedByStateProv[0]`. De naam van de verborgen velden waarin de gegevens van het vervolgkeuzemenu worden opgeslagen en verzonden, heeft de volgende namen: `header[0].drpOrderedByStateProv_DISPLAYITEMS_[0] header[0].drpOrderedByStateProv_VALUEITEMS_[0]`

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

Wanneer u formulierontwerpen maakt om als HTML te worden gerenderd, moet u het script beperken tot de XFA-subset voor scripts in JavaScript-taal.

Scripts die op de client worden uitgevoerd of op zowel de client als de server worden uitgevoerd, moeten binnen de XFA-subset worden geschreven. Scripts die op de server worden uitgevoerd, kunnen het volledige XFA-scriptmodel gebruiken en ook FormCalc gebruiken. Zie [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63)voor meer informatie over het gebruik van JavaScript.

Bij het uitvoeren van scripts op de client kan alleen het deelvenster dat momenteel wordt weergegeven, scripts gebruiken. U kunt bijvoorbeeld geen script uitvoeren op velden die zich in deelvenster A bevinden wanneer deelvenster B wordt weergegeven. Wanneer scripts op de server worden uitgevoerd, zijn alle deelvensters toegankelijk.

U moet ook voorzichtig zijn wanneer het gebruiken van de uitdrukkingen van het Model van Objecten Scripting (SOM) binnen manuscripten die op de cliënt lopen. Alleen een vereenvoudigde subset van SOM-expressies wordt ondersteund door scripts die op de client worden uitgevoerd.

## Gebeurtenistiming {#event-timing}

De XFA-subset definieert de XFA-gebeurtenissen die zijn toegewezen aan HTML-gebeurtenissen. Er is een klein verschil in gedrag met betrekking tot de timing van de gebeurtenissen calculate and validate. In een webbrowser wordt een volledige gebeurtenis calculate uitgevoerd wanneer u een veld verlaat. Gebeurtenissen berekenen worden niet automatisch uitgevoerd wanneer u een wijziging in een veldwaarde aanbrengt. U kunt een gebeurtenis calculate forceren door de `xfa.form.execCalculate` methode te roepen.

In een webbrowser worden validatiegebeurtenissen alleen uitgevoerd wanneer een veld wordt gesloten of een formulier wordt verzonden. U kunt een validate-gebeurtenis afdwingen met de `xfa.form.execValidate` methode.

Formulieren die in een webbrowser worden weergegeven (in tegenstelling tot Adobe Reader of Acrobat), voldoen aan de XFA-null-test (fouten of waarschuwingen) voor verplichte velden.

* Als de null-test een fout veroorzaakt en u een veld verlaat zonder een waarde op te geven, wordt een berichtvenster weergegeven en wordt u naar het veld verplaatst nadat u op OK hebt geklikt.
* Als een null-test een waarschuwing produceert en u een veld verlaat zonder een waarde op te geven, wordt u gevraagd op OK of Annuleren te klikken. U kunt dan doorgaan zonder een waarde op te geven of terug te keren naar het veld om een waarde in te voeren.

Zie [Formulierontwerper](https://www.adobe.com/go/learn_aemforms_designer_63)voor meer informatie over een null-test.

## Formulierknoppen {#form-buttons}

Als u op een knop Verzenden klikt, worden formuliergegevens naar de Forms-service verzonden en wordt het einde van de formulierverwerking aangegeven. De `preSubmit` gebeurtenis kan worden ingesteld om op de client of server te worden uitgevoerd. De `preSubmit` gebeurtenis wordt uitgevoerd voordat het formulier wordt verzonden als dit is geconfigureerd om op de client te worden uitgevoerd. Anders wordt de `preSubmit` gebeurtenis tijdens het verzenden van het formulier op de server uitgevoerd. Zie `preSubmit` Formulierontwerper [voor meer informatie over de](https://www.adobe.com/go/learn_aemforms_designer_63)gebeurtenis.

Als er aan een knop geen clientscript is gekoppeld, worden gegevens naar de server verzonden, worden berekeningen op de server uitgevoerd en wordt het HTML-formulier opnieuw gegenereerd. Als een knop een clientscript bevat, worden er geen gegevens naar de server verzonden en wordt het clientscript in de webbrowser uitgevoerd.

## HTML 4.0-webbrowser {#html-4-0-web-browser}

Een webbrowser die alleen HTML 4.0 ondersteunt, kan het scriptmodel van de XFA-subset client-side niet ondersteunen. Wanneer u een formulierontwerp maakt dat zowel in HTML 4.0 als in MSDHTML of CSS2HTML werkt, wordt een script dat is gemarkeerd om op de client te worden uitgevoerd, daadwerkelijk op de server uitgevoerd. Stel dat een gebruiker op een knop klikt die zich op een formulier bevindt dat in een HTML 4.0-webbrowser wordt weergegeven. In dit geval worden de formuliergegevens verzonden naar de server waar het clientscript wordt uitgevoerd.

U wordt aangeraden de formulierlogica in Calculate-gebeurtenissen te plaatsen. Deze gebeurtenissen worden uitgevoerd op de server in HTML 4.0 en op de client voor MSDHTML of CSS2HTML.

## Presentatiewijzigingen behouden {#maintaining-presentation-changes}

Bij het schakelen tussen HTML-pagina&#39;s (deelvensters) blijft alleen de status van de gegevens behouden. Instellingen zoals achtergrondkleur of verplichte veldinstellingen blijven niet behouden (als deze afwijken van de oorspronkelijke instellingen). Als u de presentatiestatus wilt behouden, moet u (gewoonlijk verborgen) velden maken die de presentatiestatus van velden aangeven. Als u een script toevoegt aan de `Calculate` gebeurtenis van een veld waarmee de presentatie wordt gewijzigd op basis van verborgen veldwaarden, kunt u de presentatiestatus behouden wanneer u heen en weer gaat tussen HTML-pagina&#39;s (deelvensters).

In het volgende script wordt de waarde `fillColor` van een veld behouden op basis van de waarde van `hiddenField`. Stel dat dit script zich in de `Calculate` gebeurtenis van een veld bevindt.

```java
     If (hiddenField.rawValue == 1)
         this.fillColor = "255,0,0"
     else
         this.fillColor = "0,255,0"
```

>[!NOTE]
Statische objecten worden niet weergegeven in een gerenderd HTML-formulier wanneer ze in een tabelcel zijn genest. Een cirkel en rechthoek die in een tabelcel zijn genest, worden bijvoorbeeld niet weergegeven in een HTML-renderformulier. Dezelfde statische objecten worden echter correct weergegeven wanneer deze zich buiten de tabel bevinden.

## HTML-formulieren digitaal ondertekenen {#digitally-signing-html-forms}

U kunt geen HTML-formulier ondertekenen dat een digitaal handtekeningveld bevat als het formulier wordt weergegeven als een van de volgende HTML-transformaties:

* AHTML
* HTML4
* StaticHTML
* NoScriptXHTML

Zie Documenten digitaal ondertekenen en certificeren voor informatie over het digitaal ondertekenen van een document. [Zie Documenten digitaal ondertekenen](/help/forms/developing/digitally-signing-certifying-documents.md)

## Een XHTML-formulier dat voldoet aan toegankelijkheidsrichtlijnen weergeven {#rendering-an-accessibility-guidelines-compliant-xhtml-form}

U kunt een volledig HTML-formulier weergeven dat voldoet aan toegankelijkheidsrichtlijnen. Het formulier wordt dus gegenereerd binnen volledige HTML-tags, in tegenstelling tot het HTML-formulier dat wordt weergegeven binnen body-tags (geen volledige HTML-pagina).

## Formuliergegevens valideren {#validating-form-data}

Het wordt aanbevolen het gebruik van validatieregels voor formuliervelden te beperken wanneer u het formulier weergeeft als een HTML-formulier. Sommige validatieregels worden mogelijk niet ondersteund voor HTML-formulieren. Wanneer bijvoorbeeld een validatiepatroon van DD-MM-JJJJ wordt toegepast op een `Date/Time` veld dat zich bevindt in een formulierontwerp dat als HTML-formulier wordt weergegeven, werkt het niet correct, zelfs niet als de datum correct is getypt. Dit validatiepatroon werkt echter goed voor formulieren die als PDF worden gegenereerd.

>[!NOTE]
Voor meer informatie over de dienst van Vormen, zie de Verwijzing van de [Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Overzicht van de stappen {#summary-of-steps}

Voer de volgende stappen uit om een HTML-formulier te genereren:

1. Inclusief projectbestanden.
1. Maak een Forms Client API-object.
1. Stel opties voor HTML-runtime in.
1. Een HTML-formulier renderen.
1. Schrijf de gegevensstroom van het formulier naar de webbrowser van de client.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**Een Forms Client API-object maken**

Voordat u gegevens via programmacode kunt importeren in een PDF formClient API, moet u een service-client maken voor de integratie van formuliergegevens. Wanneer u een serviceclient maakt, definieert u verbindingsinstellingen die vereist zijn om een service aan te roepen.

**Opties voor HTML-runtime instellen**

U stelt HTML-runtime-opties in wanneer u een HTML-formulier rendert. U kunt bijvoorbeeld een werkbalk toevoegen aan een HTML-formulier, zodat gebruikers bestandsbijlagen kunnen selecteren op de clientcomputer of bestandsbijlagen kunnen ophalen die met het HTML-formulier worden gegenereerd. Een HTML-werkbalk is standaard uitgeschakeld. Als u een werkbalk wilt toevoegen aan een HTML-formulier, moet u via programmacode opties voor de runtime instellen. Een HTML-werkbalk bestaat standaard uit de volgende knoppen:

* `Home`: Koppelt naar de hoofdmap van de toepassing.
* `Upload`: Biedt een gebruikersinterface voor het selecteren van bestanden die u wilt bijvoegen bij het huidige formulier.
* `Download`: Biedt een gebruikersinterface voor het weergeven van de bijgevoegde bestanden.

Wanneer een HTML-werkbalk op een HTML-formulier wordt weergegeven, kan een gebruiker maximaal tien bestanden selecteren die samen met de formuliergegevens moeten worden verzonden. Nadat de bestanden zijn verzonden, kan de service Forms de bestanden ophalen.

Bij het weergeven van een formulier als HTML kunt u een user-agent-waarde opgeven. Een gebruiker-agent waarde verstrekt browser en systeeminformatie. Dit is een optionele waarde en u kunt een lege tekenreekswaarde doorgeven. De weergave van een HTML-formulier met de snelle start van de Java API laat zien hoe u een gebruikersagent-waarde ophaalt en gebruikt om een formulier te genereren als HTML.

HTTP-URL&#39;s waarnaar formuliergegevens worden verzonden, kunnen worden opgegeven door de doel-URL in te stellen met de API voor de Forms Service Client of kunnen worden opgegeven in de knop Verzenden in het XDP-formulierontwerp. Als het doel-URL is opgegeven in het formulierontwerp, moet u geen waarde instellen met de API voor de Forms Service Client.

>[!NOTE]
Het weergeven van een HTML-formulier met een werkbalk is optioneel.

>[!NOTE]
Als u een AHTML-formulier genereert, wordt u aangeraden geen werkbalk aan het formulier toe te voegen.

**Een HTML-formulier renderen**

Als u een HTML-formulier wilt genereren, moet u een formulierontwerp opgeven dat in Designer is gemaakt en als XDP-bestand is opgeslagen. U moet ook een transformatietype voor HTML selecteren. U kunt bijvoorbeeld het transformatietype HTML opgeven dat een dynamische HTML voor Internet Explorer 5.0 of hoger rendert.

Voor het weergeven van een HTML-formulier zijn ook waarden vereist, zoals URI-waarden die vereist zijn voor het weergeven van andere formuliertypen.

**De formuliergegevensstroom naar de webbrowser van de client schrijven**

Wanneer de service Forms een HTML-formulier genereert, wordt een formuliergegevensstroom geretourneerd die u naar de webbrowser van de client moet schrijven. Wanneer het HTML-formulier naar de clientwebbrowser wordt geschreven, is het zichtbaar voor de gebruiker.

**Zie ook**

[Een formulier weergeven als HTML met de Java API](#render-a-form-as-html-using-the-java-api)

[Een formulier weergeven als HTML met de webservice-API](#render-a-form-as-html-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Forms Service API, snel aan de slag](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Interactieve PDF forms renderen](/help/forms/developing/rendering-interactive-pdf-forms.md)

[HTML-formulieren renderen met aangepaste werkbalken](/help/forms/developing/rendering-html-forms-custom-toolbars.md)

[Webtoepassingen maken die formulieren renderen](/help/forms/developing/creating-web-applications-renders-forms.md)

## Een formulier weergeven als HTML met de Java API {#render-a-form-as-html-using-the-java-api}

Een HTML-formulier renderen met de API voor formulieren (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-forms-client.jar, op in het klassenpad van uw Java-project.

1. Een Forms Client API-object maken

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `FormsServiceClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Opties voor HTML-runtime instellen

   * Maak een `HTMLRenderSpec` object met de constructor ervan.
   * Als u een HTML-formulier met een werkbalk wilt weergeven, roept u de methode van het `HTMLRenderSpec` object aan en geeft u een `setHTMLToolbar` `HTMLToolbar` opsommingswaarde door. Als u bijvoorbeeld een verticale HTML-werkbalk wilt weergeven, geeft u door `HTMLToolbar.Vertical`.
   * Als u de landinstellingswaarde voor het HTML-formulier wilt instellen, roept u de methode van het `HTMLRenderSpec` `setLocale` object aan en geeft u een tekenreekswaarde door die de waarde van de landinstelling opgeeft. (Dit is een optionele instelling.)
   * Als u het HTML-formulier wilt renderen binnen volledige HTML-tags, roept u de `HTMLRenderSpec` methode van het object aan en geeft u het door `setOutputType` `OutputType.FullHTMLTags`. (Dit is een optionele instelling.)

   >[!NOTE]
   Formulieren worden niet in HTML weergegeven als de `StandAlone` optie is `true` en de `ApplicationWebRoot` verwijzing naar een andere server dan de J2EE-toepassingsserver die AEM Forms host (de `ApplicationWebRoot` waarde wordt opgegeven met het `URLSpec` object dat wordt doorgegeven aan de `FormsServiceClient` methode van het `(Deprecated) renderHTMLForm` object). Als de server een andere server `ApplicationWebRoot` is van de server die als host fungeert voor de AEM Forms, moet de waarde van de URI van de webhoofdmap in de beheerconsole worden ingesteld als de URI-waarde van de webtoepassing van het formulier. Dit kan worden gedaan door login aan de beleidsconsole, het klikken van de Diensten > Vormen, en het plaatsen van de Wortel URI van het Web als https://server-name:port/FormServer. Sla vervolgens uw instellingen op.

1. Een HTML-formulier renderen

   Roep de methode van het `FormsServiceClient` `(Deprecated) renderHTMLForm` object aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u verwijst naar een formulierontwerp dat deel uitmaakt van een Forms-toepassing, moet u controleren of u het volledige pad opgeeft, bijvoorbeeld `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Een `TransformTo` opsommingswaarde waarmee het HTML-voorkeurstype wordt opgegeven. Als u bijvoorbeeld een HTML-formulier wilt genereren dat compatibel is met dynamische HTML voor Internet Explorer 5.0 of hoger, geeft u op `TransformTo.MSDHTML`.
   * Een `com.adobe.idp.Document` object dat gegevens bevat die met het formulier moeten worden samengevoegd. Geef een leeg `com.adobe.idp.Document` object door als u geen gegevens wilt samenvoegen.
   * Het `HTMLRenderSpec` object waarin de opties voor HTML-runtime worden opgeslagen.
   * Een tekenreekswaarde die de `HTTP_USER_AGENT` koptekstwaarde opgeeft; bijvoorbeeld `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
   * Een `URLSpec` object dat URI-waarden opslaat die vereist zijn om een HTML-formulier te genereren.
   * Een `java.util.HashMap` object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt opgeven `null` of u geen bestanden aan het formulier wilt koppelen.

   De `(Deprecated) renderHTMLForm` methode retourneert een `FormsResult` object dat een formuliergegevensstroom bevat die naar de webbrowser van de client kan worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Maak een `com.adobe.idp.Document` object door de `FormsResult` methode van het `getOutputContent` object aan te roepen.
   * Haal het inhoudstype van het `com.adobe.idp.Document` object op door de `getContentType` methode ervan aan te roepen.
   * Stel het inhoudstype van het `javax.servlet.http.HttpServletResponse` object in door de bijbehorende `setContentType` methode op te roepen en het inhoudstype van het `com.adobe.idp.Document` object door te geven.
   * Maak een `javax.servlet.ServletOutputStream` object dat wordt gebruikt om de gegevensstroom van het formulier naar de webbrowser van de client te schrijven door de `javax.servlet.http.HttpServletResponse` methode van het `getOutputStream` object aan te roepen.
   * Maak een `java.io.InputStream` object door de `com.adobe.idp.Document` methode van het `getInputStream` object aan te roepen.
   * Maak een bytearray en vul deze met de formuliergegevensstroom door de methode van het `InputStream` `read` object aan te roepen en de bytearray als een argument door te geven.
   * Roep de `javax.servlet.ServletOutputStream` methode van het `write` object aan om de formuliergegevensstroom naar de webbrowser van de client te verzenden. Geef de bytearray door aan de `write` methode.

**Zie ook**

[Formulieren weergeven als HTML](#rendering-forms-as-html)

[Snel starten (SOAP-modus): HTML-formulieren renderen met de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-an-html-form-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Een formulier weergeven als HTML met de webservice-API {#render-a-form-as-html-using-the-web-service-api}

Een HTML-formulier renderen met de API voor formulieren (webservice):

1. Projectbestanden opnemen

   * Maak Java-proxyklassen die de Forms service WSDL gebruiken.
   * Neem de Java-proxyklassen op in het klassepad.

1. Een Forms Client API-object maken

   Maak een `FormsService` object en stel verificatiewaarden in.

1. Opties voor HTML-runtime instellen

   * Maak een `HTMLRenderSpec` object met de constructor ervan.
   * Als u een HTML-formulier met een werkbalk wilt weergeven, roept u de methode van het `HTMLRenderSpec` object aan en geeft u een `setHTMLToolbar` `HTMLToolbar` opsommingswaarde door. Als u bijvoorbeeld een verticale HTML-werkbalk wilt weergeven, geeft u door `HTMLToolbar.Vertical`.
   * Als u de landinstellingswaarde voor het HTML-formulier wilt instellen, roept u de methode van het `HTMLRenderSpec` `setLocale` object aan en geeft u een tekenreekswaarde door die de waarde van de landinstelling opgeeft. Zie [AEM Forms API Reference](https://www.adobe.com/go/learn_aemforms_javadocs_63_en)voor meer informatie.
   * Als u het HTML-formulier wilt renderen binnen volledige HTML-tags, roept u de `HTMLRenderSpec` methode van het object aan en geeft u het door `setOutputType` `OutputType.FullHTMLTags`.

   >[!NOTE]
   Formulieren worden niet in HTML weergegeven als de `StandAlone` optie is `true` en de `ApplicationWebRoot` verwijzing naar een andere server dan de J2EE-toepassingsserver die AEM Forms host (de `ApplicationWebRoot` waarde wordt opgegeven met het `URLSpec` object dat wordt doorgegeven aan de `FormsServiceClient` methode van het `(Deprecated) renderHTMLForm` object). Als de server een andere server `ApplicationWebRoot` is van de server die als host fungeert voor de AEM Forms, moet de waarde van de URI van de webhoofdmap in de beheerconsole worden ingesteld als de URI-waarde van de webtoepassing van het formulier. Dit kan worden gedaan door login aan de beleidsconsole, het klikken van de Diensten > Vormen, en het plaatsen van de Wortel URI van het Web als https://server-name:port/FormServer. Sla vervolgens uw instellingen op.

1. Een HTML-formulier renderen

   Roep de methode van het `FormsService` `(Deprecated) renderHTMLForm` object aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u verwijst naar een formulierontwerp dat deel uitmaakt van een Forms-toepassing, moet u controleren of u het volledige pad opgeeft, bijvoorbeeld `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Een `TransformTo` opsommingswaarde waarmee het HTML-voorkeurstype wordt opgegeven. Als u bijvoorbeeld een HTML-formulier wilt genereren dat compatibel is met dynamische HTML voor Internet Explorer 5.0 of hoger, geeft u op `TransformTo.MSDHTML`.
   * Een `BLOB` object dat gegevens bevat die met het formulier moeten worden samengevoegd. Geef door als u geen gegevens wilt samenvoegen. `null` (Zie Formulieren [vooraf invullen met stroombare indelingen](/help/forms/developing/prepopulating-forms-flowable-layouts.md#prepopulating-forms-with-flowable-layouts).)
   * Het `HTMLRenderSpec` object waarin de opties voor HTML-runtime worden opgeslagen.
   * Een tekenreekswaarde die de `HTTP_USER_AGENT` koptekstwaarde opgeeft; bijvoorbeeld `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`. U kunt een lege tekenreeks doorgeven als u deze waarde niet wilt instellen.
   * Een `URLSpec` object dat URI-waarden opslaat die vereist zijn om een HTML-formulier te genereren. (Zie URI-waarden [](/help/forms/developing/rendering-interactive-pdf-forms.md)opgeven.)
   * Een `java.util.HashMap` object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt opgeven `null` of u geen bestanden aan het formulier wilt koppelen. (Zie Bestanden [aan het formulier](/help/forms/developing/rendering-interactive-pdf-forms.md)koppelen.)
   * Een leeg `com.adobe.idp.services.holders.BLOBHolder` object dat door de methode wordt gevuld. Met deze parameterwaarde wordt het gerenderde formulier opgeslagen.
   * Een leeg `com.adobe.idp.services.holders.BLOBHolder` object dat door de methode wordt gevuld. In deze parameter worden de XML-uitvoergegevens opgeslagen.
   * Een leeg `javax.xml.rpc.holders.LongHolder` object dat door de methode wordt gevuld. In dit argument wordt het aantal pagina&#39;s in het formulier opgeslagen.
   * Een leeg `javax.xml.rpc.holders.StringHolder` object dat door de methode wordt gevuld. In dit argument wordt de waarde van de landinstelling opgeslagen.
   * Een leeg `javax.xml.rpc.holders.StringHolder` object dat door de methode wordt gevuld. In dit argument wordt de gebruikte HTML-renderwaarde opgeslagen.
   * Een leeg `com.adobe.idp.services.holders.FormsResultHolder` object dat de resultaten van deze bewerking zal bevatten.

   De `(Deprecated) renderHTMLForm` methode vult het `com.adobe.idp.services.holders.FormsResultHolder` object dat als laatste argumentwaarde wordt doorgegeven, met een formuliergegevensstroom die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Maak een `FormResult` object door de waarde van het `com.adobe.idp.services.holders.FormsResultHolder` `value` gegevenslid van het object op te halen.
   * Maak een `BLOB` object dat formuliergegevens bevat door de `FormsResult` methode van het `getOutputContent` object aan te roepen.
   * Haal het inhoudstype van het `BLOB` object op door de `getContentType` methode ervan aan te roepen.
   * Stel het inhoudstype van het `javax.servlet.http.HttpServletResponse` object in door de bijbehorende `setContentType` methode op te roepen en het inhoudstype van het `BLOB` object door te geven.
   * Maak een `javax.servlet.ServletOutputStream` object dat wordt gebruikt om de gegevensstroom van het formulier naar de webbrowser van de client te schrijven door de `javax.servlet.http.HttpServletResponse` methode van het `getOutputStream` object aan te roepen.
   * Maak een bytearray en vul deze door de `BLOB` methode van het `getBinaryData` object aan te roepen. Hierdoor wordt de inhoud van het `FormsResult` object toegewezen aan de bytearray.
   * Roep de `javax.servlet.http.HttpServletResponse` methode van het `write` object aan om de formuliergegevensstroom naar de webbrowser van de client te verzenden. Geef de bytearray door aan de `write` methode.

**Zie ook**

[Formulieren weergeven als HTML](#rendering-forms-as-html)

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

