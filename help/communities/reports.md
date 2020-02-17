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
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65

---


# Rapportenconsole{#reports-console}

## Overzicht {#overview}

Voor AEM-gemeenschappen zijn er verschillende rapporten die op verschillende manieren toegankelijk zijn vanuit de auteursomgeving.

In het algemeen zijn de verschillende verslagen:

* [Toewijzingsrapport](#assignments-report) - voor een [activeringscommunity](/help/communities/overview.md#enablement-community)geeft een overzicht van de vorderingen van studenten bij het toewijzen van hun taken, inclusief een bijbehorende score bij het implementeren van de SCORM-standaard
* [Weergaverapport](#views-report) : geeft een overzicht van de weergaven van de inhoud van de website en de leden van de gebruikersgemeenschap
* [Post Report](#posts-report) - geeft een overzicht van verschillende typen berichten van leden van de gemeenschap aan elke site van de gemeenschap

Wanneer [Adobe Analytics is ingeschakeld](/help/communities/sites-console.md#analytics), bevatten rapporten het aantal weergaven, afspelen, opmerkingen en waarderingen voor elke activeringsbron in de loop van de tijd

Rapporten in tabelvorm kunnen worden geëxporteerd in de .csv-indeling voor verdere verwerking.

## Consoles rapporteren {#reporting-consoles}

### Verslagen voor communautaire sites {#reports-for-community-sites}

* van globale navigatie: **Navigatie**, **Gemeenschappen, Verslagen**

* kiezen uit

   * **Toewijzingsrapport**

      * een rapport genereren voor een geselecteerde community-site, -gebruiker of -groep en -toewijzing

      * **Post Report**

         * een rapport genereren voor een geselecteerde Community Site, Type inhoud en Tijdsperiode
      * **Rapport Weergaven**

         * een rapport genereren voor een geselecteerde Community Site, Type inhoud en Tijdsperiode


![chlimage_1-236](assets/chlimage_1-236.png)

### Rapporten voor Middelen Enablement en het Leren Wegen {#reports-for-enablement-resources-and-learning-paths}

* van globale navigatie: **Navigatie**, **Gemeenschappen, Middelen**

* selecteer een bestaande site van de enabable-community

   * Selecteer **Rapport **pictogram om rapporten te produceren die alle inschrijvingsmiddelen behandelen
   * een leerpad inschakelen
   * Selecteer **Rapport **pictogram om rapporten voor te produceren

      * de opgenomen middelen voor activering
      * de studenten die zijn toegewezen aan het leerpad

* deze verslagen bevatten :

   * tabelgegevens, downloadbaar als CSV

      * leerling identificeren
      * hun status
      * al dan niet toegewezen of benaderd via catalogus
      * aantal gemaakte opmerkingen
      * sterrenwaardering opgegeven

Voor meer details, zie de sectie [van](/help/communities/resources.md#report) Rapporten van de console van Middelen.

## Toewijzingsrapport {#assignments-report}

Met de toewijzingsconsole kunnen rapporten worden gefilterd door de communitysite, gebruikers of groepen en toewijzing in te schakelen.

Het verslag bevat informatie over de voortgang van de activiteiten en eventuele opmerkingen of beoordelingen.

![chlimage_1-237](assets/chlimage_1-237.png)

Selecteer de criteria voor het rapport:

* **Site**

   een community-site voor activering selecteren

* **Gebruiker of groep**
   * Selecteer Gebruiker om een rapport voor één student te genereren
   * Selecteer Groep om een rapport voor een groep studenten te genereren
   De tunneldienst zal tot leden en lidgroepen van publicatiemilieu toegang hebben

* **Toewijzen**

   Maak een keuze uit de instellingsbronnen die aan de geselecteerde studenten zijn toegewezen

Selecteer **produceren** om het rapport tot stand te brengen:

![chlimage_1-238](assets/chlimage_1-238.png)

## Rapport Weergaven {#views-report}

Met de weergaveconsole kunnen rapporten gedurende een bepaalde periode worden gegenereerd op paginaweergaven door een of meer algemene functies.

![chlimage_1-239](assets/chlimage_1-239.png)

Selecteer de criteria voor het rapport:

* **Site**

   selecteer een community-site

* **Inhoudstype**

   kan Alle inhoud kiezen of een van de functies op de site selecteren

* tijdkader

   selecteer een van de

   * Laatste 7 dagen
   * Laatste 30 dagen
   * Laatste 90 dagen
   * Vorig jaar

Selecteer **produceren** om het rapport tot stand te brengen:

![chlimage_1-240](assets/chlimage_1-240.png)

## Post Report {#posts-report}

Met de Post-console kunnen rapporten gedurende een bepaalde periode worden gegenereerd op het aantal posten voor een of meer algemene functies.

![chlimage_1-241](assets/chlimage_1-241.png)

Selecteer de criteria voor het rapport:

* **Site**

   selecteer een community-site

* **Inhoudstype**

   kan Alle inhoud kiezen of een van de functies op de site selecteren

* tijdkader

   selecteer een van de

   * Laatste 7 dagen
   * Laatste 30 dagen
   * Laatste 90 dagen
   * Vorig jaar

Selecteer **produceren** om het rapport tot stand te brengen:

![chlimage_1-242](assets/chlimage_1-242.png)

## Problemen oplossen {#troubleshooting}

### Geen community-sites vermeld {#no-community-sites-listed}

Als er geen communitysites worden vermeld, controleert u of Adobe Analytics is ingeschakeld voor een site. Als u rapporten over toewijzingen kiest, moet u ervoor zorgen dat de toewijzingsfunctie zich in de structuur van de gemeenschapssite bevindt.

### Rapporten worden niet weergegeven in een instantie van AEM-auteur {#reports-do-not-show-in-aem-author-instance}

Als rapporten niet worden weergegeven in een instantie van AEM-auteur, controleert u of er aanpassingen zijn, zoals URL-toewijzing bij instantie Publiceren. Als de afbeelding URL slechts op AEM wordt gedaan publiceer instantie van de communautaire plaats, zorg ervoor dat het zelfde in de instantie van de Auteur AEM in **De Factory van de Component van de Tendens van de Plaats van het Rapport Sociale **configuratie is gevormd.

![URL-toewijzing op AEM-auteur](assets/sitetrend.png)