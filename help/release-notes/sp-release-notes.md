---
title: Opmerkingen bij de release AEM 6.5 Service Pack
description: Opmerkingen bij de release specifiek voor Adobe Experience Manager 6.5 Service Pack 3.
uuid: c7bc3705-3d92-4e22-ad84-dc6002f6fa6c
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5
discoiquuid: 25542769-84d1-459c-b33f-eabd8a535462
docset: aem65
translation-type: tm+mt
source-git-commit: 9f4a460c7f64d86e35e950e512ed5b6cda1cbf2a

---


# Opmerkingen bij de release Adobe Experience Manager 6.5 Service Pack {#aem-service-pack-release-notes}

## Geen informatie {#release-information}

| Producten | **Adobe Experience Manager 6.5** |
|---|---|
| Versie | 6.5.3.0 |
| Type | Service Pack-release |
| Date | 12 december 2019 |
| URL downloaden | [PackageShare](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/servicepack/AEM-6.5.3.0) |

## Wat is inbegrepen in de Manager van de Ervaring van Adobe 6.5.3.0 {#what-s-included-in-aem}

Adobe Experience Manager 6.5.3.0 is een belangrijke release met oplossingen en verbeteringen voor prestaties, stabiliteit, beveiliging en belangrijke klanten sinds de algemene beschikbaarheid van de 6.5-release in **april 2019**. Het bestand kan boven op Adobe Experience Manager (AEM) 6.5 worden geïnstalleerd.

Enkele belangrijke hoogtepunten van deze service pack-release zijn:

* De ingebouwde opslagplaats (Apache Jackrabbit Oak) wordt bijgewerkt naar versie 1.10.6.

* De Middelen van de Manager van de ervaring steunen nu ZIP archieven die gebruikend Deflate 64 algoritme worden gecreeerd.

* Er is een nieuwe kolom voor de gemaakte datum toegevoegd aan de DAM-lijstweergave en de zoekresultaten voor elementen in de lijstweergave. Deze kolom kan worden gesorteerd.

* Asset sorting based on Name column is enabled in de mening van de Lijst.

* Dynamische media ondersteunt nu SmartCrop-video-elementen. Slim uitsnijden is een door computers aangedreven functie die een video bijsnijdt terwijl het frame wordt verplaatst om het brandpunt van de scène te volgen.

* Dynamische media ondersteunt Smart Imaging.

* Mogelijkheid om [voorkeuren voor kantoorgebruik](../forms/using/configure-out-of-office-settings.md) in AEM-workflows in te stellen.

* Mogelijkheid om items [in Postvak IN of Postvak IN te](../forms/using/configure-shared-queues-osgi.md) delen met andere gebruikers in AEM-workflows.

* De capaciteit om Interactieve Mededelingen op een wijze [van de Partij te](../forms/using/generate-multiple-interactive-communication-using-batch-api.md)produceren.

* Bijgewerkte versie van jQuery die in ContextHub aan 3.4.1 wordt gebundeld.

### Lijst met wijzigingen {#list-of-changes}

#### Assets {#assets-6530-enhancements}

**Verbeteringen voor producten**

* De Middelen van de Manager van de ervaring steunt nu ZIP archieven die gebruikend Deflate 64 algoritme (NPR-27573) worden gecreeerd.

* Er is een nieuwe kolom voor de aanmaakdatum toegevoegd, die sorteerbaar is, in de DAM-lijstweergave en in de resultaten voor het zoeken naar middelen in de lijstweergave (NPR-31312).

* Asset sorting based on Name column is allowed in List view (NPR-31299).

* De GLB-, GLTF-, OBJ- en STL-elementbestanden ondersteunen voorvertoning van elementen op de pagina Asset Details in DAM (CQ-4282277).

* ReplicationOnModifyListener-gebeurtenis wordt geactiveerd voor segmentknooppunten tijdens het uploaden van een segment in Dynamic Media (CQ-4281279).

* Dynamische media ondersteunt nu SmartCrop-video-elementen. Slim uitsnijden is een door computers aangedreven functie die een video bijsnijdt terwijl het frame wordt verplaatst om het brandpunt van de scène te volgen (CQ-4278995).

* Dynamische media ondersteunt Smart Imaging (CQ-4222249).

* De onderzoek/doorbladermening is geplaatst als standaardmening in de plukker van de Stichting als de vraagparameters in verzoek worden overgegaan (NPR-31601).

**Oplossingen**

* Metagegevens voor sommige PDF-documenten worden niet bijgewerkt en naar de PDF opgeslagen bij het wijzigen van de titel (NPR-31629).

* Delen van activa werkt niet voor activa met het plusteken (+) in hun naam (NPR-31547).

* Bewerkingen in het standaardzoekformulier Middelen Admin * Search Rail werken niet zoals verwacht (NPR-31502).

* Suggesties worden niet weergegeven wanneer u OmnZoeken op middelen gebruikt om middelen te zoeken (NPR-31496).

* Verwijzingen naar activa binnen verzamelingen worden niet bijgewerkt wanneer de betreffende activa naar een andere locatie worden verplaatst, in gevallen waarin naar dezelfde activa wordt verwezen door verschillende inzamelingen door verschillende gebruikers (NPR-31486).

* Er worden dubbele IPTC-tags toegevoegd aan metagegevens van elementen (NPR-31328).

* Het aantal zoekresultaten in de rechterbovenhoek wordt niet correct bijgewerkt wanneer het zoeken wordt gestart vanuit de filterrail (NPR-31316).

* Alle selectievakjes worden gewist wanneer de selectie van de selectievakjes van het tweede niveau in het filter Bestandstype ongedaan wordt gemaakt en de tekst in de zoekbalk is niet synchroon met de geselecteerde/niet-geselecteerde eigenschappen (NPR-31287).

* Niet alle leden (gebruikers/groepen) kunnen worden verwijderd uit de sectie Leden van een map. wanneer wordt geprobeerd om alle gebruikers te verwijderen, wordt de aangemelde gebruiker toegevoegd aan de lijst (NPR-31171).

* Elementen met het plusteken (+) in de bestandsnaam kunnen niet worden verwijderd (NPR-31162).

* Het keuzemenu Maken, dat in het bovenste menu zichtbaar is wanneer u een map selecteert, geeft &#39;Map&#39; niet weer als een optie voor maken (NPR-30877).

* Mapselectie Maken > Handelitem FileUpload ontbreekt wanneer ACL voor Deny jcr:removeChildNodes en jcr:removeNode op pad wordt toegepast voor een gebruiker (NPR-30840).

* De DAM-workflows worden in de status &#39;stale&#39; gezet wanneer bepaalde MP4-middelen worden geüpload, waardoor alle resterende workflows in de status &#39;stale&#39; gaan (NPR-30662).

* Er is een fout ten gevolge van onvoldoende geheugen opgetreden wanneer grote PDF-bestanden (met meerdere gigabytes) naar DAM worden geüpload en de bijbehorende subbestanden worden verwerkt (NPR-30614).

* Bulkverplaatsing van activa mislukt en geeft een waarschuwingsbericht weer (NPR-30610).

* Namen van middelen worden gewijzigd in kleine letters wanneer u elementen verplaatst van de ene map naar de andere in AEM die wordt uitgevoerd in de runmode van Dynamic Media Scene 7 (NPR-31630).

* Er is een fout opgetreden tijdens het bewerken van een externe imageset voor de afbeelding die zich in de map met dezelfde naam bevindt als de bedrijfsnaam van Scene 7 (NPR-31340).

* Dynamische media-elementen met referenties worden niet gepubliceerd (NPR-31180).

* Het uploaden van dynamische media van AEM - runmode 7 aan Scene 7 duurt te lang om (NPR-31048) te voltooien.

* Hotspot die aan een afbeeldingselement is toegevoegd, is niet zichtbaar via de Interactive Image Viewer op de pagina met elementdetails (NPR-30979).

* Er worden enorme slingerbanen gecreëerd en de verwerkingsbanner wordt weer opgebouwd wanneer acties op activa in AEM Assets worden doorgegeven aan Scene 7 (NPR-30947).

* Conflict doet zich voor bij het maken van Taalkopie van middelen en middelen wordt niet geüpload naar scène 7 (NPR-30932).

* Dynamische vertoningen die zijn gedownload van AEM en die worden uitgevoerd in de dynamische media-hybride modus, worden verbroken (ze zijn van het teksttype met inhoud die &#39;geen afbeelding kan vinden&#39; in plaats van het type afbeeldingsinhoud) (NPR-30876).

* De dynamische werkstroom van Media Encode Video ontbreekt om duimnagel voor de video te produceren die van Scene 7 aan Dynamische Media - de loopwijze van Scène 7 wordt gemigreerd (CQ-4282011).

* IpsApiException waargenomen terwijl het migreren van activa van één instantie aan een andere gebruikend verschillende Scene 7 bedrijfs IDs (CQ-4280548).

* De miniatuur van 3D-middelen is niet informatief wanneer een ondersteund 3D-model wordt opgenomen in AEM (CQ-4283701).

* Schuifknoppen worden weergegeven in de viewer als een 3D-element maar weinig cameraweergaven heeft (CQ-4283322).

* Onjuiste containerhoogte van een geüpload 3D-model, voorvertoond in DimensionalViewer op de pagina Asset Details (CQ-4283309).

* Video&#39;s kunnen niet worden afgespeeld met SmartCropVideoViewer in Internet Explorer 11 en Safari (CQ-4281422).

* Het gebruik van de verplaatsingsknop om meerdere elementen van de ene map naar de andere te verplaatsen, mislukt in AEM en wordt uitgevoerd op Dynamic Media - scene7 runmode (CQ-4280384).

* Vervormde video wordt weergegeven op de elementdetails wanneer het MIME-type niet MP4 is (CQ-4279704).

* Video&#39;s die onlangs in mappen met videoprofiel zijn opgenomen, worden nog steeds verwerkt nadat het coderingspercentage is voltooid tot 100% (CQ-4279389).

* Als u elementen uit een map verplaatst, ontstaan er veel slingertaken (API-aanroepen voor scène 7) dan ideaal is vereist (CQ-4278664).

* Namen van de imageset worden in scène 7 gewijzigd in kleine letters wanneer imageset (of mediaset) wordt gemaakt en benoemd met de juiste naamgevingsconventie in DAM (CQ-4281112).

* Scene 7 de reeksen van de Migrator publiceren verkeerd staat (CQ-4263492).

* De resultatenpagina Touch UI-zoekopdracht (uitgevoerd via Omnissearch) wordt automatisch naar boven geschoven en verliest de schuifpositie van de gebruiker in Content Fragments (CQ-4282898).

* PDF-bestanden zijn niet geïndexeerd en de inhoud in deze bestanden kan niet worden doorzocht (CQ-4278916).

* Een fout &quot;Groep niet vermeld door de plukker van de gebruiker: onwaar naar verwacht gelijk aan true&quot; wordt waargenomen bij het toevoegen van een gesloten gebruikersgroep met andere `principalName` en `authorizableId` (CQ-4278177).

* De Mening van de Kolom UI van activa toont alle wegen ongeacht de de dampwortel van specifieke huurder weg (CQ-4278175).

* Het zoeken door de kiezer van middelen werkt niet zoals verwacht (CQ-4275886).

* Workflows voor uitvoering ontbreken (CQ-4271928).

* DAM Event Purge verwijdert de meest recente (maxSavedActivity) gebeurtenisgegevens en bevat de gegevens die eerder zijn gemaakt (NPR-31336).

* De resultatenpagina Touch UI-zoekopdracht (uitgevoerd via Omnissearch) wordt automatisch naar boven geschoven en verliest de schuifpositie van de gebruiker (NPR-31307).

* De actiebalk en het aantal elementen worden niet bijgewerkt wanneer u alle items selecteert en vervolgens de selectie van bepaalde items (mappen/afzonderlijke elementen) in Touch UI (NPR-31118) opheft.

* Een uitzondering wordt weergegeven in AEM tijdens het opvragen voor taakdetails van een element (CQ-4283569).

* XSS-kwetsbaarheid in DAM (NPR-31654).

#### Sites {#sites}

* Als de overerving van LiveCopy is verbroken, worden op live kopieerpagina&#39;s links naar taalkopieën weergegeven in plaats van LiveCopy-koppelingen (NPR-30980).
* Voor een nieuwe blauwdruk, als het aantal verslagen meer dan 40 is, slechts worden de eerste 40 verslagen getoond. Blauwdruk geeft lege regels weer voor de rest van de records (NPR-31182).
* Wanneer een gebruiker Japanse of Koreaanse karakters in het beschrijvingsbezit van een menu toevoegt, toont het menu vervormde karakters voor Japanse en Koreaanse taaltekst. (NPR-31331).
* De Rich Text Editor (RTE) staat niet toe om een ingesloten tabel in te voegen als lijstitem (NPR-30879).
* Buiten het vak, de basislijn van de Rich Text Editor (RTE). past inline font-size toe op elementen, onverwacht (NPR-31284).
* Wanneer een gebruiker de linkerspoorgebieden concentreert en een toetsenbordkortere weg gebruikt om inhoud te kleven, kleeft het de inhoud van het paginageditor klembord in plaats van de inhoud die van de linkerspoorgebieden wordt gekopieerd (NPR-31172).
* Wanneer een gebruiker een veld Bestand uploaden toevoegt aan een veld met meerdere velden, wordt het afbeeldingspad opgeslagen in het componentknooppunt in plaats van het knooppunt met meerdere velden (NPR-30882).
* De API ResponsiveGridExporter retourneert de interface com.day.cq.wcm.foundation.model.impl.export.AllowedComponentsExporter niet. Het pakket com.day.cq.wcm.foundation.model.impl wordt gedeclareerd als een privépakket (NPR-31398).
* Wanneer een pagina die sommige ExperienceFragments bevat op niet redacteurswijze (of in Auteur zonder het `editor.html` voorvoegsel en `wcmmode=disabled`, of in Uitgever) wordt geopend., beëindigt het verzoek in code 500 van de de statusfout van HTTP (NPR-30743).
* Gebruikers kunnen hun wachtwoord niet wijzigen en toegang krijgen tot hun profielpagina (NPR-31161).
* Een JavaScript-bestand met gebruikersgegevens wordt gegenereerd aan de serverzijde (NPR-30822).
* In de gebruikersinterface van AEM-authoring is phishing met behulp van externe inhoud mogelijk (NPR-29745).
* Expressietaalinjectie-kwetsbaarheid in AEM 6.5-metagegevenseditor (NPR-31017).

#### Zoeken en gebruikersinterface {#search-ui-interface}

* Wanneer u op een pagina met zoekresultaten overschakelt van de weergave Kaart naar de weergave Lijst, is er een vertraging voordat de pagina kan worden geschoven (NPR-31286).

* Het selectievakje Alles selecteren is verborgen in de lijstweergave op sites-gebruikersinterface (NPR-31614).

* Het aantal selecties op een pagina met zoekresultaten is onjuist (NPR-31120).

* In de metagegevenseditor worden tags weergegeven die niet bestaan (NPR-31119).

#### Vertaling {#translation}

* Er worden twee kalenderpop-ups weergegeven bij het selecteren van de optie Einddatum in een vertaaltaak (NPR-31270).

#### Platform {#platform}

* De Mime typeoptie in de console van het Web werkt niet (NPR-31108).

* Clientcertificaat wordt niet geaccepteerd bij het configureren van Single Sign-On (NPR-31165).

* Updates in de configuratie van de buffergrootte voor de op Jetty-Gebaseerde dienst van HTTP worden niet bewaard (NPR-30925).

* QueryBuilder steunt nu orde ``fn:name()`` in xpath vragen (NPR-31322).

* Er wordt een dubbele activeringsstructuur gemaakt bij een upgrade van AEM 6.3 (NPR-31513).

* Door:sturen verzoeken bewaren antwoordkopballen niet die tijdens het verbinden authentificatie (NPR-30013) worden geplaatst.

* Zoeken in de kiezercomponenten werkt niet (NPR-31692).

* Er wordt een fout weergegeven bij het koppelen van een ZIP-bestand aan een AEM Communities-post vanwege verschillende versies van Apache POI en Apache Tika bundle (NPR-31018).

* De ``org.apache.sling.distribution.api`` bundel is verborgen in de configuratiemanager en is daarom niet beschikbaar voor aangepaste bundels (NPR-31720).

#### Projecten {#projects}

* Schakelen tussen kalenderweergaven werkt niet (NPR-31271).

#### Brand Portal {#assets-brand-portal}

**Verbeteringen voor producten**

* Workflow voor het importeren van middelen via Asset Sourcing in AEM Assets is gewijzigd om alleen de nieuw gemaakte middelen van Brand Portal naar AEM op te halen, en slaat de elementen over die al in de map NEW staan om replicatie te voorkomen (CQ-4278527).

**Oplossingen**

* Er wordt een onjuist pictogram weergegeven bij het maken van een nieuwe map voor bijdragen in de functie voor het zoeken naar middelen (CQ-4282825).
* Bij het maken van een nieuwe Contribute-map worden een of beide submappen (NEW en SHARED) niet weergegeven in de map Contribution (CQ-4282424).
* Het systeem genereert een uitzondering als de gebruiker probeert om de omslag van de Bijdrage van AEM aan het Portaal van het Merk opnieuw te publiceren na het ontvangen van nieuwe activa in de omslag van de Bijdrage van het eind van het Portaal van het Merk (CQ-4279740).
* Het is niet toegestaan om een Contribute-map te maken in een map met bijdragen (geneste map) om complexiteit te voorkomen (CQ-4278391).
* Het systeem genereert een uitzondering bij het uploaden van de gebruikerslijst voor het Brand Portal (.csv-bestand) die is geïmporteerd uit AEM Admin Console. Alleen de velden E-mail, Voornaam en Achternaam in het CSV-bestand zijn verplicht (CQ-4278390).

#### Gemeenschappen {#communities}

**Oplossingen**

* Snelle koppelingen voor het beheer van groepen (groepen Openen/Bewerken/Publiceren/Verwijderen) zijn niet zichtbaar voor de communautaire beheerders (beheer van groep/site) (NPR-31627).
* Een verzonden blog wordt alleen weergegeven als de pagina handmatig wordt vernieuwd of opnieuw wordt geladen (NPR-31599).
* De JCR-query die wordt gebruikt door de functie &quot;Misions&quot; is hoofdlettergevoelig en het duurt te lang om resultaten te retourneren (NPR-31475).
* AEM 6.5 UberJar-bestand genereert een uitzondering. Er ontbreekt een `cq-social-translation` bundel in AEM 6.5 UberJar-bestand (NPR-31186).
* Jackson Databind-bibliotheken bijgewerkt naar versie 2.9.9.3 om nieuwe kwetsbaarheden te verhelpen (NPR-30967).
* Activiteiten en aanmeldingstitels zijn inconsistent (NPR-30941).
* Paginering werkt niet correct in Community-blogs (NPR-30914).
* Rapporten over analysemogelijkheden worden niet gevuld in de AEM-auteuromgeving. Er wordt een lege pagina weergegeven (NPR-30913).

#### Eik {#oak}

* De indexupdates van Lucene die auteurserver veroorzaken om te vertragen (NPR-31548).

#### Formulieren {#forms-6530}

>[!NOTE]
>
>AEM Service Pack bevat geen oplossingen voor AEM-formulieren. Ze worden geleverd met behulp van een apart Forms add-on pakket. Daarnaast wordt een cumulatief installatieprogramma uitgebracht dat oplossingen voor AEM Forms in JEE bevat. Zie [Invoegtoepassing](#install-aem-forms-add-on-package) van AEM-formulieren installeren en AEM-formulieren [installeren in JEE](#install-aem-forms-jee-installer)voor meer informatie.

##### Formulierinvoegpakket {#forms-add-on-package-6530}

**Adaptieve formulieren**

* Tekenreeksen bevatten de woordenboeksleutel bij het lokaliseren van adaptieve formulieren (NPR-31110).

**Interactieve communicatie**

* **MissingNode.toString()** retourneert onjuiste resultaten nadat Jackson-bibliotheken zijn bijgewerkt naar 2.10.0 (NPR-31549).

* Teksteditor verwijdert willekeurig spatietekens uit de tekst die uit Microsoft Word is gekopieerd (NPR-31113).

**Correspondentenbeheer**

* Bijschriften en knopinfo worden niet weergegeven tijdens het migreren van letters van LiveCycle ES4SP1 naar AEM 6.5 (NPR-31615).

* **De opmaak van TextFlow wordt niet meer ondersteund** tijdens het opslaan van letters als concepten (NPR-30463).

**Workflow**

* OSGi-workflow mislukt als gevolg van 100% CPU-gebruik (NPR-31233).

**HTML5-formulieren**

* Als u HTML5-voorbeeld van een XDP-formulier genereert, wordt een flikkering weergegeven terwijl exemplaren van een subformulier worden toegevoegd (NPR-30909).

##### Formulieren bij JEE-installatieprogramma {#forms-jee-installer-6530}

**Formulieren - Document Services**

* De de Webdienst van de ZEEP die MTOM in een .NET project gebruikt toont uitzonderingen voor AssemblerServiceClient aanhaalt en methodes HtmlToPDF2 (NPR-4281771).

**Foundation JEE**

* De configuratie van de actie laadt niet de procesnamen voor Invoke a Forms Workflow submit actie (NPR-31478).
* AEM Forms on JEE-gebruikers ondervinden soortgelijke fouten bij het importeren van .lca-bestanden of het instellen van LDAP in beheerconsole:

   `com.ibm.ws.webcontainer.filter.FilterInstanceWrapper doFilter SRVE8109W: Uncaught exception thrown by filter um: java.lang.NoClassDefFoundError: org/apache/commons/io/IOUtils at org.apache.commons.fileupload.util.Streams.copy`

   `Error 500: javax.servlet.ServletException: java.lang.NoClassDefFoundError: org.apache.commons.io.IOUtils` (NPR-30931)


### Inclusief functiepakketten {#feature-packs-included-6530}

>[!NOTE]
>
>Voor klanten van AEM Forms, is het essentieel om toe:voegen-op pakket van Vormen AEM te installeren na het installeren van om het even welk AEM Service Pack, Cumulative Fix Pack, of het Pak van de Eigenschap.

#### Formulieren - Foundation JEE {#forms-foundation-jee-feature}

* AEM Forms support for Oracle 18c (NPR-29155).

## Installeer 6.5.3.0 {#install}

**Installatievereisten**

* AEM 6.5.3.0 vereist AEM 6.5. Raadpleeg de [upgradedocumentatie](/help/sites-deploying/upgrade.md) voor gedetailleerde instructies.
* De download van het Service Pack is beschikbaar op het Aandeel van het Pakket van Adobe, dat u direct van AEM 6.5 instantie kunt toegang hebben.
* Voor een plaatsing met MongoDB en veelvoudige instanties, installeer AEM 6.5.3.0 op één van de instanties van de Auteur gebruikend de Manager van het Pakket.
* Voordat u het servicepack installeert, moet u zorgen dat u een momentopname of een nieuwe back-up van uw AEM-instantie hebt.
* Start de instantie opnieuw voor de installatie. Hoewel dat alleen nodig is wanneer de instantie zich nog in de updatemodus bevindt (en dit is het geval wanneer de instantie uit een eerdere versie is bijgewerkt), wordt aangeraden of de instantie langer actief was.

>[!CAUTION]
>
>Adobe raadt u niet aan het pakket AEM 6.5.3.0 te verwijderen of te verwijderen.

### Service Pack installeren via delen pakket {#install-service-pack-via-package-share}

Voer de volgende stappen uit om het Service Pack op een bestaande AEM 6.5 instantie te installeren:

1. Meld u aan bij Delen via pakket vanuit AEM of rechtstreeks vanuit uw browser en download het pakket [](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/servicepack/AEM-6.5.3.0)AEM 6.5.3.0.

1. Installeer het gedownloade pakket met Package Manager.

>[!NOTE]
>
>**Dialoogvenster over de UI van de Manager van het Pakket sluit soms ongeschikt tijdens installatie van 6.5.3.0**
>
>Daarom wordt aangeraden te wachten totdat de foutenlogboeken zich stabiliseren voordat u de instantie opent. De gebruiker moet op specifieke logboeken met betrekking tot het verwijderen van updaterbundel wachten alvorens wordt gewaarborgd dat de installaties succesvol zijn. Het gebeurt meestal in Safari, maar kan af en toe in elke browser gebeuren.

**Automatische installatie**

Er zijn twee manieren om AEM 6.5.3.0 in een lopende instantie automatisch te installeren:

A. Plaats de verpakking in ...*/crx-quickstart/install* folder terwijl de server online beschikbaar is. Het pakket wordt automatisch geïnstalleerd.

B. Gebruik de [HTTP API van de Manager](https://docs.adobe.com/content/docs/en/crx/2-3/how_to/package_manager.html) van het Pakket - zorg ervoor dat u cmd=install&amp;recursive=true gebruikt - zodat worden de genestelde pakketten geïnstalleerd.

>[!NOTE]
>
>AEM 6.5.3.0 ondersteunt geen Bootstrap-installatie.

**Installatie valideren**

1. Op de pagina Productinformatie (/system/console/productinfo) wordt de bijgewerkte versietekenreeks weergegeven `Adobe Experience Manager, Version 6.5.3.0` onder Geïnstalleerde producten.

1. Alle OSGi-bundels zijn **[!UICONTROL ACTIEF]** of **[!UICONTROL FRAGMENT]** in de Console OSGi (de Console van het Gebruik: /systeem/console/bundels).
1. De OSGI-bundel org.apache.jackrabbit.oak-core bevindt zich op versie 1.10.6 of hoger (gebruik webconsole: /systeem/console/bundels).

Raadpleeg de [technische vereisten](/help/sites-deploying/technical-requirements.md)om te zien welke platforms zijn gecertificeerd voor uitvoering met deze release.

### AEM Forms add-on-pakket installeren {#install-aem-forms-add-on-package}

>[!NOTE]
>
>Sla dit over als u geen AEM-formulieren gebruikt. Correcties in AEM Forms worden geleverd via een afzonderlijk invoegpakket.

>[!NOTE]
>
>AEM 6.5.3.0 bevat een nieuwe versie van het compatibiliteitspakket voor [AEM-formulieren](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/compatpack/AEM-FORMS-6.5.3.0-COMPAT). Als u een oudere versie van het compatibiliteitspakket voor AEM-formulieren gebruikt en bijwerkt naar AEM 6.5.3.0, installeert u de nieuwste versie van het compatibiliteitspakket voor AEM-formulieren na de installatie van het insteekpakket Forms.

1. Controleer of u het AEM Service Pack hebt geïnstalleerd.
1. Download het overeenkomstige Forms add-on-pakket dat in de [AEM Forms-releases](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) voor uw besturingssysteem wordt vermeld.
1. Installeer het add-on pakket Formulieren zoals beschreven in de [invoegpakketten](../forms/using/installing-configuring-aem-forms-osgi.md#install-aem-forms-add-on-package)voor AEM Forms.

### AEM-formulieren installeren op JEE {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Sla dit over als u AEM Forms niet gebruikt op JEE. Correcties in AEM Forms on JEE worden geleverd via een afzonderlijk installatieprogramma.

Voor informatie over het installeren van de cumulatieve installateur voor Vormen AEM op JEE en post-plaatsing configuratie, zie de [versienota&#39;s voor flard 0007](https://helpx.adobe.com/aem-forms/quick-fixes/6-5/jee-patch-0007.html).

#### Workbench-installatieprogramma

Aangezien het een volledig installatieprogramma is, is de bestandsgrootte groter dan bij de patchversie. Verwijder de vorige Workbench-versie voordat u de nieuwe installeert.

## UberJar {#uber-jar}

De UberJar voor AEM 6.5.3.0 is beschikbaar in de [openbare gegevensopslagplaats](https://repo.adobe.com/nexus/content/groups/public/com/adobe/aem/uber-jar/6.5.3/)van Adobe.

Om UberJar in een Geweven project te gebruiken, verwijs naar het artikel, [hoe te UberJar](/help/sites-developing/ht-projects-maven.md) gebruiken en de volgende gebiedsdeel in uw projectPOM omvatten:

```shell
<dependency>
      <groupId>com.adobe.aem</groupId>
      <artifactId>uber-jar</artifactId>
      <version>6.5.3.0</version>
      <classifier>apis</classifier>
      <scope>provided</scope>
</dependency>
```

## Verouderde functies {#removed-deprecated-features}

Deze sectie bevat een lijst met functies en mogelijkheden die zijn gemarkeerd als verouderd in AEM 6.5.3.0. Functies die volgens plan in een toekomstige versie zullen worden verwijderd, worden eerst op afgekeurd ingesteld, met een andere optie die moet worden gebruikt.

Klanten wordt aangeraden na te gaan of zij in hun huidige implementatie gebruik maken van de functie of het vermogen en plannen maken om hun implementatie te wijzigen en de alternatieve optie te gebruiken.

| Gebied | Functie | Vervanging |
|---|---|---|
| Integraties | Het scherm **[!UICONTROL AEM Cloud Services Opt-In]** is verouderd. Met de integratie van AEM en Doel bijgewerkt in AEM 6.5 ter ondersteuning van de standaard-API van het Doel, die verificatie via Adobe IMS en I/O gebruikt, en de groeiende rol van Adobe Launch voor het van instrumenten voorzien van AEM-pagina&#39;s voor analyses en personalisatie, is de Opt-In-wizard functioneel irrelevant geworden. | Systeemverbindingen, Adobe IMS-verificatie en Adobe I/O-integratie configureren via de respectievelijke AEM-cloudservices |

## Bekende problemen {#known-issues}

* Als de **Verbonden tovenaar van de middelenconfiguratie** een 404 foutenmelding na het installeren van AEM 6.5.3.0 terugkeert, installeer manueel de **cq-remotedam-cliënt-ui-content** en **cq-remotedam-cliënt-ui-componenten** pakketten gebruikend de Manager van het Pakket opnieuw.
* De volgende fouten en waarschuwingsberichten kunnen tijdens de installatie van AEM 6.5.x.x worden weergegeven:
   * &quot;Wanneer de integratie van het Doel in AEM gebruikend de StandaardAPI van het Doel (authentificatie IMS) wordt gevormd, dan leidt het uitvoeren van de Fragmenten van de Ervaring naar Doel in verkeerde aanbiedingstypes die worden gecreeerd. In plaats van het type &quot;Experience Fragment&quot;/bron &quot;Adobe Experience Manager&quot;, creëert Target verschillende aanbiedingen met het type &quot;HTML&quot;/source &quot;Adobe Target Classic&quot;.
   * com.adobe.granite.Maintenance.impl.TaskScheduler: Geen onderhoudsvensters gevonden bij graniet/bediening/onderhoud.
   * De adaptieve servervalidatie van het formulier mislukt wanneer statistische functies zoals SUM, MAX en MIN worden gebruikt. CQ-4274424
   * com.adobe.granite.Maintenance.impl.TaskScheduler - Geen onderhoudsvensters gevonden bij graniet/bewerkingen/onderhoud.
   * Hotspot in een interactieve afbeelding van dynamische media is niet zichtbaar tijdens een voorvertoning van het element via de Shopable Banner-viewer.

## OSGi-bundels en inhoudspakketten inbegrepen {#osgi-bundles-and-content-packages-included}

De volgende tekstdocumenten maken een lijst van de bundels OSGi en de Pakketten van de Inhoud inbegrepen in AEM 6.5.3.0

Lijst van OSGi-bundels opgenomen in AEM 6.5.3.0

[Bestand ophalen](assets/6530_bundles.txt)

Lijst met inhoudspakketten die zijn opgenomen in AEM 6.5.3.0

[Bestand ophalen](assets/sp_6530_packages.txt)

## Nuttige bronnen {#helpful-resources}

* [Opmerkingen bij de release AEM 6.5](/help/release-notes/release-notes.md)
* [AEM-productpagina](https://www.adobe.com/marketing/experience-manager.html)
* [AEM 6.5-documentatie](https://helpx.adobe.com/support/experience-manager/6-5.html)
* Abonneren op [Adobe-productupdates met prioriteit](https://www.adobe.com/subscription/priority-product-update.html)

## Beperkte sites {#restricted-sites}

Deze sites zijn alleen beschikbaar voor klanten. Neem contact op met uw accountmanager van Adobe als u een klant bent en toegang nodig hebt.

* [Productdownload op licensing.adobe.com](https://licensing.adobe.com/)
* [Neem contact op met de klantenondersteuning](https://daycare.day.com/public/contact.html)Voor meer informatie over de toegang tot het ondersteuningsportaal raadpleegt u [Toegang tot het ondersteuningsportal](https://helpx.adobe.com/experience-manager/kb/accessing-aem-support-portal.html).
