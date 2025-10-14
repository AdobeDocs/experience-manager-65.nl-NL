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
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 0%

---

# Brontoewijzing{#resource-mapping}

Brontoewijzing wordt gebruikt om omleidingen, ijdelings-URL&#39;s en virtuele hosts voor Adobe Experience Manager (AEM) te definiëren.

U kunt bijvoorbeeld de volgende toewijzingen gebruiken:

* Plaats een voorvoegsel voor alle aanvragen bij `/content` , zodat de interne structuur verborgen is voor de bezoekers van uw website.
* Definieer een omleiding zodat alle aanvragen naar de pagina `/content/en/gateway` van uw website worden omgeleid naar `https://gbiv.com/` .

Een mogelijke HTTP-toewijzing vooraf bepaalt alle aanvragen aan `localhost:4503` met `/content` . Een dergelijke afbeelding kan worden gebruikt om de interne structuur te verbergen voor bezoekers van de website, voor zover dat mogelijk is:

`localhost:4503/content/we-retail/en/products.html`

Te benaderen via:

`localhost:4503/we-retail/en/products.html`

Als de toewijzing het voorvoegsel `/content` automatisch aan `/we-retail/en/products.html` toevoegt.

>[!CAUTION]
>
>Vanity URLs steunt geen regex patronen.

>[!NOTE]
>
>Zie de het Verdelen documentatie, en [&#x200B; Toewijzingen voor de Resolutie van het Middel &#x200B;](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) en [&#x200B; Middelen &#x200B;](https://sling.apache.org/documentation/the-sling-engine/resources.html) voor verdere informatie.

## Definities voor weergavetoewijzing {#viewing-mapping-definitions}

De toewijzingen uit twee lijsten die de Resolver van het Middel JCR (top-down) evalueert om een gelijke te vinden.

Deze lijsten kunnen (samen met configuratieinformatie) onder **JCR ResourceResolver** optie van de console van de Felix worden bekeken; bijvoorbeeld, `https://<*host*>:<*port*>/system/console/jcrresolver`:

* Configuratie
Toont de huidige configuratie (zoals die voor [&#x200B; Apache het Verdelen Resolver van het Middel &#x200B;](/help/sites-deploying/osgi-configuration-settings.md#apacheslingresourceresolver) wordt bepaald).

* Configuratietest
Hiermee kunt u een URL of een bronpad invoeren. Klik **oplossen** of **Kaart** om te bevestigen hoe het systeem de ingang zal omzetten.

* **Ingangen van de Kaart van de Resolver**
De lijst van ingangen die door de methodes ResourceResolver.resolve worden gebruikt om URLs aan Middelen in kaart te brengen.

* **de Berichten van de Kaart van de Toewijzing**
De lijst van ingangen die door de methodes ResourceResolver.map worden gebruikt om de Wegen van het Middel aan URLs in kaart te brengen.

De twee lijsten tonen diverse ingangen, met inbegrip van die die als gebreken door de toepassingen worden bepaald. Deze zijn vaak bedoeld om URL&#39;s voor de gebruiker te vereenvoudigen.

Het lijstpaar a **Patroon**, een regelmatige uitdrukking die aan het verzoek wordt aangepast, met a **Vervanging** die de op te leggen herleiding bepaalt.

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
>Er zijn vele beschikbare middelen die helpen verklaren hoe te om regelmatige uitdrukkingen te bepalen. Bijvoorbeeld, [&#x200B; https://www.regular-expressions.info/ &#x200B;](https://www.regular-expressions.info/).

### Toewijzingsdefinities maken in AEM {#creating-mapping-definitions-in-aem}

In een standaardinstallatie van AEM kunt u de map vinden:

`/etc/map/http`

Dit is de structuur die wordt gebruikt bij het definiëren van toewijzingen voor het HTTP-protocol. Andere mappen ( `sling:Folder`) kunnen onder `/etc/map` worden gemaakt voor alle andere protocollen die u wilt toewijzen.

#### Het vormen van Intern Redirect aan /content {#configuring-an-internal-redirect-to-content}

U kunt als volgt de toewijzing maken die een eventuele aanvraag vooraf instelt op https://localhost:4503/ met `/content` :

1. Als u CRXDE gebruikt, gaat u naar `/etc/map/http` .

1. Een knooppunt maken:

   * **Type** `sling:Mapping`
Dit knooppunttype is bedoeld voor dergelijke afbeeldingen, hoewel het gebruik ervan niet verplicht is.

   * **Naam** `localhost_any`

1. Klik **sparen allen**.
1. **voeg** de volgende eigenschappen aan deze knoop toe:

   * **Naam** `sling:match`

      * **Type** `String`

      * **Waarde** `localhost.4503/`

   * **Naam** `sling:internalRedirect`

      * **Type** `String[]`

      * **Waarde** `/content/`

1. Klik **sparen allen**.

Dit behandelt een verzoek zoals:
`localhost:4503/geometrixx/en/products.html`
alsof:
`localhost:4503/content/geometrixx/en/products.html`
is aangevraagd.

>[!NOTE]
>
>Zie [&#x200B; Middelen &#x200B;](https://sling.apache.org/documentation/the-sling-engine/resources.html) in de het Verdelen Documentatie voor verdere informatie over de beschikbare hellingseigenschappen en hoe zij kunnen worden gevormd.

>[!NOTE]
>
>U kunt `/etc/map.publish` gebruiken om de configuraties voor de publicatieomgeving te houden. Deze moeten worden gerepliceerd, en de nieuwe plaats ( `/etc/map.publish`) voor de **Plaats van de Afbeelding** van de [&#x200B; Apache het Verdelen Resolver van het Middel &#x200B;](/help/sites-deploying/osgi-configuration-settings.md#apacheslingresourceresolver) van het publicatiemilieu wordt gevormd.
