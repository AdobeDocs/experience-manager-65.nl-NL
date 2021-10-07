---
title: Beveiliging via hot link activeren in Dynamic Media
description: Informatie over het activeren van de beveiliging van hot links in Dynamic Media.
uuid: 5f93bc27-5edd-4143-8701-87896c52f0af
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
content-type: reference
discoiquuid: a70aa448-0f58-4ed2-9381-afcc76fa827f
role: User, Admin
exl-id: 698e8bdb-9b31-49ab-8560-26b05109bb23
feature: Configuration
source-git-commit: 65af6e33ae3897519491952f4d3a6832700f77b2
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---

# Beveiliging van hot-links activeren in Dynamic Media {#activating-hotlink-protection-in-dynamic-media}

Hot linking wordt gebruikt wanneer een externe website HTML-code gebruikt om een afbeelding van uw website weer te geven. Ze gebruiken uw bandbreedte telkens wanneer de afbeelding wordt opgevraagd, omdat de browser van de bezoeker deze rechtstreeks vanaf uw server opent. Hotlink *protection* is een methode om te voorkomen dat andere websites rechtstreeks een koppeling maken naar afbeeldingen, CSS of JavaScript op uw webpagina&#39;s. Met dit soort schermen vermindert u onnodig bandbreedtegebruik onder uw Dynamic Media-account.

[De ](https://experienceleague.adobe.com/?support-solution=Experience+Manager#support) Steun van de Klant van de Experience Manager kan een verwijzingsfilter op het niveau van CDN (het Netwerk van de Levering van de Inhoud) vormen zodat de inhoud van Dynamic Media slechts aan websites op uw lijst van toegelaten websites voor het domein wordt gediend.

>[!NOTE]
>
>Voor deze functie is het vereist dat u de CDN uit de doos gebruikt die bij Adobe Experience Manager Dynamic Media is gebundeld. Een andere aangepaste CDN wordt niet ondersteund met deze functie. Om hot link-beveiliging te activeren, moet een beheerder een Adobe Customer Support-ticket maken om de configuratiewijziging van uw Dynamic Media-account aan te vragen. Er zijn geen extra kosten voor het activeren van hotlink-beveiliging.
