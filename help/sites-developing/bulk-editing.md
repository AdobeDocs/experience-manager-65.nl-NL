---
title: Pagina configureren voor Bulk bewerken van pagina-eigenschappen
seo-title: Configuring your Page for Bulk Editing of Page Properties
description: Met de functie Pagina-eigenschappen bewerken kunt u de eigenschappen van meerdere pagina's tegelijk bewerken
seo-description: Bulk editing of page properties lets you edit the properties of multiple pages at once
uuid: 1ad403d2-4b93-4943-ae45-74bf20705b81
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: fe61ee4b-51b6-4a6f-91d8-1c02b29cc1db
exl-id: 1787e643-fc8e-40e0-8e14-97b222a7c320
source-git-commit: 10b370fd8f855f71c6d7d791c272137bb5e04d97
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# Pagina configureren voor Bulk bewerken van pagina-eigenschappen {#configuring-your-page-for-bulk-editing-of-page-properties}

[Pagina-eigenschappen in bulk bewerken](/help/sites-authoring/editing-page-properties.md#from-the-sites-console-multiple-pages) Hiermee kunt u de eigenschappen van meerdere pagina&#39;s tegelijk bewerken.

Vanwege de mogelijkheid van verschillende waarden zijn pagina-eigenschappen niet standaard ingeschakeld voor bulkbewerking. Ze moeten expliciet worden toegestaan (ingeschakeld). Wanneer u de pagina-eigenschappen definieert die beschikbaar moeten zijn voor bulkbewerking, moet u rekening houden met bepaalde implicaties, zoals:

* Bepaalde velden zijn gewoonlijk uniek, bijvoorbeeld een paginatitel. Bepaal of het zinvol is dergelijke velden in te schakelen voor bulkbewerking wanneer één waarde wordt toegepast.
* Bepaalde velden kunnen meerdere waarden hebben. Dit vereist een zinvolle weergave bij het renderen.

  Bijvoorbeeld een selectievakje dat &quot;Klaar voor publicatie&quot; aangeeft. Dit kan verschillende waarden hebben voordat u bulkbewerkingen uitvoert (bijvoorbeeld gereed, in-revisie, bezig).

>[!CAUTION]
>
>Bulkbewerking van pagina-eigenschappen is:
>
>* Niet beschikbaar in de klassieke gebruikersinterface.
>* Niet beschikbaar voor pagina&#39;s in een live kopie.
>* Alleen beschikbaar voor pagina&#39;s met hetzelfde brontype.
>

>[!NOTE]
>
>Bulkbewerking is ook beschikbaar voor Elementen. Het is erg vergelijkbaar, maar op een paar punten verschilt het. Zie [Eigenschappen van meerdere elementen bewerken](/help/assets/metadata.md) voor volledige informatie. U kunt de velden in de Bulk Metadata Editor voor Assets aanpassen met de opdracht [Schema-editor](/help/assets/metadata-schemas.md).

## Veld inschakelen {#enabling-a-field}

>[!NOTE]
>
>Bepaalde velden kunnen meerdere waarden hebben. Dit vereist een zinvolle weergave bij het renderen. Daarom moet u alleen de volgende veldtypen inschakelen:
>
>* `/libs/granite/ui/components/foundation/form/textfield`
>* `/libs/granite/ui/components/foundation/form/textarea`
>* `/libs/granite/ui/components/foundation/form/tagspicker`
>* `/libs/granite/ui/components/foundation/form/datepicker`
>* `/libs/granite/ui/components/foundation/form/pathbrowser`
>* `/libs/granite/ui/components/foundation/form/checkbox`
>

Velden zijn ingeschakeld op de paginacomponent (*niet* in de template):

1. Met CRXDE Lite (of een gelijkwaardige methode) opent u de pagina-component.

   Bijvoorbeeld: `/apps/core/wcm/components/page/v1/page`

   >[!NOTE]
   >
   >Dit voorbeeld veronderstelt dat de Componenten van de Kern op de instantie geïnstalleerd zijn, wat het geval is als de instantie met Wij.Retail steekproefinhoud loopt. Zie de [Documentatie kerncomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) voor meer informatie .

1. Ga naar het gewenste veld in het dialoogvenster `cq:dialog` definitie.
1. Definieer de volgende eigenschap op het veldknooppunt:

   * **Naam**: `allowBulkEdit`
   * **Type**: `Boolean`
   * **Waarde**: `true`

   Bijvoorbeeld voor de standaardpagina [stichtingscomponent](/help/sites-authoring/default-components-foundation.md):

   `/libs/foundation/components/page`

   De eigenschap wordt gedefinieerd op:

   `cq:dialog/content/items/tabs/items/basic/items/column/items/onofftime/items/ondate`

   >[!CAUTION]
   >
   >U ***moet*** niets wijzigen in het dialoogvenster `/libs` pad.
   >
   >Dit komt omdat de inhoud van `/libs` wordt de volgende keer overschreven wanneer u een upgrade uitvoert van uw exemplaar (en kan worden overschreven wanneer u een hotfix- of functiepakket toepast).
   >
   >De aanbevolen methode voor configuratie en andere wijzigingen is:
   >
   >    1. Het vereiste item opnieuw maken (dat wil zeggen, zoals het bestaat in `/libs`) onder `/apps`
   >    1. Breng wijzigingen aan in `/apps`

1. Selecteren **Alles opslaan** om uw updates voort te zetten.
