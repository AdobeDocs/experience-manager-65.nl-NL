---
title: Beheer en vertaling van meerdere sites
description: Leer hoe u uw inhoud kunt hergebruiken in uw project en meertalige websites in Adobe Experience Manager kunt beheren.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: site-features
content-type: reference
exl-id: 8f11f5de-f5af-4ce7-a448-2b4299de2930
solution: Experience Manager, Experience Manager Sites
feature: Multi Site Manager, Language Copy
role: Admin
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# Beheer en vertaling van meerdere sites {#msm-and-translation}

De volgende beheergereedschappen zijn beschikbaar voor het beheer van websites en pagina&#39;s:

* Met MSM (Multi Site Manager) kunt u dezelfde site-inhoud op meerdere locaties gebruiken, terwijl variaties mogelijk zijn:

   * [Inhoud opnieuw gebruiken: Sitebeheer en Live kopiëren](/help/sites-administering/msm.md)

* Met vertaling kunt u de vertaling van pagina-inhoud, elementen en door de gebruiker gegenereerde inhoud automatiseren om meertalige websites te maken en te onderhouden:

   * [Inhoud vertalen voor meertalige sites](/help/sites-administering/translation.md)

* Deze twee eigenschappen kunnen worden gecombineerd om voor websites te behandelen die zowel [ Multinationaal als Meertalig ](#multinational-and-multilingual-sites) zijn.

## Meertalige en meertalige sites {#multinational-and-multilingual-sites}

U kunt op efficiënte wijze inhoud maken voor multinationale en meertalige sites door het gecombineerde gebruik van de Multi-Site Manager en de vertaalworkflow. Maak een stramiensite in één taal, voor een specifiek land, en gebruik die inhoud als basis voor de andere sites, waar nodig met vertaling:

* [ vertaal ](/help/sites-administering/translation.md) de hoofdplaats in verschillende talen.

* Gebruik [ MultiManager van de Plaats ](/help/sites-administering/msm.md) aan:

   * Gebruik inhoud van de hoofdsite en de vertalingen opnieuw om sites te maken voor andere landen en culturen.
   * Zorg ervoor dat u het gebruik van Multi-Site Manager beperkt tot inhoud binnen één taal, bijvoorbeeld Engelse master > Engelse taalvertakkingen in landsites, Franse master > Franse taalvertakkingen in landsites.
   * Koppel zo nodig elementen van de live kopieën los om lokalisatiegegevens toe te voegen.

In het volgende diagram ziet u hoe de hoofdconcepten elkaar snijden (maar niet alle niveaus/elementen in kwestie weergeven):

![ Diagram die belangrijkste concepten MSM en Vertaling tonen ](assets/chlimage_1-71a.png)

>[!NOTE]
>
>In dit, en vergelijkbaar, scenario&#39;s MSM beheert niet de verschillende taalversies als dusdanig.
>
>* [ MSM ](/help/sites-administering/msm.md) beheert de plaatsing van vertaalde inhoud van een blauwdruk (bijvoorbeeld, een globale meester) aan de levende exemplaren (bijvoorbeeld, de lokale plaatsen), binnen de grenzen van een taal.
>* De [ vertaal ](/help/sites-administering/translation.md) integratiemogelijkheden van AEM, samen met de diensten van het derdevertaalbeheer, beheert de talen en het vertalen van inhoud in deze verschillende talen.
>
>Voor geavanceerdere gebruiksgevallen kan MSM ook voor alle taalmeesters worden gebruikt.

>[!NOTE]
>
>Voor alle gebruiksgevallen is het raadzaam de volgende aanbevolen procedures te lezen:
>
>* [ Beste praktijken voor MSM ](/help/sites-administering/msm-best-practices.md); in het bijzonder:
>
>   * [ creeer Plaats ](/help/sites-administering/msm-best-practices.md#create-site)
>   * [ MSM en Meertalige Websites ](/help/sites-administering/msm-best-practices.md#msm-and-multilingual-websites)
>
>* [ Beste praktijken voor Vertaling ](/help/sites-administering/tc-bp.md)
