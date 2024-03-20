---
title: Ondersteuning voor zelfde site-cookie voor AEM 6.5
description: Meer informatie over de ondersteuning voor Zelfde sitecookie voor AEM 6.5.
topic-tags: security
exl-id: e1616385-0855-4f70-b787-b01701929bbc
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# Ondersteuning voor zelfde site-cookie voor AEM 6.5 {#same-site-cookie-support-for-aem-65}

Sinds versie 80, introduceerde Chrome, en recentere Safari, een nieuw model voor koekjesveiligheid. Deze wijze wordt ontworpen om veiligheidscontroles rond beschikbaarheid van koekjes aan derdeplaatsen, door het plaatsen te introduceren genoemd `SameSite`. Zie deze voor meer informatie [artikel](https://web.dev/samesite-cookies-explained/).

De standaardwaarde van deze instelling (`SameSite=Lax`) kan ervoor zorgen dat verificatie tussen AEM instanties of services niet werkt. Dit komt doordat de domeinen of URL-structuren van deze services mogelijk niet onder de beperkingen van dit cookiebeleid vallen.

Als u dit wilt omzeilen, moet u de opdracht `SameSite` cookie, kenmerk naar `None` voor het aanmeldingstoken.

>[!CAUTION]
>
>De `SameSite=None` instelling wordt alleen toegepast als het protocol beveiligd is (HTTPS).
>
>Als het protocol niet veilig (HTTP) is, dan wordt het plaatsen genegeerd en de server zal dit WARN bericht tonen:
>
>`WARN com.day.crx.security.token.TokenCookie Skip 'SameSite=None'`

U kunt de instelling toevoegen door de volgende stappen uit te voeren:

1. Ga naar de webconsole op `http://serveraddress:serverport/system/console/configMgr`
1. Zoeken naar en klikken op de knop **Adobe Granite Token Authentication Handler**
1. Stel de **Het attribuut SameSite voor het cookie met het token login** tot `None`, zoals wordt weergegeven in de onderstaande afbeelding
   ![samesite](assets/samesite1.png)
1. Klik op Opslaan
1. Zodra dit het plaatsen wordt bijgewerkt en de gebruikers het programma worden geopend en opnieuw het programma geopend, `login-token` cookies hebben de `None` kenmerk ingesteld en wordt opgenomen in aanvragen voor andere sites.
