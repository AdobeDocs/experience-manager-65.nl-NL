---
title: Websitebeheer
seo-title: Website Administration
description: Leer hoe u meertalige websites beheert met Adobe Experience Manager.
seo-description: Learn how to manage multilingual websites in AEM.
uuid: a32d458b-a5ad-46ef-a68c-4717c63b4bdd
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: site-features
content-type: reference
discoiquuid: fabaa3e8-1657-4ed4-abb2-990117bec39c
exl-id: 8f11f5de-f5af-4ce7-a448-2b4299de2930
source-git-commit: 10b370fd8f855f71c6d7d791c272137bb5e04d97
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Websitebeheer{#website-administration}

De volgende beheergereedschappen zijn beschikbaar voor het beheer van websites en pagina&#39;s:

* Met MSM (Multi Site Manager) kunt u dezelfde site-inhoud op meerdere locaties gebruiken, terwijl variaties mogelijk zijn:

   * [Inhoud opnieuw gebruiken: Sitebeheer en Live kopiëren](/help/sites-administering/msm.md)

* Met vertaling kunt u de vertaling van pagina-inhoud, elementen en door de gebruiker gegenereerde inhoud automatiseren om meertalige websites te maken en te onderhouden:

   * [Inhoud vertalen voor meertalige sites](/help/sites-administering/translation.md)

* Deze twee functies kunnen worden gecombineerd om te kunnen werken met websites die beide [Meertalig en meertalig](#multinational-and-multilingual-sites).

## Meertalige en meertalige sites {#multinational-and-multilingual-sites}

U kunt op efficiënte wijze inhoud maken voor multinationale en meertalige sites door het gecombineerde gebruik van de Multi-Site Manager en de vertaalworkflow. Maak een stramiensite in één taal, voor een specifiek land, en gebruik die inhoud als basis voor de andere sites, waar nodig met vertaling:

* [Vertalen](/help/sites-administering/translation.md) de hoofdsite in verschillende talen.

* Gebruiken [Beheer van meerdere sites](/help/sites-administering/msm.md) tot:

   * Gebruik inhoud van de hoofdsite en de vertalingen opnieuw om sites te maken voor andere landen en culturen.
   * Zorg ervoor dat u het gebruik van Multi-Site Manager beperkt tot inhoud binnen één taal, bijvoorbeeld Engelse master > Engelse taalvertakkingen in landsites, Franse master > Franse taalvertakkingen in landsites.
   * Koppel zo nodig elementen van de live kopieën los om lokalisatiegegevens toe te voegen.

In het volgende diagram ziet u hoe de hoofdconcepten elkaar snijden (maar niet alle niveaus/elementen in kwestie weergeven):

![Diagram dat belangrijkste concepten MSM en Vertaling toont](assets/chlimage_1-71a.png)

>[!NOTE]
>
>In dit, en vergelijkbaar, scenario&#39;s MSM beheert niet de verschillende taalversies als dusdanig.
>
>* [MSM](/help/sites-administering/msm.md) beheert de plaatsing van vertaalde inhoud van een blauwdruk (bijvoorbeeld, een globale meester) aan de levende exemplaren (bijvoorbeeld, de lokale plaatsen), binnen de grenzen van een taal.
>* De [vertalen](/help/sites-administering/translation.md) de integratiemogelijkheden van AEM, in combinatie met de vertaaldiensten van derden, beheren de talen en vertalen van inhoud in deze verschillende talen.
>
>Voor geavanceerdere gebruiksgevallen kan MSM ook voor alle taalmeesters worden gebruikt.

>[!NOTE]
>
>Voor alle gebruiksgevallen is het raadzaam de volgende aanbevolen procedures te lezen:
>
>* [Beste praktijken voor MSM](/help/sites-administering/msm-best-practices.md); met name:
>
>   * [Site maken](/help/sites-administering/msm-best-practices.md#create-site)
>   * [MSM- en meertalige websites](/help/sites-administering/msm-best-practices.md#msm-and-multilingual-websites)
>
>* [Aanbevolen procedures voor vertaling](/help/sites-administering/tc-bp.md)
