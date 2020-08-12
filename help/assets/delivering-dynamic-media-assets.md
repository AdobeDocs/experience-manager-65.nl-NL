---
title: Dynamische media-elementen leveren
description: Leer hoe u dynamische media-elementen kunt leveren
uuid: 23eddf83-34f5-4aae-8b81-d1cd7a098a7e
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: e3b44330-d476-49c6-b7ba-079d0d60e500
docset: aem65
translation-type: tm+mt
source-git-commit: 3eacfe8a79d155dddde8908d05b05790d048b0c5
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 1%

---


# Delivering Dynamic Media Assets{#delivering-dynamic-media-assets}

Hoe u dynamische media-elementen kunt leveren (zowel video als afbeeldingen), hangt af van de manier waarop uw website is geïmplementeerd.

Met Dynamische media hebt u verschillende opties:

* Als uw website op AEM wordt gehost, wilt u de dynamische media-elementen rechtstreeks aan uw pagina toevoegen.
* Als uw website niet op AEM staat, kunt u kiezen uit:

   * Uw video of afbeelding insluiten op uw website.
   * Koppel URL&#39;s aan uw webtoepassing. Gebruik koppelingen wanneer u een videospeler wilt leveren als een pop-up- of modaal venster.
   * Als uw site reageert, kunt u geoptimaliseerde afbeeldingen [leveren.](/help/assets/responsive-site.md)

>[!NOTE]
>
>Slimme beeldverwerking werkt met bestaande voorinstellingen voor afbeeldingen en maakt gebruik van intelligentie tijdens de laatste milliseconde van levering om de bestandsgrootte van de afbeelding verder te beperken op basis van de snelheid van de browser of netwerkverbinding. Zie [Slimme afbeeldingen](/help/assets/imaging-faq.md) voor meer informatie.

Raadpleeg de volgende onderwerpen voor meer informatie:

* [Dynamische media-elementen toevoegen aan webpagina&#39;s](/help/assets/adding-dynamic-media-assets-to-pages.md)
* [Video- of afbeeldingsviewer insluiten op een webpagina](/help/assets/embed-code.md)
* [Hotlinkbeveiliging in Dynamic Media activeren](hotlink-protection.md)
* [URL&#39;s koppelen aan uw webtoepassing](/help/assets/linking-urls-to-yourwebapplication.md)
* [Geoptimaliseerde afbeeldingen voor een responsieve site leveren](/help/assets/responsive-site.md)
* [HTTP2 Levering van inhoud](/help/assets/http2.md)
* [Het ongeldig maken van uw CDN geheime voorgeheugen door middel van Dynamic Media Classic](/help/assets/invalidate-cdn-cache-dm-classic.md)
* [Regels gebruiken om URL&#39;s te transformeren](/help/assets/using-rulesets-to-transform-urls.md)


## HTTP/2-levering van Dynamic Media-elementen {#http-delivery-of-dynamic-media-assets}

AEM ondersteunt nu de levering van alle Dynamic Media-inhoud (afbeeldingen en video) via HTTP/2. Dit wil zeggen dat er een gepubliceerde URL of insluitcode voor de afbeelding of video beschikbaar is om te worden geïntegreerd met elke toepassing die een gehoste element accepteert. Dat gepubliceerde element wordt vervolgens geleverd via het HTTP/2-protocol. Deze methode van levering verbetert de manier browsers en servers communiceren, die voor betere reactie en ladingstijden van al uw Dynamische activa van Media toestaan.

Zie [HTTP/2 Levering van Inhoud Veelgestelde Vragen](/help/sites-administering/scene7-http2faq.md) om meer te leren.
