---
title: Configureren voor AEM toepassingen
seo-title: Configuring for AEM Apps
description: Leer hoe u AEM toepassingen configureert.
seo-description: Learn how to configure AEM Apps.
uuid: ab9acd93-da7f-4bb7-8d26-224044899068
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: 34f24837-f5e2-41f0-a359-fdb695e1b8f2
exl-id: f7aa5ac0-3d03-4c04-b9c2-1bda427b0588
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---

# Configureren voor AEM toepassingen{#configuring-for-aem-apps}

Adobe Experience Manager Apps biedt de mogelijkheid om de inhoud van uw toepassing via de lucht (OTA) bij te werken. De bijgewerkte inhoud wordt opgeslagen in de publicatieinstantie. Om de toepassing op uw apparaat toe te staan verbinding te maken met de publicatie-instantie en te controleren op updates, moet de publicatie-instantie worden geconfigureerd om een lege verwijzingskoptekst toe te staan.

## Leeg verwijzingskoptekst configureren {#configuring-empty-referrer-header}

Om de dienst van het verwijzingsfilter te vormen:

* Open de Apache Felix-console (**Configuraties**) om:
* https://&lt;server>:&lt;port_number>/system/console/configMgr
* Aanmelden als beheerder.
* In de **Configuraties** -menu, selecteert u: *Filter Apache Sling Referrer*
* Schakel het veld Lege toestaan in om lege/ontbrekende verwijzingskoppen toe te staan.
* Klikken **Opslaan** om uw wijzigingen op te slaan.

![chlimage_1-58](assets/chlimage_1-58a.png)

Zie de [OSGI-configuratie-instellingen](/help/sites-deploying/osgi-configuration-settings.md) en [Beveiligingscontrolelijst - Problemen met de XSS-functie voor aanvragen voor andere sites](/help/sites-administering/security-checklist.md#protect-against-cross-site-request-forgery) voor nadere bijzonderheden.
