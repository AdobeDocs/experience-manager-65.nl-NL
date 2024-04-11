---
title: Pagina grijs
description: Met de functie Pagina's diff kunt u twee pagina's naast elkaar vergelijken met de gemarkeerde verschillen.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
docset: aem65
exl-id: 3beea5cd-5ae0-485b-8dfc-8b3a23c11586
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User,Admin,Architect,Developer
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 0%

---

# Pagina grijs{#page-diff}

## Inleiding {#introduction}

Inhoud maken is een herhalend proces. Om efficiënt te kunnen ontwerpen moet u kunnen zien wat er van de ene iteratie naar de andere is veranderd. Het weergeven van de ene pagina en de andere is inefficiënt en vatbaar voor fouten. Een auteur wil de huidige pagina naast elkaar kunnen vergelijken met een andere versie.

Met de functie Pagina&#39;s diff kunt u twee pagina&#39;s naast elkaar vergelijken met de gemarkeerde verschillen.

>[!TIP]
>
>Zie [Developing and Page Diff](/help/sites-developing/pagediff.md#operation-details) voor meer technische details over deze functie.

## Gebruiken {#use}

De zijdelingse scheiding kan het volgende vergelijken:

* [Versies](/help/sites-authoring/working-with-page-versions.md#comparing-a-version-with-current-page) - Eerdere versie van een pagina met de huidige staat
* [Actieve kopieën](/help/sites-administering/msm-livecopy.md#comparing-a-live-copy-page-with-a-blueprint-page) - Live kopie met bijbehorende blauwdruk
* [Starten](/help/sites-authoring/launches-editing.md#comparing-a-launch-page-to-its-source-page) - Starten met bron
* [Taalkopieën](/help/sites-administering/tc-manage.md#comparing-language-copies) - Een pagina voor en na (her)vertaling

Zie de respectieve onderwerpen over hoe te om diff binnen die contexten te beginnen.

### Presentatie van de verschillen {#presentation-of-differences}

Ongeacht de inhoud die wordt vergeleken, blijft de presentatie van het diff gelijk.

* De inhoud die u hebt geselecteerd toen u de diff-bewerking hebt gestart, wordt links weergegeven (het diff-ingangspunt).
* De vergelijkingsinhoud wordt rechts weergegeven (ten opzichte van de geselecteerde inhoud).

Als u bijvoorbeeld versies vergelijkt, wordt de huidige versie links weergegeven en wordt de vorige versie rechts weergegeven.

De bron van beide pagina&#39;s wordt duidelijk weergegeven in de koptekstbalk boven in het browservenster.

![Bron weergegeven in koptekst](assets/chlimage_1-109.png)

Met de Diff worden wijzigingen op componentniveau en op HTML-niveau gedetecteerd. Items die zijn gewijzigd, worden met verschillende kleuren gemarkeerd.

**Componentwijzigingen**

* Lichtgroen - component toegevoegd
* Roze - component verwijderd

**Wijzigingen in HTML**

* Donkergroen - HTML toegevoegd
* Rood - HTML verwijderd

>[!NOTE]
>
>Bij het vergelijken van taalkopieën wordt het markeren gedeactiveerd, omdat in een vertaling alles verandert en het markeren geen nut zou hebben.

### Volledig scherm en afsluiten {#fullscreen-and-exiting}

Als u de focus op bepaalde inhoud wilt plaatsen, klikt u op het pictogram voor een volledig scherm voor een van de twee zijden van het deelvenstervak om dit naar het volledige browservenster te vergroten.

![Pictogram modus Volledig scherm](do-not-localize/chlimage_1-18.png)

De geselecteerde zijde vult het gehele venster, maar de balk blijft boven aan de pagina zodat u tussen de twee pagina&#39;s kunt schakelen.

![Met de balk boven kunt u schakelen tussen pagina&#39;s](assets/chlimage_1-110.png)

U kunt de volledige schermweergave ook sluiten door op het pictogram Volledig scherm afsluiten te klikken.

![Volledig scherm sluiten](do-not-localize/chlimage_1-19.png)

U kunt het schuifregelaar Naast elkaar op elk gewenst moment afsluiten door op de knop Sluiten in de koptekst te klikken.

## Beperkingen {#limitations}

In sommige situaties kan het zijn dat het pagina-diff geen verschil detecteert zoals u had verwacht.

* Wanneer verschillende versies en lanceringen, rekent diff geen dynamische componenten zoals broodkruimels, menu&#39;s, productlijsten of logo&#39;s (componenten die op de plaatsstructuur vertrouwen om hun inhoud terug te geven).
* Voor versies, maakt diff niet het toegangsbeheerbeleid en levende exemplaarverhoudingen opnieuw.
* Als een pagina wordt verplaatst, kunt u geen diff met om het even welke versies meer uitvoeren die vóór de beweging worden gemaakt.

   * Als u problemen ondervindt met een diff, controleert u de [Tijdlijn](/help/sites-authoring/basic-handling.md#timeline) om te zien of de pagina is verplaatst.

>[!NOTE]
>
>Versies kunnen niet met elkaar worden vergeleken. Alleen de huidige versie kan worden vergeleken met andere versies van de pagina. De huidige versie is altijd de versie die met wijzigingen is gemarkeerd.

>[!NOTE]
>
>Zie voor meer informatie over de werking van het mechanisme voor pagina-diff en de beperkingen die paginadiff kunnen beïnvloeden het dialoogvenster [ontwikkelaarsdocumentatie](/help/sites-developing/pagediff.md) van deze functie.
