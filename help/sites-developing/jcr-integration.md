---
title: JCR-integratie
seo-title: JCR-integratie
description: Tips voor wanneer u op JCR-niveau moet integreren
seo-description: Tips voor wanneer u op JCR-niveau moet integreren
uuid: 11518baf-521e-471d-ad4f-2baa76075cfa
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: e6647a11-a36e-4808-bb61-29b2895c6b1d
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---


# JCR-integratie{#jcr-integration}

## Voorkeur voor de Sling Resource API aan JCR API {#prefer-the-sling-resource-api-to-jcr-api}

De Sling API werkt op een hoger, abstract niveau dan de JCR API. Hierdoor kan uw code herbruikbaar en onafhankelijk van de onderliggende opslag zijn. Hierdoor wordt het gemakkelijker om externe virtuele gegevens indien nodig via het ResourceProvider-mechanisme op te nemen.

## Vermijd query&#39;s waar mogelijk {#avoid-queries-wherever-possible}

Het is altijd sneller om door de gegevensopslagplaats te navigeren om gegevens op te halen dan om een vraag in werking te stellen. Er zijn gevallen waarin de vragen noodzakelijk zullen zijn, zoals een eindgebruikersvraag of het moeten gestructureerde inhoud van over de volledige bewaarplaats vinden, maar voor alle andere gevallen, wordt het verkieslijk om aan de noodzakelijke knopen te navigeren. Vragen moeten altijd worden vermeden in renderlogica, zoals navigatiecomponenten, een &quot;lijst met recente items&quot;, tellingen van items enzovoort. In deze gevallen is het beter om door de hiërarchie te lopen of het resultaat vooraf in cache te plaatsen, zodat het direct kan worden gebruikt wanneer het wordt gerenderd.

## Het bereik van de JCR-waarneming beperken {#restrict-the-scope-of-jcr-observation}

Wanneer het luisteren naar gebeurtenissen in de bewaarplaats, is het belangrijk om het werkingsgebied zo veel mogelijk te beperken. Het is bijvoorbeeld veel beter om te luisteren naar een gebeurtenis op `/etc/mycompany` dan om te luisteren op `/etc`. Luister nooit naar gebeurtenissen in de hoofdmap van de opslagplaats. Bovendien, zorg ervoor dat de callback methodes zo snel mogelijk uitvoeren wanneer er niets voor hen is te doen.

## Elimineer gebruik van JCR admin toegang {#eliminate-use-of-jcr-admin-access}

Vanaf AEM 6, login Administratieve is afgekeurd zoals het krijgen van een administratieve zitting van ResourceResolverFactory. Eerder, zouden de de dienstrekeningen voor de achterkantoorverrichtingen moeten worden gecreeerd die dit type van toegang zouden vereisen en ResourceResolverFactory kan worden gebruikt om een ResourceResolver voor deze rekening te krijgen.
