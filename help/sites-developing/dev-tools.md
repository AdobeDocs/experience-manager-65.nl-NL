---
title: Ontwikkelingsinstrumenten
description: Voor het ontwikkelen van uw JCR-, Apache Sling- of Adobe Experience Manager-toepassingen zijn verschillende gereedschapssets beschikbaar.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
exl-id: 97310ed5-f8fb-416c-8a66-68f652abeaa0
solution: Experience Manager, Experience Manager Sites
feature: Developing,Developer Tools
role: Developer
source-git-commit: 305227eff3c0d6414a5ae74bcf3a74309dccdd13
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# Ontwikkelingsinstrumenten{#development-tools}

Voor het ontwikkelen van uw JCR-, Apache Sling- of Adobe Experience Manager-toepassingen (AEM) zijn de volgende gereedschapssets beschikbaar:

* één stel bestaande uit [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md) en WebDAV. CRXDE Lite is ingebed in CRX/AEM en laat u toe om standaardontwikkelingstaken in browser uit te voeren. Met CRXDE Lite kunt u bestanden (zoals .jsp en .java), mappen, sjablonen, componenten, dialoogvensters, knooppunten, eigenschappen en bundels maken en bewerken tijdens het aanmelden en integreren met SVN.

  CRXDE Lite wordt aanbevolen wanneer u geen directe toegang hebt tot de CRX/AEM-server, wanneer u een toepassing ontwikkelt door de componenten en Java™-bundels die buiten de box vallen uit te breiden of te wijzigen of wanneer u geen speciale foutopsporing, codevoltooiing en syntaxismarkering nodig hebt.

* één stel bestaande uit:
   * Een geïntegreerde ontwikkelomgeving. Bijvoorbeeld: [Eclipse](/help/sites-developing/howto-projects-eclipse.md) of [IntelliJ](/help/sites-developing/ht-intellij.md).
   * Een bouwstijlhulpmiddel. Bijvoorbeeld: [Apache Maven](/help/sites-developing/ht-projects-maven.md).
   * FileVault die is ontwikkeld door Adobe om een opslagplaats toe te wijzen aan een bestandssysteem, een versiecontrolesysteem. Bijvoorbeeld Subversion.
   * Een systeem voor foutopsporing. Bijvoorbeeld Jira.
   * Een centraal systeem voor afhankelijkheidsbeheer. Bijvoorbeeld Apache Archiva.
   * En een systeem voor automatisering. Bijvoorbeeld Apache Continuum.

  Met deze setup kunt u uw toepassing (inhoud, code, configuratie) volledig integreren in elke ontwikkelomgeving en elk ontwikkelingsproces. De koppeling tussen de verschillende elementen is de representatie van het bestandssysteem van de gegevensopslagruimte via FileVault, aangezien alle eerder genoemde ontwikkelingsprogramma&#39;s met bestanden kunnen werken.

## Uitbreidingen voor geïntegreerde ontwikkelomgevingen {#extensions-for-integrated-development-environments}

Adobe heeft de volgende extensies uitgebracht:

* [Extensie Eclipse AEM](/help/sites-developing/aem-eclipse.md)
* [Extensie AEM](/help/sites-developing/aem-brackets.md)

### Overige gereedschappen {#other-tools}

AEM schepen met andere instrumenten die de ontwikkeling bevorderen:

* [Dialoogeditor](/help/sites-developing/dialog-editor.md)
* [Woordenboeken beheren met Vertaler](/help/sites-developing/i18n-translator.md)
* [Pakketten beheren met Maven](/help/sites-developing/vlt-mavenplugin.md)
* [Hoe te om AEM Projecten te ontwikkelen gebruikend Eclipse](/help/sites-developing/howto-projects-eclipse.md)
* [Hoe te om AEM Projecten te bouwen gebruikend Apache Maven](/help/sites-developing/ht-projects-maven.md)
* [Hoe te om AEM Projecten te ontwikkelen gebruikend IntelliJ IDEA](/help/sites-developing/ht-intellij.md)
* [Het gereedschap VLT gebruiken](/help/sites-developing/ht-vlttool.md)
* [Het gereedschap Proxyserver gebruiken](/help/sites-developing/ht-proxy-server.md)
* [AEM-moderniseringstools](/help/sites-developing/modernization-tools.md)
* [Gereedschap AEM](/help/sites-developing/aem-repo-tool.md)

Instrumenten die het opzetten van nieuwe projecten vergemakkelijken:

* [Projectarchetype AEM](https://github.com/adobe/aem-project-archetype)
* [AEM Lazybones-sjablonen](https://github.com/Adobe-Consulting-Services/lazybones-aem-templates)

>[!NOTE]
>
>De volgende zelfstudie kan van belang zijn voor het starten van een nieuw AEM-project:
>[Aan de slag met AEM Sites Deel 1 - Projectinstelling](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-wknd-tutorial-develop/part1.html)
