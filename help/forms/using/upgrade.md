---
title: Upgrade naar AEM 6,5 Forms
description: U kunt een directe upgrade uitvoeren van AEM 6.3 Forms en AEM 6.4 Forms naar AEM 6.5 Forms.
content-type: reference
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
docset: aem65
role: Admin,User
exl-id: 2fc8abec-8ba6-40b7-bbb1-4288eeea7c86
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,AEM Forms Upgrade
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 1%

---

# Upgrade naar AEM 6,5 Forms {#upgrade-to-aem-forms}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/setup-configure-migrate/migrate-to-forms-as-a-cloud-service.html) |
| AEM 6,5 | Dit artikel |


AEM 6.5 Forms bevat verschillende nieuwe functies en verbeteringen die het maken, beheren en gebruiken van formulieren en correspondentie stroomlijnen. Om over alle nieuwe mogelijkheden en verhogingen van AEM 6.5 Forms te leren, zie [ Nieuw document van eigenschappen ](../../forms/using/whats-new.md).

U kunt uw bestaande LiveCycle- of AEM Forms-installatie upgraden om nieuwe mogelijkheden en verbeteringen te verkrijgen die worden aangeboden in AEM 6.5 Forms, terwijl de bestaande gegevens, processen en middelen intact blijven. Bij een upgrade blijven de metagegevens en de status van de processen ook behouden. U kunt een upgradepad kiezen om aan de slag te gaan met de upgrade.

Het volgende diagram toont de beschikbare verbeteringspaden voor AEM Forms op OSGi:

![ OSGi verbeteringsstroom ](do-not-localize/osgi-upgrade-path.png)

U kunt een directe upgrade uitvoeren vanaf:

* AEM 6.3 Forms over OSGi
* AEM 6.4 Forms over OSGi

U kunt een multi-hopverbetering van ook uitvoeren

* AEM 6,0 Forms op OSGi
* AEM 6.1 Forms over OSGi
* AEM 6.2 Forms over OSGi

In het volgende diagram worden de beschikbare upgradepaden voor AEM Forms op JEE weergegeven:

![ JEE verbetering 6.5 ](do-not-localize/jee-upgrade-6-5.png)


U kunt een directe upgrade uitvoeren vanaf:

* AEM 6.3 Forms in juni
* AEM 6.4 Forms in juni
* AEM 6.5.x.x Forms op JEE

U kunt een multi-hopverbetering van ook uitvoeren

* LiveCycle ES4 SP1
* AEM 6,0 Forms in juni
* AEM 6.1 Forms in juni
* AEM 6.2 Forms in juni

AEM 6.5.18.0 Forms op JEE verstrekt twee soorten installateurs: [ Volledige installateur ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html) en [ installateur van het Fatch ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html).

**Volledige installateur**: U kunt volledige installateur gebruiken om nieuwe instanties van AEM Forms op te zetten of verbeteringen van AEM 6.5.x.x Forms op JEE aan AEM 6.5.18.0 Forms op JEE uit te voeren.

**installateur van het Patch**: Het installatieprogramma van het Patch is voor klanten reeds gebruikend AEM versies 6.5.x.x. U kunt het installatieprogramma van de patch gebruiken om een upgrade uit te voeren naar de nieuwste versie van AEM Forms.

In de volgende afbeelding ziet u scenario&#39;s voor het gebruik van het volledige installatieprogramma en het patchinstallatieprogramma.

![ Volledige Installateur en de Installateur van het Patch ](/help/forms/using/assets/full-and-patch-installer.png)

Verwijs naar [ AEM 6.5 Forms Service Pack installatie instructies ](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/aem-forms-current-service-pack-installation-instructions.html) artikel om het recentste Service Pack voor milieu te installeren JEE.

<!--
[Work in Progress]

Migration involves moving only assets (PDF, XDP, images, adaptive forms, correspondence management assets) from one server to another - processes (LCA), settings, configurations, and a few other pieces of metadata are not migrated. Perform the following steps to migrate to AEM 6.3 Forms:

1. Set up a fresh environment of [AEM 6.3 Forms](https://adobe.com/go/learn_aemforms_documentation_63).
1. Move XDP or other compatible assets to the freshly set instance. For detailed instructions, see [Importing and exporting assets to AEM Forms](../../forms/using/import-export-forms-templates.md). [
   ](../../forms/using/import-export-forms-templates.md)
1. Build the required services, if any.

   For example, if you are using AEM Forms on JEE Document Services, changes are required in the code to use document services available in AEM Forms on OSGi.

1. Perform post-installation activities:

    * **Run Migration Utility**

      The migration utility makes the adaptive forms and correspondence management assets of earlier versions compatible with AEM 6.3 forms. You can download the utility from AEM Software Distribution. For step-by-step information to configure and use the migration utility, see [migration utility](../../forms/using/migration-utility.md) documentation.

    * **Reconfigure Adobe Sign**

      If you had Adobe Sign configured in the previous version of AEM Forms, then reconfigure Adobe Sign from AEM Cloud services. For more details, see [Integrate Adobe Sign with AEM Forms](../../forms/using/adobe-sign-integration-adaptive-forms.md).

      Moreover, AEM 6.3 Forms release has introduced many new Adobe Sign features. For step-by-step information to use Adobe Sign, see [Using Adobe Sign in an adaptive form](../../forms/using/working-with-adobe-sign.md).

    * **Reconfigure analytics and reports**

      In AEM 6.3 Forms, traffic variable for source and success event for impression are not available. So, when you upgrade to AEM 6.3 Forms, AEM Forms stops sending data to Adobe Analytics server and analytics reports for adaptive forms are not available. Moreover, AEM 6.3 Forms introduces traffic variable for the version of form analytics and success event for the amount of time spent on a field. So, reconfigure analytics and reports for your AEM Forms environment. For detailed steps, see [Configuring analytics and reports](../../forms/using/configure-analytics-forms-documents.md).

      Methods to calculate average fill time for forms and average read time for have changed. So, when you upgrade to AEM 6.3 forms, older data (data from previous AEM Forms release) for these metrics is available only in Adobe Analytics. It is not visible in AEM Forms analytics reports. For these metrics, AEM Forms analytics reports display data which is captured after performing the upgrade.
      
      -->


