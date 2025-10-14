---
title: Communityabonnementen
description: Communautaire leden communiceren via e-mail met andere leden
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
role: Admin
exl-id: 338be220-659a-459c-8e90-55e3a11ddeb0
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---

# Communityabonnementen {#communities-subscriptions}

## Overzicht {#overview}

Vanaf de Gemeenschappen [&#x200B; FP1 &#x200B;](deploy-communities.md#latestfeaturepack), kunnen de communautaire leden met de gemeenschap door e-mail interactie aangaan gebruikend een eigenschap die als abonnementen wordt bedoeld.

De abonnementen zijn gelijkaardig aan [&#x200B; berichten &#x200B;](notifications.md) aangezien de leden kunnen intekenen wanneer het volgende blogartikelen, forumonderwerpen of vragen QnA.

Abonnementen worden onderscheiden van meldingen:

* Leden kunnen zich niet abonneren wanneer zij andere leden volgen.
* De enige actie die leden kunnen ondernemen, is het selecteren van `Email Subscriptions` wanneer ze volgen.
* Wanneer e-mailantwoord is geconfigureerd, kunnen leden inhoud effectief posten door eenvoudig te antwoorden op de ontvangen e-mail.

### Vereisten {#requirements}

**vorm E-mail**

E-mail moet worden gevormd om abonnementen te functioneren en voor leden te antwoorden per e-mail.

Voor instructies bij vestiging e-mail, zie [&#x200B; het Vormen E-mail &#x200B;](email.md).

**laat Abonnementen toe en volgt**

De componenten moeten worden gevormd om abonnementen *en* volgend toe te laten. De eigenschappen die abonnementen toestaan zijn [&#x200B; blog &#x200B;](blog-feature.md), [&#x200B; forum &#x200B;](forum.md) en [&#x200B; QnA &#x200B;](working-with-qna.md).

## Abonnementen van volgende {#subscriptions-from-following}

![&#x200B; abonnement-volgend &#x200B;](assets/subscription-following.png)

**volgt** knoop verstrekt een middel om ingangen als activiteiten, abonnementen en/of berichten te volgen. Telkens als **volgt** knoop wordt geselecteerd, is het mogelijk om op of van een selectie van een knevel te voorzien.

Als om het even welke methode van het volgende wordt geselecteerd, verandert de tekst van de knoop in **volgend**. Voor het gemak is het mogelijk om `Unfollow All` te selecteren om alle methoden uit te schakelen.

**volgt** knoop zal de `Email Subscriptions` optie omvatten slechts wanneer een forum, QnA, of blog wordt gevormd om e-mailabonnementen toe te laten. Deze knop wordt weergegeven:

* Op de hoofdpagina met functies voor het ingeschakelde forum, stuurt QnA of blog een e-mail voor alle activiteiten onder die functie.

* Voor een specifiek bericht, zoals een forumonderwerp, een QnA-vraag of een blogartikel Er wordt een e-mail verzonden wanneer er activiteit is voor dat specifieke bericht.

## Reageren per e-mail {#reply-by-email}

Wanneer e-mail [&#x200B; voor het antwoorden door e-mail &#x200B;](email.md#configure-polling-importer) wordt gevormd, zal het lid dat zich abonneert een e-mail met de geposte inhoud en een verbinding aan de online inhoud ontvangen.

Als ze op het e-mailbericht reageren, wordt de inhoud die ze in het antwoord invoeren, online weergegeven als inhoud.

![&#x200B; e-mail-antwoord &#x200B;](assets/email-reply.png)

De hoeveelheid tijd het voor een te posten antwoord neemt wordt gecontroleerd door het [&#x200B; pollende de updateinterval van de importeur &#x200B;](email.md#configure-polling-importer).

![&#x200B; QA &#x200B;](assets/qa.png)
