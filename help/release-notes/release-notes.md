---
title: Algemene opmerkingen bij de release van Adobe Experience Manager 6.5
description: In Adobe Experience Manager 6.5 worden de releasegegevens, de nieuwe functies, de installatie en gedetailleerde wijzigingslijsten beschreven.
uuid: b916624e-9486-4391-8c6f-cb4045e78490
contentOwner: chuesler
products: SG_EXPERIENCEMANAGER/6.5
discoiquuid: 7d3ceccb-4f00-4e11-9c9f-6de46a455e02
docset: aem65
translation-type: tm+mt
source-git-commit: 23dfcc944a83dd683078cfe00f85c4cc734e7752
workflow-type: tm+mt
source-wordcount: '2182'
ht-degree: 1%

---


# Algemene opmerkingen bij de release van Adobe Experience Manager 6.5{#general-release-notes-for-adobe-experience-manager}

## Geen informatie {#release-information}

<table>
 <tbody>
  <tr>
   <th>Product</th>
   <td>Adobe Experience Manager<br /> </td>
  </tr>
  <tr>
   <th>Versie</th>
   <td>6.5</td>
  </tr>
  <tr>
   <th>Type</th>
   <td>Primaire release</td>
  </tr>
  <tr>
   <th>Algemene beschikbaarheidsdatum</th>
   <td>8 april 2019<br /> </td>
  </tr>
  <tr>
   <th>Aanbevolen updates</th>
   <td>Zie <a href="https://helpx.adobe.com/experience-manager/aem-releases-updates.html">AEM-releases en -updates</a></td>
  </tr>
 </tbody>
</table>

### Trivia {#trivia}

De releasecyclus voor deze versie van Adobe Experience Manager is gestart op 4 april 2018, doorloopt 23 versies van kwaliteitsborging en het corrigeren van fouten en eindigt op 28 maart 2019. Het totale aantal klantgerelateerde problemen, inclusief verbeteringen en nieuwe functies die in deze release zijn opgelost, is 1345.

Adobe Experience Manager 6.5 is over het algemeen beschikbaar sinds 8 april 2019.

![Aanmeldingsscherm AEM 6.5](/help/assets/assets/aem65-login-v4.png)

## What&#39;s New {#what-s-new}

Adobe Experience Manager 6.5 is een verbeteringsversie aan Adobe Experience Manager 6.4 codebasis. Het verstrekt nieuwe en verbeterde functionaliteit, zeer belangrijke klantenmoeilijke situaties, de verhogingen van de hoge prioriteit van de klant en algemene insectenmoeilijke situaties die op productstabilisatie gericht zijn. Het omvat ook Adobe Experience Manager 6.4 Service Pack versies tot SP4.

De onderstaande lijst biedt een overzicht, terwijl op de volgende pagina&#39;s alle details worden weergegeven.

### Experience Manager Foundation {#experience-manager-foundation}

Volledige lijst met wijzigingen in [AEM Foundation](/help/release-notes/wcm-platform.md).

Het platform van Adobe Experience Manager 6.5 bouwt voort op de bijgewerkte versies van het op OSGi gebaseerde kader (Apache Sling en Apache Felix) en de Inhoudsgegevensbank van Java: Apache Jackrabbit Oak 1.10.2.

De QuickStart gebruikt Eclipse Jetty 9.4.15 als servlet-engine.

#### Java-ondersteuning  {#java-support}

* Nieuwe ondersteuning voor Java 11 en de reeds ondersteunde Java 8
* Overschrijf voor optimale prestaties de standaard GC-waarden met andere waarden. Zie de sectie [Installeren en bijwerken](/help/sites-deploying/custom-standalone-install.md) voor meer informatie.
* Updates voor Java 11- en Java 8-onderhoud worden door Adobe gedistribueerd voor gebruik door klanten in AEM-gerelateerde projecten, indien deze niet openbaar zijn via Oracle

#### Java Development {#java-development}

* Er zijn nu [twee versies van Uberjar](/help/sites-developing/ht-projects-maven.md#experience-manager-api-dependencies), een geadviseerde versie met openbare interfaces die niet duidelijk voor afschrijving zijn, evenals een versie die interfaces duidelijk voor afschrijving omvat.

#### User Interface {#user-interface}

Er zijn verschillende verbeteringen aangebracht in de interface om deze productiever en gebruiksvriendelijker te maken.

* Nieuwe interface voor machtigingenbeheer voor gebruikers en groepen
* Met Kolomweergaven worden nu ook alleen items geladen die zichtbaar zijn op het scherm en worden alleen meer items geladen wanneer de gebruiker begint met schuiven. De lijst- en kaartweergave heeft dat al gedaan sinds 6.0 (verbeterd in 6.4)
* Kolomweergaven bevatten nu, indien van toepassing, de workflowstatus voor pagina&#39;s/middelen
* De handeling Alles [](/help/sites-authoring/basic-handling.md#select-all) selecteren is een snelle manier om een handeling uit te voeren met alle pagina&#39;s/middelen in dezelfde map
* Met de handeling Alles [](/help/sites-authoring/basic-handling.md#select-all) selecteren wordt geprobeerd de handeling op alle pagina&#39;s/elementen uit te voeren, niet alleen op wat is geladen. Er wordt een waarschuwingsvenster weergegeven als de handeling niet is bijgewerkt om Handelingen met opsommingstekens te verwerken

>[!CAUTION]
>
>Adobe is niet van plan verdere verbeteringen aan te brengen in de klassieke gebruikersinterface. AEM 6.5 heeft de Klassieke inbegrepen UI, en de klanten die van vroegere versies bevorderen kunnen het blijven gebruiken zoals is. Merk op dat Klassieke UI volledig wordt gesteund terwijl wordt afgekeurd. [Lees meer](/help/sites-deploying/ui-recommendations.md).

#### Zoeken en indexeren {#search-indexing}

* Zoeken in eiken ondersteunt nu dynamische facetten. Zo toont de filterrail in de zoekopdracht naar elementen de geschatte hoeveelheid resultaten.
* QueryBuilder is uitgebreid om resultaten met dynamische facetten te bieden

#### Upgrade {#upgrade}

* Directe upgrade naar AEM 6.5 wordt ondersteund voor klanten met AEM 6.2, 6.3 en 6.4. Klanten die 5.x of 6.0/6.1 gebruiken die op zijn plaats verbetering willen gebruiken moeten eerst aan 6.4 bevorderen - en dan aan 6.5 bevorderen, of via overdracht van de inhoud tussen de instanties rechtstreeks aan AEM 6.5 bevorderen.

#### Projecten en workflows {#projects-and-workflows}

* De nieuwe die redacteur van het Model van het Werkschema in 6.4 wordt geïntroduceerd is verbeterd om meer verrichtingen zoals het Exemplaar en te publiceren, veranderlijke steun in de stappen van het Werkschema en verbeterde OF en EN splits te omvatten.

### Experience Manager-sites {#experience-manager-sites}

Volledige lijst met wijzigingen in [AEM Sites en invoegtoepassingen](/help/release-notes/sites.md).

#### Beheerde apps met één pagina {#managed-single-page-apps}

De Redacteur van de Pagina voegt de capaciteit aan in-context uit te geven inhoud en samen te stellen/lay-out binnen cliënt-kant teruggegeven ervaringen (ook genoemd [als Redacteur](/help/sites-developing/spa-architecture.md)van het KUUROORD) toe. Bestaande apps van één pagina die worden gemaakt met JavaScript Framework React of Angular kunnen worden uitgebreid met de AEM SJ SDK om bewerkbaar te worden gemaakt voor professionals.

Eerste verscheepte als deel van AEM 6.4 SP2, met AEM 6.5 de steun van het KUUROORD krijgt volgende mogelijkheden:

* De Redacteur van het Malplaatje van het gebruik om de editable delen van AEM uit te geven en te vormen SPA
* Gebruik Beheer op meerdere locaties om ervaringen met SPA&#39;s te maken met landen, franchise of witte labels

#### Beheer van inhoud zonder hoofd {#headless-content-management}

AEM kan de inhoud in verschillende indelingen en op verschillende niveaus van de stapel leveren. Sommige zijn er al sinds 2008 met de [Sling GET](https://sling.apache.org/documentation/bundles/rendering-content-default-get-servlets.html) en [POST Servlet](https://sling.apache.org/documentation/bundles/manipulating-content-the-slingpostservlet-servlets-post.html). Content Services ([Sling Model Exporter](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/sling-model-exporter-tutorial-develop.html)) is geïntroduceerd in AEM 6.3 en is de methode die wordt gebruikt door de AEM SJ SDK om apps van één pagina te hydreren. De [HTTP-API voor middelen](/help/assets/mac-api-assets.md) is een CRUD-API die is uitgebreid voor AEM 6.5.

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
* Verenigde inzichten gedreven door de integratie van Adobe Analytics in de Speler van de AEM Screens

Voor meer informatie over veranderingen in AEM Screens - zie de Nota&#39;s van de Versie in de Gids [van de Gebruiker van](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/aem-screens-introduction.html)AEM Screens.

### Experience Manager Assets {#experience-manager-assets}

Volledige lijst met wijzigingen in [AEM 6.5 Assets release notes](/help/release-notes/assets.md).

AEM 6.5 introduceert de volgende mogelijkheden en verbeteringen om de productiviteit van AEM gebruikers, rollen DAM, en bijbehorende creatieve en marketing rollen te verhogen.

#### Integration with Adobe Creative Cloud {#integration-with-adobe-creative-cloud}

Dankzij de introductie van [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html), een &#39;in-app&#39;-ervaring voor creatieve gebruikers die werken in Adobe Creative Cloud-toepassingen, zoals Photoshop, Illustrator en InDesign, wordt de samenwerking tussen ontwerpers en marketers bij het maken van inhoud gestroomlijnd. De AEM-bureaubladtoepassing blijft de behoeften ondersteunen van gebruikers die met middelen van AEM op desktopcomputers werken, met elk bestandstype en elke bureaubladtoepassing.

Bovendien integreert AEM met Adobe Stock om direct van de UI van het Web van AEM het vinden, voorproef, vergunning te geven en te bewaren van de Voorraad van Adobe.

![Het deelvenster Elementen koppelen in Photoshop](/help/assets/assets/aem65-assetlink-photoshop.png)

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

### Adobe Experience Manager Forms {#experience-manager-forms}

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

### Experience Manager Communities {#communitiesreleasenotes}

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

### Experience Manager Livefyre {#experience-manager-livefyre}

U kunt Livefyre met uw AEM 6.5 instantie integreren. Hier vindt u informatie over de integratie van Livefyre in AEM:

* [Integratie van Livefyre](https://helpx.adobe.com/experience-manager/6-4/help/sites-administering/livefyre.html)

### Gebruik klantgerichte ontwikkeling {#leverage-customer-focused-development}

Adobe gebruikt een klantgericht ontwikkelingsmodel dat klanten toestaat om aan alle stadia van het ontwikkelingsproces, tijdens specificatie, ontwikkeling en het testen bij te dragen. Onze dank gaat uit naar alle klanten en partners die een bijdrage leveren aan dit proces.

Adobe beschikt over de procedures en processen om verzameling, prioritering en tracering van de klantgerichte oplossing van problemen en ontwikkeling van verbeteringsverzoeken mogelijk te maken. Het ondersteuningsportal [voor](https://helpx.adobe.com/marketing-cloud/contact-support.html) Adobe Marketingen Cloud is geïntegreerd met het Adobe-systeem voor verbetering en foutopsporing. Vragen van de klant worden waar mogelijk met de klantenservice geïdentificeerd en opgelost. Bij doorverwijzing naar O&amp;O wordt alle klantinformatie vastgelegd en gebruikt voor prioritering en rapportage. Prioriteit wordt gegeven in ontwikkeling aan betaalde steun en garantiekwesties en betaalde klantenverhogingen.

Dit proces van prioritering heeft meer dan 750 klantgerichte veranderingen opgeleverd die in AEM 6.5 worden bevestigd.

## Lijst met bestanden die deel uitmaken van de release {#list-of-files-that-are-part-of-the-release}

**Stichting**

* Standalone QuickStart: cq-quickstart-6.5.0.jar
* Quickstart toepassingsserver: cq-quickstart-6.5.0.war
* Dispatcher 4.3.2 of hoger voor de verschillende webservers en -platforms ([downloadkoppeling](https://helpx.adobe.com/experience-manager/dispatcher/release-notes.html))
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

**Formulieren**

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

Experience Manager 6.5 is gecertificeerd voor GB18030-2005 CITS om de Chinese coderingsstandaard te gebruiken.

## Installeren en bijwerken {#install-update}

Zie [installatieinstructies](/help/sites-deploying/custom-standalone-install.md) voor installatievereisten.

Zie de [upgradedocumentatie](/help/sites-deploying/upgrade.md) voor gedetailleerde instructies.

## Ondersteunde Platforms {#supported-platforms}

Hier vindt u de volledige matrix met ondersteunde platforms, inclusief. Support op het niveau van technische [AEM 6.5-vereisten](/help/sites-deploying/technical-requirements.md)

Oak MicroKernel forOak MicroKernel for

>[!NOTE]
>
>Oracle is overgestapt op een LTS-model (Long Term Support) voor Oracle Java SE-producten. Java 9 en 10 zijn niet-LTS-versies van Oracle (zie [Oracle Java SE-supportroutekaart](https://www.oracle.com/technetwork/java/eol-135779.html)). Adobe biedt alleen ondersteuning voor LTS-releases van Java om AEM in productie te kunnen uitvoeren. Daarom is Java 11 de aanbevolen versie voor gebruik met AEM 6.5.

## Verouderde en verwijderde functies {#deprecated-and-removed-features}

Adobe evalueert voortdurend de mogelijkheden in het product en is van plan om in de loop der tijd de mogelijkheden te vervangen door krachtigere versies, of besluit om geselecteerde onderdelen opnieuw te implementeren om beter voorbereid te zijn op toekomstige verwachtingen of uitbreidingen.

Voor Adobe Experience Manager 6.5, [lees de lijst van afgekeurde en verwijderde mogelijkheden](/help/release-notes/deprecated-removed-features.md). De pagina bevat ook een vooraankondiging van wijzigingen in de nabije toekomst en belangrijke kennisgeving voor klanten die een update uitvoeren van eerdere releases.

## Bekende problemen {#known-issues}

[Lijst met bekende problemen](/help/release-notes/known-issues.md)

### Productdownload en -ondersteuning (beperkt aantal sites) {#product-download-and-support-restricted-sites}

Deze sites zijn alleen beschikbaar voor klanten. Neem contact op met uw accountmanager van Adobe als u een klant bent en toegang nodig hebt.

* [](https://daycare.day.com) [Product downloaden op licensing.adobe.com](https://licensing.adobe.com/)

* [Klantenondersteuning op de dag van de zorg.dag.com](https://daycare.day.com)

