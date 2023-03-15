---
title: Een voorbeeldpagina maken
seo-title: Create a Sample Page
description: Een voorbeeldcommunitysite maken
seo-description: Create a Sample community site
uuid: 04a8f027-b7d8-493a-a9bd-5c4a6715d754
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
content-type: reference
topic-tags: developing
discoiquuid: a03145f7-6697-4797-b73e-6f8d241ce469
exl-id: d66fc1ff-a669-4a2c-b45a-093060facd97
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 1%

---

# Een voorbeeldpagina maken {#create-a-sample-page}

Vanaf AEM 6.1 Gemeenschappen is de eenvoudigste manier om een voorbeeldpagina te maken een eenvoudige gemeenschapssite te maken, die bestaat uit een functie Pagina.

Dit zal een component parsys omvatten zodat u kunt [componenten inschakelen voor ontwerpen](basics.md#accessing-communities-components).

Een andere optie voor exploratie met steekproefcomponenten is de eigenschappen te gebruiken die in worden voorgesteld [Community Components Guide](components-guide.md).

## Een Community-site maken {#create-a-community-site}

Dit lijkt sterk op het maken van een nieuwe site zoals beschreven in [Aan de slag met AEM Communities](getting-started.md).

Het belangrijkste verschil is dit leerprogramma zal tot een nieuw malplaatje van de communautaire plaats leiden dat slechts bevat [Paginafunctie](functions.md#page-function) om een eenvoudige communautaire plaats te creëren vrij van andere eigenschappen (buiten de pre-telegrafeerde eigenschappen fundamenteel voor alle communautaire plaatsen).

### Nieuw sitesjabloon maken {#create-new-site-template}

Maak een eenvoudige [sjabloon voor community-site](sites.md).

Van globale navigatie op een auteursinstantie uitgezocht **[!UICONTROL Tools]** > **[!UICONTROL Communities]** > **[!UICONTROL Site Templates]**.

![create-site-template](assets/create-site-template1.png)

* Selecteer `Create button`
* BASISINFO

   * `Name`: Sjabloon voor één pagina
   * `Description`: Een sjabloon die bestaat uit een functie Eén pagina.
   * Selecteer `Enabled`

![site-template-editor](assets/site-template-editor.png)

* STRUCTUUR

   * Sleep een `Page` functie aan de Bouwer van het Malplaatje
   * Voor de details van de Functie van de Configuratie, ga binnen

      * `Title`: Eén pagina
      * `URL`: page

![site-template-editor-structuur](assets/site-template-editor1.png)

* Selecteren **`Save`** voor de configuratie
* Selecteren **`Save`** voor de sitesjabloon

### Nieuwe community-site maken {#create-new-community-site}

Maak nu een nieuwe communitysite op basis van de eenvoudige sitesjabloon.

Nadat u de sitesjabloon hebt gemaakt, selecteert u in globale navigatie **[!UICONTROL Communities > Sites]**.

![create-community-site](assets/create-community-site1.png)

* Selecteren **`Create`** pictogram

* Stap `1 - Site Template`

   * `Title`: Eenvoudige community-site
   * `Description`: Een communautaire site die bestaat uit één pagina voor experimenten.
   * `Community Site Root: (leave blank)`
   * `Community Site Base Language: English`
   * `Name`: monster

      * url = http://localhost:4502/content/sites/sample

      * `Template`: kiezen `Single Page Template`

      ![create-community-site-template](assets/create-community-site-template.png)


* Selecteer `Next`
* Stap `2 - Design`

   * Elk ontwerp selecteren

* Selecteer `Next`
* Selecteer `Next`

   (Alle standaardinstellingen accepteren)

* Selecteer `Create`

   ![create-community-site](assets/create-community-site.png)

## De site publiceren {#publish-the-site}

![publicatiesite](assets/publish-site.png)

Van de [community sites console](sites-console.md)selecteert u het publicatiepictogram om de site te publiceren. Standaard wordt dit http://localhost:4503 weergegeven.

## De site openen op auteur in de bewerkingsmodus {#open-the-site-on-author-in-edit-mode}

![open-site](assets/open-site.png)

Selecteer het pictogram van de geopende site om de site weer te geven in de bewerkingsmodus.

De URL wordt [http://localhost:4502/editor.html/content/sites/sample/en.html](http://localhost:4502/editor.html/content/sites/sample/en.html)

![auteur-site](assets/author-site.png)

Op de eenvoudige homepage is het mogelijk om te zien wat door de communautaire functies en malplaatjes vooraf wordt getelegrafeerd, en spel met het toevoegen van en het vormen van communautaire componenten.

## Site weergeven bij publicatie {#view-site-on-publish}

Nadat u de pagina hebt gepubliceerd, opent u de pagina op het tabblad [publish-instantie](http://localhost:4503/content/sites/sample/en.html) om te experimenteren met de functies als anonieme sitebezoeker, aangemeld lid of beheerder. De verbinding van het Beleid zichtbaar in het auteursmilieu zal niet in publiceren milieu verschijnen tenzij een beheerder binnen ondertekent.
