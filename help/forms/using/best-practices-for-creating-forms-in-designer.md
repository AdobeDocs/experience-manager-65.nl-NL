---
title: Aanbevolen procedures voor het maken van formulieren in formulierontwerper
description: Meer informatie over de beste toegankelijkheidsprocedures voor het maken van formulieren in formulierontwerpers
feature: Adaptive Forms, Forms Designer
solution: Experience Manager, Experience Manager Forms
role: User, Developer
hide: true
hidefromtoc: true
source-git-commit: 6b86212a2b3a86b2205714c802dc1581d30e7441
workflow-type: tm+mt
source-wordcount: '11687'
ht-degree: 0%

---

# Aanbevolen procedures voor het maken van formulieren in formulierontwerper

Met LiveCycle Designer kunt u rijke formulierinhoud maken en voldoen aan de richtlijnen van Section 508. Deze handleiding bevat een overzicht van de beste praktijken voor het maken van een toegankelijk formulier en richtlijnen voor het implementeren van deze beste praktijken met behulp van LiveCycle Designer. De volgende aanbevolen procedures worden behandeld:

1. [Formulieren eenvoudig en gebruiksvriendelijk houden](#keep-simple)
1. [Formuliereigenschappen configureren om toegankelijkheidsinformatie te genereren](#configure-form-properties)
1. [Kies de juiste besturingselementen](#choose-right-controls)
1. [Verstrek tekstequivalenten voor beelden](#provide-text-equivalents)
1. [Geef juiste labels voor formulierbesturingselementen](#provide-proper-labels)
1. [Zorg ervoor dat de lees- en tabvolgorde correct zijn](#ensure-reading-tab-order)
1. [Zorg ervoor dat formulierbesturingselementen via het toetsenbord toegankelijk zijn](#ensure-keyboard-accessible)
1. [Kleur verantwoord gebruiken](#use-color-responsibly)
1. [Kopcellen voor tabellen opgeven](#provide-heading-cells)
1. [Een naviderbare formulierstructuur opgeven](#provide-navigable-form)
1. [Vermijd verstorende scripts](#avoid-disruptive-scripting)
1. [Controleer of alle audio- en video-inhoud toegankelijk is](#ensure-audio-video-accessible)
1. [Identificeer natuurlijke taal en om het even welke veranderingen in taal](#identify-natural-language)

## Formulieren eenvoudig en gebruiksvriendelijk houden {#keep-simple}

Een formulier is niet toegankelijk als het niet gebruiksvriendelijk is. Probeer formulieren te ontwerpen die eenvoudig en bruikbaar zijn. Een eenvoudige indeling van besturingselementen en velden met duidelijke, betekenisvolle bijschriften en knopinfo maakt het formulier veel gemakkelijker voor alle gebruikers.
Door het ontwerpen van formulieren die overzichtelijk en logisch zijn gerangschikt en duidelijke en eenvoudige instructies bevatten, kunnen alle gebruikers de formulieren zo eenvoudig mogelijk invullen. Navigatiefuncties, zoals de tabvolgorde en sneltoetsen, moeten de logische volgorde van objecten op het formulier ondersteunen.

### Vermijd het verplaatsen, knipperen of knipperen van inhoud

Sommige personen met fotogevoelige epilepsie kunnen een aanval krijgen die wordt veroorzaakt door beweging in frequenties groter dan 2 Hz (1 Hz, of Hertz, is gelijk aan 1 per seconde) en lager dan 55 Hz (55 per seconde).

Beweging bij minder dan 2 Hz wordt als traag genoeg beschouwd om veilig te zijn voor personen met fotogevoelige epilepsie. Beweging bij meer dan 55 Hz wordt als onwaarneembaar beschouwd.

Ontwikkelaars dienen zich bewust te zijn van deze parameters wanneer ze een beweging in webinhoud gebruiken.

Andere gebruikers kunnen cognitieve handicaps hebben die het moeilijk maken zich te concentreren wanneer er geanimeerde of knipperende inhoud in de vorm aanwezig is.

Probeer over het algemeen geen optische effecten te gebruiken die door scripts, zoals knipperende tekst of animatie, in interactieve formulieren zijn ingevoegd. Dergelijke effecten verminderen de bruikbaarheid van de formulieren voor bepaalde gebruikers.

Gerelateerde controlepunten
* § 508 § 1934.21

   * h) Wanneer animatie wordt weergegeven, moet de informatie, naar keuze van de gebruiker, in ten minste één niet-geanimeerde presentatiemodus kunnen worden weergegeven.
   * k) Software mag geen knipperende of knipperende tekst, objecten of andere elementen gebruiken met een flash- of knipperfrequentie van meer dan 2 Hz en minder dan 55 Hz.
* § 508 § 1934.22
   * j) De pagina&#39;s moeten zo zijn ontworpen dat het scherm niet flikkert met een frequentie van meer dan 2 Hz en minder dan 55 Hz.
* WCAG 1.0
   * 7.1 Totdat de gebruikersagenten gebruikers toestaan om het flikkeren te controleren, vermijd veroorzakend het scherm om te flikkeren. (P1)
   * 7.2 Totdat gebruikers de mogelijkheid hebben om knipperen te controleren, moet u voorkomen dat inhoud knippert (d.w.z. dat de presentatie regelmatig wordt gewijzigd, zoals in- en uitgeschakeld) (P2).
   * 7.3 Vermijd verplaatsing van pagina&#39;s totdat gebruikers de mogelijkheid hebben om bewegende inhoud te bevriezen.
   * 14.1 Gebruik de duidelijkste en eenvoudigste taal die geschikt is voor de inhoud van een site.
* WCAG 2.0
   * 2.2.2 Pauze, Stoppen, Verbergen: voor het verplaatsen, knipperen, schuiven of automatisch bijwerken van gegevens, gelden alle volgende voorwaarden: (Niveau A)
   * 2.3.1 Drie Flash of onder Drempel: Webpagina&#39;s bevatten niets dat meer dan drie keer knippert in een periode van één seconde, of de flits is onder de algemene flits en rode flitsdrempels. (Niveau A)
   * 2.3.2 Drie Flash: De Web-pagina&#39;s bevatten niets die meer dan drie keer in om het even welke tweede periode knippert. (Niveau AAA)


## Formuliereigenschappen configureren om toegankelijkheidsinformatie te genereren {#configure-form-properties}

Voor een vorm om toegankelijk te zijn, moet het [ waarneembaar ](https://www.w3.org/TR/WCAG20/#perceivable) door ondersteunende technologie zijn. De meeste schermlezers overwegen bijvoorbeeld niet de visuele indeling van het formulier, maar de onderliggende structuur.

Als u deze onderliggende structuur wilt implementeren met LiveCycle Designer, moet u een PDF-formulier maken met toegankelijkheidsinformatie (ook wel codes genoemd), zodat de schermlezer of andere ondersteunende hulpmiddelen de tekst en onderdelen van het formulier kunnen lezen. In een formulier met toegankelijkheidsinformatie bevat elk element informatie over de eigen structuur, plus informatie over hoe het verwant is aan of afhankelijk is van andere elementen. Alleen in PDF-bestanden waarin toegankelijkheidsinformatie is opgenomen, kunnen schermlezers de inhoud van een document nauwkeurig identificeren en beschrijven.

Als u een toegankelijk formulier wilt maken, moet u formuliereigenschappen zodanig configureren dat LiveCycle Designer toegankelijkheidsinformatie genereert wanneer het formulierontwerp wordt opgeslagen als een PDF-bestand:
1. Kies Bestand > Formuliereigenschappen.
1. Klik op het tabblad Opslagopties en schakel in het gebied PDF de optie Toegankelijkheidsinformatie (codes) genereren voor Acrobat in.
1. Klik op OK.

In LiveCycle Designer is deze optie standaard ingeschakeld.

>[!NOTE]
> Deze opties zijn alleen van toepassing wanneer u het formulierontwerp opslaat als een PDF-bestand. Ze zijn niet van toepassing op PDF-bestanden die zijn gemaakt met LiveCycle Forms en die configuratieopties hebben die onafhankelijk zijn van deze optie in LiveCycle Designer.

**Verwante controlepunten**

* § 508 § 194.21
   * (d) Voor ondersteunende hulpmiddelen moet voldoende informatie over een gebruikersinterface-element beschikbaar zijn, met inbegrip van de identiteit, de werking en de toestand van het element. Wanneer een afbeelding een programma-element vertegenwoordigt, moet de informatie die door de afbeelding wordt getoond ook in tekst beschikbaar zijn.
   * l) Wanneer elektronische formulieren worden gebruikt, stelt het formulier personen die gebruikmaken van ondersteunende hulpmiddelen in staat toegang te krijgen tot de informatie, veldelementen en functionaliteit die vereist zijn voor het invullen en verzenden van het formulier, met inbegrip van alle aanwijzingen en aanwijzingen.
* § 508 § 194.22
   * n) Wanneer elektronische formulieren zijn ontworpen om online te worden ingevuld, stelt het formulier mensen die gebruikmaken van ondersteunende hulpmiddelen in staat toegang te krijgen tot de informatie, veldelementen en functionaliteit die vereist zijn voor het invullen en verzenden van het formulier, met inbegrip van alle aanwijzingen en aanwijzingen.


## Kies de juiste besturingselementen {#choose-right-controls}

Wanneer u uw formulieren ontwerpt, gebruikt u ontwikkelingsobjecten op de tabbladen die beschikbaar zijn in de Objectbibliotheek van LiveCycle Designer. U kunt dit deelvenster weergeven door Venster > Objectbibliotheek te kiezen of op Shift+F12 te drukken (zie Figuur 1).

![ het Comité van de Bibliotheek van Objecten ](/help/forms/using/assets/image-1.png)

Figuur 1: **het Comité van de Bibliotheek van Objecten**

Als u andere objecten gebruikt, worden deze mogelijk genegeerd door hulpprogramma&#39;s. Als u alleen de standaardobjecten gebruikt, hoeft u alleen nog maar toegankelijkheidseigenschappen te definiëren voor objecten die u zelf hebt gemaakt. Als u wel eigen aangepaste objecten maakt en gebruikt, moet u het palet Toegankelijkheid gebruiken om toegankelijkheidseigenschappen in te stellen, zoals Rol, Knopinfo, Voorrang van Reader scherm en Aangepaste schermtekst. Kies Venster > Toegankelijkheid om het palet Toegankelijkheid weer te geven.

**Verwante controlepunten**
* § 508 § 194.21
   * (c) Er moet een duidelijk gedefinieerde indicatie op het scherm van de huidige focus worden gegeven die tussen interactieve interface-elementen beweegt naarmate de invoerfocus verandert. De focus wordt via programmacode beschikbaar gemaakt, zodat ondersteunende technologie de focus en focusveranderingen kan volgen.
   * (d) Voor ondersteunende hulpmiddelen moet voldoende informatie over een gebruikersinterface-element beschikbaar zijn, met inbegrip van de identiteit, de werking en de toestand van het element. Wanneer een afbeelding een programma-element vertegenwoordigt, moet de informatie die door de afbeelding wordt getoond ook in tekst beschikbaar zijn.
   * l) Wanneer elektronische formulieren worden gebruikt, stelt het formulier personen die gebruikmaken van ondersteunende hulpmiddelen in staat toegang te krijgen tot de informatie, veldelementen en functionaliteit die vereist zijn voor het invullen en verzenden van het formulier, met inbegrip van alle aanwijzingen en aanwijzingen.
* § 508 § 194.22
   * n) Wanneer elektronische formulieren zijn ontworpen om online te worden ingevuld, stelt het formulier mensen die gebruikmaken van ondersteunende hulpmiddelen in staat toegang te krijgen tot de informatie, veldelementen en functionaliteit die vereist zijn voor het invullen en verzenden van het formulier, met inbegrip van alle aanwijzingen en aanwijzingen.

* WCAG 2.0
   * 3.2.4 Consistente identificatie: Componenten met dezelfde functionaliteit binnen een set webpagina&#39;s worden op consistente wijze geïdentificeerd. (Niveau AA).
   * 4.1.2 Naam, Rol, Waarde: Voor alle gebruikersinterfacecomponenten (inclusief maar niet beperkt tot: formulierelementen, koppelingen en componenten die door scripts worden gegenereerd) kunnen de naam en de rol via programmacode worden bepaald; statussen, eigenschappen en waarden die door de gebruiker kunnen worden ingesteld, kunnen via programmacode worden ingesteld; en meldingen van wijzigingen in deze items zijn beschikbaar voor gebruikersagenten, inclusief ondersteunende technologieën. (Niveau A)


## Verstrek tekstequivalenten voor beelden {#provide-text-equivalents}

Afbeeldingen kunnen gebruikers met bepaalde handicaps helpen het begrip te verbeteren. Voor gebruikers van schermlezers zullen afbeeldingen de toegankelijkheid van het formulier echter verkleinen als u geen tekstueel alternatief biedt.

Als u ervoor kiest afbeeldingen te gebruiken, geef dan tekstbeschrijvingen op voor alle afbeeldings- en afbeeldingsveldobjecten. Zorg ervoor dat in de tekst het object en het doel op het formulier worden beschreven. Wanneer u een alternatief voor tekst definieert, leest de schermlezer dit alternatief wanneer de afbeelding wordt aangetroffen. Daarom moet voor een afbeelding met informatie altijd een alternatief voor de tekst zijn opgegeven.

U kunt tekstbeschrijvingen opgeven met de teksteigenschappen Knopinfo of Aangepast scherm Reader in het palet Toegankelijkheid of via tekstvelden, bijschriften en objectnamen, zoals opgegeven in de optie Naam op het tabblad Binding. Figuur 2 toont bijvoorbeeld een voorbeeld van een afbeelding met de tekst &#39;Adobe Reader ophalen&#39;. Aangezien een schermlezer geen tekst kan lezen die deel uitmaakt van een afbeelding, moet u een tekstalternatief opnemen in het veld Tekst aangepaste Reader scherm in het palet Toegankelijkheid voor dit object. In de meeste gevallen moet de alternatieve tekst hetzelfde zijn als de tekst die in de afbeelding zichtbaar is (zie Figuur 2).

![ die alternatieve tekst voor een beeld specificeren gebruikend het palet van de Toegankelijkheid ](/help/forms/using/assets/image-2.png)

Figuur 2: **specificerend alternatieve tekst voor een beeld gebruikend het palet van de Toegankelijkheid**

Houd rekening met het volgende wanneer u de alternatieve tekst opgeeft:
* Als het afbeeldingsobject of de gescande afbeelding belangrijke informatie voor het formulier bevat, maakt u in het palet Toegankelijkheid tekst voor de afbeelding waarin het object en het doel worden beschreven. De tekst voor een bedrijfslogo kan bijvoorbeeld bestaan uit de woorden &quot;bedrijfslogo&quot; en de naam van het bedrijf.
* Als het afbeeldingsobject semantische kleurgegevens bevat, neemt u deze ook op in de beschrijving. Een beschrijving van een groen licht zou bijvoorbeeld &quot;Transmissie succesvol&quot;kunnen zijn en de beschrijving van een rood licht zou &quot;Transmissie ontbroken&quot;kunnen zijn.
* Als u complexe afbeeldingen gebruikt, zoals staafdiagrammen, geeft u de informatie op in een andere toegankelijke versie, zoals een tabel of een langere tekstuele beschrijving.
* Maak geen tekstbeschrijvingen voor statische afbeeldingen die alleen voor decoratie worden gebruikt.
* Gebruik gescande gegevens niet als achtergrondinformatie. Dit kan gebeuren als een ontwerper een afdrukformulier scant en Adobe LiveCycle Designer gebruikt om nieuwe velden aan het formulier toe te voegen. Schermlezers kunnen de gescande gegevens in deze status niet detecteren.

Wanneer u zuiver decoratieve grafische inhoud in uw formulieren opneemt, moet u ervoor zorgen dat schermlezers de aanwezigheid van de afbeelding niet aankondigen. Voor de meeste schermlezers kunt u dit bereiken door de eigenschap Tekst van Reader scherm in te stellen op Geen in het palet Toegankelijkheid. Als u dit niet doet, kunnen sommige schermlezers de aanwezigheid van een afbeelding aankondigen zonder aan te geven wat de afbeelding vertegenwoordigt. Voor dynamische afbeeldingen, zoals afbeeldingsveldobjecten, moet u ervoor zorgen dat tekstalternatieven correct worden bijgewerkt wanneer de afbeelding wordt gewijzigd. Maak geen tekstbeschrijvingen voor afbeeldingsveldobjecten die alleen voor decoratie worden gebruikt. U kunt de scripttaal FormCalc gebruiken om dynamisch tekstbeschrijvingen toe te wijzen aan een afbeeldingsveldobject. FormCalc is de standaardscripttaal van Adobe LiveCycle Designer. Neem bijvoorbeeld een formulier met een afbeeldingsveld met de naam ImageField1 en de bijbehorende tekst in het afbeeldingstekstknooppunt van de runtime-gegevens. Met scripts kunt u deze tekst in een geschikte gebeurtenis (zoals `form:ready` ) als volgt doorgeven:

`ImageField1.assist.toolTip = $record.imagetext.value`

Gerelateerde controlepunten
* § 508 § 194.22
   * a) Voor elk niet-tekstequivalent moet een tekstequivalent worden opgegeven (bv. via &quot;alt&quot;, &quot;longdesc&quot; of in elementinhoud).
* WCAG 1.0
   * 1.1 Geef een tekstequivalent op voor elk niet-tekstelement (bijvoorbeeld via &quot;alt&quot;, &quot;longdesc&quot; of in elementinhoud). Dit omvat: afbeeldingen, grafische voorstellingen van tekst (inclusief symbolen), gebieden met afbeeldingen met hyperlinks, animaties (bijvoorbeeld geanimeerde GIFFEN), applets en programmatische objecten, ascii-illustraties, frames, scripts, afbeeldingen die worden gebruikt als lijstopsommingstekens, spacers, grafische knoppen, geluiden (al dan niet met gebruikersinteractie), zelfstandige audiobestanden, audiotracks van video en video (P1).
* WCAG 2.0
   * 1.1.1 Niet-tekstuele inhoud: alle niet-tekstuele inhoud die aan de gebruiker wordt aangeboden, heeft een tekstalternatief dat hetzelfde doel dient, behalve in de situaties hieronder. (Niveau A)


## Geef juiste labels voor formulierbesturingselementen{#provide-proper-labels}

Het label of bijschrift van een formulierbesturingselement geeft aan wat het formulierbesturingselement moet vertegenwoordigen. De tekst Voornaam geeft bijvoorbeeld aan dat gebruikers hun voornaam in een tekstveld moeten invoeren. Om door schermlezers toegankelijk te zijn, moet het etiket programmatically met de vormcontrole worden geassocieerd of de vormcontrole moet met extra toegankelijkheidsinformatie worden gevormd gebruikend het palet van de Toegankelijkheid; het is niet genoeg om een tekstvoorwerp naast de controle te plaatsen. Voor waargenomen of slechtziende gebruikers is het belangrijk dat het etiket behoorlijk naast de controle wordt geplaatst. Beide technieken worden in de volgende secties besproken.

### Toegankelijke labeltekst opgeven met het palet Toegankelijkheid

Het label dat door gebruikers van schermlezers wordt waargenomen, hoeft niet noodzakelijkerwijs hetzelfde te zijn als het visuele bijschrift. In sommige gevallen wilt u wellicht specifieker zijn over het doel van het besturingselement.
Voor elk veldobject in een formulier kunt u met het palet Toegankelijkheid (zie Figuur 3) opgeven wat de schermlezer zal aankondigen om het specifieke formulierveld te identificeren.
Voer de volgende stappen uit om het palet Toegankelijkheid te gebruiken:
1. Geef het palet Toegankelijkheid weer door Venster > Toegankelijkheid te kiezen of door op Shift+F6 te drukken.
1. Selecteer een object in het formulier. In het palet worden de toegankelijkheidseigenschappen van het object weergegeven.

![ het palet van de Toegankelijkheid ](/help/forms/using/assets/image-3.png)

Figuur 3: **het palet van de Toegankelijkheid**

Wanneer het formulier wordt opgeslagen als een PDF, zoekt LiveCycle Designer in dat geval in het formulier naar de eigenschappen Eigen tekst, Knopinfo, Bijschrift en Naam, in die volgorde om tekst te zoeken die door schermlezers moet worden gelezen. U kunt deze standaardvolgorde overschrijven met de optie Voorrang van Reader scherm in het palet Toegankelijkheid:

1. Selecteer het object in het formulierontwerp.
1. Klik op het palet Toegankelijkheid.
1. Selecteer een andere optie voor de prioriteit Reader van scherm dan Geen.

De volgende opties zijn beschikbaar:

* **Tekst van de Douane**, die u in het gebied van de Tekst van de Reader van het Scherm van de Toegankelijkheid van het palet van de Douane plaatst. Met deze optie kunt u alle tekst opgeven die u wilt gebruiken in de hulpprogramma&#39;s, zoals schermlezers. Het gebruik van de instelling Bijschrift is in de meeste gevallen het meest geschikt. Het maken van aangepaste schermtekst moet alleen als een optie worden beschouwd wanneer het gebruik van Bijschrift of een toolTip niet mogelijk is.
* **Uiteinde van het Hulpmiddel**, die u op het gebied van het Uiteinde van het Hulpmiddel van het palet van de Toegankelijkheid plaatst. Voor de meeste objecten wordt knopinfo weergegeven bij uitvoering wanneer de gebruiker de aanwijzer op het object plaatst. Knopinfo wordt alleen weergegeven voor bepaalde alleen-lezen objecten, zoals het object Streepjescode van een papieren formulier, wanneer een schermlezer wordt gebruikt.
* **Titel**, die LiveCycle Designer zal veroorzaken om het bijbehorende (visuele) etiket van het vormgebied als het schermlezertekst te gebruiken.
* **Naam**, die u op het Bindende gebied van de Naam van het lusje plaatst. Deze naam mag geen spaties bevatten.
* **niets**, wat het voorwerp zal veroorzaken om geen naam te hebben. Dit wordt nooit aanbevolen voor formulierbesturingselementen.

Houd rekening met het volgende wanneer u het palet Toegankelijkheid gebruikt voor formulierbesturingselementlabels:

* Als het bijschrift van het formulierbesturingselement het besturingselement correct beschrijft, is het toegankelijk voor schermlezers. In dit geval laat u zowel de velden Aangepaste tekst als Knopinfo leeg in het palet Toegankelijkheid, of wijzigt u de prioriteit SchermReader in Bijschrift.
* Wanneer het richten van het schermlezers, is er geen punt om verschillende tekstbeschrijvingen voor de zelfde vormcontrole te specificeren, aangezien slechts één zal worden gebruikt: Het eerste niet lege gebied in de Volgorde van de Reader van het Scherm. Er is bijvoorbeeld geen reden om zowel aangepaste tekst als knopinfo voor een schermlezer op te geven.
* Standaard leest de schermlezer het bijschrift als er niets is opgegeven in het vak Knopinfo of Aangepast scherm, tekst in de Reader.
* Gebruik het palet Toegankelijkheid niet om beschrijvingen te maken voor onzichtbare velden of gebieden.
* Als u een beschrijving moet maken met de opties Knopinfo of Aangepaste Reader tekst, neemt u altijd het bijschrift op dat zichtbaar is op het formulier, behalve wanneer het zichtbare bijschrift geen betekenis heeft, bijvoorbeeld wanneer het bijschrift zelf wordt afgekort. Hierdoor kunnen gebruikers van schermlezers effectief communiceren met andere gebruikers over interface-elementen. Deze verschillende groepen gebruikers kunnen moeilijk hetzelfde interface-element identificeren als de bijschrifttekst afwijkt van de tekst voor Knopinfo of Aangepast scherm Reader.
* Voor selectievakjes en besturingselementen voor vervolgkeuzelijsten in tabelcellen kondigt de schermlezer een bijschrift, knopinfo of aangepaste schermlezertekst aan die u voor het object opgeeft. Als u de kolomkop voor de alternatieve tekst voor deze objecten wilt gebruiken wanneer u deze in een tabel plaatst, moet u geen bijschrift, knopinfo of aangepaste schermlezertekst opgeven.
* Als het besturingselement aanvullende instructies vereist, moet u ervoor zorgen dat deze ook in het tekstalternatief worden opgenomen. Neem voldoende gesproken informatie op voor gebruikers om te weten welke invoer wordt verwacht en hoe het veld correct moet worden ingevuld, maar vervaag gebruikers niet met overbodige informatie.
* Verstrek niet onnodige informatie die beschrijft hoe te om controles in werking te stellen - laat de hulptechnologieën van de gebruiker dit voor de gebruiker behandelen. Gebruikers kunnen de uitgebreide configuratie aanpassen aan hun comfortniveau.

Figuur 4 toont een voorbeeld van een tekstgebied met een visuele titel die voor sommige gebruikers van het schermlezer onduidelijk kan zijn. In dit voorbeeld is Aangepast scherm Readers Tekst ingesteld op Aantal pagina&#39;s en is de voorkeur voor Reader scherm ingesteld op Aangepaste tekst. Hierdoor wordt de werkelijke (visuele) bijschrifttekst (&quot;# pagina&#39;s&quot;) niet gebruikt door de schermlezer. U kunt ook een knopinfo opgeven.

![ specificerend de Tekst van de Reader van het Scherm van de Douane wanneer het zichtbare etiket ontoereikend is ](/help/forms/using/assets/image-4.png)

Figuur 4: **specificerend de Tekst van de Reader van het Scherm van de Douane wanneer het zichtbare etiket ontoereikend is**

### Keuzerondjes labelen

Wanneer een gebruiker met een visuele handicap met de Tab-toets naar een keuzerondje gaat, moet de schermlezer twee dingen lezen:
* Een aanduiding van het doel van de groep keuzerondjes
* Een betekenisvol label voor elk keuzerondje
Keuzerondjes toegankelijk maken met de bijschriften van de knoppen:
   1. Selecteer in het palet Hiërarchie de uitsluitingsgroep.
   1. Klik op het palet Toegankelijkheid en typ in het vak Tekst van Reader Aangepast scherm de tekst die u voor de groep wilt lezen. Voor een uitsluitingsgroep die bijvoorbeeld opties voor betaling per creditcard aangeeft, typt u Een betalingsmethode selecteren.
   1. Als de bijschriften voor elk keuzerondje tekst bevatten die zinvol is wanneer deze door een schermlezer wordt gesproken, selecteert u in het palet Object het tabblad Binding en schakelt u de optie Itemwaarde opgeven uit.

  Keuzerondjes toegankelijk maken met een opgegeven itemwaarde:
   1. Selecteer in het palet Hiërarchie de uitsluitingsgroep.
   1. Klik op het palet Toegankelijkheid en typ in het vak Tekst van Reader Aangepast scherm de tekst die u voor de groep wilt lezen. Voor een uitsluitingsgroep die bijvoorbeeld opties voor betaling per creditcard aangeeft, typt u Een betalingsmethode selecteren.
   1. Selecteer in het palet Hiërarchie het eerste keuzerondje in de groep.
   1. Klik in het palet Object op het tabblad Veld. Dubbelklik in het gebied Item op het item en typ een betekenisvolle waarde voor het geselecteerde keuzerondje. Voor de eerste knop in een groep betalingsmethoden typt u bijvoorbeeld Contant.
   1. Herhaal stap 3 en 4 voor elk keuzerondje in de uitsluitingsgroep.

### Aangepaste besturingselementen labelen

Het wordt sterk geadviseerd om standaardcomponenten eerder dan douanecomponenten te gebruiken, aangezien zij de hulptechnologie van de correcte aanwijzingen en informatie door gebrek zullen voorzien. Als echter aangepaste besturingselementen worden gebruikt, kunt u het volgende overwegen:
* Geef de status van selectievakjes en keuzerondjes weer.
* Geef in keuzelijsten en vervolgkeuzelijsten aan welk item standaard in de lijst is geselecteerd. Zorg ervoor dat de gebruiker weet dat hij of zij de toetsen Pijl-omhoog en Pijl-omlaag gebruikt om door de lijstitems te gaan. Houd er rekening mee dat als u op Tab of Enter of Return drukt, het item in de lijst wordt geselecteerd. Met behulp van scripts kunt u de gebeurtenis Change van het object zo instellen dat wordt aangekondigd welk item in de lijst is geselecteerd.
* Laat gebruikers weten welke speciale toetsaanslagen ze nodig hebben om een functie uit te voeren. Druk bijvoorbeeld op de spatiebalk om een knop te selecteren of druk op Pijl-omlaag om een item in een keuzelijst te selecteren.

### Correct positioneren van het bijschrift van een besturingselement

De plaatsing van een titel is belangrijk omdat de gebruikers hen zullen verwachten om naast de controle worden gevonden. Voor gebruikers met schermvergroting is dit nog belangrijker, omdat zij niet tegelijkertijd zowel het besturingselement als het bijschrift kunnen bekijken als ze te ver van elkaar verwijderd zijn.

Wanneer u een object maakt, plaatst LiveCycle Designer automatisch het bijschrift zoals opgegeven door het objecttype. De bijschriften van keuzerondjes worden bijvoorbeeld rechts geplaatst. Deze standaardplaatsing is altijd de beste locatie voor een toegankelijk bijschrift. Voer de volgende stappen uit als u de positie van de bijschrifttekst moet wijzigen:
1. Selecteer het object door de focus ernaar te verplaatsen.
1. Selecteer in het palet Indeling de positie van het bijschrift van het object via de optie Positie in de sectie Bijschrift, onder in het palet.

Het voorbeeld in Figuur 5 toont een tekstvakje met een titel boven het. De positie in het palet Indeling is ingesteld op Boven. De standaardlocatie van het bijschrift bevindt zich links van het tekstvak.

![ Veranderende ondertitel die het palet van de Lay-out plaatst ](/help/forms/using/assets/image-5.png)

Figuur 5: **Veranderende ondertitel die het palet van de Lay-out** plaatst

De volgende lijst verstrekt een overzicht van de regels van de etiketplaatsing voor algemeen gebruikte controles.

| Type besturingselement | Plaatsingsregels |
|--------------|-----------------|
| Tekstinvoer (inclusief datum-, tijd- en wachtwoordvelden) | Plaats de titel links van de controle (gebrek). Als dit niet mogelijk is, plaatst u het direct boven of onder het scherm. De etiketten zouden dicht bij de controle voor gebruikers met verhoogde vergroting moeten worden geplaatst zodat het etiket en de controle eerder samen in de vergrote mening worden gezien. |
| Selectievakje | Plaats het bijschrift rechts van het selectievakje (standaard). Voor besturingselementen in tabelcellen kondigt de schermlezer een bijschrift, knopinfo of aangepaste schermlezertekst aan die u voor het object opgeeft. Als u de kolomkop wilt gebruiken als alternatieve tekst voor een selectievakje in een tabel, moet u geen bijschrift, knopinfo of aangepaste schermlezertekst opgeven. |
| Groep keuzerondjes | Maak een zichtbare titel voor de groep keuzerondjes door een statisch tekstelement te maken en dit links of boven de groep te plaatsen. Plaats voor elk keuzerondje het label rechts (standaard). |
| Vervolgkeuzelijst | Plaats het bijschrift links van het object (standaard). Als dit niet mogelijk is, plaatst u het onmiddellijk erboven. Voor besturingselementen voor vervolgkeuzelijsten in tabelcellen kondigt de schermlezer een bijschrift, knopinfo of aangepaste schermlezertekst aan die u voor het object opgeeft. Als u de kolomkop als alternatieve tekst voor deze objecten in een tabel wilt gebruiken, moet u geen bijschrift, knopinfo of aangepaste schermlezertekst opgeven. |
| Keuzelijst | Het bijschrift wordt standaard boven de keuzelijst geplaatst wanneer u het maakt. |
| Knop | Het bijschrift wordt automatisch op de knop geplaatst en hoeft niet handmatig te worden geplaatst. Zorg ervoor dat het doel van de knop correct wordt beschreven door de bijschrifttekst. |


### Tekst van knopinfo of Aangepast scherm dynamisch vullen

U kunt ook dynamisch het tekstalternatief van een formulierbesturingselement, zoals de knopinfo, vullen met een waarde uit een gegevensbron. U kunt bijvoorbeeld een aangepaste knopinfo weergeven voor een object in het Frans.
In het schema waarmee u verbinding maakt, kan het volgende worden gedefinieerd voor knopinfo:


```html
<form>
<tooltip dp_tt="tooltip1"/>
</form>
```


In het gegevensbestand waarnaar u verwijst, kan het volgende worden gedefinieerd voor knopinfo:

```html
<form>
<tooltip dp_tt="Quantité - Entrez un nombre inférieur ou égal à 100."/>
</form>
```

1. Klik in het palet Objectbibliotheek op de categorie Standaard en sleep een object naar het formulierontwerp. Voeg bijvoorbeeld een tekstveldobject in.
1. (Optioneel) Klik in het palet Object op het tabblad Veld en typ een bijschrift voor het object in het vak Bijschrift. Typ bijvoorbeeld Quantité.
1. Klik in het palet Toegankelijkheid op het actieve label voor Knopinfo.
1. Selecteer de gegevensverbinding.
1. Klik op het driehoekje naast het vak Binding en selecteer een binding. Selecteer bijvoorbeeld knopinfo > @dp_tt.

De volgende tekenreeks wordt in het vak Binding weergegeven: $record.tooltip.dp_tt Tip: u kunt deze tekenreeks in het vak Items typen in plaats van deze te selecteren.
1. Klik op OK.
1. Het formulier weergeven op het tabblad Voorbeeld-PDF.

### Koppelingstekst opgeven

Gebruikers van ondersteunende hulpmiddelen kunnen verschillende methoden gebruiken om gekoppelde tekst te lezen. Gebruikers van schermlezers gebruiken bijvoorbeeld vaak een lijst met koppelingen, zoals in Figuur 6, om snel de beschikbare koppelingen op een pagina te scannen.

![ de de dialoogdoos van de Lijst van Verbindingen JAWS ](/help/forms/using/assets/image-6.png)

Figuur 6: **de dialoogdoos van de Lijst van de Verbindingen van JAWS**

Daarom moeten koppelingen zelfbeschrijvend zijn; dat is de betekenis ervan niet afhankelijk van hun context (de omringende tekst). De woorden &quot;hier klikken&quot; kunnen bijvoorbeeld het element vormen van de werkelijke koppeling in de zin &quot;Klik hier om ons toepassingsformulier te downloaden&quot;. Een dergelijke koppeling is moeilijk te begrijpen wanneer u een lijst met koppelingen doorloopt, vooral wanneer er meerdere koppelingen met dezelfde tekst zijn.

Wanneer u koppelingen in een formulier gebruikt, moet u ervoor zorgen dat elke koppeling het doel correct beschrijft, afhankelijk van de omringende tekst of positie op de pagina. Gebruik in plaats van bijvoorbeeld &quot;Klik hier&quot; als koppelingstekst de tekst &quot;Toepassingsformulier downloaden&quot; als koppelingstekst.

**Verwante controlepunten**

* § 508 § 194.21
   * (d) Voor ondersteunende hulpmiddelen moet voldoende informatie over een gebruikersinterface-element beschikbaar zijn, met inbegrip van de identiteit, de werking en de toestand van het element. Wanneer een afbeelding een programma-element vertegenwoordigt, moet de informatie die door de afbeelding wordt getoond ook in tekst beschikbaar zijn.
   * l) Wanneer elektronische formulieren worden gebruikt, stelt het formulier personen die gebruikmaken van ondersteunende hulpmiddelen in staat toegang te krijgen tot de informatie, veldelementen en functionaliteit die vereist zijn voor het invullen en verzenden van het formulier, met inbegrip van alle aanwijzingen en aanwijzingen.
* § 508 § 194.22
   * n) Wanneer elektronische formulieren zijn ontworpen om online te worden ingevuld, stelt het formulier mensen die gebruikmaken van ondersteunende hulpmiddelen in staat toegang te krijgen tot de informatie, veldelementen en functionaliteit die vereist zijn voor het invullen en verzenden van het formulier, met inbegrip van alle aanwijzingen en aanwijzingen.
* WCAG 1.0
   * 12.4 Koppel etiketten uitdrukkelijk aan hun controles (P2).
   * 13.1 Het doel van elke verbinding duidelijk identificeren (P2).
* WCAG 2.0
   * 1.1.1 Niet-tekstuele inhoud: alle niet-tekstuele inhoud die aan de gebruiker wordt aangeboden, heeft een tekstalternatief dat hetzelfde doel dient, behalve in de situaties hieronder. (Niveau A)
   * 2.4.6 Koppen en labels: koppen en labels beschrijven het onderwerp of het doel. (Niveau AA)
   * 3.2.4 Consistente identificatie: Componenten met dezelfde functionaliteit binnen een set webpagina&#39;s worden op consistente wijze geïdentificeerd. (Niveau AA)
   * 3.3.2 Labels of instructies: Er worden labels of instructies gegeven wanneer de inhoud door de gebruiker moet worden ingevoerd. (Niveau A)
   * 4.1.2 Naam, Rol, Waarde: Voor alle gebruikersinterfacecomponenten (inclusief maar niet beperkt tot: formulierelementen, koppelingen en componenten die door scripts worden gegenereerd) kunnen de naam en de rol via programmacode worden bepaald; statussen, eigenschappen en waarden die door de gebruiker kunnen worden ingesteld, kunnen via programmacode worden ingesteld; en meldingen van wijzigingen in deze items zijn beschikbaar voor gebruikersagenten, inclusief ondersteunende technologieën. (Niveau A)


## Zorg ervoor dat de lees- en tabvolgorde correct zijn {#ensure-reading-tab-order}

Een zinvolle leesvolgorde is van groot belang bij het ontwerpen van formulieren die toegankelijk zijn voor gebruikers met een visuele handicap. Deze gebruikers gebruiken doorgaans geen muis om door een formulier te navigeren, zodat ze afhankelijk zijn van het toetsenbord. De leesvolgorde bepaalt de volgorde die gebruikers van schermlezers gebruiken bij het lezen door het formulier. Daarnaast kunnen gebruikers met de Tab-toets of de toetscombinatie Shift+Tab snel van het ene interactieve formulierbesturingselement naar het volgende gaan. Een logische tabvolgorde zorgt ervoor dat ze toegang hebben tot alle velden op het formulier en dat ze op een verstandige en efficiënte manier door het formulier kunnen navigeren.

De leesvolgorde van het formulier omvat alle statische objecten (zoals tekst en afbeeldingen) en veldobjecten, maar alleen de interactieve formulierbesturingselementen maken deel uit van de tabvolgorde.

>[!NOTE]
> In veel gevallen houdt de tabvolgorde nauw verband met de leesvolgorde. Voor de eenvoud wordt de term &quot;tabvolgorde&quot; gebruikt in plaats van &quot;tab- of leesvolgorde&quot; in deze handleiding.

### De standaardtabvolgorde in Designer-formulieren voor LiveCycles

De standaardtabvolgorde wordt automatisch gemaakt wanneer u het formulier opslaat als een gecodeerde PDF. In eerste instantie wordt de tabvolgorde in een formulier bepaald op basis van de lokale positie van de objecten met de volgende regels:

* Alle objecten worden van links naar rechts en van boven naar beneden geordend (lokale volgorde), vanaf de linkerbovenhoek van het formulier.
* Subformulieren die u maakt, worden beschouwd als zelfstandige eenheden en worden ook van links naar rechts en van boven naar beneden genavigeerd. Als twee subformulieren naast elkaar worden geplaatst, die beide objecten bevatten, navigeert de leesvolgorde door alle objecten in het eerste subformulier voordat naar het volgende subformulier wordt gegaan.

Voor eenvoudige formulieren (formulieren met een indeling van links naar rechts en van boven naar beneden) is de standaardtabvolgorde meestal correct. Controleer de standaardtabvolgorde voordat u het formulier publiceert. U kunt de tabvolgorde op een van de volgende manieren zichtbaar maken:

* Kies Beeld > Tabvolgorde tonen.
* Klik op Volgorde tonen in het palet Tabvolgorde.

Alle objecten worden weergegeven met een nummer in de rechterbovenhoek dat de plaats van het object in de standaardtabvolgorde aangeeft. De interactieve objecten in deze reeks vormen de tabvolgorde. In Figuur 7 ziet u de leesvolgorde van een basisformulier.

![ Visualisatie van de standaard lezingsorde voor een typische orde vorm ](/help/forms/using/assets/image-7.png)

Figuur 7: **Visualisatie van de standaardlezingsorde voor een typische orde vorm**

Elk tabvolgordenummer wordt in een gekleurde vorm weergegeven. De vormen hebben de volgende betekenis:
* Grijze cirkels (#1 en #4) worden gebruikt voor objecten in het inhoudsgebied.
* Groene cirkels (#6 en #7) worden gebruikt voor stramienpaginaobjecten.
* De lavendervierkanten (#2 en #3) worden gebruikt voor voorwerpen binnen een fragment.

U kunt ervoor kiezen alleen interactieve formulierbesturingselementen (die de tabvolgorde vormen) of alle objecten in de leesvolgorde (die ook statische objecten zoals tekst en afbeeldingen bevat) weer te geven. Als u deze voorkeur wilt wijzigen, kiest u Opties > Opties > Tabvolgorde en selecteert u Tabvolgorde alleen weergeven voor velden.

In een complex formulier kan het moeilijk zijn om te zien hoe de tabvolgorde van het ene object naar het andere loopt. Met visuele hulpmiddelen kunt u de tabvolgorde op het formulier weergeven. Wanneer u de aanwijzer boven het object houdt terwijl de visuele hulpmiddelen zijn ingeschakeld, geven blauwe pijlen de tabvolgorde voor de twee voorgaande en twee volgende objecten in de tabvolgorde weer (zie Figuur 8).

![ Visuele hulpmiddelen benadrukken de lusjeorde ](/help/forms/using/assets/image-8.png)

Figuur 8: **Visuele hulpmiddelen benadrukken de lusjeorde**

Gebruik de volgende methoden om visuele hulpmiddelen in te schakelen:
* Kies Opties > Opties > Tabvolgorde en selecteer in het venster Tabvolgorde de optie Aanvullende visuele hulpmiddelen voor tabvolgorde.
* Selecteer Visuele hulpmiddelen tonen in het menu van het palet Tabvolgorde.

### Positie gebruiken om de standaardtabvolgorde te beïnvloeden

U kunt de standaardtabvolgorde wijzigen door de coördinaten van een object naar een andere locatie te verplaatsen. In Figuur 9 vindt het veld Productnaam bijvoorbeeld plaats in de tabvolgorde vóór het veld Hoeveelheid. Als u deze volgorde wilt wijzigen, kunt u het veld Productnaam verplaatsen zodat het onder of rechts van het veld Hoeveelheid wordt geplaatst.

![ De standaardlusjeorde wordt verlaten aan recht ](/help/forms/using/assets/image-9.png)

Figuur 9: **de standaardlusjeorde wordt verlaten aan recht**

U kunt de positie van een object als volgt wijzigen:
* Sleep de muis
* Selecteer het en verplaats het met de pijltoetsen op het toetsenbord.

>[!NOTE]
> Het kan handig zijn om de objectuitlijning te behouden door Weergave > Magnetisch raster te kiezen.

U kunt de coördinaten van een object nauwkeuriger wijzigen met het palet Indeling (weergegeven in Figuur 10). Met dit palet kunt u de X- en Y-coördinaten en de breedte en hoogte van het object opgeven.

![ Gebruikend coördinaten om een voorwerp met het palet van de Lay-out nauwkeurig te plaatsen ](/help/forms/using/assets/image-10.png)

Figuur 10: **Gebruikend coördinaten om een voorwerp met het palet van de Lay-out** precies te plaatsen

>[!NOTE]
> Als het bijschrift en het besturingselement niet worden samengevoegd, is de positie van het bijschrift van een formulierbesturingselement onafhankelijk van de volgorde waarin schermlezers het object en de elementen ervan lezen. Voor meer informatie over titels, zie sectie 2.5 correcte etiketten voor vormcontroles in deze gids verstrekken.

### Subformulieren gebruiken om de standaardtabvolgorde te wijzigen

Zoals hierboven vermeld, kunt u met subformulieren groepen objecten invoegen die een eigen tabvolgorde hebben. U kunt een subformulier maken door een van de volgende handelingen uit te voeren:
* Kies Invoegen > Standaard > Subformulier.
* Selecteer de objecten in het palet Hiërarchie en groepeer ze in een subformulier door Invoegen > Onderbrengen in subformulier te kiezen.
* Selecteer de objecten in het daadwerkelijke formulier, klik met de rechtermuisknop op de selectie en kies Onderbrengen in subformulier

Wanneer twee subformulieren met veldobjecten naast elkaar worden geplaatst, doorloopt de tabvolgorde de velden in het eerste subformulier voordat naar het volgende subformulier wordt gegaan. Dit wordt geïllustreerd in Figuur 11, waar twee subformulieren worden gebruikt om een op kolom gebaseerde standaardtabvolgorde te maken.

![ Standaard lusjeorde gebruikend subforms ](/help/forms/using/assets/image-11.png)

Figuur 11: **Standaard lusjeorde gebruikend subforms**

Subformulieren, keuzerondjes en inhoudsgebieden beïnvloeden samen met de verticale positie van objecten op een pagina en de bijbehorende basispagina allemaal de tabvolgorde.

### Een aangepaste tabvolgorde maken met het palet Tabvolgorde

U kunt de standaardtabvolgorde wijzigen wanneer u een andere volgorde in het formulier nodig hebt en de wijziging kan niet worden bereikt door plaatsing of groepering in subformulieren. Als u de standaardtabvolgorde wilt wijzigen, kunt u een aangepaste tabvolgorde maken met het palet Tabvolgorde.
Met het palet Tabvolgorde (zie Figuur 12) kunt u de volgorde controleren en wijzigen waarin objecten in het formulier worden gelezen met behulp van ondersteunende hulpmiddelen en worden genavigeerd door de Tab-toets van de gebruiker.

![ het palet van de Orde van het Lusje ](/help/forms/using/assets/image-12.png)

Figuur 12: **het palet van de Orde van het Lusje**

Het palet Tabvolgorde biedt een alternatieve weergave van de tabvolgorde op het formulier. Alle objecten op het formulier worden weergegeven als een genummerde lijst, waarbij elk nummer de positie van het object in de tabvolgorde aangeeft.
Kies Venster > Tabvolgorde om het palet Tabvolgorde te openen.


Het palet Tabvolgorde bevat de volgende visuele markeringen:
* Een grijze balk markeert elke pagina van het formulier. De tabvolgorde op elke pagina begint met nummer 1.
* De letter M in een groene cirkel geeft basispaginaobjecten aan (alleen zichtbaar bij weergave van het formulier op het tabblad Ontwerpweergave).
* Een reeks getallen geeft objecten binnen een fragment aan.
* Een gele achtergrond geeft het geselecteerde item aan.
* Een vergrendelingspictogram naast het eerste object op de pagina geeft aan dat het object niet kan worden verplaatst binnen de tabvolgorde (alleen zichtbaar bij weergave van het formulier op het tabblad Basispagina&#39;s).

In de lijst staan dezelfde tabvolgordenummers als de nummers die op het formulier zelf worden weergegeven wanneer u Beeld > Tabvolgorde weergeven kiest. U wijzigt de positie van een object in de tabvolgorde door het object omhoog of omlaag te verplaatsen in de lijst in het palet Tabvolgorde. U kunt één object of een groep objecten verplaatsen. Dit kan op een van de volgende manieren worden bereikt:

* Sleep het geselecteerde object omhoog of omlaag in de lijst en plaats het op de gewenste locatie. Een zwarte handgreep markeert de huidige positie in de lijst voordat u het object plaatst.
* Klik in het palet Tabvolgorde op de pijlknoppen omhoog of omlaag totdat het geselecteerde object op de juiste positie is geplaatst. U kunt ook op Ctrl+Pijl-omhoog of Ctrl+Pijl-omlaag drukken.
* Selecteer Omhoog of Omlaag in het menu van het palet Tabvolgorde.
* Klik in de lijst in het palet Tabvolgorde op het geselecteerde object (of selecteer het en druk op F2) om het nummer naast de objectnaam bewerkbaar te maken. Typ vervolgens het getal dat de nieuwe positie van het object in de tabvolgorde aangeeft en druk op Enter.
* Selecteer Kopiëren in het menu van het palet Tabvolgorde en selecteer in de lijst het object waarboven u het object wilt plaatsen dat u verplaatst. Selecteer vervolgens Plakken in het menu.

Wanneer u het object naar een nieuwe plaats in de volgorde verplaatst, wijst LiveCycle Designer de tabvolgordenummers opnieuw toe. Hoewel de tabvolgorde voor de objecten op een basispagina wordt weergegeven op het tabblad Ontwerpweergave, kunt u de volgorde voor deze objecten alleen wijzigen op het tabblad Basispagina&#39;s. Als u fragmentverwijzingen gebruikt in uw formulier, is de tabvolgorde binnen een fragment zichtbaar wanneer u de volgorde voor het formulier weergeeft. Als u de tabvolgorde in een fragment wilt wijzigen, moet u het bronbestand van het fragment openen voor bewerking, de wijziging aanbrengen en het bestand opslaan. Deze wijziging is van invloed op alle formulieren die gebruikmaken van dit fragment.

Als u besluit dat u de aangepaste tabvolgorde niet wilt gebruiken voor uw formulier, kunt u snel terugkeren naar de automatische (standaard)tabvolgorde door de volgende stappen uit te voeren (wijzigingen in de tabvolgorde gaan verloren):
1. Selecteer Automatisch in het palet Tabvolgorde.
1. Klik in het berichtvenster op Ja om te bevestigen dat de aangepaste tabvolgorde is verwijderd.

**Verwante controlepunten**
* § 508 § 194.21
   * a) Wanneer software is ontworpen om te worden uitgevoerd op een systeem met een toetsenbord, moeten productfuncties uitvoerbaar zijn vanaf een toetsenbord waar de functie zelf of het resultaat van het uitvoeren van een functie tekstueel kan worden herkend.
* WCAG 1.0
   * 9.2 Ervoor zorgen dat elk element met een eigen interface op een apparaatonafhankelijke manier kan worden gebruikt.
* WCAG 2.0
   * 1.3.2 Betekenisvolle sequentie: wanneer de sequentie waarin inhoud wordt gepresenteerd van invloed is op de betekenis ervan, kan een correcte leesvolgorde via programmacode worden bepaald. (Niveau A)
   * 2.1.1 Toetsenbord: alle functionaliteit van de inhoud kan worden uitgevoerd via een toetsenbordinterface zonder dat specifieke tijdinstellingen voor afzonderlijke toetsaanslagen vereist zijn, behalve wanneer de onderliggende functie invoer vereist die afhankelijk is van het pad van de beweging van de gebruiker en niet alleen van de eindpunten. (Niveau A)
   * 2.1.3 Toetsenbord (geen uitzondering): alle functionaliteit van de inhoud kan worden uitgevoerd via een toetsenbordinterface zonder dat specifieke tijdinstellingen voor afzonderlijke toetsaanslagen vereist zijn. (Niveau AAA)
   * 2.4.3 Volgorde van de nadruk: Als een Web-pagina opeenvolgend kan worden genavigeerd en de navigatiereeksen betekenis of verrichting beïnvloeden, ontvangen de brandpuntbruikbare componenten nadruk in een orde die betekenis en operabiliteit bewaart. (Niveau A)


## Zorg ervoor dat formulierbesturingselementen via het toetsenbord toegankelijk zijn{#ensure-keyboard-accessible}

Gebruikers moeten het formulier volledig kunnen invullen met alleen het toetsenbord of een equivalent alternatief invoerapparaat. Gebruikers met een beperkte mobiliteit of een visuele handicap hebben misschien geen andere keuze dan het toetsenbord te gebruiken en veel gebruikers die een muis kunnen gebruiken, geven de voorkeur aan invoer via het toetsenbord. Door verschillende invoermethoden toe te staan, maakt u niet alleen toegankelijke formulieren, maar ook formulieren die beter zijn afgestemd op de voorkeuren van alle gebruikers.

In LiveCycle Designer is de eenvoudigste manier om ervoor te zorgen dat uw besturingselementen via het toetsenbord toegankelijk zijn, via de besturingselementen die op het tabblad Algemeen in het palet Objectbibliotheek worden vermeld. Deze besturingselementen reageren standaard op zowel muis- als toetsenbordinvoer. Voor meer informatie, zie sectie 2.3 kiezen de juiste controles in deze gids.

Een ander belangrijk aspect van toetsenbordtoegankelijkheid is ervoor te zorgen dat elk interactief element deel uitmaakt van de tabvolgorde van het formulier. Hierdoor kan de gebruiker de cursor vooruit en achteruit door het formulier verplaatsen met de Tab-toets en de toetscombinatie Shift+Tab. Zorg ervoor dat u een logische tabvolgorde instelt die alle velden en knoppen bevat. Zie sectie 2.6 Zorg ervoor dat de lees- en tabvolgorde in deze handleiding correct zijn voor meer informatie.

Tot slot is het belangrijk om ervoor te zorgen dat scriptgedrag toetsenbord ook toegankelijk is, en niet afhankelijk van apparaat-specifieke gebeurtenissen is. De muisgebeurtenis MouseEnter kan bijvoorbeeld niet worden uitgevoerd met het toetsenbord. Dergelijke gebeurtenishandlers mogen zich ook niet mengen in de toegankelijkheid van het toetsenbord. Zorg er bijvoorbeeld voor dat gebeurtenissen Wijzigen die in vervolgkeuzelijsten of keuzelijsten worden gebruikt, geen onverwachte acties activeren.

**Verwante controlepunten**
* § 508 § 194.21
   * a) Wanneer software is ontworpen om te worden uitgevoerd op een systeem met een toetsenbord, moeten productfuncties uitvoerbaar zijn vanaf een toetsenbord waar de functie zelf of het resultaat van het uitvoeren van een functie tekstueel kan worden herkend.
* WCAG 1.0
   * 6.4 Voor scripts en applets moet u ervoor zorgen dat gebeurtenishandlers apparaatonafhankelijk (P2) worden ingevoerd.
   * 9.2 Ervoor zorgen dat elk element met een eigen interface op een apparaatonafhankelijke manier kan worden gebruikt (P2).
   * 9.3 Voor manuscripten, specificeer logische gebeurtenismanagers eerder dan apparaat-afhankelijke gebeurtenismanagers (P2).
* WCAG 2.0
   * 2.1.1 Toetsenbord: alle functionaliteit van de inhoud kan worden uitgevoerd via een toetsenbordinterface zonder dat specifieke tijdinstellingen voor afzonderlijke toetsaanslagen vereist zijn, behalve wanneer de onderliggende functie invoer vereist die afhankelijk is van het pad van de beweging van de gebruiker en niet alleen van de eindpunten. (Niveau A)
   * 2.1.2 Geen toetsenbordovervulling: als toetsenbordfocus via een toetsenbordinterface naar een component van de pagina kan worden verplaatst, kan de focus alleen met behulp van een toetsenbordinterface van die component worden verwijderd. Als hiervoor meer dan ongewijzigde pijl- of tabtoetsen of andere standaardafsluitmethoden nodig zijn, wordt de gebruiker op de hoogte gesteld van de methode om de focus weg te verplaatsen. (Niveau A)
   * 2.1.3 Toetsenbord (geen uitzondering): alle functionaliteit van de inhoud kan worden uitgevoerd via een toetsenbordinterface zonder dat specifieke tijdinstellingen voor afzonderlijke toetsaanslagen vereist zijn. (Niveau AAA)


## Kleur verantwoord gebruiken{#use-color-responsibly}

Bij het ontwerpen van formulieren voor toegankelijkheid moet u rekening houden met enkele aanvullende richtlijnen voor het gebruik van kleuren. Ontwerpers gebruiken kleuren om de weergave van formulieren te verbeteren door verschillende formuliercomponenten te markeren. Onjuist gebruik van kleur kan echter de informatie in uw vorm moeilijk of onmogelijk leesbaar maken voor mensen met een handicap.

### Geen informatie verzenden met alleen kleur

Met kleuren kunt u bepaalde onderdelen van een formulier benadrukken en verbeteren, maar u moet de informatie niet alleen in kleur doorgeven.

Informatie die uitsluitend in kleur wordt weergegeven (kleuren met semantische betekenis) is niet toegankelijk voor blinde gebruikers. Dit geldt ook voor gebruikers met een kleurvisiehandicap of gebruikers die verschillende kleurenschema&#39;s gebruiken, zoals een kleurenscherm met hoog contrast met witte tekst of voorgrond op een zwarte achtergrond. U moet ook bedenken dat schermlezers kleurgegevens niet automatisch kunnen detecteren.

Figuur 13 toont bijvoorbeeld een formulierveld met een rood bijschrift (opgegeven met het palet Font) om aan te geven dat het formulierveld verplicht is. In dit voorbeeld is de kleur de enige indicator voor het verschil tussen de vereiste en optionele invoervelden, waardoor het voor blinde gebruikers of gebruikers met bepaalde typen kleurenblindheid onmogelijk is ze te onderscheiden.

![ Gebruikend kleur alleen om informatie ](/help/forms/using/assets/image-13.png) te vervoeren

Figuur 13: **Gebruikend kleur alleen om informatie** te vervoeren

Om dit probleem op te lossen, geeft u ook de vereiste status van het formulier op in de alternatieve tekst van het formulierbesturingselement (zoals beschreven in sectie 2.5 Geef juiste labels voor formulierbesturingselementen op). U kunt de schermlezertekst bijvoorbeeld instellen op &#39;Postcode (vereist)&#39;. Voor gebruikers die problemen hebben met het zien van kleur in bepaalde combinaties, wordt aangeraden het tekstveldtype in te stellen op Door gebruiker ingevoerd - vereist in het palet Object, naast alternatieve tekst die aangeeft dat het veld verplicht is. U kunt ook andere indicaties gebruiken dan kleuren, zoals visuele tekst, tekststijlen en randstijlen. Voor gebruikers van schermlezers moet u de vereiste informatie echter wel via het palet Toegankelijkheid verzenden.

Houd er bij het opgeven van beschrijvingen of instructies aan de gebruiker van het formulier ook rekening mee dat instructies die alleen op kleur zijn gebaseerd, onvoldoende zijn voor gebruikers met een visuele handicap. In plaats van een instructie zoals &quot;Klik op de groene knop om door te gaan&quot; gebruikt u bijvoorbeeld een tekstbeschrijving voor handelingen, zoals &quot;Klik op de knop Volgende om door te gaan.&quot;

>[!NOTE]
> Deze werkwijze verbiedt het gebruik van kleur niet. Het gebruik van kleur als enige manier om belangrijke informatie over te brengen, wordt verboden. Als voor dit soort informatie nog steeds een visuele indicatie gewenst is, kan de ontwerper een sterretje of soortgelijke visuele indicator gebruiken om vereiste velden te markeren.

### Geef voldoende kleurcontrast op

Veel gebruikers met een visuele handicap vertrouwen op een hoog contrast tussen tekst en de achtergrond voor het lezen van formulieren. Wanneer het contrast tussen de achtergrondkleur en de voorgrondkleur onvoldoende is, kan een formulier voor sommige gebruikers moeilijk of zelfs onmogelijk leesbaar worden. In Figuur 14 ziet u een voorbeeld van een formulier met onvoldoende contrast.

![ Vorm van A met ontoereikend kleurencontrast ](/help/forms/using/assets/image-14.png)

Figuur 14: **Vorm van A met ontoereikend kleurencontrast**

Het wordt ten zeerste aanbevolen de standaardkleuren voor lettertypen en achtergronden te gebruiken: zwart op een witte achtergrond. Als u deze standaardkleuren moet wijzigen, moet u een geschikte combinatie kiezen van kleuren met veel contrast. Kies een donkere voorgrondkleur voor een lichte achtergrondkleur of andersom. Om zeker te zijn, gebruik een hulpmiddel (zoals de Analysator van het Contrast van de Kleur WAT-C) om te verifiëren dat het contrast voldoende is.

Met Adobe Reader en Adobe Acrobat kunnen gebruikers opgeven of kleuren moeten worden vervangen om aan hun visuele behoeften te voldoen. De gebruikers kunnen hun eigen contrastschema specificeren, of zij kunnen verkiezen om een regeling te gebruiken die door het werkende systeem wordt verstrekt. Bovendien hebben Adobe Reader en Adobe Acrobat een eigen hoog contrastschema dat mogelijk is ingeschakeld. Deze opties zijn alleen succesvol als u altijd standaardkleuren gebruikt.

Tijdens het ontwerpen van uw formulier test u het regelmatig met een kleurenschema dat lijkt op de instelling die veel gebruikers met een visuele handicap zullen gebruiken om het formulier in te vullen. Deze praktijk helpt u kwesties vroeg in het ontwerpproces ontdekken en verbeteren.

Recommendations voor het gebruik van kleuren:
* Zorg ervoor dat er geen informatie verloren gaat als de semantische kleur niet zichtbaar is.
* Als u geen standaardkleuren kunt gebruiken, moet u ervoor zorgen dat de kleuren een hoog contrast hebben, zoals zwart op een lichte (witte) achtergrond. Gedeeltelijk waargenomen gebruikers hebben doorgaans een hoog contrast tussen de tekst en de achtergrond nodig om deze te kunnen lezen.
* Test de leesbaarheid van uw formulieren door het scherm om te schakelen naar een display met hoog contrast, zowel in Windows als in Adobe Reader of Adobe Acrobat. Mac OSX biedt alleen een eenvoudig grijswaardenfilter voor hoog contrast, dus dit is niet voldoende voor testen.
* Verstrek geen informatie die uitsluitend op kleur wordt gebaseerd. Gebruik bijvoorbeeld niet alleen kleur om belangrijke stukken tekst te markeren. Gebruik ook andere markeringsmethoden en tekstbeschrijvingen.
* Gebruik niet te veel kleuren, omdat hierdoor de werkelijke informatie in de inhoud moeilijk leesbaar kan worden. Houd altijd de leesbaarheid van de informatie als de hoogste prioriteit wanneer u besluit welke kleuren u wilt gebruiken.

**Verwante controlepunten**
* § 508 § 194.21
   * i) Kleurcodering mag niet worden gebruikt als het enige middel om informatie over te brengen, een handeling aan te geven, een antwoord te geven of een visueel element te onderscheiden.
* WCAG 1.0
   * 2.1 Zorg ervoor dat alle informatie die met kleur wordt overgebracht ook zonder kleur, bijvoorbeeld van context of prijsverhoging, beschikbaar is.
   * 2.2 Zorg ervoor dat de combinaties van de voor- en achtergrondkleur voldoende contrast bieden bij weergave door iemand met een kleurdeficit of bij weergave op een zwart-witscherm. [ Prioriteit 2 voor beelden, Prioriteit 3 voor tekst ] (P2).
* WCAG 2.0
   * 1.4.1 Gebruik van kleur: kleur wordt niet gebruikt als de enige visuele manier om informatie over te brengen, een handeling aan te geven, een reactie te vragen of een visueel element te onderscheiden. (Niveau A)
   * 1.4.3 Contrast (minimaal): de visuele weergave van tekst en afbeeldingen van tekst heeft een contrastverhouding van ten minste 4,5:1, behalve voor: (Niveau AA)
   * 1.4.6 Contrast (uitgebreid): de visuele presentatie van tekst en afbeeldingen van tekst heeft een contrastverhouding van ten minste 7:1, behalve voor de volgende: (Niveau AAA)


## Kopcellen voor tabellen opgeven{#provide-heading-cells}

Tabellen zijn een effectieve manier om inhoud in toegankelijke formulieren te ordenen en weer te geven. Als de rijen en kolommen van een tabel op de juiste wijze worden gebruikt, bieden deze een voorspelbare en consistente structuur voor de formulierinhoud. Wanneer een schermlezer bijvoorbeeld naar een cel in een tekstrij navigeert, geeft de schermlezer de cellocatie op en wordt de celinhoud gelezen. De schermlezer geeft de locatie van de cel op met een combinatie van rij- en kolomkoppen of rij- en kolomnummers. Omdat schermlezers informatie verstrekken die de gebruiker op de plaats van inhoud in de lijst plaatst, beïnvloedt zijn lay-out direct de toegankelijkheid van de lijst.

Tijdens het samenstellen van tabellen kunt u de volgende rollen voor tabelelementen opgeven. Met deze rollen kunnen schermlezers met behulp van speciale sneltoetsen door de tabelstructuur navigeren en wordt de relatie tussen tabelcellen en de bijbehorende kopcellen doorgegeven aan de gebruiker.
* Tabel
Hiermee wordt de rol van tabel toegewezen aan het geselecteerde subformulier. Wanneer de gebruiker naar dit subformulier navigeert, identificeren de meeste schermlezers het als een tabel en geven ze het aantal rijen en kolommen aan.
* Koptekstrij
Hiermee wordt de rol van koptekstrij toegewezen aan het geselecteerde subformulier of aan de geselecteerde tabelrij. Wanneer de inhoud van een cel in een tekstrij wordt voorgelezen, identificeren de meeste schermlezers eerst de inhoud van de bijbehorende cel in de koptekstrij.
* Bodyrij
Hiermee wordt de rol van tekstrij toegewezen aan het geselecteerde subformulier of aan de geselecteerde tabelrij. Als een cel een subformulier bevat, lezen schermlezers doorgaans de inhoud van de corresponderende cel in de koptekstrij voor, gevolgd door de velden in het subformulier.
* Voettekstrij
Hiermee wordt de rol van voettekstrij toegewezen aan het geselecteerde subformulier of aan de geselecteerde tabelrij.
* (Geen)
Hiermee geeft u een rij op die informatie over de tabel of de inhoud ervan bevat. De rij wordt niet beschouwd als onderdeel van de tabel, maar de schermlezer leest de inhoud ervan voor.

Tabellen zijn een effectieve manier om tabelinformatie te ordenen en weer te geven wanneer ze correct worden gebruikt. Gebruik geen al te complexe tabellen, zoals tabellen met geneste tabellen en secties.

### Eenvoudige tabellen toegankelijk maken

Tabellen met eenvoudige lay-outs worden aanbevolen. Eenvoudige tabellen beginnen met één koptekstrij gevolgd door de tekstrijen.

Houd bij het ontwerpen van eenvoudige tabellen voor toegankelijkheid rekening met de volgende richtlijnen:

* De tabvolgorde voor een tabel is een geografische volgorde, die hetzelfde is als voor het formulier zelf. Zorg ervoor dat de tabelinhoud zo is ingedeeld dat deze begrijpelijk is wanneer de inhoud van links naar rechts en van boven naar beneden wordt gelezen.
* De meeste schermlezers interpreteren de eerste rij in een tabel als de koptekstrij. Wanneer de inhoud van een cel in een tekstrij wordt gelezen, lezen deze schermlezers eerst de inhoud van de bijbehorende cel in de koptekstrij voor. Zorg ervoor dat de inhoud in elke cel van de koptekstrij een duidelijke beschrijving van de kolominhoud bevat.
* Gebruik geen cellen die twee of meer kolommen, geneste tabellen of tabelsecties beslaan. Sommige schermlezers kunnen deze functies moeilijk interpreteren of gebruiken ze niet. Als een cel in een tekstrij bijvoorbeeld twee kolommen omvat, verwijzen schermlezers mogelijk niet naar de juiste celinhoud in de koptekstrij wanneer de volgende cel in de rij wordt gelezen.

### Complexe tabellen toegankelijk maken

Wanneer u tabellen ontwerpt voor toegankelijkheid, moet u ervoor zorgen dat de tabellay-out eenvoudig blijft, met één koptekstrij gevolgd door tekstrijen. Voor bepaalde inhoud is uiteraard een complexere tabelindeling vereist. U moet bijvoorbeeld cellen die meerdere kolommen beslaan of meerdere kopteksten gebruiken om de inhoud daadwerkelijk over te brengen.

U kunt complexe tabellen maken met het tabelobject of door subformulierobjecten te combineren. Met het tabelobject kunt u functies gebruiken die u helpen bij het ontwerpproces, zoals opties voor het invoegen en vergroten of verkleinen van kolommen en rijen.

Met het palet Toegankelijkheid kunt u tabelgerelateerde rollen opgeven voor subformulieren om een toegankelijke complexe tabel te maken. Afhankelijk van uw ontwerpervaring en -voorkeuren kunt u ervoor kiezen complexe tabellen te maken door subformulierobjecten te combineren. U kunt bijvoorbeeld één subformulier maken dat twee rijen bevat en dit subformulier opgeven als koptekst voor de tabel en een ander subformulier opgeven voor de tekstrijen van de tabel.

Wanneer u subformulierobjecten in plaats van tabelobjecten gebruikt om tabellen te maken, zijn de volgende extra stappen vereist:
* Stel op het tabblad Subformulier het type voor elk subformulier in op Geplaatst.
* Stel in het palet Toegankelijkheid de juiste rol in voor elk subformulier dat de tabel vormt. Wijs bijvoorbeeld de rol Koptekstrij toe aan het subformulier dat wordt gebruikt als tabelkop.
* Voor rijen die informatie over de tabel of de inhoud ervan overbrengen maar die niet als onderdeel van de tabel worden beschouwd, wijst u de subformulierrol Geen toe. De schermlezer leest de inhoud van de rij voor.

De functies die door de schermlezer worden ondersteund, bepalen de informatie die voor een complexe tabel wordt gelezen. Neem bijvoorbeeld een tabel die een koptekstrij en een sectie met een koptekstrij bevat. Wanneer de gebruiker in een cel van de lichaamstrij in de lijstsectie navigeert, zullen de schermlezers typisch de volgende inhoud, in orde lezen:
* Inhoud uit de juiste cel in de koptekstrij voor de tabel
* Inhoud uit de juiste cel in de koptekstrij voor de sectie
* Inhoud van de geselecteerde cel
Sommige schermlezers kunnen echter de inhoud van beide koptekstrijen niet lezen.

Maak betekenisvolle zichtbare namen of titels voor uw tabellen. U kunt een tabelnaam maken als statische tekst in Adobe LiveCycle Designer en deze vóór de tabel plaatsen. U kunt een tabel en de naam ervan groeperen in een subformulier. Subformulieren zijn vooral handig wanneer u gekoppelde objecten wilt combineren in een indeling.

Voor besturingselementen in tabelcellen geeft de schermlezer een bijschrift, knopinfo of aangepaste schermlezertekst aan die u voor het object opgeeft. Als u de kolomkop wilt gebruiken als alternatieve tekst voor een besturingselement in een tabel, moet u geen bijschrift, knopinfo of aangepaste schermlezertekst opgeven. Houd er echter rekening mee dat deze strategie niet altijd zo duidelijk is voor gebruikers van schermlezers, aangezien schermlezers de kolomkop alleen aan het besturingselement kunnen koppelen wanneer de gebruiker zich niet in de modus Formulierinteractie van de schermlezer bevindt.

**Verwante controlepunten**
* § 508 § 194.22
   * g) De rij- en kolomkoppen worden voor gegevenstabellen geïdentificeerd.
   * h) Markup wordt gebruikt voor het koppelen van gegevenscellen en kopcellen voor gegevenstabellen met twee of meer logische niveaus van rij- of kolomkoppen.
* WCAG 1.0
   * 5.1 Voor gegevenstabellen, identificeer rij en kolomkopballen (P1).
   * 5.2 Voor gegevenslijsten die twee of meer logische niveaus van rij of kolomkopballen hebben, gebruik prijsverhoging om gegevenscellen en kopbalcellen (P1) te associëren
* WCAG 2.0
   * 1.3.1 Informatie en relaties: informatie, structuur en relaties die via de presentatie worden overgebracht, kunnen via programmacode worden bepaald of zijn beschikbaar in tekst. (Niveau A)


## Een naviderbare formulierstructuur opgeven{#provide-navigable-form}

Wanneer een formulier lang en complex wordt, wordt het gebruiksgemak ervan sterk beïnvloed door de structuur ervan. Net zoals een boek eenvoudiger te begrijpen is als het is onderverdeeld in hoofdstukken en secties, wordt een formulier gemakkelijker te gebruiken als het wordt onderverdeeld in koppen en subkoppen. Deze partitionering is vooral handig voor gebruikers van schermlezers, en wel om de volgende redenen:
* Elke kop vertelt de gebruiker van de schermlezer wat in de sectie na de kop kan worden verwacht.
* Schermlezers bieden snelkoppelingen waarmee u snel tussen de verschillende koppen in het formulier kunt schakelen. Bovendien kunnen gebruikers een lijst met koppen openen, met een overzicht van de documentstructuur en een snelle navigatie.

Het is handiger mechanismen in te stellen waarmee gebruikers andere gebieden van het formulier kunnen overslaan. Met het palet Toegankelijkheid in LiveCycle Designer kunt u een kopstructuur aan het formulier toevoegen.

### Schipmechanismen beschikbaar stellen

Gewogen gebruikers kunnen een pagina in om het even welke orde aftasten. Ze kunnen beginnen door naar de rechterbenedenhoek van de pagina te kijken en achterwaarts door de inhoud te scannen. De gebruiker van de schermlezer heeft deze optie niet omdat de schermlezer de pagina linksboven (zoals weergegeven in de broncode) gaat lezen en lineair doorloopt. Bovendien kan de waargenomen gebruiker de pagina scannen op interessante koppelingen en deze activeren met de muis. De gebruiker van een schermlezer moet de pagina opeenvolgend doorlopen.

De eenvoudigste en meest effectieve manier om een navigeerbare formulierstructuur te bieden, is door gebruik te maken van structuurkoppen en correct gedefinieerde lijsten in het formulier.
U kunt ook mechanismen instellen waarmee de gebruiker andere gebieden van het formulier kan overslaan, bijvoorbeeld door navigatieknoppen toe te voegen boven en onder aan het formulier. Boven aan een formulier kunt u knoppen opnemen, zoals Gegevensbestand openen, Vorige pagina en Volgende pagina. Onder aan het formulier kunt u knoppen opnemen, zoals Gegevens opslaan, Gegevens e-mailen, Naar begin van pagina en Afdrukken.

Met slimme velden kunt u bepaalde formulieren gemakkelijker invullen. Een formulier voor een reisaanvraag kan bijvoorbeeld meerdere rijen en kolommen met velden bevatten. Als een bepaalde rij leeg is, kunt u met de Tab-toets op het laatste item in die rij naar de volgende sectie van het formulier gaan in plaats van met de Tab-toets door een aantal velden te gaan die leeg blijven.

### Koppen toevoegen met het palet Toegankelijkheid

Met het palet Toegankelijkheid kunt u rollen toewijzen aan objecten op basis van de bestemming van het object. Deze rollen kunnen worden toegepast om rubrieken op verschillende niveaus tot stand te brengen.

![ die een kopbalrol in het palet van de Toegankelijkheid specificeren ](/help/forms/using/assets/image-15.png)
Figuur 15: **specificerend een koprol in het palet van de Toegankelijkheid**

Ga als volgt te werk om een kop in uw formulier te maken:

1. Het begin van elk logisch segment van het formulier identificeren met statische tekstlabels,
1. Selecteer voor elk label een van de kopopties als Rol in het palet Toegankelijkheid. Met de verschillende kopniveaus (1 tot en met 6) kunt u een kopstructuur in uw formulier maken. Begin met niveau 1 en gebruik vervolgens niveau 2 enzovoort voor geneste subsecties.

Met de meeste schermlezers kunnen gebruikers op basis van hun niveau snel navigeren tussen kopelementen. Figuur 16 toont een vorm die in kleinere segmenten gebruikend rubrieken wordt verdeeld. In dit voorbeeld wordt de volgende kopstructuur gebruikt:

* Rubriek niveau 1: Productaanvraag
   * Kop niveau 2: Bestelgegevens
      * Koptekst niveau 3: leveringsopties
* Rubriek niveau 2: Aanvullende informatie
   * Rubriek niveau 3: Persoonlijke gegevens
   * Koptekst niveau 3: Adres

![ Structurerend een vorm gebruikend rubrieken ](/help/forms/using/assets/image-16.png)

Figuur 16: **Structurerend een vorm gebruikend rubrieken**

Deze koppen zijn enkel statische tekstelementen die een specifieke doopvontgrootte en een koprol met het aangewezen niveau werden gegeven.

>[!NOTE]
> Als u alleen de visuele weergave van een tekstlabel wijzigt, zodat dit lijkt op een kop, herkennen schermlezers het label niet als een kop. U moet een koprol toepassen.

Zorg altijd dat de volgorde van de kopniveaus logisch is. Een subsectie van een kop van niveau 2 moet bijvoorbeeld altijd een kop van niveau 3 zijn. U moet niveaus nooit overslaan bij het markeren van subsecties. Gebruikers van schermlezers gebruiken de verschillende niveaus voor een beter inzicht in de structuur van het formulier. Nadat de gebruiker bijvoorbeeld een kop van niveau 2 heeft aangetroffen, kan hij met een sneltoets naar de koppen van niveau 3 zoeken en bepalen of er subsecties zijn. Als u niveaus overslaat, zal de gebruiker problemen hebben om deze subsecties te identificeren.

### Lijsten markeren

Soms is het ook handig om lijstitems aan uw formulier toe te voegen. Lijsten zijn handig om verwante items te groeperen en bieden gebruikers van schermlezers de mogelijkheid om te weten hoeveel items zich in een lijst bevinden en er snel voorbij te navigeren. Als u lijsten correct markeert, wordt de structuur van het formulier duidelijker voor schermlezers.

In LiveCycle Designer maakt u lijsten met behulp van subformulieren met de volgende stappen:

1. Selecteer een subformulier met de inhoud die wordt gemarkeerd als lijstitems.
1. Selecteer in het palet Toegankelijkheid de optie Lijst als rol.
1. Selecteer elk genest subformulier in het subformulier Lijst en stel de rol in op Lijstitem.

>[!NOTE]
> Een rol Lijstitem kan alleen worden toegewezen aan een subformulier dat zich bevindt in een subformulier met de rol Lijst. U kunt een tabel of tabelrij niet definiëren als een lijst of lijstitem. Een lijstitem kan echter wel een tabel bevatten.

**Verwante controlepunten**
* § 508 § 1934.22
   * o) Er moet een methode worden ingevoerd waarmee gebruikers herhaalde navigatiekoppelingen kunnen overslaan.
* WCAG 1.0
   * 3.5 Gebruik koptekstelementen om de documentstructuur over te brengen en deze te gebruiken volgens de specificaties (P2).
   * 3.6 Lijsten en lijstitems correct markeren. (P2)
   * 12.3 Verdeel grote blokken informatie in beter te beheren groepen waar dat natuurlijk en passend is. (P2)
   * 13.3 Geef informatie over de algemene lay-out van een site (bijvoorbeeld een site-overzicht of een inhoudsopgave).
   * 13.4 Gebruik van navigatiemechanismen op een consistente manier (P2).
* WCAG 2.0
   * 1.3.2 Betekenisvolle sequentie: wanneer de sequentie waarin inhoud wordt gepresenteerd van invloed is op de betekenis ervan, kan een correcte leesvolgorde via programmacode worden bepaald. (Niveau A)
   * 2.4.1 Blokkeringen omzeilen: er is een mechanisme beschikbaar waarmee blokken inhoud die op meerdere webpagina&#39;s worden herhaald, kunnen worden overgeslagen. (Niveau A)
   * 2.4.5 Veelvoudige Manieren: Meer dan één manier is beschikbaar om van een Web-pagina binnen een reeks Web-pagina&#39;s de plaats te bepalen behalve waar de Web-pagina het resultaat van, of een stap in, een proces is. (Niveau AA)
   * 2.4.6 Koppen en labels: koppen en labels beschrijven het onderwerp of het doel. (Niveau AA)
   * 2.4.10 Sectiekoppen: Sectiekoppen worden gebruikt om de inhoud te ordenen. (Niveau AAA)
   * 3.2.3 Consistente navigatie: Navigatiemechanismen die op meerdere webpagina&#39;s binnen een set webpagina&#39;s worden herhaald, vinden in dezelfde relatieve volgorde plaats telkens wanneer ze worden herhaald, tenzij de gebruiker een wijziging aanbrengt. (Niveau AA)


## Vermijd verstorende scripts{#avoid-disruptive-scripting}

In het kader van het formulierontwerpproces kunnen formulierontwikkelaars scripts gebruiken om gebruikers een rijkere ervaring te bieden. U kunt scripts toevoegen aan de meeste formuliervelden en -objecten. U kunt bijvoorbeeld eenvoudige scripts maken om waarden op een interactief formulier dynamisch bij te werken als reactie op de gebruikersinvoer.

Houd bij het ontwerpen van scripts voor toegankelijkheid rekening met de volgende algemene richtlijnen:

* Houd de formulierinhoud vrij van visuele onderbrekingen. Vermijd bijvoorbeeld functies die ervoor zorgen dat inhoud gaat flikkeren, knipperen of verplaatsen.
* Zorg ervoor dat pop-upvensters alleen worden weergegeven als gevolg van handelingen die door de gebruiker zijn gestart. Op dezelfde manier mag u de huidige focus van het formulier (de huidige weergave van de gebruiker) niet wijzigen of de inhoud opnieuw weergeven, tenzij dit wordt geïnitieerd door de gebruiker. Als de gebruiker bijvoorbeeld velden invult in de onderste helft van het formulier, mag de focus niet veranderen naar de linkerbovenhoek van het formulier, tenzij de gebruiker naar deze locatie navigeert.
* Gehandicapte gebruikers hebben mogelijk meer tijd nodig om invoer in velden te kunnen leveren. Geef geen op tijd gebaseerde reacties op voor invoervelden.
* Scripts op de client kunnen problemen opleveren met schermlezers en toetsenborden als het script de focus van de clienttoepassing wijzigt. De gebeurtenissen change en mouseEnter kunnen bijvoorbeeld bij vervolgkeuzelijsten of keuzelijsten onverwachte acties veroorzaken. Controleer of uw clientscripts geen problemen opleveren voor schermlezers en gebruikers met alleen het toetsenbord.
* Gebruikers van ondersteunende hulpmiddelen hebben soms extra tijd nodig om taken uit te voeren. In elk geval waar een getimede routine op het punt staat te verlopen, toon een toegankelijk bericht om voor een uitbreiding toe te staan. Dringende vakken die via JavaScript zijn gemaakt, zijn bruikbaar voor ondersteunende hulpmiddelen. Een nieuw venster met een bericht alarmerend de gebruiker van een dreigende tijd uit kan ook worden opgesteld.

**Verwante controlepunten**:
* § 508 § 194.22
   * l) Wanneer pagina&#39;s scripttalen gebruiken om inhoud weer te geven of interface-elementen te maken, moet de informatie die door het script wordt verstrekt, worden geïdentificeerd met functionele tekst die door hulpprogramma&#39;s kan worden gelezen.
   * p) Wanneer een tijdig antwoord vereist is, moet de gebruiker worden gewaarschuwd en voldoende tijd krijgen om aan te geven dat meer tijd nodig is.
* WCAG 1.0
   * 1.4 Voor elke op tijd gebaseerde multimediapresentatie (bv. een film of animatie) moet u gelijkwaardige alternatieven (bv. bijschriften of auditieve beschrijvingen van de visuele track) synchroniseren met de presentatie (P1).
   * 6.2 Zorg ervoor dat equivalenten voor dynamische inhoud worden bijgewerkt wanneer de dynamische inhoud verandert.
   * 6.3 Zorg ervoor dat pagina&#39;s bruikbaar zijn wanneer scripts, applets of andere programmatische objecten worden uitgeschakeld of niet worden ondersteund. Als dit niet mogelijk is, geef gelijkwaardige informatie op een andere toegankelijke pagina.
   * 6.5 Zorg ervoor dat dynamische inhoud toegankelijk is of een alternatieve presentatie of pagina (P2) biedt.
   * 8.1 maak programmatic elementen zoals manuscripten en applets direct toegankelijk of compatibel met ondersteunende technologieën [ Prioriteit 1 als de functionaliteit belangrijk is en niet elders ] wordt voorgesteld, anders (P2).
   * 9.3 Voor manuscripten, specificeer logische gebeurtenismanagers eerder dan apparaat-afhankelijke gebeurtenismanagers (P2).
   * 10.1 Totdat gebruikersagenten gebruikers toestaan om gekaapte vensters uit te zetten, veroorzaken geen pop-ups of andere vensters om te verschijnen en veranderen niet het huidige venster zonder de gebruiker op de hoogte te brengen.
* WCAG 2.0
   * 3.2.1 Bij focus: wanneer een component focus krijgt, leidt dit niet tot een contextwijziging. (Niveau A)
   * 3.2.2 Bij invoer: het wijzigen van de instelling van een gebruikersinterfacecomponent leidt niet automatisch tot een wijziging van de context, tenzij de gebruiker op de hoogte is gesteld van het gedrag voordat de component wordt gebruikt. (Niveau A)
   * 3.2.5 Wijziging op verzoek: wijzigingen in de context worden alleen geïnitieerd door een verzoek van de gebruiker of er is een mechanisme beschikbaar om dergelijke wijzigingen uit te schakelen. (Niveau AAA)

## Controleer of alle audio- en video-inhoud toegankelijk is{#ensure-audio-video-accessible}

Als uw formulieren audio- of video-inhoud bevatten, inclusief audio- en videoclips, moet u ervoor zorgen dat deze inhoud toegankelijk is. Zorg er in het bijzonder voor dat videoclips die in formulieren zijn opgenomen, bijschriften (ook wel ondertitels genoemd) bevatten voor doven en moeilijke gehoorgebruikers en videobeschrijvingen voor blinde gebruikers. Voor audiobestanden die niet met video-inhoud zijn gesynchroniseerd, volstaat een eenvoudige transcriptie.
Voor Flash gebaseerde media, raadpleeg [ verbinding ](/help/forms/using/best-practices-for-creating-forms-in-designer.md) voor informatie bij het verstrekken van titels.

**Verwante controlepunten**:
* § 508 § 194.22
   * b) Equivalente alternatieven voor multimediapresentaties worden gesynchroniseerd met de presentatie.
* WCAG 1.0
   * 1.1 Geef een tekstequivalent op voor elk niet-tekstelement (bijvoorbeeld via &quot;alt&quot;, &quot;longdesc&quot; of in elementinhoud). Dit omvat: afbeeldingen, grafische voorstellingen van tekst (inclusief symbolen), gebieden met afbeeldingen met hyperlinks, animaties (bijvoorbeeld geanimeerde GIFFEN), applets en programmatische objecten, ascii-illustraties, frames, scripts, afbeeldingen die worden gebruikt als lijstopsommingstekens, spacers, grafische knoppen, geluiden (al dan niet met gebruikersinteractie), zelfstandige audiobestanden, audiotracks van video en video (P1).
   * 1.3 Totdat gebruikersagenten automatisch het tekstequivalent van een visueel spoor kunnen lezen, verstrek een auditieve beschrijving van de belangrijke informatie van het visuele spoor van een presentatie van verschillende media (P1).
   * 1.4 Voor elke op tijd gebaseerde multimediapresentatie (bv. een film of animatie) moet u gelijkwaardige alternatieven (bv. bijschriften of auditieve beschrijvingen van de visuele track) synchroniseren met de presentatie (P1).
* WCAG 2.0
   * 1.2.1 Alleen audio en alleen video (vooraf opgenomen): Voor vooraf opgenomen media met alleen audio en vooraf opgenomen alleen video geldt het volgende, behalve wanneer de audio of video een alternatief voor tekst is en duidelijk als zodanig is gelabeld: (Niveau A)
   * 1.2.2 Bijschriften (vooraf opgenomen): er zijn bijschriften beschikbaar voor alle vooraf opgenomen audio-inhoud in gesynchroniseerde media, behalve wanneer de media een media-alternatief voor tekst zijn en duidelijk als zodanig zijn gelabeld. (Niveau A)
   * 1.2.3 Audio-beschrijving of media-alternatief (vooraf opgenomen): een alternatief voor tijdgebaseerde media of audiobeschrijving van de vooraf opgenomen video-inhoud wordt aangeboden voor gesynchroniseerde media, behalve wanneer de media een mediafiatief voor tekst zijn en duidelijk als zodanig zijn gelabeld. (Niveau A)
   * 1.2.4 Bijschriften (live): Bijschriften worden geleverd voor alle live audio-inhoud in gesynchroniseerde media. (Niveau AA)
   * 1.2.5 Audiobeschrijving (vooraf opgenomen): er is een audiobeschrijving beschikbaar voor alle vooraf opgenomen video-inhoud in gesynchroniseerde media. (Niveau AA)
   * 1.2.6 Taal ondertekenen (vooraf opgenomen): er is voorzien in een gebarentaal-interpretatie voor alle vooraf opgenomen audio-inhoud in gesynchroniseerde media. (Niveau AAA)
   * 1.2.7 Uitgebreide audiobeschrijving (vooraf opgenomen): wanneer pauzes in voorgrondaudio onvoldoende zijn om audiobeschrijvingen de indruk van de video te laten zien, wordt een uitgebreide audiobeschrijving gegeven voor alle vooraf opgenomen video-inhoud in gesynchroniseerde media. (Niveau AAA)
   * 1.2.8 Media-alternatief (vooraf opgenomen): er is een alternatief voor op tijd gebaseerde media beschikbaar voor alle vooraf opgenomen gesynchroniseerde media en voor alle vooraf opgenomen alleen-video-media. (Niveau AAA)
   * 1.2.9 Alleen audio (Live): er is een alternatief voor op tijd gebaseerde media met gelijkwaardige informatie voor alleen live audio-inhoud beschikbaar. (Niveau AAA)

## Identificeer natuurlijke taal en om het even welke veranderingen in taal{#identify-natural-language}

Formulierinhoud wordt gelezen door ondersteunende hulpmiddelen die taalspecifieke spraaksynthesizers gebruiken. Het is dus belangrijk dat u de primaire taal van het formulier correct herkent om ervoor te zorgen dat formulieren in de bedoelde taal worden gelezen.

Als de tekst (of alternatieve tekst) in uw formulieren in meerdere talen wordt weergegeven, moet u de gebieden van het formulier identificeren waarin een overgang van de ene taal naar de andere wordt gemaakt.

In LiveCycle Designer wordt de primaire taal ingesteld door de eigenschap Landinstelling van het formulier en de eigenschap Landinstelling voor het subformulier op hoofdniveau in te stellen. Als u wijzigingen in de primaire taal wilt identificeren, wijzigt u de eigenschap Landinstelling voor elk object dat een andere taal dan de taal van het formulier gebruikt.

De eigenschap Landinstelling van een formulier instellen:
1. Kies Bestand > Formuliereigenschappen en selecteer het tabblad Standaard
2. Selecteer de juiste taal voor de landinstelling van het formulier (zie Figuur 17)
3. Klik op OK

![ Veranderend de Plaats van de Vorm op de de dialoogdoos van de Eigenschappen van de Vorm ](/help/forms/using/assets/image-17.png)

Figuur 17: **Veranderend de Plaats van de Vorm op de de dialoogdoos van de Eigenschappen van de Vorm**

U kunt als volgt de eigenschap Lokaal instellen van het subformulier op hoofdniveau of een object waarvoor een andere taal vereist is:
1. Het bovenste subformulier of object in de ontwerpweergave selecteren
1. Geef het palet Object weer door Venster > Object te kiezen
1. Selecteer in het palet Object het tabblad Veld en selecteer in de lijst Landinstelling de taal die voor het object moet worden gebruikt (zie Figuur 18). Houd er bij het toepassen van verschillende landinstellingen op afzonderlijke objecten rekening mee dat de objecten in tabellen en subformulieren automatisch dezelfde landinstelling krijgen als de tabel en het subformulier.

![ Veranderend de scène van een voorwerp ](/help/forms/using/assets/image-18.png)

Figuur 18: **Veranderend de scène van een voorwerp**

**Verwante controlepunten**:
* WCAG 1.0
   * 4.1 Wijzigingen in de natuurlijke taal van de tekst van een document en eventuele tekstequivalenten (bijv. bijschriften) duidelijk identificeren.
* WCAG 2.0
   * 3.1.1 Taal van Pagina: De standaard menselijke taal van elke Web-pagina kan programmatically worden bepaald. (Niveau A)
   * 3.1.2 Taal van onderdelen: de menselijke taal van elke passage of uitdrukking in de inhoud kan via programmacode worden bepaald, behalve voor eigennamen, technische termen, woorden van onbepaalde taal en woorden of woordgroepen die deel zijn geworden van het woordenboek van de direct omliggende tekst. (Niveau AA)
