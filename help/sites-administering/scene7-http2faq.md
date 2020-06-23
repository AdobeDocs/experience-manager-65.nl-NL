---
title: Veelgestelde vragen over HTTP2-levering van content
seo-title: Veelgestelde vragen over HTTP2-levering van content
description: Meer informatie over de levering van HTTP2-inhoud.
seo-description: Meer informatie over de levering van HTTP2-inhoud.
uuid: e837c3e0-6e48-46f1-b510-847c9976807a
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: afbe9f80-c2a3-4a46-b9d6-4c9406667d7f
translation-type: tm+mt
source-git-commit: e916f70549197ac9f95443e972401a78735b0560
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 2%

---


# Veelgestelde vragen over HTTP2-levering van content{#http-delivery-of-content-faq}

Adobe maakt het spannend om de beschikbaarheid van HTTP/2-levering van inhoud aan te kondigen. Wanneer u HTTP/2 gebruikt, zult u een algemene prestatiesverhoging opmerken.

## Wat is HTTP/2? {#what-is-http}

HTTP/2 verbetert de manier waarop browsers en servers communiceren, waardoor informatie sneller kan worden overgedragen en de benodigde hoeveelheid verwerkingskracht wordt verminderd.

De volgende website beschrijft HTTP/2 en de voordelen ervan op een korte en eenvoudige manier:

[https://www.engadget.com/2015/02/24/what-you-need-to-know-about-http-2/](https://www.engadget.com/2015/02/24/what-you-need-to-know-about-http-2/)

## Wat zijn de belangrijkste voordelen van de overgang naar HTTP/2 voor de levering van inhoud? {#what-are-the-key-benefits-of-moving-to-http-for-content-delivery}

De verbetering van prestaties varieert wijd gebaseerd op factoren zoals de code van uw website, hoe u Scene7, het apparaat van de consument, het scherm en de plaats, etc. gebruikt.

De eigen tests van Adobe hebben de volgende resultaten opgeleverd:

* Voor afbeeldingen verbeterde de responstijd 7%-28%, afhankelijk van het apparaat en de browser. De meest opmerkelijke prestatiewinst was op iOS-apparaten.
* Voor viewers verbeterde de laadtijd tot 15%.

De volgende demonstratie illustreert het verschil tussen het laden van HTTP/1 en HTTP/2:

[https://http2.akamai.com/demo](https://http2.akamai.com/demo)

## Mag ik overschakelen op HTTP/2? {#am-i-eligible-to-switch-over-to-http}

Als u HTTP/2 wilt gebruiken, moet u aan de volgende vereisten voldoen:

* Gebruik beveiligde HTTPS voor uw rich media-aanvragen.
* Gebruik de door Adobe gebundelde CDN (content delivery network) als onderdeel van uw Classic-licentie voor Dynamic Media.
* Gebruik een specifiek domein (dat wil zeggen `images.company.com` of `mycompany.scene7.com`), geen algemeen Dynamic Media Klassiek domein (dat wil zeggen, `s7d1.scene7.com`, `s7d2.scene7.com`, of `s7d13.scene7.com`).

   Om uw domeinen te vinden, [login uw geval van Scene7 het Publiceren Systeem](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html) voor elke bedrijfrekening.

   Klik op **[!UICONTROL Setup > Application Setup > General Settings.]** Zoeken naar het veld **Gepubliceerde servernaam**. Als u momenteel een generisch domein Scene7 gebruikt, kunt u verzoeken zich over naar uw eigen douanedomein als deel van deze overgang te bewegen.

## Wat is het proces om HTTP/2 voor mijn Dynamic Media Klassieke rekening toe te laten? {#what-is-the-process-for-enabling-http-for-my-scene-account}

U moet een verzoek van de Technische Steun van Adobe (`s7support@adobe.com`) in werking stellen om op HTTP/2 over te schakelen; het wordt niet automatisch voor u gedaan.

1. Geef de volgende informatie op in uw supportverzoek:

   * Primaire contactpersoon, e-mail en telefoonnummer.
   * Alle domeinen die naar HTTP2 moeten worden overgebracht. Dat is `images.company.com` of `mycompany.scene7.com`.
   Om uw domeinen te vinden, [login uw geval van Scene7 het Publiceren Systeem](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html) voor elke bedrijfrekening.

   Klik op **[!UICONTROL Setup > Application Setup > General Settings.]** Zoeken naar het veld met het label **[!UICONTROL Published Server Name.]**

   * Controleer of u beveiligde HTTPS gebruikt voor aanvragen voor rich media.
   * Controleer of u de CDN gebruikt via Adobe en niet met een directe relatie.
   * Controleer of u een specifiek domein gebruikt. Dat is, `images.company.com` of `mycompany.scene7.com`, geen generisch domein Scene7 zoals, `s7d1.scene7.com`, `s7d2.scene7.com``s7d13.scene7.com`.
   Om uw domeinen te vinden, [login uw geval van Scene7 het Publiceren Systeem](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html) voor elke bedrijfrekening.

   Klik **[!UICONTROL Setup > Application Setup > General Settings.]** Zoek het geëtiketteerde gebied **[!UICONTROL Published Server Name.]** als u momenteel een generisch domein Scene7 gebruikt, kunt u verzoeken zich over naar uw eigen douanedomein als deel van deze overgang te bewegen.

   1. De technische Steun voegt u aan de HTTP/2 klantenwachtlijst toe die op de orde wordt gebaseerd waarin de verzoeken werden voorgelegd.
   1. Wanneer Adobe klaar is om uw verzoek af te handelen, neemt de ondersteuning contact met u op om de overgang te coördineren en een doeldatum in te stellen.
   1. U wordt op de hoogte gesteld nadat de bewerking is voltooid en u kunt controleren of de overgang naar HTTP2 is gelukt.



## Wanneer kan ik verwachten over te gaan naar HTTP/2? {#when-can-i-expect-to-be-transitioned-over-to-http}

Verzoeken worden verwerkt in de volgorde waarin ze door Technische Ondersteuning worden ontvangen.

>[!NOTE]
>
>Er kan een lange aanlooptijd zijn omdat de overgang naar HTTP/2 het wissen van de cache omvat. Daarom kunnen slechts een paar klantenovergangen tegelijkertijd worden behandeld.

## Wat zijn de risico&#39;s bij de overgang naar HTTP/2? {#what-are-the-risks-with-moving-to-http}

De overgang aan HTTP/2 ontruimt uit uw geheime voorgeheugen bij CDN omdat het het bewegen aan een nieuwe configuratie CDN impliceert.

De inhoud die niet in de cache is opgeslagen, raakt rechtstreeks de oorspronkelijke servers van Adobe totdat de cache opnieuw wordt samengesteld. Daarom is Adobe van plan enkele klantovergangen tegelijk af te handelen, zodat acceptabele prestaties behouden blijven wanneer verzoeken van onze oorsprong worden opgehaald.

## Hoe kunt u controleren of een URL of website met HTTP/2 wordt geactiveerd? {#how-can-you-verify-whether-a-url-or-website-is-activated-with-http}

U moet een externsie downloaden om met uw browser van het Web te gebruiken. Voor Firefox en Chrome is er een extensie genaamd **[!UICONTROL HTTP/2 and SPDY Indicator.]** Browsers die alleen HTTP/2 veilig ondersteunen. Het is dus nodig om een URL met HTTPS aan te roepen om dit te verifiëren. Als HTTP/2 wordt ondersteund, wordt dit aangegeven door de extensie in de vorm van een blauw Flash-symbool en een header &quot;X-Firefox-Spdy&quot;: &quot;h2&quot;.
