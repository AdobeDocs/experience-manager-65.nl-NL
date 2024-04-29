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

Vanaf Gemeenschappen [FP1](deploy-communities.md#latestfeaturepack)kunnen leden van de gemeenschap via e-mail communiceren met de gemeenschap via een functie die abonnementen wordt genoemd.

Abonnementen lijken op [meldingen](notifications.md) aangezien leden zich kunnen abonneren bij het volgen van blogartikelen, forumonderwerpen of QnA-vragen.

Abonnementen worden onderscheiden van meldingen:

* Leden kunnen zich niet abonneren wanneer zij andere leden volgen.
* De enige actie die leden kunnen ondernemen, is het selecteren van `Email Subscriptions` wanneer volgende.
* Wanneer e-mailantwoord is geconfigureerd, kunnen leden inhoud effectief posten door eenvoudig te antwoorden op de ontvangen e-mail.

### Vereisten {#requirements}

**E-mail configureren**

E-mail moet worden gevormd om abonnementen te functioneren en voor leden te antwoorden per e-mail.

Voor instructies over het instellen van e-mailberichten raadpleegt u [E-mail configureren](email.md).

**Abonnementen inschakelen en volgen**

Componenten moeten worden geconfigureerd om abonnementen in te schakelen *en* volgende. Functies die abonnementen toestaan, zijn [blog](blog-feature.md), [forum](forum.md) en [QnA](working-with-qna.md).

## Abonnementen van volgende {#subscriptions-from-following}

![abonnement-volgende](assets/subscription-following.png)

De **Volgen** biedt een manier om vermeldingen als activiteiten, abonnementen en/of meldingen te volgen. Elke keer als **Volgen** is geselecteerd, is het mogelijk om een selectie in of uit te schakelen.

Als een van de volgende methoden is geselecteerd, verandert de tekst van de knop in **volgende**. Voor het gemak is het mogelijk `Unfollow All` om alle methoden uit te schakelen.

De **Volgen** bevat de knop `Email Subscriptions` optie slechts wanneer een forum, QnA, of blog wordt gevormd om e-mailabonnementen toe te laten. Deze knop wordt weergegeven:

* Op de hoofdpagina met functies voor het ingeschakelde forum, stuurt QnA of blog een e-mail voor alle activiteiten onder die functie.

* Voor een specifiek bericht, zoals een forumonderwerp, een QnA-vraag of een blogartikel Er wordt een e-mail verzonden wanneer er activiteit is voor dat specifieke bericht.

## Reageren per e-mail {#reply-by-email}

Wanneer e-mail [geconfigureerd voor beantwoorden per e-mail](email.md#configure-polling-importer), ontvangt het lid dat zich heeft geabonneerd een e-mail met de geposte inhoud en een koppeling naar de online-inhoud.

Als ze op het e-mailbericht reageren, wordt de inhoud die ze in het antwoord invoeren, online weergegeven als inhoud.

![e-mailantwoord](assets/email-reply.png)

De tijd die nodig is om een antwoord te plaatsen, wordt bepaald door de [update-interval opiniepeilingimportmodule](email.md#configure-polling-importer).

![QA](assets/qa.png)
