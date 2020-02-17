---
title: Inhoud leveren
seo-title: Inhoud leveren
description: 'null'
seo-description: 'null'
uuid: 1e7bea34-ca50-41ed-8295-fa182c27fa69
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
discoiquuid: 3d65cc6b-5721-472f-a805-588d50f3571b
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Inhoud leveren{#content-delivery}

>[!NOTE]
>
>Adobe adviseert gebruikend de Redacteur van het KUUROORD voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (b.v. Reageren) vereisen. [Meer](/help/sites-developing/spa-overview.md)informatie.

Mobiele apps moeten alle inhoud in AEM naar wens kunnen gebruiken om de beoogde app-ervaring te bieden.

Dit omvat het gebruik van elementen, site-inhoud, CAAS-inhoud (over-the-air) en aangepaste inhoud die een eigen structuur kan hebben.

>[!NOTE]
>
>**Over-the-air inhoud** kan uit om het even welk bovenstaand via handlers ContentSync komen. Het kan worden gebruikt voor het in batches verpakken en leveren via postzegels en voor het onderhouden van updates of dergelijke pakketten.

Er zijn drie belangrijke soorten materiaal die de Diensten van de Inhoud leveren:

1. **Activa**
1. **Verpakte HTML-inhoud (HTML/CSS/JS)**
1. **Kanaalonafhankelijke inhoud**

![chlimage_1-154](assets/chlimage_1-154.png)

## Activa {#assets}

Elementverzamelingen zijn AEM-constructies die verwijzingen naar andere verzamelingen bevatten.

Een inzameling van Activa kan door de Diensten van de Inhoud worden blootgesteld. Als u een elementverzameling aanroept in een aanvraag, wordt een object geretourneerd dat een lijst is met de elementen, inclusief de URL&#39;s. Elementen zijn toegankelijk via een URL. De URL wordt opgegeven in een object. Bijvoorbeeld:

* Een pagina-entiteit retourneert JSON (paginaobject) dat een afbeeldingsverwijzing bevat. De afbeeldingsverwijzing is een URL die wordt gebruikt om het binaire element voor de afbeelding op te halen.
* Een verzoek om een lijst met elementen in een map retourneert JSON met gegevens over alle entiteiten in die map. Deze lijst is een object. De JSON heeft URL-verwijzingen die worden gebruikt om het binaire element voor elk element in die map op te halen.

### Elementoptimalisatie {#asset-optimization}

Een belangrijke waarde van Content Services is de mogelijkheid om elementen te retourneren die voor het apparaat zijn geoptimaliseerd. Dit vermindert de lokale opslagbehoeften van apparaten en verbetert de prestaties van apps.

Asset optimization wordt een serverfunctie, gebaseerd op informatie die wordt verstrekt in de API-aanvraag. Waar mogelijk moeten de rendities van activa in de cache worden geplaatst, zodat soortgelijke verzoeken geen hergeneratie van de uitvoering van activa vereisen.

### Assets Workflow {#assets-workflow}

De workflow voor elementen ziet er als volgt uit:

1. Asset Reference available in AEM out-of-the-box
1. Entiteit voor de verwijzing van activa maken op basis van het model ervan
1. Entiteit bewerken

   1. Middel- of middelenverzameling selecteren
   1. JSON-rendering aanpassen

Het volgende diagram toont het Werkschema **van de Verwijzing van** Activa:

![chlimage_1-155](assets/chlimage_1-155.png)

### Elementen beheren {#managing-assets}

Met Content Services hebt u toegang tot door AEM beheerde middelen waarnaar niet door andere AEM-inhoud kan worden verwezen.

#### Bestaande beheerde middelen {#existing-managed-assets}

Een bestaande gebruiker van de Plaatsen en van Activa van AEM gebruikt activa om al hun digitaal materiaal voor alle kanalen te beheren. Ze ontwikkelen een systeemeigen mobiele app en moeten verschillende middelen gebruiken die door AEM Assets worden beheerd. Bijvoorbeeld logo&#39;s, achtergrondafbeeldingen, knoppictogrammen, enz.

Momenteel worden deze uitgespreid rond de gegevensopslagplaats van Activa. De bestanden waarnaar de app moet verwijzen, bevinden zich in:

* /content/dam/geometrixx-outdoors/brand/logo_light.png
* /content/dam/geometrixx-outdoors/brand/logo_dark.png
* /content/dam/geometrixx-outdoors/styles/backgrounds/gray_blue.jpg
* /content/dam/geometrixx-outdoors/brand/icons/app/cart.png
* /content/dam/geometrixx-outdoors/brand/icons/app/home.png

#### Toegang tot CS Asset-entiteiten {#accessing-cs-asset-entities}

Laten we de stappen opzij zetten die aangeven hoe de pagina momenteel via de API beschikbaar is (deze wordt gedekt door de beschrijving van de AEM-gebruikersinterface) en aannemen dat deze is uitgevoerd. Elemententiteiten zijn gemaakt en toegevoegd aan de ruimte appImages. Er zijn extra mappen onder de ruimte gemaakt voor organisatiedoeleinden. De activa-entiteiten worden dus in het JCR AEM opgeslagen als:

* /content/entities/appImages/logos/logo_light
* /content/entities/appImages/logos/logo_black
* /content/entities/appImages/bkgnd/gray_blue
* /content/entities/appImages/icons/cart
* /content/entities/appImages/icons/home

#### Een lijst met beschikbare elementen ophalen {#getting-a-list-of-available-asset-entities}

Een toepassingsontwikkelaar kan een lijst met beschikbare middelen krijgen door de activa te winnen entiteiten. Het de ruimteeindpunt van de Diensten van de Inhoud kan die informatie door de dienst API SDK van het Web verstrekken.

Het resultaat is een object in JSON-indeling dat een lijst met de elementen in de map &quot;icons&quot; bevat.

![chlimage_1-156](assets/chlimage_1-156.png)

#### Een afbeelding ophalen {#getting-an-image}

JSON verstrekt een URL voor elk beeld, dat door de Diensten van de Inhoud aan het beeld wordt geproduceerd.

Om het binaire getal voor de &quot;winkelwagentje&quot;-afbeelding op te halen, wordt de clientbibliotheek opnieuw gebruikt.

## HTML-inhoud in pakket {#packaged-html-content}

HTML-inhoud is nodig voor klanten die de lay-out van inhoud moeten behouden. Dit is handig voor native toepassingen die een webcontainer gebruiken - zoals een Cordova-webweergave - om de inhoud weer te geven.

AEM Content Services kan HTML-inhoud leveren aan de mobiele app via de API. Klanten die AEM-inhoud als HTML willen onthullen, maken een HTML-pagina-entiteit die naar de AEM-inhoudsbron verwijst.

De volgende opties worden overwogen:

* **** Zip-bestand: Om de beste kans te hebben om correct op het apparaat te tonen, al het van verwijzingen voorzien materiaal van de pagina - css, JavaScript, activa, etc. - wordt opgenomen in één gecomprimeerd bestand met het antwoord. De verwijzingen in de HTML-pagina worden aangepast om een relatief pad naar deze bestanden te gebruiken.
* **** Streaming: Een manifest ophalen van de vereiste bestanden van AEM. Vervolgens gebruikt u dat manifest om alle bestanden aan te vragen (HTML, CSS, JS, enz.) met latere verzoeken.

![chlimage_1-157](assets/chlimage_1-157.png)

## Kanaalonafhankelijke inhoud {#channel-independent-content}

Kanaalonafhankelijke inhoud is een manier om AEM-inhoudsconstructies - zoals pagina&#39;s - toegankelijk te maken zonder dat u zich zorgen hoeft te maken over de lay-out, componenten of andere kanaalspecifieke informatie.

Deze inhoudentiteiten worden gegenereerd met behulp van een inhoudsmodel om de AEM-structuren om te zetten in een JSON-indeling. De resulterende JSON-gegevens bevatten informatie over de gegevens van de inhoud, die is losgekoppeld van de AEM-opslagplaats. Dit omvat het retourneren van metagegevens en AEM-verwijzingskoppelingen naar elementen en de relaties tussen inhoudsstructuren, waaronder de hiërarchie van entiteiten.

### Kanaalonafhankelijke inhoud beheren {#managing-channel-independent-content}

Inhoud kan op verschillende manieren aan de app worden toegevoegd.

1. ZIPS-inhoud ophalen via AEM Over the Air

   * Handlers voor het synchroniseren van inhoud kunnen het ZIP-pakket rechtstreeks bijwerken of door bestaande renderers van inhoud aan te roepen

      * Platform Handlers
      * AEMM-handlers
      * Aangepaste handlers

1. Inhoud rechtstreeks ophalen via inhoudrenderers

   * Out-of-the-box Default Sling Renderers
   * AEM Mobile/Content Services Content Renderers
   * Aangepaste rendering

