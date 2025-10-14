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
feature: Administering
role: Admin
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---


# Admin Consoles{#admin-consoles}

De mogelijkheid om via de beheerconsoles over te schakelen op de klassieke interface is standaard uitgeschakeld. Daarom worden de pop-uppictogrammen die werden gezien toen de muis over bepaalde consolepictogrammen beweegt, die toegang tot klassieke UI toestaan, niet meer getoond.

Elke console die een Klassieke versie UI in `/libs/cq/core/content/nav` heeft kan individueel worden re-toegelaten zodat de **Klassieke UI** optie opnieuw over het consolepictogram verschijnt wanneer het over wordt verspreid.

In dit voorbeeld, bent u re-toelatend Klassieke UI voor de console van Plaatsen.

1. Gebruikend CRXDE Lite, vind de knoop die aan de Admin Console beantwoordt waarvoor u Klassieke UI wilt re-toelaten. Deze zijn te vinden onder:

   `/libs/cq/core/content/nav`

   Bijvoorbeeld

   [`https://localhost:4502/crx/de/index.jsp#/libs/cq/core/content/nav`](https://localhost:4502/crx/de/index.jsp#/libs/cq/core/content/nav)

1. Selecteer de knoop die aan de console beantwoordt waarvoor u Klassieke UI wilt re-toelaten. In dit voorbeeld schakelt u de klassieke UI voor de Sites-console opnieuw in.

   `/libs/cq/core/content/nav/sites`

1. Creeer een bedekking gebruikend de **optie van de Knoop van de Bedekking**; bijvoorbeeld:

   * **Weg**: `/apps/cq/core/content/nav/sites`
   * **Plaats van de Bedekking**: `/apps/`
   * **de Types van Knoop van de Gelijke**: actief (selecteer checkbox)

1. Voeg de volgende booleaanse eigenschap toe aan het bovenliggende knooppunt:

   `enableDesktopOnly = {Boolean}true`

1. De **Klassieke UI** optie is opnieuw beschikbaar als popover optie in de Admin Console.

   ![&#x200B; klassieke UI popover optie &#x200B;](assets/syui-01-2019-02-27-15-16-55.png)

Herhaal deze stappen voor elke console waarvoor u toegang tot de Klassieke versie van UI wenst opnieuw toe te laten.
