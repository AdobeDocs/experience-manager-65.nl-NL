---
title: Digitale elementen en afbeeldingen zoeken in  [!DNL Adobe Experience Manager]
description: Leer hoe te om de vereiste activa in  [!DNL Adobe Experience Manager]  te vinden door het paneel van Filters te gebruiken, en hoe te om de activa te gebruiken die in onderzoek verschijnen.
contentOwner: AG
mini-toc-levels: 1
feature: Search, Metadata
role: User
exl-id: 588433b2-564a-430f-9d04-480465ece2ad
hide: true
solution: Experience Manager, Experience Manager Assets
source-git-commit: 0b90fdd13efc5408ef94ee1966f04a80810b515e
workflow-type: tm+mt
source-wordcount: '5619'
ht-degree: 2%

---

# Digitale middelen zoeken in [!DNL Adobe Experience Manager] {#search-assets-in-aem}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/assets/manage/search-assets) |
| AEM 6.5 | Dit artikel |

[!DNL Adobe Experience Manager Assets] biedt robuuste methoden voor het detecteren van elementen die u helpen een hogere snelheid van de inhoud te bereiken. Uw teams kunnen tijd aan markt met een naadloze, intelligente onderzoekservaring verminderen gebruikend out-of-the-box functionaliteit en douanemethodes. Het zoeken naar middelen is van cruciaal belang voor het gebruik van een systeem voor het beheer van digitale activa — of het nu gaat om verder gebruik door creatieve ondernemingen, voor een robuust beheer van activa door zakelijke gebruikers en marketeers, of voor beheer door DAM-beheerders. Eenvoudige, geavanceerde en aangepaste zoekopdrachten die u kunt uitvoeren via de gebruikersinterface van [!DNL Assets] of andere apps en oppervlakken helpen deze gebruiksgevallen te verhelpen.

[!DNL Experience Manager Assets] steunt de volgende gebruiksgevallen en dit artikel beschrijft het gebruik, de concepten, de configuraties, de beperkingen, en het oplossen van problemen voor deze gebruiksgevallen.

| Middelen zoeken | Zoekfuncties configureren en beheren | Werken met zoekresultaten |
|---|---|---|
| [ Basisonderzoeken ](#searchbasics) | [ index van het Onderzoek ](#searchindex) | [ de resultaten van de Soort ](#sort) |
| [ Begrijp onderzoek UI ](#searchui) | [ Visuele of gelijkenis onderzoek ](#configvisualsearch) | [ Controle de eigenschappen en de meta-gegevens van een activa ](#checkinfo) |
| [ suggesties van het Onderzoek ](#searchsuggestions) | [ Verplichte meta-gegevens ](#mandatorymetadata) | [ Download ](#download) |
| [ begrijp onderzoeksresultaten en gedrag ](#searchbehavior) | [ wijzig onderzoeksfacetten ](#searchfacets) | [ Bulk meta-gegevensupdates ](#metadataupdates) |
| [ rang van het Onderzoek en het opvoeren ](#searchrank) | [ extractie van de Tekst ](#extracttextupload) | [ Slimme inzamelingen ](#collections) |
| [ Geavanceerd onderzoek: het filtreren en werkingsgebied van onderzoek ](#scope) | [ de Voorspelden van de Douane ](#custompredicates) | [ begrijp en los onverwachte resultaten ](#unexpected-results) problemen op |
| [ Onderzoek van andere oplossingen en apps ](#search-assets-other-surfaces):<ul><li>[ de Verbinding van Activa van Adobe ](#aal)</li><li>[ Brand Portal ](#brand-portal)</li><li>[ Experience Manager Desktop app ](#desktop-app)</li><li>[ de beelden van Adobe Stock ](#adobe-stock)</li><li>[ Dynamische activa van Media ](#dynamic-media)</li></ul> | | |
| [ selecteur van Activa ](#asset-picker) | | |
| [ Beperkingen ](#limitations) en [ Uiteinden ](#tips) | | |
| [ Afgedrukte voorbeelden ](#samples) | | |

Zoek naar digitale middelen gebruikend het gebied van Onderzoek bij de bovenkant van de [!DNL Experience Manager] Webinterface. Ga naar **[!UICONTROL Assets]** > **[!UICONTROL Files]** in [!DNL Experience Manager], klik ![ search_icon ](assets/do-not-localize/search_icon.png) in hoogste bar, ga onderzoekssleutelwoord in, en selecteer `Return`. U kunt ook de trefwoordsneltoets `/` (slash) gebruiken om het veld Onderzoek te openen. `Location:Assets` is vooraf geselecteerd om de zoekopdrachten te beperken tot DAM-elementen. [!DNL Experience Manager] biedt suggesties als u begint met het typen van een trefwoord voor zoeken.

Gebruik het deelvenster **[!UICONTROL Filters]** om te zoeken naar elementen, mappen, tags en metagegevens. U kunt zoekresultaten filteren op basis van de verschillende opties (voorspelling), zoals bestandstype, bestandsgrootte, datum van laatste wijziging, status van element, gegevens over inzichten en Adobe Stock-licenties. U kunt het paneel van Filters aanpassen en onderzoek toevoegen of verwijderen voorspelt gebruikend [ onderzoeksfacetten ](/help/assets/search-facets.md). Het filter [!UICONTROL File Type] in het deelvenster [!UICONTROL Filters] heeft selectievakjes met gemengde status. Tenzij u alle geneste voorspellen (of indelingen) selecteert, worden de selectievakjes op het eerste niveau daarom gedeeltelijk gecontroleerd.

De zoekfunctie van [!DNL Experience Manager] ondersteunt het zoeken naar verzamelingen en het zoeken naar elementen in een verzameling. Zie [ onderzoeksinzamelingen ](/help/assets/manage-collections.md).

## Zoekinterface begrijpen {#searchui}

Verken uzelf met de zoekinterface en de beschikbare acties.

![ begrijp de interface van de het onderzoeksresultaten van Experience Manager Assets ](assets/aem_search_results.png)

*Cijfer: Begrijp [!DNL Experience Manager Assets] interface van onderzoeksresultaten.*

**A.** sparen onderzoek als slimme inzameling. **B.** Filters of voorspelt om de onderzoeksresultaten te beperken. **C.** de dossiers van de vertoning, omslagen, of allebei. **D.** Klik op Filters om het linkerspoor te openen of te sluiten. **E.** Zoeklocatie is DAM. **F.** het gebied van het Onderzoek met user-provided onderzoekssleutelwoord. **G.** selecteer de geladen onderzoeksresultaten. **H.** Aantal getoonde onderzoeksresultaten uit de totale onderzoeksresultaten. **I.** Dichte onderzoek. **J.** Schakelaar tussen kaartmening en lijstmening.

### Dynamische zoekfacetten {#dynamicfacets}

U kunt de gewenste elementen sneller vinden op de pagina met zoekresultaten met behulp van het dynamisch bijgewerkte aantal verwachte zoekresultaten in de zoekfacetten. Het verwachte aantal elementen wordt bijgewerkt, zelfs voordat het zoekfilter wordt toegepast. Door het verwachte aantal op het filter te zien, kunt u snel en efficiënt door de zoekresultaten navigeren.

![ zie het benaderende aantal activa zonder het filtreren onderzoeksresultaten in onderzoeksfacetten.](assets/asset_search_results_in_facets_filters.png)

*Cijfer: Zie het benaderende aantal activa zonder het filtreren onderzoeksresultaten in onderzoeksfacetten.*

## Zoekresultaten en gedrag begrijpen {#searchbehavior}

### Standaardzoektermen en -resultaten {#searchbasics}

U kunt trefwoordzoekopdrachten uitvoeren vanuit het veld UniverseelZoeken. De trefwoordzoekopdracht is niet hoofdlettergevoelig en bestaat uit een zoekopdracht in volledige tekst (in de veelgebruikte metagegevensvelden). Als er meerdere trefwoorden worden gebruikt, is `AND` de standaardoperator tussen de trefwoorden.

De resultaten worden gesorteerd op relevantie, te beginnen met de dichtstbijzijnde overeenkomsten. Voor meerdere trefwoorden zijn relevantere resultaten de elementen die beide termen in de metagegevens bevatten. Trefwoorden die in de metagegevens voorkomen, krijgen een hogere positie dan trefwoorden die in andere metagegevensvelden worden weergegeven. Met [!DNL Experience Manager] kunt u een bepaalde zoekterm een hogere waarde geven. Ook, is het mogelijk om [ de rang ](#searchrank) van een paar gerichte activa voor specifieke onderzoekstermijnen op te voeren.

Om de relevante activa snel te vinden, verstrekt de rijke interface het filtreren, het sorteren, en selectiemechanismen. U kunt resultaten filteren op basis van meerdere criteria en het aantal gezochte elementen voor verschillende filters bekijken. U kunt de zoekopdracht ook opnieuw uitvoeren door de query in het veld Onderzoek te wijzigen. Wanneer u de zoektermen of filters wijzigt, blijven de andere filters van toepassing om de context van de zoekopdracht te behouden.

Wanneer de resultaten veel elementen zijn, geeft [!DNL Experience Manager] de eerste 100 weer in de kaartweergave en 200 in de lijstweergave. Wanneer gebruikers schuiven, worden meer elementen geladen. Dit is om de prestaties te verbeteren. Bekijk een videodemonstratie van het [ aantal getoonde activa ](https://www.youtube.com/watch?v=LcrGPDLDf4o).

Het kan voorkomen dat de zoekresultaten een aantal onverwachte elementen bevatten. Voor meer info, zie [ onverwachte resultaten ](#unexpected-results).

[!DNL Experience Manager] kan in een groot aantal bestandsindelingen zoeken en de zoekfilters kunnen aan uw zakelijke vereisten worden aangepast. Neem contact op met uw beheerder om te weten welke zoekopties beschikbaar worden gesteld voor uw DAM-opslagplaats en welke beperkingen uw account heeft.

### Resultaten met en zonder verbeterde slimme tags {#withsmarttags}

Standaard worden in [!DNL Experience Manager] de zoektermen gecombineerd met een AND-component. Kijk bijvoorbeeld eens naar het doorzoeken van trefwoordenvrouwen. In de zoekresultaten worden standaard alleen de elementen weergegeven met trefwoorden voor vrouwen en het gebruik van trefwoorden in de metagegevens. Hetzelfde gedrag blijft behouden wanneer speciale tekens (punten, onderstrepingstekens of streepjes) bij de trefwoorden worden gebruikt. De volgende zoekopdrachten retourneren dezelfde resultaten:

* `woman running`
* `woman.running`
* `woman-running`

De query `woman -running` retourneert echter elementen zonder `running` in de metagegevens.
Als u slimme tags gebruikt, voegt u een extra `OR` -component toe om een zoekterm te zoeken als de toegepaste slimme tags. Een element dat is gelabeld met `woman` of `running` en dat slimme tags gebruikt, wordt ook weergegeven in een dergelijke zoekopdracht. De zoekresultaten zijn dus een combinatie van:

* Assets met `woman` en `running` trefwoorden in de metagegevens (standaardgedrag).

* Assets Smart gelabeld met een van de trefwoorden (gedrag Slimme tags).

### Suggesties zoeken terwijl u typt {#searchsuggestions}

Wanneer u trefwoorden begint te typen, stelt [!DNL Experience Manager] de mogelijke zoektrefwoorden of -woordgroepen voor. De suggesties zijn gebaseerd op de metagegevens van de bestaande elementen. In [!DNL Experience Manager] worden alle metagegevensvelden geïndexeerd voor hulp bij het zoeken. Voor zoeksuggesties gebruikt het systeem de waarden van de volgende paar metagegevensvelden. Als u zoeksuggesties wilt doen, kunt u de volgende velden vullen met de juiste trefwoorden:

* Elementlabels. (afbeeldingen `jcr:content/metadata/cq:tags` )
* Titel van element. (afbeeldingen `jcr:content/metadata/dc:title` )
* Beschrijving van element. (afbeeldingen `jcr:content/metadata/dc:description` )
* Titel in de gegevensopslagruimte van het JCR. De waarde wordt mogelijk toegewezen aan de titel Element. (afbeeldingen `jcr:content/jcr:title` )
* Beschrijving in de gegevensopslagruimte van de JCR. De waarde wordt mogelijk toegewezen aan de beschrijving van het element. (afbeeldingen `jcr:content/jcr:description` )

Als u suggesties voor meerdere zoektrefwoorden wilt ontvangen, blijft u alle trefwoorden typen zonder een suggestie voor één trefwoord te selecteren.

![ Type veelvoudige sleutelwoorden om suggesties te bekijken die hen allen ](assets/search_suggestionsmanykeywords.gif) passen

*Cijfer: Type veelvoudige sleutelwoorden om suggesties te bekijken die hen allen passen.*

### Rangschikking en boosting zoeken {#searchrank}

De zoekresultaten die overeenkomen met alle zoektermen in metagegevensvelden worden eerst weergegeven, gevolgd door de zoekresultaten die overeenkomen met een van de zoektermen in de slimme tags. In het bovenstaande voorbeeld is de weergavevolgorde van zoekresultaten bij benadering:

1. Komt overeen met `woman running` in de verschillende metagegevensvelden.
1. Komt overeen met `woman running` in slimme tags.
1. Komt overeen met `woman` of `running` in slimme tags.

U kunt de relevantie van trefwoorden voor bepaalde elementen verbeteren om zoekopdrachten op basis van trefwoorden te stimuleren. Met andere woorden, de afbeeldingen waarvoor u specifieke trefwoorden promoot, worden boven aan de zoekresultaten weergegeven wanneer u op basis van deze trefwoorden zoekt.

1. Open vanuit de gebruikersinterface van [!DNL Assets] de eigenschappenpagina voor het element. Klik op **[!UICONTROL Advanced]** en klik op **[!UICONTROL Add]** onder **[!UICONTROL Elevate for search keywords]** .
1. Geef in het vak **[!UICONTROL Search Promote]** een trefwoord op waarvoor u de zoekopdracht naar de afbeelding wilt opvoeren en klik vervolgens op **[!UICONTROL Add]** . U kunt meerdere trefwoorden op dezelfde manier opgeven.
1. Klik op **[!UICONTROL Save & Close]**. Het element dat u voor dit trefwoord hebt gepromoot, wordt weergegeven in de beste zoekresultaten.

U kunt dit in uw voordeel gebruiken door de positie van bepaalde elementen in de zoekresultaten voor het doeltrefwoord te verhogen. Zie de onderstaande voorbeeldvideo. Voor gedetailleerde info, zie [ onderzoek in  [!DNL Experience Manager] ](https://experienceleague.adobe.com/nl/docs/experience-manager-learn/assets/search-and-discovery/search-boost).

>[!VIDEO](https://video.tv.adobe.com/v/16766/?quality=6)

*Video: Begrijp hoe de onderzoeksresultaten gerangschikt zijn en hoe de rang kan worden beïnvloed.*

## Geavanceerd zoeken {#scope}

[!DNL Experience Manager] biedt verschillende methoden, zoals filters die van toepassing zijn op de gezochte elementen, zodat u de gewenste elementen sneller kunt vinden. Hieronder worden enkele veelgebruikte methoden beschreven. Sommige [ geïllustreerde voorbeelden ](#samples) worden hieronder gedeeld.

**Onderzoek naar dossiers of omslagen**: In de onderzoeksresultaten, zie of dossiers, omslagen, of allebei. In het deelvenster **[!UICONTROL Filters]** kunt u de juiste optie selecteren. Zie [ onderzoeksinterface ](#searchui).

**Onderzoek naar activa binnen een omslag**: U kunt het onderzoek tot een specifieke omslag beperken. Voeg in het deelvenster **[!UICONTROL Filters]** het pad van een map toe. U kunt slechts één map tegelijk selecteren.

![ Beperk onderzoeksresultaten tot een omslag door een omslagweg in het paneel van Filters toe te voegen ](assets/search_folder_select.gif)

*Cijfer: De onderzoeksresultaten van de grens aan een omslag door een omslagweg in het paneel van Filters toe te voegen.*

### Vergelijkbare afbeeldingen zoeken {#visualsearch}

Als u afbeeldingen wilt zoeken die visueel lijken op een door de gebruiker geselecteerde afbeelding, klikt u op de optie **[!UICONTROL Find Similar]** in de kaartweergave van een afbeelding of op de werkbalk. In [!DNL Experience Manager] worden de slimme getagde afbeeldingen uit de DAM-opslagplaats weergegeven die lijken op een door de gebruiker geselecteerde afbeelding. Zie [Zoeken naar overeenkomsten configureren](#configvisualsearch).

![ vind gelijkaardige beelden gebruikend de optie in de kaartmening ](assets/search_find_similar.png)

*Cijfer: Vind gelijkaardige beelden gebruikend de optie in de kaartmening.*

### Adobe Stock-afbeeldingen {#adobe-stock}

Van binnen het [!DNL Experience Manager] gebruikersinterface, kunnen de gebruikers [ activa van Adobe Stock ](/help/assets/aem-assets-adobe-stock.md) zoeken en de vereiste activa vergunning geven. Voeg `Location: Adobe Stock` toe in de balk Zoeken. U kunt ook het deelvenster Filters gebruiken om alle middelen te zoeken waarvoor een licentie is verleend of om een bepaald element te zoeken aan de hand van het Adobe Stock-bestandsnummer.

### Dynamische media-elementen {#dmassets}

U kunt filteren op dynamische media-afbeeldingen door **[!UICONTROL Dynamic Media]** > **[!UICONTROL Sets]** te selecteren in het deelvenster **[!UICONTROL Filters]**. Het filter en toont activa zoals beeldreeksen, carrousels, gemengde media reeksen, en spin reeksen.

### GQL-zoekopdracht met specifieke waarden in metagegevensvelden {#gql-search}

U kunt zoeken naar digitale elementen op basis van exacte waarden van metagegevensvelden, zoals titel, beschrijving en maker. Met de zoekfunctie voor volledige tekst GQL haalt u alleen die elementen op waarvan de metagegevenswaarde exact overeenkomt met uw zoekopdracht. De namen van de eigenschappen (Maker, Titel, enzovoort) en de waarden zijn hoofdlettergevoelig.

| Metagegevensveld | Facetwaarde en gebruik |
|---|---|
| Titel | titel:John |
| Maker | maker:John |
| Locatie | locatie:NA |
| Beschrijving | beschrijving:&quot;Voorbeeldafbeelding&quot; |
| Gereedschap Maker | creatortool:&quot;Adobe Photoshop&quot; |
| Copyrighteigenaar | copyrightowner:&quot;Adobe Inc&quot; |
| Medewerker | contribuant:John |
| Gebruiksvoorwaarden | usageterms:&quot;CopyRights Reserved&quot; |
| Gemaakt | gemaakt:YYYY-MM-DDTHH |
| Vervaldatum | verloopt:YYYY-MM-DDTHH |
| Op tijd | ontime:YYYY-MM-DDTHH |
| Uit-tijd | offtime:YYYY-MM-DDTHH |
| Tijdsbereik (verloopt dateontime, offtime) | facet field : lowerbound..bovenaan |
| Pad | /content/dam/&lt;naam map> |
| PDF-titel | pdftitle:&quot;Adobe-document&quot; |
| Onderwerp | onderwerp: &quot;Opleiding&quot; |
| Tags | tags:&quot;Locatie en reizen&quot; |
| Type | type:&quot;image\png&quot; |
| Breedte van afbeelding | breedte:ondergrens..bovenaan |
| Hoogte van afbeelding | hoogte:ondergrens..bovenaan |
| Persoon | persoon:John |

De eigenschappen `path` , `limit` , `size` en `orderby` kunnen niet met een `OR` -operator worden gecombineerd met een andere eigenschap.

<!-- TBD: Where are the limit, size, orderby properties defined?
-->

Het sleutelwoord voor een user-generated bezit is zijn gebiedsetiket in de bezitsredacteur in kleine letters, met verwijderde ruimten.

Hier volgen enkele voorbeelden van zoekindelingen voor complexe query&#39;s:

* Alle elementen met meerdere facetvelden weergeven (bijvoorbeeld: title=Jan Smit en creator tool = Adobe Photoshop): `title:"John Doe" creatortool:Adobe*`
* Om alle activa te tonen wanneer de facetwaarde niet één enkel woord maar een zin (bijvoorbeeld: title=Scott Reynolds) is: `title:"Scott Reynolds"`
* Elementen weergeven met meerdere waarden van één eigenschap (bijvoorbeeld: title=Scott Reynolds of Jan Smit): `title:"Scott Reynolds" OR "John Doe"`
* Elementen weergeven waarvan de eigenschapswaarden beginnen met een specifieke tekenreeks (bijvoorbeeld: title is Scott Reynolds): `title:Scott*`
* Elementen met eigenschapswaarden die eindigen met een specifieke tekenreeks (bijvoorbeeld: title is Scott Reynolds) weergeven: `title:*Reynolds`
* Elementen weergeven met een eigenschapswaarde die een specifieke tekenreeks bevat (bijvoorbeeld: title = Basel Meeting Room): `title:*Meeting*`
* Elementen weergeven die een bepaalde tekenreeks bevatten en een specifieke eigenschapswaarde hebben (bijvoorbeeld: zoeken naar tekenreeks Adobe in elementen met de naam title=Jan Smit): `*Adobe* title:"John Doe"`

## Digitale elementen zoeken vanuit andere [!DNL Experience Manager] -aanbiedingen of -interfaces {#search-assets-other-surfaces}

[!DNL Adobe Experience Manager] verbindt de DAM-opslagplaats met verschillende andere [!DNL Experience Manager] -oplossingen om snellere toegang tot digitale middelen te bieden en de creatieve workflows te stroomlijnen. Elke detectie van middelen begint met bladeren of zoeken. Het zoekgedrag blijft grotendeels hetzelfde op de verschillende oppervlakken en oplossingen. Sommige zoekmethoden veranderen als het doelpubliek, de gebruiksgevallen en de gebruikersinterface voor de [!DNL Experience Manager] -oplossingen. De specifieke methoden worden gedocumenteerd voor de afzonderlijke oplossingen in de onderstaande koppelingen. De algemeen toepasselijke tips en gedragingen worden in dit artikel beschreven.

### Digitale middelen zoeken vanuit het deelvenster Adobe Asset Link {#aal}

Creatieve professionals kunnen nu met Adobe Asset Link toegang krijgen tot inhoud die is opgeslagen in [!DNL Experience Manager Assets] zonder de ondersteunde Adobe Creative Cloud-apps te verlaten. Creatieve personen kunnen naadloos door elementen bladeren, zoeken, uitchecken en inchecken via het deelvenster in de app in de apps: [!DNL Adobe Photoshop] , [!DNL Adobe Illustrator] en [!DNL Adobe InDesign] . [!DNL Adobe Creative Cloud] Met Asset Link kunnen gebruikers ook visueel vergelijkbare resultaten zoeken. De resultaten van de visuele zoekopdrachten worden aangedreven door instructiealgoritmen van Adobe Sensei-computers en helpen gebruikers bij het zoeken naar beelden die er in esthetisch opzicht op lijken. Zie [ onderzoek en doorblader activa ](https://helpx.adobe.com/nl/enterprise/using/manage-assets-using-adobe-asset-link.html#UseAdobeAssetLink) gebruikend de Verbinding van Activa van Adobe.

### Digitale middelen zoeken in de [!DNL Experience Manager] bureaubladtoepassing {#desktop-app}

Creative-professionals gebruiken de bureaubladtoepassing om de [!DNL Experience Manager Assets] gemakkelijk doorzoekbaar te maken en beschikbaar te maken op hun lokale bureaublad (Win of Mac). Creative Cloud kan de gewenste middelen eenvoudig weergeven in Mac Finder of Windows Verkenner, geopend in bureaubladtoepassingen en lokaal gewijzigd. De wijzigingen worden opgeslagen in [!DNL Experience Manager] met een nieuwe versie die in de opslagplaats is gemaakt. De toepassing ondersteunt standaardzoekopdrachten met een of meer trefwoorden, `*` en `?` jokertekens en `AND` operator. Zie [ doorbladeren, onderzoek, en voorproefactiva ](https://experienceleague.adobe.com/nl/docs/experience-manager-desktop-app/using/using#browse-search-preview-assets) in Desktop app.

### Digitale middelen zoeken in [!DNL Brand Portal] {#brand-portal}

Line-of-business gebruikers en marketers gebruiken Brand Portal om de goedgekeurde digitale middelen efficiënt en veilig te delen met hun uitgebreide interne teams, partners en wederverkopers. Zie [ onderzoeksactiva op Brand Portal ](https://experienceleague.adobe.com/nl/docs/experience-manager-brand-portal/using/search-capabilities/brand-portal-searching).

### [!DNL Adobe Stock] afbeeldingen zoeken {#adobe-stock1}

Vanuit de gebruikersinterface van [!DNL Experience Manager] kunnen gebruikers zoeken in Adobe Stock-middelen en een licentie voor de vereiste middelen aanschaffen. Voeg `Location: Adobe Stock` toe in het veld Onderzoek. U kunt ook het deelvenster **[!UICONTROL Filters]** gebruiken om alle onder licentie gegeven of niet-gelicentieerde elementen te zoeken of een bepaald element te zoeken aan de hand van het Adobe Stock-bestandsnummer. Zie [  [!DNL Adobe Stock]  beelden in  [!DNL Experience Manager]](/help/assets/aem-assets-adobe-stock.md#usemanage) beheren.

### Zoeken in [!DNL Dynamic Media] elementen {#dynamic-media}

U kunt filteren op dynamische media-afbeeldingen door **[!UICONTROL Dynamic Media]** > **[!UICONTROL Sets]** te selecteren in het deelvenster **[!UICONTROL Filters]**. Het filtert op en toont assets zoals afbeeldingsets, carrousels, gemengde mediasets, en spinsets. Tijdens het ontwerpen van webpagina&#39;s kunnen auteurs naar sets zoeken in de Inhoudszoeker. Een filter voor sets is beschikbaar in een pop-upmenu.

### Digitale middelen zoeken in de Inhoudszoeker bij het ontwerpen van webpagina&#39;s {#content-finder}

Auteurs kunnen de Inhoudszoeker gebruiken om in de DAM-opslagplaats te zoeken naar de relevante elementen en de elementen te gebruiken op de webpagina&#39;s die ze maken. Auteurs kunnen ook de Connected Assets-functionaliteit gebruiken om te zoeken naar elementen die beschikbaar zijn op een externe [!DNL Experience Manager] -implementatie. Auteurs kunnen deze elementen vervolgens op webpagina&#39;s gebruiken bij een lokale [!DNL Experience Manager] -implementatie. Zie [ gebruik verre activa ](/help/assets/use-assets-across-connected-assets-instances.md#use-remote-assets).

### Verzamelingen zoeken {#collections}

De zoekfunctie van [!DNL Experience Manager] ondersteunt het zoeken naar verzamelingen en het zoeken naar elementen in een verzameling. Zie [ onderzoeksinzamelingen ](/help/assets/manage-collections.md).

## Elementkiezer {#asset-picker}

>[!NOTE]
>
>De activa selecteur werd genoemd [ activa plukker ](https://experienceleague.adobe.com/nl/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions) in vroegere versies van [!DNL Adobe Experience Manager].

Met de functie Asset Selector kunt u de DAM-middelen op een speciale manier zoeken, filteren en doorbladeren. Asset Selector is beschikbaar via `https://[aem_server]:[port]/aem/assetpicker.html` . U kunt de metagegevens ophalen van elementen die u selecteert met de elementkiezer. U kunt de toepassing starten met ondersteunde aanvraagparameters, zoals het type element (afbeelding, video, tekst) en de selectiemodus (enkele of meerdere selecties). Deze parameters stellen de context van de elementenkiezer voor een bepaalde zoekinstantie in en blijven tijdens de selectie intact.

De elementenkiezer gebruikt het HTML5 `Window.postMessage` -bericht om gegevens voor het geselecteerde element naar de ontvanger te verzenden. Deze functie werkt alleen in de modus Bladeren en alleen met de resultatenpagina van Omnsearch.

Geef de volgende aanvraagparameters in een URL door om de elementenkiezer in een bepaalde context te starten:

| Naam | Waarden | Voorbeeld | Doel |
|---|---|---|---|
| bronachtervoegsel (B) | De weg van de omslag als middelachtervoegsel in URL: [ https://localhost:4502/aem/assetpicker.html/&lt;folder_path> ](https://localhost:4502/aem/assetpicker.html) | Als u de elementenkiezer wilt starten terwijl een bepaalde map is geselecteerd en de map `/content/dam/we-retail/en/activities` geselecteerd is, moet de URL de volgende vorm hebben: `https://localhost:4502/aem/assetpicker.html/content/dam/we-retail/en/activities?assettype=images` | Als u wilt dat een bepaalde map wordt geselecteerd wanneer de elementenkiezer wordt gestart, geeft u deze door als een bronachtervoegsel. |
| `mode` | enkelvoudig, meerdere | <ul><li>`https://localhost:4502/aem/assetpicker.html?mode=single`</li><li>`https://localhost:4502/aem/assetpicker.html?mode=multiple`</li></ul> | In meerdere modi kunt u meerdere elementen tegelijk selecteren met de elementkiezer. |
| `dialog` | true, false | [ https://localhost:4502/aem/assetpicker.html?dialog=true](https://localhost:4502/aem/assetpicker.html?dialog=true) | Gebruik deze parameters om de elementenkiezer te openen als granietdialoogvenster. Deze optie is alleen van toepassing wanneer u de elementenkiezer start via Granite Path Field en deze configureert als pickerSrc URL. |
| `root` | &lt;folder_path> | `https://localhost:4502/aem/assetpicker.html?assettype=images&root=/content/dam/we-retail/en/activities` | Gebruik deze optie om de hoofdmap voor de elementenkiezer op te geven. In dit geval kunt u met de elementenkiezer alleen onderliggende elementen (direct/indirect) in de hoofdmap selecteren. |
| `viewmode` | zoeken | | De elementkiezer starten in de zoekmodus met de parameters `assettype` en `mimetype` . |
| `assettype` | Afbeeldingen, documenten, multimedia, archieven. | <ul><li>`https://localhost:4502/aem/assetpicker.html?viewmode=search&assettype=images`</li><li> `https://localhost:4502/aem/assetpicker.html?viewmode=search&assettype=documents` </li><li> `https://localhost:4502/aem/assetpicker.html?viewmode=search&assettype=multimedia` </li><li> `https://localhost:4502/aem/assetpicker.html?viewmode=search&assettype=archives` </li></ul> | Gebruik de optie om elementtypen te filteren op basis van de opgegeven waarde. |
| `mimetype` | MIME-type (`/jcr:content/metadata/dc:format`) van een element (jokerteken wordt ook ondersteund). | <ul><li>`https://localhost:4502/aem/assetpicker.html?mimetype=image/png`</li><li>`https://localhost:4502/aem/assetpicker.html?mimetype=*png`</li><li>`https://localhost:4502/aem/assetpicker.html?mimetype=*presentation`</li><li>`https://localhost:4502/aem/assetpicker.html?mimetype=*presentation&mimetype=*png`</li></ul> | Gebruik deze optie om elementen te filteren op basis van het MIME-type. |

Ga naar `https://[aem_server]:[port]/aem/assetpicker` als u de interface van de elementenkiezer wilt openen. Navigeer naar de gewenste map en selecteer een of meer elementen. U kunt ook zoeken naar het gewenste element in het vak Onderzoek, het filter toepassen zoals is vereist en het vervolgens selecteren.

![ doorbladert en selecteert activa in de activaselecteur ](assets/assetpicker.png)

*Cijfer: doorblader en selecteer activa in de activaselecteur.*

## Beperkingen {#limitations}

De zoekfunctie in [!DNL Experience Manager Assets] heeft de volgende beperkingen:

* Geef geen regelafstand op in de zoekopdracht als de zoekopdracht anders niet werkt.
* [!DNL Experience Manager] blijft mogelijk de zoekterm weergeven nadat u eigenschappen van een element hebt geselecteerd in de gezochte resultaten en vervolgens de zoekopdracht hebt geannuleerd. <!-- (CQ-4273540) -->
* Wanneer u naar mappen of bestanden en mappen zoekt, kunnen de zoekresultaten op geen enkele parameter worden gesorteerd.
* Als u `Return` selecteert zonder op de zoekbalk te typen, retourneert [!DNL Experience Manager] een lijst met alleen bestanden en niet mappen. Als u specifiek naar mappen zoekt zonder een trefwoord te gebruiken, geeft [!DNL Experience Manager] geen resultaten.
* U kunt zoeken in volledige tekst op mappen. Geef een zoekterm op die de zoekopdracht moet gebruiken.

Het visuele onderzoek of het gelijkenis onderzoek heeft de volgende beperkingen:

* Het visuele onderzoek werkt het best met een grote bewaarplaats. Hoewel er geen minimaal aantal afbeeldingen vereist is voor goede resultaten, is de kwaliteit van overeenkomsten met een paar afbeeldingen minder goed dan de overeenkomsten met een grote opslagplaats.
* U kunt het model of de training [!DNL Experience Manager] niet wijzigen om vergelijkbare afbeeldingen te zoeken. Als u bijvoorbeeld slimme tags toevoegt of verwijdert aan een paar elementen, verandert het model niet. De elementen worden uitgesloten van de visueel vergelijkbare zoekresultaten.

De zoekfunctionaliteit kan prestatiebeperkingen hebben in de volgende scenario&#39;s:

* De kaartweergave heeft een snellere laadtijd dan de lijstweergave om de zoekresultaten weer te geven.

## Zoektips {#tips}

* Gebruik bij het controleren van de revisiestatus van de middelen de juiste optie om te bepalen welke middelen zijn goedgekeurd of welke activa nog moeten worden goedgekeurd.
* Gebruik de Insights-voorspelling om te zoeken naar ondersteunde middelen op basis van hun gebruiksstatistieken die zijn verkregen van verschillende Creative-apps. Gebruiksgegevens worden gegroepeerd onder Gebruiksscore, Impressies, Klikken en Mediakanalen waar de elementen categorieën weergeven.
* Schakel het selectievakje **[!UICONTROL Select All]** in om de gezochte elementen te selecteren. In [!DNL Experience Manager] worden in eerste instantie 100 elementen weergegeven in de kaartweergave en 200 elementen in de lijstweergave. Er worden meer elementen geladen wanneer u door de zoekresultaten schuift. U kunt meer elementen selecteren dan de geladen elementen. Het aantal geselecteerde elementen wordt in de rechterbovenhoek van de pagina met zoekresultaten weergegeven. U kunt de selectie bijvoorbeeld activeren door de geselecteerde elementen te downloaden, de eigenschappen van metagegevens voor de geselecteerde elementen bulksgewijs bij te werken of de geselecteerde elementen aan een verzameling toe te voegen. Wanneer er meer elementen zijn geselecteerd dan worden weergegeven, wordt een actie toegepast op alle geselecteerde elementen of wordt in een dialoogvenster het aantal elementen weergegeven waarop de actie wordt toegepast. Als u een handeling wilt toepassen op de elementen die niet zijn geladen, moet u ervoor zorgen dat alle elementen expliciet zijn geselecteerd.
* Om naar activa te zoeken die niet de verplichte meta-gegevens bevatten, zie [ verplichte meta-gegevens ](#mandatorymetadata).
* Zoeken gebruikt alle metagegevensvelden. Een generieke zoekopdracht, zoals zoeken naar 12, retourneert doorgaans veel resultaten. Voor betere resultaten gebruikt u dubbele (geen enkele) aanhalingstekens of zorgt u ervoor dat het getal aangrenzend is aan een woord zonder speciaal teken (bijvoorbeeld `shoe12` ).
* Bij zoeken in volledige tekst kunnen operatoren zoals `-` en `^` worden gebruikt. Als u deze letters wilt doorzoeken als letterlijke tekenreeksen, plaatst u de zoekexpressie tussen dubbele aanhalingstekens. Gebruik bijvoorbeeld `"Notebook - Beauty"` in plaats van `Notebook - Beauty` .
* Als de onderzoeksresultaten teveel zijn, beperkt het [ werkingsgebied van onderzoek ](#scope) tot nul-binnen op de gewenste activa. Het werkt het beste als u een idee hebt van hoe u beter kunt zoeken naar de gewenste elementen, bijvoorbeeld een specifiek bestandstype, een specifieke locatie, specifieke metagegevens, enzovoort.

* **het Etiketteren**: De markeringen helpen u activa categoriseren die kunnen worden doorzocht en efficiënter gezocht. Tags helpen andere gebruikers en workflows de juiste taxonomie te geven. [!DNL Experience Manager] biedt methoden om elementen automatisch van tags te voorzien met behulp van kunstmatig intelligente services van Adobe Sensei die uw elementen steeds beter kunnen coderen met gebruik en training. Wanneer u naar elementen zoekt, wordt met de slimme tags rekening gehouden als de functie op uw account is ingeschakeld. Het werkt naast de ingebouwde zoekfunctionaliteit. Zie [ onderzoeksgedrag ](#searchbehavior). Om de orde te optimaliseren waarin de onderzoeksresultaten worden getoond, kunt u [ het onderzoek het rangschikken ](#searchrank) van een paar uitgezochte activa opvoeren.

* **het Indexeren**: Slechts worden de geïndexeerde meta-gegevens en de activa teruggekeerd in de onderzoeksresultaten. Voor betere dekking en betere prestaties, zorg behoorlijk indexeren en volg de beste praktijken. Zie [ indexerend ](#searchindex).

* Gebruik de eigenschap `excludedPath` in de Lucene-index om specifieke elementen uit te sluiten van zoekresultaten.

## Enkele voorbeelden ter illustratie van zoekopdrachten {#samples}

Gebruik dubbele aanhalingstekens rond trefwoorden om te zoeken naar elementen die de exacte woordgroep bevatten in de exacte volgorde die de gebruiker heeft opgegeven.

![ het gedrag van het Onderzoek met en zonder aanhalingstekens ](assets/search_with_quotes.gif)

*Cijfer: Het gedrag van het onderzoek met en zonder aanhalingstekens.*

**Onderzoek met asteriskvervanging**: Om het onderzoek te verbreden, gebruik een asterisk vóór of na het onderzoekswoord om het even welk aantal karakters aan te passen. Als u bijvoorbeeld zoekt naar tekst zonder sterretje, worden er geen elementen geretourneerd die een variatie van het woord bevatten (inclusief in de metagegevens). Een sterretje vervangt het gehele aantal tekens. Bijvoorbeeld:

* `run` retourneert elementen met trefwoord exact uitvoeren
* `run*` retourneert elementen met `running` , `run` , `runaway` , enzovoort.
* `*run` retourneert elementen met `outrun` , `rerun` , enzovoort.
* `*run*` retourneert alle mogelijke combinaties.

![ Illustrerend gebruik van asteriskvervanging in activaonderzoek gebruikend een voorbeeld ](assets/search_with_asterisk_run.gif)

*Cijfer: Het illustreren gebruik van asteriskvervanging in het onderzoek van Activa dat een voorbeeld gebruikt.*

**Onderzoek met vraagteken vervanging**: Om het onderzoek uit te breiden, gebruik één of meerdere &#39;?&#39; tekens die exact overeenkomen met het aantal tekens. In de volgende afbeelding, bijvoorbeeld:

* `run???` -query komt niet overeen met een element.

* `run????` -query komt overeen met het woord `running` met vier tekens na `run` .

* `??run` -query komt overeen met het woord `rerun` met twee tekens ervoor `run` .

![ Illustrerend gebruik van vraagteken vervanging in het onderzoek van Activa dat een voorbeeld gebruikt ](assets/search_with_questionmark_run.gif)

*Cijfer: Het illustreren gebruik van vraagteken vervanging in het onderzoek van Activa gebruikend een voorbeeld.*

**sluit een sleutelwoord** uit: Het streepje van het gebruik aan onderzoek naar activa die geen sleutelwoord bevatten. `running -shoe` -query retourneert bijvoorbeeld elementen die `running` bevatten, maar niet `shoe` . Op dezelfde manier retourneert `camp -night` -query elementen die `camp` maar niet `night` bevatten. De query `camp-night` retourneert elementen die zowel `camp` als `night` bevatten.

![ Gebruik van streepje om naar activa te zoeken die geen uitgesloten sleutelwoord ](assets/search_dash_exclude_keyword.gif) bevatten

*Cijfer: Gebruik van streepje aan onderzoek naar activa die geen uitgesloten sleutelwoord bevatten.*

## Configuratie- en beheertaken met betrekking tot zoekfunctionaliteit {#configadmin}

### Indexconfiguraties zoeken {#searchindex}

Asset Discovery is afhankelijk van indexering van de DAM-inhoud, inclusief de metagegevens. Snellere en nauwkeurige detectie van bedrijfsmiddelen is afhankelijk van geoptimaliseerde indexering en geschikte configuraties. Zie [ onderzoeksindex ](/help/assets/performance-tuning-guidelines.md#search-indexes), [ Oak vragen en het indexeren ](/help/sites-deploying/queries-and-indexing.md), en [ beste praktijken ](/help/sites-deploying/best-practices-for-queries-and-indexing.md).

Gebruik de eigenschap `excludedPath` in de Lucene-index om specifieke elementen uit te sluiten van zoekresultaten.

### Zoeken op visuele of gelijkenis {#configvisualsearch}

Bij visueel zoeken worden slimme tags gebruikt. Voer de volgende stappen uit nadat u de functionaliteit voor slimme tags hebt geconfigureerd.

1. Voeg in [!DNL Experience Manager] CRXDE in `/oak:index/lucene` -knooppunt de volgende eigenschappen en waarden toe en sla de wijzigingen op.

   * `costPerEntry` eigenschap van het type `Double` met de waarde `10` .
   * `costPerExecution` eigenschap van het type `Double` met de waarde `2` .
   * `refresh` eigenschap van het type `Boolean` met de waarde `true` .

   Deze configuratie staat onderzoeken van de aangewezen index toe.

1. Als u een Lucene-index wilt maken, maakt u in CRXDE op `/oak:index/damAssetLucene/indexRules/dam:Asset/properties` een knooppunt met de naam `imageFeatures` van type `nt-unstructured` . In `imageFeatures` node,

   * Voeg de eigenschap `name` van het type `String` toe met de waarde `jcr:content/metadata/imageFeatures/haystack0` .
   * Voeg `nodeScopeIndex` eigenschap van het type `Boolean` toe met de waarde van `true` .
   * Voeg `propertyIndex` eigenschap van het type `Boolean` toe met de waarde van `true` .
   * Voeg de eigenschap `useInSimilarity` van het type `Boolean` toe met de waarde `true` .

   Sla de wijzigingen op.

1. Open `/oak:index/damAssetLucene/indexRules/dam:Asset/properties/predictedTags` en voeg `similarityTags` eigenschap van het type `Boolean` toe met de waarde van `true` .
1. Pas slimme tags toe op de elementen in de [!DNL Experience Manager] -opslagplaats. Zie [ hoe te om slimme markeringen ](https://experienceleague.adobe.com/nl/docs/experience-manager-learn/assets/configuring/tagging#configuring) te vormen.
1. In CRXDE stelt u in het knooppunt `/oak-index/damAssetLucene` de eigenschap `reindex` in op `true` . Sla de wijzigingen op.
1. (Optioneel) Als u het zoekformulier hebt aangepast, kopieert u het knooppunt `/libs/settings/dam/search/facets/assets/jcr%3Acontent/items/similaritysearch` naar `/conf/global/settings/dam/search/facets/assets/jcr:content/items` . Sla de wijzigingen op.

Voor verwante informatie, zie [ slimme markeringen in Experience Manager ](https://experienceleague.adobe.com/nl/docs/experience-manager-learn/assets/metadata/image-smart-tags) begrijpen en [ hoe te om slimme markeringen ](/help/assets/enhanced-smart-tags.md) te beheren.

>[!CAUTION]
>
>Als de Lucene-indexering uit [!DNL Adobe Experience Manager] is uitgevoerd, werkt de zoekopdracht op basis van slimme tags niet zoals u had verwacht.

### Verplichte metagegevens {#mandatorymetadata}

Zakelijke gebruikers, beheerders of DAM-bibliotheken kunnen bepaalde metagegevens definiëren als verplichte metagegevens die nodig zijn om de bedrijfsprocessen te laten werken. Om verschillende redenen ontbreken deze metagegevens mogelijk bij sommige elementen, zoals oudere elementen of elementen die in bulk zijn gemigreerd. Assets met ontbrekende of ongeldige metagegevens wordt gedetecteerd en gerapporteerd op basis van de eigenschap voor geïndexeerde metagegevens. Om het te vormen, zie [ verplichte meta-gegevens ](/help/assets/metadata-schemas.md#define-mandatory-metadata).

### Zoekfacetten wijzigen {#searchfacets}

[!DNL Experience Manager Assets] biedt zoekfacetten waarmee u de zoekresultaten kunt filteren, zodat de zoekresultaten sneller worden gevonden. Het deelvenster Filters bevat standaard enkele standaardfacetten. Beheerders kunnen het deelvenster Filters aanpassen om de standaardfacetten te wijzigen met behulp van de ingebouwde voorspelling. [!DNL Experience Manager] biedt een goede verzameling ingebouwde voorspellingen en een editor om de facetten aan te passen. Zie [ onderzoeksfacetten ](/help/assets/search-facets.md).

### Tekst extraheren tijdens het uploaden van elementen {#extracttextupload}

U kunt [!DNL Experience Manager] zo configureren dat de tekst uit de elementen wordt gehaald wanneer gebruikers elementen uploaden, zoals PSD- of PDF-bestanden. [!DNL Experience Manager] indexeert de geëxtraheerde tekst en helpt gebruikers deze elementen te doorzoeken op basis van de geëxtraheerde tekst. Zie [ activa ](/help/assets/manage-assets.md#uploading-assets) uploaden.

Als de tekstextractie te hulpbronnenintensief wordt voor uw implementatie, kunt u de tekstextractie uitschakelen.

### Aangepaste voorspelling van filterzoekresultaten {#custompredicates}

Voorspellen worden gebruikt om facetten te maken. Beheerders kunnen de zoekfacetten in het deelvenster Filters aanpassen met behulp van vooraf geconfigureerde voorspellingen. Deze voorspelling kan worden aangepast met behulp van overlays. Zie [ tot douanevoorspelling ](/help/assets/searchx.md) leiden.

U kunt naar digitale elementen zoeken op basis van een of meer van de volgende eigenschappen. Filters die op sommige van deze eigenschappen van toepassing zijn, zijn standaard beschikbaar en sommige andere filters kunnen op maat worden gemaakt om op de andere eigenschappen toe te passen.

| Zoekveld | Waarden van eigenschappen zoeken |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------|
| MIME-typen | Afbeeldingen, Documenten, Multimedia, Archieven of Overige. |
| Laatst gewijzigd | Uur, Dag, Week, Maand of Jaar. |
| Bestandsgrootte | Klein, Medium of Groot |
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

## Werken met resultaten voor middelenzoekopdrachten {#aftersearch}

U kunt de volgende handelingen uitvoeren met de elementen die u hebt gezocht in [!DNL Experience Manager] :

* Eigenschappen van metagegevens en andere informatie weergeven.
* Download een of meer middelen.
* Gebruik Desktophandelingen om deze middelen in de bureaubladtoepassing te openen.
* Slimme verzamelingen maken.
* Een versie maken
* Een workflow starten
* Relatieve of ongerelateerde elementen
* Pas filters toe met behulp van het deelvenster Filters dat na het uitvoeren van de zoekopdracht automatisch wordt weergegeven om de zoekresultaten te beperken.

### Zoekresultaten sorteren {#sort}

U kunt zoekresultaten sorteren om sneller de vereiste elementen te vinden. U kunt de zoekresultaten alleen sorteren in de lijstweergave en als u **[[!UICONTROL Files]](#searchui)** in het deelvenster **[!UICONTROL Filters]** selecteert. [!DNL Assets] gebruikt sorteren op de server om snel alle elementen (hoe talrijk ook) in een map of resultaten van een zoekopdracht te sorteren. Sorteren op de server levert sneller en nauwkeuriger resultaten op dan sorteren op de client.

In de lijstweergave kunt u de zoekresultaten op dezelfde manier sorteren als elementen in een willekeurige map. Sorteren werkt op deze kolommen: Naam, Titel, Status, Dimensies, Grootte, Classificatie, Gebruik, Gemaakt, Gewijzigd, Gepubliceerd, Workflow en Uitgecheckt.

Voor beperkingen van soortfunctionaliteit, zie [ beperkingen ](#limitations).

### Gedetailleerde informatie over een element controleren {#checkinfo}

Op de pagina met zoekresultaten kunt u gedetailleerde informatie over een doorzocht element controleren.

Als u alle metagegevens van een element wilt weergeven, selecteert u het element en klikt u op **[!UICONTROL properties]** in de werkbalk.

Als u de opmerkingen over een element of de versiegeschiedenis van een element wilt controleren, klikt u op het element om een voorvertoning op grote grootte te openen. Open de tijdlijn in de linkertrack en selecteer **[!UICONTROL Comments]** of **[!UICONTROL Versions]** . U kunt de tijdlijnactiviteit zoals opmerkingen of versies ook in chronologische volgorde sorteren.

![ de chronologieingangen van de Soort voor een onderzoeksactiva ](assets/sort_timeline_search_results.gif)

*Cijfer: De chronologieingangen van de soort voor een onderzoeksactiva.*

### Gezochte middelen downloaden {#download}

U kunt de gezochte elementen en hun vertoningen downloaden enkel aangezien u regelmatige activa van omslagen downloadt. Selecteer een of meer elementen in de zoekresultaten en klik op **[!UICONTROL Download]** op de werkbalk.

### Eigenschappen van metagegevens voor bulkupdates {#metadataupdates}

Het is mogelijk om bulkupdates uit te voeren naar de algemene metagegevensvelden van meerdere elementen. Selecteer een of meer elementen in de zoekresultaten. Klik op **[!UICONTROL Properties]** op de werkbalk en werk de metagegevens naar wens bij. Klik op **[!UICONTROL Save and Close]** als u klaar bent. De eerder bestaande metagegevens in de bijgewerkte velden worden overschreven.

Voor de activa die in één enkele omslag of een inzameling beschikbaar zijn, is het gemakkelijker om [ de meta-gegevens in bulk ](/help/assets/metadata.md) bij te werken zonder de onderzoeksfunctionaliteit te gebruiken. Voor de elementen die beschikbaar zijn in verschillende mappen of voldoen aan een algemeen criterium, is het sneller om de metagegevens bulksgewijs bij te werken door te zoeken.

### Slimme verzamelingen {#smart-collections}

Een verzameling is een geordende set elementen die elementen van verschillende locaties kunnen bevatten, omdat verzamelingen alleen verwijzingen naar deze elementen bevatten. Verzamelingen zijn van de volgende twee typen:

* Een statische referentielijst met elementen, mappen en andere verzamelingen.
* Een dynamische lijst (slimme verzameling) die elementen in de verzameling vult op basis van zoekcriteria.

U kunt slimme verzamelingen maken op basis van de zoekcriteria. Selecteer in het deelvenster **[!UICONTROL Filters]** de optie **[!UICONTROL Files]** en klik op **[!UICONTROL Save Smart Collection]**. Zie [Verzamelingen beheren](/help/assets/manage-collections.md).

### Een versie maken {#create-version}

Maak een versie voor de elementen die in de zoekresultaten worden weergegeven. Selecteer het element en klik op **[!UICONTROL Create]** > **[!UICONTROL Version]** . Voeg een optioneel label of een opmerking toe en klik op **[!UICONTROL Create]** . U kunt ook meerdere elementen tegelijk selecteren en er versies voor maken.

### Een workflow maken {#create-workflow}

Net als bij de functie voor het maken van een versie kunt u ook een workflow maken voor de elementen die in de zoekresultaten worden weergegeven. Selecteer de elementen en klik op **[!UICONTROL Create]** > **[!UICONTROL Workflow]** . Selecteer het workflowmodel, geef een titel voor de workflow op en klik op **[!UICONTROL Start]** .

### Relatieve en niet-gerelateerde elementen {#relate-unrelate-assets}

Verwante en losse elementen die in de zoekresultaten worden weergegeven. Selecteer de elementen en klik op **[!UICONTROL Relate]** of **[!UICONTROL Unrelate]** .

## Onverwachte zoekresultaten en problemen {#unexpected-results}

| Fout, problemen, symptomen | Mogelijke reden | Mogelijke oplossing of begrip van het probleem |
|---|---|---|
| Onjuiste resultaten bij het zoeken naar elementen met ontbrekende metagegevens. | Bij het zoeken naar elementen waarvoor de verplichte metagegevens ontbreken, geeft [!DNL Experience Manager] mogelijk elementen weer met geldige metagegevens. De resultaten zijn gebaseerd op de eigenschap voor geïndexeerde metagegevens. | Nadat de metagegevens zijn bijgewerkt, moet de index opnieuw worden geïndexeerd om de juiste status van metagegevens voor elementen weer te geven. Zie [ verplichte meta-gegevens ](metadata-schemas.md#define-mandatory-metadata). |
| Te veel zoekresultaten. | Brede zoekparameter. | Overweeg het beperken van het [ werkingsgebied van onderzoek ](#scope). Het gebruik van slimme tags kan meer zoekresultaten opleveren dan u had verwacht. Zie [ onderzoeksgedrag met slimme markeringen ](#withsmarttags). |
| Onverwante of gedeeltelijk verwante zoekresultaten. | Wijzigingen in zoekgedrag met slimme tags. | Begrijp [ hoe het onderzoek na slim etiketteren ](#withsmarttags) verandert. |
| Geen suggesties voor automatisch aanvullen van elementen. | Nieuw geüploade elementen zijn nog niet geïndexeerd. De metagegevens zijn niet direct beschikbaar als suggesties wanneer u een trefwoord in de zoekbalk typt. | [!DNL Experience Manager] wacht tot een time-outperiode (standaard één uur) is verstreken voordat een achtergrondtaak wordt uitgevoerd om de metagegevens voor alle nieuw geüploade of bijgewerkte elementen te indexeren en voegt de metagegevens vervolgens toe aan de lijst met suggesties. |
| Geen zoekresultaten. | <ul><li>Assets die overeenkomt met uw query, bestaat niet. </li><li> Whitespace toegevoegd vóór de zoekquery. </li><li> Niet-ondersteund metagegevensveld bevat het trefwoord waarnaar u hebt gezocht.</li><li> Zoeken tijdens offline uitvoering van een element. </li></ul> | <ul><li>Zoeken met een ander trefwoord. U kunt ook slim labelen of zoeken op basis van gelijkenis gebruiken om de zoekresultaten te verbeteren. </li><li>[ Bekende beperking ](#limitations).</li><li>Niet alle metagegevensvelden worden in aanmerking genomen voor zoekopdrachten. Zie [ werkingsgebied ](#scope).</li><li>Later zoeken of on-time en off-time wijzigen voor de vereiste elementen.</li></ul> |
| Er is geen zoekfilter of voorspelling beschikbaar. | <ul><li>Het zoekfilter is niet geconfigureerd.</li><li>Het is niet beschikbaar voor uw aanmelding.</li><li>(Minder waarschijnlijk) De onderzoeksopties worden niet aangepast op de plaatsing die u gebruikt.</li></ul> | <ul><li>Neem contact op met de beheerder om te controleren of de zoekaanpassingen al dan niet beschikbaar zijn.</li><li>Neem contact op met de beheerder om te controleren of uw account de rechten/machtigingen heeft om de aanpassing te gebruiken.</li><li>Neem contact op met de beheerder en controleer de beschikbare aanpassingen voor de [!DNL Assets] -implementatie die u gebruikt.</li></ul> |
| Bij het zoeken naar visueel vergelijkbare afbeeldingen ontbreekt een verwachte afbeelding. | <ul><li>Afbeelding is niet beschikbaar in [!DNL Experience Manager] .</li><li>Afbeelding is niet geïndexeerd. Doorgaans wanneer het onlangs is geüpload.</li><li>Afbeelding heeft geen slimme tags.</li></ul> | <ul><li>Voeg de afbeelding toe aan [!DNL Assets] .</li><li>Neem contact op met de beheerder om de gegevensopslagruimte opnieuw te indexeren. Zorg er ook voor dat u de juiste index gebruikt.</li><li>Neem contact op met de beheerder om de relevante elementen een slimme tag te geven.</li></ul> |
| Bij het zoeken naar visueel vergelijkbare afbeeldingen wordt een irrelevante afbeelding weergegeven. | Visuele zoekfunctionaliteit. | In [!DNL Experience Manager] worden zoveel mogelijk relevante elementen weergegeven. Eventuele minder relevante afbeeldingen worden aan de resultaten toegevoegd, maar met een lagere zoekpositie. De kwaliteit van de overeenkomsten en de relevantie van de gezochte elementen nemen af wanneer u de zoekresultaten omlaag schuift. |
| Wanneer u zoekresultaten selecteert en gebruikt, wordt niet op alle gezochte elementen ingegaan. | Met de optie [!UICONTROL Select All] selecteert u alleen de eerste 100 zoekresultaten in de kaartweergave en de eerste 200 zoekresultaten in de lijstweergave. | |

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager]  gids van de onderzoeksimplementatie ](https://experienceleague.adobe.com/nl/docs/experience-manager-learn/sites/developing/search-tutorial-develop)
>* [ Geavanceerde configuratie om onderzoeksresultaten ](https://experienceleague.adobe.com/nl/docs/experience-manager-learn/assets/search-and-discovery/search-boost) op te voeren

