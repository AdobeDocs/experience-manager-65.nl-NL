---
title: '"Zelfstudie: Uw adaptieve formulier publiceren"'
seo-title: '"Zelfstudie: Uw adaptieve formulier publiceren"'
description: Het adaptieve formulier publiceren als een AEM-pagina, het formulier insluiten op een pagina met AEM-sites of het adaptieve formulier insluiten in een externe webpagina
seo-description: Het adaptieve formulier publiceren als een AEM-pagina, het formulier insluiten op een pagina met AEM-sites of het adaptieve formulier insluiten in een externe webpagina
uuid: 1b164376-e61a-40aa-9f16-c79d24a72e20
contentOwner: khsingh
topic-tags: introduction
discoiquuid: e24dbd0e-4481-4f9d-9570-3a4046b3ef35
docset: aem65
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317

---


# Zelfstudie: Het aangepaste formulier publiceren {#tutorial-publish-your-adaptive-form}

![](do-not-localize/13-publish-your-adaptive-form-small.png)

Deze zelfstudie is een stap in de [serie Uw eerste adaptieve formulier](https://helpx.adobe.com/experience-manager/6-3/forms/using/create-your-first-adaptive-form.html) maken. U wordt aangeraden de reeks in chronologische volgorde te volgen om het volledige gebruik van de zelfstudie te begrijpen, uit te voeren en aan te tonen.

Nadat het aangepaste formulier gereed is, kunt u het publiceren en beschikbaar maken voor eindgebruikers. De eindgebruikers kunnen het gepubliceerde formulier openen op elk apparaat en in de internetbrowser. Wanneer een adaptief formulier wordt gepubliceerd, worden het formulier en de bijbehorende inhoud gekopieerd van een AEM-auteur-exemplaar naar een AEM-publicatie-exemplaar. Het formulier wordt via het publicatieexemplaar beschikbaar gesteld voor de eindgebruiker.

U kunt op de volgende manieren een adaptief formulier publiceren:

* [Het adaptieve formulier publiceren als een AEM-pagina](../../forms/using/publish-your-adaptive-form.md#publish-the-adaptive-form-as-an-aem-page)
* [Het adaptieve formulier insluiten in een AEM-sitepagina](#embed-the-adaptive-form-in-an-aem-sites-page)
* [Het adaptieve formulier insluiten in een externe webpagina (een niet-AEM-webpagina die buiten AEM wordt gehost)](../../forms/using/publish-your-adaptive-form.md)

## Voordat u begint {#before-you-start}

* **[Een publicatie-instantie](https://helpx.adobe.com/experience-manager/6-3/forms/using/installing-configuring-aem-forms-osgi.html)**voor AEM Forms instellen: De publicatie-instantie is een openbare instantie waarbij AEM Forms wordt uitgevoerd in de publicatiemodus. In een productieomgeving bevindt de publicatie-instantie zich buiten de firewall van de organisatie.
* **[Replicatie en omgekeerde replicatie](https://helpx.adobe.com/experience-manager/6-3/help/sites-deploying/replication.html)**instellen: De replicatie kopieert inhoud van de auteursinstantie aan een publicatieinstantie en keert gebruikersinput (bijvoorbeeld, vorminput) van toe te keren publiceert instantie aan de auteursinstantie.

## Het adaptieve formulier publiceren als een AEM-pagina {#publish-the-adaptive-form-as-an-aem-page}

Als het adaptieve formulier wordt gepubliceerd als een AEM-pagina, bevat de hele webpagina alleen het gepubliceerde formulier. U kunt de URL van het aangepaste formulier gebruiken om het formulier te koppelen van een andere webpagina. Het adaptieve formulier voor het **verzendadres-add-update-form** publiceren als een AEM-pagina:

1. Meld u aan bij de auteur-instantie van AEM Forms en zoek het adaptieve formulier voor het verzendadres en de update in de gebruikersinterface van AEM Forms.
   `https://localhost:4502/aem/forms.html/content/dam/formsanddocuments`
1. Selecteer het aangepaste formulier voor het verzendadres en de update en tik op **Publiceren**. Er wordt een dialoogvenster weergegeven met elementen die betrekking hebben op het adaptieve formulier. Tik op **Publiceren**. Het adaptieve formulier wordt gepubliceerd en er verschijnt een succesdialoogvenster.
1. Open het formulier op het publicatieexemplaar. Het formulier kan door de eindgebruiker worden ingevuld en verzonden.
   `https://localhost:4503/content/forms/af/shipping-address-add-update-form.html`

## Het adaptieve formulier insluiten in een AEM-sitepagina {#embed-the-adaptive-form-in-an-aem-sites-page}

Met AEM Forms kunnen formulierontwikkelaars adaptieve formulieren naadloos insluiten in een AEM-sitepagina. Het ingesloten adaptieve formulier is volledig functioneel en gebruikers kunnen het formulier invullen en verzenden zonder de pagina te verlaten. Hiermee kan de gebruiker in de context van andere elementen op de webpagina blijven en tegelijkertijd met het formulier communiceren.

AEM Forms biedt een component, AEM Forms Container, waarmee u een adaptief formulier kunt insluiten in een pagina met AEM-sites. De component is standaard niet zichtbaar in de container van AEM-sites. Voer de volgende stappen uit om de Containercomponent voor AEM-formulieren in te schakelen en het adaptieve formulier in te sluiten in een pagina met AEM-sites:

1. Maak en open een pagina in de website Web.Retail voor bewerking. Bijvoorbeeld [https://localhost:4502/editor.html/content/we-retail/us/en/user/shipping-and-billing-address.html](https://localhost:4502/editor.html/content/we-retail/us/en/user/shipping-and-billing-address.html). Het aangepaste formulier wordt ingesloten op de sitepagina.

   U kunt het adaptieve formulier ook insluiten in een bestaande pagina van de website Web.Retail. Bijvoorbeeld de pagina ABOUT US [https://localhost:4502/editor.html/content/we-retail/us/en/about-us.html](https://localhost:4502/editor.html/content/we-retail/us/en/about-us.html). Hiermee bespaart u de tijd om een pagina te maken. In de onderstaande stappen wordt de nieuwe pagina gebruikt.

   De website We.Retail wordt geleverd bij AEM. Als u niet de website Web.Retail hebt geïnstalleerd, zie aan [Wij.Detailhandel de Implementatie](https://helpx.adobe.com/experience-manager/6-3/help/sites-developing/we-retail.html) van de Verwijzing installeert de plaats.

1. Tik op de ![eigenschappen](assets/properties.png) van de pagina-informatie en selecteer de optie Sjabloon **** bewerken op de nieuwe webpagina Web.Retail. De sjabloon van de pagina wordt geopend op een nieuw tabblad van de browser.
1. Tik in het vak van de **lay-outcontainer** en tik op ![feedbackbeheer](assets/feedmanagement.png). Vouw op het tabblad **Toegestane componenten** de accordeon **Algemeen** uit, selecteer de optie **AEM-formulier** en tik op ![](assets/save_icon.svg). De component AEM Forms Container is ingeschakeld voor de pagina.

1. Open het browsertabblad met de pagina AEM-sites die is geopend in stap 1. Tik hier **op de componenten** Slepen en tik op **+.** Tik in het vak Nieuwe component **** invoegen op **AEM-formulier.** De **component AEM Forms Container** wordt aan de pagina toegevoegd.
1. Tik op de containercomponent **AEM Forms** en tik op ![](assets/configure-icon.svg). Er wordt een dialoogvenster weergegeven met eigenschappen van de container van AEM Forms. Blader in het veld **Middelenpad** naar het adaptieve formulier voor het verzendadres en de update. Tik op ![](assets/save_icon.svg). Het adaptieve formulier is ingesloten op de pagina.
1. Publiceer zowel het aangepaste formulier als de sitepagina. Hierna volgt een aantal punten waarmee u rekening kunt houden:

   * Als u de pagina met AEM-sites voor het eerst publiceert en deze een ingesloten formulier bevat, publiceert u de pagina met sites en het ingesloten formulier.
   * Als u alleen het ingesloten formulier op een gepubliceerde sitepagina wijzigt, publiceert u het oorspronkelijke formulier en de wijzigingen worden weerspiegeld in de gepubliceerde sitepagina. De gepubliceerde sitepagina bevat een verwijzing naar het formulier en de pagina hoeft niet opnieuw te worden gepubliceerd.
   * Als u de sitepagina en het ingesloten formulier wijzigt, publiceert u de sitepagina en het formulier opnieuw.
   ![insluiten-in-aem-sites](assets/embed-in-aem-sites.png)

   Formulier Verzendadres en factuuradres wijzigen toegevoegd aan een pagina voor AEM-sites.

## Het adaptieve formulier insluiten in een externe webpagina {#embed-the-adaptive-form-in-an-external-webpage}

U kunt een adaptief formulier insluiten in een externe webpagina (een niet-AEM-webpagina die buiten AEM wordt gehost) door enkele regels JavaScript in te voegen in de externe webpagina. De JavaScript-code verzendt een HTTP-aanvraag naar de AEM Forms-server voor het adaptieve formulier en de gerelateerde bronnen en voegt het adaptieve formulier toe aan de webpagina. Zie Het aangepaste formulier [insluiten op een externe webpagina](/help/forms/using/embed-adaptive-form-external-web-page.md)voor gedetailleerde stappen.
