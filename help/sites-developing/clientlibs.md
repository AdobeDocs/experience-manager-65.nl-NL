---
title: Client-Side bibliotheken gebruiken
description: AEM biedt clientbibliotheekmappen, waarmee u uw clientcode in de opslagplaats kunt opslaan, in categorieën kunt indelen en kunt bepalen wanneer en hoe elke categorie code aan de client moet worden verzonden
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
docset: aem65
exl-id: 408ac30c-60ab-4d6c-855c-d544af8d5cf9
solution: Experience Manager, Experience Manager Sites
feature: Developing,Personalization
role: Developer
source-git-commit: 305227eff3c0d6414a5ae74bcf3a74309dccdd13
workflow-type: tm+mt
source-wordcount: '2791'
ht-degree: 0%

---

# Client-Side bibliotheken gebruiken{#using-client-side-libraries}

Moderne websites zijn sterk afhankelijk van verwerking op de client door complexe JavaScript- en CSS-code. Het organiseren en optimaliseren van het gebruik van deze code kan een ingewikkeld probleem zijn.

Om dit probleem te helpen aanpakken, AEM biedt **Client-side bibliotheekmappen**, waarmee u uw code aan de clientzijde in de opslagplaats kunt opslaan, in categorieën kunt ordenen en kunt bepalen wanneer en hoe elke categorie code aan de client moet worden aangeboden. Het bibliotheeksysteem aan de clientzijde zorgt ervoor dat de juiste koppelingen in de uiteindelijke webpagina worden gemaakt om de juiste code te laden.

## Hoe clientbibliotheken werken in AEM {#how-client-side-libraries-work-in-aem}

De standaardmanier om een bibliotheek aan de clientzijde (dat wil zeggen een JS- of CSS-bestand) op te nemen in de HTML van een pagina is door gewoon een `<script>` of `<link>` in het JSP voor die pagina, met daarin het pad naar het desbetreffende bestand. Bijvoorbeeld:

```xml
...
<head>
   ...
   <script type="text/javascript" src="/etc/clientlibs/granite/jquery/source/1.8.1/jquery-1.8.1.js"></script>
   ...
</head>
...
```

Deze aanpak werkt AEM, maar kan problemen veroorzaken wanneer pagina&#39;s en de bestanddelen ervan complex worden. In dergelijke gevallen bestaat het gevaar dat meerdere exemplaren van dezelfde JS-bibliotheek in de uiteindelijke HTML-uitvoer worden opgenomen. Om dit te vermijden en logische organisatie van cliënt-zijbibliotheken toe te staan AEM gebruik **clientbibliotheekmappen**.

Een bibliotheekmap op de client is een opslagplaats van het type `cq:ClientLibraryFolder`. De definitie ervan in [CND-notatie](https://jackrabbit.apache.org/node-type-notation.html) is

```shell
[cq:ClientLibraryFolder] > sling:Folder
  - dependencies (string) multiple
  - categories (string) multiple
  - embed (string) multiple
  - channels (string) multiple
```

Standaard, `cq:ClientLibraryFolder` knooppunten kunnen overal in de `/apps`, `/libs` en `/etc` substructuren van de opslagplaats (deze standaardinstellingen en andere instellingen kunnen via de **Adobe Granite HTML Library Manager** van het [Systeemconsole](https://localhost:4502/system/console/configMgr)).

Elk `cq:ClientLibraryFolder` wordt gevuld met een set JS- en/of CSS-bestanden, samen met enkele ondersteunende bestanden (zie hieronder). De eigenschappen van de `cq:ClientLibraryFolder` zijn als volgt geconfigureerd:

* `categories`: Identificeert de categorieën waarin de set JS- en/of CSS-bestanden binnen deze set `cq:ClientLibraryFolder` vallen. De `categories` Met een eigenschap met meerdere waarden kan een bibliotheekmap deel uitmaken van meerdere categorieën (zie hieronder voor meer informatie).

* `dependencies`: Dit is een lijst van andere categorieën van de cliëntbibliotheek waarvan deze bibliotheekomslag afhangt. Bijvoorbeeld, gegeven twee `cq:ClientLibraryFolder` knooppunten `F` en `G`, als een bestand zich in `F` vereist een ander bestand in `G` ten minste een van de `categories` van `G` behoort tot de `dependencies` van `F`.

* `embed`: Wordt gebruikt om code uit andere bibliotheken in te sluiten. Als knooppunt F knooppunten G en H insluit, is de resulterende HTML een concentratie van inhoud van knooppunten G en H.
* `allowProxy`: Als een clientbibliotheek zich onder `/apps`Met deze eigenschap is toegang tot de eigenschap via proxyservlet mogelijk. Zie [Een clientbibliotheekmap zoeken en de server Proxy Client Libraries gebruiken](/help/sites-developing/clientlibs.md#locating-a-client-library-folder-and-using-the-proxy-client-libraries-servlet) hieronder.

## Verwijzen naar clientbibliotheken {#referencing-client-side-libraries}

Omdat HTML de aangewezen technologie voor het ontwikkelen van AEM plaatsen is, zou HTML moeten worden gebruikt om cliënt-zijbibliotheken in AEM te omvatten. Het is echter ook mogelijk dit te doen met behulp van JSP.

### HTML gebruiken {#using-htl}

In HTML worden clientbibliotheken geladen via een helpersjabloon die wordt geleverd door AEM en die toegankelijk is via [`data-sly-use`](https://helpx.adobe.com/experience-manager/htl/using/block-statements.html#use). Dit bestand bevat drie sjablonen, die u kunt aanroepen via [`data-sly-call`](https://helpx.adobe.com/experience-manager/htl/using/block-statements.html#template-call):

* **css** - Laadt alleen de CSS-bestanden van de clientbibliotheken waarnaar wordt verwezen.
* **js** - Hiermee worden alleen de JavaScript-bestanden geladen van de clientbibliotheken waarnaar wordt verwezen.
* **alles** - Laadt alle bestanden van de clientbibliotheken waarnaar wordt verwezen (zowel CSS als JavaScript).

Elke hulpsjabloon verwacht een `categories` voor het verwijzen naar de gewenste clientbibliotheken. Deze optie kan ofwel een array van tekenreekswaarden zijn, ofwel een tekenreeks met een lijst met door komma&#39;s gescheiden waarden.

Raadpleeg het document voor meer informatie en voorbeelden van het gebruik [Aan de slag met de Sjabloontaal HTML](https://helpx.adobe.com/experience-manager/htl/using/getting-started.html#loading-client-libraries).

### JSP gebruiken {#using-jsp}

Voeg een `ui:includeClientLib` -tag aan uw JSP-code toevoegen om een koppeling naar clientbibliotheken op de gegenereerde HTML-pagina toe te voegen. Als u naar de bibliotheken wilt verwijzen, gebruikt u de waarde van de optie `categories` eigendom van de `ui:includeClientLib` knooppunt.

```
<%@taglib prefix="ui" uri="https://www.adobe.com/taglibs/granite/ui/1.0" %>
<ui:includeClientLib categories="<%= categories %>" />
```

Bijvoorbeeld de `/etc/clientlibs/foundation/jquery` node is type `cq:ClientLibraryFolder` met een categorie-eigenschap van waarde `cq.jquery`. De volgende code in een JSP-bestand verwijst naar de bibliotheken:

```xml
<ui:includeClientLib categories="cq.jquery"/>
```

De gegenereerde pagina HTML bevat de volgende code:

```xml
<script type="text/javascript" src="/etc/clientlibs/foundation/jquery.js"></script>
```

Voor volledige informatie, met inbegrip van attributen voor het filtreren van JS, CSS, of themabibliotheken, zie [ui:includeClientLib](/help/sites-developing/taglib.md#lt-ui-includeclientlib).

>[!CAUTION]
>
>`<cq:includeClientLib>`, die in het verleden vaak werd gebruikt om clientbibliotheken op te nemen, is sinds AEM 5.6 afgekeurd. [`<ui:includeClientLib>`](/help/sites-developing/taglib.md#lt-ui-includeclientlib) moet worden gebruikt zoals hierboven beschreven.

## Clientbibliotheekmappen maken {#creating-client-library-folders}

Een `cq:ClientLibraryFolder` om JavaScript- en Cascading Style Sheet-bibliotheken te definiëren en deze beschikbaar te maken voor HTML-pagina&#39;s. Gebruik de `categories` eigenschap van het knooppunt om de bibliotheekcategorieën te identificeren waartoe het behoort.

Het knooppunt bevat een of meer bronbestanden die tijdens runtime worden samengevoegd tot één JS- en/of CSS-bestand. De naam van het gegenereerde bestand is de knooppuntnaam met een van de `.js` of `.css` bestandsextensie. Het bibliotheekknooppunt genaamd `cq.jquery` resulteert in het gegenereerde bestand met de naam `cq.jquery.js` of `cq.jquery.css`.

Clientbibliotheekmappen bevatten de volgende items:

* De JS- en/of CSS-bronbestanden die moeten worden samengevoegd.
* Bronnen die CSS-stijlen ondersteunen, zoals afbeeldingsbestanden.

  **Opmerking:** U kunt submappen gebruiken om bronbestanden te ordenen.
* Eén `js.txt` bestand en/of één `css.txt` bestand dat de bronbestanden identificeert die moeten worden samengevoegd in de gegenereerde JS- en/of CSS-bestanden.

![clientlibarch](assets/clientlibarch.png)

Voor informatie over vereisten die specifiek zijn voor clientbibliotheken voor widgets, raadpleegt u [Widgets gebruiken en uitbreiden](/help/sites-developing/widgets.md).

De webclient moet over toegangsrechten voor de `cq:ClientLibraryFolder` knooppunt. U kunt ook bibliotheken vanuit beveiligde gebieden van de opslagplaats toegankelijk maken (zie Code insluiten vanuit andere bibliotheken, verderop).

### Bibliotheken in /lib overschrijven {#overriding-libraries-in-lib}

Clientbibliotheekmappen verderop `/apps` hebben voorrang op mappen met dezelfde naam in `/libs`. Bijvoorbeeld: `/apps/cq/ui/widgets` heeft voorrang boven `/libs/cq/ui/widgets`. Wanneer deze bibliotheken tot dezelfde categorie behoren, wordt de onderstaande bibliotheek weergegeven `/apps` wordt gebruikt.

### Een clientbibliotheekmap zoeken en de server Proxy Client Libraries gebruiken {#locating-a-client-library-folder-and-using-the-proxy-client-libraries-servlet}

In eerdere versies stonden de mappen met de clientbibliotheek hieronder. `/etc/clientlibs` in de repository. Dit wordt nog steeds ondersteund, maar het wordt aanbevolen dat clientbibliotheken zich nu onder `/apps`. De clientbibliotheken bevinden zich op deze manier in de buurt van de andere scripts, die u doorgaans hieronder vindt `/apps` en `/libs`.

>[!NOTE]
>
>Statische bronnen onder de clientbibliotheekmap moeten zich in een map met de naam *bronnen*. Als u niet over de statische bronnen beschikt, zoals afbeeldingen, onder de map *bronnen*, kan er niet naar worden verwezen op een publicatie-instantie. Hier volgt een voorbeeld: https://localhost:4503/etc.clientlibs/geometrixx/components/clientlibs/resources/example.gif

>[!NOTE]
>
>Om code beter van inhoud en configuratie te isoleren, wordt het geadviseerd om van cliëntbibliotheken onder de plaats te bepalen `/apps` en ze via `/etc.clientlibs` door de `allowProxy` eigenschap.

Voor de clientbibliotheken onder `/apps` om toegankelijk te zijn, wordt een volmachtsserver gebruikt. ACLs wordt nog afgedwongen op de omslag van de cliëntbibliotheek, maar servlet laat voor de inhoud toe om via worden gelezen `/etc.clientlibs/` als de `allowProxy` eigenschap is ingesteld op `true`.

Een statische bron is alleen toegankelijk via de proxy als deze zich onder een bron onder de map met de clientbibliotheek bevindt.

Als voorbeeld:

* U hebt een clientlib in `/apps/myproject/clientlibs/foo`
* U hebt een statische afbeelding in `/apps/myprojects/clientlibs/foo/resources/icon.png`

Vervolgens stelt u de `allowProxy` eigenschap op `foo` naar waar.

* U kunt vervolgens `/etc.clientlibs/myprojects/clientlibs/foo.js`
* U kunt dan naar de afbeelding verwijzen via `/etc.clientlibs/myprojects/clientlibs/foo/resources/icon.png`

>[!CAUTION]
>
>Wanneer het gebruiken van pro-xied cliëntbibliotheken, kan de AEM configuratie van de Ontvanger een update vereisen om ervoor te zorgen URIs met de uitbreidingsclientlibs wordt toegestaan.

>[!CAUTION]
>
>Adobe raadt aan clientbibliotheken te zoeken onder `/apps` en ze beschikbaar stellen via het proxyservlet. Houd er echter rekening mee dat de beste praktijken nog steeds vereisen dat openbare sites nooit iets bevatten dat rechtstreeks via een `/apps` of `/libs` pad.

### Een clientbibliotheekmap maken {#create-a-client-library-folder}

1. CRXDE Lite openen in een webbrowser ([https://localhost:4502/crx/de](https://localhost:4502/crx/de)).
1. Selecteer de map waarin u de clientbibliotheekmap wilt zoeken en klik op **Maken > Knooppunt maken**.
1. Voer een naam in voor het bibliotheekbestand en selecteer in de lijst Type de optie `cq:ClientLibraryFolder`. Klikken **OK** en klik vervolgens op **Alles opslaan**.
1. Selecteer de categorie of categorieën waartoe de bibliotheek behoort `cq:ClientLibraryFolder` knoop, voeg het volgende bezit toe, en klik dan **Alles opslaan**:

   * Naam: categorieën
   * Type: String
   * Waarde: de categorienaam
   * Meerdere: selecteren

1. U kunt op alle manieren bronbestanden aan de bibliotheekmap toevoegen. U kunt bijvoorbeeld een WebDav-client gebruiken om bestanden te kopiëren of een bestand te maken en de inhoud handmatig te ontwerpen.

   **Opmerking:** U kunt bronbestanden desgewenst in submappen ordenen.

1. Selecteer de clientbibliotheekmap en klik op **Maken > Bestand maken**.
1. Typ in het vak Bestandsnaam een van de volgende bestandsnamen en klik op OK:

   * **`js.txt`:** Gebruik deze bestandsnaam om een JavaScript-bestand te genereren.
   * **`css.txt`:** Gebruik deze bestandsnaam om een trapsgewijs opmaakmodel te genereren.

1. Open het bestand en typ de volgende tekst om de hoofdmap van het pad van de bronbestanden te identificeren:

   `#base=*[root]*`

   Vervangen * `[root]`* met het pad naar de map die de bronbestanden bevat, relatief ten opzichte van het TXT-bestand. Gebruik bijvoorbeeld de volgende tekst wanneer de bronbestanden zich in dezelfde map bevinden als het TXT-bestand:

   `#base=.`

   Met de volgende code wordt de hoofdmap ingesteld als de map mobile onder de `cq:ClientLibraryFolder` knooppunt:

   `#base=mobile`

1. Op de onderstaande regels `#base=[root]`Typ de paden van de bronbestanden ten opzichte van het hoofdbestand. Plaats elke bestandsnaam op een aparte regel.
1. Klikken **Alles opslaan**.

### Koppeling naar afhankelijke instellingen {#linking-to-dependencies}

Wanneer de code in de map met clientbibliotheken verwijst naar andere bibliotheken, identificeert u de andere bibliotheken als afhankelijkheden. In het JSP `ui:includeClientLib` -tag die verwijst naar de clientbibliotheekmap, bevat de HTML-code een koppeling naar het gegenereerde bibliotheekbestand en de afhankelijkheden.

De afhankelijkheden moeten een andere `cq:ClientLibraryFolder`. Om gebiedsdelen te identificeren, voeg een bezit aan uw toe `cq:ClientLibraryFolder` knooppunt met de volgende kenmerken:

* **Naam:** afhankelijkheden
* **Type:** String[]
* **Waarden:** De waarde van het eigenschap category van het knooppunt cq:ClientLibraryFolder waarvan de huidige bibliotheekmap afhankelijk is.

Bijvoorbeeld de `etc/clientlibs/myclientlibs/publicmain` is afhankelijk van de `cq.jquery` bibliotheek. JSP die verwijzingen de belangrijkste cliëntbibliotheek produceert HTML die de volgende code omvat:

```xml
<script src="/etc/clientlibs/foundation/cq.jquery.js" type="text/javascript">
<script src="/etc/clientlibs/mylibs/publicmain.js" type="text/javascript">
```

### Code van andere bibliotheken insluiten {#embedding-code-from-other-libraries}

U kunt code van een clientbibliotheek insluiten in een andere clientbibliotheek. Tijdens de runtime bevatten de gegenereerde JS- en CSS-bestanden van de insluitingsbibliotheek de code van de ingesloten bibliotheek.

Het insluiten van code is handig voor het verschaffen van toegang tot bibliotheken die zijn opgeslagen in beveiligde gebieden van de opslagplaats.

#### Toepassingsspecifieke clientbibliotheekmappen {#app-specific-client-library-folders}

Het wordt aanbevolen om alle toepassingsgerelateerde bestanden in de onderstaande toepassingsmap te houden `/apps`. Het is ook aan te raden bezoekers van websites de toegang tot de `/apps` map. Voor beide aanbevolen procedures maakt u hieronder een clientbibliotheekmap `/apps`en toegankelijk maken via het proxyservlet, zoals beschreven in [Een clientbibliotheekmap zoeken en de server Proxy Client Libraries gebruiken](/help/sites-developing/clientlibs.md#locating-a-client-library-folder-and-using-the-proxy-client-libraries-servlet).

Gebruik de eigenschap Categorieën om de clientbibliotheekmap te identificeren die u wilt insluiten. Als u de bibliotheek wilt insluiten, voegt u een eigenschap toe aan het insluiten `cq:ClientLibraryFolder` node, met de volgende eigenschapkenmerken:

* **Naam:** insluiten
* **Type:** String[]
* **Waarde:** De waarde van de eigenschap Categorieën van de `cq:ClientLibraryFolder` in te sluiten knooppunt.

#### Insluiten gebruiken om verzoeken te minimaliseren {#using-embedding-to-minimize-requests}

In sommige gevallen zult u merken dat de uiteindelijke HTML die door uw publicatieexemplaar voor een standaardpagina wordt gegenereerd, een relatief groot aantal `<script>` -elementen, met name als uw site contextinformatie van de klant gebruikt voor analyses of doelwitten. In een niet-geoptimaliseerd project kunt u bijvoorbeeld de volgende reeks van `<script>` elementen in de HTML voor een pagina:

```xml
<script type="text/javascript" src="/etc/clientlibs/granite/jquery.js"></script>
<script type="text/javascript" src="/etc/clientlibs/granite/utils.js"></script>
<script type="text/javascript" src="/etc/clientlibs/granite/jquery/granite.js"></script>
<script type="text/javascript" src="/etc/clientlibs/foundation/jquery.js"></script>
<script type="text/javascript" src="/etc/clientlibs/foundation/shared.js"></script>
<script type="text/javascript" src="/etc/clientlibs/foundation/personalization/kernel.js"></script>
```

In dergelijke gevallen kan het handig zijn om alle vereiste code van de clientbibliotheek te combineren in één bestand, zodat het aantal heen en weer aanvragen bij het laden van de pagina wordt verminderd. Om dit te doen kunt u `embed` de vereiste bibliotheken in uw toepassingsspecifieke clientbibliotheek met de eigenschap embed van het dialoogvenster `cq:ClientLibraryFolder` knooppunt.

De volgende categorieën van de cliëntbibliotheek zijn inbegrepen met AEM. U moet alleen die insluiten die vereist zijn voor het functioneren van uw specifieke site. Maar **u moet de volgorde handhaven die hier wordt weergegeven**:

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

Wanneer u CSS-bestanden insluit, gebruikt de gegenereerde CSS-code paden naar bronnen die relatief zijn ten opzichte van de insluitingsbibliotheek. De openbaar toegankelijke bibliotheek `/etc/client/libraries/myclientlibs/publicmain` sluit het `/apps/myapp/clientlib` clientbibliotheek:

![screen_shot_2012-05-29at20122pm](assets/screen_shot_2012-05-29at20122pm.png)

De `main.css` bestand bevat de volgende stijl:

```xml
body {
  padding: 0;
  margin: 0;
  background: url(images/bg-full.jpg) no-repeat center top;
  width: 100%;
}
```

Het CSS-bestand dat het `publicmain` node genereert bevat de volgende stijl met behulp van de URL van de oorspronkelijke afbeelding:

```xml
body {
  padding: 0;
  margin: 0;
  background: url(../../../apps/myapp/clientlib/styles/images/bg-full.jpg) no-repeat center top;
  width: 100%;
}
```

### Een bibliotheek gebruiken voor specifieke mobiele groepen {#using-a-library-for-specific-mobile-groups}

Gebruik de `channels` eigenschap van een clientbibliotheekmap om de mobiele groep te identificeren die de bibliotheek gebruikt. De `channels` Deze eigenschap is nuttig wanneer bibliotheken van dezelfde categorie zijn ontworpen voor verschillende apparaatmogelijkheden.

Als u een clientbibliotheekmap wilt koppelen aan een apparaatgroep, voegt u een eigenschap toe aan uw `cq:ClientLibraryFolder` knooppunt met de volgende kenmerken:

* **Naam:** kanalen
* **Type:** String[]
* **Waarden:** De naam van de mobiele groep. Als u de bibliotheekmap wilt uitsluiten van een groep, plaatst u een uitroepteken (&quot;!&quot;) vóór de naam.

In de volgende tabel wordt bijvoorbeeld de waarde van de `channels` eigenschap voor elke clientbibliotheekmap van het dialoogvenster `cq.widgets` categorie:

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

AEM maakt het mogelijk om af te spelen op preprocessoren en schepen met ondersteuning voor [YUI-compressor](https://github.com/yui/yuicompressor#yui-compressor---the-yahoo-javascript-and-css-compressor) voor CSS en JavaScript en [Google Closure Compiler (GCC)](https://developers.google.com/closure/compiler/) voor JavaScript waarvoor YUI is ingesteld als AEM standaardvoorprocessor.

Met de aanpasbare voorprocessoren kunt u flexibel gebruik maken, waaronder:

* ScriptProcessors definiëren die scriptbronnen kunnen verwerken
* Processors kunnen worden geconfigureerd met opties
* Processors kunnen worden gebruikt voor minificatie, maar ook voor niet-minieme gevallen
* Clientlib kan bepalen welke processor moet worden gebruikt

>[!NOTE]
>
>AEM gebruikt standaard de YUI-compressor. Zie de [GitHub-documentatie voor YUI-compressor](https://github.com/yui/yuicompressor/issues) voor een lijst van bekende problemen. Het schakelen naar GCC-compressor voor bepaalde clientlibs kan een aantal problemen oplossen die tijdens het gebruik van YUI zijn waargenomen.

>[!CAUTION]
>
>Plaats geen geminiateerde bibliotheek in een clientbibliotheek. Geef in plaats daarvan de onbewerkte bibliotheek op en gebruik de opties van de voorprocessoren als miniatuurafbeelding vereist is.

### Gebruik {#usage}

U kunt kiezen om de configuratie van preprocessoren per clientbibliotheek of systeembreed te configureren.

* Eigenschappen voor meerdere waarden toevoegen `cssProcessor` en `jsProcessor` op het clientbibliotheekknooppunt

* Of definieer de standaardconfiguratie van het systeem via de **HTML Library Manager** OSGi-configuratie

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

Voor meer informatie over GCC-opties raadpleegt u de [GCC-documentatie](https://developers.google.com/closure/compiler/docs/compilation_levels).

### Systeemstandaardminiatuur instellen {#set-system-default-minifier}

YUI wordt geplaatst als standaardminifier in AEM. Voer de volgende stappen uit om dit te wijzigen in GCC.

1. Ga naar Apache Felix Config Manager op [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr)
1. De opdracht Zoeken en bewerken **Adobe Granite HTML Library Manager**.
1. De optie **Minieren** (als deze optie nog niet is ingeschakeld).
1. De waarde instellen **Standaardconfiguratie JS-processor** tot `min:gcc`.

   Opties kunnen worden doorgegeven als deze bijvoorbeeld met een puntkomma worden gescheiden. `min:gcc;obfuscate=true`.

1. Klikken **Opslaan** om de wijzigingen op te slaan

## Foutopsporingsgereedschappen {#debugging-tools}

AEM beschikt over verschillende gereedschappen voor foutopsporing en het testen van clientbibliotheekmappen.

### Zie ingesloten bestanden {#see-embedded-files}

Als u de oorsprong van ingesloten code wilt traceren of wilt controleren of ingesloten clientbibliotheken de verwachte resultaten opleveren, kunt u de namen zien van de bestanden die bij uitvoering worden ingesloten. Als u de bestandsnamen wilt weergeven, voegt u de opdracht `debugClientLibs=true` aan de URL van uw webpagina. De gegenereerde bibliotheek bevat `@import` in plaats van de ingesloten code.

In het voorbeeld in het vorige [Code van andere bibliotheken insluiten](/help/sites-developing/clientlibs.md#embedding-code-from-other-libraries) de `/etc/client/libraries/myclientlibs/publicmain` clientbibliotheekmap sluit de `/apps/myapp/clientlib` clientbibliotheekmap. Als u de parameter aan de webpagina toevoegt, wordt de volgende koppeling in de broncode van de webpagina gemaakt:

```xml
<link rel="stylesheet" href="/etc/clientlibs/mycientlibs/publicmain.css">
```

Het openen van de `publicmain.css` het dossier openbaart de volgende code:

```xml
@import url("/apps/myapp/clientlib/styles/main.css");
```

1. Voeg in het adresvak van uw webbrowser de volgende tekst toe aan de URL van uw HTML:

   `?debugClientLibs=true`
1. Bekijk de paginabron wanneer de pagina wordt geladen.
1. Klik op de koppeling die wordt opgegeven als de href voor het koppelingselement om het bestand te openen en de broncode weer te geven.

### Clientbibliotheken detecteren {#discover-client-libraries}

De `/libs/cq/granite/components/dumplibs/dumplibs` genereert een pagina met informatie over alle clientbibliotheekmappen op het systeem. De `/libs/granite/ui/content/dumplibs` knooppunt heeft de component als een brontype. Als u de pagina wilt openen, gebruikt u de volgende URL (waarbij u de host en poort naar wens wijzigt):

`https://<host>:<port>/libs/granite/ui/content/dumplibs.test.html`

Tot de gegevens behoren het bibliotheekpad en -type (CSS of JS) en de waarden van de bibliotheekkenmerken, zoals categorieën en afhankelijkheden. In de volgende tabellen op de pagina worden de bibliotheken in elke categorie en elk kanaal weergegeven.

### Zie Gegenereerde uitvoer {#see-generated-output}

De `dumplibs` component omvat een testselecteur die de broncode toont die voor wordt geproduceerd `ui:includeClientLib` -tags. De pagina bevat code voor verschillende combinaties van js-, css- en themakenmerken.

1. Gebruik een van de volgende methoden om de pagina Uitvoer testen te openen:

   * Van de `dumplibs.html` pagina, klikt u op de koppeling in het dialoogvenster **Klik hier voor testen van uitvoer** tekst.

   * Open de volgende URL in uw webbrowser (gebruik indien nodig een andere host en poort):

      * `http://<host>:<port>/libs/granite/ui/content/dumplibs.html`

   Op de standaardpagina wordt uitvoer weergegeven voor tags zonder waarde voor het categoriekenmerk.

1. Als u de uitvoer voor een categorie wilt zien, typt u de waarde van de clientbibliotheek `categories` eigenschap en klik op **Query verzenden**.

## Bibliotheekverwerking configureren voor ontwikkeling en productie {#configuring-library-handling-for-development-and-production}

De de dienstprocessen van de Manager van de Bibliotheek van HTML `cq:ClientLibraryFolder` -tags en genereert de bibliotheken bij uitvoering. Het type van milieu, ontwikkeling of productie, bepaalt hoe u de dienst zou moeten vormen:

* Meer beveiliging: foutopsporing uitschakelen
* Prestaties verbeteren: witruimte verwijderen en bibliotheken comprimeren.
* Leesbaarheid verbeteren: spaties opnemen en niet comprimeren.

Voor informatie over het vormen van de dienst, zie [AEM HTML Library Manager](/help/sites-deploying/osgi-configuration-settings.md#aemhtmllibrarymanager).
