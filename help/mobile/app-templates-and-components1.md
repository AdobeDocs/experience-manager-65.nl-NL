---
title: App-sjablonen en -componenten
seo-title: App-sjablonen en -componenten
description: Volg deze pagina voor meer informatie over App Templates en Components. Deze biedt gedetailleerde informatie over de structuur van sjablonen.
seo-description: Volg deze pagina voor meer informatie over App Templates en Components. Deze biedt gedetailleerde informatie over de structuur van sjablonen.
uuid: ba2fd91b-de5a-4f39-a976-5455f9983669
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-on-demand-services-app
discoiquuid: 7f31c6a7-92d5-4a87-a9f0-68a82b834d5a
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 1%

---


# Toepassingssjablonen en -componenten{#app-templates-and-components}

>[!NOTE]
>
>Adobe raadt aan de SPA Editor te gebruiken voor projecten die renderen op basis van één pagina voor toepassingsframework op de client-side vereisen (bijvoorbeeld Reageren). [Meer](/help/sites-developing/spa-overview.md) informatie.

Een malplaatje wordt gebruikt om een Pagina tot stand te brengen en bepaalt welke componenten binnen het geselecteerde werkingsgebied kunnen worden gebruikt. Een sjabloon is een hiërarchie van knooppunten die dezelfde structuur heeft als de pagina die moet worden gemaakt, maar zonder daadwerkelijke inhoud.

Elke sjabloon bevat een selectie van componenten die beschikbaar zijn voor gebruik.

* Sjablonen zijn opgebouwd uit [Componenten](/help/sites-developing/components.md);
* Componenten gebruiken widgets en staan toegang tot deze widgets toe. Deze worden gebruikt om de inhoud te renderen.

>[!NOTE]
>
>Zie [Ontwikkelen met CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md) voor meer informatie over het ontwikkelen van uw AEM met CRXDE Lite.

Een sjabloon is de basis van een pagina.

Als u een pagina wilt maken, moet de sjabloon naar de corresponderende positie in de sitestructuur worden gekopieerd (knooppunt-boomstructuur **/apps/&lt;myapp>/templates/&lt;mytemplate>**): Dit gebeurt als een pagina wordt gemaakt met het tabblad **Websites**.

Deze kopieeractie geeft de pagina ook zijn aanvankelijke inhoud (gewoonlijk Top-Level Inhoud slechts) en het bezit die:resourceType, de weg aan de paginacomponent plaatsen die wordt gebruikt om de pagina (alles in de kindknoop jcr:content) terug te geven.

## Structuur van een sjabloon {#structure-of-a-template}

Er zijn twee aspecten die in overweging moeten worden genomen:

* de structuur van de template zelf
* de structuur van de inhoud die wordt geproduceerd wanneer een sjabloon wordt gebruikt

Een malplaatje wordt gecreeerd onder een knoop van type **cq:Malplaatje**.

Er kunnen verschillende eigenschappen worden ingesteld, met name:

* **jcr:title** - titel voor de sjabloon; wordt weergegeven in het dialoogvenster wanneer u een pagina maakt.
* **jcr:description** - description for the template; wordt weergegeven in het dialoogvenster wanneer u een pagina maakt.

Dit knooppunt bevat *a jcr:content (cq:PageContent)*-knooppunt dat wordt gebruikt als basis voor het inhoudsknooppunt van resulterende pagina&#39;s. deze verwijzingen, gebruikend *sling:resourceType*, de component die voor het teruggeven van de daadwerkelijke inhoud van een nieuwe pagina moet worden gebruikt.

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
* [Best practices voor](/help/mobile/best-practices-aem-mobile.md)
* [AEM Mobile Content Services ontwikkelen](//help/mobile/developing-content-services.md)

### Aanvullende bronnen {#additional-resources}

Raadpleeg de volgende koppelingen voor meer informatie over aanvullende onderwerpen op mobiele apps:

* [Mobiel met inhoudssynchronisatie](/help/mobile/mobile-ondemand-contentsync.md)
* [Mobiele apps testen](/help/mobile/develop-mobile-apps-testing.md)

