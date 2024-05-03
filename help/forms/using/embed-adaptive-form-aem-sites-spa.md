---
title: Een adaptief formulier of interactieve communicatie insluiten in AEM Sites-toepassing voor één pagina
description: Aangepaste formulieren of interactieve communicatie insluiten in AEM Sites-pagina's. Gebruikers kunnen formulieren invullen en verzenden zonder de sitepagina te verlaten.
topic-tags: author, interactive-communications
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Adaptive Forms
exl-id: b549f176-409a-4d81-8c2b-73d0dd0c6649
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '1107'
ht-degree: 0%

---

# Een adaptief formulier of interactieve communicatie insluiten in AEM Sites-toepassing voor één pagina{#embed-an-adaptive-form-or-interactive-communication-in-aem-sites-single-page-application}

<span class="preview"> Adobe beveelt aan moderne en uitbreidbare gegevensvastlegging te gebruiken [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) for [nieuwe Adaptieve Forms maken](/help/forms/using/create-an-adaptive-form-core-components.md) of [Aangepaste Forms toevoegen aan AEM Sites-pagina&#39;s](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

## Overzicht {#overview}

Met AEM Forms kunnen ontwikkelaars van formulieren adaptieve formulieren en interactieve communicatie naadloos insluiten in een AEM Sites Single Page Application (SPA). Het ingesloten adaptieve formulier en de interactieve communicatie zijn volledig functioneel en gebruikers kunnen het formulier invullen en verzenden zonder de pagina te verlaten. Hiermee kan de gebruiker in de context van andere elementen op de webpagina blijven en tegelijkertijd communiceren met het adaptieve formulier of de interactieve communicatie.

In AEM Sites-toepassing voor één pagina kunt u een adaptief formulier of interactieve communicatie toevoegen met de opdracht [AEM Forms SPA Containercomponent](../../forms/using/embed-adaptive-form-aem-sites-spa.md#af-component)[.](../../forms/using/embed-adaptive-form-aem-sites-spa.md#af-component) Het is een AEM Forms-component voor AEM Sites-SPA die u kunt toevoegen aan uw sitepagina.

Voor informatie over het insluiten van een adaptief formulier in een niet-SPA AEM Sites raadpleegt u [Een adaptief formulier of interactieve communicatie insluiten in een AEM Sites-pagina](/help/forms/using/embed-adaptive-form-aem-sites.md).

## Vereisten {#prerequisites}

Als u een adaptief formulier of interactieve communicatie wilt insluiten in AEM sites SPA de AEM Forms SPA Container-component te gebruiken, moet u controleren of u:

* Java SE Development Kit 8 of hoger
* Apache Maven 3.3.1 of hoger
* AEM
* [AEM Forms 6.4.2-invoegtoepassing](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) op instantie van auteur

## AEM Forms SPA Container-component installeren {#install-aem-forms-spa-container-component}

Voer de volgende stappen uit om de AEM Forms SPA Container-component te installeren:

1. [De AEM Forms-component klonen of downloaden voor SPA](https://github.com/Adobe-Marketing-Cloud/aem-forms/tree/master/forms-spa).
1. Installeer de AEM Forms-component voor SPA. De instructies voor het installeren van de component zijn beschikbaar in het dialoogvenster [README.md](https://github.com/Adobe-Marketing-Cloud/aem-forms/tree/master/forms-spa#aem-form-component) bestand.

   De component bevat een [sample React component](https://github.com/Adobe-Marketing-Cloud/aem-forms/tree/master/forms-spa/react-component) die kunnen worden gebruikt om SPA containercomponent met een React-Gebaseerd SPA project te integreren.

1. [Klonen of een React-gebaseerd SPA project downloaden](https://github.com/adobe/aem-sample-we-retail-journal).
1. Integreer SPA containercomponent met een React-gebaseerd SPA project gebruikend de instructies beschikbaar in [README.md](https://github.com/Adobe-Marketing-Cloud/aem-forms/tree/master/forms-spa/react-component#aem-form-react-component-for-spa---editor) bestand.

   Nadat u de AEM Forms SPA Container-component hebt geïnstalleerd en de component hebt geïntegreerd met een React-gebaseerd SPA-project, kunt u adaptieve formulieren en interactieve communicatie insluiten in de AEM Sites-pagina.

## Een adaptief formulier of interactieve communicatie insluiten {#af-component}

Een adaptief formulier of interactieve communicatie insluiten met AEM Forms for SPA Container-component:

1. Open de pagina AEM sites in de bewerkingsmodus waarin u een adaptief formulier of interactieve communicatie wilt insluiten.
1. Voeg de **AEM formulier voor SPA** op de pagina met een van de volgende opties:

   * Selecteer de lay-outcontainer op de pagina van Plaatsen, selecteer **+** en selecteert u de **AEM formulier voor SPA** component.

   * Sleep vanuit het deelvenster Componentbrowser de **AEM formulier voor SPA** op de pagina.
   * Zoek een adaptief formulier of interactieve communicatie in de middelenbrowser en sleep het naar de sitepagina. Het formulier wordt ingesloten in een AEM Forms voor SPA componentcontainer.

   >[!NOTE]
   >
   >Het weergeven van meerdere AEM Forms SPA Container-componenten op een pagina wordt niet ondersteund. U kunt meerdere AEM Forms SPA Container op een pagina plaatsen, maar er wordt slechts één component tegelijk gerenderd. Zorg ervoor dat slechts één component zichtbaar is op een pagina om discrepanties te voorkomen.

1. Selecteer de ingesloten AEM Forms SPA Container-component op de sitepagina en selecteer vervolgens ![settings_icon](assets/settings_icon.png) op de actiebalk. De **AEM Forms SPA-container bewerken** wordt geopend.
1. In de **AEM Forms-container bewerken** geeft u het volgende op:

   * **Type element:** Selecteer het type element dat u wilt insluiten. De opties zijn **Adaptief formulier** en **Interactieve communicatie**

   * **Middelpad**: Blader en selecteer het adaptieve formulier of de interactieve communicatie die u wilt insluiten. Het veld wordt automatisch ingevuld als een adaptief formulier of interactieve communicatie wordt ingevoegd met de middelenbrowser.
   * **Kanaal** (Alleen interactieve communicatie): selecteer het type interactief kanaal dat u wilt insluiten. De opties zijn **Webkanaal** en **Afdrukkanaal**.

   * **Thema**: Selecteer een thema waarmee u opmaak definieert voor componenten van uw adaptieve formulier of Interactieve communicatie. Stijlen omvat vormgevingseigenschappen zoals letterstijl, achtergrondkleur, afmetingen en uitlijning.

1. Selecteren ![done_icon](assets/done_icon.png) om de instellingen op te slaan. Het adaptieve formulier of de interactieve communicatie is nu ingesloten in de pagina.

## Ingesloten adaptief formulier en interactieve communicatie publiceren {#publish-embedded-adaptive-form-and-interactive-communication}

Overweeg de volgende scenario&#39;s voor het publiceren van een ingesloten element (adaptief formulier of interactieve communicatie) op de AEM Sites-pagina:

* Als u de AEM Sites-pagina voor het eerst publiceert en een ingesloten adaptief formulier of interactieve communicatie bevat, publiceert u de pagina Sites en het ingesloten element.
* Als u alleen het ingesloten adaptieve formulier of de interactieve communicatie op een gepubliceerde sitepagina hebt gewijzigd, publiceert u het oorspronkelijke element en de wijzigingen worden weerspiegeld in de gepubliceerde sitepagina. De gepubliceerde pagina Sites bevat een verwijzing naar het element en de pagina hoeft niet opnieuw te worden gepubliceerd.
* Als u de pagina Sites en het ingesloten adaptieve formulier of Interactieve communicatie hebt gewijzigd, publiceert u de pagina Sites en het ingesloten element opnieuw.

## Ingesloten adaptief formulier en interactieve communicatie wijzigen {#modify-embedded-adaptive-form-and-interactive-communication}

AEM sitepagina bevat een verwijzing naar het adaptieve formulier en de interactieve communicatie in de AEM Forms Container. Daarom blijven alle configuraties en eigenschappen, zoals het thema, de stijlen en de verzendactie, die in het oorspronkelijke adaptieve formulier en de interactieve communicatie zijn geconfigureerd, behouden in het ingesloten adaptieve formulier en de interactieve communicatie.

Voer een van de volgende handelingen uit als u een configuratie of eigenschap van het ingesloten adaptieve formulier en interactieve communicatie wilt wijzigen.

* Open het oorspronkelijke formulier in adaptieve formulieren of Interactieve communicatie in de respectievelijke editors en wijzig deze.
* Selecteer het adaptieve formulier of de interactieve communicatie vanuit de sitepagina in de bewerkingsmodus en selecteer **Bewerken in een nieuw venster**. Het oorspronkelijke formulier wordt geopend in de bewerkingsmodus.

## Overwegingen en beste praktijken {#considerations-and-best-practices}

Houd rekening met de volgende punten wanneer u adaptieve formulieren insluit in AEM sitepagina&#39;s:

* Koptekst en voettekst in het oorspronkelijke formulier worden niet opgenomen in het ingesloten formulier.
* Concepten en opmerkingen van gebruikers met ingesloten formulieren worden ondersteund en kunnen worden weergegeven op de tabbladen Concepten en Verzonden Forms op de portal Formulieren.
* De verzendactie die op het oorspronkelijke formulier is geconfigureerd, blijft behouden in het ingesloten formulier.
* De ervaring die het richten en A/B tests die op de originele vorm worden gevormd werkt niet in de ingebedde vorm richten. U kunt echter wel de ervaring gebruiken die u op de pagina Sites hebt geselecteerd om verschillende formulieren weer te geven op basis van gebruikersprofielen.
* Als u Adobe Analytics hebt geconfigureerd voor het oorspronkelijke formulier, worden de analysegegevens van het ingesloten formulier vastgelegd in Adobe Analytics. Het is echter niet beschikbaar in het rapport Formulieranalyse.
