---
title: AEM 6.5 de Nota's van de Versie van het Service Pack
description: De nota's van de versie specifiek voor Manager 6.5 Service Pack 4 van de Ervaring van Adobe.
uuid: c7bc3705-3d92-4e22-ad84-dc6002f6fa6c
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5
discoiquuid: 25542769-84d1-459c-b33f-eabd8a535462
docset: aem65
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 14df85f7a815fe567ea87375727ebe1e54733464

---


# De Manager van de Ervaring van Adobe 6.5 de Nota&#39;s van de Versie van het Service Pack {#aem-service-pack-release-notes}

## Gegevens vrijgeven {#release-information}

| Producten | **Adobe Experience Manager 6.5** |
|---|---|
| Versie | 6.5.4.0 |
| Type | Service Pack Release |
| Date | 05 maart 2020 |
| URL downloaden | [PackageShare](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/servicepack/AEM-6.5.4.0), [softwaredistributie (Bèta)](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.4.zip) |

## Wat inbegrepen in de Manager van de Ervaring van Adobe 6.5.4.0 is {#what-s-included-in-aem}

De Manager 6.5.4.0 van de Ervaring van Adobe is een belangrijke update die nieuwe eigenschappen omvat, de zeer belangrijke klant vroeg verhogingen en prestaties, stabiliteit, veiligheidsverbeteringen, vrijgegeven sinds de algemene beschikbaarheid van 6.5 versie in **april 2019**. Het kan bovenop de Manager van de Ervaring van Adobe (AEM) 6.5 worden geïnstalleerd.

Sommige zeer belangrijke eigenschappen en verhogingen die in AEM 6.5.4.0 worden geïntroduceerd omvatten:

* AEM de Activa wordt nu gevormd met het Portaal van het Merk door de Console van Adobe I/O.

* Een nieuwe [produceer geschikt om gedrukt te worden stap van de Output](../forms/using/aem-forms-workflow-step-reference.md) is nu beschikbaar voor werkschema&#39;s AEM.

* [Ondersteuning](../forms/using/resize-using-layout-mode.md) voor meerdere kolommen voor de lay-outmodus voor adaptieve formulieren en interactieve communicatie.

* Steun voor [Rijke Tekst](../forms/using/designing-form-template.md) in vormen HTML5.

* Verbeteringen van de toegankelijkheid in Activa.

* De ingebouwde opslagplaats (Apache Jackrabbit Oak) wordt bijgewerkt naar versie 1.10.8.

Voor volledige lijst van eigenschappen, zeer belangrijke hoogtepunten, zeer belangrijke eigenschappen die in vorige AEM 6.5 de dienstpakken worden geïntroduceerd, zie [wat in de Manager van de Ervaring van Adobe 6.5 Service Pack 4](new-features-latest-service-pack.md)nieuw is.

### Assets {#assets-6540-enhancements}

* De knoop om werkschema op de pagina van de activainzameling teweeg te brengen is gehandicapt (NPR-32471).

* Een omslag zonder naam wordt gecreeerd in SPS (het Publiceren Scene7 Systeem) terwijl het bewegen van activa van één omslag aan een andere in de Manager van de Ervaring met de Dynamische configuratie van Media Scene7 (NPR-32440).

* De actie om alle activa (het gebruiken van Uitgezocht allen en dan beweging) naar een omslag te verplaatsen die gepubliceerde activa bevat ontbreekt met fout (NPR-32366).

* De generatie van de renditie voor activa met $ {uitbreiding} ontbreekt (NPR-32294).

* De geschiedenis URLs van de versie wordt getoond onder Verwezen door gebied op de pagina van het activaBezit (NPR-31889).

* Het dossier van het PIT dat van DAM wordt gedownload kan niet worden geopend gebruikend WinZip (NPR-32293).

* De originele toestemmingen van een omslag worden bijgewerkt wanneer de Montages van de Omslag worden geopend om omslagtitel of duimnagelbeeld te veranderen en dan opgeslagen (NPR-32292).

* Het agendapictogram voor activering die gepland is, wordt niet weergegeven in de kolom Status (in de Klassieke UI van de DAM-lijst van activa) voor activa waarvan de activering gepland is voor een latere datum en tijd (NPR-32291).

* De verwezenlijking van het fragment die fragmentmalplaatjes gebruikt geeft fout bij het zoeken naar inzamelingen tijdens het proces van de fragmentverwezenlijking (NPR-32290).

* De veelvoudige onderzoeksvragen worden in brand gestoken wanneer de veelvoudige markeringen van onderzoeksfilter (NPR-32143) worden geselecteerd.

* De Activa UI van de Manager van de ervaring toont beknot filenames wanneer de activa met meer dan 50 karakters in filename worden geupload (NPR-32054).

* Alle controledozen in het paneel van de Filter worden ontruimd wanneer de eerste en tweede controledozen worden ontruimd, wanneer niveau twee controledozen van de controledoosboom in de Voorraad van Adobe werden geselecteerd (NPR-31919).

* Bestanden- en mapzoeken met behulp van Omniszoekfacetten bieden uitzondering (NPR-31872).

* Het gebied dat voor verplichte gebiedsselectie in meta-gegevensredacteur benadrukt wordt niet verwijderd zelfs na het selecteren van het vereiste gebied, wanneer de gebiedsdeelregels in de overeenkomstige vorm van het meta-gegevensschema (NPR-31834) worden geplaatst.

* De volledige namen van de markeringen van het bladniveau (van markeringshiërarchie) tonen niet in de pagina van activaEigenschappen (NPR-31820).

* Het gebruik van achterbevel van de pagina van activaEigenschappen op browser Safari geeft fout (NPR-31753).

* De het onderzoek van de aanraking UI (die door Omnissearch wordt gedaan) resultatenpagina scrolt automatisch omhoog en verliest de rolpositie van de gebruiker (NPR-31307).

* De het detailpagina van activa van activa PDF activa toont actieknopen behalve aan Inzameling en voegt de knopen van de Renditie in de Manager toe die van de Ervaring op de Dynamische wijze van de looppas van Media Scene7 (CQ-4286705) loopt.

* Activa van meer dan 2 GB kunnen nu worden geüpload in Dynamic Media-Scene7 (CQ-4286561).

* De activa vergen te lang om door het partij te verwerken uploadt proces van Scene7 (CQ-4286445).

* Sparen de knoop voert geen Verre Reeks in wanneer de gebruiker geen veranderingen in Vastgestelde Redacteur in de Dynamische Cliënt van Media (CQ-4285690) heeft aangebracht.

* De 3D activaduimnagel is niet informatief, wanneer een gesteund 3D model in AEM (CQ-4283701) wordt opgenomen.

* De onverwerkte status van vooraf ingestelde slimme gewas videokijker verschijnt tweemaal op de bannertekst naast de vooraf ingestelde naam (CQ-4283517).

* De onjuiste containerhoogte van een geupload 3D model previewde in 3D kijker wordt waargenomen op de de detailspagina van activa (CQ-4283309).

* De Redacteur van het Carrousel opent niet in IE 11 op de Dynamische Hybride wijze van de Media van de Manager van de Ervaring (CQ-4255590).

* De nadruk van het toetsenbord wordt geplakt in E-mail drop-down in de dialoog van de Download, in browsers Chrome en Safari (NPR-32067).

* Synchroniseer alle inhoud checkbox wordt niet toegelaten door gebrek terwijl het proberen om DM wolk config op AEM (CQ-4288533) toe te voegen.

### Sites {#sites-fixes}

* Wanneer een URL van een pagina van de Plaatsen AEM een dubbelpunt bevat (: ) of percentagesymbool (%), de onderliggende browser houdt op antwoordend en de cycli van cpu tonen een punt (NPR-32369, NPR-31918).

* Wanneer een pagina van Plaatsen AEM voor het uitgeven wordt geopend en een component wordt gekopieerd, blijft de deegactie niet beschikbaar voor sommige placeholders (NPR-32317).

* Wanneer de Manage tovenaar van de Publicatie wordt geopend, wordt een Fragment van de Ervaring verbonden aan een Component van de Kern niet getoond in de lijsten van gepubliceerde verwijzingen (NPR-32233).

* Het levende exemplaaroverzicht in Aanraking UI duurt veel langer dan Klassieke UI om terug te geven (NPR-32149).

* Wanneer de server-tijd en de machine-tijd in verschillende tijdzones zijn, publiceert de geplande tijd de servertijd van vertoningen in Aanraking UI, terwijl in Klassieke UI, de machinetijd wordt getoond (NPR-32077).

* De Plaatsen van AEM openen geen pagina met een achtervoegsel in URL (NPR-32072).

* Wanneer een gebruiker een Fragment van de Inhoud uitgeeft, wordt een geschrapte variatie van het Fragment van de Inhoud hersteld (NPR-32062).

* De gebruikers worden toegestaan om een Fragment van de Inhoud te bewaren zonder om het even welke informatie op de vereiste gebieden (NPR-31988) te verstrekken.

* kernel.js en ui.js worden niet vooraf in acht genomen of in het voorgeheugen ondergebracht. Het leidt tot extra tijd in het teruggeven van pagina&#39;s (NPR-31891).

* Wanneer PageEventAuditListener wordt toegelaten, begaat de lengte van rij verhogingen. Het beïnvloedt de prestaties van vele verrichtingen zoals bulkpublicatie, navigatie, de beweging van bulkactiva (NPR-31890).

* Wanneer de Fragmenten van de Ervaring worden gesleept, wordt de hoge reactietijd waargenomen (NPR-31878).

* Wanneer u de component van de Belemmering hier optie in placeholder van een ontvankelijk net selecteert, wordt een GET verzoek verzonden en de verzoekresultaten in fout HTTP 403 (NPR-31845).

* Wanneer het bewegen van de inhoud binnen de zelfde omslag, is de optie van de paginabeweging gehandicapt (NPR-31840).

* Op de editable wijze van de malplaatjesstructuur, de toegestane componentenlijst in de vertoningen van de lay-outcontainer onjuiste resultaten. In de lay-outcontainer (NPR-31816) worden alleen onderdelen met een ontwerpdialoog weergegeven.

* Wanneer een pagina read-only toestemmingen voor een gebruiker heeft, is de Open eigenschappen optie zichtbaar in sites.html maar niet in editor.html (NPR-31770).

* Wanneer een gebruiker de Create knoop klikt, is de paginaoptie niet beschikbaar (NPR-31756).

* Onbekwaam om campagne in de campagne van Adobe te synchroniseren die OOTB (uit de doos) bevat de component van de ontwerpimporteur (NPR-31728) bevat.

* Wanneer u probeert een opsommingsteken te wijzigen in genummerde lijst, worden alleen de eerste twee items van de lijst gewijzigd (NPR-31636).

* Wanneer een pagina niet-authored is en de kindknoop wordt geselecteerd, toont de selectiedialoog nog de aanvankelijke knoop. Wanneer de pagina authored is en de gebruiker doorbladert, richt de pagina aan de wortelknoop in plaats van de authored knoop (NPR-31618) opnieuw.

* De de dialoogdoos van de meningsconfiguratie werkt niet behoorlijk voor de eigenschap van het Inbox aanpassingswerkschema (NPR-32503 en NPR-32492).

* Een foutenmelding toont terwijl het bekijken van werkschemainformatie gebruikend Inbox (CQ-4282168).

### Foundation-UI {#foundation-ui-6540}

* De controleverschuivingen van de muis naar vorig filtergebied in plaats van het blijven in het bestaande filtergebied terwijl het zoeken van activa gebruikend het paneel van de Filter (NPR-32538).

* [Of Platform Tagging] Search for tags door in de tagvelden te typen geeft tags buiten de hoofdgrenzen weer en respecteert niet de `rootPath` eigenschap van tagvelden (NPR-31895).

* [De browser van de Weg van het platform UI] breekt als de ongeldige weg op tekstgebied (NPR-31884) wordt toegevoegd.

* Berichten worden verborgen achter een kleverig menu op pagina-selectie (NPR-31628).

### Platform {#platform-sling-6540}

* (HTL) Onderstrepen vervangen kolommen in de wegsectie van URL (NPR-32231).

### Projecten {#projects-6540}

* Creeer knoop is niet zichtbaar aan de gebruiker zelfs als de gebruiker toestemming heeft om project in subfolder (NPR-31832) tot stand te brengen.

### Projectvertaling {#projects-translation-6540}

* De verwezenlijking van het vertaalproject breekt UI wanneer de optie van de Ruimten van de Versiering in `Apache Sling JSP Script Handler` (NPR-32154) wordt geactiveerd.

* Fout in UI en de Onvolledige puntuitzondering in foutenlogboeken wordt waargenomen wanneer om het even welke te vertalen markering, aan een vertaalproject (NPR-31896) wordt toegevoegd.

### Integratie {#integrations-6540}

* De bibliotheek URL van de lancering is generatie gebaseerd slechts op `path` en `library_name` waarden van de Lancering API, en is niet gebaseerd op `library_path` waarde (NPR-31550).

* Een foutenmelding toont terwijl het verwerken van met LiveFyre verwante punten (FYR-12420).

### WCM-sjablooneditor {#wcm-template-editor-6540}

* Op de editable wijze van de malplaatjesstructuur, toont de toegestane componentenlijst in lay-outcontainer de geen component van de verbindingsknoop (CQ-4282099).

### WCM-paginaeditor {#wcm-page-editor-6540}

* Fout wordt waargenomen bij het selecteren van een bekleding en dan het selecteren van de ontvankelijke componenten van de netBelemmering hier (CQ-4283342).

### Campagne gericht op {#campaign-targeting-6540}

* De wolkenconfiguratie van het doel ontbreekt met de fout krijgt ontbroken brievenbusverzoek (CQ-4279880).

### Merk Portal {#assets-brand-portal}

* De het schemadrop-down waarden van meta-gegevens zijn niet zichtbaar in activaeigenschappen (CQ-4283287).

* Het subschema van meta-gegevens toont geen lusjes die op mimetype in activaeigenschappen worden gebaseerd (CQ-4283288).

* Unpublished bevolkt het meta-gegevensschema een foutenmelding hoewel het schema aan achterkant wordt verwijderd.

* Het beeld van de voorproef toont niet voor gepubliceerde activa (CQ-4285886).

* De gebruiker kan activa publiceren of niet publiceren die enig citaat in de naam (CQ-4272686) bevatten.

* De voorwaarden worden niet weergegeven tijdens het downloaden van meerdere bedrijfsmiddelen (CQ-4281224).

* Kleine beveiligingskwetsbaarheden worden aangepakt.

### Gemeenschappen {#communities}

* Het formulier Lid maken wordt weergegeven als een lege pagina (NPR-31997).

* De gebruiker kan het Analytische rapport over auteursinstantie (NPR-30913) niet bekijken.

### eiken- indexering en vragen {#oak-indexing-6540}

* MS Word en MS Excel documenten, die beeld JPEG bevatten, wanneer ontleed met Tika ontleden er niet in slagen om te ontleden en de klasse niet gevonden fout wordt waargenomen (NPR-31952).

### Formulieren {#forms-6530}

>[!NOTE]
>
>AEM Service Pack omvat geen moeilijke situaties voor Vormen AEM. Zij worden geleverd gebruikend een afzonderlijk toe:voegen-op pakket van Vormen. Bovendien wordt een cumulatieve installateur vrijgegeven die moeilijke situaties voor Vormen AEM op JEE omvat. Voor meer informatie, zie de Vormen [installeren AEM toe:voegen-op](#install-aem-forms-add-on-package) en de Vormen van [installeren AEM op JEE](#install-aem-forms-jee-installer).

* Correspondentiebeheer: De letters tonen extra karakters na voorlegging aan post proceswerkschema&#39;s (NPR-32626).

* Correspondentiebeheer: De brieven tonen drop-down placeholder als tekstcomponent na voorlegging aan post-proceswerkschema&#39;s (NPR-32539).

* Correspondentiebeheer: De standaardwaarden die in het brievenmalplaatje worden bepaald tonen niet op de wijze van de Voorproef (NPR-32511).

* Mobiele formulieren: Verzenden knoopvertoningen zoals uitgebreid in grootte terwijl het teruggeven van een vorm XDP in een versie van HTML (NPR-32514).

* Documentservices: URL de toegangskwesties voor Brieven en sommige andere pagina&#39;s na het toepassen van Service Pack 2 (NPR-32508, NPR-32509).

* Documentservices: Als het aantal transacties op een server een specifieke grens overschrijdt, ontbreekt de omzetting van HTML aan PDF en de dossiertype montages worden verwijderd uit server van Vormen AEM (NPR-32204).

* Aanpassingsformulieren: Browser toegankelijkheidshulpmiddel meldt mislukkingen in adaptieve vormen volgens de richtlijnen van niveau AA van WCAG2 (NPR-32312, NPR-32309, CQ-4285439).

* Aanpassingsformulieren: Het browser van het scherm toegankelijkheidshulpmiddel meldt een beste praktijkmislukking (NPR-32310).

* Aanpassingsformulieren: Vertaalproblemen tijdens het configureren van een adaptieve vorm die is ingebouwd op een pagina met AEM-sites (NPR-32168).

* Werkbank: Een foutenmelding toont terwijl het gebruiken van Get PDF de verrichting van Eigenschappen voor de dienst van Nut PDF (NPR-32150).

* Documentbeveiliging: Een beschermd Pdf- dossier slaagt er niet in om off-line met de optie te openen DisableGlobalOfflineSynchronizationData die aan Waar (NPR-32078) wordt geplaatst.

* Ontwerper: Als de het etiketteren optie wordt toegelaten, verdwijnt subform grens in de geproduceerde output PDF (NPR-32547).

* Ontwerper: Als de het etiketteren optie wordt toegelaten, verdwijnt de subform grens in de geproduceerde output PDF (NPR-31983, NPR-31950).

* Ontwerper: Als er samengevoegde cellen in een lijst zijn, ontbreekt de toegankelijkheidstest voor het outputPdf- dossier dat van een vorm wordt omgezet XDP gebruikend de outputdienst (CQ-4285372).

## Installeer 6.5.4.0 {#install}

**Installatievereisten**

* AEM 6.5.4.0 vereist AEM 6.5. De [verbeteringsdocumentatie](/help/sites-deploying/upgrade.md) van de controle voor gedetailleerde instructies.
* De download van het Pak van de Dienst is beschikbaar op het Aandeel van het Pakket van Adobe, dat u tot van AEM 6.5 instantie kunt direct toegang hebben.
* Voor een plaatsing met MongoDB en veelvoudige instanties, installeer AEM 6.5.4.0 op één van de instanties van de Auteur gebruikend de Manager van het Pakket.
* Alvorens het de dienstpak te installeren, zorg ervoor om een momentopname of een verse steun van uw AEM instantie te hebben.
* Start de installatie opnieuw vóór de installatie. Terwijl dat slechts nodig is wanneer de instantie nog op updatewijze (en dit is het geval wanneer de instantie van een vroegere versie) werd bijgewerkt is, wordt het geadviseerd als de instantie voor langere periode liep.

>[!CAUTION]
>
>Adobe adviseert niet verwijderend of desinstalleert het pakket AEM 6.5.4.0.

### Installeer het Service Pack via Package Share {#install-service-pack-via-package-share}

Voer de volgende stappen uit om het Service Pack op een bestaande AEM 6.5 instantie te installeren:

1. Login aan het Aandeel van het Pakket van binnen AEM of direct van uw browser en download [AEM 6.5.4.0 pakket](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/servicepack/AEM-6.5.4.0).

1. Installeer het gedownloade pakket met Package Manager.

>[!NOTE]
>
>**De dialoog op de Manager UI van het Pakket komt soms onvroeg tijdens installatie van 6.5.4.0 weg**
>
>Daarom wordt het geadviseerd om op foutenlogboeken te wachten om te stabiliseren alvorens tot de instantie toegang te hebben. De gebruiker moet op specifieke logboeken met betrekking tot de desinstallatie van updaterbundel wachten alvorens wordt verzekerd dat de installaties succesvol zijn. Het gebeurt over het algemeen op Safari maar kan met tussenpozen op om het even welke browser gebeuren.

**Automatische installatie**

Er zijn twee manieren om AEM 6.5.4.0 in een lopende instantie automatisch te installeren:

A. Plaats de verpakking in ...*/crx-quickstart/install* omslag terwijl de server online beschikbaar is. Het pakket wordt automatisch geïnstalleerd.

B. Gebruik [HTTP API van de Manager](https://docs.adobe.com/content/docs/en/crx/2-3/how_to/package_manager.html) van het Pakket - zorg ervoor dat u cmd=install&amp;recursive=true gebruikt - zodat zijn de genestelde pakketten geïnstalleerd.

>[!NOTE]
>
>AEM 6.5.4.0 steunt geen installatie Van Bootstrap.

**Installatie valideren**

1. De pagina van de Informatie van het Product (/systeem/console/productinfo) toont de bijgewerkte versie - koord `Adobe Experience Manager, Version 6.5.4.0` onder Geïnstalleerde Producten.

1. Alle bundels OSGi zijn of **[!UICONTROL ACTIEF]** of **[!UICONTROL FRAGMENT]** in de Console OSGi (de Console van het Web van het Gebruik: /systeem/console/bundels).
1. De OSGI-bundel org.apache.jackrabbit.oak-core is op versie 1.10.6 of hoger (Web Console gebruiken: /systeem/console/bundels).

Om te zien welke platforms om met deze versie worden verklaard te lopen, gelieve te verwijzen naar de [Technische Vereisten](/help/sites-deploying/technical-requirements.md).

### AEM-formulieren insteekpakket installeren {#install-aem-forms-add-on-package}

>[!NOTE]
>
>Sla over als u geen AEM-formulieren gebruikt. De montages in Vormen AEM worden geleverd door een afzonderlijk toe:voegen-op pakket.

>[!NOTE]
>
>AEM 6.5.4.0 omvat een nieuwe versie van het pakket [van de Verenigbaarheid van de Vormen van](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/compatpack/AEM-FORMS-6.5.3.0-COMPAT)AEM. Als u een oudere versie van het pakket van de Verenigbaarheid van Vormen AEM en het bijwerken aan AEM 6.5.4.0 gebruikt, installeer de recentste versie van het pakket van de Verenigbaarheid van Vormen AEM na installatie van het Pakket van Vormen toe:voegen-op Pakket van Vormen.

1. Zorg ervoor dat u het AEM Service Pack hebt geïnstalleerd.
1. Download het overeenkomstige pakket van Vormen toe:voegen-op dat bij de versies van de Vormen van [AEM voor uw werkend systeem wordt vermeld](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) .
1. Installeer het toe:voegen-op pakket van Vormen zoals die in het Installeren van toe:voegen-op pakketten [](../forms/using/installing-configuring-aem-forms-osgi.md#install-aem-forms-add-on-package)van Vormen AEM wordt beschreven.

### AEM-formulieren installeren op JEE {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Sla over als u geen AEM-formulieren gebruikt op JEE. De montages in Vormen AEM op JEE worden geleverd door een afzonderlijke installateur.

Voor informatie over het installeren van de cumulatieve installateur voor Vormen AEM op JEE en post-plaatsingsconfiguratie, zie de [versienota&#39;s voor flard 0011](https://helpx.adobe.com/aem-forms/quick-fixes/6-5/jee-patch-0011.html).

#### Installateur werkbank

Aangezien het een volledige installateur is, is de dossiergrootte meer in vergelijking met de flardversie. Verwijder de vorige versie van de Werkbank voordat u de nieuwe installeert.

### UberJar {#uber-jar}

UberJar voor AEM 6.5.4.0 is beschikbaar in de [Openbare Geweven bewaarplaats](https://repo.adobe.com/nexus/content/groups/public/com/adobe/aem/uber-jar/6.5.4/)van Adobe.

Om UberJar in een Maven project te gebruiken, verwijs naar het artikel, [hoe te om UberJar](/help/sites-developing/ht-projects-maven.md) te gebruiken en het volgende gebiedsdeel in uw projectPOM te omvatten:

```shell
<dependency>
      <groupId>com.adobe.aem</groupId>
      <artifactId>uber-jar</artifactId>
      <version>6.5.4.0</version>
      <classifier>apis</classifier>
      <scope>provided</scope>
</dependency>
```

## Afgekeurde functies {#removed-deprecated-features}

Deze sectie maakt een lijst van eigenschappen en mogelijkheden die zoals afgekeurd met AEM 6.5.4.0 zijn gemerkt. De eigenschappen die gepland zijn om in een toekomstige versie worden verwijderd worden geplaatst aan afgekeurde eerst, met een afwisselende optie aan gebruik.

De klanten worden geadviseerd om te herzien als zij van de eigenschap of het vermogen in hun huidige plaatsing gebruik maken, en plannen te maken om hun implementatie te veranderen om de afwisselende optie te gebruiken.

| Gebied | Functie | Vervanging |
|---|---|---|
| Integratie | Het **[!UICONTROL Opt-in]** scherm van de Diensten van de Wolk AEM is afgekeurd. Met AEM en de integratie van het Doel die in AEM 6.5 wordt bijgewerkt om het StandaardAPI van het Doel te steunen, die authentificatie via Adobe IMS en I/O, en de groeiende rol van de Lancering van Adobe voor het van instrumenten voorzien van AEM- pagina&#39;s voor analytica en verpersoonlijking gebruikt, is de Opt-in tovenaar functioneel irrelevant geworden. | Vorm systeemverbindingen, de authentificatie van Adobe IMS, en de integratie van Adobe I/O via de respectieve AEM wolkendiensten |

## Bekende problemen {#known-issues}

* Als de tovenaar van de **Connected activaconfiguratie** een 404 foutenmelding na installatie terugkeert, installeer manueel de **cq-ver*plaatsen-cliënt-ui-inhoud** en **cq-ver*plaatsen-cliënt-ui-componenten** pakketten gebruikend de Manager van het Pakket opnieuw.
* De volgende fouten en waarschuwingsberichten kunnen worden weergegeven tijdens de installatie van AEM 6.5.x.x:
   * &quot;Wanneer de integratie van het Doel in AEM gebruikend de StandaardAPI van het Doel (authentificatie IMS) wordt gevormd, dan resulteert het uitvoeren van de Fragmenten van de Ervaring naar Doel in verkeerde aanbiedingstypes die worden gecreeerd. In plaats van type &quot;het Fragment van de Ervaring&quot;/bron &quot;de Manager van de Ervaring van Adobe,&quot;leidt het Doel tot verscheidene aanbiedingen met type &quot;HTML&quot;/bron &quot;het Doel van Adobe Klassiek.&quot;
   * com.adobe.granite.maintenance.impl.TaskScheduler: Geen onderhoudsvensters gevonden bij graniet/exploitatie/onderhoud.
   * De adaptieve server-zijbevestiging van de Vorm ontbreekt wanneer de gezamenlijke functies zoals SUM, MAX, en MIN worden gebruikt. CK-4274424
   * com.adobe.granite.maintenance.impl.TaskScheduler - Geen onderhoudsvensters gevonden bij graniet/exploitatie/onderhoud.
   * Hotspot in een Dynamisch Interactief beeld van Media is niet zichtbaar terwijl het previewing van de activa door de Shopable kijker van de Banner.

## OSGi-bundels en inhoudspakketten {#osgi-bundles-and-content-packages-included}

De volgende tekstdocumenten maken een lijst van de bundels OSGi en de Pakketten van de Inhoud inbegrepen in AEM 6.5.4.0

Lijst van OSGi-bundels opgenomen in AEM 6.5.4.0

[Bestand ophalen](assets/6540_bundles.txt)

Lijst van de Inhoud Pakketten inbegrepen in AEM 6.5.4.0

[Bestand ophalen](assets/6540_packages.txt)

## Beperkte locaties {#restricted-sites}

Deze plaatsen zijn slechts beschikbaar aan klanten. Als u een klant bent en toegang nodig hebt, contacteer uw de rekeningsmanager van Adobe.

* [Download van product op license.adobe.com](https://licensing.adobe.com/)
* [Neem contact op met Customer Support](https://daycare.day.com/public/contact.html)voor meer informatie over het openen van het supportportaal, zie [Toegang krijgen tot het supportportaal](https://helpx.adobe.com/experience-manager/kb/accessing-aem-support-portal.html).

>[!MORE ZOALS DIT]
>
>* [AEM 6.5 releaseaantekeningen](/help/release-notes/release-notes.md)
>* [AEM-productpagina](https://www.adobe.com/solutions/web-experience-management.html)
>* [AEM 6.5-documentatie](https://helpx.adobe.com/support/experience-manager/6-5.html)
>* Abonneer u op [Adobe prioritaire productupdates](https://www.adobe.com/subscription/priority-product-update.html)

