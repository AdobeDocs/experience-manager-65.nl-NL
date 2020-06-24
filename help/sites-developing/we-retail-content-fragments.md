---
title: Inhoudsfragmenten in We.Retail uitproberen
seo-title: Inhoudsfragmenten in We.Retail uitproberen
description: 'null'
seo-description: 'null'
uuid: 66daddfe-8e98-47b6-8499-db055887ac17
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: d1326737-f378-46d0-9916-61ead4d31639
translation-type: tm+mt
source-git-commit: 759d2dd8d12861757bf7f54b77d8d3ca170887fe
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 4%

---


# Inhoudsfragmenten in We.Retail uitproberen{#trying-out-content-fragments-in-we-retail}

Met inhoudsfragmenten kunt u kanaalneutrale inhoud maken, samen met (mogelijk kanaalspecifieke) variaties. **Wij.Retail** (zoals beschikbaar in een out-of-the-box instantie van AEM) verstrekt het fragment **Arctic Surfing in Lofoten** als basisvoorbeeld. Hieruit blijkt dat:

* Inhoudsfragmenten van Adobe Experience Manager (AEM) worden [gemaakt en beheerd als paginaonafhankelijke assets](/help/assets/content-fragments/content-fragments.md). U kunt hiermee kanaalneutrale inhoud maken, samen met (mogelijk kanaalspecifieke) variaties.

   * Zie [Waar vindt u de elementen van Content Fragment in We.Retail](#where-to-find-content-fragments-in-we-retail)

* Vervolgens kunt u deze fragmenten en de variaties ervan [gebruiken bij het ontwerpen](/help/sites-authoring/content-fragments.md) van de inhoudspagina&#39;s.

   * Zie [waar de Fragmenten van de Inhoud in Wij.Retail worden gebruikt](#where-content-fragments-are-used-in-we-retail)

Voor de volledige documentatie over het maken, beheren, gebruiken en ontwikkelen van inhoudsfragmenten:

* Zie [Aanvullende informatie](#further-information)

>[!NOTE]
>
>**Inhoudsfragmenten** en **[ervaringsfragmenten](/help/sites-authoring/experience-fragments.md)**zijn verschillende functies in AEM:
>
>* **Inhoudsfragmenten** zijn redactionele inhoud, voornamelijk tekst en verwante afbeeldingen. Het zijn pure inhoud, zonder ontwerp en lay-out.
>* **de inhoud van de ervaringsfragmenten** volledig wordt ingedeeld; een fragment van een webpagina.
>
>
De Fragmenten van de ervaring kunnen inhoud in de vorm van Inhoudsfragmenten bevatten, maar niet andersom.

## Waar kan ik inhoudsfragmenten vinden in We.Retail {#where-to-find-content-fragments-in-we-retail}

Er zijn verscheidene fragmenten van de steekproefinhoud in Wij.Retail; navigeer via **Middelen**, **Bestanden**, **We.Retail**, **Engels**, **Ervaringen**.

Dit zijn onder andere **Arctic Surfing in Lofoten**, een fragment en verwante visuele elementen:

* Navigeer via **Middelen**, **Bestanden**, **We.Retail**, **Engels**, **Ervaringen******, Artic Surfing in Lofoten:

   * [http://localhost:4502/assets.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten](http://localhost:4502/assets.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten)

![cf-44](assets/cf-44.png)

U kunt het fragment **Arctic Surfing in Lofoten** selecteren en bewerken:

* [http://localhost:4502/editor.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten/arctic-surfing-in-lofoten](http://localhost:4502/editor.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten/arctic-surfing-in-lofoten)

Hier kunt u het fragment [bewerken en beheren](/help/assets/content-fragments/content-fragments.md) met de tabbladen (linkerdeelvenster):

<!--![](do-not-localize/cf-45-aa.png) ![](do-not-localize/cf-45-a.png) ASSET does not exist-->

* **[Variaties](/help/assets/content-fragments/content-fragments-variations.md)**, inclusief[prijsverlaging](/help/assets/content-fragments/content-fragments-markdown.md)
* **[Gekoppelde inhoud](/help/assets/content-fragments/content-fragments-assoc-content.md)**
* **[Metagegevens](/help/assets/content-fragments/content-fragments-metadata.md)**

![cf-46](assets/cf-46.png)

## Waar de Fragmenten van de Inhoud in Wij.Detailhandel worden gebruikt {#where-content-fragments-are-used-in-we-retail}

Als u het ontwerpen van [pagina&#39;s wilt illustreren met een inhoudsfragment](/help/sites-authoring/content-fragments.md) , ziet u onder andere verschillende voorbeeldpagina&#39;s:

* [http://localhost:4502/sites.html/content/we-retail/language-masters/en/experience](http://localhost:4502/sites.html/content/we-retail/language-masters/en/experience)

Het inhoudsfragment **Arctic Surfing in Lofoten** verwijst bijvoorbeeld naar de pagina Sites:

* Navigeer via **Sites**, **We.Retail**, **taalmeesters**, **Engels**, **Ervaring**. Open vervolgens **Arctic Surfing in Lofoten** voor bewerking:

   * [http://localhost:4502/editor.html/content/we-retail/language-masters/en/experience/arctic-surfing-in-lofoten.html](http://localhost:4502/editor.html/content/we-retail/language-masters/en/experience/arctic-surfing-in-lofoten.html)

![cf-53](assets/cf-53.png)

## Aanvullende informatie {#further-information}

Zie voor meer informatie:

* [Werken met contentfragmenten](/help/assets/content-fragments/content-fragments.md)

   * Leer hoe u elementen van inhoudsfragmenten maakt, bewerkt en beheert.

* [Pagina&#39;s ontwerpen met inhoudsfragmenten](/help/sites-authoring/content-fragments.md)

   * Gebruik het inhoudsfragment wanneer u een pagina ontwerpt.

* [AEM ontwikkelen - Componenten voor inhoudsfragmenten](/help/sites-developing/components-content-fragments.md)

   * Een overzicht van de componenten voor Inhoudsfragmenten.

* [Inhoudsfragmenten ontwikkelen en uitbreiden](/help/sites-developing/customizing-content-fragments.md)

   * Informatie die u helpt bij het ontwikkelen en uitbreiden van inhoudsfragmenten.

