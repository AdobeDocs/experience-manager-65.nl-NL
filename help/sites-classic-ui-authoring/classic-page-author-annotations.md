---
title: Annotaties bij het bewerken van een pagina
seo-title: Annotaties bij het bewerken van een pagina
description: Het toevoegen van inhoud aan de pagina's van uw website is vaak onderwerp van besprekingen alvorens het eigenlijk wordt gepubliceerd. Om dit te helpen, staan vele componenten direct met inhoud verwant u toe om een aantekening toe te voegen.
seo-description: Het toevoegen van inhoud aan de pagina's van uw website is vaak onderwerp van besprekingen alvorens het eigenlijk wordt gepubliceerd. Om dit te helpen, staan vele componenten direct met inhoud verwant u toe om een aantekening toe te voegen.
page-status-flag: de-activated
uuid: d8d6ba76-f2aa-4044-98bf-5d506742d90d
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 9bee0197-f275-49cc-922d-62cba826c4e5
translation-type: tm+mt
source-git-commit: c8a02ad9fc33e963d2c760840e70c40ede988054

---


# Annotaties bij het bewerken van een pagina{#annotations-when-editing-a-page}

Het toevoegen van inhoud aan de pagina&#39;s van uw website is vaak onderwerp van besprekingen alvorens het eigenlijk wordt gepubliceerd. Om dit te helpen, staan vele componenten direct met inhoud verwant (in tegenstelling, bijvoorbeeld, aan lay-out) u toe om een aantekening toe te voegen.

Een annotatie plaatst een gekleurde markering/notitie op de pagina. Met de annotatie kunt u (of andere gebruikers) opmerkingen en/of vragen laten voor andere auteurs/revisoren.

>[!NOTE]
>
>De definitie van een afzonderlijk componenttype bepaalt of het toevoegen van een aantekening (ANNOTATION) mogelijk is (of niet) op instanties van die component.

>[!NOTE]
>
>Annotaties die zijn gemaakt in de klassieke gebruikersinterface worden ook weergegeven in de gebruikersinterface voor geoptimaliseerde aanrakingen. Schetsen zijn echter specifiek voor de gebruikersinterface en worden alleen weergegeven in de gebruikersinterface waarin ze zijn gemaakt.

>[!CAUTION]
>
>Als u een bron verwijdert (bijvoorbeeld alinea), worden alle annotaties en schetsen verwijderd die aan die bron zijn gekoppeld. ongeacht hun positie op de pagina als geheel.

>[!NOTE]
>
>Afhankelijk van uw vereisten kunt u ook een workflow ontwikkelen om meldingen te verzenden wanneer annotaties worden toegevoegd, bijgewerkt of verwijderd.

## Annotaties {#annotations}

Afhankelijk van het alineaontwerp is annotatie beschikbaar als een optie in het contextmenu (meestal de rechtermuisknop als deze zich boven de vereiste alinea bevindt) of als een knop op de bewerkbalk voor alinea&#39;s.

Selecteer in beide gevallen **Notitie**. Er wordt een gekleurde notitie toegepast op de alinea. U bevindt zich direct in de modus Bewerken, zodat u rechtstreeks tekst kunt toevoegen:

![chlimage_1-137](assets/chlimage_1-137.png)

U kunt de annotatie naar een nieuwe positie op de pagina verplaatsen. Klik op de bovenste rand en houd de annotatie ingedrukt en sleep deze tegelijkertijd naar de nieuwe positie. Dit kan overal op de pagina zijn, hoewel het doorgaans zinvol is om de pagina op een of andere manier met de alinea verbonden te houden.

Annotaties (inclusief bijbehorende schetsen) worden ook opgenomen in alle kopieer-, knip- of verwijderhandelingen die worden uitgevoerd op de alinea waaraan ze zijn gehecht; voor kopieer- of kniphandelingen behoudt de positie van de annotatie (en de bijbehorende schetsen) ten opzichte van de oorspronkelijke alinea.

U kunt de grootte van de annotatie ook vergroten of verkleinen door de rechterbenedenhoek te slepen.

Voor traceringsdoeleinden geeft de voettekstregel de gebruiker aan die de annotatie heeft gemaakt en de datum. Volgende auteurs kunnen dezelfde annotatie bewerken (de voettekst wordt bijgewerkt) of een nieuwe annotatie voor dezelfde alinea maken.

Bevestiging wordt aangevraagd wanneer u de annotatie verwijdert (als u een annotatie verwijdert, worden ook de aan die annotatie gekoppelde schetsen verwijderd).

Met de drie pictogrammen linksboven kunt u de annotatie minimaliseren (samen met eventuele verwante schetsen), de kleur wijzigen en schetsen toevoegen.

>[!NOTE]
>
>Annotaties zijn alleen zichtbaar in de modus Bewerken van de auteursomgeving.
>
>Ze zijn niet zichtbaar in een publicatieomgeving en ook niet in de modus Voorbeeld of Ontwerpen die beschikbaar is in een ontwerpomgeving.

>[!NOTE]
>
>Annotaties kunnen niet worden toegevoegd aan een pagina die is vergrendeld door een andere gebruiker.

## Annotatieskettes {#annotation-sketches}

>[!NOTE]
>
>Schetsen zijn niet beschikbaar in Internet Explorer, dus:
>
>* het pictogram wordt niet weergegeven.
>* bestaande schetsen die in een andere browser zijn gemaakt, worden niet weergegeven.
>



Schetsen zijn een functie van annotaties waarmee u overal in het browservenster eenvoudige lijnafbeeldingen kunt maken (zichtbaar gedeelte):

![chlimage_1-138](assets/chlimage_1-138.png)

* De curseur zal in een dwarraad veranderen wanneer u op schetswijze bent. U kunt meerdere afzonderlijke lijnen tekenen.
* De schetslijn weerspiegelt de annotatiekleur en kan een van de volgende zijn:

   * vrij

      de standaardmodus; klaar met de muisknop.

   * recht:

      de begin- `ALT` en eindpunten ingedrukt houden en klikken; voltooien met een dubbelklik.

* Nadat u de modus Schets hebt verlaten, kunt u op een schetslijn klikken om die schets te selecteren.
* Verplaats een schets door de schets te selecteren en vervolgens naar de gewenste positie te slepen.
* Een schets bedekt de inhoud. Dit betekent dat u binnen de vier hoeken van de schets niet op de onderliggende alinea kunt klikken. bijvoorbeeld als u een koppeling moet bewerken of openen. Als dit een probleem wordt (bijvoorbeeld als u een schets hebt die een groot gebied van de pagina bedekt), minimaliseert u de juiste annotatie, aangezien hierdoor ook alle verwante schetsen worden geminimaliseerd, zodat u toegang hebt tot het onderliggende gebied.
* Om een individuele schets te schrappen - selecteer de vereiste schets, dan duw op de sleutel van de **Schrapping** (**fn**-**backspace** op MAC).

* Als u een alinea verplaatst of kopieert, worden eventuele verwante annotaties en de bijbehorende schetsen ook verplaatst of gekopieerd. hun standpunt ten aanzien van de alinea blijft ongewijzigd .
* Als u een annotatie verwijdert, worden ook alle aan die annotatie gekoppelde schetsen verwijderd.

