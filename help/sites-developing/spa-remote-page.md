---
title: De RemotePage-component
description: De component RemotePage is een aangepaste pagina-component voor het bewerken van SPA op afstand in AEM.
exl-id: 3f015997-0d42-4241-a890-0f16a19c5e34
translation-type: tm+mt
source-git-commit: a92358d187aa78e05dd9b5a7bd4ae14bf0972f62
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# De RemotePage-component {#remote-page-component}

Wanneer u bepaalt welk integratieniveau u tussen uw externe SPA en AEM wilt hebben, is het vaak duidelijk dat u de SPA binnen AEM moet kunnen bekijken en bewerken. De component RemotePage is alleen voor dit doel een aangepaste pagina-component.

## Overzicht {#overview}

De component RemotePage haalt alle noodzakelijke activa van de geproduceerde `asset-manifest.json` van de toepassing en gebruikt dit voor het teruggeven van de SPA binnen AEM.

* Met de RemotePage kunt u de scripts en stijlpagina&#39;s van een SPA in de hoofdtekst van een AEM Page-component injecteren.
* Met de Virtual Front Components kunt u secties markeren als bewerkbaar in AEM SPA Editor.
* Een SPA die op een ander domein wordt gehost, kan samen in AEM bewerkbaar worden gemaakt.

Zie het artikel [Een externe SPA bewerken in AEM](spa-edit-external.md) voor meer informatie over bewerkbare, externe SPA in AEM.

## Vereisten {#requirements}

* CORS in ontwikkeling inschakelen
* Externe URL configureren in Pagina-eigenschappen
* De SPA renderen in AEM
* De webtoepassing moet een bundler-elementmanifest gebruiken, zoals een van de volgende, en een bestand asset-manifest.json in de hoofdmap van het domein weergeven met een lijst in een entrypoints-eigenschap van alle CSS- en JS-bestanden die moeten worden geladen:
   * https://github.com/shellscape/webpack-manifest-plugin
   * https://github.com/webdeveric/webpack-assets-manifest
   * https://github.com/mugi-uno/parcel-plugin-bundle-manifest

   ![EnterPoint](assets/asset-manifest-entrypoints.png)

* De toepassing moet in een `<div id="root"></div>` onder het lichaamselement kunnen initialiseren. Als een andere prijsverhoging voor app wordt verwacht om te concretiseren, dan moet dit dienovereenkomstig in de manuscripten van HTML van de volmachtscomponent worden aangepast die `sling:resourceSuperType="spa-project-core/components/remotepage` heeft.

## Beperkingen {#limitations}

* De huidige implementatie van de component RemotePage ondersteunt alleen externe React-toepassingen.
* Interne CSS die is gedefinieerd in het HTML-hoofdbestand van de toepassing en inline CSS op het DOM-hoofdknooppunt zijn niet beschikbaar bij externe rendering in AEM.

## Technische details {#technical-details}

Net als de rest van het AEM SPA-project is de RemotePage-component een open bron. Voor de volledige technische details van de Component RemotePage, [te zien gelieve de bewaarplaats GitHub.](https://github.com/adobe/aem-spa-project-core/tree/master/ui.apps/src/main/content/jcr_root/apps/spa-project-core/components/remotepage)
