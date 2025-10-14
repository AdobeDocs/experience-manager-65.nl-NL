---
title: Core Components uitproberen in We.Retail
description: Leer hoe u Core Components kunt uitproberen in Adobe Experience Manager met We.Retail.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: b5f2be67-c93c-4dbc-acc0-3edd8f1a282f
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 0%

---

# Core Components uitproberen in We.Retail{#trying-out-core-components-in-we-retail}

De kerncomponenten zijn moderne, flexibele componenten die eenvoudig uitbreidbaar zijn en eenvoudige integratie in uw projecten mogelijk maken. De kerncomponenten zijn gebouwd rond verscheidene belangrijke ontwerpprincipes zoals HTML, bruikbaarheid out-of-the-box, configureerbaarheid, versioning, en rekbaarheid. We.Retail is gebaseerd op kerncomponenten.

## Uitproberen {#trying-it-out}

1. Het begin Adobe Experience Manager (AEM) met de wij.Retail steekproefinhoud en opent de [&#x200B; Console van Componenten &#x200B;](/help/sites-authoring/default-components-console.md).

   **Globale Navigatie > Hulpmiddelen > Componenten**

1. Wanneer u de rail opent in de componentenconsole, kunt u filteren voor een bepaalde componentgroep. De kerncomponenten vindt u in

   * `.core-wcm`: De standaard kerncomponenten
   * `.core-wcm-form`: De kerncomponenten voor het verzenden van formulieren

   Kies `.core-wcm` .

   ![&#x200B; chlimage_1-162 &#x200B;](assets/chlimage_1-162.png)

1. Alle kerncomponenten worden genoemd **v1**, die erop wijzen dat dit de eerste versie van deze kerncomponent is. Regelmatige versies worden uitgebracht, die versiecompatibel zijn met AEM en eenvoudig upgraden mogelijk maken, zodat u kunt profiteren van de nieuwste functies.
1. Klik **Tekst (v1)**.

   Zie dat het **Type van Middel** van de component `/apps/core/wcm/components/text/v1/text` is. De componenten van de kern worden gevonden onder `/apps/core/wcm/components` en zijn versioned per component.

   ![&#x200B; chlimage_1-163 &#x200B;](assets/chlimage_1-163.png)

1. Klik het **Documentatie** lusje om de ontwikkelaardocumentatie voor de component te zien.

   ![&#x200B; chlimage_1-164 &#x200B;](assets/chlimage_1-164.png)

1. Ga terug naar de componentconsole. Filter voor de groep **We.Retail** en selecteer de **3&rbrace; component van de Tekst &lbrace;.**
1. Zie dat het **Type van Middel** aan een component zoals verwacht onder `/apps/weretail` maar het **Type van Super van het Middel** wijst terug naar de kerncomponent `/apps/core/wcm/components/text/v1/text`.

   ![&#x200B; chlimage_1-165 &#x200B;](assets/chlimage_1-165.png)

1. Klik het **Levende lusje van het Gebruik** om te zien op welke pagina&#39;s deze component wordt gebruikt. Klik eerste **Dank u** pagina om de pagina uit te geven.

   ![&#x200B; chlimage_1-166 &#x200B;](assets/chlimage_1-166.png)

1. Selecteer op de pagina Hartelijk dank de tekstcomponent en klik in het bewerkingsmenu van de component op het pictogram Overerving annuleren.

   [&#x200B; Wij.Retail heeft een geglobaliseerde plaatsstructuur &#x200B;](/help/sites-developing/we-retail-globalized-site-structure.md) waar de inhoud van taalmeesters aan [&#x200B; levende exemplaren door een mechanisme genoemd erfenis &#x200B;](/help/sites-administering/msm.md) wordt geduwd. Daarom moet overerving worden geannuleerd, zodat een gebruiker tekst handmatig kan bewerken.

   ![&#x200B; chlimage_1-167 &#x200B;](assets/chlimage_1-167.png)

1. Bevestig de annulering door **ja** te klikken.

   ![&#x200B; chlimage_1-168 &#x200B;](assets/chlimage_1-168.png)

1. Nadat de overerving is geannuleerd en u de tekstcomponenten selecteert, zijn er veel meer opties beschikbaar. Klik **uitgeven**.

   ![&#x200B; chlimage_1-169 &#x200B;](assets/chlimage_1-169.png)

1. U kunt nu zien welke bewerkingsopties beschikbaar zijn voor de tekstcomponent.

   ![&#x200B; chlimage_1-170 &#x200B;](assets/chlimage_1-170.png)

1. Van het **menu van de Informatie van de Pagina**, uitgezocht **geef Malplaatje** uit.
1. In de Redacteur van het Malplaatje van de pagina, klik het **pictogram van het Beleid** van de component van de Tekst in de **Container van de Lay-out** van de pagina.

   ![&#x200B; chlimage_1-171 &#x200B;](assets/chlimage_1-171.png)

1. Met de kerncomponenten kan een sjabloonauteur configureren welke eigenschappen beschikbaar zijn voor de auteurs van de pagina. Dit zijn onder andere functies zoals toegestane bronnen voor plakken, opmaakopties en beschikbare alineastijlen.

   Dergelijke ontwerpdialoogvensters zijn beschikbaar voor veel kerncomponenten en werken samen met de sjablooneditor. Zodra toegelaten, zijn zij beschikbaar aan de auteur door de componentenredacteurs.

   ![&#x200B; chlimage_1-172 &#x200B;](assets/chlimage_1-172.png)

## Aanvullende informatie {#further-information}

Voor verdere informatie over de kerncomponenten, zie de auteursdocument [&#x200B; Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=nl-NL) voor een overzicht van de mogelijkheden van de kerncomponenten en het ontwikkelaarsdocument [&#x200B; het Ontwikkelen van de Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/overview.html?lang=nl-NL) voor een technisch overzicht.

Ook kunt u wensen om [&#x200B; editable malplaatjes &#x200B;](/help/sites-developing/we-retail-editable-templates.md) verder te onderzoeken. Verwijs naar het auteursdocument [&#x200B; Creërend de Malplaatjes van de Pagina &#x200B;](/help/sites-authoring/templates.md) of de Malplaatjes van het ontwikkelaarsdocument van de Pagina [&#x200B; - editable &#x200B;](/help/sites-developing/page-templates-editable.md) voor volledige details op editable malplaatjes.
