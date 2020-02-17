---
title: Brontoewijzing
seo-title: Brontoewijzing
description: Leer hoe u omleidingen, ijdelings-URL's en virtuele hosts voor AEM definieert met behulp van resourceretoewijzing.
seo-description: Leer hoe u omleidingen, ijdelings-URL's en virtuele hosts voor AEM definieert met behulp van resourceretoewijzing.
uuid: 2ca2d0e4-6f90-4ecc-82db-26991f08c66f
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
discoiquuid: 3582a4d8-a47b-467a-9e25-cb45f969ec93
docset: aem65
translation-type: tm+mt
source-git-commit: 44eb94b917fe88b7c90c29ec7da553e15be391db

---


# Brontoewijzing{#resource-mapping}

Brontoewijzing wordt gebruikt om omleidingen, ijdelings-URL&#39;s en virtuele hosts voor AEM te definiëren.

U kunt bijvoorbeeld de volgende toewijzingen gebruiken:

* Plaats een voorvoegsel voor alle aanvragen `/content` zodat de interne structuur verborgen is voor de bezoekers van uw website.
* Definieer een omleiding zodat alle aanvragen naar de `/content/en/gateway` pagina van uw website worden omgeleid naar `https://gbiv.com/`.

Eén mogelijke HTTP-toewijzing vooraf bepaalt alle aanvragen `localhost:4503` met `/content`. Een dergelijke afbeelding kan worden gebruikt om de interne structuur te verbergen voor bezoekers van de website, voor zover dat mogelijk is:

`localhost:4503/content/we-retail/en/products.html`

die toegankelijk zijn via:

`localhost:4503/we-retail/en/products.html`

aangezien de afbeelding automatisch het voorvoegsel `/content` aan toevoegt `/we-retail/en/products.html`.

>[!CAUTION]
>
>Vanity URLs steunt geen regex patronen.

>[!NOTE]
>
>Zie de het Verdelen documentatie, en [Toewijzingen voor de Resolutie](https://sling.apache.org/site/resources.html) van het Middel en [Middelen](https://sling.apache.org/site/mappings-for-resource-resolution.html) voor verdere informatie.

## Definities voor weergavetoewijzing {#viewing-mapping-definitions}

De toewijzingen uit twee lijsten die de Resolver van het Middel JCR (top-down) evalueert om een gelijke te vinden.

Deze lijsten kunnen (samen met configuratieinformatie) onder de optie **JCR ResourceResolver** van de console van Felix worden bekeken; bijvoorbeeld `https://<*host*>:<*port*>/system/console/jcrresolver`:

* ConfigurationShow de huidige configuratie (zoals die voor de [Apache Sling Resource Resolver](/help/sites-deploying/osgi-configuration-settings.md#apacheslingresourceresolver)wordt bepaald).

* TestThis van de configuratie staat u toe om een URL of middelweg in te gaan. Klik op **Oplossen** of **Kaart** om te bevestigen hoe het systeem de vermelding zal transformeren.

* **Resolver Kaartingangen** De lijst van ingangen die door de methodes ResourceResolver.resolve worden gebruikt om URLs aan Middelen in kaart te brengen.

* **De Vermeldingen** van de Kaart van de toewijzing De lijst van ingangen die door de methodes ResourceResolver.map worden gebruikt om de Wegen van het Middel aan URLs in kaart te brengen.

De twee lijsten bevatten verschillende items, waaronder items die door de toepassing(en) als standaardwaarden zijn gedefinieerd. Deze zijn vaak bedoeld om URL&#39;s voor de gebruiker te vereenvoudigen.

De lijsten koppelen een **Patroon**, een regelmatige uitdrukking aan het verzoek, met een **Vervanging** die de te plaatsen omleiding bepaalt.

Bijvoorbeeld:

**Patroon**`^[^/]+/[^/]+/welcome$`

wordt geactiveerd voor:

**Vervanging** `/libs/cq/core/content/welcome.html`.

om een verzoek om te leiden:

`https://localhost:4503/welcome` ``

tot:

`https://localhost:4503/libs/cq/core/content/welcome.html`

Er worden nieuwe toewijzingsdefinities gemaakt in de repository.

>[!NOTE]
>
>Er zijn vele beschikbare middelen die helpen verklaren hoe te om regelmatige uitdrukkingen te bepalen; bijvoorbeeld [https://www.regular-expressions.info/](https://www.regular-expressions.info/).

### Toewijzingsdefinities maken in AEM {#creating-mapping-definitions-in-aem}

In een standaardinstallatie van AEM kunt u de map vinden:

`/etc/map/http`

Dit is de structuur die wordt gebruikt bij het definiëren van toewijzingen voor het HTTP-protocol. Andere mappen ( `sling:Folder`) kunnen onder `/etc/map` voor andere protocollen worden gemaakt die u wilt toewijzen.

#### Het vormen van Interne Redirect aan /content {#configuring-an-internal-redirect-to-content}

Om de afbeelding tot stand te brengen die om het even welk verzoek aan https://localhost:4503/ met vooraf instelt `/content`:

1. Met behulp van CRXDE navigeert u naar `/etc/map/http`.

1. Een nieuw knooppunt maken:

   * **Type** `sling:Mapping`Dit knooptype is voorgenomen voor dergelijke afbeeldingen, hoewel zijn gebruik niet verplicht is.

   * **Naam**`localhost_any`

1. Klik op Alles **opslaan**.
1. **Voeg** de volgende eigenschappen aan dit knooppunt toe:

   * **Naam**`sling:match`

      * **Type**`String`

      * **Waarde**`localhost.4503/`
   * **Naam**`sling:internalRedirect`

      * **Type**`String`

      * **Waarde**`/content/`


1. Klik op Alles **opslaan**.

Dit behandelt een verzoek zoals:
`localhost:4503/geometrixx/en/products.html`alsof:
`localhost:4503/content/geometrixx/en/products.html`is verzocht.

>[!NOTE]
>
>Zie [Middelen](https://sling.apache.org/site/mappings-for-resource-resolution.html) in de het Verdelen Documentatie voor verdere informatie over de beschikbare hellingseigenschappen en hoe zij kunnen worden gevormd.

>[!NOTE]
>
>U kunt de configuraties voor het publicatiemilieu gebruiken `/etc/map.publish` om te houden. Deze moeten dan worden herhaald, en de nieuwe plaats ( `/etc/map.publish`) voor de Plaats **van de** Toewijzing van de Resolver [van het Middel van](/help/sites-deploying/osgi-configuration-settings.md#apacheslingresourceresolver) Apache het Verdelen van het Middel van het publiceert milieu wordt gevormd.

