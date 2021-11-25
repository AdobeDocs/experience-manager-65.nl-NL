---
title: '[!DNL Experience Manager] Opmerkingen bij de release van 6.5 servicepack'
description: Opmerkingen bij de release die specifiek zijn voor [!DNL Adobe Experience Manager] 6.5 servicepack 11
docset: aem65
mini-toc-levels: 1
exl-id: 28a5ed58-b024-4dde-a849-0b3edc7b8472
source-git-commit: 35260325b583bd047f22ffa88afb9469b2023e60
workflow-type: tm+mt
source-wordcount: '3306'
ht-degree: 0%

---

# [!DNL Adobe Experience Manager] Opmerkingen bij de release van 6.5 servicepack {#aem-service-pack-release-notes}

## Gegevens vrijgeven {#release-information}

| Producten | [!DNL Adobe Experience Manager] 6.5 |
| -------- | ---------------------------- |
| Versie | 6.5.11.0. |
| Type | Service Pack-release |
| Date | 25 november 2021 |
| URL downloaden | [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.11.zip) |

## Wat is inbegrepen in [!DNL Adobe Experience Manager] 6.5.11.0. {#what-is-included-in-aem}

[!DNL Adobe Experience Manager] 6.5.11.0 omvat nieuwe eigenschappen, zeer belangrijke klant-gevraagde verhogingen, en prestaties, stabiliteit, en veiligheidsverbeteringen, die sinds de beschikbaarheid van 6.5 versie in April 2019 worden vrijgegeven. Het de dienstpak wordt geïnstalleerd op [!DNL Adobe Experience Manager] 6.5

De belangrijkste functies en verbeteringen die zijn geïntroduceerd in [!DNL Adobe Experience Manager] 6.5.11.0 zijn:

* Ondersteuning voor meerdere velden toegevoegd voor tekstgegevenstype met meerdere regels.

* Verbetering om gebruikers bewust te maken van de asynchrone taak die momenteel op de achtergrond wordt uitgevoerd om te voorkomen dat ze meerdere asynchrone bewerkingen op hetzelfde pad activeren.

* U kunt sitemap automatisch genereren voor SEO-doeleinden met behulp van de [SEO-indexpakket](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/sites-seo-index-content-1.0.0.zip). Sitemaps, alternatieve URL&#39;s, robot meta-tags en meer worden ondersteund in de [!DNL Core Components].

* Dankzij de verbeteringen in de gebruikerservaring wordt het aantal elementen in een map weergegeven. Voor meer dan 1000 elementen in een map: [!DNL Assets] geeft 1000+ weer.

* U kunt de sorteeroptie nu renderen in de Kaart- en kolomweergave.

* U kunt nu [!DNL Dynamic Media] om Algemene Montages te vormen in plaats van het moeten door [!DNL Dynamic Media Classic] bureaubladtoepassing. Zie [Algemene instellingen van Dynamic Media configureren](/help/assets/dm-general-settings.md).

* U kunt nu [!DNL Dynamic Media] om Publish Opstelling te vormen in plaats van het moeten door [!DNL Dynamic Media Classic] bureaubladtoepassing. Zie [Dynamic Media-publicatie-instellingen configureren](/help/assets/dm-publish-settings.md).

* De ingebouwde opslagplaats (Apache Jackrabbit Oak) wordt bijgewerkt naar 1.2.2.9.

Hieronder volgt een lijst met oplossingen die u vindt in [!DNL Experience Manager] 6.5.11.0-release.

### [!DNL Sites] {#sites-65110}

Als u toegang wilt tot inhoud zonder kop met gebruik van Content Fragments met GraphQL en de verbeterde mogelijkheden van Content Fragment Models en Editor wilt gebruiken, installeert u de opdracht [indexdefinitiepakket](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/cfm-graphql-index-def-1.0.0.zip)en herindexeert de volgende asynchrone AEM indexdefinities:

* /oak:index/assetPrefixNodename

* /oak:index/fragmenten

* /oak:index/graphicConfig


De volgende problemen zijn opgelost in [!DNL Sites]:

* De sjabloon voor het maken van een inhoudsfragment is niet zichtbaar bij het maken van een inhoudsfragment (SITES-3365).

* Reguliere expressies en [!UICONTROL Unique] veldopties werken niet in [!UICONTROL appsUrl] model in de inhoudsfragmenteditor (SITES-1823).

* Configuraties worden toegevoegd in `/apps/system` knoop eerder dan dat `/libs` bij de installatie van het vorige servicepack (SITES-3203).

* Functies die gebruikmaken van inhoudsfragmenten werken niet zoals gewoonlijk bij de installatie van het vorige servicepack (SITES-3151).

* Sorteren werkt niet in [!UICONTROL Content Fragment Models] console (SITES-2722).

* GraphiQL laadt geen modellen (schema&#39;s) en ontmoet fout voor eindpunt JSON (SITES-2428).

* De veldtypen voor opsommingen die zijn toegevoegd aan een [!UICONTROL Content Fragment Model] zijn niet zichtbaar in [!UICONTROL Content Fragment Model Editor] (SITES-2391).

* Het gegevenstype van tags ondersteunt geen bepaalde gegevenstypen (SITES-2390).

* [!UICONTROL Content Fragment Rest API] exporteert verouderde tagwaarden (SITES-2386).

* De pijl in breadcrumb wordt niet goed uitgelijnd in de Content Fragments Editor (SITES-2341).

* Het zoeken naar verwijzingen naar inhoudsfragmenten gaat veel tijd in beslag bij grote datasets (SITES-2147).

* [!UICONTROL CopyUrl] optie is niet geschikt in [!UICONTROL Content Fragments Editor] (SITES-2007).

* Er wordt geen waarschuwing weergegeven wanneer het inhoudsfragment samen met een bijbehorend model wordt gepubliceerd en het model remwijzigingen introduceert (SITES-1988).

* Het bewerken van URL&#39;s van het fragmentmodel van inhoud is anders voor verschillende toepassingen van het bewerken van modellen van inhoudsfragmenten (SITES-1980).

* Wanneer u twee inhoudsfragmenten met dezelfde titel maakt met de inline [!UICONTROL New Content Fragment] , retourneert de wizard hetzelfde fragmentpad (SITES-1978).

* Automatisch aanvullen werkt niet in [!UICONTROL Content Fragment Model] zoekfacet (SITES-1976).

* If a content fragment contains a huge hierarchy of nested fragments, the [!UICONTROL Content Fragment Editor] becomes irresponsive when loading side panel (SITES-1974).

* Het algemene zoeken in de fragmentkiezer werkt niet (SITES-1973).

* References are updating when moving a content fragment (SITES-1897).

* De optie om een pagina te maken ontbreekt in de Kaart- en Kolomweergave (NPR-37549).

* Wanneer u de volgorde van componenten op een startpagina wijzigt, blijft bij het promoten van de Launch de volgorde van componenten niet behouden (NPR-37539).

* The option to select all the items in a list is not working on the rollout page (NPR-37443).

* Als u meerdere pagina&#39;s wilt activeren, wordt een nieuwe JCR-sessie geopend voor `wcm-workflow-service` gebruiker (NPR-37417).

* De verrichting van de beweging op omslagen in de console van Plaatsen ontbreekt met een foutenmelding &quot;Kon de lanceringsinformatie voor geselecteerd punt niet terugwinnen&quot;(NPR-37340).

* Bij het genereren van een miniatuur voor blauwdruk en het implementeren in live kopieën, wordt de overerving voor tabbladen na miniaturen in live kopieën verbroken (NPR-37190).

* Het filter voorspelt dat Live Copy wordt weergegeven, maar geeft niet alle live kopieën weer (NPR-37126).

* De gebeurtenis van de replicatie keert niet de lijst van alle ouder en kindpagina&#39;s terug die voor schrapping werden gemerkt wanneer de manager van de replicatiegebeurtenis op de auteur (NPR-37123) wordt geroepen.

* Wanneer u een eigenschap met meerdere waarden opslaat met de Bulk-editor, wordt de door komma&#39;s gescheiden tekenreeks opgeslagen als het eerste element van de array (NPR-37089).

* De grootte van de lay-out van de component kan niet worden gewijzigd in de mobiele lay-out (NPR-37086).

* Een nieuw knooppunt wordt onjuist gemaakt op live kopieerniveau bij het opslaan van pagina-eigenschappen na het toevoegen van rollout-configuraties (NPR-37084).

* Gebruiker kan geen live kopieën maken of uitrollen met pagina-eigenschappen voor nieuwe master pagina&#39;s (SITES-3442).

* Met labels worden namen van tags weergegeven in plaats van namen van titels en afsluitende opties, maar worden de tags niet volledig verwijderd omdat de eigenschap tags onjuist werkt wanneer de overerving op eigenschapsniveau wordt geannuleerd (NPR-36831).

* De optie om de selectie van alle items op te heffen werkt niet en de koptekst overlapt met de eerste rij in de tabel, op de pagina die een lijst met live kopieën weergeeft (NPR-37070).

* In een douanedialoog die in een werkschema wordt gebruikt, wanneer het proberen om de dialoog te bevestigen, ontbreekt de Experience Manager met een fout in de browser console (GRANITE-35049).

De volgende toegankelijkheidsverbeteringen zijn beschikbaar in [!DNL Adobe Experience Manager Sites]:

* De rol van de [!UICONTROL Site References] en [!UICONTROL Language Copies] opties (SITES-1791).

* De volgorde van de browsermodusfocus wordt nu opeenvolgend verplaatst op verschillende opties in de gebruikersinterface (SITES-1791).

* Schermlezers vertellen nu of het geselecteerde structuuritem zich in de geselecteerde toestand bevindt en geven de gebruiker ook door dat het actiegebied wordt weergegeven (SITES-2109).

* Schermlezers geven nu een melding wanneer er een laadindicator is voor het selecteren van een filter of het zoeken naar een pagina (SITES-1790).

* Schermlezers vertellen nu wanneer de [!UICONTROL Filter] retourneert geen zoekresultaat in het linkerspoor (SITES-1599).

* Wanneer schermlezers navigeren in de bladermodus, beschrijven ze de rol van de inhoudspagina en de geselecteerde staat van een pagina wanneer op Enter wordt gedrukt (SITES-1579).

* Schermlezers vertellen nu wanneer [!UICONTROL Note Add] is geselecteerd (SITES-1573).

* Formuliervelden hebben nu behalve de plaatsaanduidingen ook visuele labels, zodat de gebruikers van schermlezers de juiste instructies krijgen bij het invoeren van de veldwaarden (SITES-1258).

### [!DNL Assets] {#assets-65110}

De volgende toegankelijkheidsverbeteringen zijn beschikbaar in [!DNL Assets]:

* In de kaartweergave in het dialoogvenster [!DNL Assets] opslagplaats, bij gebruik `Tab` Als u de focus wilt verplaatsen naar het eerste item dat Snelle handelingen opent, wordt de naam van het item dat de focus heeft, bekendgemaakt door de schermlezer.
* In [!DNL Dynamic Media] [!UICONTROL Viewer Preset Editor]Als Schaduwkleur en Randkleur niet aanwezig zijn, worden de invoer uitgeschakeld met de eigenschap disabled. Toetsenbordgebruikers kunnen de focus niet op de invoer instellen en schermlezers geven de status van het besturingselement niet aan als uitgeschakeld.
* In [!DNL Dynamic Media], in de interface om een nieuw videocoderingsprofiel te maken, [!UICONTROL Smart Crop Ratio] Deze optie is gelabeld voor toegankelijkheid, zodat schermlezers de optie op de juiste wijze bekendmaken.

* U hebt nu toegang tot de besturingselementen voor de referentielijst in [!DNL Experience Manager Assets] met een toetsenbord.

De volgende problemen zijn opgelost in [!DNL Assets]:

* Wanneer een gebruiker van de contributiegroep navigeert naar de gegevensopslagplaats voor DAM-middelen, is dit een uitzondering `POST` De aanvraag wordt geactiveerd voor het maken van een verzameling. Dit `POST` De aanvraag is mislukt en geeft een fout weer in de logboeken (NPR-37171).

* Wanneer u een live kopie van de blauwdruk met een geneste mapstructuur maakt, worden de gewijzigde eigenschappen van de bronmap niet bijgewerkt in de map met live kopieën (NPR-37449).

* When selecting multiple assets and modifying the metadata field values, saving the assets does not retain the values. De wijzigingen in metagegevens worden ook niet toegepast (NPR-37341).

* Wanneer u meerdere elementen selecteert en de eigenschappen wijzigt, worden de waarden van de aangepaste eigenschappen (dropdowns) overschreven door de standaardwaarden (NPR-36437).

* Er wordt een onjuiste PDF-uitvoering gegenereerd voor de brochure-, flyer- en InDesign-sjablonen (NPR-36433).

* Een [!DNL Adobe Target] activiteit met [!DNL Experience Manager] het richten van wijze ontbreekt [!DNL Adobe Analytics] rapport metrische is referenced (NPR-37167).

* Wanneer een gebruiker met e-mail die domeinnaam met gemengde hoofdletters gebruikt een element uitcheckt, is het element niet zichtbaar in de uitgecheckte elementen van de gebruiker in [!DNL Asset Link] (CQ-4329266).

<!-- Add 
* [!DNL Adobe Asset Link] is not able to access the digital assets even when the [!DNL Creative Cloud] and [!DNL Experience Management] entitlements are provided by two different organizations. -->

* Als u een video toevoegt met aangepaste metagegevens die tijdens het uploaden naar een pagina worden gegenereerd, wordt een fout weergegeven met betrekking tot een onbekende naamruimte, zelfs als de naamruimte is geregistreerd (CQ-4331471).

* In [!DNL Assets], als [!DNL Launcher] is uitgeschakeld, werkt het terugschrijven van metagegevens niet als dit handmatig wordt geactiveerd (CQ-4329082).

### [!DNL Dynamic Media] {#dynamic-media-65110}

De volgende opgeloste problemen zijn beschikbaar in [!DNL Dynamic Media]:

* Element wordt niet bijgewerkt in [!DNL Dynamic Media] bij het herstellen van een elementversie in [!DNL Experience Manager] (NPR-37421).

* ECatalogs worden niet gepubliceerd bij het publiceren van PDF-bestanden (CQ-4329886).

* 3D-elementen worden niet geladen wanneer de gepubliceerde pagina wordt geopend voor het geval dat de component een voorinstelling gebruikt die buiten de box valt (CQ-4329205).

* Problemen bij de verwerking van PDF-activa in geval van grote gegevensbanken (CQ-4328711).

* PDF-verwerkingsfout wordt niet doorgegeven aan [!DNL Experience Manager] in geval van een storing bij [!DNL Scene7] (CQ-4331145).

* Gebruikers kunnen de standaardeigenschappen van metagegevens voor een .MOV-element niet zien (CQ-4332546).

* Kan .MXF-videobestanden niet uploaden naar [!DNL Dynamic Media] gebruiken [!DNL Experience Manager] (CQ-43297/09).

* Upload problemen wanneer de hoofdmap van het aangepaste bedrijf is ingesteld (CQ-4332800).

* In [!DNL Experience Manager] instellingen met aangepaste draagbalk met `ActivationModel` Tijdens de workflow loopt de Experience Manager vast als gevolg van geheugenproblemen bij het uploaden van PDF-bestanden. (CQ-4330512).

* Prestatieproblemen in `DamEventRecorder` (CQ-4334072).

* Als een verbluffende video-hyperlink (gekoppelde URL) speciale tekens bevat, wordt de doel-URL gecodeerd door de viewer en wordt de URL weergegeven als een onjuiste productpagina (CQ-4331639).

* Op een pagina met videoprofielen verdwijnen de werkbalkopties als de gebruiker direct bij het laden van de pagina een videoprofiel selecteert (CQ-4308521).

* Fout bij verwerking van DM-middelen vanwege gelijktijdige schrijfacties van JCR (CQ-4333489).

* Toegang tot de pagina Videoprofielen mislukt als voor de hoofdmap van het videoprofiel van de gebruiker aangepaste toegangsregels zijn gedefinieerd voor het hoofdknooppunt van videoprofielen (CQ-4332941).

* In a zoomable image, using the shortcut keys (&#39;+&#39;, &#39;-&#39;) or &#39;Esc&#39; key traps the screen readers focus (CQ-4290719).

* Wanneer een gebruiker op de sneltoets voor de formuliermodus (&#39;F&#39;) klikt, wijst de schermlezer het label van het dialoogvenster [!UICONTROL Embed Size] de menuknop beschikbaar in [!UICONTROL Get Embed] codeselectie (CQ-4290929).

* Als u via toetsenbordnavigatie het pop-upvenster met de e-mailkoppeling opent, zijn de foutsuggesties in de gebruikersinterface voor de velden Aan en Van niet beschrijvend (CQ-4290930).

* When navigating to the email link dialog box, the screen reader does not narrate the label information for the newly added edit fields on using the down arrow and form mode shortcut key (&#39;F&#39;) (CQ-4290934).

* Wanneer u naar het dialoogvenster E-mailkoppeling navigeert, geeft de schermlezer niet het visuele sterretje (*) weer voor de verplichte velden &#39;Aan&#39; en &#39;Van&#39; (CQ-4290935).

* The users are not able to identify the landmark and region using the shortcut keys (&#39;D&#39;, &#39;R&#39;) (CQ-4312118).

<!-- Anuj to check if this section is required or not. We have an enh. in CIF area that is mentioned. It is added above and not part of this bug fix section.
-->

### Commerce {#commerce-65110}

* Wanneer u de [!UICONTROL Publish Later] -optie, komt de gebruikersinterface niet overeen met de status [!UICONTROL Publication Pending] (CQ-4334229).

* Als u de publicatie van een map ongedaan maakt, wordt de publicatie van de producten van die map niet volledig ongedaan gemaakt. De producten worden uit de uitgever verwijderd, maar bestaan nog steeds in de auteurinstantie (CQ-4332731).

### Platform {#platform-65110}

* Wanneer een gebruiker op het pictogram voor het opnieuw ordenen van een optie met meerdere velden klikt, verdwijnt de schuifbalk uit de gebruikersinterface (CQ-4331100).

* Wanneer een gebruiker na de upgrade de containercomponent voor de aanmelding op de werkplek opent, is de koptekst van het dialoogvenster niet zichtbaar in de gebruikersinterface (CQ-4316173).

### Integrations {#integrations-65110}

* Een [!DNL Adobe Target] activiteit met [!DNL Experience Manager] het richten van wijze ontbreekt [!DNL Adobe Analytics] rapport metrische is referenced (NPR-37167).

### Projecten {#projects-65110}

* Bij upgrade vanaf [!DNL Experience Manager] 6.5.8.0 tot versie 6.5.9.0 overschrijft de installatie de eigenschappen op `/content/dam/projects`. Het stelt het toegewezen meta-gegevensschema en de eigenschappen van de omslag aan gebrek (NPR-37124) terug.

### Gebruikersinterface {#user-interface-65110}

* The folder icon representing the model is incorrect (NPR-37176).

* Wanneer een gebruiker een onderzoek uitvoert of gebruikend browser van het weggebied doorbladert, worden de onjuiste knopen getoond (NPR-37175).

* Op de publicatie-instantie worden de binnenkomende aanvragen enkele minuten geblokkeerd (NPR-37169).

* Wanneer u een eigenschap voor meerdere velden toevoegt in een dialoogvenster voor een aangepaste workflow, gaat het dialoogvenster niet verder en kan de gebruiker het dialoogvenster niet sluiten (NPR-37075).

### Vertaalprojecten {#translation-65110}

* De automatische promotie van de lancering van de vertaling ontbreekt met een uitzondering (NPR-37528).

* De vertaling van het ervaringsfragment werkt de referenties voor de taalkopie van de URL (NPR-37522) niet bij.

* Wanneer een fragment van de Ervaring in een weg wordt gecreeerd die niet de weg van de taalwortelstructuur aanpast, weerspiegelt het toevoegen van die pagina aan een vertaalproject een leeg foutenmelding (NPR-37425).

* Wanneer een pagina (Engels) met Experience Fragments wordt gewijzigd en verzonden voor vertaling, worden de reeds vertaalde Erviteitsfragmenten overschreven door Engelse inhoud (NPR-37283).

* Het filter voor vertaalbureaus werkt niet correct (NPR-37186).

* De componenten Fragment en Accordion van de ervaring worden niet vertaald uit-van-de-doos voor de inhoud van de steekproefplaats (NPR-37170).

* Na de upgrade naar [!DNL Experience Manager] 6.5.9.0. Als u een pagina aan het vertaalproject toevoegt, wordt een leeg foutbericht weergegeven (NPR-37105).

* Wanneer u pagina&#39;s toevoegt aan de binnenzijde van de opstart, worden de vertaalpagina&#39;s met vergelijkbare namen niet opgenomen in het project (NPR-37082).

* Wanneer u een formulierwoordenboek exporteert als een .xliff-bestand met behulp van de conversieinterface, is de veldvolgorde van het geëxporteerde bestand onjuist (NPR-37048).

* Wanneer het opstellen van een ouderpagina van een vertaalproject, worden de taal-specifieke kindpagina&#39;s geschrapt (NPR-36998).

* Bij het maken van een vertaalproject leidt het cyclische verwijzen naar de pagina&#39;s tot een introductie die een fout oplevert (CQ-4332982).

* De koppeling Experience fragment in het vertaalde ervaringsfragment en de pagina bevat de startverwijzing (NPR-37649).

### Sling {#sling-65110}

* Wanneer het uploaden van een nieuw pakket, wordt de geheugenalias in de kaart MapEntifications verwijderd (NPR-37067).

### Workflow {#workflow-65110}

* `Deactivate` methode in `InboxOmniSearchHandler` geeft een null pointer-uitzondering weer (NPR-37533).

### [!DNL Communities] {#communities-65110}

* De gebruiker kan geen opmerking toevoegen aan de pagina, de `Post` De bewerking mislukt met foutcode 500 (NPR-37156).

* Wanneer het opstellen van de toepassing, wordt een segment niet gevonden uitzondering gezien toe te schrijven aan de lange lopende zitting van SyncManager (NPR-37351).

* De gebruiker kan de reacties op de forumdiscussiestuk (NPR-37083) niet zien.




<!--
Need to verify with Engineering, the status is currently showing as Resolved
-->


<!--
### [!DNL Brand Portal] {#brandportal-65110}

*

-->

### [!DNL Forms] {#forms-65110}


>[!NOTE]
>
>* [!DNL Experience Manager Forms] geeft toe:voegen-on pakketten één week na gepland vrij [!DNL Experience Manager] Releasedatum van Service Pack.


<!--

[!DNL AEM 6.5.10.0 Forms] includes the following bug fixes:

* When you install [!DNL AEM 6.5 Forms], the following third-party libraries are installed automatically (CQDOC-18373):
  * [!DNL Microsoft Visual C++ 2008 Service Pack 1 (x86)]
  * [!DNL Microsoft Visual C++ 2010 Service Pack 1 (x86)]

**Adaptive Forms**

* If the validations performed on the field values in an adaptive form are successful, [!DNL AEM Forms] fails to invoke the Form Data Model (CQ-4325491).

* When you add a language dictionary to a translation project and then open the project, [!DNL AEM Forms] displays an error message (CQ-4324933):

   ```TXT
   Uncaught TypeError: Cannot read property 'PROJECT_LISTING_PATH' of undefined
   at openButtonClickHandler (clientlibs.js:245)
   at HTMLButtonElement.onclick (clientlibs.js:258)

   ```

* Performance issues after installing [!DNL AEM Forms] Service Pack 7 (CQ-4326828).

* When you submit a form containing a standard HTML upload field from an Apple iOS device, sometimes, the content of the file is not sent and a 0-byte file is received at the other end. Apple iOS 15.1 provides a fix for the issue (CQ-4325361).

**Correspondence Management**

* Delay in the display of characters in the [!UICONTROL Data] tab as well as in the HTML letter preview (NPR-37020).

* When you are editing a text document fragment, the new words display as HTML tags after saving the fragment (NPR-36837).

* Unable to view the letters that are saved as drafts (NPR-36816).

* When you edit a text document fragment and then preview the letter, AEM Forms displays the expression language in the HTML letter preview (CQ-4322331).

* Issues while rendering data with a self-service letter template (NPR-37161).


**Interactive Communications**

* A tab character duplicates between two words each time you print preview an Interactive Communication after editing a text document fragment (NPR-37021).

* [!DNL AEM Forms] displays an error when you save a text document fragment that exceeds the maximum size limit (NPR-36874).

* When you add an image to an Interactive Communication, an additional empty block displays after the image (NPR-36659).

* When you select all text in an editor, you cannot change the font text to Arial (NPR-36646).

* When you create a URL in an editor and preview the changes, a black background displays instead of the URL text (NPR-36640).

* When you copy and paste text to an editor, there are issues while changing the font to Arial for bullets available in the document (NPR-36628). 

* Indentation issues for bullets in the text editor (NPR-36513).

**Designer**

* Screen Reader fails to read floating field data placed inside text label on the Master page or on Subform pages in a dynamic PDF (CQ-4321587).

**Document Services**

* When you convert XDP files to PDF files and then assemble the resultant PDF, the PDF generations fails and displays the following error message:

   ```TXT
   Caused by: com.adobe.fd.assembler.client.AssemblerException$ClientException: Document is in a disposed state!
   ```

**Forms Workflow**

* Unable to submit a form to a Workbench process after upgrading to AEM Forms Service Pack 8 (CQ-4325846).

**HTML5 Forms**

* When you set the value for the `mfAllowAttachments` property as `True` in the CRX DE repository, the `dataXml` gets corrupted on submitting the HTML5 form (NPR-37035).

* When you render an XDP as HTML using `dataXml`, [!DNL AEM Forms] displays a `Page Unresponsive` error (NPR-36631).

### Commerce {#commerce-65110}

* The value in the **[!UICONTROL Published By]** field displayed is incorrect in the Column view (NPR-36902).
* When a Catalog is rolled out, new products are incorrectly marked as modified products (NPR-36666).
* When you recreate a deleted product, the product page is not recreated (NPR-36665).
* Modified pages are updated but the corresponding linked products are not updated on Catalog rollout (CQ-4321409, NPR-36422).
* The **[!UICONTROL Publish later]** and **[!UICONTROL Unpublish later]** workflows do not work (CQ-4327679).

-->

Voor informatie over beveiligingsupdates raadpleegt u [[!DNL Experience Manager] beveiligingspagina met opsommingstekens](https://helpx.adobe.com/security/products/experience-manager.html).

## Installeer 6.5.11.0 {#install}

**Instellingsvereisten en meer informatie**

* Experience Manager 6.5.11.0 vereist Experience Manager 6.5. Zie [upgradedocumentatie](/help/sites-deploying/upgrade.md) voor gedetailleerde instructies.
* De download van het de dienstpak is beschikbaar op Adobe [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).
* Voor een plaatsing met MongoDB en veelvoudige instanties, installeer Experience Manager 6.5.11.0 op één van de instanties van de Auteur gebruikend de Manager van het Pakket.

>[!NOTE]
>
>Adobe raadt u niet aan de installatie van de [!DNL Adobe Experience Manager] 6.5.11.0-pakket.

### Het servicepack installeren {#install-service-pack}

Om het de dienstpak op een [!DNL Adobe Experience Manager] 6.5-instantie voert u de volgende stappen uit:

1. Start de instantie opnieuw vóór de installatie als de updatemodus voor de instantie is geactiveerd (wanneer de instantie is bijgewerkt vanaf een eerdere versie). Adobe raadt aan de toepassing opnieuw te starten als de huidige uptime voor een instantie hoog is.

1. Maak voordat u gaat installeren een momentopname of een nieuwe back-up van uw [!DNL Experience Manager] -instantie.

1. Download het servicepack van [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.11.zip).

1. Pakketbeheer openen en klikken **[!UICONTROL Upload Package]** om het pakket te uploaden. Zie voor meer informatie [Pakketbeheer](/help/sites-administering/package-manager.md).

1. Selecteer het pakket en klik op **[!UICONTROL Install]**.

1. Om de S3 schakelaar bij te werken, stop de instantie na installatie van het Service Pack, vervang de bestaande schakelaar met een nieuw binair dossier dat in de installatiemap wordt verstrekt, en begin de instantie opnieuw. Zie [Amazon S3 Data Store](/help/sites-deploying/data-store-config.md#upgrading-to-a-new-version-of-the-s-connector).

>[!NOTE]
>
>De dialoog over de Manager UI van het Pakket bestaat soms tijdens de installatie van het de dienstpak. Adobe raadt aan dat u op foutenlogboeken wacht om zich te stabiliseren alvorens tot de plaatsing toegang te hebben. Wacht op de specifieke logboeken met betrekking tot het verwijderen van de updaterbundel alvorens wordt verzekerd dat de installaties succesvol zijn. Typically, this issue occurs in [!DNL Safari] browser but can intermittently occur on any browser.

**Automatic installation**

Er zijn twee manieren om automatisch te installeren [!DNL Experience Manager] 6.5.11.0 op een werkexemplaar:

A. Plaats het pakket in `../crx-quickstart/install` als de server online beschikbaar is. Het pakket wordt automatisch geïnstalleerd.

B. Use the [HTTP API from Package Manager](/help/sites-administering/package-manager.md#package-share). Gebruiken `cmd=install&recursive=true` zodat de geneste pakketten worden geïnstalleerd.

>[!NOTE]
>
>Adobe Experience Manager 6.5.11.0 does not support Bootstrap installation.

**Validate the installation**

1. The product information page (`/system/console/productinfo`) displays the updated version string `Adobe Experience Manager (6.5.11.0)` under [!UICONTROL Installed Products].

1. All OSGi bundles are either **[!UICONTROL ACTIVE]** or **[!UICONTROL FRAGMENT]** in the OSGi Console (Use Web Console: `/system/console/bundles`).

1. De OSGi-bundel `org.apache.jackrabbit.oak-core` is versie 1.2.2.3 of hoger (Webconsole gebruiken: `/system/console/bundles`).

Als u wilt weten welke platformen gecertificeerd zijn voor deze release, raadpleegt u de [technische voorschriften](/help/sites-deploying/technical-requirements.md).

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

UberJar voor Experience Manager 6.5.11.0 is beschikbaar in [Maven Central-opslagplaats](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.5.11/).

Om UberJar in een Geweven project te gebruiken, zie [gebruiken van UberJar](/help/sites-developing/ht-projects-maven.md) en neem het volgende gebiedsdeel in uw project POM op:

```shell
<dependency>
     <groupId>com.adobe.aem</groupId>
     <artifactId>uber-jar</artifactId>
     <version>6.5.11</version>
     <scope>provided</scope>
</dependency>
```

>[!NOTE]
>
>UberJar en de andere verwante artefacten zijn beschikbaar op de Centrale Bewaarplaats van de Adobe Openbare Maven bewaarplaats (`repo.adobe.com`). The main UberJar file is renamed to `uber-jar-<version>.jar`. Er is dus geen `classifier`, met `apis` als de waarde voor de `dependency` tag.

## Verouderde functies {#removed-deprecated-features}

Hieronder vindt u een lijst met functies en mogelijkheden die zijn gemarkeerd als verouderd met [!DNL Experience Manager] 6.5.7.0. Functies worden in eerste instantie gemarkeerd als afgekeurd en in een toekomstige versie verwijderd. Er is een alternatieve optie opgegeven.

Herzie als u een eigenschap of een vermogen in een plaatsing gebruikt. Ook, ben van plan om de implementatie te veranderen om een afwisselende optie te gebruiken.

| Gebied | Functie | Vervanging |
|---|---|---|
| Integraties | De **[!UICONTROL AEM Cloud Services Opt-In]** het scherm is verouderd sinds [!DNL Experience Manager] en [!DNL Adobe Target] de integratie wordt bijgewerkt in Experience Manager 6.5. De integratie ondersteunt de Adobe Target Standard API. De API gebruikt verificatie via Adobe IMS en [!DNL Adobe I/O] en steunt de groeiende rol van Adobe Launch naar instrument [!DNL Experience Manager] De optiewizard is functioneel niet relevant op pagina&#39;s voor analyse en personalisatie. | Systeemverbindingen, Adobe IMS-verificatie en [!DNL Adobe I/O] integratie via de respectieve [!DNL Experience Manager] cloudservices. |
| Connectors | De Adobe JCR Connector voor Microsoft® SharePoint 2010 en Microsoft® SharePoint 2013 is afgekeurd voor Experience Manager 6.5. | N.v.t. |

## Bekende problemen {#known-issues}

* Wanneer u AEM 6.5 Service Pack 11 installeert en het ZIP-bestand met de status probeert te downloaden, downloadt Experience Manager een beschadigd bestand. Downloaden en installeren [AEM Sites SEO Index Package](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/sites-seo-index-content-1.0.0.zip) op uw AEM voordat het ZIP-bestand wordt gedownload om het probleem op te lossen.

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

## OSGi-bundels en inhoudspakketten inbegrepen {#osgi-bundles-and-content-packages-included}

De volgende tekstdocumenten maken een lijst van de bundels OSGi en de Pakketten van de Inhoud inbegrepen in [!DNL Experience Manager] 6.5.11.0:

* [Lijst van OSGi-bundels opgenomen in Experience Manager 6.5.11.0](assets/65110_bundles.txt)

* [Lijst met inhoudspakketten die zijn opgenomen in Experience Manager 6.5.11.0](assets/65110_packages.txt)

## Beperkte websites {#restricted-sites}

Deze websites zijn alleen beschikbaar voor klanten. Als u een klant bent en toegang nodig hebt, neemt u contact op met uw Adobe-accountmanager.

* [Productdownload op licensing.adobe.com](https://licensing.adobe.com/)
* Zie [hoe contact op te nemen met de Adobe Klantenondersteuning](https://experienceleague.adobe.com/docs/customer-one/using/home.html).

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] Opmerkingen bij de release 6.5](/help/release-notes/release-notes.md)
>* [[!DNL Experience Manager] productpagina](https://business.adobe.com/products/experience-manager/adobe-experience-manager.html)
>* [[!DNL Experience Manager] 6.5 Documentatie](https://experienceleague.adobe.com/docs/experience-manager-65.html)
>* [Abonneren op updates van prioritaire Adobe-producten](https://www.adobe.com/subscription/priority-product-update.html)

