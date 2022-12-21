---
title: ASRP - Adobe Storage Resource Provider
seo-title: ASRP - Adobe Storage Resource Provider
description: AEM Communities instellen om een relationele database te gebruiken als de algemene opslag
seo-description: Set up AEM Communities to use a relational database as its common store
uuid: abe47ad9-9f72-4dad-a5e9-6d621a9722d4
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 3e81b519-57ca-4ee1-94bd-7adac4605407
docset: aem65
role: Admin
exl-id: 6430ed96-5d96-41b6-866f-90b34ff84f7a
source-git-commit: 42feafa381c129117dae5345255702f0b0951a17
workflow-type: tm+mt
source-wordcount: '803'
ht-degree: 0%

---

# ASRP - Adobe Storage Resource Provider {#asrp-adobe-storage-resource-provider}

## Info over ASRP {#about-asrp}

Wanneer AEM Communities wordt gevormd om ASRP als zijn gemeenschappelijke opslag te gebruiken, is de gebruiker geproduceerde inhoud (UGC) toegankelijk van alle auteur en publiceer instanties zonder de behoefte aan synchronisatie of replicatie.

Zie ook [Kenmerken van SRP-opties](/help/communities/working-with-srp.md#characteristics-of-srp-options) en [Aanbevolen topologieën](/help/communities/topologies.md).

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

De [Opslagconfiguratieconsole](/help/communities/srp-config.md) maakt het mogelijk de standaardopslagconfiguratie te selecteren, die aangeeft welke implementatie van SRP moet worden gebruikt.

**Instantie van AEM-auteur:**

* Navigeer van globale navigatie naar **[!UICONTROL Tools > Communities > Storage Configuration]** en selecteert u **[!UICONTROL Adobe Storage Resource Provider (ASRP)]**.

![asrp-default](assets/asrp-default.png)

De volgende informatie is afkomstig uit het inrichtingsproces:

* **URL datacenter**: Kies het productiecentrum dat door uw accountvertegenwoordiger is geïdentificeerd.
* **Standaardrapportsuite**: Ga de naam van de standaardrapportreeks in.
* **Consumentencode**: Voer de sleutel voor de consument in.
* **Geheim**: Voer het geheim in.
* Selecteren **Verzenden**.

De publicatie-instanties voorbereiden:

* [De cryptotoets dupliceren](#replicate-the-crypto-key)
* [De configuratie dupliceren](#publishing-the-configuration)

Na het voorleggen van de configuratie, test de verbinding:

* Selecteren **Config. testen**.

   Voor elke auteur en publiceer instantie, test de verbinding aan het gegevenscentrum van de console van de Configuratie van de Opslag.

* Zorg ervoor dat de site-URL&#39;s voor profielgegevens vanuit het datacenter kunnen worden gerouteerd door [externe koppelingen](#externalize-links).

### De cryptosleutel dupliceren {#replicate-the-crypto-key}

De Consumentensleutel en de Geheime Sleutel worden gecodeerd. De sleutels worden alleen correct gecodeerd/gedecodeerd als de primaire Crypto-sleutel van Granite op alle AEM gelijk is.

Volg de instructies op [De cryptosleutel dupliceren](/help/communities/deploy-communities.md#replicate-the-crypto-key).

### Koppelingen extern maken {#externalize-links}

Voor correcte profiel- en profielafbeeldingskoppelingen moet u controleren of deze correct zijn [Vorm de Verbinding Externalzer](/help/sites-developing/externalizer.md).

Ben zeker om de domeinen te plaatsen om URLs te zijn die van het Centrum URL van Gegevens (het eindpunt van ASRP) routable zijn.

### Tijdsynchronisatie {#time-synchronization}

Om authentificatie met het eindpunt van ASRP te slagen, moeten de machines die uw ontvangen AEM Communities in werking stellen tijd gesynchroniseerd zijn, zoals met [Netwerktijdprotocol (NTP)](https://www.ntp.org/).

### De configuratie publiceren {#publishing-the-configuration}

ASRP moet als gemeenschappelijke opslag op alle auteur en publiceer instanties worden geïdentificeerd.

De identieke configuratie beschikbaar stellen in de publicatieomgeving:

Instantie van AEM-auteur:

* Navigeren van hoofdmenu naar **[!UICONTROL Tools]** > **[!UICONTROL Deployment]** > **[!UICONTROL Replication]**
* Selecteren **Boom activeren**
* **Startpad**: bladeren naar `/conf/global/settings/communities/srpc/`
* Deselecteren **Alleen gewijzigd**
* Selecteren **Activeren**

## Upgrade uitvoeren vanaf AEM 6.0 {#upgrading-from-aem}

>[!CAUTION]
>
>Als u ASRP op een gepubliceerde communautaire plaats toelaat, om het even welke UGC die reeds in wordt opgeslagen [JCR](/help/communities/jsrp.md) niet meer zichtbaar is, aangezien er geen synchronisatie van gegevens tussen on-premise opslag en wolkenopslag is.

**`AEM Communities Extension`** werd eerder in AEM 6.0 sociale gemeenschappen geïntroduceerd als cloudservice. Vanaf AEM 6.1 Gemeenschappen is geen wolkenconfiguratie noodzakelijk, eenvoudig uitgezocht ASRP van [opslagconfiguratieconsole](/help/communities/srp-config.md).

Gezien de nieuwe opslagstructuur is het noodzakelijk de [upgrade](/help/communities/upgrade.md#adobe-cloud-storage) instructies bij de opwaardering van sociale gemeenschappen naar gemeenschappen.

## Gebruikersgegevens beheren {#managing-user-data}

Voor informatie over *gebruikers*, *gebruikersprofielen* en *gebruikersgroepen*, die vaak in de publicatieomgeving worden ingevoerd, gaat u naar

* [Gebruikerssynchronisatie](/help/communities/sync.md)
* [Gebruikers en gebruikersgroepen beheren](/help/communities/users.md)

## Problemen oplossen {#troubleshooting}

### UGC verdwijnt na upgrade {#ugc-disappears-after-upgrade}

Als u een upgrade uitvoert van een bestaande AEM 6.0-site voor de sociale gemeenschap, moet u de [upgradeinstructies](/help/communities/upgrade.md#adobe-cloud-storage), anders lijkt UGC verloren te gaan.

### Verificatiefouten {#authentication-errors}

Als het ontvangen van authentificatiefouten tegen het Centrum URL van Gegevens, en AEM error.log berichten over stabiele timestamps bevat, dan verifieer dat tijdsynchronisatie plaatsvindt.

Een gereedschap zoals de [Netwerktijdprotocol (NTP)](https://www.ntp.org/) om alle AEM auteur- en publicatieservers te synchroniseren.

### Nieuwe inhoud wordt niet weergegeven in zoekopdrachten {#new-content-does-not-appear-in-searches}

De Adobe-cloudopslaginfrastructuur gebruikt *uiteindelijke consistentie* de schaalings- en prestatiedoelstellingen te bereiken. Daarom is nieuwe inhoud niet direct beschikbaar en duurt het enkele seconden voordat deze in de zoekresultaten wordt weergegeven.

Terwijl het interval dat invloed heeft op de uiteindelijke consistentie wordt gecontroleerd, neemt u contact op met uw accountvertegenwoordiger als het langer dan een paar seconden duurt voordat nieuwe inhoud in zoekopdrachten wordt weergegeven.

### UGC niet zichtbaar in ASRP {#ugc-not-visible-in-asrp}

Zorg ervoor dat ASRP is gevormd om de standaardleverancier te zijn door de configuratie van de opslagoptie te controleren. Door gebrek, is de leverancier van het opslagmiddel JSRP, niet ASRP.

Ga bij alle auteurs en publiceer AEM instanties terug naar de opslagconfiguratieconsole of controleer de AEM opslagplaats.

In JCR, als [/conf/global/settings/community](https://localhost:4502/crx/de/index.jsp#/etc/socialconfig/):

* Bevat geen [srpc](https://localhost:4502/crx/de/index.jsp#/conf/global/settings/communities/srp) knoop, betekent het dat de opslagleverancier JSRP is.
* Als het srpc-knooppunt bestaat en bevat [standaardconfiguratie](https://localhost:4502/crx/de/index.jsp#/conf/global/settings/communities/srp/defaultconfiguration) knoop, bepalen de eigenschappen van de standaardconfiguratie ASRP om de standaardleverancier te zijn.
