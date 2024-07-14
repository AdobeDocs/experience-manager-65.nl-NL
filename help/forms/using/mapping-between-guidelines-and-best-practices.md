---
title: Richtlijnen en de beste toegankelijkheidsprocedures voor het maken van formulieren in formulierontwerpers
description: Tips en trucs voor toegankelijkheid tijdens het ontwikkelen van formulieren in formulierontwerper.
feature: Adaptive Forms, Forms Designer
solution: Experience Manager, Experience Manager Forms
role: User, Developer
hide: true
hidefromtoc: true
source-git-commit: 38fb132f0eb5b710745db11e7ddf59efc0f0ae95
workflow-type: tm+mt
source-wordcount: '3366'
ht-degree: 0%

---

# Toewijzing tussen richtlijnen en beste praktijken

In de volgende secties worden de richtsnoeren van sectie 508 en WCAG aan de in deze handleiding beschreven beste praktijken gekoppeld.

## § 1194.21 Richtsnoer Beschrijving en beste praktijken

### Section 508 § 1194.21: Software applications and operating systems

| § 1194.21 | Beschrijving van hulplijnen | Vereiste Designer Best Practices voor LiveCycle | Notities |
|-----------|-----------------------|-----------------------------------------------------------|-------|
| a) | Wanneer software is ontworpen om te worden uitgevoerd op een systeem met een toetsenbord, moeten productfuncties uitvoerbaar zijn vanaf een toetsenbord waar de functie zelf of het resultaat van het uitvoeren van een functie tekstueel kan worden herkend. | <li> 2.7 Zorg ervoor dat formulierbesturingselementen via het toetsenbord toegankelijk zijn </li><li> 2.6 Zorg ervoor dat de lees- en tabvolgorde correct zijn</li> | |
| b) | Toepassingen mogen de actiefuncties van andere producten die als toegankelijkheidskenmerken zijn geïdentificeerd, niet verstoren of uitschakelen, wanneer deze kenmerken volgens de industrienormen zijn ontwikkeld en gedocumenteerd. Toepassingen mogen ook geen geactiveerde functies van een besturingssysteem verstoren of uitschakelen die als toegankelijkheidskenmerken zijn geïdentificeerd, wanneer de programmeringsinterface van de toepassing voor die toegankelijkheidsfuncties door de fabrikant van het besturingssysteem is gedocumenteerd en beschikbaar is voor de productontwikkelaar. | Geen specifieke LiveCycle Designer-technieken - deze richtlijn wordt door Adobe Reader gehanteerd voor PDF forms. | |
| c) | Er moet een duidelijk gedefinieerde indicatie op het scherm van de huidige focus worden gegeven die beweegt tussen interactieve interface-elementen wanneer de invoerfocus verandert. De focus wordt via programmacode beschikbaar gemaakt, zodat ondersteunende technologie de focus en focusveranderingen kan volgen. | 2.3 Kies de juiste besturingselementen om ervoor te zorgen dat de focus zowel via de programmacode als visueel wordt weergegeven, gebruik altijd de standaardbesturingselementen. | |
| d) | Voor ondersteunende hulpmiddelen moet voldoende informatie over een gebruikersinterface-element beschikbaar zijn, met inbegrip van de identiteit, de werking en de toestand van het element. Wanneer een afbeelding een programma-element vertegenwoordigt, moet de informatie die door de afbeelding wordt getoond ook in tekst beschikbaar zijn. | <ul><li>2.1 Formulieren eenvoudig en gebruiksvriendelijk houden</li> <li>2.1.1 Verplaats, knipperende of knipperende inhoud niet</li> <li>2.2 Formuliereigenschappen configureren om toegankelijkheidsinformatie te genereren</li> <li>2.5 Geef juiste labels voor formulierbesturingselementen</li></ul> | |
| e) | Wanneer bitmapafbeeldingen worden gebruikt om besturingselementen, statusindicatoren of andere programmatische elementen te identificeren, moet de betekenis die aan deze afbeeldingen wordt toegekend, consistent zijn in de prestaties van de toepassing. | <ul><li>2.4 Verstrek tekstequivalenten voor beelden</li><li> 2.5 Geef juiste labels voor formulierbesturingselementen. Deze standaard is alleen van toepassing als u dezelfde afbeelding op meerdere plaatsen op een formulier gebruikt. Het gebruik van aangepaste besturingselementen voor afbeeldingen wordt afgeraden. Gebruik in plaats daarvan alleen de standaardbesturingselementen die door LiveCycle Designer worden geleverd. Als u wel afbeeldingen in uw besturingselementen gebruikt, moet u ervoor zorgen dat deze op consistente wijze worden gebruikt.</li> | |
| f) | Voor de weergave van tekst wordt tekstinformatie verstrekt via functies van het besturingssysteem. De minimale informatie die beschikbaar moet worden gesteld, is tekstinhoud, tekstinvoerinvoeglocatie en tekstkenmerken. | 2.3 Kies de juiste besturingselementen. Gebruik geen afbeeldingen om tekstuele informatie over te brengen. Gebruik altijd de standaardbesturingselementen in plaats van aangepaste invoercomponenten te gebruiken die teksteigenschappen mogelijk niet goed toegankelijk maken voor het besturingssysteem. | |
| g) | Toepassingen hebben geen voorrang op door de gebruiker geselecteerde contrast- en kleurselecties en andere individuele weergavekenmerken. | Geen specifieke LiveCycle Designer-technieken | Gebruik waar mogelijk de standaardkleuren van het systeem. |
| h) | Wanneer animatie wordt weergegeven, moet de informatie, naar keuze van de gebruiker, in ten minste één niet-geanimeerde presentatiemodus kunnen worden weergegeven. | 2.1 Formulieren eenvoudig en gebruiksvriendelijk houden Gebruik geen animaties in uw formulieren of gebruik afzonderlijke versies waarin animaties worden vervangen door statische afbeeldingen. | |
| i) | Kleurcodering mag niet worden gebruikt als het enige middel om informatie over te brengen, een handeling aan te geven, een antwoord te geven of een visueel element te onderscheiden. | 2.8 Kleur verantwoord gebruiken | |
| (j) | Wanneer een product een gebruiker in staat stelt de kleur- en contrastinstellingen aan te passen, moet een verscheidenheid aan kleurselecties worden verstrekt die een reeks contrastniveaus kunnen produceren. | Niet van toepassing | Deze functionaliteit wordt meestal geleverd door Adobe Reader, niet door de ontwikkelaar van het formulier. |
| k) | Software mag geen knipperende of knipperende tekst, objecten of andere elementen gebruiken met een flash- of knipperfrequentie van meer dan 2 Hz en minder dan 55 Hz. | 2.1.1 Verplaats, knipperende of knipperende inhoud niet | |
| l) | Wanneer elektronische formulieren worden gebruikt, stelt het formulier personen die gebruikmaken van ondersteunende hulpmiddelen in staat toegang te krijgen tot de informatie, veldelementen en functionaliteit die vereist zijn voor het invullen en verzenden van het formulier, met inbegrip van alle aanwijzingen en aanwijzingen. | 2.5 Geef juiste labels voor formulierbesturingselementen | |

### Section 508 § 11942: Web-based intranet and Internet information and applications

| Artikel 11942 Richtsnoer | Beschrijving van hulplijnen | Vereiste Designer Best Practices voor LiveCycle | Notities |
|-----------|-----------------------|-----------------------------------------------------------|-------|
| a) | Voor elk niet-tekstequivalent moet een tekstequivalent worden opgegeven (bijvoorbeeld via &quot;alt&quot;, &quot;longdesc&quot; of in elementinhoud). | 2.4 Verstrek tekstequivalenten voor beelden | |
| b) | Gelijkwaardige alternatieven voor multimediapresentaties worden gesynchroniseerd met de presentatie. | 2.12 Ervoor zorgen dat alle multimedia-inhoud toegankelijk is | |
| c) | De webpagina&#39;s moeten zo zijn ontworpen dat alle informatie die met kleur wordt verstuurd, ook zonder kleur beschikbaar is, bijvoorbeeld vanuit context of opmaak. | 2.8 Kleur verantwoord gebruiken | |
| d) | Documenten moeten zo worden georganiseerd dat zij leesbaar zijn zonder dat daarvoor een bijbehorende stijlpagina nodig is. | Niet van toepassing | |
| e) | Voor elk actief gebied van een afbeeldingskaart aan de serverzijde moeten redundante tekstkoppelingen worden opgegeven. | Niet van toepassing | |
| f) | Afbeeldingen met hyperlinks aan de clientzijde worden in plaats van afbeeldingen met hyperlinks aan de serverzijde geleverd, behalve wanneer de gebieden niet met een beschikbare geometrische vorm kunnen worden gedefinieerd. | Niet van toepassing | |
| g) | Rij- en kolomkoppen worden voor gegevenstabellen geïdentificeerd. | 2.9 Cellen met koppen voor tabellen opgeven | |
| h) | Markup wordt gebruikt voor het koppelen van gegevenscellen en kopcellen voor gegevenstabellen met twee of meer logische niveaus van rij- of kolomkoppen. | 2.9 Cellen met koppen voor tabellen opgeven | |
| i) | Kaders krijgen een naam met tekst die de identificatie en navigatie van kaders vergemakkelijkt. | Niet van toepassing | |
| (j) | Pagina&#39;s moeten zo zijn ontworpen dat het scherm niet flikkert met een frequentie van meer dan 2 Hz en minder dan 55 Hz. | 2.1 Formulieren eenvoudig en gebruiksvriendelijk houden | |
| k) | Een tekstpagina met gelijkwaardige informatie of functionaliteit moet worden verstrekt om een website aan de bepalingen van dit deel te laten voldoen, wanneer de conformiteit op geen enkele andere manier kan worden verwezenlijkt. De inhoud van de alleen-tekstpagina wordt bijgewerkt wanneer de primaire pagina verandert. | Niet van toepassing | |
| l) | Wanneer pagina&#39;s scripttalen gebruiken om inhoud weer te geven of interface-elementen te maken, moet de informatie die door het script wordt verschaft, worden geïdentificeerd met functionele tekst die door hulpprogramma&#39;s kan worden gelezen. | 2.11 Scripts niet verstoren | |
| (m) | Wanneer een webpagina vereist dat een applet, plug-in of andere toepassing op het clientsysteem aanwezig is om pagina-inhoud te interpreteren, moet de pagina een koppeling bevatten naar een plug-in of applet die voldoet aan § 1194.21, onder a) tot en met l). | Niet van toepassing | Webpagina&#39;s die aan PDF forms zijn gekoppeld, moeten een koppeling naar Adobe Reader bevatten. |
| (n) | Wanneer elektronische formulieren zijn ontworpen om online te worden ingevuld, stelt het formulier mensen die gebruikmaken van ondersteunende hulpmiddelen in staat toegang te krijgen tot de informatie, veldelementen en functionaliteit die vereist zijn voor het invullen en verzenden van het formulier, met inbegrip van alle aanwijzingen en aanwijzingen. | 2.5 Geef juiste labels voor formulierbesturingselementen | |
| o) | Er moet een methode worden ingevoerd die gebruikers in staat stelt herhaalde navigatiekoppelingen over te slaan. | 2.10 Een navigeerbare formulierstructuur bieden | |
| p) | Wanneer een getimede reactie vereist is, moet de gebruiker worden gewaarschuwd en voldoende tijd krijgen om aan te geven dat meer tijd nodig is. | 2.11 Scripts niet verstoren | |

### WCAG 1.0-controlepunten van prioriteit 1

| Controlepunt | Beschrijving controlepunt | Vereiste Designer Best Practices voor LiveCycle | Notities |
|------------|------------------------|-----------------------------------------------------------|-------|
| [ 1.1 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-text-equivalent) | Geef een tekstequivalent op voor elk niet-tekstelement (bijvoorbeeld via &quot;alt&quot;, &quot;longdesc&quot; of in elementinhoud). Dit omvat: afbeeldingen, grafische voorstellingen van tekst (inclusief symbolen), gebieden met afbeeldingen met hyperlinks, animaties (bijvoorbeeld geanimeerde GIFFEN), applets en programmatische objecten, ASCII-illustraties, frames, scripts, afbeeldingen die worden gebruikt als lijstopsommingstekens, spacers, grafische knoppen, geluiden (al dan niet met gebruikersinteractie), zelfstandige audiobestanden, audiotracks van video en video. | <ul><li>2.4 Verstrek tekstequivalenten voor beelden</li> <li>2.12 Ervoor zorgen dat alle multimedia-inhoud toegankelijk is</li> | |
| [ 1.2 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-redundant-server-links) | Verstrek overtollige tekstverbindingen voor elk actief gebied van een server-kant beeldkaart. | Niet van toepassing | |
| [ 1.3 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-auditory-descriptions) | Totdat gebruikersagenten automatisch het tekstequivalent van een visueel spoor kunnen lezen, verstrek een auditieve beschrijving van de belangrijke informatie van het visuele spoor van een presentatie van verschillende media. | 2.12 Ervoor zorgen dat alle multimedia-inhoud toegankelijk is | |
| [ 1.4 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-synchronize-equivalents) | Voor elke op tijd gebaseerde multimediapresentatie (bijvoorbeeld een film of animatie) moet u equivalente alternatieven (bijvoorbeeld bijschriften of auditieve beschrijvingen van de visuele track) synchroniseren met de presentatie. | 2.12 Ervoor zorgen dat alle multimedia-inhoud toegankelijk is | |
| [ 2.1 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-color-convey) | Zorg ervoor dat alle informatie die met kleur wordt overgebracht ook zonder kleur, bijvoorbeeld van context of prijsverhoging beschikbaar is. | 2.8 Kleur verantwoord gebruiken | |
| [ 4.1 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-identify-changes) | Wijzigingen in de natuurlijke taal van de tekst van een document en eventuele tekstequivalenten (bijvoorbeeld bijschriften) duidelijk identificeren. | 2.13 Wijzigingen in de taal identificeren | |
| [ 5.1 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-table-headers) | Voor gegevenslijsten, identificeer rij en kolomkopballen. | 2.9 Cellen met koppen voor tabellen opgeven | |
| [ 5.2 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-table-structure) | Voor gegevenslijsten die twee of meer logische niveaus van rij of kolomkopballen hebben, gebruik prijsverhoging om gegevenscellen en kopbalcellen te associëren. | 2.9 Cellen met koppen voor tabellen opgeven | |
| [ 6.1 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-order-style-sheets) | Documenten ordenen zodat ze zonder stijlpagina&#39;s kunnen worden gelezen. Wanneer een HTML-document bijvoorbeeld wordt gerenderd zonder gekoppelde stijlpagina&#39;s, moet het nog steeds mogelijk zijn het document te lezen. | Niet van toepassing | |
| [ 6.2 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-dynamic-source) | Zorg ervoor dat equivalenten voor dynamische inhoud worden bijgewerkt wanneer de dynamische inhoud verandert. | 2.11 Scripts niet verstoren | |
| [ 6.3 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-scripts) | Zorg ervoor dat pagina&#39;s bruikbaar zijn wanneer scripts, applets of andere programmatische objecten worden uitgeschakeld of niet worden ondersteund. Als dit niet mogelijk is, geef gelijkwaardige informatie op een andere toegankelijke pagina. | 2.11 Scripts niet verstoren | |
| [ 7.1 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-avoid-flicker) | Totdat de gebruikersagenten gebruikers toestaan om het flikkeren te controleren, vermijd veroorzakend het scherm om te flikkeren. | 2.1 Formulieren eenvoudig en gebruiksvriendelijk houden | |
| [ 9.1 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-client-side-maps) | Maak afbeeldingen met hyperlinks aan de clientzijde in plaats van afbeeldingen met hyperlinks aan de serverzijde, behalve waar de gebieden niet met een beschikbare geometrische vorm kunnen worden gedefinieerd. | Niet van toepassing | |
| [ 11.4 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-alt-pages) | Als u na de beste inspanningen geen toegankelijke pagina kunt maken, een koppeling naar een alternatieve pagina met W3C-technologieën kunt opgeven, toegankelijk is, gelijkwaardige informatie (of functionaliteit) heeft en zo vaak als de ontoegankelijke (originele) pagina wordt bijgewerkt. | Niet van toepassing | |
| [ 12.1 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-frame-titles) | Geef elk frame een titel om de identificatie en navigatie van frames te vergemakkelijken. | Niet van toepassing | |
| [ 14.1 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-simple-and-straightforward) | Gebruik de helderste en eenvoudigste taal die geschikt is voor de inhoud van een site. | 2.1 Formulieren eenvoudig en gebruiksvriendelijk houden | |

### WCAG 1.0 Prioriteit 2 Controlepunten

| Checkpoint voor prioriteit 2 | Beschrijving controlepunt | Aanbevolen best practices voor LiveCycle voor naleving | Notities |
|------------|------------------------|-------------------------------------------------|-------|
| [ 2.2 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-color-contrast) | Zorg ervoor dat de combinaties van voor- en achtergrondkleur voldoende contrast bieden bij weergave door iemand met een kleurdeficit of bij weergave op een zwart-witscherm. [ Prioriteit 2 voor beelden, Prioriteit 3 voor tekst ]. | 2.8 Kleur verantwoord gebruiken | |
| [ 3.1 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-use-markup) | Als er een geschikte markeringstaal bestaat, gebruikt u markering in plaats van afbeeldingen om informatie over te brengen. | <ul><li>2.1 Formulieren eenvoudig en gebruiksvriendelijk houden</li><li> 2.1.1 Verplaats, knipperende of knipperende inhoud niet</li> <li>2.2 Formuliereigenschappen configureren om toegankelijkheidsinformatie te genereren. Gebruik altijd de werkelijke tekst in plaats van afbeeldingen van tekst.</li> | |
| [ 3.2 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-identify-grammar) | Maak documenten die valideren naar gepubliceerde formele grammen. | | PDF forms moeten overeenkomen met de gepubliceerde PDF-specificatie om te kunnen worden weergegeven in Adobe Reader. |
| [ 3.3 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-style-sheets) | Stijlpagina&#39;s gebruiken om de indeling en presentatie te bepalen. | Niet van toepassing | |
| [ 3.4 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-relative-units) | Gebruik relatieve in plaats van absolute eenheden in kenmerkwaarden voor de opmaaktaal en eigenschapwaarden voor stijlbladen. | Niet van toepassing | |
| [ 3.5 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-logical-headings) | Gebruik koptekstelementen om de documentstructuur over te brengen en deze te gebruiken volgens de specificaties. | 2.10 Een navigeerbare formulierstructuur bieden | |
| [ 3.6 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-list-structure) | Lijsten en lijstitems correct markeren. | 2.10.3 het Markeren van omhoog maakt een lijst-gebaseerde inhoud als lijsten gebruikend de Lijsten en de rollen van het Punt van de Lijst. | |
| [ 3.7 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-quotes) | Aanhalingstekens markeren. Gebruik geen aanhalingstekens voor het opmaken van effecten zoals inspringing. | Niet van toepassing | |
| [ 5.3 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-avoid-table-for-layout) | Gebruik geen tabellen voor de indeling, tenzij de tabel zinvol is als de tabel wordt uitgelijnd. Anders, als de lijst geen nut heeft, verstrek een alternatief gelijkwaardig (die een linearzed versie kan zijn). | Geen specifieke LiveCycles | Er is geen reden om tabellen te gebruiken voor de indeling van LiveCycles. Gebruik in plaats daarvan het palet Indeling om de formuliervelden in een rasterpatroon te plaatsen. Gebruik een tabel alleen bij gebruik van tabelspecifieke functies, zoals tabelkoppen. |
| [ 5.4 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-table-layout) | Als een tabel wordt gebruikt voor de indeling, gebruikt u geen structuurmarkeringen voor de visuele opmaak. | Geen specifieke LiveCycles | |
| [ 6.4 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-keyboard-operable-scripts) | Voor scripts en applets moet u ervoor zorgen dat gebeurtenishandlers apparaatonafhankelijk zijn. | 2.7 Zorg ervoor dat formulierbesturingselementen via het toetsenbord toegankelijk zijn | |
| [ 6.5 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-fallback-page) | Zorg ervoor dat dynamische inhoud toegankelijk is of een alternatieve presentatie of pagina biedt. | 2.11 Scripts niet verstoren | |
| [ 7.2 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-avoid-blinking) | Totdat de gebruikersagenten gebruikers toestaan om het knipperen te controleren, vermijd veroorzakend dat de inhoud knippert (d.w.z., presentatie aan een regelmatige snelheid veranderen, zoals het aanzetten en weg). | 2.1 Formulieren eenvoudig en gebruiksvriendelijk houden | |
| [ 7.3 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-avoid-movement) | Vermijd verplaatsing op pagina&#39;s totdat gebruikers bewegende inhoud kunnen stilzetten door tussenkomst van gebruikersagenten. | 2.1 Formulieren eenvoudig en gebruiksvriendelijk houden | |
| [ 7.4 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-no-periodic-refresh) | Totdat gebruikersagenten de capaciteit verstrekken om te stoppen verfrist zich, creeer geen periodiek auto-verfrist pagina&#39;s. | Niet van toepassing | |
| [ 7.5 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-no-auto-forward) | Totdat gebruikersagenten de capaciteit verstrekken om auto-omleiding tegen te houden, gebruik geen prijsverhoging om pagina&#39;s automatisch om te leiden. In plaats daarvan configureert u de server om omleidingen uit te voeren. | Niet van toepassing | |
| [ 8.1 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-directly-accessible) | Maak programmatic elementen zoals manuscripten en applets direct toegankelijk of compatibel met ondersteunende technologieën [ Prioriteit 1 als de functionaliteit belangrijk is en niet elders, anders Prioriteit 2 wordt voorgesteld.] | 2.11 Scripts niet verstoren | |
| [ 9.2 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-keyboard-operable) | Zorg ervoor dat elk element met een eigen interface op een apparaatonafhankelijke manier kan worden gebruikt. | 2.7 Zorg ervoor dat formulierbesturingselementen via het toetsenbord toegankelijk zijn | |
| [ 9.3 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-device-independent-events) | Voor manuscripten, specificeer logische gebeurtenismanagers eerder dan apparaat-afhankelijke gebeurtenismanagers. | 2.7 Zorg ervoor dat formulierbesturingselementen via het toetsenbord toegankelijk zijn | |
| [ 10.1 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-avoid-pop-ups) | Totdat gebruikersagenten gebruikers toestaan om gekaapte vensters uit te zetten, veroorzaken geen pop-ups of andere vensters om te verschijnen en veranderen niet het huidige venster zonder de gebruiker op de hoogte te brengen. | 2.11 Scripts niet verstoren | |
| [ 10.2 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-unassociated-labels) | Totdat gebruikersagenten expliciete verenigingen tussen etiketten en vormcontroles steunen, voor alle vormcontroles met impliciet bijbehorende etiketten, zorg ervoor dat het etiket behoorlijk wordt geplaatst. | 2.5 Geef juiste labels voor formulierbesturingselementen | |
| [ 11.1 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-latest-w3c-specs) | Gebruik W3C-technologieën wanneer deze beschikbaar en geschikt zijn voor een taak en gebruik de nieuwste versies wanneer deze worden ondersteund. | Niet van toepassing | |
| [ 11.2 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-avoid-deprecated) | Vermijd vervangen functies van W3C-technologieën. | Niet van toepassing | |
| [ 12.2 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-frame-longdesc) | Beschrijf het doel van kaders en hoe de kaders op elkaar betrekking hebben als het niet door kadertitels alleen duidelijk is. | Niet van toepassing | |
| [ 12.3 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-group-information) | Verdeel grote blokken van informatie in beter te beheren groepen waar natuurlijk en aangewezen. | 2.10 Een navigeerbare formulierstructuur bieden | |
| [ 12.4 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-associate-labels) | Koppel labels expliciet aan hun besturingselementen. | 2.5 Geef juiste labels voor formulierbesturingselementen | |
| [ 13.1 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-meaningful-links) | Identificeer duidelijk het doel van elke verbinding. | 2.5 Geef juiste labels voor formulierbesturingselementen 2.5.6 Koppelingstekst | |
| [ 13.2 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-use-metadata) | Geef metagegevens op om semantische informatie toe te voegen aan pagina&#39;s en sites. | Niet van toepassing | |
| [ 13.3 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-site-description) | Geef informatie over de algemene lay-out van een site (bijvoorbeeld een site-overzicht of een inhoudsopgave). | 2.10 Een navigeerbare formulierstructuur bieden | |
| [ 13.4 ](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-clear-nav-mechanism) | Gebruik op consistente wijze navigatiemechanismen. | 2.10 Een navigeerbare formulierstructuur bieden | Basispagina&#39;s gebruiken om consistente navigatie-inhoud te maken. |

### WCAG 2.0 Succescriteria

| Prioriteit 1 G 2 Controlepunten | Aanbevolen best practices voor LiveCycle voor naleving | Notities |
| --- | --- | --- |
| 1.1 [ Alternatieven van de Tekst ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/text-equiv.html) | | |
| 1.1.1 [ Niet-tekstuele Inhoud ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/text-equiv-all.html) | 2.4 Verstrek tekstequivalenten voor beelden | |
| | 2.5 Geef juiste labels voor formulierbesturingselementen | |
| 1.2 [ op tijd-gebaseerde Media ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv.html) | | |
| 1.2.1 [ audio-slechts en video-slechts (Vooraf opgenomen) ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-av-only-alt.html) | 2.12 Zorg ervoor dat alle audio- en video-inhoud toegankelijk is | |
| 1.2.2 [ (Vooraf opgenomen) Bijschriften ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-captions.html) | 2.12 Zorg ervoor dat alle audio- en video-inhoud toegankelijk is | |
| 1.2.3 [ AudioBeschrijving of Alternatief van Media (vooraf opgenomen) ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-audio-desc.html) | 2.12 Zorg ervoor dat alle audio- en video-inhoud toegankelijk is | |
| 1.2.4 [ Bijschriften (Levend) ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-real-time-captions.html) | 2.12 Zorg ervoor dat alle audio- en video-inhoud toegankelijk is | |
| 1.2.5 [ AudioBeschrijving (vooraf opgenomen) ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-audio-desc-only.html) | 2.12 Zorg ervoor dat alle audio- en video-inhoud toegankelijk is | |
| 1.2.6 [ Taal van het Teken (vooraf opgenomen) ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-sign.html) | 2.12 Zorg ervoor dat alle audio- en video-inhoud toegankelijk is | |
| 1.2.7 [ Uitgebreide AudioBeschrijving (vooraf opgenomen) ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-extended-ad.html) | 2.12 Zorg ervoor dat alle audio- en video-inhoud toegankelijk is | |
| 1.2.8 [ Alternatieve Media (vooraf opgenomen) ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-text-doc.html) | 2.12 Zorg ervoor dat alle audio- en video-inhoud toegankelijk is | |
| 1.2.9 [ audio-slechts (Levend) ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-live-audio-only.html) | 2.12 Zorg ervoor dat alle audio- en video-inhoud toegankelijk is | |
| 1.3 [ Aanpasbaar ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/content-structure-separation.html) | | |
| 1.3.1 [ Info en Verhoudingen ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/content-structure-separation-programmatic.html) | 2.9 Cellen met koppen voor tabellen opgeven | |
| 1.3.2 [ Betekenisvolle Opeenvolging ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/content-structure-separation-sequence.html) | 2.6 Zorg ervoor dat de lees- en tabvolgorde correct zijn | |
| | 2.10 Een navigeerbare formulierstructuur bieden | |
| 1.3.3 [ Sensorische Kenmerken ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/content-structure-separation-understanding.html) | 2.8 Kleur verantwoord gebruiken | |
| 1.4 [ Distinguished ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast.html) | | |
| 1.4.1 [ Gebruik van Kleur ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-without-color.html) | 2.8 Kleur verantwoord gebruiken | |
| 1.4.2 [ AudioControle ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-dis-audio.html) | Geen specifieke LiveCycles | |
| 1.4.3 [ Contrast (Minimum) ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-contrast.html) | 2.8 Kleur verantwoord gebruiken | |
| 1.4.4 [ Resize tekst ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-scale.html) | Geen specifieke LiveCycles | |
| 1.4.5 [ Beelden van Tekst ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-text-presentation.html) | Geen specifieke LiveCycles | |
| 1.4.6 [ Contrast (Verbeterd) ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast7.html) | 2.8 Kleur verantwoord gebruiken | |
| 1.4.7 [ Laag of Geen Achtergrond Audio ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-noaudio.html) | Geen specifieke LiveCycles | |
| 1.4.9 [ Beelden van Tekst (Geen Uitzondering) ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-text-images.html) | Geen specifieke LiveCycles | |
| 2.1 [ Toegankelijk Toetsenbord ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/keyboard-operation.html) | | |
| 2.1.1 [ Toetsenbord ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/keyboard-operation-keyboard-operable.html) | 2.6 Zorg ervoor dat de lees- en tabvolgorde correct zijn | |
| | 2.7 Zorg ervoor dat formulierbesturingselementen via het toetsenbord toegankelijk zijn | |
| 2.1.2 [ Geen Overvul van het Toetsenbord ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/keyboard-operation-trapping.html) | 2.7 Zorg ervoor dat formulierbesturingselementen via het toetsenbord toegankelijk zijn | |
| 2.1.3 [ Keyboard (Geen Uitzondering) ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/keyboard-operation-all-funcs.html) | 2.6 Zorg ervoor dat de lees- en tabvolgorde correct zijn | |
| | 2.7 Zorg ervoor dat formulierbesturingselementen via het toetsenbord toegankelijk zijn | |
| 2.2 [ genoeg Tijd ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/time-limits.html) | | |
| 2.2.1 [ Aanpasbare timing ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/time-limits-required-behaviors.html) | Geen specifieke LiveCycles | |
| 2.2.2 [ Pauze, Einde, Verbergen ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/time-limits-pause.html) | 2.1 Formulieren eenvoudig en gebruiksvriendelijk houden | |
| 2.2.3 [ Geen timing ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/time-limits-no-exceptions.html) | Geen specifieke LiveCycles | |
| 2.2.4 [ Onderbrekingen ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/time-limits-postponed.html) | Geen specifieke LiveCycles | |
| 2.2.5 [ opnieuw voor authentiek makend ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/time-limits-server-timeout.html) | Geen specifieke LiveCycles | |
| 2.3 [ Convulsies ] | | |
| 2.3.1 [ Drie Flash of onder Drempel ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/seizure-does-not-violate.html) | 2.1 Formulieren eenvoudig en gebruiksvriendelijk houden | |
| 2.3.2 [ Drie Flash ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/seizure-three-times.html) | 2.1 Formulieren eenvoudig en gebruiksvriendelijk houden | |
| 2.4 [ Navigable ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms.html) | | |
| 2.4.1 [ Blokken van de Bypass ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-skip.html) | 2.10 Een navigeerbare formulierstructuur bieden | |
| 2.4.2 [ Getitelde Pagina ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-title.html) | Geen specifieke LiveCycles | |
| 2.4.3 [ Orde van de Nadruk ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-focus-order.html) | 2.6 Zorg ervoor dat de lees- en tabvolgorde correct zijn | |
| 2.4.4 [ Doel van de Verbinding (in context) ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-refs.html) | Geen specifieke LiveCycles | Het doel van een koppeling is afhankelijk van de keuze van auteurs voor betekenisvolle tekst voor gekoppelde elementen. |
| 2.4.5 [ Veelvoudige Manieren ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-mult-loc.html) | 2.10 Een navigeerbare formulierstructuur bieden | |
| 2.4.6 [ Koppen en Etiketten ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-descriptive.html) | <ul><li>2.5 Geef juiste labels voor formulierbesturingselementen</li><li>2.10 Een navigeerbare formulierstructuur bieden</li> | |
| 2.4.7 [ Zichtbare Nadruk ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-focus-visible.html) | Geen specifieke LiveCycles | De standaardfocus in LiveCycles formulieren is zichtbaar. |
| 2.4.8 [ Plaats ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-location.html) | Geen specifieke LiveCycles | Niet van toepassing: voor formulieren van LiveCycles zijn geen navigatiesystemen vereist. |
| 2.4.9 [ Doel van de Verbinding (Verbinding slechts) ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-link.html) | Geen specifieke LiveCycles | Het doel van een koppeling is afhankelijk van de keuze van auteurs voor betekenisvolle tekst voor gekoppelde elementen. |
| 2.4.10 [ Koppen van de Sectie ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-headings.html) | 2.10 Een navigeerbare formulierstructuur bieden | |
| 3.1 [ Leesbaar ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/meaning.html) | | |
| 3.1.1 [ Taal van Pagina ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/meaning-doc-lang-id.html) | 2.13 Identificeer de natuurlijke taal en eventuele taalwijzigingen | |
| 3.1.2 [ Taal van Delen ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/meaning-other-lang-id.html) | 2.13 Identificeer de natuurlijke taal en eventuele taalwijzigingen | |
| 3.1.3 [ Ongebruikelijke Woorden ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/meaning-idioms.html) | Geen specifieke LiveCycles | |
| 3.1.4 [ Afkortingen ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/meaning-located.html) | Geen specifieke LiveCycles | |
| 3.1.5 [ Leesniveau ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/meaning-supplements.html) | Geen specifieke LiveCycles | |
| 3.1.6 [ Uitspraak ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/meaning-pronunciation.html) | Geen specifieke LiveCycles | |
| 3.2 [ voorspelbaar ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/consistent-behavior.html) | | |
| 3.2.1 [ op nadruk ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/consistent-behavior-receive-focus.html) | 2.11 Scripts niet verstoren | |
| 3.2.2 [ op input ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/consistent-behavior-unpredictable-change.html) | 2.11 Scripts niet verstoren | |
| 3.2.3 [ Consistente Navigatie ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/consistent-behavior-consistent-locations.html) | 2.10 Een navigeerbare formulierstructuur bieden | |
| 3.2.4 [ Consistente Identificatie ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/consistent-behavior-consistent-functionality.html) | <ul><li>2.3 Kies de juiste besturingselementen</li><li>2.5 Geef juiste labels voor formulierbesturingselementen</li> | |
| 3.2.5 [ Verandering op Verzoek ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/consistent-behavior-no-extreme-changes-context.html) | 2.11 Scripts niet verstoren | |
| 3.3 [ Hulp van de Input ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/minimize-error.html) | | |
| 3.3.1 [ Identificatie van de Fout ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/minimize-error-identified.html) |  | LiveCycle Designer biedt gereedschappen om formuliervelden naar wens te markeren en validatie van formulierinvoer uit te voeren. |
| 3.3.2 [ Etiketten of Instructies ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/minimize-error-cues.html) | 2.5 Geef juiste labels voor formulierbesturingselementen | |
| 3.3.3 [ Suggestie van de Fout ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/minimize-error-suggestions.html) |  | LiveCycle Designer biedt gereedschappen om formuliervelden naar wens te markeren en validatie van formulierinvoer uit te voeren. |
| 3.3.4 [ Preventie van de Fout (Juridisch, Financieel, Gegevens) ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/minimize-error-reversible.html) | Geen specifieke LiveCycles | |
| 3.3.5 [ Hulp ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/minimize-error-context-help.html) | Geen specifieke LiveCycles | |
| 3.3.6 [ Preventie van de Fout (allen) ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/minimize-error-reversible-all.html) | Geen specifieke LiveCycles | |
| 4.1 [ Compatibel ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/ensure-compat.html) | | |
| 4.1.1 [ het ontleden ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/ensure-compat-parses.html) | Geen specifieke LiveCycles | |
| 4.1.2 [ Naam, Rol, Waarde ](https://www.w3.org/TR/UNDERSTANDING-WCAG20/ensure-compat-rsv.html) | <ul><li>2.3 Kies de juiste besturingselementen</li> <li>2.5 Geef juiste labels voor formulierbesturingselementen</li> | |



