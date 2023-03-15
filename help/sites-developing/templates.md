---
title: Sjablonen
seo-title: Templates
description: Sjablonen worden gebruikt bij het maken van een pagina die als basis voor de nieuwe pagina wordt gebruikt
seo-description: Templates are used when creating a page which will be used as the base for the new page
uuid: 6fa3dafc-dfa1-42d8-b296-d4be57449411
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: 7c723773-7c23-43d7-85dc-53e54556b648
legacypath: /content/docs/en/aem/6-1/develop/the-basics/templates
exl-id: 59f01bb1-4ff1-42b6-afc9-56d448b1f803
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '963'
ht-degree: 0%

---

# Sjablonen{#templates}

Sjablonen worden op verschillende punten in AEM gebruikt:

* Wanneer [een pagina maken die u nodig hebt om een sjabloon te selecteren](#templates-pages); dit wordt gebruikt als basis voor de nieuwe pagina . De sjabloon definieert de structuur van de resulterende pagina, eventuele initiële inhoud en de [componenten](/help/sites-authoring/default-components.md) die kunnen worden gebruikt (ontwerpeigenschappen).

* Wanneer [een inhoudsfragment maken dat u ook moet selecteren](#templates-content-fragments). Deze sjabloon definieert de structuur, initiële elementen en variaties.

De volgende sjablonen worden in detail besproken:

* [Paginasjablonen - Bewerkbaar](/help/sites-developing/page-templates-editable.md)
* [Paginasjablonen - statisch](/help/sites-developing/page-templates-static.md)
* [Sjablonen voor inhoudsfragmenten](/help/sites-developing/content-fragment-templates.md)
* [Adaptieve sjabloonrendering](/help/sites-developing/templates-adaptive-rendering.md)

## Sjablonen - Pagina&#39;s {#templates-pages}

AEM biedt nu twee basistypen sjablonen voor het maken van pagina&#39;s:

>[!NOTE]
>
>Als u een sjabloon gebruikt naar [een nieuwe pagina maken](/help/sites-authoring/managing-pages.md#creating-a-new-page) er is geen zichtbaar verschil (voor de auteur van de pagina) en er is geen aanduiding van het type sjabloon dat wordt gebruikt.

### Bewerkbare sjablonen {#editable-templates}

Bewerkbare sjablonen worden nu beschouwd als aanbevolen werkwijzen voor het ontwikkelen met AEM.

De voordelen van bewerkbare sjablonen:

* Kan [gemaakt](/help/sites-authoring/templates.md#creating-a-new-template-template-author) en [bewerkt](/help/sites-authoring/templates.md#editing-a-template-structure-template-author) door uw auteurs.

* Zijn geïntroduceerd zodat u het volgende kunt definiëren voor pagina&#39;s die met de sjabloon zijn gemaakt:

   * de structuur
   * de initiële inhoud
   * inhoudsbeleid

* Nadat de nieuwe pagina is gemaakt, wordt een dynamische verbinding onderhouden tussen de pagina en de sjabloon. dit betekent dat wijzigingen in de sjabloonstructuur worden doorgevoerd op alle pagina&#39;s die met die sjabloon worden gemaakt (wijzigingen in de oorspronkelijke inhoud worden niet doorgevoerd).
* Gebruikt het inhoudsbeleid (dat van de malplaatjeredacteur wordt uitgegeven) om de ontwerpeigenschappen (gebruikt niet de wijze van het Ontwerp binnen de paginaredacteur) voort te zetten.
* worden opgeslagen onder `/conf`
* Zie [Bewerkbare sjablonen](/help/sites-developing/page-templates-editable.md) voor nadere informatie.

>[!NOTE]
>
>Er is een AEM communautair artikel beschikbaar waarin wordt uitgelegd hoe u een site voor Experience Managers met bewerkbare sjablonen kunt ontwikkelen, raadpleegt u [Een Adobe Experience Manager 6.5-website maken met Bewerkbare sjablonen](https://helpx.adobe.com/experience-manager/using/first_aem64_website.html).

### Statische sjablonen {#static-templates}

Statische sjablonen:

* Moet door uw ontwikkelaars worden bepaald en worden gevormd.
* Dit was het oorspronkelijke sjabloonsysteem van AEM en is al in vele versies beschikbaar.
* Een statische sjabloon is een hiërarchie van knooppunten die dezelfde structuur heeft als de pagina die moet worden gemaakt, maar zonder daadwerkelijke inhoud.
* Wordt gekopieerd om de nieuwe pagina te maken. Hierna bestaat geen dynamische verbinding.
* Gebruiksmiddelen [Ontwerpmodus](/help/sites-authoring/default-components-designmode.md) om ontwerpeigenschappen te behouden.
* worden opgeslagen onder `/apps`
* Zie [Statische sjablonen](/help/sites-developing/page-templates-static.md) voor nadere informatie.

>[!NOTE]
>
>Vanaf AEM 6.5 wordt het gebruik van statische sjablonen niet als een goede praktijk beschouwd. Gebruik in plaats hiervan Bewerkbare sjablonen.
>
>[AEM Modernisering](modernization-tools.md) met gereedschappen kunt u migreren van statische naar bewerkbare sjablonen.

### Beschikbaarheid sjabloon {#template-availability}

>[!CAUTION]
>
>AEM biedt meerdere eigenschappen om de sjablonen te beheren die zijn toegestaan onder **Sites**. Het combineren ervan kan echter leiden tot zeer complexe regels die moeilijk te volgen en te beheren zijn.
>
>Daarom adviseert Adobe dat u eenvoudig begint, door te bepalen:
>
>* alleen `cq:allowedTemplates` eigenschap
>
>* alleen in de hoofdmap van de site
>
>Voor een voorbeeld, zie Wij.Retail: `/content/we-retail/jcr:content`
>
>De eigenschappen `allowedPaths`, `allowedParents`, en `allowedChildren` kan ook op de malplaatjes worden geplaatst om verfijndere regels te bepalen. Waar mogelijk is het echter *veel* eenvoudiger te definiëren `cq:allowedTemplates` eigenschappen op subsecties van de site als de toegestane sjablonen verder moeten worden beperkt.
>
>Een extra voordeel is dat de `cq:allowedTemplates` eigenschappen kunnen door een auteur worden bijgewerkt in het dialoogvenster **Geavanceerd** tabblad van het dialoogvenster **Pagina-eigenschappen**. De andere malplaatjeeigenschappen kunnen niet worden bijgewerkt gebruikend (standaard) UI, zodat zou een ontwikkelaar nodig hebben om de regels en een codeplaatsing voor elke verandering te handhaven.

Wanneer u een nieuwe pagina maakt in de interface voor sitebeheer, is de lijst met beschikbare sjablonen afhankelijk van de locatie van de nieuwe pagina en de plaatsingsbeperkingen die in elke sjabloon zijn opgegeven.

De volgende eigenschappen bepalen of een sjabloon `T` mag worden gebruikt voor een nieuwe pagina die als onderliggend item van pagina moet worden geplaatst `P`. Elk van deze eigenschappen is een tekenreeks met meerdere waarden die nul of meer reguliere expressies bevat die worden gebruikt voor overeenkomsten met paden:

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

Als u wilt beperken welke sjablonen kunnen worden gebruikt om onderliggende pagina&#39;s onder een bepaalde pagina te maken, gebruikt u de opdracht `cq:allowedTemplates` eigenschap van `jcr:content` knooppunt van de pagina om de lijst op te geven met sjablonen die als onderliggende pagina&#39;s zijn toegestaan. Elke waarde in de lijst moet een absoluut pad zijn naar een sjabloon voor een toegestane onderliggende pagina, bijvoorbeeld `/apps/geometrixx/templates/contentpage`.

U kunt de `cq:allowedTemplates` eigenschap op de sjabloon  `jcr:content` knoop om deze configuratie toe te passen op alle pas gecreëerde pagina&#39;s die dit malplaatje gebruiken.

Als u meer beperkingen wilt toevoegen, bijvoorbeeld met betrekking tot de sjabloonhiërarchie, kunt u de opdracht `allowedParents/allowedChildren` eigenschappen op de sjabloon. U kunt dan uitdrukkelijk specificeren dat de pagina&#39;s die van een malplaatjeT worden gecreeerd ouderpagina/kinderen van pagina&#39;s moeten zijn die van een malplaatjeT worden gecreeerd.

## Sjablonen - Inhoudsfragmenten {#templates-content-fragments}

Zie [Sjablonen voor inhoudsfragmenten](/help/sites-developing/content-fragment-templates.md) voor volledige informatie.
