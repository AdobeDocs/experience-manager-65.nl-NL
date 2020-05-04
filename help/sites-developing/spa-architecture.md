---
title: SBZ's voor AEM ontwikkelen
seo-title: SBZ's voor AEM ontwikkelen
description: Dit artikel stelt belangrijke vragen om te overwegen wanneer het in dienst nemen van een front-end ontwikkelaar om een KUUROORD voor AEM te ontwikkelen evenals geeft een overzicht van de architectuur van AEM met betrekking tot SPAs om in mening te houden wanneer het opstellen van een ontwikkelde KUUROORD op AEM.
seo-description: Dit artikel stelt belangrijke vragen om te overwegen wanneer het in dienst nemen van een front-end ontwikkelaar om een KUUROORD voor AEM te ontwikkelen evenals geeft een overzicht van de architectuur van AEM met betrekking tot SPAs om in mening te houden wanneer het opstellen van een ontwikkelde KUUROORD op AEM.
uuid: 6673a041-c557-4968-ae54-4cd5b9f56251
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: spa
content-type: reference
discoiquuid: 9584392a-d8a3-45a4-9cdf-fd211c8e6091
docset: aem65
translation-type: tm+mt
source-git-commit: 590dc4464182d4baf8293e7bb0774ce92971c0af

---


# SBZ&#39;s voor AEM ontwikkelen{#developing-spas-for-aem}

Toepassingen van één pagina (SPAs) kunnen dwingende ervaringen voor websitegebruikers aanbieden. De ontwikkelaars willen plaatsen kunnen bouwen gebruikend het kader van het KUUROORD en de auteurs willen inhoud binnen AEM voor een plaats foutloos uitgeven die gebruikend dergelijke kaders wordt gebouwd.

Dit artikel stelt belangrijke vragen om te overwegen wanneer het in dienst nemen van een front-end ontwikkelaar om een SPA voor AEM te ontwikkelen en geeft een overzicht van de architectuur van AEM met betrekking tot het opstellen van SPAs op AEM.

>[!NOTE]
>
>De redacteur van het KUUROORD is de geadviseerde oplossing voor projecten die het kader van het KUUROORD gebaseerde cliënt-kant teruggeven (b.v. Reageren of Hoekig) vereisen.

## SBO-ontwikkelingsbeginselen voor AEM {#spa-development-principles-for-aem}

Het ontwikkelen van enige paginatoepassingen op AEM veronderstelt dat de front-end ontwikkelaar standaardbeste praktijken wanneer het creëren van een KUUROORD waarneemt. Als als front-end ontwikkelaar u deze algemene beste praktijken evenals weinig AEM-specifieke principes volgt, zal uw SPA functioneel met [AEM en zijn inhoud-creatie mogelijkheden](/help/sites-developing/spa-walkthrough.md#content-editing-experience-with-spa)zijn.

* **[Draagbaarheid](/help/sites-developing/spa-architecture.md#portability)-**Zoals bij alle onderdelen moeten de onderdelen zo draagbaar mogelijk zijn. Het KUUROORD zou met draaglijk en herbruikbare componenten moeten worden gebouwd.
* **[AEM Drives Site Structure](/help/sites-developing/spa-architecture.md#aem-drives-site-structure)**- De ontwikkelaar aan de voorzijde maakt onderdelen en bezit hun interne structuur, maar vertrouwt op AEM om de inhoudsstructuur van de site te definiëren.
* **[Dynamische rendering](/help/sites-developing/spa-architecture.md#dynamic-rendering)**- Alle rendering moet dynamisch zijn.
* **[Het dynamische Verpletteren](#dynamic-routing)**- het KUUUROORD is verantwoordelijk voor het verpletteren en AEM luistert aan het en haalt die op het wordt gebaseerd. Om het even welk verpletteren zou ook dynamisch moeten zijn.

Als u deze principes in mening houdt aangezien u uw SPA ontwikkelt, zal het zo flexibel en zo toekomstig bewijs mogelijk zijn terwijl het toelaten van alle gesteunde auteursfunctionaliteit AEM.

Als u niet AEM auteurseigenschappen te hoeven steunen, kunt u een verschillend het ontwerpmodel [van het](/help/sites-developing/spa-architecture.md#spa-design-models)SPA moeten overwegen.

### Overdraagbaarheid {#portability}

Zoals bij het ontwikkelen van om het even welke component, zouden uw componenten op een zodanige manier moeten worden ontworpen dat hun draagbaarheid wordt gemaximaliseerd. Patronen die de draagbaarheid of herbruikbaarheid van de onderdelen in de weg staan, moeten worden vermeden om ervoor te zorgen dat de onderdelen compatibel, flexibel en duurzaam zijn.

Het resulterende KUUROORD zou met hoogst draagbare en herbruikbare componenten moeten worden gebouwd.

### AEM Drives Site Structure {#aem-drives-site-structure}

De front-end ontwikkelaar moet zichzelf als verantwoordelijke voor het creëren van een bibliotheek van componenten van het KUUROORD zien die worden gebruikt om app te bouwen. De front-end ontwikkelaar heeft volledige controle over de interne structuur van de componenten. [AEM is echter altijd eigenaar van de structuur van de site.](/help/sites-developing/spa-overview.md)

Dit betekent dat de front-end ontwikkelaar klanteninhoud vóór of na het ingangspunt van de componenten kan toevoegen en derde vraag binnen de component kan ook maken. De front-end ontwikkelaar heeft echter geen volledige controle over hoe de componenten bijvoorbeeld nesten.

### Dynamische rendering {#dynamic-rendering}

Het SPA zou zich slechts op dynamische teruggeven van inhoud moeten baseren. Dit is de standaardverwachting waarbij AEM alle onderliggende elementen van de inhoudsstructuur ophaalt en rendert. [](/help/sites-developing/spa-architecture.md#portability)

Elke expliciete rendering die naar specifieke inhoud verwijst, wordt beschouwd als statische rendering, maar wordt wel ondersteund, is niet compatibel met de ontwerpfuncties voor inhoud van AEM. Dit druist ook in tegen het beginsel van [portabiliteit](/help/sites-developing/spa-architecture.md#portability).

### Dynamische routering {#dynamic-routing}

Zoals met het teruggeven, zou al het verpletteren ook dynamisch moeten zijn. In AEM, zou [het KUUROORD altijd het verpletteren](/help/sites-developing/spa-routing.md) moeten bezitten en AEM luistert aan het en haalt inhoud die op het wordt gebaseerd.

Om het even welke statische verpletterende werken tegen het [beginsel van portabiliteit](/help/sites-developing/spa-architecture.md#portability) en beperkt de auteur door niet compatibel te zijn met inhoud auteurseigenschappen van AEM. Bijvoorbeeld, met het statische verpletteren, als de inhoudsauteur een route zou willen veranderen of een pagina zou veranderen, zou hij of zij de front eindontwikkelaar moeten vragen om het te doen.

## AEM-projectarchetype {#aem-project-archetype}

Om het even welk project AEM zou hefboomwerking het Archetype [van het Project van](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/overview.html)AEM, dat de projecten van het KUUROORD gebruikend React of Hoekig steunt en hefboomwerkingen SDK van het KUUROORD.

## SPA-ontwerpmodellen {#spa-design-models}

Als de [principes van het ontwikkelen van SPAs in AEM](/help/sites-developing/spa-architecture.md#spa-development-principles-for-aem) worden gevolgd, dan zal uw SPA functioneel met alle gesteunde inhoud AEM auteurseigenschappen zijn. [](/help/sites-developing/spa-architecture.md#spa-development-principles-for-aem)

Er kunnen zich echter gevallen voordoen waarin dit niet volledig noodzakelijk is. In de volgende tabel vindt u een overzicht van de verschillende ontwerpmodellen, hun voordelen en hun nadelen.

<table>
 <tbody>
  <tr>
   <th><strong>Ontwerpmodel<br /> </strong></th>
   <th><strong>Voordelen</strong></th>
   <th><strong>Nadelen</strong></th>
  </tr>
  <tr>
   <td>AEM wordt gebruikt als koploze CMS zonder het kader van SDK van de Redacteur van het <a href="/help/sites-developing/spa-reference-materials.md">KUUROORD te gebruiken.</a></td>
   <td>De front-end ontwikkelaar heeft volledige controle over de app.</td>
   <td><p>Inhoudsauteurs kunnen geen gebruikmaken van de AEM-ervaring voor het schrijven van inhoud.</p> <p>De code is noch draagbaar noch herbruikbaar als het statische verwijzingen of het verpletteren bevat.</p> <p>Hiermee wordt het gebruik van de sjablooneditor niet toegestaan, zodat de ontwikkelaar van de front-end via het JCR bewerkbare sjablonen moet bijhouden.</p> </td>
  </tr>
  <tr>
   <td>De voorste eindontwikkelaar gebruikt het kader van SDK van de Redacteur van het KUUROORD maar opent slechts enkele gebieden aan de inhoudauteur.</td>
   <td>De ontwikkelaar behoudt de controle over de app door alleen authoring in beperkte delen van de app in te schakelen.</td>
   <td><p>Inhoudsauteurs zijn beperkt tot een beperkt aantal AEM-programma's voor het schrijven van inhoud.</p> <p>De code riskeert noch draagbaar noch herbruikbaar als het statische verwijzingen of het verpletteren bevat.</p> <p>Hiermee wordt het gebruik van de sjablooneditor niet toegestaan, zodat de ontwikkelaar van de front-end via het JCR bewerkbare sjablonen moet bijhouden.</p> </td>
  </tr>
  <tr>
   <td>Het project hefboomwerkingen volledig de Redacteur SDK van het KUUROORD en de frontend componenten worden ontwikkeld als bibliotheek en de inhoudsstructuur van app wordt gedelegeerd aan AEM.</td>
   <td><p>De app is herbruikbaar en draagbaar.</p> <p>De auteur van de inhoud kan de app bewerken met behulp van de AEM-ervaring voor het schrijven van inhoud.<br /> </p> <p>Het KUUROORD is compatibel met de malplaatjeredacteur.</p> </td>
   <td><p>De ontwikkelaar heeft geen controle over de structuur van de app en het gedeelte van de inhoud dat aan AEM is gedelegeerd.</p> <p>De ontwikkelaar kan gedeelten van de app nog steeds reserveren voor de inhoud die niet met AEM kan worden gemaakt.</p> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Hoewel alle modellen in AEM worden gesteund, slechts door de derde uit te voeren (en daardoor na de geadviseerde ontwikkelingsbeginselen van het [KUUROORD in AEM](/help/sites-developing/spa-architecture.md#spa-development-principles-for-aem)) zullen de inhoudsauteurs met de inhoud van het KUUROORD in AEM kunnen in wisselwerking staan en uitgeven aangezien zij gewend zijn.
>[](/help/sites-developing/spa-architecture.md#spa-development-principles-for-aem)

## Bestaande SPA&#39;s migreren naar AEM {#migrating-existing-spas-to-aem}

Over het algemeen als uw SPA de Beginselen van de Ontwikkeling van het [KUUROORD voor AEM](/help/sites-developing/spa-architecture.md#spa-development-principles-for-aem)volgt, dan zal uw KUUROORD in AEM werken en editable zijn gebruikend de Redacteur van het KUUROORD AEM.

Volg deze stappen om uw bestaande SPA klaar te krijgen om met AEM te werken.

1. **Maak uw componenten JS modulair.**

   Zorg ervoor dat ze in elke volgorde, positie en grootte kunnen worden gerenderd.
1. **Gebruik de containers die worden geleverd door de SDK om uw componenten op het scherm te plaatsen.**

   AEM biedt een pagina- en alineasysteem voor gebruik.
1. **Maak een AEM-component voor elke JS-component.**

   De AEM-componenten definiëren het dialoogvenster en de JSON-uitvoer.

## Instructies voor front-end ontwikkelaars {#instructions-for-front-end-developers}

De belangrijkste taak in het aanmoedigen van een front-end ontwikkelaar om een KUUROORD voor AEM tot stand te brengen is op de componenten en hun modellen JSON in te stemmen.

Het volgende is een overzicht van de stappen een front-end ontwikkelaar moet volgen wanneer het ontwikkelen van een KUUROORD voor AEM.

1. **Onderdelen en hun JSON-model overeenkomen**

   Voor-eind ontwikkelaars en de achterste ontwikkelaars van AEM moeten overeenkomen over welke componenten noodzakelijk zijn en een model zodat is er een één-op-één gelijke van de componenten van het KUUROORD aan de achterste eindcomponenten.

   AEM-componenten zijn nog steeds vooral nodig om bewerkingsdialoogvensters te bieden en het componentmodel te exporteren.

1. **In React componenten, heb toegang tot het model via`this.props.cqModel`**

   Zodra de componenten worden overeengekomen en het model JSON op zijn plaats is, is de front-end ontwikkelaar vrij om het KUUROORD te ontwikkelen en kan eenvoudig tot het model toegang hebben JSON via `this.props.cqModel`.

1. **De`render()`methode van de component implementeren**

   De front-end ontwikkelaar implementeert de `render()` methode zoals hij/zij dat geschikt acht en kan de velden van de `cqModel` eigenschap gebruiken. Hiermee worden het DOM en de HTML-fragmenten uitgevoerd die in de pagina worden ingevoegd. Dit is de standaardmanier om een app te maken in React.

1. **Wijs de component aan het AEM middeltype via toe`MapTo()`**

   De afbeelding slaat componentenklassen op en wordt intern door de verstrekte `Container` component gebruikt om componenten terug te winnen en dynamisch te concretiseren die op het bepaalde middeltype worden gebaseerd.

   Dit dient als de &quot;lijm&quot;tussen voorkant en achtereind zodat weet de redacteur aan welke componenten de reactiecomponenten beantwoorden.

   Het `Page` en `ResponsiveGrid` zijn goede voorbeelden van klassen die de basis uitbreiden `Container`.

1. **De parameter van de component definiëren`EditConfig`als parameter voor`MapTo()`**

   Deze parameter is noodzakelijk om de redacteur te vertellen hoe de component zou moeten worden genoemd zolang bij nog niet wordt teruggegeven of geen inhoud heeft om terug te geven.

1. **De opgegeven`Container`klasse voor pagina&#39;s en containers uitbreiden**

   Pagina- en alineasystemen moeten deze klasse uitbreiden, zodat delegatie naar binnencomponenten naar behoren werkt.

1. **Voer een verpletterende oplossing uit die het gebruiken van HTML5`History`API.**

   Als de optie `ModelRouter` is ingeschakeld, wordt bij het aanroepen van de `pushState` en `replaceState` functies een verzoek aan de gebruiker geactiveerd `PageModelManager` om een ontbrekend fragment van het model op te halen.

   De huidige versie van het model ondersteunt `ModelRouter` alleen het gebruik van URL&#39;s die verwijzen naar het feitelijke bronnenpad van de entry-punten Sling Model. Het steunt niet het gebruik van vanity URLs of aliassen.

   De instructies `ModelRouter` kunnen worden uitgeschakeld of geconfigureerd om een lijst met reguliere expressies te negeren.

## AEM-agnost {#aem-agnostic}

Deze codeblokken laten zien hoe uw React- en hoekcomponenten niets nodig hebben dat specifiek is voor Adobe of AEM.

* Alles wat zich in de JavaScript-component bevindt, is AEM-agnostisch.
* Wat echter specifiek voor AEM is, is dat de JS-component aan een AEM-component moet worden toegewezen met de MapTo-hulpfunctie.

![screen_shot_2018-12-11at144019](assets/screen_shot_2018-12-11at144019.png)

De `MapTo` hulplijn is de &quot;lijm&quot; die het mogelijk maakt de achterkant en de voorkant van de onderdelen aan elkaar te koppelen:

* Het vertelt de container JS (of JS paragraafsysteem) welke component JS voor het teruggeven van elk van de componenten verantwoordelijk is die in JSON aanwezig zijn.
* Het voegt een de gegevensattribuut van HTML aan HTML toe die de component JS teruggeeft, zodat de redacteur van het KUUROORD weet welke dialoog aan de auteur wanneer het uitgeven van de component te tonen.

Voor meer informatie over het gebruiken `MapTo` en het bouwen van SPAs voor AEM in het algemeen, zie de Begonnen gids Aan de slag voor uw gekozen kader.

* [Aan de slag met SPA&#39;s in AEM - Reageren](/help/sites-developing/spa-getting-started-react.md)
* [Aan de slag met SPA&#39;s in AEM - hoekig](/help/sites-developing/spa-getting-started-angular.md)

## AEM-architectuur en SPA&#39;s {#aem-architecture-and-spas}

De algemene architectuur van AEM met inbegrip van ontwikkeling, creatie, en het publiceren milieu&#39;s verandert niet wanneer het gebruiken van SPAs. Nochtans is het nuttig om te begrijpen hoe de ontwikkeling van het KUUROORD in deze architectuur past.

![screen_shot_2018-12-11at145348](assets/screen_shot_2018-12-11at145348.png)

* **Build-omgeving**

   Dit is waar de bron voor de de toepassingsbron en componentenbron van het KUUROORD uitgecheckt zijn.

   * De NPM clientlib generator leidt tot een cliëntbibliotheek van het project van het KUUROORD.
   * Deze bibliotheek wordt door Maven genomen en samen met de component geïmplementeerd door de Maven Build-plug-in bij de AEM-auteur.

* **AEM-auteur**

   De inhoud wordt gecreeerd op de auteur AEM, met inbegrip van creatie SPAs.

   Wanneer een KUUROORD gebruikend de Redacteur van het KUUROORD op het auteursmilieu wordt uitgegeven:

   1. De SPA vraagt om de buitenste HTML.
   1. De CSS is geladen.
   1. Javascript van de toepassing van het KUUROORD wordt geladen.
   1. Wanneer de toepassing van het KUUROORD wordt uitgevoerd, wordt JSON gevraagd, toestaand app om DOM van de pagina met inbegrip van de `cq-data` attributen te bouwen.
   1. Met deze `cq-data` kenmerken kan de editor aanvullende pagina-informatie laden, zodat deze weet welke bewerkingsconfiguraties beschikbaar zijn voor de componenten.

* **AEM-publicatie**

   Dit is waar de geschreven inhoud en de gecompileerde bibliotheken met inbegrip van de toepassingsartefacten van het KUUROORD, clientlibs, en de componenten voor openbare consumptie worden gepubliceerd.

* **Dispatcher/CDN**

   De verzender fungeert als de cachelaag van AEM voor bezoekers van de site.

   * Verzoeken worden op dezelfde manier verwerkt als aanvragen bij de AEM-auteur. Er is echter geen verzoek om de pagina-informatie, omdat dit alleen nodig is voor de editor.
   * JavaScript, CSS, JSON en HTML worden in cache geplaatst, waardoor de pagina wordt geoptimaliseerd voor snelle levering.

>[!NOTE]
>
>Binnen AEM is het niet nodig om bouwstijlmechanismen uit te voeren JavaScript of Javascript zelf uit te voeren. AEM slechts gastheren de gecompileerde artefacten van de toepassing van het KUUROORD.

## Volgende stappen {#next-steps}

Voor een overzicht van hoe een eenvoudige KUUROORD in AEM wordt gestructureerd en hoe het werkt, zie de begonnen gids voor zowel [React](/help/sites-developing/spa-getting-started-react.md) als [Hoekig](/help/sites-developing/spa-getting-started-angular.md).

Voor een geleidelijke gids aan het creëren van uw eigen SPA, zie [Begonnen het Worden met de Redacteur AEM SPA - het Leerprogramma](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-spa-wknd-tutorial-develop.html)van Gebeurtenissen WKND.

Voor verdere details over het dynamische model aan componentenafbeelding en hoe het binnen SPAs in AEM werkt, zie het artikel [Dynamisch Model aan de Afbeelding van de Component voor SPAs](/help/sites-developing/spa-dynamic-model-to-component-mapping.md).

Als u wenst om SPAs in AEM voor een kader buiten React of Hoekig uit te voeren of eenvoudig een diepe duik in te nemen hoe het KUUROORD SDK voor AEM werkt, verwijs naar het artikel van het Blauwdruk [van het](/help/sites-developing/spa-blueprint.md) KUUROORD.
