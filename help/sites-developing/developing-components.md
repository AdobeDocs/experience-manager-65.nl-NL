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

* Wanneer [ontwerpen, pagina&#39;s](/help/sites-authoring/default-components.md)Met deze componenten kunnen de auteurs de inhoud bewerken en configureren.

   * Wanneer u een [Handel](/help/commerce/cif-classic/administering/ecommerce.md) de componenten kunnen bijvoorbeeld informatie uit de catalogus verzamelen en renderen.
Zie [Ontwikkeling van eCommerce](/help/commerce/cif-classic/developing/ecommerce.md) voor meer informatie .

   * Wanneer u een [Gemeenschappen](/help/communities/author-communities.md) de componenten kunnen informatie aan uw bezoekers verstrekken en informatie van uw bezoekers verzamelen.
Zie [Ontwikkelingsgemeenschappen](/help/communities/communities.md) voor meer informatie .

* In de publicatie-instantie renderen de componenten uw inhoud en presenteren deze zoals u nodig hebt aan uw websitebezoekers.

>[!NOTE]
>
>Deze pagina is een vervolg op het document [Componenten AEM - De basisbeginselen](/help/sites-developing/components-basics.md).

>[!CAUTION]
>
>Onderliggende componenten `/libs/cq/gui/components/authoring/dialog` zijn alleen bedoeld voor gebruik in de Editor (componentdialoogvensters in Authoring). Als ze elders worden gebruikt (bijvoorbeeld in een wizard), gedragen ze zich mogelijk niet naar behoren.

## Codevoorbeelden {#code-samples}

Deze pagina bevat de referentiedocumentatie (of koppelingen naar referentiedocumentatie) die vereist is voor het ontwikkelen van nieuwe componenten voor AEM. Zie [Ontwikkelen AEM componenten - Codevoorbeelden](/help/sites-developing/developing-components-samples.md) voor enkele praktische voorbeelden .

## Structuur {#structure}

De basisstructuur van een component wordt op de pagina bedekt [Componenten AEM - De basisbeginselen](/help/sites-developing/components-basics.md#structure). In dat document worden zowel de aanraakinterface als de klassieke gebruikersinterface behandeld. Zelfs als u niet de klassieke montages in uw nieuwe component te hoeven gebruiken kan het helpen om zich van hen bewust te zijn wanneer het erven van bestaande componenten.

## Bestaande componenten en dialoogvensters uitbreiden {#extending-existing-components-and-dialogs}

Afhankelijk van de component die u wilt implementeren, kan het mogelijk zijn een bestaande instantie uit te breiden of aan te passen in plaats van de gehele instantie te definiëren en te ontwikkelen [structuur](#structure) helemaal niet.

Wanneer u een bestaande component of een bestaand dialoogvenster uitbreidt of aanpast, kunt u de volledige structuur of de structuur die voor het dialoogvenster is vereist, kopiëren of repliceren voordat u de wijzigingen aanbrengt.

### Een bestaande component uitbreiden {#extending-an-existing-component}

Een bestaande component uitbreiden kan worden bereikt met [Hiërarchie van brontype](/help/sites-developing/components-basics.md#component-hierarchy-and-inheritance) en de daarmee samenhangende overervingsmechanismen.

>[!NOTE]
>
>Componenten kunnen ook opnieuw worden gedefinieerd met een bedekking op basis van de logica van het zoekpad. In dat geval echter [Samenvoeging van verkoopbronnen](/help/sites-developing/sling-resource-merger.md) niet geactiveerd is en `/apps` moet de volledige overlay definiëren.

>[!NOTE]
>
>De [inhoudsfragmentcomponent](/help/sites-developing/customizing-content-fragments.md) kunnen ook worden aangepast en uitgebreid, hoewel rekening moet worden gehouden met de volledige structuur en relaties met activa.

### Dialoogvenster Bestaande componenten aanpassen {#customizing-a-existing-component-dialog}

Het is ook mogelijk een *dialoogvenster voor componenten* met de [Samenvoeging van verkoopbronnen](/help/sites-developing/sling-resource-merger.md) en de eigenschap definiëren `sling:resourceSuperType`.

Dit betekent dat u alleen de vereiste verschillen opnieuw hoeft te definiëren in plaats van het volledige dialoogvenster opnieuw te definiëren (met `sling:resourceSuperType`). Deze methode wordt nu aanbevolen voor het uitbreiden van een componentdialoogvenster

Zie de [Samenvoeging van verkoopbronnen](/help/sites-developing/sling-resource-merger.md) voor meer informatie .

## Opmaak definiëren {#defining-the-markup}

Uw component wordt weergegeven met [HTML](https://www.w3schools.com/htmL/html_intro.asp). Uw component moet de HTML definiëren die nodig is om de vereiste inhoud te nemen en deze vervolgens naar wens weer te geven, zowel in de auteur- als in de publicatieomgeving.

### De HTML Sjabloontaal gebruiken {#using-the-html-template-language}

De [HTML Templating Language (HTL)](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html), die met AEM 6.0 is geïntroduceerd, vervangt JSP (JavaServer Pages) als voorkeurssjabloonsysteem en als aanbevolen sjabloonsysteem voor HTML. Voor webontwikkelaars die robuuste bedrijfswebsites moeten maken, helpt HTL om meer beveiliging en ontwikkelingsefficiëntie te bereiken.

>[!NOTE]
>
>Hoewel zowel HTML als JSP voor het ontwikkelen van componenten kunnen worden gebruikt, zullen wij ontwikkeling met HTML op deze pagina illustreren, aangezien het de geadviseerde scripting taal voor AEM is.

## De Content Logic ontwikkelen {#developing-the-content-logic}

Deze optionele logica selecteert en/of berekent de inhoud die moet worden gerenderd. Deze wordt aangeroepen vanuit HTML-expressies met het juiste gebruik-API-patroon.

Het mechanisme om logica en verschijning te scheiden helpt verduidelijken wat voor een bepaalde mening wordt vereist. Het staat ook verschillende logica voor verschillende meningen van het zelfde middel toe.

### Java gebruiken {#using-java}

[Met de HTML Java Use-API kan een HTML-bestand toegang krijgen tot hulplijnmethoden in een aangepaste Java-klasse](https://experienceleague.adobe.com/docs/experience-manager-htl/content/java-use-api.html). Hiermee kunt u Java-code gebruiken om de logica voor het selecteren en configureren van de componentinhoud te implementeren.

### JavaScript gebruiken {#using-javascript}

[Met de HTML JavaScript Use-API kan een HTML-bestand toegang krijgen tot hulplijncode die in JavaScript is geschreven](https://experienceleague.adobe.com/docs/experience-manager-htl/content/java-use-api.html). Hiermee kunt u JavaScript-code gebruiken om de logica voor het selecteren en configureren van de componentinhoud te implementeren.

### Client-Side HTML-bibliotheken gebruiken {#using-client-side-html-libraries}

Moderne websites zijn sterk afhankelijk van verwerking op de client door complexe JavaScript- en CSS-code. Het organiseren en optimaliseren van het gebruik van deze code kan een ingewikkeld probleem zijn.

Om dit probleem te helpen aanpakken, AEM biedt **Client-side bibliotheekmappen**, waarmee u uw code aan de clientzijde in de gegevensopslagruimte kunt opslaan, kunt u deze in categorieën ordenen en bepalen wanneer en hoe elke categorie code aan de client moet worden aangeboden. Het client-side bibliotheeksysteem zorgt vervolgens voor het maken van de juiste koppelingen in de uiteindelijke webpagina om de juiste code te laden.

Lezen [Client-Side HTML-bibliotheken gebruiken](/help/sites-developing/clientlibs.md) voor meer informatie .

## Werking bewerken configureren {#configuring-the-edit-behavior}

U kunt het bewerkingsgedrag van een component configureren, inclusief kenmerken zoals handelingen die beschikbaar zijn voor de component, kenmerken van de plaatsingseditor en listeners die betrekking hebben op gebeurtenissen in de component. De configuratie wordt gebruikt voor zowel de aanraakinterface als de klassieke gebruikersinterface, maar met bepaalde specifieke verschillen.

De [bewerkingsgedrag van een component is geconfigureerd](/help/sites-developing/components-basics.md#edit-behavior) door een `cq:editConfig` knooppunt van type `cq:EditConfig` onder het componentknooppunt (van het type `cq:Component`) en door specifieke eigenschappen en onderliggende knooppunten toe te voegen.

## Het gedrag Voorvertoning configureren {#configuring-the-preview-behavior}

De [WCM-modus](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/api/WCMMode.html) cookie wordt ingesteld wanneer wordt geschakeld naar **Voorvertoning** zelfs als de pagina niet is vernieuwd.

Voor componenten met een teruggeven die voor de Wijze van WCM gevoelig zijn, moeten zij worden bepaald om zich specifiek te verfrissen, dan zich op de waarde van het koekje baseren.

>[!NOTE]
>
>In de interface met aanraakfuncties alleen de waarden `EDIT` en `PREVIEW` worden gebruikt voor de [WCM-modus](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/api/WCMMode.html) cookie.

## Een dialoogvenster maken en configureren {#creating-and-configuring-a-dialog}

Dialogen worden gebruikt om auteur toe te staan om met de component in wisselwerking te staan. In een dialoogvenster kunnen auteurs en/of beheerders inhoud bewerken, de component configureren of ontwerpparameters definiëren (met behulp van een [Ontwerpdialoogvenster](#creating-and-configuring-a-design-dialog))

### Gebruikersinterface voor koralen en graniet {#coral-ui-and-granite-ui}

[Koraalinterface](https://developer.adobe.com/experience-manager/reference-materials/6-5/coral-ui/coralui3/index.html) en [Graniet-interface](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html) de moderne kijk op de AEM bepalen.

[De graniet-interface biedt een groot aantal basiscomponenten (widgets)](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html) nodig zijn om een dialoogvenster over de ontwerpomgeving te maken. Indien nodig kunt u deze selectie uitbreiden en [uw eigen widget maken](#creatinganewwidget).

Zie voor meer informatie:

* Koraalinterface

   * Biedt een consistente gebruikersinterface voor alle cloudoplossingen
   * [Concepten van de AEM interface met aanraakfuncties - koraalinterface](/help/sites-developing/touch-ui-concepts.md#coral-ui)
   * [Handleiding voor koraalinterface](https://developer.adobe.com/experience-manager/reference-materials/6-5/coral-ui/coralui3/index.html)

* Graniet-interface

   * Verstrekt de prijsverhoging van de Koraal UI die in het Verdelen componenten voor de bouw van consoles UI en dialogen wordt verpakt
   * [Concepten van de AEM interface met aanraakfuncties - graniet-interface](/help/sites-developing/touch-ui-concepts.md#coral-ui)
   * [Granite UI-documentatie](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html)

>[!NOTE]
>
>Vanwege de aard van de graniet UI-componenten (en verschillen met de ExtJS-widgets) zijn er enkele verschillen tussen de manier waarop componenten communiceren met de interface met aanraakbediening en de interface [klassieke gebruikersinterface](/help/sites-developing/developing-components-classic.md).

### Een nieuw dialoogvenster maken {#creating-a-new-dialog}

Dialoogvensters voor de interface met aanraakbediening:

* are named `cq:dialog`.
* worden gedefinieerd als een `nt:unstructured` knoop met `sling:resourceType` eigenschap ingesteld.

* onder hun `cq:Component` en naast de componentdefinitie ervan.
* worden op de server weergegeven (als Sling-componenten), op basis van hun inhoudsstructuur en de `sling:resourceType` eigenschap.
* gebruik het Granite UI-framework.
* bevatten een knoopstructuur die de gebieden binnen de dialoog beschrijft.

   * deze knooppunten zijn `nt:unstructured` met de vereiste `sling:resourceType` eigenschap.

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
>Als er voor een component geen dialoogvenster is gedefinieerd voor de interface met aanraakbediening, wordt het klassieke dialoogvenster UI gebruikt als fallback binnen een compatibiliteitslaag. Als u een dergelijk dialoogvenster wilt aanpassen, moet u het dialoogvenster voor klassieke gebruikersinterface aanpassen. Zie [Componenten AEM voor de klassieke gebruikersinterface](/help/sites-developing/developing-components-classic.md).

### Dialoogvenstervelden aanpassen {#customizing-dialog-fields}

>[!NOTE]
>
>Zie:
>
>* de zitting van AEM Gems over [Dialoogvenstervelden aanpassen](https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2015/aem-customizing-dialog-fields-in-touch-ui.html).
>* de desbetreffende steekproefcode die onder [Codevoorbeeld - Hoe te om de Gebieden van de Dialoog aan te passen](/help/sites-developing/developing-components-samples.md#code-sample-how-to-customize-dialog-fields).
>

#### Een nieuw veld maken {#creating-a-new-field}

Widgets voor de interface met aanraakbediening worden geïmplementeerd als graniet-UI-componenten.

Als u een widget wilt maken voor gebruik in een componentdialoogvenster voor de interface met aanraakbediening, moet u: [een graniet UI-veldcomponent maken](/help/sites-developing/granite-ui-component.md).

>[!NOTE]
>
>Voor volledige informatie over de graniet-interface raadpleegt u de [Granite UI-documentatie](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html).

Als u het dialoogvenster beschouwt als een eenvoudige container voor een formulierelement, kunt u ook de primaire inhoud van het dialoogvenster zien als formuliervelden. Voor het maken van een formulierveld moet u een brontype maken. Dit is hetzelfde als het maken van een component. Om u in die taak te helpen, biedt granite UI een generische gebiedscomponent aan om van (het gebruiken van `sling:resourceSuperType`):

`/libs/granite/ui/components/coral/foundation/form/field`

Meer specifiek verstrekt granite UI een waaier van gebiedscomponenten die voor gebruik in dialogen (of, meer in het algemeen, in [formulieren](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/components/foundation/form/index.html)).

>[!NOTE]
>
>Dit verschilt van de klassieke UI, waar widgets door worden vertegenwoordigd `cq:Widgets` knooppunten, elk met een bepaalde `xtype` om de relatie met de bijbehorende ExtJS-widget vast te stellen. Vanuit implementatiestandpunt zijn deze widgets weergegeven aan de clientzijde door het ExtJS-framework.

Zodra u uw middeltype hebt gecreeerd, kunt u uw gebied concretiseren door een nieuw knooppunt in uw dialoog, met het bezit toe te voegen `sling:resourceType` verwijzen naar het middeltype u net hebt geïntroduceerd.

#### Een clientbibliotheek maken voor stijl en gedrag {#creating-a-client-library-for-style-and-behavior}

Als u stijlen en gedrag voor uw component wilt definiëren, kunt u een speciale [clientbibliotheek](/help/sites-developing/clientlibs.md) die uw aangepaste CSS/LESS en JS definieert.

Als u de clientbibliotheek alleen voor het dialoogvenster van de component wilt laden (dat wil zeggen dat deze niet voor een andere component wordt geladen), moet u de eigenschap instellen `extraClientlibs` van het dialoogvenster naar de categorienaam van de clientbibliotheek die u hebt gemaakt. Dit is aan te raden als uw clientbibliotheek erg groot is en/of als uw veld specifiek is voor dat dialoogvenster en niet nodig is in andere dialoogvensters.

Als u de clientbibliotheek voor alle dialoogvensters wilt laden, stelt u de categorie-eigenschap van de clientbibliotheek in op `cq.authoring.dialog`. Dit is de categorienaam van de clientbibliotheek die standaard wordt opgenomen wanneer alle dialoogvensters worden weergegeven. U wilt dat doen als uw clientbibliotheek klein is en/of uw veld algemeen is en opnieuw kan worden gebruikt in andere dialoogvensters.

Zie voor een voorbeeld:

* `cqgems/customizingfield/components/colorpicker/clientlibs`

   * door de [Codevoorbeeld](/help/sites-developing/developing-components-samples.md#code-sample-how-to-customize-dialog-fields)

#### Een veld uitbreiden (overnemen van) {#extending-inheriting-from-a-field}

Afhankelijk van uw vereisten kunt u:

* Een bepaald veld voor een graniet-UI uitbreiden naar componentovererving ( `sling:resourceSuperType`)
* Een bepaalde widget uitbreiden vanuit de onderliggende widgetbibliotheek (als er Granite UI is, is dit Coral UI), door de widgetbibliotheek-API (JS/CSS-overerving) te volgen

#### Toegang tot dialoogvelden {#access-to-dialog-fields}

U kunt ook rendervoorwaarden gebruiken ( `rendercondition`) om te bepalen wie toegang heeft tot specifieke tabbladen/velden in uw dialoogvenster, bijvoorbeeld:

```xml
+ mybutton
  - sling:resourceType = granite/ui/components/coral/foundation/button
  + rendercondition
    - sling:resourceType = myapp/components/renderconditions/group
    - groups = ["administrators"]
```

### Veldgebeurtenissen afhandelen {#handling-field-events}

De methode voor het verwerken van gebeurtenissen in dialoogvelden is nu voltooid met [listeners in een aangepaste clientbibliotheek](#listeners-in-a-custom-client-library). Dit is een wijziging ten opzichte van de oude methode van [listeners in de inhoudsstructuur](#listenersinthecontentstructureclassicui).

#### Listeners in een aangepaste clientbibliotheek {#listeners-in-a-custom-client-library}

Om logica in uw gebied te injecteren, zou u moeten:

1. Laat uw veld gemarkeerd zijn met een bepaalde CSS-klasse (de *haak*).
1. Definieer in uw clientbibliotheek een JS-listener die is gekoppeld aan de naam van die CSS-klasse (dit zorgt ervoor dat uw aangepaste logica alleen binnen het bereik van uw veld valt en niet van invloed is op andere velden van hetzelfde type).

Hiervoor moet u weten welke onderliggende widgetbibliotheek u wilt gebruiken. Zie de [Coral UI-documentatie](https://developer.adobe.com/experience-manager/reference-materials/6-5/coral-ui/coralui3/index.html) om aan te geven op welke gebeurtenis u wilt reageren. Dit lijkt op het proces dat u in het verleden met ExtJS moest uitvoeren: zoek de documentatiepagina van een bepaalde widget en controleer vervolgens de details van de gebeurtenis-API.

Zie voor een voorbeeld:

* `cqgems/customizingfield/components/clientlibs/customizingfield`

   * door de [Codevoorbeeld](/help/sites-developing/developing-components-samples.md#code-sample-how-to-customize-dialog-fields)

#### Listeners in de inhoudsstructuur {#listeners-in-the-content-structure}

In de klassieke UI met ExtJS, was het gebruikelijk om luisteraars voor een bepaalde widget in de inhoudsstructuur te hebben. Hetzelfde bereiken in de interface met aanraakbediening is anders dan het bereiken van JS-listenercode (of enige andere code) wordt niet meer gedefinieerd in de inhoud.

De inhoudstructuur beschrijft de semantische structuur; het zou (moeten) niet de aard van de onderliggende widget moeten impliceren. Als u geen JS-code hebt in de inhoudsstructuur, kunt u de implementatiedetails wijzigen zonder de inhoudsstructuur te wijzigen. Met andere woorden, u kunt de widgetbibliotheek wijzigen zonder de inhoudsstructuur aan te raken.

#### Beschikbaarheid van dialoogvenster vaststellen {#dialog-ready}

Als u een aangepaste JavaScript hebt die alleen moet worden uitgevoerd wanneer het dialoogvenster beschikbaar en gereed is, moet u luisteren naar de `dialog-ready` gebeurtenis.

Deze gebeurtenis wordt geactiveerd wanneer het dialoogvenster wordt geladen (of opnieuw wordt geladen) en klaar voor gebruik is. Dit houdt in dat telkens wanneer er een wijziging (maken/bijwerken) plaatsvindt in de DOM van het dialoogvenster.

`dialog-ready` U kunt dit gebruiken om aangepaste JavaScript-code te koppelen die aanpassingen uitvoert op de velden in een dialoogvenster of vergelijkbare taken.

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

Veldvalidatie in de gebruikersinterface van graniet en de componenten van de gebruikersinterface van graniet (equivalent aan widgets) wordt uitgevoerd met de `foundation-validation` API. [Zie de `foundation-valdiation` Korte documentatie voor meer informatie.](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/clientlibs/foundation/js/validation/index.html)

Zie voor voorbeelden:

* `cqgems/customizingfield/components/clientlibs/customizingfield/js/validations.js`

   * door de [Codevoorbeeld](/help/sites-developing/developing-components-samples.md#code-sample-how-to-customize-dialog-fields)

* `/libs/cq/gui/components/authoring/dialog/clientlibs/dialog/js/validations.js`

## Een ontwerpdialoogvenster maken en configureren {#creating-and-configuring-a-design-dialog}

Het dialoogvenster Ontwerpen wordt weergegeven wanneer een component ontwerpdetails bevat die kunnen worden bewerkt [Ontwerpmodus](/help/sites-authoring/default-components-designmode.md).

De definitie lijkt sterk op die van een [dialoogvenster voor het bewerken van inhoud](#creating-a-new-dialog), met het verschil dat het als knoop wordt gedefinieerd:

* Node name: `cq:design_dialog`
* Type: `nt:unstructured`

## Een Inplace Editor maken en configureren {#creating-and-configuring-an-inplace-editor}

Met een installatieeditor kan de gebruiker inhoud rechtstreeks in de alineasstroom bewerken, zonder dat een dialoogvenster hoeft te worden geopend. De standaardcomponenten Tekst en Titel hebben bijvoorbeeld beide een geïntegreerde editor.

Een plaatsredacteur is niet noodzakelijk/zinvol voor elk componenttype.

Zie [Pagina-authoring uitbreiden - Nieuwe plaatsingseditor toevoegen](/help/sites-developing/customizing-page-authoring-touch.md#add-new-in-place-editor) voor meer informatie .

## De werkbalk Component aanpassen {#customizing-the-component-toolbar}

De [Werkbalk Component](/help/sites-developing/touch-ui-structure.md#component-toolbar) geeft de gebruiker toegang tot een waaier van acties voor de component zoals uitgeven, vormen, kopiëren, en schrappen.

Zie [Pagina-authoring uitbreiden - Nieuwe handeling toevoegen aan een componentwerkbalk](/help/sites-developing/customizing-page-authoring-touch.md#add-new-action-to-a-component-toolbar) voor meer informatie .

## Een component voor de referentierail configureren (geleend/geleend) {#configuring-a-component-for-the-references-rail-borrowed-lent}

Als uw nieuwe component verwijst naar inhoud van andere pagina&#39;s, kunt u overwegen of u het effect wilt hebben op **Geleende inhoud** en **Inhoud van regel** van de [**Verwijzingen**](/help/sites-authoring/basic-handling.md#references) Rail.

Uit-de-doos AEM slechts de component van de Verwijzing. Om uw component toe te voegen moet u de bundel vormen OSGi **Configuratie van WCM-ontwerpnaslaggids**.

Maak een item in de definitie en geef de component op, samen met de eigenschap die moet worden gecontroleerd. Bijvoorbeeld:

`/apps/<*your-Project*>/components/reference@parentPath`

>[!NOTE]
>
>Wanneer het werken met AEM, zijn er verscheidene methodes om de configuratiemontages voor dergelijke diensten te beheren. Zie [OSGi configureren](/help/sites-deploying/configuring-osgi.md) voor meer details en de aanbevolen werkwijzen.

## De component inschakelen en toevoegen aan het alineasysteem {#enabling-and-adding-your-component-to-the-paragraph-system}

Nadat het onderdeel is ontwikkeld, moet het zijn ingeschakeld voor gebruik in een geschikt alineasysteem, zodat het op de vereiste pagina&#39;s kan worden gebruikt.

Dit kan gebeuren door:

* gebruiken [Ontwerpmodus](/help/sites-authoring/default-components-designmode.md) wanneer u een specifieke pagina bewerkt.
* [de definitie van `components` eigenschap in het alineasysteem van een sjabloon](/help/sites-developing/components-basics.md#adding-your-component-to-the-paragraph-system).

## Een alineasysteem configureren, zodat een componentinstantie wordt gemaakt wanneer u een element sleept {#configuring-a-paragraph-system-so-that-dragging-an-asset-creates-a-component-instance}

AEM biedt de mogelijkheid om een alineasysteem op uw pagina te configureren zodat [er wordt automatisch een instantie van de nieuwe component gemaakt wanneer een gebruiker een (geschikt) element naar een instantie van die pagina sleept](/help/sites-authoring/editing-content.md#insertingacomponenttouchoptimizedui) (in plaats van altijd een lege component naar de pagina te slepen).

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

   * `assetGroup`:

      * Type: `String`
      * Waarde: de groep waartoe het gerelateerde actief behoort; bijvoorbeeld `media`

   * `assetMimetype`:

      * Type: `String`
      * Waarde: het mime-type van het gerelateerde element, bijvoorbeeld `image/*`

   * `droptarget`:

      * Type: `String`
      * Waarde: het doel voor neerzetten, bijvoorbeeld `image`

   * `resourceType`:

      * Type: `String`
      * Waarde: de gerelateerde componentbron, bijvoorbeeld `foundation/components/image`

   * `type`:

      * Type: `String`
      * Waarde: het type, bijvoorbeeld `Images`

Zie voor voorbeelden:

* `/etc/designs/geometrixx/jcr:content/page/par/cq:authoring`
* `/etc/designs/geometrixx-outdoors/jcr:content/page/par/cq:authoring`
* `/etc/designs/geometrixx-media/jcr:content/article/article-content-par/cq:authoring`

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [Open aem-project-archetype project op GitHub](https://github.com/adobe/aem-project-archetype)
* Het project downloaden als [een ZIP-bestand](https://github.com/adobe/aem-project-archetype/archive/master.zip)

>[!NOTE]
>
>De automatische verwezenlijking van componenteninstanties kan nu gemakkelijk binnen UI worden gevormd wanneer het gebruiken [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) en bewerkbare sjablonen. Zie [Paginasjablonen maken](/help/sites-authoring/templates.md#editing-a-template-structure-template-author) voor meer informatie over het bepalen van welke componenten automatisch met bepaalde media types worden geassocieerd.

## De extensie AEM accolades gebruiken {#using-the-aem-brackets-extension}

De [Extensie AEM](/help/sites-developing/aem-brackets.md) biedt een vloeiende workflow voor het bewerken van AEM componenten en clientbibliotheken. Het is gebaseerd op de [Haakjes](https://brackets.io/) code-editor.

De extensie:

* Vereenvoudigt synchronisatie (geen Maven of File Vault vereist) om de efficiëntie van ontwikkelaars te verhogen en helpt ook front-end ontwikkelaars met beperkte AEM kennis om aan projecten deel te nemen.
* Bevat enkele [HTL](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html) ondersteuning, de sjabloontaal die is ontworpen om de ontwikkeling van componenten te vereenvoudigen en de beveiliging te verhogen.

>[!NOTE]
>
>Brackets is het aanbevolen mechanisme voor het maken van componenten. Het vervangt CRXDE Lite - creeer de functionaliteit van de Component, die voor klassieke UI werd ontworpen.

## Migreren vanuit een klassieke component {#migrating-from-a-classic-component}

Bij het migreren van een component die is ontworpen voor gebruik met de klassieke UI naar een component die met touch-enabled UI (of slechts of gezamenlijk) kan worden gebruikt zouden de volgende kwesties moeten worden overwogen:

* HTL

   * Gebruik van [HTL](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html) is niet verplicht, maar als uw component moet worden bijgewerkt, is het een ideaal moment om na te denken [migreren van JSP naar HTML](/help/sites-developing/components-basics.md#htl-vs-jsp).

* Onderdelen

   * Migreren [`cq:listener`](/help/sites-developing/developing-components.md#migrating-cq-listener-code) code die klassieke UI-specifieke functies gebruikt
   * RTE-plug-in voor meer informatie, zie [De Rich Text Editor configureren](/help/sites-administering/rich-text-editor.md).
   * [Migreren `cq:listener` code](#migrating-cq-listener-code) die functies gebruikt die specifiek zijn voor de klassieke gebruikersinterface

* Dialoogvensters

   * Maak een dialoogvenster voor gebruik in de interface met aanraakbediening. Voor compatibiliteitsdoeleinden kan de interface met aanraakbediening echter gebruikmaken van de definitie van een klassiek dialoogvenster UI, wanneer er geen dialoogvenster is gedefinieerd voor de interface met aanraakbediening.
   * De [AEM moderniseringsinstrumenten](/help/sites-developing/modernization-tools.md) worden geleverd om u te helpen bestaande componenten uit te breiden.
   * [ExtJS toewijzen aan UI-componenten voor graniet](/help/sites-developing/touch-ui-concepts.md#extjs-and-corresponding-granite-ui-components) verstrekt een geschikt overzicht van xtypes ExtJS en knooptypes van hun gelijkwaardige middeltypes van Granite UI.
   * Velden aanpassen, raadpleeg de sessie AEM Gems over voor meer informatie [Dialoogvenstervelden aanpassen](https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2015/aem-customizing-dialog-fields-in-touch-ui.html).
   * Migreren van typen naar [Graniet UI-validatie](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/components/foundation/clientlibs/foundation/js/validation/index.html)
   * JS-listeners gebruiken, zie voor meer informatie [Veldgebeurtenissen afhandelen](#handling-field-events) en de zitting van AEM Gems over [Dialoogvenstervelden aanpassen](https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2015/aem-customizing-dialog-fields-in-touch-ui.html).

### cq:listenercode migreren {#migrating-cq-listener-code}

Als u een project migreert dat voor klassieke UI werd ontworpen, dan `cq:listener` de code (en component verwante clientlibs) zou functies kunnen gebruiken die voor klassieke UI (zoals `CQ.wcm.*`). Voor de migratie moet u dergelijke code bijwerken met behulp van de equivalente objecten/functies in de interface met aanraakbediening.

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

Een `README.md` in de componentstructuur. Deze markering wordt weergegeven in het dialoogvenster [componentconsole](/help/sites-authoring/default-components-console.md).

![chlimage_1-7](assets/chlimage_1-7.png)

De ondersteunde markering is gelijk aan die voor [inhoudsfragmenten](/help/assets/content-fragments/content-fragments-markdown.md).
