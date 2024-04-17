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
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '1275'
ht-degree: 0%

---

# Container en lay-outmodus configureren{#configuring-layout-container-and-layout-mode}

[Responsieve lay-out](/help/sites-authoring/responsive-layout.md) is een mechanisme om te realiseren [responsief webontwerp](https://en.wikipedia.org/wiki/Responsive_web_design). Hierdoor kan de gebruiker webpagina&#39;s maken met een indeling en afmetingen die afhankelijk zijn van de apparaten die de gebruikers gebruiken.

>[!NOTE]
>
>Dit kan worden vergeleken met de [Mobiel web](/help/sites-developing/mobile-web.md) mechanismen die gebruikmaken van adaptief webontwerp (voornamelijk voor de klassieke interface).

AEM realiseert responsieve lay-out voor uw pagina&#39;s gebruikend een combinatie mechanismen:

* [**Layout Container**](/help/sites-authoring/responsive-layout.md#adding-a-layout-container-and-its-content-edit-mode) component

  Deze component verstrekt een net-paragraaf systeem om u toe te voegen en componenten binnen een ontvankelijk net te plaatsen. Het kan als standaardparsys voor uw pagina worden gebruikt en/of ter beschikking gesteld aan auteurs in componentenbrowser.

   * De standaardwaarde **Layout Container** component wordt gedefinieerd onder:

     /libs/wcm/foundation/components/responsivegrid

   * U kunt lay-outcontainers definiëren:

      * Als een component die de gebruiker aan een pagina kan toevoegen.
      * Als standaardparsys voor de pagina.
      * Beide.

        U kunt de lay-outcontainer als standaard voor de pagina hebben, terwijl het toestaan van de gebruiker om verdere lay-outcontainers binnen dit toe te voegen; bijvoorbeeld, om kolomcontrole te bereiken.

* **[Lay-outmodus](/help/sites-authoring/responsive-layout.md#defining-layouts-layout-mode)**
Als de lay-outcontainer eenmaal op de pagina is geplaatst, kunt u de opdracht **Layout** om de inhoud binnen het responsieve raster te plaatsen.

* [**Emulator**](/help/sites-authoring/responsive-layout.md#selecting-a-device-to-emulate)
Zo kunt u responsieve websites maken en bewerken die de lay-out op basis van de grootte van het apparaat of venster opnieuw rangschikken door de grootte van componenten interactief aan te passen. De gebruiker kan dan zien hoe de inhoud wordt gerenderd met de emulator.

>[!CAUTION]
>
>Hoewel de **Layout Container** is beschikbaar in de klassieke UI, is zijn volledige functionaliteit slechts beschikbaar in aanraking-toegelaten UI.

Met deze responsieve rastermechanismen kunt u:

* Gebruik onderbrekingspunten (die apparaatgroepering aangeven) om een verschillend gedrag voor de inhoud te definiëren op basis van de apparaatlay-out.
* Componenten verbergen op basis van apparaatgroep (definiëren op welk onderbrekingspunt een component wordt verborgen).
* Gebruik horizontale uitlijning op het raster (plaats componenten in het raster, wijzig de grootte naar wens en definieer wanneer ze naast elkaar of boven/onder moeten samenvouwen/opnieuw moeten plaatsen).
* Kolombesturingselement realiseren.

>[!NOTE]
>
>In een installatie buiten de doos, is de ontvankelijke lay-out gevormd voor [We.Retail-referentiesite](/help/sites-developing/we-retail.md). [De component Layout Container activeren](#enable-the-layout-container-component-for-page) voor andere pagina&#39;s.

## De responsieve emulator configureren {#configuring-the-responsive-emulator}

Met deze taak kunt u de responsieve **Emulator** op uw site.

### Uw pagina-componenten registreren voor emulatie {#register-your-page-components-for-emulation}

Als u wilt dat de emulator uw pagina&#39;s ondersteunt, moet u de paginacomponenten registreren. Zie [Pagina-componenten registreren voor simulatie](/help/sites-developing/responsive.md#registering-page-components-for-simulation).

### Apparaatgroepen opgeven {#specify-the-device-groups}

Zie voor informatie over de apparaatgroepen die worden weergegeven in de lijst met apparaten van de emulator [Apparaatgroepen opgeven](/help/sites-developing/responsive.md#specifying-the-device-groups).

### Uw site koppelen aan de opgegeven apparaatgroepen {#link-your-site-to-the-specified-device-groups}

Als u de emulator wilt opnemen, koppelt u uw site aan de apparaatgroepen. Zie [De lijst met apparaten toevoegen](/help/sites-developing/responsive.md#adding-the-devices-list) (voor zowel de klassieke gebruikersinterface als de gebruikersinterface met aanraakfuncties).

## Lay-outmodus voor uw site activeren {#activate-layout-mode-for-your-site}

Deze procedures worden gebruikt om de **Layout** op uw site.

### De onderbrekingspunten configureren {#configure-the-breakpoints}

[Onderbrekingspunten](/help/sites-authoring/responsive-layout.md#selecting-a-device-to-emulate):

* Wordt gebruikt in responsief ontwerp.
* Kan worden gedefinieerd:

   * Op het paginasjabloon, vanaf waar de instellingen worden gekopieerd naar pagina&#39;s die met die sjabloon zijn gemaakt.
   * Op het paginaknooppunt, vanwaar de montages door om het even welke kindpagina&#39;s worden geërft.

* Een titel en breedte definiëren:

   * De titel beschrijft de generieke apparatengroepering, met richtlijn indien nodig; bijvoorbeeld, telefoon, tablet, tabletlandscape.
   * De breedte bepaalt de maximumbreedte in pixel voor die generische apparatengroepering. Bijvoorbeeld, als de breekpunttelefoon een breedte van 768 heeft dan dat het de maximumbreedte van de lay-out heeft die voor een telefoonapparaat wordt gebruikt.

* U kunt de emulator gebruiken als markeringen boven aan de pagina-editor.
* Wordt overgeërfd van de hiërarchie van de ouderknoop en kan bij wil worden met voeten getreden.
* Er is een standaardbreekpunt (uit-van-de-doos) dat alles boven het laatste behandelt *geconfigureerd* breekpunt.

Ze kunnen worden gedefinieerd met behulp van CRXDE Lite of XML.

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

1. Navigeer met behulp van CRXDE Lite (of equivalent) naar:

   * Uw sjabloondefinitie.
   * De `jcr:content` knooppunt van uw pagina.

1. Onder `jcr:content` Maak het knooppunt:

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

Onderbrekingspunten bevinden zich in de `<jcr:content>` van de `.context.html` in de juiste sjabloonmap (of inhoudsmap).

Een voorbeelddefinitie:

```xml
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

Kopieer het volgende `cq:infoProviders` knooppuntstructuur in uw bovenliggende paginacomponent:

`/libs/foundation/components/page/cq:infoProviders/responsive`

## Component resizing voor de pagina inschakelen {#enable-component-resizing-for-the-page}

Deze procedures zijn vereist zodat u de grootte van componenten in de **Layout** -modus.

### De container van de Lay-out instellen als HoofdParsys {#set-layout-container-as-main-parsys}

Om hoofdparsys van uw pagina te plaatsen om een lay-outcontainer te zijn, bepaal parsys als:

`wcm/foundation/components/responsivegrid`

In één van beide:

* Pagina-component
* Paginasjabloon (voor toekomstig gebruik)

De volgende twee voorbeelden illustreren de definitie:

* **HTL:**

  ```xml
  <sly data-sly-resource="${'par' @ resourceType='wcm/foundation/components/responsivegrid'}/>
  ```

* **JSP:**

  ```
  <cq:include path="par" resourceType="wcm/foundation/components/responsivegrid" />
  ```

### Inclusief de responsieve CSS {#include-the-responsive-css}

#### CSS voor onderbrekingspunten die MINDER gebruiken {#css-for-breakpoints-using-less}

AEM gebruikt LESS om delen van noodzakelijke CSS te produceren, moeten deze voor uw projecten worden omvat.

U moet ook een [clientbibliotheek](https://experienceleague.adobe.com/docs/) om extra configuratie en functievraag te verstrekken. Het volgende LESS extract is een voorbeeld van het minimum dat u aan uw project moet toevoegen:

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

Als u de inhoud van een adaptieve afbeelding in een responsief raster op de juiste wijze wilt vergroten of verkleinen en bijwerken, moet u een `afterEdit` instellen op `REFRESH_PAGE` listener in de `EditConfig` bestand van elke component in het bestand.

Bijvoorbeeld:

`<cq:listeners jcr:primaryType="cq:EditListenersConfig" afteredit="REFRESH_PAGE" />`

Het mechanisme voor adaptieve afbeeldingen is beschikbaar via een script dat de selectie van de juiste afbeelding voor de huidige grootte van het venster bepaalt. De gebeurtenis wordt geactiveerd nadat de DOM gereed is of wanneer een specifieke gebeurtenis wordt ontvangen. De pagina moet momenteel worden vernieuwd om het resultaat van de actie van de gebruiker correct weer te geven.

>[!CAUTION]
>
>Aangepaste stijlbladclientlibs moeten als onderdeel van de koptekst worden geladen, anders werken ze niet goed bij de auteur en publiceren.

## De Containercomponent voor lay-out inschakelen voor pagina {#enable-the-layout-container-component-for-page}

Met deze taken kunnen auteurs instanties van de **Layout Container** op de pagina.

### De Containercomponent voor lay-out inschakelen voor paginabewerking {#enable-the-layout-container-component-for-page-editing}

Auteurs kunnen meer responsieve rasters toevoegen aan de inhoudspagina&#39;s als u de component Layout Container voor uw pagina wilt inschakelen. U kunt dit doen door:

* **Auteursomgeving**

  Gebruiken [Ontwerpmodus](/help/sites-authoring/default-components-designmode.md) om de **Laagcontainer** voor een pagina.

* **Componentdefinitie**

  Gebruiken `allowedComponent` of een statische include-opdracht wanneer de component wordt gedefinieerd.

### Het raster van de container van de layout configureren {#configure-the-grid-of-the-layout-container}

U kunt het aantal beschikbare kolommen voor elke specifieke instantie van lay-outcontainer vormen:

1. **Auteursomgeving**

   U kunt het aantal kolommen vormen beschikbaar voor elke specifieke instantie van lay-outcontainer.

   Om dit te doen, gebruik [Ontwerpmodus](/help/sites-authoring/default-components-designmode.md)Open vervolgens het dialoogvenster voor het ontwerp van de vereiste container. Hier kunt u opgeven hoeveel kolommen beschikbaar zijn voor positionering en grootte. De standaardwaarde is 12.

1. **XML**

   Definities voor het responsieve raster worden opgegeven in:

   `etc/design/<*your-project-name*>/.content.xml`

   De volgende parameters kunnen worden gedefinieerd:

   * Aantal beschikbare kolommen:

      * `columns="{String}8"`

   * Componenten die aan de huidige component kunnen worden toegevoegd:

      * `components="[/libs/wcm/foundation/components/responsivegrid, ...`
