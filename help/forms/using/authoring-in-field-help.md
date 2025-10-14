---
title: Contextassistentie voor het ontwerpen van formuliervelden
description: Met AEM Forms kunt u in de context Help toevoegen om formuliervelden en deelvensters als tekst of rich media, inclusief video's, aan te passen.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
docset: aem65
feature: Adaptive Forms,Foundation Components
exl-id: 6569bfba-9af5-4060-8640-e51d7af46614
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# Contextassistentie voor het ontwerpen van formuliervelden{#authoring-in-context-help-for-form-fields}

<span class="preview"> de Adobe adviseert gebruikend de moderne en verlengbare gegevens vangen [&#x200B; Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=nl-NL) voor [&#x200B; het creëren van nieuwe Aangepaste Forms &#x200B;](/help/forms/using/create-an-adaptive-form-core-components.md) of [&#x200B; het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites &#x200B;](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

## Inleiding {#introduction}

In bepaalde situaties weten eindgebruikers die een formulier invullen niet zeker hoe ze details in een bepaald formulierveld moeten invullen. Om dergelijke problemen te verhelpen, bieden adaptieve formulieren ondersteuning voor het toevoegen van tekst of rich in-context Help aan een formulierveld. Hiermee verbetert u de ervaring bij het invullen van formulieren en voorkomt u dubbelzinnigheid voor eindgebruikers.

In dit artikel wordt besproken hoe formulierauteurs in-context Help kunnen toevoegen tijdens het ontwerpen van Adaptive Forms.

## In-context-Help toevoegen {#add-in-context-help}

U kunt in-context hulp specificeren gebruikend de volgende opties in de sectie van de Inhoud van de Hulp van het eigenschappen lusje in sidebar.

* [Korte beschrijving](../../forms/using/authoring-in-field-help.md#p-short-description-p)
* [Lange beschrijving](../../forms/using/authoring-in-field-help.md#p-long-description-p)

![&#x200B; In-context hulp voor vormgebieden &#x200B;](assets/descriptions.png)

>[!NOTE]
>
>Lange beschrijving heeft voorrang op de korte beschrijving. Als u beide hebt opgegeven, wordt alleen de beschrijving Lang weergegeven.

### Korte beschrijving {#short-description}

In het veld Korte beschrijving kunt u snelle en korte aanwijzingen geven over het invullen van een formulierveld. De tekst die in het veld Korte beschrijving is opgegeven, wordt als knopinfo weergegeven wanneer u de muis boven het veld houdt.

![&#x200B; Korte beschrijving voor het toevoegen van in-context hulp voor vormgebieden &#x200B;](assets/tooltip.png)

>[!NOTE]
>
>Selecteer **altijd tonen korte beschrijving** om de hulptekst onder het gebied permanent te tonen.

![&#x200B; Permanente korte in-context hulp onder het gebied &#x200B;](assets/short1.png)

### Lange beschrijving {#long-description}

U kunt het lange beschrijvingsgebied gebruiken om lange teksten te specificeren of rijke media inhoud, met inbegrip van video&#39;s in te bedden, als in-context hulp. In de volgende afbeelding ziet u bijvoorbeeld hoe u een video kunt insluiten als in-context-Help.

![&#x200B; Toevoegend rijke media als in-context hulp voor vormgebieden &#x200B;](assets/long-descriptions.png)

Als u een lange beschrijving toevoegt, wordt een **weergegeven?** naast het veld. Als u op het pictogram klikt, wordt de inhoud weergegeven die is toegevoegd in de lange beschrijving.

![&#x200B; Voorbeeld van rijke media in-context hulp &#x200B;](assets/photoshop.png)

### Help op deelvensterniveau {#panel-level-help}

Naast de contextHelp voor formuliervelden kunt u op deelvensterniveau Help opgeven op het tabblad Help-inhoud van het dialoogvenster Bewerken van het deelvenster.

![&#x200B; Toevoegend in-context hulp voor een vormpaneel &#x200B;](assets/panel-level-help.png)

Wanneer u Help voor het deelvenster toevoegt, wordt een **weergegeven?** naast de beschrijving van het deelvenster. Als u op het pictogram klikt, wordt de inhoud weergegeven die is toegevoegd in de sectie Help-inhoud van het dialoogvenster voor het bewerken van deelvensters.

![&#x200B; Voorbeeld van in-context hulp op het niveau van het vormpaneel &#x200B;](assets/photoshop-1.png)
