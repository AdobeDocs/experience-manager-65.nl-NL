---
title: Algemene Nota's van de Versie voor  [!DNL Adobe Experience Manager]  6.5
description: In [!DNL Adobe Experience Manager] 6.5 worden de releasegegevens, de nieuwe functies, de installatie en gedetailleerde wijzigingslijsten beschreven.
exl-id: b3d4a527-44ca-4eb6-b393-f3e8117cf1a6
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
source-git-commit: f96b178ae84b4b930b59e36d4994970682c53dbd
workflow-type: tm+mt
source-wordcount: '4477'
ht-degree: 0%

---

# Algemene opmerkingen bij de release voor [!DNL Adobe Experience Manager] 6.5{#general-release-notes-for-adobe-experience-manager}

## Gegevens vrijgeven {#release-information}

| Product | [!DNL Adobe Experience Manager] |
|---|---|
| Versie | 6,5 |
| Type | Grote release |
| Algemene beschikbaarheidsdatum | 8 april 2019 |
| Aanbevolen updates | Zie [ recente updates van AEM ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/aem-releases-updates.html). |

### Trivia {#trivia}

De releasecyclus voor deze versie van [!DNL Adobe Experience Manager] is op 4 april 2018 gestart, 23 versies van kwaliteitsborging en het corrigeren van fouten doorlopen en op 28 maart 2019 afgelopen. Het totale aantal klantgerelateerde problemen, inclusief verbeteringen en nieuwe functies die in deze release zijn opgelost, is 1345.

[!DNL Adobe Experience Manager] 6.5 is over het algemeen beschikbaar sinds 8 april 2019.

![ AEM 6.5 het Login Scherm ](/help/assets/assets/aem65-login-v4.png)

## Wat is er nieuw? {#what-s-new}

[!DNL Adobe Experience Manager] 6.5 is een upgradeversie naar de [!DNL Adobe Experience Manager] 6.4-codebasis. Het verstrekt nieuwe en verbeterde functionaliteit, zeer belangrijke klantenmoeilijke situaties, de verhogingen van de hoge prioriteit, en algemene insectenmoeilijke situaties die op productstabilisatie gericht zijn. Het omvat ook [!DNL Adobe Experience Manager] 6.4 Service Pack-releases tot SP4.

De onderstaande lijst biedt een overzicht, terwijl op de volgende pagina&#39;s alle details worden weergegeven.

### [!DNL Experience Manager Foundation] {#experience-manager-foundation}

Het platform van [!DNL Adobe Experience Manager] 6.5 bouwt voort op bijgewerkte versies van het op OSGi gebaseerde framework (Apache Sling en Apache Felix) en de Java™ Content Repository: Apache Jackrabbit Oak 1.10.2.

De QuickStart gebruikt Eclipse Jetty 9.4.15 als servlet-engine.

#### Java™-ondersteuning  {#java-support}

* Nieuwe ondersteuning voor Java™ 11 en de reeds ondersteunde Java™ 8.
* Overschrijf voor optimale prestaties de standaard GC-waarden met andere waarden. Voor meer informatie, zie [ installeer en werk ](/help/sites-deploying/custom-standalone-install.md) sectie bij.
* Java™ 11- en Java™ 8-onderhoudsupdates worden door Adobe gedistribueerd voor gebruik door klanten in AEM-gerelateerde projecten, indien deze updates niet openbaar zijn vanuit Oracle.

#### Java™-ontwikkeling {#java-development}

* Er zijn nu [ twee versies van Uberjar ](/help/sites-developing/ht-projects-maven.md#experience-manager-api-dependencies), een geadviseerde versie met openbare interfaces die niet voor afschrijving worden gemerkt, en een versie die interfaces duidelijk voor afschrijving omvat.

#### Gebruikersinterface {#user-interface}

Er zijn verschillende verbeteringen aangebracht in de interface om deze productiever en gebruiksvriendelijker te maken.

* Nieuwe interface voor machtigingenbeheer voor gebruikers en groepen.
* Met Kolomweergaven worden nu ook alleen items geladen die op het scherm zichtbaar zijn en alleen meer laden wanneer de gebruiker begint met schuiven. De lijst- en kaartweergave heeft dat al gedaan sinds 6.0 (verbeterd in 6.4).
* Kolomweergaven bevatten nu, indien van toepassing, de workflowstatus voor pagina&#39;s/middelen.
* [ Uitgezochte Al ](/help/sites-authoring/basic-handling.md#select-all) actie is een snelle manier om een actie met alle pagina&#39;s/activa in de zelfde omslag uit te voeren.
* De [ Uitgezochte Al ](/help/sites-authoring/basic-handling.md#select-all) actie probeert om de actie aan alle pagina&#39;s/activa uit te voeren, niet alleen wat is geladen. Er wordt een waarschuwingsvenster weergegeven als de handeling niet is bijgewerkt om Bulk-handelingen af te handelen.

>[!CAUTION]
>
>Adobe is niet van plan verdere verbeteringen aan te brengen in de klassieke gebruikersinterface. AEM 6.5 heeft de klassieke gebruikersinterface inbegrepen, en klanten die van vroegere versies bevorderen kunnen het blijven gebruiken zoals is. Klassieke UI blijft volledig gesteund terwijl wordt afgekeurd. [ las meer ](/help/sites-deploying/ui-recommendations.md).

#### Zoeken en indexeren {#indexing-and-search}

* Zoeken in Oak ondersteunt nu dynamische facetten. Zo toont de filterrail in de zoekopdracht naar elementen het geschatte aantal resultaten.
* QueryBuilder is uitgebreid om resultaten met dynamische facetten te bieden.

#### Upgrade {#upgrade}

* Directe upgrade naar AEM 6.5 wordt ondersteund voor klanten met AEM 6.2, 6.3 en 6.4. Klanten die 5.x of 6.0/6.1 gebruiken die op plaats verbetering willen gebruiken moeten eerst aan 6.4 bevorderen. Voer vervolgens een upgrade uit naar 6.5 of voer een upgrade uit door de inhoud tussen de verschillende exemplaren rechtstreeks over te brengen naar AEM 6.5.
* De upgradeprocedure blijft grotendeels dezelfde in paragraaf 6.5.
* We blijven de functies Achterwaartse compatibiliteit, Complexiteitsbeoordeling upgraden en Duurzame upgrades die in 6.4 zijn geïntroduceerd, ondersteunen. Er zijn waar nodig versiespecifieke updates aangebracht op deze gebieden.
* Het pakket Patroondetector is nu vereenvoudigd. Er is één pakket dat verbeteringen aan 6.5 voor de beschikbare bronversies evalueert.
* Voor details over verbeteringsprocedure, zie de [ verbeteringsdocumentatie ](/help/sites-deploying/upgrade.md).

#### Projecten en workflows {#projects-and-workflows}

* De nieuwe workflowmodeleditor die in 6.4 is geïntroduceerd, is verbeterd en bevat nu meer bewerkingen, zoals Kopiëren en Publiceren, Variabele ondersteuning in workflowstappen en verbeterde splitsingen `OR` en `AND` .

#### Bewaarplaats {#repository}

* De basis van Adobe Experience Manager 6.5 bouwt voort op de bijgewerkte versies van het op OSGi gebaseerde framework (Apache Sling en Apache Felix) en de Java™ Content Repository: Apache Jackrabbit Oak 1.10.2.
* Voor een overzicht van vaste kwesties, zie [ Apache Jackrabbit Oak Jira v. 1.10.0 ](https://archive.apache.org/dist/jackrabbit/oak/1.10.0/RELEASE-NOTES.txt), [ Apache Jackrabbit Oak Jira v. 1.10.1 ](https://archive.apache.org/dist/jackrabbit/oak/1.10.1/RELEASE-NOTES.txt) en [ Apache Jackrabbit Oak Jira v. 1.10.2 ](https://archive.apache.org/dist/jackrabbit/oak/1.10.2/RELEASE-NOTES.txt).

>[!CAUTION]
>
>Voor de nieuwe versie van de Oak Segment Tar, die aanwezig is sinds AEM 6.3, is een migratie naar de opslagplaats vereist. Deze stap is verplicht als u een upgrade uitvoert van een oudere versie van TarMK of als u de nieuwe segmentmarkering wilt overschakelen van een ander type persistentie. Voor meer informatie over wat de voordelen van nieuwe Tar van het Segment zijn, zie [ Migrerend aan de Veelgestelde vragen van Tar van het Segment van Oak ](/help/sites-deploying/revision-cleanup.md#migrating-to-oak-segment-tar).

#### OSGI {#osgi}

* Toegevoegde OSGi Promises en de nutsbibliotheken van de Converter.

#### Beveiliging {#security}

* Wachtwoordvervaldatum voor Admin-gebruiker toegevoegd.

#### Webserver {#web-server}

* Bij de distributie van Quickstart wordt Eclipse Jetty 9.4.15 gebruikt als servlet-engine (AEM 6.4 geleverd met 9.3.22).

### [!DNL Experience Manager] Sites {#experience-manager-sites}

#### Beheerde apps met één pagina {#managed-single-page-apps}

De Redacteur van de Pagina voegt de capaciteit aan in-context toe geeft inhoud uit en stelt/lay-out binnen cliënt-kant teruggegeven ervaringen (ook genoemd [ als Redacteur van het KUUROORD ](/help/sites-developing/spa-architecture.md)) samen. De bestaande apps van één pagina bouwen met het kader van JavaScript React of Angular kunnen met AEM SJ SDK worden uitgebreid om editable voor artsen te worden gemaakt.

Eerste verscheepte als deel van AEM 6.4 SP2, met AEM 6.5 krijgt de steun van het KUUROORD volgende mogelijkheden:

* De Redacteur van het Malplaatje van het gebruik om de bewerkbare delen van AEM uit te geven en te vormen SPA
* Gebruik Beheer op meerdere locaties om ervaringen met het maken van een land, franchise of witte SPA te maken

#### Beheer van inhoud zonder hoofd {#headless-content-management}

AEM kan de inhoud in verschillende indelingen en op verschillende niveaus van de stapel leveren. Sommigen zijn rond sinds 2008 met [ het Verdelen GET ](https://sling.apache.org/documentation/bundles/rendering-content-default-get-servlets.html) en [ POST Servlet ](https://sling.apache.org/documentation/bundles/manipulating-content-the-slingpostservlet-servlets-post.html) geweest. De Diensten van de inhoud ([ het Verdelen ModelExporter ](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/develop-sling-model-exporter.html)) werd geïntroduceerd in AEM 6.3 en is de methode die door AEM SJ SDK wordt gebruikt om single-page apps te bevrijden. [ HTTP API voor Assets ](/help/assets/mac-api-assets.md) is een CRUD API, die voor AEM 6.5 werd uitgebreid.

Nieuwe HTTP API-mogelijkheden:

* Toegevoegde [ steun van het Fragment van de Inhoud aan HTTP API voor Assets ](/help/assets/assets-api-content-fragments.md) om, fragmenten tot stand te brengen bij te werken, te lezen en te schrappen.
* Stel lijsten van Inhoudsfragmenten via de Diensten van de Inhoud met de [ Component van de Kern van de Lijst van het Fragment van de Inhoud ](https://www.aemcomponents.dev) bloot.
* [ Bibliotheek van de Component van de Kern ](https://www.aemcomponents.dev) die de output van de Diensten JSON van de Inhoud van de standaard voor elke component toont

#### Screens-invoegtoepassing {#screens-add-on}

Efficiënt ontwerpen, leveren en optimaliseren van ervaringen op alle digitale schermen, van interactieve kiosken tot digitale signage.

* Ervaringen en inhoud op digitale en in-store gelijktrekken met verbeterd hergebruik van inhoud
* Gestroomlijnde workflows voor schrijven en goedkeuren/publiceren met ondersteuning voor Starts
* Bewerk en lever rijke interactieve ervaringen met de SPA Editor
* Het gebruiken van Lanceringen om toekomstige inhoudsveranderingen voor signaalinhoud te plannen
* Metered playback in een opeenvolgingskanaal
* Automatisch een projectstructuur maken met een bronbestand, zoals een Excel-werkblad
* Uitgebreide ondersteuning voor mediaspelers met robuuste online en offline bediening (Smart Sync) die kan worden geschaald naar zelfs de grootste signaalnetwerken.
* Personaliseer door plaats of configuratie van gegevens teweeggebrachte inhoud door dynamische placeholders te gebruiken.
* Verenigde inzichten gedreven door de integratie van Adobe Analytics in AEM Screens Player

Voor meer details op veranderingen in AEM Screens - zie de Nota&#39;s van de Versie in de [ Gids van de Gebruiker van AEM Screens ](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/aem-screens-introduction.html).

#### Component- en sjabloonontwikkeling {#component-amp-template-development}

* Gemaakt Archetype 18+ van het Project voor nieuwe projecten, zie [ GitHub voor versienota&#39;s ](https://github.com/adobe/aem-project-archetype/releases).
* Enige-pagina App Maven Type van Projectarchetype 1.0.6+ voor nieuwe projecten, zie [ GitHub voor versienota&#39;s ](https://github.com/adobe/aem-spa-project-archetype/releases).
* HTML versie 1.4, zie [ GitHub voor versienota&#39;s ](https://github.com/adobe/htl-spec/releases/tag/1.4).

   * operator &quot;in&quot; voor tekenreeksen, arrays en objecten:

     ```html
     ${'a' in 'abc'}
     ${100 in myArray}
     ${'a' in myObject}
     ```

   * Declaraties van variabelen met subset van gegevens:
     `<sly data-sly-set.title="${currentPage.title}"/>${title}`

   * De controleparameters van de lijst en van de herhaling: begin, stap, eind:
     `<h2 data-sly-repeat="${currentPage.listChildren @ begin = 1, step=2}">${item.title}</h2>`

   * Id&#39;s voor terugloop van gegevensdoorhaling:

     ```html
     <div data-sly-unwrap.isUnwrapped="${myCondition || myOtherCondition}">
     text <span data-sly-test="${isUnwrapped}>is unwrapped</code>
     </div>
     ```

   * Ondersteuning voor negatieve getallen

* De Componenten van de kern 2.3.2+, zie [ GitHub voor versienota&#39;s ](https://github.com/adobe/aem-core-wcm-components/releases).
* Het Systeem van het net voor de Container van de Lay-out, zie [ GitHub ](https://github.com/Adobe-Marketing-Cloud/aem-responsivegrid).
* Clientlib Manager: hiermee wordt Google Closure Compiler standaard ingesteld op minificatie van JavaScript-clientlibs (de oude standaardwaarde was Yahoo YUI) en wordt Google Closure Compiler bijgewerkt naar versie v20190121
* Sjablooneditor en beleidsregels

   * Creeer en geef malplaatjes voor enig-pagina apps uit die JS SDK (ook genoemd Redacteur van het KUUROORD) gebruiken

* De Plaats van de verwijzing wij.Retail 4.0, zie [ GitHub voor versienota&#39;s ](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/releases).
* Toolkit om bestaande plaatsen te bevorderen om de recentste redacteursmogelijkheden te gebruiken, zie ](https://github.com/adobe/aem-modernize-tools) bewaarplaats GitHub [

>[!CAUTION]
>
>AEM bevat versie 1.12.4 van de jQuery-bibliotheek voor maximale compatibiliteit met bestaande aangepaste code. Adobe heeft wijzigingen aangebracht om bekende beveiligingsproblemen aan te pakken.

#### Sitebeheer {#site-administration}

* Het [ spoor van de Verwijzing ](/help/sites-authoring/author-environment-tools.md#references) heeft een nieuwe sectie om van interne verbindingen een lijst te maken die aan de geselecteerde pagina richten. Dit is handig wanneer u een pagina offline of verwijderd wilt maken. Zo kunt u zien welke pagina&#39;s moeten worden aangepast voordat u de pagina&#39;s offline plaatst.
* De [ lijstmening ](/help/sites-authoring/basic-handling.md#list-view) heeft een nieuwe werkschemakolom die de status toont wanneer de pagina in een werkschema is.
* In de [ paginaeigenschappen ](/help/sites-authoring/editing-page-properties.md), is het nu mogelijk om voor bestaande activa te doorbladeren wanneer het toewijzen van een Duimnagel aan de pagina (het lusje van de Duimnagel).

#### Pagina-editor {#page-editor}

* In context bewerken en samenstellen van app-ervaringen van één pagina toestaan die zijn opgebouwd met React en Angular client-side componenten die JS SDK (ook wel SPA Editor genoemd) gebruiken
* De modus Basisstructuur wordt alleen weergegeven als op de pagina een basispagina is geconfigureerd.

#### Inhoudsfragmenten en editor {#content-fragments-amp-editor}

* Nieuwe ](/help/assets/content-fragments/content-fragments-variations.md#viewing-editing-deleting-annotations) spoorstaaf 0} Annotaties {in de Redacteur van het Fragment van de Inhoud om algemene commentaren te maken en commentaren te zien die binnen de tekst (ook verschijnen in spoorstaaf van de Chronologie) worden gemaakt[
* Mogelijkheid om het standaardinhoudstype van een multi-line tekstelement in het model van het Fragment van de Inhoud van a [ ](/help/assets/content-fragments/content-fragments-models.md) aan eenvoudige tekst, rijke tekst, of prijsdaling te plaatsen
* Voeg [ commentaar/annotaties ](/help/assets/content-fragments/content-fragments-variations.md#annotating-a-content-fragment) toe door tekst in RTE (het volledig-schermmening) te selecteren
* [ vergelijk versies ](/help/assets/content-fragments/content-fragments-managing.md#comparing-fragment-versions) van een Fragment van de Inhoud zij aan zij via spoorstaaf van de Verwijzing
* In het rapport Downloaden van middelen worden nu inhoudsfragmenten dienovereenkomstig weergegeven
* Voeg [ steun van het Fragment van de Inhoud aan HTTP API van Assets ](/help/assets/assets-api-content-fragments.md) via /api.json toe. Er zijn API&#39;s voor het maken, bijwerken, lezen en verwijderen van inhoudsfragmenten.

#### Ervaar fragmenten {#experience-fragments}

* Verbeterde het indexeren van [ Fragmenten van de Ervaring ](/help/sites-authoring/experience-fragments.md), zodat wordt hun inhoud gevonden in onderzoek naar pagina&#39;s waar zij worden gebruikt.
* De [ Uitvoer aan de optie van het Doel ](/help/sites-administering/experience-fragments-target.md) laat u nu het Fragment van de Ervaring als JSON (gebrek is HTML) of allebei verzenden.

#### Vertaling {#translation}

* Vereenvoudig het maken van vertaalprojecten met behulp van Projectstramienen.
* Vereenvoudig het uitvoeren van vertaalprojecten door vertaalbanen aan goedgekeurde status door gebrek te plaatsen.
* Het bijwerken van vertaalde pagina&#39;s met wijzigingen in het vertaalgeheugen van derden toestaan.
* Vertaaltaken in JSON-indeling exporteren toestaan.
* Microsoft® Translation-integratie bijwerken om de V3 API te gebruiken.

#### Multisite beheer (MSM) {#multi-site-management-msm}

* Voor roll-out vormen die PushOnModify gebruiken, betere behandeling van paginabewegingsverrichting om inconsistente staat te vermijden.
* Als u een pagina maakt in de structuur van de livecopy, wordt standaard een zelfstandige pagina gemaakt.
* De eigenschappen van MSM van het gebruik in single-page apps die JS SDK (ook genoemd Redacteur van het KUUROORD) gebruiken

#### Lanceringen {#launches}

* Nieuwe revisie- en goedkeuringswerkstroom voor introducties en de mogelijkheid om alleen goedgekeurde startpagina&#39;s te promoten
* Toegevoegde [ optie in UI om te verkiezen om het recht van de Lancering na de bevorderingsstap ](/help/sites-authoring/launches-promoting.md#promoting-launch-pages) te schrappen

#### Inhoud richten en simuleren {#content-targeting-simulation}

* De de gegevenslaag van ContextHub en cliënt-zijregelmotor JavaScript is bijgewerkt om jQuery 3 door gebrek te gebruiken.

#### AEM en Adobe Target {#aem-amp-adobe-target}

>[!CAUTION]
>
>Momenteel:
>
>* Alleen `at.js 1.x` wordt ondersteund als u Adobe Target gebruikt als de doelengine in de AEM Activity Console.
>
>* Zowel `at.js. 1.x` als `at.js 2.x` worden ondersteund als u Experience Fragment exporteert naar Doel en Activiteiten uitvoert binnen de console van Target.

* Adobe Target-integratie gebruikt nu de Target Standard API. Eerdere versies van AEM gebruiken de Classic HTTP-API van Target, die nu is afgekeurd.
* Adobe Target `mbox.js` versie 63 is inbegrepen. Adobe raadt u ten zeerste aan de implementatie over te schakelen op `at.js` v1.x.
* `at.js` versie 1.5.0 is nu inbegrepen. Adobe adviseert dat u [ Adobe Experience Platform Launch ](https://business.adobe.com/products/experience-platform/launch.html) aan voorziening `at.js` v1.x in de plaats gebruikt.

#### AEM en Adobe Analytics {#aem-amp-adobe-analytics}

* `s_code.js` H.27.5 is opgenomen. Adobe raadt u aan over te schakelen op `AppMeasurement.js`
* `AppMeasurement.js` v1.8.0 is opgenomen. Adobe adviseert dat u [ Adobe Experience Platform Launch ](https://business.adobe.com/products/experience-platform/launch.html) aan voorziening AppMeasurement.js in de plaats gebruikt.

#### AEM en Commerce {#aem-commerce}

Verbeteringen aan de Commerce integration framework zijn sinds AEM 6.4 sneller beschikbaar. Leer meer van [ de Integratie van AEM en van Adobe Commerce Gebruikend Commerce integration framework ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/magento.html).

#### Invoegtoepassing Gemeenschappen {#communities-add-on}

Om de recentste versie te verkrijgen, zie [ het Opstellen van Gemeenschappen ](/help/communities/deploy-communities.md) sectie van de documentatie.

##### Verbeteringen van de betrokkenheid van de gemeenschap {#enhancements-to-community-engagement}

**@Ondersteuning voor vermeldingen**
In AEM Communities kunnen geregistreerde gebruikers nu tags toewijzen (andere geregistreerde leden vermelden) om hun aandacht te vestigen op door gebruikers gegenereerde inhoud. De gelabelde (vermelde) leden worden vervolgens op de hoogte gesteld, met een diepe koppeling naar de overeenkomstige door de gebruiker gegenereerde inhoud. Gebruikers kunnen er echter voor kiezen om het web- en e-mailbericht uit te schakelen of in te schakelen.

![ bij de steun van Vermeldingen ](/help/release-notes/assets/at-mentions.png)

De gebruikers van de Gemeenschap te hoeven niet naar hun voornaam, familienaam, of gebruikersnaam te zoeken om te zien of heeft iemand uit aan hen bereikt of hun aandacht nodig. Bovendien kunnen UGC-auteurs reacties vragen bij specifieke geregistreerde gebruikers die het probleem het beste kunnen oplossen en invoer kunnen toevoegen.

De communautaire beheerders moeten **Mentie** op communautaire componenten toelaten om geregistreerde gebruikers toe te staan de functionaliteit op die componenten gebruiken.

**overseinen van de Groep**

Geregistreerde leden van de community kunnen nu bulksgewijs directe berichten naar groepen verzenden via één e-mailcompositie, in plaats van hetzelfde bericht afzonderlijk naar groepsleden te verzenden. Om [ groepsoverseinen ](/help/communities/configure-messaging.md) toe te staan, laat beide instanties van [ de Dienst van de Verrichtingen van het Overseinen ](/help/communities/messaging.md#group-messaging) toe.

![ het bericht van de Groep ](/help/release-notes/assets/group-messaging.png)

##### Verbeteringen voor Bulk Moderation {#enhancements-to-bulk-moderation}

Aangepaste filters in Bulk-moderatie

[ de filters van de Douane ](/help/communities/moderation.md#custom-filters) kunnen nu worden ontwikkeld en aan Onduidelijke Moderatie UI worden toegevoegd.

A [ steekproefproject ](https://github.com/Adobe-Marketing-Cloud/aem-communities-extensions/tree/master/aem-communities-moderation-filter) dat het filtreren door markeringen aantoont is beschikbaar in [ GitHub ](https://github.com/Adobe-Marketing-Cloud/aem-communities-extensions/tree/master/aem-communities-moderation-filter). Dit project kan als basis worden gebruikt om analoge douanefilters te ontwikkelen.

![ de filters van de Douane ](/help/release-notes/assets/custom-tag-filter.png)

**Mening van de Lijst in Bulk Moderatie**

De nieuwe Mening van de Lijst met betere UI is verstrekt in bulkmoderatie om Gebruiker te tonen Gegenereerde Inhoudsingangen.

![ Bulk matiging in lijstmening ](/help/release-notes/assets/list-view-moderation.png)

##### Verbeteringen voor site- en groepsbeheer {#enhancements-to-site-and-group-management}

**de zijplaats en groepbeheerders van de auteur**

Gemeenschappen, AEM 6.5 en hoger, maken gedecentraliseerd beheer (en beheer) van verschillende gemeenschapssites en -groepen/ geneste groepen mogelijk. Organisaties die meerdere communitysites en geneste groepen hosten, kunnen nu leden selecteren voor beheerdersrollen aan de Auteur op het moment dat de site (en groep) wordt gemaakt.

![ beheerder van de Plaats ](/help/release-notes/assets/site-admin.png)

Sitebeheerders kunnen een groep op elk hiërarchisch niveau maken en de standaardbeheerders worden. Deze beheerders kunnen later door andere groepbeheerders worden verwijderd. De beheerders van de groep kunnen hun groep G1 beheren en tot een subgroep leiden die onder G1 wordt genest.

##### Verbeteringen op gebied van activering {#enhancements-to-enablement}

**SCORM 2017.1 steun**

De enablement-functionaliteit van AEM 6.5 Communities ondersteunt Shareable Content Object Reference Model [ (SCORM) 2017.1 ](https://rusticisoftware.com/blog/scorm-engine-2017-released/) -engine.

* Ondersteuning voor toetsenbordnavigatie op schakelingscomponenten
* De componenten van Enablement (bijvoorbeeld, Catalog en Cursus het Spelen, Toewijzingen, de Bibliotheek van het Dossier) in AEM Communities steunen toetsenbordnavigatie voor betere toegankelijkheid.

##### Andere verbeteringen {#other-enhancements}

* Solr 7-ondersteuning
* AEM 6.5-gemeenschappen ondersteunen Apache Solr 7.0-versie van het zoekplatform bij het opzetten van MSRP en DSRP.

### [!DNL Experience Manager Assets] {#experience-manager-assets}

AEM 6.5 introduceert de volgende mogelijkheden en verbeteringen om de productiviteit van AEM-gebruikers, DAM-rollen en de bijbehorende creatieve en marketingrollen te verhogen.

#### Integratie met [!DNL Adobe Creative Cloud] en creatieve workflows {#integration-with-adobe-creative-cloud-and-creative-workflows}

[!DNL Adobe Experience Manager] biedt verschillende manieren om te integreren met [!DNL Adobe Creative Cloud] en elementen te delen voor gebruik in workflows waarbij de creatieve en marketingteams of de zakelijke teams nauw samenwerken. [!DNL Experience Manager] 6.5 gaat door met het verbeteren van de integratie en stroomlijnt deze verder om meer mogelijkheden te bieden en de bestaande methoden te stroomlijnen.

Lees verder om de specifieke mogelijkheden en integratie van [!DNL Experience Manager] 6.5 te kennen die u kunt gebruiken om de gebruiksscenario&#39;s van de inhoudssnelheid het beste te ondersteunen.

##### Adobe Asset Link {#aal}

[!DNL Adobe Asset Link] versterkt de samenwerking tussen ontwerpers en marketers bij het maken van inhoud. Creatieven hebben toegang tot inhoud die is opgeslagen in [!DNL Experience Manager Assets] zonder de apps te verlaten waarmee ze het meest vertrouwd zijn. Creatieven kunnen naadloos door elementen bladeren, zoeken, uitchecken en inchecken via het deelvenster in de app in [!DNL Adobe Photoshop] -, [!DNL Adobe Illustrator] - en [!DNL Adobe InDesign] -apps.

[!DNL Adobe Asset Link] is een deel van [ Creative Cloud voor onderneming ](https://www.adobe.com/creativecloud/business/enterprise.html) het aanbieden. Voor meer informatie over het, met inbegrip van noodzakelijke configuratie van uw [!DNL Experience Manager] plaatsing, zie [ de Verbinding van Activa van Adobe ](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html).

![ activa van het Onderzoek in Adobe Photoshop ](/help/release-notes/assets/asset_search_photoshop.png)

##### [!DNL Adobe Stock] integratie {#stock}

Uw organisatie kan haar [!DNL Adobe Stock] ondernemingsplan binnen [!DNL Experience Manager Assets] gebruiken om ervoor te zorgen dat gelicentieerde activa over het algemeen beschikbaar voor uw creatieve en marketing projecten zijn. U kunt [!DNL Adobe Stock] -elementen die zijn opgeslagen in Experience Manager, snel zoeken, voorvertonen en licentiëren met de krachtige DAM-mogelijkheden van [!DNL Experience Manager] .

[!DNL Adobe Stock] biedt ontwerpers en bedrijven toegang tot miljoenen kwalitatief hoogstaande, gekrulde, royaltyvrije foto&#39;s, vectoren, illustraties, video&#39;s, sjablonen en 3D-middelen voor al hun creatieve projecten.

Voor meer info, zie [ de activa van Adobe Stock van het Gebruik in Experience Manager Assets ](/help/assets/aem-assets-adobe-stock.md).

![ het beeld en de vergunning van de Voorproef Adobe Stock van binnen Experience Manager Assets ](/help/release-notes/assets/stock_image_preview_license_options.png)

*Cijfer: Voorproef [!DNL Adobe Stock] beeld en vergunning van binnen [!DNL Experience Manager Assets].*

![ Onderzoek en filter de vergunning gegeven beelden van Adobe Stock in Experience Manager ](/help/release-notes/assets/aem-search-filters2.jpg)

*Cijfer: Onderzoek en filter de vergunning gegeven [!DNL Adobe Stock] beelden in [!DNL Experience Manager].*

##### Dynamische verwijzingen in [!DNL Adobe InDesign] {#dynamic-references-in-indesign}

[!DNL Experience Manager Assets] die in [!DNL Adobe InDesign] -bestanden wordt gebruikt, is dynamisch. De verwijzingen worden automatisch bijgewerkt als de middelen waarnaar wordt verwezen in de bewaarplaats worden verplaatst. Voor meer informatie, zie [ hoe te om samengestelde activa ](/help/assets/managing-linked-subassets.md) te beheren.

#### Brand Portal-mogelijkheden {#brand-portal-capabilities}

Met [!DNL Experience Manager Assets Brand Portal] kunt u de goedgekeurde middelen eenvoudig aanschaffen, effectief beheren en veilig verspreiden onder externe leveranciers/agentschappen en interne zakelijke gebruikers op verschillende apparaten. Het helpt de efficiëntie van het delen van bedrijfsmiddelen te verbeteren, versnelt de tijd tot aan de markt voor bedrijfsmiddelen en voorkomt het risico van niet-conform gebruik en ongeoorloofde toegang.

Voor meer informatie, zie [ wat in Brand Portal ](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/whats-new.html) nieuw is.

#### Verbonden Assets {#connectedassets}

In grote ondernemingen kan de infrastructuur die nodig is om websites te maken, worden gedistribueerd. Soms bevinden de mogelijkheden voor het maken van websites en de vereiste digitale middelen zich in verschillende silo&#39;s.

[!DNL Experience Manager Sites] biedt mogelijkheden om webpagina&#39;s te maken en [!DNL Experience Manager Assets] is het DAM-systeem (Digital Asset Management) dat de vereiste middelen voor websites levert. [!DNL Experience Manager] biedt nu ondersteuning voor het bovenstaande gebruik van hoofdletters en kleine letters door [!DNL Sites] en [!DNL Assets] te integreren. Zie [ hoe te om Verbonden eigenschap van Assets te vormen en te gebruiken ](/help/assets/use-assets-across-connected-assets-instances.md).

![ belemmering een activa van een [!DNL Experience Manager] plaatsing op een [!DNL Sites] pagina van een verschillende [!DNL Experience Manager] plaatsing ](/help/release-notes/assets/connected-assets-drag-and-drop-only.gif)

*Cijfer: Sleep activa van een [!DNL Experience Manager] plaatsing op een [!DNL Sites] pagina op een verschillende [!DNL Experience Manager] plaatsing.*

#### Dynamische media {#dynamic-media}

[!DNL Dynamic Media] biedt verbeterde functies voor het schrijven en leveren van geavanceerde media in [!DNL Experience Manager Assets] voor geavanceerde ervaringen die overweldigend en gepersonaliseerd zijn. Door één primaire bron van hoge kwaliteit te uploaden en Adobe te gebruiken voor geavanceerde cloudrendering en viewers, kunt u elke combinatie van uitvoeringen ter plekke aanbieden ter ondersteuning van de mediastrategie van uw organisatie.

Voor meer details op nieuwe [!DNL Dynamic Media] eigenschappen, zie [ Dynamische Nota&#39;s van de Versie van Media ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/release-notes/s7rn2017.html).

##### 360 video-ondersteuning {#video-support}

Beheer uw 360-videobestanden rechtstreeks in [!DNL Experience Manager] met behulp van de meest geavanceerde viewers voor VR-ervaringen op desktops, mobiele apparaten en VR-headsets. Voor meer informatie, zie [ Gebruikend 360 Video ](/help/assets/360-video.md).

##### Aangepaste videominiaturen {#custom-video-thumbnails}

U kunt de miniaturen voor uw video-elementen nu aanpassen met frames uit de video zelf of andere inhoud die is opgeslagen in de DAM. Voor extra instructies, zie [ Ongeveer VideoDuimnagels ](/help/assets/video.md#about-video-thumbnails-in-dynamic-media-scene-mode).

##### Verbeteringen voor toegankelijkheid {#accessibility-enhancements}

[!DNL Dynamic Media] -viewers bieden nu ondersteuning voor verbeterde toegankelijkheidsfuncties, zoals apparaatondersteuning, schermlezers en Alt-tekst. Voor extra details, zie {de Gids van de Verwijzing van 0} Kijkers ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/homeviewers.html).[

#### Verbeterde zoekervaring {#experience-enhancement-for-searching}

Vanaf [!DNL Experience Manager] 6.5 kunnen marketers de gewenste middelen sneller vinden op de pagina met zoekresultaten. De zoekfacetten worden met het aantal elementen bijgewerkt, zelfs voordat het zoekfilter wordt toegepast. Door het verwachte aantal op het filter te zien, kunnen gebruikers efficiënt door de zoekresultaten navigeren. Voor meer informatie, zie [ activa van het Onderzoek in Experience Manager ](/help/assets/search-assets.md).

![ zie het aantal activa zonder het filtreren onderzoeksresultaten in onderzoeksfacetten ](/help/assets/assets/asset_search_results_in_facets_filters.png)

*Cijfer: Zie het aantal activa zonder het filtreren onderzoeksresultaten in onderzoeksfacetten.*

#### Verbetering van bruikbaarheid {#usability-enhancement}

U kunt nu alle geladen elementen in een map selecteren of vanuit een zoekresultaat in één keer. Hiermee kunt u meerdere elementen snel beheren. Met het selectievakje worden alle elementen geselecteerd die in het scenario passen, zoals een zoekresultaat, en niet alleen de elementen die zichtbaar zijn in de interface van [!DNL Experience Manager] .

![ Uitgezocht van het Gebruik Al optie om alle geladen activa in één klik te selecteren.](/help/release-notes/assets/select-all-in-aem-assets.gif)

*Cijfer: Gebruik Uitgezocht Al optie om alle geladen activa in één klik te selecteren.*

#### Verbeteringen in metagegevens {#metadata-enhancements}

Met [!DNL Assets] kunt u metagegevensschema&#39;s maken voor middelenmappen, waarmee de lay-out en de metagegevens worden gedefinieerd die op de pagina&#39;s met mapeigenschappen worden weergegeven. U kunt nu een schema voor mapmetagegevens toewijzen aan een bestaande map of bij het maken van een map. Voor meer informatie, zie [ het meta-gegevensschema van de Omslag ](/help/assets/metadata-config.md#folder-metadata-schema).

Als u trapsgewijze metagegevens opgeeft, kunnen de opties tijdens de runtime uit een JSON-bestand worden geladen, bijvoorbeeld in plaats van handmatig in het formulier te typen. Voor meer informatie, zie [ het draperen meta-gegevens ](/help/assets/metadata-schemas.md#cascading-metadata).

#### Verbeteringen rapporteren {#reporting-enhancements}

De Inhoudsfragmenten en de aandelen van de verbinding zijn nu inbegrepen in het gedownloade rapport. Voor meer informatie, zie [ de rapporten van Assets ](/help/assets/asset-reports.md).

### [!DNL Adobe Experience Manager Forms] {#experience-manager-forms}

AEM 6.5 Forms biedt verschillende nieuwe functies en verbeteringen. De hooglichten omvatten:

* Transactierapporten om het aantal ingediende formulieren, verwerkte documenten en gerenderde documenten bij te houden
* Verbeteringen van de bruikbaarheid van interactieve communicatie
* Digitale handtekeningen op basis van cloud in adaptieve formulieren
* Aangepaste formulieren en interactieve communicatie insluiten in een AEM Sites single page application (SPA).
* Ondersteuning voor variabelen in AEM Workflows
* Ondersteuning van gegevenspatronen in interactieve communicatie
* Aangepaste formulieren en interactieve communicatietabellen sorteren
* Geautomatiseerde validatie van invoergegevens in formuliergegevensmodellen

Zie [ Samenvatting van nieuwe eigenschappen en verhogingen in AEM 6.5 Forms ](/help/forms/using/whats-new.md) voor informatie over nieuwe en betere eigenschappen en documentatiemiddelen.

### Gebruik klantgerichte ontwikkeling {#use-customer-focused-development}

Adobe gebruikt een klantgericht ontwikkelingsmodel dat klanten toestaat om aan alle stadia van het ontwikkelingsproces, tijdens specificatie, ontwikkeling, en het testen bij te dragen. Onze dank gaat uit naar alle klanten en partners die een bijdrage leveren aan dit proces.

Adobe heeft de procedures en processen op zijn plaats om inzameling, prioriteitstelling, en het volgen van klant-geconcentreerde insectenresolutie en de ontwikkeling van verbeteringsverzoeken toe te laten. Het [ portaal van de Steun van Experience Manager ](https://experienceleague.adobe.com/?support-solution=Experience+Manager#support) is geïntegreerd met de Verbetering van Adobe en het Gebrek die Systeem volgen. De vragen van de klant worden geïdentificeerd en opgelost door het team van de Steun van de Klant waar mogelijk. Bij doorverwijzing naar O&amp;O wordt alle klantinformatie vastgelegd en gebruikt voor prioritering en rapportage. Prioriteit wordt gegeven in ontwikkeling aan betaalde steun, garantiekwesties, en klant-betaalde verhogingen.

Dit proces van prioritering heeft meer dan 750 klantgerichte veranderingen opgeleverd die in AEM 6.5 worden bevestigd.

## Lijst met bestanden die deel uitmaken van de release {#list-of-files-that-are-part-of-the-release}

**Stichting**

* Zelfstandige QuickStart: `cq-quickstart-6.5.0.jar`.
* Application Server QuickStart: `cq-quickstart-6.5.0.war`.
* Dispatcher 4.3.2 of hoger voor de verschillende webservers en -platforms. Zie [ downloadverbinding ](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/getting-started/release-notes.html)
* Plug-in voor winde van de Verduistering ([ lees meer en download ](/help/sites-developing/aem-eclipse.md))

* Uitbreiding voor de Redacteur van de Code van de Brackets ([ lees meer en download ](/help/sites-developing/aem-brackets.md))
* Geweven/de gebiedsdelen van de Wieg ([ downloadverbinding ](https://repo1.maven.org/maven2/com/adobe/aem/uber-jar/6.5.0/))

**Plaatsen**

* De Componenten van de kern ([ project GitHub ](https://github.com/adobe/aem-core-wcm-components))
* Wij.Retail de implementatie van de Verwijzing ([ las meer ](/help/sites-developing/we-retail.md))
* Maven Project archetypes:

   * voor volledig-stapelplaatsen: [ het project GitHub ](https://github.com/adobe/aem-project-archetype)
   * voor enig-pagina apps met React/Angular: [ GitHub project ](https://github.com/adobe/aem-spa-project-archetype)

* AEM Screens Players voor diverse doelplatforms ([ download ](https://download.macromedia.com/screens/))

* Smart Content Language Models. Engels is vooraf geïnstalleerd - meer talen kunnen worden gedownload

   * [ Duits ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-de)
   * [ Spaans ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-es)
   * [ Italiaans ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-it)
   * [ Frans ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-fr)

* AEM Modernize Tools Suite, bijvoorbeeld Dialog Conversion Tool. ([ project GitHub ](https://github.com/adobe/aem-modernize-tools))

**Assets**

* Pakket om verbeterde Rasterizer van PDF toe te voegen ([ lees meer ](/help/assets/aem-pdf-rasterizer.md))
* Pakket om uitgebreide RAW beeldsteun toe te voegen ([ lees meer ](/help/assets/camera-raw.md))

**Forms**

* [ Pakketten voor de mogelijkheden van AEM Forms ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html)
* [ AEM Forms OSGi Cliënt SDK ](https://repo1.maven.org/maven2/com/adobe/aemfd/aemfd-client-sdk/)

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

Voor opstellingsvereisten, zie [ installatieinstructies ](/help/sites-deploying/custom-standalone-install.md).

Voor gedetailleerde instructies, zie [ verbeteringsdocumentatie ](/help/sites-deploying/upgrade.md).

## Ondersteunde platforms {#supported-platforms}

Vind de volledige matrijs van gesteunde platforms met inbegrip van steun-niveau op [ AEM 6.5 technische vereisten ](/help/sites-deploying/technical-requirements.md).

>[!NOTE]
>
>Oracle is overgestapt op een LTS-model (Long Term Support) voor Oracle Java™ SE-producten. Java™ 9 en 10 zijn niet-LTS versies van Oracle. Zie [ Oracle Java™ SE steun roadmap ](https://www.oracle.com/technetwork/java/eol-135779.html). Adobe ondersteunt LTS-versies van Java™ om alleen AEM in productie te houden. Java™ 11 is de aanbevolen versie voor AEM 6.5.

## Verouderde en verwijderde functies {#deprecated-and-removed-features}

Adobe evalueert voortdurend de mogelijkheden in het product en is van plan om in de loop der tijd mogelijkheden te vervangen door krachtigere versies, of besluit om geselecteerde onderdelen opnieuw uit te voeren om beter voorbereid te zijn op toekomstige verwachtingen of uitbreidingen.

Voor [!DNL Adobe Experience Manager] 6.5, [ lees de lijst van afgekeurde en verwijderde mogelijkheden ](/help/release-notes/deprecated-removed-features.md). De pagina bevat ook een vooraankondiging van wijzigingen die in de toekomst zullen plaatsvinden en een belangrijke kennisgeving voor klanten die een update uitvoeren van eerdere releases.

## Bekende problemen {#known-issues}

### Platform {#platform}

* Er wordt een probleem gerapporteerd waarbij de CRX-Quickstart en de inhoud ervan worden verwijderd.

  Controleer bij elk van deze handelingen of de eigenschap `htmllibmanager.fileSystemOutputCacheLocation` geen lege tekenreeks is:

   1. Het roepen `/libs/granite/ui/content/dumplibs.rebuild.html?invalidate=true`.
   2. Upgrade uitvoeren naar AEM 6.5.
   3. Uitvoeren van &quot;luie content migration&quot; op AEM 6.5.

* Als u JDK 11 met AEM 6.5 instantie gebruikt, zouden sommige pagina&#39;s als leeg kunnen tonen na het opstellen van sommige pakketten. Het volgende foutbericht wordt weergegeven in het logbestand:

  ```java
  *ERROR* [OsgiInstallerImpl] org.apache.sling.scripting.sightly bundle org.apache.sling.scripting.sightly:1.1.2.1_4_0 (558)[org.apache.sling.scripting.sightly.impl.engine.extension.use.JavaUseProvider(3345)] : Error during instantiation of the implementation object (java.lang.NoClassDefFoundError: jdk/internal/reflect/ConstructorAccessorImpl)
  java.lang.NoClassDefFoundError: jdk/internal/reflect/ConstructorAccessorImpl
  ```

Deze fout oplossen:

1. Stop de AEM-instantie. Ga naar `<aem_server_path_on_server>crx-quickstart\conf` en open het `sling.properties` -bestand. Adobe raadt u aan een back-up van dit bestand te maken.

1. Zoeken naar `org.osgi.framework.bootdelegation=` . Voeg `jdk.internal.reflect,jdk.internal.reflect.*` eigenschappen toe om het resultaat als resultaat weer te geven.

```java
org.osgi.framework.bootdelegation=sun.*,com.sun.*,jdk.internal.reflect,jdk.internal.reflect.*
```

1. Sla het bestand op en start het AEM-exemplaar opnieuw.

### Sites {#sites}

* **Werkend met de Versies van de Pagina**: [ als een pagina is bewogen, kunt u niet meer een voorproef op om het even welke versies uitvoeren die vóór de beweging ](/help/sites-authoring/working-with-page-versions.md#previewing-a-version) worden gemaakt.

### Assets {#assets}

* **Onderzoek:** het Onderzoek resulteert geen winst als het onderzoekskoord belangrijke ruimten bevat ([ OAK-4786 ](https://issues.apache.org/jira/browse/OAK-4786))
* **het Schema van Meta-gegevens van de Omslag**: Na het toevoegen van een keuzerondje, worden identiteitskaart en het gebied van de Waarde niet teruggegeven zoals verwacht en de schrappingsfunctionaliteit werkt niet. (CQ-4261144)
* Wanneer u de naam van een element wijzigt, is het niet mogelijk een witruimte in de elementnaam te gebruiken. (CQ-4266403)

### Forms {#forms}

* Als AEM Forms is geïnstalleerd op het Linux®-besturingssysteem, werkt Digital Signature with Hardware Security Module niet. (CQ-4266721)
* (AEM Forms op WebSphere® slechts) de **Forms Workflow** > **optie van het Onderzoek van de Taak** keert geen resultaat terug als u naar een **Beheerder** met **Gebruikersnaam** als onderzoekscriteria zoekt. (CQ-426457)

* AEM Forms kan TIF- en TIFF-bestanden met JPEG-compressie niet converteren naar PDF-documenten. (CQ-4265972)
* De **Scanner van AEM Forms Assets** en **Brief aan Interactieve Communicatie Migratie** opties werken niet op de **AEM Forms migratie** pagina. (CQ-4266572)

* (Alleen JBoss® 7) Wanneer u een upgrade uitvoert van een vorige versie naar AEM 6.5 Forms en de vorige versie processen (.lca) had die een kopie van het standaard verzendings- of standaardinstellingsproces hebben gemaakt en gebruikt, voert HTML5 Forms met dergelijke processen (.lca) de vereiste handelingen niet uit. (CQ-4243928)
* Wanneer een formuliergegevensmodelservice wordt aangeroepen vanuit de regeleditor om de waarden van de afbeeldingskeuzescomponent dynamisch bij te werken, worden de waarden van de afbeeldingskeuzeselectie niet bijgewerkt. (CQ-4254754)
* Het installatieprogramma van AEM Forms Designer vereist de versie met 32 bits van [ Visuele C++ redistributable runtime pakket 2012 ](https://docs.microsoft.com/en-US/cpp/windows/latest-supported-vc-redist?view=msvc-170) en [ Visuele C++ redistributable runtime pakketten 2013 ](https://support.microsoft.com/en-us/topic/update-for-visual-c-2013-and-visual-c-redistributable-package-5b2ac5ab-4139-8acc-08e2-9578ec9b2cf1). Zorg ervoor dat de eerder vermelde herdistribueerbare runtimepakketten zijn geïnstalleerd voordat u de installatie start. (CQ-4265668)

* PDF Generator biedt geen ondersteuning voor verificatie op basis van smartcards. Wanneer een beheerder het Beleid van de Groep `Interactive Logon: Require Smart card` op een server van Vensters toelaat, worden alle bestaande gebruikers van PDF Generator ongeldig gemaakt.

* Wanneer een adaptief formulier is geconfigureerd om de waarden van een component dynamisch bij te werken en het publicatie-exemplaar dat als host fungeert voor het formulier via de Dispatcher, werkt de functionaliteit voor het dynamisch bijwerken van waarden van een veld niet meer. Als u het probleem wilt oplossen, opent u CRXDE in de publicatie-instantie, navigeert u naar `/libs/fd/af/runtime/clientlibs/guideChartReducer` en maakt u de eigenschap die hieronder wordt vermeld.

   * Naam: allowProxy
   * Type: Boolean
   * Waarde: true
   * Beveiligd: Onwaar
   * Verplicht: Onwaar
   * Meerdere: onwaar
   * Automatisch gemaakt: Onwaar

  Met deze eigenschap hebben de clientbibliotheken in de runtimemap toegang tot proxy&#39;s. (CQ-4268679)

* Wanneer AEM Forms wordt gestart, wordt de waarschuwing `SAX Security Manager could not be setup` weergegeven.
* Als u een PDF die is beveiligd met AEM Forms Document Security opent op een Apple iOS of iPadOS met versie 20.10.00 van Adobe Acrobat Reader
* Wanneer u een formulier verzendt met een standaard HTML-uploadveld van een Apple iOS-apparaat, wordt soms de inhoud van het bestand niet verzonden en wordt aan de andere kant een bestand van 0 byte ontvangen. Apple iOS 15.1 biedt een oplossing voor het probleem.

## Productdownload en -ondersteuning (beperkt aantal sites) {#product-download-and-support-restricted-sites}

De volgende sites zijn alleen beschikbaar voor klanten. Neem contact op met uw Adobe-accountmanager als u een klant bent en toegang nodig hebt.

* [ Download van het Product bij licensing.adobe.com ](https://licensing.adobe.com/).

* De updates van het product, de flarden, en de pakketten voor extra functionaliteit op [ Distributie van de Software ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).

* [ de Steun van de Klant via Admin Console ](https://adminconsole.adobe.com/). Voor meer informatie, zie [ Nieuwe Ervaring van de Klantenondersteuning van Adobe ](https://experienceleague.adobe.com/docs/customer-one/using/home.html).
