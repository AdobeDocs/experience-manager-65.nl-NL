---
title: Configureren voor AEM toepassingen
seo-title: Configureren voor AEM toepassingen
description: Leer hoe u AEM toepassingen configureert.
seo-description: Leer hoe u AEM toepassingen configureert.
uuid: ab9acd93-da7f-4bb7-8d26-224044899068
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: 34f24837-f5e2-41f0-a359-fdb695e1b8f2
translation-type: tm+mt
source-git-commit: 684d2d5f73d571a15c8155e7870134c28dc892b7
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 0%

---


# Het vormen voor AEM Apps{#configuring-for-aem-apps}

Adobe Experience Manager Apps biedt de mogelijkheid om de inhoud van uw toepassing via de lucht (OTA) bij te werken. De bijgewerkte inhoud wordt opgeslagen in de publicatieinstantie. Om de toepassing op uw apparaat toe te staan verbinding te maken met de publicatie-instantie en te controleren op updates, moet de publicatie-instantie worden geconfigureerd om een lege verwijzingskoptekst toe te staan.

## Leeg verwijzingskoptekst {#configuring-empty-referrer-header} configureren

Om de dienst van het verwijzingsfilter te vormen:

* Open de Apache Felix-console (**Configurations**) op:
* https://&lt;server>:&lt;port_number>/system/console/configMgr
* Aanmelden als beheerder.
* Selecteer in het menu **Configuraties**: *Apache Sling Referrer Filter*
* Schakel het veld Lege toestaan in om lege/ontbrekende verwijzingskoppen toe te staan.
* Klik **Opslaan** om uw wijzigingen op te slaan.

![chlimage_1-58](assets/chlimage_1-58a.png)

Zie [OSGI Configuration Settings](/help/sites-deploying/osgi-configuration-settings.md) en [Security Checklist - Issues with Cross-Site Request Modification](/help/sites-administering/security-checklist.md#protect-against-cross-site-request-forgery) voor meer informatie.
