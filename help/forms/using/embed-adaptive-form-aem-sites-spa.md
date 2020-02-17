---
title: Een adaptief formulier of interactieve communicatie insluiten in de toepassing Eén pagina voor AEM-sites
seo-title: Aangepaste formulieren of interactieve communicatie insluiten in pagina's met AEM-sites
description: Aangepaste formulieren of interactieve communicatie insluiten in pagina's met AEM-sites. Gebruikers kunnen formulieren invullen en verzenden zonder de sitepagina te verlaten.
seo-description: U kunt adaptieve formulieren of interactieve communicatie insluiten in pagina's met AEM-sites. Gebruikers kunnen formulieren invullen en verzenden zonder de sitepagina te verlaten.
uuid: 4c75494e-e9d2-43b9-bbae-562e0eda8abb
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: a74ed6c1-3006-4baf-bd77-ad4045e23c22
docset: aem65
translation-type: tm+mt
source-git-commit: d12d35bf8355d3069071523427a7794b88c09b13

---


# Een adaptief formulier of interactieve communicatie insluiten in de toepassing Eén pagina voor AEM-sites{#embed-an-adaptive-form-or-interactive-communication-in-aem-sites-single-page-application}

## Overzicht {#overview}

Met AEM Forms kunnen formulierontwikkelaars naadloos adaptieve formulieren en interactieve communicatie insluiten in een AEM Sites Single Page Application (SPA). Het ingesloten adaptieve formulier en de interactieve communicatie zijn volledig functioneel en gebruikers kunnen het formulier invullen en verzenden zonder de pagina te verlaten. Hiermee kan de gebruiker in de context van andere elementen op de webpagina blijven en tegelijkertijd communiceren met het adaptieve formulier of de interactieve communicatie.

In AEM-sites kunt u een adaptief formulier of interactieve communicatie toevoegen met de [AEM Forms SPA Container-component](../../forms/using/embed-adaptive-form-aem-sites-spa.md#af-component)[.](../../forms/using/embed-adaptive-form-aem-sites-spa.md#af-component) Het is een component van Vormen AEM voor Plaatsen SPAs AEM die u aan uw pagina van Plaatsen kunt toevoegen.

Zie Een adaptief formulier of interactieve communicatie insluiten in de pagina [](/help/forms/using/embed-adaptive-form-aem-sites.md)AEM-sites van AEM voor informatie over het insluiten van een adaptief formulier in een niet-SPA.

## Vereisten {#prerequisites}

Als u een adaptief formulier of interactieve communicatie wilt insluiten in een AEM-sites SPA met behulp van de AEM Forms SPA Container-component, moet u ervoor zorgen dat u hebt geïnstalleerd:

* Java SE Development Kit 8 of hoger
* Apache Maven 3.3.1 of hoger
* AEM-auteur-exemplaar
* [AEM Forms 6.4.2 add-on package](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) bij auteurinstantie

## AEM Forms SPA Container-component installeren {#install-aem-forms-spa-container-component}

Voer de volgende stappen uit installeert de component van de Container van AEM Forms SPA:

1. [Kloon of download de component van Vormen AEM voor SPA](https://github.com/Adobe-Marketing-Cloud/aem-forms/tree/master/forms-spa).
1. Installeer de component van Vormen AEM voor SPA. De instructies voor het installeren van de component zijn beschikbaar in het bestand [README.md](https://github.com/Adobe-Marketing-Cloud/aem-forms/tree/master/forms-spa#aem-form-component) .

   De component omvat een component [van de](https://github.com/Adobe-Marketing-Cloud/aem-forms/tree/master/forms-spa/react-component) steekproefReact die kan worden gebruikt om de containercomponent van het KUUROORD met een React-Gebaseerd project van het KUUROORD te integreren.

1. [Kloon of download een React-based project](https://github.com/adobe/aem-sample-we-retail-journal)van het KUUROORD.
1. Integreer de containercomponent van het KUUROORD met een React-Gebaseerd project van het KUUROORD gebruikend de instructies beschikbaar in het [README.md](https://github.com/Adobe-Marketing-Cloud/aem-forms/tree/master/forms-spa/react-component#aem-form-react-component-for-spa---editor) - dossier.

   Na het installeren van de component van de Container van de Vormen AEM SPA en het integreren van de component met een React-based project van het KUUROORD, kunt u een adaptieve vormen en Interactieve Mededelingen in de AEM pagina van Plaatsen inbedden.

## Een adaptief formulier of interactieve communicatie insluiten {#af-component}

Een adaptief formulier of interactieve communicatie insluiten met AEM Forms for SPA Container component:

1. Open de pagina met AEM-sites in de bewerkingsmodus, waarin u een adaptief formulier of interactieve communicatie wilt insluiten.
1. Voeg het **AEM-formulier voor de component SPA** op de pagina in met een van de volgende opties:

   * Tik op de lay-outcontainer op de pagina Sites, tik **+** en selecteer het **AEM-formulier voor de component SPA** .

   * Sleep vanuit het deelvenster Componentbrowser het **AEM-formulier voor de SPA** -component naar de pagina.
   * Zoek een adaptief formulier of interactieve communicatie in de middelenbrowser en sleep het naar de sitepagina. Het sluit de vorm in een Vormen AEM voor de componentencontainer van SPA in.
   >[!NOTE]
   >
   >Het weergeven van meerdere AEM Forms SPA Container-componenten op een pagina wordt niet ondersteund. U kunt meerdere AEM Forms SPA Container op een pagina hebben, maar er wordt slechts één component tegelijk gerenderd. Zorg ervoor dat slechts één component zichtbaar is op een pagina om discrepanties te voorkomen.

1. Tik op de ingesloten AEM Forms SPA Container-component op de sitepagina en tik vervolgens op ![settings_icon](assets/settings_icon.png) op de actiebalk. Het dialoogvenster **AEM Forms SPA Container** bewerken wordt geopend.
1. Geef het volgende op in het dialoogvenster Container **** voor AEM-formulieren bewerken:

   * **** Type element: Selecteer het type element dat u wilt insluiten. De opties zijn **Adaptief formulier** en **Interactieve communicatie**

   * **Middelenpad**: Blader en selecteer het adaptieve formulier of de interactieve communicatie die u wilt insluiten. Het veld wordt automatisch ingevuld als een adaptief formulier of interactieve communicatie wordt ingevoegd met de middelenbrowser.
   * **Kanaal** (alleen interactieve communicatie): Selecteer het type interactief kanaal dat u wilt insluiten. De opties zijn **Webkanaal** en **Afdrukkanaal**.

   * **Thema**: Selecteer een thema waarmee u opmaak definieert voor componenten van uw adaptieve formulier of Interactieve communicatie. Stijlen omvat vormgevingseigenschappen zoals letterstijl, achtergrondkleur, afmetingen en uitlijning.

1. Tik ![](assets/done_icon.png) om de instellingen op te slaan. Het adaptieve formulier of de interactieve communicatie is nu ingesloten in de pagina.

## Ingesloten adaptief formulier en interactieve communicatie publiceren {#publish-embedded-adaptive-form-and-interactive-communication}

Overweeg de volgende scenario&#39;s voor het publiceren van een ingesloten element (adaptief formulier of interactieve communicatie) op de pagina AEM-sites:

* Als u de pagina met AEM-sites voor het eerst publiceert en deze een ingesloten adaptief formulier of interactieve communicatie bevat, publiceert u de pagina Sites en het ingesloten element.
* Als u alleen het ingesloten adaptieve formulier of de interactieve communicatie op een gepubliceerde sitepagina hebt gewijzigd, publiceert u het oorspronkelijke element en de wijzigingen worden weerspiegeld in de gepubliceerde sitepagina. De gepubliceerde pagina Sites bevat een verwijzing naar het element en de pagina hoeft niet opnieuw te worden gepubliceerd.
* Als u de pagina Sites en het ingesloten adaptieve formulier of Interactieve communicatie hebt gewijzigd, publiceert u de pagina Sites en het ingesloten element opnieuw.

## Ingesloten adaptief formulier en interactieve communicatie wijzigen {#modify-embedded-adaptive-form-and-interactive-communication}

Op de pagina met AEM-sites wordt een verwijzing naar het adaptieve formulier en de interactieve communicatie bijgehouden in de AEM Forms Container. Daarom blijven alle configuraties en eigenschappen, zoals het thema, de stijlen en de verzendactie, die in het oorspronkelijke adaptieve formulier en de interactieve communicatie zijn geconfigureerd, behouden in het ingesloten adaptieve formulier en de interactieve communicatie.

Voer een van de volgende handelingen uit als u een configuratie of eigenschap van het ingesloten adaptieve formulier en interactieve communicatie wilt wijzigen.

* Open het oorspronkelijke formulier in adaptieve formulieren of Interactieve communicatie in de respectievelijke editors en wijzig deze.
* Tik in de bewerkingsmodus op het adaptieve formulier of de interactieve communicatie vanuit de sitepagina en tik vervolgens op **Bewerken in een nieuw venster**. Het oorspronkelijke formulier wordt geopend in de bewerkingsmodus.

## Overwegingen en beste praktijken {#considerations-and-best-practices}

Houd rekening met de volgende punten wanneer u adaptieve formulieren insluit in AEM-sitepagina&#39;s:

* Koptekst en voettekst in het oorspronkelijke formulier worden niet opgenomen in het ingesloten formulier.
* Concepten en opmerkingen van gebruikers met ingesloten formulieren worden ondersteund en worden weergegeven op de tabbladen Concepten en Verzendformulieren op de portal Formulieren.
* De verzendactie die op het oorspronkelijke formulier is geconfigureerd, blijft behouden in het ingesloten formulier.
* De ervaring die het richten en A/B tests die op de originele vorm worden gevormd werkt niet in de ingebedde vorm richten. U kunt echter wel de ervaring gebruiken die u op de pagina Sites hebt geselecteerd om verschillende formulieren weer te geven op basis van gebruikersprofielen.
* Als u Adobe Analytics hebt geconfigureerd voor het oorspronkelijke formulier, worden de analysegegevens van het ingesloten formulier vastgelegd in Adobe Analytics. Het is echter niet beschikbaar in het rapport Formulieranalyse.

