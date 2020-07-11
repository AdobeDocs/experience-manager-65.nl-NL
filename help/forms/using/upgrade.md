---
title: Upgrade naar AEM 6.5-formulieren
seo-title: Upgrade naar AEM 6.5-formulieren
description: U kunt een directe upgrade uitvoeren van AEM 6.3 Forms en AEM 6.4 Forms naar AEM 6.5 Forms.
seo-description: U kunt een directe upgrade uitvoeren van AEM 6.3 Forms en AEM 6.4 Forms naar AEM 6.5 Forms.
uuid: 7a38cd72-2d01-4af7-b6a3-00dc34c4f02b
content-type: reference
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: f89921ef-c638-4a07-88d5-3dd8614c5166
docset: aem65
translation-type: tm+mt
source-git-commit: 1dfc8fa91d3e5ae8ca49cf1f3cb739b59feb18cf
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---


# Upgrade naar AEM 6.5-formulieren{#upgrade-to-aem-forms}

AEM 6.5 Forms bevat verschillende nieuwe functies en verbeteringen die het maken, beheren en gebruiken van formulieren en correspondentie stroomlijnen. Voor meer informatie over alle nieuwe mogelijkheden en verbeteringen van AEM 6.5 Forms raadpleegt u het overzichtsdocument [](../../forms/using/whats-new.md)Nieuwe functies.

U kunt een upgrade uitvoeren op uw bestaande installatie van LiveCycle of AEM Forms om nieuwe mogelijkheden en verbeteringen te verkrijgen die in AEM 6.5 Forms worden aangeboden, terwijl de bestaande gegevens, processen en middelen intact blijven. Bij een upgrade blijven de metagegevens en de status van de processen ook behouden. U kunt een upgradepad kiezen om aan de slag te gaan met de upgrade.

Het volgende diagram toont de beschikbare verbeteringswegen voor AEM Forms op OSGi:

![](do-not-localize/osgi-upgrade-path.png)

U kunt een directe upgrade uitvoeren vanaf:

* AEM 6.3 Formulieren op OSGi
* AEM 6.4 Formulieren op OSGi

U kunt een multi-hopverbetering van ook uitvoeren

* AEM 6.0-formulieren op OSGi
* AEM 6.1 Formulieren op OSGi
* AEM 6.2 Formulieren op OSGi

In het volgende diagram worden de beschikbare upgradepaden voor AEM Forms op JEE weergegeven:

![](do-not-localize/jee-upgrade-6-5.png)

U kunt een directe upgrade uitvoeren vanaf:

* AEM 6.3 Formulieren in JEE
* AEM 6.4-formulieren in JEE

U kunt een multi-hopverbetering van ook uitvoeren

* LiveCycle ES2
* LiveCycle ES3
* LiveCycle ES4 SP1
* AEM 6.0-formulieren in JEE
* AEM 6.1 Formulieren in JEE
* AEM 6.2-formulieren in JEE

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
