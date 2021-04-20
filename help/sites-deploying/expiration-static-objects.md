---
title: Verlopen van statische objecten
seo-title: Verlopen van statische objecten
description: Leer hoe u AEM zodanig configureert dat statische objecten niet verlopen (gedurende een redelijke periode).
seo-description: Leer hoe u AEM zodanig configureert dat statische objecten niet verlopen (gedurende een redelijke periode).
uuid: ee019a3d-4133-4d40-98ec-e0914b751fb3
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
discoiquuid: 73f37b3c-5dbe-4132-bb60-daa8de871884
feature: Configuring
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---


# Verlopen van statische objecten{#expiration-of-static-objects}

Statische objecten (bijvoorbeeld pictogrammen) veranderen niet. Daarom moet het systeem zo worden geconfigureerd dat zij niet (gedurende een redelijke periode) verlopen en zo onnodig verkeer verminderen.

Dit heeft het volgende effect:

* Offloadt aanvragen van de serverinfrastructuur.
* Hiermee verbetert u de prestaties van het laden van pagina&#39;s, aangezien de browser objecten in het cachegeheugen van de browser opslaat.

Verlopen worden gespecificeerd door de norm van HTTP betreffende &quot;vervaldatum&quot;van dossiers (zie, bijvoorbeeld, hoofdstuk 14.21 van [RFC 2616](https://www.ietf.org/rfc/rfc2616.txt) &quot;Hypertext Transfer Protocol — HTTP 1.1&quot;). Deze standaard gebruikt de header om clients toe te staan objecten in cache te plaatsen totdat ze als &#39;stale&#39; worden beschouwd. dergelijke objecten worden gedurende de opgegeven tijd in cache geplaatst zonder dat er een statuscontrole op de oorspronkelijke server wordt uitgevoerd.

>[!NOTE]
>
>Deze configuratie staat volledig los van (en werkt niet voor) de Dispatcher.
>
>Het doel van de Dispatcher is om gegevens vóór AEM in cache te plaatsen.

Alle bestanden, die niet dynamisch zijn en niet in de loop der tijd veranderen, kunnen en moeten in cache worden geplaatst. De configuratie voor de Apache HTTPD-server kan er als volgt uitzien - afhankelijk van de omgeving:

>[!CAUTION]
>
>U moet voorzichtig zijn wanneer u de tijdsperiode definieert waarin een object als up-to-date wordt beschouwd. Aangezien er *geen controle is tot de gespecificeerde tijdspanne is verlopen*, kan de cliënt omhoog het voorstellen van oude inhoud van het geheime voorgeheugen beëindigen.

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

   Hierdoor kunnen in de cache (bijvoorbeeld de browsercache) maximaal één maand CSS-, Javascript-, PNG- en GIF-bestanden worden opgeslagen, totdat ze verlopen. Dit betekent dat ze niet hoeven te worden aangevraagd bij AEM of de webserver, maar wel in de cache van de browser kunnen blijven staan.

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

   Hierdoor kan de cache (bijvoorbeeld de cache van de browser) gedurende maximaal één dag CSS-, Javascript-, PNG- en GIF-bestanden in clientcache opslaan. Hoewel dit voorbeeld algemene instellingen illustreert voor alles onder `/content` en `/etc/designs`, zou u het korter moeten maken.

   Afhankelijk van hoe vaak uw site wordt bijgewerkt, kunt u ook overwegen HTML-pagina&#39;s in cache te plaatsen. Een redelijke termijn zou 1 uur zijn:

   ```xml
   <Location /content>
     ExpiresByType text/html "access plus 1 hour"
   </Location>
   ```

Nadat u de statische voorwerpen hebt gevormd, aftasten `request.log`, terwijl het selecteren van pagina&#39;s die dergelijke voorwerpen houden, om te bevestigen dat geen (onnodige) verzoeken voor statische voorwerpen worden gemaakt.
