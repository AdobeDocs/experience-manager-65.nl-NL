---
title: Geen back-up van database tijdens upgrade naar 6.5.12.0 voor MySQL.
description: Wanneer een gebruiker aan Experience Manager 6.5.12.0 bevordert en "Upgrade MySQL"klikt, ontbreekt de configuratiemanager aan file het vorige Gegevensbestand van Experience Manager Forms.
source-git-commit: bf974331157e21b28c0daa5b878ac927ce5a2304
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 0%

---

# Geen back-up van database tijdens upgrade naar 6.5.12.0 voor MySQL (#issue)

Wanneer een gebruiker aan Experience Manager 6.5.12.0 bevordert en &quot;Upgrade MySQL&quot;klikt, ontbreekt de configuratiemanager aan file het vorige Gegevensbestand van Experience Manager Forms, toont het de fout:

`Failed to backup the previous Adobe Experience Manager Forms Database`


## Van toepassing op {#applies-to}

* Experience Manager 6.5 Forms

## Oplossing {#solution}

Om de kwestie op te lossen, verhoog max_packet_size van het gegevensbestand aan 100 M of zoals vereist in het my.ini- dossier dat bij wordt gevestigd {AEM_HOME}/mysql.
