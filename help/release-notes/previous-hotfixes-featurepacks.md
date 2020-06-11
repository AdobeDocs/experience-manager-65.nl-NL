---
title: Opmerkingen bij de release Adobe Experience Manager 6.5 Vorige Service Pack
description: Opmerkingen bij de release specifiek voor Adobe Experience Manager 6.5 Service Pack 3 en eerder.
contentOwner: AK
translation-type: tm+mt
source-git-commit: b2b8178f96d1e0a551a58ba649443aa03f0608ac
workflow-type: tm+mt
source-wordcount: '8084'
ht-degree: 0%

---


# Hotfixes en de Pakken van de Eigenschap inbegrepen in vorige Packs van de Dienst {#hotfixes-and-feature-packs-included-in-previous-service-packs}

## Adobe Experience Manager 6.5.4.0 {#experience-manager-6540}

Adobe Experience Manager 6.5.4.0 is een belangrijke update met nieuwe functies, belangrijke verbeteringen en prestaties die door de klant zijn aangevraagd, stabiliteit en verbeteringen op het gebied van beveiliging, die zijn uitgebracht sinds de algemene beschikbaarheid van de release van 6.5 in **april 2019**. Deze kan boven op Adobe Experience Manager 6.5 worden geïnstalleerd.

Enkele belangrijke functies en verbeteringen in Adobe Experience Manager 6.5.4.0 zijn:

* Adobe Experience Manager-middelen zijn nu geconfigureerd met Brand Portal via Adobe I/O Console.

* Er is nu een nieuwe stap Afdrukbare uitvoer [](../forms/using/aem-forms-workflow-step-reference.md) genereren beschikbaar voor Adobe Experience Manager Forms-workflows.

* [Ondersteuning](../forms/using/resize-using-layout-mode.md) voor meerdere kolommen in de lay-outmodus voor adaptieve formulieren en interactieve communicatie.

* Ondersteuning voor [RTF](../forms/using/designing-form-template.md) -bestanden in HTML5-formulieren.

* [Verbeterde](new-features-latest-service-pack.md#accessibility-enhancements) toegankelijkheid in de middelen van Experience Manager.

* De ingebouwde opslagplaats (Apache Jackrabbit Oak) wordt bijgewerkt naar versie 1.10.8.

* U kunt selectieve inhoudsubstructuren nu synchroniseren met *Dynamische Media - wijze* Scene7 in plaats van alle beschikbare bij `content/dam`.

* Integratie van formuliergegevensmodellen met SOAP-webservice ondersteunt nu keuzegroepen of kenmerken voor elementen.

* De invoer of de output van de ZEEP en complexe gegevensstructuren steunen nu Dynamische Vervanging van de Groep.

Voor een volledige lijst van eigenschappen en belangrijkste hoogtepunten die in de recentste de dienstpakken worden geïntroduceerd, zie [Nieuw in de dienstpakken](new-features-latest-service-pack.md)van de Manager van de Ervaring van Adobe 6.5.

### Sites {#sites-fixes}

* Wanneer een URL van een pagina met Adobe Experience Manager-sites een dubbele punt (`:`) of percentagesymbool (`%`) bevat, reageert de browser niet meer en geven CPU-gebruiksspecificaties niet meer door (NPR-32369, NPR-31918).

* Wanneer een pagina van de Plaatsen van het Manager van de Ervaring voor het uitgeven en een component wordt geopend, blijft de deegactie voor sommige placeholders (NPR-32317) niet beschikbaar.

* Wanneer de wizard Publicatie beheren wordt geopend, wordt een ervaringsfragment dat is gekoppeld aan een kerncomponent niet weergegeven in de lijsten met gepubliceerde referenties (NPR-32233).

* Het overzicht van live kopieën in Touch UI duurt veel langer dan de klassieke interface die wordt weergegeven (NPR-32149).

* Wanneer de server-tijd en machine-tijd in verschillende tijdzones zijn, toont de geplande publicatietijd servertijd in Touch UI, terwijl in Klassieke UI, machinetijd wordt getoond (NPR-32077).

* Experience Manager Sites kan geen pagina openen met een achtervoegsel in de URL (NPR-32072).

* Wanneer een gebruiker een inhoudsfragment bewerkt, wordt een verwijderde variant van het inhoudsfragment hersteld (NPR-32062).

* Gebruikers mogen een inhoudsfragment opslaan zonder informatie op te geven in de vereiste velden (NPR-31988).

* kernel.js en ui.js worden niet vooraf in acht genomen of in cache geplaatst. Het leidt tot extra tijd bij het teruggeven van pagina&#39;s (NPR-31891).

* Wanneer PageEventAuditListener wordt toegelaten, breidt de lengte van toe verbindt rij. Het beïnvloedt de prestaties van vele verrichtingen zoals bulkpublicaties, navigatie, bulkactivabeweging (NPR-31890).

* Wanneer de Fragmenten van de Ervaring worden gesleept, wordt de hoge reactietijd waargenomen (NPR-31878).

* Wanneer u de component van de Belemmering hier optie in ontvankelijke placeholder van het net selecteert, wordt een GET verzoek verzonden en het verzoek resulteert in HTTP 403 fout (NPR-31845).

* Wanneer u de inhoud binnen dezelfde map verplaatst, is de optie Pagina verplaatsen uitgeschakeld (NPR-31840).

* In de bewerkbare sjabloonstructuurmodus worden in de lijst met toegestane componenten in de lay-outcontainer onjuiste resultaten weergegeven. Alleen componenten met een dialoogvenster voor ontwerpen worden weergegeven in de lay-outcontainer (NPR-31816).

* Wanneer een pagina alleen-lezen toestemmingen voor een gebruiker heeft, is de Open eigenschappen optie zichtbaar in sites.html maar niet in editor.html (NPR-31770).

* Wanneer een gebruiker op de knop Maken klikt, is de pagina-optie niet beschikbaar (NPR-31756).

* Kan de campagne in de Adobe-campagne niet synchroniseren met de ontwerpimportcomponent OOTB (Out of the box) (NPR-31728).

* Wanneer u een lijst met opsommingstekens probeert te wijzigen in een genummerde lijst, worden alleen de eerste twee items van de lijst gewijzigd (NPR-31636).

* Wanneer een pagina niet-geschreven is en het onderliggende knooppunt is geselecteerd, wordt in het dialoogvenster Selecteren nog steeds het eerste knooppunt weergegeven. Wanneer de pagina is geschreven en de gebruiker doorbladert, richt de pagina zich aan de wortelknoop in plaats van de authored knoop (NPR-31618).

* Het dialoogvenster Weergaveconfiguratie werkt niet correct voor de workflowfunctie voor het aanpassen van postvakken (NPR-32503 en NPR-32492).

* Er wordt een foutbericht weergegeven tijdens het weergeven van workflowinformatie met Inbox (CQ-4282168).

### Assets {#assets-6540-enhancements}

* De knop waarmee de workflow voor het verzamelen van elementen wordt geactiveerd, is uitgeschakeld (NPR-32471).

* Een omslag zonder naam wordt gecreeerd in SPS (het Publiceren Scene7 Systeem) terwijl het bewegen van activa van één omslag aan een andere in de Manager van de Ervaring met Dynamische Configuratie Scene7 van Media (NPR-32440).

* De handeling voor het verplaatsen van alle elementen (met de opdracht Alles selecteren en vervolgens verplaatsen) naar een map met gepubliceerde elementen mislukt bij fout (NPR-32366).

* Het genereren van uitvoeringen voor elementen met ${extension} mislukt (NPR-32294).

* URL&#39;s met versiegeschiedenis worden weergegeven onder Veld Verwijzing naar op de eigenschappenpagina voor elementen (NPR-31889).

* ZIP-bestand dat is gedownload van DAM, kan niet worden geopend met WinZip (NPR-32293).

* Oorspronkelijke machtigingen van een map worden bijgewerkt wanneer Mapinstellingen worden geopend om de maptitel of miniatuurafbeelding te wijzigen en vervolgens worden opgeslagen (NPR-32292).

* Het kalenderpictogram voor activering dat is gepland, wordt niet weergegeven in de kolom Status (in de klassieke gebruikersinterface van de DAM-lijst met activa) voor elementen waarvan de activering voor een latere datum en tijd is gepland (NPR-32291).

* Het maken van fragmenten met behulp van fragmentsjablonen geeft een fout op bij het zoeken naar verzamelingen tijdens het maken van fragmenten (NPR-32290).

* Meerdere zoekquery&#39;s worden geactiveerd wanneer meerdere tags zijn geselecteerd met het zoekfilter (NPR-32143).

* De interface van Experience Manager Assets geeft afgekapte bestandsnamen weer wanneer elementen met meer dan 50 tekens in de bestandsnaam zijn geüpload (NPR-32054).

* Alle selectievakjes in het deelvenster Filter worden gewist wanneer het eerste en het tweede selectievakje worden gewist, terwijl niveau twee selectievakjes in de boomstructuur van het selectievakje in Adobe Stock zijn ingeschakeld (NPR-31919).

* Bestanden en mapzoekopdrachten met Omnissearch-facetten geven uitzondering (NPR-31872).

* Veldmarkering voor verplichte veldselectie in de metagegevenseditor wordt niet verwijderd, zelfs niet nadat het vereiste veld is geselecteerd, wanneer de afhankelijkheidsregels zijn ingesteld in het corresponderende metagegevensschema (NPR-31834).

* Volledige namen van bladniveautags (uit de taghiërarchie) worden niet weergegeven op de pagina Eigenschappen van element (NPR-31820).

* Het gebruik van de opdracht back van de pagina Eigenschappen van element op de Safari-browser geeft een fout (NPR-31753).

* De resultatenpagina Touch UI-zoekopdracht (uitgevoerd via Omnissearch) wordt automatisch naar boven geschoven en verliest de schuifpositie van de gebruiker (NPR-31307).

* De elementendetailpagina van PDF-elementen bevat geen actieknoppen, behalve de knoppen voor Verzameling en Vertoning toevoegen in Experience Manager die wordt uitgevoerd in de uitvoeringsmodus Dynamische media Scene7 (CQ-4286705).

* De activa vergen te lang om door het partijuploadproces van Scene7 (CQ-4286445) te verwerken.

* Met de knop Opslaan wordt de externe set niet geïmporteerd als de gebruiker geen wijzigingen heeft aangebracht in de Editor instellen in de Dynamic Media Client (CQ-4285690).

* Miniatuur van 3D-middelen is niet informatief wanneer een ondersteund 3D-model wordt opgenomen in Experience Manager (CQ-4283701).

* De onverwerkte status van de voorinstelling van de viewer voor SmartCrop wordt twee keer weergegeven op de bannertekst naast de naam van de voorinstelling (CQ-4283517).

* Onjuiste containerhoogte van een geüpload 3D-model, voorvertoond in 3D-viewer, wordt weergegeven op de detailpagina van het element (CQ-4283309).

* De Carousel Editor wordt niet geopend in IE 11 in de modus Dynamische media hybride van Experience Manager (CQ-4255590).

* De toetsenbordfocus blijft vastzitten in de vervolgkeuzelijst E-mail in het dialoogvenster Downloaden, in Chrome- en Safari-browsers (NPR-32067).

* Het selectievakje Alle inhoud synchroniseren is standaard niet ingeschakeld wanneer wordt geprobeerd om DM-cloud config toe te voegen via Experience Manager (CQ-4288533).

### Foundation-UI {#foundation-ui-6540}

* Bij het zoeken van elementen met het deelvenster Filter wordt de muiscontrole verplaatst naar het vorige filterveld in plaats van in het bestaande filterveld te blijven (NPR-32538).

* Tags voor platforms: Als u tags zoekt door in de tagvelden te typen, worden tags buiten de hoofdgrenzen weergegeven en wordt de `rootPath` eigenschap van tagvelden niet gerespecteerd (NPR-31895).

* Gebruikersinterface platform: Browseronderbrekingen van het pad als een ongeldig pad wordt toegevoegd in het tekstveld (NPR-31884).

* Melding wordt verborgen achter een plakmenu op paginaselectie (NPR-31628).

### Platform {#platform-sling-6540}

* (HTL) Onderstrepingstekens vervangen dubbele punten in de padsectie van URL (NPR-32231).

### Projecten {#projects-6540}

* De knop Maken is niet zichtbaar voor de gebruiker, zelfs niet als de gebruiker toestemming heeft om een project te maken in de submap (NPR-31832).

### Projectomzetting {#projects-translation-6540}

* Wanneer de optie Snijruimten bijsnijden is geactiveerd in `Apache Sling JSP Script Handler` (NPR-32154), wordt de interface van het vertaalproject verbroken.

* Fout in UI en Null-puntuitzondering in foutenlogboeken wordt waargenomen wanneer om het even welke te vertalen markering aan een vertaalproject (NPR-31896) wordt toegevoegd.

### Integrations {#integrations-6540}

* Het genereren van een URL-bibliotheek met opstarthandleidingen is alleen gebaseerd op `path` en `library_name` waarden van de opstartAPI en is niet gebaseerd op `library_path` waarde (NPR-31550).

* Er wordt een foutbericht weergegeven tijdens het verwerken van aan LiveFyre gerelateerde items (FYR-12420).

* ReportSuitesServlet is kwetsbaar voor SSRF (NPR-32156).

### WCM-sjablooneditor {#wcm-template-editor-6540}

* In de bewerkbare sjabloonstructuurmodus wordt de lijst met toegestane componenten in de lay-outcontainer niet weergegeven met de koppelingsknopcomponent (CQ-4282099).

### WCM Pagina-editor {#wcm-page-editor-6540}

* Er is een fout opgetreden bij het selecteren van een overlay en het selecteren van responsieve rastersleepcomponenten hier (CQ-4283342).

### Campagne gericht {#campaign-targeting-6540}

* De configuratie van de doelcloud mislukt als de fout get-boxes is mislukt (CQ-4279880).

### Brand Portal {#assets-brand-portal-6540}

* Gebruikers van het Brand Portal kunnen geen middelen uit de bijdragemap publiceren naar [!DNL Assets] bij de upgrade naar Adobe I/O op Experience Manager 6.5.4 (CQDOC-15655). Voor een directe oplossing voor Experience Manager 6.5.4 wordt aangeraden de hotfix [te](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/hotfix/cq-6.5.0-hotfix-33041) downloaden en op de auteurinstantie te installeren.

* Pop-upwaarden van het metagegevensschema zijn niet zichtbaar in de elementeigenschappen (CQ-4283287).

* In het subschema Metagegevens worden geen tabbladen weergegeven die zijn gebaseerd op mimetype in eigenschappen van elementen (CQ-4283288).

* Als u het schema voor metagegevens niet publiceert, wordt een foutbericht weergegeven, maar wordt het schema op de achtergrond verwijderd.

* Voorvertoningsafbeelding wordt niet weergegeven voor een gepubliceerd element (CQ-4285886).

* De gebruiker kan activa publiceren of unpublish die enig citaat in de naam bevatten (CQ-4272686).

* De voorwaarden worden niet weergegeven tijdens het downloaden van meerdere middelen (CQ-4281224).

* Kleine beveiligingskwetsbaarheden verholpen.

### Gemeenschappen {#communities-6540}

* Het formulier Lid maken wordt weergegeven als een lege pagina (NPR-31997).

* De gebruiker kan het Analytics-rapport over de auteurinstantie (NPR-30913) niet bekijken.

### eikenindexering en vragen {#oak-indexing-6540}

* MS Word- en MS Excel-documenten met JPEG-afbeeldingen kunnen niet worden geparseerd en er is een fout opgetreden bij het parseren van een klasse die niet is gevonden (NPR-31952).

### Formulieren {#forms-6540}

>[!NOTE]
>
>Experience Manager Service Pack bevat geen oplossingen voor Experience Manager Forms. Ze worden geleverd met behulp van een apart Forms add-on pakket. Daarnaast wordt een cumulatief installatieprogramma uitgebracht dat oplossingen voor Adobe Experience Manager Forms op JEE bevat. Zie Invoegtoepassing [van Experience Manager Forms](/help/release-notes/sp-release-notes.md#install-aem-forms-add-on-package) installeren en Formulieren Experience Manager [installeren op JEE](/help/release-notes/sp-release-notes.md#install-aem-forms-jee-installer)voor meer informatie.

* Correspondentenbeheer: Letters geven extra tekens weer na verzending naar workflows voor postprocessen (NPR-32626).

* Correspondentenbeheer: Bij letters wordt een tijdelijke aanduiding voor een vervolgkeuzelijst weergegeven als een tekstonderdeel na verzending naar workflows na verwerking (NPR-32539).

* Correspondentenbeheer: De standaardwaarden die in de lettertypesjabloon worden gedefinieerd, worden niet weergegeven in de voorvertoningsmodus (NPR-32511).

* Mobiele formulieren: De knop Verzenden wordt weergegeven als vergroot tijdens het renderen van een XDP-formulier in een HTML-versie (NPR-32514).

* Documentservices: Problemen met URL-toegang voor Letters en enkele andere pagina&#39;s na toepassing van Service Pack 2 (NPR-32508, NPR-32509).

* Documentservices: Als het aantal transacties op een server een specifieke limiet overschrijdt, mislukt de conversie van HTML naar PDF en worden de instellingen voor het bestandstype van de [!DNL Forms] server verwijderd (NPR-32204).

* Adaptieve formulieren: Browser het hulpmiddel van de toegankelijkheid meldt mislukkingen in adaptieve vormen overeenkomstig de richtlijnen van niveau AA van WCAG2 (NPR-32312, NPR-32309, CQ-4285439).

* Adaptieve formulieren: Het hulpmiddel van de de browser van Chrome rapporteert een beste praktijkmislukking (NPR-32310).

* Adaptieve formulieren: Problemen met de omzetting tijdens het configureren van een adaptief formulier dat is ingesloten op de pagina Experience Manager Sites (NPR-32168).

* Workbench: Er wordt een foutbericht weergegeven wanneer de bewerking PDF-eigenschappen ophalen voor de PDF Utilities-service (NPR-32150) wordt gebruikt.

* Documentbeveiliging: Een beveiligd PDF-bestand kan niet offline worden geopend met de optie DisableGlobalOfflineSynchronizationData ingesteld op True (NPR-32078).

* Designer: Als de coderingsoptie is ingeschakeld, verdwijnt de subformulierrand in de gegenereerde PDF-uitvoer (NPR-32547, NPR-31983, NPR-31950).

* Designer: Als een tabel samengevoegde cellen bevat, mislukt de toegankelijkheidstest voor het PDF-uitvoerbestand dat is geconverteerd van een XDP-formulier met de uitvoerservice (CQ-4285372).

* Foundation JEE: Als een Experience Manager Forms-server is losgekoppeld van een cluster, kunnen cacheproblemen voorkomen dat deze opnieuw verbinding maakt met de server (NPR-32412).

## Adobe Experience Manager 6.5.3.0 {#experience-manager-6530}

[!DNL Adobe Experience Manager] 6.5.3.0 is een belangrijke release die prestatievermogen, stabiliteit, beveiliging en belangrijke correcties en verbeteringen voor klanten bevat die zijn vrijgegeven sinds de algemene beschikbaarheid van de 6.5-release in **april 2019**. Het kan bovenop [!DNL Adobe Experience Manager] 6.5 worden geïnstalleerd.

Enkele belangrijke hoogtepunten van deze service pack-release zijn:

* De ingebouwde opslagplaats (Apache Jackrabbit Oak) wordt bijgewerkt naar versie 1.10.6.

* [!DNL Experience Manager Assets] ondersteunt nu ZIP-archieven die zijn gemaakt met het Deflate64-algoritme.

* Er is een nieuwe kolom voor de gemaakte datum toegevoegd aan de DAM-lijstweergave en de zoekresultaten voor elementen in de lijstweergave. Deze kolom kan worden gesorteerd.

* Asset sorting based on Name column is enabled in de mening van de Lijst.

* [!DNL Dynamic Media] ondersteunt nu SmartCrop-video-elementen. Slim uitsnijden is een door computers aangedreven functie die een video bijsnijdt terwijl het frame wordt verplaatst om het brandpunt van de scène te volgen.

* [!DNL Dynamic Media] ondersteunt Smart Imaging.

* Mogelijkheid om de voorkeuren voor [Buiten-Office](../forms/using/configure-out-of-office-settings.md) in [!DNL Experience Manager] workflows in te stellen.

* Mogelijkheid om items [in Postvak IN of Postvak IN te](../forms/using/configure-shared-queues-osgi.md) delen met andere gebruikers in [!DNL Experience Manager] workflows.

* De capaciteit om Interactieve Mededelingen op een wijze [van de Partij te](../forms/using/generate-multiple-interactive-communication-using-batch-api.md)produceren.

* Bijgewerkte versie van jQuery die in ContextHub aan 3.4.1 wordt gebundeld.

### Assets {#assets-6530-enhancements}

**Verbeteringen voor producten**

* [!DNL Experience Manager Assets] ondersteunt nu ZIP-archieven die zijn gemaakt met het Deflate64-algoritme (NPR-27573).

* De nieuwe kolom voor gemaakte datum, die sorteerbaar is, wordt toegevoegd in de DAM-lijstweergave en in de resultaten voor het zoeken naar middelen in de lijstweergave (NPR-31312).

* In de lijstmening, kunnen de gebruikers de lijst van activa sorteren gebruikend [!UICONTROL Name] kolom (NPR-31299).

* De GLB-, GLTF-, OBJ- en STL-bestanden kunnen worden voorvertoond op [!UICONTROL Asset Details] pagina&#39;s in DAM (CQ-4282277).

* `ReplicationOnModifyListener` De gebeurtenis wordt geactiveerd voor segmentknooppunten tijdens het uploaden naar een segment in [!DNL Dynamic Media] (CQ-4281279).

* [!DNL Dynamic Media] ondersteunt nu SmartCrop-video-elementen. Slim uitsnijden is een door computers aangedreven functie die een video bijsnijdt terwijl het frame wordt verplaatst om het brandpunt van de scène te volgen (CQ-4278995).

* [!DNL Dynamic Media] ondersteunt Smart Imaging (CQ-4222249).

* De onderzoek of doorbladert mening wordt geplaatst als standaardmening in de plukker van de Stichting als de vraagparameters in verzoek worden overgegaan (NPR-31601).

**Oplossingen**

* Metagegevens voor sommige PDF-documenten worden niet bijgewerkt en in de PDF opgeslagen wanneer de titel wordt gewijzigd (NPR-31629).

* Het delen van elementen werkt niet voor elementen met een plusteken (`+`) in de bestandsnaam (NPR-31547).

* Bewerkingen in het standaardzoekformulier Middelen Admin * Search Rail werken niet zoals verwacht (NPR-31502).

<!-- Review: Check if this seemingly stray asterisk is needed there or not.
-->

* Suggesties worden niet weergegeven wanneer u OmnZoeken op middelen gebruikt om middelen te zoeken (NPR-31496).

* Verwijzingen naar activa binnen verzamelingen worden niet bijgewerkt wanneer de betreffende activa naar een andere locatie worden verplaatst, in gevallen waarin naar dezelfde activa wordt verwezen door verschillende inzamelingen door verschillende gebruikers (NPR-31486).

* Er worden dubbele IPTC-tags toegevoegd aan metagegevens van elementen (NPR-31328).

* Het aantal zoekresultaten wordt niet op de juiste wijze bijgewerkt wanneer een zoekopdracht wordt gestart vanaf de filterrail (NPR-31316).

* Alle selectievakjes worden gewist wanneer de selectie van de selectievakjes van het tweede niveau in het filter Bestandstype wordt opgeheven en de tekst in de zoekbalk is niet synchroon met de geselecteerde of gedeselecteerde eigenschappen (NPR-31287).

* Niet alle leden (gebruikers/groepen) kunnen worden verwijderd uit de sectie Leden van een map. wanneer wordt geprobeerd om alle gebruikers te verwijderen, wordt de aangemelde gebruiker toegevoegd aan de lijst (NPR-31171).

* Elementen met een plusteken (`+`) in de bestandsnaam kunnen niet worden verwijderd (NPR-31162).

* Het keuzemenu Maken, dat in het bovenste menu zichtbaar is wanneer u een map selecteert, geeft &#39;Map&#39; niet weer als een optie voor maken (NPR-30877).

* Mapselectie Maken > Handelitem FileUpload ontbreekt wanneer ACL voor Weigeren `jcr:removeChildNodes` en `jcr:removeNode` op pad wordt toegepast voor een gebruiker (NPR-30840).

* De DAM-workflows worden in de status &#39;stale&#39; gezet wanneer bepaalde MP4-middelen worden geüpload, waardoor alle resterende workflows in de status &#39;stale&#39; gaan (NPR-30662).

* Er is een fout ten gevolge van onvoldoende geheugen opgetreden wanneer grote PDF-bestanden (met meerdere gigabytes) naar DAM worden geüpload en de bijbehorende subbestanden worden verwerkt (NPR-30614).

* Bulkverplaatsing van activa mislukt en geeft een waarschuwingsbericht weer (NPR-30610).

* De namen van activa worden veranderd in kleine letters wanneer het bewegen van activa van één omslag aan een andere in [!DNL Experience Manager] lopen in wijze [!DNL Dynamic Media]-Scene7 (NPR-31630).

* Er wordt een fout waargenomen tijdens het bewerken van een externe imageset, voor de afbeelding die zich bevindt in de map met de naam van het Scene7-bedrijf (NPR-31340).

* [!DNL Dynamic Media] activa met referenties worden niet gepubliceerd (NPR-31180).

* Het uploaden van [!DNL Dynamic Media][!DNL Dynamic Media Classic] 7-Scene7 wijze aan duurt te lang om (NPR-31048) te voltooien.

* Hotspot die aan een afbeeldingselement is toegevoegd, is niet zichtbaar via de Interactive Image Viewer op de pagina met elementdetails (NPR-30979).

* Er worden enorme slingerbanen gecreëerd en de verwerkingsbanner wordt opnieuw weergegeven wanneer acties die op activa in [!DNL Experience manager Assets] worden uitgevoerd, worden doorgegeven aan Scene7 (NPR-30947).

* Conflict doet zich voor bij het maken van Taalkopie van middelen en middelen wordt niet geüpload naar Scene7 (NPR-30932).

* Dynamische vertoningen die zijn gedownload van [!DNL Experience Manager] uitvoering in [!DNL Dynamic Media]-hybride modus worden verbroken (het gaat om teksttypen met de inhoud &#39;kan afbeelding niet vinden&#39; in plaats van het type afbeeldingsinhoud) (NPR-30876).

* [!DNL Dynamic Media] De werkstroom Video coderen genereert geen miniatuur voor de video die in Adobe Experience Manager is gemigreerd van [!DNL Dynamic Media Classic] naar de modus [!DNL Dynamic Media]-Scene7 (CQ-428/2011).

* IpsApiException waargenomen terwijl het migreren van activa van één instantie aan een andere gebruikend verschillende het bedrijfs IDs Scene7 (CQ-4280548).

* De miniatuur van 3D-middelen is niet informatief wanneer een ondersteund 3D-model wordt ingesloten in [!DNL Experience Manager] (CQ-4283701).

* Schuifknoppen worden weergegeven in de viewer als een 3D-element maar weinig cameraweergaven heeft (CQ-4283322).

* Onjuiste containerhoogte van een geüpload 3D-model, voorvertoond in DimensionalViewer op de pagina Asset Details (CQ-4283309).

* Video&#39;s kunnen niet worden afgespeeld met SmartCropVideoViewer in Internet Explorer 11 en Safari (CQ-4281422).

* Het gebruik van verplaatsingsknoop om veelvoudige activa, van één omslag aan een andere te bewegen, ontbreekt in [!DNL Experience Manager] lopende op runmode [!DNL Dynamic Media]-Scene7 (CQ-4280384).

* Vervormde video wordt weergegeven op de elementdetails wanneer het MIME-type niet MP4 is (CQ-4279704).

* Video&#39;s die onlangs in mappen met videoprofiel zijn opgenomen, worden nog steeds verwerkt nadat het coderingspercentage is voltooid tot 100% (CQ-4279389).

* Het bewegen van activa van een omslag leidt tot grote aantallen sling banen (vraag Scene7 API) dan ideaal vereist (CQ-4278664).

* De namen van de imageset worden veranderd in kleine letters in Scene7, wanneer imageset (of mediaset) wordt gecreeerd en met aangewezen noemende overeenkomst in DAM (CQ-4281112) genoemd.

* Scene7 de reeksen van de Migrator publiceren verkeerd staat (CQ-4263492).

* De resultatenpagina Touch UI-zoekopdracht (uitgevoerd via Omnissearch) wordt automatisch naar boven geschoven en verliest de schuifpositie van de gebruiker in Content Fragments (CQ-4282898).

* PDF-bestanden zijn niet geïndexeerd en de inhoud in deze bestanden kan niet worden doorzocht (CQ-4278916).

* Een fout &quot;Groep niet vermeld door de plukker van de gebruiker: onwaar naar verwacht gelijk aan true&quot; wordt waargenomen bij het toevoegen van een gesloten gebruikersgroep met andere `principalName` en `authorizableId` (CQ-4278177).

* De Mening van de Kolom UI van activa toont alle wegen ongeacht de de dampwortel van specifieke huurder weg (CQ-4278175).

* Het zoeken door de kiezer van middelen werkt niet zoals verwacht (CQ-4275886).

* Workflows voor uitvoering ontbreken (CQ-4271928).

* DAM Event Purge verwijdert de meest recente (`maxSavedActivities`) gebeurtenisgegevens en slaat de eerder gemaakte gegevens op (NPR-31336).

* De resultatenpagina Touch UI-zoekopdracht (uitgevoerd via Omnissearch) wordt automatisch naar boven geschoven en verliest de schuifpositie van de gebruiker (NPR-31307).

* De actiebalk en het aantal elementen worden niet bijgewerkt wanneer u alle items selecteert en vervolgens de selectie van bepaalde items (mappen/afzonderlijke elementen) in Touch UI (NPR-31118) opheft.

* Er wordt een uitzondering weergegeven bij [!DNL Experience Manager] het opvragen van taakdetails van een element (CQ-4283569).

### Sites {#sites}

* Als de overerving van LiveCopy is verbroken, worden op live kopieerpagina&#39;s links naar taalkopieën weergegeven in plaats van LiveCopy-koppelingen (NPR-30980).
* Voor een nieuwe blauwdruk, als het aantal verslagen meer dan 40 is, slechts worden de eerste 40 verslagen getoond. Blauwdruk geeft lege regels weer voor de rest van de records (NPR-31182).
* Wanneer een gebruiker Japanse of Koreaanse karakters in het beschrijvingsbezit van een menu toevoegt, toont het menu vervormde karakters voor Japans en Koreaans taaltekst (NPR-31331).
* De Rich Text Editor (RTE) staat niet toe om een ingesloten tabel in te voegen als lijstitem (NPR-30879).
* Buiten het vak, de basislijn van de Rich Text Editor (RTE). past inline font-size toe op elementen, onverwacht (NPR-31284).
* Wanneer een gebruiker de linkerspoorgebieden concentreert en een toetsenbordkortere weg gebruikt om inhoud te kleven, kleeft het de inhoud van het paginageditor klembord in plaats van de inhoud die van de linkerspoorgebieden wordt gekopieerd (NPR-31172).
* Wanneer een gebruiker een veld Bestand uploaden toevoegt aan een veld met meerdere velden, wordt het afbeeldingspad opgeslagen in het componentknooppunt in plaats van het knooppunt met meerdere velden (NPR-30882).
* De `ResponsiveGridExporter` API retourneert geen `com.day.cq.wcm.foundation.model.impl.export.AllowedComponentsExporter` interface. Het `com.day.cq.wcm.foundation.model.impl` pakket wordt gedeclareerd als een particulier pakket (NPR-31398).

<!-- Review: NPR-31398 has fixVersion as 6530. However, it is mentioned twice in 6530 and 6520 as fixed. 
Remove one mention of this fix.
-->

* Wanneer een pagina met bepaalde fragmenten van de Ervaring in niet redacteurswijze (of in Auteur zonder het `editor.html` voorvoegsel en `wcmmode=disabled`, of in Uitgever) wordt geopend., beëindigt het verzoek in de code van de de statusfout van HTTP `500` (NPR-30743).
* Gebruikers kunnen hun wachtwoord niet wijzigen en toegang krijgen tot hun profielpagina (NPR-31161).

### Zoeken en gebruikersinterface {#search-ui-interface}

* Wanneer u op een pagina met zoekresultaten overschakelt van de kaartweergave naar de lijstweergave, is er een vertraging voordat de pagina kan worden geschoven (NPR-31286).

* Het [!UICONTROL Select All] selectievakje is verborgen in de lijstweergave in de [!DNL Sites] gebruikersinterface (NPR-31614).

* Het [!UICONTROL Select All] aantal op een pagina met zoekresultaten is onjuist (NPR-31120).

* In de metagegevenseditor worden tags weergegeven die niet bestaan (NPR-31119).

### Vertaling {#translation}

* Er worden twee kalenderpop-ups weergegeven bij het selecteren van de optie Einddatum in een vertaaltaak (NPR-31270).

### Platform {#platform}

* De Mime typeoptie in de console van het Web werkt niet (NPR-31108).

* Clientcertificaat wordt niet geaccepteerd bij het configureren van Single Sign-On (NPR-31165).

* Updates in de configuratie van de buffergrootte voor de op Jetty-Gebaseerde dienst van HTTP worden niet bewaard (NPR-30925).

* QueryBuilder steunt nu orde ``fn:name()`` in xpath vragen (NPR-31322).

* Er wordt een dubbele activeringsstructuur gemaakt bij een upgrade vanaf [!DNL Experience Manager] 6.3 (NPR-31513).

* Door:sturen verzoeken bewaren antwoordkopballen niet die tijdens het verbinden authentificatie (NPR-30013) worden geplaatst.

* Zoeken in de kiezercomponenten werkt niet (NPR-31692).

* Er wordt een fout weergegeven bij het koppelen van een ZIP-bestand aan een [!DNL Experience Manager Communities] bericht vanwege verschillende versies van Apache POI en Apache Tika bundle (NPR-31018).

* De ``org.apache.sling.distribution.api`` bundel is verborgen in de configuratiemanager en is daarom niet beschikbaar voor aangepaste bundels (NPR-31720).

### Projecten {#projects}

* Schakelen tussen kalenderweergaven werkt niet (NPR-31271).

### Brand Portal {#assets-brand-portal-6530}

**Verbeteringen voor producten**

* De workflow voor het importeren van middelen in [!DNL Experience Manager Assets] is gewijzigd om alleen de nieuw gemaakte elementen van [!DNL Brand Portal] te halen naar [!DNL Experience Manager], en slaat de elementen over die al in de map NEW staan om replicatie te voorkomen (CQ-4278527).

**Oplossingen**

* Er wordt een onjuist pictogram weergegeven bij het maken van een nieuwe map voor bijdragen in de functie voor het zoeken naar middelen (CQ-4282825).
* Bij het maken van een nieuwe Contribute-map worden een of beide submappen (NEW en SHARED) niet weergegeven in de map Contribution (CQ-4282424).
* Het systeem genereert een uitzondering als de gebruiker de map Contribution opnieuw probeert te publiceren van [!DNL Experience Manager] naar [!DNL Brand Portal] na het ontvangen van nieuwe middelen in de map Contribution vanaf [!DNL Brand Portal] het einde (CQ-4279740).
* Het is niet toegestaan om een Contribute-map te maken in een map met bijdragen (geneste map) om complexiteit te voorkomen (CQ-4278391).
* Het systeem genereert een uitzondering bij het uploaden van de [!DNL Brand Portal] gebruikerslijst (.csv-bestand) die is geïmporteerd uit [!DNL Experience Manager] Admin Console. Alleen de velden E-mail, Voornaam en Achternaam in het CSV-bestand zijn verplicht (CQ-4278390).

### Gemeenschappen {#communities-6530}

**Oplossingen**

* Snelle koppelingen voor het beheer van groepen (groepen Openen/Bewerken/Publiceren/Verwijderen) zijn niet zichtbaar voor de communautaire beheerders (beheer van groep/site) (NPR-31627).
* Een verzonden blog wordt alleen weergegeven als de pagina handmatig wordt vernieuwd of opnieuw wordt geladen (NPR-31599).
* De JCR-query die wordt gebruikt door de functie &quot;Misions&quot; is hoofdlettergevoelig en het duurt te lang om resultaten te retourneren (NPR-31475).
* [!DNL Experience Manager] 6.5 Het bestand UberJar genereert een uitzondering, `cq-social-translation` er ontbreekt een bundel in het bestand UberJar [!DNL Experience Manager] 6.5 (NPR-31186).
* Jackson Databind-bibliotheken bijgewerkt naar versie 2.9.9.3 om nieuwe kwetsbaarheden te verhelpen (NPR-30967).
* Activiteiten en aanmeldingstitels zijn inconsistent (NPR-30941).
* Paginering werkt niet correct in [!DNL Communities] Blogs (NPR-30914).
* Rapporten over analysemogelijkheden worden niet gevuld in de [!DNL Experience Manager] auteursomgeving. Er wordt een lege pagina weergegeven (NPR-30913).

### Eik {#oak}

* De indexupdates van Lucene die auteurserver veroorzaken om te vertragen (NPR-31548).

### Formulieren {#forms-6530}

>[!NOTE]
>
>[!DNL Experience Manager] Service Pack bevat geen oplossingen voor [!DNL Experience Manager Forms]. Ze worden geleverd met behulp van een apart Forms add-on pakket. Daarnaast wordt een cumulatief installatieprogramma uitgebracht dat oplossingen voor [!DNL Experience Manager Forms] JEE bevat. Zie Invoegtoepassing [van Experience Manager Forms](/help/release-notes/sp-release-notes.md#install-aem-forms-add-on-package) installeren en Formulieren Experience Manager [installeren op JEE](/help/release-notes/sp-release-notes.md#install-aem-forms-jee-installer)voor meer informatie.

#### Formulierinvoegpakket {#forms-add-on-package-6530}

**Adaptieve formulieren**

* Tekenreeksen bevatten de woordenboeksleutel bij het lokaliseren van adaptieve formulieren (NPR-31110).

**Interactieve communicatie**

* **MissingNode.toString()** retourneert onjuiste resultaten nadat Jackson-bibliotheken zijn bijgewerkt naar 2.10.0 (NPR-31549).

* Teksteditor verwijdert willekeurig spatietekens uit de tekst die uit Microsoft Word is gekopieerd (NPR-31113).

**Correspondentenbeheer**

* Bijschriften en knopinfo worden niet weergegeven tijdens het migreren van letters van LiveCycle ES4SP1 naar [!DNL Experience Manager] 6.5 (NPR-31615).

* **De opmaak van TextFlow wordt niet meer ondersteund** tijdens het opslaan van letters als concepten (NPR-30463).

**Workflow**

* OSGi-workflow mislukt als gevolg van 100% CPU-gebruik (NPR-31233).

**HTML5-formulieren**

* Als u HTML5-voorbeeld van een XDP-formulier genereert, wordt een flikkering weergegeven terwijl exemplaren van een subformulier worden toegevoegd (NPR-30909).

#### Formulieren bij JEE-installatieprogramma {#forms-jee-installer-6530}

**Formulieren - Document Services**

* De de Webdienst van de ZEEP die MTOM in een .NET project gebruikt toont uitzonderingen voor AssemblerServiceClient aanhaalt en methodes HtmlToPDF2 (NPR-4281771).

**Foundation JEE**

* De configuratie van de actie laadt niet de procesnamen voor Invoke a Forms Workflow submit actie (NPR-31478).

### Inclusief functiepakketten {#feature-packs-included-6530}

>[!NOTE]
>
>Voor [!DNL Experience Manager Forms] klanten is het van essentieel belang om een [!DNL Experience Manager Forms] invoegpakket te installeren nadat u een [!DNL Experience Manager] Service Pack, Cumulative Fix Pack of Feature Pack hebt geïnstalleerd.

#### Formulieren - Foundation JEE {#forms-foundation-jee-feature}

* [!DNL Experience Manager] Formulierondersteuning voor Oracle 18c (NPR-29155).

## Adobe Experience Manager 6.5.2.0 {#experience-manager-6520}

[!DNL Adobe Experience Manager] 6.5.2.0 is een belangrijke release die prestatievermogen, stabiliteit, beveiliging en belangrijke correcties en verbeteringen voor klanten bevat die zijn geïntroduceerd sinds de algemene beschikbaarheid van [!DNL Adobe Experience Manager] 6.5 in **april 2019**. Het kan bovenop [!DNL Experience Manager] 6.5 worden geïnstalleerd.

Enkele belangrijke hoogtepunten van deze service pack-release zijn:

* De ingebouwde opslagplaats (Apache Jackrabbit Oak) wordt bijgewerkt naar versie 1.10.3.
* Er is een configuratie-eigenschap toegevoegd waarmee u Experience Fragments rechtstreeks kunt exporteren naar door de gebruiker gedefinieerde werkruimten voor [!DNL Adobe Target].
* Met middelen kunnen gebruikers visueel vergelijkbare afbeeldingen zoeken. [!DNL Experience Manager] geeft de slimme getagde afbeeldingen uit de DAM-opslagplaats weer die lijken op een door de gebruiker geselecteerde afbeelding. Zie [visuele zoekopdracht](../assets/search-assets.md#visualsearch).

* Verbeterde functionaliteit Connected Assets om ondersteuning toe te voegen voor het ophalen van documenten van externe DAM-implementaties. Siteauteurs kunnen nu ondersteunde documenttypen zoeken en filteren in de Inhoudszoeker. De externe documenten kunnen worden toegevoegd aan de component Download op webpagina&#39;s. Zie [Gekoppelde elementen](../assets/use-assets-across-connected-assets-instances.md)gebruiken.

* Filters van het type Document verbeteren met meer types MIME om multi-getaxeerde opties te steunen.
* Introduceerde een externe workflow voor herverwerking voor ondersteuning van meerdere bronnen.
* Geoptimaliseerde [!DNL Dynamic Media] prestaties door standaardmiddelfilters voor replicatie te gebruiken.
* Opties voor het bewerken van middelen voor uitsnijden en roteren zijn hersteld voor DMS7.
* Een optie geïmplementeerd om een video te dempen tijdens het laden in VideoPlayer.
* Repareren om ervoor te zorgen dat de de kolommening van Activa slechts huurdersspecifieke inhoud toont.
* Oplossing voor wijzigingen in stijlaccordeon in zoekresultaten.

### Assets {#assets}

**Verbeteringen voor producten**

* Verbeterde functionaliteit Connected Assets om ondersteuning toe te voegen voor het ophalen van documenten van externe DAM-implementaties. Siteauteurs kunnen nu ondersteunde documenttypen zoeken en filteren in de Inhoudszoeker. De externe documenten kunnen worden toegevoegd aan de component Download op webpagina&#39;s. Hotfix voor CQ-4270245. Zie [Gekoppelde elementen](/help/assets/use-assets-across-connected-assets-instances.md)gebruiken.

* [!DNL Experience Manager Assets] gebruikers kunnen visueel vergelijkbare afbeeldingen zoeken. [!DNL Experience Manager] geeft de slimme getagde afbeeldingen uit de DAM-opslagplaats weer die lijken op een door de gebruiker geselecteerde afbeelding. Zie [visuele zoekopdracht](../assets/search-assets.md#visualsearch).

**Oplossingen**

* Elementpaden in URL&#39;s en mapmetagegevens die door de ACS-API worden gegenereerd, worden niet via URL gecodeerd. GRANITE-26198: Hotfix voor CQ-4271814
* Het uitpakken van een archief met een map met een procentteken (%) in de naam kan niet worden geopend via [!DNL Experience Manager Assets] interface. NPR-29989: Hotfix voor CQ-4270467
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
* De functie van de Verbinding van het aandeel werkt niet aan [!DNL Experience Manager] instantie met configuratie DMS7. NPR-30080, NPR-30492: Hotfix voor CQ-4273651
* Het toevoegen van de [!DNL Dynamic Media]-component Scene7 aan de pagina, en dan het publiceren van de pagina brengt niet de configuratie dmscene7 telkens teweeg. NPR-30641: Hotfix voor CQ-4275962
* Toegevoegd een IPSJobJournal in [!DNL Experience Manager] om slechts één baan van de Systemen van de Preventie van het Binnendringen (IPS) per verwerkingsprofiel tot stand te brengen. NPR-30490: Hotfix voor CQ-4273614
* [!DNL Dynamic Media]: Er zijn standaardfilters toegevoegd om te voorkomen dat elementen worden gerepliceerd naar het [!DNL Experience Manager] publicatieknooppunt. NPR-30538: Hotfix voor CQ-4274678
* Introduceerde een externe werkstroom van het Herproces voor multi-middelsteun om omslag als lading toe te staan. De werkstroom heeft twee stappen - verwerkt activa zonder handvatten via meta-gegevenskaart aan volgende stap opnieuw en uploadt alle activa zonder activa handvat aan S7 in één enkele IPS baan. Zie Cloudservices configureren voor meer informatie. [!DNL Dynamic Media] NPR-30489: Hotfix voor CQ-4272903
* Het uploaden van onjuiste CSV na correcte CSV wipes uit correcte CSV. Hotfix voor CQ-4277694, CQ-4277814
* Het onjuiste pictogram dat specifiek is voor de bijdragemappen die moeten worden verwijderd. Hotfix voor CQ-4277580
* Als u een gebruiker selecteert in de gebruikerskiezer op het tabblad Asset Contribution, wordt de naam van de gebruiker niet weergegeven in de tabel en wordt in het dialoogvenster Gebruikers verwijderen op de eigenschappenpagina een onjuiste tekst weergegeven. Hotfix voor CQ-4277875
* Medewerkers kunnen niet vanuit de gebruikerskiezer worden toegevoegd aan de map Asset Contributor door een gebruiker te selecteren en op Toevoegen te klikken. Hotfix voor CQ-4277824, CQ-4278087
* Zoeken in kleine letters werkt niet in de gebruikerskiezer. Hotfix voor CQ-4277958, CQ-4277930
* Niet-beheerders kunnen elementen publiceren in een nieuwe map in de map Asset Contribution. Hotfix voor CQ-4278200
* de gebruiker van de dam (niet-admin) heeft geen optie om contribuanten aan de omslag van de inbreng van Activa toe te voegen. Hotfix voor CQ-4278192
* De knop Maken is zichtbaar in de map Asset Contribution. Hotfix voor CQ-4277560
* Als u de zoekopdracht sorteert op relevantie, worden [!DNL InDesign] documenten samen met [!DNL InDesign] sjablonen geretourneerd. Hotfix voor CQ-4273864
* Als de gebruiker een e-mailadres in hoofdletters heeft, kunnen gebruikers niet inchecken voor de elementen die eerder zijn uitgecheckt. Hotfix voor CQ-4276575
* De bewerking Verwijderen is alleen van toepassing op voorinstellingen die zijn geselecteerd. Als de lijst na de bewerking automatisch wordt vernieuwd op het scherm, worden andere voorinstellingen weergegeven die al zijn vernieuwd. Hotfix voor CQ-4261461
* Als u [!DNL Dynamic Media] Cloud Services configureert in de [!DNL Dynamic Media]hybride modus, ontstaan meerdere lege rapportsuites die zijn gemaakt in [!DNL Analytics]en waarvoor geen id van de rapportsuite is opgeslagen [!DNL Experience Manager], wat resulteert in een duplicatie van de rapportsuite. Hotfix voor CQ-4249780
* Rename verrichting in [!DNL Experience Manager] activa aan gedupliceerde naam kan niet synchroniseren aan Scene7. Hotfix voor CQ-4276763
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
* De `ResponsiveGridExporter` API retourneert geen `com.day.cq.wcm.foundation.model.impl.export.AllowedComponentsExporter` interface. Het `com.day.cq.wcm.foundation.model.impl` pakket wordt gedeclareerd als privé-pakket (NPR-31398).
* Wanneer een pagina met bepaalde fragmenten van de Ervaring in niet redacteurswijze (of in Auteur zonder het `editor.html` voorvoegsel en `wcmmode=disabled`, of in Uitgever) wordt geopend, beëindigt het verzoek in code 500 van de de statusfout van HTTP (NPR-30743).

### WCM - Pagina-editor {#wcm-page-editor-6520}

**Verbeteringen voor producten**

* Verbeter documenttype filters met meer MIME Types om multi-getaxeerde opties te steunen. Hotfix voor CQ-4270694

### Beheer van inhoudsfragmenten {#content-fragment-management-6520}

* De query die wordt gebruikt door de gebruikersinterface van Content Fragment-modellen is erg langzaam en resulteert uiteindelijk in een fout. Hotfix voor CQ-4270807

### UI - Foundation {#ui-foundation}

* Sneltoetsen die voorkomen dat de gebruiker &#39;m,&#39; &#39;p,&#39; &#39;e&#39; gebruikt in specifieke gebruikersinterfaces. NPR-30355: Hotfix voor GRANITE-26346
* Als u de zoekinterface sluit, wordt de linkertrack niet opnieuw ingesteld op Inhoud, zodat de gebruiker de filterrail niet de tweede keer kan openen. [!DNL Experience Manager Assets] NPR-30509: Hotfix voor CQ-4274716
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

### Integratie {#integration}

* De aangepaste inhoud wordt pas correct weergegeven op de publicatieversie als de instantie opnieuw is gestart. NPR-30377: Hotfix voor CQ-4273706
* Wanneer u Starten op een website configureert, wordt voor het bibliotheekadres een schuine streep (/) toegevoegd, zodat u telkens handmatig kunt ingrijpen. NPR-30694: Hotfix voor CQ-4275501

### Formulieren {#forms-6520}

>[!NOTE]
>
>[!DNL Experience Manager] Service Pack bevat geen oplossingen voor [!DNL Experience Manager Forms]. Ze worden geleverd met een apart [!DNL Forms] invoegpakket. Daarnaast wordt een cumulatief installatieprogramma uitgebracht dat oplossingen voor [!DNL Experience Manager Forms] JEE bevat. Zie Invoegtoepassing [van Experience Manager Forms](/help/release-notes/sp-release-notes.md#install-aem-forms-add-on-package) installeren en JEE-installatieprogramma [van Experience Manager](#forms-jee-installer)installeren voor meer informatie.

De belangrijkste markeringen voor [!DNL Experience Manager] 6.5.2.0 vormen zijn:

* Instelling Automatisch toegevoegd aan `RenderAtClient` de API voor `PDFFormRenderOptions` [!DNL Experience Manager] Forms OSGi.

#### Formulierinvoegpakket {#forms-add-on-package}

**Back-end integratie**

* Kan het formuliergegevensmodel niet configureren met een door AWS gehoste taakgebalanceerde URL. NPR-30123: Hotfix voor CQ-4273359
* Tijdens het creëren van het Model van de Gegevens van de Vorm (FDM) met de Taal van de Definitie van de Dienst van het Web (WSDL), `Caused by: com.adobe.aem.dermis.exception.DermisException: java.lang.Exception: Unable to handle content type` is het foutenbericht teruggekeerd: NPR-30477: Hotfix voor CQ-4272921

**Correspondentenbeheer**

* De vertoning van de &quot;van de Correspondentie UI van de Making (CCR UI) ontbreekt periodiek met hieronder fout in console:
   `- Uncaught Error: variable [object Object]is already known the letter`- NPR-30127

**Interactieve communicatie**

* Een veld dat is gemarkeerd als vereist in het formuliergegevensmodel, wordt weergegeven als vereist in de interface Correspondentie maken (CCR UI). NPR-30623: Hotfix voor CQ-4274902

**Formulieren - workflow**

* Niet-toegewezen uitvoervariabelen op Gecontroleerde mappen zorgen ervoor dat de activering mislukt. Hotfix voor CQ-4264451

**HTML5-formulieren**

* Wanneer de douanecode of het project voor de tweede keer wordt opgesteld, geeft de pagina niet terug en de volgende fout komt voor:

   `org.apache.sling.scripting.sightly.SightlyException.`

   NPR-30539: Hotfix voor CQ-4272509

* Wanneer u in de modus Bladeren een HTML5-formulier leest met toegang tot niet-visuele desktops, wordt in de Chrome-browser vóór elke SVG (Scalable Vector Graphic) in het formulierontwerp &quot;graphic&quot; gelezen. NPR-30449: Hotfix voor CQ-4274732

#### Forms JEE-installatieprogramma {#forms-jee-installer}

**Formulieren - Documentbeveiliging**

* Het toepassen van een handtekening met tijdstempel mislukt vanwege een fout: ALC-DSC-003-000: com.adobe.idp.dsc.DSCInvocationException: Inroepfout. NPR-30820: Hotfix voor CQ-4275852

**Formulieren - Document Services**

* Als &quot;SubmitURL&quot;een en-teken (&amp;) bevat, worden de parseringsfouten gezien in het logbestand wanneer de POST-aanvraag wordt ingediend voor renderpdf servlet. NPR-30865: Hotfix voor CQ-4278232

**Formulieren - Foundation JEE**

* De HTMLtoPDF-service geeft maxReuseCount niet weer in de JMX-console. NPR-30134, NPR-30304: Hotfix voor CQ-4273763
* Het toevoegen van of het uitgeven van een verbinding van de Dienst van het Web door de Webdiensten van [!DNL Experience Manager Forms] Workbench aan te halen veroorzaakt een fout: ClassNotFoundException org.apache.axis.message.SOAPBodyElement. NPR-30105: Hotfix voor CQ-4273217

### Inclusief functiepakketten {#feature-packs-included}

>[!NOTE]
>
>Voor [!DNL Experience Manager Forms] klanten is het van essentieel belang om een [!DNL Experience Manager Forms] invoegpakket te installeren nadat u een [!DNL Experience Manager] Service Pack, Cumulative Fix Pack of Feature Pack hebt geïnstalleerd.

#### Sites {#sites-feature-packs-included}

* Er is een configuratie-eigenschap toegevoegd waarmee u Experience Fragments rechtstreeks kunt exporteren naar door de gebruiker gedefinieerde werkruimten voor [!DNL Adobe Target]. NPR-29189: Hotfix voor CQ-4249782

#### Formulieren - Document Services {#forms-document-services-1}

* Instelling Automatisch toegevoegd aan `RenderAtClient` de API voor `PDFFormRenderOptions` [!DNL Experience Manager Forms] OSGi. NPR-30759: Hotfix voor CQ-4278193

## Adobe Experience Manager 6.5.1.0 {#experience-manager-6510}

[!DNL Adobe Experience Manager] 6.5.1.0 is een belangrijke release die prestatievermogen, stabiliteit, beveiliging en belangrijke correcties en verbeteringen voor klanten bevat die zijn geïntroduceerd sinds de algemene beschikbaarheid van [!DNL Adobe Experience Manager] 6.5 in *april 2019.* Het kan bovenop [!DNL Experience Manager] 6.5 worden geïnstalleerd.

Enkele belangrijke hoogtepunten van deze service pack-release zijn:

* De opname van de status dynamic-UI in het bijhouden van gebeurtenissen als aangepaste kenmerken ingeschakeld.
* Inclusief ondersteuning voor de levering van video-elementen van 360 graden in de modus [!DNL Dynamic Media]-Scene7.
* De functie *Japanse omloop* van Word is ingeschakeld via de stijlplug-in van de Rich Text Editor. Voor meer informatie, zie Japanse woordomslag [vormen](/help/sites-administering/configure-rich-text-editor-plug-ins.md#jpwordwrap)

### Assets

* Bijgewerkte interface DAM DMGateway voor S3 multipart steun. NPR-29740: Hotfix voor CQ-4226303
* Voorvertoning van uitvoeringen genereert `Only empty tenantId is currently supported` fout na upgrade naar [!DNL Experience Manager] 6.5. NPR-29986: Hotfix voor CQ-4272353
* Dialoogvenster Verwijderen is niet zichtbaar om het verwijderen van taken toe te staan. NPR-29720: Hotfix voor CQ-4271074
* Nadat een gebruiker de elementtitel op de eigenschappenpagina heeft toegevoegd en vervolgens de pagina probeert te sluiten, [!DNL Experience Manager] wordt de eigenschappenpagina weer geopend. NPR-29627: Hotfix voor CQ-4264929
* VersioningTimelineEventProvider moet een hoofdversie leveren samen met het knooppunt van het type nt: versie. Hotfix voor GRANITE-26063
* Uitgevoerde de capaciteit om 360 bolvormige video&#39;s op wijze te uploaden en te spelen [!DNL Experience Manager] DM-Scene7. Hotfix voor CQ-4265131
* Met Live kopie wordt een onjuiste status opgehaald als de bron wordt bewerkt. Hotfix voor CQ-4265451
* Ondersteuning voor beheer van meerdere sites ingeschakeld voor [!DNL Experience Manager Assets]. Hotfix voor CQ-4271453, CQ-4268621, CQ-4257491
* [!DNL Experience Manager] een extra item voor de huidige versie van het element in de tijdlijngeschiedenis weer te geven, waarbij de laatste incheckopmerking van [!DNL Adobe Asset Link]wordt weergegeven. Hotfix voor CQ-4262864
* In de tijdlijn van het inhoudsfragment wordt een foutbericht weergegeven wanneer eigenschappen ontbreken. Hotfix voor CQ-4272560
* Een kwestie met Scene7 videospeler wanneer uitgebreid aan het volledige scherm. Hotfix voor CQ-4266700
* ZoomVerticalViewer: Panknoppen mogen niet worden weergegeven als één afbeeldingselement wordt gebruikt. Hotfix voor CQ-4264795
* Wanneer u een onderliggende node in de live kopie verwijdert, moet de liveRelationship worden losgekoppeld. Hotfix voor CQ-4270395
* Het meta-gegevensschema bevat slechts punten van de globale configuratie en mist degenen van de actieve huurder. De URL-waarde van het formPath wordt weer ingesteld op de standaardwaarde, zelfs als deze wordt gewijzigd. NPR-29945: Hotfix voor CQ-4262898
* Publiceer vooraf ingestelde beelden om met 500 foutencode te [!DNL Brand Portal] ontbreken. NPR-29510: Hotfix voor CQ-4268659

### Sites

* Lege eigenschappen en meerdere eigenschappen verspreiden zich niet van blauwdruk tijdens de rollout. Actieve kopie herstellen met blauwdruk werkt niet voor componenten. NPR-29253: Hotfix voor CQ-4264928, CQ-4264926, CQ-4267722
* CoralUI, wanneer gebruikt met `Multifield`, slaat het `fileReferenceParameter` op componentenniveau in plaats van multifield niveau op. NPR-29537: Hotfix voor CQ-4266129
* Verbetering van [!DNL Experience Manager] tekstcomponent en Teksteditor naar Japans. NPR-29785: Hotfix voor CQ-4265090
* De pagina die wordt teruggezet met Timewarp, moet naar het correcte beeld op het tijdstip van versioning verwijzen. NPR-29431: Hotfix voor CQ-4262638
* An issue with the inheritance of Style System nodes from parent to child. NPR-29516: Hotfix voor CQ-4270330
* Een foutbericht tijdens het instellen van het sociaal posten naar [!DNL Facebook] verificatie. NPR-29211: Hotfix voor CQ-4266630
* De weergegeven miniatuur op Inhoudsfragment toont de interne kalenderrepresentatie voor het veld Datum en tijd. NPR-29531: Hotfix voor CQ-4269362
* De knoppen worden niet weergegeven wanneer u het tabblad met machtigingen opent in de implementatie van Coral2. Hotfix voor CQ-4269419

### Handel

* RestrictionViolationException, when running lazy content migration for e-commerce. NPR-29247: Hotfix voor CQ-4264383

### Beheer van inhoudsfragmenten

* Parseerfout bij het openen van een inhoudsfragment met de tekens dollar `($)` en open accolade `({)`. Hotfix voor CQ-4270266

### Ervaringsfragmenten

* Exporteer [!DNL Experience Manager] ervaringsfragmenten naar [!DNL Adobe Target]. Hotfix voor CQ-4265469
* De uitvoer van de Fragmenten van de ervaring naar doel ontbreekt met slimme beeld. Hotfix voor CQ-4269606

* De gebruiker raakt een doodlopende weg wanneer het proberen om de Fragmenten van de Ervaring door Onderzoek in kaartmening te bewegen. Hotfix voor CQ-4263848

### WCM - Pagina-editor

* Gespiegeld XSS (Cross-site scripting) bij gebruik van een ongeldige kiezer. Hotfix voor CQ-4270397

### Replicatie

* Door de gebruiker opgegeven gegevens worden niet beschermd bij uitvoer in de `cq/replication/components/agent` component, wat resulteert in een opgeslagen XSS-kwetsbaarheid (Cross-site scripting). Hotfix voor CQ-4266263

### Workflow

* Het veld Kalenderkiezer van deelnemer in dialoogvenster is verbroken. NPR-29727: Hotfix voor CQ-4270423

### WCM - SPA-editor

* Toegelaten het halen van pre-teruggegeven inhoud van een ver eindpunt. Hotfix voor CQ-4270238
* Waarschuwingen in logboeken wanneer het openen van een Pagina van het Malplaatje van het KUUROORD server-kant teruggegeven. Hotfix voor CQ-4270238

### WCM - MSM

* Door een upgrade naar [!DNL Experience Manager] 6.4.3 duurt het lang voordat u de functie voor beheer van meerdere sites uitvoert. Hotfix voor CQ-4271410

### Integratie

* BrightEdge-referenties zijn mislukt vanwege een verbindingsfout. NPR-29168: Hotfix voor CQ-4265872

* Er wordt een uitzonderingsbericht weergegeven wanneer u de [!DNL Experience Manager] startconfiguratie probeert te bewerken en op te slaan. NPR-29176: Hotfix voor CQ-4265782/CQ-4266153

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

* Sessielek tijdens OAuth voor elke replicatie naar [!DNL Brand Portal]. NPR-30001: Hotfix voor GRANITE-26196

### Projecten

* Publiceren [!DNL Experience Manager Assets] vanuit de map [!DNL Experience Manager] Auteur/content/dam/mac naar [!DNL Brand Portal] werkt niet. NPR-29819: Hotfix voor CQ-4271118

### Platform

* HtmlLibraryManager verwijdert alle inhoud van crx-quickstart bij cachevalidatie. NPR-29863: Hotfix voor GRANITE-26197

### Felix

* Gegevens over geheugengebruik worden niet weergegeven in de systeemconsole bij gebruik van Java11\. NPR-29669

### Formulieren

De belangrijkste hooglichten voor [!DNL Experience Manager Forms] 6.5.1.0 zijn:

* Alleen OSGi: Er is een nieuw kenmerk toegevoegd `PAGECOUNT` in de service Uitvoer en Formulieren.

* Alleen OSGI: Ondersteuning ingeschakeld voor het maken van statische PDF-bestanden met Forms Service.
* Toegelaten toestemmingen op XMLForm.exe voor beheerder en wortelgebruikers.
* Ondersteuning ingeschakeld voor ADFS v3.0 for Dynamics on-premise integratie.

#### Formulierinvoegpakket

**Backend-integratie**

* Fout bij het ophalen van de beveiligde Web Service Definition Language (WSDL). NPR-29944: Hotfix voor CQ-4270777
* Als een formulier op IBM WebSphere [!DNL Experience Manager Forms] is geïnstalleerd, mislukt het maken van een formuliergegevensmodel op basis van SOAP. Hotfix voor CQ-4251134
* Toegelaten steun voor de Actieve Diensten van de Federatie van de Folder (ADFS) v3.0 voor de Integratie van de Dynamiek van Microsoft op-gebouw. Hotfix voor CQ-4270586
* Als de titel van een gegevensbron wordt gewijzigd, wordt de bijgewerkte titel niet weergegeven in het formuliergegevensmodel. Hotfix voor CQ-4265599
* Als de naam van een entiteit of kenmerk afbreekstreepjes of spaties bevat, worden dergelijke entiteiten en kenmerken niet door expressies geëvalueerd. Hotfix voor CQ-4225129

* Er wordt een onjuiste uitvoer waargenomen wanneer een dubbele punt aanwezig is in de primitieve uitvoer van de tekenreeks. Hotfix voor CQ-4260825

* Zelfs als er geen inhoud wordt verwacht van de REST API-uitvoer, genereert de aanroepbewerking van het formuliergegevensmodel een fout. Hotfix voor CQ-4268828

**Adaptieve formulieren**

* Unable to add new instance in Adaptive Form Fragment during lazy loading. NPR-29818: Hotfix voor CQ-4269875
* Verify component registreert of toont geen fout voor Document van de malplaatjes van het Verslag. Hotfix voor CQ-4272999
* Toegevoegde ondersteuning voor het uitschakelen van de layouteditor voor Adaptieve formulieren. Hotfix voor CQ-4270810
* De stap Verifiëren voor Adaptive Forms is hersteld in [!DNL Experience Manager] 6.5. Hotfix voor CQ-4269583

* Fout bij validatie van adaptieve formuliervelden [!DNL Adobe Sign]. Hotfix voor CQ-4269463
* Wanneer een [!DNL Experience Manager Forms] instantie meer dan 20 adaptieve formulierfragmenten heeft en de naam van alle formulierfragmenten begint met dezelfde tekenreeks, retourneert de zoekopdracht niet of alleen naar recente 20 gemaakte fragmenten. Hotfix voor CQ-4264414, CQ-4264914

* Prestatieproblemen wanneer de toepassing Adaptive Forms wordt gebruikt met een grote dataset. . Hotfix voor CQ-4235310

* Wanneer betreden door anonieme rekening op een publicatie instantie, ontbreekt GuideRuntime manuscript om te laden. Hotfix voor CQ-4268679

**Formulieren - Interactieve communicatie**

* De interactieve Communicatie malplaatje maakt geen lijst van kopbal en footer componenten in toegestane componentenlijst. Hotfix voor CQ-4237895
* Wanneer u een interactieve sjabloon voor communicatie-afdrukken maakt die een afbeeldingsveld bevat, wordt de titel van het diagram ingesteld op leeg. Hotfix voor CQ-4264772
* De lijnkleur van een diagram wordt, wanneer deze wordt verwijderd, ingesteld op ongedefinieerd. Hotfix voor CQ-4264762
* Wijzigingen in de lay-outlaag die zijn aangebracht op documentfragment, verdwijnen bij het uitvoeren van de wijzigingen en blijven synchroon. Hotfix voor CQ-4266054
* Het formuliergegevensmodelelement in een documentfragment dat aan een tekstveld is gebonden, geeft geen overervingspictogram weer en staat binding toe. Hotfix voor CQ-4261089
* De printerkanaal-render-API heeft geen optie om gegevens als parameter door te geven in de API. Hotfix voor CQ-4263540
* De montages van de agent zijn niet zichtbaar aangezien Editable door de controledoos van de Agent wordt ongecontroleerd wanneer het bindingstype van het Fragment van de Tekst in niets/het ModelVoorwerp van Gegevens voor het gebied van het Koord/variabele wordt veranderd. Hotfix voor CQ-4261953
* Voor de voorlegging van de UI van de Agent, slaat het resulterende dossier van Webgegevens informatie voor erving-geannuleerde niet gebonden gebieden op. Hotfix voor CQ-4265621

**Formulieren - workflow**

* Wanneer een formulier opnieuw wordt verzonden vanuit de Postvak UIT de app voor adaptieve formulieren, gaan er gegevens verloren. NPR-28345: Hotfix voor CQ-4260929
* Documenten worden niet gesloten tijdens het opslaan voor niet-variabele gevallen. Hotfix voor CQ-4269784
* De app Adaptive Forms heeft de ondersteuning voor Microsoft Windows 8.1 ingetrokken. Hotfix voor CQ-4265274
* Wanneer een afbeelding van meer dan 2 MB als een bijlage op veldniveau aan een formulier wordt gekoppeld in de Android-versie van de [!DNL Experience Manager Forms] app, loopt de app vast. Hotfix voor CQ-4265578

* Toegelaten pre-populatieopties voor Interactieve Communicatie Kanaal van de Druk in Assign taak. Hotfix voor CQ-4265577
* De gebruikers kunnen geen gedeelde taak bekijken tot zij lid van de groep worden waaraan de taak wordt toegewezen. Hotfix voor CQ-4248733
* Het opslaan of verzenden van JEE-toepassingen in de app Adaptief formulier is geblokkeerd in Windows. Hotfix voor CQ-4268704
* Het formuliergegevensmodel dat is gekoppeld aan de variabele van het formuliergegevensmodel is niet zichtbaar. Hotfix voor CQ-4266554
* Geen ondersteuning voor de statusvariabele van het documentteken met variabele ondersteuning. Hotfix voor CQ-4266312
* Verzending vanuit werkruimte mislukt met een umlaut-teken. Hotfix voor CQ-4263172
* Als de workflow tijdens een upgrade wordt geopend voor bewerking, wordt in de gebruikersinterface van de controlemap (UI) een fout weergegeven in plaats van de naam van de workflow. Hotfix voor CQ-4238579

**Formulieren - Beheer**

* Wanneer een andere extensie dan xsd of schema.json wordt geüpload, vindt uploaden niet plaats en wordt er geen foutbericht gegenereerd. Hotfix voor CQ-4266716

**Formulieren - Correspondentenbeheer**

* [!DNL Experience Manager Forms] 6.5 de Create Correspondence UI (CCR UI) kan geen correspondentie openen die met [!DNL Experience Manager Forms] 6.3 wordt gecreeerd. Hotfix voor CQ-4266392
* De functie Som in XDP werkt niet als het DDE gegevenstype van type aantal is. Hotfix voor CQ-4227403
* Letters voor de invalidatielogica voor de cache in het geheugen die moeten worden bijgewerkt, omdat de laatste gewijzigde tijd van een element niet wordt bijgewerkt wanneer een element wordt gepubliceerd. Hotfix voor CQ-4250465
* Kan documentfragment, DD &amp; letters niet publiceren. Hotfix voor CQ-4272893

#### Forms JEE-installatieprogramma

**PDF Generator**

* CAD-bestanden naar PDF-conversie mislukken met 64-bits JDK. NPR-29924, NPR-29925: Hotfix voor CQ-4272113
* De naam van PhantomJS is vervangen door WebToPDF voor conversie van HTML naar PDF. NPR-29933: Hotfix voor CQ-4234545
* Er wordt een fout gegenereerd bij het converteren van het ZIP-bestand naar PDF. Hotfix voor CQ-4268628

**Formulieren - Designer**

* Wanneer een volledige toegankelijkheidscontrole wordt uitgevoerd op de statische PDF die is gemaakt met [!DNL Experience Manager Forms Designer]het gereedschap, mislukt de controle van de primaire taal omdat het taalkenmerk ontbreekt. Hotfix voor CQ-4272923, CQ-4271002

**Formulieren - Documentbeveiliging**

* Digital Signature with Hardware Security Module (HSM) werkt niet op OSGi Linux op Java 11 en Java 8\. NPR-29838: Hotfix voor CQ-4270441
* Digital Signature with Hardware Security Module (HSM) werkt niet op JEE Linux en op alle ondersteunde toepassingsservers, zoals JBoss en Websphere. NPR-29839: Hotfix voor CQ-4266721
* Als u de handtekeningen in een PDF verifieert met behulp van PDF Advanced Electronic Signatures (PAdES), wordt InvalidOperationException gegenereerd. NPR-29842: Hotfix voor CQ-4244837
* Extra ondersteuning voor documentbeveiliging voor Office 2019\. Hotfix voor CQ-4254369, CQ-4259764

**Formulieren - Document Services**

* PDF kan niet worden geconverteerd naar PDF/A-1b met formulierveld heeft geen weergavewoordenboek. NPR-29940: Hotfix voor CQ-4269618

* OSGi: Kan het aantal pagina&#39;s dat tijdens het renderen is gegenereerd niet bepalen. NPR-28922: Hotfix voor CQ-4270870
* Ondersteuning ingeschakeld voor statische PDF-bestanden met Forms Service in [!DNL Experience Manager Forms OSGi]. NPR-28572: Hotfix voor CQ-4270869
* Kan de machtigingen voor XMLForm.exe niet wijzigen. NPR-29828, NPR-29237: Hotfix voor Q-4267080
* In de statische PDF die door de uitvoermodule van de [!DNL Experience Manager Forms] server wordt gemaakt, wordt het taalkenmerk/de taaltag niet gevuld met de taal van het gemaakte document. NPR-27332: Hotfix voor CQ-4271002

**Formulieren - Foundation JEE**

* Niet-beschikbare pdfg_srt in definitieve artefacten veroorzaakt het installatieprogramma om te ontbreken. NPR-29854: Hotfix voor CQ-4270137
* LCBackupMode.sh werkt niet. NPR-29840: Hotfix voor CQ-4269424
* De UDP havenverwijzing zou uit gebruikersinterface (UI) voor WebSphere moeten worden verwijderd. Hotfix voor CQ-4264782

### Inclusief functiepakketten

#### Activa - opgenomen

* Ondersteuning voor beheer van meerdere sites ingeschakeld voor [!DNL Experience Manager Assets]. Zie Elementen [hergebruiken met MSM voor de Elementen](https://helpx.adobe.com/experience-manager/6-5/help/assets/reuse-assets-using-msm.html)van Experience Manager voor meer informatie. NPR-29199: Hotfix voor CQ-4259922

#### Sites - inbegrepen

* Exporteer [!DNL Experience Manager] ervaringsfragmenten naar [!DNL Adobe Target]. Zie [de Experience Fragment Link Rewriter Provider - HTML](https://helpx.adobe.com/experience-manager/6-5/help/sites-developing/experience-fragments.html#TheExperienceFragmentLinkRewriterProviderHTML)voor meer informatie. Hotfix voor CQ-4265469

#### Formulieren - Document Services - inbegrepen

* Alleen OSGi: Een nieuw kenmerk PAGECOUNT toegevoegd in Output and Forms Service. NPR-28922: Hotfix voor CQ-4270870
* Alleen OSGi: Ondersteuning ingeschakeld voor het maken van statische PDF-bestanden met Forms Service. NPR-28572: Hotfix voor CQ-4270869
* Toegelaten toestemmingen op XMLForm.exe voor beheerder en wortelgebruikers. NPR-29237: Hotfix voor CQ-4267080

### OSGi-bundels en inhoudspakketten

De volgende tekstdocumenten maken een lijst van de bundels OSGi en de Pakketten van de Inhoud inbegrepen in [!DNL Experience Manager] 6.5.1.0

Lijst van OSGi-bundels opgenomen in [!DNL Experience Manager] 6.5.1.0

[Bestand ophalen](assets/6_5-bundle-list.txt)

Lijst met inhoudspakketten opgenomen in [!DNL Experience Manager] 6.5.1.0

[Bestand ophalen](assets/6_5-content-package-list.txt)
