---
title: MPEG voor Gemeenschappen
seo-title: MPEG voor Gemeenschappen
description: Mpeg for Communities installeren en configureren
seo-description: Mpeg for Communities installeren en configureren
uuid: ef2f821c-70e9-4889-a8d7-a93b10a1d428
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 739ec991-552b-42cd-85cd-984d1c9fe8fd
role: Admin
exl-id: dbe28334-3b38-4362-b4f8-e0630e634503
source-git-commit: 603518dbe3d842a08900ac40651919c55392b573
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 1%

---

# MPEG voor Gemeenschappen {#ffmpeg-for-communities}

## Overzicht {#overview}

mpeg is een oplossing voor het converteren en streamen van audio en video en wordt, indien geïnstalleerd, gebruikt voor de juiste transcodering van [video-elementen](../../help/sites-authoring/default-components-foundation.md#video) en voor de functie voor activering van AEM-gemeenschappen.

mpeg wordt gebruikt in de auteursomgeving om meta-gegevens voor geupload enablement middelen te verkrijgen evenals een duimnagel te produceren om te tonen wanneer het vermelden van het enablement middel.

## Mpeg installeren {#installing-ffmpeg}

MPEG moet worden geïnstalleerd op de server(s) die als host fungeert voor de AEM *auteur*-instantie(s).

1. Ga naar [https://www.ffmpeg.org](https://www.ffmpeg.org/).
1. Download de nieuwste versie van MPEG voor uw specifieke omgeving (Macintosh, Windows of Linux).

   * Het is belangrijk om MPEG up-to-date te houden wegens veiligheidskwetsbaarheden in oudere versies.

1. Installeer de MPEG volgens de instructies voor het besturingssysteem.

1. Zorg ervoor dat het uitvoerbare bestand van de MPEG is ingesteld in het systeempad.

   U moet Mpeg vanuit elke map in uw systeem kunnen uitvoeren.

   * Bijvoorbeeld, `ffmpeg -version`.

## MPEG Transcoding Service configureren {#configure-ffmpeg-transcoding-service}

Wanneer MPEG wordt geïnstalleerd, worden standaard meerdere uitvoeringen geconfigureerd (transcoderingen) volgens de [!UICONTROL DAM Update Asset]-workflowdefinitie.

Aangezien de transcoderingen CPU-intensief zijn, wordt aangeraden de lijst met doeluitvoeringen te wijzigen. In de meeste gevallen is transcodering niet nodig.

U kunt als volgt de [!UICONTROL DAM Update Asset]-workflow wijzigen en in dit voorbeeld de transcodering uitschakelen:

* Meld u aan bij de instantie van de auteur met beheerdersrechten.
* Navigeer vanuit globale navigatie naar **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
* **[!UICONTROL DAM Update Asset]** zoeken.
* Dubbelklik om de workflow voor bewerking te openen in de klassieke gebruikersinterface.

   Resulterende locatie: [http://localhost:4502/cf#/etc/workflow/models/dam/update_asset.html](http://localhost:4502/cf#/etc/workflow/models/dam/update_asset.html)

* Dubbelklik op de stap **[!UICONTROL FFmpeg transcoding]** om het dialoogvenster Step Properties te openen.
* Onder het tabblad **[!UICONTROL Process]**:

   * **[!UICONTROL Arugments]**: Wis alle ingangen om transcoderende Standaardwaarden onbruikbaar te maken:  `profile:format_ogg,profile:format_aac,profile:format_flv,profile:format_aac_ie`

   ![configure-ffmpeg](assets/configure-ffmpeg.png)

* Selecteer **[!UICONTROL OK]** om het dialoogvenster `Step Properties` te sluiten.

* Selecteer **[!UICONTROL Save]** om het `DAM Update Asset` werkschema te bewaren.
