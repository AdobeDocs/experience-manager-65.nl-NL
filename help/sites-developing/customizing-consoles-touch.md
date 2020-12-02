---
title: De consoles aanpassen
seo-title: De consoles aanpassen
description: AEM biedt verschillende mechanismen waarmee u de consoles van de ontwerpinstantie kunt aanpassen
seo-description: AEM biedt verschillende mechanismen waarmee u de consoles van de ontwerpinstantie kunt aanpassen
uuid: 8ecce9ff-5907-41e1-af3b-a8646352d633
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 61a4e196-bd53-4ef0-816b-c14401462457
docset: aem65
translation-type: tm+mt
source-git-commit: c13eabdf4938a47ddf64d55b00f845199591b835
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 0%

---


# De consoles {#customizing-the-consoles} aanpassen

>[!CAUTION]
>
>In dit document wordt beschreven hoe consoles in de moderne interface met aanraakbediening kunnen worden aangepast. Dit document is niet van toepassing op de klassieke gebruikersinterface.

AEM verstrekt diverse mechanismen om u toe te laten om de consoles (en [pagina auteursfunctionaliteit](/help/sites-developing/customizing-page-authoring-touch.md)) van uw auteursinstantie aan te passen.

* Clientlibs
Clientlibs staan u toe om de standaardimplementatie uit te breiden om nieuwe functionaliteit te realiseren, terwijl het hergebruiken van de standaardfuncties, de voorwerpen, en de methodes. Wanneer het aanpassen, kunt u uw eigen clientlib onder `/apps.` tot stand brengen bijvoorbeeld het kan de code houden die voor uw douanecomponent wordt vereist.

* Bedekkingen
Bedekkingen zijn gebaseerd op knooppuntdefinities en staan u toe om de standaardfunctionaliteit (in `/libs`) met uw eigen aangepaste functionaliteit (in `/apps`) te bedekken. Bij het maken van een overlay is een 1:1-kopie van het origineel niet vereist, omdat de samenvoeging van de tekenbron overerving toestaat.

Deze kunnen op vele manieren worden gebruikt om uw AEM consoles uit te breiden. Een kleine selectie wordt hieronder behandeld (op een hoog niveau).

>[!NOTE]
>
>Zie voor meer informatie:
>
>* Het gebruiken en het creëren van [clientlibs](/help/sites-developing/clientlibs.md).
>* [overlays](/help/sites-developing/overlays.md) gebruiken en maken.
>* [Graniet](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html)

>
>
Dit onderwerp wordt ook behandeld in [AEM Gems](https://docs.adobe.com/content/ddc/en/gems.html) zitting - [Gebruikersinterfaceaanpassing voor AEM 6.0](https://docs.adobe.com/content/ddc/en/gems/user-interface-customization-for-aem-6.html).

>[!CAUTION]
>
>U ***must*** verandert niets in `/libs` weg.
>
>Dit komt doordat de inhoud van `/libs` de volgende keer wordt overschreven dat u uw exemplaar bijwerkt (en dat kan worden overschreven wanneer u een hotfix- of functiepakket toepast).
>
>De aanbevolen methode voor configuratie en andere wijzigingen is:
>
>1. Het vereiste item opnieuw maken (dat wil zeggen zoals het bestaat in `/libs`) onder `/apps`
   >
   >
1. Wijzigingen aanbrengen binnen `/apps`

>



De volgende locatie in de `/libs`-structuur kan bijvoorbeeld worden bedekt:

* consoles (consoles op basis van gebruikersinterface-pagina&#39;s van graniet); bijvoorbeeld:

   * `/libs/wcm/core/content`

>[!NOTE]
>
>Zie het artikel in de Knowledge Base, [Problemen oplossen AEM TouchUI-problemen](https://helpx.adobe.com/experience-manager/kb/troubleshooting-aem-touchui-issues.html), voor meer tips en gereedschappen.

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

   * **Naam**:  `sling:orderBefore`
   * **Type**:  `String`
   * **Waarde**:  `column`

### Nieuwe handeling toevoegen aan de werkbalk {#add-new-action-to-the-toolbar}

1. U kunt uw eigen componenten bouwen en de overeenkomstige cliëntbibliotheken voor douaneacties omvatten. Bijvoorbeeld een handeling **Promote to Twitter** op:

   `/apps/wcm/core/clientlibs/sites/js/twitter.js`

   Dit kan dan met een toolbarpunt op uw console worden verbonden:

   `/apps/<yourProject>/admin/ext/launches`

   In de selectiemodus bijvoorbeeld:

   `content/jcr:content/body/content/header/items/selection/items/twitter`

### Een werkbalkhandeling beperken tot een specifieke groep {#restrict-a-toolbar-action-to-a-specific-group}

1. U kunt een aangepaste rendervoorwaarde gebruiken om de standaardhandeling te bedekken en specifieke voorwaarden op te leggen waaraan moet worden voldaan voordat deze wordt gerenderd.

   Maak bijvoorbeeld een component om de rendervoorwaarden op basis van groep te beheren:

   `/apps/myapp/components/renderconditions/group`

1. U kunt deze toepassen op de actie Site maken op de Sites-console:

   `/libs/wcm/core/content/sites`

   Maak de bedekking:

   `/apps/wcm/core/content/sites`

1. Voeg vervolgens de rendervoorwaarde voor de actie toe:

   `jcr:content/body/content/header/items/default/items/create/items/createsite/rendercondition`

   Gebruikend eigenschappen op deze knoop kunt u `groups` bepalen toegestaan om de specifieke actie uit te voeren; bijvoorbeeld `administrators`

### Kolommen aanpassen in de lijstweergave {#customizing-columns-in-the-list-view}

>[!NOTE]
>
>Deze functie is geoptimaliseerd voor kolommen met tekstvelden. voor andere gegevenstypen is het mogelijk om `cq/gui/components/siteadmin/admin/listview/columns/analyticscolumnrenderer` in `/apps` te bedekken.

U kunt als volgt de kolommen in de lijstweergave aanpassen:

1. Bedek de lijst met beschikbare kolommen.

   * Op het knooppunt:

      ```
             /apps/wcm/core/content/common/availablecolumns
      ```

   * Voeg uw nieuwe kolommen toe - of verwijder bestaande kolommen.
   Zie [Bedekkingen gebruiken (en de Samenvoegen van het Middel van de Verspreiding)](/help/sites-developing/overlays.md) voor meer informatie.

1. Optioneel:

   * Als u aanvullende gegevens wilt insluiten, moet u een [PageInforProvider](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageInfoProvider.html) met een
      `pageInfoProviderType` eigenschap.

   Bijvoorbeeld, zie hieronder de klasse/de bundel in bijlage (van GitHub).

1. U kunt nu de kolom selecteren in de kolomconfigurator van de lijstweergave.

### Bronnen filteren {#filtering-resources}

Wanneer u een console gebruikt, wordt vaak gebruikgemaakt van een array die de gebruiker moet selecteren (pagina&#39;s, componenten, elementen, enzovoort). Dit kan de vorm hebben van een lijst, bijvoorbeeld van waaruit de auteur een punt moet kiezen.

Om de lijst tot een redelijke grootte te houden en ook relevant voor het gebruiksgeval, kan een filter in de vorm van een douane predikaat worden uitgevoerd. Zie [dit artikel](/help/sites-developing/customizing-page-authoring-touch.md#filtering-resources) voor meer informatie.
