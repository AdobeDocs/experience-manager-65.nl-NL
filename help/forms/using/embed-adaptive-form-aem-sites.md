---
title: Een adaptief formulier of interactieve communicatie insluiten in AEM sitepagina
description: U kunt adaptieve formulieren insluiten in AEM sitepagina's. Gebruikers kunnen formulieren invullen en verzenden zonder de sitepagina's te verlaten.
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author, interactive-communications
feature: Adaptive Forms,Foundation Components
exl-id: 00ee7929-649f-4cbb-be79-ba13ac73a16d
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '1141'
ht-degree: 0%

---

# Een adaptief formulier of interactieve communicatie insluiten in AEM sitepagina {#embed-an-adaptive-form-or-interactive-communication-in-aem-sites-page}

<span class="preview"> de Adobe adviseert gebruikend de moderne en verlengbare gegevens vangen [ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=nl-NL) voor [ het creëren van nieuwe Aangepaste Forms ](/help/forms/using/create-an-adaptive-form-core-components.md) of [ het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites ](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/services/embed-adaptive-form-aem-sites.html?lang=nl-NL) |
| AEM 6,5 | Dit artikel |


## Overzicht {#overview}

Met AEM Forms kunnen ontwikkelaars van formulieren adaptieve formulieren en interactieve communicatie naadloos insluiten in een AEM Sites-pagina of een webpagina die buiten AEM wordt gehost. Het ingesloten adaptieve formulier en de interactieve communicatie zijn volledig functioneel en gebruikers kunnen het formulier invullen en verzenden zonder de pagina te verlaten. Hiermee kan de gebruiker in de context van andere elementen op de webpagina blijven en tegelijkertijd communiceren met het formulier of de interactieve communicatie.

Voor informatie over het inbedden van een adaptieve vorm in een externe Web-pagina, zie [ inbedden adaptieve vorm in externe Web-pagina ](/help/forms/using/embed-adaptive-form-external-web-page.md).

Op de AEM Sites-pagina kunt u een adaptief formulier of interactieve communicatie toevoegen met:

* **[de component van de Container van AEM Forms](/help/forms/using/embed-adaptive-form-aem-sites.md#af-component)**
AEM Forms biedt een component die u aan uw sitepagina&#39;s kunt toevoegen. Met de AEM Forms Container-component kunt u een adaptief formulier en interactieve communicatie insluiten.

* **[browser van Activa](/help/forms/using/embed-adaptive-form-aem-sites.md#asset-browser)**
Alle formulieren en interactieve communicatie die u maakt, zijn beschikbaar onder Assets. U kunt het formulier slepen en neerzetten als middel op de pagina.

## Vereisten {#prerequisites}

Als u een adaptief formulier of interactieve communicatie wilt insluiten in een AEM sitepagina die een bewerkbare sjabloon gebruikt, moet u ervoor zorgen dat de AEM formuliercomponent is geconfigureerd als een toegestane component in de bijbehorende sjabloon. Voor meer informatie, zie **Beleid &amp; Eigenschappen (de Container van de Lay-out)** sectie in [ Creërend de Malplaatjes van de Pagina ](/help/sites-authoring/templates.md).

Als er een pagina van Plaatsen gebruikend een statisch malplaatje is, moet u het in het paragraafsysteem van de plaatspagina vormen. Zie [ Vormende Componenten op de Wijze van het Ontwerp ](/help/sites-authoring/default-components-designmode.md) voor meer informatie.

## Een adaptief formulier of interactieve communicatie insluiten {#af-component}

Een adaptief formulier of interactieve communicatie insluiten met AEM Forms Container-component:

1. Open de pagina AEM sites in de bewerkingsmodus waarin u een adaptief formulier of interactieve communicatie wilt insluiten.
1. Sleep vanuit het deelvenster Componentbrowser de AEM Forms Container-component naar de pagina.

   U kunt ook zoeken naar een adaptief formulier of interactieve communicatie in de Assets-browser en het formulier naar de Sites-pagina slepen. Het formulier wordt ingesloten in een AEM Forms-container.

   >[!NOTE]
   >
   >Meerdere AEM Forms Container-componenten op een pagina worden niet ondersteund.

1. Selecteer de ingebedde component van de Container van AEM Forms in de plaatspagina, en selecteer dan ![ settings_icon ](assets/settings_icon.png) op de actiebar. Het dialoogvenster **[!UICONTROL Edit AEM Forms Container]** wordt geopend.
1. Geef het volgende op in het dialoogvenster AEM Forms-container bewerken.

   * **Type van Activa:** selecteer het type van activa om in te bedden. De opties zijn adaptieve vorm en interactieve communicatie
   * **Weg van Activa**: Blader en selecteer de adaptieve vorm of de interactieve mededeling om in te bedden. Deze wordt automatisch ingevuld als u deze uit de Assets-browser hebt verwijderd.
   * (Alleen adaptieve vorm) **Post-verzending**: selecteer de actie die moet worden geactiveerd bij het verzenden van formulieren. U kunt ervoor kiezen om een bedankbericht of een pagina voor bedankt weer te geven.

      * **Dank u Bericht**: Schrijf een bericht gebruikend de rijke tekstredacteur om op vormvoorlegging te tonen. Deze optie is alleen beschikbaar als u een bedankbericht wilt weergeven.
      * **Dank u Pagina**: doorblader en selecteer de pagina om op vormvoorlegging te tonen. Deze optie is alleen beschikbaar wanneer u een pagina voor bedankt weergeeft.
      * **verfrist Pagina op Verzending**: Laat toe zodat kunt u de pagina verfrissen die de ingebedde adaptieve vorm bevat om te tonen bedankt u pagina. Anders vervangt de pagina Hartelijk dank het aangepaste formulier in de AEM Forms-container, zonder de pagina te vernieuwen. Deze optie is alleen beschikbaar wanneer u een pagina voor bedankt weergeeft.

   * **Thema**: Selecteer een thema dat het stileren voor componenten van uw adaptieve vorm of interactieve mededeling bepaalt. Stijlen omvat vormgevingseigenschappen zoals letterstijl, achtergrondkleur, afmetingen en uitlijning.
   * **Hoogte**: Specificeer de hoogte van de container. Laat deze leeg om de grootte van de container automatisch te wijzigen.
   * **CSS de bibliotheek van de Cliënt**: Specificeer weg aan een CSS cliëntbibliotheek.

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
* Selecteer het adaptieve formulier of de interactieve communicatie vanuit de sitepagina in de bewerkingsmodus en selecteer vervolgens **[!UICONTROL Edit in a new window]** . Het oorspronkelijke formulier wordt geopend in de bewerkingsmodus die u kunt wijzigen.

>[!NOTE]
>
>De wijzigingen in het oorspronkelijke adaptieve formulier of de interactieve communicatie worden automatisch doorgevoerd in het ingesloten formulier. U kunt het aangepaste formulier, de interactieve communicatie of de sitepagina echter opnieuw publiceren om de wijzigingen in de gepubliceerde pagina weer te geven.

## Overwegingen en beste praktijken {#considerations-and-best-practices}

Houd rekening met de volgende punten wanneer u adaptieve formulieren insluit in AEM sitepagina&#39;s:

* Koptekst en voettekst in het oorspronkelijke formulier worden niet opgenomen in het ingesloten formulier.
* Concepten en opmerkingen van gebruikers met ingesloten formulieren worden ondersteund en kunnen worden weergegeven op de tabbladen Concepten en Verzonden Forms op de portal Formulieren.
* De verzendactie die op het oorspronkelijke formulier is geconfigureerd, blijft behouden in het ingesloten formulier.
* De ervaring die het richten en A/B tests die op de originele vorm worden gevormd werkt niet in de ingebedde vorm richten. U kunt echter de pagina Sites gebruiken om verschillende formulieren weer te geven op basis van gebruikersprofielen.
* Als u Adobe Analytics hebt geconfigureerd voor het oorspronkelijke formulier, worden de analysegegevens van het ingesloten formulier vastgelegd in Adobe Analytics. Het is echter niet beschikbaar in het rapport Formulieranalyse.
