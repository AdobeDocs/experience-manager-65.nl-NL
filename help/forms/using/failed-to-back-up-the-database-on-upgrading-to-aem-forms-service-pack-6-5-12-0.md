---
title: Geen back-up van database tijdens upgrade naar 6.5.12.0 voor MySQL.
description: Wanneer een gebruiker aan Experience Manager 6.5.12.0 bevordert en "Upgrade MySQL"klikt, ontbreekt de configuratiemanager aan file het vorige Gegevensbestand van Experience Manager Forms.
exl-id: 1af000fa-439b-4ffd-8b5a-3ba45f0c524c
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 0%

---

# Geen back-up van database tijdens upgrade naar 6.5.12.0 voor MySQL {#issue}

Wanneer een gebruiker aan Experience Manager 6.5.12.0 bevordert en &quot;Upgrade MySQL&quot;klikt, ontbreekt de configuratiemanager aan file het vorige Gegevensbestand van Experience Manager Forms, toont het de fout:

`Failed to backup the previous Adobe Experience Manager Forms Database`


## Van toepassing op {#applies-to}

* Experience Manager 6.5 Forms

## Oplossing {#solution}

Om de kwestie op te lossen, verhoog max_packet_size van het gegevensbestand aan 100 M of zoals vereist in het my.ini- dossier dat bij wordt gevestigd {AEM_HOME}/mysql.
