---
title: Pagina configureren voor Bulk bewerken van pagina-eigenschappen
description: Met de functie Pagina-eigenschappen bewerken kunt u de eigenschappen van meerdere pagina's tegelijk bewerken
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
exl-id: 1787e643-fc8e-40e0-8e14-97b222a7c320
solution: Experience Manager, Experience Manager Sites
feature: Administering
role: Developer
source-git-commit: eae057caed533ef16bb541b4ad41b8edd7aaa1c7
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# Pagina configureren voor Bulk bewerken van pagina-eigenschappen {#configuring-your-page-for-bulk-editing-of-page-properties}

[ Bulk het uitgeven van paginaeigenschappen ](/help/sites-authoring/editing-page-properties.md#from-the-sites-console-multiple-pages) laat u de eigenschappen van veelvoudige pagina&#39;s in één keer uitgeven.

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
>Bulkbewerking is ook beschikbaar voor Assets. Het is erg vergelijkbaar, maar op een paar punten verschilt het. Zie [ het Uitgeven Eigenschappen van Veelvoudige Assets ](/help/assets/metadata.md) voor volledige informatie. U kunt de gebieden in de Bulk redacteur van Meta-gegevens voor Assets aanpassen gebruikend de [ redacteur van het Schema ](/help/assets/metadata-schemas.md).

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

De gebieden worden toegelaten op de paginacomponent (*niet* op het malplaatje):

1. Met CRXDE Lite (of een gelijkwaardige methode) opent u de pagina-component.

   Bijvoorbeeld: `/apps/core/wcm/components/page/v1/page`

   >[!NOTE]
   >
   >Dit voorbeeld veronderstelt dat de Componenten van de Kern op de instantie geïnstalleerd zijn, wat het geval is als de instantie met Wij.Retail steekproefinhoud loopt. Zie de [ documentatie van de Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) voor meer informatie.

1. Navigeer naar het vereiste veld binnen de definitie van `cq:dialog` .
1. Definieer de volgende eigenschap op het veldknooppunt:

   * **Naam**: `allowBulkEdit`
   * **Type**: `Boolean`
   * **Waarde**: `true`

   Bijvoorbeeld, voor de standaardpagina [ stichtingscomponent ](/help/sites-authoring/default-components-foundation.md):

   `/libs/foundation/components/page`

   De eigenschap wordt gedefinieerd op:

   `cq:dialog/content/items/tabs/items/basic/items/column/items/onofftime/items/ondate`

   >[!CAUTION]
   >
   >U ***moet*** niets in de `/libs` weg veranderen.
   >
   >De reden hiervoor is dat de inhoud van `/libs` de volgende keer dat u een upgrade uitvoert van de instantie wordt overschreven (en dat deze inhoud ook kan worden overschreven wanneer u een hotfix- of functiepakket toepast).
   >
   >De aanbevolen methode voor configuratie en andere wijzigingen is:
   >
   >    1. Het vereiste item opnieuw maken (dat wil zeggen, zoals het in `/libs` staat) onder `/apps`
   >    1. Breng eventuele wijzigingen aan binnen `/apps`

1. Selecteer **sparen allen** om uw updates voort te zetten.
