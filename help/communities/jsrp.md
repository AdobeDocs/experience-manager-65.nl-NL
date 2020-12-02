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
source-git-commit: e7268e43620860b7a1f7aa0a1f1a54199dadcf17
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 1%

---


# JSRP - JCR Storage Resource Provider {#jsrp-jcr-storage-resource-provider}

## Info over JSRP {#about-jsrp}

Wanneer AEM Communities JSRP als opslagoptie gebruikt (de standaardinstelling), wordt inhoud van de community opgeslagen in JCR en door de gebruiker gegenereerde inhoud (UGC) is alleen toegankelijk van de auteur of de publicatieinstantie waarnaar deze is gepost.

Wegens de eenvoud van plaatsing, is JSRP over het algemeen best geschikt voor demonstratie of ontwikkelingsmilieu&#39;s van één publiceer instantie en één auteursinstantie.

Zie ook [Kenmerken van SRP Options](working-with-srp.md#characteristics-of-srp-options) en [Recommended Topologies](topologies.md).

## Configuratie {#configuration}

### JSRP {#select-jsrp} selecteren

Standaard is JSRP de opslagoptie voor UGC.

Met de [Opslagconfiguratieconsole](srp-config.md) kunt u de standaardopslagconfiguratie selecteren, die aangeeft welke implementatie van SRP moet worden gebruikt.

In de auteursomgeving, om de console van de Configuratie van de Opslag te bereiken

* Vanuit globale navigatie: **[!UICONTROL Tools]** > **[!UICONTROL Communities]** > **[!UICONTROL Storage Configuration]**

* Selecteer **[!UICONTROL JCR Storage Resource Provider (JSRP)]**

* Selecteer **[!UICONTROL Submit]**

![jsrp-configuration](assets/jsrp-configuration.png)

### De configuratie {#publishing-the-configuration} publiceren

Terwijl JSRP de standaardconfiguratie is, om ervoor te zorgen dat de identieke configuratie in het publicatiemilieu wordt geplaatst:

* Vanuit globale navigatie: **[!UICONTROL Tools]** > **[!UICONTROL Deployment]** > **[!UICONTROL Replication]**
* Selecteer **[!UICONTROL Activate Tree]** > **[!UICONTROL Start Path]**:

   * Bladeren naar `/conf/global/settings/community/srpc/`

* Selecteer **[!UICONTROL Activate]**

## Gebruikersgegevens {#managing-user-data} beheren

Voor informatie over *gebruikers*, *gebruikersprofielen* en *gebruikersgroepen*, die vaak in publicatieomgeving worden ingevoerd, gaat u naar:

* [Gebruikerssynchronisatie](sync.md)
* [Gebruikers en gebruikersgroepen beheren](users.md)

## Problemen oplossen {#troubleshooting}

### UGC niet zichtbaar in JCR {#ugc-not-visible-in-jcr}

Zorg ervoor JSRP is gevormd om de standaardleverancier te zijn door de configuratie van de opslagoptie te controleren. Standaard is de leverancier van de opslagbron JSRP.

Ga bij alle auteur- en publiceer AEM naar de opslagconfiguratieconsole of controleer de AEM opslagplaats:

* In JCR, als [/conf/global/settings/community](http://localhost:4502/crx/de/index.jsp#/conf/global/settings/community)

   * Bevat geen [srpc](http://localhost:4502/crx/de/index.jsp#/conf/global/settings/community/srpc) knoop, het betekent de opslagleverancier JSRP is.
   * Als het srpc-knooppunt bestaat en knooppunt [default configuration](http://localhost:4502/crx/de/index.jsp#/conf/global/settings/community/srpc/defaultconfiguration) bevat, moeten de eigenschappen van de standaardconfiguratie JSRP definiëren als de standaardprovider.

### UGC niet zichtbaar op Auteursinstantie {#ugc-not-visible-on-author-instance}

Dit is geen bug. Een kenmerk van JSRP is dat communautaire inhoud die in de publicatieomgeving wordt ingevoerd, alleen zichtbaar is in de publicatieomgeving.

### UGC niet zichtbaar op instantie publiceren {#ugc-not-visible-on-publish-instance}

Als één enkele publiceer instantie of als een publicatiecluster wordt opgesteld, dan volg instructies voor [UGC niet Zichtbaar in JCR](#ugc-not-visible-in-jcr).

Als een publicatielandbouwbedrijf wordt opgesteld, is een kenmerk van JSRP dat de communautaire inhoud slechts op publicatiegeval zichtbaar zal zijn waaraan het werd gepost.

Om ervoor te zorgen dat UGC zichtbaar is vanuit elke publicatie-instantie, is een publicatiecluster vereist.
