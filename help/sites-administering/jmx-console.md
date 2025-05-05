---
title: Serverbronnen controleren met de JMX-console
description: Leer hoe u serverbronnen kunt controleren met de JMX-console.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
docset: aem65
exl-id: eabd8335-6140-4c15-8cff-21608719aa5f
solution: Experience Manager, Experience Manager Sites
feature: Developing,Operations
role: Admin
source-git-commit: 305227eff3c0d6414a5ae74bcf3a74309dccdd13
workflow-type: tm+mt
source-wordcount: '4830'
ht-degree: 0%

---

# Serverbronnen controleren met de JMX-console{#monitoring-server-resources-using-the-jmx-console}

Met de JMX-console kunt u services op de CRX-server controleren en beheren. In de volgende secties wordt een overzicht gegeven van de kenmerken en bewerkingen die via het JMX-framework worden weergegeven.

Voor informatie over hoe te om de consolecontroles te gebruiken, zie [ Gebruikend de Console JMX ](#using-the-jmx-console). Voor achtergrondinformatie over JMX, zie de [ pagina van de Uitbreidingen van het Beheer van Java van de Uitbreidingen (JMX) Technologie ](https://www.oracle.com/technetwork/java/javase/tech/javamanagement-140525.html) op de website van het Oracle.

Voor informatie over het creëren van MBans om uw diensten te beheren gebruikend de Console JMX, zie [ Integrerend de Diensten met de Console JMX ](/help/sites-developing/jmx-integration.md).

## Workflowonderhoud {#workflow-maintenance}

Bewerkingen voor het beheren van actieve, voltooide, geschaalde en mislukte workflowinstanties.

* Domein: com.adobe.granite.workflow
* Type: onderhoud

>[!NOTE]
>
>Zie de [ werkschemaconsole ](/help/sites-administering/workflows-administering.md) voor extra werkschemabeleidshulpmiddelen en beschrijvingen van mogelijke statussen van de werkschemainstantie.

### Bewerkingen {#operations}

**listRunningWorkflowsPerModel** maakt een lijst van het aantal werkschemainstanties die voor elk werkschemamodel lopen.

* Argumenten: geen
* Geretourneerde waarde: tabelgegevens met de kolommen Aantal en ModelId.

**listCompletedWorkflowsPerModel** maakt een lijst van het aantal voltooide werkschemainstanties voor elk werkschemamodel.

* Argumenten: geen
* Geretourneerde waarde: tabelgegevens met de kolommen Aantal en ModelId.

**returnWorkflowQueueInfo** Lijsten informatie over werkschemapunten die zijn verwerkt en die voor verwerking een rij worden gevormd.

* Argumenten: geen
* Geretourneerde waarde: tabelgegevens met de volgende kolommen:

   * Taken
   * Naam wachtrij
   * Actieve taken
   * Gemiddelde verwerkingstijd
   * Gemiddelde wachttijd
   * Geannuleerde taken
   * Mislukte taken
   * Voltooide taken
   * Verwerkte banen
   * In de wachtrij geplaatste taken

**returnWorkflowJobTopicInfo** maakt een lijst van verwerkingsinformatie voor werkschemabanen, die door onderwerp worden georganiseerd.

* Argumenten: geen
* Geretourneerde waarde: tabelgegevens met de volgende kolommen:

   * Onderwerpnaam
   * Gemiddelde verwerkingstijd
   * Gemiddelde wachttijd
   * Geannuleerde taken
   * Mislukte taken
   * Voltooide taken
   * Verwerkte banen

**returnFailedWorkflowCount** toont het aantal werkschemainstanties die ontbroken hebben. U kunt een workflowmodel opgeven voor het opvragen of ophalen van informatie voor alle workflowmodellen.

* Argumenten:

   * model: De id van het model waarnaar moet worden gezocht. Als u een aantal mislukte workflowinstanties voor alle workflowmodellen wilt zien, geeft u geen waarde op. De id is het pad naar het modelknooppunt, bijvoorbeeld:

     `/conf/global/settings/workflow/models/dam/update_asset/jcr:content/model`

* Geretourneerde waarde: het aantal mislukte werkstroominstanties.

**returnFailedWorkflowCountPerModel** toont het aantal werkschemainstanties die voor elk werkschemamodel hebben ontbroken.

* Argumenten: geen.
* Geretourneerde waarde: tabelgegevens met de kolommen Aantal en Model-id.

**terminateFailedInstances** beëindigt werkschemainstanties die ontbroken hebben. U kunt alle mislukte exemplaren beëindigen of slechts de ontbroken instanties voor een specifiek model. Desgewenst kunt u de exemplaren opnieuw beginnen nadat zij worden geëindigd. U kunt de bewerking ook testen om de resultaten te zien zonder de bewerking daadwerkelijk uit te voeren.

* Argumenten:

   * Start de instantie opnieuw: (Optioneel) Geef de waarde `true` op om de instanties opnieuw te starten nadat ze zijn beëindigd. De standaardwaarde van `false` zorgt ervoor dat de beëindigde workflowinstanties niet opnieuw worden gestart.
   * Droge uitvoering: (Optioneel) Geef een waarde op van `true` om de resultaten van de bewerking weer te geven zonder de bewerking daadwerkelijk uit te voeren. De standaardwaarde van `false` zorgt dat de bewerking wordt uitgevoerd.
   * Model: (Optioneel) De id van het model waarop de bewerking wordt toegepast. Geef geen model op om de bewerking toe te passen op de mislukte exemplaren van alle workflowmodellen. De id is het pad naar het modelknooppunt, bijvoorbeeld:

     `/conf/global/settings/workflow/models/dam/update_asset/jcr:content/model`

* Geretourneerde waarde: tabelgegevens over de instanties die worden beëindigd, met de volgende kolommen:

   * Initiator
   * InstanceId
   * ModelId
   * Payload
   * StartComment
   * WorkflowTitle

**retryFailedWorkItems** probeert om de stappen van het het werkpunt uit te voeren die ontbroken hebben. U kunt alle mislukte werkitems of alleen de mislukte werkitems voor een specifiek workflowmodel opnieuw proberen. U kunt de bewerking desgewenst testen om de resultaten te zien zonder de bewerking daadwerkelijk uit te voeren.

* Argumenten:

   * Droge uitvoering: (Optioneel) Geef een waarde op van `true` om de resultaten van de bewerking weer te geven zonder de bewerking daadwerkelijk uit te voeren. De standaardwaarde van `false` zorgt dat de bewerking wordt uitgevoerd.
   * Model: (Optioneel) De id van het model waarop de bewerking wordt toegepast. Geef geen model op om de bewerking toe te passen op de mislukte werkitems van alle workflowmodellen. De id is het pad naar het modelknooppunt, bijvoorbeeld:

     `/conf/global/settings/workflow/models/dam/update_asset/jcr:content/model`

* Geretourneerde waarde: tabelgegevens over de mislukte werkitems die opnieuw worden geprobeerd, inclusief de volgende kolommen:

   * Initiator
   * InstanceId
   * ModelId
   * Payload
   * StartComment
   * WorkflowTitle

**PurgeActive** verwijdert actieve werkschemainstanties van een specifieke leeftijd. U kunt actieve exemplaren voor alle modellen of slechts de instanties voor een specifiek model leegmaken. U kunt de bewerking desgewenst testen om de resultaten te zien zonder de bewerking daadwerkelijk uit te voeren.

* Argumenten:

   * Model: (Optioneel) De id van het model waarop de bewerking wordt toegepast. Geef geen model op om de bewerking toe te passen op de workflowinstanties van alle workflowmodellen. De id is het pad naar het modelknooppunt, bijvoorbeeld:

     `/conf/global/settings/workflow/models/dam/update_asset/jcr:content/model`
   * Aantal dagen sinds het begin van de werkstroom: de leeftijd van de werkstroominstanties die moeten worden gewist, in dagen.
   * Droge uitvoering: (Optioneel) Geef een waarde op van `true` om de resultaten van de bewerking weer te geven zonder de bewerking daadwerkelijk uit te voeren. De standaardwaarde van `false` zorgt dat de bewerking wordt uitgevoerd.

* Geretourneerde waarde: tabelgegevens over de actieve werkstroominstanties die worden gewist, inclusief de volgende kolommen:

   * Initiator
   * InstanceId
   * ModelId
   * Payload
   * StartComment
   * WorkflowTitle

**countStaleWorkflows** keert het aantal werkschemainstanties terug die stabiel zijn. U kunt het aantal instanties van de schaal voor alle werkschemamodellen of voor een specifiek model terugwinnen.

* Argumenten:

   * Model: (Optioneel) De id van het model waarop de bewerking wordt toegepast. Geef geen model op om de bewerking toe te passen op de workflowinstanties van alle workflowmodellen. De id is het pad naar het modelknooppunt, bijvoorbeeld:

     `/conf/global/settings/workflow/models/dam/update_asset/jcr:content/model`

* Geretourneerde waarde: het aantal instanties van een schaalworkflow.

**startStaleWorkflows** herstelt de instanties van het stapelwerkschema. U kunt alle instanties van de schaal of slechts de instanties van de schaal voor een specifiek model opnieuw beginnen. U kunt de bewerking ook testen om de resultaten te zien zonder de bewerking daadwerkelijk uit te voeren.

* Argumenten:

   * Model: (Optioneel) De id van het model waarop de bewerking wordt toegepast. Geef geen model op om de bewerking toe te passen op de schaalvarianten van alle workflowmodellen. De id is het pad naar het modelknooppunt, bijvoorbeeld:

     `/conf/global/settings/workflow/models/dam/update_asset/jcr:content/model`
   * Droge uitvoering: (Optioneel) Geef een waarde op van `true` om de resultaten van de bewerking weer te geven zonder de bewerking daadwerkelijk uit te voeren. De standaardwaarde van `false` zorgt dat de bewerking wordt uitgevoerd.

* Geretourneerde waarde: een lijst met werkstroominstanties die opnieuw worden gestart.

**fetchModelList** maakt een lijst van alle werkschemamodellen.

* Argumenten: geen
* Geretourneerde waarde: tabelgegevens die de workflowmodellen identificeren, inclusief de kolommen ModelId en ModelName.

**countRunningWorkflows** keert het aantal werkschemainstanties terug die lopen. U kunt het aantal actieve exemplaren voor alle workflowmodellen of voor een specifiek model ophalen.

* Argumenten:

   * Model: (Optioneel) De id van het model waarvoor het aantal actieve exemplaren wordt geretourneerd. Geef geen model op om het aantal actieve exemplaren van alle workflowmodellen te retourneren. De id is het pad naar het modelknooppunt, bijvoorbeeld:

     `/conf/global/settings/workflow/models/dam/update_asset/jcr:content/model`

* Geretourneerde waarde: het aantal actieve workflowinstanties.

**countCompletedWorkflows** keert het aantal werkschemainstanties terug die worden voltooid. U kunt het aantal voltooide exemplaren ophalen voor alle workflowmodellen of voor een specifiek model.

* Argumenten:

   * Model: (Optioneel) De id van het model waarvoor het aantal voltooide exemplaren wordt geretourneerd. Geef geen model op om het aantal voltooide exemplaren van alle workflowmodellen te retourneren. De id is het pad naar het modelknooppunt, bijvoorbeeld:

     `/conf/global/settings/workflow/models/dam/update_asset/jcr:content/model`

* Geretourneerde waarde: het aantal voltooide workflowinstanties.

**purgeCompleted** verwijdert verslagen van voltooide werkschema&#39;s van een specifieke leeftijd uit de bewaarplaats. Gebruik deze bewerking regelmatig om de grootte van de opslagplaats te minimaliseren wanneer u veel gebruik maakt van workflows. U kunt voltooide exemplaren voor alle modellen of slechts de instanties voor een specifiek model leegmaken. U kunt de bewerking desgewenst testen om de resultaten te zien zonder de bewerking daadwerkelijk uit te voeren.

* Argumenten:

   * Model: (Optioneel) De id van het model waarop de bewerking wordt toegepast. Geef geen model op om de bewerking toe te passen op de workflowinstanties van alle workflowmodellen. De id is het pad naar het modelknooppunt, bijvoorbeeld:

     `/conf/global/settings/workflow/models/dam/update_asset/jcr:content/model`
   * Aantal dagen sinds de werkstroom is voltooid: Het aantal dagen dat de werkstroominstanties de voltooide status hebben.
   * Droge uitvoering: (Optioneel) Geef een waarde op van `true` om de resultaten van de bewerking weer te geven zonder de bewerking daadwerkelijk uit te voeren. De standaardwaarde van `false` zorgt dat de bewerking wordt uitgevoerd.

* Geretourneerde waarde: tabelgegevens over de voltooide werkstroominstanties die worden gewist, inclusief de volgende kolommen:

   * Initiator
   * InstanceId
   * ModelId
   * Payload
   * StartComment
   * WorkflowTitle

## Bewaarplaats {#repository}

Informatie over de CRX-opslagplaats

* Domein: com.adobe.granite
* Type: gegevensopslagruimte

### Attributen {#attributes}

**Naam** De naam van de JCR bewaarplaatsimplementatie. Alleen-lezen.

**Versie** de versie van de opbergimplementatie. Alleen-lezen.

**HomeDir** De folder waar de bewaarplaats wordt gevestigd. De standaardlocatie is &lt;QuickStart_Jar_Location>/crx-quickstart/repository. Alleen-lezen.

**CustomerName** De naam van de klant die de softwarevergunning aan wordt uitgegeven. Alleen-lezen.

**LicenseKey** de unieke vergunningssleutel voor deze installatie van de bewaarplaats. Alleen-lezen.

**AvailableDiskSpace** De schijfruimte die aan dit geval van de bewaarplaats, in Mbytes beschikbaar is. Alleen-lezen.

**MaximumNumberOfOpenFiles** het aantal dossiers die in één keer kunnen worden geopend. Alleen-lezen.

**SessionTracker** de waarde van de het systeemvariabele crx.debug.essies. true geeft een foutopsporingssessie aan. false geeft een normale sessie aan. Lezen/schrijven.

**Beschrijvers** een reeks zeer belangrijke-waardeparen die bewaarplaatseigenschappen vertegenwoordigen. Alle eigenschappen zijn alleen-lezen.

<table>
 <tbody>
  <tr>
   <th>Sleutel</th>
   <th>Waarde</th>
  </tr>
  <tr>
   <td>option.node.and.property.with.same.name.supported</td>
   <td>Geeft aan of een knooppunt en een eigenschap van het knooppunt dezelfde naam kunnen hebben. true geeft aan dat dezelfde namen worden ondersteund, false geeft aan dat dit niet wordt ondersteund. </td>
  </tr>
  <tr>
   <td>identifier.stability</td>
   <td>Geeft de stabiliteit van niet-referentieerbare knooppuntid's aan. De volgende waarden zijn mogelijk:
    <ul>
     <li>identifier.stability.indefinite.duration: Identifiers do not change.</li>
     <li>identifier.stability.method.duration: id's kunnen veranderen tussen methodeaanroepen.</li>
     <li>identifier.stability.save.duration: id's worden niet gewijzigd in een cyclus voor opslaan en vernieuwen.</li>
     <li>identifier.stability.session.duration: id's worden niet gewijzigd tijdens een sessie.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>query.xpath.pos.index</td>
   <td>Geeft aan of de JCR 1.0 XPath-querytaal wordt ondersteund. true geeft ondersteuning aan en false geeft geen ondersteuning aan.</td>
  </tr>
  <tr>
   <td>crx.repository.systemid</td>
   <td>De systeem-id, zoals gevonden in het bestand system.id.</td>
  </tr>
  <tr>
   <td>option.query.sql.supported</td>
   <td>Geeft aan of de JCR 1.0 XPath-querytaal wordt ondersteund. true geeft ondersteuning aan en false geeft geen ondersteuning aan.</td>
  </tr>
  <tr>
   <td>jcr.repository.version</td>
   <td>De versie van de implementatie van de repository.</td>
  </tr>
  <tr>
   <td>option.update.primary.node.type.supported</td>
   <td>Geeft aan of het primaire knooppunttype van een knooppunt kan worden gewijzigd. true geeft aan dat u het primaire knooppunttype kunt wijzigen en false geeft aan dat de wijziging niet wordt ondersteund.</td>
  </tr>
  <tr>
   <td>option.node.type.management.supported</td>
   <td>Geeft aan of knooppunttypebeheer wordt ondersteund. true geeft aan dat dit wordt ondersteund en false geeft aan dat dit niet het geval is.</td>
  </tr>
  <tr>
   <td>node.type.management.overrides.supported</td>
   <td>Geeft aan of u de overgenomen eigenschap of onderliggende knooppuntdefinitie van een knooppunttype kunt overschrijven. true geeft aan dat overschrijvingen worden ondersteund en false geeft aan dat er geen overschrijvingen plaatsvinden.</td>
  </tr>
  <tr>
   <td>option.observation.supported</td>
   <td>true geeft aan dat asynchrone waarneming van wijzigingen in de repository wordt ondersteund. De steun van asynchrone observatie laat toepassingen toe om berichten over elke verandering te ontvangen en te antwoorden aangezien zij voorkomen.</td>
  </tr>
  <tr>
   <td>query.jcrscore</td>
   <td><p>true geeft aan dat de pseudo-eigenschap jcr:score beschikbaar is in XPath en SQL-query's die een jcrfn:contains (in XPath) of CONTAINS (in SQL) functie bevatten om een full-text zoekopdracht uit te voeren.</p> </td>
  </tr>
  <tr>
   <td>option.simple.versioning.supported</td>
   <td>true geeft aan dat de gegevensopslagruimte eenvoudige versioning ondersteunt. Met eenvoudige versioning onderhoudt de repository een sequentiële reeks versies van een knooppunt.</td>
  </tr>
  <tr>
   <td>option.workspace.management.supported</td>
   <td>true geeft aan dat de gegevensopslagruimte het maken en verwijderen van werkruimten met behulp van API's ondersteunt.</td>
  </tr>
  <tr>
   <td>option.update.mixin.node.types.supported</td>
   <td>true geeft aan dat de gegevensopslagruimte de toevoeging en verwijdering van mixinknooppunttypen van een bestaand knooppunt ondersteunt.</td>
  </tr>
  <tr>
   <td>node.type.management.primary.item.name.supported</td>
   <td>true geeft aan dat de repository nodedefinities toestaat om een primair item als onderliggend item te bevatten. Een primair item is toegankelijk via de API zonder de naam van het item te kennen.</td>
  </tr>
  <tr>
   <td>level.2.supported</td>
   <td>true geeft aan dat zowel LEVEL_1_SUPPORTED als OPTION_XML_IMPORT_SUPPORTED true zijn.</td>
  </tr>
  <tr>
   <td>write.supported</td>
   <td>true geeft aan dat de repository schrijftoegang biedt met behulp van de API. false geeft alleen-lezen toegang aan.</td>
  </tr>
  <tr>
   <td>node.type.management.update.in.use.supported</td>
   <td>true geeft aan dat u knooppuntdefinities kunt wijzigen die door bestaande knooppunten worden gebruikt.</td>
  </tr>
  <tr>
   <td>jcr.specification.version</td>
   <td>De versie van de JCR-specificatie die de repository implementeert.</td>
  </tr>
  <tr>
   <td>option.journaled.observation.supported</td>
   <td>true geeft aan dat toepassingen waarnemingen door journalisten van de gegevensopslagruimte kunnen uitvoeren. met journalistieke waarnemingen kan een reeks wijzigingsmeldingen voor een bepaalde periode worden verkregen . </td>
  </tr>
  <tr>
   <td>query.languages</td>
   <td>De querytalen die de gegevensopslagruimte ondersteunt. Geen waarde geeft aan dat er geen query wordt ondersteund.</td>
  </tr>
  <tr>
   <td>option.xml.export.supported</td>
   <td>true geeft aan dat de gegevensopslagruimte het exporteren van knooppunten als XML-code ondersteunt.</td>
  </tr>
  <tr>
   <td>node.type.management.multiple.binary.properties.supported</td>
   <td>true geeft aan dat de gegevensopslagruimte de registratie van knooppunttypen met meerdere binaire eigenschappen ondersteunt. false geeft aan dat één binaire eigenschap wordt ondersteund voor een knooppunttype.</td>
  </tr>
  <tr>
   <td>option.access.control.supported</td>
   <td>true geeft aan dat de gegevensopslagruimte toegangsbeheer ondersteunt, voor het instellen en bepalen van gebruikersrechten voor knooppunttoegang.</td>
  </tr>
  <tr>
   <td>option.baselines.supported</td>
   <td>true geeft aan dat de repository zowel configuraties als basislijnen ondersteunt.</td>
  </tr>
  <tr>
   <td>option.shareable.nodes.supported</td>
   <td>true geeft aan dat de gegevensopslagruimte het maken van deelbare knooppunten ondersteunt.</td>
  </tr>
  <tr>
   <td>crx.cluster.id</td>
   <td>De id van de opslagcluster.</td>
  </tr>
  <tr>
   <td>query.stored.queries.supported</td>
   <td>true geeft aan dat de opslagplaats opgeslagen query's ondersteunt.</td>
  </tr>
  <tr>
   <td>query.full.text.search.supported</td>
   <td>true geeft aan dat de gegevensopslagruimte zoeken in volledige tekst ondersteunt.</td>
  </tr>
  <tr>
   <td>node.type.management.inheritance</td>
   <td><p>Geeft het niveau van opslagruimteondersteuning voor overerving van knooppunttypen aan. De volgende waarden zijn mogelijk:</p> <p>node.type.management.inheritance.minimum: de registratie van de types van primaire knoop is beperkt tot die die slechts niet:base als supertype hebben. Registratie van typen mixinknooppunten is beperkt tot knooppunten zonder supertype.</p> <p>node.type.management.inheritance.single: Registratie van typen primaire knooppunten is beperkt tot knooppunten met één supertype. Registratie van typen mixinknooppunten is beperkt tot knooppunten met ten hoogste één supertype.</p> <p><br /> node.type.management.inheritance.multiple: de primaire knooppunttypes kunnen met één of meerdere supertypes worden geregistreerd. Mixinknooptypen kunnen met nul of meer supertypen worden geregistreerd.</p> </td>
  </tr>
  <tr>
   <td>crx.cluster.preferredMaster</td>
   <td>true geeft aan dat dit clusterknooppunt de voorkeursmaster van de cluster is.</td>
  </tr>
  <tr>
   <td>option.transactions.supported</td>
   <td>true geeft aan dat de gegevensopslagruimte transacties ondersteunt.</td>
  </tr>
  <tr>
   <td>jcr.repository.vendor.url</td>
   <td>De URL van de leverancier van de opslagplaats.</td>
  </tr>
  <tr>
   <td>node.type.management.value.constraints.supported</td>
   <td>true geeft aan dat de gegevensopslagruimte waardebeperkingen voor knooppunteigenschappen ondersteunt.</td>
  </tr>
  <tr>
   <td>node.type.management.property.types</td>
   <td>een array van javax.jcr.PropertyType-constanten die de eigenschapstypen vertegenwoordigen die een geregistreerd knooppunttype kan opgeven. Een array met lengte nul geeft aan dat geen eigenschapdefinities kunnen worden opgegeven voor geregistreerde knooppunttypen. Eigenschapstypen zijn STRING, URI, BOOLEAN, LONG, DUBBEL, DECIMAAL, BINARY, DATE, NAME, PAD, WEAKREFERENCE, REFERENCE en UNDEFINED (indien ondersteund)</td>
  </tr>
  <tr>
   <td>node.type.management.orderable.child.nodes.supported</td>
   <td>true geeft aan dat de opslagplaats het behoud van de volgorde van onderliggende knooppunten ondersteunt.</td>
  </tr>
  <tr>
   <td>jcr.repository.vendor</td>
   <td>De naam van de leverancier van de opslagplaats.</td>
  </tr>
  <tr>
   <td>query.joins</td>
   <td><p>Het niveau van steun voor verbindingen in vragen. De volgende waarden zijn mogelijk:</p>
    <ul>
     <li>query.joins.none: geen ondersteuning voor verbindingen. Voor query's kan één kiezer worden gebruikt.</li>
     <li>query.joins.inner: Ondersteuning voor binnenverbindingen.</li>
     <li>query.joins.inner.outer: Ondersteuning voor binnenste en buitenste verbindingen.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>org.apache.jackrabbit.spi.commons.AdditionalEventInfo</td>
   <td> </td>
  </tr>
  <tr>
   <td>query.xpath.doc.order</td>
   <td>true geeft aan dat de opslagplaats de querytaal XPath 1.0 ondersteunt.</td>
  </tr>
  <tr>
   <td>query.jcrpath</td>
   <td> </td>
  </tr>
  <tr>
   <td>option.xml.import.supported</td>
   <td>true geeft aan dat de repository het importeren van XML-code als inhoud ondersteunt.</td>
  </tr>
  <tr>
   <td>node.type.management.same.name.siblings.supported</td>
   <td>true geeft aan dat de gegevensopslagruimte knooppunten op hetzelfde niveau (knooppunten met dezelfde bovenliggende knooppunten) met dezelfde naam ondersteunt.</td>
  </tr>
  <tr>
   <td>node.type.management.residual.definitions.supported</td>
   <td>true geeft aan dat de gegevensopslagruimte naameigenschappen met residuele definities ondersteunt. Als dit wordt ondersteund, kan het kenmerk name van een itemdefinitie een sterretje ("*") zijn.</td>
  </tr>
  <tr>
   <td>node.type.management.autocreated.definitions.supported</td>
   <td>true geeft aan dat de gegevensopslagruimte het automatisch maken van onderliggende items (knooppunten of eigenschappen) van een knooppunt ondersteunt wanneer het knooppunt wordt gemaakt.</td>
  </tr>
  <tr>
   <td>crx.cluster.master</td>
   <td>true geeft aan dat dit opslagruimteknooppunt het hoofdknooppunt van de cluster is.</td>
  </tr>
  <tr>
   <td>level.1.supported</td>
   <td>true geeft aan dat option.xml.export.support true is en query.languages niet-lengte nul is.</td>
  </tr>
  <tr>
   <td>option.unfiled.content.supported</td>
   <td>true geeft aan dat de gegevensopslagruimte niet-gearchiveerde inhoud ondersteunt. knooppunten zonder veld maken geen deel uit van de hiërarchie van de opslagplaats.</td>
  </tr>
  <tr>
   <td>jcr.specification.name</td>
   <td>De naam van de JCR-specificatie die de gegevensopslagruimte implementeert.</td>
  </tr>
  <tr>
   <td>option.versioning.supported</td>
   <td>true geeft aan dat de gegevensopslagruimte volledige versioning ondersteunt.</td>
  </tr>
  <tr>
   <td>jcr.repository.name</td>
   <td>De naam van de gegevensopslagruimte.</td>
  </tr>
  <tr>
   <td>option.locking.supported</td>
   <td>true geeft aan dat de repository het vergrendelen van knooppunten ondersteunt. Door vergrendeling kan de gebruiker tijdelijk voorkomen dat andere gebruikers wijzigingen aanbrengen.</td>
  </tr>
  <tr>
   <td>jcr.repository.version.display</td>
   <td> </td>
  </tr>
  <tr>
   <td>option.activities.supported</td>
   <td>true geeft aan dat de gegevensopslagruimte activiteiten ondersteunt. Activiteiten zijn een set wijzigingen die worden uitgevoerd in een werkruimte die wordt samengevoegd in een andere werkruimte.</td>
  </tr>
  <tr>
   <td>node.type.management.multivalued.properties.supported</td>
   <td>true geeft aan dat de gegevensopslagruimte knoopeigenschappen ondersteunt die nul of meer waarden kunnen hebben.</td>
  </tr>
  <tr>
   <td>option.retention.supported</td>
   <td>true geeft aan dat de opslagplaats het gebruik van externe toepassingen voor retentiebeheer ondersteunt om retentiebeleid toe te passen op inhoud en ondersteuning biedt voor bewaring en vrijgave.</td>
  </tr>
  <tr>
   <td>option.lifecycle.supported</td>
   <td>true geeft aan dat de opslagplaats levenscyclusbeheer ondersteunt.</td>
  </tr>
 </tbody>
</table>

**WorkspaceNames** De namen van de werkruimten in de bewaarplaats. Alleen-lezen.

**DataStoreGarbageCollectionDelay** De hoeveelheid tijd in milliseconden die de huisvuilinzameling na het aftasten van elke tiende knoop slaapt. Lezen/schrijven.

**BackupDelay** de hoeveelheid tijd in milliseconden dat het reserveproces tussen elke stap van de steun stroomt. Lezen/schrijven.

**BackupInProgress** De waarde van waar wijst op dat een reserveproces uitvoert. Alleen-lezen.

**BackupProgress** voor de huidige steun, het percentage van alle dossiers die zijn gesteund. Alleen-lezen.

**CurrentBackupTarget** voor de huidige steun, het dossier van het ZIP waar de reservedossiers worden opgeslagen. Als er geen back-up wordt gemaakt, wordt er geen waarde weergegeven. Alleen-lezen.

**BackupIsSuccessful** Een waarde van waar wijst erop dat geen fouten tijdens de huidige steun zijn voorgekomen, of geen steun lopend is. false geeft aan dat er een fout is opgetreden tijdens de huidige back-up. Alleen-lezen.

**BackupResult** De status van de huidige steun. De volgende waarden zijn mogelijk:

* Back-up wordt uitgevoerd: er wordt momenteel een back-up uitgevoerd.
* Back-up geannuleerd: de back-up is geannuleerd.
* Back-up voltooid met fout: er is een fout opgetreden tijdens de back-up. Het foutbericht bevat informatie over de oorzaak.
* Back-up voltooid: de back-up is gelukt.
* Er is tot nu toe geen back-up uitgevoerd: er is geen back-up bezig.

Alleen-lezen.

**TarOptimizationRunningSince** De tijd waarop het huidige proces van de het dossieroptimalisering van TAR begon. Alleen-lezen.

**TarOptimizationDelay** De hoeveelheid tijd in milliseconden dat het proces van de optimalisering van TAR tussen elke stap van het proces slaagt. Lezen/schrijven.

**ClusterProperties** een reeks sleutel-waarde paren die clustereigenschappen en waarden vertegenwoordigen. Elke rij in de tabel vertegenwoordigt een clustereigenschap. Alleen-lezen.

**ClusterNodes** De leden van de bewaarplaatscluster.

**ClusterId** Het herkenningsteken van deze bewaarplaatscluster. Alleen-lezen.

**ClusterMasterId** Het herkenningsteken van de hoofdknoop van deze bewaarplaatscluster. Alleen-lezen.

**ClusterNodeId** Het herkenningsteken van deze knoop van de bewaarplaatscluster. Alleen-lezen.

### Bewerkingen {#operations-1}

**createWorkspace** creeert een werkruimte in deze bewaarplaats.

* Argumenten:

   * name: Een tekenreekswaarde die de naam van de nieuwe werkruimte vertegenwoordigt.

* Geretourneerde waarde: geen

**runDataStoreGarbageCollection** voert huisvuilinzameling op de gegevensopslagplaatsen uit.

* Argumenten:

   * delete: Een Booleaanse waarde die aangeeft of ongebruikte opslagplaats-items moeten worden verwijderd. De waarde true zorgt ervoor dat ongebruikte knooppunten en eigenschappen worden verwijderd. Bij de waarde false worden alle knooppunten gescand, maar worden geen knooppunten verwijderd.

* Geretourneerde waarde: geen

**stopDataStoreGarbageCollection** Stopt een lopende inzameling van het huisvuil van de gegevensopslag.

* Argumenten: geen
* Geretourneerde waarde: tekenreeksrepresentatie van huidige status

**startBackup** maakt een back-up van gegevens in een ZIP-bestand.

* Argumenten:

   * `target`: (Optioneel) Een `String` -waarde die de naam vertegenwoordigt van het ZIP-bestand of de ZIP-map waarin de gegevens van de gegevensopslagruimte moeten worden gearchiveerd. Als u een ZIP-bestand wilt gebruiken, neemt u de bestandsnaamextensie ZIP op. Als u een map wilt gebruiken, neemt u geen bestandsnaamextensie op.

     Om een stijgende steun uit te voeren, specificeer de folder die eerder voor de steun werd gebruikt.

     U kunt een absoluut of relatief pad opgeven. Relatieve paden zijn relatief ten opzichte van de bovenliggende map van de map crx-quickstart.

     Wanneer u geen waarde opgeeft, wordt de standaardwaarde `backup-currentdate.zip` gebruikt, waarbij `currentdate` de notatie `yyyyMMdd-HHmm` heeft.

* Geretourneerde waarde: geen

**cancelBackup** stopt het huidige reserveproces en schrapt het tijdelijke archief dat het proces voor het archiveren gegevens werd gecreeerd.

* Argumenten: geen
* Geretourneerde waarde: geen

**blockRepositoryWrites** De veranderingen van Blokken in de gegevensopslagplaats. Alle back-uplisteners van de opslagplaats worden op de hoogte gesteld van het blok.

* Argumenten: geen
* Geretourneerde waarde: geen

**unblockRepositoryWrites** verwijdert het blok uit de bewaarplaats. Alle back-uplisteners van de opslagplaats worden op de hoogte gesteld van de blokverwijdering.

* Argumenten: geen
* Geretourneerde waarde: geen

**startTarOptimization** begint het proces van de het dossieroptimalisering van TAR gebruikend de standaardwaarde voor tarOptimizationDelay.

* Argumenten: geen
* Geretourneerde waarde: geen

**stopTarOptimization** stopt de optimalisering van het het dossierdossier van TAR.

* Argumenten: geen
* Geretourneerde waarde: geen

**tarIndexMerge** voegt de hoogste indexdossiers van alle reeksen TAR samen. De bovenste indexbestanden zijn bestanden met verschillende hoofdversies. De volgende bestanden worden bijvoorbeeld samengevoegd in het bestand index_3_1.tar: index_1_1.tar, index_2_0.tar, index_3_0.tar. De samengevoegde bestanden worden verwijderd (in het vorige voorbeeld worden index_1_1.tar, index_2_0.tar en index_3_0.tar verwijderd).

* Argumenten:

   * `background`: Een Booleaanse waarde die aangeeft of de bewerking op de achtergrond moet worden uitgevoerd, zodat de webconsole tijdens de uitvoering bruikbaar is. De waarde true voert de bewerking op de achtergrond uit.

* Geretourneerde waarde: geen

**wordtClusterMaster** plaatst deze gegevensopslaggegevensopslagknoop als hoofdknoop van de cluster. Als deze opdracht nog niet het hoofdniveau heeft, wordt de listener van de huidige hoofdinstantie gestopt en wordt een hoofdlistener op het huidige knooppunt gestart. Dit knooppunt wordt vervolgens ingesteld als het hoofdknooppunt en wordt opnieuw opgestart, waardoor alle andere knooppunten in de cluster (dat wil zeggen die welke door de master worden gecontroleerd) verbinding maken met deze instantie.

* Argumenten: geen
* Geretourneerde waarde: geen

**joinCluster** voegt deze bewaarplaats aan een cluster als knoop toe die door de clustermeester wordt gecontroleerd. Geef een gebruikersnaam en wachtwoord op voor verificatiedoeleinden. De verbinding gebruikt basisauthentificatie. De beveiligingsreferenties zijn base-64 gecodeerd voordat ze naar de server worden verzonden.

* Argumenten:

   * `master`: Een tekenreekswaarde die het IP-adres of de computernaam vertegenwoordigt van de computer waarop het knooppunt van de hoofdopslagplaats wordt uitgevoerd.
   * `username`: de naam die moet worden gebruikt voor verificatie met de cluster.
   * `password`: Het wachtwoord voor verificatie.

* Geretourneerde waarde: geen

**traversalCheck** reizen en naar keuze moeilijke inconsistenties in een subtree die bij een specifieke knoop begint. Dit wordt uitvoerig besproken in de documentatie over persistentiemanagers.

**Controles 0&rbrace; ConsistentCheck &lbrace;en naar keuze fixes consistentie in de Datastore.** Dit wordt uitvoerig besproken in de documentatie op de Datastore.

## Statistieken opslagplaats (TimeSeries) {#repository-statistics-timeseries}

De waarde van het veld TimeSeries voor elk statistisch type dat `org.apache.jackrabbit.api.stats.RepositoryStatistics` definieert.

* Domein: `com.adobe.granite`
* Type: `TimeSeries`
* Naam: een van de volgende waarden uit de klasse `org.apache.jackrabbit.api.stats.RepositoryStatistics.Type` Enum:

   * BUNDLE_CACHE_ACCESS_COUNTER
   * BUNDLE_CACHE_MISS_AVERAGE
   * BUNDLE_CACHE_MISS_COUNTER
   * BUNDLE_CACHE_MISS_DURATION
   * BUNDLE_CACHE_SIZE_COUNTER
   * BUNDLE_COUNTER
   * BUNDLE_READ_COUNTER
   * BUNDLE_WRITE_AGE
   * BUNDLE_WRITE_COUNTER
   * BUNDLE_WRITE_DURATION
   * BUNDLE_WS_SIZE_COUNTER
   * QUERY_AVERAGE
   * QUERY_COUNT
   * QUERY_DURATION
   * SESSION_COUNT
   * SESSION_LOGIN_COUNTER
   * SESSION_READ_AVERAGE
   * SESSION_READ_COUNTER
   * SESSION_READ_DURATION
   * SESSION_WRITE_AVERAGE
   * SESSION_WRITE_COUNTER
   * SESSION_WRITE_DURATION

### Attributen {#attributes-1}

De volgende eigenschappen worden verstrekt voor elk statistisch type dat wordt gerapporteerd:

* ValuePerSecond: de gemeten waarde per seconde gedurende de laatste minuut. Alleen-lezen.
* ValuePerMinute: de gemeten waarde per minuut gedurende het laatste uur. Alleen-lezen.
* ValuePerHour: de gemeten waarde per uur gedurende de laatste week. Alleen-lezen.
* ValuePerWeek: de gemeten waarde per week gedurende de laatste drie jaar. Alleen-lezen.

## Query-statistische gegevens opslagplaats {#repository-query-stats}

Statistische informatie over query&#39;s in de gegevensopslagruimte.

* Domein: com.adobe.granite
* Type: QueryState

### Attributen {#attributes-2}

**SlowQueries** Informatie over de bewaarplaatscequery&#39;s die de langste tijd hebben genomen om te voltooien. Alleen-lezen.

**SlowQueriesQueueSize** Het maximumaantal vragen om in de lijst te omvatten SlowQueries. Lezen.

**PopularQueries** Informatie over de bewaarplaatscequery&#39;s die het meest voorkwamen. Alleen-lezen.

**PopularQueriesQueueSize** Het maximumaantal vragen in de lijst PopularQueries. Lezen.

### Bewerkingen {#operations-2}

**clearSlowQueriesQueue** verwijdert alle vragen uit de lijst SlowQueries.

* Argumenten: geen
* Geretourneerde waarde: geen

**clearPopularQueriesQueue** verwijdert alle vragen uit de lijst PopularQueries.

* Argumenten: geen
* Geretourneerde waarde: geen

## Replication Agents {#replication-agents}

Controleer de diensten voor elke replicatieagent. Wanneer u een replicatieagent creeert, verschijnt de dienst automatisch in de console JMX.

* **Domein:** com.adobe.granite.replication
* **Type:** agent
* **Naam:** geen waarde
* **Eigenschappen:** &lbrace;id= &quot;*Naam*&quot;, waar *Naam* de waarde van het bezit van de Naam van de agent is.

### Attributen {#attributes-3}

**Identiteitskaart** een waarde van het Koord die het herkenningsteken van de configuratie van de replicatieagent vertegenwoordigt. De veelvoudige agenten kunnen de zelfde configuratie gebruiken. Alleen-lezen.

**Geldige** een booleaanse waarde die erop wijst of de agent correct wordt gevormd:

* `true`: geldige configuratie.
* `false` : de configuratie bevat fouten.

Alleen-lezen.

**Toegelaten** een booleaanse waarde die erop wijst of de agent wordt toegelaten:

* `true`: Ingeschakeld.
* `false`: Uitgeschakeld.

**QueueBlocked** een booleaanse waarde die erop wijst of de rij bestaat en wordt geblokkeerd:

* `true`: geblokkeerd. Er is een automatisch opnieuw proberen in behandeling.
* `false`: niet geblokkeerd of bestaat niet.

Alleen-lezen.

**QueuePaused** een booleaanse waarde die erop wijst of de baanrij wordt gepauzeerd:

* `true`: Gepauzeerd (opgeschort)
* `false`: Niet gepauzeerd of bestaat niet.

Lezen.

**QueueNumEnapters** een int. waarde die het aantal banen in de agentenrij vertegenwoordigt. Alleen-lezen.

**QueueStatusTime** Een waarde van de Datum die op de tijd op de server wijst toen de getoonde statuswaarden werden verkregen. De waarde komt overeen met de tijd waarop de pagina is geladen. Alleen-lezen.

**QueueNextRetryTime** voor geblokkeerde rijen, een waarde van de Datum die erop wijst wanneer volgende automatisch opnieuw probeert voorkomt. Als er geen tijd wordt weergegeven, wordt de wachtrij niet geblokkeerd. Alleen-lezen.

**QueueProcessingSince** een waarde van de Datum die erop wijst wanneer de verwerking voor de huidige baan begon. Wanneer er geen tijd wordt weergegeven, wordt de wachtrij geblokkeerd of inactief. Alleen-lezen.

**QueueLastProcessTime** Een waarde van de Datum die erop wijst toen de vorige baan werd voltooid. Alleen-lezen.

### Bewerkingen {#operations-3}

**queueForceRetry** voor geblokkeerde rijen, geeft het opnieuw proberen bevel aan de rij uit.

* Argumenten: geen
* Geretourneerde waarde: geen

**queueClear** verwijdert alle banen uit de rij.

* Argumenten: geen
* Geretourneerde waarde: geen

## Sling Engine {#sling-engine}

Verstrekt statistieken over HTTP- verzoeken zodat u de prestaties van de dienst kunt controleren SlingRequestProcessor.

* Domein: org.apache.sling
* Type: motor
* Eigenschappen: {service=RequestProcessor}

### Attributen {#attributes-4}

**RequestsCount** Het aantal verzoeken die zijn voorgekomen sinds de statistieken het laatst teruggesteld werden.

**MinRequestDurationMsec** De kortste hoeveelheid tijd (in milliseconden) die werd vereist om een verzoek te verwerken aangezien de statistieken het laatst werden teruggesteld.

**MaxRequestDurationMsec** De langste hoeveelheid tijd (in milliseconden) die werd vereist om een verzoek te verwerken aangezien de statistieken het laatst teruggesteld werden.

**StandardDeviationDurationMsec** De standaardafwijking van de hoeveelheid tijd die werd vereist om verzoeken te verwerken. De standaardafwijking wordt berekend gebruikend alle verzoeken aangezien de statistieken het laatst werden teruggesteld.

**MeanRequestDurationMsec** De gemiddelde hoeveelheid tijd die werd vereist om een verzoek te verwerken. Het gemiddelde wordt berekend aan de hand van alle aanvragen sinds de statistieken voor het laatst zijn ingesteld

### Bewerkingen {#operations-4}

**resetStatistics** plaatst alle statistieken aan nul. Herstel de statistieken wanneer u de prestaties van de verzoekverwerking tijdens een specifiek tijdkader moet analyseren.

* Argumenten: geen
* Geretourneerde waarde: geen

**identiteitskaart** De vertegenwoordiging van het Koord van pakketidentiteitskaart

**geïnstalleerd** een booleaanse waarde die erop wijst of het pakket geïnstalleerd is:

* `true`: geïnstalleerd.
* `false`: niet geïnstalleerd.

**installedBy** identiteitskaart van de gebruiker die het pakket het laatst installeerde.

**installedDate** de datum toen het pakket het laatst werd geïnstalleerd.

**grootte** een lange waarde die de grootte van het pakket in bytes houdt.


## QuickStart Launcher {#quickstart-launcher}

Informatie over het opstartproces en de QuickStart-starter.

* Domein: com.adobe.granite.quickstart
* Type: Launcher

### Bewerkingen {#operations-5}

**logboek**

Toont een bericht in het QuickStart venster.

Argumenten:

* p1: Een `String` -waarde die het bericht vertegenwoordigt dat moet worden weergegeven.
* Geretourneerde waarde: geen

**startFinished**

Roept de opstartenFinished methode van de serverlancerer. De methode probeert de welkomstpagina in een webbrowser te openen.

* Argumenten: geen
* Geretourneerde waarde: geen

**startupProgress**

Hiermee wordt de voltooiingswaarde van het opstartproces van de server ingesteld. De voortgangsbalk in het QuickStart-venster vertegenwoordigt de voltooiingswaarde.

* Argumenten:
   * p1: Een drijvende-kommawaarde die aangeeft hoeveel van het opstartproces is voltooid, als een breuk. De waarde moet liggen tussen nul en één. 0,3 geeft bijvoorbeeld aan dat 30% is voltooid.
* Geretourneerde waarde: geen.

## Services van derden {#third-party-services}

Verschillende serverbronnen van derden installeren MBans die kenmerken en bewerkingen aan de JMX-console beschikbaar maken. De volgende lijst maakt een lijst van de derdemiddelen en verstrekt verbindingen aan meer informatie.

<table>
 <tbody>
  <tr>
   <th>Domein</th>
   <th>Type</th>
   <th>MBean Class</th>
  </tr>
  <tr>
   <td>JMImplementation</td>
   <td>MBeanServerDelegate</td>
   <td><a href="https://docs.oracle.com/javase/8/docs/api/javax/management/MBeanServerDelegate.html">javax.management.MBeanServerDelegate</a></td>
  </tr>
  <tr>
   <td>com.sun.management</td>
   <td>HotSpotDiagnostic</td>
   <td><a href="https://docs.oracle.com/javase/8/docs/jre/api/management/extension/com/sun/management/HotSpotDiagnosticMXBean.html">com.sun.management.HotSpotDiagnosticMXBean</a></td>
  </tr>
  <tr>
   <td>java.lang</td>
   <td>
    <ul>
     <li>ClassLoading</li>
     <li>Compilatie</li>
     <li>GarbageCollector</li>
     <li>Geheugen</li>
     <li>MemoryManager</li>
     <li>MemoryPool</li>
     <li>Besturingssysteem</li>
     <li>Runtime</li>
     <li>Verbindingen</li>
    </ul> </td>
   <td><a href="https://docs.oracle.com/javase/8/docs/api/javax/management/package-summary.html"> javax.management </a> pakket</td>
  </tr>
  <tr>
   <td>java.util.logging</td>
   <td> </td>
   <td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/logging/LoggingMXBean.html">java.util.logging.LoggingMXBean</a></td>
  </tr>
  <tr>
   <td>osgi.core</td>
   <td>
    <ul>
     <li>bundleState</li>
     <li>kader</li>
     <li>packageState</li>
     <li>serviceState</li>
    </ul> </td>
   <td><a href="https://osgi.org/specification/osgi.enterprise/7.0.0/service.jmx.html#d0e42567"> org.osgi.jmx.framework </a> pakket</td>
  </tr>
 </tbody>
</table>

## De JMX-console gebruiken {#using-the-jmx-console}

In de JMX-console wordt informatie weergegeven over verschillende services die op de server worden uitgevoerd:

* Attributen: Service-eigenschappen zoals configuraties of runtime-gegevens. Kenmerken kunnen alleen-lezen of lezen-schrijven zijn.
* Bewerkingen: opdrachten die u op de service kunt aanroepen.

MBeans die met de dienst OSGi worden opgesteld stelt de dienstattributen en verrichtingen aan de console bloot. De MBean bepaalt de attributen en de verrichtingen die worden blootgesteld, en of de attributen read-only of read-write zijn.

De belangrijkste pagina van de console JMX omvat een lijst van de diensten. Elke rij in de lijst vertegenwoordigt de dienst die door een MBean wordt blootgesteld.

1. Open de webconsole en klik op het tabblad JMX. ([ http://localhost:4502/system/console/jmx](http://localhost:4502/system/console/jmx))
2. Klik een celwaarde voor de dienst om de attributen en de verrichtingen voor de dienst te zien.
3. Als u een kenmerkwaarde wilt wijzigen, klikt u op de waarde, geeft u de waarde op in het dialoogvenster dat verschijnt en klikt u op Opslaan.
4. Als u een servicebewerking wilt aanroepen, klikt u op de naam van de bewerking, geeft u in het dialoogvenster argumentwaarden op en klikt u op Invoke.

## Externe JMX-toepassingen gebruiken voor bewaking {#using-external-jmx-applications-for-monitoring}

CRX staat externe toepassingen toe om met Beheerde Bonen (MBeans) via [ de Uitbreidingen van het Beheer van Java (JMX) ](https://docs.oracle.com/javase/6/docs/technotes/guides/management/overview.html) in wisselwerking te staan. Gebruikend generische consoles zoals [ JConsole ](https://java.sun.com/developer/technicalArticles/J2SE/jconsole.html) of domein-specifieke controletoepassingen, staat het krijgen en het plaatsen van de configuraties en eigenschappen van CRX, en de controle van prestaties en middelgebruik toe.

### Verbinding maken met CRX via JConsole {#using-jconsole-to-connect-to-crx}

Ga als volgt te werk om verbinding te maken met CRX met behulp van JConsole:

1. Open een terminalvenster.
1. Voer de volgende opdracht in:

   `jconsole`

JConsole wordt gestart en het JConsole-venster wordt weergegeven.

### Verbinding maken met een lokaal CRX-proces {#connecting-to-a-local-crx-process}

JConsole zal een lijst van lokale processen van de Virtuele Machine van Java tonen. De lijst bevat twee snelstartprocessen. Selecteer het &#39;KINDERproces&#39; in de lijst met lokale processen (meestal het proces met de hogere PID).

![ screen_shot_2012-03-26at114557am ](assets/screen_shot_2012-03-26at114557am.png)

### Verbinding maken met een CRX-proces op afstand {#connecting-to-a-remote-crx-process}

Als u verbinding wilt maken met een extern CRX-proces, moet de JVM die het externe CRX-proces host, zijn ingeschakeld voor het accepteren van externe JMX-verbindingen.

Om externe JMX-verbindingen in te schakelen, moet de volgende systeemeigenschap worden ingesteld bij het starten van de JVM:

`com.sun.management.jmxremote.port=portNum`

In de eigenschap hierboven is `portNum` het poortnummer waarmee u JMX RMI-verbindingen wilt inschakelen. Ben zeker om een ongebruikt havenaantal te specificeren. Naast het publiceren van een schakelaar RMI voor lokale toegang, publiceert het plaatsen van dit bezit een extra schakelaar RMI in een privé read-only register bij de gespecificeerde haven gebruikend een bekende naam, &quot;jmxrmi&quot;.

Wanneer u de JMX-agent inschakelt voor externe controle, gebruikt deze standaard wachtwoordverificatie op basis van een wachtwoordbestand dat moet worden opgegeven met de volgende systeemeigenschap bij het starten van de Java VM:

`com.sun.management.jmxremote.password.file=pwFilePath`

Zie de [ relevante documentatie JMX ](https://docs.oracle.com/javase/6/docs/technotes/guides/management/agent.html) voor gedetailleerde instructies bij vestiging een wachtwoorddossier.

Voorbeeld:

```shell
$ java
  -Dcom.sun.management.jmxremote.password.file=pwFilePath
  -Dcom.sun.management.jmxremote.port=8463
  -jar ./cq-quickstart.jar
```

### De MBans van CRX gebruiken {#using-the-mbeans-provided-by-crx}

Nadat u verbinding hebt gemaakt met het quickstart-proces, biedt JConsole een reeks algemene controlemiddelen voor de JVM waarin CRX wordt uitgevoerd.

![ screen_shot_2012-03-26at115056am ](assets/screen_shot_2012-03-26at115056am.png)

Om tot CRX toegang te hebben intern controle en configuratieopties, ga naar het lusje MBans, en van de hiërarchische inhoudsboom op de linkerzijde, selecteer de sectie van Attributen of van Verrichtingen die u geinteresseerd bent in. Bijvoorbeeld de sectie com.adobe.granite/Repository/Operations.

Selecteer in die sectie het gewenste kenmerk of de gewenste bewerking in het linkerdeelvenster.

![ screen_shot_2012-03-26at115728am ](assets/screen_shot_2012-03-26at115728am.png)
