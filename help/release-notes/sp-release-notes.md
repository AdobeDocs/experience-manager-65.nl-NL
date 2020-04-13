---
title: Opmerkingen bij de release AEM 6.5 Service Pack
description: Opmerkingen bij de release specifiek voor Adobe Experience Manager 6.5 Service Pack 4.
uuid: c7bc3705-3d92-4e22-ad84-dc6002f6fa6c
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5
discoiquuid: 25542769-84d1-459c-b33f-eabd8a535462
docset: aem65
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 9daad219d885c1c6972ace0b247f3537dcdc38a9

---


# Opmerkingen bij de release Adobe Experience Manager 6.5 Service Pack {#aem-service-pack-release-notes}

## Geen informatie {#release-information}

| Producten | **Adobe Experience Manager 6.5** |
|---|---|
| Versie | 6.5.4.0 |
| Type | Service Pack-release |
| Date | 5 maart 2020 |
| URL downloaden | [PackageShare](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/servicepack/AEM-6.5.4.0), [Softwaredistributie (bèta)](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.4.zip) |

## Wat is inbegrepen in de Manager van de Ervaring van Adobe 6.5.4.0 {#what-s-included-in-aem}

Adobe Experience Manager 6.5.4.0 is een belangrijke update met nieuwe functies, belangrijke verbeteringen en prestaties die door de klant zijn aangevraagd, stabiliteit en verbeteringen op het gebied van beveiliging, die zijn uitgebracht sinds de algemene beschikbaarheid van de release van 6.5 in **april 2019**. Het bestand kan boven op Adobe Experience Manager (AEM) 6.5 worden geïnstalleerd.

Enkele belangrijke functies en verbeteringen die zijn geïntroduceerd in AEM 6.5.4.0 zijn:

* AEM Assets wordt nu geconfigureerd met Brand Portal via Adobe I/O Console.

* Er is nu een nieuwe stap Afdrukbare uitvoer [](../forms/using/aem-forms-workflow-step-reference.md) genereren beschikbaar voor AEM Forms-workflows.

* [Ondersteuning](../forms/using/resize-using-layout-mode.md) voor meerdere kolommen in de lay-outmodus voor adaptieve formulieren en interactieve communicatie.

* Ondersteuning voor [RTF](../forms/using/designing-form-template.md) -bestanden in HTML5-formulieren.

* [Verbeterde](new-features-latest-service-pack.md#accessibility-enhancements) toegankelijkheid in de middelen van Experience Manager.

* De ingebouwde opslagplaats (Apache Jackrabbit Oak) wordt bijgewerkt naar versie 1.10.8.

* U kunt selectieve inhoudsubstructuren nu synchroniseren met *Dynamische Media - wijze* Scene7 in plaats van alle beschikbare bij `content/dam`.

* Integratie van formuliergegevensmodellen met SOAP-webservice ondersteunt nu keuzegroepen of kenmerken voor elementen.

* De invoer of de output van de ZEEP en complexe gegevensstructuren steunen nu Dynamische Vervanging van de Groep.

Voor een volledige lijst van eigenschappen, zeer belangrijke hoogtepunten, zeer belangrijke eigenschappen die in vorige AEM 6.5 de dienstpakken worden geïntroduceerd, zie [Nieuw in de Manager van de Ervaring van Adobe 6.5 Service Pack 4](new-features-latest-service-pack.md).

### Sites {#sites-fixes}

* Wanneer een URL van pagina&#39;s van AEM-sites een dubbele punt bevat ( : ) of percentagesymbool (%), de onderliggende browser stopt met reageren en CPU-cycli geven een punt aan (NPR-32369, NPR-31918).

* Wanneer een pagina met AEM-sites wordt geopend voor bewerking en een component wordt gekopieerd, blijft de plakhandeling niet beschikbaar voor sommige plaatsaanduidingen (NPR-32317).

* Wanneer de wizard Publicatie beheren wordt geopend, wordt een ervaringsfragment dat is gekoppeld aan een kerncomponent niet weergegeven in de lijsten met gepubliceerde referenties (NPR-32233).

* Het overzicht van live kopieën in Touch UI duurt veel langer dan de klassieke interface die wordt weergegeven (NPR-32149).

* Wanneer de server-tijd en machine-tijd in verschillende tijdzones zijn, toont de geplande publicatietijd servertijd in Touch UI, terwijl in Klassieke UI, machinetijd wordt getoond (NPR-32077).

* AEM-sites kunnen geen pagina openen met een achtervoegsel in de URL (NPR-32072).

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

* De miniatuur van 3D-elementen is niet informatief wanneer een ondersteund 3D-model wordt opgenomen in AEM (CQ-4283701).

* De onverwerkte status van de voorinstelling van de viewer voor SmartCrop wordt twee keer weergegeven op de bannertekst naast de naam van de voorinstelling (CQ-4283517).

* Onjuiste containerhoogte van een geüpload 3D-model, voorvertoond in 3D-viewer, wordt weergegeven op de detailpagina van het element (CQ-4283309).

* De Carousel Editor wordt niet geopend in IE 11 in de modus Dynamische media hybride van Experience Manager (CQ-4255590).

* De toetsenbordfocus blijft vastzitten in de vervolgkeuzelijst E-mail in het dialoogvenster Downloaden, in Chrome- en Safari-browsers (NPR-32067).

* Het selectievakje Alle inhoud synchroniseren is niet standaard ingeschakeld wanneer wordt geprobeerd om een DM-cloud te configureren op AEM (CQ-4288533).

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

### Integraties {#integrations-6540}

* Het genereren van een URL-bibliotheek met opstarthandleidingen is alleen gebaseerd op `path` en `library_name` waarden van de opstartAPI en is niet gebaseerd op `library_path` waarde (NPR-31550).

* Er wordt een foutbericht weergegeven tijdens het verwerken van aan LiveFyre gerelateerde items (FYR-12420).

* ReportSuitesServlet is kwetsbaar voor SSRF (NPR-32156).

### WCM-sjablooneditor {#wcm-template-editor-6540}

* In de bewerkbare sjabloonstructuurmodus wordt de lijst met toegestane componenten in de lay-outcontainer niet weergegeven met de koppelingsknopcomponent (CQ-4282099).

### WCM Pagina-editor {#wcm-page-editor-6540}

* Er is een fout opgetreden bij het selecteren van een overlay en het selecteren van responsieve rastersleepcomponenten hier (CQ-4283342).

### Campagne gericht {#campaign-targeting-6540}

* De configuratie van de doelcloud mislukt als de fout get-boxes is mislukt (CQ-4279880).

### Brand Portal {#assets-brand-portal}

* Gebruikers van Brand Portal kunnen geen middelen uit de bijdragemap publiceren naar AEM Assets bij de upgrade naar Adobe I/O op AEM 6.5.4 (CQDOC-15655).

   Dit probleem wordt opgelost in het volgende servicepack AEM 6.5.5.

   Voor directe correctie op AEM 6.5.4 wordt aangeraden de hotfix [te](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/hotfix/cq-6.5.0-hotfix-33041) downloaden en op de auteurinstantie te installeren.


* Vervolgkeuzemenu voor het metagegevensschema zijn niet zichtbaar in de elementeigenschappen (CQ-4283287).

* In het subschema Metagegevens worden geen tabbladen weergegeven die zijn gebaseerd op mimetype in eigenschappen van elementen (CQ-4283288).

* Als u het schema voor metagegevens niet publiceert, wordt een foutbericht weergegeven, maar wordt het schema op de achtergrond verwijderd.

* Voorvertoningsafbeelding wordt niet weergegeven voor een gepubliceerd element (CQ-4285886).

* De gebruiker kan activa publiceren of unpublish die enig citaat in de naam bevatten (CQ-4272686).

* De voorwaarden worden niet weergegeven tijdens het downloaden van meerdere middelen (CQ-4281224).

* Kleine beveiligingskwetsbaarheden verholpen.

### Gemeenschappen {#communities}

* Het formulier Lid maken wordt weergegeven als een lege pagina (NPR-31997).

* De gebruiker kan het Analytics-rapport over de auteurinstantie (NPR-30913) niet bekijken.

### eikenindexering en vragen {#oak-indexing-6540}

* MS Word- en MS Excel-documenten met JPEG-afbeeldingen kunnen niet worden geparseerd en er is een fout opgetreden bij het parseren van een klasse die niet is gevonden (NPR-31952).

### Formulieren {#forms-6530}

>[!NOTE]
>
>AEM Service Pack bevat geen oplossingen voor AEM-formulieren. Ze worden geleverd met behulp van een apart Forms add-on pakket. Daarnaast wordt een cumulatief installatieprogramma uitgebracht dat oplossingen voor AEM Forms in JEE bevat. Zie [Invoegtoepassing](#install-aem-forms-add-on-package) van AEM-formulieren installeren en AEM-formulieren [installeren in JEE](#install-aem-forms-jee-installer)voor meer informatie.

* Correspondentenbeheer: Letters geven extra tekens weer na verzending naar workflows voor postprocessen (NPR-32626).

* Correspondentenbeheer: Bij letters wordt een tijdelijke aanduiding voor een vervolgkeuzelijst weergegeven als een tekstonderdeel na verzending naar workflows na verwerking (NPR-32539).

* Correspondentenbeheer: De standaardwaarden die in de lettertypesjabloon worden gedefinieerd, worden niet weergegeven in de voorvertoningsmodus (NPR-32511).

* Mobiele formulieren: De knop Verzenden wordt weergegeven als vergroot tijdens het renderen van een XDP-formulier in een HTML-versie (NPR-32514).

* Documentservices: Problemen met URL-toegang voor Letters en enkele andere pagina&#39;s na toepassing van Service Pack 2 (NPR-32508, NPR-32509).

* Documentservices: Als het aantal transacties op een server een specifieke limiet overschrijdt, mislukt de conversie van HTML naar PDF en worden de instellingen voor het bestandstype verwijderd van de AEM Forms-server (NPR-32204).

* Adaptieve formulieren: Browser het hulpmiddel van de toegankelijkheid meldt mislukkingen in adaptieve vormen overeenkomstig de richtlijnen van niveau AA van WCAG2 (NPR-32312, NPR-32309, CQ-4285439).

* Adaptieve formulieren: Het hulpmiddel van de de browser van Chrome rapporteert een beste praktijkmislukking (NPR-32310).

* Adaptieve formulieren: Problemen met de omzetting tijdens het configureren van een adaptief formulier dat is ingesloten op een pagina met AEM-sites (NPR-32168).

* Workbench: Er wordt een foutbericht weergegeven wanneer de bewerking PDF-eigenschappen ophalen voor de PDF Utilities-service (NPR-32150) wordt gebruikt.

* Documentbeveiliging: Een beveiligd PDF-bestand kan niet offline worden geopend met de optie DisableGlobalOfflineSynchronizationData ingesteld op True (NPR-32078).

* Designer: Als de coderingsoptie is ingeschakeld, verdwijnt de subformulierrand in de gegenereerde PDF-uitvoer (NPR-32547, NPR-31983, NPR-31950).

* Designer: Als een tabel samengevoegde cellen bevat, mislukt de toegankelijkheidstest voor het PDF-uitvoerbestand dat is geconverteerd van een XDP-formulier met de uitvoerservice (CQ-4285372).

* Foundation JEE: Als een AEM Forms-server is losgekoppeld van een cluster, wordt door cacheproblemen voorkomen dat deze opnieuw verbinding maakt met de server (NPR-32412).

## 6.5.4.0 installeren {#install}

**Installatievereisten**

* AEM 6.5.4.0 vereist AEM 6.5. Raadpleeg de [upgradedocumentatie](/help/sites-deploying/upgrade.md) voor gedetailleerde instructies.
* De download van het Service Pack is beschikbaar op het Aandeel van het Pakket van Adobe, dat u direct van AEM 6.5 instantie kunt toegang hebben.
* Voor een plaatsing met MongoDB en veelvoudige instanties, installeer AEM 6.5.4.0 op één van de instanties van de Auteur gebruikend de Manager van het Pakket.
* Voordat u het servicepack installeert, moet u zorgen dat u een momentopname of een nieuwe back-up van uw AEM-instantie hebt.
* Start de instantie opnieuw voor de installatie. Hoewel dat alleen nodig is wanneer de instantie zich nog in de updatemodus bevindt (en dit is het geval wanneer de instantie uit een eerdere versie is bijgewerkt), wordt aangeraden of de instantie langer actief was.

>[!CAUTION]
>
>Adobe raadt u niet aan het pakket AEM 6.5.4.0 te verwijderen of te verwijderen.

### Service Pack installeren via delen pakket {#install-service-pack-via-package-share}

Voer de volgende stappen uit om het Service Pack op een bestaande AEM 6.5 instantie te installeren:

1. Meld u aan bij Delen via pakket vanuit AEM of rechtstreeks vanuit uw browser en download het pakket [](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/servicepack/AEM-6.5.4.0)AEM 6.5.4.0.

1. Installeer het gedownloade pakket met Package Manager.

>[!NOTE]
>
>**Dialoogvenster over de UI van de Manager van het Pakket sluit soms ongeschikt tijdens installatie van 6.5.4.0**
>
>Daarom wordt aangeraden te wachten totdat de foutenlogboeken zich stabiliseren voordat u de instantie opent. De gebruiker moet op specifieke logboeken met betrekking tot het verwijderen van updaterbundel wachten alvorens wordt gewaarborgd dat de installaties succesvol zijn. Het gebeurt meestal in Safari, maar kan af en toe in elke browser gebeuren.

**Automatische installatie**

Er zijn twee manieren om AEM 6.5.4.0 in een lopende instantie automatisch te installeren:

A. Plaats de verpakking in ...*/crx-quickstart/install* folder terwijl de server online beschikbaar is. Het pakket wordt automatisch geïnstalleerd.

B. Gebruik de [HTTP API van de Manager](https://docs.adobe.com/content/docs/en/crx/2-3/how_to/package_manager.html) van het Pakket - zorg ervoor dat u cmd=install&amp;recursive=true gebruikt - zodat worden de genestelde pakketten geïnstalleerd.

>[!NOTE]
>
>AEM 6.5.4.0 ondersteunt geen Bootstrap-installatie.

**Installatie valideren**

1. Op de pagina Productinformatie (/system/console/productinfo) wordt de bijgewerkte versietekenreeks weergegeven `Adobe Experience Manager, Version 6.5.4.0` onder Geïnstalleerde producten.

1. Alle OSGi-bundels zijn **[!UICONTROL ACTIEF]** of **[!UICONTROL FRAGMENT]** in de Console OSGi (de Console van het Gebruik: /systeem/console/bundels).
1. De OSGI-bundel org.apache.jackrabbit.oak-core bevindt zich op versie 1.10.6 of hoger (gebruik webconsole: /systeem/console/bundels).

Raadpleeg de [technische vereisten](/help/sites-deploying/technical-requirements.md)om te zien welke platforms zijn gecertificeerd voor uitvoering met deze release.

### AEM Forms add-on-pakket installeren {#install-aem-forms-add-on-package}

>[!NOTE]
>
>Sla dit over als u geen AEM-formulieren gebruikt. Correcties in AEM Forms worden geleverd via een afzonderlijk invoegpakket.

>[!NOTE]
>
>AEM 6.5.4.0 bevat een nieuwe versie van het compatibiliteitspakket voor [AEM-formulieren](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/compatpack/AEM-FORMS-6.5.3.0-COMPAT). Als u een oudere versie van het compatibiliteitspakket voor AEM-formulieren gebruikt en bijwerkt naar AEM 6.5.4.0, installeert u de nieuwste versie van het compatibiliteitspakket voor AEM-formulieren na de installatie van het insteekpakket Forms.

1. Controleer of u het AEM Service Pack hebt geïnstalleerd.
1. Download het overeenkomstige Forms add-on-pakket dat in de [AEM Forms-releases](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) voor uw besturingssysteem wordt vermeld.
1. Installeer het add-on pakket Formulieren zoals beschreven in de [invoegpakketten](../forms/using/installing-configuring-aem-forms-osgi.md#install-aem-forms-add-on-package)voor AEM Forms.

### AEM-formulieren installeren op JEE {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Sla dit over als u AEM Forms niet gebruikt op JEE. Correcties in AEM Forms on JEE worden geleverd via een afzonderlijk installatieprogramma.

Voor informatie over het installeren van het cumulatieve installatieprogramma voor AEM Forms op JEE en configuratie na implementatie, zie de [versienota&#39;s voor flard 0011](https://helpx.adobe.com/aem-forms/quick-fixes/6-5/jee-patch-0011.html).

#### Workbench-installatieprogramma

Aangezien het een volledig installatieprogramma is, is de bestandsgrootte groter dan bij de patchversie. Verwijder de vorige Workbench-versie voordat u de nieuwe installeert.

### UberJar {#uber-jar}

De UberJar voor AEM 6.5.4.0 is beschikbaar in de [openbare gegevensopslagplaats](https://repo.adobe.com/nexus/content/groups/public/com/adobe/aem/uber-jar/6.5.4/)van Adobe.

Om UberJar in een Geweven project te gebruiken, verwijs naar het artikel, [hoe te UberJar](/help/sites-developing/ht-projects-maven.md) gebruiken en de volgende gebiedsdeel in uw projectPOM omvatten:

```shell
<dependency>
      <groupId>com.adobe.aem</groupId>
      <artifactId>uber-jar</artifactId>
      <version>6.5.4</version>
      <classifier>apis</classifier>
      <scope>provided</scope>
</dependency>
```

De bijgewerkte UberJar-versie voor 6.5.4.0 die het pakket **com.fasterxml.jackson.core.async** bevat, is beschikbaar in de [Adobe Public Maven-opslagruimte](https://repo.adobe.com/nexus/content/groups/public/com/adobe/aem/uber-jar/6.5.4-1.0/).

Als u de bijgewerkte versie van UberJar gebruikt, omvat het volgende gebiedsdeel in uw project POM:

```shell
<dependency>
      <groupId>com.adobe.aem</groupId>
      <artifactId>uber-jar</artifactId>
      <version> 6.5.4-1.0</version>
      <classifier>apis</classifier>
      <scope>provided</scope>
</dependency>
```

## Verouderde functies {#removed-deprecated-features}

Deze sectie bevat een lijst met functies en mogelijkheden die zijn gemarkeerd als verouderd in AEM 6.5.4.0. Functies die volgens plan in een toekomstige versie zullen worden verwijderd, worden eerst op afgekeurd ingesteld, met een andere optie die moet worden gebruikt.

Klanten wordt aangeraden na te gaan of zij in hun huidige implementatie gebruik maken van de functie of het vermogen en plannen maken om hun implementatie te wijzigen en de alternatieve optie te gebruiken.

| Gebied | Functie | Vervanging |
|---|---|---|
| Integraties | Het scherm **[!UICONTROL AEM Cloud Services Opt-In]** is verouderd. Met de integratie van AEM en Doel bijgewerkt in AEM 6.5 ter ondersteuning van de standaard-API van het Doel, die verificatie via Adobe IMS en I/O gebruikt, en de groeiende rol van Adobe Launch voor het van instrumenten voorzien van AEM-pagina&#39;s voor analyses en personalisatie, is de Opt-In-wizard functioneel irrelevant geworden. | Systeemverbindingen, Adobe IMS-verificatie en Adobe I/O-integratie configureren via de respectievelijke AEM-cloudservices |

## Known issues {#known-issues}

* Als de **Verbonden tovenaar van de middelenconfiguratie** een 404 foutenmelding na installatie terugkeert, installeer manueel de **cq-remotedam-cliënt-ui-content** en **cq-remotedam-cliënt-ui-componenten** pakketten gebruikend de Manager van het Pakket opnieuw.
* De volgende fouten en waarschuwingsberichten kunnen tijdens de installatie van AEM 6.5.x.x worden weergegeven:
   * &quot;Wanneer de integratie van het Doel in AEM gebruikend de StandaardAPI van het Doel (authentificatie IMS) wordt gevormd, dan leidt het uitvoeren van de Fragmenten van de Ervaring naar Doel in verkeerde aanbiedingstypes die worden gecreeerd. In plaats van het type &quot;Experience Fragment&quot;/bron &quot;Adobe Experience Manager&quot;, creëert Target verschillende aanbiedingen met het type &quot;HTML&quot;/source &quot;Adobe Target Classic&quot;.
   * com.adobe.granite.Maintenance.impl.TaskScheduler: Geen onderhoudsvensters gevonden bij graniet/bediening/onderhoud.
   * De adaptieve servervalidatie van het formulier mislukt wanneer statistische functies zoals SUM, MAX en MIN worden gebruikt. CQ-4274424
   * com.adobe.granite.Maintenance.impl.TaskScheduler - Geen onderhoudsvensters gevonden bij graniet/bewerkingen/onderhoud.
   * Hotspot in een interactieve afbeelding van dynamische media is niet zichtbaar tijdens een voorvertoning van het element via de Shopable Banner-viewer.

## OSGi-bundels en inhoudspakketten inbegrepen {#osgi-bundles-and-content-packages-included}

De volgende tekstdocumenten maken een lijst van de bundels OSGi en de Pakketten van de Inhoud inbegrepen in AEM 6.5.4.0

Lijst van OSGi-bundels opgenomen in AEM 6.5.4.0

[Bestand ophalen](assets/6540_bundles.txt)

Lijst met inhoudspakketten die zijn opgenomen in AEM 6.5.4.0

[Bestand ophalen](assets/6540_packages.txt)

## Beperkte locaties {#restricted-sites}

Deze sites zijn alleen beschikbaar voor klanten. Neem contact op met uw accountmanager van Adobe als u een klant bent en toegang nodig hebt.

* [Productdownload op licensing.adobe.com](https://licensing.adobe.com/)
* [Neem contact op met de klantenondersteuning](https://daycare.day.com/public/contact.html)Voor meer informatie over de toegang tot het ondersteuningsportaal raadpleegt u [Toegang tot het ondersteuningsportal](https://helpx.adobe.com/experience-manager/kb/accessing-aem-support-portal.html).

>[!MORE ZOALS DIT]
>
>* [Opmerkingen bij de release AEM 6.5](/help/release-notes/release-notes.md)
>* [AEM-productpagina](https://www.adobe.com/solutions/web-experience-management.html)
>* [AEM 6.5-documentatie](https://helpx.adobe.com/nl/support/experience-manager/6-5.html)
>* Abonneren op [Adobe-productupdates met prioriteit](https://www.adobe.com/subscription/priority-product-update.html)

