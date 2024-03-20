---
title: Modus voor ontwikkelaars
description: In de modus Ontwikkelaar wordt een zijpaneel geopend met verschillende tabbladen die een ontwikkelaar informatie geven over de huidige pagina.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
docset: aem65
exl-id: aef0350f-4d3d-47f4-9c7e-5675efef65d9
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '683'
ht-degree: 0%

---

# Modus voor ontwikkelaars{#developer-mode}

Tijdens het bewerken van pagina&#39;s in Adobe Experience Manager (AEM), diverse [modi](/help/sites-authoring/author-environment-tools.md#modestouchoptimizedui) zijn beschikbaar, inclusief de modus Ontwikkelaar. Hiermee wordt een zijpaneel geopend met verschillende tabbladen die een ontwikkelaar informatie geven over de huidige pagina. De drie tabbladen zijn:

* **[Componenten](#components)** voor het bekijken van structuur en prestatiesinformatie.
* **[Tests](#tests)** voor het uitvoeren van tests en het analyseren van de resultaten.
* **[Fouten](#errors)** om eventuele problemen te zien.

Deze hulp een ontwikkelaar om:

* Detecteren: waaruit de pagina&#39;s bestaan.
* Foutopsporing: waar en wanneer gebeurt, wat op zijn beurt helpt om problemen op te lossen.
* Test: gedraagt de toepassing zich zoals verwacht.

>[!CAUTION]
>
>Modus Ontwikkelaar:
>
>* Deze optie is alleen beschikbaar in de interface met aanraakbediening (wanneer u pagina&#39;s bewerkt).
>* Is niet beschikbaar op mobiele apparaten of kleine vensters op het bureaublad (vanwege ruimtebeperkingen).
>
>   * Dit gebeurt wanneer de breedte minder dan 1024 px is.
>* Is alleen beschikbaar voor gebruikers die lid zijn van de `administrators` groep.

>[!CAUTION]
>
>De wijze van de ontwikkelaar is slechts beschikbaar op een standaardauteursinstantie die niet de runtime-wijze van de nosamplcontent gebruikt.
>
>Indien nodig, kan het voor gebruik worden gevormd:
>
>* op een instantie van de auteur die geen runtime van de Inhoud gebruikt
>* een publicatie-instantie
>
>Het moet na gebruik opnieuw worden uitgeschakeld.

>[!NOTE]
>
>Zie het volgende:
>
>* artikel in de kennisbank; [Problemen AEM TouchUI oplossen](https://helpx.adobe.com/experience-manager/kb/troubleshooting-aem-touchui-issues.html)voor meer tips en hulpmiddelen.
>* AEM Gems-sessie over [AEM 6.0 Developer Mode](https://experienceleague.adobe.com/docs/events/experience-manager-gems-recordings/gems2014/aem-developer-mode.html).
>

## Ontwerpmodus openen {#opening-developer-mode}

De modus Ontwikkelaar wordt als een zijpaneel geïmplementeerd in de pagina-editor. Als u het deelvenster wilt openen, selecteert u **Ontwikkelaar** in de moduskiezer op de werkbalk van de pagina-editor:

![chlimage_1-11](assets/chlimage_1-11.png)

Het deelvenster bestaat uit twee tabbladen:

* **[Componenten](/help/sites-developing/developer-mode.md#components)** - Dit toont een componentenboom, gelijkend op [inhoudsstructuur](/help/sites-authoring/author-environment-tools.md#content-tree) voor auteurs

* **[Fouten](/help/sites-developing/developer-mode.md#errors)** - Als er problemen optreden, worden de details voor elke component weergegeven.

### Onderdelen {#components}

![chlimage_1-12](assets/chlimage_1-12.png)

Dit toont een componentenboom die:

* Hiermee wordt de keten van componenten en sjablonen die op de pagina worden weergegeven (SLY, JSP enzovoort) omlijnd. De structuur kan worden uitgebreid om de context binnen de hiërarchie te tonen.
* Geeft de computertijd aan de serverzijde weer om de component te renderen.
* Hiermee kunt u de structuur uitvouwen en specifieke componenten in de structuur selecteren. De selectie biedt toegang tot componentdetails, zoals:

   * Pad naar opslagplaats
   * Koppelingen naar scripts (geopend in CRXDE Lite)

* Geselecteerde componenten (in de inhoudsstroom, aangegeven door een blauwe rand) worden gemarkeerd in de inhoudsstructuur (en omgekeerd).

Dit kan helpen bij:

* Bepaal en vergelijk de rendertijd per component.
* Zie en begrijp de hiërarchie.
* Begrijp en verbeter vervolgens de laadtijd van de pagina door langzame componenten te zoeken.

Elk componentitem kan worden weergegeven (bijvoorbeeld:

![chlimage_1-13](assets/chlimage_1-13.png)

* **Details weergeven**: een koppeling naar een lijst met:

   * alle componentscripts die worden gebruikt om de component te renderen.
   * het inhoudspad van de gegevensopslagruimte voor deze specifieke component.

  ![chlimage_1-14](assets/chlimage_1-14.png)

* **Script bewerken**: een koppeling die:

   * Hiermee wordt het componentscript in CRXDE Lite geopend.

* Door een componentitem uit te vouwen (pijlkop) kunt u ook het volgende weergeven:

   * De hiërarchie binnen de geselecteerde component.
   * Renderingtijden voor de geselecteerde component afzonderlijk, eventuele afzonderlijke componenten die erin zijn genest en het gecombineerde totaal.

  ![chlimage_1-15](assets/chlimage_1-15.png)

>[!CAUTION]
>
>Sommige koppelingen wijzen naar scripts onder `/libs`. Deze zijn echter uitsluitend ter referentie, u **mogen** alles onder bewerken `/libs`, omdat eventuele wijzigingen die u aanbrengt, verloren kunnen gaan. Dit komt doordat deze vertakking mogelijk verandert wanneer u een hotfix of functiepakket bijwerkt of toepast. Breng de wijzigingen aan die u onder `/apps`. Zie [Bedekkingen en overschrijvingen](/help/sites-developing/overlays.md).

### Fouten {#errors}

![chlimage_1-16](assets/chlimage_1-16.png)

Hopelijk **Fouten** tab is altijd leeg (zoals hierboven), maar wanneer er problemen optreden, worden de volgende details voor elke component weergegeven:

* Een waarschuwing als de component een ingang aan het foutenlogboek, samen met details van de fout en directe verbindingen aan de aangewezen code binnen CRXDE Lite schrijft.
* Een waarschuwing als de component een beheersessie opent.

Wanneer bijvoorbeeld een niet-gedefinieerde methode wordt aangeroepen, wordt de resulterende fout weergegeven in het dialoogvenster **Fouten** tab:

![chlimage_1-17](assets/chlimage_1-17.png)

Het componentitem in de structuur van het tabblad Componenten wordt ook gemarkeerd met een indicator wanneer een fout optreedt.

### Tests {#tests}

>[!CAUTION]
>
>In AEM 6.2 werden de testfuncties van de modus Ontwikkelaar opnieuw geïmplementeerd als een zelfstandige toepassing Tools.
>
>Zie voor meer informatie [Uw gebruikersinterface testen](/help/sites-developing/hobbes.md).
