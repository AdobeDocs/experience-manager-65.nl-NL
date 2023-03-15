---
title: Opslagconfiguratie
seo-title: Storage Configuration
description: Toegang tot de configuratieconsole voor opslag
seo-description: How to access the Storage Configuration Console
uuid: 6a5a71d5-6aaa-4635-8852-4dae33c497a9
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 71fac7e9-814a-48b5-b816-9bdcb2a05190
role: Admin
exl-id: 67de7e26-3f93-4034-9e3a-5c127f7447bc
source-git-commit: 603518dbe3d842a08900ac40651919c55392b573
workflow-type: tm+mt
source-wordcount: '194'
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

* Selecteer bij globale navigatie de optie **[!UICONTROL Tools]** > **[!UICONTROL Communities]** > **[!UICONTROL Storage Configuration]**

U selecteert als volgt een andere opslagoptie dan de standaard-JCR:

* Selecteer een optie
* Passend configureren

   * Zie details voor [selecteren van MSRP](msrp.md#select-msrp)
   * Zie details voor [selecteren, DSRP](dsrp.md#select-dsrp)
   * Zie details voor [selecteren van ASRP](asrp.md#select-asrp)

* Selecteer **[!UICONTROL Submit]**.

### Informatie over JCR-opslag {#about-jcr-storage}

Houd er rekening mee dat als er geen selectie wordt gemaakt, de standaardinstelling de AEM opslagplaats JCR is.

JCR is *niet* een gemeenschappelijke opslag die door de auteur en het publiceren milieu&#39;s wordt gedeeld. Community-inhoud is alleen zichtbaar van de auteur- of publicatieomgeving waarin deze is gemaakt.

Bezoek [JCR-winkel](jsrp.md) voor aanvullende informatie.

>[!NOTE]
>
>De afwezigheid van het knooppunt `srpc` krachtens `/etc/socialconfig` Hiermee wordt de standaardinstelling aangegeven [JCR-archief](jsrp.md).
