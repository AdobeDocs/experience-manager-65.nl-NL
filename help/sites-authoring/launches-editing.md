---
title: Lanceringen bewerken
seo-title: Lanceringen bewerken
description: 'Nadat u een opstartafbeelding voor de pagina (of set pagina''s) hebt gemaakt, kunt u de inhoud bewerken in de opstartafbeelding van de pagina(''s). '
seo-description: 'Nadat u een opstartafbeelding voor de pagina (of set pagina''s) hebt gemaakt, kunt u de inhoud bewerken in de opstartafbeelding van de pagina(''s). '
uuid: 1f2c2e53-73a3-4bd7-b2c7-425491bc0118
contentOwner: Alison Heimoz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 30aa3177-bcf4-4260-8f64-e73bc907942a
docset: aem65
legacypath: /content/docs/en/aem/6-0/author/site-page-features/launches
translation-type: tm+mt
source-git-commit: 2d7492cdee9f7f730dfa6ad2ffae396b3a737b15
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 19%

---


# Lanceringen bewerken{#editing-launches}

## Starten van pagina&#39;s bewerken {#editing-launch-pages}

Wanneer een startpagina (of een set pagina&#39;s) is gemaakt, kunt u de inhoud bewerken in de opstartafbeelding van de pagina(&#39;s).

1. Open [Starten vanuit Referenties (Sites-console)](/help/sites-authoring/launches.md#launches-in-references-sites-console) om de beschikbare handelingen weer te geven.
1. Selecteer **Ga naar de pagina** om de pagina te openen voor bewerking.

### Starten van pagina&#39;s bewerken die zijn onderworpen aan een actieve kopie {#editing-launch-pages-subject-to-a-live-copy}

Als uw lancering op een [levende exemplaar](/help/sites-administering/msm.md) gebaseerd is, dan zult u:

* zie vergrendelingssymbolen (kleine hangsloten) wanneer u een component (inhoud en/of eigenschappen) bewerkt.
* zie het **tabblad Live kopie** in **Pagina-eigenschappen**

Een livekopie wordt gebruikt om content te synchroniseren *van* de bronvertakking *naar* de startvertakking (om uw lancering up-to-date te houden als er veranderingen in de bron worden aangebracht).

U kunt wijzigingen aanbrengen op dezelfde manier als waarop u een live standaardkopie kunt bewerken. bijvoorbeeld:

* Als u op een gesloten hangslot klikt, wordt deze synchronisatie verbroken en kunt u nieuwe updates voor de inhoud uitvoeren wanneer u de toepassing start. Als de vergrendeling is opgeheven (open hanglock), worden de wijzigingen niet overschreven door wijzigingen die op dezelfde locatie in de bronvertakking zijn aangebracht.
* **Overname** voor een bepaalde pagina onderbreken (en **hervatten**).

Zie [Inhoud van actieve kopie wijzigen](/help/sites-administering/msm-livecopy.md#changing-live-copy-content) voor meer informatie.

## Een startpagina vergelijken met de bijbehorende bronpagina {#comparing-a-launch-page-to-its-source-page}

Als u de door u aangebrachte wijzigingen wilt bijhouden, kunt u de start weergeven in **Referenties** en de startpagina vergelijken met de bijbehorende bronpagina:

1. In **Sites** console, [navigeer aan de bronpagina van uw lancering en selecteer het ](/help/sites-authoring/basic-handling.md#viewingandselectingyourresources).
1. Open het venster **[Referenties](/help/sites-authoring/basic-handling.md#references)** en selecteer **Launches**.
1. Selecteer uw specifieke lancering toen **Vergelijk met Bron**:

   ![screen-shot_2019-03-05at121952](assets/screen-shot_2019-03-05at121952.png)

1. De twee pagina&#39;s (opstart en bron) worden naast elkaar geopend.

   Zie [Paginadiff](/help/sites-authoring/page-diff.md) voor volledige informatie over het gebruik van deze functie.

## De gebruikte bronpagina&#39;s wijzigen {#changing-the-source-pages-used}

U kunt op elk gewenst moment pagina&#39;s toevoegen aan of verwijderen uit het bereik van bronpagina&#39;s voor een opstart:

1. Open en selecteer de opstart vanuit:

   * de [Startconsole](/help/sites-authoring/launches.md#the-launches-console):

      * Selecteer **Bewerken**.
   * [Referenties (Sites-console)](/help/sites-authoring/launches.md#launches-in-references-sites-console) om de beschikbare acties weer te geven:

      * Selecteer **Starten bewerken**.

   De bronpagina&#39;s worden weergegeven.

1. Breng de gewenste wijzigingen aan en bevestig vervolgens met **Opslaan**.

   >[!NOTE]
   >
   >Als u pagina&#39;s wilt toevoegen aan een opstart, moeten deze zich onder een gemeenschappelijke taalbasis bevinden. d.w.z. binnen één locatie.

## Een opstartconfiguratie bewerken {#editing-a-launch-configuration}

U kunt op elk gewenst moment de eigenschappen voor een opstart bewerken:

1. Open en selecteer de opstart vanuit:

   * de [Startconsole](/help/sites-authoring/launches.md#the-launches-console):

      * Selecteer **Eigenschappen**.
   * [Referenties (Sites-console)](/help/sites-authoring/launches.md#launches-in-references-sites-console) om de beschikbare acties weer te geven:

      * Selecteer **Eigenschappen bewerken**.

   De details worden weergegeven.

1. Breng de gewenste wijzigingen aan en bevestig vervolgens met **Opslaan**.

   Zie [Lanceringen - de volgorde van gebeurtenissen](/help/sites-authoring/launches.md#launches-the-order-of-events) voor informatie over het doel en de interactie van de velden **Startdatum** en **Geschikt voor productie**.

## De opstartstatus van een pagina {#discovering-the-launch-status-of-a-page} opzoeken

De status wordt weergegeven wanneer u een specifieke start selecteert op het tabblad Referenties (zie [Starten in Referenties (Sites Console)](/help/sites-authoring/launches.md#launches-in-references-sites-console)).

![screen-shot_2019-03-05at121901](assets/screen-shot_2019-03-05at121901.png)
