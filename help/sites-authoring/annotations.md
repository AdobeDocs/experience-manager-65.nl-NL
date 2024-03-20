---
title: Annotaties bij het bewerken van een inhoudspagina
description: Met veel componenten die rechtstreeks betrekking hebben op inhoud, kunt u een annotatie toevoegen.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
exl-id: de1ae7e3-db3a-4b5e-8a4f-ae111227181f
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 0%

---

# Annotaties bij het bewerken van een pagina{#annotations-when-editing-a-page}

Het toevoegen van inhoud aan de pagina&#39;s van uw website is vaak onderwerp van besprekingen alvorens het eigenlijk wordt gepubliceerd. Om dit te helpen, laat vele componenten direct met inhoud verwant (in tegenstelling, bijvoorbeeld, aan lay-out) u een aantekening toevoegen.

Een annotatie plaatst een gekleurde markering/notitie op de pagina. Met de annotatie kunt u (of andere gebruikers) opmerkingen en/of vragen laten voor andere auteurs/revisoren.

>[!NOTE]
>
>De definitie van een afzonderlijk componenttype bepaalt of het toevoegen van een aantekening (ANNOTATION) mogelijk is (of niet) op instanties van die component.

>[!NOTE]
>
>Annotaties die zijn gemaakt in de klassieke gebruikersinterface, worden weergegeven in de gebruikersinterface voor aanraakbediening. Schetsen zijn echter specifiek voor de gebruikersinterface en worden alleen weergegeven in de gebruikersinterface waarin ze zijn gemaakt.

>[!CAUTION]
>
>Als u een bron verwijdert (bijvoorbeeld alinea), worden alle annotaties en schetsen verwijderd die aan die bron zijn gekoppeld, ongeacht de positie op de pagina als geheel.

>[!NOTE]
>
>Afhankelijk van uw vereisten kunt u ook een workflow ontwikkelen om meldingen te verzenden wanneer annotaties worden toegevoegd, bijgewerkt of verwijderd.

## Annotaties {#annotations}

Een speciale [mode](/help/sites-authoring/author-environment-tools.md#page-modes) wordt gebruikt voor het maken en weergeven van annotaties.

>[!NOTE]
>
>Vergeet niet dat [opmerkingen](/help/sites-authoring/basic-handling.md#timeline) zijn ook beschikbaar voor het opgeven van feedback op een pagina.

>[!NOTE]
>
>U kunt verschillende bronnen van notities voorzien:
>
>* [Annoteren van elementen](/help/assets/manage-assets.md#annotating)
>* [Video-elementen annoteren](/help/assets/managing-video-assets.md#annotate-video-assets)
>

### Een component annoteren {#annotating-a-component}

In de modus Annotatie kunt u annotaties voor uw inhoud maken, bewerken, verplaatsen of verwijderen:

1. U kunt de modus Annotatie activeren met het pictogram op de werkbalk (rechtsboven) wanneer u een pagina bewerkt:

   ![Annoteren](do-not-localize/screen_shot_2018-03-22at110414.png)

   U kunt nu bestaande annotaties weergeven.

   >[!NOTE]
   >
   >Als u de modus Annotatie wilt afsluiten, klikt u op het pictogram Annotatie (x-symbool) rechts van de bovenste werkbalk.

1. Klik op het pictogram Annotatie toevoegen (plus symbool links op de werkbalk) om annotaties toe te voegen.

   >[!NOTE]
   >
   >Klik op het pictogram Annuleren (x-symbool in een witte cirkel) links van de bovenste werkbalk om het toevoegen van annotaties (en terug te keren naar de weergave) te stoppen.

1. Klik op de vereiste component (componenten die kunnen worden geannoteerd, worden gemarkeerd met een blauwe rand) om de annotatie toe te voegen en het dialoogvenster te openen:

   ![screen_shot_2018-03-22at110606](assets/screen_shot_2018-03-22at110606.png)

   Hier kunt u het juiste veld en/of pictogram gebruiken om:

   * Voer de annotatietekst in.
   * Maak een schets (lijnen en vormen) om een gebied van de component te markeren.

     De cursor verandert in een kruisdraad wanneer u een schets maakt. U kunt meerdere afzonderlijke lijnen tekenen. De schetslijn geeft de annotatiekleur weer en kan een pijl, cirkel of ovaal zijn.

     ![Schets](do-not-localize/screen_shot_2018-03-22at110640.png)

   * Kies of wijzig de kleur:

     ![Kleur kiezen/wijzigen](do-not-localize/chlimage_1-19.png)

   * Verwijder de aantekening.

     ![Annotatie verwijderen](do-not-localize/screen_shot_2018-03-22at110647.png)

1. U kunt het dialoogvenster met annotaties sluiten door buiten het dialoogvenster te klikken of erop te tikken. Een afgekapte weergave (het eerste woord) van de annotatie wordt samen met eventuele schetsen weergegeven:

   ![screen_shot_2018-03-22at110850](assets/screen_shot_2018-03-22at110850.png)

1. Nadat u een specifieke annotatie hebt bewerkt, kunt u:

   * Klik op de tekstmarkering om de annotatie te openen. Nadat u de volledige tekst hebt geopend, kunt u de annotatie wijzigen of verwijderen.

      * Schetsen kunnen niet onafhankelijk van de annotatie worden verwijderd.

   * Verander de positie van de tekstmarkering.
   * Klik op een schetslijn om die schets te selecteren en sleep deze naar de gewenste positie.
   * Een component verplaatsen of kopiëren

      * Eventuele verwante annotaties en de bijbehorende schetsen worden ook verplaatst of gekopieerd en hun positie ten opzichte van de alinea blijft dezelfde.

1. Als u de Annotatiemodus wilt afsluiten en wilt terugkeren naar de eerder gebruikte modus, klikt u op het pictogram Annotatie (x-symbool) rechts van de bovenste werkbalk.

>[!NOTE]
>
>Annotaties kunnen niet worden toegevoegd aan een pagina die is vergrendeld door een andere gebruiker.

### Annotatie-indicator {#annotation-indicator}

Annotaties worden niet weergegeven in de modus Bewerken, maar het symbool rechtsboven op de werkbalk geeft aan hoeveel annotaties er bestaan voor de huidige pagina. Het pictogram vervangt het standaardpictogram Annotaties, maar werkt nog steeds als een snelle koppeling die van/naar de modus Annotatie schakelt:

![Indicator voor annotaties](assets/chlimage_1-242.png)
