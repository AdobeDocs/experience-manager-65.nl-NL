---
title: Een voorbeeldpagina maken
description: Leer hoe u een sjabloon voor een communitysite maakt die alleen de paginafunctie bevat die u kan helpen een eenvoudige communitysite te maken.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
content-type: reference
topic-tags: developing
exl-id: d66fc1ff-a669-4a2c-b45a-093060facd97
solution: Experience Manager
feature: Communities
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# Een voorbeeldpagina maken {#create-a-sample-page}

Vanaf AEM 6.1 Gemeenschappen is de eenvoudigste manier om een voorbeeldpagina te maken een eenvoudige gemeenschapssite te maken, die bestaat uit een functie Pagina.

Dit omvat een component parsys zodat u kunt [componenten inschakelen voor ontwerpen](basics.md#accessing-communities-components).

Een andere optie voor exploratie met steekproefcomponenten is de eigenschappen te gebruiken die in worden voorgesteld [Community Components Guide](components-guide.md).

## Een Community-site maken {#create-a-community-site}

Dit is vergelijkbaar met het maken van een site die wordt beschreven in [Aan de slag met AEM Communities](getting-started.md).

Het belangrijkste verschil is dat deze zelfstudie een sjabloon voor een community-site maakt die alleen de [Paginafunctie](functions.md#page-function) om een eenvoudige communitysite te maken. Het doet dit vrij van andere eigenschappen (behalve de pre-getelegrafeerde eigenschappen fundamenteel voor alle communautaire plaatsen).

### Nieuw sitesjabloon maken {#create-new-site-template}

Om aan de slag te gaan, maakt u een eenvoudige [sjabloon voor community-site](sites.md).

Van globale navigatie op een auteursinstantie, selecteer **[!UICONTROL Tools]** > **[!UICONTROL Communities]** > **[!UICONTROL Site Templates]**.

![create-site-template](assets/create-site-template1.png)

* Selecteren `Create button`
* BASISINFO

   * `Name`: Sjabloon voor één pagina
   * `Description`: Een sjabloon die bestaat uit een functie Eén pagina.
   * Selecteren `Enabled`

![site-template-editor](assets/site-template-editor.png)

* STRUCTUUR

   * Sleep een `Page` functie naar de Sjabloonbouwer
   * Voor de details van de Functie van de Configuratie, ga

      * `Title`: Eén pagina
      * `URL`: pagina

![site-template-editor-structuur](assets/site-template-editor1.png)

* Selecteren **`Save`** voor de configuratie
* Selecteren **`Save`** voor de sitesjabloon

### Nieuwe community-site maken {#create-new-community-site}

Maak nu een communitysite op basis van de eenvoudige sitesjabloon.

Nadat u de sitesjabloon hebt gemaakt, selecteert u in globale navigatie **[!UICONTROL Communities > Sites]**.

![create-community-site](assets/create-community-site1.png)

* Selecteren **`Create`** pictogram

* Stap `1 - Site Template`

   * `Title`: Eenvoudige Community-site
   * `Description`: Een communautaire site die bestaat uit één pagina voor experimenten.
   * `Community Site Root: (leave blank)`
   * `Community Site Base Language: English`
   * `Name`: monster

      * url = http://localhost:4502/content/sites/sample

      * `Template`: choose `Single Page Template`

     ![create-community-site-template](assets/create-community-site-template.png)

* Selecteren `Next`
* Stap `2 - Design`

   * Elk ontwerp selecteren

* Selecteren `Next`
* Selecteren `Next`

  (Alle standaardinstellingen accepteren)

* Selecteren `Create`

  ![create-community-site](assets/create-community-site.png)

## De site publiceren {#publish-the-site}

![publicatiesite](assets/publish-site.png)

Van de [community sites console](sites-console.md)selecteert u het publicatiepictogram om de site te publiceren. Standaard wordt dit http://localhost:4503 weergegeven.

## Site openen op auteur in bewerkingsmodus {#open-the-site-on-author-in-edit-mode}

![open-site](assets/open-site.png)

Selecteer het pictogram van de geopende site zodat u de site in de bewerkingsmodus kunt bekijken.

De URL is [http://localhost:4502/editor.html/content/sites/sample/en.html](http://localhost:4502/editor.html/content/sites/sample/en.html)

![auteur-site](assets/author-site.png)

Op de eenvoudige homepage, is het mogelijk om te zien wat door de communautaire functies en malplaatjes vooraf wordt getelegrafeerd, en spel met het toevoegen en het vormen van communautaire componenten.

## Site weergeven bij publicatie {#view-site-on-publish}

Na publicatie van de pagina opent u de pagina op de [publish-instantie](http://localhost:4503/content/sites/sample/en.html) om te experimenteren met de functies als anonieme sitebezoeker, aangemeld lid of beheerder. De verbinding van het Beleid zichtbaar in het auteursmilieu verschijnt niet in publiceer milieu tenzij een beheerder binnen ondertekent.
