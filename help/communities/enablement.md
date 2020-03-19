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
source-git-commit: d6c8bbb9aa763a2eb6660b6b6755aba75241e394

---


# Functies van Enablement configureren {#configuring-enablement-features}

## Overzicht {#overview}

De enablement-functies bieden de mogelijkheid om [enablement-gemeenschappen](overview.md#enablement-community)te maken.

* Deze functie vereist extra licenties voor gebruik in een productieomgeving.

Het gebruik van de functies voor activering vereist het volgende:

Installatie van:

* **SCORM** Sharable Content Object Reference Model (SCORM) is een verzameling standaarden en specificaties voor e-learning. SCORM definieert ook hoe inhoud kan worden verpakt in een overdraagbaar ZIP-bestand.

* **MySQL** MySQL is een relationele database die voornamelijk wordt gebruikt voor het bijhouden en rapporteren van SCORM-gegevens voor Enablement en voor tabellen voor het bijhouden van videovoortgang. Voor het SCORM for enablement-functiepakket is het MySQL JDBC-stuurprogramma vereist.

* **mpeg** FFmpeg is een oplossing voor het converteren en streamen van audio en video en wordt, indien geïnstalleerd, gebruikt voor een correcte transcodering van [Video-elementen](../../help/sites-authoring/default-components-foundation.md#video). Voor gemeenschappen van activering wordt deze methode in de auteursomgeving gebruikt om metagegevens voor geüploade bronnen op te halen en om een miniatuur te genereren die wordt weergegeven wanneer de bron wordt vermeld.

Instellen van:

* **Community Managers** For enablement community, only members of the `Community Enablement Managers` user group may be assigned the role of `Community Site Enablement Manager`, which permissions may include content creation, toewijzingen, and member management in the publish environment.

Optionele configuratie van:

* **Adobe Analytics** Integration with Adobe Analytics voegt uitgebreide rapportfuncties toe en ondersteunt de toevoeging Video Heartbeat aan Analytics.

* **Dispatcher**

## Configuratiestappen {#configuration-steps}

Hieronder volgen de stappen die nodig zijn voor gemeenschappen die zich toeleggen op de opvang van vluchtelingen.

Elke stap verbindt met documentatie die de noodzakelijke details verstrekt.

**Op alle auteur-/publicatieinstanties:**

1. **[Installeer het JDBC-stuurprogramma voor MySQL](deploy-communities.md#jdbc-driver-for-mysql)**Use Web Console (bundels):*http://localhost:4502/system/console/bundles*Installeren *voordat*SCORM-pakket wordt geïnstalleerd

1. **[SCORM-pakket](deploy-communities.md#scorm-package)**installeren Pakketbeheer gebruiken:*http://localhost:4502/crx/packmgr/*

**Op elke server:**

1. **[MySQL, MySQL Workbench installeren](mysql.md)**

1. **[MySQL-databases installeren](mysql.md#database-setup)**SQL-scripts uitvoeren die zijn gedownload van de auteur instanceUse MySQL Workbench

**Op dezelfde serverhostingauteurinstantie:**

1. **[Mpeg installeren](ffmpeg.md)**

**Op alle auteur-/publicatieinstanties:**

1. **[Configureer de JDBC-verbindingspool](mysql.md#configure-jdbc-connections)**Webconsole (configMgr):*http://localhost:4502/system/console/configMgr*

1. **[Configureer de SCORM-motorservice](mysql.md#aem-communities-scormengine-service)**Webconsole gebruiken (configMgr):*http://localhost:4502/system/console/configMgr*

1. **[Configureer CSRF-filters](mysql.md#adobe-granite-csrf-filter)**Webconsole gebruiken (configMgr):*http://localhost:4502/system/console/configMgr*

**Instantie van auteur:**

1. (*Optioneel*) **[Configureer Hulpprogramma&#39;s, Implementatie en Cloud Services-console voor Analytics-service](analytics.md)**:*http://localhost:4502/etc/cloudservices/sitecatalyst.html*

1. **[MPEG](ffmpeg.md#configure-ffmpeg-transcoding-service)**Use Workflow/Models-console configureren

1. **[De Console van het](deploy-communities.md#tunnel-service-on-author)**Gebruik van het Gebruik van de Dienst van de Tunnel (configMgr) toelaten:*http://localhost:4502/system/console/configMgr*

1. **[Communautaire beheerders](users.md#creating-community-members)**maken voor de auteursomgeving: gebruik de klassieke UI-beveiligingsconsole:*http://localhost:4502/useradmin*maken gebruiker(s) met pad = /home/users/community

   * Voeg leden toe aan de volgende groepen:

      * Community Enablement Managers
      * Administrateurs van Gemeenschappen

## Dispatcher {#dispatcher}

Wanneer de implementatie de [AEM Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html)bevat, moeten de functies voor activering `clientheader` en `filter` secties worden gewijzigd om ervoor te zorgen dat deze correct werken. Zie [Dispatcher configureren voor Gemeenschappen](dispatcher.md#enablement).
