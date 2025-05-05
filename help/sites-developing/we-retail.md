---
title: We.Retail Reference Implementation
description: We.Retail is een voorvertoning van een referentie-implementatie die de aanbevolen manier illustreert om een online aanwezigheid in AEM
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: 504c61c7-dcd3-412c-9239-d24a2b78e4b9
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: bf99ad3710638ec823d3b17967e1c750d0405c77
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 0%

---

# We.Retail Reference Implementation{#we-retail-reference-implementation}

## Inleiding {#introduction}

Wij.Retail is een referentie-implementatie en voorbeeldinhoud die de aanbevolen manier illustreren om een online aanwezigheid met Adobe Experience Manager in te stellen.

Wij.Retail gebruikt de nieuwste Adobe Experience Manager (AEM) technologieën zoals HTML, responsieve lay-outs, bewerkbare sjablonen, kerncomponenten en nog veel meer.

Hoewel het een verticale handelsversie illustreert, kan de manier waarop de site is ingesteld op elke verticale locatie worden toegepast, en zijn alleen de productcatalogus en de winkelwagenonderdelen specifiek.

## Functies {#features}

Als AEM standaard verwijzingsimplementatie, toont Wij.Retail enkele van de krachtigste eigenschappen van AEM.

| **Eigenschap** | **Beschrijving** | **Geïnteresseerd?** |
|---|---|---|
| [ Globalized plaatsstructuur ](/help/sites-administering/tc-bp.md) | Wij.Retail omvat taalstramienen die live naar landspecifieke sites worden gekopieerd. | [ probeer het!](/help/sites-developing/we-retail-globalized-site-structure.md) |
| [ Responsieve lay-out ](/help/sites-authoring/responsive-layout.md) | Alle pagina&#39;s hebben een responsieve indeling die dynamisch kan worden aangepast aan de grootte van het scherm en het apparaat. | [ probeer het!](/help/sites-developing/we-retail-responsive-layout.md) |
| [ Bewerkbare malplaatjes ](/help/sites-developing/page-templates-editable.md) | Alle pagina&#39;s zijn gebaseerd op bewerkbare sjablonen, waarmee niet-ontwikkelaars de sjablonen kunnen aanpassen en aanpassen. | [ probeer het!](/help/sites-developing/we-retail-editable-templates.md) |
| [ Taal van het Malplaatje van HTML ](https://experienceleague.adobe.com/nl/docs/experience-manager-htl/content/overview) | Alle componenten zijn gebaseerd op HTML |  |
| [ eCommerce mogelijkheden ](/help/commerce/cif-classic/developing/ecommerce.md) | Functies van een productcatalogus |  |
| [ de plaatsen van Gemeenschappen ](/help/communities/overview.md) | Bezoekers toestaan deel te nemen aan discussies binnen gemeenschappen, blogs lezen en nog veel meer |  |
| [ Componenten van de Kern ](https://experienceleague.adobe.com/nl/docs/experience-manager-core-components/using/introduction) | Alle componenten zijn gebaseerd op de nieuwe kerncomponenten en zijn bruikbaarder en gebruiker-configureerbaar uit-van-de-doos | [ probeer het!](/help/sites-developing/we-retail-core-components.md) |
| [Contentfragmenten](/help/assets/content-fragments/content-fragments.md) | In de sectie We.Retail-ervaringen wordt de kracht getoond om inhoud opnieuw te gebruiken als inhoudsfragmenten. | [ probeer hen!](/help/sites-developing/we-retail-content-fragments.md) |
| [Ervaringsfragmenten](/help/sites-authoring/experience-fragments.md) | Een ervaringsfragment is een groep van een of meer componenten, inclusief inhoud en lay-out, waarnaar op pagina&#39;s kan worden verwezen. | [ probeer hen!](/help/sites-developing/we-retail-experience-fragments.md) |

## Aan de slag {#getting-started}

Wij.Detailhandel wordt geleverd als AEM inhoud van het monster. Om te gebruiken, eenvoudig [ begin AEM aangezien u normaal ](/help/sites-deploying/deploy.md#getting-started) zou zijn, ervoor zorgen dat de steekproefinhoud niet gehandicapt is.

>[!CAUTION]
>
>Installeer We.Retail niet op productieexemplaren. De instanties van de productie zouden op `nosamplecontent` [ looppaswijze ](/help/sites-deploying/configure-runmodes.md) moeten zijn begonnen.

>[!CAUTION]
>
>Wij.Retail is gebaseerd op de recentste AEM technologie en steunt daarom niet [ klassieke UI authoring ](/help/sites-classic-ui-authoring/classic-page-author-first-steps.md).

### Laatste versie {#latest-version}

Hoewel wij.Retail met de AEM release wordt gedistribueerd, kunnen updates van de inhoud en de bijbehorende functies na de release worden uitgevoerd. Daarom is het mogelijk om [ de recentste versie van GitHub ](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/releases) te downloaden en dan [&#128279;](/help/sites-administering/package-manager.md#uploading-packages-from-your-file-system) te uploaden en [ te installeren ](/help/sites-administering/package-manager.md#installing-packages) het als pakket op uw AEM instantie.

### Eerste stappen {#first-steps}

1. Zodra AEM is begonnen (en/of Wij.Retail is geïnstalleerd), is de plaats **Wij.Retail** beschikbaar in de [ console van Plaatsen ](/help/sites-authoring/basic-handling.md#global-navigation).
1. Bijvoorbeeld, kan de volgende pagina worden geopend en het zou moeten kijken zoals getoond in [ bijlage ](#appendix) hieronder:

   `https://<server name>:<port number>/editor.html/content/we-retail/language-masters/en.html`

## Wij.Detailhandel &amp; Geometrixx {#we-retail-geometrixx}

Geometrixx en zijn vele incarnaties dienden als steekproefinhoud in vroegere versies van AEM. Sinds versie 6.3, is Wij.Retail de steekproefinhoud geleverd met AEM en dient als nieuwe standaardverwijzingsimplementatie.

Wij.Detailhandel is technisch robuuster en maakt gebruik van de nieuwste AEM technologie om flexibeler en schaalbaarder te zijn, terwijl ook de nieuwste kenmerken van het product worden getoond.

### Functievergelijking {#feature-comparison}

De volgende lijst geeft een overzicht van de belangrijkste eigenschappen die in Wij.Retail in vergelijking met Geometrixx beschikbaar zijn.

* **Beschikbaar** betekent dat de voorbeelden van de eigenschap in de steekproefinhoud worden gevonden.
* **niet beschikbaar** betekent dat de voorbeelden van de eigenschap niet beschikbaar in de steekproefinhoud zijn, maar betekent niet dat de eigenschap zelf niet is.

| **Eigenschap** | **Wij.Retail** | **Geometrixx** |
|---|---|---|
| Globale sitestructuur | Taalmasters worden live gekopieerd naar landspecifieke sites | Niet beschikbaar |
| Inhoudsfragmenten | Beschikbaar | Niet beschikbaar |
| Ervaar fragmenten | Beschikbaar | Niet beschikbaar |
| Responsieve lay-out | Voor alle pagina&#39;s | Alleen Geometrixx Media |
| Bewerkbare sjablonen | Voor alle pagina&#39;s | Niet beschikbaar |
| HTL | Alle componenten | Beperkt |
| Targeting | Voor alle pagina&#39;s | Alleen Geometrixx Outdoors |
| Screens | Beschikbaar | Niet beschikbaar |
| Mobiel | Niet beschikbaar | Beschikbaar |
| Manuscripts | Niet beschikbaar | Beschikbaar |
| Carousel-viewer, -downloads en -diagramonderdelen | Niet beschikbaar | Beschikbaar |
| Kolombesturingselement | Vervangen door opmaakcontainer | Beschikbaar |
| Forms | Niet beschikbaar | Beschikbaar |
| Campagne | Geen e-mailvoorbeelden | Beschikbaar |

>[!NOTE]
>
>Deze lijst is volledig, maar mag niet als volledig worden beschouwd.

## Contribute {#contribute}

We.Retail is vrijgegeven als open-bronproject en de recentste versie van de broncode kan van GitHub worden gedownload.

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden.

* [ open a-sample-wij-kleinhandelsproject op GitHub ](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail)
* Download het project als [ een dossier van het PIT ](https://codeload.github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/zip/refs/heads/master)

De recentste versie kan ook [ direct ](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/releases/tag/we.retail.reactor-4.0.0) als installable pakket worden gedownload.

Als u problemen ontmoet, dossier a [ GitHub kwestie ](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/issues).

Voel vrij om met [ trekkingsverzoeken ](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/pulls) bij te dragen.

## Voorvertoning {#preview}

Voorbeeld van de welkomstpagina Web.Retail:

![ screencapture-localhost-4502-editor-html-content-we-retail-us-nl-html-2018-08-17-14_33_32 ](assets/screencapture-localhost-4502-editor-html-content-we-retail-us-en-html-2018-08-17-14_33_32.png)
