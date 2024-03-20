---
title: Bewerkbare sjablonen uitproberen in We.Detailhandel
description: Leer hoe u bewerkbare sjablonen kunt uitproberen in Adobe Experience Manager met We.Retail.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: efebe66d-3d30-4033-9c4c-ae347e134f2f
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# Bewerkbare sjablonen uitproberen in We.Detailhandel{#trying-out-editable-templates-in-we-retail}

Met de bewerkbare sjablonen is het maken en onderhouden van sjablonen niet langer alleen een taak voor ontwikkelaars. Een type van macht-gebruiker, die een malplaatjeauteur wordt genoemd, kan malplaatjes nu tot stand brengen. Ontwikkelaars moeten de omgeving nog steeds instellen, clientbibliotheken maken en de componenten maken die moeten worden gebruikt, maar als deze basisbeginselen eenmaal zijn ingesteld, beschikt de sjabloonauteur over de flexibiliteit om sjablonen zonder ontwikkelingsproject te maken en te configureren.

Alle pagina&#39;s in We.Retail zijn gebaseerd op bewerkbare sjablonen, waardoor niet-ontwikkelaars de sjablonen kunnen aanpassen en aanpassen.

## Uitproberen {#trying-it-out}

1. Bewerk de pagina Apparatuur van de taalstramienvertakking.

   http://localhost:4502/editor.html/content/we-retail/language-masters/en/equipment.html

1. De moduskiezer beschikt niet meer over een ontwerpmodus. Alle pagina&#39;s voor We.Retail zijn gebaseerd op bewerkbare sjablonen en om het ontwerp van bewerkbare sjablonen te wijzigen, moeten deze worden bewerkt in de sjablooneditor.
1. Van de **Pagina-informatie** menu selecteren **Sjabloon bewerken**.
1. U bewerkt nu de sjabloon voor de hoofdpagina.

   In de structuurmodus van de pagina kunt u de structuur van de sjabloon wijzigen. Dit geldt bijvoorbeeld voor de componenten die zijn toegestaan in de lay-outcontainer.

   ![chlimage_1-138](assets/chlimage_1-138.png)

1. Configureer het beleid voor de container van de layout om te definiëren welke componenten zijn toegestaan in de container.

   Het beleid is het equivalent van ontwerpconfiguraties.

   ![chlimage_1-139](assets/chlimage_1-139.png)

1. In het dialoogvenster Ontwerp van de container voor lay-outs kunt u

   * Een bestaand beleid selecteren of een beleid voor de container maken
   * Selecteer welke componenten zijn toegestaan in de container
   * De standaardcomponenten definiëren die moeten worden geplaatst wanneer een element naar de container wordt gesleept

   ![chlimage_1-140](assets/chlimage_1-140.png)

1. In de sjablooneditor kunt u het beleid van de tekstcomponent in de lay-outcontainer bewerken.

   Hiermee kunt u:

   * Een bestaand beleid selecteren of een beleid voor de container maken
   * Definieer de functies die beschikbaar zijn voor de auteur van de pagina wanneer u deze component gebruikt, zoals

      * Toegestane bronnen voor plakken
      * Opmaakopties
      * Alineastijlen toegestaan
      * Speciale tekens toegestaan

   Vele componenten die op de kerncomponenten worden gebaseerd staan de configuratie van opties op componentenniveau door de editable malplaatjes toe, die de behoefte aan aanpassing door ontwikkelaars verwijderen.

   ![chlimage_1-141](assets/chlimage_1-141.png)

1. In de sjablooneditor kunt u de moduskiezer gebruiken om over te schakelen op **Oorspronkelijke inhoud** om te bepalen welke inhoud op de pagina wordt vereist.

   **Layout** Deze modus kan worden gebruikt zoals deze zich op een normale pagina bevindt om de indeling voor de sjabloon te definiëren.

## Meer informatie {#more-information}

Zie het ontwerpdocument voor meer informatie [Paginasjablonen maken](/help/sites-authoring/templates.md) of de pagina voor ontwikkelaarsdocumenten [Sjablonen - Bewerkbaar](/help/sites-developing/page-templates-editable.md) voor volledige technische details over bewerkbare sjablonen.

Misschien wilt u ook een onderzoek instellen [kerncomponenten](/help/sites-developing/we-retail-core-components.md). Zie het ontwerpdocument [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) voor een overzicht van de mogelijkheden van de kerncomponenten en het ontwikkelaarsdocument [Basiscomponenten ontwikkelen](https://helpx.adobe.com/experience-manager/core-components/using/developing.html) voor een technisch overzicht.
