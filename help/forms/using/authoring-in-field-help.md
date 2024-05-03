---
title: Contextassistentie voor het ontwerpen van formuliervelden
description: Met AEM Forms kunt u in de context Help toevoegen om formuliervelden en deelvensters als tekst of rich media, inclusief video's, aan te passen.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
docset: aem65
feature: Adaptive Forms, Foundation Components
exl-id: 6569bfba-9af5-4060-8640-e51d7af46614
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# Contextassistentie voor het ontwerpen van formuliervelden{#authoring-in-context-help-for-form-fields}

<span class="preview"> Adobe beveelt aan moderne en uitbreidbare gegevensvastlegging te gebruiken [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) for [nieuwe Adaptieve Forms maken](/help/forms/using/create-an-adaptive-form-core-components.md) of [Aangepaste Forms toevoegen aan AEM Sites-pagina&#39;s](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

## Inleiding {#introduction}

In bepaalde situaties weten eindgebruikers die een formulier invullen niet zeker hoe ze details in een bepaald formulierveld moeten invullen. Om dergelijke problemen te verhelpen, bieden adaptieve formulieren ondersteuning voor het toevoegen van tekst of rich in-context Help aan een formulierveld. Hiermee verbetert u de ervaring bij het invullen van formulieren en voorkomt u dubbelzinnigheid voor eindgebruikers.

In dit artikel wordt besproken hoe formulierauteurs in-context Help kunnen toevoegen tijdens het ontwerpen van Adaptive Forms.

## In-context-Help toevoegen {#add-in-context-help}

U kunt in-context hulp specificeren gebruikend de volgende opties in de sectie van de Inhoud van de Hulp van het eigenschappen lusje in sidebar.

* [Korte beschrijving](../../forms/using/authoring-in-field-help.md#p-short-description-p)
* [Lange beschrijving](../../forms/using/authoring-in-field-help.md#p-long-description-p)

![In-context Help voor formuliervelden](assets/descriptions.png)

>[!NOTE]
>
>Lange beschrijving heeft voorrang op de korte beschrijving. Als u beide hebt opgegeven, wordt alleen de beschrijving Lang weergegeven.

### Korte beschrijving {#short-description}

In het veld Korte beschrijving kunt u snelle en korte aanwijzingen geven over het invullen van een formulierveld. De tekst die in het veld Korte beschrijving is opgegeven, wordt als knopinfo weergegeven wanneer u de muis boven het veld houdt.

![Korte beschrijving voor het toevoegen van hulp in context voor formuliervelden](assets/tooltip.png)

>[!NOTE]
>
>Selecteren **Altijd korte beschrijving tonen** om de Help-tekst permanent onder het veld weer te geven.

![Permanente korte hulp in de context onder het veld](assets/short1.png)

### Lange beschrijving {#long-description}

U kunt het lange beschrijvingsgebied gebruiken om lange teksten te specificeren of rijke media inhoud, met inbegrip van video&#39;s in te bedden, als in-context hulp. In de volgende afbeelding ziet u bijvoorbeeld hoe u een video kunt insluiten als in-context-Help.

![Veelzijdige media toevoegen als in-context Help voor formuliervelden](assets/long-descriptions.png)

Een lange beschrijving wordt weergegeven als **?** naast het veld. Als u op het pictogram klikt, wordt de inhoud weergegeven die is toegevoegd in de lange beschrijving.

![Voorbeeld van uitgebreide media in-context-Help](assets/photoshop.png)

### Help op deelvensterniveau {#panel-level-help}

Naast de contextHelp voor formuliervelden kunt u op deelvensterniveau Help opgeven op het tabblad Help-inhoud van het dialoogvenster Bewerken van het deelvenster.

![In-context-Help toevoegen voor een formuliervenster](assets/panel-level-help.png)

Wanneer u Help voor een deelvenster toevoegt, wordt een **?** naast de beschrijving van het deelvenster. Als u op het pictogram klikt, wordt de inhoud weergegeven die is toegevoegd in de sectie Help-inhoud van het dialoogvenster voor het bewerken van deelvensters.

![Voorbeeld van in-context Help op het niveau van het formulierdeelvenster](assets/photoshop-1.png)
