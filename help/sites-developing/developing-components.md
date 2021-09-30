---
title: AEM ontwikkelen
seo-title: Developing AEM Components
description: AEM componenten worden gebruikt om de inhoud die op uw webpagina's beschikbaar is, vast te houden, op te maken en weer te geven.
seo-description: AEM components are used to hold, format, and render the content made available on your webpages.
uuid: 1f39daa6-7277-45a2-adcc-74b58c93b8e4
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
discoiquuid: 8cdb6db4-adaa-4eda-af7d-310a0b44b80b
docset: aem65
legacypath: /content/docs/en/aem/6-2/develop/components/components-touch-optimized
exl-id: 573cdc36-e9c3-4803-9c4e-cebd0cf0a56f
source-git-commit: f2a208acfa28f23cbf63d055c5d28698df476892
workflow-type: tm+mt
source-wordcount: '3485'
ht-degree: 1%

---

# AEM ontwikkelen{#developing-aem-components}

AEM componenten worden gebruikt om de inhoud die op uw webpagina&#39;s beschikbaar is, vast te houden, op te maken en weer te geven.

* Wanneer [authoring pages](/help/sites-authoring/default-components.md), staan de componenten de auteurs toe om de inhoud uit te geven en te vormen.

   * Wanneer het construeren van een [Commerce](/help/commerce/cif-classic/administering/ecommerce.md) plaats kunnen de componenten, bijvoorbeeld, informatie van de catalogus verzamelen en teruggeven.
Zie [eCommerce ontwikkelen](/help/commerce/cif-classic/developing/ecommerce.md) voor meer informatie.

   * Wanneer u een [Communities](/help/communities/author-communities.md)-site samenstelt, kunnen de componenten informatie verschaffen aan en informatie verzamelen van uw bezoekers.
Zie [Gemeenschappen ontwikkelen](/help/communities/communities.md) voor meer informatie.

* In de publicatie-instantie renderen de componenten uw inhoud en presenteren deze zoals u nodig hebt aan uw websitebezoekers.

>[!NOTE]
>
>Deze pagina is een vervolg van het document [AEM Componenten - de Basisbeginselen](/help/sites-developing/components-basics.md).

>[!CAUTION]
>
>Onderliggende componenten `/libs/cq/gui/components/authoring/dialog` zijn alleen bedoeld voor gebruik in de Editor (dialoogvensters met componenten in Authoring). Als ze elders worden gebruikt (bijvoorbeeld in een wizard), gedragen ze zich mogelijk niet naar behoren.

## Codevoorbeelden {#code-samples}

Deze pagina bevat de referentiedocumentatie (of koppelingen naar referentiedocumentatie) die vereist is voor het ontwikkelen van nieuwe componenten voor AEM. Zie [Ontwikkelen AEM Componenten - Codevoorbeelden](/help/sites-developing/developing-components-samples.md) voor enkele praktische voorbeelden.

## Structuur {#structure}

De basisstructuur van een component wordt behandeld op de pagina [AEM Componenten - de Basisbeginselen](/help/sites-developing/components-basics.md#structure). Dat document behandelt zowel de aanraakinterface als de klassieke gebruikersinterface. Zelfs als u niet de klassieke montages in uw nieuwe component te hoeven gebruiken kan het helpen om zich van hen bewust te zijn wanneer het erven van bestaande componenten.

## Bestaande componenten en dialoogvensters uitbreiden {#extending-existing-components-and-dialogs}

Afhankelijk van de component die u wilt implementeren, is het mogelijk een bestaande instantie uit te breiden of aan te passen in plaats van de gehele [structuur](#structure) helemaal vanaf het begin te definiëren en te ontwikkelen.

Wanneer u een bestaande component of een bestaand dialoogvenster uitbreidt of aanpast, kunt u de volledige structuur of de structuur die voor het dialoogvenster is vereist, kopiëren of repliceren voordat u de wijzigingen aanbrengt.

### Een bestaande component uitbreiden {#extending-an-existing-component}

Het uitbreiden van een bestaande component kan met [de Hiërarchie van het Type van Middel](/help/sites-developing/components-basics.md#component-hierarchy-and-inheritance) en de verwante overervingsmechanismen worden bereikt.

>[!NOTE]
>
>Componenten kunnen ook opnieuw worden gedefinieerd met een bedekking op basis van de logica van het zoekpad. In dat geval wordt de [Sling Resource Merger](/help/sites-developing/sling-resource-merger.md) echter niet geactiveerd en moet `/apps` de volledige overlay definiëren.

>[!NOTE]
>
>De [inhoudfragmentcomponent](/help/sites-developing/customizing-content-fragments.md) kan ook worden aangepast en uitgebreid, hoewel de volledige structuur en de verhoudingen met Activa moeten worden overwogen.

### Dialoogvenster Bestaande componenten aanpassen {#customizing-a-existing-component-dialog}

Het is ook mogelijk om een *componentendialoog* met behulp van [Sling Resource Merger](/help/sites-developing/sling-resource-merger.md) met voeten te treden en het bezit `sling:resourceSuperType` te bepalen.

Dit betekent dat u alleen de vereiste verschillen opnieuw hoeft te definiëren in plaats van het volledige dialoogvenster opnieuw te definiëren (met `sling:resourceSuperType`). Deze methode wordt nu aanbevolen voor het uitbreiden van een componentdialoogvenster

Zie [Sling Resource Merger](/help/sites-developing/sling-resource-merger.md) voor meer informatie.

## Opmaak definiëren {#defining-the-markup}

Uw component wordt weergegeven met [HTML](https://www.w3schools.com/htmL/html_intro.asp). Uw component moet de HTML definiëren die nodig is om de vereiste inhoud te nemen en deze vervolgens naar wens weer te geven, zowel in de auteur- als in de publicatieomgeving.

### De HTML-sjabloontaal gebruiken {#using-the-html-template-language}

De [HTML Templating Language (HTL)](https://docs.adobe.com/content/help/en/experience-manager-htl/using/overview.html), geïntroduceerd met AEM 6.0, vervangt JSP (JavaServer Pages) als voorkeurssjabloonsysteem en aanbevolen voor HTML op de server. Voor webontwikkelaars die robuuste bedrijfswebsites moeten maken, helpt HTL om meer beveiliging en ontwikkelingsefficiëntie te bereiken.

>[!NOTE]
>
>Hoewel zowel HTML als JSP voor het ontwikkelen van componenten kunnen worden gebruikt, zullen wij ontwikkeling met HTML op deze pagina illustreren, aangezien het de geadviseerde scripting taal voor AEM is.

## De Content Logic ontwikkelen {#developing-the-content-logic}

Deze optionele logica selecteert en/of berekent de inhoud die moet worden gerenderd. Deze wordt aangeroepen vanuit HTML-expressies met het juiste gebruik-API-patroon.

Het mechanisme om logica en verschijning te scheiden helpt verduidelijken wat voor een bepaalde mening wordt vereist. Het staat ook verschillende logica voor verschillende meningen van het zelfde middel toe.

### Java gebruiken {#using-java}

[De HTML Java Use-API laat een HTML- dossier toe om helpermethodes in een douaneJava klasse](https://helpx.adobe.com/experience-manager/htl/using/use-api-java.html) toegang te hebben. Hierdoor kunt u Java-code gebruiken om de logica voor het selecteren en configureren van de inhoud van de component te implementeren.

### Werken met JavaScript {#using-javascript}

[Met de HTML JavaScript Use-API kan een HTML-bestand toegang krijgen tot hulplijncode die in JavaScript](https://helpx.adobe.com/experience-manager/htl/using/use-api-javascript.html) is geschreven. Hierdoor kunt u JavaScript-code gebruiken om de logica voor het selecteren en configureren van de componentinhoud te implementeren.

### HTML-bibliotheken aan de clientzijde gebruiken {#using-client-side-html-libraries}

Moderne websites zijn sterk afhankelijk van verwerking op de client door complexe JavaScript- en CSS-code. Het organiseren en optimaliseren van het gebruik van deze code kan een ingewikkeld probleem zijn.

Om dit probleem te verhelpen, biedt AEM **Client-side bibliotheekmappen**, waarmee u uw code aan de clientzijde in de opslagplaats kunt opslaan, deze in categorieën kunt indelen en kunt definiëren wanneer en hoe elke categorie code aan de client moet worden verzonden. Het client-side bibliotheeksysteem zorgt vervolgens voor het maken van de juiste koppelingen in de uiteindelijke webpagina om de juiste code te laden.

Lees [HTML-bibliotheken aan de clientzijde gebruiken](/help/sites-developing/clientlibs.md) voor meer informatie.

## Werking bewerken configureren {#configuring-the-edit-behavior}

U kunt het bewerkingsgedrag van een component configureren, inclusief kenmerken zoals handelingen die beschikbaar zijn voor de component, kenmerken van de plaatsingseditor en listeners die betrekking hebben op gebeurtenissen in de component. De configuratie wordt gebruikt voor zowel de aanraakinterface als de klassieke gebruikersinterface, maar met bepaalde specifieke verschillen.

Het [bewerkingsgedrag van een component wordt geconfigureerd](/help/sites-developing/components-basics.md#edit-behavior) door een `cq:editConfig`-knooppunt van het type `cq:EditConfig` onder het componentknooppunt (van het type `cq:Component`) toe te voegen en door specifieke eigenschappen en onderliggende knooppunten toe te voegen.

## Het gedrag Voorvertoning configureren {#configuring-the-preview-behavior}

Het [WCM Modus](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/WCMMode.html) koekje wordt geplaatst wanneer het schakelen aan **Voorproef** wijze zelfs wanneer de pagina niet wordt verfrist.

Voor componenten met een teruggeven die voor de Wijze van WCM gevoelig zijn, moeten zij worden bepaald om zich specifiek te verfrissen, dan zich op de waarde van het koekje baseren.

>[!NOTE]
>
>In de interface met aanraakfuncties worden alleen de waarden `EDIT` en `PREVIEW` gebruikt voor het cookie [WCM Mode](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/WCMMode.html).

## Een dialoogvenster maken en configureren {#creating-and-configuring-a-dialog}

Dialogen worden gebruikt om auteur toe te staan om met de component in wisselwerking te staan. Met behulp van een dialoogvenster kunnen auteurs en/of beheerders inhoud bewerken, de component configureren of ontwerpparameters definiëren (met een [dialoogvenster Ontwerpen](#creating-and-configuring-a-design-dialog))

### Gebruikersinterface voor koralen en graniet {#coral-ui-and-granite-ui}

[Koraal ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/coral-ui/coralui3/index.html) UIand  [Granite ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html) UIbepaalt het moderne beeld en het gevoel van AEM.

[De graniet-interface biedt een groot aantal basiscomponenten (widgets) ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html) die nodig zijn om een dialoogvenster in de ontwerpomgeving te maken. Indien nodig kunt u deze selectie uitbreiden en [uw eigen widget maken](#creatinganewwidget).

Zie voor meer informatie:

* Koraalinterface

   * Biedt een consistente gebruikersinterface voor alle cloudoplossingen
   * [Concepten van de AEM interface met aanraakfuncties - koraalinterface](/help/sites-developing/touch-ui-concepts.md#coral-ui)
   * [Handleiding voor koraal](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/coral-ui/coralui3/index.html)

* Graniet-interface

   * Verstrekt de prijsverhoging van de Koraal UI die in het Verdelen componenten voor de bouw van consoles UI en dialogen wordt verpakt
   * [Concepten van de AEM interface met aanraakfuncties - graniet-interface](/help/sites-developing/touch-ui-concepts.md#coral-ui)
   * [Granite UI-documentatie](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html)

>[!NOTE]
>
>Vanwege de aard van de graniet UI-componenten (en verschillen met de ExtJS-widgets) zijn er enkele verschillen tussen de manier waarop componenten communiceren met de interface met aanraakbediening en de [klassieke UI](/help/sites-developing/developing-components-classic.md).

### Een nieuw dialoogvenster maken {#creating-a-new-dialog}

Dialoogvensters voor de interface met aanraakbediening:

* worden met de naam `cq:dialog` genoemd.
* worden gedefinieerd als een `nt:unstructured`-knooppunt met de eigenschap `sling:resourceType` ingesteld.

* bevinden zich onder hun `cq:Component`-knooppunt en naast hun componentdefinitie.
* worden op de server weergegeven (als Sling-componenten), op basis van hun inhoudsstructuur en de eigenschap `sling:resourceType`.
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

Het aanpassen van een dialoog is gelijkaardig aan het ontwikkelen van een component aangezien de dialoog zelf een component is (d.w.z. prijsverhoging die door een componentenmanuscript samen met gedrag/stijl die door een cliëntbibliotheek wordt verstrekt) wordt teruggegeven.

Zie voor voorbeelden:

* `/libs/foundation/components/text/cq:dialog`
* `/libs/foundation/components/download/cq:dialog`

>[!NOTE]
>
>Als er voor een component geen dialoogvenster is gedefinieerd voor de interface met aanraakbediening, wordt het klassieke dialoogvenster UI gebruikt als fallback binnen een compatibiliteitslaag. Als u een dergelijk dialoogvenster wilt aanpassen, moet u het dialoogvenster voor klassieke gebruikersinterface aanpassen. Zie [AEM Componenten voor de Klassieke UI](/help/sites-developing/developing-components-classic.md).

### Dialoogvenstervelden aanpassen {#customizing-dialog-fields}

>[!NOTE]
>
>Zie:
>
>* De AEM Gems-sessie op [Dialoogvelden aanpassen](https://docs.adobe.com/content/ddc/en/gems/customizing-dialog-fields-in-touch-ui.html).
>* de verwante steekproefcode die onder [de Steekproef van de Code - hoe te de Gebieden van de Dialoog aanpassen](/help/sites-developing/developing-components-samples.md#code-sample-how-to-customize-dialog-fields) wordt behandeld.

>


#### Een nieuw veld maken {#creating-a-new-field}

Widgets voor de interface met aanraakbediening worden geïmplementeerd als graniet-UI-componenten.

Als u een nieuwe widget wilt maken voor gebruik in een componentdialoogvenster voor de interface met aanraakbediening, moet u [een nieuwe graniet-UI-veldcomponent maken](/help/sites-developing/granite-ui-component.md).

>[!NOTE]
>
>Zie de [Granite UI-documentatie](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html) voor meer informatie over de graniet-interface.

Als u het dialoogvenster beschouwt als een eenvoudige container voor een formulierelement, kunt u ook de primaire inhoud van het dialoogvenster zien als formuliervelden. Voor het maken van een nieuw formulierveld moet u een brontype maken; dit is hetzelfde als het maken van een nieuwe component. Om u in die taak te helpen, biedt granite UI een generische gebiedscomponent aan om van (het gebruiken van `sling:resourceSuperType`) te erven:

`/libs/granite/ui/components/coral/foundation/form/field`

Meer specifiek verstrekt granite UI een waaier van gebiedscomponenten die voor gebruik in dialogen (of, meer in het algemeen, in [formulieren](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/foundation/form/index.html)) geschikt zijn.

>[!NOTE]
>
>Dit verschilt van de klassieke UI, waar widgets door `cq:Widgets` knopen worden vertegenwoordigd, elk met bepaalde `xtype` om het verband met hun overeenkomstige widget te vestigen ExtJS. Vanuit implementatiestandpunt zijn deze widgets weergegeven aan de clientzijde door het ExtJS-framework.

Zodra u uw middeltype hebt gecreeerd, kunt u uw gebied concretiseren door een nieuw knooppunt in uw dialoog toe te voegen, met het bezit `sling:resourceType` die naar het middeltype verwijzen u net hebt geïntroduceerd.

#### Een clientbibliotheek maken voor stijl en gedrag {#creating-a-client-library-for-style-and-behavior}

Als u opmaak en gedrag voor uw component wilt definiëren, kunt u een speciale [clientbibliotheek](/help/sites-developing/clientlibs.md) maken die uw aangepaste CSS/LESS en JS definieert.

Als u uw clientbibliotheek alleen voor het dialoogvenster van de component wilt laden (zodat deze niet voor een andere component wordt geladen), moet u de eigenschap `extraClientlibs`** ** van het dialoogvenster instellen op de categorienaam van de clientbibliotheek die u zojuist hebt gemaakt. Dit is aan te raden als uw clientbibliotheek erg groot is en/of als uw veld specifiek is voor dat dialoogvenster en niet nodig is in andere dialoogvensters.

Als u de clientbibliotheek voor alle dialoogvensters wilt laden, stelt u de categorie-eigenschap van uw clientbibliotheek in op `cq.authoring.dialog`. Dit is de categorienaam van de clientbibliotheek die standaard wordt opgenomen bij het renderen van alle dialoogvensters. U wilt dat doen als uw clientbibliotheek klein is en/of uw veld algemeen is en opnieuw kan worden gebruikt in andere dialoogvensters.

Zie voor een voorbeeld:

* `cqgems/customizingfield/components/colorpicker/clientlibs`

   * verstrekt door [Codesteekproef](/help/sites-developing/developing-components-samples.md#code-sample-how-to-customize-dialog-fields)

#### Een veld uitbreiden (overnemen van) {#extending-inheriting-from-a-field}

Afhankelijk van uw vereisten kunt u:

* Een bepaald veld voor een graniet-UI uitbreiden naar componentovererving ( `sling:resourceSuperType`)
* Een bepaalde widget uitbreiden vanuit de onderliggende widgetbibliotheek (in het geval van een graniet-interface is dit de Coral-UI) door de API voor de widgetbibliotheek (JS/CSS-overerving) te volgen

#### Toegang tot dialoogvelden {#access-to-dialog-fields}

U kunt rendervoorwaarden ( `rendercondition`) ook gebruiken om te controleren wie toegang tot specifieke lusjes/gebieden in uw dialoog heeft; bijvoorbeeld:

```xml
+ mybutton
  - sling:resourceType = granite/ui/components/coral/foundation/button
  + rendercondition
    - sling:resourceType = myapp/components/renderconditions/group
    - groups = ["administrators"]
```

### Veldgebeurtenissen afhandelen {#handling-field-events}

De methode om gebeurtenissen op dialooggebieden te behandelen wordt nu gedaan met [luisteraars in een douane cliëntbibliotheek](#listeners-in-a-custom-client-library). Dit is een wijziging ten opzichte van de oudere methode waarbij [listeners in de inhoudsstructuur](#listenersinthecontentstructureclassicui) worden geplaatst.

#### Listeners in een aangepaste clientbibliotheek {#listeners-in-a-custom-client-library}

Om logica in uw gebied te injecteren, zou u moeten:

1. Laat uw veld gemarkeerd zijn met een bepaalde CSS-klasse (de *haak*).
1. Definieer in uw clientbibliotheek een JS-listener die is gekoppeld aan de naam van die CSS-klasse (dit zorgt ervoor dat uw aangepaste logica alleen binnen het bereik van uw veld valt en niet van invloed is op andere velden van hetzelfde type).

Hiervoor moet u weten welke onderliggende widgetbibliotheek u wilt gebruiken. Zie [Coral UI documentation](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/coral-ui/coralui3/index.html) om te identificeren aan welke gebeurtenis u wilt reageren. Dit lijkt erg op het proces dat u in het verleden met ExtJS moest uitvoeren: Zoek de documentatiepagina van een bepaalde widget en controleer vervolgens de details van de bijbehorende API voor gebeurtenissen.

Zie voor een voorbeeld:

* `cqgems/customizingfield/components/clientlibs/customizingfield`

   * verstrekt door [Codesteekproef](/help/sites-developing/developing-components-samples.md#code-sample-how-to-customize-dialog-fields)

#### Listeners in de inhoudsstructuur {#listeners-in-the-content-structure}

In de klassieke UI met ExtJS, was het gebruikelijk om luisteraars voor een bepaalde widget in de inhoudsstructuur te hebben. Hetzelfde bereiken in de interface met aanraakbediening is anders dan het bereiken van JS-listenercode (of enige andere code) wordt niet meer gedefinieerd in de inhoud.

De inhoudstructuur beschrijft de semantische structuur; het mag (moet) niet de aard van de onderliggende widget impliceren. Als u geen JS-code hebt in de inhoudsstructuur, kunt u de implementatiedetails wijzigen zonder de inhoudsstructuur te wijzigen. Met andere woorden, u kunt de widgetbibliotheek wijzigen zonder de inhoudsstructuur aan te raken.

#### Beschikbaarheid van dialoogvenster vaststellen {#dialog-ready}

Als u een aangepast JavaScript hebt dat alleen moet worden uitgevoerd wanneer het dialoogvenster beschikbaar en gereed is, moet u luisteren naar de gebeurtenis `dialog-ready`.

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

Veldvalidatie in de gebruikersinterface van graniet en de componenten van de gebruikersinterface van graniet (equivalent aan widgets) wordt uitgevoerd met de API `foundation-validation`. [Raadpleeg de documentatie bij  `foundation-valdiation` Granite voor meer informatie.](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/clientlibs/foundation/js/validation/index.html)

Zie voor voorbeelden:

* `cqgems/customizingfield/components/clientlibs/customizingfield/js/validations.js`

   * verstrekt door [Codesteekproef](/help/sites-developing/developing-components-samples.md#code-sample-how-to-customize-dialog-fields)

* `/libs/cq/gui/components/authoring/dialog/clientlibs/dialog/js/validations.js`

## Een ontwerpdialoogvenster maken en configureren {#creating-and-configuring-a-design-dialog}

Het dialoogvenster Ontwerpen wordt weergegeven wanneer een component ontwerpdetails bevat die kunnen worden bewerkt in [Ontwerpmodus](/help/sites-authoring/default-components-designmode.md).

De definitie lijkt erg op die van een [dialoogvenster dat wordt gebruikt voor het bewerken van inhoud](#creating-a-new-dialog), met het verschil dat deze als een knooppunt wordt gedefinieerd:

* Node name: `cq:design_dialog`
* Type: `nt:unstructured`

## Een Inplace Editor maken en configureren {#creating-and-configuring-an-inplace-editor}

Met een installatieeditor kan de gebruiker inhoud rechtstreeks in de alineasstroom bewerken, zonder dat een dialoogvenster hoeft te worden geopend. De standaardcomponenten Tekst en Titel hebben bijvoorbeeld beide een geïntegreerde editor.

Een plaatsredacteur is niet noodzakelijk/zinvol voor elk componenttype.

Zie [Paginaontwerp uitbreiden - Nieuwe Inplace Editor toevoegen](/help/sites-developing/customizing-page-authoring-touch.md#add-new-in-place-editor) voor meer informatie.

## De werkbalk Component aanpassen {#customizing-the-component-toolbar}

De [Component Toolbar](/help/sites-developing/touch-ui-structure.md#component-toolbar) geeft de gebruiker toegang tot een waaier van acties voor de component zoals uitgeven, vormen, kopiëren, en schrappen.

Zie [Paginaontwerp uitbreiden - Nieuwe handeling toevoegen aan een componentwerkbalk](/help/sites-developing/customizing-page-authoring-touch.md#add-new-action-to-a-component-toolbar) voor meer informatie.

## Een component voor de referentierail configureren (geleend/geleend) {#configuring-a-component-for-the-references-rail-borrowed-lent}

Als uw nieuwe component verwijst naar inhoud van andere pagina&#39;s, kunt u overwegen of het de secties **Geleende Inhoud** en **Lent Inhoud** van [**References**](/help/sites-authoring/basic-handling.md#references) Rail wilt beïnvloeden.

Uit-de-doos AEM slechts de component van de Verwijzing. Om uw component toe te voegen moet u de bundel OSGi **WCM Authoring Content Reference Configuration** vormen.

Maak een nieuw item in de definitie en geef de component op, samen met de eigenschap die moet worden gecontroleerd. Bijvoorbeeld:

`/apps/<*your-Project*>/components/reference@parentPath`

>[!NOTE]
>
>Wanneer het werken met AEM zijn er verscheidene methodes om de configuratiemontages voor dergelijke diensten te beheren. Zie [Het vormen OSGi](/help/sites-deploying/configuring-osgi.md) voor meer details en de geadviseerde praktijken.

## De component inschakelen en toevoegen aan het alineasysteem {#enabling-and-adding-your-component-to-the-paragraph-system}

Nadat het onderdeel is ontwikkeld, moet het zijn ingeschakeld voor gebruik in een geschikt alineasysteem, zodat het op de vereiste pagina&#39;s kan worden gebruikt.

Dit kan gebeuren door:

* gebruiken [Ontwerpmodus](/help/sites-authoring/default-components-designmode.md) bij het bewerken van een specifieke pagina.
* [het definiëren van de  `components` eigenschap in het alineasysteem van een sjabloon](/help/sites-developing/components-basics.md#adding-your-component-to-the-paragraph-system).

## Een alineasysteem configureren, zodat een componentinstantie wordt gemaakt wanneer u een element sleept {#configuring-a-paragraph-system-so-that-dragging-an-asset-creates-a-component-instance}

AEM biedt de mogelijkheid om een paragraafsysteem op uw pagina te vormen zodat [een geval van uw nieuwe component automatisch wordt gecreeerd wanneer een gebruiker (aangewezen) activa op een geval van die pagina (in plaats van het moeten altijd een lege component aan de pagina slepen).](/help/sites-authoring/editing-content.md#insertingacomponenttouchoptimizedui)

Dit gedrag, en de vereiste activa-aan-component verhouding kan worden gevormd:

1. Onder de alinea-definitie van het paginaontwerp. Bijvoorbeeld:

   * `/etc/designs/<myApp>/page/par`

   Een nieuw knooppunt maken:

   * Naam: `cq:authoring`
   * Type: `nt:unstructured`


1. Onder dit creeer een nieuwe knoop om al activa-aan-component afbeeldingen te houden:

   * Naam: `assetToComponentMapping`
   * Type: `nt:unstructured`

1. Voor elke element-aan-component afbeelding creeer een knoop:

   * Naam: tekst; het verdient aanbeveling dat de naam het element en het type van het verwante onderdeel aanduidt; bijvoorbeeld
   * Type: `nt:unstructured`

   Elke eigenschap heeft de volgende eigenschappen:

   * `assetGroup`:

      * Type: `String`
      * Waarde: de groep waartoe het gerelateerde actief behoort; bijvoorbeeld `media`
   * `assetMimetype`:

      * Type: `String`
      * Waarde: het mime-type van het gerelateerde actief; bijvoorbeeld `image/*`
   * `droptarget`:

      * Type: `String`
      * Waarde: de neerzetbestemming; bijvoorbeeld `image`
   * `resourceType`:

      * Type: `String`
      * Waarde: de daarmee verband houdende component-bron; bijvoorbeeld `foundation/components/image`
   * `type`:

      * Type: `String`
      * Waarde: het type, bijvoorbeeld `Images`






Zie voor voorbeelden:

* `/etc/designs/geometrixx/jcr:content/page/par/cq:authoring`
* `/etc/designs/geometrixx-outdoors/jcr:content/page/par/cq:authoring`
* `/etc/designs/geometrixx-media/jcr:content/article/article-content-par/cq:authoring`

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [Open aem-project-archetype project op GitHub](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype)
* Het project downloaden als [een ZIP-bestand](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype/archive/master.zip)

>[!NOTE]
>
>De automatische verwezenlijking van componenteninstanties kan nu gemakkelijk binnen UI worden gevormd wanneer het gebruiken van [de Componenten van de Kern](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/introduction.html) en Bewerkbare Malplaatjes. Zie [Paginasjablonen maken](/help/sites-authoring/templates.md#editing-a-template-structure-template-author) voor meer informatie over het definiëren van welke componenten automatisch worden gekoppeld aan bepaalde mediatypen.

## De extensie AEM accolades gebruiken {#using-the-aem-brackets-extension}

De [AEM Brackets Extension](/help/sites-developing/aem-brackets.md) biedt een vloeiende workflow voor het bewerken van AEM componenten en clientbibliotheken. Het is gebaseerd op [Brackets](https://brackets.io/) coderedacteur.

De extensie:

* Vereenvoudigt synchronisatie (geen Maven of File Vault vereist) om de efficiëntie van ontwikkelaars te verhogen en helpt ook front-end ontwikkelaars met beperkte AEM kennis om aan projecten deel te nemen.
* Verstrekt wat [HTML](https://docs.adobe.com/content/help/en/experience-manager-htl/using/overview.html) steun, de malplaatjetaal die wordt ontworpen om componentenontwikkeling te vereenvoudigen en veiligheid te verhogen.

>[!NOTE]
>
>Brackets is het aanbevolen mechanisme voor het maken van componenten. Het vervangt CRXDE Lite - creeer de functionaliteit van de Component, die voor klassieke UI werd ontworpen.

## Migreren vanuit een klassieke component {#migrating-from-a-classic-component}

Bij het migreren van een component die is ontworpen voor gebruik met de klassieke UI naar een component die met touch-enabled UI (of slechts of gezamenlijk) kan worden gebruikt zouden de volgende kwesties moeten worden overwogen:

* HTL

   * Het gebruik van [HTL](https://docs.adobe.com/content/help/en/experience-manager-htl/using/overview.html) is niet verplicht, maar als uw component moet worden bijgewerkt, is het ideale moment om [migreren van JSP naar HTL](/help/sites-developing/components-basics.md#htl-vs-jsp) te overwegen.

* Onderdelen

   * [ `cq:listener`](/help/sites-developing/developing-components.md#migrating-cq-listener-code) code migreren die klassieke UI specifieke functies gebruiken
   * De stop van RTE, voor verdere informatie zie [Vormend de Rich Text Editor](/help/sites-administering/rich-text-editor.md).
   * [Migreer  `cq:listener` ](#migrating-cq-listener-code) code die functies gebruikt specifiek voor klassieke UI

* Dialoogvensters

   * U moet een nieuw dialoogvenster maken voor gebruik in de interface met aanraakbediening. Voor compatibiliteitsdoeleinden kan de interface met aanraakbediening echter gebruikmaken van de definitie van een klassiek dialoogvenster UI, wanneer er geen dialoogvenster is gedefinieerd voor de interface met aanraakbediening.
   * De [AEM Moderniseringshulpmiddelen](/help/sites-developing/modernization-tools.md) worden verstrekt om u te helpen bestaande componenten uitbreiden.
   * [Het in kaart brengen ExtJS aan de ](/help/sites-developing/touch-ui-concepts.md#extjs-and-corresponding-granite-ui-components) Componenten van Granite UI verstrekt een geschikt overzicht van xtypes ExtJS en knooptypes van ExtJS met hun gelijkwaardige middeltypes van Granite UI.
   * Het aanpassen van gebieden, voor meer informatie zie de zitting van AEM Gems op [Aanpassen van de Gebieden van de Dialoog](https://docs.adobe.com/content/ddc/en/gems/customizing-dialog-fields-in-touch-ui.html).
   * Migreren van vtypen naar [graniet-UI-validatie](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/foundation/clientlibs/foundation/js/validation/index.html)
   * Gebruikend JS luisteraars, voor meer informatie zie [Behandelend de Gebeurtenissen van het Gebied ](#handling-field-events) en de zitting van AEM Gems op [Aanpassen van de Gebieden van de Dialoog](https://docs.adobe.com/content/ddc/en/gems/customizing-dialog-fields-in-touch-ui.html).

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
* enz.

Daarom is het vrij gemakkelijk om het even welke bestaande documentatiemarkering te maken u binnen de component zelf beschikbaar hebt.

U hoeft alleen een `README.md`-bestand in de componentstructuur te plaatsen. Deze markering zal dan in [componentenconsole](/help/sites-authoring/default-components-console.md) worden getoond.

![chlimage_1-7](assets/chlimage_1-7.png)

De ondersteunde markering is gelijk aan die voor [inhoudsfragmenten](/help/assets/content-fragments/content-fragments-markdown.md).
