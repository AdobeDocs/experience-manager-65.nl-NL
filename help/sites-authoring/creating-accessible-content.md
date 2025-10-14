---
title: Toegankelijke inhoud voor Adobe Experience Manager maken (WCAG 2.1-compatibiliteit)
description: AEM gebruiken om webinhoud toegankelijk te maken voor en bruikbaar te maken voor personen met een handicap
exl-id: 2145d761-f51d-482b-a0e7-ef7500c4872f
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User,Admin,Architect,Developer
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '13636'
ht-degree: 2%

---

# Toegankelijke inhoud maken (WCAG 2.1-compatibiliteit) {#creating-accessible-content-wcag-conformance}

De [&#x200B; Richtlijnen van de Toegankelijkheid van de Inhoud van het Web van Web (WCAG) 2.1 &#x200B;](https://www.w3.org/TR/WCAG/), die door [&#x200B; een werkgroep van het Consortium van het World Wide Web &#x200B;](https://www.w3.org/groups/#Accessibility_Guidelines_Working_Group) wordt opgesteld, bestaan uit een reeks technologie-onafhankelijke richtlijnen en succescriteria helpen Web-inhoud toegankelijk maken voor, en bruikbaar voor, personen met handicaps.

Als inleiding geeft het consortium een reeks secties en ondersteunende documenten:

* [&#x200B; Nieuwe Eigenschappen in WCAG 2.1 &#x200B;](https://www.w3.org/TR/WCAG/#new-features-in-wcag-2-1)
* [&#x200B; hoe te WCAG 2.1 ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/)
* [&#x200B; Begrijpend WCAG 2.1 &#x200B;](https://www.w3.org/WAI/WCAG21/Understanding/)
* [&#x200B; Technieken voor WCAG 2.1 &#x200B;](https://www.w3.org/WAI/WCAG21/Techniques/)
* [&#x200B; de Documenten WCAG &#x200B;](https://www.w3.org/WAI/standards-guidelines/wcag/docs/)

Zie ook:
* De [&#x200B; Snelle Gids aan WCAG 2.1 &#x200B;](/help/managing/qg-wcag.md).
* De [&#x200B; rapporten van de Conformiteit van de Toegankelijkheid voor de oplossingen van de Adobe &#x200B;](https://www.adobe.com/accessibility/compliance.html).
* [De Rich Text Editor configureren voor het produceren van toegankelijke inhoud](/help/sites-administering/rte-accessible-content.md)

De richtlijnen worden ingedeeld volgens drie conformiteitsniveaus: Niveau A (laagste), Niveau AA en Niveau AAA (hoogste). De niveaus worden kort samengevat als volgt gedefinieerd:

* **Niveau A:** Uw site bereikt een minimaal basistoegankelijkheidsniveau. Om aan dit niveau te voldoen moet aan alle slagingscriteria voor Niveau A worden voldaan.
* **Niveau AA:** dit is een ideaal niveau van toegankelijkheid om voor te streven, waarin uw plaats een fundamenteel niveau van toegankelijkheid bereikt, zodat het voor de meeste mensen in de meeste situaties toegankelijk is gebruikend de meeste technologieën. Om aan dit niveau te voldoen moet aan alle slagingscriteria voor Niveau A en Niveau AA worden voldaan.
* **Niveau AAA:** Uw plaats bereikt een hoog niveau van toegankelijkheid. Om aan dit niveau te voldoen, worden alle criteria van Niveau A, Niveau AA, en van het Succes van Niveau AAA vervuld.

Wanneer u uw site maakt, moet u het algemene niveau bepalen waaraan u uw site wilt laten voldoen.

De volgende sectie stelt [&#x200B; lagen van WCAG 2.1 Richtlijnen &#x200B;](https://www.w3.org/TR/WCAG/#wcag-2-layers-of-guidance) met verwante succescriteria voor Niveau A en Niveau AA [&#x200B; conformiteitsniveaus &#x200B;](https://www.w3.org/TR/WCAG/#conformance-to-wcag-2-1) voor.

>[!NOTE]
>
>In dit document wordt het volgende gebruikt:
>
>* De [&#x200B; korte namen voor WCAG 2.1 Richtlijnen &#x200B;](https://www.w3.org/TR/WCAG/#wcag-2-layers-of-guidance).
>* De [&#x200B; nummering die in WCAG 2.1 Richtsnoeren &#x200B;](https://www.w3.org/TR/WCAG/#numbering-in-wcag-2-1) wordt gebruikt om kruisverwijzingen met de website van WCAG te helpen.

## Beginsel 1: Overdraagbaar {#principle-perceivable}

[&#x200B; Beginsel 1: Percieable - de Informatie en gebruikersinterfacecomponenten moeten aan gebruikers op manieren presenteerbaar zijn zij kunnen waarnemen.](https://www.w3.org/TR/WCAG/#perceivable)

### Alternatieven voor tekst (1.1) {#text-alternatives}

[&#x200B; Richtsnoer 1.1 Alternatieven van de Tekst: Verstrek tekstalternatieven voor om het even welke niet-tekstinhoud zodat het in andere vormen kan worden veranderd mensen, zoals grote druk, braille, toespraak, symbolen, of eenvoudigere taal nodig hebben.](https://www.w3.org/TR/WCAG/#text-alternatives)

### Niet-tekstuele inhoud (1.1.1) {#non-text-content}

* Succescriterium 1.1.1
* Niveau A
* Niet-tekstuele inhoud: alle niet-tekstuele inhoud die aan de gebruiker wordt aangeboden, heeft een tekstalternatief dat hetzelfde doel dient, behalve in de onderstaande situaties.

#### Doel - Niet-tekstuele inhoud (1.1.1) {#purpose-non-text-content}

Informatie op een webpagina kan in vele verschillende niet-tekstindelingen worden opgegeven, zoals afbeeldingen, video&#39;s, animaties, grafieken en grafieken. Mensen die blind zijn of een ernstige visuele handicap hebben, kunnen geen niet-tekstuele inhoud zien. Ze hebben echter wel toegang tot tekstinhoud door deze door een schermlezer te laten lezen of door een brailleweergaveapparaat in tactiele vorm te laten weergeven. Dus door tekstalternatieven voor inhoud in grafische indeling te bieden, kunnen mensen die de grafische inhoud niet kunnen zien, toegang krijgen tot een equivalente versie van de informatie die de inhoud biedt.

Een nuttig extra voordeel is dat tekstopties het mogelijk maken dat niet-tekstuele inhoud wordt geïndexeerd door zoekmachinetechnologie.

#### Ontmoeten - Niet-tekstuele inhoud (1.1.1) {#how-to-meet-non-text-content}

Voor statische afbeeldingen is het basisvereiste dat een equivalent tekstalternatief voor de afbeelding wordt geboden. Dit kan op het **Alternatieve gebied van de Tekst** worden gedaan. Zie, bijvoorbeeld, het Beeld van de Component van de Kern **[&#128279;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/image.html?lang=nl-NL)**.

>[!NOTE]
>
>Sommige uit-van-de-doos Componenten van de Kern, zoals **[Carrousel &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/carousel.html?lang=nl-NL)** verstrekken geen **Alternatieve 4&rbrace; gebied van de Tekst om afwisselende tekstbeschrijvingen aan individuele beelden toe te voegen, hoewel er het** 6&rbrace; gebied van het Etiket **[(](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/carousel.html?lang=nl-NL#accessibility-tab)** lusje van de Toegankelijkheid) voor de volledige component is.**&#x200B;**
>
>Wanneer het uitvoeren van versies van deze voor uw AEM instantie, moet uw ontwikkelingsteam dergelijke componenten vormen om het `alt` attribuut te steunen zodat de auteurs het aan de inhoud (zie [&#x200B; Toevoegend Steun voor Extra Elementen en Attributen van de HTML &#x200B;](/help/sites-administering/rte-accessible-content.md#add-support-for-more-html-elements-and-attributes)) kunnen toevoegen.

AEM vereist het **Alternatieve** gebied van de Tekst dat door gebrek moet worden gevuld. Als het beeld puur decoratief is en de alternatieve tekst onnodig zou zijn, is het **Beeld decoratief** optie kan worden gecontroleerd.

#### Alternatieven voor goede tekst maken {#creating-good-text-alternatives}

Er zijn verschillende vormen van niet-tekstuele inhoud, zodat de waarde van het tekstoptie afhankelijk is van de rol die de afbeelding in de webpagina speelt. De volgende algemene regels voor duim zijn van toepassing:

* Alternatieven voor tekst moeten beknopt zijn, maar toch duidelijk aangeven welke essentiële informatie door de niet-tekstuele inhoud wordt verstrekt.
* Te lange beschrijvingen (meer dan 100 tekens) moeten worden vermeden. Als een tekstalternatief meer details vereist:
   * een korte beschrijving geven in de alternatieve tekst
   * en hebben een langere beschrijving in tekst elders op dezelfde pagina of in een aparte webpagina. Koppel deze afzonderlijke beschrijving door van de afbeelding een koppeling te maken of door een tekstkoppeling naast de afbeelding te plaatsen.
* Alternatieve tekst mag geen inhoud repliceren die in tekstvorm dichtbij op dezelfde pagina wordt geleverd. Houd er rekening mee dat veel afbeeldingen illustraties zijn van punten die al in de tekst van een pagina zijn opgenomen, zodat er mogelijk een gedetailleerd tekstalternatief bestaat.
* Als de niet-tekstinhoud een koppeling naar een andere pagina of een ander document is en er geen andere tekst deel uitmaakt van dezelfde koppeling, moet de alternatieve tekst voor de afbeelding de bestemming van de koppeling aangeven. De afbeelding mag niet worden beschreven.
* Als de niet-tekstuele inhoud zich in een knopelement bevindt en er geen tekst bestaat die deel uitmaakt van dezelfde knop, moet de alternatieve tekst van de afbeelding de functionaliteit van de knop aangeven. De afbeelding mag niet worden beschreven.
* Het is perfect acceptabel dat een afbeelding een lege (null) alternatieve tekst krijgt, maar alleen als de afbeelding geen alternatieve tekst nodig heeft. Het is bijvoorbeeld een puur decoratieve afbeelding of als de equivalente tekst voorkomt in de paginatekst.

<!--
The [W3C draft: HTML5 Techniques for providing useful text alternatives](https://dev.w3.org/html5/alt-techniques/) has more details and examples of appropriate alternative text provision for images of different types.
-->

Specifieke typen niet-tekstuele inhoud waarvoor tekstopties nodig zijn, zijn onder meer:

* Illustratieve foto&#39;s: dit zijn afbeeldingen van personen, objecten of plaatsen. Het is belangrijk om na te denken over de rol van de foto op de pagina en om de afbeeldingsinhoud te beschrijven, aangezien ondersteunende hulpmiddelen het elementtype aankondigen (bijvoorbeeld `graphic` of `image` ). Hierdoor kan de helderheid van het gebruik van `screenshot` of `illustration` in alternatieve tekstbeschrijvingen toenemen, maar dit hangt af van de context. Consistentie is een significante factor, een besluit zou voor een volledig auteursteam moeten worden genomen en dit wordt toegepast door de gebruikerservaring.
* Pictogrammen: dit zijn kleine pictogrammen (afbeeldingen) die specifieke informatie bevatten. Ze moeten consistent worden gebruikt op een pagina en site. Alle exemplaren van het pictogram op een pagina of site moeten hetzelfde korte en korte tekstalternatief hebben, tenzij dit leidt tot onnodige duplicatie van aangrenzende tekst.
* Grafieken en grafieken: deze vertegenwoordigen meestal numerieke gegevens. U kunt dus een alternatief voor tekst bieden door een korte samenvatting op te nemen van de belangrijkste trends die in de grafiek of afbeelding worden weergegeven. Indien noodzakelijk, ook verstrek een meer gedetailleerde beschrijving in tekst gebruikend het **1&rbrace; gebied van de Beschrijving &lbrace;op het** Geavanceerde **beeldeigenschappen tabel.** U kunt de brongegevens ook elders op de pagina of op de site in tabelvorm opgeven.
* Kaarten, diagrammen, stroomdiagrammen: voor afbeeldingen die ruimtelijke gegevens leveren (bijvoorbeeld om beschrijvende relaties tussen objecten of een proces te ondersteunen), zorgt u ervoor dat het sleutelbericht wordt aangeboden in tekstindeling en dat deze tekstinformatie bij elk gekoppeld gegevenspunt wordt geplaatst. Voor kaarten, die een volledig tekstequivalent verstrekken zal waarschijnlijk onpraktisch zijn, maar als de kaart als manier wordt verstrekt om mensen te helpen hun manier aan een bepaalde plaats vinden, dan kan de alternatieve tekst van het kaartafbeelding *Kaart van X* kort wijzen, dan richtingen aan die plaats elders in de pagina of door het **3&rbrace; gebied van de Beschrijving in het** Geavanceerde **lusje van de** component verstrekken **.**
* CAPTCHAs: Een CAPTCHA is a *volledig Geautomatiseerde Openbare Turing test om Computers en Humans Apart* te vertellen. Het is een veiligheidscontrole die op webpagina&#39;s wordt gebruikt om mensen van kwaadaardige software te onderscheiden, maar die toegankelijkheidsbarrières kan veroorzaken. Dit zijn afbeeldingen waarvoor gebruikers een beschrijving moeten geven van wat ze zien om een beveiligingstest te doorstaan. Het is niet mogelijk om een tekstalternatief voor de afbeelding te bieden, dus u moet alternatieve niet-grafische oplossingen overwegen. De W3C biedt een aantal suggesties, zoals:
   * Logische puzzels
   * Het gebruik van geluidsuitvoer in plaats van afbeeldingen
   * Beperkte gebruikaccounts en spamfilters.
* Achtergrondafbeeldingen: deze worden bereikt met CSS (Cascading Style Sheets) in plaats van met HTML. Dit betekent dat het niet mogelijk is een alternatieve tekstwaarde op te geven. Achtergrondafbeeldingen mogen daarom geen belangrijke tekstgegevens opleveren. Als dat het geval is, moet deze informatie ook in de paginatekst worden vermeld. Het is echter belangrijk dat een andere achtergrond wordt weergegeven wanneer de afbeelding niet kan worden weergegeven.

>[!NOTE]
>
>Er zou een aangewezen niveau van contrast tussen de achtergrond en de voorgrondtekst moeten zijn; dit wordt besproken meer in detail in [&#x200B; Contrast (Minimum) (1.4.3) &#x200B;](#contrast-minimum).

#### Meer informatie - Niet-tekstuele inhoud (1.1.1) {#more-information-non-text-content}

* [&#x200B; Begrijpend Criteria 1.1.1 van het Succes &#x200B;](https://www.w3.org/WAI/WCAG21/Understanding/non-text-content.html)
* [&#x200B; hoe te om Criteria 1.1.1 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#non-text-content)
* [&#x200B; W3C verklaring van en alternatieven aan CAPTCHAs &#x200B;](https://www.w3.org/TR/turingtest/)

<!--
* [W3C: HTML5 Techniques for providing useful text alternatives (draft)](https://dev.w3.org/html5/alt-techniques/)
-->

### Op tijd gebaseerde media (1.2) {#time-based-media}

[&#x200B; Richtsnoer 1.2 op tijd-gebaseerde Media: Verstrek alternatieven voor op tijd-gebaseerde media.](https://www.w3.org/TR/WCAG/#time-based-media)

Dit behandelt webinhoud die *op tijd-gebaseerd* is. Dit geldt voor inhoud die de gebruiker kan afspelen (zoals video, audio en geanimeerde inhoud) en die vooraf is opgenomen of een live stream.

### Alleen audio en alleen video (vooraf opgenomen) (1.2.1) {#audio-only-and-video-only-prerecorded}

* Succescriterium 1.2.1
* Niveau A
* Alleen audio en alleen video (vooraf opgenomen): Voor vooraf opgenomen media met alleen audio en vooraf opgenomen alleen video geldt het volgende, behalve wanneer de audio of video een media-alternatief is voor tekst en duidelijk als zodanig is gelabeld:
   * Vooraf opgenomen audio-slechts: Een alternatief voor op tijd-gebaseerde media wordt verstrekt die gelijkwaardige informatie voor vooraf opgenomen audio-slechts inhoud voorstelt.
   * Vooraf opgenomen alleen-video: ofwel een alternatief voor op tijd gebaseerde media, ofwel een audiotrack met gelijkwaardige informatie voor vooraf opgenomen alleen-video-inhoud.

#### Doel - Alleen audio en alleen video (vooraf opgenomen) (1.2.1) {#purpose-audio-only-and-video-only-prerecorded}

Toegankelijkheidsproblemen voor video en audio kunnen worden ondervonden door:

* Mensen met een visuele handicap zonder soundtrack of de soundtrack volstaat niet om hen te informeren over wat er in de video of animatie gebeurt;
* personen met een slechthorende werking of doof zijn, die de soundtrack niet kunnen horen;
* Mensen die de soundtrack kunnen horen, maar niet begrijpen wat er wordt gesproken (bijvoorbeeld omdat het in een taal staat die ze niet begrijpen).

Video of audio is mogelijk ook niet beschikbaar voor gebruikers die browsers gebruiken of apparaten die het afspelen van inhoud in specifieke media-indelingen, zoals Adobe Flash, niet ondersteunen.

Als u deze informatie in een andere indeling verstrekt, zoals tekst (of audio voor video zonder audio), kunt u deze toegankelijk maken voor mensen die geen toegang hebben tot de oorspronkelijke inhoud.

#### Ontmoeten - alleen audio en alleen video (vooraf opgenomen) (1.2.1) {#how-to-meet-audio-only-and-video-only-prerecorded}

* Als de inhoud vooraf opgenomen audio zonder video (zoals een podcast) is:
   * Geef een koppeling voor of na de inhoud op naar een teksttranscriptie van de audio-inhoud. De transcriptie moet een HTML-pagina zijn met een tekstequivalent van alle gesproken en belangrijke niet-gesproken inhoud, plus een indicatie van wie spreekt, een beschrijving van de instelling, spraakexpressies en een beschrijving van andere belangrijke audio.
* Als de inhoud een animatie of vooraf opgenomen video zonder audio is:
   * Een koppeling verschaffen vlak voor of na de inhoud naar een equivalente tekstbeschrijving van de informatie die door de video wordt verschaft
   * Of een equivalente audiobeschrijving in een veelgebruikte audio-indeling, zoals MP3.

>[!NOTE]
>
>Als de audio- of video-inhoud wordt aangeboden als alternatief voor inhoud die in een andere indeling op dezelfde webpagina bestaat, is mogelijk geen extra alternatief vereist.
>
>De richtlijnen, [&#x200B; Begrijpend WCAG 1.2.1 &#x200B;](https://www.w3.org/WAI/WCAG21/Understanding/audio-only-and-video-only-prerecorded.html), verstrekken verdere informatie.

Het invoegen van multimedia in AEM webpagina&#39;s lijkt op het invoegen van een afbeelding. Aangezien multimedia-inhoud echter veel meer is dan een stilstaand beeld, zijn er verschillende instellingen en opties om te bepalen hoe de multimedia wordt afgespeeld.

>[!NOTE]
>
>Wanneer u multimedia met informatieve inhoud gebruikt, moet u verbindingen aan alternatieven ook tot stand brengen. Als u bijvoorbeeld een teksttranscriptie wilt opnemen, maakt u een HTML-pagina waarop de transcriptie wordt weergegeven en voegt u vervolgens een koppeling toe naast of onder de audio-inhoud.

#### Meer informatie - alleen audio en alleen video (vooraf opgenomen) (1.2.1) {#more-information-audio-only-and-video-only-prerecorded}

* [&#x200B; Begrijpend Criteria 1.2.1 van het Succes &#x200B;](https://www.w3.org/WAI/WCAG21/Understanding/audio-only-and-video-only-prerecorded.html)
* [&#x200B; hoe te om Criteria 1.2.1 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#audio-only-and-video-only-prerecorded)

### Bijschriften (vooraf opgenomen) (1.2.2) {#captions-prerecorded}

* Succescriterium 1.2.2
* Niveau A
* Bijschriften (vooraf opgenomen): Bijschriften zijn beschikbaar voor alle vooraf opgenomen audio-inhoud in gesynchroniseerde media, behalve wanneer de media een media-alternatief voor tekst zijn en duidelijk als zodanig zijn gelabeld.

#### Doel - Bijschriften (vooraf opgenomen) (1.2.2) {#purpose-captions-prerecorded}

Mensen die doof of moeilijk te horen zijn, krijgen geen toegang tot audio-inhoud of hebben er grote moeite mee. Bijschriften zijn tekstequivalenten voor gesproken en niet-gesproken audio die op het juiste moment tijdens de video op het scherm worden weergegeven. Ze stellen mensen die de audio niet kunnen horen in staat te begrijpen wat er gebeurt.

#### Hoe kan ik-Bijschriften (vooraf opgenomen) (1.2.2) {#how-to-meet-captions-prerecorded}

Bijschriften kunnen:

* Openen: altijd zichtbaar wanneer de video wordt afgespeeld
* Gesloten: de ondertitels kunnen door de gebruiker worden in- of uitgeschakeld

Gebruik ondertiteling waar mogelijk, aangezien dit gebruikers de keus over of geeft om ondertitels te bekijken.

Voor gesloten titels, creeer en verstrek een gesynchroniseerd bijschriftdossier in een aangewezen formaat (zoals [&#x200B; SMIL &#x200B;](https://www.w3.org/AudioVideo/)) naast het videodossier (details over hoe te om dit te doen zijn voorbij het werkingsgebied van deze gids, maar wij hebben verbindingen aan sommige leerprogramma&#39;s onder [&#x200B; Meer Informatie - Bijschriften (Voorgeschreven) (1.2.2) &#x200B;](#more-information-captions-prerecorded) verstrekt). Zorg ervoor dat u een notitie opgeeft of schakel de functie Bijschrift in de videospeler in om gebruikers te laten weten dat ondertitels beschikbaar zijn voor de video.

Sluit de tekst in de videotrack in als u open bijschriften moet gebruiken. Dit kan worden bereikt met videobewerkingstoepassingen waarmee titels kunnen worden bedekt op de video.

#### Meer informatie - Bijschriften (vooraf opgenomen) (1.2.2) {#more-information-captions-prerecorded}

* [&#x200B; Begrijpend Criteria 1.2.2 van het Succes &#x200B;](https://www.w3.org/WAI/WCAG21/Understanding/captions-prerecorded.html)
* [&#x200B; hoe te om Criteria 1.2.2 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#captions-prerecorded)

<!--
* [W3C: Synchronized Multimedia](https://www.w3.org/AudioVideo/)
* [Captions, Transcripts, and Audio Descriptions - by WebAIM](https://webaim.org/techniques/captions/)
-->

### Audiobeschrijving of media-alternatief (vooraf opgenomen) (1.2.3) {#audio-description-or-media-alternative-prerecorded}

* Succescriterium 1.2.3
* Niveau A
* Audiobeschrijving of Media-alternatief (vooraf opgenomen): een alternatief voor op tijd gebaseerde media of audiobeschrijving van de vooraf opgenomen video-inhoud is beschikbaar voor gesynchroniseerde media, behalve wanneer de media een media-alternatief voor tekst zijn en duidelijk als zodanig zijn gelabeld.

#### Doel - Audio-beschrijving of Media-alternatief (vooraf opgenomen) (1.2.3) {#purpose-audio-description-or-media-alternative-prerecorded}

Mensen die blind of visueel gehandicapt zijn, ondervinden toegankelijkheidsbarrières als de informatie in een video of animatie alleen visueel wordt verstrekt, of als de soundtrack niet voldoende informatie biedt om te begrijpen wat er visueel gebeurt.

#### Hoe kan ik-audio-beschrijving of media-alternatief (vooraf opgenomen) (1.2.3) {#how-to-meet-audio-description-or-media-alternative-prerecorded}

Er zijn twee manieren om aan dit succescriterium te voldoen. Beide zijn acceptabel:

1. Neem een aanvullende audiobeschrijving op voor de video-inhoud. Dit kan op drie manieren worden bereikt:
   * Geef tijdens pauzes in het bestaande dialoogvenster informatie over wijzigingen in de scène die niet worden weergegeven als onderdeel van de bestaande audiotrack.
   * Geef een nieuwe, aanvullende en optionele audiotrack op die de oorspronkelijke soundtrack bevat, maar ook aanvullende audiogegevens over wijzigingen in de scène bevat.
      * De gebruikers kunnen tussen het bestaande audiospoor (dat *geen* audiobeschrijving) en het nieuwe audiospoor (dat ** bevat een audiobeschrijving) schakelen.
      * Dit voorkomt verstoring voor gebruikers die de aanvullende beschrijving niet nodig hebben.
   * Maak een tweede versie van de video-inhoud voor uitgebreide audiobeschrijvingen. Dit vermindert de moeilijkheden verbonden aan het verstrekken van gedetailleerde audiobeschrijvingen binnen de hiaten tussen bestaande dialoog, door de audio en video op aangewezen punten tijdelijk te pauzeren. Hierdoor kan een veel langere audiobeschrijving worden gegeven voordat de handeling opnieuw wordt gestart. Zoals in het vorige voorbeeld, is dit best verstrekt als facultatieve extra audiospoor om verstoring voor gebruikers te verhinderen die niet de extra beschrijving nodig hebben.
1. Verstrek een tekstranscriptie die een geschikt tekstequivalent van de audio en visuele elementen van de video of de animatie is. Dit moet, indien van toepassing, een indicatie bevatten van wie spreekt, een beschrijving van de instelling, gebeurtenissen, of visueel gepresenteerde informatie en mondelinge expressies. Afhankelijk van de lengte kunt u de transcriptie op dezelfde pagina plaatsen als de video of animatie, of op een aparte pagina. Als u de laatste optie kiest, moet u een koppeling naar de transcriptie naast de video of animatie opgeven.

Exacte details over het maken van video met audioverichting vallen buiten het bereik van deze handleiding. Het maken van video&#39;s en audiobeschrijvingen kan tijdrovend zijn, maar andere producten van de Adobe kunnen u helpen deze taken uit te voeren.

#### Meer informatie - Audio-beschrijving of Media-alternatief (vooraf opgenomen) (1.2.3) {#more-information-audio-description-or-media-alternative-prerecorded}

* [&#x200B; Begrijpend Criteria 1.2.3 van het Succes &#x200B;](https://www.w3.org/WAI/WCAG21/Understanding/audio-description-or-media-alternative-prerecorded.html)
* [&#x200B; hoe te om Criteria 1.2.3 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#audio-description-or-media-alternative-prerecorded)

<!--
* [Adobe Encore](https://www.adobe.com/products/encore.html) - a DVD authoring software tool
-->

### Bijschriften (live) (1.2.4)  {#captions-live}

* Succescriterium 1.2.4
* Niveau AA
* Bijschriften (live): Bijschriften worden geleverd voor alle live audio-inhoud in gesynchroniseerde media.

#### Doel - Bijschriften (live) (1.2.4) {#purpose-captions-live}

Dit succescriterium is identiek aan [&#x200B; (Vooraf opgenomen) Bijschriften &#x200B;](#captions-prerecorded) in die zin dat het toegankelijkheidsbarrières richt die door mensen worden ervaren die doof of slechthorend zijn, behalve dat dit succescriterium levende presentaties zoals webcasts behandelt.

#### Hoe kan ik-Bijschriften (live) ontmoeten (1.2.4) {#how-to-meet-captions-live}

Volg de begeleiding voor [&#x200B; (Vooraf opgenomen) Bijschriften &#x200B;](#captions-prerecorded) hierboven wordt verstrekt die. Gezien de levende aard van de media moet er echter zo snel mogelijk een bijschriftvoorziening worden gecreëerd, als reactie op wat er gebeurt. Daarom zou u het gebruiken van ondertiteling in real time of toespraak-aan-tekst hulpmiddelen moeten overwegen.

Gedetailleerde instructies vallen buiten het bereik van dit document, maar de volgende bronnen bieden nuttige informatie:

* [&#x200B; WebAIM: Echt - tijd het Behouden &#x200B;](https://webaim.org/techniques/captions/realtime)

* [&#x200B; AccessComputing project (Universiteit van Washington): Kan de titels automatisch worden geproduceerd gebruikend toespraakerkenning?](https://www.washington.edu/accesscomputing/can-captions-be-generated-automatically-using-speech-recognition)

#### Meer informatie - Bijschriften (live) (1.2.4) {#more-information-captions-live}

* [&#x200B; Begrijpend Criteria 1.2.4 van het Succes &#x200B;](https://www.w3.org/WAI/WCAG21/Understanding/captions-live.html)
* [&#x200B; hoe te om Criteria 1.2.4 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#captions-live)

### Audiobeschrijving (vooraf opgenomen) (1.2.5)  {#audio-description-prerecorded}

* Succescriterium 1.2.5
* Niveau AA
* Audiobeschrijving (vooraf opgenomen): audiobeschrijving is beschikbaar voor alle vooraf opgenomen video-inhoud in gesynchroniseerde media.

#### Doel - Audiobeschrijving (vooraf opgenomen) (1.2.5) {#purpose-audio-description-prerecorded}

Dit succescriterium is identiek aan [&#x200B; AudioBeschrijving of Alternatief van Media (vooraf opgenomen) &#x200B;](#audio-description-or-media-alternative-prerecorded), behalve dat de auteurs een veel gedetailleerdere audiobeschrijving moeten verstrekken om met Niveau AA in overeenstemming te zijn.

#### Hoe kan ik-audiobeschrijving (vooraf opgenomen) (1.2.5) {#how-to-meet-audio-description-prerecorded}

Volg de begeleiding die voor [&#x200B; wordt verstrekt AudioBeschrijving of Alternatief van Media (vooraf opgenomen) &#x200B;](#audio-description-or-media-alternative-prerecorded).

#### Meer informatie - Audio-beschrijving (vooraf opgenomen) (1.2.5) {#more-information-audio-description-prerecorded}

* [&#x200B; Begrijpend Criteria 1.2.5 van het Succes &#x200B;](https://www.w3.org/WAI/WCAG21/Understanding/audio-description-prerecorded.html)
* [&#x200B; hoe te om Criteria 1.2.5 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#audio-description-prerecorded)

### Aanpasbaar (1.3) {#adaptable}

[&#x200B; Richtsnoer 1.3 Aangepast: creeer inhoud die op verschillende manieren (bijvoorbeeld, eenvoudigere lay-out) zonder het verliezen van informatie of structuur kan worden voorgesteld.](https://www.w3.org/TR/WCAG/#adaptable)

Dit richtsnoer heeft betrekking op de vereisten die nodig zijn ter ondersteuning van personen die:

* Het is mogelijk dat u geen toegang hebt tot informatie zoals deze door een auteur wordt weergegeven in de standaardpresentatie van die inhoud (bijvoorbeeld een lay-out met meerdere kolommen of een pagina met veel gebruik van kleur en/of afbeeldingen).

* kan alleen-audio of een andere visuele weergave gebruiken, zoals grote tekst of een hoog contrast.

### Informatie en relaties (1.3.1)  {#info-and-relationships}

* Succescriterium 1.3.1
* Niveau A
* Info en relaties: informatie, structuur en relaties die via presentatie worden overgebracht, kunnen via programmacode worden bepaald of zijn beschikbaar in tekst.

#### Doel - Informatie en relaties (1.3.1) {#purpose-info-and-relationships}

Vele ondersteunende technologieën die door mensen met handicaps worden gebruikt baseren zich op structurele informatie om ** inhoud effectief te tonen of te begrijpen. Deze structuurinformatie kan de vorm hebben van paginakoppen, tabelrij- en kolomkoppen en lijsttypen. Een schermlezer kan een gebruiker bijvoorbeeld in staat stellen van kop naar kop door een pagina te navigeren. Wanneer pagina-inhoud echter alleen via visuele opmaak lijkt te zijn gestructureerd in plaats van via de onderliggende HTML, is er geen structurele informatie beschikbaar voor ondersteunende hulpmiddelen, waardoor deze minder geschikt zijn om eenvoudiger te kunnen bladeren.

Dit succescriterium bestaat om ervoor te zorgen dat dergelijke structurele informatie programmatically door HTML, of andere coderingstechnieken wordt verstrekt, zodat browsers en hulptechnologieën tot de informatie kunnen toegang hebben en voordeel kunnen halen.

#### Hoe te om te ontmoeten - Informatie en Verband (1.3.1) {#how-to-meet-info-and-relationships}

AEM maakt het eenvoudig semantisch betekenisvolle webinhoud samen te stellen met de juiste HTML-elementen. Open uw paginainhoud in RTE (een component van de Tekst), en gebruik het **Paraformat** menu (paragraafsymbool) om het aangewezen structurele element (bijvoorbeeld, paragraaf en rubriek) te specificeren.

U kunt ervoor zorgen dat uw webpagina&#39;s de juiste structuur krijgen door, waar van toepassing, de volgende elementen te gebruiken:

* **Koppen:** zolang u de toegankelijkheidseigenschappen van toegelaten RTE hebt, AEM biedt drie niveaus van paginakop aan. U kunt deze gebruiken om secties en subsecties van content te identificeren. Kop 1 is het hoogste niveau van koptekst, kop 3 het laagste. De systeembeheerder kan het systeem configureren om het gebruik van meer kopniveaus toe te staan.

* **Lijsten**: U kunt HTML gebruiken om drie verschillende soorten lijsten te specificeren:
   * Het element `<ul>` wordt gebruikt voor *ongeordende* lijsten (met opsommingstekens). Afzonderlijke lijstitems worden geïdentificeerd met behulp van het element `<li>` . In RTE, gebruik het **pictogram van de Lijst van de Opsommingstekens**.
   * Het `<ol>` element wordt gebruikt voor *genummerde* lijsten. Afzonderlijke lijstitems worden geïdentificeerd met behulp van het element `<li>` . In RTE, gebruik het **Genummerde pictogram van de Lijst**.

  Als u bestaande inhoud wilt wijzigen in een specifiek lijsttype, markeert u de desbetreffende tekst en selecteert u het gewenste lijsttype. Zoals in het vorige voorbeeld wordt getoond hoe de paragraaftekst wordt ingegaan, worden de aangewezen lijstelementen automatisch toegevoegd aan uw HTML.

  In de volledige-schermmodus zijn de afzonderlijke pictogrammen **Lijst met opsommingstekens** en **Genummerde lijst** zichtbaar. Als de volledige-schermmodus niet is geactiveerd, zijn de twee opties beschikbaar achter het enkele pictogram **Lijsten**.

* **Lijsten**: De lijsten van gegevens moeten worden geïdentificeerd gebruikend de lijstelementen van HTML:
   * element one `<table>`
   * a `<tr>` -element voor elke rij van de tabel
   * a `<th>` element voor elke rij en kolomkop
   * a `<td>` -element voor elke gegevenscel

  Toegankelijke tabellen gebruiken ook de volgende elementen en kenmerken:

   * Het element `<caption>` wordt gebruikt om een zichtbaar bijschrift voor de tabel te maken. Bijschriften worden standaard gecentreerd boven de tabel weergegeven, maar kunnen op de juiste wijze worden geplaatst met CSS. Het bijschrift is via programmacode gekoppeld aan de tabel en is daarom een handige methode om inhoud te introduceren.
   * Het element `<summary>` helpt niet-waargenomen gebruikers om de informatie die in een tabel wordt gepresenteerd, gemakkelijker te begrijpen door een synopsis te geven van wat een waargenomen gebruiker kan zien. Dit is handig wanneer complexe of onconventionele tabellay-outs worden gebruikt (dit kenmerk wordt niet weergegeven in de browser, het wordt alleen voorgelezen naar ondersteunende hulpmiddelen).
   * Het kenmerk `scope` van het element `<th>` wordt gebruikt om aan te geven of een cel een koptekst voor een bepaalde rij of voor een bepaalde kolom vertegenwoordigt. Een vergelijkbare aanpak is het gebruik van de kenmerken header en id in complexe tabellen, waarbij gegevenscellen aan een of meer kopteksten kunnen worden gekoppeld.

  >[!NOTE]
  >
  >Door gebrek, zijn deze elementen en attributen niet direct beschikbaar, hoewel het voor de systeembeheerder mogelijk is om steun voor deze waarden in het **de dialoogvakje van de Eigenschappen van de Lijst toe te voegen** (zie [&#x200B; Toevoegend Steun voor Extra Elementen en Attributen van de HTML &#x200B;](/help/sites-administering/rte-accessible-content.md#add-support-for-more-html-elements-and-attributes).

  Om de **dialoog van de Lijst** te openen waar u de **Eigenschappen van de Lijst** tabel kunt selecteren:

   * Bepaal een aangewezen **Titel**.
   * U kunt het beste standaardwaarden voor **Breedte**, **Hoogte**, **Rand**, **Celopvulling** en **Celafstand** verwijderen aangezien deze eigenschappen in een globaal opmaakmodel kunnen worden ingesteld.

  U kunt de **Eigenschappen van het Cel** dan gebruiken om te kiezen of de cel een gegevens of kopbalcel is:

* **Nadruk**: Gebruik het `<strong>` of `<em>` element om nadruk te wijzen. Gebruik geen koppen om tekst in alinea&#39;s te markeren.
   * Markeer de tekst die u wilt benadrukken.
   * Klik het **B** pictogram (voor `<strong>`) of **I** pictogram (voor `<em>`) binnen het **wordt getoond Eigenschappen** paneel (zorg ervoor dat HTML wordt geselecteerd).

     >[!NOTE]
     >
     >RTE in een standaard AEM installatie is opstelling aan gebruik:
     >
     >* `<b>` for `<strong>`
     >* `<i>` for `<em>`
     >
     >Ze zijn in feite hetzelfde, maar `<strong>` en `<em>` hebben de voorkeur omdat ze semantisch correct HTML zijn. Uw ontwikkelingsteam kan de RTE zodanig configureren dat deze `<strong>` en `<em>` (in plaats van `<b>` en `<i>` ) gebruikt bij het ontwikkelen van uw projectinstantie.

* **de Complexe Lijsten van Gegevens**: Soms, waar er complexe lijsten met twee of meer niveaus van kopballen zijn, dan kunnen de basiseigenschappen van de Lijst niet genoeg zijn om alle structurele informatie noodzakelijk te verstrekken. Voor deze soorten complexe lijsten, moeten de directe verhoudingen tussen de kopballen en hun verwante cellen worden gecreeerd gebruikend de **kopbal** en **identiteitskaart** attributen.

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

  U bereikt dit in AEM door de markering rechtstreeks toe te voegen met de bronbewerkingsmodus.

  >[!NOTE]
  >
  >Deze functionaliteit is niet onmiddellijk beschikbaar in een standaardinstallatie. Het vereist configuratie van RTE, HTML regels, en serializer.

#### Meer informatie - Informatie en relaties (1.3.1) {#more-information-info-and-relationships}

* [&#x200B; Begrijpend Criteria 1.3.1 van het Succes &#x200B;](https://www.w3.org/WAI/WCAG21/Understanding/info-and-relationships.html)
* [&#x200B; hoe te om Criteria 1.3.1 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#info-and-relationships)

### Betekenisvolle reeks (1.3.2)  {#meaningful-sequence}

* Succescriterium 1.3.2
* Niveau A
* Betekenisvolle Reeks: wanneer de opeenvolging waarin de inhoud wordt voorgesteld zijn betekenis beïnvloedt, kan een correcte lezingsopeenvolging programmatically worden bepaald.

#### Doel - Betekenisvolle reeks (1.3.2) {#purpose-meaningful-sequence}

Dit succescriterium is bedoeld om een gebruikersagent in staat te stellen een alternatieve presentatie van inhoud te bieden en tegelijkertijd de leesvolgorde te behouden die nodig is om de betekenis te begrijpen. Het is belangrijk dat het mogelijk is om via programmacode minstens één sequentie van de inhoud te bepalen die zinvol is. Inhoud die niet voldoet aan dit criterium voor succes, kan gebruikers verwarren of desoriënteren wanneer ondersteunende hulpmiddelen de inhoud in de verkeerde volgorde lezen of wanneer alternatieve stijlpagina&#39;s of andere opmaakwijzigingen worden toegepast.

#### Hoe kan ik-betekenisvolle reeks (1.3.2) {#how-to-meet-meaningful-sequence}

Volg de richtlijnen onder [&#x200B; hoe te om Criteria 1.3.2 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#meaningful-sequence).

#### Meer informatie - Betekenisvolle reeks (1.3.2) {#more-information-meaningful-sequence}

* [&#x200B; Begrijpend Criteria 1.3.2 van het Succes &#x200B;](https://www.w3.org/WAI/WCAG21/Understanding/meaningful-sequence.html)
* [&#x200B; hoe te om Criteria 1.3.2 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#meaningful-sequence)

### Sensorische kenmerken (1.3.3)  {#sensory-characteristics}

* Succescriterium 1.3.3
* Niveau A
* Sensorische kenmerken: instructies voor het begrijpen en gebruiken van inhoud zijn niet uitsluitend gebaseerd op sensorische kenmerken van componenten zoals vorm, grootte, visuele locatie, oriëntatie of geluid.

#### Doel - Sensorische kenmerken (1.3.3) {#purpose-sensory-characteristics}

Ontwerpers richten zich vaak op visuele ontwerpfuncties, zoals kleur, vorm, tekststijl of de absolute of relatieve positie van een stuk inhoud wanneer ze informatie presenteren. Dit kunnen krachtige ontwerptechnieken zijn voor het overbrengen van informatie (en kunnen de algemene toegankelijkheid voor waargenomen gebruikers met cognitieve toegankelijkheidsbehoeften verbeteren), maar blinden of slechtzienden hebben mogelijk geen toegang tot informatie die visuele identificatie van kenmerken zoals positie, kleur of vorm vereist.

Ook informatie die onderscheid moet maken tussen verschillende geluiden (bijvoorbeeld mannelijke of vrouwelijke gesproken inhoud), vormt toegankelijkheidsbelemmeringen voor mensen met gehoorstoornissen, als deze informatie niet wordt weerspiegeld in een tekstalternatief voor de audio-inhoud.

>[!NOTE]
>
>Voor vereisten met betrekking tot alternatieven aan kleur, zie [&#x200B; Gebruik van Kleur &#x200B;](#use-of-color).

#### Voldoen aan sensorische kenmerken (1.3.3) {#how-to-meet-sensory-characteristics}

Zorg ervoor dat alle informatie die afhankelijk is van visuele kenmerken van pagina-inhoud, ook in een andere indeling wordt weergegeven.

* Vertrouw niet op de visuele positie om informatie te geven. Bijvoorbeeld, als u gebruikers naar een menu op de rechterkant van de pagina voor toegang tot verdere informatie wilt verwijzen, verwijs niet naar *het menu op het recht*; in plaats daarvan, noem het menu (bijvoorbeeld, als rubriek) en verwijs naar die naam in tekst.
* Vertrouw niet op tekstopmaak (bijvoorbeeld vette of cursieve tekst) als enige manier om informatie over te brengen.

>[!NOTE]
>
>Het gebruik van beschrijvende termen is acceptabel als ze in een niet-visuele context betekenis hebben. Bijvoorbeeld, zou het gebruiken van *hierboven* en *hieronder* over het algemeen aanvaardbaar zijn, aangezien zij inhoud vóór en na een bepaald punt van inhoud impliceren; dit zou nog steek houden wanneer de inhoud hardop wordt gesproken.

#### Meer informatie - Sensorische kenmerken (1.3.3) {#more-information-sensory-characteristics}

* [&#x200B; Begrijpend Criteria 1.3.3 van het Succes &#x200B;](https://www.w3.org/WAI/WCAG21/Understanding/sensory-characteristics.html)
* [&#x200B; hoe te om Criteria 1.3.3 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#sensory-characteristics)

### Doorneembaar (1.4) {#distinguishable}

[&#x200B; Richtsnoer 1.4 onderscheiden: Maak het voor gebruikers gemakkelijker om inhoud te zien en te horen die met inbegrip van het scheiden van voorgrond van achtergrond omvat.](https://www.w3.org/TR/WCAG/#distinguishable)

### Gebruik van kleur (1.4.1)  {#use-of-color}

* Succescriterium 1.4.1
* Niveau A
* Gebruik van Kleur: kleur wordt niet gebruikt als het enige visuele middel om informatie over te brengen, een actie te wijzen, een reactie te veroorzaken, of een visueel element te onderscheiden.

>[!NOTE]
>
>Dit succescriterium richt zich specifiek op kleurwaarneming. Andere vormen van perceptie worden behandeld in [&#x200B; Aangepast (1.3) &#x200B;](#adaptable); met inbegrip van programmatic toegang tot kleur en andere visuele presentatiecodes.

#### Doel - Gebruik van kleur (1.4.1) {#purpose-use-of-color}

Kleur is een effectieve manier om de esthetische aantrekkingskracht van webpagina&#39;s te verbeteren en is ook handig voor het overbrengen van informatie. Er is echter een reeks visuele beperkingen, van blindheid tot kleurstoornissen, wat betekent dat sommige mensen geen onderscheid kunnen maken tussen bepaalde kleuren. Hierdoor wordt kleurcodering een onbetrouwbare manier om informatie te verschaffen.

Zo kan bijvoorbeeld iemand met een rode-groene kleur een gebrek aan gezichtsvermogen hebben om onderscheid te maken tussen groene tinten en rode tinten. Beide kleuren worden mogelijk als een derde kleur (bijvoorbeeld bruin) weergegeven, waardoor ze geen onderscheid kunnen maken tussen rood, groen en bruin.

Kleuren kunnen ook niet worden waargenomen door mensen die alleen tekst weergeven, monochrome weergaveapparaten of een zwart-witafdruk van de pagina gebruiken.

Een verdere overweging is de *geselecteerde* staat voor een interfaceelement (bijvoorbeeld, lusjes, knevelknopen, onder anderen), die op één of andere manier buiten enkel met kleur en voorbij enkel een visuele presentatie moeten worden overgebracht. Voor dergelijke elementen is het extra gebruik van patronen, vormen en programmatische informatie nuttig bij het creëren van een volledig inclusieve gebruikerservaring die niet op een specifieke zin steunt.

#### Voldoen aan - gebruik van kleur (1.4.1) {#how-to-meet-use-of-color}

Telkens wanneer kleur wordt gebruikt om informatie over te brengen, zorg ervoor dat de informatie beschikbaar is zonder de behoefte om de kleur te zien.

Zorg er bijvoorbeeld voor dat informatie die door kleur wordt verschaft, ook expliciet in tekst wordt vermeld.

Wanneer kleur wordt gebruikt als een actiepunt om informatie te verschaffen, moet u een extra visuele aanwijzing opgeven, zoals het wijzigen van de stijl (bijvoorbeeld vet, cursief) of het lettertype. Dit helpt mensen met een laag gezichtsvermogen of die een kleurgezichtsgebrek hebben om de informatie te identificeren. Er kan echter niet volledig op worden vertrouwd, omdat het mensen die de pagina helemaal niet kunnen zien, niet helpt. Daarom is het (soms) nuttig om verborgen teksten te verstrekken of programmatic oplossingen, zoals de [&#x200B; Toegankelijke Rich Internet Applications (ARIA) reeks van Webnormen &#x200B;](https://www.w3.org/WAI/standards-guidelines/aria/) te gebruiken, om deze informatie aan niet-waargenomen gebruikers over te brengen.

#### Meer informatie - Gebruik van kleur (1.4.1) {#more-information-use-of-color}

* [&#x200B; Begrijpend Criteria 1.4.1 van het Succes &#x200B;](https://www.w3.org/WAI/WCAG21/Understanding/use-of-color.html)
* [&#x200B; hoe te om Criteria 1.4.1 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#use-of-color)

### Audiobesturing (1.4.2)  {#audio-control}

* Succescriterium 1.4.2
* Niveau A
* Audiobesturing: als audio op een webpagina automatisch langer dan 3 seconden wordt afgespeeld, is een mechanisme beschikbaar om de audio te onderbreken of te stoppen, of is een mechanisme beschikbaar om het audiovolume onafhankelijk van het algehele volumeniveau van het systeem te regelen.

#### Doel - Audiobesturing (1.4.2) {#purpose-audio-control}

Personen die schermleessoftware gebruiken, kunnen het moeilijk vinden om de spraakuitvoer te horen als er andere audio tegelijkertijd wordt afgespeeld. Deze moeilijkheid wordt verergerd wanneer de de toespraakoutput van de schermlezer op software-gebaseerd is (zoals de meesten vandaag zijn) en door de zelfde volumeregeling zoals het geluid wordt gecontroleerd. Ook kunnen sommige mensen met cognitieve handicaps en mensen die neurodivergerend zijn, een goede gevoeligheid hebben. Deze personen kunnen het volumeniveau van audio-inhoud niet wijzigen.

Daarom is het belangrijk dat de gebruiker het achtergrondgeluid kan uitschakelen.

>[!NOTE]
>
>Als u het volume wilt regelen, kunt u het volume tot nul terugbrengen.

#### Ontmoeten - Audiocontrole (1.4.2) {#how-to-meet-audio-control}

Volg de richtlijnen onder [&#x200B; hoe te om Criteria 1.4.2 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#audio-control).

#### Meer informatie - Audiobesturing (1.4.2) {#more-information-audio-control}

* [&#x200B; Begrijpend Criteria 1.4.2 van het Succes &#x200B;](https://www.w3.org/WAI/WCAG21/Understanding/audio-control.html)
* [&#x200B; hoe te om Criteria 1.4.2 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#audio-control)

### Contrast (minimaal) (1.4.3) {#contrast-minimum}

* Succescriterium 1.4.3
* Niveau AA
* Contrast (Minimum): de visuele presentatie van tekst en afbeeldingen van tekst heeft een contrastverhouding van ten minste 4,5:1, behalve voor de volgende:
   * Grote tekst: tekst op grote schaal en afbeeldingen van grote tekst hebben een contrastverhouding van ten minste 3:1.
   * Incidental: Tekst of beelden van tekst die deel van een inactieve gebruikersinterfacecomponent, [&#x200B; zuivere decoratie &#x200B;](https://www.w3.org/TR/WCAG/#dfn-pure-decoration) uitmaken, niet zichtbaar aan iedereen, of deel van een beeld uitmaken dat significante andere visuele inhoud bevat, hebben geen contrastvereiste.
   * Logotypes: tekst die deel uitmaakt van een logo of merknaam, heeft geen minimumvereiste voor contrast.

  >[!NOTE]
  >
  >Zie [&#x200B; Begrijpend Contrast van de Niet-Tekst &#x200B;](https://www.w3.org/WAI/WCAG21/Understanding/non-text-contrast.html) voor verdere informatie, helpen ervoor zorgen dat de inhoudsauteurs de extra vereisten rond niet-tekstelementen (met inbegrip van pictogrammen, interfaceelementen, onder anderen) begrijpen.

#### Doel - Contrast (minimaal) (1.4.3) {#purpose-contrast-minimum}

Mensen met een bepaalde visuele handicap kunnen mogelijk geen onderscheid maken tussen bepaalde kleurenparen met een laag contrast. Toegankelijkheidsproblemen kunnen optreden bij deze personen als:

* De tekst contrasteert slecht met de achtergrondkleur.
* De kleurcodering van tekst (zoals koppelingstekst en niet-koppelingstekst) is belangrijk voor het maken van onderscheid tussen gegevens.

>[!NOTE]
>
>Tekst die uitsluitend voor decoratiedoeleinden wordt gebruikt, valt niet onder dit succescriterium.

#### Hoe kan ik-contrast (minimaal) (1.4.3) {#how-to-meet-contrast-minimum}

Zorg ervoor dat de tekst voldoende contrasteert met de achtergrond. Contrastverhoudingen zijn afhankelijk van de grootte en de stijl van de desbetreffende tekst:

* Voor tekst met een grootte kleiner dan 18 punten (of 14 punten vet) moet de contrastverhouding tussen tekst/afbeeldingen van tekst en de achtergrond ten minste 4,5:1 zijn.
* Voor tekst die minimaal 18 punten (of 14 punten vet) groot is, moet de contrastverhouding ten minste 3:1 zijn.
* Als een achtergrond een patroon krijgt, moet de achtergrond rondom elke tekst worden gearceerd, zodat de verhouding van 4,5:1 of 3:1 behouden blijft.

>[!NOTE]
>
>Vergeet niet dat lettertypen kunnen verschillen in de manier waarop ze de equivalente PT/PX/EM-grootte weergeven.
>
>Gebruik een goede beoordeling en fout aan de kant van leesbaarheid en bruikbaarheid wanneer u de juiste lettertypen en grootten voor webinhoud selecteert.

>[!NOTE]
>
>De volgende sites kunnen u helpen bij conversies naar andere eenheden:
>
>* [&#x200B; px aan de Rekenmachine van Em - Omni &#x200B;](https://www.omnicalculator.com/conversion/px-to-em)
>* Zie &quot;Fontgrootteomzetting: pixel-point-em-rem-percent&quot; op `https://websemantics.uk/tools/font-size-conversion-pixel-point-em-rem-percent/`
>* Zie PMtoEM.com: PX naar EM conversie eenvoudig gemaakt op `http://pxtoem.com/`

Om contrastverhoudingen te controleren, gebruik een hulpmiddel van het kleurencontrast, zoals de [&#x200B; Analysator van het Contrast van de Kleur van de Groep Paciello &#x200B;](https://www.paciellogroup.com/resources/contrast-analyser.html) of de [&#x200B; controle van het kleurencontrast WebAIM &#x200B;](https://webaim.org/resources/contrastchecker/). Met deze gereedschappen kunt u kleurenparen controleren en contrastproblemen melden.

Als u zich minder zorgen maakt over het opgeven van de vormgeving van de pagina, kunt u er ook voor kiezen geen kleur voor de achtergrond en de voorgrondtekst op te geven. Er is geen controle op het contrast vereist, omdat de browser van de gebruiker de kleuren van de tekst en de achtergrond bepaalt.

Als het niet mogelijk is om aan de aanbevolen contrastniveaus te voldoen, geef dan een koppeling op naar een andere, equivalente versie van de pagina (die geen problemen met het kleurcontrast heeft). Of laat de gebruiker het contrast van het kleurenschema van de pagina aan hun eigen vereisten aanpassen.

#### Meer informatie - Contrast (minimaal) (1.4.3) {#more-information-contrast-minimum}

* [&#x200B; Begrijpend Criteria 1.4.3 van het Succes &#x200B;](https://www.w3.org/WAI/WCAG21/Understanding/contrast-minimum.html)
* [&#x200B; hoe te om Criteria 1.4.3 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#contrast-minimum)

### Tekst vergroten/verkleinen (1.4.4)  {#resize-text}

* Succescriterium 1.4.4
* Niveau A
* Tekst vergroten/verkleinen: behalve voor bijschriften en afbeeldingen van tekst kan de grootte van tekst zonder hulpprogramma tot 200 procent worden aangepast zonder dat inhoud of functionaliteit verloren gaat.

#### Doel - Tekst vergroten/verkleinen (1.4.4) {#purpose-resize-text}

De bedoeling van dit Criterium van Succes is ervoor te zorgen dat visueel teruggegeven tekst, met inbegrip van op tekst-gebaseerde controles (tekstkarakters die zijn getoond zodat zij [ tegenover tekstkarakters kunnen worden gezien die nog in gegevensvorm zoals ASCII ] zijn) met succes kunnen worden geschraapt zodat het direct door mensen met milde visuele handicaps kan worden gelezen, zonder het gebruik van hulptechnologie zoals een schermvergroting te vereisen. De gebruikers kunnen van het schrapen van al inhoud op de Web-pagina profiteren, maar de tekst is het meest kritiek.

#### Procedure - Formaat tekst wijzigen (1.4.4) {#how-to-meet-resize-text}

Naast het volgen van de richtlijnen onder [&#x200B; hoe te om Criteria 1.4.4 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#resize-text) kunt u inhoudsauteurs aanmoedigen om vloeistof, flexibele breedten, en hoogten in hun paginaontwerpen en doopvontgrootte (bijvoorbeeld, het Responsieve Ontwerp van het Web) te gebruiken om lezers de capaciteit toe te staan om tekst te resize.

#### Meer informatie - Tekst vergroten/verkleinen (1.4.4) {#more-information-resize-text}

* [&#x200B; Begrijpend Criteria 1.4.4 van het Succes &#x200B;](https://www.w3.org/WAI/WCAG21/Understanding/resize-text.html)
* [&#x200B; hoe te om Criteria 1.4.4 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#resize-text)

### Afbeeldingen van tekst (1.4.5) {#images-of-text}

* Succescriterium 1.4.5
* Niveau AA
* Afbeeldingen van tekst: als de gebruikte technologieën de visuele presentatie kunnen bereiken, wordt de tekst gebruikt om informatie over te brengen eerder dan beelden van tekst behalve het volgende:
   * Aanpasbaar: de afbeelding van tekst kan visueel worden aangepast aan de wensen van de gebruiker.
   * Essentieel: een bepaalde presentatie van de tekst is van essentieel belang voor de informatie die wordt doorgegeven.

>[!NOTE]
>
>Logotypen (tekst die deel uitmaakt van een logo of merknaam) worden als essentieel beschouwd.

#### Doel - Afbeeldingen van tekst (1.4.5) {#purpose-images-of-text}

Afbeeldingen van tekst worden vaak gebruikt wanneer de voorkeur wordt gegeven aan een bepaalde tekststijl, bijvoorbeeld een logo of tekst die is gegenereerd vanuit een andere bron (bijvoorbeeld een scan van een papieren document). In vergelijking met tekst in HTML en opgemaakt met CSS beschikken tekstafbeeldingen echter niet over de flexibiliteit om de grootte of weergave te wijzigen die nodig kan zijn voor mensen met een visuele handicap of leesproblemen.

#### Procedure - Afbeeldingen van tekst (1.4.5) {#how-to-meet-images-of-text}

Als afbeeldingen van tekst moeten worden gebruikt, gebruikt u CSS om de afbeeldingen van tekst te vervangen door equivalente tekst in HTML, zodat de tekst op een aanpasbare manier beschikbaar is. Voor een voorbeeld, zie [&#x200B; C30: Het gebruiken van CSS om tekst met beelden van tekst te vervangen en gebruikersinterfacecontroles te verstrekken om &#x200B;](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/C30) te schakelen.

#### Meer informatie - Afbeeldingen van tekst (1.4.5) {#more-information-images-of-text}

* [&#x200B; Begrijpend Criteria 1.4.5 van het Succes &#x200B;](https://www.w3.org/WAI/WCAG21/Understanding/images-of-text.html)
* [&#x200B; hoe te om Criteria 1.4.5 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#images-of-text)

## Beginsel 2: Werkbaar {#principle-operable}

[&#x200B; Beginsel 2: Operabel - de componenten van het gebruikersinterface en de navigatie moeten operabel zijn.](https://www.w3.org/TR/WCAG/#operable)

### Toegankelijk toetsenbord (2.1) {#keyboard-accessible}

[&#x200B; Richtsnoer 2.1 Toegankelijk Toetsenbord: Maak alle functionaliteit van een toetsenbord beschikbaar.](https://www.w3.org/TR/WCAG/#keyboard-accessible)

Hierbij wordt ervoor gezorgd dat gebruikers toegang hebben tot alle functionaliteit met een toetsenbord.

### Toetsenbord (2.1.1)  {#keyboard}

* Succescriterium 2.1.1
* Niveau A
* Toetsenbord: alle functionaliteit van de inhoud kan worden uitgevoerd via een toetsenbordinterface zonder specifieke tijdinstellingen voor afzonderlijke toetsaanslagen te vereisen, behalve wanneer de onderliggende functie invoer vereist die afhankelijk is van het pad van de beweging van de gebruiker en niet alleen van de eindpunten.

#### Doel - Toetsenbord (2.1.1) {#purpose-keyboard}

Het doel van dit succescriterium is ervoor te zorgen dat inhoud waar mogelijk kan worden gebruikt via een toetsenbord- of toetsenbordinterface (zodat een alternatief toetsenbord kan worden gebruikt). Wanneer de inhoud door een toetsenbord of afwisselend toetsenbord kan worden in werking gesteld, is het operabel door mensen zonder zicht (die geen apparaten zoals muizen kunnen gebruiken die oogcoördinatie vereisen) en door mensen die afwisselende toetsenborden of inputapparaten moeten gebruiken die als toetsenbordmededingers dienst doen. Toetsenbordemulators zijn onder andere spraakinvoersoftware, software voor sip-and-puff, toetsenborden op het scherm, scansoftware en diverse ondersteunende hulpmiddelen en alternatieve toetsenborden. Personen met een visuele handicap kunnen problemen ondervinden bij het bijhouden van een aanwijzer en het gebruik van software veel gemakkelijker (of alleen mogelijk) vinden als ze deze via het toetsenbord kunnen besturen.

#### Ontmoeten - Toetsenbord (2.1.1) {#how-to-meet-keyboard}

Volg de richtlijnen onder [&#x200B; hoe te om Criteria 2.1.1 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#keyboard).

#### Meer informatie - Toetsenbord (2.1.1) {#more-information-keyboard}

* [&#x200B; Begrijpend Criteria 2.1.1 van het Succes &#x200B;](https://www.w3.org/WAI/WCAG21/Understanding/no-keyboard-trap.html)
* [&#x200B; hoe te om Criteria 2.1.1 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#keyboard)

### Geen toetsenbordovervulling (2.1.2)  {#no-keyboard-trap}

* Succescriterium 2.1.2
* Niveau A
* Geen toetsenbordovervulling: als toetsenbordfocus naar een component van de pagina kan worden verplaatst met behulp van een toetsenbordinterface, kan de focus van die component worden verplaatst met alleen een toetsenbordinterface. Als hiervoor meer dan ongewijzigde pijl- of tabtoetsen of andere standaardafsluitmethoden nodig zijn, wordt de gebruiker op de hoogte gesteld van de methode om de focus weg te verplaatsen.

#### Doel - Geen toetsenbordovervulling (2.1.2) {#purpose-no-keyboard-trap}

De bedoeling van dit Criterium van Succes is ervoor te zorgen dat de inhoud *toetsenbordnadruk niet* overvult binnen subsecties van inhoud op een Web-pagina. Dit is een veelvoorkomend probleem wanneer meerdere indelingen worden gecombineerd binnen een pagina en worden weergegeven met insteekmodules of ingesloten toepassingen.

Het kan voorkomen dat de functionaliteit van de webpagina de focus beperkt tot een subsectie van de inhoud (bijvoorbeeld een modaal dialoogvenster). In dergelijke gevallen moet u een methode opgeven waarmee een gebruiker die subsectie van inhoud kan verlaten (met de ESC-toets wordt bijvoorbeeld het modale dialoogvenster gesloten of met de knop Sluiten sluit u het modale dialoogvenster).

#### Ontmoeten - Geen toetsenbordovervulling (2.1.2) {#how-to-meet-no-keyboard-trap}

Volg de richtlijnen onder [&#x200B; hoe te om Criteria 2.1.2 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#no-keyboard-trap).

#### Meer informatie - Geen toetsenbordovervulling (2.1.2) {#more-information-no-keyboard-trap}

* [&#x200B; Begrijpend Criteria 2.1.2 van het Succes &#x200B;](https://www.w3.org/WAI/WCAG21/Understanding/no-keyboard-trap.html)
* [&#x200B; hoe te om Criteria 2.1.2 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#no-keyboard-trap)

### Voldoende tijd (2.2) {#enough-time}

[&#x200B; Richtsnoer 2.2 genoeg Tijd: Verstrek gebruikers genoeg tijd om inhoud te lezen en te gebruiken.](https://www.w3.org/TR/WCAG/#enough-time)

Hierbij wordt ervoor gezorgd dat gebruikers voldoende tijd hebben om te lezen en actie te ondernemen.

### Aanpasbare timing (2.2.1)  {#timing-adjustable}

* Succescriterium 2.2.1
* Niveau A
* Toetsenbord: geef gebruikers voldoende tijd om inhoud te lezen en te gebruiken.

#### Doel - Aanpasbare timing (2.2.1) {#purpose-timing-adjustable}

Het doel van dit succescriterium is ervoor te zorgen dat gebruikers met een handicap voldoende tijd krijgen om waar mogelijk met webinhoud te communiceren. Personen met een handicap, zoals blindheid, slechtziendheid, motorische beperkingen en cognitieve beperkingen, hebben mogelijk meer tijd nodig om inhoud te lezen of functies uit te voeren zoals het invullen van online formulieren. Als de functies van het Web tijd-afhankelijk zijn, zal het voor sommige gebruikers moeilijk zijn om de vereiste actie uit te voeren alvorens een tijdgrens voorkomt. Hierdoor kan de service voor hen ontoegankelijk worden gemaakt. Het ontwerpen van functies die niet afhankelijk zijn van de tijd helpt mensen met een handicap deze functies te voltooien. Met opties voor het uitschakelen van tijdslimieten, het aanpassen van de tijdslimieten of het aanvragen van meer tijd voordat een tijdslimiet optreedt, kunnen gebruikers die meer tijd nodig hebben dan verwacht om taken te voltooien, gemakkelijker taken uitvoeren. Deze opties worden vermeld in de volgorde die het meest geschikt is voor de gebruiker. Het onbruikbaar maken van tijdslimieten is beter dan het aanpassen van de lengte van tijdslimieten, wat beter is dan het vragen van meer tijd alvorens een tijdslimiet voorkomt.

#### Hoe kan ik-timing aanpassen (2.2.1) {#how-to-meet-timing-adjustable}

Volg de richtlijnen onder [&#x200B; hoe te om Criteria 2.2.1 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#timing-adjustable).

#### Meer informatie - Aanpasbare timing (2.2.1) {#more-information-timing-adjustable}

* [&#x200B; Begrijpend Criteria 2.2.1 van het Succes &#x200B;](https://www.w3.org/WAI/WCAG21/Understanding/timing-adjustable.html)
* [&#x200B; hoe te om Criteria 2.2.1 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#timing-adjustable)

### Pauzeren, stoppen en verbergen (2.2.2)  {#pause-stop-hide}

* Succescriterium 2.2.2
* Niveau A
* Pauzeren, Stoppen, Verbergen: voor het verplaatsen, knipperen, schuiven of automatisch bijwerken van gegevens, geldt het volgende:
   * Verplaatsen, knipperen, schuiven: voor alle informatie over verplaatsen, knipperen of schuiven die
      * a) automatisch begint,
      * b) langer dan vijf seconden duurt, en
      * C) parallel met andere inhoud wordt aangeboden,
er een mechanisme is waarmee de gebruiker het kan onderbreken, stoppen of verbergen, tenzij de beweging, het knipperen of het schuiven deel uitmaakt van een activiteit waar dat essentieel is;
   * Automatisch bijwerken: voor automatisch bijwerken van gegevens die
      * a) automatisch begint, en
      * b) parallel met andere inhoud wordt aangeboden
er is een mechanisme waarmee de gebruiker de update kan onderbreken, stoppen of verbergen of de frequentie van de update kan bepalen, tenzij de automatische bijwerking deel uitmaakt van een activiteit waar dit essentieel is.

Opmerkingen zijn:

1. Zie Inhoud niet ontwerpen op een manier waarvan bekend is dat ze aanvallen veroorzaakt (2.3) voor vereisten met betrekking tot het flikkeren of knipperen van inhoud.
1. Aangezien inhoud die niet aan dit succescriterium voldoet, de mogelijkheid van een gebruiker om de hele pagina te gebruiken kan beïnvloeden, moet alle inhoud op de webpagina (ongeacht of deze wordt gebruikt om aan andere succescriteria te voldoen of niet) aan dit succescriterium voldoen. Zie [&#x200B; Vereiste van de Conformiteit 5: Niet-interferentie &#x200B;](https://www.w3.org/TR/WCAG20/#cc5).
1. Inhoud die regelmatig door software wordt bijgewerkt of naar de gebruikersagent wordt gestreamd, is niet verplicht informatie te bewaren of te presenteren die wordt gegenereerd of ontvangen tussen het begin van de pauze- en de hervattingspresentatie, aangezien dit technisch mogelijk is en in veel situaties misleidend kan zijn om dit te doen.
1. Een animatie die optreedt als onderdeel van een voorlaadfase of een vergelijkbare situatie, kan als essentieel worden beschouwd als er tijdens die fase geen interactie kan optreden voor alle gebruikers en als de voortgang niet wordt aangegeven, gebruikers in verwarring kan brengen of kan leiden tot het vermoeden dat de inhoud is bevroren of gebroken.

#### Doel - Pauzeren, Stoppen, Verbergen (2.2.2) {#purpose-pause-stop-hide}

Bepaalde gebruikers vinden mogelijk inhoud die beweegt afleidt, of zelfs fysiek pijnlijk, waardoor het moeilijk wordt om zich op andere delen van de pagina te concentreren. Bovendien kan dergelijke inhoud moeilijk leesbaar zijn voor mensen die moeite hebben met het bijhouden van bewegende tekst.

#### Ontmoeten - Pauzeren, Stoppen, Verbergen (2.2.2) {#how-to-meet-pause-stop-hide}

Afhankelijk van de aard van de inhoud kunt u een of meer van de volgende suggesties toepassen bij het maken van webpagina&#39;s met bewegende, knipperende of knipperende inhoud:

* Biedt een manier om schuivende inhoud te pauzeren zodat gebruikers voldoende tijd hebben om deze te lezen. Bijvoorbeeld nieuwstickers, automatisch bijgewerkte tekst en afbeeldingscarrousels die automatisch worden weergegeven.
* Zorg ervoor dat de inhoud die knippert na vijf seconden stopt met knipperen.
* Gebruik de juiste technologieën om bewegende of knipperende inhoud weer te geven die door de browser kan worden uitgeschakeld. Bijvoorbeeld Graphics Interchange Format (GIF) of Geanimeerde Portable Network Graphics (APNG)-bestanden.
* Geef een formulierbesturingselement op de webpagina zodat de gebruiker alle bewegende of knipperende inhoud op de pagina kan uitschakelen.
* Als een van de bovenstaande opties niet mogelijk is, geeft u een koppeling op naar een pagina die alle inhoud bevat, maar zonder verplaatsen of knipperen.

#### Meer informatie - Pauzeren, Stoppen, Verbergen (2.2.2) {#more-information-pause-stop-hide}

* [&#x200B; Begrijpend criterium van het Succes 2.2.2 &#x200B;](https://www.w3.org/WAI/WCAG21/Understanding/pause-stop-hide.html)
* [&#x200B; hoe te om Criterium 2.2.2 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#pause-stop-hide)

### Convulsies en fysieke reacties (2.3) {#seizures-and-physcial-reactions}

[&#x200B; Richtsnoer 2.3 Convulsies: Ontwerp geen inhoud op een manier die gekend is om aanvallen of fysieke reacties te veroorzaken.](https://www.w3.org/TR/WCAG/#seizures-and-physical-reactions)

### Drie Flash of onder de drempelwaarde (2.3.1) {#three-flashes-or-below-threshold}

* Succescriterium 2.3.1
* Niveau A
* Drie Flash of onder Drempel: de Web-pagina&#39;s bevatten niets die meer dan drie keer in om het even welke één-tweede periode knippert, of de flits is onder de algemene flits en rode flitsdrempels.

>[!NOTE]
>
>Omdat inhoud die niet aan dit succescriterium voldoet, de mogelijkheid van een gebruiker om de hele pagina te gebruiken kan beïnvloeden, moet alle inhoud op de webpagina (of deze nu wordt gebruikt om aan andere succescriteria te voldoen of niet) aan dit succescriterium voldoen. Zie [&#x200B; Vereiste van de Conformiteit 5: Niet-interferentie &#x200B;](https://www.w3.org/TR/WCAG/#cc5).

#### Doel - Drie Flash of onder de drempelwaarde (2.3.1) {#purpose-three-flashes-or-below-threshold}

In bepaalde gevallen kan knipperende inhoud fotosensitieve aanvallen veroorzaken. Aan de hand van dit succescriterium kunnen dergelijke gebruikers toegang krijgen tot alle inhoud en deze beleven zonder zich zorgen te maken over knipperende inhoud.

#### Hoe te om te ontmoeten - Drie Flash of onder Drempel (2.3.1) {#how-to-meet-three-flashes-or-below-threshold}

Ga als volgt te werk om ervoor te zorgen dat de volgende technieken worden toegepast:

* ervoor zorgen dat de onderdelen gedurende een periode van één seconde niet meer dan drie keer knipperen;
* Als de bovengenoemde voorwaarde niet kan worden voldaan aan, dan vertoning het opvlammen inhoud binnen a *klein veilig gebied* in pixel op het scherm. Dit gebied wordt berekend gebruikend een complexe formule, die in [&#x200B; G176 wordt behandeld: Het houden van het opvlammende gebied klein genoeg &#x200B;](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/G176), zodat zou deze techniek slechts moeten worden gevolgd als het opvlammen inhoud *necessary is.

#### Meer informatie - drie Flash of onder de drempelwaarde (2.3.1) {#more-information-three-flashes-or-below-threshold}

* [&#x200B; Begrijpend criterium van het Succes 2.3.1 &#x200B;](https://www.w3.org/WAI/WCAG21/Understanding/three-flashes-or-below-threshold.html)
* [&#x200B; hoe te om Criterium 2.3.1 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#three-flashes-or-below-threshold)

### Navigeerbaar (2.4) {#navigable}

[&#x200B; Richtsnoer 2.4 Navigable: Verstrek manieren om gebruikers te helpen navigeren, inhoud vinden, en bepalen waar zij zijn.](https://www.w3.org/TR/WCAG/#navigable)

Hiermee wordt ervoor gezorgd dat de inhoud eenvoudig en eenvoudig door de gebruikers kan worden genavigeerd.

### Blokken omzeilen (2.4.1)  {#bypass-blocks}

* Succescriterium 2.4.1
* Niveau A
* Blokken omzeilen: er is een mechanisme beschikbaar waarmee blokken inhoud die op meerdere webpagina&#39;s worden herhaald, worden overgeslagen.

#### Doel - Blokkeringen omzeilen (2.4.1) {#purpose-bypass-blocks}

De bedoeling van dit criterium van Succes is om mensen toe te staan die opeenvolgend door inhoud meer directe toegang tot de primaire inhoud van de Web-pagina navigeren. Webpagina&#39;s en toepassingen bevatten vaak inhoud die op andere pagina&#39;s of schermen wordt weergegeven. Voorbeelden van herhaalde blokken inhoud zijn onder andere, maar niet uitsluitend, navigatiekoppelingen, koptekstafbeeldingen, menu&#39;s en advertentiekaders. Kleine herhaalde secties zoals afzonderlijke woorden, woordgroepen of afzonderlijke koppelingen worden voor de toepassing van deze bepaling niet als blokken beschouwd.

#### Hoe te om te ontmoeten - Blokkeringen van de Omleiding (2.4.1) {#how-to-meet-bypass-blocks}

Volg de richtlijnen onder [&#x200B; hoe te om Criteria 2.4.1 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#bypass-blocks).

#### Meer informatie - Blokkeringen omzeilen (2.4.1) {#more-information-bypass-blocks}

* [&#x200B; Begrijpend Criteria 2.4.1 van het Succes &#x200B;](https://www.w3.org/WAI/WCAG21/Understanding/bypass-blocks.html)
* [&#x200B; hoe te om Criteria 2.4.1 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#bypass-blocks)

### Getitelde pagina (2.4.2)  {#page-titled}

* Succescriterium 2.4.2
* Niveau A
* Getitelde pagina: webpagina&#39;s hebben titels die het onderwerp of het doel beschrijven.

#### Doel - Getitelde pagina (2.4.2) {#purpose-page-titled}

Met dit succescriterium kan iedereen, ongeacht een bepaalde handicap, de inhoud van een webpagina snel identificeren zonder de pagina volledig te lezen. Dit is handig wanneer meerdere webpagina&#39;s op de tabbladen van de browser worden geopend, omdat de paginatitel op het tabblad wordt weergegeven en deze daarom snel kan worden gevonden.

#### Hoe kan ik-pagina getiteld (2.4.2) {#how-to-meet-page-titled}

Wanneer een nieuwe HTML-pagina wordt gemaakt in AEM, kunt u de paginatitel opgeven. Zorg ervoor dat de titel een adequate beschrijving geeft van de inhoud en het doel van de pagina, met name van eventuele unieke aspecten, zodat bezoekers snel kunnen zien of de inhoud relevant is voor hun behoeften.

U kunt de paginatitel ook bewerken tijdens het bewerken van een pagina. Deze kan worden geopend via **Pagina-informatie** - **Eigenschappen.**

#### Meer informatie - Getitelde pagina (2.4.2) {#more-information-page-titled}

* [&#x200B; Begrijpend criterium van het Succes 2.4.2 &#x200B;](https://www.w3.org/WAI/WCAG21/Understanding/page-titled.html)
* [&#x200B; hoe te om Criterium 2.4.2 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#page-titled)

### Focusvolgorde (2.4.3)  {#focus-order}

* Succescriterium 2.4.3
* Niveau A
* De Orde van de nadruk: Als een Web-pagina opeenvolgend kan worden genavigeerd en de navigatiereeksen betekenis of verrichting beïnvloeden, ontvangen de geconcentreerde componenten nadruk in een orde die betekenis en operabiliteit bewaart.

#### Doel - Activeringsvolgorde (2.4.3) {#purpose-focus-order}

Het doel van dit succescriterium is ervoor te zorgen dat gebruikers die opeenvolgend door inhoud navigeren, informatie tegenkomen in een volgorde die consistent is met de betekenis van de inhoud en vanaf het toetsenbord kunnen worden gebruikt. Dit vermindert verwarring door gebruikers een consistent mentaal model van de inhoud te laten vormen. Er kunnen verschillende volgorden zijn die logische verhoudingen in de inhoud weerspiegelen. Als u bijvoorbeeld componenten doorloopt in een onlineformulier dat uit meerdere velden en/of stappen bestaat, weerspiegelt u de logische relaties in de inhoud.

#### Hoe kan ik-focusvolgorde (2.4.3) {#how-to-meet-focus-order}

Volg de richtlijnen onder [&#x200B; hoe te om Criteria 2.4.3 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#focus-order).

#### Meer informatie - Activeringsvolgorde (2.4.3) {#more-information-focus-order}

* [&#x200B; Begrijpend Criteria 2.4.3 van het Succes &#x200B;](https://www.w3.org/WAI/WCAG21/Understanding/focus-order.html)
* [&#x200B; hoe te om Criteria 2.4.3 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#focus-order)

### Koppelingsdoel (in context) (2.4.4)  {#link-purpose-in-context}

* Succescriterium 2.4.4
* Niveau A
* Doel van koppeling (in context): het doel van elke koppeling kan worden bepaald op basis van alleen de koppelingstekst of van de koppelingstekst samen met de programmatisch bepaalde koppelingscontext, behalve wanneer het doel van de koppeling voor gebruikers in het algemeen ambigu zou zijn.

#### Doel - Koppelingsdoel (in context) (2.4.4) {#purpose-link-purpose-in-context}

Voor alle gebruikers, ongeacht de handicap, is het van essentieel belang dat duidelijk de richting van een koppeling wordt aangegeven door middel van de juiste koppelingstekst. Hierdoor kunnen gebruikers beter beslissen of ze een koppeling willen volgen. Voor zichtbare gebruikers is betekenisvolle koppelingstekst handig wanneer er meerdere koppelingen op een pagina staan (met name als de pagina veel tekst bevat), omdat betekenisvolle koppelingstekst een duidelijkere indicatie geeft van de functionaliteit van de doelpagina. Gebruikers van bepaalde ondersteunende hulpmiddelen, die een lijst met alle koppelingen op één pagina kunnen genereren, kunnen de koppelingstekst eenvoudiger uit hun context zien als die koppelingstekst uniek en informatief is. Zichtbare personen met cognitieve handicaps kunnen echter verward raken als een link niet voldoende informatie biedt om nauwkeurig te beschrijven waar de link hen naartoe brengt.

#### Hoe te om te ontmoeten - verbind Doel (in context) (2.4.4) {#how-to-meet-link-purpose-in-context}

Zorg er vooral voor dat het doel van een koppeling duidelijk wordt beschreven in de tekst van de koppeling.

* Onjuist voorbeeld:
   * Tekst: Klik hier voor meer informatie over onze avondlessen voor het najaar van 2010.
   * Reden: de bestemming wordt niet duidelijk en ondubbelzinnig aangegeven.
* Goed voorbeeld:
   * Tekst: Gebeurtenisklassen voor het najaar van 2010 - details.
   * Reden: door de tekst en de positie van het koppelingselement enigszins aan te passen, kan de koppelingstekst worden verbeterd:

Koppelingen moeten op alle pagina&#39;s consistent worden gephrasd, met name voor navigatiebalken. Bijvoorbeeld, als een verbinding aan een specifieke pagina **Publicaties** op één pagina wordt genoemd, gebruik die tekst op andere pagina&#39;s om consistentie te verzekeren.

Op het moment van schrijven zijn er enkele problemen met betrekking tot het gebruik van titelkenmerken om ervoor te zorgen dat vergelijkbare koppelingen op een pagina unieke informatie over de bestemming bieden (zo verwijst &quot;Meer lezen&quot; bijvoorbeeld vaak naar een reeks verschillende bestemmingen):

* Tekst in het titelkenmerk is alleen beschikbaar voor muisgebruikers als pop-upvenster met knopinfo en kan niet consistent worden benaderd via het toetsenbord of door mobiele gebruikers.
* Schermlezers kunnen titelkenmerken uitlezen, maar deze functionaliteit is mogelijk niet standaard ingeschakeld. Het is dus mogelijk dat gebruikers zich niet bewust zijn van het bestaan van een titelkenmerk.
* Het is moeilijk om de weergave van de titeltekst te wijzigen, wat betekent dat het moeilijk of onmogelijk kan zijn om door sommige mensen te lezen.

Dus terwijl het titelkenmerk kan worden gebruikt om extra context aan een koppeling te bieden, dient u zich bewust te zijn van de beperkingen ervan en deze niet te gebruiken als alternatief voor de juiste koppelingstekst.

Als de koppeling bestaat uit een afbeelding, controleert u of de alternatieve tekst voor de afbeelding de bestemming van de koppeling beschrijft. Bijvoorbeeld, als een beeld van een boekenkast als verbinding aan de publicaties van een persoon wordt geplaatst, zou de alternatieve tekst **de publicaties van John Smith** en niet **boekenkast** moeten lezen.

Als het koppelingsanker echter tekst bevat die het doel van de koppeling naast het afbeeldingselement beschrijft (en de tekst dus naast de afbeelding verschijnt), gebruikt u een leeg alt-kenmerk voor de afbeelding:

```xml
<a href="publications.html">
<img src = "bookshelf.jpg" alt = "" />
John Smith's publications
</a>
```

>[!NOTE]
>
>Het bovengenoemde fragment is een illustratie, wordt het geadviseerd om de **component van het Beeld** te gebruiken.

Hoewel het raadzaam is om koppelingstekst te geven die het doel van de koppeling aangeeft zonder dat er een extra context nodig is, wordt erkend dat dit niet altijd mogelijk is. De vrij verbindingen van de context kunnen in de volgende gevallen worden gebruikt, waarvan de voorbeelden van HTML in [&#x200B; worden gevonden hoe te om het Criterium 2.4.4 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#link-purpose-in-context).

* De koppelingstekst maakt deel uit van een lijst met nauw verwante koppelingen en wanneer het lijstitem dat de koppeling omsluit voldoende context biedt.
* Het doel van een verbinding kan duidelijk van de *voorafgaande* (niet het volgende) paragraaftekst worden geïdentificeerd.
* De koppeling is opgenomen in een gegevenstabel en het doel kan dus duidelijk worden aangegeven in de bijbehorende koppen.
* Een lijst met koppelingen is opgenomen in een aantal koppen en de kop zelf biedt een geschikte context.
* Een lijst met koppelingen is opgenomen in een geneste koppeling en het bovenliggende lijstitem boven de geneste koppeling biedt een geschikte context.

Soms, wanneer er meerdere koppelingen op een pagina staan (die elk de richting van een koppeling in complexe, maar noodzakelijke details aangeven), kan het aangewezen zijn een alternatieve versie van de webpagina op te geven die exact dezelfde inhoud weergeeft, maar waarbij de koppelingstekst niet zo gedetailleerd is.

U kunt ook scripts gebruiken, zodat er een minimale hoeveelheid tekst in de koppeling zelf is opgegeven. Bij het activeren van een aangewezen controle die aan de bovenkant van de pagina wordt geplaatst, wordt de verbindingstekst *uitgebreid* in verder detail. Een gelijkaardige benadering moet CSS gebruiken ** de volledige verbinding van waargenomen gebruikers verbergen, maar nog het volledig uitvoeren aan de gebruikers van de het schermlezer. Dit valt buiten het werkingsgebied van dit document, maar meer informatie over hoe dit kan worden bereikt kan in [&#x200B; worden gevonden Meer Informatie - verbind Doel (in Context) (2.4.4) &#x200B;](#more-information-link-purpose-in-context) sectie.

#### Meer informatie - Koppelingsdoel (in context) (2.4.4) {#more-information-link-purpose-in-context}

* [&#x200B; Begrijpend criterium van het Succes 2.4.4 &#x200B;](https://www.w3.org/WAI/WCAG21/Understanding/link-purpose-in-context.html)
* [&#x200B; hoe te om Criterium 2.4.4 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#link-purpose-in-context)

<!--
* [C7: Using CSS to hide a portion of the link text](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/C7)
-->

### Meerdere manieren (2.4.5)  {#multiple-ways}

* Succescriterium 2.4.5
* Niveau AA
* Meerdere manieren: er zijn meerdere manieren beschikbaar om een webpagina in een set webpagina&#39;s te zoeken, behalve wanneer de webpagina het resultaat is van of een stap in een proces.

#### Doel - Meerdere manieren (2.4.5) {#purpose-multiple-ways}

Het doel van dit succescriterium is dat gebruikers inhoud kunnen vinden op een manier die het best aansluit bij hun behoeften. Gebruikers kunnen een bepaalde techniek gemakkelijker of begrijpelijker gebruiken dan een andere.

Zelfs kleine sites moeten gebruikers enige oriëntatiemiddelen bieden. Voor een site met drie of vier pagina&#39;s, waarbij alle pagina&#39;s zijn gekoppeld vanaf de startpagina, is het mogelijk voldoende om koppelingen te verschaffen van en naar de startpagina, waar de koppelingen op de startpagina ook als een site-overzicht kunnen fungeren.

#### Hoe kan ik-op-meerdere manieren (2.4.5) {#how-to-meet-multiple-ways}

Volg de richtlijnen onder [&#x200B; hoe te om Criteria 2.4.5 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#multiple-ways).

#### Meer informatie - Meerdere manieren (2.4.5) {#more-information-multiple-ways}

* [&#x200B; Begrijpend Criteria 2.4.5 van het Succes &#x200B;](https://www.w3.org/WAI/WCAG21/Understanding/multiple-ways.html)
* [&#x200B; hoe te om Criteria 2.4.5 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#multiple-ways)

### Koppen en labels (2.4.6)  {#headings-and-labels}

* Succescriterium 2.4.6
* Niveau AA
* Koppen en labels: koppen en labels beschrijven het onderwerp of het doel.

#### Doel - Koppen en labels (2.4.6) {#purpose-headings-and-labels}

Het doel van dit criterium van Succes is gebruikers te helpen begrijpen welke informatie in Web-pagina&#39;s bevat en hoe die informatie wordt georganiseerd. Wanneer de koppen duidelijk en beschrijvend zijn, kunnen de gebruikers de informatie vinden zij gemakkelijker zoeken, en zij kunnen de verhouding tussen verschillende delen van de inhoud gemakkelijker begrijpen. Met beschrijvende labels kunnen gebruikers specifieke componenten in de inhoud identificeren.

#### Voldoen - Koppen en labels (2.4.6) {#how-to-meet-headings-and-labels}

Volg de richtlijnen onder [&#x200B; hoe te om Criteria 2.4.6 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#headings-and-labels).

#### Meer informatie - Koppen en labels (2.4.6) {#more-information-headings-and-labels}

* [&#x200B; Begrijpend Criteria 2.4.6 van het Succes &#x200B;](https://www.w3.org/WAI/WCAG21/Understanding/headings-and-labels.html)
* [&#x200B; hoe te om Criteria 2.4.6 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#headings-and-labels)

### Focus zichtbaar (2.4.7)  {#focus-visible}

* Succescriterium 2.4.7
* Niveau AA
* Focus zichtbaar: elke gebruikersinterface van een bedienbaar toetsenbord heeft een werkingsmodus waarin de focusindicator van het toetsenbord zichtbaar is.

#### Doel - Focus zichtbaar (2.4.7) {#purpose-focus-visible}

Het doel van dit succescriterium is om een persoon te helpen weten welk element de toetsenbordfocus heeft.

Het moet voor een persoon mogelijk zijn om te weten welk element onder veelvoudige elementen de toetsenbordnadruk heeft. Als er slechts één besturingselementen voor actioneren van het toetsenbord op het scherm zijn, is aan het succescriterium voldaan omdat het visuele ontwerp slechts één actionabel item voor het toetsenbord voorstelt.

Wanneer in het succescriterium &quot;wijze van exploitatie&quot; wordt vermeld, moet rekening worden gehouden met perrons die niet altijd een focusindicator kunnen weergeven. Gewoonlijk is er slechts één werkwijze, zodat deze succescriteria van toepassing zijn.

#### Hoe kan ik-Focus zichtbaar maken (2.4.7) {#how-to-meet-focus-visible}

Volg de richtlijnen onder [&#x200B; hoe te om Criteria 2.4.7 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#focus-visible).

#### Meer informatie - Focus zichtbaar (2.4.7) {#more-information-focus-visible}

* [&#x200B; Begrijpend Criteria 2.4.7 van het Succes &#x200B;](https://www.w3.org/WAI/WCAG21/Understanding/focus-visible.html)
* [&#x200B; hoe te om Criteria 2.4.7 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#focus-visible)

## Beginsel 3: begrijpelijk {#principle-understandable}

[&#x200B; Beginsel 3: Begrip - Informatie en de verrichting van gebruikersinterface moeten begrijpelijk zijn.](https://www.w3.org/TR/WCAG/#understandable)

### Tekstinhoud leesbaar en begrijpelijk maken (3.1) {#make-text-content-readable-and-understandable}

[&#x200B; Richtsnoer 3.1 Leesbaar: Maak tekstinhoud leesbaar en begrijpelijk.](https://www.w3.org/TR/WCAG/#readable)

### Taal van pagina (3.1.1) {#language-of-page}

* Succescriterium 3.1.1
* Niveau A
* Taal van pagina: de standaard menselijke taal van elke Web-pagina kan programmatically worden bepaald.

#### Doel - Taal van pagina (3.1.1) {#purpose-language-of-page}

Het doel van dit succescriterium is ervoor te zorgen dat tekst en andere taalkundige inhoud correct worden weergegeven. Voor gebruikers van schermlezers zorgt dit ervoor dat de inhoud correct wordt uitgedruct, terwijl visuele browsers eerder bepaalde tekensets correct zullen weergeven.

#### Hoe kan ik-taal van pagina (3.1.1) {#how-to-meet-language-of-page}

Om aan dit succescriterium te voldoen, kan de standaardtaal van een webpagina worden geïdentificeerd met het kenmerk `lang` in het element `<html>` boven aan de pagina. Bijvoorbeeld:

* Als een pagina in het Engels is geschreven, moet het element `<html>` als volgt worden gelezen:
  `<html lang = "en">`

* Overwegende dat voor een in het Spaans af te geven pagina de volgende norm moet worden vastgesteld:
  `<html lang = "es">`

In AEM, wordt de standaardtaal van uw pagina geplaatst wanneer het creëren van de pagina, maar kan ook worden veranderd wanneer het uitgeven van [&#x200B; Eigenschappen van de Pagina &#x200B;](/help/sites-authoring/editing-page-properties.md).

>[!NOTE]
>
>AEM biedt verdere verfijning voor variaties van een hoofdtaal, bijvoorbeeld Amerikaans Engels - en-us, Brits Engels - en-gb en Canadees Engels - en-ca. Dit detailniveau is vaak overbodig voor ondersteunende hulpmiddelen, maar kan worden gebruikt voor regionale variaties in pagina-inhoud.

#### Meer informatie - Taal van pagina (3.1.1) {#more-information-language-of-page}

* [&#x200B; Begrijpend criterium van het Succes 3.1.1 &#x200B;](https://www.w3.org/WAI/WCAG21/Understanding/language-of-page.html)
* [&#x200B; hoe te om Criterium 3.1.1 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#language-of-page)
* De codes zijn gebaseerd op ISO 639-1. Een uitgebreidere lijst van codes voor elke taal kan bij de [&#x200B; plaats van Scholen W3 &#x200B;](https://www.w3schools.com/tags/ref_language_codes.asp) worden gevonden.

### Taal van onderdelen (3.1.2)  {#language-of-parts}

* Succescriterium 3.1.2
* Niveau AA
* Taal van onderdelen: de menselijke taal van elke passage of uitdrukking in de inhoud kan via programmacode worden bepaald. Uitzonderingen zijn eigennamen, technische termen, woorden van onbepaalde taal en woorden of woordgroepen die deel zijn geworden van het woordenboek van de direct omliggende tekst.

#### Doel - Taal van onderdelen (3.1.2) {#purpose-language-of-parts}

Het doel van dit succescriterium is gelijkaardig aan het succescriterium [&#x200B; Taal van Pagina &#x200B;](#language-of-page), behalve dat het op Web-pagina&#39;s van toepassing is die inhoud in veelvoudige talen op één enkele pagina (bijvoorbeeld, wegens citaten of ongewone leningswoorden) bevatten.

Pagina&#39;s die dit succescriterium toepassen, maken het mogelijk:

* Braille-overgangssoftware voor het invoegen van tekens met accenten.
* Schermlezers spreken woorden uit die speciale tekens hebben of niet in de standaardtaal staan die op paginaniveau is geïdentificeerd.
* Vertaalgereedschappen zoals Google Vertalen om inhoud van de ene taal naar de andere te vertalen.

#### Hoe kan ik-taal van onderdelen (3.1.2) {#how-to-meet-language-of-parts}

Het kenmerk `lang` kan worden gebruikt om wijzigingen in de taal van de inhoud te identificeren. Een citaat in het Duits (ISO 639-1 code &quot;de&quot;) kan bijvoorbeeld als volgt worden weergegeven:

```xml
<blockquote cite = "John F. Kennedy" lang = "de">
     <p>Ich bin ein Berliner</p>
 </blockquote>
```

>[!NOTE]
>
>Blockquotes worden niet ondersteund in een out-of-the-box-instantie. Een aangepaste component kan worden ontwikkeld ter ondersteuning van de functie.

Op dezelfde manier kan de browser een ongewoon woord of ongebruikelijke woordgroep correct weergeven als het element `span` als volgt wordt gebruikt:

```xml
<p>The only French phrase I know is <span lang = "fr">je ne sais quoi</code>.</p>
```

>[!NOTE]
>
>Dit succescriterium hoeft niet te worden gevolgd wanneer namen of steden in verschillende talen worden opgenomen. Of, wanneer het gebruiken van leningswoorden of uitdrukkingen die algemeen in de standaardtaal, zoals *schadenfreude* in het Engels zijn geworden.

Om het spanwijdtelement, met een aangewezen taal toe te voegen, kunt u uw prijsverhoging van de HTML op de bron uitgeven wijze van RTE zodat het zoals hierboven leest. Alternatief kan het `lang` attribuut in RTE door een systeembeheerder worden omvat (zie [&#x200B; Toevoegend Steun voor Extra Elementen en Attributen van de HTML &#x200B;](/help/sites-administering/rte-accessible-content.md#add-support-for-more-html-elements-and-attributes)).

#### Meer informatie - Taal van onderdelen (3.1.2) {#more-information-language-of-parts}

* [&#x200B; Begrijpend criterium van het Succes 3.1.2 &#x200B;](https://www.w3.org/WAI/WCAG21/Understanding/language-of-parts.html)
* [&#x200B; hoe te om Criterium 3.1.2 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#language-of-parts)

### Voorspelbaar (3.2) {#predictable}

[&#x200B; Richtsnoer 3.2 voorspelbaar: Maak Web-pagina&#39;s verschijnen en werken op voorspelbare manieren.](https://www.w3.org/TR/WCAG/#predictable)

Hierbij wordt ervoor gezorgd dat de webpagina&#39;s er consistent uitzien en functioneren.

### Veld activeren (3.2.1)  {#on-focus}

* Succescriterium 3.2.1
* Niveau A
* Bij focus: wanneer een gebruikersinterfacecomponent focus krijgt, wordt er geen contextwijziging gestart.

#### Doel - Veld activeren (3.2.1) {#purpose-on-focus}

Het doel van dit succescriterium is ervoor te zorgen dat de functionaliteit voorspelbaar is wanneer bezoekers door een document navigeren. Elke component die een gebeurtenis kan activeren wanneer deze focus krijgt, mag de context niet wijzigen. Voorbeelden van het wijzigen van de context wanneer een component focus krijgt, zijn onder andere:

* formulieren die automatisch worden ingediend wanneer een component focus krijgt;
* nieuwe vensters die worden gestart wanneer een component focus krijgt;
* focus wordt gewijzigd in een andere component wanneer die component focus krijgt;

Focus kan naar een besturingselement worden verplaatst via het toetsenbord (bijvoorbeeld met Tab naar een besturingselement) of de muis (bijvoorbeeld door op een tekstveld te klikken). Als u de muis over een besturingselement beweegt, wordt de focus niet verplaatst, tenzij dit gedrag door scripts wordt geïmplementeerd. Voor sommige soorten controles, kan het klikken van een controle de controle (bijvoorbeeld, knoop) ook activeren, die, beurtelings, een verandering in context kan in werking stellen.

#### Hoe te om te ontmoeten - op Focus (3.2.1) {#how-to-meet-on-focus}

Volg de richtlijnen onder [&#x200B; hoe te om Criteria 3.2.1 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#on-focus).

#### Meer informatie - Veld activeren (3.2.1) {#more-information-on-focus}

* [&#x200B; Begrijpend Criteria 3.2.1 van het Succes &#x200B;](https://www.w3.org/WAI/WCAG21/Understanding/on-focus.html)
* [&#x200B; hoe te om Criteria 3.2.1 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#on-focus)

### Bij invoer (3.2.2)  {#on-input}

* Succescriterium 3.2.2
* Niveau A
* Bij Invoer: het wijzigen van de instelling van een gebruikersinterfacecomponent leidt niet automatisch tot een wijziging van de context, tenzij de gebruiker op de hoogte is gesteld van het gedrag voordat de component wordt gebruikt.

#### Doel - Aan-invoer (3.2.2) {#purpose-on-input}

Het doel van dit succescriterium is ervoor te zorgen dat het invoeren van gegevens of het selecteren van een formulierbesturingselement voorspelbare effecten heeft. Wanneer u de instelling van een gebruikersinterfacecomponent wijzigt, verandert u een aspect in het besturingselement dat blijft bestaan wanneer de gebruiker niet meer met het element communiceert. Als u dus een selectievakje inschakelt, tekst invoert in een tekstveld of de geselecteerde optie wijzigt in een lijstbesturingselement, wijzigt u de instelling, maar het activeren van een koppeling of een knop doet dit niet. Wijzigingen in context kunnen gebruikers verwarren die de wijziging niet gemakkelijk waarnemen of die gemakkelijk door wijzigingen worden afgeleid. Wijzigingen in de context zijn alleen geschikt wanneer duidelijk is dat een dergelijke wijziging plaatsvindt in reactie op de actie van de gebruiker.

#### Hoe kan ik-op-invoer (3.2.2) {#how-to-meet-on-input}

Volg de richtlijnen onder [&#x200B; hoe te om Criteria 3.2.2 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#on-input).

#### Meer informatie - Bij invoer (3.2.2) {#more-information-on-input}

* [&#x200B; Begrijpend Criteria 3.2.2 van het Succes &#x200B;](https://www.w3.org/WAI/WCAG21/Understanding/on-input.html)
* [&#x200B; hoe te om Criteria 3.2.2 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#on-input)

### Consistente navigatie (3.2.3)  {#consistent-navigation}

* Succescriterium 3.2.3
* Niveau AA
* Consistente navigatie: Navigatiemechanismen die op meerdere webpagina&#39;s binnen een set webpagina&#39;s worden herhaald, vinden in dezelfde relatieve volgorde plaats telkens wanneer ze worden herhaald, tenzij de gebruiker een wijziging aanbrengt.

#### Doel - Consistente navigatie (3.2.3) {#purpose-consistent-navigation}

Dit succescriterium is bedoeld om het gebruik van een consistente presentatie en lay-out aan te moedigen voor gebruikers die met herhaalde inhoud binnen een set webpagina&#39;s werken en die meer dan één keer specifieke informatie of functionaliteit moeten zoeken. Personen met een laag gezichtsvermogen die schermvergroting gebruiken om een klein gedeelte van het scherm tegelijk weer te geven, gebruiken vaak visuele aanwijzingen en paginagrenzen om snel herhaalde inhoud te vinden. Het presenteren van herhaalde inhoud in dezelfde volgorde is ook belangrijk voor visuele gebruikers die ruimtelijk geheugen of visuele aanwijzingen in het ontwerp gebruiken om herhaalde inhoud te zoeken.

Het gebruik van de uitdrukking &quot;zelfde orde&quot;in deze sectie is niet bedoeld om te impliceren dat de subnavigatiemenu&#39;s niet kunnen worden gebruikt of dat de blokken van secundaire navigatie of paginastructuur niet kunnen worden gebruikt. In plaats daarvan, is dit Criterium van Succes bedoeld om gebruikers bij te staan die met herhaalde inhoud over Web-pagina&#39;s in wisselwerking staan om de plaats van de inhoud te kunnen voorspellen zij zoeken. En om het sneller te vinden wanneer ze het weer tegenkomen.

Gebruikers kunnen een wijziging in de volgorde initiëren met behulp van adaptieve gebruikersagents of door voorkeuren in te stellen, zodat de informatie op een voor hen meest nuttige manier wordt weergegeven.

#### Ontmoeten - Consistente Navigatie (3.2.3) {#how-to-meet-consistent-navigation}

Volg de richtlijnen onder [&#x200B; hoe te om Criteria 3.2.3 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#consistent-navigation).

#### Meer informatie - Consistente navigatie (3.2.3) {#more-information-consistent-navigation}

* [&#x200B; Begrijpend Criteria 3.2.3 van het Succes &#x200B;](https://www.w3.org/WAI/WCAG21/Understanding/consistent-navigation.html)
* [&#x200B; hoe te om Criteria 3.2.3 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#consistent-navigation)

### Consistente identificatie (3.2.4)  {#consistent-identification}

* Succescriterium 3.2.4
* Niveau A
* Consistente identificatie: Componenten met dezelfde functionaliteit binnen een set webpagina&#39;s worden consistent geïdentificeerd.

#### Doel - Consistente identificatie (3.2.4) {#purpose-consistent-identification}

Het doel van dit succescriterium is ervoor te zorgen dat functionele componenten die herhaaldelijk in een set webpagina&#39;s voorkomen, op consistente wijze worden geïdentificeerd. Een strategie die mensen die het schermlezers gebruiken wanneer het werken van een Website moet zich zwaar op hun vertrouwdheid met functies baseren die op verschillende Web-pagina&#39;s kunnen verschijnen. Als de identieke functies verschillende etiketten (of, meer in het algemeen, een verschillende toegankelijke naam) op verschillende Web-pagina&#39;s hebben, is de plaats beduidend moeilijker te gebruiken. Het kan ook verwarrend zijn en de cognitieve belasting verhogen voor mensen met cognitieve beperkingen. Daarom helpt een consistente etikettering.

Deze consistentie geldt ook voor de alternatieven voor de tekst. Als pictogrammen of andere niet-tekstitems dezelfde functionaliteit hebben, moeten de alternatieven voor de tekst ook consistent zijn.

Als er twee componenten op een webpagina zijn die beide dezelfde functionaliteit hebben als een component op een andere pagina in een set webpagina&#39;s, moeten alle drie consistent zijn. De twee op dezelfde pagina zullen dus consistent zijn.

3.2.4 is weliswaar wenselijk en is altijd in overeenstemming met één webpagina, maar 3.2.4 gaat alleen over consistentie binnen een set webpagina&#39;s waar iets op meer dan één pagina in de set wordt herhaald.

#### Voldoen aan consistente identificatie (3.2.4) {#how-to-meet-consistent-identification}

Volg de richtlijnen onder [&#x200B; hoe te om Criteria 3.2.4 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#consistent-identification).

#### Meer informatie - Consistente identificatie (3.2.4) {#more-information-consistent-identification}

* [&#x200B; Begrijpend Criteria 3.2.4 van het Succes &#x200B;](https://www.w3.org/WAI/WCAG21/Understanding/consistent-identification.html)
* [&#x200B; hoe te om Criteria 3.2.4 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#consistent-identification)

### Invoerbijstand (3.3) {#input-assistance}

[&#x200B; Richtsnoer 3.3 de Hulp van de Input: De gebruikers van de hulp vermijden en verbeteren fouten.](https://www.w3.org/TR/WCAG/#input-assistance)

### Foutidentificatie (3.3.1)  {#error-identification}

* Succescriterium 3.3.1
* Niveau A
* Foutidentificatie: als er automatisch een invoerfout wordt gedetecteerd, wordt het foutbericht weergegeven en wordt de fout in de tekst aan de gebruiker beschreven.

#### Doel - Foutidentificatie (3.3.1) {#purpose-error-identification}

Dit succescriterium is bedoeld om ervoor te zorgen dat gebruikers weten dat er een fout is opgetreden en kunnen bepalen wat fout is. Het foutbericht moet zo specifiek mogelijk zijn. Als het verzenden van een formulier mislukt is, kunnen sommige gebruikers niet zien dat er een fout is opgetreden en kunnen ze het formulier niet opnieuw weergeven en de foutvelden aangeven. Gebruikers van schermlezers weten bijvoorbeeld niet dat er een fout is opgetreden totdat ze een van de indicatoren tegenkomen. Ze kunnen het formulier helemaal verlaten voordat ze de foutindicator tegenkomen, omdat ze denken dat de pagina gewoon niet functioneel is. Per de definitie in WCAG, is een [&#x200B; inputfout &#x200B;](https://www.w3.org/TR/WCAG/#dfn-input-error) informatie die door de gebruiker wordt verstrekt die niet wordt goedgekeurd. Dit omvat het volgende.

Informatie die door de webpagina wordt vereist maar door de gebruiker wordt weggelaten, of informatie die door de gebruiker wordt verstrekt maar die buiten het vereiste gegevensformaat of toegestane waarden valt.
Bijvoorbeeld:

* de gebruiker de juiste afkorting niet invoert in het veld Staat, provincie of regio;
* de gebruiker een statusafkorting invoert die geen geldige status is;
* de gebruiker een niet-bestaande postcode of postcode invoert;
* de gebruiker in de toekomst 2 jaar na de geboorte ingaat;
* de gebruiker voert alfabetische karakters of haakjes in hun gebied van het telefoonaantal in dat slechts aantallen goedkeurt;
* de gebruiker voert een bod in dat lager is dan het vorige bod of de minimumbodverhoging.

#### Hoe kan ik-fout-identificatie (3.3.1) {#how-to-meet-error-identification}

Volg de richtlijnen onder [&#x200B; hoe te om Criteria 3.3.1 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#error-identification).

#### Meer informatie - Foutidentificatie (3.3.1) {#more-information-error-identification}

* [&#x200B; Begrijpend Criteria 3.3.1 van het Succes &#x200B;](https://www.w3.org/WAI/WCAG21/Understanding/error-identification.html)
* [&#x200B; hoe te om Criteria 3.3.1 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#error-identification)

### Labels of instructies (3.3.2) {#labels-or-instructions}

* Succescriterium 3.3.2
* Niveau A
* Labels of instructies: Er worden labels of instructies gegeven wanneer de inhoud door de gebruiker moet worden ingevoerd.

#### Doel - Labels of instructies (3.3.2) {#purpose-labels-or-instructions}

Het geven van instructies om mensen te helpen vormen in te vullen is een fundamenteel onderdeel van goede praktijken in interfacebruikbaarheid. Dit is handig voor mensen met een visuele of cognitieve handicap die anders moeite zouden hebben om de indeling van een formulier en het soort gegevens dat in een bepaald formulierveld moet worden verstrekt, te begrijpen.

##### Forms

In het AEM WKND demoproject wordt een standaardetiket toegevoegd wanneer u een vormcomponent, zoals het Gebied van de Tekst van de a **&#x200B;**, aan de pagina toevoegt. Deze standaardtitel is afhankelijk van het componenttype. U kunt uw eigen titel op de **Titel en het lusje van de Tekst** toevoegen van uitgeeft dialoog voor dat gebied. Het is belangrijk dat labels gebruikers helpen de gegevens te begrijpen die aan elke formuliercomponent zijn gekoppeld.

Dit **gebied van de Titel** moet voor gebiedselementen worden gebruikt aangezien het een etiket verstrekt dat aan hulptechnologie beschikbaar is. Alleen het schrijven van een label in tekst naast het veld is niet voldoende.

Voor sommige vormcomponenten, is het ook mogelijk om etiketten visueel te verbergen gebruikend **de checkbox van de Titel van de Verbergen**. Labels die op deze manier zijn verborgen, zijn nog steeds beschikbaar voor ondersteunende technologie, maar worden niet op het scherm weergegeven. Hoewel dit in sommige situaties een goede aanpak kan zijn, is het beter om waar mogelijk een visueel label op te nemen, aangezien sommige gebruikers een klein gedeelte van het scherm (één veld tegelijk) kunnen bekijken en de etiketten nodig hebben om het gebied correct te identificeren.

###### Afbeeldingsknoppen {#image-buttons}

Waar de beeldknopen worden gebruikt (bijvoorbeeld, geeft de **component van de Knoop van het Beeld 0&rbrace; {van het WKND-project), het** 3} gebied van de Titel **en het lusje van de Tekst** van de bewerkingsdialoog eigenlijk de alt tekst voor het beeld, eerder dan het etiket. **&#x200B;**&#x200B;In het onderstaande voorbeeld heeft de afbeelding met de tekst `Submit` dus alternatieve tekst van `Submit`, toegevoegd met het veld **Titel** in het dialoogvenster Bewerken.

###### Groepen formuliervelden {#groups-of-form-fields}

In het project WKND, waar er een groep verwante controles, zoals **Groep van de Radio** is, kan een titel voor de groep, en individuele controles nodig zijn. Wanneer u een set keuzerondjes toevoegt in AEM, wordt in het veld **Titel** deze groepstitel weergegeven, terwijl afzonderlijke titels worden opgegeven wanneer de keuzerondjes (**Items**) worden gemaakt.

Er is echter geen programmatische koppeling tussen de groepstitel en de keuzerondjes zelf. Sjablooneditors moeten de titel in de benodigde `fieldset` - en `legend` -tags plaatsen om deze koppeling te maken. Dit kan alleen door de broncode van de pagina te bewerken. Alternatief, kan een systeembeheerder steun voor deze elementen toevoegen zodat zij in de **dialoog van de Eigenschappen van het Gebied** verschijnen (zie [&#x200B; Toevoegend Steun voor Extra Elementen en Attributen van de HTML &#x200B;](/help/sites-administering/rte-accessible-content.md#add-support-for-more-html-elements-and-attributes)).

###### Aanvullende overwegingen voor Forms {#additional-considerations-for-forms}

Als gegevens in een specifieke indeling moeten worden ingevoerd, maakt u dit duidelijk in de labeltekst. Als bijvoorbeeld een datum moet worden ingevoerd in de `DD-MM-YYYY` -indeling, geeft u dit specifiek op als onderdeel van het label. Dit betekent dat wanneer gebruikers van schermlezers het veld tegenkomen, het label automatisch wordt aangekondigd, samen met aanvullende informatie over de indeling.

Als invoer voor een formulierveld verplicht is, maakt u dit duidelijk door het vereiste woord als onderdeel van het label te gebruiken. AEM voegt een sterretje toe wanneer een veld vereist is, maar het is ideaal om het woord `required`in het label zelf op te nemen (in het veld **Titel** in het dialoogvenster Bewerken).

Het positioneren van labels is ook belangrijk, omdat ze hierdoor geschikte velden kunnen vinden. Dit is van bijzonder belang wanneer de gebruiker met een complexe vorm wordt geconfronteerd. Volg de onderstaande conventie:

* Selectievakjes of keuzerondjes:
De labels worden direct rechts van het veld geplaatst.
* Alle andere formuliercomponenten (bijvoorbeeld tekstvakken, keuzelijsten met invoervak):
De labels worden direct boven of direct links van het veld geplaatst.

In eenvoudige formulieren met beperkte functionaliteit kan het correct labelen van een `Submit` -knop als label voor het aangrenzende veld (bijvoorbeeld `Search` ). Dit is handig in situaties waarin het lastig kan zijn om ruimte te zoeken voor de labeltekst.

#### Meer informatie - Labels of instructies (3.3.2) {#more-information-labels-or-instructions}

* [&#x200B; Begrijpend criterium van het Succes 3.3.2 &#x200B;](https://www.w3.org/WAI/WCAG21/Understanding/labels-or-instructions.html)
* [&#x200B; hoe te om Criterium 3.3.2 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#labels-or-instructions)

### Foutmelding (3.3.3)  {#error-suggestion}

* Succescriterium 3.3.3
* Niveau AA
* Toetsenbord: als er automatisch een invoerfout wordt gedetecteerd en suggesties voor correctie bekend zijn, worden de suggesties aan de gebruiker doorgegeven, tenzij dit de beveiliging of het doel van de inhoud in gevaar zou brengen.

#### Doel - Foutvoorstel (3.3.3) {#purpose-error-suggestion}

Het doel van dit succescriterium is ervoor te zorgen dat gebruikers passende suggesties ontvangen voor het corrigeren van een invoerfout als dat mogelijk is. De definitie WCAG van [&#x200B; inputfout &#x200B;](https://www.w3.org/TR/WCAG/#dfn-input-error) zegt dat het &quot;informatie is die door de gebruiker wordt verstrekt die niet&quot;door het systeem wordt goedgekeurd. Voorbeelden van informatie die niet wordt geaccepteerd, zijn informatie die vereist is maar door de gebruiker wordt weggelaten en informatie die door de gebruiker wordt verstrekt maar die buiten de vereiste of toegestane gegevensindeling valt.

In criterium 3.3.1 van het succescriterium is voorzien in een foutmelding. Personen met cognitieve beperkingen kunnen het echter moeilijk vinden te begrijpen hoe de fouten moeten worden gecorrigeerd. Mensen met een visuele handicap kunnen wellicht niet precies uitzoeken hoe de fout kan worden gecorrigeerd. Als het verzenden van een formulier niet is gelukt, kunnen gebruikers het formulier verlaten omdat ze niet zeker weten hoe de fout moet worden gecorrigeerd, ook al weten ze dat deze wel is opgetreden.

De inhoudauteur kan de beschrijving van de fout verstrekken, of de gebruikersagent kan de beschrijving van de fout verstrekken die op technologie-specifieke, programmatically bepaalde informatie wordt gebaseerd.

#### Hoe kan ik-fout suggestie (3.3.3) {#how-to-meet-error-suggestion}

Volg de richtlijnen onder [&#x200B; hoe te om Criteria 3.3.3 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#error-suggestion).

#### Meer informatie - Foutmelding (3.3.3) {#more-information-error-suggestion}

* [&#x200B; Begrijpend Criteria 3.3.3 van het Succes &#x200B;](https://www.w3.org/WAI/WCAG21/Understanding/error-suggestion.html)
* [&#x200B; hoe te om Criteria 3.3.3 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#error-suggestion)

### Preventie van fouten (juridisch, financieel, gegevens) (3.3.4)  {#error-prevention-legal-financial-data}

* Succescriterium 3.3.4
* Niveau AA
* Foutpreventie (Legal, Financial, Data): voor webpagina&#39;s die juridische verbintenissen of financiële transacties voor de gebruiker veroorzaken, die door de gebruiker te controleren gegevens in gegevensopslagsystemen wijzigen of verwijderen, of die testreacties van gebruikers indienen, is ten minste een van de volgende zaken waar:

   * Omkeerbaar
Indieningen zijn omkeerbaar.
   * Ingeschakeld
De gegevens die door de gebruiker worden ingevoerd, worden gecontroleerd op invoerfouten en de gebruiker krijgt de gelegenheid deze te corrigeren.
   * Bevestigd
Er is een mechanisme beschikbaar voor het controleren, bevestigen en corrigeren van informatie voordat de verzending wordt voltooid.

#### Doel - Preventie van fouten (juridisch, financieel, gegevens) (3.3.4) {#purpose-error-prevention-legal-financial-data}

Dit succescriterium is bedoeld om gebruikers met een handicap te helpen ernstige gevolgen te voorkomen die het gevolg zijn van een fout bij het uitvoeren van een actie die niet ongedaan kan worden gemaakt. De aankoop van niet-terugvorderbare vliegtickets of het indienen van een bestelling voor de aankoop van aandelen op een makelaarsrekening zijn bijvoorbeeld financiële transacties met ernstige gevolgen. Als een gebruiker een fout heeft gemaakt op de datum van het luchtvervoer, zou hij een ticket kunnen krijgen voor de verkeerde dag die niet kan worden uitgewisseld. Als de gebruiker een fout maakte met betrekking tot het aantal te kopen aandelen, zou hij uiteindelijk meer aandelen kunnen kopen dan hij had verwacht. Beide soorten kostbare fouten hebben betrekking op transacties die onmiddellijk plaatsvinden en achteraf niet kunnen worden gewijzigd. Evenzo kan het een onherstelbare fout zijn als gebruikers per ongeluk gegevens wijzigen of verwijderen die zijn opgeslagen in een database waartoe ze later toegang moeten krijgen, zoals hun volledige reisprofiel op een website voor reisservices. Wanneer wordt verwezen naar het wijzigen of verwijderen van gegevens die door de gebruiker kunnen worden gecontroleerd, is het de bedoeling te voorkomen dat er massaal gegevens verloren gaan, zoals het verwijderen van een bestand of record. Het is niet de bedoeling een bevestiging te vereisen voor elke sparen bevel of het eenvoudige creëren of uitgeven van documenten, verslagen of andere gegevens.

Gehandicapte gebruikers kunnen vaker fouten maken. Mensen met een leeshandicap kunnen nummers en letters omzetten en personen met een motorische handicap kunnen per ongeluk de toetsen raken. Door de mogelijkheid te bieden acties om te keren, kunnen gebruikers een fout corrigeren die ernstige gevolgen kan hebben. Het bieden van de capaciteit om informatie te herzien en te verbeteren geeft de gebruiker de kans om een fout te ontdekken alvorens een actie te ondernemen die ernstige gevolgen heeft.

Door de gebruiker te controleren gegevens zijn door de gebruiker te bekijken gegevens die de gebruiker via een opzettelijke handeling kan wijzigen en/of verwijderen. Voorbeelden van de gebruiker die dergelijke gegevens beheert, zijn het bijwerken van het telefoonnummer en het adres van de account van de gebruiker of het verwijderen van een record met facturen uit het verleden van een website. De code verwijst niet naar zaken als internetlogboeken en controlegegevens van zoekprogramma&#39;s die de gebruiker niet rechtstreeks kan bekijken of gebruiken.

#### Hoe te om te ontmoeten - de Preventie van de Fout (Juridisch, Financieel, Gegevens) (3.3.4) {#how-to-meet-error-prevention-legal-financial-data}

Volg de richtlijnen onder [&#x200B; hoe te om Criteria 3.3.4 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#error-prevention-legal-financial-data).

#### Meer informatie - Foutpreventie (juridisch, financieel, gegevens) (3.3.4) {#more-information-error-prevention-legal-financial-data}

* [&#x200B; Begrijpend Criteria 3.3.4 van het Succes &#x200B;](https://www.w3.org/WAI/WCAG21/Understanding/error-prevention-legal-financial-data.html)
* [&#x200B; hoe te om Criteria 3.3.4 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#error-prevention-legal-financial-data)

## Beginsel 4: Robuust {#principle-robust}

[&#x200B; Beginsel 4: Robuust - de Inhoud moet robuust genoeg zijn dat het door een brede verscheidenheid van gebruikersagenten, met inbegrip van ondersteunende technologieën kan worden geïnterpreteerd.](https://www.w3.org/TR/WCAG/#robust)

### Compatibel (4.1) {#compatible}

[&#x200B; Richtsnoer 4.1 Compatibel: Maximaliseer verenigbaarheid met huidige en toekomstige gebruikersagenten, met inbegrip van hulptechnologieën.](https://www.w3.org/TR/WCAG/#compatible)

Maximaliseer verenigbaarheid met huidige en toekomstige gebruikersagenten, met inbegrip van ondersteunende technologieën.

### Parseren (4.1.1)  {#parsing}

* Succescriterium 4.1.1
* Niveau A
* Parseren: in inhoud die is geïmplementeerd met behulp van opmaaktalen, hebben elementen volledige start- en eindtags, worden elementen genest volgens hun specificaties, bevatten elementen geen dubbele kenmerken en zijn alle id&#39;s uniek, behalve wanneer de specificaties deze functies toestaan.

#### Doel - Parseren (4.1.1) {#purpose-parsing}

Het doel van dit succescriterium is ervoor te zorgen dat gebruikersagenten, inclusief ondersteunende hulpmiddelen, inhoud nauwkeurig kunnen interpreteren en parseren. Als de inhoud niet in een gegevensstructuur kan worden geparseerd, dan kunnen de verschillende gebruikersagenten het anders voorstellen of kunnen niet het ontleden. Sommige gebruikersagenten gebruiken &quot;reparatietechnieken&quot;om slecht gecodeerde inhoud terug te geven.

Omdat de reparatietechnieken tussen gebruikersagenten variëren, kunnen de auteurs niet veronderstellen dat de inhoud nauwkeurig in een gegevensstructuur wordt geparseerd of dat het correct door gespecialiseerde gebruikersagenten, met inbegrip van ondersteunende technologieën zal worden teruggegeven, tenzij de inhoud volgens de regels die in de formele grammatica voor die technologie worden bepaald wordt gecreeerd. In opmaaktalen leiden fouten in de element- en kenmerksyntaxis en het niet op de juiste manier leveren van geneste start- en eindtags tot fouten die ervoor zorgen dat gebruikersagents de inhoud niet betrouwbaar kunnen parseren. Daarom vereist het criterium van het Succes dat de inhoud kan worden geparseerd gebruikend slechts de regels van de formele grammatica.

#### Hoe kan ik-parseren (4.1.1) {#how-to-meet-parsing}

Volg de richtlijnen onder [&#x200B; hoe te om Criteria van het Succes 4.1.1 &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#parsing) te ontmoeten.

#### Meer informatie - parseren (4.1.1) {#more-information-parsing}

* [&#x200B; Begrijpend Criteria 4.1.1 van het Succes &#x200B;](https://www.w3.org/WAI/WCAG21/Understanding/parsing.html)
* [&#x200B; hoe te om Criteria 4.1.1 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#parsing)

### Naam, Rol, Waarde (4.1.2)  {#name-role-value}

* Succescriterium 4.1.2
* Niveau A
* Naam, Rol, Waarde: Voor alle gebruikersinterfacecomponenten (met inbegrip van maar niet beperkt tot: vormelementen, verbindingen, en componenten die door manuscripten worden geproduceerd), kan de naam, en de rol programmatically worden bepaald; staten, eigenschappen, en waarden die door de gebruiker kunnen worden geplaatst kunnen programmatically worden geplaatst; en bericht van veranderingen in deze punten is beschikbaar aan gebruikersagenten, met inbegrip van hulptechnologieën.

#### Doel - Naam, Rol, Waarde (4.1.2) {#purpose-ame-role-value}

Het doel van dit criterium van Succes is ervoor te zorgen dat de Technologieën van de Hulpverlening (AT) informatie over kunnen verzamelen, activeren (of plaatsen) en bijgewerkt op de status van gebruikersinterfacecontroles in de inhoud houden.

Wanneer standaardcontroles van toegankelijke technologieën worden gebruikt, is dit proces ongecompliceerd. Als de elementen van de gebruikersinterface volgens specificatie worden gebruikt, wordt aan de voorwaarden van deze bepaling voldaan. (Zie voorbeelden van succescriterium 4.1.2 hieronder)

Als douanecontroles worden gecreeerd, echter, of de interface elementen (in code of manuscript) geprogrammeerd om een verschillende rol en/of een functie te hebben dan gebruikelijk, dan moeten de extra maatregelen worden genomen om ervoor te zorgen dat de controles belangrijke informatie aan hulptechnologieën verstrekken en zich om door ondersteunende technologieën laten worden gecontroleerd.

Een belangrijke staat van een gebruikersinterfacecontrole is of het nadruk heeft. De nadrukstaat van een controle kan programmatically worden bepaald, en de berichten over verandering van nadruk worden verzonden naar gebruikersagenten en hulptechnologie. Andere voorbeelden van de besturingsstatus van de gebruikersinterface zijn of een selectievakje of keuzerondje is geselecteerd. Of, of een doen ineenstorten boom of lijstknoop wordt uitgebreid of samengevouwen.

#### Hoe te om te ontmoeten - Naam, Rol, Waarde (4.1.2) {#how-to-meet-ame-role-value}

Volg de richtlijnen onder [&#x200B; hoe te om Criteria van het Succes 4.1.2 &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#name-role-value) te ontmoeten.

#### Meer informatie - Naam, Rol, Waarde (4.1.2 {#more-information-ame-role-value}

* [&#x200B; Begrijpend Criteria 4.1.2 van het Succes &#x200B;](https://www.w3.org/WAI/WCAG21/Understanding/name-role-value.html)
* [&#x200B; hoe te om Criteria 4.1.2 van het Succes te ontmoeten &#x200B;](https://www.w3.org/WAI/WCAG21/quickref/#name-role-value)
