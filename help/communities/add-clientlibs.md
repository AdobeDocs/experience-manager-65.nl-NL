---
title: Clientlibs toevoegen
description: Leer hoe u een ClientLibraryFolder (clientlibs) toevoegt die wordt gebruikt om de JavaScript en Cascading Style Sheets te bevatten die worden gebruikt om de pagina's van uw site weer te geven.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
docset: aem65
exl-id: 569f2052-b4fe-4f7f-aec9-657217cba091
solution: Experience Manager
feature: Communities
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '690'
ht-degree: 0%

---

# Clientlibs toevoegen {#add-clientlibs}

## Een ClientLibraryFolder (clientlibs) toevoegen {#add-a-clientlibraryfolder-clientlibs}

Maak een ClientLibraryFolder met de naam `clientlibs` die de JavaScript (JS) en de Cascading Styles Sheets (CSS) bevat die worden gebruikt om de pagina&#39;s van uw site weer te geven.

De waarde van de eigenschap `categories` die aan deze clientbibliotheek wordt gegeven, is de id die wordt gebruikt om deze clientlib rechtstreeks vanaf een inhoudspagina in te sluiten of om deze in andere clientlibs in te sluiten.

1. Gebruikend **CRXDE Lite**, breid `/etc/designs` uit

1. Klik met de rechtermuisknop `an-scf-sandbox` en selecteer `Create Node`

   * Name : `clientlibs`
   * Type: `cq:ClientLibraryFolder`

1. Klik **O.K.**

![ toe:voegen-cliënt-bibliotheek ](assets/add-client-library.png)

In het **lusje van Eigenschappen** voor de nieuwe `clientlibs` knoop, ga het **categorieën** bezit in:

* Naam: **categorieën**
* Type: **Koord**
* Waarde: **apps.an-scf-zandbak**
* Klik **toevoegen**
* Klik **sparen allen**

Opmerking: geef de waarde voor categorieën een voorvoegsel met &#39;apps&#39;. is een conventie om aan te geven dat de &#39;toepassing die eigenaar is&#39; zich in de map /apps bevindt, niet /libs. BELANGRIJK: voeg plaatsaanduidingen voor `js.tx` t- en **`css.txt`** -bestanden toe. (Zonder deze bestanden is het officieel geen cq:ClientLibraryFolder.)

1. Klikken met rechtermuisknop **`/etc/designs/an-scf-sandbox/clientlibs`**
1. Selecteer **tot Dossier leiden...**
1. Ga **Naam in:** `css.txt`
1. Selecteer **tot Dossier leiden...**
1. Ga **Naam in:** `js.txt`
1. Klik **sparen allen**

![ clientlibs-css ](assets/clientlibs-css.png)

De eerste regel van css.txt en js.txt identificeert de basislocatie van waaruit de volgende lijsten met bestanden moeten worden gevonden.

Stel de inhoud van css.txt in op

```
#base=.
 style.css
```

Maak vervolgens een bestand onder clientlibs met de naam style.css en stel de inhoud in op

`body {`

`background-color: #b0c4de;`

`}`

### SCF-clips insluiten {#embed-scf-clientlibs}

In het **lusje van Eigenschappen** voor de `clientlibs` knoop, ga het bezit van het multi-waardeKoord **in bed** in. Dit sluit de noodzakelijke [ cliënt-zijbibliotheken (clientlibs) voor componenten SCF ](/help/communities/client-customize.md#clientlibs-for-scf) in. Voor deze zelfstudie worden veel van de clientlibs die nodig zijn voor de onderdelen Communities toegevoegd.

Dit kan al dan niet de gewenste benadering voor een productiesite zijn aangezien er overwegingen van gemak tegenover grootte/snelheid van de clientlibs die voor elke pagina worden gedownload zijn.

Als u slechts één functie op één pagina gebruikt, kunt u de volledige clientlib van die functie direct op de pagina opnemen, bijvoorbeeld

`% ui:includeClientLib categories=cq.social.hbs.forum" %`

In dit geval, met inbegrip van hen allen en zo de meer basiscliënten SCF die de auteur clientlibs zijn worden geprefereerd:

* Name : **`embed`**
* Type: **`String`**
* Klikken **`Multi`**
* Waarde: **`cq.social.scf`**

   * Er wordt een dialoogvenster weergegeven,
Klik op **`+`** na elke vermelding om de volgende clientlib-categorieën toe te voegen:

      * **`cq.ckeditor`**
      * **`cq.social.author.hbs.comments`**
      * **`cq.social.author.hbs.forum`**
      * **`cq.social.author.hbs.rating`**
      * **`cq.social.author.hbs.reviews`**
      * **`cq.social.author.hbs.voting`**
      * Klik **O.K.**

* Klik **sparen allen**

![ scf-clientlibs ](assets/scf-clientlibs.png)

Zo wordt `/etc/designs/an-scf-sandbox/clientlibs` nu weergegeven in de opslagplaats:

![ scf-clientlibs-mening ](assets/scf-clientlibs1.png)

### Clientlibs opnemen in PlayPage-sjabloon {#include-clientlibs-in-playpage-template}

Zonder de categorie `apps.an-scf-sandbox` ClientLibraryFolder op de pagina toe te voegen, zijn de SCF-componenten niet functioneel en niet opgemaakt omdat de benodigde JavaScript- en CSS-stijlen niet beschikbaar zijn.

Bijvoorbeeld, zonder de clientlibs op te nemen, lijkt de SCF commentaarcomponent ongestileerd:

![ clientlibs-commentaar ](assets/clientlibs-comment.png)

Zodra apps.an-scf-sandbox clientlibs is opgenomen, wordt de stijl van de SCF-commentaarcomponent weergegeven:

![ clientlibs-commentaar-gestileerde ](assets/clientlibs-comment1.png)

De instructie include behoort tot de sectie `head` van het script van `html` . De standaardwaarde **`foundation head.jsp`** bevat een script dat kan worden bedekt: **`headlibs.jsp`** .

**Kopieer headlibs.jsp en omvat clientlibs:**

1. Gebruikend **CRXDE Lite**, uitgezocht **`/libs/foundation/components/page/headlibs.jsp`**

1. Klik met de rechtermuisknop en selecteer **Exemplaar** (of selecteer Exemplaar van de toolbar)
1. Selecteren **`/apps/an-scf-sandbox/components/playpage`**
1. Klik met de rechtermuisknop en selecteer **Deeg** (of uitgezocht Deeg van de toolbar)
1. Dubbelklik op **`headlibs.jsp`** om het te openen
1. De volgende regel toevoegen aan het einde van het bestand
   **`<ui:includeClientLib categories="apps.an-scf-sandbox"/>`**

1. Klik **sparen allen**

```xml
<%@ page session="false" %><%
%><%@include file="/libs/foundation/global.jsp" %><%
%><ui:includeClientLib categories="cq.foundation-main"/><%
%>
<cq:include script="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp"/>
<% currentDesign.writeCssIncludes(pageContext); %>
<ui:includeClientLib categories="apps.an-scf-sandbox"/>
```

Laad uw website in de browser en controleer of de achtergrond geen blauwe tint heeft.

[ https://localhost:4502/content/an-scf-sandbox/en/play.html](https://localhost:4502/content/an-scf-sandbox/en/play.html)

![ gemeenschap-spel ](assets/community-play.png)

### Uw werk tot nu toe opslaan {#saving-your-work-so-far}

Op dit moment bestaat er een minimalistische zandbak. Het kan de moeite waard zijn om op te slaan als een pakket, zodat u tijdens het afspelen uw server kunt uitschakelen als uw opslagplaats beschadigd raakt en u opnieuw wilt beginnen. Wijzig vervolgens de naam van de map crx-quickstart/ of verwijder deze, schakel de server in, upload en installeer dit opgeslagen pakket en hoef deze basisstappen niet te herhalen.

Dit pakket bestaat op [ creeer een leerprogramma van de Pagina van de Steekproef ](/help/communities/create-sample-page.md) voor hen die niet kunnen wachten binnen te springen en beginnen speel.

Een pakket maken:

* Van CRXDE Lite, klik het [ pictogram van het Pakket ](https://localhost:4502/crx/packmgr/)
* Klik **Create Pakket**

   * Pakketnaam: an-scf-sandbox-minimum-pkg
   * Versie: 0.1
   * Groep: `leave as default`
   * Klik **O.K.**

* Klik **uitgeven**

   * Selecteer **Filters** lusje

      * Klik **toevoegen filter**
      * Hoofdpad: bladeren naar `/apps/an-scf-sandbox`
      * Klik **Gereed**
      * Klik **toevoegen filter**
      * Hoofdpad: bladeren naar `/etc/designs/an-scf-sandbox`
      * Klik **Gereed**
      * Klik **toevoegen filter**
      * Hoofdpad: bladeren naar `/content/an-scf-sandbox**`
      * Klik **Gereed**

   * Klik **sparen**

* Klik **Bouwstijl**

Nu kunt u **Download** selecteren om het aan schijf te bewaren en **Pakket** elders uploaden, en **selecteren Meer > Repliceert** om zandbak aan een localhost te duwen publiceer instantie om het domein van uw zandbak uit te breiden.
