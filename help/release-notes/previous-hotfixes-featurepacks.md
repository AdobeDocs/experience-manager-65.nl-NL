---
title: '[!DNL Adobe Experience Manager] 6.5 de vorige de versienota''s van het de dienstpak'
description: Opmerkingen bij de release voor [!DNL Adobe Experience Manager] 6.5 de dienstpakken
contentOwner: AK
mini-toc-levels: 2
exl-id: aeed49a0-c7c2-44da-b0b8-ba9f6b6f7101
source-git-commit: 80f4e8c857fe9e0dfe344042fc1db81dde721e18
workflow-type: tm+mt
source-wordcount: '26073'
ht-degree: 0%

---

# Hotfixes en de Pakken van de Eigenschap inbegrepen in de vorige de dienstpakken {#hotfixes-and-feature-packs-included-in-previous-service-packs}

## [!DNL Adobe Experience Manager] 6.5.10.0. {#experience-manager-65100}

[!DNL Adobe Experience Manager] 6.5.10.0 omvat nieuwe eigenschappen, zeer belangrijke klant-gevraagde verhogingen, en prestaties, stabiliteit, en veiligheidsverbeteringen, die sinds de beschikbaarheid van 6.5 versie in April 2019 worden vrijgegeven. Het de dienstpak wordt geïnstalleerd op [!DNL Adobe Experience Manager] 6.5

De belangrijkste functies en verbeteringen die zijn geïntroduceerd in [!DNL Adobe Experience Manager] 6.5.10.0 zijn:

* **Verbeterd [!DNL Content Fragment] Modellen en Editor**: U kunt nu complexe en aangepaste modellen voor gestructureerde inhoud maken met behulp van geneste [!DNL Content Fragment] modellen. Inhoudsstructuren worden gemoduleerd in basiselementen die zijn gemodelleerd als subfragmenten. Fragmenten op een hoger niveau verwijzen naar deze subfragmenten. Meer functies voor gegevenstypen, zoals geavanceerde validatieregels, verbeteren de flexibiliteit van contentmodellering nog meer door [!DNL Content Fragments]. De [!DNL Experience Manager] [!DNL Content Fragment] de redacteur steunt genestelde fragmentstructuren in een gemeenschappelijke redacteurszitting, met verhogingen zoals de mening van de boomstructuur en van labels voorzien broodkruimelnavigatie door fragmenthiërarchieën.

* **GraphQL API voor[!DNL Content Fragments]**: De nieuwe GraphQL API is de standaardmethode om gestructureerde inhoud in formaat te leveren JSON. Met GraphQL-query&#39;s kunnen clients alleen de relevante inhoudsitems aanvragen om een ervaring weer te geven. Een dergelijke selectie voorkomt overlevering van inhoud (mogelijkheid met HTTP REST API&#39;s) waarvoor inhoud moet worden geparseerd op de client. GraphQL-schema&#39;s zijn afgeleid van [!DNL Content Fragment] modellen en API-reacties worden gemaakt in JSON-indeling. In [!DNL Experience Manager] als [!DNL Cloud Service], [GraphQL-query&#39;s blijven bestaan](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/admin/graphql-api-content-fragments.html#persisted-queries-caching) en verzoeken om cachevriendelijke GET verwerken. Het is nog niet mogelijk in [!DNL Experience Manager] 6.5.10.0.

* **GraphQL API voor[!DNL Content Fragments]**: Om GraphQL API te ondersteunen, zijn afbreekstreepjes niet meer toegestaan in het veld Eigenschap inhoudsfragmentmodel. GraphQL-query&#39;s kunnen ongewenste resultaten opleveren als een afbreekstreepje voorkomt in namen van eigenschappen van het Content Fragment Model.
Alleen de volgende tekens zijn toegestaan voor de naam van de eigenschap: A-Za-z0-9_. Een cijfer kan niet op de eerste positie staan.

* **Hiërarchiebeheer en voorvertoning in de toekomst**: Gebruikers hebben nu een interface voor toegang tot de inhoudstructuren van hun [!DNL Experience Manager] wordt gestart, inclusief de mogelijkheid om pagina&#39;s toe te voegen en te verwijderen bij het starten. Deze functie verbetert de flexibiliteit van [!DNL Experience Manager] wordt gestart bij de versie van de auteursinhoud die is bedoeld voor toekomstig publiceren. [Time-warp, functie](/help/sites-authoring/working-with-page-versions.md#timewarp) Hiermee kunnen gebruikers voorvertoningen starten als toekomstige inhoudsstaten.

* **Verbonden elementen**: [!DNL Experience Manager] breidt de [!DNL Connected Assets] functionaliteit voor het gebruik van [!DNL Dynamic Media] afbeeldingen in de toepasselijke kerncomponenten. Zie [Aangesloten elementen gebruiken](/help/assets/use-assets-across-connected-assets-instances.md).

* **Opties voor delen koppelen om elementen of vertoningen te downloaden**: Wanneer gebruikers elementen en verzamelingen delen als koppelingen, kunnen ze kiezen of ze het downloaden van originele elementen, hun vertoningen of beide toestaan met behulp van de gedeelde koppeling. Ook krijgen de gebruikers die de elementen downloaden die via de koppeling met hen worden gedeeld, de optie om alleen de oorspronkelijke elementen, alleen de uitvoeringen of beide te downloaden.

* **Gegenereerde subactiva beperken**: Beheerders kunnen het aantal subelementen beperken dat [!DNL Experience Manager] wordt gegenereerd voor samengestelde elementen zoals PDF-, PowerPoint-, InDesign- en toetsenbordbestanden. Zie [Samengestelde elementen beheren](/help/assets/managing-linked-subassets.md#generate-subassets).

* **Camera Raw ondersteuning**: Een nieuwe [!DNL Camera Raw] -pakket beschikbaar is dat ondersteuning biedt voor [!DNL Adobe Camera Raw] v10.4 Zie [afbeeldingen verwerken met [!DNL Camera Raw]](/help/assets/camera-raw.md).

* De ingebouwde opslagplaats (Apache Jackrabbit Oak) wordt bijgewerkt naar 1.2.8.

* **Verbeteringen voor toegankelijkheid**:

   * [!DNL Dynamic Media] biedt veel toegankelijkheidsverbeteringen voor Viewers. Zie [[!DNL Dynamic Media] updates](#dynamic-media-65100).

   * Platform biedt enkele toegankelijkheidsverbeteringen. Zie [Platform-updates](#platform-65100).

* **Verbeterde gebruikerservaring**:

   * [!DNL Experience Manager] geeft rechtstreeks een lijst weer van alle inhoudsmodellen onder een map zonder dat de auteurs van de inhoud door de bestandsstructuur hoeven te navigeren. De functie vereist nu minder klikken en verbetert de efficiëntie van het ontwerpen.

   * Pathfield in [!DNL Sites] de redacteur staat auteurs toe om activa van te slepen [!DNL Content Finder].

* Extra ondersteuning voor `GuideBridge#getGuidePath` API in [!DNL AEM Forms].

* U kunt de dienst van de Automatede form conversion nu gebruiken aan [PDF forms converteren in het Frans, Duits, Spaans, Italiaans en Portugees](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html#language-specific-meta-model) aan adaptieve formulieren.

* **Foutberichten in de browser Eigenschappen**: Foutberichten toegevoegd voor elke eigenschap in de browser Adaptive Forms Properties. Met deze berichten kunt u de toegestane waarden voor een veld beter begrijpen.

* **Ondersteuning voor het gebruik van de letterlijke optie voor het instellen van de waarde voor een JSON-typevariabele**: U kunt letterlijke optie gebruiken om waarde voor een JSON typevariabele in de vastgestelde veranderlijke stap van een AEM Werkstroom te plaatsen. Met de letterlijke optie kunt u een JSON opgeven in de vorm van een tekenreeks.

* [Updates van Platform](../forms/using/aem-forms-jee-supported-platforms.md): [!DNL Adobe Experience Manager Forms] op JEE heeft ondersteuning toegevoegd voor de volgende platforms:
   * [!DNL Adobe Acrobat 2020]
   * [!DNL Ubuntu 20.04]
   * [!DNL Open Office 4.1.10]
   * [!DNL Microsoft Office 2019]
   * [!DNL Microsoft Windows Server 2019]
   * [!DNL RHEL8]

Voor een lijst met alle nieuwe functies en verbeteringen in [!DNL Experience Manager] 6.5.10.0, zie [nieuwe functies in [!DNL Adobe Experience Manager] 6.5 Service Pack 10](new-features-latest-service-pack.md).

Hieronder volgt een lijst met oplossingen die u vindt in [!DNL Experience Manager] 6.5.10.0 release.

### [!DNL Sites] {#sites-65100}

* De focus verschuift naar een ander veld tijdens het typen in het dialoogvenster **[!UICONTROL Default Value]** onder de **[!UICONTROL Properties]** tabblad van de Inhoudsfragmenteditor (NPR-36992).

* Tijdens het filteren [!DNL Content Fragment] modellen onder een opgegeven pad; [!DNL Experience Manager] zoeken retourneert alle knooppunten met `cq:Template` in plaats van alleen paden en knooppunten te retourneren voor de [!DNL Content Fragment] model (SITES-1453).
* [!DNL Content Fragments] return `null` als de status van mappen (SITES-1157).
* [!DNL Experience Manager] laat gebruikers niet onbruikbaar maken en toelaten [!DNL Content Fragment] Modellen (SITES-1088).
* Wanneer een gebruiker beweegt, anders noemt, of schrapt [!DNL Content Fragments] of media-elementen, waarnaar wordt verwezen [!DNL Content Fragments] niet automatisch worden bijgewerkt (SITES-196).
* Wanneer componenten van de ene pagina naar de andere worden geplakt, ontstaan er JavaScript-fouten (NPR-37030).
* Wanneer pagina-eigenschappen snel worden weergegeven, worden de Pagina-eigenschappen voor een andere pagina geopend (NPR-37025).
* Met het inhoudsfragment kan het inhoudsfragment zelf verwijzen. De kiezer ondersteunt de bewerking niet (NPR-36993).
* Na de bevordering aan de dienstpak 9, kunnen sommige gebruikers omslagen niet in Experience Manager bewegen en zien fouten in het logboeken (SITES-1481).
* Bij het aanpassen van de breedte van de component in de lay-outcontainer in de bewerkingsmodus wordt een flikkering waargenomen (NPR-36961).
* Bij het promoten van een lancering worden de wijzigingen in de gepropageerde lancering tweemaal doorgevoerd in de andere lanceringen. Als een gebruiker de dubbel-uitgerolde lancering bevordert, wordt de verdubbelde inhoud weerspiegeld op de bronpagina (NPR-36893).
* [!DNL Experience Manager] voegt een grijze rand toe aan sommige PNG-afbeeldingen met transparantie als u de afbeeldingen aan een pagina toevoegt met de component Image Core of als u de grootte wijzigt met de component Foundation Image (NPR-36879).
* [!DNL Experience Manager Sites] Admin UI met een hoog aantal malplaatjes resulteert in langzame navigatie (NPR-36870).
* De verbetering aan de dienstpak 9 verhindert authoring van een paar componenten. Dit probleem is niet toegestaan [!DNL Sites] gebruikers om nieuwe pagina&#39;s te maken (NPR-36857).
* De `ContextHubImpl` methode maakt een `ResourceResolver` dat is niet gesloten. Het leidt tot waarschuwingsberichten over lang lopend `ResourceResolver` en de service retourneert onverwachte resultaten op momenten (NPR-36853).
* Bij het synchroniseren van één live kopie van de eigenschappen van de blauwdrukpagina worden alle andere live kopieën ook gesynchroniseerd (NPR-36829, NPR-36522).
* Wanneer alleen XLS MIME-type wordt gebruikt, werkt de functie voor het uploaden van bestanden niet zoals verwacht (NPR-36785).
* Nieuwe tags met hoofdletters en kleine letters worden niet weergegeven in het tagveld binnen [!DNL Content Fragments] (NPR-36742).
* De optie Eén tekstelement bij het toevoegen van een [!DNL Content Fragment] zorgt ervoor dat tekst ontbreekt en maakt een oneven opmaak met betrekking tot lijsten en geneste lijsten (NPR-36565).
* Wanneer een auteur om het even welke component op een pagina aanwijst, schrapt de component, en voert ongedaan maakt op de schrappingsverrichting uit, wordt een fout ontmoet wanneer het proberen om de gegevens van de Chronologie voor de pagina in de plaatsenconsole (NPR-36528) te bekijken.
* Pagina-eigenschappen Bulk Editor [!UICONTROL Save & Close] slaat wijzigingen op, maar sluit de editor niet (NPR-36527).
* Wanneer een gebruiker een nieuwe component Text naar een pagina probeert te slepen, verdwijnt de component direct (NPR-36442).
* Wanneer een gebruiker typt in een tag op aanvraag die ruimte bevat (de tag die niet op het systeem aanwezig is) en op Enter drukt, wordt de tag onder het veld weergegeven. Wanneer echter [!DNL Content Fragment] wordt opgeslagen en opnieuw geopend, wordt de tag op aanvraag niet weergegeven (NPR-36441).
* De sjabloon kan niet worden verwijderd wanneer de instantie wordt benaderd via de Dispatcher (NPR-36385).
* Wanneer een pagina wordt verplaatst, moet de browser handmatig worden vernieuwd om de wijzigingen weer te geven (NPR-36381).
* Wanneer u een component selecteert, kunt u deze knippen of kopiëren met Ctrl+X of Ctrl+C (en Command+X of Command+C in Mac). Wanneer u op een andere component klikt, kunt u met de werkbalk plakken, maar niet met het toetsenbord (Ctrl+V of Command+V) (NPR-36379).
* Wanneer een gebruiker knipcomponenten probeert te verplaatsen met het schaarpictogram, treedt een consolefout op. Bovendien wordt bij het plakken slechts één component verplaatst (NPR-36378).
* [!DNL Experience Manager] heeft een vraag zonder index op WCM of berichten, vertraagt het prestaties (NPR-36303).
* Wanneer een auteur de overerving van de verwijderde overerfde component herstelt, kunt u alle pagina-inhoud synchroniseren. De auteurs van de inhoud moeten de volledige pagina synchroniseren, zelfs als de overerving slechts op één component wordt hersteld. Een volledige synchronisatie kan ertoe leiden dat ongewenste inhoud wordt gesynchroniseerd (NPR-34456, CQ-4310183).
* Live gebruik van een component op een instantie Auteur geeft niet alle exemplaren weer. Sommige componenten worden gebruikt in meer dan 1000 pagina&#39;s maar het rapport geeft slechts ongeveer 40 pagina&#39;s weer (CQ-4323724).
* Wanneer er een sitestructuur is met veel subpagina&#39;s, duurt het laden van de subpagina&#39;s in de kolomweergave meer tijd in Experience Manager 6.5.8 dan in Experience Manager 6.4.8.2 (CQ-4322766).
* De optie Alles uitschakelen werkt niet bij de optie &#39;Rollout Page&#39; (NPR-37070).
* Wanneer u een bestaande versie van een pagina met v3-componenten opent, wordt het dialoogvenster Pagina-eigenschappen niet geopend en wordt een `NullPointerException` wordt geregistreerd (SITES-1830).

### [!DNL Assets] {#assets-65100}

De volgende problemen zijn opgelost in [!DNL Assets]:

* De waarde van de eigenschap `jcr:title` wordt niet bijgewerkt in de instantie Publiceren nadat een map is verplaatst. Als u de naam van een map wijzigt en de map opnieuw publiceert binnen de auteur, wordt de map niet bijgewerkt met `jcr:title` eigenschapswaarde van hetzelfde in de instantie Publiceren (NPR-36369).

* Als twee of meer elementen zijn geselecteerd en een of meer metagegevensvelden worden bewerkt, mislukt het opslaan met foutcode 500 in de Safari-browser (NPR-36413).

* Bulk-metagegevens kunnen niet worden geïmporteerd omdat de datumnotatie onjuist is (NPR-36428).

* Wanneer een selectie wordt gemaakt in het dialoogvenster [!UICONTROL Properties] pagina om meta-gegevens bij te werken, is de interface langzaam om te antwoorden wanneer er vele opties door schema (NPR-36430) worden verstrekt.

* Zoekfilter gebruiken [!UICONTROL Expiry Status] predikaat werkt niet (NPR-36436).

* Het pop-upmenu voor verschillende velden in [!UICONTROL Folder Metadata] eigenschappen geven de laatst geselecteerde waarden niet weer (NPR-36937, CQ-4314429).

* Als de gebruiker bij het zoeken naar bestanden en mappen een filter toepast en [!UICONTROL Files & Folders]worden alleen de bestanden weergegeven, maar niet de map (CQ-4319543, NPR-36627).

* De werkbalkopties verschillen wanneer dezelfde verzameling in een map is geselecteerd en wanneer deze is geselecteerd uit een zoekresultaat (NPR-36620).

* De [!UICONTROL Quick Publish] Deze optie is niet beschikbaar op de pagina met zoekresultaten (NPR-36904, CQ-4317748).

* Wanneer gebruikers een live kopie van een element maken zonder de extensie op te geven, is het live-kopiebestand na downloaden niet bruikbaar (NPR-36903, CQ-4326305).

* Wanneer een gebruiker als eigenaar van een kindomslag wordt toegevoegd, dan krijgt de gebruiker eigenaartoestemming van zijn ouderomslag en vandaar van de andere kindomslagen van de ouder. De gebruiker wordt ook niet verwijderd als eigenaar van een bovenliggende map wanneer deze probeert deze te verwijderen. (NPR-36801, CQ-4323737).

* [!DNL Experience Manager] genereert een uitzondering wegens onvoldoende geheugen wanneer u subelementen probeert te maken voor samengestelde elementen, zoals een PowerPoint-presentatie (NPR-36668).

* Wanneer gebruikers een element verplaatsen dat al in een gepubliceerde sitepagina wordt gebruikt, wordt de sitepagina opnieuw gepubliceerd, zelfs als de publicatieoptie niet is geselecteerd (NPR-36636, CQ-4323500).

* Wanneer u de functie voor het detecteren van het type Apache Tika MIME gebruikt, worden de elementen geüpload met de functie `AssetManager.createAsset` methode laat een tijdelijk bestand met de naam `apache-tika-*.tmp` in de tijdelijke map. Dit tijdelijke bestand gebruikt alle beschikbare vrije schijfruimte (NPR-36545).

* Alle DRM-beveiligde middelen worden gedownload en de selectie van de gebruiker om specifiek middel te downloaden wordt niet gevolgd (CQ-4327422).

* Kan elementen niet slepen naar `pathfield` in de gebruikersinterface (NPR-36849).

* Wanneer u een element selecteert in de kolomweergave, verdwijnt het deelvenster met de elementdetails (NPR-36667).

### [!DNL Dynamic Media] {#dynamic-media-65100}

**Verbeteringen voor toegankelijkheid**

De volgende toegankelijkheidsverbeteringen zijn beschikbaar in [!DNL Dynamic Media Viewers].

* Schermlezers vertellen nu de plaatsaanduidingstekst om het e-mailadres te zoeken en toe te voegen als een vereist veld voor het delen van elementen als een koppelingsdialoogvenster, en kondigen ook het dialoogvenster [!UICONTROL Please fill out this field] knopinfo (CQ-4327761).

* Schermlezers vertellen nu correct de namen en doelen van verschillende velden in het dialoogvenster [!UICONTROL Image Preset Editor] op het gebruiken van het toetsenbord om tot de gebruikersinterfacevelden toegang te hebben (CQ-4325677).

* Toetsenbordfocus wordt nu op de juiste manier verplaatst naar het zoektabblad van [!UICONTROL Viewer Presets] dialoogvenster van de elementkiezer van [!UICONTROL Rich Media Type] optie (CQ-4324736).

* Wanneer schermlezers in de formuliermodus navigeren met behulp van toetsenbordtoetsen, vertellen ze de labels die overeenkomen met de opties voor verhogen en verlagen op [!UICONTROL Create] tabblad van [!UICONTROL Image Presets] (CQ-4323900).

* Schermlezers kondigen nu de [!UICONTROL Search and Add Email Address] optie voor het delen van elementen als een koppelingsdialoogvenster (CQ-4323352).

* De toetsenbordfocus blijft behouden op de werkbalk wanneer u door elementen navigeert met behulp van toetsenbordtoetsen (CQ-4322037).

* Schermlezers vertellen nu over het toegevoegde item [!UICONTROL Edit] veldinformatie na het selecteren van de [!UICONTROL Add Crop] in de [!UICONTROL Responsive Image Crop] op [!UICONTROL Edit Image Processing Profile] pagina (CQ-4290734).

* Aan [!UICONTROL Edit Image Preset] en [!UICONTROL Create Interactive Video] De pagina&#39;s worden nu door schermlezers correct aangekondigd wanneer de paginakop door de pagina&#39;s wordt genavigeerd met behulp van sneltoetsen voor kopteksten (CQ-4290730)(CQ-4290701).

* Schermlezers kunnen nu de verschillende gebieden van het scherm (zoals het rechterdeelvenster, het linkerdeelvenster, de actiewerkbalk, het liggend streepje van de viewerwerkbalk en het landmerk van de zoombare afbeelding) herkennen met behulp van de sneltoetsen voor landmarkeringen en regio&#39;s bij het navigeren op de volgende pagina&#39;s.

   * [!UICONTROL Viewer Preset Editor] (CQ-4290729)

   * [!UICONTROL Image Set Editor] (CQ-4290710)

   * [!UICONTROL Create Interactive Video] (CQ-4290702).

* Schermlezers kondigen nu de naam aan voor de optie Delen in het videoframe wanneer ze navigeren met de pijltoets-omlaag (CQ-4290728).

* Schermlezers vertellen nu de namen van de verschillende opties in [!UICONTROL Sprite] en [!UICONTROL Background] tabs in [!UICONTROL Appearance] tab in [!UICONTROL Viewer Preset Editor] (CQ-4290727).

* Verplichte velden, zoals het veld dat moet worden bewerkt [!UICONTROL Width]in de [!UICONTROL Basic] tabblad van [!UICONTROL Edit Video Encoding] De pagina heeft nu een sterretje (*) (CQ-4290725).

* Schermlezers kondigen nu het label voor de opties aan op [!UICONTROL Image Profiles] pagina (CQ-4290723).

* Windows-gebruikers kunnen nu uit de uitgevouwen CSS-editor navigeren [!UICONTROL Viewer Preset Editor] wanneer de nadruk ligt op de CSS-editor (CQ-4290720).

* Aan [!UICONTROL Basic] tabblad van [!UICONTROL Edit Image Preset] Wanneer u in de modus Formulier navigeert, vertellen schermlezers nu de labels voor verschillende bewerkingsvelden en -opties (CQ-4290717).

* Schermlezers vertellen nu de rol en status (geselecteerd of niet geselecteerd) van gebruikersinterface-opties in de linkernavigatie op de detailpagina van elementen (CQ-4290709).

* Schermlezers vertellen nu correct de status (geselecteerd of niet geselecteerd) en de koppeling voor de afbeeldingswisseling in het dialoogvenster [!UICONTROL Content] tabblad van [!UICONTROL Create Interactive Video] pagina (CQ-4290707).

* Schermlezers vertellen de naam, rol en status van verschillende segmenten in de tijdlijnschaal van de video nu correct wanneer ze navigeren met de pijltoets omlaag op [!UICONTROL Create Interactive Video] pagina (CQ-4290706).

* Schermlezers vertellen nu de naam, de rol, de standaardstatus (geselecteerd of niet geselecteerd) en de eigenschap wanneer ze door de opties navigeren in [!UICONTROL Create Interactive Video] pagina (CQ-4290704).

* Schermlezers vertellen nu de naam, rol en standaardstatus (geselecteerd of niet geselecteerd) van opties in [!UICONTROL All Assets] en [!UICONTROL All Collections] opties bij het navigeren door de [!UICONTROL Publish] pagina (CQ-4290705).

* Wanneer u een niet-ondersteunde video-indeling (anders dan MP4) uploadt naar [!UICONTROL Create Interactive Video] pagina, toont en kondigt de Experience Manager foutenmeldingen (CQ-4290700) aan.

* Het contrast van de getallen (tijd in seconden) in de tijdlijnschaal op [!UICONTROL Create Interactive Video] pagina voldoet nu aan de minimale vereiste lichtsterkteverhouding, zodat gebruikers met een beperkte kleurperceptie gemakkelijk kunnen lezen (CQ-4290699).

* Schermlezers kondigen nu het label aan voor de [!UICONTROL Product Name] veld bij navigeren door de [!UICONTROL Create Interactive Video] pagina (CQ-4290697).

**Opgeloste problemen**

De volgende opgeloste problemen zijn beschikbaar in [!DNL Dynamic Media].

* Geüploade video&#39;s naar [!DNL Experience Manager] display `Process failed` na `dynamicmedia_scene7` De runmode is ingeschakeld en de synchronisatie is uitgeschakeld (CQ-4327791).

### Platform {#platform-65100}

De volgende verhogingen worden geleverd in dit de dienstpak:

* Wanneer een gebruiker een item selecteert in de structuurweergave, kondigen de schermlezers de selectie en de werkbalkopties bovenaan aan aan (NPR-36504).
* Sommige tekst- en regelnamen zijn beter leesbaar voor gebruikers met een visuele handicap, omdat de lichtsterkteverhouding voldoet aan de minimaal vereiste verhouding van 4,5:1 (NPR-36503).
* Wanneer een gebruiker de kalendercontroles gebruikt, bespreekt de het schermlezer de beschrijvende datum, maand, en weekdaginformatie. Wanneer een gebruiker een sneltoets voor de kalender gebruikt, beschrijft de schermlezer de wijziging in datum, maand en jaar (NPR-36498).
* Ondersteuning voor het uitvoeren van aangepaste JavaScript `Clientlibs` het gebruik van ECMAScript 6-functies zonder te voldoen aan de strikte modus. Specifiek: `emitUseStrict` markering wordt toegevoegd aan de `GCCScriptProcessor` (NPR-36411).

De volgende insectenmoeilijke situaties maken deel uit van dit de dienstpak:

* Aangepaste gezondheidscontroles worden vaker uitgevoerd dan gepland (NPR-36985).
* De `Resourceresolver map` methode retourneert een onjuist resultaat voor aliaspagina&#39;s (NPR-36767).
* [!DNL Experience Manager] Het opstarten wordt vertraagd door werkstromen bij het laden (NPR-36615).

### Integrations {#integrations-65100}

* Experience Manager reageert niet wanneer het primaire knooppunt MongoDB overschakelt naar een ander knooppunt (NPR-36566).
* [!DNL Sling content distribution] mislukt bij het uitvoeren van de verwijderbewerking voor het verzamelingslid (NPR-36521, CQ-4323578).

### Gebruikersinterface {#user-interface-65100}

* De **[!UICONTROL References]** op het zijpaneel worden geen elementen en siteverwijzingen weergegeven (GRANITE-35078, GRANITE-34892).

### Vertaalprojecten {#translation-65100}

* Extra subpagina&#39;s in een taalkopie van een meervoudig vertaalproject worden verwijderd (NPR-36622).

### Workflow {#workflow-65100}

* Als de server een uit-van-bureaubericht ontvangt, rapporteert het geheugenalarm en houdt op antwoordend (NPR-36768).

### [!DNL Communities] {#communities-65100}

* Pagina&#39;s met communautaire sites worden geopend in `LoggedIn` staat voor anonieme gastgebruikers (NPR-36908).

* Wanneer er meer dan één pagina in **[!UICONTROL Community]** > **[!UICONTROL Ideas]** > **[!UICONTROL Comments]** pagina, werkt de paginanavigatie niet (NPR-36541).

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
>* [!DNL Experience Manager Forms] geeft toe:voegen-on pakketten één week na gepland vrij [!DNL Experience Manager] Releasedatum van Service Pack.


[!DNL AEM 6.5.10.0 Forms] bevat de volgende opgeloste problemen:

* Wanneer u [!DNL AEM 6.5 Forms], worden de volgende bibliotheken van derden automatisch geïnstalleerd (CQDOC-18373):
   * [!DNL Microsoft Visual C++ 2008 Service Pack 1 (x86)]
   * [!DNL Microsoft Visual C++ 2010 Service Pack 1 (x86)]

**Adaptieve Forms**

* Als de validaties die op de veldwaarden in een adaptief formulier zijn uitgevoerd, succesvol zijn [!DNL AEM Forms] Kan het formuliergegevensmodel niet aanroepen (CQ-4325491).

* Wanneer u een taalwoordenboek aan een vertaalproject toevoegt en dan het project opent, [!DNL AEM Forms] geeft een foutbericht weer (CQ-4324933):

   ```TXT
   Uncaught TypeError: Cannot read property 'PROJECT_LISTING_PATH' of undefined
   at openButtonClickHandler (clientlibs.js:245)
   at HTMLButtonElement.onclick (clientlibs.js:258)
   ```

* Prestatieproblemen na installatie [!DNL AEM Forms] Service Pack 7 (CQ-4326828).

**Correspondentenbeheer**

* Vertraging bij de weergave van tekens in het dialoogvenster [!UICONTROL Data] en in de voorvertoning van de HTML letter (NPR-37020).

* Wanneer u een tekstdocumentfragment bewerkt, worden de nieuwe woorden na het opslaan van het fragment weergegeven als HTML-tags (NPR-36837).

* Kan de letters die zijn opgeslagen als concepten niet weergeven (NPR-36816).

* Wanneer u een tekstdocumentfragment bewerkt en vervolgens een voorvertoning van de letter bekijkt, geeft AEM Forms de expressietaal weer in de HTML-lettervoorvertoning (CQ-4322331).

* Problemen tijdens het renderen van gegevens met een sjabloon voor een zelfbedieningsbrief (NPR-37161).


**Interactieve communicatie**

* Een tabteken dupliceert tussen twee woorden telkens wanneer u een voorbeeld van een interactieve communicatie afdrukt na het bewerken van een tekstdocumentfragment (NPR-37021).

* [!DNL AEM Forms] geeft een fout weer wanneer u een tekstdocumentfragment opslaat dat de maximale groottebeperking overschrijdt (NPR-36874).

* Wanneer u een afbeelding toevoegt aan een interactieve communicatie, wordt na de afbeelding een extra leeg blok weergegeven (NPR-36659).

* Wanneer u alle tekst in een editor selecteert, kunt u de lettertypetekst niet wijzigen in Arial (NPR-36646).

* Wanneer u een URL maakt in een editor en de wijzigingen voorvertoont, wordt een zwarte achtergrond weergegeven in plaats van de URL-tekst (NPR-36640).

* Wanneer u tekst kopieert en plakt in een editor, kunnen er problemen optreden wanneer u het lettertype wijzigt in Arial voor opsommingstekens die beschikbaar zijn in het document (NPR-36628).

* Problemen met inspringing van opsommingstekens in de teksteditor (NPR-36513).

**Designer**

* De Reader van het scherm kan geen zwevende veldgegevens lezen die in het tekstlabel op de Master pagina of op subformulierpagina&#39;s in een dynamische PDF zijn geplaatst (CQ-4321587).

**Document Services**

* Wanneer u XDP-bestanden omzet in PDF-bestanden en vervolgens de resulterende PDF samenstelt, mislukken de PDF-generaties en wordt het volgende foutbericht weergegeven:

   ```TXT
   Caused by: com.adobe.fd.assembler.client.AssemblerException$ClientException: Document is in a disposed state!
   ```

**Forms Workflow**

* Kan geen formulier indienen bij een Workbench-proces na upgrade naar AEM Forms Service Pack 8 (CQ-4325846).

**HTML5 Forms**

* Wanneer u de waarde voor de `mfAllowAttachments` eigenschap as `True` in de CRX DE-opslagplaats `dataXml` wordt beschadigd bij het verzenden van het HTML5-formulier (NPR-37035).

* Wanneer u een XDP als HTML teruggeeft die `dataXml`, [!DNL AEM Forms] geeft een `Page Unresponsive` fout (NPR-36631).

### Handel {#commerce-65100}

* De waarde in het dialoogvenster **[!UICONTROL Published By]** weergegeven veld is onjuist in de kolomweergave (NPR-36902).
* Wanneer een Catalogus wordt uitgerold, worden de nieuwe producten verkeerd gemerkt als gewijzigde producten (NPR-36666).
* Wanneer u een verwijderd product opnieuw maakt, wordt de productpagina niet opnieuw gemaakt (NPR-36665).
* Gewijzigde pagina&#39;s worden bijgewerkt, maar de bijbehorende gekoppelde producten worden niet bijgewerkt bij de uitrol van de catalogus (CQ-4321409, NPR-36422).
* De **[!UICONTROL Publish later]** en **[!UICONTROL Unpublish later]** workflows werken niet (CQ-4327679).

Voor informatie over beveiligingsupdates raadpleegt u [[!DNL Experience Manager] beveiligingspagina met opsommingstekens](https://helpx.adobe.com/security/products/experience-manager.html).

## Bekende problemen in Experience Manager 6.5.10.0 {#known-issues}

* Als [!DNL Microsoft Windows Server 2019] ondersteunt niet [!DNL MySQL 5.7] en [!DNL JBoss EAP 7.1], [!DNL Microsoft Windows Server 2019] ondersteunt geen kant-en-klare installaties voor [!DNL AEM Forms 6.5.10.0].

* Als u een upgrade uitvoert op uw [!DNL Experience Manager] van 6.5 tot 6.5.10.0 versie, kunt u bekijken `RRD4JReporter` uitzonderingen in de `error.log` bestand. Start de instantie opnieuw om het probleem op te lossen.

* Als u [!DNL Experience Manager] 6.5 Service Pack 10 of een vorig de dienstpak op [!DNL Experience Manager] 6.5, de runtime kopie van het aangepaste workflowmodel voor uw middelen (gemaakt in `/var/workflow/models/dam`) wordt geschrapt.
Om uw runtime exemplaar terug te winnen, adviseert Adobe om het ontwerp-tijd exemplaar van het model van het douanewerkschema met zijn runtime exemplaar te synchroniseren gebruikend HTTP API:
   `<designModelPath>/jcr:content.generate.json`.

* Gebruikers kunnen de naam wijzigen van een map in een hiërarchie in [!DNL Assets] en publiceer een geneste map naar [!DNL Brand Portal]. De titel van de map wordt echter niet bijgewerkt in [!DNL Brand Portal] totdat de hoofdmap opnieuw wordt gepubliceerd.

* Wanneer een gebruiker een veld voor het eerst in een adaptief formulier configureert, wordt de optie voor het opslaan van een configuratie niet weergegeven in de eigenschappenbrowser. Als u een ander veld van het adaptieve formulier in dezelfde editor selecteert, wordt het probleem opgelost.

* De volgende fouten en waarschuwingsberichten kunnen tijdens de installatie van Experience Manager 6.5.x.x worden weergegeven:
   * &quot;Wanneer de integratie van Adobe Target in Experience Manager gebruikend de StandaardAPI van het Doel (authentificatie IMS) wordt gevormd, dan leidt het uitvoeren van de Fragmenten van de Ervaring naar Doel in verkeerde aanbiedingstypes die worden gecreeerd. In plaats van het type &quot;Experience Fragment&quot;/bron &quot;Adobe Experience Manager&quot; maakt Target verschillende aanbiedingen met het type &quot;HTML&quot;/bron &quot;Adobe Target Classic&quot;.
   * `com.adobe.granite.maintenance.impl.TaskScheduler`: Geen onderhoudsvensters gevonden bij graniet/bediening/onderhoud.
   * De validatie aan de adaptieve formulierserver-side mislukt wanneer statistische functies zoals SUM, MAX en MIN worden gebruikt (CQ-4274424).
   * `com.adobe.granite.maintenance.impl.TaskScheduler` - Geen onderhoudsvensters gevonden bij graniet/bediening/onderhoud.
   * Hotspot in een interactieve Dynamic Media-afbeelding is niet zichtbaar wanneer u een voorvertoning van het element weergeeft via de Shopable Banner-viewer.
   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]` : Time-out bij wachten op wijziging van reg om niet-geregistreerd te voltooien.

## [!DNL Adobe Experience Manager] 6.5.9.0. {#experience-manager-6590}

[!DNL Adobe Experience Manager] 6.5.9.0 omvat nieuwe eigenschappen, zeer belangrijke klant-gevraagde verhogingen, en prestaties, stabiliteit, en veiligheidsverbeteringen, die sinds de beschikbaarheid van 6.5 versie in April 2019 worden vrijgegeven. Het de dienstpak wordt geïnstalleerd op [!DNL Adobe Experience Manager] 6.5

De belangrijkste functies en verbeteringen die zijn geïntroduceerd in [!DNL Adobe Experience Manager] 6.5.9.0 zijn:

* [!DNL Experience Manager Sites] Met de Dynamic Media Foundation-component kunt u de optimalisatie voor apparaten met een hogere resolutie nu in- of uitschakelen wanneer u responsieve voorinstelling voor afbeeldingen of Slim uitsnijden gebruikt.

* Om de prestaties te verbeteren, `hidden=false` voorwaarde wordt verplaatst van JCR-query naar [!UICONTROL QueryBuilder] beoordelaar. Om te verifiëren dat een verborgen predikaat na de verandering werkt, [!DNL Experience Manager] controleert of er geen verborgen map wordt weergegeven.

* De mogelijkheid om verwijderde pagina&#39;s en boomstructuur te herstellen op een [!DNL Experience Manager Sites] pagina.

* Steun voor een nieuwe gebruiker om het toegangstoken te verfrissen gebruikend verfrist token voor de dienst van de brievenbusconfiguratie.

* [Ondersteuning voor SMTP XOAUTH2](/help/sites-administering/notification.md#setting-up-oauth) mechanisme voor de dienst van de postconfiguratie.

* Ondersteuning voor [!DNL MongoDB] versies 4.2 en 4.4.

* Namen die betrekking hebben op Hongkong, Macau en Taiwan worden bijgewerkt volgens de nieuwe naamconventies voor Chinese landinstellingen en regio&#39;s.

* Verbeterde toegankelijkheid in [!DNL Experience Manager] [[!DNL Assets]](#assets-accessibility-6590) en [[!DNL Dynamic Media]](#accessibility-dm-6590).

* Met de functie Smart Imaging DPR (Device Pixel Ratio) en de optimalisatie van de netwerkbandbreedte kunt u afbeeldingen van de beste kwaliteit efficiënt leveren. op apparaten met vertoningen met hoge resolutie en beperkte netwerkbandbreedte. Zie voor meer informatie en een tijdlijn [veelgestelde vragen over slimme beeldverwerking](/help/assets/imaging-faq.md).

* [!DNL Dynamic Media] levering (`fmt` URL (optie) ondersteunt de volgende generatie afbeeldingsindeling AVIF (AV1-afbeeldingsindeling). Zie voor meer informatie en een tijdlijn [fmt voor API voor beeldweergave en rendering](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-is-http-fmt.html).

* De mogelijkheid om een e-mailbericht naar een groep te verzenden met [!UICONTROL Assign Task] workflowstap.

* Capaciteit om een Interactief Communicatie ontwerp terug te winnen na het wijzigen van de bron Interactieve Communicatie.

* Aangepaste domeinnaam instellen voor het laden, renderen en valideren van de reCAPTCHA-service in [!DNL Experience Manager Forms].

* Verbeterde invoergegevens voor [!UICONTROL Invoke Form Data Model Service] workflowstap.

* Mogelijkheid om meerdere master pagina&#39;s te gebruiken in een sjabloon Document of Record in [!DNL Experience Manager Forms].

* Pagina-einden in document van record ondersteunen in [!DNL Experience Manager Forms].

* De ingebouwde opslagplaats (Apache Jackrabbit Oak) wordt bijgewerkt naar 1.2.7.

Voor een volledige lijst met functies en verbeteringen die zijn geïntroduceerd in [!DNL Experience Manager] 6.5.9.0, zie [nieuwe functies in [!DNL Adobe Experience Manager] 6.5 Service Pack 9](new-features-latest-service-pack.md).

>[!NOTE]
>
>Beginnend met Service Pack 9, [!DNL Experience Manager] klanten kunnen hun [!DNL Experience Manager] toepassingen met verspreiding van de [!DNL Azul Zulu] OpenJDK is een build die voldoet aan de standaarden van Java™ SE.
>Steun voor de [!DNL Azul Zulu] JDK&#39;s worden ook door Adobe aan de [!DNL Experience Manager] klanten.
>U kunt de relevante versies van de [!DNL Azul Zulu] JDK&#39;s van [Adobe-softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).
>De gebruiksrechten voor de Oracle Java™-technologie, zoals die door Adobe wordt gedistribueerd, lopen eind december 2022 af. [!DNL Experience Manager] klanten worden aangemoedigd om het gebruik voor de [!DNL Azul Zulu] JDK&#39;s laatst op deze datum. Voor meer informatie over het gebruik van de [!DNL Oracle Java™] technologie en [!DNL Azul Zulu] -technologie, raadpleegt u de bijbehorende [Veelgestelde vragen](https://experienceleague.adobe.com/docs/experience-manager-65/assets/adobe-azul-openjdk-license-agreement.pdf).

Hieronder volgt een lijst met oplossingen die u vindt in [!DNL Experience Manager] 6.5.9.0 release.

### [!DNL Sites] {#sites-6590}

* Gepubliceerde pagina&#39;s waarvoor de eigenschap Verificatievereiste is ingeschakeld, leiden niet om naar de aanmeldingspagina en retourneren het 404-foutbericht (NPR-36354).

* Wanneer u een hyperlink maakt, werkt de optie voor het doorzoeken van een koppeling niet in de tekstcomponent (NPR-35849).

* Een transversale vraag wordt teweeggebracht bij het gebruiken van `com.day.cq.wcm.commons.ReferenceSearch` API. Het beïnvloedt prestaties van [!DNL Experience Manager] server (NPR-36407).

* De geneste lay-outcontainer binnen een andere resized lay-outcontainer toont een onjuist aantal kolommen voor zijn kindcomponenten, die in deze componenten resulteren die niet aan het net worden gericht (NPR-36359).

* Externe Linkchecker geeft geldige externe koppelingen weer als ongeldige koppelingen (NPR-36289).

* Nadat u de referenties een tijdje hebt weergegeven, wordt in het venster Referenties een foutbericht weergegeven (NPR-36167).

* Wanneer het bewegen van een component, automatisch gecreeerd parsys, heeft niet `sling:resourceType` knooppunt (NPR-36165).

* Wanneer u probeert een livecopy te synchroniseren (tijdens het gebruik van uitrolconfiguraties) [!UICONTROL Activate on Blueprint activation] en [!UICONTROL De-activate on Blueprint activation]) als een component wordt verwijderd in de master livecopy, mislukt de synchronisatie en een `NullPointerException` wordt geregistreerd (NPR-36127).

* Wanneer een gebruiker in geïmproviseerde tekst typt voor tag (tag die niet op het systeem aanwezig is) en op Enter drukt, wordt de tag onder het veld weergegeven, maar wanneer het inhoudsfragment wordt opgeslagen en opnieuw geopend, verdwijnt de geïmproviseerde tag (NPR-36132).

* De status van asynchrone bewerkingen (NPR-36104) wordt niet weergegeven in Postvak In.

* Er wordt een dubbele component gemaakt na het herstellen van de overerving (NPR-36000).

* Wanneer u de `RemoteContentRenderingService`, het verzoek aan de `RemoteContentRendererRequestHandler.getRequest` bevat altijd de basispagina voor de  `ComponentExporter`, maar bevat niet de gevraagde pagina als deze niet is opgenomen in het hoofdmodel op basis van de ingestelde opties voor de transversale diepte en filteropties. Het verzoek moet altijd de gevraagde pagina omvatten zodat de SPA genoeg informatie heeft om een antwoord terug te geven (NPR-35961).

* onTime/offTime-items activeren/deactiveren niet op de verwachte onTime/offTime (NPR-35936).

* Wanneer u een pagina publiceert die een ervaringsfragment bevat dat geen `cq:lastModified` eigenschap, a `NullPointerException` treedt op (NPR-35914).

* Wanneer u probeert de grootte van een component in een container te wijzigen, is het niet mogelijk de oorspronkelijke grootte te herstellen. Wanneer de grootte van de container van de component wordt verkleind, is het niet mogelijk de grootte terug te zetten naar het origineel (NPR-35809).

* In het rollout dialoogvenster, dat in de redacteur of van het Levende Overzicht van het Exemplaar wordt teweeggebracht, zijn de statuspictogrammen voor losgemaakte, geschorste of niet gecreeerde pagina&#39;s verkeerd (NPR-35691).

* Op pagina&#39;s uitrollen van beheer voor meerdere sites hebben de eigenschappen master het selectievakje Uitrollout-pagina en subpagina&#39;s negeren (NPR-35634).

* De functie Herstelboomstructuur, beschikbaar in de klassieke gebruikersinterface, ontbreekt in Touch-gebruikersinterface (CQ-4315352, CQ-4309415).

* Problemen tijdens het omkeren van overerving en het uitrollen van een pagina op een [!DNL Experience Manager Sites] bladzijde (NPR-36033).

### [!DNL Assets] {#assets-6590}

De volgende verbeteringen in de gebruikerservaring zijn doorgevoerd in [!DNL Assets]:

* Elementen weergeven die niet zijn gesorteerd op basis van een van de [!UICONTROL Create], [!UICONTROL Modify], of [!UICONTROL Name] parameters, [!DNL Adobe Experience Manager] biedt een [!UICONTROL None] optie binnen [!UICONTROL Sort by] opties. De [!UICONTROL None] zorgt ervoor dat de elementen in de gebruikersinterface van Elementen (in de Kaart, Kolom, en mening) in de zelfde orde zijn zoals zij in knoop JCR (NPR-36356) bestaan.

* De e-mailid in kleine letters weergeven in de ACS API-reactie van [!DNL Adobe Experience Manager] een facultatieve instelling wordt ingevoerd; als de [!DNL Adobe Asset Link] gebruikers konden elementen niet inchecken als hun id niet alle tekens in kleine letters bevatte. De [!DNL Adobe Asset Link] -panel gebruikt de ACS API-reactie van [!DNL Adobe Experience Manager] (CQ-4317704).

De volgende toegankelijkheidsverbeteringen zijn beschikbaar in [!DNL Assets] als onderdeel van dienstenpakket 9:

Het contrast (met de achtergrond) van de volgende tekst en pictogrammen is verbeterd, zodat gebruikers met een beperkt gezichtsvermogen en kleurperceptie deze kunnen begrijpen:

* Titel van element op [!UICONTROL Properties] bladzijde (NPR-35967).
* Pictogrammen voor sterwaardering in [!UICONTROL Rating] secties op verschillende plaatsen (NPR-36009).
* Tekst op het middel en de omslagmening van de Kaart (NPR-35966).
* Plaatsaanduidingstekst op het tabblad [!UICONTROL Timeline] zicht (NPR-35965).
* Namen van activa in de zoekresultaten van activa (NPR-35964).
* Plaatsaanduidingstekst op het tabblad [!UICONTROL Link Sharing] dialoog (NPR-35963).
* [!UICONTROL Metadata], [!UICONTROL Status], en [!UICONTROL Other] tekst in [!UICONTROL List] in de [!UICONTROL View Settings] dialoog (NPR-35910).
* [!UICONTROL Location] en [!UICONTROL Type to search] plaatsaanduidingsteksten in algemeen onderzoek (NPR-35909).
* Pictogrammen uitvouwen en samenvouwen onder [!UICONTROL Content Tree] (NPR-35908).
* De [!UICONTROL Assets] tekst op de pagina waarop mappen met elementen worden weergegeven (NPR-35905).
* Tekst in [!UICONTROL Asset Metadata], [!UICONTROL Usage Statistics] binnen [!UICONTROL Overview] op de pagina met gegevens over activa (NPR-35904).
* Tekst voor sneltoetsen voor [!UICONTROL properties] en [!UICONTROL edit] opties op de pagina met elementdetails (NPR-35904).

De volgende opgeloste problemen zijn beschikbaar in [!DNL Assets] als onderdeel van dienstenpakket 9:

* De tags die zijn gemaakt vanuit een element met tagselectie in een [!UICONTROL Folder Metadata Schema] formulier wordt niet opgeslagen (NPR-36119).

* Wanneer een kleine ellips wordt gebruikt om elementen aan te brengen, overlapt de ellips met het nummer van de annotatie in de afdrukversie (NPR-36114).

* Soms, in de kolomweergave, [!DNL Experience Manager] veroorzaakt geen dubbel activaconflict wanneer een dubbel middel wordt geupload (NPR-36048).

* Het dialoogvenster Koppeling delen wordt niet gesloten als het wordt geopend en er geen wijzigingen worden aangebracht (NPR-36030).

* Wanneer er meerdere elementen zijn geselecteerd om de eigenschappen bij te werken, treedt soms een fout op of worden eigenschappen van een niet-geselecteerd element bijgewerkt (NPR-36002).

* Wanneer bij het uploaden van middelen witruimten worden toegevoegd aan het begin of einde van namen van elementbestanden, met resterende tekens die gelijk zijn aan de naam van een bestaand element in de gegevensopslagruimte, wordt het bestaande element vervangen zonder dat een fout wordt geregistreerd (NPR-36001).

* Wanneer video wordt afgespeeld op de pagina met elementdetails, werken de opties voor afspelen en pauzeren niet (NPR-35999).

* Wanneer het unpublishing van activa in bulk, Brand Portal een fout veroorzaakt die erop wijst dat het verzoek URI te lang is (NPR-35954).

* Wanneer een element met lange annotatietekst wordt afgedrukt, wordt de annotatietekst bijgesneden, zelfs als er ruimte beschikbaar is (NPR-35948).

* De optie om naar de volgende pagina te gaan is uitgeschakeld wanneer u de pagina selecteert in de weergave Sjablonen op de pagina Catalogus maken (CQ-4315462).

* Wanneer de werkstroom voor het bijwerken van elementen wordt gestart voor het video-element, wordt de pagina herhaaldelijk vernieuwd (CQ-4313375).

* DAM-mappen kunnen niet worden verwijderd of verplaatst en er wordt een uitzondering vastgelegd (NPR-35942).

### [!DNL Dynamic Media] {#dynamic-media-6590}

In [!DNL Adobe Experience Manager] 6.5.9.0. zijn de volgende toegankelijkheidsverbeteringen beschikbaar in [!DNL Dynamic Media]:

* Wanneer u het dialoogvenster opent om elementen toe te voegen met de toetsenbordtoetsen in [!UICONTROL Image Set] editor:
   * Schermlezers vertellen dat het dialoogvenster wordt geopend.
   * De toetsenbordfocus wordt naar het dialoogvenster verplaatst wanneer het wordt geopend.
   * De toetsenbordfocus gaat terug naar de optie Element toevoegen wanneer het dialoogvenster wordt gesloten (CQ-4312134).

* U kunt nu Hotspots op elementen toevoegen en bewerken met de sneltoetsen in de Hotspot-editor (CQ-4305965).

* U kunt hyperlink nu op hotspot plaatsen via Hotspot-beheer met behulp van toetsenbordtoetsen. De focus van de schermlezer gaat nu naar het veld om het URL-pad te bewerken en de optie voor het dialoogvenster Selectie openen (CQ-4290735).

* Het contrast (met de achtergrond) van tekst en besturingselementen op de pagina van de Editor voor de afbeeldingsset is verbeterd, zodat gebruikers met een beperkte gezichtsscherpte en kleurperceptie deze kunnen begrijpen (CQ-4290733).

* U kunt nu naar opties voor het delen van elementen navigeren in de Viewer Preset Editor en de uitgevouwen deeloptie samenvouwen met de toetsenbordtoetsen (CQ-4290724).

* U kunt nu met toetsenbordtoetsen navigeren en knopinfo weergeven in de informatiepictogrammen en waarschuwingspictogrammen op de tabbladen Standaard en Geavanceerd van de pagina Video coderen bewerken (CQ-4290722).

* Schermlezers vertellen nu de instructies voor verschillende velden op het tabblad Weergave en op het tabblad Gedrag in de Viewer Preset Editor (CQ-4290721).

* Wanneer u in de modus Formulier door de pagina Voorinstelling afbeelding bewerken navigeert, worden het doel en de namen van de verschillende velden en besturingselementen in schermlezers vermeld (CQ-4290717).

* Bij het navigeren door de detailpagina met elementen beschrijven schermlezers nu het doel van verschillende opties in Viewers (CQ-4290716).

* Contrast (met achtergrond) van de plaatsaanduidingstekst De optie Alle uitvoeringen in uitvoeringen van de pagina met elementdetails is verbeterd, zodat gebruikers met een beperkt gezichtsvermogen en kleurperceptie deze kunnen begrijpen (CQ-4290713).

* De visuele asterisk om verplicht gebied te betekenen wordt nu verstrekt op het gebied van de Titel van activa in de Redacteur van de Reeks van het Beeld, en de schermlezers kondigen de vereiste informatie voor het gebied aan (CQ-4290712).

* Schermlezers hebben nu toegang tot de pagina met elementdetails voor verschillende interactieve opties in Viewers (CQ-4290708) en kunnen het doel van deze opties nu vertellen.

Adobe Experience Manager 6.5.9.0 Middelen corrigeren de volgende problemen in [!DNL Dynamic Media]:

* Aangepaste ViewerVoorinstellingen en CSS worden niet gerepliceerd naar [!DNL Dynamic Media] wanneer [!DNL Dynamic Media] selectief wordt geactiveerd en door [default](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/dynamicmedia/config-dm.html#troubleshoot-dm-config) (NPR-36232).

* Wanneer u video-uitvoeringen wilt voorvertonen op de pagina met elementdetails, worden de video&#39;s traag geladen (CQ-4320122).

* Browserpagina reageert niet en wordt trager wanneer meer dan 200 elementen worden geüpload terwijl Duplicate Asset Detector is ingeschakeld (CQ-4319633).

* Wanneer een panoramisch afbeeldingselement wordt toegevoegd aan het panoramische mediacomponent op een pagina, wordt een niet-afgevangen referentiefout vastgelegd (CQ-4317666).

* Wanneer de interactieve media viewer wordt geïmplementeerd met Experience Fragment, wordt het Experience Fragment niet geopend bij de uitgever en wordt een fout vastgelegd (CQ-4317655).

* [!UICONTROL Publish to Dynamic Media] optie is niet beschikbaar binnen [!UICONTROL Quick Publish] opties in [!UICONTROL Properties] pagina (CQ-4317199).

* Siteauteurs met de machtiging Alleen-lezen kunnen de functie voor slim uitsnijden gebruiken voor elementen en de slimme bijgesneden uitvoeringen bewerken (CQ-4316450).

* Video-annotaties werken niet voor mappaden waarbij [!DNL Dynamic Media] de configuratie wordt niet toegelaten, zelfs als [!DNL Experience Manager] -instantie is ingesteld in [!DNL Dynamic Media] modus (CQ-4314950).

* Wanneer de titel van het element dubbel-byte, multi-byte, hoge ASCII, Cyrillisch, surrogaat paar, Hebreeuws, Arabisch, en GB18030 karakters heeft, dan bij het publiceren aan Dynamic Media heeft de activa titel een vraagteken (?) (CQ-4311872).

>Bekende problemen met het afspelen van video in Dynamic Media *alleen in Experience Manager 6.5.9.0*:
>
>* 

   <!-- CQDOC-18116 -->You cannot play video renditions from the asset's Details page on Experience Manager - Dynamic Media running in hybrid mode.
>* 

   <!-- CQDOC-18116 -->You cannot stream videos on Experience Manager - Dynamic Media running in hybrid mode.


### Platform {#platform-6590}

* Wanneer u een miniatuur voor een blauwdruk genereert en de wijzigingen in de live kopie doorvoert, werkt de overerving voor sommige velden niet (CQ-4319517).

* Wanneer u een map maakt, selecteert u de eigenschap Bestelbaar en voegt u meer dan 20 elementen aan de map toe. Als u alle elementen in de map selecteert, wordt een onjuist aantal weergegeven (CQ-4316243).

* Wanneer u een pagina vernieuwt, geeft het sorteren van mappen of elementen niet de juiste resultaten weer (CQ-4316200).

* Handlebars JavaScript bibliotheek wordt bevorderd aan v4.7.7 (NPR-36375).

* Aangepaste bundels worden niet bijgewerkt wanneer u een nieuw codepakket installeert met Package Manager (NPR-35949).

* A `resourceresolver` Sling bundle veroorzaakt `Sling:alias` query voor mislukken (NPR-35335).

* Het contextpad wordt verwijderd bij het instellen van SSL in Experience Manager (NPR-35294).

* De `SegmentNotFound` de uitzondering wordt geretourneerd na een langdurige sessie (NPR-36405).

### Integraties {#integrations-6590}

* Kan pagina-eigenschappen niet opslaan met overerving ingeschakeld voor Cloud Services-ervaringsfragmenten (NPR-36107).

* De paginering en lazy loading van de IMS-gebruikersinterface geven geen geschikte resultaten weer (NPR-36046).

* Wanneer u een configuratie van het Doel A4T creeert en rapportbron selecteert zoals [!DNL Adobe Analytics]Er zijn geen Adobe Target-compatibele rapportsuites beschikbaar in de vervolgkeuzelijst (NPR-36006).

### Projecten {#projects-6590}

* Kan de eigenschappen van een project niet opslaan omdat het JCR-pad naar het project niet is opgelost door een extra slash (`/`) toegevoegd aan het projectpad (NPR-36191).

### Schermen {#screens-6590}

* [!DNL Experience Manager Screens] spelers kunnen niet voor authentiek verklaren als een douane twee-factor authentificatiemanager wordt gebruikt (NPR-35854).

### Handel {#commerce-6590}

* De [!UICONTROL Commerce Catalog] De wizard kan niet meer dan 40 items laden in de kolomweergave (CQ-4318379).

### Vertaalprojecten {#translation-6590}

* Opties voor bijwerken of overschrijven worden niet weergegeven tijdens het opnieuw omzetten van een `es` tot `es_es` bladzijde (NPR-36170).

* Wanneer de optie Automatisch goedkeuren is geselecteerd voor een project met menselijke vertaling, wordt de taakstatus weergegeven als `Unknown` (NPR-35981).

* Wanneer u een pagina vertaalt, is het referentiepad van [!DNL Experience Fragments] wordt niet bijgewerkt naar het doel [!DNL Experience Fragment] referentiepad (NPR-35911).

* Wanneer u wijzigingen aanbrengt in de bovenliggende en onderliggende pagina&#39;s en de bovenliggende pagina ter vertaling verzendt, worden de onderliggende pagina&#39;s ook onjuist vertaald (NPR-35896).

* Wanneer er meerdere gelijktijdige vertaalprojecten voor een geselecteerde pagina zijn, wordt [!UICONTROL Go To Projects] Deze optie is niet gekoppeld aan het meest recente vertaalproject (NPR-35454).

* Wanneer u elementen publiceert naar [!DNL Dynamic Media], [!DNL Experience Manager] geeft een onjuist bericht weer voor niet-gepubliceerde tags (CQ-4315914, CQ-4315913).

* Wanneer u een verwijderde taak opent, [!DNL Experience Manager] geeft een onjuist bericht weer (CQ-4315910).

### Workflow {#workflow-6590}

* Wanneer u op Handelingen Voltooien, Delegeren of Openen klikt voor items die beschikbaar zijn in Inbox, is er geen visuele aanwijzing voor het voltooien van deze handelingen (NPR-36317).

### [!DNL Communities] {#communities-6590}

* Bij spamfiltering verbruikt het systeem 100% van de Java™ heap-ruimte, waardoor de Experience Manager server niet reageert (NPR-36316, NPR-36493).
* In forums verzamelt het JCR gegevens die afkomstig zijn van `SearchCommentSocialComponentListProvider` wordt uitgelekt (NPR-36235).
* Het openen van een specifiek postbusbericht weerspiegelt alle berichten met onjuiste paginering en andere kwesties (NPR-35917).

### [!DNL Brand Portal] {#brandportal-6590}

* De markering voor de functie Asset Sourcing wordt automatisch ingeschakeld bij het configureren [!DNL Experience Manager Assets] with [!DNL Brand Portal] (NPR-36010).

### [!DNL Forms] {#forms-6590}

>[!NOTE]
>
>* [!DNL Experience Manager Forms] geeft toe:voegen-on pakketten één week na gepland vrij [!DNL Experience Manager] Releasedatum van Service Pack.


**Adaptieve Forms**

* Problemen met taalinitialisatie in [!DNL Experience Manager Forms] 6.5.7.0 en het genereren van meerdere vertaalwoordenboeken (NPR-36439).
* Wanneer u een bijlage toevoegt aan een adaptief formulierfragment en het formulier verzendt, [!DNL Experience Manager Forms] geeft het volgende foutbericht weer (NPR-36195):

   ```TXT
    POST /content/forms/af/attachmentissue/jcr:content/guideContainer.af.submit.jsp HTTP/1.1] com.adobe.aemds.guide.servlet.GuideSubmitServlet [AF] Invalid file name or mime type for file resulted in submission failure
   ```

* Wanneer u menselijke vertaling gebruikt om een woordenboek bij te werken en dan een voorbeeld van een adaptief formulier te bekijken, worden de wijzigingen niet weergegeven (NPR-36035).

**Interactieve communicatie**

* Wanneer u een afbeelding uploadt via het Interactieve communicatiekanaal Afdrukken en deze bewerkt, is de afbeelding niet meer zichtbaar (NPR-36518).

* Bij het bewerken van een tekstelement en het vullen van een plaatsaanduiding worden alle interactieve elementen verwijderd uit het navigatiegebied (NPR-35991).

**Workflow**

* Wanneer u het REST-eindpunt van een [!DNL Experience Manager Forms] service op JBoss®, [!DNL Experience Manager] geeft het volgende foutbericht weer (NPR-36305):

   ```TXT
   Invalid input. The maximum length of 2000 characters was exceeded.
   ```

**BackendIntegration**

* Kan een formuliergegevensmodel niet opslaan terwijl het Leesservice-argument wordt gebonden aan een letterlijke waarde die een streepje bevat (NPR-36366).

**Documentbeveiliging**

* Wanneer u certificering en HSM instelt voor GlobalSign, [!DNL Experience Manager Forms] geeft het dialoogvenster `Unsuported Algorithm` en `Invalid TSA Certificate` foutberichten tijdens het toevoegen van een tijdstempel aan LTV (NPR-36026, NPR-36025).

**Document Services**

* Updates voor [!DNL Gibson] bibliotheek voor integratie met [!DNL Experience Manager Forms] (NPR-36211).

**Foundation JEE**

* Wanneer u het Beheer van Eindpunten op AdminUI selecteert, [!DNL Experience Manager Forms] geeft het dialoogvenster `endpoint registry failure` foutbericht (CQ-4320249).

Voor informatie over beveiligingsupdates raadpleegt u [[!DNL Experience Manager] beveiligingspagina met opsommingstekens](https://helpx.adobe.com/security/products/experience-manager.html).

### Bekende problemen in Experience Manager 6.5.9.0 {#known-issues-6590}

* Als u een upgrade uitvoert op uw [!DNL Experience Manager] van 6.5 tot 6.5.10.0 versie, kunt u bekijken `RRD4JReporter` uitzonderingen in de `error.log` bestand. Start de instantie opnieuw om het probleem op te lossen.

* Als u [!DNL Experience Manager] 6.5 Service Pack 5 of een vorig de dienstpak op [!DNL Experience Manager] 6.5, de runtime kopie van het aangepaste workflowmodel voor uw middelen (gemaakt in `/var/workflow/models/dam`) wordt geschrapt.
Om uw runtime exemplaar terug te winnen, adviseert Adobe om het ontwerp-tijd exemplaar van het model van het douanewerkschema met zijn runtime exemplaar te synchroniseren gebruikend HTTP API:
   `<designModelPath>/jcr:content.generate.json`.

* Gebruikers kunnen de naam wijzigen van een map in een hiërarchie in [!DNL Assets] en publiceer een geneste map naar [!DNL Brand Portal]. De titel van de map wordt echter niet bijgewerkt in [!DNL Brand Portal] totdat de hoofdmap opnieuw wordt gepubliceerd.

* Wanneer een gebruiker een veld voor het eerst in een adaptief formulier configureert, wordt de optie voor het opslaan van een configuratie niet weergegeven in de eigenschappenbrowser. Als u een ander veld van het adaptieve formulier in dezelfde editor selecteert, wordt het probleem opgelost.

* De volgende fouten en waarschuwingsberichten kunnen tijdens de installatie van Experience Manager 6.5.x.x worden weergegeven:
   * &quot;Wanneer de integratie van Adobe Target in Experience Manager gebruikend de StandaardAPI van het Doel (authentificatie IMS) wordt gevormd, dan leidt het uitvoeren van de Fragmenten van de Ervaring naar Doel in verkeerde aanbiedingstypes die worden gecreeerd. In plaats van het type &quot;Experience Fragment&quot;/bron &quot;Adobe Experience Manager&quot; maakt Target verschillende aanbiedingen met het type &quot;HTML&quot;/bron &quot;Adobe Target Classic&quot;.
   * `com.adobe.granite.maintenance.impl.TaskScheduler`: Geen onderhoudsvensters gevonden bij graniet/bediening/onderhoud.
   * De validatie aan de adaptieve formulierserver-side mislukt wanneer statistische functies zoals SUM, MAX en MIN worden gebruikt (CQ-4274424).
   * `com.adobe.granite.maintenance.impl.TaskScheduler` - Geen onderhoudsvensters gevonden bij graniet/bediening/onderhoud.
   * Hotspot in een interactieve Dynamic Media-afbeelding is niet zichtbaar wanneer u een voorvertoning van het element weergeeft via de Shopable Banner-viewer.
   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]` : Time-out bij wachten op wijziging van reg om niet-geregistreerd te voltooien.

## [!DNL Adobe Experience Manager] 6.5.8.0. {#experience-manager-6580}

[!DNL Adobe Experience Manager] 6.5.8.0 omvat nieuwe eigenschappen, zeer belangrijke klant-gevraagde verhogingen, en prestaties, stabiliteit, en veiligheidsverbeteringen, die sinds de beschikbaarheid van 6.5 versie in April 2019 worden vrijgegeven. Het de dienstpak wordt geïnstalleerd op [!DNL Adobe Experience Manager] 6.5

De belangrijkste functies en verbeteringen die zijn geïntroduceerd in [!DNL Adobe Experience Manager] 6.5.8.0 zijn:

<!-- TBD:
* Using the Connected Assets functionality, it is now possible to connect up to 3 [!DNL Sites] instances with 1 [!DNL Assets] instances. The configuration user interface now allows the administrators to provide the details of these [!DNL Sites] instances. -->

* Wanneer u [Functionaliteit van verbonden elementen](/help/assets/use-assets-across-connected-assets-instances.md)kunt u nu een lijst weergeven met alle [!DNL Sites] pagina&#39;s die het element gebruiken. Deze verwijzingen naar een actief zijn beschikbaar in het [!UICONTROL Properties] pagina. Op deze manier kunnen beheerders, marketers en bibliothecarissen een volledig overzicht van het gebruik van bedrijfsmiddelen krijgen, zodat ze het bedrijfsmerk beter kunnen bijhouden, beheren en het merk consistenter zijn.

* Wanneer u een element verwijdert waarnaar in een webpagina wordt verwezen, [!DNL Experience Manager] [geeft een waarschuwing weer](/help/assets/use-assets-across-connected-assets-instances.md#asset-usage-references). U kunt afdwingen dat een element waarnaar wordt verwezen wordt verwijderd, of de referenties controleren en wijzigen die worden weergegeven in het dialoogvenster [!DNL Properties] pagina van het element. Als u op de referenties klikt, worden de lokale en externe [!DNL Sites] pagina&#39;s.

* De pagina&#39;s van Live Copy die beschikbaar zijn voor rollout sorteren met de opdracht [!UICONTROL Name], [!UICONTROL Last modified date,] en [!UICONTROL Last rollout date] eigenschappen.

* De ingebouwde opslagplaats (Apache Jackrabbit Oak) wordt bijgewerkt naar 1.2.2.6. <!-- TBD: Mention the version -->

Voor een volledige lijst met functies en verbeteringen die zijn geïntroduceerd in [!DNL Experience Manager] 6.5.8.0, zie [nieuwe functies in [!DNL Adobe Experience Manager] 6.5 Service Pack 8](new-features-latest-service-pack.md).

Hieronder volgt een lijst met oplossingen die u vindt in [!DNL Experience Manager] 6.5.8.0 release.

### [!DNL Sites] {#sites-6580}

* Wanneer een pagina naar een blauwdruk wordt verplaatst, wordt de bestemming van koppelingen niet bijgewerkt (NPR-35724).
* Op Tizen gebaseerde speler kan niet worden geverifieerd voor bepaalde browsers. Het probleem treedt op bij browsers die het kenmerk samesite=none niet ondersteunen (NPR-35589).
* Een niet-vergrendelde responsieve container geeft geen toegestane onderdelen weer (NPR-35565).
* Wanneer u een live kopie van een zojuist toegevoegde pagina maakt, maakt de master taal twee kopieën voor elk domein (NPR-35545).
* Deadlock in de SCR Registratie van de Component wanneer vele draden wegens worden geblokkeerd `org.apache.felix.scr.impl.ComponentRegistry` timer. Dientengevolge [!DNL Experience Manager] reageert niet langer voor onbepaalde tijd (GRANITE-33125,FELIX-6252).
* Wanneer u een specifiek middel in de zijspoorstaaf zoekt, bevat het resultaat sommige niet-gezochte activa (NPR-35524).
* Wanneer u SSL voor een instantie van de Experience Manager toelaat, wordt de contextweg verwijderd (NPR-35477).
* Wanneer u een lijst creeert, voeg wat tekst als eerste element toe, voeg een lijst als tweede element toe, en voeg een lijst binnen de lijst toe, vervormt de ouderlijst (NPR-35465).
* Als u verschillende plug-ins gebruikt voor opeenvolgende lijstitems, kunt u een extra <br> -tag wordt toegevoegd aan de lijstitems (NPR-35464).
* Wanneer een lijst tussen twee paragrafen wordt geplaatst, kunt u geen lijst aan de lijst (NPR-35356) toevoegen.
* Wanneer u een AEM instantieverbetering van AEM 6.3 tot AEM 6.5 begint, duurt de verbeteringsinstantie langer om (NPR-35323) te beginnen.
* Wanneer u een AEM element dupliceert dat een haakje () bevat. in de naam, ontbreekt de replicatie (GRANITE-27004, NPR-35315).
* Wanneer u koppen toevoegt aan een RTF-editor, is de alineaknop uitgeschakeld (NPR-35256).
* Wanneer u een punt aan een bestaande lijst toevoegt, schrapt het het opvouwen of knevellijst (NPR-35206).
* Als de optie Pagina uitrollen is geselecteerd, wordt een dialoogvenster weergegeven met alle beschikbare live kopieën en wordt de functie automatisch uitrollen uitgevoerd. De live kopieën van pagina&#39;s worden zonder tussenkomst van de gebruiker naar alle geografische gebieden uitgerold (NPR-35138).
* Wanneer u de optie Inclusief onderliggende pagina&#39;s gebruikt, worden niet alle pagina&#39;s vermeld met de optie Publicatie beheren. Er worden slechts 22 pagina&#39;s vermeld (NPR-35086).
* Wanneer een beleid wordt uitgegeven, behoudt de tekstcomponent niet de beleidsveranderingen (NPR-35070).
* Wanneer u een aantal items in een genummerde lijst inspringt, behouden alle items hetzelfde nummer, maar de nummering moet beginnen bij 1 voor items met dezelfde inspringing (CQ-4313011).
* Wanneer minificatie is ingeschakeld, kunt u geen enkele pagina of component bewerken. De kwesties begonnen na het installeren AEM 6.5 Service Pack 7 (CQ-4311133).
* Universeel zoek- en assetfilters retourneren irrelevant of geen resultaten (CQ-4312322, NPR-35793).
* Wanneer meerdere pagina&#39;s tegelijk toegang krijgen tot een clientbibliotheek, kan de HTML-bibliotheekbeheerder de clientbibliotheek niet laden. Dit leidt tot een onjuiste weergave van pagina&#39;s (NPR-35538).
* Het contextpad wordt automatisch verwijderd wanneer u een SSL instelt in [!DNL Experience Manager] (NPR-35294).
* De manager van het pakket registreert geen gebruikers na het klikken van de Logout optie (NPR-35160).

### [!DNL Assets] {#assets-6580}

[!DNL Adobe Experience Manager] 6.5.8.0. [!DNL Assets] verhelpt de volgende problemen en biedt de volgende verbeteringen.

* Na het herstellen van een vorige versie van activa, wordt de gebeurtenis DamEvent.Type RESTORED niet teweeggebracht in de console OSGi (NPR-35789).
* `IndexWriter.merge` oorzaken `OutOfMemoryError` fout als functie voor slimme tags grote `/oak:index/lucene` en `/oak:index/ntBaseLucene` indexen (NPR-35651).
* Er wordt een foutbericht weergegeven wanneer u een [!UICONTROL Asset Contribution] typemap met multibyte-tekens in de naam (NPR-35605).
* Wanneer trapsgewijze subtypevelden voor metagegevens worden gebruikt, treedt de fout &#39;Dit veld invullen&#39; op (NPR-35643).
* Wanneer een bestaand element op de [!DNL Assets] en er wordt een nieuwe versie gemaakt. De wijzigingen in de metagegevens zijn niet blijvend (NPR-34940).
* Wanneer u regels maakt in de metagegevensschemaeditor voor een trapsgewijs menu, wordt de opdracht [!UICONTROL Dependant On] wordt dezelfde naam herhaald (NPR-35596).
* Zoeken op gelijkenis werkt niet na bewerken [!UICONTROL Assets Admin Search Rail] (NPR-35588).
* Vanuit een map als u de zoekfunctie voor elementen in de linkertrack opent door op [!UICONTROL Filter], het filter in [!UICONTROL Status] > [!UICONTROL Checkout] > [!UICONTROL Checked out] werkt niet (NPR-35530).
* Als u probeert alle slimme tags van een element te verwijderen en de wijzigingen op te slaan, worden de tags niet verwijderd. De gebruikersinterface geeft echter aan dat de wijzigingen worden opgeslagen (NPR-35519).
* Gebruikers kunnen elementen in de lijstweergave niet opnieuw rangschikken of sorteren in een bestelbare map (NPR-35516).
* Als u het standaardmetagegevensschema bewerkt, wordt het veld Tags in het element [!UICONTROL Properties] verandert in een tekstveld. Door de wijziging kunnen onbewuste gebruikers tags op aanvraag toevoegen en worden de tags als een tekenreeks opgeslagen in de opslagplaats (NPR-35478).
* Als u tijdens het downloaden van een element een naam opgeeft die geen geldig e-mailadres heeft, is de downloadoptie niet beschikbaar. Als er echter een andere optie in het dialoogvenster Downloaden is geselecteerd, wordt de knop ingeschakeld, maar wordt geen e-mail verzonden (NPR-35365).
* Gebruikers kunnen elementen niet inchecken nadat ze de elementen in [!DNL Adobe InDesign] en een fout ontvangen bij gebrek aan machtigingen (NPR-35341).
* Handlebars JavaScript bibliotheek wordt bevorderd aan v4.7.6 (NPR-35333).
* De interface van de metagegevenseditor werkt niet meer zoals u had verwacht wanneer u begint met het bewerken van bulkmetagegevens en items deselecteert totdat één item geselecteerd blijft (NPR-35144).
* De globale navigatie opent niet de correcte console wanneer geklikt van binnen `assets.html` pagina (CQ-4312311).
* [!DNL Assets] geeft geen RGB-uitvoering weer voor een element met RGB-uitvoering (CQ-4310190).
* De [!UICONTROL Relate] in het menu wordt niet correct weergegeven in het dialoogvenster [!UICONTROL Properties] pagina (CQ-4310188).
* Als filetype filter voor documenten wordt gebruikt om activa te zoeken en een Slimme Inzameling tot stand te brengen, wordt de filter niet toegepast wanneer de inzameling wordt betreden. In plaats daarvan worden alle typen elementen weergegeven in de zoekopdracht (NPR-35759).
* U kunt geen elementen in een lichtbak slepen en toevoegen vanuit de [!DNL Assets] gebruikersinterface (NPR-35901).
* Wanneer een nieuwe versie van een bestaand element wordt gemaakt nadat het naamconflict is opgelost, worden de metagegevens van het oorspronkelijke element overschreven (CQ-4313594).
* Wanneer u het zoeken van elementen filtert met een zoekfilter of voorspeld, een element opent om het te bekijken of te bewerken en teruggaat naar de pagina met zoekresultaten, werkt het filter niet. Alle gezochte activa zijn vermeld ongefilterd (NPR-35913).

#### [!DNL Dynamic Media] {#dynamic-media-6580}

* De optie URL voor de voorinstelling van een RESS-afbeelding wordt ingeschakeld op de pagina met elementdetails. Nu zijn zowel URL- als RESS-opties beschikbaar op de pagina met elementdetails wanneer de RESS-voorinstelling is geselecteerd in de sectie met dynamische uitvoeringen. (CQ-4311241)
* Interactieve mediacomponent - interactieve video werkt niet als de gebruiker [!DNL Experience Manager] met selectieve publicatieconfiguratie (CQ-4311054).
* Als u elementen naar andere mappen verplaatst, moet u de synchronisatie tussen [!DNL Experience Manager] en [!DNL Dynamic Media–Scene7] via API is zeer langzaam (CQ-4310001).
* Bij gebruik van Omnissearch neemt de grootte van de logs aanzienlijk toe (CQ-4309153).
* Wanneer selectieve synchronisatie is ingeschakeld en een element wordt gekopieerd (niet verplaatst) naar een synchronisatiemap, wordt het niet gesynchroniseerd zoals u had verwacht (CQ-4307122).
* Voor geüploade elementen die automatisch naar DM worden gepubliceerd, wordt de status niet weergegeven bij AEM. Bovendien wordt in de statuskolom Dynamic Media Publish niet de juiste gepubliceerde status weergegeven (CQ-4306415).
* Als een actief wordt gepubliceerd op [!DNL Experience Manager] en is ingesteld op publiceren naar [!DNL Dynamic Media] bij activering `scene7FileStatus` De metagegevenswaarde wordt niet zoals verwacht bijgewerkt (CQ-4308269).
* Bij het bewerken van het videoprofiel [!DNL Experience Manager] geeft niet de hoogte- en bitsnelheidwaarden weer die zijn ingesteld voor de videovoorinstelling. De velden worden leeg weergegeven (CQ-4311828).

### [!DNL Commerce] {#commerce-6580}

* Kan geen aangepaste tag maken voor alle producten in de handel (CQ-4310682).

* De update van de verwijzing van het productelement veroorzaakt replicatiedraden om in de wachtstand te zijn tot de draad ProductAssetListener zijn verplichtingen aan JCR voltooit (NPR-35269).

### Platform {#platform-6580}

* Wanneer u een component van de Mening van het Lusje van het Koraal zonder lusjes gebruikt en dan een validator van de Stichting teweegbrengt, komt de volgende fout voor (NPR-35636):

   ```TXT
    Uncaught TypeError: Cannot set property 'invalid' of undefined
     at enable (foundation.js:10703)
     at foundation.js:10710
   ```

* SCD door:sturen replicatie ontbreekt voor de gebeurtenissen van de Schrapping voor knopen die een komma in de naam (NPR-35191) omvatten.

* Nadat u aan AEM 6.5.7 bevordert, beginnen de bouwstijlen te ontbreken. De reden hiervoor is dat een oude versie of geen cola van de nakker is ingebed in de uber-jar (GRANITE-33006).

### Gebruikersinterface {#ui-6580}

* Wanneer u van de mening van de Kaart aan de mening van de Lijst voor documenten in een omslag in de console van Activa overschakelt, werkt het sorteren niet geschikt (NPR-35842).

* Wanneer u tekst in een tekstcomponent hyperlinkt, geeft de zoekfunctie niet de juiste resultaten weer (NPR-35849).

* Wanneer geen waarde wordt verstrekt aan een verborgen gebied dat wordt gemerkt vereist, verhindert het u een component (NPR-35219) op te slaan.

### Integraties {#integrations-6580}

* Wanneer u verschillende waarden voor IMS huurder ID en de code van de Cliënt van het Doel gebruikt, [!DNL Experience Manager] kan niet integreren met [!DNL Adobe Target] (NPR-35342).

### Vertaalprojecten {#translation-6580}

* Problemen bij het exporteren of importeren van een vertaaltaak in [!DNL Experience Manager] (NPR-35259).

### Campagne {#campaign-6580}

* Wanneer u een campagnepagina maakt met een out-of-the-box-sjabloon in Touch UI en het tabblad E-mail opent in het dialoogvenster met pagina-eigenschappen, blijft de variabele voor de personalisatie van het onderwerp en de tekstvelden uitgeschakeld (CQ-4312388).

### [!DNL Communities] {#communities-6580}

* Bij het toevoegen van een paginastructuur aan een communitygroep, [!UICONTROL Group] de titel in de breadcrumb wordt gewijzigd in de titel van de eerste [!UICONTROL Page] (NPR-35803).
* In tegenstelling tot moderatoren is een standaardlid van de community geen toegang tot een ontwerppost (NPR-35339) en kan het deze niet bewerken.
* Verbroken toegangscontrole en ontkenning van de dienst met `DSRPReindexServlet` waardoor de site van de gemeenschappen wordt verkleind tot de indexering is voltooid (NPR-35591).
* Verwijderen [!UICONTROL All Users] van de [!UICONTROL Administrators] het veld verwijdert deze niet daadwerkelijk uit het achterste gedeelte (NPR-35592, NPR-35611).
* De [!UICONTROL Compose Message] geen resultaat retourneert wanneer de ingevoerde tekst een gedeeltelijke overeenkomst is (NPR-35666).

* Wanneer u tags aan een nieuwe blog wilt toevoegen door **[!UICONTROL Add Tags]**. Om de prestaties te verbeteren, installeert u [cqTagLucene-0.0.1.zip hotfix](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/cqTagLucene-0.0.1.zip).

### [!DNL Brand Portal] {#brandportal-6580}

* Een lid toevoegen aan een [!UICONTROL Asset Contribution] tekstmap toont [!UICONTROL Add User or Group] bijschrift in de gebruikersinterface, hoewel alleen actieve Brand Portal-gebruikers worden ondersteund en niet groepen (NPR-35332).

### [!DNL Forms] {#forms-6580}

>[!NOTE]
>
>[!DNL Experience Manager Forms] geeft toe:voegen-on pakketten één week na gepland vrij [!DNL Experience Manager] Releasedatum van Service Pack.

**Adaptieve Forms**

* Wanneer u een tabel met een herhaalbare rij invoegt in een herhaalbaar paneel dat meerdere instanties in een adaptieve vorm heeft, wordt de tabel altijd toegevoegd aan de eerste instantie van het paneel (NPR-35635).

* Wanneer de tabfocus de component CAPTCHA opnieuw bereikt nadat deze eenmaal in een adaptieve vorm is geverifieerd, [!DNL Experience Manager Forms] geeft het dialoogvenster `Provide Captcha phrase to proceed` foutbericht (NPR-35539).

**Interactieve communicatie**

* Wanneer u een vertaald formulier verzendt, worden de verzendberichten in het Engels weergegeven en niet in de juiste taal vertaald (NPR-35808).

* Wanneer u een hide-voorwaarde opneemt in de bijgevoegde XDP- of documentfragmenten, kan de interactieve communicatie niet worden geladen (NPR-35745).

**Correspondentenbeheer**

* Wanneer u een letter bewerkt, duurt het langer om de modules met voorwaarden te laden (NPR-35325).

* Wanneer u in het linkernavigatievenster een element selecteert dat niet in een letter is opgenomen en vervolgens het volgende element selecteert, wordt de blauwe markering niet uit het eerder geselecteerde element verwijderd (NPR-35851).

* Wanneer u tekstvelden in een letter bewerkt, [!DNL Experience Manager Forms] geeft het dialoogvenster `Text Edit Failed` foutbericht (CQ-4313770).

**Workflow**

* Wanneer u een adaptief formulier probeert te openen op een [!DNL Experience Manager Forms] De toepassing reageert niet meer op een mobiele toepassing voor iOS (CQ-4314825).

* De [!UICONTROL To-do] in de werkruimte HTML worden HTML-tekens weergegeven (NPR-35298).

**XMLFM**

* Wanneer u een XML-document genereert met de Output Service, wordt `OutputServiceException` Er treedt een fout op bij sommige XML-bestanden (CQ-4311341, CQ-4313893).

* Wanneer u superscript-eigenschap toepast op het eerste teken van het opsommingsteken, wordt de grootte van het opsommingsteken kleiner (CQ-4306476).

* De PDF forms die worden gegenereerd met de uitvoerservice omvatten geen randen (CQ-4312564).

**Designer**

* Wanneer u een XDP-bestand opent in [!DNL Experience Manager Forms] In Designer wordt een bestand designer.log gegenereerd in dezelfde map als het XDP-bestand (CQ-4309427, CQ-4310865).

**HTML5 Forms**

* Wanneer u een selectievakje in een adaptief formulier selecteert in [!DNL Safari] webbrowser voor [!DNL iOS 14.1 or 14.2], worden geen extra velden weergegeven (NPR-35652).

**Forms Management**

* Geen bevestigingsbericht om aan te geven dat XDP-bestanden in bulk zijn geüpload naar CRX-opslagplaats (NPR-35546).

**Documentbeveiliging**

* Meerdere emissies gerapporteerd voor de [!UICONTROL Edit Policy] op AdminUI (NPR-35747).

### Bekende problemen in Experience Manager 6.5.8.0 {#known-issues-6580}

* Als u een upgrade uitvoert op uw [!DNL Experience Manager] -instantie van versie 6.5 tot versie 6.5.8.0 `RRD4JReporter` uitzonderingen in de `error.log` bestand. Start de instantie opnieuw om het probleem op te lossen.

* Als u [!DNL Experience Manager] 6.5 Service Pack 5 of een vorig de dienstpak op [!DNL Experience Manager] 6.5, de runtime kopie van het aangepaste workflowmodel voor uw middelen (gemaakt in `/var/workflow/models/dam`) wordt geschrapt.
Om uw runtime exemplaar terug te winnen, adviseert Adobe om het ontwerp-tijd exemplaar van het model van het douanewerkschema met zijn runtime exemplaar te synchroniseren gebruikend HTTP API:
   `<designModelPath>/jcr:content.generate.json`.

* Neem contact op met de klantenondersteuning van Adobe als u problemen ondervindt bij het bewerken en maken van trapsgewijze regels in de [!UICONTROL Folder Metadata Schema Forms Editor] en [!UICONTROL Metadata Schema Forms Editor] gebruiken [!UICONTROL Define Rule] . De regels die al zijn gemaakt en opgeslagen, werken zoals u had verwacht.

* Als de naam van een map in de hiërarchie wordt gewijzigd in [!DNL Experience Manager Assets] en de geneste map met een element is gepubliceerd naar [!DNL Brand Portal], wordt de titel van de map niet bijgewerkt in [!DNL Brand Portal] totdat de hoofdmap opnieuw wordt gepubliceerd.

* Wanneer een gebruiker een veld voor het eerst in een adaptief formulier configureert, wordt de optie voor het opslaan van een configuratie niet weergegeven in de eigenschappenbrowser. Als u een ander veld van het adaptieve formulier in dezelfde editor selecteert, wordt het probleem opgelost.

* Indien [!UICONTROL Connected assets configuration] de tovenaar keert een 404 foutenmelding na installatie terug, manueel herinstalleert `cq-remotedam-client-ui-content` en `cq-remotedam-client-ui-components` pakketten met gebruik van Package Manager.

* De volgende fouten en waarschuwingsberichten kunnen tijdens de installatie van Experience Manager 6.5.x.x worden weergegeven:
   * &quot;Wanneer de integratie van Adobe Target in Experience Manager gebruikend de StandaardAPI van het Doel (authentificatie IMS) wordt gevormd, dan leidt het uitvoeren van de Fragmenten van de Ervaring naar Doel in verkeerde aanbiedingstypes die worden gecreeerd. In plaats van het type &quot;Experience Fragment&quot;/bron &quot;Adobe Experience Manager&quot; maakt Target verschillende aanbiedingen met het type &quot;HTML&quot;/bron &quot;Adobe Target Classic&quot;.
   * `com.adobe.granite.maintenance.impl.TaskScheduler`: Geen onderhoudsvensters gevonden bij graniet/bediening/onderhoud.
   * De validatie aan de adaptieve formulierserver-side mislukt wanneer statistische functies zoals SUM, MAX en MIN worden gebruikt (CQ-4274424).
   * `com.adobe.granite.maintenance.impl.TaskScheduler` - Geen onderhoudsvensters gevonden bij graniet/bediening/onderhoud.
   * Hotspot in een interactieve Dynamic Media-afbeelding is niet zichtbaar wanneer u een voorvertoning van het element weergeeft via de Shopable Banner-viewer.
   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]` : Time-out bij wachten op wijziging van reg om niet-geregistreerd te voltooien.

## [!DNL Adobe Experience Manager] 6.5.7.0. {#experience-manager-6570}

[!DNL Adobe Experience Manager] 6.5.7.0 is een belangrijke update die nieuwe eigenschappen, zeer belangrijke klant gevraagde verhogingen, en prestaties, stabiliteit, en veiligheidsverbeteringen omvat, die sinds de beschikbaarheid van 6.5 versie in April 2019 worden vrijgegeven. Het Service Pack is geïnstalleerd op [!DNL Adobe Experience Manager] 6.5

De belangrijkste functies en verbeteringen die zijn geïntroduceerd in [!DNL Adobe Experience Manager] 6.5.7.0 omvat:

* Als u de pagina uitvoert, worden de pagina verplaatst en MSM-rollouts als asynchrone bewerkingen uitgevoerd, zodat de runtime minder wordt belast met de prestaties.

* Gebruikers kunnen digitale elementen sorteren in de Kaart- en kolomweergave.

* [!DNL Assets] en [!DNL Dynamic Media] bieden meerdere toegankelijkheidsverbeteringen. De verbeteringen hebben betrekking op toetsenbordnavigatie, het gebruik van schermlezers en het inschakelen van gebruikers om vergelijkbare ondersteunende hulpmiddelen (AT) te gebruiken. Zie [[!DNL Assets] verbeteringen](#assets-6570) en [[!DNL Dynamic Media] verbeteringen](#dynamic-media-6570).

* [Formuliergegevensmodel HTTP-clientconfiguratie](../../help/forms/using/configure-data-sources.md#fdm-http-client-configuration) om de prestaties te optimaliseren.

* [Beschikbaarheid van de Optie van het Terugstellen voor elke component](../../help/forms/using/resize-using-layout-mode.md#resize-components) in de modus Lay-out

* [!DNL Experience Manager] 6.5 Service Pack 7 Forms verbetert de prestaties voor:

   * De veldwaarden op de server valideren wanneer u een adaptief formulier verzendt.

   * Een PDF-formulier converteren naar een adaptief formulier met de opdracht [!DNL Automated Forms Conversion service].

* Ondersteuning voor [!DNL Microsoft SQL Server] 2019 inch [!DNL Experience Manager Forms].

* Ondersteuning voor [!DNL Microsoft] SQL Server 2016 altijd op beschikbaarheidsgroepen voor Hoge Beschikbaarheid voor plaatsingen OSGi.

* De ingebouwde opslagplaats (Apache Jackrabbit Oak) wordt bijgewerkt naar versie 1.22.5.

Voor een volledige lijst met functies en verbeteringen die zijn geïntroduceerd in [!DNL Experience Manager] 6.5.7.0, zie [Nieuwe functies [!DNL Adobe Experience Manager] 6.5 Service Pack 7](new-features-latest-service-pack.md).

Hieronder volgt een lijst met oplossingen die u vindt in [!DNL Experience Manager] 6.5.7.0 release.

### [!DNL Sites] {#sites-6570}

* Wanneer u het dialoogvenster [!UICONTROL Timewrap] optie voor een pagina, de optie voor de track aan de zijkant van de tijdlijn open houden en naar [!UICONTROL Sites] console, de `Failed to Load` Er is een fout opgetreden (NPR-34951).

* De [!UICONTROL Timewrap] geeft geen afbeeldingen weer voor het geselecteerde datum- en tijdbereik (NPR-34951).

* Wanneer een filter aanroept `getHeader()` van een pagina die een inhoudsfragment bevat, `java.lang.AbstractMethodError` Er is een fout opgetreden (NPR-34942).

* Wanneer het pad van een pagina meerdere subtekenreeksen voor inhoud bevat, kunnen voorvertoningen niet worden weergegeven en mislukt de functie Vergelijken van versie ook (NPR-34740).

* Wanneer u een numerieke waarde instelt voor de `String` type label eigenschap van een component, kunt u de component verwijderen en de verwijderbewerking ongedaan maken. Nadat u de verwijdering ongedaan hebt gemaakt, verandert de eigenschap label echter van `String` tot `Long` (NPR-34739).

* De volgende uitzondering geldt bij het toevoegen van een ervaringsfragment dat is gebaseerd op een sjabloon met een vergrendelde indeling aan een pagina (NPR-34632):

   ```TXT
   org.apache.sling.api.SlingException: Cannot get DefaultSlingScript: org.apache.sling.api.SlingException: Cannot get DefaultSlingScript: org.mozilla.javascript.EcmaError: TypeError: Cannot call method "getChildren" of null
   ```

* Wanneer u een map verplaatst, veroorzaakt dit traversale problemen en treedt de volgende fout op (NPR-34554):

   ```TXT
   org.apache.sling.api.SlingException: Cannot get DefaultSlingScript. org.apache.jackrabbit.oak.query.RuntimeNodeTraversalException: The query read or traversed more than 100000 nodes. To avoid affecting other tasks, processing was stopped
   ```

* Wanneer nieuwe elementen worden gemaakt, gepubliceerd en naar een nieuwe locatie worden verplaatst, worden de `Request to complete move operation` wordt gemaakt en resulteert in een afgebroken status. Een nieuw element uploaden en een `move` resulteert in het maken van de `Request to complete move operation` workflow in hangende toestand (NPR-34543).

* Wanneer u een ervaringsfragment exporteert uit [!DNL Experience Manager] 6.5.2 milieu aan [!DNL Target] Standaard mislukt de API-aanroep omdat de werkruimte-eigenschap niet beschikbaar is voor [!DNL Target] Standaard (NPR-34557).

* Gebruikers kunnen geen pagina&#39;s publiceren via [!UICONTROL manage publication] omdat de [!UICONTROL Publish] verdwijnt (NPR-34542).

* Wanneer u enkele stijlen aan de tekst toevoegt, kunt u een `<div>` -label wordt aan de tekst toegevoegd en de stijl kan niet meer op de tekst worden toegepast (NPR-34531).

* Wanneer u een item in een pop-upmenu selecteert en de vereiste bestanden bijwerkt, is het niet toegestaan dialoogvensterwaarden op te slaan omdat het andere menu een leeg vereist veld heeft (NPR-34529).

* Wanneer u een pagina maakt op basis van een aangepaste sjabloon en deze verplaatst binnen de hiërarchie van de blauwdruk, worden componenten die eerder van de pagina zijn verwijderd, weergegeven op de pagina in de hiërarchie van de live kopie (NPR-34527).

* Wanneer een artikelstijl op een inhoud is toegepast, kan deze niet worden verwijderd (NPR-34486).

* Alle live kopieën en kopieën van een Experience Fragment wijzen naar hetzelfde [!DNL Adobe Target] aanbieding-id (NPR-34469).

* Lijstitems met opsommingstekens worden naast de genummerde lijst weergegeven (NPR-34455).

* De optie Vergelijken met bron geeft het verschil tussen de bronpagina en de bewerkte versie van een pagina niet aan (NPR-34285).

* Wanneer u een pagina schrapt, zijn de versiedetails niet configureerbaar (NPR-34159).

* Wanneer een gebruiker de optie [!UICONTROL Open Selection] wordt de focus van het toetsenbord verplaatst naar het verborgen besturingselement op de pagina (CQ-4307779, CQ-4293601).

* Wanneer u een gepubliceerde map op de Auteur verplaatst, worden de mappaden niet overeenkomstig bijgewerkt in de instantie Publiceren (CQ-4305144).

* Wanneer een gebruiker de optie `Enter` op de toets [!UICONTROL Select All] wordt de toetsenbordfocus niet naar de [!UICONTROL Create Control] optie (CQ-4293599).

* Wanneer u `Esc` -toets, wordt de focus niet teruggezet naar het bovenliggende besturingselement (CQ-4293593, CQ-4293590).

* Verbeterde WCAG-compatibiliteit voor [!DNL Sites] UI- en kerncomponenten (CQ-4293448).

* [!UICONTROL Zoom] en [!UICONTROL Scale] functies zijn uitgeschakeld voor de [!DNL Sites Editor] pagina (CQ-4282353).

* Nadat u de optie Rechtsom roteren hebt gebruikt, houdt de schermlezer op met commentaar voor de huidige rotatie- of spiegelstatus (CQ-4282128).

* De knoppen Gereed en Annuleren in het dialoogvenster Configureren bevatten veel tabstops (CQ-4274601).

* Het verplaatsen van pagina&#39;s met een vergelijkbare naam op hetzelfde niveau is niet toegestaan (NPR-35041).

* Nadat u de optie Wissen (x) hebt geselecteerd, wordt de toetsenbordfocus niet verplaatst naar de knop [!UICONTROL Filter] field (CQ-4293581).

* Wanneer u een upgrade uitvoert naar [!DNL Experience Manager] 6.5.6.0, het gedrag van het overgeërfde alineasysteem verandert en werkt niet correct (NPR-35117).

* Toetsenbordgebruikers kunnen de tabfocus niet in de juiste volgorde verplaatsen nadat ze de opdracht [!UICONTROL Action] deel over een [!DNL AEM Sites] pagina (CQ-4307786).

* Nadat u een optie hebt geselecteerd in de vervolgkeuzelijst met koppelingsdoelen van de RTE-werkbalk tijdens het bewerken van een inhoudsfragment, wordt het dialoogvenster met de auteur van het inhoudsfragment geflickeerd (CQ-4305532).

* Keyboard-gebruikers kunnen de opties in het dialoogvenster [!UICONTROL Add Component] vervolgkeuzelijst met gebruik van de pijl-omlaag (CQ-4295097).

* De tabfocus verschuift niet in de juiste volgorde wanneer u een datum selecteert in het menu Kalender in het dialoogvenster [!UICONTROL Assets] tabblad van een [!DNL Sites] pagina (CQ-4293600).

* De tabfocus verschuift niet naar de volgende of vorige opties voor toetsenbordgebruikers nadat de beschikbare opties voor Koppeling of Tekst zijn verwijderd tijdens het bewerken van een sitepagina (CQ-4293597).

* Toetsenbordgebruikers kunnen de tabfocus niet terugzetten op Meer opties in het dialoogvenster [!UICONTROL Actions] sectie na het bekijken van de beschikbare opties en het drukken van `Esc` key (CQ-4293592).

* Wanneer u het dialoogvenster [!UICONTROL Rotate] voor een afbeelding in het dialoogvenster [!UICONTROL Edit] wordt de tabfocus verplaatst naar de [!UICONTROL Redo] voor toetsenbordgebruikers (CQ-4293587).

* In de [!UICONTROL Open Selection] dialoogvenster beschikbaar op [!UICONTROL Link and Actions] tabs, verschuift de tabfocus naar verborgen elementen op de pagina na de [!UICONTROL Cancel] optie (CQ-4293579).

* Wanneer toetsenbordgebruikers een afbeelding bewerken, navigeert u naar de [!UICONTROL Finish] en drukt u op Enter. De schermlezers geven de voltooiing niet aan (CQ-4282351).

* De opties Omhoog en Omlaag in het dialoogvenster [!UICONTROL Link and Actions] zijn niet beschikbaar voor schermlezers en toetsenbordgebruikers (CQ-4281120).

* Toetsenbordgebruikers kunnen de tabfocus niet herstellen nadat ze naar de optie Sluiten (X) op de knop [!UICONTROL Properties] pagina (CQ-4293581, NPR-34653).

### [!DNL Assets] {#assets-6570}

[!DNL Adobe Experience Manager] 6.5.7.0. [!DNL Assets] verhelpt de volgende problemen en biedt de volgende verbeteringen.

* De volgende verbeteringen zijn aangebracht voor toegankelijkheid in [!DNL Experience Manager Assets] in deze release. Zie voor meer informatie [toegankelijkheidsfuncties in [!DNL Assets]](/help/assets/accessibility.md).

   * Wanneer u met een toetsenbord door de tijdlijn navigeert, wordt de `Esc` sleutel kan de [!UICONTROL Show All] zonder focus te verliezen (CQ-4293/598).
   * Wanneer u navigeert met de Tab-toets op het toetsenbord, behoudt het tagveld de focus nadat u de laatste tag uit de toegevoegde tags hebt verwijderd (NPR-35109).
   * [!DNL Experience Manager] De componenten bevatten nu de juiste informatie voor de naam, rol en waarde die door schermlezers moeten worden gebruikt (NPR-34255).
   * Nadat u de keuzelijst Type/Grootte, keuzelijst Koppeling, keuzelijst Taal of Tekstbewerking hebt verwijderd, keert de toetsenbordfocus terug naar de volgende of vorige gebruikersinterface-elementen of naar een relevanter gebruikersinterface-element (CQ-4293585).
   * Als u de aanwijzer op opties plaatst, worden er tips zoals Selecteren en Downloaden weergegeven. Gebruikers die een schermvergroting gebruiken, zien de miniaturen van het bestand mogelijk niet vanwege deze tips. Nu is het mogelijk om de focus te behouden nadat u de optie hebt verwijderd met `Escape` toets. (CQ-4293554).
   * Wanneer u een rastercel selecteert uit het raster dat aanwezig is op de pagina, wordt de focus verplaatst naar de actiebalk die wordt weergegeven op het scherm (CQ-4282127).
   * Visuele gebruikers kunnen onderscheid maken tussen normale tekst en een koppeling, aangezien visuele aanwijzingen (onderstreping en chevron-pictogram) worden weergegeven voor koppelingen naar alle oplossingen in [!DNL Experience Manager] homepage (CQ-428/20072).

* De volgende gebruikerservaring is verbeterd in [!DNL Assets]:

   * Het sorteren van elementen in kaart- en kolomweergave inschakelen (NPR-35097).

* Als na de upgrade naar 6.5 een JSON-bestand wordt gegenereerd met de HTTP-API voor Middelen, zijn er problemen met de codering die in het bestand wordt gebruikt (NPR-35129).

* Gebruikers van een groep die niet de machtiging heeft gekregen om verzamelingen te maken (de optie Verzameling maken is niet beschikbaar), kunnen nog steeds verzamelingen maken door rechtstreeks toegang te krijgen tot de URL `https://[aem_server]:[port]/mnt/overlay/dam/gui/content/collections/createcollectionwizard.html/content/dam/collections?contentPath=/content/dam/collections` (NPR-35115).

* Wanneer gesorteerd op naam, worden de gezochte activa gesorteerd op case-sensitive manier. Hierdoor worden twee aparte gesorteerde lijsten gemaakt op basis van de trapsgewijze lijsten die op geordende wijze in de zoekresultaten worden weergegeven (NPR-35068).

* Wanneer een inhoudsfragment wordt geopend in de editor, worden waarschuwingsberichten (`Invalid value specified for a metadata property`) zijn aangemeld bij de foutenlogboeken (NPR-35012).

* Gebruikers zonder beheerdersrechten kunnen verlopen elementen bewerken met [Experience Manager] bureaubladtoepassing. (NPR-34993).

* Wanneer hetzelfde element in de gebruikersinterface van Elementen wordt gesleept en een nieuwe versie wordt gemaakt, zijn de wijzigingen in de metagegevens niet blijvend (NPR-34940).

* Bij het bewerken van verzamelingen kan een gebruiker de titel van de verzameling verwijderen en de wijzigingen opslaan (NPR-34889).

* Wanneer u een gedupliceerde afbeelding uploadt, wordt een verwijderingsoptie weergegeven. Als u Verwijderen selecteert, kunnen de afbeeldingen worden geüpload. DAM Update Asset workflow wordt ook geactiveerd (NPR-34744).

* Wanneer u [!DNL Adobe Asset Link] with [!DNL Adobe InDesign]bevatten de zoekresultaten geen mappen en verzamelingen, maar alleen elementen (NPR-34699, CQ-4303666).

* Als u de aanwijzer op de kaartweergave plaatst, schuift het scherm als gevolg van (automatische) focus op de snelle acties die beschikbaar zijn op de kaart (NPR-34514).

* Wanneer u de eigenschappen van meerdere elementen bulksgewijs bewerkt, selecteert u de optie [!UICONTROL Save] de optie sluit de bulkredacteursmening en richt aan het belangrijkste opnieuw [!DNL Assets] pagina. Dit gedrag is hetzelfde als het gedrag van [!UICONTROL Save & Close] en niet wordt verwacht (NPR-34546).

* De slimme verzameling bevat na het opslaan niet de juiste instelling voor de gebruikersinterface. De vraag wordt bewaard behoorlijk maar de interface toont altijd de laatste toegevoegde predikaat van de Optie (NPR-34539).

* Bij het toevoegen van elementen aan [!DNL Experience Manager], worden de metagegevens zonder naamruimte niet geïmporteerd (NPR-34530).

* Wanneer u elementen naar een map sleept om deze te verplaatsen, wordt in de gebruikersinterface ook de optie weergegeven om [!UICONTROL Drop in Lightbox] en [!UICONTROL Drop in Collection]. Zelfs als de verplaatsingsbewerking wordt geannuleerd, worden in de gebruikersinterface de laatste twee opties weergegeven (NPR-34526).

* Het symbool `%>` wordt weergegeven op de pagina Verzamelingen (NPR-34499).

* In de kolomweergave, [!DNL Assets] Hiermee geeft u dubbele map- en elementnamen weer wanneer u omhoog en omlaag schuift voordat alle elementen worden weergegeven (NPR-34464).

* Als u direct na het maken van een openbare map een privémap maakt, worden in de openbare map de instellingen voor de privémap gebruikt (NPR-34415).

* In de kaartweergave worden de kaarten niet in alfabetische volgorde weergegeven en kunnen kaarten niet alfabetisch worden gesorteerd (NPR-34234).

* Bij het opnieuw openen van trapsgewijze regels blijven de opties niet behouden in de gebruikersinterface (CQ-4301452).

#### [!DNL Dynamic Media] {#dynamic-media-6570}

* De volgende verbeteringen zijn aangebracht voor toegankelijkheid in [!DNL Dynamic Media] (CQ-4290306). Zie voor meer informatie [toegankelijkheidsfuncties in [!DNL Dynamic Media]](/help/assets/accessibility-dm.md).

   * Schermlezers (JAWS, Narrator) vertellen de naam, rol en status van de menu-items in de menuoptie Grootte insluiten (CQ-4290927).
   * Gebruikers kunnen in het dialoogvenster E-mailkoppeling navigeren met het dialoogvenster `Tab` key (CQ-4290926).
   * De workflow voor het maken van videocoderingsprofielen is gebruiksvriendelijker gezien de schermlezerverbetering (CQ-4290623, CQ-4290622).
   * Bij navigeren met `Tab` belangrijk is, gaat de focus naar de juiste gebruikersinterface-elementen in de workflow om een interactieve video te maken (CQ-4290621, CQ-4290620, CQ-4290619).
   * De pagina Publiceren, Asset-pagina bewerken, Smart Crops bewerken en de pagina Editor afbeeldingsset zijn verbeterd en voldoen nu aan de webstandaarden. Gebruikers van ondersteunende technologie (AT) kunnen nu gemakkelijk door deze pagina&#39;s navigeren en acties uitvoeren zoals het bijsnijden van afbeeldingen (CQ-4290617, CQ-4290616, CQ-4290613, CQ-4290612, CQ-49) 0610, CQ-4290614).
   * Gebruikers kunnen nu beter navigeren met een toetsenbord (CQ-4290615).
   * Gebruikers van het toetsenbord en de schermlezer kunnen de uitsnijdfunctionaliteit gebruiken (CQ-4290609).
   * Gebruikers met het toetsenbord kunnen de hotspots beter beheren (CQ-4290604, CQ-4290603).

* Externe afbeeldingen kunnen niet worden bewerkt in [!DNL Experience Manager] als de naam van het bedrijf en de mapnaam gelijk zijn (NPR-31340).

* De z-indexvolgorde is onjuist wanneer u een voorbeeld van de uitvoer probeert weer te geven nadat u een hotspot aan een [!DNL Dynamic Media] afbeelding of na het bewerken van een [!DNL Dynamic Media] video of een [!DNL Experience Fragment] met een afbeelding (CQ-4307267).

* [!DNL Dynamic Media] sync mislukt wanneer gemengde mediasets opnieuw worden verwerkt (CQ-4307184).

* Als een element wordt verplaatst naar een map waarin automatische synchronisatie naar [!DNL Dynamic Media] is geconfigureerd, wordt het element niet gesynchroniseerd (CQ-4307122).

* [!DNL Dynamic Media] video wordt niet afgespeeld op iOS-apparaten met de native HTML5-videoknoppen (CQ-4306977, CQ-4306727).

* Kan geen afbeeldingen downloaden waarop SmartCrop is toegepast (CQ-4304558).

* Kan mappen niet selectief publiceren naar Dynamic Media (CQ-4304526).

* De publicatie van een videobestand ongedaan maken [!DNL Experience Manager] maak de publicatie van de Adaptive Video Set niet ongedaan op basis van een geconfigureerde Scene7-implementatie (CQ-4304405).

* Als u een panoramisch afbeeldingselement toevoegt aan een panoramisch mediacomponent en de pagina vernieuwt, resulteert dit in `Uncaught ReferenceError: $ is not defined` fout (CQ-4302810).

* In de [!UICONTROL Viewer Presets Editor], tijdens het bewerken [!UICONTROL PanoramicImage/PanoramicImage_VR] voorinstelling, in de `PanoramicView` de `PANORAMICVIEW_AUTOROTATE` label voor modifier is niet beschikbaar (CQ-4302443).

* Videobijschriften worden niet weergegeven als de video niet de eerste is in een MixedMediaSet (CQ-4298161).

* HTML5 eCatalog Viewer op mobiele apparaten met iPhones kan de pagina&#39;s niet draaien of de pagina&#39;s omdraaien (CQ-4296611).

* Wanneer u stalen op een mobiel apparaat schuift, schuiven de stalen naar rechts en uit het zichtbare gebied gedurende een paar seconden voordat u weer in beeld bladert (CQ-4296439).

* Wanneer een Voorinstelling voor viewer Master record wordt gemaakt, worden de CSS en de illustraties niet gepubliceerd en wordt alleen de voorinstelling voor viewers gepubliceerd (CQ-4262205).

* Wanneer u een ervaringsfragment probeert te koppelen voor een bepaalde hotspot in het dialoogvenster [!UICONTROL Interactive Video/Images] wordt het geselecteerde pad van het ervaringsfragment niet weergegeven. In plaats daarvan wordt een lege waarde vanuit het padveld geretourneerd (NPR-35146, CQ-4298136).

* Kan geen voorvertoning van een ervaringsfragment weergeven in de IVV Editor (CQ-4308560).

* Wanneer u een hotspot aan een afbeelding toevoegt en een ervaringsfragment selecteert, is het niet mogelijk om de submappen en de varianten van het ervaringsfragment te selecteren (CQ-4307455).

* De niet-afbeeldingselementen worden niet weergegeven zoals gepubliceerd na het uploaden (CQ-4306415).

#### [!DNL Experience Manager] 3D-elementen {#three-d-assets-6570}

* `DAM CQ MIME Type` de dienst past onjuiste MIME types op 3D activa toe die tot onjuiste teruggave leiden (NPR-34731).

### [!DNL Commerce] {#commerce-6570}

* De gebruikersinterface voor het verzamelen van handelsproducten bevat niet meer dan 15 producten binnen een collectie (NPR-34502).

### Platform {#platform-6570}

* Een HTTP-sessie via HTTPS wordt niet ongeldig gemaakt (NPR-35083).
* A `NullPointerException` wordt geretourneerd bij het starten van dagelijkse of wekelijkse onderhoudstaken vanuit de gebruikersinterface (NPR-34953).
* De W3C-validator rapporteert waarschuwingen voor compatibele JavaScript-bestanden uit de clientbibliotheek (NPR-34898).
* De `AudienceOmniSearchHandler` gebruikt een afgekeurde index (NPR-34870).
* Afmelden bij Experience Manager wist de cookies niet (NPR-34743).
* De `findByTitle` de functie van de `TagManager` API werkt niet als de tagnaam een speciaal teken bevat (NPR-34357).
* Het proces voor het importeren van het synchronisatiepakket van de gebruiker mislukt (NPR-34399).
* Extra ondersteuning voor `ariaLabel` en `ariaLabelledby` eigenschappen voor de `Coral.Masonry` component (GRANITE-29962).
* De Dispatcher-cache wordt niet vernieuwd voor pagina&#39;s met inhoudsfragmenten nadat de nieuwste kerncomponentpakketten zijn geïnstalleerd (CQ-4306788).
* Gelokaliseerde tagnamen met aanhalingstekens (`"`) niet correct worden weergegeven in de gebruikersinterface (CQ-4305439).

### Gebruikersinterface {#ui-6570}

* De [!UICONTROL Link to] veld in componenteigenschappen geeft automatisch aangevulde suggesties weer die niet overeenkomen met de opgegeven tekenreeks (NPR-34865).

* AEM geeft het volgende foutbericht weer wanneer u een dagelijks onderhoudvenster plant dat tussen twee dagen wordt verdeeld (NPR-35280):

   ```TXT
   ERROR The start time must precede (be less than) the end time
   ```

### Integraties {#integrations-6570}

* Een bestaande [!DNL Adobe Launch] configuratie mislukt (NPR-35045).
* Kan niet exporteren [!DNL Experience Fragments] tot [!DNL Adobe Target] bij gebruik van IMS-configuratie en [!DNL Adobe Target Standard] milieu (NPR-34555).
* De [!UICONTROL Create] wordt weergegeven op het tabblad [!UICONTROL Audiences] pagina bij het navigeren van een map naar de [!UICONTROL Audiences] bladzijde (NPR-35151).

### Sling {#sling-6570}

* De standaardlogin gezondheidscontrole bevestigt de geloofsbrieven van een gebruiker die niet bestaat (NPR-34686).

### Vertaalprojecten {#translation-6570}

* Bij het annuleren van een vertaalproject in [!DNL Experience Manager], wordt het verzoek tot annulering niet naar de vertaalaanbieder gezonden (NPR-34433).

### [!DNL Communities] {#communities-6570}

* Alle gevallen van onbillijke terminologie in het product worden vervangen door aanvaarde equivalenten (NPR-34311).
* [!DNL Google+] wordt verwijderd uit de lijst van opties voor sociale media (NPR-33877).

### [!DNL Brand Portal] {#brandportal-6570}

* De gebruikersinterface reageert niet bij het selecteren van de elementen in het dialoogvenster [!UICONTROL List View] (NPR-34728).

### [!DNL Forms] {#forms-6570}

>[!NOTE]
>
>[!DNL Experience Manager Forms] geeft toe:voegen-on pakketten één week na gepland vrij [!DNL Experience Manager] Releasedatum van Service Pack.

>[!NOTE]
>
>[!DNL Experience Manager] Service Pack bevat geen oplossingen voor [!DNL Forms]. Ze worden geleverd met behulp van een aparte [!DNL Forms] add-on-pakket. Daarnaast wordt een cumulatief installatieprogramma uitgebracht dat oplossingen bevat voor [!DNL Experience Manager Forms] op JEE. Zie voor meer informatie [AEM Forms-invoegtoepassing installeren](#install-aem-forms-add-on-package) en [AEM Forms installeren op JEE](#install-aem-forms-jee-installer).

**Adaptieve Forms**

* Kan een adaptief formulier niet bewerken met de klassieke gebruikersinterface nadat het is toegepast [!DNL Experience Manager] Service Pack 6 (NPR-35126).

* Wanneer u een PDF omzet in een adaptief formulier, kunt u geen waarde instellen voor een genest deelvenster met een formuliergegevensmodel in de indeling met tabbladen. Daarnaast zijn er problemen wanneer u een waarde voor Keuzerondjesgroepen dynamisch instelt met een statische array met behulp van de code-editor (NPR-35062).

* Wanneer u Japanse tekens in een adaptieve vorm in een tekstveldcomponent invoert, kunt u meer tekens opgeven dan de maximale limiet van 35 tekens (NPR-35039).

* Het adaptieve formulier geeft ongewenste parameters weer, zoals `owner` en `status`over de **[!UICONTROL Thank you]** pagina die wordt weergegeven na het verzenden van het formulier (NPR-34989).

* De [!UICONTROL File Selection] voor de [!UICONTROL Attachment] geeft de niet-ondersteunde bestandstypen ook weer voor selectie, wat resulteert in een fout tijdens het verzenden van het adaptieve formulier (NPR-34970).

* Wanneer u een adaptief formulier invoegt in een [!DNL Experience Manager Sites] op pagina die tekst vóór het formulier bevat, wordt de cursorfocus direct naar het formulier verplaatst in plaats van naar de tekst vóór het formulier (NPR-34947).

* [!UICONTROL Preview with Data] optie om een adaptief formulier vooraf in te vullen met een [!DNL Experience Manager] 6.2 gegevens-XML-bestand werkt niet naar behoren (NPR-35087).

* Wanneer u het gegevenswoordenboek voor een adaptief formulier bijwerkt, wordt het formulier niet vertaald omdat het adaptieve formulier in de cache opgeslagen waarden retourneert (NPR-34845).

* Het laden van fragmenten in adaptieve vorm duurt langer omdat de cache ongeldig wordt (NPR-34567).

* Tabnavigatie werkt niet correct voor schermlezers in adaptieve vorm (NPR-34544).

**Correspondentenbeheer**

* Kan waarden voor XML-labels met numerieke gegevens, waaronder floattype, niet opslaan als concept (NPR-35050).

* Wanneer u de activa van ES3 migreert, omvatten de activa twee niet-editable wanbetalingsvoorwaarden (NPR-34972).

* Wanneer u een gegevenswoordenboek in een letter bewerkt, wordt [!UICONTROL Lent Content] geeft draaiende rechthoeken weer in plaats van nuttige informatie (NPR-34853).

**Interactieve communicatie**

* De naam van de rollout configuratie voor Interactieve Communicatie, beschikbaar na het installeren van [!DNL Forms] add-on pakket, dupliceert de standaardnaam van de rollout-configuratie (NPR-34976).

**Documentbeveiliging**

* Als u een nieuw beveiligingsbeleid voor een document opslaat, geeft Experience Manager Forms het dialoogvenster `Relative validity period is required` foutbericht (NPR-34679).

* Documentbeveiliging kan PDF 2.0-document niet beschermen (CQ-4305851).

Voor informatie over beveiligingsupdates raadpleegt u [Pagina met beveiligingsbulletins voor Experience Managers](https://helpx.adobe.com/security/products/experience-manager.html).

## [!DNL Adobe Experience Manager] 6.5.6.0. {#experience-manager-6560}

Adobe Experience Manager 6.5.6.0 is een belangrijke update die nieuwe eigenschappen, zeer belangrijke klant gevraagde verhogingen, en prestaties, stabiliteit, en veiligheidsverbeteringen omvat die sinds de algemene beschikbaarheid van versie 6.5 in **April 2019**. Deze kan boven op Adobe Experience Manager 6.5 worden geïnstalleerd.

De belangrijkste functies en verbeteringen die in Adobe Experience Manager 6.5.6.0 zijn geïntroduceerd, zijn:

* Elementen selectief publiceren of de publicatie ervan ongedaan maken [!DNL Experience Manager] of [!DNL Dynamic Media] gebruiken [!UICONTROL Quick Publish] of [!UICONTROL Manage Publication] wizard.

* Gebruik de [!DNL Dynamic Media] gebruikersinterface om inhoud in cache van CDN (Content Delivery Network) ongeldig te maken.

* Het publiceren van mappen voor middelenbijdragen van Brand Portal naar Experience Manager Assets wordt nu ook ondersteund via proxyserver.

* De automatisch gegenereerde groepen privémappen worden nu opgeschoond wanneer de persoonlijke map in [!DNL Experience Manager Assets].

* De beschrijvingen van modifiers in video [!UICONTROL Viewer] editor met voorinstellingen is bijgewerkt in [!DNL Dynamic Media].

* Er wordt een nieuwe ondernemingsinstelling aangeboden die de status van [!DNL Dynamic Media] -aansluiting.

* De standaardopties voor `test` en `aiprocess` worden bijgewerkt naar `Thumbnail`, van `Rasterize` eerder in Dynamic Media, om ervoor te zorgen dat gebruikers alleen miniaturen hoeven te maken en de extractie van pagina&#39;s en trefwoorden overslaan.

* [Een adaptief formulier vooraf invullen op de client](../../help/forms/using/prepopulate-adaptive-form-fields.md#prefill-at-client).

* [Integratie van formuliergegevensmodellen met RESTful-API&#39;s op een server met 2-wegs SSL-implementatie](../../help/forms/using/configure-data-sources.md).

* [Verbeterd in cache plaatsen voor vertaalde adaptieve formulierpagina&#39;s](../../help/forms/using/configure-adaptive-forms-cache.md).

* Ondersteuning voor [Adobe Sign Text Tags in Automatede form conversion Service](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/convert-existing-forms-to-adaptive-forms.html).

* Ondersteuning voor [gekleurde formulieren omzetten in aangepaste formulieren](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/convert-existing-forms-to-adaptive-forms.html) gebruiken [!DNL Automated Forms Conversion service].

* Steun voor SMB 2 en SMB 3 protocollen.

* De ingebouwde opslagplaats (Apache Jackrabbit Oak) wordt bijgewerkt naar versie 1.2.2.4.

Voor een volledige lijst van eigenschappen en verhogingen die in Experience Manager 6.5.6.0 worden geïntroduceerd, zie [Nieuw in Adobe Experience Manager 6.5 Service Pack 6](new-features-latest-service-pack.md).

Hieronder volgt een lijst met oplossingen die u vindt in [!DNL Experience Manager] 6.5.6.0 release.

### [!DNL Sites] {#sites-6560}

* In [!DNL Sites] of [!DNL Screens]selecteert u een project en klikt u op [!UICONTROL Management Publications]. Gebruikers kunnen niet verdergaan in de [!UICONTROL Manage Publication] vanwege gebruikersinterfacefouten. In het bijzonder de [!UICONTROL Publish] werkt niet (NPR-34099).
* De positie van iParsys (het Overgenomen Systeem van de Paragraaf) wordt niet teruggekeerd aan zijn originele standaardpositie na het deselecteren [!UICONTROL Cancel Inheritance] of [!UICONTROL Disable Inheritance] (NPR-34097).
* Als de `RolloutConfigManagerFactoryImpl` kan geen rollout config laden, probeert het niet om de ontbrekende vormen te laden. Het keert de caching configuraties (NPR-34092) terug.
* In de kerncomponent Text, na gebruik van de HTML-bronbewerkingsoptie, de klasse van `em` -tag wordt verwijderd (NPR-34081).
* Na het upgraden van Experience Manager 6.3.3 naar Experience Manager 6.5.3 duurt het uitrolproces veel langer en mislukt de uitrol met een time-outfout (NPR-34049).
* De `htmlwriter` codeert de kenmerkwaarden niet terug. De opmaak die aanwezig is in de XF-opmaak wordt geëxporteerd met gedecodeerde kenmerkwaarden (namelijk `"` in plaats van `&#34`). Het veroorzaakt kwesties op de kant van het Doel met Visuele Composer van de Ervaring die uitgevoerde XF (NPR-34048) gebruikt.
* Wanneer u pagina&#39;s verplaatst in [!DNL Experience Manager Sites], verbeter het registreren om de fout van de versieverwezenlijking met reden (NPR-34014) te vangen.
* In [!DNL Rich Text Editor] Als alle tekst wordt verwijderd, wordt het alinealabel ook verwijderd (NPR-33976).
* Wanneer de `siteadmin` pagina (in de klassieke gebruikersinterface) wordt geopend of vernieuwd, worden de opties in het dialoogvenster `New` worden uitgeschakeld (NPR-33949).

   ![Screenshot om het probleem van het ontbreken van een menu in de klassieke gebruikersinterface te illustreren](assets/33949_missing_menu.png)

* A [!DNL Content Fragment] kan niet worden gebruikt als een `TemplatedResource` aangezien het binnen ontbreekt `ContentFragmentUsePojo` (NPR-33911).
* Synchrone en asynchrone verplaatsingsbewerkingen kunnen leiden tot fouten als gevolg van gelijktijdige overdrachten. Verplaatsingsbewerkingen voor pagina&#39;s zijn beperkt tot alleen asynchrone verplaatsing. Hiermee wordt gelijktijdige verplaatsing van pagina&#39;s voorkomen (NPR-33875).
* [!UICONTROL Manage Publication] bewerking voor het repliceren van inhoud van de instantie Auteur naar instantie Publiceren mislukt en genereert een JavaScript-fout (NPR-33872).
* Wanneer u meerdere pagina&#39;s of middelen hebt geselecteerd om versies te maken, wordt de nieuwe versie alleen gemaakt voor de laatst geselecteerde pagina of het laatst geselecteerde element (NPR-33866).
* Verplaats een pagina met een blauwdruk met live kopieën naar een andere map. Wanneer u de afbeelding naar de oorspronkelijke map verplaatst, mislukt de verplaatsing zonder fout (NPR-33864).
* Wanneer de verplaatsingsactie wordt gebruikt om een Web-pagina in anders te noemen [!DNL Sites] Console, toont het twee overlappende dialogen bij de laatste stap van de tovenaar (NPR-33831).

   ![Screenshot ter illustratie van NPR-33831-probleem van overlappend dialoogvenster voor verplaatsen](assets/33831_rename_dialog.png)

* De `cq:acLinks` en `cq:acUUID` eigenschappen voor [!DNL Adobe Campaign] op de kopie worden verwijderd tijdens kopiëren en plakken (NPR-33794).
* Wanneer u een rollout probeert te maken op een onderliggende pagina van een losgekoppelde bovenliggende live kopie, [!DNL Experience Manager] genereert een null pointer-uitzondering (NPR-33676).
* De [!DNL RTE] componenten in een lay-outcontainer zijn niet zichtbaar wanneer de lay-outcontainer wordt gekopieerd en opnieuw op de pagina geplakt. De [!DNL RTE] onderdelen kunnen niet worden bewerkt, maar worden wel weergegeven wanneer de pagina wordt vernieuwd (NPR-33662).
* Wanneer u de grootte van een lay-outcomponent wijzigt voor verschillende (middelgrote en grote) onderbrekingspunten, gedraagt de lay-out zich niet zoals verwacht (NPR-33608).
* In de inline bewerkingsmodus in [!DNL RTE], werkt het slepen van een afbeelding niet voor de component Text (NPR-33602).
* Het is mogelijk om een component op een blauwdrukpagina met dezelfde naam als de paginanaam te maken. Tijdens de rollout `_msm_moved` is achtervoegd om de naam van de component te wijzigen. De component wordt verplaatst naar het einde van de [!UICONTROL Paragraph System] (NPR-33535).
* Wanneer offTime of onTime op vele pagina&#39;s of activa wordt geplaatst, is het middel-intensief en vertraagt het systeem tijdens opstarten en sluiting (NPR-33482).
* Een gebruiker met CRUD-machtigingen op `/content/experience-fragment` kan een map niet verwijderen (NPR-33436).
* U kunt [!UICONTROL HTML & JSON] als de optie voor [!UICONTROL Adobe Target export format] in een bovenliggende map in [!DNL Experience Fragments] sectie. Dezelfde eigenschappen worden weergegeven in een interface met aanraakfuncties voor de submappen van deze bovenliggende map. In CRXDE echter, voor `cq:adobeTargetExportFormat`wordt alleen HTML weergegeven in plaats van `html,json` (NPR-33423).
* Publiceren of Publiceren ongedaan maken van een pagina-alias wordt niet ondersteund. Verwijder de optie die anders lijkt te zijn (NPR-33415).
* Een specifieke tag kan van de ene locatie naar de andere worden verplaatst in [!DNL Experience Manager]. Deze kan ook op verschillende pagina&#39;s worden toegepast vóór en na het verplaatsen. Wanneer u de eigenschappen van de pagina&#39;s bewerkt, wordt de tag niet weergegeven voor bewerking, ook al is de tag gelijk (NPR-33353).
* Een paginasjabloon wordt niet correct weergegeven wanneer een lay-outcontainer wordt verwijderd uit een sjabloon die meerdere lay-outcontainers bevat (NPR-33347).
* Probeer in de sjablooneditor een sjabloon te verwijderen die door meer dan 100000 pagina&#39;s onder `/content/`. Er wordt een fout weergegeven zonder foutbericht (NPR-33312).
* Omleiden naar [!DNL Experience Manager] pagina met anker werkt niet als `PageRedirectServlets` plaatst querytekenreeks na een URL-fragment of anker (NPR-34288).
* Een merk maken onder `/content/campaign` resulteert in een structuur die het niet mogelijk maakt campagnes te maken. [!UICONTROL Create Brand] laat het nieuwe merk onveranderd [!UICONTROL Offers and Activities] omdat er geen [!UICONTROL Create] (NPR-34113).
* U kunt de [!DNL Live Copy] van een pagina en de overerving zijn verbroken in de weergave Editor. In de pagina-eigenschappen geeft het pictogram dat overerving vertegenwoordigt onjuist aan dat de overerving bestaat en niet wordt verbroken (NPR-34017).
* Pagina&#39;s met veel verwijzingen kunnen niet asynchroon worden verplaatst en soms mislukt de verplaatsingsbewerking (CQ-4297969).
* Een webpagina met `/` in de URL reageert niet tijdens het ontwerpen. Wanneer een component tijdens het ontwerpen wordt toegevoegd, neemt het CPU-gebruik toe en reageert de browser niet meer (CQ-4295749).
* In de modus Bladeren wordt een waarde die u in het menu Type/Grootte hebt geselecteerd, niet door NVDA van commentaar voorzien. De visuele focus is niet op het geselecteerde element. Gebruikers die op een schermlezer vertrouwen, kunnen de modus Bladeren niet gebruiken (CQ-4294993).
* Wanneer gebruikers een webpagina maken, kunnen ze [!UICONTROL Content Page] sjabloon. In de [!UICONTROL Social Media] tabblad, selecteren gebruikers een [!UICONTROL Preferred XF variation]. Gebruikers kunnen geen toetsenbordtoetsen gebruiken om een Experience Fragment in de NVDA-bladermodus te selecteren (CQ-4292669).
* De handbalkbibliotheek is bijgewerkt naar versie 4.7.3 (NPR-34484) met meer beveiliging.
* Meerdere cross-site scriptinstanties in [!DNL Experience Manager Sites] componenten (NPR-33925).
* Het veld Mapnaam bij het maken van een nieuwe map is kwetsbaar voor opgeslagen cross-site scripting (GRANITE-30094).
* De zoekresultaten op het tabblad[!UICONTROL  Welcome] pagina&#39;s en de padvoltooiingssjabloon zijn kwetsbaar voor cross-site scripting (NPR-33719, NPR-33718).
* Als u een binaire eigenschap maakt op een ongestructureerd knooppunt, wordt naar andere sites cross-site scripting uitgevoerd op het dialoogvenster voor binaire eigenschappen (NPR-33717).
* Scripts voor meerdere sites gebruiken [!UICONTROL Access Control Test] op de CRX DE-interface (NPR-33716).
* Gebruikersinvoer wordt niet op de juiste wijze gecodeerd voor verschillende componenten bij het verzenden van informatie naar de client (NPR-33695).
* Scripts voor andere sites in de kalenderweergave voor Experience Manager Inbox (NPR-33545).
* Een URL die eindigt met `childrenlist.html` geeft een pagina HTML weer in plaats van een reactie van 404. Dergelijke URL&#39;s zijn kwetsbaar voor cross-site scripting (NPR-33441).


### [!DNL Assets] {#assets-6560}

**Toegankelijkheidsverbeteringen in Experience Manager Assets**

* Met behulp van de toetsenbordtoetsen kunnen gebruikers nu toegang krijgen tot de interactieve gebruikersinterfaceopties en zich hierop concentreren in het dialoogvenster [!UICONTROL References] lijst van activa (NPR-34115).

* De schermlezer kondigt nu de bedoelde actie aan van de voorspelling op de zoekpagina (NPR-34104).

* De pagina met zoekresultaten en de pagina met zoekresultaten hebben nu meer informatieve titels voor een beter begrip van schermlezers (NPR-34093).

* Schermlezers kondigen nu de opties aan om de geselecteerde tags te verwijderen in [!UICONTROL Basic] tabblad van element [!UICONTROL Properties] bladzijde (NPR-33972).

* De elementen in elke rij in de lijstweergave worden nu door schermlezers aangekondigd als de elementen van dezelfde rij (NPR-33932).

* Focus van gebruiker bij navigeren met `Tab` De toets gaat nu naar de optie close in de voorvertoning van de versie (NPR-33863).

* De focus van de gebruiker wordt nu naar het zoekpictogram verplaatst nadat het onderzoek is gesloten (NPR-33705).

* De opties voor de gebruikersinterface die u kunt activeren, hebben nu een prominentere visuele focus met verbeterd contrast wanneer u navigeert met behulp van toetsenbordtoetsen. De gebruikers van het toetsenbord kunnen de gebieden met focus identificeren (NPR-33542).

* De sleepfunctionaliteit met het toetsenbord werkt nu in [!UICONTROL Metadata Schema Editor] in de bladermodus van schermlezer (CQ-4296326).

* In het dialoogvenster voor het delen van koppelingen navigeert u in de bladermodus door een schermlezer.

   * De tabelinformatie wordt niet van commentaar voorzien zodra het dialoogvenster is geladen.

   * Kan naar alle vermelde automatische suggesties navigeren.

   * Hiermee worden de weergegeven automatische suggesties voor de [!UICONTROL Add Email Address/Search] (CQ-4294232).

* Gebruik van de `Esc` om de snelactiepictogrammen uit de kaartweergave te verwijderen, wordt de toetsenbordfocus niet langer van het laatste item met focus verwijderd (CQ-4293554).

* Voor interactieve opties in de gebruikersinterface worden nu het doel van de pictogrammen door de schermlezer aangegeven in plaats van de letterlijke namen (CQ-4272943).

* Toetsenbordfocus wordt nu verplaatst naar [!UICONTROL Flyout], [!UICONTROL InlineZoom], [!UICONTROL Shoppable_Banner], [!UICONTROL Zoom_dark], [!UICONTROL Zoom_light], [!UICONTROL ZoomVertical_dark], en [!UICONTROL ZoomVertical_light] opties bij navigeren met de Tab-toets op het toetsenbord in de elementdetails [!UICONTROL Viewers] in [!DNL Dynamic Media] (CQ-4290605).

* [!UICONTROL Save & Close] optie voor element [!UICONTROL Properties] De pagina kan nu worden geopend met behulp van toetsenbordtoetsen (NPR-34107).

* Foutberichten als gevolg van onjuiste combinaties van gebruikersnaam en wachtwoord op de aanmeldingspagina worden nu door schermlezers gemeld wanneer de fout optreedt (NPR-33722).

* In [!DNL Experience Manager] koptekstsectie, wanneer u in de bladermodus navigeert, meldt de schermlezer dit nu;

   * Suggesties die automatisch worden bewerkt in [!UICONTROL Type to search] in Omnissearch.

   * De toestand als uitgevouwen of samengevouwen voor [!UICONTROL Solutions], [!UICONTROL Help], [!UICONTROL Inbox], en [!UICONTROL User] opties.

   * De [!UICONTROL Searching Help] statusbericht dat wordt weergegeven wanneer de gebruiker een zoektekenreeks invoert in [!UICONTROL Search for Help] veld onder [!UICONTROL Help] optie.

   ![Menu Help in koptekst](assets/Help_aem_header.png)

   *Afbeelding: [!UICONTROL Search for Help] in [!UICONTROL Help] -menu.*

   * Het foutbericht als er een onjuiste waarde is ingevoerd [!UICONTROL Impersonate as] veld onder [!UICONTROL User] en verplaatst de focus correct naar het tekstveld (NPR-33804).

   ![Menu Gebruiker in koptekst](assets/User_aem_header.png)

   *Afbeelding: [!UICONTROL Impersonate as] veld in [!UICONTROL User] in de koptekst.*

* De gebruiker kan nu de focus wijzigen met het toetsenbord binnen:

   * [!UICONTROL Search/Add Email Address] in het [!UICONTROL Link Sharing] .

   * [!UICONTROL Add User or Group] veld onder [!UICONTROL Closed User Group] in de [!UICONTROL Permissions] tabblad van map [!UICONTROL Properties] (NPR-34452).

**In Experience Manager Assets opgeloste problemen**

[!DNL Adobe Experience Manager] 6.5.6.0. [!DNL Assets] bevat oplossingen voor de volgende problemen:

* Annotaties worden niet gemarkeerd wanneer deze worden geselecteerd in de tijdlijn van het element (CQ-4302422).

* Voorvertoning van marketingonderpandselementen (zoals brochure, Flyer en Business Card) die zijn gemaakt met [!DNL Adobe InDesign] De sjabloon geeft geen regeleinden en alinea-einden weer (NPR-34268).

* Het uitnemen van tekst en dus het zoeken naar de geüploade PDF-bestanden in volledige tekst werkt niet (NPR-34164). Als u het wilt repareren, start u de [!DNL sAdobe Experience Manager] implementatie na installatie van Service Pack 6.

* In de tijdlijn van elementen die uit meerdere pagina&#39;s bestaan, worden annotaties weergegeven die op alle subelementen zijn toegepast wanneer u in het element bladert in de tijdlijnweergave, in plaats van de annotaties weer te geven die specifiek zijn voor de specifieke subelementen (NPR-34100).

* Elementenmappen worden niet gepubliceerd met [!UICONTROL Manage Publication] als de mappen bronnen bevatten in de bestandsindelingen JavaScript, CSS of JSON (NPR-34090).

* Wanneer u de selectie of het verwijderen van de toegepaste tags of filters in Omnsearch opheft, wordt de zoekquery meerdere keren uitgevoerd. Dit leidt tot een langere zoektijd (NPR-34078).

* In de kaartweergave wanneer een workflow (op een middel in een map) wordt uitgevoerd of in behandeling is, wordt de pagina opnieuw geladen totdat de workflow is voltooid of beëindigd. Auteurs kunnen dan ook niet werken met die middelen in de map waarvoor ze moeten schuiven (NPR-33986).

* Als de gebruiker een gepubliceerd element naar een nieuwe locatie verplaatst, wordt het element opnieuw gepubliceerd, zelfs als [!UICONTROL Republish] is uitgeschakeld. Dit leidt tot vele zwevende elementen die op de publicatie-instantie liggen. Het standaardgedrag is echter dat de publicatie van een gepubliceerd element automatisch wordt ongedaan gemaakt door de verplaatsingsbewerking. dit element wordt opnieuw gepubliceerd als de auteur het [!UICONTROL Republish] optie bij het verplaatsen van het actief (NPR-33934).

* De [!UICONTROL Move Assets] pagina voor elementen in verzamelingen laadt niet alle HTML-inhoud, zoals [!UICONTROL Adjust/ Republish] optie. Daarom kunnen gebruikers de verplaatsingsbewerking niet voltooien (NPR-33860).

* Als u een element verplaatst en speciale tekens toevoegt in de naam en de titel van de verplaatste elementen, wordt een extra map (met dezelfde naam) gemaakt op de nieuwe locatie van het element (NPR-33826).

* [!UICONTROL Download] knop voor een element wordt uitgeschakeld wanneer [!UICONTROL Email] optie is geselecteerd op de [!UICONTROL Download] dialoog (NPR-33730).

* De fout &quot;Request-URI too long&quot; wordt waargenomen bij het uitvoeren van bulkbewerkingen op elementen, zoals het bewerken van bulkmetagegevens (NPR-33723).

* Er is een JavaScript-fout opgetreden en gebruikers kunnen de opties die zijn gegenereerd in [!UICONTROL Dropdown] veld voor [!UICONTROL Add through JSON path] in de [!UICONTROL Folder Metadata Schema Form Editor], als het geüploade JSON-bestand waarde heeft voor spatie of speciale tekens (NPR-33712).

* De statische vertoningen van elementen worden niet bijgewerkt wanneer het element wordt bijgewerkt met [!UICONTROL Open] optie in [!DNL desktop app] of [!DNL Adobe Asset Link] en worden gesynchroniseerd naar [!DNL Adobe Experience Manager] (CQ-4296/279).

* In de kolomweergave verplaatst de verplaatsingsbewerking voor een set elementen ook de elementen die zijn geselecteerd voordat deze werden gebruikt [!UICONTROL Filter] voor hen. Let op: gebruik van [!UICONTROL Filter] Hiermee heft u de selectie van de vorige selectie op (NPR-34018).

* Backslashes worden toegevoegd vóór speciale tekens in zoeksuggesties voor elementen, die speciale tekens in hun naam hebben (NPR-33834).

* Bij het maken van regels voor vervolgkeuzelijsten in [!UICONTROL Folder Metadata Schema Form]kan de gebruiker geen waarden selecteren uit [!UICONTROL Field Choices] kolom (CQ-4297530).

* Het aangepaste workflowmodel voor elementen die tijdens runtime worden gebruikt (gemaakt in `/var/workflow/models/dam`) wordt verwijderd wanneer u installeert [!DNL Experience Manager] 6.5 Service Pack 5 of een vorige versie op [!DNL Experience Manager] 6.5 (NPR-34532). Als u de runtimekopie wilt ophalen, synchroniseert u de ontwerptijdkopie van het workflowmodel met de runtimekopie met de HTTP-API:
   `<designModelPath>/jcr:content.generate.json`.

**In Dynamic Media opgeloste problemen**

* Als de gebruiker de coderingsinstellingen definieert in bewerkingen nadat het videoprofiel is gemaakt, worden de instellingen voor slimme uitsnijdingen verwijderd uit videoprofielen (CQ-4299177).

* Elementen flikkeren bij het laden van de pagina wanneer de gebruiker schakelt tussen opties voor naast elkaar (bijvoorbeeld [!UICONTROL Overview], [!UICONTROL Timeline], [!UICONTROL Viewers]) op de pagina met gegevens over activa (NPR-34235).

* De volgende problemen worden waargenomen bij het opnieuw verwerken van de taak:

   * Taak-id ontbreekt in taakgreep die wordt geretourneerd door herverwerkingstaak.

   * Alleen bestandsnaam en niet volledig pad worden opnieuw verwerkt in taak voor videologboeken.

   * Herverwerkingstaak heeft geen optie om het elementtype als statisch in te stellen.

   * `ExcludeFromAVS` geen optie is opgegeven (CQ-4298401).

* De functie Slim uitsnijden mislukt met een fout wanneer een afbeeldingsprofiel wordt toegevoegd aan een map met meerdere (bijvoorbeeld 11) hoogte-breedteverhoudingen (NPR-34082).

* Workflow voor DAM-updatebestanden wordt geactiveerd wanneer de gebruiker omlaag schuift [!UICONTROL Workflow Archive] pagina op [!UICONTROL Workflow] tab within [!UICONTROL Tools] in [!DNL Adobe Experience Manager] geconfigureerd met Dynamic Media Scene7 (CQ-4299727).

* Symbolen in [!UICONTROL Behavior] tabblad van [!UICONTROL Viewer Preset Editor] niet gelokaliseerd zijn (CQ-4299026).

* In de hoofdweergave wordt de afbeelding in een onjuiste lay-out weergegeven die niet in de viewer past, als de viewer in de responsieve modus staat (CQ-4298293).

* Wijzigingen in voorinstellingen voor afbeeldingen in [!UICONTROL Adobe Experience Manager] synchroniseren niet met Scene7 Publishing System (CQ-4299713).

### [!DNL Commerce] {#commerce-6560}

* Koppelingen naar activa van producten worden niet geheroriënteerd wanneer activa worden verplaatst (NPR-34098).

### Platform {#platform-6560}

* Kan logboeken niet downloaden met het hulpprogramma Diagnosis op een geüpgrade Experience Manager-instantie (NPR-34336).
* De verbetering ontbreekt met een fout toe te schrijven aan gebiedsdelen op een specifieke versie van `cq-wcm-api` stichtingspakket (CQ-4300520).
* De standaardwaarden voor de **[!UICONTROL Connect Timeout]** en **[!UICONTROL Socket Timeout]** De montages voor de Configuratie Default Agent (publiceren) worden niet gespecificeerd (NPR-33707).
* Updates van de toewijzingsconfiguratie onder `/etc/map.publish` niet op de sitepagina&#39;s weerspiegelen (NPR-34015).
* [API-naslagdocumentatie](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/tagging/package-summary.html) bevat niet de documentatie voor de `com.day.cq.tagging` pakket (CQ-4295864).

### Gebruikersinterface {#ui-6560}

* In de interface van de browser Offloading worden niet alle taakonderwerpen weergegeven (NPR-34308).
* De [Configuratiebrowser](/help/sites-administering/configurations.md) niet alle configuraties worden weergegeven (NPR-33644).
* Bij het indrukken van de `Esc` als u wilt zoeken naar gebruikers die zich moeten laten verpersoonlijken, **[!UICONTROL User]** wordt gesloten in plaats van de gebruikerslijst (NPR-34084).

### Integraties {#integrations-6560}

* Activiteiten met lange namen worden niet gesynchroniseerd met [!DNL Adobe Target] (NPR-34254).

* Wanneer u een eigenschap selecteert terwijl u een nieuwe configuratie voor het starten van de Adobe maakt, wordt het volgende foutbericht weergegeven (NPR-33947):

   ```javascript
   GET http://hostname:Port/libs/cq/dtm-reactor/content/configurations/createcloudconfigwizard/jcr:content/body/items/form/items/wizard/items/general/items/fixedcolumns/items/container/items/general/items/property/data.html?query=&start=0&end=25&imsConfigurationId=Adobe%20Launch&companyId=&_charset_=utf-8 400 (Bad Request)
   ```

### Omzettingsprojecten {#translation-6560}

* Er wordt geen vertaalproject gemaakt als de gebruiker `authorizableID` bevat speciale tekens (NPR-33828).

### Sling {#sling-6560}

* Health Check en Pattern Detector hebben overlappende functionaliteit. Hierdoor wordt de gezondheidscontrole uit het product verwijderd (NPR-33928).

### WCM {#wcm-6560}

* De Componenten van de stichting - wanneer u een component van het stichtingsbeeld aan een pagina toevoegt en een beeld van verwijzingen voorziet, `Undo` De bewerking werkt niet (NPR-34516).

* Kan de bewerking Pagina verplaatsen niet gebruiken (CQ-4303028).

### [!DNL Communities] {#communities-6560}

* Bij het delen van een artikel op sociale media is de optie Google+ verouderd (NPR-33877).

* Lid van de Gemeenschap kan groepsmalplaatje of andere montages van de Functie van de Groep niet wijzigen (NPR-33530).

* Hyperlink-tags op afbeeldingen worden niet correct gegenereerd in een forumbericht (NPR-33464).

* Toegankelijkheidsproblemen worden geïdentificeerd in de communautaire toewijzingsfunctie (NPR-33442).

* De bestaande gebruikers van een communautaire groep die via admin console wordt toegevoegd worden verwijderd uit de gebruikerslijst op om het even welke wijziging in de communautaire groepsconsole (NPR-34315).

* De `TagFilterServlet` lekt potentieel gevoelige gegevens (NPR-33868).

<!--
* Tag filters are vulnerable to sensitive information disclosure (NPR-33868).
-->

### [!DNL Forms] {#forms-6560}

>[!NOTE]
>
>[!DNL Experience Manager] Service Pack bevat geen oplossingen voor [!DNL Forms]. Ze worden geleverd met behulp van een aparte [!DNL Forms] add-on-pakket. Daarnaast wordt een cumulatief installatieprogramma uitgebracht dat oplossingen bevat voor [!DNL Experience Manager Forms] op JEE. Zie voor meer informatie [AEM Forms-invoegtoepassing installeren](#install-aem-forms-add-on-package) en [AEM Forms installeren op JEE](#install-aem-forms-jee-installer).

Nadat u de [!DNL Experience Manager Forms] 6.5.6.0 add-onpakket:

* Stop de [!DNL Experience Manager Forms] -instantie.

* Verwijderen `bcpkix-1.51`, `bcmail-1.51`, en `bcprov-1.51` JAR-bestanden van de `crx-repository\launchpad\ext` directory.

* Verwijderen` sling.bootdelegation.class.org.bouncycastle.jce.provider.BouncyCastleProvider` eigenschap van de `sling.properties` bestand.

* Start de [!DNL Experience Manager Forms] -instantie.

**Adaptieve Forms**

* Als er een ontbrekend adaptief formulierfragment is, kan het adaptieve formulier niet worden weergegeven (NPR-34302).

* In de beschrijving van de Help-inhoud van een adaptief formulierveld wordt een alinea HTML-label weergegeven (NPR-34116).

* Wanneer u **[!UICONTROL Revalidate on Server]** eigenschap, het adaptieve formulier niet wordt ingediend (NPR-33876).

* De **[!UICONTROL Submit to REST endpoint]** submit action does not work for an adaptive form (CQ-4299044).

* Toegankelijkheid: Wanneer u een adaptief formulier probeert te verzenden zonder een bijlage voor een verplicht veld te uploaden, wordt de focus niet automatisch naar het bijlageveld (CQ-4298065).

* Wanneer u rijen toevoegt aan een tabel van een adaptief formulier, wordt de **[!UICONTROL Add to top]** en **[!UICONTROL Add to bottom]** geeft geen geschikte resultaten weer (CQ-4297511).

* De [!UICONTROL Value Commit] script wordt onjuist geactiveerd, wat resulteert in gegevensverlies in een adaptieve vorm (CQ-4296874).

* De Datumkiezer werkt niet correct voor gelokaliseerde adaptieve formulieren (NPR-34333).

* Als de bestandsnaam een onderstrepingsteken of een spatie bevat, kunt u het bestand niet aan een adaptief formulier koppelen (CQ-4301001).

* Wanneer een genest herhaalbaar deelvenster meer voorvallen heeft dan het bovenliggende deelvenster, wordt het geneste herhaalbare deelvenster niet voorafgegaan (NPR-33666).

* Aangepaste formulieren hebben enkele open resourceoplossers. Deze leiden tot mislukte indiening. Het probleem doet zich af en toe voor (CQ-4299407).

* Wanneer u de veldconfiguratie voor het eerst opent, wordt het eigenschappenpictogram niet weergegeven (CQ-4296284).

* Gebruikers kunnen metagegevens voor verzending bewerken, zoals `afPath`, `afSubmissionTime` en `signers`, wanneer een adaptief formulier wordt ingediend. Om het probleem op te lossen, worden de metagegevenswaarden verwijderd uit de formulierverzendgegevens op de client. Gebruikers kunnen de `FormSubmitInfo` object om deze waarden op te halen van de server (NPR-33654).

* Gebruikersinvoer is niet correct gecodeerd voor [!DNL Forms] componenten bij het verzenden van informatie naar de cliënt (NPR-33611).

**Workflow**

* Wanneer een werkstroomfiatteur een bijlage uploadt, wordt de naam van de bijlage gewijzigd in `undefined` (NPR-33699).

* [!DNL Experience Manager] De werkstroom leegmaken mislukt en geeft het volgende foutbericht weer (NPR-33575):

   `java.lang.UnsupportedOperationException: The query read more than 500000 nodes in memory`

* [!DNL Experience Manager Forms] app voor [!DNL Windows] reageert niet meer na het verzenden van een formulier (NPR-34409).

* Wanneer u AEM Service Pack installeert, **Taak** lijst met items wordt niet weergegeven als koppelingen. De tekst voor de **Taak** Voorbeelden van items zijn HTML-tags (NPR-34317).

**Interactieve communicatie**

* Wanneer u een tekstdocumentfragment met geneste herhaalbare componenten opneemt, kan de interactieve communicatie niet worden opgeslagen (NPR-34095).

**Correspondentenbeheer**

* Wanneer u een fragment van het tekstdocument wijzigt dat de waarden van het gegevenswoordenboek omvat, houdt UI van de Agent op antwoordend (NPR-33930).

* Inhoud kopiëren en plakken uit een [!DNL Microsoft Word] Als u documenten naar een tekstdocumentfragment in een letter verplaatst, resulteert dit in opmaakproblemen (NPR-33536).

**Document Services**

* Wanneer u een PDF-bestand genereert op basis van een XDP-bestand met Output- en Forms-services, resulteert dit in ontbrekende en overlappende tekst (NPR-34237, CQ-4299331).

* Wanneer u een HTML-bestand omzet in PDF, worden de `MaxReuseCount` attribuut is niet configureerbaar (NPR-33470).

* Wanneer u een PDF-bestand downloadt dat interactieve functies voor extensies voor Readers bevat, kunt u geen bijlage aan het PDF-bestand toevoegen met [!DNL Adobe Reader] (NPR-33729).

**Documentbeveiliging**

* Kan de ondertekeningsbewerking met HSM-certificaten niet uitvoeren in een PDF-bestand na installatie [!DNL Experience Manager] Service Pack (NPR-34310).

**Designer**

* Kan XForms niet openen in Designer versie 6.5.x (CQ-4295322).

* Wanneer u Designer opent, wordt in het welkomstscherm een onjuist jaar weergegeven (CQ-4295289).

* Wanneer u [!DNL Acrobat DC] op de server **[!UICONTROL Distribute Form]** is inactief (CQ-4296304).

Voor informatie over beveiligingsupdates raadpleegt u [Pagina met beveiligingsbulletins voor Experience Managers](https://helpx.adobe.com/security/products/experience-manager.html).

## [!DNL Adobe Experience Manager] 6.5.5.0. {#experience-manager-6550}

Adobe Experience Manager 6.5.5.0 is een belangrijke update die nieuwe eigenschappen, zeer belangrijke klant gevraagde verhogingen, en prestaties, stabiliteit, en veiligheidsverbeteringen omvat die sinds de algemene beschikbaarheid van versie 6.5 in **April 2019**. Deze kan boven op Adobe Experience Manager 6.5 worden geïnstalleerd.

Enkele belangrijke functies en verbeteringen die zijn geïntroduceerd in [!DNL Adobe Experience Manager] 6.5.5.0 omvat:

* Anonieme toegang tot CRXDE Lite is niet toegestaan. In plaats daarvan worden de gebruikers naar het aanmeldingsscherm geleid. Zie [Ontwikkelen met CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md).

* De kolomnamen aanpassen die worden weergegeven in [!DNL Adobe Experience Manager] Postvak IN.

* Verbeterde toegankelijkheid op diverse gebieden in het Beheer van de Inhoud van het Web van de Experience Manager (WCM) zoals de Redacteur van de Pagina, de Componenten van de Kern, RTE, en Admin gebruikersinterface.

* Een [!DNL Interactive Communication] als concept.

* Ondersteuning voor [!DNL Oracle WebLogic 12] voor Experience Manager Forms op JEE.

* Verbeterde uitzonderingenbehandeling in [!DNL Adobe Experience Manager Assets] gebruikersinterfacestroom.

* Een nieuwe methode voor het publiceren van een URL voor Dynamic Media Scene7 `getRemoteAssetPublishURL` wordt toegevoegd aan `com.day.cq.dam.api.s7dam.scene7.ImageUrlApi` interface.

* [Verbeteringen voor toegankelijkheid](#assets-6550) in [!DNL Adobe Experience Manager Assets] in overeenstemming met de Web Content Accessibility Guidelines (WCAG).

* Integratie met delen van pakket is verwijderd uit Adobe Experience Manager.

* De ingebouwde opslagplaats (Apache Jackrabbit Oak) wordt bijgewerkt naar versie 1.22.3.

Voor volledige lijst van eigenschappen, zeer belangrijke hoogtepunten, zeer belangrijke eigenschappen die in Experience Manager 6.5 Service Pack 5 worden geïntroduceerd, zie [Nieuw in Adobe Experience Manager 6.5 Service Pack 5](new-features-latest-service-pack.md) .

Hieronder volgt een lijst met oplossingen die u vindt in [!DNL Experience Manager] 6.5.5.0 release.

### [!DNL Sites] {#sites-6550}

* Experience Manager Sites biedt een optie voor het publiceren of ongedaan maken van de publicatie van een pagina vanuit de alias. De optie werkt niet (NPR-33415).
* Wanneer een lay-outcontainer wordt verwijderd uit een sjabloon met meerdere sjablonen, wordt de sjabloon niet correct weergegeven (NPR-33347).
* Wanneer een Experience Manager Sites-pagina deel uitmaakt van een grote inhoudsset met meerdere live-kopieën, kan de voorvertoning van de paginaversiegeschiedenis niet worden geladen (NPR-33311).
* Wanneer u de opdracht Verplaatsen gebruikt om de naam van een Experience Manager Sites-pagina te wijzigen, wordt de paginatitel niet bijgewerkt (NPR-33264).
* Wanneer u pagina&#39;s door de kolommening beweegt, verdwijnen de kolommen (NPR-33216).
* Wanneer de naam van een lokale component in een taalkopie identiek is aan de naam van een component in de blauwdruk en de component wordt opgerold uit blauwdruk, wordt de term `_msm_moved` wordt niet toegevoegd aan de naam van het lokale onderdeel (NPR-33208).
* De service Paginaomleiding voegt .html toe aan een Experience Manager Sites-URL waar ResourceType niet is `cq:Page` (NPR-33176).
* Wanneer u een substructuur plakt, is er geen optie om te bepalen of corresponderende subpagina&#39;s moeten worden geplakt (NPR-33149).
* Het aantal resultaten in levend gebruik van een component is beperkt tot nummer 49 (NPR-33058).
* Wanneer u een inhoudsfragment baseert op een schema en het een verplicht tekstgebied of een weggebied bevat, kan het inhoudsfragment niet opslaan (NPR-33007).
* Wanneer u een aangepaste component maakt met de standaardcomponent Experience Fragment en deze gebruikt in Experience Manager Sites-pagina&#39;s, geeft Experience Manager geen referenties (gebruik) weer voor de aangepaste component (NPR-32852).
* Wanneer u de naam van een map wijzigt met een groot aantal verwijzingen, worden veel verwijzingen naar de map niet bijgewerkt (NPR-32765).
* Wanneer u de optie voor bronbewerking inschakelt, wordt deze beschikbaar voor inlineopties voor volledig scherm, maar blijft deze beschikbaar voor opties voor het bewerken van het dialoogvenster en het volledige scherm van de RTF-editor (NPR-32763).
* Als u een veld met meerdere velden hebt en een vereist veld (zoals een vervolgkeuzelijst of een padveld) in de pagina-eigenschappen van een blauwdruk bevat, worden de pagina-eigenschappen van de live kopie niet opgeslagen (NPR-32751) wanneer een pagina die een dergelijk veld bevat, wordt opgerold.
* Schermlezers kunnen niet door de kopstructuur van een pagina navigeren. Bovendien heeft het tabblad Componenten het verkeerde label (NPR-32648).
* Wanneer de paginering begint, laadt de Plukker van de Fragmenten van de Ervaring niet alle punten (NPR-32605).
* Auteurmachtigingen voor het lezen, wijzigen, maken en verwijderen van live kopieën worden ingetrokken. Elke auteur moest lees- en wijzigingstoestemmingen uitdrukkelijk verstrekken om pagina&#39;s binnen een Blauwdruk (NPR-32550) te bewegen.
* Inhoudsauteurs kunnen de functie Starten niet maken voor een pagina die is geïntegreerd met Adobe Analytics (NPR-32548).
* Wanneer een gebruiker de overerving met synchronisatie hervat, synchroniseert de live kopie van de bovenliggende pagina niet met de blauwdruk en geeft deze een onjuiste status weer (NPR-32500).
* Het laden van de Experience Manager Sites-editorpagina duurt meer dan 15 seconden (NPR-32413).
* In bepaalde velden wordt de optie Overerving annuleren niet weergegeven (NPR-32362).
* Wanneer u een pad selecteert voor een ervaringsfragmentcomponent en het selectievakje Dialoogvenster Selectie openen inschakelt, wordt niet naar het geselecteerde pad genavigeerd in de padbrowser (NPR-32308).
* Wanneer u van Experience Manager 6.2 aan Experience Manager 6.5 bevordert, toont de component Parsys van statische malplaatjes niet correct. De hoogte van de component Parsys wordt geplaatst aan 0 en de componenten binnen het zijn niet zichtbaar (NPR-33663).
* Wanneer een gebruiker een Layout Container op dezelfde pagina kopieert en plakt, worden componenten in een Layout Container niet weergegeven (NPR-33648).
* Weergave statuscontrole `Invalid cookie header` waarschuwingsbericht in de logbestanden (NPR-33629).
* Gereflecteerde XSS in PreferencesServlet (NPR-33438).
* Anonieme gebruikers hebben toegang tot CRXDE Lite-functies (GRANITE-27790).

### [!DNL Assets] {#assets-6550}

>[!IMPORTANT]
>
>Windows-gebruikers van [!DNL Experience Manager desktop app] wordt aangeraden om te upgraden naar [bureaubladtoepassing versie 2.0.3.2](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/release-notes.html#what-is-new) toegang te krijgen tot de DAM-gegevensopslagruimte op [!DNL Adobe Experience Manager 6.5.5.0] -instantie. Omdat ze problemen kunnen ondervinden bij het openen van de DAM-opslagplaats op [!DNL Adobe Experience Manager] 6.5.5.0-exemplaar met de bureaubladtoepassing versie 2.0.2.

**Toegankelijkheidsverbeteringen in Experience Manager Assets**

* Het is nu mogelijk om toetsenbordfocus te plaatsen op [!UICONTROL Comments] lijst en klikbare optie aan [!UICONTROL Create] versieopmerkingen onder [!UICONTROL Create new version] in [!UICONTROL Timeline] panel van activa (NPR-33424).

* Het is nu mogelijk [!UICONTROL View Settings] optie voor elementen en instellingen wijzigen in [!UICONTROL View Settings] dialoog met behulp van toetsenbordtoetsen (NPR-33420).

* De keuzelijst met keuzelijsten met invoervak (in verschillende velden op verschillende pagina&#39;s) bevat nu items als een lijst met opties die door schermlezers kunnen worden aangekondigd (NPR-33516).

* De sorteerfunctionaliteit van sorteerbare koppen (in de lijstweergave) [!UICONTROL Timeline] en [!UICONTROL Manage Publication] pagina) worden nu door schermlezers aangekondigd en de sorteerbesturingselementen op kolomkoppen zijn toegankelijk via het toetsenbord (NPR-32979).

* De klikbare elementen zoals commentaarkaarten, versie-updates, combodozen, en chevron pictogrammen van menu&#39;s kunnen nu worden geconcentreerd op en met het gebruiken van een toetsenbord (NPR-33514) in wisselwerking staan.

* Functionaliteit (of doel van de handeling) van inzichtspictogrammen (voor gebruik, indrukken en klikken) op [!UICONTROL Insights View] correct worden aangekondigd door schermlezers (NPR-33513).

* Alleen-lezen formuliervelden (bijvoorbeeld uitgeschakelde velden op [!UICONTROL Basic tab] van activa [!UICONTROL Properties]) kunt u nu focussen met het toetsenbord (NPR-33493, CQ-4273031).

* Labels in verschillende invoervelden zijn nu permanente labels (dus toegankelijk) en niet alleen plaatsaanduidingslabels, die zijn verdwenen bij het invoeren van tekst (NPR-33475).

* Verschillende kopniveaus (zoals paginatitels en sectiekoppen) worden nu gezien als koppen met verschillende niveaus voor schermlezers (NPR-33471).

* Interactieve elementen in de gebruikersinterface, zoals koppelingen en opties (op koptekst- en zoomopties van de elementenpagina, mapnavigatie), zijn nu toegankelijk via een toetsenbord (NPR-33468, CQ-4271412).

* De [!UICONTROL Options], [!UICONTROL Scope], en [!UICONTROL Workflows] voortgangsindicatoren voor [!UICONTROL Manage Publication] De pagina wordt nu correct door schermlezers gelezen als voortgangsindicatoren in plaats van tabbladen (NPR-33416).

* De kleur van sterrenclassificatiepictogrammen (zoals in [!UICONTROL Rating] deel van [!UICONTROL Advanced] tab in element [!UICONTROL Properties] of in de kaartweergave) wordt gewijzigd om het juiste contrast zichtbaar te maken voor gebruikers met een beperkt gezichtsvermogen en zonder kleurperceptie (NPR-33414).

* Chevron up pijl naast [!UICONTROL Comment] veld op de pagina met informatie over elementen kan nu worden geopend met behulp van toetsenbordtoetsen (NPR-33397).

* De uitgevouwen en samengevouwen staten van [!UICONTROL Tags] dialoogvenster over element [!UICONTROL Properties] en de linkse spoornavigatie (op de gebruikersinterface voor bedrijfsmiddelen) worden nu correct aangekondigd door schermlezers (NPR-33396).

* Titels van alle bladerpagina&#39;s op [!DNL Adobe Experience Manager] Activa zijn nu uniek (NPR-33343).

* Bij het navigeren door boomstructuur worden verschillende elementen van het besturingselement voor de structuurweergave nu correct aangekondigd door schermlezers (NPR-33304).

* Verschillende versies van elementen in [!UICONTROL Timeline] De pagina met informatie over elementen is nu toegankelijk via toetsenbordtoetsen (NPR-33283).

* Namen van zoeksuggesties die worden weergegeven in de keuzelijst Omnzoekopdracht worden nu door schermlezers aangekondigd wanneer ze de zoekfunctie gebruiken (NPR-33280).

* Klikbare elementen en [!UICONTROL Go to link] in [!UICONTROL References rail] worden nu door schermlezers aangekondigd als klikbare elementen (NPR-33278).

* Tabelstructuurgegevens (zoals rij 1, cel 1, tabel) van [!UICONTROL Share Link] wanneer het dialoogvenster wordt geopend (NPR-33268).

* Het doel van verschillende keuzelijstelementen (zoals het veld Pad en de optie om het dialoogvenster Selectie te openen op het tabblad Standaard van Eigenschappen van element) worden nu correct aangekondigd door schermlezers (NPR-33235).

* De informatie dat de rijen in de lijst van de lijstmening selecteerbaar zijn wordt nu meegedeeld aan de gebruikers van de schermlezer wanneer toetsenbordnadruk op hen is. Wanneer een aanwijzer op de rijen wordt geplaatst, geven de schermlezers de informatie aan (NPR-33234).

* Opties (met [!UICONTROL x]) om alle geselecteerde tags onder de [!UICONTROL Tags] veld in [!UICONTROL Basic] tabblad van [!UICONTROL Properties] zijn nu toegankelijk voor schermlezers (NPR-33206).

* Datumkiezer voor kalenderdatums kan nu worden geactiveerd en geactiveerd met het toetsenbord van schermlezers en gebruikers van waargenomen toetsenborden (NPR-33200).

* Als u schakelt tussen de lijstweergave en de kaartweergave, wordt de functionaliteit (van het aanpassen van weergaven) nu correct weergegeven voor schermlezers (NPR-33069).

* Het menu in de linkerrail is nu toegankelijk. Functionaliteit en doel van het uitbreiden van het menu worden door schermlezers op de juiste wijze aangekondigd (NPR-33068).

* De keuzelijst en veel andere gebruikersinterface-elementen zijn nu toegankelijk voor gebruikers met een niet-visuele schermlezer. De volgende informatie hierover wordt door schermlezers aangekondigd (NPR-33040):

   * of gebruikersinvoer op een element is vereist voordat het formulier wordt verzonden.
   * of een element niet bewerkbaar is.
   * of een widget is geselecteerd of niet.

* De optie om filterzijbalk te openen kan nu met het toetsenbord worden geopend (NPR-32842, CQ-4273018).

* Het besturingselement voor selectievakjes in de kolomkop van de lijstweergave is nu toegankelijk en het doel van het gebruik van het besturingselement wordt door schermlezers aangekondigd (NPR-32722, NPR-33005).

* Labels voor uren (HH) en minuten (mm) velden in de datumkiezer voor de kalenderdatum zijn nu permanente labels in plaats van plaatsaanduidingslabels en verdwijnen niet wanneer de gebruiker tekst in deze velden invoert (NPR-32720).

* De koppelingstekst van berichten (die wordt weergegeven nadat op het belpictogram is geklikt) wordt nu aangekondigd voor gebruikers van schermlezers die met Tab toegang krijgen tot elke koppeling (NPR-32645).

* [!UICONTROL Select], [!UICONTROL Download], [!UICONTROL Properties], en [!UICONTROL More Actions] opties op assetkaarten in [!UICONTROL Insights View] zijn nu toegankelijk via het toetsenbord (NPR-32609).

* Visueel verborgen inhoud (zoals de inhoud van de menubalk van de header op zoekresultaten) wordt niet meer aangekondigd door schermlezers wanneer deze toegang krijgen met het toetsenbord (NPR-32606).

* Het doel van de etiketten op besturingselementen om naar volgende en vorige maanden in een kalenderdatumkiezer te gaan, worden nu door schermlezers bekendgemaakt (NPR-32604).

* Sterrenclassificatiepictogrammen zijn nu brandbaar en kunnen worden geactiveerd met behulp van toetsenbordtoetsen (NPR-32513).

* Functionaliteit voor het regelen van het videovolume is nu toegankelijk via de Tab-toets (om de volumeschuifregelaar te activeren) en de pijltoetsen (om het volume aan te passen) op het toetsenbord (NPR-32065).

* Het doel van de ondergrens ([!UICONTROL From]) en bovengrens ([!UICONTROL To]) invoervelden van het filter Bestandsgrootte worden nu aangekondigd voor gebruikers van een niet-zichtbare schermlezer (NPR-32064).

* De [!UICONTROL Languages] menu in [!UICONTROL Create and Translate] Het formulier is nu toegankelijk voor schermlezers in de bladermodus (CQ-4293906).

* De [!UICONTROL References] Het paneel is nu toegankelijk met de volgende verbeteringen (NPR-33261, CQ-4293798):

   * In de modus Bladeren wordt de focus van schermlezers niet meer verplaatst naar verborgen bewerkingsvelden met meerdere regels onder [!UICONTROL Site References], [!UICONTROL Asset References], [!UICONTROL Copies], en [!UICONTROL Form References] secties.

   * Schermlezers kondigen nu de rol aan van [!UICONTROL Site References] en [!UICONTROL Language Copies] elementen.

   * De focus van schermlezers in de modus Bladeren verschuift in een betekenisvolle volgorde naar verschillende elementen.

* [!UICONTROL Metadata Schema Editor] De pagina en de elementen ervan zijn nu toegankelijk met het toetsenbord en zijn gebruiksvriendelijk voor schermlezers (CQ-4290962, CQ-4272953).

* Het doel van `X` Het symbool voor het verwijderen van de geselecteerde tags wordt nu door schermlezers aangekondigd samen met het aantal geselecteerde tags (CQ-4273017).

* Om verwarring te voorkomen voor niet-zichtbare gebruikers die een schermlezer gebruiken, worden decoratieve pictogrammen en afbeeldingen nu genegeerd door schermlezers (CQ-4272944).

**In Experience Manager Assets opgeloste problemen**

[!DNL Adobe Experience Manager] 6.5.5.0 Middelen bieden oplossingen voor de volgende problemen:

* [!UICONTROL Start] optie aan [!UICONTROL Create Workflow] dialoog voor activa in een inzameling wordt onbruikbaar gemaakt, daardoor verhinderend werkschema om worden teweeggebracht (NPR-32471).

* Als u CSS-opnamen gebruikt in metagegevensschema&#39;s en een vervolgkeuzelijst selecteert en opslaat met een apostrof (uit de vervolgkeuzelijst met onderliggende elementen), verdwijnt de geselecteerde optie apostrof na het opnieuw openen van het element [!UICONTROL Properties] (NPR-32649).

* [!UICONTROL Assets Insights Sync Job] stopt en mislukt als er ongeldige items worden aangetroffen (aan de zijde Analytics) in plaats van naar de volgende vermelding te gaan (NPR-32674).

* Gyroscoop werkt niet omdat bewegingssensoren standaard zijn uitgeschakeld in mobiele browsers in panoramische viewer (CQ-4272937).

* [!UICONTROL Connected Assets Configuration] De wizard werkt niet met een fout van 404 bij de installatie van versie 6.5.3 op 6.5.1 (NPR-32730).

* Tijdens het XMP terugschrijven proces, veranderen alle eigenschappen van de meta-gegevens van douanenamespace de prefix van douanespaconruimte in ns2 in tegenstelling tot het namespaceprefix die wordt gevormd (NPR-32748).

* Lazy loading wordt niet geactiveerd en er worden slechts 100 assets weergegeven bij het selecteren om de taken te bekijken vanuit de berichten in het Postvak IN (NPR-32750).

* `NullPointerException` wordt waargenomen omdat voorkeuren voor ontbrekende knooppunten ontbreken in het nieuwe gebruikersprofiel (SAML/SSO). Deze fout voorkomt dat nieuwe aangemelde gebruikers gebruiken [!DNL Adobe Experience Manager Stock] integratie (NPR-32777).

* Traversale waarschuwingen worden waargenomen in logboeken bij het openen van een slimme verzameling die meer dan 10.000 activa bevat (NPR-32980).

* Elementnamen worden gewijzigd in kleine letters wanneer middelen van de ene map naar de andere worden verplaatst [!DNL Adobe Experience Manager] werken op de Dynamic Media Scene7-runmode (NPR-32995).

* Een doorzocht middel kan niet worden geschrapt nadat aan zijn eigenschappen van de onderzoeksresultaten navigeert en dan naar onderzoeksresultaten teruggaat om het te schrappen (NPR-32998).

* [!UICONTROL Next] optie blijft uitgeschakeld als u een doelmap selecteert in [!UICONTROL Move Assets] interface (NPR-33356).

* [!UICONTROL Next] Deze optie is niet ingeschakeld bij het selecteren van het bovenliggende knooppunt (waar één onderliggende map zichtbaar is) en het selecteren van de onderliggende map (NPR-33275).

* De controle binnen en de controle uit toestemmingen worden onbruikbaar gemaakt op de Verbinding van Activa van Adobe (AAL) voor gebruikers met schrappingstoestemming, zelfs als andere toestemmingen zoals lezen, creëren, of wijzigen worden verleend (NPR-33272).

* Smart Crop-uitvoeringen zijn niet beschikbaar in het dialoogvenster voor het downloaden van bestanden (NPR-33167).

* Uitzondering wordt waargenomen in logboeken bij het openen van renditions rail voor een PDF onder een map met profiel van smart crop (CQ-4294201).

* Voorinstellingen afbeelding publiceren niet, als [!UICONTROL Dynamic Media sync mode] is standaard uitgeschakeld op Experience Manager met Dynamic Media Scene7-runmode (CQ-4294200).

* De verwerking van bedrijfsmiddelen tijdens bulkupload blijft vastzitten en de werkstroominstantie toont vastgelopen instanties van update DAM-middelen (CQ-4293916).

* Het creëren van een configuratie van Dynamic Media op Experience Manager werkt, maar op het gebruikersinterface gebeurt niets bij het selecteren van sparen (CQ-4292442).

* Voorvertoning van F4V-video-elementen werkt niet in progressief afspelen op Safari/Mac (CQ-4289844).

* Er wordt een extra map gemaakt bij het slim uitsnijden van middelen die zich in een bovenliggende map met punt bevinden `.` in zijn naam (CQ-4289337).

* De miniatuur wordt verbroken en de videoverwerkingsbanner wordt niet weergegeven wanneer een video wordt gekopieerd (CQ-4284125).

* In de DIG-viewer worden in Firefox voor sommige modellen met lege cameraweergaven ten onrechte lege miniaturen weergegeven (CQ-4283447).

* De prestatieproblemen die zijn vastgelegd in 6.5.5.0 zijn (CQ-4279206):

   * Het uploaden van grote binaire bestanden naar Dynamic Media Image Processing-servers duurt te lang.

   * De tijd van de miniatuurgeneratie bij Experience Manager neemt toe vanwege de Dynamic Media Scene7-architectuur.

* Dynamic Media Scene7-migratiekwesties mislukken voor klanten met een groot aantal middelen (CQ-4279206).

* Layout van video 360-viewer wordt verbroken als `setVideo` wordt gebruikt, en de videoverschuivingen neer op het gebruiken `video= modifier` (CQ-4263/2001).

* Er wordt een foutbericht weergegeven tijdens de installatie van het SDL-pakket van de Experience Manager (NPR-33175).

* SSRF-kwetsbaarheid in Experience Manager (NPR-33435).

### Platform {#platform-6550}

* De [!DNL Sling] wordt niet aangeroepen als de `sling:match` kaartitem wordt gemaakt onder `/etc/maps` (NPR-33362).
* Experience Manager loopt vast als gevolg van segmentatiefout met [!DNL Apache Lucene] (NPR-32988).
* [!DNL Jackson] kernpakket ontbreekt in het Experience Manager uberjar-bestand (NPR-32848).
* CRXDE Lite laadt geen inhoud voor gebruikers zonder leesmachtigingen op het tabblad `jcr:primaryType` eigenschap voor een knooppunt (NPR-32611).
* [!DNL Granite] De planner van de onderhoudstaak herinitialiseert te vaak tijdens de plaatsingen van de Experience Manager (CQ-4294627).
* Wanneer een SQL-query lang wordt uitgevoerd, bijvoorbeeld 7 uur, stopt de Experience Manager met reageren (NPR-33044).

### Gebruikersinterface {#ui-6550}

* Selectie van keuzerondjes blijft niet behouden in een multiveld (NPR-33309).
* Lazy loading limit werkt niet voor de lijstweergave (NPR-33124).
* De resultatenpagina van het onderzoek toont geen bericht als er geen gelijken (NPR-32974) zijn.
* Het filter van het onderzoek keert alle gelijken onder terug `/content` knooppunt dat de geselecteerde locatie negeert (NPR-32849).

### Integraties {#integrations-6550}

* De interne cache wordt gewist wanneer een pagina met een Adobe Target-component wordt gepubliceerd (NPR-33162).
* Integratie met Adobe Target werkt niet aan [!DNL Windows Internet Explorer] 11 (NPR-33111).
* Wanneer u Adobe Target configureert, wordt [!UICONTROL Company] en [!UICONTROL Report Suite] velden worden niet weergegeven bij het selecteren van een bron voor rapportage (NPR-32502).
* Bij exporteren [!DNL Experience Fragments] gebruiken [!DNL Adobe I/O], worden metagegevens zoals het bronproduct niet geëxporteerd naar Adobe Target (NPR-32159).
* Erkende IMS-gebruikers in de lokale beheergroep van Experience Managers kunnen geen IMS-configuraties maken of wijzigen (NPR-33045).
* Op de pagina Startconfiguraties van Adobe worden niet alle records weergegeven (NPR-33011).
* Gebruikers in een groep van inhoudsauteurs kunnen vanwege een JavaScript-fout de eigenschappen van een Adobe Target-component niet bewerken (NPR-32996).
* Xxx-site scripting voor JSON (NPR-32744).

### Omzettingsprojecten {#translation-6550}

* Vertaalde tags worden niet geïmporteerd in de Experience Manager van vertaalservices van derden (NPR-33154).
* Op de pagina voor vertaalconfiguratie wordt een onjuiste vertaalprovider weergegeven dan de provider die wordt gebruikt voor de vertaling (NPR-32971).
* Als u een ervaringsfragmentmap toevoegt aan een bestaand vertaalproject, wordt een nieuw project gemaakt (NPR-32843).
* A `NullPointerException` Er is een fout opgetreden in de logboeken met een vertaaltaak (NPR-32628).

### WCM {#wcm-6550}

* Pagina-editor - De [!DNL Sites] In de Pagina-editor kunnen gebruikers met alleen het toetsenbord niet naar de hoofdinhoud gaan in plaats van de tabfocus door alle opties in de header te verplaatsen (CQ-4293883).
* Pagina-editor - Deelvensters die de component Well gebruiken en opgeslagen gegevens bevatten, worden niet weergegeven vanwege updates in [!DNL Chrome] en [!DNL Firefox] versies (CQ-4292/95).
* MSM - Als u een component van de pagina verwijdert, wordt de component niet verwijderd uit de gepubliceerde versie van de pagina (CQ-4292360).

### [!DNL Brand Portal] {#assets-brand-portal-6550}

* Een gepubliceerd metagegevensschema verwijderen uit [!DNL Brand Portal] resulteert in een fout (CQ-429/20063).
* Als een beheerder configureert [!DNL Experience Manager Assets] 6.5.4 met Brand Portal via Adobe Developer Console, de [!DNL Brand Portal] gebruiker kan de middelen van een bijdragemap niet publiceren vanuit [!DNL Brand Portal] tot [!DNL Experience Manager] (NPR-33046).
* Dubbele replicatie van de bovenliggende mappen die conflicten veroorzaken (NPR-33001).

### [!DNL Communities] {#communities-6550}

* Kan een kaart in moderatieconsole niet verwijderen met de snelmenuoptie (NPR-33117).
* Er treedt een fout op bij de toegang tot de [!UICONTROL Activity Stream] bladzijde (NPR-33146).
* Groepen die op een instantie van de auteur worden verwijderd, worden niet uit alle publicatie-instanties verwijderd (NPR-33199).
* Auteurs worden na het maken van een nieuwe groep niet doorgestuurd naar de [!UICONTROL Community Group] sectie over [!DNL Internet Explorer] 11 (NPR-33205).
* De toegang tot van een bericht in Experience Manager Inbox verandert niet de status van het bericht aan Gelezen (NPR-32764).
* Een [!DNL Communities] Als u de miniatuurafbeelding van een groep wijzigt en deze wijzigt, wordt de groepminiatuurafbeelding niet bijgewerkt (NPR-32599).
* Een gebruiker kan geen e-mail naar een andere gebruiker in een gemeenschap (NPR-32598) verzenden.
* Een verzonden blog wordt pas weergegeven wanneer de gebruiker de pagina vernieuwt (NPR-32391).
* Tijdens het maken van een versie van meldingen en abonnementen op door gebruikers gegenereerde inhoud (UGC) wordt een onjuiste id van de bronpagina opgeslagen (CQ-4279355, CQ-4289703).
* Probleem met scripts die verwijzen naar andere sites (NPR-33203).

### Workflow {#workflow-6550}

* De [!UICONTROL Timeline] in de linkerspoorstaaf meer tijd nodig heeft om te laden dan verwacht (NPR-32851).
* Nadat u een Experience Manager-instantie opnieuw hebt gestart, bevat de e-mail voor de overzichtstaak voor een verzameling een onjuiste payload-koppeling (NPR-32774).

### [!DNL Forms] {#forms-6550}

>[!NOTE]
>
>Experience Manager Service Pack bevat geen oplossingen voor [!DNL Forms]. Ze worden geleverd met een apart Forms-add-onpakket. Daarnaast wordt een cumulatief installatieprogramma uitgebracht dat oplossingen voor AEM Forms op JEE bevat. Zie voor meer informatie [Experience Manager Forms-invoegtoepassing installeren](/help/release-notes/sp-release-notes.md#install-aem-forms-add-on-package) en [Experience Manager Forms installeren op JEE](/help/release-notes/sp-release-notes.md#install-aem-forms-jee-installer).

* Correspondentenbeheer: De volgorde van de activa in een doelgebied verandert na indiening van een brief (NPR-33359, NPR-33153).
* Adaptieve Forms: Wanneer een gebruiker een adaptief formulier bewerkt, [!UICONTROL Start Workflow] beschikbaar in het dialoogvenster [!UICONTROL Page Information] werkt niet (NPR-33004).
* Adaptieve Forms: De gebruiker kan geen adaptief formulier opslaan met meer dan één bijlage (NPR-32997).
* Adaptieve Forms: Als u de indeling van het deelvenster wijzigt in een adaptief formulier, treedt er een fout op (CQ-4293880).
* Adaptieve Forms: Een nieuwe regel aan een tekenreeks in een woordenboek voor adaptieve formulieren wordt toegevoegd `&#xa;` tekens naar het woordenboek (NPR-33266).
* Adaptieve toegankelijkheid voor Forms: Wanneer een gebruiker een adaptief formulier weergeeft als een HTML-formulier, wordt de [!UICONTROL Scribble Signature] veld kan tabfocus niet behouden (NPR-33159).
* Adaptieve toegankelijkheid voor Forms: De foutberichten die worden weergegeven bij het verzenden van een adaptief formulier, zijn niet gekoppeld aan een `aria-describedBy` kenmerk (NPR-33071).
* Adaptieve toegankelijkheid voor Forms: Velden die verplicht zijn gemarkeerd in een adaptief formulier, hebben niet het verplichte kenmerk ingesteld op Waar in het ARIA-toegankelijkheidsschema (NPR-33070).
* PDFG-service: Wanneer een gebruiker een tekstbestand in een PDF omzet, worden Japanse tekens niet correct weergegeven (NPR-33238).
* PDFG-service: `CreatePDF` de bewerking kan een PDF-bestand niet omzetten in de OCR-indeling PDF (NPR-32994).
* PDFG-service: PDF-conversie mislukt voor de 200e instantie van een [!DNL OpenOffice] document (NPR-32766).
* BackendIntegration: De verzoeken van het het gegevensmodel van de vorm ontbreken aangezien verfrist teken wegens onjuiste inactieve staat (NPR-33169) verloopt.
* Designer: Schermlezers voeren de tabvolgorde uit op basis van de standaard geografische volgorde in plaats van de aangepaste tabvolgorde die is gedefinieerd in het XDP-bestand (NPR-32160).
* Designer: Als de optie Tags toevoegen is ingeschakeld, verdwijnt de rand van het subformulier in de gegenereerde PDF-uitvoer (NPR-32778).
* Opgeslagen XSS met GuideSOMProviderServlet (NPR-32700).

## Adobe Experience Manager 6.5.4.0 {#experience-manager-6540}

Adobe Experience Manager 6.5.4.0 is een belangrijke update die nieuwe functies bevat, belangrijke verbeteringen en prestaties die door de klant zijn aangevraagd, stabiliteit en verbeteringen op het gebied van beveiliging, die zijn uitgebracht sinds de algemene beschikbaarheid van de 6.5-release in **April 2019**. Deze kan boven op Adobe Experience Manager 6.5 worden geïnstalleerd.

Enkele belangrijke functies en verbeteringen die zijn geïntroduceerd in Adobe Experience Manager 6.5.4.0 zijn:

* Adobe Experience Manager Assets is nu geconfigureerd met Brand Portal via [!DNL Adobe I/O] Console.

* Een nieuwe [Afdrukbare uitvoer genereren](../forms/using/aem-forms-workflow-step-reference.md) Deze stap is nu beschikbaar voor Adobe Experience Manager Forms-workflows.

* [Ondersteuning voor meerdere kolommen](../forms/using/resize-using-layout-mode.md) voor lay-outmodus voor adaptieve formulieren en interactieve communicatie.

* Ondersteuning voor [RTF](../forms/using/designing-form-template.md) in HTML5-vorm.

* [Verbeteringen voor toegankelijkheid](new-features-latest-service-pack.md#accessibility-enhancements) in Experience Manager Assets.

* De ingebouwde opslagplaats (Apache Jackrabbit Oak) wordt bijgewerkt naar versie 1.10.8.

* U kunt selectieve inhoudsubstructuren nu synchroniseren met *Dynamic Media - Scene7-modus* in plaats van alle beschikbare `content/dam`.

* Integratie van formuliergegevensmodellen met SOAP-webservice ondersteunt nu keuzegroepen of kenmerken voor elementen.

* De invoer of de output van de ZEEP en complexe gegevensstructuren steunen nu Dynamische Vervanging van de Groep.

Voor een volledige lijst van eigenschappen en belangrijkste hoogtepunten die in de recentste Pakken van de Dienst worden geïntroduceerd, zie [Nieuw in Adobe Experience Manager 6.5 Service Packs](new-features-latest-service-pack.md).

### Sites {#sites-fixes}

* Wanneer een URL van een Adobe Experience Manager Sites-pagina een dubbele punt bevat (`:`) of percentagesymbool (`%`), stopt de browser met reageren en CPU-gebruikspikes (NPR-32369, NPR-31918).

* Wanneer een Experience Manager Sites-pagina wordt geopend voor bewerking en een component wordt gekopieerd, blijft de plakhandeling niet beschikbaar voor sommige plaatsaanduidingen (NPR-32317).

* Wanneer de wizard Publicatie beheren wordt geopend, wordt een ervaringsfragment dat is gekoppeld aan een kerncomponent niet weergegeven in de lijsten met gepubliceerde referenties (NPR-32233).

* Het overzicht van live kopieën in Touch UI duurt veel langer dan de klassieke interface die wordt weergegeven (NPR-32149).

* Wanneer de server-tijd en machine-tijd in verschillende tijdzones zijn, toont de geplande publicatietijd servertijd in Touch UI, terwijl in Klassieke UI, machinetijd wordt getoond (NPR-32077).

* Experience Manager Sites kan geen pagina openen met een achtervoegsel in de URL (NPR-32072).

* Wanneer een gebruiker een inhoudsfragment bewerkt, wordt een verwijderde variant van het inhoudsfragment hersteld (NPR-32062).

* Gebruikers mogen een inhoudsfragment opslaan zonder informatie op te geven in de vereiste velden (NPR-31988).

* kernel.js en ui.js worden niet vooraf in acht genomen of in cache geplaatst. Het leidt tot extra tijd bij het teruggeven van pagina&#39;s (NPR-31891).

* Wanneer PageEventAuditListener wordt toegelaten, breidt de lengte van toe verbindt rij. Het beïnvloedt de prestaties van vele verrichtingen zoals bulkpublicaties, navigatie, bulkactivabeweging (NPR-31890).

* Wanneer de Fragmenten van de Ervaring worden gesleept, wordt de hoge reactietijd waargenomen (NPR-31878).

* Wanneer u de component van de Belemmering hier optie in ontvankelijke placeholder van het net selecteert, wordt een verzoek van de GET verzonden en het verzoek resulteert in fout HTTP 403 (NPR-31845).

* Wanneer u de inhoud binnen dezelfde map verplaatst, is de optie Pagina verplaatsen uitgeschakeld (NPR-31840).

* In de bewerkbare sjabloonstructuurmodus worden in de lijst met toegestane componenten in de lay-outcontainer onjuiste resultaten weergegeven. Alleen componenten met een dialoogvenster voor ontwerpen worden weergegeven in de lay-outcontainer (NPR-31816).

* Wanneer een pagina alleen-lezen toestemmingen voor een gebruiker heeft, is de Open eigenschappen optie zichtbaar in sites.html maar niet in editor.html (NPR-31770).

* Wanneer een gebruiker op de knop Maken klikt, is de pagina-optie niet beschikbaar (NPR-31756).

* Kan de campagne niet synchroniseren in Adobe-campagne met OOTB (Out of the box)-ontwerpimportcomponent (NPR-31728).

* Wanneer u een lijst met opsommingstekens probeert te wijzigen in een genummerde lijst, worden alleen de eerste twee items van de lijst gewijzigd (NPR-31636).

* Wanneer een pagina niet-geschreven is en het onderliggende knooppunt is geselecteerd, wordt in het dialoogvenster Selecteren nog steeds het eerste knooppunt weergegeven. Wanneer de pagina is geschreven en de gebruiker doorbladert, richt de pagina zich aan de wortelknoop in plaats van de authored knoop (NPR-31618).

* Het dialoogvenster Weergaveconfiguratie werkt niet correct voor de workflowfunctie voor het aanpassen van postvakken (NPR-32503 en NPR-32492).

* Er wordt een foutbericht weergegeven tijdens het weergeven van workflowinformatie met Inbox (CQ-4282168).

### Assets {#assets-6540-enhancements}

* De knop waarmee de workflow voor het verzamelen van elementen wordt geactiveerd, is uitgeschakeld (NPR-32471).

* Een map zonder naam wordt gemaakt in SPS (Scene7 Publishing System) en een element van de ene map naar de andere verplaatst in Experience Manager met de Dynamic Media Scene7-configuratie (NPR-32440).

* De handeling voor het verplaatsen van alle elementen (met de opdracht Alles selecteren en vervolgens verplaatsen) naar een map met gepubliceerde elementen mislukt bij fout (NPR-32366).

* Het genereren van uitvoeringen voor elementen met ${extension} mislukt (NPR-32294).

* URL&#39;s met versiegeschiedenis worden weergegeven onder Veld Verwijzing naar op de eigenschappenpagina voor elementen (NPR-31889).

* ZIP-bestand dat is gedownload van DAM, kan niet worden geopend met WinZip (NPR-32293).

* Oorspronkelijke machtigingen van een map worden bijgewerkt wanneer Mapinstellingen worden geopend om de maptitel of miniatuurafbeelding te wijzigen en vervolgens worden opgeslagen (NPR-32292).

* Het kalenderpictogram voor activering dat is gepland, wordt niet weergegeven in de kolom Status (in de klassieke gebruikersinterface van de DAM-lijst met activa) voor elementen waarvan de activering voor een latere datum en tijd is gepland (NPR-32291).

* Het maken van fragmenten met behulp van fragmentsjablonen geeft een fout op bij het zoeken naar verzamelingen tijdens het maken van fragmenten (NPR-32290).

* Meerdere zoekquery&#39;s worden geactiveerd wanneer meerdere tags zijn geselecteerd met het zoekfilter (NPR-32143).

* De gebruikersinterface van Experience Manager Assets geeft afgekapte bestandsnamen weer wanneer elementen met meer dan 50 tekens in de bestandsnaam worden geüpload (NPR-32054).

* Alle selectievakjes in het deelvenster Filter worden gewist wanneer het eerste en het tweede selectievakje worden gewist, terwijl op niveau twee selectievakjes in de boomstructuur van het selectievakje in Adobe Stock zijn ingeschakeld (NPR-31919).

* Bestanden en mapzoekopdrachten met Omnissearch-facetten geven uitzondering (NPR-31872).

* Veldmarkering voor verplichte veldselectie in de metagegevenseditor wordt niet verwijderd, zelfs niet nadat het vereiste veld is geselecteerd, wanneer de afhankelijkheidsregels zijn ingesteld in het corresponderende metagegevensschema (NPR-31834).

* Volledige namen van bladniveautags (uit de taghiërarchie) worden niet weergegeven op de pagina Eigenschappen van element (NPR-31820).

* Het gebruik van de opdracht back van de pagina Eigenschappen van element op de Safari-browser geeft een fout (NPR-31753).

* De resultatenpagina Touch UI-zoekopdracht (uitgevoerd via Omnissearch) wordt automatisch naar boven geschoven en verliest de schuifpositie van de gebruiker (NPR-31307).

* Op de elementendetailpagina van PDF-elementen worden geen actieknoppen weergegeven, behalve naar de knoppen voor verzameling en uitvoering toevoegen in Experience Manager die in de Dynamic Media Scene7-uitvoeringsmodus worden uitgevoerd (CQ-4286705).

* Het duurt te lang om de batchupload van Scene7 te doorlopen (CQ-4286445).

* Met de knop Opslaan wordt de externe set niet geïmporteerd als de gebruiker geen wijzigingen heeft aangebracht in de Set Editor in de Dynamic Media Client (CQ-4285690).

* Miniatuur van 3D-elementen is niet informatief wanneer een ondersteund 3D-model in de Experience Manager wordt opgenomen (CQ-4283701).

* De onverwerkte status van de voorinstelling van de viewer voor SmartCrop wordt twee keer weergegeven op de bannertekst naast de naam van de voorinstelling (CQ-4283517).

* Onjuiste containerhoogte van een geüpload 3D-model, voorvertoond in 3D-viewer, wordt weergegeven op de detailpagina van het element (CQ-4283309).

* De Carousel Editor wordt niet geopend in IE 11 in de modus Dynamic Media Hybrid Experience Manager (CQ-4255590). **Voor Adobe Dynamic Media — Hybride modusklanten:** Na mei 2022 beëindigt Adobe de ondersteuning voor Internet Explorer 11 in Dynamic Media - hybride modus.

* De toetsenbordfocus blijft vastzitten in de vervolgkeuzelijst E-mail in het dialoogvenster Downloaden, in Chrome- en Safari-browsers (NPR-32067).

* Het selectievakje Alle inhoud synchroniseren is standaard niet ingeschakeld wanneer wordt geprobeerd om DM-cloud config op Experience Manager toe te voegen (CQ-4288533).

### Foundation-UI {#foundation-ui-6540}

* Bij het zoeken van elementen met het deelvenster Filter wordt de muiscontrole verplaatst naar het vorige filterveld in plaats van in het bestaande filterveld te blijven (NPR-32538).

* Tags voor Platforms: Als u naar tags zoekt door in de tagvelden te typen, worden codes buiten de hoofdgrenzen weergegeven en wordt de instelling `rootPath` eigenschap van tagvelden (NPR-31895).

* UI Platform: Browseronderbrekingen van het pad als een ongeldig pad wordt toegevoegd in het tekstveld (NPR-31884).

* Melding wordt verborgen achter een plakmenu op paginaselectie (NPR-31628).

### Platform {#platform-sling-6540}

* (HTL) Onderstrepingstekens vervangen dubbele punten in de padsectie van URL (NPR-32231).

### Projecten {#projects-6540}

* De knop Maken is niet zichtbaar voor de gebruiker, zelfs niet als de gebruiker toestemming heeft om een project te maken in de submap (NPR-31832).

### Projectomzetting {#projects-translation-6540}

* Het maken van een vertaalproject verbreekt de gebruikersinterface wanneer de optie Snijruimten activeren is `Apache Sling JSP Script Handler` (NPR-32154).

* Fout in UI en Null-puntuitzondering in foutenlogboeken wordt waargenomen wanneer om het even welke te vertalen markering aan een vertaalproject (NPR-31896) wordt toegevoegd.

### Integraties {#integrations-6540}

* URL-genereren van bibliotheek starten is alleen gebaseerd op `path` en `library_name` waarden uit de API voor starten en is niet gebaseerd op `library_path` waarde (NPR-31550).

* Er wordt een foutbericht weergegeven tijdens het verwerken van aan LiveFyre gerelateerde items (FYR-12420).

* ReportSuitesServlet is kwetsbaar voor SSRF (NPR-32156).

### WCM-sjablooneditor {#wcm-template-editor-6540}

* In de bewerkbare sjabloonstructuurmodus wordt de lijst met toegestane componenten in de lay-outcontainer niet weergegeven met de koppelingsknopcomponent (CQ-4282099).

### WCM Pagina-editor {#wcm-page-editor-6540}

* Er is een fout opgetreden bij het selecteren van een overlay en het selecteren van responsieve rastersleepcomponenten hier (CQ-4283342).

### Campagne gericht {#campaign-targeting-6540}

* De configuratie van de doelcloud mislukt als de fout get-boxes is mislukt (CQ-4279880).

### Brand Portal {#assets-brand-portal-6540}

* Brand Portal-gebruikers kunnen geen middelen van de map met Help-informatie publiceren naar [!DNL Assets] bij upgrade naar [!DNL Adobe I/O] op Experience Manager 6.5.4 (CQDOC-15655). Voor een onmiddellijke oplossing van Experience Manager 6.5.4 wordt aanbevolen [de hotfix downloaden](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/hotfix/cq-6.5.0-hotfix-33041) en installeer op de auteur-instantie.

* Pop-upwaarden van het metagegevensschema zijn niet zichtbaar in de elementeigenschappen (CQ-4283287).

* In het subschema Metagegevens worden geen tabbladen weergegeven op basis van MIME-typen in de eigenschappen van elementen (CQ-4283288).

* Als u het schema voor metagegevens niet publiceert, wordt een foutbericht weergegeven, maar wordt het schema op de achtergrond verwijderd.

* Voorvertoningsafbeelding wordt niet weergegeven voor een gepubliceerd element (CQ-4285886).

* De gebruiker kan activa publiceren of unpublish die enig citaat in de naam bevatten (CQ-4272686).

* De voorwaarden worden niet weergegeven tijdens het downloaden van meerdere middelen (CQ-4281224).

* Kleine beveiligingskwetsbaarheden verholpen.

### Gemeenschappen {#communities-6540}

* Het formulier Lid maken wordt weergegeven als een lege pagina (NPR-31997).

* De gebruiker kan het Analytics-rapport over de auteurinstantie (NPR-30913) niet bekijken.

### eikenindexering en vragen {#oak-indexing-6540}

* MS Word- en MS Excel-documenten met een JPEG-afbeelding kunnen niet worden geparseerd als de Tika-parser wordt geparseerd en er is een fout opgetreden bij het verwerken van de klasse Geen (NPR-31952).

### Forms {#forms-6540}

>[!NOTE]
>
>Experience Manager Service Pack bevat geen oplossingen voor Experience Manager Forms. Ze worden geleverd met een apart Forms-add-onpakket. Daarnaast wordt een cumulatief installatieprogramma uitgebracht dat oplossingen voor Adobe Experience Manager Forms op JEE bevat. Zie voor meer informatie [Experience Manager Forms-invoegtoepassing installeren](/help/release-notes/sp-release-notes.md#install-aem-forms-add-on-package) en [Experience Manager Forms installeren op JEE](/help/release-notes/sp-release-notes.md#install-aem-forms-jee-installer).

* Correspondentenbeheer: Letters geven extra tekens weer na verzending naar workflows voor postprocessen (NPR-32626).

* Correspondentenbeheer: Bij letters wordt een tijdelijke aanduiding voor een vervolgkeuzelijst weergegeven als een tekstonderdeel na verzending naar workflows na verwerking (NPR-32539).

* Correspondentenbeheer: De standaardwaarden die in de lettertypesjabloon worden gedefinieerd, worden niet weergegeven in de voorvertoningsmodus (NPR-32511).

* Mobiele Forms: De knop Verzenden wordt weergegeven als vergroot tijdens het renderen van een XDP-formulier in een HTML-versie (NPR-32514).

* Documentservices: Problemen met URL-toegang voor Letters en enkele andere pagina&#39;s na toepassing van Service Pack 2 (NPR-32508, NPR-32509).

* Documentservices: Als het aantal transacties op een server een specifieke limiet overschrijdt, mislukt de conversie van HTML naar PDF en worden de instellingen voor het bestandstype verwijderd uit [!DNL Forms] server (NPR-32204).

* Adaptieve Forms: Browser het hulpmiddel van de toegankelijkheid meldt mislukkingen in adaptieve vormen overeenkomstig de richtlijnen van niveau AA van WCAG2 (NPR-32312, NPR-32309, CQ-4285439).

* Adaptieve Forms: Het hulpmiddel van de de browser van Chrome rapporteert een beste praktijkmislukking (NPR-32310).

* Adaptieve Forms: Vertaalproblemen tijdens het configureren van een adaptief formulier dat is ingesloten in een Experience Manager Sites-pagina (NPR-32168).

* Workbench: Een foutenmelding toont terwijl het gebruiken van Get PDF Eigenschappen verrichting voor de dienst van Hulpmiddelen van de PDF (NPR-32150).

* Documentbeveiliging: Een beveiligd PDF-bestand kan niet offline worden geopend met de optie DisableGlobalOfflineSynchronizationData ingesteld op True (NPR-32078).

* Designer: Als de coderingsoptie is ingeschakeld, verdwijnt de subformulierrand in de gegenereerde PDF-uitvoer (NPR-32547, NPR-31983, NPR-31950).

* Designer: Als een tabel samengevoegde cellen bevat, mislukt de toegankelijkheidstest voor het PDF-uitvoerbestand dat vanuit een XDP-formulier is geconverteerd met de uitvoerservice (CQ-4285372).

* Foundation JEE: Als een Experience Manager Forms-server wordt losgekoppeld van een cluster, wordt door cacheproblemen voorkomen dat deze opnieuw verbinding maakt met de server (NPR-32412).

## Adobe Experience Manager 6.5.3.0 {#experience-manager-6530}

[!DNL Adobe Experience Manager] 6.5.3.0 is een belangrijke release die prestaties, stabiliteit, beveiliging en belangrijke correcties en verbeteringen voor klanten bevat die zijn vrijgegeven sinds de algemene beschikbaarheid van 6.5-release in **April 2019**. Het kan boven op [!DNL Adobe Experience Manager] 6.5

Enkele belangrijke kenmerken van deze Service Pack-release zijn:

* De ingebouwde opslagplaats (Apache Jackrabbit Oak) wordt bijgewerkt naar versie 1.10.6.

* [!DNL Experience Manager Assets] ondersteunt nu ZIP-archieven die zijn gemaakt met het Deflate64-algoritme.

* Er is een nieuwe kolom voor de gemaakte datum toegevoegd aan de DAM-lijstweergave en de zoekresultaten voor elementen in de lijstweergave. Deze kolom kan worden gesorteerd.

* Asset sorting based on Name column is enabled in de mening van de Lijst.

* [!DNL Dynamic Media] ondersteunt nu SmartCrop-video-elementen. Slim uitsnijden is een door computers aangedreven functie die een video bijsnijdt terwijl het frame wordt verplaatst om het brandpunt van de scène te volgen.

* [!DNL Dynamic Media] ondersteunt Smart Imaging.

* Vermogen [set Out of Office](../forms/using/configure-out-of-office-settings.md) voorkeuren in [!DNL Experience Manager] workflows.

* Vermogen [In-box- of postvakitems delen](../forms/using/configure-shared-queues-osgi.md) met andere gebruikers in [!DNL Experience Manager] workflows.

* Vermogen [Interactieve communicatie genereren in de modus Batch](../forms/using/generate-multiple-interactive-communication-using-batch-api.md).

* Bijgewerkte versie van jQuery die in ContextHub aan 3.4.1 wordt gebundeld.

### Activa {#assets-6530-enhancements}

**Verbeteringen voor producten**

* [!DNL Experience Manager Assets] ondersteunt nu ZIP-archieven die zijn gemaakt met het Deflate64-algoritme (NPR-27573).

* De nieuwe kolom voor gemaakte datum, die sorteerbaar is, wordt toegevoegd in de DAM-lijstweergave en in de resultaten voor het zoeken naar middelen in de lijstweergave (NPR-31312).

* In de lijstweergave kunnen gebruikers de lijst met elementen sorteren met [!UICONTROL Name] kolom (NPR-31299).

* De GLB-, GLTF-, OBJ- en STL-bestanden kunnen worden voorvertoond in [!UICONTROL Asset Details] pagina in DAM (CQ-4282277).

* `ReplicationOnModifyListener` gebeurtenis wordt geactiveerd voor segmentknooppunten tijdens uploaden naar segment in [!DNL Dynamic Media] (CQ-4281279).

* [!DNL Dynamic Media] ondersteunt nu SmartCrop-video-elementen. Slim uitsnijden is een door computers aangedreven functie die een video bijsnijdt terwijl het frame wordt verplaatst om het brandpunt van de scène te volgen (CQ-4278995).

* [!DNL Dynamic Media] ondersteunt Smart Imaging (CQ-4222249).

* De onderzoek of doorbladert mening wordt geplaatst als standaardmening in de plukker van de Stichting als de vraagparameters in verzoek worden overgegaan (NPR-31601).

**Oplossingen**

* Metagegevens voor sommige PDF-documenten worden niet bijgewerkt en opgeslagen op de PDF wanneer de titel wordt gewijzigd (NPR-31629).

* Delen van middelen werkt niet voor een element met het plusteken (`+`) in de bestandsnaam (NPR-31547).

* Bewerkingen in het standaardzoekformulier Middelen Admin Search Rail werken niet zoals verwacht (NPR-31502).

* Suggesties worden niet weergegeven wanneer u OmnZoeken op middelen gebruikt om middelen te zoeken (NPR-31496).

* Verwijzingen naar activa binnen verzamelingen worden niet bijgewerkt wanneer de betreffende activa naar een andere locatie worden verplaatst, in gevallen waarin naar dezelfde activa wordt verwezen door verschillende inzamelingen door verschillende gebruikers (NPR-31486).

* Er worden dubbele IPTC-tags toegevoegd aan metagegevens van elementen (NPR-31328).

* Het aantal zoekresultaten wordt niet op de juiste wijze bijgewerkt wanneer een zoekopdracht wordt gestart vanaf de filterrail (NPR-31316).

* Alle selectievakjes worden gewist wanneer de selectie van de selectievakjes van het tweede niveau in het filter Bestandstype wordt opgeheven en de tekst in de zoekbalk is niet synchroon met de geselecteerde of gedeselecteerde eigenschappen (NPR-31287).

* Niet alle leden (gebruikers/groepen) kunnen worden verwijderd uit de sectie Leden van een map. wanneer wordt geprobeerd om alle gebruikers te verwijderen, wordt de aangemelde gebruiker toegevoegd aan de lijst (NPR-31171).

* Middelen met plus-symbool (`+`) in de bestandsnaam niet kan worden verwijderd (NPR-31162).

* Het keuzemenu Maken, dat in het bovenste menu zichtbaar is wanneer u een map selecteert, geeft &#39;Map&#39; niet weer als een optie voor maken (NPR-30877).

* Mapselectie Maken > Handelitem FileUpload ontbreekt wanneer ACL voor Weigeren `jcr:removeChildNodes` en `jcr:removeNode` op pad worden toegepast voor een gebruiker (NPR-30840).

* De DAM-workflows worden in de status &#39;stale&#39; gezet wanneer bepaalde MP4-middelen worden geüpload, waardoor alle resterende workflows in de status &#39;stale&#39; gaan (NPR-30662).

* Er is een fout in het geheugen opgetreden wanneer grote PDF-bestanden (van meerdere gigabytes) naar DAM worden geüpload en de bijbehorende subbestanden worden verwerkt (NPR-30614).

* Bulkverplaatsing van activa mislukt en geeft een waarschuwingsbericht weer (NPR-30610).

* Elementnamen worden in kleine letters gewijzigd wanneer u elementen van de ene map naar de andere verplaatst in [!DNL Experience Manager] uitvoeren in [!DNL Dynamic Media]-Scene7-modus (NPR-31630).

* Er is een fout opgetreden tijdens het bewerken van een externe imageset voor de afbeelding die zich bevindt in de map met dezelfde naam als de bedrijfsnaam van Scene7 (NPR-31340).

* [!DNL Dynamic Media] activa met referenties worden niet gepubliceerd (NPR-31180).

* Uploads van [!DNL Dynamic Media]7-Scene7-modus naar [!DNL Dynamic Media Classic] duurt te lang om te voltooien (NPR-31048).

* Hotspot die aan een afbeeldingselement is toegevoegd, is niet zichtbaar via de Interactive Image Viewer op de pagina met elementdetails (NPR-30979).

* Er worden enorme slingerbanen gecreëerd en de verwerkingsbanner wordt weer weergegeven wanneer acties worden uitgevoerd op middelen in [!DNL Experience manager Assets] worden doorgegeven aan Scene7 (NPR-30947).

* Conflict doet zich voor bij het maken van Taalkopie van middelen en middelen wordt niet geüpload naar Scene7 (NPR-30932).

* Dynamische vertoningen gedownload van [!DNL Experience Manager] uitvoeren in [!DNL Dynamic Media]-De hybride modus is verbroken (deze is van het teksttype met de inhoud &#39;kan afbeelding niet vinden&#39; in plaats van het type afbeeldingsinhoud) (NPR-30876).

* [!DNL Dynamic Media] De werkstroom Video coderen kan geen miniatuur genereren voor de video waaruit wordt gemigreerd [!DNL Dynamic Media Classic] tot [!DNL Dynamic Media]-Scene7-modus op Adobe Experience Manager (CQ-428/2011).

* IpsApiException werd waargenomen terwijl het migreren van activa van één geval aan een andere gebruikend verschillende het bedrijfs identiteitskaart van Scene7 (CQ-4280548).

* De miniatuur van 3D-middelen is niet informatief wanneer een ondersteund 3D-model wordt opgenomen in [!DNL Experience Manager] (CQ-4283701).

* Schuifknoppen worden weergegeven in de viewer als een 3D-element maar weinig cameraweergaven heeft (CQ-4283322).

* Onjuiste containerhoogte van een geüpload 3D-model, voorvertoond in DimensionalViewer op de pagina Asset Details (CQ-4283309).

* Video&#39;s kunnen niet worden afgespeeld met SmartCropVideoViewer in Internet Explorer 11 en Safari (CQ-4281422).

* Het gebruik van de verplaatsingsknop om meerdere elementen van de ene map naar de andere te verplaatsen, mislukt in [!DNL Experience Manager] wordt uitgevoerd op [!DNL Dynamic Media]-Scene7 runmode (CQ-4280384).

* Vervormde video wordt weergegeven op de elementdetails wanneer het MIME-type niet MP4 is (CQ-4279704).

* Video&#39;s die onlangs in mappen met videoprofiel zijn opgenomen, worden nog steeds verwerkt nadat het coderingspercentage is voltooid tot 100% (CQ-4279389).

* Als u elementen uit een map verplaatst, ontstaan er veel slingertaken (Scene7 API-aanroepen) die bij voorkeur vereist zijn (CQ-4278664).

* Namen van de imageset worden in Scene7 gewijzigd in kleine letters, wanneer imageset (of mediaset) wordt gemaakt en benoemd met de juiste naamgevingsconventie in DAM (CQ-4281112).

* Scene7 Migrator-sets publiceren de status onjuist (CQ-4263492).

* De resultatenpagina Touch UI-zoekopdracht (uitgevoerd via Omnissearch) wordt automatisch naar boven geschoven en verliest de schuifpositie van de gebruiker in Content Fragments (CQ-4282898).

* PDF-bestanden worden niet geïndexeerd en inhoud binnen is niet doorzoekbaar (CQ-4278916).

* Een fout &quot;Groep niet vermeld door de plukker van de gebruiker: onwaar verwacht om waar te zijn&quot; wordt waargenomen bij het toevoegen van een gesloten gebruikersgroep met een andere `principalName` en `authorizableId` (CQ-4278177).

* De Mening van de Kolom UI van activa toont alle wegen ongeacht de de dampwortel van specifieke huurder weg (CQ-4278175).

* Het zoeken door de kiezer van middelen werkt niet zoals verwacht (CQ-4275886).

* Workflows voor uitvoering ontbreken (CQ-4271928).

* Met DAM-gebeurtenis wissen verwijdert u de meest recente (`maxSavedActivities`) gegevens van gebeurtenissen en houdt de eerder gemaakte gegevens bij (NPR-31336).

* De resultatenpagina Touch UI-zoekopdracht (uitgevoerd via Omnissearch) wordt automatisch naar boven geschoven en verliest de schuifpositie van de gebruiker (NPR-31307).

* De actiebalk en het aantal elementen worden niet bijgewerkt wanneer u alle items selecteert en vervolgens de selectie van bepaalde items (mappen/afzonderlijke elementen) in Touch UI (NPR-31118) opheft.

* Een uitzondering wordt weergegeven in [!DNL Experience Manager] tijdens de opiniepeiling voor de taakdetails van een middel (CQ-4283569).

### Sites

* Als de overerving van LiveCopy is verbroken, worden op live kopieerpagina&#39;s links naar taalkopieën weergegeven in plaats van LiveCopy-koppelingen (NPR-30980).
* Voor een nieuwe blauwdruk, als het aantal verslagen meer dan 40 is, slechts worden de eerste 40 verslagen getoond. Blauwdruk geeft lege regels weer voor de rest van de records (NPR-31182).
* Wanneer een gebruiker Japanse of Koreaanse karakters in het beschrijvingsbezit van een menu toevoegt, toont het menu vervormde karakters voor Japans en Koreaans taaltekst (NPR-31331).
* De Rich Text Editor (RTE) staat niet toe om een ingesloten tabel in te voegen als lijstitem (NPR-30879).
* Buiten het vak, de basislijn van de Rich Text Editor (RTE). past inline font-size toe op elementen, onverwacht (NPR-31284).
* Wanneer een gebruiker de linkerspoorgebieden concentreert en een toetsenbordkortere weg gebruikt om inhoud te kleven, kleeft het de inhoud van het paginageditor klembord in plaats van de inhoud die van de linkerspoorgebieden wordt gekopieerd (NPR-31172).
* Wanneer een gebruiker een veld Bestand uploaden toevoegt aan een veld met meerdere velden, wordt het afbeeldingspad opgeslagen in het componentknooppunt in plaats van het knooppunt met meerdere velden (NPR-30882).
* De `ResponsiveGridExporter` API retourneert niet `com.day.cq.wcm.foundation.model.impl.export.AllowedComponentsExporter` interface. De `com.day.cq.wcm.foundation.model.impl` pakket wordt gedeclareerd als een particulier pakket (NPR-31398).

<!-- Review: NPR-31398 has fixVersion as 6530. However, it is mentioned twice in 6530 and 6520 as fixed. 
Remove one mention of this fix.
-->

* Wanneer een pagina die bepaalde fragmenten uit de ervaring bevat, wordt geopend in de modus Niet-editor (in Auteur zonder de opdracht `editor.html` voorvoegsel en `wcmmode=disabled`, of in Publisher)., eindigt de aanvraag in de code van de HTTP-statusfout. `500` (NPR-30743).
* Gebruikers kunnen hun wachtwoord niet wijzigen en toegang krijgen tot hun profielpagina (NPR-31161).

### Zoeken en gebruikersinterface {#ui-interface-and-search}

* Wanneer u op een pagina met zoekresultaten overschakelt van de kaartweergave naar de lijstweergave, is er een vertraging voordat de pagina kan worden geschoven (NPR-31286).

* De [!UICONTROL Select All] selectievakje is verborgen in de lijstweergave op [!DNL Sites] gebruikersinterface (NPR-31614).

* De [!UICONTROL Select All] Het aantal op een pagina met zoekresultaten is onjuist (NPR-31120).

* In de metagegevenseditor worden tags weergegeven die niet bestaan (NPR-31119).

### Vertaling {#translation}

* Er worden twee kalenderpop-ups weergegeven bij het selecteren van de optie Einddatum in een vertaaltaak (NPR-31270).

### Platform

* De Mime typeoptie in de console van het Web werkt niet (NPR-31108).

* Clientcertificaat wordt niet geaccepteerd bij het configureren van Single Sign-On (NPR-31165).

* Updates in de configuratie van de buffergrootte voor de op Jetty-Gebaseerde dienst van HTTP worden niet bewaard (NPR-30925).

* QueryBuilder biedt nu ondersteuning voor orderby `fn:name()` in xpath query&#39;s (NPR-31322).

* Er wordt een dubbele activeringsstructuur gemaakt bij een upgrade van [!DNL Experience Manager] 6.3 (NPR-31513).

* Door:sturen verzoeken bewaren antwoordkopballen niet die tijdens het verbinden authentificatie (NPR-30013) worden geplaatst.

* Zoeken in de kiezercomponenten werkt niet (NPR-31692).

* Er wordt een fout weergegeven bij het koppelen van een ZIP-bestand aan een [!DNL Experience Manager Communities] post vanwege verschillende versies van Apache POI en Apache Tika bundle (NPR-31018).

* De `org.apache.sling.distribution.api` wordt verborgen in de configuratiemanager en is daarom niet beschikbaar voor aangepaste bundels (NPR-31720).

### Projecten

* Schakelen tussen kalenderweergaven werkt niet (NPR-31271).

### Brand Portal {#assets-brand-portal-6530}

**Verbeteringen voor producten**

* Workflow voor het importeren van bronnen in [!DNL Experience Manager Assets] wordt gewijzigd om alleen de nieuwe elementen op te halen uit [!DNL Brand Portal] tot [!DNL Experience Manager]en sla de elementen over die al in de map NEW staan om replicatie te voorkomen (CQ-4278527).

**Oplossingen**

* Er wordt een onjuist pictogram weergegeven bij het maken van een nieuwe map voor bijdragen in de functie voor het zoeken naar middelen (CQ-4282825).
* Bij het maken van een nieuwe Contribute-map worden een of beide submappen (NEW en SHARED) niet weergegeven in de map Contribution (CQ-4282424).
* Het systeem genereert een uitzondering als de gebruiker probeert om de omslag van de Bijdrage van opnieuw te publiceren [!DNL Experience Manager] tot [!DNL Brand Portal] na ontvangst van nieuwe elementen in de map Contributie van [!DNL Brand Portal] end (CQ-4279740).
* Het is niet toegestaan om een Contribute-map te maken in een map met bijdragen (geneste map) om complexiteit te voorkomen (CQ-4278391).
* Het systeem genereert een uitzondering bij het uploaden van het [!DNL Brand Portal] gebruikerslijst (.csv-bestand) geïmporteerd uit [!DNL Experience Manager] Admin Console. Alleen de velden E-mail, Voornaam en Achternaam in het CSV-bestand zijn verplicht (CQ-4278390).

### Gemeenschappen {#communities-6530}

**Oplossingen**

* Snelle koppelingen voor het beheer van groepen (groepen Openen/Bewerken/Publiceren/Verwijderen) zijn niet zichtbaar voor de communautaire beheerders (beheer van groep/site) (NPR-31627).
* Een verzonden blog wordt alleen weergegeven als de pagina handmatig wordt vernieuwd of opnieuw wordt geladen (NPR-31599).
* De JCR-query die wordt gebruikt door de functie &quot;Misions&quot; is hoofdlettergevoelig en het duurt te lang om resultaten te retourneren (NPR-31475).
* [!DNL Experience Manager] 6.5 het dossier van UberJar werpt uitzondering, `cq-social-translation` bundel ontbreekt uit [!DNL Experience Manager] 6.5 UberJar-bestand (NPR-31186).
* Jackson Databind-bibliotheken bijgewerkt naar versie 2.9.9.3 om nieuwe kwetsbaarheden te verhelpen (NPR-30967).
* Activiteiten en aanmeldingstitels zijn inconsistent (NPR-30941).
* Paginering werkt niet correct in [!DNL Communities] Blogs (NPR-30914).
* Analyserapporten worden niet ingevuld in [!DNL Experience Manager] auteursomgeving, lege pagina verschijnt (NPR-30913).

### Eik {#oak}

* De indexupdates van Lucene die auteurserver veroorzaken om te vertragen (NPR-31548).

### Forms {#forms-6530}

>[!NOTE]
>
>[!DNL Experience Manager] Service Pack bevat geen oplossingen voor [!DNL Experience Manager Forms]. Ze worden geleverd met een apart Forms-add-onpakket. Daarnaast wordt een cumulatief installatieprogramma uitgebracht dat oplossingen bevat voor [!DNL Experience Manager Forms] op JEE. Zie voor meer informatie [Experience Manager Forms-invoegtoepassing installeren](/help/release-notes/sp-release-notes.md#install-aem-forms-add-on-package) en [Experience Manager Forms installeren op JEE](/help/release-notes/sp-release-notes.md#install-aem-forms-jee-installer).

#### Forms-invoegtoepassing {#forms-add-on-package-6530}

**Adaptieve Forms**

* Tekenreeksen bevatten de woordenboeksleutel bij het lokaliseren van adaptieve formulieren (NPR-31110).

**Interactieve communicatie**

* **MissingNode.toString()** retourneert onjuiste resultaten na het upgraden van Jackson-bibliotheken naar 2.10.0 (NPR-31549).

* Teksteditor verwijdert willekeurig spatietekens uit de tekst die uit Microsoft Word is gekopieerd (NPR-31113).

**Correspondentenbeheer**

* Bijschriften en knopinfo worden niet weergegeven tijdens het migreren van letters van LiveCycle ES4SP1 naar [!DNL Experience Manager] 6.5 (NPR-31615).

* **Tekststroomopmaak wordt niet meer ondersteund** foutbericht wordt weergegeven tijdens het opslaan van letters als concepten (NPR-30463).

**Workflow**

* OSGi-workflow mislukt als gevolg van 100% CPU-gebruik (NPR-31233).

**HTML5 Forms**

* Als u een HTML5-voorbeeld van een XDP-formulier genereert, wordt een flikkering weergegeven terwijl exemplaren van een subformulier worden toegevoegd (NPR-30909).

#### Forms op JEE-installatieprogramma {#forms-jee-installer-6530}

**Forms - Document Services**

* De de Webdienst van de ZEEP die MTOM in een .NET project gebruikt toont uitzonderingen voor AssemblerServiceClient aanhaalt en methodes HtmlToPDF2 (NPR-4281771).

* Beveiligingskwetsbaarheid 2012-5784 en 2014-3596 gevonden met AXIS 1.4-jar en oplossing meegeleverd bij [AXIS1.4.1 jar](https://helpx.adobe.com/aem-forms/quick-fixes/6-5/jee-patch-0014.html) (NPR-31015).

**Foundation JEE**

* De configuratie van de actie laadt niet de procesnamen voor het aanhalen van een Forms Workflow voorlegt actie (NPR-31478).

### Inclusief functiepakketten {#feature-packs-included-6530}

>[!NOTE]
>
>Voor [!DNL Experience Manager Forms] klanten, is het essentieel om te installeren [!DNL Experience Manager Forms] invoegpakket na installatie van een [!DNL Experience Manager] Service Pack, Cumulative Fix Pack of Feature Pack.

#### Forms - Foundation JEE {#forms-foundation-jee-feature}

* [!DNL Experience Manager] Forms-steun voor Oracle 18c (NPR-29155).

## Adobe Experience Manager 6.5.2.0 {#experience-manager-6520}

[!DNL Adobe Experience Manager] 6.5.2.0 is een belangrijke versie die prestaties, stabiliteit, veiligheid, en belangrijkste klantenmoeilijke situaties en verhogingen omvat die sinds de algemene beschikbaarheid van [!DNL Adobe Experience Manager] 6,5 inch **April 2019**. Het kan boven op [!DNL Experience Manager] 6.5

Enkele belangrijke kenmerken van deze Service Pack-release zijn:

* De ingebouwde opslagplaats (Apache Jackrabbit Oak) wordt bijgewerkt naar versie 1.10.3.
* Een configuratie-eigenschap toegevoegd om het exporteren van Experience Fragments rechtstreeks toe te staan naar door de gebruiker gedefinieerde werkruimten voor [!DNL Adobe Target].
* Met middelen kunnen gebruikers visueel vergelijkbare afbeeldingen zoeken. [!DNL Experience Manager] geeft de slimme getagde afbeeldingen uit de DAM-opslagplaats weer die lijken op een door de gebruiker geselecteerde afbeelding. Zie [visueel zoeken](../assets/search-assets.md#visualsearch).

* Verbeterde functionaliteit Connected Assets om ondersteuning toe te voegen voor het ophalen van documenten van externe DAM-implementaties. Siteauteurs kunnen nu ondersteunde documenttypen zoeken en filteren in de Inhoudszoeker. De externe documenten kunnen worden toegevoegd aan de component Download op webpagina&#39;s. Zie [gekoppelde elementen gebruiken](../assets/use-assets-across-connected-assets-instances.md).

* Filters van het type Document verbeteren met meer types MIME om multi-getaxeerde opties te steunen.
* Introduceerde een externe workflow voor herverwerking voor ondersteuning van meerdere bronnen.
* Geoptimaliseerd [!DNL Dynamic Media] prestaties door standaardactivafilters voor replicatie te gebruiken.
* Opties voor het bewerken van middelen voor uitsnijden en roteren zijn hersteld voor DMS7.
* Een optie geïmplementeerd om een video te dempen tijdens het laden in VideoPlayer.
* Repareren om ervoor te zorgen dat de de kolommening van Activa slechts huurdersspecifieke inhoud toont.
* Oplossing voor wijzigingen in stijlaccordeon in zoekresultaten.

### Activa

**Verbeteringen voor producten**

* Verbeterde functionaliteit Connected Assets om ondersteuning toe te voegen voor het ophalen van documenten van externe DAM-implementaties. Siteauteurs kunnen nu ondersteunde documenttypen zoeken en filteren in de Inhoudszoeker. De externe documenten kunnen worden toegevoegd aan de component Download op webpagina&#39;s. Hotfix voor CQ-4270245. Zie [gekoppelde elementen gebruiken](/help/assets/use-assets-across-connected-assets-instances.md).

* [!DNL Experience Manager Assets] gebruikers kunnen visueel vergelijkbare afbeeldingen zoeken. [!DNL Experience Manager] geeft de slimme getagde afbeeldingen uit de DAM-opslagplaats weer die lijken op een door de gebruiker geselecteerde afbeelding. Zie [visueel zoeken](../assets/search-assets.md#visualsearch).

**Oplossingen**

* Elementpaden in URL&#39;s en mapmetagegevens die door de ACS-API worden gegenereerd, worden niet via URL gecodeerd. GRANITE-26198: Hotfix voor CQ-4271814
* Het uitpakken van een archief met een map met een procentteken (%) in de naam kan niet worden geopend met [!DNL Experience Manager Assets] interface. NPR-29989: Hotfix voor CQ-4270467
* Aanraakinterface: Tijdens de wizard Publiceren beheren worden verwijzingen toegevoegd na de pagina in de hoofdtekst van het postverzoek, waardoor alle elementen na de pagina worden gepubliceerd. Wanneer de pagina wordt weergegeven, worden sommige elementen in de publicatieinstantie overgeslagen. NPR-29985: Hotfix voor CQ-4270724
* De functie Niet-gerelateerd element Element werkt niet voor gerelateerde elementen die speciale tekens (tekens die door URI worden gecodeerd) in de naam hebben. NPR-30387: Hotfix voor CQ-4274446
* Wanneer u een inhoudsfragment bewerkt, wordt de versie gemaakt met de verkeerde gebruiker.
* Mislukking tijdens het creëren van inzamelingen op het Gebaseerde systeem van de Aannemer. NPR-30114: Hotfix voor CQ-4272948
* De de kolommening van activa UI respecteert niet de de damwortel van de huidige huurder maar de toegang tot van alle paden van de huurdersdam. NPR-30636: Hotfix voor CQ-4275481
* Mogelijke XSS-aanval (cross-site scripting) via een beperkt waarschuwingsvenster voor bestanden, aangezien de geïnjecteerde afbeelding zichtbaar is. NPR-30617: Hotfix voor CQ-4270133
* MultiTenant: Bij huurders die mapeigenschappen opslaan, wordt zowel een melding met de succesmelding als een foutbericht weergegeven waarin de handeling wordt beschreven. &quot;Kan de eigenschappen niet bewerken. Onvoldoende rechten.&quot; dat leidt tot verwarring . NPR-30545: Hotfix voor CQ-4275333
* In het dialoogvenster Asset Selector is het selecteren van elementen niet toegestaan. De bron kan daarom niet worden bijgewerkt met de desbetreffende functie voor bronvervanging. NPR-30502: Hotfix voor CQ-4275029
* [!UICONTROL DAM Update Asset] workflow - In de status Gestreefd bij het uploaden van grote MP4-bestanden. NPR-30480: Hotfix voor CQ-4271352
* De functie Revisietaak maken werkt niet omdat de payload null is en alle volgende aan een revisie gerelateerde handelingen mislukken. NPR-30468: Hotfix voor CQ-4274263
* Verbindingsprobleem met Adobe Smart Tag via Datapower. NPR-30026: Hotfix voor CQ-4269457
* In de kolomweergave van elementen wordt een fout gegenereerd wanneer wordt geprobeerd de filters te openen zonder rails. NPR-30501: Hotfix voor CQ-4273862
* Wanneer u groepen toevoegt die via LDAP zijn gesynchroniseerd in de CUG-eigenschappen (Closed User Group) van een map Asset, wordt de groep niet opgeslagen en opgehaald. NPR-30615: Hotfix voor CQ-4274689
* De de onderzoeksstijl en richtingsgebieden van het filter passen niet de autocompleted waarde op de onderzoeksvraag toe. NPR-30620: Hotfix voor CQ-4275724
* Koppeling voor het delen van middelen van een map met spatie en &quot;&amp;&quot;-teken in de naam geeft lege grijze kaarten voor bepaalde elementen weer. NPR-30557: Hotfix voor CQ-4270187
* Het metagegevensschema van mappen detecteert het gegevenstype niet automatisch en maakt dus geen gerelateerde TypeHint in de vorm van het verzenden van formulieren. NPR-30599: Hotfix voor CQ-4275227
* Opties voor het bewerken van elementen uitsnijden en roteren zijn uitgeschakeld in de DMS7-ontwerpinterface. NPR-30118: Hotfix voor CQ-4273221
* De functie Koppeling delen werkt niet aan [!DNL Experience Manager] instantie met DMS7-configuratie. NPR-30080, NPR-30492: Hotfix voor CQ-4273651
* Het toevoegen van [!DNL Dynamic Media]-Scene7 component aan de pagina, en dan het publiceren van de pagina teweegbrengt niet de configuratie dmscene7 telkens teweeg. NPR-30641: Hotfix voor CQ-4275962
* IPSJobJournal toegevoegd in [!DNL Experience Manager] om slechts één baan van de Systemen van de Preventie van het Binnendringen (IPS) per verwerkingsprofiel tot stand te brengen. NPR-30490: Hotfix voor CQ-4273614
* [!DNL Dynamic Media]: Er zijn standaardfilters toegevoegd om te voorkomen dat elementen worden gerepliceerd naar de [!DNL Experience Manager] publicatieknooppunt. NPR-30538: Hotfix voor CQ-4274678
* Introduceerde een externe werkstroom van het Herproces voor multi-middelsteun om omslag als lading toe te staan. De werkstroom heeft twee stappen - verwerkt activa zonder handvatten via meta-gegevenskaart aan volgende stap opnieuw en uploadt alle activa zonder activa handvat aan S7 in één enkele IPS baan. Voor meer details, zie het Vormen [!DNL Dynamic Media] Cloud Services. NPR-30489: Hotfix voor CQ-4272903
* Het uploaden van onjuiste CSV na correcte CSV wipes uit correcte CSV. Hotfix voor CQ-4277694, CQ-4277814
* Het onjuiste pictogram dat specifiek is voor de bijdragemappen die moeten worden verwijderd. Hotfix voor CQ-4277580
* Als u een gebruiker selecteert in de gebruikerskiezer op het tabblad Asset Contribution, wordt de naam van de gebruiker niet weergegeven in de tabel en wordt in het dialoogvenster Gebruikers verwijderen op de eigenschappenpagina een onjuiste tekst weergegeven. Hotfix voor CQ-4277875
* Medewerkers kunnen niet vanuit de gebruikerskiezer worden toegevoegd aan de map Asset Contributor door een gebruiker te selecteren en op Toevoegen te klikken. Hotfix voor CQ-4277824, CQ-4278087
* Zoeken in kleine letters werkt niet in de gebruikerskiezer. Hotfix voor CQ-4277958, CQ-4277930
* Niet-beheerders kunnen elementen publiceren in een nieuwe map in de map Asset Contribution. Hotfix voor CQ-4278200
* de gebruiker van de dam (niet-admin) heeft geen optie om contribuanten aan de omslag van de inbreng van Activa toe te voegen. Hotfix voor CQ-4278192
* De knop Maken is zichtbaar in de map Asset Contribution. Hotfix voor CQ-4277560
* Zoekopdracht sorteren op relevantieresultaten [!DNL InDesign] documenten samen met [!DNL InDesign] sjablonen. Hotfix voor CQ-4273864
* Als de gebruiker een e-mailadres in hoofdletters heeft, kunnen gebruikers niet inchecken voor de elementen die eerder zijn uitgecheckt. Hotfix voor CQ-4276575
* De bewerking Verwijderen is alleen van toepassing op voorinstellingen die zijn geselecteerd. Als de lijst na de bewerking automatisch wordt vernieuwd op het scherm, worden andere voorinstellingen weergegeven die al zijn vernieuwd. Hotfix voor CQ-4261461
* Configureren [!DNL Dynamic Media] Cloud Services in [!DNL Dynamic Media]-De hybride wijze resulteert in veelvoudige lege rapportreeksen die in worden gecreeerd [!DNL Analytics]en zonder rapportsuite-id opgeslagen in [!DNL Experience Manager], resulterend in rapportsuite duplicatie. Hotfix voor CQ-4249780
* Naam van bewerking wijzigen in [!DNL Experience Manager] Het element met gedupliceerde naam kan niet worden gesynchroniseerd met Scene7. Hotfix voor CQ-4276763
* Door de gebruiker gegenereerde inhoud wordt onjuist weergegeven in het deelvenster met zoekfilters. Hotfix voor CQ-4273875
* De optie Vergelijkbare zoeken is niet beschikbaar voor TIFF-afbeeldingen. Hotfix voor CQ-4278238
* Geïmplementeerde optie om video te dempen bij het laden in VideoPlayer. Hotfix voor CQ-4266465
* Viewers - VideoViewer: poster=none werkt onjuist als een externe video wordt gebruikt. Hotfix voor CQ-4265536
* Het pictogram Wachten is zichtbaar tijdens het afspelen van video in IE11- en MS Edge-browsers. Hotfix voor CQ-4251539
* 3.8 SDK- en 5.13 README-bestanden voor viewers worden niet bijgewerkt en bevatten informatie uit eerdere releases. Hotfix voor CQ-4273737
* Inhoudsfragment wordt versieeerd, zelfs voordat de wijzigingen worden opgeslagen. NPR-30616: Hotfix voor CQ-4273088
* Vervang Asset#getMetadata(String) door Asset#getMetadataValueFromJcr(String) in het miniatuurproces. NPR-30491: Hotfix voor CQ-4273067
* Bij het uploaden van jpg wordt het bericht op meerdere plaatsen weergegeven: &quot;ReplicateOnModifyWorker Replicating UPDATED&quot; voor elk element, waardoor de prestaties afnemen.
* Als u het ZIP-archief uitpakt met de functie Archiveren uitpakken, ontstaan er problemen met mappen waarvan de naam een percentage (%) in de titel bevat. NPR-29990: Hotfix voor CQ-4270467

### Sites {#sites-6520}

* Als de overerving van LiveCopy is verbroken, worden op live kopieerpagina&#39;s links naar taalkopieën weergegeven in plaats van LiveCopy-koppelingen (NPR-30980).
* Voor een nieuwe blauwdruk worden alleen de eerste 40 records weergegeven als het aantal records groter is dan 40. Met Blueprint worden lege regels weergegeven voor de rest van de records (NPR-31182).
* Plug-in Rich Text Editor (RTE) van de tekstcomponent geeft vervormde tekens voor Japanse en Koreaanse tekst weer (NPR-31331).
* De Rich Text Editor (RTE) staat niet toe om een ingesloten tabel in te voegen als lijstitem (NPR-30879).
* De RTE (Rich Text Editor) is een onverwacht gealigneerde tekengrootte van buiten het vak en past deze onverwacht toe op elementen (NPR-31284).
* Wanneer een gebruiker de linkerspoorgebieden concentreert en toetsenbordkortere weg gebruikt om inhoud te kleven, kleeft het inhoud van pagina redacteurs klembord in plaats van de inhoud die van linkerspoorgebieden wordt gekopieerd (NPR-31172).
* Wanneer een gebruiker een veld Bestand uploaden toevoegt aan een veld met meerdere velden, wordt het afbeeldingspad opgeslagen in het componentknooppunt in plaats van het knooppunt met meerdere velden (NPR-30882).
* De `ResponsiveGridExporter` API retourneert niet `com.day.cq.wcm.foundation.model.impl.export.AllowedComponentsExporter` interface. De `com.day.cq.wcm.foundation.model.impl` pakket wordt gedeclareerd als particulier pakket (NPR-31398).
* Wanneer een pagina die bepaalde fragmenten uit de ervaring bevat, wordt geopend in de modus Niet-editor (in Auteur zonder de opdracht `editor.html` voorvoegsel en `wcmmode=disabled`, of in Publisher), eindigt de aanvraag in HTTP-statusfoutcode 500 (NPR-30743).

### WCM - Pagina-editor {#wcm-page-editor-6520}

**Verbeteringen voor producten**

* `EnhanceDocument` Typ filters met meer MIME-typen ter ondersteuning van multigetaxeerde opties. Hotfix voor CQ-4270694

### Beheer van inhoudsfragmenten {#content-fragment-management-6520}

* De query die wordt gebruikt door de gebruikersinterface van Content Fragment-modellen is erg langzaam en resulteert uiteindelijk in een fout. Hotfix voor CQ-4270807

### UI - Foundation {#ui-foundation}

* Sneltoetsen die voorkomen dat de gebruiker &#39;m,&#39; &#39;p,&#39; &#39;e&#39; gebruikt in specifieke gebruikersinterfaces. NPR-30355: Hotfix voor GRANITE-26346
* Sluiting [!DNL Experience Manager Assets] De zoekinterface herstelt de selectie van de linkerrail niet naar de inhoud, zodat de gebruiker de filterrail de tweede keer kan openen. NPR-30509: Hotfix voor CQ-4274716
* Omgeving met meerdere gebruikers: [!DNL Experience Manager Assets] De bovenste navigatie van de gebruikersinterface is niet beschikbaar en er wordt een JavaScript-fout gegenereerd. NPR-30104: Hotfix voor GRANITE-26344

### Vertaling {#translation-6520}

* Probleem met vertaling - Slechts een paar componenten worden vertaald met behulp van Machine Translation. NPR-30079: Hotfix voor CQ-4273764

### Platform {#platform-6520}

* [!DNL Experience Manager] De standaard afzender van de Post kan geen post naar een verre server SMTP over TLS v1.2 verzenden. NPR-30476: Hotfix voor GRANITE-26605

### Projecten {#projects-6520}

* dam:folderThumbnailPaths de waarden worden niet vernieuwd en tonen oude duimnagels zelfs na het schrappen van de activa binnen de omslag. NPR-30424: Hotfix voor CQ-4273667
* Als u de optie &quot;verplaatsen&quot; voltooit, blijven de titel en de naam van het element ongewijzigd. NPR-30647: Hotfix voor CQ-4276265

### Gemeenschappen {#communities-6520}

* Diagnostiek voor gebruikerssynchronisatie is volledig verbroken en werkt niet. NPR-30004, NPR-29943: Hotfix voor CQ-4270287, CQ-4271348

### Sling {#sling}

* De bijgewerkte instantie van 6.3.3.2 tot 6.5 resulteert in dubbele configuraties OSGi. NPR-30130: Hotfix voor CQ-4274016

### Integratie

* De aangepaste inhoud wordt pas correct weergegeven op de publicatieversie als de instantie opnieuw is gestart. NPR-30377: Hotfix voor CQ-4273706
* Wanneer u Starten op een website configureert, wordt voor het bibliotheekadres een schuine streep (/) toegevoegd, zodat u telkens handmatig kunt ingrijpen. NPR-30694: Hotfix voor CQ-4275501

### Forms {#forms-6520}

>[!NOTE]
>
>[!DNL Experience Manager] Service Pack bevat geen oplossingen voor [!DNL Experience Manager Forms]. Ze worden geleverd met behulp van een aparte [!DNL Forms] add-on-pakket. Daarnaast wordt een cumulatief installatieprogramma uitgebracht dat oplossingen bevat voor [!DNL Experience Manager Forms] op JEE. Zie voor meer informatie [Experience Manager Forms-invoegtoepassing installeren](/help/release-notes/sp-release-notes.md#install-aem-forms-add-on-package) en [Experience Manager Forms installeren op JEE](/help/release-notes/sp-release-notes.md#install-aem-forms-jee-installer).

De belangrijkste markeringen voor [!DNL Experience Manager] 6.5.2.0 vormen zijn:

* Instelling Automatisch toegevoegd aan `RenderAtClient` in `PDFFormRenderOptions` API voor [!DNL Experience Manager] Forms OSGi.

#### Forms-invoegtoepassing

**Back-end integratie**

* Kan het formuliergegevensmodel niet configureren met een door AWS gehoste taakgebalanceerde URL. NPR-30123: Hotfix voor CQ-4273359
* Tijdens het creëren van het Model van de Gegevens van de Vorm (FDM) met de Taal van de Definitie van de Dienst van het Web (WSDL), het foutenbericht `Caused by: com.adobe.aem.dermis.exception.DermisException: java.lang.Exception: Unable to handle content type` wordt geretourneerd: NPR-30477: Hotfix voor CQ-4272921

**Correspondentenbeheer**

* De vertoning van de &quot;van de Correspondentie UI van de Making (CCR UI) ontbreekt periodiek met hieronder fout in console:
   `- Uncaught Error: variable [object Object]is already known the letter`- NPR-30127

**Interactieve communicatie**

* Een veld dat is gemarkeerd als vereist in het formuliergegevensmodel, wordt weergegeven als vereist in de interface Correspondentie maken (CCR UI). NPR-30623: Hotfix voor CQ-4274902

**Forms - Workflow**

* Niet-toegewezen uitvoervariabelen op Gecontroleerde mappen zorgen ervoor dat de activering mislukt. Hotfix voor CQ-4264451

**HTML5 Forms**

* Wanneer de douanecode of het project voor de tweede keer wordt opgesteld, geeft de pagina niet terug en de volgende fout komt voor:

   `org.apache.sling.scripting.sightly.SightlyException.`

   NPR-30539: Hotfix voor CQ-4272509

* Als u in de modus Bladeren een HTML5-formulier leest met toegang tot niet-visuele desktop, leest de Chrome-browser &quot;grafisch&quot; vóór elke Scalable Vector Graphic (SVG) in het formulierontwerp. NPR-30449: Hotfix voor CQ-4274732

#### Forms JEE-installatieprogramma

**Forms - Documentbeveiliging**

* Het toepassen van een handtekening met tijdstempel mislukt vanwege een fout: ALC-DSC-003-000: com.adobe.idp.dsc.DSCInvocationException: Inroepfout. NPR-30820: Hotfix voor CQ-4275852

**Forms - Document Services**

* Als de &quot;SubmitURL&quot;een en-teken (&amp;) bevat, worden de parseringsfouten gezien in het logbestand wanneer de POST-aanvraag wordt ingediend op `renderpdf` servlet. NPR-30865: Hotfix voor CQ-4278232

**Forms - Foundation JEE**

* De HTMLtoPDF-service geeft maxReuseCount niet weer in de JMX-console. NPR-30134, NPR-30304: Hotfix voor CQ-4273763
* Een webserviceverbinding toevoegen of bewerken door webservices aan te roepen vanuit [!DNL Experience Manager Forms] Workbench genereert een fout: ClassNotFoundException org.apache.axis.message.SOAPBodyElement. NPR-30105: Hotfix voor CQ-4273217

### Inclusief functiepakketten

>[!NOTE]
>
>Voor [!DNL Experience Manager Forms] klanten, is het essentieel om te installeren [!DNL Experience Manager Forms] invoegpakket na installatie van een [!DNL Experience Manager] Service Pack, Cumulative Fix Pack of Feature Pack.

#### Sites {#sites-feature-packs-included}

* Een configuratie-eigenschap toegevoegd om het exporteren van Experience Fragments rechtstreeks toe te staan naar door de gebruiker gedefinieerde werkruimten voor [!DNL Adobe Target]. NPR-29189: Hotfix voor CQ-4249782

#### Forms - Document Services {#forms-document-services-1}

* Instelling Automatisch toegevoegd aan `RenderAtClient` in `PDFFormRenderOptions` API voor [!DNL Experience Manager Forms] OSGi. NPR-30759: Hotfix voor CQ-4278193

## Adobe Experience Manager 6.5.1.0 {#experience-manager-6510}

[!DNL Adobe Experience Manager] 6.5.1.0 is een belangrijke versie die prestaties, stabiliteit, veiligheid, en belangrijkste klantenmoeilijke situaties en verhogingen omvat die sinds de algemene beschikbaarheid van [!DNL Adobe Experience Manager] 6,5 inch *april 2019.* Het kan boven op [!DNL Experience Manager] 6.5

Enkele belangrijke kenmerken van deze Service Pack-release zijn:

* De opname van de status dynamic-UI in het bijhouden van gebeurtenissen als aangepaste kenmerken ingeschakeld.
* Inclusief ondersteuning voor de levering van video-elementen van 360 graden in [!DNL Dynamic Media]-Scene7-modus.
* Ingeschakeld *Japanse tekstomloop* gebruiken via de stijlenplug-in van de Rich Text Editor. Zie voor meer informatie [Japanse tekstomloop configureren](/help/sites-administering/configure-rich-text-editor-plug-ins.md#jpwordwrap)

### Activa

* Bijgewerkte interface DAM DMGateway voor S3 multipart steun. NPR-29740: Hotfix voor CQ-4226303
* Voorvertoning van uitvoeringen genereert `Only empty tenantId is currently supported` fout na upgrade naar [!DNL Experience Manager] 6.5 NPR-29986: Hotfix voor CQ-4272353
* Dialoogvenster Verwijderen is niet zichtbaar om het verwijderen van taken toe te staan. NPR-29720: Hotfix voor CQ-4271074
* Na het toevoegen van een elementtitel in de eigenschappenpagina wanneer een gebruiker de pagina probeert te sluiten, [!DNL Experience Manager] Hiermee opent u de eigenschappenpagina opnieuw. NPR-29627: Hotfix voor CQ-4264929
* VersioningTimelineEventProvider moet een hoofdversie leveren samen met het knooppunt van het type nt: versie. Hotfix voor GRANITE-26063
* De mogelijkheid om 360 sferische video&#39;s te uploaden en af te spelen geïmplementeerd in [!DNL Experience Manager] DM-Scene7-modus. Hotfix voor CQ-4265131
* Met Live kopie wordt een onjuiste status opgehaald als de bron wordt bewerkt. Hotfix voor CQ-4265451
* Ondersteuning voor beheer van meerdere sites ingeschakeld voor [!DNL Experience Manager Assets]. Hotfix voor CQ-4271453, CQ-4268621, CQ-4257491
* [!DNL Experience Manager] de interface moet een extra ingang voor de huidige versie van het element in de chronologiegeschiedenis tonen, tonend de recentste controle commentaar van [!DNL Adobe Asset Link]. Hotfix voor CQ-4262864
* In de tijdlijn van het inhoudsfragment wordt een foutbericht weergegeven wanneer eigenschappen ontbreken. Hotfix voor CQ-4272560
* Dit is een probleem met Scene7-videospeler wanneer deze wordt uitgevouwen tot volledig scherm. Hotfix voor CQ-4266700
* ZoomVerticalViewer: Panknoppen mogen niet worden weergegeven als één afbeeldingselement wordt gebruikt. Hotfix voor CQ-4264795
* Als u een onderliggende node in de live kopie verwijdert, moet de liveRelationship worden losgekoppeld. Hotfix voor CQ-4270395
* Het meta-gegevensschema bevat slechts punten van de globale configuratie en mist degenen van de actieve huurder. De URL-waarde van het formPath wordt weer ingesteld op de standaardwaarde, zelfs als deze wordt gewijzigd. NPR-29945: Hotfix voor CQ-4262898
* Voorinstellingen voor afbeeldingen publiceren naar [!DNL Brand Portal] mislukt met 500 foutcode. NPR-29510: Hotfix voor CQ-4268659

### Sites

* Lege eigenschappen en meerdere eigenschappen verspreiden zich niet van blauwdruk tijdens de rollout. Actieve kopie herstellen met blauwdruk werkt niet voor componenten. NPR-29253: Hotfix voor CQ-4264928, CQ-4264926, CQ-4267722
* CoralUI, indien gebruikt met `Multifield`, slaat de `fileReferenceParameter` op componentniveau in plaats van op multifield niveau. NPR-29537: Hotfix voor CQ-4266129
* Verbetering van [!DNL Experience Manager] tekstcomponent en Teksteditor naar Japans. NPR-29785: Hotfix voor CQ-4265090
* De pagina die wordt teruggezet met Timewarp, moet naar het correcte beeld op het tijdstip van versioning verwijzen. NPR-29431: Hotfix voor CQ-4262638
* An issue with the inheritance of Style System nodes from parent to child. NPR-29516: Hotfix voor CQ-4270330
* Een foutbericht tijdens het instellen van de sociale postfunctie op [!DNL Facebook] verificatie. NPR-29211: Hotfix voor CQ-4266630
* De weergegeven miniatuur op Inhoudsfragment toont de interne kalenderrepresentatie voor het veld Datum en tijd. NPR-29531: Hotfix voor CQ-4269362
* De knoppen worden niet weergegeven wanneer u het tabblad met machtigingen opent in de implementatie van Coral2. Hotfix voor CQ-4269419

### Handel

* RestrictionViolationException, when running lazy content migration for e-commerce. NPR-29247: Hotfix voor CQ-4264383

### Beheer van inhoudsfragmenten

* Parseerfout bij het openen van een inhoudsfragment met dollartekens `($)` en open accolade `({)`. Hotfix voor CQ-4270266

### Ervaringsfragmenten

* Exporteren [!DNL Experience Manager] Ervaar fragmenten naar [!DNL Adobe Target]. Hotfix voor CQ-4265469
* De uitvoer van de Fragmenten van de ervaring naar doel ontbreekt met slimme beeld. Hotfix voor CQ-4269606

* De gebruiker raakt een doodlopende weg wanneer het proberen om de Fragmenten van de Ervaring door Onderzoek in kaartmening te bewegen. Hotfix voor CQ-4263848

### WCM - Pagina-editor

* Gespiegeld XSS (Cross-site scripting) bij gebruik van een ongeldige kiezer. Hotfix voor CQ-4270397

### Replicatie

* Door de gebruiker opgegeven gegevens worden niet gewist bij uitvoer in de `cq/replication/components/agent` resulteert in een opgeslagen XSS-kwetsbaarheid (Cross-site scripting). Hotfix voor CQ-4266263

### Workflow

* Het veld Kalenderkiezer van deelnemer in dialoogvenster is verbroken. NPR-29727: Hotfix voor CQ-4270423

### WCM - SPA Editor

* Toegelaten het halen van pre-teruggegeven inhoud van een ver eindpunt. Hotfix voor CQ-4270238
* Waarschuwingen in logbestanden bij het openen van een SPA Sjabloonpagina die op de server wordt weergegeven. Hotfix voor CQ-4270238

### WCM - MSM

* Upgrade uitvoeren naar [!DNL Experience Manager] 6.4.3 zorgt ervoor dat het lang duurt om beheer voor meerdere sites wordt geïmplementeerd. Hotfix voor CQ-4271410

### Integratie

* BrightEdge-referenties zijn mislukt vanwege een verbindingsfout. NPR-29168: Hotfix voor CQ-4265872

* Er wordt een uitzonderingsbericht weergegeven wanneer u de [!DNL Experience Manager] startconfiguratie. NPR-29176: Hotfix voor CQ-4265782/CQ-4266153

### Gebruikersinterface

* Toegevoegde ondersteuning voor het bijhouden van dynamische UI-statussen als aangepaste kenmerken bij het bijhouden van bepaalde gebeurtenissen in de API voor het bijhouden van stichtingen. Hotfix voor GRANITE-26283
* Kan de functie voor bijhouden niet instellen op de verzendknop. Hotfix voor GRANITE-26326
* De wizard kan de functie voor bijhouden niet instellen op de verzendknop. NPR-29995, NPR-30025: Hotfix voor CQ-4264289

### Gemeenschappen

* Kan geen nieuwe badges uitlijnen in de vervolgkeuzelijst op de pagina voor het lidprofiel. NPR-29381: Hotfix voor CQ-4267987
* Bezoekers en leden zonder moderatorrechten kunnen niet-goedgekeurde/hangende berichten zien door de URL te plakken. NPR-29724: Hotfix voor CQ-4271124, CQ-4271441
* Hoge responstijd tot 40-50 seconden wordt waargenomen bij het aanmelden bij de gebruiker voor de Gemeenschap. NPR-29677: Hotfix voor CQ-4269444

### Replicatie

* De component van de Agent van de replicatie is vatbaar voor een kwetsbaarheid die gevoelige informatie aan onbevoegde gebruikers openbaart. NPR-29611: Hotfix voor GRANITE-25070

* Sessieklek tijdens OAuth voor elke replicatie naar [!DNL Brand Portal]. NPR-30001: Hotfix voor GRANITE-26196

### Projecten

* Publiceren [!DNL Experience Manager Assets] van [!DNL Experience Manager] Map Auteur/content/dam/mac naar [!DNL Brand Portal] werkt niet. NPR-29819: Hotfix voor CQ-4271118

### Platform

* HtmlLibraryManager verwijdert alle inhoud van crx-quickstart bij cachevalidatie. NPR-29863: Hotfix voor GRANITE-26197

### Felix

* Gegevens over geheugengebruik worden niet weergegeven in de systeemconsole bij gebruik van Java11\. NPR-29669

### Forms

De belangrijkste markeringen voor [!DNL Experience Manager Forms] 6.5.1.0 zijn:

* Alleen OSGi: Een nieuw kenmerk toegevoegd `PAGECOUNT` in Output en Forms Service.

* Alleen OSGI: Ondersteuning ingeschakeld voor het maken van statische PDF-bestanden met behulp van Forms Service.
* Toegelaten toestemmingen op XMLForm.exe voor beheerder en wortelgebruikers.
* Ondersteuning ingeschakeld voor ADFS v3.0 for Dynamics on-premise integratie.

#### Forms-invoegtoepassing

**Backend-integratie**

* Fout bij het ophalen van de beveiligde Web Service Definition Language (WSDL). NPR-29944: Hotfix voor CQ-4270777
* Wanneer [!DNL Experience Manager Forms] wordt geïnstalleerd op IBM WebSphere en het maken van een formuliergegevensmodel op basis van SOAP mislukt. Hotfix voor CQ-4251134
* Ondersteuning ingeschakeld voor Active Directory Federation Services (ADFS) v3.0 voor Microsoft Dynamics on-premise integratie. Hotfix voor CQ-4270586
* Als de titel van een gegevensbron wordt gewijzigd, wordt de bijgewerkte titel niet weergegeven in het formuliergegevensmodel. Hotfix voor CQ-4265599
* Als de naam van een entiteit of kenmerk afbreekstreepjes of spaties bevat, worden dergelijke entiteiten en kenmerken niet door expressies geëvalueerd. Hotfix voor CQ-4225129

* Er wordt een onjuiste uitvoer waargenomen wanneer een dubbele punt aanwezig is in de primitieve uitvoer van de tekenreeks. Hotfix voor CQ-4260825

* Zelfs als er geen inhoud wordt verwacht van de REST API-uitvoer, genereert de aanroepbewerking van het formuliergegevensmodel een fout. Hotfix voor CQ-4268828

**Adaptieve Forms**

* Unable to add new instance in Adaptive Form Fragment during lazy loading. NPR-29818: Hotfix voor CQ-4269875
* Verify component registreert of toont geen fout voor Document van de malplaatjes van het Verslag. Hotfix voor CQ-4272999
* Toegevoegde ondersteuning voor het uitschakelen van de lay-outeditor voor Adaptive Forms. Hotfix voor CQ-4270810
* De stap Verifiëren voor Adaptive Forms in [!DNL Experience Manager] 6.5 Hotfix voor CQ-4269583

* Fout bij validatie van adaptieve formuliervelden [!DNL Adobe Sign]. Hotfix voor CQ-4269463
* Wanneer een [!DNL Experience Manager Forms] -instantie heeft meer dan 20 adaptieve formulierfragmenten en de naam van alle formulierfragmenten begint met dezelfde tekenreeks. De zoekopdracht retourneert alleen recente 20 gemaakte fragmenten. Hotfix voor CQ-4264414, CQ-4264914

* Prestatieproblemen wanneer de adaptieve Forms-toepassing wordt gebruikt met een grote dataset. . Hotfix voor CQ-4235310

* Wanneer betreden door anonieme rekening op een publicatie instantie, ontbreekt GuideRuntime manuscript om te laden. Hotfix voor CQ-4268679

**Forms - Interactieve communicatie**

* De interactieve Communicatie malplaatje maakt geen lijst van kopbal en footer componenten in toegestane componentenlijst. Hotfix voor CQ-4237895
* Wanneer u een interactieve sjabloon voor communicatie-afdrukken maakt die een afbeeldingsveld bevat, wordt de titel van het diagram ingesteld op leeg. Hotfix voor CQ-4264772
* De lijnkleur van een diagram wordt, wanneer deze wordt verwijderd, ingesteld op ongedefinieerd. Hotfix voor CQ-4264762
* Wijzigingen in de lay-outlaag die zijn aangebracht op documentfragment, verdwijnen bij het uitvoeren van de wijzigingen en blijven synchroon. Hotfix voor CQ-4266054
* Het formuliergegevensmodelelement in een documentfragment dat aan een tekstveld is gebonden, geeft geen overervingspictogram weer en staat binding toe. Hotfix voor CQ-4261089
* De printerkanaal-render-API heeft geen optie om gegevens als parameter door te geven in de API. Hotfix voor CQ-4263540
* De montages van de agent zijn niet zichtbaar aangezien Editable door de controledoos van de Agent wordt ongecontroleerd wanneer het bindingstype van het Fragment van de Tekst in niets/het ModelVoorwerp van Gegevens voor het gebied van het Koord/variabele wordt veranderd. Hotfix voor CQ-4261953
* Voor de voorlegging van de UI van de Agent, slaat het resulterende dossier van Webgegevens informatie voor erving-geannuleerde niet gebonden gebieden op. Hotfix voor CQ-4265621

**Forms - Workflow**

* Wanneer een formulier opnieuw wordt verzonden vanuit de Postvak UIT de app voor adaptieve formulieren, gaan er gegevens verloren. NPR-28345: Hotfix voor CQ-4260929
* Documenten worden niet gesloten tijdens het opslaan voor niet-variabele gevallen. Hotfix voor CQ-4269784
* De adaptieve Forms-app heeft de ondersteuning voor Microsoft Windows 8.1 ingetrokken. Hotfix voor CQ-4265274
* Als een afbeelding van meer dan 2 MB als een bijlage op veldniveau is gekoppeld aan een formulier in de Android-versie van [!DNL Experience Manager Forms] de app vastloopt. Hotfix voor CQ-4265578

* Toegelaten pre-populatieopties voor Interactieve Communicatie Kanaal van de Druk in Assign taak. Hotfix voor CQ-4265577
* De gebruikers kunnen geen gedeelde taak bekijken tot zij lid van de groep worden waaraan de taak wordt toegewezen. Hotfix voor CQ-4248733
* Het opslaan of verzenden van JEE-toepassingen in de app Adaptief formulier is geblokkeerd in Windows. Hotfix voor CQ-4268704
* Het formuliergegevensmodel dat is gekoppeld aan de variabele van het formuliergegevensmodel is niet zichtbaar. Hotfix voor CQ-4266554
* Geen ondersteuning voor de statusvariabele van het documentteken met variabele ondersteuning. Hotfix voor CQ-4266312
* Verzending vanuit werkruimte mislukt met een umlaut-teken. Hotfix voor CQ-4263172
* Als de workflow tijdens een upgrade wordt geopend voor bewerking, wordt in de gebruikersinterface van de controlemap (UI) een fout weergegeven in plaats van de naam van de workflow. Hotfix voor CQ-4238579

**Forms - Beheer**

* Wanneer een andere extensie dan xsd of schema.json wordt geüpload, vindt uploaden niet plaats en wordt er geen foutbericht gegenereerd. Hotfix voor CQ-4266716

**Forms - Correspondentenbeheer**

* [!DNL Experience Manager Forms] 6.5 Create Correspondence UI (CCR UI) kan geen correspondentie openen die is gemaakt met [!DNL Experience Manager Forms] 6.3. Hotfix voor CQ-4266392
* De functie Som in XDP werkt niet als het DDE gegevenstype van type aantal is. Hotfix voor CQ-4227403
* Letters voor de invalidatielogica voor de cache in het geheugen die moeten worden bijgewerkt, omdat de laatste gewijzigde tijd van een element niet wordt bijgewerkt wanneer een element wordt gepubliceerd. Hotfix voor CQ-4250465
* Kan documentfragment, DD &amp; letters niet publiceren. Hotfix voor CQ-4272893

#### Forms JEE-installatieprogramma

**PDF Generator**

* CAD-bestanden naar PDF-conversie mislukken bij 64-bits JDK. NPR-29924, NPR-29925: Hotfix voor CQ-4272113
* De naam van PhantomJS is vervangen door WebToPDF voor conversie van HTML naar PDF. NPR-29933: Hotfix voor CQ-4234545
* Er wordt een fout gegenereerd bij het converteren van het ZIP-bestand naar PDF. Hotfix voor CQ-4268628

**Forms - Designer**

* Wanneer een volledige toegankelijkheidscontrole wordt uitgevoerd op de statische PDF die wordt gemaakt met [!DNL Experience Manager Forms Designer], mislukt de controle Primaire taal omdat het taalkenmerk ontbreekt. Hotfix voor CQ-4272923, CQ-4271002

**Forms - Documentbeveiliging**

* Digital Signature with Hardware Security Module (HSM) werkt niet op OSGi Linux op Java 11 en Java 8\. NPR-29838: Hotfix voor CQ-4270441
* Digital Signature with Hardware Security Module (HSM) werkt niet op JEE Linux en op alle ondersteunde toepassingsservers, zoals JBoss en Websphere. NPR-29839: Hotfix voor CQ-4266721
* Wanneer de handtekeningen in een PDF worden gecontroleerd met behulp van PDF Advanced Electronic Signatures (PAdES), wordt InvalidOperationException gegenereerd. NPR-29842: Hotfix voor CQ-4244837
* Extra ondersteuning voor documentbeveiliging voor Office 2019\. Hotfix voor CQ-4254369, CQ-4259764

**Forms - Document Services**

* PDF kan niet worden geconverteerd naar PDF/A-1b met formulierveld, omdat dit geen weergavewoordenboek heeft. NPR-29940: Hotfix voor CQ-4269618

* OSGi: Kan het aantal pagina&#39;s dat tijdens de rendering wordt gegenereerd, niet bepalen. NPR-28922: Hotfix voor CQ-4270870
* Ondersteuning ingeschakeld voor Static PDF files using Forms Service in [!DNL Experience Manager Forms OSGi]. NPR-28572: Hotfix voor CQ-4270869
* Kan de machtigingen voor XMLForm.exe niet wijzigen. NPR-29828, NPR-29237: Hotfix voor Q-4267080
* De statische PDF die door [!DNL Experience Manager Forms] In de uitvoermodule van de server wordt het taalkenmerk/de taaltag niet gevuld met de taal van het gemaakte document. NPR-27332: Hotfix voor CQ-4271002

**Forms - Foundation JEE**

* Niet-beschikbare pdfg_srt in definitieve artefacten veroorzaakt het installatieprogramma om te ontbreken. NPR-29854: Hotfix voor CQ-4270137
* LCBackupMode.sh werkt niet. NPR-29840: Hotfix voor CQ-4269424
* De UDP havenverwijzing zou uit gebruikersinterface (UI) voor WebSphere moeten worden verwijderd. Hotfix voor CQ-4264782

### Inclusief functiepakketten

#### Activa - opgenomen

* Ondersteuning voor beheer van meerdere sites ingeschakeld voor [!DNL Experience Manager Assets]. Zie voor meer informatie [Elementen opnieuw gebruiken met MSM voor Experience Manager Assets](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/reuse-assets-using-msm.html). NPR-29199: Hotfix voor CQ-4259922

#### Sites - inbegrepen

* Exporteren [!DNL Experience Manager] Ervaar fragmenten naar [!DNL Adobe Target]. Zie voor meer informatie [De Experience Fragment Link Rewriter Provider - HTML](https://helpx.adobe.com/experience-manager/6-5/help/sites-developing/experience-fragments.html#TheExperienceFragmentLinkRewriterProviderHTML). Hotfix voor CQ-4265469

#### Forms - Document Services - inbegrepen

* Alleen OSGi: Een nieuw kenmerk PAGECOUNT toegevoegd in Output en Forms Service. NPR-28922: Hotfix voor CQ-4270870
* Alleen OSGi: Ondersteuning ingeschakeld voor het maken van statische PDF-bestanden met behulp van Forms Service. NPR-28572: Hotfix voor CQ-4270869
* Toegelaten toestemmingen op XMLForm.exe voor beheerder en wortelgebruikers. NPR-29237: Hotfix voor CQ-4267080

### OSGi-bundels en inhoudspakketten

De volgende tekstdocumenten maken een lijst van de bundels OSGi en de Pakketten van de Inhoud inbegrepen in [!DNL Experience Manager] 6.5.1.0.

Lijst van OSGi-bundels opgenomen in [!DNL Experience Manager] 6.5.1.0.

[Bestand ophalen](assets/6_5-bundle-list.txt)

Lijst met inhoudspakketten die zijn opgenomen in [!DNL Experience Manager] 6.5.1.0.

[Bestand ophalen](assets/6_5-content-package-list.txt)
