---
title: Container en lay-outmodus voor lay-out configureren
seo-title: Container en lay-outmodus voor lay-out configureren
description: Leer hoe u de container van de lay-out en de lay-outmodus configureert.
seo-description: Leer hoe u de container van de lay-out en de lay-outmodus configureert.
uuid: 952b7c86-76ab-4699-8530-8638e46bb50f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: 10940000-808a-48ae-8e46-61eccef71eab
legacypath: /content/docs/en/aem/6-2/administer/operations/page-authoring/configuring-responsive-layouting
translation-type: tm+mt
source-git-commit: ebf3f34af7da6b1a659ac8d8843152b97f30b652
workflow-type: tm+mt
source-wordcount: '1324'
ht-degree: 1%

---


# Container en lay-outmodus voor lay-out configureren{#configuring-layout-container-and-layout-mode}

[Responsieve lay-out](/help/sites-authoring/responsive-layout.md) is een mechanisme voor het realiseren van [responsieve webontwerpen](https://en.wikipedia.org/wiki/Responsive_web_design). Hierdoor kan de gebruiker webpagina&#39;s maken met een indeling en afmetingen die afhankelijk zijn van de apparaten die de gebruikers gebruiken.

>[!NOTE]
>
>Dit kan worden vergeleken met de mechanismen voor [mobiel web](/help/sites-developing/mobile-web.md) , die een adaptief webontwerp gebruiken (voornamelijk voor de klassieke gebruikersinterface).

AEM realiseert een responsieve indeling voor uw pagina&#39;s met behulp van een combinatie van mechanismen:

* [**Containercomponent **](/help/sites-authoring/responsive-layout.md#adding-a-layout-container-and-its-content-edit-mode)layout

   Deze component biedt een rasteralineasysteem waarmee u componenten kunt toevoegen en positioneren binnen een responsief raster. Het kan als standaardparsys voor uw pagina worden gebruikt en/of ter beschikking gesteld aan auteurs in componentenbrowser.

   * De standaardcomponent **Container** voor lay-out wordt hieronder gedefinieerd:

      /libs/wcm/foundation/components/responsivegrid

   * U kunt lay-outcontainers definiëren:

      * Als een component die de gebruiker aan een pagina kan toevoegen.
      * Als standaardparsys voor de pagina.
      * Beide.

         U kunt de lay-outcontainer als standaard voor de pagina hebben, terwijl het toestaan van de gebruiker om verdere lay-outcontainers binnen dit toe te voegen; bijvoorbeeld om kolombesturing te bereiken.

* **[Lay-outmodus](/help/sites-authoring/responsive-layout.md#defining-layouts-layout-mode)**Zodra de lay-outcontainer op de pagina is geplaatst, kunt u de **modus Lay-out**gebruiken om inhoud binnen het responsieve raster te plaatsen.

* [**Emulator **](/help/sites-authoring/responsive-layout.md#selecting-a-device-to-emulate)Hiermee kunt u responsieve websites maken en bewerken die de lay-out op basis van de grootte van het apparaat/venster opnieuw rangschikken door de grootte van componenten interactief aan te passen. De gebruiker kan dan zien hoe de inhoud wordt gerenderd met de emulator.

>[!CAUTION]
>
>Hoewel de component **Layout Container** beschikbaar is in de klassieke gebruikersinterface, is de volledige functionaliteit alleen beschikbaar in de gebruikersinterface met aanraakbediening.

Met deze responsieve rastermechanismen kunt u:

* Gebruik onderbrekingspunten (die apparaatgroepering aangeven) om een verschillend gedrag voor de inhoud te definiëren op basis van de apparaatlay-out.
* Componenten verbergen op basis van apparaatgroep (definiëren op welk onderbrekingspunt een component wordt verborgen).
* Gebruik horizontale uitlijning op het raster (plaats componenten in het raster, wijzig de grootte naar wens en definieer wanneer ze naast elkaar of boven/onder moeten samenvouwen/opnieuw moeten plaatsen).
* Kolombesturingselement realiseren.

>[!NOTE]
>
>In een out-of-the-box installatie, is de ontvankelijke lay-out gevormd voor de [Wij.Retail verwijzingsplaats](/help/sites-developing/we-retail.md). U moet de component [van de Container van de Lay-out voor andere pagina&#39;s nog](#enable-the-layout-container-component-for-page) activeren.

## De responsieve emulator configureren {#configuring-the-responsive-emulator}

Hierdoor kunt u de responsieve **emulator** op uw site zien.

### Uw pagina-componenten registreren voor emulatie {#register-your-page-components-for-emulation}

Als u wilt dat de emulator uw pagina&#39;s ondersteunt, moet u de paginacomponenten registreren. Zie Pagina-componenten [registreren voor simulatie](/help/sites-developing/responsive.md#registering-page-components-for-simulation).

### Apparaatgroepen opgeven {#specify-the-device-groups}

Zie [Apparaatgroepen](/help/sites-developing/responsive.md#specifying-the-device-groups)opgeven om de apparaatgroepen op te geven die worden weergegeven in de lijst Apparaten van de emulator.

### Uw site koppelen aan de opgegeven apparaatgroepen {#link-your-site-to-the-specified-device-groups}

Als u de emulator wilt opnemen, moet u uw site koppelen aan de apparaatgroepen. Zie [De lijst](/help/sites-developing/responsive.md#adding-the-devices-list) met apparaten toevoegen (voor zowel de klassieke gebruikersinterface als de gebruikersinterface die is geoptimaliseerd voor aanrakingen).

## Lay-outmodus voor uw site activeren {#activate-layout-mode-for-your-site}

Deze procedures worden gebruikt om de **lay-outmodus** op uw site in te schakelen.

### De onderbrekingspunten configureren {#configure-the-breakpoints}

[Onderbrekingspunten](/help/sites-authoring/responsive-layout.md#selecting-a-device-to-emulate):

* Wordt gebruikt in responsief ontwerp.
* Kan worden gedefinieerd:

   * Op het paginasjabloon, vanaf waar de instellingen worden gekopieerd naar pagina&#39;s die met die sjabloon zijn gemaakt.
   * Op het paginaknooppunt, vanwaar de montages door om het even welke kindpagina&#39;s zullen worden geërft.

* Een titel en breedte definiëren:

   * De titel beschrijft de generieke apparaatgroep, zo nodig met oriëntatie; bijvoorbeeld telefoon, tablet, tabletlandscape.
   * De breedte bepaalt de maximumbreedte in pixel voor die generische apparatengroepering. Bijvoorbeeld, als de breekpunttelefoon een breedte van 768 heeft dan dat het de maximumbreedte van de lay-out heeft die voor een telefoonapparaat wordt gebruikt.

* U kunt de emulator gebruiken als markeringen boven aan de pagina-editor.
* Wordt overgeërfd van de hiërarchie van de ouderknoop en kan bij wil worden met voeten getreden.
* Er is een standaardbreekpunt (uit-van-de-doos) dat alles boven het laatste *gevormde* breekpunt behandelt.

Ze kunnen worden gedefinieerd met behulp van CRXDE Lite of XML.

>[!NOTE]
>
>Als u een nieuw project instelt:
>
>* u moet onderbrekingspunten toevoegen aan de sjablonen.
>
>
Als u een bestaand project (met bestaande inhoud) migreert, moet u:
>
>* Onderbrekingspunten toevoegen aan de sjablonen
>* Voeg dezelfde onderbrekingspunten toe aan de bestaande pagina&#39;s
>
>  
Aangezien de overerving in verrichting is, kunt u dit tot de wortelpagina van uw inhoud beperken.

#### Onderbrekingspunten configureren met behulp van CRXDE Lite {#configuring-breakpoints-using-crxde-lite}

1. Navigeer met behulp van CRXDE Lite (of equivalent) naar:

   * Uw sjabloondefinitie.
   * Het `jcr:content` knooppunt van de pagina.

1. Onder `jcr:content` maak het knooppunt:

   * Naam: `cq:responsive`
   * Type: `nt:unstructured`

1. Onder dit creeer de knoop:

   * Naam: `breakpoints`
   * Type: `nt:unstructured`

1. Onder het knooppunt voor onderbrekingspunten kunt u een willekeurig aantal onderbrekingspunten maken. Elke definitie is één knooppunt met de volgende eigenschappen:

   * Naam: `<descriptive name>`
   * Type: `nt:unstructured`
   * Titel: `String` * `<descriptive title seen in Emulator>`*
   * Breedte: `Decimal` * `<value of breakpoint>`*

#### Onderbrekingspunten configureren met XML {#configuring-breakpoints-using-xml}

Onderbrekingspunten bevinden zich in de `<jcr:content>` sectie van de sjabloon `.context.html` onder de toepasselijke sjabloonmap (of inhoudsmap).

Een voorbeelddefinitie:

```xml
<cq:responsive jcr:primaryType="nt:unstructured">
  <breakpoints jcr:primaryType="nt:unstructured">
    <phone jcr:primaryType="nt:unstructured" title="{String}Phone" width="{Decimal}768"/>
    <tablet jcr:primaryType="nt:unstructured" title="{String}Tablet" width="{Decimal}1200"/>
  </breakpoints>
</cq:responsive>
```

### Een responsieve informatieprovider toevoegen {#add-a-responsive-information-provider}

>[!NOTE]
>
>Dit is alleen nodig als de paginacomponent niet is gebaseerd op de component van de basispagina.

Kopieer de volgende `cq:infoProviders` knooppuntstructuur naar de bovenliggende pagina-component:

`/libs/foundation/components/page/cq:infoProviders/responsive`

## Component resizing voor de pagina inschakelen {#enable-component-resizing-for-the-page}

Deze procedures zijn vereist, zodat u de grootte van componenten in de **modus Lay-out** kunt wijzigen.

### De container van de Lay-out instellen als HoofdParsys {#set-layout-container-as-main-parsys}

Om hoofdparsys van uw pagina te plaatsen om een lay-outcontainer te zijn moet u parsys als bepalen:

`wcm/foundation/components/responsivegrid`

In één van beide:

* Pagina-component
* Paginasjabloon (voor toekomstig gebruik)

De volgende twee voorbeelden illustreren de definitie:

* **HTML:**

   ```xml
   <sly data-sly-resource="${'par' @ resourceType='wcm/foundation/components/responsivegrid'}/>
   ```

* **JSP:**

   ```
   <cq:include path="par" resourceType="wcm/foundation/components/responsivegrid" />
   ```

### Inclusief de responsieve CSS {#include-the-responsive-css}

#### CSS voor onderbrekingspunten die MINDER gebruiken {#css-for-breakpoints-using-less}

AEM gebruikt LESS om delen van noodzakelijke CSS te produceren, deze moeten voor uw projecten worden omvat.

U zult ook een [cliëntbibliotheek](https://docs.adobe.com/content/docs/en/aem/6-0/develop/the-basics/clientlibs.html) moeten tot stand brengen om extra configuratie en functievraag te verstrekken. Het volgende LESS extract is een voorbeeld van het minimum u aan uw project moet toevoegen:

```java
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

De basisrasterdefinitie is te vinden onder:

`/libs/wcm/foundation/clientlibs/grid/grid_base.less`

#### Overwegingen bij opmaken {#styling-considerations}

De grootte van componenten die in een responsieve container worden gehouden, wordt aangepast (samen met hun respectievelijke HTML DOM-elementen) aan de responsieve rastergrootte. Daarom wordt in deze omstandigheden aanbevolen definities van DOM-elementen met een vaste breedte (bevat) te vermijden (of bij te werken).

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

Als u de inhoud van een adaptieve afbeelding die is opgenomen in een responsief raster op de juiste wijze wilt vergroten of verkleinen en bijwerken, moet u een `afterEdit` set aan `REFRESH_PAGE` listener toevoegen aan het `EditConfig` bestand van elke component in de component.

Bijvoorbeeld:

`<cq:listeners jcr:primaryType="cq:EditListenersConfig" afteredit="REFRESH_PAGE" />`

Het mechanisme voor adaptieve afbeeldingen is beschikbaar via een script dat de selectie van de juiste afbeelding voor de huidige grootte van het venster bepaalt. De gebeurtenis wordt geactiveerd nadat de DOM gereed is of wanneer een specifieke gebeurtenis wordt ontvangen. De pagina moet momenteel worden vernieuwd om het resultaat van de actie van de gebruiker correct weer te geven.

>[!CAUTION]
>
>Aangepaste stijlbladclientlibs moeten worden geladen als onderdeel van de koptekst, anders kunnen ze niet alleen worden gepubliceerd, maar ook goed werken op de auteur.

## De Containercomponent voor lay-out inschakelen voor pagina {#enable-the-layout-container-component-for-page}

Met deze taken kunnen auteurs instanties van de **component Layout Container** naar de pagina slepen.

### De Containercomponent voor lay-out inschakelen voor paginabewerking {#enable-the-layout-container-component-for-page-editing}

Auteurs kunnen meer responsieve rasters toevoegen aan de inhoudspagina&#39;s als u de component Layout Container voor uw pagina wilt inschakelen. U kunt dit doen door:

* **Auteursomgeving**

   Gebruik de modus [](/help/sites-authoring/default-components-designmode.md) Ontwerpen om de component **Laagcontainer** voor een pagina te activeren.

* **Componentdefinitie**

   Gebruik `allowedComponent` of statisch include-bestand bij het definiëren van de component.

### Het raster van de container van de layout configureren {#configure-the-grid-of-the-layout-container}

U kunt het aantal beschikbare kolommen voor elke specifieke instantie van lay-outcontainer vormen:

1. **Auteursomgeving**

   U kunt het aantal kolommen vormen beschikbaar voor elke specifieke instantie van lay-outcontainer.

   Hiervoor gebruikt u de [ontwerpmodus](/help/sites-authoring/default-components-designmode.md)en opent u het dialoogvenster Ontwerp voor de vereiste container. Hier kunt u opgeven hoeveel kolommen beschikbaar zijn voor positionering en grootte. De standaardwaarde is 12.

1. **XML**

   Definities voor het responsieve raster worden opgegeven in:

   `etc/design/<*your-project-name*>/.content.xml`

   De volgende parameters kunnen worden gedefinieerd:

   * Aantal beschikbare kolommen:

      * `columns="{String}8"`
   * Componenten die aan de huidige component kunnen worden toegevoegd:

      * `components="[/libs/wcm/foundation/components/responsivegrid, ...`


