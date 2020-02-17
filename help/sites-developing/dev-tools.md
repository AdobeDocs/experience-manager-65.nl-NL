---
title: Ontwikkelingsinstrumenten
seo-title: Ontwikkelingsinstrumenten
description: Voor het ontwikkelen van JCR-, Apache Sling- of AEM-toepassingen zijn een aantal gereedschapssets beschikbaar
seo-description: Voor het ontwikkelen van JCR-, Apache Sling- of AEM-toepassingen zijn een aantal gereedschapssets beschikbaar
uuid: 1bee3a52-5d76-4b0c-a222-a02e12ff3a43
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: 76c570e5-46ed-46be-9864-4fe4a83f0caf
translation-type: tm+mt
source-git-commit: c13eabdf4938a47ddf64d55b00f845199591b835

---


# Ontwikkelingsinstrumenten{#development-tools}

Voor het ontwikkelen van uw JCR-, Apache Sling- of AEM-toepassingen zijn de volgende gereedschapssets beschikbaar:

* één set bestaande uit [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md) en WebDAV. CRXDE Lite is ingebed in CRX/AEM en laat u toe om standaardontwikkelingstaken in browser uit te voeren. Met CRXDE Lite, kunt u dossiers (zoals .jsp en .java), omslagen, malplaatjes, componenten, dialogen, knopen, eigenschappen en bundels creëren en uitgeven terwijl het registreren en het integreren met SVN.

   CRXDE Lite wordt geadviseerd wanneer u geen directe toegang tot de server CRX/AEM hebt, wanneer u een toepassing door uit-van-de-doos componenten en de bundels van Java uit te breiden of te wijzigen of wanneer u geen specifieke debugger, codevoltooiing en syntaxismarkering nodig hebt.

* een reeks bestaande uit een geïntegreerde ontwikkelomgeving (bijvoorbeeld: [Eclipse](/help/sites-developing/howto-projects-eclipse.md) of [IntelliJ](/help/sites-developing/ht-intellij.md)), een bouwstijlhulpmiddel (bijvoorbeeld: [Apache Maven](/help/sites-developing/ht-projects-maven.md)), FileVault die door Adobe is ontwikkeld om een opslagplaats toe te wijzen aan een bestandssysteem, een versiecontrolesysteem (bijvoorbeeld: Subversion), een systeem van de insectencontrole (bijvoorbeeld: Jira), een centraal systeem voor afhankelijkheidsbeheer (bijvoorbeeld: Apache Archiva) en een automatiseringssysteem voor build (bijvoorbeeld: Apache Continuum).

   Met deze installatie kunt u uw toepassing (inhoud, code, configuratie) volledig integreren in elke ontwikkelomgeving en elk proces. De koppeling tussen de verschillende elementen is de bestandssysteemweergave van de opslagplaats via FileVault, aangezien alle bovengenoemde ontwikkelingsprogramma&#39;s met bestanden kunnen werken.

## Uitbreidingen voor geïntegreerde ontwikkelomgevingen {#extensions-for-integrated-development-environments}

Adobe heeft de volgende extensies uitgebracht:

* [AEM Eclipse-extensie](/help/sites-developing/aem-eclipse.md)
* [AEM Brackets Extension](/help/sites-developing/aem-brackets.md)
* [AEM IntelliJ Extension](https://github.com/headwirecom/aem-ide-tooling-4-intellij/blob/master/documenation/AEM%20Tooling%20Plugin%20for%20IntelliJ%20IDEA.pdf) (van headwire)

### Overige gereedschappen {#other-tools}

AEM wordt geleverd met andere instrumenten die de ontwikkeling bevorderen:

* [Dialoogvenster-editor](/help/sites-developing/dialog-editor.md)
* [Woordenboeken beheren met Vertaler](/help/sites-developing/i18n-translator.md)
* [Pakketten beheren met Maven](/help/sites-developing/vlt-mavenplugin.md)
* [AEM-projecten ontwikkelen met Eclipse](/help/sites-developing/howto-projects-eclipse.md)
* [AEM-projecten bouwen met Apache Maven](/help/sites-developing/ht-projects-maven.md)
* [AEM-projecten ontwikkelen met behulp van IntelliJ IDEA](/help/sites-developing/ht-intellij.md)
* [Het gereedschap VLT gebruiken](/help/sites-developing/ht-vlttool.md)
* [Het gereedschap Proxyserver gebruiken](/help/sites-developing/ht-proxy-server.md)
* [Dialoogvenster omzetten](/help/sites-developing/dialog-conversion.md)
* [AEM-repo](/help/sites-developing/aem-repo-tool.md)

Instrumenten die het opzetten van nieuwe projecten vergemakkelijken:

* [AEM-projectarchetype](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype)
* [AEM Lazybones sjablonen](https://github.com/Adobe-Consulting-Services/lazybones-aem-templates)

>[!NOTE]
>
>De volgende zelfstudie kan van belang zijn voor het starten van een nieuw AEM-project:
>[Aan de slag met deel 1 van de Plaatsen AEM - de Opstelling van het Project](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-wknd-tutorial-develop/part1.html)

