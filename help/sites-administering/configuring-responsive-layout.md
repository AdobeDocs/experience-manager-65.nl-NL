---
title: Container en lay-outmodus configureren
description: Leer hoe u de container van de lay-out en de lay-outmodus configureert.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
legacypath: /content/docs/en/aem/6-2/administer/operations/page-authoring/configuring-responsive-layouting
exl-id: 61152b2d-4c0b-4cfd-9669-cf03d32cb7c7
solution: Experience Manager, Experience Manager Sites
feature: Operations
role: Admin
source-git-commit: 17c4084d9ee93e5fe6652d63438eaf34cbc83c12
workflow-type: tm+mt
source-wordcount: '1479'
ht-degree: 0%

---


# Container en lay-outmodus configureren{#configuring-layout-container-and-layout-mode}

Leer hoe u de container van de lay-out en de lay-outmodus configureert.

>[!TIP]
>
>Dit document biedt een overzicht van responsieve ontwerpen voor sitebeheerders en -ontwikkelaars waarin wordt beschreven hoe functies in AEM worden uitgevoerd.
>
>Voor inhoudsauteurs, zijn de details van hoe te om ontvankelijke ontwerpeigenschappen op een inhoudspagina te gebruiken beschikbaar in het document [ Responsieve lay-out voor uw inhoudspagina&#39;s.](/help/sites-authoring/responsive-layout.md)

## Overzicht {#overview}

[ Responsieve Lay-out ](/help/sites-authoring/responsive-layout.md) is een mechanisme om [ ontvankelijk Webontwerp ](https://en.wikipedia.org/wiki/Responsive_web_design) te realiseren. Hierdoor kan de gebruiker webpagina&#39;s maken met een indeling en afmetingen die afhankelijk zijn van de apparaten die de gebruikers gebruiken.

AEM realiseert een responsieve indeling voor uw pagina&#39;s met behulp van een combinatie van mechanismen:

* **](/help/sites-authoring/responsive-layout.md#adding-a-layout-container-and-its-content-edit-mode)component van de Container van 0} Lay-out[**

  Deze component verstrekt een net-paragraaf systeem om u toe te voegen en componenten binnen een ontvankelijk net te plaatsen. Het kan als standaardparsys voor uw pagina worden gebruikt en/of ter beschikking gesteld aan auteurs in componentenbrowser.

   * De standaard **component van de Container van 0} Lay-out wordt bepaald onder:**

     `/libs/wcm/foundation/components/responsivegrid`

   * U kunt lay-outcontainers definiëren:

      * Als een component die de gebruiker aan een pagina kan toevoegen.
      * Als standaardparsys voor de pagina.
      * Beide.

        U kunt de lay-outcontainer als standaard voor de pagina hebben, terwijl het toestaan van de gebruiker om verdere lay-outcontainers binnen dit toe te voegen; bijvoorbeeld, om kolomcontrole te bereiken.

* **[Wijze van de Lay-out](/help/sites-authoring/responsive-layout.md#defining-layouts-layout-mode)**
Zodra de lay-outcontainer op uw pagina wordt geplaatst kunt u de **3} wijze van de Lay-out {gebruiken om inhoud binnen het ontvankelijke net te plaatsen.**

* [**Emulator**](/help/sites-authoring/responsive-layout.md#selecting-a-device-to-emulate)
Zo kunt u responsieve websites maken en bewerken die de lay-out op basis van de grootte van het apparaat of venster opnieuw rangschikken door de grootte van componenten interactief aan te passen. De gebruiker kan dan zien hoe de inhoud wordt gerenderd met de emulator.

Met deze responsieve rastermechanismen kunt u:

* Gebruik onderbrekingspunten (die apparaatgroepering aangeven) om een verschillend gedrag voor de inhoud te definiëren op basis van de apparaatlay-out.
* Componenten verbergen op basis van apparaatgroep (definiëren op welk onderbrekingspunt een component wordt verborgen).
* Gebruik horizontale uitlijning op het raster (plaats componenten in het raster, wijzig de grootte naar wens en definieer wanneer ze naast elkaar of boven/onder moeten samenvouwen/opnieuw moeten plaatsen).
* Kolombesturingselement realiseren.

>[!TIP]
>
>Adobe verstrekt [ documentatie GitHub ](https://adobe-marketing-cloud.github.io/aem-responsivegrid/) van de ontvankelijke lay-out als verwijzing die aan front-end ontwikkelaars kan worden gegeven die hen toestaan om het net van AEM buiten AEM te gebruiken, bijvoorbeeld, wanneer het creëren van statische modellen van HTML voor een toekomstige plaats van AEM.

>[!NOTE]
>
>In een uit-van-de-doos installatie, is de ontvankelijke lay-out gevormd voor de [ Wij.Retail verwijzingsplaats ](/help/sites-developing/we-retail.md). [ activeer de component van de Container van de Lay-out ](#enable-the-layout-container-component-for-page) voor andere pagina&#39;s.

>[!CAUTION]
>
>Hoewel de **component van de Container van de Lay-out** in klassieke UI beschikbaar is, is zijn volledige functionaliteit slechts beschikbaar in touch-Toegelaten UI.

## De responsieve emulator configureren {#configuring-the-responsive-emulator}

Deze taak laat u de ontvankelijke **Mededinger** op uw plaats zien.

### Uw pagina-componenten registreren voor emulatie {#register-your-page-components-for-emulation}

Als u wilt dat de emulator uw pagina&#39;s ondersteunt, moet u de paginacomponenten registreren. Zie [ Registrerend de Componenten van de Pagina voor Simulatie ](/help/sites-developing/responsive.md#registering-page-components-for-simulation).

### Apparaatgroepen opgeven {#specify-the-device-groups}

Om de apparatengroepen te specificeren die in de lijst van Apparaten van de mededinger verschijnen zie [ specificerend de Groepen van het Apparaat ](/help/sites-developing/responsive.md#specifying-the-device-groups).

### Uw site koppelen aan de opgegeven apparaatgroepen {#link-your-site-to-the-specified-device-groups}

Als u de emulator wilt opnemen, koppelt u uw site aan de apparaatgroepen. Zie [ Toevoegend de Lijst van Apparaten ](/help/sites-developing/responsive.md#adding-the-devices-list) (voor zowel klassieke als aanraking-geoptimaliseerde UI).

## Lay-outmodus voor uw site activeren {#activate-layout-mode-for-your-site}

Deze procedures worden gebruikt om de **wijze van de Lay-out** op uw plaats toe te laten.

### De onderbrekingspunten configureren {#configure-the-breakpoints}

[ Onderbrekingspunten ](/help/sites-authoring/responsive-layout.md#selecting-a-device-to-emulate):

* Wordt gebruikt in responsief ontwerp.
* Kan worden gedefinieerd:

   * Op het paginasjabloon, vanaf waar de instellingen worden gekopieerd naar pagina&#39;s die met die sjabloon zijn gemaakt.
   * Op het paginaknooppunt, vanwaar de montages door om het even welke kindpagina&#39;s worden geërft.

* Een titel en breedte definiëren:

   * De titel beschrijft de generieke apparatengroepering, met richtlijn indien nodig; bijvoorbeeld, telefoon, tablet, tabletlandscape.
   * De breedte bepaalt de maximumbreedte in pixel voor die generische apparatengroepering. Bijvoorbeeld, als de breekpunttelefoon een breedte van 768 heeft dan dat het de maximumbreedte van de lay-out heeft die voor een telefoonapparaat wordt gebruikt.

* U kunt de emulator gebruiken als markeringen boven aan de pagina-editor.
* Wordt overgeërfd van de hiërarchie van de ouderknoop en kan bij wil worden met voeten getreden.
* Er is een gebrek (uit-van-de-doos) breekpunt dat alles boven het laatste *gevormde* breekpunt behandelt.

Ze kunnen worden gedefinieerd met CRXDE Lite of XML.

>[!NOTE]
>
>Als u een nieuw project instelt:
>
>* Voeg onderbrekingspunten toe aan de sjablonen.
>
>Als u een bestaand project (met bestaande inhoud) migreert, moet u:
>
>* Onderbrekingspunten toevoegen aan de sjablonen
>* Voeg dezelfde onderbrekingspunten toe aan de bestaande pagina&#39;s
>
>  Aangezien de overerving in verrichting is, kunt u dit tot de wortelpagina van uw inhoud beperken.

#### Onderbrekingspunten configureren met CRXDE Lite {#configuring-breakpoints-using-crxde-lite}

1. Met CRXDE Lite (of een equivalent) navigeert u naar:

   * Uw sjabloondefinitie.
   * The `jcr:content` node of your page.

1. Onder `jcr:content` maakt u het knooppunt:

   * Naam: `cq:responsive`
   * Type: `nt:unstructured`

1. Onder dit creeer de knoop:

   * Naam: `breakpoints`
   * Type: `nt:unstructured`

1. Onder het knooppunt voor onderbrekingspunten kunt u een willekeurig aantal onderbrekingspunten maken. Elke definitie is één knooppunt met de volgende eigenschappen:

   * Naam: `<descriptive name>`
   * Type: `nt:unstructured`
   * Titel: `String` * `<descriptive title seen in Emulator>`*
   * Breedte: `Decimal` * `<value of breakpoint>` *

#### Onderbrekingspunten configureren met XML {#configuring-breakpoints-using-xml}

Onderbrekingspunten bevinden zich in de `<jcr:content>` -sectie van `.context.html` onder de toepasselijke sjabloonmap (of inhoudsmap).

Een voorbeelddefinitie:

```html
<cq:responsive jcr:primaryType="nt:unstructured">
  <breakpoints jcr:primaryType="nt:unstructured">
    <phone jcr:primaryType="nt:unstructured" title="{String}Phone" width="{Decimal}768"/>
    <tablet jcr:primaryType="nt:unstructured" title="{String}Tablet" width="{Decimal}1200"/>
  </breakpoints>
</cq:responsive>
```

### Een provider van responsieve informatie toevoegen {#add-a-responsive-information-provider}

>[!NOTE]
>
>Dit is alleen nodig als de paginacomponent niet is gebaseerd op de component van de basispagina.

Kopieer de volgende `cq:infoProviders` nodestructuur naar de bovenliggende pagina-component:

`/libs/foundation/components/page/cq:infoProviders/responsive`

## Component resizing voor de pagina inschakelen {#enable-component-resizing-for-the-page}

Deze procedures worden vereist zodat kunt u componenten op de **wijze van de Lay-out** resize.

### De container van de Lay-out instellen als HoofdParsys {#set-layout-container-as-main-parsys}

Om hoofdparsys van uw pagina te plaatsen om een lay-outcontainer te zijn, bepaal parsys als:

`wcm/foundation/components/responsivegrid`

In één van beide:

* Pagina-component
* Paginasjabloon (voor toekomstig gebruik)

De volgende twee voorbeelden illustreren de definitie:

* **HTML:**

  ```html
  <sly data-sly-resource="${'par' @ resourceType='wcm/foundation/components/responsivegrid'}/>
  ```

* **JSP:**

  ```html
  <cq:include path="par" resourceType="wcm/foundation/components/responsivegrid" />
  ```

### Inclusief de responsieve CSS {#include-the-responsive-css}

#### CSS voor onderbrekingspunten die MINDER gebruiken {#css-for-breakpoints-using-less}

AEM gebruikt LESS om delen van noodzakelijke CSS te produceren, deze moeten voor uw projecten worden omvat.

U zult ook a [ cliëntbibliotheek ](https://experienceleague.adobe.com/docs/) moeten creëren om extra configuratie en functievraag te verstrekken. Het volgende LESS extract is een voorbeeld van het minimum dat u aan uw project moet toevoegen:

```css
@import (once) "/libs/wcm/foundation/clientlibs/grid/grid_base.less";

/* maximum amount of grid cells to be provided */
@max_col: 12;

/* default breakpoint */
.aem-Grid {
  .generate-grid(default, @max_col);
}

/* phone breakpoint */
@media (max-width: 768px) {
  .aem-Grid {
    .generate-grid(phone, @max_col);
  }
}

/* tablet breakpoint */
@media (min-width: 769px) and (max-width: 1200px) {
  .aem-Grid {
    .generate-grid(tablet, @max_col);
  }
}
```

De definitie van het basisraster is te vinden onder:

`/libs/wcm/foundation/clientlibs/grid/grid_base.less`

#### Overwegingen bij opmaken {#styling-considerations}

Componenten die in een responsieve container worden vastgehouden, worden vergroot of verkleind (samen met hun respectievelijke HTML DOM-elementen) op basis van de responsieve rastergrootte. Daarom wordt in deze omstandigheden aanbevolen definities van DOM-elementen met een vaste breedte (bevat) te vermijden (of bij te werken).

Bijvoorbeeld:

* Voor:

   * `width=100px`

* Na:

   * `max-width=100px`

#### Compatibiliteit van afbeeldingen vergroten/verkleinen en aanpassen {#resizing-and-adaptive-image-compliance}

Als u de grootte van een component in het raster wijzigt, worden de volgende listeners geactiveerd, indien van toepassing:

* `beforeedit`
* `beforechildedit`
* `afteredit`

* `afterchildedit`

Als u de inhoud van een adaptieve afbeelding in een responsief raster op de juiste wijze wilt vergroten of verkleinen en bijwerken, moet u een `afterEdit` set to `REFRESH_PAGE` listener toevoegen aan het `EditConfig` -bestand van elke component in de component.

Bijvoorbeeld:

`<cq:listeners jcr:primaryType="cq:EditListenersConfig" afteredit="REFRESH_PAGE" />`

Het mechanisme voor adaptieve afbeeldingen is beschikbaar via een script dat de selectie van de juiste afbeelding voor de huidige grootte van het venster bepaalt. De gebeurtenis wordt geactiveerd nadat de DOM gereed is of wanneer een specifieke gebeurtenis wordt ontvangen. De pagina moet momenteel worden vernieuwd om het resultaat van de actie van de gebruiker correct weer te geven.

>[!CAUTION]
>
>Aangepaste stijlbladclientlibs moeten als onderdeel van de koptekst worden geladen, anders werken ze niet goed bij de auteur en publiceren.

## De Containercomponent voor lay-out inschakelen voor pagina {#enable-the-layout-container-component-for-page}

Deze taken staan auteurs toe om instanties van de **component van de Container van de Lay-out** op de pagina te slepen.

### De Containercomponent voor lay-out inschakelen voor paginabewerking {#enable-the-layout-container-component-for-page-editing}

Auteurs kunnen meer responsieve rasters toevoegen aan de inhoudspagina&#39;s als u de component Layout Container voor uw pagina wilt inschakelen. U kunt dit doen door:

* **Milieu van de Auteur**

  De wijze van het Ontwerp van het gebruik ](/help/sites-authoring/default-components-designmode.md) om de **Container van de Laag** component voor een pagina te activeren.[

* **de Definitie van de Component**

  Gebruik `allowedComponent` of een statische include-bestand wanneer u de component definieert.

### Het raster van de container van de layout configureren {#configure-the-grid-of-the-layout-container}

U kunt het aantal beschikbare kolommen voor elke specifieke instantie van lay-outcontainer vormen:

1. **Milieu van de Auteur**

   U kunt het aantal kolommen vormen beschikbaar voor elke specifieke instantie van lay-outcontainer.

   Om dit te doen, gebruik {de wijze van het 0} Ontwerp ](/help/sites-authoring/default-components-designmode.md), dan open de ontwerpdialoog voor de vereiste container. [ Hier kunt u opgeven hoeveel kolommen beschikbaar zijn voor positionering en grootte. De standaardwaarde is 12.

1. **XML**

   Definities voor het responsieve raster worden opgegeven in:

   `etc/design/<*your-project-name*>/.content.xml`

   De volgende parameters kunnen worden gedefinieerd:

   * Aantal beschikbare kolommen:

      * `columns="{String}8"`

   * Componenten die aan de huidige component kunnen worden toegevoegd:

      * `components="[/libs/wcm/foundation/components/responsivegrid, ...`

## Geneste responsieve rasters {#nested-responsive-grids}

Het kan voorkomen dat u responsieve rasters moet nesten om de behoeften van uw project te ondersteunen. Houd er echter rekening mee dat de aanbevolen werkwijze van Adobe erin bestaat de structuur zo vlak mogelijk te houden.

Zorg ervoor dat wanneer u het gebruik van geneste responsieve rasters niet kunt vermijden:

* Alle containers (containers, tabbladen, accordeons, enz.) hebben de eigenschap `layout = responsiveGrid` .
* Meng de eigenschap `layout = simple` niet in de containerhiërarchie.

Dit omvat alle structurele containers van het paginasjabloon.

Het kolomnummer van de binnencontainer mag nooit groter zijn dan dat van de buitencontainer. In het volgende voorbeeld wordt aan deze voorwaarde voldaan. Terwijl het kolomnummer van de buitencontainer 8 is voor het standaardscherm (bureaublad), is het kolomnummer van de binnencontainer 4.

>[!BEGINTABS]

>[!TAB  Structuur van de Knoop van het Voorbeeld ]

```text
container
  @layout = responsiveGrid
  cq:responsive
    default
      @offset = 0
      @width = 8
  container
  @layout = responsiveGrid
    cq:responsive
      default
        @offset = 0
        @width = 4
    text
      @text =" Text Column 1"
```

>[!TAB  Voorbeeld resulterend HTML ]

```html
<div class="container responsivegrid aem-GridColumn--default--none aem-GridColumn aem-GridColumn--default--8 aem-GridColumn--offset--default--0">
  <div id="container-c9955c233c" class="cmp-container">
    <div class="aem-Grid aem-Grid--8 aem-Grid--default--8 ">
      <div class="container responsivegrid aem-GridColumn--default--none aem-GridColumn aem-GridColumn--offset--default--0 aem-GridColumn--default--4">
        <div id="container-8414e95866" class="cmp-container">
          <div class="aem-Grid aem-Grid--4 aem-Grid--default--4 ">
            <div class="text aem-GridColumn aem-GridColumn--default--4">
              <div data-cmp-data-layer="..." id="text-1234567890" class="cmp-text">
                <p>Text Column 1</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>
```

>[!ENDTABS]
