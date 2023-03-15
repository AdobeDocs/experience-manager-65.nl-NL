---
title: Een SCF-sandbox maken
seo-title: Create An SCF Sandbox
description: Dit leerprogramma is hoofdzakelijk voor ontwikkelaars, nieuw aan AEM, die in het gebruiken van componenten SCF geinteresseerd zijn.  Het door de verwezenlijking van een zandbakplaats SCF
seo-description: This tutorial is primarily for developers, new to AEM, who are interested in using SCF components.  It walks through the creation of An SCF Sandbox site
uuid: ee52e670-e1e6-4bcd-9548-c963142e6704
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: e1b5c25d-cbdd-421c-b81a-feb6039610a3
exl-id: 89858814-6625-4a56-8359-cc1eca402816
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# Een SCF-sandbox maken  {#create-an-scf-sandbox}


Vanaf AEM 6.1 Gemeenschappen is het maken van een communitysite de eenvoudigste manier om snel een sandbox te maken. Zie [Aan de slag met AEM Communities](getting-started.md).

Een ander nuttig hulpmiddel voor ontwikkelaars is het [Community Components Guide](components-guide.md), die het mogelijk maakt onderdelen en kenmerken van Gemeenschappen te verkennen en snel te prototypen.

Het maken van een website kan nuttig zijn voor het begrijpen van de structuur van een AEM website, die functies van de Gemeenschappen kan bevatten, en voor het verschaffen van eenvoudige pagina&#39;s waarop u kunt zoeken naar het werken met de [Sociaal-componentkader (SCF)](scf.md).

Dit leerprogramma is hoofdzakelijk voor ontwikkelaars, nieuw aan AEM, die in het gebruiken van componenten SCF geinteresseerd zijn. Het doorloopt de verwezenlijking van een zandbak SCF, gelijkend op het leerprogramma voor [Een volledig aanbevolen internetwebsite maken](../../help/sites-developing/website.md) waarin de nadruk ligt op sitestructuren, zoals navigatie, logo, zoekopdracht, werkbalk en het weergeven van onderliggende pagina&#39;s.

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
>Deze zelfstudie maakt geen community-site met de functionaliteit die is gemaakt met de [Community Sites-console](sites-console.md). In deze zelfstudie wordt bijvoorbeeld niet beschreven hoe u aanmelding, zelfregistratie kunt instellen, [sociale aanmelding](social-login.md), berichten, profielen enzovoort.
>
>Als u de voorkeur geeft aan een eenvoudige communitysite, voert u de [Een voorbeeldpagina maken](create-sample-page.md) zelfstudie.

## Vereisten {#prerequisites}

In deze zelfstudie wordt ervan uitgegaan dat u één AEM auteur en één AEM publicatieexemplaar hebt geïnstalleerd waarop de [nieuwste release](deploy-communities.md#latest-releases) van de Gemeenschappen.

Hier volgen enkele handige koppelingen voor ontwikkelaars die nog niet vertrouwd zijn met het AEM platform:

* [Aan de slag](../../help/sites-deploying/deploy.md#getting-started): voor het implementeren van AEM instanties.

   * [De basisbeginselen](../../help/sites-developing/the-basics.md): voor ontwikkelaars van websites en functies.
   * [Eerste stappen voor auteurs](../../help/sites-authoring/first-steps.md): voor het ontwerpen van pagina-inhoud.

## CRXDE Lite Development Environment gebruiken {#using-crxde-lite-development-environment}

AEM ontwikkelaars besteden veel tijd aan [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md) ontwikkelomgeving op een auteurinstantie. CRXDE Lite biedt minder beperkte toegang tot de CRX-opslagplaats. Klassieke UI-gereedschappen en UI-consoles met aanraakbediening bieden meer gestructureerde toegang tot specifieke delen van de CRX-opslagplaats.

Nadat u zich hebt aangemeld met beheerdersrechten, kunt u op verschillende manieren toegang krijgen tot CRXDE Lite:

1. Selecteer navigatie in globale navigatie **[!UICONTROL Tools > CRXDE Lite]**.

   ![crxde-lite](assets/tools-crxde.png)

2. Van de [klassieke UI-welkomstpagina](http://localhost:4502/welcome.html), schuiven omlaag en klikken **[!UICONTROL CRXDE Lite]** in het rechterdeelvenster.

   ![classic-ui-crxde](assets/classic-ui-crxde.png)

3. Bladeren naar `CRXDE Lite`: `<server>:<port>/crx/de`

   Bijvoorbeeld op een lokale auteur-instantie: [http://localhost:4502/crx/de](http://localhost:4502/crx/de)

Als u met CRXDE Lite wilt werken, moet u zich aanmelden met ontwikkelaars- of beheerdersprikkels. Voor de standaardinstantie localhost kunt u zich aanmelden met

* `username: admin`
* `password: admin`


**Wees voorzichtig** dat deze login onderbreking zal en u periodiek opnieuw zult moeten inloggen gebruikend de trek neer op het juiste eind van de CRXDe Lite hulpmiddelbar.

Als u zich niet hebt aangemeld, kunt u niet door de JCR-opslagplaats navigeren of bewerkingen uitvoeren/opslaan.

***Bij twijfel kunt u zich opnieuw aanmelden!***

![opnieuw aanmelden](assets/relogin.png)
