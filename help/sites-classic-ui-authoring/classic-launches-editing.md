---
title: Lanceringen bewerken
seo-title: Editing Launches
description: Wanneer een startpagina (of een set pagina's) is gemaakt, kunt u de inhoud bewerken in de opstartafbeelding van de pagina('s).
seo-description: When a launch has been created for a page (or set of pages) you can edit the content in the launch copy of the page(s).
uuid: 3a310eeb-553d-4d2b-98b5-c5bc523b2aca
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 666b967a-e94b-4f94-a676-00adf150580f
legacypath: /content/docs/en/aem/6-0/author/site-page-features/launches
exl-id: 21776f42-cd81-459d-b4b9-1d92e0aec164
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 1%

---

# Lanceringen bewerken{#editing-launches}

## Starten van pagina&#39;s bewerken {#editing-launch-pages}

Wanneer een startpagina (of een set pagina&#39;s) is gemaakt, kunt u de inhoud bewerken in de opstartafbeelding van de pagina(&#39;s).

1. Open de pagina voor bewerking.
1. Selecteer in Sidetrap de optie **Versioning** en vouwt vervolgens de **Starten** groep. De titel van de opstart die momenteel wordt bewerkt, gebruikt een vet lettertype.

   ![chlimage_1-13](assets/chlimage_1-13.jpeg)

1. Selecteer de start waaraan u wilt werken en klik op **Overschakelen**.
1. Bewerken starten.

   >[!NOTE]
   >
   >U kunt de **Pagina** tabblad van het hulpprogramma om handelingen uit te voeren zoals **Onderliggende pagina maken**, onder andere.

## Een opstartconfiguratie bewerken {#editing-a-launch-configuration}

Nadat u een lancering creeert kunt u de lanceringsnaam en de datum van de lancering veranderen. U kunt ook een afbeelding opgeven die u aan het starten wilt koppelen.

1. Open de startpagina ([http://localhost:4502/libs/launches/content/admin.html](http://localhost:4502/libs/launches/content/admin.html)).

1. Selecteer de vereiste start en klik op **Bewerken** om het dialoogvenster te openen:

   * In de **Algemeen** kunt u bewerken:

      * **Titel**
      * **LiveDate**: dit komt overeen met de startdatum
      * **Gereed voor productie**

      Zie [Starten - de volgorde van gebeurtenissen](/help/sites-authoring/launches.md#launches-the-order-of-events) voor informatie over het doel en de interactie van deze velden.

   * In de **Afbeelding** kunt u een afbeeldingsbestand uploaden.


1. Klikken **Opslaan**.

## De opstartstatus van een pagina vaststellen {#discovering-the-launch-status-of-a-page}

Als u een startpagina bewerkt, wordt onder aan het dialoogvenster **Versioning** tabblad Sidetrap:

* De naam van de opstart.
* De tijd sinds de laatste wijziging.
* De gebruiker die de laatste wijziging heeft uitgevoerd.
* De status van de **Gereed voor productie** markering (orange=niet ingesteld; green=set).

![chlimage_1-186](assets/chlimage_1-186.png)
