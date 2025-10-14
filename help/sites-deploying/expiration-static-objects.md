---
title: Verlopen van statische objecten
description: Leer hoe u Adobe Experience Manager zo configureert dat statische objecten niet verlopen (gedurende een redelijke periode).
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
feature: Configuring
exl-id: bfd5441c-19cc-4fa8-b597-b1221465f75d
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# Verlopen van statische objecten{#expiration-of-static-objects}

Statische objecten (bijvoorbeeld pictogrammen) veranderen niet. Daarom moet het systeem zo worden geconfigureerd dat zij niet verlopen (voor een redelijke periode) en zo onnodig verkeer verminderen.

Dit heeft het volgende effect:

* Offloadt aanvragen van de serverinfrastructuur.
* Hiermee verbetert u de prestaties van het laden van pagina&#39;s, aangezien de browser objecten in het cachegeheugen van de browser opslaat.

De vervalsingen worden gespecificeerd door de norm van HTTP betreffende &quot;vervaldatum&quot;van dossiers (bijvoorbeeld, zie hoofdstuk 14.21 van [&#x200B; RFC 2616 &#x200B;](https://www.ietf.org/rfc/rfc2616.txt) &quot;Protocol van de Overdracht van de Hypertext — HTTP 1.1&quot;). Deze standaard gebruikt de header om clients toe te staan objecten in cache te plaatsen totdat ze als &#39;stale&#39; worden beschouwd; dergelijke objecten worden gedurende de opgegeven tijd in cache geplaatst zonder dat er een statuscontrole naar de oorspronkelijke server wordt uitgevoerd.

>[!NOTE]
>
>Deze configuratie staat los van (en werkt niet voor) de Dispatcher.
>
>Het doel van de Dispatcher is om gegevens voor Adobe Experience Manager (AEM) in cache op te slaan.

Alle bestanden, die niet dynamisch zijn en niet in de loop der tijd veranderen, kunnen en moeten in cache worden geplaatst. De configuratie voor de Apache HTTPD-server kan er als volgt uitzien - afhankelijk van de omgeving:

>[!CAUTION]
>
>Wees voorzichtig wanneer u de tijdsperiode definieert waarin een object als up-to-date wordt beschouwd. Aangezien er *geen controle is tot de gespecificeerde tijdspanne* is verlopen, kan de cliënt omhoog het voorstellen van oude inhoud van het geheime voorgeheugen beëindigen.

1. **voor een instantie van de Auteur:**

   ```xml
   LoadModule expires_module modules/mod_expires.so
   <Location /libs>
     ExpiresByType text/css "access plus 1 month"
     ExpiresByType text/javascript "access plus 1 month"
     ExpiresByType image/png "access plus 1 month"
     ExpiresByType image/gif "access plus 1 month"
   </Location>
   ```

   Hierdoor kunnen in de cache (bijvoorbeeld de browsercache) maximaal een maand CSS-, JavaScript-, PNG- en GIF-bestanden worden opgeslagen, totdat ze verlopen. Dit betekent dat ze niet hoeven te worden aangevraagd bij AEM of de webserver, maar wel in de cache van de browser kunnen blijven staan.

   Andere gedeelten van de site moeten niet in de cache worden geplaatst op een instantie van de auteur, omdat deze op elk moment kunnen worden gewijzigd.

1. **voor een instantie van Publish:**

   ```xml
   LoadModule expires_module modules/mod_expires.so
   <Location /content>
     ExpiresByType text/css "access plus 1 day"
     ExpiresByType text/javascript "access plus 1 day"
     ExpiresByType image/png "access plus 1 day"
     ExpiresByType image/gif "access plus 1 day"
   </Location>
   <Location /etc/designs>
     ExpiresByType text/css "access plus 1 day"
     ExpiresByType text/javascript "access plus 1 day"
     ExpiresByType image/png "access plus 1 day"
     ExpiresByType image/gif "access plus 1 day"
   </Location>
   ```

   Hierdoor kan de cache van een tussenliggende gebruiker (bijvoorbeeld de browsercache) maximaal één dag CSS-, JavaScript-, PNG- en GIF-bestanden opslaan in clientcache. Hoewel dit voorbeeld algemene instellingen illustreert voor alles onder `/content` en `/etc/designs` , moet u deze korter maken.

   Afhankelijk van hoe vaak uw site wordt bijgewerkt, kunt u ook overwegen HTML-pagina&#39;s in cache te plaatsen. Een redelijke termijn is één uur:

   ```xml
   <Location /content>
     ExpiresByType text/html "access plus 1 hour"
   </Location>
   ```

Nadat u de statische objecten hebt geconfigureerd, scant u `request.log` terwijl u pagina&#39;s selecteert die dergelijke objecten bevatten, om te bevestigen dat er geen (overbodige) aanvragen worden gedaan voor statische objecten.
