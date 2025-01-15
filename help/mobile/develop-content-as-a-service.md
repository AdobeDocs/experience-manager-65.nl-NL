---
title: Inhoud leveren
description: Leer hoe u alle inhoud in Adobe Experience Manager kunt gebruiken om de beoogde app-ervaring te bieden.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
exl-id: 85e73679-684e-402f-8186-8b56d8bd9372
solution: Experience Manager
feature: Mobile
role: User
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '955'
ht-degree: 0%

---

# Inhoud leveren{#content-delivery}

{{ue-over-mobile}}

Mobiele apps moeten alle inhoud in AEM kunnen gebruiken als dat nodig is om de beoogde app-ervaring te bieden.

Dit omvat het gebruik van elementen, site-inhoud, CAAS-inhoud (over-the-air) en aangepaste inhoud die een eigen structuur kan hebben.

>[!NOTE]
>
>**over-de-Luchtinhoud** kan uit om het even welk hierboven door managers komen ContentSync. Het kan worden gebruikt om de verpakking en de levering in batches te verzenden via ritssluitingen en updates of dergelijke pakketten te onderhouden.

Er zijn drie belangrijke soorten materiaal die de Diensten van de Inhoud leveren:

1. **Assets**
1. **verpakte inhoud van HTML (HTML/CSS/JS)**
1. **Onafhankelijke inhoud van het Kanaal**

![ chlimage_1-154 ](assets/chlimage_1-154.png)

## Assets {#assets}

Verzamelingen van middelen zijn AEM constructies die verwijzingen naar andere verzamelingen bevatten.

Een inzameling van Activa kan door de Diensten van de Inhoud worden blootgesteld. Als u een elementverzameling aanroept in een aanvraag, wordt een object geretourneerd dat een lijst is met de elementen, inclusief de URL&#39;s. Assets is toegankelijk via een URL. De URL wordt opgegeven in een object. Bijvoorbeeld:

* Een pagina-entiteit retourneert de JSON (paginaobject) die een afbeeldingsverwijzing bevat. De afbeeldingsverwijzing is een URL die wordt gebruikt om het binaire element voor de afbeelding op te halen.
* Een verzoek om een lijst met elementen in een map retourneert de JSON met gegevens over alle entiteiten in die map. Deze lijst is een object. De JSON heeft URL-verwijzingen die worden gebruikt om het binaire element voor elk element in die map op te halen.

### Elementoptimalisatie {#asset-optimization}

Een belangrijke waarde van Content Services is de mogelijkheid om elementen te retourneren die voor het apparaat zijn geoptimaliseerd. Dit vermindert de lokale opslagbehoeften van apparaten en verbetert de prestaties van apps.

Elementoptimalisatie is een serverfunctie, gebaseerd op informatie die wordt verstrekt in de API-aanvraag. Waar mogelijk moeten de rendities van activa in de cache worden geplaatst, zodat soortgelijke verzoeken geen regeneratie van de uitvoering van activa vereisen.

### Assets Workflow {#assets-workflow}

De workflow voor elementen ziet er als volgt uit:

1. De Verwijzing van activa beschikbaar in AEM uit-van-de-doos
1. Een entiteit voor de inventarisatie van activa maken op basis van haar model
1. Entiteit bewerken

   1. Middelen of middelen verzamelen
   1. JSON-rendering aanpassen

Het volgende diagram toont het **Werkschema van de Verwijzing van Assets**:

![ chlimage_1-155 ](assets/chlimage_1-155.png)

### Assets beheren {#managing-assets}

De Diensten van de inhoud verleent toegang tot AEM-beheerde activa die niet door andere AEM inhoud kunnen worden van verwijzingen voorzien.

#### Bestaande beheerde Assets {#existing-managed-assets}

Een gebruiker van AEM Sites en Assets gebruikt AEM Assets om al zijn digitale materiaal voor alle kanalen te beheren. Ze ontwikkelen een systeemeigen mobiele app en moeten verschillende middelen gebruiken die door AEM Assets worden beheerd. Bijvoorbeeld logo&#39;s, achtergrondafbeeldingen en knoppictogrammen.

Momenteel worden deze verspreid over de Assets-opslagplaats. De bestanden waarnaar de toepassing moet verwijzen, zijn:

* /content/dam/geometrixx-outdoors/brand/logo_light.png
* /content/dam/geometrixx-outdoors/brand/logo_dark.png
* /content/dam/geometrixx-outdoors/styles/backgrounds/gray_blue.jpg
* /content/dam/geometrixx-outdoors/brand/icons/app/cart.png
* /content/dam/geometrixx-outdoors/brand/icons/app/home.png

#### Toegang tot CS Asset-entiteiten {#accessing-cs-asset-entities}

Laten we de stappen opzij zetten die aangeven hoe de pagina momenteel via de API beschikbaar is (deze wordt gedekt door de beschrijving van de AEM-interface) en aannemen dat deze is uitgevoerd. Elemententiteiten zijn gemaakt en toegevoegd aan de ruimte appImages. Er zijn extra mappen onder de ruimte gemaakt voor organisatiedoeleinden. De activa-entiteiten worden dus in het AEM JCR opgeslagen als:

* /content/entities/appImages/logos/logo_light
* /content/entities/appImages/logos/logo_black
* /content/entities/appImages/bkgnd/gray_blue
* /content/entities/appImages/icons/cart
* /content/entities/appImages/icons/home

#### Een lijst met beschikbare asset-entiteiten ophalen {#getting-a-list-of-available-asset-entities}

Een toepassingsontwikkelaar kan een lijst met beschikbare middelen krijgen door de activa te winnen entiteiten. Het de ruimteeindpunt van de Diensten van de Inhoud kan die informatie door de dienst API SDK verstrekken.

Het resultaat is een object in JSON-indeling dat een lijst met de elementen in de map &quot;icons&quot; bevat.

![ chlimage_1-156 ](assets/chlimage_1-156.png)

#### Een afbeelding ophalen {#getting-an-image}

JSON verstrekt een URL voor elk beeld dat door de Diensten van de Inhoud aan het beeld wordt geproduceerd.

Om het binaire getal voor de &quot;winkelwagentje&quot;-afbeelding op te halen, wordt de clientbibliotheek opnieuw gebruikt.

## Inhoud verpakte HTML {#packaged-html-content}

HTML-inhoud is nodig voor klanten die de lay-out van inhoud moeten behouden. Dit is handig voor native toepassingen die een webcontainer gebruiken - zoals een Cordova-webweergave - om de inhoud weer te geven.

AEM Content Services biedt HTML-inhoud aan de mobiele app via de API. Klanten die AEM inhoud als HTML willen blootstellen, kunnen een HTML-pagina-entiteit maken die naar de AEM inhoudsbron wijst.

De volgende opties worden overwogen:

* **Zip dossier:** om de beste kans te hebben om behoorlijk op het apparaat te tonen, de van verwijzingen voorzien materiaal-css van de pagina, JavaScript, activa, etc. zijn inbegrepen in één enkel samengeperst dossier met de reactie. De verwijzingen in de pagina van de HTML kunnen worden aangepast om een relatieve weg aan deze dossiers te gebruiken.
* **Streaming:** die manifest van de vereiste dossiers van AEM krijgen. Gebruik vervolgens dat manifest om alle bestanden (HTML, CSS, JS, enzovoort) met volgende aanvragen aan te vragen.

![ chlimage_1-157 ](assets/chlimage_1-157.png)

## Kanaalonafhankelijke inhoud {#channel-independent-content}

Kanaalonafhankelijke inhoud is een manier om AEM inhoudconstructies, zoals pagina&#39;s, toegankelijk te maken zonder dat u zich zorgen hoeft te maken over de lay-out, componenten of andere kanaalspecifieke informatie.

Deze inhoudentiteiten worden gegenereerd met behulp van een inhoudsmodel om de AEM structuren om te zetten in een JSON-indeling. De resulterende JSON-gegevens bevatten informatie over de gegevens van de inhoud die zijn losgekoppeld van de AEM opslagplaats. Dit omvat het retourneren van metagegevens en AEM verwijzingskoppelingen naar elementen en de relaties tussen inhoudsstructuren, waaronder de hiërarchie van entiteiten.

### Kanaalonafhankelijke inhoud beheren {#managing-channel-independent-content}

Inhoud kan op verschillende manieren aan de app worden toegevoegd.

1. GET-inhoud ZIPS via AEM over de lucht

   * Handlers voor het synchroniseren van inhoud kunnen het ZIP-pakket rechtstreeks bijwerken of door bestaande renderers van inhoud aan te roepen

      * Platform Handlers
      * AEM handlers
      * Aangepaste handlers

1. Inhoud rechtstreeks via inhoudrenderers GET

   * Out-of-the-box Default Sling Renderers
   * AEM Mobile/Content Services Content Renderers
   * Aangepaste rendering
