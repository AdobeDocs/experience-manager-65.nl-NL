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
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 1%

---


# Weergaven van pagina-eigenschappen aanpassen{#customizing-views-of-page-properties}

Elke pagina heeft een reeks [eigenschappen](/help/sites-authoring/editing-page-properties.md) die door gebruikers kunnen worden bekeken en worden uitgegeven; Sommige zijn vereist voor het maken van de pagina (de weergave Maken), andere kunnen in een later stadium worden weergegeven en bewerkt (de weergave Bewerken). Deze pagina-eigenschappen worden gedefinieerd en beschikbaar gesteld door het dialoogvenster ( `cq:dialog`) van de juiste paginacomponent.

>[!CAUTION]
>
>Het aanpassen van de weergave van pagina-eigenschappen is niet beschikbaar in de klassieke interface.

De standaardstatus voor elke pagina-eigenschap is:

* verborgen in de ontwerpweergave (bijvoorbeeld **Pagina maken** wizard)

* beschikbaar in de bewerkingsweergave (bijvoorbeeld **Eigenschappen weergeven**)

De gebieden moeten specifiek worden gevormd als om het even welke verandering wordt vereist. Dit wordt gedaan gebruikend de aangewezen knoopeigenschappen:

* Pagina-eigenschap die beschikbaar moet zijn in de weergave Maken (bijvoorbeeld **Create Page** wizard):

   * Naam: `cq:showOnCreate`
   * Type: `Boolean`

* Pagina-eigenschap die beschikbaar moet zijn in de bewerkingsweergave (bijvoorbeeld **Weergave**/**Bewerken**) **Eigenschappen** (optie):

   * Naam: `cq:hideOnEdit`
   * Type: `Boolean`

Zie bijvoorbeeld de instellingen voor velden die zijn gegroepeerd onder **Meer titels en beschrijvingen** op het tabblad **Standaard** voor de basispaginacomponent. Deze zijn zichtbaar in **Create Page** tovenaar aangezien `cq:showOnCreate` aan `true` is geplaatst:

```xml
/libs/foundation/components/page/cq:dialog/content/items/tabs/items/basic/items/column/items/moretitles
```

>[!TIP]
>
>Zie de zelfstudie [Pagina-eigenschappen uitbreiden](https://docs.adobe.com/content/help/en/experience-manager-learn/sites/developing/page-properties-technical-video-develop.html) voor een handleiding voor het aanpassen van pagina-eigenschappen.

## De pagina-eigenschappen {#configuring-your-page-properties} configureren

U kunt ook de beschikbare velden configureren door het dialoogvenster van de paginacomponent te configureren en de juiste knoopeigenschappen toe te passen.

De wizard [**Pagina maken**](/help/sites-authoring/managing-pages.md#creating-a-new-page) geeft standaard de velden weer die zijn gegroepeerd onder **Meer titels en beschrijving**. Om deze te verbergen vormt u:

1. Maak uw paginacomponent onder `/apps`.
1. Maak een overschrijving (met *dialog diff* geleverd door [Sling Resource Merger](/help/sites-developing/sling-resource-merger.md)) voor de sectie `basic` van uw paginacomponent; bijvoorbeeld:

   ```xml
   <your-page-component>/cq:dialog/content/items/tabs/items/basic
   ```

   >[!NOTE]
   >
   >Zie ter referentie:
   >
   >    `/libs/wcm/foundation/components/basicpage/v1/basicpage/cq:dialog`
   U moet ***echter*** niets in het `/libs`-pad wijzigen.
   Dit komt doordat de inhoud van `/libs` de volgende keer wordt overschreven dat u uw exemplaar bijwerkt (en dat kan worden overschreven wanneer u een hotfix- of functiepakket toepast).
   De aanbevolen methode voor configuratie en andere wijzigingen is:
   1. Het vereiste item opnieuw maken (dat wil zeggen zoals het bestaat in `/libs`) onder `/apps`
   1. Wijzigingen aanbrengen binnen `/apps`


1. Stel de eigenschap `path` op `basic` in om naar de overschrijving van het basistabblad te verwijzen (zie ook de volgende stap). Bijvoorbeeld:

   ```xml
   /apps/demos/components/page/tabs/basic
   ```

1. Maak een overschrijving van de sectie `basic` - `moretitles` bij het corresponderende pad; bijvoorbeeld:

   ```xml
   /apps/demos/components/page/tabs/basic/items/column/items/moretitles
   ```

1. Pas de juiste node-eigenschap toe:

   * **Naam**:  `cq:showOnCreate`
   * **Type**:  `Boolean`
   * **Waarde**:  `false`

   De sectie **Meer titels en beschrijving** wordt niet meer weergegeven in de wizard **Pagina maken**.

>[!NOTE]
Zie [MSM-vergrendelingen configureren op pagina-eigenschappen](/help/sites-developing/extending-msm.md#configuring-msm-locks-on-page-properties-touch-enabled-ui) voor meer informatie wanneer u pagina-eigenschappen configureert voor gebruik met live kopieën.

## Voorbeeldconfiguratie van pagina-eigenschappen {#sample-configuration-of-page-properties}

Dit voorbeeld demonstreert de Dialoog Diff-techniek van [Sling Resource Merger](/help/sites-developing/sling-resource-merger.md). inclusief het gebruik van [`sling:orderBefore`](/help/sites-developing/sling-resource-merger.md#properties). Het illustreert ook het gebruik van zowel `cq:showOnCreate` als `cq:hideOnEdit`.

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [Open aem-creatie-uitbreiding-pagina-dialoog project op GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-page-dialog)
