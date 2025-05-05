---
title: Client-Side bibliotheken gebruiken
description: AEM biedt clientbibliotheekmappen, waarmee u uw clientcode in de opslagplaats kunt opslaan, in categorieën kunt ordenen en kunt bepalen wanneer en hoe elke categorie code aan de client moet worden verzonden
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
docset: aem65
exl-id: 408ac30c-60ab-4d6c-855c-d544af8d5cf9
solution: Experience Manager, Experience Manager Sites
feature: Developing,Personalization
role: Developer
source-git-commit: f965c449da06a1b7e60428e0734c621f004d318c
workflow-type: tm+mt
source-wordcount: '2791'
ht-degree: 0%

---

# Client-Side bibliotheken gebruiken{#using-client-side-libraries}

Moderne websites zijn sterk afhankelijk van verwerking op de client door complexe JavaScript- en CSS-code. Het organiseren en optimaliseren van het gebruik van deze code kan een ingewikkeld probleem zijn.

Om met deze kwestie te helpen behandelen, verstrekt AEM **Cliënt-zijOmslagen van de Bibliotheek**, die u uw cliënt-zijcode in de bewaarplaats laten opslaan, het in categorieën organiseren, en bepalen wanneer en hoe elke categorie van code aan de cliënt moet worden gediend. Het bibliotheeksysteem aan de clientzijde zorgt ervoor dat de juiste koppelingen in de uiteindelijke webpagina worden gemaakt om de juiste code te laden.

## Hoe clientbibliotheken werken in AEM {#how-client-side-libraries-work-in-aem}

De standaardmanier om een bibliotheek aan de clientzijde (dat wil zeggen een JS- of CSS-bestand) op te nemen in de HTML van een pagina, is eenvoudig om een `<script>` - of `<link>` -tag op te nemen in de JSP voor die pagina, die het pad naar het desbetreffende bestand bevat. Bijvoorbeeld:

```xml
...
<head>
   ...
   <script type="text/javascript" src="/etc/clientlibs/granite/jquery/source/1.8.1/jquery-1.8.1.js"></script>
   ...
</head>
...
```

Deze aanpak werkt in AEM, maar kan problemen veroorzaken wanneer pagina&#39;s en de bestanddelen ervan complex worden. In dergelijke gevallen bestaat het gevaar dat meerdere exemplaren van dezelfde JS-bibliotheek in de uiteindelijke HTML-uitvoer worden opgenomen. Om dit te vermijden en logische organisatie van cliënt-zijbibliotheken toe te staan AEM gebruikt **cliënt-zijbibliotheekomslagen**.

Een bibliotheekmap op de client is een opslagplaats van het type `cq:ClientLibraryFolder` . Zijn definitie in [ aantekening CND ](https://jackrabbit.apache.org/node-type-notation.html) is

```shell
[cq:ClientLibraryFolder] > sling:Folder
  - dependencies (string) multiple
  - categories (string) multiple
  - embed (string) multiple
  - channels (string) multiple
```

Door gebrek, `cq:ClientLibraryFolder` knopen kunnen overal binnen `/apps`, `/libs` en `/etc` worden geplaatst onderaan de bewaarplaats (deze gebreken, en andere montages kunnen door het **Granite paneel van de Bibliotheek van HTML van Adobe** van de [ Console van het Systeem ](https://localhost:4502/system/console/configMgr) worden gecontroleerd).

Elke `cq:ClientLibraryFolder` wordt gevuld met een set JS- en/of CSS-bestanden, samen met enkele ondersteunende bestanden (zie hieronder). De eigenschappen van de `cq:ClientLibraryFolder` worden als volgt geconfigureerd:

* `categories`: identificeert de categorieën waarin de set JS- en/of CSS-bestanden in deze `cq:ClientLibraryFolder` valt. Met de eigenschap `categories` , die meerdere waarden heeft, kan een bibliotheekmap deel uitmaken van meerdere categorieën (zie hieronder voor meer informatie over de bruikbaarheid).

* `dependencies`: Dit is een lijst met andere categorieën in de clientbibliotheek waarvan deze bibliotheekmap afhankelijk is. Als een bestand in `F` bijvoorbeeld een ander bestand in `G` nodig heeft om correct te werken, moet op basis van twee `cq:ClientLibraryFolder` nodes `F` en `G` ten minste een van de `categories` of `G` -knooppunten deel uitmaken van de `dependencies` of `F` -lus.

* `embed`: wordt gebruikt om code uit andere bibliotheken in te sluiten. Als knooppunt F knooppunten G en H insluit, is de resulterende HTML een concentratie van inhoud van knooppunten G en H.
* `allowProxy`: Als een clientbibliotheek zich onder `/apps` bevindt, staat deze eigenschap toegang tot de bibliotheek via een proxyservlet toe. Zie [ het Vestiging van een Omslag van de Bibliotheek van de Cliënt van de Volmacht Servlet ](/help/sites-developing/clientlibs.md#locating-a-client-library-folder-and-using-the-proxy-client-libraries-servlet) hieronder.

## Verwijzen naar clientbibliotheken {#referencing-client-side-libraries}

Omdat HTML de aangewezen technologie voor het ontwikkelen van AEM plaatsen is, zou HTML moeten worden gebruikt om cliënt-zijbibliotheken in AEM op te nemen. Het is echter ook mogelijk dit te doen met behulp van JSP.

### HTML gebruiken {#using-htl}

In HTML, worden de cliëntbibliotheken geladen door een helpermalplaatje dat door AEM wordt verstrekt, dat door [`data-sly-use` kan worden betreden ](https://helpx.adobe.com/experience-manager/htl/using/block-statements.html#use). Er zijn drie sjablonen beschikbaar in dit bestand, dat kan worden aangeroepen via [`data-sly-call` ](https://helpx.adobe.com/experience-manager/htl/using/block-statements.html#template-call) :

* **css** - laadt slechts de CSS dossiers van de referenced cliëntbibliotheken.
* **js** - Laadt slechts de dossiers van JavaScript van de referenced cliëntbibliotheken.
* **allen** - Laadt alle dossiers van de referenced cliëntbibliotheken (zowel CSS als JavaScript).

Elke hulpsjabloon verwacht een `categories` optie voor het verwijzen naar de gewenste clientbibliotheken. Deze optie kan ofwel een array van tekenreekswaarden zijn, ofwel een tekenreeks met een lijst met door komma&#39;s gescheiden waarden.

Voor verdere details en voorbeeld van gebruik, zie het document [ Begonnen het worden met de Taal van het Malplaatje van HTML ](https://helpx.adobe.com/experience-manager/htl/using/getting-started.html#loading-client-libraries).

### JSP gebruiken {#using-jsp}

Voeg een `ui:includeClientLib` -tag toe aan uw JSP-code om een koppeling naar clientbibliotheken op de gegenereerde HTML-pagina toe te voegen. Als u naar de bibliotheken wilt verwijzen, gebruikt u de waarde van de eigenschap `categories` van het knooppunt `ui:includeClientLib` .

```
<%@taglib prefix="ui" uri="https://www.adobe.com/taglibs/granite/ui/1.0" %>
<ui:includeClientLib categories="<%= categories %>" />
```

Het knooppunt `/etc/clientlibs/foundation/jquery` is bijvoorbeeld van het type `cq:ClientLibraryFolder` met een categorie-eigenschap van de waarde `cq.jquery` . De volgende code in een JSP-bestand verwijst naar de bibliotheken:

```xml
<ui:includeClientLib categories="cq.jquery"/>
```

De gegenereerde HTML-pagina bevat de volgende code:

```xml
<script type="text/javascript" src="/etc/clientlibs/foundation/jquery.js"></script>
```

Voor volledige informatie, met inbegrip van attributen voor het filtreren van JS, CSS, of themabibliotheken, zie [ ui:includeClientLib ](/help/sites-developing/taglib.md#lt-ui-includeclientlib).

>[!CAUTION]
>
>`<cq:includeClientLib>` , dat in het verleden veel werd gebruikt om clientbibliotheken op te nemen, is afgekeurd sinds AEM 5.6. [`<ui:includeClientLib>`](/help/sites-developing/taglib.md#lt-ui-includeclientlib) moet worden gebruikt zoals hierboven beschreven.

## Clientbibliotheekmappen maken {#creating-client-library-folders}

Maak een knooppunt `cq:ClientLibraryFolder` om JavaScript- en Cascading Style Sheet-bibliotheken te definiëren en beschikbaar te maken voor HTML-pagina&#39;s. Gebruik de eigenschap `categories` van het knooppunt om de bibliotheekcategorieën te identificeren waartoe het behoort.

Het knooppunt bevat een of meer bronbestanden die tijdens runtime worden samengevoegd tot één JS- en/of CSS-bestand. De naam van het gegenereerde bestand is de knooppuntnaam met de bestandsnaamextensie `.js` of `.css` . Het bibliotheekknooppunt `cq.jquery` resulteert bijvoorbeeld in het gegenereerde bestand met de naam `cq.jquery.js` of `cq.jquery.css` .

Clientbibliotheekmappen bevatten de volgende items:

* De JS- en/of CSS-bronbestanden die moeten worden samengevoegd.
* Bronnen die CSS-stijlen ondersteunen, zoals afbeeldingsbestanden.

  **Nota:** u subfolders kunt gebruiken om brondossiers te organiseren.
* Eén `js.txt` -bestand en/of één `css.txt` -bestand dat de bronbestanden identificeert die in de gegenereerde JS- en/of CSS-bestanden moeten worden samengevoegd.

![ clientlibarch ](assets/clientlibarch.png)

Voor informatie over vereisten die voor cliëntbibliotheken voor widgets specifiek zijn, zie [ Gebruikend en Uitbreidend Widgets ](/help/sites-developing/widgets.md).

De webclient moet over toegangsrechten voor het knooppunt `cq:ClientLibraryFolder` beschikken. U kunt ook bibliotheken vanuit beveiligde gebieden van de opslagplaats toegankelijk maken (zie Code insluiten vanuit andere bibliotheken, verderop).

### Bibliotheken in /lib overschrijven {#overriding-libraries-in-lib}

Clientbibliotheekmappen onder `/apps` hebben voorrang op mappen met dezelfde naam die zich op dezelfde manier in `/libs` bevinden. `/apps/cq/ui/widgets` heeft bijvoorbeeld voorrang op `/libs/cq/ui/widgets` . Wanneer deze bibliotheken tot dezelfde categorie behoren, wordt de onderstaande bibliotheek `/apps` gebruikt.

### Een clientbibliotheekmap zoeken en de server Proxy Client Libraries gebruiken {#locating-a-client-library-folder-and-using-the-proxy-client-libraries-servlet}

In eerdere versies stonden de clientbibliotheekmappen onder `/etc/clientlibs` in de opslagplaats. Dit wordt nog steeds ondersteund, maar het wordt aanbevolen de clientbibliotheken nu onder `/apps` te plaatsen. Hiermee zoekt u de clientbibliotheken in de buurt van de andere scripts, die u doorgaans onder `/apps` en `/libs` vindt.

>[!NOTE]
>
>De statische middelen onder de omslag van de cliëntbibliotheek moeten in een omslag genoemd *middelen* zijn. Als u niet de statische middelen, zoals beelden, onder de omslag *middelen* hebt, kan het niet op publiceer instantie worden van verwijzingen voorzien. Hier volgt een voorbeeld: https://localhost:4503/etc.clientlibs/geometrixx/components/clientlibs/resources/example.gif

>[!NOTE]
>
>Als u code beter wilt isoleren van de inhoud en configuratie, is het raadzaam clientbibliotheken onder `/apps` te zoeken en deze via `/etc.clientlibs` weer te geven met de eigenschap `allowProxy` .

De clientbibliotheken onder `/apps` zijn alleen toegankelijk als een proxyserver wordt gebruikt. ACLs wordt nog afgedwongen op de omslag van de cliëntbibliotheek, maar servlet staat voor de inhoud toe om via `/etc.clientlibs/` worden gelezen als het `allowProxy` bezit aan `true` wordt geplaatst.

Een statische bron is alleen toegankelijk via de proxy als deze zich onder een bron onder de map met de clientbibliotheek bevindt.

Als voorbeeld:

* U hebt een clientlib in `/apps/myprojects/clientlibs/foo`
* U hebt een statische afbeelding in `/apps/myprojects/clientlibs/foo/resources/icon.png`

Vervolgens stelt u de eigenschap `allowProxy` op `foo` in op true.

* Vervolgens kunt u `/etc.clientlibs/myprojects/clientlibs/foo.js` aanvragen
* U kunt dan naar de afbeelding verwijzen via `/etc.clientlibs/myprojects/clientlibs/foo/resources/icon.png`

>[!CAUTION]
>
>Als u proxy-clientbibliotheken gebruikt, is voor de AEM Dispatcher-configuratie mogelijk een update vereist om ervoor te zorgen dat de URI&#39;s met de extensiekclientlibs zijn toegestaan.

>[!CAUTION]
>
>Adobe raadt aan om clientbibliotheken onder `/apps` te zoeken en beschikbaar te maken via de proxyserver. Houd er echter rekening mee dat openbare sites altijd alleen gebruik kunnen maken van objecten die rechtstreeks via een `/apps` - of `/libs` -pad worden aangeboden.

### Een clientbibliotheekmap maken {#create-a-client-library-folder}

1. Open CRXDE Lite in Webbrowser ([ https://localhost:4502/crx/de ](https://localhost:4502/crx/de)).
1. Selecteer de omslag waar u van de omslag van de cliëntbibliotheek wilt de plaats bepalen en **klikken creeert > Node** leidt.
1. Voer een naam in voor het bibliotheekbestand en selecteer `cq:ClientLibraryFolder` in de lijst Type. Klik **O.K.** en klik dan **sparen allen**.
1. Om de categorie of de categorieën te specificeren dat de bibliotheek tot behoort, selecteer de `cq:ClientLibraryFolder` knoop, voeg het volgende bezit toe, en klik dan **sparen allen**:

   * Naam: categorieën
   * Type: String
   * Waarde: de categorienaam
   * Meerdere: selecteren

1. U kunt op alle manieren bronbestanden aan de bibliotheekmap toevoegen. U kunt bijvoorbeeld een WebDav-client gebruiken om bestanden te kopiëren of een bestand te maken en de inhoud handmatig te ontwerpen.

   **Nota:** u kunt brondossiers in subfolders organiseren indien gewenst.

1. Selecteer de omslag van de cliëntbibliotheek en klik **creëren > dossier** creëren.
1. Typ in het vak Bestandsnaam een van de volgende bestandsnamen en klik op OK:

   * **`js.txt`:** gebruik deze bestandsnaam om een JavaScript-bestand te genereren.
   * **`css.txt`:** gebruik deze bestandsnaam om een trapsgewijs opmaakmodel te genereren.

1. Open het bestand en typ de volgende tekst om de hoofdmap van het pad van de bronbestanden te identificeren:

   `#base=*[root]*`

   Vervang * `[root]`* door het pad naar de map met de bronbestanden ten opzichte van het TXT-bestand. Gebruik bijvoorbeeld de volgende tekst wanneer de bronbestanden zich in dezelfde map bevinden als het TXT-bestand:

   `#base=.`

   Met de volgende code wordt de hoofdmap ingesteld als de map met de naam mobile onder het knooppunt `cq:ClientLibraryFolder` :

   `#base=mobile`

1. Typ op de onderstaande regels `#base=[root]` de paden van de bronbestanden ten opzichte van het hoofdbestand. Plaats elke bestandsnaam op een aparte regel.
1. Klik **sparen allen**.

### Koppeling naar afhankelijke instellingen {#linking-to-dependencies}

Wanneer de code in de map met clientbibliotheken verwijst naar andere bibliotheken, identificeert u de andere bibliotheken als afhankelijkheden. In JSP, de markering `ui:includeClientLib` die verwijzingen uw omslag van de cliëntbibliotheek veroorzaakt de code van HTML om een verbinding aan uw geproduceerd bibliotheekdossier en de gebiedsdelen te omvatten.

De afhankelijkheden moeten een andere `cq:ClientLibraryFolder` zijn. Om gebiedsdelen te identificeren, voeg een bezit aan uw `cq:ClientLibraryFolder` knoop met de volgende attributen toe:

* **Naam:** gebiedsdelen
* **Type:** Koord []
* **Waarden:** de waarde van het categoriereigenschap van de cq:ClientLibraryFolder knoop die de huidige bibliotheekomslag van afhangt.

De constructor / `etc/clientlibs/myclientlibs/publicmain` is bijvoorbeeld afhankelijk van de `cq.jquery` -bibliotheek. JSP die verwijzingen de belangrijkste cliëntbibliotheek produceert HTML die de volgende code omvat:

```xml
<script src="/etc/clientlibs/foundation/cq.jquery.js" type="text/javascript">
<script src="/etc/clientlibs/mylibs/publicmain.js" type="text/javascript">
```

### Code van andere bibliotheken insluiten {#embedding-code-from-other-libraries}

U kunt code van een clientbibliotheek insluiten in een andere clientbibliotheek. Tijdens de runtime bevatten de gegenereerde JS- en CSS-bestanden van de insluitingsbibliotheek de code van de ingesloten bibliotheek.

Het insluiten van code is handig voor het verschaffen van toegang tot bibliotheken die zijn opgeslagen in beveiligde gebieden van de opslagplaats.

#### Toepassingsspecifieke clientbibliotheekmappen {#app-specific-client-library-folders}

U kunt het beste alle toepassingsgerelateerde bestanden in hun toepassingsmap onder `/apps` houden. Het wordt ook aanbevolen bezoekers van websites toegang tot de map `/apps` te weigeren. Om aan beide beste praktijken te voldoen, creeer een omslag van de cliëntbibliotheek onder `/apps`, en maak het toegankelijk door volmachtsservlet zoals die onder [ van een Omslag van de Bibliotheek van de Cliënt van de Cliënt wordt beschreven en Gebruikend Servlet van de Bibliotheken van de Cliënt van de Volmacht ](/help/sites-developing/clientlibs.md#locating-a-client-library-folder-and-using-the-proxy-client-libraries-servlet).

Gebruik de eigenschap Categorieën om de clientbibliotheekmap te identificeren die u wilt insluiten. Als u de bibliotheek wilt insluiten, voegt u een eigenschap toe aan het insluitingsknooppunt `cq:ClientLibraryFolder` en gebruikt u de volgende eigenschapkenmerken:

* **Naam:** bed in
* **Type:** Koord []
* **Waarde:** de waarde van het categoriebezit van de `cq:ClientLibraryFolder` knoop in te bedden.

#### Insluiten gebruiken om verzoeken te minimaliseren {#using-embedding-to-minimize-requests}

In sommige gevallen zult u zien dat de uiteindelijke HTML die door uw publicatieexemplaar wordt gegenereerd voor een standaardpagina, een relatief groot aantal `<script>` -elementen bevat, met name als uw site contextgegevens van klanten gebruikt voor analyses of doelwitten. In een niet-geoptimaliseerd project vindt u bijvoorbeeld de volgende reeks `<script>` -elementen in de HTML voor een pagina:

```xml
<script type="text/javascript" src="/etc/clientlibs/granite/jquery.js"></script>
<script type="text/javascript" src="/etc/clientlibs/granite/utils.js"></script>
<script type="text/javascript" src="/etc/clientlibs/granite/jquery/granite.js"></script>
<script type="text/javascript" src="/etc/clientlibs/foundation/jquery.js"></script>
<script type="text/javascript" src="/etc/clientlibs/foundation/shared.js"></script>
<script type="text/javascript" src="/etc/clientlibs/foundation/personalization/kernel.js"></script>
```

In dergelijke gevallen kan het handig zijn om alle vereiste code van de clientbibliotheek te combineren in één bestand, zodat het aantal heen en weer aanvragen bij het laden van de pagina wordt verminderd. Hiervoor kunt u `embed` de vereiste bibliotheken in uw toepassingsspecifieke clientbibliotheek plaatsen met de eigenschap embed van het knooppunt `cq:ClientLibraryFolder` .

De volgende categorieën in de clientbibliotheek worden bij AEM meegeleverd. U moet alleen die insluiten die vereist zijn voor het functioneren van uw specifieke site. Nochtans, **zou u de hier vermelde orde moeten handhaven**:

1. `browsermap.standard`
1. `browsermap`
1. `jquery-ui`
1. `cq.jquery.ui`
1. `personalization`
1. `personalization.core`
1. `personalization.core.kernel`
1. `personalization.clientcontext.kernel`
1. `personalization.stores.kernel`
1. `personalization.kernel`
1. `personalization.clientcontext`
1. `personalization.stores`
1. `cq.collab.comments`
1. `cq.collab.feedlink`
1. `cq.collab.ratings`
1. `cq.collab.toggle`
1. `cq.collab.forum`
1. `cq.cleditor`

#### Paden in CSS-bestanden {#paths-in-css-files}

Wanneer u CSS-bestanden insluit, gebruikt de gegenereerde CSS-code paden naar bronnen die relatief zijn ten opzichte van de insluitingsbibliotheek. De openbaar toegankelijke bibliotheek `/etc/client/libraries/myclientlibs/publicmain` sluit bijvoorbeeld de `/apps/myapp/clientlib` -clientbibliotheek in:

![ screen_shot_2012-05-29at20122pm ](assets/screen_shot_2012-05-29at20122pm.png)

Het bestand `main.css` bevat de volgende stijl:

```xml
body {
  padding: 0;
  margin: 0;
  background: url(images/bg-full.jpg) no-repeat center top;
  width: 100%;
}
```

Het CSS-bestand dat de node `publicmain` genereert, bevat de volgende stijl met behulp van de URL van de oorspronkelijke afbeelding:

```xml
body {
  padding: 0;
  margin: 0;
  background: url(../../../apps/myapp/clientlib/styles/images/bg-full.jpg) no-repeat center top;
  width: 100%;
}
```

### Een bibliotheek gebruiken voor specifieke mobiele groepen {#using-a-library-for-specific-mobile-groups}

Gebruik de eigenschap `channels` van een clientbibliotheekmap om de mobiele groep te identificeren die de bibliotheek gebruikt. De eigenschap `channels` is nuttig wanneer bibliotheken van dezelfde categorie zijn ontworpen voor verschillende apparaatmogelijkheden.

Als u een clientbibliotheekmap wilt koppelen aan een apparaatgroep, voegt u een eigenschap toe aan uw knooppunt `cq:ClientLibraryFolder` met de volgende kenmerken:

* **Naam:** kanalen
* **Type:** Koord []
* **Waarden:** De naam van de mobiele groep. Als u de bibliotheekmap wilt uitsluiten van een groep, plaatst u een uitroepteken (&quot;!&quot;) vóór de naam.

De volgende tabel bevat bijvoorbeeld de waarde van de eigenschap `channels` voor elke clientbibliotheekmap van de categorie `cq.widgets` :

| Map voor clientbibliotheek | Waarde van kanaaleigenschap |
|---|---|
| `/libs/cq/analytics/widgets` | `!touch` |
| `/libs/cq/analytics/widgets/themes/default` | `!touch` |
| `/libs/cq/cloudserviceconfigs/widgets` | `!touch` |
| `/libs/cq/touch/widgets` | `touch` |
| `/libs/cq/touch/widgets/themes/default` | `touch` |
| `/libs/cq/ui/widgets` | `!touch` |
| `/libs/cq/ui/widgets/themes/default` | `!touch` |

<!-- Search&Promote is end of life as of September 1, 2022 | `/libs/cq/searchpromote/widgets` | `!touch` | -->
<!-- Search&Promote is end of life as of September 1, 2022 | `/libs/cq/searchpromote/widgets/themes/default` |*[no value]* -->

## Voorprocessors gebruiken {#using-preprocessors}

AEM staat voor pluggable preprocessoren en schepen met steun voor [ Compressor YUI ](https://github.com/yui/yuicompressor#yui-compressor---the-yahoo-javascript-and-css-compressor) voor CSS en JavaScript toe en [ de Compiler van de Sluiting van Google (GCC) ](https://developers.google.com/closure/compiler/) voor JavaScript met YUI die als AEM standaard preprocessor wordt geplaatst.

Met de aanpasbare voorprocessoren kunt u flexibel gebruik maken, waaronder:

* ScriptProcessors definiëren die scriptbronnen kunnen verwerken
* Processors kunnen worden geconfigureerd met opties
* Processors kunnen worden gebruikt voor minificatie, maar ook voor niet-minieme gevallen
* Clientlib kan bepalen welke processor moet worden gebruikt

>[!NOTE]
>
>AEM gebruikt standaard de YUI-compressor. Zie de [ documentatie van GitHub van de Compressor van YUI ](https://github.com/yui/yuicompressor/issues) voor een lijst van bekende kwesties. Het schakelen naar GCC-compressor voor bepaalde clientlibs kan een aantal problemen oplossen die tijdens het gebruik van YUI zijn waargenomen.

>[!CAUTION]
>
>Plaats geen geminiateerde bibliotheek in een clientbibliotheek. Geef in plaats daarvan de onbewerkte bibliotheek op en gebruik de opties van de voorprocessoren als miniatuurafbeelding vereist is.

### Gebruik {#usage}

U kunt kiezen om de configuratie van preprocessoren per clientbibliotheek of systeembreed te configureren.

* De eigenschappen multivalue `cssProcessor` en `jsProcessor` toevoegen aan het clientbibliotheekknooppunt

* Of bepaal de systeem standaardconfiguratie via de **configuratie OSGi van de Manager van de Bibliotheek 0&rbrace; HTML**

Een preprocessorconfiguratie op de clientlib knoop neemt belangrijkheid over de configuratie OSGI.

### Indeling en voorbeelden {#format-and-examples}

#### Indeling {#format}

```xml
config:= mode ":" processorName options*;
mode:= "default" | "min";
processorName := "none" | <name>;
options := ";" option;
option := name "=" value;
```

#### YUI-compressor voor CSS-miniatuur en GCC voor JS {#yui-compressor-for-css-minification-and-gcc-for-js}

```xml
cssProcessor: ["default:none", "min:yui"]
jsProcessor: ["default:none", "min:gcc;compilationLevel=advanced"]
```

#### Typescript aan preprocess en dan GCC om te kleven en te verduisteren {#typescript-to-preprocess-and-then-gcc-to-minify-and-obfuscate}

```xml
jsProcessor: [
   "default:typescript",
   "min:typescript",
   "min:gcc;obfuscate=true"
]
```

#### Aanvullende GCC-opties {#additional-gcc-options}

```xml
failOnWarning (defaults to "false")
languageIn (defaults to "ECMASCRIPT5")
languageOut (defaults to "ECMASCRIPT5")
compilationLevel (defaults to "simple") (can be "whitespace", "simple", "advanced")
```

Voor verdere details op opties GCC, zie de [ documentatie GCC ](https://developers.google.com/closure/compiler/docs/compilation_levels).

### Systeemstandaardminiatuur instellen {#set-system-default-minifier}

YUI wordt geplaatst als standaardminifier in AEM. Voer de volgende stappen uit om dit te wijzigen in GCC.

1. Ga naar de Manager van Configuratie van de Felix van Apache in [ https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr)
1. Vind en geef **de Manager van de Bibliotheek van Adobe Granite HTML** uit.
1. Laat **toe** optie &lbrace;indien niet reeds toegelaten).
1. Plaats het Standaard van de Bewerker van waarde **JS vormt** aan `min:gcc`.

   Opties kunnen worden doorgegeven als deze worden gescheiden met een puntkomma, bijvoorbeeld `min:gcc;obfuscate=true` .

1. Klik **sparen** om de veranderingen te bewaren.

## Foutopsporingsgereedschappen {#debugging-tools}

AEM biedt verschillende gereedschappen voor foutopsporing en het testen van clientbibliotheekmappen.

### Zie ingesloten bestanden {#see-embedded-files}

Als u de oorsprong van ingesloten code wilt traceren of wilt controleren of ingesloten clientbibliotheken de verwachte resultaten opleveren, kunt u de namen zien van de bestanden die bij uitvoering worden ingesloten. Als u de bestandsnamen wilt zien, voegt u de parameter `debugClientLibs=true` toe aan de URL van de webpagina. De gegenereerde bibliotheek bevat `@import` -instructies in plaats van de ingesloten code.

In het voorbeeld in het vorige [ Inbedden Code van Andere Bibliotheken ](/help/sites-developing/clientlibs.md#embedding-code-from-other-libraries) sectie, sluit de `/etc/client/libraries/myclientlibs/publicmain` omslag van de cliëntbibliotheek de `/apps/myapp/clientlib` omslag van de cliëntbibliotheek in. Als u de parameter aan de webpagina toevoegt, wordt de volgende koppeling in de broncode van de webpagina gemaakt:

```xml
<link rel="stylesheet" href="/etc/clientlibs/mycientlibs/publicmain.css">
```

Wanneer u het `publicmain.css` -bestand opent, wordt de volgende code weergegeven:

```xml
@import url("/apps/myapp/clientlib/styles/main.css");
```

1. Voeg in het adresvak van uw webbrowser de volgende tekst toe aan de URL van uw HTML:

   `?debugClientLibs=true`
1. Bekijk de paginabron wanneer de pagina wordt geladen.
1. Klik op de koppeling die wordt opgegeven als de href voor het koppelingselement om het bestand te openen en de broncode weer te geven.

### Clientbibliotheken detecteren {#discover-client-libraries}

De component `/libs/cq/granite/components/dumplibs/dumplibs` genereert een pagina met informatie over alle clientbibliotheekmappen op het systeem. Het knooppunt `/libs/granite/ui/content/dumplibs` heeft de component als een brontype. Als u de pagina wilt openen, gebruikt u de volgende URL (waarbij u de host en poort naar wens wijzigt):

`https://<host>:<port>/libs/granite/ui/content/dumplibs.test.html`

Tot de gegevens behoren het bibliotheekpad en -type (CSS of JS) en de waarden van de bibliotheekkenmerken, zoals categorieën en afhankelijkheden. In de volgende tabellen op de pagina worden de bibliotheken in elke categorie en elk kanaal weergegeven.

### Zie Gegenereerde uitvoer {#see-generated-output}

De component `dumplibs` bevat een testkiezer die de broncode weergeeft die voor `ui:includeClientLib` -tags wordt gegenereerd. De pagina bevat code voor verschillende combinaties van js-, css- en themakenmerken.

1. Gebruik een van de volgende methoden om de pagina Uitvoer testen te openen:

   * Van de `dumplibs.html` pagina, klik de verbinding in **klik hier voor output het testen** tekst.

   * Open de volgende URL in uw webbrowser (gebruik indien nodig een andere host en poort):

      * `http://<host>:<port>/libs/granite/ui/content/dumplibs.html`

   Op de standaardpagina wordt uitvoer weergegeven voor tags zonder waarde voor het categoriekenmerk.

1. Om de output voor een categorie te zien, typ de waarde van het bezit van de cliëntbibliotheek `categories` en klik **voorleggen Vraag**.

## Bibliotheekverwerking configureren voor ontwikkeling en productie {#configuring-library-handling-for-development-and-production}

De HTML Library Manager-service verwerkt `cq:ClientLibraryFolder` -tags en genereert de bibliotheken bij uitvoering. Het type van milieu, ontwikkeling of productie, bepaalt hoe u de dienst zou moeten vormen:

* Meer beveiliging: foutopsporing uitschakelen
* Prestaties verbeteren: witruimte verwijderen en bibliotheken comprimeren.
* Leesbaarheid verbeteren: spaties opnemen en niet comprimeren.

Voor informatie over het vormen van de dienst, zie [ de Manager van de Bibliotheek van AEM HTML ](/help/sites-deploying/osgi-configuration-settings.md#aemhtmllibrarymanager).
