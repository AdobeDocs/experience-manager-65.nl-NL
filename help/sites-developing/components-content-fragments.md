---
title: Componenten voor inhoudsfragmenten
description: Adobe Experience Manager (AEM)-inhoudsfragmenten worden gemaakt en beheerd als pagina-onafhankelijke elementen
contentOwner: AEM Docs
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
docset: aem65
pagetitle: Components for Content Fragments
exl-id: f2edd9b2-f231-42f3-a25e-428cd1d96c2a
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '932'
ht-degree: 0%

---

# Componenten voor inhoudsfragmenten{#components-for-content-fragments}

## Componenten voor het ontwerpen van fragmenten {#components-for-fragment-authoring}

>[!CAUTION]
>
>Het wordt afgeraden de werkelijke componenten die in de fragmenteditor worden gebruikt, uit te breiden of te wijzigen, omdat deze nog steeds kunnen worden gewijzigd.

Zie de [Content Fragment Management API - Client-kant](/help/sites-developing/customizing-content-fragments.md#the-content-fragment-management-api-client-side).

## Componenten voor paginaontwerp {#components-for-page-authoring}

>[!CAUTION]
>
>De [Component Content Fragment Core](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html) wordt nu aanbevolen. Zie [Basiscomponenten ontwikkelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/overview.html) voor meer informatie .
>
>In deze sectie wordt de oorspronkelijke component beschreven die is geleverd voor gebruik met inhoudsfragmenten (**Inhoudsfragment** in de **Algemeen** groep).

>[!NOTE]
>
>Zie ook [Inhoudsfragmenten die componenten voor rendering configureren](/help/sites-developing/content-fragments-config-components-rendering.md) voor nadere informatie.

Adobe Experience Manager (AEM)-inhoudsfragmenten zijn [gemaakt en beheerd als pagina-onafhankelijke elementen](/help/assets/content-fragments/content-fragments.md). U kunt hiermee kanaalneutrale inhoud maken, samen met (mogelijk kanaalspecifieke) variaties. [Vervolgens kunt u deze fragmenten en de variaties ervan gebruiken bij het ontwerpen van de inhoudspagina&#39;s](/help/sites-authoring/content-fragments.md). U kunt ook een bestaand inhoudsfragmentelement gebruiken door [het slepen van middelenbrowser naar pagina](/help/sites-authoring/content-fragments.md#adding-a-content-fragment-to-your-page) (zoals voor andere op activa-gebaseerde componenten, zoals het stichtingscomponentenbeeld). De inhoud van het inhoudsfragmentcomponent uit de doos toont slechts één [element](/help/assets/content-fragments/content-fragments.md#constituent-parts-of-a-content-fragment) van het inhoudsfragment waarnaar wordt verwezen. Met behulp van het componentdialoogvenster kunt u het dialoogvenster [element, variatie en bereik van fragmentalinea&#39;s](/help/assets/content-fragments/content-fragments.md#constituent-parts-of-a-content-fragment) die u op de pagina wilt weergeven.

>[!NOTE]
>
>Deze component van het Fragment van de Inhoud werd geïntroduceerd in AEM 6.2 als verbeterde versie van de component van het Artikel, die is afgekeurd.

>[!NOTE]
>
>Inhoudsfragmenten worden niet ondersteund in de klassieke UI.

### Definitie {#definition}

De **Inhoudsfragment** wordt gebruikt om een verwijzing naar een inhoudsfragmentelement (effectief verbeterde tekstelementen) te bevatten. Het middeltype voor het inhoudsfragment is:

`dam/cfm/components/contentfragment/contentfragment`

De verwijzing wordt gedefinieerd in de eigenschap:

`fileReference`

Alleen de editor van de interface met aanraakbediening biedt volledige ondersteuning voor componenten van inhoudsfragmenten, waaronder de clientbibliotheek:

`cq.authoring.editor.plugin.cfm`

Deze bibliotheek voegt eigenschappen, specifiek voor inhoudsfragmenten, aan de redacteur toe. Er is bijvoorbeeld ondersteuning beschikbaar voor de mogelijkheid om inhoudsfragmenten op de pagina toe te voegen en te configureren, de mogelijkheid om te zoeken naar elementen van inhoudsfragmenten in de elementenbrowser en naar bijbehorende inhoud in het zijpaneel.

### Tussen inhoud {#in-between-content}

De **Inhoudskader** Hiermee kunt u extra componenten tussen de verschillende alinea&#39;s van het weergegeven [element](/help/assets/content-fragments/content-fragments.md#constituent-parts-of-a-content-fragment). In feite bestaat het weergegeven element uit verschillende alinea&#39;s (elke alinea wordt gemarkeerd door een regelterugloop). Tussen deze alinea&#39;s kunt u inhoud invoegen met behulp van andere componenten.

Vanuit technisch gezichtspunt, leeft elke paragraaf van het getoonde element in zijn eigen parsys, en elke component die u tussen de paragrafen toevoegt wordt (onder de kap) opgenomen in parsys.

Met andere woorden, als de instantie van de inhoudfragment component uit drie paragrafen wordt samengesteld, dan heeft de component drie verschillende parsys in de bewaarplaats. Alle inwendige inhoud die aan het inhoudsfragment wordt toegevoegd wordt eigenlijk gevestigd binnen deze parsys.

In de opslagplaats wordt de tussenliggende inhoud opgeslagen ten opzichte van de positie binnen de algemene alineastijl, dat wil zeggen dat de inhoud niet is gekoppeld aan de werkelijke alinea-inhoud.

U kunt dit als volgt illustreren:

* Een instantie van een inhoudsfragment dat bestaat uit drie alinea&#39;s
* En dat bepaalde inhoud al is ingevoegd na de tweede alinea

   * Dit betekent dat de inhoud in tweede parsys wordt opgeslagen.

Als de alineabstructuur van dit exemplaar verandert (door de variatie, het element of het bereik van de weergegeven alinea&#39;s te wijzigen), kan dit van invloed zijn op de tussenliggende inhoud die wordt weergegeven wanneer de inhoud van het inhoudsfragment:

* Wordt bewerkt en een andere alinea wordt toegevoegd vóór de tweede alinea:

   * De inhoud tussen wordt weergegeven na de zojuist gemaakte alinea (de tweede alinea bevat nu de zojuist gemaakte alinea).

* Wordt bewerkt en de tweede alinea wordt verwijderd:

   * De inhoud tussen wordt weergegeven na de alinea die eerder de derde alinea was (de tweede alinea bevat nu de vorige derde alinea).

* Is zo gevormd dat slechts de eerste paragraaf wordt getoond:

   * De inhoud tussen wordt niet getoond (tweede parsys wordt niet meer teruggegeven toe te schrijven aan de nieuwe configuratie).

### De component Inhoudsfragment aanpassen {#customizing-the-content-fragment-component}

Als u de uit-van-de-doos component van het inhoudsfragment als blauwdruk voor uitbreiding wilt gebruiken, zou u het volgende contract moeten respecteren:

* U kunt het HTML-renderingsscript en de bijbehorende POJO opnieuw gebruiken, zodat u kunt zien hoe de functie voor de tussenliggende inhoud is geïmplementeerd.
* Het knooppunt voor inhoudsfragmenten opnieuw gebruiken: `cq:editConfig`

   * De `afterinsert`/ `afteredit`/ `afterdelete` listeners worden gebruikt om JS-gebeurtenissen te activeren. Deze gebeurtenissen worden verwerkt in het dialoogvenster `cq.authoring.editor.plugin.cfm` clientbibliotheek om de bijbehorende inhoud in het zijpaneel weer te geven.
   * De `cq:dropTargets` zijn geconfigureerd voor het slepen van inhoud van fragmentelementen.
   * `cq:inplaceEditing` is geconfigureerd ter ondersteuning van het ontwerpen van een inhoudsfragment in de pagina-editor. De fragmentbewerker ter plekke wordt gedefinieerd in het dialoogvenster `cq.authoring.editor.plugin.cfm` clientbibliotheek en maakt een snelle koppeling mogelijk om de huidige [element/variatie](/help/assets/content-fragments/content-fragments.md#constituent-parts-of-a-content-fragment) in de [fragmenteditor](/help/assets/content-fragments/content-fragments-variations.md).

### Herschrijven van element vóór renderen {#asset-rewriting-before-rendering}

Bij Inhoudsfragmentbeheer wordt een intern renderingsproces gebruikt om de uiteindelijke HTML-uitvoer voor een pagina te genereren. Dit wordt intern gebruikt door de component van het Fragment van de Inhoud, maar ook door het achtergrondproces dat referenced fragmenten op het van verwijzingen voorzien pagina&#39;s bijwerkt.

Intern wordt de Sling Rewriter gebruikt voor die rendering. De respectievelijke configuratie is te vinden op `/libs/dam/config/rewriter/cfm` en kan zo nodig worden aangepast. Zie de [Apache Sling Rewriter](https://sling.apache.org/documentation/bundles/output-rewriting-pipelines-org-apache-sling-rewriter.html) voor meer informatie .

>[!CAUTION]
>
>Als u de configuratie van de rewriter aanpast/bedekt:
>
>* `/libs/dam/config/rewriter/cfm`
>
>Vervolgens worden de `serializerType` **moet** worden bijgewerkt naar:
>
>* `serializerType="html5-serializer"`

De uit-van-de-doos configuratie gebruikt de volgende transformatoren:

* `transformer-cfm-payloadfilter` - voor het ophalen van de `body` deel ( `<body>...</body>`) van alleen de HTML van het fragment

* `transformer-cfm-parfilter` - filtert ongewenste alinea&#39;s uit als er een alineabereik is opgegeven (zoals u kunt doen met de component Content Fragment)
* `transformer-cfm-assetprocessor` - intern wordt gebruikt voor het ophalen van een lijst met elementen die zijn ingesloten in het fragment

Het renderingsproces wordt via [`com.adobe.cq.dam.cfm.content.FragmentRenderService`](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/dam/cfm/ContentFragment.html) en kan, indien nodig, worden gebruikt (bijvoorbeeld) door aangepaste componenten.
