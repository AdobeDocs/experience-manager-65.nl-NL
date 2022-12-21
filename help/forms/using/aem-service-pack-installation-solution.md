---
title: CRX/bundle en de dienst van de pagina van het Begin niet beschikbare fouten zodra laatste 6.5.15.0 de dienstpak wordt geïnstalleerd
description: CRX/bundle en de dienst van de pagina van het Begin niet beschikbare fouten zodra laatste 6.5.15.0 de dienstpak wordt geïnstalleerd
source-git-commit: f5bf33e0a2ff73b8884a55bbe77e87ee991aeef9
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 1%

---


# Service niet-beschikbare fouten na installatie van AEM (6.5.15.0) servicepack {#steps-to-resolve-error-after-installing-service-pack}

## Probleem {#issue}

Nadat u de [AEM 6.5.15.0 servicepack](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.15.0.zip), treedt de fout op als:
* FOUT [FelixDispatchQueue] org.apache.sling.scripting.console FrameworkEvent ERROR (org.osgi.framework.BundleException: Kan org.apache.sling.scripting.console niet omzetten

Nadat u AEM 6.5.15.0-servicepack hebt geïnstalleerd, tonen de CRX/bundle en de startpagina de niet-beschikbare servicefouten.

## Oplossing {#solution}

>[!NOTE]
>
>De stappen voor het oplossen van problemen zijn van toepassing op alle toepassingsservers behalve JBoss EAP 7.4.

Na installatie [AEM 6.5.15.0 servicepack](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.15.0.zip)Als er op de CRX/bundle en de startpagina fouten optreden die niet beschikbaar zijn voor de service, voert u de volgende stappen uit:

1. Stop de toepassingsserver.
1. Ga naar `[aem-forms root]\crx-repository\launchpad\felix\bundle52`.
1. Zoek de `bundle.info` bestand.
1. Open de `bundle.info` bestand in een teksteditor en zoek naar de bundelnaam als `org.apache.felix.http.bridge`.

   >[!NOTE]
   >
   >Als de `bundle.info` krachtens `bundle52` bevat niet de `org.apache.felix.http.bridge` bundel, controleer het bundelaantal in vierkant haakje naast `org.apache.felix.http.bridge`. Navigeer vervolgens naar [basis van em-formulieren]\crx-repository\launchpad\felix\bundle[x] en voer de volgende stappen uit op deze locatie.

1. Ga naar URL: `[aem-forms root]\crx-repository\launchpad\felix\bundle[x]\version0.1`.
1. Zoeken naar `bundle.jar` en wijzigt u de naam van de `bundle.jar` tot `bundle.jar.bak`.
1. Kopiëren `bundle.jar` op deze locatie vanuit de [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/bundle.jar).
1. Start de toepassingsserver, wacht tot de logbestanden zijn gestabiliseerd en controleer de toestand van de bundel.
1. Wanneer alle bundels in de geactiveerde staat zijn, installeert u de `org.apache.felix.http.servlet-api-1.2.0_fragment-full.jar` servlet-fragment uit de `system/console/bundles` gedownload van [Softwaredistributie.](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/org.apache.felix.http.servlet-api-1.2.0_fragment_full.jar) en wacht tot de toepassingsserver is gestabiliseerd.
1. Stop de toepassingsserver.
1. Navigeren naar `[aem-forms root]\crx-repository\launchpad\felix\bundle52\version0.1` en de `bundle.jar`.
1. De naam van de `bundle.jar.bak` aan de `bundle.jar`.
1. Start de toepassingsserver.

## Van toepassing op {#applies-to}

Deze oplossing is van toepassing op:
* AEM Forms op alle JEE-servers, behalve op JBoss EAP 7.4.0
