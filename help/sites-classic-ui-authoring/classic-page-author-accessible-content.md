---
title: Toegankelijke content maken (WCAG 2.0-compatibiliteit)
seo-title: Toegankelijke content maken (WCAG 2.0-compatibiliteit)
description: WCAG 2.0 bestaat uit een reeks technologieonafhankelijke richtlijnen en succescriteria om ervoor te zorgen dat webcontent toegankelijk en bruikbaar is voor personen met een handicap.
seo-description: WCAG 2.0 bestaat uit een reeks technologieonafhankelijke richtlijnen en succescriteria om ervoor te zorgen dat webcontent toegankelijk en bruikbaar is voor personen met een handicap.
page-status-flag: de-activated
uuid: c2c0cac0-2a9f-478d-8261-e8cc894aae34
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 378bc33d-ab6c-4651-9688-102c961561fc
translation-type: tm+mt
source-git-commit: df992fc0204519509c4662a7d4315939af2fc92c
workflow-type: tm+mt
source-wordcount: '9241'
ht-degree: 9%

---


# Toegankelijke content maken (WCAG 2.0-compatibiliteit){#creating-accessible-content-wcag-conformance}

>[!CAUTION]
>
>Aangezien de klassieke gebruikersinterface is afgekeurd in AEM 6.4, is de inhoud op deze pagina niet bijgewerkt voor WCAG 2.1.
>
>Raadpleeg de volgende pagina&#39;s voor meer informatie over AEM en WCAG 2.1:
>
>* [AEM en de Web Accessibility Guidelines](/help/managing/web-accessibility.md)
>* [Snelgids voor WCAG 2.1](/help/managing/qg-wcag.md)
>* [Toegankelijke content maken (WCAG 2.1-compatibiliteit)](/help/sites-authoring/creating-accessible-content.md)


WCAG 2.0 bestaat uit een reeks technologieonafhankelijke richtlijnen en succescriteria om ervoor te zorgen dat webcontent toegankelijk en bruikbaar is voor personen met een handicap.

>[!NOTE]
>
>Zie ook:
>
>* Onze [Snelle Gids aan WCAG 2.0](/help/managing/qg-wcag.md) voor meer details
>* [De Rich Text Editor configureren voor het produceren van toegankelijke inhoud](/help/sites-administering/rte-accessible-content.md)
>



Deze worden ingedeeld op basis van drie compatibiliteitsniveaus: Niveau A (laagste), Niveau AA en Niveau AAA (hoogste). De niveaus worden kort samengevat als volgt gedefinieerd:

* **Niveau A:** Uw site bereikt een minimaal basistoegankelijkheidsniveau. Om aan dit niveau te voldoen moet aan alle slagingscriteria voor Niveau A worden voldaan.
* **Niveau AA:** Dit is een ideaal toegankelijkheidsniveau waarnaar u wilt streven, waarbij uw site een verbeterd toegankelijkheidsniveau bereikt, zodat deze voor de meeste mensen in de meeste situaties en met de meeste technologieën toegankelijk is. Om aan dit niveau te voldoen moet aan alle slagingscriteria voor Niveau A en Niveau AA worden voldaan.
* **Niveau AAA:** Uw site bereikt een zeer hoog toegankelijkheidsniveau. Om aan dit niveau te voldoen moet aan alle slagingscriteria voor Niveau A, Niveau AA en Niveau AAA worden voldaan.

Wanneer u uw site maakt, moet u het algemene niveau bepalen waaraan u uw site wilt laten voldoen.

In het volgende gedeelte worden de [WCAG 2.0-richtsnoeren](https://www.w3.org/TR/WCAG20/#guidelines) gepresenteerd met de bijbehorende succescriteria voor Niveau A- en Niveau AA- [conformiteitsniveaus](https://www.w3.org/TR/UNDERSTANDING-WCAG20/conformance.html).

>[!NOTE]
>
>Aangezien het niet mogelijk is om voor bepaalde soorten inhoud aan alle criteria van de Amerikaanse club van automobilisten van niveau A te voldoen, wordt het niet aanbevolen dat dit niveau van overeenstemming als algemeen beleid wordt vereist.

>[!NOTE]
>
>In dit document gebruiken we:
>
>* de korte namen voor de [WCAG 2.0-richtsnoeren](https://www.w3.org/TR/WCAG20/#guidelines).
>* de nummering die wordt gebruikt in de richtsnoeren [van](https://www.w3.org/TR/WCAG20/#guidelines) WCAG 2.0 voor kruisverwijzingen naar de WCAG-website.
>



## Beginsel 1: Perceerbaar {#principle-perceivable}

[Beginsel 1: Mogelijkheid - De informatie en gebruikersinterfacecomponenten moeten aan gebruikers op manieren presenteerbaar zijn zij kunnen waarnemen.](https://www.w3.org/TR/WCAG20/#perceivable)

### Alternatieven voor tekst (1.1) {#text-alternatives}

[Richtsnoer 1.1 Tekstalternatieven: Maak tekstalternatieven voor alle niet-tekstuele inhoud, zodat deze kan worden gewijzigd in andere formulieren die u nodig hebt, zoals grote gedrukte tekst, braille, spraak, symbolen of eenvoudigere taal.](https://www.w3.org/TR/WCAG20/#text-equiv)

### Niet-tekstuele inhoud (1.1.1) {#non-text-content}

* Succescriterium 1.1.1
* Niveau A
* Niet-tekstuele inhoud: Alle niet-tekstuele inhoud die aan de gebruiker wordt aangeboden, heeft een tekstalternatief dat het gelijkwaardige doel dient, behalve in de situaties hieronder.

#### Doel - Niet-tekstuele inhoud (1.1.1) {#purpose-non-text-content}

De informatie op een webpagina kan in vele verschillende niet-tekstformaten, zoals beelden, video&#39;s, animaties, grafieken worden verstrekt. Personen die blind zijn of een ernstige visuele handicap hebben, kunnen geen niet-tekstuele inhoud zien, maar hebben wel toegang tot tekstinhoud door deze door een schermlezer te laten lezen of in tactiele vorm te laten weergeven door een brailleweergaveapparaat. Dus door tekstalternatieven voor inhoud in grafische indeling te bieden, kunnen mensen die de grafische inhoud niet kunnen zien, toegang krijgen tot een equivalente versie van de informatie die de inhoud biedt.

Een nuttig extra voordeel is dat tekstopties het mogelijk maken dat niet-tekstuele inhoud wordt geïndexeerd door zoekmachinetechnologie.

#### Ontmoeten - Niet-tekstuele inhoud (1.1.1) {#how-to-meet-non-text-content}

Voor statische afbeeldingen is het basisvereiste dat een equivalent tekstalternatief voor de afbeelding wordt geboden. Dit kan in het veld **Alt-tekst** worden gedaan:

>[!NOTE]
>
>Sommige standaardcomponenten, zoals **Carrousel** en **Diapresentatie**, bieden geen manier om alternatieve tekstbeschrijvingen aan afbeeldingen toe te voegen. Bij het uitvoeren van versies van deze componenten voor uw AEM-exemplaar zal uw ontwikkelingsteam dergelijke componenten moeten configureren om het kenmerk `alt`[ te ondersteunen zodat auteurs dit aan de content kunnen toevoegen (zie Ondersteuning toevoegen voor aanvullende HTML-elementen en -kenmerken](/help/sites-administering/rte-accessible-content.md#add-support-for-more-html-elements-and-attributes)).

Het veld **Alt-tekst** is beschikbaar op het tabblad **Geavanceerde** afbeeldingseigenschappen van het dialoogvenster **Afbeeldingscomponent** :

![Dialoogvenster van de component Image in de klassieke UI bewerken; geeft het veld Alt-tekst weer.](assets/chlimage_1-17a.png)

AEM voegt standaard een **Alt-tekst** toe aan uw afbeeldingen. Voor de klassieke UI zijn er twee verschillende scenario&#39;s voor hoe het standaardattribuut wordt gecreeerd (hoewel de standaardwaarde als alternatief kan niet voldoende zijn en zeer waarschijnlijk zal moeten op het **Geavanceerde** beeldeigenschappen tabel worden uitgegeven):

* Bestand:

   Een afbeelding wordt geüpload vanaf de vaste schijf van de gebruiker. Als u een afbeeldingscomponent aan een pagina toevoegt en vervolgens een afbeelding op de vaste schijf of een andere bron kiest, wordt de standaardwaarde voor **Alt-tekst** `file`. Dit moet worden gewijzigd op het tabblad **Geavanceerde** afbeeldingseigenschappen. Deze waarde wordt ook hier niet weergegeven in het veld **Alt-tekst** , maar als de waarde wordt gewijzigd, wordt de nieuwe waarde in het veld weergegeven.

* Element:

   Er wordt een afbeelding toegevoegd vanuit de gegevensopslagruimte voor digitale middelen. Als u een afbeelding van de gegevensopslagruimte voor digitale elementen naar een webpagina sleept, worden de waarden voor **Titel** en **Alt-tekst** voor die afbeelding ontleend aan de metagegevens voor die afbeelding.

>[!NOTE]
>
>In beide bovenstaande scenario&#39;s is de standaardwaarde voor **Alt-tekst** niet zichtbaar op het tabblad **Geavanceerde afbeeldingseigenschappen** . Als u de standaardwaarde wilt wijzigen, typt u een nieuwe waarde in het veld **Alt-tekst** .

>[!NOTE]
>
>Als uw afbeelding zuiver decoratief is (zie Correcte [tekstalternatieven](#creating-good-text-alternatives)maken), kunt u een spatie in het veld **Alt-tekst** invoeren met de spatiebalk. Hierdoor wordt een leeg `alt` kenmerk gemaakt, waardoor een schermlezer wordt gevraagd de afbeelding te negeren.

#### Alternatieven voor goede tekst maken {#creating-good-text-alternatives}

Er zijn verschillende vormen van niet-tekstuele inhoud, zodat de waarde van het tekstoptie afhankelijk is van de rol die de afbeelding in de webpagina speelt. De volgende algemene regels voor duim zijn van toepassing:

* Alternatieven voor tekst moeten beknopt zijn, maar toch duidelijk aangeven welke essentiële informatie door de niet-tekstuele inhoud wordt verstrekt.
* Te lange beschrijvingen (meer dan 100 tekens) moeten worden vermeden. Als een tekstalternatief meer details vereist:

   * een korte beschrijving geven in de alternatieve tekst
   * en hebben een langere beschrijving in tekst elders op dezelfde pagina of in een aparte webpagina. Koppel deze afzonderlijke beschrijving door van de afbeelding een koppeling te maken of door een tekstkoppeling naast de afbeelding te plaatsen.

* Alternatieve tekst mag geen inhoud repliceren die in tekstvorm dichtbij op dezelfde pagina wordt geleverd. Houd er rekening mee dat veel afbeeldingen illustraties zijn van punten die al in de tekst van een pagina zijn opgenomen, zodat er al een gedetailleerd tekstalternatief bestaat.
* Als de niet-tekstinhoud een koppeling naar een andere pagina of een ander document is en er geen andere tekst deel uitmaakt van dezelfde koppeling, moet de alternatieve tekst voor de afbeelding de bestemming van de koppeling aangeven en niet de afbeelding.
* Als de niet-tekstuele inhoud zich in een knopelement bevindt en er geen tekst bestaat die deel uitmaakt van dezelfde knop, moet de alternatieve tekst van de afbeelding de functionaliteit van de knop aangeven en de afbeelding niet beschrijven.
* Het is volkomen aanvaardbaar dat een afbeelding een lege (null) alternatieve tekst krijgt, maar alleen als de afbeelding geen alternatieve tekst heeft (bijvoorbeeld een zuiver decoratieve afbeelding) of als de equivalente tekst al in de paginatekst staat.

Het [W3C-concept: De Technieken van HTML5 voor het verstrekken van nuttige tekstalternatieven](https://dev.w3.org/html5/alt-techniques/) heeft meer details en voorbeelden van aangewezen alternatieve tekstvoorziening voor beelden van verschillende types.

Specifieke typen niet-tekstuele inhoud waarvoor tekstopties nodig zijn, zijn onder meer:

* Illustratieve foto&#39;s:

   Dit zijn afbeeldingen van mensen, objecten of plaatsen. Denk na over de rol van de foto op de pagina. Een geschikt tekstequivalent is waarschijnlijk *Foto van[object ]*, maar kan afhankelijk zijn van de omringende tekst.

* Pictogrammen:

   Dit zijn kleine pictogrammen (afbeeldingen) die specifieke informatie bevatten. Ze moeten consistent worden gebruikt op een pagina en site. Alle exemplaren van het pictogram op een pagina of site moeten hetzelfde korte en korte tekstalternatief hebben, tenzij dit leidt tot onnodige duplicatie van aangrenzende tekst.

* Grafieken en grafieken:

   Deze vertegenwoordigen meestal numerieke gegevens. U kunt dus een alternatief voor tekst bieden door een korte samenvatting op te nemen van de belangrijkste trends die in de grafiek of afbeelding worden weergegeven. Geef indien nodig ook een gedetailleerdere beschrijving in de tekst op met behulp van het veld **Beschrijving** op het tabblad **Geavanceerde** afbeeldingseigenschappen. Bovendien kunt u de brongegevens elders op de pagina of site in tabelvorm opgeven.

   ![Voorbeeld van een grafiek. Hieronder ziet u de beste aanpak om een alternatief te bieden.](assets/chlimage_1-2a.jpeg)

   Als u een alternatief wilt bieden voor dit voorbeelddiagram, voegt u een beknopte `alt` tekst toe aan de afbeelding zelf en volgt u de afbeelding met een alternatief voor volledige tekst.

   ```xml
   <p><img src="figure1.gif" alt="Figure 1" ></p>
   <p> Figure 1. Distribution of Articles by Journal Category.
   Pie chart: Language=68%, Education=14% and Science=18%.</p>
   ```

   >[!NOTE]
   >
   >Het bovenstaande fragment wordt alleen gebruikt om de volgorde te illustreren. U wordt aangeraden de component **Afbeelding** te gebruiken in plaats van de `img src` verwijzing die hierboven is gebruikt.

   In AEM kan dit worden gedaan gebruikend een combinatie van de gebieden van de Tekst **en van de** Beschrijving **van** Alt in de de configuratiedialoog van het beeld - zoals in [hoe te ontmoeten - Niet-tekstuele Inhoud (1.1.1)](#how-to-meet-non-text-content).

* Kaarten, diagrammen, stroomdiagrammen:

   Voor afbeeldingen die ruimtelijke gegevens leveren (bijvoorbeeld om beschrijvende relaties tussen objecten of een proces te ondersteunen), zorgt u ervoor dat het sleutelbericht in tekstopmaak wordt weergegeven. Voor kaarten is het opgeven van een volledige-tekstequivalent waarschijnlijk onpraktisch, maar als de kaart wordt verstrekt als manier om mensen te helpen hun weg naar een bepaalde plaats vinden, dan kan de alternatieve tekst van de afbeelding kort *Kaart van X* aangeven, en vervolgens elders op de pagina of via het veld **Beschrijving** op het tabblad **Geavanceerd** van de component **Afbeelding** een routebeschrijving naar die plaats in tekst opgeven.

* CAPTCHA&#39;s:

   Een CAPTCHA is een *volledig geautomatiseerde Publieke Turing-test om computers en mensen te informeren*. Het is een veiligheidscontrole die op webpagina&#39;s wordt gebruikt om mensen van kwaadaardige software te onderscheiden, maar die toegankelijkheidsbarrières kan veroorzaken. Dit zijn afbeeldingen waarvoor gebruikers een beschrijving moeten geven van wat ze zien om een beveiligingstest te kunnen doorstaan. Het is duidelijk niet mogelijk om een tekstalternatief voor de afbeelding te bieden, dus in plaats daarvan moet u alternatieve niet-grafische oplossingen overwegen.

   De W3C biedt een aantal suggesties, zoals:Elk van deze benaderingen heeft zijn eigen verdiensten en nadelen.

   * Logische puzzels
   * Het gebruik van geluidsuitvoer in plaats van afbeeldingen
   * Beperkte gebruikaccounts en spamfilters.

* Achtergrondafbeeldingen:

   Deze worden bereikt met CSS (Cascading Style Sheets) in plaats van met HTML. Dit betekent dat het niet mogelijk is een alternatieve tekstwaarde op te geven. Achtergrondafbeeldingen mogen daarom geen belangrijke tekstuele informatie opleveren. Als dat wel het geval is, moet deze informatie ook in de paginatekst worden vermeld.

   Het is echter belangrijk dat een andere achtergrond wordt weergegeven wanneer de afbeelding niet kan worden weergegeven.

   >[!NOTE]
   >
   >Er moet een passend contrastniveau zijn tussen de achtergrond en de voorgrondtekst. dit wordt meer in detail besproken in [Contrast (Minimum) (1.4.3)](#contrast-minimum).

#### Meer informatie - Niet-tekstuele inhoud (1.1.1) {#more-information-non-text-content}

* [Werken met succescriteria 1.1.1](https://www.w3.org/TR/UNDERSTANDING-WCAG20/text-equiv-all.html)
* [Voldoen aan criteria 1.1.1](https://www.w3.org/WAI/WCAG20/quickref/#text-equiv)
* [W3C: HTML5-technieken voor het bieden van bruikbare tekstalternatieven (concept)](https://dev.w3.org/html5/alt-techniques/)
* [W3C-uitleg van en alternatieven voor CAPTCHA&#39;s](https://www.w3.org/TR/turingtest/)

### Op tijd gebaseerde media (1.2) {#time-based-media}

[Richtsnoer 1.2 Op tijd gebaseerde media: Alternatieven bieden voor tijdgebaseerde media.](https://www.w3.org/TR/WCAG20/#text-equiv)

Dit heeft betrekking op webinhoud die op *tijd is gebaseerd*. Dit geldt voor inhoud die de gebruiker kan afspelen (zoals video, audio en bewegende inhoud) en die vooraf kan worden opgenomen of een live stream.

### Alleen audio en alleen video (vooraf opgenomen) (1.2.1) {#audio-only-and-video-only-pre-recorded}

* Succescriterium 1.2.1
* Niveau A
* Alleen audio en alleen video (vooraf opgenomen): Voor vooraf opgenomen audio-slechts en vooraf opgenomen video-slechts media, zijn het volgende waar, behalve wanneer de audio of de video een media alternatief voor tekst is en duidelijk als dusdanig geëtiketteerd:

   * Alleen vooraf opgenomen audio: Er is een alternatief voor op tijd gebaseerde media beschikbaar met gelijkwaardige informatie voor vooraf opgenomen inhoud met alleen audio.
   * Alleen vooraf opgenomen video: Er is een alternatief voor op tijd gebaseerde media of een audiotrack beschikbaar met gelijkwaardige informatie voor vooraf opgenomen video-inhoud.

#### Doel - Alleen audio en alleen video (vooraf opgenomen) (1.2.1) {#purpose-audio-only-and-video-only-pre-recorded}

Toegankelijkheidsproblemen voor video en audio kunnen worden ondervonden door:

* Mensen met een visuele handicap zonder soundtrack of de soundtrack volstaat niet om hen te informeren over wat er in de video of animatie gebeurt;
* personen met een slechthorende werking of doof zijn, die de soundtrack niet kunnen horen;
* Mensen die de soundtrack kunnen horen, maar niet begrijpen wat er wordt gesproken (bijvoorbeeld omdat het in een taal staat die ze niet begrijpen).

Video of audio is mogelijk ook niet beschikbaar voor gebruikers die browsers of apparaten gebruiken die het afspelen van inhoud in bepaalde media-indelingen, zoals Adobe Flash, niet ondersteunen.

Als u deze informatie in een andere indeling verstrekt, zoals tekst (of audio voor video zonder audio), kunt u deze toegankelijk maken voor mensen die geen toegang hebben tot de oorspronkelijke inhoud.

#### Hoe kan ik-alleen-audio en alleen-video (vooraf opgenomen) (1.2.1) {#how-to-meet-audio-only-and-video-only-pre-recorded}

* Als de inhoud vooraf opgenomen audio zonder video is (zoals een podcast):

   * Geef een koppeling voor of na de inhoud op naar een teksttranscriptie van de audio-inhoud.

      De transcriptie moet een HTML-pagina zijn met een tekstequivalent van alle gesproken en belangrijke niet-gesproken inhoud, plus een indicatie van wie spreekt, een beschrijving van de instelling, spraakexpressies en een beschrijving van andere belangrijke audio.

* Als de inhoud een animatie of een vooraf opgenomen video zonder audio is:

   * Een koppeling verschaffen vlak voor of na de inhoud naar een equivalente tekstbeschrijving van de informatie die door de video wordt verschaft
   * Of een equivalente audiobeschrijving in een veelgebruikte audio-indeling, zoals MP3.

>[!NOTE]
>
>Als de audio- of video-inhoud wordt aangeboden als alternatief voor inhoud die al in een andere indeling op een webpagina bestaat, hoeven de bovenstaande vereisten niet te worden nageleefd. Als een video bijvoorbeeld een lijst met tekstinstructies illustreert, vereist deze video geen alternatief omdat de tekstinstructies al als alternatief voor de video fungeren.

Het invoegen van multimedia, met name Flash-inhoud, in uw AEM-webpagina&#39;s lijkt op het invoegen van een afbeelding. Aangezien multimedia-inhoud echter veel meer is dan een stilstaand beeld, zijn er verschillende instellingen en opties om te bepalen hoe de multimedia wordt afgespeeld.

>[!NOTE]
>
>Als u multimedia gebruikt met informatieve inhoud, moet u ook koppelingen naar alternatieven maken. Als u bijvoorbeeld een teksttranscriptie wilt opnemen, maakt u een HTML-pagina waarop de transcriptie wordt weergegeven en voegt u vervolgens een koppeling toe naast of onder de audio-inhoud.

#### Meer informatie - Alleen audio en alleen video (vooraf opgenomen) (1.2.1) {#more-information-audio-only-and-video-only-pre-recorded}

* [Werken met succescriteria 1.2.1](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-av-only-alt.html)
* [Voldoen aan criteria 1.2.1](https://www.w3.org/WAI/WCAG20/quickref/#media-equiv)

### Bijschriften (vooraf opgenomen) (1.2.2) {#captions-pre-recorded}

* Succescriterium 1.2.2
* Niveau A
* Bijschriften (vooraf opgenomen): Er zijn bijschriften beschikbaar voor alle vooraf opgenomen audio-inhoud in gesynchroniseerde media, behalve wanneer de media een media-alternatief voor tekst zijn en duidelijk als zodanig zijn gelabeld.

#### Doel - Bijschriften (vooraf opgenomen) (1.2.2) {#purpose-captions-pre-recorded}

Mensen die doof of moeilijk te horen zijn, hebben geen of grote moeite om toegang te krijgen tot audio-inhoud. Bijschriften zijn tekstequivalenten voor gesproken en niet-gesproken audio die op het juiste moment tijdens de video op het scherm worden weergegeven. Ze stellen mensen die de audio niet kunnen horen in staat te begrijpen wat er gebeurt.

>[!NOTE]
>
>Bijschriften zijn niet vereist wanneer geschikte tekst of niet-tekstequivalenten (die direct gelijkwaardige informatie verstrekken) beschikbaar zijn op dezelfde pagina als de video of animatie.

#### Hoe kan ik-Bijschriften (vooraf opgenomen) (1.2.2) {#how-to-meet-captions-pre-recorded}

Bijschriften kunnen:

* Openen: altijd zichtbaar wanneer de video wordt afgespeeld)
* Gesloten: de ondertitels kunnen door de gebruiker worden in- of uitgeschakeld

Gebruik waar mogelijk ondertiteling sluiten, omdat gebruikers dan de keuze hebben om ondertitels al dan niet weer te geven.

Voor gesloten bijschriften moet u een gesynchroniseerd bijschriftbestand in een geschikte indeling (zoals [SMIL](https://www.w3.org/AudioVideo/)) naast het videobestand maken en opgeven (details over hoe dit te doen vallen buiten het bereik van deze handleiding, maar we hebben koppelingen naar enkele zelfstudies beschikbaar gesteld onder [Meer informatie - Bijschriften (vooraf opgenomen) (1.2.2)](#more-information-captions-pre-recorded)). Zorg ervoor dat u een notitie opgeeft om gebruikers te laten weten dat er ondertitels beschikbaar zijn voor de video.

Sluit de tekst in de videotrack in als u open bijschriften moet gebruiken. Dit kan worden bereikt met videobewerkingstoepassingen waarmee titels kunnen worden bedekt op de video.

#### Meer informatie - Bijschriften (vooraf opgenomen) (1.2.2) {#more-information-captions-pre-recorded}

* [Werken met succescriteria 1.2.2](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-captions.html):
* [Voldoen aan criteria 1.2.2](https://www.w3.org/WAI/WCAG20/quickref/#media-equiv)
* [W3C: Gesynchroniseerde multimedia](https://www.w3.org/AudioVideo/)
* [Bijschriften, transcripties en audiobeschrijvingen - door WebAIM](https://webaim.org/techniques/captions/)

### Audiobeschrijving of media-alternatief (vooraf opgenomen) (1.2.3) {#audio-description-or-media-alternative-pre-recorded}

* Succescriterium 1.2.3
* Niveau A
* Audiobeschrijving of Media-alternatief (vooraf opgenomen): Voor gesynchroniseerde media wordt een alternatief voor op tijd gebaseerde media of audiobeschrijving van de vooraf opgenomen video-inhoud geboden, behalve wanneer de media een media-alternatief voor tekst zijn en duidelijk als zodanig zijn gelabeld.

#### Doel - Audio-beschrijving of media-alternatief (vooraf opgenomen) (1.2.3) {#purpose-audio-description-or-media-alternative-pre-recorded}

Mensen die blind of visueel gehandicapt zijn, ondervinden toegankelijkheidsbarrières als de informatie in een video of animatie alleen visueel wordt verstrekt, of als de soundtrack niet voldoende informatie biedt om te begrijpen wat er visueel gebeurt.

#### Hoe kan ik-audio-beschrijving of media-alternatief (vooraf opgenomen) (1.2.3) {#how-to-meet-audio-description-or-media-alternative-pre-recorded}

Er zijn twee manieren om aan dit succescriterium te voldoen. Beide zijn acceptabel:

1. Neem een aanvullende audiobeschrijving op voor de video-inhoud. Dit kan op drie manieren worden bereikt:

   * Geef tijdens pauzes in het bestaande dialoogvenster informatie over wijzigingen in de scène die niet worden weergegeven als onderdeel van de bestaande audiotrack.
   * Geef een nieuwe, aanvullende en optionele audiotrack op die de oorspronkelijke soundtrack bevat, maar ook aanvullende audiogegevens over wijzigingen in de scène bevat.

      * Hierdoor kunnen gebruikers schakelen tussen de bestaande audiotrack (die *geen* audiobeschrijving bevat) en de nieuwe audiotrack (die *wel* een audiobeschrijving bevat).
      * Hiermee voorkomt u onderbrekingen voor gebruikers die de aanvullende beschrijving niet nodig hebben.
   * Maak een tweede versie van de video-inhoud voor uitgebreide audiobeschrijvingen. Dit vermindert de moeilijkheden verbonden aan het verstrekken van gedetailleerde audiobeschrijvingen binnen de hiaten tussen bestaande dialoog, door de audio en video op aangewezen punten tijdelijk te pauzeren. Hierdoor kan een veel langere audiobeschrijving worden gegeven voordat de handeling opnieuw wordt gestart. Zoals in het vorige voorbeeld, wordt dit het best verstrekt als facultatieve extra audiospoor om verstoring voor gebruikers te verhinderen die niet de extra beschrijving nodig hebben.


1. Verstrek een tekstranscriptie die een geschikt tekstequivalent van de audio en visuele elementen van de video of de animatie is. In voorkomend geval moet daarin worden vermeld wie het woord voert, een beschrijving van de instelling, mondelinge uitdrukkingen. Afhankelijk van de lengte kunt u de transcriptie op dezelfde pagina plaatsen als de video of animatie, of op een aparte pagina. Als u de laatste optie kiest, geeft u een koppeling op naar de transcriptie naast de video of animatie.

Exacte details over het maken van video met een audiobeschrijving vallen buiten het bereik van deze handleiding. Het maken van video&#39;s en audiobeschrijvingen kan tijdrovend zijn, maar andere Adobe-producten kunnen u helpen deze taken uit te voeren. Als u inhoud maakt in Adobe Flash Professional, moet u ook een script maken waarmee de gebruiker wordt gevraagd de juiste plug-in te downloaden en een alternatief tekstonderdeel via het `<noscript>` element te bieden.

#### Meer informatie - Audio-beschrijving of Media-alternatief (vooraf opgenomen) (1.2.3) {#more-information-audio-description-or-media-alternative-pre-recorded}

* [Werken met succescriteria 1.2.3](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-audio-desc.html):
* [Voldoen aan criteria 1.2.3](https://www.w3.org/WAI/WCAG20/quickref/#qr-media-equiv-audio-desc)
* [Adobe Encore CS5](https://www.adobe.com/products/premiere/encore/)

### Bijschriften (live) (1.2.4)  {#captions-live}

* Succescriterium 1.2.4
* Niveau AA
* Bijschriften (live): Bijschriften worden geleverd voor alle live audio-inhoud in gesynchroniseerde media.

#### Doel - Bijschriften (live) (1.2.4) {#purpose-captions-live}

Dit succescriterium is identiek aan [Bijschriften (pre-Opgenomen)](#captions-pre-recorded) in die zin dat het toegankelijkheidsbarrières aanpakt die mensen die doof of slechthorend zijn ervaren, behalve dat dit succescriterium betrekking heeft op live presentaties zoals webcasts.

#### Hoe kan ik-Bijschriften (live) ontmoeten (1.2.4) {#how-to-meet-captions-live}

Volg de instructies voor [Bijschriften (vooraf opgenomen)](#captions-pre-recorded) hierboven. Gezien de levende aard van de media moet er echter zo snel mogelijk een bijschriftvoorziening worden gecreëerd, als reactie op wat er gebeurt. Daarom zou u het gebruiken van ondertiteling in real time of toespraak-aan-tekst hulpmiddelen moeten overwegen.

Gedetailleerde instructies vallen buiten het bereik van dit document, maar de volgende bronnen bieden nuttige informatie:

* [WebAIM: Real Time Captioning](https://www.webaim.org/techniques/captions/realtime.php)
* [AccessIT (University of Washington): Kunnen de titels automatisch worden geproduceerd gebruikend toespraakerkenning?](https://www.washington.edu/accessit/articles?1209)

#### Meer informatie - Bijschriften (live) (1.2.4) {#more-information-captions-live}

* [Werken met succescriteria 1.2.4](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-real-time-captions.html)
* [Voldoen aan criteria 1.2.4](https://www.w3.org/WAI/WCAG20/quickref/#qr-media-equiv-real-time-captions)

### Audiobeschrijving (vooraf opgenomen) (1.2.5)  {#audio-description-pre-recorded}

* Succescriterium 1.2.5
* Niveau AA
* Audiobeschrijving (vooraf opgenomen): Audiobeschrijving is beschikbaar voor alle vooraf opgenomen video-inhoud in gesynchroniseerde media.

#### Doel - Audiobeschrijving (vooraf opgenomen) (1.2.5) {#purpose-audio-description-pre-recorded}

Dit succescriterium is identiek aan [audiobeschrijving of media-alternatief (vooraf opgenomen)](#audio-description-or-media-alternative-pre-recorded), behalve dat auteurs een veel gedetailleerdere audiobeschrijving moeten geven om te voldoen aan niveau AA.

#### Hoe kan ik-audiobeschrijving (vooraf opgenomen) (1.2.5) {#how-to-meet-audio-description-pre-recorded}

Volg de richtlijnen voor [audiobeschrijving of media-alternatief (vooraf opgenomen)](#audio-description-or-media-alternative-pre-recorded).

#### Meer informatie - Audiobeschrijving (vooraf opgenomen) (1.2.5) {#more-information-audio-description-pre-recorded}

* [Werken met succescriteria 1.2.5](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-audio-desc-only.html)
* [Voldoen aan criteria 1.2.5](https://www.w3.org/WAI/WCAG20/quickref/#qr-media-equiv-audio-desc-only)

### Aanpasbaar (1.3) {#adaptable}

[Richtsnoer 1.3 Aanpasbaar: Maak inhoud die op verschillende manieren kan worden weergegeven (bijvoorbeeld een eenvoudigere indeling) zonder verlies van informatie of structuur.](https://www.w3.org/TR/WCAG20/#content-structure-separation)

Dit richtsnoer heeft betrekking op de vereisten die nodig zijn ter ondersteuning van personen die:

* heeft mogelijk geen toegang tot de informatie die door de auteur wordt gepresenteerd in een *standard *tweedimensionale, gekleurde webpaginalay-out met meerdere kolommen

* U kunt kiezen voor alleen-audio of een andere visuele weergave, zoals grote tekst of een hoog contrast.

### Informatie en relaties (1.3.1)  {#info-and-relationships}

* Succescriterium 1.3.1
* Niveau A
* Informatie en relaties: De informatie, de structuur, en de verhoudingen die door presentatie worden overgebracht kunnen programmatically worden bepaald of zijn beschikbaar in tekst.

#### Doel - Informatie en relaties (1.3.1) {#purpose-info-and-relationships}

Veel ondersteunende technologieën die door mensen met een handicap worden gebruikt, zijn afhankelijk van structurele informatie om inhoud effectief weer te geven of uit te voeren. Deze structuurinformatie kan de vorm aannemen van paginakoppen, tabelrijen, kolomkoppen en lijsttypen. Een schermlezer kan een gebruiker bijvoorbeeld in staat stellen van kop naar kop door een pagina te navigeren. Wanneer pagina-inhoud echter alleen structuur lijkt te hebben via visuele opmaak in plaats van de onderliggende HTML, is er geen structurele informatie beschikbaar voor ondersteunende hulpmiddelen, waardoor deze minder geschikt zijn om eenvoudiger te kunnen bladeren.

Dit succescriterium bestaat om ervoor te zorgen dat dergelijke structurele informatie wordt verstrekt door HTML, zodat browsers en ondersteunende technologieën toegang hebben tot en gebruik kunnen maken van de informatie.

#### Hoe te om te ontmoeten - Informatie en Verband (1.3.1) {#how-to-meet-info-and-relationships}

Met AEM kunt u eenvoudig webpagina&#39;s maken met behulp van de juiste HTML-elementen. Open de pagina-inhoud in de RTE (een tekstcomponent) en gebruik het menu **Indeling** om het juiste structuurelement op te geven (bijvoorbeeld alinea, kop, enz.).

In de volgende afbeelding ziet u tekst die is opgemaakt als alineatekst. uit de broncodeweergave die wordt gebruikt, blijkt dat deze de juiste openings- en sluitingstags &lt;p> en &lt;/p> heeft.

![Een voorbeeld van het element Alinea dat wordt weergegeven in de bronbewerkingsmodus (klassieke UI).](assets/chlimage_1-18a.png)

U kunt ervoor zorgen dat uw webpagina&#39;s de juiste structuur hebben door:

* **Koppen gebruiken:**

   Zolang u de toegankelijkheidsfuncties van de RTE hebt ingeschakeld (zie [AEM en Toegankelijkheid](/help/sites-administering/rte-accessible-content.md)), biedt AEM 3 niveaus aan paginakoppen. U kunt deze gebruiken om secties en subsecties van content te identificeren. Kop 1 is het hoogste niveau van koptekst, kop 3 het laagste. De systeembeheerder kan het systeem configureren om het gebruik van meer kopniveaus toe te staan.

   In de volgende afbeelding ziet u een voorbeeld van de verschillende typen koppen.

   ![Koppen H1 tot en met H3 weergegeven in de keuzelijst (klassieke UI).](assets/chlimage_1-19a.png)

* **Gemarkeerde tekst**:

   Gebruik het element &lt;strong> of &lt;em> om de nadruk aan te geven. Gebruik geen koppen om tekst in alinea&#39;s te markeren.

   * Markeer de tekst die u wilt benadrukken.
   * Click on the **B** icon (for &lt;strong>) or the **I** icon (for &lt;em>) shown within the **Properties** panel (make sure that HTML is selected).
   >[!NOTE]
   >
   >RTE in een standaardAEM installatie is opstelling aan gebruik:
   >
   >* &lt;b> for &lt;strong>
   * &lt;i> voor &lt;em>
   Ze zijn in feite hetzelfde, maar &lt;strong> en &lt;em> hebben de voorkeur omdat ze semantisch correct html zijn. Uw ontwikkelingsteam kan RTE vormen om &lt;strong> en &lt;em> (in plaats van &lt;b> en &lt;i>) te gebruiken wanneer het ontwikkelen van uw projectinstantie.

* **Lijsten gebruiken:** Met HTML kunt u drie verschillende typen lijsten opgeven:

   * The `<ul>` element is used for *unordered* lists (bulleted) lists. Afzonderlijke lijstitems worden geïdentificeerd met behulp van het `<li>` element.

      in RTE, gebruik het **Bulleted pictogram van de Lijst** .

   * The `<ol>` element is used for *numbered* lists. Afzonderlijke lijstitems worden geïdentificeerd met behulp van het `<li>` element.

      In RTE, gebruik het **Genummerde pictogram van de Lijst** .
   Als u bestaande inhoud wilt wijzigen in een specifiek lijsttype, markeert u de desbetreffende tekst en selecteert u het gewenste lijsttype. Zoals in het vorige voorbeeld wordt getoond hoe alineatekst wordt ingegaan, worden de aangewezen lijstelementen automatisch toegevoegd aan uw HTML, maar u kunt dit in bron bekijken uitgeeft mening.

   >[!NOTE]
   `<dl>` wordt niet gesteund door RTE.

* **Tabellen** gebruiken:

   Gegevenstabellen moeten worden geïdentificeerd met behulp van HTML-tabelelementen:

   * één `<table>` element
   * een `<tr>` element voor elke rij van de tabel
   * een `<th>` element voor elke rij- en kolomkop
   * een `<td>` element voor elke gegevenscel
   >[!NOTE]
   Tabellen moeten worden gerealiseerd met de **component Tabel** . Hoewel tabellen kunnen worden gemaakt in de component Text, wordt dit niet aanbevolen.

   Daarnaast maken toegankelijke tabellen gebruik van de volgende elementen en kenmerken:

   * Het `<caption>` element wordt gebruikt om een zichtbaar bijschrift voor de tabel te verstrekken. Bijschriften worden standaard gecentreerd boven de tabel weergegeven, maar kunnen op de juiste wijze worden geplaatst met CSS. Het bijschrift is via programmacode gekoppeld aan de tabel en is daarom een handige methode om inhoud te introduceren.
   * Het `<h3 class="summary">` element helpt niet-waargenomen gebruikers om de informatie gemakkelijker te begrijpen die binnen een lijst wordt voorgesteld, door een synopsis van te verstrekken wat een waargenomen gebruiker kan zien. Dit is met name handig wanneer complexe of onconventionele tabellay-outs worden gebruikt (dit kenmerk wordt niet weergegeven in de browser, het wordt alleen voorgelezen naar ondersteunende hulpmiddelen).
   * Het `scope` kenmerk van het `<th>` element wordt gebruikt om aan te geven of een cel een koptekst voor een bepaalde rij of voor een bepaalde kolom vertegenwoordigt. Een vergelijkbare aanpak is het gebruik van de kenmerken header en id in complexe tabellen, waarbij gegevenscellen aan een of meer kopteksten kunnen worden gekoppeld.
   >[!NOTE]
   Deze elementen en kenmerken zijn standaard niet rechtstreeks beschikbaar, maar de systeembeheerder kan wel ondersteuning voor deze waarden toevoegen in het dialoogvenster **Tabeleigenschappen**[ (zie Ondersteuning voor aanvullende HTML-elementen en -kenmerken toevoegen](/help/sites-administering/rte-accessible-content.md#add-support-for-more-html-elements-and-attributes)).

   Wanneer u een **tabel** toevoegt, kunt u **Tabeleigenschappen** configureren in het dialoogvenster.

   * een geschikt **bijschrift**.
   * U kunt het beste standaardwaarden voor **Breedte**, **Hoogte**, **Rand**, **Celopvulling** en **Celafstand** verwijderen aangezien deze eigenschappen in een globaal opmaakmodel kunnen worden ingesteld.
   ![Dialoogvenster Tabeleigenschappen.](assets/chlimage_1-20a.png)

   Vervolgens kunt u met de eigenschappen **** Cel bepalen of de cel een gegevens- of kopcel is en, in het geval van een kopcel, of de cel betrekking heeft op een rij, kolom of beide:

   ![Dialoogvenster Eigenschappen van aanroep; het plaatsen van een rij (gewoonlijk eerste) als kopbalrij.](assets/chlimage_1-21a.png)

* **Complexe gegevenstabellen:**

   In sommige gevallen, waar er complexe lijsten met twee of meer niveaus van kopballen zijn, dan kunnen de basiseigenschappen van de Lijst niet genoeg zijn om alle noodzakelijke structurele informatie te verstrekken. Voor dit soort complexe tabellen moeten er directe relaties worden gemaakt tussen de koppen en de bijbehorende cellen met behulp van de kenmerken **header** en **id**. In de onderstaande tabel worden de koppen en id&#39;s bijvoorbeeld aangepast om een programmatische koppeling te maken voor gebruikers van ondersteunende technologie.

   >[!NOTE]
   Het kenmerk id is niet beschikbaar in een installatie buiten de box. Het kan worden toegelaten door de regels van HTML en serializer in RTE te vormen.

   >[!NOTE]
   Tabellen moeten worden gerealiseerd met de **component Tabel** . Hoewel tabellen kunnen worden gemaakt in de component Text, wordt dit niet aanbevolen.

   ```xml
   <table>
      <tr>
        <th rowspan="2" id="h">Homework</th>
        <th colspan="3" id="e">Exams</th>
        <th colspan="3" id="p">Projects</th>
      </tr>
      <tr>
        <th id="e1" headers="e">1</th>
        <th id="e2" headers="e">2</th>
        <th id="ef" headers="e">Final</th>
        <th id="p1" headers="p">1</th>
        <th id="p2" headers="p">2</th>
        <th id="pf" headers="p">Final</th>
      </tr>
      <tr>
       <td headers="h">15%</td>
       <td headers="e e1">15%</td>
       <td headers="e e2">15%</td>
       <td headers="e ef">20%</td>
       <td headers="p p1">10%</td>
       <td headers="p p2">10%</td>
       <td headers="p pf">15%</td>
      </tr>
     </table>
   ```

   Om dit in AEM te bereiken moet u de prijsverhoging direct toevoegen gebruikend de bron uitgeeft wijze.

   >[!NOTE]
   Deze functionaliteit is niet onmiddellijk beschikbaar in een standaardinstallatie. Hiervoor is configuratie van de RTE vereist; HTML-regels en serienummering.

#### Meer informatie - Informatie en relaties (1.3.1) {#more-information-info-and-relationships}

* [Werken met succescriteria 1.3.1](https://www.w3.org/TR/UNDERSTANDING-WCAG20/content-structure-separation-programmatic.html)
* [Voldoen aan criteria 1.3.1](https://www.w3.org/WAI/WCAG20/quickref/#qr-content-structure-separation-programmatic)

### Sensorische kenmerken (1.3.3)  {#sensory-characteristics}

* Correctie 1.3.3
* Niveau A
* Sensorische kenmerken: Instructies voor het begrijpen en gebruiken van inhoud zijn niet uitsluitend gebaseerd op sensorische kenmerken van componenten zoals vorm, grootte, visuele locatie, oriëntatie of geluid.

#### Doel - Sensorische kenmerken (1.3.3) {#purpose-sensory-characteristics}

Ontwerpers richten zich vaak op visuele ontwerpfuncties, zoals kleur, vorm, tekststijl of de absolute of relatieve positie van een stuk inhoud wanneer ze informatie presenteren. Dit kunnen zeer krachtige ontwerptechnieken zijn voor het overbrengen van informatie, maar blinden of slechtzienden hebben mogelijk geen toegang tot informatie die visuele identificatie van kenmerken zoals positie, kleur of vorm vereist.

Ook informatie die onderscheid moet maken tussen verschillende geluiden (bv. mannelijke of vrouwelijke gesproken inhoud) zal toegankelijkheidsbelemmeringen voor mensen met gehoorstoornissen opleveren, als deze informatie niet wordt weerspiegeld in een tekstalternatief voor de audio-inhoud.

>[!NOTE]
Raadpleeg [Kleurgebruik](#use-of-color)voor vereisten met betrekking tot alternatieven voor kleuren.

#### Voldoen aan sensorische kenmerken (1.3.3) {#how-to-meet-sensory-characteristics}

Zorg ervoor dat alle informatie die afhankelijk is van visuele kenmerken van pagina-inhoud, ook in een andere indeling wordt weergegeven.

* Vertrouw niet op de visuele positie om informatie te geven. Als u bijvoorbeeld gebruikers naar een menu aan de rechterkant van de pagina wilt verwijzen voor toegang tot meer informatie, verwijst u niet naar *het menu aan de rechterkant*. Geef in plaats daarvan het menu een naam (bijvoorbeeld via een kop) en verwijs naar die naam in de tekst.
* Vertrouw niet op tekstopmaak (bijvoorbeeld vette of cursieve tekst) als enige manier om informatie over te brengen.

>[!NOTE]
Het gebruik van beschrijvende termen is acceptabel als ze in een niet-visuele context betekenis hebben. Het gebruik van *boven* en *onder* bijvoorbeeld is over het algemeen aanvaardbaar, aangezien het inhoud vóór en na een bepaald inhoudsitem betreft. dit zou nog steeds zinvol zijn wanneer de inhoud hardop wordt gehoord .

#### Meer informatie - Sensorische kenmerken (1.3.3) {#more-information-sensory-characteristics}

* [Werken met succescriteria 1.3.3](https://www.w3.org/TR/UNDERSTANDING-WCAG20/content-structure-separation-understanding.html)
* [Voldoen aan criteria 1.3.3](https://www.w3.org/WAI/WCAG20/quickref/#qr-content-structure-separation-understanding)

### Doorneembaar (1.4) {#distinguishable}

[Richtsnoer 1.4. Te onderscheiden: Het is voor gebruikers gemakkelijker om inhoud te zien en te horen, inclusief het scheiden van voorgrond en achtergrond.](https://www.w3.org/TR/WCAG20/#visual-audio-contrast)

### Gebruik van kleur (1.4.1)  {#use-of-color}

* Succescriterium 1.4.1
* Niveau A
* Gebruik van kleur: Kleur wordt niet gebruikt als de enige visuele manier om informatie over te brengen, een handeling aan te geven, een reactie te vragen of een visueel element te onderscheiden.

>[!NOTE]
Dit succescriterium richt zich specifiek op kleurwaarneming. Andere vormen van waarneming vallen onder [Aanpasbaar (1.3)](#adaptable); inclusief programmatische toegang tot kleur en andere codering van de visuele presentatie.

#### Doel - Gebruik van kleur (1.4.1) {#purpose-use-of-color}

Kleur is een duidelijk effectieve manier om de esthetische aantrekkingskracht van webpagina&#39;s te vergroten en is ook handig voor het doorgeven van informatie. Er is echter een reeks visuele beperkingen, van blindheid tot kleurstoornissen, waardoor sommige mensen geen onderscheid kunnen maken tussen bepaalde kleuren. Hierdoor wordt kleurcodering een onbetrouwbare manier om informatie te verschaffen.

Zo kan bijvoorbeeld iemand met een rode-groene kleur een gebrek aan gezichtsvermogen hebben om onderscheid te maken tussen groene tinten en rode tinten. Beide kleuren worden mogelijk als een derde kleur (bijvoorbeeld bruin) weergegeven, waardoor ze geen onderscheid kunnen maken tussen rood, groen en bruin.

Bovendien kan kleur niet worden waargenomen door mensen die alleen tekst weergeven, monochrome weergaveapparaten of een zwart-witafdruk van de pagina gebruiken.

#### Voldoen aan - gebruik van kleur (1.4.1) {#how-to-meet-use-of-color}

Telkens wanneer kleur wordt gebruikt om informatie over te brengen, zorg ervoor dat de informatie beschikbaar is zonder de behoefte om de kleur te zien.

Zorg er bijvoorbeeld voor dat informatie die door kleur wordt verschaft, ook expliciet in tekst wordt vermeld. In de onderstaande afbeelding ziet u hoe kleur en tekst beide de beschikbaarheid van zitplaatsen voor een bepaalde prestatie aangeven:

<table>
 <tbody>
  <tr>
   <td><p><strong>Prestaties</strong></p> </td>
   <td><p><strong>Beschikbaarheid</strong></p> </td>
  </tr>
  <tr>
   <td><p>Dinsdag 16<sup>maart</sup></p> </td>
   <td><p>BESCHIKBARE ZITPLAATSEN</p> </td>
  </tr>
  <tr>
   <td><p>Woensdag 17 maart</p> </td>
   <td><p>BESCHIKBARE ZITPLAATSEN</p> </td>
  </tr>
  <tr>
   <td><p>Donderdag 18<sup>maart</sup></p> </td>
   <td><p>VERKOCHT</p> </td>
  </tr>
 </tbody>
</table>

Als kleur wordt gebruikt als actiepunt voor het verschaffen van informatie, moet u een extra visuele aanwijzing opgeven, zoals het wijzigen van de stijl (bijvoorbeeld vet, cursief) of het lettertype. Dit helpt mensen met een laag gezichtsvermogen of die een kleurgezichtsgebrek hebben om de informatie te identificeren. Er kan echter niet volledig op worden vertrouwd, omdat het mensen die de pagina helemaal niet kunnen zien, niet helpt.

#### Meer informatie - Gebruik van kleur (1.4.1) {#more-information-use-of-color}

* [Werken met succescriteria 1.4.1](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/working-examples/G183/link-contrast.html)
* [Voldoen aan criteria 1.4.1](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/working-examples/G183/link-contrast.html)
* [Richtlijnen voor het bereiken van een contrastverhouding van 3:1, met een lijst &quot;webveilige&quot; kleuren](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/working-examples/G183/link-contrast.html)

### Contrast (minimaal) (1.4.3) {#contrast-minimum}

* Succescriterium 1.4.3
* Niveau AA
* Contrast (minimaal): De visuele presentatie van tekst en afbeeldingen van tekst heeft een contrastverhouding van ten minste 4,5:1, behalve voor de volgende:

   * Grote tekst: Op grote schaal uitgevoerde tekst en afbeeldingen van grote tekst hebben een contrastverhouding van ten minste 3:1.
   * Incidental: Voor tekst of afbeeldingen van tekst die deel uitmaken van een niet-actieve gebruikersinterfacecomponent, die puur decoratie zijn, die voor niemand zichtbaar zijn of die deel uitmaken van een afbeelding die belangrijke andere visuele inhoud bevat, is geen contrast vereist.
   * Logotypes: Voor tekst die deel uitmaakt van een logo of merknaam is geen minimaal contrast vereist.

#### Doel - Contrast (minimaal) (1.4.3) {#purpose-contrast-minimum}

Mensen met een bepaalde visuele handicap kunnen mogelijk geen onderscheid maken tussen bepaalde kleurenparen met een laag contrast. Toegankelijkheidsproblemen kunnen optreden bij deze personen als:

* De tekst contrasteert slecht met de achtergrondkleur.
* De kleurcodering van tekst (zoals koppelingstekst en niet-koppelingstekst) is belangrijk voor het maken van onderscheid tussen gegevens.

>[!NOTE]
Tekst die uitsluitend voor decoratiedoeleinden wordt gebruikt, valt niet onder dit succescriterium.

#### Hoe moet ik voldoen - Contrast (minimaal) (1.4.3) {#how-to-meet-contrast-minimum}

Zorg ervoor dat de tekst voldoende contrasteert met de achtergrond. Contrastverhoudingen zijn afhankelijk van de grootte en de stijl van de desbetreffende tekst:

* Voor tekst met een grootte kleiner dan 18 punten (of 14 punten vet) moet de contrastverhouding tussen tekst/afbeeldingen van tekst en de achtergrond ten minste 4,5:1 zijn.
* Voor tekst die minimaal 18 punten (of 14 punten vet) groot is, moet de contrastverhouding ten minste 3:1 zijn.
* Als een achtergrond een patroon krijgt, moet de achtergrond rondom elke tekst worden gearceerd, zodat de verhouding van 4,5:1 of 3:1 behouden blijft.

Als u contrastverhoudingen wilt controleren, gebruikt u een gereedschap voor kleurcontrast, zoals de [Paciello Group Color Contrast Analyser](https://www.paciellogroup.com/resources/contrast-analyser.html) of de [WebAIM-kleurcontrastcontrole](https://www.webaim.org/resources/contrastchecker/). Met deze gereedschappen kunt u kleurenparen controleren en contrastproblemen melden.

Als u zich minder zorgen maakt over het opgeven van de vormgeving van de pagina, kunt u er ook voor kiezen geen kleur voor de achtergrond en de voorgrondtekst op te geven. Er is geen controle op het contrast nodig, omdat de browser van de gebruiker de kleuren van de tekst en de achtergrond bepaalt.

Als het niet mogelijk is om aan de aanbevolen contrastniveaus te voldoen, moet u een koppeling naar een alternatieve, equivalente versie van de pagina (die geen problemen met het kleurcontrast heeft) opgeven of moet u de gebruiker toestaan het contrast van het kleurenschema aan te passen aan zijn eigen vereisten.

#### Meer informatie - Contrast (minimaal) (1.4.3) {#more-information-contrast-minimum}

* [Werken met succescriteria 1.4.3](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-contrast.html)
* [Voldoen aan criteria 1.4.3](https://www.w3.org/WAI/WCAG20/quickref/#qr-visual-audio-contrast-contrast)

### Afbeeldingen van tekst (1.4.5) {#images-of-text}

* Succescriterium 1.4.5
* Niveau AA
* Afbeeldingen van tekst: Als de gebruikte technologieën de visuele presentatie kunnen bereiken, wordt de tekst gebruikt om informatie eerder dan beelden van tekst over te brengen behalve het volgende:

   * Aanpasbaar: De afbeelding van tekst kan visueel worden aangepast aan de wensen van de gebruiker.
   * Essentieel: Een bepaalde presentatie van de tekst is van essentieel belang voor de informatie die wordt doorgegeven.

>[!NOTE]
Logotypen (tekst die deel uitmaakt van een logo of merknaam) worden als essentieel beschouwd.

#### Doel - Afbeeldingen van tekst (1.4.5) {#purpose-images-of-text}

Afbeeldingen van tekst worden vaak gebruikt wanneer een bepaalde tekststijl de voorkeur heeft; bijvoorbeeld een logo of tekst die uit een andere bron is gegenereerd (bijvoorbeeld een scan van een papieren document). In vergelijking met tekst in HTML en opgemaakt met CSS beschikken afbeeldingen van tekst echter niet over de flexibiliteit om de grootte of weergave te wijzigen die nodig kan zijn voor mensen met een visuele handicap of leesproblemen.

#### Procedure - Afbeeldingen van tekst (1.4.5) {#how-to-meet-images-of-text}

Als afbeeldingen van tekst moeten worden gebruikt, gebruikt u CSS om de afbeeldingen van tekst te vervangen door equivalente tekst in HTML, zodat de tekst op een aanpasbare manier beschikbaar is. Zie [C30 voor een voorbeeld van hoe dit kan worden bereikt: CSS gebruiken om tekst te vervangen door afbeeldingen van tekst en besturingselementen voor de gebruikersinterface bieden om te schakelen](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/C30).

#### Meer informatie - Afbeeldingen van tekst (1.4.5) {#more-information-images-of-text}

* [Werken met succescriteria 1.4.5](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-text-presentation.html)
* [Voldoen aan criteria 1.4.5](https://www.w3.org/WAI/WCAG20/quickref/#qr-visual-audio-contrast-text-presentation)

## Beginsel 2: Werkbaar {#principle-operable}

[Beginsel 2: - De gebruikersinterfacecomponenten en de navigatie moeten kunnen worden bediend.](https://www.w3.org/TR/WCAG20/#operable)

### Pauzeren, stoppen en verbergen (2.2.2)  {#pause-stop-hide}

* Succescriterium 2.2.2
* Niveau A
* Pauze, Stoppen, Verbergen: Voor het verplaatsen, knipperen, schuiven of automatisch bijwerken van gegevens geldt het volgende:

   * Verplaatsen, knipperen, schuiven: Voor elke bewegende, knipperende of schuivende informatie die a) automatisch begint, b) langer dan vijf seconden duurt en c) parallel met andere inhoud wordt weergegeven, is er een mechanisme waarmee de gebruiker deze kan onderbreken, stoppen of verbergen, tenzij de beweging, het knipperen of schuiven deel uitmaakt van een activiteit waar dit essentieel is;
   * Automatisch bijwerken: Voor alle automatisch bij te werken informatie die a) automatisch wordt gestart en b) parallel met andere inhoud wordt weergegeven, is er een mechanisme waarmee de gebruiker deze kan onderbreken, stoppen of verbergen of de frequentie van de update kan bepalen, tenzij de automatisch bij te werken informatie deel uitmaakt van een activiteit waar dit essentieel is.

Opmerkingen zijn:

1. Raadpleeg &#39;Inhoud [niet ontwerpen op een manier waarvan bekend is dat ze aanvallen veroorzaakt&#39; (2.3)](#seizures)voor vereisten met betrekking tot het flikkeren of knipperen van inhoud.
1. Aangezien inhoud die niet aan dit succescriterium voldoet, de mogelijkheid van een gebruiker om de hele pagina te gebruiken kan beïnvloeden, moet alle inhoud op de webpagina (ongeacht of deze wordt gebruikt om aan andere succescriteria te voldoen of niet) aan dit succescriterium voldoen. Zie [Conformiteitsvereiste 5: Geen interferentie](https://www.w3.org/TR/WCAG20/#cc5).
1. Inhoud die regelmatig door software wordt bijgewerkt of naar de gebruikersagent wordt gestreamd, is niet verplicht informatie te bewaren of te presenteren die wordt gegenereerd of ontvangen tussen het begin van de pauze- en de hervattingspresentatie, aangezien dit technisch mogelijk is en in veel situaties misleidend kan zijn om dit te doen.
1. Een animatie die optreedt als onderdeel van een voorlaadfase of een vergelijkbare situatie, kan als essentieel worden beschouwd als er tijdens die fase geen interactie kan optreden voor alle gebruikers en als de voortgang niet wordt aangegeven, gebruikers in verwarring kan brengen of kan leiden tot het vermoeden dat de inhoud is bevroren of gebroken.

#### Doel - Pauzeren, Stoppen, Verbergen (2.2.2) {#purpose-pause-stop-hide}

Bepaalde gebruikers kunnen vinden dat de inhoud die wordt verplaatst, afleidt en het moeilijk maakt zich op andere delen van de pagina te concentreren. Bovendien kan dergelijke inhoud moeilijk leesbaar zijn voor mensen die moeite hebben met het bijhouden van bewegende tekst.

#### Ontmoeten - Pauzeren, Stoppen, Verbergen (2.2.2) {#how-to-meet-pause-stop-hide}

Afhankelijk van de aard van de inhoud kunt u een of meer van de volgende suggesties toepassen bij het maken van webpagina&#39;s met bewegende, knipperende of knipperende inhoud:

* Biedt een manier om schuivende inhoud te pauzeren zodat gebruikers voldoende tijd hebben om deze te lezen. Bijvoorbeeld nieuwstickers of automatisch bijgewerkte tekst.
* Zorg ervoor dat de inhoud die knippert na vijf seconden stopt met knipperen.
* Gebruik de juiste technologieën om knipperende inhoud weer te geven die door de browser kan worden uitgeschakeld. Bijvoorbeeld GIF- (Graphics Interchange Format) of APNG-bestanden (Animated Portable Network Graphics).
* Geef een formulierbesturingselement op de webpagina zodat de gebruiker alle knipperende inhoud op de pagina kan uitschakelen.
* Als een van de bovenstaande opties niet mogelijk is, geeft u een koppeling op naar een pagina die alle inhoud bevat, maar zonder knippering.

#### Meer informatie - Pauzeren, Stoppen, Verbergen (2.2.2) {#more-information-pause-stop-hide}

* [Succescriterium 2.2.2](https://www.w3.org/TR/UNDERSTANDING-WCAG20/time-limits-pause.html)
* [Voldoen aan criterium 2.2.2](https://www.w3.org/WAI/WCAG20/quickref/#qr-time-limits-pause)

### Convulsies (2.3) {#seizures}

[Richtsnoer 2.3 Convulsies: Ontwerp de inhoud niet op een manier waarvan bekend is dat deze aanvallen veroorzaakt.](https://www.w3.org/TR/WCAG20/#seizure)

### Drie instanties of onder de drempelwaarde (2.3.1) {#three-flashes-or-below-threshold}

* Succescriterium 2.3.1
* Niveau A
* Drie instanties of onder de drempelwaarde: Webpagina&#39;s bevatten niets dat meer dan drie keer knippert in een periode van één seconde, of de flits is onder de algemene flash- en rode flitsdrempels.

>[!NOTE]
Aangezien inhoud die niet aan dit succescriterium voldoet, de mogelijkheid van een gebruiker om de hele pagina te gebruiken kan beïnvloeden, moet alle inhoud op de webpagina (ongeacht of deze wordt gebruikt om aan andere succescriteria te voldoen of niet) aan dit succescriterium voldoen. Zie [Conformiteitsvereiste 5: Geen interferentie](https://www.w3.org/TR/WCAG20/#cc5).

#### Doel - Drie instanties van Flash of onder de drempelwaarde (2.3.1) {#purpose-three-flashes-or-below-threshold}

In bepaalde gevallen kan knipperende inhoud fotosensitieve aanvallen veroorzaken. Aan de hand van dit succescriterium kunnen dergelijke gebruikers toegang krijgen tot alle inhoud en deze beleven zonder zich zorgen te maken over knipperende inhoud.

#### Hoe te om te ontmoeten - Drie Vlamjes of onder Drempel (2.3.1) {#how-to-meet-three-flashes-or-below-threshold}

Ga als volgt te werk om ervoor te zorgen dat de volgende technieken worden toegepast:

* ervoor zorgen dat de onderdelen gedurende een periode van één seconde niet meer dan drie keer knipperen;
* Als niet aan de bovenstaande voorwaarde kan worden voldaan, kunt u knipperende inhoud binnen een *klein veilig gebied* in pixels op het scherm weergeven. Dit areaal wordt berekend aan de hand van een complexe formule die onder [G176 valt: Het knipperende gebied klein genoeg](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/G176)houden, zodat dient deze techniek alleen te worden gevolgd als knipperende inhoud *absoluut* noodzakelijk is.

#### Meer informatie - Drie instanties of onder de drempelwaarde (2.3.1) {#more-information-three-flashes-or-below-threshold}

* [Werken met succescriterium 2.3.1](https://www.w3.org/TR/UNDERSTANDING-WCAG20/seizure-does-not-violate.html)
* [Voldoen aan criterium 2.3.1](https://www.w3.org/WAI/WCAG20/quickref/#seizure)

### Getitelde pagina (2.4.2)  {#page-titled}

* Correctie 2.4.2
* Niveau A
* Getitelde pagina: Webpagina&#39;s hebben titels die onderwerp of doel beschrijven.

#### Doel - Getitelde pagina (2.4.2) {#purpose-page-titled}

Met dit succescriterium kan iedereen, ongeacht een bepaalde handicap, de inhoud van een webpagina snel identificeren zonder de pagina volledig te lezen. Dit is vooral handig wanneer meerdere webpagina&#39;s worden geopend op de tabbladen van de browser, omdat de paginatitel op het tabblad wordt weergegeven en deze daarom snel kan worden gevonden.

#### Hoe kan ik-pagina getiteld (2.4.2) {#how-to-meet-page-titled}

Wanneer in AEM een nieuwe HTML-pagina wordt gemaakt, kunt u de paginatitel opgeven. Zorg ervoor dat de titel de inhoud van de pagina adequaat beschrijft, zodat bezoekers snel kunnen vaststellen of de inhoud al dan niet relevant is voor hun behoeften.

You can also edit the page title when editing a page, which is accessible by **Sidekick** - **Page** tab - **Page Properties...**

#### Meer informatie - Getitelde pagina (2.4.2) {#more-information-page-titled}

* [Succescriterium 2.4.2](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-title.html)
* [Voldoen aan criterium 2.2.2](https://www.w3.org/WAI/WCAG20/quickref/#qr-navigation-mechanisms-title)

### Koppelingsdoel (in context) (2.4.4)  {#link-purpose-in-context}

* Correctie 2.4.4
* Niveau A
* Koppelingsdoel (in context): Het doel van elke koppeling kan worden bepaald op basis van alleen de koppelingstekst of van de koppelingstekst samen met de programmatisch bepaalde koppelingscontext, behalve wanneer het doel van de koppeling dubbelzinnig zou zijn voor gebruikers in het algemeen.

#### Doel - Koppelingsdoel (in context) (2.4.4) {#purpose-link-purpose-in-context}

Voor alle gebruikers, ongeacht de handicap, is het van essentieel belang dat duidelijk de richting van een koppeling wordt aangegeven door middel van de juiste koppelingstekst. Hierdoor kunnen gebruikers beter beslissen of ze een koppeling willen volgen of niet. Voor waargenomen gebruikers is betekenisvolle koppelingstekst uiterst nuttig wanneer er meerdere koppelingen op een pagina staan (met name als de pagina tekstoptig is), omdat betekenisvolle koppelingstekst een duidelijkere indicatie geeft van de functionaliteit van de doelpagina. Terwijl gebruikers van ondersteunende hulpmiddelen, die een lijst van alle verbindingen op één enkele pagina kunnen produceren, gemakkelijker de verbindingstekst uit context kunnen begrijpen.

#### Hoe te om te ontmoeten - verbind Doel (in context) (2.4.4) {#how-to-meet-link-purpose-in-context}

Zorg er vooral voor dat het doel van een koppeling duidelijk wordt beschreven in de tekst van de koppeling.

* Onjuist voorbeeld:

   * Tekst: Klik hier voor meer informatie over onze avondlessen voor het najaar van 2010.
   * Reden: de bestemming ervan wordt niet duidelijk en ondubbelzinnig aangegeven.

* Goed voorbeeld:

   * Tekst: Gebeurtenisklassen voor het najaar van 2010 - details.
   * Reden: Door de tekst en de positie van het koppelingselement enigszins aan te passen, kan de koppelingstekst worden verbeterd:

Koppelingen moeten op alle pagina&#39;s consistent worden gephrasd, met name voor navigatiebalken. Als een koppeling naar een specifieke pagina bijvoorbeeld op één pagina de naam **Publicaties** heeft, gebruikt u die tekst op andere pagina&#39;s om de consistentie te garanderen.

Op het moment van schrijven zijn er echter enkele problemen met betrekking tot het gebruik van titels:

* Tekst in het titelkenmerk is doorgaans alleen beschikbaar voor muisgebruikers als pop-upvenster met knopinfo en kan niet worden geopend met het toetsenbord.
* Schermlezers kunnen titelkenmerken lezen, maar deze functionaliteit is mogelijk niet standaard ingeschakeld. gebruikers zijn zich mogelijk niet bewust van het bestaan van een titelkenmerk.
* Het is moeilijk om de weergave van de titeltekst te wijzigen, wat betekent dat het moeilijk of onmogelijk kan zijn om door sommige mensen te lezen.

Dus terwijl het titelkenmerk kan worden gebruikt om extra context aan een koppeling te bieden, dient u zich bewust te zijn van de beperkingen ervan en deze niet te gebruiken als alternatief voor de juiste koppelingstekst.

Als de koppeling bestaat uit een afbeelding, controleert u of de alternatieve tekst voor de afbeelding de bestemming van de koppeling beschrijft. Als een afbeelding van een boekenkast bijvoorbeeld is ingesteld als een koppeling naar de publicaties van een persoon, moet de alternatieve tekst de publicaties **van** John Smith lezen en niet de **boekenkast**.

Als het koppelingsanker echter tekst bevat die het doel van de koppeling naast het afbeeldingselement beschrijft (en de tekst dus naast de afbeelding verschijnt), gebruikt u een leeg alt-kenmerk voor de afbeelding:

```xml
<a href="publications.html">
<img src = "bookshelf.jpg" alt = "" />
John Smith’s publications
</a>
```

>[!NOTE]
Het bovenstaande fragment is een illustratie. Het wordt aangeraden de **component Afbeelding** te gebruiken.

Hoewel het raadzaam is om koppelingstekst te verschaffen die het doel van de koppeling aangeeft zonder dat u een extra context nodig hebt, wordt erkend dat dit niet altijd mogelijk is. Contextvrije koppelingen kunnen in de volgende gevallen worden gebruikt, waarvan HTML-voorbeelden te vinden zijn in [Hoe kan ik voldoen aan criterium 2.4.4](https://www.w3.org/WAI/WCAG20/quickref/#qr-navigation-mechanisms-refs).

* Waar de koppelingstekst deel uitmaakt van een lijst met nauw verwante koppelingen en wanneer het lijstitem dat de koppeling omsluit voldoende context biedt.
* Wanneer het doel van een koppeling duidelijk kan worden bepaald aan de hand van de *voorgaande* (niet de volgende) alineatekst.
* Indien de koppeling zich in een gegevenstabel bevindt, kan het doel duidelijk worden aangegeven in de desbetreffende rubrieken.
* Wanneer een lijst met koppelingen zich in een reeks koppen bevindt en de kop zelf een geschikte context biedt.
* Wanneer een lijst met koppelingen zich in een geneste koppeling bevindt en het bovenliggende lijstitem boven de geneste koppeling een geschikte context biedt.

In sommige gevallen, waar er verscheidene verbindingen op een pagina zijn (elk die de richting van een verbinding in complexe, maar noodzakelijke detail verstrekt), kan het aangewezen zijn om een alternatieve versie van de Web-pagina te verstrekken die de nauwkeurige zelfde inhoud toont maar waar de verbindingstekst niet zo gedetailleerd is.

U kunt ook scripts gebruiken, zodat er een minimale hoeveelheid tekst wordt opgegeven in de koppeling zelf. Als u echter een geschikt besturingselement activeert dat zich boven aan de pagina bevindt, wordt de koppelingstekst *uitgebreid* tot meer details. Een vergelijkbare aanpak is het gebruik van CSS om de volledige koppeling voor waargenomen gebruikers te *verbergen* , maar deze toch volledig uit te voeren naar schermlezers. Dit valt buiten het toepassingsgebied van dit document, maar meer informatie over hoe dit kan worden bereikt is te vinden in de sectie [Meer informatie - Koppelingsdoel (In context) (2.4.4)](#more-information-link-purpose-in-context) .

#### Meer informatie - Koppelingsdoel (in context) (2.4.4) {#more-information-link-purpose-in-context}

* [Succescriterium 2.4.4](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-refs.html)
* [Voldoen aan criterium 2.4.4](https://www.w3.org/WAI/WCAG20/quickref/#qr-navigation-mechanisms-refs)
* [C7: CSS gebruiken om een gedeelte van de koppelingstekst te verbergen](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/C7)

## Beginsel 3: Begrijpelijk {#principle-understandable}

[Beginsel 3: Begrijpelijk - Informatie en de werking van gebruikersinterface moeten begrijpelijk zijn.](https://www.w3.org/TR/WCAG20/#understandable)

### Tekstinhoud leesbaar en begrijpelijk maken (3.1) {#make-text-content-readable-and-understandable}

[Richtsnoer 3.1 Leesbaar: Maak tekstinhoud leesbaar en begrijpelijk.](https://www.w3.org/TR/WCAG20/#meaning)

### Taal van pagina (3.1.1) {#language-of-page}

* Succescriterium 3.1.1
* Niveau A
* Taal van pagina: De standaard menselijke taal van elke Web-pagina kan programmatically worden bepaald.

#### Doel - Taal van pagina (3.1.1) {#purpose-language-of-page}

Het doel van dit succescriterium is ervoor te zorgen dat tekst en andere taalkundige inhoud correct worden weergegeven. Voor gebruikers van schermlezers zorgt dit ervoor dat de inhoud correct wordt uitgedruct, terwijl visuele browsers eerder bepaalde tekensets correct zullen weergeven.

#### Hoe kan ik-taal van pagina (3.1.1) {#how-to-meet-language-of-page}

Om aan dit succescriterium te voldoen, kan de standaardtaal van een Web-pagina worden geïdentificeerd gebruikend het `lang` attribuut binnen het `<html>` element bij de bovenkant van de pagina. Bijvoorbeeld:

* Als een pagina in het Brits Engels is geschreven, moet het `<html>` element als volgt worden gelezen:

   `<html lang = “en-gb”>`

* Overwegende dat een pagina die als Amerikaans Engels moet worden weergegeven, de volgende norm moet aannemen:

   `<html lang = “en-us”>`

In AEM wordt de standaardtaal van uw pagina ingesteld bij het maken van de pagina, maar kan deze ook worden gewijzigd bij het bewerken van een pagina. Deze kan worden geopend via **Sidekick** - tabblad **Pagina** - **Pagina-eigenschappen** - tabblad **Geavanceerd**.

#### Meer informatie - Taal van pagina (3.1.1) {#more-information-language-of-page}

* [Werken met succescriterium 3.1.1](https://www.w3.org/TR/UNDERSTANDING-WCAG20/meaning-doc-lang-id.html)
* [Voldoen aan criterium 3.1.1](https://www.w3.org/WAI/WCAG20/quickref/#qr-meaning-doc-lang-id)
* De codes zijn gebaseerd op ISO 639-1. Een uitgebreidere lijst met codes voor elke taal is te vinden op de [W3-website](https://www.w3schools.com/tags/ref_language_codes.asp).

### Taal van onderdelen (3.1.2)  {#language-of-parts}

* Succescriterium 3.1.2
* Niveau AA
* Taal van onderdelen: De menselijke taal van elke passage of uitdrukking in de inhoud kan programmatisch worden bepaald behalve juiste namen, technische termijnen, woorden van onbepaalde taal, en woorden of uitdrukkingen die deel van het woordenboek van de onmiddellijk omringende tekst zijn geworden.

#### Doel - Taal van onderdelen (3.1.2) {#purpose-language-of-parts}

Het doel van dit succescriterium lijkt op dat van het succescriterium [Taal van pagina](#language-of-page), behalve dat het van toepassing is op webpagina&#39;s die inhoud bevatten in meerdere talen op één pagina (bijvoorbeeld vanwege noteringen of ongebruikelijke leenwoorden).

Pagina&#39;s die dit succescriterium toepassen, maken het mogelijk:

* Braille-overgangssoftware voor het invoegen van tekens met accenten.
* Schermlezers spreken de woorden uit die zich niet correct in de standaardtaal bevinden.
* Met vertaalprogramma&#39;s zoals Google Translate kunt u inhoud van de ene taal naar de andere vertalen.

#### Hoe te om te ontmoeten - Taal van Delen (3.1.2) {#how-to-meet-language-of-parts}

Het `lang` kenmerk kan worden gebruikt om wijzigingen in de taal van de inhoud te identificeren. Een citaat in het Duits (ISO 639-1 code &quot;de&quot;) kan bijvoorbeeld als volgt worden weergegeven:

```xml
<blockquote cite = "John F. Kennedy" lang = "de">
     <p>Ich bin ein Berliner</p>
 </blockquote>
```

>[!NOTE]
Blockquotes worden niet ondersteund in een out-of-the-box-instantie. Een aangepaste component kan worden ontwikkeld ter ondersteuning van de functie.

Op dezelfde manier kan browser een ongewoon woord of een woordgroep correct teruggeven als het `span` element als volgt wordt gebruikt:

```xml
<p>The only French phrase I know is <span lang = “fr”>je ne sais quoi</span>.</p>
```

>[!NOTE]
Dit succescriterium hoeft niet te worden gevolgd wanneer namen of steden in verschillende talen worden opgenomen of wanneer leningswoorden of zinnen worden gebruikt die in de standaardtaal gangbaar zijn geworden (zoals *overlijden* in het Engels).

Als u het span-element met een geschikte taal wilt toevoegen, kunt u de HTML-markering handmatig bewerken in de bronbewerkingsmodus van de RTE, zodat deze als hierboven wordt gelezen. Alternatief kan het `lang` attribuut in RTE door een systeembeheerder worden omvat (zie het [Toevoegen van Steun voor Extra Elementen en Attributen](/help/sites-administering/rte-accessible-content.md#add-support-for-more-html-elements-and-attributes)van HTML).

#### Meer informatie - Taal van onderdelen (3.1.2) {#more-information-language-of-parts}

* [Werken met succescriterium 3.1.2](https://www.w3.org/TR/UNDERSTANDING-WCAG20/meaning-other-lang-id.html)
* [Voldoen aan criterium 3.1.2](https://www.w3.org/WAI/WCAG20/quickref/#qr-meaning-other-lang-id)

### Gebruikers helpen fouten te voorkomen en te corrigeren (3.3) {#help-users-avoid-and-correct-mistakes}

[Richtsnoer 3.3 Invoerbijstand: Gebruikers helpen fouten te voorkomen en te corrigeren.](https://www.w3.org/TR/WCAG20/#minimize-error)

### Labels of instructies (3.3.2) {#labels-or-instructions}

* Succescriterium 3.3.2
* Niveau A
* Labels of instructies: Labels of instructies worden gegeven wanneer de inhoud gebruikersinvoer vereist.

#### Doel - Labels of instructies (3.3.2) {#purpose-labels-or-instructions}

Het geven van instructies om mensen te helpen vormen in te vullen is een fundamenteel onderdeel van goede praktijken in interfacebruikbaarheid. Dit is vooral handig voor mensen met een visuele of cognitieve handicap die anders moeite zouden hebben om de indeling van een formulier en het soort gegevens dat in een bepaald formulierveld moet worden verstrekt, te begrijpen.

In AEM wordt een standaardlabel toegevoegd wanneer u een formuliercomponent, zoals een **tekstveld**, aan de pagina toevoegt. Deze standaardtitel is afhankelijk van het type component. U kunt uw eigen titel toevoegen op het tabblad **Titel en Tekst** van het dialoogvenster Bewerken voor dat veld. Het is belangrijk dat labels gebruikers helpen de gegevens te begrijpen die aan elke formuliercomponent zijn gekoppeld.

![Tabblad Titel en Tekst (dialoogvenster Bewerken); de titel &quot;Beschrijving&quot; is toegevoegd.](assets/chlimage_1-22a.png)

Dit veld **Titel** moet worden gebruikt voor veldelementen omdat het een label bevat dat beschikbaar is voor ondersteunende hulpmiddelen. Alleen het schrijven van een label in tekst naast het veld is niet voldoende.

Voor sommige formuliercomponenten is het ook mogelijk om labels visueel te verbergen met het selectievakje **Titel verbergen**. Labels die op deze manier zijn verborgen, zijn nog steeds beschikbaar voor ondersteunende technologie, maar worden niet op het scherm weergegeven. Hoewel dit in sommige situaties een goede aanpak kan zijn, is het doorgaans het beste om waar mogelijk een visueel label op te nemen, omdat sommige gebruikers wellicht een zeer klein gedeelte van het scherm bekijken (één veld tegelijk) en de labels nodig hebben om het veld correct te identificeren.

#### Afbeeldingsknoppen {#image-buttons}

Wanneer afbeeldingsknoppen worden gebruikt (bijvoorbeeld de component **Afbeeldingsknop**), bevat het veld **Titel** op het tabblad **Titel en tekst** van het dialoogvenster Bewerken in feite de alternatieve tekst voor de afbeelding in plaats van het label. In het onderstaande voorbeeld heeft de afbeelding met de tekst `Submit` dus alternatieve tekst van `Submit`, toegevoegd met het veld **Titel** in het dialoogvenster Bewerken.

![Afbeeldingsknop met Alt-tekst ingesteld in het veld Titel (dialoogvenster Bewerken).](assets/chlimage_1-23a.png)

#### Groepen formuliervelden {#groups-of-form-fields}

Als er een groep gerelateerde besturingselementen is, zoals **Keuzegroep**, kan een titel nodig zijn voor de groep en voor afzonderlijke besturingselementen. Wanneer u een set keuzerondjes toevoegt in AEM, wordt in het veld **Titel** deze groepstitel weergegeven, terwijl afzonderlijke titels worden opgegeven wanneer de keuzerondjes (**Items**) worden gemaakt.

![Items toevoegen aan de groep keuzerondjes. De groepstitel is &#39;Contact me door&#39; - bepaald op het gebied van de Titel.](assets/chlimage_1-24a.png)

Er is echter geen programmatische koppeling tussen de groepstitel en de keuzerondjes zelf. Sjablooneditors moeten de titel in de benodigde `fieldset`- en `legend`-tags plaatsen om deze koppeling te maken. Dit kan alleen door de broncode van de pagina te bewerken. Een systeembeheerder kan ook ondersteuning voor deze elementen toevoegen, zodat deze worden weergegeven in het dialoogvenster **Veldeigenschappen**[ (zie Ondersteuning voor aanvullende HTML-elementen en -kenmerken toevoegen](/help/sites-administering/rte-accessible-content.md#add-support-for-more-html-elements-and-attributes)).

#### Aanvullende overwegingen voor Forms {#additional-considerations-for-forms}

Als gegevens in een specifieke indeling moeten worden ingevoerd, maakt u dit duidelijk in de labeltekst. Als bijvoorbeeld een datum in de `DD-MM-YYYY` notatie moet worden ingevoerd, geeft u dit specifiek op als onderdeel van het label. Dit betekent dat wanneer gebruikers van schermlezers het veld tegenkomen, het label automatisch wordt aangekondigd, samen met aanvullende informatie over de indeling.

Als invoer voor een formulierveld verplicht is, maakt u dit duidelijk door het vereiste woord als onderdeel van het label te gebruiken. AEM voegt een sterretje toe wanneer een veld vereist is, maar het is ideaal om het woord `required`in het label zelf op te nemen (in het veld **Titel** in het dialoogvenster Bewerken).

![Extra informatie (het vereiste woord) toevoegen aan schermlezers in het veld Titel.](assets/chlimage_1-25a.png)

Het positioneren van labels is ook belangrijk, omdat ze hierdoor geschikte velden kunnen vinden. Dit is van bijzonder belang wanneer de gebruiker met een complexe vorm wordt geconfronteerd. Volg de onderstaande conventie:

* Selectievakjes of keuzerondjes:

   De labels worden direct rechts van het veld geplaatst.

* Alle andere formuliercomponenten (bijvoorbeeld tekstvakken, keuzelijsten met invoervak):

   De labels worden direct boven of direct links van het veld geplaatst.

In eenvoudige formulieren met een zeer beperkte functionaliteit kan een juiste etikettering van een `Submit` knop fungeren als een label voor het aangrenzende veld (bijvoorbeeld `Search`). Dit is handig in situaties waarin het lastig kan zijn om ruimte te zoeken voor de labeltekst.

#### Meer informatie - Labels of instructies (3.3.2) {#more-information-labels-or-instructions}

* [Werken met succescriterium 3.3.2](https://www.w3.org/TR/UNDERSTANDING-WCAG20/minimize-error-cues.html)
* [Voldoen aan criterium 3.3.2](https://www.w3.org/WAI/WCAG20/quickref/#qr-minimize-error-cues)

