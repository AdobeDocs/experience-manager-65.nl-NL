---
title: Een voorbeeldpagina maken
seo-title: Een voorbeeldpagina maken
description: Een voorbeeldcommunitysite maken
seo-description: Een voorbeeldcommunitysite maken
uuid: 04a8f027-b7d8-493a-a9bd-5c4a6715d754
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
content-type: reference
topic-tags: developing
discoiquuid: a03145f7-6697-4797-b73e-6f8d241ce469
translation-type: tm+mt
source-git-commit: 824ddd48e4680eed1d4612c6ad450a8f1bc68e7c
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 1%

---


# Een voorbeeldpagina maken {#create-a-sample-page}

Vanaf AEM 6.1 Gemeenschappen is de eenvoudigste manier om een voorbeeldpagina te maken een eenvoudige gemeenschapssite te maken, die bestaat uit een functie Pagina.

Dit zal een parsys component omvatten zodat u componenten voor creatie ](basics.md#accessing-communities-components) kunt [toelaten.

Een andere optie voor exploratie met steekproefcomponenten is de eigenschappen te gebruiken die in [Communautaire Gids van Componenten ](components-guide.md) worden voorgesteld.

## Een communautaire site maken {#create-a-community-site}

Dit lijkt op het maken van een nieuwe site die wordt beschreven in [Aan de slag met AEM Communities](getting-started.md).

Het belangrijkste verschil is dat deze zelfstudie een nieuwe communitysitesjabloon maakt dat alleen de [Paginafunctie](functions.md#page-function) bevat om een eenvoudige communitysite te maken die vrij is van andere functies (andere dan de vooraf bekabelde functies die van fundamenteel belang zijn voor alle communitysites).

### Nieuwe sitesjabloon maken {#create-new-site-template}

Om te beginnen, creeer een eenvoudige [communitymalplaatje](sites.md).

Selecteer **[!UICONTROL Tools]** > **[!UICONTROL Communities]** > **[!UICONTROL Site Templates]** vanuit globale navigatie op een auteurinstantie.

![create-site-template](assets/create-site-template1.png)

* Selecteer `Create button`
* BASISINFO

   * `Name`: Sjabloon voor één pagina
   * `Description`: Een sjabloon die bestaat uit een functie Eén pagina.
   * Selecteer `Enabled`

![site-template-editor](assets/site-template-editor.png)

* STRUCTUUR

   * Sleep een functie `Page` naar de Sjabloonbouwer
   * Voor de details van de Functie van de Configuratie, ga binnen

      * `Title`: Eén pagina
      * `URL`: page

![site-template-editor-structuur](assets/site-template-editor1.png)

* Selecteer **`Save`** voor de configuratie
* Selecteer **`Save`** voor de sitesjabloon

### Nieuwe Community-site maken {#create-new-community-site}

Maak nu een nieuwe communitysite op basis van de eenvoudige sitesjabloon.

Selecteer **[!UICONTROL Communities > Sites]** bij globale navigatie nadat u de sitesjabloon hebt gemaakt.

![create-community-site](assets/create-community-site1.png)

* Pictogram **`Create`** selecteren

* Stap `1 - Site Template`

   * `Title`: Eenvoudige community-site
   * `Description`: Een communautaire site die bestaat uit één pagina voor experimenten.
   * `Community Site Root: (leave blank)`
   * `Community Site Base Language: English`
   * `Name`: monster

      * url = http://localhost:4502/content/sites/sample

      * `Template`: kiezen  `Single Page Template`

      ![create-community-site-template](assets/create-community-site-template.png)


* Selecteer `Next`
* Stap `2 - Design`

   * Elk ontwerp selecteren

* Selecteer `Next`
* Selecteer `Next`

   (Alle standaardinstellingen accepteren)

* Selecteer `Create`

   ![create-community-site](assets/create-community-site.png)

## De site {#publish-the-site} publiceren

![publicatiesite](assets/publish-site.png)

Selecteer in de [communitysiteconsole](sites-console.md) het publicatiepictogram om de site te publiceren, standaard op http://localhost:4503.

## Site openen op auteur in bewerkingsmodus {#open-the-site-on-author-in-edit-mode}

![open-site](assets/open-site.png)

Selecteer het pictogram van de geopende site om de site weer te geven in de bewerkingsmodus.

De URL is [http://localhost:4502/editor.html/content/sites/sample/en.html](http://localhost:4502/editor.html/content/sites/sample/en.html)

![auteur-site](assets/author-site.png)

Op de eenvoudige homepage is het mogelijk om te zien wat door de communautaire functies en malplaatjes vooraf wordt getelegrafeerd, en spel met het toevoegen en het vormen van communautaire componenten.

## Site weergeven bij publiceren {#view-site-on-publish}

Nadat u de pagina hebt gepubliceerd, opent u de pagina op het [publish-exemplaar](http://localhost:4503/content/sites/sample/en.html) om te experimenteren met de functies als anonieme sitebezoeker, aangemeld lid of beheerder. De verbinding van het Beleid zichtbaar in het auteursmilieu zal niet in publiceren milieu verschijnen tenzij een beheerder binnen ondertekent.
