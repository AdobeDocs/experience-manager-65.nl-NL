---
title: Rapportenconsole
seo-title: Reports Console
description: Leer hoe u rapporten kunt openen
seo-description: Learn how to access reports
uuid: 7bb15a15-077b-4bfb-aaf4-50fddc67f237
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: fde053ff-b671-456b-869c-81f16ea1f1be
docset: aem65
role: Admin
exl-id: 2aff2ffe-ba6f-4cc9-a126-40fc2a1161e2
source-git-commit: 942db8fe3dad16be53dc6abe0e519d97a659e480
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# Rapportenconsole {#reports-console}

## Overzicht {#overview}

Voor AEM Communities zijn er diverse rapporten die op verschillende manieren toegankelijk zijn vanuit de auteursomgeving.

In het algemeen zijn de verschillende verslagen:

* [Rapport Weergaven](#views-report)

   Verstrekt een grafiek van meningen van inhoud door communautaire leden en plaatsbezoekers voor om het even welke communautaire plaats.

* [Post Report](#posts-report)

   Verstrekt een grafiek van diverse soorten posten door communautaire leden aan om het even welke communautaire plaats.

Rapporten in tabelvorm kunnen worden geëxporteerd in de .csv-indeling voor verdere verwerking.

## Consoles rapporteren {#reporting-consoles}

### Verslagen voor communautaire sites {#reports-for-community-sites}

* Vanuit globale navigatie: **[!UICONTROL Navigation]** > **[!UICONTROL Communities]** >  **[!UICONTROL Reports]**

* Kies uit:

   * **[!UICONTROL Assignments Report]**

      * Genereer een rapport voor de geselecteerde Community Site, Gebruiker of Groep en Toewijzing.
   * **[!UICONTROL Posts Report]**

      * Genereer een rapport voor een geselecteerde Community Site, Type inhoud en Tijdsperiode.
   * **[!UICONTROL Views Report]**

      * een rapport genereren voor een geselecteerde Community Site, Type inhoud en Tijdsperiode.



![rapporten](assets/reports1.png)

## Rapport Weergaven {#views-report}

Met de weergaveconsole kunnen rapporten gedurende een bepaalde periode worden gegenereerd op paginaweergaven door een of meer algemene functies.

![view-report](assets/view-report.png)

Selecteer de criteria voor het rapport:

* **[!UICONTROL Site]**

   Selecteer een communitysite.

* **[!UICONTROL Content Type]**

   Kan Alle inhoud kiezen of een van de functies op de site selecteren.

* **[!UICONTROL Time frame]**

   Selecteer een van de volgende opties:

   * Laatste 7 dagen
   * Laatste 30 dagen
   * Laatste 90 dagen
   * Vorig jaar

Selecteren **[!UICONTROL Generate]** om het rapport te maken.

![genereren, weergaven](assets/generate-views.png)

## Post Report {#posts-report}

Met de Post-console kunnen rapporten gedurende een bepaalde periode worden gegenereerd op het aantal posten voor een of meer algemene functies.

![verslag](assets/posts-report.png)

Selecteer de criteria voor het rapport:

* **[!UICONTROL Site]**

   Selecteer een communitysite.

* **[!UICONTROL Content Type]**

   Kan Alle inhoud kiezen of een van de functies op de site selecteren.

* **[!UICONTROL Time frame]**

   Selecteer een van de volgende opties:

   * Laatste 7 dagen
   * Laatste 30 dagen
   * Laatste 90 dagen
   * Vorig jaar

Selecteren **[!UICONTROL Generate]** om het rapport te maken.

![genereren](assets/generate-posts-report.png)

## Problemen oplossen {#troubleshooting}

### Geen community-sites vermeld {#no-community-sites-listed}

Als er geen community-sites worden vermeld, moet u ervoor zorgen dat Adobe Analytics is ingeschakeld voor een site. Als u rapporten over toewijzingen kiest, moet u ervoor zorgen dat de toewijzingsfunctie zich in de structuur van de gemeenschapssite bevindt.

### Rapporten worden niet weergegeven in een instantie van AEM-auteur {#reports-do-not-show-in-aem-author-instance}

Als rapporten niet worden weergegeven in een instantie van AEM-auteur, controleert u of er aanpassingen zijn, zoals URL-toewijzing bij instantie Publiceren. Als URL-toewijzing alleen wordt uitgevoerd op de AEM-publicatieversie van de communitysite, moet u ervoor zorgen dat hetzelfde is geconfigureerd in de instantie AEM-auteur in **Site Trend Report Social Component Factory** configuratie.

![URL-toewijzing op AEM-auteur](assets/sitetrend.png)
