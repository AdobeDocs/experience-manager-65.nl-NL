---
title: Starten bewerken
description: Nadat u een opstartafbeelding voor de pagina (of set pagina's) hebt gemaakt, kunt u de inhoud bewerken in de opstartafbeelding van de pagina's.
contentOwner: AEM Docs
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
docset: aem65
legacypath: /content/docs/en/aem/6-0/author/site-page-features/launches
exl-id: 2d441820-b394-47c8-b4ca-a8aede590937
solution: Experience Manager, Experience Manager Sites
feature: Authoring,Launches
role: User,Admin,Architect,Developer
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 17%

---

# Starten bewerken{#editing-launches}

## Starten van pagina&#39;s bewerken {#editing-launch-pages}

Wanneer een startpagina (of een set pagina&#39;s) is gemaakt, kunt u de inhoud bewerken in de opstartafbeelding van de pagina&#39;s.

1. Heb toegang tot [ Lancering van Verwijzingen (de console van Plaatsen) ](/help/sites-authoring/launches.md#launches-in-references-sites-console) om de beschikbare acties te tonen.
1. Selecteer **gaan naar de pagina** om de pagina voor het uitgeven te openen.

>[!NOTE]
>
>U mag een pagina niet verplaatsen binnen een startperiode. Als u deze handeling uitvoert, wordt een waarschuwingsbericht weergegeven:
>
>* Waarschuwing: deze pagina is de bron van een opstart. Het verplaatsen van de pagina is niet toegestaan.

### Pagina&#39;s starten bewerken die zijn onderworpen aan een live kopie {#editing-launch-pages-subject-to-a-live-copy}

Als uw lancering op a [ levend exemplaar ](/help/sites-administering/msm.md) dan gebaseerd is zult u:

* zie vergrendelingssymbolen (kleine hangsloten) wanneer u een component (inhoud en/of eigenschappen) bewerkt.
* zie het **Levende lusje van het Exemplaar** in **Eigenschappen van de Pagina**

Een livekopie wordt gebruikt om content te synchroniseren *van* de bronvertakking *naar* de startvertakking (om uw lancering up-to-date te houden als er veranderingen in de bron worden aangebracht).

U kunt wijzigingen aanbrengen op dezelfde manier als u een standaard live kopie kunt bewerken, bijvoorbeeld:

* Als u op een gesloten hangslot klikt, wordt deze synchronisatie verbroken en kunt u nieuwe updates voor de inhoud uitvoeren wanneer u de toepassing start. Als de vergrendeling is opgeheven (open hanglock), worden de wijzigingen niet overschreven door wijzigingen die op dezelfde locatie in de bronvertakking zijn aangebracht.
* **Overname** voor een bepaalde pagina onderbreken (en **hervatten**).

Zie [ Veranderend Levende Inhoud van het Exemplaar ](/help/sites-administering/msm-livecopy.md#changing-live-copy-content) voor verdere informatie.

## Een startpagina vergelijken met de bijbehorende Source-pagina {#comparing-a-launch-page-to-its-source-page}

Als u de door u aangebrachte wijzigingen wilt bijhouden, kunt u de start weergeven in **Referenties** en de startpagina vergelijken met de bijbehorende bronpagina:

1. In de **console van Plaatsen**, [ navigeer aan de bronpagina van uw lancering en selecteer het ](/help/sites-authoring/basic-handling.md#viewingandselectingyourresources).
1. Open het **[paneel van Verwijzingen](/help/sites-authoring/basic-handling.md#references)** en selecteer **Lanceringen**.
1. Selecteer uw specifieke lancering toen **vergelijk met Source**:

   ![ scherm-shot_2019-03-05at121952 ](assets/screen-shot_2019-03-05at121952.png)

1. De twee pagina&#39;s (opstart en bron) worden naast elkaar geopend.

   Voor volledige informatie over het gebruiken van deze eigenschap zie [ Afschuiving van de Pagina ](/help/sites-authoring/page-diff.md).

## De gebruikte Source-pagina&#39;s wijzigen {#changing-the-source-pages-used}

U kunt op elk gewenst moment pagina&#39;s toevoegen aan of verwijderen uit het bereik van bronpagina&#39;s voor een opstart:

1. Open en selecteer de opstart vanuit:

   * de [ console van Lanceringen ](/help/sites-authoring/launches.md#the-launches-console):

      * Selecteer **uitgeven**.

   * [ Verwijzingen (de console van Plaatsen) ](/help/sites-authoring/launches.md#launches-in-references-sites-console) om de beschikbare acties te tonen:

      * Selecteer **uitgeven Lancering**.

   De bronpagina&#39;s worden weergegeven.

1. Breng de gewenste wijzigingen aan en bevestig vervolgens met **Opslaan**.

   >[!NOTE]
   >
   >Als u pagina&#39;s wilt toevoegen aan een introductie, moeten deze zich onder een gemeenschappelijke hoofdtaalmap bevinden, dat wil zeggen binnen één site.

## Een opstartconfiguratie bewerken {#editing-a-launch-configuration}

U kunt op elk gewenst moment de eigenschappen voor een opstart bewerken:

1. Open en selecteer de opstart vanuit:

   * de [ console van Lanceringen ](/help/sites-authoring/launches.md#the-launches-console):

      * Selecteer **Eigenschappen**.

   * [ Verwijzingen (de console van Plaatsen) ](/help/sites-authoring/launches.md#launches-in-references-sites-console) om de beschikbare acties te tonen:

      * Selecteer **uitgeven Eigenschappen**.

   De details worden weergegeven.

1. Breng de gewenste wijzigingen aan en bevestig vervolgens met **Opslaan**.

   Zie [Lanceringen - de volgorde van gebeurtenissen](/help/sites-authoring/launches.md#launches-the-order-of-events) voor informatie over het doel en de interactie van de velden **Startdatum** en **Geschikt voor productie**.

## De opstartstatus van een pagina vaststellen {#discovering-the-launch-status-of-a-page}

De status wordt getoond wanneer u een specifieke lancering van het verwijzingenlusje selecteert (zie [ Lanceringen in Verwijzingen (de Console van Plaatsen) ](/help/sites-authoring/launches.md#launches-in-references-sites-console)).

![ scherm-shot_2019-03-05at121901 ](assets/screen-shot_2019-03-05at121901.png)
