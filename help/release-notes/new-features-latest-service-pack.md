---
title: Nieuwe functies in [!DNL Experience Manager] 6.5 Service Pack 11
description: Nieuwe functies in [!DNL Experience Manager] 6.5 Service Pack 11
contentOwner: AK
mini-toc-levels: 1
exl-id: 32470e6e-8a66-4670-82da-2259f6e001c3
source-git-commit: 35260325b583bd047f22ffa88afb9469b2023e60
workflow-type: tm+mt
source-wordcount: '4330'
ht-degree: 0%

---

# Nieuwe functies in [!DNL Adobe Experience Manager] 6.5 Service Pack 11 {#aem-whats-new-service-pack}

<!-- TBD: Downsample this image. We do not need as big an image since customers don't use as big a screen to view. Also, having a 700+ KB decorative image is bad for page load time.
-->

![Wit-nieuw](assets/whatsnew.jpeg)

[!DNL Adobe Experience Manager] 6.5 De Pakken van de Dienst verstrekken nieuwe eigenschappen, klant-gevraagde verhogingen, en prestaties, stabiliteit, en veiligheidsverbeteringen op kwartaalintervallen. De beschikbaarheid op kwartaalbasis maakt het gemakkelijk om tot nieuwe eigenschappen en innovaties toegang te hebben en te nemen.

Dit artikel benadrukt de eigenschappen inbegrepen in het recentste Service Pack [de belangrijkste eigenschappen inbegrepen in vorige 6.5 de Pakken van de Dienst](#key-features-previous-service-packs)en de [zeer belangrijke versies sinds het laatste Service Pack](#key-releases-since-last-sp) vrijgeven.

## [!DNL Adobe Experience Manager Sites] {#aem-sites}

* U kunt sitemap automatisch genereren voor SEO-doeleinden met behulp van de [SEO-indexpakket](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/sites-seo-index-content-1.0.0.zip). Sitemaps, alternatieve URL&#39;s, robot meta-tags en meer worden ondersteund in de [!DNL Core Components].

* Ondersteuning voor meerdere velden toegevoegd voor tekstgegevenstype met meerdere regels.

* Verbetering om gebruikers bewust te maken van de asynchrone taak die momenteel op de achtergrond wordt uitgevoerd om te voorkomen dat ze meerdere asynchrone bewerkingen op hetzelfde pad activeren.

## [!DNL Adobe Experience Manager Assets] {#aem-assets}

* Dankzij de verbeteringen in de gebruikerservaring wordt het aantal elementen in een map weergegeven. Voor meer dan 1000 elementen in een map: [!DNL Assets] geeft 1000+ weer.

   ![Aantal elementen in een map](/help/assets/assets/browse-folder-number-of-assets.png)

* De volgende toegankelijkheidsverbeteringen zijn beschikbaar:

   * In de kaartweergave in het dialoogvenster [!DNL Assets] opslagplaats, bij gebruik `Tab` Als u de focus wilt verplaatsen naar het eerste item dat Snelle handelingen opent, wordt de naam van het item dat de focus heeft, bekendgemaakt door de schermlezer.
   * In [!DNL Dynamic Media] [!UICONTROL Viewer Preset Editor]Als Schaduwkleur en Randkleur niet aanwezig zijn, worden de invoer uitgeschakeld met de eigenschap disabled. Toetsenbordgebruikers kunnen de focus niet op de invoer instellen en schermlezers geven de status van het besturingselement niet aan als uitgeschakeld.
   * In [!DNL Dynamic Media], in de interface om een nieuw videocoderingsprofiel te maken, [!UICONTROL Smart Crop Ratio] Deze optie is gelabeld voor toegankelijkheid, zodat schermlezers de optie op de juiste wijze bekendmaken.

### [!DNL Dynamic Media] {#dynamic-media}

* U kunt nu [!DNL Dynamic Media] om Algemene Montages te vormen in plaats van het moeten door [!DNL Dynamic Media Classic] bureaubladtoepassing. Zie [Algemene instellingen van Dynamic Media configureren](/help/assets/dm-general-settings.md).

   ![Algemene DM-instellingen](/help/assets/assets-dm/dm-general-settings.png)

* U kunt nu [!DNL Dynamic Media] om Publish Opstelling te vormen in plaats van het moeten door [!DNL Dynamic Media Classic] bureaubladtoepassing. Zie [Dynamic Media-publicatie-instellingen configureren](/help/assets/dm-publish-settings.md).

   ![DM-publicatie-instellingen](/help/assets/assets-dm/dm-publish-setup.png)

## [!DNL Adobe Experience Manager Forms] {#aem-forms}

>[!NOTE]
>
>* [!DNL Experience Manager Forms] releases the add-on packages one week after the scheduled [!DNL Experience Manager] Service Pack release date.


## Belangrijke functies in vorige [!DNL Experience Manager] 6.5 Servicepacks {#key-features-previous-service-packs}

### [!DNL Experience Manager Sites] {#aem-sites-previous-service-packs}

#### Functies die zijn opgenomen in AEM 6.5.10.0-release {#features-sites-65100}

* **Enhanced [!DNL Content Fragment] Models and Editor**: You can now create complex and custom models for structured content using nested [!DNL Content Fragment] models. Inhoudsstructuren worden gemoduleerd in basiselementen die zijn gemodelleerd als subfragmenten. Higher-level fragments reference these sub-fragments. More data type enhancements such as advanced validation rules further enhance the flexibility of content modeling with [!DNL Content Fragments]. De [!DNL Experience Manager] [!DNL Content Fragment] de redacteur steunt genestelde fragmentstructuren in een gemeenschappelijke redacteurszitting, met verhogingen zoals de mening van de boomstructuur en van labels voorzien broodkruimelnavigatie door fragmenthiërarchieën.

* **GraphQL API voor[!DNL Content Fragments]**: De nieuwe GraphQL API is de standaardmethode om gestructureerde inhoud in formaat te leveren JSON. Met GraphQL-query&#39;s kunnen clients alleen de relevante inhoudsitems aanvragen om een ervaring weer te geven. Een dergelijke selectie voorkomt overlevering van inhoud (mogelijkheid met HTTP REST API&#39;s) waarvoor inhoud moet worden geparseerd op de client. GraphQL-schema&#39;s zijn afgeleid van [!DNL Content Fragment] modellen en API-reacties worden gemaakt in JSON-indeling. In [!DNL Experience Manager] als [!DNL Cloud Service], [GraphQL-query&#39;s blijven bestaan](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/admin/graphql-api-content-fragments.html#persisted-queries-caching) en verzoeken om cachevriendelijke GET verwerken. Het is nog niet mogelijk in [!DNL Experience Manager] 6.5

* **Hiërarchiebeheer en voorvertoning in de toekomst**: Gebruikers hebben nu een interface voor toegang tot de inhoudstructuren van hun [!DNL Experience Manager] wordt gestart, inclusief de mogelijkheid om pagina&#39;s toe te voegen en te verwijderen bij het starten. Deze functie verbetert de flexibiliteit van [!DNL Experience Manager] wordt gestart bij de versie van de auteursinhoud die is bedoeld voor toekomstig publiceren. [Time-warp feature](/help/sites-authoring/working-with-page-versions.md#timewarp) lets users preview launches as future content states.

* [!DNL Experience Manager] geeft rechtstreeks een lijst weer van alle inhoudsmodellen onder een map zonder dat de auteurs van de inhoud door de bestandsstructuur hoeven te navigeren. De functionaliteit vereist nu minder klikken en verbetert de efficiëntie van het ontwerpen.

* Pathfield in [!DNL Sites] de redacteur staat auteurs toe om activa van te slepen [!DNL Content Finder].

* Platform biedt enkele toegankelijkheidsverbeteringen. Zie [Platform-updates](/help/release-notes/sp-release-notes.md#platform-65100).

#### Mogelijkheid om verwijderde pagina&#39;s en boomstructuur te herstellen (6.5.9.0) {#ability-to-restore-pages-tree}

U kunt nu de verwijderde pagina&#39;s en de volledige structuurweergave herstellen op een [!DNL Experience Manager Sites] pagina.

#### Live Copy-pagina&#39;s die beschikbaar zijn voor rollout (6.5.8.0) sorteren {#sort-livecopy-pages}

U kunt de pagina&#39;s van Live Copy die beschikbaar zijn voor rollout nu sorteren met de opdracht [!UICONTROL Name], [!UICONTROL Last modified date], en [!UICONTROL Last rollout date] eigenschappen. De [!UICONTROL Last rollout date] voor een pagina is een nieuwe eigenschap die in deze release is geïntroduceerd.

#### Beschikbaarheid van paginabewegingen en MSM-rollouts als asynchrone bewerkingen (6.5.7.0) {#page-moves-msm-asynchronous}

U kunt nu de paginabewegingen en MSM-rollouts uitvoeren als asynchrone bewerkingen om het effect ervan op de prestaties bij uitvoering te beperken. U kunt de bewerkingen plannen voor directe of latere uitvoering. De status van bijbehorende taken en processtappen wordt weergegeven in een console, die nuttig is voor het controleren van grootschalige MSM-rollouts.

#### Beschikbaarheid van de bewerking Pagina verplaatsen in de asynchrone modus (6.5.6.0) {#page-move-asynchronous}

De bewerking Pagina verplaatsen is nu beschikbaar in de asynchrone modus. U kunt de bewerking Pagina verplaatsen niet alleen direct uitvoeren, maar ook later plannen.

#### Verbeteringen van de toegankelijkheid (6.5.5.0) {#accessibility-sites}

* Verbeterde foutrapportage door tekstgegevens toe te voegen.

* Verbeterde focus van de gebruikersinterface tijdens toetsenbordnavigatie.

* Verbeterde contrastverhouding voor verschillende gebruikersinterface-elementen.

* Improved consistency of alt attributes for page images.

* Improved consistency of Accessible Rich Internet Applications (ARIA) labels.

* Verbeterde NVDA-mogelijkheden (Non-Visual Desktop Access).

* Verbeterde ondersteuning voor schermlezers.

#### Other key enhancements (6.5.5.0) {#other-enhancements-sites}

* Anonymous access to CRXDE Lite is disallowed to enhance security. Instead, the users are directed to the login screen. Zie [Ontwikkelen met CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md).

* Wanneer u een paginastructuur kopieert of plakt, kunt u nu de basispagina plakken of de basispagina plakken met de subpagina&#39;s van de structuur.

* [!DNL Adobe Experience Manager Experience Fragments] exported to [!DNL Adobe Target] workspaces now appear as unique offer types and offer sources in [!DNL Target].

* Beheer van meerdere sites - De trigger Publiceren verwijdert nu een component van de gepubliceerde pagina als een component van de bronpagina wordt verwijderd.

* Multi Site Manager - wanneer de naam van een lokale component in een [!UICONTROL Live Copy] is identiek aan de naam van een component in de blauwdruk en de component wordt opgerold uit de blauwdruk, dan de termijn `_msm_moved` wordt nu toegevoegd aan de naam van de lokale component.

#### Stijlsysteemverbeteringen (6.5.4.0) {#style-system-enhancements}

U kunt nu stijlen selecteren in het dialoogvenster met het verbeterde stijlsysteem.

#### Prestatieverbeteringen op verschillende gebieden (6.5.4.0) {#performance-improvements}

* Verminderde tijd om ContextHub binnen een plaats te laden en te initialiseren (`contexthub.kernel.js`). Hierdoor worden pagina&#39;s tijdens een bezoek aan de site sneller geladen.

* De tijd die nodig is om een pagina na het slepen te vernieuwen, is verkort [!DNL Experience Fragments] tot [!DNL Sites] Pagina-editor.

* De laadtijd voor vermeldingen op een [!DNL Sites] pagina met meer dan 200 live kopieën in **[!UICONTROL Live Copy Overview]**.

* Verbeterde verwerking van onvolledige of ongeldige URL&#39;s. Dergelijke URL&#39;s kunnen de Sjablooneditor vertragen.

### [!DNL Adobe Experience Manager Assets] {#aem-assets-previous-service-packs}

#### Functies die zijn opgenomen in AEM 6.5.10.0-release {#features-assets-65100}

* [!DNL Experience Manager] breidt de Connected Assets-functionaliteit uit tot het gebruik van [!DNL Dynamic Media] afbeeldingen in de toepasselijke kerncomponenten. Zie [Aangesloten elementen gebruiken](/help/assets/use-assets-across-connected-assets-instances.md).

* Bij het delen van afzonderlijke elementen en verzamelingen als een koppeling (met [!UICONTROL Link Sharing] ), kunnen gebruikers kiezen of de ontvanger de oorspronkelijke elementen of hun uitvoeringen of beide mag downloaden. Zie [Elementen delen via koppeling](/help/assets/link-sharing.md).

   ![optie om alleen oorspronkelijke elementen, alleen de uitvoeringen of beide te downloaden](/help/release-notes/assets/share-assets-as-link.png)

* Wanneer gebruikers elementen downloaden die met hen als verbinding worden gedeeld, kunnen zij verkiezen om de originele activa, de vertoningen, of allebei te downloaden.

* **Gegenereerde subactiva beperken**: Beheerders kunnen het aantal subelementen beperken dat [!DNL Experience Manager] wordt gegenereerd voor samengestelde elementen zoals PDF-, PowerPoint-, InDesign- en toetsenbordbestanden.

   ![het genereren van subactiva beperken](/help/assets/assets/sub-asset-limit.png)

* Een nieuwe [!DNL Camera Raw] -pakket beschikbaar is dat ondersteuning biedt voor [!DNL Adobe Camera Raw] v10.4 Zie [afbeeldingen verwerken met [!DNL Camera Raw]](/help/assets/camera-raw.md).

#### Eerdere versies {#previous-releases-assets}

* Bijgewerkt aan de naamgeving van Chinese landinstellingen en regio&#39;s met betrekking tot Hongkong, Macau en Taiwan, om deze in overeenstemming te brengen met de sociale en politieke standpunten van China (6.5.9.0).

* Er is een optionele configuratie geïntroduceerd om de casus in de e-mailid&#39;s in de ACS API-reactie te wijzigen van [!DNL Adobe Experience Manager] (6.5.9.0).

   ![configuratie voor het wijzigen van e-mailadressen in kleine letters in ACS-reacties van [!DNL Experience Manager]](assets/email-lowcase-config.png)

* Het contrast van tekst en pictogrammen tegen de achtergrond wordt verbeterd voor verschillende functies. Deze implementatie van de richtlijnen van de Web Content Accessibility Guidelines (WCAG) maakt [!DNL Assets] toegankelijker zijn voor gebruikers met een beperkt gezichtsvermogen en een beperkte kleurperceptie. Zie [toegankelijkheidsverbeteringen in [!DNL Assets]](sp-release-notes.md#assets-accessibility-6590) (6.5.9.0).
* When using [Connected Assets functionality](/help/assets/use-assets-across-connected-assets-instances.md), you can now view a list of all the [!DNL Sites] pages that use the asset. Deze verwijzingen naar een actief zijn beschikbaar in het [!UICONTROL Properties] pagina. Op deze manier kunnen beheerders, marketers en bibliothecarissen een volledig overzicht van het gebruik van bedrijfsmiddelen krijgen, waardoor ze het bedrijfsmerk beter kunnen bijhouden, beheren en de consistentie van merken kunnen verbeteren (6.5.8.0).

* When deleting an asset that is referenced in a web page, [!DNL Experience Manager] displays a warning. U kunt afdwingen dat een element waarnaar wordt verwezen wordt verwijderd, of de referenties controleren en wijzigen die worden weergegeven in het dialoogvenster [!DNL Properties] pagina van het element. Als u op de referenties klikt, worden de lokale en externe [!DNL Sites] pagina&#39;s (6.5.8.0).

* [!DNL Assets] en [!DNL Dynamic Media] bieden meerdere toegankelijkheidsverbeteringen. De verbeteringen hebben betrekking op toetsenbordnavigatie, gebruik van schermlezers en vergelijkbare verbeteringen om het gebruik van ondersteunende hulpmiddelen (AT) mogelijk te maken. Zie [[!DNL Assets] verbeteringen](/help/release-notes/sp-release-notes.md#assets-6570) en [[!DNL Dynamic Media] verbeteringen](/help/release-notes/sp-release-notes.md#dynamic-media-6570) (6.5.7.0)

* Gebruikers kunnen digitale elementen sorteren in de Kaart- en kolomweergave (6.5.7.0).

#### Toegankelijkheidsverbeteringen (6.5.6.0) {#accessibility-assets-6560}

* **Verbeterde focus van de gebruikersinterface tijdens toetsenbordnavigatie**, bijvoorbeeld:

   * `x` pictogram in [!UICONTROL Version Preview] dialoogvenster van een element in [!UICONTROL Timeline].

   * Opties voor een uitvoerbare gebruikersinterface.

   * Veld e-mailen op [!UICONTROL Share Link] en veld om gesloten gebruikersgroep toe te voegen in [!UICONTROL Permission] tabblad van map [!UICONTROL Properties].

* **Verbeterde functionaliteit met toetsenbordtoetsen**

   Gebruikers kunnen toetsenbordtoetsen gebruiken om besturingselementen te slepen in de formuliereditor voor metagegevensschema&#39;s in de bladermodus van schermlezers.

* **Verbeterde bruikbaarheid voor schermlezers**, vanwege het volgende:

   * Schermlezers geven het doel van video- en audiospelers aan.

   * Schermlezers geven aan wat het doel is van de gebruikersinterfaceopties om de geselecteerde tags te verwijderen met behulp van [!UICONTROL Tags selection dialog] op actief [!UICONTROL Properties].

   * Schermlezers kondigen de rijkoppen en rij-items van tabellen aan, zodat gebruikers weten welke items tot dezelfde rij behoren.

   * Beschrijvende en betekenisvolle paginatitel van zoekpagina.

   * Schermlezers geven de opties in het deelvenster met zoekfilters aan als uitbreidbare accordeons.

#### Andere verbeteringen in [!DNL Assets] (6.5.6.0) {#other-enhancements-assets-6560}

* Gebruikersgroepen die zijn gekoppeld aan mappen (privégroepen en niet-privégroepen) worden nu verwijderd uit de opslagplaats op [verwijderen van die mappen](/help/assets/private-folder.md#delete-private-folder). De bestaande overbodige, zwevende, ongebruikte en automatisch gegenereerde gebruikersgroepen kunnen echter met JMX uit de opslagplaats worden verwijderd.

#### Verbeterde toegankelijkheid in [!DNL Assets] (6.5.5.0) {#assets-accessibility}

[!DNL Experience Manager Assets] is nu toegankelijker in overeenstemming met de Web Content Accessibility Guidelines (WCAG). De toegankelijkheid is verbeterd dankzij de volgende verbeteringen:

* Veel gebruikersinterface-elementen, besturingselementen, pagina&#39;s en dialoogvensters zijn schermlezervriendelijk.

* Many user interface elements, controls, and input form fields are accessible using keyboard.

* Color and contrast of some user interface elements are updated so that users with limited vision or users without perception of color can distinguish these user interface elements. De kleur van sterrenclassificatiepictogrammen (bijvoorbeeld in [!UICONTROL Rating] deel van [!UICONTROL Advanced] tab in element [!UICONTROL Properties] of in de kaartweergave) wordt gewijzigd voor het juiste contrast.

   ![Rating icons with improved contrast](assets/star-rating-icons.png)

#### Uitgebreide afhandeling van uitzonderingen (6.5.5.0) {#exception-handling}

[!DNL Assets] de stroom van de gebruikersinterface heeft betere uitzonderingsbehandeling. Als een element geen type heeft voor de dimensie, wordt de waargenomen uitzondering opgenomen in de logbestanden.

#### Configureren [!DNL Experience Manager Assets] with [!DNL Brand Portal] (6.5.4.0) {#configure-assets-bp}

Het machtigingskanaal tussen [!DNL Experience Manager Assets] en [!DNL Brand Portal] is gewijzigd. Eerder, [!DNL Brand Portal] werd gevormd in Klassieke UI via de Gateway van de Oudheid OAuth, die de het symbolenuitwisseling van JWT gebruikt om een token van de Toegang te verkrijgen IMS voor vergunning. [!DNL Experience Manager Assets] is nu geconfigureerd met [!DNL Brand Portal] doorheen [!DNL Adobe I/O], die een IMS-token aanschaft voor goedkeuring van uw [!DNL Brand Portal] huurder.

The steps to configure [!DNL Experience Manager Assets] with [!DNL Brand Portal] are different depending on your [!DNL Experience Manager] version, and whether you are configuring for the first time, or upgrading the existing configurations. Zie [Experience Manager Assets configureren met Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/configure-aem-assets-with-brand-portal.html) voor meer informatie.

#### Toegankelijkheidsverbeteringen (6.5.4.0) {#accessibility-enhancements-6540}

[!DNL Experience Manager Assets] bevat de volgende toegankelijkheidsverbeteringen:

* Met de pijltoetsen op het toetsenbord kunt u gebieden binnen ingezoomde afbeeldingen verplaatsen en pannen. Zie voor meer informatie [elementen alleen met toetsenbordtoetsen voorvertonen](../assets/manage-assets.md#previewing-assets).

* De selectievakjes voor gemengde status (waarin de selectievakjes voor het eerste niveau niet zijn geselecteerd en zijn doorgehaald) in het deelvenster Filters zijn leesbaar voor schermlezers, tenzij u alle geneste selectievakjes selecteert.

* Er zijn beperkingen in de datum- en tijdnotatie opgenomen in veldlabels van datumvelden, zodat gebruikers de datum in de juiste notatie kunnen invoeren met het toetsenbord.
Bijvoorbeeld, `On Time (MM-DD-YYYY HH:mm)`. Hier is MM maand in het formaat van twee cijfers, YYYY is jaar, DD is dag in het formaat van twee cijfers, HH is uur in 24-uurs militair formaat, en mm is minuut.

* Schermlezers kondigen de optie aan om geselecteerde tags te verwijderen (`X` ) en het nummer van de geselecteerde tags.

#### Kolom Sorteerbaar voor aanmaakdatum van elementen in lijstweergave (6.5.3.0) {#sortable-date-created-column}

Een nieuwe sorteerbare kolom voor de aanmaakdatum van elementen wordt toegevoegd in de DAM-lijstweergave en in de resultaten van zoekopdrachten naar elementen in de lijstweergave.

![Kolom Sorteerbaar voor datum die is gemaakt](assets/asset-created-date.png)

#### Visueel zoeken naar [!DNL Adobe Experience Manager Assets] (6.5.2.0) {#visual-search}

[!DNL Assets] gebruikers kunnen visueel vergelijkbare afbeeldingen zoeken. Experience Manager geeft de slimme getagde afbeeldingen uit de DAM-opslagplaats weer die lijken op een door de gebruiker geselecteerde afbeelding. Zie [Visueel zoeken](../assets/search-assets.md).

###  Dynamic Media  {#dynamic-media-previous-service-packs}

* Veel toegankelijkheidsverbeteringen zijn uitgevoerd in [!DNL Dynamic Media] zodat een schermlezer een geschiktere en bruikbaardere beschrijving van de handeling of gebruikersinterface kan geven. Zie [[!DNL Dynamic Media] updates](/help/release-notes/sp-release-notes.md#dynamic-media-65100) (6.5.10.0).

* [[!DNL Dynamic Media] is toegankelijker](sp-release-notes.md#assets-accessibility-6590) in termen van:

   * Gebruiksgemak met toetsenbordtoetsen.
   * Contrast (met achtergrond) van tekst, plaatsaanduidingstekst en besturingselementen in verschillende editors.
   * Toegankelijkheid en gesproken tekst voor schermlezers.

* Efficiënt beelden van de beste kwaliteit leveren op apparaten met displays met hoge resolutie en beperkte netwerkbandbreedte, met Smart Imaging DPR (Device Pixel Ratio) en optimalisatie van de netwerkbandbreedte. Zie [Veelgestelde vragen over slimme beeldverwerking](/help/assets/imaging-faq.md) (6.5.9.0).

* [!DNL Dynamic Media] levering (`fmt` URL (optie) ondersteunt nu AVIF-afbeeldingsindeling van de volgende generatie (AV1-afbeeldingsindeling). Zie voor meer informatie en een tijdlijn [fmt voor API voor beeldweergave en rendering](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-is-http-fmt.html) (6.5.9.0).

#### Ondersteuning voor 3D-elementen in [!DNL Dynamic Media] (6.5.5.0) {#support-for-3d}

Ondersteuning voor 3D-afbeeldingen in [!DNL Dynamic Media] kunnen klanten 3D-inhoud publiceren en toevoegen aan webpagina&#39;s en toepassingen. De steun omvat:

* Publiceer algemene indelingen voor 3D-elementen en genereren een middel-URL die kan worden gebruikt in webpagina&#39;s en andere toepassingen.

* Een 3D-webviewer, aangedreven door [!DNL Adobe Dimension], om de gepubliceerde 3D-elementen interactief te bekijken.

* Algemene 3D-elementen publiceren en weergeven op [!DNL Experience Manager Sites] pagina&#39;s met de [!DNL Sites] WCM-component.

#### CDN-inhoud in cache ongeldig maken (6.5.6.0) {#invalidate-cdn-cached-content}

U kunt nu de opdracht [!DNL Dynamic Media] gebruikersinterface om inhoud in cache van CDN (Content Delivery Network) ongeldig te maken. Hierdoor zijn de bijgewerkte elementen direct beschikbaar in plaats van te wachten tot de cache verloopt. U kunt CDN ongeldig maken door:

* Een CDN-validatiesjabloon maken: Elementen en aan een sjabloon gekoppelde URL&#39;s selecteren

* Elementen en bijbehorende voorinstellingen selecteren via de elementkiezer

* URL&#39;s van volledige middelen toevoegen

#### Selectieve publicatie van elementen naar [!DNL Experience Manager] en [!DNL Dynamic Media] (6.5.6.0) {#selective-publishing}

U kunt nu kiezen of u elementen selectief wilt publiceren of de publicatie ervan ongedaan wilt maken [!DNL Experience Manager] of [!DNL Dynamic Media] gebruiken [!UICONTROL Quick Publish] of [!UICONTROL Manage Publication] wizard. U kunt ook de `Publish` of `Unpublish` op mapniveau.

#### Smart Imaging voor Dynamic Media {#smart-imaging}

Slimme beeldverwerking gebruikt de unieke weergavekenmerken van elke gebruiker om automatisch de juiste afbeeldingen te leveren die zijn geoptimaliseerd voor zijn of haar ervaring, wat resulteert in betere prestaties en betrokkenheid. Slimme beeldverwerking werkt met bestaande voorinstellingen voor afbeeldingen en maakt gebruik van intelligentie tijdens de laatste milliseconde van levering om de bestandsgrootte van de afbeelding verder te beperken op basis van de snelheid van de browser of netwerkverbinding. Zie [Slimme afbeeldingen](../assets/imaging-faq.md).

#### Slim uitsnijden in videoprofielen voor Dynamic Media (6.5.3.0) {#smart-crop-video}

Slim uitsnijden voor video - een optionele functie die beschikbaar is in videoprofielen - gebruikt Adobe Sensei om het brandpunt automatisch te detecteren en uit te snijden in adaptieve video of progressieve video, ongeacht de grootte. Zie [informatie over slim uitsnijden in videoprofielen](../assets/video-profiles.md).

### Experience Manager Forms {#aem-forms-previous-service-packs}

#### Functies die zijn opgenomen in AEM 6.5.10.0-release {#features-forms-65100}

>[!NOTE]
>
>Het invoegpakket van [!DNL Experience Manager Forms] een week na de geplande [!DNL Experience Manager] Service Pack-release.

* U kunt de dienst van de Automatede form conversion nu gebruiken aan [PDF forms converteren in het Frans, Duits, Spaans, Italiaans en Portugees](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html#language-specific-meta-model) aan adaptieve formulieren.

* **Foutberichten in de browser Eigenschappen**: Foutberichten toegevoegd voor elke eigenschap in de browser Adaptive Forms Properties. Met deze berichten kunt u de toegestane waarden voor een veld beter begrijpen.

* **Ondersteuning voor het gebruik van de letterlijke optie voor het instellen van de waarde voor een JSON-typevariabele**: U kunt letterlijke optie gebruiken om waarde voor een JSON typevariabele in de vastgestelde veranderlijke stap van een AEM Werkstroom te plaatsen. The literal option allows you to specify a JSON in the form of a string.

* [Updates van Platform](../forms/using/aem-forms-jee-supported-platforms.md): [!DNL Adobe Experience Manager Forms] op JEE heeft ondersteuning toegevoegd voor de volgende platforms:
   * [!DNL Adobe Acrobat 2020]
   * [!DNL Ubuntu 20.04]
   * [!DNL Open Office 4.1.10]
   * [!DNL Microsoft Office 2019]
   * [!DNL Microsoft Windows Server 2019]
   * [!DNL RHEL8]

* Added support for `GuideBridge#getGuidePath` API in [!DNL AEM Forms].

#### Ondersteuning voor [!DNL Azul Zulu OpenJDK] (6.5.9.0) {#support-azul-zulu}

U kunt nu toepassingen ontwikkelen en gebruiken met [!DNL Azul Zulu] builds van [!DNL OpenJDK] for [!DNL Experience Manager Forms] op OSGi-implementaties. Zie voor meer informatie [Opmerkingen bij de release van Experience Manager 6.5 Service Pack 9](sp-release-notes.md) en [Technische vereisten](../sites-deploying/technical-requirements.md).

#### De mogelijkheid om een e-mailbericht naar een groep te verzenden met [!UICONTROL Assign Task] (6.5.9.0) {#group-notification-email}

U kunt nu een e-mailbericht naar een groep e-mailadres verzenden met de workflowstap Taak toewijzen.

#### Capaciteit om een Interactief Communicatie ontwerp terug te winnen na het wijzigen van de bron Interactieve Mededeling (6.5.9.0) {#retrieve-draft-after-source-modifications}

U kunt nu een interactieve communicatie ophalen die als concept is opgeslagen nadat u de bron Interactieve communicatie hebt gewijzigd.

#### Set custom domain name for loading, rendering, and validating the reCAPTCHA service (6.5.9.0) {#set-custom-domain-name-recaptcha}

reCAPTCHA-service gebruikt `https://www.recaptcha.net/` als het standaarddomein. U kunt nu de instellingen wijzigen die u wilt instellen `https://www.google.com/` of een aangepaste domeinnaam om de reCAPTCHA-service te laden, renderen en te valideren.

#### Verbeterde invoergegevens voor [!UICONTROL Invoke Form Data Model Service] workflowstap (6.5.9.0) {#input-data-enhancements-fdm}

Als u een formuliergegevensmodel en een service selecteert in [!UICONTROL Invoke Form Data Model Service] workflowstap, geeft u serviceargumenten op voor invoergegevens.

Als u [!UICONTROL Relative to Payload] als u een bestand als een serviceargument wilt toevoegen, kunt u nu het mappad opgeven dat het bestand bevat in plaats van de feitelijke bestandsnaam. Als u de mapnaam definieert in plaats van de naam van de bestandsbijlage, kunt u workflowmodellen opnieuw gebruiken. U beperkt het workflowmodel niet tot één bestandsnaam voor bijlagen.

#### Mogelijkheid om meerdere master pagina&#39;s te gebruiken in een sjabloon Document of Record (6.5.9.0) {#use-multiple-master-pages-dor-template}

U kunt nu meerdere master pagina&#39;s gebruiken in een document met een recordsjabloon. Hierdoor kunt u nu verschillende koptekst-, voettekst-, lettertypen- en logogegevens op de titelpagina en andere pagina&#39;s van de sjabloon plaatsen.

#### Pagina-einden in Document of Record (6.5.9.0) worden ondersteund {#support-page-breaks-dor}

U kunt nu pagina-einden toevoegen aan een Document of Record. Als een deelvenster pagina&#39;s afbreekt, kunt u daarom een pagina-einde toevoegen om het deelvenster te verplaatsen naar een nieuwe pagina in een document met records.

#### CAPTCHA-component weergeven of verbergen in een adaptieve vorm op basis van regels (6.5.8.0) {#show-hide-captcha}

U kunt CAPTCHA nu valideren bij het verzenden van het aangepaste formulier of bij actie van de gebruiker. U kunt ook voorwaarden toevoegen om CAPTCHA te valideren bij een gebruikersactie en de component CAPTCHA weergeven of verbergen in een adaptief formulier op basis van regels.

#### Aangepaste CAPTCHA-services toevoegen (6.5.8.0) {#add-custom-captcha-services}

[!DNL Experience Manager Forms] biedt in de box-ondersteuning voor het gebruik van Google reCAPTCHA (een aparte licentie voor Google reCAPTCHA API&#39;s is vereist) als validatieservice CAPTCHA. U kunt ook een aangepaste CAPTCHA-service gebruiken om CAPTCHA&#39;s te valideren.

#### Andere verbeteringen (6.5.8.0) {#other-enhancements-forms-6580}

* Verbeterde toegankelijkheid van de [!DNL Experience Manager Forms] De component Date Picker.

* Extra ondersteuning voor het genereren van een interactieve communicatie in PCL-indeling met de PrintChannel-API.

* Wanneer u een PDFG-conversie uitvoert, kunt u de opdracht [!DNL Experience Manager Forms] registerwijzigingen voor het genereren van aangepaste bladwijzers.

#### Prestatieverbeteringen (6.5.7.0) {#performance-improvements-forms}

[!DNL Experience Manager] 6.5 Service Pack 7 Forms verbetert de prestaties voor:

* De veldwaarden op de server valideren wanneer u een adaptief formulier verzendt.

* Een PDF-formulier converteren naar een adaptief formulier met de opdracht [!DNL Automated Forms Conversion service].

#### Ondersteuning voor Microsoft SQL Server 2016 Altijd op beschikbaarheidsgroepen voor Hoge Beschikbaarheid (6.5.7.0) {#always-on-availability-groups}

[!DNL Experience Manager Forms] now supports [!DNL Microsoft] SQL Server 2016 altijd op beschikbaarheidsgroepen voor Hoge Beschikbaarheid voor plaatsingen OSGi.

#### Formuliergegevensmodel HTTP-clientconfiguratie voor optimale prestaties (6.5.7.0) {#fdm-http-client-config}

[!DNL Experience Manager Forms] het model van vormgegevens wanneer het integreren met RESTful Webdiensten als gegevensbron omvat nu de cliëntconfiguraties van HTTP voor prestatiesoptimalisering. Zie [Gegevensbronnen configureren](../../help/forms/using/configure-data-sources.md#fdm-http-client-configuration).

#### Beschikbaarheid van de Optie van het Terugstellen voor elke component in de wijze van de Lay-out (6.5.7.0) {#reset-option-layout-mode}

U kunt nu de resetoptie voor elke component in de modus Indeling van een adaptief formulier gebruiken. Wanneer u een lay-out met meerdere kolommen definieert voor een deelvenster, kunt u deze functie gebruiken om afzonderlijke componenten in het deelvenster opnieuw in te stellen. Zie [De lay-outmodus gebruiken om de grootte van componenten te wijzigen](../../help/forms/using/resize-using-layout-mode.md#resize-components).

#### Een adaptief formulier vooraf invullen op de client (6.5.6.0) {#prefill-merge-data-at-client}

Wanneer u een adaptief formulier vooraf instelt, wordt [!DNL Experience Manager Forms] gegevens worden samengevoegd met een adaptief formulier en het ingevulde formulier wordt aan u geleverd. De handeling voor het samenvoegen van gegevens vindt standaard plaats op de server.
U kunt nu de [!DNL Experience Manager Forms] server naar [De handeling voor het samenvoegen van gegevens op de client uitvoeren](../../help/forms/using/prepopulate-adaptive-form-fields.md) in plaats van de server. Hierdoor wordt de tijd die nodig is om adaptieve formulieren vooraf in te vullen en weer te geven, aanzienlijk verkort.

#### Integratie van formuliergegevensmodellen met RESTful-API&#39;s op een server met 2-wegs SSL-implementatie (6.5.6.0) {#fdm-integration-rest-apis-two-way-ssl}

[!DNL Experience Manager Forms] formuliergegevensmodel kan nu [integreren met RESTful-API&#39;s op een server waarop een bidirectionele SSL is geïmplementeerd](../../help/forms/using/configure-data-sources.md).

#### Extra ondersteuning voor [!DNL Adobe Sign] Tekstlabels in de service Automatede form conversion (6.5.6.0) {#sign-integration-acroform-afcs}

Als een AcroForm-formulier [!DNL Adobe Sign] Tekstlabels, deze velden worden nu herkend en weergegeven als [!DNL Adobe Sign] velden in het adaptieve formulier geconverteerd met [!DNL Automated Forms Conversion service]. Een ondertekenaar kan dergelijke velden invullen terwijl hij het adaptieve formulier ondertekent.

#### Ondersteuning voor de omzetting van gekleurde PDF forms in adaptieve formulieren (6.5.6.0) {#colored-PDF-forms}

U kunt [!DNL Automated Forms Conversion service] om gekleurde PDF forms om te zetten in adaptieve formulieren.

#### Steun voor SMB 2 en SMB 3 protocollen (6.5.6.0) {#smb-support}

[!DNL Experience Manager Forms] steunt nu SMB 2 en SMB 3 protocollen.

#### Verbeterd in cache plaatsen voor vertaalde adaptieve formulierpagina&#39;s (6.5.6.0) {#enhanced-caching-translated-adaptive-forms}

U kunt nu [locale as a selector in the adaptive form URL in plaats van an argument in adaptive form URL](../../help/forms/using/supporting-new-language-localization.md). Hiermee kunt u vertaalde adaptieve formulieren in cache plaatsen op [!DNL Experience Manager Dispatcher]. Het in cache plaatsen van vertaald adaptief formulier was niet mogelijk in eerdere versies. Zie voor meer informatie over het configureren van caching voor het gebruik van landinstellingen als kiezer in de URL van het aangepaste formulier [Adaptieve formuliercache configureren bij verzender](../../help/forms/using/configure-adaptive-forms-cache.md).

#### Uitvoer van formuliergegevensmodelservice opslaan naar een variabele (6.5.6.0) {#save-fdm-service-to-variable}

Met het formuliergegevensmodel kunt u de uitvoer van een service van een formuliergegevensmodel opslaan in een variabele. [!DNL Experience Manager Forms] Hiermee wordt nu automatisch het type van de service van het formuliergegevensmodel toegewezen aan het type variabele.

#### Meerdere bestanden koppelen voor component Bestandsbijlage (6.5.6.0) {#attach-multiple-files}

U kunt nu [meerdere bestanden bijvoegen](../../help/forms/using/introduction-forms-authoring.md) aan de [!UICONTROL File Attachment] component van adaptieve formulieren.

#### De Adobe Experience Manager Inbox-kolommen aanpassen (6.5.5.0) {#customize-aem-inbox-columns}

U kunt een [!DNL Experience Manager] InBox om de standaardtitel van een kolom te wijzigen, de positie van een kolom opnieuw te ordenen en extra kolommen weer te geven die op de gegevens van een werkstroom worden gebaseerd. Leden van `administrators` of `workflow-administrators` kunt u de kolommen aanpassen. For more information, see [Admin Control](../sites-authoring/inbox.md#inbox-admin-control).

![Customize Experience Manager Inbox columns](assets/customize-columns.gif)

#### Interactieve communicatie opslaan als concept (6.5.5.0) {#save-as-draft}

You can use the Agent UI to save one or more drafts for each Interactive Communication and retrieve the draft later to continue working on it. You can specify a different name for each draft to identify it. Zie voor meer informatie [Interactieve communicatie opslaan als concept](../forms/using/prepare-send-interactive-communication.md#save-as-draft).

![Opslaan als concept](assets/save-as-draft.gif)

#### [!DNL Oracle WebLogic] application server support (6.5.5.0) {#weblogic-support}

Adobe Experience Manager Forms has added support for [!DNL Oracle WebLogic 12] for Adobe Experience Manager Forms on JEE. U kunt een upgrade uitvoeren vanaf een vorige versie of een nieuwe Experience Manager 6.5 Forms instellen op de JEE-server [!DNL Oracle WebLogic] 12.2.1.4 en hoger. Later komt dit overeen met de kleine versiewijzigingen, waarbij x in 12.2.1.x wordt vervangen door een versienummer.

#### Verbeteringen van de toegankelijkheid (6.5.5.0) {#accessibility-improvements}

Adobe Experience Manager Forms bevat de volgende toegankelijkheidsverbeteringen:

* Wanneer een gebruiker een adaptief formulier weergeeft als een HTML-formulier, wordt de [!UICONTROL Scribble Signature] blijft de tabfocus behouden.

* De foutberichten die worden weergegeven bij het verzenden van een adaptief formulier, bevatten nu de `aria-describedBy` kenmerk. Het kenmerk is gekoppeld aan de velden waarnaar in het foutbericht wordt verwezen. De `aria-describedby` kenmerk geeft id&#39;s aan van de elementen die het object beschrijven. Het helpt een relatie tot stand te brengen tussen widgets of groepen en tekst die hen beschrijft.

* Als een adaptief formulier een aantal verplichte velden heeft, wordt het verplichte kenmerk ingesteld op `True` voor dergelijke velden in het ARIA-toegankelijkheidsschema.

#### X-509 op certificaten gebaseerde verificatie voor SOAP-webservices in formuliergegevensmodel (6.5.5.0) {#x509-based-authentication-soap}

Het formuliergegevensmodel ondersteunt nu X-509 op certificaten gebaseerde verificatie terwijl SOAP-webservices als gegevensbron worden gebruikt. Zie voor meer informatie [SOAP-webservices configureren](../forms/using/configure-data-sources.md#configure-soap-web-services).

#### Andere belangrijke verbeteringen (6.5.5.0) {#other-improvements}

* Experience Manager 6.5 Forms on JEE Document Security is nu gebaseerd op [!DNL Apache Struts 2].

* Extra ondersteuning voor [!DNL Oracle Real Applications Cluster (RAC) 19c].

#### Afdrukbare uitvoer genereren in Experience Manager Forms-workflows (6.5.4.0) {#generate-printable-output}

Met de workflowstap Afdrukbare uitvoer genereren kunt u een bronsjabloonbestand integreren met een gegevensbestand. Dankzij deze integratie kunt u verschillende exemplaren van het sjabloonbestand afdrukken of opslaan. De stap genereert een PCL-, PostScript-, ZPL-, IPL-, TPCL- of DPL-uitvoer. Voor meer informatie over deze functie raadpleegt u [Forms-centric workflow voor OSGi - Step Reference](../forms/using/aem-forms-workflow-step-reference.md).

![Afdrukbare uitvoer genereren](assets/generate-print-output-step.gif)

#### Ondersteuning voor meerdere kolommen voor adaptieve formulieren en interactieve communicatie in de modus Lay-out (6.5.4.0) {#multi-column-adaptive-forms}

U kunt nu het aantal kolommen voor een deelvenster definiëren in adaptieve formulieren en interactieve communicatie. Schakel over naar de lay-outmodus om de nieuwe optie voor meerdere kolommen te gebruiken. Zie voor meer informatie [Gebruik de modus Lay-out om het formaat van componenten te wijzigen](../forms/using/resize-using-layout-mode.md).

![Lay-out met meerdere kolommen](assets/multi-column-layout.gif)

#### Aanpassingen in Experience Manager-inbox (6.5.4.0) {#aem-inbox}

Met de nieuwe optie Beheer beheren kunnen beheerders:

* De koptekst en het logo aanpassen.

* Hiermee bepaalt u de weergave van navigatiekoppelingen die beschikbaar zijn in de koptekst.

De optie Beheer is alleen zichtbaar voor de leden van de `administrators` of `workflow-administrators` groep. Voor meer informatie over deze functie raadpleegt u [Uw Postvak IN](../sites-authoring/inbox.md).

#### RTF-ondersteuning in HTML5-formulieren (6.5.4.0) {#rich-text-support}

Zet een tekstveld in een XFA-formulier om in een RTF-formulier. Zie voor meer informatie [Formuliersjablonen ontwerpen voor HTML5-formulieren](../forms/using/designing-form-template.md).

#### Toegankelijkheidsverbeteringen (6.5.4.0) {#forms-accessibility-enhancements-6540}

Experience Manager Forms bevat de volgende toegankelijkheidsverbeteringen:

* Schermlezers kondigen selectievakjes, koppelingen, Datumkiezer en Datuminvoer correct aan in een adaptief formulier.

* Elke pagina van een adaptief formulier bevat nu één titel en één hoofdlabel met een liggend streepje.

#### Delen en toegang aanvragen tot InBox-items van een Experience Manager Forms-gebruiker (6.5.3.0) {#share-request-access}

U kunt uw Inbox punten met een andere gebruiker delen. Zodra een andere gebruiker toegang krijgt tot uw Inbox-items, kan de gebruiker een claim indienen en de juiste actie ondernemen voor gedeelde items. Op dezelfde manier kunt u andere gebruikers om toegang tot Inbox-items verzoeken. Zie [Deel en verzoek toegang tot Inbox punten van een gebruiker](../forms/using/configure-shared-queues-osgi.md).

#### De buiten-van-bureaumontages voor Inbox punten van een gebruiker van Experience Manager Forms (6.5.3.0) vormen {#configure-out-of-office}

Als u van plan bent om uit het bureau te zijn, kunt u specificeren wat aan punten gebeurt die aan u voor die periode worden toegewezen.
U kunt een begindatum en -tijd en een einddatum en -tijd opgeven die van kracht moeten worden als uw instellingen buiten het kantoor zijn. U kunt een standaardpersoon instellen waarnaar al uw items worden verzonden. Zie [Vorm uit de montages van het Bureau](../forms/using/configure-out-of-office-settings.md).

#### Meerdere interactieve communicatie genereren met de Batch-API voor Experience Manager Forms (6.5.3.0) {#generate-multiple-ic}

U kunt de batch-API gebruiken om meerdere interactieve communicatie van een sjabloon te maken. De sjabloon is een interactieve communicatie zonder gegevens. De batch-API combineert gegevens met een sjabloon voor interactieve communicatie. De API is nuttig bij de massaproductie van interactieve communicatie. Bijvoorbeeld telefoonrekeningen, creditcardoverzichten voor meerdere klanten. Zie [Meerdere interactieve communicatie genereren met de Batch-API](../forms/using/generate-multiple-interactive-communication-using-batch-api.md).

<!-- TBD: Check if the wider team released anything in FY21.
-->

## Toetsreleases sinds [!DNL Adobe Experience Manager] 6,5 SP10{#key-releases-since-last-sp}

Tussen 26 augustus 2021 en 25 november 2021 heeft Adobe het volgende uitgebracht, in aanvulling op de servicepacks:

* [!DNL Adobe Experience Manager] as a Cloud Service [2021,9,0](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/2021/release-notes-2021-9-0.html) en [2021 10,0](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html).

* [[!DNL Experience Manager] bureaubladtoepassing 2.1 (2.1.3.4)](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/release-notes.html).

* [Experience Managers Screens: Feature Pack 202109](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202109.html)

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] 6.5 Documentatie](https://experienceleague.adobe.com/docs/experience-manager-65.html)
>* [Algemene opmerkingen bij de beschikbaarheidsrelease voor [!DNL Experience Manager] 6,5](release-notes.md)
>* [Opmerkingen bij de release van het servicepack voor [!DNL Experience Manager] 6,5](sp-release-notes.md)

