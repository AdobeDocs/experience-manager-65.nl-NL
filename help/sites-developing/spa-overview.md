---
title: Overzicht SPA Editor
seo-title: Overzicht SPA Editor
description: In dit artikel wordt een uitgebreid overzicht gegeven van de SPA Editor en van de manier waarop dit werkt. In dit artikel zijn gedetailleerde workflows opgenomen van interactie tussen de SPA Editor in AEM.
seo-description: In dit artikel wordt een uitgebreid overzicht gegeven van de SPA Editor en van de manier waarop dit werkt. In dit artikel zijn gedetailleerde workflows opgenomen van interactie tussen de SPA Editor in AEM.
uuid: c283abab-f5bc-414a-bc81-bf3bdce38534
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: spa
content-type: reference
discoiquuid: 06b8c0be-4362-4bd1-ad57-ea5503616b17
docset: aem65
translation-type: tm+mt
source-git-commit: 4c9a0bd73e8d87d3869c6a133f5d1049f8430cd1
workflow-type: tm+mt
source-wordcount: '1691'
ht-degree: 0%

---


# SPA Editor - overzicht{#spa-editor-overview}

Toepassingen op één pagina (SPA) kunnen aantrekkelijke ervaringen bieden voor websitegebruikers. Ontwikkelaars willen sites kunnen maken met behulp van SPA frameworks en auteurs willen inhoud naadloos bewerken binnen AEM voor een site die is gebouwd met behulp van dergelijke frameworks.

De SPA Editor biedt een uitgebreide oplossing voor het ondersteunen van SPA binnen AEM. Deze pagina geeft een overzicht van hoe SPA ondersteuning is gestructureerd in AEM, hoe de SPA Editor werkt en hoe het SPA framework en de AEM synchroon blijven.

>[!NOTE]
>
>De SPA Editor is de aanbevolen oplossing voor projecten die SPA op raamwerk gebaseerde renderen aan de clientzijde vereisen (bijvoorbeeld Reageren of Hoekig).

## Inleiding {#introduction}

Sites die zijn gemaakt met behulp van gemeenschappelijke SPA, zoals React en Angular, laden de inhoud via dynamische JSON en bieden niet de HTML-structuur die nodig is om bewerkingsbesturingselementen te kunnen plaatsen in de AEM Paginaeditor.

Om het bewerken van SPA binnen AEM mogelijk te maken, is een toewijzing tussen de JSON-uitvoer van de SPA en het inhoudsmodel in de AEM opslagplaats nodig om wijzigingen in de inhoud op te slaan.

SPA ondersteuning in AEM introduceert een dunne JS-laag die communiceert met de SPA JS-code wanneer deze wordt geladen in de Pagina-editor waarmee gebeurtenissen kunnen worden verzonden en de locatie voor de bewerkingsbesturingselementen kan worden geactiveerd om in-context bewerken mogelijk te maken. Deze eigenschap bouwt op het concept van het Eindpunt van de Diensten van de Inhoud API voort aangezien de inhoud van de SPA via de Diensten van de Inhoud moet worden geladen.

Raadpleeg de volgende documenten voor meer informatie over SPA in AEM:

* [SPA ](/help/sites-developing/spa-blueprint.md) Blauwdruk voor de technische voorschriften van een SPA
* [Aan de slag met SPA in ](/help/sites-developing/spa-getting-started-react.md) AEMvoor een snelle rondleiding van een eenvoudige SPA

## Ontwerp {#design}

De paginacomponent voor een SPA verstrekt niet de elementen van HTML van zijn kindcomponenten via het JSP of HTML- dossier. Deze bewerking wordt gedelegeerd aan het SPA. De representatie van onderliggende componenten of modellen wordt opgehaald als een JSON-gegevensstructuur van het JCR. De SPA componenten worden vervolgens volgens die structuur aan de pagina toegevoegd. Dit gedrag onderscheidt de aanvankelijke lichaamssamenstelling van de paginacomponent van niet-SPA tegenhangers.

### Paginamodel beheren {#page-model-management}

De resolutie en het beheer van het paginamodel worden gedelegeerd aan een opgegeven `PageModel`-bibliotheek. De SPA moet de bibliotheek Paginamodel gebruiken om te worden geïnitialiseerd en door de SPA Editor te worden ontworpen. De bibliotheek Paginamodel die indirect via de `aem-react-editable-components` npm aan de component AEMPagina wordt verstrekt. Het paginamodel is een tolk tussen AEM en de SPA en moet daarom altijd aanwezig zijn. Wanneer de pagina is gemaakt, moet een extra bibliotheek `cq.authoring.pagemodel.messaging` worden toegevoegd om de communicatie met de paginaeditor mogelijk te maken.

Als de SPA paginacomponent overerft van de hoofdcomponent van de pagina, zijn er twee opties om de categorie `cq.authoring.pagemodel.messaging` van de cliëntbibliotheek beschikbaar te maken:

* Als de sjabloon bewerkbaar is, voegt u deze toe aan het paginabeleid.
* Of voeg de categorieën toe gebruikend `customfooterlibs.html`.

Voor elke bron in het geëxporteerde model zal de SPA een werkelijke component toewijzen die de opdracht
renderen. Het model, dat als JSON wordt vertegenwoordigd, wordt dan teruggegeven gebruikend de componentenafbeeldingen binnen een container.
![screen_shot_2018-08-20at144152](assets/screen_shot_2018-08-20at144152.png)

>[!CAUTION]
>
>De opname van de categorie `cq.authoring.pagemodel.messaging` moet beperkt blijven tot de context van de SPA-editor.

### Gegevenstype voor communicatie {#communication-data-type}

Wanneer de categorie `cq.authoring.pagemodel.messaging` aan de pagina wordt toegevoegd, wordt een bericht naar de Pagina-editor verzonden om het gegevenstype JSON-communicatiegegevens vast te stellen. Wanneer het gegevenstype van communicatiegegevens aan JSON wordt geplaatst, zullen de verzoeken van de GET met de Sling Model eindpunten van een component communiceren. Nadat een update in de pagina-editor plaatsvindt, wordt de JSON-representatie van de bijgewerkte component verzonden naar de bibliotheek Paginamodel. De bibliotheek Paginamodel stelt vervolgens de SPA van updates op de hoogte.

![screen_shot_2018-08-20at143628](assets/screen_shot_2018-08-20at143628.png)

## Workflow {#workflow}

U kunt de stroom van de interactie tussen de SPA en AEM begrijpen door de SPA Redacteur als bemiddelaar tussen twee te denken.

* De communicatie tussen de pagina-editor en de SPA wordt gemaakt met JSON in plaats van HTML.
* De pagina-editor biedt de meest recente versie van het paginamodel aan de SPA via de iframe- en messaging-API.
* De manager van het paginamodel brengt de redacteur op de hoogte het klaar voor uitgave is en gaat het paginamodel als structuur JSON over.
* De editor wijzigt de DOM-structuur van de pagina die wordt gemaakt niet of opent deze zelfs niet, maar biedt het nieuwste paginamodel.

![screen_shot_2018-08-20at144324](assets/screen_shot_2018-08-20at144324.png)

### Basic SPA Editor Workflow {#basic-spa-editor-workflow}

Met inachtneming van de belangrijkste elementen van de SPA Editor, ziet de auteur de workflow op hoog niveau voor het bewerken van een SPA binnen AEM er als volgt uit.

![naamloos1](assets/untitled1.gif)

1. SPA Editor wordt geladen.
1. SPA wordt in een afzonderlijk frame geladen.
1. SPA vraagt JSON-inhoud aan en rendert componenten client-side.
1. SPA Editor detecteert gerenderde componenten en genereert overlays.
1. De auteur klikt op bedekking en toont de bewerkingswerkbalk van de component.
1. SPA de Redacteur met een verzoek van de POST aan de server voortduurt uitgeeft.
1. SPA Editor vraagt bijgewerkte JSON naar de SPA Editor, die met een DOM-gebeurtenis naar de SPA wordt verzonden.
1. SPA geeft de betrokken component opnieuw weer, waarbij het DOM wordt bijgewerkt.

>[!NOTE]
>
>Houd rekening met:
>
>* De SPA is altijd verantwoordelijk voor de weergave.
>* De SPA Editor staat los van de SPA zelf.
>* In productie (publiceren), wordt de SPA redacteur nooit geladen.

>



### Workflow voor paginabewerking tussen client en server {#client-server-page-editing-workflow}

Dit is een gedetailleerder overzicht van de interactie tussen client en server bij het bewerken van een SPA.

![page_editor_spa_authoringmediator-2](assets/page_editor_spa_authoringmediator-2.png)

1. De SPA initialiseert zichzelf en vraagt het paginamodel aan bij Sling Model Exporter.
1. De verkoper ModelExporter verzoekt om de middelen die de pagina van de bewaarplaats samenstellen.
1. De repository retourneert de bronnen.
1. De verkoper van het ModelExporter keert het model van de pagina terug.
1. De SPA instantieert zijn componenten die op het paginamodel worden gebaseerd.
1. **6** aDe inhoud deelt de redacteur mee dat het voor ontwerp klaar is.

   **6** bDe paginaredacteur verzoekt de componentenauteursconfiguraties.

   **6** cDe pagina-editor ontvangt de componentconfiguraties.
1. Wanneer de auteur een component bewerkt, wordt in de pagina-editor een wijzigingsverzoek naar de standaard POST servlet gepost.
1. De bron wordt bijgewerkt in de opslagplaats.
1. De bijgewerkte bron wordt doorgegeven aan de POST servlet.
1. De standaard server van de POST deelt de paginaredacteur mee dat het middel is bijgewerkt.
1. De paginaeditor vraagt om het nieuwe paginamodel.
1. De bronnen waaruit de pagina bestaat, worden opgevraagd bij de opslagplaats.
1. De bronnen waaruit de pagina bestaat, worden door de gegevensopslagruimte aan de Verkoopmodel Exporter verschaft.
1. Het bijgewerkte paginamodel wordt geretourneerd aan de editor.
1. De paginaredacteur werkt de verwijzing van het paginamodel van de SPA bij.
1. De SPA werkt zijn componenten bij die op de nieuwe verwijzing van het paginamodel worden gebaseerd.
1. De componentconfiguraties van de paginaeditors worden bijgewerkt.

   **17** aDe SPA geeft aan dat de inhoud gereed is voor de pagina-editor.

   **17** bDe paginaredacteur voorziet de SPA van componentenconfiguraties.

   **17** cDe SPA biedt bijgewerkte componentconfiguraties.

### Ontwerpwerkstroom {#authoring-workflow}

Dit is een gedetailleerder overzicht dat is toegespitst op de ontwerpervaring.

![spa_content_authoringmodel](assets/spa_content_authoringmodel.png)

1. De SPA haalt het paginamodel op.
1. **2** aHet paginamodel voorziet de redacteur van de gegevens die voor creatie worden vereist.

   **2** bWanneer op de hoogte gesteld, werkt de componentenbeheerder de inhoudsstructuur van de pagina bij.
1. De componentenbeheerder vraagt de afbeelding tussen een AEM middeltype en een SPA component.
1. De componentinstantie instantieert dynamisch de SPA component op basis van het paginamodel en de componenttoewijzing.
1. De paginaeditor werkt het paginamodel bij.
1. **6** aHet paginamodel verstrekt bijgewerkte auteursgegevens aan de paginaredacteur.

   **6** bHet paginamodel verzendt wijzigingen naar de componentorchestrator.
1. De componentorchestrator haalt de componenttoewijzing op.
1. De componentbeheerder werkt de inhoud van de pagina bij.
1. Wanneer de SPA klaar is met het bijwerken van de inhoud van de pagina, laadt de pagina-editor de ontwerpomgeving.

## Vereisten en beperkingen {#requirements-limitations}

Om de auteur in staat te stellen om de paginaredacteur te gebruiken om de inhoud van een SPA uit te geven, moet uw SPA toepassing worden uitgevoerd om met de AEM SPA Redacteur SDK in wisselwerking te staan. Zie [Aan de slag met SPA in AEM](/help/sites-developing/spa-getting-started-react.md) document voor het minimale waarvan u op de hoogte moet zijn om uw werk uit te voeren.

### Ondersteunde kaders {#supported-frameworks}

De SPA Editor SDK ondersteunt de volgende minimale versies:

* 16.x en hoger reageren
* Hoek 6.x en hoger

Eerdere versies van deze frameworks werken mogelijk met de AEM SPA Editor SDK, maar worden niet ondersteund.

### Extra kaders {#additional-frameworks}

Er kunnen aanvullende SPA worden geïmplementeerd om te werken met de AEM SPA Editor SDK. Zie [SPA Blueprint](/help/sites-developing/spa-blueprint.md) document voor de vereisten waaraan een framework moet voldoen om een framespecifieke laag te maken die bestaat uit modules, componenten en services om met de AEM SPA Editor te werken.

### Meerdere kiezers gebruiken {#multiple-selectors}

Aanvullende aangepaste kiezers kunnen worden gedefinieerd en gebruikt als onderdeel van een SPA die is ontwikkeld voor de AEM SPA SDK. Voor deze ondersteuning is echter vereist dat de `model`-kiezer de eerste kiezer is en dat de extensie `.json` is als [vereist door de JSON Exporter.](json-exporter-components.md#multiple-selectors)

### Vereisten voor teksteditor {#text-editor-requirements}

Als u de op plaats-editor wilt gebruiken van een tekstcomponent die in SPA is gemaakt, is er aanvullende configuratie vereist.

1. Stel een willekeurig kenmerk in op het containerelement dat de tekst-HTML bevat. In het geval van de WKND steekproefinhoud van het Dagboek, is het een `<div>` element en de selecteur die is gebruikt is `data-rte-editelement`.
1. Stel de configuratie `editElementQuery` in op de `cq:InplaceEditingConfig` van de corresponderende AEM tekstcomponent die naar die kiezer wijst, bijvoorbeeld `data-rte-editelement`. Hierdoor weet de editor welk HTML-element de HTML-tekst omsluit.

Voor een voorbeeld van hoe dit wordt gedaan, zie [de steekproefinhoud van het Dagboek van WKND.](https://github.com/adobe/aem-sample-we-retail-journal/pull/16/files)

Voor extra informatie over het `editElementQuery` bezit en de configuratie van de rijke tekstredacteur, zie [vorm de Rich Redacteur van de Tekst.](/help/sites-administering/rich-text-editor.md)

### Beperkingen {#limitations}

De AEM SPA Editor SDK werd geïntroduceerd met AEM 6.4 service pack 2. Het wordt volledig gesteund door Adobe, en als nieuwe eigenschap blijft het worden verbeterd en uitgebreid. De volgende AEM worden nog niet ondersteund door de SPA Editor:

* Doelmodus
* ContextHub
* Inline-afbeeldingen bewerken
* Configs bewerken (bijv. listeners)
* Stijlsysteem
* Ongedaan maken/Opnieuw
* Pagina diff en Tijd verdraaien
* Functies voor het herschrijven van HTML aan de serverzijde, zoals Koppelingencontrole, CDN-herschrijfservice, URL-verkorting, enz.
* Modus Ontwikkelaar
* AEM starten
