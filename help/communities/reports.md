---
title: Rapportenconsole
description: Leer hoe u verschillende rapporten kunt gebruiken die u op verschillende manieren kunt openen vanuit de Adobe Experience Manager Author-omgeving.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
docset: aem65
role: Admin
exl-id: 2aff2ffe-ba6f-4cc9-a126-40fc2a1161e2
source-git-commit: 00b6f2f03470aca7f87717818d0dfcd17ac16bed
workflow-type: tm+mt
source-wordcount: '384'
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

Met de weergaveconsole kunnen rapporten gedurende een bepaalde periode worden gegenereerd op paginaweergaven door gemeenschapsfuncties.

![view-report](assets/view-report.png)

Selecteer de criteria voor het rapport:

* **[!UICONTROL Site]**

  Selecteer een communitysite.

* **[!UICONTROL Content Type]**

  Kies mogelijk Alle inhoud of selecteer een van de functies die op de site aanwezig zijn.

* **[!UICONTROL Time frame]**

  Selecteer een van de volgende opties:

   * Laatste 7 dagen
   * Laatste 30 dagen
   * Laatste 90 dagen
   * Vorig jaar

Selecteren **[!UICONTROL Generate]** om het rapport te maken.

![genereren, weergaven](assets/generate-views.png)

## Post Report {#posts-report}

De console van Posten laat rapporten toe om op het aantal posten aan communautaire eigenschappen voor een bepaalde tijdspanne worden geproduceerd.

![post-rapport](assets/posts-report.png)

Selecteer de criteria voor het rapport:

* **[!UICONTROL Site]**

  Selecteer een communitysite.

* **[!UICONTROL Content Type]**

  Kies mogelijk Alle inhoud of selecteer een van de functies die op de site aanwezig zijn.

* **[!UICONTROL Time frame]**

  Selecteer een van de volgende opties:

   * Laatste 7 dagen
   * Laatste 30 dagen
   * Laatste 90 dagen
   * Vorig jaar

Selecteren **[!UICONTROL Generate]** om het rapport te maken.

![genereren van rapporten](assets/generate-posts-report.png)

## Problemen oplossen {#troubleshooting}

### Geen community-sites vermeld {#no-community-sites-listed}

Als er geen communitysites worden weergegeven, controleert u of Adobe Analytics is ingeschakeld voor een site. Als u rapporten over toewijzingen kiest, moet u ervoor zorgen dat de toewijzingsfunctie zich in de structuur van de gemeenschapssite bevindt.

### Rapporten worden niet weergegeven in AEM instantie Auteur {#reports-do-not-show-in-aem-author-instance}

Als rapporten niet worden weergegeven in de instantie AEM Auteur, controleert u op de aanpassingen, zoals URL-toewijzing op de instantie Publiceren. Als URL-toewijzing alleen wordt uitgevoerd op de AEM Publish-instantie van de communitysite, moet u ervoor zorgen dat hetzelfde is geconfigureerd in de AEM Author-instantie in **Site Trend Report Social Component Factory** configuratie.

![URL-toewijzing op AEM auteur](assets/sitetrend.png)
