---
title: Functies van Enablement configureren
seo-title: Configuring Enablement Features
description: Functies voor activering configureren in Gemeenschappen
seo-description: Configure enablement features in Communities
uuid: 27be3128-1a7d-412e-99a9-6e3b3b0aec1c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 765a3d9b-4552-403e-872c-fdf684ac271d
role: Admin
exl-id: b635e2ed-4637-4b2f-a746-ec8dc7541bab
source-git-commit: 603518dbe3d842a08900ac40651919c55392b573
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# Functies van Enablement configureren {#configuring-enablement-features}

## Overzicht {#overview}

De functies voor activering bieden de mogelijkheid om [gemeenschappen](overview.md#enablement-community).

* Deze functie vereist extra licenties voor gebruik in een productieomgeving.

Het gebruik van de functies voor activering vereist het volgende:

Installatie van:

* **SCORM**

   SCORM (Sharable Content Object Reference Model) is een verzameling standaarden en specificaties voor e-learning. SCORM definieert ook hoe inhoud kan worden verpakt in een overdraagbaar ZIP-bestand.

* **MySQL**

   MySQL is een relationele database die voornamelijk wordt gebruikt voor het bijhouden en rapporteren van SCORM-gegevens voor Enablement en voor tabellen voor het bijhouden van videovoortgang. Voor het SCORM for enablement-functiepakket is het MySQL JDBC-stuurprogramma vereist.

* **FFmpeg**

   mpeg is een oplossing voor het converteren en streamen van audio en video en wordt, indien geïnstalleerd, gebruikt voor de juiste transcodering van [Video-elementen](../../help/sites-authoring/default-components-foundation.md#video). Voor gemeenschappen van activering wordt deze methode in de auteursomgeving gebruikt om metagegevens voor geüploade bronnen op te halen en om een miniatuur te genereren die wordt weergegeven wanneer de bron wordt vermeld.

Instellen van:

* **Community-managers**

   Alleen leden van de `Community Enablement Managers` aan een gebruikersgroep kan de rol van `Community Site Enablement Manager`, waarvan de machtigingen het maken van inhoud, toewijzingen en lidbeheer in de publicatieomgeving kunnen omvatten.

Optionele configuratie van:

* **Adobe Analytics**

   De integratie met Adobe Analytics voegt uitvoerige rapporteringseigenschappen toe en steunt de Video Heartmaattoevoeging aan Analytics.

* **Dispatcher**

## Configuratiestappen {#configuration-steps}

Hieronder volgen de stappen die nodig zijn voor gemeenschappen die zich toeleggen op de opvang van vluchtelingen.

Elke stap verbindt met documentatie die de noodzakelijke details verstrekt.

**Op alle auteur-/publicatieinstanties:**

1. **[JDBC-stuurprogramma installeren voor MySQL](deploy-communities.md#jdbc-driver-for-mysql)**

   Webconsole gebruiken (bundels): *http://localhost:4502/system/console/bundles*

   Installeren *voor* SCORM-pakket installeren

1. **[SCORM-pakket installeren](deploy-communities.md#scorm-package)**


   Pakketbeheer gebruiken: *http://localhost:4502/crx/packmgr/*

**Op elke server:**

1. **[MySQL, MySQL Workbench installeren](mysql.md)**

1. **[MySQL-databases installeren](mysql.md#database-setup)**

   SQL-scripts uitvoeren die zijn gedownload van de auteur-instantie

   MySQL Workbench gebruiken

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

1. (*Optioneel*) **[Analyseservice configureren](analytics.md)**

   Hulpmiddelen, Plaatsing, de console van Cloud Services van het gebruik: *http://localhost:4502/etc/cloudservices/sitecatalyst.html*

1. **[MPEG configureren](ffmpeg.md#configure-ffmpeg-transcoding-service)**

   Workflow-/modelconsole gebruiken

1. **[Tunnelservice inschakelen](deploy-communities.md#tunnel-service-on-author)**

   Webconsole gebruiken (configMgr): *http://localhost:4502/system/console/configMgr*

1. **[Community-beheerders maken](users.md#creating-community-members)**

   Voor het auteursmilieu gebruik klassieke-UI de console van de Veiligheid: *http://localhost:4502/useradmin*

   Gebruiker(s) maken met pad = /home/users/community

   * Voeg leden toe aan de volgende groepen:

      * Community Enablement Managers
      * Administrateurs van Gemeenschappen

## Dispatcher {#dispatcher}

Wanneer de implementatie [AEM Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html), zodat de schakelfuncties naar behoren werken, `clientheader` en `filter` secties moeten worden gewijzigd. Zie [Dispatcher configureren voor Gemeenschappen](dispatcher.md#enablement).
