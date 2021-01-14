---
title: Sjablonen
seo-title: Sjablonen
description: Sjablonen worden gebruikt bij het maken van een pagina die als basis voor de nieuwe pagina wordt gebruikt
seo-description: Sjablonen worden gebruikt bij het maken van een pagina die als basis voor de nieuwe pagina wordt gebruikt
uuid: 6fa3dafc-dfa1-42d8-b296-d4be57449411
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: 7c723773-7c23-43d7-85dc-53e54556b648
legacypath: /content/docs/en/aem/6-1/develop/the-basics/templates
translation-type: tm+mt
source-git-commit: 27276945a0bdb20410f4c0e98868ea5ce1c09a47
workflow-type: tm+mt
source-wordcount: '982'
ht-degree: 0%

---


# Sjablonen{#templates}

Sjablonen worden op verschillende punten in AEM gebruikt:

* Als u een pagina maakt [een sjabloon moet selecteren](#templates-pages); dit wordt gebruikt als basis voor de nieuwe pagina . De sjabloon definieert de structuur van de resulterende pagina, eventuele initiële inhoud en de [componenten](/help/sites-authoring/default-components.md) die kunnen worden gebruikt (ontwerpeigenschappen).

* Wanneer u een inhoudsfragment maakt [moet u ook een sjabloon selecteren](#templates-content-fragments). Deze sjabloon definieert de structuur, initiële elementen en variaties.

De volgende sjablonen worden in detail besproken:

* [Paginasjablonen - Bewerkbaar](/help/sites-developing/page-templates-editable.md)
* [Paginasjablonen - statisch](/help/sites-developing/page-templates-static.md)
* [Sjablonen voor inhoudsfragmenten](/help/sites-developing/content-fragment-templates.md)
* [Adaptieve sjabloonrendering](/help/sites-developing/templates-adaptive-rendering.md)

## Sjablonen - Pagina&#39;s {#templates-pages}

AEM biedt nu twee basistypen sjablonen voor het maken van pagina&#39;s:

>[!NOTE]
>
>Wanneer u een sjabloon gebruikt om [een nieuwe pagina te maken](/help/sites-authoring/managing-pages.md#creating-a-new-page), is er geen zichtbaar verschil (voor de auteur van de pagina) en is er geen indicatie van het type sjabloon dat wordt gebruikt.

### Bewerkbare sjablonen {#editable-templates}

Bewerkbare sjablonen worden nu beschouwd als aanbevolen werkwijzen voor het ontwikkelen met AEM.

De voordelen van bewerkbare sjablonen:

* Kan [worden gecreeerd](/help/sites-authoring/templates.md#creating-a-new-template-template-author) en [uitgegeven](/help/sites-authoring/templates.md#editing-a-template-structure-template-author) door uw auteurs.

* Zijn geïntroduceerd zodat u het volgende kunt definiëren voor pagina&#39;s die met de sjabloon zijn gemaakt:

   * de structuur
   * de initiële inhoud
   * inhoudsbeleid

* Nadat de nieuwe pagina is gemaakt, wordt een dynamische verbinding onderhouden tussen de pagina en de sjabloon. dit betekent dat wijzigingen in de sjabloonstructuur worden doorgevoerd op alle pagina&#39;s die met die sjabloon worden gemaakt (wijzigingen in de oorspronkelijke inhoud worden niet doorgevoerd).
* Gebruikt het inhoudsbeleid (dat van de malplaatjeredacteur wordt uitgegeven) om de ontwerpeigenschappen (gebruikt niet de wijze van het Ontwerp binnen de paginaredacteur) voort te zetten.
* Wordt opgeslagen onder `/conf`
* Zie [Bewerkbare sjablonen](/help/sites-developing/page-templates-editable.md) voor meer informatie.

>[!NOTE]
>
>Er is een AEM Community-artikel beschikbaar waarin wordt uitgelegd hoe u een Experience Manager-site met bewerkbare sjablonen kunt ontwikkelen. Zie [Een Adobe Experience Manager 6.5-website maken met Bewerkbare sjablonen](https://helpx.adobe.com/experience-manager/using/first_aem64_website.html).

### Statische sjablonen {#static-templates}

Statische sjablonen:

* Moet door uw ontwikkelaars worden bepaald en worden gevormd.
* Dit was het oorspronkelijke sjabloonsysteem van AEM en is al in vele versies beschikbaar.
* Een statische sjabloon is een hiërarchie van knooppunten die dezelfde structuur heeft als de pagina die moet worden gemaakt, maar zonder daadwerkelijke inhoud.
* Wordt gekopieerd om de nieuwe pagina te maken. Hierna bestaat geen dynamische verbinding.
* Gebruikt [Ontwerpmodus](/help/sites-authoring/default-components-designmode.md) om ontwerpeigenschappen te behouden.
* Wordt opgeslagen onder `/apps`
* Zie [Statische sjablonen](/help/sites-developing/page-templates-static.md) voor meer informatie.

>[!NOTE]
>
>Vanaf AEM 6.5 wordt het gebruik van statische sjablonen niet als een goede praktijk beschouwd. Gebruik in plaats hiervan Bewerkbare sjablonen.
>
>[AEM ](modernization-tools.md) Moderniseringsgereedschappen kunnen u helpen bij het migreren van statische naar bewerkbare sjablonen.

### Beschikbaarheid van sjabloon {#template-availability}

>[!CAUTION]
>
>AEM biedt veelvoudige eigenschappen aan om de malplaatjes te controleren die onder **Plaatsen** worden toegestaan. Het combineren ervan kan echter leiden tot zeer complexe regels die moeilijk te volgen en te beheren zijn.
>
>Daarom adviseert Adobe dat u eenvoudig begint, door te bepalen:
>
>* alleen de eigenschap `cq:allowedTemplates`
   >
   >
* alleen in de hoofdmap van de site
>
>
Voor een voorbeeld, zie Wij.Retail: `/content/we-retail/jcr:content`
>
>De eigenschappen `allowedPaths`, `allowedParents`, en `allowedChildren` kunnen ook op de malplaatjes worden geplaatst om verfijndere regels te bepalen. Waar mogelijk is het *veel* eenvoudiger om verdere `cq:allowedTemplates` eigenschappen op subsecties van de site te definiëren als de toegestane sjablonen verder moeten worden beperkt.
>
>Een extra voordeel is dat de `cq:allowedTemplates` eigenschappen door een auteur op **Geavanceerd** lusje van **Pagina-eigenschappen** kunnen worden bijgewerkt. De andere malplaatjeeigenschappen kunnen niet worden bijgewerkt gebruikend (standaard) UI, zodat zou een ontwikkelaar nodig hebben om de regels en een codeplaatsing voor elke verandering te handhaven.

Wanneer u een nieuwe pagina maakt in de interface voor sitebeheer, is de lijst met beschikbare sjablonen afhankelijk van de locatie van de nieuwe pagina en de plaatsingsbeperkingen die in elke sjabloon zijn opgegeven.

De volgende eigenschappen bepalen of een sjabloon `T` mag worden gebruikt voor een nieuwe pagina die als onderliggend item van pagina `P` moet worden geplaatst. Elk van deze eigenschappen is een tekenreeks met meerdere waarden die nul of meer reguliere expressies bevat die worden gebruikt voor overeenkomsten met paden:

* De eigenschap `cq:allowedTemplates` van het `jcr:content`-subknooppunt van `P` of een voorouder van `P`.

* De eigenschap `allowedPaths` van `T`.

* De eigenschap `allowedParents` van `T`.

* De eigenschap `allowedChildren` van de sjabloon `P`.

De evaluatie werkt als volgt:

* De eerste niet-lege `cq:allowedTemplates`-eigenschap die wordt gevonden terwijl de paginahiërarchie oploopt, beginnend met `P`, wordt vergeleken met het pad van `T`. Als geen van de waarden overeenkomt, wordt `T` geweigerd.

* Als `T` een niet-lege `allowedPaths` eigenschap heeft, maar geen van de waarden komt overeen met het pad van `P`, wordt `T` afgewezen.

* Als beide bovenstaande eigenschappen leeg of niet bestaan, wordt `T` geweigerd, tenzij het tot dezelfde toepassing behoort als `P`. `T` behoort tot dezelfde toepassing als  `P` alleen als de naam van het tweede niveau van het pad van dezelfde  `T` is als de naam van het tweede niveau van het pad van  `P`. De sjabloon `/apps/geometrixx/templates/foo` behoort bijvoorbeeld tot dezelfde toepassing als de pagina `/content/geometrixx`.

* Als `T` een niet-lege `allowedParents` eigenschap heeft, maar geen van de waarden komt overeen met het pad van `P`, wordt `T` afgewezen.

* Als de sjabloon van `P` een niet-lege `allowedChildren` eigenschap heeft, maar geen van de waarden komt overeen met het pad van `T`, wordt `T` afgewezen.

* In alle andere gevallen is `T` toegestaan.

Het volgende diagram toont het sjabloonevaluatieproces:

![chlimage_1-176](assets/chlimage_1-176.png)

#### Sjablonen beperken die worden gebruikt op onderliggende pagina&#39;s {#limiting-templates-used-in-child-pages}

Om te beperken welke malplaatjes kunnen worden gebruikt om kindpagina&#39;s onder een bepaalde pagina tot stand te brengen, gebruik `cq:allowedTemplates` bezit van `jcr:content` knoop van de pagina om de lijst van malplaatjes te specificeren die als kindpagina&#39;s moeten worden toegestaan. Elke waarde in de lijst moet een absoluut pad zijn naar een sjabloon voor een toegestane onderliggende pagina, bijvoorbeeld `/apps/geometrixx/templates/contentpage`.

U kunt het `cq:allowedTemplates` bezit op de `jcr:content` knoop van het malplaatje gebruiken om deze configuratie toe te passen op alle pas gecreëerde pagina&#39;s die dit malplaatje gebruiken.

Als u meer beperkingen wilt toevoegen, bijvoorbeeld met betrekking tot de sjabloonhiërarchie, kunt u de eigenschappen `allowedParents/allowedChildren` op de sjabloon gebruiken. U kunt dan uitdrukkelijk specificeren dat de pagina&#39;s die van een malplaatjeT worden gecreeerd ouderpagina/kinderen van pagina&#39;s moeten zijn die van een malplaatjeT worden gecreeerd.

## Sjablonen - Inhoudsfragmenten {#templates-content-fragments}

Zie [Sjablonen voor inhoudsfragmenten](/help/sites-developing/content-fragment-templates.md) voor volledige informatie.
