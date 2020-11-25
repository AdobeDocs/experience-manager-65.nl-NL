---
title: ASRP - Adobe Storage Resource Provider
seo-title: ASRP - Adobe Storage Resource Provider
description: AEM Communities instellen om een relationele database te gebruiken als de algemene opslag
seo-description: AEM Communities instellen om een relationele database te gebruiken als de algemene opslag
uuid: abe47ad9-9f72-4dad-a5e9-6d621a9722d4
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 3e81b519-57ca-4ee1-94bd-7adac4605407
docset: aem65
translation-type: tm+mt
source-git-commit: ef57d53fc780bd222abbe994fc71e133ce8a77fc
workflow-type: tm+mt
source-wordcount: '815'
ht-degree: 0%

---


# ASRP - Adobe Storage Resource Provider {#asrp-adobe-storage-resource-provider}

## Info over ASRP {#about-asrp}

Wanneer AEM Communities wordt gevormd om ASRP als zijn gemeenschappelijke opslag te gebruiken, is de gebruiker geproduceerde inhoud (UGC) toegankelijk van alle auteur en publiceer instanties zonder de behoefte aan synchronisatie of replicatie.

Zie ook [Kenmerken van Opties](/help/communities/working-with-srp.md#characteristics-of-srp-options) SRP en [Aanbevolen Topologieën](/help/communities/topologies.md).

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

De console [van de Configuratie van de](/help/communities/srp-config.md) Opslag staat voor de selectie van de standaardopslagconfiguratie toe, die identificeert welke implementatie van SRP aan gebruik.

**Instantie van AEM-auteur:**

* Navigeer vanuit globale navigatie naar **[!UICONTROL Tools > Communities > Storage Configuration]** en selecteer **[!UICONTROL Adobe Storage Resource Provider (ASRP)]**.

![asrp-default](assets/asrp-default.png)

De volgende informatie is afkomstig uit het inrichtingsproces:

* **URL** datacenter: Kies het productiecentrum dat door uw accountvertegenwoordiger is geïdentificeerd.
* **Standaardrapportsuite**: Ga de naam van de standaardrapportreeks in.
* **Consumentencode**: Voer de sleutel voor de consument in.
* **Geheim**: Voer het geheim in.
* Selecteer **Verzenden**.

De publicatie-instanties voorbereiden:

* [De cryptotoets dupliceren](#replicate-the-crypto-key)
* [De configuratie dupliceren](#publishing-the-configuration)

Na het voorleggen van de configuratie, test de verbinding:

* Selecteer **Config** testen.

   Voor elke auteur en publiceer instantie, test de verbinding aan het gegevenscentrum van de console van de Configuratie van de Opslag.

* Zorg ervoor dat de site-URL&#39;s voor profielgegevens vanuit het datacenter routeerbaar zijn door koppelingen [te extern](#externalize-links)maken.

### De cryptosleutel dupliceren {#replicate-the-crypto-key}

De Consumentensleutel en de Geheime Sleutel worden gecodeerd. De sleutels worden alleen correct gecodeerd/gedecodeerd als de primaire Crypto-sleutel van Granite op alle AEM gelijk is.

Volg de instructies bij [Replicate de Sleutel](/help/communities/deploy-communities.md#replicate-the-crypto-key)van Crypto.

### Koppelingen extern maken {#externalize-links}

Voor correcte profiel en de verbindingen van het profielbeeld, ben zeker om de Verbinding Externalzer [behoorlijk te](/help/sites-developing/externalizer.md)vormen.

Ben zeker om de domeinen te plaatsen om URLs te zijn die van het Centrum URL van Gegevens (het eindpunt van ASRP) routable zijn.

### Tijdsynchronisatie {#time-synchronization}

Opdat de authentificatie met het eindpunt van ASRP om te slagen, moeten de machines die uw ontvangen AEM Communities in werking stellen tijd gesynchroniseerd zijn, zoals met het Protocol van de Tijd van het [Netwerk (NTP)](https://www.ntp.org/).

### De configuratie publiceren {#publishing-the-configuration}

ASRP moet als gemeenschappelijke opslag op alle auteur en publiceer instanties worden geïdentificeerd.

De identieke configuratie beschikbaar stellen in de publicatieomgeving:

Instantie van AEM-auteur:

* Navigeer van hoofdmenu aan **[!UICONTROL Tools > Operations > Replication]**.
* Boomstructuur **activeren selecteren**
* **Startpad**: bladeren naar `/etc/socialconfig/srpc/`
* Selectie **alleen gewijzigd opheffen**
* Selecteer **Activeren**

## Upgrade uitvoeren vanaf AEM 6.0 {#upgrading-from-aem}

>[!CAUTION]
>
>Als u ASRP op een gepubliceerde communautaire plaats toelaat, is om het even welke UGC die reeds in [JCR](/help/communities/jsrp.md) wordt opgeslagen niet meer zichtbaar, aangezien er geen synchronisatie van gegevens tussen on-premise opslag en wolkenopslag is.

**`AEM Communities Extension`** werd eerder in AEM 6.0 sociale gemeenschappen geïntroduceerd als cloudservice. Vanaf AEM 6.1 Communities is geen wolkenconfiguratie nodig, selecteer eenvoudig ASRP van de console [van de](/help/communities/srp-config.md)opslagconfiguratie.

Vanwege de nieuwe opslagstructuur is het nodig de [upgradeinstructies](/help/communities/upgrade.md#adobe-cloud-storage) te volgen wanneer de overstap van sociale gemeenschappen naar Gemeenschappen wordt verbeterd.

## Gebruikersgegevens beheren {#managing-user-data}

Voor informatie over *gebruikers*, *gebruikersprofielen* en *gebruikersgroepen*, die vaak worden ingevoerd in de publicatieomgeving, gaat u naar

* [Gebruikerssynchronisatie](/help/communities/sync.md)
* [Gebruikers en gebruikersgroepen beheren](/help/communities/users.md)

## Problemen oplossen {#troubleshooting}

### UGC verdwijnt na upgrade {#ugc-disappears-after-upgrade}

Als de verbetering van een bestaande AEM 6.0 sociale gemeenschapsplaats, zeker is om de [verbeteringsinstructies](/help/communities/upgrade.md#adobe-cloud-storage)te volgen, anders schijnt UGC te worden verloren.

### Verificatiefouten {#authentication-errors}

Als het ontvangen van authentificatiefouten tegen het Centrum URL van Gegevens, en AEM error.log berichten over stabiele timestamps bevat, dan verifieer dat tijdsynchronisatie plaatsvindt.

Gebruik een hulpmiddel zoals het Protocol van de Tijd van het [Netwerk (NTP)](https://www.ntp.org/) om alle AEM auteur te synchroniseren en te publiceren servers.

### Nieuwe inhoud wordt niet weergegeven in zoekopdrachten {#new-content-does-not-appear-in-searches}

De Adobe-infrastructuur voor cloudopslag maakt gebruik van *uiteindelijke consistentie* om de schaalings- en prestatiedoelstellingen te bereiken. Daarom is nieuwe inhoud niet direct beschikbaar en duurt het enkele seconden voordat deze in de zoekresultaten wordt weergegeven.

Terwijl het interval dat invloed heeft op de uiteindelijke consistentie wordt gecontroleerd, neemt u contact op met uw accountvertegenwoordiger als het langer dan een paar seconden duurt voordat nieuwe inhoud in zoekopdrachten wordt weergegeven.

### UGC niet zichtbaar in ASRP {#ugc-not-visible-in-asrp}

Zorg ervoor dat ASRP is gevormd om de standaardleverancier te zijn door de configuratie van de opslagoptie te controleren. Door gebrek, is de leverancier van het opslagmiddel JSRP, niet ASRP.

Ga bij alle auteurs en publiceer AEM instanties terug naar de opslagconfiguratieconsole of controleer de AEM opslagplaats.

In JCR, als [/etc/socialconfig](https://localhost:4502/crx/de/index.jsp#/etc/socialconfig/):

* Bevat geen [srpc](https://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc) knoop, betekent het dat de opslagleverancier JSRP is.
* Als de srpc knoop bestaat en knoop [standaardconfiguratie](https://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc/defaultconfiguration)bevat, bepalen de eigenschappen van de standaardconfiguratie ASRP om de standaardleverancier te zijn.

