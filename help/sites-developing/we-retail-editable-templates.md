---
title: Bewerkbare sjablonen uitproberen in We.Detailhandel
seo-title: Bewerkbare sjablonen uitproberen in We.Detailhandel
description: 'null'
seo-description: 'null'
uuid: 0d4b97cb-efcc-4312-a783-eae3ecd6f889
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 3cc8ac23-98ff-449f-bd76-1203c7cbbed7
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 10%

---


# Bewerkbare sjablonen uitproberen in We.Retail{#trying-out-editable-templates-in-we-retail}

Met de bewerkbare sjablonen is het maken en onderhouden van sjablonen niet langer alleen een taak voor ontwikkelaars. Een type van macht-gebruiker, die een malplaatjeauteur wordt genoemd, kan malplaatjes nu tot stand brengen. Ontwikkelaars zijn nog steeds nodig om de omgeving in te stellen, clientbibliotheken te maken en de te gebruiken componenten te maken, maar zodra deze basisbeginselen zijn ingesteld, kan de maker van sjablonen sjablonen maken en configureren zonder een ontwikkelingsproject.

Alle pagina&#39;s in We.Retail zijn gebaseerd op bewerkbare sjablonen, waardoor niet-ontwikkelaars de sjablonen kunnen aanpassen en aanpassen.

## Uitproberen {#trying-it-out}

1. Bewerk de pagina Apparatuur van de master taalvertakking.

   http://localhost:4502/editor.html/content/we-retail/language-masters/en/equipment.html

1. De moduskiezer biedt niet langer een ontwerpmodus. Alle pagina&#39;s voor We.Retail zijn gebaseerd op bewerkbare sjablonen en om het ontwerp van bewerkbare sjablonen te wijzigen, moeten deze worden bewerkt in de sjablooneditor.
1. Selecteer **Sjabloon bewerken** in het menu **Pagina-informatie**.
1. U bewerkt nu de sjabloon voor de hoofdpagina.

   In de structuurmodus van de pagina kunt u de structuur van de sjabloon wijzigen. Dit geldt bijvoorbeeld voor de componenten die zijn toegestaan in de lay-outcontainer.

   ![chlimage_1-138](assets/chlimage_1-138.png)

1. Configureer het beleid voor de container van de layout om te definiëren welke componenten zijn toegestaan in de container.

   Het beleid is het equivalent van ontwerpconfiguraties.

   ![chlimage_1-139](assets/chlimage_1-139.png)

1. In het dialoogvenster Ontwerp van de container voor lay-outs kunt u

   * Een bestaand beleid selecteren of een nieuw beleid voor de container maken
   * Selecteer welke componenten zijn toegestaan in de container
   * De standaardcomponenten definiëren die moeten worden geplaatst wanneer een element naar de container wordt gesleept

   ![chlimage_1-140](assets/chlimage_1-140.png)

1. In de sjablooneditor kunt u het beleid van de tekstcomponent in de lay-outcontainer bewerken.

   Zo kunt u:

   * Een bestaand beleid selecteren of een nieuw beleid voor de container maken
   * Definieer de functies die beschikbaar zijn voor de auteur van de pagina wanneer u deze component gebruikt, zoals

      * Toegestane bronnen voor plakken
      * Opmaakopties
      * Toegestane alineastijlen
      * Speciale tekens toegestaan

   Vele componenten die op de kerncomponenten worden gebaseerd staan de configuratie van opties op componentenniveau door de editable malplaatjes toe, die de behoefte aan aanpassing door ontwikkelaars verwijderen.

   ![chlimage_1-141](assets/chlimage_1-141.png)

1. In de sjablooneditor kunt u de moduskiezer gebruiken om de modus **Oorspronkelijke inhoud** te wijzigen en te definiëren welke inhoud op de pagina is vereist.

   **De** layoutmodus kan worden gebruikt zoals deze zich op een normale pagina bevindt om de lay-out voor de sjabloon te definiëren.

## Meer informatie {#more-information}

Raadpleeg voor meer informatie het ontwerpdocument [Paginasjablonen maken](/help/sites-authoring/templates.md) of het document voor ontwikkelaars Pagina [Sjablonen - Bewerkbaar](/help/sites-developing/page-templates-editable.md) voor volledige technische details over bewerkbare sjablonen.

U kunt ook [kerncomponenten](/help/sites-developing/we-retail-core-components.md) willen onderzoeken. Zie het ontwerpdocument [Core Components](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/introduction.html) voor een overzicht van de mogelijkheden van de kerncomponenten en het document [Developer Core Components](https://helpx.adobe.com/experience-manager/core-components/using/developing.html) voor een technisch overzicht.

