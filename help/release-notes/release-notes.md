---
title: Algemene opmerkingen bij de release van [!DNL Adobe Experience Manager] 6.5
description: '[!DNL Adobe Experience Manager] 6.5 notities waarin de releasegegevens, de nieuwe functies, de installatie en gedetailleerde lijsten met wijzigingen worden beschreven.'
translation-type: tm+mt
source-git-commit: 8d60e064ab50f24016c049c8d5d0fceb784c99a3
workflow-type: tm+mt
source-wordcount: '2150'
ht-degree: 1%

---


# Algemene opmerkingen bij de release [!DNL Adobe Experience Manager] 6.5{#general-release-notes-for-adobe-experience-manager}

## Informatie opheffen {#release-information}

| Product | [!DNL Adobe Experience Manager] |
|---|---|
| Versie | 6,5 |
| Type | Grote release |
| Algemene beschikbaarheidsdatum | 8 april 2019 |
| Aanbevolen updates | Zie [AEM recente updates](https://helpx.adobe.com/experience-manager/aem-releases-updates.html). |

### Trivia {#trivia}

De releasecyclus voor deze versie van [!DNL Adobe Experience Manager] is op 4 april 2018 gestart, 23 versies van kwaliteitsborging en het corrigeren van fouten doorlopen en op 28 maart 2019 afgelopen. Het totale aantal klantgerelateerde problemen, inclusief verbeteringen en nieuwe functies die in deze release zijn opgelost, is 1345.

[!DNL Adobe Experience Manager] 6.5 is over het algemeen beschikbaar sinds 8 april 2019.

![AEM 6.5 Aanmeldingsscherm](/help/assets/assets/aem65-login-v4.png)

## Wat is er nieuw?{#what-s-new}

[!DNL Adobe Experience Manager] 6.5 is een verbeteringsversie aan de  [!DNL Adobe Experience Manager] 6.4 codebasis. Het verstrekt nieuwe en verbeterde functionaliteit, zeer belangrijke klantenmoeilijke situaties, de verhogingen van de hoge prioriteit van de klant en algemene insectenmoeilijke situaties die op productstabilisatie gericht zijn. Het omvat ook [!DNL Adobe Experience Manager] 6.4 Service Pack-releases tot SP4.

De onderstaande lijst biedt een overzicht, terwijl op de volgende pagina&#39;s alle details worden weergegeven.

### [!DNL Experience Manager Foundation] {#experience-manager-foundation}

Volledige lijst van veranderingen in [AEM Stichting](/help/release-notes/wcm-platform.md).

Het platform van [!DNL Adobe Experience Manager] 6.5 bouwt voort op bijgewerkte versies van het op OSGi-Gebaseerde kader (Apache Sling en Apache Felix) en de Inhoudsbewaarder van Java: Apache Jackrabbit Oak 1.10.2.

De QuickStart gebruikt Eclipse Jetty 9.4.15 als servlet-engine.

#### Java-ondersteuning {#java-support}

* Nieuwe ondersteuning voor Java 11 en de reeds ondersteunde Java 8.
* Overschrijf voor optimale prestaties de standaard GC-waarden met andere waarden. Zie de sectie [installeren en bijwerken](/help/sites-deploying/custom-standalone-install.md) voor meer informatie.
* Java 11- en Java 8-onderhoudsupdates worden door Adobe gedistribueerd voor gebruik door klanten in AEM gerelateerde projecten, wanneer deze niet openbaar beschikbaar zijn in Oracle.

#### Java Development {#java-development}

* Er zijn nu [twee versies van Uberjar](/help/sites-developing/ht-projects-maven.md#experience-manager-api-dependencies), een geadviseerde versie met openbare interfaces die niet duidelijk voor afschrijving zijn, evenals een versie die interfaces duidelijk voor afschrijving omvat.

#### Gebruikersinterface {#user-interface}

Er zijn verschillende verbeteringen aangebracht in de interface om deze productiever en gebruiksvriendelijker te maken.

* Nieuwe interface voor machtigingenbeheer voor gebruikers en groepen.
* Met Kolomweergaven worden nu ook alleen items geladen die zichtbaar zijn op het scherm en worden alleen meer items geladen wanneer de gebruiker begint met schuiven. De lijst- en kaartweergave heeft dat al gedaan sinds 6.0 (verbeterd in 6.4).
* Kolomweergaven bevatten nu, indien van toepassing, de workflowstatus voor pagina&#39;s/middelen.
* De handeling [Alles selecteren](/help/sites-authoring/basic-handling.md#select-all) is een snelle manier om een handeling uit te voeren met alle pagina&#39;s/middelen in dezelfde map.
* Met de handeling [Alles selecteren](/help/sites-authoring/basic-handling.md#select-all) wordt geprobeerd de handeling uit te voeren op alle pagina&#39;s/elementen, niet alleen op wat is geladen. Er wordt een waarschuwingsvenster weergegeven als de handeling niet is bijgewerkt om Bulk-handelingen af te handelen.

>[!CAUTION]
>
>Adobe is niet van plan om verdere verhogingen aan Klassieke UI te maken. AEM 6.5 heeft de klassieke gebruikersinterface inbegrepen, en klanten die van vroegere versies bevorderen kunnen het blijven gebruiken zoals is. Merk op dat Klassieke UI volledig wordt gesteund terwijl wordt afgekeurd. [Lees meer](/help/sites-deploying/ui-recommendations.md).

#### {#indexing-and-search} zoeken en indexeren

* Zoeken in eiken ondersteunt nu dynamische facetten. Zo toont de filterrail in de zoekopdracht naar elementen de geschatte hoeveelheid resultaten.
* QueryBuilder is uitgebreid om resultaten met dynamische facetten te bieden.

#### Upgrade {#upgrade}

* Directe upgrade naar AEM 6.5 wordt ondersteund voor klanten die AEM 6.2, 6.3 en 6.4 uitvoeren. Klanten die 5.x of 6.0/6.1 gebruiken die op zijn plaats verbetering willen gebruiken moeten eerst aan 6.4 bevorderen - en dan aan 6.5 bevorderen, of via overdracht van de inhoud tussen de instanties rechtstreeks aan AEM 6.5 bevorderen.

#### Projecten en workflows {#projects-and-workflows}

* De nieuwe die redacteur van het Model van het Werkschema in 6.4 wordt geïntroduceerd is verbeterd om meer verrichtingen zoals het Exemplaar en te publiceren, veranderlijke steun in de stappen van het Werkschema en verbeterde OF en EN splits te omvatten.

### [!DNL Experience Manager] Sites {#experience-manager-sites}

Volledige lijst van veranderingen in [AEM Sites en toe:voegen-ons](/help/release-notes/sites.md).

#### Beheerde apps voor één pagina {#managed-single-page-apps}

De Pagina-editor voegt de mogelijkheid toe om in de context inhoud te bewerken en samen te stellen/op te maken in gerenderde ervaringen op de client (ook wel [SPA Editor](/help/sites-developing/spa-architecture.md) genoemd). De bestaande apps van één pagina bouwen met kader JavaScript React of Hoekig kan met AEM SDK worden uitgebreid om editable voor artsen te worden gemaakt.

De eerste verscheepte als deel van AEM 6.4 SP2, met AEM 6.5 de SPA steun krijgt volgende mogelijkheden:

* De Redacteur van het Malplaatje van het gebruik om de AEM editable delen van de SPA uit te geven en te vormen
* Met beheer op meerdere locaties kunt u ervaringen met landspecifieke, franchise- of witgelabelde SPA creëren

#### Beheer van inhoud zonder hoofd {#headless-content-management}

AEM heeft de mogelijkheid om de inhoud in verschillende indelingen en op verschillende niveaus van de stapel te bedienen. Sommige zijn sinds 2008 rond met [Sling GET](https://sling.apache.org/documentation/bundles/rendering-content-default-get-servlets.html) en [POST Servlet](https://sling.apache.org/documentation/bundles/manipulating-content-the-slingpostservlet-servlets-post.html). Content Services ([Sling Model Exporter](https://docs.adobe.com/content/help/en/experience-manager-learn/foundation/development/develop-sling-model-exporter.html)) is geïntroduceerd in AEM 6.3 en is de methode die wordt gebruikt door de AEM SJ SDK om apps van één pagina te hydrateren. De [HTTP-API voor Middelen](/help/assets/mac-api-assets.md) is een CRUD-API, die is uitgebreid voor AEM 6.5.

Nieuwe HTTP API-mogelijkheden:

* [Ondersteuning voor inhoudsfragmenten is toegevoegd aan de HTTP API voor Elementen](/help/assets/assets-api-content-fragments.md) om fragmenten te maken, bij te werken, te lezen en te verwijderen.
* Stel lijsten van Inhoudsfragmenten via de Diensten van de Inhoud met [de Component van de Kern van de Lijst van het Fragment van de Inhoud ](https://opensource.adobe.com/aem-core-wcm-components/library/content-fragment-list.html) bloot.
* [Core Component ](https://opensource.adobe.com/aem-core-wcm-components/library.html) Library die de standaard Content Services JSON-uitvoer voor elke component weergeeft

#### Scherminvoegtoepassing {#screens-add-on}

Efficiënt ontwerpen, leveren en optimaliseren ervaringen op alle digitale schermen, van interactieve kiosken tot digitale signage.

**Ontwerp**

* Ervaringen en inhoud op digitale en in-store gelijktrekken met verbeterd hergebruik van inhoud
* Gestroomlijnde workflows voor schrijven en goedkeuren/publiceren met ondersteuning voor Starts
* Rijke interactieve ervaringen bewerken en leveren met SPA Editor

**Leveren**

* Uitgebreide ondersteuning voor mediaspelers met robuuste online en offline bediening (Smart Sync) die kan worden geschaald naar zelfs de grootste signaalnetwerken.

**Optimaliseren**

* Personaliseer door plaats of configuratie van gegevens teweeggebrachte inhoud door dynamische placeholders te gebruiken.
* Verenigde inzichten gedreven door de integratie van Adobe Analytics in AEM Screens Player

Voor meer details over veranderingen in AEM Screens - zie de Nota&#39;s van de Versie in [de Gids van de Gebruiker van AEM Screens](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/aem-screens-introduction.html).

### [!DNL Experience Manager Assets] {#experience-manager-assets}

Volledige lijst met wijzigingen in [AEM 6.5 Opmerkingen bij de release Elementen](/help/release-notes/assets.md).

AEM 6.5 introduceert de volgende mogelijkheden en verbeteringen om de productiviteit van AEM gebruikers, DAM-rollen en de bijbehorende creatieve en marketingrollen te verhogen.

#### Integratie met Adobe Creative Cloud {#integration-with-adobe-creative-cloud}

Dankzij de introductie van [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html), een ervaring in de app voor creatieve gebruikers die werken in Adobe Creative Cloud-toepassingen, zoals Photoshop, Illustrator en InDesign, wordt de samenwerking tussen creatieve en marketingmedewerkers in het proces voor het maken van inhoud gestroomlijnd. AEM bureaubladtoepassing blijft de behoeften ondersteunen van gebruikers die werken met middelen van AEM op het bureaublad, met elk bestandstype en elke bureaubladtoepassing.

Daarnaast AEM u met Adobe Stock geïntegreerd om Adobe Stock-middelen rechtstreeks vanuit de gebruikersinterface van AEM te zoeken, voor te vertonen, in licentie te geven en op te slaan.

![Deelvenster Asset Link in Photoshop](/help/assets/assets/aem65-assetlink-photoshop.png)

#### Gekoppelde assets {#connected-assets}

De Connected Assets-mogelijkheid is gericht op grotere implementaties met een aantal AEM Sites-implementaties die middelen van een centrale AEM Assets DAM-implementatie moeten benutten. Het staat voor het verbeteren van bestuur rond centraal beheerde activa toe terwijl het toestaan voor hoge efficiency van het leveren van activa aan de diverse plaatsingen van Plaatsen.

###  Dynamic Media {#dynamic-media}

Dynamic Media biedt verbeterde mogelijkheden voor het schrijven en leveren van rijke media in AEM Assets, zodat u de meest geavanceerde ervaringen kunt opdoen die u zowel immersief als gepersonaliseerd vindt. Met één master troef van hoge kwaliteit kunt u onze geavanceerde cloudrendering, Smart Crop en best-in-class viewers gebruiken om de meest aantrekkelijke ervaringen met toonaangevende prestaties te bieden.

Nieuwe functies zijn onder andere:

* Ondersteuning voor 360-video- en VR-headsets
* Aangepaste videominiaturen
* Verbeterde toegankelijkheidsondersteuning
* Warmkoppelingsbeveiliging

#### Gebruikerservaring en zoeken {#user-experience-and-search}

Belangrijke verbeteringen helpen de juiste middelen sneller te vinden door dynamische zoekfacetten te bieden en om meerdere middelen efficiënter te beheren door de mogelijkheid te bieden om alle middelen in een map of zoekresultaat te selecteren.

### [!DNL Adobe Experience Manager Forms] {#experience-manager-forms}

AEM 6.5 Forms biedt verschillende nieuwe functies en verbeteringen. De hooglichten omvatten:

* Transactierapporten om het aantal ingediende formulieren, verwerkte documenten en gerenderde documenten bij te houden
* Verbeteringen in bruikbaarheid van interactieve communicatie
* Digitale handtekeningen op basis van cloud in adaptieve formulieren
* Aangepaste formulieren en interactieve communicatie insluiten in AEM Sites-toepassingen van één pagina (SPA).
* Ondersteuning voor variabelen in AEM Workflows
* Ondersteuning van gegevenspatronen in interactieve communicatie
* Aangepaste formulieren en interactieve communicatietabellen sorteren
* Geautomatiseerde validatie van invoergegevens in formuliergegevensmodellen

Zie [Overzicht van nieuwe functies en verbeteringen in AEM 6.5 Forms](/help/forms/using/whats-new.md) voor informatie over nieuwe en verbeterde functies en documentatiebronnen.

### [!DNL Experience Manager Communities] {#communitiesreleasenotes}

AEM 6.5 voegt nieuwe functies en verbeteringen toe aan de Gemeenschappen. De belangrijkste punten voor deze release zijn:

* Labelen van geregistreerde leden (@genoemd) wordt ondersteund tijdens het ontwerpen van door gebruikers gegenereerde inhoud.
* Direct bulkberichten naar groepen leden worden nu ondersteund.
* Aangepaste filters ontwikkeld en toegevoegd in UI voor bulkmoderatie. Een [voorbeeldproject](https://github.com/Adobe-Marketing-Cloud/aem-communities-extensions/tree/master/aem-communities-moderation-filter) dat het filtreren door markeringen aantoont kan als basis worden gebruikt om analoge douanefilters te ontwikkelen.
* De nieuwe Mening van de Lijst wordt voorzien van verbeterde UI in Bulk Moderatie die.
* De afzonderlijke beheerders voor verschillende communautaire plaatsen en genestelde groepen kunnen worden toegewezen, in plaats van één enkele communautaire beheerder.
* Functionaliteit voor activering van AEM 6.5 Communities ondersteunt [(SCORM) 2017.1](https://rusticisoftware.com/blog/scorm-engine-2017-released/) engine.
* Ondersteuning voor toetsenbordnavigatie op componenten voor betere toegankelijkheid.
* Apache Solr 7.0 ondersteunde tijdens het instellen van MSRP en DSRP.

Zie [AEM 6.5 Opmerkingen bij de release van Communities](/help/release-notes/communities-release-notes.md) voor een gedetailleerde lijst met wijzigingen.

### [!DNL Experience Manager Livefyre] {#experience-manager-livefyre}

U kunt Livefyre met uw AEM 6.5 instantie integreren. Zie [Hoe te om Levenswijze met AEM](https://docs.adobe.com/content/help/en/experience-manager-64/administering/integration/livefyre.html) te integreren.

### Gebruik klantgerichte ontwikkeling {#leverage-customer-focused-development}

Adobe gebruikt een klantgericht ontwikkelingsmodel dat klanten toestaat om aan alle stadia van het ontwikkelingsproces, tijdens specificatie, ontwikkeling en het testen bij te dragen. Onze dank gaat uit naar alle klanten en partners die een bijdrage leveren aan dit proces.

Adobe heeft de procedures en de processen op zijn plaats om inzameling, prioritering, en het volgen van klant gerichte insectenresolutie en de ontwikkeling van verbeteringsverzoeken toe te laten. Het [Adobe Marketing Cloud Support Portal](https://helpx.adobe.com/nl/contact/enterprise-support.ec.html) is geïntegreerd met het systeem voor het bijhouden van Adobe-waarden en-fouten. Vragen van de klant worden waar mogelijk met de klantenservice geïdentificeerd en opgelost. Bij doorverwijzing naar O&amp;O wordt alle klantinformatie vastgelegd en gebruikt voor prioritering en rapportage. Prioriteit wordt gegeven in ontwikkeling aan betaalde steun, garantiekwesties, en klant-betaalde verhogingen.

Dit proces van prioritering heeft meer dan 750 klantgerichte veranderingen opgeleverd die in AEM 6.5 worden bevestigd.

## Lijst met bestanden die deel uitmaken van de release {#list-of-files-that-are-part-of-the-release}

**Stichting**

* Standalone QuickStart: `cq-quickstart-6.5.0.jar`.
* Quickstart toepassingsserver: `cq-quickstart-6.5.0.war`.
* Dispatcher 4.3.2 of hoger voor de verschillende webservers en -platforms. Zie [downloadkoppeling](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/getting-started/release-notes.html)
* Plug-in voor Eclipse IDE ([meer lezen en downloaden](/help/sites-developing/aem-eclipse.md))

* Extensie voor de Redacteur van de Code van Brackets ([lees meer en download](/help/sites-developing/aem-brackets.md))
* Geweven/de Afhankelijkheden van de Wieg ([downloadverbinding](https://repo.adobe.com/nexus/content/repositories/releases/com/adobe/aem/uber-jar/6.5.0/))

**Sites**

* De Componenten van de kern ([GitHub project](https://github.com/adobe/aem-core-wcm-components))
* We.Retail Reference Implementation ([lees meer](/help/sites-developing/we-retail.md))
* Maven Project archetypes:

   * voor volledig-stapelsites: [GitHub-project](https://github.com/adobe/aem-project-archetype)
   * voor apps van één pagina met React/Hoekig: [GitHub-project](https://github.com/adobe/aem-spa-project-archetype)

* AEM Screens Players voor diverse doelplatforms ([download](https://download.macromedia.com/screens/))

* Smart Content Language Models. Engels is vooraf geïnstalleerd - meer talen kunnen worden gedownload

   * [Duits](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-de)
   * [Spaans](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-es)
   * [Italiaans](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-it)
   * [Frans](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-fr)

* AEM Tools Suite moderniseren, bijvoorbeeld Dialog Conversion Tool. ([GitHub project](https://github.com/adobe/aem-modernize-tools))

**Assets**

* Pakket maken om verbeterde PDF-rasterfunctie toe te voegen ([meer lezen](/help/assets/aem-pdf-rasterizer.md))
* Pakket om uitgebreide RAW beeldsteun toe te voegen ([lees meer](/help/assets/camera-raw.md))

**Forms**

* [Pakketten voor AEM Forms-mogelijkheden](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html)
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

## {#install-update} installeren en bijwerken

Zie [installatie-instructies](/help/sites-deploying/custom-standalone-install.md) voor instellingsvereisten.

Voor gedetailleerde instructies, zie [verbeteringsdocumentatie](/help/sites-deploying/upgrade.md).

## Ondersteunde Platforms {#supported-platforms}

Vind de volledige matrijs van gesteunde platforms met steun-niveau op [AEM 6.5 technische vereisten](/help/sites-deploying/technical-requirements.md).

>[!NOTE]
>
>Oracle is overgestapt op een LTS-model (Long Term Support) voor Oracle Java SE-producten. Java 9 en 10 zijn niet-LTS versies van Oracle. Zie [Oracle Java SE support roadmap](https://www.oracle.com/technetwork/java/eol-135779.html). Adobe biedt ondersteuning voor LTS-versies van Java, zodat alleen AEM in productie worden uitgevoerd. Java 11 is de aanbevolen versie voor gebruik met AEM 6.5.

## Vervangen en verwijderde functies {#deprecated-and-removed-features}

Adobe evalueert constant mogelijkheden in het product en in tijd plannen om mogelijkheden met krachtigere versies te vervangen, of besluit om geselecteerde delen opnieuw uit te voeren om beter voor toekomstige verwachtingen of uitbreidingen worden voorbereid.

Voor [!DNL Adobe Experience Manager] 6.5, [lees de lijst van afgekeurde en verwijderde mogelijkheden](/help/release-notes/deprecated-removed-features.md). De pagina bevat ook een vooraankondiging van wijzigingen in de nabije toekomst en belangrijke kennisgeving voor klanten die een update uitvoeren van eerdere releases.

## Bekende problemen {#known-issues}

[Lijst met bekende problemen](/help/release-notes/known-issues.md)

### Productdownload en -ondersteuning (Beperkte sites) {#product-download-and-support-restricted-sites}

De volgende sites zijn alleen beschikbaar voor klanten. Als u een klant bent en toegang nodig hebt, neemt u contact op met uw Adobe-accountmanager.

* [Product downloaden op licensing.adobe.com](https://licensing.adobe.com/).

* Productupdates, patches en pakketten voor extra functionaliteit op [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).

* [Klantenondersteuning via Admin Console](https://adminconsole.adobe.com/). Zie [Nieuwe ervaring voor klantenondersteuning van Adobe](https://docs.adobe.com/content/help/en/customer-one/using/home.html) voor meer informatie.
