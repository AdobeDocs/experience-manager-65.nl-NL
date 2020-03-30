---
title: Documentfragmenten
seo-title: Documentfragmenten
description: Met documentfragmenten, zoals tekst, lijsten, voorwaarden en layoutfragmenten, kunt u in Correspondence Management de statische, dynamische en herhaalbare componenten van klantcorrespondentie vormen.
seo-description: Met documentfragmenten, zoals tekst, lijsten, voorwaarden en layoutfragmenten, kunt u in Correspondence Management de statische, dynamische en herhaalbare componenten van klantcorrespondentie vormen.
uuid: 4273323d-14f5-4b3b-8fed-80beef641efe
topic-tags: correspondence-management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 0d5436c6-1976-496c-b9a7-7dc6e830bb5d
docset: aem65
translation-type: tm+mt
source-git-commit: e4d84b5c6f7d2bfcac942b0b685a8f1fd11274f0

---


# Documentfragmenten{#document-fragments}

## Documentfragmenten {#document-fragments-1}

Documentfragmenten zijn herbruikbare onderdelen/onderdelen van een correspondentie waarmee u letters/correspondentie kunt samenstellen. De documentfragmenten zijn van de volgende typen:

* **Tekst**: Een tekstelement is een stuk inhoud dat bestaat uit een of meer tekstalinea&#39;s. Een alinea kan statisch of dynamisch zijn.
* **Lijst**: List is een groep documentfragmenten, waaronder tekst, lijsten, voorwaarden en afbeeldingen. De volgorde van de lijstelementen kan vast of bewerkbaar zijn. Tijdens het maken van een letter kunt u enkele of alle lijstelementen gebruiken om een herbruikbaar patroon van elementen te repliceren.
* **Voorwaarde**: De voorwaarden laten u toe om te bepalen welke inhoud inbegrepen bij de tijd van de brievenverwezenlijking wordt, die op de geleverde gegevens wordt gebaseerd. De voorwaarde wordt beschreven in termen van controlevariabelen. Een besturingsvariabele kan een gegevenswoordenboekelement of een plaatsaanduiding zijn.
* **Lay-outfragment**: Een lay-outfragment is een lay-out die binnen één of meerdere letters kan worden gebruikt. Een lay-outfragment wordt gebruikt om herhaalbare patronen, vooral dynamische lijsten tot stand te brengen. De indeling kan typische formuliervelden bevatten, zoals &quot;Adres&quot; en &quot;Referentienummer&quot;. Het bevat ook lege subformulieren die doelgebieden aangeven. De lay-outs (XDP&#39;s) worden gemaakt in Designer en worden vervolgens geüpload naar AEM Forms.

## Tekst {#text}

Een tekstelement is een stuk inhoud dat bestaat uit een of meer tekstalinea&#39;s. Een alinea kan statisch of dynamisch zijn. Een dynamische alinea bevat verwijzingen naar gegevenselementen waarvan de waarden bij uitvoering worden verschaft. De naam van de klant in een letterlijke aanhef kan bijvoorbeeld een dynamisch gegevenselement zijn, waarbij de waarde ervan tijdens runtime beschikbaar wordt gemaakt. Door deze waarden te wijzigen, kan het zelfde brievenmalplaatje worden gebruikt om brieven voor verschillende klanten te produceren.

De oplossing van het Beheer van de Correspondentie steunt twee soorten aan dynamische gegevenspunten (veranderlijke gegevens):

* **Gegevenswoordenboekelementen**: Deze elementen zijn gebonden aan het gegevenswoordenboek en krijgen hun waarden van de geleverde gegevensbron. Een gegevenswoordenboekvariabele kan worden beveiligd of niet worden beveiligd. Tijdens het maken van correspondentie kan de gebruiker de standaardwaarde van niet-beveiligde gegevenswoordenboekvariabelen wijzigen, maar de variabelen van het beveiligde gegevenswoordenboek kunnen niet worden gewijzigd.
* **Plaatsaanduidingen**: Dit zijn variabelen die niet aan een achtereind gegevensbron verbindend zijn. Ze vereisen dat de gebruiker een waarde invult tijdens het maken van correspondentie. De plaatsaanduidingen zijn standaard niet beveiligd.

>[!NOTE]
>
>De sjablonen voor Correspondentiebeheer dwingen u niet unieke namen te maken wanneer u plaatsaanduidingen maakt. Als u twee plaatsaanduidingen met dezelfde naam maakt, zoals tekst en een voorwaarde, en deze beide gebruikt in een lettertypesjabloon, worden de waarden van de plaatsaanduiding die het laatst is ingevoegd, gebruikt voor beide plaatsaanduidingen. Als twee plaatsaanduidingen dezelfde naam hebben, worden de typen vergeleken. Als de typen verschillend zijn, wordt het type String. Binnen een module kunt u echter geen meerdere plaatsaanduidingen met dezelfde naam maken.

### Tekst maken {#create-text}

1. Selecteer **Formulieren** > **Documentfragmenten**.
1. Tik op **Maken** > **Tekst** of selecteer een tekstelement en tik op **Bewerken**.
1. Geef de volgende informatie op voor de tekst:

   * **Titel: (Optioneel)** Voer de titel in voor het tekstelement. Titels hoeven niet uniek te zijn en kunnen speciale tekens en niet-Engelse tekens bevatten. De teksten worden bedoeld door hun titels (indien beschikbaar) zoals in duimnagels en activa eigenschappen.
   * **Naam:** De unieke naam voor het tekstelement. Er kunnen in geen enkele staat twee elementen (tekst, voorwaarde of lijst) bestaan met dezelfde naam. In het veld Naam kunt u alleen Engelse tekens, cijfers en afbreekstreepjes invoeren. Het veld Naam wordt automatisch ingevuld op basis van het veld Titel. De speciale tekens, spaties, getallen en niet-Engelse tekens die in het veld Titel zijn ingevoerd, worden vervangen door afbreekstreepjes in het veld Naam. Hoewel de waarde in het veld Titel automatisch naar de naam wordt gekopieerd, kunt u de waarde bewerken.
   * **Omschrijving**: Typ een beschrijving van het element.
   * **Gegevenswoordenboek**: Selecteer desgewenst het gegevenswoordenboek waarin u wilt toewijzen. Met dit kenmerk kunt u verwijzingen naar gegevenswoordenboekelementen in het tekstelement toevoegen.
   * **Tags**: Als u een aangepaste tag wilt maken, typt u een waarde in het tekstveld en drukt u op Enter. U ziet de tag onder het tekstveld met tags. Wanneer u deze tekst opslaat, worden ook de toegevoegde tags gemaakt.

1. Tik op **Volgende**. Met Correspondentiebeheer wordt de Editor-pagina weergegeven waar u tekstalinea&#39;s en gegevenselementen aan de tekst kunt toevoegen.

   De standaardspellingcontrole in uw browser controleert spelling in de redacteur van de Tekst. Als u de spelling en grammatica wilt controleren, kunt u de instellingen voor spellingcontrole van uw browser bewerken of browserinsteekmodules/invoegtoepassingen installeren om de spelling en de grammatica te controleren.

   U kunt ook de verschillende sneltoetsen in de teksteditor gebruiken voor het beheren, bewerken en opmaken van tekst. Voor meer informatie over [de toetsenbordkortere weg van de Redacteur](/help/forms/using/keyboard-shortcuts.md#p-formatting-p) van de Tekst in de Kortere weg van het Beheer van de Correspondentie.

1. Er wordt een teksteditor geopend en u voert de tekst in. Gebruik de werkbalk boven aan de pagina om de tekst, invoegvoorwaarden, koppeling en pagina-einden op te maken.

   [ ![Toolbar](assets/advancedediting.png)

   * **Koppeling**: Voeg [hypertextkoppeling](#insert-hyperlink) in de tekst in.
   * **Herhalen**: Met Herhalen wordt het verzamelingselement in het gegevenswoordenboek afgedrukt met een scheidingsteken.
   * **Voorwaarde**: Tik om een voorwaarde in te voegen. Voeg op voorwaarde gebaseerde tekst in. Als de voorwaarde waar is, dan is de tekst zichtbaar in brief, anders niet.
   * **Beschrijving** toevoegen: Voeg een aantekening aan een stuk van tekst toe. Dit zijn metagegevens die zichtbaar zijn voor de auteur, maar geen deel van de gemaakte brief.
   * **Pagina-einde**: Als u het kenmerk Pagina-einden van een tekstmodule instelt op false, wordt de tekstmodule niet over pagina&#39;s verdeeld.
   Er wordt een teksteditor geopend. Voer de tekst in. De werkbalk verandert afhankelijk van het type bewerkingen dat u wilt uitvoeren: Alinea, Uitlijning of Lijst:

   ![Type werkbalk selecteren](assets/toolbarselection.png)

   Selecteer een type werkbalk: Alinea, Uitlijning of Lijst

   ![Alinea, werkbalk](assets/fonteditingtoolbar.png)

   Alinea, werkbalk
   [ ![Uitlijning,](assets/paragrapheditingtoolbar.png)](assets/paragrapheditingtoolbar-1.png)werkbalkUitlijning, werkbalk

   ![Aanbiedingswerkbalk](assets/bulleteditingtoolbar.png)

   De werkbalk Lijst (klik om een afbeelding op volledige grootte te openen)

1. Als u een of meer alinea&#39;s tekst die in een andere toepassing voorkomen, zoals MS Word- of HTML-pagina&#39;s, wilt hergebruiken, kopieert en plakt u de tekst in de teksteditor. De opmaak van de gekopieerde tekst blijft behouden in de teksteditor.

   U kunt een of meer alinea&#39;s tekst in een bewerkbare tekstmodule kopiëren en plakken. U hebt bijvoorbeeld een MS Word-document met een lijst met geldige verblijfstitels, zoals:

   ![pastetextmsword-1](assets/pastetextmsword-1.png)

   U kunt de tekst rechtstreeks vanuit het MS Word-document naar een bewerkbare tekstmodule kopiëren en plakken. De opmaak, zoals een lijst met opsommingstekens, lettertype en tekstkleur, blijft behouden in de tekstmodule.

   ![pastettextmodule](assets/pastetexttextmodule.png)

   >[!NOTE]
   >
   >De opmaak van geplakte tekst heeft echter enkele [beperkingen](https://helpx.adobe.com/aem-forms/kb/cm-copy-paste-text-limitations.html).

1. Voeg zo nodig speciale tekens in het documentfragment in. U kunt bijvoorbeeld het palet Speciale tekens gebruiken om het volgende in te voegen:

   * Valutasymbolen zoals €, ¥ en £
   * Wiskundige symbolen zoals A, Ö, ∂ en ^
   * Interpunctiesymbolen zoals ‟ en&quot;
   ![specialcharacters-1](assets/specialcharacters-1.png)

   Correspondence Management biedt ondersteuning voor 210 speciale tekens. De beheerder kan ondersteuning voor meer/aangepaste speciale tekens [toevoegen door deze aan te passen](/help/forms/using/custom-special-characters.md).

1. Selecteer de tekst en tik op Markeringskleur om\gedeelten van tekst in een bewerkbare inlinemodule te benadrukken.

   ![textBackgroundColor toegepast](assets/textbackgroundcolorapplied.png)

   U kunt rechtstreeks op een basiskleur in het palet Standaardkleuren tikken of op `**[A]**` Selecteren **tikken nadat u de schuifregelaar hebt gebruikt** `**[B]**` om de juiste kleurtint te kiezen.

   Desgewenst kunt u ook naar het tabblad Geavanceerd gaan om de juiste kleurtoon, helderheid en verzadiging te selecteren `**[C]**` en vervolgens op Selecteren tikken `**[D]**` om de tekst te markeren.

   ![textBackgroundColor-1](assets/textbackgroundcolor-1.png)

1. Sleep vanuit het gegevensvenster gegevenswoordenboekelementen en plaatsaanduidingselementen naar de tekst.

   Naar:

   * Voeg een gegevenswoordenboekelement in de tekst toe, selecteer een gegevenselement in de lijst en tik op Invoegen ( ![invoegen](assets/insert.png)). Als u Beveiligd selecteert, is het gegevenswoordenboekelement alleen-lezen en wordt het weergegeven in de lettereditor, maar niet in de gebruikersinterface Correspondentie maken of Correspondence Creator.
   * Voeg een plaatsaanduidingselement toe aan de tekst. Tik in het deelvenster Gegevenselementen op Nieuw maken, voer de details voor het nieuwe gegevenselement in en tik op Maken om het nieuwe element aan de lijst toe te voegen. De nieuwe plaatsaanduiding kan op dezelfde manier in de tekst worden ingevoegd als het gegevenswoordenboekelement. Als u een tijdelijke aanduiding wilt bewerken, selecteert u een tijdelijke aanduiding en tikt u op Bewerken.
   ![Plaatsaanduidingselementen](assets/placeholder_elements_in_xmldata.png)

   Plaatsaanduidingselementen zoals opgegeven in het bestand met voorbeeldgegevens van een gegevenswoordenboek

   ![Plaatsaanduidingselementen in letter](assets/placeholder_elements_in_text.png)

   Plaatsaanduidingselementwaarden in de CCR-weergave die zijn gevuld met de gegevenswoordenboekvariabelen zoals opgegeven in het bestand met voorbeeldgegevens

   Met het @-symbool kunt u ook gegevenswoordenboek en plaatsaanduidingselementen zoeken en toevoegen aan de teksteditor. Plaats de cursor op de plaats waar u het element wilt invoegen. Typ @ gevolgd door de zoekreeks. De teksteditor voert de zoekbewerking uit op alle gegevenswoordenboeken en plaatsaanduidingselementen die beschikbaar zijn in het tekstdocumentfragment. De zoekbewerking haalt de elementen met de zoekreeks op en geeft deze weer als een vervolgkeuzelijst. Navigeer door de onderzoeksresultaten en klik het element dat u bij de cursorplaats wilt opnemen. Druk op Esc om de zoekresultaten te verbergen.

1. U kunt inline voorwaarden en herhalingen gebruiken om uw brief in hoge mate contextueel en goed gestructureerd te maken. Zie [Inline-voorwaarden en Herhaling in letters](/help/forms/using/cm-inline-condition.md)voor meer informatie over inline-voorwaarde en herhaling.
1. Tik op **Opslaan**.

#### Hyperlink invoegen in tekst {#insert-hyperlink}

Voer de volgende stappen uit om een hyperlink in een tekstelement te maken:

1. Selecteer de tekst of het gegevensmodelobject in de teksteditor.

2. Tik op **[!UICONTROL Koppeling]**. Tik op het veld **[!UICONTROL Alt-tekst]** om de bestaande naam of tekst van het gegevensmodel te verwijderen.

3. Geef de URL op en tik op ![Opslaan](assets/save_icon.svg).

![Hyperlink maken in tekstelement](assets/text-create-hyperlink.png)

#### Tekst zoeken en vervangen {#searching-and-replacing-text}

Wanneer u werkt met tekstelementen die een grote hoeveelheid tekst bevatten, moet u zoeken naar een specifieke tekstreeks. U moet mogelijk ook een specifieke tekenreeks vervangen door een alternatieve tekenreeks.

Met de functie Zoeken en vervangen kunt u elke tekenreeks in een tekstelement zoeken (en vervangen). De functie bevat ook een krachtige zoekopdracht met een reguliere expressie.

#### Tekst zoeken in een tekstmodule {#to-search-text-in-a-text-module}

1. Open de tekstmodule in de teksteditor.

1. Tik op Zoeken en vervangen.
1. Typ de tekst die u wilt zoeken in het tekstvak Zoeken en druk op Zoeken. De zoektekst wordt gemarkeerd in de tekstmodule.
1. Druk nogmaals op Zoeken om naar het volgende exemplaar van de tekst te zoeken.

   Als u op de knop Zoeken blijft drukken, gaat de zoekopdracht verder op de pagina. Nadat de laatste instantie van de tekst is gevonden, geeft het bericht **Reached end end of module** aan dat er geen zoekresultaten meer zijn gevonden.

   Als er echter geen zoektekst wordt gevonden in de tekstmodule, wordt het volgende bericht weergegeven: Niet **gevonden**.

1. Als u nogmaals op Zoeken drukt, gaat de zoekopdracht verder boven aan de pagina.

#### Zoekopties {#search-options}

**Hoofdlettergebruik afstemmen:** De zoekopdracht geeft alleen resultaten met hetzelfde hoofdlettergebruik.

**Heel woord:** Zoekopdracht retourneert alleen hele woorden.

**Opmerking:** Als u speciale tekens invoert in het tekstvak Zoeken, is de optie Heel woord uitgeschakeld.

**Voorbeeld:** Zoeken met reguliere expressies. Met de volgende reguliere expressie wordt bijvoorbeeld gezocht naar e-mailadressen in een tekstmodule:

`[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,4}`

#### Tekst zoeken en vervangen in een tekstmodule {#to-search-and-replace-text-in-a-text-module}

1. Open de tekstmodule in de teksteditor.
1. Tik op Zoeken en vervangen.
1. Typ de tekst die u wilt zoeken in het tekstvak Zoeken en de tekst waarmee u de zoektekst wilt vervangen en druk op Vervangen.
1. Als de zoektekst wordt gevonden, wordt de tekst vervangen door de tekst Vervangen.

   * Als er een ander exemplaar van de zoektekst wordt gevonden, wordt dat exemplaar gemarkeerd in de tekstmodule. Als u nogmaals op Vervangen drukt, wordt het gemarkeerde exemplaar vervangen en gaat de cursor verder als een derde exemplaar wordt gevonden.
   * Als een andere instantie niet wordt gevonden, stopt de cursor bij de laatste vervangen instantie.

1. Als u nogmaals op Zoeken drukt, gaat de zoekopdracht verder boven aan de pagina.

   Met de optie Alles vervangen kunt u alle instanties van een tekst in de tekstmodule vervangen. Wanneer u ons &quot; doet, wordt het aantal vervangingen weergegeven als een bericht in het dialoogvenster Zoeken en vervangen.

#### Tips en trucs voor beste praktijken/trucs voor tekstmodules {#best-practices-tips-and-tricks-for-text-modules}

* Gebruik een consistente naamgevingsconventie om dubbel werk te voorkomen.
* Gebruik de juiste gegevenswoordenboekbinding in tekstmodules.
* De volgende regels zijn van toepassing wanneer u de Teksteditor gebruikt bij het wijzigen van een tekstelement:

   * **Toevoeging van variabele:** Toegestaan
   * **Verwijderen van variabele:** Toegestaan
   * **Bijwerken van eigenschappen:** Toegestaan
   * **Wijziging van gegevenswoordenboek:** Toegestaan totdat het gegevenswoordenboekelement niet wordt gebruikt. U kunt het gegevenswoordenboek niet wijzigen tijdens het bijwerken.

## Lijst {#list}

Een lijst is een groep documentfragmenten, waaronder tekst, (andere) lijsten, voorwaarden en afbeeldingen. De volgorde van de lijstelementen kan vast of bewerkbaar zijn. Tijdens het maken van een letter kunt u sommige of alle lijstelementen gebruiken om een herbruikbaar patroon van elementen te repliceren. Lijsten gedragen zich in feite als doelen die binnen andere doelen kunnen worden genest.

### Uitvoeringslijsten {#implementing-lists}

De uitvoeringslijsten bestaan uit twee stappen:

1. Basiseigenschappen definiëren, zoals naam, beschrijving en gegevenswoordenboek.
1. Sectie van inhoud die deel uitmaakt van de lijst, en dan plaatsend eigenschappen zoals slotorde en bibliotheektoegang voor de lijst.

### Een lijst maken {#create-a-list}

Een lijst is een groep gerelateerde inhoud die in een lettertypesjabloon als één eenheid kan worden gebruikt. Elke soort inhoud kan aan een lijst worden toegevoegd. Lijsten kunnen ook worden genest. Lijstmodules kunnen worden opgegeven als:

* **GEVOLGEN**: De volgorde kan niet worden gewijzigd in de runtime Correspondentie maken.
* **Bibliotheektoegang**: Gebruikers kunnen modules aan de lijst toevoegen. Deze markering geeft aan of bibliotheektoegang is ingeschakeld. Indien ingeschakeld (open), kan de gebruiker modules aan de lijst toevoegen terwijl de letter wordt voorvertoond.
* Wanneer u een lijst maakt, kunt u een type opgeven, zoals:
* **Normaal**: Er wordt geen extra stijlopmaak toegepast op de lijst.
* **Met opsommingstekens**: Een lijst die is opgemaakt met een eenvoudig opsommingsteken.
* **Genummerd**: Een numerieke lijst met de standaardcijfers (1,2,...), hoger Romeins (I, II, ...) en lager Romeins (i, ii,...).
* **Met briefing**: Een alfabetische lijst met kleine letters (a,b,...) en hoofdletters (A,B,...).
* **Aangepast**: U kunt naar keuze een willekeurig genummerd/met briefhoofd en voor- en achtervoegselwaarden maken.

1. Selecteer **Formulieren** > **Documentfragmenten**.

1. Selecteer **Maken** > **Lijst**.

1. Geef de volgende informatie voor de lijst op:

   * **Titel (optioneel): Voer** de titel voor de lijst in. De titel mag niet uniek zijn en mag speciale tekens en niet-Engelse tekens bevatten. Lijsten worden aangeduid door hun titels (indien beschikbaar), zoals in miniaturen en de eigenschappen van elementen.
   * **Naam:** De unieke naam voor de lijst. Er kunnen in geen enkele staat twee elementen (tekst, voorwaarde of lijst) bestaan met dezelfde naam. In het veld Naam kunt u alleen Engelse tekens, cijfers en afbreekstreepjes invoeren. Het veld Naam wordt automatisch gevuld met de waarde in het veld Titel. De speciale tekens, spaties, getallen en niet-Engelse tekens die in het veld Titel zijn ingevoerd, worden vervangen door afbreekstreepjes in het veld Naam. Hoewel de waarde in het veld Titel automatisch naar de naam wordt gekopieerd, kunt u de waarde bewerken.
   * **Beschrijving (optioneel)**: Typ een beschrijving van het element.
   * **Gegevenswoordenboek (optioneel)**: Selecteer eventueel het gegevenswoordenboek waarmee u verbinding wilt maken. Alleen elementen die hetzelfde gegevenswoordenboek gebruiken als de lijst, of elementen waaraan geen gegevenswoordenboek is toegewezen, kunnen aan de lijst worden toegevoegd. Door een gegevenswoordenboek aan een lijst toe te wijzen, kan de persoon die een lettertypesjabloon maakt, gemakkelijker de juiste lijst vinden.
   * **Tags (optioneel)**: Selecteer de tags die u wilt toepassen. U kunt ook de naam van een nieuwe tag typen en deze maken. (De nieuwe tag wordt gemaakt wanneer u op **Opslaan** tikt.)

1. Tik op **Volgende**.
1. Tik op Element **toevoegen**.
1. Als u elementen aan de lijst wilt toevoegen, selecteert u deze op de pagina Elementen selecteren en tikt u op **Gereed**.

   ![Elementen selecteren om aan de lijst toe te voegen](assets/selectassets.png)

1. De elementen worden toegevoegd aan de pagina Lijstitems.
Als u de volgorde van de elementen in de lijst wilt wijzigen, tikt u op het pijlpictogram ( ![dragndrop](assets/dragndrop.png) ) en houdt u de muisknop ingedrukt. Wanneer de gebruiker een lettertypesjabloon opent in de gebruikersinterface Correspondentie maken, wordt de inhoud samengesteld in de volgorde die u hier hebt gedefinieerd.

   ![Elementen in een lijst opnieuw rangschikken en configureren](assets/listitems.png)

1. U kunt de volgende opties selecteren om te specificeren hoe de lijst zich in het CCR gebruikersinterface gedraagt:

   * **Bibliotheektoegang**: Tik op Library Access om bibliotheektoegang voor het toevoegen van elementen in te schakelen. Wanneer de Toegang van de Bibliotheek wordt toegelaten, beweert aanpast of kan meer inhoud aan de lijst toevoegen. Anders is de functie Aanpassing claims beperkt tot de inhoud die u voor de lijst hebt gedefinieerd.
   * **Vergrendelingsvolgorde**: Tik op Volgorde vergrendelen om de volgorde van de elementen in de lijst te vergrendelen zodat de Aanpasser voor claims de volgorde niet kan wijzigen. Als u deze optie niet selecteert, kan de Aanpassing van claims de volgorde van de lijstitems wijzigen.

   * **Opsommingstekens** toevoegen: Gebruik deze optie om een opsommingsteken of nummeringsstijl toe te passen op de module. U kunt een vooraf ontworpen lijststijl of een aangepaste stijl gebruiken. U kunt ook de tekst opgeven die voor en na elk van de lijstitems moet worden weergegeven.
   * **Pagina-einde**: Selecteer deze optie ( ![onderbreking](assets/break.png)) om een pagina-einde tussen de inhoud van de lijst toe te voegen. Als deze optie niet is geselecteerd ( ![nobreak](assets/nobreak.png)) en de inhoud van de lijst overloopt naar de volgende pagina, wordt de hele lijst verplaatst naar de volgende pagina in plaats van de pagina tussen de lijst te breken.

   * **Toewijzingsconfiguratie**: Met deze optie geeft u het minimale en maximale aantal elementen op dat aan de lijst kan worden toegevoegd.

1. U kunt de volgende opties selecteren om op te geven hoe elk element in de lijst zich gedraagt bij uitvoering:

   * **Bewerkbaar:** Als deze optie is geselecteerd, kan de inhoud worden bewerkt in de gebruikersinterface Correspondentie maken. (Deze optie is niet beschikbaar voor de modules Lijst en Afbeelding.)
   * **Verplicht:** Als deze optie is geselecteerd, is de inhoud vereist in de gebruikersinterface Correspondentie maken.
   * **Geselecteerd:** Als deze optie is geselecteerd, wordt de inhoud vooraf geselecteerd in de gebruikersinterface Correspondentie maken.
   * **Stijl overslaan:** Als deze optie is geselecteerd, slaat de inhoud opsommingstekens en nummering over in de gebruikersinterface Correspondentie maken. (Deze optie is niet beschikbaar voor afbeeldingsmodules. Tussen Stijl, Samenstelling en Lijststijl negeren kan bovendien slechts een van de opties worden toegepast op een module. Een van deze opties kan voor een module worden gebruikt wanneer u Opsommingstekens toevoegen voor een module selecteert.)
   * **Inspringing:** U kunt het inspringingsniveau wijzigen van elke module of inhoud die als onderdeel van de lijst is geselecteerd. De inspringing wordt opgegeven in termen van niveaus (te beginnen met nul), zodat elk inspringingsniveau overeenkomt met een opvulling van 36 punten.
   * **Samengesteld:** Als deze optie is geselecteerd, wordt de samengestelde nummering toegepast als een combinatie van de stijl van de buitenste (bovenliggende) lijst en is het een eigen stijl. De samengestelde nummering in deze geneste lijst is gebaseerd op de volgorde waarin deze geneste lijst wordt weergegeven in de buitenste lijst.
   * **Lijststijl negeren:** Als de optie Samengestelde nummering is uitgeschakeld, is de optie Lijststijl negeren ingeschakeld. Bij deze selectie wordt de eigen stijl van de geneste lijst genegeerd. De nummering gaat verder vanaf de buitenste lijst. Daarom worden de modules van de genestelde lijst behandeld als deel van de buitenlijst zelf, die om het even welke stijlen veronachtzamen die op de genestelde Lijst worden gespecificeerd. Als de optie Lijststijl negeren is uitgeschakeld voor een geneste lijst, hebben de modules die deel uitmaken van die geneste lijst een eigen nummeringsstijl.
   * **Houden bij: Volgende** Hiermee stelt u het pagina-einde in voor de elementen in een lijst. Als u de eigenschap Houden bij volgende van een element in een lijst instelt op **Aan**, blijven dat element en het volgende element op dezelfde pagina staan. Dit houdt in dat de inhoud van het geselecteerde element en het volgende element niet worden verdeeld over pagina&#39;s.

1. Tik op **Opslaan**.

### Tips en trucs {#best-practices-tips-and-tricks}

* Gebruik een consistente naamgevingsconventie om dubbel werk te voorkomen.
* Gebruik de juiste gegevenswoordenboekbinding
* De volgende regels zijn van toepassing wanneer u de List Editor gebruikt om een lijst te wijzigen:

   * Bijwerken van eigenschappen: Toegestaan
   * **Wijziging van gegevenswoordenboek:** Toegestaan totdat er geen item is gekoppeld dat het gegevenswoordenboek gebruikt. U kunt het gegevenswoordenboek niet wijzigen tijdens het bijwerken.

## Voorwaarden {#conditions}

Aan de hand van voorwaarden kunt u bepalen welke inhoud tijdens het aanmaken van de brief of brief wordt opgenomen, op basis van de verschafte gegevens. De voorwaarde wordt beschreven in termen van controlevariabelen. Wanneer u een voorwaarde toevoegt, kunt u verkiezen om een activa op te nemen die op de waarde wordt gebaseerd die de controlevariabele heeft.

Op basis van de opties die u kiest, wordt alleen de eerste expressie die op basis van de huidige voorwaardelijke variabele waar is gevonden, geëvalueerd of alle voorwaarde. Wanneer u de letter in Create Correspondence (CCR) vult, gedragen de voorwaarden zich als &quot;witte vakken&quot;. Als een voorwaarde een lijst oplevert, worden alle verplichte en vooraf geselecteerde items van de lijst uitgevoerd. Als een van deze items voorwaarden zijn of zichzelf opsomt, wordt de resulterende inhoud ook uitgevoerd in de volgorde top-down, depth-first als een platte lijst met tekst en afbeeldingsinhoud. Voorwaarderesultaten kunnen van elk type zijn (tekst, lijst, voorwaarde of afbeelding).

### Uitvoeringsvoorwaarden {#implementing-conditions}

De Condition Editor wordt geleverd met een [Expression Builder](/help/forms/using/expression-builder.md) -gebruikersinterface die het maken van expressies met zowel meerdere plaatsaanduidingen als gegevenswoordenboekelementen ondersteunt. In dergelijke expressies kunt u algemene operanden en lokale/algemene functies gebruiken. Elke expressie kan aan bepaalde inhoud worden gekoppeld en optioneel kan er een standaardsectie zijn als geen van de expressies true oplevert. Alle expressies worden geëvalueerd in de volgorde waarin ze zijn gedefinieerd en de eerste expressies die true retourneren worden geselecteerd en de bijbehorende inhoud wordt geretourneerd door die voorwaardelijke module.

Als de tekst van de voorwaarden in een brief bijvoorbeeld verschilt, afhankelijk van de status waarin de klant zich bevindt en het gegevenswoordenboek een element bevat met de naam &quot;state&quot;, kunt u de voorwaarde als volgt toevoegen:
・ state = NY, selecteert T&amp;C_NY tekst paragraaf・ staat = NC, selecteert T&amp;C_NC tekst paragraaf

Met de Condition-editor kunt u een standaardvoorwaarde opgeven. Als de waarde van de besturingsvariabelen niet overeenkomt met een van de voorwaarden, wordt de inhoud gebruikt die aan de standaardvoorwaarde is gekoppeld. In het volgende voorbeeld kunt u deze voorwaardenrij toevoegen:
・ Standaard, selecteer T&amp;C_Rest

### Een voorwaarde maken {#create-a-condition}

1. Selecteer **Formulieren** > **Documentfragmenten**.
1. Selecteer **Maken > Voorwaarde**.
1. Geef de volgende informatie voor de lijst op:

   * **Titel (optioneel):** Voer de titel voor de voorwaarde in. De titel mag niet uniek zijn en mag speciale tekens en niet-Engelse tekens bevatten. De voorwaarden worden verwezen door hun titels (indien beschikbaar) zoals in duimnagels en activa eigenschappen.
   * **Naam:** De unieke naam voor de voorwaarde. Er kunnen in geen enkele staat twee elementen (tekst, voorwaarde of lijst) bestaan met dezelfde naam. In het veld Naam kunt u alleen Engelse tekens, cijfers en afbreekstreepjes invoeren. Het veld Naam wordt automatisch ingevuld op basis van het veld Titel. De speciale tekens, spaties, getallen en niet-Engelse tekens die in het veld Titel zijn ingevoerd, worden vervangen door afbreekstreepjes in het veld Naam. Hoewel de waarde in het veld Titel automatisch naar de naam wordt gekopieerd, kunt u de waarde bewerken.
   * **Beschrijving (optioneel)** Typ een beschrijving van de voorwaarde.
   * **Gegevenswoordenboek (optioneel)**: Selecteer eventueel het gegevenswoordenboek waarmee u verbinding wilt maken. Alleen elementen die hetzelfde gegevenswoordenboek gebruiken als de voorwaarde, of elementen waaraan geen gegevenswoordenboek is toegewezen, kunnen aan de lijst worden toegevoegd. Door een gegevenswoordenboek aan een lijst toe te wijzen, kan de persoon die een lettertypesjabloon maakt, gemakkelijker de juiste voorwaarde vinden.
   * **Tags (optioneel)**: Selecteer eventueel de tags die u wilt toepassen. U kunt ook de naam van een nieuwe tag typen en deze maken. (De nieuwe tag wordt gemaakt wanneer u op **Opslaan** tikt.)

1. Tik op **Volgende**.
1. Tik op Element **toevoegen**.
1. Als u een element aan de voorwaarde wilt toevoegen, selecteert u het element op de pagina Elementen selecteren en tikt u op **Gereed**. De elementen worden toegevoegd aan het deelvenster Expressie.
1. U kunt de volgende opties selecteren om op te geven hoe de voorwaarde zich gedraagt bij uitvoering:

   * **Meerdere resultaten-evaluatie uitschakelen\Meerdere resultaten-evaluatie** inschakelen: Wanneer deze optie is ingeschakeld (wordt &#39;&#39;Meerdere inschakelen...&#39;&#39; weergegeven), worden alle voorwaarden geëvalueerd en is het resultaat de som van alle werkelijke voorwaarden. Als deze optie is uitgeschakeld (wordt &#39;&#39;Meerdere uitschakelen...&#39;&#39; weergegeven), wordt alleen de eerste voorwaarde waarvan is vastgesteld dat deze true is, geëvalueerd en wordt deze de uitvoer van de voorwaarde.
   * **Pagina-einde**: Selecteer deze optie ( ![onderbreking](assets/break.png)) om een pagina-einde tussen de modules van de voorwaarden toe te voegen. Als deze optie niet is geselecteerd ( ![noBreak](assets/nobreak.png)) en een voorwaarde overloopt naar de volgende pagina, wordt de hele voorwaarde verplaatst naar de volgende pagina in plaats van de pagina tussen de voorwaarde te verbreken.

1. Als u de volgorde van de elementen binnen de voorwaarde wilt wijzigen, tikt u op het pijlpictogram ( ![dragndrop](assets/dragndrop.png) ) en houdt u de muisknop ingedrukt. Wanneer de gebruiker een lettertypesjabloon opent in de gebruikersinterface Correspondentie maken, wordt de inhoud samengesteld in de volgorde die u hier hebt gedefinieerd.
1. Tik op **Verwijderen** om de rij te verwijderen. Als u op Verwijderen tikt voor de standaardrij, worden alleen de elementgegevens gewist.
1. Tik op **Kopiëren** om een rij te dupliceren.
1. Tik op **Bewerken** om het element te wijzigen of de expressie te bewerken.

   Verder:

   * Tik op het mappictogram onder de kolom Element om het element bij te werken.
   * Tik op het mappictogram onder de kolom Expressie om de expressiebouwer te openen en een expressie in te voegen. Voor meer informatie over de Bouwer van de Uitdrukking, zie de Bouwer [van de](/help/forms/using/expression-builder.md)Uitdrukking.

### Tips en trucs {#best-practices-tips-and-tricks-1}

* Gebruik een consistente naamgevingsconventie voor eenvoudig zoeken en om dubbel werk te voorkomen.
* Voorwaarden gedragen zich als case statements, dus de volgorde van condities is belangrijk. De eerste overeenkomst wordt geretourneerd.
* Gebruik de juiste gegevenswoordenboekbinding
* De volgende regels zijn van toepassing wanneer u de Condition Editor gebruikt om een voorwaarde te bewerken:

   * **Toevoeging van variabele:** Toegestaan
   * **Verwijderen van variabele:** Toegestaan
   * **Bijwerken van eigenschappen:** Toegestaan
   * **Wijziging van gegevenswoordenboek:** Toegestaan totdat het gegevenswoordenboekelement niet wordt gebruikt.

## Lay-outfragmenten {#layoutfragments}

Een lay-outfragment is gebaseerd op XDPs die in Ontwerper worden gecreeerd. Als u lay-outfragmenten wilt maken, moet u de XDP&#39;s maken en deze [uploaden naar AEM-formulieren](/help/forms/using/import-export-forms-templates.md).

Een of meer lay-outfragmenten kunnen onderdelen van een letter vormen en de grafische lay-out van die onderdelen definiëren. Een indelingsfragment kan typische formuliervelden bevatten, zoals Adres en Referentienummer, en lege subformulieren die doelgebieden aangeven. Bovendien kunt u met layoutfragmenten tabellen maken en deze in letters invoegen.

Doorgaans worden layout-patronen die u opnieuw kunt gebruiken, gezocht in Letters en worden er lay-outfragmenten voor gemaakt. Bijvoorbeeld de aanhef, het adres en het onderwerpgedeelte van de letter, die in dezelfde volgorde staat als meerdere letters. Een ander voorbeeld kan een tabel zijn met een vergelijkbaar aantal rijen en kolommen die in meerdere letters worden gebruikt.

U kunt een lay-outfragment maken op basis van een bestaande XDP. Een lay-outfragment kan bestaan uit velden en doelgebieden of uit een of meer tabellen. De tabellen in een layout kunnen statisch of dynamisch zijn. Er wordt een XDP gemaakt in Designer en [geüpload naar AEM-formulieren](/help/forms/using/import-export-forms-templates.md). Een XDP kan de structuur of van een lay-outfragment of van een brief vormen. Meer informatie over [lay-outontwerp](/help/forms/using/layout-design-details.md).

Met fragmenten die zijn gebonden aan doelgebieden, kan de letter worden gewijzigd op het moment van ontwerpen. U kunt een lay-outfragment met verschillende afmetingen maken en het juiste fragment kan aan het doelgebied worden gebonden. Met layoutfragmenten kunt u ook enkele tabeleigenschappen aanpassen:

1. U kunt het rij- en kolomaantal verhogen.
1. U kunt de kop- en voettekst opgeven voor meer rijen en kolommen.
1. U kunt de verhouding van de breedte van de tabelkolom definiëren. De grootte van de tabelkolommen bij uitvoering wordt aangepast aan de gedefinieerde verhouding en de beschikbare ruimte. De som van de breedteverhouding moet 100 zijn. Anders is het niet van toepassing.
1. Als een tabel een plaatsaanduiding is (slechts één lege cel bevat), kunt u het type (doelgebied/veld) van nieuwe kolommen definiëren.
1. U kunt kop- en voettekstrijen verbergen.

Creëer vóór het uitvoeren van deze procedure een XFA-fragment met Designer. Het fragment kan tabellen bevatten voor het ordenen van velden en doelgebieden. In Designer kunt u twee typen tabellen maken: statisch en dynamisch. Statische tabellen bevatten een vast aantal rijen. Statische tabellen kunnen doelgebieden en -velden bevatten. Deze doelgebieden en velden kunnen niet worden gebonden aan herhalende DDE&#39;s. Een dynamische tabel kan ook uit één rij bestaan. De gegevens die aan tabelcellen zijn gebonden, bepalen het aantal rijen voor dynamische tabellen. Een dynamische tabel kan alleen velden bevatten. DDEs kan herhalend of niet-herhalend zijn.

Houd rekening met de volgende punten bij het ontwerpen van tabellen:

1. Tabellen kunnen worden aangepast op het moment dat u het fragment maakt. De optie Aanpassen is echter alleen ingeschakeld wanneer het bovenliggende subformulier van de tabel wordt weergegeven.
1. Voor dynamische tabellen gebruiken alle velden, herhaalbare rijen en tabellen &#39;use name binding&#39; voor gegevens die correct worden samengevoegd.
1. Voor dynamische tabellen maken alle herhalende DDE&#39;s die aan de tabelvelden zijn gebonden, deel uit van dezelfde hiërarchie. Voor niet-herhalende DDE&#39;s bestaat een dergelijke beperking niet.
1. Op het moment van het samenvoegen van lay-outfragment in bovenliggende doeltabellen wordt de grootte aangepast aan de beschikbare ruimte, maar de grootte wordt alleen aangepast wanneer het layoutfragment geen doelgebied of veld bevat dat zich direct binnen het bovenste subformulier bevindt. Doelgebied en velden binnen tabel zijn toegestaan.
1. U kunt plaatsaanduidingstabellen maken. Tabellen voor plaatsaanduidingen hebben slechts één lege cel.

* Voor plaatsaanduidingstabellen kunt u de volgende eigenschappen aanpassen op het moment dat het fragment wordt gemaakt.

   * aantal rijen
   * aantal kolommen
   * kop- en voettekst voor elke kolom
   * type (doelgebied/veld) van elke kolom
   * breedteverhouding voor elke kolom

* Voor een niet-plaatsaanduidingstabel kunt u de volgende eigenschappen aanpassen:

   * aantal rijen
   * aantal kolommen
   * kop- en voettekst voor extra kolom
   * breedteverhouding voor elke kolom

U kunt fragmenten in een letter nesten. Dit betekent dat u een fragment kunt toevoegen binnen een fragment. De Correspondence Management-oplossing ondersteunt maximaal vier nestniveaus binnen een letter: **Letter**->**Fragment**->**Fragment**->**Fragment**->**Fragment.**

Zie [Voorbeeld met voorbeeldbestanden voor een gedetailleerd voorbeeld van het gebruik van statische en dynamische tabellen in lay-outfragmenten: statische en dynamische tabellen in een letter](#examplewithsamplefiles)gebruiken.

### Een lay-outfragment maken {#creating-a-layout-fragment}

1. Selecteer **Maken** > **Lay-outfragment**.
1. Correspondence Management geeft de beschikbare XDP&#39;s weer. Selecteer de XDP waarop u het lay-outfragment wilt baseren en tik op **Volgende**.
1. Geef de volgende informatie op voor de indeling:

   * **Titel (optioneel):** Voer de titel in voor het layoutfragment. De titel mag niet uniek zijn en mag speciale tekens en niet-Engelse tekens bevatten. Indelingsfragmenten worden aangeduid met hun titels (indien beschikbaar), zoals miniaturen en elementeigenschappen.
   * **Naam:** De unieke naam voor het lay-outfragment. Er kunnen in geen enkele staat twee elementen (tekst, voorwaarde of lijst) bestaan met dezelfde naam. In het veld Naam kunt u alleen Engelse tekens, cijfers en afbreekstreepjes invoeren. Het veld Naam wordt automatisch ingevuld op basis van het veld Titel. De speciale tekens, spaties, getallen en niet-Engelse tekens die in het veld Titel zijn ingevoerd, worden vervangen door afbreekstreepjes in het veld Naam. Hoewel de waarde in het veld Titel automatisch naar de naam wordt gekopieerd, kunt u de waarde bewerken. Deze naam wordt weergegeven in de lijst in de gebruikersinterface Middelen beheren.
   * **Beschrijving (optioneel)**: Beschrijving die wordt weergegeven in de lijst in de gebruikersinterface Middelen beheren.
   * **Tags (optioneel)**: Selecteer eventueel de tags die u op de voorwaarde wilt toepassen. U kunt ook de naam van een nieuwe tag typen en deze maken.

1. Tik op het tabblad **Tabel** en geef de volgende informatie op voor de indeling:

   * **Configuratie voor**: Selecteer de lijst die wordt gevormd.Als achtervoegsel aan de lijstnaam in dropdown is (Statisch) als de lijst statisch is of (Dynamisch) als de lijst een dynamische lijst is. Statische tabellen bevatten een vast aantal rijen. Statische tabellen kunnen doelgebieden en -velden bevatten. Deze doelgebieden en velden kunnen niet worden gebonden aan herhalende DDE&#39;s. De gegevens die aan tabelcellen zijn gebonden, bepalen het aantal rijen voor dynamische tabellen.

   * **Rijen**: Selecteer het aantal rijen voor de indeling. De gevormde rijtelling moet groter dan of gelijk aan de originele rijtelling zijn.
   * **Kolommen**: Selecteer het aantal kolommen voor de lay-out. De gevormde kolomtelling moet groter dan of gelijk aan de originele kolomtelling zijn.
   Voor elke kolom zijn de volgende gegevens vereist:

   * **Koptekst**: tekst die moet worden weergegeven voor de koptekst
   * **Voettekst**: tekst die moet worden weergegeven voor de voettekst
   * **Type**: type van extra kolom. Veld of doelgebied. Type is ingeschakeld voor statische plaatsaanduidingstabellen. Het type kan op kolomniveau en niet op celniveau worden bepaald. Alle cellen in een uitgebreide kolom zouden van het zelfde type zijn. Voor een dynamische tabel zijn alle kolommen van het veldtype. Voor tabellen zonder plaatsaanduiding kunt u het type van extra kolommen niet definiëren. In dat geval is het type van de extra cellen in de uitgebreide kolom gelijk aan het type van de laatste kolom in die rij; en het type cel in een extra rij is hetzelfde als het type van de laatste cel in die kolom.
   * **Breedteverhouding:** verhouding van de tabelkolombreedten.
   Zie [Voorbeeld met voorbeeldbestanden voor een gedetailleerd voorbeeld van het gebruik van statische en dynamische tabellen in lay-outfragmenten: statische en dynamische tabellen in een letter](#main-pars-header-28)gebruiken.

1. Tik op **Opslaan**.

### Een XDP uploaden naar Correspondentenbeheer {#upload-an-xdp-to-correspondence-management}

Zie Elementen [importeren en exporteren naar AEM-formulieren](/help/forms/using/import-export-forms-templates.md)voor instructies over het uploaden/importeren van een XDP naar Correspondentiebeheer.

### Tips en trucs {#best-practices-tips-and-tricks-2}

#### De standaardbinding voor subformulieren instellen {#set-the-default-subform-binding}

Wanneer u doelgebieden maakt in Designer, kunt u de standaardbinding voor alle nieuwe subformulieren instellen op Geen.

De standaardbinding instellen:

1. Tik in Designer op **Gereedschappen** > **Opties** > **Gegevensbindingen** > **Subformulierbinding**.

1. Selecteer **Geen gegevensbinding in de lijst Standaardbinding voor nieuwe subformulieren**.

Zo zorgt u ervoor dat subformulieren die worden ingevoegd met de opdracht Invoegen > Subformulier of door slepen en neerzetten vanuit het palet Object, standaard de binding &quot;none&quot; hebben. Dit betekent dat elk nieuw subformulier standaard een doelgebied is, tenzij u er inhoud aan toevoegt, de bindingsinstelling wijzigt of het subformulier een naam geeft met het achtervoegsel &quot;_int&quot;.

#### Sectie 508 — Naleving {#section-compliance}

Als de voltooide brief die in de Create Correspondence gebruikersinterface wordt gecreeerd voor het invullen van een recentere werkschema wordt gebruikt. Volg deze aanbevelingen met betrekking tot Sectie 508 wanneer het creëren van de lay-out. Anders is de letter PDF bestemd voor weergave en kunt u deze aanbevelingen negeren:

* Alle subformulieren van het doelgebied en alle velden in een indeling hebben een tabvolgorde.
* Velden met bijschriften zijn standaard 508-compatibel. Het kenmerk /field/assist/speak@priority van het veld is standaard ingesteld op &quot;custom&quot;. Dit betekent dat de schermlezer het bijschrift van het veld leest, tenzij aangepaste schermlezertekst wordt opgegeven.
* Velden zonder bijschriften geven knopinfo op en geven aan dat schermlezers de knopinfo lezen door de instelling

`/field/assist/speak@priority="toolTip"` en geeft u de tekst van de knopinfo op in `/field/assist/toolTip`.

#### Datumnotaties in Designer en Asset Configuration Manager {#date-formats-in-designer-and-asset-configuration-manager}

Zorg er tijdens het ontwerpen van een lay-out in Designer voor dat de indelingen voor datumvelden overeenkomen met de datumnotaties die zijn opgegeven in Gegevensweergave-indelingen in [Eigenschappen](/help/forms/using/cm-configuration-properties.md)van Correspondentiebeheer. Zie &quot;Veldwaarden opmaken en patronen gebruiken&quot; in de Help van Designer voor meer informatie.

#### Datumbereiken vastleggen {#capturing-date-ranges}

Wanneer u werkt met een combinatie van datums, zoals startDate - endDate, gebruikt u één subformulier om de correcte uitlijning van de voltooide letter te garanderen en het aantal velden tot een minimum te beperken.

#### Binding op formulierniveau instellen {#setting-form-level-binding}

Wanneer een indeling veel velden en doelgebieden bevat die zijn toegewezen aan één XML-element, gebruikt u binding op formulierniveau en maakt u een afzonderlijk knooppunt voor elk element. Velden die op formulierniveau zijn gebonden, worden genegeerd bij het toewijzen van gegevens in Correspondentiebeheer.

#### Doelgebieden van subformulieren in een basispagina niet gebruiken {#do-not-use-subform-target-areas-in-a-master-page}

Subformulieren zijn bedoeld voor gebieden in een basispagina en zijn niet zichtbaar in de gebruikersinterface Middelen beheren en er kunnen geen gegevens aan worden toegewezen.

#### De juiste posities en typen kiezen voor de doelgebieden {#choosing-appropriate-positions-and-types-for-target-areas}

Let bij het ontwerpen van de indeling op het kiezen van subformulieren. Als de indeling één subformulier bevat, kan het een stroomtype zijn. Nadat u de velden in het subformulier hebt geplaatst, kunt u het subformulier onderbrengen in een ander subformulier, zodat het subformulier met terugloop ook wordt weergegeven en de indeling niet wordt verstoord.

#### Velden op stramienpagina&#39;s plaatsen {#placing-fields-on-master-pages}

Let op het volgende wanneer u een veld op een stramienpagina plaatst:

* De binding van stramienpaginavelden instellen op Globale gegevens gebruiken
* Plaats het veld niet rechtstreeks onder het basisgebied PageArea van de basispagina.
* Plaats het veld in een benoemd subformulier en zorg ervoor dat de binding van het benoemde subformulier is ingesteld op Naam gebruiken.

## Tabellen maken met behulp van lay-outfragmenten {#creating-tables-using-layout-fragments}

Veel lettertypesjablonen bevatten tabellen. Tabellen kunnen statisch zijn, zoals een lijst met voorwaarden, waarbij elke rij één voorwaarde vertegenwoordigt en elk onderdeel in een aparte kolom wordt weergegeven. Tabellen kunnen ook dynamisch zijn, zoals accountgegevens, die informatie bevatten zoals de naam van de klant, de account-id, het transactienummer en het transactiebedrag.

* **Statische tabellen**: Tabellen worden soms gemaakt met rijen met een verschillend aantal kolommen, zoals voor een lijst met voorwaarden. Waar elke rij één voorwaarde vertegenwoordigt en elke voorwaarde kan verschillende subdelen hebben. Elk onderdeel wordt in een aparte kolom weergegeven.
* **Dynamische tabellen**: Indelingsfragmenten bieden de mogelijkheid om de velden van een dynamische tabel te binden aan DDE&#39;s voor verzamelingen. Op het tijdstip van de de lijstrijen van de lettergeneratie worden geproduceerd volgens de grootte van inzameling DDEs.

DD heeft een inzamelingselement Nominee_details dat een samengesteld element met drie primitieve elementen heeft: Nominee_name, Nominee_address en Nominee_gender.
De dynamische XDP heeft ook de zelfde kopballen. Zo kunt u de dynamische XDP gebieden met de bovengenoemde gebieden van DD in kaart brengen.

### Voorbeeld met voorbeeldbestanden: Statische en dynamische tabellen in een letter gebruiken {#examplewithsamplefiles}

In dit voorbeeld wordt getoond hoe u een dynamische en een statische tabel kunt maken, de dynamische tabel aan DDE&#39;s kunt binden en vervolgens een letter kunt maken die deze twee tabellen bevat. Wanneer u met dit voorbeeld werkt, kunt u geheel nieuwe bestanden maken of de invoerbestanden in de stappen gebruiken.

1. Maak een gegevenswoordenboek (DD) dat u in het voorbeeld wilt gebruiken, zoals wordt weergegeven in de afbeelding.

   Selecteer vervolgens DD en exporteer voorbeeldgegevens. Het XML-bestand dat u krijgt, bevat werknemersgegevens en drie instanties voor Nomine_details (standaard worden 3 instanties gedownload. U kunt toevoegen of verwijderen naar wens). Werk de waarden bij en importeer vervolgens de testgegevens in DD. Het CMP-bestand is het pakket en bevat de DD. Zo, voer DD in Correspondence Management in.

   Zie [Gegevenswoordenboek voor meer informatie over het werken met gegevenswoordenboek en testgegevens](/help/forms/using/data-dictionary.md#p-working-with-test-data-p).

   ![Gegevenswoordenboekstructuur](assets/dd.jpeg)

   [Bestand ophalen](assets/exportpackage_1431709897770.cmp.zip)

1. Maak in Designer twee XDP&#39;s (layoutfragmenten): een dynamische tabel en een statische tabel. Voor beide lay-outs:

   * Voeg subformulier toe aan de tabelkolom. Zorg ervoor dat u de indeling van het bovenliggende subformulier van de tabel wijzigt in Stroominhoud en dat u de bindingen van het subformulier uit de tabel verwijdert.
   * Voeg een subformulier toe aan de tabelcel. Zorg ervoor dat u de indeling van het bovenliggende subformulier van de tabel wijzigt in Stroominhoud en dat u de bindingen van het subformulier uit de tabel verwijdert.
   U kunt ook de statische en dynamische XDP&#39;s gebruiken die bij deze stap zijn gevoegd.

   Zie [Lay-outfragmenten voor meer informatie over het werken met lay-outfragmenten](#layoutfragments).
Raadpleeg de Help bij [Designer](https://help.adobe.com/en_US/AEMForms/6.1/DesignerHelp/)voor meer informatie over het ontwerpen van lay-outs.

   [Bestand ophalen](assets/static.xdp.zip)

   [Bestand ophalen](assets/dynamic.xdp.zip)

1. Upload de XDP&#39;s naar AEM-formulieren.
1. Maak een lay-outfragment op basis van de dynamische XDP. Het lusje van de Lijst van de eigenschappen toont dat de lijst dynamisch is (Configuratie voor gebied). Het aantal rijen (1) en kolommen (3) worden afgeleid van het XDP/Layout-fragment.

   De velden van deze indeling worden later gebonden aan de geïmporteerde DD en in de letter wordt het aantal rijen dynamisch gemaakt op basis van het aantal records in het bestand met testgegevens (het XML-gegevensbestand dat is gekoppeld aan de DD).

   ![Een layoutfragmentscherm maken](assets/dynamictableproperties.png)

   Klik om een afbeelding op volledige grootte te openen

1. Maak een lay-outfragment op basis van de statische XDP. Het lusje van de Lijst van de eigenschappen toont dat de lijst statisch is (Configuratie voor gebied). Het aantal rijen (1) en kolommen (3) worden afgeleid van het XDP/Layout-fragment.

   U kunt het aantal kolommen en rijen hier wijzigen. Afhankelijk van wat u in dit scherm kiest, blijft het aantal rijen en kolommen van een statische tabel vast in de letter die met deze indeling wordt gemaakt.
   [ Een layoutfragmentscherm ![maken](assets/statictableproperties.png)](assets/statictableproperties-1.png)

1. Maak een letter met beide lay-outfragmenten erin. Wanneer u dynamische XDP in de brief opneemt, plaats de band van zijn gebieden aan de de inzamelingselementen van het Woordenboek van Gegevens.

   Zie [Letter](/help/forms/using/create-letter.md)maken voor meer informatie over het maken van Letters en Letter-sjablonen.

1. Sla de brief op en geef een voorvertoning weer. Wanneer u een voorvertoning van de letter weergeeft, worden de waarden uit het gegevenswoordenboek in de letter weergegeven. Voor de dynamische tabel zijn er drie rijen. Dit komt doordat de testgegevens drie records voor deze rijen hebben.

   Voor de statische tabel zijn er evenveel rijen en kolommen als u hebt opgegeven bij het maken van het lay-outfragment.

   ![Statische tabel in de letter](assets/statictableletter.png)

   Voor de dynamische tabel worden de drie rijen weergegeven op basis van het aantal records in het bestand met testgegevens. Dit is gebeurd omdat u tijdens het toevoegen van de layout aan de letter een binding hebt gemaakt tussen de velden van de dynamische tabel en de verzamelingselementen van het gegevenswoordenboek. De waarden Naam, Adres en Geslacht worden ingevuld in het bestand met testgegevens dat u hebt gebruikt.

   ![Dynamische tabel in de letter](assets/dynamictableletter.png)

## Een kopie van een documentfragment maken {#create-a-copy-of-a-document-fragment}

Als u snel een documentfragment wilt maken met eigenschappen en inhoud die vergelijkbaar zijn met een bestaand documentfragment, kunt u dit kopiëren en plakken.

1. Selecteer een of meer documentfragmenten in de lijst met documentfragmenten. In de gebruikersinterface wordt het pictogram Kopiëren weergegeven.
1. Tik op Kopiëren. In de gebruikersinterface wordt het pictogram Plakken weergegeven. U kunt er ook voor kiezen om in een map te gaan voordat u gaat plakken. Verschillende mappen kunnen elementen met dezelfde naam bevatten. Zie [Mappen en elementen](/help/forms/using/import-export-forms-templates.md#folders-and-organizing-assets)ordenen voor meer informatie over mappen.
1. Tik op Plakken. Het dialoogvenster Plakken wordt geopend. Als u de documentfragmenten op dezelfde plaats kopieert en plakt, wijst het systeem automatisch namen en titels toe aan de nieuwe exemplaren van letters, maar u kunt de titels en namen van de letters bewerken.
1. Bewerk indien nodig de titel en de naam waarmee u de kopie van het documentfragment wilt opslaan.
1. Tik op Plakken. De kopie van het documentfragment wordt gemaakt.

