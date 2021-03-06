---
title: Een SCF-sandbox maken
seo-title: Een SCF-sandbox maken
description: Dit leerprogramma is hoofdzakelijk voor ontwikkelaars, nieuw aan AEM, die in het gebruiken van componenten SCF geinteresseerd zijn.  Het door de verwezenlijking van een zandbakplaats SCF
seo-description: Dit leerprogramma is hoofdzakelijk voor ontwikkelaars, nieuw aan AEM, die in het gebruiken van componenten SCF geinteresseerd zijn.  Het door de verwezenlijking van een zandbakplaats SCF
uuid: ee52e670-e1e6-4bcd-9548-c963142e6704
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: e1b5c25d-cbdd-421c-b81a-feb6039610a3
translation-type: tm+mt
source-git-commit: 548e19b0fc76ede8685ea938ed871fbdc8c3858f
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 0%

---



# Een SCF-sandbox maken {#create-an-scf-sandbox}


Vanaf AEM 6.1 Gemeenschappen is het maken van een communitysite de eenvoudigste manier om snel een sandbox te maken. Zie [Aan de slag met AEM Communities](getting-started.md).

Een ander handig hulpmiddel voor ontwikkelaars is de [Community Components guide](components-guide.md), waarmee u onderdelen en functies van Gemeenschappen kunt verkennen en snel prototypen kunt maken.

Het maken van een website kan handig zijn voor het begrijpen van de structuur van een AEM website die functies van de Gemeenschappen kan bevatten, en voor het verschaffen van eenvoudige pagina&#39;s waarop u kunt zoeken naar het werken met het [social component framework (SCF)](scf.md).

Dit leerprogramma is hoofdzakelijk voor ontwikkelaars, nieuw aan AEM, die in het gebruiken van componenten SCF geinteresseerd zijn. Het doorloopt de verwezenlijking van een Zandbakplaats SCF, gelijkend op de zelfstudie voor [hoe te om een Volledig Getoonde Website van Internet te creëren](../../help/sites-developing/website.md) die zich op plaatsstructuren, zoals navigatie, embleem, onderzoek, toolbar, en het vermelden van kindpagina&#39;s concentreert.

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
>Deze zelfstudie maakt geen community-site met de functionaliteit die is gemaakt met de [Community Sites-console](sites-console.md). In deze zelfstudie wordt bijvoorbeeld niet beschreven hoe u aanmeldingsgegevens, zelfregistratie, [sociale aanmelding](social-login.md), berichten, profielen enzovoort kunt instellen.
>
>Als u de voorkeur geeft aan een eenvoudige communitysite, volgt u de zelfstudie [Een voorbeeldpagina maken](create-sample-page.md).

## Vereisten {#prerequisites}

In deze zelfstudie wordt ervan uitgegaan dat u één AEM auteur en één AEM publicatieexemplaar hebt geïnstalleerd waarop de [nieuwste release](deploy-communities.md#latest-releases) van de Gemeenschappen is geïnstalleerd.

Hier volgen enkele handige koppelingen voor ontwikkelaars die nog niet vertrouwd zijn met het AEM platform:

* [Aan de slag](../../help/sites-deploying/deploy.md#getting-started): voor het implementeren van AEM instanties.

   * [De basisbeginselen](../../help/sites-developing/the-basics.md): voor ontwikkelaars van websites en functies.
   * [Eerste stappen voor auteurs](../../help/sites-authoring/first-steps.md): voor het ontwerpen van pagina-inhoud.

## Werken met CRXDE Lite-ontwikkelomgeving {#using-crxde-lite-development-environment}

AEM ontwikkelaars besteden veel van hun tijd in de [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md) ontwikkelomgeving aan een auteursinstantie. CRXDE Lite biedt minder beperkte toegang tot de CRX-opslagplaats. Klassieke UI-gereedschappen en UI-consoles met aanraakbediening bieden meer gestructureerde toegang tot specifieke delen van de CRX-opslagplaats.

Nadat u zich hebt aangemeld met beheerdersrechten, kunt u op verschillende manieren toegang krijgen tot CRXDE Lite:

1. Selecteer navigatie **[!UICONTROL Tools > CRXDE Lite]** vanuit globale navigatie.

   ![crxde-lite](assets/tools-crxde.png)

2. Van [klassieke UI welkomstpagina](http://localhost:4502/welcome.html), scrol neer en klik **[!UICONTROL CRXDE Lite]** in het juiste paneel.

   ![classic-ui-crxde](assets/classic-ui-crxde.png)

3. Ga direct naar `CRXDE Lite`: `<server>:<port>/crx/de`

   Bijvoorbeeld op een lokale auteur-instantie: [http://localhost:4502/crx/de](http://localhost:4502/crx/de)

Als u met CRXDE Lite wilt werken, moet u zich aanmelden met ontwikkelaars- of beheerdersprikkels. Voor de standaardinstantie localhost kunt u zich aanmelden met

* `username: admin`
* `password: admin`


**Wees** ervan op de hoogte dat deze time-out voor de aanmelding zal optreden en u regelmatig opnieuw moet aanmelden met de pull-down aan de rechterkant van de werkbalk van CRXDe Lite.

Als u zich niet hebt aangemeld, kunt u niet door de JCR-opslagplaats navigeren of bewerkingen uitvoeren/opslaan.

***Bij twijfel kunt u zich opnieuw aanmelden!***

![opnieuw aanmelden](assets/relogin.png)
