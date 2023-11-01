---
title: Het CSRF-beschermingskader
seo-title: The CSRF Protection Framework
description: Het framework maakt gebruik van tokens om te garanderen dat het verzoek van de klant legitiem is
seo-description: The framework makes use of tokens to guarantee that the client request is legitimate
uuid: 7cb222ba-fc7a-46ee-8b49-a5f39a53580b
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
discoiquuid: f453427d-c813-48b7-b2f9-adadea39c67d
exl-id: e6b0f8f7-54b0-4dd6-86ad-5516954c6d90
source-git-commit: 1807919078996b1cf1cbd1f2d90c3b14cb660e2c
workflow-type: tm+mt
source-wordcount: '254'
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

Elke component die afhankelijk is van de component `granite.jquery` de afhankelijkheid zal automatisch profiteren van het CSRF-beschermingskader. Als dit niet het geval voor om het even welk van uw componenten is, moet u een gebiedsdeel verklaren aan `granite.csrf.standalone` voordat u het framework kunt gebruiken.

### De crypto-sleutel repliceren {#replicating-crypto-keys}

Om gebruik van de tokens te maken, moet u het binaire getal HMAC aan alle instanties in uw plaatsing herhalen. Zie [Replicatie van de HMAC-sleutel](/help/sites-administering/encapsulated-token.md#replicating-the-hmac-key) voor meer informatie .

>[!NOTE]
>
>Zorg ervoor dat u ook de vereiste [Wijzigingen in de configuratie van Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/user-guide.html) het CSRF-beschermingskader te gebruiken.

>[!NOTE]
>
>Als u het manifestgeheime voorgeheugen met uw Webtoepassing gebruikt, zorg ervoor u &quot;**&amp;asteren;**&quot; aan manifest om ervoor te zorgen neemt het teken niet de CSRF symbolische generatievraag offline. Raadpleeg deze voor meer informatie [link](https://www.w3.org/TR/offline-webapps/).
>
>Voor meer informatie over aanvallen CSRF en manieren om hen te verlichten, zie [OWASP-pagina voor XSS-aanvragen voor andere sites](https://owasp.org/www-community/attacks/csrf).
