---
title: HTTP2 Veelgestelde vragen over inhoud
description: Meer informatie over de levering van HTTP2-inhoud en over de manier waarop dit de algemene prestaties van uw webinhoud kan verbeteren.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
exl-id: 2428914c-5fb0-439e-a1ef-8ee30b890f58
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '747'
ht-degree: 0%

---

# HTTP2 Veelgestelde vragen over inhoud{#http-delivery-of-content-faq}

De Adobe is opgetogen om de beschikbaarheid van HTTP/2 levering van inhoud aan te kondigen. Wanneer u HTTP/2 gebruikt, wordt een algemene prestatiesverhoging opgemerkt.

## Wat is HTTP/2? {#what-is-http}

HTTP/2 verbetert de manier waarop browsers en servers communiceren, waardoor informatie sneller kan worden overgedragen en de benodigde hoeveelheid verwerkingskracht wordt verminderd.

De volgende website beschrijft HTTP/2 en de voordelen ervan op een korte en eenvoudige manier:

[Wat u moet weten over HTTP/2](https://www.engadget.com/2015-02-24-what-you-need-to-know-about-http-2.html).

## Wat zijn de belangrijkste voordelen van de overgang naar HTTP/2 voor de levering van inhoud? {#what-are-the-key-benefits-of-moving-to-http-for-content-delivery}

Prestatieverbetering varieert sterk op basis van factoren zoals de code van uw website, hoe u Dynamic Media gebruikt, het apparaat, het scherm en de locatie van de klant.

De eigen tests van de Adobe leverden de volgende resultaten op:

* Voor afbeeldingen verbeterde de responstijd 7%-28%, afhankelijk van apparaat en browser. De meest opmerkelijke prestatiewinst was op iOS-apparaten.
* Voor viewers zijn de prestaties tijdens de laadtijd met 15% verbeterd.

De volgende demonstratie illustreert het verschil tussen het laden van HTTP/1 en HTTP/2:

[https://http2.akamai.com/demo](https://http2.akamai.com/demo)

## Mag ik overschakelen op HTTP/2? {#am-i-eligible-to-switch-over-to-http}

Als u HTTP/2 wilt gebruiken, moet u aan de volgende vereisten voldoen:

* Gebruik beveiligde HTTPS voor uw rich media-aanvragen.
* Gebruik de Adobe-gebundelde CDN (content delivery network) als deel van uw Dynamic Media-licentie.
* Gebruik een speciaal domein (dat wil zeggen `images.company.com` of `mycompany.scene7.com`), niet een algemeen Dynamic Media-domein (dat wil zeggen: `s7d1.scene7.com`, `s7d2.scene7.com`, of `s7d13.scene7.com`).

  Om uw domeinen te vinden, open [Dynamic Media Classic-bureaubladtoepassing](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)en meld u vervolgens aan bij uw bedrijfsaccount of -accounts. Blader vervolgens naar **[!UICONTROL Setup]** > **[!UICONTROL Application Setup]** > **[!UICONTROL General Settings]**. Zoeken naar het veld met het label **Gepubliceerde servernaam**. Als u momenteel een algemeen Dynamic Media-domein gebruikt, kunt u vragen dat u in het kader van deze overgang overschakelt naar uw eigen aangepaste domein.

## Wat is het proces voor het inschakelen van HTTP/2 voor mijn Dynamic Media-account? {#what-is-the-process-for-enabling-http-for-my-scene-account}

1. [Gebruik de Admin Console om een steungeval te creëren](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html) en verzoek om over te schakelen naar HTTP/2; dit wordt niet automatisch voor u gedaan.
1. Geef de volgende informatie op in uw ondersteuningsgeval:

   * Primaire contactpersoon, e-mail en telefoonnummer.
   * Alle domeinen die naar HTTP2 moeten worden overgebracht. Dat wil zeggen: `images.company.com` of `mycompany.scene7.com`.

     Om uw domeinen te vinden, open [Dynamic Media Classic-bureaubladtoepassing](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)en meld u vervolgens aan bij uw bedrijfsaccount of -accounts. Blader vervolgens naar **[!UICONTROL Setup]** > **[!UICONTROL Application Setup]** > **[!UICONTROL General Settings]**. Zoeken naar het veld met het label **[!UICONTROL Published Server Name]**.

   * Controleer of u beveiligde HTTPS gebruikt voor aanvragen voor rich media.
   * Verifieer u CDN door Adobe gebruikt en niet beheerd met een directe verhouding.
   * Controleer of u een specifiek domein gebruikt. Dat wil zeggen: `images.company.com` of `mycompany.scene7.com`, niet een algemeen Dynamic Media-domein zoals `s7d1.scene7.com`, `s7d2.scene7.com`, `s7d13.scene7.com`.

     Om uw domeinen te vinden, open [Dynamic Media Classic-bureaubladtoepassing](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)en meld u vervolgens aan bij uw bedrijfsaccount of -accounts. Blader vervolgens naar **[!UICONTROL Setup]** > **[!UICONTROL Application Setup]** > **[!UICONTROL General Settings]**. Zoeken naar het veld met het label **[!UICONTROL Published Server Name]**. Als u momenteel een algemeen Dynamic Media-domein gebruikt, kunt u vragen dat u in het kader van deze overgang overschakelt naar uw eigen aangepaste domein.

1. De Steun van de Klant van de Adobe voegt u aan de HTTP/2 klantenwachtlijst toe die op de orde wordt gebaseerd waarin de verzoeken werden voorgelegd.
1. Wanneer de Adobe bereid is om uw verzoek te behandelen, contacteert de Steun u om de overgang te coördineren en een doeldatum te plaatsen.
1. U wordt op de hoogte gesteld nadat de bewerking is voltooid en u kunt controleren of de overgang naar HTTP2 is gelukt.

## Wanneer kan ik een overgang naar HTTP/2 verwachten? {#when-can-i-expect-to-be-transitioned-over-to-http}

Verzoeken worden verwerkt in de volgorde waarin ze door de Adobe Klantenondersteuning worden ontvangen.

>[!NOTE]
>
>Er is een lange aanlooptijd omdat de overgang naar HTTP/2 het wissen van de cache omvat. Daarom kunnen slechts een paar klantenovergangen tegelijkertijd worden behandeld.

## Wat zijn de risico&#39;s bij de overgang naar HTTP/2? {#what-are-the-risks-with-moving-to-http}

De overgang aan HTTP/2 ontruimt uit uw geheime voorgeheugen bij CDN omdat het het bewegen aan een nieuwe configuratie CDN impliceert.

De inhoud die niet in de cache is opgeslagen, raakt de oorspronkelijke servers van de Adobe rechtstreeks aan totdat de cache opnieuw wordt samengesteld. Wegens deze actie, is de Adobe van plan om een paar klantenovergangen in een tijd te behandelen zodat de aanvaardbare prestaties worden gehandhaafd wanneer het trekken van verzoeken van de oorsprong van de Adobe.

## Hoe kunt u controleren of een URL of website met HTTP/2 wordt geactiveerd? {#how-can-you-verify-whether-a-url-or-website-is-activated-with-http}

Download een extensie die u met uw webbrowser kunt gebruiken. Voor Firefox en Chrome is er een extensie genaamd **[!UICONTROL HTTP/2 and SPDY Indicator]**. Browsers ondersteunen alleen veilig HTTP/2, dus het is nodig een URL met HTTPS aan te roepen om te verifiëren. Als HTTP/2 wordt ondersteund, wordt dit aangegeven door de extensie in de vorm van een blauw symbool voor Flash en de header &quot;X-Firefox-Spdy&quot;: &quot;h2&quot;.
