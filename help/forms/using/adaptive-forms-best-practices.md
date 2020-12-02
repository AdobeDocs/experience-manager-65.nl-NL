---
title: Aanbevolen werkwijzen voor het werken met adaptieve formulieren
seo-title: Aanbevolen werkwijzen voor het werken met adaptieve formulieren
description: Hierin worden de beste praktijken beschreven voor het opzetten van een AEM Forms-project, het ontwikkelen van adaptieve formulieren en het optimaliseren van de prestaties voor het AEM Forms-systeem.
seo-description: Hierin worden de beste praktijken beschreven voor het opzetten van een AEM Forms-project, het ontwikkelen van adaptieve formulieren en het optimaliseren van de prestaties voor het AEM Forms-systeem.
uuid: ed95fc64-56b3-4ea1-a5ba-2e96953fca56
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 43c431e4-5286-4f4e-b94f-5a7451c4a22c
translation-type: tm+mt
source-git-commit: 615b0db6da0986d7a74c42ec0d0e14bad7ede168
workflow-type: tm+mt
source-wordcount: '4296'
ht-degree: 0%

---


# Aanbevolen werkwijzen voor het werken met aangepaste formulieren {#best-practices-for-working-with-adaptive-forms}

## Overzicht {#overview}

Met Adobe Experience Manager (AEM)-formulieren kunt u complexe transacties transformeren in eenvoudige, prachtige digitale ervaringen. Het vereist echter gezamenlijke inspanningen om een efficiënt en productief AEM Forms-ecosysteem te implementeren, op te bouwen, uit te voeren en in stand te houden.

Dit document bevat richtlijnen en aanbevelingen die beheerders, auteurs en ontwikkelaars van formulieren kunnen gebruiken wanneer ze met AEM Forms werken, en met name wanneer ze onderdelen voor adaptieve formulieren gebruiken. Hierin worden de beste werkwijzen besproken, van het instellen van een formulierontwikkelingsproject tot het configureren, aanpassen, ontwerpen en optimaliseren van AEM Forms. Deze beste praktijken dragen collectief bij tot de algemene prestaties van het ecosysteem van AEM Forms.

Daarnaast zijn er enkele aanbevelingen voor algemene AEM aanbevolen procedures:

* [Tips en trucs: Implementeren en onderhouden van AEM](/help/sites-deploying/best-practices.md)
* [Tips en trucs: Inhoud ontwerpen](/help/sites-authoring/best-practices.md)
* [Tips en trucs: AEM beheren](/help/sites-administering/administer-best-practices.md)
* [Tips en trucs: Oplossingen ontwikkelen](/help/sites-developing/best-practices.md)

## AEM Forms {#set-up-and-configure-aem-forms} instellen en configureren

### Formulierontwikkelingsproject {#setting-up-forms-development-project} instellen

Een vereenvoudigde en gestandaardiseerde projectstructuur kan de ontwikkeling en het onderhoud aanzienlijk verminderen. Apache Maven is een opensource tool die wordt aanbevolen voor het bouwen van AEM projecten.

* Met Apache Maven `aem-project-archetype` kunt u een structuur voor AEM project maken en beheren. Het leidt tot geadviseerde structuur en malplaatjes voor uw AEM project. Ook, verstrekt het bouwstijlautomatisering en veranderingscontrolesystemen om het project te helpen beheren.

   * Gebruik de gemaskeerde opdracht `archetype:generate` om de initiële structuur te genereren.
   * Met de opdracht `eclipse:eclipse` gebruikt u de overgestoken projectbestanden en importeert u het project in een eclipse.

Voor meer informatie, zie [hoe te AEM Projecten bouwen gebruikend Apache Maven](/help/sites-developing/ht-projects-maven.md).

* Met het gereedschap FileVault of VLT kunt u de inhoud van een CRX- of AEM-instantie toewijzen aan uw bestandssysteem. Het verstrekt verrichtingen van het veranderingsbeheer, zoals controle-binnen en controle-out van de AEM projectinhoud. Zie [Het gereedschap VLT gebruiken](/help/sites-developing/ht-vlttool.md).

* Als u Eclipse-Geïntegreerde ontwikkelomgeving gebruikt, kunt u AEM hulpmiddelen van de Ontwikkelaar voor naadloze integratie van winde van de Verduistering met AEM instanties gebruiken om AEM toepassingen tot stand te brengen. Zie [AEM ontwikkelaarsgereedschappen voor Eclipse](/help/sites-developing/aem-eclipse.md) voor meer informatie.

* Sla geen inhoud op en breng geen wijzigingen aan in de map /libs. Maak overlays in /app-mappen om standaardfuncties uit te breiden of te overschrijven.

* Wanneer u pakketten maakt om inhoud te verplaatsen, moet u ervoor zorgen dat paden met pakketfilters correct zijn en dat alleen vereiste paden worden vermeld.

* Sla geen inhoud op en breng geen wijzigingen aan in de map /libs. Maak overlays in /app-mappen om standaardfuncties uit te breiden of te overschrijven.

* Bepaal correcte gebiedsdelen voor de pakketten om een vooraf bepaalde installatieorde/opeenvolging te dwingen.

* Maak geen knooppunten waarnaar kan worden verwezen in /libs of /apps.

### Planning voor ontwerpomgeving {#planning-for-authoring-environment}

Wanneer u uw AEM project hebt ingesteld, definieert u een strategie voor het ontwerpen en aanpassen van adaptieve formuliersjablonen en componenten.

* Een adaptieve formuliersjabloon is een gespecialiseerde AEM die structuur en de informatie over de kop- en voettekst van een adaptief formulier definieert. Een sjabloon heeft vooraf geconfigureerde indelingen, stijlen en basisstructuur voor een adaptief formulier. AEM Forms beschikt over out-of-the-box sjablonen en componenten waarmee u adaptieve formulieren kunt maken. U kunt echter naar wens aangepaste sjablonen en componenten maken. Het wordt aanbevolen vereisten te verzamelen voor aanvullende sjablonen en componenten die u nodig hebt in uw aangepaste formulieren. Zie [Aangepaste formulieren en componenten aanpassen](/help/forms/using/adaptive-forms-best-practices.md#customize-components) voor meer informatie.
* Met AEM Forms kunt u adaptieve formulieren maken op basis van de volgende formuliermodellen. De formuliermodellen fungeren als interface voor gegevensuitwisseling tussen een formulier en AEM en bieden een op XML gebaseerde structuur voor gegevensstroom binnen en buiten een adaptief formulier. Bovendien leggen de formuliermodellen regels en beperkingen op aan adaptieve formulieren in de vorm van schema- en XFA-beperkingen.

   * **Geen**: Voor adaptieve formulieren die met deze optie worden gemaakt, wordt geen formuliermodel gebruikt. De XML-gegevens die op basis van dergelijke formulieren worden gegenereerd, hebben een vlakke structuur met velden en bijbehorende waarden.
   * **XML- of JSON-schema**: De schema&#39;s van XML en JSON vertegenwoordigen de structuur waarin de gegevens door het achterste deelsysteem in uw organisatie worden geproduceerd of worden verbruikt. U kunt een schema aan een adaptief formulier koppelen en de elementen ervan gebruiken om dynamische inhoud aan het aangepaste formulier toe te voegen. De elementen van het schema zijn beschikbaar op het tabblad Gegevensmodel van de inhoudbrowser voor het ontwerpen van adaptieve formulieren. U kunt de schema-elementen slepen en neerzetten om het formulier samen te stellen.
   * **XFA-formuliersjabloon**: Het is een ideaal formuliermodel als u investeert in op XFA gebaseerde HTML5-formulieren. Dit biedt een directe manier om uw XFA-formulieren om te zetten in adaptieve formulieren. Bestaande XFA-regels blijven behouden in de bijbehorende adaptieve formulieren. De resulterende adaptieve formulieren ondersteunen XFA-constructies, zoals validaties, gebeurtenissen, eigenschappen en patronen.
   * **Formuliergegevensmodel**: Het is een voorkeursformuliermodel als u uw back-endsystemen, zoals databases, webservices en AEM gebruikersprofiel, wilt integreren om adaptieve formulieren vooraf in te vullen en verzonden formuliergegevens terug te schrijven naar de back-endsystemen. Met een formuliergegevensmodeleditor kunt u entiteiten en services definiëren en configureren in een formuliergegevensmodel waarmee u adaptieve formulieren kunt maken. Zie [AEM Forms Data Integration](/help/forms/using/data-integration.md) voor meer informatie.

Het is belangrijk om zorgvuldig het gegevensmodel te kiezen dat niet alleen aan uw vereisten voldoet maar uw bestaande investeringen in XFA en XSD activa uitbreidt, als om het even welk. Het wordt aanbevolen XSD-model te gebruiken om formuliersjablonen te maken, omdat de gegenereerde XML gegevens bevat volgens de XPATH-definitie in het schema. Het gebruik van XSD-model als standaardkeuze voor het formuliergegevensmodel helpt ook omdat het formulierontwerp loskoppelt van een back-end systeem dat gegevens verwerkt en verbruikt, en het verbetert de prestaties van het formulier door een-op-een-toewijzing van formuliervelden. BindRef van het veld kan ook de XPATH van de gegevenswaarde in XML worden gemaakt.

Zie [Een adaptief formulier maken](/help/forms/using/creating-adaptive-form.md) voor meer informatie.

* Er zijn enkele algemene secties in adaptieve formulieren. U kunt ze identificeren en een strategie definiëren om hergebruik van inhoud te bevorderen. Met adaptieve formulieren kunt u zelfstandige fragmenten maken en deze hergebruiken in verschillende formulieren. U kunt een deelvenster ook in een adaptief formulier opslaan als een fragment. Wijzigingen in een fragment worden in alle bijbehorende formulieren doorgevoerd. Hierdoor kunt u de ontwerptijd verkorten en consistentie in verschillende formulieren garanderen. Bovendien maakt het gebruik van fragmenten adaptieve formulieren lichtgewicht, wat resulteert in een verbeterde ontwerpervaring, met name in grote vormen. Zie [Adaptieve formulierfragmenten](/help/forms/using/adaptive-form-fragments.md) voor meer informatie.

### Aangepaste formulieren en componenten aanpassen {#customize-components}

* AEM Forms biedt adaptieve formuliersjablonen die u kunt gebruiken om adaptieve formulieren te maken. U kunt ook uw eigen sjablonen maken. AEM biedt statische en bewerkbare sjablonen.

   * Statische sjablonen worden gedefinieerd en geconfigureerd door ontwikkelaars.
   * Bewerkbare sjablonen worden gemaakt door auteurs die de sjablooneditor gebruiken. Met de sjablooneditor kunt u een basisstructuur en initiële inhoud in een sjabloon definiëren. Wijzigingen in de structuurlaag worden in alle formulieren met die sjabloon doorgevoerd. De eerste inhoud kan een vooraf geconfigureerd thema, vooraf ingevulde service, verzendactie enzovoort bevatten. Deze instellingen kunnen echter wel worden gewijzigd voor een formulier in de formuliereditor. Zie [Aangepaste formuliersjablonen](/help/forms/using/template-editor.md) voor meer informatie.

* Gebruik [inline styling](/help/forms/using/inline-style-adaptive-forms.md) voor het opmaken van een specifieke veld- of deelvensterinstantie. U kunt ook een klasse definiëren in een CSS-bestand en de klassenaam opgeven in de CSS-klasseneigenschap van de component.
* Neem een clientbibliotheek in een component op om stijlen consistent toe te passen op adaptieve formulieren of fragmenten die die component gebruiken. Zie [Een adaptieve formulierpaginacomponent maken](/help/forms/using/custom-adaptive-forms-templates.md) voor meer informatie.
* Pas stijlen toe die zijn gedefinieerd in een clientbibliotheek om adaptieve formulieren te selecteren door het pad naar de clientbibliotheek op te geven in het veld CSS-bestandspad in de adaptieve eigenschappen van de formuliercontainer.
* Als u een clientbibliotheek met uw stijlen wilt maken, kunt u het aangepaste CSS-bestand configureren in de basisclient van de Thema-editor of in de eigenschappen van de Form Container.
* Aangepaste formulieren bieden deelvensterlay-outs, zoals responsieve formulieren, tabbladen, accordeons en wizard, om te bepalen hoe formuliercomponenten worden ingedeeld in een deelvenster. U kunt aangepaste deelvensterlay-outs maken en beschikbaar maken voor gebruik door formulierauteurs. Zie [Aangepaste indelingscomponenten maken voor adaptieve formulieren](/help/forms/using/custom-layout-components-forms.md) voor meer informatie.
* U kunt ook specifieke aangepaste formuliercomponenten aanpassen, zoals velden en de indeling van deelvensters.

   * Gebruik de [Overlay](/help/sites-developing/overlays.md) functionaliteit van AEM om een kopie van een component te wijzigen. Het wordt afgeraden standaardcomponenten te wijzigen.
   * Als u de indeling van adaptieve formuliercomponenten buiten de box wilt aanpassen in /libs, [maakt u naast de [standaardlayouts](/help/forms/using/layout-capabilities-adaptive-forms.md) ook aangepaste indelingscomponenten.](/help/forms/using/custom-layout-components-forms.md)
   * Introduceer aangepaste interactiviteiten door aangepaste widgets of weergaven te maken. Het wordt afgeraden standaardcomponenten te wijzigen. Zie [Vormgevingsframework](/help/forms/using/introduction-widgets.md) voor meer informatie.

* Zie [Persoonlijke identificeerbare informatie verwerken](/help/forms/using/adaptive-forms-best-practices.md#p-handling-personally-identifiable-information-p) voor aanbevelingen voor de verwerking van PII-gegevens.

## Aangepaste formulieren voor auteurs {#author-adaptive-forms}

### Gebruikend touch-geoptimaliseerde UI voor het ontwerpen {#using-touch-optimized-ui-for-authoring}

* Gebruik de browser Objecten in het zijpaneel om snel velden te openen die diep onder in de formulierhiërarchie liggen. Met het zoekvak kunt u zoeken naar objecten in het formulier of in de objectstructuur en van het ene object naar het andere navigeren.
* Als u de eigenschappen van een component wilt weergeven en bewerken in de componentbrowser in de zijbalk, selecteert u de component en klikt u op ![cmp-1](assets/cmppr-1.png). U kunt ook dubbelklikken op een component om de eigenschappen ervan weer te geven in de eigenschappenbrowser.
* Gebruik sneltoetsen om snel actie te ondernemen op uw formulieren. Zie [AEM Forms-sneltoetsen](/help/forms/using/keyboard-shortcuts.md).

* Aangepaste formuliercomponenten worden alleen aanbevolen voor gebruik op adaptieve formulierpagina&#39;s. De componenten zijn afhankelijk van hun bovenliggende hiërarchie. Gebruik deze daarom niet op een AEM pagina.

Zie ook componentbeschrijvingen en aanbevolen procedures in [Inleiding tot het ontwerpen van adaptieve formulieren](/help/forms/using/introduction-forms-authoring.md).

### Regels in aangepaste vormen {#using-rules-in-adaptive-forms} gebruiken

AEM Forms biedt een [regeleditor](/help/forms/using/rule-editor.md) waarmee u regels kunt maken om dynamisch gedrag toe te voegen aan adaptieve formuliercomponenten. Met deze regels kunt u voorwaarden evalueren en acties activeren op componenten, zoals velden weergeven of verbergen, waarden berekenen, vervolgkeuzelijst dynamisch wijzigen, enzovoort.

De redacteur van de regel verstrekt een visuele redacteur en een coderedacteur voor het schrijven van regels. Overweeg het volgende wanneer het schrijven van regels gebruikend de wijze van de coderedacteur:

* Gebruik betekenisvolle en unieke namen voor formuliervelden en componenten om mogelijke conflicten te voorkomen tijdens het schrijven van regels.
* Gebruik de operator `this` voor een component om naar zichzelf in een regelexpressie te verwijzen. Het zorgt ervoor dat de regel geldig blijft zelfs als de componentennaam verandert. Bijvoorbeeld, `field1.valueCommit script: this.value > 10`.

* Gebruik componentnamen wanneer u naar andere formuliercomponenten verwijst. Gebruik de eigenschap `value` om de waarde van een veld of component op te halen. Bijvoorbeeld, `field1.value`.

* Verwijs componenten door relatieve unieke hiërarchie om het even welk conflict te vermijden. Bijvoorbeeld, `parentName.fieldName`.

* Wanneer u complexe of veelgebruikte regels afhandelt, kunt u bedrijfslogica als functies in een aparte clientbibliotheek schrijven die u kunt opgeven en hergebruiken voor adaptieve formulieren. De clientbibliotheek moet een zelfstandige bibliotheek zijn en mag geen externe afhankelijkheden hebben, behalve op jQuery en Underscore.js. U kunt de clientbibliotheek ook gebruiken om [servervalidatie](/help/forms/using/configuring-submit-actions.md#server-side-revalidation-in-adaptive-form) van verzonden formuliergegevens af te dwingen.
* Adaptieve formulieren bieden een set API&#39;s waarmee u kunt communiceren en waarmee u handelingen kunt uitvoeren op adaptieve formulieren. Enkele belangrijke API&#39;s zijn als volgt. Zie [JavaScript Library API reference for Adaptive Forms](https://adobe.com/go/learn_aemforms_documentation_63) voor meer informatie.

   * `guideBridge.reset()`: Hiermee herstelt u een formulier.
   * `guideBridge.submit()`: Hiermee verzendt u een formulier.
   * `guideBridge.setFocus(somExp, focusOption, runCompletionExp)`: Hiermee wordt de focus op een veld ingesteld.
   * `guideBridge.validate(errorList, somExpression, focus)`: Valideert een formulier.
   * `guideBridge.getDataXML(options)`: Hiermee worden formuliergegevens opgehaald als XML.
   * `guideBridge.resolveNode(somExpression)`: Hiermee wordt een formulierobject opgehaald.
   * `guideBridge.setProperty(somList, propertyName, valueList)`: Hiermee wordt de eigenschap van een formulierobject ingesteld.
   * Daarnaast kunt u de volgende veldeigenschappen gebruiken:

      * `field.value` om de waarde van een veld te wijzigen.
      * f `ield.enabled` om een veld in of uit te schakelen.
      * `field.visible` om de zichtbaarheid van een veld te wijzigen.

* Auteurs van adaptieve formulieren moeten mogelijk JavaScript-code schrijven om bedrijfslogica in een formulier te maken. JavaScript is weliswaar krachtig en effectief, maar het is waarschijnlijk dat hierdoor de beveiligingsverwachtingen in het gedrang komen. Daarom moet u ervoor zorgen dat de auteur van het formulier een vertrouwd persoon is en dat er processen zijn om de JavaScript-code te controleren en goed te keuren voordat een formulier in productie wordt genomen. De beheerder kan de toegang tot de toegang van de regelredacteur tot gebruikersgroepen beperken die op hun rol of functie wordt gebaseerd. Zie [Toegang van de regeleditor verlenen om gebruikersgroepen te selecteren](/help/forms/using/rule-editor-access-user-groups.md).
* U kunt expressies in regels gebruiken om adaptieve formulieren dynamisch te maken. Alle expressies zijn geldige JavaScript-expressies en gebruiken API&#39;s van het scriptmodel voor aangepaste formulieren. Deze expressies retourneren waarden van bepaalde typen. Zie [Aangepaste formulierexpressies](/help/forms/using/adaptive-form-expressions.md) voor meer informatie over expressies en tips en trucs.

### Werken met thema&#39;s {#working-with-themes}

Met Aangepast voor thema&#39;s kunt u herbruikbare stijlen maken die op verschillende formulieren kunnen worden toegepast voor een consistente vormgeving. U wordt aangeraden thema&#39;s te gebruiken om stijlen voor formuliercomponenten en deelvensters te definiëren. De beste praktijken rond thema&#39;s zijn als volgt:

* Gebruik de elementenbibliotheek voor een snelle toepassing van tekststijlen, achtergrond en afbeeldingen. Wanneer een stijl wordt toegevoegd aan de elementenbibliotheek, is deze beschikbaar voor andere thema&#39;s en in de stijlmodus van de formuliereditor.
* Algemene instellingen zoals lettertype en pagina-achtergrond toepassen met behulp van een kiezer op paginaniveau.
* Met clientbibliotheken kunt u bestaande of geavanceerde stijlen in uw thema&#39;s importeren.
* U kunt de opmaak overschrijven voor specifieke velden, deelvensters of knoppen in een formulierstijllaag.
* Als een thema niet aan uw opmaakvereisten voldoet, kunt u vooraf gedefinieerde klassen gebruiken, zoals guideFieldNode, guideFieldLabel, guideFieldWidget en guidePanelNode, om algemene stijl op formulieren toe te passen.

Zie [Thema&#39;s](/help/forms/using/themes.md) voor meer informatie.

### Prestaties van grote en complexe formulieren optimaliseren {#optimizing-performance-of-large-and-complex-forms}

Auteurs van formulieren en eindgebruikers van formulieren hebben doorgaans te maken met prestatieproblemen bij het laden van grote formulieren in de ontwerpmodus of bij uitvoering. Naarmate het aantal objecten (velden en deelvensters) in het formulier toeneemt, wordt het ontwerp en de runtime minder prettig. Het voorkomt ook dat meerdere auteurs tegelijkertijd samenwerken en een formulier ontwerpen.

Overweeg de volgende aanbevolen procedures om prestatieproblemen met grote formulieren te verhelpen:

* Aanbevolen wordt om adaptieve formulieren te maken met behulp van XSD-formuliergegevensmodel, zelfs als een XFA wordt geconverteerd naar een adaptief formulier, indien mogelijk.
* Neem alleen de velden en deelvensters op in adaptieve formulieren die informatie van de gebruiker vastleggen. Houd statische inhoud minimaal of gebruik URL&#39;s om deze in een apart venster te openen.
* Hoewel elk formulier is ontworpen voor een bepaald doel, zijn er in de meeste formulieren enkele gangbare segmenten. Bijvoorbeeld persoonlijke gegevens, adres, arbeidsgegevens enzovoort. Maak [adaptieve formulierfragmenten](/help/forms/using/adaptive-form-fragments.md) voor algemene formulierelementen en -secties en gebruik deze in alle formulieren. U kunt een deelvenster in een bestaand formulier ook opslaan als een fragment. Elke wijziging in een fragment wordt weerspiegeld in alle bijbehorende adaptieve formulieren. Het bevordert samenwerkingscreatie aangezien de veelvoudige auteurs aan verschillende fragmenten gelijktijdig kunnen werken die omhoog een vorm maken.

   * Net als adaptieve formulieren wordt aangeraden dat alle fragmentspecifieke opmaak en aangepaste scripts in de clientbibliotheek worden gedefinieerd met behulp van het dialoogvenster Fragmentcontainer. Probeer ook zelf-voldoende fragmenten te maken die niet afhankelijk zijn van objecten buiten de fragmenten.
   * Gebruik geen cross-fragments-scripts. Als er een object is buiten het fragment waarnaar u moet verwijzen, probeert u dat object te maken tot onderdeel van het bovenliggende formulier. Als het object zich nog steeds in een ander fragment moet bevinden, kunt u het met de naam ervan in het script raadplegen.

* Met Opslaan en hervatten met automatisch opslaan kunt u het aangepaste formulier periodiek opslaan en gebruikers in staat stellen later opnieuw te klikken om het formulier in te vullen.
* Configureer fragmenten die geleidelijk moeten worden geladen. Tijdens de runtime wordt een fragment dat is gemarkeerd om geladen, alleen gerenderd wanneer dit vereist is. Hierdoor wordt de laadtijd voor grote formulieren aanzienlijk verkort. Deze functie wordt ook ondersteund in fragmenten met herhaalbare deelvensters. Zie [Lazy loading](/help/forms/using/lazy-loading-adaptive-forms.md) configureren voor meer informatie.

   * Configureer lui laden niet op fragmenten in een responsieve rasterlay-out of in het eerste deelvenster.
   * Componenten voor bestandsbijlagen en Algemene voorwaarden worden niet ondersteund in laaggeladen fragmenten.
   * Markeer een waarde in een lazy geladen paneel als Waarde globaal gebruiken als die waarde in een ander deel van het formulier wordt gebruikt zodat de waarde beschikbaar is voor gebruik wanneer het bevattende paneel wordt verwijderd.
   * U kunt zichtbaarheidsregels schrijven voor fragmenten die op basis van een voorwaarde moeten worden weergegeven of verborgen.

### Aangepaste formulieren {#prefilling-adaptive-forms} vooraf invullen

U kunt adaptieve formuliervelden vooraf invullen met gegevens die vanaf de achtergrond zijn opgehaald, zodat gebruikers het formulier snel kunnen invullen en typfouten kunnen voorkomen.

* AEM Forms biedt een vooraf ingevulde service voor het lezen van gegevens uit een vooraf gedefinieerd XML-gegevensbestand en het vooraf invullen van de velden van een adaptief formulier met de inhoud in het vooraf ingevulde XML-bestand.
* De XML van de vooraf ingevulde gegevens moet voldoen aan het schema van het formuliermodel dat is gekoppeld aan het adaptieve formulier.
* Neem `afBoundedData`- en `afUnBoundedData`-secties op in de vooraf ingevulde XML om zowel gebonden als niet-gebonden velden vooraf in een adaptief formulier in te vullen.

* Voor adaptieve formulieren die zijn gebaseerd op het formuliergegevensmodel, biedt AEM Forms een vooraf ingevulde service voor het formuliergegevensmodel. De Prefill-service zoekt naar gegevensbronnen voor gegevensmodelobjecten in het adaptieve formulier en vult de veldwaarden vooraf in bij het weergeven van het formulier.
* U kunt ook het bestand, de crx, de service of de http-protocollen gebruiken om adaptieve formulieren vooraf in te vullen.
* AEM Forms biedt ondersteuning voor aangepaste Prefill-services die u kunt insluiten als een OSGi-service om adaptieve formulieren vooraf in te vullen.

Zie [Aangepaste formuliervelden vooraf invullen](/help/forms/using/prepopulate-adaptive-form-fields.md) voor meer informatie.

### Aangepaste formulieren ondertekenen en verzenden {#signing-and-submitting-adaptive-forms}

Voor adaptieve formulieren zijn acties verzenden vereist om door de gebruiker opgegeven gegevens te verwerken. Een handeling Verzenden bepaalt de taak die wordt uitgevoerd voor de gegevens die u verzendt met behulp van een adaptief formulier.

* Er zijn verschillende verzendacties beschikbaar in adaptieve formulieren. Zie [De handeling Verzenden configureren](/help/forms/using/configuring-submit-actions.md) voor meer informatie.
* U kunt een aangepaste verzendactie schrijven als de standaardverzendacties niet voldoen aan uw gebruiksscenario. Zie [Aangepaste handeling Verzenden schrijven voor adaptieve formulieren](/help/forms/using/custom-submit-action-form.md) voor meer informatie.
* Voeg validaties aan de serverzijde toe om te voorkomen dat er ongeldige gegevens worden verzonden.

U kunt de multi-sign ervaring van Adobe Sign in adaptieve vormen gebruiken. Houd rekening met het volgende wanneer u Adobe Sign in adaptieve formulieren configureert. Zie [Adobe Sign gebruiken in een adaptieve vorm](/help/forms/using/working-with-adobe-sign.md) voor meer informatie.

* Het adaptieve formulier dat geschikt is voor Adobe Sign, wordt alleen verzonden nadat alle ondertekenaars het formulier hebben ondertekend. Forms wordt weergegeven in de status In afwachting van ondertekening totdat het formulier door alle ondertekenaars is ondertekend.
* U kunt ondertekeningservaring in formulieren configureren of ondertekenaars omleiden naar een ondertekeningspagina bij verzending.
* Configureer sequentiële of parallelle ondertekeningservaring, indien van toepassing.

### Document met record {#generating-document-of-record} genereren

Een recorddocument (DoR) is een afgevlakte PDF-versie van een adaptief formulier dat u kunt afdrukken, ondertekenen of archiveren.

* Afhankelijk van het formuliergegevensmodel waarop een adaptief formulier is gebaseerd, kunt u als volgt een sjabloon configureren voor DoR:

   * **XFA-formuliersjabloon**: Gebruik het bijbehorende XDP-bestand als de DoR-sjabloon.
   * **XSD-schema**: Gebruik de bijbehorende XFA-sjabloon die hetzelfde XML-schema gebruikt als het adaptieve formulier.
   * **Geen**: Gebruik automatisch gegenereerde doR.

* Configureer kop-, voettekst-, afbeeldingen, kleur-, lettertype- en dergelijke rechts op het tabblad Document of Record van de adaptieve formuliereditor.
* Gebruik `DoRService` om DoR programmatically te produceren.
* Verborgen velden uitsluiten van de DoR.
* Gebruik `afAcceptLang` verzoekparameter om DoR in een andere scène te bekijken.

### Fouten opsporen en adaptieve formulieren testen {#debugging-and-testing-adaptive-forms}

[AEM Chrome Plug-](https://adobe-consulting-services.github.io/acs-aem-tools/aem-chrome-plugin/) inis een browserextensie voor Google Chrome met hulpprogramma&#39;s voor foutopsporing in adaptieve formulieren. Auteurs en ontwikkelaars van formulieren kunnen deze gereedschappen gebruiken:

* Problemen identificeren en de prestaties van het genereren van formulieren optimaliseren
* Fouten opsporen in trefwoorden en fouten met bindRef in het formulier
* Logbestanden inschakelen en configureren
* Fouten opsporen in regels en scripts in het formulier
* Meer informatie over guideBridge-API&#39;s

Zie [AEM Chrome-plug-in - Adaptief formulier](https://adobe-consulting-services.github.io/acs-aem-tools/aem-chrome-plugin/adaptive-form/) voor meer informatie.

Calvin SDK is een hulpprogramma-API waarmee Adaptive Forms-ontwikkelaars Adaptive Forms kunnen testen. Calvin SDK is gebaseerd op het [Hobbes.js-testframework](https://docs.adobe.com/docs/en/aem/6-3/develop/ref/test-api/index.html). U kunt het framework gebruiken om het volgende te testen:

* Uitvoering van een adaptief formulier
* Vooraf ingevuld met een adaptief formulier
* Ervaring met een adaptief formulier verzenden
* Expressieregels
* Validaties
* Lazy Loading

Zie [Testen van adaptieve formulieren automatiseren](/help/forms/using/calvin.md) voor meer informatie.

### Aangepaste formulieren op AEM server {#validating-adaptive-forms-on-aem-server} valideren

Validaties aan de serverzijde zijn vereist om te voorkomen dat er pogingen worden ondernomen om validaties op de client te omzeilen en dat er een mogelijk compromis ontstaat tussen gegevensverzending en overtredingen van de bedrijfsregels. Servervalidaties worden op de server uitgevoerd door de vereiste clientbibliotheek te laden.

* Neem functies op in een clientbibliotheek voor het valideren van expressies in adaptieve formulieren en geef de clientbibliotheek op in het dialoogvenster Container voor adaptieve formulieren. Zie [Herhaling aan de serverzijde](/help/forms/using/configuring-submit-actions.md#p-server-side-revalidation-in-adaptive-form-p) voor meer informatie.
* Servervalidatie valideert het formuliermodel. Het wordt aanbevolen een aparte clientbibliotheek voor validaties te maken en deze niet te mengen met andere elementen, zoals HTML-opmaak en DOM-manipulatie, in dezelfde clientbibliotheek.

### Aangepaste formulieren {#localizing-adaptive-forms} lokaliseren

AEM biedt vertaalworkflows waarmee u adaptieve formulieren kunt lokaliseren. Zie [AEM vertaalworkflow gebruiken om adaptieve formulieren te lokaliseren](/help/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.md) voor meer informatie.

U kunt het beste adaptieve formulieren als volgt lokaliseren:

* Gebruik adaptieve formulierfragmenten voor gemeenschappelijke elementen in verschillende formulieren en lokaliseer fragmenten. Zo weet u zeker dat u een fragment één keer lokaliseert en het geeft in alle formulieren weer waar het gelokaliseerde fragment wordt gebruikt.
* Wijzigingen zoals het toevoegen van een nieuwe component of het toepassen van een script in een gelokaliseerd formulier, worden niet automatisch gelokaliseerd. Daarom moet u een formulier invullen voordat u het lokaliseert om meerdere lokalisatiecycli te voorkomen.
* Gebruik `afAcceptLang`-aanvraagparameter om de landinstelling van de browser te overschrijven en het formulier in de opgegeven landinstelling te genereren. Met de volgende URL wordt het formulier bijvoorbeeld geforceerd weergegeven in de Japanse landinstelling, ongeacht de landinstelling die in de browser is opgegeven:

   `https://'[server]:[port]'/<contextPath>/<formFolder>/<formName>.html?wcmmode=disabled&afAcceptLang=ja`

* AEM Forms ondersteunt momenteel de lokalisatie van adaptieve formulieren met inhoud in het Engels (en), Spaans (es), Frans (fr), Italiaans (it), Duits (de), Japans (ja), Portugees-Braziliaans (pt-BR), Chinees (zh-CN), Chinees-Taiwan (zh-TW) en Koreaans (ko-KR). U kunt echter tijdens runtime ondersteuning toevoegen voor nieuwe landinstellingen voor adaptieve formulieren. Zie [Ondersteuning van nieuwe landinstellingen voor lokalisatie van adaptieve formulieren](/help/forms/using/supporting-new-language-localization.md) voor meer informatie.

## Formulierproject voorbereiden voor productie {#prepare-forms-project-for-production}

### Procesverwerkingsserver {#adding-forms-processing-server} toevoegen

U kunt een extra instantie van de server van AEM Forms vormen die achter de firewall in een beveiligde streek verblijft. U kunt deze instantie gebruiken voor:

* **Batchverwerking**: taken die terugkerend of gepland zijn in batches met een zware belasting. U kunt bijvoorbeeld instructies afdrukken, correspondentie genereren en documentservices gebruiken, zoals PDF Generator, Output en Assembler.
* **PII-gegevens** opslaan: PII-gegevens opslaan op de verwerkingsserver. Dit is niet verplicht als u al een aangepaste opslagprovider gebruikt voor het opslaan van PII-gegevens.

### Project verplaatsen naar een andere omgeving {#moving-project-to-another-environment}

U moet vaak uw AEM projecten van één milieu naar een andere verplaatsen. Enkele belangrijke dingen die u moet onthouden tijdens het verplaatsen zijn:

* Maak een back-up van uw bestaande clientbibliotheken, aangepaste code en configuraties.
* Implementeer productpakketten en patches handmatig en in de opgegeven volgorde in de nieuwe omgeving.
* Implementeer projectspecifieke codepakketten en -bundels handmatig en als een afzonderlijk pakket of bundel op de nieuwe AEM.
* (*AEM Forms alleen op JEE*) Implementeer LCA&#39;s en DSC&#39;s handmatig op de server van de Forms Workflow.
* Gebruik [Export-Import](/help/forms/using/import-export-forms-templates.md)-functionaliteit om elementen naar de nieuwe omgeving te verplaatsen. U kunt de replicatieagent ook vormen en de activa publiceren.
* Wanneer u een upgrade uitvoert, vervangt u alle verouderde API&#39;s en functies door nieuwe API&#39;s en functies.

### AEM {#configuring-aem} configureren

Sommige beste praktijken om AEM te vormen om de algemene prestaties te verbeteren zijn als volgt:

* Compressie van HTML-clientbibliotheek voor JavaScript en CSS vanuit Felix Console inschakelen. Zie [Clientlibs uitgelegd door voorbeeld](https://blogs.adobe.com/experiencedelivers/experience-management/clientlibs-explained-example/).
* Plaats alle clientbibliotheken in `/etc.clientlibs/fd` en eventuele extra aangepaste clientbibliotheken in AEM dispatcher om de reactiesnelheid en beveiliging van uw gepubliceerde formulieren te verbeteren. Zie [Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html) voor meer informatie.

* Plaats geen `/content/forms/af/`- en `/content/dam/formsanddocuments/*`-paden in de cache. Zie [Aangepaste formulieren in cache plaatsen](/help/forms/using/configure-adaptive-forms-cache.md) voor gedetailleerde informatie over het configureren van adaptieve formulieren in cache.

* Schakel HTML in via de compressiemodule van de webserver. Zie [Prestaties afstemmen van AEM Forms-server](/help/forms/using/performance-tuning-aem-forms.md) voor meer informatie.
* Verhoog de aanroepen per aanvraagconfiguratie voor grote formulieren. Zie [Prestaties van grote en complexe formulieren optimaliseren](/help/forms/using/adaptive-forms-best-practices.md#optimizing-performance-of-large-and-complex-forms).
* Maak [aangepaste foutpagina&#39;s die worden weergegeven door fouthandler](https://helpx.adobe.com/experience-manager/6-2/sites-developing/customizing-errorhandler-pages.html).
* Beveiligde AEM Forms-server.

   * Gebruik de uitvoermodus `nosamplecontent` om ervoor te zorgen dat er geen voorbeeldinhoud is en dat voorbeeldgebruikers op de productieserver zijn geïmplementeerd. Zie [AEM uitvoeren in productieklaar](/help/sites-administering/production-ready.md).

* Houd de heapgrootte tot minimaal 8 GB. Zie [Prestaties van de AEM Forms-server afstemmen](/help/forms/using/performance-tuning-aem-forms.md) voor andere instellingen.
* Gebruik gebruikerssessies voor services in plaats van beheersessies voor het uitvoeren van taken op serviceniveau. Zie [Serviceverificatie](https://sling.apache.org/documentation/the-sling-engine/service-authentication.html) voor meer informatie.

>[!VIDEO](https://vimeo.com/)

### Externe opslag configureren voor concepten en verzonden formuliergegevens {#external-storage}

In een productieomgeving wordt aanbevolen de ingediende formuliergegevens niet in AEM opslagplaats op te slaan. Bij de standaardimplementatie van de acties Forms Portal Store, Store Content en Store PDF verzenden worden formuliergegevens opgeslagen in AEM opslagplaats. Deze indieningsacties zijn alleen bedoeld voor demonstratiedoeleinden. Bovendien maken de functies Opslaan, Hervatten en Automatisch opslaan standaard gebruik van poortopslag. Overweeg daarom de volgende aanbevelingen:

* **Conceptgegevens** opslaan: Als u de functie Concept van adaptieve formulieren gebruikt, moet u een aangepaste Service Provider Interface (SPI) implementeren om conceptgegevens op te slaan in een veiligere opslag, zoals een database. Zie [Voorbeeld voor het integreren van concepten en verzendingscomponenten met database](/help/forms/using/integrate-draft-submission-database.md) voor meer informatie.

* **Verzendgegevens** opslaan: Als u de Opslag van de Verzending van het Portaal van de Vorm gebruikt, zou u een douaneSPI moeten uitvoeren om voorleggingsgegevens in een gegevensbestand op te slaan. Zie [Voorbeeld voor het integreren van concepten en verzendingscomponenten met database](/help/forms/using/integrate-draft-submission-database.md) voor een voorbeeldintegratie.

   U kunt ook een aangepaste verzendactie schrijven waarmee formuliergegevens en bijlagen worden opgeslagen in een beveiligde opslagruimte. Zie [Aangepaste handeling Verzenden schrijven voor adaptieve formulieren](/help/forms/using/custom-submit-action-form.md) voor meer informatie.

* **Lengte van concept-id**: Wanneer u een adaptief formulier opslaat als concept, wordt een concept-id gegenereerd om het concept op unieke wijze te identificeren. De minimumwaarde voor de lengte van het veld concept-id is 26 tekens. Adobe raadt u aan de lengte van de concept-id in te stellen op 26 of meer tekens.

### Persoonlijke identificeerbare informatie {#handling-personally-identifiable-information} verwerken

Een van de belangrijkste uitdagingen voor organisaties is hoe te om persoonlijk identificeerbare (PII) gegevens te behandelen. Hier volgt een aantal aanbevolen procedures voor het verwerken van dergelijke gegevens:

* Gebruik een beveiligde externe opslagruimte, zoals een database, om gegevens op te slaan uit concepten en verzonden formulieren. Zie [Externe opslag configureren voor concepten en verzonden formuliergegevens](/help/forms/using/adaptive-forms-best-practices.md#external-storage).
* Met de component Voorwaarden en Voorwaarden van het gebruik kunt u expliciete toestemming van de gebruiker nemen voordat u het automatisch opslaan inschakelt. In dit geval schakelt u automatisch opslaan alleen in als de gebruiker akkoord gaat met de voorwaarden in de component Voorwaarden.

