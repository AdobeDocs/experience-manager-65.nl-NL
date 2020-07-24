---
title: JSRP - JCR Storage Resource Provider
seo-title: JSRP - JCR Storage Resource Provider
description: JSRP is over het algemeen het meest geschikt voor demonstratie- of ontwikkelomgevingen van één publicatie-instantie en één auteur-instantie
seo-description: JSRP is over het algemeen het meest geschikt voor demonstratie- of ontwikkelomgevingen van één publicatie-instantie en één auteur-instantie
uuid: 358a43c1-4137-4300-8443-c0d7166968ad
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: f5316a73-84e2-4a18-98c1-a384eeaa77cf
translation-type: tm+mt
source-git-commit: c798eb79dc9f8e58cef86cf90af02622c3a2ed78
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 1%

---


# JSRP - JCR Storage Resource Provider {#jsrp-jcr-storage-resource-provider}

## Info over JSRP {#about-jsrp}

Wanneer AEM Communities JSRP als opslagoptie gebruiken (de standaardinstelling), wordt inhoud van de gemeenschap opgeslagen in JCR en door de gebruiker gegenereerde inhoud (UGC) is alleen toegankelijk van de auteur of de publicatieinstantie waarnaar deze is gepost.

Wegens de eenvoud van plaatsing, is JSRP over het algemeen best geschikt voor demonstratie of ontwikkelingsmilieu&#39;s van één publiceer instantie en één auteursinstantie.

Zie ook [Kenmerken van Opties](working-with-srp.md#characteristics-of-srp-options) SRP en [Aanbevolen Topologieën](topologies.md).

## Configuratie {#configuration}

### JSRP selecteren {#select-jsrp}

Standaard is JSRP de opslagoptie voor UGC.

De console [van de Configuratie van de](srp-config.md) Opslag staat voor de selectie van de standaardopslagconfiguratie toe, die identificeert welke implementatie van SRP aan gebruik.

In de auteursomgeving, om de console van de Configuratie van de Opslag te bereiken

* Vanuit globale navigatie: **[!UICONTROL Tools]** > **[!UICONTROL Communities]** > **[!UICONTROL Storage Configuration]**

* Selecteer **[!UICONTROL JCR Storage Resource Provider (JSRP)]**

* Selecteer **[!UICONTROL Submit]**

![chlimage_1-234](assets/chlimage_1-234.png)

### De configuratie publiceren {#publishing-the-configuration}

Terwijl JSRP de standaardconfiguratie is, om ervoor te zorgen dat de identieke configuratie in het publicatiemilieu wordt geplaatst:

* Op auteur:

   * Vanuit globale navigatie: **[!UICONTROL Tools]** > **[!UICONTROL Deployment]** > **[!UICONTROL Replication]**
   * Selecteer **[!UICONTROL Activate Tree]** > **[!UICONTROL Start Path]**:

      * Bladeren naar `/conf/global/settings/community/srpc/`
   * Selecteer **[!UICONTROL Activate]**


## Gebruikersgegevens beheren {#managing-user-data}

Voor informatie over *gebruikers*, *gebruikersprofielen* en *gebruikersgroepen*, die vaak in publicatieomgeving worden ingevoerd, gaat u naar:

* [Gebruikerssynchronisatie](sync.md)
* [Gebruikers en gebruikersgroepen beheren](users.md)

## Problemen oplossen {#troubleshooting}

### UGC niet zichtbaar in JCR {#ugc-not-visible-in-jcr}

Zorg ervoor JSRP is gevormd om de standaardleverancier te zijn door de configuratie van de opslagoptie te controleren. Standaard is de leverancier van de opslagbron JSRP.

Ga bij alle auteurs naar de opslagconfiguratieconsole of controleer de AEM-opslagplaats op alle AEM-exemplaren en publiceer deze:

* In JCR, als [/conf/global/settings/community](http://localhost:4502/crx/de/index.jsp#/conf/global/settings/community)

   * Bevat geen [srpc](http://localhost:4502/crx/de/index.jsp#/conf/global/settings/community/srpc) knoop, betekent het de opslagleverancier JSRP is.
   * Als de srpc knoop bestaat en knoop [standaardconfiguratie](http://localhost:4502/crx/de/index.jsp#/conf/global/settings/community/srpc/defaultconfiguration)bevat, zouden de eigenschappen van de standaardconfiguratie JSRP moeten bepalen om de standaardleverancier te zijn.

### UGC niet zichtbaar op instantie Auteur {#ugc-not-visible-on-author-instance}

Dit is geen bug. Een kenmerk van JSRP is dat communautaire inhoud die in de publicatieomgeving wordt ingevoerd, alleen zichtbaar is in de publicatieomgeving.

### UGC niet zichtbaar bij publicatie-instantie {#ugc-not-visible-on-publish-instance}

Als één publiceer instantie of als een publicatiecluster wordt opgesteld, dan volg instructies voor [UGC niet Zichtbaar in JCR](#ugc-not-visible-in-jcr).

Als een publicatielandbouwbedrijf wordt opgesteld, is een kenmerk van JSRP dat de communautaire inhoud slechts op publicatiegeval zichtbaar zal zijn waaraan het werd gepost.

Om ervoor te zorgen dat UGC zichtbaar is vanuit elke publicatie-instantie, is een publicatiecluster vereist.
