---
title: Core Components uitproberen in We.Retail
seo-title: Core Components uitproberen in We.Retail
description: 'null'
seo-description: 'null'
uuid: 8d1cea0b-99d9-49b2-b275-41f14864b1ff
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: af3cd818-61cf-4da1-bfb5-87540911ddd5
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Core Components uitproberen in We.Retail{#trying-out-core-components-in-we-retail}

De kerncomponenten zijn moderne, flexibele componenten die eenvoudig uitbreidbaar zijn en eenvoudige integratie in uw projecten mogelijk maken. De kerncomponenten zijn gebouwd rond verscheidene belangrijke ontwerpprincipes zoals HTML, bruikbaarheid out-of-the-box, configureerbaarheid, versioning, en rekbaarheid. We.Retail is gebaseerd op kerncomponenten.

## Uitproberen {#trying-it-out}

1. Start AEM met de voorbeeldinhoud Web.Retail en open de [Componentenconsole](/help/sites-authoring/default-components-console.md).

   **Algemene navigatie -> Gereedschappen -> Componenten**

1. Wanneer u de rail opent in de componentenconsole, kunt u filteren voor een bepaalde componentgroep. De kerncomponenten vindt u in

   * `.core-wcm`: De standaardbasiscomponenten
   * `.core-wcm-form`: De kerncomponenten voor het verzenden van formulieren
   Choose `.core-wcm`.

   ![chlimage_1-162](assets/chlimage_1-162.png)

1. Merk op dat alle kerncomponenten **v1** worden genoemd, die erop wijzen dat dit de eerste versie van deze kerncomponent is. Regelmatige versies worden uitgebracht, die compatibel zijn met de versie van AEM en eenvoudige upgrades mogelijk maken zodat u kunt profiteren van de nieuwste functies.
1. Klik op **Tekst (v1)**.

   Zie dat het Type **van** Middel van de component is `/apps/core/wcm/components/text/v1/text`. De componenten van de kern worden gevonden onder `/apps/core/wcm/components` en zijn versioned per component.

   ![chlimage_1-163](assets/chlimage_1-163.png)

1. Klik op het tabblad **Documentatie** om de documentatie voor ontwikkelaars voor de component te bekijken.

   ![chlimage_1-164](assets/chlimage_1-164.png)

1. Ga terug naar de componentconsole. Filter voor de groep **We.Retail** en selecteer de **component Text** .
1. Zie dat het Type **van** Middel aan een component zoals verwacht onder `/apps/weretail` maar het Type **van Super van het** Middel wijst terug naar de kerncomponent `/apps/core/wcm/components/text/v1/text`.

   ![chlimage_1-165](assets/chlimage_1-165.png)

1. Klik op het tabblad **Live-gebruik** om te zien op welke pagina&#39;s deze component momenteel wordt gebruikt. Klik op de eerste pagina **Bedankt** om de pagina te bewerken.

   ![chlimage_1-166](assets/chlimage_1-166.png)

1. Selecteer op de pagina Hartelijk dank de tekstcomponent en klik in het bewerkingsmenu van de component op het pictogram Overerving annuleren.

   [We.Retail heeft een geglobaliseerde sitestructuur](/help/sites-developing/we-retail-globalized-site-structure.md) waarbij inhoud wordt overgezet van taalstramienen naar [live kopieën via een mechanisme dat overerving](/help/sites-administering/msm.md)wordt genoemd. Daarom moet overerving worden geannuleerd om een gebruiker in staat te stellen tekst handmatig te bewerken.

   ![chlimage_1-167](assets/chlimage_1-167.png)

1. Bevestig de annulering door op **Ja** te klikken.

   ![chlimage_1-168](assets/chlimage_1-168.png)

1. Nadat de overerving is geannuleerd en u de tekstcomponenten selecteert, zijn er veel meer opties beschikbaar. Klik op** Bewerken**.

   ![chlimage_1-169](assets/chlimage_1-169.png)

1. U kunt nu zien welke bewerkingsopties beschikbaar zijn voor de tekstcomponent.

   ![chlimage_1-170](assets/chlimage_1-170.png)

1. Selecteer Sjabloon **** bewerken in het menu **Pagina-informatie**.
1. Klik in de Sjablooneditor van de pagina op het pictogram **Beleid** van de tekstcomponent in de **container** Indeling van de pagina.

   ![chlimage_1-171](assets/chlimage_1-171.png)

1. Met de kerncomponenten kan een sjabloonauteur configureren welke eigenschappen beschikbaar zijn voor de auteurs van de pagina. Het gaat hierbij onder andere om functies zoals toegestane bronnen voor plakken, opmaakopties, beschikbare alineastijlen, enzovoort.

   Dergelijke ontwerpdialoogvensters zijn beschikbaar voor veel kerncomponenten en werken samen met de sjablooneditor. Zodra toegelaten, zijn zij beschikbaar aan de auteur door de componentenredacteurs.

   ![chlimage_1-172](assets/chlimage_1-172.png)

## Aanvullende informatie {#further-information}

Voor meer informatie over de kerncomponenten, zie het auteursdocument [de Componenten](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/introduction.html) van de Kern voor een overzicht van de mogelijkheden van de kerncomponenten en het ontwikkelaarsdocument [Ontwikkelend de Componenten](https://helpx.adobe.com/experience-manager/core-components/using/developing.html) van de Kern voor een technisch overzicht.

Mogelijk wilt u ook [bewerkbare sjablonen](/help/sites-developing/we-retail-editable-templates.md)nader onderzoeken. Raadpleeg het ontwerpdocument [Paginasjablonen](/help/sites-authoring/templates.md) maken of het [ontwikkelaarsdocument Paginasjablonen - Bewerkbaar](/help/sites-developing/page-templates-editable.md) voor meer informatie over bewerkbare sjablonen.
