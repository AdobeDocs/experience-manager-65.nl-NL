---
title: Weergaven van pagina-eigenschappen aanpassen
seo-title: Weergaven van pagina-eigenschappen aanpassen
description: Elke pagina heeft een set eigenschappen die u naar wens kunt bewerken
seo-description: Elke pagina heeft een set eigenschappen die u naar wens kunt bewerken
uuid: cbfca6e6-cb9e-43b1-8889-09a7cc9f8a51
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 6f8e08d1-831e-441a-ad1a-f5c8788f32d7
translation-type: tm+mt
source-git-commit: c38c27d6f7172734f80735dd2f42cfa7bf58ad1d

---


# Weergaven van pagina-eigenschappen aanpassen{#customizing-views-of-page-properties}

Elke pagina heeft een set [eigenschappen](/help/sites-authoring/editing-page-properties.md) die gebruikers kunnen weergeven en bewerken. Sommige zijn vereist voor het maken van de pagina (de weergave Maken), andere kunnen in een later stadium worden weergegeven en bewerkt (de weergave Bewerken). Deze pagina-eigenschappen worden gedefinieerd en beschikbaar gesteld door het dialoogvenster ( `cq:dialog`) van de juiste pagina-component.

>[!CAUTION]
>
>Het aanpassen van de weergave van pagina-eigenschappen is niet beschikbaar in de klassieke interface.

De standaardstatus voor elke pagina-eigenschap is:

* verborgen in de weergave Maken (bijvoorbeeld de wizard Pagina **** maken)

* beschikbaar in de weergave Bewerken (bijvoorbeeld **Weergave-eigenschappen**)

De gebieden moeten specifiek worden gevormd als om het even welke verandering wordt vereist. Dit wordt gedaan gebruikend de aangewezen knoopeigenschappen:

* Pagina-eigenschap die beschikbaar moet zijn in de weergave Maken (bijvoorbeeld de wizard Pagina **** maken):

   * Naam: `cq:showOnCreate`
   * Type: `Boolean`

* Pagina-eigenschap die beschikbaar moet zijn in de bewerkingsweergave (bijvoorbeeld de optie **Weergeven**/**Bewerken**) **Eigenschappen** :

   * Naam: `cq:hideOnEdit`
   * Type: `Boolean`

Zie bijvoorbeeld de instellingen voor velden die zijn gegroepeerd onder **Meer titels en beschrijving** op het tabblad **Standaard** voor de component Pagina. Deze worden in de wizard **Pagina** maken weergegeven zoals `cq:showOnCreate` is ingesteld op `true`:

```xml
/libs/foundation/components/page/cq:dialog/content/items/tabs/items/basic/items/column/items/moretitles
```

>[!TIP]
>
>Zie de zelfstudie [Pagina-eigenschappen](https://docs.adobe.com/content/help/en/experience-manager-learn/sites/developing/page-properties-technical-video-develop.html) uitbreiden voor een handleiding voor het aanpassen van pagina-eigenschappen.

## De pagina-eigenschappen configureren {#configuring-your-page-properties}

U kunt ook de beschikbare velden configureren door het dialoogvenster van de paginacomponent te configureren en de juiste knoopeigenschappen toe te passen.

Standaard geeft de wizard [**Pagina **](/help/sites-authoring/managing-pages.md#creating-a-new-page)maken bijvoorbeeld de velden weer die zijn gegroepeerd onder** Meer titels en beschrijving **. Om deze te verbergen vormt u:

1. Maak de pagina-component onder `/apps`.
1. Maak een overschrijving (met *dialoogdiff* van de [Sling Resource Merger](/help/sites-developing/sling-resource-merger.md)) voor de `basic` sectie van de paginacomponent; bijvoorbeeld:

   ```xml
   <your-page-component>/cq:dialog/content/items/tabs/items/basic
   ```

   >[!NOTE]
   >
   >Zie ter referentie:
   >
   >    `/libs/wcm/foundation/components/basicpage/v1/basicpage/cq:dialog`
   U ***mag*** echter niets in het `/libs` pad wijzigen.
   De reden hiervoor is dat de inhoud van `/libs` de volgende keer dat u een upgrade uitvoert van uw exemplaar, wordt overschreven (en dat deze inhoud ook kan worden overschreven wanneer u een hotfix- of functiepakket toepast).
   De aanbevolen methode voor configuratie en andere wijzigingen is:
   1. Het vereiste item opnieuw maken (d.w.z. zoals het in `/libs`) `/apps`
   1. Breng wijzigingen aan in `/apps`


1. Stel de `path` eigenschap in `basic` om naar de overschrijving van het basistabblad te verwijzen (zie ook de volgende stap). Bijvoorbeeld:

   ```xml
   /apps/demos/components/page/tabs/basic
   ```

1. Maak een overschrijving van het `basic` -- `moretitles` gedeelte op het corresponderende pad. bijvoorbeeld:

   ```xml
   /apps/demos/components/page/tabs/basic/items/column/items/moretitles
   ```

1. Pas de juiste node-eigenschap toe:

   * **Naam**: `cq:showOnCreate`
   * **Type**: `Boolean`
   * **Waarde**: `false`
   De sectie **Meer titels en beschrijving** wordt niet meer weergegeven in de wizard **Pagina** maken.

>[!NOTE]
Wanneer het vormen van pagina-eigenschappen voor gebruik met levende exemplaren zie het [Vormen Msm op Eigenschappen](/help/sites-developing/extending-msm.md#configuring-msm-locks-on-page-properties-touch-enabled-ui) van de Pagina voor meer details.

## Voorbeeldconfiguratie van pagina-eigenschappen {#sample-configuration-of-page-properties}

Dit voorbeeld demonstreert de Dialog Diff-techniek van de [Sling Resource Merger](/help/sites-developing/sling-resource-merger.md). inclusief het gebruik van [`sling:orderBefore`](/help/sites-developing/sling-resource-merger.md#properties). Het illustreert ook het gebruik van zowel `cq:showOnCreate` als `cq:hideOnEdit`.

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [Open aem-creatie-uitbreiding-pagina-dialoog project op GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-page-dialog)
