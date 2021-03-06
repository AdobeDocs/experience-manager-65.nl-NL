---
title: Ontwerpmodus
seo-title: Ontwerpmodus
description: In de modus Ontwikkelaar wordt een zijpaneel geopend met verschillende tabbladen die een ontwikkelaar informatie geven over de huidige pagina
seo-description: In de modus Ontwikkelaar wordt een zijpaneel geopend met verschillende tabbladen die een ontwikkelaar informatie geven over de huidige pagina
uuid: 8301ab51-93d6-44f9-a813-ba7f03f54485
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
discoiquuid: 589e3a83-7d1a-43fd-98b7-3b947122829d
docset: aem65
translation-type: tm+mt
source-git-commit: ebf3f34af7da6b1a659ac8d8843152b97f30b652
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 0%

---


# Modus voor ontwikkelaar{#developer-mode}

Bij het bewerken van pagina&#39;s in AEM zijn verschillende [modi](/help/sites-authoring/author-environment-tools.md#modestouchoptimizedui) beschikbaar, waaronder de modus Ontwikkelaar. Hiermee wordt een zijpaneel geopend met verschillende tabbladen die een ontwikkelaar informatie geven over de huidige pagina. De drie tabbladen zijn:

* **[](#components)** Componenten voor het bekijken van structuur en prestatiesinformatie.
* **[Test](#tests)** voor het uitvoeren van tests en het analyseren van de resultaten.
* **[Er](#errors)** zijn fouten opgetreden.

Deze hulp een ontwikkelaar om:

* Detecteren: waaruit bestaan de pagina&#39;s?
* Foutopsporing: waar en wanneer gebeurt dat , wat op zijn beurt helpt om problemen op te lossen .
* Testen: gedraagt de toepassing zich zoals verwacht.

>[!CAUTION]
>
>Modus Ontwikkelaar:
>
>* Deze optie is alleen beschikbaar in de interface met aanraakbediening (wanneer u pagina&#39;s bewerkt).
>* Is niet beschikbaar op mobiele apparaten of kleine vensters op het bureaublad (vanwege ruimtebeperkingen).

   >
   >   
   * Dit gebeurt wanneer de breedte minder dan 1024 px is.
>* Is alleen beschikbaar voor gebruikers die lid zijn van de groep `administrators`.


>[!CAUTION]
>
>De wijze van de ontwikkelaar is slechts beschikbaar op een standaardauteursinstantie die niet de runtime-wijze van de nosamplcontent gebruikt.
>
>Indien vereist kan het voor gebruik worden gevormd:
>
>* op een instantie van de auteur die geen runtime van de Inhoud gebruikt
>* een publicatie-instantie

>
>
Het moet na gebruik opnieuw worden uitgeschakeld.

>[!NOTE]
>
>Zie het volgende:
>
>* Het artikel van de Kennisbank, [Oplossen van problemen AEM TouchUI kwesties](https://helpx.adobe.com/experience-manager/kb/troubleshooting-aem-touchui-issues.html), voor verdere uiteinden en hulpmiddelen.
>* AEM Gems-sessie over [AEM 6.0 Developer Mode](https://docs.adobe.com/content/ddc/en/gems/aem-6-0-developer-mode.html).

>



## Ontwerpmodus openen {#opening-developer-mode}

De modus Ontwikkelaar wordt als een zijpaneel ge??mplementeerd in de pagina-editor. Als u het deelvenster wilt openen, selecteert u **Developer** in de moduskiezer op de werkbalk van de pagina-editor:

![chlimage_1-11](assets/chlimage_1-11.png)

Het deelvenster bestaat uit twee tabbladen:

* **[Componenten](/help/sites-developing/developer-mode.md#components)**  - Dit toont een componentstructuur, vergelijkbaar met de  [inhoudslijn ](/help/sites-authoring/author-environment-tools.md#content-tree) voor auteurs

* **[Fouten](/help/sites-developing/developer-mode.md#errors)**  - Wanneer er problemen optreden, worden de details voor elke component weergegeven.

### Onderdelen {#components}

![chlimage_1-12](assets/chlimage_1-12.png)

Dit toont een componentenboom die:

* Hiermee wordt de keten van componenten en sjablonen die op de pagina worden weergegeven (SLY, JSP, enz.) weergegeven. De structuur kan worden uitgebreid om de context binnen de hi??rarchie te tonen.
* Geeft de computertijd aan de serverzijde weer die nodig is om de component te renderen.
* Hiermee kunt u de structuur uitvouwen en specifieke componenten in de structuur selecteren. De selectie biedt toegang tot componentdetails; zoals:

   * Pad naar opslagplaats
   * Koppelingen naar scripts (geopend in CRXDE Lite)

* Geselecteerde componenten (in de inhoudsstroom, aangegeven door een blauwe rand) worden gemarkeerd in de inhoudsstructuur (en andersom).

Dit kan helpen bij:

* Bepaal en vergelijk de rendertijd per component.
* Zie en begrijp de hi??rarchie.
* Begrijp en verbeter vervolgens de laadtijd van de pagina door langzame componenten te zoeken.

Elk componentitem kan worden weergegeven (bijvoorbeeld:

![chlimage_1-13](assets/chlimage_1-13.png)

* **Details** weergeven: een koppeling naar een lijst met:

   * alle componentscripts die worden gebruikt om de component te renderen.
   * het inhoudspad van de gegevensopslagruimte voor deze specifieke component.

   ![chlimage_1-14](assets/chlimage_1-14.png)

* **Script** bewerken: een koppeling die:

   * Hiermee wordt het componentscript in CRXDE Lite geopend.

* Door een componentitem uit te vouwen (pijlkop) kunt u ook het volgende weergeven:

   * De hi??rarchie binnen de geselecteerde component.
   * Renderingtijden voor de geselecteerde component afzonderlijk, eventuele afzonderlijke componenten die erin zijn genest en het gecombineerde totaal.

   ![chlimage_1-15](assets/chlimage_1-15.png)

>[!CAUTION]
>
>Sommige verbindingen richten aan manuscripten onder `/libs`. Deze zijn echter alleen ter referentie; u **mag niets onder `/libs` bewerken, omdat wijzigingen die u aanbrengt mogelijk verloren gaan.** Dit is toe te schrijven aan het feit dat deze tak aan veranderingen kan zijn wanneer u bevordert of een hotfix/eigenschappak toepast. Alle wijzigingen die u nodig hebt, moeten worden aangebracht onder `/apps`, zie [Bedekkingen en overschrijvingen](/help/sites-developing/overlays.md).

### Fouten {#errors}

![chlimage_1-16](assets/chlimage_1-16.png)

Hopelijk is het tabblad **Fouten** altijd leeg (zoals hierboven), maar wanneer problemen optreden, worden de volgende details voor elke component weergegeven:

* Een waarschuwing als de component een ingang aan het foutenlogboek, samen met details van de fout en directe verbindingen aan de aangewezen code binnen CRXDE Lite schrijft.
* Een waarschuwing als de component een beheersessie opent.

Bijvoorbeeld, in een situatie waar een ongedefinieerde methode wordt geroepen, zal de resulterende fout op **Fouten** tabel worden getoond:

![chlimage_1-17](assets/chlimage_1-17.png)

Het componentitem in de structuur van het tabblad Componenten wordt ook gemarkeerd met een indicator wanneer een fout optreedt.

### Tests {#tests}

>[!CAUTION]
>
>In AEM 6.2 werden de testfuncties van de modus Ontwikkelaar opnieuw ge??mplementeerd als een zelfstandige toepassing Tools.
>
>Zie [Uw interface testen](/help/sites-developing/hobbes.md) voor meer informatie.

