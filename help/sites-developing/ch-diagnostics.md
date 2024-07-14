---
title: ContextHub Diagnostics
description: ContextHub verstrekt een diagnostische pagina waar u een overzicht van het kader ContextHub kunt zien
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
exl-id: b833c28b-76c6-42a2-b690-3e81ddf91bc2
solution: Experience Manager, Experience Manager Sites
feature: Developing,Personalization
role: Developer
source-git-commit: 305227eff3c0d6414a5ae74bcf3a74309dccdd13
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# ContextHub Diagnostics {#contexthub-diagnostics}

ContextHub verstrekt een diagnostische pagina waar u een overzicht van het kader kunt zien ContextHub. Als u de pagina wilt openen, gaat u bijvoorbeeld naar de pagina `contexthub.diagnostics.html` van de AEM auteur-instantie:

`http://<host>:<port>/conf/<tenant>/settings/cloudsettings/default/contexthub.diagnostics.html`

De pagina van de Diagnostiek ContextHub verstrekt informatie over de opslag en modules UI die zijn gecreeerd, de omslagen van de cliëntbibliotheek die, en verbindingen aan nuttige pagina&#39;s worden geladen.

>[!NOTE]
>
>De foutopsporingsmodus moet zijn ingeschakeld om diagnostische gegevens te kunnen retourneren. Als dit niet het geval is, is de pagina Diagnostics leeg. Zie [ dit document ](ch-configuring.md#debugging-contexthub) voor details op hoe te om toe te laten zuiveren wijze.

>[!NOTE]
>
>Voor configuraties ContextHub die nog onder hun erfeniswegen worden gevestigd, is de plaats van de diagnostische pagina `http://<host>:<port>/libs/settings/cloudsettings/legacy/contexthub.diagnostics.html`.

## Winkels {#stores}

De sectie van Sporen maakt een lijst van alle opslag ContextHub die zijn gevormd. Elk item in de lijst bestaat uit de volgende informatie:

* **Titel:** het [ opslagtype ](/help/sites-developing/ch-samplestores.md) dat de opslag op gebaseerd is.
* **weg:** de weg aan de opslagplaats knoop die de configuratie houdt.
* **resourceType:** de weg van de bewaargegevensknoop waar het opslagtype wordt bepaald.
* **clientlibs:** De categorieën van de cliëntbibliotheken die worden geladen die het archieftype uitvoeren.

## Modules {#modules}

De sectie van Modules maakt een lijst van alle modules ContextHub UI die zijn gevormd. Elk item in de lijst bestaat uit de volgende informatie:

* **Titel:** het [ type van Module UI ](/help/sites-developing/ch-samplemodules.md) dat de module UI gebaseerd is op.
* **weg:** de weg aan de opslagplaats knoop die de configuratie houdt.
* **resourceType:** de weg van de opslagplaats knoop waar het UI moduletype wordt bepaald.
* **clientlibs:** De categorieën van de cliëntbibliotheken die worden geladen die het UI moduletype uitvoeren.

## Clientlibs {#clientlibs}

De sectie Clientlibs maakt een lijst van alle omslagen van de cliëntbibliotheek die ContextHub heeft geladen. De clientbibliotheken zijn gecategoriseerd:

* **kernel.js:** de bibliotheken van de Cliënt die het kader ContextHub, de segmentmotor, en opslagtypes uitvoeren.
* **ui.js:** de bibliotheken van de Cliënt die ContextHub UI en UI moduletypes uitvoeren.
* **style.css:** CSS dossiers die van cliëntbibliotheken worden geladen.

## URL&#39;s {#urls}

De sectie URLs bevat verbindingen aan eigenschappen ContextHub:

* **redacteur van de Configuratie:** opent de [ pagina van de Configuratie ContextHub ](ch-configuring.md) waar u opslag, wijzen UI, en modules kunt vormen UI.

* **Configuratie van modules ContextHub:** opent het bestand /etc/cloudsettings/default/contexthub.config.kernel.js, dat de objecten van JavaScript vertegenwoordiging van de ContextHub opslagconfiguraties bevat.
* **Configuratie van ContextHub UI:** opent het /etc/cloudsettings/default/contexthub.config.ui.js- dossier, dat de objecten van JavaScript vertegenwoordiging van de ContextHub UI wijzeconfiguraties bevat.
* **kernel.js:** opent het /etc/cloudsettings/default/contexthub.kernel.js- dossier, dat de broncode van de cliëntbibliotheken bevat die het kader ContextHub, de segmentmotor, en opslagtypes uitvoeren.
* **ui.js:** opent het bestand /etc/cloudsettings/default/contexthub.ui.js, dat de broncode van de cliëntbibliotheken bevat die de ContextHub UI en UI moduletypes uitvoeren.
* **style.css:** opent het bestand /etc/cloudsettings/default/contexthub.styles.css, dat de CSS stijlen voor de modules ContextHub UI en UI bevat.
