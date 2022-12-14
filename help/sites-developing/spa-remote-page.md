---
title: De RemotePage-component
description: De component RemotePage is een aangepaste pagina-component voor het bewerken van SPA op afstand in AEM.
exl-id: 3f015997-0d42-4241-a890-0f16a19c5e34
source-git-commit: 41aac3b4ea3b100e9d927bef161929477d667a95
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# De RemotePage-component {#remote-page-component}

Wanneer u bepaalt welk integratieniveau u tussen uw externe SPA en AEM wilt hebben, is het vaak duidelijk dat u de SPA binnen AEM moet kunnen bekijken en bewerken. De component RemotePage is alleen voor dit doel een aangepaste pagina-component.

## Overzicht {#overview}

De component RemotePage haalt alle noodzakelijke activa van de geproduceerde toepassing `asset-manifest.json` en gebruikt dit voor het renderen van de SPA binnen AEM.

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

* De toepassing moet in een `<div id="root"></div>` onder het tekstelement. Als er een andere opmaak wordt verwacht voor de toepassing die moet worden geïnstantieerd, moet deze overeenkomstig worden aangepast in de HTML-scripts van de proxycomponent die een `sling:resourceSuperType="spa-project-core/components/remotepage`.

## Beperkingen {#limitations}

* De component RemotePage verwacht dat de implementatie activa-manifest zoals levert [hier gevonden.](https://github.com/shellscape/webpack-manifest-plugin) De component RemotePage, echter, is slechts getest om met het React kader (en Next.js via ver-pagina-volgende component) te werken, en daarom steunt ver het laden van toepassingen van andere kaders, zoals Angular niet.
* Interne CSS die is gedefinieerd in het hoofdbestand van de HTML van de toepassing en inline CSS op het basisknooppunt DOM zijn niet beschikbaar bij externe rendering in AEM.

## Technische details {#technical-details}

Net als de rest van het AEM SPA-project is de RemotePage-component een open bron. Voor de volledige technische details van de RemotePage-component, [zie gelieve de bewaarplaats GitHub.](https://github.com/adobe/aem-spa-project-core/tree/master/ui.apps/src/main/content/jcr_root/apps/spa-project-core/components/remotepage)
