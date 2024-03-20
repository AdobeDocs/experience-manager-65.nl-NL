---
title: Core Components uitproberen in We.Retail
description: Leer hoe u Core Components kunt uitproberen in Adobe Experience Manager met We.Retail.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: b5f2be67-c93c-4dbc-acc0-3edd8f1a282f
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 0%

---

# Core Components uitproberen in We.Retail{#trying-out-core-components-in-we-retail}

De kerncomponenten zijn moderne, flexibele componenten die eenvoudig uitbreidbaar zijn en eenvoudige integratie in uw projecten mogelijk maken. De kerncomponenten zijn gebouwd rond verscheidene belangrijke ontwerpprincipes zoals HTML, bruikbaarheid out-of-the-box, configureerbaarheid, versioning, en rekbaarheid. We.Retail is gebaseerd op kerncomponenten.

## Uitproberen {#trying-it-out}

1. Start Adobe Experience Manager (AEM) met de voorbeeldinhoud Web.Retail en open de [Componentenconsole](/help/sites-authoring/default-components-console.md).

   **Algemene navigatie > Gereedschappen > Componenten**

1. Wanneer u de rail opent in de componentenconsole, kunt u filteren voor een bepaalde componentgroep. De kerncomponenten vindt u in

   * `.core-wcm`: De standaard kerncomponenten
   * `.core-wcm-form`: De kerncomponenten voor het verzenden van formulieren

   Kies `.core-wcm`.

   ![chlimage_1-162](assets/chlimage_1-162.png)

1. Alle kerncomponenten krijgen een naam **v1**, waaruit blijkt dat dit de eerste versie van deze kerncomponent is. Regelmatige versies worden uitgebracht, die versiecompatibel zijn met AEM en eenvoudig upgraden mogelijk maken, zodat u kunt profiteren van de nieuwste functies.
1. Klikken **Tekst (v1)**.

   Zie de **Resourcetype** van de component `/apps/core/wcm/components/text/v1/text`. Kerncomponenten vindt u onder `/apps/core/wcm/components` en zijn versioned per component.

   ![chlimage_1-163](assets/chlimage_1-163.png)

1. Klik op de knop **Documentatie** om de documentatie voor ontwikkelaars voor de component te zien.

   ![chlimage_1-164](assets/chlimage_1-164.png)

1. Ga terug naar de componentconsole. Filter voor de groep **Wij.Detailhandel** en selecteert u de **Tekst** component.
1. Zie de **Resourcetype** punten naar een component zoals wordt verwacht onder `/apps/weretail` maar de **Super Type resource** verwijst terug naar de kerncomponent `/apps/core/wcm/components/text/v1/text`.

   ![chlimage_1-165](assets/chlimage_1-165.png)

1. Klik op de knop **Live-gebruik** om te zien op welke pagina&#39;s deze component wordt gebruikt. Klik eerst **Bedankt** pagina om de pagina te bewerken.

   ![chlimage_1-166](assets/chlimage_1-166.png)

1. Selecteer op de pagina Hartelijk dank de tekstcomponent en klik in het bewerkingsmenu van de component op het pictogram Overerving annuleren.

   [We.Retail heeft een geglobaliseerde sitestructuur](/help/sites-developing/we-retail-globalized-site-structure.md) waar inhoud van taalstramienen naar [levende exemplaren door een mechanisme genoemd erfenis](/help/sites-administering/msm.md). Daarom moet overerving worden geannuleerd, zodat een gebruiker tekst handmatig kan bewerken.

   ![chlimage_1-167](assets/chlimage_1-167.png)

1. De annulering bevestigen door op **Ja**.

   ![chlimage_1-168](assets/chlimage_1-168.png)

1. Nadat de overerving is geannuleerd en u de tekstcomponenten selecteert, zijn er veel meer opties beschikbaar. Klikken **Bewerken**.

   ![chlimage_1-169](assets/chlimage_1-169.png)

1. U kunt nu zien welke bewerkingsopties beschikbaar zijn voor de tekstcomponent.

   ![chlimage_1-170](assets/chlimage_1-170.png)

1. Van de **Pagina-informatie** menu, selecteert u **Sjabloon bewerken**.
1. Klik in de Sjablooneditor van de pagina op de knop **Beleid** pictogram van de component Text in het deelvenster **Layout Container** van de pagina.

   ![chlimage_1-171](assets/chlimage_1-171.png)

1. Met de kerncomponenten kan een sjabloonauteur configureren welke eigenschappen beschikbaar zijn voor de auteurs van de pagina. Dit zijn onder andere functies zoals toegestane bronnen voor plakken, opmaakopties en beschikbare alineastijlen.

   Dergelijke ontwerpdialoogvensters zijn beschikbaar voor veel kerncomponenten en werken samen met de sjablooneditor. Zodra toegelaten, zijn zij beschikbaar aan de auteur door de componentenredacteurs.

   ![chlimage_1-172](assets/chlimage_1-172.png)

## Aanvullende informatie {#further-information}

Raadpleeg het ontwerpdocument voor meer informatie over de kerncomponenten [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) voor een overzicht van de mogelijkheden van de kerncomponenten en het ontwikkelaarsdocument [Basiscomponenten ontwikkelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/overview.html) voor een technisch overzicht.

Mogelijk wilt u verder onderzoek uitvoeren [bewerkbare sjablonen](/help/sites-developing/we-retail-editable-templates.md). Verwijs naar het auteursdocument [Paginasjablonen maken](/help/sites-authoring/templates.md) of de pagina voor ontwikkelaarsdocumenten [Sjablonen - Bewerkbaar](/help/sites-developing/page-templates-editable.md) voor volledige details over bewerkbare sjablonen.
