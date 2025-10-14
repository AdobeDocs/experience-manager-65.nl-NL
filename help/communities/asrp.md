---
title: ASRP - Adobe Storage Resource Provider
description: AEM Communities instellen om een relationele database te gebruiken als de algemene opslag
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
docset: aem65
role: Admin
exl-id: 6430ed96-5d96-41b6-866f-90b34ff84f7a
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '780'
ht-degree: 0%

---

# ASRP - Adobe Storage Resource Provider {#asrp-adobe-storage-resource-provider}

## Info over ASRP {#about-asrp}

Wanneer AEM Communities wordt gevormd om ASRP als zijn gemeenschappelijke opslag te gebruiken, is de gebruiker geproduceerde inhoud (UGC) toegankelijk van alle auteur en publiceer instanties zonder de behoefte aan synchronisatie of replicatie.

Zie ook [&#x200B; Kenmerken van Opties SRP &#x200B;](/help/communities/working-with-srp.md#characteristics-of-srp-options) en [&#x200B; Aanbevolen Topologieën &#x200B;](/help/communities/topologies.md).

## Vereisten {#requirements}

Een extra vergunning wordt vereist voor het gebruik van ASRP.

Als u uw AEM Communities-site wilt configureren voor gebruik van ASRP voor UGC, neemt u contact op met uw accountvertegenwoordiger voor:

* Het Centrum URL van gegevens (adres van het eindpunt van ASRP)
* Consumentencode
* Geheime sleutel
* ID(&#39;s) van rapportsuite

De consument en geheime sleutels worden gedeeld over alle rapportseries voor een bedrijf. Er is één rapportsuite per huurder.

## Configuratie {#configuration}

### Selecteer ASRP {#select-asrp}

De [&#x200B; console van de Configuratie van de Opslag &#x200B;](/help/communities/srp-config.md) staat voor de selectie van de standaardopslagconfiguratie toe, die identificeert welke implementatie van SRP aan gebruik.

**op AEM instantie van de Auteur:**

* Navigeer vanuit de globale navigatie naar **[!UICONTROL Tools > Communities > Storage Configuration]** en selecteer **[!UICONTROL Adobe Storage Resource Provider (ASRP)]** .

![&#x200B; asrp-gebrek &#x200B;](assets/asrp-default.png)

De volgende informatie is afkomstig uit het inrichtingsproces:

* **Centrum URL van Gegevens**: Pull-down om het centrum van productiegegevens te selecteren dat door uw rekeningsvertegenwoordiger wordt geïdentificeerd.
* **Suite van het Standaard Rapport**: Ga de naam van de standaardrapportreeks in.
* **Consumentensleutel**: Ga de Consumentensleutel in.
* **Geheim**: Ga het geheim in.
* Selecteer **voorleggen**.

De publicatie-instanties voorbereiden:

* [De cryptotoets dupliceren](#replicate-the-crypto-key)
* [De configuratie dupliceren](#publishing-the-configuration)

Na het voorleggen van de configuratie, test de verbinding:

* Selecteer **Configuratie van de Test**.

  Voor elke auteur en publiceer instantie, test de verbinding aan het gegevenscentrum van de console van de Configuratie van de Opslag.

* Zorg ervoor dat de plaats URLs voor profielgegevens van het Centrum van Gegevens door [&#x200B; het externaliseren verbindingen &#x200B;](#externalize-links) routable zijn.

### De cryptosleutel dupliceren {#replicate-the-crypto-key}

De Consumentensleutel en de Geheime Sleutel worden gecodeerd. De sleutels worden alleen correct gecodeerd/gedecodeerd als de primaire Crypto-sleutel van Granite op alle AEM gelijk is.

Volg de instructies bij [&#x200B; Repliceer Crypto Sleutel &#x200B;](/help/communities/deploy-communities.md#replicate-the-crypto-key).

### Koppelingen extern maken {#externalize-links}

Voor correcte profiel en de verbindingen van het profielbeeld, ben zeker om [&#x200B; behoorlijk te vormen de Verbinding uiterlijk &#x200B;](/help/sites-developing/externalizer.md).

Ben zeker om de domeinen te plaatsen om URLs te zijn die van het Centrum URL van Gegevens (eindpunt ASRP) routable zijn.

### Tijdsynchronisatie {#time-synchronization}

Opdat authentificatie met het eindpunt van ASRP om te slagen, moeten de machines die uw ontvangen AEM Communities in werking stellen tijd gesynchroniseerd zijn, zoals met het [&#x200B; Protocol van de Tijd van het Netwerk (NTP) &#x200B;](https://www.ntp.org/).

### De configuratie publiceren {#publishing-the-configuration}

ASRP moet als gemeenschappelijke opslag op alle auteur en publiceer instanties worden geïdentificeerd.

De identieke configuratie beschikbaar stellen in de publicatieomgeving:

Op AEM instantie Auteur:

* Ga van hoofdmenu naar **[!UICONTROL Tools]** > **[!UICONTROL Deployment]** > **[!UICONTROL Replication]**
* Selecteer **activeren Boom**
* **Weg van het Begin**: doorblader aan `/conf/global/settings/communities/srpc/`
* Deselecteer **slechts Gewijzigd**
* Selecteer **activeren**

## Upgrade uitvoeren vanaf AEM 6.0 {#upgrading-from-aem}

>[!CAUTION]
>
>Als u ASRP op een gepubliceerde communautaire plaats toelaat, is om het even welke UGC die reeds in [&#x200B; JCR &#x200B;](/help/communities/jsrp.md) wordt opgeslagen niet meer zichtbaar, aangezien er geen synchronisatie van gegevens tussen opslag op locatie en wolkenopslag is.

**`AEM Communities Extension`** werd eerder in AEM 6.0 sociale gemeenschappen geïntroduceerd als cloudservice. Vanaf AEM 6.1 Gemeenschappen, is geen wolkenconfiguratie noodzakelijk, eenvoudig uitgezochte ASRP van de [&#x200B; console van de opslagconfiguratie &#x200B;](/help/communities/srp-config.md).

Wegens de nieuwe opslagstructuur, is het noodzakelijk om de [&#x200B; verbetering &#x200B;](/help/communities/upgrade.md#adobe-cloud-storage) instructies te volgen wanneer bevordering van sociale gemeenschappen aan Gemeenschappen.

## Gebruikersgegevens beheren {#managing-user-data}

Voor informatie betreffende *gebruikers*, *gebruikersprofielen* en *gebruikersgroepen*, vaak ingegaan in publiceer milieu, bezoek

* [Gebruikerssynchronisatie](/help/communities/sync.md)
* [Gebruikers en gebruikersgroepen beheren](/help/communities/users.md)

## Problemen oplossen {#troubleshooting}

### UGC verdwijnt na upgrade {#ugc-disappears-after-upgrade}

Als bevordering van een bestaande AEM 6.0 sociale communautaire plaats, ben zeker om de [&#x200B; verbeteringsinstructies &#x200B;](/help/communities/upgrade.md#adobe-cloud-storage) te volgen, anders lijkt UGC te worden verloren.

### Verificatiefouten {#authentication-errors}

Als het ontvangen van authentificatiefouten tegen het Centrum URL van Gegevens, en AEM error.log berichten over stabiele timestamps bevat, dan verifieer dat tijdsynchronisatie plaatsvindt.

Gebruik een hulpmiddel zoals het [&#x200B; Protocol van de Tijd van het Netwerk (NTP) &#x200B;](https://www.ntp.org/) om alle AEM auteur te synchroniseren en servers te publiceren.

### Nieuwe inhoud wordt niet weergegeven in zoekopdrachten {#new-content-does-not-appear-in-searches}

De de opslaginfrastructuur van de wolk van de Adobe gebruikt *uiteindelijke consistentie* om zijn het schrapen en prestatiesdoelstellingen te bereiken. Daarom is nieuwe inhoud niet direct beschikbaar en duurt het enkele seconden voordat deze in de zoekresultaten wordt weergegeven.

Terwijl het interval dat invloed heeft op de uiteindelijke consistentie wordt gecontroleerd, neemt u contact op met uw accountvertegenwoordiger als het langer dan een paar seconden duurt voordat nieuwe inhoud in zoekopdrachten wordt weergegeven.

### UGC niet zichtbaar in ASRP {#ugc-not-visible-in-asrp}

Zorg ervoor dat ASRP is gevormd om de standaardleverancier te zijn door de configuratie van de opslagoptie te controleren. Door gebrek, is de leverancier van het opslagmiddel JSRP, niet ASRP.

Ga bij alle auteurs en publiceer AEM instanties terug naar de opslagconfiguratieconsole of controleer de AEM opslagplaats.

In JCR, als [/conf/global/settings/community &#x200B;](https://localhost:4502/crx/de/index.jsp#/etc/socialconfig/):

* Bevat geen [&#x200B; srpc &#x200B;](https://localhost:4502/crx/de/index.jsp#/conf/global/settings/communities/srp) knoop, betekent het dat de opslagleverancier JSRP is.
* Als de srpc knoop bestaat en [&#x200B; standaardconfiguratie &#x200B;](https://localhost:4502/crx/de/index.jsp#/conf/global/settings/communities/srp/defaultconfiguration) knoop bevat, bepalen de eigenschappen van de standaardconfiguratie ASRP om de standaardleverancier te zijn.
