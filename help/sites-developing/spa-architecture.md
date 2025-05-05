---
title: SPA ontwikkelen voor Adobe Experience Manager
description: Dit artikel stelt belangrijke vragen om te overwegen wanneer het in dienst nemen van een front-end ontwikkelaar om een SPA voor Adobe Experience Manager (AEM) te ontwikkelen en geeft een overzicht van de architectuur van AEM betreffende SPA om in mening te houden wanneer het opstellen van een ontwikkelde SPA op AEM.
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: spa
content-type: reference
docset: aem65
exl-id: c1429889-e2ed-4e2f-a45f-33f8a6a52745
solution: Experience Manager, Experience Manager Sites
feature: Developing,SPA Editor
role: Developer
source-git-commit: 6d961456e0e1f7a26121da9be493308a62c53e04
workflow-type: tm+mt
source-wordcount: '2018'
ht-degree: 0%

---


# SPA ontwikkelen voor AEM{#developing-spas-for-aem}

Toepassingen op één pagina (SPA) kunnen aantrekkelijke ervaringen bieden voor websitegebruikers. Ontwikkelaars willen sites kunnen maken met behulp van SPA frameworks en auteurs willen inhoud binnen Adobe Experience Manager (AEM) naadloos bewerken voor een site die is gebouwd met behulp van dergelijke frameworks.

Dit artikel stelt belangrijke vragen om te overwegen wanneer het in dienst nemen van een front-end ontwikkelaar om een SPA voor AEM te ontwikkelen en geeft een overzicht van de architectuur van AEM betreffende het opstellen van SPA op AEM.

{{ue-over-spa}}

## SPA ontwikkelingsbeginselen voor AEM {#spa-development-principles-for-aem}

Bij het ontwikkelen van toepassingen voor één pagina op AEM wordt ervan uitgegaan dat de ontwikkelaar aan de voorzijde de aanbevolen standaardprocedures voor het maken van een SPA in acht neemt. Als als front-end ontwikkelaar u deze algemene beste praktijken en een paar AEM-specifieke principes volgt, zal uw SPA met [ AEM en zijn inhoud-creatie mogelijkheden ](/help/sites-developing/spa-walkthrough.md#content-editing-experience-with-spa) functioneel zijn.

* **[Portability ](/help/sites-developing/spa-architecture.md#portability) -** zoals met om het even welke componenten, zouden de componenten moeten worden gebouwd om zo draagbaar mogelijk te zijn. De SPA moet met draagbare en herbruikbare onderdelen worden gebouwd.
* **[AEM de Structuur van de Plaats van de Stations](/help/sites-developing/spa-architecture.md#aem-drives-site-structure)** - de front-end ontwikkelaar leidt tot componenten en bezit hun interne structuur, maar baseert zich op AEM om de inhoudsstructuur van de plaats te bepalen.
* **[Dynamische Rendering](/help/sites-developing/spa-architecture.md#dynamic-rendering)** - allen zou het teruggeven dynamisch moeten zijn.
* **[Dynamisch Verpletterend ](#dynamic-routing) -** de SPA is verantwoordelijk voor het verpletteren en AEM luistert aan het en haalt die op het wordt gebaseerd. Om het even welk verpletteren zou ook dynamisch moeten zijn.

Als u deze principes in gedachten houdt bij het ontwikkelen van uw SPA, is deze zo flexibel en mogelijk in de toekomst, waarbij alle ondersteunde AEM ontwerpfuncties worden ingeschakeld.

Als u niet AEM auteurseigenschappen moet steunen, kunt u een verschillend [ SPA ontwerpmodel ](/help/sites-developing/spa-architecture.md#spa-design-models) moeten overwegen.

### Overdraagbaarheid {#portability}

Zoals bij het ontwikkelen van om het even welke component, zouden uw componenten op een zodanige manier moeten worden ontworpen dat hun draagbaarheid wordt gemaximaliseerd. Patronen die de draagbaarheid of herbruikbaarheid van de onderdelen in de weg staan, moeten worden vermeden om ervoor te zorgen dat de onderdelen compatibel, flexibel en duurzaam zijn.

De resulterende SPA moet worden gebouwd met zeer draagbare en herbruikbare onderdelen.

### Sitestructuur AEM stations {#aem-drives-site-structure}

De front-end ontwikkelaar moet zichzelf zien als verantwoordelijk voor het maken van een bibliotheek met SPA componenten die worden gebruikt om de app te maken. De front-end ontwikkelaar heeft volledige controle over de interne structuur van de componenten. [ Nochtans, AEM, altijd, bezit de structuur van de plaats.](/help/sites-developing/spa-overview.md)

Dit betekent dat de front-end ontwikkelaar klanteninhoud vóór of na het ingangspunt van de componenten kan toevoegen en derde vraag binnen de component kan ook maken. De front-end ontwikkelaar heeft echter geen volledige controle over hoe de componenten bijvoorbeeld nesten.

### Dynamische rendering {#dynamic-rendering}

De SPA mag alleen vertrouwen op dynamische rendering van inhoud. Dit is de standaardverwachting waarbij AEM alle onderliggende elementen van de inhoudsstructuur ophaalt en rendert.

Elke expliciete rendering die naar specifieke inhoud verwijst, wordt als statische rendering beschouwd en wordt wel ondersteund, maar is niet compatibel met AEM ontwerpfuncties voor inhoud. Dit gaat ook tegen het beginsel van [ portability ](/help/sites-developing/spa-architecture.md#portability).

### Dynamische routering {#dynamic-routing}

Zoals met het teruggeven, zou al het verpletteren ook dynamisch moeten zijn. In AEM, [ zou de SPA altijd het verpletteren ](/help/sites-developing/spa-routing.md) moeten bezitten en AEM luistert aan het en haalt inhoud die op het wordt gebaseerd.

Om het even welk statisch verpletterend werk tegen het [ beginsel van portability ](/help/sites-developing/spa-architecture.md#portability) en beperkt de auteur door niet compatibel met inhoud te zijn creërend eigenschappen van AEM. Bijvoorbeeld, met het statische verpletteren, als de inhoudsauteur een route wil veranderen of een pagina veranderen, zou de auteur de front-end ontwikkelaar moeten vragen om het te doen.

## Projectarchetype AEM {#aem-project-archetype}

Om het even welk AEM project zou [ AEM Archetype van het Project ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=nl-NL) moeten gebruiken, dat SPA projecten gebruikend React of Angular steunt en SPA SDK gebruikt.

## SPA ontwerpmodellen {#spa-design-models}

Als de [ principes van het ontwikkelen van SPA in AEM ](/help/sites-developing/spa-architecture.md#spa-development-principles-for-aem) worden gevolgd, dan zal uw SPA met alle gesteunde AEM tevreden auteurseigenschappen functioneel zijn.

Er kunnen zich echter gevallen voordoen waarin dit niet volledig noodzakelijk is. In de volgende tabel vindt u een overzicht van de verschillende ontwerpmodellen, hun voordelen en hun nadelen.

<table>
 <tbody>
  <tr>
   <th><strong>Ontwerpmodel<br /> </strong></th>
   <th><strong>Voordelen</strong></th>
   <th><strong>Nadelen</strong></th>
  </tr>
  <tr>
   <td>AEM wordt gebruikt als headless CMS zonder het <a href="/help/sites-developing/spa-reference-materials.md"> SPA kader van SDK van de Redacteur te gebruiken.</a></td>
   <td>De front-end ontwikkelaar heeft volledige controle over de app.</td>
   <td><p>Inhoudsauteurs kunnen geen AEM gebruiken voor het schrijven van inhoud.</p> <p>De code is niet draagbaar of herbruikbaar als het statische verwijzingen of het verpletteren bevat.</p> <p>Hiermee wordt het gebruik van de sjablooneditor niet toegestaan, zodat de ontwikkelaar aan de voorzijde bewerkbare sjablonen moet bijhouden via het JCR.</p> </td>
  </tr>
  <tr>
   <td>De front-end ontwikkelaar gebruikt het kader van SPA Editor SDK maar opent slechts enkele gebieden voor de auteur van de inhoud.</td>
   <td>De ontwikkelaar behoudt de controle over de app door alleen authoring in beperkte delen van de app in te schakelen.</td>
   <td><p>Inhoudsauteurs hebben slechts een beperkte AEM ervaring bij het schrijven van inhoud.</p> <p>De code riskeert noch draagbaar noch herbruikbaar als het statische verwijzingen of het verpletteren bevat.</p> <p>Hiermee wordt het gebruik van de sjablooneditor niet toegestaan, zodat de ontwikkelaar aan de voorzijde bewerkbare sjablonen via het JCR moet onderhouden.</p> </td>
  </tr>
  <tr>
   <td>Het project gebruikt volledig de SPA Redacteur SDK en de frontend componenten worden ontwikkeld als bibliotheek en de inhoudsstructuur van app wordt gedelegeerd aan AEM.</td>
   <td><p>De app is herbruikbaar en draagbaar.</p> <p>De auteur van de inhoud kan de app bewerken via AEM ontwerpervaring voor inhoud.<br /> </p> <p>De SPA is compatibel met de sjablooneditor.</p> </td>
   <td><p>De ontwikkelaar heeft geen controle over de structuur van de app en het gedeelte van de inhoud dat aan AEM is gedelegeerd.</p> <p>De ontwikkelaar kan gedeelten van de app nog steeds reserveren voor de inhoud die niet is bedoeld om te worden gemaakt met AEM.</p> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Hoewel alle modellen in AEM worden gesteund, slechts door de derde (en daarom na de geadviseerde [ SPA ontwikkelingsbeginselen in AEM ](/help/sites-developing/spa-architecture.md#spa-development-principles-for-aem)) uit te voeren kunnen inhoudauteurs met de inhoud van de SPA in AEM in wisselwerking staan en uitgeven aangezien zij gewend zijn.

## Bestaande SPA migreren naar AEM {#migrating-existing-spas-to-aem}

Over het algemeen als uw SPA de [ SPA Beginselen van de Ontwikkeling voor AEM ](/help/sites-developing/spa-architecture.md#spa-development-principles-for-aem) volgt, dan zal uw SPA in AEM werken en editable zijn gebruikend de AEM Redacteur SPA.

Ga als volgt te werk om uw bestaande SPA klaar te maken voor AEM.

1. **maak uw componenten JS modulair.**

   Zorg ervoor dat ze in elke volgorde, positie en grootte kunnen worden gerenderd.
1. **gebruik de containers die door SDK van de Adobe worden verstrekt om uw componenten op het scherm te plaatsen.**

   AEM biedt een pagina- en alineasysteem voor gebruik.
1. **creeer een AEM component voor elke component JS.**

   De AEM componenten bepalen de dialoog en output JSON.

## Instructies voor front-end ontwikkelaars {#instructions-for-front-end-developers}

De belangrijkste taak bij het in dienst nemen van een front-end ontwikkelaar om een SPA voor AEM tot stand te brengen is akkoord te gaan over de componenten en hun modellen JSON.

Hieronder volgt een overzicht van de stappen die een front-end ontwikkelaar moet volgen bij het ontwikkelen van een SPA voor AEM.

1. **ga op componenten en hun JSON model** akkoord

   Voor-eind ontwikkelaars en achterste-AEM ontwikkelaars moeten het eens zijn over welke componenten noodzakelijk en een model zodat is er één-op-één gelijke van SPA componenten aan de achterste-eindcomponenten.

   AEM componenten zijn nog steeds nodig, vooral om te zorgen voor bewerkingsdialoogvensters en om het componentmodel te exporteren.

1. **In React componenten, toegang het model via`this.props.cqModel`**

   Zodra componenten zijn overeengekomen en het JSON-model is geïmplementeerd, kan de front-end ontwikkelaar de SPA vrij ontwikkelen en eenvoudig toegang krijgen tot het JSON-model via `this.props.cqModel` .

1. `render()` methode van de component van 0&rbrace; uitvoeren **&#x200B;**

   De front-end ontwikkelaar implementeert de `render()` -methode naar eigen inzicht en kan de velden van de `cqModel` -eigenschap gebruiken. Hiermee worden het DOM en de HTML-fragmenten uitgevoerd die in de pagina worden ingevoegd. Dit is de standaardmanier om een app te maken in React.

1. **Kaart de component aan het AEM middeltype via`MapTo()`**

   In de toewijzing worden componentklassen opgeslagen en intern door de opgegeven `Container` -component gebruikt om componenten op basis van het opgegeven brontype op te halen en dynamisch te instantiëren.

   Dit dient als de &quot;lijm&quot;tussen voorkant en achtereind zodat weet de redacteur aan welke componenten de reactiecomponenten beantwoorden.

   De `Page` en `ResponsiveGrid` zijn goede voorbeelden van klassen die de basis uitbreiden `Container` .

1. **Bepaal de component `EditConfig` als parameter aan`MapTo()`**

   Deze parameter is noodzakelijk om de redacteur te vertellen hoe de component zou moeten worden genoemd zolang bij nog niet wordt teruggegeven of geen inhoud heeft om terug te geven.

1. **breid de verstrekte `Container` klasse voor pagina&#39;s en containers** uit

   Pagina- en alineasystemen moeten deze klasse uitbreiden, zodat delegatie naar binnencomponenten naar behoren werkt.

1. **voer een verpletterende oplossing uit die HTML5 `History` API gebruikt.**

   Wanneer de functie `ModelRouter` is ingeschakeld, wordt door het aanroepen van de functies `pushState` en `replaceState` een verzoek aan de `PageModelManager` verzonden om een ontbrekend fragment van het model op te halen.

   De huidige versie van de `ModelRouter` ondersteunt alleen het gebruik van URL&#39;s die verwijzen naar het feitelijke bronnenpad van de entry-punten Sling Model. Het ondersteunt het gebruik van vanity-URL&#39;s of aliassen niet.

   `ModelRouter` kan worden onbruikbaar gemaakt of worden gevormd om een lijst van regelmatige uitdrukkingen te negeren.

## AEM-agnost {#aem-agnostic}

Deze codeblokken illustreren hoe uw React en Angular componenten niets nodig hebben dat Adobe of AEM specifiek is.

* Alles wat zich in de JavaScript-component bevindt, is AEM-agnostisch.
* Nochtans, wat voor AEM specifiek is is dat de component JS aan een AEM component met de hulp moet worden in kaart gebracht MapTo.

![ screen_shot_2018-12-11at144019 ](assets/screen_shot_2018-12-11at144019.png)

De `MapTo` helper is de &quot;lijm&quot;die de achterkant en de voorste componenten om samen toelaat worden aangepast:

* Het vertelt de container JS (of JS paragraafsysteem) welke component JS voor het teruggeven van elk van de componenten verantwoordelijk is die in JSON aanwezig zijn.
* Er wordt een HTML-gegevenskenmerk toegevoegd aan de HTML die de JS-component rendert, zodat de SPA Editor weet welk dialoogvenster aan de auteur moet worden weergegeven wanneer de component wordt bewerkt.

Zie de handleiding Aan de slag voor het door u gekozen framework voor meer informatie over het gebruik van `MapTo` en het samenstellen van SPA voor AEM in het algemeen.

* [Aan de slag met SPA in AEM - Reageren](/help/sites-developing/spa-getting-started-react.md)
* [Aan de slag met SPA in AEM - Angular](/help/sites-developing/spa-getting-started-angular.md)

## AEM Architectuur en SPA {#aem-architecture-and-spas}

De algemene architectuur van AEM, inclusief ontwikkelings-, auteurs- en publicatieomgevingen, verandert niet wanneer u SPA gebruikt. Het is echter nuttig te begrijpen hoe SPA ontwikkeling in deze architectuur past.

![ screen_shot_2018-12-11at145348 ](assets/screen_shot_2018-12-11at145348.png)

* **bouwt Milieu**

  Dit is waar de bron voor de SPA toepassingsbron en componentenbron wordt uitgecheckt.

   * De NPM clientlib generator leidt tot een cliëntbibliotheek van het SPA project.
   * Deze bibliotheek is afkomstig van Maven en wordt samen met de component geïmplementeerd door de plug-in Maven Build bij de AEM Auteur.

* **AEM Auteur**

  Inhoud wordt gemaakt op de AEM auteur, inclusief SPA.

  Wanneer een SPA wordt bewerkt met de SPA Editor in de ontwerpomgeving:

   1. De SPA vraagt om de buitenste HTML.
   1. De CSS is geladen.
   1. De JavaScript van de SPA toepassing wordt geladen.
   1. Wanneer de SPA toepassing wordt uitgevoerd, wordt de JSON opgevraagd, zodat de app het DOM van de pagina kan maken met de kenmerken `cq-data` .
   1. Met deze `cq-data` -kenmerken kan de editor aanvullende pagina-informatie laden, zodat deze weet welke bewerkingsconfiguraties beschikbaar zijn voor de componenten.

* **AEM Publish**

  Dit is waar de authored inhoud en de gecompileerde bibliotheken met inbegrip van SPA toepassingsartefacten, clientlibs, en componenten voor openbare consumptie worden gepubliceerd.

* **Dispatcher / CDN**

  De Dispatcher fungeert als de cachelaag van AEM voor bezoekers van de site.

   * Verzoeken worden op dezelfde manier verwerkt als AEM auteur, maar er is geen verzoek om paginagegevens, omdat dit alleen nodig is voor de editor.
   * JavaScript, CSS, JSON en HTML worden in cache geplaatst, waardoor de pagina wordt geoptimaliseerd voor snelle levering.

>[!NOTE]
>
>Binnen AEM is het niet nodig JavaScript-constructiemechanismen uit te voeren of de JavaScript zelf uit te voeren. AEM alleen de gecompileerde artefacten van de SPA toepassing.

## Volgende stappen {#next-steps}

Voor een overzicht van hoe een eenvoudige SPA in AEM gestructureerd is en hoe het werkt, zie de begonnen gids voor zowel [ Reageren ](/help/sites-developing/spa-getting-started-react.md) als [ Angular ](/help/sites-developing/spa-getting-started-angular.md).

Voor een geleidelijke gids aan het creëren van uw eigen SPA, zie [ Begonnen het worden met de AEM SPA Redacteur - het Leerprogramma van de Gebeurtenissen van WKND ](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-spa-wknd-tutorial-develop.html).

Voor verdere details over het dynamische model aan componentenafbeelding en hoe het binnen SPA in AEM werkt, zie het artikel [ Dynamisch Model aan de Afbeelding van de Component voor SPA ](/help/sites-developing/spa-dynamic-model-to-component-mapping.md).

Als u wenst om SPA in AEM voor een kader buiten React of Angular uit te voeren of eenvoudig een diepe duik in te nemen hoe SPA SDK voor AEM werkt, zie het [ SPA 1&rbrace; artikel van de Vervaging.](/help/sites-developing/spa-blueprint.md)
