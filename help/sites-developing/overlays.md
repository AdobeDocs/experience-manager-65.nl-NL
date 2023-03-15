---
title: Bedekkingen
seo-title: Overlays
description: AEM gebruikt het principe van overlays om consoles en andere functies uit te breiden en aan te passen
seo-description: AEM uses the principle of overlays to allow you to extend and customize the consoles and other functionality
uuid: d14c08fe-04c0-4925-8c99-c6644357919d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: 0470b74c-2c34-4327-afed-b95eefb1d521
exl-id: e57a6971-6a6f-427b-a8cd-a2f2e8cdf9e2
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '606'
ht-degree: 0%

---

# Bedekkingen{#overlays}

AEM (en daarvoor, CQ) heeft het beginsel van overlays al lang gebruikt om u toe te staan de [consoles](/help/sites-developing/customizing-consoles-touch.md) en andere functies (bijvoorbeeld [pagina&#39;s ontwerpen](/help/sites-developing/customizing-page-authoring-touch.md)).

Bedekking is een term die in veel contexten kan worden gebruikt. In deze context (het uitbreiden van AEM) betekent een overlay het nemen van de vooraf bepaalde functionaliteit en het opleggen van uw eigen definities over dat (om de standaardfunctionaliteit aan te passen).

In een standaardinstantie wordt de vooraf gedefinieerde functionaliteit onder gehouden `/libs` en het wordt aanbevolen om uw bedekking (aanpassingen) onder de `/apps` vertakking. AEM gebruikt een zoekpad om een bron te zoeken, waarbij u eerst de `/apps` vertakt en vervolgens `/libs` vertakking [zoekpad kan worden geconfigureerd](#configuring-the-search-paths)). Dit mechanisme betekent dat uw bedekking (en de aanpassingen die daar worden bepaald) prioriteit zal hebben.

Sinds AEM 6.0 zijn wijzigingen aangebracht in de manier waarop overlays worden geïmplementeerd en gebruikt:

* AEM 6.0 vanaf - voor [Graniet](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html)gerelateerde overlays (d.w.z. de interface met aanraakbediening)

   * Methode

      * Reconstrueren `/libs` structuur onder `/apps`.

         Hiervoor is geen 1:1-kopie nodig, de [Samenvoegen van verkoopbronnen](/help/sites-developing/sling-resource-merger.md) wordt gebruikt voor kruisverwijzingen naar de oorspronkelijke definities die vereist zijn. De het Verdelen Fusie van het Middel verleent de diensten om tot middelen toegang te hebben en samen te voegen door (het differentiëren) mechanismen af te schilderen.

      * Breng eventuele wijzigingen aan onder `/apps`.
   * Voordelen

      * Meer robuust voor wijzigingen onder `/libs`.
      * Alleen opnieuw definiëren wat werkelijk vereist is.


* Niet-graniet-overlays en -overlays vóór AEM 6.0

   * Methode

      * Inhoud kopiëren uit `/libs` tot `/apps`

         U moet de gehele subvertakking kopiëren, inclusief de eigenschappen.

      * Breng eventuele wijzigingen aan onder `/apps`.
   * Nadelen

      * Hoewel uw wijzigingen niet verloren gaan wanneer er iets verandert onder `/libs`, kan het zijn dat u bepaalde wijzigingen opnieuw moet aanbrengen die optreden in de bedekking onder `/apps`.


>[!CAUTION]
>
>De [Samenvoegen van verkoopbronnen](/help/sites-developing/sling-resource-merger.md) en de bijbehorende methoden mogen alleen worden gebruikt met [Graniet](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html). Dit betekent dat het maken van een bedekking met een skeletstructuur alleen geschikt is voor de standaardinterface met aanraakbediening.
>
>Bij overlays voor andere gebieden (waaronder de klassieke UI) worden het juiste knooppunt en de volledige substructuur gekopieerd en worden vervolgens de vereiste wijzigingen aangebracht.

Bedekkingen zijn de aanbevolen methode voor veel wijzigingen, zoals [configureren, consoles](/help/sites-developing/customizing-consoles-touch.md#create-a-custom-console) of [selectiecategorie maken voor de middelenbrowser in het zijpaneel](/help/sites-developing/customizing-page-authoring-touch.md#add-new-selection-category-to-asset-browser) (wordt gebruikt bij het ontwerpen van pagina&#39;s). Zij zijn vereist als:

* U ***mogen* wijzigingen aanbrengen in de `/libs` vertakking **Alle wijzigingen die u aanbrengt, kunnen verloren gaan, omdat deze vertakking mogelijk wordt gewijzigd wanneer u:

   * upgrade uitvoeren op uw exemplaar
   * hotfix toepassen
   * een functiepakket installeren

* Ze concentreren uw wijzigingen op één locatie. het voor u gemakkelijker maken om uw wijzigingen te volgen, te migreren, er een back-up van te maken en/of er fouten in op te sporen.

## De zoekpaden configureren {#configuring-the-search-paths}

Voor bedekkingen is de geleverde bron een aggregaat van de opgehaalde bronnen en eigenschappen, afhankelijk van zoekpaden die kunnen worden gedefinieerd:

* De bron **Zoekpad omzetten** zoals gedefinieerd in het [OSGi-configuratie](/help/sites-deploying/configuring-osgi.md) voor de **Apache Sling Resource Resolver Factory**.

   * De top-down orde van onderzoekspaden wijst op hun respectieve prioriteiten.
   * In een standaardinstallatie zijn de primaire standaardinstellingen `/apps`, `/libs` - dus de inhoud van `/apps` heeft een hogere prioriteit dan die van `/libs` (d.w.z. *bedekkingen* het).

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
