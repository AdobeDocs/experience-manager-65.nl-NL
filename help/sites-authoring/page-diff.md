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
role: User,Admin,Developer
source-git-commit: c77849740fab51377ce60aff5f611e0408dca728
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
>Zie [ het Ontwikkelen en Afschuiving van de Pagina ](/help/sites-developing/pagediff.md#operation-details) voor meer technische details op deze eigenschap.

## Gebruiken {#use}

De zijdelingse scheiding kan het volgende vergelijken:

* [ Versies ](/help/sites-authoring/working-with-page-versions.md#comparing-a-version-with-current-page) - Eerdere versie van een pagina met zijn huidige staat
* [ Levende Exemplaren ](/help/sites-administering/msm-livecopy.md#comparing-a-live-copy-page-with-a-blueprint-page) - Levend Exemplaar met zijn Vervaging
* [ Lanceringen ](/help/sites-authoring/launches-editing.md#comparing-a-launch-page-to-its-source-page) - Lanceer met zijn Source
* [ Kopieën van de Taal ](/help/sites-administering/tc-manage.md#comparing-language-copies) - een pagina vóór en na (re-)vertaling

Zie de respectieve onderwerpen over hoe te om diff binnen die contexten te beginnen.

### Presentatie van de verschillen {#presentation-of-differences}

Ongeacht de inhoud die wordt vergeleken, blijft de presentatie van het diff gelijk.

* De inhoud die u hebt geselecteerd toen u de diff-bewerking hebt gestart, wordt links weergegeven (het diff-ingangspunt).
* De vergelijkingsinhoud wordt rechts weergegeven (ten opzichte van de geselecteerde inhoud).

Als u bijvoorbeeld versies vergelijkt, wordt de huidige versie links weergegeven en wordt de vorige versie rechts weergegeven.

De bron van beide pagina&#39;s wordt duidelijk weergegeven in de koptekstbalk boven in het browservenster.

![ Source die in kopbal ](assets/chlimage_1-109.png) wordt getoond

De diff ontdekt veranderingen op het component en HTML niveau. Items die zijn gewijzigd, worden met verschillende kleuren gemarkeerd.

**de Veranderingen van de Component**

* Lichtgroen - component toegevoegd
* Roze - component verwijderd

**de Veranderingen van HTML**

* Donkergroen - HTML toegevoegd
* Rood - HTML verwijderd

>[!NOTE]
>
>Bij het vergelijken van taalkopieën wordt het markeren gedeactiveerd, omdat in een vertaling alles verandert en het markeren geen nut zou hebben.

### Volledig scherm en afsluiten {#fullscreen-and-exiting}

Als u de focus op bepaalde inhoud wilt plaatsen, klikt u op het pictogram voor een volledig scherm voor een van de twee zijden van het deelvenstervak om dit naar het volledige browservenster te vergroten.

![ het Volledige pictogram van de het schermwijze ](do-not-localize/chlimage_1-18.png)

De geselecteerde zijde vult het gehele venster, maar de balk blijft boven aan de pagina zodat u tussen de twee pagina&#39;s kunt schakelen.

![ Bar bij bovenkant laat u tussen pagina&#39;s ](assets/chlimage_1-110.png) schakelen

U kunt de volledige schermweergave ook sluiten door op het pictogram Volledig scherm afsluiten te klikken.

![ dicht volledig scherm ](do-not-localize/chlimage_1-19.png)

U kunt het schuifregelaar Naast elkaar op elk gewenst moment afsluiten door op de knop Sluiten in de koptekst te klikken.

## Beperkingen {#limitations}

In sommige situaties kan het zijn dat het pagina-diff geen verschil detecteert zoals u had verwacht.

* Wanneer verschillende versies en lanceringen, rekent diff geen dynamische componenten zoals broodkruimels, menu&#39;s, productlijsten of logo&#39;s (componenten die op de plaatsstructuur vertrouwen om hun inhoud terug te geven).
* Voor versies, maakt diff niet het toegangsbeheerbeleid en levende exemplaarverhoudingen opnieuw.
* Als een pagina wordt verplaatst, kunt u geen diff met om het even welke versies meer uitvoeren die vóór de beweging worden gemaakt.

   * Als u problemen met afschuiving ervaart, controleer de [ Chronologie ](/help/sites-authoring/basic-handling.md#timeline) voor de pagina om te zien of de pagina is bewogen.

>[!NOTE]
>
>Versies kunnen niet met elkaar worden vergeleken. Alleen de huidige versie kan worden vergeleken met andere versies van de pagina. De huidige versie is altijd de versie die met wijzigingen is gemarkeerd.

>[!NOTE]
>
>Voor meer details over de verrichting van het mechanisme en de beperkingen van de paginascheiding die paginascheiding kunnen beïnvloeden, zie de [ documentatie van de ontwikkelaar ](/help/sites-developing/pagediff.md) van deze eigenschap.
