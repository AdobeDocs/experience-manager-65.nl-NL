---
title: Inhoudsfragmenten in We.Retail uitproberen
description: Leer hoe u in Adobe Experience Manager contentfragmenten kunt uitproberen met We.Retail.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: 1e5d8184-7164-4984-b43e-421015e8bf52
solution: Experience Manager, Experience Manager Sites
feature: Content Fragments,Developing
role: Developer
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# Inhoudsfragmenten in We.Retail uitproberen{#trying-out-content-fragments-in-we-retail}

Met Inhoudsfragmenten kunt u kanaalneutrale inhoud maken, samen met (mogelijk kanaalspecifieke) variaties. **Wij.Retail** (zoals beschikbaar in een uit-van-de-doosgeval van Adobe Experience Manager) verstrekt het fragment **Arctic Surfing in Vloeiend** als basissteekproef. Hieruit blijkt dat:

* Adobe Experience Manager (AEM) inhoudsfragmenten worden [&#x200B; gecreeerd en geleid als pagina-onafhankelijke activa &#x200B;](/help/assets/content-fragments/content-fragments.md). U kunt hiermee kanaalneutrale inhoud maken, samen met (mogelijk kanaalspecifieke) variaties.

   * Zie [&#x200B; waar te om de activa van het Fragment van de Inhoud in Wij.Retail te vinden &#x200B;](#where-to-find-content-fragments-in-we-retail)

* U kunt [&#x200B; deze fragmenten, en hun variaties dan gebruiken, wanneer het ontwerpen van &#x200B;](/help/sites-authoring/content-fragments.md) uw inhoudspagina&#39;s.

   * Zie [&#x200B; waar de Fragmenten van de Inhoud in Wij.Retail &#x200B;](#where-content-fragments-are-used-in-we-retail) worden gebruikt

Voor de volledige documentatie over het maken, beheren, gebruiken en ontwikkelen van inhoudsfragmenten:

* Zie [&#x200B; Verdere Informatie &#x200B;](#further-information)

>[!NOTE]
>
>**de Fragmenten van de Inhoud** en **[Fragmenten van de Ervaring](/help/sites-authoring/experience-fragments.md)** zijn verschillende eigenschappen binnen AEM:
>
>* **de Fragmenten van de Inhoud** zijn redactionele inhoud, hoofdzakelijk tekst, en verwante beelden. Het zijn pure inhoud, zonder ontwerp en lay-out.
>* **de Fragmenten van de Ervaring** zijn volledig opgemaakt inhoud; een fragment van een Web-pagina.
>
>De Fragmenten van de ervaring kunnen inhoud in de vorm van Inhoudsfragmenten bevatten, maar niet andersom.

## Waar kan ik inhoudsfragmenten vinden in We.Retail {#where-to-find-content-fragments-in-we-retail}

Er zijn verscheidene fragmenten van de steekproefinhoud in Wij.Retail; navigeer via **Assets**, **Dossiers**, **Wij.Retail**, **Engels**, **Ervaringen**.

Deze omvatten **het Surfen van het Noordpoolgebied in Vloeiend**, een fragment samen met verwante visuele activa:

* Navigeer als **Assets**, **Dossiers**, **Wij.Retail**, **Engels**, **Ervaringen**, **het Opdrijven van het Noordpoolgebied in Vloeiend**:

   * [&#x200B; http://localhost:4502/assets.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten](http://localhost:4502/assets.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten)

![&#x200B; cf-44 &#x200B;](assets/cf-44.png)

U kunt **Arctic Surfing in** fragment selecteren en uitgeven Lofoten:

* [&#x200B; http://localhost:4502/editor.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten/arctic-surfing-in-lofoten](http://localhost:4502/editor.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten/arctic-surfing-in-lofoten)

Hier kunt u [&#128279;](/help/assets/content-fragments/content-fragments.md) uw fragment uitgeven en beheren  gebruikend de lusjes (linkerzijpaneel):

<!--![cf-45-aa](do-not-localize/cf-45-aa.png) ![cf-45-a](do-not-localize/cf-45-a.png) ASSET does not exist-->

* **[Variaties](/help/assets/content-fragments/content-fragments-variations.md)** met inbegrip van [&#x200B; Markting &#x200B;](/help/assets/content-fragments/content-fragments-markdown.md)
* **[Verwante Inhoud](/help/assets/content-fragments/content-fragments-assoc-content.md)**
* **[Metagegevens](/help/assets/content-fragments/content-fragments-metadata.md)**

![&#x200B; cf-46 &#x200B;](assets/cf-46.png)

## Waar de Fragmenten van de Inhoud in Wij.Retail worden gebruikt {#where-content-fragments-are-used-in-we-retail}

Om [&#x200B; pagina te illustreren creerend met een inhoudsfragment &#x200B;](/help/sites-authoring/content-fragments.md) zijn er verscheidene voorbeeldpagina&#39;s onder, bijvoorbeeld:

* [&#x200B; http://localhost:4502/sites.html/content/we-retail/language-masters/en/experience](http://localhost:4502/sites.html/content/we-retail/language-masters/en/experience)

Bijvoorbeeld, wordt het **Arctic Surfing in Vloeiend** inhoudsfragment van het Noordpoolgebied van verwijzingen voorzien in de pagina van Plaatsen:

* Navigeer via **Plaatsen**, **wij.Retail**, **de Meesters van de Taal**, **Engels**, **Ervaring**. Dan open **Arctic Surfing in Vloeiend** voor het uitgeven:

   * [&#x200B; http://localhost:4502/editor.html/content/we-retail/language-masters/en/experience/arctic-surfing-in-lofoten.html](http://localhost:4502/editor.html/content/we-retail/language-masters/en/experience/arctic-surfing-in-lofoten.html)

![&#x200B; cf-53 &#x200B;](assets/cf-53.png)

## Aanvullende informatie {#further-information}

Zie voor meer informatie:

* [Werken met inhoudsfragmenten](/help/assets/content-fragments/content-fragments.md)

   * Leer hoe u elementen van inhoudsfragmenten maakt, bewerkt en beheert.

* [Pagina&#39;s ontwerpen met inhoudsfragmenten](/help/sites-authoring/content-fragments.md)

   * Gebruik het inhoudsfragment wanneer u een pagina ontwerpt.

* [AEM ontwikkelen - Componenten voor inhoudsfragmenten](/help/sites-developing/components-content-fragments.md)

   * Een overzicht van de componenten voor Content Fragments.

* [Inhoudsfragmenten ontwikkelen en uitbreiden](/help/sites-developing/customizing-content-fragments.md)

   * Informatie die u helpt bij het ontwikkelen en uitbreiden van inhoudsfragmenten.
