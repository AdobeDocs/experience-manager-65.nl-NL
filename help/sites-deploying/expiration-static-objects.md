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
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# Verlopen van statische objecten{#expiration-of-static-objects}

Statische objecten (bijvoorbeeld pictogrammen) veranderen niet. Daarom moet het systeem zo worden geconfigureerd dat zij niet verlopen (voor een redelijke periode) en zo onnodig verkeer verminderen.

Dit heeft het volgende effect:

* Offloadt aanvragen van de serverinfrastructuur.
* Hiermee verbetert u de prestaties van het laden van pagina&#39;s, aangezien de browser objecten in het cachegeheugen van de browser opslaat.

De vervaldatums worden gespecificeerd door de norm van HTTP betreffende &quot;vervaldatum&quot;van dossiers (bijvoorbeeld, zie hoofdstuk 14.21 van [RFC 2616](https://www.ietf.org/rfc/rfc2616.txt) &quot; Hypertext Transfer Protocol — HTTP 1.1&quot;). Deze standaard gebruikt de header om clients toe te staan objecten in cache te plaatsen totdat ze als &#39;stale&#39; worden beschouwd; dergelijke objecten worden gedurende de opgegeven tijd in cache geplaatst zonder dat er een statuscontrole naar de oorspronkelijke server wordt uitgevoerd.

>[!NOTE]
>
>Deze configuratie staat los van (en werkt niet voor) de Dispatcher.
>
>Het doel van de Dispatcher is om gegevens voor Adobe Experience Manager (AEM) in het cachegeheugen op te slaan.

Alle bestanden, die niet dynamisch zijn en niet in de loop der tijd veranderen, kunnen en moeten in cache worden geplaatst. De configuratie voor de Apache HTTPD-server kan er als volgt uitzien - afhankelijk van de omgeving:

>[!CAUTION]
>
>Wees voorzichtig wanneer u de tijdsperiode definieert waarin een object als up-to-date wordt beschouwd. Als er *geen controle tot de opgegeven periode is verstreken* kan de client de oude inhoud uit de cache presenteren.

1. **Voor een instantie Auteur:**

   ```xml
   LoadModule expires_module modules/mod_expires.so
   <Location /libs>
     ExpiresByType text/css "access plus 1 month"
     ExpiresByType text/javascript "access plus 1 month"
     ExpiresByType image/png "access plus 1 month"
     ExpiresByType image/gif "access plus 1 month"
   </Location>
   ```

   Hierdoor kan de cache van een tussenliggend item (bijvoorbeeld de browsercache) maximaal een maand CSS-, JavaScript-, PNG- en GIF-bestanden opslaan, totdat ze verlopen. Dit betekent dat ze niet hoeven te worden aangevraagd bij AEM of de webserver, maar wel in de cache van de browser kunnen blijven staan.

   Andere gedeelten van de site moeten niet in de cache worden geplaatst op een instantie van de auteur, omdat deze op elk moment kunnen worden gewijzigd.

1. **Voor een instantie Publish:**

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

   Hierdoor kan de tussenliggende cache (bijvoorbeeld de browsercache) maximaal één dag CSS-, JavaScript-, PNG- en GIF-bestanden opslaan in clientcaches. Hoewel dit voorbeeld algemene instellingen voor alles hieronder illustreert `/content` en `/etc/designs`, moet u het korter maken.

   Afhankelijk van hoe vaak uw site wordt bijgewerkt, kunt u ook overwegen HTML-pagina&#39;s in cache te plaatsen. Een redelijke termijn is één uur:

   ```xml
   <Location /content>
     ExpiresByType text/html "access plus 1 hour"
   </Location>
   ```

Nadat u de statische objecten hebt geconfigureerd, scant u `request.log`Selecteer pagina&#39;s die dergelijke objecten bevatten, om te bevestigen dat er geen (overbodige) aanvragen worden gedaan voor statische objecten.
