---
title: Upgradeprocedure
description: Meer informatie over de procedure voor het upgraden van Adobe Experience Manager (AEM).
contentOwner: sarchiz
topic-tags: upgrading
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
docset: aem65
targetaudience: target-audience upgrader
feature: Upgrading
exl-id: 5242600c-2281-46f9-a347-d985b4e319b3
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 0%

---

# Upgradeprocedure {#upgrade-procedure}

>[!NOTE]
>
>De upgrade vereist downtime voor de Auteur-laag, aangezien de meeste Adobe Experience Manager-upgrades (AEM) op hun plaats worden uitgevoerd. Door deze beste praktijken te volgen, kunt u Publish laagonderbreking minimaliseren of elimineren.

Wanneer u uw AEM-omgevingen upgradet, moet u rekening houden met de verschillen in aanpak tussen het upgraden van de auteursomgevingen of het publiceren van omgevingen om downtime voor zowel uw auteurs als eindgebruikers te minimaliseren. Deze pagina schetst de procedure op hoog niveau voor de bevordering van een AEM topologie die momenteel op een versie van AEM 6.x loopt. Omdat het proces tussen auteur en publicatielagen en op Mongo en TarMK gebaseerde plaatsingen verschilt, is elke rij en microkernel vermeld in een afzonderlijke sectie. Wanneer het uitvoeren van uw plaatsing, adviseert de Adobe eerst uw auteursmilieu te bevorderen, bepalend succes, en dan aan de publicatiemilieu&#39;s te werk te gaan.

<!--
>[!IMPORTANT]
>
>The downtime during the upgrade can be significally reduced by indexing the repository before performing the upgrade. For more information, see [Using Offline Reindexing To Reduce Downtime During an Upgrade](/help/sites-deploying/upgrade-offline-reindexing.md)
-->

## TarMK-auteurreeks {#tarmk-author-tier}

### Begintopologie {#starting-topology}

De veronderstelde topologie voor deze sectie bestaat uit een server van de Auteur die op TarMK met een Koude Reserve loopt. De replicatie komt van de server van de Auteur aan TarMK voor publiceert landbouwbedrijf. Hoewel hier niet geïllustreerd, kan deze benadering ook voor plaatsingen worden gebruikt die het ontladen gebruiken. Zorg ervoor om de het ontladen instantie op de nieuwe versie te bevorderen of te herbouwen na het onbruikbaar maken van replicatieagenten op de instantie van de Auteur en alvorens hen opnieuw toe te laten.

![tarmk_starting_topologie](assets/tarmk_starting_topology.jpg)

### Voorbereiding upgrade {#upgrade-preparation}

![upgrade-voorbereiding-auteur](assets/upgrade-preparation-author.png)

1. Inhoud niet schrijven.

1. Stop de stand-by instantie.

1. Schakel replicatieagents op de auteur uit.

1. Voer de [onderhoudstaken voorafgaand aan de upgrade](/help/sites-deploying/pre-upgrade-maintenance-tasks.md).

### Uitvoering upgrade {#upgrade-execution}

![execute_upgrade](assets/execute_upgrade.jpg)

1. Voer de [upgrade ter plekke](/help/sites-deploying/in-place-upgrade.md).
1. De module Dispatcher bijwerken *indien nodig*.

1. QA valideert de verbetering.

1. Sluit de instantie van de auteur af.

### Indien gelukt {#if-successful}

![if_success](assets/if_successful.jpg)

1. Kopieer de geüpgrade instantie om een koude stand-by te maken.

1. Start de instantie Auteur.

1. Start de Standby-instantie.

### Indien mislukt (Terugdraaien) {#if-unsuccessful-rollback}

![terugdraaien](assets/rollback.jpg)

1. Start de Cold Standby-instantie als de nieuwe primaire instantie.

1. Maak de Auteur-omgeving opnieuw vanuit de koude stand-by.

## Auteurscluster MongoMK {#mongomk-author-cluster}

### Begintopologie {#starting-topology-1}

De veronderstelde topologie voor deze sectie bestaat uit een cluster van de Auteur MongoMK met minstens twee AEM instanties van de Auteur, gesteund door minstens twee gegevensbestanden MongoMK. Alle instanties van Auteurs delen een datastore. Deze stappen zouden op zowel S3 als de datastores van het Dossier moeten van toepassing zijn. De replicatie komt van de servers van de Auteur aan het TarMK voor publiceert landbouwbedrijf.

![mongotopologie](assets/mongo-topology.jpg)

### Voorbereiding upgrade {#upgrade-preparation-1}

![mongo-upgrade_prep](assets/mongo-upgrade_prep.jpg)

1. Inhoud niet schrijven.
1. Kloont de gegevensopslag voor back-up.
1. Stop op één na alle AEM instantie Auteur, uw primaire auteur.
1. Verwijder op één na alle MongoDB-knooppunten uit de replicaset, uw primaire Mongo-instantie.
1. Werk de `DocumentNodeStoreService.cfg` bestand op de primaire auteur om de replicaset voor één lid weer te geven.
1. Start de primaire auteur opnieuw om ervoor te zorgen dat deze opnieuw op de juiste wijze wordt opgestart.
1. Schakel replicatieagents op de primaire auteur uit.
1. Uitvoeren [onderhoudstaken voorafgaand aan de upgrade](/help/sites-deploying/pre-upgrade-maintenance-tasks.md) op de primaire instantie Auteur.
1. Indien nodig, bevorder MongoDB op de primaire instantie Mongo aan versie 3.2 met WiredTiger.

### Uitvoering upgrade {#Upgrade-execution-1}

![mongo-uitvoering](assets/mongo-execution.jpg)

1. Een [upgrade ter plekke](/help/sites-deploying/in-place-upgrade.md) op de primaire auteur.
1. De Dispatcher of de Module van het Web bijwerken *indien nodig*.
1. QA valideert de verbetering.

### Indien gelukt {#if-successful-1}

![mongo-gedetacheerde](assets/mongo-secondaries.jpg)

1. Maak nieuwe 6.5 Auteur-instanties die zijn verbonden met de geüpgrade Mongo-instantie.

1. Maak de MongoDB-knooppunten die uit de cluster zijn verwijderd, opnieuw.

1. Werk de `DocumentNodeStoreService.cfg` bestanden om de volledige replicaset weer te geven.

1. Start de instanties Auteur opnieuw, één voor één.

1. Verwijder de gekloonde gegevensopslag.

### Indien mislukt (Terugdraaien)  {#if-unsuccessful-rollback-2}

![mongo-rollback](assets/mongo-rollback.jpg)

1. Wijzig de secundaire instanties van de Auteur om met de gekloonde gegevensopslag te verbinden.

1. Sluit de bijgewerkte primaire instantie van Auteur.

1. Sluit de bijgewerkte primaire instantie van Mongo af.

1. Start de secundaire Mongo-instanties op met een van hen als de nieuwe primaire instantie.

1. Vorm `DocumentNodeStoreService.cfg` bestanden op de instanties van de secundaire auteur verwijzen naar de replicaset van nog niet bijgewerkte Mongo-instanties.

1. Start de secundaire Auteur-instanties op.

1. Maak de bijgewerkte auteur-instanties, het Mongo-knooppunt en de gegevensopslag leeg.

## TarMK Publish Farm {#tarmk-publish-farm}

### TarMK Publish Farm {#tarmk-publish-farm-1}

De veronderstelde topologie voor deze sectie bestaat uit twee te publiceren TarMK instanties, die door Dispatchers worden geleid die beurtelings door een taakverdelingsmechanisme worden voorafgegaan. De replicatie komt van de server van de Auteur aan het TarMK voor publiceert landbouwbedrijf.

![tarmk-pub-farmv5](assets/tarmk-pub-farmv5.png)

### Uitvoering upgrade {#upgrade-execution-2}

![upgrade-publish2](assets/upgrade-publish2.png)

1. Stop het verkeer naar de instantie Publish 2 bij het taakverdelingsmechanisme.
1. Uitvoeren [onderhoud vóór upgrade](/help/sites-deploying/pre-upgrade-maintenance-tasks.md) op Publicatie 2.
1. Een [upgrade ter plekke](/help/sites-deploying/in-place-upgrade.md) op Publicatie 2.
1. De Dispatcher of de Module van het Web bijwerken *indien nodig*.
1. Maak de Dispatcher-cache leeg.
1. QA valideert Publish 2 door Dispatcher, achter de firewall.
1. Uitschakelen Publicatie 2.
1. Kopieer het exemplaar Publish 2.
1. Publiceren starten 2.

### Indien gelukt {#if-successful-2}

![upgrade-publish1](assets/upgrade-publish1.png)

1. Laat verkeer toe om 2 te publiceren.
1. Stop verkeer naar Publiceren 1.
1. Stop de instantie Publish 1.
1. Vervang de instantie Publish 1 door een kopie van Publish 2.
1. De Dispatcher of de Module van het Web bijwerken *indien nodig*.
1. Maak de Dispatcher-cache leeg voor Publiceren 1.
1. Start Publish 1.
1. QA valideert Publish 1 door Dispatcher, achter de firewall.

### Indien mislukt (Terugdraaien) {#if-unsuccessful-rollback-1}

![pub_rollback](assets/pub_rollback.jpg)

1. Maak een kopie van Publiceren 1.
1. Vervang de instantie Publish 2 door een kopie van Publish 1.
1. Maak de Dispatcher-cache leeg voor Publiceren 2.
1. Publiceren starten 2.
1. QA valideert Publish 2 door Dispatcher, achter de firewall.
1. Laat verkeer toe om 2 te publiceren.

## Eindstappen voor upgrade {#final-upgrade-steps}

1. Laat verkeer toe om 1 te publiceren.
1. QA voert definitieve bevestiging van een openbare URL uit.
1. Schakel replicatieagents in de auteuromgeving.
1. Inhoud opnieuw ontwerpen.
1. Uitvoeren [controles na de upgrade](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md).

![final](assets/final.jpg)
