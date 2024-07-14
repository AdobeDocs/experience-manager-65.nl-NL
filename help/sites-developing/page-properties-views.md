---
title: Weergaven van pagina-eigenschappen aanpassen
description: Elke pagina heeft een set eigenschappen die u naar wens kunt bewerken
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
exl-id: 292874bf-2ee6-4638-937c-f8f26c93ca65
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---

# Weergaven van pagina-eigenschappen aanpassen{#customizing-views-of-page-properties}

Elke pagina heeft een reeks [ eigenschappen ](/help/sites-authoring/editing-page-properties.md) die door gebruikers kunnen worden bekeken en worden uitgegeven; sommige worden vereist wanneer het creëren van de pagina (creeer mening), anderen kunnen (geef mening uit) in een recentere fase worden bekeken en worden uitgegeven. Deze pagina-eigenschappen worden gedefinieerd en beschikbaar gesteld door het dialoogvenster ( `cq:dialog` ) van de juiste paginacomponent.

>[!CAUTION]
>
>Het aanpassen van de weergave van pagina-eigenschappen is niet beschikbaar in de klassieke interface.

De standaardstatus voor elke pagina-eigenschap is:

* verborgen in creeer mening (bijvoorbeeld, **creeer de tovenaar van de Pagina**)

* beschikbaar in geef mening uit (bijvoorbeeld, **Eigenschappen van de Mening**)

De gebieden moeten specifiek worden gevormd als om het even welke verandering wordt vereist. Dit wordt gedaan gebruikend de aangewezen knoopeigenschappen:

* Het bezit van de pagina dat in creeert mening (bijvoorbeeld, **moet beschikbaar zijn leidt tot de tovenaar van de Pagina**):

   * Naam: `cq:showOnCreate`
   * Type: `Boolean`

* Het bezit van de pagina om in uit te geven mening (bijvoorbeeld, **Mening** te zijn/ **geeft** uit) **Eigenschappen** optie):

   * Naam: `cq:hideOnEdit`
   * Type: `Boolean`

Bijvoorbeeld, zie de montages voor gebieden die onder **worden gegroepeerd Meer Titels en Beschrijving** op het **Basis** lusje voor de component van de stichtingspagina. Deze zijn zichtbaar in **Create de tovenaar van de Pagina** aangezien `cq:showOnCreate` aan `true` is geplaatst:

```xml
/libs/foundation/components/page/cq:dialog/content/items/tabs/items/basic/items/column/items/moretitles
```

>[!TIP]
>
>Zie het [ Uitbreiden van de zelfstudie van de Eigenschappen van de Pagina ](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/developing/page-properties-technical-video-develop.html) voor een gids aan het aanpassen van paginaeigenschappen.

## De pagina-eigenschappen configureren {#configuring-your-page-properties}

U kunt ook de beschikbare velden configureren door het dialoogvenster van de paginacomponent te configureren en de juiste knoopeigenschappen toe te passen.

Bijvoorbeeld, door gebrek leidt [**tot de tovenaar van de Pagina** ](/help/sites-authoring/managing-pages.md#creating-a-new-page) de gebieden die onder **Meer Titels en Beschrijving** worden gegroepeerd. Om deze te verbergen vormt u:

1. Maak uw paginacomponent onder `/apps` .
1. Creeer een opheffing (gebruikend *diff van de dialoog* die door [ wordt verstrekt het Verspreiden van de Fusie van het Middel ](/help/sites-developing/sling-resource-merger.md)) voor de `basic` sectie van uw paginacomponent; bijvoorbeeld:

   ```xml
   <your-page-component>/cq:dialog/content/items/tabs/items/basic
   ```

   >[!NOTE]
   >
   >Zie ter referentie:
   >
   >    `/libs/wcm/foundation/components/basicpage/v1/basicpage/cq:dialog`
   >
   >Nochtans, moet u ****** niets in de `/libs` weg veranderen.
   >
   >De reden hiervoor is dat de inhoud van `/libs` de volgende keer dat u een upgrade uitvoert van de instantie wordt overschreven (en dat deze inhoud ook kan worden overschreven wanneer u een hotfix- of functiepakket toepast).
   >
   >De aanbevolen methode voor configuratie en andere wijzigingen is:
   >
   >1. Het vereiste item opnieuw maken (dat wil zeggen, zoals het in `/libs` staat) onder `/apps`
   >1. Breng eventuele wijzigingen aan binnen `/apps`

1. Stel de eigenschap `path` op `basic` zo in dat deze naar de overschrijving van het basistabblad verwijst (zie ook de volgende stap). Bijvoorbeeld:

   ```xml
   /apps/demos/components/page/tabs/basic
   ```

1. Maak een overschrijving van de sectie `basic` - `moretitles` op het bijbehorende pad, bijvoorbeeld:

   ```xml
   /apps/demos/components/page/tabs/basic/items/column/items/moretitles
   ```

1. Pas de juiste node-eigenschap toe:

   * **Naam**: `cq:showOnCreate`
   * **Type**: `Boolean`
   * **Waarde**: `false`

   De **Meer Titels en de sectie van de Beschrijving** zullen niet meer in **worden getoond creëren de tovenaar van de Pagina**.

>[!NOTE]
>
>Wanneer het vormen van paginaeigenschappen voor gebruik met levende exemplaren zie [ het Vormen Msm op de Eigenschappen van de Pagina ](/help/sites-developing/extending-msm.md#configuring-msm-locks-on-page-properties-touch-enabled-ui) voor meer details.

## Voorbeeldconfiguratie van pagina-eigenschappen {#sample-configuration-of-page-properties}

Deze steekproef toont de dialoog afschuivende techniek van de [ Verteller van het Middel Sling ](/help/sites-developing/sling-resource-merger.md) aan; met inbegrip van gebruik van [`sling:orderBefore`](/help/sites-developing/sling-resource-merger.md#properties). Het illustreert ook het gebruik van zowel `cq:showOnCreate` als `cq:hideOnEdit` .

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [ open aem-auteurs-uitbreiding-pagina-dialoog project op GitHub ](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-page-dialog)
