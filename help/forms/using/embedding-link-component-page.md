---
title: Koppelingscomponent insluiten in een pagina
description: U kunt de koppelingscomponent gebruiken om een adaptief document of een adaptief formulier van een willekeurige pagina te koppelen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
docset: aem65
exl-id: eb45adf2-d0f3-4de6-92ac-fb146953e989
solution: Experience Manager, Experience Manager Forms
feature: Forms Portal
role: Admin, User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# Koppelingscomponent insluiten in een pagina{#embedding-link-component-in-a-page}

## Vereisten {#prerequisites}

De koppelingscomponent is een lid van de categorie Document Services. Zorg ervoor dat de categorie Document Services zichtbaar is in de browser met AEM componenten. Als de categorie niet vermeld is, volg de stappen die bij [ worden vermeld toelatend vormen portalcomponenten ](/help/forms/using/enabling-forms-portal-components.md).

## Component koppelen {#link-component}

Met de component Koppeling kunnen auteurs van formulierportaalpagina&#39;s vanaf elke locatie op een pagina een koppeling naar een adaptief formulier maken. De component Link is beschikbaar in de sectie Document Services in de componentbrowser.

Voer de volgende stappen uit om een component van de Verbinding aan de pagina toe te voegen:

1. Sleep de **component van de Verbinding** op de pagina. Selecteer de component en selecteer ![ cmp ](assets/cmppr.png). Het dialoogvenster Koppelingscomponent bewerken wordt geopend.

   ![ uitgeven-verbinding-component ](assets/edit-link-component.png)

1. In het **lusje van de Vertoning**, specificeer het volgende:

   * **Bijschrift van de Verbinding**: De tekst of de titel van de verbinding voor de verbinding.
   * **Tooltip van de Verbinding**: Knopinfo voor de verbinding.
   * **Malplaatje van de Lay-out**: Malplaatje voor de lay-out van de component van de Verbinding.

1. Open het **lusje van Info van Activa** en specificeer het type van de activa. Een activa kan a **vorm** zijn. Afhankelijk van het geselecteerde type element worden de onderstaande opties weergegeven:

   * **Weg van Activa**: De weg van de Bewaarplaats waar het element wordt opgeslagen.

   * **geeft Type** terug: Teruggeven formaat-PDF, HTML, of Auto. Met het rendertype Automatisch wordt de gebruikersomgeving gedetecteerd en wordt het formulier dienovereenkomstig weergegeven als HTML of als PDF. Als het formulier bijvoorbeeld wordt geopend vanaf een mobiel apparaat, geeft het rendertype Automatisch het formulier weer in HTML.
   * **legt URL voor:** URL aan servlet waar de vormgegevens worden voorgelegd.
   * **Profiel van HTML**: Profiel voor het teruggeven van de vorm als HTML.
   * **Profiel van PDF**: Profiel voor het teruggeven van de vorm als document van PDF.

1. Open het **Geavanceerde** lusje. U kunt de extra parameters in het sleutel-waarde paarformaat specificeren. Wanneer op de koppeling wordt geklikt, worden deze aanvullende parameters doorgegeven en samen met het formulier doorgegeven.

   Selecteer **Gedaan** om de configuratie te bewaren.

## Aanbevolen procedures voor het gebruik van de component Koppeling {#best-practices-for-using-link-component-br}

* Zorg ervoor dat u PDF selecteert als het rendertype als het pad dat is opgegeven in Formulierpad, verwijst naar een document met de toegestane renderindeling PDF als.
* De verzendURL voor een formulier kan op verschillende plaatsen worden opgegeven en de prioriteitsvolgorde is als volgt:

   1. Verzenden van URL die is ingesloten in het formulier (in verzendknop) heeft de hoogste prioriteit.
   1. De verzendURL die in Forms Manager wordt vermeld, heeft de middelhoge prioriteit.
   1. De laagste prioriteit voor het verzenden van een URL die in het formulierportaal wordt vermeld.
