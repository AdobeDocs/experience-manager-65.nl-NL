---
title: Uw accountomgeving configureren
seo-title: Uw accountomgeving configureren
description: AEM biedt u de mogelijkheid om uw account en bepaalde aspecten van de auteursomgeving te configureren
seo-description: AEM biedt u de mogelijkheid om uw account en bepaalde aspecten van de auteursomgeving te configureren
uuid: ef31be29-5c18-4dc9-ad51-fb001588b31e
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
discoiquuid: b610e19c-f8d9-4ae2-b056-9fd5cf541261
docset: aem65
translation-type: tm+mt
source-git-commit: bcb1840d23ae538c183eecb0678b6a75d346aa50
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 4%

---


# Uw accountomgeving configureren{#configuring-your-account-environment}

AEM biedt u de mogelijkheid om uw account en bepaalde aspecten van de auteursomgeving te configureren.

Met de optie [Gebruiker](/help/sites-authoring/user-properties.md#user-settings) in de [koptekst](/help/sites-authoring/basic-handling.md#the-header) en het bijbehorende dialoogvenster [Mijn voorkeuren](#userpreferences) kunt u uw gebruikersopties wijzigen, zoals

Begin door tot [User](/help/sites-authoring/user-properties.md#user-settings) optie in de kopbal toegang te hebben.

## Gebruikersinstellingen {#user-settings}

In het instellingendialoogvenster **Gebruiker** hebt u toegang tot:

* Imiteren als

   * Met [Imiteren als](/help/sites-administering/security.md#impersonating-another-user) functionaliteit kan een gebruiker namens een andere gebruiker werken.

* Profiel

   * Biedt een handige koppeling naar uw [gebruikersinstellingen](/help/sites-administering/security.md))

* [Mijn voorkeuren](/help/sites-authoring/user-properties.md#my-preferences)

   * Verschillende voorkeursinstellingen opgeven die uniek zijn voor uw gebruiker

![screen_shot_2018-03-20at103808](assets/screen_shot_2018-03-20at103808.png)

### Mijn voorkeuren {#my-preferences}

Het dialoogvenster **Mijn voorkeuren** is toegankelijk via de optie [Gebruiker](/help/sites-authoring/user-properties.md#user-settings) in de koptekst.

Elke gebruiker kan bepaalde eigenschappen voor zichzelf instellen.

![screen-shot_2019-03-05at100322](assets/screen-shot_2019-03-05at100322.png)

* **Taal**

   Dit bepaalt de taal voor UI van het auteursmilieu te gebruiken. Selecteer de gewenste taal in de beschikbare lijst.

   Deze configuratie wordt ook gebruikt voor klassieke UI.

* **Vensterbeheer**

   Hiermee definieert u het gedrag voor het openen van vensters. Selecteer een van de volgende opties:

   * **Meerdere vensters**  (standaard)

      * Pagina&#39;s worden in een nieuw venster geopend.
   * **Eén venster**

      * Pagina&#39;s worden geopend in het huidige venster.


* **Bureaubladhandelingen voor elementen weergeven**

   Voor deze optie moet AEM bureaubladtoepassing worden gebruikt.

* **Annotatiekleur**

   Hiermee definieert u de standaardkleur die wordt gebruikt bij het maken van annotaties.

   * Klik op het kleurblok om de staalkiezer te openen en een kleur te selecteren.
   * U kunt ook de hexadecimale code voor de gewenste kleur in het veld invoeren.

* **Relatieve datumpresentatie**

   Om de leesbaarheid te verbeteren, worden AEM datums in de laatste zeven dagen weergegeven als relatieve datums (bijvoorbeeld drie dagen geleden) en oudere datums als exacte datums (bijvoorbeeld 20 maart 2017).

   Met deze optie bepaalt u hoe datums in het systeem worden weergegeven. De volgende opties zijn beschikbaar:

   * **Altijd exacte datum** weergeven: De exacte datum wordt altijd weergegeven (nooit een relatieve datum).
   * **1 dag**: De relatieve datum wordt weergegeven voor datums binnen één dag, anders wordt een exacte datum weergegeven.

   * **7 dagen (standaard)**: De relatieve datum wordt weergegeven voor datums binnen zeven dagen, anders wordt een exacte datum weergegeven.

   * **1 maand**: De relatieve datum wordt weergegeven voor datums binnen een maand, anders wordt een exacte datum weergegeven.

   * **1 jaar**: De relatieve datum wordt weergegeven voor data binnen een jaar, anders wordt een exacte datum vermeld.

   * **Relatieve datum** altijd weergeven: Exacte datums worden nooit weergegeven en alleen relatieve datums worden weergegeven.

* **Sneltoetsen inschakelen**

   AEM ondersteunt een aantal sneltoetsen die het ontwerpen efficiënter maken.

   * [Sneltoetsen voor het bewerken van pagina&#39;s](/help/sites-authoring/page-authoring-keyboard-shortcuts.md)
   * [Sneltoetsen voor consoles](/help/sites-authoring/keyboard-shortcuts.md)

   Met deze optie schakelt u sneltoetsen in. Deze worden standaard ingeschakeld, maar kunnen worden uitgeschakeld, bijvoorbeeld als een gebruiker bepaalde toegankelijkheidsvereisten heeft.

* **Klassieke ontwerpervaring gebruiken**

   Met deze optie schakelt u op [klassieke UI](/help/sites-classic-ui-authoring/home.md) gebaseerde pagina-authoring in. Standaard wordt de standaardinterface gebruikt.

* **Introductiepagina van middelen inschakelen**

   Deze optie is alleen beschikbaar als uw systeembeheerder de functie voor het introductiepagina van middelen heeft ingeschakeld voor de hele organisatie.

* **Bestandsconfiguratie**

   Met deze optie kunt u de voorkeursconfiguratie van Adobe Stock opgeven. Deze optie is alleen beschikbaar als uw systeembeheerder [Adobe Stock-integratie](/help/assets/aem-assets-adobe-stock.md) heeft ingeschakeld.
