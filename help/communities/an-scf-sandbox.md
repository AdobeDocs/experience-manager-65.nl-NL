---
title: Een SCF-sandbox maken
description: Dit leerprogramma is hoofdzakelijk voor ontwikkelaars, nieuw aan AEM, die in het gebruiken van componenten SCF geïnteresseerd zijn. Het door de verwezenlijking van een zandbakplaats SCF
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 89858814-6625-4a56-8359-cc1eca402816
solution: Experience Manager
feature: Communities
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# Een SCF-sandbox maken  {#create-an-scf-sandbox}

Vanaf AEM 6.1 Gemeenschappen is het maken van een communitysite de eenvoudigste manier om snel een sandbox te maken. Zie [&#x200B; Begonnen het Worden met AEM Communities &#x200B;](getting-started.md).

Een ander nuttig hulpmiddel voor ontwikkelaars is de [&#x200B; gids van de Componenten van de Gemeenschap &#x200B;](components-guide.md), die voor exploratie en het snelle prototypen van de componenten en de eigenschappen van Gemeenschappen toestaat.

De oefening van het creëren van een website kan nuttig zijn om de structuur van een AEM website te begrijpen die de eigenschappen van Gemeenschappen kan omvatten, terwijl ook het verstrekken van eenvoudige pagina&#39;s waarop het werken met het [&#x200B; sociale componentenkader (SCF) &#x200B;](scf.md) te onderzoeken.

Dit leerprogramma is hoofdzakelijk voor ontwikkelaars, nieuw aan AEM, die in het gebruiken van componenten SCF geïnteresseerd zijn. Het loopt door de verwezenlijking van een zandbakplaats SCF, gelijkend op het leerprogramma voor [&#x200B; hoe te om een Volledig Getekende Website van Internet &#x200B;](../../help/sites-developing/website.md) te creëren die op-plaatstructuren, zoals navigatie, embleem, onderzoek, toolbar, en het vermelden van kindpagina&#39;s concentreert.

De ontwikkeling vindt op een auteursgeval plaats, terwijl het experimenteren met de plaats best op een publicatiegeval is.

De stappen in deze zelfstudie zijn:

* [Websitestructuur instellen](setup-website.md)
* [Aanvankelijke zandbaktoepassing](initial-app.md)
* [Oorspronkelijke inhoud van sandbox](initial-content.md)
* [Sandbox-toepassing ontwikkelen](develop-app.md)
* [Clientlibs toevoegen](add-clientlibs.md)
* [Sandbox-inhoud ontwikkelen](develop-content.md)

>[!CAUTION]
>
>Dit leerprogramma leidt tot geen communautaire plaats met de functionaliteit die gebruikend de [&#x200B; console van de Plaatsen van Gemeenschappen &#x200B;](sites-console.md) wordt gecreeerd. Bijvoorbeeld, beschrijft dit leerprogramma niet hoe te opstelling login, zelfregistratie, [&#x200B; sociale login &#x200B;](social-login.md), overseinen, profielen, etc.
>
>Als een eenvoudige communautaire plaats wordt geprefereerd, volg [&#x200B; tot een leerprogramma van de Pagina van de Steekproef &#x200B;](create-sample-page.md).

## Vereisten {#prerequisites}

Dit leerprogramma veronderstelt u één AEM auteur hebt en één AEM geïnstalleerde instantie publiceren die de [&#x200B; recentste versie &#x200B;](deploy-communities.md#latest-releases) van Gemeenschappen heeft.

Hier volgen enkele handige koppelingen voor ontwikkelaars die nog niet vertrouwd zijn met het AEM platform:

* [&#x200B; Begonnen het Worden &#x200B;](../../help/sites-deploying/deploy.md#getting-started): voor het opstellen van AEM instanties.

   * [&#x200B; de Basisbeginselen &#x200B;](../../help/sites-developing/the-basics.md): voor ontwikkelaars van websites en eigenschappen.
   * [&#x200B; Eerste Stappen voor Auteurs &#x200B;](../../help/sites-authoring/first-steps.md): voor het ontwerpen van paginainhoud.

## CRXDE Lite Development Environment gebruiken {#using-crxde-lite-development-environment}

AEM ontwikkelaars brengen veel van hun tijd in het [&#x200B; CRXDE Lite &#x200B;](../../help/sites-developing/developing-with-crxde-lite.md) ontwikkelmilieu op een auteursinstantie door. CRXDE Lite biedt minder beperkte toegang tot de CRX-opslagplaats. Klassieke UI-gereedschappen en UI-consoles met aanraakbediening bieden meer gestructureerde toegang tot specifieke delen van de CRX-opslagplaats.

Nadat u zich hebt aangemeld met beheerdersrechten, zijn er verschillende manieren om toegang te krijgen tot CRXDE Lite:

1. Selecteer navigatie **[!UICONTROL Tools > CRXDE Lite]** bij globale navigatie.

   ![&#x200B; crxde-lite &#x200B;](assets/tools-crxde.png)

2. Van [&#x200B; klassieke UI welkomstpagina &#x200B;](http://localhost:4502/welcome.html), scrol neer en klik **[!UICONTROL CRXDE Lite]** in het juiste paneel.

   ![&#x200B; klassieke-ui-crxde &#x200B;](assets/classic-ui-crxde.png)

3. Ga rechtstreeks naar `CRXDE Lite` : `<server>:<port>/crx/de`

   Bijvoorbeeld, op een lokale auteursinstantie: [&#x200B; http://localhost:4502/crx/de &#x200B;](http://localhost:4502/crx/de)

Als u met CRXDE Lite wilt werken, moet u zich aanmelden met de ontwikkelaar- of beheerdersrechten. Voor de standaardinstantie localhost kunt u zich aanmelden met

* `username: admin`
* `password: admin`


Deze login tijden uit en u moet periodiek opnieuw login gebruikend het pull-down op het rechtereind van de het hulpmiddelbar van de CRXDE Lite.

Als u zich niet hebt aangemeld, kunt u niet door de JCR-opslagplaats navigeren of bewerkingen uitvoeren/opslaan.

***wanneer in twijfel, herlogin!***

![&#x200B; opnieuw login &#x200B;](assets/relogin.png)
