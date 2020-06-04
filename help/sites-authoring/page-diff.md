---
title: Page Diff-optie
seo-title: Page Diff-optie
description: Met de functie Pagina's diff kunt u twee pagina's naast elkaar vergelijken met de gemarkeerde verschillen.
seo-description: Met de functie Pagina's diff kunt u twee pagina's naast elkaar vergelijken met de gemarkeerde verschillen.
uuid: 5af8b466-5922-4fe6-9eae-7bad99be23e0
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 8386a16a-9d47-46d5-bc60-5f290c59e60e
docset: aem65
translation-type: tm+mt
source-git-commit: eb9a4792f4d64f98805919f00bb62193a6a7dafc
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 1%

---


# Page Diff-optie{#page-diff}

## Inleiding {#introduction}

Het maken van inhoud is een herhalend proces. Om efficiënt te kunnen ontwerpen moet u kunnen zien wat er van de ene iteratie naar de andere is veranderd. Het weergeven van de ene pagina en de andere is inefficiënt en vatbaar voor fouten. Een auteur wil de huidige pagina naast elkaar kunnen vergelijken met een andere versie.

Met de functie Pagina&#39;s diff kunt u twee pagina&#39;s naast elkaar vergelijken met de gemarkeerde verschillen.

>[!TIP]
>
>Zie [Developing and Page Diff](/help/sites-developing/pagediff.md#operation-details) voor meer technische details over deze functie.

## Use {#use}

De zijdelingse scheiding kan het volgende vergelijken:

* [Versies](/help/sites-authoring/working-with-page-versions.md#comparing-a-version-with-current-page) - Eerdere versie van een pagina met de huidige status
* [Actieve kopieën](/help/sites-administering/msm-livecopy.md#comparing-a-live-copy-page-with-a-blueprint-page) - Live kopie met vervaging
* [Starten](/help/sites-authoring/launches-editing.md#comparing-a-launch-page-to-its-source-page) - Starten met bron
* [Taalkopieën](/help/sites-administering/tc-manage.md#comparing-language-copies) - Een pagina voor en na (her)vertaling

Zie de respectieve onderwerpen over hoe te om diff binnen die contexten te beginnen.

### Presentatie van de verschillen {#presentation-of-differences}

Ongeacht de inhoud die wordt vergeleken, blijft de presentatie van het diff gelijk.

* De inhoud die u hebt geselecteerd toen u de diff-bewerking hebt gestart, wordt links weergegeven (het diff-ingangspunt).
* De vergelijkingsinhoud wordt rechts weergegeven (ten opzichte van de geselecteerde inhoud).

Als u bijvoorbeeld versies vergelijkt, wordt de huidige versie links weergegeven en wordt de vorige versie rechts weergegeven.

De bron van beide pagina&#39;s wordt duidelijk weergegeven in de koptekstbalk boven in het browservenster.

![chlimage_1-109](assets/chlimage_1-109.png)

De diff ontdekt veranderingen op het component en HTML niveau. Items die zijn gewijzigd, worden met verschillende kleuren gemarkeerd.

**Componentwijzigingen**

* Lichtgroen - component toegevoegd
* Roze - component verwijderd
* Blauw - component gewijzigd
* Blauw - component verplaatst

De kleuren Gewijzigd en Verplaatst zijn hetzelfde.

**HTML-wijzigingen**

* Donkergroen - HTML toegevoegd
* Rood - HTML verwijderd

>[!NOTE]
>
>Bij het vergelijken van taalkopieën wordt het markeren gedeactiveerd, omdat in een vertaling alles verandert en het markeren geen nut zou hebben.

### Volledig scherm en afsluiten {#fullscreen-and-exiting}

Als u de focus op bepaalde inhoud wilt plaatsen, klikt u op het pictogram voor een volledig scherm voor een van de twee zijden van het deelvenstervak om het venster te vergroten naar het volledige browservenster.

![](do-not-localize/chlimage_1-18.png)

De geselecteerde zijde vult het gehele venster, maar de balk blijft boven aan de pagina zodat u tussen de twee pagina&#39;s kunt schakelen.

![chlimage_1-110](assets/chlimage_1-110.png)

U kunt de volledige schermweergave ook sluiten door op het pictogram Volledig scherm afsluiten te klikken.

![](do-not-localize/chlimage_1-19.png)

U kunt het schuifregelaar Naast elkaar op elk gewenst moment afsluiten door op de knop Sluiten in de koptekst te klikken.

## Beperkingen {#limitations}

In sommige situaties kan het zijn dat het pagina-diff geen verschil detecteert zoals u had verwacht.

* Bij verschillende versies en lanceringen houdt diff geen rekening met dynamische componenten zoals broodkruimels, menu&#39;s, productlijsten of logo&#39;s (componenten die op de plaatsstructuur vertrouwen om hun inhoud terug te geven).
* Voor versies maakt diff niet het toegangsbeheerbeleid en levende exemplaarverhoudingen opnieuw.
* Als er wijzigingen worden aangebracht in een afbeelding, zoals het wijzigen van de kenmerken alt, title of src, wordt deze in blauw gemarkeerd als gewijzigd. In sommige gevallen heeft de afbeelding echter een Base64-representatie van het kenmerk src en zelfs als beide afbeeldingen er hetzelfde uitzien, worden ze door het diff als verschillend gemarkeerd vanwege de verschillende src-kenmerken.
* Het diff kan beeldomwenteling niet ontdekken.
* Als een pagina wordt verplaatst, kunt u geen diff met om het even welke versies meer uitvoeren die vóór de beweging worden gemaakt.

   * Als u problemen ondervindt met een diff, controleert u de [tijdlijn](/help/sites-authoring/basic-handling.md#timeline) voor de pagina om te zien of de pagina is verplaatst.

>[!NOTE]
>
>Versies kunnen niet met elkaar worden vergeleken. Alleen de huidige versie kan worden vergeleken met andere versies van de pagina. De huidige versie is altijd de versie die met wijzigingen is gemarkeerd.

>[!NOTE]
>
>Zie de documentatie over [de](/help/sites-developing/pagediff.md) ontwikkelaar van deze functie voor meer informatie over de werking van het mechanisme voor pagina-diff en de beperkingen die paginadiff kunnen beïnvloeden.
