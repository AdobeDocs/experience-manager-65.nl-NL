---
title: HTTP2-levering van inhoud
description: Leer hoe HTTP/2 de manier verbetert browsers en servers communiceren, die voor snellere overdracht van informatie terwijl het verminderen van de hoeveelheid nodig verwerkingscapaciteit toestaan.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
role: User, Admin
exl-id: 9eb9f309-33e5-4694-84d2-fb2cd3de50a6
feature: Publishing,Configuration
solution: Experience Manager, Experience Manager Assets
source-git-commit: f749892bf7fba9889adfc930771178154b92fa5d
workflow-type: tm+mt
source-wordcount: '735'
ht-degree: 0%

---

# HTTP/2-levering van inhoud {#http-delivery-of-content}

Adobe is verheugd de beschikbaarheid van HTTP/2-levering van inhoud aan te kondigen, wat over het algemeen voordeel oplevert van verbeterde prestaties.

>[!NOTE]
>
>Deze functie vereist dat u de uit-van-de-doos CDN gebruikt die met de Dynamische Media van Adobe Experience Manager wordt gebundeld. Een andere aangepaste CDN wordt niet ondersteund met deze functie.

## Wat is HTTP/2? {#what-is-http}

HTTP/2 verbetert de manier waarop browsers en servers communiceren, waardoor informatie sneller kan worden overgedragen en de benodigde hoeveelheid verwerkingskracht wordt verminderd.

De volgende website beschrijft HTTP/2 en de voordelen ervan op een korte en eenvoudige manier:

[ wat u over HTTP/2 ](https://www.engadget.com/2015-02-24-what-you-need-to-know-about-http-2.html) moet weten

## Wat zijn de belangrijkste voordelen van de overgang naar HTTP/2 voor de levering van inhoud? {#what-are-the-key-benefits-of-moving-to-http-for-content-delivery}

Prestatieverbetering kan sterk variëren. Deze is gebaseerd op vele factoren, zoals code van uw website, hoe u Dynamic Media gebruikt, het apparaat, het scherm en de locatie van de consument.

De eigen tests van Adobe leverden de volgende resultaten op:

* Voor afbeeldingen verbeterde de responstijd 7%-28%, afhankelijk van apparaat en browser. De meest opmerkelijke prestatiewinst was op iOS-apparaten.
* Voor viewers verbeterde de laadtijd tot 15%.

<!--
The following demonstration illustrates the difference between HTTP/1 versus HTTP/2 loading:

[https://http2.akamai.com/demo](https://http2.akamai.com/demo) -->

## Mag ik overschakelen op HTTP/2? {#am-i-eligible-to-switch-over-to-http}

Als u HTTP/2 wilt gebruiken, moet u aan de volgende vereisten voldoen:

* Gebruik beveiligde HTTPS voor uw rich media-aanvragen.
* Gebruik de Adobe-gebundelde CDN (content delivery network) als onderdeel van uw Dynamic Media-licentie.
* Gebruik een specifiek (niet-bedrijf-h.assetsadobe#.com) domein.

  Als u al een toegewezen domein hebt, kunt u zich aanmelden via Adobe Klantenondersteuning.

  Als u geen specifiek domein hebt, is Adobe van plan om uw overgang naar HTTP/2 in 2018 te plannen.

## Wat is het proces om HTTP/2 voor mijn Dynamische rekening van Media toe te laten? {#what-is-the-process-for-enabling-http-for-my-dynamic-media-account}

U stelt het verzoek in werking om op HTTP/2 over te schakelen; het wordt niet automatisch gedaan voor u.

1. Als u wilt overschakelen op HTTP/2, start u een Adobe Customer Support-aanvraag. Zie [ een steunkaartje ](https://experienceleague.adobe.com/?support-solution=General&lang=en&support-tab=home#support) openen.

   1. Geef de volgende informatie op in uw supportverzoek:

      1. Primaire contactpersoon, e-mail, telefoon.
      1. Alle domeinen die moeten worden overgezet naar HTTP/2.
      1. Controleer of u beveiligde HTTPS gebruikt voor aanvragen voor rich media.
      1. Verifieer dat u CDN door Adobe gebruikt en niet met een directe verhouding beheerd.
      1. Controleer of u een specifiek domein gebruikt. Als u Dynamische media gebruikt, dan gebruikt u een specifiek domein.

   1. De Steun van de klant voegt u aan de HTTP/2 klantenwachtlijst toe die in de orde wordt gebaseerd waarin de verzoeken werden voorgelegd.
   1. Wanneer Adobe klaar is om uw verzoek af te handelen, neemt de klantenondersteuning contact met u op om de overgang te coördineren en een streefdatum in te stellen.
   1. U wordt op de hoogte gesteld na voltooiing en kunt een geslaagde overgang naar HTTP2 controleren.

      Omdat in de browser dit feit niet wordt vermeld, is het nodig een extensie te downloaden.

      Voor Firefox en Chrome is er een extensie met de naam &quot;HTTP/2 en SPDY Indicator&quot;. Browsers ondersteunen alleen veilig http/2, dus is het nodig een URL met https aan te roepen om te verifiëren. Als http/2 wordt ondersteund, geeft de extensie dit aan. De extensie heeft de vorm van een blauw Flash-symbool en een header `X-Firefox-Spdy` : `h2` .

## Wanneer kan ik verwachten dat de overgang naar HTTP/2 plaatsvindt? {#when-can-i-expect-to-be-transitioned-over-to-http}

Verzoeken worden verwerkt in de volgorde waarin de Klantenondersteuning ze ontvangt.

>[!NOTE]
>
>Er kan een lange aanlooptijd zijn, omdat de overgang naar HTTP/2 het wissen van de cache omvat. Daarom kunnen slechts een paar klantenovergangen tegelijkertijd worden behandeld.

## Wat zijn de risico&#39;s bij de overgang naar HTTP/2? {#what-are-the-risks-with-moving-to-http}

De overgang aan HTTP/2 ontruimt uit uw geheime voorgeheugen bij CDN omdat het het bewegen aan een nieuwe configuratie CDN impliceert.

De inhoud die niet in de cache is opgeslagen, raakt de oorspronkelijke Adobe-servers direct aan totdat de cache opnieuw wordt samengesteld. Als zodanig is Adobe van plan om enkele klantovergangen tegelijk af te handelen, zodat acceptabele prestaties behouden blijven wanneer verzoeken van de oorsprong worden opgehaald.

## Hoe kunt u controleren of een URL of website met HTTP/2 wordt geactiveerd? {#how-can-you-verify-whether-a-url-or-website-is-activated-with-http}

Omdat in de browser dit feit niet wordt vermeld, is het nodig een extensie te downloaden.

Voor Firefox en Chrome is er een extensie met de naam &quot;HTTP/2 en SPDY Indicator&quot;. Browsers ondersteunen alleen veilig http/2, dus is het nodig een URL met https aan te roepen om te verifiëren. Als http/2 wordt ondersteund, wordt dit aangegeven door de extensie. De extensie heeft de vorm van een blauw Flash-symbool en een header `X-Firefox-Spdy` : `h2` .
