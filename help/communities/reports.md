---
title: Rapportenconsole
seo-title: Rapportenconsole
description: Leer hoe u rapporten kunt openen
seo-description: Leer hoe u rapporten kunt openen
uuid: 7bb15a15-077b-4bfb-aaf4-50fddc67f237
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: fde053ff-b671-456b-869c-81f16ea1f1be
docset: aem65
translation-type: tm+mt
source-git-commit: 0051791da06d15a48b82cf93164a89b4ea42ce98
workflow-type: tm+mt
source-wordcount: '601'
ht-degree: 0%

---


# Rapportconsole {#reports-console}

## Overzicht {#overview}

Voor AEM Communities zijn er diverse rapporten die op verschillende manieren toegankelijk zijn vanuit de auteursomgeving.

In het algemeen zijn de verschillende verslagen:

* [Toewijzingsrapport](#assignments-report)

   Voor een [enablement community](/help/communities/overview.md#enablement-community) geeft u een overzicht van de vorderingen van studenten bij het toewijzen van hun taken, inclusief een bijbehorende score bij het implementeren van de SCORM-standaard.

* [Rapport Weergaven](#views-report)

   Verstrekt een grafiek van meningen van inhoud door communautaire leden en plaatsbezoekers voor om het even welke communautaire plaats.

* [Post Report](#posts-report)

   Verstrekt een grafiek van diverse soorten posten door communautaire leden aan om het even welke communautaire plaats.

Wanneer [Adobe Analytics is ingeschakeld](/help/communities/sites-console.md#analytics), bevatten rapporten het aantal weergaven, afspelen, opmerkingen en classificaties voor elke activeringsbron in de loop van de tijd.

Rapporten in tabelvorm kunnen worden geëxporteerd in de .csv-indeling voor verdere verwerking.

## Consoles {#reporting-consoles} rapporteren

### Rapporten voor communautaire sites {#reports-for-community-sites}

* Vanuit globale navigatie: **[!UICONTROL Navigation]** > **[!UICONTROL Communities]** > **[!UICONTROL Reports]**

* Kies uit:

   * **[!UICONTROL Assignments Report]**

      * Genereer een rapport voor de geselecteerde Community Site, Gebruiker of Groep en Toewijzing.
   * **[!UICONTROL Posts Report]**

      * Genereer een rapport voor een geselecteerde Community Site, Type inhoud en Tijdsperiode.
   * **[!UICONTROL Views Report]**

      * een rapport genereren voor een geselecteerde Community Site, Type inhoud en Tijdsperiode.



![rapporten](assets/reports1.png)

### Rapporten voor Middelen van Enablement en het Leren Wegen {#reports-for-enablement-resources-and-learning-paths}

* Vanuit globale navigatie: **[!UICONTROL Navigation]** > **[!UICONTROL Communities]** > **[!UICONTROL Resources]**

* Selecteer een bestaande communitysite voor activering:

   * Selecteer **het pictogram Rapport** om rapporten te produceren die alle enablement middelen behandelen.
   * Selecteer een leerpad voor inschakelen.
   * Selecteer **rapportpictogram** om rapporten te produceren voor:

      * De meegeleverde bronnen voor activering.
      * De studenten die zijn toegewezen aan het leerpad.

* Deze verslagen bevatten:

   * Tabelgegevens, downloadbaar als CSV:

      * Student identificeren
      * Hun status
      * Of toegewezen of benaderd via catalogus
      * Aantal gemaakte opmerkingen
      * Sterrenclassificatie gegeven

Voor meer details, zie [de sectie van Rapporten](/help/communities/resources.md#report) van de console van Middelen.

## Rapport Toewijzingen {#assignments-report}

Met de toewijzingsconsole kunnen rapporten worden gefilterd door de communitysite, gebruikers of groepen en toewijzing in te schakelen.

Het verslag bevat informatie over de voortgang van de activiteiten en eventuele opmerkingen of beoordelingen.

![toewijzingsrapport](assets/assignment-report.png)

Selecteer de criteria voor het rapport:

* **Site**

   Selecteer een community-site voor activering.

* **Gebruiker of groep**
   * Selecteer Gebruiker om een rapport voor één student te genereren.
   * Selecteer Groep om een rapport voor een groep studenten te genereren.

   De tunneldienst zal tot leden en lidgroepen van het publicatiemilieu toegang hebben.

* **Toewijzen**

   Maak een keuze uit de instellingsbronnen die aan de geselecteerde studenten zijn toegewezen.

Selecteer **Generate** om het rapport tot stand te brengen:

![genereren](assets/generate-assignment-report.png)

## Rapport {#views-report} weergaven

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

Selecteer **[!UICONTROL Generate]** om het rapport tot stand te brengen.

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

Selecteer **[!UICONTROL Generate]** om het rapport tot stand te brengen.

![genereren](assets/generate-posts-report.png)

## Problemen oplossen {#troubleshooting}

### Geen vermelde communitysites {#no-community-sites-listed}

Als er geen community-sites worden vermeld, moet u ervoor zorgen dat Adobe Analytics is ingeschakeld voor een site. Als u rapporten over toewijzingen kiest, moet u ervoor zorgen dat de toewijzingsfunctie zich in de structuur van de gemeenschapssite bevindt.

### Rapporten worden niet weergegeven in instantie AEM-auteur {#reports-do-not-show-in-aem-author-instance}

Als rapporten niet worden weergegeven in een instantie van AEM-auteur, controleert u of er aanpassingen zijn, zoals URL-toewijzing bij instantie Publiceren. Als de afbeelding URL slechts op AEM wordt gedaan publiceer instantie van de communautaire plaats, zorg ervoor dat het zelfde in de instantie van de Auteur AEM in **de Configuratie van de Component van het Rapport Sociale van de Tendens van de Plaats** is gevormd.

![URL-toewijzing op AEM-auteur](assets/sitetrend.png)