---
title: "Lesbestand: uw adaptieve formulier publiceren"
description: Het adaptieve formulier publiceren als een AEM pagina, het formulier insluiten op een AEM Sites-pagina of het adaptieve formulier insluiten in een externe webpagina
contentOwner: khsingh
topic-tags: introduction
docset: aem65
feature: Adaptive Forms
exl-id: c039faec-f832-43d5-8a86-22afa3bef2a4
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '859'
ht-degree: 0%

---

# Zelfstudie: uw adaptieve formulier publiceren {#tutorial-publish-your-adaptive-form}

![Hoofdafbeelding](do-not-localize/13-publish-your-adaptive-form-small.png)

Deze zelfstudie is een stap in de [Uw eerste adaptieve formulier maken](https://helpx.adobe.com/experience-manager/6-3/forms/using/create-your-first-adaptive-form.html) reeks. U wordt aangeraden de reeks in chronologische volgorde te volgen om het volledige gebruik van de zelfstudie te begrijpen, uit te voeren en aan te tonen.

Nadat het aangepaste formulier gereed is, kunt u het publiceren en beschikbaar maken voor eindgebruikers. De eindgebruikers kunnen het gepubliceerde formulier openen op elk apparaat en in de internetbrowser. Wanneer een adaptief formulier wordt gepubliceerd, worden het formulier en de bijbehorende inhoud gekopieerd van een AEM auteur naar een AEM publicatie-exemplaar. Het formulier wordt via het publicatieexemplaar beschikbaar gesteld voor de eindgebruiker.

U kunt op de volgende manieren een adaptief formulier publiceren:

* [Het adaptieve formulier publiceren als een AEM](../../forms/using/publish-your-adaptive-form.md#publish-the-adaptive-form-as-an-aem-page)
* [Het adaptieve formulier insluiten in een AEM Sites-pagina](#embed-the-adaptive-form-in-an-aem-sites-page)
* [Het adaptieve formulier insluiten in een externe webpagina (een niet-AEM webpagina die buiten AEM wordt gehost)](../../forms/using/publish-your-adaptive-form.md)

## Voordat u begint {#before-you-start}

* **[Een AEM Forms-publicatie-instantie instellen](https://helpx.adobe.com/experience-manager/6-3/forms/using/installing-configuring-aem-forms-osgi.html)**: De instantie publish is een openbare instantie waarbij AEM [!DNL Forms] in de publicatiemodus. In een productieomgeving bevindt de publicatie-instantie zich buiten de firewall van de organisatie.
* **[Replicatie instellen en replicatie omkeren](https://helpx.adobe.com/experience-manager/6-3/help/sites-deploying/replication.html)**: Replicatie kopieert inhoud van de auteurinstantie naar een publicatie-instantie en retourneert gebruikersinvoer (bijvoorbeeld formulierinvoer) van de publicatie-instantie naar de auteur-instantie.

## Het adaptieve formulier publiceren als een AEM {#publish-the-adaptive-form-as-an-aem-page}

Wanneer het adaptieve formulier wordt gepubliceerd als een AEM pagina, bevat de hele webpagina alleen het gepubliceerde formulier. U kunt de URL van het aangepaste formulier gebruiken om het formulier te koppelen van een andere webpagina. Als u het dialoogvenster **verzendadres-add-update-form** adaptief formulier als AEM pagina:

1. Aanmelden bij AEM [!DNL Forms] -instantie en zoek het adaptieve formulier voor het verzendadres-add-update-formulier in de AEM [!DNL Forms] UI.
   `https://localhost:4502/aem/forms.html/content/dam/formsanddocuments`
1. Selecteer het adaptieve formulier voor het verzendadres-add-update en selecteer **[!UICONTROL Publish]**. Er wordt een dialoogvenster weergegeven met elementen die betrekking hebben op het adaptieve formulier. Selecteer **[!UICONTROL Publish]**. Het adaptieve formulier wordt gepubliceerd en er verschijnt een succesdialoogvenster.
1. Open het formulier op het publicatieexemplaar. Het formulier kan door de eindgebruiker worden ingevuld en verzonden.
   `https://localhost:4503/content/forms/af/shipping-address-add-update-form.html`

## Het adaptieve formulier insluiten in een AEM Sites-pagina {#embed-the-adaptive-form-in-an-aem-sites-page}

AEM [!DNL Forms] stelt formulierontwikkelaars in staat om adaptieve formulieren naadloos in te sluiten in een AEM [!DNL Sites] pagina. Het ingesloten adaptieve formulier is volledig functioneel en gebruikers kunnen het formulier invullen en verzenden zonder de pagina te verlaten. Hiermee kan de gebruiker in de context van andere elementen op de webpagina blijven en tegelijkertijd met het formulier communiceren.

AEM [!DNL Forms] een component AEM [!DNL Forms] Container voor het insluiten van een adaptief formulier op een AEM [!DNL Sites] pagina. De component is standaard niet zichtbaar in AEM [!DNL Sites] container. Voer de volgende stappen uit om de AEM in te schakelen [!DNL Forms] Containercomponent en insluiten van het adaptieve formulier in een AEM [!DNL Sites] Pagina:

1. Maak en open een pagina in de website Web.Retail voor bewerking. Bijvoorbeeld: [https://localhost:4502/editor.html/content/we-retail/us/en/user/shipping-and-billing-address.html](https://localhost:4502/editor.html/content/we-retail/us/en/user/shipping-and-billing-address.html). Het adaptieve formulier is ingesloten in de [!DNL Sites] pagina.

   U kunt het adaptieve formulier ook insluiten in een bestaande We.Retail [!DNL Site's] pagina. Bijvoorbeeld de pagina ABOUT US [https://localhost:4502/editor.html/content/we-retail/us/en/about-us.html](https://localhost:4502/editor.html/content/we-retail/us/en/about-us.html). Hiermee bespaart u de tijd om een pagina te maken. In de onderstaande stappen wordt de nieuwe pagina gebruikt.

   De website We.Retail wordt verzonden met AEM. Als u niet de website Web.Retail geïnstalleerd hebt, zie [We.Retail Reference Implementation](https://helpx.adobe.com/experience-manager/6-3/help/sites-developing/we-retail.html) installeer de site.

1. Selecteren ![eigenschappen](assets/properties.png) pagina-informatie en selecteer de **[!UICONTROL Edit Template]** in de nieuwe Web.Retail-site. De sjabloon van de pagina wordt geopend op een nieuw tabblad van de browser.
1. Selecteren in het dialoogvenster **[!UICONTROL layout container]** en selecteert u ![voederbeheer](assets/feedmanagement.png). In de **[!UICONTROL Allowed Components]** tabblad, vouwt u de **[!UICONTROL General]** accordeon selecteert u de **[!UICONTROL AEM Form]** en selecteert u ![save_icon](assets/save_icon.svg). De AEM [!DNL Forms] Containercomponent is ingeschakeld voor de pagina.

1. Open het browsertabblad met AEM [!DNL Sites] pagina geopend in stap 1. Selecteer de **[!UICONTROL Drag components here]** en selecteert u **+.** In de **[!UICONTROL Insert New Component]** vak, selecteren **[!UICONTROL AEM Form]**. De **[!UICONTROL AEM Forms Container]** wordt toegevoegd aan de pagina.
1. Selecteer de **[!UICONTROL AEM Forms container]** en selecteert u ![configure-icon](assets/configure-icon.svg). Een dialoogvenster met eigenschappen van AEM [!DNL Forms] Container wordt weergegeven. In de **[!UICONTROL Asset Path]** , bladert en selecteert u het aangepaste formulier voor het verzendadres en de update. Selecteren ![save_icon](assets/save_icon.svg). Het adaptieve formulier is ingesloten op de pagina.
1. Publiceer zowel het adaptieve formulier als [!DNL Sites] pagina. Hieronder volgen enkele punten die u in overweging wilt nemen:

   * Als u de AEM publiceert [!DNL Sites] voor het eerst pagina&#39;s maken en een ingesloten formulier bevatten, publiceert u de [!DNL Sites] en het ingesloten formulier.
   * Als u alleen het ingesloten formulier op een gepubliceerde sitepagina wijzigt, publiceert u het oorspronkelijke formulier en de wijzigingen worden weerspiegeld in de gepubliceerde sitepagina. De gepubliceerde sitepagina bevat een verwijzing naar het formulier en de pagina hoeft niet opnieuw te worden gepubliceerd.
   * Als u de [!DNL Sites] pagina en het ingesloten formulier, publiceert u de [!DNL Sites] en het formulier.

     ![insluiten-in-aem-sites](assets/embed-in-aem-sites.png)

   Formulier Verzendadres en factuuradres wijzigen toegevoegd aan een AEM [!DNL Sites] pagina.

## Het adaptieve formulier insluiten in een externe webpagina {#embed-the-adaptive-form-in-an-external-webpage}

U kunt een adaptief formulier insluiten in een externe webpagina (een niet-AEM webpagina die buiten AEM wordt gehost) door enkele regels JavaScript in de externe webpagina in te voegen. De JavaScript-code verzendt een HTTP-aanvraag naar de AEM [!DNL Forms] voor het adaptieve formulier en de bijbehorende bronnen en voegt het adaptieve formulier toe aan de webpagina. Zie voor meer informatie [het aangepaste formulier insluiten in een externe webpagina](/help/forms/using/embed-adaptive-form-external-web-page.md).
