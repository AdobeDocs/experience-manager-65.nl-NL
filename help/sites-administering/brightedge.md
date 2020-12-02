---
title: Integreren met BrightStor Content Optimizer
seo-title: Integreren met BrightStor Content Optimizer
description: Leer hoe u AEM kunt integreren met BrightStor Content Optimizer.
seo-description: Leer hoe u AEM kunt integreren met BrightStor Content Optimizer.
uuid: 7075dd3c-2fd6-4050-af1c-9b16ad4366ec
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: cf25c9a8-0555-4c67-8aa5-55984fd8d301
translation-type: tm+mt
source-git-commit: 684d2d5f73d571a15c8155e7870134c28dc892b7
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---


# Integreren met BrightStor Content Optimizer{#integrating-with-brightedge-content-optimizer}

Maak een BrightEdge-cloudconfiguratie zodat AEM verbinding kunnen maken met de referenties van uw BrightStor-account. U kunt meerdere configuraties maken als u meerdere accounts gebruikt.

Wanneer u de configuratie creeert, specificeert u een titel. De titel moet beschrijvend zijn, zodat mensen de configuratie kunnen correleren met de BrightStor-account. Wanneer een auteur of beheerder van een pagina een webpagina maakt met het BrightStor-account, wordt deze titel weergegeven in een vervolgkeuzelijst.

1. Klik in de track op Gereedschappen > Bewerkingen > Wolk > Cloud Services.
1. Klik op de koppeling die wordt weergegeven in de sectie BrightEdge Content Optimizer. De koppelingstekst wordt bepaald door het feit of er een BrightEdge-configuratie is gemaakt:

   * Nu configureren: Deze koppeling wordt weergegeven wanneer er geen configuratie is gemaakt.
   * Configuraties tonen: Deze koppeling wordt weergegeven wanneer een of meer configuraties zijn gemaakt.

   ![chlimage_1-4](assets/chlimage_1-4a.png)

1. Als u op Configuraties tonen hebt geklikt, klikt u op de koppeling + naast Beschikbare configuraties.
1. Typ een titel voor de configuratie. Naar keuze, typ een naam voor de knoop die wordt gebruikt om de configuratie in de bewaarplaats op te slaan. Klik op Maken.
1. Typ in het dialoogvenster Configuratie van BrightStor Content Optimizer de gebruikersnaam en het wachtwoord van de BrightStor-account en klik op OK.

## Een BrightEdge-configuratie {#editing-a-brightedge-configuration} bewerken

Wijzig indien nodig de gebruikersnaam en het wachtwoord van een BrightStor-configuratie. De wijzigingen zijn van invloed op alle pagina&#39;s die de configuratie gebruiken.

1. Klik in de track op Gereedschappen > Bewerkingen > Wolk > Cloud Services.
1. Klik in de sectie BrightEdge Content Optimizer op Configuraties tonen.

   ![chlimage_1-5](assets/chlimage_1-5a.png)

1. Klik op de naam van de configuratie die u wilt bewerken.
1. Klik op Bewerken, wijzig de eigenschapswaarden en klik op OK.

## Pagina&#39;s koppelen aan een BrightEdge-configuratie {#associating-pages-with-a-brightedge-configuration}

Koppel pagina&#39;s aan een BrightStor-configuratie om paginagegevens naar de BrightStor-service te verzenden voor analyse. Wanneer u een pagina aan een configuratie associeert, erven de kindpagina&#39;s de vereniging. Meestal koppelt u de startpagina van uw site, zodat gegevens van alle pagina&#39;s naar BrightStor Edge worden verzonden.

1. Open de klassieke websiteconsole. ([http://localhost:4502/siteadmin#/content](http://localhost:4502/siteadmin#/content))
1. Selecteer in de boomstructuur Websites de map of pagina die de pagina bevat die u aan de configuratie van BrightStor wilt koppelen.
1. Klik in de lijst met pagina&#39;s met de rechtermuisknop op de pagina die u wilt configureren en klik op Eigenschappen.
1. Klik op het tabblad Cloud Services op de knop Service toevoegen en selecteer BrightEdge Content Optimizer in het dialoogvenster Cloud Services en klik vervolgens op OK.
1. Selecteer in de lijst BrightEdge Content Optimizer de BrightEdge-configuratie die u aan de pagina wilt koppelen en klik op OK.

   ![chlimage_1-6](assets/chlimage_1-6a.png)

## Een BrightEdge-configuratie {#activating-a-brightedge-configuration} activeren

Activeer een BrightEdge-configuratie om deze te repliceren op de publicatie-instantie en om gepubliceerde pagina&#39;s in staat te stellen te communiceren met de BrightStor-service.

1. Klik op Sites in de track en blader naar de pagina die u aan de configuratie van BrightStor Edge hebt gekoppeld en selecteer deze.
1. Klik of tik op het pictogram Publiceren en klik vervolgens op Publiceren.

   ![chlimage_1-7](assets/chlimage_1-7a.png)

1. Controleer in de lijst met configuraties die wordt weergegeven of uw BrightStor-configuratie is geselecteerd en klik op Publiceren.

   ![chlimage_1-8](assets/chlimage_1-8a.png)

