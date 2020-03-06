---
title: Zoek digitale activa en beelden in AEM
description: Leer hoe te om de vereiste activa in AEM te vinden door het paneel van Filters te gebruiken, en hoe te om de activa te gebruiken die in onderzoek verschijnen.
contentOwner: AG
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: c491b77dac1bf25b9e348ed12d16ed7894e5493e

---


# Zoekmiddelen in AEM {#search-assets-in-aem}

De Activa van de Manager van de Ervaring van Adobe (AEM) verstrekt robuuste methodes van de activaontdekking die u helpen hogere inhoudssnelheid bereiken. Uw teams verminderen tijd aan markt met naadloze, intelligente onderzoekservaring gebruikend uit-van-de-doosfunctionaliteit en douanemethodes. Het zoeken naar middelen is van essentieel belang voor het gebruik van een digitaal systeem voor het beheer van activa — of het nu gaat om verder gebruik door creatieven, voor een robuust beheer van activa door zakelijke gebruikers en marketeers, of voor beheer door DAM-beheerders. Eenvoudige, geavanceerde en aangepaste zoekopdrachten die u via de gebruikersinterface van AEM Assets of andere toepassingen en oppervlakken kunt uitvoeren, helpen deze gebruiksgevallen te vervullen.

AEM steunt de volgende gebruiksgevallen en dit artikel beschrijft het gebruik, de concepten, de configuraties, de beperkingen, en het oplossen van problemen voor deze gebruiksgevallen.

| Assets doorzoeken | Configuratie en beheer | Werken met zoekresultaten |
|---|---|---|
| [Basiszoekopdrachten](#searchbasics) | [Zoekindex](#searchindex) | [Sorteerresultaten](#sort) |
| [Zoekinterface begrijpen](#searchui) | [Visuele of gelijkenis zoeken](#configvisualsearch) | [De eigenschappen en de meta-gegevens van de controle van activa](#checkinfo) |
| [Zoeksuggesties](#searchsuggestions) | [Verplichte metagegevens](#mandatorymetadata) | [Downloaden](#download) |
| [Begrijp onderzoeksresultaten en gedrag](#searchbehavior) | [Zoekfacetten wijzigen](#searchfacets) | [Bulksgewijze metagegevensupdates](#metadataupdates) |
| [Zoekrang en opvoeren](#searchrank) | [Tekstextractie](#extracttextupload) | [Slimme verzamelingen](#collections) |
| [Geavanceerd zoeken: filteren en toepassingsgebied van de zoekopdracht](#scope) | [Aangepaste voorspellingen](#custompredicates) | [Begrijp onverwachte resultaten en los problemen op](#troubleshoot-unexpected-search-results-and-issues) |
| [Zoeken op andere oplossingen en toepassingen](#beyondomnisearch):<ul><li>[Adobe Asset Link](#aal)</li><li>[Merk Portal](#brandportal)</li><li>[AEM-desktop-app](#desktopapp)</li><li>[Adobe Stock-afbeeldingen](#adobestock)</li><li>[Dynamische media-elementen](#dynamicmedia)</li></ul> |  |  |
| [Selector/kiezer van bedrijfsmiddelen](#assetselector) |  |  |
| [Beperkingen](#limitations) en [tips](#tips) |  |  |
| [Illustratieve voorbeelden](#samples) |  |  |

Zoek naar activa die het gebied van het Onderzoek bij de bovenkant van de AEM Webinterface gebruiken. Ga naar **[!UICONTROL Activa]** > **[!UICONTROL Dossiers]** in AEM, klik onderzoekspictogram in hoogste bar, ga onderzoekssleutelwoord in, en druk terugkeer. Alternatief, gebruik de sleutelwoordkortere weg/(voorwaartse schuine streep) om het gebied van het Onderzoek te openen. Locatie:de middelen zijn vooraf geselecteerd om de zoekopdrachten te beperken tot DAM-middelen. AEM verstrekt suggesties aangezien uw begin een onderzoekssleutelwoord typt.

Gebruik het paneel van **[!UICONTROL Filters]** om uw onderzoek te versmallen door onderzoeksresultaten te filtreren die op de diverse opties (predikaten) worden gebaseerd, zoals dossiertype, dossiergrootte, laatste gewijzigde datum, status van activa, inzichten gegevens, en het verlenen van vergunningen van de Voorraad van Adobe. Uw beheerders kunnen het paneel van Filters aanpassen en onderzoeksvoorspelling toevoegen of verwijderen gebruikend onderzoeksfacetten.

De het onderzoekscapaciteit van AEM steunt het zoeken naar inzamelingen en het zoeken naar activa binnen een inzameling. Zie [zoekverzamelingen](/help/assets/managing-collections-touch-ui.md).

## Begrijp onderzoeksinterface {#searchui}

Vertrouwd me met de onderzoeksinterface en de beschikbare acties.

![Het begrip van delen van de interface van de onderzoeksresultaten van Activa](assets/aem_search_results.png)

*Afbeelding: Het begrip van delen van de interface van de onderzoeksresultaten van Activa*

**A.** Sla de zoekopdracht op als een slimme verzameling. **B.** Filters (predicaten) om de zoekresultaten te verfijnen. **C.** Geef bestanden, mappen of beide weer in de zoekresultaten. **D.** Klik op Filters om het linkerspoor te openen of te sluiten. **E.** Zoeklocatie is DAM. **F.** Het gebied van het onderzoek met user-provided onderzoekssleutelwoord. **G.** Schakel het selectievakje in om alle zoekresultaten te selecteren. **H.** Aantal getoonde onderzoeksresultaten uit de totale onderzoeksresultaten. **Ik.** Sluit de zoekopdracht **J.** Schakelaar tussen kaartmening en lijstmening.

### Dynamische zoekfacetten {#dynamicfacets}

U kunt de gewenste activa van de pagina van onderzoeksresultaten sneller ontdekken gebruikend het dynamisch bijgewerkte aantal verwachte onderzoeksresultaten in de onderzoeksfacetten. Het verwachte aantal activa wordt bijgewerkt zelfs alvorens de onderzoeksfilter toe te passen. Het zien van de verwachte telling tegen de filter helpt u door de onderzoeksresultaten snel en efficiënt navigeren. Voor meer informatie, zie de activa van het [Onderzoek in AEM](search-assets.md).

![Zie het benaderende aantal activa zonder het filtreren onderzoeksresultaten in onderzoeksfacetten.](assets/asset_search_results_in_facets_filters.png)

*Afbeelding: Zie het benaderende aantal activa zonder het filtreren onderzoeksresultaten in onderzoeksfacetten.*

## Begrijp onderzoeksresultaten en gedrag {#searchbehavior}

### Basiszoektermen en resultaten {#searchbasics}

U kunt sleutelwoordonderzoeken van het gebied in werking stellen OmniSearch. Het sleutelwoordonderzoek is niet hoofdlettergevoelig en is een full-text onderzoek (over de populaire meta-gegevensgebieden. Als meer dan één sleutelwoord wordt gezocht naar, is de standaardexploitant tussen de sleutelwoorden `AND` voor standaardonderzoek en het is `OR` wanneer de activa slim geëtiketteerd zijn.

De resultaten worden gesorteerd door relevantie, beginnend met dichtste gelijken. Voor veelvoudige sleutelwoorden, zijn de relevantere resultaten de activa die beide termijnen in hun meta-gegevens bevatten. Binnen meta-gegevens, worden de sleutelwoorden die als slimme markeringen verschijnen hoger gerangschikt dan sleutelwoorden die op andere meta-gegevensgebieden verschijnen. AEM staat het geven van een bepaalde onderzoekstermijn toe hoger gewicht. Ook is het mogelijk om de rang [van een paar doelactiva voor specifieke onderzoekstermijnen te](#searchrank) verhogen.

Om de relevante activa snel te vinden, verstrekt de rijke interface het filtreren, het sorteren, en selectiemechanismen. U kunt resultaten filtreren die op veelvoudige criteria worden gebaseerd en aantal gezochte activa voor diverse filters zien. Alternatief, kunt u onderzoek opnieuw uitvoeren door de vraag op het gebied van het Onderzoek te veranderen. Wanneer u uw onderzoekstermijnen of filters verandert, blijven de andere filters van toepassing om de context van uw onderzoek te bewaren.

Wanneer de resultaten vele activa zijn, toont AEM eerste 100 in de kaartmening en 200 in de lijstmening. Aangezien de gebruikers scrollen, worden meer activa geladen. Dit is om de prestaties te verbeteren.

>[!VIDEO](https://www.youtube.com/watch?v=LcrGPDLDf4o)

Soms, kunt u sommige onverwachte activa in de onderzoeksresultaten zien. Voor meer info, zie [onverwachte resultaten](#troubleshoot-unexpected-search-results-and-issues).

AEM kan vele dossierformaten zoeken en de onderzoeksfilters kunnen worden aangepast om uw bedrijfsvereisten aan te passen. Neem contact op met uw beheerder om te begrijpen welke zoekopties beschikbaar worden gesteld voor uw DAM-opslagplaats en welke beperkingen uw account heeft.

### Resultaten met en zonder Verbeterde Slimme Markeringen {#withsmarttags}

Door gebrek, combineert het onderzoek AEM de onderzoekstermijnen met een EN clausule. Bijvoorbeeld, denk na zoekend naar sleutelwoordvrouw lopend. Slechts verschijnen de activa met zowel vrouw als lopende sleutelwoorden in de meta-gegevens in de onderzoeksresultaten door gebrek. Het zelfde gedrag wordt behouden wanneer de speciale karakters (periodes, onderstreept, of streepjes) met de sleutelwoorden worden gebruikt. De volgende onderzoeksvragen keren de zelfde resultaten terug:

* `woman running`
* `woman.running`
* `woman-running`

Nochtans, `woman -running` keert de vraag activa zonder `running` in hun meta-gegevens terug.
Het gebruiken van slimme markeringen voegt een extra `OR` clausule toe om het even welke onderzoekstermijnen als toegepaste slimme markeringen te vinden. Een activa die met of `woman` of of het gebruiken van Slimme Markeringen wordt geëtiketteerd `running` verschijnen ook in zulk een onderzoeksvraag die. De zoekresultaten zijn dus een combinatie van:

* De activa met `woman` en de `running` sleutelwoorden in de meta-gegevens (standaardgedrag).

* Slimme activa die met één van beiden van de sleutelwoorden worden geëtiketteerd (het Slimme gedrag van Markeringen).

### Zoeksuggesties bij het typen {#searchsuggestions}

Wanneer u sleutelwoorden begint te typen, stelt AEM de mogelijke onderzoekssleutelwoorden of de uitdrukkingen voor. De suggesties zijn gebaseerd op de meta-gegevens van de bestaande activa. AEM indexeert alle meta-gegevensgebieden om met onderzoek te helpen. Om onderzoekssuggesties te verstrekken, gebruikt het systeem de waarden van de volgende weinig meta-gegevensgebieden. Om onderzoekssuggesties te verstrekken, overweeg bevolkend de volgende gebieden met aangewezen sleutelwoorden:

* Asset-tags. (kaarten naar `jcr:content/metadata/cq:tags`)
* Benaming van activa. (kaarten naar `jcr:content/metadata/dc:title`)
* Beschrijving van de activa. (kaarten naar `jcr:content/metadata/dc:description`)
* Titel in de JCR-databank. De waarde kan aan de titel van Activa in kaart worden gebracht. (kaarten naar `jcr:content/jcr:title`)
* Beschrijving in de JCR-databank. De waarde kan aan de beschrijving van Activa in kaart worden gebracht. (kaarten naar `jcr:content/jcr:description`)

Om suggesties voor meer dan één onderzoekssleutelwoorden te ontvangen, blijf alle sleutelwoorden typen zonder enige suggestie voor één enkel sleutelwoord te selecteren.

![Typ veelvoudige sleutelwoorden om suggesties te bekijken die hen allen passen](assets/search_suggestionsmanykeywords.gif)

*Afbeelding: Typ veelvoudige sleutelwoorden om suggesties te bekijken die hen allen passen*

### Rangschikking en boeking zoeken {#searchrank}

De onderzoeksresultaten die alle onderzoekstermijnen op meta-gegevensgebieden aanpassen worden eerst getoond, gevolgd door de onderzoeksresultaten die om het even welke onderzoekstermijnen in de slimme markeringen aanpassen. In het bovenstaande voorbeeld, is de benaderende orde van vertoning van onderzoeksresultaten:

1. De gelijken van `woman running` op de diverse meta-gegevensgebieden.
1. Overeenkomsten van `woman running` in slimme tags.
1. Matches van `woman` of van `running` in slimme tags.

U kunt de relevantie van sleutelwoorden voor bepaalde activa verbeteren helpen onderzoeken opvoeren die op de sleutelwoorden worden gebaseerd. Met andere woorden, de beelden waarvoor u specifieke sleutelwoorden bevordert verschijnen bij de bovenkant van de onderzoeksresultaten wanneer u die op deze sleutelwoorden zoekt.

1. Open vanuit de gebruikersinterface Assets de pagina met eigenschappen voor de asset. Klik op **[!UICONTROL Geavanceerd]** en klik op **[!UICONTROL Toevoegen]** onder **[!UICONTROL Hoogte voor zoektrefwoorden]**.
1. In het **[!UICONTROL Onderzoek promote]** vakje, specificeer een sleutelwoord waarvoor u het onderzoek naar het beeld wilt opvoeren en dan klikken/de kraan **[!UICONTROL toevoegt]**. U kunt veelvoudige sleutelwoorden op de zelfde manier specificeren.
1. Klik/tik op **[!UICONTROL Opslaan en sluiten]**. De activa die u voor dit sleutelwoord bevorderde verschijnen onder de hoogste onderzoeksresultaten.

U kunt dit aan uw voordeel gebruiken door de rang van sommige activa in de onderzoeksresultaten voor het gerichte sleutelwoord op te voeren. Zie de voorbeeldvideo hieronder. Voor gedetailleerde informatie, zie [onderzoek in AEM](https://helpx.adobe.com/experience-manager/kt/assets/using/search-feature-video-use.html).

>[!VIDEO](https://video.tv.adobe.com/v/16766/?quality=6)

*Begrijp hoe de onderzoeksresultaten gerangschikt zijn en hoe de rang kan worden beïnvloed.*

## Geavanceerd zoeken {#scope}

AEM verstrekt diverse methodes zoals filters die op de bezochte activa van toepassing zijn, om u te helpen van de gewenste activa de plaats bepalen sneller. Hieronder worden enkele algemeen gebruikte methoden beschreven. Enkele [geïllustreerde voorbeelden](#samples) worden hieronder gedeeld.

**Zoeken naar bestanden of mappen**: In de onderzoeksresultaten, zie of dossiers, omslagen, of allebei. Van het paneel van **[!UICONTROL Filters]** , kunt u de aangewezen optie selecteren. Zie [onderzoeksinterface](#searchui).

**Zoeken naar elementen in een map**: U kunt het onderzoek tot een specifieke omslag beperken. In het paneel van **[!UICONTROL Filters]** , voeg weg van een omslag toe. U kunt slechts één omslag tegelijkertijd selecteren.

![De onderzoeksresultaten van de grens aan een omslag door een omslagweg in het paneel van Filters toe te voegen](assets/search_folder_select.gif)

*Afbeelding: De onderzoeksresultaten van de grens aan een omslag door een omslagweg in het paneel van Filters toe te voegen*

### Vergelijkbare afbeeldingen zoeken {#visualsearch}

To find images that are visually similar to a user-selected image, click **[!UICONTROL Find Similar]** option from the card view of an image or from the toolbar. AEM geeft de slimme getagde afbeeldingen uit de DAM-opslagplaats weer die lijken op een door de gebruiker geselecteerde afbeelding. Zie [Zoeken naar overeenkomsten configureren](#configvisualsearch).

![Vind gelijkaardige beelden gebruikend de optie in de kaartmening](assets/search_find_similar.png)

*Afbeelding: Vind gelijkaardige beelden gebruikend de optie in de kaartmening*

### Adobe Stock-afbeeldingen {#adobestock}

Van binnen het gebruikersinterface AEM, kunnen de gebruikers de activa [van de Voorraad van](/help/assets/aem-assets-adobe-stock.md) Adobe zoeken en de vereiste activa in licentie geven. Voeg `Location: Adobe Stock` in de bar van het Onderzoek toe. U kunt het paneel van Filters ook gebruiken om alle gelicentieerde of niet vergunning gegeven activa te vinden of een specifieke activa te zoeken gebruikend het dossieraantal van de Voorraad van Adobe.

### Dynamische media-elementen {#dmassets}

You can filter for Dynamic Media images by selecting **[!UICONTROL Dynamic Media > Sets]** from the **[!UICONTROL Filters]** panel. Het filtert op en toont assets zoals afbeeldingsets, carrousels, gemengde mediasets, en spinsets.

### Zoeken met specifieke waarden in metagegevensvelden {#gqlsearch}

U kunt naar activa zoeken die op nauwkeurige waarden van specifieke meta-gegevensgebieden, zoals, titel, beschrijving, en auteur worden gebaseerd. De eigenschap van het full-text onderzoek GQL haalt slechts die activa de waarvan meta-gegevenswaarde precies uw onderzoeksvraag aanpast. De namen van de eigenschappen (bijvoorbeeld auteur, titel, etc.) en de waarden zijn case-sensitive.

| Metagegevensveld | Facultatieve waarde en gebruik |
|---|---|
| Titel | titel:John |
| Creator | maker:John |
| Locatie | locatie:nvt |
| Beschrijving | beschrijving:&quot;Voorbeeldafbeelding&quot; |
| Gereedschap Creator | creatortool:&quot;Adobe Photoshop CC 2015&quot; |
| Copyright Owner | copyrightowner:&quot;Adobe Systems&quot; |
| Contributor | contribuant:John |
| Gebruiksvoorwaarden | gebruikstermijnen:&quot;CopyRights Reserved&quot; |
| Gemaakt | gemaakt:JJJJ-MM-DDTHH |
| Vervaldatum | verloopt:JJJJ-MM-DDTHH |
| Op tijd | Ontime:JJJJ-MM-DDTHH |
| Off time | offtime:JJJJ-MM-DDTHH |
| Bereik van tijd (verloopt dateontime, offtime) | gezichtsveld : naar beneden...bovengrens |
| Pad | /content/dam/&lt;naam van map> |
| PDF-titel | pdftitle: &quot;Adobe-document&quot; |
| Subject | onderwerp: &quot;Opleiding&quot; |
| Tags | tags:&quot;Locatie en reizen&quot; |
| Type | type:&quot;image\png&quot; |
| Breedte van de afbeelding | breedte:omlaag...bovengrens |
| Hoogte van de afbeelding | hoogte:naar beneden..bovengrens |
| Person | persoon:John |

De eigenschappen weg, de grens, de grootte, en de orde kunnen niet ORed met een ander bezit zijn.

Het sleutelwoord voor een user-generated bezit is zijn gebiedsetiket in de bezitsredacteur in kleine letters, met verwijderde ruimten.

Hier zijn sommige voorbeelden van onderzoeksformaten voor complexe vragen:

* Om alle activa met veelvoudige facetten gebieden (bijvoorbeeld te tonen: title=John Doe en creator hulpmiddel = Adobe Photoshop): `tiltle:"John Doe" creatortool : Adobe*`
* Om alle activa te tonen wanneer de facetwaarde geen één enkel woord maar een zin is (bijvoorbeeld: title=Scott Reynolds): `title:"Scott Reynolds"`
* Om activa met veelvoudige waarden van één enkel bezit (bijvoorbeeld te tonen: title=Scott Reynolds of John Doe): `title:"Scott Reynolds" OR "John Doe"`
* Om activa met bezitswaarden te tonen die met een specifiek koord beginnen (bijvoorbeeld: de titel is Scott Reynolds): `title:Scott*`
* Om activa met bezitswaarden te tonen die met een specifiek koord beëindigen (bijvoorbeeld: de titel is Scott Reynolds): `title:*Reynolds`
* Om activa met een bezitswaarde te tonen die een specifiek koord (bijvoorbeeld bevat: titel = de Zaal van de Vergadering van Bazel): `title:*Meeting*`
* Om activa te tonen die een bepaald koord bevatten en een specifieke bezitswaarde hebben (bijvoorbeeld: onderzoek naar koordAdobe in activa die title=John Doe hebben): `*Adobe* title:"John Doe"`

## De activa van het onderzoek van ander dienstenaanbod AEM of interfaces {#beyondomnisearch}

De Manager van de Ervaring van Adobe (AEM) verbindt de bewaarplaats DAM met diverse andere oplossingen AEM om snellere toegang tot digitale activa te verlenen en de creatieve werkschema&#39;s te stroomlijnen. Om het even welke activaontdekking begint met doorbladeren of onderzoek. Het onderzoeksgedrag blijft grotendeels hetzelfde over de verschillende oppervlakken en oplossingen. Sommige onderzoeksmethodes veranderen aangezien het doelpubliek, de gebruiksgevallen, en het gebruikersinterface over de oplossingen AEM variëren. De specifieke methodes zijn gedocumenteerd voor de individuele oplossingen bij de hieronder verbindingen. De universeel toepasselijke uiteinden en het gedrag zijn gedocumenteerd in dit artikel.

### De activa van het onderzoek van het paneel van de Verbinding van de Activa van Adobe {#aal}

Gebruikend de Verbinding van de Activa van Adobe, kunnen de creatieve beroeps tot inhoud nu toegang hebben die in activa AEM wordt opgeslagen, zonder de gesteunde Adobe Creative Cloud te verlaten apps. Creative kan probleemloos zoeken, zoeken, uitchecken en inchecken in bedrijfsmiddelen via het in-app-paneel in Creative Cloud-toepassingen: Photoshop, Illustrator, en InDesign. De Verbinding van activa staat ook gebruikers toe om visueel gelijkaardige resultaten te zoeken. De visuele resultaten van de onderzoeksvertoning worden aangedreven door de machine het leren van de machine van Adobe Sensei algoritmen en de hulpgebruikers vinden esthetisch gelijkaardige beelden. Zie [onderzoek en doorblader activa](https://helpx.adobe.com/enterprise/using/manage-assets-using-adobe-asset-link.html#UseAdobeAssetLink) gebruikend de Verbinding van de Activa van Adobe.

### Zoekmiddelen in AEM-desktop-app {#desktopapp}

Creatieve beroeps gebruiken Desktop app om de Activa van AEM gemakkelijk doorzoekbaar en beschikbaar op hun lokale Desktop (Win of MAC) te maken. De creatieve producten kunnen de gewenste activa in de Vinder van MAC of de Ontdekkingsreiziger van Vensters gemakkelijk openbaren, die in Desktoptoepassingen worden geopend, en plaatselijk worden veranderd - de veranderingen worden bewaard terug naar AEM met een nieuwe versie die in de bewaarplaats wordt gecreeerd. De toepassing steunt basisonderzoeken gebruikend één of meerdere sleutelwoorden, * en? jokertekens en AND operator. Zie [doorbladeren, zoeken, en voorproefactiva](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html#browse-search-preview-assets) in Desktop app.

### Zoekmiddelen in Brand Portal {#brandportal}

De gebruikers van de lijn-van-zaken en de marketeers gebruiken het Portaal van het Merk om de goedgekeurde digitale activa met hun uitgebreide interne teams, partners, en resellers efficiënt en veilig te delen. Zie [onderzoeksactiva op het Portaal](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/search-capabilities/brand-portal-searching.html)van het Merk.

### Adobe Stockafbeeldingen zoeken {#adobestock-1}

Van binnen het gebruikersinterface AEM, kunnen de gebruikers de activa van de Voorraad van Adobe zoeken en de vereiste activa in licentie geven. Voeg toe `Location: Adobe Stock` op het gebied van Onderzoek. U kunt het paneel van **[!UICONTROL Filters]** ook gebruiken om alle gelicentieerde of niet vergunning gegeven activa te vinden of een specifieke activa te zoeken gebruikend het dossieraantal van de Voorraad van Adobe. Zie Adobe Stock-afbeeldingen [beheren in AEM](/help/assets/aem-assets-adobe-stock.md#usemanage).

### Dynamische media zoeken {#dynamicmedia}

U kunt voor de Dynamische beelden van Media filtreren door **[!UICONTROL Dynamische Media]** te selecteren > **[!UICONTROL Reeksen]** van het paneel van **[!UICONTROL Filters]** . Het filtert op en toont assets zoals afbeeldingsets, carrousels, gemengde mediasets, en spinsets. Tijdens het ontwerpen van webpagina&#39;s kunnen auteurs naar sets zoeken in de Inhoudszoeker. Een filter voor sets is beschikbaar in een pop-upmenu.

### De activa van het onderzoek in de Vinder van de Inhoud wanneer het ontwerpen van Web-pagina&#39;s {#contentfinder}

De auteurs kunnen de Vinder van de Inhoud gebruiken om de bewaarplaats van DAM naar de relevante activa te zoeken en de activa in de Web-pagina&#39;s te gebruiken die zij hebben gecreeerd. De auteurs kunnen de Connected Assets-functionaliteit ook gebruiken om te zoeken naar middelen die beschikbaar zijn op een externe AEM-implementatie. De auteurs kunnen deze activa in Web-pagina&#39;s op een lokale plaatsing dan gebruiken AEM. Zie Externe [middelen](/help/assets/use-assets-across-connected-assets-instances.md#use-remote-assets)gebruiken.

### Zoekverzamelingen {#collections}

De het onderzoekscapaciteit van AEM steunt het zoeken naar inzamelingen en het zoeken naar activa binnen een inzameling. Zie [zoekverzamelingen](/help/assets/managing-collections-touch-ui.md).

## Selector van bedrijfsmiddelen {#assetselector}

De selecteur van activa laat u, de activa van DAM op een speciale manier zoeken filtreren en doorbladeren. De selecteur van activa is beschikbaar bij `https://[aem-server]:[port]/aem/assetpicker.html`. U kunt de meta-gegevens van activa halen die u gebruikend de activaselecteur selecteert. U kunt het met gesteunde verzoekparameters, zoals activatype (beeld, video, tekst) en selectiewijze (enige of veelvoudige selecties) lanceren. Deze parameters plaatsen de context van de activaselecteur voor een bepaalde onderzoeksinstantie en blijven intact door de selectie.

De activaselecteur gebruikt het bericht HTML5 Window.postMessage om gegevens voor de geselecteerde activa naar de ontvanger te verzenden. De activaselecteur is gebaseerd op de de stichtingskiezerswoordenschat van Granite. Door gebrek, werkt de activaselecteur op Browse wijze.

U kunt de volgende verzoekparameters in een URL overgaan om de activaselecteur in een bepaalde context te lanceren:

| Naam | Waarden | Voorbeeld | Doel |
|---|---|---|---|
| bronsuffix (B) | De weg van de omslag als middelachtervoegsel in URL:[https://localhost:4502/aem/assetpicker.html/&lt;folder_path>](https://localhost:4502/aem/assetpicker.html) | Om de activaselecteur met een bepaalde geselecteerde omslag te lanceren, bijvoorbeeld met de `/content/dam/we-retail/en/activities` geselecteerde omslag, zou URL van de vorm moeten zijn: [https://localhost:4502/aem/assetpicker.html/content/dam/we-retail/en/activities?assettype=images](https://localhost:4502/aem/assetpicker.html/content/dam/we-retail/en/activities?assettype=images) | Als u vereist dat een bepaalde omslag wordt geselecteerd wanneer de activaselecteur wordt gelanceerd, ging het als middelachtervoegsel over. |
| modus | enkelvoudig, meervoudig | <ul><li>[https://localhost:4502/aem/assetpicker.html?mode=single](https://localhost:4502/aem/assetpicker.html?mode=single)</li><li>[https://localhost:4502/aem/assetpicker.html?mode=multiple](https://localhost:4502/aem/assetpicker.html?mode=multiple)</li></ul> | Op veelvoudige wijze, kunt u verscheidene activa gelijktijdig selecteren gebruikend de activaselecteur. |
| mimetype | nabootsing(en) (`/jcr:content/metadata/dc:format`van) een actief (ook ondersteunde vervanging) | <ul><li>[https://localhost:4502/aem/assetpicker.html?mimetype=image/png](https://localhost:4502/aem/assetpicker.html?mimetype=image/png)</li><li>[https://localhost:4502/aem/assetpicker.html?mimetype=*png](https://localhost:4502/aem/assetpicker.html?mimetype=*png)</li><li>[https://localhost:4502/aem/assetpicker.html?mimetype=*presentation](https://localhost:4502/aem/assetpicker.html?mimetype=*presentation)</li><li>[https://localhost:4502/aem/assetpicker.html?mimetype=*presentation&amp;mimetype=*png](https://localhost:4502/aem/assetpicker.html?mimetype=*presentation&mimetype=*png)</li></ul> | Gebruik het om activa te filtreren die op MIME type(n) worden gebaseerd |
| dialoog | waar, vals | [https://localhost:4502/aem/assetpicker.html?dialog=true](https://localhost:4502/aem/assetpicker.html?dialog=true) | Gebruik deze parameters om de activaselecteur als Granite Dialoog te openen. Deze optie is slechts van toepassing wanneer u de activaselecteur door het Gebied van de Weg van de Graniet lanceert, en vormt het als plukkerSrc URL. |
| assettype (S) | afbeeldingen, documenten, multimedia, archieven | <ul><li>[https://localhost:4502/aem/assetpicker.html?assettype=images](https://localhost:4502/aem/assetpicker.html?assettype=images)</li><li>[https://localhost:4502/aem/assetpicker.html?assettype=documents](https://localhost:4502/aem/assetpicker.html?assettype=documents)</li><li>[https://localhost:4502/aem/assetpicker.html?assettype=multimedia](https://localhost:4502/aem/assetpicker.html?assettype=multimedia)</li><li>[https://localhost:4502/aem/assetpicker.html?assettype=archives](https://localhost:4502/aem/assetpicker.html?assettype=archives)</li></ul> | Gebruik deze optie aan de types van filteractiva die op de overgegaane waarde worden gebaseerd. |
| wortel | &lt;folder_path> | [https://localhost:4502/aem/assetpicker.html?assettype=images&amp;root=/content/dam/we-retail/en/activities](https://localhost:4502/aem/assetpicker.html?assettype=images&root=/content/dam/we-retail/en/activities) | Gebruik deze optie om de wortelomslag voor de activaselecteur te specificeren. In dit geval, laat de activaselecteur u slechts kindactiva (direct/indirect) onder de wortelomslag selecteren. |

Om tot de interface van de activaselecteur toegang te hebben, ga naar `https://[aem_server]:[port]/aem/assetpicker`. Navigeer aan de gewenste omslag, en selecteer één of meerdere activa. Alternatief, onderzoek naar de gewenste activa van de doos van het Onderzoek, pas filter toe zoals vereist, en selecteer het dan.

![Doorblader en selecteer activa in de activaplukker](assets/assetpicker.png)

*Afbeelding: Doorblader en selecteer activa in de activaplukker*

## Beperkingen {#limitations}

De zoekfunctie in AEM-elementen heeft de volgende beperkingen:

* Ga geen belangrijke ruimte in de onderzoeksvraag in anders niet het onderzoek werkt.
* AEM kan de onderzoekstermijn blijven tonen nadat u eigenschappen van een activa van gezochte resultaten selecteert en dan het onderzoek annuleert. <!-- (CQ-4273540) -->
* Wanneer het zoeken naar omslagen of dossiers en omslagen, kunnen de onderzoeksresultaten niet op om het even welke parameter worden gesorteerd.
* Als u op terugkeer drukt zonder om het even wat in de bar van het Onderzoek te typen, keert AEM een lijst van slechts dossiers en niet omslagen terug. Als u specifiek naar omslagen zoekt zonder een sleutelwoord te gebruiken, keert AEM geen resultaten terug.
* Gebruikend de [!UICONTROL Uitgezochte Alle] controledoos, kunt u de eerste 100 gezochte activa in kaartmening en eerste 200 gezochte activa in lijstmening slechts selecteren. Als u scrolt en meer activa in het gebruikersinterface laadt, kunt u meer selecteren gebruikend de [!UICONTROL Uitgezochte Al] optie.

Het visuele onderzoek of het gelijkenis onderzoek heeft de volgende beperkingen:

* Het visuele onderzoek werkt het best met grotere bewaarplaatsen. Hoewel er geen minimumaantal afbeeldingen vereist is voor goede resultaten, is de kwaliteit van de overeenkomsten met een paar afbeeldingen mogelijk niet zo goed als de resultaten van een grote repository.
* U kunt het model niet veranderen of AEM opleiden om gelijkaardige beelden te vinden. Bijvoorbeeld, verandert het toevoegen van of het verwijderen van slimme markeringen aan een paar activa niet het model. De activa worden uitgesloten van de visueel gelijkaardige onderzoeksresultaten.

De functionaliteit van het onderzoek kan prestatiesbeperkingen in de volgende scenario&#39;s hebben:

* De mening van de kaart heeft een snellere ladingstijd in vergelijking met lijstmening om de onderzoeksresultaten te tonen.

## Zoektips {#tips}

* Bij het toezicht op de status van het overzicht van activa, gebruik de aangewezen optie om te vinden welke activa worden goedgekeurd of activa die in afwachting van goedkeuring zijn.
* Gebruik de Inzichten voorspellen om naar gesteunde activa te zoeken die op hun gebruiksstatistieken worden gebaseerd die van diverse Creatieve apps worden verkregen. De gegevens van het gebruik worden gegroepeerd onder de score van het Gebruik, Impressies, klikken, en de kanalen van Media waar de activa categorieën verschijnen.
* Gebruik het **[!UICONTROL Uitgezochte Al]** controlevakje om de gezochte activa te selecteren. Het selecteert eerste 100 activa in kaartmening en eerste 200 activa in lijstmening. U kunt op de selectie werken, bijvoorbeeld, de geselecteerde activa downloaden, meta-gegevenseigenschappen in bulk voor de geselecteerde activa bijwerken, of de geselecteerde activa toevoegen aan een Inzameling.
* Raadpleeg de [verplichte metagegevens](#mandatorymetadata)om te zoeken naar elementen die niet de verplichte metagegevens bevatten.
* Het onderzoek gebruikt alle meta-gegevensgebieden. Een generisch onderzoek, zoals het zoeken naar 12, keert gewoonlijk vele resultaten terug. Voor betere resultaten, gebruik dubbele (niet enige) citaten of zorg ervoor dat het aantal aan een woord zonder een speciaal karakter (bijvoorbeeld *shoe12*) aangrenzend is.
* Het volledige tekstonderzoek steunt exploitanten zoals -, ^, etc. Om deze brieven als koordliterals te zoeken, sluit de onderzoeksuitdrukking in dubbele citaten in. Bijvoorbeeld, gebruik &quot;Notitieboekje - Schoonheid&quot;in plaats van Notitieboekje - Schoonheid.
* Als de onderzoeksresultaten te veel zijn, beperk het [werkingsgebied van onderzoek](#scope) tot nul-binnen op de gewenste activa. Het werkt het best wanneer u één of ander idee van hebt hoe te om de gewenste activa beter te zoeken, bijvoorbeeld, specifiek dossiertype, specifieke plaats, specifieke meta-gegevens, etc.

* **Etikettering**: De markeringen helpen u activa categoriseren die kunnen efficiënter worden doorbladeren en worden gezocht. Het etiketteren helpt in het verspreiden van de aangewezen taxonomie aan andere gebruikers en werkschema&#39;s. AEM biedt methodes aan om activa automatisch te etiketteren gebruikend de kunstmatig intelligente diensten van Adobe Sensei die beter blijven worden in het etiketteren van uw activa met gebruik en opleiding. Wanneer u naar activa zoekt, worden de slimme markeringen binnen factored als de eigenschap op uw rekening wordt toegelaten. Het werkt samen met de ingebouwde zoekfunctionaliteit van AEM. Zie [zoekgedrag](#searchbehavior). Om de orde te optimaliseren waarin de onderzoeksresultaten worden getoond, kunt u de onderzoeksrangschikking [van een paar uitgezochte activa](#searchrank) opvoeren.

* **Indexering**: Slechts zijn de geïndexeerde meta-gegevens en de activa teruggekeerd in de onderzoeksresultaten. Voor betere dekking en prestaties, verzeker juiste indexering en volg de beste praktijken. Zie [indexeren](#searchindex).

## Enkele voorbeelden ter illustratie van zoekopdracht {#samples}

De dubbele citaten van het gebruik rond sleutelwoorden om activa te vinden die de nauwkeurige uitdrukking in de nauwkeurige orde bevatten zoals die door de gebruiker wordt gespecificeerd.

![Zoekgedrag met en zonder aanhalingstekens](assets/search_with_quotes.gif)

*Afbeelding: Zoekgedrag met en zonder aanhalingstekens*

**Zoeken met sterretje**: Om de opsporing te verbreden, gebruik een asterisk vóór of na het onderzoekswoord om het even welk aantal karakters aan te passen. Bijvoorbeeld, keert het zoeken naar looppas zonder een asterisk geen activa terug die om het even welke variatie van het woord (met inbegrip van in de meta-gegevens) bevatten. Een asterisk vervangt om het even welk aantal karakters. Bijvoorbeeld:

* `run` keert activa met precies looppassleutelwoord terug
* `run*` keert activa met het lopen, looppas, wegloop, etc. terug.
* `*run` terugkeert outrun, opnieuw, etc.
* `*run*` geeft alle mogelijke combinaties terug.

![Het illustreren van gebruik van asteriskvervanging in het onderzoek van Activa dat een voorbeeld gebruikt](assets/search_with_asterisk_run.gif)

*Afbeelding: Het illustreren van gebruik van asteriskvervanging in het onderzoek van Activa dat een voorbeeld gebruikt*

**Zoek met vraagteken vervanging**: Om het onderzoek te verbreden, gebruik één of meerdere &#39;?&#39;? tekens die overeenkomen met het exacte aantal tekens. Bijvoorbeeld, in de volgende illustratie,

* `run???` de vraag past geen activa aan.

* `run????` de vraag past het woord `running` met vier karakters na aan `run`.

* `??run` de vraag past het woord `rerun` met twee karakters vóór aan `run`.

![Het illustreren van gebruik van vraagteken vervanging in het onderzoek van Activa dat een voorbeeld gebruikt](assets/search_with_questionmark_run.gif)

*Afbeelding: Het illustreren van gebruik van vraagteken vervanging in het onderzoek van Activa dat een voorbeeld gebruikt*

**Sluit een sleutelwoord** uit: Het streepje van het gebruik aan onderzoek naar activa die geen sleutelwoord bevatten. Bijvoorbeeld, keert de `running -shoe` vraag activa terug die bevatten `running`, maar niet `shoe`. Op dezelfde manier keert de `camp -night` vraag activa terug die `camp` maar niet bevatten `night`. Merk op dat de `camp-night` vraag activa terugkeert die zowel `camp` als `night`. bevatten.

![Gebruik van streepje om naar activa te zoeken die geen uitgesloten sleutelwoord bevatten](assets/search_dash_exclude_keyword.gif)

*Afbeelding: Gebruik van streepje om naar activa te zoeken die geen uitgesloten sleutelwoord bevatten*

## Configuratie- en beheertaken met betrekking tot zoekfunctionaliteit {#configadmin}

### Zoekindexconfiguraties {#searchindex}

De ontdekking van activa baseert zich op indexering van inhoud DAM, met inbegrip van de meta-gegevens. Snellere en nauwkeurige bedrijfsmiddelendetectie is gebaseerd op geoptimaliseerde indexering en geschikte configuraties. Zie [onderzoeksindex](/help/assets/performance-tuning-guidelines.md#search-indexes), [eikenvragen en indexering](/help/sites-deploying/queries-and-indexing.md), en [beste praktijken](/help/sites-deploying/best-practices-for-queries-and-indexing.md).

### Visuele of gelijkenis zoeken {#configvisualsearch}

Het visuele onderzoek gebruikt het slimme etiketteren en vereist AEM 6.5.2.0 of later. Na het vormen van slimme etiketteringsfunctionaliteit, volg deze stappen.

1. In AEM CRXDE, in `/oak:index/lucene` knoop, voeg de volgende eigenschappen en de waarden toe en sla de veranderingen op.

   * `costPerEntry` eigenschap van type `Double` met de waarde `10`.

   * `costPerExecution` eigenschap van type `Double` met de waarde `2`.

   * `refresh` eigenschap van type `Boolean` met de waarde `true`.
   Deze configuratie staat onderzoeken van de aangewezen index toe.

1. Om de index van Lucene, in CRXDE, bij tot stand te brengen, creeer knoop genoemd `/oak:index/damAssetLucene/indexRules/dam:Asset/properties`van type `imageFeatures` `nt-unstructured`. In `imageFeatures` knoop,

   * Voeg `name` bezit van type `String` met de waarde toe `jcr:content/metadata/imageFeatures/haystack0`.

   * Voeg `nodeScopeIndex` bezit van type `Boolean` met de waarde van toe `true`.

   * Voeg `propertyIndex` bezit van type `Boolean` met de waarde van toe `true`.

   * Voeg `useInSimilarity` bezit van type `Boolean` met de waarde toe `true`.
   Sla de wijzigingen op.

1. De toegang `/oak:index/damAssetLucene/indexRules/dam:Asset/properties/predictedTags` en voegt `similarityTags` bezit van type `Boolean` met de waarde van toe `true`.
1. Pas Slimme Markeringen toe op de elementen in uw AEM-opslagplaats. Zie [hoe te om slimme markeringen](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/metadata/smart-tags-technical-video-setup.html)te vormen.
1. In CRXDE, in `/oak-index/damAssetLucene` knoop, plaats het `reindex` bezit aan `true`. Sla de wijzigingen op.
1. (Facultatief) als u hebt aangepast onderzoeksvorm dan kopieer de `/libs/settings/dam/search/facets/assets/jcr%3Acontent/items/similaritysearch` knoop aan `/conf/global/settings/dam/search/facets/assets/jcr:content/items`. Sla alle wijzigingen op.

Voor verwante informatie, zie slimme markeringen in AEM [](https://helpx.adobe.com/experience-manager/kt/assets/using/smart-tags-feature-video-understand.html) begrijpen en [hoe te om slimme markeringen](/help/assets/managing-smart-tags.md)te beheren.

### Verplichte metagegevens {#mandatorymetadata}

De bedrijfsgebruikers, de beheerders, of de bibliotheken van DAM kunnen sommige meta-gegevens als verplichte meta-gegevens bepalen die voor de bedrijfsprocessen aan het werk moeten zijn. Om diverse redenen, kunnen sommige activa deze meta-gegevens missen, zoals erfenisactiva of activa die in bulk worden gemigreerd. De activa met ontbrekende of ongeldige meta-gegevens worden ontdekt en worden gemeld gebaseerd op het geïndexeerde meta-gegevensbezit. Om het te vormen, zie [verplichte meta-gegevens](/help/assets/metadata-schemas.md#define-mandatory-metadata).

### Zoekfacetten wijzigen {#searchfacets}

Om de snelheid van ontdekking te verbeteren, biedt de Activa van AEM onderzoeksfacetten aan gebruikend die u de onderzoeksresultaten kunt filtreren. Het paneel van Filters omvat een paar standaardfacetten door gebrek. De beheerders kunnen het paneel van Filters aanpassen om de standaardfacetten te wijzigen gebruikend de in-gebouwde predikaten. AEM verstrekt een goede inzameling van ingebouwde predikaten en een redacteur om de facetten aan te passen. Zie [zoekfacetten](/help/assets/search-facets.md).

### Tekst uittrekken bij het uploaden van elementen {#extracttextupload}

U kunt AEM vormen om de tekst uit de activa te halen wanneer de gebruikers activa, zoals Psd of Pdf- dossiers uploaden. AEM indexeert de gehaalde tekst en helpt gebruikers die activa zoeken op de gehaalde tekst worden gebaseerd. Zie [upload elementen](/help/assets/managing-assets-touch-ui.md#uploading-assets).

### De predikaten van de douane aan de resultaten van het filteronderzoek {#custompredicates}

De voorspelling wordt gebruikt om facetten tot stand te brengen. De beheerders kunnen de onderzoeksfacetten in het paneel van Filters aanpassen gebruikend pre-gevormde predikaten. Deze voorspelling kan worden aangepast gebruikend bekledingen. Zie aangepaste voorspelling [maken](/help/assets/searchx.md).

U kunt naar digitale activa zoeken die op één of meer van de volgende eigenschappen worden gebaseerd. De filters die op sommige van deze eigenschappen van toepassing zijn zijn beschikbaar door gebrek en sommige andere filters kunnen worden douane-gecreeerd om op de andere eigenschappen van toepassing te zijn.

| Zoekveld | De bezitswaarden van het onderzoek |
|---|---|
| MIME-typen | Afbeeldingen, documenten, multimedia, archieven of andere documenten. |
| Laatst gewijzigd | Uur, Dag, Week, Maand, of Jaar. |
| Bestandsgrootte | Klein, middelgroot, of Groot. |
| Status publiceren | Gepubliceerd of niet gepubliceerd. |
| Goedgekeurde status | Goedgekeurd of verworpen. |
| Afdrukstand | Horizontale, Verticale, of Vierkant. |
| Stijl | Kleur, of Zwart &amp; Wit. |
| Videohoogte | Als minimum en maximumwaarde gespecificeerd. De waarde wordt opgeslagen in de meta-gegevens van videovertolkingen slechts. |
| Videobreedte | Als minimum en maximumwaarde gespecificeerd. De waarde wordt opgeslagen in de meta-gegevens van videovertolkingen slechts. |
| Video-indeling | DVI, Flits, MPEG4, MPEG, OGG Theora, QuickTime, de Media van Vensters. De waarde wordt opgeslagen in de meta-gegevens van de bronvideo en om het even welke vertolkingen. |
| Videocodec | x264. De waarde wordt opgeslagen in de meta-gegevens van videovertolkingen slechts. |
| Videobitrate | Als minimum en maximumwaarde gespecificeerd. De waarde wordt opgeslagen in de meta-gegevens van videovertolkingen slechts. |
| Audio-codec | Libvorbis, Lame MP3, AAC-codering. De waarde wordt opgeslagen in de meta-gegevens van videovertolkingen slechts. |
| Audio-bitrate | Als minimum en maximumwaarde gespecificeerd. De waarde wordt opgeslagen in de meta-gegevens van videovertolkingen slechts. |

## Werken met zoekresultaten voor bedrijfsmiddelen {#aftersearch}

Zodra u sommige gezochte activa ziet die uw criteria aanpassen, kunt u de volgende typische taken met doen of de volgende acties op deze onderzoeksresultaten ondernemen:

* De meta-gegevenseigenschappen van de mening en andere informatie.
* Download één of meerdere activa.
* Gebruik de Acties van de Desktop om deze activa in Desktop app te openen.
* Maak slimme collecties.

### Gezochte resultaten sorteren {#sort}

Door de zoekresultaten te sorteren kunt u sneller de vereiste asset vinden. Sorting search results works in list view and only when you select **[!UICONTROL [Files](#searchui)]**from the**[!UICONTROL  Filters ]**panel. AEM Assets gebruikt sorteren op de server om snel alle assets (hoe talrijk ook) in een map of de resultaten van een zoekopdracht te sorteren. Sorteren op de server levert sneller en nauwkeuriger resultaten op dan sorteren op de client.

In lijstmening, kunt u de onderzoeksresultaten sorteren enkel aangezien u activa in om het even welke omslag kunt sorteren. Het sorteren werkt aan deze kolommen — Naam, Titel, Status, Afmetingen, Grootte, Rating, Gebruik, (Datum) gecreeerd, (Datum) Gewijzigd, (Datum) Gepubliceerd, Werkschema, en Uitgecheckt.

Voor beperkingen van soortfunctionaliteit, zie [beperkingen](#limitations).

### Gedetailleerde informatie over een actief controleren {#checkinfo}

U kunt gedetailleerde informatie van een gezocht activa van de pagina van het onderzoeksresultaat controleren.

Om alle meta-gegevens van activa te zien, selecteer de activa en klik **[!UICONTROL eigenschappen]** van de toolbar.

Als u de opmerkingen over een asset of de versiegeschiedenis van een asset wilt controleren, klikt u op de asset om een voorvertoning op grote grootte te openen. Open timeline in the left rail and select **[!UICONTROL Comments]** or **[!UICONTROL Versions]**. U kunt de tijdlijnactiviteit zoals opmerkingen of versies ook in chronologische volgorde sorteren.

![De chronologieingangen van de soort voor een onderzoeksactiva](assets/sort_timeline_search_results.gif)

*Afbeelding: De chronologieingangen van de soort voor een onderzoeksactiva*

### Gezochte activa downloaden {#download}

U kunt de bezochte activa en hun vertolkingen downloaden enkel aangezien u regelmatige activa van omslagen downloadt. Selecteer één of meerdere activa van de onderzoeksresultaten en klik **[!UICONTROL Download]** van de toolbar.

### Bulksgewijs bijwerken metagegevenseigenschappen {#metadataupdates}

Het is mogelijk om bulkupdates aan de gemeenschappelijke meta-gegevensgebieden van veelvoudige activa te maken. Van de onderzoeksresultaten, selecteer één of meerdere activa. Klik **[!UICONTROL Eigenschappen]** van de toolbar en werk de meta-gegevens bij zoals vereist. Klik **[!UICONTROL sparen en sluit]** wanneer gedaan. De eerder bestaande meta-gegevens op de bijgewerkte gebieden is beschreven.

Voor de activa die in één enkele omslag of een inzameling beschikbaar zijn, is het gemakkelijker om de meta-gegevens in bulk [bij te](/help/assets/managing-multiple-assets.md) werken zonder de onderzoeksfunctionaliteit te gebruiken. Voor de activa die over omslagen beschikbaar zijn of een gemeenschappelijke criteria aanpassen, is het sneller om de meta-gegevens in bulk bij te werken door te zoeken.

### Slimme verzamelingen {#collections-1}

Een inzameling is een bevolen reeks activa die activa van verschillende plaatsen kunnen omvatten omdat de inzamelingen slechts verwijzingen naar deze activa bevatten. De inzamelingen zijn van de volgende twee types:

* Een statische verwijzingslijst van activa, omslagen, en andere inzamelingen.
* Een dynamische lijst (slimme inzameling) die activa in de inzameling bevolkt die op een onderzoekscriteria wordt gebaseerd.

U kunt slimme verzamelingen maken op basis van de zoekcriteria. Van het paneel van **[!UICONTROL Filters]** , uitgezochte **[!UICONTROL Dossiers]** en klik **[!UICONTROL sparen Slimme Inzameling]**. Zie [Verzamelingen beheren](/help/assets/managing-collections-touch-ui.md).

## Los onverwachte onderzoeksresultaten en kwesties problemen op {#troubleshoot-unexpected-search-results-and-issues}

| Fout, problemen, symptomen | Mogelijke reden | Mogelijke oplossing of begrip van het probleem |
|---|---|---|
| Onjuiste resultaten wanneer het zoeken naar activa met ontbrekende meta-gegevens | Wanneer het zoeken naar activa die de verplichte meta-gegevens missen, kan AEM sommige activa tonen die geldige meta-gegevens hebben. De resultaten zijn gebaseerd op geïndexeerd meta-gegevensbezit. | Nadat de meta-gegevens worden bijgewerkt, wordt het opnieuw dexeren vereist om op correcte staat van activa meta-gegevens te wijzen. Zie [verplichte metagegevens](metadata-schemas.md#define-mandatory-metadata). |
| Te veel zoekresultaten | Brede zoekparameter. | Denk na beperkend het [werkingsgebied van onderzoek](#scope). Het gebruik van slimme markeringen kan u meer onderzoeksresultaten geven dan u verwachtte. Zie [onderzoeksgedrag met slimme markeringen](#withsmarttags). |
| Onafhankelijke of gedeeltelijk gerelateerde zoekresultaten | Het gedrag van het onderzoek verandert met het slimme etiketteren. | Begrijp [hoe het onderzoek na slim etiketteren verandert](#withsmarttags). |
| Geen automatisch voltooide suggesties voor activa | Nieuw geüploade activa zijn nog niet geïndexeerd. De meta-gegevens zijn niet onmiddellijk beschikbaar als suggesties wanneer u begint een onderzoekssleutelwoord in de bar van het Onderzoek te typen. | De Activa van AEM wacht tot het verstrijken van een onderbrekingsperiode (één uur door gebrek) alvorens een achtergrondbaan in werking te stellen om de meta-gegevens voor alle onlangs geupload of bijgewerkte activa te indexeren en voegt dan de meta-gegevens aan de lijst van suggesties toe. |
| Geen zoekresultaten | <ul><li>Er zijn geen activa die uw vraag aanpassen.</li><li>U voegde whitespace vóór de onderzoeksvraag toe.</li><li>Een niet gestaafd meta-gegevensgebied bevat het sleutelwoord dat u zoekt naar.</li><li>De tijd en de uit tijd wordt gevormd voor activa en het onderzoek werd gemaakt tijdens de off-time van activa.</li></ul> | <ul><li>Zoeken met een ander trefwoord. Alternatief, gebruik (slim) etiketteren om onderzoeksresultaten te verbeteren.</li><li>Het is een [bekende beperking](#limitations).</li><li>Niet worden alle meta-gegevensgebieden overwogen voor onderzoeken. Zie [bereik](#scope).</li><li>Zoek later of wijzig op en uit tijden voor de vereiste activa.</li></ul> |
| Zoekfilter/-voorspelling is niet beschikbaar | <ul><li>De onderzoeksfilter wordt of niet gevormd.</li><li>Het is niet beschikbaar voor uw login.</li><li>(Minder waarschijnlijk) de onderzoeksopties worden niet aangepast op de plaatsing u gebruikt.</li></ul> | <ul><li>De beheerder van het contact om te controleren of zijn de onderzoeksaanpassingen beschikbaar of niet.</li><li>Neem contact op met de beheerder om te controleren of uw account over de rechten/machtigingen beschikt om de aanpassing te gebruiken.</li><li>Neem contact op met de beheerder en controleer de beschikbare aanpassingen voor de implementatie van AEM-middelen die u gebruikt.</li></ul> |
| Bij het zoeken naar visueel vergelijkbare afbeeldingen ontbreekt een verwacht beeld | <ul><li>Afbeelding is niet beschikbaar in AEM.</li><li>Het beeld wordt niet geïndexeerd. Typisch, wanneer het onlangs wordt geupload.</li><li>Het beeld is niet slim geëtiketteerd.</li></ul> | <ul><li>Voeg de afbeelding toe aan AEM-elementen.</li><li>Neem contact op met uw beheerder om de repository opnieuw te indexeren. Ook, zorg ervoor dat u de aangewezen index gebruikt.</li><li>Contacteer uw beheerder om de relevante activa te slim te etiketteren.</li></ul> |
| Bij het zoeken naar visueel vergelijkbare afbeeldingen wordt een irrelevant beeld weergegeven | Visuele zoekgedrag. | AEM toont zoveel mogelijk potentieel relevante activa mogelijk. Minder relevante afbeeldingen, indien aanwezig, worden aan de resultaten toegevoegd, maar met een lagere zoekrangschikking. De kwaliteit van de gelijken en de relevantie van gezochte activa verminderen aangezien u onderaan de onderzoeksresultaten scrolt. |
| Bij het selecteren van en het werken op onderzoeksresultaten, worden alle gezochte activa niet in werking gesteld op | De [!UICONTROL Uitgezochte Al] optie selecteert slechts eerste 100 onderzoeksresultaten in kaartmening en eerste 200 onderzoeksresultaten in lijstmening. |  |

>[!MORELIKETHIS]
>
>* [Handleiding voor AEM-zoekimplementatie](https://docs.adobe.com/content/help/en/experience-manager-learn/sites/developing/search-tutorial-develop.html)
>* [Geavanceerde configuratie van de voorspelling van het multi-value en markeringsonderzoek](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/metadata/search-feature-video-use.html)
>* [Slimme vertaalzoek configureren](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/translation/smart-translation-search-technical-video-setup.html)

