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

mpeg is een oplossing voor het omzetten en het stromen audio en video en, wanneer geïnstalleerd, wordt gebruikt voor juiste transcodering van [ videoactiva ](../../help/sites-authoring/default-components-foundation.md#video).

## Mpeg installeren {#installing-ffmpeg}

mpeg zou op de server(s) moeten worden geïnstalleerd die de AEM *auteur* instantie(s) ontvangen.

1. Ga naar [ https://www.ffmpeg.org ](https://www.ffmpeg.org/).
1. Download de nieuwste versie van MPEG voor uw specifieke omgeving (Macintosh, Windows of Linux).

   * Het is belangrijk om MPEG up-to-date te houden wegens veiligheidskwetsbaarheden in oudere versies.

1. Installeer de MPEG volgens de instructies voor het besturingssysteem.

1. Zorg ervoor dat het uitvoerbare bestand van de MPEG is ingesteld in het systeempad.

   U moet Mpeg vanuit elke map in uw systeem kunnen uitvoeren.

   * Bijvoorbeeld `ffmpeg -version` .

## MPEG Transcoding Service configureren {#configure-ffmpeg-transcoding-service}

Wanneer MPEG wordt geïnstalleerd, worden standaard meerdere uitvoeringen geconfigureerd (transcoderingen) volgens de workflowdefinitie van [!UICONTROL DAM Update Asset] .

Aangezien de transcoderingen CPU-intensief zijn, wordt aangeraden de lijst met doeluitvoeringen te wijzigen. In de meeste gevallen is transcodering niet nodig.

U kunt als volgt de [!UICONTROL DAM Update Asset] -workflow wijzigen en in dit voorbeeld de transcodering uitschakelen:

* Meld u aan bij de instantie van de auteur met beheerdersrechten.
* Navigeer vanuit de globale navigatie naar **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]** .
* Zoek **[!UICONTROL DAM Update Asset]** .
* Dubbelklik om de workflow voor bewerking te openen in de klassieke gebruikersinterface.

  Resulterende plaats: [ http://localhost:4502/cf#/etc/workflow/models/dam/update_asset.html](http://localhost:4502/cf#/etc/workflow/models/dam/update_asset.html)

* Dubbelklik op de stap **[!UICONTROL FFmpeg transcoding]** om het dialoogvenster Step Properties te openen.
* Onder het tabblad **[!UICONTROL Process]** :

   * **[!UICONTROL Arugments]**: wis alle items om transcodering van standaardwaarden uit te schakelen: `profile:format_ogg,profile:format_aac,profile:format_flv,profile:format_aac_ie`

  ![ vorm-ffmpeg ](assets/configure-ffmpeg.png)

* Selecteer **[!UICONTROL OK]** om het dialoogvenster `Step Properties` te sluiten.

* Selecteer **[!UICONTROL Save]** om de `DAM Update Asset` -workflow op te slaan.
