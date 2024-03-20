---
title: Dynamic Media-middelen leveren
description: Leer hoe u Dynamic Media-elementen, zoals video en afbeeldingen, kunt leveren aan uw webpagina's.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
docset: aem65
role: User, Admin
exl-id: 274af114-845a-46bd-b091-802cf589687a
feature: Asset Management,Renditions
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%

---

# Dynamic Media-middelen leveren{#delivering-dynamic-media-assets}

Hoe u uw Dynamic Media-middelen kunt leveren - zowel video als afbeeldingen - hangt af van de manier waarop uw website is geïmplementeerd.

Met Dynamic Media hebt u verschillende opties:

* Als uw website op Adobe Experience Manager wordt gehost, wilt u de Dynamic Media-elementen rechtstreeks aan uw pagina toevoegen.
* Als uw website niet op Experience Manager is, kunt u kiezen uit:

   * Uw video of afbeelding insluiten op uw website.
   * Koppel URL&#39;s aan uw webtoepassing. Gebruik koppelingen wanneer u een videospeler wilt leveren als een pop-up- of modaal venster.
   * Als uw site reageert, kunt u [geoptimaliseerde afbeeldingen leveren](/help/assets/responsive-site.md).

>[!NOTE]
>
>Slimme beeldverwerking werkt met bestaande voorinstellingen voor afbeeldingen en maakt gebruik van intelligentie tijdens de laatste milliseconde van levering om de bestandsgrootte van de afbeelding verder te beperken op basis van de snelheid van de browser of netwerkverbinding. Zie [Slimme afbeeldingen](/help/assets/imaging-faq.md) voor meer informatie .

Raadpleeg de volgende onderwerpen voor meer informatie:

* [Dynamic Media-elementen toevoegen aan webpagina&#39;s](/help/assets/adding-dynamic-media-assets-to-pages.md)
* [De video- of afbeeldingsviewer insluiten op een webpagina](/help/assets/embed-code.md)
* [Hotlink-beveiliging activeren in Dynamic Media](/help/assets/hotlink-protection.md)
* [URL&#39;s koppelen aan uw webtoepassing](/help/assets/linking-urls-to-yourwebapplication.md)
* [Geoptimaliseerde afbeeldingen leveren voor een responsieve site](/help/assets/responsive-site.md)
* [HTTP2-levering van inhoud](/help/assets/http2.md)
* [De CDN-cache ongeldig maken via Dynamic Media Classic](/help/assets/invalidate-cdn-cache-dm-classic.md)
* [Regels gebruiken om URL&#39;s te transformeren](/help/assets/using-rulesets-to-transform-urls.md)


## HTTP/2 levering van Dynamic Media-middelen {#http-delivery-of-dynamic-media-assets}

Experience Manager ondersteunt nu de levering van alle Dynamic Media-inhoud (afbeeldingen en video) via HTTP/2. Dit wil zeggen dat er een gepubliceerde URL of insluitcode voor de afbeelding of video beschikbaar is om te worden geïntegreerd met elke toepassing die een gehoste element accepteert. Dat gepubliceerde element wordt vervolgens geleverd via het HTTP/2-protocol. Deze leveringsmethode verbetert de manier waarop browsers en servers communiceren, waardoor u betere responstijd en laadtijden voor al uw Dynamic Media-middelen krijgt.

Zie voor meer informatie [HTTP/2 levering van inhoud vaak gestelde vragen](/help/sites-administering/scene7-http2faq.md).
