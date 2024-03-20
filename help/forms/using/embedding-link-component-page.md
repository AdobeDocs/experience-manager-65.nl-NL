---
title: Koppelingscomponent insluiten in een pagina
description: U kunt de koppelingscomponent gebruiken om een adaptief document of een adaptief formulier van een willekeurige pagina te koppelen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
docset: aem65
exl-id: eb45adf2-d0f3-4de6-92ac-fb146953e989
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# Koppelingscomponent insluiten in een pagina{#embedding-link-component-in-a-page}

## Vereisten {#prerequisites}

De koppelingscomponent is een lid van de categorie Document Services. Zorg ervoor dat de categorie Document Services zichtbaar is in de browser met AEM componenten. Als de categorie niet wordt vermeld, voert u de stappen uit die worden weergegeven op [portalcomponenten voor formulieren inschakelen](/help/forms/using/enabling-forms-portal-components.md).

## Component koppelen {#link-component}

Met de component Koppeling kunnen auteurs van formulierportaalpagina&#39;s vanaf elke locatie op een pagina een koppeling naar een adaptief formulier maken. De component Link is beschikbaar in de sectie Document Services in de componentbrowser.

Voer de volgende stappen uit om een component van de Verbinding aan de pagina toe te voegen:

1. Sleep de **Koppeling** op de pagina. Selecteer de component en selecteer ![cmppr](assets/cmppr.png). Het dialoogvenster Koppelingscomponent bewerken wordt geopend.

   ![edit-link-component](assets/edit-link-component.png)

1. In de **Weergave** kunt u het volgende opgeven:

   * **Bijschrift koppelen**: Koppel tekst of bijschrift voor de koppeling.
   * **Knopinfo koppeling**: Knopinfo voor de koppeling.
   * **Lay-outsjabloon**: Sjabloon voor de lay-out van de component Koppeling.

1. Open de **Elementinfo** en geeft u het type element op. Een element kan een **formulier**. Afhankelijk van het geselecteerde type element worden de onderstaande opties weergegeven:

   * **Middelpad**: Pad naar opslagplaats waar het element is opgeslagen.

   * **Rendertype**: De renderindeling—PDF, HTML of Automatisch. Met het rendertype Automatisch wordt de gebruikersomgeving gedetecteerd en wordt het formulier dienovereenkomstig weergegeven als HTML of als PDF. Als het formulier bijvoorbeeld wordt geopend vanaf een mobiel apparaat, geeft het rendertype Automatisch het formulier weer in HTML.
   * **URL verzenden:**  URL aan servlet waar de vormgegevens worden voorgelegd.
   * **HTML-profiel**: Profiel voor het weergeven van het formulier als HTML.
   * **PDF-profiel**: Profiel voor het weergeven van het formulier als PDF-document.

1. Open de **Geavanceerd** tab. U kunt de extra parameters in het sleutel-waarde paarformaat specificeren. Wanneer op de koppeling wordt geklikt, worden deze aanvullende parameters doorgegeven en samen met het formulier doorgegeven.

   Selecteren **Gereed** om de configuratie op te slaan.

## Aanbevolen procedures voor het gebruik van de component Koppeling {#best-practices-for-using-link-component-br}

* Zorg ervoor dat u PDF selecteert als het rendertype als het pad dat is opgegeven in Formulierpad, verwijst naar een document met de toegestane renderindeling PDF als.
* De verzendURL voor een formulier kan op verschillende plaatsen worden opgegeven en de prioriteitsvolgorde is als volgt:

   1. Verzenden van URL die is ingesloten in het formulier (in verzendknop) heeft de hoogste prioriteit.
   1. De verzendURL die in Forms Manager wordt vermeld, heeft de middelhoge prioriteit.
   1. De laagste prioriteit voor het verzenden van een URL die in het formulierportaal wordt vermeld.
