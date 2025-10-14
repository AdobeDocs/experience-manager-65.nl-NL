---
title: JSRP - JCR Storage Resource Provider
description: JSRP is het meest geschikt voor demonstratie- of ontwikkelomgevingen van één Publish-instantie en één Author-instantie
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

Wegens de eenvoud van plaatsing, is JSRP het best geschikt voor demonstratie of ontwikkelomgevingen van één instantie van Publish en één instantie van de Auteur.

Zie ook [&#x200B; Kenmerken van Opties SRP &#x200B;](working-with-srp.md#characteristics-of-srp-options) en [&#x200B; Aanbevolen Topologieën &#x200B;](topologies.md).

## Configuratie {#configuration}

### JSRP selecteren {#select-jsrp}

Standaard is JSRP de opslagoptie voor UGC.

De [&#x200B; console van de Configuratie van de Opslag &#x200B;](srp-config.md) staat voor de selectie van de standaardopslagconfiguratie toe, die identificeert welke implementatie van SRP aan gebruik.

In de auteursomgeving, om de console van de Configuratie van de Opslag te bereiken

* Vanuit globale navigatie: **[!UICONTROL Tools]** > **[!UICONTROL Communities]** > **[!UICONTROL Storage Configuration]**

* Selecteren **[!UICONTROL JCR Storage Resource Provider (JSRP)]**

* Selecteren **[!UICONTROL Submit]**

![&#x200B; jsrp-configuration &#x200B;](assets/jsrp-configuration.png)

### De configuratie publiceren {#publishing-the-configuration}

Terwijl JSRP de standaardconfiguratie is, om ervoor te zorgen dat de identieke configuratie in het publicatiemilieu wordt geplaatst:

* Vanuit globale navigatie: **[!UICONTROL Tools]** > **[!UICONTROL Deployment]** > **[!UICONTROL Replication]**
* Selecteer **[!UICONTROL Activate Tree]** > **[!UICONTROL Start Path]** :

   * Bladeren naar `/conf/global/settings/community/srpc/`

* Selecteren **[!UICONTROL Activate]**

## Gebruikersgegevens beheren {#managing-user-data}

Voor informatie betreffende *gebruikers*, *gebruikersprofielen* en *gebruikersgroepen*, vaak ingegaan in publiceer milieu, bezoek:

* [Gebruikerssynchronisatie](sync.md)
* [Gebruikers en gebruikersgroepen beheren](users.md)

## Problemen oplossen {#troubleshooting}

### UGC niet zichtbaar in JCR {#ugc-not-visible-in-jcr}

Zorg ervoor dat JSRP is gevormd om de standaardleverancier te zijn door de configuratie van de opslagoptie te controleren. Standaard is de opslagbronprovider JSRP.

Ga in alle AEM van Auteur en Publish naar de Storage Configuration-console of controleer de AEM:

* In JCR, als [/conf/global/settings/community &#x200B;](http://localhost:4502/crx/de/index.jsp#/conf/global/settings/community)

   * Het bevat geen [&#x200B; srpc &#x200B;](http://localhost:4502/crx/de/index.jsp#/conf/global/settings/community/srpc) knoop, het betekent dat de opslagleverancier JSRP is.
   * Als de srpc knoop bestaat en knoop [&#x200B; standaardconfiguratie &#x200B;](http://localhost:4502/crx/de/index.jsp#/conf/global/settings/community/srpc/defaultconfiguration) bevat, zouden de eigenschappen van de standaardconfiguratie JSRP moeten bepalen om de standaardleverancier te zijn.

### UGC niet zichtbaar op instantie Auteur {#ugc-not-visible-on-author-instance}

Dit is geen bug. Een kenmerk van JSRP is dat communautaire inhoud die in de publicatieomgeving wordt ingevoerd, alleen zichtbaar is in de Publish-omgeving.

### UGC niet zichtbaar op Publish-instantie {#ugc-not-visible-on-publish-instance}

Als één enkele instantie van Publish of als een publicatiecluster wordt opgesteld, dan volg de instructies voor [&#x200B; UGC niet Zichtbaar in JCR &#x200B;](#ugc-not-visible-in-jcr).

Als een publicatielandbouwbedrijf wordt opgesteld, is een kenmerk van JSRP dat de communautaire inhoud slechts zichtbaar op de instantie van Publish is waaraan het werd gepost.

Als u wilt dat UGC zichtbaar is vanuit een Publish-instantie, is een publicatiecluster vereist.
