---
title: Een adaptief formulier of interactieve communicatie insluiten in AEM sitepagina
seo-title: Een adaptief formulier of interactieve communicatie insluiten in AEM sitepagina
description: U kunt adaptieve formulieren insluiten in AEM sitepagina's. Gebruikers kunnen formulieren invullen en verzenden zonder de sitepagina's te verlaten.
seo-description: U kunt adaptieve formulieren insluiten in AEM sitepagina's. Gebruikers kunnen formulieren invullen en verzenden zonder de sitepagina's te verlaten.
uuid: 59b49e2f-6d95-42e5-b31e-fc40936c42d2
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author, interactive-communications
discoiquuid: 43362643-69cd-4006-a613-f998c79eeddc
translation-type: tm+mt
source-git-commit: 46f2ae565fe4a8cfea49572eb87a489cb5d9ebd7
workflow-type: tm+mt
source-wordcount: '1105'
ht-degree: 0%

---


# Een adaptief formulier of interactieve communicatie insluiten in AEM sitepagina {#embed-an-adaptive-form-or-interactive-communication-in-aem-sites-page}

## Overzicht {#overview}

Met AEM Forms kunnen ontwikkelaars van formulieren adaptieve formulieren en interactieve communicatie naadloos insluiten in een AEM Sites-pagina of een webpagina die buiten AEM wordt gehost. Het ingesloten adaptieve formulier en de interactieve communicatie zijn volledig functioneel en gebruikers kunnen het formulier invullen en verzenden zonder de pagina te verlaten. Hiermee kan de gebruiker in de context van andere elementen op de webpagina blijven en tegelijkertijd communiceren met het formulier of de interactieve communicatie.

Zie Aangepast formulier [insluiten in externe webpagina](/help/forms/using/embed-adaptive-form-external-web-page.md)voor informatie over het insluiten van een adaptief formulier in een externe webpagina.

Op de AEM Sites-pagina kunt u een adaptief formulier of interactieve communicatie toevoegen met:

* **[AEM Forms Container-component](/help/forms/using/embed-adaptive-form-aem-sites.md#af-component)** AEM Forms biedt een component die u aan uw sitepagina&#39;s kunt toevoegen. Met de AEM Forms Container-component kunt u een adaptief formulier en interactieve communicatie insluiten.

* **[Bandenbrowser](/help/forms/using/embed-adaptive-form-aem-sites.md#asset-browser)** Alle formulieren en interactieve communicatie die u maakt, zijn beschikbaar onder Elementen. U kunt het formulier slepen en neerzetten als middel op de pagina.

## Vereisten {#prerequisites}

Als u een adaptief formulier of interactieve communicatie wilt insluiten in een AEM sitepagina die een bewerkbare sjabloon gebruikt, moet u ervoor zorgen dat de AEM formuliercomponent is geconfigureerd als een toegestane component in de bijbehorende sjabloon. Zie de sectie **Beleid en eigenschappen (container van layout)** in [Paginasjablonen](/help/sites-authoring/templates.md)maken voor meer informatie.

In het geval van een pagina van Plaatsen die een statisch malplaatje gebruikt, moet u het in het paragraafsysteem van de plaatspagina vormen. Zie Componenten [configureren in Ontwerpmodus](/help/sites-authoring/default-components-designmode.md) voor meer informatie.

## Een adaptief formulier of interactieve communicatie insluiten {#af-component}

Een adaptief formulier of interactieve communicatie insluiten met AEM Forms Container-component:

1. Open de pagina AEM sites in de bewerkingsmodus waarin u een adaptief formulier of interactieve communicatie wilt insluiten.
1. Sleep vanuit het deelvenster Componentbrowser de AEM Forms Container-component naar de pagina.

   U kunt ook zoeken naar een adaptief formulier of interactieve communicatie in de middelenbrowser en het formulier slepen en neerzetten op de sitepagina. Het formulier wordt ingesloten in een AEM Forms-container.

   >[!NOTE]
   >
   >Meerdere AEM Forms Container-componenten op een pagina worden niet ondersteund.

1. Tik op de ingesloten AEM Forms Container-component op de sitepagina en tik vervolgens op ![settings_icon](assets/settings_icon.png) op de actiebalk. Het **[!UICONTROL Edit AEM Forms Container]** dialoogvenster wordt geopend.
1. Geef het volgende op in het dialoogvenster AEM Forms-container bewerken.

   * **Type element:** Selecteer het type element dat u wilt insluiten. De opties zijn adaptieve vorm en interactieve communicatie
   * **Middelenpad**: Blader naar het aangepaste formulier of de interactieve communicatie die u wilt insluiten en selecteer dit. Deze wordt automatisch ingevuld als u deze uit de middelenbrowser hebt verwijderd.
   * (Alleen adaptief formulier) **Na verzending**: Selecteer de actie die moet worden geactiveerd bij het verzenden van het formulier. U kunt ervoor kiezen om een bedankbericht of een pagina voor bedankt weer te geven.

      * **Bedankt voor uw bericht**: Schrijf een bericht met de teksteditor Rich die moet worden weergegeven bij het verzenden van formulieren. Deze optie is alleen beschikbaar als u een bedankbericht wilt weergeven.
      * **Hartelijk dank, pagina**: Blader en selecteer de pagina die u wilt weergeven bij het verzenden van het formulier. Deze optie is alleen beschikbaar wanneer u een pagina voor bedankt weergeeft.
      * **Pagina vernieuwen bij verzending**: Schakel deze optie in om de pagina met het ingesloten adaptieve formulier te vernieuwen en de pagina voor bedankt weer te geven. Anders vervangt de pagina Hartelijk dank het aangepaste formulier in de AEM Forms-container, zonder de pagina te vernieuwen. Deze optie is alleen beschikbaar wanneer u een pagina voor bedankt weergeeft.
   * **Thema**: Selecteer een thema waarmee u stijlen definieert voor onderdelen van uw adaptieve formulier of interactieve communicatie. Stijlen omvat vormgevingseigenschappen zoals letterstijl, achtergrondkleur, afmetingen en uitlijning.
   * **Hoogte**: Geef de hoogte van de container op. Laat deze leeg om de grootte van de container automatisch te wijzigen.
   * **CSS-clientbibliotheek**: Geef het pad naar een CSS-clientbibliotheek op.


1. Sla de instellingen op. Het aangepaste formulier of de interactieve communicatie is nu ingesloten op de pagina.

## Ingesloten adaptief formulier en interactieve communicatie publiceren {#publishing-embedded-adaptive-form-and-interactive-communication}

Laten we de volgende scenario&#39;s in overweging nemen voor het publiceren van een ingesloten element (adaptief formulier of interactieve communicatie) op AEM sitepagina:

* Als u de pagina met AEM sites voor het eerst publiceert en deze een ingesloten adaptief formulier of interactieve communicatie bevat, publiceert u de pagina met sites en het ingesloten element.
* Als u alleen het ingesloten adaptieve formulier of de interactieve communicatie op een gepubliceerde sitepagina hebt gewijzigd, publiceert u het oorspronkelijke element en de wijzigingen worden weerspiegeld in de gepubliceerde sitepagina. De gepubliceerde sitepagina bevat een verwijzing naar het element en de pagina hoeft niet opnieuw te worden gepubliceerd.
* Als u de sitepagina en het ingesloten adaptieve formulier of interactieve communicatie hebt gewijzigd, publiceert u de sitepagina en het ingesloten element opnieuw.

## Ingesloten adaptief formulier en interactieve communicatie aanpassen {#modifying-embedded-adaptive-form-and-interactive-communication}

AEM sitepagina bevat een verwijzing naar het adaptieve formulier en de interactieve communicatie in de AEM Forms Container. Daarom blijven alle configuraties en eigenschappen, zoals het thema, de stijlen en de verzendactie, die zijn geconfigureerd in het oorspronkelijke adaptieve formulier en de interactieve communicatie, behouden in het ingesloten adaptieve formulier en de interactieve communicatie.

Voer een van de volgende handelingen uit als u een configuratie of eigenschap van het ingesloten adaptieve formulier en interactieve communicatie wilt wijzigen.

* Open het oorspronkelijke formulier in adaptieve formulieren of interactieve communicatie in de respectievelijke editors en wijzig deze.
* Tik in de bewerkingsmodus op het aangepaste formulier of de interactieve communicatie vanuit de sitepagina en tik vervolgens op **[!UICONTROL Edit in a new window]**. Het oorspronkelijke formulier wordt geopend in de bewerkingsmodus die u kunt wijzigen.

>[!NOTE]
>
>De wijzigingen in het oorspronkelijke adaptieve formulier of de interactieve communicatie worden automatisch doorgevoerd in het ingesloten formulier. U kunt het aangepaste formulier, de interactieve communicatie of de sitepagina echter opnieuw publiceren om de wijzigingen in de gepubliceerde pagina weer te geven.

## Considerations and best practices {#considerations-and-best-practices}

Houd rekening met de volgende punten wanneer u adaptieve formulieren insluit in AEM sitepagina&#39;s:

* Koptekst en voettekst in het oorspronkelijke formulier worden niet opgenomen in het ingesloten formulier.
* Concepten en opmerkingen van gebruikers met ingesloten formulieren worden ondersteund en kunnen worden weergegeven op de tabbladen Concepten en Verzonden Forms op de portal Formulieren.
* De verzendactie die op het oorspronkelijke formulier is geconfigureerd, blijft behouden in het ingesloten formulier.
* De ervaring die het richten en A/B tests die op de originele vorm worden gevormd werkt niet in de ingebedde vorm richten. U kunt echter de pagina Sites gebruiken om verschillende formulieren weer te geven op basis van gebruikersprofielen.
* Als u Adobe Analytics hebt geconfigureerd voor het oorspronkelijke formulier, worden de analysegegevens van het ingesloten formulier vastgelegd in Adobe Analytics. Het is echter niet beschikbaar in het rapport Formulieranalyse.

