---
title: Websitebeheer
seo-title: Websitebeheer
description: Leer hoe u meertalige websites beheert in AEM.
seo-description: Leer hoe u meertalige websites beheert in AEM.
uuid: a32d458b-a5ad-46ef-a68c-4717c63b4bdd
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: site-features
content-type: reference
discoiquuid: fabaa3e8-1657-4ed4-abb2-990117bec39c
translation-type: tm+mt
source-git-commit: 0885fb6eb6b6a6b8fefd522b2656c8f64e0a537e

---


# Websitebeheer{#website-administration}

De volgende beheergereedschappen zijn beschikbaar voor het beheer van websites en pagina&#39;s:

* Met MSM (Multi Site Manager) kunt u dezelfde site-inhoud op meerdere locaties gebruiken, terwijl variaties mogelijk zijn:

   * [Inhoud opnieuw gebruiken: Beheer van meerdere sites en Live Copy](/help/sites-administering/msm.md)

* Met vertaling kunt u de vertaling van pagina-inhoud, elementen en door de gebruiker gegenereerde inhoud automatiseren om meertalige websites te maken en te onderhouden:

   * [Inhoud vertalen voor meertalige sites](/help/sites-administering/translation.md)

* Deze twee functies kunnen worden gecombineerd om tegemoet te komen aan zowel [multinationale als meertalige](#multinational-and-multilingual-sites)websites.

## Meertalige en meertalige sites {#multinational-and-multilingual-sites}

U kunt op efficiënte wijze inhoud maken voor multinationale en meertalige sites door het gecombineerde gebruik van de Multi-Site Manager en de vertaalworkflow. Maak een stramiensite in één taal, voor een specifiek land, en gebruik die inhoud als basis voor de andere sites, waar nodig met vertaling:

* [Vertaal](/help/sites-administering/translation.md) de hoofdsite in verschillende talen.

* Gebruik [beheer](/help/sites-administering/msm.md) van meerdere sites om:

   * Gebruik inhoud van de hoofdsite en de vertalingen opnieuw om sites te maken voor andere landen en culturen.
   * Zorg ervoor dat u het gebruik van Multi-Site Manager beperkt tot inhoud binnen één taal, bijvoorbeeld Engelse master -> Engelse taalbijkantoren in landsites, Franse master -> Franse taalbijkantoren in landsites.
   * Koppel zo nodig elementen van de live kopieën los om lokalisatiegegevens toe te voegen.

In het volgende diagram ziet u hoe de hoofdconcepten elkaar snijden (maar niet alle niveaus/elementen in kwestie weergeven):

![chlimage_1-71](assets/chlimage_1-71a.png)

>[!NOTE]
>
>In dit, en vergelijkbaar, scenario&#39;s MSM beheert niet de verschillende taalversies als dusdanig.
>
>* [MSM](/help/sites-administering/msm.md) beheert de plaatsing van vertaalde inhoud van een blauwdruk (b.v. een globale meester) aan de levende exemplaren (b.v. de lokale plaatsen), binnen de grenzen van een taal.
>* Met de [vertaalintegratiemogelijkheden](/help/sites-administering/translation.md) van AEM, in combinatie met vertaalbeheerservices van derden, worden de talen beheerd en wordt inhoud in deze verschillende talen vertaald.
>
>
Voor geavanceerdere gebruiksgevallen kan MSM ook voor alle taalmeesters worden gebruikt.

>[!NOTE]
>
>Voor alle gebruiksgevallen is het raadzaam de volgende aanbevolen procedures te lezen:
>
>* [beste praktijken voor MSM](/help/sites-administering/msm-best-practices.md); met name:
   >
   >   
   * [Site maken](/help/sites-administering/msm-best-practices.md#create-site)
   >   * [MSM- en meertalige websites](/help/sites-administering/msm-best-practices.md#msm-and-multilingual-websites)
>
>* [Aanbevolen procedures voor vertaling](/help/sites-administering/tc-bp.md)

