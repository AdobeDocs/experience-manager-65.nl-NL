---
title: Wat is nieuw in [!DNL Experience Manager] 6.5 Service Pack 10
description: Wat is nieuw in [!DNL Experience Manager] 6.5 Service Pack 10
contentOwner: AK
mini-toc-levels: 1
exl-id: 32470e6e-8a66-4670-82da-2259f6e001c3
source-git-commit: 5dfce89b2c03625e5f93fdcfaafd91d1ee77f476
workflow-type: tm+mt
source-wordcount: '4040'
ht-degree: 0%

---

# Nieuw in [!DNL Adobe Experience Manager] 6.5 Service Pack 10 {#aem-whats-new-service-pack}

<!-- TBD: Downsample this image. We do not need as big an image since customers don't use as big a screen to view. Also, having a 700+ KB decorative image is bad for page load time.
-->

![Wit-nieuw](assets/whatsnew.jpeg)

[!DNL Adobe Experience Manager] 6.5 De Pakken van de Dienst verstrekken nieuwe eigenschappen, klant-gevraagde verhogingen, en prestaties, stabiliteit, en veiligheidsverbeteringen op kwartaalintervallen. De beschikbaarheid op kwartaalbasis maakt het gemakkelijk om tot nieuwe eigenschappen en innovaties toegang te hebben en te nemen.

In dit artikel worden de functies beschreven die zijn opgenomen in het meest recente Service Pack, [belangrijke functies die zijn opgenomen in de vorige 6.5 Service Packs](#key-features-previous-service-packs) en de [belangrijke releases sinds de laatste release van Service Pack](#key-releases-since-last-sp).

## [!DNL Adobe Experience Manager Sites] {#aem-sites}

* **Verbeterde  [!DNL Content Fragment] modellen en Editor**: U kunt nu complexe en aangepaste modellen voor gestructureerde inhoud maken met behulp van geneste  [!DNL Content Fragment] modellen. Inhoudsstructuren worden gemoduleerd in basiselementen die zijn gemodelleerd als subfragmenten. Fragmenten op een hoger niveau verwijzen naar deze subfragmenten. Meer verbeteringen in gegevenstypen, zoals geavanceerde validatieregels, verbeteren de flexibiliteit van het modelleren van inhoud met [!DNL Content Fragments]. De [!DNL Experience Manager] [!DNL Content Fragment] redacteur steunt genestelde fragmentstructuren in een gemeenschappelijke redacteurszitting, met verhogingen zoals de mening van de boomstructuur en van labels voorzien broodkruimelnavigatie door fragmenthiërarchieën.

* **GraphQL API voor[!DNL Content Fragments]**: De nieuwe GraphQL API is de standaardmethode om gestructureerde inhoud in formaat te leveren JSON. Met GraphQL-query&#39;s kunnen clients alleen de relevante inhoudsitems aanvragen om een ervaring weer te geven. Een dergelijke selectie voorkomt overlevering van inhoud (mogelijkheid met HTTP REST API&#39;s) waarvoor inhoud moet worden geparseerd op de client. GraphQL-schema&#39;s zijn afgeleid van [!DNL Content Fragment]-modellen en API-reacties worden gemaakt in JSON-indeling. In [!DNL Experience Manager] als [!DNL Cloud Service], blijven [GraphQL vragen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/admin/graphql-api-content-fragments.html#persisted-queries-caching) en proces geheim voorgeheugenvriendelijke verzoeken van de GET. Het is nog niet mogelijk in [!DNL Experience Manager] 6.5.

* **Hiërarchiebeheer en toekomstig voorbeeld**: Gebruikers hebben nu een interface voor toegang tot de inhoudsstructuren van hun  [!DNL Experience Manager] startpagina&#39;s, waaronder de mogelijkheid om pagina&#39;s toe te voegen en te verwijderen bij het starten. Deze functie verbetert de flexibiliteit van [!DNL Experience Manager] lanceringen aan de versies van de auteursinhoud die voor toekomstige publicatie worden gericht. [Met de ](/help/sites-authoring/working-with-page-versions.md#timewarp) functie Tijd verdraaien kunnen gebruikers de voorvertoning starten als toekomstige inhoudsstaten.

* [!DNL Experience Manager] geeft rechtstreeks een lijst weer van alle inhoudsmodellen onder een map zonder dat de auteurs van de inhoud door de bestandsstructuur hoeven te navigeren. De functionaliteit vereist nu minder klikken en verbetert de efficiëntie van het ontwerpen.

* Met een padveld in de [!DNL Sites]-editor kunnen auteurs elementen slepen van [!DNL Content Finder].

* Platform biedt enkele toegankelijkheidsverbeteringen. Zie [Platform-updates](/help/release-notes/sp-release-notes.md#platform-65100).

## [!DNL Adobe Experience Manager Assets] {#aem-assets}

* [!DNL Experience Manager] breidt de Connected Assets-functionaliteit uit tot het gebruik van  [!DNL Dynamic Media] afbeeldingen in de toepasselijke kerncomponenten. Zie [Aangesloten elementen gebruiken](/help/assets/use-assets-across-connected-assets-instances.md).

* Wanneer gebruikers afzonderlijke elementen en verzamelingen als een koppeling delen (met het dialoogvenster [!UICONTROL Link Sharing]), kunnen ze kiezen of de ontvanger de oorspronkelijke elementen of hun uitvoeringen of beide mag downloaden. Zie [Elementen delen via koppeling](/help/assets/link-sharing.md).

   ![optie om alleen oorspronkelijke elementen, alleen de uitvoeringen of beide te downloaden](/help/release-notes/assets/share-assets-as-link.png)

* Wanneer gebruikers elementen downloaden die met hen als verbinding worden gedeeld, kunnen zij verkiezen om de originele activa, de vertoningen, of allebei te downloaden.

* **Gegenereerde** onderactiva beperken: Beheerders kunnen het aantal subelementen beperken dat  [!DNL Experience Manager] wordt gegenereerd voor samengestelde elementen zoals PDF-, PowerPoint-, InDesign- en toetsenbordbestanden.

   ![het genereren van subactiva beperken](/help/assets/assets/sub-asset-limit.png)

* Er is een nieuw [!DNL Camera Raw]-pakket beschikbaar dat [!DNL Adobe Camera Raw] v10.4 ondersteunt. Zie [Afbeeldingen verwerken met [!DNL Camera Raw]](/help/assets/camera-raw.md).

### [!DNL Dynamic Media] {#assets-dynamic-media}

* Er worden veel toegankelijkheidsverbeteringen aangebracht in de [!DNL Dynamic Media]-client, zodat een schermlezer een geschiktere en nuttige beschrijving van de handeling of gebruikersinterface kan presenteren. Zie [[!DNL Dynamic Media] updates](/help/release-notes/sp-release-notes.md#dynamic-media-65100).

## [!DNL Adobe Experience Manager Forms] {#aem-forms}

>[!NOTE]
>
>Het add-on pakket van [!DNL Experience Manager Forms] wordt een week na de geplande [!DNL Experience Manager] Service Pack-release beschikbaar gesteld.

* U kunt nu de service Automatede form conversion gebruiken om PDF forms in het Frans, Duits en Spaans ](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?lang=en#language-specific-meta-model) om te zetten in aangepaste formulieren.[

* **Foutberichten in de browser** Eigenschappen: Foutberichten toegevoegd voor elke eigenschap in de browser Adaptive Forms Properties. Met deze berichten kunt u de toegestane waarden voor een veld beter begrijpen.

* **Ondersteuning voor het gebruik van de letterlijke optie voor het instellen van de waarde voor een JSON-typevariabele**: U kunt letterlijke optie gebruiken om waarde voor een JSON typevariabele in de vastgestelde veranderlijke stap van een AEM Werkstroom te plaatsen. Met de letterlijke optie kunt u een JSON opgeven in de vorm van een tekenreeks.

* Toegevoegde ondersteuning voor `GuideBridge#getGuidePath` API in [!DNL AEM Forms].

<!--

* [Platform Updates](../forms/using/aem-forms-jee-supported-platforms.md): [!DNL Adobe Experience Manager Forms] on JEE has added support for the following platforms:
  * [!DNL Adobe Acrobat 2020]
  * [!DNL Ubuntu 20.04]
  * [!DNL Open Office 4.1.10]
  * [!DNL Microsoft Office 2019]
  * [!DNL Microsoft Windows Server 2019]
  * [!DNL RHEL8]

  -->

## Belangrijkste kenmerken in vorige [!DNL Experience Manager] 6.5-servicepacks {#key-features-previous-service-packs}

### Mogelijkheid om verwijderde pagina&#39;s en boomstructuur te herstellen (6.5.9.0) {#ability-to-restore-pages-tree}

U kunt nu de verwijderde pagina&#39;s en de gehele structuurweergave herstellen op een [!DNL Experience Manager Sites]-pagina.

### [!DNL Experience Manager Sites] {#aem-sites-previous-service-packs}

#### Live Copy-pagina&#39;s die beschikbaar zijn voor rollout (6.5.8.0) sorteren {#sort-livecopy-pages}

U kunt de Live Copy-pagina&#39;s die beschikbaar zijn voor rollout nu sorteren met de eigenschappen [!UICONTROL Name], [!UICONTROL Last modified date] en [!UICONTROL Last rollout date]. De [!UICONTROL Last rollout date] voor een pagina is een nieuwe eigenschap die in deze release is geïntroduceerd.

#### Beschikbaarheid van paginabewegingen en MSM-rollouts als asynchrone bewerkingen (6.5.7.0) {#page-moves-msm-asynchronous}

U kunt nu de paginabewegingen en MSM-rollouts uitvoeren als asynchrone bewerkingen om het effect ervan op de prestaties bij uitvoering te beperken. U kunt de bewerkingen plannen voor directe of latere uitvoering. De status van bijbehorende taken en processtappen wordt weergegeven in een console, die nuttig is voor het controleren van grootschalige MSM-rollouts.

#### Beschikbaarheid van de bewerking Pagina verplaatsen in de asynchrone modus (6.5.6.0) {#page-move-asynchronous}

De bewerking Pagina verplaatsen is nu beschikbaar in de asynchrone modus. U kunt de bewerking Pagina verplaatsen niet alleen direct uitvoeren, maar ook later plannen.

#### Verbeteringen van de toegankelijkheid (6.5.5.0) {#accessibility-sites}

* Verbeterde foutrapportage door tekstgegevens toe te voegen.

* Verbeterde focus van de gebruikersinterface tijdens toetsenbordnavigatie.

* Verbeterde contrastverhouding voor verschillende gebruikersinterface-elementen.

* Verbeterde consistentie van alt-kenmerken voor paginaafbeeldingen.

* Verbeterde consistentie van Toegankelijke Rich Internet Applications (ARIA) etiketten.

* Verbeterde NVDA-mogelijkheden (Non-Visual Desktop Access).

* Verbeterde ondersteuning voor schermlezers.

#### Andere belangrijke verbeteringen (6.5.5.0) {#other-enhancements-sites}

* Anonieme toegang tot CRXDE Lite is niet toegestaan om de beveiliging te verbeteren. In plaats daarvan worden de gebruikers naar het aanmeldingsscherm geleid. Zie [Ontwikkelen met CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md).

* Wanneer u een paginastructuur kopieert of plakt, kunt u nu de basispagina plakken of de basispagina plakken met de subpagina&#39;s van de structuur.

* [!DNL Adobe Experience Manager Experience Fragments] geëxporteerd naar  [!DNL Adobe Target] werkruimten worden nu weergegeven als unieke aanbiedingstypen en bieden bronnen aan in  [!DNL Target].

* Beheer van meerdere sites - De trigger Publiceren verwijdert nu een component van de gepubliceerde pagina als een component van de bronpagina wordt verwijderd.

* Beheer van meerdere sites - Wanneer de naam van een lokale component in een [!UICONTROL Live Copy] identiek is aan de naam van een component in de blauwdruk en de component uit de blauwdruk wordt opgerold, wordt de term `_msm_moved` nu toegevoegd aan de naam van de lokale component.

#### Stijlsysteemverbeteringen (6.5.4.0) {#style-system-enhancements}

U kunt nu stijlen selecteren in het dialoogvenster met het verbeterde stijlsysteem.

#### Prestatieverbeteringen op verschillende gebieden (6.5.4.0) {#performance-improvements}

* Verminderde tijd om ContextHub binnen een plaats (`contexthub.kernel.js`) te laden en te initialiseren. Hierdoor worden pagina&#39;s tijdens een bezoek aan de site sneller geladen.

* Verlaagde tijd om een pagina te vernieuwen nadat u [!DNL Experience Fragments] naar [!DNL Sites] Pagina-editor hebt gesleept.

* De laadtijd voor vermeldingen op een [!DNL Sites]-pagina met meer dan 200 actieve kopieën in **[!UICONTROL Live Copy Overview]** verkort.

* Verbeterde verwerking van onvolledige of ongeldige URL&#39;s. Dergelijke URL&#39;s kunnen de Sjablooneditor vertragen.

### [!DNL Adobe Experience Manager Assets] {#aem-assets-previous-service-packs}


* Bijgewerkt aan de naamgeving van Chinese landinstellingen en regio&#39;s met betrekking tot Hongkong, Macau en Taiwan, om deze in overeenstemming te brengen met de sociale en politieke standpunten van China (6.5.9.0).

* Er is een optionele configuratie geïntroduceerd om de casing in de e-mailid&#39;s in de ACS API-respons te wijzigen van [!DNL Adobe Experience Manager] (6.5.9.0).

   ![configuratie voor het wijzigen van e-mailadressen in kleine letters in ACS-reacties van  [!DNL Experience Manager]](assets/email-lowcase-config.png)

* Het contrast van tekst en pictogrammen tegen de achtergrond wordt verbeterd voor verschillende functies. Deze implementatie van WCAG-richtlijnen (Web Content Accessibility Guidelines) maakt [!DNL Assets] toegankelijker voor gebruikers met een beperkt gezichtsvermogen en kleurperceptie. Zie [toegankelijkheidsverbeteringen in [!DNL Assets]](sp-release-notes.md#assets-accessibility-6590) (6.5.9.0).
* Wanneer u [Functionaliteit voor verbonden elementen](/help/assets/use-assets-across-connected-assets-instances.md) gebruikt, kunt u nu een lijst weergeven met alle [!DNL Sites] pagina&#39;s die het element gebruiken. Deze verwijzingen naar een element zijn beschikbaar op de pagina [!UICONTROL Properties] van een element. Op deze manier kunnen beheerders, marketers en bibliothecarissen een volledig overzicht van het gebruik van bedrijfsmiddelen krijgen, waardoor ze het bedrijfsmerk beter kunnen bijhouden, beheren en de consistentie van merken kunnen verbeteren (6.5.8.0).

* Als u een element verwijdert waarnaar in een webpagina wordt verwezen, wordt een waarschuwing weergegeven. [!DNL Experience Manager] U kunt een element waarnaar wordt verwezen, forceren verwijderen of de verwijzingen controleren en wijzigen die op de pagina [!DNL Properties] van het element worden weergegeven. Als u op de referenties klikt, worden de lokale en externe [!DNL Sites] pagina&#39;s (6.5.8.0) geopend.

* [!DNL Assets] en  [!DNL Dynamic Media] bieden meerdere toegankelijkheidsverbeteringen. De verbeteringen hebben betrekking op toetsenbordnavigatie, gebruik van schermlezers en vergelijkbare verbeteringen om het gebruik van ondersteunende hulpmiddelen (AT) mogelijk te maken. Zie [[!DNL Assets] verbeteringen](/help/release-notes/sp-release-notes.md#assets-6570) en [[!DNL Dynamic Media] verbeteringen](/help/release-notes/sp-release-notes.md#dynamic-media-6570) (6.5.7.0)

* Gebruikers kunnen digitale elementen sorteren in de Kaart- en kolomweergave (6.5.7.0).

#### Toegankelijkheidsverbeteringen (6.5.6.0) {#accessibility-assets-6560}

* **Verbeterde focus van de gebruikersinterface tijdens toetsenbordnavigatie**, bijvoorbeeld focus op:

   * `x` in  [!UICONTROL Version Preview] dialoogvenster van een element in  [!UICONTROL Timeline].

   * Opties voor een uitvoerbare gebruikersinterface.

   * E-mailveld in het dialoogvenster [!UICONTROL Share Link] en veld voor het toevoegen van een gesloten gebruikersgroep op het tabblad [!UICONTROL Permission] in de map [!UICONTROL Properties].

* **Verbeterde functionaliteit met toetsenbordtoetsen**

   Gebruikers kunnen toetsenbordtoetsen gebruiken om besturingselementen in de formuliereditor voor metagegevensschema te slepen in de bladermodus van schermlezers.

* **Verbeterde bruikbaarheid voor schermlezers**, als gevolg van het volgende:

   * Schermlezers geven het doel van video- en audiospelers aan.

   * Schermlezers geven aan wat het doel is van de gebruikersinterfaceopties om de geselecteerde tags te verwijderen met [!UICONTROL Tags selection dialog] op element [!UICONTROL Properties].

   * Schermlezers kondigen de rijkoppen en rij-items van tabellen aan, zodat gebruikers weten welke items tot dezelfde rij behoren.

   * Beschrijvende en betekenisvolle paginatitel van zoekpagina.

   * Schermlezers geven de opties in het deelvenster met zoekfilters aan als uitbreidbare accordeons.

#### Andere verbeteringen in [!DNL Assets] (6.5.6.0) {#other-enhancements-assets-6560}

* Gebruikersgroepen die zijn gekoppeld aan mappen (privégroepen en niet-privégroepen) worden nu verwijderd uit de opslagplaats wanneer deze mappen [worden verwijderd. ](/help/assets/private-folder.md#delete-private-folder) De bestaande overbodige, zwevende, ongebruikte en automatisch gegenereerde gebruikersgroepen kunnen echter met JMX uit de opslagplaats worden verwijderd.

#### Toegankelijkheidsverbeteringen in [!DNL Assets] (6.5.5.0) {#assets-accessibility}

[!DNL Experience Manager Assets] is nu toegankelijker in overeenstemming met de Web Content Accessibility Guidelines (WCAG). De toegankelijkheid is verbeterd dankzij de volgende verbeteringen:

* Veel gebruikersinterface-elementen, besturingselementen, pagina&#39;s en dialoogvensters zijn schermlezervriendelijk.

* Veel elementen, besturingselementen en invoerformuliervelden van de gebruikersinterface zijn toegankelijk via het toetsenbord.

* De kleur en het contrast van bepaalde elementen van de gebruikersinterface worden bijgewerkt, zodat gebruikers met een beperkt gezichtsvermogen of gebruikers zonder kleurperceptie deze elementen van de gebruikersinterface kunnen onderscheiden. De kleur van sterrenbeoordelingspictogrammen (zoals in de sectie [!UICONTROL Rating] van het tabblad [!UICONTROL Advanced] in element [!UICONTROL Properties] of in de kaartweergave) wordt bijvoorbeeld gewijzigd voor het juiste contrast.

   ![Classificatiepictogrammen met verbeterd contrast](assets/star-rating-icons.png)

#### Uitgebreide afhandeling van uitzonderingen (6.5.5.0) {#exception-handling}

[!DNL Assets] de stroom van de gebruikersinterface heeft betere uitzonderingsbehandeling. Als een element geen type heeft voor de dimensie, wordt de waargenomen uitzondering opgenomen in de logbestanden.

#### Ondersteuning voor 3D-elementen in [!DNL Dynamic Media] (6.5.5.0) {#support-for-3d}

Met ondersteuning voor 3D-afbeeldingen in [!DNL Dynamic Media] kunnen klanten 3D-inhoud publiceren en toevoegen aan webpagina&#39;s en toepassingen. De steun omvat:

* Publiceer algemene indelingen voor 3D-elementen en genereren een middel-URL die kan worden gebruikt in webpagina&#39;s en andere toepassingen.

* Een 3D-webviewer, aangedreven door [!DNL Adobe Dimension], om de gepubliceerde 3D-elementen interactief weer te geven.

* Publiceer en bekijk gemeenschappelijke 3D activa op [!DNL Experience Manager Sites] pagina&#39;s gebruikend de [!DNL Sites] component WCM.

#### [!DNL Experience Manager Assets] configureren met [!DNL Brand Portal] (6.5.4.0) {#configure-assets-bp}

Het machtigingskanaal tussen [!DNL Experience Manager Assets] en [!DNL Brand Portal] wordt gewijzigd. Eerder, [!DNL Brand Portal] werd gevormd in Klassieke UI via Verouderde Gateway OAuth, die de het symbolenuitwisseling van JWT gebruikt om een token van de Toegang te verkrijgen IMS voor vergunning. [!DNL Experience Manager Assets] wordt nu gevormd met  [!DNL Brand Portal] door  [!DNL Adobe I/O], die een teken IMS voor vergunning van uw  [!DNL Brand Portal] huurder verwerft.

De stappen om [!DNL Experience Manager Assets] met [!DNL Brand Portal] te vormen zijn verschillend afhankelijk van uw [!DNL Experience Manager] versie, en of u voor het eerst vormt, of de bestaande configuraties bevordert. Zie [Elementen van Experience Managers configureren met Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/configure-aem-assets-with-brand-portal.html) voor meer informatie.

#### Toegankelijkheidsverbeteringen (6.5.4.0) {#accessibility-enhancements-6540}

[!DNL Experience Manager Assets] bevat de volgende toegankelijkheidsverbeteringen:

* Met de pijltoetsen op het toetsenbord kunt u gebieden binnen ingezoomde afbeeldingen verplaatsen en pannen. Zie [Elementen voorvertonen met alleen toetsenbordtoetsen](../assets/manage-assets.md#previewing-assets) voor meer informatie.

* De selectievakjes voor gemengde status (waarin de selectievakjes voor het eerste niveau niet zijn geselecteerd en zijn doorgehaald) in het deelvenster Filters zijn leesbaar voor schermlezers, tenzij u alle geneste selectievakjes selecteert.

* Er zijn beperkingen in de datum- en tijdnotatie opgenomen in veldlabels van datumvelden, zodat gebruikers de datum in de juiste notatie kunnen invoeren met het toetsenbord.
Bijvoorbeeld, `On Time (MM-DD-YYYY HH:mm)`. Hier is MM maand in het formaat van twee cijfers, YYYY is jaar, DD is dag in het formaat van twee cijfers, HH is uur in 24-uurs militair formaat, en mm is minuut.

* Schermlezers geven aan dat u de geselecteerde tags (`X`-symbool) en het aantal geselecteerde tags wilt verwijderen.

#### Kolom Sorteerbaar voor aanmaakdatum van elementen in lijstweergave (6.5.3.0) {#sortable-date-created-column}

Een nieuwe sorteerbare kolom voor de aanmaakdatum van elementen wordt toegevoegd in de DAM-lijstweergave en in de resultaten van zoekopdrachten naar elementen in de lijstweergave.

![Kolom Sorteerbaar voor datum die is gemaakt](assets/asset-created-date.png)

#### Visuele zoekopdracht naar [!DNL Adobe Experience Manager Assets] (6.5.2.0) {#visual-search}

[!DNL Assets] gebruikers kunnen visueel vergelijkbare afbeeldingen zoeken. Experience Manager geeft de slimme getagde afbeeldingen uit de DAM-opslagplaats weer die lijken op een door de gebruiker geselecteerde afbeelding. Zie [Visuele zoekopdracht](../assets/search-assets.md).

###  Dynamic Media  {#dynamic-media-previous-service-packs}

* [[!DNL Dynamic Media] is toegankelijker ](sp-release-notes.md#assets-accessibility-6590) voor:

   * Gebruiksgemak met toetsenbordtoetsen.
   * Contrast (met achtergrond) van tekst, plaatsaanduidingstekst en besturingselementen in verschillende editors.
   * Toegankelijkheid en gesproken tekst voor schermlezers.

* Efficiënt beelden van de beste kwaliteit leveren op apparaten met displays met hoge resolutie en beperkte netwerkbandbreedte, met Smart Imaging DPR (Device Pixel Ratio) en optimalisatie van de netwerkbandbreedte. Zie [Veelgestelde vragen over slimme beeldverwerking](/help/assets/imaging-faq.md) (6.5.9.0).

* [!DNL Dynamic Media] levering (`fmt` URL-optie) ondersteunt nu AVIF (AV1-afbeeldingsindeling) van de volgende generatie. Zie [fmt](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-is-http-fmt.html) (6.5.9.0) voor informatie over beeldserving en rendering.

#### CDN-inhoud in cache ongeldig maken (6.5.6.0) {#invalidate-cdn-cached-content}

U kunt de [!DNL Dynamic Media] gebruikersinterface nu gebruiken om inhoud van het Netwerk van de Levering van de Inhoud (CDN) ongeldig te maken caching. Hierdoor zijn de bijgewerkte elementen direct beschikbaar in plaats van te wachten tot de cache verloopt. U kunt CDN ongeldig maken door:

* Een CDN-validatiesjabloon maken: Elementen en aan een sjabloon gekoppelde URL&#39;s selecteren

* Elementen en bijbehorende voorinstellingen selecteren via de elementkiezer

* URL&#39;s van volledige middelen toevoegen

#### Selectieve publicatie van activa naar [!DNL Experience Manager] en [!DNL Dynamic Media] (6.5.6.0) {#selective-publishing}

U kunt er nu voor kiezen om elementen selectief te publiceren of de publicatie ervan ongedaan te maken op [!DNL Experience Manager] of [!DNL Dynamic Media] met de wizard [!UICONTROL Quick Publish] of [!UICONTROL Manage Publication]. U kunt de modus `Publish` of `Unpublish` ook op mapniveau instellen.

#### Smart Imaging voor Dynamic Media {#smart-imaging}

Slimme beeldverwerking gebruikt de unieke weergavekenmerken van elke gebruiker om automatisch de juiste afbeeldingen te leveren die zijn geoptimaliseerd voor zijn of haar ervaring, wat resulteert in betere prestaties en betrokkenheid. Slimme beeldverwerking werkt met bestaande voorinstellingen voor afbeeldingen en maakt gebruik van intelligentie tijdens de laatste milliseconde van levering om de bestandsgrootte van de afbeelding verder te beperken op basis van de snelheid van de browser of netwerkverbinding. Zie [Slimme beeldverwerking](../assets/imaging-faq.md).

#### Slim uitsnijden in videoprofielen voor Dynamic Media (6.5.3.0) {#smart-crop-video}

Slim uitsnijden voor video - een optionele functie die beschikbaar is in videoprofielen - gebruikt Adobe Sensei om het brandpunt automatisch te detecteren en uit te snijden in adaptieve video of progressieve video, ongeacht de grootte. Zie [Informatie over het gebruik van SmartCrop in videoprofielen](../assets/video-profiles.md).

### Experience Manager Forms {#aem-forms-previous-service-packs}

#### Ondersteuning voor [!DNL Azul Zulu OpenJDK] (6.5.9.0) {#support-azul-zulu}

U kunt nu toepassingen ontwikkelen en gebruiken met [!DNL Azul Zulu] builds van [!DNL OpenJDK] voor [!DNL Experience Manager Forms] op OSGi-implementaties. Zie [Opmerkingen bij de release van Experience Manager 6.5 Service Pack 9](sp-release-notes.md) en [Technische vereisten](../sites-deploying/technical-requirements.md) voor meer informatie.

#### Mogelijkheid om een bericht-e-mail naar een groep te verzenden met [!UICONTROL Assign Task] (6.5.9.0) {#group-notification-email}

U kunt nu een e-mailbericht naar een groep e-mailadres verzenden met de workflowstap Taak toewijzen.

#### Capaciteit om een Interactief Communicatie ontwerp terug te winnen na het wijzigen van de bron Interactieve Mededeling (6.5.9.0) {#retrieve-draft-after-source-modifications}

U kunt nu een interactieve communicatie ophalen die als concept is opgeslagen nadat u de bron Interactieve communicatie hebt gewijzigd.

#### Aangepaste domeinnaam instellen voor het laden, renderen en valideren van de reCAPTCHA-service (6.5.9.0) {#set-custom-domain-name-recaptcha}

reCAPTCHA-service gebruikt `https://www.recaptcha.net/` als het standaarddomein. U kunt nu de instellingen wijzigen om `https://www.google.com/` of een aangepaste domeinnaam in te stellen voor het laden, renderen en valideren van de reCAPTCHA-service.

#### Verbeteringen van invoergegevens voor [!UICONTROL Invoke Form Data Model Service]-workflowstap (6.5.9.0) {#input-data-enhancements-fdm}

Wanneer u een formuliergegevensmodel en een service selecteert in de workflowstap [!UICONTROL Invoke Form Data Model Service], geeft u serviceargumenten op voor invoergegevens.

Als u [!UICONTROL Relative to Payload] optie selecteert om een dossier als de dienstargument vast te maken, kunt u nu de omslagweg specificeren die het dossier in plaats van de daadwerkelijke dossiernaam bevat. Als u de mapnaam definieert in plaats van de naam van de bestandsbijlage, kunt u workflowmodellen opnieuw gebruiken. U beperkt het workflowmodel niet tot één bestandsnaam voor bijlagen.

#### Mogelijkheid om meerdere master pagina&#39;s te gebruiken in een sjabloon Document of Record (6.5.9.0) {#use-multiple-master-pages-dor-template}

U kunt nu meerdere master pagina&#39;s gebruiken in een document met een recordsjabloon. Hierdoor kunt u nu verschillende koptekst-, voettekst-, lettertypen- en logogegevens op de titelpagina en andere pagina&#39;s van de sjabloon plaatsen.

#### Pagina-einden in Document of Record (6.5.9.0) worden ondersteund {#support-page-breaks-dor}

U kunt nu pagina-einden toevoegen aan een Document of Record. Als een deelvenster pagina&#39;s afbreekt, kunt u daarom een pagina-einde toevoegen om het deelvenster te verplaatsen naar een nieuwe pagina in een document met records.

#### CAPTCHA-component weergeven of verbergen in een adaptieve vorm op basis van regels (6.5.8.0) {#show-hide-captcha}

U kunt CAPTCHA nu valideren bij het verzenden van het aangepaste formulier of bij actie van de gebruiker. U kunt ook voorwaarden toevoegen om CAPTCHA op een gebruikersactie te valideren en de component CAPTCHA in een adaptief formulier weergeven of verbergen op basis van regels.

#### Aangepaste CAPTCHA-services toevoegen (6.5.8.0) {#add-custom-captcha-services}

[!DNL Experience Manager Forms] biedt in de box-ondersteuning voor het gebruik van Google reCAPTCHA (een aparte licentie voor Google reCAPTCHA-API&#39;s is vereist) als een CAPTCHA-validatieservice. U kunt ook een aangepaste CAPTCHA-service gebruiken om CAPTCHA&#39;s te valideren.

#### Andere verbeteringen (6.5.8.0) {#other-enhancements-forms-6580}

* Verbeterde toegankelijkheid van de component [!DNL Experience Manager Forms] Datumkiezer.

* Extra ondersteuning voor het genereren van een interactieve communicatie in PCL-indeling met de PrintChannel-API.

* Wanneer u een PDFG-conversie uitvoert, kunt u nu de registerwijzigingen voor het genereren van aangepaste bladwijzers in- of uitschakelen.[!DNL Experience Manager Forms]

#### Prestatieverbeteringen (6.5.7.0) {#performance-improvements-forms}

[!DNL Experience Manager] 6.5 Service Pack 7 Forms verbetert de prestaties voor:

* De veldwaarden op de server valideren wanneer u een adaptief formulier verzendt.

* Een PDF-formulier converteren naar een adaptief formulier met [!DNL Automated Forms Conversion service].

#### Ondersteuning voor Microsoft SQL Server 2016 Altijd op beschikbaarheidsgroepen voor Hoge Beschikbaarheid (6.5.7.0) {#always-on-availability-groups}

[!DNL Experience Manager Forms] steunt nu  [!DNL Microsoft] SQL Server 2016 altijd op beschikbaarheidsgroepen voor Hoge Beschikbaarheid voor plaatsingen OSGi.

#### Formuliergegevensmodel HTTP-clientconfiguratie voor optimale prestaties (6.5.7.0) {#fdm-http-client-config}

[!DNL Experience Manager Forms] het model van vormgegevens wanneer het integreren met RESTful Webdiensten als gegevensbron omvat nu de cliëntconfiguraties van HTTP voor prestatiesoptimalisering. Zie [Gegevensbronnen configureren](../../help/forms/using/configure-data-sources.md#fdm-http-client-configuration).

#### Beschikbaarheid van de Optie van het Terugstellen voor elke component in de wijze van de Lay-out (6.5.7.0) {#reset-option-layout-mode}

U kunt nu de resetoptie voor elke component in de modus Indeling van een adaptief formulier gebruiken. Wanneer u een lay-out met meerdere kolommen definieert voor een deelvenster, kunt u deze functie gebruiken om afzonderlijke componenten in het deelvenster opnieuw in te stellen. Zie [De lay-outwijze van het gebruik resize componenten](../../help/forms/using/resize-using-layout-mode.md#resize-components).

#### Een adaptief formulier vooraf invullen op de client (6.5.6.0) {#prefill-merge-data-at-client}

Wanneer u een adaptief formulier vooraf instelt, voegt de [!DNL Experience Manager Forms]-server gegevens samen met een adaptief formulier en levert het ingevulde formulier aan u. De handeling voor het samenvoegen van gegevens vindt standaard plaats op de server.
U kunt de [!DNL Experience Manager Forms] server nu zodanig configureren dat [de handeling voor het samenvoegen van gegevens op de client wordt uitgevoerd](../../help/forms/using/prepopulate-adaptive-form-fields.md) in plaats van op de server. Hierdoor wordt de tijd die nodig is om adaptieve formulieren vooraf in te vullen en weer te geven, aanzienlijk verkort.

#### Integratie van formuliergegevensmodellen met RESTful-API&#39;s op een server met 2-wegs SSL-implementatie (6.5.6.0) {#fdm-integration-rest-apis-two-way-ssl}

[!DNL Experience Manager Forms] Het formuliergegevensmodel kan nu worden  [geïntegreerd met RESTful-API&#39;s op een server waarop een 2-wegs-SSL is geïmplementeerd](../../help/forms/using/configure-data-sources.md).

#### Toegevoegde ondersteuning voor [!DNL Adobe Sign] Tekstlabels in Automatede form conversion Service (6.5.6.0) {#sign-integration-acroform-afcs}

Als een AcroForm [!DNL Adobe Sign] tekstcodes bevat, worden deze velden nu herkend en weergegeven als [!DNL Adobe Sign] velden in het adaptieve formulier geconverteerd met [!DNL Automated Forms Conversion service]. Een ondertekenaar kan dergelijke velden invullen terwijl hij het adaptieve formulier ondertekent.

#### Ondersteuning voor de omzetting van gekleurde PDF forms in adaptieve formulieren (6.5.6.0) {#colored-PDF-forms}

Met [!DNL Automated Forms Conversion service] kunt u gekleurde PDF forms converteren naar adaptieve formulieren.

#### Steun voor SMB 2 en SMB 3 protocollen (6.5.6.0) {#smb-support}

[!DNL Experience Manager Forms] steunt nu SMB 2 en SMB 3 protocollen.

#### Verbeterd in cache plaatsen voor vertaalde adaptieve formulierpagina&#39;s (6.5.6.0) {#enhanced-caching-translated-adaptive-forms}

U kunt nu [locale als kiezer opgeven in het aangepaste formulier-URL in plaats van een argument in de aangepaste vorm URL](../../help/forms/using/supporting-new-language-localization.md). Hiermee kunt u vertaalde adaptieve formulieren in cache plaatsen op [!DNL Experience Manager Dispatcher]. Het in cache plaatsen van vertaald adaptief formulier was niet mogelijk in eerdere versies. Zie [Aangepaste formuliercache configureren op dispatcher](../../help/forms/using/configure-adaptive-forms-cache.md) voor gedetailleerde informatie over het configureren van caching voor het gebruik van landinstellingen als kiezer in de aangepaste formulier-URL.

#### Uitvoer van formuliergegevensmodelservice opslaan naar een variabele (6.5.6.0) {#save-fdm-service-to-variable}

Met het formuliergegevensmodel kunt u de uitvoer van een service van een formuliergegevensmodel opslaan in een variabele. [!DNL Experience Manager Forms] Hiermee wordt nu automatisch het type van de service van het formuliergegevensmodel toegewezen aan het type variabele.

#### Meerdere bestanden koppelen voor component Bestandsbijlage (6.5.6.0) {#attach-multiple-files}

U kunt nu [meerdere bestanden toevoegen](../../help/forms/using/introduction-forms-authoring.md) aan de [!UICONTROL File Attachment]-component van adaptieve formulieren.

#### De Adobe Experience Manager Inbox-kolommen aanpassen (6.5.5.0) {#customize-aem-inbox-columns}

U kunt een [!DNL Experience Manager] Inbox aanpassen om de standaardtitel van een kolom te veranderen, de positie van een kolom te herschikken, en extra kolommen te tonen die op de gegevens van een werkschema worden gebaseerd. Leden van de groep `administrators` of `workflow-administrators` kunnen de kolommen aanpassen. Zie [Beheer](../sites-authoring/inbox.md#inbox-admin-control) voor meer informatie.

![Kolommen van het Postvak IN van Experience Manager aanpassen](assets/customize-columns.gif)

#### Interactieve communicatie opslaan als concept (6.5.5.0) {#save-as-draft}

U kunt de Agent UI gebruiken om één of meerdere concepten voor elke Interactieve Mededeling te bewaren en het ontwerp later terug te winnen om aan het verder te werken. U kunt voor elk concept een andere naam opgeven om het te identificeren. Zie [Interactieve communicatie opslaan als concept](../forms/using/prepare-send-interactive-communication.md#save-as-draft) voor meer informatie.

![Opslaan als concept](assets/save-as-draft.gif)

#### [!DNL Oracle WebLogic] ondersteuning toepassingsserver (6.5.5.0) {#weblogic-support}

Adobe Experience Manager Forms heeft ondersteuning toegevoegd voor [!DNL Oracle WebLogic 12] voor Adobe Experience Manager Forms op JEE. U kunt een upgrade uitvoeren van een vorige versie of een nieuwe Experience Manager 6.5 Forms instellen op de JEE-server op [!DNL Oracle WebLogic] 12.2.1.4 en hoger. Later komt dit overeen met de kleine versiewijzigingen, waarbij x in 12.2.1.x wordt vervangen door een versienummer.

#### Verbeteringen van de toegankelijkheid (6.5.5.0) {#accessibility-improvements}

Adobe Experience Manager Forms bevat de volgende toegankelijkheidsverbeteringen:

* Wanneer een gebruiker een adaptief formulier voorvertoont als HTML-formulier, behoudt het veld [!UICONTROL Scribble Signature] de tabfocus.

* De foutberichten die worden weergegeven bij het verzenden van een adaptief formulier, bevatten nu het kenmerk `aria-describedBy`. Het kenmerk is gekoppeld aan de velden waarnaar in het foutbericht wordt verwezen. Het `aria-describedby` attribuut wijst op IDs van de elementen die het voorwerp beschrijven. Het helpt een relatie tot stand te brengen tussen widgets of groepen en tekst die hen beschrijft.

* Als een adaptief formulier bepaalde verplichte velden heeft, wordt het verplichte kenmerk voor dergelijke velden in het ARIA-toegankelijkheidsschema ingesteld op `True`.

#### X-509 op certificaten gebaseerde verificatie voor SOAP-webservices in formuliergegevensmodel (6.5.5.0) {#x509-based-authentication-soap}

Het formuliergegevensmodel ondersteunt nu X-509 op certificaten gebaseerde verificatie terwijl SOAP-webservices als gegevensbron worden gebruikt. Zie [SOAP-webservices configureren](../forms/using/configure-data-sources.md#configure-soap-web-services) voor meer informatie.

#### Andere belangrijke verbeteringen (6.5.5.0) {#other-improvements}

* Experience Manager 6.5 Forms on JEE Document Security is nu gebaseerd op [!DNL Apache Struts 2].

* Toegevoegde ondersteuning voor [!DNL Oracle Real Applications Cluster (RAC) 19c].

#### Afdrukbare uitvoer genereren in Experience Manager Forms-workflows (6.5.4.0) {#generate-printable-output}

Met de workflowstap Afdrukbare uitvoer genereren kunt u een bronsjabloonbestand integreren met een gegevensbestand. Dankzij deze integratie kunt u verschillende exemplaren van het sjabloonbestand afdrukken of opslaan. De stap genereert een PCL-, PostScript-, ZPL-, IPL-, TPCL- of DPL-uitvoer. Voor meer informatie over deze eigenschap, zie [Forms-centric werkschema op OSGi - de Verwijzing van de Stap](../forms/using/aem-forms-workflow-step-reference.md).

![Afdrukbare uitvoer genereren](assets/generate-print-output-step.gif)

#### Ondersteuning voor meerdere kolommen voor adaptieve formulieren en interactieve communicatie in de modus Lay-out (6.5.4.0) {#multi-column-adaptive-forms}

U kunt nu het aantal kolommen voor een deelvenster definiëren in adaptieve formulieren en interactieve communicatie. Schakel over naar de lay-outmodus om de nieuwe optie voor meerdere kolommen te gebruiken. Zie [De modus Lay-out gebruiken om het formaat van componenten te wijzigen](../forms/using/resize-using-layout-mode.md) voor meer informatie.

![Lay-out met meerdere kolommen](assets/multi-column-layout.gif)

#### Aanpassingen in Experience Manager-inbox (6.5.4.0) {#aem-inbox}

Met de nieuwe optie Beheer beheren kunnen beheerders:

* De koptekst en het logo aanpassen.

* Hiermee bepaalt u de weergave van navigatiekoppelingen die beschikbaar zijn in de koptekst.

De optie Beheer is alleen zichtbaar voor de leden van de groep `administrators` of `workflow-administrators`. Voor meer informatie over deze eigenschap, zie [Uw Inbox](../sites-authoring/inbox.md).

#### RTF-ondersteuning in HTML5-formulieren (6.5.4.0) {#rich-text-support}

Zet een tekstveld in een XFA-formulier om in een RTF-formulier. Zie [Formuliersjablonen ontwerpen voor HTML5-formulieren](../forms/using/designing-form-template.md) voor meer informatie.

#### Toegankelijkheidsverbeteringen (6.5.4.0) {#forms-accessibility-enhancements-6540}

Experience Manager Forms bevat de volgende toegankelijkheidsverbeteringen:

* Schermlezers kondigen selectievakjes, koppelingen, Datumkiezer en Datuminvoer correct aan in een adaptief formulier.

* Elke pagina van een adaptief formulier bevat nu één titel en één hoofdlabel met een liggend streepje.

#### Deel en verzoek om toegang tot Inbox-items van een Experience Manager Forms-gebruiker (6.5.3.0) {#share-request-access}

U kunt uw Inbox punten met een andere gebruiker delen. Zodra een andere gebruiker toegang krijgt tot uw Inbox-items, kan de gebruiker een claim indienen en de juiste actie ondernemen voor gedeelde items. Op dezelfde manier kunt u andere gebruikers om toegang tot Inbox-items verzoeken. Zie [Toegang tot In-box-items van een gebruiker delen en aanvragen](../forms/using/configure-shared-queues-osgi.md).

#### Vorm de montages buiten-van-bureau voor Inbox punten van een gebruiker van Forms van de Experience Manager (6.5.3.0) {#configure-out-of-office}

Als u van plan bent om uit het bureau te zijn, kunt u specificeren wat aan punten gebeurt die aan u voor die periode worden toegewezen.
U kunt een begindatum en -tijd en een einddatum en -tijd opgeven die van kracht moeten worden als uw instellingen buiten het kantoor zijn. U kunt een standaardpersoon instellen waarnaar al uw items worden verzonden. Zie [De instellingen voor Buiten het Bureau configureren](../forms/using/configure-out-of-office-settings.md).

#### Meerdere interactieve communicatie genereren met de Batch-API voor Experience Manager Forms (6.5.3.0) {#generate-multiple-ic}

U kunt de batch-API gebruiken om meerdere interactieve communicatie van een sjabloon te maken. De sjabloon is een interactieve communicatie zonder gegevens. De batch-API combineert gegevens met een sjabloon voor interactieve communicatie. De API is nuttig bij de massaproductie van interactieve communicatie. Bijvoorbeeld telefoonrekeningen, creditcardoverzichten voor meerdere klanten. Zie [Meerdere interactieve communicatie genereren met de batch-API](../forms/using/generate-multiple-interactive-communication-using-batch-api.md).

<!-- TBD: Check if the wider team released anything in FY21.
-->

## Toetsreleases sinds [!DNL Adobe Experience Manager] 6.5 SP9 {#key-releases-since-last-sp}

Tussen 27 mei 2021 en 26 augustus 2021 heeft Adobe het volgende uitgebracht, in aanvulling op de servicepacks:

* [!DNL Adobe Experience Manager] als Cloud Service  [2021.6.0](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/2021/release-notes-2021-6-0.html),  [2021.7.0](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/2021/release-notes-2021-7-0.html) en  [2021.8.0](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=en).

* [[!DNL Experience Manager] bureaubladtoepassing 2.1 (2.1.3.3)](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/release-notes.html).

* [Experience Managers Screens: Feature Pack 202105](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202105.html?lang=en)

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] 6.5 Documentatie](https://experienceleague.adobe.com/docs/experience-manager-65.html)
>* [Algemene opmerkingen bij de beschikbaarheidsrelease voor [!DNL Experience Manager]  6.5](release-notes.md)
>* [Opmerkingen bij de release van het servicepack voor [!DNL Experience Manager]  6.5](sp-release-notes.md)

