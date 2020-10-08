---
title: Opslagconfiguratie
seo-title: Opslagconfiguratie
description: Toegang tot de configuratieconsole voor opslag
seo-description: Toegang tot de configuratieconsole voor opslag
uuid: 6a5a71d5-6aaa-4635-8852-4dae33c497a9
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 71fac7e9-814a-48b5-b816-9bdcb2a05190
translation-type: tm+mt
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---


# Opslagconfiguratie {#storage-configuration}

Opslagconfiguratie is het middel om de opslag te identificeren die voor communautaire inhoud wordt gekozen, die ook als gebruiker geproduceerde inhoud (UGC) wordt bekend.

Dit het plaatsen informeert de code van AEM Communities over welke implementatie van de leverancier van het opslagmiddel (SRP) moet worden gebruikt wanneer het toegang tot van UGC en moet op de topologie wijzen die wordt gevestigd toen AEM werd opgesteld.

Voor een bespreking van opslagopties en plaatsingstopologieën, bezoek:

* [Community Content Store](working-with-srp.md)
* [Aanbevolen topologieën](topologies.md)

## Opslagconfiguratieconsole {#storage-configuration-console}

![jsrp-configuration](assets/jsrp-configuration.png)

In het auteursmilieu, om de console van de opslagconfiguratie te bereiken.

* Selecteer **[!UICONTROL Tools]** > **[!UICONTROL Communities]** > **[!UICONTROL Storage Configuration]**

U selecteert als volgt een andere opslagoptie dan de standaard-JCR:

* Selecteer een optie
* Passend configureren

   * Zie details voor het [selecteren van MSRP](msrp.md#select-msrp)
   * Zie details voor het [selecteren van DSRP](dsrp.md#select-dsrp)
   * Zie details voor het [selecteren van ASRP](asrp.md#select-asrp)

* Selecteer **[!UICONTROL Submit]**.

### Informatie over JCR-opslag {#about-jcr-storage}

Houd er rekening mee dat als er geen selectie wordt gemaakt, de standaardinstelling de AEM opslagplaats JCR is.

JCR is *geen* algemene winkel die door de auteur- en publicatieomgeving wordt gedeeld. Community-inhoud is alleen zichtbaar van de auteur- of publicatieomgeving waarin deze is gemaakt.

Ga naar de [JCR Store](jsrp.md) voor meer informatie.

>[!NOTE]
>
>De afwezigheid van het knooppunt `srpc` onder `/etc/socialconfig` geeft de standaard [JCR-opslag](jsrp.md)aan.
