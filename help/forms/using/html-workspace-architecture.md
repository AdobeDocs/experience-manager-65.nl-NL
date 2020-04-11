---
title: AEM Forms Workspace Architecture
seo-title: AEM Forms Workspace Architecture
description: Conceptuele informatie en overzicht van de architectuur van de werkruimte van LiveCycle AEM-formulieren.
seo-description: Conceptuele informatie en overzicht van de architectuur van de werkruimte van LiveCycle AEM-formulieren.
uuid: e1a48452-ed44-4ea7-ba38-d961c8faafa5
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: c3a312fb-f684-477d-916d-2d3c99aa7607
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317

---


# AEM Forms Workspace Architecture {#aem-forms-workspace-architecture}

De werkruimte van AEM-formulieren is een webtoepassing die wordt gehost op CRX™. Wanneer de werkruimte in browser wordt geopend, wordt een middel van CRX betreden, en de toepassing wordt teruggegeven als HTML- pagina in browser.

De toepassing opent AEM Forms-server op REST-eindpunten en doet het volgende:

* Gebruikerstaken ophalen, beginpunten van processen, procesgeschiedenis en gebruikersgegevens
* Handeling uitvoeren op taken
* Query uitvoeren in database
* Gebruikersvoorkeuren en meer bijwerken

De AEM Forms-server heeft via JDBC toegang tot de AEM Forms-database. De database bestaat uit taken, processen en instanties, gebruikers en gerelateerde informatie.

De werkruimte AEM Forms is ontworpen voor modulaire JavaScript™-componenten die afzonderlijk kunnen worden aangepast en opnieuw kunnen worden gebruikt in andere webtoepassingen. De componenten zijn gebaseerd op BackBone, een JavaScript-bibliotheek die structuur geeft aan webtoepassingen. Een gedetailleerd artikel dat interactie van componenten met BackBone beschrijft is [hier](/help/forms/using/backbone-interaction.md). De organisatie van componenten in de CRX omslagstructuur wordt besproken in [dit](/help/forms/using/folder-structure.md) artikel.

Pakketten geleverd voor de werkruimte van AEM-formulieren:

* `adobe-lc-workspace-pkg-<version>.zip`: Het is CRX pakket, dat wil zeggen, het kan in CRX worden opgesteld gebruikend de Manager van het Pakket.
* `adobe-lc-workspace-<version>-src.zip`: Het is een archief dat volledige code van de werkruimte en de manuscripten van Vormen AEM bevat om opstellen pakketten-verschepen, zuivert, en Dev pakketten.
