---
title: Starten maken
description: Maak een lancering om het bijwerken van een nieuwe versie van bestaande Web-pagina's voor toekomstige activering toe te laten. Wanneer u een Starten creeert, specificeert u een titel en de bronpagina.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
legacypath: /content/docs/en/aem/6-0/author/site-page-features/launches
exl-id: 8ab21067-c19a-4faa-8bf0-cd9f21f6df70
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 13%

---

# Starten maken{#creating-launches}

Maak een lancering om het bijwerken van een nieuwe versie van bestaande Web-pagina&#39;s voor toekomstige activering toe te laten. Wanneer u een Starten creeert, specificeert u een titel en de bronpagina:

* De titel wordt weergegeven in het dialoogvenster **Sidekick**, van waaruit auteurs toegang hebben om aan hen te werken.
* De onderliggende pagina&#39;s van de bronpagina worden standaard in de opstart opgenomen. U kunt desgewenst alleen de bronpagina gebruiken.
* Standaard, [Live kopie](/help/sites-administering/msm.md) werkt automatisch de startpagina&#39;s bij terwijl de bronpagina&#39;s veranderen. U kunt opgeven dat er een statische kopie wordt gemaakt om automatische wijzigingen te voorkomen.

U kunt desgewenst de **Startdatum** (en -tijd) opgeven om te bepalen wanneer de startpagina&#39;s moeten worden gepromoveerd en geactiveerd. De **startdatum** werkt echter alleen in combinatie met de markering **Geschikt voor productie** (zie [Een startconfiguratie bewerken](/help/sites-classic-ui-authoring/classic-launches-editing.md#editing-a-launch-configuration)). Opdat de acties automatisch zouden optreden, moeten beide worden ingesteld.

## Starten maken {#creating-a-launch}

De volgende procedure leidt tot een lancering.

1. De pagina Website Administration ([http://localhost:4502/siteadmin](http://localhost:4502/siteadmin)).
1. Klikken **Nieuw...** dan **Nieuwe start...**.
1. In de **Starten maken** geeft u waarden op voor de volgende eigenschappen:

   * **Titel starten**: De naam van de Launch. De naam moet zinvol zijn voor auteurs.
   * **Bronpagina**: Het pad naar de pagina waarvoor de introductie moet worden gemaakt. Standaard worden alle onderliggende pagina&#39;s opgenomen.
   * **Subpagina&#39;s uitsluiten**: Selecteer deze optie als u alleen de startpagina en niet de onderliggende pagina&#39;s wilt starten. Deze optie is standaard niet geselecteerd.
   * **Synchronisatie behouden**: Selecteer deze optie als u de inhoud van startpagina&#39;s automatisch wilt bijwerken wanneer de bronpagina&#39;s veranderen. Dit wordt bereikt door de lancering van [live kopie](/help/sites-administering/msm.md).
   * **Opstartdatum**: De datum en tijd waarop de opstartafbeelding moet worden geactiveerd (afhankelijk van de **Gereed voor productie** markering; zie [Starten - de volgorde van gebeurtenissen](/help/sites-authoring/launches.md#launches-the-order-of-events)).

   ![chlimage_1-99](assets/chlimage_1-99a.png)

1. Klikken **Maken**.

## Een Starten verwijderen {#deleting-a-launch}

U kunt ook een opstart verwijderen.

1. In de [opstartconsole](/help/sites-classic-ui-authoring/classic-launches.md)selecteert u de gewenste opstart.
1. Klikken **Verwijderen** - bevestiging is vereist:

   ![chlimage_1-100](assets/chlimage_1-100a.png)

   >[!CAUTION]
   >
   >Wanneer u geneste startpunten verwijdert, moet u eerst lagere niveaus verwijderen.
