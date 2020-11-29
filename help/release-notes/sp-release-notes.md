---
title: '[!DNL Adobe Experience Manager] 6.5 Opmerkingen bij de release Service Pack'
description: De nota's van de versie specifiek voor [!DNL Adobe Experience Manager] 6.5 Service Pack 7
docset: aem65
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: ed8299662139c2c2ab2fa304c9fa3448b0fce223
workflow-type: tm+mt
source-wordcount: '3696'
ht-degree: 0%

---


# [!DNL Adobe Experience Manager] 6.5 Opmerkingen bij de release Service Pack {#aem-service-pack-release-notes}

## Gegevens vrijgeven {#release-information}

| Producten | [!DNL Adobe Experience Manager] 6.5 |
| -------- | ---------------------------- |
| Versie | 6.5.7.0 |
| Type | Service Pack-release |
| Date | 26 november 2020 |
| URL downloaden | [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.7.zip) |

<!-- TBD: Update the SD link when SP7 is available. -->

## Wat is inbegrepen in [!DNL Adobe Experience Manager] 6.5.7.0 {#what-s-included-in-aem}

[!DNL Adobe Experience Manager] 6.5.7.0 is een belangrijke update die nieuwe eigenschappen, zeer belangrijke klant gevraagde verhogingen, en prestaties, stabiliteit, en veiligheidsverbeteringen omvat, die sinds de beschikbaarheid van 6.5 versie in April 2019 worden vrijgegeven. Het de dienstpak wordt geïnstalleerd op [!DNL Adobe Experience Manager] 6.5.

De belangrijkste kenmerken en verbeteringen die in [!DNL Adobe Experience Manager] 6.5.7.0 zijn geïntroduceerd, zijn:

* Pagina&#39;s van Live Copy die beschikbaar zijn voor rollout, worden gesorteerd met de eigenschappen [!UICONTROL Name], [!UICONTROL Last modified date,] en [!UICONTROL Last rollout date] .

* Als u de pagina uitvoert, worden de pagina verplaatst en MSM-rollouts als asynchrone bewerkingen uitgevoerd, zodat de runtime minder wordt belast met de prestaties.

* Gebruikers kunnen digitale elementen sorteren in de Kaart- en kolomweergave.

* [!DNL Assets] en [!DNL Dynamic Media] bieden meerdere toegankelijkheidsverbeteringen. De verbeteringen hebben betrekking op toetsenbordnavigatie, het gebruik van schermlezers en het inschakelen van gebruikers om vergelijkbare ondersteunende hulpmiddelen (AT) te gebruiken. Zie [[!DNL Assets] verbeteringen](#assets-6570) en [[!DNL Dynamic Media] verbeteringen](#dynamic-media-6570).

* De ingebouwde opslagplaats (Apache Jackrabbit Oak) wordt bijgewerkt naar versie 1.22.5.

Voor een volledige lijst van eigenschappen en verhogingen die in [!DNL Experience Manager] 6.5.7.0 worden geïntroduceerd, zie [wat in [!DNL Adobe Experience Manager] 6.5 Service Pack 7](new-features-latest-service-pack.md)nieuw is.

Hier volgt een lijst met oplossingen uit de release van [!DNL Experience Manager] 6.5.7.0.

### [!DNL Sites] {#sites-6570}

* Wanneer u de [!UICONTROL Timewrap] optie voor een pagina opent, de optie Regelpaneel aan de zijkant van de tijdlijn open houdt en naar [!UICONTROL Sites] console navigeert, treedt de `Failed to Load` fout op (NPR-34951).

* De [!UICONTROL Timewrap] optie geeft geen afbeeldingen weer voor het geselecteerde datum- en tijdbereik (NPR-34951).

* Wanneer een filter wordt aangeroepen `getHeader()` vanaf een pagina die een inhoudsfragment bevat, treedt de `java.lang.AbstractMethodError` fout op (NPR-34942).

* Wanneer het pad van een pagina meerdere subtekenreeksen voor inhoud bevat, kunnen voorvertoningen niet worden weergegeven en mislukt de functie Vergelijken van versie ook (NPR-34740).

* Wanneer u een numerieke waarde instelt voor de eigenschap `String` type label van een component, kunt u de component verwijderen en de verwijderbewerking ongedaan maken. Na het ongedaan maken van de verwijdering verandert de eigenschap label echter van `String` naar `Long` (NPR-34739).

* De volgende uitzondering geldt bij het toevoegen van een ervaringsfragment dat is gebaseerd op een sjabloon met een vergrendelde indeling aan een pagina (NPR-34632):

   ```TXT
   org.apache.sling.api.SlingException: Cannot get DefaultSlingScript: org.apache.sling.api.SlingException: Cannot get DefaultSlingScript: org.mozilla.javascript.EcmaError: TypeError: Cannot call method "getChildren" of null
   ```

* Wanneer u een map verplaatst, veroorzaakt dit traversale problemen en treedt de volgende fout op (NPR-34554):

   ```TXT
   org.apache.sling.api.SlingException: Cannot get DefaultSlingScript. org.apache.jackrabbit.oak.query.RuntimeNodeTraversalException: The query read or traversed more than 100000 nodes. To avoid affecting other tasks, processing was stopped
   ```

* Wanneer nieuwe elementen worden gemaakt, gepubliceerd en naar een nieuwe locatie worden verplaatst, wordt de `Request to complete move operation` workflow gemaakt en wordt de status Afgebroken weergegeven. Als u een nieuw element uploadt en een `move` bewerking uitvoert, wordt de `Request to complete move operation` workflow in de wachtrij gemaakt (NPR-34543).

* Wanneer u een fragment van de Ervaring van [!DNL Experience Manager] 6.5.2 milieu naar [!DNL Target] Norm uitvoert, ontbreekt de API vraag omdat het werkruimtebezit niet beschikbaar voor [!DNL Target] Norm (NPR-34557) is.

* Gebruikers kunnen geen pagina&#39;s publiceren via de [!UICONTROL manage publication] optie omdat de [!UICONTROL Publish] optie verdwijnt (NPR-34542).

* Wanneer u bepaalde stijlen aan de tekst toevoegt, wordt een `<div>` label aan de tekst toegevoegd en kan de stijl niet meer op de tekst worden toegepast (NPR-34531).

* Wanneer u een item in een pop-upmenu selecteert en de vereiste bestanden bijwerkt, is het niet toegestaan dialoogvensterwaarden op te slaan omdat het andere menu een leeg vereist veld heeft (NPR-34529).

* Wanneer u een pagina maakt op basis van een aangepaste sjabloon en deze verplaatst binnen de hiërarchie van de blauwdruk, worden componenten die eerder van de pagina zijn verwijderd, weergegeven op de pagina in de hiërarchie van de live kopie (NPR-34527).

* Wanneer een artikelstijl op een inhoud is toegepast, kan deze niet worden verwijderd (NPR-34486).

* Alle live kopieën en kopieën van een Experience Fragment verwijzen naar dezelfde [!DNL Adobe Target] aanbieding-id (NPR-34469).

* Lijstitems met opsommingstekens worden naast de genummerde lijst weergegeven (NPR-34455).

* De optie Vergelijken met bron geeft het verschil tussen de bronpagina en de bewerkte versie van een pagina niet aan (NPR-34285).

* Wanneer u een pagina schrapt, zijn de versiedetails niet configureerbaar (NPR-34159).

* Wanneer een gebruiker de [!UICONTROL Open Selection] dialoogoptie selecteert, wordt de toetsenbordfocus verplaatst naar het verborgen besturingselement op de pagina (CQ-4307779, CQ-4293601).

* Wanneer u een gepubliceerde map op de Auteur verplaatst, worden de mappaden niet overeenkomstig bijgewerkt in de instantie Publiceren (CQ-4305144).

* Wanneer een gebruiker de `Enter` toets op de [!UICONTROL Select All] optie selecteert, wordt de toetsenbordfocus niet naar de [!UICONTROL Create Control] optie verplaatst (CQ-4293599).

* Wanneer u de `Esc` toets selecteert, wordt de focus niet teruggezet naar het bovenliggende besturingselement (CQ-4293593, CQ-4293590).

* Verbeterde WCAG-compatibiliteit voor [!DNL Sites] UI- en Core-componenten (CQ-4293448).

* [!UICONTROL Zoom] en [!UICONTROL Scale] functies zijn uitgeschakeld voor de [!DNL Sites Editor] pagina (CQ-4282353).

* Nadat u de optie Rechtsom roteren hebt gebruikt, houdt de schermlezer op met commentaar voor de huidige rotatie- of spiegelstatus (CQ-4282128).

* De knoppen Gereed en Annuleren in het dialoogvenster Configureren hebben meerdere tabstops (CQ-4274601).

* Het verplaatsen van pagina&#39;s met een vergelijkbare naam op hetzelfde niveau is niet toegestaan (NPR-35041).

* Nadat u de optie Wissen (x) hebt geselecteerd, wordt de toetsenbordfocus niet naar het [!UICONTROL Filter] veld verplaatst (CQ-4293581).

* Wanneer u een upgrade uitvoert naar [!DNL Experience Manager] 6.5.6.0, verandert het gedrag van het overgeërfde alineasysteem en werkt het niet correct (NPR-35117).

* Toetsenbordgebruikers kunnen de tabfocus niet in de juiste volgorde verplaatsen nadat ze de [!UICONTROL Action] sectie op een [!DNL AEM Sites] pagina hebben geselecteerd (CQ-4307786).

* Nadat u een optie hebt geselecteerd in de vervolgkeuzelijst met koppelingsdoelen van de RTE-werkbalk tijdens het bewerken van een inhoudsfragment, wordt het dialoogvenster met de auteur van het inhoudsfragment geflickeerd (CQ-4305532).

* Toetsenbordgebruikers kunnen de opties in de [!UICONTROL Add Component] vervolgkeuzelijst niet selecteren met de toets Pijl-omlaag (CQ-4295097).

* De tabfocus verschuift niet in de juiste volgorde wanneer u een datum selecteert in het menu Kalender op het [!UICONTROL Assets] tabblad van een [!DNL Sites] pagina (CQ-4293600).

* De tabfocus verschuift niet naar de volgende of vorige opties voor toetsenbordgebruikers nadat de beschikbare opties voor Koppeling of Tekst zijn verwijderd tijdens het bewerken van een sitepagina (CQ-4293597).

* Toetsenbordgebruikers kunnen de tabfocus niet terugzetten naar Meer opties in de [!UICONTROL Actions] sectie nadat ze de beschikbare opties hebben bekeken en op de `Esc` toets hebben gedrukt (CQ-4293592).

* Wanneer u de [!UICONTROL Rotate] optie voor een afbeelding activeert in de [!UICONTROL Edit] modus, wordt de tabfocus in plaats van te blijven roteren verplaatst naar de [!UICONTROL Redo] optie voor de toetsenbordgebruikers (CQ-4293587).

* In het [!UICONTROL Open Selection] dialoogvenster dat beschikbaar is op het [!UICONTROL Link and Actions] tabblad, wordt de tabfocus verplaatst naar verborgen elementen op de pagina na de [!UICONTROL Cancel] optie (CQ-4293579).

* Wanneer gebruikers van het toetsenbord een afbeelding bewerken, naar de [!UICONTROL Finish] optie navigeren en op Enter drukken, wordt de voltooiing niet door de schermlezers aangekondigd (CQ-4282351).

* De opties Omhoog en Omlaag in het [!UICONTROL Link and Actions] dialoogvenster zijn niet beschikbaar voor schermlezers en toetsenbordgebruikers (CQ-4281120).

* Keyboard-gebruikers kunnen de tabfocus niet herstellen nadat ze naar de optie Close (X) op de [!UICONTROL Properties] pagina zijn genavigeerd (CQ-4293581, NPR-34653).

### [!DNL Assets] {#assets-6570}

[!DNL Adobe Experience Manager] 6.5.7.0 [!DNL Assets] verhelpt de volgende problemen en biedt de volgende verbeteringen.

* De volgende verbeteringen zijn aangebracht voor de toegankelijkheid in [!DNL Experience Manager Assets] deze release. Zie [toegankelijkheidsfuncties in [!DNL Assets]](/help/assets/accessibility.md)voor meer informatie.

   * Wanneer u met een toetsenbord door de tijdlijn navigeert, kan de `Esc` toets de [!UICONTROL Show All] optie samenvouwen zonder de focus te verliezen (CQ-4293598).
   * Wanneer u navigeert met de Tab-toets op het toetsenbord, behoudt het tagveld de focus nadat u de laatste tag uit de toegevoegde tags hebt verwijderd (NPR-35109).
   * [!DNL Experience Manager] De componenten bevatten nu de juiste informatie voor de naam, rol en waarde die door schermlezers moeten worden gebruikt (NPR-34255).
   * Nadat u de keuzelijst Type/Grootte, keuzelijst Koppeling, keuzelijst Taal of Tekstbewerking hebt verwijderd, keert de toetsenbordfocus terug naar de volgende of vorige gebruikersinterface-elementen of naar een relevanter gebruikersinterface-element (CQ-4293585).
   * Als u de aanwijzer op opties plaatst, worden er tips zoals Selecteren en Downloaden weergegeven. Gebruikers die een schermvergroting gebruiken, zien de miniaturen van het bestand mogelijk niet vanwege deze tips. Nu is het mogelijk om de focus te behouden nadat u de optie met `Escape` toets hebt verwijderd. (CQ-4293554).
   * Wanneer u een rastercel selecteert uit het raster dat aanwezig is op de pagina, wordt de focus verplaatst naar de actiebalk die wordt weergegeven op het scherm (CQ-4282127).
   * Visuele gebruikers kunnen onderscheid maken tussen normale tekst en een koppeling, aangezien visuele aanwijzingen (onderstreping en chevron-pictogram) worden weergegeven voor koppelingen naar alle oplossingen op de [!DNL Experience Manager] startpagina (CQ-4282072).

* De volgende gebruikerservaring wordt verbeterd in [!DNL Assets]:

   * Het sorteren van elementen in kaart- en kolomweergave inschakelen (NPR-35097).

* Als na de upgrade naar 6.5 een JSON-bestand wordt gegenereerd met de HTTP-API voor Middelen, zijn er problemen met de codering die in het bestand wordt gebruikt (NPR-35129).

* Gebruikers van een groep die niet de machtiging heeft gekregen om verzamelingen te maken (de optie Verzameling maken is niet beschikbaar), kunnen nog steeds verzamelingen maken door rechtstreeks toegang te krijgen tot de URL `https://[aem_server]:[port]/mnt/overlay/dam/gui/content/collections/createcollectionwizard.html/content/dam/collections?contentPath=/content/dam/collections` (NPR-35115).

* Wanneer gesorteerd op naam, worden de gezochte activa gesorteerd op case-sensitive manier. Hierdoor worden twee aparte gesorteerde lijsten gemaakt op basis van de trapsgewijze lijsten die op geordende wijze in de zoekresultaten worden weergegeven (NPR-35068).

* Wanneer een tevreden Fragment in de redacteur wordt geopend, worden de waarschuwingsberichten (`Invalid value specified for a metadata property`) het programma geopend in foutenlogboeken (NPR-35012).

* Gebruikers zonder beheerdersrechten kunnen verlopen middelen bewerken met de bureaubladtoepassing van de [Experience Manager] . (NPR-34993).

* Wanneer hetzelfde element in de gebruikersinterface van Elementen wordt gesleept en een nieuwe versie wordt gemaakt, zijn de wijzigingen in de metagegevens niet blijvend (NPR-34940).

* Bij het bewerken van verzamelingen kan een gebruiker de titel van de verzameling verwijderen en de wijzigingen opslaan (NPR-34889).

* Wanneer u een gedupliceerde afbeelding uploadt, wordt een verwijderingsoptie weergegeven. Als u Verwijderen selecteert, kunnen de afbeeldingen worden geüpload. DAM Update Asset workflow wordt ook geactiveerd (NPR-34744).

* Bij gebruik [!DNL Adobe Asset Link] met [!DNL Adobe InDesign]bevatten de zoekresultaten geen mappen en verzamelingen, maar alleen elementen (NPR-34699, CQ-4303666).

* Als u de aanwijzer op de kaartweergave plaatst, schuift het scherm als gevolg van (automatische) focus op de snelle acties die beschikbaar zijn op de kaart (NPR-34514).

* Als u de eigenschappen van meerdere elementen bulksgewijs bewerkt, wordt de weergave van de grote editor gesloten en wordt de hoofdpagina [!UICONTROL Save] [!DNL Assets] weergegeven. Dit gedrag is hetzelfde als het gedrag van [!UICONTROL Save & Close] optie en wordt niet verwacht (NPR-34546).

* De slimme verzameling bevat na het opslaan niet de juiste instelling voor de gebruikersinterface. De vraag wordt bewaard behoorlijk maar de interface toont altijd de laatste toegevoegde predikaat van de Optie (NPR-34539).

* Wanneer u elementen toevoegt aan [!DNL Experience Manager], worden de metagegevens zonder naamruimte niet geïmporteerd (NPR-34530).

* Wanneer u middelen naar een map sleept om deze te verplaatsen, wordt in de gebruikersinterface ook de optie voor [!UICONTROL Drop in Lightbox] en [!UICONTROL Drop in Collection]. Zelfs als de verplaatsingsbewerking wordt geannuleerd, worden in de gebruikersinterface de laatste twee opties weergegeven (NPR-34526).

* Het symbool `%>` wordt weergegeven op de pagina Verzamelingen (NPR-34499).

* In de kolomweergave worden dubbele map- en elementnamen weergegeven wanneer naar boven en naar beneden wordt geschoven voordat alle elementen worden weergegeven (NPR-34464). [!DNL Assets]

* Als u direct na het maken van een openbare map een privémap maakt, worden in de openbare map de instellingen voor de privémap gebruikt (NPR-34415).

* In de kaartweergave worden de kaarten niet in alfabetische volgorde weergegeven en kunnen kaarten niet alfabetisch worden gesorteerd (NPR-34234).

* Bij het opnieuw openen van trapsgewijze regels blijven de opties niet behouden in de gebruikersinterface (CQ-4301452).

#### [!DNL Dynamic Media] {#dynamic-media-6570}

* De volgende verbeteringen zijn aangebracht op het gebied van toegankelijkheid in [!DNL Dynamic Media] (CQ-4290306). Zie [toegankelijkheidsfuncties in [!DNL Dynamic Media]](/help/assets/accessibility-dm.md)voor meer informatie.

   * Schermlezers (JAWS, Narrator) vertellen de naam, rol en status van de menu-items in de menuoptie Grootte insluiten (CQ-4290927).
   * Gebruikers kunnen met de `Tab` toets navigeren in het dialoogvenster E-mailkoppeling (CQ-4290926).
   * De workflow voor het maken van videocoderingsprofielen is gebruiksvriendelijker gezien de schermlezerverbetering (CQ-4290623, CQ-4290622).
   * Wanneer u navigeert met behulp van `Tab` toets, gaat de focus naar de juiste gebruikersinterface-elementen in de workflow om een interactieve video te maken (CQ-4290621, CQ-4290620, CQ-4290619).
   * De pagina Publiceren, Asset-pagina bewerken, Smart Crops bewerken en de pagina Editor afbeeldingsset zijn verbeterd en voldoen nu aan de webstandaarden. Gebruikers van ondersteunende technologie (AT) kunnen nu gemakkelijk door deze pagina&#39;s navigeren en acties uitvoeren zoals het bijsnijden van afbeeldingen (CQ-4290617, CQ-4290616, CQ-4290613, CQ-4290612, CQ-49) 0610, CQ-4290614).
   * Gebruikers kunnen nu beter navigeren met een toetsenbord (CQ-4290615).
   * Gebruikers van het toetsenbord en de schermlezer kunnen de uitsnijdfunctionaliteit gebruiken (CQ-4290609).
   * Gebruikers met het toetsenbord kunnen de hotspots beter beheren (CQ-4290604, CQ-4290603).

* Externe afbeeldingen kunnen niet worden bewerkt [!DNL Experience Manager] als de bedrijfsnaam en mapnaam gelijk zijn (NPR-31340).

* De z-indexvolgorde is onjuist wanneer u de uitvoer probeert voor te vertonen nadat u een hotspot aan een [!DNL Dynamic Media] afbeelding hebt toegevoegd of nadat u een [!DNL Dynamic Media] video of een video [!DNL Experience Fragment] met een afbeelding hebt bewerkt (CQ-4307267).

* [!DNL Dynamic Media] sync mislukt wanneer gemengde mediasets opnieuw worden verwerkt (CQ-4307184).

* Als een element wordt verplaatst naar een map waarin automatische synchronisatie [!DNL Dynamic Media] is geconfigureerd, wordt het element niet gesynchroniseerd (CQ-4307122).

* [!DNL Dynamic Media] video wordt niet afgespeeld op iOS-apparaten met de native HTML5-videobesturingselementen (CQ-4306977, CQ-4306727).

* Kan geen afbeeldingen downloaden waarop SmartCrop is toegepast (CQ-4304558).

* Kan mappen niet selectief publiceren naar dynamische media (CQ-4304526).

* Als u de publicatie van een videobestand ongedaan maakt, wordt de publicatie van de Adaptive Video Set op basis van een geconfigureerde Scene7-implementatie [!DNL Experience Manager] niet ongedaan gemaakt (CQ-4304405).

* Als u een panoramisch afbeeldingselement toevoegt aan een panoramisch mediacomponent en de pagina vernieuwt, treedt een `Uncaught ReferenceError: $ is not defined` fout op (CQ-4302810).

* In [!UICONTROL Viewer Presets Editor], wanneer het uitgeven vooraf ingesteld, in de [!UICONTROL PanoramicImage/PanoramicImage_VR] component, is het `PanoramicView` `PANORAMICVIEW_AUTOROTATE` modifier etiket niet beschikbaar (CQ-4302443).

* Videobijschriften worden niet weergegeven als de video niet de eerste is in een MixedMediaSet (CQ-4298161).

* HTML5 eCatalog Viewer op mobiele apparaten met iPhones kan de pagina&#39;s niet draaien of de pagina&#39;s omdraaien (CQ-4296611).

* Wanneer u stalen op een mobiel apparaat schuift, schuiven de stalen naar rechts en uit het zichtbare gebied gedurende een paar seconden voordat u weer in beeld bladert (CQ-4296439).

* Wanneer een Voorinstelling voor viewer Master record wordt gemaakt, worden de CSS en de illustraties niet gepubliceerd en wordt alleen de voorinstelling voor viewers gepubliceerd (CQ-4262205).

* Wanneer u een ervaringsfragment probeert te koppelen voor een bepaalde hotspot in de [!UICONTROL Interactive Video/Images] component, wordt het geselecteerde pad van het ervaringsfragment niet weergegeven. In plaats daarvan wordt een lege waarde vanuit het padveld geretourneerd (NPR-35146, CQ-4298136).

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
* De `AudienceOmniSearchHandler` functie gebruikt een afgekeurde index (NPR-34870).
* Afmelden bij Experience Manager wist de cookies niet (NPR-34743).
* De `findByTitle` functie van de `TagManager` API werkt niet als de tagnaam een speciaal teken bevat (NPR-34357).
* Het proces voor het importeren van het synchronisatiepakket van de gebruiker mislukt (NPR-34399).
* Extra ondersteuning voor `ariaLabel` en `ariaLabelledby` eigenschappen van de `Coral.Masonry` component (GRANITE-29962).
* De Dispatcher-cache wordt niet vernieuwd voor pagina&#39;s met inhoudsfragmenten nadat de nieuwste kerncomponentpakketten zijn geïnstalleerd (CQ-4306788).
* Gelokaliseerde tagnamen met aanhalingstekens (`"`) worden niet correct weergegeven in de gebruikersinterface (CQ-4305439).

### User Interface {#ui-6570}

* Het [!UICONTROL Link to] veld in componenteigenschappen bevat suggesties voor automatisch aanvullen die niet overeenkomen met de opgegeven tekenreeks (NPR-34865).

* AEM geeft het volgende foutbericht weer wanneer u een dagelijks onderhoudvenster plant dat tussen twee dagen wordt verdeeld (NPR-35280):

   ```TXT
   ERROR The start time must precede (be less than) the end time
   ```

### Integrations {#integrations-6570}

* Het bewerken van een bestaande [!DNL Adobe Launch] configuratie mislukt (NPR-35045).
* Kan niet exporteren [!DNL Experience Fragments] naar [!DNL Adobe Target] indien IMS-configuratie en - [!DNL Adobe Target Standard] omgeving wordt gebruikt (NPR-34555).
* De [!UICONTROL Create] optie wordt weergegeven op de [!UICONTROL Audiences] pagina bij het navigeren van een map naar de [!UICONTROL Audiences] pagina (NPR-35151).

### Sling {#sling-6570}

* De standaardlogin gezondheidscontrole bevestigt de geloofsbrieven van een gebruiker die niet bestaat (NPR-34686).

### Omzettingsprojecten {#translation-6570}

* Bij het annuleren van een vertaalproject in [!DNL Experience Manager]wordt het verzoek tot annulering niet naar de vertaalprovider gezonden (NPR-34433).

### [!DNL Communities] {#communities-6570}

* Alle gevallen van onbillijke terminologie in het product worden vervangen door aanvaarde equivalenten (NPR-34311).
* [!DNL Google+] wordt verwijderd uit de lijst van opties voor sociale media (NPR-33877).

### [!DNL Brand Portal] {#brandportal-6570}

* De gebruikersinterface reageert niet bij het selecteren van de middelen in de [!UICONTROL List View] (NPR-34728).

### [!DNL Forms] {#forms-6570}

>[!NOTE]
>
>[!DNL Experience Manager Forms] geeft toe:voegen-op pakketten één week na de geplande de versiedatum van het [!DNL Experience Manager] Service Pack vrij.

Voor informatie over veiligheidsupdates, zie de pagina [van bulletins van de](https://helpx.adobe.com/security/products/experience-manager.html)Experience Manager veiligheid.

## Installeer 6.5.7.0 {#install}

**Instellingsvereisten en meer informatie**

* AEM 6.5.7.0 vereist AEM 6.5. Zie [upgradedocumentatie](/help/sites-deploying/upgrade.md) voor gedetailleerde instructies.
* De download van het de dienstpak is beschikbaar op de Distributie [van de](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)Software van Adobe.
* Voor een plaatsing met MongoDB en veelvoudige instanties, installeer AEM 6.5.7.0 op één van de instanties van de Auteur gebruikend de Manager van het Pakket.

>[!NOTE]
>
>Adobe raadt u niet aan het pakket [!DNL Adobe Experience Manager] 6.5.7.0 te verwijderen of te verwijderen.

### Het Service Pack installeren {#install-service-pack}

Voer de volgende stappen uit om het Service Pack op een bestaande Adobe Experience Manager 6.5-instantie te installeren:

1. Start de instantie opnieuw vóór de installatie als de updatemodus voor de instantie is geactiveerd (dit is het geval wanneer de instantie is bijgewerkt vanaf een eerdere versie). Adobe raadt ook aan de toepassing opnieuw te starten als de huidige uptime voor een instantie hoog is.

1. Maak voordat u gaat installeren een momentopname of een nieuwe back-up van de [Experience Manager] -instantie.

1. Download het de dienstpak van de Distributie van de [Software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.7.zip).

1. Open Package Manager en klik **[!UICONTROL Upload Package]** om het pakket te uploaden. Zie [Pakketbeheer](/help/sites-administering/package-manager.md)voor meer informatie.

1. Selecteer het pakket en klik **[!UICONTROL Install]**.

1. Om de S3 schakelaar bij te werken, stop de instantie na installatie van het Service Pack, vervang de bestaande schakelaar met een nieuw binair dossier dat in de installatiemap wordt verstrekt, en begin de instantie opnieuw. Zie [Amazon S3 Data Store](/help/sites-deploying/data-store-config.md#upgrading-to-a-new-version-of-the-s-connector).

>[!NOTE]
>
>De dialoog over de Manager UI van het Pakket bestaat soms tijdens de installatie van het de dienstpak. Adobe raadt aan dat u op foutenlogboeken wacht om zich te stabiliseren alvorens tot de plaatsing toegang te hebben. Wacht op de specifieke logboeken met betrekking tot het verwijderen van de updaterbundel alvorens wordt verzekerd dat de installaties succesvol zijn. Dit gebeurt meestal op, [!DNL Safari] maar kan soms gebeuren in elke browser.

**Automatische installatie**

Er zijn twee manieren om Adobe Experience Manager 6.5.7.0 automatisch op een werkexemplaar te installeren:

A. Plaats het pakket in de `../crx-quickstart/install` map wanneer de server online beschikbaar is. Het pakket wordt automatisch geïnstalleerd.

B. Gebruik de [HTTP-API van Package Manager](https://docs.adobe.com/content/docs/en/crx/2-3/how_to/package_manager.html). Gebruik deze optie `cmd=install&recursive=true` om de geneste pakketten te installeren.

>[!NOTE]
>
>Adobe Experience Manager 6.5.7.0 biedt geen ondersteuning voor Bootstrap-installatie.

**Installatie valideren**

1. Op de pagina met productinformatie (`/system/console/productinfo`) wordt de bijgewerkte versietekenreeks `Adobe Experience Manager (6.5.7.0)` onder weergegeven [!UICONTROL Installed Products].

1. Alle bundels OSGi zijn of **[!UICONTROL ACTIVE]** of **[!UICONTROL FRAGMENT]** in de Console OSGi (de Console van het Web van het Gebruik: `/system/console/bundles`).

1. De bundel OSGi `org.apache.jackrabbit.oak-core` is versie 1.22.3 of later (de Console van het Web van het Gebruik: `/system/console/bundles`).

Zie de [technische vereisten](/help/sites-deploying/technical-requirements.md)voor informatie over de platforms die zijn gecertificeerd voor deze release.

### Adobe Experience Manager Forms-invoegtoepassing installeren {#install-aem-forms-add-on-package}

>[!NOTE]
>
>[!DNL Experience Manager Forms] geeft toe:voegen-op pakketten één week na de geplande de versiedatum van het [!DNL Experience Manager] Service Pack vrij.

>[!NOTE]
>
>Sla dit over als u AEM Forms niet gebruikt. Correcties in Adobe Experience Manager Forms worden geleverd via een afzonderlijk invoegpakket.

1. Controleer of u het Adobe Experience Manager Service Pack hebt geïnstalleerd.
1. Download het overeenkomstige Forms add-on pakket dat in [AEM Forms-releases](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) voor uw besturingssysteem wordt vermeld.
1. Installeer het invoegpakket voor Forms zoals beschreven in de [invoegtoepassing](../forms/using/installing-configuring-aem-forms-osgi.md#install-aem-forms-add-on-package)voor AEM Forms installeren.

### Adobe Experience Manager Forms installeren op JEE {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Sla dit over als u AEM Forms niet gebruikt op JEE. Correcties in Adobe Experience Manager Forms op JEE worden via een afzonderlijk installatieprogramma geleverd.

Voor informatie over het installeren van het cumulatieve installatieprogramma voor Experience Manager Forms op JEE en configuratie na de implementatie, zie de [versienota&#39;s](jee-patch-installer-65.md).

### UberJar {#uber-jar}

UberJar voor Experience Manager 6.5.7.0 is beschikbaar in de [Centrale bewaarplaats](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.5.7/)van Maven.

Om UberJar in een Geweven project te gebruiken, zie [hoe te UberJar](/help/sites-developing/ht-projects-maven.md) gebruiken en omvat het volgende gebiedsdeel in uw projectPOM:

```shell
<dependency>
     <groupId>com.adobe.aem</groupId>
     <artifactId>uber-jar</artifactId>
     <version>6.5.7</version>
     <scope>provided</scope>
</dependency>
```

>[!NOTE]
>
>UberJar en de andere verwante artefacten zijn beschikbaar op Maven Central Repository in plaats van Adobe Public Maven repository (`repo.adobe.com`). De naam van het hoofdbestand van UberJar wordt gewijzigd in `uber-jar-<version>.jar`. Er is dus geen `classifier`, met `apis` als waarde, voor de `dependency` tag.

## Deprecated features {#removed-deprecated-features}

Hieronder vindt u een lijst met functies en mogelijkheden die zijn gemarkeerd als verouderd in [!DNL Experience Manager] 6.5.7.0. Functies worden in eerste instantie gemarkeerd als afgekeurd en in een toekomstige versie verwijderd. Een alternatieve optie wordt gewoonlijk verstrekt.

Herzie als u een eigenschap of een vermogen in een plaatsing gebruikt. Ook, ben van plan om de implementatie te veranderen om een afwisselende optie te gebruiken.

| Gebied | Functie | Vervanging |
|---|---|---|
| Integrations | Het **[!UICONTROL AEM Cloud Services Opt-In]** scherm is afgekeurd. Met de integratie van de AEM en van het Doel in AEM 6.5 wordt bijgewerkt om de Standaard API van het Doel te steunen, die authentificatie via Adobe IMS en I/O gebruikt, en de groeiende rol van de Lancering van de Adobe voor het van instrumenten voorzien van AEM pagina&#39;s voor analyse en verpersoonlijking, is de Opt-In tovenaar functioneel irrelevant geworden. | Configureer systeemverbindingen, Adobe IMS-verificatie en Adobe I/O-integratie via de respectievelijke AEM-cloudservices. |
| Connectors | De Adobe JCR-connector voor Microsoft SharePoint 2010 en Microsoft SharePoint 2013 is vervangen door AEM 6.5. | N.v.t. |

## Known issues {#known-issues}

* Negeer de volgende fouten in het `error.log` bestand tijdens de installatie van Experience Manager 6.5.7.0:

   ```TXT
   com.day.cq.dam.cq-dam-core bundle com.day.cq.dam.cq-dam-core:5.12.276 (331)[com.day.cq.dam.core.impl.collection.CollectionCreationListenerDummy] :  Cannot register component (org.osgi.service.component.ComponentException: The component name 'com.day.cq.dam.core.impl.collection.CollectionCreationListenerDummy' has already been registered by Bundle 331 (com.day.cq.dam.cq-dam-core) as Component of Class com.day.cq.dam.core.impl.collection.CollectionCreationListenerDummy)
   
   com.day.cq.dam.cq-dam-core bundle com.day.cq.dam.cq-dam-core:5.12.276 (331)[com.day.cq.dam.core.impl.team.MediaPortalShareHandlerDummy(1314)] : Could not load implementation object class com.day.cq.dam.core.impl.team.MediaPortalShareHandlerDummy (java.lang.ClassNotFoundException: com.day.cq.dam.core.impl.team.MediaPortalShareHandlerDummy not found by com.day.cq.dam.cq-dam-core [331])
   
   com.day.cq.dam.cq-dam-core bundle com.day.cq.dam.cq-dam-core:5.12.276 (331)[com.day.cq.dam.core.impl.collection.CollectionCreationListenerDummy(1316)] : Could not load implementation object class com.day.cq.dam.core.impl.collection.CollectionCreationListenerDummy (java.lang.ClassNotFoundException: com.day.cq.dam.core.impl.collection.CollectionCreationListenerDummy not found by com.day.cq.dam.cq-dam-core [331])
   
   com.day.cq.dam.cq-dam-core bundle com.day.cq.dam.cq-dam-core:5.12.276 (331)[com.day.cq.dam.core.impl.team.MediaPortaltRoleProviderDummy(1315)] : Could not load implementation object class com.day.cq.dam.core.impl.team.MediaPortaltRoleProviderDummy (java.lang.ClassNotFoundException: com.day.cq.dam.core.impl.team.MediaPortaltRoleProviderDummy not found by com.day.cq.dam.cq-dam-core [331])
   
   com.day.cq.dam.cq-dam-core bundle com.day.cq.dam.cq-dam-core:5.12.276 (331)BundleComponentActivator : Unexpected failure enabling component holder com.day.cq.dam.core.impl.collection.CollectionCreationListenerDummy (java.lang.IllegalStateException: Could not load implementation object class com.day.cq.dam.core.impl.collection.CollectionCreationListenerDummy)
   
   com.day.cq.dam.cq-dam-core bundle com.day.cq.dam.cq-dam-core:5.12.276 (331)BundleComponentActivator : Unexpected failure enabling component holder com.day.cq.dam.core.impl.team.MediaPortaltRoleProviderDummy (java.lang.IllegalStateException: Could not load implementation object class com.day.cq.dam.core.impl.team.MediaPortaltRoleProviderDummy)
   
   com.day.cq.dam.cq-dam-core bundle com.day.cq.dam.cq-dam-core:5.12.276 (331)[com.day.cq.dam.core.impl.team.MediaPortaltRoleProviderDummy] :  Cannot register component (org.osgi.service.component.ComponentException: The component name 'com.day.cq.dam.core.impl.team.MediaPortaltRoleProviderDummy' has already been registered by Bundle 331 (com.day.cq.dam.cq-dam-core) as Component of Class com.day.cq.dam.core.impl.team.MediaPortaltRoleProviderDummy)
   
   com.day.cq.dam.cq-dam-core bundle com.day.cq.dam.cq-dam-core:5.12.276 (331)[com.day.cq.dam.core.impl.team.MediaPortalShareHandlerDummy] :  Cannot register component (org.osgi.service.component.ComponentException: The component name 'com.day.cq.dam.core.impl.team.MediaPortalShareHandlerDummy' has already been registered by Bundle 331 (com.day.cq.dam.cq-dam-core) as Component of Class com.day.cq.dam.core.impl.team.MediaPortalShareHandlerDummy)
   
   com.day.cq.dam.cq-dam-core bundle com.day.cq.dam.cq-dam-core:5.12.276 (331)BundleComponentActivator : Unexpected failure enabling component holder com.day.cq.dam.core.impl.team.MediaPortalShareHandlerDummy (java.lang.IllegalStateException: Could not load implementation object class com.day.cq.dam.core.impl.team.MediaPortalShareHandlerDummy)
   ```

* Als u een upgrade uitvoert van uw [!DNL Experience Manager] instantie van versie 6.5 tot versie 6.5.7.0, kunt u uitzonderingen weergeven in het `RRD4JReporter` `error.log` bestand. Start de instantie opnieuw om het probleem op te lossen.

* Als u [!DNL Experience Manager] 6.5 Service Pack 5 of een vorig de dienstpak op [!DNL Experience Manager] 6.5 installeert, wordt het runtime exemplaar van uw activa aangepaste werkschemamodel (gecreeerd in `/var/workflow/models/dam`) geschrapt.
Om uw runtime exemplaar terug te winnen, adviseert Adobe om het ontwerp-tijd exemplaar van het model van het douanewerkschema met zijn runtime exemplaar te synchroniseren gebruikend HTTP API:
   `<designModelPath>/jcr:content.generate.json`.

* Neem contact op met de klantenservice van Adobe als u problemen ondervindt bij het bewerken en maken van trapsgewijze regels in [!UICONTROL Folder Metadata Schema Forms Editor] en [!UICONTROL Metadata Schema Forms Editor] via het [!UICONTROL Define Rule] dialoogvenster. De regels die al zijn gemaakt en opgeslagen, werken zoals u had verwacht.

* Als de naam van een map in de hiërarchie wordt gewijzigd [!DNL Experience Manager Assets] en de geneste map met een element wordt gepubliceerd naar [!DNL Brand Portal], wordt de titel van de map pas bijgewerkt [!DNL Brand Portal] als de hoofdmap opnieuw wordt gepubliceerd.

* Wanneer een gebruiker een veld voor het eerst in een adaptief formulier configureert, wordt de optie voor het opslaan van een configuratie niet weergegeven in de eigenschappenbrowser. Als u een ander veld van het adaptieve formulier in dezelfde editor selecteert, wordt het probleem opgelost.

* Als de [!UICONTROL Connected assets configuration] tovenaar een 404 foutenmelding na installatie terugkeert, installeer manueel de `cq-remotedam-client-ui-content` en de `cq-remotedam-client-ui-components` pakketten opnieuw gebruikend de Manager van het Pakket.

* De volgende fouten en waarschuwingsberichten kunnen tijdens de installatie van AEM 6.5.x.x worden weergegeven:
   * &quot;Wanneer de integratie van het Doel in AEM gebruikend StandaardAPI van het Doel (authentificatie IMS) wordt gevormd, dan leidt het uitvoeren van de Fragmenten van de Ervaring naar Doel in verkeerde aanbiedingstypes die worden gecreeerd. In plaats van het type &quot;Experience Fragment&quot;/bron &quot;Adobe Experience Manager&quot; maakt Target verschillende aanbiedingen met het type &quot;HTML&quot;/source &quot;Adobe Target Classic&quot;.
   * `com.adobe.granite.maintenance.impl.TaskScheduler`: Geen onderhoudsvensters gevonden bij graniet/bediening/onderhoud.
   * De adaptieve servervalidatie van het formulier mislukt wanneer statistische functies zoals SUM, MAX en MIN worden gebruikt. CQ-4274424
   * `com.adobe.granite.maintenance.impl.TaskScheduler` - Geen onderhoudsvensters gevonden bij graniet/bediening/onderhoud.
   * Hotspot in een interactieve afbeelding voor dynamische media is niet zichtbaar wanneer u een voorvertoning van het element weergeeft via de Shopable Banner-viewer.

## OSGi-bundels en inhoudspakketten inbegrepen {#osgi-bundles-and-content-packages-included}

De volgende tekstdocumenten maken een lijst van de bundels OSGi en de Pakketten van de Inhoud inbegrepen in AEM 6.5.7.0:

* [Lijst van OSGi-bundels opgenomen in AEM 6.5.7.0](assets/6570_bundles.txt)

* [Lijst met inhoudspakketten die zijn opgenomen in AEM 6.5.7.0](assets/6570_packages.txt)

## Beperkte websites {#restricted-sites}

Deze websites zijn alleen beschikbaar voor klanten. Als u een klant bent en toegang nodig hebt, neemt u contact op met uw Adobe-accountmanager.

* [Productdownload op licensing.adobe.com](https://licensing.adobe.com/)
* Zie [hoe u contact opneemt met de klantenondersteuning](https://experienceleague.adobe.com/docs/customer-one/using/home.html).

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] Opmerkingen bij de release 6.5](/help/release-notes/release-notes.md)
>* [[!DNL Experience Manager] productpagina](https://www.adobe.com/marketing/experience-manager.html)
>* [[!DNL Experience Manager] 6.5 Documentatie](https://experienceleague.adobe.com/docs/experience-manager-65.html)
>* Abonneren op [Adobe-productupdates met prioriteit](https://www.adobe.com/subscription/priority-product-update.html)

