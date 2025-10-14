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
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# App-sjablonen en -componenten{#app-templates-and-components}

{{ue-over-mobile}}

Een malplaatje wordt gebruikt om een Pagina tot stand te brengen en bepaalt welke componenten binnen het geselecteerde werkingsgebied kunnen worden gebruikt. Een sjabloon is een hiërarchie van knooppunten die dezelfde structuur heeft als de pagina die moet worden gemaakt, maar zonder daadwerkelijke inhoud.

Elke Malplaatje stelt u met een selectie van componenten beschikbaar voor gebruik voor.

* De malplaatjes worden opgebouwd van [&#x200B; Componenten &#x200B;](/help/sites-developing/components.md);
* Componenten gebruiken widgets en staan toegang tot deze widgets toe. Deze worden gebruikt om de inhoud te renderen.

>[!NOTE]
>
>Leren hoe te om uw toepassing van Adobe Experience Manager (AEM) te ontwikkelen gebruikend CRXDE Lite, zie [&#x200B; Ontwikkelen met CRXDE Lite &#x200B;](/help/sites-developing/developing-with-crxde-lite.md).

Een sjabloon is de basis van een pagina.

Om een pagina tot stand te brengen, moet het malplaatje (knoop-boom **/apps/&lt;myapp>/templates/&lt;mytemplate>**) aan de overeenkomstige positie in plaats-boom worden gekopieerd: dit is wat gebeurt als een pagina gebruikend **wordt gecreeerd Websites** tabel.

Deze kopieeractie geeft de pagina ook zijn aanvankelijke inhoud (gewoonlijk Top-Level Inhoud slechts) en het bezit die:resourceType, de weg aan de paginacomponent plaatsen die wordt gebruikt om de pagina (alles in de kindknoop jcr:content) terug te geven.

## Structuur van een sjabloon {#structure-of-a-template}

Er zijn twee aspecten die in overweging moeten worden genomen:

* de structuur van de template zelf
* de structuur van de inhoud die wordt geproduceerd wanneer een sjabloon wordt gebruikt

Een Malplaatje wordt gecreeerd onder een knoop van type **cq:Malplaatje**.

Er kunnen verschillende eigenschappen worden ingesteld, met name:

* **jcr:titel** - titel voor het malplaatje; verschijnt in de dialoog wanneer het creëren van een pagina.
* **jcr:beschrijving** - beschrijving voor het malplaatje; verschijnt in de dialoog wanneer het creëren van een pagina.

Deze knoop bevat *jcr:content (cq:PageContent)* knoop die als basis voor de inhoudsknoop van resulterende pagina&#39;s wordt gebruikt. Dit verwijzingen, die *gebruiken sleept:resourceType*, de component die voor het teruggeven van de daadwerkelijke inhoud van een nieuwe pagina moet worden gebruikt.

>[!NOTE]
>
>Zie de volgende bronnen voor informatie over de basisbeginselen van sjablonen en componenten in AEM:
>
>* [&#x200B; Malplaatjes &#x200B;](/help/sites-developing/templates.md)
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
