---
title: Nota's van de versie voor  [!DNL Adobe Experience Manager]  6.5
description: Vind versieinformatie, wat nieuw is, installeer hoe te, en een gedetailleerde veranderingslijst voor  [!DNL Adobe Experience Manager]  6.5.
mini-toc-levels: 4
solution: Experience Manager
feature: Release Information
role: User,Admin,Developer
exl-id: 811fccbc-6f63-4309-93c8-13b7ace07925
source-git-commit: 6eccdab5cd492686dda2aca3fee4df171a2d9011
workflow-type: tm+mt
source-wordcount: '8925'
ht-degree: 0%

---

# [!DNL Adobe Experience Manager] 6.5 Nieuwste opmerkingen bij de release Service Pack {#aem-service-pack-release-notes}

<!-- For an itemized list of all issues found in this release information, see the following spreadsheet: https://adobe-my.sharepoint.com/:x:/r/personal/anujkapo_adobe_com/_layouts/15/Doc.aspx?sourcedoc=%7B3ea81ae4-e605-4153-b132-f2698c86f84e%7D&action=edit&wdinitialsession=d8c7b903-87fc-4f2d-9ef2-542a82169570&wdrldsc=3&wdrldc=1&wdrldr=SessionMemoryQuotaExceededDuringSession -->

<!-- DO NOT DELETE THIS HIDDEN NOTE      DO NOT DELETE THIS HIDDEN NOTE
>[!NOTE]
>
>Fixes in [!DNL Experience Manager] Forms are delivered through a separate add-on package one week after the scheduled [!DNL Experience Manager] Service Pack release date. In this case, the add-on packages release Thursday, May 29, 2025. In addition, a list of Forms fixes and enhancements is added to this section. -->

## Gegevens vrijgeven {#release-information}

| Product | [!DNL Adobe Experience Manager] 6.5 |
| -------- | ---------------------------- |
| Versie | 6.5.24.0 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Type | Service Pack-release |
| Datum | 26 november 2025 <!-- UPDATE FOR EACH NEW RELEASE --> |
| URL downloaden | [&#x200B; Distributie van de Software &#x200B;](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.24.0.zip) <!-- UPDATE FOR EACH NEW RELEASE --> |

<!-- OLD DOWNLOAD URL
(https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.23.0.zip) -->

## Wat is inbegrepen in [!DNL Experience Manager] 6.5.24.0 {#what-is-included-in-aem-6524}

[!DNL Experience Manager] 6.5.24.0 bevat nieuwe functies, belangrijke verbeteringen die door de klant worden aangevraagd en opgeloste problemen. Het omvat ook prestaties, stabiliteit, en veiligheidsverbeteringen die sinds de aanvankelijke beschikbaarheid van 6.5 in April 2019 worden vrijgegeven. [&#x200B; installeer dit Pak van de Dienst &#x200B;](#install) op [!DNL Experience Manager] 6.5.

<!-- UPDATE FOR EACH NEW RELEASE -->

<!--
## Key features and enhancements
-->




## Opgeloste problemen in Service Pack 24 {#fixed-issues}

<!-- 6.5.24.0 REVIEWERS: WHAT ARE THE KEY FEATURES AND ENHANCEMENTS THAT YOU WANT TO HIGHLIGHT IN THIS RELEASE? -->

<!-- UPDATE BELOW FOR EACH NEW RELEASE -->

### [!DNL Assets] {#assets-sp24}

* Na het bijwerken naar versie 6.5.23.0 leidde het sorteren van mappen op wijzigingsdatum in de Kaartweergave tot problemen bij het zoeken naar onlangs gewijzigde middelen voor on-premise implementaties. (ASSETS-56946)
* De herhaalde ingangen van het waarschuwingslogboek worden geproduceerd tijdens planneruitvoeringen. (ASSETS-52554)
* Het sorteren van titels werkt niet in de Lijstweergave. (ASSETS-50716)
* Het venster Eigenschappen van verzameling wordt niet gesloten, zelfs niet nadat u op de knop Annuleren hebt geklikt. (ASSETS-48504)

* Een *Ongeldige URL* fout komt voor wanneer het proberen om activa in AEM 6.5.22 te annoteren. (NPR-42684)
* Het Assets Metadata Editor-formulier wordt niet opnieuw geïnitialiseerd nadat er handelingen met betrekking tot de metagegevens zijn uitgevoerd of wanneer de relatie tussen de gegevens is verbroken. (ASSETS-52207)
* Wanneer elementen van de externe DAM opnieuw worden gesynchroniseerd naar de lokale Sites, wordt de gepubliceerde status van de elementen onjuist bijgewerkt naar `Not published` . (ASSETS-48958)
* Problemen die zijn opgetreden tijdens een upgrade van SP23 naar 6.5 LTS. (ASSETS-50541)

### [!DNL Sites]{#sites-6524}

#### Toegankelijkheid {#sites-accessibility-6524}

* Het **de vertoningsformaat van de Schakelaar** dialoogvakje steunt nu volledige toetsenbordverrichting. De nadruk slaat niet meer de **knoop van de Montages van de Mening** over, en standaardsleutels (`Tab`, `Enter`, `Space`) werk constant. (SITES-24306)
* Toetsenbordgebruikers kunnen de gepubliceerde statustags zonder muis verwijderen. Focus landt op elke tag en activering werkt met `Enter`/`Space` en Backspace/Delete. Het besturingselement voor tags gedraagt zich nu als een knop, die de feedback van schermlezers verbetert en voldoet aan WCAG 2.1.1-toetsenbord. (SITES-24491)
* De spoorterugvloeiingen van filters reageren responsief bij smalle viewports. De besturingselementen en resultaten van de selectie blijven in de viewport beschikbaar met een zoompercentage van 400%, zodat horizontaal schuiven en de inhoud niet wordt onderbroken. (SITES-24708)
* AEM herstelt volledige toetsenbordtoegang tot het Terugstellen ContextHub, Persona, en de knopen van het Apparaat. Tab en pijltoetsen bereiken elk besturingselement, tonen een zichtbare focusindicator en activeren handelingen met `Enter` of `Space` . Schermlezers kondigen duidelijke labels aan. (SITES-24939)
* Datuminvoer en de kiezer blijven volledig zichtbaar bij 320 px. Bij de modale tijdverdraaiing wordt een responsieve grootte gebruikt, zodat de besturing niet langer wordt bijgesneden of verdwijnt op de kleinste viewport. (SITES-24962)
* References rail ondersteunt nu 400% browserzoom zonder dat toegang tot de inhoud verloren gaat. De spoorstaaf gebruikt ontvankelijke grootte in plaats van een vaste breedte, zodat blijven de punten zichtbaar en selecteerbaar bij 1280×1024. (SITES-24972)
* Filterrails werken nu met een zoompercentage van 400%. De spoorstaaf resizes met relatieve eenheden en blokkeert niet meer of verbergt filtercontroles. Gebruikers kunnen elke filteroptie weergeven en selecteren zonder horizontaal schuiven of geknipte raakdoelen. (SITES-24981)
* Toetsenbordgebruikers kunnen opmaakmenu&#39;s gebruiken in het modaal Taser. Het drukken `Enter` of `Space` op **Lijst** of **Formaat van de Paragraaf** opent pop-up, de sleutels van de Pijl navigeren opties, en `Enter` past de selectie toe. `Escape` sluit het menu en herstelt de focus naar het activerende besturingselement, waardoor een consistente werkbalkworkflow ontstaat. (SITES-25235)
* De pop-up Kleurkiezer voor staal blijft nu bij 320 px in de viewport staan. In het pop-upvenster worden alle kleurrijen weergegeven en wordt schuiven ondersteund. Auteurs kunnen dus elk staal op kleine schermen selecteren. (SITES-25274)
* De demografische drop-down menu&#39;s van de toolbar werken nu volledig met het toetsenbord. Als u een menu opent, gaat de focus naar de eerste optie, navigeert de pijltoets naar de lijst en gaat Esc/Tab dichtbij of verder zonder de focus naar de werkbalk te verplaatsen. Interactieve items gebruiken de juiste semantiek, zodat NVDA en andere lezers de opties correct bekendmaken. (SITES-25310)
* De functie Component toevoegen in de inhoudsstructuur werkt naar behoren in AEM 6.5 SP24. De fout die aanvankelijk optrad, kwam van ontbrekende auteurstoestemmingen in een lokale opstelling, niet van AEM. Auteurs met bewerkingsrechten kunnen de knop activeren en componenten toevoegen met het toetsenbord of de muis. (SITES-25312)
* Toetsenbord- en schermlezertoegang op de werkbalk Demografisch werkt nu betrouwbaar. De auteurs die NVDA gebruiken kunnen **Commerce**, **Persona**, en 88 met pijlen oversteken, duidelijke nadruk waarnemen terugkoppelt, en begrijpen welk lusje actief is. (SITES-25326)

* De **Skip aan inhoud** verbinding verplaatst nu toetsenbordnadruk naar de belangrijkste inhoudskop. De focus blijft zichtbaar op een uniek geïdentificeerd doel, zodat schermlezers de juiste sectie aankondigen. De wijziging voldoet aan WCAG 2.4.1 en 2.4.3. (SITES-24061)
* De navigatie van het toetsenbord in de het huispaginaboom van Plaatsen volgt een logische opeenvolging na het gebruiken van **Uitgezocht allen**. De bewegingen van de nadruk van **Uitgezochte allen** aan de volgende controle (Open linkerspoor) in plaats van terug naar het begin van de pagina te springen. (SITES-24307)
* De titels van de sectie en geven controles in de redacteur van Plaatsen uit antwoorden op toetsenbordnadruk en activering. Toetsenbordgebruikers geven dezelfde titel en handelingen weer die eerder alleen op de muisaanwijzer werden weergegeven. (SITES-24479)
* De knopen in de redacteur van Plaatsen stellen beschrijvende namen in plaats van generische of ontbrekende etiketten bloot. Hulptechnologieën kondigen de juiste actie aan, die helderheid verbetert en wanklikken vermindert. (SITES-24480)
* Schermlezers ontvangen een gesproken bericht &quot;Laden&quot; terwijl de weergave Sites wordt vernieuwd. De update voegt een speciale status live regio toe en schrijft de boodschap programmatisch in deze regio, die de voortgang bevestigt zonder de focus te verplaatsen. (SITES-24481)
* De zijspoor van Assets omvat nu een duidelijke **Dichte** controle en keert nadruk aan de knevelknoop terug. Gebruikers van toetsenborden en schermlezers sluiten het deelvenster direct af in plaats van met de Tab-toets door elk besturingselement te gaan. Door deze wijziging worden toetsaanslagen verminderd en komt het gedrag van het deelvenster overeen. (SITES-24489)
* De tablijst ARIA in de Sites Page Editor bevat een beschrijvende naam. Schermlezers identificeren het besturingselement nu als een tablijst en lezen het juiste label, zodat gebruikers de juiste set tabbladen kunnen vinden en betrouwbaar tussen de tabbladen kunnen navigeren. (SITES-24492)
* Door te zoeken in de Editor side rail worden de resultaten nu voor schermlezers bekendgemaakt. Terwijl gebruikers typen, wordt in een live statusbericht het aantal overeenkomsten en updates gerapporteerd zonder de focus te verplaatsen. Toetsenbordgebruikers detecteren de resultaten direct. (SITES-24506)
* De selectie van de rij in de Mening van de Lijst verbetert voor hulptechnologiegebruikers. Checkbox stelt een betekenisvolle naam bloot die uit de rijTitel wordt afgeleid, zodat blijven de aankondigingen kort en beschrijven correct de actie. (SITES-24514)
* Toegankelijkheidsnamen van de lijstweergave zijn gecorrigeerd. De tabel verwijdert `aria-label` uit niet-interactieve elementen en wijst het label toe aan de koppeling of knop die kan worden geactiveerd. Gebruikers van schermlezers horen nu nauwkeurige, niet-gedupliceerde labels in de kolom. (SITES-24515)
* De plakkoptekst verbergt het modale dialoogvenster voor het gereedschap Taser tijdens het gebruik van de functie voor zoomen met hoge waarde niet. De inhoud blijft leesbaar en kan worden gebruikt bij een zoompercentage van 200% en 400%, met verticale stroom en geen geknipte secties. (SITES-24523)
* Wanneer u in het zoekveld typt, wordt niet langer een voortijdige aankondiging van het eerste resultaat of een accidentele activering uitgevoerd. De ervaring kondigt nu een beknopt statusbericht met de resultaattelling aan, terwijl de nadruk op het gebied blijft tot de gebruiker aan de lijst navigeert. (SITES-24658)
* In het tekstveld Alternatieve tekst in het hyperlinkdialoogvenster van de teksteditor wordt nu een programmatisch label weergegeven. Schermlezers kondigen &#39;Alternatieve tekst&#39; aan voor het veld en focussen landen op het correct benoemde besturingselement. Met deze oplossing verbetert u de navigatie voor toetsenbord- en spraakgebruikers. (SITES-24675)
* Er is een live statusbericht toegevoegd aan de References rail, waarbij wijzigingen onmiddellijk worden aangekondigd. Als u meerdere items selecteert, wordt er een duidelijk bericht over de beschikbaarheid van verwijzingen weergegeven. Dit voorkomt wijzigingen in de stille toestand en reduceert herhalingsacties. (SITES-24678)
* In het dialoogvenster Afbeelding wordt nu de laadstatus aangekondigd via een live ARIA-regio. Schermlezers horen het bericht &quot;Laden, een ogenblik geduld&quot; terwijl de spinner wordt weergegeven. En, een klaar update wanneer de inhoud eindigt, zodat weten de gebruikers wanneer zij kunnen interactie aangaan. (SITES-24697)
* In het dialoogvenster Koppelingsselectie wordt nu een actief gebied weergegeven waarin de zoekresultaten worden aangekondigd. Schermlezers horen de status &#39;resultaten bijgewerkt&#39; na elke zoekopdracht zonder de focus te verplaatsen, zodat gebruikers de duidelijke bevestiging krijgen dat de zoekopdracht is voltooid. (SITES-24700)
* Het dialoogvenster Koppelingsselectie wordt nu opnieuw geplaatst bij 320 px. Alle velden en handelingen blijven zichtbaar en kunnen worden gebruikt. De horizontale schuifbalk wordt dan niet meer weergegeven. (SITES-24709)
* In het dialoogvenster Koppelingsselectie wordt nu hetzelfde label gebruikt voor de schermtekst en de toegankelijke naam voor elk structuuritem. Schermlezers kondigen elk item aan terwijl ze met de pijltoetsen bewegen, inclusief het laatste niveau, zodat er geen sprake is van stille knooppunten en namen die niet overeenkomen. (SITES-24710)
* Wijzigingsfilters rapporteren nu de toestand als uitgevouwen of samengevouwen. Met de knop wordt `aria-expanded` synchroon met het filterdeelvenster geschakeld en wordt één duidelijke naam (&quot;Filters wijzigen&quot;) weergegeven, waardoor de verwarrende &#39;filter?&#39; wordt verwijderd aankondiging. Gebruikers van schermlezers kunnen het resultaat voorspellen van het activeren van het besturingselement. (SITES-24713)
* De modulaire kopballen behandelen niet meer inhoud bij breedte 320 px. De header wordt losgelaten uit de status van de sticky en de hoofdtekst van het dialoogvenster schuift, zodat alle velden en actieknoppen zichtbaar en bruikbaar blijven. Keyboard gebruikers kunnen elke controle bereiken zonder verlies van nadruk. (SITES-24718)
* Toepassingsnavigatiekoppelingen geven nu de juiste koppelingssemantiek weer. Schermlezers kondigen elk item aan als een koppeling in plaats van als een lijstitem, dat de toetsenbordnavigatie en spraakcontrole verbetert. De lijstcontainer houdt lijstsemantiek, terwijl de verbindingen de brandbare doelstellingen blijven. (SITES-24719)
* De resultaatstatus wordt nu aan schermlezers gemeld wanneer filters veranderen. NVDA leest zowel het &quot;X van de resultaten van Y&quot;aantal als het &quot;geen resultaat&quot;bericht. De pagineringsstatus gebruikt een actief gebied dat op zijn plaats bijwerkt, zodat horen de gebruikers bevestiging zonder nadruk te bewegen. (SITES-24720)
* De centrifugeknop in het dialoogvenster Carrousel kondigt nu één beknopte naam aan voor schermlezers. Het besturingselement herhaalt niet langer zowel het groeplabel als het invoerlabel, waardoor de gebruikers van NVDA minder uitgebreide informatie en verwarring krijgen. (SITES-24725)
* De zoeklijst in het menu Help bevat de juiste semantiek. De container stelt een lijst voor en elk resultaat blijft een koppeling zonder een conflicterende rol. NVDA en JAWS kondigen de koppelingen correct aan en de navigatie blijft consistent. (SITES-24729)
* Adobe heeft de pop-up met kleurstalen gecorrigeerd in Gebruikersvoorkeuren zodat NVDA het staal in focus aankondigt, niet het eerder geselecteerde staal. Toetsenbordgebruikers horen nauwkeurige kleurnamen terwijl ze door de lijst gaan en kunnen de juiste selectie bevestigen. (SITES-24739)
* NVDA leest nu de volledige Beschrijving in de folder van de Boom. In het deelvenster Details wordt tekst met meerdere regels als één waarde beschikbaar gemaakt en gekoppeld aan het veldlabel. Toetsenbordgebruikers horen de volledige tekst terwijl ze met de Tab-toets door alleen-lezen velden gaan. (SITES-24780)
* De structuurmap kondigt nu de datum Gewijzigd aan. NVDA leest de datum wanneer de nadruk zich in de Gewijzigde kolom beweegt. Het raster koppelt elke datum aan de itemnaam, zodat gebruikers zowel het bestand als de laatste update horen. (SITES-24782)
* In de voorvertoningsmodus worden nu de voorkeuren voor tekstspatiëring van de gebruiker gerespecteerd. Het canvas bevat de wijzigingen in de letter, het woord en de regelhoogte van alle vooraf bekeken inhoud. Tekst blijft niet meer vast of clips wanneer de tussenruimte wordt vergroot. Gebruikers met een toetsenbord en een laag gezichtsveld lezen inhoud zonder layouteonderbrekingen. (SITES-24936)
* AEM corrigeert de tabvolgorde op de pagina&#39;s van de Assets Editor. De tabvolgorde verplaatst zich nu van de kopbesturingselementen naar de knoppen in de contacthub en ten slotte naar de canvasgereedschappen in een duidelijke volgorde. Schermlezers volgen dezelfde volgorde, waardoor verwarring en snelheden op het toetsenbord worden voorkomen. (SITES-24937)
* AEM voegt een programmatische naam toe aan de menubalk Kaarthandelingen. De lezers van het scherm kondigen de controle correct aan, en de toespraakgebruikers kunnen het door naam richten. Toetsenbordnavigatie en -focus blijven ongewijzigd. (SITES-24938)
* De menu&#39;s van de Kaartweergave respecteren verhoogde tekstspatiëring. Het item Meer handelingen wordt groter en er worden geen afkortingen meer toegepast op labels, waaronder Snel publiceren. Gebruikers die letters, woorden of regelafstand opheffen, behouden volledige labels en toegang tot het toetsenbord. (SITES-24941)
* De rol &quot;presentatie&quot; die de tabel op de startpagina Sites in de toegankelijkheidsstructuur had verborgen, is verwijderd. De tabel wordt opnieuw correct gelezen. NVDA en JAWS detecteren de tabel, herkennen kopteksten en kondigen koptekstrelaties aan tijdens rij- en kolomnavigatie. (SITES-24942)
* Het sorteren van feedback in de lijstweergave is expliciet en consistent. Na een sortering stelt de koptekst de volgorde beschikbaar via `aria-sort` . De wijziging wordt aangekondigd, terwijl niet-gesorteerde koppen niet langer een status claimen, waardoor gebruikers van schermlezers gemakkelijker kunnen bijhouden welke kolom de sortering bepaalt. (SITES-24943)
* De Edit kopbal van de Lay-out stelt niet meer een niet-werkende **&#x200B;**&#x200B;knoop uit. Het besturingselement fungeert nu als een statisch statuslabel en blijft buiten de tabvolgorde zodat gebruikers van het toetsenbord geen toetsaanslag verspillen. Het gebruik **selecteert een andere wijze** om wijzen te veranderen, met duidelijk scherm-lezer terugkoppelt. (SITES-24950)
* Op de emulatorwerkbalk worden standaard volledige apparaatnamen weergegeven. Het label wordt niet meer afgebroken tijdens het laden, zodat gebruikers apparaten kunnen lezen en selecteren zonder te raden. De tekst wordt op zuivere wijze geschaald over zoomniveaus en smalle breedten. (SITES-24952)
* De Emulatorwerkbalk past bij kleine viewports. Bij 320 pixels wordt de weergave zonder clipping weergegeven in de lijst met apparaten. Gebruikers kunnen dus Galaxy S7 en nieuwere modellen selecteren. De lay-out wordt geschaald en omlopen om horizontaal schuiven te voorkomen, zelfs bij een zoompercentage van 400%. (SITES-24953)
* Schermlezers kondigen het geselecteerde apparaat en de bijbehorende metingen aan in de emulator. De NVDA houdt op met het lezen van de liniaalstroom. De apparaatknop gebruikt een bijgevoegde beschrijving voor de knopinfo-tekst, die ruis en navigatie door hulplijnen vermindert. (SITES-24955)
* In de filterbalk wordt elke geselecteerde tag nu behandeld als een actieknop. Toegankelijke namen wissen en focusverwerking verbeteren de aankondigingen en het toetsenbord. (SITES-24980)
* De updates van de status in de de filtermening van Admin van Plaatsen kondigen aan het schermlezers aan. Wanneer gebruikers van Kaart/Lijst schakelen terwijl de punten laden, spreekt NVDA nu het &quot;gelieve te wachten&quot;bericht door een levend gebied. Deze richtlijn voorkomt extra kliks en verwarring. (SITES-24992)
* De toetsenbordfocus beweegt nu in logische volgorde wanneer gebruikers de linkerrail uitbreiden. De nadruk verschuift direct van de linkerspoorknoop aan de uitgebreide inhoud, die de behoefte elimineert om elementen te achterhouden of over te slaan. Deze wijziging verbetert de toegankelijkheid voor schermlezers en toetsenbordgebruikers. (SITES-24998)
* De lezer van het scherm koppelt voor **uitgeeft** knoop nu de controle. Als u de knop activeert, wordt de actie Bewerken aangekondigd in plaats van een voorvertoningsbericht. Hierdoor wordt de helderheid verbeterd en worden invoerfouten voor niet-muisgebruikers verminderd. (SITES-25208)
* De bevestigingshandeling in het dialoogvenster Taser wordt correct voor schermlezers weergegeven. De besturingselementen &quot;Bevestigen&quot;, niet de pictogrambeschrijving, geven gebruikers van het toetsenbord en de schermlezer duidelijke aanwijzingen. (SITES-25223)
* Met de knop Help wordt nu een duidelijke, toegankelijke naam weergegeven. Schermlezers kondigen &quot;Help&quot; aan in plaats van een uitgebreide pictogrambeschrijving. Gebruikers begrijpen de actie en kunnen sneller hulp zoeken. (SITES-25224)
* De modale vertoningen Timewarp een duidelijke nadrukring op **`Set Date`** en **de verbindingen van de Tijdverdraaiing van de Uitgang**. Gebruikers die met de Tab-toets werken, zien precies waar de focus ligt en vermijden ongewenste acties. De ring handhaaft minstens 3 :1 contrast tegen de achtergrond. (SITES-25232)
* Schermlezers geven de besturingselementen Annotatie en Annotatie sluiten nu op de juiste wijze aan op de werkbalk Annotatie. NVDA zegt niet langer &quot;Voorvertoning ingedrukt&quot;, wat schrijvers heeft misleid en de verkeerde actie heeft voorgesteld. De aankondiging komt overeen met de ingedrukte knop en zorgt ervoor dat de workflow leeg blijft. (SITES-25234)
* De toetsenbordnavigatie op de werkbalk Annotatie werkt consistent. Bij het openen van de modus springt de focus niet meer naar Afsluiten, maar naar het beginbesturingselement voor het toevoegen van annotaties. Gebruikers navigeren achtereenvolgens door de besturingselementen zonder de Tab-toets om te keren. (SITES-25241)
* De kleine-schermweergave werkt zoals verwacht in de modus Taser. Het dialoogvenster maakt niet langer een horizontale schuifbalk met een resolutie van 320 px en de werkbalk blijft toegankelijk zonder dat er zijdelings wordt pannen. Deze update helpt slechtzienden die op de pagina inzoomen. (SITES-25242)
* De weergave op een klein scherm werkt zoals u had verwacht in de modus Afbeelding. Het dialoogvenster maakt niet langer een horizontale schuifbalk met een resolutie van 320 px en de afbeeldingsgereedschappen blijven toegankelijk zonder dat er zijdelings wordt pannen. Deze update verbetert de navigatie voor slechtzienden die op de pagina inzoomen. (SITES-25244)
* In de modus Zoeken worden de instellingen voor tekstspatiëring van de gebruiker gerespecteerd. Bij een hogere regelhoogte, alinea-afstand, letterspatiëring of woordspatiëring wordt de tekst niet meer geknipt of overlapt de structuur. Inhoud wordt opnieuw geplaatst bij WCAG 1.4.12-waarden en blijft volledig leesbaar. (SITES-25245)
* Het modaal Onderzoek past nu kleine schermen zonder de boomfolder bij 320 px te overlappen. Inhoud wordt opnieuw geplaatst in het dialoogvenster, houdt alleen verticaal schuiven in en zorgt ervoor dat de besturingselementen zichtbaar blijven. Deze oplossing verbetert de leesbaarheid en de toetsenbordnavigatie en richt zich op WCAG Reflow. (SITES-25246)
* De modale overloop van Carrousel dwingt niet langer horizontaal schuiven bij breedte van de telefoon. De component past zich aan aan 320 px, behoudt verticale stroom, en houdt controles in mening. De wijziging verbetert de leesbaarheid en de toegang tot het toetsenbord tijdens het ontwerpen. (SITES-25254)
* Workflows voor annotaties verliezen niet langer de focus. Bij modal wordt de focus aanvankelijk op een betekenisvolle kop geplaatst, wordt voorkomen dat de focus buiten het dialoogvenster valt en wordt de focus na het ontslag hersteld naar de trigger. De schermlezeruitvoer blijft beknopt en relevant. (SITES-25257)
* Het **de dialoogvakje van de Annotatie van de Schrapping** behandelt nu correct toetsenbordnadruk. Het openen van de dialoogdoos verplaatst nadruk aan zijn rubriek voor scherm-lezercontext, en het sluiten verzendt nadruk terug naar de **knoop van de Annotatie van de Schrapping** die het lanceerde. Gebruikers landen niet langer op niet-verbonden besturingselementen of achter het modaal. (SITES-25258)
* De tijdverdraaiingsdatumkiezer beheert nu de focus op de juiste wijze. Het drukken `Esc` keert nadruk aan de **Plukker van de Datum** knoop terug, en het kiezen van een datum verplaatst nadruk naar het verbonden inputgebied. Gebruikers van toetsenborden en schermlezers houden context en landen niet achter het modaal. (SITES-25264)
* De lezers van het scherm kondigen de correcte acties voor **aan annoteert** en **dicht annoteert** knopen. NVDA zegt niet langer &quot;Voorvertoningsknop ingedrukt&quot;; het kondigt de knopnaam aan zodat gebruikers weten wanneer de annotatiemodus begint of eindigt. (SITES-25268)
* Het modaal van de Annotatie toont nu een duidelijke **voorlegt** actie. Auteurs kunnen een opmerking toevoegen en deze verzenden met de knop voor het penpictogram of het modaal sluiten met `Esc` zonder de stroom te raden. (SITES-25269)
* Annotatie-item bevat expliciete actieknoppen. De dialoogdoos stelt **bloot legt** voor om de nota te bewaren en **annuleert** om het te sluiten, zowel toetsenbord toegankelijk als aangekondigd door ondersteunende technologie. Auteurs hoeven niet langer te vertrouwen op het klikken buiten het dialoogvenster of het alleen drukken op `Esc` om te voltooien. (SITES-25281)
* In de annotatiemodus blijft het toetsenbord nu actief op de overlay en de bijbehorende werkbalk. De pagina achter de overlay krijgt geen focus meer wanneer auteurs op Tab drukken. Gebruikers blijven dus georiënteerd en kunnen door annotaties navigeren zonder naar onderliggende inhoud te springen. (SITES-25282)
* De apparaatkiezer in Lay-out bewerken werkt naar behoren. Wanneer twee apparaatopties ongeveer dezelfde breedte hebben (bijvoorbeeld iPhone 8 Plus naast Galaxy 7), wordt knopinfo met de knoppen weergegeven om het volledige label weer te geven, terwijl beide knoppen zichtbaar en toegankelijk blijven. (SITES-25285)
* Bij een zoompercentage van 200% overschrijdt Lay-out bewerken de pagina niet meer. De werkbalk wordt volledig gerenderd en indien nodig wordt horizontaal schuiven weergegeven, zodat gebruikers met een laag gezichtsvermogen weer toegang krijgen tot eerder verborgen besturingselementen. (SITES-25288)
* De tabvolgorde in de voorvertoning van de layout gaat nu van de primaire werkbalk naar de werkbalk Demografisch. Gebruikers van toetsenborden en schermlezers kunnen de besturingselementen in een voorspelbare volgorde doorlopen in plaats van naar de secundaire werkbalk te gaan. De wijziging wordt uitgelijnd op de WCAG 2.4.3-focusvolgorde. (SITES-25305)
* Als u op de pagina zoomt naar 200%, wordt een deel van de werkbalk Demografisch niet meer verborgen. De werkbalksectie beheert overloop en biedt schuiven in een eigen gebied, zodat elk besturingselement zichtbaar blijft en met een hoge vergroting kan worden gebruikt. (SITES-25309)
* Tekstinvoer op de werkbalk Demografische gegevens geeft nu de juiste toegankelijke namen weer. Elk veld bevat een unieke id met een programmatisch label, zodat schermlezers het doel van het veld bekendmaken en gebruikers door een label kunnen navigeren. Het zichtbare label bevindt zich in de buurt van het besturingselement om de leesbaarheid bij een laag gezichtsvermogen te verbeteren. (SITES-25316)
* De knop Bewerken kondigt nu de juiste actie aan voor schermlezers op de secundaire werkbalk. Als u deze activeert, wordt &#39;&#39;Bewerken&#39;&#39; weergegeven in plaats van de niet-verwante &#39;&#39;Voorvertoningsknop ingedrukt&#39;&#39;, waardoor verwarring tijdens toetsenbordnavigatie wordt voorkomen. (SITES-25320)
* De schuifregelaar Illustratie op de werkbalk Demografie geeft nu een juiste toegankelijke naam weer. De lezers van het scherm kondigen &quot;het totaal van de Kar&quot;aan en de toespraak-input hulpmiddelen kunnen de controle door naam richten, verbeterend naleving WCAG 4.1.2 (Naam, Rol, Waarde). (SITES-25322)
* De schuifregelaar op de werkbalk Demografie blijft nu actief wanneer auteurs de waarde wijzigen met de pijltoetsen. De focus springt niet meer naar de knop Illustratie, dus gebruikers van het toetsenbord passen de waarde voortdurend aan en schermlezers geven elke wijziging aan. (SITES-25324)
* Zoek in Assets nu Helder opnieuw plaatsen bij 320 px (ongeveer 400% zoomen). Met het modale model blijven koppen, velden en handelingen leesbaar en niet-overlappend, zodat ontwerpers kunnen zoeken zonder horizontaal schuiven. (SITES-25330)
* Het deelvenster Assets in de editor volgt een logische focusvolgorde. Toetsenbordgebruikers gaan met de Tab-toets over elke miniatuur en hebben toegang tot de afsluitbesturingselementen van het deelvenster. De wijziging verwijdert skips en verbetert de naleving van WCAG 2.4.3. (SITES-25360)
* AEM werkt de **Lijsten** en **3&rbrace; knopen van Paragraaf &lbrace;in de rijke tekstredacteur van het Taser modale bij om hun uitgevouwen en doen ineenstorten staat bloot te stellen.** Met de knoppen schakelt u nu `aria-expanded` in en wordt de statuswijziging voor schermlezers aangekondigd. Auteurs krijgen duidelijke feedback en raden niet voordat ze de opmaakmenu&#39;s openen of sluiten. (SITES-25365)
* AEM kondigt de laadstatus aan in het modaal Teaser. Het modaal stelt nu een live statusbericht bloot terwijl de inhoud wordt geladen. NVDA en JAWS spreken dus &quot;Laden, een ogenblik geduld.&quot; Auteurs moeten duidelijke feedback ontvangen en geen interactie met het dialoogvenster krijgen voordat het klaar is. (SITES-25366)
* Verbetert statusoverseinen op het lusje van Activa van de de selectiedialoogdoos van de Verbinding. Wanneer een fout voorkomt, injecteert de component een leesbare statusupdate en houdt toetsenbordnadruk stabiel, latend NVDA/JAWS gebruikers onmiddellijk op de hoogte stellen. (SITES-25368)
* Het gedrag van de gebruikersinterface in het deelvenster Notitie voor zeer smalle viewports is gecorrigeerd. Bij 320 px, vulden de titel en de Add controle eerder; de toolbar stroomt nu opnieuw en bewaart duidelijke scheiding tussen elementen. Auteurs kunnen de besturingselementen zonder verlies van informatie of functie gebruiken. (SITES-25376)
* Vaste een het lopen foutenstaat in de **2&rbrace; Verbindingen &amp; Acties** tabel van de de dialoogdoos van de Taser **&lbrace;.** Nadat de auteurs **Call to action** en correcte lege of ongeldige gebieden toelaten, ontruimt het lusje zijn fout het stileren en pictogram en verwijdert `aria-invalid`. Schermlezers melden niet langer een fout wanneer de velden zijn gevalideerd. (SITES-25527)
* Foutafhandeling in Sites Admin-formulieren voldoet nu aan toegankelijkheidsverwachtingen. Wanneer validatie mislukt, wordt de fout direct weergegeven op de pagina, wordt de focus verplaatst naar een bruikbaar berichtdoel en wordt de tekst voor schermlezers beschikbaar gemaakt, zoals JAWS. (SITES-27138)
* Als u een map in Sites maakt, wordt nu een duidelijk bevestigingsprogramma weergegeven. JAWS kondigt het bericht via het live gebied aan, zodat auteurs direct toegankelijke feedback ontvangen na de actie. (SITES-27141)
* Probleem verholpen waarbij afbeeldingen in ontwerpdialoogvensters zonder alternatieve tekst werden weergegeven. Het dialoogvenster bevat nu waar nodig beschrijvende alt-tekst en lege alt voor louter visuele elementen, waarmee het gedrag voor JAWS en andere schermlezers wordt hersteld. (SITES-27153)
* Verbeterde foutafhandeling in ontwerpdialoogvensters. Wanneer een configuratiefout voorkomt, toont UI expliciete tekst en brengt een scherm-lezer aankondiging door als waakzaam gebied teweeg. Auteurs ontvangen direct feedback en kunnen het probleem verhelpen zonder context te verliezen. (SITES-27155)
* Probleem met toegankelijkheid van opnieuw plaatsen in Sites-beheerder verholpen. Bij een zoompercentage van 400% in de browser overlapten de werkbalk- en rasterbesturingselementen en duwden ze toetshandelingen buiten het scherm, waardoor toetsenbordnavigatie en het gebruik van schermlezers werden geblokkeerd. De lay-out wordt nu op de juiste wijze opnieuw geplaatst, zodat de zoek-, filter- en actieknoppen zichtbaar en bedienbaar blijven bij een zoompercentage van 400%. (SITES-27238)
* Gecorrigeerd laag contrast in het slotstatusbericht dat wordt weergegeven in de pagina Vergrendelen/Ontgrendelen-workflow. Het bericht voldoet nu aan een 4.5 :1 verhouding, die leesbaarheid en naleving ADA voor auteurs verbetert. (SITES-27270)
* Toegevoegde toegankelijke namen aan de controletekenpictogrammen in het **Effectieve de dialoogvakje van Toestemmingen**. JAWS kondigt nu de pictogrammen en hun betekenis aan, waardoor toetsenbordnavigatie en ADA-compatibiliteit worden verbeterd. (SITES-27272)
* Verborgen koptekstnavigatie heeft focus geaccepteerd en heeft zowel gebruikers met een visuele als schermlezer in verwarring gebracht. De update schakelt focus op samengevouwen besturingselementen uit en stelt alleen zichtbare items beschikbaar. Navigatie blijft voorspelbaar en voldoet aan WCAG 2.4.3. (SITES-35224)

* Probleem verholpen met de miniatuurpictogrammen van de map in Sites Admin om zich als decoratieve afbeeldingen te gedragen. De update verwijdert de afbeeldingsrol en past lege alt-tekst toe, zodat de ondersteunende hulpmiddelen pictogrammen negeren en alleen betekenisvolle labels lezen. (SITES-2852)
* Adobe heeft het kleurcontrast voor de tekst Verwijzingen op de homepage van Sites verhoogd. De tekst voldoet nu aan WCAG 2.1 AA met een verhouding van minstens 4.5 :1 en leest duidelijk op lichte thema&#39;s en heldere schermen. (SITES-24755)
* Het landmerk References rail kondigt de naam nu aan voor schermlezers. Het gebied stelt een unieke `aria-label` (&quot;References rail&quot;) bloot, die de landmerkennavigatie verbetert en het van andere gebieden onderscheidt. (SITES-24973)
* De RTE van de Beschrijving blokkeerde voorwaartse navigatie van het Lusje en brak dialoogstroom. Met deze correctie wordt de standaardverplaatsing van het toetsenbord hersteld. Auteurs gaan verder dan het veld met één tab en zorgen dat de selectievolgorde voorspelbaar blijft. (SITES-35228)
* Authoring-besturingselementen hadden niet-toegankelijke namen en onbewerkte pictogramtekst die door JAWS werd verward. Met deze correctie worden expliciete ARIA-labels en standaardrollen toegevoegd. Mededelingen hebben het juiste geluid en zijn afgestemd op de toegankelijkheidsverwachtingen. (SITES-35227)
* De vervolgkeuzelijst Categorieën bevatte een specifiek label, dus JAWS sprak een generiek &quot;menu voor afbeeldingsknoppen&quot;. De update noemt de controle &quot;Categorieën&quot;en bepaalt zijn rol. Gebruikers van schermlezers horen een nauwkeurig label en begrijpen welke opties beschikbaar zijn. (SITES-35226)
* In het dialoogvenster Eigenschappen wordt een gegevensraster weergegeven dat schermlezers als onbewerkte tekst behandelen. JAWS en NVDA hebben de focus gemist en hebben geen rijen en kolommen aangekondigd. Met deze correctie worden echte tabelsemantiek en ARIA-rollen toegevoegd. Schermlezers herkennen de tabel en volgen de focus op de juiste wijze. (SITES-35225)
* De teksteditor voor inhoudsfragmenten die met een afgebroken actiebalk is geladen. De geknipte pictogrammen en het overloopmenu werden onbereikbaar. De update corrigeert de lay-out, zodat de volledige werkbalk zichtbaar en toegankelijk blijft. (SITES-33005)
* Formuliervelden op het tabblad Standaard bevatten geen nuttige fouttekst. In het formulier worden nu duidelijke, inline berichten weergegeven en gekoppeld aan het veld voor schermlezers. Gebruikers van toetsenborden en ondersteunende hulpmiddelen krijgen direct hulp bij het herstellen van invoer. (SITES-32480)
* In het veld Multifield dat in een aangepaste component wordt gebruikt, worden pictogramknoppen zonder label en een inconsistente tabvolgorde weergegeven. JAWS/NVDA kondigde alleen &quot;knop&quot; aan of overgeslagen besturingselementen, waardoor de toetsenbordbewerking werd geblokkeerd. De update biedt beschrijvende namen voor Add, Remove en Move, normaliseert tabstops en kondigt lijsupdates aan om aan de verwachtingen van ADA te voldoen. (SITES-30660)
* Met Snel publiceren wordt nu een duidelijk succesbericht geretourneerd. Het dialoogvenster wordt gesloten, een pop bevestigt de handeling en schermlezers kondigen het bericht aan, zodat auteurs het resultaat niet missen. (SITES-26912)
* Geen wijziging vereist. Adobe beoordeelde de claim dat het zoekpictogram tekst in de buurt overlapt. De koptekst bevat een label dat aan de klant is toegevoegd. Met vanilla AEM wordt alleen het pictogram weergegeven. Een schone instantie toont de correcte lay-out bij 100% gezoem, zodat werd de bug gesloten aangezien buiten werkingsgebied. (SITES-26910)
* Bij het maken van paginathema&#39;s wordt de focusstatus niet meer verborgen. De stijlen van Aquatic en van de Dringing geven een verenigbare hoogtepunt op het **Basis** lusje en aangrenzende lusjes tijdens toetsenbordnavigatie terug. Deze verandering herstelt voorspelbare, waarneembare nadrukterugkoppel voor slechtziende gebruikers. (SITES-26907)



#### Gebruikersinterface Admin{#sites-adminui-6524}

De scherm-lezer gebruikers ontvingen geen navigatiehulp in het **net van de Vervaging van het Systeem van de Catalogus**. JAWS kondigde alleen het celstandpunt aan en viel vervolgens stil. De versie voegt toegankelijke begeleiding en rollen toe, toelatend JAWS om de lijstcontext, het geselecteerde punt, en de vereiste pijl/ruimtecontroles te lezen. (SITES-30661)

#### Klassieke interface{#sites-classicui-6524}

Klassieke UI-selectievakjes hebben hun labels verloren en lege opties weergegeven. Dialoogvensters die ook gecodeerde HTML, zoals `<br>` , weergeven. De update herstelt checkbox etiketten en decodeert prijsverhoging, zodat de dialoogvakjes correct lezen. (SITES-31822)

<!--
#### [!DNL Content Fragments]{#sites-contentfragments-6524}
-->

#### [!DNL Content Fragments] - Beheer{#sites-admin-6524}

Haakjes in de naam van een inhoudsfragment hebben ertoe geleid dat het deelvenster Verwijzingen een verkeerd gebruik heeft gerapporteerd. Auteurs zagen 0 zelfs wanneer andere fragmenten ernaar verwezen. De correctie corrigeert het parseren van paden voor &quot;(&quot; en &quot;)&quot; en oppervlakken het juiste aantal en de items zonder nul. (SITES-35078)


#### [!DNL Content Fragments] - Fragmenteditor{#sites-fragments-editor-6524}

* Unpublish failed for Content Fragments wiens DAM path ronde haakjes bevatte. De wizard Publicatie beheren herschreef &quot;(&quot; en &quot;)&quot; en brak het middelenpad. In de correctie blijven de tekens behouden en wordt het juiste item omgezet, zodat de handeling voor het ongedaan maken van de publicatie is voltooid. (SITES-35077)
* Als u een inhoudsfragment bewerkt en teruggaat naar de Assets-lijst, wordt het fragment of de hele map verborgen. De lijst is niet vernieuwd nadat de editor is gesloten. Met deze correctie wordt de lijst nu op betrouwbare wijze vernieuwd en blijft het bewerkte fragment zichtbaar zonder dat het opnieuw wordt geladen. (SITES-35374)

* De Inhoudsfragmenteditor kan de Polaris Asset Selector niet openen omdat het vereiste IMS-bereik is verwijderd. De moeilijke situatie herstelt het minimale werkingsgebied en herstelt de verbinding van de Levering. Het bladeren en selecteren van middelen werken opnieuw, zonder HTTP 500 fouten. (SITES-35837)

#### [!DNL Content Fragments] - GraphQL API {#sites-graphql-api-6524}

Na elke implementatie werden geldige GraphQL-query&#39;s geretourneerd `GraphQL_QueryValidationError` . Het eindpunt hield een stale schema tot de teams geheime voorgeheugens leegten of opnieuw begonnen. De moeilijke situatie verfrist het schema van GraphQL en het voortgeduurde-vraagregister tijdens plaatsing, die normale reacties onmiddellijk herstellen. (SITES-34301)

<!--
#### [!DNL Content Fragments] - GraphQL Query Editor{#sites-graphql-query-editor-6524}


#### [!DNL Content Fragments] - REST API{#sites-restapi-6524}


#### Component Console{#sites-component-console-6524}


#### Core Backend{#sites-core-backend-6524}


#### Core Components{#sites-core-components-6524}


#### Campaign integration{#sites-campaign-integration-6524}
-->


#### ContentHub {#sites-contenthub-6524}

ContextHub injecteert niet meer een tweede jQuery exemplaar op publicatiepagina&#39;s. De segment-motor cliëntbibliotheek laat de cq.shared gebiedsdeel vallen die jQuery 1.12.4 trok, zodat laden de plaatsen één verenigbare jQuery en front-end code betrouwbaar werken. (SITES-30404)

#### Ervaar fragmenten{#sites-experiencefragments-6524}

* De Fragmenten van de ervaring lokaliseren nu de getoonde waarschuwing wanneer geen configuratie van Adobe Target bestaat. Het bericht wordt weergegeven in de landinstelling van de auteur in plaats van in het Engels. Exporteer- en activeringsstappen worden dus goed gelezen voor algemene teams. (SITES-11868)
* Als u een variant van een ervaringsfragment publiceert, wordt nu een gelokaliseerde foutmelding weergegeven wanneer er geen cloudservice aan de wijziging is gekoppeld. Het bericht wordt in de gebruikersinterface weergegeven in de taal van de gebruiker in plaats van in een tekenreeks met alleen het Engels. (SITES-20293)
* Bij het exporteren van een Ervingsfragment naar Doel is het bestand vastgelopen met `Attempt to modify attribute at illegal index: -1` . De instrumentatie van vitals van het Web was in conflict met de exporteur en bedorven attributenbehandeling. Met de fix wordt de verwerking van kenmerken verhardd en wordt dat conflict verwijderd. Exporteren is voltooid en het fragment wordt weergegeven in Doel. (SITES-31891)

* De eigenschappen van het Fragment van de ervaring lokaliseren nu de **Verwijzingen** tabel. Labels en kolomkoppen zoals &quot;Pagina&quot;, &quot;Paginapad&quot; en &quot;Titel van variatie&quot; worden weergegeven in de taal van de auteur. Deze wijziging verwijdert alleen-Engelstalige tekenreeksen en zorgt ervoor dat de weergave van eigenschappen consistent blijft voor algemene teams. (SITES-11203)
* De **Variaties** > **creeer werkschema** toont nu volledige vertaaltekst. In het dialoogvenster worden lange tekenreeksen in de landinstelling afgehandeld door de inhoud op de juiste wijze om te buigen en te vergroten of te verkleinen. Zo worden bijgesneden of geknipte labels verwijderd. (SITES-19304)
* De eigenschappen van het Fragment van de ervaring lokaliseren nu de statusetiketten van Sociale Media. Auteurs zien statuswaarden zoals Gepost en Niet gepost in de geselecteerde taal voor alle landinstellingen. Deze wijziging verwijdert alleen-Engelstalige tekenreeksen die tijdens de revisie tot verwarring hebben geleid. (SITES-2014)

<!--
#### Foundation Components (Legacy){#sites-foundation-components-legacy-6524}
-->

#### Lanceringen{#sites-launches-6524}

* Het schrappen van een zeer grote Lancering bevriest de bewaarplaats. De baan stelde teveel verwijderingen in de rij en verhongerde andere verzoeken. Met de correctie worden nu batches verwijderd en worden de resultaten tussen de delen weergegeven. Opschonen wordt voltooid wanneer het systeem reageert. (SITES-32004)

* De Configuratie van de lancering > Eigenschappen toont het werkende Bedrijf en drop-down Bezit. **sparen** en **dicht** eert voltooide gebieden, en de bevestiging van de Titel brengt niet meer fouten op Bedrijf of Bezit teweeg. (CQ-4359853)
* Vereiste controles in IMS Configuration worden uitgevoerd bij update, niet alleen bij het maken. Lege waarden in velden zoals Client ID of Client Secret geven een fout weer en stoppen het opslaan totdat een geldige waarde is ingevoerd, waardoor hergebruik van de vorige waarde wordt voorkomen. (CQ-4359938)
* Bij het maken van de start worden vertaalde validatie- en fouttekenreeksen weergegeven. Berichten met alleen het Engels voor aanmaakfouten en ontbrekende bronpagina&#39;s worden niet meer weergegeven. Auteurs zien duidelijke, landspecifieke feedback tijdens het instellen van de opstartprocedure. (SITES-13085)
* Bij Promotie starten worden de pagina-eigenschappen `jcr:title` , `jcr:description` en `cq:redirectTarget` op de bronpagina bijgewerkt. De verandering verwijdert bezitsuitsluitingen in MSM rollout config en werkschemalogica. Campagnes, vertalingen en SEO houden consistente titels, beschrijvingen en omleidingen. (SITES-34509)
* Het bereik van de handeling Starten is genegeerd en bevat pagina&#39;s die hetzelfde bovenliggende element hebben als de doelsectie. De update dwingt subboomgrenzen af en bevordert slechts de gekozen pagina en zijn nakomelingen. Onverwante pagina&#39;s behouden hun bestaande inhoud. (SITES-34344)
* Correctie van geneste automatische promotie starten die bij Auteur is gestopt en de Publishing-laag heeft overgeslagen. Met Automatisch bevorderen voor het starten van een kind worden de bijgewerkte pagina&#39;s naar de geconfigureerde uitgevers gepubliceerd en wordt de volledige introductie volgens schema voltooid. (SITES-30420)

<!--
#### Link Checker{#sites-link-checker-6524}
-->

#### MSM - Actieve kopieën{#sites-msm-live-copies-6524}

* Bij een uitrol op mapniveau konden geen live kopieën worden gemaakt voor Experience Fragments onder die map. Individuele rollouts werkten, waardoor de bulkworkflows werden verbroken. Met de wijziging wordt de rollout van mappen uitgelijnd op het paginagedrag en worden relaties en verwijzingen verspreid over de substructuur. (SITES-35161)
* Na het schrappen van een component in Levend Exemplaar, **laat Overerving** met een fout van JavaScript breken toe en de component bleef mist tot een tweede poging. De update corrigeert het opnieuw laden na verwijdering om de juiste parameters te dragen en vervangt de verouderde waarschuwingsaanroep. Het dialoogvenster wordt geopend en bij de eerste poging wordt de overerving hersteld. (SITES-31387)
* De tovenaar van de Uitvoer stemde **later** zonder datum over. Auteurs hebben een introductie zonder een schema gemaakt en geavanceerd. De update dwingt datumselectie af en geeft een duidelijke aanwijzing weer. De **gaat** actie voort gehandicapt tot een datum bestaat. (SITES-31374)


#### Pagina-editor{#sites-pageeditor-6524}

* Als u de inhoudsstructuur op een pagina opent met een Personalization-container, wordt een leeg deelvenster en een null-reference-fout geretourneerd. Auteurs kunnen geen componenten kiezen of configureren. De update verwijdert de fout en schakelt de structuur- en componentinteractie opnieuw in. (SITES-34336)
* AEM 6.5 SP23 brak wijzeomschakeling in de Redacteur van de Pagina. Het klikken van **Lay-out**, **Ontwikkelaar**, of **het richten** verlaten de redacteur die in **wordt geplakt geeft** wijze uit en gooide een console `TypeError`. De update herstelt de wijzigingen in de werkbalkmodus en wist de fout. (SITES-34536)
* De Pagina-editor sprong weg van de invoegpositie wanneer auteurs componenten in lange containers toevoegden. In de update worden de timing en de afhandeling van de bedekking ingesteld. De mening houdt zijn plaats en de nieuwe component blijft in zicht en klaar om te vormen. (SITES-32621)
* Aangepaste labellabels zijn mislukt in de Pagina-editor en de gebruikersinterface heeft altijd &#39;Tags&#39; weergegeven. Het predikaat evalueert nu `fieldLabel` eerst en `labelText` seconde, dan past het gebrek toe. Auteurs zien het label dat ze instellen. (SITES-32278)
* Als u het filter Locatie in Sites annuleert, wordt het pictogram OmniSearch verkeerd uitgelijnd en overlapt u dit met de plaatsaanduidingstekst. Er kon niet op het pictogram worden geklikt. De correctie past het pictogram opnieuw aan en herstelt het raakgebied, zodat de muis en het toetsenbord beide zoekopdrachten activeren. (SITES-30946)
* Als u Developer kiest, is de pagina in een slechte staat gebleven en is het ontwerpen op die pagina geblokkeerd. Het deelvenster is verdwenen en de gebruikersinterface reageert niet meer. De update herstelt de mode-toggle logica en geheim voorgeheugenbehandeling, die de pagina editable houden en de gegevens van de Ontwikkelaar onmiddellijk tonen. (SITES-30922)
* Het klikken **Duidelijk** in **Tussenvoegsel Nieuwe Component** verwijdert niet de onderzoeksvraag en verliet de lijst die aan één enkel punt (Accordeon) wordt gefiltreerd. Met de correctie wordt de query opnieuw ingesteld en wordt de lijst vernieuwd. Alle toegestane componenten worden opnieuw weergegeven. (SITES-30921)

<!--
#### Replication{#sites-replication-6524}
-->

#### RTF-editor{#sites-rte-6524}

* In het volledige scherm verborgen de rijke tekstredacteur het resultaat van de Controle van de Spelling achter de dialoogdoos wanneer geen fouten bestonden. De update plaatst het resultatenvenster op de voorgrond en houdt berichten en suggesties zichtbaar. Auteurs controleren en accepteren correcties zonder het volledige scherm te verlaten. (SITES-32366)
* In afbeeldingen met rijke teksteditors wordt de geselecteerde uitlijning nu gerespecteerd. Auteurs instellen links, centreren of rechts in het dialoogvenster Afbeelding en de editor past die keuze consistent toe in de uitvoer. Met deze wijziging wordt ook het dialoogvenster Alt-tekst gestabiliseerd, zodat tekst en uitlijning worden opgeslagen en behouden blijven voor alle nieuwe bewerkingen. (SITES-30634)

#### Universele editor {#sites-universal-editor-6524}

Het vormen van de manager van de Authentificatie van het Teken van de Vraag verwarde gebruikers omdat de etiketten niet de gebieden aanpasten. De UI trok tekst van de weg en toonde de verkeerde namen. De moeilijke situatie herstelt duidelijke, nauwkeurige etiketten voor de dienstclassificatie en de opties van het vraagteken. (SITES-31305)


### [!DNL Assets]{#assets-6524}


#### [!DNL Dynamic Media]{#assets-dm-6524}

* De **Uitgezochte Duimnagel** optie voor video&#39;s gedraagt zich nu correct in AEM Assets - Dynamische Media. Met de klik wordt het dialoogvenster geopend en kunt u een miniatuur uit Assets selecteren. Zo voorkomt u het vorige gedrag bij klikken en verwijdert u alleen de beperking tot het uitnemen van videoframes. (ASSETS-58926)


### [!DNL Forms]{#forms-6524}

>[!NOTE]
>
>Correcties in [!DNL Experience Manager] Forms worden één week na de geplande releasedatum van [!DNL Experience Manager] Service Pack via een afzonderlijk invoegpakket geleverd. In dit geval worden de invoegpakketten op donderdag 4 december 2025 uitgebracht. Daarnaast wordt een lijst met Forms-correcties en -verbeteringen toegevoegd aan deze sectie.

<!--
#### Forms Designer 

#### Forms

#### Forms JEE 

#### Forms Captcha {#forms-captcha-6524} 

#### XMLFM {#forms-xmlfm-6524}

#### [!DNL Forms Designer] {#forms-designer-6524}

-->


### Stichting {#foundation-6524}


#### Apache Felix {#foundation-apachefelix-6524}

De Felix Web Console-bundel is bijgewerkt met FELIX-6747. Deze patch verbetert reactie behandeling die eerder paginerendering en authentificatie in de Console van het Web OSGi brak. De console laadt constant en werpt niet meer InlegalStateException ingangen in de logboeken. (NPR-42730)

<!--
#### Campaign{#foundation-campaign-6524}

#### Cloud Services{#foundation-cloudservices-6524}

#### Communities {#foundation-communities-6524}

#### Content distribution{#foundation-content-distribution-6524}

#### CRX {#foundation-crx-6524}
-->

#### Graniet{#foundation-granite-6524}

* Onbewerkte of Engels-slechts koorden verschijnen niet meer in **verwijdert de dialoogdoos van het Toegangsbeheer**. In het dialoogvenster wordt volledig gelokaliseerde inhoud in alle ondersteunde talen weergegeven voor consistente toegankelijkheid. (GRANITE-48479)
* Het Help-pictogram geeft nu een beknopt label weer aan ondersteunende hulpmiddelen. JAWS leest &quot;Help-knop&quot; en voegt geen overbodige &quot;menu&quot;-tekst meer toe. Deze update brengt de controle in overeenstemming met WCAG 4.1.2 en vereenvoudigt toetsenbord en scherm-lezer gebruik. (GRANITE-55360)
* Herstel de fabriek van de HTML manuscriptmotor na het elimineren van een gebiedsdeellijn in diensten OSGi. De omgevingen beginnen op een schone manier, HTML-rendering werkt in de verschillende pods van de auteur en beheerders ondervinden niet langer opstartfouten of ontbrekende scriptservices. (GRANITE-58276)

* Het vak Zoeken in koptekst bedekt niet langer het pictogram van een vergrootglas op de plaatsaanduidingstekst. De tijdelijke aanduiding wordt weergegeven met de juiste opvulling en blijft volledig leesbaar in alle browsers. (GRANITE-54391)
* Auteurs zien leesbare labels in de velden Automatisch aanvullen in plaats van onbewerkte waarden in het dialoogvenster. De implementatie houdt de waarde in JCR aan en verbetert de helderheid voor configuraties met één of meerdere selecties die dynamisch opties bron. (GRANITE-57615)
* De bewerkingsmodus blijft functioneel wanneer htmlLibraryManager.debug is ingesteld op true. De wijziging herstelt de juiste clientlib-resolutie en het laden, zodat ontwikkelaars de foutopsporingsprogramma&#39;s van HTML Library Manager tijdens het ontwerpen kunnen gebruiken. (GRANITE-58002)
* De bewerkingspagina van de replicatieagent genereert niet langer een JavaScript-fout in de klassieke gebruikersinterface. De pagina wordt geopend, alle tabbladen worden weergegeven en de agentinstellingen worden zonder consolefouten opgeslagen. (GRANITE-58302)
* Correcteerde gezondheid-status samenvoeging in het Overzicht van het Systeem. De weergave wordt nu bijgewerkt nadat afzonderlijke controles zijn uitgevoerd en het juiste aantal wordt weergegeven. De exploitanten zien &quot;O.K.&quot;wanneer de controles van de Veiligheid en van het Onderhoud overgaan, in plaats van een onjuiste &quot;2 fouten&quot;banner. (GRANITE-61482)
* De uitvoering van `CodeUpgradeTasks` is gestopt tijdens upgrades van AEM 6.5 LTS (Long Term Support). De upgrade gaat nu door zonder wijzigingen of herconfiguraties in de opslagplaats die door een taak worden geactiveerd. Met deze oplossing wordt het upgrademisico verminderd en vermijdbare downtime voorkomen. (GRANITE-61486)
* In de ontwerpdialoogvensters wordt in de vereiste velden nu één nauwkeurige validatiefout weergegeven. Het bericht gebruikt het eigen etiket van het gebied wanneer heden, en valt terug naar een generische herinnering wanneer geen etiket bestaat. Gedupliceerde en niet-overeenkomende berichten in verschillende velden worden niet meer weergegeven. (GRANITE-59531)
* In het dialoogvenster Wizard Pagina maken worden nu de vereiste velden voor elke interactie opnieuw gevalideerd, inclusief tabwijzigingen en bewerkingen met meerdere velden. De **creeer** knoopverblijven gehandicapt tot de auteurs alle vereiste input voltooien, en de tovenaar toont gealigneerde fouten voor ontbrekende waarden. (GRANITE-58826)

#### Integrations{#foundation-integrations-6524}

Het publiceren van AEM Target-activiteiten mislukt niet meer wanneer auteurs start- en einddatums instellen. De integratie verzendt norm-volgzame timestamps die de tijdzone omvatten, zodat verwerkt het Doel de activiteitenlading en voltooit de synchronisatie zoals verwacht. (CQ-4360733)

<!--
#### Jetty{#foundation-jetty-6524}
-->

#### Lokalisatie{#foundation-localization-6524}

* De lokalisatie in zh-CN verwijdert een dubbelzinnige uitdrukking in de verwijzing-verzamelende status die tijdens activaverrichtingen zoals Beweging wordt getoond. De gebruikersinterface geeft nu `正在获取对 [[0]] 项的引用` weer, zodat u over een nauwkeurige betekenis en consistente terminologie beschikt. (CQ-4354648)
* Als u een slimme verzameling maakt, worden opgeslagen zoektrefwoorden niet meer vertaald bij vernieuwen. De auteurs die Engelse termijnen ingaan zien dat die zelfde termijnen worden behouden en de inzameling blijft verenigbare resultaten terugkeren. (NPR-43158)
* Tekst van afgebroken knopinfo in het deelvenster Afbeelding is gecorrigeerd. De beschrijving &#39;Bijschrift weergeven als pop-up&#39; wordt volledig weergegeven in alle ondersteunde landinstellingen, wat de begeleiding voor niet-Engelse auteurs verbetert. (SITES-10490)
* In de weergave Sites Admin Column zijn gelokaliseerde labels in het Frans en Spaans afgebroken. &quot;Eindtijd&quot; en &quot;Uit-tijd&quot; leken afgekapt en tonen geen knopinfo. Adobe corrigeerde de vertalingen en herstelde de knopinfo bij aanwijzen, zodat de labels volledig werden gelezen. (SITES-31318)
* Het **de dialoogvakje van de Beweging** in Plaatsen toonde ruwe i18n sleutels in plaats van leesbare etiketten. Items zoals &quot;Verwijzen naar pagina&#39;s&quot;, &quot;Gemaakt op&quot;, &quot;Gemaakt door&quot; en &quot;Pad&quot; leken onjuist. De correctie koppelt het dialoogvakje aan de correcte woordenboeken en levert vertalingen, met een Engelse reserve. (SITES-30881)

<!--
#### Oak {#foundation-oak-6524}
-->

#### Platform{#foundation-platform-6524}

* Validatiefouten tonen nu duidelijke, beschrijvende tekst in plaats van alleen een pictogram. Schermlezers kondigen het bericht automatisch aan wanneer het wordt weergegeven, zodat gebruikers niet naar een pictogram hoeven te navigeren om te leren wat er mis ging. (CQ-4359152)


* De etiketten van de hand in de Bar van de Navigatie blijven niet meer op het scherm nadat de curseur zich van de controle beweegt. De gebruikersinterface verbergt deze knopinfo direct bij vervagen of met de muis uit, zodat visuele verwarring en klikfouten worden voorkomen. (CQ-4360030)
* In Sites wordt met werkbalkhandelingen niet langer een tweede pop-up gemaakt wanneer nogmaals wordt geklikt. Met de tweede klik sluit u de bestaande pop-up en laat u slechts één instantie zichtbaar, zodat overlappingen en afleiding worden voorkomen. (CQ-4360038)
* De verouderde copyrighttekst van 2024 wordt niet meer weergegeven. De Login pagina en de **Hulp** > **Ongeveer AEM** pop-up tonen 2025, en AEM leest programmatically het jaar om handredits te vermijden. (CQ-4360042)
* Wanneer u op knopinfo in de AEM-koptekstbalk klikt, wordt de onderliggende actie niet meer geactiveerd. Pop-ups worden alleen geopend wanneer de gebruiker op de werkelijke knop klikt. Hierdoor wordt voorkomen dat dialoogvensters per ongeluk met knopinfo werken. (CQ-4360105)
* Bij het omvergooien van jaren blijft de copyrighttekst verouderd. Het Login scherm en de **Hulp** > **Ongeveer AEM** dialoogdoos leiden het jaar van de systeemklok af en geven de bijgewerkte waarde terug telkens als UI laadt. (CQ-4360173)
* In-/uitschakelen van pop-ups in de kopbalk. Het klikken van de zelfde actie (bijvoorbeeld, **Onderzoek** of **Filter**) sluit open pop-up in plaats van het openen van een andere bekleding. Door deze wijziging worden pop-ups in een stapel voorkomen en wordt de focus naar het besturingselement voor koptekst teruggestuurd. (NPR-42891)
* Projecten en de kalenderweergave Inbox worden correct weergegeven. Wanneer u overschakelt naar een andere weergave, wordt de pagina niet meer leeg gemaakt. De kalender wordt geladen en er worden geplande items weergegeven. (NPR-42968)

<!--
#### Security{#foundation-security-6524}
-->


#### Sling{#foundation-sling-6524}

* Gecorrigeerde caching gedrag op SAML-Beschermde pagina&#39;s. AEM voegt het juiste cache-besturingselement toe en varieert de metagegevens voor geverifieerde sessies, zodat proxy&#39;s en de Dispatcher persoonlijke reacties in cache overslaan. Anonieme inhoud wordt nog steeds op de normale manier in cache opgeslagen, terwijl aanmeldingsweergaven gebruikersspecifiek blijven. (NPR-42640)

* Het platform verbetert de kernSling Motor van 2.16.2 aan 2.16.6. De nieuwere engine verhardt de invoervalidering en stabiliseert de aanvraag tot verwerking onder belasting. (NPR-43105)

#### SPA-editor {#foundation-spa-editor-6524}

Het aanzetten van het Verzenden van HoofdServlet **Controle inhoud-Type** treedt gebroken `.model.json` uitvoer in AEM 6.5 SP21/22 met voeten. Verzoeken hebben HTML of fouten geretourneerd omdat de exportfunctie het type in de middelste keten heeft gespiegeld. De correctie verzendt JSON met het juiste type vanaf het begin, zodat `.model.json` werkt in auteur- en publicatieomgevingen. (SITES-32634)


#### Vertaling{#foundation-translation-6524}

* Er is een herindexbewerking toegevoegd voor de status van het vertaalproject. Beheerders kunnen de index voor het maken van back-ups opnieuw genereren wanneer de statusweergave niet meer synchroon is, de resultaten worden hersteld en Oak-traversale waarschuwingen worden verwijderd. De pagina wordt sneller geladen en de huidige taakstaten worden weergegeven. (NPR-42699)
* Probleem verholpen waarbij XLIFF-import melding maakte van succes, maar JSON-woordenboekbestanden ongewijzigd liet. De invoer richt nu de correcte i18n weg en handhaaft vertalingen zodat localisatierontrips zonder handredits volledig zijn. (NPR-42989)


* XML van vertaalregels werkt nu zoals geconfigureerd. Het vertaalframework houdt zich aan uitzonderingsregels en is tijdens het maken van taken correct van toepassing op `include` - en `exclude` -patronen. Met een vertaalaanvraag wordt uitgesloten inhoud niet meer verzonden. (NPR-42761)



#### Gebruikersinterface{#foundation-ui-6524}

* Probleem verholpen met een UI-regressie waarbij invoer werd uitgeschakeld in het dialoogvenster Adobe Stock-licentie. Het dialoogvenster gedraagt zich nu normaal, accepteert tekst in de vereiste velden en voltooit de licentiestroom voor de voorraadelementen vanuit de weergave Asset Details. (NPR-42748)

* Zichtbaarheid van groep opgelost in de auteuromgeving. De console van Groepen houdt niet meer bij ongeveer 41 resultaten op en keert de volledige reeks lidmaatschappen voor elke gebruiker terug. Deze moeilijke situatie herstelt verenigbaar gedrag na cumulatieve moeilijke situaties en handhaaft huidige veiligheid het verharden. (NPR-42749)


<!--
#### WCM{#foundation-wcm-6524}



#### Workflow{#foundation-workflow-6524}
-->




## Installeren [!DNL Experience Manager] 6.5.24.0{#install}

<!-- Remaining content from here to bottom stays the same except for version updating as needed as per update team feedback. -->

* [!DNL Experience Manager] 6.5.24.0 requires [!DNL Experience Manager] 6.5. Zie [&#x200B; verbeteringsdocumentatie &#x200B;](/help/sites-deploying/upgrade.md) voor gedetailleerde instructies. <!-- UPDATE FOR EACH NEW RELEASE -->
* De download van het Pak van de Dienst is beschikbaar op de Distributie van de Software van Adobe [&#x200B; &#x200B;](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.24.0.zip).
* Voor een plaatsing met MongoDB en veelvoudige instanties, installeer [!DNL Experience Manager] 6.5.24.0 op één van de instanties van de Auteur gebruikend de Manager van het Pakket.<!-- UPDATE FOR EACH NEW RELEASE -->

>[!IMPORTANT]
>
> Adobe raadt u niet aan het pakket [!DNL Experience Manager] 6.5.24.0 te verwijderen of te verwijderen. Daarom moet u, voordat u het pakket installeert, een back-up van de `crx-repository` maken voor het geval u deze moet terugdraaien. <!-- UPDATE FOR EACH NEW RELEASE -->

<!-- FORMS For instructions to install Service Pack for Experience Manager Forms, see [Experience Manager Forms Service Pack installation instructions](/help/release-notes/aem-forms-current-service-pack-installation-instructions.md). -->

### Het Service Pack installeren op [!DNL Experience Manager] 6.5{#install-service-pack}

1. Start de instantie opnieuw vóór de installatie als de updatemodus voor de instantie is geactiveerd (wanneer de instantie is bijgewerkt vanaf een eerdere versie). Adobe raadt aan de toepassing opnieuw te starten als de huidige uptime voor een instantie hoog is.

1. Maak voordat u gaat installeren een momentopname of een nieuwe back-up van de [!DNL Experience Manager] -instantie.

1. Download het Sack van de Dienst van [&#x200B; Distributie van de Software &#x200B;](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.24.0.zip). <!-- UPDATE FOR EACH NEW RELEASE -->

1. Open Package Manager en selecteer vervolgens **[!UICONTROL Upload Package]** om het pakket te uploaden. Om meer te weten, zie [&#x200B; Manager van het Pakket &#x200B;](/help/sites-administering/package-manager.md).

1. Selecteer het pakket en selecteer vervolgens **[!UICONTROL Install]** .

1. Om de S3 schakelaar bij te werken, stop de instantie na installatie van het Service Pack, vervang de bestaande schakelaar met een nieuw binair dossier dat in de installatiemap wordt verstrekt, en begin de instantie opnieuw. Zie [&#x200B; de Opslag van Gegevens van Amazon S3 &#x200B;](/help/sites-deploying/data-store-config.md#upgrading-to-a-new-version-of-the-s-connector).

>[!NOTE]
>
>Het dialoogvakje op de Manager UI van het Pakket eindigt soms tijdens de installatie van het Pak van de Dienst. Adobe raadt u aan te wachten totdat de foutenlogboeken zich stabiliseren voordat u de implementatie opent. Wacht op de specifieke logboeken met betrekking tot het verwijderen van de updaterbundel alvorens wordt verzekerd dat de installatie succesvol is. Dit probleem doet zich doorgaans voor in de [!DNL Safari] -browser, maar kan soms ook in elke browser optreden.

**Automatische installatie**

Er zijn twee verschillende methoden die u kunt gebruiken om [!DNL Experience Manager] 6.5.24.0 te installeren. <!-- UPDATE FOR EACH NEW RELEASE -->

* Plaats het pakket in de map `../crx-quickstart/install` wanneer de server online beschikbaar is. Het pakket wordt automatisch geïnstalleerd.
* Gebruik [&#x200B; HTTP API van de Manager van het Pakket &#x200B;](/help/sites-administering/package-manager.md#package-share). Gebruik `cmd=install&recursive=true` om de geneste pakketten te installeren.

>[!NOTE]
>
>Experience Manager 6.5.24.0 biedt geen ondersteuning voor Bootstrap-installatie. <!-- UPDATE FOR EACH NEW RELEASE -->

**bevestigt de installatie**

Om de platforms te kennen die om met deze versie worden verklaard te werken, zie de [&#x200B; technische vereisten &#x200B;](/help/sites-deploying/technical-requirements.md).

1. Op de pagina met productinformatie (`/system/console/productinfo`) wordt de bijgewerkte versietekenreeks weergegeven `Adobe Experience Manager (6.5.24.0)` onder [!UICONTROL Installed Products] . <!-- UPDATE FOR EACH NEW RELEASE -->

1. Alle OSGi-bundels staan **[!UICONTROL ACTIVE]** of **[!UICONTROL FRAGMENT]** in de OSGi-console (Webconsole gebruiken: `/system/console/bundles`).

1. De OSGi-bundel `org.apache.jackrabbit.oak-core` is versie 1.22.20 of hoger (Webconsole gebruiken: `/system/console/bundles` ). <!-- OAK Oak oak VERSION -MAY- NEED TO BE UPDATED FOR EACH NEW RELEASE. CHECK WITH SAMEER DHAWAN -->

### Service Pack installeren voor [!DNL Experience Manager] Forms{#install-aem-forms-add-on-package}

Voor instructies om het Service Pack op Experience Manager Forms te installeren, zie [&#x200B; de installatieinstructies van het Pak van de Dienst van Experience Manager Forms &#x200B;](/help/release-notes/aem-forms-current-service-pack-installation-instructions.md).

>[!NOTE]
>
>De Adaptieve eigenschap van Forms, beschikbaar in [&#x200B; AEM 6.5 QuickStart &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/deploying/deploying/deploy), wordt ontworpen voor exploratie en evaluatiedoeleinden slechts. Voor productiegebruik is het van essentieel belang een geldige licentie voor AEM Forms te verkrijgen, aangezien voor de adaptieve Forms-functionaliteit een correcte licentie vereist is.

### GraphQL-indexpakket installeren voor Experience Manager-inhoudsfragmenten{#install-aem-graphql-index-add-on-package}

De klanten die GraphQL gebruiken moeten het [&#x200B; Fragment van de Inhoud van Experience Manager met het Pakket van de Index van GraphQL 1.1.1 &#x200B;](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/cfm-graphql-index-def-1.1.1.zip) installeren.

Zo kunt u de vereiste indexdefinitie toevoegen op basis van de functies die ze daadwerkelijk gebruiken.

Als u dit pakket niet installeert, kan dit leiden tot trage of mislukte GraphQL-query&#39;s.

>[!NOTE]
>
>Installeer dit pakket slechts eenmaal per instantie; het hoeft niet opnieuw te worden geïnstalleerd met elk Service Pack.

### UberJar{#uber-jar}

UberJar voor [!DNL Experience Manager] 6.5.24.0 is beschikbaar in de [&#x200B; Gemaakt Centrale bewaarplaats &#x200B;](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.5.24/). <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

Om UberJar in een Geweven project te gebruiken, zie [&#x200B; hoe te om UberJar &#x200B;](/help/sites-developing/ht-projects-maven.md) te gebruiken en de volgende gebiedsdeel in uw projectPOM te omvatten: <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

```shell
  <dependency>
  <groupId>com.adobe.aem</groupId>
  <artifactId>uber-jar</artifactId>
  <version>6.5.24</version>
  <scope>provided</scope>          
  </dependency>
```

>[!NOTE]
>
>UberJar en de andere verwante artefacten zijn beschikbaar op Centrale Bewaarplaats van de Bewaarplaats van Adobe Public Maven (`repo.adobe.com`). De naam van het hoofdbestand van UberJar wordt gewijzigd in `uber-jar-<version>.jar` . Er is dus geen `classifier` , met `apis` als waarde, voor de tag `dependency` .



## Verouderde en verwijderde functies{#removed-deprecated-features}

Zie [&#x200B; Vervangen en verwijderde eigenschappen &#x200B;](/help/release-notes/deprecated-removed-features.md) voor een gedetailleerde lijst van alle eigenschappen afgekeurd of verwijderd voor AEM 6.5.

### SPA-editor {#spa-editor}

[&#x200B; de Redacteur van het KUUROORD &#x200B;](/help/sites-developing/spa-overview.md) is afgekeurd voor nieuwe projecten die met versie 6.5.24 van AEM 6.5 beginnen. De redacteur van het KUUROORD blijft gesteund voor bestaande projecten, maar zou niet voor nieuwe projecten moeten worden gebruikt.

De voorkeurseditors voor het beheer van inhoud zonder kop in AEM zijn nu:

* [&#x200B; de Universele Redacteur &#x200B;](/help/sites-developing/universal-editor/introduction.md) voor het visuele uitgeven.
* [&#x200B; de Redacteur van het Fragment van de Inhoud &#x200B;](/help/sites-developing/universal-editor/introduction.md) voor op vorm-gebaseerde het uitgeven.

## Bekende problemen{#known-issues}

<!-- THESE KNOWN ISSUES CARRY OVER EACH RELEASE. THE "PRODUCT UPDATES TEAM" IS SUPPOSED TO VERIFY EACH ISSUE AND LET YOU KNOW IF ANYTHING NEEDS TO BE ADDED, DELETED, OR CHANGED IN THIS LIST. -->

* **kwestie met JSP scripting bundel in AEM 6.5.21-6.5.24 en AEM 6.5 LTS GA**
AEM 6.5.21 tot 6.5.24 en AEM 6.5 LTS GA worden geleverd met de `org.apache.sling.scripting.jsp:2.6.0` -bundel, die een bekende uitgave bevat. De kwestie komt typisch onder hoge lading voor wanneer de instantie van AEM vele gezamenlijke verzoeken behandelt.

  Wanneer dit probleem optreedt, kan een van de volgende uitzonderingen voorkomen in de foutenlogboeken naast verwijzingen naar `org.apache.sling.scripting.jsp:2.6.0` :

   * `java.io.IOException: classFile.delete() failed`
   * `java.io.IOException: tmpFile.renameTo(classFile) failed`
   * `java.lang.ArrayIndexOutOfBoundsException: Index 0 out of bounds for length 0`
   * `java.io.FileNotFoundException`

  Als deze fout optreedt, kunt u de AEM-instantie alleen opnieuw starten als de herstelmethode is uitgevoerd.

  Neem contact op met de klantenondersteuning van Adobe en raadpleeg deze releaseopmerking voor een oplossing.

* **Verwant aan Oak**
Van Service Pack 13 en hierboven, is het volgende foutenlogboek begonnen te verschijnen dat het persistentiegeheime voorgeheugen beïnvloedt:

  ```shell
  org.h2.mvstore.MVStoreException: The write format 1 is smaller than the supported format 2 [2.0.202/5]
  at org.h2.mvstore.DataUtils.newMVStoreException(DataUtils.java:1004)
      at org.h2.mvstore.MVStore.getUnsupportedWriteFormatException(MVStore.java:1059)
      at org.h2.mvstore.MVStore.readStoreHeader(MVStore.java:878)
      at org.h2.mvstore.MVStore.<init>(MVStore.java:455)
      at org.h2.mvstore.MVStore$Builder.open(MVStore.java:4052)
      at org.h2.mvstore.db.Store.<init>(Store.java:129)
  ```

  of

  ```shell
  org.h2.mvstore.MVStoreException: The write format 1 is smaller than the supported format 2 [2.1.214/5].
  ```

  U kunt deze uitzondering als volgt oplossen:

   1. De volgende twee mappen verwijderen uit `crx-quickstart/repository/`

      * `cache`
      * `diff-cache`

   1. Installeer het Service Pack of start Experience Manager as a Cloud Service opnieuw.
Er worden automatisch nieuwe mappen van `cache` en `diff-cache` gemaakt en er is geen uitzondering meer die gerelateerd is aan `mvstore` in de `error.log` .

* Werk uw GraphQL-query&#39;s bij die mogelijk een aangepaste API-naam voor uw inhoudsmodel hebben gebruikt om in plaats daarvan de standaardnaam van het inhoudsmodel te gebruiken.

* Een GraphQL-query kan de `damAssetLucene` index gebruiken in plaats van de `fragments` index. Deze handeling kan resulteren in GraphQL-query&#39;s die mislukken of die lang duren.

  `damAssetLucene` moet zijn geconfigureerd om de volgende twee eigenschappen op te nemen onder `/indexRules/dam:Asset/properties` om het probleem op te lossen:

   * `contentFragment`
      * `jcr:primaryType="nt:unstructured"`
      * `name="jcr:content/contentFragment"`
      * `propertyIndex="{Boolean}true"`
      * `type="Boolean"`
   * `model`
      * `jcr:primaryType="nt:unstructured"`
      * `name="jcr:content/data/cq:model"`
      * `ordered="{Boolean}true"`
      * `propertyIndex="{Boolean}true"`
      * `type="String"`

  Nadat de indexdefinitie is gewijzigd, is opnieuw indexeren vereist (`reindex` = `true`).

  Na deze stappen zouden de vragen van GraphQL sneller moeten presteren.

* Wanneer u probeert inhoudsfragmenten, sites of pagina&#39;s te verplaatsen, te verwijderen of te publiceren, is er een probleem wanneer verwijzingen naar inhoudsfragmenten worden opgehaald. De achtergrondquery is mislukt. De functionaliteit werkt dus niet.
U zorgt voor een correcte bewerking door de volgende eigenschappen toe te voegen aan het indexdefinitieknooppunt `/oak:index/damAssetLucene` (opnieuw indexeren is niet vereist):

  ```xml
  "tags": [
      "visualSimilaritySearch"
    ]
  "refresh": true
  ```

* Als u uw [!DNL Experience Manager] -instantie upgradet van 6.5.0 tot 6.5.4 naar het meest recente Service Pack op Java™ 11, ziet u `RRD4JReporter` uitzonderingen in het `error.log` -bestand. Start de instantie van [!DNL Experience Manager] opnieuw om de uitzonderingen te stoppen. <!-- THIS BULLET POINT WAS UPDATED AS PER CQDOC-20021, JANUARY 23, 2023 -->

* Gebruikers kunnen de naam van een map in een hiërarchie in [!DNL Assets] wijzigen en een geneste map publiceren naar [!DNL Brand Portal] . De titel van de map wordt echter pas bijgewerkt in [!DNL Brand Portal] als de hoofdmap opnieuw wordt gepubliceerd.

* De volgende fouten en waarschuwingsberichten kunnen worden weergegeven tijdens de installatie van [!DNL Experience Manager] 6.5.x.x:
   * &quot;Wanneer de Adobe Target-integratie is geconfigureerd in [!DNL Experience Manager] met de Target Standard API (IMS-verificatie), leidt het exporteren van Experience Fragments naar Target tot onjuiste aanbiedingstypen die worden gemaakt. In plaats van het type &quot;Experience Fragment&quot;/bron &quot;Adobe Experience Manager&quot; maakt Target verschillende aanbiedingen met het type &quot;HTML&quot;/bron &quot;Adobe Target Classic&quot;.
   * `com.adobe.granite.maintenance.impl.TaskScheduler`: Er zijn geen onderhoudsvensters gevonden in `granite/operations/maintenance` .
   * De validatie aan de adaptieve formulierserver-side mislukt wanneer statistische functies zoals SUM, MAX en MIN worden gebruikt (CQ-4274424).
   * `com.adobe.granite.maintenance.impl.TaskScheduler` : er zijn geen onderhoudsvensters gevonden in `granite/operations/maintenance` .
   * De hotspot in een interactieve afbeelding voor dynamische media is niet zichtbaar wanneer u een voorvertoning van het element weergeeft via de Shopable Banner-viewer.
   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]` : time-out die wacht tot de registerwijziging niet is geregistreerd.

* Vanaf AEM 6.5.15 heeft de Rhino JavaScript Engine die door de ```org.apache.servicemix.bundles.rhino``` -bundel wordt geleverd, een nieuw hoistinggedrag. De manuscripten die de strikte wijze (```use strict;```) gebruiken moeten hun correcte variabelen verklaren. Anders worden ze niet uitgevoerd en wordt er een runtimefout gegenereerd.

* Als u labelen van verwant kant-en-klare inhoud via een officieel updatepakket installeert, wordt de standaardinstelling van de eigenschap languages van het knooppunt `/content/cq:tags` hersteld. Deze actie is waar voor de Packs van de Dienst, de Pakketten van de Dienst van de Veiligheid, de Uitgebreide Packs van de Eigenschap, de Cumulatieve Packs van de Eigenschap, de flarden, etc. Daarom is het noodzakelijk om het uit de eigenschappen vóór installatie toe te voegen.

### Bekend probleem voor AEM Sites {#known-issues-aem-sites-6524}

Voorvertoning van inhoudfragmenten mislukt als gevolg van DoS-beveiliging voor een grote boomstructuur met fragmenten. Zie het [&#x200B; KB- artikel over Standaard de configuratieopties van de Vraag van GraphQL van de Uitvoerder &#x200B;](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-23945) (SITES-17934)

### Bekende problemen voor AEM Forms {#known-issues-aem-forms-6524}

>[!NOTE]
>
>Gebruik geen upgrade naar Service Pack 6.5.24.0 voor problemen zonder beschikbare hotfix. Dit kan leiden tot onverwachte fouten. Voer pas een upgrade uit naar Service Pack 6.5.24.0 nadat de vereiste hotfixes zijn uitgebracht.

#### Problemen met hotfixes beschikbaar {#aem-forms-issues-with-hotfixes}

Voor de volgende problemen is een hotfix beschikbaar voor downloaden en installatie. U kunt [&#x200B; downloaden en Hotfix &#x200B;](/help/release-notes/aem-forms-hotfix.md) installeren om deze kwesties op te lossen:

* **FORMS-20203**: Wanneer een gebruiker het kader van Struts van versie 2.5.x aan 6.x bevordert, ontbreekt UI van het Beleid in AEM Forms om alle configuraties, zoals de optie te tonen om een watermerk toe te voegen.

* **FORMS-20360**: Na bevordering aan het Pak van de Dienst van AEM Forms 6.5.24.0, ontbreekt de de omzettingsdienst ImageToPDF met de fout:
  ```17:15:44,468 ERROR [com.adobe.pdfg.GeneratePDFImpl] (default task-49) ALC-PDG-001-000-ALC-PDG-011-028-Error occurred while converting the input image file to PDF. com/adobe/internal/pdftoolkit/core/encryption/EncryptionImp```

* **FORMS-20478**: Wanneer het proberen om type 7/8 dossiers van TIFF in PDF om te zetten, ontbreekt het omzettingsproces met fout &quot;ALC-PDG-001-000-Image2Pdf mislukte omzetting, die door: com/sun/image/codec/jpeg/JPEGCodec&quot;en &quot;ALC-PDG-01 wordt veroorzaakt 6-003-Er is een onbekende/onverwachte fout opgetreden tijdens de nabewerking van PDF.&quot; Het systeem probeert opnieuw te proberen met TM ImageIO TIFF-decoder, maar uiteindelijk kan de taak niet worden voltooid.

* **FORMS-14521**: Als een gebruiker probeert om een ontwerp brief met opgeslagen gegevens van XML voor te vertonen, wordt het geplakt in `Loading` staat voor sommige specifieke brieven.

* AEM Forms bevat nu een upgrade van Struts-versie van 2.5.33 naar 6.x voor de formuliercomponent. Deze verbetering levert eerder gemiste veranderingen van Struts die niet inbegrepen in SP24 waren. De steun werd toegevoegd via a [&#x200B; Hotfix &#x200B;](/help/release-notes/aem-forms-hotfix.md) dat u kunt downloaden en installeren om steun voor de recentste versie van Struts toe te voegen.

#### Andere bekende problemen {#aem-forms-other-known-issues}

* Nadat u AEM Forms JEE Service Pack 21 (6.5.21.0) hebt geïnstalleerd, voert u de volgende stappen uit om het probleem op te lossen als u dubbele vermeldingen van Geode jars `(geode-*-1.15.1.jar and geode-*-1.15.1.2.jar)` onder de map `<AEM_Forms_Installation>/lib/caching/lib` (FORMS-14926) vindt:

   1. Stop de locators, als zij lopen.
   2. Stop de AEM-server.
   3. Ga naar de `<AEM_Forms_Installation>/lib/caching/lib` .
   4. Verwijder alle Geode-patchbestanden behalve `geode-*-1.15.1.2.jar` . Bevestig dat alleen de Geode-jars met `version 1.15.1.2` aanwezig zijn.
   5. Open de opdrachtprompt in de beheerdermodus.
   6. Installeer de Geode-patch met het `geode-*-1.15.1.2.jar` -bestand.

* Toen gebruikers van AEM 6.5 Forms Service Pack 18 of 19 aan Service Pack 20 of 21 bevorderden, ontmoetten zij een fout van de JSP compilatie. Door deze fout konden ze geen aangepaste formulieren openen of maken. Het veroorzaakte ook problemen met andere interfaces van AEM. Die interfaces omvatten de Redacteur van de Pagina, UI van AEM Forms, de redacteur van het Werkschema, en het Overzicht UI van het Systeem. (FORMS-15256)

  Voer de volgende stappen uit om een dergelijk probleem op te lossen:
   1. Navigeer naar de map `/libs/fd/aemforms/install/` in CRXDE.
   2. Verwijder de bundel met de naam `com.adobe.granite.ui.commons-5.10.26.jar` .
   3. Start de AEM-server opnieuw.

* In de Voorproef van de Druk van de Interactieve Communicatie Agent UI, wordt het muntsymbool (zoals het dollarteken $) inconsistent getoond voor alle gebiedswaarden. Deze wordt weergegeven voor waarden tot en met 999, maar ontbreekt voor waarden van 1000 en hoger. (FORMS-16557)
* Eventuele wijzigingen in de XDP van geneste lay-outfragmenten in een interactieve communicatie worden niet weerspiegeld in de IC-editor. (FORMS-16575)
* In de Voorproef van de Druk van de Interactieve Communicatie Agent UI, worden sommige berekende waarden niet correct getoond. (FORMS-16603)
* Wanneer de brief in de Voorproef van de Druk wordt bekeken, wordt de inhoud veranderd. Dat wil zeggen dat sommige spaties verdwijnen en dat bepaalde letters worden vervangen door `x` . (FORMS-15681)
* **FORMS-15428**: Na het bijwerken aan AEM Forms Service Pack 20 (6.5.20.0) met Forms toe:voegen-On, configuraties die op de dienst van de erfenisAdobe Analytics Cloud gebruikend op referentie-gebaseerde authentificatieophouden werkend vertrouwen. Hierdoor konden de analyseregels niet correct worden uitgevoerd.

* Wanneer een gebruiker een instantie WebLogic 14c vormt, ontbreekt de dienst PDFG in AEM Forms Service Pack 21 (6.5.21.0) op JEE die op JBoss® loopt toe te schrijven aan klasseconflicten die de bibliotheek SLF4J impliceren. De fout wordt als volgt weergegeven (CQDOC-22178):

  ```java
  Caused by: java.lang.LinkageError: loader constraint violation: when resolving method "org.slf4j.impl.StaticLoggerBinder.getLoggerFactory()Lorg/slf4j/ILoggerFactory;"
  the class loader org.ungoverned.moduleloader.ModuleClassLoader @404a2f79 (instance of org.ungoverned.moduleloader.ModuleClassLoader, child of 'deployment.adobe-livecycle-jboss.ear'
  @7e313f80 org.jboss.modules.ModuleClassLoader) of the current class, org/slf4j/LoggerFactory, and the class loader 'org.slf4j.impl@1.1.0.Final-redhat-00001' @506ab52
  (instance of org.jboss.modules.ModuleClassLoader, child of 'app' jdk.internal.loader.ClassLoaders$AppClassLoader) for the method's defining class, org/slf4j/impl/StaticLoggerBinder,
  have different Class objects for the type org/slf4j/ILoggerFactory used in the signature.
  ```

* FORMS-21378: Als validatie op de server is ingeschakeld, kunnen formulierverzendingen mislukken. Neem contact op met Adobe Support voor hulp als dit probleem zich voordoet.



## OSGi-bundels en inhoudspakketten inbegrepen{#osgi-bundles-and-content-packages-included}

De volgende tekstdocumenten maken een lijst van de bundels OSGi en de Pakketten van de Inhoud inbegrepen in deze [!DNL Experience Manager] 6.5 versie van het Service Pack:

* [&#x200B; Lijst van bundels OSGi inbegrepen in Experience Manager 6.5.24.0](/help/release-notes/assets/65240-bundles.txt) <!-- UPDATE FOR EACH NEW RELEASE -->
* [&#x200B; Lijst met inhoudspakketten die zijn opgenomen in Experience Manager 6.5.24.0](/help/release-notes/assets/65240-packages.txt) <!-- UPDATE FOR EACH NEW RELEASE -->

## Beperkte websites{#restricted-sites}

Deze websites zijn alleen beschikbaar voor klanten. Neem contact op met uw Adobe-accountmanager als u een klant bent en toegang nodig hebt.

* [&#x200B; download van het Product bij licensing.adobe.com &#x200B;](https://licensing.adobe.com/)
* [&#x200B; de Klantenondersteuning van Adobe van het Contact &#x200B;](https://experienceleague.adobe.com/en/docs/customer-one/using/home).

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager]  productpagina &#x200B;](https://business.adobe.com/products/experience-manager/adobe-experience-manager.html)
>* [[!DNL Experience Manager]  6.5 documentatie &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-65)
>* [&#x200B; Abonneren aan de updates van het de prioritaire product van Adobe &#x200B;](https://www.adobe.com/subscription/priority-product-update.html)
