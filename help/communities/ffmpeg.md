---
title: MPEG voor Gemeenschappen
description: Mpeg for Communities installeren en configureren
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
role: Admin
exl-id: dbe28334-3b38-4362-b4f8-e0630e634503
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---

# MPEG voor Gemeenschappen {#ffmpeg-for-communities}

## Overzicht {#overview}

mpeg is een oplossing voor het converteren en streamen van audio en video en wordt, indien geïnstalleerd, gebruikt voor de juiste transcodering van [video-elementen](../../help/sites-authoring/default-components-foundation.md#video).

## Mpeg installeren {#installing-ffmpeg}

Fmpeg moet worden geïnstalleerd op de server(s) die als host fungeert voor de AEM *auteur* instantie(s).

1. Ga naar [https://www.ffmpeg.org](https://www.ffmpeg.org/).
1. Download de nieuwste versie van MPEG voor uw specifieke omgeving (Macintosh, Windows of Linux).

   * Het is belangrijk om MPEG up-to-date te houden wegens veiligheidskwetsbaarheden in oudere versies.

1. Installeer de MPEG volgens de instructies voor het besturingssysteem.

1. Zorg ervoor dat het uitvoerbare bestand van de MPEG is ingesteld in het systeempad.

   U moet Mpeg vanuit elke map in uw systeem kunnen uitvoeren.

   * Bijvoorbeeld: `ffmpeg -version`.

## MPEG Transcoding Service configureren {#configure-ffmpeg-transcoding-service}

Wanneer MPEG wordt geïnstalleerd, worden standaard meerdere uitvoeringen geconfigureerd (transcoderingen) volgens de [!UICONTROL DAM Update Asset] workflowdefinitie.

Aangezien de transcoderingen CPU-intensief zijn, wordt aangeraden de lijst met doeluitvoeringen te wijzigen. In de meeste gevallen is transcodering niet nodig.

Als u de [!UICONTROL DAM Update Asset] workflow en in dit voorbeeld om transcodering uit te schakelen:

* Meld u aan bij de instantie van de auteur met beheerdersrechten.
* Navigeer van globale navigatie naar **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
* Zoeken **[!UICONTROL DAM Update Asset]**.
* Dubbelklik om de workflow voor bewerking te openen in de klassieke gebruikersinterface.

  Resulterende locatie: [http://localhost:4502/cf#/etc/workflow/models/dam/update_asset.html](http://localhost:4502/cf#/etc/workflow/models/dam/update_asset.html)

* Dubbelklik op de knop **[!UICONTROL FFmpeg transcoding]** om het dialoogvenster Step Properties te openen.
* Onder de **[!UICONTROL Process]** tab:

   * **[!UICONTROL Arugments]**: Wis alle items om transcoderingsstandaardwaarden uit te schakelen: `profile:format_ogg,profile:format_aac,profile:format_flv,profile:format_aac_ie`

  ![configure-ffmpeg](assets/configure-ffmpeg.png)

* Selecteren **[!UICONTROL OK]** om de `Step Properties` in.

* Selecteren **[!UICONTROL Save]** om de `DAM Update Asset` workflow.
