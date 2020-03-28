---
title: Functies van Enablement configureren
seo-title: Functies van Enablement configureren
description: Functies voor activering configureren in Gemeenschappen
seo-description: Functies voor activering configureren in Gemeenschappen
uuid: 27be3128-1a7d-412e-99a9-6e3b3b0aec1c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 765a3d9b-4552-403e-872c-fdf684ac271d
translation-type: tm+mt
source-git-commit: 0b25d956c19c5fc5d79f87b292a0c61a23e5d66a

---


# Functies van Enablement configureren {#configuring-enablement-features}

## Overzicht {#overview}

De enablement-functies bieden de mogelijkheid om [enablement-gemeenschappen](overview.md#enablement-community)te maken.

* Deze functie vereist extra licenties voor gebruik in een productieomgeving.

Het gebruik van de functies voor activering vereist het volgende:

Installatie van:

* **SCORM**

   SCORM (Sharable Content Object Reference Model) is een verzameling standaarden en specificaties voor e-learning. SCORM definieert ook hoe inhoud kan worden verpakt in een overdraagbaar ZIP-bestand.

* **MySQL**

   MySQL is een relationele database die voornamelijk wordt gebruikt voor het bijhouden en rapporteren van SCORM-gegevens voor Enablement en voor tabellen voor het bijhouden van videovoortgang. Voor het SCORM for enablement-functiepakket is het MySQL JDBC-stuurprogramma vereist.

* **FFmpeg**

   mpeg is een oplossing voor het converteren en streamen van audio en video en wordt, indien geïnstalleerd, gebruikt voor de juiste transcodering van [video-elementen](../../help/sites-authoring/default-components-foundation.md#video). Voor gemeenschappen van activering wordt deze methode in de auteursomgeving gebruikt om metagegevens voor geüploade bronnen op te halen en om een miniatuur te genereren die wordt weergegeven wanneer de bron wordt vermeld.

Instellen van:

* **Community-managers**

   Voor gemeenschappen van enablement, slechts kunnen de leden van de `Community Enablement Managers` gebruikersgroep de rol van worden toegewezen, `Community Site Enablement Manager`waarvan de toestemmingen inhoudsverwezenlijking, taken, en lidbeheer in het publicatiemilieu kunnen omvatten.

Optionele configuratie van:

* **Adobe Analytics**

   De integratie met de Analyse van Adobe voegt uitvoerige rapporteringseigenschappen toe en steunt de Video Heartmaattoevoeging aan Analytics.

* **Dispatcher**

## Configuratiestappen {#configuration-steps}

Hieronder volgen de stappen die nodig zijn voor gemeenschappen die zich toeleggen op de opvang van vluchtelingen.

Elke stap verbindt met documentatie die de noodzakelijke details verstrekt.

**Op alle auteur-/publicatieinstanties:**

1. **[JDBC-stuurprogramma installeren voor MySQL](deploy-communities.md#jdbc-driver-for-mysql)**

   Webconsole gebruiken (bundels): *http://localhost:4502/system/console/bundles* Installeren *voordat* SCORM-pakket wordt geïnstalleerd

1. **[SCORM-pakket](deploy-communities.md#scorm-package)**installeren Pakketbeheer gebruiken:*http://localhost:4502/crx/packmgr/*

**Op elke server:**

1. **[MySQL, MySQL Workbench installeren](mysql.md)**

1. **[MySQL-databases installeren](mysql.md#database-setup)**

   SQL-scripts uitvoeren die u hebt gedownload van de auteur instanceUse MySQL Workbench

**Op dezelfde serverhostingauteurinstantie:**

1. **[Mpeg installeren](ffmpeg.md)**

**Op alle auteur-/publicatieinstanties:**

1. **[JDBC-verbindingspool configureren](mysql.md#configure-jdbc-connections)**

   Webconsole gebruiken (configMgr): *http://localhost:4502/system/console/configMgr*

1. **[SCORM-motorservice configureren](mysql.md#aem-communities-scormengine-service)**

   Webconsole gebruiken (configMgr): *http://localhost:4502/system/console/configMgr*

1. **[CSRF-filters configureren](mysql.md#adobe-granite-csrf-filter)**

   Webconsole gebruiken (configMgr): *http://localhost:4502/system/console/configMgr*

**Instantie van auteur:**

1. (*Optioneel*) Analyseservice **[configureren](analytics.md)**

   Tools, implementatie en Cloud Services-console gebruiken: *http://localhost:4502/etc/cloudservices/sitecatalyst.html*

1. **[MPEG configureren](ffmpeg.md#configure-ffmpeg-transcoding-service)**

   Workflow-/modelconsole gebruiken

1. **[Tunnelservice inschakelen](deploy-communities.md#tunnel-service-on-author)**

   Webconsole gebruiken (configMgr): *http://localhost:4502/system/console/configMgr*

1. **[Community-beheerders maken](users.md#creating-community-members)**

   Voor het auteursmilieu gebruik klassieke-UI de console van de Veiligheid: *http://localhost:4502/useradmin* maken gebruiker(s) met pad = /home/users/community

   * Voeg leden toe aan de volgende groepen:

      * Community Enablement Managers
      * Administrateurs van Gemeenschappen

## Dispatcher {#dispatcher}

Wanneer de implementatie de [AEM Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html)bevat, moeten de functies voor activering `clientheader` en `filter` secties worden gewijzigd om ervoor te zorgen dat deze correct werken. Zie [Dispatcher configureren voor Gemeenschappen](dispatcher.md#enablement).
