---
title: We.Retail Reference Implementation
seo-title: We.Retail Reference Implementation
description: We.Retail is een voorvertoning van een referentie-implementatie die de aanbevolen manier illustreert om een online aanwezigheid in te stellen met AEM
seo-description: We.Retail is een voorvertoning van een referentie-implementatie die de aanbevolen manier illustreert om een online aanwezigheid in te stellen met AEM
uuid: d8833192-b592-4812-bf9b-bd882e8ee7f0
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: f50150af-deff-4c29-bfe0-1cfc67b29d51
exl-id: 504c61c7-dcd3-412c-9239-d24a2b78e4b9
translation-type: tm+mt
source-git-commit: 1cef6f87fa66fd78d439c23e6ac907f9531b8fd6
workflow-type: tm+mt
source-wordcount: '779'
ht-degree: 3%

---

# We.Retail Reference Implementation{#we-retail-reference-implementation}

## Inleiding {#introduction}

Wij.Retail is een referentie-implementatie en voorbeeldinhoud die de aanbevolen manier illustreren om een online aanwezigheid met Adobe Experience Manager in te stellen.

Wij.Retail maakt gebruik van de nieuwste AEM technologieën zoals HTML, responsieve lay-outs, bewerkbare sjablonen, kerncomponenten en nog veel meer.

Hoewel het een verticale handelsversie illustreert, kan de manier waarop de site is ingesteld op elke verticale locatie worden toegepast en zijn alleen de productcatalogus en de winkelwagenfuncties specifiek voor de detailhandel.

## Functies {#features}

Als AEM standaardimplementatie van verwijzingen, toont Wij.Retail enkele van de krachtigste eigenschappen van AEM.

| **Functie** | **Beschrijving** | **Geïnteresseerd?** |
|---|---|---|
| [Globale sitestructuur](/help/sites-administering/tc-bp.md) | Wij.Retail omvat taalstramienen die live naar landspecifieke sites worden gekopieerd. | [Probeer het!](/help/sites-developing/we-retail-globalized-site-structure.md) |
| [Responsieve indeling](/help/sites-authoring/responsive-layout.md) | Alle pagina&#39;s hebben een responsieve indeling die zich dynamisch aanpast aan de grootte van het scherm en het apparaat. | [Probeer het!](/help/sites-developing/we-retail-responsive-layout.md) |
| [Bewerkbare sjablonen](/help/sites-developing/page-templates-editable.md) | Alle pagina&#39;s zijn gebaseerd op bewerkbare sjablonen, waarmee niet-ontwikkelaars de sjablonen kunnen aanpassen en aanpassen. | [Probeer het!](/help/sites-developing/we-retail-editable-templates.md) |
| [HTML-sjabloontaal](https://docs.adobe.com/content/help/en/experience-manager-htl/using/overview.html) | Alle componenten zijn gebaseerd op HTML |  |
| [eCommerce-mogelijkheden](/help/commerce/cif-classic/developing/ecommerce.md) | Functies van een productcatalogus |  |
| [Communitysites](/help/communities/overview.md) | Bezoekers toestaan deel te nemen aan discussies binnen gemeenschappen, blogs lezen en nog veel meer |  |
| [Kernonderdelen](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/introduction.html) | Alle componenten zijn gebaseerd op de nieuwe kerncomponenten en zijn bruikbaarder en gebruiker-configureerbaar uit-van-de-doos | [Probeer het!](/help/sites-developing/we-retail-core-components.md) |
| [Contentfragmenten](/help/assets/content-fragments/content-fragments.md) | In de sectie We.Retail-ervaringen wordt de kracht getoond van het hergebruiken van inhoud via inhoudsfragmenten. | [Probeer ze!](/help/sites-developing/we-retail-content-fragments.md) |
| [Ervaringsfragmenten](/help/sites-authoring/experience-fragments.md) | Een ervaringsfragment is een groep van een of meer componenten, inclusief inhoud en lay-out, waarnaar op pagina&#39;s kan worden verwezen. | [Probeer ze!](/help/sites-developing/we-retail-experience-fragments.md) |

## Aan de slag {#getting-started}

Wij.Detailhandel wordt geleverd als AEM voorbeeldinhoud. Om te gebruiken, eenvoudig [begin AEM aangezien u normaal ](/help/sites-deploying/deploy.md#getting-started) zou, ervoor zorgen dat de steekproefinhoud niet gehandicapt is.

>[!CAUTION]
>
>Wij.Detailhandel zou niet op productieinstanties moeten worden geïnstalleerd. Productieinstanties moeten worden gestart in `nosamplecontent` [runmode](/help/sites-deploying/configure-runmodes.md).

>[!CAUTION]
>
>We.Retail is gebaseerd op de nieuwste AEM technologie en biedt daarom geen ondersteuning voor [klassieke UI authoring](/help/sites-classic-ui-authoring/home.md).

### Laatste versie {#latest-version}

Hoewel wij.Retail met de AEM release wordt gedistribueerd, kunnen updates van de inhoud en de bijbehorende functies na de release worden uitgevoerd. Daarom is het mogelijk om [de recentste versie van GitHub](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/releases) en dan [upload](/help/sites-administering/package-manager.md#uploading-packages-from-your-file-system) en [install](/help/sites-administering/package-manager.md#installing-packages) als pakket op uw AEM instantie te downloaden.

### Eerste stappen {#first-steps}

1. Nadat AEM is gestart (en/of We.Retail is geïnstalleerd), is de site **We.Retail** beschikbaar in de [Siteconsole](/help/sites-authoring/basic-handling.md#global-navigation).
1. De volgende pagina kan bijvoorbeeld worden geopend en moet eruit zien zoals hieronder in [appendix](#appendix) wordt weergegeven:

   `https://<server name>:<port number>/editor.html/content/we-retail/language-masters/en.html`

## Wij.Detailhandel &amp; Geometrixx {#we-retail-geometrixx}

Geometrixx en zijn vele incarnaties dienden als steekproefinhoud in vroegere versies van AEM. Sinds versie 6.3, is Wij.Retail de steekproefinhoud geleverd met AEM en dient als nieuwe standaardverwijzingsimplementatie.

Wij.Detailhandel is technisch robuuster en maakt gebruik van de nieuwste AEM technologie om flexibeler en schaalbaarder te zijn, terwijl ook de nieuwste kenmerken van het product worden getoond.

### Vergelijking van functies {#feature-comparison}

De volgende lijst geeft een overzicht van belangrijkste eigenschappen die in Wij.Retail in vergelijking met Geometrixx beschikbaar zijn.

* **** Beschikbaar dat de voorbeelden van de eigenschap in de steekproefinhoud worden gevonden.
* **Niet** beschikbaar betekent dat voorbeelden van de functie niet beschikbaar zijn in de voorbeeldinhoud, maar niet dat de functie zelf niet beschikbaar is.

| **Functie** | **Wij.Detailhandel** | **Geometrixx** |
|---|---|---|
| Globale sitestructuur | Taalmasters worden live gekopieerd naar landspecifieke sites | Niet beschikbaar |
| Contentfragmenten | Beschikbaar | Niet beschikbaar |
| Ervaringsfragmenten | Beschikbaar | Niet beschikbaar |
| Responsieve lay-out | Voor alle pagina&#39;s | Alleen Geometrixx Media |
| Bewerkbare sjablonen | Voor alle pagina&#39;s | Niet beschikbaar |
| HTL | Alle componenten | Beperkt |
| Doelstelling | Voor alle pagina&#39;s | Alleen Geometrixx Outdoors |
| Schermen | Beschikbaar | Niet beschikbaar |
| Mobiel | Niet beschikbaar | Beschikbaar |
| Manuscripts | Niet beschikbaar | Beschikbaar |
| Carrousel, downloaden, diagramonderdelen | Niet beschikbaar | Beschikbaar |
| Kolombesturingselement | Vervangen door opmaakcontainer | Beschikbaar |
| Forms | Niet beschikbaar | Beschikbaar |
| Campagne | Geen e-mailvoorbeelden | Beschikbaar |

>[!NOTE]
>
>Deze lijst is volledig, maar mag niet als volledig worden beschouwd.

## Contribute {#contribute}

We.Retail is vrijgegeven als open-bronproject en de recentste versie van de broncode kan van GitHub worden gedownload.

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [Open aem-steekproef-wij-kleinhandelsproject op GitHub](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail)
* Het project downloaden als [een ZIP-bestand](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/archive/master.zip)

De nieuwste versie kan ook [direct worden gedownload](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/releases/latest) als een installable pakket.

Als u problemen ontmoet, gelieve [GitHub kwesties](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/issues) te behandelen.

Voel vrij om met [trekverzoeken](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/pulls) bij te dragen.

## Voorvertoning {#preview}

Voorbeeld van de welkomstpagina Web.Retail:

![screencapture-localhost-4502-editor-html-content-we-retail-us-en-html-2018-08-17-14_33_32](assets/screencapture-localhost-4502-editor-html-content-we-retail-us-en-html-2018-08-17-14_33_32.png)
