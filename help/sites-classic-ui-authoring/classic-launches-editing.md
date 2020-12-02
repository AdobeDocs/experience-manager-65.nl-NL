---
title: Lanceringen bewerken
seo-title: Lanceringen bewerken
description: Wanneer een startpagina (of een set pagina's) is gemaakt, kunt u de inhoud bewerken in de opstartafbeelding van de pagina('s).
seo-description: Wanneer een startpagina (of een set pagina's) is gemaakt, kunt u de inhoud bewerken in de opstartafbeelding van de pagina('s).
uuid: 3a310eeb-553d-4d2b-98b5-c5bc523b2aca
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 666b967a-e94b-4f94-a676-00adf150580f
legacypath: /content/docs/en/aem/6-0/author/site-page-features/launches
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 2%

---


# Lanceringen bewerken{#editing-launches}

## Starten van pagina&#39;s bewerken {#editing-launch-pages}

Wanneer een startpagina (of een set pagina&#39;s) is gemaakt, kunt u de inhoud bewerken in de opstartafbeelding van de pagina(&#39;s).

1. Open de pagina voor bewerking.
1. Selecteer in Sidetrap de tab **Versioning** en vouw vervolgens de groep **Launches** uit. De titel van de opstart die momenteel wordt bewerkt, gebruikt een vet lettertype.

   ![chlimage_1-13](assets/chlimage_1-13.jpeg)

1. Selecteer de lancering die u wilt werken en dan **Schakelaar** klikken.
1. Bewerken starten.

   >[!NOTE]
   >
   >Met het tabblad **Pagina** van Help kunt u onder andere handelingen uitvoeren zoals **Onderliggende pagina maken**.

## Een opstartconfiguratie bewerken {#editing-a-launch-configuration}

Nadat u een lancering creeert kunt u de lanceringsnaam en de datum van de lancering veranderen. U kunt ook een afbeelding opgeven die u aan het starten wilt koppelen.

1. Open de startbeleidspagina ([http://localhost:4502/libs/launches/content/admin.html](http://localhost:4502/libs/launches/content/admin.html)).

1. Selecteer de vereiste start en klik op **Bewerken** om het dialoogvenster te openen:

   * Op het tabblad **Algemeen** kunt u:

      * **Titel**
      * **Live datum**: dit komt overeen met de startdatum
      * **Gereed voor productie**

      Zie [Launches - de Orde van Gebeurtenissen](/help/sites-authoring/launches.md#launches-the-order-of-events) voor informatie over het doel en de interactie van deze gebieden.

   * Op het tabblad **Afbeelding** kunt u een afbeeldingsbestand uploaden.


1. Klik **Opslaan**.

## De opstartstatus van een pagina {#discovering-the-launch-status-of-a-page} opzoeken

Wanneer u een lancering van een pagina uitgeeft, verschijnt de informatie over de lancering bij de bodem van **Versioning** lusje van Sidetrap:

* De naam van de opstart.
* De tijd sinds de laatste wijziging.
* De gebruiker die de laatste wijziging heeft uitgevoerd.
* De status van de markering **Production Ready** (orange=niet ingesteld; green=set).

![chlimage_1-186](assets/chlimage_1-186.png)

