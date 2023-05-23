---
title: Clientlibs toevoegen
seo-title: Add Clientlibs
description: Een ClientLibraryFolder toevoegen
seo-description: Add a ClientLibraryFolder
uuid: 2944923d-caca-4607-81a4-4122a2ce8e41
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 46f81c3f-6512-43f1-8ec1-cc717ab6f6ff
docset: aem65
exl-id: 569f2052-b4fe-4f7f-aec9-657217cba091
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '682'
ht-degree: 0%

---

# Clientlibs toevoegen {#add-clientlibs}

## Een ClientLibraryFolder (clientlibs) toevoegen {#add-a-clientlibraryfolder-clientlibs}

Een ClientLibraryFolder maken met de naam `clientlibs` die de JS en CSS bevat die worden gebruikt om de pagina&#39;s van uw site weer te geven.

De `categories` De eigenschapwaarde die aan deze clientbibliotheek wordt gegeven, is de id die wordt gebruikt om deze clientlib rechtstreeks vanaf een inhoudspagina in te sluiten of om deze in andere clientlibs in te sluiten.

1. Gebruiken **CRXDE Lite**, uitbreiden `/etc/designs`

1. Klikken met rechtermuisknop `an-scf-sandbox` en selecteert u `Create Node`

   * Naam: `clientlibs`
   * Type: `cq:ClientLibraryFolder`

1. Klikken **OK**

![add-client-library](assets/add-client-library.png)

In de **Eigenschappen** tab voor de nieuwe `clientlibs` knoop, ga in **categorieën** eigenschap:

* Naam: **categorieën**
* Type: **String**
* Waarde: **apps.an-scf-sandbox**
* Klikken **Toevoegen**
* Klikken **Alles opslaan**

Opmerking: De waarde voor categorieën wordt voorafgegaan door &#39;apps&#39;. is een conventie om aan te geven dat de &#39;toepassing die eigenaar is&#39; zich in de map /apps bevindt, niet /libs.  BELANGRIJK : Plaatsaanduiding toevoegen `js.tx`t en **`css.txt`** bestanden. (Het is officieel geen cq:ClientLibraryFolder zonder hen.)

1. Klikken met rechtermuisknop **`/etc/designs/an-scf-sandbox/clientlibs`**
1. Selecteren **Bestand maken...**
1. Enter **Naam:** `css.txt`
1. Selecteren **Bestand maken...**
1. Enter **Naam:** `js.txt`
1. Klikken **Alles opslaan**

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

In de **Eigenschappen** tab voor de `clientlibs` node, voer de eigenschap String voor meerdere waarden in **insluiten**. Dit sluit de noodzakelijke [client-side bibliotheken (clientlibs) voor SCF-componenten](/help/communities/client-customize.md#clientlibs-for-scf). Voor deze zelfstudie worden veel clientlibs toegevoegd die nodig zijn voor de onderdelen Communities.

**Opmerking** dat dit al dan niet de gewenste benadering voor een productiesite kan zijn aangezien er overwegingen van gemak tegenover grootte/snelheid van de clientlibs die voor elke pagina worden gedownload zijn.

Als u slechts één functie op één pagina gebruikt, kunt u de volledige clientlib van die functie rechtstreeks op de pagina opnemen, bijvoorbeeld:

`% ui:includeClientLib categories=cq.social.hbs.forum" %`

In dit geval, met inbegrip van hen allen en zo worden de meer basiscliënten SCF die de auteur clientlibs zijn verkiesd:

* Naam: **`embed`**
* Type: **`String`**
* Klik op **`Multi`**
* Waarde: **`cq.social.scf`**

   * Hiermee wordt een dialoogvenster weergegeven. Klik op **`+`** na elke vermelding om de volgende clientlib-categorieën toe te voegen:

      * **`cq.ckeditor`**
      * **`cq.social.author.hbs.comments`**
      * **`cq.social.author.hbs.forum`**
      * **`cq.social.author.hbs.rating`**
      * **`cq.social.author.hbs.reviews`**
      * **`cq.social.author.hbs.voting`**
      * Klikken **OK**

* Klikken **Alles opslaan**

![scf-clientlibs](assets/scf-clientlibs.png)

Zo `/etc/designs/an-scf-sandbox/clientlibs` moet nu in de gegevensopslagruimte worden weergegeven:

![scf-clientlibs-weergave](assets/scf-clientlibs1.png)

### Clientlibs opnemen in PlayPage-sjabloon {#include-clientlibs-in-playpage-template}

Zonder de `apps.an-scf-sandbox` De categorie ClientLibraryFolder op de pagina, de SCF-componenten zijn niet functioneel en niet opgemaakt omdat de benodigde Javascript(s) en stijl(en) niet beschikbaar zijn.

Bijvoorbeeld, zonder de clientlibs op te nemen, lijkt de SCF commentaarcomponent ongestileerd:

![clientlibs-comment](assets/clientlibs-comment.png)

Zodra apps.an-scf-sandbox clientlibs is opgenomen, wordt de stijl van de SCF-commentaarcomponent weergegeven:

![clientlibs-comment-styled](assets/clientlibs-comment1.png)

De instructie include behoort tot de `head` van de `html` script. De standaardwaarde **`foundation head.jsp`** bevat een script dat kan worden bedekt: **`headlibs.jsp`**.

**Kopieer koplibs.jsp en neem clientlibs op:**

1. Gebruiken **CRXDE Lite**, selecteert u **`/libs/foundation/components/page/headlibs.jsp`**

1. Klik met de rechtermuisknop en selecteer **Kopiëren** (Of selecteer Kopiëren op de werkbalk)
1. Selecteer **`/apps/an-scf-sandbox/components/playpage`**
1. Klik met de rechtermuisknop en selecteer **Plakken** (of selecteer Plakken op de werkbalk)
1. Dubbelklikken **`headlibs.jsp`** openen
1. De volgende regel toevoegen aan het einde van het bestand
   **`<ui:includeClientLib categories="apps.an-scf-sandbox"/>`**

1. Klikken **Alles opslaan**

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

Dit pakket is beschikbaar op het tabblad [Een voorbeeldpagina maken](/help/communities/create-sample-page.md) zelfstudie voor hen die niet kunnen wachten om gewoon binnen te springen en te beginnen met afspelen...

Een pakket maken:

* Van CRXDE Lite klik [Pakketpictogram](https://localhost:4502/crx/packmgr/)
* Klikken **Pakket maken**

   * Pakketnaam: an-scf-sandbox-minimum-pkg
   * Versie: 0,1
   * Groep: `leave as default`
   * Klikken **OK**

* Klikken **Bewerken**

   * Selecteren **Filters** tab

      * Klikken **Filter toevoegen**
      * Hoofdpad: bladeren naar `/apps/an-scf-sandbox`
      * Klikken **Gereed**
      * Klikken **Filter toevoegen**
      * Hoofdpad: bladeren naar `/etc/designs/an-scf-sandbox`
      * Klikken **Gereed**
      * Klikken **Filter toevoegen**
      * Hoofdpad: bladeren naar `/content/an-scf-sandbox**`
      * Klikken **Gereed**
   * Klikken **Opslaan**


* Klikken **Opbouwen**

Nu kunt u **Downloaden** opslaan naar schijf en **Pakket uploaden** en selecteert u **Meer > Repliceren** om de sandbox naar een publicatieinstantie van de localhost te verplaatsen en het domein van de sandbox uit te breiden.
