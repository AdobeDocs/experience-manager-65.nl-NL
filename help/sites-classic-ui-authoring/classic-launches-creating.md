---
title: Starten maken
seo-title: Starten maken
description: Maak een lancering om het bijwerken van een nieuwe versie van bestaande Web-pagina's voor toekomstige activering toe te laten. Wanneer u een Starten creeert, specificeert u een titel en de bronpagina.
seo-description: Maak een lancering om het bijwerken van een nieuwe versie van bestaande Web-pagina's voor toekomstige activering toe te laten. Wanneer u een Starten creeert, specificeert u een titel en de bronpagina.
uuid: e67608a9-e6c9-42f3-bd1d-63a5fa87ae18
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 48826f03-6731-49c5-a6c5-6e2fb718f912
legacypath: /content/docs/en/aem/6-0/author/site-page-features/launches
translation-type: tm+mt
source-git-commit: 016c705230dffec052c200b058a36cdbe0520fc4

---


# Starten maken{#creating-launches}

Maak een lancering om het bijwerken van een nieuwe versie van bestaande Web-pagina&#39;s voor toekomstige activering toe te laten. Wanneer u een Starten creeert, specificeert u een titel en de bronpagina:

* De titel wordt weergegeven in de **Sidetrap**, waar auteurs ze kunnen openen om aan hen te werken.
* De onderliggende pagina&#39;s van de bronpagina worden standaard in de opstart opgenomen. U kunt desgewenst alleen de bronpagina gebruiken.
* Standaard worden de startpagina&#39;s automatisch bijgewerkt door [Live Copy](/help/sites-administering/msm.md) . U kunt opgeven dat er een statische kopie wordt gemaakt om automatische wijzigingen te voorkomen.

U kunt desgewenst de datum **(en de tijd) van** start opgeven om te bepalen wanneer de startpagina&#39;s moeten worden bevorderd en geactiveerd. Nochtans werkt de Datum **van de** Lancering slechts in combinatie met de Klaar **vlag van de** Productie (zie het [Uitgeven van een Configuratie](/help/sites-classic-ui-authoring/classic-launches-editing.md#editing-a-launch-configuration)van de Lancering); voor de acties om automatisch te voorkomen, moeten beide worden geplaatst.

## Starten maken {#creating-a-launch}

De volgende procedure leidt tot een lancering.

1. Open de pagina Website Administration ([http://localhost:4502/siteadmin](http://localhost:4502/siteadmin)).
1. **** Klik op **Nieuw... vervolgens** Nieuwe start... .
1. Geef in het dialoogvenster **Starten** maken waarden op voor de volgende eigenschappen:

   * **Titel** starten: De naam van de Launch. De naam moet zinvol zijn voor auteurs.
   * **Bronpagina**: Het pad naar de pagina waarvoor de introductie moet worden gemaakt. Standaard worden alle onderliggende pagina&#39;s opgenomen.
   * **Subpagina&#39;s** uitsluiten: Selecteer deze optie als u alleen de startpagina wilt starten en niet de onderliggende pagina&#39;s. Deze optie is standaard niet geselecteerd.
   * **Sync** houden: Selecteer deze optie als u de inhoud van startpagina&#39;s automatisch wilt bijwerken wanneer de bronpagina&#39;s veranderen. Dit wordt bereikt door van de lancering een [levende kopie](/help/sites-administering/msm.md)te maken.
   * **Startdatum**: de datum en het tijdstip waarop de lanceerkopie moet worden geactiveerd (afhankelijk van de markering **Productie gereed** ; zie [Launches - de Orde van Gebeurtenissen](/help/sites-authoring/launches.md#launches-the-order-of-events)).
   ![chlimage_1-99](assets/chlimage_1-99a.png)

1. Klik op **Maken**.

## Een Starten verwijderen {#deleting-a-launch}

U kunt ook een opstart verwijderen.

1. Selecteer in de [startconsole](/help/sites-classic-ui-authoring/classic-launches.md)de vereiste opstart.
1. Klik op **Verwijderen** - bevestiging is vereist:

   ![chlimage_1-100](assets/chlimage_1-100a.png)

   >[!CAUTION]
   >
   >Wanneer u geneste startpunten verwijdert, moet u eerst lagere niveaus verwijderen.

