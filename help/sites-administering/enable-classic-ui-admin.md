---
title: Admin Consoles
description: Leer hoe u de Admin Consoles gebruikt die beschikbaar zijn in Adobe Experience Manager.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
docset: aem65
exl-id: d4de517e-50bc-4ca5-89b1-295d259fd5bb
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---


# Admin Consoles{#admin-consoles}

De mogelijkheid om via de beheerconsoles over te schakelen op de klassieke interface is standaard uitgeschakeld. Daarom worden de pop-uppictogrammen die werden gezien toen de muis over bepaalde consolepictogrammen beweegt, die toegang tot klassieke UI toestaan, niet meer getoond.

Elke console die een Klassieke versie UI in heeft `/libs/cq/core/content/nav` kan individueel opnieuw worden toegelaten zodat **Klassieke interface** Deze optie wordt weer boven het consolepictogram weergegeven wanneer de muis erboven wordt geplaatst.

In dit voorbeeld, bent u re-toelatend Klassieke UI voor de console van Plaatsen.

1. Gebruikend CRXDE Lite, vind de knoop die aan de Admin Console beantwoordt waarvoor u Klassieke UI wilt re-toelaten. Deze zijn te vinden onder:

   `/libs/cq/core/content/nav`

   Bijvoorbeeld

   [`https://localhost:4502/crx/de/index.jsp#/libs/cq/core/content/nav`](https://localhost:4502/crx/de/index.jsp#/libs/cq/core/content/nav)

1. Selecteer de knoop die aan de console beantwoordt waarvoor u Klassieke UI wilt re-toelaten. In dit voorbeeld schakelt u de klassieke UI voor de Sites-console opnieuw in.

   `/libs/cq/core/content/nav/sites`

1. Een overlay maken met de opdracht **Overlayknooppunt** optie; bijvoorbeeld:

   * **Pad**: `/apps/cq/core/content/nav/sites`
   * **Overlay-locatie**: `/apps/`
   * **Identieke knooppunttypen**: actief (schakel het selectievakje in)

1. Voeg de volgende booleaanse eigenschap toe aan het bovenliggende knooppunt:

   `enableDesktopOnly = {Boolean}true`

1. De **Klassieke interface** Deze optie is weer beschikbaar als een popover-optie in de Admin Console.

   ![Klassieke UI-popover, optie](assets/syui-01-2019-02-27-15-16-55.png)

Herhaal deze stappen voor elke console waarvoor u toegang tot de Klassieke versie van UI wenst opnieuw toe te laten.
