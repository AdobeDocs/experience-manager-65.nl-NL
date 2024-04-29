---
title: Stijl Adobe Experience Manager CIF Core-onderdelen
description: Leer hoe u Adobe Experience Manager CIF Core Components opmaakt. In de zelfstudie wordt uitgelegd hoe Client-Side Libraries of clientlibs worden gebruikt om CSS en JavaScript voor een Adobe Experience Manager (AEM) Commerce-implementatie te implementeren en te beheren. Deze zelfstudie behandelt ook hoe de module ui.frontend en een webpack-project worden geïntegreerd in het end-to-end buildproces.
sub-product: Commerce
topics: Development
version: Cloud Service
doc-type: tutorial
feature: Commerce Integration Framework
kt: 3456
thumbnail: 3456-style-cif.jpg
exl-id: 04d553be-c67d-4ecb-a23f-2694c2adfc2b
solution: Experience Manager,Commerce
role: Admin, Developer
source-git-commit: 10268f617b8a1bb22f1f131cfd88236e7d5beb47
workflow-type: tm+mt
source-wordcount: '2338'
ht-degree: 0%

---

# Stijl AEM CIF kerncomponenten {#style-aem-cif-core-components}

De [CIF Venia-project](https://github.com/adobe/aem-cif-guides-venia) is een referentiecode die als basis kan dienen voor [CIF kerncomponenten](https://github.com/adobe/aem-core-cif-components). In deze zelfstudie inspecteert u het Venia-referentieproject en begrijpt u hoe CSS en JavaScript die door AEM Core-componenten worden gebruikt, zijn geordend. U maakt ook een stijl met CSS om de standaardstijl van het dialoogvenster **Productteam** component.

>[!TIP]
>
>Gebruik de [Project archetype AEM](https://github.com/adobe/aem-project-archetype) wanneer het beginnen van uw eigen handelsimplementatie.

## Wat u gaat maken

In deze zelfstudie wordt een nieuwe stijl geïmplementeerd voor de component Product Teaser die op een kaart lijkt. De lessen die in het leerprogramma worden geleerd kunnen op andere Componenten van de Kern worden toegepast CIF.

![Wat u gaat maken](../assets/style-cif-component/what-you-will-build.png)

## Vereisten {#prerequisites}

U hebt een lokale ontwikkelomgeving nodig om deze zelfstudie te voltooien. Dit omvat een lopende instantie van AEM die wordt gevormd en met een instantie van Adobe Commerce verbonden. De vereisten en stappen voor [een plaatselijke ontwikkeling opzetten met AEM](../develop.md).

## Het Venia-project klonen {#clone-venia-project}

We klonen de [Venia-project](https://github.com/adobe/aem-cif-guides-venia) en overschrijf vervolgens de standaardstijlen.

>[!NOTE]
>
>**U kunt een bestaand project zonder problemen gebruiken** (gebaseerd op het AEM Projectarchetype met CIF inbegrepen) en sla deze sectie over.

1. Voer de volgende git-opdracht uit om het project te klonen:

   ```shell
   $ git clone git@github.com:adobe/aem-cif-guides-venia.git
   ```

1. Bouw en stel het project aan een lokaal geval van AEM op:

   ```shell
   $ cd aem-cif-guides-venia/
   $ mvn clean install -PautoInstallPackage,cloud
   ```

1. Voeg de noodzakelijke configuraties OSGi toe om uw AEM instantie met een instantie van Adobe Commerce te verbinden of de configuraties aan het onlangs gecreeerd project toe te voegen.

1. Op dit moment hebt u een werkende versie van een winkel die is verbonden met een Adobe Commerce-instantie. Ga naar de `US` > `Home` pagina bij: [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html).

   Je moet zien dat de winkel het Venia-thema gebruikt. Als u het hoofdmenu van de winkel uitbreidt, ziet u verschillende categorieën die aangeven dat de verbinding met Adobe Commerce werkt.

   ![Storefront geconfigureerd met Venia-thema](../assets/style-cif-component/venia-store-configured.png)

## Client Libraries en ui.frontend Module {#introduction-to-client-libraries}

De CSS en JavaScript die verantwoordelijk zijn voor het renderen van het thema of de stijlen van de winkel, worden in AEM beheerd door een [clientbibliotheek](/help/sites-developing/clientlibs.md) of clientlibs voor korte tijd. Clientbibliotheken bieden een mechanisme om CSS en JavaScript in de code van een project te organiseren en vervolgens op de pagina te leveren.

Brand-specifieke stijlen kunnen op AEM Componenten van de Kern worden toegepast door CSS toe te voegen en met voeten te treden die door deze cliëntbibliotheken wordt geleid. Inzicht in de structuur van clientbibliotheken en de inhoud van deze bibliotheken op de pagina is essentieel.

De [ui.frontend](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/uifrontend.html) is een speciale [webpack](https://webpack.js.org/) project voor het beheer van alle front-end activa voor een project. Op deze manier kunnen front-end ontwikkelaars elk aantal talen en technologieën gebruiken, zoals [TypeScript](https://www.typescriptlang.org/), [Soort](https://sass-lang.com/) en nog veel meer.

De `ui.frontend` de module is ook een Gemaakt module en geïntegreerd met het grotere project door een module te gebruiken NPM [aem-clientlib-generator](https://github.com/wcm-io-frontend/aem-clientlib-generator). Tijdens een build `aem-clientlib-generator` Hiermee kopieert u de gecompileerde CSS- en JavaScript-bestanden naar een clientbibliotheek in het dialoogvenster `ui.apps` -module.

![ui.frontend naar ui.apps-architectuur](../assets/style-cif-component/ui-frontend-architecture.png)

*Gecompileerde CSS en JavaScript worden gekopieerd uit de `ui.frontend` in de `ui.apps` module als clientbibliotheek tijdens een Maven-build*

## Teastijl bijwerken {#ui-frontend-module}

Breng vervolgens een kleine wijziging aan in de stijl Taser om te zien hoe de `ui.frontend` en clientbibliotheken werken. Gebruiken [de IDE van uw keuze](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html#set-up-the-development-ide) het Venia-project in te voeren. De gebruikte screenshots zijn afkomstig van de [Visual Studio Code IDE](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html#microsoft-visual-studio-code).

1. Navigeren en de **ui.frontend** en breid de maphiërarchie uit naar: `ui.frontend/src/main/styles/commerce`:

   ![ui.frontend commercemap](../assets/style-cif-component/ui-frontend-commerce-folder.png)

   Er zijn meerdere controles (`.scss`) onder de map. Dit zijn de Commerce-specifieke stijlen voor elk van de Commerce-componenten.

1. Het bestand openen `_productteaser.scss`.

1. Werk de `.item__image` en wijzigt u de randregel:

   ```scss
   .item__image {
       border: #ea00ff 8px solid; /* <-- modify this rule */
       display: block;
       grid-area: main;
       height: auto;
       opacity: 1;
       transition-duration: 512ms;
       transition-property: opacity, visibility;
       transition-timing-function: ease-out;
       visibility: visible;
       width: 100%;
   }
   ```

   Met de bovenstaande regel moet u een vette, roze rand toevoegen aan de Product Teaser Component.

1. Open een nieuw terminalvenster en ga naar het `ui.frontend` map:

   ```shell
   $ cd <project-location>/aem-cif-guides-venia/ui.frontend
   ```

1. Voer de volgende Maven-opdracht uit:

   ```shell
   $ mvn clean install
   ...
   [INFO] ------------------------------------------------------------------------
   [INFO] BUILD SUCCESS
   [INFO] ------------------------------------------------------------------------
   [INFO] Total time:  29.497 s
   [INFO] Finished at: 2020-08-25T14:30:44-07:00
   [INFO] ------------------------------------------------------------------------
   ```

   Inspect de einduitvoer. U kunt zien dat de Maven-opdracht verschillende NPM-scripts heeft uitgevoerd, waaronder `npm run build`. De `npm run build` wordt in het dialoogvenster `package.json` en heeft het effect van het compileren van het webpack-project en het activeren van de clientbibliotheek.

1. Het bestand Inspect `ui.frontend/dist/clientlib-site/site.css`:

   ![Gecompileerde site-CSS](../assets/style-cif-component/comiled-site-css.png)

   Het dossier is de gecompileerde en geminificeerde versie van alle dossiers van de Klasse in het project.

   >[!NOTE]
   >
   >Bestanden als deze worden genegeerd vanuit de broncontrole omdat deze tijdens de ontwikkeltijd moeten worden gegenereerd.

1. Het bestand Inspect `ui.frontend/clientlib.config.js`.

   ```js
   /* clientlib.config.js*/
   ...
   // Config for `aem-clientlib-generator`
   module.exports = {
       context: BUILD_DIR,
       clientLibRoot: CLIENTLIB_DIR,
       libs: [
           {
               ...libsBaseConfig,
               name: 'clientlib-site',
               categories: ['venia.site'],
               dependencies: ['venia.dependencies', 'aem-core-cif-react-components'],
               assets: {
   ...
   ```

   Dit is het configuratiebestand voor [aem-clientlib-generator](https://github.com/wcm-io-frontend/aem-clientlib-generator) en bepaalt waar en hoe het gecompileerde CSS en JavaScript in een AEM cliëntbibliotheek zal worden omgezet.

1. In de `ui.apps` inspecteer het bestand: `ui.apps/src/main/content/jcr_root/apps/venia/clientlibs/clientlib-site/css/site.css`:

   ![Gecompileerde site-CSS in ui.apps](../assets/style-cif-component/comiled-css-ui-apps.png)

   Hiermee kopieert u de `site.css` in het bestand `ui.apps` project. Het maakt nu deel uit van een clientbibliotheek met de naam `clientlib-site` met een categorie `venia.site`. Als het bestand eenmaal deel uitmaakt van het `ui.apps` kan het aan AEM worden opgesteld.

   >[!NOTE]
   >
   >Bestanden als deze worden ook genegeerd vanuit de broncontrole omdat deze tijdens de ontwikkeltijd moeten worden gegenereerd.

1. Inspecteer dan de andere cliëntbibliotheken die door het project worden geproduceerd:

   ![Andere clientbibliotheken](../assets/style-cif-component/other-clientlibs.png)

   Deze clientbibliotheken worden niet beheerd door de `ui.frontend` -module. In plaats daarvan bevatten deze clientbibliotheken CSS- en JavaScript-afhankelijkheden die door Adobe worden verschaft. De definitie van deze clientbibliotheken vindt u in het dialoogvenster `.content.xml` bestand onder elke map.

   **clientlib-base** - Dit is een lege clientbibliotheek waarin eenvoudig de benodigde afhankelijkheden zijn ingesloten [AEM kerncomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html). De categorie is `venia.base`.

   **clientlib-cif** - Dit is ook een lege clientbibliotheek die de benodigde afhankelijkheden insluit vanuit [CIF kerncomponenten AEM](https://github.com/adobe/aem-core-cif-components). De categorie is `venia.cif`.

   **clientlib-raster** - Dit omvat de CSS nodig om AEM functie Responsief raster in te schakelen. Met het AEM schakelt u [Lay-outmodus](/help/sites-authoring/responsive-layout.md) in de AEM Editor en biedt de auteur van de inhoud de mogelijkheid om de grootte van componenten te wijzigen. De categorie is `venia.grid` en is ingesloten in de `venia.base` bibliotheek.

1. Inspect de bestanden `customheaderlibs.html` en `customfooterlibs.html` beneide `ui.apps/src/main/content/jcr_root/apps/venia/components/page`:

   ![Scripts voor Aangepaste kopteksten en voetteksten](../assets/style-cif-component/custom-header-footer-script.png)

   Deze scripts bevatten **venia.base** en **venia.cif** als onderdeel van alle pagina&#39;s.

   >[!NOTE]
   >
   >Alleen de basisbibliotheken zijn &#39;hard-coded&#39; als onderdeel van de paginascripts. `venia.site` is niet opgenomen in deze bestanden en wordt in plaats daarvan opgenomen als onderdeel van de paginasjabloon voor meer flexibiliteit. Dit wordt later geïnspecteerd.

1. Van de terminal, bouw en stel het volledige project aan een lokaal geval van AEM op:

   ```shell
   $ cd aem-cif-guides-venia/
   $ mvn clean install -PautoInstallPackage,cloud
   ```

## Auteur van een producttaser {#author-product-teaser}

Nu de codeupdates zijn opgesteld, voeg een nieuw geval van de component van de Teaser van het Product aan de homepage van de plaats toe gebruikend de AEM auteurshulpmiddelen. Hierdoor kunnen we de bijgewerkte stijlen bekijken.

1. Een nieuw browsertabblad openen en naar het tabblad **Startpagina** van het gebied: [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html).

1. De zoekfunctie voor bedrijfsmiddelen (de zijspoor) uitbreiden in **Bewerken** -modus. Het middelenfilter overschakelen op **Producten**.

   ![De Finder en het filter Middelen uitvouwen op producten](../assets/style-cif-component/drag-drop-product-page.png)

1. Sleep een nieuw product naar de startpagina in de container van de hoofdlay-out:

   ![Producttaser met roze rand](../assets/style-cif-component/pink-border-product-teaser.png)

   U moet zien dat de Product Teaser nu een helderroze rand heeft die is gebaseerd op de eerder gemaakte CSS-regelwijziging.

## Clientbibliotheken op de pagina controleren {#verify-client-libraries}

Controleer vervolgens de opname van de clientbibliotheken op de pagina.

1. Ga naar de **Startpagina** van het gebied: [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html).

1. Selecteer de **Pagina-informatie** menu en klik op **Weergeven als gepubliceerd**:

   ![Weergeven als gepubliceerd](../assets/style-cif-component/view-as-published.png)

   Hierdoor wordt de pagina geopend zonder dat de AEM auteur JavaScript is geladen, zoals deze op de gepubliceerde site wordt weergegeven. De URL heeft de queryparameter `?wcmmode=disabled` toegevoegd. Bij het ontwikkelen van CSS en JavaScript is het aan te raden deze parameter te gebruiken om de pagina te vereenvoudigen zonder dat AEM auteur iets hoeft te doen.

1. Bekijk de paginabron en u zou verscheidene cliëntbibliotheken moeten kunnen identificeren inbegrepen zijn:

   ```html
   <!DOCTYPE html>
   <html lang="en-US">
   <head>
       ...
       <link rel="stylesheet" href="/etc.clientlibs/venia/clientlibs/clientlib-base.min.css" type="text/css">
       <link rel="stylesheet" href="/etc.clientlibs/venia/clientlibs/clientlib-site.min.css" type="text/css">
   </head>
   ...
       <script type="text/javascript" src="/etc.clientlibs/venia/clientlibs/clientlib-site.min.js"></script>
       <script type="text/javascript" src="/etc.clientlibs/core/wcm/components/commons/site/clientlibs/container.min.js"></script>
       <script type="text/javascript" src="/etc.clientlibs/venia/clientlibs/clientlib-base.min.js"></script>
   <script type="text/javascript" src="/etc.clientlibs/core/cif/clientlibs/common.min.js"></script>
   <script type="text/javascript" src="/etc.clientlibs/venia/clientlibs/clientlib-cif.min.js"></script>
   </body>
   </html>
   ```

   Clientbibliotheken die worden geleverd aan de pagina, worden vooraf uitgerust met `/etc.clientlibs` en via een [proxy](/help/sites-developing/clientlibs.md) om te voorkomen dat er gevoelige `/apps` of `/libs`.

   Kennisgeving `venia/clientlibs/clientlib-site.min.css` en `venia/clientlibs/clientlib-site.min.js`. Dit zijn de gecompileerde CSS- en JavaScript-bestanden die zijn afgeleid van de `ui.frontend` -module.

## Opname van clientbibliotheek met paginasjablonen {#client-library-inclusion-pagetemplates}

Er zijn verschillende opties voor het opnemen van een bibliotheek aan de clientzijde. Ga vervolgens na hoe het gegenereerde project de `clientlib-site` bibliotheken via [Paginasjablonen](/help/sites-developing/templates.md).

1. Ga naar de **Startpagina** van de site in de AEM Editor: [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html).

1. Selecteer de **Pagina-informatie** menu en klik op **Sjabloon bewerken**:

   ![De sjabloon bewerken](../assets/style-cif-component/edit-template.png)

   Hierdoor wordt het **Openingspagina** de sjabloon **Home** is gebaseerd op.

   >[!NOTE]
   >
   >Als u alle beschikbare sjablonen wilt weergeven vanuit het scherm AEM starten, navigeert u naar **Gereedschappen** > **Algemeen** > **Sjablonen**.

1. Selecteer in de linkerbovenhoek de optie **Pagina-informatie** pictogram en klik **Paginabeleid**.

   ![Menu-item voor paginabeleid](../assets/style-cif-component/page-policy-menu.png)

1. Hiermee opent u het paginabeleid voor de sjabloon Openingspagina:

   ![Paginabeleid - bestemmingspagina](../assets/style-cif-component/page-policy-properties.png)

   Rechts ziet u een lijst met clientbibliotheken **categorieën** die worden opgenomen op alle pagina&#39;s die deze sjabloon gebruiken.

   * `venia.dependencies` - Biedt leveranciers die `venia.site` is afhankelijk van.
   * `venia.site` - Dit is de categorie voor `clientlib-site` dat de `ui.frontend` wordt gegenereerd.

   Merk op dat andere malplaatjes het zelfde beleid gebruiken, **Inhoud pagina**, **Openingspagina**, enzovoort. Door hetzelfde beleid opnieuw te gebruiken, kunnen we ervoor zorgen dat dezelfde clientbibliotheken op alle pagina&#39;s worden opgenomen.

   Het voordeel van het gebruiken van Malplaatjes en het beleid van de Pagina om de opneming van cliëntbibliotheken te beheren is dat u het beleid per malplaatje kunt veranderen. U beheert bijvoorbeeld twee verschillende merken binnen dezelfde AEM. Elk merk heeft zijn eigen unieke stijl of *thema* maar de basisbibliotheken en de code zullen het zelfde zijn. Een ander voorbeeld: als u een grotere clientbibliotheek had die u alleen op bepaalde pagina&#39;s wilde weergeven, kon u een uniek paginabeleid maken, alleen voor die sjabloon.

## Lokale WebPack-ontwikkeling {#local-webpack-development}

In de vorige oefening werd een update gemaakt aan een dossier van de Klasse in `ui.frontend` en na het uitvoeren van een Maven bouwt de veranderingen worden opgesteld aan AEM. Vervolgens bekijken we het gebruik van een webpack-dev-server om de front-end stijlen snel te ontwikkelen.

Met de webpack-dev-server worden afbeeldingen en sommige van de CSS/JavaScript-code in de lokale versie van AEM beschikbaar gemaakt, maar kan de ontwikkelaar de stijlen en JavaScript-code in het dialoogvenster `ui.frontend` -module.

1. Navigeer in de browser naar de knop **Home** pagina en **Weergeven als gepubliceerd**: [http://localhost:4502/content/venia/us/en.html?wcmmode=disabled](http://localhost:4502/content/venia/us/en.html?wcmmode=disabled).

1. De bron van de pagina en de **kopiëren** de onbewerkte HTML van de pagina.

1. Terugkeren naar IDE van uw keuze onder de `ui.frontend` het bestand openen: `ui.frontend/src/main/static/index.html`

   ![Statisch HTML-bestand](../assets/style-cif-component/static-index-html.png)

1. De inhoud van `index.html` en **plakken** de HTML die in de vorige stap is gekopieerd.

1. Zoeken naar include-bestanden voor `clientlib-site.min.css`, `clientlib-site.min.js` en **remove** zij.

   ```html
   <head>
       <!-- remove this link -->
       <link rel="stylesheet" href="/etc.clientlibs/venia/clientlibs/clientlib-base.min.css" type="text/css">
       ...
   </head>
   <body>
       ...
        <!-- remove this link -->
       <script type="text/javascript" src="/etc.clientlibs/venia/clientlibs/clientlib-site.min.js"></script>
   </body>
   ```

   Deze worden verwijderd omdat ze de gecompileerde versie vertegenwoordigen van de CSS en JavaScript die zijn gegenereerd door de `ui.frontend` -module. Laat de andere clientbibliotheken ongewijzigd, omdat ze van de actieve AEM worden proxy&#39;s.

1. Open een nieuw terminalvenster en navigeer in de `ui.frontend` map. De opdracht uitvoeren `npm start`:

   ```shell
   $ cd ui.frontend
   $ npm start
   ```

   Hiermee start u de webpack-dev-server op [http://localhost:8080/](http://localhost:8080/)

   >[!CAUTION]
   >
   >Als u een fout hebt met betrekking tot de klasse Sass, stopt u de server en voert u de opdracht uit `npm rebuild node-sass` en herhaal de bovenstaande stappen. Dit kan gebeuren als u een andere versie van `npm` en `node` vervolgens opgegeven in het project `aem-cif-guides-venia/pom.xml`.

1. Ga naar de [http://localhost:8080/](http://localhost:8080/) in een nieuw tabblad met dezelfde browser als een AEM die u hebt aangemeld. U moet de startpagina van Venia zien via de webpack-dev-server:

   ![Webpack-ontwikkelserver op poort 80](../assets/style-cif-component/webpack-dev-server-port80.png)

   Laat de webpack-dev-server actief. Het wordt gebruikt in de volgende oefening.

## Kaartstijl voor productteam implementeren {#update-css-product-teaser}

Wijzig daarna de dossiers van de Klasse in `ui.frontend` -module voor het implementeren van een op kaarten lijkende stijl voor de Product Teaser. De webpack-dev-server wordt gebruikt om de wijzigingen snel te zien.

Terugkeer aan winde en het geproduceerde project.

1. In de **ui.frontend** -module, het bestand opnieuw openen `_productteaser.scss` om `ui.frontend/src/main/styles/commerce/_productteaser.scss`.

1. Breng de volgende wijzigingen aan in de rand Product Teaser:

   ```diff
       .item__image {
   -       border: #ea00ff 8px solid;
   +       border-bottom: 1px solid #c0c0c0;
           display: block;
           grid-area: main;
           height: auto;
           opacity: 1;
           transition-duration: 512ms;
           transition-property: opacity, visibility;
           transition-timing-function: ease-out;
           visibility: visible;
           width: 100%;
       }
   ```

   Sla de wijzigingen op en de webpack-dev-server moet automatisch vernieuwen met de nieuwe stijlen.

1. Voeg een slagschaduw toe en neem afgeronde hoeken op in de producttaser.

   ```scss
    .item__root {
        position: relative;
        box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
        transition: 0.3s;
        border-radius: 5px;
        float: left;
        margin-left: 12px;
        margin-right: 12px;
   }
   
   .item__root:hover {
      box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
   }
   ```

1. Werk de naam van het product bij zodat deze onder aan het gummetje wordt weergegeven en wijzig de tekstkleur.

   ```css
   .item__name {
       color: #000;
       display: block;
       float: left;
       font-size: 22px;
       font-weight: 900;
       line-height: 1em;
       padding: 0.75em;
       text-transform: uppercase;
       width: 75%;
   }
   ```

1. Werk de prijs van het product bij zodat deze ook onder aan het gummetje wordt weergegeven en wijzig de tekstkleur.

   ```css
   .price {
       color: #000;
       display: block;
       float: left;
       font-size: 18px;
       font-weight: 900;
       padding: 0.75em;
       padding-bottom: 2em;
       width: 25%;
   
       ...
   ```

1. Werk de mediaquery onderaan bij om de naam en prijs te stapelen in schermen kleiner dan **992 px**.

   ```css
   @media (max-width: 992px) {
       .productteaser .item__name {
           font-size: 18px;
           width: 100%;
       }
       .productteaser .item__price {
           font-size: 14px;
           width: 100%;
       }
   }
   ```

   De kaartstijl wordt nu weerspiegeld in de webpack-dev-server:

   ![Wijzigingen in het testprogramma van WebPack Dev Server](../assets/style-cif-component/webpack-dev-server-teaser-changes.png)

   De wijzigingen zijn echter nog niet AEM. U kunt de [oplossingsbestand hier](../assets/style-cif-component/_productteaser.scss).

1. Stel de updates op om AEM te gebruiken uw Maven vaardigheden, van een bevel-lijn terminal:

   ```shell
   $ cd aem-cif-guides-venia/
   $ mvn clean install -PautoInstallPackage,cloud
   ```

   >[!NOTE]
   >Er zijn extra [IDE-instellingen en -gereedschappen](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html#set-up-an-integrated-development-environment) die projectbestanden rechtstreeks met een lokale AEM kunnen synchroniseren zonder een volledige Maven-build uit te voeren.

## Bijgewerkte producttaser weergeven {#view-updated-product-teaser}

Nadat de code voor het project aan AEM wordt opgesteld, zou u de veranderingen in de Teaser van het Product moeten kunnen zien.

1. Ga terug naar uw browser en vernieuw de startpagina: [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html). De bijgewerkte stijlen voor productgummeters moeten worden toegepast.

   ![Bijgewerkte stijl van de Teaser van het Product](../assets/style-cif-component/product-teaser-new-style.png)

1. Experimenteer door extra Product teasers toe te voegen. Gebruik de modus Lay-out om de breedte en verschuiving van de componenten te wijzigen en meerdere trappen in een rij weer te geven.

   ![Meerdere productteams](../assets/style-cif-component/multiple-teasers-final.png)

## Problemen oplossen {#troubleshooting}

U kunt controleren in [CRXDE-Lite](http://localhost:4502/crx/de/index.jsp) dat het bijgewerkte CSS-bestand is geïmplementeerd: [http://localhost:4502/crx/de/index.jsp#/apps/venia/clientlibs/clientlib-site/css/site.css](http://localhost:4502/crx/de/index.jsp#/apps/venia/clientlibs/clientlib-site/css/site.css)

Bij het implementeren van nieuwe CSS- en/of JavaScript-bestanden is het ook belangrijk ervoor te zorgen dat de browser geen bestanden met een vaste status levert. U kunt dit voorkomen door de browsercache te wissen of een nieuwe browsersessie te starten.

AEM probeert ook clientbibliotheken in cache te plaatsen voor prestaties. Soms, na een codeplaatsing worden de oudere dossiers gediend. U kunt de AEM cache van de clientbibliotheek handmatig invalideren met [Het gereedschap Clientbibliotheken opnieuw samenstellen](http://localhost:4502/libs/granite/ui/content/dumplibs.rebuild.html). *Schakel de voorkeursmethode Caches ongeldig maken in als u vermoedt dat AEM een oude versie van een clientbibliotheek in het cachegeheugen heeft opgeslagen. Het opnieuw samenstellen van bibliotheken is inefficiënt en tijdrovend.*

## Gefeliciteerd {#congratulations}

U hebt uw eerste AEM Core Component vormgegeven en u hebt een webpack-ontwikkelserver gebruikt!

## Bonus Challenge {#bonus-challenge}

Gebruik de [Systeem AEM](/help/sites-authoring/style-system.md) om twee stijlen te maken die door de auteur van de inhoud in- en uitgeschakeld kunnen worden. [Ontwikkelen met het Stijlsysteem](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/project-archetype/style-system.html) bevat gedetailleerde stappen en informatie over hoe u dit kunt bereiken.

![Bonus Challenge - Stijl Systeem](../assets/style-cif-component/bonus-challenge.png)

## Aanvullende bronnen {#additional-resources}

* [Projectarchetype AEM](https://github.com/adobe/aem-project-archetype)
* [CIF kerncomponenten AEM](https://github.com/adobe/aem-core-cif-components)
* [Een lokale AEM ontwikkelomgeving instellen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html)
* [Client-Side bibliotheken](/help/sites-developing/clientlibs.md)
* [Aan de slag met AEM Sites](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)
* [Ontwikkelen met het Stijlsysteem](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/project-archetype/style-system.html)
