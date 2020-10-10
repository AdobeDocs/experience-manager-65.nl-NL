---
title: Pagina configureren voor Bulk bewerken van pagina-eigenschappen
seo-title: Pagina configureren voor Bulk bewerken van pagina-eigenschappen
description: Dankzij het Bulksgewijs bewerken van pagina-eigenschappen kunt u de eigenschappen van meerdere pagina's tegelijk bewerken
seo-description: Dankzij het Bulksgewijs bewerken van pagina-eigenschappen kunt u de eigenschappen van meerdere pagina's tegelijk bewerken
uuid: 1ad403d2-4b93-4943-ae45-74bf20705b81
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: fe61ee4b-51b6-4a6f-91d8-1c02b29cc1db
translation-type: tm+mt
source-git-commit: b08149e00c418319ebacec71c56472ad4e8e1089
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 2%

---


# Pagina configureren voor Bulk bewerken van pagina-eigenschappen {#configuring-your-page-for-bulk-editing-of-page-properties}

[Met de functie Pagina-eigenschappen](/help/sites-authoring/editing-page-properties.md#from-the-sites-console-multiple-pages) bewerken kunt u de eigenschappen van meerdere pagina&#39;s tegelijk bewerken.

Vanwege de mogelijkheid van verschillende waarden zijn pagina-eigenschappen niet standaard ingeschakeld voor bulkbewerking. Ze moeten expliciet worden toegestaan (ingeschakeld). Wanneer u de pagina-eigenschappen definieert die beschikbaar moeten zijn voor bulkbewerking, moet u rekening houden met bepaalde implicaties, zoals:

* Bepaalde velden zijn gewoonlijk uniek; bijvoorbeeld een paginatitel. U moet beslissen of het zinvol is dergelijke velden in te schakelen voor bulkbewerking, wanneer er één waarde wordt toegepast.
* Bepaalde velden kunnen meerdere waarden hebben. Dit vereist een zinvolle weergave bij het renderen.

   Bijvoorbeeld een selectievakje dat &quot;Klaar voor publicatie&quot; aangeeft. Dit kan verschillende waarden hebben voordat het document bulksgewijs wordt bewerkt (bijvoorbeeld gereed, in revisie, in uitvoering).

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
>Bulkbewerking is ook beschikbaar voor Elementen. Het is erg vergelijkbaar, maar op een paar punten verschilt het. Zie Eigenschappen van meerdere elementen [](/help/assets/metadata.md) bewerken voor meer informatie. Met de [Schema-editor](/help/assets/metadata-schemas.md)kunt u de velden in de editor Metagegevens voor opsommingstekens aanpassen.

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



Velden worden ingeschakeld in de paginacomponent (*niet* in de sjabloon):

1. Met CRXDE Lite (of een gelijkwaardige methode) opent u de pagina-component.

   Bijvoorbeeld: `/apps/core/wcm/components/page/v1/page`

   >[!NOTE]
   >
   >Dit voorbeeld veronderstelt dat de Componenten van de Kern op de instantie geïnstalleerd zijn, wat het geval is als de instantie met Wij.Retail steekproefinhoud loopt. Raadpleeg de documentatie bij [](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/introduction.html) Core Components voor meer informatie.

1. Navigeer naar het vereiste veld binnen de `cq:dialog` definitie.
1. Definieer de volgende eigenschap op het veldknooppunt:

   * **Naam**: `allowBulkEdit`
   * **Type**: `Boolean`
   * **Waarde**: `true`

   Bijvoorbeeld voor de standaard pagina [stichting component](/help/sites-authoring/default-components-foundation.md):

   `/libs/foundation/components/page`

   De eigenschap wordt gedefinieerd op:

   `cq:dialog/content/items/tabs/items/basic/items/column/items/onofftime/items/ondate`

   >[!CAUTION]
   >
   >U ***mag*** niets in het `/libs` pad wijzigen.
   >
   >De reden hiervoor is dat de inhoud van `/libs` de volgende keer dat u een upgrade uitvoert van uw exemplaar, wordt overschreven (en dat deze inhoud ook kan worden overschreven wanneer u een hotfix- of functiepakket toepast).
   >
   >De aanbevolen methode voor configuratie en andere wijzigingen is:
   >
   >    1. Het vereiste item opnieuw maken (d.w.z. zoals het in `/libs`) `/apps`
   >    1. Breng wijzigingen aan in `/apps`


1. Selecteer Alles **** opslaan om uw updates voort te zetten.

