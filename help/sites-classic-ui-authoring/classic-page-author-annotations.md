---
title: Annotaties bij het bewerken van een pagina
description: Over het toevoegen van inhoud aan de pagina's van uw website wordt vaak gediscussieerd voordat deze daadwerkelijk wordt gepubliceerd. Om dit te helpen, laten vele componenten direct met inhoud verwant u een aantekening toevoegen.
page-status-flag: de-activated
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
exl-id: d60e9601-d15b-4378-a33e-e90961f63195
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 0%

---

# Annotaties bij het bewerken van een pagina{#annotations-when-editing-a-page}

Over het toevoegen van inhoud aan de pagina&#39;s van uw website wordt vaak gediscussieerd voordat deze daadwerkelijk wordt gepubliceerd. Om dit te helpen, laten vele componenten direct met inhoud verwant (in tegenstelling, bijvoorbeeld om te lay-out) u een aantekening toevoegen.

Een annotatie plaatst een gekleurde markering/notitie op de pagina. Met de annotatie kunt u (of andere gebruikers) opmerkingen en/of vragen laten voor andere auteurs/revisoren.

>[!NOTE]
>
>De definitie van een afzonderlijk componenttype bepaalt of het toevoegen van een aantekening (ANNOTATION) mogelijk is (of niet) op instanties van die component.

>[!NOTE]
>
>Annotaties die zijn gemaakt in de klassieke gebruikersinterface worden weergegeven in de gebruikersinterface voor geoptimaliseerde aanrakingen. Schetsen zijn echter specifiek voor de gebruikersinterface en worden alleen weergegeven in de gebruikersinterface waarin ze zijn gemaakt.

>[!CAUTION]
>
>Als u een bron verwijdert (bijvoorbeeld alinea), worden alle annotaties en schetsen verwijderd die aan die bron zijn gekoppeld, ongeacht de positie op de pagina als geheel.

>[!NOTE]
>
>Afhankelijk van uw vereisten kunt u ook een workflow ontwikkelen om meldingen te verzenden wanneer annotaties worden toegevoegd, bijgewerkt of verwijderd.

## Annotaties {#annotations}

Afhankelijk van het alineaontwerp is annotatie beschikbaar als een optie in het contextmenu (meestal de rechtermuisknop als deze zich boven de vereiste alinea bevindt) of als een knop op de bewerkbalk voor alinea&#39;s.

Selecteer in beide gevallen **Annoteren**. Er wordt een gekleurde notitie toegepast op de alinea. U bevindt zich direct in de modus Bewerken, zodat u rechtstreeks tekst kunt toevoegen:

![chlimage_1-137](assets/chlimage_1-137.png)

U kunt de annotatie naar een nieuwe positie op de pagina verplaatsen. Klik op het bovenste randgebied en houd de annotatie ingedrukt en sleep deze tegelijkertijd naar de nieuwe positie. Dit kan overal op de pagina zijn, hoewel het vaak zinvol is om de pagina op een of andere manier verbonden te houden met de alinea.

Annotaties (inclusief verwante schetsen) worden ook opgenomen in alle kopieer-, knip- of verwijderhandelingen die worden uitgevoerd op de alinea waaraan ze zijn gekoppeld. Voor kopieer- of kniphandelingen blijft de positie van de annotatie (en de bijbehorende schetsen) ten opzichte van de oorspronkelijke alinea behouden.

U kunt de grootte van de annotatie ook vergroten of verkleinen door de rechterbenedenhoek te slepen.

Voor traceringsdoeleinden geeft de voettekstregel de gebruiker aan die de annotatie en de datum heeft gemaakt. Volgende auteurs kunnen dezelfde annotatie bewerken (voettekst wordt bijgewerkt) of een andere annotatie voor dezelfde alinea maken.

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

* De curseur verandert in een dwarraad wanneer u op schetswijze bent. U kunt meerdere afzonderlijke lijnen tekenen.
* De schetslijn weerspiegelt de annotatiekleur en kan een van de volgende zijn:

   * vrij

     de standaardmodus; sluit de bewerking af door de muisknop los te laten.

   * recht:

     onderdrukken `ALT` en klik op het begin- en eindpunt. Voltooi de bewerking met een dubbelklik.

* Nadat u de modus Schets hebt verlaten, kunt u op een schetslijn klikken om die schets te selecteren.
* Verplaats een schets door de schets te selecteren en vervolgens naar de gewenste positie te slepen.
* Een schets bedekt de inhoud. Dit betekent dat u binnen de vier hoeken van de schets niet op de onderliggende alinea kunt klikken. Als u bijvoorbeeld een koppeling moet bewerken of openen. Als dit een probleem wordt (bijvoorbeeld als u een schets hebt die een groot gebied van de pagina bedekt), minimaliseert u de juiste annotatie, aangezien hierdoor ook alle verwante schetsen worden geminimaliseerd, zodat u toegang hebt tot het onderliggende gebied.
* Als u een afzonderlijke schets wilt verwijderen, selecteert u de gewenste schets en drukt u vervolgens op de knop **Verwijderen** key (**fn**-**backspace** op een Mac).

* Als u een alinea verplaatst of kopieert, worden eventuele verwante annotaties en de bijbehorende schetsen ook verplaatst of gekopieerd. De positie ten opzichte van de alinea blijft ongewijzigd.
* Als u een annotatie verwijdert, worden ook alle schetsen verwijderd die aan die annotatie zijn gekoppeld.
