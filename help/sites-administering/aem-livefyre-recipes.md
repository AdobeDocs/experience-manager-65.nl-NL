---
title: AEM leverontvangers
seo-title: AEM Livefyre Recipes
description: Stapsgewijze instructies over gangbare gebruiksgevallen voor Adobe Experience Manager Livefyre.
seo-description: Step-by-step instructions on common use cases for Adobe Experience Manager Livefyre.
uuid: 78695a63-fca6-4990-9755-0aeaae4a7f64
contentOwner: alba
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: fdea5ede-d44f-463e-af8a-111ee7469ede
exl-id: 7ccd67a7-9945-48c1-9986-f4eaf0f2b961
source-git-commit: 63f066013c34a5994e2c6a534d88db0c464cc905
workflow-type: tm+mt
source-wordcount: '1503'
ht-degree: 0%

---

# AEM leverontvangers{#aem-livefyre-recipes}

Stapsgewijze instructies over gangbare gebruiksgevallen voor Adobe Experience Manager Livefyre.

## UGC krommen met de uit-van-de-doos AEM componenten en vertoning gebruikend de Muur van de Media van de Livefyre {#curate-ugc-using-the-out-of-the-box-livefyre-aem-components-and-display-using-livefyre-media-wall}

Media Wall streamt sociale en native Livefyre-inhoud naar een sociale muur in real time. Er zijn veelvoudige manieren om de Muur van Media in AEM afhankelijk van uw gebruiksgeval en vereisten uit te voeren.

Het AEM LiveCycle-pakket biedt een out-of-box implementatie, terwijl de traditionele integratie de mogelijkheid biedt om aangepaste Livefyre-AEM te maken.

### AEM integratie {#aem-integration}

Het Livefyre Adobe Experience Manager-pakket is beschikbaar voor AEM 6.1, 6.2SP1, 6.3, 6.4 en 6.4 SP1. AEM 5.x en 6.0 worden niet ondersteund. Zie voor gedetailleerde instructies [Integreren met Livefyre](https://helpx.adobe.com/experience-manager/6-4/sites/administering/using/livefyre.html).

Als u wilt zien welke LiveCyre-apps worden ondersteund, raadpleegt u de [Ondersteuningsmatrix AEM voor LiveCyre-apps](https://helpx.adobe.com/experience-manager/6-3/sites/administering/using/livefyre.html#AEMSupportMatrixforLivefyreApps).

### Traditionele implementatie (voor aangepaste AEM componenten) {#traditional-implementation-for-customized-aem-components}

Er zijn drie manieren om Livefy in een douane AEM component of andere CMSs zoals WordPress, Sitecore, of DemandWare uit te voeren. Een traditionele Livefyre-integratie is CMS agnostic.

**Methode 1: Designer-app-implementatie**

* **Wat:** Eenvoudige en snelste manier om een LiveCycle-app te integreren. U kunt een aangepaste JavaScript-insluitcode ontwerpen, configureren en genereren om een Media Wall-app op een pagina in minuten te integreren.
* **Hoe:**  [Een Media Wall-app maken, voorvertonen, publiceren en insluiten](https://experienceleague.adobe.com/docs/livefyre/using/apps/c-create-an-app.html)

* **Voorbeeld:** [https://codepen.io/dharafyre/pen/bvGrLo](https://codepen.io/dharafyre/pen/bvGrLo)

**Methode 2: SDK-implementatie**

* **Wat:** [Livefyre.js](https://experienceleague.adobe.com/docs/livefyre/implementation/c-livefyre_js.html) is de kernbibliotheek die Apps en Auth op een plaats macht. Het definieert de globale *window.Livefyre* object en één openbare methode; *Livefyre.require*, die kan worden gebruikt om andere LiveCycle JavaScript-bibliotheken te laden die u helpen bij het insluiten van LiveCycle-apps en de integratie met externe gebruikersauteplatforms.

* **Hoe**: [Gebruik het streamhub-wallpakket van de Livefyre JavaScript SDK](https://experienceleague.adobe.com/docs/livefyre/implementation/app-integrations/c-media-wall-integration.html)

* **Voorbeeld**: [https://codepen.io/dharafyre/pen/KZKBNv?editors=1010](https://codepen.io/dharafyre/pen/KZKBNv?editors=1010)

Voor geavanceerde aanpassingen met de SDK raadpleegt u [StreamHub SDKs](https://github.com/Livefyre/streamhub-sdk).

**Methode 3: API-implementatie**

* Voor het maken van aangepaste ervaringen en gegevensvisualisaties kunnen Livefyre-apps helemaal vanaf het begin worden gemaakt met behulp van de [Bootstrap- en Stream-API](https://experienceleague.adobe.com/docs/livefyre/implementation/advanced-topics/bootstrap-stream-api.html).

Zorg ervoor dat u volgt [Twitter](https://developer.twitter.com/en/developer-terms/display-requirements.html), [Facebook](https://en.facebookbrand.com/guidelines/brand), en [Instagram](https://en.instagram-brand.com/) weergaverichtlijnen bij het samenstellen van de gebruikersinterface voor UGC.

### Integratie van mediumwand {#media-wall-authentication-integration}

Voor de Integraties van de Muur van Media die authentificatie vereisen, gelieve te verwijzen naar:

* [Single Sign on Integration aanpassen](https://helpx.adobe.com/experience-manager/6-4/sites/administering/using/livefyre.html#CustomizeSingleSignonIntegration) voor AEM Identity Management
* [Identiteitsintegratie](https://experienceleague.adobe.com/docs/livefyre/implementation/identity-integration/t-about-identity-integration.html) voor externe verificatieplatforms

### Hoofdlettergebruik - overzicht {#use-case-overview}

Als AEM klant, wil ik UGC leiden gebruikend de uit-van-de-doos AEM componenten en vertoning gebruikend de Muur van de Media van de Livefyre:

Uitvoeringsmaatregelen:

1. [Aan de slag](https://helpx.adobe.com/experience-manager/6-3/sites/administering/using/livefyre.html)
1. [AEM configureren voor gebruik van Livefyre](https://helpx.adobe.com/experience-manager/6-3/sites/administering/using/livefyre.html)
1. [Sleep AEM Media Wall-component naar de pagina](https://helpx.adobe.com/experience-manager/6-3/sites/administering/using/livefyre.html#UseLivefyrewithAEMSites)
1. [Vorm Streams en voeg regels toe om UGC en vertoning op de component van de Muur van Media te leiden](https://experienceleague.adobe.com/docs/livefyre/using/streams/c-streams.html)

Ga voor trainingsvideo&#39;s over het streamen van UGC naar [Automatische inhoudsstromen maken en sociale inhoud zoeken in Adobe Experience Manager LiveCycle](https://helpx.adobe.com/experience-manager/tutorials.html).

### Voorbeelden van klanten {#customer-examples}

* [CNN Media Wall](https://edition.cnn.com/specials/nepal-earthquake-media-wall)
* [PGA-kleurendrukschijf](https://www.pgatour.com/social-hub.html)

Voor het maken van aangepaste ervaringen en gegevensvisualisaties kunnen Livefyre-apps helemaal vanaf het begin worden gemaakt met behulp van de [Bootstrap- en Stream-API](https://experienceleague.adobe.com/docs/livefyre/implementation/advanced-topics/bootstrap-stream-api.html).

Voor LiveCyre-toepassingen die verificatie vereisen, raadpleegt u [Identiteitsintegratie](https://experienceleague.adobe.com/docs/livefyre/implementation/identity-integration/t-about-identity-integration.html) voor externe verificatieplatforms.

* [PGA-kleurendrukschijf](https://www.pgatour.com/social-hub.html)
* [TimeOut](https://www.timeout.com/london/restaurants/forest-bar-kitchen#tab_panel_3)

## Livefyre-opmerkingen integreren met AEM of traditionele Livefyre-integratie {#integrate-livefyre-comments-using-aem-components-or-traditional-livefyre-integration}

### AEM integratie {#aem-integration-1}

Het Livefyre Adobe Experience Manager-pakket is beschikbaar voor AEM 6.1, 6.2SP1, 6.3, 6.4 en 6.4 SP1. AEM 5.x en 6.0 worden niet ondersteund. Zie voor gedetailleerde instructies [Integreren met Livefyre](https://helpx.adobe.com/experience-manager/6-4/sites/administering/using/livefyre.html).

### Traditionele implementatie (voor aangepaste AEM componenten) {#traditional-implementation-for-customized-aem-components-1}

Er zijn drie manieren om Livefyre Commentaar App in een douane AEM component of andere CMSs zoals WordPress, Sitecore, of DemandWare uit te voeren. Een traditionele Livefyre-integratie is CMS agnostic.

**Methode 1: Designer-app-implementatie**

* **Wat:** Eenvoudige en snelste manier om een LiveCycle-app te integreren. U kunt een aangepaste JavaScript-insluitcode ontwerpen, configureren en genereren om een Media Wall-app op een pagina in minuten te integreren.
* **Hoe:** [Een app voor opmerkingen maken, voorvertonen, publiceren en insluiten](https://experienceleague.adobe.com/docs/livefyre/using/apps/c-create-an-app.html)

* **Voorbeeld:** [https://codepen.io/dharafyre/pen/oYoJdP](https://codepen.io/dharafyre/pen/oYoJdP)

**Methode 2: SDK-implementatie**

* **Wat:** [Livefyre.js](https://experienceleague.adobe.com/docs/livefyre/implementation/c-livefyre_js.html) is de kernbibliotheek die Apps en Auth op een plaats macht. Het definieert de globale *window.Livefyre* object en één openbare methode; *Livefyre.require*, die kan worden gebruikt om andere LiveCycle JavaScript-bibliotheken te laden die u helpen bij het insluiten van LiveCycle-apps en de integratie met externe gebruikersauteplatforms.

* **Hoe:**

   * Een verzameling/app maken met [CollectionMeta-token](https://experienceleague.adobe.com/docs/livefyre/implementation/getting-started/implementation-process/c-collectionmeta-tokent.html).
   * Integreren [App met opmerkingen](https://experienceleague.adobe.com/docs/livefyre/implementation/app-integrations/comments/c-comments-integration.html) in sites die de codestructuur Livefyre.js gebruiken.

* **Voorbeeld:**  [https://codepen.io/dharafyre/pen/oYoJdP](https://codepen.io/dharafyre/pen/oYoJdP)

Voor geavanceerde aanpassingen met de SDK raadpleegt u [StreamHub SDKs](https://github.com/Livefyre/streamhub-sdk).

**Methode 3: API-implementatie**

* Voor het maken van aangepaste ervaringen en gegevensvisualisaties kunnen Livefyre-apps helemaal vanaf het begin worden gemaakt met behulp van de [Bootstrap- en Stream-API](https://experienceleague.adobe.com/docs/livefyre/implementation/advanced-topics/bootstrap-stream-api.html).

### Integratie van verificatie van opmerkingen {#comments-app-authentication-integration}

* [Single Sign on Integration aanpassen](https://helpx.adobe.com/experience-manager/6-4/sites/administering/using/livefyre.html#CustomizeSingleSignonIntegration) voor AEM Identity Management
* [Identiteitsintegratie](https://experienceleague.adobe.com/docs/livefyre/implementation/identity-integration/t-about-identity-integration.html) voor externe verificatieplatforms

### Voorbeelden van klanten {#customer-examples-1}

* [Poise (Kimberly Klark)](https://www.poise.com/en-us/advice-and-support/blog-and-podcast/blog/5-holiday-party-tips-for-managing-lbl)

## De Livefyre AEM Assets-integratie gebruiken om UGC te importeren in AEM Assets {#use-livefyre-aem-assets-integration-to-import-ugc-in-aem-assets}

**Livefyre Setup (voor UGC Curation and Rights Management):**

1. [Streams configureren en regels toevoegen om UGC aan LiveCycle Asset Library-mappen toe te voegen](https://experienceleague.adobe.com/docs/livefyre/using/streams/c-streams.html).

   1. Ga voor trainingsvideo&#39;s over het streamen van UGC naar [Automatische inhoudsstromen maken en sociale inhoud zoeken in Adobe Experience Manager LiveCycle](https://helpx.adobe.com/experience-manager/tutorials.html).

1. [Gelieerde UGC verzamelen, ordenen en beheren in mappen in de bibliotheek van Livefyre](https://experienceleague.adobe.com/docs/livefyre/using/library/assets/c-assets.html).

   1. Ga voor trainingsvideo&#39;s over het maken en beheren van mappen in de LiveCycle Studio Asset Library naar [Werken met middelen in Adobe Experience Manager Livefyre](https://helpx.adobe.com/experience-manager/tutorials.html).

1. [Rechten aanvragen voor cursieve UGC met gebruik van Livefyre Studio](https://experienceleague.adobe.com/docs/livefyre/using/rights-requests/c-how-requesting-rights-works.html).

**AEM instellen (voor het importeren van UGC naar AEM Assets):**

1. [Aan de slag](https://helpx.adobe.com/experience-manager/6-3/sites/administering/using/livefyre.html#GettingStarted)
1. [AEM configureren voor gebruik van Livefyre](https://helpx.adobe.com/experience-manager/6-3/sites/administering/using/livefyre.html#ConfigureAEMtouseLivefyre)
1. [UGC die door Livefyre in aan AEM Assets wordt beheerd importeren](https://helpx.adobe.com/experience-manager/6-3/sites/administering/using/livefyre.html#UseLivefyrewithAEMAssets)

* [Toerisme Australië](https://www.australia.com/en-us)

## LiveCyre Reviews integreren met AEM of traditionele LiveCyre-integratie {#integrate-livefyre-reviews-using-aem-components-or-traditional-livefyre-integration}

### AEM integratie {#aem-integration-2}

Het Livefyre Adobe Experience Manager-pakket is beschikbaar voor AEM 6.1, 6.2SP1, 6.3, 6.4 en 6.4 SP1. AEM 5.x en 6.0 worden niet ondersteund. Zie voor gedetailleerde instructies [Integreren met Livefyre](https://helpx.adobe.com/experience-manager/6-4/sites/administering/using/livefyre.html).

De Component Reviews is geen ondersteunde component voor AEM 6.1. Controleer de [AEM supportmatrix voor alle Livefyre-apps](https://helpx.adobe.com/experience-manager/6-3/sites/administering/using/livefyre.html#AEMSupportMatrixforLivefyreApps).

### Traditionele implementatie (voor aangepaste AEM componenten) {#traditional-implementation-for-customized-aem-components-2}

Er zijn twee manieren om de app van de Revisies van Livefy in een douane AEM component of andere CMSs zoals WordPress, Sitecore, of DemandWare uit te voeren. Een traditionele Livefyre-integratie is CMS agnostic.

**Methode 1: SDK-implementatie**

* **Wat:** [Livefyre.js](https://experienceleague.adobe.com/docs/livefyre/implementation/c-livefyre_js.html) is de kernbibliotheek die Apps en Auth op een plaats macht. Het definieert de globale *window.Livefyre* object en één openbare methode; *Livefyre.require*, die kan worden gebruikt om andere LiveCycle JavaScript-bibliotheken te laden die u helpen bij het insluiten van LiveCycle-apps en de integratie met externe gebruikersauteplatforms.

* **Hoe:**

   * De revisies maken [CollectionMeta-token](https://experienceleague.adobe.com/docs/livefyre/implementation/app-integrations/c-reviews-integration.html) om metagegevens op te geven die moeten worden opgeslagen in de verzameling Revisies.
   * Integreren [Revisies-app](https://experienceleague.adobe.com/docs/livefyre/implementation/app-integrations/c-reviews-integration.html) naar sites met de *Livefyre.js* codestructuur insluiten

* **Voorbeeld:**  [https://codepen.io/dharafyre/pen/GXgvvd](https://codepen.io/dharafyre/pen/GXgvvd)

Voor geavanceerde aanpassingen met de SDK raadpleegt u [StreamHub SDKs](https://github.com/Livefyre/streamhub-sdk).

**Methode 2: API-implementatie**

* Voor het maken van aangepaste ervaringen en gegevensvisualisaties kunnen LiveCyre-apps helemaal vanaf het begin worden gemaakt door LiveCycle- en sociale gegevens te gebruiken met de API voor Bootstrap en streamen.

Aanvullende beoordelingen en revisies-API&#39;s vindt u [hier](https://api.livefyre.com/docs/apis/by-category/ratings-and-reviews).

### Integratie van verificatie van opmerkingen {#comments-app-authentication-integration-1}

* [Single Sign on Integration aanpassen](https://helpx.adobe.com/experience-manager/6-4/sites/administering/using/livefyre.html#CustomizeSingleSignonIntegration) voor AEM Identity Management
* [Identiteitsintegratie](https://experienceleague.adobe.com/docs/livefyre/implementation/identity-integration/t-about-identity-integration.html) voor externe verificatieplatforms

### Voorbeelden van klanten {#customer-examples-2}

* [TimeOut](https://www.timeout.com/london/restaurants/forest-bar-kitchen#tab_panel_3)
* [myrecipes](https://www.myrecipes.com/recipe/shrimp-florentine-pasta)
