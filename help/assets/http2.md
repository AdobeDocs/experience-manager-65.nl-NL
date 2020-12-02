---
title: HTTP2 Levering van inhoud
description: HTTP/2 verbetert de manier waarop browsers en servers communiceren, waardoor informatie sneller kan worden overgedragen en de hoeveelheid benodigde verwerkingskracht wordt verminderd.
uuid: d9deb945-bdf5-4d6b-95c8-8bae4442e618
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: c8e145ad-f021-4043-8190-62151775e296
translation-type: tm+mt
source-git-commit: 0595d89409e0ca21f771be5c55c3ec9548a8449f
workflow-type: tm+mt
source-wordcount: '705'
ht-degree: 0%

---


# HTTP2 Levering van inhoud {#http-delivery-of-content}

Adobe is opgetogen om de beschikbaarheid van HTTP/2 levering van inhoud aan te kondigen met het algemene voordeel van betere prestaties.

## Wat is HTTP/2? {#what-is-http}

HTTP/2 verbetert de manier waarop browsers en servers communiceren, waardoor informatie sneller kan worden overgedragen en de benodigde hoeveelheid verwerkingskracht wordt verminderd.

De volgende website beschrijft HTTP/2 en zijn voordelen op een korte en eenvoudige manier:

[https://www.engadget.com/2015/02/24/what-you-need-to-know-about-http-2/](https://www.engadget.com/2015/02/24/what-you-need-to-know-about-http-2/)

## Wat zijn de belangrijkste voordelen van de overgang naar HTTP/2 voor de levering van inhoud? {#what-are-the-key-benefits-of-moving-to-http-for-content-delivery}

Prestatieverbetering varieert sterk op basis van factoren zoals de code van uw website, hoe u Dynamic Media gebruikt, het apparaat van de consument, het scherm en de locatie, enzovoort.

Resultaten:

* Voor afbeeldingen verbeterde de responstijd 7%-28%, afhankelijk van het apparaat en de browser. De meest opmerkelijke prestatiewinst was op iOS-apparaten.
* Voor viewers verbeterde de laadtijd tot 15%.

De volgende demonstratie illustreert het verschil tussen het laden van HTTP/1 en HTTP/2:

[https://http2.akamai.com/demo](https://http2.akamai.com/demo)

## Mag ik overschakelen op HTTP/2? {#am-i-eligible-to-switch-over-to-http}

Als u HTTP/2 wilt gebruiken, moet u aan de volgende vereisten voldoen:

* Gebruik beveiligde HTTPS voor uw rich media-aanvragen.
* Gebruik de Adobe-gebundelde CDN (content delivery network) als onderdeel van uw Dynamic Media-licentie.
* Gebruik een specifiek (niet-bedrijf-h.assetsadobe#.com) domein.

   Als u al een specifiek domein hebt, kunt u zich aanmelden via Technische ondersteuning.

   Als u geen specifiek domein hebt, zal Adobe uw overgang aan HTTP/2 in 2018 plannen.

## Wat is het proces om HTTP/2 voor mijn Dynamische rekening van Media toe te laten? {#what-is-the-process-for-enabling-http-for-my-dynamic-media-account}

U moet het verzoek in werking stellen om op HTTP/2 over te schakelen; het wordt niet automatisch voor u gedaan.

1. Initieer een verzoek van de Technische Steun om op HTTP2 over te schakelen. Zie [Toegang tot het AEM Support Portal](https://helpx.adobe.com/experience-manager/kb/accessing-aem-support-portal.html).

   1. Geef de volgende informatie op in uw supportverzoek:

      1. Primaire contactpersoon, e-mail, telefoon.
      1. Alle domeinen die naar HTTP2 moeten worden overgebracht.
      1. Verifieer u veilige HTTPS voor rijke media verzoeken gebruikt.
      1. Verifieer u CDN door Adobe gebruikt en niet met een directe verhouding beheerd.
      1. Controleer of u een specifiek domein gebruikt. Als u Dynamische media gebruikt, dan gebruikt u reeds een specifiek domein.
   1. De technische Steun zal u aan HTTP/2 klantenwachtlijst toevoegen die in de orde wordt gebaseerd waarin de verzoeken werden voorgelegd.
   1. Wanneer Adobe klaar is om uw verzoek te behandelen, zal de steun u contacteren om de overgang te coördineren en een doeldatum te plaatsen.
   1. U wordt op de hoogte gesteld na voltooiing en u kunt controleren of de overgang naar HTTP2 is gelukt.

      Omdat in de browser dit feit niet wordt vermeld, is het nodig een extensie te downloaden.

      Voor Firefox en Chrome is er een extensie genaamd &quot;HTTP/2 en SPDY Indicator&quot;. Browsers ondersteunen alleen veilig http/2, dus is het nodig een URL met https aan te roepen om te verifiëren. Als http/2 wordt ondersteund, wordt dit aangegeven door de extensie in de vorm van een blauw Flash-symbool en een header &quot;X-Firefox-Spdy&quot;: &quot;h2&quot;.


## Wanneer kan ik verwachten over te gaan naar HTTP/2? {#when-can-i-expect-to-be-transitioned-over-to-http}

Verzoeken worden behandeld in de volgorde waarin ze door Technische Ondersteuning worden ontvangen.

>[!NOTE]
>
>Er kan een lange aanlooptijd zijn omdat de overgang naar HTTP/2 het wissen van de cache omvat. Daarom kunnen slechts een paar klantenovergangen tegelijkertijd worden behandeld.

## Wat zijn de risico&#39;s bij de overgang naar HTTP/2? {#what-are-the-risks-with-moving-to-http}

De overgang aan HTTP/2 ontruimt uit uw geheime voorgeheugen bij CDN omdat het het bewegen aan een nieuwe configuratie CDN impliceert.

De inhoud in de cache raakt de servers van Adobe die niet in de cache zijn opgeslagen, rechtstreeks aan. Wegens dit, is Adobe van plan om een paar klantenovergangen in een tijd te behandelen zodat de aanvaardbare prestaties worden gehandhaafd wanneer het trekken van verzoeken van onze oorsprong.

## Hoe kunt u controleren of een URL of website met HTTP/2 wordt geactiveerd? {#how-can-you-verify-whether-a-url-or-website-is-activated-with-http}

Omdat in de browser dit feit niet wordt vermeld, is het nodig een extensie te downloaden.

Voor Firefox en Chrome is er een extensie genaamd &quot;HTTP/2 en SPDY Indicator&quot;. Browsers ondersteunen alleen veilig http/2, dus is het nodig een URL met https aan te roepen om te verifiëren. Als http/2 wordt ondersteund, wordt dit aangegeven door de extensie in de vorm van een blauw Flash-symbool en een header &quot;X-Firefox-Spdy&quot;: &quot;h2&quot;.
