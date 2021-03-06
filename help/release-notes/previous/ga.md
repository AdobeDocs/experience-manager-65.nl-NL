---
title: Algemene opmerkingen bij de release [!DNL Adobe Experience Manager] 6,5
description: '"[!DNL Adobe Experience Manager] 6.5 notities waarin de releasegegevens, de nieuwe functies, de installatie en gedetailleerde lijsten met wijzigingen worden beschreven."'
source-git-commit: e24316cb9495a552960ae0620e4198f10a08b691
workflow-type: tm+mt
source-wordcount: '4696'
ht-degree: 1%

---

# Algemene opmerkingen bij de release [!DNL Adobe Experience Manager] 6,5{#general-release-notes-for-adobe-experience-manager}

## Geen informatie {#release-information}

| Product | [!DNL Adobe Experience Manager] |
|---|---|
| Versie | 6,5 |
| Type | Grote release |
| Algemene beschikbaarheidsdatum | 8 april 2019 |
| Aanbevolen updates | Zie [Recente updates AEM](https://helpx.adobe.com/experience-manager/aem-releases-updates.html). |

### Trivia {#trivia}

De releasecyclus voor deze versie van [!DNL Adobe Experience Manager] begon op 4 april 2018, doorliep 23 versies van kwaliteitsborging en het corrigeren van fouten en eindigde op 28 maart 2019. Het totale aantal klantgerelateerde problemen, inclusief verbeteringen en nieuwe functies die in deze release zijn opgelost, is 1345.

[!DNL Adobe Experience Manager] 6.5 is over het algemeen beschikbaar sinds 8 april 2019.

![AEM 6.5 Aanmeldingsscherm](/help/assets/assets/aem65-login-v4.png)

## Wat is er nieuw? {#what-s-new}

[!DNL Adobe Experience Manager] 6.5 is een verbeteringsversie aan [!DNL Adobe Experience Manager] 6.4 basis van de code. Het verstrekt nieuwe en verbeterde functionaliteit, zeer belangrijke klantenmoeilijke situaties, de verhogingen van de hoge prioriteit van de klant en algemene insectenmoeilijke situaties die op productstabilisatie gericht zijn. Het omvat ook [!DNL Adobe Experience Manager] 6.4 Service Pack versies tot SP4.

De onderstaande lijst biedt een overzicht, terwijl op de volgende pagina&#39;s alle details worden weergegeven.

### [!DNL Experience Manager Foundation] {#experience-manager-foundation}

Het platform van [!DNL Adobe Experience Manager] 6.5 bouwen voort op de bijgewerkte versies van het op OSGi gebaseerde framework (Apache Sling en Apache Felix) en de Java Content Repository: Apache Jackrabbit Oak 1.10.2.

De QuickStart gebruikt Eclipse Jetty 9.4.15 als servlet-engine.

#### Java-ondersteuning  {#java-support}

* Nieuwe ondersteuning voor Java 11 en de reeds ondersteunde Java 8.
* Overschrijf voor optimale prestaties de standaard GC-waarden met andere waarden. Zie voor meer informatie de [installeren en bijwerken](/help/sites-deploying/custom-standalone-install.md) sectie.
* Java 11- en Java 8-onderhoudsupdates worden door Adobe gedistribueerd voor gebruik door klanten in AEM gerelateerde projecten, wanneer deze niet openbaar beschikbaar zijn vanuit Oracle.

#### Java Development {#java-development}

* Er is nu [twee versies van de Uberjar](/help/sites-developing/ht-projects-maven.md#experience-manager-api-dependencies), een geadviseerde versie met openbare interfaces die niet duidelijk voor afschrijving zijn, evenals een versie die interfaces duidelijk voor afschrijving omvat.

#### Gebruikersinterface {#user-interface}

Er zijn verschillende verbeteringen aangebracht in de interface om deze productiever en gebruiksvriendelijker te maken.

* Nieuwe interface voor machtigingenbeheer voor gebruikers en groepen.
* Met Kolomweergaven worden nu ook alleen items geladen die zichtbaar zijn op het scherm en worden alleen meer items geladen wanneer de gebruiker begint met schuiven. De lijst- en kaartweergave heeft dat al gedaan sinds 6.0 (verbeterd in 6.4).
* Kolomweergaven bevatten nu, indien van toepassing, de workflowstatus voor pagina&#39;s/middelen.
* De [Alles selecteren](/help/sites-authoring/basic-handling.md#select-all) Deze handeling is een snelle manier om een handeling uit te voeren met alle pagina&#39;s/middelen in dezelfde map.
* De [Alles selecteren](/help/sites-authoring/basic-handling.md#select-all) handeling probeert de handeling uit te voeren naar alle pagina&#39;s/elementen, niet alleen naar wat is geladen. Er wordt een waarschuwingsvenster weergegeven als de handeling niet is bijgewerkt om Bulk-handelingen af te handelen.

>[!CAUTION]
>
>Adobe is niet van plan om verdere verhogingen aan Klassieke UI te maken. AEM 6.5 heeft de klassieke gebruikersinterface inbegrepen, en klanten die van vroegere versies bevorderen kunnen het blijven gebruiken zoals is. Merk op dat Klassieke UI volledig wordt gesteund terwijl wordt afgekeurd. [Meer informatie](/help/sites-deploying/ui-recommendations.md).

#### Zoeken en indexeren {#indexing-and-search}

* Zoeken in eiken ondersteunt nu dynamische facetten. Zo toont de filterrail in de zoekopdracht naar elementen de geschatte hoeveelheid resultaten.
* QueryBuilder is uitgebreid om resultaten met dynamische facetten te bieden.

#### Upgrade {#upgrade}

* Directe upgrade naar AEM 6.5 wordt ondersteund voor klanten die AEM 6.2, 6.3 en 6.4 uitvoeren. Klanten die 5.x of 6.0/6.1 gebruiken die op zijn plaats verbetering willen gebruiken moeten eerst aan 6.4 bevorderen - en dan aan 6.5 bevorderen, of via overdracht van de inhoud tussen de instanties rechtstreeks aan AEM 6.5 bevorderen.
* De upgradeprocedure blijft grotendeels dezelfde in paragraaf 6.5.
* We blijven de functies Achterwaartse compatibiliteit, Complexiteitsbeoordeling upgraden en Duurzame upgrades ondersteunen die in 6.4 zijn ge??ntroduceerd. Waar nodig zijn op deze gebieden versiespecifieke wijzigingen aangebracht.
* Het verpakken van de Detector van het Patroon is vereenvoudigd, en er zal ????n pakket zijn die verbeteringen aan 6.5 voor de beschikbare bronversies evalueren.
* Voor details over verbeteringsprocedure, zie [upgradedocumentatie](/help/sites-deploying/upgrade.md).

#### Projecten en workflows {#projects-and-workflows}

* De nieuwe die redacteur van het Model van het Werkschema in 6.4 wordt ge??ntroduceerd is verbeterd om meer verrichtingen zoals Exemplaar en Publiceren, veranderlijke steun in de stappen van het Werkschema en verbeterd op te nemen `OR` en `AND` splitsen.

#### Bewaarplaats {#repository}

* De basis voor Adobe Experience Manager 6.5 is gebaseerd op de bijgewerkte versies van het op OSGi gebaseerde framework (Apache Sling en Apache Felix) en de Java Content Repository: Apache Jackrabbit Oak 1.10.2.
* Voor een overzicht van de vaste problemen raadpleegt u [Apache Jackrabbit Oak Jira v. 1.10.0](https://archive.apache.org/dist/jackrabbit/oak/1.10.0/RELEASE-NOTES.txt), [Apache Jackrabbit Oak Jira v. 1.10.1](https://archive.apache.org/dist/jackrabbit/oak/1.10.1/RELEASE-NOTES.txt) en [Apache Jackrabbit Oak Jira v. 1.10.2](https://archive.apache.org/dist/jackrabbit/oak/1.10.2/RELEASE-NOTES.txt).

>[!CAUTION]
>
>De nieuwe versie van de Oak Segment Tar aanwezig sinds AEM 6.3 vereist een repository migratie. Deze stap is verplicht als u een upgrade uitvoert van een oudere versie van TarMK of als u de nieuwe segmentmarkering wilt overschakelen van een ander type persistentie. Voor meer informatie over wat de voordelen van het nieuwe Segment Tar zijn, zie [Veelgestelde vragen over migreren naar eikensegment](/help/sites-deploying/revision-cleanup.md#migrating-to-oak-segment-tar).

#### OSGI {#osgi}

* Toegevoegde OSGi Promises en de nutsbibliotheken van de Converter.

#### Beveiliging {#security}

* Vervaldatum wachtwoord toegevoegd voor gebruiker van beheerder.

#### Webserver {#web-server}

* Bij de distributie van QuickStart wordt Eclipse Jetty 9.4.15 gebruikt als servletengine (AEM 6.4 geleverd bij 9.3.22).

### [!DNL Experience Manager] Sites {#experience-manager-sites}

#### Beheerde apps met ????n pagina {#managed-single-page-apps}

De paginabewerker voegt de mogelijkheid toe om inhoud in context te bewerken en samen te stellen/op te maken in ervaringen die op de client worden weergegeven (ook bekend) [als SPA Editor](/help/sites-developing/spa-architecture.md)). Bestaande apps van ????n pagina die worden gemaakt met JavaScript-framework React of Angular kunnen worden uitgebreid met de AEM SDK van SJ om bewerkbaar te maken voor professionals.

De eerste verscheepte als deel van AEM 6.4 SP2, met AEM 6.5 de SPA steun krijgt volgende mogelijkheden:

* De Redacteur van het Malplaatje van het gebruik om de AEM editable delen van de SPA uit te geven en te vormen
* Met beheer op meerdere locaties kunt u ervaringen met landspecifieke, franchise- of witgelabelde SPA cre??ren

#### Beheer van inhoud zonder hoofd {#headless-content-management}

AEM heeft de mogelijkheid om de inhoud in verschillende indelingen en op verschillende niveaus van de stapel te bedienen. Sommige zijn sinds 2008 met de [Sling GET](https://sling.apache.org/documentation/bundles/rendering-content-default-get-servlets.html) en [POST Servlet](https://sling.apache.org/documentation/bundles/manipulating-content-the-slingpostservlet-servlets-post.html). Inhoudsservices ([Verkoopmodel exporteren](https://docs.adobe.com/content/help/en/experience-manager-learn/foundation/development/develop-sling-model-exporter.html)) is ge??ntroduceerd in AEM 6.3 en is de methode die wordt gebruikt door de AEM SJ SDK voor het hydreren van apps van ????n pagina. De [HTTP-API voor middelen](/help/assets/mac-api-assets.md) is een CRUD API, die is uitgebreid voor AEM 6.5.

Nieuwe HTTP API-mogelijkheden:

* Toegevoegd [Ondersteuning van inhoudsfragmenten voor HTTP API voor middelen](/help/assets/assets-api-content-fragments.md) om fragmenten te maken, bij te werken, te lezen en te verwijderen.
* Maak lijsten van Inhoudsfragmenten via de Diensten van de Inhoud bloot [Kern van inhoudsfragmentlijst](https://opensource.adobe.com/aem-core-wcm-components/library/content-fragment-list.html).
* [Core Component Library](https://opensource.adobe.com/aem-core-wcm-components/library.html) dat de standaardoutput van de Diensten JSON van de Inhoud voor elke component toont

#### Scherminvoegtoepassing {#screens-add-on}

Effici??nt ontwerpen, leveren en optimaliseren ervaringen op alle digitale schermen, van interactieve kiosken tot digitale signage.

* Ervaringen en inhoud op digitale en in-store gelijktrekken met verbeterd hergebruik van inhoud
* Gestroomlijnde workflows voor schrijven en goedkeuren/publiceren met ondersteuning voor Starts
* Rijke interactieve ervaringen bewerken en leveren met SPA Editor
* Using Launches to plan future content changes for signage content
* Metered playback in een opeenvolgingskanaal
* Automatisch een projectstructuur maken met een bronbestand, zoals een Excel-werkblad
* Uitgebreide ondersteuning voor mediaspelers met robuuste online en offline bediening (Smart Sync) die kan worden geschaald naar zelfs de grootste signaalnetwerken.
* Personaliseer door plaats of configuratie van gegevens teweeggebrachte inhoud door dynamische placeholders te gebruiken.
* Verenigde inzichten gedreven door de integratie van Adobe Analytics in AEM Screens Player

Voor meer informatie over wijzigingen in AEM Screens raadpleegt u de opmerkingen bij de release in het dialoogvenster [AEM Screens-gebruikershandleiding](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/aem-screens-introduction.html).

#### Component- en sjabloonontwikkeling {#component-amp-template-development}

* Maven Project Archetype 18+ voor nieuwe projecten, zie [Github voor opmerkingen bij de release](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype/releases).
* App Maven Project Archetype 1.0.6+ van ????n pagina voor nieuwe projecten, zie [Github voor opmerkingen bij de release](https://github.com/adobe/aem-spa-project-archetype/releases).
* HTML versie 1.4, zie [Github voor opmerkingen bij de release](https://github.com/adobe/htl-spec/releases/tag/1.4).

   * operator &quot;in&quot; voor tekenreeksen, arrays en objecten:

      ```html
      ${'a' in 'abc???}
      ${100 in myArray}
      ${'a' in myObject}
      ```

   * Declaraties van variabelen met subset van gegevens:
      `<sly data-sly-set.title="${currentPage.title}"/>${title}`

   * Controleparameters weergeven en herhalen: begin, stap, einde:
      `<h2 data-sly-repeat="${currentPage.listChildren @ begin = 1, step=2}">${item.title}</h2>`

   * Id&#39;s voor terugloop van gegevensdoorhaling:

      ```html
      <div data-sly-unwrap.isUnwrapped="${myCondition || myOtherCondition}">
      text <span data-sly-test="${isUnwrapped}>is unwrapped</code>
      </div>
      ```

   * Ondersteuning voor negatieve getallen

* Core Components 2.3.2+, zie [Github voor opmerkingen bij de release](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/releases).
* Rastersysteem voor lay-outcontainer, zie [Github](https://github.com/Adobe-Marketing-Cloud/aem-responsivegrid).
* Clientlib Manager: Google Closure Compiler standaard ingesteld op minificatie van JavaScript-clientlibs (de oude standaard was Yahoo YUI) en Google Closure Compiler bijgewerkt naar versie v20190121
* Sjablooneditor en beleidsregels

   * Sjablonen maken en bewerken voor apps van ????n pagina die de JS SDK gebruiken (ook wel SPA Editor genoemd)

* Referentie Site We.Retail 4.0, zie [Github voor opmerkingen bij de release](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/releases).
* Toolkit om bestaande sites te upgraden zodat de nieuwste editormogelijkheden worden benut, raadpleegt u [Github-opslagplaats](https://github.com/adobe/aem-modernize-tools)

>[!CAUTION]
>
>AEM bevat versie 1.12.4 van de jQuery-bibliotheek voor maximale compatibiliteit met bestaande aangepaste code. Adobe heeft wijzigingen aangebracht om bekende beveiligingsproblemen aan te pakken.

#### Sitebeheer {#site-administration}

* De [Referentie](/help/sites-authoring/author-environment-tools.md#references) rail heeft een nieuwe sectie om interne verbindingen te vermelden die aan de geselecteerde pagina richten. Dit is handig wanneer u een pagina offline of verwijderd wilt maken. Zo kunt u zien welke pagina&#39;s moeten worden aangepast voordat u de pagina&#39;s offline plaatst.
* De [lijstweergave](/help/sites-authoring/basic-handling.md#list-view) heeft een nieuwe werkstroomkolom die de status toont wanneer de pagina momenteel in een werkschema is.
* In de [pagina-eigenschappen](/help/sites-authoring/editing-page-properties.md)kunt u nu bladeren naar bestaande elementen wanneer u een miniatuur aan de pagina toewijst (tabblad Miniatuur).

#### Pagina-editor {#page-editor}

* In-context bewerken en samenstellen van app-ervaringen van ????n pagina toestaan die zijn opgebouwd met React en Angular-clientcomponenten die gebruikmaken van de JS SDK (ook wel SPA Editor genoemd)
* De modus Basisstructuur wordt alleen weergegeven als op de pagina een basispagina is geconfigureerd.

#### Inhoudsfragmenten en -editor {#content-fragments-amp-editor}

* Nieuw [Annotaties](/help/assets/content-fragments/content-fragments-variations.md#viewing-editing-deleting-annotations) rail in de Inhoudsfragmenteditor om algemene opmerkingen te maken en opmerkingen in de tekst te bekijken (ook weergegeven in de tijdlijntrack)
* Mogelijkheid om het standaard inhoudstype van een tekstelement met meerdere regels in te stellen in een [Inhoudsfragmentmodel](/help/assets/content-fragments/content-fragments-models.md) naar eenvoudige tekst, tekst met opmaak of markeringen
* Toevoegen [opmerking/annotaties](/help/assets/content-fragments/content-fragments-variations.md#annotating-a-content-fragment) door tekst in RTE (volledig-schermmening) te selecteren
* [Versies vergelijken](/help/assets/content-fragments/content-fragments-managing.md#comparing-fragment-versions) van een inhoudsfragment naast elkaar via referentieslegel
* In het rapport Downloaden van middelen worden nu inhoudsfragmenten dienovereenkomstig weergegeven
* Toevoegen [Ondersteuning voor inhoudsfragmenten op HTTP-API voor middelen](/help/assets/assets-api-content-fragments.md) via /api.json. Er zijn API&#39;s voor het maken, bijwerken, lezen en verwijderen van inhoudsfragmenten.

#### Ervaringsfragmenten {#experience-fragments}

* Verbeterde indexering van [Ervaar fragmenten](/help/sites-authoring/experience-fragments.md), zodat de inhoud ervan wordt gevonden in zoekopdrachten naar pagina&#39;s waar ze worden gebruikt
* De [Exporteren naar doel](/help/sites-administering/experience-fragments-target.md) kunt u nu het ervaringsfragment verzenden als JSON (standaard is HTML) of beide

#### Vertaling {#translation}

* Vereenvoudig het cre??ren van OmzettingsProjecten door de Stramienen van het Project te gebruiken
* Vereenvoudig het uitvoeren van vertaalprojecten door vertaalbanen aan goedgekeurde status door gebrek te plaatsen
* Het bijwerken van vertaalde pagina&#39;s met wijzigingen in het vertaalgeheugen van derden toestaan
* Vertaaltaken in JSON-indeling exporteren toestaan
* Microsoft-vertalingsintegratie bijwerken voor gebruik van de V3-API

#### Multisite beheer (MSM) {#multi-site-management-msm}

* Voor roll-out vormen die PushOnModify gebruiken, betere behandeling van pagina bewegingsverrichting om inconsistente staat te vermijden
* Als u een nieuwe pagina maakt in de bibliotheekstructuur, wordt standaard een zelfstandige pagina gemaakt
* Gebruik MSM-functies in apps van ????n pagina die de JS SDK gebruiken (ook wel SPA Editor genoemd)

#### Lanceringen {#launches}

* Nieuwe revisie- en goedkeuringswerkstroom voor introducties en de mogelijkheid om alleen goedgekeurde startpagina&#39;s te promoten
* Toegevoegd [optie in UI om te verkiezen om de Lancering recht na de bevorderingsstap te schrappen](/help/sites-authoring/launches-promoting.md#promoting-launch-pages)

#### Inhoud richten en simuleren {#content-targeting-simulation}

* De de gegevenslaag van ContextHub en cli??nt-zijregelingsmotor JavaScript is bijgewerkt om jQuery 3 door gebrek te gebruiken.

#### AEM en Adobe Target {#aem-amp-adobe-target}

>[!CAUTION]
>
>Momenteel:
>
>* Alleen `at.js 1.x` wordt ondersteund als u Adobe Target gebruikt als de doelengine in AEM Activiteiten-console.
>
>* Both `at.js. 1.x` and `at.js 2.x` are supported if you are using Experience Fragment export to Target and running Activities within Target&#39;s console.


* Adobe Target integration is can now use the Target Standard API. Eerdere versies van AEM gebruiken de Classic HTTP-API van Target, die nu is afgekeurd.
* Adobe Target `mbox.js` versie 63 is opgenomen. Adobe beveelt ten zeerste aan om over te schakelen op `at.js` v1.x.
* `at.js` versie 1.5.0 is nu inbegrepen. Adobe raadt u aan [Adobe Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) aan `at.js` v1.x naar de site.

#### AEM en Adobe Analytics {#aem-amp-adobe-analytics}

* `s_code.js` H.27.5 is inbegrepen. Adobe raadt u aan over te schakelen op `AppMeasurement.js`
* `AppMeasurement.js` v1.8.0 is inbegrepen. Adobe raadt u aan [Adobe Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) om AppMeasurement.js op de site te plaatsen.

#### AEM en handel {#aem-commerce}

De verbeteringen aan het Kader van de Integratie van de Handel zijn op een snellere versiecyclus sinds AEM 6.4. [Meer informatie hier](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/docs.html).

#### Invoegtoepassing Gemeenschappen {#communities-add-on}

Voor de nieuwste release raadpleegt u de [Gemeenschappen inzetten](/help/communities/deploy-communities.md) van de documentatie.

##### Verbeteringen van de betrokkenheid van de gemeenschap {#enhancements-to-community-engagement}

**@Misions-ondersteuning**
In AEM Communities kunnen geregistreerde gebruikers nu tags toewijzen (andere geregistreerde leden vermelden) om hun aandacht te vestigen op door gebruikers gegenereerde inhoud. De gelabelde (vermelde) leden worden vervolgens op de hoogte gesteld, met een diepe koppeling naar de overeenkomstige door de gebruiker gegenereerde inhoud. Gebruikers kunnen er echter voor kiezen om het web- en e-mailbericht uit te schakelen of in te schakelen.

![Op de vergadering](/help/release-notes/assets/at-mentions.png)

De gebruikers van de Gemeenschap hoeven niet naar hun voornaam, familienaam, of gebruikersnaam te zoeken om te zien of heeft iemand uit aan hen bereikt of hun aandacht nodig. Bovendien kunnen UGC-auteurs reacties vragen bij specifieke geregistreerde gebruikers die het probleem het beste kunnen oplossen en invoer kunnen toevoegen.

De gemeenschapsbeheerders moeten **Menu inschakelen** op communautaire componenten om geregistreerde gebruikers toe te staan de functionaliteit op die componenten te gebruiken.

**Groepsberichten**

Geregistreerde leden van de community kunnen nu bulksgewijs directe berichten naar groepen verzenden via ????n e-mailcompositie, in plaats van hetzelfde bericht afzonderlijk naar groepsleden te verzenden. Om toe te staan [groepsberichten](/help/communities/configure-messaging.md), beide instanties van [Service voor berichtenverkeer](/help/communities/messaging.md#group-messaging).

![Groepsbericht](/help/release-notes/assets/group-messaging.png)

##### Verbeteringen voor Bulk Moderation {#enhancements-to-bulk-moderation}

Aangepaste filters in Bulk Moderatie

[Aangepaste filters](/help/communities/moderation.md#custom-filters) kan nu worden ontwikkeld en aan BulkModeration UI worden toegevoegd.

A [voorbeeldproject](https://github.com/Adobe-Marketing-Cloud/aem-communities-extensions/tree/master/aem-communities-moderation-filter) filteren via tags kan worden aangetoond in [Github](https://github.com/Adobe-Marketing-Cloud/aem-communities-extensions/tree/master/aem-communities-moderation-filter). Dit project kan als basis worden gebruikt om analoge douanefilters te ontwikkelen.

![Aangepaste filters](/help/release-notes/assets/custom-tag-filter.png)

**Lijstweergave in bulkmodernisering**

De nieuwe Mening van de Lijst met betere UI is verstrekt in bulkmoderatie om Gebruiker te tonen Gegenereerde Inhoudsingangen.

![Modernisering van de lijst](/help/release-notes/assets/list-view-moderation.png)

##### Verbeteringen voor site- en groepsbeheer {#enhancements-to-site-and-group-management}

**Site- en groepsbeheerders van auteurs**

Gemeenschappen, AEM 6.5 en hoger, maken gedecentraliseerd beheer (en beheer) van verschillende gemeenschapssites en groepen/geneste groepen mogelijk. Organisaties die meerdere communitysites en geneste groepen hosten, kunnen nu leden selecteren voor beheerdersrollen aan de Auteur op het moment dat de site (en groep) wordt gemaakt.

![Sitebeheerder](/help/release-notes/assets/site-admin.png)

Sitebeheerders kunnen een groep op elk hi??rarchisch niveau maken en de standaardbeheerders worden. Deze beheerders kunnen later door andere groepbeheerders worden verwijderd. De beheerders van de groep kunnen hun groep G1 beheren en tot een subgroep leiden die onder G1 wordt genest.

##### Verbeteringen op gebied van activering {#enhancements-to-enablement}

**Ondersteuning voor SCORM 2017.1**

De enablement-functionaliteit van AEM 6.5 Communities ondersteunt Shareable Content Object Reference Model [(SCORM) 2017.1](https://rusticisoftware.com/blog/scorm-engine-2017-released/) motor.

* Ondersteuning voor toetsenbordnavigatie op schakelingscomponenten
* De componenten van Enablement (bijvoorbeeld Catalog en Course die spelen, Toewijzingen, de Bibliotheek van het Dossier) in AEM Communities steunen toetsenbordnavigatie voor betere toegankelijkheid.

##### Andere verbeteringen {#other-enhancements}

* Solr 7-ondersteuning
* AEM 6.5 Community&#39;s ondersteunen Apache Solr 7.0-versie van het zoekplatform bij het opzetten van MSRP en DSRP.

### [!DNL Experience Manager Assets] {#experience-manager-assets}

AEM 6.5 introduceert de volgende mogelijkheden en verbeteringen om de productiviteit van AEM gebruikers, DAM-rollen en de bijbehorende creatieve en marketingrollen te verhogen.

#### Integratie met [!DNL Adobe Creative Cloud] en creatieve workflows {#integration-with-adobe-creative-cloud-and-creative-workflows}

[!DNL Adobe Experience Manager] biedt verschillende manieren om mee te integreren [!DNL Adobe Creative Cloud] en delen van middelen voor gebruik in werkstromen waar de creatieve en marketing- of bedrijfsteams nauw samenwerken. [!DNL Experience Manager] 6.5 De integratie blijft verbeteren en wordt verder gestroomlijnd om meer kansen te cre??ren en de bestaande methoden te stroomlijnen.

Lees verder om de specifieke mogelijkheden en integratie van [!DNL Experience Manager] 6.5 die u kunt gebruiken om de gebruiksscenario&#39;s van de inhoudssnelheid het best te ondersteunen.

##### Adobe-itemkoppeling {#aal}

[!DNL Adobe Asset Link] versterkt de samenwerking tussen creatieve en marketingmedewerkers bij het maken van inhoud. Creatieven hebben toegang tot inhoud die is opgeslagen in [!DNL Experience Manager Assets], zonder de toepassingen te verlaten die ze het meest kennen. Met het deelvenster in de app in kunt u op een naadloze manier door middelen bladeren, zoeken, uitchecken en inchecken [!DNL Adobe Photoshop], [!DNL Adobe Illustrator], en [!DNL Adobe InDesign] apps.

[!DNL Adobe Asset Link] maakt deel uit van [Creative Cloud voor bedrijven](https://www.adobe.com/creativecloud/business/enterprise.html) aanbieden. Voor meer informatie over het, met inbegrip van noodzakelijke configuratie van uw [!DNL Experience Manager] implementatie, zie [Adobe-itemkoppeling](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html).

![Middelen zoeken in Adobe Photoshop](/help/release-notes/assets/asset_search_photoshop.png)

##### [!DNL Adobe Stock] integratie {#stock}

Uw organisatie kan [!DNL Adobe Stock] ondernemingsplan binnen [!DNL Experience Manager Assets] om ervoor te zorgen dat gelicentieerde activa algemeen beschikbaar zijn voor uw creatieve en marketing projecten. U kunt snel zoeken, voorvertonen en licenties maken [!DNL Adobe Stock] middelen die in Experience Manager worden bewaard, die de krachtige mogelijkheden DAM van [!DNL Experience Manager].

[!DNL Adobe Stock] biedt ontwerpers en bedrijven toegang tot miljoenen kwalitatief hoogstaande, gekrulde, royaltyvrije foto&#39;s, vectoren, illustraties, video&#39;s, sjablonen en 3D-middelen voor al hun creatieve projecten.

Zie voor meer informatie [Adobe Stock-middelen gebruiken in Experience Manager Assets](/help/assets/aem-assets-adobe-stock.md).

![Adobe Stock-afbeelding en -licentie voorvertonen vanuit Experience Manager Assets](/help/release-notes/assets/stock_image_preview_license_options.png)

*Afbeelding: Voorvertoning [!DNL Adobe Stock] image en licentie vanuit [!DNL Experience Manager Assets].*

![De gelicentieerde Adobe Stock-afbeeldingen zoeken en filteren in Experience Manager](/help/release-notes/assets/aem-search-filters2.jpg)

*Afbeelding: De licentie zoeken en filteren [!DNL Adobe Stock] afbeeldingen in [!DNL Experience Manager].*

##### Dynamische verwijzingen in [!DNL Adobe InDesign] {#dynamic-references-in-indesign}

[!DNL Experience Manager Assets] gebruikt in [!DNL Adobe InDesign] zijn dynamische bestanden. De verwijzingen worden automatisch bijgewerkt als de middelen waarnaar wordt verwezen in de bewaarplaats worden verplaatst. Zie voor meer informatie [hoe te om samengestelde activa te beheren](/help/assets/managing-linked-subassets.md).

#### Brand Portal-mogelijkheden {#brand-portal-capabilities}

[!DNL Experience Manager Assets Brand Portal] helpt u de goedgekeurde middelen eenvoudig te verwerven, effectief te controleren en veilig te distribueren aan externe leveranciers/agentschappen en interne zakelijke gebruikers over verschillende apparaten. Het helpt de effici??ntie van het delen van bedrijfsmiddelen te verbeteren, versnelt de tijd tot aan de markt voor bedrijfsmiddelen en voorkomt het risico van niet-conform gebruik en ongeoorloofde toegang.

Zie voor meer informatie [Nieuwe functies in Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/whats-new.html?lang=en).

#### Gekoppelde assets {#connectedassets}

In grote ondernemingen kan de infrastructuur die nodig is om websites te maken, worden gedistribueerd. Soms bevinden de mogelijkheden voor het maken van websites en de vereiste digitale middelen zich in verschillende silo&#39;s.

[!DNL Experience Manager Sites] biedt functies voor het maken van webpagina&#39;s en is het DAM-systeem (Digital Asset Management) dat de vereiste assets voor websites levert. [!DNL Experience Manager Assets] [!DNL Experience Manager] ondersteunt nu het bovenstaande gebruiksgeval door integratie van [!DNL Sites] en [!DNL Assets]. Zie [hoe te om de Verbonden eigenschap van Activa te vormen en te gebruiken](/help/assets/use-assets-across-connected-assets-instances.md).

![Een element slepen vanuit een [!DNL Experience Manager] implementatie op een [!DNL Sites] pagina van een andere [!DNL Experience Manager] implementatie](/help/release-notes/assets/connected-assets-drag-and-drop-only.gif)

*Afbeelding: Een element slepen vanuit een [!DNL Experience Manager] implementatie op een [!DNL Sites] pagina op een andere pagina [!DNL Experience Manager] implementatie.*

####  Dynamic Media  {#dynamic-media}

[!DNL Dynamic Media] biedt verbeterde mogelijkheden voor het schrijven en leveren van rijke media in [!DNL Experience Manager Assets] om geavanceerde ervaringen te stimuleren die meeslepend en gepersonaliseerd zijn. Door ????n primair middel van hoge kwaliteit te uploaden en geavanceerde cloudrendering en viewers van hoge kwaliteit te gebruiken, kunt u elke combinatie van uitvoeringen ter plekke aanbieden ter ondersteuning van de mediastrategie van uw organisatie.

Meer informatie over nieuwe [!DNL Dynamic Media] functies, zie [Opmerkingen bij de release van Dynamic Media](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/release-notes/s7rn2017.html).

##### 360 video-ondersteuning {#video-support}

Uw 360-videobestanden rechtstreeks beheren in [!DNL Experience Manager] de meest geavanceerde viewers gebruiken om VR-ervaringen te bieden aan desktops, mobiele apparaten en VR-headsets. Zie voor meer informatie [360-video gebruiken](/help/assets/360-video.md).

##### Aangepaste videominiaturen {#custom-video-thumbnails}

U kunt de miniaturen voor uw video-elementen nu aanpassen met frames uit de video zelf of andere inhoud die is opgeslagen in de DAM. Zie voor aanvullende instructies [Informatie over videominiaturen](/help/assets/video.md#about-video-thumbnails-in-dynamic-media-scene-mode).

##### Verbeteringen voor toegankelijkheid {#accessibility-enhancements}

[!DNL Dynamic Media] viewers bieden nu ondersteuning voor verbeterde toegankelijkheidsfuncties, zoals apparaatondersteuning, schermlezers en Alt-tekst. Zie voor meer informatie [Referentiehandleiding voor viewers](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/homeviewers.html).

#### Verbeterde zoekervaring {#experience-enhancement-for-searching}

[!DNL Experience Manager] Vanaf 6.5 kunnen marketers de gewenste middelen sneller vinden op de pagina met zoekresultaten. De zoekfacetten worden met het aantal elementen bijgewerkt, zelfs voordat het zoekfilter wordt toegepast. Door het verwachte aantal op het filter te zien, kunnen gebruikers effici??nt door de zoekresultaten navigeren. Zie voor meer informatie [Middelen zoeken in Experience Manager](/help/assets/search-assets.md).

![Het aantal elementen weergeven zonder zoekresultaten te filteren in zoekfacetten](/help/assets/assets/asset_search_results_in_facets_filters.png)

*Afbeelding: Zie het aantal elementen zonder zoekresultaten te filteren in zoekfacetten.*

#### Verbetering van bruikbaarheid {#usability-enhancement}

U kunt nu alle geladen elementen in een map selecteren of vanuit een zoekresultaat in ????n keer. Hiermee kunt u meerdere elementen snel beheren. Met het selectievakje selecteert u alle elementen die in het scenario passen, zoals een zoekresultaat, en niet alleen de elementen die in het venster [!DNL Experience Manager] interface.

![Met de optie Alles selecteren kunt u alle geladen elementen met ????n klik selecteren.](/help/release-notes/assets/select-all-in-aem-assets.gif)

*Afbeelding: Gebruik de optie Alles selecteren om alle geladen elementen met ????n klik te selecteren.*

#### Verbeteringen in metagegevens {#metadata-enhancements}

[!DNL Assets] Hiermee kunt u metagegevensschema&#39;s voor middelenmappen maken, waarmee de lay-out en de metagegevens worden gedefinieerd die op pagina&#39;s met mapeigenschappen worden weergegeven. U kunt nu een schema voor mapmetagegevens toewijzen aan een bestaande map of bij het maken van een map. Zie voor meer informatie [Metagegevensschema van map](/help/assets/metadata-config.md#folder-metadata-schema).

Als u trapsgewijze metagegevens opgeeft, kunnen de opties tijdens de runtime uit een JSON-bestand worden geladen, bijvoorbeeld in plaats van handmatig in het formulier te typen. Zie voor meer informatie [trapsgewijze metagegevens](/help/assets/metadata-schemas.md#cascading-metadata).

#### Verbeteringen rapporteren {#reporting-enhancements}

De Inhoudsfragmenten en de aandelen van de verbinding zijn nu inbegrepen in het gedownloade rapport. Zie voor meer informatie [Elementenrapporten](/help/assets/asset-reports.md).

### [!DNL Adobe Experience Manager Forms] {#experience-manager-forms}

AEM 6.5 Forms biedt verschillende nieuwe functies en verbeteringen. De hooglichten omvatten:

* Transactierapporten om het aantal ingediende formulieren, verwerkte documenten en gerenderde documenten bij te houden
* Verbeteringen in bruikbaarheid van interactieve communicatie
* Digitale handtekeningen op basis van cloud in adaptieve formulieren
* Aangepaste formulieren en interactieve communicatie insluiten in AEM Sites-toepassingen van ????n pagina (SPA).
* Ondersteuning voor variabelen in AEM Workflows
* Ondersteuning van gegevenspatronen in interactieve communicatie
* Aangepaste formulieren en interactieve communicatietabellen sorteren
* Geautomatiseerde validatie van invoergegevens in formuliergegevensmodellen

Zie de [Overzicht van nieuwe functies en verbeteringen in AEM 6.5 Forms](/help/forms/using/whats-new.md) voor informatie over nieuwe en verbeterde functies en documentatiebronnen.

### [!DNL Experience Manager Livefyre] {#experience-manager-livefyre}

U kunt Livefyre met uw AEM 6.5 instantie integreren. Zie [Hoe te om Livefyre met AEM te integreren](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/livefyre.html).

### Gebruik van klantgerichte ontwikkeling {#leverage-customer-focused-development}

Adobe gebruikt een klantgericht ontwikkelingsmodel dat klanten toestaat om aan alle stadia van het ontwikkelingsproces, tijdens specificatie, ontwikkeling en het testen bij te dragen. Onze dank gaat uit naar alle klanten en partners die een bijdrage leveren aan dit proces.

Adobe heeft de procedures en de processen op zijn plaats om inzameling, prioritering, en het volgen van klant gerichte insectenresolutie en de ontwikkeling van verbeteringsverzoeken toe te laten. De [Experience Manager Support-portal](https://experienceleague.adobe.com/?support-solution=Experience+Manager#support) is ge??ntegreerd met het Adobe-systeem voor verbetering en foutopsporing. De vragen van de klant worden ge??dentificeerd en opgelost door het team van de Steun van de Klant waar mogelijk. Bij doorverwijzing naar O&amp;O wordt alle klantinformatie vastgelegd en gebruikt voor prioritering en rapportage. Prioriteit wordt gegeven in ontwikkeling aan betaalde steun, garantiekwesties, en klant-betaalde verhogingen.

Dit proces van prioritering heeft meer dan 750 klantgerichte veranderingen opgeleverd die in AEM 6.5 worden bevestigd.

## Lijst met bestanden die deel uitmaken van de release {#list-of-files-that-are-part-of-the-release}

**Stichting**

* Standalone QuickStart: `cq-quickstart-6.5.0.jar`.
* Quickstart toepassingsserver: `cq-quickstart-6.5.0.war`.
* Dispatcher 4.3.2 of hoger voor de verschillende webservers en -platforms. Zie [downloadkoppeling](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/getting-started/release-notes.html)
* Plug-in voor Eclipse IDE ([meer lezen en downloaden](/help/sites-developing/aem-eclipse.md))

* Extension for Brackets Code Editor ([meer lezen en downloaden](/help/sites-developing/aem-brackets.md))
* Geweven/grijze afhankelijkheden ([downloadkoppeling](https://repo1.maven.org/maven2/com/adobe/aem/uber-jar/6.5.0/))

**Sites**

* Kerncomponenten ([GitHub-project](https://github.com/adobe/aem-core-wcm-components))
* We.Retail Reference Implementation ([meer lezen](/help/sites-developing/we-retail.md))
* Maven Project archetypes:

   * voor volledig-stapelsites: [GitHub-project](https://github.com/adobe/aem-project-archetype)
   * voor apps van ????n pagina met React/Angular: [GitHub-project](https://github.com/adobe/aem-spa-project-archetype)

* AEM Screens Players voor diverse doelplatforms ([downloaden](https://download.macromedia.com/screens/))

* Smart Content Language Models. Engels is vooraf ge??nstalleerd - meer talen kunnen worden gedownload

   * [Duits](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-de)
   * [Spaans](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-es)
   * [Italiaans](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-it)
   * [Frans](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-fr)

* AEM Tools Suite moderniseren, bijvoorbeeld Dialog Conversion Tool. ([GitHub-project](https://github.com/adobe/aem-modernize-tools))

**Assets**

* Pakket maken om verbeterde PDF Rasterizer toe te voegen ([meer lezen](/help/assets/aem-pdf-rasterizer.md))
* Pakket maken om uitgebreide ondersteuning voor RAW-afbeeldingen toe te voegen ([meer lezen](/help/assets/camera-raw.md))

**Forms**

* [Pakketten voor AEM Forms-mogelijkheden](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html)
* [AEM Forms OSGi Client SDK](https://repo1.maven.org/maven2/com/adobe/aemfd/aemfd-client-sdk/)

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

Voor opstellingsvereisten, zie [installatie-instructies](/help/sites-deploying/custom-standalone-install.md).

Zie voor gedetailleerde instructies [upgradedocumentatie](/help/sites-deploying/upgrade.md).

## Ondersteunde Platforms {#supported-platforms}

Zoek de volledige matrix van ondersteunde platforms, inclusief ondersteuning op [AEM 6.5 technische voorschriften](/help/sites-deploying/technical-requirements.md).

>[!NOTE]
>
>Oracle is overgestapt op een LTS-model (Long Term Support) voor Oracle Java SE-producten. Java 9 en 10 zijn niet-LTS versies door Oracle. Zie [Ondersteuning voor roadmap voor oracle Java SE](https://www.oracle.com/technetwork/java/eol-135779.html). Adobe biedt ondersteuning voor LTS-versies van Java, zodat alleen AEM in productie worden uitgevoerd. Java 11 is de aanbevolen versie voor gebruik met AEM 6.5.

## Verouderde en verwijderde functies {#deprecated-and-removed-features}

Adobe evalueert constant mogelijkheden in het product en in tijd plannen om mogelijkheden met krachtigere versies te vervangen, of besluit om geselecteerde delen opnieuw uit te voeren om beter voor toekomstige verwachtingen of uitbreidingen worden voorbereid.

Voor [!DNL Adobe Experience Manager] 6.5 [lees de lijst met afgekeurde en verwijderde mogelijkheden](/help/release-notes/deprecated-removed-features.md). De pagina bevat ook een vooraankondiging van wijzigingen in de nabije toekomst en belangrijke kennisgeving voor klanten die een update uitvoeren van eerdere releases.

## Bekende problemen {#known-issues}

### Platform {#platform}

* Er wordt een probleem gerapporteerd waarbij de CRX-Quickstart en de inhoud ervan worden verwijderd.

   Controleer bij elk van deze handelingen of de eigenschap `htmllibmanager.fileSystemOutputCacheLocation` is geen lege tekenreeks:

   1. Aanroepen `/libs/granite/ui/content/dumplibs.rebuild.html?invalidate=true`.
   2. Upgrade naar AEM 6.5.
   3. Uitvoeren van &quot;luie migratie van inhoud&quot; op AEM 6.5.

   A [Kennisbank](https://helpx.adobe.com/experience-manager/kb/avoid-crx-quickstart-deletion-in-aem-6-5.html) het artikel is beschikbaar met meer details en de oplossing voor deze kwestie .

* Als u JDK 11 met AEM 6.5 instantie gebruikt, zouden sommige pagina&#39;s als leeg kunnen tonen na het opstellen van sommige pakketten. Het volgende foutbericht wordt weergegeven in het logbestand:

   ```java
   *ERROR* [OsgiInstallerImpl] org.apache.sling.scripting.sightly bundle org.apache.sling.scripting.sightly:1.1.2.1_4_0 (558)[org.apache.sling.scripting.sightly.impl.engine.extension.use.JavaUseProvider(3345)] : Error during instantiation of the implementation object (java.lang.NoClassDefFoundError: jdk/internal/reflect/ConstructorAccessorImpl)
   java.lang.NoClassDefFoundError: jdk/internal/reflect/ConstructorAccessorImpl
   ```

Deze fout oplossen:

1. Stop de AEM instantie. Ga naar `<aem_server_path_on_server>crx-quickstart\conf` en opent u de `sling.properties` bestand. Adobe raadt u aan een back-up van dit bestand te maken.

1. Zoeken naar `org.osgi.framework.bootdelegation=`. Toevoegen `jdk.internal.reflect,jdk.internal.reflect.*` eigenschappen om het resultaat als weer te geven.

```java
org.osgi.framework.bootdelegation=sun.*,com.sun.*,jdk.internal.reflect,jdk.internal.reflect.*
```

1. Sla het bestand op en start de AEM opnieuw.

### Sites {#sites}

* **Werken met paginaversies**: [Als een pagina is verplaatst, kunt u geen voorvertoning meer weergeven van versies die zijn gemaakt voor de verplaatsing](/help/sites-authoring/working-with-page-versions.md#previewing-a-version).

### Assets {#assets}

* **Zoeken:** Er worden geen resultaten geretourneerd als de zoekreeks een of meer spaties ([OAK-4786](https://issues.apache.org/jira/browse/OAK-4786))
* **Metagegevensschema van map**: Nadat u een keuzerondje hebt toegevoegd, worden het veld Id en Waarde niet weergegeven zoals u had verwacht en werkt de verwijderfunctie niet. (CQ-4261144)
* Wanneer u de naam van een element wijzigt, is het niet mogelijk een witruimte in de elementnaam te gebruiken. (CQ-4266403)

### Forms {#forms}

* Als AEM Forms is ge??nstalleerd op Linux-besturingssystemen, werkt Digital Signature met Hardware Security Module niet. (CQ-4266721)
* (Alleen AEM Forms op WebSphere) De **Forms Workflow** > **Zoeken in taken** Deze optie geeft geen resultaat als u naar een **Beheerder** with **Gebruikersnaam** als de zoekcriteria. (CQ-4266457)

* AEM Forms converteert TIF- en TIFF-bestanden met JPEG-compressie niet naar PDF-documenten. (CQ-4265972)
* De **AEM Forms Assets Scanner** en **Letter to Interactive Communication Migration** de opties werken niet op de **AEM Forms-migratie** pagina. (CQ-4266572)

* (Alleen JBoss 7) Wanneer u een upgrade uitvoert van een vorige versie naar AEM 6.5 Forms en de vorige versie processen had (.lca) die een kopie van het standaard verzendproces of het standaard renderproces maakten en gebruikten, voert HTML5 Forms met dergelijke processen (.lca) de vereiste handelingen niet uit. (CQ-4243928)
* Wanneer een formuliergegevensmodelservice wordt aangeroepen vanuit de regeleditor om de waarden van de afbeeldingskeuzescomponent dynamisch bij te werken, worden de waarden van de afbeeldingskeuzeselectie niet bijgewerkt. (CQ-4254754)
* Voor het installatieprogramma van AEM Forms Designer is de 32-bits versie van [Visuele C++ redistributable runtime package 2012](https://support.microsoft.com/en-in/help/2977003/the-latest-supported-visual-c-downloads) en [Visuele C++ redistributable runtime pakketten 2013](https://support.microsoft.com/en-in/help/3179560/update-for-visual-c-2013-and-visual-c-redistributable-package). Zorg ervoor dat de hierboven vermelde herdistribueerbare runtimepakketten zijn ge??nstalleerd voordat u de installatie start. (CQ-4265668)

* PDF Generator ondersteunt geen verificatie op basis van smartcards.  Wanneer een beheerder het Beleid van de Groep toelaat `Interactive Logon: Require Smart card` op een Windows-server worden alle bestaande PDF Generator-gebruikers ongeldig gemaakt.

* Wanneer een adaptief formulier is geconfigureerd om de waarden van een component dynamisch bij te werken en het publicatie-exemplaar dat als host fungeert voor het formulier via de verzender, werkt de functionaliteit voor het dynamisch bijwerken van waarden van een veld niet meer. Als u het probleem wilt oplossen, opent u CRXDE in de publicatie-instantie en navigeert u naar `/libs/fd/af/runtime/clientlibs/guideChartReducer`en maakt u de eigenschap die hieronder wordt vermeld.

   * Naam: allowProxy
   * Type: Boolean
   * Waarde: true
   * Beveiligd: Onwaar
   * Verplicht: Onwaar
   * Meerdere: Onwaar
   * Automatisch gemaakt: Onwaar

   Met deze eigenschap hebben de clientbibliotheken in de runtimemap toegang tot proxy&#39;s. (CQ-4268679)

* Wanneer AEM Forms wordt gestart, wordt `SAX Security Manager could not be setup` verschijnt.
* Wanneer u een PDF die met AEM Forms Document Security is beveiligd opent op een Apple iOS of iPad OS met Adobe Acrobat Reader versie 20.10.00.
* Wanneer u een formulier verzendt met een standaard HTML-uploadveld van een Apple iOS-apparaat, wordt soms de inhoud van het bestand niet verzonden en wordt aan de andere kant een bestand van 0 byte ontvangen. Apple iOS 15.1 biedt een oplossing voor het probleem.

## Productdownload en -ondersteuning (beperkt aantal sites) {#product-download-and-support-restricted-sites}

De volgende sites zijn alleen beschikbaar voor klanten. Als u een klant bent en toegang nodig hebt, neemt u contact op met uw Adobe-accountmanager.

* [Product downloaden op licensing.adobe.com](https://licensing.adobe.com/).

* Productupdates, patches en pakketten voor extra functionaliteit op [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).

* [Klantenondersteuning via Admin Console](https://adminconsole.adobe.com/). Zie voor meer informatie [Nieuwe Adobe Customer Support-ervaring](https://docs.adobe.com/content/help/en/customer-one/using/home.html).
