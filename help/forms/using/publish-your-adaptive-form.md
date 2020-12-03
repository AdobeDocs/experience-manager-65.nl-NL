---
title: '"Zelfstudie: Uw adaptieve formulier publiceren"'
seo-title: '"Zelfstudie: Uw adaptieve formulier publiceren"'
description: Het adaptieve formulier publiceren als een AEM pagina, het formulier insluiten op een AEM Sites-pagina of het adaptieve formulier insluiten in een externe webpagina
seo-description: Het adaptieve formulier publiceren als een AEM pagina, het formulier insluiten op een AEM Sites-pagina of het adaptieve formulier insluiten in een externe webpagina
uuid: 1b164376-e61a-40aa-9f16-c79d24a72e20
contentOwner: khsingh
topic-tags: introduction
discoiquuid: e24dbd0e-4481-4f9d-9570-3a4046b3ef35
docset: aem65
translation-type: tm+mt
source-git-commit: 1a816672b3e97346f5a7a984fcb4dc0df1a5b0da
workflow-type: tm+mt
source-wordcount: '939'
ht-degree: 1%

---


# Zelfstudie: Het aangepaste formulier {#tutorial-publish-your-adaptive-form} publiceren

![](do-not-localize/13-publish-your-adaptive-form-small.png)

Deze zelfstudie is een stap in de serie [Uw eerste adaptieve vorm maken](https://helpx.adobe.com/experience-manager/6-3/forms/using/create-your-first-adaptive-form.html). U wordt aangeraden de reeks in chronologische volgorde te volgen om het volledige gebruik van de zelfstudie te begrijpen, uit te voeren en aan te tonen.

Nadat het aangepaste formulier gereed is, kunt u het publiceren en beschikbaar maken voor eindgebruikers. De eindgebruikers kunnen het gepubliceerde formulier openen op elk apparaat en in de internetbrowser. Wanneer een adaptief formulier wordt gepubliceerd, worden het formulier en de bijbehorende inhoud gekopieerd van een AEM auteur naar een AEM publicatie-exemplaar. Het formulier wordt via het publicatieexemplaar beschikbaar gesteld voor de eindgebruiker.

U kunt op de volgende manieren een adaptief formulier publiceren:

* [Het adaptieve formulier publiceren als een AEM](../../forms/using/publish-your-adaptive-form.md#publish-the-adaptive-form-as-an-aem-page)
* [Het adaptieve formulier insluiten in een AEM Sites-pagina](#embed-the-adaptive-form-in-an-aem-sites-page)
* [Het adaptieve formulier insluiten in een externe webpagina (een niet-AEM webpagina die buiten AEM wordt gehost)](../../forms/using/publish-your-adaptive-form.md)

## Voordat u begint {#before-you-start}

* **[Een AEM Forms-publicatie-instantie](https://helpx.adobe.com/experience-manager/6-3/forms/using/installing-configuring-aem-forms-osgi.html)** instellen: De publicatie-instantie is een openbare instantie waarbij AEM wordt  [!DNL Forms] uitgevoerd in de publicatiemodus. In een productieomgeving bevindt de publicatie-instantie zich buiten de firewall van de organisatie.
* **[Replicatie en omgekeerde replicatie](https://helpx.adobe.com/experience-manager/6-3/help/sites-deploying/replication.html)** instellen: De replicatie kopieert inhoud van de auteursinstantie aan een publicatieinstantie en keert gebruikersinput (bijvoorbeeld, vorminput) van toe te keren publiceert instantie aan de auteursinstantie.

## Het adaptieve formulier publiceren als een AEM Pagina {#publish-the-adaptive-form-as-an-aem-page}

Wanneer het adaptieve formulier wordt gepubliceerd als een AEM pagina, bevat de hele webpagina alleen het gepubliceerde formulier. U kunt de URL van het aangepaste formulier gebruiken om het formulier te koppelen van een andere webpagina. Het aangepaste formulier **Shipping-address-add-update-form** publiceren als een AEM Pagina:

1. Meld u aan bij AEM [!DNL Forms] auteur-exemplaar en zoek het verzendadres-add-update-form adaptieve formulier in de AEM [!DNL Forms] UI.
   `https://localhost:4502/aem/forms.html/content/dam/formsanddocuments`
1. Selecteer het aangepaste formulier voor het verzendadres-add-update-form en tik op **[!UICONTROL Publish]**. Er wordt een dialoogvenster weergegeven met elementen die betrekking hebben op het adaptieve formulier. Tik op **[!UICONTROL Publish]**. Het adaptieve formulier wordt gepubliceerd en er verschijnt een succesdialoogvenster.
1. Open het formulier op het publicatieexemplaar. Het formulier kan door de eindgebruiker worden ingevuld en verzonden.
   `https://localhost:4503/content/forms/af/shipping-address-add-update-form.html`

## Het aangepaste formulier insluiten in een AEM Sites-pagina {#embed-the-adaptive-form-in-an-aem-sites-page}

AEM [!DNL Forms] stelt formulierontwikkelaars in staat om adaptieve formulieren naadloos in te sluiten in een AEM [!DNL Sites]-pagina. Het ingesloten adaptieve formulier is volledig functioneel en gebruikers kunnen het formulier invullen en verzenden zonder de pagina te verlaten. Hiermee kan de gebruiker in de context van andere elementen op de webpagina blijven en tegelijkertijd met het formulier communiceren.

AEM [!DNL Forms] verstrekt een component, AEM [!DNL Forms] Container, om een adaptief formulier aan een AEM [!DNL Sites] pagina in te bedden. De component is standaard niet zichtbaar in AEM [!DNL Sites]-container. Voer de volgende stappen uit om de AEM [!DNL Forms] Containercomponent in te schakelen en het adaptieve formulier in te sluiten in een AEM [!DNL Sites] Pagina:

1. Maak en open een pagina in de website Web.Retail voor bewerking. Bijvoorbeeld [https://localhost:4502/editor.html/content/we-retail/us/en/user/shipping-and-billing-address.html](https://localhost:4502/editor.html/content/we-retail/us/en/user/shipping-and-billing-address.html). Het aangepaste formulier wordt ingesloten op de pagina [!DNL Sites].

   U kunt het adaptieve formulier ook insluiten in een bestaande pagina [!DNL Site's] van We.Retail. Bijvoorbeeld de pagina ABOUT US [https://localhost:4502/editor.html/content/we-retail/us/en/about-us.html](https://localhost:4502/editor.html/content/we-retail/us/en/about-us.html). Hiermee bespaart u de tijd om een pagina te maken. In de onderstaande stappen wordt de nieuwe pagina gebruikt.

   De website We.Retail wordt verzonden met AEM. Als u de website Web.Retail niet hebt geïnstalleerd, raadpleegt u [We.Retail Reference Implementation](https://helpx.adobe.com/experience-manager/6-3/help/sites-developing/we-retail.html) om de site te installeren.

1. Tik op ![eigenschappen](assets/properties.png) pagina-informatie en selecteer de optie **[!UICONTROL Edit Template]** in de nieuwe webpagina Web.Retail. De sjabloon van de pagina wordt geopend op een nieuw tabblad van de browser.
1. Tik binnen de **[!UICONTROL layout container]** doos en tik ![feedmanagement](assets/feedmanagement.png). Vouw op het tabblad **[!UICONTROL Allowed Components]** de accordeon **[!UICONTROL General]** uit, selecteer de optie **[!UICONTROL AEM Form]** en tik ![save_icon](assets/save_icon.svg). De AEM [!DNL Forms] Containercomponent is ingeschakeld voor de pagina.

1. Open het browsertabblad met AEM [!DNL Sites] pagina geopend in stap 1. Tik op de **[!UICONTROL Drag components here]** doos en tik **+.** Tik in de  **[!UICONTROL Insert New Component]** doos op  **[!UICONTROL AEM Form]**. De component **[!UICONTROL AEM Forms Container]** wordt toegevoegd aan de pagina.
1. Tik op de **[!UICONTROL AEM Forms container]**-component en tik ![configure-icon](assets/configure-icon.svg). Er wordt een dialoogvenster weergegeven met eigenschappen van AEM [!DNL Forms] Container. Blader in het veld **[!UICONTROL Asset Path]** naar het adaptieve formulier voor het verzendadres-add-update-formulier en selecteer dit. Tik ![save_icon](assets/save_icon.svg). Het adaptieve formulier is ingesloten op de pagina.
1. Publiceer zowel het aangepaste formulier als de [!DNL Sites] pagina. Hierna volgt een aantal punten waarmee u rekening kunt houden:

   * Als u de pagina AEM [!DNL Sites] voor het eerst publiceert en deze een ingesloten formulier bevat, publiceert u de pagina [!DNL Sites] en het ingesloten formulier.
   * Als u alleen het ingesloten formulier op een gepubliceerde sitepagina wijzigt, publiceert u het oorspronkelijke formulier en de wijzigingen worden weerspiegeld in de gepubliceerde sitepagina. De gepubliceerde sitepagina bevat een verwijzing naar het formulier en de pagina hoeft niet opnieuw te worden gepubliceerd.
   * Als u de pagina [!DNL Sites] en het ingesloten formulier wijzigt, publiceert u de pagina [!DNL Sites] en het formulier opnieuw.

      ![insluiten-in-aem-sites](assets/embed-in-aem-sites.png)
   Formulier Verzendadres en factuuradres wijzigen toegevoegd aan een AEM [!DNL Sites] pagina.

## Het adaptieve formulier insluiten in een externe webpagina {#embed-the-adaptive-form-in-an-external-webpage}

U kunt een adaptief formulier insluiten in een externe webpagina (een niet-AEM webpagina die buiten AEM wordt gehost) door enkele regels JavaScript in de externe webpagina in te voegen. De JavaScript-code verzendt een HTTP-aanvraag naar de AEM [!DNL Forms]-server voor het adaptieve formulier en de gerelateerde bronnen en voegt het adaptieve formulier toe aan de webpagina. Zie [Het aangepaste formulier insluiten in een externe webpagina](/help/forms/using/embed-adaptive-form-external-web-page.md) voor gedetailleerde stappen.
