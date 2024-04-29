---
title: JSRP - JCR Storage Resource Provider
description: JSRP is het meest geschikt voor demonstratie- of ontwikkelomgevingen van één instantie Publish en één instantie Auteur
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
role: Admin
exl-id: 873e013c-a2da-4b37-b0e3-56bdf240004a
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# JSRP - JCR Storage Resource Provider {#jsrp-jcr-storage-resource-provider}

## Info over JSRP {#about-jsrp}

Wanneer AEM Communities JSRP gebruikt als opslagoptie (de standaardinstelling), wordt inhoud van de community opgeslagen in de JCR en door de gebruiker gegenereerde inhoud (UGC) is alleen toegankelijk van de auteur of de publicatieinstantie waarnaar deze is gepost.

Wegens de eenvoud van plaatsing, is JSRP best geschikt voor demonstratie of ontwikkelomgevingen van één Publish instantie en één Auteur instantie.

Zie ook [Kenmerken van SRP-opties](working-with-srp.md#characteristics-of-srp-options) en [Aanbevolen topologieën](topologies.md).

## Configuratie {#configuration}

### JSRP selecteren {#select-jsrp}

Standaard is JSRP de opslagoptie voor UGC.

De [Opslagconfiguratieconsole](srp-config.md) maakt het mogelijk de standaardopslagconfiguratie te selecteren, die aangeeft welke implementatie van SRP moet worden gebruikt.

In de auteursomgeving, om de console van de Configuratie van de Opslag te bereiken

* Vanuit globale navigatie: **[!UICONTROL Tools]** > **[!UICONTROL Communities]** > **[!UICONTROL Storage Configuration]**

* Selecteren **[!UICONTROL JCR Storage Resource Provider (JSRP)]**

* Selecteren **[!UICONTROL Submit]**

![jsrp-configuration](assets/jsrp-configuration.png)

### De configuratie publiceren {#publishing-the-configuration}

Terwijl JSRP de standaardconfiguratie is, om ervoor te zorgen dat de identieke configuratie in het publicatiemilieu wordt geplaatst:

* Vanuit globale navigatie: **[!UICONTROL Tools]** > **[!UICONTROL Deployment]** > **[!UICONTROL Replication]**
* Selecteren **[!UICONTROL Activate Tree]** > **[!UICONTROL Start Path]**:

   * Bladeren naar `/conf/global/settings/community/srpc/`

* Selecteren **[!UICONTROL Activate]**

## Gebruikersgegevens beheren {#managing-user-data}

Voor informatie over *gebruikers*, *gebruikersprofielen* en *gebruikersgroepen*, die vaak in de publicatieomgeving worden ingevoerd, gaat u naar:

* [Gebruikerssynchronisatie](sync.md)
* [Gebruikers en gebruikersgroepen beheren](users.md)

## Problemen oplossen {#troubleshooting}

### UGC niet zichtbaar in JCR {#ugc-not-visible-in-jcr}

Zorg ervoor dat JSRP is gevormd om de standaardleverancier te zijn door de configuratie van de opslagoptie te controleren. Standaard is de opslagbronprovider JSRP.

Ga bij alle AEM Auteur en Publiceren naar de Storage Configuration-console of controleer de AEM:

* In JCR, als [/conf/global/settings/community](http://localhost:4502/crx/de/index.jsp#/conf/global/settings/community)

   * Het bevat geen [srpc](http://localhost:4502/crx/de/index.jsp#/conf/global/settings/community/srpc) knoop, betekent het dat de opslagleverancier JSRP is.
   * Als het srpc-knooppunt bestaat en het knooppunt bevat [standaardconfiguratie](http://localhost:4502/crx/de/index.jsp#/conf/global/settings/community/srpc/defaultconfiguration), zouden de eigenschappen van de standaardconfiguratie JSRP moeten bepalen om de standaardleverancier te zijn.

### UGC niet zichtbaar op instantie Auteur {#ugc-not-visible-on-author-instance}

Dit is geen bug. Een kenmerk van JSRP is dat communautaire inhoud die wordt ingevoerd in de publicatieomgeving, alleen zichtbaar is in de publicatieomgeving.

### UGC niet zichtbaar bij publicatie-instantie {#ugc-not-visible-on-publish-instance}

Als één enkel Publish instantie of als publicatiecluster wordt opgesteld, dan volg de instructies voor [UGC niet zichtbaar in JCR](#ugc-not-visible-in-jcr).

Als een publicatielandbouwbedrijf wordt opgesteld, is een kenmerk van JSRP dat de communautaire inhoud slechts zichtbaar op de Publish instantie is waaraan het werd gepost.

Om ervoor te zorgen dat UGC zichtbaar is vanuit elke publicatie-instantie, is een publicatiecluster vereist.
