---
title: Brontoewijzing
seo-title: Brontoewijzing
description: Leer hoe te om omleidingen, ijdelheid URLs en virtuele gastheren voor AEM te bepalen door middel van middeltoewijzing.
seo-description: Leer hoe te om omleidingen, ijdelheid URLs en virtuele gastheren voor AEM te bepalen door middel van middeltoewijzing.
uuid: 2ca2d0e4-6f90-4ecc-82db-26991f08c66f
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
discoiquuid: 3582a4d8-a47b-467a-9e25-cb45f969ec93
docset: aem65
translation-type: tm+mt
source-git-commit: 44eb94b917fe88b7c90c29ec7da553e15be391db
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 0%

---


# Brontoewijzing{#resource-mapping}

De afbeelding van het middel wordt gebruikt om omleidingen, ijdelheid URLs en virtuele gastheren voor AEM te bepalen.

U kunt bijvoorbeeld de volgende toewijzingen gebruiken:

* Plaats een voorvoegsel voor alle aanvragen bij `/content`, zodat de interne structuur verborgen is voor de bezoekers van uw website.
* Definieer een omleiding zodat alle aanvragen naar de `/content/en/gateway`-pagina van uw website worden omgeleid naar `https://gbiv.com/`.

Één mogelijke afbeelding van HTTP prefixeert alle verzoeken aan `localhost:4503` met `/content`. Een dergelijke afbeelding kan worden gebruikt om de interne structuur te verbergen voor bezoekers van de website, voor zover dat mogelijk is:

`localhost:4503/content/we-retail/en/products.html`

die toegankelijk zijn via:

`localhost:4503/we-retail/en/products.html`

aangezien de afbeelding automatisch het voorvoegsel `/content` aan `/we-retail/en/products.html` toevoegt.

>[!CAUTION]
>
>Vanity URLs steunt geen regex patronen.

>[!NOTE]
>
>Zie de documentatie van het Schelpen, en [Toewijzingen voor Resolutie van het Middel](https://sling.apache.org/site/resources.html) en [Middelen](https://sling.apache.org/site/mappings-for-resource-resolution.html) voor verdere informatie.

## Definities {#viewing-mapping-definitions} voor weergavekoppeling

De toewijzingen uit twee lijsten die de Resolver van het Middel JCR (top-down) evalueert om een gelijke te vinden.

Deze lijsten kunnen (samen met configuratieinformatie) onder **JCR ResourceResolver** optie van de console van Felix worden bekeken; bijvoorbeeld `https://<*host*>:<*port*>/system/console/jcrresolver`:

* Configuratie
Toont de huidige configuratie (zoals die voor [Apache Sling Resource Resolver](/help/sites-deploying/osgi-configuration-settings.md#apacheslingresourceresolver) wordt bepaald).

* Configuratietest
Op deze manier kunt u een URL- of bronpad invoeren. Klik **Los** of **Kaart** om te bevestigen hoe het systeem de ingang zal omzetten.

* **Resolver Map**
IngangenDe lijst van ingangen die door de methodes worden gebruikt ResourceResolver.resolve om URLs aan Middelen in kaart te brengen.

* **Toewijzing van**
VermeldingenDe lijst van ingangen die door de methodes ResourceResolver.map worden gebruikt om de Wegen van het Middel aan URLs in kaart te brengen.

De twee lijsten bevatten verschillende items, waaronder items die door de toepassing(en) als standaardwaarden zijn gedefinieerd. Deze zijn vaak bedoeld om URL&#39;s voor de gebruiker te vereenvoudigen.

De lijsten koppelen een **Patroon**, een regelmatige uitdrukking die aan het verzoek wordt aangepast, met een **Vervanging** die de op te leggen omleiding bepaalt.

Bijvoorbeeld:

**Patroon** `^[^/]+/[^/]+/welcome$`

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

Dit is de structuur die wordt gebruikt bij het definiëren van toewijzingen voor het HTTP-protocol. Andere mappen ( `sling:Folder`) kunnen worden gemaakt onder `/etc/map` voor andere protocollen die u wilt toewijzen.

#### Het vormen van een Interne Omleiding aan /content {#configuring-an-internal-redirect-to-content}

Om de afbeelding tot stand te brengen die om het even welk verzoek aan https://localhost:4503/ met `/content` vooraf bepaalt:

1. Met behulp van CRXDE navigeert u naar `/etc/map/http`.

1. Een nieuw knooppunt maken:

   * **** `sling:Mapping`
TypeThis knooptype is voorgenomen voor dergelijke afbeeldingen, hoewel zijn gebruik niet verplicht is.

   * **Naam** `localhost_any`

1. Klik **Alles opslaan**.
1. **Voeg de volgende eigenschappen** toe aan dit knooppunt:

   * **Naam** `sling:match`

      * **Type** `String`

      * **Waarde** `localhost.4503/`
   * **Naam** `sling:internalRedirect`

      * **Type** `String`

      * **Waarde** `/content/`


1. Klik **Alles opslaan**.

Dit behandelt een verzoek zoals:
`localhost:4503/geometrixx/en/products.html`
alsof:
`localhost:4503/content/geometrixx/en/products.html`
is aangevraagd.

>[!NOTE]
>
>Zie [Middelen](https://sling.apache.org/site/mappings-for-resource-resolution.html) in de het Verdelen Documentatie voor verdere informatie over de beschikbare hellingseigenschappen en hoe zij kunnen worden gevormd.

>[!NOTE]
>
>U kunt `/etc/map.publish` gebruiken om de configuraties voor het publicatiemilieu te houden. Deze moeten vervolgens worden gerepliceerd en de nieuwe locatie ( `/etc/map.publish`) moet worden geconfigureerd voor de **Mapping Location** van de [Apache Sling Resource Resolver](/help/sites-deploying/osgi-configuration-settings.md#apacheslingresourceresolver) van de publicatieomgeving.

