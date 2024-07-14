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
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# Rapportenconsole {#reports-console}

## Overzicht {#overview}

Voor AEM Communities zijn er diverse rapporten die op verschillende manieren toegankelijk zijn vanuit de auteursomgeving.

In het algemeen zijn de verschillende verslagen:

* [ Rapport van Meningen ](#views-report)

  Verstrekt een grafiek van meningen van inhoud door communautaire leden en plaatsbezoekers voor om het even welke communautaire plaats.

* [ het Rapport van Post ](#posts-report)

  Verstrekt een grafiek van diverse soorten posten door communautaire leden aan om het even welke communautaire plaats.

Rapporten in tabelvorm kunnen worden geëxporteerd in de .csv-indeling voor verdere verwerking.

## Consoles rapporteren {#reporting-consoles}

### Verslagen voor communautaire sites {#reports-for-community-sites}

* Vanuit globale navigatie: **[!UICONTROL Navigation]** > **[!UICONTROL Communities]** > **[!UICONTROL Reports]**

* Kies uit:

   * **[!UICONTROL Assignments Report]**

      * Genereer een rapport voor de geselecteerde Community Site, Gebruiker of Groep en Toewijzing.

   * **[!UICONTROL Posts Report]**

      * Genereer een rapport voor een geselecteerde Community Site, Type inhoud en Tijdsperiode.

   * **[!UICONTROL Views Report]**

      * een rapport genereren voor een geselecteerde Community Site, Type inhoud en Tijdsperiode.

![ rapporten ](assets/reports1.png)

## Rapport Weergaven {#views-report}

Met de weergaveconsole kunnen rapporten gedurende een bepaalde periode worden gegenereerd op paginaweergaven door gemeenschapsfuncties.

![ mening-rapport ](assets/view-report.png)

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

Selecteer **[!UICONTROL Generate]** om het rapport te maken.

![ produceren-meningen ](assets/generate-views.png)

## Post Report {#posts-report}

De console van Posten laat rapporten toe om op het aantal posten aan communautaire eigenschappen voor een bepaalde tijdspanne worden geproduceerd.

![ post-rapport ](assets/posts-report.png)

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

Selecteer **[!UICONTROL Generate]** om het rapport te maken.

![ produceren-rapport ](assets/generate-posts-report.png)

## Problemen oplossen {#troubleshooting}

### Geen community-sites vermeld {#no-community-sites-listed}

Als er geen communitysites worden weergegeven, controleert u of Adobe Analytics is ingeschakeld voor een site. Als u rapporten over toewijzingen kiest, moet u ervoor zorgen dat de toewijzingsfunctie zich in de structuur van de gemeenschapssite bevindt.

### Rapporten worden niet weergegeven in AEM instantie Auteur {#reports-do-not-show-in-aem-author-instance}

Als rapporten niet worden weergegeven in de AEM Author-instantie, controleert u of er aanpassingen zijn, zoals URL-toewijzing op de Publish-instantie. Als de afbeelding URL slechts op de AEM instantie van Publish van de communautaire plaats wordt gedaan, zorg ervoor dat het zelfde in de AEM instantie van de Auteur in **de Configuratie van de Factory van de Component van de Tendens van de Plaats van de Steek Sociale van de Component** is gevormd.

![ afbeelding URL op AEM Auteur ](assets/sitetrend.png)
