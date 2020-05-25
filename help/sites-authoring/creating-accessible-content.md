---
title: Toegankelijke inhoud maken voor Adobe Experience Manager (WCAG 2.1-compatibiliteit)
description: Met AEM kunt u webinhoud toegankelijk maken voor en bruikbaar maken voor personen met een handicap
translation-type: tm+mt
source-git-commit: cb7df7301364eb1ce3a1ca376256d2cd5afcb2c8
workflow-type: tm+mt
source-wordcount: '13956'
ht-degree: 5%

---


# Toegankelijke content maken (WCAG 2.1-compatibiliteit) {#creating-accessible-content-wcag-conformance}

De [Web Content Accessibility Guidelines (WCAG) 2.1](https://www.w3.org/TR/WCAG/), opgesteld door [een werkgroep van het World Wide Wec Consortium](https://www.w3.org/Consortium/activities#Accessibility_Guidelines_Working_Group), bestaan uit een reeks technologische onafhankelijke richtsnoeren en succescriteria om ervoor te zorgen dat webinhoud toegankelijk en bruikbaar is voor personen met een handicap.

Als inleiding geeft het consortium een reeks secties en ondersteunende documenten:

* [Nieuwe functies in WCAG 2.1](https://www.w3.org/TR/WCAG/#new-features-in-wcag-2-1)
* [Voldoen aan WCAG 2.1](https://www.w3.org/WAI/WCAG21/quickref/)
* [WCAG 2.1 begrijpen](https://www.w3.org/WAI/WCAG21/Understanding/)
* [Technieken voor WCAG 2.1](https://www.w3.org/WAI/WCAG21/Techniques/)
* [De WCAG-documenten](https://www.w3.org/WAI/standards-guidelines/wcag/docs/)

Zie ook:
* Our [Quick Guide to WCAG 2.1](/help/managing/qg-wcag.md).
* De rapporten [van de Overeenstemming van de Toegankelijkheid voor de oplossingen](https://www.adobe.com/accessibility/compliance.html)van Adobe.
* [De Rich Text Editor configureren voor het produceren van toegankelijke inhoud](/help/sites-administering/rte-accessible-content.md)

De richtsnoeren worden ingedeeld op basis van drie conformiteitsniveaus: Niveau A (laagste), Niveau AA en Niveau AAA (hoogste). De niveaus worden kort samengevat als volgt gedefinieerd:

* **Niveau A:** Uw site bereikt een minimaal basistoegankelijkheidsniveau. Om aan dit niveau te voldoen moet aan alle slagingscriteria voor Niveau A worden voldaan.
* **Niveau AA:** Dit is een ideaal toegankelijkheidsniveau waarnaar u wilt streven, waarbij uw site een basisniveau van toegankelijkheid bereikt, zodat deze in de meeste situaties toegankelijk is voor de meeste mensen die de meeste technologieën gebruiken. Om aan dit niveau te voldoen moet aan alle slagingscriteria voor Niveau A en Niveau AA worden voldaan.
* **Niveau AAA:** Uw site bereikt een zeer hoog toegankelijkheidsniveau. Om aan dit niveau te voldoen moet aan alle slagingscriteria voor Niveau A, Niveau AA en Niveau AAA worden voldaan.

Wanneer u uw site maakt, moet u het algemene niveau bepalen waaraan u uw site wilt laten voldoen.

In de volgende sectie worden de [lagen van de WCAG 2.1-richtsnoeren](https://www.w3.org/TR/WCAG/#wcag-2-layers-of-guidance) met de bijbehorende succescriteria voor Niveau A- en Niveau AA- [conformiteitsniveaus](https://www.w3.org/TR/WCAG/#conformance-to-wcag-2-1)gepresenteerd.

>[!NOTE]
>
>In dit document gebruiken we:
>
>* De [korte namen voor de WCAG 2.1-richtsnoeren](https://www.w3.org/TR/WCAG/#wcag-2-layers-of-guidance).
>* De [nummering die in de WCAG 2.1-richtsnoeren](https://www.w3.org/TR/WCAG/#numbering-in-wcag-2-1) wordt gebruikt voor kruisverwijzingen naar de WCAG-website.


## Beginsel 1: Perceerbaar {#principle-perceivable}

[Beginsel 1: Mogelijkheid - De informatie en gebruikersinterfacecomponenten moeten aan gebruikers op manieren presenteerbaar zijn zij kunnen waarnemen.](https://www.w3.org/TR/WCAG/#perceivable)

### Alternatieven voor tekst (1.1) {#text-alternatives}

[Richtsnoer 1.1 Tekstalternatieven: Maak tekstalternatieven voor alle niet-tekstuele inhoud, zodat deze kan worden gewijzigd in andere formulieren die u nodig hebt, zoals grote gedrukte tekst, braille, spraak, symbolen of eenvoudigere taal.](https://www.w3.org/TR/WCAG/#text-alternatives)

### Niet-tekstuele inhoud (1.1.1) {#non-text-content}

* Succescriterium 1.1.1
* Niveau A
* Niet-tekstuele inhoud: Alle niet-tekstuele inhoud die aan de gebruiker wordt aangeboden, heeft een tekstalternatief dat het gelijkwaardige doel dient, behalve in de situaties hieronder.

#### Doel - Niet-tekstuele inhoud (1.1.1) {#purpose-non-text-content}

De informatie op een webpagina kan in vele verschillende niet-tekstformaten, zoals beelden, video&#39;s, animaties, grafieken worden verstrekt. Personen die blind zijn of een ernstige visuele handicap hebben, kunnen geen niet-tekstuele inhoud zien, maar hebben wel toegang tot tekstinhoud door deze door een schermlezer te laten lezen of in tactiele vorm te laten weergeven door een brailleweergaveapparaat. Dus door tekstalternatieven voor inhoud in grafische indeling te bieden, kunnen mensen die de grafische inhoud niet kunnen zien, toegang krijgen tot een equivalente versie van de informatie die de inhoud biedt.

Een nuttig extra voordeel is dat tekstopties het mogelijk maken dat niet-tekstuele inhoud wordt geïndexeerd door zoekmachinetechnologie.

#### Ontmoeten - Niet-tekstuele inhoud (1.1.1) {#how-to-meet-non-text-content}

Voor statische afbeeldingen is het basisvereiste dat een equivalent tekstalternatief voor de afbeelding wordt geboden. Dit kan worden gedaan in het veld **Alternatieve tekst** ; Zie bijvoorbeeld de Core Component **[Image](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/components/image.html)**.

>[!NOTE]
>
>Bepaalde Core-componenten buiten de box, zoals **[Carousel](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/components/carousel.html)**, beschikken niet over een veld**Alternatieve tekst **waarmee alternatieve tekstbeschrijvingen aan afzonderlijke afbeeldingen kunnen worden toegevoegd, hoewel het veld**Label **(tabblad**[Toegankelijkheid](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/components/carousel.html#accessibility-tab)** ) voor de gehele component aanwezig is.
>
>Bij het uitvoeren van versies van deze componenten voor uw AEM-exemplaar zal uw ontwikkelingsteam dergelijke componenten moeten configureren om het kenmerk `alt`[ te ondersteunen zodat auteurs dit aan de content kunnen toevoegen (zie Ondersteuning toevoegen voor aanvullende HTML-elementen en -kenmerken](/help/sites-administering/rte-accessible-content.md#adding-support-for-additional-html-elements-and-attributes)).

AEM vereist dat het veld **Alternatieve tekst** standaard wordt ingevuld. Als de afbeelding zuiver decoratief is en alternatieve tekst overbodig is, kan de optie **Afbeelding decoratief** worden gecontroleerd.

#### Alternatieven voor goede tekst maken {#creating-good-text-alternatives}

Er zijn verschillende vormen van niet-tekstuele inhoud, zodat de waarde van het tekstoptie afhankelijk is van de rol die de afbeelding in de webpagina speelt. De volgende algemene regels voor duim zijn van toepassing:

* Alternatieven voor tekst moeten beknopt zijn, maar toch duidelijk aangeven welke essentiële informatie door de niet-tekstuele inhoud wordt verstrekt.
* Te lange beschrijvingen (meer dan 100 tekens) moeten worden vermeden. Als een tekstalternatief meer details vereist:
   * een korte beschrijving geven in de alternatieve tekst
   * en hebben een langere beschrijving in tekst elders op dezelfde pagina of in een aparte webpagina. Koppel deze afzonderlijke beschrijving door van de afbeelding een koppeling te maken of door een tekstkoppeling naast de afbeelding te plaatsen.
* Alternatieve tekst mag geen inhoud repliceren die in tekstvorm dichtbij op dezelfde pagina wordt geleverd. Houd er rekening mee dat veel afbeeldingen illustraties zijn van punten die al in de tekst van een pagina zijn opgenomen, zodat er al een gedetailleerd tekstalternatief bestaat.
* Als de niet-tekstinhoud een koppeling naar een andere pagina of een ander document is en er geen andere tekst deel uitmaakt van dezelfde koppeling, moet de alternatieve tekst voor de afbeelding de bestemming van de koppeling aangeven en niet de afbeelding.
* Als de niet-tekstuele inhoud zich in een knopelement bevindt en er geen tekst bestaat die deel uitmaakt van dezelfde knop, moet de alternatieve tekst van de afbeelding de functionaliteit van de knop aangeven en de afbeelding niet beschrijven.
* Het is perfect acceptabel dat een afbeelding een lege (null) alternatieve tekst krijgt, maar alleen als de afbeelding geen alternatieve tekst nodig heeft (bijvoorbeeld een zuiver decoratieve afbeelding) of als de equivalente tekst al in de paginatekst staat.

<!--
The [W3C draft: HTML5 Techniques for providing useful text alternatives](https://dev.w3.org/html5/alt-techniques/) has more details and examples of appropriate alternative text provision for images of different types.
-->

Specifieke typen niet-tekstuele inhoud waarvoor tekstopties nodig zijn, zijn onder meer:

* Illustratieve foto&#39;s: Dit zijn afbeeldingen van mensen, objecten of plaatsen. Het is belangrijk om over de rol van de foto in de pagina te denken, en over het algemeen te adviseren om de beeldinhoud te beschrijven, aangezien de hulptechnologie het elementtype (bijvoorbeeld, `graphic` of `image`) zal aankondigen; het kan de duidelijkheid vergroten om te gebruiken `screenshot` of `illustration` in alternatieve tekstbeschrijvingen , maar dit hangt af van de context . Consistentie is een belangrijke factor, een besluit zou voor een volledig auteursteam moeten worden genomen en dit was van toepassing door de gebruikerservaring.
* Pictogrammen: Dit zijn kleine pictogrammen (afbeeldingen) die specifieke informatie bevatten. Ze moeten consistent worden gebruikt op een pagina en site. Alle exemplaren van het pictogram op een pagina of site moeten hetzelfde korte en korte tekstalternatief hebben, tenzij dit leidt tot onnodige duplicatie van aangrenzende tekst.
* Grafieken en grafieken: Deze vertegenwoordigen meestal numerieke gegevens. U kunt dus een alternatief voor tekst bieden door een korte samenvatting op te nemen van de belangrijkste trends die in de grafiek of afbeelding worden weergegeven. Geef indien nodig ook een gedetailleerdere beschrijving in de tekst op met behulp van het veld **Beschrijving** op het tabblad **Geavanceerde** afbeeldingseigenschappen. Bovendien kunt u de brongegevens elders op de pagina of site in tabelvorm opgeven.
* Kaarten, diagrammen, stroomdiagrammen: Voor afbeeldingen die ruimtelijke gegevens leveren (bijvoorbeeld om beschrijvende relaties tussen objecten of een proces te ondersteunen), moet u ervoor zorgen dat het sleutelbericht wordt weergegeven in de tekstindeling en dat deze tekstinformatie bij elk gekoppeld gegevenspunt wordt geplaatst. Voor kaarten is het opgeven van een volledige-tekstequivalent waarschijnlijk onpraktisch, maar als de kaart wordt verstrekt als manier om mensen te helpen hun weg naar een bepaalde plaats vinden, dan kan de alternatieve tekst van de afbeelding kort *Kaart van X* aangeven, en vervolgens elders op de pagina of via het veld **Beschrijving** op het tabblad **Geavanceerd** van de component **Afbeelding** een routebeschrijving naar die plaats in tekst opgeven.
* CAPTCHA&#39;s: Een CAPTCHA is een *volledig geautomatiseerde Publieke Turing-test om computers en mensen te informeren*. Het is een veiligheidscontrole die op webpagina&#39;s wordt gebruikt om mensen van kwaadaardige software te onderscheiden, maar die toegankelijkheidsbarrières kan veroorzaken. Dit zijn afbeeldingen waarvoor gebruikers een beschrijving moeten geven van wat ze zien om een beveiligingstest te kunnen doorstaan. Het is duidelijk niet mogelijk om een tekstalternatief voor de afbeelding te bieden, dus in plaats daarvan moet u alternatieve niet-grafische oplossingen overwegen. De W3C biedt een aantal suggesties, zoals:Elk van deze benaderingen heeft zijn eigen verdiensten en nadelen.
   * Logische puzzels
   * Het gebruik van geluidsuitvoer in plaats van afbeeldingen
   * Beperkte gebruikaccounts en spamfilters.
* Achtergrondafbeeldingen: Deze worden bereikt met CSS (Cascading Style Sheets) in plaats van met HTML. Dit betekent dat het niet mogelijk is een alternatieve tekstwaarde op te geven. Achtergrondafbeeldingen mogen daarom geen belangrijke tekstuele informatie opleveren. Als dat wel het geval is, moet deze informatie ook in de paginatekst worden vermeld. Het is echter belangrijk dat een andere achtergrond wordt weergegeven wanneer de afbeelding niet kan worden weergegeven.

>[!NOTE]
>
>Er moet een passend contrastniveau zijn tussen de achtergrond en de voorgrondtekst. dit wordt meer in detail besproken in [Contrast (Minimum) (1.4.3)](#contrast-minimum).

#### Meer informatie - Niet-tekstuele inhoud (1.1.1) {#more-information-non-text-content}

* [Werken met succescriteria 1.1.1](https://www.w3.org/WAI/WCAG21/Understanding/non-text-content.html)
* [Voldoen aan criteria 1.1.1](https://www.w3.org/WAI/WCAG21/quickref/#non-text-content)
* [W3C-uitleg van en alternatieven voor CAPTCHA&#39;s](https://www.w3.org/TR/turingtest/)

<!--
* [W3C: HTML5 Techniques for providing useful text alternatives (draft)](https://dev.w3.org/html5/alt-techniques/)
-->

### Op tijd gebaseerde media (1.2) {#time-based-media}

[Richtsnoer 1.2 Op tijd gebaseerde media: Alternatieven bieden voor tijdgebaseerde media.](https://www.w3.org/TR/WCAG/#time-based-media)

Dit heeft betrekking op webinhoud die op *tijd is gebaseerd*. Dit geldt voor inhoud die de gebruiker kan afspelen (zoals video, audio en geanimeerde inhoud) en die vooraf is opgenomen of een live stream.

### Alleen audio en alleen video (vooraf opgenomen) (1.2.1) {#audio-only-and-video-only-prerecorded}

* Succescriterium 1.2.1
* Niveau A
* Alleen audio en alleen video (vooraf opgenomen): Voor vooraf opgenomen audio-slechts en vooraf opgenomen video-slechts media, zijn het volgende waar, behalve wanneer de audio of de video een media alternatief voor tekst is en duidelijk als dusdanig geëtiketteerd:
   * Alleen vooraf opgenomen audio: Er is een alternatief voor op tijd gebaseerde media beschikbaar met gelijkwaardige informatie voor vooraf opgenomen inhoud met alleen audio.
   * Alleen vooraf opgenomen video: Er is een alternatief voor op tijd gebaseerde media of een audiotrack beschikbaar met gelijkwaardige informatie voor vooraf opgenomen video-inhoud.

#### Doel - Alleen audio en alleen video (vooraf opgenomen) (1.2.1) {#purpose-audio-only-and-video-only-prerecorded}

Toegankelijkheidsproblemen voor video en audio kunnen worden ondervonden door:

* Mensen met een visuele handicap zonder soundtrack of de soundtrack volstaat niet om hen te informeren over wat er in de video of animatie gebeurt;
* personen met een slechthorende werking of doof zijn, die de soundtrack niet kunnen horen;
* Mensen die de soundtrack kunnen horen, maar niet begrijpen wat er wordt gesproken (bijvoorbeeld omdat het in een taal staat die ze niet begrijpen).

Video of audio is mogelijk ook niet beschikbaar voor gebruikers die browsers of apparaten gebruiken die het afspelen van inhoud in bepaalde media-indelingen, zoals Adobe Flash, niet ondersteunen.

Als u deze informatie in een andere indeling verstrekt, zoals tekst (of audio voor video zonder audio), kunt u deze toegankelijk maken voor mensen die geen toegang hebben tot de oorspronkelijke inhoud.

#### Hoe kan ik-alleen-audio en alleen-video (vooraf opgenomen) (1.2.1) {#how-to-meet-audio-only-and-video-only-prerecorded}

* Als de inhoud vooraf opgenomen audio zonder video (zoals een podcast) is:
   * Geef een koppeling voor of na de inhoud op naar een teksttranscriptie van de audio-inhoud. De transcriptie moet een HTML-pagina zijn met een tekstequivalent van alle gesproken en belangrijke niet-gesproken inhoud, plus een indicatie van wie spreekt, een beschrijving van de instelling, spraakexpressies en een beschrijving van andere belangrijke audio.
* Als de inhoud een animatie of vooraf opgenomen video zonder audio is:
   * Een koppeling verschaffen vlak voor of na de inhoud naar een equivalente tekstbeschrijving van de informatie die door de video wordt verschaft
   * Of een equivalente audiobeschrijving in een veelgebruikte audio-indeling, zoals MP3.

>[!NOTE]
>
>Als de audio- of video-inhoud wordt aangeboden als alternatief voor inhoud die al in een andere indeling op dezelfde webpagina bestaat, is mogelijk geen extra alternatief vereist.
>
>De richtsnoeren, [die WCAG 1.2.1](https://www.w3.org/WAI/WCAG21/Understanding/audio-only-and-video-only-prerecorded.html)begrijpen, bevatten nadere informatie.

Het invoegen van multimedia in uw AEM-webpagina&#39;s lijkt op het invoegen van een afbeelding. Aangezien multimedia-inhoud echter veel meer is dan een stilstaand beeld, zijn er verschillende instellingen en opties om te bepalen hoe de multimedia wordt afgespeeld.

>[!NOTE]
>
>Als u multimedia gebruikt met informatieve inhoud, moet u ook koppelingen naar alternatieven maken. Als u bijvoorbeeld een teksttranscriptie wilt opnemen, maakt u een HTML-pagina waarop de transcriptie wordt weergegeven en voegt u vervolgens een koppeling toe naast of onder de audio-inhoud.

#### Meer informatie - alleen audio en alleen video (vooraf opgenomen) (1.2.1) {#more-information-audio-only-and-video-only-prerecorded}

* [Werken met succescriteria 1.2.1](https://www.w3.org/WAI/WCAG21/Understanding/audio-only-and-video-only-prerecorded.html)
* [Voldoen aan criteria 1.2.1](https://www.w3.org/WAI/WCAG21/quickref/#audio-only-and-video-only-prerecorded)

### Bijschriften (vooraf opgenomen) (1.2.2) {#captions-prerecorded}

* Succescriterium 1.2.2
* Niveau A
* Bijschriften (vooraf opgenomen): Er zijn bijschriften beschikbaar voor alle vooraf opgenomen audio-inhoud in gesynchroniseerde media, behalve wanneer de media een media-alternatief voor tekst zijn en duidelijk als zodanig zijn gelabeld.

#### Doel - Bijschriften (vooraf opgenomen) (1.2.2) {#purpose-captions-prerecorded}

Mensen die doof of moeilijk te horen zijn, krijgen geen toegang tot audio-inhoud of hebben er grote moeite mee. Bijschriften zijn tekstequivalenten voor gesproken en niet-gesproken audio die op het juiste moment tijdens de video op het scherm worden weergegeven. Ze stellen mensen die de audio niet kunnen horen in staat te begrijpen wat er gebeurt.

#### Hoe kan ik-Bijschriften (vooraf opgenomen) (1.2.2) {#how-to-meet-captions-prerecorded}

Bijschriften kunnen:

* Openen: altijd zichtbaar wanneer de video wordt afgespeeld
* Gesloten: de ondertitels kunnen door de gebruiker worden in- of uitgeschakeld

Gebruik waar mogelijk ondertiteling sluiten, omdat gebruikers dan de keuze hebben om ondertitels al dan niet weer te geven.

Voor gesloten bijschriften moet u een gesynchroniseerd bijschriftbestand in een geschikte indeling (zoals [SMIL](https://www.w3.org/AudioVideo/)) naast het videobestand maken en opgeven (details over hoe dit te doen vallen buiten het bereik van deze handleiding, maar we hebben koppelingen naar enkele zelfstudies beschikbaar gesteld onder [Meer informatie - Bijschriften (vooraf opgenomen) (1.2.2)](#more-information-captions-prerecorded). Zorg ervoor dat u een notitie opgeeft of schakel de functie Bijschrift in de videospeler in om gebruikers te laten weten dat ondertitels beschikbaar zijn voor de video.

Sluit de tekst in de videotrack in als u open bijschriften moet gebruiken. Dit kan worden bereikt met videobewerkingstoepassingen waarmee titels kunnen worden bedekt op de video.

#### Meer informatie - Bijschriften (vooraf opgenomen) (1.2.2) {#more-information-captions-prerecorded}

* [Werken met succescriteria 1.2.2](https://www.w3.org/WAI/WCAG21/Understanding/captions-prerecorded.html)
* [Voldoen aan criteria 1.2.2](https://www.w3.org/WAI/WCAG21/quickref/#captions-prerecorded)

<!--
* [W3C: Synchronized Multimedia](https://www.w3.org/AudioVideo/)
* [Captions, Transcripts, and Audio Descriptions - by WebAIM](https://webaim.org/techniques/captions/)
-->

### Audiobeschrijving of media-alternatief (vooraf opgenomen) (1.2.3) {#audio-description-or-media-alternative-prerecorded}

* Succescriterium 1.2.3
* Niveau A
* Audiobeschrijving of Media-alternatief (vooraf opgenomen): Voor gesynchroniseerde media wordt een alternatief voor op tijd gebaseerde media of audiobeschrijving van de vooraf opgenomen video-inhoud geboden, behalve wanneer de media een media-alternatief voor tekst zijn en duidelijk als zodanig zijn gelabeld.

#### Doel - Audio-beschrijving of Media-alternatief (vooraf opgenomen) (1.2.3) {#purpose-audio-description-or-media-alternative-prerecorded}

Mensen die blind of visueel gehandicapt zijn, ondervinden toegankelijkheidsbarrières als de informatie in een video of animatie alleen visueel wordt verstrekt, of als de soundtrack niet voldoende informatie biedt om te begrijpen wat er visueel gebeurt.

#### Hoe kan ik-audio-beschrijving of media-alternatief (vooraf opgenomen) (1.2.3) {#how-to-meet-audio-description-or-media-alternative-prerecorded}

Er zijn twee manieren om aan dit succescriterium te voldoen. Beide zijn acceptabel:

1. Neem een aanvullende audiobeschrijving op voor de video-inhoud. Dit kan op drie manieren worden bereikt:
   * Geef tijdens pauzes in het bestaande dialoogvenster informatie over wijzigingen in de scène die niet worden weergegeven als onderdeel van de bestaande audiotrack.
   * Geef een nieuwe, aanvullende en optionele audiotrack met de oorspronkelijke soundtrack op, maar voeg ook extra audiogegevens over wijzigingen in de scène toe.
      * Hierdoor kunnen gebruikers schakelen tussen de bestaande audiotrack (die *geen* audiobeschrijving bevat) en de nieuwe audiotrack (die *wel* een audiobeschrijving bevat).
      * Hiermee voorkomt u onderbrekingen voor gebruikers die de aanvullende beschrijving niet nodig hebben.
   * Maak een tweede versie van de video-inhoud voor uitgebreide audiobeschrijvingen. Dit vermindert de moeilijkheden verbonden aan het verstrekken van gedetailleerde audiobeschrijvingen binnen de hiaten tussen bestaande dialoog, door de audio en video op aangewezen punten tijdelijk te pauzeren. Hierdoor kan een veel langere audiobeschrijving worden gegeven voordat de handeling opnieuw wordt gestart. Zoals in het vorige voorbeeld, wordt dit het best verstrekt als facultatieve extra audiospoor om verstoring voor gebruikers te verhinderen die niet de extra beschrijving nodig hebben.
1. Verstrek een tekstranscriptie die een geschikt tekstequivalent van de audio en visuele elementen van de video of de animatie is. Dit moet, waar van toepassing, een vermelding bevatten over wie spreekt, een beschrijving van de instelling, gebeurtenissen of informatie die visueel worden gepresenteerd, en mondelinge uitdrukkingen. Afhankelijk van de lengte kunt u de transcriptie op dezelfde pagina plaatsen als de video of animatie, of op een aparte pagina. Als u de laatste optie kiest, geeft u een koppeling op naar de transcriptie naast de video of animatie.

Exacte details over het maken van video met een audiobeschrijving vallen buiten het bereik van deze handleiding. Het maken van video&#39;s en audiobeschrijvingen kan tijdrovend zijn, maar andere Adobe-producten kunnen u helpen deze taken uit te voeren.

#### Meer informatie - Audio-beschrijving of Media-alternatief (vooraf opgenomen) (1.2.3) {#more-information-audio-description-or-media-alternative-prerecorded}

* [Werken met succescriteria 1.2.3](https://www.w3.org/WAI/WCAG21/Understanding/audio-description-or-media-alternative-prerecorded.html)
* [Voldoen aan criteria 1.2.3](https://www.w3.org/WAI/WCAG21/quickref/#audio-description-or-media-alternative-prerecorded)

<!--
* [Adobe Encore](https://www.adobe.com/products/encore.html) - a DVD authoring software tool
-->

### Bijschriften (live) (1.2.4)  {#captions-live}

* Succescriterium 1.2.4
* Niveau AA
* Bijschriften (live): Bijschriften worden geleverd voor alle live audio-inhoud in gesynchroniseerde media.

#### Doel - Bijschriften (live) (1.2.4) {#purpose-captions-live}

Dit succescriterium is identiek aan [Bijschriften (vooraf opgenomen)](#captions-prerecorded) in die zin dat het toegankelijkheidsbarrières aanpakt die mensen die doof of slechthorend zijn ervaren, behalve dat dit succescriterium betrekking heeft op live presentaties zoals webcasts.

#### Hoe kan ik-Bijschriften (live) ontmoeten (1.2.4) {#how-to-meet-captions-live}

Volg de instructies voor [Bijschriften (vooraf opgenomen)](#captions-prerecorded) hierboven. Gezien de levende aard van de media moet er echter zo snel mogelijk een bijschriftvoorziening worden gecreëerd, als reactie op wat er gebeurt. Daarom zou u het gebruiken van ondertiteling in real time of toespraak-aan-tekst hulpmiddelen moeten overwegen.

Gedetailleerde instructies vallen buiten het bereik van dit document, maar de volgende bronnen bieden nuttige informatie:

* [WebAIM: Real Time Captioning](https://www.webaim.org/techniques/captions/realtime.php)

* [AccessComputing-project (University of Washington): Kunnen de titels automatisch worden geproduceerd gebruikend toespraakerkenning?](https://www.washington.edu/accesscomputing/can-captions-be-generated-automatically-using-speech-recognition)

#### Meer informatie - Bijschriften (live) (1.2.4) {#more-information-captions-live}

* [Werken met succescriteria 1.2.4](https://www.w3.org/WAI/WCAG21/Understanding/captions-live.html)
* [Voldoen aan criteria 1.2.4](https://www.w3.org/WAI/WCAG21/quickref/#captions-live)

### Audiobeschrijving (vooraf opgenomen) (1.2.5)  {#audio-description-prerecorded}

* Succescriterium 1.2.5
* Niveau AA
* Audiobeschrijving (vooraf opgenomen): Audiobeschrijving is beschikbaar voor alle vooraf opgenomen video-inhoud in gesynchroniseerde media.

#### Doel - Audiobeschrijving (vooraf opgenomen) (1.2.5) {#purpose-audio-description-prerecorded}

Dit succescriterium is identiek aan [Audiobeschrijving of Media-alternatief (vooraf opgenomen)](#audio-description-or-media-alternative-prerecorded), behalve dat auteurs een veel gedetailleerdere audiobeschrijving moeten geven om te voldoen aan niveau AA.

#### Hoe kan ik-audiobeschrijving (vooraf opgenomen) (1.2.5) {#how-to-meet-audio-description-prerecorded}

Volg de richtlijnen voor [audiobeschrijving of media-alternatief (vooraf opgenomen)](#audio-description-or-media-alternative-prerecorded).

#### Meer informatie - Audio-beschrijving (vooraf opgenomen) (1.2.5) {#more-information-audio-description-prerecorded}

* [Werken met succescriteria 1.2.5](https://www.w3.org/WAI/WCAG21/Understanding/audio-description-prerecorded.html)
* [Voldoen aan criteria 1.2.5](https://www.w3.org/WAI/WCAG21/quickref/#audio-description-prerecorded)

### Aanpasbaar (1.3) {#adaptable}

[Richtsnoer 1.3 Aanpasbaar: Maak inhoud die op verschillende manieren kan worden weergegeven (bijvoorbeeld een eenvoudigere indeling) zonder verlies van informatie of structuur.](https://www.w3.org/TR/WCAG/#adaptable)

Dit richtsnoer heeft betrekking op de vereisten die nodig zijn ter ondersteuning van personen die:

* Het is mogelijk dat u geen toegang hebt tot informatie zoals deze door een auteur wordt weergegeven in de standaardpresentatie van die inhoud (bijvoorbeeld een lay-out met meerdere kolommen of een pagina met veel gebruik van kleur en/of afbeeldingen).

* kan alleen-audio of een andere visuele weergave gebruiken, zoals grote tekst of een hoog contrast.

### Informatie en relaties (1.3.1)  {#info-and-relationships}

* Succescriterium 1.3.1
* Niveau A
* Informatie en relaties: De informatie, de structuur, en de verhoudingen die door presentatie worden overgebracht kunnen programmatically worden bepaald of zijn beschikbaar in tekst.

#### Doel - Informatie en relaties (1.3.1) {#purpose-info-and-relationships}

Veel ondersteunende technologieën die door mensen met een handicap worden gebruikt, zijn afhankelijk van structurele informatie om inhoud op effectieve wijze weer te geven of te *begrijpen* . Deze structuurinformatie kan de vorm aannemen van paginakoppen, tabelrijen, kolomkoppen en lijsttypen. Een schermlezer kan een gebruiker bijvoorbeeld in staat stellen van kop naar kop door een pagina te navigeren. Wanneer pagina-inhoud echter alleen structuur lijkt te hebben via visuele opmaak in plaats van de onderliggende HTML, is er geen structurele informatie beschikbaar voor ondersteunende hulpmiddelen, waardoor deze minder geschikt zijn om eenvoudiger te kunnen bladeren.

Dit succescriterium bestaat om ervoor te zorgen dat dergelijke structurele informatie programmatically door HTML, of andere coderingstechnieken wordt verstrekt, zodat browsers en hulptechnologieën tot de informatie kunnen toegang hebben en voordeel kunnen halen.

#### Hoe te om te ontmoeten - Informatie en Verband (1.3.1) {#how-to-meet-info-and-relationships}

Met AEM kunt u eenvoudig semantisch betekenisvolle webinhoud maken met de juiste HTML-elementen. Open de pagina-inhoud in de RTE (een tekstcomponent) en gebruik het menu **Paraformat** (alineasymbool) om het juiste structuurelement op te geven (bijvoorbeeld alinea, kop, enz.).

U kunt ervoor zorgen dat uw webpagina&#39;s de juiste structuur krijgen door, waar van toepassing, de volgende elementen te gebruiken:

* **Koppen:** Zolang u de toegankelijkheidsfuncties van RTE hebt ingeschakeld, biedt AEM 3 niveaus van paginakop aan. U kunt deze gebruiken om secties en subsecties van content te identificeren. Kop 1 is het hoogste niveau van koptekst, kop 3 het laagste. De systeembeheerder kan het systeem configureren om het gebruik van meer kopniveaus toe te staan.

* **Lijsten**: Met HTML kunt u drie verschillende typen lijsten opgeven:
   * Het element `<ul>` wordt gebruikt voor *ongeordende* lijsten (met opsommingstekens). Afzonderlijke lijstitems worden geïdentificeerd met behulp van het element `<li>`. Gebruik in de RTE het pictogram **Lijst met opsommingstekens**.
   * The `<ol>` element is used for *numbered* lists. Afzonderlijke lijstitems worden geïdentificeerd met behulp van het `<li>` element. In RTE, gebruik het **Genummerde pictogram van de Lijst** .
   Als u bestaande inhoud wilt wijzigen in een specifiek lijsttype, markeert u de desbetreffende tekst en selecteert u het gewenste lijsttype. Net als in het vorige voorbeeld waarin wordt getoond hoe alineatekst wordt ingevoerd, worden de desbetreffende lijstelementen automatisch toegevoegd aan de HTML.

   In de volledige-schermmodus zijn de afzonderlijke pictogrammen **Lijst met opsommingstekens** en **Genummerde lijst** zichtbaar. Als de volledige-schermmodus niet is geactiveerd, zijn de twee opties beschikbaar achter het enkele pictogram **Lijsten**.

* **Tabellen**: Gegevenstabellen moeten worden geïdentificeerd met behulp van HTML-tabelelementen:
   * één `<table>` element
   * een `<tr>` element voor elke rij van de tabel
   * een `<th>` element voor elke rij- en kolomkop
   * een `<td>` element voor elke gegevenscel
   Daarnaast maken toegankelijke tabellen gebruik van de volgende elementen en kenmerken:

   * Het `<caption>` element wordt gebruikt om een zichtbaar bijschrift voor de tabel te verstrekken. Bijschriften worden standaard gecentreerd boven de tabel weergegeven, maar kunnen op de juiste wijze worden geplaatst met CSS. Het bijschrift is via programmacode gekoppeld aan de tabel en is daarom een handige methode om inhoud te introduceren.
   * Het `<summary>` element helpt niet-waargenomen gebruikers om de informatie gemakkelijker te begrijpen die binnen een lijst wordt voorgesteld, door een synopsis van te verstrekken wat een waargenomen gebruiker kan zien. Dit is met name handig wanneer complexe of onconventionele tabellay-outs worden gebruikt (dit kenmerk wordt niet weergegeven in de browser, het wordt alleen voorgelezen naar ondersteunende hulpmiddelen).
   * Het `scope` kenmerk van het `<th>` element wordt gebruikt om aan te geven of een cel een koptekst voor een bepaalde rij of voor een bepaalde kolom vertegenwoordigt. Een vergelijkbare aanpak is het gebruik van de kenmerken header en id in complexe tabellen, waarbij gegevenscellen aan een of meer kopteksten kunnen worden gekoppeld.
   >[!NOTE]
   >
   >Deze elementen en kenmerken zijn standaard niet rechtstreeks beschikbaar, maar de systeembeheerder kan wel ondersteuning voor deze waarden toevoegen in het dialoogvenster **Tabeleigenschappen**[ (zie Ondersteuning voor aanvullende HTML-elementen en -kenmerken toevoegen](/help/sites-administering/rte-accessible-content.md#adding-support-for-additional-html-elements-and-attributes).

   U opent het dialoogvenster **Tabel** door het tabblad **Tabeleigenschappen** te selecteren:

   * Geef een geschikt **bijschrift** op.
   * U kunt het beste standaardwaarden voor **Breedte**, **Hoogte**, **Rand**, **Celopvulling** en **Celafstand** verwijderen aangezien deze eigenschappen in een globaal opmaakmodel kunnen worden ingesteld.
   Vervolgens kunt u met de **Celeigenschappen** kiezen of de cel een gegevens- of een kopcel is:

* **Nadruk**: Gebruik het `<strong>` of het `<em>` element om nadruk te wijzen. Gebruik geen koppen om tekst in alinea&#39;s te markeren.
   * Markeer de tekst die u wilt benadrukken.
   * Klik op het pictogram **B** (voor `<strong>`) of het pictogram **I** (voor `<em>`) dat wordt weergegeven in het deelvenster **Eigenschappen** (zorg ervoor dat HTML is geselecteerd).

      >[!NOTE]
      >
      >RTE in een standaardAEM installatie is opstelling aan gebruik:
      >
      >* `<b>` for `<strong>`
      >* `<i>` for `<em>`
      >
      >Ze zijn in feite hetzelfde, maar `<strong>` en `<em>` hebben de voorkeur omdat ze semantisch correct html zijn. Uw ontwikkelingsteam kan RTE vormen om `<strong>` en `<em>` (in plaats van `<b>` en `<i>`) te gebruiken wanneer het ontwikkelen van uw projectinstantie.


* **Complexe datatabellen**: In sommige gevallen, waar er complexe tabellen met twee of meer niveaus van koppen zijn, kunnen de basistabeleigenschappen mogelijk niet voldoende zijn om alle noodzakelijke structurele informatie te verstrekken. Voor dit soort complexe tabellen moeten er directe relaties worden gemaakt tussen de koppen en de bijbehorende cellen met behulp van de kenmerken **header** en **id.**

   >[!NOTE]
   >
   >Het kenmerk id is niet beschikbaar in een installatie buiten de box. Het kan worden toegelaten door de regels van HTML en serializer in RTE te vormen.

   In de onderstaande tabel worden de koppen en id&#39;s bijvoorbeeld aangepast om een programmatische koppeling te maken voor gebruikers van ondersteunende technologie.

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
   >
   >Deze functionaliteit is niet onmiddellijk beschikbaar in een standaardinstallatie. Het vereist configuratie van RTE, de regels van HTML, en serializer.

#### Meer informatie - Informatie en relaties (1.3.1) {#more-information-info-and-relationships}

* [Werken met succescriteria 1.3.1](https://www.w3.org/WAI/WCAG21/Understanding/info-and-relationships.html)
* [Voldoen aan criteria 1.3.1](https://www.w3.org/WAI/WCAG21/quickref/#info-and-relationships)

### Betekenisvolle reeks (1.3.2)  {#meaningful-sequence}

* Succescriterium 1.3.2
* Niveau A
* Betekenisvolle reeks: Wanneer de opeenvolging waarin de inhoud wordt voorgesteld zijn betekenis beïnvloedt, kan een correcte lezingsopeenvolging programmatically worden bepaald.

#### Doel - Betekenisvolle reeks (1.3.2) {#purpose-meaningful-sequence}

Dit succescriterium is bedoeld om een gebruikersagent in staat te stellen een alternatieve presentatie van inhoud te bieden en tegelijkertijd de leesvolgorde te behouden die nodig is om de betekenis te begrijpen. Het is belangrijk dat het mogelijk is om via programmacode minstens één sequentie van de inhoud te bepalen die zinvol is. Inhoud die niet voldoet aan dit criterium voor succes, kan gebruikers verwarren of desoriënteren wanneer ondersteunende hulpmiddelen de inhoud in de verkeerde volgorde lezen of wanneer alternatieve stijlpagina&#39;s of andere opmaakwijzigingen worden toegepast.

#### Hoe te om te ontmoeten - Betekenisvolle Opeenvolging (1.3.2) {#how-to-meet-meaningful-sequence}

Volg de richtlijnen onder [Hoe te om Succes Criteria 1.3.2](https://www.w3.org/WAI/WCAG21/quickref/#meaningful-sequence)te ontmoeten.

#### Meer informatie - Betekenisvolle reeks (1.3.2) {#more-information-meaningful-sequence}

* [Werken met succescriteria 1.3.2](https://www.w3.org/WAI/WCAG21/Understanding/meaningful-sequence.html)
* [Voldoen aan criteria 1.3.2](https://www.w3.org/WAI/WCAG21/quickref/#meaningful-sequence)

### Sensorische kenmerken (1.3.3)  {#sensory-characteristics}

* Succescriterium 1.3.3
* Niveau A
* Sensorische kenmerken: Instructies voor het begrijpen en gebruiken van inhoud zijn niet uitsluitend gebaseerd op sensorische kenmerken van componenten zoals vorm, grootte, visuele locatie, oriëntatie of geluid.

#### Doel - Sensorische kenmerken (1.3.3) {#purpose-sensory-characteristics}

Ontwerpers richten zich vaak op visuele ontwerpfuncties, zoals kleur, vorm, tekststijl of de absolute of relatieve positie van een stuk inhoud wanneer ze informatie presenteren. Dit kunnen zeer krachtige ontwerptechnieken zijn voor het overbrengen van informatie (en kunnen de algemene toegankelijkheid voor waargenomen gebruikers met cognitieve toegankelijkheidsbehoeften verbeteren), maar mensen die blind of visueel gehandicapt zijn kunnen geen toegang hebben tot informatie die visuele identificatie van eigenschappen zoals positie, kleur of vorm vereist.

Ook informatie die onderscheid moet maken tussen verschillende geluiden (bv. mannelijke of vrouwelijke gesproken inhoud) zal toegankelijkheidsbelemmeringen voor mensen met gehoorstoornissen opleveren, als deze informatie niet wordt weerspiegeld in een tekstalternatief voor de audio-inhoud.

>[!NOTE]
>
>Raadpleeg [Kleurgebruik](#use-of-color)voor vereisten met betrekking tot alternatieven voor kleuren.

#### Voldoen aan sensorische kenmerken (1.3.3) {#how-to-meet-sensory-characteristics}

Zorg ervoor dat alle informatie die afhankelijk is van visuele kenmerken van pagina-inhoud, ook in een andere indeling wordt weergegeven.

* Vertrouw niet op de visuele positie om informatie te geven. Als u bijvoorbeeld gebruikers naar een menu aan de rechterkant van de pagina wilt verwijzen voor toegang tot meer informatie, verwijst u niet naar *het menu aan de rechterkant*. Geef in plaats daarvan het menu een naam (bijvoorbeeld via een kop) en verwijs naar die naam in de tekst.
* Vertrouw niet op tekstopmaak (bijvoorbeeld vette of cursieve tekst) als enige manier om informatie over te brengen.

>[!NOTE]
>
>Het gebruik van beschrijvende termen is acceptabel als ze in een niet-visuele context betekenis hebben. Het gebruik van *boven* en *onder* bijvoorbeeld is over het algemeen aanvaardbaar, aangezien het inhoud vóór en na een bepaald inhoudsitem betreft. dit zou nog steeds zinvol zijn wanneer de inhoud hardop wordt gehoord .

#### Meer informatie - Sensorische kenmerken (1.3.3) {#more-information-sensory-characteristics}

* [Werken met succescriteria 1.3.3](https://www.w3.org/WAI/WCAG21/Understanding/sensory-characteristics.html)
* [Voldoen aan criteria 1.3.3](https://www.w3.org/WAI/WCAG21/quickref/#sensory-characteristics)

### Doorneembaar (1.4) {#distinguishable}

[Richtsnoer 1.4. Te onderscheiden: Het is voor gebruikers gemakkelijker om inhoud te zien en te horen, inclusief het scheiden van voorgrond en achtergrond.](https://www.w3.org/TR/WCAG/#distinguishable)

### Gebruik van kleur (1.4.1)  {#use-of-color}

* Succescriterium 1.4.1
* Niveau A
* Gebruik van kleur: Kleur wordt niet gebruikt als de enige visuele manier om informatie over te brengen, een handeling aan te geven, een reactie te vragen of een visueel element te onderscheiden.

>[!NOTE]
>
>Dit succescriterium richt zich specifiek op kleurwaarneming. Andere vormen van waarneming vallen onder [Aanpasbaar (1.3)](#adaptable); inclusief programmatische toegang tot kleur en andere codering van de visuele presentatie.

#### Doel - Gebruik van kleur (1.4.1) {#purpose-use-of-color}

Kleur is een duidelijk effectieve manier om de esthetische aantrekkingskracht van webpagina&#39;s te vergroten en is ook handig voor het doorgeven van informatie. Er is echter een reeks visuele beperkingen, van blindheid tot kleurstoornissen, waardoor sommige mensen geen onderscheid kunnen maken tussen bepaalde kleuren. Hierdoor wordt kleurcodering een onbetrouwbare manier om informatie te verschaffen.

Zo kan bijvoorbeeld iemand met een rode-groene kleur een gebrek aan gezichtsvermogen hebben om onderscheid te maken tussen groene tinten en rode tinten. Beide kleuren worden mogelijk als een derde kleur (bijvoorbeeld bruin) weergegeven, waardoor ze geen onderscheid kunnen maken tussen rood, groen en bruin.

Bovendien kan kleur niet worden waargenomen door mensen die alleen tekst weergeven, monochrome weergaveapparaten of een zwart-witafdruk van de pagina gebruiken.

Een andere overweging is de *geselecteerde* status voor een interface-element (bijvoorbeeld tabbladen, schakelknoppen, enz.), die op een andere manier moet worden overgebracht dan alleen met kleur en niet alleen met een visuele presentatie. Voor dergelijke elementen is het extra gebruik van patronen, vormen en programmatische informatie nuttig bij het creëren van een volledig inclusieve gebruikerservaring die niet op een specifieke zin steunt.

#### Voldoen aan - gebruik van kleur (1.4.1) {#how-to-meet-use-of-color}

Telkens wanneer kleur wordt gebruikt om informatie over te brengen, zorg ervoor dat de informatie beschikbaar is zonder de behoefte om de kleur te zien.

Zorg er bijvoorbeeld voor dat informatie die door kleur wordt verschaft, ook expliciet in tekst wordt vermeld.

Als kleur wordt gebruikt als actiepunt voor het verschaffen van informatie, moet u een extra visuele aanwijzing opgeven, zoals het wijzigen van de stijl (bijvoorbeeld vet, cursief) of het lettertype. Dit helpt mensen met een laag gezichtsvermogen of die een kleurgezichtsgebrek hebben om de informatie te identificeren. Er kan echter niet volledig op worden vertrouwd, omdat het mensen die de pagina helemaal niet kunnen zien, niet helpt. Daarom is het (soms) nuttig om verborgen teksten te verstrekken of programmatic oplossingen, zoals de [Toegankelijke Rich Internet Applications (ARIA) reeks van Webnormen](https://www.w3.org/WAI/standards-guidelines/aria/)te gebruiken, om deze informatie aan niet-waargenomen gebruikers over te brengen.

#### Meer informatie - Gebruik van kleur (1.4.1) {#more-information-use-of-color}

* [Werken met succescriteria 1.4.1](https://www.w3.org/WAI/WCAG21/Understanding/use-of-color.html)
* [Voldoen aan criteria 1.4.1](https://www.w3.org/WAI/WCAG21/quickref/#use-of-color)

### Audiobesturing (1.4.2)  {#audio-control}

* Succescriterium 1.4.2
* Niveau A
* Audiobesturing: Als om het even welke audio op een Web-pagina automatisch meer dan 3 seconden speelt, of is een mechanisme beschikbaar om de audio te pauzeren of tegen te houden, of een mechanisme is beschikbaar om audiovolume onafhankelijk van het algemene niveau van het systeemvolume te controleren.

#### Doel - Audiobesturing (1.4.2) {#purpose-audio-control}

Personen die schermleessoftware gebruiken, kunnen het moeilijk vinden om de spraakuitvoer te horen als er andere audio tegelijkertijd wordt afgespeeld. Deze moeilijkheid wordt verergerd wanneer de de toespraakoutput van de het lezer software gebaseerd is (zoals de meesten vandaag zijn) en door de zelfde volumeregeling zoals het geluid wordt gecontroleerd. Bovendien kunnen sommige mensen met cognitieve handicaps en mensen die neurodivergerend zijn, een goede gevoeligheid hebben. Deze individuen zullen om het even welk onvermogen vinden om het volumeniveau op audio inhoud vrij verstorend te veranderen.

Daarom is het belangrijk dat de gebruiker het achtergrondgeluid kan uitschakelen.

>[!NOTE]
>
>Als u het volume wilt regelen, kunt u het volume tot nul terugbrengen.

#### Ontmoeten - Audiocontrole (1.4.2) {#how-to-meet-audio-control}

Volg de richtlijnen onder [Hoe te om Succes Criteria 1.4.2](https://www.w3.org/WAI/WCAG21/quickref/#audio-control)te ontmoeten.

#### Meer informatie - Audiobesturing (1.4.2) {#more-information-audio-control}

* [Werken met succescriteria 1.4.2](https://www.w3.org/WAI/WCAG21/Understanding/audio-control.html)
* [Voldoen aan criteria 1.4.2](https://www.w3.org/WAI/WCAG21/quickref/#audio-control)

### Contrast (minimaal) (1.4.3) {#contrast-minimum}

* Succescriterium 1.4.3
* Niveau AA
* Contrast (minimaal): De visuele presentatie van tekst en afbeeldingen van tekst heeft een contrastverhouding van ten minste 4,5:1, behalve voor de volgende:
   * Grote tekst: Op grote schaal uitgevoerde tekst en afbeeldingen van grote tekst hebben een contrastverhouding van ten minste 3:1.
   * Incidental: Voor tekst of afbeeldingen van tekst die deel uitmaken van een niet-actieve gebruikersinterfacecomponent, die [zuiver versieren](https://www.w3.org/TR/WCAG/#dfn-pure-decoration)zijn, die voor niemand zichtbaar zijn of die deel uitmaken van een afbeelding die belangrijke andere visuele inhoud bevat, is geen contrast vereist.
   * Logotypes: Voor tekst die deel uitmaakt van een logo of merknaam is geen minimaal contrast vereist.
   >[!NOTE]
   >
   >Zie Contrast [voor niet-tekst](https://www.w3.org/WAI/WCAG21/Understanding/non-text-contrast.html) begrijpen voor meer informatie om ervoor te zorgen dat auteurs van inhoud de extra vereisten rond niet-tekstelementen (met inbegrip van pictogrammen, interface-elementen, onder andere) begrijpen.

#### Doel - Contrast (minimaal) (1.4.3) {#purpose-contrast-minimum}

Mensen met een bepaalde visuele handicap kunnen mogelijk geen onderscheid maken tussen bepaalde kleurenparen met een laag contrast. Toegankelijkheidsproblemen kunnen optreden bij deze personen als:

* De tekst contrasteert slecht met de achtergrondkleur.
* De kleurcodering van tekst (zoals koppelingstekst en niet-koppelingstekst) is belangrijk voor het maken van onderscheid tussen gegevens.

>[!NOTE]
>
>Tekst die uitsluitend voor decoratiedoeleinden wordt gebruikt, valt niet onder dit succescriterium.

#### Hoe moet ik voldoen - Contrast (minimaal) (1.4.3) {#how-to-meet-contrast-minimum}

Zorg ervoor dat de tekst voldoende contrasteert met de achtergrond. Contrastverhoudingen zijn afhankelijk van de grootte en de stijl van de desbetreffende tekst:

* Voor tekst met een grootte kleiner dan 18 punten (of 14 punten vet) moet de contrastverhouding tussen tekst/afbeeldingen van tekst en de achtergrond ten minste 4,5:1 zijn.
* Voor tekst die minimaal 18 punten (of 14 punten vet) groot is, moet de contrastverhouding ten minste 3:1 zijn.
* Als een achtergrond een patroon krijgt, moet de achtergrond rondom elke tekst worden gearceerd, zodat de verhouding van 4,5:1 of 3:1 behouden blijft.

>[!NOTE]
>
>Vergeet niet dat lettertypen kunnen verschillen in de manier waarop ze de equivalente PT/PX/EM-grootte weergeven.
>
>U wordt aangeraden goed te beoordelen en fouten te maken aan de kant van leesbaarheid en bruikbaarheid wanneer u de juiste lettertypen en grootten voor webinhoud selecteert.

>[!NOTE]
>
>De volgende sites kunnen u helpen bij conversies naar andere eenheden:
>
>* [Px naar Em-calculator - Universeel](https://www.omnicalculator.com/conversion/px-to-em)
>* [Omzetting lettergrootte: pixel-point-em-rem-percent](https://websemantics.uk/tools/font-size-conversion-pixel-point-em-rem-percent/)
>* [PMtoEM.com: Eenvoudige omzetting van PX naar EM](http://pxtoem.com)


Als u contrastverhoudingen wilt controleren, gebruikt u een gereedschap voor kleurcontrast, zoals de [Paciello Group Color Contrast Analyser](https://www.paciellogroup.com/resources/contrast-analyser.html) of de [WebAIM-kleurcontrastcontrole](https://www.webaim.org/resources/contrastchecker/). Met deze gereedschappen kunt u kleurenparen controleren en contrastproblemen melden.

Als u zich minder zorgen maakt over het opgeven van de vormgeving van de pagina, kunt u er ook voor kiezen geen kleur voor de achtergrond en de voorgrondtekst op te geven. Er is geen controle op het contrast nodig, omdat de browser van de gebruiker de kleuren van de tekst en de achtergrond bepaalt.

Als het niet mogelijk is om aan de aanbevolen contrastniveaus te voldoen, moet u een koppeling naar een alternatieve, equivalente versie van de pagina (die geen problemen met het kleurcontrast heeft) opgeven of moet u de gebruiker toestaan het contrast van het kleurenschema aan te passen aan zijn eigen vereisten.

#### Meer informatie - Contrast (minimaal) (1.4.3) {#more-information-contrast-minimum}

* [Werken met succescriteria 1.4.3](https://www.w3.org/WAI/WCAG21/Understanding/contrast-minimum.html)
* [Voldoen aan criteria 1.4.3](https://www.w3.org/WAI/WCAG21/quickref/#contrast-minimum)

### Tekst vergroten/verkleinen (1.4.4)  {#resize-text}

* Succescriterium 1.4.4
* Niveau A
* Tekst vergroten/verkleinen: Met uitzondering van bijschriften en afbeeldingen van tekst, kan de grootte van tekst zonder hulpprogramma tot 200 procent worden aangepast zonder verlies van inhoud of functionaliteit.

#### Doel - Tekst vergroten/verkleinen (1.4.4) {#purpose-resize-text}

Het doel van dit succescriterium is ervoor te zorgen dat visueel weergegeven tekst, inclusief op tekst gebaseerde besturingselementen (teksttekens die zijn weergegeven zodat ze kunnen worden gezien [versus teksttekens die nog steeds in gegevensvorm zijn zoals ASCII]), met succes kan worden geschaald, zodat deze rechtstreeks kan worden gelezen door mensen met een lichte visuele handicap, zonder dat het gebruik van ondersteunende hulpmiddelen, zoals een schermvergroting, vereist is. De gebruikers kunnen van het schrapen van al inhoud op de Web-pagina profiteren, maar de tekst is het meest kritiek.

#### Procedure - Formaat tekst wijzigen (1.4.4) {#how-to-meet-resize-text}

Naast het volgen van de richtlijnen onder [Hoe te om Criteria 1.4.4](https://www.w3.org/WAI/WCAG21/quickref/#resize-text) van het Succes te ontmoeten kunt u inhoudsauteurs aanmoedigen om dynamische, flexibele breedten en hoogten in hun paginaontwerpen en doopvontgrootte (bijvoorbeeld, Responsief Web Design) te gebruiken om lezers de capaciteit toe te staan om tekst te resize.

#### Meer informatie - Tekst vergroten/verkleinen (1.4.4) {#more-information-resize-text}

* [Werken met succescriteria 1.4.4](https://www.w3.org/WAI/WCAG21/Understanding/resize-text.html)
* [Voldoen aan criteria 1.4.4](https://www.w3.org/WAI/WCAG21/quickref/#resize-text)

### Afbeeldingen van tekst (1.4.5) {#images-of-text}

* Succescriterium 1.4.5
* Niveau AA
* Afbeeldingen van tekst: Als de gebruikte technologieën de visuele presentatie kunnen bereiken, wordt de tekst gebruikt om informatie eerder dan beelden van tekst over te brengen behalve het volgende:
   * Aanpasbaar: De afbeelding van tekst kan visueel worden aangepast aan de wensen van de gebruiker.
   * Essentieel: Een bepaalde presentatie van de tekst is van essentieel belang voor de informatie die wordt doorgegeven.

>[!NOTE]
>
>Logotypen (tekst die deel uitmaakt van een logo of merknaam) worden als essentieel beschouwd.

#### Doel - Afbeeldingen van tekst (1.4.5) {#purpose-images-of-text}

Afbeeldingen van tekst worden vaak gebruikt wanneer een bepaalde tekststijl de voorkeur heeft; bijvoorbeeld een logo of tekst die uit een andere bron is gegenereerd (bijvoorbeeld een scan van een papieren document). In vergelijking met tekst in HTML en opgemaakt met CSS beschikken afbeeldingen van tekst echter niet over de flexibiliteit om de grootte of weergave te wijzigen die nodig kan zijn voor mensen met een visuele handicap of leesproblemen.

#### Procedure - Afbeeldingen van tekst (1.4.5) {#how-to-meet-images-of-text}

Als afbeeldingen van tekst moeten worden gebruikt, gebruikt u CSS om de afbeeldingen van tekst te vervangen door equivalente tekst in HTML, zodat de tekst op een aanpasbare manier beschikbaar is. Zie [C30 voor een voorbeeld van hoe dit kan worden bereikt: CSS gebruiken om tekst te vervangen door afbeeldingen van tekst en besturingselementen voor de gebruikersinterface bieden om te schakelen](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/C30).

#### Meer informatie - Afbeeldingen van tekst (1.4.5) {#more-information-images-of-text}

* [Werken met succescriteria 1.4.5](https://www.w3.org/WAI/WCAG21/Understanding/images-of-text.html)
* [Voldoen aan criteria 1.4.5](https://www.w3.org/WAI/WCAG21/quickref/#images-of-text)

## Beginsel 2: Werkbaar {#principle-operable}

[Beginsel 2: - De gebruikersinterfacecomponenten en de navigatie moeten kunnen worden bediend.](https://www.w3.org/TR/WCAG/#operable)

### Toegankelijk toetsenbord (2.1) {#keyboard-accessible}

[Richtsnoer 2.1 Toegankelijk toetsenbord: Alle functionaliteit beschikbaar stellen via een toetsenbord.](https://www.w3.org/TR/WCAG/#keyboard-accessible)

Hierbij wordt ervoor gezorgd dat gebruikers toegang hebben tot alle functionaliteit met een toetsenbord.

### Toetsenbord (2.1.1)  {#keyboard}

* Succescriterium 2.1.1
* Niveau A
* Toetsenbord: Alle functionaliteit van de inhoud kan worden uitgevoerd via een toetsenbordinterface zonder specifieke tijdinstellingen voor afzonderlijke toetsaanslagen te vereisen, behalve wanneer de onderliggende functie invoer vereist die afhankelijk is van het pad van de beweging van de gebruiker en niet alleen van de eindpunten.

#### Doel - Toetsenbord (2.1.1) {#purpose-keyboard}

Het doel van dit succescriterium is ervoor te zorgen dat inhoud waar mogelijk kan worden gebruikt via een toetsenbord- of toetsenbordinterface (zodat een alternatief toetsenbord kan worden gebruikt). Wanneer de inhoud door een toetsenbord of afwisselend toetsenbord kan worden in werking gesteld, is het operabel door mensen zonder zicht (die geen apparaten zoals muizen kunnen gebruiken die oogcoördinatie vereisen) evenals door mensen die afwisselende toetsenborden of inputapparaten moeten gebruiken die als toetsenbordmededingers dienst doen. Toetsenbordemulators zijn onder andere spraakinvoersoftware, software voor sip-and-puff, toetsenborden op het scherm, scansoftware en diverse ondersteunende hulpmiddelen en alternatieve toetsenborden. Personen met een visuele handicap kunnen problemen ondervinden bij het bijhouden van een aanwijzer en het gebruik van software veel gemakkelijker (of alleen mogelijk) vinden als ze deze via het toetsenbord kunnen besturen.

#### Ontmoeten - Toetsenbord (2.1.1) {#how-to-meet-keyboard}

Volg de richtlijnen onder [Hoe te om Criteria 2.1.1](https://www.w3.org/WAI/WCAG21/quickref/#keyboard)van het Succes te ontmoeten.

#### Meer informatie - Toetsenbord (2.1.1) {#more-information-keyboard}

* [Werken met succescriteria 2.1.1](https://www.w3.org/WAI/WCAG21/Understanding/no-keyboard-trap.html)
* [Voldoen aan criteria 2.1.1](https://www.w3.org/WAI/WCAG21/quickref/#keyboard)

### Geen toetsenbordovervulling (2.1.2)  {#no-keyboard-trap}

* Succescriterium 2.1.2
* Niveau A
* Geen toetsenbordovervulling: Als toetsenbordfocus naar een component van de pagina kan worden verplaatst met behulp van een toetsenbordinterface, dan kan de focus van die component worden verwijderd met behulp van alleen een toetsenbordinterface. Als hiervoor meer dan ongewijzigde pijltoetsen of tabtoetsen of andere standaardafsluitmethoden nodig zijn, wordt de gebruiker gewezen op de methode om de focus weg te verplaatsen.

#### Doel - Geen toetsenbordovervulling (2.1.2) {#purpose-no-keyboard-trap}

Dit succescriterium is bedoeld om ervoor te zorgen dat die inhoud geen toetsenbordfocus *overvult* binnen subsecties van inhoud op een webpagina. Dit is een veelvoorkomend probleem wanneer meerdere indelingen op een pagina worden gecombineerd en met insteekmodules of ingesloten toepassingen worden gerenderd.

Het kan voorkomen dat de functionaliteit van de webpagina de focus beperkt tot een subsectie van de inhoud (bijvoorbeeld een modaal dialoogvenster). In dergelijke gevallen moet u een methode opgeven waarmee een gebruiker die subsectie van inhoud kan verlaten (met de ESC-toets wordt bijvoorbeeld het modale dialoogvenster gesloten of met de knop Sluiten sluit u het modale dialoogvenster).

#### Ontmoeten - Geen toetsenbordovervulling (2.1.2) {#how-to-meet-no-keyboard-trap}

Volg de richtlijnen onder [Hoe te om Succes Criteria 2.1.2](https://www.w3.org/WAI/WCAG21/quickref/#no-keyboard-trap)te ontmoeten.

#### Meer informatie - Geen toetsenbordovervulling (2.1.2) {#more-information-no-keyboard-trap}

* [Werken met succescriteria 2.1.2](https://www.w3.org/WAI/WCAG21/Understanding/no-keyboard-trap.html)
* [Voldoen aan criteria 2.1.2](https://www.w3.org/WAI/WCAG21/quickref/#no-keyboard-trap)

### Voldoende tijd (2.2) {#enough-time}

[Richtsnoer 2.2 Voldoende tijd: Geef gebruikers voldoende tijd om inhoud te lezen en te gebruiken.](https://www.w3.org/TR/WCAG/#enough-time)

Hierbij wordt ervoor gezorgd dat gebruikers voldoende tijd hebben om te lezen en actie te ondernemen.

### Aanpasbare timing (2.2.1)  {#timing-adjustable}

* Succescriterium 2.2.1
* Niveau A
* Toetsenbord: Geef gebruikers voldoende tijd om inhoud te lezen en te gebruiken.

#### Doel - Aanpasbare timing (2.2.1) {#purpose-timing-adjustable}

Het doel van dit succescriterium is ervoor te zorgen dat gebruikers met een handicap voldoende tijd krijgen om waar mogelijk met webinhoud te communiceren. Personen met een handicap, zoals blindheid, slechtziendheid, motorische beperkingen en cognitieve beperkingen, hebben mogelijk meer tijd nodig om inhoud te lezen of functies uit te voeren zoals het invullen van online formulieren. Als de functies van het Web tijd-afhankelijk zijn, zal het voor sommige gebruikers moeilijk zijn om de vereiste actie uit te voeren alvorens een tijdgrens voorkomt. Hierdoor kan de service voor hen ontoegankelijk worden gemaakt. Het ontwerpen van functies die niet afhankelijk zijn van de tijd zal mensen met een handicap helpen deze functies te voltooien. Met opties voor het uitschakelen van tijdslimieten, het aanpassen van de tijdslimieten of het aanvragen van meer tijd voordat een tijdslimiet optreedt, kunnen gebruikers die meer tijd nodig hebben dan verwacht om taken te voltooien, gemakkelijker taken uitvoeren. Deze opties worden vermeld in de volgorde die het meest geschikt is voor de gebruiker. Het onbruikbaar maken van tijdslimieten is beter dan het aanpassen van de lengte van tijdslimieten, wat beter is dan het vragen van meer tijd alvorens een tijdslimiet voorkomt.

#### Hoe kan ik-timing aanpassen (2.2.1) {#how-to-meet-timing-adjustable}

Volg de richtlijnen onder [Hoe te om Succes Criteria 2.2.1](https://www.w3.org/WAI/WCAG21/quickref/#timing-adjustable)te ontmoeten.

#### Meer informatie - Aanpasbare timing (2.2.1) {#more-information-timing-adjustable}

* [Werken met succescriteria 2.2.1](https://www.w3.org/WAI/WCAG21/Understanding/timing-adjustable.html)
* [Voldoen aan criteria 2.2.1](https://www.w3.org/WAI/WCAG21/quickref/#timing-adjustable)

### Pauzeren, stoppen en verbergen (2.2.2)  {#pause-stop-hide}

* Succescriterium 2.2.2
* Niveau A
* Pauze, Stoppen, Verbergen: Voor het verplaatsen, knipperen, schuiven of automatisch bijwerken van gegevens geldt het volgende:
   * Verplaatsen, knipperen, schuiven: Voor elke bewegende, knipperende of schuivende informatie die a) automatisch begint, b) langer dan vijf seconden duurt en c) parallel met andere inhoud wordt weergegeven, is er een mechanisme waarmee de gebruiker deze kan onderbreken, stoppen of verbergen, tenzij de beweging, het knipperen of schuiven deel uitmaakt van een activiteit waar dit essentieel is;
   * Automatisch bijwerken: Voor alle automatisch bij te werken informatie die a) automatisch wordt gestart en b) parallel met andere inhoud wordt weergegeven, is er een mechanisme waarmee de gebruiker deze kan onderbreken, stoppen of verbergen of de frequentie van de update kan bepalen, tenzij de automatisch bij te werken informatie deel uitmaakt van een activiteit waar dit essentieel is.

Opmerkingen zijn:

1. Raadpleeg &#39;Inhoud niet ontwerpen op een manier waarvan bekend is dat ze aanvallen veroorzaakt&#39; voor vereisten met betrekking tot flikkerende of knipperende inhoud (2.3).
1. Aangezien inhoud die niet aan dit succescriterium voldoet, de mogelijkheid van een gebruiker om de hele pagina te gebruiken kan beïnvloeden, moet alle inhoud op de webpagina (ongeacht of deze wordt gebruikt om aan andere succescriteria te voldoen of niet) aan dit succescriterium voldoen. Zie [Conformiteitsvereiste 5: Geen interferentie](https://www.w3.org/TR/WCAG20/#cc5).
1. Inhoud die regelmatig door software wordt bijgewerkt of naar de gebruikersagent wordt gestreamd, is niet verplicht informatie te bewaren of te presenteren die wordt gegenereerd of ontvangen tussen het begin van de pauze- en de hervattingspresentatie, aangezien dit technisch mogelijk is en in veel situaties misleidend kan zijn om dit te doen.
1. Een animatie die optreedt als onderdeel van een voorlaadfase of een vergelijkbare situatie, kan als essentieel worden beschouwd als er tijdens die fase geen interactie kan optreden voor alle gebruikers en als de voortgang niet wordt aangegeven, gebruikers in verwarring kan brengen of kan leiden tot het vermoeden dat de inhoud is bevroren of gebroken.

#### Doel - Pauzeren, Stoppen, Verbergen (2.2.2) {#purpose-pause-stop-hide}

Bepaalde gebruikers vinden mogelijk inhoud die beweegt afleidt, of zelfs fysiek pijnlijk, waardoor het moeilijk wordt om zich op andere delen van de pagina te concentreren. Bovendien kan dergelijke inhoud moeilijk leesbaar zijn voor mensen die moeite hebben met het bijhouden van bewegende tekst.

#### Ontmoeten - Pauzeren, Stoppen, Verbergen (2.2.2) {#how-to-meet-pause-stop-hide}

Afhankelijk van de aard van de inhoud kunt u een of meer van de volgende suggesties toepassen bij het maken van webpagina&#39;s met bewegende, knipperende of knipperende inhoud:

* Biedt een manier om schuivende inhoud te pauzeren zodat gebruikers voldoende tijd hebben om deze te lezen. Bijvoorbeeld nieuwstickers, automatisch bijgewerkte tekst en afbeeldingscarrousels die automatisch worden weergegeven.
* Zorg ervoor dat de inhoud die knippert na vijf seconden stopt met knipperen.
* Gebruik de juiste technologieën om bewegende of knipperende inhoud weer te geven die door de browser kan worden uitgeschakeld. Bijvoorbeeld GIF- (Graphics Interchange Format) of APNG-bestanden (Animated Portable Network Graphics).
* Geef een formulierbesturingselement op de webpagina zodat de gebruiker alle bewegende of knipperende inhoud op de pagina kan uitschakelen.
* Als een van de bovenstaande opties niet mogelijk is, geeft u een koppeling op naar een pagina die alle inhoud bevat, maar zonder verplaatsen of knipperen.

#### Meer informatie - Pauzeren, Stoppen, Verbergen (2.2.2) {#more-information-pause-stop-hide}

* [Succescriterium 2.2.2](https://www.w3.org/WAI/WCAG21/Understanding/pause-stop-hide.html)
* [Voldoen aan criterium 2.4.2](https://www.w3.org/WAI/WCAG21/quickref/#pause-stop-hide)

### Convulsies en fysieke reacties (2.3) {#seizures-and-physcial-reactions}

[Richtsnoer 2.3 Convulsies: Ontwerp de inhoud niet op een manier waarvan bekend is dat deze aanvallen of fysieke reacties veroorzaakt.](https://www.w3.org/TR/WCAG/#seizures-and-physical-reactions)

### Drie instanties of onder de drempelwaarde (2.3.1) {#three-flashes-or-below-threshold}

* Succescriterium 2.3.1
* Niveau A
* Drie instanties of onder de drempelwaarde: Webpagina&#39;s bevatten niets dat meer dan drie keer knippert in een periode van één seconde, of de flits is onder de algemene flash- en rode flitsdrempels.

>[!NOTE]
>
>Aangezien inhoud die niet aan dit succescriterium voldoet, de mogelijkheid van een gebruiker om de hele pagina te gebruiken kan beïnvloeden, moet alle inhoud op de webpagina (ongeacht of deze wordt gebruikt om aan andere succescriteria te voldoen of niet) aan dit succescriterium voldoen. Zie [Conformiteitsvereiste 5: Geen interferentie](https://www.w3.org/TR/WCAG/#cc5).

#### Doel - Drie instanties van Flash of onder de drempelwaarde (2.3.1) {#purpose-three-flashes-or-below-threshold}

In bepaalde gevallen kan knipperende inhoud fotosensitieve aanvallen veroorzaken. Aan de hand van dit succescriterium kunnen dergelijke gebruikers toegang krijgen tot alle inhoud en deze beleven zonder zich zorgen te maken over knipperende inhoud.

#### Hoe te om te ontmoeten - Drie Vlamjes of onder Drempel (2.3.1) {#how-to-meet-three-flashes-or-below-threshold}

Ga als volgt te werk om ervoor te zorgen dat de volgende technieken worden toegepast:

* ervoor zorgen dat de onderdelen gedurende een periode van één seconde niet meer dan drie keer knipperen;
* Als niet aan de bovenstaande voorwaarde kan worden voldaan, kunt u knipperende inhoud binnen een *klein veilig gebied* in pixels op het scherm weergeven. Dit areaal wordt berekend aan de hand van een complexe formule die onder [G176 valt: Het knipperende gebied klein genoeg](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/G176)houden, zodat dient deze techniek alleen te worden gevolgd als knipperende inhoud *absoluut* noodzakelijk is.

#### Meer informatie - Drie instanties of onder de drempelwaarde (2.3.1) {#more-information-three-flashes-or-below-threshold}

* [Werken met succescriterium 2.3.1](https://www.w3.org/WAI/WCAG21/Understanding/three-flashes-or-below-threshold.html)
* [Voldoen aan criterium 2.3.1](https://www.w3.org/WAI/WCAG21/quickref/#three-flashes-or-below-threshold)

### Navigeerbaar (2.4) {#navigable}

[Richtsnoer 2.4 Navigeerbaar: Biedt manieren om gebruikers te helpen navigeren, inhoud te zoeken en te bepalen waar ze zich bevinden.](https://www.w3.org/TR/WCAG/#navigable)

Hiermee zorgt u ervoor dat gebruikers eenvoudig door de inhoud kunnen navigeren.

### Blokken omzeilen (2.4.1)  {#bypass-blocks}

* Succescriterium 2.4.1
* Niveau A
* Blokken omzeilen: Er is een mechanisme beschikbaar waarmee blokken inhoud worden overgeslagen die op meerdere webpagina&#39;s worden herhaald.

#### Doel - Blokkeringen omzeilen (2.4.1) {#purpose-bypass-blocks}

De bedoeling van dit criterium van Succes is om mensen toe te staan die opeenvolgend door inhoud meer directe toegang tot de primaire inhoud van de Web-pagina navigeren. Webpagina&#39;s en toepassingen bevatten vaak inhoud die op andere pagina&#39;s of schermen wordt weergegeven. Voorbeelden van herhaalde blokken inhoud zijn onder andere, maar niet uitsluitend, navigatiekoppelingen, koptekstafbeeldingen, menu&#39;s en advertentiekaders. Kleine herhaalde secties, zoals afzonderlijke woorden, woordgroepen of afzonderlijke koppelingen, worden voor de toepassing van deze bepaling niet als blokken beschouwd.

#### Hoe te om te ontmoeten - Blokkeringen van de Omleiding (2.4.1) {#how-to-meet-bypass-blocks}

Volg de richtlijnen onder [Hoe te om Succes Criteria 2.4.1](https://www.w3.org/WAI/WCAG21/quickref/#bypass-blocks)te ontmoeten.

#### Meer informatie - Blokkeringen omzeilen (2.4.1) {#more-information-bypass-blocks}

* [Werken met succescriteria 2.4.1](https://www.w3.org/WAI/WCAG21/Understanding/bypass-blocks.html)
* [Voldoen aan criteria 2.4.1](https://www.w3.org/WAI/WCAG21/quickref/#bypass-blocks)

### Getitelde pagina (2.4.2)  {#page-titled}

* Succescriterium 2.4.2
* Niveau A
* Getitelde pagina: Webpagina&#39;s hebben titels die onderwerp of doel beschrijven.

#### Doel - Getitelde pagina (2.4.2) {#purpose-page-titled}

Met dit succescriterium kan iedereen, ongeacht een bepaalde handicap, de inhoud van een webpagina snel identificeren zonder de pagina volledig te lezen. Dit is vooral handig wanneer meerdere webpagina&#39;s worden geopend op de tabbladen van de browser, omdat de paginatitel op het tabblad wordt weergegeven en deze daarom snel kan worden gevonden.

#### Hoe kan ik-pagina getiteld (2.4.2) {#how-to-meet-page-titled}

Wanneer in AEM een nieuwe HTML-pagina wordt gemaakt, kunt u de paginatitel opgeven. Zorg ervoor dat de titel een adequate beschrijving geeft van de inhoud en het doel van de pagina, met name van eventuele unieke aspecten, zodat bezoekers snel kunnen zien of de inhoud al dan niet relevant is voor hun behoeften.

U kunt de paginatitel ook bewerken tijdens het bewerken van een pagina. Deze kan worden geopend via **Pagina-informatie** - **Eigenschappen.**

#### Meer informatie - Getitelde pagina (2.4.2) {#more-information-page-titled}

* [Succescriterium 2.4.2](https://www.w3.org/WAI/WCAG21/Understanding/page-titled.html)
* [Voldoen aan criterium 2.2.2](https://www.w3.org/WAI/WCAG21/quickref/#page-titled)

### Focusvolgorde (2.4.3)  {#focus-order}

* Succescriterium 2.4.3
* Niveau A
* Focusvolgorde: Als een Web-pagina opeenvolgend kan worden genavigeerd en de navigatiereeksen betekenis of verrichting beïnvloeden, ontvangen de brandpuntbruikbare componenten nadruk in een orde die betekenis en operabiliteit bewaart.

#### Doel - Activeringsvolgorde (2.4.3) {#purpose-focus-order}

Het doel van dit succescriterium is ervoor te zorgen dat gebruikers die opeenvolgend door inhoud navigeren, informatie tegenkomen in een volgorde die consistent is met de betekenis van de inhoud en vanaf het toetsenbord kunnen worden gebruikt. Dit vermindert verwarring door gebruikers een consistent mentaal model van de inhoud te laten vormen. Er kunnen verschillende volgorden zijn die logische verhoudingen in de inhoud weerspiegelen. Als u bijvoorbeeld componenten doorloopt in een onlineformulier dat uit meerdere velden en/of stappen bestaat, weerspiegelt u de logische relaties in de inhoud.

#### Hoe kan ik-focusvolgorde (2.4.3) {#how-to-meet-focus-order}

Volg de richtlijnen onder [Hoe te om Succes Criteria 2.4.3](https://www.w3.org/WAI/WCAG21/quickref/#focus-order)te ontmoeten.

#### Meer informatie - Activeringsvolgorde (2.4.3) {#more-information-focus-order}

* [Werken met succescriteria 2.4.3](https://www.w3.org/WAI/WCAG21/Understanding/focus-order.html)
* [Voldoen aan criteria 2.4.3](https://www.w3.org/WAI/WCAG21/quickref/#focus-order)

### Koppelingsdoel (in context) (2.4.4)  {#link-purpose-in-context}

* Succescriterium 2.4.4
* Niveau A
* Koppelingsdoel (in context): Het doel van elke koppeling kan worden bepaald op basis van alleen de koppelingstekst of van de koppelingstekst samen met de programmatisch bepaalde koppelingscontext, behalve wanneer het doel van de koppeling dubbelzinnig zou zijn voor gebruikers in het algemeen.

#### Doel - Koppelingsdoel (in context) (2.4.4) {#purpose-link-purpose-in-context}

Voor alle gebruikers, ongeacht de handicap, is het van essentieel belang dat duidelijk de richting van een koppeling wordt aangegeven door middel van de juiste koppelingstekst. Hierdoor kunnen gebruikers beter beslissen of ze een koppeling willen volgen of niet. Voor waargenomen gebruikers is betekenisvolle koppelingstekst uiterst nuttig wanneer er meerdere koppelingen op een pagina staan (met name als de pagina tekstoptig is), omdat betekenisvolle koppelingstekst een duidelijkere indicatie geeft van de functionaliteit van de doelpagina. Gebruikers van bepaalde ondersteunende hulpmiddelen, die een lijst met alle koppelingen op één pagina kunnen genereren, kunnen de koppelingstekst eenvoudiger uit hun context zien als die koppelingstekst uniek en informatief is. Zichtbare personen met cognitieve handicaps kunnen echter verward raken als een link niet voldoende informatie biedt om nauwkeurig te beschrijven waar de koppeling hen naartoe brengt.

#### Hoe te om te ontmoeten - verbind Doel (in context) (2.4.4) {#how-to-meet-link-purpose-in-context}

Zorg er vooral voor dat het doel van een koppeling duidelijk wordt beschreven in de tekst van de koppeling.

* Onjuist voorbeeld:
   * Tekst: Klik hier voor meer informatie over onze avondlessen voor het najaar van 2010.
   * Reden: de bestemming ervan wordt niet duidelijk en ondubbelzinnig aangegeven.
* Goed voorbeeld:
   * Tekst: Gebeurtenisklassen voor het najaar van 2010 - details.
   * Reden: Door de tekst en de positie van het koppelingselement enigszins aan te passen, kan de koppelingstekst worden verbeterd:

Koppelingen moeten op alle pagina&#39;s consistent worden gephrasd, met name voor navigatiebalken. Als een koppeling naar een specifieke pagina bijvoorbeeld op één pagina de naam **Publicaties** heeft, gebruikt u die tekst op andere pagina&#39;s om de consistentie te garanderen.

Op het moment van schrijven zijn er enkele problemen met betrekking tot het gebruik van titelkenmerken om ervoor te zorgen dat vergelijkbare koppelingen op een pagina unieke informatie over de bestemming bieden (zo verwijst &quot;Meer lezen&quot; vaak naar een reeks verschillende doelen):

* Tekst in het titelkenmerk is doorgaans alleen beschikbaar voor muisgebruikers als pop-upvenster met knopinfo en kan niet consistent worden benaderd met het toetsenbord of door mobiele gebruikers.
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
>
>Het bovenstaande fragment is een illustratie. Het wordt aangeraden de **component Afbeelding** te gebruiken.

Hoewel het raadzaam is om koppelingstekst te verstrekken die het doel van de verbinding zonder extra context identificeert, wordt erkend dat dit niet altijd mogelijk is. Contextvrije koppelingen kunnen in de volgende gevallen worden gebruikt, waarvan HTML-voorbeelden te vinden zijn in [Hoe kan ik voldoen aan criterium 2.4.4](https://www.w3.org/WAI/WCAG21/quickref/#link-purpose-in-context).

* Waar de koppelingstekst deel uitmaakt van een lijst met nauw verwante koppelingen en wanneer het lijstitem dat de koppeling omsluit voldoende context biedt.
* Wanneer het doel van een koppeling duidelijk kan worden bepaald aan de hand van de *voorgaande* (niet de volgende) alineatekst.
* Indien de koppeling zich in een gegevenstabel bevindt, kan het doel duidelijk worden aangegeven in de desbetreffende rubrieken.
* Wanneer een lijst met koppelingen zich in een reeks koppen bevindt en de kop zelf een geschikte context biedt.
* Wanneer een lijst met koppelingen zich in een geneste koppeling bevindt en het bovenliggende lijstitem boven de geneste koppeling een geschikte context biedt.

In sommige gevallen, waar er verscheidene verbindingen op een pagina zijn (elk die de richting van een verbinding in complexe, maar noodzakelijke detail verstrekt), kan het aangewezen zijn om een alternatieve versie van de Web-pagina te verstrekken die de nauwkeurige zelfde inhoud toont maar waar de verbindingstekst niet zo gedetailleerd is.

U kunt ook scripts gebruiken, zodat er een minimale hoeveelheid tekst wordt opgegeven in de koppeling zelf. Als u echter een geschikt besturingselement activeert dat zich boven aan de pagina bevindt, wordt de koppelingstekst *uitgebreid* tot meer details. Een vergelijkbare aanpak is het gebruik van CSS om de volledige koppeling voor waargenomen gebruikers te *verbergen* , maar deze toch volledig uit te voeren naar schermlezers. Dit valt buiten het toepassingsgebied van dit document, maar meer informatie over hoe dit kan worden bereikt is te vinden in de sectie [Meer informatie - Koppelingsdoel (In context) (2.4.4)](#more-information-link-purpose-in-context) .

#### Meer informatie - Koppelingsdoel (in context) (2.4.4) {#more-information-link-purpose-in-context}

* [Succescriterium 2.4.4](https://www.w3.org/WAI/WCAG21/Understanding/link-purpose-in-context.html)
* [Voldoen aan criterium 2.4.4](https://www.w3.org/WAI/WCAG21/quickref/#link-purpose-in-context)

<!--
* [C7: Using CSS to hide a portion of the link text](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/C7)
-->

### Meerdere manieren (2.4.5)  {#multiple-ways}

* Succescriterium 2.4.5
* Niveau AA
* Meerdere manieren: Meer dan één manier is beschikbaar om van een Web-pagina binnen een reeks Web-pagina&#39;s de plaats te bepalen behalve waar de Web-pagina het resultaat van, of een stap in, een proces is.

#### Doel - Meerdere manieren (2.4.5) {#purpose-multiple-ways}

Het doel van dit succescriterium is dat gebruikers inhoud kunnen vinden op een manier die het best aansluit bij hun behoeften. Gebruikers kunnen een bepaalde techniek gemakkelijker of begrijpelijker gebruiken dan een andere.

Zelfs kleine sites moeten gebruikers enige oriëntatiemiddelen bieden. Voor een site met drie of vier pagina&#39;s, waarbij alle pagina&#39;s zijn gekoppeld vanaf de startpagina, is het mogelijk voldoende om koppelingen te verschaffen van en naar de startpagina, waar de koppelingen op de startpagina ook als een site-overzicht kunnen fungeren.

#### Hoe te om - Veelvoudige Manieren (2.4.5) te ontmoeten {#how-to-meet-multiple-ways}

Volg de richtlijnen onder [Hoe te om Succes Criteria 2.4.5](https://www.w3.org/WAI/WCAG21/quickref/#multiple-ways)te ontmoeten.

#### Meer informatie - Meerdere manieren (2.4.5) {#more-information-multiple-ways}

* [Werken met succescriteria 2.4.5](https://www.w3.org/WAI/WCAG21/Understanding/multiple-ways.html)
* [Voldoen aan criteria 2.4.5](https://www.w3.org/WAI/WCAG21/quickref/#multiple-ways)

### Koppen en labels (2.4.6)  {#headings-and-labels}

* Succescriterium 2.4.6
* Niveau AA
* Koppen en labels: De rubrieken en de etiketten beschrijven onderwerp of doel.

#### Doel - Koppen en labels (2.4.6) {#purpose-headings-and-labels}

Het doel van dit criterium van Succes is gebruikers te helpen begrijpen welke informatie in Web-pagina&#39;s bevat en hoe die informatie wordt georganiseerd. Wanneer de koppen duidelijk en beschrijvend zijn, kunnen de gebruikers de informatie vinden zij gemakkelijker zoeken, en zij kunnen de verhouding tussen verschillende delen van de inhoud gemakkelijker begrijpen. Met beschrijvende labels kunnen gebruikers specifieke componenten in de inhoud identificeren.

#### Voldoen - Koppen en labels (2.4.6) {#how-to-meet-headings-and-labels}

Volg de richtlijnen onder [Hoe te om Succes Criteria 2.4.6](https://www.w3.org/WAI/WCAG21/quickref/#headings-and-labels)te ontmoeten.

#### Meer informatie - Koppen en labels (2.4.6) {#more-information-headings-and-labels}

* [Werken met succescriteria 2.4.6](https://www.w3.org/WAI/WCAG21/Understanding/headings-and-labels.html)
* [Voldoen aan criteria 2.4.6](https://www.w3.org/WAI/WCAG21/quickref/#headings-and-labels)

### Focus zichtbaar (2.4.7)  {#focus-visible}

* Succescriterium 2.4.7
* Niveau AA
* Zichtbare focus: Om het even welke toetsenbord werkende gebruikersinterface heeft een wijze van verrichting waar de toetsenbordnadrukindicator zichtbaar is.

#### Doel - Focus zichtbaar (2.4.7) {#purpose-focus-visible}

Het doel van dit succescriterium is om een persoon te helpen weten welk element de toetsenbordfocus heeft.

Het moet voor een persoon mogelijk zijn om te weten welk element onder veelvoudige elementen de toetsenbordnadruk heeft. Als er slechts één besturingselementen voor actioneren van het toetsenbord op het scherm zijn, is aan het succescriterium voldaan omdat het visuele ontwerp slechts één actionabel item voor het toetsenbord voorstelt.

Wanneer het succescriterium &quot;wijze van werking&quot; aangeeft, moet dit worden gebruikt voor platforms die niet altijd een focusindicator kunnen weergeven. In de meeste gevallen is er slechts één werkwijze, zodat deze succescriteria van toepassing zijn.

#### Hoe kan ik-Focus zichtbaar maken (2.4.7) {#how-to-meet-focus-visible}

Volg de richtlijnen onder [Hoe te om Succes Criteria 2.4.7](https://www.w3.org/WAI/WCAG21/quickref/#focus-visible)te ontmoeten.

#### Meer informatie - Focus zichtbaar (2.4.7) {#more-information-focus-visible}

* [Werken met succescriteria 2.4.7](https://www.w3.org/WAI/WCAG21/Understanding/focus-visible.html)
* [Voldoen aan criteria 2.4.7](https://www.w3.org/WAI/WCAG21/quickref/#focus-visible)

## Beginsel 3: Begrijpelijk {#principle-understandable}

[Beginsel 3: Begrijpelijk - Informatie en de werking van gebruikersinterface moeten begrijpelijk zijn.](https://www.w3.org/TR/WCAG/#understandable)

### Tekstinhoud leesbaar en begrijpelijk maken (3.1) {#make-text-content-readable-and-understandable}

[Richtsnoer 3.1 Leesbaar: Maak tekstinhoud leesbaar en begrijpelijk.](https://www.w3.org/TR/WCAG/#readable)

### Taal van pagina (3.1.1) {#language-of-page}

* Succescriterium 3.1.1
* Niveau A
* Taal van pagina: De standaard menselijke taal van elke Web-pagina kan programmatically worden bepaald.

#### Doel - Taal van pagina (3.1.1) {#purpose-language-of-page}

Het doel van dit succescriterium is ervoor te zorgen dat tekst en andere taalkundige inhoud correct worden weergegeven. Voor gebruikers van schermlezers zorgt dit ervoor dat de inhoud correct wordt uitgedruct, terwijl visuele browsers eerder bepaalde tekensets correct zullen weergeven.

#### Hoe kan ik-taal van pagina (3.1.1) {#how-to-meet-language-of-page}

Om aan dit succescriterium te voldoen, kan de standaardtaal van een Web-pagina worden geïdentificeerd gebruikend het `lang` attribuut binnen het `<html>` element bij de bovenkant van de pagina. Bijvoorbeeld:

* Als een pagina in het Engels is geschreven, moet het `<html>` element als volgt worden gelezen:
   `<html lang = “en”>`

* Overwegende dat voor een in het Spaans af te geven pagina de volgende norm moet worden vastgesteld:
   `<html lang = “es”>`

In AEM wordt de standaardtaal van de pagina ingesteld bij het maken van de pagina, maar deze taal kan ook worden gewijzigd bij het bewerken van [Pagina-eigenschappen](/help/sites-authoring/editing-page-properties.md).

>[!NOTE]
>
>AEM verstrekt verdere verfijning voor variaties van een worteltaal; Bijvoorbeeld Amerikaans Engels - en-us, Brits Engels - en-gb en Canadees Engels - en-ca. Dit detailniveau is vaak overbodig voor ondersteunende hulpmiddelen, maar kan worden gebruikt voor regionale variaties in pagina-inhoud.

#### Meer informatie - Taal van pagina (3.1.1) {#more-information-language-of-page}

* [Werken met succescriterium 3.1.1](https://www.w3.org/WAI/WCAG21/Understanding/language-of-page.html)
* [Voldoen aan criterium 3.1.1](https://www.w3.org/WAI/WCAG21/quickref/#language-of-page)
* De codes zijn gebaseerd op ISO 639-1. Een uitgebreidere lijst met codes voor elke taal is te vinden op de [W3-website](https://www.w3schools.com/tags/ref_language_codes.asp).

### Taal van onderdelen (3.1.2)  {#language-of-parts}

* Succescriterium 3.1.2
* Niveau AA
* Taal van onderdelen: De menselijke taal van elke passage of uitdrukking in de inhoud kan programmatisch worden bepaald behalve juiste namen, technische termijnen, woorden van onbepaalde taal, en woorden of uitdrukkingen die deel van het woordenboek van de onmiddellijk omringende tekst zijn geworden.

#### Doel - Taal van onderdelen (3.1.2) {#purpose-language-of-parts}

Het doel van dit succescriterium lijkt op dat van het succescriterium [Taal van pagina](#language-of-page), behalve dat het van toepassing is op webpagina&#39;s die inhoud bevatten in meerdere talen op één pagina (bijvoorbeeld vanwege noteringen of ongebruikelijke leenwoorden).

Pagina&#39;s die dit succescriterium toepassen, maken het mogelijk:

* Braille-overgangssoftware voor het invoegen van tekens met accenten.
* Schermlezers spreken woorden uit die speciale tekens hebben of niet in de standaardtaal staan die op paginaniveau is geïdentificeerd.
* Met vertaalprogramma&#39;s zoals Google Translate kunt u inhoud van de ene taal naar de andere vertalen.

#### Hoe te om te ontmoeten - Taal van Delen (3.1.2) {#how-to-meet-language-of-parts}

Het `lang` kenmerk kan worden gebruikt om wijzigingen in de taal van de inhoud te identificeren. Een citaat in het Duits (ISO 639-1 code &quot;de&quot;) kan bijvoorbeeld als volgt worden weergegeven:

```xml
<blockquote cite = "John F. Kennedy" lang = "de">
     <p>Ich bin ein Berliner</p>
 </blockquote>
```

>[!NOTE]
>
>Blockquotes worden niet ondersteund in een out-of-the-box-instantie. Een aangepaste component kan worden ontwikkeld ter ondersteuning van de functie.

Op dezelfde manier kan browser een ongewoon woord of een woordgroep correct teruggeven als het `span` element als volgt wordt gebruikt:

```xml
<p>The only French phrase I know is <span lang = “fr”>je ne sais quoi</code>.</p>
```

>[!NOTE]
>
>Dit succescriterium hoeft niet te worden gevolgd wanneer namen of steden in verschillende talen worden opgenomen of wanneer leningswoorden of zinnen worden gebruikt die in de standaardtaal gangbaar zijn geworden (zoals *overlijden* in het Engels).

Als u het span-element met een geschikte taal wilt toevoegen, kunt u de HTML-markering handmatig bewerken in de bronbewerkingsmodus van de RTE, zodat deze als hierboven wordt gelezen. Alternatief kan het `lang` attribuut in RTE door een systeembeheerder worden omvat (zie het [Toevoegen van Steun voor Extra Elementen en Attributen](/help/sites-administering/rte-accessible-content.md#adding-support-for-additional-html-elements-and-attributes)van HTML).

#### Meer informatie - Taal van onderdelen (3.1.2) {#more-information-language-of-parts}

* [Werken met succescriterium 3.1.2](https://www.w3.org/WAI/WCAG21/Understanding/language-of-parts.html)
* [Voldoen aan criterium 3.1.2](https://www.w3.org/WAI/WCAG21/quickref/#language-of-parts)

### Voorspelbaar (3.2) {#predictable}

[Richtsnoer 3.2 voorspelbaar: Webpagina&#39;s maken verschijnen en werken op voorspelbare manieren.](https://www.w3.org/TR/WCAG/#predictable)

Hierbij wordt ervoor gezorgd dat de webpagina&#39;s er consistent uitzien en functioneren.

### Veld activeren (3.2.1)  {#on-focus}

* Succescriterium 3.2.1
* Niveau A
* Veld activeren: Wanneer een gebruikersinterfacecomponent focus krijgt, wordt er geen contextwijziging gestart.

#### Doel - Veld activeren (3.2.1) {#purpose-on-focus}

Het doel van dit succescriterium is ervoor te zorgen dat de functionaliteit voorspelbaar is wanneer bezoekers door een document navigeren. Elke component die een gebeurtenis kan activeren wanneer deze focus krijgt, mag de context niet wijzigen. Voorbeelden van het wijzigen van de context wanneer een component focus krijgt, zijn onder andere:

* formulieren die automatisch worden ingediend wanneer een component focus krijgt;
* nieuwe vensters die worden gestart wanneer een component focus krijgt;
* focus wordt gewijzigd in een andere component wanneer die component focus krijgt;

Focus kan naar een besturingselement worden verplaatst via het toetsenbord (bijvoorbeeld met Tab naar een besturingselement) of de muis (bijvoorbeeld door op een tekstveld te klikken). Als u de muis over een besturingselement beweegt, wordt de focus niet verplaatst, tenzij dit gedrag door scripts wordt geïmplementeerd. Merk op dat voor sommige soorten controles, het klikken op een controle de controle (b.v. knoop) kan ook activeren, die, beurtelings, een verandering in context kan in werking stellen.

#### Hoe te om te ontmoeten - op Focus (3.2.1) {#how-to-meet-on-focus}

Volg de richtlijnen onder [Hoe te om Succes Criteria 3.2.1](https://www.w3.org/WAI/WCAG21/quickref/#on-focus)te ontmoeten.

#### Meer informatie - Veld activeren (3.2.1) {#more-information-on-focus}

* [Werken met succescriteria 3.2.1](https://www.w3.org/WAI/WCAG21/Understanding/on-focus.html)
* [Voldoen aan criteria 3.2.1](https://www.w3.org/WAI/WCAG21/quickref/#on-focus)

### Bij invoer (3.2.2)  {#on-input}

* Succescriterium 3.2.2
* Niveau A
* Bij invoer: Als u de instelling van een gebruikersinterfacecomponent wijzigt, wordt de context niet automatisch gewijzigd, tenzij de gebruiker op de hoogte is gesteld van het gedrag voordat de component wordt gebruikt.

#### Doel - Aan-invoer (3.2.2) {#purpose-on-input}

Het doel van dit succescriterium is ervoor te zorgen dat het invoeren van gegevens of het selecteren van een formulierbesturingselement voorspelbare effecten heeft. Het veranderen van het plaatsen van om het even welk gebruikersinterfacecomponent verandert één of ander aspect in de controle die zal voortbestaan wanneer de gebruiker niet meer met het communiceert. Als u dus een selectievakje inschakelt, tekst invoert in een tekstveld of de geselecteerde optie wijzigt in een lijstbesturingselement, wijzigt u de instelling, maar het activeren van een koppeling of een knop doet dit niet. Wijzigingen in context kunnen gebruikers verwarren die de wijziging niet gemakkelijk waarnemen of die gemakkelijk door wijzigingen worden afgeleid. Wijzigingen in de context zijn alleen geschikt wanneer duidelijk is dat een dergelijke wijziging zal plaatsvinden als reactie op de actie van de gebruiker.

#### Hoe kan ik-op-invoer (3.2.2) {#how-to-meet-on-input}

Volg de richtlijnen onder [Hoe te om Succes Criteria 3.2.2](https://www.w3.org/WAI/WCAG21/quickref/#on-input)te ontmoeten.

#### Meer informatie - Bij invoer (3.2.2) {#more-information-on-input}

* [Werken met succescriteria 3.2.2](https://www.w3.org/WAI/WCAG21/Understanding/on-input.html)
* [Voldoen aan criteria 3.2.2](https://www.w3.org/WAI/WCAG21/quickref/#on-input)

### Consistente navigatie (3.2.3)  {#consistent-navigation}

* Succescriterium 3.2.3
* Niveau AA
* Consistente navigatie: De navigatiemechanismen die op veelvoudige Web-pagina&#39;s binnen een reeks Web-pagina&#39;s worden herhaald komen in de zelfde relatieve orde voor telkens als zij worden herhaald, tenzij een verandering door de gebruiker in werking wordt gesteld.

#### Doel - Consistente navigatie (3.2.3) {#purpose-consistent-navigation}

Dit succescriterium is bedoeld om het gebruik van een consistente presentatie en lay-out aan te moedigen voor gebruikers die met herhaalde inhoud binnen een set webpagina&#39;s werken en meer dan één keer specifieke informatie of functionaliteit moeten zoeken. Personen met een laag gezichtsvermogen die schermvergroting gebruiken om een klein gedeelte van het scherm tegelijk weer te geven, gebruiken vaak visuele aanwijzingen en paginagrenzen om snel herhaalde inhoud te vinden. Het presenteren van herhaalde inhoud in dezelfde volgorde is ook belangrijk voor visuele gebruikers die ruimtelijk geheugen of visuele aanwijzingen in het ontwerp gebruiken om herhaalde inhoud te zoeken.

Het is belangrijk om op te merken dat het gebruik van de uitdrukking &quot;zelfde orde&quot;in deze sectie niet bedoeld is om te impliceren dat de subnavigatiemenu&#39;s niet kunnen worden gebruikt of dat de blokken van secundaire navigatie of paginastructuur niet kunnen worden gebruikt. In plaats daarvan, is dit Criterium van Succes bedoeld om gebruikers te helpen die met herhaalde inhoud over Web-pagina&#39;s in wisselwerking staan om de plaats van de inhoud te kunnen voorspellen zij zoeken en het sneller vinden wanneer zij het opnieuw ontmoeten.

Gebruikers kunnen een wijziging in de volgorde initiëren met behulp van adaptieve gebruikersagents of door voorkeuren in te stellen, zodat de informatie op een voor hen meest nuttige manier wordt weergegeven.

#### Ontmoeten - Consistente Navigatie (3.2.3) {#how-to-meet-consistent-navigation}

Volg de richtlijnen onder [Hoe te om Succes Criteria 3.2.3](https://www.w3.org/WAI/WCAG21/quickref/#consistent-navigation)te ontmoeten.

#### Meer informatie - Consistente navigatie (3.2.3) {#more-information-consistent-navigation}

* [Werken met succescriteria 3.2.3](https://www.w3.org/WAI/WCAG21/Understanding/consistent-navigation.html)
* [Voldoen aan criteria 3.2.3](https://www.w3.org/WAI/WCAG21/quickref/#consistent-navigation)

### Consistente identificatie (3.2.4)  {#consistent-identification}

* Succescriterium 3.2.4
* Niveau A
* Consistente identificatie: Componenten met dezelfde functionaliteit in een set webpagina&#39;s worden consistent geïdentificeerd.

#### Doel - Consistente identificatie (3.2.4) {#purpose-consistent-identification}

Het doel van dit succescriterium is ervoor te zorgen dat functionele componenten die herhaaldelijk in een set webpagina&#39;s voorkomen, op consistente wijze worden geïdentificeerd. Een strategie die mensen die het schermlezers gebruiken wanneer het werken van een Website moet zich zwaar op hun vertrouwdheid met functies baseren die op verschillende Web-pagina&#39;s kunnen verschijnen. Als de identieke functies verschillende etiketten (of, meer in het algemeen, een verschillende toegankelijke naam) op verschillende Web-pagina&#39;s hebben, zal de plaats aanzienlijk moeilijker te gebruiken zijn. Het kan ook verwarrend zijn en de cognitieve belasting verhogen voor mensen met cognitieve beperkingen. Daarom zal consistente etikettering helpen.

Deze consistentie geldt ook voor de alternatieven voor de tekst. Als pictogrammen of andere niet-tekstitems dezelfde functionaliteit hebben, moeten de alternatieven voor de tekst ook consistent zijn.

Als er twee componenten op een webpagina zijn die beide dezelfde functionaliteit hebben als een component op een andere pagina in een set webpagina&#39;s, moeten alle drie consistent zijn. De twee op dezelfde pagina zullen dus consistent zijn.

3.2.4 is weliswaar wenselijk en is altijd in overeenstemming met één webpagina, maar 3.2.4 gaat alleen over consistentie binnen een set webpagina&#39;s waar iets op meer dan één pagina in de set wordt herhaald.

#### Voldoen aan consistente identificatie (3.2.4) {#how-to-meet-consistent-identification}

Volg de richtlijnen onder [Hoe te om Succes Criteria 3.2.4](https://www.w3.org/WAI/WCAG21/quickref/#consistent-identification)te ontmoeten.

#### Meer informatie - Consistente identificatie (3.2.4) {#more-information-consistent-identification}

* [Werken met succescriteria 3.2.4](https://www.w3.org/WAI/WCAG21/Understanding/consistent-identification.html)
* [Voldoen aan criteria 3.2.4](https://www.w3.org/WAI/WCAG21/quickref/#consistent-identification)

### Invoerbijstand (3.3) {#input-assistance}

[Richtsnoer 3.3 Invoerbijstand: Gebruikers helpen fouten te voorkomen en te corrigeren.](https://www.w3.org/TR/WCAG/#input-assistance)

### Foutidentificatie (3.3.1)  {#error-identification}

* Succescriterium 3.3.1
* Niveau A
* Foutidentificatie: Als er automatisch een invoerfout wordt gedetecteerd, wordt het foutitem geïdentificeerd en wordt de fout in tekst aan de gebruiker beschreven.

#### Doel - Foutidentificatie (3.3.1) {#purpose-error-identification}

Dit succescriterium is bedoeld om ervoor te zorgen dat gebruikers weten dat er een fout is opgetreden en kunnen bepalen wat fout is. Het foutbericht moet zo specifiek mogelijk zijn. Als het verzenden van een formulier mislukt is, is het niet voldoende om het formulier opnieuw weer te geven en de foutvelden aan te geven om te zien dat er een fout is opgetreden. Gebruikers van schermlezers weten bijvoorbeeld pas dat er een fout is opgetreden als ze een van de indicatoren tegenkomen. Ze kunnen het formulier helemaal verlaten voordat ze de foutindicator tegenkomen, omdat ze denken dat de pagina gewoon niet functioneel is. Volgens de definitie in WCAG is een [invoerfout](https://www.w3.org/TR/WCAG/#dfn-input-error) informatie die door de gebruiker is opgegeven en die niet is geaccepteerd. Dit omvat:

informatie die door de webpagina wordt vereist maar door de gebruiker wordt weggelaten, of informatie die door de gebruiker wordt verstrekt maar die buiten het vereiste gegevensformaat of toegestane waarden valt.
Bijvoorbeeld:

* de gebruiker geeft de juiste afkorting in aan de staat, provincie, regio, enz. field;
* de gebruiker een statusafkorting invoert die niet geldig is;
* de gebruiker een niet-bestaande postcode invoert;
* de gebruiker in de toekomst 2 jaar na de geboorte ingaat;
* de gebruiker voert alfabetische karakters of haakjes in hun gebied van het telefoonaantal in dat slechts aantallen goedkeurt;
* de gebruiker voert een bod in dat lager is dan het vorige bod of de minimumbodverhoging.

#### Hoe kan ik-fout-identificatie (3.3.1) {#how-to-meet-error-identification}

Volg de richtlijnen onder [Hoe te om Succes Criteria 3.3.1](https://www.w3.org/WAI/WCAG21/quickref/#error-identification)te ontmoeten.

#### Meer informatie - Foutidentificatie (3.3.1) {#more-information-error-identification}

* [Werken met succescriteria 3.3.1](https://www.w3.org/WAI/WCAG21/Understanding/error-identification.html)
* [Voldoen aan criteria 3.3.1](https://www.w3.org/WAI/WCAG21/quickref/#error-identification)

### Labels of instructies (3.3.2) {#labels-or-instructions}

* Succescriterium 3.3.2
* Niveau A
* Labels of instructies: Labels of instructies worden gegeven wanneer de inhoud gebruikersinvoer vereist.

#### Doel - Labels of instructies (3.3.2) {#purpose-labels-or-instructions}

Het geven van instructies om mensen te helpen vormen in te vullen is een fundamenteel onderdeel van goede praktijken in interfacebruikbaarheid. Dit is vooral handig voor mensen met een visuele of cognitieve handicap die anders moeite zouden hebben om de indeling van een formulier en het soort gegevens dat in een bepaald formulierveld moet worden verstrekt, te begrijpen.

##### Formulieren

In het AEM WKND demoproject wordt een standaardlabel toegevoegd wanneer u een formuliercomponent, zoals een **tekstveld**, aan de pagina toevoegt. Deze standaardtitel is afhankelijk van het type component. U kunt uw eigen titel toevoegen op het tabblad **Titel en Tekst** van het dialoogvenster Bewerken voor dat veld. Het is belangrijk dat labels gebruikers helpen de gegevens te begrijpen die aan elke formuliercomponent zijn gekoppeld.

Dit veld **Titel** moet worden gebruikt voor veldelementen omdat het een label bevat dat beschikbaar is voor ondersteunende hulpmiddelen. Alleen het schrijven van een label in tekst naast het veld is niet voldoende.

Voor sommige formuliercomponenten is het ook mogelijk om labels visueel te verbergen met het selectievakje **Titel verbergen**. Labels die op deze manier zijn verborgen, zijn nog steeds beschikbaar voor ondersteunende technologie, maar worden niet op het scherm weergegeven. Hoewel dit in sommige situaties een goede aanpak kan zijn, is het doorgaans het beste om waar mogelijk een visueel label op te nemen, omdat sommige gebruikers wellicht een zeer klein gedeelte van het scherm bekijken (één veld tegelijk) en de labels nodig hebben om het veld correct te identificeren.

###### Afbeeldingsknoppen {#image-buttons}

Where image buttons are used (for example, the **Image Button** component of the WKND project) the **Title** field in the **Title and Text** tab of the edit dialog actually provides the alt text for the image, rather than the label. In het onderstaande voorbeeld heeft de afbeelding met de tekst `Submit` dus alternatieve tekst van `Submit`, toegevoegd met het veld **Titel** in het dialoogvenster Bewerken.

###### Groepen formuliervelden {#groups-of-form-fields}

In the WKND project, where there is a group of related controls, such as **Radio Group**, a title may be needed for the group, as well as individual controls. Wanneer u een set keuzerondjes toevoegt in AEM, wordt in het veld **Titel** deze groepstitel weergegeven, terwijl afzonderlijke titels worden opgegeven wanneer de keuzerondjes (**Items**) worden gemaakt.

Er is echter geen programmatische koppeling tussen de groepstitel en de keuzerondjes zelf. Sjablooneditors moeten de titel in de benodigde `fieldset`- en `legend`-tags plaatsen om deze koppeling te maken. Dit kan alleen door de broncode van de pagina te bewerken. Een systeembeheerder kan ook ondersteuning voor deze elementen toevoegen, zodat deze worden weergegeven in het dialoogvenster **Veldeigenschappen**[ (zie Ondersteuning voor aanvullende HTML-elementen en -kenmerken toevoegen](/help/sites-administering/rte-accessible-content.md#adding-support-for-additional-html-elements-and-attributes)).

###### Aanvullende overwegingen voor Forms {#additional-considerations-for-forms}

Als gegevens in een specifieke indeling moeten worden ingevoerd, maakt u dit duidelijk in de labeltekst. Als bijvoorbeeld een datum in de `DD-MM-YYYY` notatie moet worden ingevoerd, geeft u dit specifiek op als onderdeel van het label. Dit betekent dat wanneer gebruikers van schermlezers het veld tegenkomen, het label automatisch wordt aangekondigd, samen met aanvullende informatie over de indeling.

Als invoer voor een formulierveld verplicht is, maakt u dit duidelijk door het vereiste woord als onderdeel van het label te gebruiken. AEM voegt een sterretje toe wanneer een veld vereist is, maar het is ideaal om het woord `required`in het label zelf op te nemen (in het veld **Titel** in het dialoogvenster Bewerken).

Het positioneren van labels is ook belangrijk, omdat ze hierdoor geschikte velden kunnen vinden. Dit is van bijzonder belang wanneer de gebruiker met een complexe vorm wordt geconfronteerd. Volg de onderstaande conventie:

* Selectievakjes of keuzerondjes:
De labels worden direct rechts van het veld geplaatst.
* Alle andere formuliercomponenten (bijvoorbeeld tekstvakken, keuzelijsten met invoervak):
De labels worden direct boven of direct links van het veld geplaatst.

In eenvoudige formulieren met een zeer beperkte functionaliteit kan een juiste etikettering van een `Submit` knop fungeren als een label voor het aangrenzende veld (bijvoorbeeld `Search`). Dit is handig in situaties waarin het lastig kan zijn om ruimte te zoeken voor de labeltekst.

#### Meer informatie - Labels of instructies (3.3.2) {#more-information-labels-or-instructions}

* [Werken met succescriterium 3.3.2](https://www.w3.org/WAI/WCAG21/Understanding/labels-or-instructions.html)
* [Voldoen aan criterium 3.3.2](https://www.w3.org/WAI/WCAG21/quickref/#labels-or-instructions)

### Foutmelding (3.3.3)  {#error-suggestion}

* Succescriterium 3.3.3
* Niveau AA
* Toetsenbord: Als automatisch een invoerfout wordt ontdekt en de suggesties voor correctie zijn bekend, dan worden de suggesties verstrekt aan de gebruiker, tenzij het de veiligheid of het doel van de inhoud in gevaar zou brengen.

#### Doel - Foutvoorstel (3.3.3) {#purpose-error-suggestion}

Het doel van dit succescriterium is ervoor te zorgen dat gebruikers passende suggesties ontvangen voor het corrigeren van een invoerfout als dat mogelijk is. In de WCAG-definitie van [invoerfout](https://www.w3.org/TR/WCAG/#dfn-input-error) staat dat het gaat om &quot;informatie die door de gebruiker is verstrekt en die niet door het systeem wordt geaccepteerd&quot;. Voorbeelden van informatie die niet wordt geaccepteerd, zijn informatie die vereist is maar door de gebruiker wordt weggelaten en informatie die door de gebruiker wordt verstrekt maar die buiten de vereiste of toegestane gegevensindeling valt.

In criterium 3.3.1 van het succescriterium is voorzien in een foutmelding. Personen met cognitieve beperkingen kunnen het echter moeilijk vinden te begrijpen hoe de fouten moeten worden gecorrigeerd. Mensen met een visuele handicap kunnen wellicht niet precies uitzoeken hoe de fout kan worden gecorrigeerd. In het geval van een niet-succesvol verzonden formulier kunnen gebruikers het formulier verlaten omdat ze niet zeker weten hoe de fout kan worden gecorrigeerd, ook al weten ze dat deze is opgetreden.

De inhoudauteur kan de beschrijving van de fout verstrekken, of de gebruikersagent kan de beschrijving van de fout verstrekken die op technologie-specifieke, programmatically bepaalde informatie wordt gebaseerd.

#### Hoe kan ik-fout suggestie (3.3.3) {#how-to-meet-error-suggestion}

Volg de richtlijnen onder [Hoe te om Succes Criteria 3.3.3](https://www.w3.org/WAI/WCAG21/quickref/#error-suggestion)te ontmoeten.

#### Meer informatie - Foutmelding (3.3.3) {#more-information-error-suggestion}

* [Werken met succescriteria 3.3.3](https://www.w3.org/WAI/WCAG21/Understanding/error-suggestion.html)
* [Voldoen aan criteria 3.3.3](https://www.w3.org/WAI/WCAG21/quickref/#error-suggestion)

### Preventie van fouten (juridisch, financieel, gegevens) (3.3.4)  {#error-prevention-legal-financial-data}

* Succescriterium 3.3.4
* Niveau AA
* Foutpreventie (wettelijk, financieel, gegevens): Voor Web-pagina&#39;s die wettelijke verplichtingen of financiële transacties voor de gebruiker veroorzaken om voor te komen, die gebruiker-controleerbare gegevens in gegevensopslagsystemen wijzigen of schrappen, of die gebruikerstestreacties voorleggen, is minstens één van het volgende waar:

   * ReversibleSubmissions zijn omkeerbaar.
   * CheckedData die de gebruiker heeft ingevoerd, wordt gecontroleerd op invoerfouten en de gebruiker krijgt de gelegenheid deze te corrigeren.
   * BevestigdEr is een mechanisme beschikbaar voor het controleren, bevestigen en corrigeren van informatie voordat de verzending wordt voltooid.

#### Doel - Preventie van fouten (juridisch, financieel, gegevens) (3.3.4) {#purpose-error-prevention-legal-financial-data}

Dit succescriterium is bedoeld om gebruikers met een handicap te helpen ernstige gevolgen te voorkomen die het gevolg zijn van een fout bij het uitvoeren van een actie die niet ongedaan kan worden gemaakt. De aankoop van niet-terugvorderbare vliegtickets of het indienen van een bestelling voor de aankoop van aandelen op een makelaarsrekening zijn bijvoorbeeld financiële transacties met ernstige gevolgen. Als een gebruiker een fout heeft gemaakt op de datum van het luchtvervoer, zou hij of zij kunnen eindigen met een ticket voor de verkeerde dag die niet kan worden uitgewisseld. Indien de gebruiker een fout heeft gemaakt met betrekking tot het aantal te kopen aandelen, zou hij uiteindelijk meer aandelen kunnen kopen dan bedoeld. Beide soorten fouten hebben betrekking op transacties die onmiddellijk plaatsvinden en achteraf niet kunnen worden gewijzigd, en die zeer kostbaar kunnen zijn. Evenzo kan het een onherstelbare fout zijn als gebruikers per ongeluk gegevens wijzigen of verwijderen die zijn opgeslagen in een database waartoe ze later toegang moeten krijgen, zoals hun volledige reisprofiel op een website voor reisservices. Wanneer wordt verwezen naar het wijzigen of verwijderen van gegevens die door de gebruiker kunnen worden gecontroleerd, is het de bedoeling te voorkomen dat er massaal gegevens verloren gaan, zoals het verwijderen van een bestand of record. Het is niet de bedoeling een bevestiging te vereisen voor elke sparen bevel of het eenvoudige creëren of uitgeven van documenten, verslagen of andere gegevens.

Gehandicapte gebruikers kunnen vaker fouten maken. Mensen met een leeshandicap kunnen nummers en letters omzetten en personen met een motorische handicap kunnen per ongeluk de toetsen raken. Door de mogelijkheid te bieden acties om te keren, kunnen gebruikers een fout corrigeren die ernstige gevolgen kan hebben. Het bieden van de capaciteit om informatie te herzien en te verbeteren geeft de gebruiker de kans om een fout te ontdekken alvorens een actie te ondernemen die ernstige gevolgen heeft.

Door de gebruiker te controleren gegevens zijn door de gebruiker te bekijken gegevens die de gebruiker via een opzettelijke handeling kan wijzigen en/of verwijderen. Voorbeelden van de gebruiker die dergelijke gegevens beheert, zijn het bijwerken van het telefoonnummer en het adres van de account van de gebruiker of het verwijderen van een record met facturen uit het verleden van een website. Het verwijst niet naar zaken zoals Internet logboeken en onderzoeksmotor controlegegevens die de gebruiker niet kan bekijken of met direct in wisselwerking staan.

#### Hoe te om te ontmoeten - de Preventie van de Fout (Juridisch, Financieel, Gegevens) (3.3.4) {#how-to-meet-error-prevention-legal-financial-data}

Volg de richtlijnen onder [Hoe te om Succes Criteria 3.3.4](https://www.w3.org/WAI/WCAG21/quickref/#error-prevention-legal-financial-data)te ontmoeten.

#### Meer informatie - Foutpreventie (juridisch, financieel, gegevens) (3.3.4) {#more-information-error-prevention-legal-financial-data}

* [Werken met succescriteria 3.3.4](https://www.w3.org/WAI/WCAG21/Understanding/error-prevention-legal-financial-data.html)
* [Voldoen aan criteria 3.3.4](https://www.w3.org/WAI/WCAG21/quickref/#error-prevention-legal-financial-data)

## Beginsel 4: Robuust {#principle-robust}

[Beginsel 4: Robuust - De inhoud moet robuust genoeg zijn dat het door een grote verscheidenheid van gebruikersagenten, met inbegrip van hulptechnologieën kan worden geïnterpreteerd.](https://www.w3.org/TR/WCAG/#robust)

### Compatibel (4.1) {#compatible}

[Richtsnoer 4.1 Compatibel met: Maximaliseer verenigbaarheid met huidige en toekomstige gebruikersagenten, met inbegrip van ondersteunende technologieën.](https://www.w3.org/TR/WCAG/#compatible)

Maximaliseer verenigbaarheid met huidige en toekomstige gebruikersagenten, met inbegrip van ondersteunende technologieën.

### Parseren (4.1.1)  {#parsing}

* Succescriterium 4.1.1
* Niveau A
* Parseren: In inhoud die is geïmplementeerd met behulp van opmaaktalen, hebben elementen volledige start- en eindtags, worden elementen genest volgens hun specificaties, bevatten elementen geen dubbele kenmerken en zijn alle id&#39;s uniek, behalve wanneer de specificaties deze functies toestaan.

#### Doel - Parseren (4.1.1) {#purpose-parsing}

Het doel van dit succescriterium is ervoor te zorgen dat gebruikersagenten, inclusief ondersteunende hulpmiddelen, inhoud nauwkeurig kunnen interpreteren en parseren. Als de inhoud niet in een gegevensstructuur kan worden geparseerd, dan kunnen de verschillende gebruikersagenten het anders voorstellen of volledig onbekwaam zijn om het te ontleden. Sommige gebruikersagenten gebruiken &quot;reparatietechnieken&quot;om slecht gecodeerde inhoud terug te geven.

Aangezien de reparatietechnieken tussen gebruikersagenten variëren, kunnen de auteurs niet veronderstellen dat de inhoud nauwkeurig in een gegevensstructuur zal worden geparseerd of dat het correct door gespecialiseerde gebruikersagenten, met inbegrip van hulptechnologieën zal worden teruggegeven, tenzij de inhoud volgens de regels die in de formele grammatica voor die technologie worden bepaald wordt gecreeerd. In opmaaktalen leiden fouten in de element- en kenmerksyntaxis en het niet op de juiste manier leveren van geneste start- en eindtags tot fouten die ervoor zorgen dat gebruikersagents de inhoud niet betrouwbaar kunnen parseren. Daarom vereist het criterium van het Succes dat de inhoud kan worden geparseerd gebruikend slechts de regels van de formele grammatica.

#### Hoe kan ik-parseren (4.1.1) {#how-to-meet-parsing}

Volg de richtlijnen onder [Hoe kan ik voldoen aan criteria 4.1.1](https://www.w3.org/WAI/WCAG21/quickref/#parsing).

#### Meer informatie - parseren (4.1.1) {#more-information-parsing}

* [Werken met succescriteria 4.1.1](https://www.w3.org/WAI/WCAG21/Understanding/parsing.html)
* [Voldoen aan de criteria 4.1.1](https://www.w3.org/WAI/WCAG21/quickref/#parsing)

### Naam, Rol, Waarde (4.1.2)  {#name-role-value}

* Succescriterium 4.1.2
* Niveau A
* Naam, Rol, Waarde: Voor alle gebruikersinterfacecomponenten (inclusief maar niet beperkt tot: formulierelementen, koppelingen en componenten die door scripts zijn gegenereerd), de naam en de rol kunnen via programmacode worden bepaald; statussen, eigenschappen en waarden die door de gebruiker kunnen worden ingesteld, kunnen via programmacode worden ingesteld. en kennisgeving van wijzigingen in deze items is beschikbaar voor gebruikersagenten, waaronder ondersteunende hulpmiddelen.

#### Doel - Naam, Rol, Waarde (4.1.2) {#purpose-ame-role-value}

Het doel van dit criterium van Succes is ervoor te zorgen dat de Technologieën van de Hulpverlening (AT) informatie over kunnen verzamelen, activeren (of plaatsen) en bijgewerkt op de status van gebruikersinterfacecontroles in de inhoud houden.

Wanneer standaardcontroles van toegankelijke technologieën worden gebruikt, is dit proces ongecompliceerd. Als de elementen van de gebruikersinterface volgens de specificatie worden gebruikt, zal aan de voorwaarden van deze bepaling worden voldaan. (Zie voorbeelden van succescriterium 4.1.2 hieronder)

Als douanecontroles worden gecreeerd, echter, of de interface elementen (in code of manuscript) geprogrammeerd om een verschillende rol en/of een functie te hebben dan normaal, dan moeten de extra maatregelen worden genomen om ervoor te zorgen dat de controles belangrijke informatie aan hulptechnologieën verstrekken en zich om door ondersteunende technologieën laten worden gecontroleerd.

Een bijzonder belangrijke staat van een gebruikersinterfacecontrole is al dan niet het nadruk heeft. De nadrukstaat van een controle kan programmatically worden bepaald, en de berichten over verandering van nadruk worden verzonden naar gebruikersagenten en hulptechnologie. Andere voorbeelden van gebruikersinterfacecontrolestatus zijn of een selectievakje of een keuzerondje is geselecteerd, of al dan niet een inklapbare boom of lijstknoop wordt uitgebreid of samengevouwen.

#### Hoe te om te ontmoeten - Naam, Rol, Waarde (4.1.2) {#how-to-meet-ame-role-value}

Volg de richtlijnen onder [Hoe te om Succes Criteria 4.1.2](https://www.w3.org/WAI/WCAG21/quickref/#name-role-value)te ontmoeten.

#### Meer informatie - Naam, Rol, Waarde (4.1.2 {#more-information-ame-role-value}

* [Werken met succescriteria 4.1.2](https://www.w3.org/WAI/WCAG21/Understanding/name-role-value.html)
* [Voldoen aan de criteria 4.1.2](https://www.w3.org/WAI/WCAG21/quickref/#name-role-value)
