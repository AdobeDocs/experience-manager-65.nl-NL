---
title: Configureren voor AEM-toepassingen
seo-title: Configureren voor AEM-toepassingen
description: Leer hoe u AEM-apps configureert.
seo-description: Leer hoe u AEM-apps configureert.
uuid: ab9acd93-da7f-4bb7-8d26-224044899068
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: 34f24837-f5e2-41f0-a359-fdb695e1b8f2
translation-type: tm+mt
source-git-commit: 684d2d5f73d571a15c8155e7870134c28dc892b7

---


# Configureren voor AEM-toepassingen{#configuring-for-aem-apps}

Met Adobe Experience Manager Apps kunt u de inhoud van uw toepassing via de lucht (OTA) bijwerken. De bijgewerkte inhoud wordt opgeslagen in de publicatieinstantie. Om de toepassing op uw apparaat toe te staan verbinding te maken met de publicatie-instantie en te controleren op updates, moet de publicatie-instantie worden geconfigureerd om een lege verwijzingskoptekst toe te staan.

## Leeg verwijzingskoptekst configureren {#configuring-empty-referrer-header}

Om de dienst van het verwijzingsfilter te vormen:

* Open de Apache Felix-console (**Configurations**) op:
* https://&lt;server>:&lt;port_number>/system/console/configMgr
* Aanmelden als beheerder.
* Selecteer in het menu **Configuraties** : Filter *Apache-schuifverwijzing*
* Schakel het veld Lege toestaan in om lege/ontbrekende verwijzingskoppen toe te staan.
* Klik op **Opslaan** om de wijzigingen op te slaan.

![chlimage_1-58](assets/chlimage_1-58a.png)

Zie de de Montages [van de Configuratie](/help/sites-deploying/osgi-configuration-settings.md) OSGI en Controlelijst van de [Veiligheid - Kwesties met de Vervalsing](/help/sites-administering/security-checklist.md#protect-against-cross-site-request-forgery) van het Verzoek van de Verkeer van de Plaats voor verdere details.
