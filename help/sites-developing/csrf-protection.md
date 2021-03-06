---
title: Het CSRF-beschermingskader
seo-title: Het CSRF-beschermingskader
description: Het framework maakt gebruik van tokens om te garanderen dat het verzoek van de klant legitiem is
seo-description: Het framework maakt gebruik van tokens om te garanderen dat het verzoek van de klant legitiem is
uuid: 7cb222ba-fc7a-46ee-8b49-a5f39a53580b
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
discoiquuid: f453427d-c813-48b7-b2f9-adadea39c67d
translation-type: tm+mt
source-git-commit: c83c77c5c313099944dd73c8cbe63d429d84a518
workflow-type: tm+mt
source-wordcount: '300'
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

Om het even welke component die op `granite.jquery` gebiedsdeel baseert zal automatisch van het Kader van de Bescherming CSRF profiteren. Als dit niet het geval voor om het even welk van uw componenten is, moet u een gebiedsdeel aan `granite.csrf.standalone` verklaren alvorens u het kader kunt gebruiken.

### De crypto-sleutel {#replicating-crypto-keys} repliceren

Om van de tokens gebruik te maken, moet u `/etc/keys/hmac` binair aan alle instanties in uw plaatsing herhalen. Een handige manier om de HMAC-sleutel naar alle instanties te kopiëren, is door een pakket met de sleutel te maken en deze via Package Manager op alle instanties te installeren.

>[!NOTE]
>
>Zorg ervoor u ook de noodzakelijke [veranderingen van de de configuratieveranderingen van de Verzender ](https://helpx.adobe.com/experience-manager/dispatcher/user-guide.html) aanbrengt om het Kader van de Bescherming te gebruiken CSRF.

>[!NOTE]
>
>Als u het duidelijke geheime voorgeheugen met uw Webtoepassing gebruikt, zorg ervoor u &quot;**&amp;ast;**&quot;aan manifest toevoegt om ervoor te zorgen het teken niet de symbolische generatievraag CSRF offline neemt. Raadpleeg deze [link](https://www.w3.org/TR/offline-webapps/) voor meer informatie.
>
>Voor meer informatie over aanvallen CSRF en manieren om hen te verlichten, zie [de pagina van OWASP van het Verzoek van de Vervalsmachine van de Depositovergangen](https://owasp.org/www-community/attacks/csrf).
