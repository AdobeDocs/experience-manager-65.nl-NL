---
title: Digitale elementen en afbeeldingen zoeken in [!DNL Adobe Experience Manager].
description: Leer hoe u de vereiste elementen vindt in [!DNL Adobe Experience Manager] met het deelvenster Filters en hoe u de elementen gebruikt die in de zoekopdracht worden weergegeven.
contentOwner: AG
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: f5aa1d31f3b31e29073937e044c8fbac27138c4d
workflow-type: tm+mt
source-wordcount: '5720'
ht-degree: 4%

---


# Middelen zoeken in [!DNL Adobe Experience Manager] {#search-assets-in-aem}

[!DNL Adobe Experience Manager Assets] biedt robuuste methoden voor het detecteren van bedrijfsmiddelen die u helpen een hogere snelheid van de inhoud te bereiken. Uw teams kunnen tijd aan markt met naadloze, intelligente onderzoekservaring verminderen gebruikend out-of-the-box functionaliteit en douanemethodes. Het zoeken naar middelen is van cruciaal belang voor het gebruik van een systeem voor het beheer van digitale activa — of het nu gaat om verder gebruik door creatieve ondernemingen, voor een robuust beheer van activa door zakelijke gebruikers en marketeers, of voor beheer door DAM-beheerders. Eenvoudige, geavanceerde en aangepaste zoekopdrachten die u kunt uitvoeren via [!DNL Assets]-gebruikersinterface of andere apps en oppervlakken helpen deze gebruiksgevallen te verhelpen.

[!DNL Experience Manager Assets] steunt de volgende gebruiksgevallen en dit artikel beschrijft het gebruik, de concepten, de configuraties, de beperkingen, en het oplossen van problemen voor deze gebruiksgevallen.

| Assets doorzoeken | Configuratie en beheer | Werken met zoekresultaten |
|---|---|---|
| [Standaardzoekopdrachten](#searchbasics) | [Zoekindex](#searchindex) | [Resultaten sorteren](#sort) |
| [Gebruiksinterface voor zoeken begrijpen](#searchui) | [Zoeken op visuele of gelijkenis](#configvisualsearch) | [Eigenschappen en metagegevens van een element controleren](#checkinfo) |
| [Zoeken in suggesties](#searchsuggestions) | [Verplichte metagegevens](#mandatorymetadata) | [Downloaden](#download) |
| [Zoekresultaten en gedrag begrijpen](#searchbehavior) | [Zoekfacetten wijzigen](#searchfacets) | [Bulkupdates van metagegevens](#metadataupdates) |
| [Zoeken in rang en opvoeren](#searchrank) | [Tekst extraheren](#extracttextupload) | [Slimme verzamelingen](#collections) |
| [Geavanceerd zoeken: filteren en zoekbereik](#scope) | [Aangepaste voorspelling](#custompredicates) | [Onverwachte resultaten begrijpen en problemen oplossen](#unexpectedresults) |
| [Zoeken in andere oplossingen en apps](#beyondomnisearch):<ul><li>[Adobe-itemkoppeling](#aal)</li><li>[Brand Portal](#brandportal)</li><li>[Experience Manager-bureaubladtoepassing](#desktopapp)</li><li>[Adobe Stock-afbeeldingen](#adobestock)</li><li>[Dynamische media-elementen](#dynamicmedia)</li></ul> |  |  |
| [Elementkiezer](#assetpicker) |  |  |
| [](#limitations) Beperkingen en  [tips](#tips) |  |  |
| [Afbeeldingsvoorbeelden](#samples) |  |  |

Zoek elementen met behulp van het veld Onderzoek boven aan de webinterface. [!DNL Experience Manager] Ga naar **[!UICONTROL Assets]** > **[!UICONTROL Files]** in [!DNL Experience Manager], klik ![search_icon](assets/do-not-localize/search_icon.png) in hoogste bar, ga onderzoekssleutelwoord in, en druk terugkeer. U kunt ook de trefwoordsneltoets `/` (slash) gebruiken om het veld Onderzoek te openen. `Location:Assets` is vooraf geselecteerd om de zoekopdrachten te beperken tot DAM-middelen. [!DNL Experience Manager] biedt suggesties als u begint met het typen van een trefwoord voor zoeken.

Gebruik het **[!UICONTROL Filters]** paneel om naar activa, omslagen, markeringen, en meta-gegevens te zoeken. U kunt zoekresultaten filteren op basis van de verschillende opties (voorspelling), zoals bestandstype, bestandsgrootte, datum van laatste wijziging, status van element, gegevens over inzichten en Adobe Stock-licenties. U kunt het deelvenster Filters aanpassen en zoekvoorvertoningen toevoegen of verwijderen met behulp van [zoekfacetten](/help/assets/search-facets.md). Het filter [!UICONTROL File Type] in het [!UICONTROL Filters] paneel heeft gemengde-staat checkboxes. Tenzij u alle geneste voorspellen (of indelingen) selecteert, worden de selectievakjes op het eerste niveau daarom gedeeltelijk gecontroleerd.

[!DNL Experience Manager] zoekmogelijkheden bieden ondersteuning voor het zoeken naar verzamelingen en het zoeken naar elementen in een verzameling. Zie [zoekverzamelingen](/help/assets/manage-collections.md).

## Zoekinterface {#searchui} begrijpen

Verken uzelf met de zoekinterface en de beschikbare acties.

![De zoekresultateninterface voor Experience Manager Assets begrijpen](assets/aem_search_results.png)

*Afbeelding: Begrijp de interface van  [!DNL Experience Manager Assets] onderzoeksresultaten.*

**A.** Sla zoekopdracht op als een slimme verzameling. **B.** Filters of voorspelt om de onderzoeksresultaten te beperken. **C.** Bestanden, mappen of beide weergeven. **D.** Klik op Filters om het linkerspoor te openen of te sluiten. **E.** Zoeklocatie is DAM. **F.** Het onderzoeksgebied met user-provided onderzoekssleutelwoord. **G.** Selecteer de geladen zoekresultaten. **H.** Aantal weergegeven zoekresultaten van de totale zoekresultaten. **I.** Dichte zoekopdracht. **J.** Schakel tussen de kaartweergave en de lijstweergave.

### Dynamische zoekfacetten {#dynamicfacets}

U kunt de gewenste elementen sneller vinden op de pagina met zoekresultaten met behulp van het dynamisch bijgewerkte aantal verwachte zoekresultaten in de zoekfacetten. Het verwachte aantal elementen wordt bijgewerkt, zelfs voordat het zoekfilter wordt toegepast. Door het verwachte aantal op het filter te zien, kunt u snel en efficiënt door de zoekresultaten navigeren.

![Zie het geschatte aantal elementen zonder de zoekresultaten te filteren in zoekfacetten.](assets/asset_search_results_in_facets_filters.png)

*Afbeelding: Zie het geschatte aantal elementen zonder de zoekresultaten te filteren in zoekfacetten.*

## Zoekresultaten en gedrag {#searchbehavior} begrijpen

### Standaardzoektermen en -resultaten {#searchbasics}

U kunt trefwoordzoekopdrachten uitvoeren vanuit het veld UniverseelZoeken. De trefwoordzoekopdracht is niet hoofdlettergevoelig en bestaat uit een zoekopdracht in volledige tekst (in de veelgebruikte metagegevensvelden). Als meer dan één sleutelwoord wordt gebruikt, `AND` is de standaardexploitant tussen de sleutelwoorden.

De resultaten worden gesorteerd op relevantie, te beginnen met de dichtstbijzijnde overeenkomsten. Voor meerdere trefwoorden zijn relevantere resultaten de elementen die beide termen in de metagegevens bevatten. Trefwoorden die in de metagegevens voorkomen, krijgen een hogere positie dan trefwoorden die in andere metagegevensvelden worden weergegeven. [!DNL Experience Manager] maakt het mogelijk een bepaalde zoekterm een hoger gewicht te geven. Ook, is het mogelijk om [de rang](#searchrank) van een paar gerichte activa voor specifieke onderzoekstermijnen te verhogen.

Om de relevante activa snel te vinden, verstrekt de rijke interface het filtreren, het sorteren, en selectiemechanismen. U kunt resultaten filteren op basis van meerdere criteria en het aantal gezochte elementen voor verschillende filters bekijken. U kunt de zoekopdracht ook opnieuw uitvoeren door de query in het veld Onderzoek te wijzigen. Wanneer u de zoektermen of filters wijzigt, blijven de andere filters van toepassing om de context van de zoekopdracht te behouden.

Wanneer de resultaten veel elementen zijn, [!DNL Experience Manager] toont eerste 100 in de kaartmening en 200 in de lijstmening. Wanneer gebruikers schuiven, worden meer elementen geladen. Dit is om de prestaties te verbeteren. Bekijk een videodemonstratie van het [aantal getoonde activa](https://www.youtube.com/watch?v=LcrGPDLDf4o).

Het kan voorkomen dat de zoekresultaten een aantal onverwachte elementen bevatten. Zie [onverwachte resultaten](#troubleshoot-unexpected-search-results-and-issues) voor meer informatie.

[!DNL Experience Manager] U kunt naar vele dossierformaten zoeken en de onderzoeksfilters kunnen worden aangepast aan uw bedrijfsvereisten. Neem contact op met uw beheerder om te weten welke zoekopties beschikbaar worden gesteld voor uw DAM-opslagplaats en welke beperkingen uw account heeft.

### Resultaten met en zonder verbeterde slimme tags {#withsmarttags}

Standaard combineert de zoekopdracht [!DNL Experience Manager] de zoektermen met een AND-component. Kijk bijvoorbeeld eens naar het doorzoeken van trefwoordenvrouwen. In de zoekresultaten worden standaard alleen de elementen weergegeven met trefwoorden voor vrouwen en het gebruik van trefwoorden in de metagegevens. Hetzelfde gedrag blijft behouden wanneer speciale tekens (punten, onderstrepingstekens of streepjes) bij de trefwoorden worden gebruikt. De volgende zoekopdrachten retourneren dezelfde resultaten:

* `woman running`
* `woman.running`
* `woman-running`

De query `woman -running` retourneert echter elementen zonder `running` in de metagegevens.
Als u slimme tags gebruikt, wordt een extra `OR`-component toegevoegd om een zoekterm te zoeken als de toegepaste slimme tags. Een element dat is getagd met `woman` of `running` en dat slimme tags gebruikt, wordt ook weergegeven in een dergelijke zoekopdracht. De zoekresultaten zijn dus een combinatie van:

* Elementen met `woman` en `running` trefwoorden in de metagegevens (standaardgedrag).

* Elementen die zijn getagd met een van de trefwoorden (gedrag voor slimme tags).

### Suggesties zoeken terwijl u {#searchsuggestions} typt

Als u trefwoorden begint te typen, stelt [!DNL Experience Manager] de mogelijke zoektrefwoorden of -woordgroepen voor. De suggesties zijn gebaseerd op de metagegevens van de bestaande elementen. [!DNL Experience Manager] Hiermee worden alle metagegevensvelden geïndexeerd, zodat u deze gemakkelijker kunt gebruiken bij het zoeken. Voor zoeksuggesties gebruikt het systeem de waarden van de volgende paar metagegevensvelden. Als u zoeksuggesties wilt doen, kunt u de volgende velden vullen met de juiste trefwoorden:

* Elementlabels. (afbeeldingen tot `jcr:content/metadata/cq:tags`)
* Titel van element. (afbeeldingen tot `jcr:content/metadata/dc:title`)
* Beschrijving van element. (afbeeldingen tot `jcr:content/metadata/dc:description`)
* Titel in de gegevensopslagruimte van het JCR. De waarde wordt mogelijk toegewezen aan de titel van het element. (afbeeldingen tot `jcr:content/jcr:title`)
* Beschrijving in de gegevensopslagruimte van de JCR. De waarde wordt mogelijk toegewezen aan de beschrijving van het element. (afbeeldingen tot `jcr:content/jcr:description`)

Als u suggesties voor meerdere zoektrefwoorden wilt ontvangen, blijft u alle trefwoorden typen zonder een suggestie voor één trefwoord te selecteren.

![Typ meerdere trefwoorden om suggesties weer te geven die in alle trefwoorden passen](assets/search_suggestionsmanykeywords.gif)

*Afbeelding: Typ meerdere trefwoorden om suggesties weer te geven die in alle trefwoorden passen.*

### {#searchrank} zoeken in volgorde en opfrissen

De zoekresultaten die overeenkomen met alle zoektermen in metagegevensvelden worden eerst weergegeven, gevolgd door de zoekresultaten die overeenkomen met een van de zoektermen in de slimme tags. In het bovenstaande voorbeeld is de weergavevolgorde van zoekresultaten bij benadering:

1. Komt overeen met `woman running` in de verschillende metagegevensvelden.
1. Komt overeen met `woman running` in slimme tags.
1. Komt overeen met `woman` of `running` in slimme tags.

U kunt de relevantie van trefwoorden voor bepaalde elementen verbeteren om zoekopdrachten op basis van trefwoorden te stimuleren. Met andere woorden, de afbeeldingen waarvoor u specifieke trefwoorden promoot, worden boven aan de zoekresultaten weergegeven wanneer u op basis van deze trefwoorden zoekt.

1. Open in de gebruikersinterface [!DNL Assets] de eigenschappenpagina voor het element. Klik **[!UICONTROL Advanced]** en klik **[!UICONTROL Add]** onder **[!UICONTROL Elevate for search keywords]**.
1. Geef in het tekstvak **[!UICONTROL Search Promote]** een trefwoord op waarvoor u de zoekopdracht naar de afbeelding wilt opvoeren en klik vervolgens op **[!UICONTROL Add]**. U kunt meerdere trefwoorden op dezelfde manier opgeven.
1. Klik op **[!UICONTROL Save & Close]**. Het element dat u voor dit trefwoord hebt gepromoot, wordt weergegeven in de beste zoekresultaten.

U kunt dit in uw voordeel gebruiken door de positie van bepaalde elementen in de zoekresultaten voor het doeltrefwoord te verhogen. Zie de onderstaande voorbeeldvideo. Voor gedetailleerde informatie, zie [onderzoek in [!DNL Experience Manager]](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/search-and-discovery/search-boost.html).

>[!VIDEO](https://video.tv.adobe.com/v/16766/?quality=6)

*Video: Begrijp hoe de onderzoeksresultaten worden gerangschikt en hoe de rang kan worden beïnvloed.*

## Geavanceerd zoeken {#scope}

[!DNL Experience Manager] biedt verschillende methoden, zoals filters die van toepassing zijn op de gezochte elementen, zodat u de gewenste elementen sneller kunt vinden. Hieronder worden enkele veelgebruikte methoden beschreven. Enkele [geïllustreerde voorbeelden](#samples) worden hieronder gedeeld.

**Bestanden of mappen** zoeken: Zie bestanden, mappen of beide in de zoekresultaten. In het deelvenster **[!UICONTROL Filters]** kunt u de juiste optie selecteren. Zie [zoekinterface](#searchui).

**Zoeken naar elementen in een map**: U kunt de zoekopdracht beperken tot een specifieke map. Voeg in het deelvenster **[!UICONTROL Filters]** het pad van een map toe. U kunt slechts één map tegelijk selecteren.

![Zoekresultaten beperken tot een map door een mappad toe te voegen in het deelvenster Filters](assets/search_folder_select.gif)

*Afbeelding: Beperk de zoekresultaten tot een map door een mappad toe te voegen in het deelvenster Filters.*

### Vergelijkbare afbeeldingen zoeken {#visualsearch}

Als u afbeeldingen wilt zoeken die visueel lijken op een door de gebruiker geselecteerde afbeelding, klikt u op de optie **[!UICONTROL Find Similar]** in de kaartweergave van een afbeelding of op de werkbalk. [!DNL Experience Manager] geeft de slimme getagde afbeeldingen uit de DAM-opslagplaats weer die lijken op een door de gebruiker geselecteerde afbeelding. Zie [Zoeken naar overeenkomsten configureren](#configvisualsearch).

![Vergelijkbare afbeeldingen zoeken met de optie in de kaartweergave](assets/search_find_similar.png)

*Afbeelding: U kunt vergelijkbare afbeeldingen zoeken met de optie in de kaartweergave.*

### Adobe Stock-afbeeldingen {#adobestock}

Vanuit de [!DNL Experience Manager]-gebruikersinterface kunnen gebruikers [Adobe Stock-middelen](/help/assets/aem-assets-adobe-stock.md) doorzoeken en een licentie voor de vereiste middelen aanschaffen. Voeg `Location: Adobe Stock` in de bar van het Onderzoek toe. U kunt ook het deelvenster Filters gebruiken om alle middelen te zoeken waarvoor een licentie is verleend of om een bepaald element te zoeken aan de hand van het Adobe Stock-bestandsnummer.

### Dynamische media-elementen {#dmassets}

U kunt filteren op dynamische media-afbeeldingen door **[!UICONTROL Dynamic Media]** > **[!UICONTROL Sets]** te selecteren in het deelvenster **[!UICONTROL Filters]**. Het filtert op en toont assets zoals afbeeldingsets, carrousels, gemengde mediasets, en spinsets.

### Zoeken met specifieke waarden in metagegevensvelden {#gqlsearch}

U kunt naar elementen zoeken op basis van exacte waarden van specifieke metagegevensvelden, zoals titel, beschrijving en auteur. Met de zoekfunctie voor volledige tekst GQL haalt u alleen die elementen op waarvan de metagegevenswaarde exact overeenkomt met uw zoekopdracht. De namen van de eigenschappen (bijvoorbeeld auteur, titel, enzovoort) en de waarden zijn hoofdlettergevoelig.

| Metagegevensveld | Facetwaarde en gebruik |
| ----------------------------------------- | ------------------------------------- |
| Titel | titel:John |
| Creator | maker:John |
| Locatie | locatie:NA |
| Beschrijving | beschrijving:&quot;Voorbeeldafbeelding&quot; |
| Gereedschap Maker | creatortool:&quot;Adobe Photoshop CC 2020&quot; |
| Copyrighteigenaar | copyrightowner:&quot;Adobe Systems&quot; |
| Medewerker | contribuant:John |
| Gebruiksvoorwaarden | usageterms:&quot;CopyRights Reserved&quot; |
| Gemaakt | gemaakt:YYYY-MM-DDTHH |
| Vervaldatum | verloopt:YYYY-MM-DDTHH |
| Op tijd | ontime:YYYY-MM-DDTHH |
| Uit-tijd | offtime:YYYY-MM-DDTHH |
| Tijdsbereik (verloopt dateontime, offtime) | Veld facet: lager gebonden..bovenaan |
| Pad | /content/dam/&lt;naam map> |
| PDF-titel | pdftitle:&quot;Adobe-document&quot; |
| Subject | onderwerp: &quot;Opleiding&quot; |
| Tags | tags:&quot;Locatie en reizen&quot; |
| Type | type:&quot;image\png&quot; |
| Breedte van afbeelding | breedte:ondergrens..bovenaan |
| Hoogte van afbeelding | hoogte:ondergrens..bovenaan |
| Person | persoon:John |

De eigenschappen `path`, `limit`, `size` en `orderby` kunnen niet worden gecombineerd met een `OR` operator met een andere eigenschap.

Het sleutelwoord voor een user-generated bezit is zijn gebiedsetiket in de bezitsredacteur in kleine letters, met verwijderde ruimten.

Hier volgen enkele voorbeelden van zoekindelingen voor complexe query&#39;s:

* Alle elementen weergeven met meerdere facetvelden (bijvoorbeeld: title=Jan Smit en creator tool = Adobe Photoshop): `title:"John Doe" creatortool:Adobe*`
* Om alle activa te tonen wanneer de facetwaarde niet één enkel woord maar één zin is (bijvoorbeeld: title=Scott Reynolds): `title:"Scott Reynolds"`
* Elementen weergeven met meerdere waarden van één eigenschap (bijvoorbeeld: title=Scott Reynolds of Jan Smit): `title:"Scott Reynolds" OR "John Doe"`
* Elementen weergeven met eigenschapswaarden die beginnen met een specifieke tekenreeks (bijvoorbeeld: de titel is Scott Reynolds): `title:Scott*`
* Elementen weergeven met eigenschapswaarden die eindigen met een specifieke tekenreeks (bijvoorbeeld: de titel is Scott Reynolds): `title:*Reynolds`
* Elementen weergeven met een eigenschapswaarde die een specifieke tekenreeks bevat (bijvoorbeeld: titel = Bazel-vergaderruimte): `title:*Meeting*`
* Elementen weergeven die een bepaalde tekenreeks bevatten en een specifieke eigenschapswaarde hebben (bijvoorbeeld: zoek naar string Adobe in assets met title=Jan Smit): `*Adobe* title:"John Doe"`

## Elementen zoeken vanuit andere [!DNL Experience Manager]-aanbiedingen of interfaces {#beyondomnisearch}

[!DNL Adobe Experience Manager] Maakt de DAM-opslagplaats aan verschillende andere  [!DNL Experience Manager] oplossingen aan om snellere toegang tot digitale middelen te bieden en de creatieve workflows te stroomlijnen. Elke detectie van middelen begint met bladeren of zoeken. Het zoekgedrag blijft grotendeels hetzelfde op de verschillende oppervlakken en oplossingen. Sommige onderzoeksmethodes veranderen aangezien het doelpubliek, de gebruiksgevallen, en de gebruikersinterface over de [!DNL Experience Manager] oplossingen variëren. De specifieke methoden worden gedocumenteerd voor de afzonderlijke oplossingen in de onderstaande koppelingen. De algemeen toepasselijke tips en gedragingen worden in dit artikel beschreven.

### Elementen zoeken in het deelvenster Koppeling van Adobe-element {#aal}

Met Adobe Asset Link kunnen creatieve professionals nu toegang krijgen tot inhoud die is opgeslagen in [!DNL Experience Manager Assets], zonder de ondersteunde Adobe Creative Cloud-apps te verlaten. Creatieve personen kunnen naadloos door middelen bladeren, zoeken, uitchecken en inchecken met het deelvenster in de app in [!DNL Adobe Creative Cloud apps]: [!DNL Adobe Photoshop], [!DNL Adobe Illustrator] en [!DNL Adobe InDesign]. Met Asset Link kunnen gebruikers ook visueel vergelijkbare resultaten zoeken. De resultaten van de visuele zoekopdrachten worden aangedreven door instructiealgoritmen van Adobe Sensei-computers en helpen gebruikers bij het zoeken naar beelden die er in esthetisch opzicht op lijken. Zie [Elementen zoeken en doorbladeren](https://helpx.adobe.com/enterprise/using/manage-assets-using-adobe-asset-link.html#UseAdobeAssetLink) met behulp van Adobe Asset Link.

### Middelen zoeken in [!DNL Experience Manager] desktop app {#desktopapp}

Creatieve professionals gebruiken de desktop-app om de [!DNL Experience Manager Assets] gemakkelijk doorzoekbaar en beschikbaar te maken op hun lokale bureaublad (Windows of Mac). Creative Cloud kan de gewenste middelen eenvoudig weergeven in Mac Finder of Windows Verkenner, geopend in bureaubladtoepassingen en lokaal gewijzigd. De wijzigingen worden weer opgeslagen in [!DNL Experience Manager] met een nieuwe versie die in de opslagplaats is gemaakt. De toepassing ondersteunt basiszoekopdrachten met een of meer trefwoorden, `*`- en `?`-jokertekens en `AND`-operator. Zie [Elementen doorbladeren, zoeken en voorvertonen](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#browse-search-preview-assets) in desktop app.

### Middelen zoeken in [!DNL Brand Portal] {#brandportal}

De gebruikers van de lijn-van-zaken en de marketers gebruiken het Portaal van het Merk om de goedgekeurde digitale activa met hun uitgebreide interne teams, partners, en resellers efficiënt en veilig te delen. Zie [zoekmiddelen op Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/search-capabilities/brand-portal-searching.html).

### [!DNL Adobe Stock] afbeeldingen doorzoeken {#adobestock-1}

Vanuit de [!DNL Experience Manager]-gebruikersinterface kunnen gebruikers zoeken in Adobe Stock-middelen en een licentie voor de vereiste middelen aanschaffen. Voeg `Location: Adobe Stock` op het gebied van Onderzoek toe. U kunt ook **[!UICONTROL Filters]** gebruiken om alle gelicentieerde of niet gelicentieerde activa te vinden of een specifiek middel te zoeken gebruikend het dossieraantal van Adobe Stock. Zie [Adobe Stock-afbeeldingen beheren in Experience Manager](/help/assets/aem-assets-adobe-stock.md#usemanage).

### Dynamische media-elementen zoeken {#dynamicmedia}

U kunt filteren op dynamische media-afbeeldingen door **[!UICONTROL Dynamic Media]** > **[!UICONTROL Sets]** te selecteren in het deelvenster **[!UICONTROL Filters]**. Het filtert op en toont assets zoals afbeeldingsets, carrousels, gemengde mediasets, en spinsets. Tijdens het ontwerpen van webpagina&#39;s kunnen auteurs naar sets zoeken in de Inhoudszoeker. Een filter voor sets is beschikbaar in een pop-upmenu.

### Elementen zoeken in de Inhoudszoeker bij het ontwerpen van webpagina&#39;s {#contentfinder}

Auteurs kunnen de Inhoudszoeker gebruiken om in de DAM-opslagplaats te zoeken naar de relevante elementen en de elementen te gebruiken op de webpagina&#39;s die ze maken. Auteurs kunnen ook de functie Verbonden elementen gebruiken om te zoeken naar elementen die beschikbaar zijn op een externe [!DNL Experience Manager]-implementatie. Auteurs kunnen deze elementen vervolgens gebruiken in webpagina&#39;s op een lokale [!DNL Experience Manager]-implementatie. Zie [externe elementen gebruiken](/help/assets/use-assets-across-connected-assets-instances.md#use-remote-assets).

### Verzamelingen zoeken {#collections}

[!DNL Experience Manager] zoekmogelijkheden bieden ondersteuning voor het zoeken naar verzamelingen en het zoeken naar elementen in een verzameling. Zie [zoekverzamelingen](/help/assets/manage-collections.md).

## Elementkiezer {#assetpicker}

>[!NOTE]
>
>Asset selector werd [asset picker](https://helpx.adobe.com/experience-manager/6-2/assets/using/asset-picker.html) in eerdere versies van [!DNL Adobe Experience Manager] genoemd.

Met de functie Asset Selector kunt u op een speciale manier door DAM-middelen bladeren, zoeken en filteren. U kunt de elementenkiezer in uw [!DNL Experience Manager]-instantie starten met `https://[aem-server]:[port]/aem/assetpicker.html`. Deze URL opent de elementenkiezer in de bladermodus. Gebruik de ondersteunde aanvraagparameters als achtervoegsel, zoals `mode` (enkele of meerdere selecties) of `viewmode` met `assettype` (afbeelding, video, tekst) en `mimetype`. Deze parameters stellen de context van de elementenkiezer voor een bepaalde zoekinstantie in en blijven tijdens de selectie intact. U kunt ook de metagegevens ophalen van elementen die u selecteert met deze functie.

De elementkiezer gebruikt het HTML5 `Window.postMessage`-bericht om gegevens voor het geselecteerde element naar de ontvanger te verzenden. Deze functie werkt alleen in de modus Bladeren en alleen met de resultatenpagina van Omnsearch.

Geef de volgende aanvraagparameters in een URL door om de elementenkiezer in een bepaalde context te starten:

| Naam | Waarden | Voorbeeld | Doel |
|---|---|---|---|
| bronachtervoegsel (B) | Het pad van de map als het bronachtervoegsel in de URL:[https://localhost:4502/aem/assetpicker.html/&lt;folder_path>](https://localhost:4502/aem/assetpicker.html) | Als u de elementenkiezer wilt starten terwijl een bepaalde map is geselecteerd, bijvoorbeeld met de map `/content/dam/we-retail/en/activities` geselecteerd, moet de URL de volgende vorm hebben: [https://localhost:4502/aem/assetpicker.html/content/dam/we-retail/en/activities?assettype=images](https://localhost:4502/aem/assetpicker.html/content/dam/we-retail/en/activities?assettype=images) | Als u wilt dat een bepaalde map wordt geselecteerd wanneer de elementenkiezer wordt gestart, geeft u deze door als een bronachtervoegsel. |
| mode | enkelvoudig, meerdere | <ul><li>[https://localhost:4502/aem/assetpicker.html?mode=single](https://localhost:4502/aem/assetpicker.html?mode=single)</li><li>[https://localhost:4502/aem/assetpicker.html?mode=multiple](https://localhost:4502/aem/assetpicker.html?mode=multiple)</li></ul> | In meerdere modi kunt u meerdere elementen tegelijk selecteren met de elementkiezer. |
| dialoogvenster | true, false | [https://localhost:4502/aem/assetpicker.html?dialog=true](https://localhost:4502/aem/assetpicker.html?dialog=true) | Gebruik deze parameters om de elementenkiezer te openen als granietdialoogvenster. Deze optie is alleen van toepassing wanneer u de elementenkiezer start via Granite Path Field en deze configureert als pickerSrc URL. |
| basis | &lt;folder_path> | [https://localhost:4502/aem/assetpicker.html?assettype=images&amp;root=/content/dam/we-retail/en/activities](https://localhost:4502/aem/assetpicker.html?assettype=images&amp;root=/content/dam/we-retail/en/activities) | Gebruik deze optie om de hoofdmap voor de elementenkiezer op te geven. In dit geval kunt u met de elementenkiezer alleen onderliggende elementen (direct/indirect) in de hoofdmap selecteren. |
| viewmode | zoeken |  | De elementenkiezer starten in de zoekmodus met parameters assettype en mimetype. |
| assettype | afbeeldingen, documenten, multimedia, archieven | <ul><li>[https://localhost:4502/aem/assetpicker.html?viewmode=search&amp;assettype=images](https://localhost:4502/aem/assetpicker.html?viewmode=search&amp;assettype=images)</li><li>[https://localhost:4502/aem/assetpicker.html?viewmode=search&amp;assettype=documents](https://localhost:4502/aem/assetpicker.html?assettype=documents)</li><li>[https://localhost:4502/aem/assetpicker.html?viewmode=search&amp;assettype=multimedia](https://localhost:4502/aem/assetpicker.html?viewmode=search&amp;assettype=multimedia)</li><li>[https://localhost:4502/aem/assetpicker.html?viewmode=search&amp;assettype=archives](https://localhost:4502/aem/assetpicker.html?viewmode=search&amp;assettype=archives)</li></ul> | Gebruik deze optie om elementtypen te filteren op basis van de doorgegeven waarde. |
| mimetype | mimetype(s) (`/jcr:content/metadata/dc:format`) van een element (jokerteken wordt ook ondersteund) | <ul><li>[https://localhost:4502/aem/assetpicker.html?viewmode=search&amp;mimetype=image/png](https://localhost:4502/aem/assetpicker.html?viewmode=search&amp;mimetype=image/png)</li><li>[https://localhost:4502/aem/assetpicker.html?viewmode=search&amp;mimetype=*png](https://localhost:4502/aem/assetpicker.html?viewmode=search&amp;mimetype=*png)</li><li>[https://localhost:4502/aem/assetpicker.html?viewmode=search&amp;mimetype=*presentation](https://localhost:4502/aem/assetpicker.html?viewmode=search&amp;mimetype=*presentation)</li><li>[https://localhost:4502/aem/assetpicker.html?viewmode=search&amp;mimetype=*presentation&amp;mimetype=*png](https://localhost:4502/aem/assetpicker.html?viewmode=search&amp;mimetype=*presentation&amp;mimetype=*png)</li></ul> | Hiermee kunt u elementen filteren op basis van MIME-typen |

Ga naar `https://[aem_server]:[port]/aem/assetpicker` om de interface van de elementenkiezer te openen. Navigeer naar de gewenste map en selecteer een of meer elementen. U kunt ook naar het gewenste element zoeken in het vak Zoeken, naar wens een filter toepassen en het vervolgens selecteren.

![Door element bladeren en dit selecteren in de elementenkiezer](assets/assetpicker.png)

*Afbeelding: Blader door elementen en selecteer deze in de elementenkiezer.*

## Beperkingen {#limitations}

De zoekfunctie in [!DNL Experience Manager Assets] heeft de volgende beperkingen:

* Geef geen regelafstand op in de zoekopdracht als de zoekopdracht anders niet werkt.
* [!DNL Experience Manager] Mogelijk blijft de zoekterm zichtbaar nadat u eigenschappen van een element hebt geselecteerd in de gezochte resultaten en vervolgens de zoekopdracht hebt geannuleerd.  <!-- (CQ-4273540) -->
* Wanneer u naar mappen of bestanden en mappen zoekt, kunnen de zoekresultaten op geen enkele parameter worden gesorteerd.
* Als u op Return drukt zonder op de zoekbalk te typen, geeft [!DNL Experience Manager] alleen een lijst met bestanden en niet met mappen. Als u specifiek naar omslagen zonder een sleutelwoord zoekt, [!DNL Experience Manager] keert geen resultaten terug.

Het visuele onderzoek of het gelijkenis onderzoek heeft de volgende beperkingen:

* Visueel onderzoek werkt het best met grotere bewaarplaatsen. Hoewel er geen minimaal aantal afbeeldingen vereist is voor goede resultaten, is de kwaliteit van overeenkomsten met een paar afbeeldingen mogelijk minder goed dan de overeenkomsten met een grote opslagplaats.
* U kunt het model niet wijzigen of [!DNL Experience Manager] trainen om vergelijkbare afbeeldingen te zoeken. Als u bijvoorbeeld slimme tags toevoegt of verwijdert aan een paar elementen, verandert het model niet. De elementen worden wel uitgesloten van de visueel vergelijkbare zoekresultaten.

De zoekfunctionaliteit kan prestatiebeperkingen hebben in de volgende scenario&#39;s:

* De kaartweergave heeft een snellere laadtijd dan de lijstweergave om de zoekresultaten weer te geven.

## Zoektips {#tips}

* Gebruik bij het controleren van de revisiestatus van de middelen de juiste optie om te bepalen welke middelen zijn goedgekeurd of welke activa nog moeten worden goedgekeurd.
* Gebruik de Insights-voorspelling om te zoeken naar ondersteunde middelen op basis van de gebruiksstatistieken die zijn verkregen van verschillende Creative-apps. Gebruiksgegevens worden gegroepeerd onder Gebruiksscore, Impressies, Klikken en Mediakanalen waar de elementen categorieën weergeven.
* Schakel het selectievakje **[!UICONTROL Select All]** in om de gezochte elementen te selecteren. [!DNL Experience Manager] In eerste instantie worden 100 elementen weergegeven in de kaartweergave en 200 elementen in de lijstweergave. Er worden meer elementen geladen wanneer u door de zoekresultaten schuift. U kunt meer elementen selecteren dan de geladen elementen. Het aantal geselecteerde elementen wordt in de rechterbovenhoek van de pagina met zoekresultaten weergegeven. U kunt de selectie bijvoorbeeld activeren door de geselecteerde elementen te downloaden, de eigenschappen van metagegevens voor de geselecteerde elementen bulksgewijs bij te werken of de geselecteerde elementen aan een verzameling toe te voegen. Wanneer er meer elementen zijn geselecteerd dan worden weergegeven, wordt een actie toegepast op alle geselecteerde elementen of wordt in een dialoogvenster het aantal elementen weergegeven waarop de actie wordt toegepast. Als u een handeling wilt toepassen op de elementen die niet zijn geladen, moet u ervoor zorgen dat alle elementen expliciet zijn geselecteerd.
* Zie [verplichte metagegevens](#mandatorymetadata) als u wilt zoeken naar elementen die de verplichte metagegevens niet bevatten.
* Zoeken gebruikt alle metagegevensvelden. Een generieke zoekopdracht, zoals zoeken naar 12, retourneert doorgaans veel resultaten. Voor betere resultaten gebruikt u dubbele (geen enkele) aanhalingstekens of zorgt u ervoor dat het getal aangrenzend is aan een woord zonder speciaal teken (bijvoorbeeld `shoe12`).
* Het zoeken in volledige tekst ondersteunt operatoren zoals `-` en `^`. Als u deze letters wilt doorzoeken als letterlijke tekenreeksen, plaatst u de zoekexpressie tussen dubbele aanhalingstekens. Gebruik bijvoorbeeld `"Notebook - Beauty"` in plaats van `Notebook - Beauty`.
* Als de zoekresultaten te veel zijn, beperkt u het [bereik van zoeken](#scope) tot nul-in op de gewenste elementen. Het werkt het beste als u een idee hebt van hoe u beter kunt zoeken naar de gewenste elementen, bijvoorbeeld een specifiek bestandstype, een specifieke locatie, specifieke metagegevens, enzovoort.

* **Tags**: Met tags kunt u elementen categoriseren waarin u efficiënter kunt bladeren en zoeken. Tags helpen andere gebruikers en workflows de juiste taxonomie te geven. [!DNL Experience Manager] biedt methoden om elementen automatisch te labelen met behulp van kunstmatig intelligente services van Adobe Sensei die uw elementen steeds beter kunnen coderen met gebruik en training. Wanneer u naar elementen zoekt, wordt met de slimme tags rekening gehouden als de functie op uw account is ingeschakeld. Het werkt naast de ingebouwde zoekfunctionaliteit. Zie [zoekgedrag](#searchbehavior). Om de orde te optimaliseren waarin de onderzoeksresultaten worden getoond, kunt u [het onderzoek rangschikken](#searchrank) van een paar uitgezochte activa opvoeren.

* **Indexeren**: Alleen geïndexeerde metagegevens en elementen worden geretourneerd in de zoekresultaten. Voor betere dekking en betere prestaties, zorg behoorlijk indexeren en volg de beste praktijken. Zie [indexeren](#searchindex).

* Om specifieke activa van onderzoeksresultaten uit te sluiten, gebruik `excludedPath` bezit in de index van Lucene.

## Enkele voorbeelden ter illustratie van zoekopdracht {#samples}

Gebruik dubbele aanhalingstekens rond trefwoorden om te zoeken naar elementen die de exacte woordgroep bevatten in de exacte volgorde die de gebruiker heeft opgegeven.

![Gedrag zoeken met en zonder aanhalingstekens](assets/search_with_quotes.gif)

*Afbeelding: Gedrag zoeken met en zonder aanhalingstekens.*

**Zoeken met jokerteken** sterretje: Als u de zoekopdracht wilt uitbreiden, gebruikt u een sterretje voor of na het zoekwoord om het gewenste aantal tekens te zoeken. Als u bijvoorbeeld zoekt naar tekst zonder sterretje, worden er geen elementen geretourneerd die een variatie van het woord bevatten (inclusief in de metagegevens). Een sterretje vervangt het gehele aantal tekens. Bijvoorbeeld,

* `run` retourneert elementen met trefwoord exact uitvoeren
* `run*` retourneert elementen met actieve, actieve, weglopende enzovoort.
* `*run` retourneert outrun, reerun enzovoort.
* `*run*` retourneert alle mogelijke combinaties.

![Het gebruik van jokertekens voor sterretjes in het zoeken naar elementen illustreren aan de hand van een voorbeeld](assets/search_with_asterisk_run.gif)

*Afbeelding: Het illustreren van het gebruik van asteriskvervanging in het onderzoek van Activa gebruikend een voorbeeld.*

**Zoeken met jokerteken voor** vraagtekens: Als u de zoekopdracht wilt uitbreiden, gebruikt u een of meer &#39;?&#39; tekens die exact overeenkomen met het aantal tekens. In de volgende afbeelding, bijvoorbeeld:

* `run???` query komt niet overeen met enig element.

* `run????` De vraag past het woord  `running` met vier karakters na aan  `run`.

* `??run` De vraag past het woord  `rerun` met twee karakters vóór  `run`.

![Het gebruik van jokertekens in de zoekfunctie voor elementen illustreren aan de hand van een voorbeeld](assets/search_with_questionmark_run.gif)

*Afbeelding: Het illustreren van het gebruik van vraagtekenvervanging in de onderzoek van Activa gebruikend een voorbeeld.*

**Een trefwoord** uitsluiten: Gebruik een streepje om te zoeken naar elementen die geen trefwoord bevatten. Met de query `running -shoe` worden bijvoorbeeld elementen geretourneerd die `running` bevatten, maar niet `shoe`. Op dezelfde manier `camp -night` de vraag keert activa terug die `camp` maar niet `night` bevatten. De query `camp-night` retourneert elementen die zowel `camp` als `night` bevatten.

![Gebruik van streepje om te zoeken naar elementen die geen uitgesloten trefwoord bevatten](assets/search_dash_exclude_keyword.gif)

*Afbeelding: Gebruik van streepje om te zoeken naar elementen die geen uitgesloten trefwoord bevatten.*

## Configuratie- en beheerstaken met betrekking tot zoekfunctionaliteit {#configadmin}

### Zoekindexconfiguraties {#searchindex}

Asset Discovery is afhankelijk van indexering van de DAM-inhoud, inclusief de metagegevens. Snellere en nauwkeurige detectie van bedrijfsmiddelen is afhankelijk van geoptimaliseerde indexering en geschikte configuraties. Zie [zoekindex](/help/assets/performance-tuning-guidelines.md#search-indexes), [oak-query&#39;s en indexering](/help/sites-deploying/queries-and-indexing.md), en [best practices](/help/sites-deploying/best-practices-for-queries-and-indexing.md).

Om specifieke activa van onderzoeksresultaten uit te sluiten, gebruik `excludedPath` bezit in de index van Lucene.

### Zoeken op visuele of gelijkenis {#configvisualsearch}

Bij visueel zoeken wordt slimme tags gebruikt en is [!DNL Experience Manager] 6.5.2.0 of hoger vereist. Voer de volgende stappen uit nadat u de functionaliteit voor slimme tags hebt geconfigureerd:

1. In [!DNL Experience Manager] CRXDE, in `/oak:index/lucene` knoop, voeg de volgende eigenschappen en de waarden toe en sparen de veranderingen.

   * `costPerEntry` eigenschap van het type  `Double` met de waarde  `10`.
   * `costPerExecution` eigenschap van het type  `Double` met de waarde  `2`.
   * `refresh` eigenschap van het type  `Boolean` met de waarde  `true`.

   Deze configuratie staat onderzoeken van de aangewezen index toe.

1. Om een index van Luceen, in CRXDE, bij `/oak:index/damAssetLucene/indexRules/dam:Asset/properties` tot stand te brengen, creeer knoop genoemd `imageFeatures` van type `nt-unstructured`. In `imageFeatures` node,

   * Voeg `name` bezit van type `String` met de waarde `jcr:content/metadata/imageFeatures/haystack0` toe.
   * Voeg `nodeScopeIndex` bezit van type `Boolean` met de waarde van `true` toe.
   * Voeg `propertyIndex` bezit van type `Boolean` met de waarde van `true` toe.
   * Voeg `useInSimilarity` bezit van type `Boolean` met de waarde `true` toe.

   Sla de wijzigingen op.

1. Open `/oak:index/damAssetLucene/indexRules/dam:Asset/properties/predictedTags` en voeg `similarityTags` bezit van type `Boolean` met de waarde van `true` toe.
1. Pas slimme tags toe op de elementen in uw [!DNL Experience Manager]-opslagplaats.
1. In CRXDE, in `/oak-index/damAssetLucene` knoop, plaats `reindex` bezit aan `true`. Sla de wijzigingen op.
1. (Optioneel) Als u het zoekformulier hebt aangepast, kopieert u het knooppunt `/libs/settings/dam/search/facets/assets/jcr%3Acontent/items/similaritysearch` naar `/conf/global/settings/dam/search/facets/assets/jcr:content/items`. Sla de wijzigingen op.

Voor verwante informatie, zie [slimme markeringen in Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/metadata/image-smart-tags.html) en [hoe te om slimme markeringen te beheren](/help/assets/enhanced-smart-tags.md).

>[!CAUTION]
>
>Als het indexeren van Lucene uit [!DNL Adobe Experience Manager] wordt gedaan, dan werkt het onderzoek dat op slimme markeringen wordt gebaseerd niet zoals verwacht.

### Verplichte metagegevens {#mandatorymetadata}

Zakelijke gebruikers, beheerders of DAM-bibliotheken kunnen bepaalde metagegevens definiëren als verplichte metagegevens die nodig zijn om de bedrijfsprocessen te laten werken. Om verschillende redenen ontbreken deze metagegevens mogelijk bij sommige elementen, zoals oudere elementen of elementen die in bulk zijn gemigreerd. Elementen met ontbrekende of ongeldige metagegevens worden gedetecteerd en gerapporteerd op basis van de eigenschap voor geïndexeerde metagegevens. Zie [verplichte metagegevens](/help/assets/metadata-schemas.md#define-mandatory-metadata) om deze te configureren.

### Zoekfacetten wijzigen {#searchfacets}

[!DNL Experience Manager Assets] biedt zoekfacetten waarmee u de zoekresultaten kunt filteren om de snelheid van detectie te verbeteren. Het deelvenster Filters bevat standaard enkele standaardfacetten. Beheerders kunnen het deelvenster Filters aanpassen om de standaardfacetten te wijzigen met behulp van de ingebouwde voorspelling. [!DNL Experience Manager] verstrekt een goede inzameling van ingebouwde predikaten en een redacteur om de facetten aan te passen. Zie [zoekfacetten](/help/assets/search-facets.md).

### Tekst extraheren tijdens het uploaden van elementen {#extracttextupload}

U kunt [!DNL Experience Manager] zodanig configureren dat de tekst uit de elementen wordt gehaald wanneer gebruikers elementen uploaden, zoals PSD- of PDF-bestanden. [!DNL Experience Manager] indexeert de geëxtraheerde tekst en helpt gebruikers deze elementen te doorzoeken op basis van de geëxtraheerde tekst. Zie [Elementen uploaden](/help/assets/manage-assets.md#uploading-assets).

Als de tekstextractie te resource-intensief wordt voor uw plaatsing, denk [onbruikbaar makend tekstextractie](https://helpx.adobe.com/experience-manager/kb/Disable-binary-text-extraction-to-optimize-Lucene-indexing-AEM.html).

### Aangepaste voorspelling van filterzoekresultaten {#custompredicates}

Voorspellen worden gebruikt om facetten te maken. Beheerders kunnen de zoekfacetten in het deelvenster Filters aanpassen met behulp van vooraf geconfigureerde voorspellingen. Deze voorspelling kan worden aangepast met behulp van overlays. Zie [aangepaste voorspelling maken](/help/assets/searchx.md).

U kunt naar digitale elementen zoeken op basis van een of meer van de volgende eigenschappen. Filters die op sommige van deze eigenschappen van toepassing zijn, zijn standaard beschikbaar en sommige andere filters kunnen op maat worden gemaakt om op de andere eigenschappen toe te passen.

| Zoekveld | Waarden van eigenschappen zoeken |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------|
| MIME-typen | Afbeeldingen, Documenten, Multimedia, Archieven of Overige. |
| Laatst gewijzigd | Uur, Dag, Week, Maand of Jaar. |
| Bestandsgrootte | Klein, Normaal of Groot. |
| Status publiceren | Gepubliceerd of Niet gepubliceerd. |
| Goedgekeurde status | Goedgekeurd of geweigerd. |
| Afdrukstand | Horizontaal, Verticaal of Vierkant. |
| Stijl | Kleur, of Zwart-wit. |
| Videohoogte | Opgegeven als minimum- en maximumwaarde. Waarde wordt alleen opgeslagen in de metagegevens van video-uitvoeringen. |
| Videobreedte | Opgegeven als minimum- en maximumwaarde. Waarde wordt alleen opgeslagen in de metagegevens van video-uitvoeringen. |
| Video-indeling | DVI, Flash, MPEG4, MPEG, OGG Theora, QuickTime, Windows Media. Waarde wordt opgeslagen in de metagegevens van de bronvideo en eventuele uitvoeringen. |
| Videocodec | x264. Waarde wordt alleen opgeslagen in de metagegevens van video-uitvoeringen. |
| Videobitsnelheid | Opgegeven als minimum- en maximumwaarde. Waarde wordt alleen opgeslagen in de metagegevens van video-uitvoeringen. |
| Audiocodec | Libvorbis, Lame MP3, AAC-codering. Waarde wordt alleen opgeslagen in de metagegevens van video-uitvoeringen. |
| Audiobitsnelheid | Opgegeven als minimum- en maximumwaarde. Waarde wordt alleen opgeslagen in de metagegevens van video-uitvoeringen. |

## Werken met zoekresultaten voor elementen {#aftersearch}

U kunt het volgende doen met de activa u in [!DNL Experience Manager] hebt gezocht:

* Eigenschappen van metagegevens en andere informatie weergeven.
* Download een of meer middelen.
* Gebruik Desktophandelingen om deze middelen in de bureaubladtoepassing te openen.
* Slimme verzamelingen maken.

### Zoekresultaten sorteren {#sort}

U kunt zoekresultaten sorteren om sneller de vereiste elementen te vinden. U kunt de onderzoeksresultaten slechts sorteren wanneer u **[[!UICONTROL Files]](#searchui)** van **[!UICONTROL Filters]** paneel selecteert. [!DNL Assets] gebruikt sorteren op de server om snel alle assets (hoe talrijk ook) in een map of de resultaten van een zoekopdracht te sorteren. Sorteren op de server levert sneller en nauwkeuriger resultaten op dan sorteren op de client.

U kunt de zoekresultaten op dezelfde manier sorteren als elementen in een willekeurige map. Sorteren werkt op deze kolommen: Naam, Titel, Status, Dimension, Grootte, Classificatie, Gebruik (Gemaakt op), (Datum) Gewijzigd, (Datum) Gepubliceerd, Workflow en Uitgecheckt.

Voor beperkingen van soortfunctionaliteit, zie [beperkingen](#limitations).

### Gedetailleerde informatie over een element {#checkinfo} controleren

Op de pagina met zoekresultaten kunt u gedetailleerde informatie over een doorzocht element controleren.

Als u alle metagegevens van een element wilt weergeven, selecteert u het element en klikt u op **[!UICONTROL properties]** op de werkbalk.

Als u de opmerkingen over een asset of de versiegeschiedenis van een asset wilt controleren, klikt u op de asset om een voorvertoning op grote grootte te openen. Open de tijdlijn in het linkerspoor en selecteer **[!UICONTROL Comments]** of **[!UICONTROL Versions]**. U kunt de tijdlijnactiviteit zoals opmerkingen of versies ook in chronologische volgorde sorteren.

![Tijdlijnitems voor een zoekmiddel sorteren](assets/sort_timeline_search_results.gif)

*Afbeelding: Sorteer de tijdlijnitems voor een zoekmiddel.*

### Gezochte middelen {#download} downloaden

U kunt de gezochte elementen en hun vertoningen downloaden enkel aangezien u regelmatige activa van omslagen downloadt. Selecteer een of meer elementen in de zoekresultaten en klik op **[!UICONTROL Download]** op de werkbalk.

### Eigenschappen van metagegevens voor bulkupdates {#metadataupdates}

Het is mogelijk om bulkupdates uit te voeren naar de algemene metagegevensvelden van meerdere elementen. Selecteer een of meer elementen in de zoekresultaten. Klik op **[!UICONTROL Properties]** op de werkbalk en werk de metagegevens naar wens bij. Klik **[!UICONTROL Save and Close]** wanneer gereed. De eerder bestaande metagegevens in de bijgewerkte velden worden overschreven.

Voor de activa die in één enkele omslag of een inzameling beschikbaar zijn, is het gemakkelijker om [meta-gegevens in massa ](/help/assets/metadata.md) bij te werken zonder de onderzoeksfunctionaliteit te gebruiken. Voor de elementen die beschikbaar zijn in verschillende mappen of voldoen aan een algemeen criterium, is het sneller om de metagegevens bulksgewijs bij te werken door te zoeken.

### Slimme verzamelingen {#smart-collections}

Een verzameling is een geordende set elementen die elementen van verschillende locaties kunnen bevatten, omdat verzamelingen alleen verwijzingen naar deze elementen bevatten. Verzamelingen zijn van de volgende twee typen:

* Een statische referentielijst met elementen, mappen en andere verzamelingen.
* Een dynamische lijst (slimme verzameling) die elementen in de verzameling vult op basis van zoekcriteria.

U kunt slimme verzamelingen maken op basis van de zoekcriteria. Selecteer in het deelvenster **[!UICONTROL Filters]** de optie **[!UICONTROL Files]** en klik op **[!UICONTROL Save Smart Collection]**. Zie [Verzamelingen beheren](/help/assets/manage-collections.md).

## Onverwachte zoekresultaten en problemen {#unexpectedresults}

| Fout, problemen, symptomen | Mogelijke reden | Mogelijke oplossing of begrip van het probleem |
|---|---|---|
| Onjuiste resultaten bij het zoeken naar elementen met ontbrekende metagegevens. | Bij het zoeken naar elementen waarvoor de verplichte metagegevens ontbreken, kunnen [!DNL Experience Manager] elementen weergeven die geldige metagegevens hebben. De resultaten zijn gebaseerd op de eigenschap voor geïndexeerde metagegevens. | Nadat de metagegevens zijn bijgewerkt, moet de index opnieuw worden geïndexeerd om de juiste status van metagegevens voor elementen weer te geven. Zie [verplichte metagegevens](metadata-schemas.md#define-mandatory-metadata). |
| Te veel zoekresultaten. | Brede zoekparameter. | Overweeg het [bereik van zoeken](#scope) te beperken. Het gebruik van slimme tags kan meer zoekresultaten opleveren dan u had verwacht. Zie [zoekgedrag met slimme tags](#withsmarttags). |
| Onverwante of gedeeltelijk verwante zoekresultaten. | Wijzigingen in zoekgedrag met slimme tags. | Begrijp [hoe zoekopdracht verandert na slimme tags](#withsmarttags). |
| Geen suggesties voor automatisch aanvullen van elementen. | Nieuw geüploade elementen zijn nog niet geïndexeerd. De metagegevens zijn niet direct beschikbaar als suggesties wanneer u een trefwoord in de zoekbalk typt. | [!DNL Assets] wacht tot een time-outperiode (standaard één uur) is verstreken voordat een achtergrondtaak wordt uitgevoerd om de metagegevens voor alle nieuw geüploade of bijgewerkte elementen te indexeren en voegt de metagegevens vervolgens toe aan de lijst met suggesties. |
| Geen zoekresultaten. | <ul><li>Elementen die overeenkomen met uw query bestaan niet. </li><li> Whitespace toegevoegd vóór de zoekquery. </li><li> Niet-ondersteund metagegevensveld bevat het trefwoord waarnaar u hebt gezocht.</li><li> Zoeken tijdens offline uitvoering van een element. </li></ul> | <ul><li>Zoeken met een ander trefwoord. U kunt ook slim labelen of zoeken op basis van gelijkenis gebruiken om de zoekresultaten te verbeteren. </li><li>[Bekende beperking](#limitations).</li><li>Niet alle metagegevensvelden worden in aanmerking genomen voor zoekopdrachten. Zie [scope](#scope).</li><li>Later zoeken of on-time en off-time wijzigen voor de vereiste elementen.</li></ul> |
| Zoekfilter of voorspelling is niet beschikbaar. | <ul><li>Het zoekfilter is niet geconfigureerd.</li><li>Het is niet beschikbaar voor uw aanmelding.</li><li>(Minder waarschijnlijk) De onderzoeksopties worden niet aangepast op de plaatsing u gebruikt.</li></ul> | <ul><li>Neem contact op met de beheerder om te controleren of de zoekaanpassingen beschikbaar zijn of niet.</li><li>Neem contact op met de beheerder om te controleren of uw account de rechten/machtigingen heeft om de aanpassing te gebruiken.</li><li>Neem contact op met de beheerder en controleer de beschikbare aanpassingen voor de [!DNL Assets]-implementatie die u gebruikt.</li></ul> |
| Bij het zoeken naar visueel vergelijkbare afbeeldingen ontbreekt een verwachte afbeelding. | <ul><li>Afbeelding is niet beschikbaar in [!DNL Experience Manager].</li><li>Afbeelding is niet geïndexeerd. Doorgaans wanneer het onlangs is geüpload.</li><li>Afbeelding heeft geen slimme tags.</li></ul> | <ul><li>Voeg de afbeelding toe aan [!DNL Assets].</li><li>Neem contact op met de beheerder om de gegevensopslagruimte opnieuw te indexeren. Zorg er ook voor dat u de juiste index gebruikt.</li><li>Neem contact op met de beheerder om de relevante elementen een slimme tag te geven.</li></ul> |
| Bij het zoeken naar visueel vergelijkbare afbeeldingen wordt een irrelevante afbeelding weergegeven. | Zichtbaar zoekgedrag. | [!DNL Experience Manager] geeft zoveel mogelijk relevante activa weer. Eventuele minder relevante afbeeldingen worden aan de resultaten toegevoegd, maar met een lagere zoekpositie. De kwaliteit van de overeenkomsten en de relevantie van de gezochte elementen nemen af wanneer u de zoekresultaten omlaag schuift. |
| Wanneer u zoekresultaten selecteert en gebruikt, wordt niet op alle gezochte elementen ingegaan. | Met de optie [!UICONTROL Select All] worden alleen de eerste 100 zoekresultaten in de kaartweergave geselecteerd en de eerste 200 zoekresultaten in de lijstweergave. |  |

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] zoekimplementatiegids](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/developing/search-tutorial-develop.html)
>* [Geavanceerde configuratie om zoekresultaten te verhogen](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/search-and-discovery/search-boost.html)
>* [Zoeken naar slimme vertaling configureren](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/translation/smart-translation-search-technical-video-setup.html)

