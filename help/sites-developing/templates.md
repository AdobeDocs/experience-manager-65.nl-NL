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

* [Wanneer u een pagina maakt, selecteert u een sjabloon](#templates-pages). Deze sjabloon wordt gebruikt als basis voor de nieuwe pagina. De sjabloon definieert de structuur van de pagina, eventuele eerste inhoud en de [componenten](/help/sites-authoring/default-components.md) die kunnen worden gebruikt (ontwerpeigenschappen).

* [Wanneer u een inhoudsfragment maakt, selecteert u ook een sjabloon](#templates-content-fragments). Deze sjabloon definieert de structuur, initiële elementen en variaties.

De volgende sjablonen worden in detail besproken:

* [Paginasjablonen - Bewerkbaar](/help/sites-developing/page-templates-editable.md)
* [Paginasjablonen - statisch](/help/sites-developing/page-templates-static.md)
* [Sjablonen voor inhoudsfragmenten](/help/sites-developing/content-fragment-templates.md)
* [Adaptieve sjabloonrendering](/help/sites-developing/templates-adaptive-rendering.md)

## Sjablonen - Pagina&#39;s {#templates-pages}

AEM biedt nu twee basistypen sjablonen voor het maken van pagina&#39;s:

>[!NOTE]
>
>Als u een sjabloon gebruikt naar [een pagina maken](/help/sites-authoring/managing-pages.md#creating-a-new-page)Er is echter geen zichtbaar verschil (voor de auteur van de pagina) en er is geen indicatie van het type sjabloon dat wordt gebruikt.

### Bewerkbare sjablonen {#editable-templates}

Bewerkbare sjablonen worden nu beschouwd als aanbevolen werkwijzen voor het ontwikkelen met AEM.

De voordelen van bewerkbare sjablonen:

* Kan [gemaakt](/help/sites-authoring/templates.md#creating-a-new-template-template-author) en [bewerkt](/help/sites-authoring/templates.md#editing-a-template-structure-template-author) door uw auteurs.

* Er zijn nu regels waarmee u het volgende kunt definiëren voor pagina&#39;s die met de sjabloon zijn gemaakt:

   * de structuur
   * de initiële inhoud
   * inhoudsbeleid

* Nadat de nieuwe pagina is gemaakt, wordt een dynamische verbinding onderhouden tussen de pagina en de sjabloon. Deze verbinding houdt in dat wijzigingen in de sjabloonstructuur worden weerspiegeld op alle pagina&#39;s die met die sjabloon worden gemaakt. Wijzigingen in de oorspronkelijke inhoud worden niet doorgevoerd.
* Gebruikt het inhoudsbeleid (dat van de malplaatjeredacteur wordt uitgegeven) om de ontwerpeigenschappen (gebruikt niet de wijze van het Ontwerp binnen de paginaredacteur) voort te zetten.
* worden opgeslagen onder `/conf`
* Zie [Bewerkbare sjablonen](/help/sites-developing/page-templates-editable.md) voor nadere informatie.

>[!NOTE]
>
>Zie [Bewerkbare paginasjablonen gebruiken om een Experience Manager-site te ontwikkelen](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/page-authoring/template-editor-feature-video-use.html).

### Statische sjablonen {#static-templates}

Statische sjablonen:

* Moet door uw ontwikkelaars worden bepaald en worden gevormd.
* Het oorspronkelijke sjabloonsysteem van AEM dat voor veel versies beschikbaar was.
* Een statische sjabloon is een hiërarchie van knooppunten die dezelfde structuur heeft als de pagina die moet worden gemaakt, maar zonder daadwerkelijke inhoud.
* Wordt gekopieerd om de pagina te maken. Hierna bestaat geen dynamische verbinding.
* Gebruiksmiddelen [Ontwerpmodus](/help/sites-authoring/default-components-designmode.md) om ontwerpeigenschappen te behouden.
* worden opgeslagen onder `/apps`
* Zie [Statische sjablonen](/help/sites-developing/page-templates-static.md) voor nadere informatie.

>[!NOTE]
>
>Vanaf AEM 6.5 wordt het gebruik van statische sjablonen niet als een goede praktijk beschouwd. Gebruik in plaats hiervan Bewerkbare sjablonen.
>
>[AEM modernisering](modernization-tools.md) met gereedschappen kunt u migreren van statische naar bewerkbare sjablonen.

### Beschikbaarheid sjabloon {#template-availability}

>[!CAUTION]
>
>AEM biedt meerdere eigenschappen om de sjablonen te beheren die zijn toegestaan onder **Sites**. Het combineren van deze regels kan echter leiden tot complexe regels die moeilijk te volgen en te beheren zijn.
>
>Daarom adviseert de Adobe dat u eenvoudig begint, door te bepalen:
>
>* alleen de `cq:allowedTemplates` eigenschap
>
>* alleen in de hoofdmap van de site
>
>Voor een voorbeeld, zie Wij.Retail: `/content/we-retail/jcr:content`
>
>De eigenschappen `allowedPaths`, `allowedParents`, en `allowedChildren` kan ook op de malplaatjes worden geplaatst om verfijndere regels te bepalen. Waar mogelijk is het echter *veel* eenvoudiger te definiëren `cq:allowedTemplates` eigenschappen op subsecties van de site als de toegestane sjablonen verder moeten worden beperkt.
>
>Een extra voordeel is dat de `cq:allowedTemplates` eigenschappen kunnen door een auteur worden bijgewerkt in het dialoogvenster **Geavanceerd** tabblad van het **Pagina-eigenschappen**. De andere malplaatjeeigenschappen kunnen niet worden bijgewerkt gebruikend (standaard) UI, zodat zou een ontwikkelaar nodig hebben om de regels en een codeplaatsing voor elke verandering te handhaven.

Wanneer u een pagina maakt in de interface voor sitebeheer, is de lijst met beschikbare sjablonen afhankelijk van de locatie van de nieuwe pagina en de plaatsingsbeperkingen die in elke sjabloon zijn opgegeven.

De volgende eigenschappen bepalen of een sjabloon `T` wordt gebruikt voor een nieuwe pagina die als onderliggend item van een pagina moet worden geplaatst `P`. Elk van deze eigenschappen is een tekenreeks met meerdere waarden die nul of meer reguliere expressies bevat die worden gebruikt voor overeenkomsten met paden:

* De `cq:allowedTemplates` eigendom van de `jcr:content` subknooppunt van `P` of een voorouder van `P`.

* De `allowedPaths` eigenschap van `T`.

* De `allowedParents` eigenschap van `T`.

* De `allowedChildren` eigenschap van de template van `P`.

De evaluatie werkt als volgt:

* De eerste niet-lege `cq:allowedTemplates` eigenschap gevonden tijdens oplopende paginahiërarchie, beginnend met `P` komt overeen met het pad van `T`. Als geen van de waarden overeenkomt, `T` wordt verworpen.

* Indien `T` heeft een niet-leeg `allowedPaths` eigenschap, maar geen van de waarden komt overeen met het pad van `P`, `T` wordt verworpen.

* Als beide bovengenoemde eigenschappen leeg of niet bestaan, `T` wordt afgewezen, tenzij het tot dezelfde aanvraag behoort als `P`. `T` behoort tot dezelfde toepassing als `P` als en alleen als de naam van het tweede niveau van het pad van `T` is gelijk aan de naam van het tweede niveau van het pad van `P`. De sjabloon `/apps/geometrixx/templates/foo` behoort tot dezelfde toepassing als de pagina `/content/geometrixx`.

* Indien `T` heeft een niet-leeg `allowedParents` eigenschap, maar geen van de waarden komt overeen met het pad van `P`, `T` wordt verworpen.

* Indien de template van `P` heeft een niet-leeg `allowedChildren` eigenschap, maar geen van de waarden komt overeen met het pad van `T`, `T` wordt verworpen.

* In alle andere gevallen `T` is toegestaan.

Het volgende diagram toont het sjabloonevaluatieproces:

![chlimage_1-176](assets/chlimage_1-176.png)

#### Sjablonen beperken die worden gebruikt in onderliggende pagina&#39;s {#limiting-templates-used-in-child-pages}

Als u wilt beperken welke sjablonen kunnen worden gebruikt om onderliggende pagina&#39;s onder een bepaalde pagina te maken, gebruikt u de opdracht `cq:allowedTemplates` eigenschap van `jcr:content` knooppunt van de pagina om de lijst op te geven met sjablonen die als onderliggende pagina&#39;s zijn toegestaan. Elke waarde in de lijst moet een absoluut pad zijn naar een sjabloon voor bijvoorbeeld een toegestane onderliggende pagina. `/apps/geometrixx/templates/contentpage`.

U kunt de `cq:allowedTemplates` eigenschap op de sjabloon  `jcr:content` knoop om deze configuratie toe te passen op alle pas gecreëerde pagina&#39;s die dit malplaatje gebruiken.

Als u meer beperkingen wilt toevoegen, bijvoorbeeld met betrekking tot de sjabloonhiërarchie, kunt u de opdracht `allowedParents/allowedChildren` eigenschappen op de sjabloon. U kunt dan uitdrukkelijk specificeren dat de pagina&#39;s die van een malplaatjeT worden gecreeerd ouderpagina/kinderen van pagina&#39;s moeten zijn die van een malplaatjeT worden gecreeerd.

## Sjablonen - Inhoudsfragmenten {#templates-content-fragments}

Zie [Sjablonen voor inhoudsfragmenten](/help/sites-developing/content-fragment-templates.md).
