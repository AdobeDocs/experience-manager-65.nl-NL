---
title: Opslagconfiguratie
description: Leer over de console van de Configuratie van de Opslag als middel om de opslag te identificeren die voor communautaire inhoud wordt gekozen, die ook als gebruiker-geproduceerde inhoud wordt bekend.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
role: Admin
exl-id: 67de7e26-3f93-4034-9e3a-5c127f7447bc
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# Opslagconfiguratie {#storage-configuration}

Opslagconfiguratie is het middel om de opslag te identificeren die voor communautaire inhoud wordt gekozen, die ook als gebruiker-geproduceerde inhoud (UGC) wordt bekend.

Deze instelling informeert de AEM Communities-code over de implementatie van de opslagbronprovider (SRP) die wordt gebruikt bij de toegang tot UGC. Het moet op de topologie wijzen die werd gevestigd toen Adobe Experience Manager (AEM) werd opgesteld.

Voor een bespreking van opslagopties en plaatsingstopologieën, bezoek:

* [Community Content Store](working-with-srp.md)
* [Aanbevolen topologieën](topologies.md)

## Opslagconfiguratieconsole {#storage-configuration-console}

![&#x200B; jsrp-configuration &#x200B;](assets/jsrp-configuration.png)

In de auteuromgeving, om de console van de opslagconfiguratie te bereiken.

* Selecteer **[!UICONTROL Tools]** > **[!UICONTROL Communities]** > **[!UICONTROL Storage Configuration]** bij globale navigatie

U selecteert als volgt een andere opslagoptie dan de standaard-JCR:

* Selecteer een optie
* Passend configureren

   * Zie details voor [&#x200B; selecterend MSRP &#x200B;](msrp.md#select-msrp)
   * Zie details voor [&#x200B; selecterend DSRP &#x200B;](dsrp.md#select-dsrp)
   * Zie details voor [&#x200B; selecterend ASRP &#x200B;](asrp.md#select-asrp)

* Selecteer **[!UICONTROL Submit]** .

### Informatie over JCR-opslag {#about-jcr-storage}

Als er geen selectie wordt gemaakt, is de standaardinstelling de AEM opslagplaats, JCR.

JCR is *niet* een gemeenschappelijke opslag die door de milieu&#39;s van de Auteur en van Publish wordt gedeeld. Community-inhoud is alleen zichtbaar in de auteur- of Publish-omgeving waarin deze is gemaakt.

Bezoek {de Opslag van 0} JCR [&#128279;](jsrp.md) voor extra informatie.

>[!NOTE]
>
>De afwezigheid van de knoop `srpc` onder `/etc/socialconfig` wijst op de standaard [&#x200B; opslag JCR &#x200B;](jsrp.md).
