---
title: Brontoewijzing
description: Leer hoe u omleidingen, ijdelings-URL's en virtuele hosts voor Adobe Experience Manager definieert aan de hand van resourceretoewijzing.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
docset: aem65
feature: Configuring
exl-id: 3eebdd38-da5b-4c38-868a-22c3c7a97b66
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 0%

---

# Brontoewijzing{#resource-mapping}

Brontoewijzing wordt gebruikt om omleidingen, ijdelings-URL&#39;s en virtuele hosts voor Adobe Experience Manager (AEM) te definiëren.

U kunt bijvoorbeeld de volgende toewijzingen gebruiken:

* Alle aanvragen vooraf bevestigen met `/content` zodat de interne structuur verborgen is voor de bezoekers van uw website.
* Definieer een omleiding, zodat alle verzoeken aan de `/content/en/gateway` pagina van uw website wordt omgeleid naar `https://gbiv.com/`.

Eén mogelijke HTTP-toewijzing vooraf bepaalt alle aanvragen aan `localhost:4503` with `/content`. Een dergelijke afbeelding kan worden gebruikt om de interne structuur te verbergen voor bezoekers van de website, voor zover dat mogelijk is:

`localhost:4503/content/we-retail/en/products.html`

Te benaderen via:

`localhost:4503/we-retail/en/products.html`

Als de toewijzing automatisch het voorvoegsel toevoegt `/content` tot `/we-retail/en/products.html`.

>[!CAUTION]
>
>Vanity URLs steunt geen regex patronen.

>[!NOTE]
>
>Zie de documentatie over verkopers, en [Toewijzingen voor resolutie van bronnen](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) en [Bronnen](https://sling.apache.org/documentation/the-sling-engine/resources.html) voor nadere informatie.

## Definities voor weergavetoewijzing {#viewing-mapping-definitions}

De toewijzingen uit twee lijsten die de Resolver van het Middel JCR (top-down) evalueert om een gelijke te vinden.

Deze lijsten kunnen (samen met configuratiegegevens) onder de **JCR ResourceResolver** optie van de Felix-console, bijvoorbeeld `https://<*host*>:<*port*>/system/console/jcrresolver`:

* De configuratie toont de huidige configuratie (zoals die voor [Resolver Apache Sling-resource](/help/sites-deploying/osgi-configuration-settings.md#apacheslingresourceresolver)).

* De Test van de configuratie dit laat u een URL of middelweg ingaan. Klikken **Oplossen** of **Kaart** om te bevestigen hoe het systeem de ingang zal omzetten.

* **Resolver Map-items**
De lijst van ingangen die door de methodes ResourceResolver.resolve worden gebruikt om URLs aan Middelen in kaart te brengen.

* **Toewijzingskaartitems**
De lijst van ingangen die door de methodes ResourceResolver.map worden gebruikt om de Wegen van het Middel aan URLs in kaart te brengen.

De twee lijsten tonen diverse ingangen, met inbegrip van die die als gebreken door de toepassingen worden bepaald. Deze zijn vaak bedoeld om URL&#39;s voor de gebruiker te vereenvoudigen.

De lijsten vormen een paar **Patroon**, een reguliere expressie die overeenkomt met de aanvraag, met een **Vervanging** Hiermee definieert u de omleiding die moet worden toegepast.

Bijvoorbeeld:

**Patroon** `^[^/]+/[^/]+/welcome$`

Hiermee wordt het volgende geactiveerd:

**Vervanging** `/libs/cq/core/content/welcome.html`.

Een aanvraag doorsturen:

`https://localhost:4503/welcome` &quot;

Aan:

`https://localhost:4503/libs/cq/core/content/welcome.html`

Er worden nieuwe toewijzingsdefinities gemaakt in de repository.

>[!NOTE]
>
>Er zijn vele beschikbare middelen die helpen verklaren hoe te om regelmatige uitdrukkingen te bepalen. Bijvoorbeeld: [https://www.regular-expressions.info/](https://www.regular-expressions.info/).

### Toewijzingsdefinities maken in AEM {#creating-mapping-definitions-in-aem}

In een standaardinstallatie van AEM kunt u de map vinden:

`/etc/map/http`

Dit is de structuur die wordt gebruikt bij het definiëren van toewijzingen voor het HTTP-protocol. Overige mappen ( `sling:Folder`) kan worden gemaakt onder `/etc/map` voor andere protocollen die u in kaart wilt brengen.

#### Het vormen van Intern Redirect aan /content {#configuring-an-internal-redirect-to-content}

Om de afbeelding tot stand te brengen die om het even welk verzoek aan https://localhost:4503/ met prefixen `/content`:

1. Met CRXDE navigeert u naar `/etc/map/http`.

1. Een knooppunt maken:

   * **Type** `sling:Mapping`
Dit knooppunttype is bedoeld voor dergelijke afbeeldingen, hoewel het gebruik ervan niet verplicht is.

   * **Naam** `localhost_any`

1. Klikken **Alles opslaan**.
1. **Toevoegen** de volgende eigenschappen voor dit knooppunt:

   * **Naam** `sling:match`

      * **Type** `String`

      * **Waarde** `localhost.4503/`

   * **Naam** `sling:internalRedirect`

      * **Type** `String[]`

      * **Waarde** `/content/`

1. Klikken **Alles opslaan**.

Dit behandelt een verzoek zoals:
`localhost:4503/geometrixx/en/products.html`
alsof:
`localhost:4503/content/geometrixx/en/products.html`
is aangevraagd.

>[!NOTE]
>
>Zie [Bronnen](https://sling.apache.org/documentation/the-sling-engine/resources.html) in de Verschuivende Documentatie voor verdere informatie over de beschikbare hellingseigenschappen en hoe zij kunnen worden gevormd.

>[!NOTE]
>
>U kunt `/etc/map.publish` om de configuraties voor het publicatiemilieu te houden. Deze moeten worden gerepliceerd en de nieuwe locatie ( `/etc/map.publish`) geconfigureerd voor de **Toewijzingslocatie** van de [Resolver Apache Sling-resource](/help/sites-deploying/osgi-configuration-settings.md#apacheslingresourceresolver) van de publicatieomgeving.
