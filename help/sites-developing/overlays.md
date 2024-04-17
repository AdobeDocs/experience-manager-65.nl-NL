---
title: Bedekkingen
description: Adobe Experience Manager gebruikt het principe van overlays om consoles en andere functies uit te breiden en aan te passen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
exl-id: e57a6971-6a6f-427b-a8cd-a2f2e8cdf9e2
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# Bedekkingen{#overlays}

Adobe Experience Manager (AEM) - en daarvoor heeft CQ - het principe van overlays al lang gebruikt om het [consoles](/help/sites-developing/customizing-consoles-touch.md) en andere functies (bijvoorbeeld [pagina&#39;s ontwerpen](/help/sites-developing/customizing-page-authoring-touch.md)).

Bedekking is een term die in veel contexten wordt gebruikt. In deze context (uitbreiding van AEM), betekent een bekleding om de vooraf bepaalde functionaliteit te nemen en uw eigen definities op te leggen over dat (om de standaardfunctionaliteit aan te passen).

In een standaardinstantie wordt de vooraf gedefinieerde functionaliteit onder gehouden `/libs` en het wordt aanbevolen om uw bedekking (aanpassingen) onder de `/apps` vertakking. AEM gebruikt een zoekpad om een bron te zoeken, waarbij u eerst de `/apps` vertakking en vervolgens de `/libs` vertakking [zoekpad kan worden geconfigureerd](#configuring-the-search-paths)). Dit mechanisme betekent dat uw bedekking (en de aanpassingen die daar worden bepaald) prioriteit heeft.

Sinds AEM 6.0 zijn wijzigingen aangebracht in de manier waarop overlays worden geïmplementeerd en gebruikt:

* AEM 6.0 en on - for [Graniet](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html)-gerelateerde overlays (d.w.z. de interface met aanraakbediening)

   * Methode

      * Reconstrueren de juiste `/libs` structuur onder `/apps`.

        Hiervoor is geen 1:1-kopie nodig, de [Samenvoeging van verkoopbronnen](/help/sites-developing/sling-resource-merger.md) wordt gebruikt voor kruisverwijzingen naar de oorspronkelijke definities die vereist zijn. De het Verdelen Fusie van het Middel verleent de diensten om tot middelen met (het onderscheiden) mechanismen toegang te hebben en samen te voegen.

      * Onder `/apps`, brengt u eventuele wijzigingen aan.

   * Voordelen

      * Meer robuust voor wijzigingen onder `/libs`.
      * Alleen opnieuw definiëren wat vereist is.

* Niet-graniet-overlays en -overlays voor AEM 6.0

   * Methode

      * De inhoud kopiëren vanuit `/libs` tot `/apps`

        Kopieer de volledige subvertakking, inclusief eigenschappen.

      * Onder `/apps`, brengt u eventuele wijzigingen aan.

   * Nadelen

      * Hoewel uw wijzigingen niet verloren gaan wanneer er iets verandert onder `/libs`, kan het zijn dat u bepaalde wijzigingen opnieuw moet aanbrengen die optreden in de bedekking onder `/apps`.

>[!CAUTION]
>
>De [Samenvoeging van verkoopbronnen](/help/sites-developing/sling-resource-merger.md) en de bijbehorende methoden mogen alleen worden gebruikt met [Graniet](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html). Dit betekent dat het maken van een bedekking met een skeletstructuur alleen geschikt is voor de standaardinterface met aanraakbediening.
>
>Bij overlays voor andere gebieden (inclusief de klassieke UI) worden het juiste knooppunt en de volledige substructuur gekopieerd en worden vervolgens de vereiste wijzigingen aangebracht.

Bedekkingen zijn de aanbevolen methode voor veel wijzigingen, zoals [configureren, consoles](/help/sites-developing/customizing-consoles-touch.md#create-a-custom-console) of [de selectiecategorie voor de middelenbrowser in het zijpaneel maken](/help/sites-developing/customizing-page-authoring-touch.md#add-new-selection-category-to-asset-browser) (wordt gebruikt bij het ontwerpen van pagina&#39;s). Zij zijn vereist als:

* ***Niet gebruiken* wijzigingen aanbrengen in de `/libs` vertakking **Alle wijzigingen die u aanbrengt, kunnen verloren gaan, omdat deze vertakking mogelijk wordt gewijzigd wanneer u:

   * upgrade uitvoeren op uw exemplaar
   * een hotfix toepassen
   * een functiepakket installeren

* Zij concentreren uw veranderingen in één plaats; makend het voor u gemakkelijker om, uw veranderingen te volgen, te migreren, file, of te zuiveren, zonodig.

## De zoekpaden configureren {#configuring-the-search-paths}

Voor bedekkingen is de geleverde bron een aggregaat van de opgehaalde bronnen en eigenschappen, afhankelijk van zoekpaden die kunnen worden gedefinieerd:

* De bron **Zoekpad omzetten** zoals gedefinieerd in het [OSGi-configuratie](/help/sites-deploying/configuring-osgi.md) voor de **Apache Sling Resource Resolver Factory**.

   * De top-down orde van onderzoekspaden wijst op hun respectieve prioriteiten.
   * In een standaardinstallatie zijn de primaire standaardwaarden `/apps`, `/libs` - dus de inhoud van `/apps` heeft een hogere prioriteit dan die van `/libs` (dat wil zeggen: *bedekkingen* het).

* Twee servicegebruikers hebben JCR nodig:ReAD toegang tot de locatie waar de scripts zijn opgeslagen. Deze gebruikers zijn: components-search-service (gebruikt door de componenten com.day.cq.wcm.coreto access/cache) en sling-scripting (gebruikt door org.apache.sling.servlets.resolver om servlets te zoeken).
* De volgende configuratie moet ook worden gevormd volgens waar u uw manuscripten (in dit voorbeeld onder /etc, /libs of /apps) zet.

  ```
  PID = org.apache.sling.jcr.resource.internal.JcrResourceResolverFactoryImpl
  resource.resolver.searchpath=["/etc","/apps","/libs"]
  resource.resolver.vanitypath.whitelist=["/etc/","/apps/","/libs/","/content/"]
  ```

* Tot slot moet de Resolver van Servlet ook worden gevormd (in dit voorbeeld, om /etc ook toe te voegen)

  ```
  PID = org.apache.sling.servlets.resolver.SlingServletResolver
  servletresolver.paths=["/bin/","/libs/","/apps/","/etc/","/system/","/index.servlet","/login.servlet","/services/"]
  ```

## Voorbeeld van gebruik {#example-of-usage}

Enkele voorbeelden worden behandeld wanneer:

* [De consoles aanpassen](/help/sites-developing/customizing-consoles-touch.md)
* [Paginaontwerp aanpassen](/help/sites-developing/customizing-page-authoring-touch.md)
