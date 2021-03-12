---
title: Ondersteuning voor zelfde site-cookie voor AEM 6.5
description: Ondersteuning voor zelfde site-cookie voor AEM 6.5
topic-tags: security
translation-type: tm+mt
source-git-commit: ac2f3d69fd20d7779120a194c698d6f0dd6e6a84
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 1%

---


# Ondersteuning voor zelfde sitecookie voor AEM 6.5 {#same-site-cookie-support-for-aem-65}

Sinds versie 80, introduceerde Chrome, en recentere Safari, een nieuw model voor koekjesveiligheid. Deze wijze wordt ontworpen om veiligheidscontroles rond beschikbaarheid van koekjes aan derdeplaatsen, door het plaatsen te introduceren genoemd `SameSite`. Voor meer gedetailleerde informatie, zie dit [artikel](https://web.dev/samesite-cookies-explained/).

De standaardwaarde van dit plaatsen (`SameSite=Lax`) zou authentificatie tussen AEM instanties of de diensten kunnen veroorzaken om niet te werken. Dit komt doordat de domeinen of URL-structuren van deze services mogelijk niet onder de beperkingen van dit cookiebeleid vallen.

Om rond dit te krijgen, moet u het koekjesattribuut SameSite aan `None` voor het login token plaatsen.

U kunt dit doen door de volgende stappen te volgen:

1. Ga naar de webconsole op `http://serveraddress:serverport/system/console/configMgr`
1. Zoek naar en klik **Adobe granite Token Authentication Handler**
1. Stel het **SameSite-kenmerk voor het cookie** in op `None`, zoals in de onderstaande afbeelding wordt getoond
   ![samesite](assets/samesite1.png)
1. Klik op Opslaan
1. Als deze instelling eenmaal is bijgewerkt en gebruikers opnieuw zijn afgemeld en aangemeld, worden `login-token`-cookies ingesteld als `None`-kenmerk en worden deze opgenomen in intersite verzoeken.
