---
title: De consoles aanpassen
description: AEM biedt verschillende mechanismen waarmee u de consoles van de ontwerpinstantie kunt aanpassen
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
docset: aem65
exl-id: 6e67f2b3-78b9-45f2-b496-61776b9fd9cc
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 3aa55b88f589749fb49d5ff46340b0912d490157
workflow-type: tm+mt
source-wordcount: '649'
ht-degree: 0%

---

# De consoles aanpassen {#customizing-the-consoles}

>[!CAUTION]
>
>In dit document wordt beschreven hoe consoles in de moderne interface met aanraakbediening kunnen worden aangepast. Dit document is niet van toepassing op de klassieke gebruikersinterface.

AEM verstrekt diverse mechanismen om u toe te laten om de consoles (en de [ pagina auteursfunctionaliteit ](/help/sites-developing/customizing-page-authoring-touch.md)) van uw auteursinstantie aan te passen.

* Clientlibs
Clientlibs laten u de standaardimplementatie uitbreiden om nieuwe functionaliteit te realiseren, terwijl het hergebruiken van de standaardfuncties, de voorwerpen, en de methodes. Bij het aanpassen kunt u onder `/apps.` uw eigen clientlib maken. Deze kan bijvoorbeeld de code bevatten die is vereist voor uw aangepaste component.

* Bedekkingen
Bedekkingen zijn gebaseerd op knooppuntdefinities en u kunt de standaardfunctionaliteit (in `/libs` ) bedekken met uw eigen aangepaste functionaliteit (in `/apps` ). Bij het maken van een overlay is een 1:1-kopie van het origineel niet vereist, omdat de samenvoeging van de tekenbron overerving toestaat.

Deze kunnen op vele manieren worden gebruikt om uw AEM te uitbreiden. Een kleine selectie wordt hieronder behandeld (op een hoog niveau).

>[!NOTE]
>
>Zie voor meer informatie:
>
>* Het gebruiken van en het creëren van [ clientlibs ](/help/sites-developing/clientlibs.md).
>* Het gebruiken van en het creëren van [ bekledingen ](/help/sites-developing/overlays.md).
>* [ Graniet ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html)
>


>[!CAUTION]
>
>U ***moet*** niets in de `/libs` weg veranderen.
>
>De reden hiervoor is dat de inhoud van `/libs` de volgende keer dat u een upgrade uitvoert van de instantie wordt overschreven (en dat deze inhoud ook kan worden overschreven wanneer u een hotfix- of functiepakket toepast).
>
>De aanbevolen methode voor configuratie en andere wijzigingen is:
>
>1. Het vereiste item opnieuw maken (dat wil zeggen, zoals het in `/libs` staat) onder `/apps`
>
>1. Breng eventuele wijzigingen aan binnen `/apps`
>

De volgende locatie in de `/libs` -structuur kan bijvoorbeeld worden bedekt:

* consoles (consoles op basis van gebruikersinterface-pagina&#39;s van graniet), bijvoorbeeld:

   * `/libs/wcm/core/content`

>[!NOTE]
>
>Zie het artikel van de Kennisbank, [ het Oplossen van problemen AEM kwesties TouchUI ](https://helpx.adobe.com/experience-manager/kb/troubleshooting-aem-touchui-issues.html), voor verdere uiteinden en hulpmiddelen.

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

1. U kunt uw eigen componenten bouwen en de overeenkomstige cliëntbibliotheken voor douaneacties omvatten. Bijvoorbeeld, bevorderen a **aan Twitter** actie bij:

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

   Met eigenschappen op dit knooppunt kunt u de handeling `groups` definiëren die de specifieke handeling mag uitvoeren, bijvoorbeeld `administrators`

### Kolommen aanpassen in de lijstweergave {#customizing-columns-in-the-list-view}

>[!NOTE]
>
>Deze functie is geoptimaliseerd voor kolommen met tekstvelden; voor andere gegevenstypen is het mogelijk om `cq/gui/components/siteadmin/admin/listview/columns/analyticscolumnrenderer` in `/apps` te bedekken.

U kunt als volgt de kolommen in de lijstweergave aanpassen:

1. Bedek de lijst met beschikbare kolommen.

   * Op het knooppunt:

     ```
            /apps/wcm/core/content/common/availablecolumns
     ```

   * Voeg uw nieuwe kolommen toe - of verwijder bestaande kolommen.

   Zie [ Gebruikend Bedekkingen (en de het Verschuiven Fusie van het Middel) ](/help/sites-developing/overlays.md) voor meer informatie.

1. Optioneel:

   * Als u extra gegevens wilt stoppen, moet u a [ PageInforProvider ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageInfoProvider.html) met a schrijven

     `pageInfoProviderType` eigenschap.

   Bijvoorbeeld, zie hieronder de klasse/de bundel in bijlage (van GitHub).

1. U kunt nu de kolom selecteren in de kolomconfigurator van de lijstweergave.

### Bronnen filteren {#filtering-resources}

Wanneer het gebruiken van een console, is een gemeenschappelijk gebruiksgeval wanneer de gebruiker uit middelen (bijvoorbeeld, pagina&#39;s, componenten, activa, etc.) moet selecteren. Dit kan bijvoorbeeld de vorm aannemen van een lijst waaruit de auteur een item moet kiezen.

Om de lijst tot een redelijke grootte en ook relevant voor het gebruiksgeval te houden, kan een filter in de vorm van een douanevoorspelling worden uitgevoerd. Zie [ het Aanpassen van de Authoring van de Pagina - het Filtreren Middelen ](/help/sites-developing/customizing-page-authoring-touch.md#filtering-resources) voor details.
