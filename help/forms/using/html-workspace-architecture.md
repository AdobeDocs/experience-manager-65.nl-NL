---
title: AEM Forms Workspace Architecture
description: Conceptuele informatie en overzicht van de architectuur van de werkruimte van LiveCycle AEM Forms.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: c6f216d4-781c-4356-b9f0-3324903a28e7
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---

# AEM Forms Workspace Architecture {#aem-forms-workspace-architecture}

De AEM Forms-werkruimte is een webtoepassing die wordt gehost op CRX™. Wanneer de werkruimte in browser wordt geopend, wordt een middel CRX betreden, en de toepassing wordt teruggegeven als pagina van de HTML in browser.

De toepassing benadert de AEM Forms-server op REST-eindpunten voor het volgende:

* Gebruikerstaken ophalen, beginpunten van processen, procesgeschiedenis en gebruikersgegevens
* Handeling uitvoeren op taken
* Query uitvoeren in database
* Gebruikersvoorkeuren en meer bijwerken

De AEM Forms-server heeft via JDBC toegang tot de AEM Forms-database. De database bestaat uit taken, processen en instanties, gebruikers en gerelateerde informatie.

De AEM Forms-werkruimte is ontworpen voor modulaire JavaScript™-componenten die afzonderlijk kunnen worden aangepast en opnieuw kunnen worden gebruikt in andere webtoepassingen. De componenten zijn gebaseerd op BackBone, een JavaScript-bibliotheek die structuur geeft aan webtoepassingen. Een gedetailleerd artikel waarin de interactie van componenten met BackBone wordt beschreven is [hier](/help/forms/using/backbone-interaction.md). De organisatie van componenten in de CRX omslagstructuur wordt besproken in [dit](/help/forms/using/folder-structure.md) artikel.

Pakketten geleverd voor de AEM Forms-werkruimte:

* `adobe-lc-workspace-pkg-<version>.zip`: Het is CRX-pakket, dat wil zeggen dat het kan worden geïmplementeerd in CRX met behulp van Package Manager.
* `adobe-lc-workspace-<version>-src.zip`: Het is een archief dat volledige code van de werkruimte en de manuscripten van AEM Forms bevat om opstellen pakketten-verschepen, zuivert, en Dev pakketten.
