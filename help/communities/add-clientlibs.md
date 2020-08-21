---
title: Clientlibs toevoegen
seo-title: Clientlibs toevoegen
description: Een ClientLibraryFolder toevoegen
seo-description: Een ClientLibraryFolder toevoegen
uuid: 2944923d-caca-4607-81a4-4122a2ce8e41
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 46f81c3f-6512-43f1-8ec1-cc717ab6f6ff
docset: aem65
translation-type: tm+mt
source-git-commit: fcdae5363e7a0070b5d6b76227e5c65efb71bc03
workflow-type: tm+mt
source-wordcount: '687'
ht-degree: 1%

---


# Clientlibs toevoegen {#add-clientlibs}

## Een ClientLibraryFolder (clientlibs) toevoegen {#add-a-clientlibraryfolder-clientlibs}

Maak een ClientLibraryFolder met de naam `clientlibs` die de JS en CSS bevat die worden gebruikt om de pagina&#39;s van uw site weer te geven.

De `categories` eigenschapswaarde die aan deze clientbibliotheek wordt gegeven, is de id die wordt gebruikt om deze clientlib rechtstreeks vanaf een inhoudspagina in te sluiten of om deze in andere clientlibs in te sluiten.

1. Met **CRXDE Lite** uitvouwen `/etc/designs`

1. Klik met de rechtermuisknop `an-scf-sandbox` en selecteer `Create Node`

   * Naam : `clientlibs`
   * Type : `cq:ClientLibraryFolder`

1. Click **OK**

![add-client-library](assets/add-client-library.png)

Voer op het tabblad **Eigenschappen** voor het nieuwe `clientlibs` knooppunt de eigenschap **Categorieën** in:

* Naam: **categorieën**
* Type: **String**
* Waarde: **apps.an-scf-sandbox**
* Click **Add**
* Klik op Alles **opslaan**

Opmerking: De waarde voor categorieën wordt voorafgegaan door &#39;apps&#39;. is een conventie om aan te geven dat de &#39;toepassing die eigenaar is&#39; zich in de map /apps bevindt, niet /libs.  BELANGRIJK : Voeg plaatsaanduiding `js.tx`aan en **`css.txt`** bestanden toe. (Het is officieel geen cq:ClientLibraryFolder zonder hen.)

1. Klikken met rechtermuisknop **`/etc/designs/an-scf-sandbox/clientlibs`**
1. Bestand **maken selecteren...**
1. Voer de **naam in:** `css.txt`
1. Bestand **maken selecteren...**
1. Voer de **naam in:** `js.txt`
1. Klik op Alles **opslaan**

![clientlibs-css](assets/clientlibs-css.png)

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

Voer op het tabblad **Eigenschappen** voor het `clientlibs` knooppunt de eigenschap String met meerdere waarden in die u wilt **insluiten**. Dit bedt de noodzakelijke [cliënt-zijbibliotheken (clientlibs) voor componenten](/help/communities/client-customize.md#clientlibs-for-scf)SCF in. Voor deze zelfstudie worden veel clientlibs toegevoegd die nodig zijn voor de onderdelen Communities.

**Merk** op dat dit of niet de gewenste benadering voor een productiesite kan zijn aangezien er overwegingen van gemak tegenover grootte/snelheid van de clientlibs die voor elke pagina worden gedownload zijn.

Als u slechts één functie op één pagina gebruikt, kunt u de volledige clientlib van die functie rechtstreeks op de pagina opnemen, bijvoorbeeld:

`% ui:includeClientLib categories=cq.social.hbs.forum" %`

In dit geval, met inbegrip van hen allen en zo worden de meer basiscliënten SCF die de auteur clientlibs zijn verkiesd:

* Naam : **`embed`**
* Type : **`String`**
* Klik op **`Multi`**
* Waarde: **`cq.social.scf`**

   * Er wordt een dialoogvenster weergegeven. Klik op elk item **`+`** om de volgende clientlib-categorieën toe te voegen:

      * **`cq.ckeditor`**
      * **`cq.social.author.hbs.comments`**
      * **`cq.social.author.hbs.forum`**
      * **`cq.social.author.hbs.rating`**
      * **`cq.social.author.hbs.reviews`**
      * **`cq.social.author.hbs.voting`**
      * Click **OK**

* Klik op Alles **opslaan**

![scf-clientlibs](assets/scf-clientlibs.png)

Dit is hoe `/etc/designs/an-scf-sandbox/clientlibs` zou nu in bewaarplaats moeten verschijnen:

![scf-clientlibs-weergave](assets/scf-clientlibs1.png)

### Clientlibs opnemen in PlayPage-sjabloon {#include-clientlibs-in-playpage-template}

Zonder de categorie `apps.an-scf-sandbox` ClientLibraryFolder op de pagina te plaatsen, zijn de SCF-componenten niet functioneel en niet opgemaakt omdat de benodigde JavaScript(s) en stijl(en) niet beschikbaar zijn.

Bijvoorbeeld, zonder de clientlibs op te nemen, lijkt de SCF commentaarcomponent ongestileerd:

![clientlibs-comment](assets/clientlibs-comment.png)

Zodra apps.an-scf-sandbox clientlibs is opgenomen, wordt de stijl van de SCF-commentaarcomponent weergegeven:

![clientlibs-comment-styled](assets/clientlibs-comment1.png)

De instructie include behoort tot de `head` sectie van het `html` script. De standaardwaarde **`foundation head.jsp`** bevat een script dat kan worden bedekt: **`headlibs.jsp`**.

**Kopieer koplibs.jsp en neem clientlibs op:**

1. Selecteer met **CRXDE Lite****`/libs/foundation/components/page/headlibs.jsp`**

1. Klik met de rechtermuisknop en selecteer **Kopiëren** (of selecteer Kopiëren op de werkbalk)
1. Selecteer **`/apps/an-scf-sandbox/components/playpage`**
1. Klik met de rechtermuisknop en selecteer **Plakken** (of selecteer Plakken op de werkbalk)
1. Dubbelklik **`headlibs.jsp`** om het te openen
1. De volgende regel toevoegen aan het einde van het bestand
   **`<ui:includeClientLib categories="apps.an-scf-sandbox"/>`**

1. Klik op Alles **opslaan**

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

[https://localhost:4502/content/an-scf-sandbox/en/play.html](https://localhost:4502/content/an-scf-sandbox/en/play.html)

![gemeenschapszin](assets/community-play.png)

### Uw werk tot nu toe opslaan {#saving-your-work-so-far}

Op dit moment bestaat er een minimalistische sandbox en het is misschien de moeite waard om op te slaan als een pakket, zodat u tijdens het afspelen, als uw opslagplaats beschadigd raakt en u opnieuw wilt beginnen, uw server kunt uitschakelen, de naam van de map crx-quickstart/ wijzigen of verwijderen, uw server in kunt schakelen, uploaden en installeren van dit opgeslagen pakket, en deze basisstappen niet hoeft te herhalen.

Dit pakket staat in de zelfstudie [Een voorbeeldpagina](/help/communities/create-sample-page.md) maken voor gebruikers die niet kunnen wachten om alleen binnen te springen en af te spelen...

Een pakket maken:

* Van CRXDE Lite klik het pictogram van het [Pakket](https://localhost:4502/crx/packmgr/)
* Klik op Pakket **maken**

   * Pakketnaam: an-scf-sandbox-minimum-pkg
   * Versie: 0,1
   * Groeperen: `leave as default`
   * Click **OK**

* Click **Edit**

   * Tabblad **Filters** selecteren

      * Klik op **Toevoegen, filter**
      * Hoofdpad: bladeren naar `/apps/an-scf-sandbox`
      * Klik op **Gereed**
      * Klik op **Toevoegen, filter**
      * Hoofdpad: bladeren naar `/etc/designs/an-scf-sandbox`
      * Klik op **Gereed**
      * Klik op **Toevoegen, filter**
      * Hoofdpad: bladeren naar `/content/an-scf-sandbox**`
      * Klik op **Gereed**
   * Click **Save**


* Klik op **Samenstellen**

Nu kunt u **Downloaden** selecteren om het op schijf op te slaan en Pakket **elders te** uploaden, evenals **Meer > Repliceren** selecteren om de zandbak aan een localhost te duwen publiceert instantie om het domein van uw zandbak uit te breiden.