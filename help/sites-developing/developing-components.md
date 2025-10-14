---
title: Ontwikkelen AEM componenten
description: AEM componenten worden gebruikt om de inhoud die op uw webpagina's beschikbaar is, vast te houden, op te maken en weer te geven.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
docset: aem65
legacypath: /content/docs/en/aem/6-2/develop/components/components-touch-optimized
exl-id: 573cdc36-e9c3-4803-9c4e-cebd0cf0a56f
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '3246'
ht-degree: 0%

---

# Ontwikkelen AEM componenten{#developing-aem-components}

AEM componenten worden gebruikt om de inhoud die op uw webpagina&#39;s beschikbaar is, vast te houden, op te maken en weer te geven.

* Wanneer [&#x200B; auteurspagina&#39;s &#x200B;](/help/sites-authoring/default-components.md), de componenten de auteurs toestaan om de inhoud uit te geven en te vormen.

   * Wanneer het construeren van a [&#x200B; Commerce &#x200B;](/help/commerce/cif-classic/administering/ecommerce.md) plaats kunnen de componenten, bijvoorbeeld, informatie van de catalogus verzamelen en teruggeven.
Zie [&#x200B; Ontwikkelend eCommerce &#x200B;](/help/commerce/cif-classic/developing/ecommerce.md) voor meer informatie.

   * Wanneer het construeren van de plaats van a [&#x200B; Gemeenschappen &#x200B;](/help/communities/author-communities.md) kunnen de componenten informatie aan verstrekken en informatie van uw bezoekers verzamelen.
Zie [&#x200B; het Ontwikkelen van Gemeenschappen &#x200B;](/help/communities/communities.md) voor meer informatie.

* In de publicatie-instantie renderen de componenten uw inhoud en presenteren deze zoals u nodig hebt aan uw websitebezoekers.

>[!NOTE]
>
>Deze pagina is een voortzetting van het document [&#x200B; AEM Componenten - de Grondbeginselen &#x200B;](/help/sites-developing/components-basics.md).

>[!CAUTION]
>
>Onderstaande componenten `/libs/cq/gui/components/authoring/dialog` zijn alleen bestemd voor gebruik in de Editor (dialoogvensters met componenten in Authoring). Als ze elders worden gebruikt (bijvoorbeeld in een wizard), gedragen ze zich mogelijk niet naar behoren.

## Codevoorbeelden {#code-samples}

Deze pagina bevat de referentiedocumentatie (of koppelingen naar referentiedocumentatie) die vereist is voor het ontwikkelen van nieuwe componenten voor AEM. Zie [&#x200B; het Ontwikkelen AEM Componenten - de Steekproeven van de Code &#x200B;](/help/sites-developing/developing-components-samples.md) voor sommige praktische voorbeelden.

## Structuur {#structure}

De basisstructuur van een component is behandeld op de pagina [&#x200B; Componenten AEM - de Grondbeginselen &#x200B;](/help/sites-developing/components-basics.md#structure). In dat document worden zowel de aanraakinterface als de klassieke gebruikersinterface behandeld. Zelfs als u niet de klassieke montages in uw nieuwe component te hoeven gebruiken kan het helpen om zich van hen bewust te zijn wanneer het erven van bestaande componenten.

## Bestaande componenten en dialoogvensters uitbreiden {#extending-existing-components-and-dialogs}

Afhankelijk van de component u wilt uitvoeren, zou het mogelijk kunnen zijn om een bestaande instantie uit te breiden of aan te passen, eerder dan het bepalen van en het ontwikkelen van de volledige [&#x200B; structuur &#x200B;](#structure) van kras.

Wanneer u een bestaande component of een bestaand dialoogvenster uitbreidt of aanpast, kunt u de volledige structuur of de structuur die voor het dialoogvenster is vereist, kopiëren of repliceren voordat u de wijzigingen aanbrengt.

### Een bestaande component uitbreiden {#extending-an-existing-component}

Het uitbreiden van een bestaande component kan met [&#x200B; Hiërarchie van het Type van Middel &#x200B;](/help/sites-developing/components-basics.md#component-hierarchy-and-inheritance) en de verwante overervingsmechanismen worden bereikt.

>[!NOTE]
>
>Componenten kunnen ook opnieuw worden gedefinieerd met een bedekking op basis van de logica van het zoekpad. Nochtans, in zulk geval, wordt de [&#x200B; Verschuivende Fusie van het Middel &#x200B;](/help/sites-developing/sling-resource-merger.md) niet teweeggebracht en `/apps` moet de volledige bekleding bepalen.

>[!NOTE]
>
>De [&#x200B; component van het inhoudsfragment &#x200B;](/help/sites-developing/customizing-content-fragments.md) kan ook worden aangepast en worden uitgebreid, hoewel de volledige structuur en de verhoudingen met Assets moeten worden overwogen.

### Dialoogvenster Bestaande componenten aanpassen {#customizing-a-existing-component-dialog}

Het is ook mogelijk om de de componentendialoog van a *met voeten te treden* gebruikend de [&#x200B; Verschuivende Fusie van het Middel &#x200B;](/help/sites-developing/sling-resource-merger.md) en het bepalen van het bezit `sling:resourceSuperType`.

Dit betekent dat u alleen de vereiste verschillen opnieuw hoeft te definiëren in plaats van het volledige dialoogvenster opnieuw te definiëren (met `sling:resourceSuperType`). Deze methode wordt nu aanbevolen voor het uitbreiden van een componentdialoogvenster

Zie de [&#x200B; Verschuivende Fusie van het Middel &#x200B;](/help/sites-developing/sling-resource-merger.md) voor meer details.

## Opmaak definiëren {#defining-the-markup}

Uw component zal met [&#x200B; HTML &#x200B;](https://www.w3schools.com/htmL/html_intro.asp) worden teruggegeven. Uw component moet de HTML definiëren die nodig is om de vereiste inhoud te nemen en deze vervolgens naar wens weer te geven, zowel in de auteur- als in de publicatieomgeving.

### De HTML Sjabloontaal gebruiken {#using-the-html-template-language}

De [&#x200B; Templating Templating Taal van de HTML (HTML) &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html?lang=nl-NL), die met AEM 6.0 wordt geïntroduceerd, neemt de plaats van JSP (de Pagina&#39;s van JavaServer) als aangewezen en geadviseerd server-zijmalplaatjesysteem voor HTML. Voor webontwikkelaars die robuuste bedrijfswebsites moeten maken, helpt HTL om meer beveiliging en ontwikkelingsefficiëntie te bereiken.

>[!NOTE]
>
>Hoewel zowel HTML als JSP voor het ontwikkelen van componenten kunnen worden gebruikt, zullen wij ontwikkeling met HTML op deze pagina illustreren, aangezien het de geadviseerde scripting taal voor AEM is.

## De Content Logic ontwikkelen {#developing-the-content-logic}

Deze optionele logica selecteert en/of berekent de inhoud die moet worden gerenderd. Deze wordt aangeroepen vanuit HTML-expressies met het juiste gebruik-API-patroon.

Het mechanisme om logica en verschijning te scheiden helpt verduidelijken wat voor een bepaalde mening wordt vereist. Het staat ook verschillende logica voor verschillende meningen van het zelfde middel toe.

### Java gebruiken {#using-java}

[&#x200B; HTML Java gebruiken-API laat een HTML- dossier toe om helpermethodes in een klasse van douaneJava &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-htl/content/java-use-api.html?lang=nl-NL) toegang te hebben. Hiermee kunt u Java-code gebruiken om de logica voor het selecteren en configureren van de componentinhoud te implementeren.

### JavaScript gebruiken {#using-javascript}

[&#x200B; HTML JavaScript gebruiken-API laat een HTML- dossier toe om tot helpercode toegang te hebben die in JavaScript &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-htl/content/java-use-api.html?lang=nl-NL) wordt geschreven. Hiermee kunt u JavaScript-code gebruiken om de logica voor het selecteren en configureren van de componentinhoud te implementeren.

### Client-Side HTML-bibliotheken gebruiken {#using-client-side-html-libraries}

Moderne websites zijn sterk afhankelijk van verwerking op de client door complexe JavaScript- en CSS-code. Het organiseren en optimaliseren van het gebruik van deze code kan een ingewikkeld probleem zijn.

Om met deze kwestie te helpen behandelen, AEM verstrekt **Cliënt-zijOmslagen van de Bibliotheek**, die u uw cliënt-zijcode in de bewaarplaats laten opslaan, het in categorieën organiseren en bepalen wanneer en hoe elke categorie van code aan de cliënt moet worden gediend. Het client-side bibliotheeksysteem zorgt vervolgens voor het maken van de juiste koppelingen in de uiteindelijke webpagina om de juiste code te laden.

Lees [&#x200B; Gebruikend de Bibliotheken van de HTML van client-zij &#x200B;](/help/sites-developing/clientlibs.md) voor meer informatie.

## Werking bewerken configureren {#configuring-the-edit-behavior}

U kunt het bewerkingsgedrag van een component configureren, inclusief kenmerken zoals handelingen die beschikbaar zijn voor de component, kenmerken van de plaatsingseditor en listeners die betrekking hebben op gebeurtenissen in de component. De configuratie wordt gebruikt voor zowel de aanraakinterface als de klassieke gebruikersinterface, maar met bepaalde specifieke verschillen.

Het [&#x200B; geeft gedrag van een component uit wordt gevormd &#x200B;](/help/sites-developing/components-basics.md#edit-behavior) door a `cq:editConfig` knoop van type `cq:EditConfig` onder de componentenknoop (van type `cq:Component`) toe te voegen en door specifieke eigenschappen en kindknopen toe te voegen.

## Het gedrag Voorvertoning configureren {#configuring-the-preview-behavior}

Het [&#128279;](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/api/WCMMode.html) koekje van de Wijze WCM wordt geplaatst wanneer het schakelen naar **3&rbrace; wijze van de Voorproef &lbrace;zelfs wanneer de pagina niet wordt verfrist.**

Voor componenten met een teruggeven die voor de Wijze van WCM gevoelig zijn, moeten zij worden bepaald om zich specifiek te verfrissen, dan zich op de waarde van het koekje baseren.

>[!NOTE]
>
>In aanraking-toegelaten UI slechts worden de waarden `EDIT` en `PREVIEW` gebruikt voor het [&#128279;](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/api/WCMMode.html) koekje van de Wijze WCM.

## Een dialoogvenster maken en configureren {#creating-and-configuring-a-dialog}

Dialogen worden gebruikt om auteur toe te staan om met de component in wisselwerking te staan. Het gebruiken van een dialoog staat auteurs en/of beheerders toe om inhoud uit te geven, de component te vormen of ontwerpparameters te bepalen (gebruikend de Dialoog van het Ontwerp van de a [&#128279;](#creating-and-configuring-a-design-dialog))

### Gebruikersinterface voor koralen en graniet {#coral-ui-and-granite-ui}

[&#x200B; Koraal UI &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/coral-ui/coralui3/index.html) en [&#x200B; graniet UI &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html) bepaalt het moderne blik en het gevoel van AEM.

[&#x200B; graniet UI verstrekt een grote waaier van de basiscomponenten (widgets) &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html) nodig om uw dialoog over het auteursmilieu tot stand te brengen. Indien nodig kunt u deze selectie uitbreiden en [&#x200B; uw eigen widget &#x200B;](#creatinganewwidget) creëren.

Zie voor meer informatie:

* Koraalinterface

   * Biedt een consistente gebruikersinterface voor alle cloudoplossingen
   * [Concepten van de AEM interface met aanraakfuncties - koraalinterface](/help/sites-developing/touch-ui-concepts.md#coral-ui)
   * [&#x200B; Koraal UI Gids &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/coral-ui/coralui3/index.html)

* Graniet-interface

   * Verstrekt de prijsverhoging van de Koraal UI die in het Verdelen componenten voor de bouw van consoles UI en dialogen wordt verpakt
   * [Concepten van de AEM interface met aanraakfuncties - graniet-interface](/help/sites-developing/touch-ui-concepts.md#coral-ui)
   * [&#x200B; de Documentatie van graniet UI &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html)

>[!NOTE]
>
>Wegens de aard van de componenten van Granite UI (en verschillen aan ExtJS widgets), zijn er sommige verschillen tussen hoe de componenten met aanraking-toegelaten UI en [&#x200B; klassieke UI &#x200B;](/help/sites-developing/developing-components-classic.md) in wisselwerking staan.

### Een nieuw dialoogvenster maken {#creating-a-new-dialog}

Dialoogvensters voor de interface met aanraakbediening:

* hebben de naam `cq:dialog` .
* worden gedefinieerd als een `nt:unstructured` -knooppunt met de eigenschap `sling:resourceType` ingesteld.

* bevinden zich onder hun `cq:Component` -node en naast de componentdefinitie.
* worden op de server weergegeven (als Sling-componenten), op basis van hun inhoudsstructuur en de eigenschap `sling:resourceType` .
* gebruik het Granite UI-framework.
* bevatten een knoopstructuur die de gebieden binnen de dialoog beschrijft.

   * deze knooppunten hebben de eigenschap `nt:unstructured` required `sling:resourceType` .

Een voorbeeld van een knooppuntstructuur kan zijn:

```xml
newComponent (cq:Component)
  cq:dialog (nt:unstructured)
    content
      layout
      items
        column
          items
            file
            description
```

Het aanpassen van een dialoog is gelijkaardig aan het ontwikkelen van een component aangezien de dialoog zelf een component is (namelijk prijsverhoging die door een componentenmanuscript samen met gedrag/stijl door een cliëntbibliotheek wordt teruggegeven).

Zie voor voorbeelden:

* `/libs/foundation/components/text/cq:dialog`
* `/libs/foundation/components/download/cq:dialog`

>[!NOTE]
>
>Als er voor een component geen dialoogvenster is gedefinieerd voor de interface met aanraakbediening, wordt het klassieke dialoogvenster UI gebruikt als fallback binnen een compatibiliteitslaag. Als u een dergelijk dialoogvenster wilt aanpassen, moet u het dialoogvenster voor klassieke gebruikersinterface aanpassen. Zie [&#x200B; AEM Componenten voor Klassieke UI &#x200B;](/help/sites-developing/developing-components-classic.md).

### Dialoogvenstervelden aanpassen {#customizing-dialog-fields}

>[!NOTE]
>
>Zie:
>
>* De AEM Gems zitting op [&#x200B; Aanpassen de Gebieden van de Dialoog &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2015/aem-customizing-dialog-fields-in-touch-ui.html?lang=nl-NL).
>* de verwante steekproefcode die onder [&#x200B; Steekproef van de Code wordt behandeld - hoe te de Gebieden van de Dialoog aanpassen &#x200B;](/help/sites-developing/developing-components-samples.md#code-sample-how-to-customize-dialog-fields).
>

#### Een nieuw veld maken {#creating-a-new-field}

Widgets voor de interface met aanraakbediening worden geïmplementeerd als graniet-UI-componenten.

Om een widget voor gebruik in een componentendialoogvakje voor aanraking-toegelaten UI te creëren vereist u [&#x200B; een graniet UI gebiedscomponent &#x200B;](/help/sites-developing/granite-ui-component.md) creëren.

>[!NOTE]
>
>Voor volledige details over granite UI, zie de [&#x200B; documentatie van graniet UI &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html).

Als u het dialoogvenster beschouwt als een eenvoudige container voor een formulierelement, kunt u ook de primaire inhoud van het dialoogvenster zien als formuliervelden. Voor het maken van een formulierveld moet u een brontype maken. Dit is hetzelfde als het maken van een component. Om u in die taak te helpen, biedt granite UI een generische gebiedscomponent aan om van (het gebruiken van `sling:resourceSuperType`) te erven:

`/libs/granite/ui/components/coral/foundation/form/field`

Specifieker verstrekt UI een waaier van gebiedscomponenten die voor gebruik in dialogen (of, meer in het algemeen, in [&#x200B; vormen &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/components/foundation/form/index.html)) geschikt zijn.

>[!NOTE]
>
>Dit verschilt van de klassieke UI, waar widgets door `cq:Widgets` knopen worden vertegenwoordigd, elk met een bepaalde `xtype` om het verband met hun overeenkomstige widget te vestigen ExtJS. Vanuit implementatiestandpunt zijn deze widgets weergegeven aan de clientzijde door het ExtJS-framework.

Zodra u uw middeltype hebt gecreeerd, kunt u uw gebied concretiseren door een nieuw knooppunt in uw dialoog toe te voegen, met het bezit `sling:resourceType` dat naar het middeltype verwijst u net hebt geïntroduceerd.

#### Een clientbibliotheek maken voor stijl en gedrag {#creating-a-client-library-for-style-and-behavior}

Als u het stileren en het gedrag voor uw component wilt bepalen, kunt u een specifieke [&#x200B; cliëntbibliotheek &#x200B;](/help/sites-developing/clientlibs.md) tot stand brengen die uw douane CSS/LESS en JS bepaalt.

Als u de clientbibliotheek alleen voor het dialoogvenster van de component wilt laden (dat wil zeggen dat deze niet voor een andere component wordt geladen), moet u de eigenschap `extraClientlibs` van het dialoogvenster instellen op de categorienaam van de clientbibliotheek die u hebt gemaakt. Dit is aan te raden als uw clientbibliotheek erg groot is en/of als uw veld specifiek is voor dat dialoogvenster en niet nodig is in andere dialoogvensters.

Als u de clientbibliotheek voor alle dialoogvensters wilt laden, stelt u de categorie-eigenschap van de clientbibliotheek in op `cq.authoring.dialog` . Dit is de categorienaam van de clientbibliotheek die standaard wordt opgenomen wanneer alle dialoogvensters worden weergegeven. U wilt dat doen als uw clientbibliotheek klein is en/of uw veld algemeen is en opnieuw kan worden gebruikt in andere dialoogvensters.

Zie voor een voorbeeld:

* `cqgems/customizingfield/components/colorpicker/clientlibs`

   * verstrekt door de [&#x200B; Steekproef van de Code &#x200B;](/help/sites-developing/developing-components-samples.md#code-sample-how-to-customize-dialog-fields)

#### Een veld uitbreiden (overnemen van) {#extending-inheriting-from-a-field}

Afhankelijk van uw vereisten kunt u:

* Een bepaald veld voor een graniet-interface uitbreiden naar componentovererving ( `sling:resourceSuperType`)
* Een bepaalde widget uitbreiden vanuit de onderliggende widgetbibliotheek (als er Granite UI is, is dit Coral UI), door de widgetbibliotheek-API (JS/CSS-overerving) te volgen

#### Toegang tot dialoogvelden {#access-to-dialog-fields}

U kunt ook rendervoorwaarden ( `rendercondition` ) gebruiken om te bepalen wie toegang heeft tot specifieke tabbladen/velden in het dialoogvenster, bijvoorbeeld:

```xml
+ mybutton
  - sling:resourceType = granite/ui/components/coral/foundation/button
  + rendercondition
    - sling:resourceType = myapp/components/renderconditions/group
    - groups = ["administrators"]
```

### Veldgebeurtenissen afhandelen {#handling-field-events}

De methode om gebeurtenissen op dialooggebieden te behandelen wordt nu gedaan met [&#x200B; luisteraars in een bibliotheek van de douanecliënt &#x200B;](#listeners-in-a-custom-client-library). Dit is een verandering van de oudere methode om [&#x200B; luisteraars in de inhoudsstructuur &#x200B;](#listenersinthecontentstructureclassicui) te hebben.

#### Listeners in een aangepaste clientbibliotheek {#listeners-in-a-custom-client-library}

Om logica in uw gebied te injecteren, zou u moeten:

1. Heb uw gebied duidelijk met een bepaalde CSS klasse (de *haak*).
1. Definieer in uw clientbibliotheek een JS-listener die is gekoppeld aan de naam van die CSS-klasse (dit zorgt ervoor dat uw aangepaste logica alleen binnen het bereik van uw veld valt en niet van invloed is op andere velden van hetzelfde type).

Hiervoor moet u weten welke onderliggende widgetbibliotheek u wilt gebruiken. Zie de [&#x200B; documentatie van de Koraal UI &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/coral-ui/coralui3/index.html) om te identificeren aan welke gebeurtenis u wilt reageren. Dit lijkt op het proces dat u in het verleden met ExtJS moest uitvoeren: zoek de documentatiepagina van een bepaalde widget en controleer vervolgens de details van de gebeurtenis-API.

Zie voor een voorbeeld:

* `cqgems/customizingfield/components/clientlibs/customizingfield`

   * verstrekt door de [&#x200B; Steekproef van de Code &#x200B;](/help/sites-developing/developing-components-samples.md#code-sample-how-to-customize-dialog-fields)

#### Listeners in de inhoudsstructuur {#listeners-in-the-content-structure}

In de klassieke UI met ExtJS, was het gebruikelijk om luisteraars voor een bepaalde widget in de inhoudsstructuur te hebben. Hetzelfde bereiken in de interface met aanraakbediening is anders dan het bereiken van JS-listenercode (of enige andere code) wordt niet meer gedefinieerd in de inhoud.

De inhoudstructuur beschrijft de semantische structuur; het zou (moeten) niet de aard van de onderliggende widget moeten impliceren. Als u geen JS-code hebt in de inhoudsstructuur, kunt u de implementatiedetails wijzigen zonder de inhoudsstructuur te wijzigen. Met andere woorden, u kunt de widgetbibliotheek wijzigen zonder de inhoudsstructuur aan te raken.

#### Beschikbaarheid van dialoogvenster vaststellen {#dialog-ready}

Als u een aangepaste JavaScript hebt die alleen moet worden uitgevoerd wanneer het dialoogvenster beschikbaar en gereed is, moet u luisteren naar de gebeurtenis `dialog-ready` .

Deze gebeurtenis wordt geactiveerd wanneer het dialoogvenster wordt geladen (of opnieuw wordt geladen) en klaar voor gebruik is. Dit houdt in dat telkens wanneer er een wijziging (maken/bijwerken) plaatsvindt in de DOM van het dialoogvenster.

`dialog-ready` kan worden gebruikt om in aangepaste JavaScript-code die aanpassingen uitvoert op de velden in een dialoogvenster of vergelijkbare taken, aan elkaar te koppelen.

### Veldvalidatie {#field-validation}

#### Verplicht veld {#mandatory-field}

Als u een bepaald veld wilt markeren als een verplicht veld, stelt u de volgende eigenschap in op het inhoudsknooppunt van het veld:

* Naam: `required`
* Type: `Boolean`

Zie voor een voorbeeld:

```xml
/libs/foundation/components/page/cq:dialog/content/items/tabs/items/basic/items/column/items/title/items/title
```

#### Veldvalidatie (graniet-UI) {#field-validation-granite-ui}

Veldvalidatie in de gebruikersinterface van Granite en de componenten van de gebruikersinterface van Granite (equivalent aan widgets) wordt uitgevoerd met de API `foundation-validation` . [&#x200B; zie de `foundation-valdiation` documentatie van Granite voor details.](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/clientlibs/foundation/js/validation/index.html)

Zie voor voorbeelden:

* `cqgems/customizingfield/components/clientlibs/customizingfield/js/validations.js`

   * verstrekt door de [&#x200B; Steekproef van de Code &#x200B;](/help/sites-developing/developing-components-samples.md#code-sample-how-to-customize-dialog-fields)

* `/libs/cq/gui/components/authoring/dialog/clientlibs/dialog/js/validations.js`

## Een ontwerpdialoogvenster maken en configureren {#creating-and-configuring-a-design-dialog}

De dialoog van het Ontwerp wordt verstrekt wanneer een component ontwerpdetails heeft die in [&#x200B; Wijze van het Ontwerp &#x200B;](/help/sites-authoring/default-components-designmode.md) kunnen worden uitgegeven.

De definitie is zeer gelijkaardig aan dat van a [&#x200B; dialoog die voor het uitgeven van inhoud &#x200B;](#creating-a-new-dialog) wordt gebruikt, met het verschil dat het als knoop wordt bepaald:

* Node name: `cq:design_dialog`
* Type: `nt:unstructured`

## Een Inplace Editor maken en configureren {#creating-and-configuring-an-inplace-editor}

Met een installatieeditor kan de gebruiker inhoud rechtstreeks in de alineasstroom bewerken, zonder dat een dialoogvenster hoeft te worden geopend. De standaardcomponenten Tekst en Titel hebben bijvoorbeeld beide een geïntegreerde editor.

Een plaatsredacteur is niet noodzakelijk/zinvol voor elk componenttype.

Zie [&#x200B; Uitbreidend de Authoring van de Pagina - voeg Nieuwe Inplace Redacteur &#x200B;](/help/sites-developing/customizing-page-authoring-touch.md#add-new-in-place-editor) voor meer informatie toe.

## De werkbalk Component aanpassen {#customizing-the-component-toolbar}

De [&#x200B; Toolbar van de Component &#x200B;](/help/sites-developing/touch-ui-structure.md#component-toolbar) geeft de gebruikerstoegang tot een waaier van acties voor de component zoals uitgeven, vormen, kopiëren, en schrappen.

Zie [&#x200B; Uitbreidend de Authoring van de Pagina - voeg Nieuwe Actie aan Toolbar van de Component &#x200B;](/help/sites-developing/customizing-page-authoring-touch.md#add-new-action-to-a-component-toolbar) voor meer informatie toe.

## Een component voor de referentierail configureren (geleend/geleend) {#configuring-a-component-for-the-references-rail-borrowed-lent}

Als uw nieuwe componentenverwijzingen inhoud van andere pagina&#39;s dan u kunt overwegen of u het de **Geleende Inhoud** en **Lent Inhoud** secties van het [**Rail van Verwijzingen**](/help/sites-authoring/basic-handling.md#references) wilt beïnvloeden.

Uit-de-doos AEM slechts de component van de Verwijzing. Om uw component toe te voegen moet u de OSGi bundel **WCM vormen Authoring Configuratie van de Verwijzing van de Inhoud**.

Maak een item in de definitie en geef de component op, samen met de eigenschap die moet worden gecontroleerd. Bijvoorbeeld:

`/apps/<*your-Project*>/components/reference@parentPath`

>[!NOTE]
>
>Wanneer het werken met AEM, zijn er verscheidene methodes om de configuratiemontages voor dergelijke diensten te beheren. Zie [&#x200B; Vormend OSGi &#x200B;](/help/sites-deploying/configuring-osgi.md) voor meer details en geadviseerde praktijken.

## De component inschakelen en toevoegen aan het alineasysteem {#enabling-and-adding-your-component-to-the-paragraph-system}

Nadat het onderdeel is ontwikkeld, moet het zijn ingeschakeld voor gebruik in een geschikt alineasysteem, zodat het op de vereiste pagina&#39;s kan worden gebruikt.

Dit kan gebeuren door:

* het gebruiken van [&#x200B; wijze van het Ontwerp &#x200B;](/help/sites-authoring/default-components-designmode.md) wanneer het uitgeven van een specifieke pagina.
* [&#x200B; die het `components` bezit op het paragraafsysteem van een malplaatje &#x200B;](/help/sites-developing/components-basics.md#adding-your-component-to-the-paragraph-system) bepalen.

## Een alineasysteem configureren, zodat een componentinstantie wordt gemaakt wanneer u een element sleept {#configuring-a-paragraph-system-so-that-dragging-an-asset-creates-a-component-instance}

AEM biedt de mogelijkheid aan om een paragraafsysteem op uw pagina te vormen zodat [&#x200B; een geval van uw nieuwe component automatisch wordt gecreeerd wanneer een gebruiker (aangewezen) activa op een geval van die pagina &#x200B;](/help/sites-authoring/editing-content.md#insertingacomponenttouchoptimizedui) (in plaats van het moeten altijd een lege component aan de pagina) sleept.

Dit gedrag, en de vereiste activa-aan-component verhouding kan worden gevormd:

1. Onder de alinea-definitie van het paginaontwerp. Bijvoorbeeld:

   * `/etc/designs/<myApp>/page/par`

   Een knooppunt maken:

   * Naam: `cq:authoring`
   * Type: `nt:unstructured`

1. Onder dit, creeer een knoop om al activa-aan-component afbeeldingen te houden:

   * Naam: `assetToComponentMapping`
   * Type: `nt:unstructured`

1. Voor elke element-aan-component afbeelding creeer een knoop:

   * Naam: tekst. Het wordt aanbevolen dat de naam het element en het type verwante component aanduidt, bijvoorbeeld de afbeelding
   * Type: `nt:unstructured`

   Elke eigenschap heeft de volgende eigenschappen:

   * `assetGroup` :

      * Type: `String`
      * Waarde: de groep waartoe het gerelateerde element behoort, bijvoorbeeld `media`

   * `assetMimetype`:

      * Type: `String`
      * Waarde: het mime-type van het gerelateerde element, bijvoorbeeld `image/*`

   * `droptarget`:

      * Type: `String`
      * Waarde: het doel voor neerzetten, bijvoorbeeld `image`

   * `resourceType`:

      * Type: `String`
      * Waarde: de gerelateerde componentbron; bijvoorbeeld `foundation/components/image`

   * `type`:

      * Type: `String`
      * Waarde: het type, bijvoorbeeld `Images`

Zie voor voorbeelden:

* `/etc/designs/geometrixx/jcr:content/page/par/cq:authoring`
* `/etc/designs/geometrixx-outdoors/jcr:content/page/par/cq:authoring`
* `/etc/designs/geometrixx-media/jcr:content/article/article-content-par/cq:authoring`

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [&#x200B; open a-project-archetype project op GitHub &#x200B;](https://github.com/adobe/aem-project-archetype)
* Download het project als [&#x200B; een dossier van het PIT &#x200B;](https://github.com/adobe/aem-project-archetype/archive/master.zip)

>[!NOTE]
>
>De automatische verwezenlijking van componenteninstanties kan nu gemakkelijk binnen UI worden gevormd wanneer het gebruiken van [&#x200B; Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=nl-NL) en Bewerkbare Malplaatjes. Zie [&#x200B; Creërend de Malplaatjes van de Pagina &#x200B;](/help/sites-authoring/templates.md#editing-a-template-structure-template-author) voor meer informatie over het bepalen van welke componenten automatisch met bepaalde media types worden geassocieerd.

## De extensie AEM accolades gebruiken {#using-the-aem-brackets-extension}

De [&#x200B; AEM Uitbreiding van Brackets &#x200B;](/help/sites-developing/aem-brackets.md) verstrekt een vlotte werkschema om AEM componenten en cliëntbibliotheken uit te geven. Het is gebaseerd op de [&#128279;](https://brackets.io/) coderedacteur 0&rbrace; Brackets &lbrace;.

De extensie:

* Vereenvoudigt synchronisatie (geen Maven of File Vault vereist) om de efficiëntie van ontwikkelaars te verhogen en helpt ook front-end ontwikkelaars met beperkte AEM kennis om aan projecten deel te nemen.
* Verstrekt wat [&#x200B; HTML &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html?lang=nl-NL) steun, de malplaatjetaal die wordt ontworpen om componentenontwikkeling te vereenvoudigen en veiligheid te verhogen.

>[!NOTE]
>
>Brackets is het aanbevolen mechanisme voor het maken van componenten. Het vervangt CRXDE Lite - creeer de functionaliteit van de Component, die voor klassieke UI werd ontworpen.

## Migreren vanuit een klassieke component {#migrating-from-a-classic-component}

Bij het migreren van een component die is ontworpen voor gebruik met de klassieke UI naar een component die met touch-enabled UI (of slechts of gezamenlijk) kan worden gebruikt zouden de volgende kwesties moeten worden overwogen:

* HTL

   * Het gebruik van [&#x200B; HTML &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html?lang=nl-NL) is niet verplicht, maar als uw component dan moet bijwerken is het een ideale tijd om te overwegen [&#x200B; migrerend van JSP aan HTML &#x200B;](/help/sites-developing/components-basics.md#htl-vs-jsp).

* Onderdelen

   * [`cq:listener`](/help/sites-developing/developing-components.md#migrating-cq-listener-code) -code migreren die klassieke UI-specifieke functies gebruikt
   * De stop van RTE, voor verdere informatie zie [&#x200B; Vormend de Rijke Redacteur van de Tekst &#x200B;](/help/sites-administering/rich-text-editor.md).
   * [&#x200B; migreer `cq:listener` code &#x200B;](#migrating-cq-listener-code) die functies specifiek voor klassieke UI gebruikt

* Dialoogvensters

   * Maak een dialoogvenster voor gebruik in de interface met aanraakbediening. Voor compatibiliteitsdoeleinden kan de interface met aanraakbediening echter gebruikmaken van de definitie van een klassiek dialoogvenster UI, wanneer er geen dialoogvenster is gedefinieerd voor de interface met aanraakbediening.
   * De [&#x200B; AEM Moderniseringshulpmiddelen &#x200B;](/help/sites-developing/modernization-tools.md) worden verstrekt om u te helpen bestaande componenten uitbreiden.
   * [&#x200B; Afbeelding ExtJS aan de Componenten van Granite UI &#x200B;](/help/sites-developing/touch-ui-concepts.md#extjs-and-corresponding-granite-ui-components) verstrekt een geschikt overzicht van xtypes ExtJS en knooptypes van ExtJS met hun gelijkwaardige middeltypes van Granite UI.
   * Het aanpassen van gebieden, voor meer informatie zie de zitting van AEM Gems op [&#x200B; het Aanpassen van de Gebieden van de Dialoog &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2015/aem-customizing-dialog-fields-in-touch-ui.html?lang=nl-NL).
   * Migreer van vtypes aan [&#x200B; bevestiging van graniet UI &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/components/foundation/clientlibs/foundation/js/validation/index.html)
   * Gebruikend JS luisteraars, voor meer informatie zie [&#x200B; Behandelende Gebeurtenissen van het Gebied &#x200B;](#handling-field-events) en de zitting van AEM Gems op [&#x200B; het Aanpassen van de Gebieden van de Dialoog &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2015/aem-customizing-dialog-fields-in-touch-ui.html?lang=nl-NL).

### cq:listenercode migreren {#migrating-cq-listener-code}

Als u een project migreert dat voor klassieke UI werd ontworpen, dan zou `cq:listener` code (en component verwante clientlibs) functies kunnen gebruiken die voor klassieke UI (zoals `CQ.wcm.*`) specifiek zijn. Voor de migratie moet u dergelijke code bijwerken met behulp van de equivalente objecten/functies in de interface met aanraakbediening.

Als uw project volledig wordt gemigreerd naar de interface met aanraakbediening, moet u deze code vervangen om de objecten en functies te gebruiken die relevant zijn voor de interface met aanraakbediening.

Nochtans, als uw project zowel klassieke UI als aanraking-toegelaten UI tijdens de migratieperiode (het gebruikelijke scenario) moet behandelen, dan moet u een schakelaar uitvoeren om de afzonderlijke code te onderscheiden die de aangewezen voorwerpen van verwijzingen voorziet.

Dit schakelaarmechanisme kan als worden uitgevoerd:

```
if (Granite.author) {
    // touch UI
} else {
    // classic UI
}
```

## Uw component documenteren {#documenting-your-component}

Als ontwikkelaar wilt u gemakkelijk toegang tot componentendocumentatie zodat u snel kunt begrijpen:

* Beschrijving
* Beoogd gebruik
* Inhoudsstructuur en eigenschappen
* Toegankelijke API&#39;s en uitbreidingspunten
* En zo verder

Daarom is het eenvoudig om bestaande documentatiemarkering die u binnen de component zelf beschikbaar hebt, te maken.

Plaats een `README.md` -bestand in de componentstructuur. Deze prijsdaling wordt getoond in de [&#x200B; componentenconsole &#x200B;](/help/sites-authoring/default-components-console.md).

![&#x200B; chlimage_1-7 &#x200B;](assets/chlimage_1-7.png)

De gesteunde prijsdaling is het zelfde als dat voor [&#x200B; inhoudsfragmenten &#x200B;](/help/assets/content-fragments/content-fragments-markdown.md).
