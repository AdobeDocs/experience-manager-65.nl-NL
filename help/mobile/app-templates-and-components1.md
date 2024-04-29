---
title: App-sjablonen en -componenten
description: Volg deze pagina voor meer informatie over App Templates en Components. Deze biedt gedetailleerde informatie over de structuur van sjablonen.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-on-demand-services-app
exl-id: 58d95325-7cb1-4204-842d-17add70e1fbf
solution: Experience Manager
feature: Mobile
role: User
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# App-sjablonen en -componenten{#app-templates-and-components}

>[!NOTE]
>
>De Adobe adviseert het gebruiken van de SPARedacteur voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (bijvoorbeeld, Reageren) vereisen. [Meer informatie](/help/sites-developing/spa-overview.md).

Een malplaatje wordt gebruikt om een Pagina tot stand te brengen en bepaalt welke componenten binnen het geselecteerde werkingsgebied kunnen worden gebruikt. Een sjabloon is een hiërarchie van knooppunten die dezelfde structuur heeft als de pagina die moet worden gemaakt, maar zonder daadwerkelijke inhoud.

Elke Malplaatje stelt u met een selectie van componenten beschikbaar voor gebruik voor.

* Sjablonen zijn samengesteld uit [Componenten](/help/sites-developing/components.md);
* Componenten gebruiken widgets en staan toegang tot deze widgets toe. Deze worden gebruikt om de inhoud te renderen.

>[!NOTE]
>
>Ga voor meer informatie over het ontwikkelen van uw Adobe Experience Manager-toepassing (AEM) met behulp van CRXDE Lite naar [Ontwikkelen met CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md).

Een sjabloon is de basis van een pagina.

Als u een pagina wilt maken, moet de sjabloon worden gekopieerd (node-tree) **/apps/&lt;myapp>/templates/&lt;mytemplate>**) op de corresponderende positie in de sitestructuur: dit is wat er gebeurt als een pagina wordt gemaakt met de **Websites** tab.

Deze kopieeractie geeft de pagina ook zijn aanvankelijke inhoud (gewoonlijk Top-Level Inhoud slechts) en het bezit die:resourceType, de weg aan de paginacomponent plaatsen die wordt gebruikt om de pagina (alles in de kindknoop jcr:content) terug te geven.

## Structuur van een sjabloon {#structure-of-a-template}

Er zijn twee aspecten die in overweging moeten worden genomen:

* de structuur van de template zelf
* de structuur van de inhoud die wordt geproduceerd wanneer een sjabloon wordt gebruikt

Een malplaatje wordt gecreeerd onder een knoop van type **cq:sjabloon**.

Er kunnen verschillende eigenschappen worden ingesteld, met name:

* **jcr:titel** - titel voor de sjabloon; wordt weergegeven in het dialoogvenster wanneer u een pagina maakt.
* **jcr:beschrijving** - beschrijving voor de sjabloon; wordt weergegeven in het dialoogvenster wanneer u een pagina maakt.

Dit knooppunt bevat *a jcr:content (cq:PageContent)* knooppunt dat wordt gebruikt als basis voor het inhoudsknooppunt van de resulterende pagina&#39;s. Deze verwijzing, gebruiken *sling:resourceType*, de component die moet worden gebruikt voor het weergeven van de daadwerkelijke inhoud van een nieuwe pagina.

>[!NOTE]
>
>Zie de volgende bronnen voor informatie over de basisbeginselen van sjablonen en componenten in AEM:
>
>* [Sjablonen](/help/sites-developing/templates.md)
>* [Onderdelen](/help/sites-developing/components.md)
>

Nadat u het basisbegrip van Malplaatjes en Componenten hebt, zie de volgende middelen:

* [Sjablonen en componenten maken en toevoegen](/help/mobile/mobile-ondemand-app-templates.md)
* [Inhoud-eigenschappen gebruiken om inhoud te exporteren](/help/mobile/on-demand-content-properties-exporting.md)
* [Aanbevolen procedures](/help/mobile/best-practices-aem-mobile.md)
* [AEM Mobile Content Services ontwikkelen](/help/mobile/developing-content-services.md)

### Aanvullende bronnen {#additional-resources}

Raadpleeg de volgende koppelingen voor meer informatie over aanvullende onderwerpen op mobiele apps:

* [Mobiel met inhoudssynchronisatie](/help/mobile/mobile-ondemand-contentsync.md)
* [Mobiele apps testen](/help/mobile/develop-mobile-apps-testing.md)
