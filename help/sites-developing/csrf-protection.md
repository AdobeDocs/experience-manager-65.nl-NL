---
title: Het CSRF-beschermingskader
description: Het framework maakt gebruik van tokens om te garanderen dat het verzoek van de klant legitiem is
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
exl-id: e6b0f8f7-54b0-4dd6-86ad-5516954c6d90
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# Het CSRF-beschermingskader{#the-csrf-protection-framework}

Naast het filter Apache Sling Referrer biedt Adobe ook een nieuw CSRF-beschermingskader dat bescherming biedt tegen dit type aanvallen.

Het framework maakt gebruik van tokens om te garanderen dat het verzoek van de klant legitiem is. De tokens worden gegenereerd wanneer het formulier naar de client wordt verzonden en gevalideerd wanneer het formulier naar de server wordt teruggestuurd.

>[!NOTE]
>
>De publicatie-instanties bevatten geen tokens voor anonieme gebruikers.

## Vereisten {#requirements}

### Afhankelijkheden {#dependencies}

Elke component die afhankelijk is van de component `granite.jquery` afhankelijkheid kan automatisch profiteren van het CSRF-beschermingskader. Als niet, voor om het even welk van uw componenten, moet u een gebiedsdeel verklaren aan `granite.csrf.standalone` voordat u het framework kunt gebruiken.

### De crypto-sleutel repliceren {#replicating-crypto-keys}

Om de tokens te gebruiken, moet u het binaire getal HMAC aan alle instanties in uw plaatsing herhalen. Zie [Replicatie van de HMAC-sleutel](/help/sites-administering/encapsulated-token.md#replicating-the-hmac-key) voor meer informatie .

>[!NOTE]
>
>Zorg ervoor dat u ook de vereiste [Wijzigingen in de configuratie van Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/user-guide.html) het CSRF-beschermingskader te gebruiken.

>[!NOTE]
>
>Als u het manifestgeheime voorgeheugen met uw Webtoepassing gebruikt, zorg ervoor u &quot;**&amp;asteren;**&quot; aan manifest om ervoor te zorgen neemt het teken niet de CSRF symbolische generatievraag offline. Raadpleeg deze voor meer informatie [link](https://www.w3.org/TR/offline-webapps/).
>
Voor meer informatie over aanvallen CSRF en manieren om hen te verlichten, zie [OWASP-pagina voor XSS-aanvragen voor andere sites](https://owasp.org/www-community/attacks/csrf).
