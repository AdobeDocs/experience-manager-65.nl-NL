---
title: Starten bewerken
description: Wanneer een startpagina (of een set pagina's) is gemaakt, kunt u de inhoud van de opstartafbeelding van de pagina's bewerken.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
legacypath: /content/docs/en/aem/6-0/author/site-page-features/launches
exl-id: 21776f42-cd81-459d-b4b9-1d92e0aec164
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# Starten bewerken{#editing-launches}

## Starten van pagina&#39;s bewerken {#editing-launch-pages}

Wanneer een startpagina (of een set pagina&#39;s) is gemaakt, kunt u de inhoud van de opstartafbeelding van de pagina&#39;s bewerken.

1. Open de pagina voor bewerking.
1. In Sidekick, selecteer het **Versioning** lusje, breid dan de **Lanceereenheden** groep uit. De titel van de opstart die momenteel wordt bewerkt, gebruikt een vet lettertype.

   ![&#x200B; chlimage_1-13 &#x200B;](assets/chlimage_1-13.jpeg)

1. Selecteer de lancering die u wilt werken en dan **Schakelaar** klikken.
1. Bewerken starten.

   >[!NOTE]
   >
   >U kunt het **lusje van de Pagina** gebruiken van hulpwerktuig om acties uit te voeren zoals **creeer de Pagina van het Kind**, onder anderen.

## Een opstartconfiguratie bewerken {#editing-a-launch-configuration}

Nadat u een lancering creeert kunt u de lanceringsnaam en de datum van de lancering veranderen. U kunt ook een afbeelding opgeven die u aan het starten wilt koppelen.

1. Open de pagina van het lanceerbeleid ([&#x200B; http://localhost:4502/libs/launches/content/admin.html &#x200B;](http://localhost:4502/libs/launches/content/admin.html)).

1. Selecteer de vereiste lancering en klik **uitgeven** om de dialoog te openen:

   * In het **Algemene** lusje, kunt u uitgeven:

      * **Titel**
      * **Levende Datum**: dit is gelijkwaardig aan de lanceringsdatum
      * **Productie Klaar**

     Zie [&#x200B; Lanceringen - de Orde van Gebeurtenissen &#x200B;](/help/sites-authoring/launches.md#launches-the-order-of-events) voor informatie over het doel en de interactie van deze gebieden.

   * In het **Beeld** lusje, kunt u een beelddossier uploaden.

1. Klik **sparen**.

## De opstartstatus van een pagina vaststellen {#discovering-the-launch-status-of-a-page}

Wanneer u een lancering van een pagina uitgeeft, verschijnt de informatie over de lancering bij de bodem van het **Versioning** lusje van Sidekick:

* De naam van de opstart.
* De tijd sinds de laatste wijziging.
* De gebruiker die de laatste wijziging heeft uitgevoerd.
* De status van de **Klaar 1&rbrace; vlag van de Productie &lbrace;(orange=niet plaats; green=set).**

![&#x200B; chlimage_1-186 &#x200B;](assets/chlimage_1-186.png)
