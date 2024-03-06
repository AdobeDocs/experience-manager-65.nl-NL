---
title: Digitale middelen en afbeeldingen zoeken in [!DNL Adobe Experience Manager]
description: Leer hoe u de vereiste middelen kunt vinden in [!DNL Adobe Experience Manager] met het deelvenster Filters en hoe u de elementen gebruikt die in de zoekopdracht worden weergegeven.
contentOwner: AG
mini-toc-levels: 1
feature: Search, Metadata
role: User
exl-id: 588433b2-564a-430f-9d04-480465ece2ad
hide: true
source-git-commit: 9d497413d0ca72f22712581cf7eda1413eb8d643
workflow-type: tm+mt
source-wordcount: '5593'
ht-degree: 3%

---

# Digitale middelen zoeken in [!DNL Adobe Experience Manager] {#search-assets-in-aem}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/search-assets.html?lang=en) |
| AEM 6,5 | Dit artikel |

[!DNL Adobe Experience Manager Assets] biedt robuuste methoden voor het detecteren van bedrijfsmiddelen die u helpen een hogere snelheid van de inhoud te bereiken. Uw teams kunnen tijd aan markt met naadloze, intelligente onderzoekservaring verminderen gebruikend out-of-the-box functionaliteit en douanemethodes. Het zoeken naar middelen is van cruciaal belang voor het gebruik van een systeem voor het beheer van digitale activa — of het nu gaat om verder gebruik door creatieve ondernemingen, voor een robuust beheer van activa door zakelijke gebruikers en marketeers, of voor beheer door DAM-beheerders. Eenvoudige, geavanceerde en aangepaste zoekopdrachten die u kunt uitvoeren via [!DNL Assets] In deze gebruiksgevallen kunt u met gebruikersinterface of andere apps en oppervlakken gemakkelijker aan de slag gaan.

[!DNL Experience Manager Assets] steunt de volgende gebruiksgevallen en dit artikel beschrijft het gebruik, de concepten, de configuraties, de beperkingen, en het oplossen van problemen voor deze gebruiksgevallen.

| Middelen zoeken | Zoekfuncties configureren en beheren | Werken met zoekresultaten |
|---|---|---|
| [Standaardzoekopdrachten](#searchbasics) | [Zoekindex](#searchindex) | [Resultaten sorteren](#sort) |
| [Gebruiksinterface voor zoeken begrijpen](#searchui) | [Zoeken op visuele of gelijkenis](#configvisualsearch) | [Eigenschappen en metagegevens van een element controleren](#checkinfo) |
| [Zoeken in suggesties](#searchsuggestions) | [Verplichte metagegevens](#mandatorymetadata) | [Downloaden](#download) |
| [Zoekresultaten en gedrag begrijpen](#searchbehavior) | [Zoekfacetten wijzigen](#searchfacets) | [Bulkupdates van metagegevens](#metadataupdates) |
| [Zoeken in rang en opvoeren](#searchrank) | [Tekst extraheren](#extracttextupload) | [Slimme verzamelingen](#collections) |
| [Geavanceerd zoeken: filteren en zoekbereik](#scope) | [Aangepaste voorspelling](#custompredicates) | [Onverwachte resultaten begrijpen en problemen oplossen](#unexpected-results) |
| [Zoeken in andere oplossingen en toepassingen](#search-assets-other-surfaces):<ul><li>[Adobe-itemkoppeling](#aal)</li><li>[Brand Portal](#brand-portal)</li><li>[Experience Manager-bureaubladtoepassing](#desktop-app)</li><li>[Adobe Stock-afbeeldingen](#adobe-stock)</li><li>[Dynamic Media-middelen](#dynamic-media)</li></ul> | | |
| [Elementkiezer](#asset-picker) | | |
| [Beperkingen](#limitations) en [Tips](#tips) | | |
| [Afbeeldingsvoorbeelden](#samples) | | |

Digitale middelen zoeken met behulp van het veld Onderzoek boven aan het dialoogvenster [!DNL Experience Manager] webinterface. Ga naar **[!UICONTROL Assets]** > **[!UICONTROL Files]** in [!DNL Experience Manager], klikt u op ![search_icon](assets/do-not-localize/search_icon.png) Voer in de bovenste balk het trefwoord Zoeken in en selecteer `Return`. U kunt ook de trefwoordsneltoets gebruiken `/` (slash) om het veld Onderzoek te openen. `Location:Assets` is vooraf geselecteerd om de zoekopdrachten te beperken tot DAM-middelen. [!DNL Experience Manager] biedt suggesties als u begint met het typen van een trefwoord voor zoeken.

Gebruik de **[!UICONTROL Filters]** om te zoeken naar elementen, mappen, tags en metagegevens. U kunt zoekresultaten filteren op basis van de verschillende opties (voorspelling), zoals bestandstype, bestandsgrootte, datum van laatste wijziging, status van element, gegevens over inzichten en Adobe Stock-licenties. U kunt het deelvenster Filters aanpassen en voorvertoningen van zoekopdrachten toevoegen of verwijderen met behulp van [zoekfacetten](/help/assets/search-facets.md). De [!UICONTROL File Type] filter in de [!UICONTROL Filters] heeft selectievakjes met gemengde status. Tenzij u alle geneste voorspellen (of indelingen) selecteert, worden de selectievakjes op het eerste niveau daarom gedeeltelijk gecontroleerd.

[!DNL Experience Manager] zoekmogelijkheden bieden ondersteuning voor het zoeken naar verzamelingen en het zoeken naar elementen in een verzameling. Zie [zoekverzamelingen](/help/assets/manage-collections.md).

## Zoekinterface begrijpen {#searchui}

Verken uzelf met de zoekinterface en de beschikbare acties.

![Experience Manager Assets-interface voor zoekresultaten begrijpen](assets/aem_search_results.png)

*Afbeelding: Begrijpen [!DNL Experience Manager Assets] zoekresultateninterface.*

**A.** Sla de zoekopdracht op als een slimme verzameling. **B.** Hiermee kunt u de zoekresultaten beperken door filters of voorspelling in te stellen. **C.** Bestanden, mappen of beide weergeven. **D.** Klik op Filters om het linkerspoor te openen of te sluiten. **E.** Zoeklocatie is DAM. **F.** Het gebied van het onderzoek met user-provided onderzoekssleutelwoord. **G.** Selecteer de geladen zoekresultaten. **H.** Aantal weergegeven zoekresultaten van de totale zoekresultaten. **I.** Zoekopdracht sluiten. **J.** Schakel tussen de kaartweergave en de lijstweergave.

### Dynamische zoekfacetten {#dynamicfacets}

U kunt de gewenste elementen sneller vinden op de pagina met zoekresultaten met behulp van het dynamisch bijgewerkte aantal verwachte zoekresultaten in de zoekfacetten. Het verwachte aantal elementen wordt bijgewerkt, zelfs voordat het zoekfilter wordt toegepast. Door het verwachte aantal op het filter te zien, kunt u snel en efficiënt door de zoekresultaten navigeren.

![Zie het geschatte aantal elementen zonder de zoekresultaten te filteren in zoekfacetten.](assets/asset_search_results_in_facets_filters.png)

*Figuur: Zie het benaderende aantal activa zonder het filtreren onderzoeksresultaten in onderzoeksfacetten.*

## Zoekresultaten en gedrag begrijpen {#searchbehavior}

### Standaardzoektermen en -resultaten {#searchbasics}

U kunt trefwoordzoekopdrachten uitvoeren vanuit het veld UniverseelZoeken. De trefwoordzoekopdracht is niet hoofdlettergevoelig en bestaat uit een zoekopdracht in volledige tekst (in de veelgebruikte metagegevensvelden). Als meer dan één sleutelwoord wordt gebruikt, `AND` is de standaardoperator tussen de trefwoorden.

De resultaten worden gesorteerd op relevantie, te beginnen met de dichtstbijzijnde overeenkomsten. Voor meerdere trefwoorden zijn relevantere resultaten de elementen die beide termen in de metagegevens bevatten. Trefwoorden die in de metagegevens voorkomen, krijgen een hogere positie dan trefwoorden die in andere metagegevensvelden worden weergegeven. [!DNL Experience Manager] maakt het mogelijk een bepaalde zoekterm een hoger gewicht te geven. Ook is het mogelijk om [de rangorde verhogen](#searchrank) van een paar doelactiva voor specifieke onderzoekstermijnen.

Om de relevante activa snel te vinden, verstrekt de rijke interface het filtreren, het sorteren, en selectiemechanismen. U kunt resultaten filteren op basis van meerdere criteria en het aantal gezochte elementen voor verschillende filters bekijken. U kunt de zoekopdracht ook opnieuw uitvoeren door de query in het veld Onderzoek te wijzigen. Wanneer u de zoektermen of filters wijzigt, blijven de andere filters van toepassing om de context van de zoekopdracht te behouden.

Wanneer de resultaten veel elementen zijn, [!DNL Experience Manager] geeft de eerste 100 weer in de kaartweergave en 200 in de lijstweergave. Wanneer gebruikers schuiven, worden meer elementen geladen. Dit is om de prestaties te verbeteren. Bekijk een videodemonstratie van de [aantal weergegeven elementen](https://www.youtube.com/watch?v=LcrGPDLDf4o).

Het kan voorkomen dat de zoekresultaten een aantal onverwachte elementen bevatten. Zie voor meer informatie [onverwachte resultaten](#unexpected-results).

[!DNL Experience Manager] U kunt naar vele dossierformaten zoeken en de onderzoeksfilters kunnen worden aangepast aan uw bedrijfsvereisten. Neem contact op met uw beheerder om te weten welke zoekopties beschikbaar worden gesteld voor uw DAM-opslagplaats en welke beperkingen uw account heeft.

### Resultaten met en zonder verbeterde slimme tags {#withsmarttags}

Standaard, [!DNL Experience Manager] de zoektermen worden gecombineerd met een AND-component. Kijk bijvoorbeeld eens naar het doorzoeken van trefwoordenvrouwen. In de zoekresultaten worden standaard alleen de elementen weergegeven met trefwoorden voor vrouwen en het gebruik van trefwoorden in de metagegevens. Hetzelfde gedrag blijft behouden wanneer speciale tekens (punten, onderstrepingstekens of streepjes) bij de trefwoorden worden gebruikt. De volgende zoekopdrachten retourneren dezelfde resultaten:

* `woman running`
* `woman.running`
* `woman-running`

De query `woman -running` retourneert elementen zonder `running` in hun metagegevens.
Als u Slimme tags gebruikt, wordt een extra `OR` om een zoekterm te zoeken als de toegepaste slimme tags. Een middel gelabeld met of `woman` of `running` het gebruik van slimme tags wordt ook weergegeven in een dergelijke zoekopdracht. De zoekresultaten zijn dus een combinatie van:

* Middelen met `woman` en `running` trefwoorden in de metagegevens (standaardgedrag).

* Elementen die zijn gelabeld met een van de trefwoorden (gedrag Slimme tags).

### Suggesties zoeken terwijl u typt {#searchsuggestions}

Wanneer u trefwoorden begint te typen, [!DNL Experience Manager] stelt de mogelijke zoektrefwoorden of -woordgroepen voor. De suggesties zijn gebaseerd op de metagegevens van de bestaande elementen. [!DNL Experience Manager] Hiermee worden alle metagegevensvelden geïndexeerd, zodat u deze gemakkelijker kunt gebruiken bij het zoeken. Voor zoeksuggesties gebruikt het systeem de waarden van de volgende paar metagegevensvelden. Als u zoeksuggesties wilt doen, kunt u de volgende velden vullen met de juiste trefwoorden:

* Elementlabels. (afbeeldingen `jcr:content/metadata/cq:tags`)
* Titel van element. (afbeeldingen `jcr:content/metadata/dc:title`)
* Beschrijving van element. (afbeeldingen `jcr:content/metadata/dc:description`)
* Titel in de gegevensopslagruimte van het JCR. De waarde wordt mogelijk toegewezen aan de titel van het element. (afbeeldingen `jcr:content/jcr:title`)
* Beschrijving in de gegevensopslagruimte van de JCR. De waarde wordt mogelijk toegewezen aan de beschrijving van het element. (afbeeldingen `jcr:content/jcr:description`)

Als u suggesties voor meerdere zoektrefwoorden wilt ontvangen, blijft u alle trefwoorden typen zonder een suggestie voor één trefwoord te selecteren.

![Typ meerdere trefwoorden om suggesties weer te geven die in alle trefwoorden passen](assets/search_suggestionsmanykeywords.gif)

*Figuur: Typ veelvoudige sleutelwoorden om suggesties te bekijken die hen allen passen.*

### Rangschikking en boosting zoeken {#searchrank}

De zoekresultaten die overeenkomen met alle zoektermen in metagegevensvelden worden eerst weergegeven, gevolgd door de zoekresultaten die overeenkomen met een van de zoektermen in de slimme tags. In het bovenstaande voorbeeld is de weergavevolgorde van zoekresultaten bij benadering:

1. Komt overeen met `woman running` in de verschillende metagegevensvelden.
1. Komt overeen met `woman running` in slimme tags.
1. Komt overeen met `woman` of van `running` in slimme tags.

U kunt de relevantie van trefwoorden voor bepaalde elementen verbeteren om zoekopdrachten op basis van trefwoorden te stimuleren. Met andere woorden, de afbeeldingen waarvoor u specifieke trefwoorden promoot, worden boven aan de zoekresultaten weergegeven wanneer u op basis van deze trefwoorden zoekt.

1. Van de [!DNL Assets] gebruikersinterface, opent u de eigenschappenpagina voor het element. Klikken **[!UICONTROL Advanced]** en klik op **[!UICONTROL Add]** krachtens **[!UICONTROL Elevate for search keywords]**.
1. In de **[!UICONTROL Search Promote]** geeft u een trefwoord op waarvoor u de zoekopdracht naar de afbeelding wilt opvoeren en klikt u vervolgens op **[!UICONTROL Add]**. U kunt meerdere trefwoorden op dezelfde manier opgeven.
1. Klik op **[!UICONTROL Save & Close]**. Het element dat u voor dit trefwoord hebt gepromoot, wordt weergegeven in de beste zoekresultaten.

U kunt dit in uw voordeel gebruiken door de positie van bepaalde elementen in de zoekresultaten voor het doeltrefwoord te verhogen. Zie de onderstaande voorbeeldvideo. Zie voor meer informatie [zoeken in [!DNL Experience Manager]](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/search-and-discovery/search-boost.html).

>[!VIDEO](https://video.tv.adobe.com/v/16766/?quality=6)

*Video: begrijp hoe zoekresultaten worden gerangschikt en hoe de rang kan worden beïnvloed.*

## Geavanceerd zoeken {#scope}

[!DNL Experience Manager] biedt verschillende methoden, zoals filters die van toepassing zijn op de gezochte elementen, zodat u de gewenste elementen sneller kunt vinden. Hieronder worden enkele veelgebruikte methoden beschreven. Sommige [geïllustreerde voorbeelden](#samples) worden hieronder gedeeld.

**Bestanden of mappen zoeken**: Zie bestanden, mappen of beide in de zoekresultaten. Van **[!UICONTROL Filters]** kunt u de juiste optie selecteren. Zie [zoekinterface](#searchui).

**Middelen in een map zoeken**: U kunt de zoekopdracht beperken tot een specifieke map. In de **[!UICONTROL Filters]** , voegt u het pad van een map toe. U kunt slechts één map tegelijk selecteren.

![Zoekresultaten beperken tot een map door een mappad toe te voegen in het deelvenster Filters](assets/search_folder_select.gif)

*Afbeelding: Beperk de zoekresultaten tot een map door een mappad toe te voegen in het deelvenster Filters.*

### Vergelijkbare afbeeldingen zoeken {#visualsearch}

Als u afbeeldingen wilt zoeken die visueel lijken op een door de gebruiker geselecteerde afbeelding, klikt u op de optie **[!UICONTROL Find Similar]** in de kaartweergave van een afbeelding of op de werkbalk. [!DNL Experience Manager] geeft de slimme getagde afbeeldingen uit de DAM-opslagplaats weer die lijken op een door de gebruiker geselecteerde afbeelding. Zie [Zoeken naar overeenkomsten configureren](#configvisualsearch).

![Vergelijkbare afbeeldingen zoeken met de optie in de kaartweergave](assets/search_find_similar.png)

*Afbeelding: vergelijkbare afbeeldingen zoeken met de optie in de kaartweergave.*

### Adobe Stock-afbeeldingen {#adobe-stock}

Van binnen [!DNL Experience Manager] gebruikersinterface, gebruikers kunnen zoeken [Adobe Stock-middelen](/help/assets/aem-assets-adobe-stock.md) en de vereiste activa in licentie geven. Toevoegen `Location: Adobe Stock` in de balk Onderzoek. U kunt ook het deelvenster Filters gebruiken om alle middelen te zoeken waarvoor een licentie is verleend of om een bepaald element te zoeken aan de hand van het Adobe Stock-bestandsnummer.

### Dynamic Media-middelen {#dmassets}

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
| Copyrighteigenaar | copyrightowner:&quot;Adobe Systems&quot; |
| Medewerker | contribuant:John |
| Gebruiksvoorwaarden | usageterms:&quot;CopyRights Reserved&quot; |
| Gemaakt | gemaakt:YYYY-MM-DDTHH |
| Vervaldatum | verloopt:YYYY-MM-DDTHH |
| Op tijd | ontime:YYYY-MM-DDTHH |
| Uit-tijd | offtime:YYYY-MM-DDTHH |
| Tijdsbereik (verloopt dateontime, offtime) | facet field : lowerbound..bovenaan |
| Pad | /content/dam/&lt;folder name=&quot;&quot;> |
| PDF-titel | pdftitle:&quot;Document Adoben&quot; |
| Onderwerp | onderwerp: &quot;Opleiding&quot; |
| Tags | tags:&quot;Locatie en reizen&quot; |
| Type | type:&quot;image\png&quot; |
| Breedte van afbeelding | breedte:ondergrens..bovenaan |
| Hoogte van afbeelding | hoogte:ondergrens..bovenaan |
| Persoon | persoon:John |

De eigenschappen `path`, `limit`, `size`, en `orderby` kan niet worden gecombineerd `OR` met een andere eigenschap.

<!-- TBD: Where are the limit, size, orderby properties defined?
-->

Het sleutelwoord voor een user-generated bezit is zijn gebiedsetiket in de bezitsredacteur in kleine letters, met verwijderde ruimten.

Hier volgen enkele voorbeelden van zoekindelingen voor complexe query&#39;s:

* Alle elementen weergeven met meerdere facetvelden (bijvoorbeeld: title=Jan Smit en creator tool = Adobe Photoshop): `title:"John Doe" creatortool:Adobe*`
* Om alle activa te tonen wanneer de facetwaarde niet één enkel woord maar een zin (bijvoorbeeld: title=Scott Reynolds) is: `title:"Scott Reynolds"`
* Elementen weergeven met meerdere waarden van één eigenschap (bijvoorbeeld: title=Scott Reynolds of Jan Smit): `title:"Scott Reynolds" OR "John Doe"`
* Elementen weergeven waarvan de eigenschapswaarden beginnen met een specifieke tekenreeks (bijvoorbeeld: title is Scott Reynolds): `title:Scott*`
* Elementen weergeven met eigenschapswaarden die eindigen met een specifieke tekenreeks (bijvoorbeeld: title is Scott Reynolds): `title:*Reynolds`
* Elementen weergeven met een eigenschapswaarde die een specifieke tekenreeks bevat (bijvoorbeeld: title = Basel Meeting Room): `title:*Meeting*`
* Elementen weergeven die een bepaalde tekenreeks bevatten en een specifieke eigenschapswaarde hebben (bijvoorbeeld: zoeken naar Adobe van tekenreeks in elementen met de naam title=Jan Smit): `*Adobe* title:"John Doe"`

## Digitale middelen zoeken vanuit andere bronnen [!DNL Experience Manager] aanbiedingen of interfaces {#search-assets-other-surfaces}

[!DNL Adobe Experience Manager] maakt verbinding met DAM-opslagplaats met verschillende andere [!DNL Experience Manager] oplossingen om snellere toegang tot digitale middelen te bieden en de creatieve workflows te stroomlijnen. Elke detectie van middelen begint met bladeren of zoeken. Het zoekgedrag blijft grotendeels hetzelfde op de verschillende oppervlakken en oplossingen. Sommige zoekmethoden veranderen als doelpubliek, de gebruiksgevallen en de gebruikersinterface. Dit kan per doelgroep en gebruikersinterface verschillen. [!DNL Experience Manager] oplossingen. De specifieke methoden worden gedocumenteerd voor de afzonderlijke oplossingen in de onderstaande koppelingen. De algemeen toepasselijke tips en gedragingen worden in dit artikel beschreven.

### Digitale elementen zoeken vanuit het deelvenster Adobe Asset Link {#aal}

Met Adobe Asset Link hebben creatieve professionals nu toegang tot inhoud die is opgeslagen in [!DNL Experience Manager Assets], zonder de ondersteunde Adobe Creative Cloud-apps te verlaten. Met het deelvenster in de app in het [!DNL Adobe Creative Cloud] apps: [!DNL Adobe Photoshop], [!DNL Adobe Illustrator], en [!DNL Adobe InDesign]. Met Asset Link kunnen gebruikers ook visueel vergelijkbare resultaten zoeken. De resultaten van de visuele zoekopdrachten worden aangedreven door instructiealgoritmen van Adobe Sensei-computers en helpen gebruikers bij het zoeken naar beelden die er in esthetisch opzicht op lijken. Zie [elementen zoeken en doorbladeren](https://helpx.adobe.com/enterprise/using/manage-assets-using-adobe-asset-link.html#UseAdobeAssetLink) het gebruiken van de Verbinding van Activa van de Adobe.

### Digitale middelen zoeken in [!DNL Experience Manager] bureaubladtoepassing {#desktop-app}

Creatieve professionals gebruiken de desktop-app om de [!DNL Experience Manager Assets] gemakkelijk doorzoekbaar en beschikbaar op hun lokale bureaublad (Win of Mac). Creative Cloud kan de gewenste middelen eenvoudig weergeven in Mac Finder of Windows Verkenner, geopend in bureaubladtoepassingen en lokaal gewijzigd - de wijzigingen worden opgeslagen in [!DNL Experience Manager] met een nieuwe versie die in de repository is gemaakt. De toepassing ondersteunt standaardzoekopdrachten met een of meer trefwoorden. `*` en `?` jokertekens, en `AND` operator. Zie [elementen zoeken, zoeken en voorvertonen](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#browse-search-preview-assets) in bureaubladtoepassing.

### Digitale middelen zoeken in [!DNL Brand Portal] {#brand-portal}

Line-of-business gebruikers en marketers gebruiken Brand Portal om de goedgekeurde digitale middelen efficiënt en veilig te delen met hun uitgebreide interne teams, partners en wederverkopers. Zie [zoekmiddelen op Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/search-capabilities/brand-portal-searching.html).

### Zoeken [!DNL Adobe Stock] afbeeldingen {#adobe-stock1}

Van binnen [!DNL Experience Manager] gebruikersinterface kunnen gebruikers zoeken in Adobe Stock-middelen en een licentie voor de vereiste middelen aanschaffen. Toevoegen `Location: Adobe Stock` op het gebied van het onderzoek. U kunt ook **[!UICONTROL Filters]** om alle gelicentieerde of niet-gelicentieerde middelen te zoeken of een bepaald middel te zoeken met Adobe Stock-bestandsnummer. Zie [beheren [!DNL Adobe Stock] afbeeldingen in [!DNL Experience Manager]](/help/assets/aem-assets-adobe-stock.md#usemanage).

### Zoeken [!DNL Dynamic Media] elementen {#dynamic-media}

U kunt filteren op dynamische media-afbeeldingen door **[!UICONTROL Dynamic Media]** > **[!UICONTROL Sets]** te selecteren in het deelvenster **[!UICONTROL Filters]**. Het filtert op en toont assets zoals afbeeldingsets, carrousels, gemengde mediasets, en spinsets. Tijdens het ontwerpen van webpagina&#39;s kunnen auteurs naar sets zoeken in de Inhoudszoeker. Een filter voor sets is beschikbaar in een pop-upmenu.

### Digitale middelen zoeken in de Inhoudszoeker bij het ontwerpen van webpagina&#39;s {#content-finder}

Auteurs kunnen de Inhoudszoeker gebruiken om in de DAM-opslagplaats te zoeken naar de relevante elementen en de elementen te gebruiken op de webpagina&#39;s die ze maken. Auteurs kunnen ook de functie Verbonden elementen gebruiken om te zoeken naar elementen die op een externe server beschikbaar zijn [!DNL Experience Manager] implementatie. Auteurs kunnen deze elementen vervolgens gebruiken in webpagina&#39;s op een lokale [!DNL Experience Manager] implementatie. Zie [externe elementen gebruiken](/help/assets/use-assets-across-connected-assets-instances.md#use-remote-assets).

### Verzamelingen zoeken {#collections}

[!DNL Experience Manager] zoekmogelijkheden bieden ondersteuning voor het zoeken naar verzamelingen en het zoeken naar elementen in een verzameling. Zie [zoekverzamelingen](/help/assets/manage-collections.md).

## Elementkiezer {#asset-picker}

>[!NOTE]
>
>Elementkiezer is aangeroepen [middelenkiezer](https://helpx.adobe.com/experience-manager/6-2/assets/using/asset-picker.html) in eerdere versies van [!DNL Adobe Experience Manager].

Met de functie Asset Selector kunt u de DAM-middelen op een speciale manier zoeken, filteren en doorbladeren. Asset Selector is beschikbaar op `https://[aem_server]:[port]/aem/assetpicker.html`. U kunt de metagegevens ophalen van elementen die u selecteert met de elementkiezer. U kunt de toepassing starten met ondersteunde aanvraagparameters, zoals het type element (afbeelding, video, tekst) en de selectiemodus (enkele of meerdere selecties). Deze parameters stellen de context van de elementenkiezer voor een bepaalde zoekinstantie in en blijven tijdens de selectie intact.

De elementkiezer gebruikt de HTML5 `Window.postMessage` bericht om gegevens voor het geselecteerde element naar de ontvanger te verzenden. Deze functie werkt alleen in de modus Bladeren en alleen met de resultatenpagina van Omnsearch.

Geef de volgende aanvraagparameters in een URL door om de elementenkiezer in een bepaalde context te starten:

| Naam | Waarden | Voorbeeld | Doel |
|---|---|---|---|
| bronachtervoegsel (B) | Mappad als resix van de bron in de URL: [https://localhost:4502/aem/assetpicker.html/&lt;folder_path>](https://localhost:4502/aem/assetpicker.html) | De elementenkiezer starten terwijl een bepaalde map is geselecteerd, bijvoorbeeld met de map `/content/dam/we-retail/en/activities` geselecteerd is, moet de URL de volgende vorm hebben: `https://localhost:4502/aem/assetpicker.html/content/dam/we-retail/en/activities?assettype=images` | Als u wilt dat een bepaalde map wordt geselecteerd wanneer de elementenkiezer wordt gestart, geeft u deze door als een bronachtervoegsel. |
| `mode` | enkelvoudig, meerdere | <ul><li>`https://localhost:4502/aem/assetpicker.html?mode=single`</li><li>`https://localhost:4502/aem/assetpicker.html?mode=multiple`</li></ul> | In meerdere modi kunt u meerdere elementen tegelijk selecteren met de elementkiezer. |
| `dialog` | true, false | [https://localhost:4502/aem/assetpicker.html?dialog=true](https://localhost:4502/aem/assetpicker.html?dialog=true) | Gebruik deze parameters om de elementenkiezer te openen als granietdialoogvenster. Deze optie is alleen van toepassing wanneer u de elementenkiezer start via Granite Path Field en deze configureert als pickerSrc URL. |
| `root` | &lt;folder_path> | `https://localhost:4502/aem/assetpicker.html?assettype=images&root=/content/dam/we-retail/en/activities` | Gebruik deze optie om de hoofdmap voor de elementenkiezer op te geven. In dit geval kunt u met de elementenkiezer alleen onderliggende elementen (direct/indirect) in de hoofdmap selecteren. |
| `viewmode` | zoeken | | U kunt de elementkiezer in de zoekmodus starten met `assettype` en `mimetype` parameters. |
| `assettype` | Afbeeldingen, documenten, multimedia, archieven. | <ul><li>`https://localhost:4502/aem/assetpicker.html?viewmode=search&assettype=images`</li><li> `https://localhost:4502/aem/assetpicker.html?viewmode=search&assettype=documents` </li><li> `https://localhost:4502/aem/assetpicker.html?viewmode=search&assettype=multimedia` </li><li> `https://localhost:4502/aem/assetpicker.html?viewmode=search&assettype=archives` </li></ul> | Gebruik de optie om elementtypen te filteren op basis van de opgegeven waarde. |
| `mimetype` | MIME-type (`/jcr:content/metadata/dc:format`) van een element (jokerteken wordt ook ondersteund). | <ul><li>`https://localhost:4502/aem/assetpicker.html?mimetype=image/png`</li><li>`https://localhost:4502/aem/assetpicker.html?mimetype=*png`</li><li>`https://localhost:4502/aem/assetpicker.html?mimetype=*presentation`</li><li>`https://localhost:4502/aem/assetpicker.html?mimetype=*presentation&mimetype=*png`</li></ul> | Gebruik deze optie om elementen te filteren op basis van het MIME-type. |

Ga naar `https://[aem_server]:[port]/aem/assetpicker`. Navigeer naar de gewenste map en selecteer een of meer elementen. U kunt ook naar het gewenste element zoeken in het vak Zoeken, naar wens een filter toepassen en het vervolgens selecteren.

![Door element bladeren en dit selecteren in de elementenkiezer](assets/assetpicker.png)

*Afbeelding: Blader door elementen en selecteer deze in de elementenkiezer.*

## Beperkingen {#limitations}

De zoekfunctie in [!DNL Experience Manager Assets] heeft de volgende beperkingen:

* Geef geen regelafstand op in de zoekopdracht als de zoekopdracht anders niet werkt.
* [!DNL Experience Manager] Mogelijk blijft de zoekterm zichtbaar nadat u eigenschappen van een element hebt geselecteerd in de gezochte resultaten en vervolgens de zoekopdracht hebt geannuleerd. <!-- (CQ-4273540) -->
* Wanneer u naar mappen of bestanden en mappen zoekt, kunnen de zoekresultaten op geen enkele parameter worden gesorteerd.
* Als u `Return` zonder tekst te typen op de balk Zoeken, [!DNL Experience Manager] Hiermee wordt een lijst geretourneerd met alleen bestanden en niet mappen. Als u specifiek naar mappen zoekt zonder een trefwoord te gebruiken, [!DNL Experience Manager] retourneert geen resultaten.
* U kunt zoeken in volledige tekst op mappen. Geef een zoekterm op die de zoekopdracht moet gebruiken.

Het visuele onderzoek of het gelijkenis onderzoek heeft de volgende beperkingen:

* Het visuele onderzoek werkt het best met een grote bewaarplaats. Hoewel er geen minimaal aantal afbeeldingen vereist is voor goede resultaten, is de kwaliteit van overeenkomsten met een paar afbeeldingen minder goed dan de overeenkomsten met een grote opslagplaats.
* U kunt het model of de trein niet wijzigen [!DNL Experience Manager] om vergelijkbare afbeeldingen te zoeken. Als u bijvoorbeeld slimme tags toevoegt of verwijdert aan een paar elementen, verandert het model niet. De elementen worden wel uitgesloten van de visueel vergelijkbare zoekresultaten.

De zoekfunctionaliteit kan prestatiebeperkingen hebben in de volgende scenario&#39;s:

* De kaartweergave heeft een snellere laadtijd dan de lijstweergave om de zoekresultaten weer te geven.

## Zoektips {#tips}

* Gebruik bij het controleren van de revisiestatus van de middelen de juiste optie om te bepalen welke middelen zijn goedgekeurd of welke activa nog moeten worden goedgekeurd.
* Gebruik de Insights-voorspelling om te zoeken naar ondersteunde middelen op basis van de gebruiksstatistieken die zijn verkregen van verschillende Creative-apps. Gebruiksgegevens worden gegroepeerd onder Gebruiksscore, Impressies, Klikken en Mediakanalen waar de elementen categorieën weergeven.
* Gebruik de **[!UICONTROL Select All]** Schakel het selectievakje in om de gezochte elementen te selecteren. [!DNL Experience Manager] In eerste instantie worden 100 elementen weergegeven in de kaartweergave en 200 elementen in de lijstweergave. Er worden meer elementen geladen wanneer u door de zoekresultaten schuift. U kunt meer elementen selecteren dan de geladen elementen. Het aantal geselecteerde elementen wordt in de rechterbovenhoek van de pagina met zoekresultaten weergegeven. U kunt de selectie bijvoorbeeld activeren door de geselecteerde elementen te downloaden, de eigenschappen van metagegevens voor de geselecteerde elementen bulksgewijs bij te werken of de geselecteerde elementen aan een verzameling toe te voegen. Wanneer er meer elementen zijn geselecteerd dan worden weergegeven, wordt een actie toegepast op alle geselecteerde elementen of wordt in een dialoogvenster het aantal elementen weergegeven waarop de actie wordt toegepast. Als u een handeling wilt toepassen op de elementen die niet zijn geladen, moet u ervoor zorgen dat alle elementen expliciet zijn geselecteerd.
* Als u wilt zoeken naar elementen die de verplichte metagegevens niet bevatten, raadpleegt u [verplichte metagegevens](#mandatorymetadata).
* Zoeken gebruikt alle metagegevensvelden. Een generieke zoekopdracht, zoals zoeken naar 12, retourneert doorgaans veel resultaten. Voor betere resultaten gebruikt u dubbele (geen enkele) aanhalingstekens of zorgt u ervoor dat het getal aangrenzend is aan een woord zonder speciaal teken (bijvoorbeeld `shoe12`).
* Bij zoeken in volledige tekst worden operatoren zoals `-` en `^`. Als u deze letters wilt doorzoeken als letterlijke tekenreeksen, plaatst u de zoekexpressie tussen dubbele aanhalingstekens. Gebruik bijvoorbeeld `"Notebook - Beauty"` in plaats van `Notebook - Beauty`.
* Als de zoekresultaten te veel zijn, beperkt u de instelling [zoekopdracht](#scope) naar nul-in op de gewenste activa. Het werkt het beste als u een idee hebt van hoe u beter kunt zoeken naar de gewenste elementen, bijvoorbeeld een specifiek bestandstype, een specifieke locatie, specifieke metagegevens, enzovoort.

* **Tags**: Met tags kunt u elementen categoriseren waarin u efficiënter kunt bladeren en zoeken. Tags helpen andere gebruikers en workflows de juiste taxonomie te geven. [!DNL Experience Manager] biedt methoden om elementen automatisch te labelen met behulp van kunstmatig intelligente services van Adobe Sensei die uw elementen steeds beter kunnen coderen met gebruik en training. Wanneer u naar elementen zoekt, wordt met de slimme tags rekening gehouden als de functie op uw account is ingeschakeld. Het werkt naast de ingebouwde zoekfunctionaliteit. Zie [zoekgedrag](#searchbehavior). Als u de volgorde wilt optimaliseren waarin de zoekresultaten worden weergegeven, kunt u [de zoekpositie verhogen](#searchrank) van een paar geselecteerde elementen.

* **Indexeren**: Alleen geïndexeerde metagegevens en elementen worden geretourneerd in de zoekresultaten. Voor betere dekking en betere prestaties, zorg behoorlijk indexeren en volg de beste praktijken. Zie [indexeren](#searchindex).

* Als u bepaalde elementen wilt uitsluiten van zoekresultaten, gebruikt u `excludedPath` eigenschap in de index van Lucene.

## Enkele voorbeelden ter illustratie van zoekopdrachten {#samples}

Gebruik dubbele aanhalingstekens rond trefwoorden om te zoeken naar elementen die de exacte woordgroep bevatten in de exacte volgorde die de gebruiker heeft opgegeven.

![Gedrag zoeken met en zonder aanhalingstekens](assets/search_with_quotes.gif)

*Afbeelding: Gedrag zoeken met en zonder aanhalingstekens.*

**Zoeken met jokerteken voor sterretje**: Als u de zoekopdracht wilt uitbreiden, gebruikt u een sterretje voor of na het zoekwoord om het gewenste aantal tekens te zoeken. Als u bijvoorbeeld zoekt naar tekst zonder sterretje, worden er geen elementen geretourneerd die een variatie van het woord bevatten (inclusief in de metagegevens). Een sterretje vervangt het gehele aantal tekens. Bijvoorbeeld:

* `run` retourneert elementen met trefwoord exact uitvoeren
* `run*` retourneert elementen met `running`, `run`, `runaway`, enzovoort.
* `*run` retourneert elementen met `outrun`, `rerun`, enzovoort.
* `*run*` retourneert alle mogelijke combinaties.

![Het gebruik van een sterretje in het zoeken naar elementen illustreren aan de hand van een voorbeeld](assets/search_with_asterisk_run.gif)

*Afbeelding: het gebruik van jokertekens voor sterretjes in het zoeken naar elementen aan de hand van een voorbeeld.*

**Zoeken met jokerteken voor vragen**: Als u de zoekopdracht wilt uitbreiden, gebruikt u een of meer &#39;?&#39; tekens die exact overeenkomen met het aantal tekens. In de volgende afbeelding, bijvoorbeeld:

* `run???` query komt niet overeen met enig element.

* `run????` query komt overeen met het woord `running` met vier tekens na `run`.

* `??run` query komt overeen met het woord `rerun` met twee tekens eerder `run`.

![Het gebruik van jokertekens in de zoekfunctie voor elementen illustreren aan de hand van een voorbeeld](assets/search_with_questionmark_run.gif)

*Afbeelding: een voorbeeld van het gebruik van jokertekens voor vraagtekens bij het zoeken naar elementen.*

**Een trefwoord uitsluiten**: Gebruik een streepje om te zoeken naar elementen die geen trefwoord bevatten. Bijvoorbeeld: `running -shoe` query retourneert elementen die bevatten `running`, maar niet `shoe`. Op dezelfde manier `camp -night` query retourneert elementen die bevatten `camp` maar niet `night`. De query `camp-night` retourneert elementen die beide bevatten `camp` en `night`.

![Gebruik van streepje om te zoeken naar elementen die geen uitgesloten trefwoord bevatten](assets/search_dash_exclude_keyword.gif)

*Figuur: Het gebruik van streepje om naar activa te zoeken die geen uitgesloten sleutelwoord bevatten.*

## Configuratie- en beheertaken met betrekking tot zoekfunctionaliteit {#configadmin}

### Indexconfiguraties zoeken {#searchindex}

Asset Discovery is afhankelijk van indexering van de DAM-inhoud, inclusief de metagegevens. Snellere en nauwkeurige detectie van bedrijfsmiddelen is afhankelijk van geoptimaliseerde indexering en geschikte configuraties. Zie [zoekindex](/help/assets/performance-tuning-guidelines.md#search-indexes), [vragen en indexeren van eikels](/help/sites-deploying/queries-and-indexing.md), en [best practices](/help/sites-deploying/best-practices-for-queries-and-indexing.md).

Als u bepaalde elementen wilt uitsluiten van zoekresultaten, gebruikt u `excludedPath` eigenschap in de index van Lucene.

### Zoeken op visuele of gelijkenis {#configvisualsearch}

Bij visueel zoeken worden slimme tags gebruikt. Voer de volgende stappen uit nadat u de functionaliteit voor slimme tags hebt geconfigureerd.

1. In [!DNL Experience Manager] CRXDE, in `/oak:index/lucene` , voegt u de volgende eigenschappen en waarden toe en slaat u de wijzigingen op.

   * `costPerEntry` eigenschap of type `Double` met de waarde `10`.
   * `costPerExecution` eigenschap of type `Double` met de waarde `2`.
   * `refresh` eigenschap of type `Boolean` met de waarde `true`.

   Deze configuratie staat onderzoeken van de aangewezen index toe.

1. Om een index van Lucene, in CRXDE, tot stand te brengen bij `/oak:index/damAssetLucene/indexRules/dam:Asset/properties`, knooppunt maken met naam `imageFeatures` van het type `nt-unstructured`. In `imageFeatures` knooppunt,

   * Toevoegen `name` eigenschap of type `String` met de waarde `jcr:content/metadata/imageFeatures/haystack0`.
   * Toevoegen `nodeScopeIndex` eigenschap of type `Boolean` met de waarde van `true`.
   * Toevoegen `propertyIndex` eigenschap of type `Boolean` met de waarde van `true`.
   * Toevoegen `useInSimilarity` eigenschap of type `Boolean` met de waarde `true`.

   Sla de wijzigingen op.

1. Toegang `/oak:index/damAssetLucene/indexRules/dam:Asset/properties/predictedTags` en toevoegen `similarityTags` eigenschap of type `Boolean` met de waarde van `true`.
1. Slimme tags toepassen op de elementen in uw [!DNL Experience Manager] opslagplaats. Zie [hoe u slimme tags kunt configureren](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/configuring/tagging.html#configuring).
1. In CRXDE, in `/oak-index/damAssetLucene` node, stel de `reindex` eigenschap aan `true`. Sla de wijzigingen op.
1. (Optioneel) Als u het zoekformulier hebt aangepast, kopieert u het `/libs/settings/dam/search/facets/assets/jcr%3Acontent/items/similaritysearch` knooppunt naar `/conf/global/settings/dam/search/facets/assets/jcr:content/items`. Sla de wijzigingen op.

Zie voor gerelateerde informatie [slimme tags in Experience Manager begrijpen](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/metadata/image-smart-tags.html) en [slimme tags beheren](/help/assets/enhanced-smart-tags.md).

>[!CAUTION]
>
>Als de Lucene-indexering uit [!DNL Adobe Experience Manager]De zoekopdracht op basis van slimme tags werkt dan niet zoals u had verwacht.

### Verplichte metagegevens {#mandatorymetadata}

Zakelijke gebruikers, beheerders of DAM-bibliotheken kunnen bepaalde metagegevens definiëren als verplichte metagegevens die nodig zijn om de bedrijfsprocessen te laten werken. Om verschillende redenen ontbreken deze metagegevens mogelijk bij sommige elementen, zoals oudere elementen of elementen die in bulk zijn gemigreerd. Elementen met ontbrekende of ongeldige metagegevens worden gedetecteerd en gerapporteerd op basis van de eigenschap voor geïndexeerde metagegevens. Zie voor meer informatie [verplichte metagegevens](/help/assets/metadata-schemas.md#define-mandatory-metadata).

### Zoekfacetten wijzigen {#searchfacets}

Om de snelheid van detectie te verbeteren, [!DNL Experience Manager Assets] bevat zoekfacetten waarmee u de zoekresultaten kunt filteren. Het deelvenster Filters bevat standaard enkele standaardfacetten. Beheerders kunnen het deelvenster Filters aanpassen om de standaardfacetten te wijzigen met behulp van de ingebouwde voorspelling. [!DNL Experience Manager] verstrekt een goede inzameling van in-gebouwde predikaten en een redacteur om de facetten aan te passen. Zie [zoekfacetten](/help/assets/search-facets.md).

### Tekst extraheren tijdens het uploaden van elementen {#extracttextupload}

U kunt [!DNL Experience Manager] om de tekst uit de elementen te halen wanneer gebruikers elementen uploaden, zoals PSD- of PDF-bestanden. [!DNL Experience Manager] indexeert de geëxtraheerde tekst en helpt gebruikers deze elementen te doorzoeken op basis van de geëxtraheerde tekst. Zie [elementen uploaden](/help/assets/manage-assets.md#uploading-assets).

Als de tekstextractie te resource-intensief wordt voor uw plaatsing, overweeg [tekstextractie uitschakelen](https://helpx.adobe.com/experience-manager/kb/Disable-binary-text-extraction-to-optimize-Lucene-indexing-AEM.html).

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

## Werken met resultaten voor middelenzoekopdrachten {#aftersearch}

U kunt het volgende doen met de middelen u hebt gezocht in [!DNL Experience Manager]:

* Eigenschappen van metagegevens en andere informatie weergeven.
* Download een of meer middelen.
* Gebruik Desktophandelingen om deze middelen in de bureaubladtoepassing te openen.
* Slimme verzamelingen maken.
* Een versie maken
* Een workflow starten
* Relatieve of ongerelateerde elementen
* Pas filters toe met behulp van het deelvenster Filters dat na het uitvoeren van de zoekopdracht automatisch wordt weergegeven om de zoekresultaten te beperken.

### Zoekresultaten sorteren {#sort}

U kunt zoekresultaten sorteren om sneller de vereiste elementen te vinden. U kunt de zoekresultaten alleen sorteren in de lijstweergave en wanneer u **[[!UICONTROL Files]](#searchui)** van de **[!UICONTROL Filters]** deelvenster. [!DNL Assets] gebruikt sorteren op de server om snel alle elementen (hoe talrijk ook) in een map of resultaten van een zoekopdracht te sorteren. Sorteren op de server levert sneller en nauwkeuriger resultaten op dan sorteren op de client.

In de lijstweergave kunt u de zoekresultaten op dezelfde manier sorteren als elementen in een willekeurige map. Sorteren werkt op deze kolommen: Naam, Titel, Status, Dimensionen, Grootte, Classificatie, Gebruik, Gemaakt, Gewijzigd, Gepubliceerd, Workflow en Uitgecheckt.

Voor beperkingen van de sorteerfunctionaliteit raadpleegt u [beperkingen](#limitations).

### Gedetailleerde informatie over een element controleren {#checkinfo}

Op de pagina met zoekresultaten kunt u gedetailleerde informatie over een doorzocht element controleren.

Als u alle metagegevens van een element wilt weergeven, selecteert u het element en klikt u op **[!UICONTROL properties]** op de werkbalk.

Als u de opmerkingen over een asset of de versiegeschiedenis van een asset wilt controleren, klikt u op de asset om een voorvertoning op grote grootte te openen. Open de tijdlijn in het linkerspoor en selecteer **[!UICONTROL Comments]** of **[!UICONTROL Versions]**. U kunt de tijdlijnactiviteit zoals opmerkingen of versies ook in chronologische volgorde sorteren.

![Tijdlijnitems voor een zoekmiddel sorteren](assets/sort_timeline_search_results.gif)

*Afbeelding: de items in de tijdlijn sorteren voor een zoekelement.*

### Gezochte middelen downloaden {#download}

U kunt de gezochte elementen en hun vertoningen downloaden enkel aangezien u regelmatige activa van omslagen downloadt. Selecteer een of meer elementen in de zoekresultaten en klik op **[!UICONTROL Download]** op de werkbalk.

### Eigenschappen van metagegevens voor bulkupdates {#metadataupdates}

Het is mogelijk om bulkupdates uit te voeren naar de algemene metagegevensvelden van meerdere elementen. Selecteer een of meer elementen in de zoekresultaten. Klikken **[!UICONTROL Properties]** op de werkbalk en werk de metagegevens naar wens bij. Klikken **[!UICONTROL Save and Close]** wanneer gereed. De eerder bestaande metagegevens in de bijgewerkte velden worden overschreven.

Voor de middelen die in één enkele omslag of een inzameling beschikbaar zijn, is het gemakkelijker om [de metagegevens bulksgewijs bijwerken](/help/assets/metadata.md) zonder de zoekfunctie te gebruiken. Voor de elementen die beschikbaar zijn in verschillende mappen of voldoen aan een algemeen criterium, is het sneller om de metagegevens bulksgewijs bij te werken door te zoeken.

### Slimme verzamelingen {#smart-collections}

Een verzameling is een geordende set elementen die elementen van verschillende locaties kunnen bevatten, omdat verzamelingen alleen verwijzingen naar deze elementen bevatten. Verzamelingen zijn van de volgende twee typen:

* Een statische referentielijst met elementen, mappen en andere verzamelingen.
* Een dynamische lijst (slimme verzameling) die elementen in de verzameling vult op basis van zoekcriteria.

U kunt slimme verzamelingen maken op basis van de zoekcriteria. Selecteer in het deelvenster **[!UICONTROL Filters]** de optie **[!UICONTROL Files]** en klik op **[!UICONTROL Save Smart Collection]**. Zie [Verzamelingen beheren](/help/assets/manage-collections.md).

### Een versie maken {#create-version}

Maak een versie voor de elementen die in de zoekresultaten worden weergegeven. Selecteer het element en klik op **[!UICONTROL Create]** > **[!UICONTROL Version]**. Voeg een optioneel label of een opmerking toe en klik op **[!UICONTROL Create]**. U kunt ook meerdere elementen tegelijk selecteren en er versies voor maken.

### Een workflow maken {#create-workflow}

Net als bij de functie voor het maken van een versie kunt u ook een workflow maken voor de elementen die in de zoekresultaten worden weergegeven. Selecteer de elementen en klik op **[!UICONTROL Create]** > **[!UICONTROL Workflow]**. Selecteer het workflowmodel, geef een titel voor de workflow op en klik op **[!UICONTROL Start]**.

### Relatieve en niet-gerelateerde elementen {#relate-unrelate-assets}

Verwante en losse elementen die in de zoekresultaten worden weergegeven. Selecteer de elementen en klik op **[!UICONTROL Relate]** of **[!UICONTROL Unrelate]**.

## Onverwachte zoekresultaten en problemen {#unexpected-results}

| Fout, problemen, symptomen | Mogelijke reden | Mogelijke oplossing of begrip van het probleem |
|---|---|---|
| Onjuiste resultaten bij het zoeken naar elementen met ontbrekende metagegevens. | Bij het zoeken naar elementen waarbij de verplichte metagegevens ontbreken, [!DNL Experience Manager] kunnen elementen weergeven die geldige metagegevens hebben. De resultaten zijn gebaseerd op de eigenschap voor geïndexeerde metagegevens. | Nadat de metagegevens zijn bijgewerkt, moet de index opnieuw worden geïndexeerd om de juiste status van metagegevens voor elementen weer te geven. Zie [verplichte metagegevens](metadata-schemas.md#define-mandatory-metadata). |
| Te veel zoekresultaten. | Brede zoekparameter. | Overweeg het beperken van [zoekopdracht](#scope). Het gebruik van slimme tags kan meer zoekresultaten opleveren dan u had verwacht. Zie [zoekgedrag met slimme tags](#withsmarttags). |
| Onverwante of gedeeltelijk verwante zoekresultaten. | Wijzigingen in zoekgedrag met slimme tags. | Begrijpen [hoe zoeken verandert na slimme tags](#withsmarttags). |
| Geen suggesties voor automatisch aanvullen van elementen. | Nieuw geüploade elementen zijn nog niet geïndexeerd. De metagegevens zijn niet direct beschikbaar als suggesties wanneer u een trefwoord in de zoekbalk typt. | [!DNL Experience Manager] wacht tot een time-outperiode (standaard één uur) is verstreken voordat een achtergrondtaak wordt uitgevoerd om de metagegevens voor alle nieuw geüploade of bijgewerkte elementen te indexeren en voegt de metagegevens vervolgens toe aan de lijst met suggesties. |
| Geen zoekresultaten. | <ul><li>Elementen die overeenkomen met uw query bestaan niet. </li><li> Whitespace toegevoegd vóór de zoekquery. </li><li> Niet-ondersteund metagegevensveld bevat het trefwoord waarnaar u hebt gezocht.</li><li> Zoeken tijdens offline uitvoering van een element. </li></ul> | <ul><li>Zoeken met een ander trefwoord. U kunt ook slim labelen of zoeken op basis van gelijkenis gebruiken om de zoekresultaten te verbeteren. </li><li>[Bekende beperking](#limitations).</li><li>Niet alle metagegevensvelden worden in aanmerking genomen voor zoekopdrachten. Zie [bereik](#scope).</li><li>Later zoeken of on-time en off-time wijzigen voor de vereiste elementen.</li></ul> |
| Zoekfilter of voorspelling is niet beschikbaar. | <ul><li>Het zoekfilter is niet geconfigureerd.</li><li>Het is niet beschikbaar voor uw aanmelding.</li><li>(Minder waarschijnlijk) De onderzoeksopties worden niet aangepast op de plaatsing u gebruikt.</li></ul> | <ul><li>Neem contact op met de beheerder om te controleren of de zoekaanpassingen beschikbaar zijn of niet.</li><li>Neem contact op met de beheerder om te controleren of uw account de rechten/machtigingen heeft om de aanpassing te gebruiken.</li><li>Neem contact op met de beheerder en controleer de beschikbare aanpassingen voor de [!DNL Assets] implementatie die u gebruikt.</li></ul> |
| Bij het zoeken naar visueel vergelijkbare afbeeldingen ontbreekt een verwachte afbeelding. | <ul><li>Afbeelding is niet beschikbaar in [!DNL Experience Manager].</li><li>Afbeelding is niet geïndexeerd. Doorgaans wanneer het onlangs is geüpload.</li><li>Afbeelding heeft geen slimme tags.</li></ul> | <ul><li>Voeg de afbeelding toe aan [!DNL Assets].</li><li>Neem contact op met de beheerder om de gegevensopslagruimte opnieuw te indexeren. Zorg er ook voor dat u de juiste index gebruikt.</li><li>Neem contact op met de beheerder om de relevante elementen een slimme tag te geven.</li></ul> |
| Bij het zoeken naar visueel vergelijkbare afbeeldingen wordt een irrelevante afbeelding weergegeven. | Visuele zoekfunctionaliteit. | [!DNL Experience Manager] geeft zoveel mogelijk relevante activa weer. Eventuele minder relevante afbeeldingen worden aan de resultaten toegevoegd, maar met een lagere zoekpositie. De kwaliteit van de overeenkomsten en de relevantie van de gezochte elementen nemen af wanneer u de zoekresultaten omlaag schuift. |
| Wanneer u zoekresultaten selecteert en gebruikt, wordt niet op alle gezochte elementen ingegaan. | De [!UICONTROL Select All] Hiermee selecteert u alleen de eerste 100 zoekresultaten in de kaartweergave en de eerste 200 zoekresultaten in de lijstweergave. | |

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] naslaggids voor implementatie](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/developing/search-tutorial-develop.html)
>* [Geavanceerde configuratie om zoekresultaten te verhogen](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/search-and-discovery/search-boost.html)
>* [Zoeken naar slimme vertaling configureren](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/translation/smart-translation-search-technical-video-setup.html)
