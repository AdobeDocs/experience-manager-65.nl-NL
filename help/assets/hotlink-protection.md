---
title: Beveiliging via hot link activeren in Dynamic Media
description: Informatie over het activeren van de beveiliging van hot links in Dynamic Media.
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
content-type: reference
role: User, Admin
exl-id: 698e8bdb-9b31-49ab-8560-26b05109bb23
feature: Configuration
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---

# Beveiliging van hot-links activeren in Dynamic Media {#activating-hotlink-protection-in-dynamic-media}

Hot linking wordt gebruikt wanneer een externe website HTML-code gebruikt om een afbeelding van uw website weer te geven. Ze gebruiken uw bandbreedte telkens wanneer de afbeelding wordt opgevraagd, omdat de browser van de bezoeker deze rechtstreeks vanaf uw server opent. Hotlink *bescherming* is een methode om te voorkomen dat andere websites rechtstreeks koppelingen maken naar afbeeldingen, CSS of JavaScript op uw webpagina&#39;s. Met dit soort schermen vermindert u onnodig bandbreedtegebruik onder uw Dynamic Media-account.

[Klantenondersteuning Experience Manager](https://experienceleague.adobe.com/?support-solution=Experience+Manager#support) U kunt een verwijzingsfilter op het niveau van CDN (het Netwerk van de Levering van de Inhoud) vormen zodat de inhoud van Dynamic Media slechts aan websites op uw lijst van toegelaten websites voor het domein wordt gediend.

>[!NOTE]
>
>Voor deze functie is het vereist dat u de CDN uit de doos gebruikt die bij Adobe Experience Manager Dynamic Media is gebundeld. Een andere aangepaste CDN wordt niet ondersteund met deze functie. Om hot link-beveiliging te activeren, moet een beheerder een Adobe maken voor Klantenondersteuning om de configuratiewijziging van uw Dynamic Media-account aan te vragen. Er zijn geen extra kosten voor het activeren van hotlink-beveiliging.
