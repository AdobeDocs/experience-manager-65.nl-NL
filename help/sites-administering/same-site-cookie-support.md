---
title: Ondersteuning voor zelfde site-cookie voor AEM 6.5
description: Meer informatie over de ondersteuning voor Zelfde sitecookie voor AEM 6.5.
topic-tags: security
exl-id: e1616385-0855-4f70-b787-b01701929bbc
solution: Experience Manager, Experience Manager Sites
feature: Security
role: Admin
source-git-commit: db7830895c8a2d1b7228dc4780296d43f15776df
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# Ondersteuning voor zelfde site-cookie voor AEM 6.5 {#same-site-cookie-support-for-aem-65}

Sinds versie 80, Chrome, en later Safari, introduceerde een nieuw model voor koekjesveiligheid. Deze modus is ontworpen om beveiligingsinstellingen te introduceren voor de beschikbaarheid van cookies op sites van derden, via een instelling die `SameSite` wordt genoemd. Voor meer gedetailleerde informatie, zie dit [&#x200B; web.dev - Cookies SameSite verklaarde &#x200B;](https://web.dev/samesite-cookies-explained/) artikel.

De standaardwaarde van dit plaatsen (`SameSite=Lax`) zou authentificatie tussen AEM instanties of de diensten kunnen veroorzaken om niet te werken. Dit komt doordat de domeinen of URL-structuren van deze services mogelijk niet onder de beperkingen van dit cookiebeleid vallen.

U kunt dit omzeilen door het attribuut `SameSite` cookie voor het aanmeldingstoken in te stellen op `None` .

>[!CAUTION]
>
>De instelling `SameSite=None` wordt alleen toegepast als het protocol beveiligd is (HTTPS).
>
>Als het protocol niet veilig (HTTP) is, dan wordt het plaatsen genegeerd en de server zal dit WARN bericht tonen:
>
>`WARN com.day.crx.security.token.TokenCookie Skip 'SameSite=None'`

U kunt de instelling toevoegen door de volgende stappen uit te voeren:

1. Ga naar de webconsole op `http://serveraddress:serverport/system/console/configMgr`
1. Onderzoek naar en klik de **Adobe granite Symbolische Handler van de Authentificatie**
1. Plaats het **SameSite attribuut voor het login-symbolische koekje** aan `None`, zoals aangetoond in het hieronder beeld
   ![&#x200B; gelijk &#x200B;](assets/samesite1.png)
1. Klik op Opslaan
1. Zodra deze instelling is bijgewerkt en gebruikers zijn afgemeld en opnieuw zijn aangemeld, wordt voor `login-token` -cookies het kenmerk `None` ingesteld en worden deze opgenomen in intersite aanvragen.
