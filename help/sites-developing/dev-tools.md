---
title: Ontwikkelingsinstrumenten
seo-title: Development Tools
description: Voor het ontwikkelen van uw JCR-, Apache Sling- of AEM-toepassingen zijn een aantal gereedschapssets beschikbaar
seo-description: To develop your JCR, Apache Sling or AEM applications, a number of tool sets are available
uuid: 1bee3a52-5d76-4b0c-a222-a02e12ff3a43
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: 76c570e5-46ed-46be-9864-4fe4a83f0caf
exl-id: 97310ed5-f8fb-416c-8a66-68f652abeaa0
source-git-commit: 4967a6d9ad92272a1ff442456fe65de51cc46a73
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# Ontwikkelingsinstrumenten{#development-tools}

Voor het ontwikkelen van uw JCR-, Apache Sling- of AEM-toepassingen zijn de volgende gereedschapssets beschikbaar:

* één stel bestaande uit [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md) en WebDAV. CRXDE Lite is ingebed in CRX/AEM en laat u toe om standaardontwikkelingstaken in browser uit te voeren. Met CRXDE Lite kunt u bestanden (zoals .jsp en .java), mappen, sjablonen, componenten, dialoogvensters, knooppunten, eigenschappen en bundels maken en bewerken terwijl u zich aanmeldt en integreert met SVN.

   CRXDE Lite wordt aanbevolen wanneer u geen directe toegang hebt tot de CRX/AEM-server, wanneer u een toepassing ontwikkelt door de out-of-the-box componenten en Java-bundels uit te breiden of te wijzigen of wanneer u geen speciale debugger, codevoltooiing en syntaxismarkering nodig hebt.

* een reeks bestaande uit een geïntegreerde ontwikkelomgeving (bijvoorbeeld: [Eclipse](/help/sites-developing/howto-projects-eclipse.md) of [IntelliJ](/help/sites-developing/ht-intellij.md)), een bouwstijlhulpmiddel (bijvoorbeeld: [Apache Maven](/help/sites-developing/ht-projects-maven.md)), FileVault die door Adobe is ontwikkeld om een opslagplaats toe te wijzen aan een bestandssysteem, een versiecontrolesysteem (bijvoorbeeld: Subversion), een systeem van de insectencontrole (bijvoorbeeld: Jira), een centraal systeem voor afhankelijkheidsbeheer (bijvoorbeeld: Apache Archiva) en een automatiseringssysteem voor build (bijvoorbeeld: Apache Continuum).

   Met deze installatie kunt u uw toepassing (inhoud, code, configuratie) volledig integreren in elke ontwikkelomgeving en elk proces. De koppeling tussen de verschillende elementen is de bestandssysteemweergave van de opslagplaats via FileVault, aangezien alle bovengenoemde ontwikkelingsprogramma&#39;s met bestanden kunnen werken.

## Uitbreidingen voor geïntegreerde ontwikkelomgevingen {#extensions-for-integrated-development-environments}

Adobe heeft de volgende extensies uitgebracht:

* [Extensie Eclipse AEM](/help/sites-developing/aem-eclipse.md)
* [Extensie AEM](/help/sites-developing/aem-brackets.md)

### Overige gereedschappen {#other-tools}

AEM schepen met andere instrumenten die de ontwikkeling bevorderen:

* [Dialoogvenster-editor](/help/sites-developing/dialog-editor.md)
* [Woordenboeken beheren met Vertaler](/help/sites-developing/i18n-translator.md)
* [Pakketten beheren met Maven](/help/sites-developing/vlt-mavenplugin.md)
* [Hoe te om AEM Projecten te ontwikkelen gebruikend Eclipse](/help/sites-developing/howto-projects-eclipse.md)
* [Hoe te om AEM Projecten te bouwen gebruikend Apache Maven](/help/sites-developing/ht-projects-maven.md)
* [Hoe te om AEM Projecten te ontwikkelen gebruikend IntelliJ IDEA](/help/sites-developing/ht-intellij.md)
* [Het gereedschap VLT gebruiken](/help/sites-developing/ht-vlttool.md)
* [Het gereedschap Proxyserver gebruiken](/help/sites-developing/ht-proxy-server.md)
* [AEM-moderniseringstools](/help/sites-developing/modernization-tools.md)
* [AEM](/help/sites-developing/aem-repo-tool.md)

Instrumenten die het opzetten van nieuwe projecten vergemakkelijken:

* [Projectarchetype AEM](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype)
* [AEM Lazybones-sjablonen](https://github.com/Adobe-Consulting-Services/lazybones-aem-templates)

>[!NOTE]
>
>De volgende zelfstudie kan van belang zijn voor het starten van een nieuw AEM-project:
>[Aan de slag met AEM Sites Deel 1 - Projectinstelling](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-wknd-tutorial-develop/part1.html)
