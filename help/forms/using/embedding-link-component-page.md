---
title: Koppelingscomponent insluiten in een pagina
seo-title: Koppelingscomponent insluiten in een pagina
description: U kunt de koppelingscomponent gebruiken om een adaptief document of een adaptief formulier van een willekeurige pagina te koppelen.
seo-description: U kunt de koppelingscomponent gebruiken om een adaptief document of een adaptief formulier van een willekeurige pagina te koppelen.
uuid: 22f488fc-bb1a-40aa-a5f4-6d04d7250f29
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
discoiquuid: 9d63152d-41ca-4c7c-bb20-af16c7bdec13
docset: aem65
translation-type: tm+mt
source-git-commit: f9ed171c188a4dfb71f12ae9c98105a4c1895542

---


# Koppelingscomponent insluiten in een pagina{#embedding-link-component-in-a-page}

## Vereisten {#prerequisites}

De koppelingscomponent is een lid van de categorie Document Services. Zorg ervoor dat de categorie Document Services zichtbaar is in de browser met AEM-componenten. Als de categorie niet wordt vermeld, voert u de stappen uit die worden weergegeven bij [Inschakelen van componenten](/help/forms/using/enabling-forms-portal-components.md)van de portal Formulieren.

## Component koppelen {#link-component}

Met de component Koppeling kunnen auteurs van formulierportaalpagina&#39;s vanaf elke locatie op een pagina een koppeling naar een adaptief formulier maken. De component van de Verbinding is beschikbaar in de sectie van de Diensten van het Document in componentenbrowser.

Voer de volgende stappen uit om een component van de Verbinding aan de pagina toe te voegen:

1. Sleep de component **Koppeling** naar de pagina. Selecteer de component en tik op ![cmp](assets/cmppr.png). Het dialoogvenster Koppelingscomponent bewerken wordt geopend.

   ![edit-link-component](assets/edit-link-component.png)

1. Geef op het tabblad **Weergave** het volgende op:

   * **Bijschrift** koppeling: Tekst of bijschrift voor de koppeling koppelen.
   * **Knopinfo** koppeling: Knopinfo voor de koppeling.
   * **Lay-outsjabloon**: Sjabloon voor de lay-out van de component Koppeling.

1. Open het tabblad **Elementinfo** en geef het type element op. Een element kan een **formulier** zijn. Afhankelijk van het geselecteerde type element worden de onderstaande opties weergegeven:

   * **Middelenpad**: Pad naar opslagplaats waar het element is opgeslagen.

   * **Type** rendering: De renderindeling: PDF, HTML of Automatisch. Met het rendertype Automatisch wordt de gebruikersomgeving gedetecteerd en wordt het formulier dienovereenkomstig weergegeven als HTML of als PDF. Als het formulier bijvoorbeeld wordt geopend vanaf een mobiel apparaat, geeft het rendertype Automatisch het formulier weer in HTML.
   * **** URL verzenden:  URL aan servlet waar de vormgegevens worden voorgelegd.
   * **HTML-profiel**: Profiel voor weergave van het formulier als HTML.
   * **PDF-profiel**: Profiel voor weergave van het formulier als PDF-document.

1. Open het tabblad **Geavanceerd** . U kunt de extra parameters in het sleutel-waarde paarformaat specificeren. Wanneer op de koppeling wordt geklikt, worden deze aanvullende parameters doorgegeven en samen met het formulier doorgegeven.

   Tik op **Gereed** om de configuratie op te slaan.

## Aanbevolen procedures voor het gebruik van de component Koppeling {#best-practices-for-using-link-component-br}

* Selecteer PDF als het rendertype als het pad dat in Formulierpad is opgegeven, verwijst naar een document met PDF als de toegestane renderindeling.
* De verzendURL voor een formulier kan op verschillende plaatsen worden opgegeven en de prioriteitsvolgorde is als volgt:

   1. Verzenden van URL die is ingesloten in het formulier (in verzendknop) heeft de hoogste prioriteit.
   1. De verzendURL die in Forms Manager wordt vermeld, heeft de middelhoge prioriteit.
   1. De laagste prioriteit voor het verzenden van een URL die in het formulierportaal wordt vermeld.
