---
title: De consoles aanpassen
seo-title: De consoles aanpassen
description: AEM verstrekt diverse mechanismen om u toe te laten om de consoles van uw auteursinstantie aan te passen
seo-description: AEM verstrekt diverse mechanismen om u toe te laten om de consoles van uw auteursinstantie aan te passen
uuid: 8ecce9ff-5907-41e1-af3b-a8646352d633
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 61a4e196-bd53-4ef0-816b-c14401462457
docset: aem65
translation-type: tm+mt
source-git-commit: c13eabdf4938a47ddf64d55b00f845199591b835

---


# De consoles aanpassen {#customizing-the-consoles}

>[!CAUTION]
>
>In dit document wordt beschreven hoe consoles in de moderne interface met aanraakbediening kunnen worden aangepast. Dit document is niet van toepassing op de klassieke gebruikersinterface.

AEM verstrekt diverse mechanismen om u toe te laten om de consoles (en de [pagina auteursfunctionaliteit](/help/sites-developing/customizing-page-authoring-touch.md)) van uw auteursinstantie aan te passen.

* ClientlibsClientlibs staan u toe om de standaardimplementatie uit te breiden om nieuwe functionaliteit te realiseren, terwijl het hergebruiken van de standaardfuncties, de voorwerpen, en de methodes. Bij het aanpassen kunt u uw eigen clientlib maken onder `/apps.` Bijvoorbeeld de code bevatten die nodig is voor uw aangepaste component.

* OverlaysOverlays zijn gebaseerd op knooppuntdefinities en maken het mogelijk de standaardfunctionaliteit (in `/libs`) te bedekken met uw eigen aangepaste functionaliteit (in `/apps`). Bij het maken van een overlay is een 1:1-kopie van het origineel niet vereist, omdat de samenvoeging van de tekenbron overerving toestaat.

Deze kunnen op verschillende manieren worden gebruikt om uw AEM-consoles uit te breiden. Een kleine selectie wordt hieronder behandeld (op een hoog niveau).

>[!NOTE]
>
>Zie voor meer informatie:
>
>* Clibs gebruiken en maken [](/help/sites-developing/clientlibs.md).
>* Bedekkingen gebruiken en maken [](/help/sites-developing/overlays.md).
>* [Graniet](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html)
>
>
Dit onderwerp wordt ook behandeld in de zitting [AEM Gems](https://docs.adobe.com/content/ddc/en/gems.html) - de aanpassing van de [Gebruikersinterface voor AEM 6.0](https://docs.adobe.com/content/ddc/en/gems/user-interface-customization-for-aem-6.html).

>[!CAUTION]
>
>U ***mag*** niets in het `/libs` pad wijzigen.
>
>De reden hiervoor is dat de inhoud van `/libs` de volgende keer dat u een upgrade uitvoert van uw exemplaar, wordt overschreven (en dat deze inhoud ook kan worden overschreven wanneer u een hotfix- of functiepakket toepast).
>
>De aanbevolen methode voor configuratie en andere wijzigingen is:
>
>1. Het vereiste item opnieuw maken (d.w.z. zoals het in `/libs`) `/apps`
   >
   >
1. Breng wijzigingen aan in `/apps`
>



De volgende locatie in de `/libs` structuur kan bijvoorbeeld worden bedekt:

* consoles (consoles op basis van gebruikersinterface-pagina&#39;s van graniet); bijvoorbeeld:

   * `/libs/wcm/core/content`

>[!NOTE]
>
>Raadpleeg het Knowledge Base-artikel, [Problemen met](https://helpx.adobe.com/experience-manager/kb/troubleshooting-aem-touchui-issues.html)AEM TouchUI oplossen, voor meer tips en gereedschappen.

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

1. U kunt uw eigen componenten bouwen en de overeenkomstige cliëntbibliotheken voor douaneacties omvatten. Bijvoorbeeld een actie **Promote to Twitter** op:

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

   Met eigenschappen op dit knooppunt kunt u definiëren `groups` welke handelingen mogen worden uitgevoerd. bijvoorbeeld: `administrators`

### Kolommen aanpassen in de lijstweergave {#customizing-columns-in-the-list-view}

>[!NOTE]
>
>Deze functie is geoptimaliseerd voor kolommen met tekstvelden. voor andere gegevenstypen is overlay mogelijk `cq/gui/components/siteadmin/admin/listview/columns/analyticscolumnrenderer` in `/apps`.

U kunt als volgt de kolommen in de lijstweergave aanpassen:

1. Bedek de lijst met beschikbare kolommen.

   * Op het knooppunt:

      ```
             /apps/wcm/core/content/common/availablecolumns
      ```

   * Voeg uw nieuwe kolommen toe - of verwijder bestaande kolommen.
   Zie Bedekkingen [gebruiken (en de Samenvoeging van het Middel van de Verspreiding)](/help/sites-developing/overlays.md) voor meer informatie.

1. Optioneel:

   * Als u aanvullende gegevens wilt aansluiten, moet u een [PageInforProvider](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageInfoProvider.html) schrijven met een
      `pageInfoProviderType` eigenschap.
   Bijvoorbeeld, zie hieronder de klasse/de bundel in bijlage (van GitHub).

1. U kunt nu de kolom selecteren in de kolomconfigurator van de lijstweergave.

### Bronnen filteren {#filtering-resources}

Wanneer u een console gebruikt, wordt vaak gebruikgemaakt van een array die de gebruiker moet selecteren (pagina&#39;s, componenten, elementen, enzovoort). Dit kan de vorm hebben van een lijst, bijvoorbeeld van waaruit de auteur een punt moet kiezen.

Om de lijst tot een redelijke grootte te houden en ook relevant voor het gebruiksgeval, kan een filter in de vorm van een douane predikaat worden uitgevoerd. Zie [dit artikel](/help/sites-developing/customizing-page-authoring-touch.md#filtering-resources) voor meer informatie.
