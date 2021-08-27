---
title: '[!DNL Experience Manager] Opmerkingen bij de release van 6.5 servicepack'
description: Opmerkingen bij de release specifiek voor [!DNL Adobe Experience Manager] 6.5 service pack 10
docset: aem65
mini-toc-levels: 1
exl-id: 28a5ed58-b024-4dde-a849-0b3edc7b8472
source-git-commit: 9c262f57b3c3b7a1d2deaba78d13d02b74c5208d
workflow-type: tm+mt
source-wordcount: '3525'
ht-degree: 0%

---

# [!DNL Adobe Experience Manager] Opmerkingen bij de release van 6.5 servicepack {#aem-service-pack-release-notes}

## Gegevens vrijgeven {#release-information}

| Producten | [!DNL Adobe Experience Manager] 6,5 |
| -------- | ---------------------------- |
| Versie | 6.5.10.0. |
| Type | Service Pack-release |
| Date | 26 augustus 2021 |
| URL downloaden | [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.10.zip) |

## Wat is inbegrepen in [!DNL Adobe Experience Manager] 6.5.10.0 {#what-is-included-in-aem}

[!DNL Adobe Experience Manager] 6.5.10.0 omvat nieuwe eigenschappen, zeer belangrijke klant-gevraagde verhogingen, en prestaties, stabiliteit, en veiligheidsverbeteringen, die sinds de beschikbaarheid van 6.5 versie in April 2019 worden vrijgegeven. Het servicepack is geïnstalleerd op [!DNL Adobe Experience Manager] 6.5.

De belangrijkste eigenschappen en de verhogingen die in [!DNL Adobe Experience Manager] 6.5.10.0 worden geïntroduceerd zijn:

* **Verbeterde  [!DNL Content Fragment] modellen en Editor**: U kunt nu complexe en aangepaste modellen voor gestructureerde inhoud maken met behulp van geneste  [!DNL Content Fragment] modellen. Inhoudsstructuren worden gemoduleerd in basiselementen die zijn gemodelleerd als subfragmenten. Fragmenten op een hoger niveau verwijzen naar deze subfragmenten. Meer verbeteringen in gegevenstypen, zoals geavanceerde validatieregels, verbeteren de flexibiliteit van het modelleren van inhoud met [!DNL Content Fragments]. De [!DNL Experience Manager] [!DNL Content Fragment] redacteur steunt genestelde fragmentstructuren in een gemeenschappelijke redacteurszitting, met verhogingen zoals de mening van de boomstructuur en van labels voorzien broodkruimelnavigatie door fragmenthiërarchieën.

* **GraphQL API voor[!DNL Content Fragments]**: De nieuwe GraphQL API is de standaardmethode om gestructureerde inhoud in formaat te leveren JSON. Met GraphQL-query&#39;s kunnen clients alleen de relevante inhoudsitems aanvragen om een ervaring weer te geven. Een dergelijke selectie voorkomt overlevering van inhoud (mogelijkheid met HTTP REST API&#39;s) waarvoor inhoud moet worden geparseerd op de client. GraphQL-schema&#39;s zijn afgeleid van [!DNL Content Fragment]-modellen en API-reacties worden gemaakt in JSON-indeling. In [!DNL Experience Manager] als [!DNL Cloud Service], blijven [GraphQL vragen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/admin/graphql-api-content-fragments.html#persisted-queries-caching) en proces geheim voorgeheugenvriendelijke verzoeken van de GET. Het is nog niet mogelijk in [!DNL Experience Manager] 6.5.10.0.

* **Hiërarchiebeheer en toekomstig voorbeeld**: Gebruikers hebben nu een interface voor toegang tot de inhoudsstructuren van hun  [!DNL Experience Manager] startpagina&#39;s, waaronder de mogelijkheid om pagina&#39;s toe te voegen en te verwijderen bij het starten. Deze functie verbetert de flexibiliteit van [!DNL Experience Manager] lanceringen aan de versies van de auteursinhoud die voor toekomstige publicatie worden gericht. [Met de ](/help/sites-authoring/working-with-page-versions.md#timewarp) functie Tijd verdraaien kunnen gebruikers de voorvertoning starten als toekomstige inhoudsstaten.

* **Verbonden elementen**:  [!DNL Experience Manager] breidt de  [!DNL Connected Assets] functionaliteit uit tot het gebruik van  [!DNL Dynamic Media] beelden in de toepasselijke kerncomponenten. Zie [Aangesloten elementen gebruiken](/help/assets/use-assets-across-connected-assets-instances.md).

* **Opties voor delen koppelen om elementen of uitvoeringen** te downloaden: Wanneer gebruikers elementen en verzamelingen delen als koppelingen, kunnen ze kiezen of ze het downloaden van originele elementen, hun vertoningen of beide toestaan met behulp van de gedeelde koppeling. Ook krijgen de gebruikers die de elementen downloaden die via de koppeling met hen worden gedeeld, de optie om alleen de oorspronkelijke elementen, alleen de uitvoeringen of beide te downloaden.

* **Gegenereerde** onderactiva beperken: Beheerders kunnen het aantal subelementen beperken dat  [!DNL Experience Manager] wordt gegenereerd voor samengestelde elementen zoals PDF-, PowerPoint-, InDesign- en toetsenbordbestanden. Zie [Samengestelde elementen beheren](/help/assets/managing-linked-subassets.md#generate-subassets).

* **Camera Raw ondersteuning**: Er is een nieuw  [!DNL Camera Raw] pakket beschikbaar dat  [!DNL Adobe Camera Raw] versie 10.4 ondersteunt. Zie  [Afbeeldingen verwerken met [!DNL Camera Raw]](/help/assets/camera-raw.md).

* De ingebouwde opslagplaats (Apache Jackrabbit Oak) wordt bijgewerkt naar 1.2.8.

* **Verbeteringen** voor toegankelijkheid:

   * [!DNL Dynamic Media] biedt veel toegankelijkheidsverbeteringen voor Viewers. Zie [[!DNL Dynamic Media] updates](#dynamic-media-65100).

   * Platform biedt enkele toegankelijkheidsverbeteringen. Zie [Platform-updates](#platform-65100).

* **Verbeterde gebruikerservaring**:

   * [!DNL Experience Manager] geeft rechtstreeks een lijst weer van alle inhoudsmodellen onder een map zonder dat de auteurs van de inhoud door de bestandsstructuur hoeven te navigeren. De functie vereist nu minder klikken en verbetert de efficiëntie van het ontwerpen.

   * Met een padveld in de [!DNL Sites]-editor kunnen auteurs elementen slepen van [!DNL Content Finder].

Voor een lijst van alle eigenschappen en verhogingen die in [!DNL Experience Manager] 6.5.10.0 worden geïntroduceerd, zie [nieuw in  [!DNL Adobe Experience Manager] 6.5 Service Pack 10](new-features-latest-service-pack.md).

Hier volgt een lijst met oplossingen die is opgenomen in [!DNL Experience Manager] 6.5.10.0.

### [!DNL Sites] {#sites-65100}

* De focus wordt verplaatst naar een ander veld wanneer u in het veld **[!UICONTROL Default Value]** onder het tabblad **[!UICONTROL Properties]** van de Inhoudsfragmenteditor (NPR-36992) typt.

* Wanneer het filtreren [!DNL Content Fragment] modellen onder een gespecificeerd weg, [!DNL Experience Manager] onderzoek keert alle knopen met `cq:Template` in plaats van het terugkeren van wegen en knopen slechts voor het [!DNL Content Fragment] model (SITES-1453) terug.
* [!DNL Content Fragments] retourneren  `null` als de status van mappen (SITES-1157).
* [!DNL Experience Manager] Hiermee kunnen gebruikers  [!DNL Content Fragment] Modellen niet uitschakelen en inschakelen (SITES-1088).
* Wanneer een gebruiker [!DNL Content Fragments] of media-elementen verplaatst, hernoemt of verwijdert, worden de [!DNL Content Fragments] waarnaar wordt verwezen niet automatisch bijgewerkt (SITES-196).
* Wanneer componenten van de ene pagina naar de andere worden geplakt, ontstaan er JavaScript-fouten (NPR-37030).
* Wanneer pagina-eigenschappen snel worden weergegeven, worden de Pagina-eigenschappen voor een andere pagina geopend (NPR-37025).
* Met het inhoudsfragment kan het inhoudsfragment zelf verwijzen. De kiezer ondersteunt de bewerking niet (NPR-36993).
* Na de bevordering aan de dienstpak 9, kunnen sommige gebruikers omslagen niet in Experience Manager bewegen en zien fouten in het logboeken (SITES-1481).
* Bij het aanpassen van de breedte van de component in de lay-outcontainer in de bewerkingsmodus wordt een flikkering waargenomen (NPR-36961).
* Bij het promoten van een lancering worden de wijzigingen in de gepropageerde lancering tweemaal doorgevoerd in de andere lanceringen. Als een gebruiker de dubbel-uitgerolde lancering bevordert, wordt de verdubbelde inhoud weerspiegeld op de bronpagina (NPR-36893).
* [!DNL Experience Manager] voegt een grijze rand toe aan sommige PNG-afbeeldingen met transparantie als u de afbeeldingen aan een pagina toevoegt met de component Image Core of als u de grootte wijzigt met de component Foundation Image (NPR-36879).
* [!DNL Experience Manager Sites] Admin UI met een hoog aantal malplaatjes resulteert in langzame navigatie (NPR-36870).
* De verbetering aan de dienstpak 9 verhindert authoring van een paar componenten. Met dit probleem kunnen gebruikers van [!DNL Sites] geen nieuwe pagina&#39;s maken (NPR-36857).
* Met de methode `ContextHubImpl` wordt een `ResourceResolver` gemaakt die niet is gesloten. Het leidt tot waarschuwingsberichten over lang lopend `ResourceResolver` en de dienst keert onverwachte resultaten op tijden terug (NPR-36853).
* Bij het synchroniseren van één live kopie van de eigenschappen van de blauwdrukpagina worden alle andere live kopieën ook gesynchroniseerd (NPR-36829, NPR-36522).
* Wanneer alleen XLS MIME-type wordt gebruikt, werkt de functie voor het uploaden van bestanden niet zoals verwacht (NPR-36785).
* Nieuwe tags met hoofdletters en kleine letters worden niet weergegeven in het tagveld in [!DNL Content Fragments] (NPR-36742).
* De optie Eén tekstelement bij het toevoegen van een [!DNL Content Fragment] zorgt ervoor dat tekst ontbreekt en creëert een oneven opmaak met betrekking tot lijsten en geneste lijsten (NPR-36565).
* Wanneer een auteur om het even welke component op een pagina aanwijst, schrapt de component, en voert ongedaan maakt op de schrappingsverrichting uit, wordt een fout ontmoet wanneer het proberen om de gegevens van de Chronologie voor de pagina in de plaatsenconsole (NPR-36528) te bekijken.
* Met de optie [!UICONTROL Save & Close] van de pagina-eigenschappen van de Bulk-editor worden wijzigingen opgeslagen, maar wordt de editor niet gesloten (NPR-36527).
* Wanneer een gebruiker een nieuwe component Text naar een pagina probeert te slepen, verdwijnt de component direct (NPR-36442).
* Wanneer een gebruiker typt in een tag op aanvraag die ruimte bevat (de tag die niet op het systeem aanwezig is) en op Enter drukt, wordt de tag onder het veld weergegeven. Wanneer de [!DNL Content Fragment] echter wordt opgeslagen en opnieuw geopend, wordt de tag op aanvraag niet weergegeven (NPR-36441).
* De sjabloon kan niet worden verwijderd wanneer de instantie wordt benaderd via de Dispatcher (NPR-36385).
* Wanneer een pagina wordt verplaatst, moet de browser handmatig worden vernieuwd om de wijzigingen weer te geven (NPR-36381).
* Wanneer u een component selecteert, kunt u deze knippen of kopiëren met Ctrl+X of Ctrl+C (en Command+X of Command+C op de Mac). Wanneer u op een andere component klikt, kunt u met de werkbalk plakken, maar niet met het toetsenbord (Ctrl+V of Command+V) (NPR-36379).
* Wanneer een gebruiker knipcomponenten probeert te verplaatsen met het schaarpictogram, treedt een consolefout op. Bovendien wordt bij het plakken slechts één component verplaatst (NPR-36378).
* [!DNL Experience Manager] heeft een vraag zonder index op WCM of berichten, vertraagt het prestaties (NPR-36303).
* Wanneer een auteur de overerving van de verwijderde overerfde component herstelt, kunt u alle pagina-inhoud synchroniseren. De auteurs van de inhoud moeten de volledige pagina synchroniseren, zelfs als de overerving slechts op één component wordt hersteld. Een volledige synchronisatie kan ertoe leiden dat ongewenste inhoud wordt gesynchroniseerd (NPR-34456, CQ-4310183).
* Live gebruik van een component op een instantie Auteur geeft niet alle exemplaren weer. Sommige componenten worden gebruikt in meer dan 1000 pagina&#39;s maar het rapport geeft slechts ongeveer 40 pagina&#39;s weer (CQ-4323724).
* Wanneer er een sitestructuur is met veel subpagina&#39;s, duurt het laden van de subpagina&#39;s in de kolomweergave meer tijd in Experience Manager 6.5.8 dan in Experience Manager 6.4.8.2 (CQ-4322766).
* De optie Alles uitschakelen werkt niet bij de optie &#39;Rollout Page&#39; (NPR-37070).
* Wanneer u een bestaande versie van een pagina met v3-componenten opent, wordt het dialoogvenster Pagina-eigenschappen niet geopend en wordt een `NullPointerException` geregistreerd (SITES-1830).

### [!DNL Assets] {#assets-65100}

De volgende problemen zijn opgelost in [!DNL Assets]:

* De waarde van de eigenschap `jcr:title` wordt niet bijgewerkt in de instantie Publiceren nadat een map is verplaatst. Als de naam van een map wordt gewijzigd en opnieuw wordt gepubliceerd binnen de auteur, wordt de eigenschapswaarde `jcr:title` van dezelfde waarde in de instantie Publiceren (NPR-36369) niet bijgewerkt.

* Als twee of meer elementen zijn geselecteerd en een of meer metagegevensvelden worden bewerkt, mislukt het opslaan met foutcode 500 in de Safari-browser (NPR-36413).

* Bulk-metagegevens kunnen niet worden geïmporteerd omdat de datumnotatie onjuist is (NPR-36428).

* Wanneer een selectie in [!UICONTROL Properties] pagina wordt gemaakt om meta-gegevens bij te werken, is de interface langzaam om te antwoorden wanneer er vele opties door schema (NPR-36430) worden verstrekt.

* Zoekfilter met de voorspelling [!UICONTROL Expiry Status] werkt niet (NPR-36436).

* Het pop-upmenu voor verschillende velden in [!UICONTROL Folder Metadata]-eigenschappen geeft niet de laatst geselecteerde waarden weer (NPR-36937, CQ-4314429).

* Als de gebruiker bij het zoeken naar bestanden en mappen een filter toepast en [!UICONTROL Files & Folders] selecteert, worden alleen de bestanden weergegeven, maar niet de map (CQ-4319543, NPR-36627).

* De werkbalkopties verschillen wanneer dezelfde verzameling in een map is geselecteerd en wanneer deze is geselecteerd uit een zoekresultaat (NPR-36620).

* De optie [!UICONTROL Quick Publish] is niet beschikbaar op de pagina met zoekresultaten (NPR-36904, CQ-4317748).

* Wanneer gebruikers een live kopie van een element maken zonder de extensie op te geven, is het live-kopiebestand na downloaden niet bruikbaar (NPR-36903, CQ-4326305).

* Wanneer een gebruiker als eigenaar van een kindomslag wordt toegevoegd, dan krijgt de gebruiker eigenaartoestemming van zijn ouderomslag en vandaar van de andere kindomslagen van de ouder. De gebruiker wordt ook niet verwijderd als eigenaar van een bovenliggende map wanneer deze probeert deze te verwijderen. (NPR-36801, CQ-4323737).

* [!DNL Experience Manager] genereert een uitzondering wegens onvoldoende geheugen wanneer u subelementen probeert te maken voor samengestelde elementen, zoals een PowerPoint-presentatie (NPR-36668).

* Wanneer gebruikers een element verplaatsen dat al in een gepubliceerde sitepagina wordt gebruikt, wordt de sitepagina opnieuw gepubliceerd, zelfs als de publicatieoptie niet is geselecteerd (NPR-36636, CQ-4323500).

* Wanneer u de functie voor het detecteren van het type Apache Tika MIME gebruikt, blijven de elementen die zijn geüpload met de methode `AssetManager.createAsset` een tijdelijk bestand met de naam `apache-tika-*.tmp` in de tijdelijke map staan. Dit tijdelijke bestand gebruikt alle beschikbare vrije schijfruimte (NPR-36545).

* Alle DRM-beveiligde middelen worden gedownload en de selectie van de gebruiker om specifiek middel te downloaden wordt niet gevolgd (CQ-4327422).

* Kan elementen niet naar `pathfield` in de gebruikersinterface slepen (NPR-36849).

* Wanneer u een element selecteert in de kolomweergave, verdwijnt het deelvenster met de elementdetails (NPR-36667).

### [!DNL Dynamic Media] {#dynamic-media-65100}

**Verbeteringen voor toegankelijkheid**

De volgende toegankelijkheidsverbeteringen zijn beschikbaar in [!DNL Dynamic Media Viewers].

* Schermlezers vertellen nu de tekst van de tijdelijke aanduiding voor het doorzoeken en toevoegen van het e-mailadres als een vereist veld voor het delen van elementen als een koppelingsdialoogvenster, en geven ook de knopinfo [!UICONTROL Please fill out this field] aan (CQ-4327761).

* Schermlezers vertellen nu correct de namen en doelen van verschillende velden in de [!UICONTROL Image Preset Editor] over het openen van gebruikersinterfacevelden met het toetsenbord (CQ-4325677).

* De toetsenbordfocus wordt nu op de juiste wijze verplaatst naar het zoektabblad van het dialoogvenster [!UICONTROL Viewer Presets] vanuit de elementenkiezer van de optie [!UICONTROL Rich Media Type] (CQ-4324736).

* Wanneer schermlezers in de formuliermodus navigeren met behulp van toetsenbordtoetsen, vertellen ze de labels die overeenkomen met opties voor verhogen en verlagen op het tabblad [!UICONTROL Create] van [!UICONTROL Image Presets] (CQ-4323900).

* Schermlezers kondigen nu de optie [!UICONTROL Search and Add Email Address] aan om elementen te delen als een dialoogvenster voor een koppeling (CQ-4323352).

* De toetsenbordfocus blijft behouden op de werkbalk wanneer u door elementen navigeert met behulp van toetsenbordtoetsen (CQ-4322037).

* Schermlezers vertellen nu de toegevoegde [!UICONTROL Edit] veldinformatie nadat ze de optie [!UICONTROL Add Crop] hebben geselecteerd op de pagina [!UICONTROL Responsive Image Crop] op [!UICONTROL Edit Image Processing Profile] (CQ-4290734).

* Op [!UICONTROL Edit Image Preset]- en [!UICONTROL Create Interactive Video]-pagina&#39;s kondigen schermlezers nu de paginakop correct aan wanneer ze door de pagina&#39;s navigeren met sneltoetsen voor koppen (CQ-4290730) (CQ-4290701).

* Schermlezers kunnen nu de verschillende gebieden van het scherm (zoals het rechterdeelvenster, het linkerdeelvenster, de actiewerkbalk, het liggend streepje van de viewerwerkbalk en het landmerk van de zoombare afbeelding) herkennen met behulp van de sneltoetsen voor landmarkeringen en regio&#39;s bij het navigeren op de volgende pagina&#39;s.

   * [!UICONTROL Viewer Preset Editor] (CQ-4290729)

   * [!UICONTROL Image Set Editor] (CQ-4290710)

   * [!UICONTROL Create Interactive Video] (CQ-4290702).

* Schermlezers kondigen nu de naam aan voor de optie Delen in het videoframe wanneer ze navigeren met de pijltoets-omlaag (CQ-4290728).

* Schermlezers vertellen nu de namen voor verschillende opties op de tabbladen [!UICONTROL Sprite] en [!UICONTROL Background] op het tabblad [!UICONTROL Appearance] in [!UICONTROL Viewer Preset Editor] (CQ-4290727).

* Verplichte velden, zoals het te bewerken veld [!UICONTROL Width], hebben nu op het tabblad [!UICONTROL Basic] van [!UICONTROL Edit Video Encoding] een sterretje (*) (CQ-4290725).

* Schermlezers kondigen nu het label voor de opties aan op de pagina [!UICONTROL Image Profiles] (CQ-4290723).

* Windows-gebruikers kunnen nu uit de uitgevouwen CSS-editor navigeren op [!UICONTROL Viewer Preset Editor] wanneer de CSS-editor de focus heeft (CQ-4290720).

* Op het tabblad [!UICONTROL Basic] van [!UICONTROL Edit Image Preset] wanneer u in de formuliermodus navigeert, vertellen schermlezers nu de labels voor verschillende bewerkingsvelden en -opties (CQ-4290717).

* Schermlezers vertellen nu de rol en status (geselecteerd of niet geselecteerd) van gebruikersinterface-opties in de linkernavigatie op de detailpagina van elementen (CQ-4290709).

* Schermlezers vertellen nu correct de status (geselecteerd of niet geselecteerd) en de koppeling voor de afbeeldingswisselaars op het tabblad [!UICONTROL Content] van [!UICONTROL Create Interactive Video] pagina (CQ-4290707).

* Schermlezers vertellen de naam, rol en status van verschillende segmenten in de tijdlijnschaal van de video nu correct wanneer ze navigeren met de pijltoets omlaag op de pagina [!UICONTROL Create Interactive Video] (CQ-4290706).

* Schermlezers vertellen nu de naam, de rol en de standaardstatus (geselecteerd of niet geselecteerd) en de eigenschap tijdens het navigeren door de opties op de pagina [!UICONTROL Create Interactive Video] (CQ-4290704).

* Schermlezers vertellen nu de naam, de rol en de standaardstatus (geselecteerd of niet geselecteerd) van de opties in de opties [!UICONTROL All Assets] en [!UICONTROL All Collections] tijdens het navigeren op de pagina [!UICONTROL Publish] (CQ-4290705).

* Wanneer u een niet-ondersteunde video-indeling (anders dan MP4) uploadt op de pagina [!UICONTROL Create Interactive Video], worden foutberichten weergegeven en aangekondigd in Experience Manager (CQ-4290700).

* Het contrast van de getallen (tijd in seconden) in de tijdlijnschaal op de pagina [!UICONTROL Create Interactive Video] voldoet nu aan de minimale vereiste lichtsterkteverhouding, zodat gebruikers met een beperkte kleurperceptie gemakkelijk kunnen lezen (CQ-4290699).

* Schermlezers kondigen nu het label voor het veld [!UICONTROL Product Name] aan bij het navigeren op de pagina [!UICONTROL Create Interactive Video] (CQ-4290697).

**Opgeloste problemen**

De volgende insectenmoeilijke situaties zijn beschikbaar in [!DNL Dynamic Media].

* Geüploade video&#39;s naar [!DNL Experience Manager] display `Process failed` nadat `dynamicmedia_scene7` runmode is ingeschakeld en synchronisatie is uitgeschakeld (CQ-4327791).

### Platform {#platform-65100}

De volgende verhogingen worden geleverd in dit de dienstpak:

* Wanneer een gebruiker een item selecteert in de structuurweergave, kondigen de schermlezers de selectie en de werkbalkopties bovenaan aan aan (NPR-36504).
* Sommige tekst- en regelnamen zijn beter leesbaar voor gebruikers met een visuele handicap, omdat de lichtsterkteverhouding voldoet aan de minimaal vereiste verhouding van 4,5:1 (NPR-36503).
* Wanneer een gebruiker de kalendercontroles gebruikt, bespreekt de het schermlezer de beschrijvende datum, maand, en weekdaginformatie. Wanneer een gebruiker een sneltoets voor de kalender gebruikt, beschrijft de schermlezer de wijziging in datum, maand en jaar (NPR-36498).
* Ondersteuning voor het uitvoeren van aangepaste JavaScript `Clientlibs` met behulp van ECMAScript 6-functies zonder dat dit in de strikte modus gebeurt. Met name wordt `emitUseStrict`-markering toegevoegd aan `GCCScriptProcessor` (NPR-36411).

De volgende insectenmoeilijke situaties maken deel uit van dit de dienstpak:

* Aangepaste gezondheidscontroles worden vaker uitgevoerd dan gepland (NPR-36985).
* De methode `Resourceresolver map` retourneert een onjuist resultaat voor aliaspagina&#39;s (NPR-36767).
* [!DNL Experience Manager] Het opstarten wordt vertraagd door werkstromen bij het laden (NPR-36615).

### Integrations {#integrations-65100}

* Experience Manager reageert niet wanneer het primaire knooppunt MongoDB overschakelt naar een ander knooppunt (NPR-36566).
* [!DNL Sling content distribution] mislukt bij het uitvoeren van de verwijderbewerking voor het verzamelingslid (NPR-36521, CQ-4323578).

### Gebruikersinterface {#user-interface-65100}

* Op het zijpaneel **[!UICONTROL References]** worden geen elementen en siteverwijzingen weergegeven (GRANITE-35078, GRANITE-34892).

### Vertaalprojecten {#translation-65100}

* Extra subpagina&#39;s in een taalkopie van een meervoudig vertaalproject worden verwijderd (NPR-36622).

### Workflow {#workflow-65100}

* Als de server een uit-van-bureaubericht ontvangt, rapporteert het geheugenalarm en houdt op antwoordend (NPR-36768).

### [!DNL Communities] {#communities-65100}

* Pagina&#39;s van communautaire sites worden geopend in de status `LoggedIn` voor anonieme gastgebruikers (NPR-36908).

* Wanneer de pagina **[!UICONTROL Community]** > **[!UICONTROL Ideas]** > **[!UICONTROL Comments]** meerdere pagina&#39;s bevat, werkt de paginanavigatie niet (NPR-36541).

<!--
Need to verify with Engineering, the status is currently showing as Resolved
-->


<!--
### [!DNL Brand Portal] {#brandportal-65100}

*
-->

### [!DNL Forms] {#forms-65100}

>[!NOTE]
>
>* [!DNL Experience Manager Forms] geeft toe:voegen-op pakketten één week na de geplande de versiedatum van het  [!DNL Experience Manager] Service Pack vrij.


### Handel {#commerce-65100}

* De waarde in het **[!UICONTROL Published By]** getoonde gebied is onjuist in de mening van de Kolom (NPR-36902).
* Wanneer een Catalogus wordt uitgerold, worden de nieuwe producten verkeerd gemerkt als gewijzigde producten (NPR-36666).
* Wanneer u een verwijderd product opnieuw maakt, wordt de productpagina niet opnieuw gemaakt (NPR-36665).
* Gewijzigde pagina&#39;s worden bijgewerkt, maar de bijbehorende gekoppelde producten worden niet bijgewerkt bij de uitrol van de catalogus (CQ-4321409, NPR-36422).
* De **[!UICONTROL Publish later]**- en **[!UICONTROL Unpublish later]**-workflows werken niet (CQ-4327679).

Zie [[!DNL Experience Manager] pagina met beveiligingsbulletins](https://helpx.adobe.com/security/products/experience-manager.html) voor informatie over beveiligingsupdates.

## 6.5.10.0 installeren {#install}

**Instellingsvereisten en meer informatie**

* Experience Manager 6.5.10.0 vereist Experience Manager 6.5. Zie [upgrade documentation](/help/sites-deploying/upgrade.md) voor gedetailleerde instructies.
* De download van het de dienstpak is beschikbaar op Adobe [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).
* Voor een plaatsing met MongoDB en veelvoudige instanties, installeer Experience Manager 6.5.10.0 op één van de instanties van de Auteur gebruikend de Manager van het Pakket.

>[!NOTE]
>
>Adobe raadt u niet aan het [!DNL Adobe Experience Manager] 6.5.10.0-pakket te verwijderen of te verwijderen.

### Het servicepack installeren {#install-service-pack}

Voer de volgende stappen uit om het servicepack te installeren op een [!DNL Adobe Experience Manager] 6.5-exemplaar:

1. Start de instantie opnieuw vóór de installatie als de updatemodus voor de instantie is geactiveerd (wanneer de instantie is bijgewerkt vanaf een eerdere versie). Adobe raadt aan de toepassing opnieuw te starten als de huidige uptime voor een instantie hoog is.

1. Maak voordat u gaat installeren een momentopname of een nieuwe back-up van uw [!DNL Experience Manager]-exemplaar.

1. Download het servicepakket van [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.10.zip).

1. Open Package Manager en klik **[!UICONTROL Upload Package]** om het pakket te uploaden. Zie [Pakketbeheer](/help/sites-administering/package-manager.md) voor meer informatie.

1. Selecteer het pakket en klik **[!UICONTROL Install]**.

1. Om de S3 schakelaar bij te werken, stop de instantie na installatie van het Service Pack, vervang de bestaande schakelaar met een nieuw binair dossier dat in de installatiemap wordt verstrekt, en begin de instantie opnieuw. Zie [Amazon S3 Data Store](/help/sites-deploying/data-store-config.md#upgrading-to-a-new-version-of-the-s-connector).

>[!NOTE]
>
>De dialoog over de Manager UI van het Pakket bestaat soms tijdens de installatie van het de dienstpak. Adobe raadt aan dat u op foutenlogboeken wacht om zich te stabiliseren alvorens tot de plaatsing toegang te hebben. Wacht op de specifieke logboeken met betrekking tot het verwijderen van de updaterbundel alvorens wordt verzekerd dat de installaties succesvol zijn. Dit probleem doet zich doorgaans voor in de [!DNL Safari]-browser, maar kan zich soms ook voordoen in elke browser.

**Automatische installatie**

Er zijn twee manieren om [!DNL Experience Manager] 6.5.10.0 op een werkende instantie automatisch te installeren:

A. Plaats het pakket in de map `../crx-quickstart/install` als de server online beschikbaar is. Het pakket wordt automatisch geïnstalleerd.

B. Gebruik [HTTP API van de Manager van het Pakket](/help/sites-administering/package-manager.md#package-share). Gebruik `cmd=install&recursive=true` zodat de geneste pakketten worden geïnstalleerd.

>[!NOTE]
>
>Adobe Experience Manager 6.5.10.0 ondersteunt geen Bootstrap-installatie.

**De installatie valideren**

1. Op de pagina met productinformatie (`/system/console/productinfo`) wordt de bijgewerkte versietekenreeks `Adobe Experience Manager (6.5.10.0)` weergegeven onder [!UICONTROL Installed Products].

1. Alle OSGi-bundels zijn **[!UICONTROL ACTIVE]** of **[!UICONTROL FRAGMENT]** in de Console OSGi (de Console van het Gebruik: `/system/console/bundles`).

1. De bundel OSGi `org.apache.jackrabbit.oak-core` is versie 1.22.3 of later (de Console van het Gebruik: `/system/console/bundles`).

Raadpleeg de [technische vereisten](/help/sites-deploying/technical-requirements.md) voor meer informatie over de platforms die zijn gecertificeerd voor deze release.

<!--

### Install Adobe Experience Manager Forms add-on package {#install-aem-forms-add-on-package}

>[!NOTE]
>
>Skip if you are not using Experience Manager Forms. Fixes in Experience Manager Forms are delivered through a separate add-on package a week after the scheduled [!DNL Experience Manager] Service Pack release.

1. Ensure that you have installed the Adobe Experience Manager Service Pack.
1. Download the corresponding Forms add-on package listed at [AEM Forms releases](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html#forms-updates) for your operating system.
1. Install the Forms add-on package as described in [Installing AEM Forms add-on packages](../forms/using/installing-configuring-aem-forms-osgi.md#install-aem-forms-add-on-package).

>[!NOTE]
>
>Experience Manager 6.5.10.0 includes a new version of [AEM Forms Compatibility Package](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html#aem-65-forms-releases). If you are using an older version of AEM Forms Compatibility Package and updating to Experience Manager 6.5.10.0, install the latest version of the package post installation of Forms Add-On Package.

### Install Adobe Experience Manager Forms on JEE {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Skip if you are not using AEM Forms on JEE. Fixes in Adobe Experience Manager Forms on JEE are delivered through a separate installer.

For information about installing the cumulative installer for Experience Manager Forms on JEE and post-deployment configuration, see the [release notes](jee-patch-installer-65.md).

>[!NOTE]
>
>After installing the cumulative installer for Experience Manager Forms on JEE, install the latest Forms add-on package, delete the Forms add-on package from the `crx-repository\install` folder, and restart the server.

-->

### UberJar {#uber-jar}

UberJar voor Experience Manager 6.5.10.0 is beschikbaar in [Maven Centrale bewaarplaats](https://repo1.maven.org/maven2/com/adobe/aem/uber-jar/6.5.10/).

Om UberJar in een Geweven project te gebruiken, zie [hoe te UberJar](/help/sites-developing/ht-projects-maven.md) gebruiken en omvat de volgende gebiedsdeel in uw projectPOM:

```shell
<dependency>
     <groupId>com.adobe.aem</groupId>
     <artifactId>uber-jar</artifactId>
     <version>6.5.10</version>
     <scope>provided</scope>
</dependency>
```

>[!NOTE]
>
>UberJar en de andere verwante artefacten zijn beschikbaar op Maven Central Repository in plaats van Adobe Public Maven repository (`repo.adobe.com`). De naam van het hoofdbestand van UberJar wordt gewijzigd in `uber-jar-<version>.jar`. Er is dus geen `classifier`, met `apis` als waarde, voor de tag `dependency`.

## Verouderde functies {#removed-deprecated-features}

Hieronder vindt u een lijst met functies en mogelijkheden die zijn gemarkeerd als verouderd met [!DNL Experience Manager] 6.5.7.0. Functies worden in eerste instantie gemarkeerd als afgekeurd en in een toekomstige versie verwijderd. Er is een alternatieve optie opgegeven.

Herzie als u een eigenschap of een vermogen in een plaatsing gebruikt. Ook, ben van plan om de implementatie te veranderen om een afwisselende optie te gebruiken.

| Gebied | Functie | Vervanging |
|---|---|---|
| Integraties | Het **[!UICONTROL AEM Cloud Services Opt-In]** scherm is verouderd omdat de integratie [!DNL Experience Manager] en [!DNL Adobe Target] in Experience Manager 6.5 wordt bijgewerkt. De integratie ondersteunt de Adobe Target Standard API. De API gebruikt authentificatie via Adobe IMS en [!DNL Adobe I/O] en steunt de groeiende rol van de Starten van Adobe aan instrument [!DNL Experience Manager] pagina&#39;s voor analyse en verpersoonlijking, de opt-in tovenaar functioneel irrelevant is. | Configureer systeemverbindingen, Adobe IMS-verificatie en [!DNL Adobe I/O]-integratie via de respectievelijke [!DNL Experience Manager]-cloudservices. |
| Connectors | De Adobe JCR-connector voor Microsoft® SharePoint 2010 en Microsoft® SharePoint 2013 is vervangen door Experience Manager 6.5. | N.v.t. |

## Bekende problemen {#known-issues}

* Als u uw [!DNL Experience Manager] instantie van versie 6.5 aan versie 6.5.10.0 bevordert, kunt u `RRD4JReporter` uitzonderingen in het `error.log` dossier bekijken. Start de instantie opnieuw om het probleem op te lossen.

* Als u [!DNL Experience Manager] 6.5 Service Pack 10 of een eerder servicepakket op [!DNL Experience Manager] 6.5 installeert, wordt de runtime-kopie van het aangepaste workflowmodel voor uw middelen (gemaakt in `/var/workflow/models/dam`) verwijderd.
Om uw runtime exemplaar terug te winnen, adviseert Adobe om het ontwerp-tijd exemplaar van het model van het douanewerkschema met zijn runtime exemplaar te synchroniseren gebruikend HTTP API:
   `<designModelPath>/jcr:content.generate.json`.

* Gebruikers kunnen de naam van een map in een hiërarchie in [!DNL Assets] wijzigen en een geneste map publiceren naar [!DNL Brand Portal]. De titel van de map wordt echter pas bijgewerkt in [!DNL Brand Portal] als de hoofdmap opnieuw wordt gepubliceerd.

* Wanneer een gebruiker een veld voor het eerst in een adaptief formulier configureert, wordt de optie voor het opslaan van een configuratie niet weergegeven in de eigenschappenbrowser. Als u een ander veld van het adaptieve formulier in dezelfde editor selecteert, wordt het probleem opgelost.

* De volgende fouten en waarschuwingsberichten kunnen tijdens de installatie van Experience Manager 6.5.x.x worden weergegeven:
   * &quot;Wanneer de integratie van Adobe Target in Experience Manager gebruikend de StandaardAPI van het Doel (authentificatie IMS) wordt gevormd, dan leidt het uitvoeren van de Fragmenten van de Ervaring naar Doel in verkeerde aanbiedingstypes die worden gecreeerd. In plaats van het type &quot;Experience Fragment&quot;/bron &quot;Adobe Experience Manager&quot; maakt Target verschillende aanbiedingen met het type &quot;HTML&quot;/source &quot;Adobe Target Classic&quot;.
   * `com.adobe.granite.maintenance.impl.TaskScheduler`: Geen onderhoudsvensters gevonden bij graniet/bediening/onderhoud.
   * De adaptieve servervalidatie van formulieren mislukt wanneer statistische functies zoals SUM, MAX en MIN worden gebruikt (CQ-4274424).
   * `com.adobe.granite.maintenance.impl.TaskScheduler` - Geen onderhoudsvensters gevonden bij graniet/bediening/onderhoud.
   * Hotspot in een interactieve Dynamic Media-afbeelding is niet zichtbaar wanneer u een voorvertoning van het element weergeeft via de Shopable Banner-viewer.
   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]` : Time-out bij wachten op wijziging van reg om niet-geregistreerd te voltooien.

## OSGi-bundels en inhoudspakketten inbegrepen {#osgi-bundles-and-content-packages-included}

De volgende tekstdocumenten maken een lijst van de bundels OSGi en de Pakketten van de Inhoud inbegrepen in [!DNL Experience Manager] 6.5.10.0:

* [Lijst van OSGi-bundels opgenomen in Experience Manager 6.5.10.0](assets/65100_bundles.txt)

* [Lijst met inhoudspakketten die zijn opgenomen in Experience Manager 6.5.10.0](assets/65100_packages.txt)

## Beperkte websites {#restricted-sites}

Deze websites zijn alleen beschikbaar voor klanten. Als u een klant bent en toegang nodig hebt, neemt u contact op met uw Adobe-accountmanager.

* [Productdownload op licensing.adobe.com](https://licensing.adobe.com/)
* Zie [hoe u contact opneemt met de klantenservice van Adobe](https://experienceleague.adobe.com/docs/customer-one/using/home.html).

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] Opmerkingen bij de release 6.5](/help/release-notes/release-notes.md)
>* [[!DNL Experience Manager] productpagina](https://business.adobe.com/products/experience-manager/adobe-experience-manager.html)
>* [[!DNL Experience Manager] 6.5 Documentatie](https://experienceleague.adobe.com/docs/experience-manager-65.html)
>* [Abonneren op updates van prioritaire Adobe-producten](https://www.adobe.com/subscription/priority-product-update.html)

