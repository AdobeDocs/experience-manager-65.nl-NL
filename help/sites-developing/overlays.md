---
title: Bedekkingen
seo-title: Bedekkingen
description: AEM gebruikt het principe van overlays om consoles en andere functies uit te breiden en aan te passen
seo-description: AEM gebruikt het principe van overlays om consoles en andere functies uit te breiden en aan te passen
uuid: d14c08fe-04c0-4925-8c99-c6644357919d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: 0470b74c-2c34-4327-afed-b95eefb1d521
translation-type: tm+mt
source-git-commit: 5128a08d4db21cda821de0698b0ac63ceed24379
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 0%

---


# Bedekkingen{#overlays}

AEM (en daarvoor, CQ) heeft het beginsel van bekledingen lang gebruikt om u toe te staan om [consoles](/help/sites-developing/customizing-consoles-touch.md) en andere functionaliteit (bijvoorbeeld, [page authoring](/help/sites-developing/customizing-page-authoring-touch.md)) uit te breiden en aan te passen.

Bedekking is een term die in veel contexten kan worden gebruikt. In deze context (het uitbreiden van AEM) betekent een overlay het nemen van de vooraf bepaalde functionaliteit en het opleggen van uw eigen definities over dat (om de standaardfunctionaliteit aan te passen).

In een standaardinstantie wordt de vooraf gedefinieerde functionaliteit gehouden onder `/libs` en het wordt aanbevolen de overlay (aanpassingen) te definiëren onder de `/apps`-vertakking. AEM gebruikt een onderzoekspad om een middel te vinden, eerst zoekend `/apps` tak en toen `/libs` tak (de [onderzoekspad kan worden gevormd](#configuring-the-search-paths)). Dit mechanisme betekent dat uw bedekking (en de aanpassingen die daar worden bepaald) prioriteit zal hebben.

Sinds AEM 6.0 zijn wijzigingen aangebracht in de manier waarop overlays worden geïmplementeerd en gebruikt:

* AEM 6.0 en hoger - voor graniet[gerelateerde overlays (d.w.z. de interface met aanraakbediening)](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html)

   * Methode

      * Reconstrueer de aangewezen `/libs` structuur onder `/apps`.

         Dit vereist geen 1:1 exemplaar, [Sling het Samenvoegen van het Middel ](/help/sites-developing/sling-resource-merger.md) wordt gebruikt om de originele definities te verwijzen die worden vereist. De het Verdelen Fusie van het Middel verleent de diensten om tot middelen toegang te hebben en samen te voegen door (het differentiëren) mechanismen af te schilderen.

      * Breng eventuele wijzigingen aan onder `/apps`.
   * Voordelen

      * Meer robuust voor wijzigingen onder `/libs`.
      * Alleen opnieuw definiëren wat werkelijk vereist is.


* Niet-graniet-overlays en -overlays vóór AEM 6.0

   * Methode

      * Kopieer de inhoud van `/libs` naar `/apps`

         U moet de gehele subvertakking kopiëren, inclusief de eigenschappen.

      * Breng eventuele wijzigingen aan onder `/apps`.
   * Nadelen

      * Hoewel de wijzigingen niet verloren gaan wanneer iets verandert onder `/libs`, moet u mogelijk bepaalde wijzigingen opnieuw maken die voorkomen in de overlay onder `/apps`.


>[!CAUTION]
>
>De [Sling Resource Merger](/help/sites-developing/sling-resource-merger.md) en de verwante methoden kunnen alleen worden gebruikt met [Granite](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html). Dit betekent dat het maken van een bedekking met een skeletstructuur alleen geschikt is voor de standaardinterface met aanraakbediening.
>
>Bij overlays voor andere gebieden (waaronder de klassieke UI) worden het juiste knooppunt en de volledige substructuur gekopieerd en worden vervolgens de vereiste wijzigingen aangebracht.

Bedekkingen zijn de aanbevolen methode voor vele wijzigingen, zoals het configureren van de consoles[ of ](/help/sites-developing/customizing-consoles-touch.md#create-a-custom-console)het maken van uw selectiecategorie in de middelenbrowser in het zijpaneel[ (wordt gebruikt bij het ontwerpen van pagina&#39;s). ](/help/sites-developing/customizing-page-authoring-touch.md#add-new-selection-category-to-asset-browser) Zij zijn vereist als:

* U ***mag niet* wijzigingen aanbrengen in de `/libs`-vertakking **Alle wijzigingen die u aanbrengt, kunnen verloren gaan, omdat deze vertakking mogelijk wordt gewijzigd wanneer u:

   * upgrade uitvoeren op uw exemplaar
   * hotfix toepassen
   * een functiepakket installeren

* Ze concentreren uw wijzigingen op één locatie. het voor u gemakkelijker maken om uw wijzigingen te volgen, te migreren, er een back-up van te maken en/of er fouten in op te sporen.

## De zoekpaden configureren {#configuring-the-search-paths}

Voor bedekkingen is de geleverde bron een aggregaat van de opgehaalde bronnen en eigenschappen, afhankelijk van zoekpaden die kunnen worden gedefinieerd:

* De bron **Zoekpad voor oplosmiddel** zoals gedefinieerd in de [OSGi-configuratie](/help/sites-deploying/configuring-osgi.md) voor de **Apache Sling Resource Resolver Factory**.

   * De top-down orde van onderzoekspaden wijst op hun respectieve prioriteiten.
   * In een standaardinstallatie zijn de primaire standaardinstellingen `/apps`, `/libs` - dus heeft de inhoud van `/apps` een hogere prioriteit dan die van `/libs` (d.w.z. het *overlays* het).

* Twee servicegebruikers hebben JCR nodig:ReAD toegang tot de locatie waar de scripts zijn opgeslagen. Deze gebruikers zijn: components-search-service (gebruikt door de componenten com.day.cq.wcm.coreto access/cache) en sling-scripting (gebruikt door org.apache.sling.servlets.resolver om servlets te zoeken).
* De volgende configuratie moet ook worden gevormd volgens waar u uw manuscripten (in dit voorbeeld onder /etc, /libs of /apps) zet.

   ```
   PID = org.apache.sling.jcr.resource.internal.JcrResourceResolverFactoryImpl
   resource.resolver.searchpath=["/etc","/apps","/libs"]
   resource.resolver.vanitypath.whitelist=["/etc/","/apps/","/libs/","/content/"]
   ```

* Tot slot moet de Resolver van Servlet ook worden gevormd (in dit voorbeeld om /etc eveneens toe te voegen)

   ```
   PID = org.apache.sling.servlets.resolver.SlingServletResolver
   servletresolver.paths=["/bin/","/libs/","/apps/","/etc/","/system/","/index.servlet","/login.servlet","/services/"]
   ```

## Voorbeeld van gebruik {#example-of-usage}

Enkele voorbeelden worden behandeld wanneer:

* [De consoles aanpassen](/help/sites-developing/customizing-consoles-touch.md)
* [Paginaontwerp aanpassen](/help/sites-developing/customizing-page-authoring-touch.md)

