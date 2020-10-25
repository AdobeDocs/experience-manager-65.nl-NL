---
title: Annotaties bij het bewerken van een pagina
seo-title: Annotaties bij het bewerken van een pagina
description: Met veel rechtstreeks aan inhoud gerelateerde componenten kunt u een annotatie toevoegen
seo-description: Met veel rechtstreeks aan inhoud gerelateerde componenten kunt u een annotatie toevoegen
uuid: 157be55c-8ab8-472e-be32-0dcc02bfa41d
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: aa89326a-ad33-4b0b-8d09-c68c5a5c790a
translation-type: tm+mt
source-git-commit: cec6c4f9a1a75eb049dd4b8461c36c8d58d46f79
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 0%

---


# Annotaties bij het bewerken van een pagina{#annotations-when-editing-a-page}

Het toevoegen van inhoud aan de pagina&#39;s van uw website is vaak onderwerp van besprekingen alvorens het eigenlijk wordt gepubliceerd. Om dit te helpen, staan vele componenten direct met inhoud verwant (in tegenstelling, bijvoorbeeld, aan lay-out) u toe om een aantekening toe te voegen.

Een annotatie plaatst een gekleurde markering/notitie op de pagina. Met de annotatie kunt u (of andere gebruikers) opmerkingen en/of vragen laten voor andere auteurs/revisoren.

>[!NOTE]
>
>De definitie van een afzonderlijk componenttype bepaalt of het toevoegen van een aantekening (ANNOTATION) mogelijk is (of niet) op instanties van die component.

>[!NOTE]
>
>Annotaties die zijn gemaakt in de klassieke gebruikersinterface worden weergegeven in de gebruikersinterface voor aanraakbediening. Schetsen zijn echter specifiek voor de gebruikersinterface en worden alleen weergegeven in de gebruikersinterface waarin ze zijn gemaakt.

>[!CAUTION]
>
>Als u een bron verwijdert (bijvoorbeeld een alinea), worden alle annotaties en schetsen verwijderd die aan die bron zijn gekoppeld, ongeacht de positie op de pagina als geheel.

>[!NOTE]
>
>Afhankelijk van uw vereisten kunt u ook een workflow ontwikkelen om meldingen te verzenden wanneer annotaties worden toegevoegd, bijgewerkt of verwijderd.

## Annotaties {#annotations}

Een speciale [modus](/help/sites-authoring/author-environment-tools.md#page-modes) wordt gebruikt voor het maken en weergeven van annotaties.

>[!NOTE]
>
>Vergeet niet dat [opmerkingen](/help/sites-authoring/basic-handling.md#timeline) ook beschikbaar zijn voor het geven van feedback op een pagina.

>[!NOTE]
>
>U kunt verschillende bronnen van notities voorzien:
>
>* [Annoteren van elementen](/help/assets/manage-assets.md#annotating)
>* [Video-elementen annoteren](/help/assets/managing-video-assets.md#annotate-video-assets)

>



### Een component annoteren {#annotating-a-component}

In de modus Annoteren kunt u annotaties voor uw inhoud maken, bewerken, verplaatsen of verwijderen:

1. U kunt de modus Annotatie activeren met het pictogram op de werkbalk (rechtsboven) wanneer u een pagina bewerkt:

   ![](do-not-localize/screen_shot_2018-03-22at110414.png)

   U kunt nu bestaande annotaties weergeven.

   >[!NOTE]
   >
   >Tik op het pictogram Annotatie (x-symbool) rechts van de bovenste werkbalk om de modus Annotatie af te sluiten.

1. Klik of tik op het pictogram Annotatie toevoegen (plus symbool links op de werkbalk) om annotaties toe te voegen.

   >[!NOTE]
   >
   >Tik op of klik op het pictogram Annuleren (x-symbool in een witte cirkel) links van de bovenste werkbalk om het toevoegen van annotaties (en terug te keren naar de weergave) te stoppen.

1. Klik of tik op de vereiste component (componenten die kunnen worden geannoteerd, worden gemarkeerd met een blauwe rand) om de annotatie toe te voegen en het dialoogvenster te openen:

   ![screen_shot_2018-03-22at110606](assets/screen_shot_2018-03-22at110606.png)

   Hier kunt u het juiste veld en/of pictogram gebruiken om:

   * Voer de annotatietekst in.
   * Maak een schets (lijnen en vormen) om een gebied van de component te markeren.

      De cursor verandert in een kruisdraad wanneer u een schets maakt. U kunt meerdere afzonderlijke lijnen tekenen. De schetslijn geeft de annotatiekleur weer en kan een pijl, cirkel of ovaal zijn.
   ![](do-not-localize/screen_shot_2018-03-22at110640.png)

   * Kies of wijzig de kleur:

   ![](do-not-localize/chlimage_1-19.png)

   * Verwijder de annotatie.

   ![](do-not-localize/screen_shot_2018-03-22at110647.png)

1. U kunt het dialoogvenster met annotaties sluiten door buiten het dialoogvenster te klikken of erop te tikken. Een afgekapte weergave (het eerste woord) van de annotatie wordt samen met eventuele schetsen weergegeven:

   ![screen_shot_2018-03-22at110850](assets/screen_shot_2018-03-22at110850.png)

1. Nadat u een specifieke annotatie hebt bewerkt, kunt u:

   * Klik of tik op de tekstmarkering om de annotatie te openen. Nadat u de volledige tekst hebt geopend, kunt u de annotatie wijzigen of verwijderen.

      * Schetsen kunnen niet onafhankelijk van de annotatie worden verwijderd.
   * Verander de positie van de tekstmarkering.
   * Klik of tik op een schetslijn om die schets te selecteren en sleep deze naar de gewenste positie.
   * Een component verplaatsen of kopiëren

      * Eventuele verwante annotaties en de bijbehorende schetsen worden ook verplaatst of gekopieerd en hun positie ten opzichte van de alinea blijft dezelfde.


1. Tik op het pictogram Annotatie (x-symbool) rechts van de bovenste werkbalk of klik op het pictogram Annotatie om de Annotatiemodus te sluiten en terug te keren naar de eerder gebruikte modus.

>[!NOTE]
>
>Annotaties kunnen niet worden toegevoegd aan een pagina die is vergrendeld door een andere gebruiker.

### Annotatie-indicator {#annotation-indicator}

Annotaties worden niet weergegeven in de modus Bewerken, maar het symbool rechtsboven op de werkbalk geeft aan hoeveel annotaties er bestaan voor de huidige pagina. Het pictogram vervangt het standaardpictogram Annotaties, maar werkt nog steeds als een snelle koppeling die van/naar de modus Annotatie schakelt:

![chlimage_1-242](assets/chlimage_1-242.png)

