---
title: Componenten voor inhoudsfragmenten
seo-title: Componenten voor inhoudsfragmenten
description: AEM inhoudsfragmenten worden gemaakt en beheerd als pagina-onafhankelijke elementen
seo-description: AEM inhoudsfragmenten worden gemaakt en beheerd als pagina-onafhankelijke elementen
uuid: 81a9e0fe-ed45-4880-b36c-4f49e2598389
contentOwner: Alison Heimoz
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
discoiquuid: b7777dc5-a867-4799-9e2c-a1f4bb5dd96a
docset: aem65
pagetitle: Components for Content Fragments
translation-type: tm+mt
source-git-commit: afed13a2f832b91d0df825d1075852cc84443646
workflow-type: tm+mt
source-wordcount: '960'
ht-degree: 1%

---


# Componenten voor inhoudsfragmenten{#components-for-content-fragments}

## Componenten voor het ontwerpen van fragmenten {#components-for-fragment-authoring}

>[!CAUTION]
>
>Het wordt afgeraden de werkelijke componenten die in de fragmenteditor worden gebruikt, uit te breiden of te wijzigen, omdat deze nog steeds kunnen worden gewijzigd.

Zie [Inhoudsfragmentbeheer-API - Client-Side](/help/sites-developing/customizing-content-fragments.md#the-content-fragment-management-api-client-side).

## Componenten voor pagina-ontwerp {#components-for-page-authoring}

>[!CAUTION]
>
>De [Content Fragment Core Component](https://helpx.adobe.com/experience-manager/core-components/using/content-fragment-component.html) wordt nu aanbevolen. Zie [Core Components](https://helpx.adobe.com/experience-manager/core-components/using/developing.html) ontwikkelen voor meer informatie.
>
>In deze sectie wordt de oorspronkelijke component beschreven die is geleverd voor gebruik met inhoudsfragmenten (**Inhoudsfragment** in de groep **Algemeen**).

>[!NOTE]
>
>Zie ook [Inhoudsfragmenten die Componenten configureren voor rendering](/help/sites-developing/content-fragments-config-components-rendering.md) voor meer informatie.

Inhoudsfragmenten van Adobe Experience Manager (AEM) worden [gemaakt en beheerd als paginaonafhankelijke assets](/help/assets/content-fragments/content-fragments.md). U kunt hiermee kanaalneutrale inhoud maken, samen met (mogelijk kanaalspecifieke) variaties. [Vervolgens kunt u deze fragmenten en de variaties ervan gebruiken bij het ontwerpen van de inhoudspagina](/help/sites-authoring/content-fragments.md)&#39;s. U kunt ook een bestaand inhoudsfragmentelement gebruiken door het element [van de elementenbrowser naar de pagina te slepen](/help/sites-authoring/content-fragments.md#adding-a-content-fragment-to-your-page) (zoals bij andere elementen, zoals de basiscomponentafbeelding). De component van het inhoudsfragment uit de doos toont slechts één [element](/help/assets/content-fragments/content-fragments.md#constituent-parts-of-a-content-fragment) van het referenced inhoudsfragment. Met behulp van het componentdialoogvenster kunt u het [element, de variatie en het bereik van fragmentalinea&#39;s](/help/assets/content-fragments/content-fragments.md#constituent-parts-of-a-content-fragment) definiëren die u op de pagina wilt weergeven.

>[!NOTE]
>
>Deze component Content Fragment is in AEM 6.2 geïntroduceerd als een verbeterde versie van de component Article, die is vervangen.

>[!NOTE]
>
>Inhoudsfragmenten worden niet ondersteund in de klassieke UI.

### Definitie {#definition}

De component **Inhoudsfragment** wordt gebruikt om een verwijzing naar een inhoudsfragmentelement (effectief verbeterde tekstelementen) te bevatten. Het middeltype voor het inhoudsfragment is:

`dam/cfm/components/contentfragment/contentfragment`

De verwijzing wordt gedefinieerd in de eigenschap:

`fileReference`

Alleen de editor van de interface met aanraakbediening biedt volledige ondersteuning voor componenten van inhoudsfragmenten, waaronder de clientbibliotheek:

`cq.authoring.editor.plugin.cfm`

Deze bibliotheek voegt eigenschappen, specifiek voor inhoudsfragmenten, aan de redacteur toe. Er is bijvoorbeeld ondersteuning beschikbaar voor het toevoegen en configureren van inhoudsfragmenten op de pagina, het zoeken naar elementen van inhoudsfragmenten in de elementenbrowser en de bijbehorende inhoud in het zijpaneel.

### Tussen inhoud {#in-between-content}

Met de component **Inhoudskader** t kunt u extra componenten tussen de verschillende alinea&#39;s van het weergegeven [element](/help/assets/content-fragments/content-fragments.md#constituent-parts-of-a-content-fragment) neerzetten. In feite bestaat het weergegeven element uit verschillende alinea&#39;s (elke alinea wordt gemarkeerd door een regelterugloop). Tussen deze alinea&#39;s kunt u inhoud invoegen met behulp van andere componenten.

Vanuit technisch gezichtspunt, zal elke paragraaf van het getoonde element* *life in zijn eigen parsys, en elke component die u binnen-tussen de paragrafen toevoegt (onder de kap) in parsys worden opgenomen.

Met andere woorden, als de instantie van de inhoudfragment component uit drie paragrafen wordt samengesteld, dan zal de component drie verschillende parsys in de bewaarplaats hebben. Alle inwendige inhoud die aan het inhoudsfragment wordt toegevoegd zal eigenlijk binnen deze parsys worden gevestigd.

In de gegevensopslagruimte wordt de tussenliggende inhoud opgeslagen ten opzichte van de positie binnen de algemene alinearichting, d.w.z. de inhoud is niet gekoppeld aan de werkelijke alinea-inhoud.

Om dit te illustreren, moeten we bedenken dat we:

* Een instantie van een inhoudsfragment dat bestaat uit drie alinea&#39;s
* En dat bepaalde inhoud al is ingevoegd na de tweede alinea

   * Dit betekent dat de inhoud in tweede parsys zal worden opgeslagen.

Als de alineabstructuur van dit exemplaar verandert (door de variatie, het element of het bereik van de weergegeven alinea&#39;s te wijzigen), kan dit van invloed zijn op de tussenliggende inhoud die wordt weergegeven wanneer de inhoud van het inhoudsfragment:

* Wordt bewerkt en een andere alinea wordt toegevoegd vóór de tweede alinea:

   * De inhoud tussen wordt weergegeven na de nieuwe alinea (de tweede alinea bevat nu de nieuwe alinea).

* Wordt bewerkt en de tweede alinea wordt verwijderd:

   * De inhoud tussen de pagina&#39;s wordt weergegeven na de alinea die eerder de derde alinea was (de tweede alinea bevat nu de vorige derde alinea).

* Is zo gevormd dat slechts de eerste paragraaf wordt getoond:

   * De inhoud in-tussen zal niet worden getoond (tweede parsys wordt niet meer teruggegeven toe te schrijven aan de nieuwe configuratie).

### De component Inhoudsfragment {#customizing-the-content-fragment-component} aanpassen

Als u de uit-van-de-doos component van het inhoudsfragment als blauwdruk voor uitbreiding wilt gebruiken, zou u het volgende contract moeten respecteren:

* U kunt het HTML-renderscript en de bijbehorende POJO opnieuw gebruiken om te zien hoe de functie voor de tussenliggende inhoud is geïmplementeerd.
* Het knooppunt voor inhoudsfragmenten opnieuw gebruiken: `cq:editConfig`

   * De `afterinsert`/ `afteredit`/ `afterdelete` listeners worden gebruikt om JS-gebeurtenissen te activeren. Deze gebeurtenissen worden afgehandeld in de clientbibliotheek `cq.authoring.editor.plugin.cfm` om de bijbehorende inhoud weer te geven in het zijpaneel.
   * `cq:dropTargets` worden gevormd om het slepen van de elementen van het inhoudsfragment te steunen.
   * `cq:inplaceEditing` is geconfigureerd ter ondersteuning van het ontwerpen van een inhoudsfragment in de pagina-editor. De op plaats-plaats fragmentredacteur wordt bepaald in `cq.authoring.editor.plugin.cfm` cliëntbibliotheek en staat een snelle verbinding toe om het huidige [element/variation](/help/assets/content-fragments/content-fragments.md#constituent-parts-of-a-content-fragment) in [fragmentredacteur](/help/assets/content-fragments/content-fragments-variations.md) te openen.

### Element herschrijven vóór renderen {#asset-rewriting-before-rendering}

Bij Inhoudsfragmentbeheer wordt een intern renderingsproces gebruikt om de uiteindelijke HTML-uitvoer voor een pagina te genereren. Dit wordt intern gebruikt door de component van het Fragment van de Inhoud, maar ook door het achtergrondproces dat referenced fragmenten op het van verwijzingen voorzien pagina&#39;s bijwerkt.

Intern wordt de Sling Rewriter gebruikt voor die rendering. De respectieve configuratie wordt gevonden bij `/libs/dam/config/rewriter/cfm` en kan indien nodig worden aangepast. Zie [Apache Sling Rewriter](https://sling.apache.org/documentation/bundles/output-rewriting-pipelines-org-apache-sling-rewriter.html) voor meer informatie.

De uit-van-de-doos configuratie gebruikt de volgende transformatoren:

* `transformer-cfm-payloadfilter` - alleen voor het ophalen van het  `body` deel (  `<body>...</body>`) van de HTML van het fragment

* `transformer-cfm-parfilter` - filtert ongewenste alinea&#39;s uit als er een alineabereik is opgegeven (zoals u kunt doen met de component Content Fragment)
* `transformer-cfm-assetprocessor` - intern wordt gebruikt voor het ophalen van een lijst met elementen die zijn ingesloten in het fragment

Het renderingsproces wordt zichtbaar via [`com.adobe.cq.dam.cfm.content.FragmentRenderService`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/dam/cfm/ContentFragment.html) en kan (bijvoorbeeld) worden benut door aangepaste componenten indien nodig.
