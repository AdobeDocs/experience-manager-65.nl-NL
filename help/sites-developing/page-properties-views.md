---
title: Weergaven van pagina-eigenschappen aanpassen
seo-title: Customizing Views of Page Properties
description: Elke pagina heeft een set eigenschappen die u naar wens kunt bewerken
seo-description: Every page has a set of properties that you can edit as required
uuid: cbfca6e6-cb9e-43b1-8889-09a7cc9f8a51
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 6f8e08d1-831e-441a-ad1a-f5c8788f32d7
exl-id: 292874bf-2ee6-4638-937c-f8f26c93ca65
source-git-commit: b886844dc80482ae4aae5fc7ce09e466efecc3bd
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# Weergaven van pagina-eigenschappen aanpassen{#customizing-views-of-page-properties}

Elke pagina heeft een set [eigenschappen](/help/sites-authoring/editing-page-properties.md) die door gebruikers kunnen worden bekeken en bewerkt; Sommige zijn vereist voor het maken van de pagina (de weergave Maken), andere kunnen in een later stadium worden weergegeven en bewerkt (de weergave Bewerken). Deze pagina-eigenschappen worden gedefinieerd en beschikbaar gesteld door het dialoogvenster ( `cq:dialog`) van het desbetreffende pagina-onderdeel.

>[!CAUTION]
>
>Het aanpassen van de weergave van pagina-eigenschappen is niet beschikbaar in de klassieke interface.

De standaardstatus voor elke pagina-eigenschap is:

* verborgen in de ontwerpweergave (bijvoorbeeld **Pagina maken** wizard)

* beschikbaar in de bewerkingsweergave (bijvoorbeeld **Eigenschappen weergeven**)

De gebieden moeten specifiek worden gevormd als om het even welke verandering wordt vereist. Dit wordt gedaan gebruikend de aangewezen knoopeigenschappen:

* Pagina-eigenschap die beschikbaar moet zijn in de weergave Maken (bijvoorbeeld **Pagina maken** wizard):

   * Naam: `cq:showOnCreate`
   * Type: `Boolean`

* Pagina-eigenschap die beschikbaar moet zijn in de bewerkingsweergave (bijvoorbeeld **Weergave**/**Bewerken**) **Eigenschappen** optie):

   * Naam: `cq:hideOnEdit`
   * Type: `Boolean`

Zie bijvoorbeeld de instellingen voor velden die zijn gegroepeerd onder de **Meer titels en beschrijving** op de **Basis** tabblad voor de basiscomponent Pagina. Deze zijn zichtbaar in het dialoogvenster **Pagina maken** wizard als `cq:showOnCreate` is ingesteld op `true`:

```xml
/libs/foundation/components/page/cq:dialog/content/items/tabs/items/basic/items/column/items/moretitles
```

>[!TIP]
>
>Zie de [Zelfstudie Pagina-eigenschappen uitbreiden](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/developing/page-properties-technical-video-develop.html) voor een handleiding voor het aanpassen van pagina-eigenschappen.

## De pagina-eigenschappen configureren {#configuring-your-page-properties}

U kunt ook de beschikbare velden configureren door het dialoogvenster van de paginacomponent te configureren en de juiste knoopeigenschappen toe te passen.

Standaard worden bijvoorbeeld de [**Pagina maken** wizard](/help/sites-authoring/managing-pages.md#creating-a-new-page) geeft de velden weer die onder zijn gegroepeerd **Meer titels en beschrijving**. Om deze te verbergen vormt u:

1. De pagina-component maken onder `/apps`.
1. Overschrijven maken (met *Diff* door de [Samenvoegen van verkoopbronnen](/help/sites-developing/sling-resource-merger.md)) voor de `basic` sectie van uw paginacomponent; bijvoorbeeld:

   ```xml
   <your-page-component>/cq:dialog/content/items/tabs/items/basic
   ```

   >[!NOTE]
   >
   >Zie ter referentie:
   >
   >    `/libs/wcm/foundation/components/basicpage/v1/basicpage/cq:dialog`
   U ***moet*** niets wijzigen in de `/libs` pad.
   Dit komt omdat de inhoud van `/libs` wordt de volgende keer overschreven wanneer u een upgrade uitvoert van uw exemplaar (en kan worden overschreven wanneer u een hotfix- of functiepakket toepast).
   De aanbevolen methode voor configuratie en andere wijzigingen is:
   1. Het vereiste item opnieuw maken (bijvoorbeeld zoals het bestaat in `/libs`) onder `/apps`
   1. Breng wijzigingen aan in `/apps`


1. Stel de `path` eigenschap op `basic` om naar de opheffing van het basislusje te wijzen (zie ook de volgende stap). Bijvoorbeeld:

   ```xml
   /apps/demos/components/page/tabs/basic
   ```

1. Een overschrijving maken van de `basic` - `moretitles` het desbetreffende pad; bijvoorbeeld:

   ```xml
   /apps/demos/components/page/tabs/basic/items/column/items/moretitles
   ```

1. Pas de juiste node-eigenschap toe:

   * **Naam**: `cq:showOnCreate`
   * **Type**: `Boolean`
   * **Waarde**: `false`

   De **Meer titels en beschrijving** wordt niet meer weergegeven in het dialoogvenster **Pagina maken** wizard.

>[!NOTE]
Zie wanneer u pagina-eigenschappen configureert voor gebruik met live kopieën [MSM-vergrendelingen configureren in pagina-eigenschappen](/help/sites-developing/extending-msm.md#configuring-msm-locks-on-page-properties-touch-enabled-ui) voor meer informatie .

## Voorbeeldconfiguratie van pagina-eigenschappen {#sample-configuration-of-page-properties}

In dit voorbeeld ziet u de dialoochtechniek van het dialoogvenster [Samenvoegen van verkoopbronnen](/help/sites-developing/sling-resource-merger.md); inclusief het gebruik van [`sling:orderBefore`](/help/sites-developing/sling-resource-merger.md#properties). Het illustreert ook het gebruik van beide `cq:showOnCreate` en `cq:hideOnEdit`.

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [Open aem-creatie-uitbreiding-pagina-dialoog project op GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-page-dialog)
