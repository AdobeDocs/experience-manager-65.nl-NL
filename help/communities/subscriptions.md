---
title: Communityabonnementen
seo-title: Communityabonnementen
description: Communautaire leden communiceren via e-mail met andere leden
seo-description: Communautaire leden communiceren via e-mail met andere leden
uuid: a4b98769-c219-4e18-8e80-9a806ab979ff
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 33c85af4-4c56-487a-ba60-55211cb9f72c
translation-type: tm+mt
source-git-commit: 2fcd87cd1def7fc265ba40c83b50db86618f3b70
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---


# Communityabonnementen {#communities-subscriptions}

## Overzicht {#overview}

Vanaf Community [FP1](deploy-communities.md#latestfeaturepack) kunnen leden van de gemeenschap via e-mail communiceren met de community via een functie die wordt aangeduid als abonnementen.

Abonnementen zijn vergelijkbaar met [meldingen](notifications.md) omdat leden zich kunnen abonneren bij het volgen van blogartikelen, forumonderwerpen of QnA-vragen.

Abonnementen worden onderscheiden van meldingen:

* Leden kunnen zich niet abonneren wanneer zij andere leden volgen.
* De enige actie die leden kunnen ondernemen, is om `Email Subscriptions` te selecteren wanneer volgende.
* Wanneer e-mailantwoord is geconfigureerd, kunnen leden inhoud effectief posten door eenvoudig te antwoorden op de ontvangen e-mail.

### Vereisten {#requirements}

**E-mail configureren**

E-mail moet worden gevormd om abonnementen te functioneren en voor leden te antwoorden per e-mail.

Zie [E-mail configureren](email.md) voor instructies voor het instellen van e-mail.

**Abonnementen inschakelen en volgen**

Componenten moeten worden geconfigureerd om de volgende abonnementen *en* in te schakelen. Functies die abonnementen toestaan, zijn [blog](blog-feature.md), [forum](forum.md) en [QnA](working-with-qna.md).

## Abonnementen van volgende {#subscriptions-from-following}

![abonnement-volgende](assets/subscription-following.png)

Met de knop **Follow** kunt u items opvolgen als activiteiten, abonnementen en/of meldingen. Telkens wanneer de **Follow** knoop wordt geselecteerd, is het mogelijk om of van een selectie van een knevel te voorzien.

Als een methode van het volgende wordt geselecteerd, verandert de tekst van de knoop in **volgend**. Voor het gemak, is het mogelijk om `Unfollow All` te selecteren om alle methodes van een knevel te voorzien.

De **Follow** knoop zal `Email Subscriptions` optie slechts omvatten wanneer een forum, QnA, of blog wordt gevormd om e-mailabonnementen toe te laten. Deze knop wordt weergegeven:

* Op de hoofdpagina met functies voor het ingeschakelde forum, stuurt QnA of blog een e-mail voor alle activiteiten onder die functie.

* Voor een specifiek bericht, zoals een forumonderwerp, een QnA-vraag of een blogartikel Er wordt een e-mail verzonden wanneer er activiteit is voor dat specifieke bericht.

## Reageren via e-mail {#reply-by-email}

Als e-mail [geconfigureerd is voor het beantwoorden via e-mail](email.md#configure-polling-importer), ontvangt het lid dat zich heeft geabonneerd een e-mail met de geposte inhoud en een koppeling naar de online-inhoud.

Als ze op het e-mailbericht reageren, wordt de inhoud die ze in het antwoord invoeren, online weergegeven als inhoud.

![e-mailantwoord](assets/email-reply.png)

De hoeveelheid tijd die nodig is om een antwoord te verzenden, wordt bepaald door het update-interval van de [opiniepeilingimporteur](email.md#configure-polling-importer).

![QA](assets/qa.png)

