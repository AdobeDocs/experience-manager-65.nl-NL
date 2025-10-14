---
title: Sjablonen
description: Sjablonen worden gebruikt bij het maken van een pagina die als basis voor de nieuwe pagina wordt gebruikt.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
legacypath: /content/docs/en/aem/6-1/develop/the-basics/templates
exl-id: 59f01bb1-4ff1-42b6-afc9-56d448b1f803
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '924'
ht-degree: 0%

---

# Sjablonen{#templates}

Sjablonen worden op verschillende punten in AEM gebruikt:

* [&#x200B; wanneer u een pagina creeert, selecteert u een malplaatje &#x200B;](#templates-pages). Deze sjabloon wordt gebruikt als basis voor de nieuwe pagina. Het malplaatje bepaalt de structuur van de pagina, om het even welke aanvankelijke inhoud, en de [&#x200B; componenten &#x200B;](/help/sites-authoring/default-components.md) die (ontwerpeigenschappen) kunnen worden gebruikt.

* [&#x200B; wanneer u een Fragment van de Inhoud creeert, selecteert u ook een malplaatje &#x200B;](#templates-content-fragments). Deze sjabloon definieert de structuur, initiële elementen en variaties.

De volgende sjablonen worden in detail besproken:

* [Paginasjablonen - Bewerkbaar](/help/sites-developing/page-templates-editable.md)
* [Paginasjablonen - statisch](/help/sites-developing/page-templates-static.md)
* [Sjablonen voor inhoudsfragmenten](/help/sites-developing/content-fragment-templates.md)
* [Adaptieve sjabloonrendering](/help/sites-developing/templates-adaptive-rendering.md)

## Sjablonen - Pagina&#39;s {#templates-pages}

AEM biedt nu twee basistypen sjablonen voor het maken van pagina&#39;s:

>[!NOTE]
>
>Wanneer het gebruiken van een malplaatje om een pagina [&#128279;](/help/sites-authoring/managing-pages.md#creating-a-new-page) tot stand te brengen , is er geen zichtbaar verschil (aan de paginaauteur) en geen aanwijzing van het type van malplaatje dat wordt gebruikt.

### Bewerkbare sjablonen {#editable-templates}

Bewerkbare sjablonen worden nu beschouwd als aanbevolen werkwijzen voor het ontwikkelen met AEM.

De voordelen van bewerkbare sjablonen:

* Kan [&#x200B; worden gecreeerd &#x200B;](/help/sites-authoring/templates.md#creating-a-new-template-template-author) en [&#x200B; worden uitgegeven &#x200B;](/help/sites-authoring/templates.md#editing-a-template-structure-template-author) door uw auteurs.

* Er zijn nu regels waarmee u het volgende kunt definiëren voor pagina&#39;s die met de sjabloon zijn gemaakt:

   * de structuur
   * de initiële inhoud
   * inhoudsbeleid

* Nadat de nieuwe pagina is gemaakt, wordt een dynamische verbinding onderhouden tussen de pagina en de sjabloon. Deze verbinding houdt in dat wijzigingen in de sjabloonstructuur worden weerspiegeld op alle pagina&#39;s die met die sjabloon worden gemaakt. Wijzigingen in de oorspronkelijke inhoud worden niet doorgevoerd.
* Gebruikt het inhoudsbeleid (dat van de malplaatjeredacteur wordt uitgegeven) om de ontwerpeigenschappen (gebruikt niet de wijze van het Ontwerp binnen de paginaredacteur) voort te zetten.
* Wordt opgeslagen onder `/conf`
* Zie [&#x200B; Bewerkbare Malplaatjes &#x200B;](/help/sites-developing/page-templates-editable.md) voor verdere informatie.

>[!NOTE]
>
>Zie [&#x200B; Gebruikend Bewerkbare Malplaatjes van de Pagina om een plaats van de Experience Manager &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/page-authoring/template-editor-feature-video-use.html?lang=nl-NL) te ontwikkelen.

### Statische sjablonen {#static-templates}

Statische sjablonen:

* Moet door uw ontwikkelaars worden bepaald en worden gevormd.
* Het oorspronkelijke sjabloonsysteem van AEM dat voor veel versies beschikbaar was.
* Een statische sjabloon is een hiërarchie van knooppunten die dezelfde structuur heeft als de pagina die moet worden gemaakt, maar zonder daadwerkelijke inhoud.
* Wordt gekopieerd om de pagina te maken. Hierna bestaat geen dynamische verbinding.
* Gebruikt [&#x200B; Wijze van het Ontwerp &#x200B;](/help/sites-authoring/default-components-designmode.md) om ontwerpeigenschappen voort te zetten.
* Wordt opgeslagen onder `/apps`
* Zie [&#x200B; Statische Malplaatjes &#x200B;](/help/sites-developing/page-templates-static.md) voor verdere informatie.

>[!NOTE]
>
>Vanaf AEM 6.5 wordt het gebruik van statische sjablonen niet als een goede praktijk beschouwd. Gebruik in plaats hiervan Bewerkbare sjablonen.
>
>[&#x200B; AEM de hulpmiddelen van de Modernisering &#x200B;](modernization-tools.md) kunnen u helpen van statisch aan editable malplaatjes migreren.

### Beschikbaarheid sjabloon {#template-availability}

>[!CAUTION]
>
>AEM biedt veelvoudige eigenschappen aan om de malplaatjes te controleren die onder **Plaatsen** worden toegestaan. Het combineren van deze regels kan echter leiden tot complexe regels die moeilijk te volgen en te beheren zijn.
>
>Daarom adviseert de Adobe dat u eenvoudig begint, door te bepalen:
>
>* alleen de eigenschap `cq:allowedTemplates`
>
>* alleen in de hoofdmap van de site
>
>Zie We.Retail voor een voorbeeld: `/content/we-retail/jcr:content`
>
>De eigenschappen `allowedPaths`, `allowedParents` en `allowedChildren` kunnen ook op de sjablonen worden geplaatst om geavanceerdere regels te definiëren. Nochtans, waar mogelijk, is het veel *eenvoudiger om verdere `cq:allowedTemplates` eigenschappen op subsections van de plaats te bepalen als er een behoefte is om de toegestane malplaatjes verder te beperken.*
>
>Een extra voordeel is dat de `cq:allowedTemplates` eigenschappen door een auteur op het **Geavanceerde** lusje van de **Eigenschappen van de Pagina** kunnen worden bijgewerkt. De andere malplaatjeeigenschappen kunnen niet worden bijgewerkt gebruikend (standaard) UI, zodat zou een ontwikkelaar nodig hebben om de regels en een codeplaatsing voor elke verandering te handhaven.

Wanneer u een pagina maakt in de interface voor sitebeheer, is de lijst met beschikbare sjablonen afhankelijk van de locatie van de nieuwe pagina en de plaatsingsbeperkingen die in elke sjabloon zijn opgegeven.

De volgende eigenschappen bepalen of een sjabloon `T` wordt gebruikt voor een nieuwe pagina die als onderliggend item van pagina `P` moet worden geplaatst. Elk van deze eigenschappen is een tekenreeks met meerdere waarden die nul of meer reguliere expressies bevat die worden gebruikt voor overeenkomsten met paden:

* De eigenschap `cq:allowedTemplates` van de `jcr:content` subnode van `P` of een voorouder van `P` .

* De eigenschap `allowedPaths` van `T` .

* De eigenschap `allowedParents` van `T` .

* De eigenschap `allowedChildren` van de sjabloon `P` .

De evaluatie werkt als volgt:

* De eerste niet-lege `cq:allowedTemplates` eigenschap die wordt gevonden terwijl de paginahiërarchie oploopt, beginnend met `P` , komt overeen met het pad van `T` . Als geen van de waarden overeenkomt, wordt `T` afgewezen.

* Als `T` een niet-lege `allowedPaths` eigenschap heeft, maar geen van de waarden overeenkomen met het pad van `P` , wordt `T` afgewezen.

* Als beide bovenstaande eigenschappen leeg of niet bestaan, wordt `T` afgewezen, tenzij het tot dezelfde toepassing behoort als `P` . `T` behoort tot dezelfde toepassing als `P` als en alleen als de naam van het tweede niveau van het pad van `T` gelijk is aan de naam van het tweede niveau van het pad van `P` . De sjabloon `/apps/geometrixx/templates/foo` behoort bijvoorbeeld tot dezelfde toepassing als de pagina `/content/geometrixx` .

* Als `T` een niet-lege `allowedParents` eigenschap heeft, maar geen van de waarden overeenkomen met het pad van `P` , wordt `T` afgewezen.

* Als de sjabloon van `P` een niet-lege eigenschap `allowedChildren` heeft, maar geen van de waarden overeenkomen met het pad van `T` , wordt `T` afgewezen.

* In alle andere gevallen is `T` toegestaan.

Het volgende diagram toont het sjabloonevaluatieproces:

![&#x200B; chlimage_1-176 &#x200B;](assets/chlimage_1-176.png)

#### Sjablonen beperken die worden gebruikt in onderliggende pagina&#39;s {#limiting-templates-used-in-child-pages}

Als u wilt beperken welke sjablonen kunnen worden gebruikt om onderliggende pagina&#39;s onder een bepaalde pagina te maken, gebruikt u de eigenschap `cq:allowedTemplates` van het knooppunt `jcr:content` van de pagina om de lijst met sjablonen op te geven die als onderliggende pagina&#39;s moeten worden toegestaan. Elke waarde in de lijst moet een absoluut pad zijn naar een sjabloon voor een toegestane onderliggende pagina, bijvoorbeeld `/apps/geometrixx/templates/contentpage` .

U kunt de eigenschap `cq:allowedTemplates` op het knooppunt `jcr:content` van de sjabloon gebruiken om deze configuratie toe te passen op alle nieuwe pagina&#39;s die deze sjabloon gebruiken.

Als u meer beperkingen wilt toevoegen, bijvoorbeeld met betrekking tot de sjabloonhiërarchie, kunt u de eigenschappen `allowedParents/allowedChildren` op de sjabloon gebruiken. U kunt dan uitdrukkelijk specificeren dat de pagina&#39;s die van een malplaatjeT worden gecreeerd ouderpagina/kinderen van pagina&#39;s moeten zijn die van een malplaatjeT worden gecreeerd.

## Sjablonen - Inhoudsfragmenten {#templates-content-fragments}

Zie [&#x200B; de Malplaatjes van het Fragment van de Inhoud &#x200B;](/help/sites-developing/content-fragment-templates.md).
