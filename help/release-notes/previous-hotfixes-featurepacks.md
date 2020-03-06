---
title: AEM 6.5 de Vorige Nota's van de Versie van het Service Pack
description: De nota's van de versie specifiek voor Manager 6.5 Service Pack 3 van de Ervaring van Adobe en vroeger.
uuid: c7bc3705-3d92-4e22-ad84-dc6002f6fa6c
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5
discoiquuid: 25542769-84d1-459c-b33f-eabd8a535462
docset: aem65
translation-type: tm+mt
source-git-commit: 7ae0055e09c3ae2ff2898ac4f6c537a825dc0cf0

---


# Hotfixes en de Pakken van de Eigenschap inbegrepen in vorige Pakken van de Dienst {#hotfixes-and-feature-packs-included-in-previous-service-packs}

## AEM 6.5.3.0

De Manager 6.5.3.0 van de Ervaring van Adobe is een belangrijke versie die prestaties, stabiliteit, veiligheid, en zeer belangrijke klantenmoeilijke situaties en verhogingen omvat die sinds de algemene beschikbaarheid van 6.5 versie in **april 2019** worden vrijgegeven. Het kan bovenop de Manager van de Ervaring van Adobe (AEM) 6.5 worden geïnstalleerd.

Enkele zeer belangrijke hoogtepunten van deze versie van het de dienstpak zijn:

* De ingebouwde opslagplaats (Apache Jackrabbit Oak) wordt bijgewerkt naar versie 1.10.6.

* De Activa van de Manager van de ervaring steunen nu de archieven van het PIT die gebruikend Deflate 64 algoritme worden gecreeerd.

* De nieuwe kolom voor gecreeerde datum, die sorteerbaar is, is toegevoegd in de de lijstmening van DAM en op de resultaten van het activaonderzoek in lijstmening.

* Het sorteren van activa op de kolom van de Naam wordt gebaseerd is toegelaten in de mening die van de Lijst.

* De dynamische Media steunen nu Slimme de videoactiva van het Gewas. Het slimme Gewas is een machine het leren gedreven eigenschap die een video opnieuw teweegbrengt terwijl het bewegen van het kader om het steunpunt van de scène te volgen.

* Dynamic Media ondersteunt Smart Imaging.

* Capaciteit om uit de voorkeur van het Bureau [in AEM- werkschema&#39;s te](../forms/using/configure-out-of-office-settings.md) plaatsen.

* Mogelijkheid om items [in Postvak IN of Postvak In te](../forms/using/configure-shared-queues-osgi.md) delen met andere gebruikers in AEM-workflows.

* Capaciteit om Interactieve Mededelingen op een wijze [van de Partij te](../forms/using/generate-multiple-interactive-communication-using-batch-api.md)produceren.

* Bijgewerkte versie van jQuery die in ContextHub aan 3.4.1 wordt gebundeld.

### Assets {#assets-6530-enhancements}

**Productverbeteringen**

* De Activa van de Manager van de ervaring steunt nu de archieven van het PIT die gebruikend Deflate 64 algoritme (NPR-27573) worden gecreeerd.

* De nieuwe kolom voor gecreeerde datum, die sorteerbaar is, is toegevoegd in de DAM lijstmening en op de resultaten van het activaonderzoek in lijstmening (NPR-31312).

* Asset sorting op basis van de kolom Naam is toegestaan in de lijstweergave (NPR-31299).

* De GLB, GLTF, OBJ, en de activadossiers van STL steunen activavoorproef in de pagina van de Details van Activa in DAM (CQ-4282277).

* ReplicationOnChangeListener wordt de gebeurtenis teweeggebracht voor brokkenknopen tijdens brokkenupload in Dynamische Media (CQ-4281279).

* De dynamische Media steunen nu Slimme de videoactiva van het Gewas. Het slimme Gewas is een machine het leren gedreven eigenschap die een video opnieuw teweegbrengt terwijl het bewegen van het kader om het steunpunt van de scène (CQ-4278995) te volgen.

* Dynamic Media ondersteunt Smart Imaging (CQ-422249).

* De mening van het onderzoek/doorblader is geplaatst als standaardmening in de plukker van de Stichting als de vraagparameters in verzoek (NPR-31601) worden overgegaan.

**Fixes**

* De meta-gegevens voor sommige Pdf- documenten worden niet bijgewerkt en aan PDF bewaard bij het wijzigen van zijn titel (NPR-31629).

* Het delen van activa werkt niet voor activa met een &quot;+&quot;-karakter in hun naam (NPR-31547).

* Geeft in de standaard onderzoeksvorm Activa Admin * De Rail van het Onderzoek uit werkt niet zoals verwacht (NPR-31502).

* Suggesties worden niet weergegeven bij het gebruik van Omnissearch op assets view voor het zoeken naar middelen (NPR-31496).

* Verwijzingen naar activa binnen verzamelingen worden niet bijgewerkt wanneer de desbetreffende activa naar een andere locatie worden verplaatst, in gevallen waarin dezelfde activa worden gerefereerd door verschillende collecties door verschillende gebruikers (NPR-31486).

* Dubbele IPTC-tags worden toegevoegd aan metagegevens over activa (NPR-31328).

* De telling van het onderzoeksresultaat op de hoogste juiste hoek werkt niet nauwkeurig bij wanneer het onderzoek van de filterspoorstaaf (NPR-31316) wordt teweeggebracht.

* Alle controlevakjes worden ontruimd bij het deselecteren van de tweede niveaucontrolevakjes in de filter van het Type van Dossier, en de tekst in de onderzoeksbar is niet in synchronisatie met de geselecteerde/unselected eigenschappen (NPR-31287).

* Alle leden (gebruikers/groepen) kunnen niet uit de sectie Leden van een omslag worden verwijderd; bij het proberen om alle gebruikers te verwijderen, het programma geopende gebruiker wordt toegevoegd aan de lijst (NPR-31171).

* Activa met het plusteken &quot;+&quot; in de bestandsnaam kunnen niet worden verwijderd (NPR-31162).

* Creeer daling onderaan menu, dat in hoogste menu bij het selecteren van een omslag zichtbaar is, toont &quot;Omslag&quot;niet als creeer optie (NPR-30877).

* De selectie van de omslag leidt tot > FileUpload actiepunt mist wanneer ACL voor Deny jcr:removeChildNodes en jcr:removeNode op weg wordt toegepast voor een gebruiker (NPR-30840).

* De DAM-workflows gaan naar de status &#39;stale&#39; wanneer bepaalde mp4-bedrijfsmiddelen worden geüpload, waardoor alle resterende workflows in de status &#39;stale&#39; (NPR-30662) terechtkomen.

* Uit Geheugenfout wordt waargenomen wanneer een grote Pdf- dossiers (van verscheidene gigabytes) aan DAM wordt geupload en zijn sub-activa worden verwerkt (NPR-30614).

* Bulkverplaatsing van activa mislukt en geeft een waarschuwingsbericht weer (NPR-30610).

* De namen van activa worden veranderd in lager geval wanneer het bewegen van activa van één omslag aan een andere in AEM die op Dynamische runmode van Media Scene 7 (NPR-31630) lopen.

* De fout wordt waargenomen terwijl het uitgeven van een verre imageset, voor het beeld dat in de omslag verblijft genoemd het zelfde als Scene 7 bedrijfnaam (NPR-31340).

* De dynamische activa van Media die verwijzingen bevatten worden niet gepubliceerd (NPR-31180).

* Uploads van Dynamische Media AEM - Scene 7 runmode aan Scene 7 duurt te lang om te voltooien (NPR-31048).

* Hotspot die aan een beeldactiva wordt toegevoegd is niet zichtbaar door de Interactieve Kijker van het Beeld in de pagina van activadetails (NPR-30979).

* Er worden enorme slingerende banen gecreëerd en de verwerkingsbanner verdwijnt weer wanneer acties op activa in AEM Assets worden doorgegeven aan Scene 7 (NPR-30947).

* Conflict doet zich voor bij het maken van Taal Kopie van bedrijfsmiddelen en bedrijfsmiddelen wordt niet geüpload naar Scene 7 (NPR-30932).

* De dynamische die rendities van AEM worden gedownload die op Dynamische Hybride wijze lopen van Media worden gebroken (zij zijn van teksttype met inhoud &quot;niet kan om beeld&quot;in plaats van beeldinhoudstype te vinden) (NPR-30876).

* De dynamische Media Encodeert het Videowerkschema slaagt er niet in om duimnagel voor de video te produceren die van Scène 7 aan Dynamische Media - de looppaswijze van Scène 7 (CQ-4282011) wordt gemigreerd.

* IpsApiException werd waargenomen terwijl het migreren van activa van één instantie aan een andere gebruikend verschillende Scene 7 bedrijf IDs (CQ-4280548).

* De miniatuur van 3D-middelen is niet informatief wanneer een ondersteund 3D-model in AEM wordt ingeslikt (CQ-4283701).

* De knopen van de rol worden getoond in kijker, als 3D activa weinig camerameningen (CQ-4283322) heeft.

* Onjuiste containerhoogte van een geüploade 3D-model, voorafgegaan door DimensionalViewer op de pagina Asset Details (CQ-4283309).

* De video&#39;s kunnen niet met SmartCropVideoViewer op Internet Explorer 11 en Safari (CQ-4281422) worden gespeeld.

* Het gebruik van bewegingsknoop om veelvoudige activa, van één omslag aan een andere te bewegen, ontbreekt in AEM die op Dynamische Media loopt - scène7 runmode (CQ-4280384).

* De vervormde video wordt gezien op activadetails wanneer het type MIME buiten MP4 (CQ-4279704) is.

* De video&#39;s die onlangs in omslagen met videoprofiel worden opgenomen blijven in verwerkingsstaat zelfs nadat het codepercentage aan 100% (CQ-4279389) voltooit.

* Het bewegen van activa van een omslag leidt tot grote aantallen slingerende banen (Scene 7 API vraag) dan ideaal vereist (CQ-4278664).

* De namen van imageset worden veranderd in lager geval in Scène 7, wanneer imageset (of mediaset) wordt gecreeerd en met aangewezen noemende overeenkomst in DAM (CQ-4281112) genoemd.

* Scene 7 de reeksen van de Migrator publiceren verkeerd staat (CQ-4263492).

* Het onderzoek van de aanraking UI (dat door Omnissearch wordt gedaan) resulteert pagina automatisch scrolt omhoog en verliest de rolpositie van de gebruiker in de Fragmenten van de Inhoud (CQ-4282898).

* PDF-bestanden zijn niet geïndexeerd en inhoud binnen kan niet worden doorzocht (CQ-4278916).

* Een fout &quot;Groep niet die door gebruikerskiezer wordt vermeld: verwacht vals aan gelijk waar&quot;wordt waargenomen bij het toevoegen van de Gesloten Groep van de Gebruiker met verschillend `principalName` en `authorizableId` (CQ-4278177).

* De Mening van de Kolom van activa UI toont alle wegen ongeacht de weg van de de damwortel van de specifieke huurder (CQ-4278175).

* De zoekopdracht van de activaselecteur werkt niet zoals verwacht (CQ-4275886).

* De Werkschema&#39;s van de renditie ontbreken (CQ-4271928).

* DAM de Zuivering van de Gebeurtenis schrapt de recentste (maxSavedActivities) gebeurtenisgegevens en houdt de gegevens die vroeger (NPR-31336) werden gecreeerd.

* De het onderzoek van de aanraking UI (die door Omnissearch wordt gedaan) resultatenpagina scrolt automatisch omhoog en verliest de rolpositie van de gebruiker (NPR-31307).

* De actiesbar en de telling van activa werken niet bij het selecteren van allen bij en deselecteren dan sommige punten (omslagen/individuele activa) in Touch UI (NPR-31118).

* Een uitzondering wordt weergegeven in AEM tijdens het opvragen voor taakdetails van een bedrijfsmiddel (CQ-4283569).

### Sites {#sites}

* Als de overerving LiveCopy gebroken is, tonen de levende exemplaarverbindingen van de exemplaartaal van exemplaarpagina&#39;s in plaats van verbindingen LiveCopy (NPR-30980).
* Voor een nieuwe blauwdruk, als het aantal verslagen meer dan 40 is, slechts worden de eerste 40 verslagen getoond. De blauwdruk toont lege lijnen voor de rest van de verslagen (NPR-31182).
* Wanneer een gebruiker Japanse of Koreaanse karakters in het beschrijvingsbezit van een menu toevoegt, de menuvertoningen vervormde karakters voor Japanse en Koreaanse taaltekst. (NPR-31331).
* De rijke Redacteur van de Tekst (RTE) staat niet toe om een ingebedde Lijst als lijstpunt (NPR-30879) op te nemen.
* Uit de doos, steigere Rich Text Editor (RTE). past gealigneerde doopvont-grootte op elementen toe, onverwacht (NPR-31284).
* Wanneer een gebruiker zich op linker spoorgebieden concentreert en een toetsenbordkortere weg gebruikt om inhoud te kleven, kleeft het de inhoud van het klembord van de paginaredacteur in plaats van de inhoud die van de linkerspoorgebieden (NPR-31172) wordt gekopieerd.
* Wanneer een gebruiker een Dossier toevoegt uploadt gebied aan een multi-gebied, wordt de beeldweg opgeslagen in de componentenknoop in plaats van de multi-gebiedsknoop (NPR-30882).
* ResponsiveGridExporter API keert geen interface com.day.cq.wcm.foundation.model.impl.export.AllowedComponentsExporter terug. Het pakket com.day.cq.wcm.foundation.model.impl wordt verklaard als privé pakket (NPR-31398).
* Wanneer een pagina die sommige ExperienceFragmenten bevat op niet-redacteurswijze (of in Auteur zonder de `editor.html` prefix en `wcmmode=disabled`, of in Uitgever) wordt geopend., beëindigt het verzoek in de code van de de statusfout van HTTP 500 (NPR-30743).
* De gebruikers kunnen hun wachtwoord veranderen en tot hun profielpagina (NPR-31161) toegang hebben.

### Zoeken en gebruikersinterface {#search-ui-interface}

* Wanneer het schakelen van de mening van de Kaart aan de mening van de Lijst op een pagina van onderzoeksresultaten, is er een vertraging vóór de pagina kan worden gescrold (NPR-31286).

* Selecteren Al checkbox is verborgen in de mening van de Lijst op Plaatsen UI (NPR-31614).

* Selecteer allen tellen op een pagina van het onderzoeksresultaat is onjuist (NPR-31120).

* De meta-gegevensredacteur toont markeringen die niet bestaan (NPR-31119).

### Vertaling {#translation}

* Twee kalender-pop-ups worden weergegeven bij het selecteren van de optie Vervaldatum in een vertaaltaak (NPR-31270).

### Platform {#platform}

* De het type van Mime optie in de console van het Web werkt niet (NPR-31108).

* Het certificaat van de cliënt wordt niet goedgekeurd wanneer het vormen van enige sign-on (NPR-31165).

* De updates in de configuratie van de buffergrootte voor de op Jetty-Gebaseerde dienst van HTTP worden niet bewaard (NPR-30925).

* QueryBuilder steunt nu ordby ``fn:name()`` in xpath vragen (NPR-31322).

* De duplo activeringsboom wordt gecreeerd bij bevordering van AEM 6.3 (NPR-31513).

* De door:sturen verzoeken bewaren antwoordkopballen niet die tijdens het slingeren authentificatie (NPR-30013) worden geplaatst.

* Zoeken in de componenten van de plukker werkt niet (NPR-31692).

* Er wordt een fout weergegeven bij het koppelen van een ZIP-bestand aan een AEM Communities-post vanwege verschillende versies van Apache POI en Apache Tika bundle (NPR-31018).

* De ``org.apache.sling.distribution.api`` bundel is verborgen in de configuratiemanager en daarom niet beschikbaar aan douanesbundels (NPR-31720).

### Projecten {#projects}

* De de kalendermeningen van de omschakeling werken niet (NPR-31271).

### Merk Portal {#assets-brand-portal}

**Productverbeteringen**

* Asset Sourcing-importworkflow in AEM-bedrijfsmiddelen wordt gewijzigd om alleen de nieuw gecreëerde bedrijfsmiddelen van het Brand Portal naar AEM te halen en de bedrijfsmiddelen die al in de NIEUWE map aanwezig zijn, over te slaan om replicatie te voorkomen (CQ-4278527).

**Fixes**

* Het onjuiste pictogram verschijnt bij het creëren van een nieuwe omslag van de Bijdrage in de eigenschap van de Inkoop van Activa (CQ-4282825).
* Bij het creëren van een nieuwe omslag van de Bijdrage, verschijnen één of beide subfolders (NIEUW en GEDEELD) niet binnen de omslag van de Bijdrage (kw-4282424).
* Het systeem werpt een uitzondering als de gebruiker probeert om de omslag van de Bijdrage van AEM aan het Portaal van het Merk opnieuw te publiceren na het ontvangen van nieuwe activa in de omslag van de Bijdrage van het Portaal eind van het Merk (CQ-4279740).
* Het maken van de map Contributie in een map Contribution (geneste map) is verboden om complexiteit te vermijden (CQ-4278391).
* Het systeem werpt een uitzondering bij het uploaden van de Poortgebruikerslijst van het Merk (.csv- dossier) die van AEM Admin Console wordt ingevoerd. Alleen de velden Email, FirstName en LastName in het .csv-bestand zijn verplicht (CQ-4278390).

### Gemeenschappen {#communities}

**Fixes**

* De snelle verbindingen om groepen (Open/Edit/publiceren/schrap Groepen) te beheren zijn niet zichtbaar aan de communautaire beheerders (het beheer van de Groep/van de Plaats) (NPR-31627).
* Een verzonden blog wordt niet getoond tenzij de pagina manueel wordt verfrist/herladen (NPR-31599).
* De JCR-query die wordt gebruikt door de functie &quot;Mounds&quot; is hoofdlettergevoelig en duurt te lang om resultaten terug te geven (NPR-31475).
* AEM 6.5 UberJar dossier werpt uitzondering, `cq-social-translation` bundel mist van AEM 6.5 UberJar dossier (NPR-31186).
* De bibliotheken van het Gegevensbestand van Jackson die aan versie 2.9.9.3 worden bijgewerkt om nieuwe kwetsbaarheid (NPR-30967) te richten.
* De titels van activiteiten en van Berichten zijn inconsistent (NPR-30941).
* Paginering werkt niet goed in Communities Blogs (NPR-30914).
* De rapporten van de analyse zijn niet bevolkt in AEM auteursmilieu, blanco pagina verschijnt (NPR-30913).

### Oak {#oak}

* De indexupdates van Lucene die auteursserver veroorzaken vertragen (NPR-31548).

### Formulieren {#forms-6530}

>[!NOTE]
>
>AEM Service Pack omvat geen moeilijke situaties voor Vormen AEM. Zij worden geleverd gebruikend een afzonderlijk toe:voegen-op pakket van Vormen. Bovendien wordt een cumulatieve installateur vrijgegeven die moeilijke situaties voor Vormen AEM op JEE omvat. Voor meer informatie, zie de Vormen [installeren AEM toe:voegen-op](#install-aem-forms-add-on-package) en de Vormen van [installeren AEM op JEE](#install-aem-forms-jee-installer).

#### Formulierinvoegpakket {#forms-add-on-package-6530}

**Aanpassingsvormen**

* De koorden bevatten de woordenboeksleutel terwijl het lokaliseren van adaptieve vormen (NPR-31110).

**Interactieve communicatie**

* **MissingNode.toString()** geeft onjuiste resultaten terug na het upgraden van Jackson bibliotheken naar 2.10.0 (NPR-31549).

* De redacteur van de tekst verwijdert willekeurig ruimtekarakters uit de tekst die uit Microsoft Word (NPR-31113) wordt gekopieerd.

**Correspondentiebeheer**

* De titels en tooltips tonen niet terwijl het migreren van brieven van LiveCycle ES4SP1 aan AEM 6.5 (NPR-31615).

* **De formattering van de tekststroom is niet meer gesteunde** foutenmeldingsvertoningen terwijl het bewaren van brieven als ontwerpen (NPR-30463).

**Werkstroom**

* De OSGi-workflow is mislukt als gevolg van 100% CPU-gebruik (NPR-31233).

**HTML5-formulieren**

* Het produceren van HTML5 voorproef van een vorm XDP toont een flikkering terwijl het toevoegen van instanties van subform (NPR-30909).

#### Formulieren voor JEE-installateur {#forms-jee-installer-6530}

**Formulieren - Documentservices**

* De het Webdienst die van de ZEEP MTOM in een .NET project gebruikt toont uitzonderingen voor AssemblerServiceClient haalt en methodes HtmlToPDF2 (NPR-4281771) aan.

**Foundation JEE**

* De configuratie van de actie laadt niet de procesnamen voor Invoke een van de Vormen Werkschema voorleggen actie (NPR-31478).

### Inclusief functiepakketten {#feature-packs-included-6530}

>[!NOTE]
>
>Voor klanten van de Vormen AEM, is het essentieel om toe:voegen-op pakket van Vormen AEM te installeren na het installeren van om het even welk AEM Service Pack, Cumulative Fix Pack, of het Pak van de Eigenschap.

#### Formulieren - Foundation JEE {#forms-foundation-jee-feature}

* AEM vormt ondersteuning voor Oracle 18c (NPR-29155).

## AEM 6.5.2.0

AEM 6.5.2.0 is een belangrijke versie die prestaties, stabiliteit, veiligheid, en zeer belangrijke klantenmoeilijke situaties en verhogingen omvat die sinds de algemene beschikbaarheid van AEM 6.5 in **april 2019** worden vrijgegeven. Het kan bovenop AEM 6.5 worden geïnstalleerd.

Enkele zeer belangrijke hoogtepunten van deze versie van het de dienstpak zijn:

* De ingebouwde opslagplaats (Apache Jackrabbit Oak) wordt bijgewerkt naar versie 1.10.3.
* Toegevoegd een configuratiebezit om het uitvoeren van de Fragmenten van de Ervaring aan user-defined werkruimten voor het Doel van Adobe direct toe te staan.
* De gebruikers van activa kunnen visueel gelijkaardige beelden zoeken. AEM geeft de slimme getagde afbeeldingen uit de DAM-opslagplaats weer die lijken op een door de gebruiker geselecteerde afbeelding. Zie [visueel zoeken](../assets/search-assets.md#visualsearch).

* Verbeterde de Verbonden functionaliteit van Activa om steun toe te voegen om documenten van verre plaatsingen te halen DAM. De Auteurs van de plaats kunnen gesteunde documenttypes in de Vinder van de Inhoud nu zoeken en filtreren. De verre documenten kunnen aan de component van de Download op Web-pagina&#39;s worden toegevoegd. Zie [gebruik verbonden activa](../assets/use-assets-across-connected-assets-instances.md).

* Verbeter het type van Document filters met meer MIME types om multi-getaxeerde opties te steunen.
* Introduceerde een externe werkschema van het Herproces voor multi-resource steun.
* Optimaliseerde de Dynamische prestaties van Media door standaard activafilters voor replicatie te gebruiken.
* Herstelde gewas/roteer de het uitgeven van Activa opties voor DMS7.
* Implementeerde een optie om een video op lading in VideoPlayer te dempen.
* Bevestig om ervoor te zorgen dat de de kolommening van Activa UI huurdersspecifieke slechts inhoud toont.
* Bevestig om de veranderingen van de stijlharmonika toe te staan om in onderzoeksresultaten na te denken.

### Assets {#assets}

**Productverbeteringen**

* Verbeterde de Verbonden functionaliteit van Activa om steun toe te voegen om documenten van verre plaatsingen te halen DAM. De Auteurs van de plaats kunnen gesteunde documenttypes in de Vinder van de Inhoud nu zoeken en filtreren. De verre documenten kunnen aan de component van de Download op Web-pagina&#39;s worden toegevoegd. Hotfix voor CQ-4270245. Zie [gebruik verbonden activa](/help/assets/use-assets-across-connected-assets-instances.md).

* De gebruikers van activa kunnen visueel gelijkaardige beelden zoeken. AEM geeft de slimme getagde afbeeldingen uit de DAM-opslagplaats weer die lijken op een door de gebruiker geselecteerde afbeelding. Zie [visueel zoeken](../assets/search-assets.md#visualsearch).

**Fixes**

* De wegen van activa in URLs en omslagmeta-gegevens die door de ACS API worden geproduceerd zijn geen URL gecodeerd. GRANITE-26198: Hotfix voor CQ-4271814
* Unzipping een archief met een omslag die een percententeken (%) in zijn naam heeft kan niet worden geopend gebruikend de interface van Activa. NPR-29989: Hotfix voor CQ-4270467
* Aanraakinterface: Tijdens het leiden publicatietovenaar, worden de verwijzingen toegevoegd na de pagina in het postverzoeklichaam, veroorzakend alle activa om na de pagina te publiceren, en wanneer de pagina wordt teruggegeven, worden sommige activa in publiceren instantie gemist. NPR-29985: Hotfix voor CQ-4270724
* De onsamenhangende eigenschap van Activa werkt niet voor verwante activa die speciale karakters (karakters die URI worden gecodeerd) in de naam hebben. NPR-30387: Hotfix voor CQ-4274446
* Wanneer het uitgeven van een inhoudsfragment, wordt de versie gecreeerd met de verkeerde gebruiker.
* Falen tijdens het maken van verzamelingen op een op huurders gebaseerd systeem. NPR-30114: Hotfix voor CQ-4272948
* De de kolommening van activa UI respecteert niet de de damwortel van de huidige huurder maar de toegang tot van alle wegen van de huurdersdam. NPR-30636: Hotfix voor CQ-4275481
* Mogelijke dwars-plaats scripting (XSS) aanval door beperkt dossier waakzaam venster aangezien het geïnjecteerde beeld kan worden gezien. NPR-30617: Hotfix voor CQ-4270133
* MultiTenant: De huurders die omslageigenschappen bewaren observeren zowel succesherinnering als foutenmelding beschrijvend actie niet succesvol was, &quot;Onbekwaam om eigenschappen uit te geven. Onvoldoende rechten.&quot; dus verwarrend. NPR-30545: Hotfix voor CQ-4275333
* De dialoog van de selecteur van activa staat geen selectie van activa toe, daarom kan geen bron bijwerken gebruikend de verwante bronvervangingsfunctionaliteit. NPR-30502: Hotfix voor CQ-4275029
* Werkstroom van bedrijfsmiddelen voor DAM-updates - In de huidige staat bij het uploaden van grote MP4-bestanden. NPR-30480: Hotfix voor CQ-4271352
* Creeer de functionaliteit van de Taak van het Overzicht werkt niet toe te schrijven aan ongeldige nuttige lading die alle verdere op taak betrekking hebbende handelingen van het overzicht maken om te ontbreken. NPR-30468: Hotfix voor CQ-4274263
* De de connectiviteitskwestie van de Markering van Adobe Slimme door Datapower. NPR-30026: Hotfix voor CQ-4269457
* De Mening van de Kolom van activa UI werpt een fout wanneer het proberen om de filters te openen verlaten de spoorstaaf. NPR-30501: Hotfix voor CQ-4273862
* Wanneer het toevoegen van groepen die van LDAP in de Gesloten eigenschappen van de Groep van de Gebruiker (CUG) van een Omslag van Activa worden gesynchroniseerd, wordt de groep niet bewaard en teruggewonnen. NPR-30615: Hotfix voor CQ-4274689
* De het onderzoeksstijl en van de richtlijn van de filter gebieden passen niet de automatisch voltooide waarde op de onderzoeksvraag toe. NPR-30620: Hotfix voor CQ-4275724
* De aandeelverbinding van activa van een omslag met ruimte en &quot;&amp;&quot;karakter in de naam toont lege grijze kaarten voor sommige activa. NPR-30557: Hotfix voor CQ-4270187
* De het schemavorm van de omslag is niet automatisch ontdekt datatype en vandaar, creërend niet verwante TypeHint in vormvoorlegging. NPR-30599: Hotfix voor CQ-4275227
* Het gewas en roteert de het uitgeven van Activa opties zijn onbruikbaar gemaakt van de creatie UI DMS7. NPR-30118: Hotfix voor CQ-4273221
* De eigenschap van de Verbinding van het aandeel werkt niet aan instantie AEM met configuratie DMS7. NPR-30080, NPR-30492: Hotfix voor CQ-4273651
* Het toevoegen van de Dynamische component van Media Scene7 aan de pagina, en dan het publiceren van de pagina brengt niet de configuratie dmscène7 elke keer teweeg. NPR-30641: Hotfix voor CQ-4275962
* Toegevoegd een IPSJobJournal in AEM om slechts één baan van de Systemen van de Preventie van het Binnendringen (IPS) per verwerkingsprofiel tot stand te brengen. NPR-30490: Hotfix voor CQ-4273614
* Dynamische media: Toegevoegde standaardfilters om activa uit te sluiten van wordt herhaald aan AEM publiceren knoop. NPR-30538: Hotfix voor CQ-4274678
* Introduceerde een extern werkschema van het Herproces voor multi-middelsteun om omslag als nuttige lading toe te staan. Het werkschema heeft twee stappen - herwerkt activa zonder handvatten via meta-gegevenskaart aan volgende stap en heruploadt alle activa zonder activahandvat aan S7 in één enkele IPS baan. Voor meer details, zie het Vormen de Dynamische Diensten van de Wolk van Media. NPR-30489: Hotfix voor CQ-4272903
* Het uploaden van een onjuiste CSV na correcte CSV wist correcte CSV. Hotfix voor CQ-4277694, CQ-4277814
* Het onjuiste pictogram specifiek voor de te verwijderen bijdrageomslagen. Hotfix voor CQ-4277580
* Bij het selecteren van een gebruiker in de gebruikerskiezer van het lusje van de bijdrage van Activa, verschijnt de naam van de gebruiker niet in de lijst en de de gebruikersdialoog van de Schrapping op eigenschappen pagina toont verkeerde teksten. Hotfix voor CQ-4277875
* De contribuanten kunnen niet aan de omslag van de bijdrage van Activa van de gebruikerskiezer worden toegevoegd door gebruiker te selecteren en te klikken voegt toe. Hotfix voor CQ-4277824, CQ-4278087
* Zoeken op de naam van de kleine hoofdletters werkt niet in de gebruikerskiezer. Hotfix voor CQ-4277958, CQ-4277930
* Niet-beheerders kunnen activa in een nieuwe omslag van een de premieomslag van Activa publiceren. Hotfix voor CQ-4278200
* de stuwdamgebruiker (niet-admin) heeft niet de optie om contribuanten aan de omslag van de activabijdrage toe te voegen. Hotfix voor CQ-4278192
* De knop &#39;Maken&#39; is zichtbaar in de map voor de bijdrage van bedrijfsmiddelen. Hotfix voor CQ-4277560
* Het sorteren van onderzoeksvraag door relevantie keert documenten InDesign samen met malplaatjes InDesign terug. Hotfix voor CQ-4273864
* Als de gebruiker een e-mailid in hoofdletters heeft, kunnen de gebruikers niet inchecken voor de activa die eerder zijn uitgecheckt. Hotfix voor CQ-4276575
* De verrichting van de Schrapping is slechts op vooraf instelt van toepassing die worden geselecteerd, en als het scherm automatisch de lijst na de verrichting verfrist, toont het andere vooraf instelt die reeds hebben verfrist. Hotfix voor CQ-4261461
* Het vormen van de Dynamische Diensten van de Wolk van Media op wijze DMHybrid resulteert in veelvoudige lege rapportreeksen die in Analytics worden gecreeerd, en zonder rapportreeks identiteitskaart die in AEM wordt opgeslagen, resulterend in de duplicatie van de rapportreeks. Hotfix voor CQ-4249780
* Noem verrichting in activa AEM om gedupliceerde naam te dupliceren er niet in slaagt om aan Scene7 te synchroniseren. Hotfix voor CQ-4276763
* De gebruiker-Gegenereerde Inhoud wordt verkeerd getoond in het paneel van de onderzoeksfilter. Hotfix voor CQ-4273875
* Vind gelijkaardige&#39; optie is niet beschikbaar voor de beelden van TIF. Hotfix voor CQ-4278238
* Geïmplementeerde optie om video op lading in VideoPlayer te dempen. Hotfix voor CQ-4266465
* Kijkers - VideoViewer: poster=none werkt verkeerd in het geval van een externe gebruikte video. Hotfix voor CQ-4265536
* Het pictogram van de wacht is zichtbaar tijdens videospel op browsers van de Rand van IE11 en van MS. Hotfix voor CQ-4251539
* 3.8 SDK en 5.13 dossiers van de kijkersREADME worden niet bijgewerkt en bevatten informatie van vorige versies. Hotfix voor CQ-4273737
* Het Fragment van de inhoud wordt versioned zelfs alvorens de veranderingen te bewaren. NPR-30616: Hotfix voor CQ-4273088
* Vervang Asset#getMetadata (Koord) met Asset#getMetadataValueFromJcr (Koord) in duimnagelproces. NPR-30491: Hotfix voor CQ-4273067
* Het uploaden van jpg veroorzaakt veelvoudige instanties van het bericht: &quot;ReplicateOnChangeWorker Replicating UPDATED&quot; voor elk element, waardoor de prestaties afnemen.
* Het uitpakken van zip archiveren die de eigenschap gebruiken van het Archief van het Uittreksel&quot;veroorzaakt kwesties met omslagen de waarvan naam percenten (%) in hun titel bevat. NPR-29990: Hotfix voor CQ-4270467

### Sites {#sites-6520}

* Als de overerving LiveCopy gebroken is, tonen de levende exemplaarverbindingen van de exemplaartaal van exemplaarpagina&#39;s in plaats van verbindingen LiveCopy. (NPR-30980)
* Voor een nieuwe blauwdruk, als het aantal verslagen meer dan 40 is, slechts worden de eerste 40 verslagen getoond. De vertoningen van de blauwdruk lege lijnen voor rest van de verslagen. (NPR-31182)
* Het rijke elektrische toestel van de Redacteur van de Tekst (RTE) van de vertoningen van de tekstcomponent vervormde karakters voor Japanse en Koreaanse taaltekst. (NPR-31331)
* De rijke Redacteur van de Tekst (RTE) staat niet toe om een ingebedde Lijst als lijstpunt op te nemen. (NPR-30879)
* Uit de doos steigere Rich Text Editor (RTE) is van toepassing gealigneerde doopvont-grootte op elementen, onverwacht. (NPR-31284)
* Wanneer een gebruiker zich op linker spoorgebieden concentreert en toetsenbordkortere weg gebruikt om inhoud te kleven, kleeft het inhoud van het klembord van de paginaredacteur in plaats van de inhoud die van linkerspoorgebieden wordt gekopieerd. (NPR-31172)
* Wanneer een gebruiker een Dossier toevoegt uploadt gebied aan een multi-gebied, wordt de beeldweg opgeslagen in de componentenknoop in plaats van de multi-gebiedknoop. (NPR-30882)
* ResponsiveGridExporter API keert geen interface com.day.cq.wcm.foundation.model.impl.export.AllowedComponentsExporter terug. Het pakket com.day.cq.wcm.foundation.model.impl wordt verklaard als privé pakket. (NPR-31398)
* Wanneer een pagina die sommige ExperienceFragmenten bevat op niet-redacteurswijze (of in Auteur zonder de `editor.html` prefix en `wcmmode=disabled`, of in Uitgever) wordt geopend, beëindigt het verzoek in de code van de de statusfout van HTTP 500. (NPR-30743)

### WCM - Pagina-editor {#wcm-page-editor-6520}

**Productverbeteringen**

* Verbeter het type van Document filters met meer MIME Types om multi-getaxeerde opties te steunen. Hotfix voor CQ-4270694

### Beheer van contentfragmentatie {#content-fragment-management-6520}

* De vraag die door de modellen UI van het Fragment van de Inhoud wordt gebruikt is zeer langzaam en resulteert uiteindelijk in een fout. Hotfix voor CQ-4270807

### UI - Foundation {#ui-foundation}

* De trekker van kortere weg die de gebruiker verhindert &quot;m,&quot;p,&quot;e&quot;binnen specifiek gebruikersinterface te gebruiken. NPR-30355: Hotfix voor GRANITE-26346
* Het sluiten van ActivaOnderzoek UI stelt niet de linkerspoor aan Tevreden selectie terug verhindert de gebruiker de filterspoorstaaf later te openen. NPR-30509: Hotfix voor CQ-4274716
* Omgeving met meerdere gebruikers: De hoogste navigatie van activa UI is niet beschikbaar en het werpen van een fout JavaScript. NPR-30104: Hotfix voor GRANITE-26344

### Vertaling {#translation-6520}

* Vertaalprobleem - Slechts enkele onderdelen worden vertaald met behulp van Machine Translation. NPR-30079: Hotfix voor CQ-4273764

### Platform {#platform-6520}

* AEM de StandaardAfzender van de Post kan post naar een verre server SMTP over TLS v1.2 verzenden niet. NPR-30476: Hotfix voor GRANITE-26605

### Projecten {#projects-6520}

* dam:folderThumbnailPaths de waarden worden niet verfrist en tonen oude duimnagels zelfs na het schrappen van de activa binnen de omslag. NPR-30424: Hotfix voor CQ-4273667
* Bij het voltooien van de optie &quot;Verplaatsen&quot; blijven de titel en de naam van het actief ongewijzigd. NPR-30647: Hotfix voor CQ-4276265

### Gemeenschappen {#communities-6520}

* De Diagnostiek van de Synchronisatie van de gebruiker is volledig gebroken en werkt niet. NPR-30004, NPR-29943: Hotfix voor CQ-4270287, CQ-4271348

### Sling {#sling}

* De verbeterde instantie van 6.3.3.2 tot 6.5 resulteert in dubbele configuraties OSGi. NPR-30130: Hotfix voor CQ-4274016

### Integratie {#integration}

* De aangepaste inhoud wordt niet correct getoond op publiceren instantie tot het nieuwe begin van de instantie. NPR-30377: Hotfix voor CQ-4273706
* Wanneer het vormen van Lancering op een website, heeft het bibliotheekadres een schuine streep (/) vooraf gepende veroorzakend handmatige interventie telkens. NPR-30694: Hotfix voor CQ-4275501

### Formulieren {#forms-6520}

>[!NOTE]
>
>AEM Service Pack omvat geen moeilijke situaties voor Vormen AEM. Zij worden geleverd gebruikend een afzonderlijk toe:voegen-op pakket van Vormen. Bovendien wordt een cumulatieve installateur vrijgegeven die moeilijke situaties voor Vormen AEM op JEE omvat. Voor meer informatie, zie de [Vormen van AEM toe:voegen-op](#install-aem-forms-add-on-package) installeren en de installateurJEE van Vormen van AEM [installeren](#forms-jee-installer).

De belangrijkste hoogtepunten voor vormen AEM 6.5.2.0 zijn:

* Toegevoegd &quot;Auto&quot;plaatsend aan `RenderAtClient` in `PDFFormRenderOptions` API voor Vormen OSGi van AEM.

#### Formulierinvoegpakket {#forms-add-on-package}

**Back-end-integratie**

* Onbekwaam om het Model van de Gegevens van de Vorm te vormen gebruikend een ontvangen lading AWS evenwichtige URL. NPR-30123: Hotfix voor CQ-4273359
* Terwijl het creëren van het Model van de Gegevens van de Vorm (FDM) met de Taal van de Definitie van de Dienst van het Web (WSDL), `Caused by: com.adobe.aem.dermis.exception.DermisException: java.lang.Exception: Unable to handle content type` is de foutenmelding teruggekeerd: NPR-30477: Hotfix voor CQ-4272921

**Correspondentiebeheer**

* &quot;Creeer de renditie van de Correspondentie UI (CCR UI) periodiek met onder fout in console ontbreekt:
   `- Uncaught Error: variable [object Object]is already known the letter`- NPR-30127

**Interactieve communicatie**

* Een gebied duidelijk dat in het model van vormgegevens wordt vereist wordt getoond zoals vereist in Create Correspondentie UI (CCR UI). NPR-30623: Hotfix voor CQ-4274902

**Formulieren - Werkstroom**

* Unmapped outputvariabelen op de Gevolgde Omslagen veroorzaken aanroeping om te ontbreken. Hotfix voor CQ-4264451

**HTML5-formulieren**

* Wanneer de douanecode of het project voor de tweede keer wordt opgesteld, geeft de pagina niet terug en de volgende fout komt voor:

   `org.apache.sling.scripting.sightly.SightlyException.`

   NPR-30539: Hotfix voor CQ-4272509

* Wanneer het gebruiken van de Toegang van de Desktop nietVisual op Browse wijze om een vorm te lezen HTML5, browser van het Chroom leest &quot;grafisch&quot;vóór elke Scalable Vector Grafisch (SVG) in het vormontwerp. NPR-30449: Hotfix voor CQ-4274732

#### Forms JEE-installateur {#forms-jee-installer}

**Formulieren - Documentbeveiliging**

* Het toepassen van een handtekening met timestamp ontbreekt met fout: ALC-DSC-003-000: com.adobe.idp.dsc.DSCInvocationException: Inroepfout. NPR-30820: Hotfix voor CQ-4275852

**Formulieren - Documentservices**

* Als &quot;SubmitURL&quot;een ampersand (&amp;) bevat, worden het ontleden fouten gezien in het logboek wanneer het POST- verzoek aan renderpdf servlet wordt gemaakt. NPR-30865: Hotfix voor CQ-4278232

**Formulieren - Foundation JEE**

* De dienst van HTMLtoPDF is niet toont maxReuseCount in console JMX. NPR-30134, NPR-30304: Hotfix voor CQ-4273763
* Het toevoegen van of het uitgeven van een verbinding van de Dienst van het Web door de Webdiensten van AEM aan te halen vormt Werkbank werpt een fout: ClassNotFoundException org.apache.as.message.SOAPBodyElement. NPR-30105: Hotfix voor CQ-4273217

### Inclusief functiepakketten {#feature-packs-included}

>[!NOTE]
>
>Voor klanten van de Vormen AEM, is het essentieel om toe:voegen-op pakket van Vormen AEM te installeren na het installeren van om het even welk AEM Service Pack, Cumulative Fix Pack, of het Pak van de Eigenschap.

#### Sites {#sites-feature-packs-included}

* Toegevoegd een configuratiebezit om het uitvoeren van de Fragmenten van de Ervaring aan user-defined werkruimten voor het Doel van Adobe direct toe te staan. NPR-29189: Hotfix voor CQ-4249782

#### Formulieren - Documentservices {#forms-document-services-1}

* Toegevoegd &quot;Auto&quot;plaatsend aan `RenderAtClient` in `PDFFormRenderOptions` API voor Vormen OSGi van AEM. NPR-30759: Hotfix voor CQ-4278193

## AEM 6.5.1.0 {#release-6510}

AEM 6.5.1.0 is een belangrijke versie die prestaties, stabiliteit, veiligheid, en zeer belangrijke klantenmoeilijke situaties en verhogingen omvat die sinds de algemene beschikbaarheid van AEM 6.5 in *april 2019 worden vrijgegeven.* Het kan bovenop AEM 6.5 worden geïnstalleerd.

Enkele zeer belangrijke hoogtepunten van deze versie van het de dienstpak zijn:

* Toegelaten de opneming van dynamisch-UI-staat in het volgen van gebeurtenissen als douaneattributen.
* Omvat steun voor de levering van videoactiva van 360 graads in Dynamische Scène 7 van Media.
* De toegelaten eigenschap van de Omslag *van* Japans Word via de stijlen plugin van de Rich Text Editor. Voor meer informatie, zie Japanse [woordomslag vormen](/help/sites-administering/configure-rich-text-editor-plug-ins.md#jpwordwrap)

### Assets

* De bijgewerkte interface van DAM DMGGateway voor S3 multipart steun. NPR-29740: Hotfix voor CQ-4226303
* De voorvertoning van rendities genereert een `Only empty tenantId is currently supported` fout na een upgrade naar AEM 6.5\. NPR-29986: Hotfix voor CQ-4272353
* De dialoog van de schrapping is niet zichtbaar om schrapping van banen toe te staan. NPR-29720: Hotfix voor CQ-4271074
* Na het toevoegen van activatitel in de eigenschappen pagina, wanneer een gebruiker probeert om de pagina te sluiten, opent AEM opnieuw de eigenschappen pagina. NPR-29627: Hotfix voor CQ-4264929
* VersioningChronologieEventProvider zou wortelversie samen met knoop van het type niet moeten verstrekken: versie. Hotfix voor GRANITE-26063
* Implementeerde de capaciteit om 360 sferische video&#39;s op AEM DM-Scene7 wijze te uploaden en te spelen. Hotfix voor CQ-4265131
* Het levende exemplaar wint onjuiste status terug als de bron wordt uitgegeven. Hotfix voor CQ-4265451
* Ondersteuning voor beheer op meerdere sites voor bedrijfsmiddelen. Hotfix voor CQ-4271453, CQ-4268621, CQ-4257491
* De interface AEM zou een extra ingang voor de huidige versie van de activa in de chronologiegeschiedenis moeten tonen, tonend de recentste controlecommentaar van de Verbinding van de Activa van Adobe. Hotfix voor CQ-4262864
* De Chronologie van het Fragment van de inhoud toont een foutenmelding wanneer de eigenschappen missen. Hotfix voor CQ-4272560
* Een kwestie met Scene 7 videospeler wanneer uitgebreid aan het volledige scherm. Hotfix voor CQ-4266700
* ZoomVerticalViewer: De knopen van de pan zouden niet moeten worden getoond als één enkel beeldactiva wordt gebruikt. Hotfix voor CQ-4264795
* Het schrappen van een kindknoop in het levende exemplaar zou liveRelationship moeten losmaken. Hotfix voor CQ-4270395
* Het meta-gegevensschema bevat slechts punten van de globale configuratie en mist degenen van de actieve huurder. De formPath URL waarde keert aan het gebrek terug zelfs wanneer veranderd. NPR-29945: Hotfix voor CQ-4262898
* Publiceer beeld vooraf instelt aan het Portaal van het Merk ontbreekt met 500 foutencode. NPR-29510: Hotfix voor CQ-4268659

### Sites

* De lege eigenschappen en de veelvoudige eigenschappen verspreiden zich niet van blauwdruk tijdens uitlooptraject. Het levende exemplaar van het terugstellen met blauwdruk werkt niet voor componenten. NPR-29253: Hotfix voor CQ-4264928, CQ-4264926, CQ-4267722
* CoralUI, wanneer gebruikt met `Multifield`, slaat het `fileReferenceParameter` op het componentenniveau in plaats van multifield niveau op. NPR-29537: Hotfix voor CQ-4266129
* Verbetering van AEM-tekstcomponent en teksteditor naar Japans. NPR-29785: Hotfix voor CQ-4265090
* De pagina die met Timewarp wordt teruggezet zou naar het correcte beeld op het tijdstip van versioning moeten verwijzen. NPR-29431: Hotfix voor CQ-4262638
* Een kwestie met de overerving van de knopen van het Systeem van de Stijl van ouder aan kind. NPR-29516: Hotfix voor CQ-4270330
* Een foutmelding bij het installeren van het sociale bericht op Facebook-verificatie. NPR-29211: Hotfix voor CQ-4266630
* De teruggegeven duimnagel op het Fragment van de Inhoud toont interne kalendervertegenwoordiging voor het gebied van de Datum en van de Tijd. NPR-29531: Hotfix voor CQ-4269362
* Het openen van het toestemmingenlusje in implementatie Coral2 toont niet de knopen. Hotfix voor CQ-4269419

### Handel

* ConstraintViolationException, wanneer het runnen van luie inhoudsmigratie voor e-handel. NPR-29247: Hotfix voor CQ-4264383

### Beheer van contentfragmentatie

* Het ontleden fout wanneer het openen van een Fragment van de Inhoud dat karakters dollar `($)` en open steun heeft `({)`. Hotfix voor CQ-4270266

### Ervaringsfragmenten

* De Fragmenten van de Ervaring van de uitvoer AEM naar het Doel van Adobe. Hotfix voor CQ-4265469
* De uitvoer van de Fragmenten van de ervaring naar doel ontbreekt met slim beeld. Hotfix voor CQ-4269606

* De gebruiker raakt een dood eind wanneer het probeert om de Fragmenten van de Ervaring door Onderzoek in kaartmening te bewegen. Hotfix voor CQ-4263848

### WCM - Pagina-editor

* Het weerspiegelde dwars-plaats scripting (XSS) wanneer het gebruiken van een ongeldige selecteur. Hotfix voor CQ-4270397

### Replicatie

* De gebruiker-verstrekte gegevens zijn niet ontsnapt aan output in de `cq/replication/components/agent` component, resulterend in opgeslagen dwars-plaats scripting (XSS) kwetsbaarheid. Hotfix voor CQ-4266263

### Werkstroom

* Het veld Kalender van dialoogdeelnemer is kapot. NPR-29727: Hotfix voor CQ-4270423

### WCM - SPA-editor

* Toegelaten het halen van pre-teruggegeven inhoud van een ver eindpunt. Hotfix voor CQ-4270238
* Waarschuwingen in logboeken wanneer het openen van een teruggegeven server-kant van de Pagina van het Malplaatje van het KUUROORD. Hotfix voor CQ-4270238

### WCM - MSM

* De verbetering aan AEM 6.4.3 maakt de Manager van de Multi-Plaats lang om uit te rollen. Hotfix voor CQ-4271410

### Integratie

* BrightEdge-referenties ontbreken bij verbindingsfout. NPR-29168: Hotfix voor CQ-4265872

* Een uitzonderingsbericht wordt getoond wanneer het proberen om de AEM lanceringsconfiguratie uit te geven en te bewaren. NPR-29176: Hotfix voor CQ-4265782/CQ-4266153

### Gebruikersinterface

* Toegevoegde steun voor het volgen dynamisch-UI-staten als douaneattributen terwijl het volgen van bepaalde gebeurtenissen in de stichting die API volgen. Hotfix voor GRANITE-26283
* De volgende functie kan niet worden ingesteld op de knop Verzenden. Hotfix voor GRANITE-26326
* De tovenaar kan niet de volgende eigenschap op voorleggen plaatsen knoop. NPR-29995, NPR-30025: Hotfix voor CQ-4264289

### Gemeenschappen

* Onbekwaam om nieuwe badges in dropdown op de pagina van het lidprofiel te richten. NPR-29381: Hotfix voor CQ-4267987
* De bezoekers en de leden, zonder moderatorvoorrechten, kunnen niet goedgekeurde/hangende posten zien door URL te kleven. NPR-29724: Hotfix voor CQ-4271124, CQ-4271441
* De hoge reactietijd tot 40-50 seconden wordt waargenomen op gebruikerslogin voor Gemeenschap. NPR-29677: Hotfix voor CQ-4269444

### Replicatie

* De component van de Agent van de replicatie is vatbaar voor een kwetsbaarheid die gevoelige informatie aan onbevoegde gebruikers openbaart. NPR-29611: Hotfix voor GRANITE-25070

* Het lek van de zitting tijdens OAuth voor elke replicatie aan het Portaal van het Merk. NPR-30001: Hotfix voor GRANITE-26196

### Projecten

* Publiceer Activa van de omslag van de Auteur AEM /content/dam/mac aan het Portaal van het Merk werkt niet. NPR-29819: Hotfix voor CQ-4271118

### Platform

* HtmlLibraryManager schrapt alle inhoud van crx-quickstart op geheim voorgeheugenongeldigverklaring. NPR-29863: Hotfix voor GRANITE-26197

### Felix

* De details van het geheugengebruik verschijnen niet in de systeemconsole wanneer u Java11\ gebruikt. NPR-29669

### Formulieren

De belangrijkste hoogtepunten voor vormen AEM 6.5.1.0 zijn:

* Alleen OSGi: Toegevoegd een nieuw attribuut `PAGECOUNT` in Output en vormt de Dienst.

* Alleen OSGI: Toegelaten steun om statische Pdf- dossiers tot stand te brengen gebruikend de Dienst van Vormen.
* Toegelaten toestemmingen op XMLForm.exe voor beheerder en wortelgebruikers.
* Toegelaten steun voor ADFS v3.0 voor Dynamica op-gebouwintegratie.

#### Formulierinvoegpakket

**Backend-integratie**

* Fout in het halen van de beschermde Taal van de Definitie van de Dienst van het Web (WSDL). NPR-29944: Hotfix voor CQ-4270777
* Wanneer de Vormen van AEM op IBM WebSphere wordt geïnstalleerd, ontbreekt het creëren van een model van vormgegevens dat op ZEEP wordt gebaseerd. Hotfix voor CQ-4251134
* Toegelaten steun voor de Actieve Diensten van de Federatie van de Folder (ADFS) v3.0 voor de Dynamica op-gebouwintegratie van Microsoft. Hotfix voor CQ-4270586
* Wanneer de titel van een gegevensbron wordt veranderd, toont het model van vormgegevens niet de bijgewerkte titel. Hotfix voor CQ-4265599
* Als de naam van een entiteit of een attribuut koppelteken of ruimte bevat, ontbreken de uitdrukkingen om dergelijke entiteiten en attributen te evalueren. Hotfix voor CQ-4225129

* De onjuiste output wordt waargenomen wanneer een dubbelpunt in de primitieve koordoutput aanwezig is. Hotfix voor CQ-4260825

* Zelfs wanneer geen inhoud van de REST API output wordt verwacht, roept de verrichting van het model van vormgegevens een fout aan. Hotfix voor CQ-4268828

**Aanpassingsvormen**

* Onbekwaam om nieuwe instantie in het Aanpassende Fragment van de Vorm toe te voegen tijdens luie lading. NPR-29818: Hotfix voor CQ-4269875
* Verifieer de component registreert of toont geen fout voor Document van de malplaatjes van het Verslag. Hotfix voor CQ-4272999
* Toegevoegde steun om lay-outredacteur voor AanpassingsVormen onbruikbaar te maken. Hotfix voor CQ-4270810
* Herstelde de verifiestap voor AanpassingsVormen in AEM 6.5 \. Hotfix voor CQ-4269583

* De adaptieve mislukking van de het gebiedsbevestiging van de Vorm breekt het Teken van Adobe. Hotfix voor CQ-4269463
* Wanneer een instantie van de Vormen van AEM meer dan 20 adaptieve vormfragmenten heeft en de naam van alle vormfragmenten begint met het zelfde koord, keert het onderzoek op of slechts recente 20 gecreeerde fragmenten terug. Hotfix voor CQ-4264414, CQ-4264914

* De kwesties van prestaties wanneer de AanpassingsVormen app met grote dataset wordt gebruikt. . Hotfix voor CQ-4235310

* Wanneer betreden door anonieme rekening op publiceert instantie, slaagt het manuscript GuideRuntime er niet in om te laden. Hotfix voor CQ-4268679

**Formulieren - Interactieve communicatie**

* Het interactieve Communicatie malplaatje maakt geen lijst van kopbal en footer componenten in toegestane componentenlijst. Hotfix voor CQ-4237895
* Wanneer u een interactief malplaatje van de communicatie drukdruk creeert dat een beeldgebied bevat, wordt de titel van de grafiek geplaatst aan spatie. Hotfix voor CQ-4264772
* De kleur van de lijn van een grafiek, wanneer geschrapt, wordt geplaatst aan niet gedefiniëerd. Hotfix voor CQ-4264762
* De de laagveranderingen van de lay-out die op het Fragment van het Document worden aangebracht verdwijnen bij het uitvoeren houden veranderingen synchronisatie. Hotfix voor CQ-4266054
* Het element van het de gegevensmodel van de vorm binnen een Fragment van het Document verbindend aan een tekstgebied toont overervingspictogram niet en staat band toe. Hotfix voor CQ-4261089
* Het Kanaal van de druk geeft API terug heeft niet de optie om gegevens als parameter in API over te gaan. Hotfix voor CQ-4263540
* De montages van de agent zijn niet zichtbaar aangezien Editable door checkbox van de Agent ongecontroleerd wordt wanneer het bindende type van het fragment van de Tekst in Geen/het ModelVoorwerp van Gegevens voor het gebied van het Koord/de variabele wordt veranderd. Hotfix voor CQ-4261953
* Voor de voorlegging van Agent UI, slaat het resulterende dossier van Webgegevens json informatie voor erfenis-geannuleerde niet verbindende gebieden op. Hotfix voor CQ-4265621

**Formulieren - Werkstroom**

* Wanneer een formulier opnieuw wordt ingediend vanuit de outbox van adaptieve formulieren app, leidt dit tot verlies van gegevens. NPR-28345: Hotfix voor CQ-4260929
* De documenten worden niet gesloten terwijl het bewaren voor niet veranderlijke gevallen. Hotfix voor CQ-4269784
* Adaptive Forms app heeft ondersteuning voor Microsoft Windows 8.1\ laten vallen. Hotfix voor CQ-4265274
* Wanneer een beeld van meer dan 2 MB als gehechtheid van het gebiedsniveau aan een vorm in de Android versie van app van Vormen AEM in bijlage is, crasht app. Hotfix voor CQ-4265578

* Toegelaten pre-populatieopties voor het Interactieve Kanaal van de Communicatie Druk in Toewijzing taak. Hotfix voor CQ-4265577
* De gebruikers kunnen geen gedeelde taak bekijken tot zij lid van de groep worden waaraan de taak wordt toegewezen. Hotfix voor CQ-4248733
* Sparen of verzend van toepassingen JEE op AanpassingsVorm app wordt geblokkeerd op Vensters. Hotfix voor CQ-4268704
* Het model van vormgegevens verbonden aan de modelvariabele van vormgegevens is niet zichtbaar. Hotfix voor CQ-4266554
* Geen steun voor de statusvariabele van documentteken gebruikend veranderlijke steun. Hotfix voor CQ-4266312
* De verklaringen van werkruimte ontbreken met umlautkarakter. Hotfix voor CQ-4263172
* Voor een promotieopstelling, als het werkschema voor het uitgeven wordt geopend, wordt een fout getoond in plaats van werkschemanaam in het gebruikersinterface van de horlogeomslag (UI). Hotfix voor CQ-4238579

**Formulieren - Beheer**

* Wanneer een uitbreiding buiten xsd of schema.json wordt geupload, upload niet gebeurt en, geen foutenmelding wordt geproduceerd. Hotfix voor CQ-4266716

**Formulieren - Correspondentiebeheer**

* AEM 6.5 de Vormen leiden tot Correspondentie UI (CCR UI) er niet in om correspondentie te openen die met AEM 6.3 Vormen wordt gecreeerd. Hotfix voor CQ-4266392
* De functie van de som in XDP werkt niet als het DDE gegevenstype van typeaantal is. Hotfix voor CQ-4227403
* De de invalidatielogica van het in-geheugengeheime voorgeheugen van brieven die moeten worden bijgewerkt, omdat wanneer een activa wordt gepubliceerd, zijn laatste gewijzigde tijd niet wordt bijgewerkt. Hotfix voor CQ-4250465
* Kan documentfragment, DD &amp; Letters niet publiceren. Hotfix voor CQ-4272893

#### Forms JEE-installateur

**PDF-generator**

* De CAD-bestanden naar PDF-conversie zijn mislukt met 64-bits JDK. NPR-29924, NPR-29925: Hotfix voor CQ-4272113
* Verving de naam van PhantomJS aan WebToPDF voor omzetting HTMLtoPDF. NPR-29933: Hotfix voor CQ-4234545
* Er wordt een fout gegenereerd bij het converteren van zip-bestand naar PDF. Hotfix voor CQ-4268628

**Formulieren - Ontwerper**

* Wanneer een volledige toegankelijkheidscontrole op statische PDF wordt uitgevoerd die gebruikend de Ontwerper van de Vorm AEM wordt gecreeerd, ontbreekt de Primaire controle van de Taal toe te schrijven aan het missen van taalattributen. Hotfix voor CQ-4272923, CQ-4271002

**Formulieren - Documentbeveiliging**

* De digitale Handtekening met de Module van de Veiligheid van de Hardware (HSM) werkt niet aan OSGi Linux op Java 11 en Java 8 \. NPR-29838: Hotfix voor CQ-4270441
* De digitale handtekening met de Module van de Veiligheid van de Hardware (HSM) werkt niet aan JEE Linux, en alle gesteunde app servers, d.w.z., JBoss en Websphere. NPR-29839: Hotfix voor CQ-4266721
* Het verifiëren van handtekeningen in een PDF gebruikend PDF de Geavanceerde Elektronische Handtekeningen (PAdES) produceert OngeldigeOperationException. NPR-29842: Hotfix voor CQ-4244837
* Extra ondersteuning voor documentbeveiligingsextensie voor Office 2019\. Hotfix voor CQ-4254369, CQ-4259764

**Formulieren - Documentservices**

* PDF kan niet worden geconverteerd naar PDF/A-1b met het veld Formulier zonder weergavekaart. NPR-29940: Hotfix voor CQ-4269618

* OSGi: Onbekwaam om het aantal pagina&#39;s te bepalen die tijdens het teruggeven worden geproduceerd. NPR-28922: Hotfix voor CQ-4270870
* Toegelaten steun voor Statische Pdf- dossiers gebruikend de Dienst van Vormen in AEM Vormen OSGi. NPR-28572: Hotfix voor CQ-4270869
* Onbekwaam om de toestemmingen op XMLForm.exe te veranderen. NPR-29828, NPR-29237: Hotfix voor Q-4267080
* De statische PDF die door de de outputmodule van de server van Vormen AEM wordt gecreeerd bevolkt niet de taalattributen/de markering met de taal van het gecreeerde document. NPR-27332: Hotfix voor CQ-4271002

**Formulieren - Foundation JEE**

* Niet beschikbaar pdfg_srt in definitieve artefacten veroorzaakt de installateur om te ontbreken. NPR-29854: Hotfix voor CQ-4270137
* LCBackupMode.sh werkt niet. NPR-29840: Hotfix voor CQ-4269424
* De UDP havenverwijzing zou uit gebruikersinterface (UI) voor WebSphere moeten worden verwijderd. Hotfix voor CQ-4264782

### Inclusief functiepakketten

#### Activa - inbegrepen

* Ondersteuning voor beheer op meerdere sites voor bedrijfsmiddelen. Voor meer informatie, zie [Hergebruik activa gebruikend MSM voor Activa](https://helpx.adobe.com/experience-manager/6-5/help/assets/reuse-assets-using-msm.html). NPR-29199: Hotfix voor CQ-4259922

#### Locaties - inbegrepen

* De Fragmenten van de Ervaring van de uitvoer AEM naar het Doel van Adobe. Voor meer details, zie [de Verbinding Rewriter Provider van de Verbinding van het Fragment van de Ervaring - HTML](https://helpx.adobe.com/experience-manager/6-5/help/sites-developing/experience-fragments.html#TheExperienceFragmentLinkRewriterProviderHTML). Hotfix voor CQ-4265469

#### Formulieren - Documentservices - inbegrepen

* Alleen OSGi: Toegevoegd een nieuwe attribuut PAGECOUNT in Output en vormt de Dienst. NPR-28922: Hotfix voor CQ-4270870
* Alleen OSGi: Toegelaten steun om statische Pdf- dossiers tot stand te brengen gebruikend de Dienst van Vormen. NPR-28572: Hotfix voor CQ-4270869
* Toegelaten toestemmingen op XMLForm.exe voor beheerder en wortelgebruikers. NPR-29237: Hotfix voor CQ-4267080

### OSGi-bundels en inhoud-pakketten

De volgende tekstdocumenten maken een lijst van de bundels OSGi en de Pakketten van de Inhoud inbegrepen in AEM 6.5.1.0

Lijst van OSGi-bundels in AEM 6.5.1.0

[Bestand ophalen](assets/6_5-bundle-list.txt)

Lijst van de Inhoud Pakketten inbegrepen in AEM 6.5.1.0

[Bestand ophalen](assets/6_5-content-package-list.txt)
