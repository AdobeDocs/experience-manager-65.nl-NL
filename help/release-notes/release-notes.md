---
title: Algemene opmerkingen bij de release voor [!DNL Adobe Experience Manager] 6.5
description: '[!DNL Adobe Experience Manager] 6.5 nota''s schetterend de versieinformatie, wat nieuw is, hoe te, en gedetailleerde veranderingslijsten te installeren.'
translation-type: tm+mt
source-git-commit: 8d60e064ab50f24016c049c8d5d0fceb784c99a3
workflow-type: tm+mt
source-wordcount: '2154'
ht-degree: 1%

---


# Algemene opmerkingen bij de release van [!DNL Adobe Experience Manager] 6.5{#general-release-notes-for-adobe-experience-manager}

## Geen informatie {#release-information}

| Product | [!DNL Adobe Experience Manager] |
|---|---|
| Versie | 6.5 |
| Type | Grote release |
| Algemene beschikbaarheidsdatum | 8 april 2019 |
| Aanbevolen updates | Zie [AEM recente updates](https://helpx.adobe.com/experience-manager/aem-releases-updates.html). |

### Trivia {#trivia}

De releasecyclus voor deze versie van [!DNL Adobe Experience Manager] begon op 4 april 2018, doorliep 23 herhalingen van kwaliteitsborging en het bevestigen van fouten, en eindigde op 28 maart 2019. Het totale aantal klantgerelateerde problemen, inclusief verbeteringen en nieuwe functies die in deze release zijn opgelost, is 1345.

[!DNL Adobe Experience Manager] 6.5 is over het algemeen beschikbaar sinds 8 april 2019.

![AEM 6.5 Aanmeldingsscherm](/help/assets/assets/aem65-login-v4.png)

## What&#39;s New {#what-s-new}

[!DNL Adobe Experience Manager] 6.5 is een verbeteringsversie aan de [!DNL Adobe Experience Manager] 6.4 codebasis. Het verstrekt nieuwe en verbeterde functionaliteit, zeer belangrijke klantenmoeilijke situaties, de verhogingen van de hoge prioriteit van de klant en algemene insectenmoeilijke situaties die op productstabilisatie gericht zijn. Het omvat ook [!DNL Adobe Experience Manager] 6.4 de versies van het Pak van de Dienst tot SP4.

De onderstaande lijst biedt een overzicht, terwijl op de volgende pagina&#39;s alle details worden weergegeven.

### [!DNL Experience Manager Foundation] {#experience-manager-foundation}

Volledige lijst van veranderingen in [AEM Stichting](/help/release-notes/wcm-platform.md).

Het platform van [!DNL Adobe Experience Manager] 6.5 bouwt voort op de bijgewerkte versies van het op OSGi gebaseerde framework (Apache Sling en Apache Felix) en de Java Content Repository: Apache Jackrabbit Oak 1.10.2.

De QuickStart gebruikt Eclipse Jetty 9.4.15 als servlet-engine.

#### Java-ondersteuning  {#java-support}

* Nieuwe ondersteuning voor Java 11 en de reeds ondersteunde Java 8.
* Overschrijf voor optimale prestaties de standaard GC-waarden met andere waarden. Zie de sectie [Installeren en bijwerken](/help/sites-deploying/custom-standalone-install.md) voor meer informatie.
* Java 11- en Java 8-onderhoudsupdates worden door Adobe gedistribueerd voor gebruik door klanten in AEM gerelateerde projecten, wanneer deze niet openbaar zijn bij Oracle.

#### Java Development {#java-development}

* Er zijn nu [twee versies van Uberjar](/help/sites-developing/ht-projects-maven.md#experience-manager-api-dependencies), een geadviseerde versie met openbare interfaces die niet duidelijk voor afschrijving zijn, evenals een versie die interfaces duidelijk voor afschrijving omvat.

#### User Interface {#user-interface}

Er zijn verschillende verbeteringen aangebracht in de interface om deze productiever en gebruiksvriendelijker te maken.

* Nieuwe interface voor machtigingenbeheer voor gebruikers en groepen.
* Met Kolomweergaven worden nu ook alleen items geladen die zichtbaar zijn op het scherm en worden alleen meer items geladen wanneer de gebruiker begint met schuiven. De lijst- en kaartweergave heeft dat al gedaan sinds 6.0 (verbeterd in 6.4).
* Kolomweergaven bevatten nu, indien van toepassing, de workflowstatus voor pagina&#39;s/middelen.
* Met de handeling Alles [](/help/sites-authoring/basic-handling.md#select-all) selecteren kunt u snel een handeling uitvoeren met alle pagina&#39;s/middelen in dezelfde map.
* Met de handeling Alles [](/help/sites-authoring/basic-handling.md#select-all) selecteren wordt geprobeerd de handeling op alle pagina&#39;s/elementen uit te voeren, niet alleen op wat is geladen. Er wordt een waarschuwingsvenster weergegeven als de handeling niet is bijgewerkt om Bulk-handelingen af te handelen.

>[!CAUTION]
>
>Adobe is niet van plan om verdere verhogingen aan Klassieke UI te maken. AEM 6.5 heeft de klassieke gebruikersinterface inbegrepen, en klanten die van vroegere versies bevorderen kunnen het blijven gebruiken zoals is. Merk op dat Klassieke UI volledig wordt gesteund terwijl wordt afgekeurd. [Lees meer](/help/sites-deploying/ui-recommendations.md).

#### Zoeken en indexeren {#indexing-and-search}

* Zoeken in eiken ondersteunt nu dynamische facetten. Zo toont de filterrail in de zoekopdracht naar elementen de geschatte hoeveelheid resultaten.
* QueryBuilder is uitgebreid om resultaten met dynamische facetten te bieden.

#### Upgrade {#upgrade}

* Directe upgrade naar AEM 6.5 wordt ondersteund voor klanten die AEM 6.2, 6.3 en 6.4 uitvoeren. Klanten die 5.x of 6.0/6.1 gebruiken die op zijn plaats verbetering willen gebruiken moeten eerst aan 6.4 bevorderen - en dan aan 6.5 bevorderen, of via overdracht van de inhoud tussen de instanties rechtstreeks aan AEM 6.5 bevorderen.

#### Projecten en workflows {#projects-and-workflows}

* De nieuwe die redacteur van het Model van het Werkschema in 6.4 wordt geïntroduceerd is verbeterd om meer verrichtingen zoals het Exemplaar en te publiceren, veranderlijke steun in de stappen van het Werkschema en verbeterde OF en EN splits te omvatten.

### [!DNL Experience Manager] Sites {#experience-manager-sites}

Volledige lijst met wijzigingen in [AEM Sites en invoegtoepassingen](/help/release-notes/sites.md).

#### Beheerde apps met één pagina {#managed-single-page-apps}

De Redacteur van de Pagina voegt de capaciteit aan in-context uit te geven inhoud en samen te stellen/lay-out binnen cliënt-kant teruggegeven ervaringen (ook genoemd [als Redacteur](/help/sites-developing/spa-architecture.md)van het KUUROORD) toe. De bestaande apps van één pagina bouwen met kader JavaScript React of Hoekig kan met AEM SDK worden uitgebreid om editable voor artsen te worden gemaakt.

Eerste verscheepte als deel van AEM 6.4 SP2, met AEM 6.5 de steun van het KUUROORD krijgt volgende mogelijkheden:

* De Redacteur van het Malplaatje van het gebruik om de AEM editable delen van SPA uit te geven en te vormen
* Gebruik Beheer op meerdere locaties om ervaringen met SPA&#39;s te maken met landen, franchise of witte labels

#### Beheer van inhoud zonder hoofd {#headless-content-management}

AEM heeft de mogelijkheid om de inhoud in verschillende indelingen en op verschillende niveaus van de stapel te bedienen. Sommige zijn er al sinds 2008 met de [Sling GET](https://sling.apache.org/documentation/bundles/rendering-content-default-get-servlets.html) en [POST Servlet](https://sling.apache.org/documentation/bundles/manipulating-content-the-slingpostservlet-servlets-post.html). Content Services ([Sling Model Exporter](https://docs.adobe.com/content/help/en/experience-manager-learn/foundation/development/develop-sling-model-exporter.html)) werd geïntroduceerd in AEM 6.3 en is de methode die wordt gebruikt door de AEM SJ SDK om apps van één pagina te hydreren. De [HTTP API voor Middelen](/help/assets/mac-api-assets.md) is een CRUD API, die is uitgebreid voor AEM 6.5.

Nieuwe HTTP API-mogelijkheden:

* Ondersteuning voor [inhoudsfragmenten is toegevoegd aan de HTTP API voor middelen](/help/assets/assets-api-content-fragments.md) voor het maken, bijwerken, lezen en verwijderen van fragmenten.
* Stel lijsten van Inhoudsfragmenten via de Diensten van de Inhoud met de Component [van de Kern van de Lijst van het Fragment van de](https://opensource.adobe.com/aem-core-wcm-components/library/content-fragment-list.html)Inhoud bloot.
* [De Bibliotheek](https://opensource.adobe.com/aem-core-wcm-components/library.html) van de Component van de kern die de standaard output van de Diensten JSON van de Inhoud voor elke component toont

#### Scherminvoegtoepassing {#screens-add-on}

Efficiënt ontwerpen, leveren en optimaliseren ervaringen op alle digitale schermen, van interactieve kiosken tot digitale signage.

**Ontwerp**

* Ervaringen en inhoud op digitale en in-store gelijktrekken met verbeterd hergebruik van inhoud
* Gestroomlijnde workflows voor schrijven en goedkeuren/publiceren met ondersteuning voor Starts
* Bewerk en lever rijke interactieve ervaringen met de SPA Editor

**Leveren**

* Uitgebreide ondersteuning voor mediaspelers met robuuste online en offline bediening (Smart Sync) die kan worden geschaald naar zelfs de grootste signaalnetwerken.

**Optimaliseren**

* Personaliseer door plaats of configuratie van gegevens teweeggebrachte inhoud door dynamische placeholders te gebruiken.
* Verenigde inzichten gedreven door de integratie van Adobe Analytics in de Speler van AEM Screens

Voor meer informatie over veranderingen in AEM Screens - zie de Nota&#39;s van de Versie in de Gids [van de Gebruiker van](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/aem-screens-introduction.html)AEM Screens.

### [!DNL Experience Manager Assets] {#experience-manager-assets}

Volledige lijst met wijzigingen in [AEM 6.5 Opmerkingen](/help/release-notes/assets.md)bij de release Middelen.

AEM 6.5 introduceert de volgende mogelijkheden en verbeteringen om de productiviteit van AEM gebruikers, DAM-rollen en de bijbehorende creatieve en marketingrollen te verhogen.

#### Integration with Adobe Creative Cloud {#integration-with-adobe-creative-cloud}

Dankzij de introductie van [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html), een in-app-ervaring voor creatieve gebruikers die werken in Adobe Creative Cloud-toepassingen, zoals Photoshop, Illustrator en InDesign, wordt de samenwerking tussen creatieve en marketingmedewerkers in het proces voor het maken van inhoud gestroomlijnd. AEM bureaubladtoepassing blijft de behoeften ondersteunen van gebruikers die werken met middelen van AEM op het bureaublad, met elk bestandstype en elke bureaubladtoepassing.

Daarnaast AEM u met Adobe Stock geïntegreerd om Adobe Stock-middelen rechtstreeks vanuit de gebruikersinterface van AEM te zoeken, voor te vertonen, in licentie te geven en op te slaan.

![Deelvenster Asset Link in Photoshop](/help/assets/assets/aem65-assetlink-photoshop.png)

#### Gekoppelde assets {#connected-assets}

De Connected Assets-mogelijkheid is gericht op grotere implementaties met een aantal implementaties van AEM Sites die gebruikmaken van middelen van een centrale DAM-implementatie van AEM Assets. Het staat voor het verbeteren van bestuur rond centraal beheerde activa toe terwijl het toestaan voor hoge efficiency van het leveren van activa aan de diverse plaatsingen van Plaatsen.

###  Dynamic Media {#dynamic-media}

Dynamic Media bieden verbeterde mogelijkheden voor het schrijven en leveren van rijke media in AEM Assets om de meest geavanceerde ervaringen te stimuleren die zowel meeslepend als gepersonaliseerd zijn. Met één master troef van hoge kwaliteit kunt u onze geavanceerde cloudrendering, Smart Crop en best-in-class viewers gebruiken om de meest aantrekkelijke ervaringen met toonaangevende prestaties te bieden.

Nieuwe functies zijn onder andere:

* Ondersteuning voor 360-video- en VR-headsets
* Aangepaste videominiaturen
* Verbeterde toegankelijkheidsondersteuning
* Warmkoppelingsbeveiliging

#### Gebruikerservaring en Zoeken {#user-experience-and-search}

Belangrijke verbeteringen helpen de juiste middelen sneller te vinden door dynamische zoekfacetten te bieden en om meerdere middelen efficiënter te beheren door de mogelijkheid te bieden om alle middelen in een map of zoekresultaat te selecteren.

### [!DNL Adobe Experience Manager Forms] {#experience-manager-forms}

AEM 6.5 Forms biedt verschillende nieuwe functies en verbeteringen. De hooglichten omvatten:

* Transactierapporten om het aantal ingediende formulieren, verwerkte documenten en gerenderde documenten bij te houden
* Verbeteringen in bruikbaarheid van interactieve communicatie
* Digitale handtekeningen op basis van cloud in adaptieve formulieren
* Aangepaste formulieren en interactieve communicatie insluiten in een AEM Sites met één pagina (SPA).
* Ondersteuning voor variabelen in AEM Workflows
* Ondersteuning van gegevenspatronen in interactieve communicatie
* Aangepaste formulieren en interactieve communicatietabellen sorteren
* Geautomatiseerde validatie van invoergegevens in formuliergegevensmodellen

Zie het [overzicht van nieuwe functies en verbeteringen in AEM 6.5 Forms](/help/forms/using/whats-new.md) voor informatie over nieuwe en verbeterde functies en documentatiebronnen.

### [!DNL Experience Manager Communities] {#communitiesreleasenotes}

AEM 6.5 voegt nieuwe functies en verbeteringen toe aan de Gemeenschappen. De belangrijkste punten voor deze release zijn:

* Labelen van geregistreerde leden (@genoemd) wordt ondersteund tijdens het ontwerpen van door gebruikers gegenereerde inhoud.
* Direct bulkberichten naar groepen leden worden nu ondersteund.
* Aangepaste filters ontwikkeld en toegevoegd in UI voor bulkmoderatie. Een [steekproefproject](https://github.com/Adobe-Marketing-Cloud/aem-communities-extensions/tree/master/aem-communities-moderation-filter) dat het filtreren door markeringen aantoont kan als basis worden gebruikt om analoge douanefilters te ontwikkelen.
* De nieuwe Mening van de Lijst wordt voorzien van verbeterde UI in Bulk Moderatie die.
* De afzonderlijke beheerders voor verschillende communautaire plaatsen en genestelde groepen kunnen worden toegewezen, in plaats van één enkele communautaire beheerder.
* Functionaliteit van AEM 6.5 Communities ondersteunt [(SCORM) 2017.1](https://rusticisoftware.com/blog/scorm-engine-2017-released/) -engine.
* Ondersteuning voor toetsenbordnavigatie op componenten voor betere toegankelijkheid.
* Apache Solr 7.0 ondersteunde tijdens het instellen van MSRP en DSRP.

Voor een gedetailleerde lijst van veranderingen, zie [AEM 6.5 de versienota](/help/release-notes/communities-release-notes.md)van Gemeenschappen.

### [!DNL Experience Manager Livefyre] {#experience-manager-livefyre}

U kunt Livefyre met uw AEM 6.5 instantie integreren. Zie [hoe u Livefyre kunt integreren met AEM](https://docs.adobe.com/content/help/en/experience-manager-64/administering/integration/livefyre.html).

### Gebruik van klantgerichte ontwikkeling {#leverage-customer-focused-development}

Adobe gebruikt een klantgericht ontwikkelingsmodel dat klanten toestaat om aan alle stadia van het ontwikkelingsproces, tijdens specificatie, ontwikkeling en het testen bij te dragen. Onze dank gaat uit naar alle klanten en partners die een bijdrage leveren aan dit proces.

Adobe heeft de procedures en de processen op zijn plaats om inzameling, prioritering, en het volgen van klant gerichte insectenresolutie en de ontwikkeling van verbeteringsverzoeken toe te laten. Het portaal [van de Steun van de](https://helpx.adobe.com/nl/contact/enterprise-support.ec.html) Adobe Marketing Cloud is geïntegreerd met de Verbetering van de Adobe en het Systeem van het Tekstspatiëring. Vragen van de klant worden waar mogelijk met de klantenservice geïdentificeerd en opgelost. Bij doorverwijzing naar O&amp;O wordt alle klantinformatie vastgelegd en gebruikt voor prioritering en rapportage. Prioriteit wordt gegeven in ontwikkeling aan betaalde steun, garantiekwesties, en klant-betaalde verhogingen.

Dit proces van prioritering heeft meer dan 750 klantgerichte veranderingen opgeleverd die in AEM 6.5 worden bevestigd.

## Lijst met bestanden die deel uitmaken van de release {#list-of-files-that-are-part-of-the-release}

**Stichting**

* Standalone QuickStart: `cq-quickstart-6.5.0.jar`.
* Quickstart toepassingsserver: `cq-quickstart-6.5.0.war`.
* Dispatcher 4.3.2 of hoger voor de verschillende webservers en -platforms. Zie [downloadkoppeling](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/getting-started/release-notes.html)
* Plug-in voor Eclipse IDE (meer[lezen en downloaden](/help/sites-developing/aem-eclipse.md))

* Extension for Brackets Code Editor (meer[lezen en downloaden](/help/sites-developing/aem-brackets.md))
* Geweven/de Beelddelen van de Wieg ([downloadverbinding](https://repo.adobe.com/nexus/content/repositories/releases/com/adobe/aem/uber-jar/6.5.0/))

**Sites**

* Core Components ([GitHub-project](https://github.com/adobe/aem-core-wcm-components))
* We.Retail Reference Implementation ([lees meer](/help/sites-developing/we-retail.md))
* Maven Project archetypes:

   * voor volledig-stapelsites: [GitHub-project](https://github.com/adobe/aem-project-archetype)
   * voor apps van één pagina met React/Hoekig: [GitHub-project](https://github.com/adobe/aem-spa-project-archetype)

* AEM Screens voor verschillende doelplatforms ([downloaden](https://download.macromedia.com/screens/))

* Smart Content Language Models. Engels is vooraf geïnstalleerd - meer talen kunnen worden gedownload

   * [Duits](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-de)
   * [Spaans](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-es)
   * [Italiaans](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-it)
   * [Frans](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-fr)

* AEM Tools Suite moderniseren, bijvoorbeeld Dialog Conversion Tool. ([GitHub-project](https://github.com/adobe/aem-modernize-tools))

**Assets**

* Pakket maken om verbeterde PDF-rasterfunctie toe te voegen ([lees meer](/help/assets/aem-pdf-rasterizer.md))
* Pakket maken om uitgebreide ondersteuning voor RAW-afbeeldingen toe te voegen ([lees meer](/help/assets/camera-raw.md))

**Forms**

* [Pakketten voor AEM Forms](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html)
* [AEM Forms OSGi Client SDK](https://repo.adobe.com/nexus/content/repositories/public/com/adobe/aemfd/aemfd-client-sdk/6.0.80/)

## Talen {#languages}

De gebruikersinterface is beschikbaar in de volgende talen:

* Engels
* Duits
* Frans
* Spaans
* Italiaans
* Braziliaans Portugees
* Japans
* Vereenvoudigd Chinees
* Traditioneel Chinees (beperkte ondersteuning)
* Koreaans

[!DNL Experience Manager] 6.5 is gecertificeerd voor GB18030-2005 CITS om de Chinese coderingsstandaard te gebruiken.

## Installeren en bijwerken {#install-update}

Zie de [installatie-instructies](/help/sites-deploying/custom-standalone-install.md)voor de installatievereisten.

Zie de [upgradedocumentatie](/help/sites-deploying/upgrade.md)voor gedetailleerde instructies.

## Ondersteunde Platforms {#supported-platforms}

Zoek naar de volledige matrix van ondersteunde platforms, inclusief support op [AEM 6.5 technische vereisten](/help/sites-deploying/technical-requirements.md).

>[!NOTE]
>
>Oracle is overgestapt op een LTS-model (Long Term Support) voor Oracle Java SE-producten. Java 9 en 10 zijn niet-LTS-versies van Oracle. Zie [Oracle Java SE-supportroutekaart](https://www.oracle.com/technetwork/java/eol-135779.html). Adobe biedt ondersteuning voor LTS-versies van Java, zodat alleen AEM in productie worden uitgevoerd. Java 11 is de aanbevolen versie voor gebruik met AEM 6.5.

## Verouderde en verwijderde functies {#deprecated-and-removed-features}

Adobe evalueert constant mogelijkheden in het product en in tijd plannen om mogelijkheden met krachtigere versies te vervangen, of besluit om geselecteerde delen opnieuw uit te voeren om beter voor toekomstige verwachtingen of uitbreidingen worden voorbereid.

Voor [!DNL Adobe Experience Manager] 6.5 [leest u de lijst met afgekeurde en verwijderde mogelijkheden](/help/release-notes/deprecated-removed-features.md). De pagina bevat ook een vooraankondiging van wijzigingen in de nabije toekomst en belangrijke kennisgeving voor klanten die een update uitvoeren van eerdere releases.

## Bekende problemen {#known-issues}

[Lijst met bekende problemen](/help/release-notes/known-issues.md)

### Productdownload en -ondersteuning (beperkt aantal sites) {#product-download-and-support-restricted-sites}

De volgende sites zijn alleen beschikbaar voor klanten. Als u een klant bent en toegang nodig hebt, neemt u contact op met uw Adobe-accountmanager.

* [Product downloaden op licensing.adobe.com](https://licensing.adobe.com/).

* Productupdates, patches en pakketten voor extra functionaliteit op het gebied van [softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).

* [Klantenondersteuning via Admin Console](https://adminconsole.adobe.com/). Zie [Nieuwe Adobe Customer Support Experience](https://docs.adobe.com/content/help/en/customer-one/using/home.html)voor meer informatie.
