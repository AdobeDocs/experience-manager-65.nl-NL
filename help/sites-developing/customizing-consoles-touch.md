---
title: De consoles aanpassen
seo-title: Customizing the Consoles
description: AEM biedt verschillende mechanismen waarmee u de consoles van de ontwerpinstantie kunt aanpassen
seo-description: AEM provides various mechanisms to enable you to customize the consoles of your authoring instance
uuid: 8ecce9ff-5907-41e1-af3b-a8646352d633
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 61a4e196-bd53-4ef0-816b-c14401462457
docset: aem65
exl-id: 6e67f2b3-78b9-45f2-b496-61776b9fd9cc
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '669'
ht-degree: 0%

---

# De consoles aanpassen {#customizing-the-consoles}

>[!CAUTION]
>
>In dit document wordt beschreven hoe consoles in de moderne interface met aanraakbediening kunnen worden aangepast. Dit document is niet van toepassing op de klassieke gebruikersinterface.

AEM biedt verschillende mechanismen om u in staat te stellen de consoles (en de [functionaliteit voor paginaontwerp](/help/sites-developing/customizing-page-authoring-touch.md)) van de ontwerpinstantie.

* Clientlibs Clientlibs laten u de standaardimplementatie uitbreiden om nieuwe functionaliteit te realiseren, terwijl het hergebruiken van de standaardfuncties, de voorwerpen, en de methodes. Bij het aanpassen kunt u uw eigen clientlib maken onder `/apps.` Het kan bijvoorbeeld de code bevatten die is vereist voor uw aangepaste component.

* Bedekkingen zijn gebaseerd op knooppuntdefinities en laten u de standaardfunctionaliteit bedekken (in `/libs`) met uw eigen aangepaste functionaliteit (in `/apps`). Bij het maken van een overlay is een 1:1-kopie van het origineel niet vereist, omdat de samenvoeging van de tekenbron overerving toestaat.

Deze kunnen op vele manieren worden gebruikt om uw AEM te uitbreiden. Een kleine selectie wordt hieronder behandeld (op een hoog niveau).

>[!NOTE]
>
>Zie voor meer informatie:
>
>* Gebruiken en maken [clientlibs](/help/sites-developing/clientlibs.md).
>* Gebruiken en maken [bedekkingen](/help/sites-developing/overlays.md).
>* [Graniet](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html)
>


>[!CAUTION]
>
>U ***moet*** niets wijzigen in het dialoogvenster `/libs` pad.
>
>Dit komt omdat de inhoud van `/libs` wordt de volgende keer overschreven wanneer u een upgrade uitvoert van uw exemplaar (en kan worden overschreven wanneer u een hotfix- of functiepakket toepast).
>
>De aanbevolen methode voor configuratie en andere wijzigingen is:
>
>1. Het vereiste item opnieuw maken (bijvoorbeeld zoals het bestaat in `/libs`) onder `/apps`
>
>1. Breng wijzigingen aan in `/apps`
>

De volgende locatie in het dialoogvenster `/libs` de structuur kan worden bedekt door :

* consoles (consoles op basis van gebruikersinterface-pagina&#39;s van graniet), bijvoorbeeld:

   * `/libs/wcm/core/content`

>[!NOTE]
>
>Zie het artikel in de Knowledge Base. [Problemen AEM TouchUI oplossen](https://helpx.adobe.com/experience-manager/kb/troubleshooting-aem-touchui-issues.html)voor meer tips en hulpmiddelen.

## De standaardweergave voor een console aanpassen {#customizing-the-default-view-for-a-console}

U kunt de standaardweergave (kolom, kaart, lijst) voor een console aanpassen:

1. U kunt de volgorde van de weergaven wijzigen door de vereiste invoer onder te plaatsen:

   `/libs/wcm/core/content/sites/jcr:content/views`

   De eerste vermelding is de standaardinstelling.

   De beschikbare knooppunten zijn gerelateerd aan de beschikbare weergaveopties:

   * `column`
   * `card`
   * `list`

1. Bijvoorbeeld in een overlay voor de lijst:

   `/apps/wcm/core/content/sites/jcr:content/views/list`

   Definieer de volgende eigenschap:

   * **Naam**: `sling:orderBefore`
   * **Type**: `String`
   * **Waarde**: `column`

### Nieuwe handeling toevoegen aan de werkbalk {#add-new-action-to-the-toolbar}

1. U kunt uw eigen componenten bouwen en de overeenkomstige cliëntbibliotheken voor douaneacties omvatten. Bijvoorbeeld een **Bevorderen tot Twitter** actie bij:

   `/apps/wcm/core/clientlibs/sites/js/twitter.js`

   Dit kan dan met een toolbarpunt op uw console worden verbonden:

   `/apps/<yourProject>/admin/ext/launches`

   In de selectiemodus bijvoorbeeld:

   `content/jcr:content/body/content/header/items/selection/items/twitter`

### Een werkbalkactie beperken tot een specifieke groep {#restrict-a-toolbar-action-to-a-specific-group}

1. U kunt een aangepaste rendervoorwaarde gebruiken om de standaardhandeling te bedekken en specifieke voorwaarden op te leggen waaraan moet worden voldaan voordat deze wordt gerenderd.

   Maak bijvoorbeeld een component om de rendervoorwaarden op basis van groep te beheren:

   `/apps/myapp/components/renderconditions/group`

1. U kunt deze toepassen op de actie Site maken op de Sites-console:

   `/libs/wcm/core/content/sites`

   Maak de bedekking:

   `/apps/wcm/core/content/sites`

1. Voeg vervolgens de rendervoorwaarde voor de actie toe:

   `jcr:content/body/content/header/items/default/items/create/items/createsite/rendercondition`

   Met de eigenschappen van dit knooppunt kunt u de `groups` is toegestaan de specifieke handeling uit te voeren, bijvoorbeeld `administrators`

### Kolommen aanpassen in de lijstweergave {#customizing-columns-in-the-list-view}

>[!NOTE]
>
>Deze functie is geoptimaliseerd voor kolommen met tekstvelden; voor andere gegevenstypen is het mogelijk om te bedekken `cq/gui/components/siteadmin/admin/listview/columns/analyticscolumnrenderer` in `/apps`.

U kunt als volgt de kolommen in de lijstweergave aanpassen:

1. Bedek de lijst met beschikbare kolommen.

   * Op het knooppunt:

     ```
            /apps/wcm/core/content/common/availablecolumns
     ```

   * Voeg uw nieuwe kolommen toe - of verwijder bestaande kolommen.

   Zie [Bedekkingen gebruiken (en de samenvoeging van bronnen voor verschuiven)](/help/sites-developing/overlays.md) voor meer informatie .

1. Optioneel:

   * Als u aanvullende gegevens wilt aansluiten, moet u een [PageInforProvider](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageInfoProvider.html) met een
     `pageInfoProviderType` eigenschap.

   Bijvoorbeeld, zie hieronder de klasse/de bundel in bijlage (van GitHub).

1. U kunt nu de kolom selecteren in de kolomconfigurator van de lijstweergave.

### Bronnen filteren {#filtering-resources}

Wanneer het gebruiken van een console, is een gemeenschappelijk gebruiksgeval wanneer de gebruiker uit middelen (bijvoorbeeld, pagina&#39;s, componenten, activa, etc.) moet selecteren. Dit kan bijvoorbeeld de vorm aannemen van een lijst waaruit de auteur een item moet kiezen.

Om de lijst tot een redelijke grootte en ook relevant voor het gebruiksgeval te houden, kan een filter in de vorm van een douanevoorspelling worden uitgevoerd. Zie [dit artikel](/help/sites-developing/customizing-page-authoring-touch.md#filtering-resources) voor meer informatie.
