---
title: Serverbronnen controleren met de JMX-console
seo-title: Serverbronnen controleren met de JMX-console
description: Leer hoe u serverbronnen kunt controleren met de JMX-console.
seo-description: Leer hoe u serverbronnen kunt controleren met de JMX-console.
uuid: 0a28aafe-61b2-472b-8f8f-2cd6540cbfee
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: 873ce073-0055-4e1b-b3c6-ae7967700894
docset: aem65
translation-type: tm+mt
source-git-commit: 97c93a95cd7fe63b306d80fe127388a209b727c7
workflow-type: tm+mt
source-wordcount: '4974'
ht-degree: 0%

---


# De Middelen van de Server van de controle die JMX Console{#monitoring-server-resources-using-the-jmx-console} gebruiken

Met de JMX-console kunt u services op de CRX-server controleren en beheren. In de volgende secties wordt een overzicht gegeven van de kenmerken en bewerkingen die via het JMX-framework worden weergegeven.

Voor informatie over hoe te om de consolecontroles te gebruiken, zie [Gebruikend de Console JMX](#using-the-jmx-console). Raadpleeg de pagina [Java Management Extensions (JMX) Technology](https://www.oracle.com/technetwork/java/javase/tech/javamanagement-140525.html) op de Oracle-website voor achtergrondinformatie over JMX.

Zie [Services integreren met de JMX-console](/help/sites-developing/jmx-integration.md) voor informatie over het maken van MBeans om uw services te beheren met de JMX-console.

## Workflowonderhoud {#workflow-maintenance}

Bewerkingen voor het beheren van actieve, voltooide, geschaalde en mislukte workflowinstanties.

* Domein: com.adobe.granite.workflow
* Type: Onderhoud

>[!NOTE]
>
>Zie de [workflowconsole](/help/sites-administering/workflows-administering.md) voor aanvullende tools voor workflowbeheer en beschrijvingen van mogelijke statussen van workflowinstanties.

### Bewerkingen {#operations}

**** listRunningWorkflowsPerModelList geeft het aantal werkstroominstanties weer dat wordt uitgevoerd voor elk workflowmodel.

* Argumenten: none
* Geretourneerde waarde: Tabelgegevens met de kolommen Aantal en ModelId.

**** listCompletedWorkflowsPerModelHiermee geeft u het aantal voltooide workflowinstanties voor elk workflowmodel weer.

* Argumenten: none
* Geretourneerde waarde: Tabelgegevens met de kolommen Aantal en ModelId.

**** returnWorkflowQueueInfoLists informatie over werkschemapunten die zijn verwerkt en die voor verwerking een rij worden gevormd.

* Argumenten: none
* Geretourneerde waarde: Tabelgegevens met de volgende kolommen:

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

**** returnWorkflowJobTopicInfoLists verwerkingsinformatie voor werkstroombanen, georganiseerd door onderwerp.

* Argumenten: none
* Geretourneerde waarde: Tabelgegevens met de volgende kolommen:

   * Onderwerpnaam
   * Gemiddelde verwerkingstijd
   * Gemiddelde wachttijd
   * Geannuleerde taken
   * Mislukte taken
   * Voltooide taken
   * Verwerkte banen

**** returnFailedWorkflowCountHiermee wordt het aantal mislukte werkstroominstanties weergegeven. U kunt een workflowmodel opgeven voor het opvragen of ophalen van informatie voor alle workflowmodellen.

* Argumenten:

   * model: De id van het model waarop moet worden gezocht. Als u een aantal mislukte workflowinstanties voor alle workflowmodellen wilt zien, geeft u geen waarde op. De id is het pad naar het modelknooppunt, bijvoorbeeld:

      `/conf/global/settings/workflow/models/dam/update_asset/jcr:content/model`

* Geretourneerde waarde: Het aantal mislukte werkstroominstanties.

**** returnFailedWorkflowCountPerModelToont het aantal werkschemainstanties die voor elk werkschemamodel hebben ontbroken.

* Argumenten: geen.
* Geretourneerde waarde: Tabelgegevens met de kolommen Aantal en Model-id.

**Workflowinstanties** terminateFailedInstancesTerminate die zijn mislukt. U kunt alle mislukte exemplaren be??indigen of slechts de ontbroken instanties voor een specifiek model. Desgewenst kunt u de exemplaren opnieuw beginnen nadat zij worden ge??indigd. U kunt de bewerking ook testen om de resultaten te zien zonder de bewerking daadwerkelijk uit te voeren.

* Argumenten:

   * Start de instantie opnieuw: (Optioneel) Geef een waarde op van `true` om de instanties opnieuw te starten nadat ze zijn be??indigd. De standaardwaarde van `false` veroorzaakt geen herstart van ge??indigde werkschemainstanties.
   * Droge run: (Optioneel) Geef een waarde op van `true` om de resultaten van de bewerking weer te geven zonder de bewerking daadwerkelijk uit te voeren. De standaardwaarde van `false` veroorzaakt dat de verrichting wordt uitgevoerd.
   * Model: (Optioneel) De id van het model waarop de bewerking wordt toegepast. Geef geen model op om de bewerking toe te passen op de mislukte exemplaren van alle workflowmodellen. De id is het pad naar het modelknooppunt, bijvoorbeeld:

      `/conf/global/settings/workflow/models/dam/update_asset/jcr:content/model`

* Geretourneerde waarde: Tabelgegevens over de instanties die worden be??indigd, die de volgende kolommen bevatten:

   * Initiator
   * InstanceId
   * ModelId
   * Payload
   * StartComment
   * WorkflowTitle

**** retryFailedWorkItemsAttempts om de stappen van het werkpunt uit te voeren die ontbroken hebben. U kunt alle mislukte werkitems of alleen de mislukte werkitems voor een specifiek workflowmodel opnieuw proberen. U kunt de bewerking desgewenst testen om de resultaten te zien zonder de bewerking daadwerkelijk uit te voeren.

* Argumenten:

   * Droge run: (Optioneel) Geef een waarde op van `true` om de resultaten van de bewerking weer te geven zonder de bewerking daadwerkelijk uit te voeren. De standaardwaarde van `false` veroorzaakt dat de verrichting wordt uitgevoerd.
   * Model: (Optioneel) De id van het model waarop de bewerking wordt toegepast. Geef geen model op om de bewerking toe te passen op de mislukte werkitems van alle workflowmodellen. De id is het pad naar het modelknooppunt, bijvoorbeeld:

      `/conf/global/settings/workflow/models/dam/update_asset/jcr:content/model`

* Geretourneerde waarde: Tabelgegevens over de mislukte werkitems die opnieuw worden geprobeerd, inclusief de volgende kolommen:

   * Initiator
   * InstanceId
   * ModelId
   * Payload
   * StartComment
   * WorkflowTitle

**** PurgeActiveRemoves active workflow instances van een bepaalde leeftijd. U kunt actieve exemplaren voor alle modellen of slechts de instanties voor een specifiek model leegmaken. U kunt de bewerking desgewenst testen om de resultaten te zien zonder de bewerking daadwerkelijk uit te voeren.

* Argumenten:

   * Model: (Optioneel) De id van het model waarop de bewerking wordt toegepast. Geef geen model op om de bewerking toe te passen op de workflowinstanties van alle workflowmodellen. De id is het pad naar het modelknooppunt, bijvoorbeeld:

      `/conf/global/settings/workflow/models/dam/update_asset/jcr:content/model`
   * Aantal dagen sinds het begin van de workflow: De leeftijd van de werkstroominstanties die moeten worden gewist, in dagen.
   * Droge run: (Optioneel) Geef een waarde op van `true` om de resultaten van de bewerking weer te geven zonder de bewerking daadwerkelijk uit te voeren. De standaardwaarde van `false` veroorzaakt dat de verrichting wordt uitgevoerd.

* Geretourneerde waarde: Tabelgegevens over de actieve werkstroominstanties die worden gewist, inclusief de volgende kolommen:

   * Initiator
   * InstanceId
   * ModelId
   * Payload
   * StartComment
   * WorkflowTitle

**** countStaleWorkflowsRetourneert het aantal werkstroominstanties dat stabiel is. U kunt het aantal instanties van de schaal voor alle werkschemamodellen of voor een specifiek model terugwinnen.

* Argumenten:

   * Model: (Optioneel) De id van het model waarop de bewerking wordt toegepast. Geef geen model op om de bewerking toe te passen op de workflowinstanties van alle workflowmodellen. De id is het pad naar het modelknooppunt, bijvoorbeeld:

      `/conf/global/settings/workflow/models/dam/update_asset/jcr:content/model`

* Geretourneerde waarde: Het aantal instanties van een schaalworkflow.

**** startStaleWorkflowsHiermee worden de instanties van de stapelworkflow opnieuw gestart. U kunt alle instanties van de schaal of slechts de instanties van de schaal voor een specifiek model opnieuw beginnen. U kunt de bewerking ook testen om de resultaten te zien zonder de bewerking daadwerkelijk uit te voeren.

* Argumenten:

   * Model: (Optioneel) De id van het model waarop de bewerking wordt toegepast. Geef geen model op om de bewerking toe te passen op de schaalvarianten van alle workflowmodellen. De id is het pad naar het modelknooppunt, bijvoorbeeld:

      `/conf/global/settings/workflow/models/dam/update_asset/jcr:content/model`
   * Droge run: (Optioneel) Geef een waarde op van `true` om de resultaten van de bewerking weer te geven zonder de bewerking daadwerkelijk uit te voeren. De standaardwaarde van `false` veroorzaakt dat de verrichting wordt uitgevoerd.

* Geretourneerde waarde: Een lijst met werkstroominstanties die opnieuw worden gestart.

**** fetchModelListList bevat alle workflowmodellen.

* Argumenten: none
* Geretourneerde waarde: Tabelgegevens die de workflowmodellen identificeren, inclusief de kolommen ModelId en ModelName.

**** countRunningWorkflowsRetourneert het aantal werkstroominstanties dat wordt uitgevoerd. U kunt het aantal actieve exemplaren voor alle werkschemamodellen of voor een specifiek model terugwinnen.

* Argumenten:

   * Model: (Optioneel) De id van het model waarvoor het aantal actieve exemplaren wordt geretourneerd. Geef geen model op om het aantal actieve exemplaren van alle workflowmodellen te retourneren. De id is het pad naar het modelknooppunt, bijvoorbeeld:

      `/conf/global/settings/workflow/models/dam/update_asset/jcr:content/model`

* Geretourneerde waarde: Het aantal actieve workflowinstanties.

**** countCompletedWorkflowsRetourneert het aantal werkstroominstanties dat is voltooid. U kunt het aantal voltooide exemplaren voor alle werkschemamodellen of voor een specifiek model terugwinnen.

* Argumenten:

   * Model: (Optioneel) De id van het model waarvoor het aantal voltooide exemplaren wordt geretourneerd. Geef geen model op om het aantal voltooide exemplaren van alle workflowmodellen te retourneren. De id is het pad naar het modelknooppunt, bijvoorbeeld:

      `/conf/global/settings/workflow/models/dam/update_asset/jcr:content/model`

* Geretourneerde waarde: Het aantal voltooide workflowexemplaren.

**** purgeCompletedHiermee verwijdert u records van voltooide workflows van een specifieke leeftijd uit de opslagplaats. Gebruik deze bewerking regelmatig om de grootte van de opslagplaats te minimaliseren wanneer u veel gebruik maakt van workflows. U kunt voltooide exemplaren voor alle modellen of slechts de instanties voor een specifiek model leegmaken. U kunt de bewerking desgewenst testen om de resultaten te zien zonder de bewerking daadwerkelijk uit te voeren.

* Argumenten:

   * Model: (Optioneel) De id van het model waarop de bewerking wordt toegepast. Geef geen model op om de bewerking toe te passen op de workflowinstanties van alle workflowmodellen. De id is het pad naar het modelknooppunt, bijvoorbeeld:

      `/conf/global/settings/workflow/models/dam/update_asset/jcr:content/model`
   * Aantal dagen sinds werkstroom is voltooid: Het aantal dagen dat de werkstroominstanties de voltooide status hebben.
   * Droge run: (Optioneel) Geef een waarde op van `true` om de resultaten van de bewerking weer te geven zonder de bewerking daadwerkelijk uit te voeren. De standaardwaarde van `false` veroorzaakt dat de verrichting wordt uitgevoerd.

* Geretourneerde waarde: Tabelgegevens over de voltooide werkstroominstanties die worden gewist, inclusief de volgende kolommen:

   * Initiator
   * InstanceId
   * ModelId
   * Payload
   * StartComment
   * WorkflowTitle

## Bewaarplaats {#repository}

Informatie over de CRX-opslagplaats

* Domein: com.adobe.granite
* Type: Bewaarplaats

### Kenmerken {#attributes}

**** NaamDe naam van de implementatie van de JCR-opslagruimte. Alleen-lezen.

**** VersionThe repository implementation version. Alleen-lezen.

**** HomeDirDe directory waarin de repository zich bevindt. De standaardlocatie is &lt;QuickStart_Jar_Location>/crx-quickstart/repository. Alleen-lezen.

**** KlantnaamDe naam van de klant aan wie de softwarelicentie is verleend. Alleen-lezen.

**** LicentieKeyDe unieke licentiecode voor deze installatie van de opslagplaats. Alleen-lezen.

**** AvailableDiskSpaceDe schijfruimte die beschikbaar is voor deze instantie van de opslagplaats, in Mbytes. Alleen-lezen.

**** MaximumNumberOfOpenFilesHet aantal bestanden dat tegelijk kan worden geopend. Alleen-lezen.

**** SessionTrackerThe value of the crx.debug.session system variable. true geeft een foutopsporingssessie aan. false geeft een normale sessie aan. Lezen/schrijven.

**** DescriptorsEen set sleutelwaardeparen die de eigenschappen van de repository vertegenwoordigen. Alle eigenschappen zijn alleen-lezen.

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
     <li>identifier.stability.indefinite.duration: Id's worden niet gewijzigd.</li>
     <li>identifier.stability.method.duration: Identifiers kunnen tussen methodevraag veranderen.</li>
     <li>identifier.stability.save.duration: Id's worden niet gewijzigd in een cyclus voor opslaan en vernieuwen.</li>
     <li>identifier.stability.session.duration: Id's worden tijdens een sessie niet gewijzigd.</li>
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
   <td>true geeft aan dat de gegevensopslagruimte eenvoudige versioning ondersteunt. Met eenvoudige versioning onderhoudt de repository een sequenti??le reeks versies van een knooppunt.</td>
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
   <td>true geeft aan dat de gegevensopslagruimte de registratie van knooppunttypen met meerdere binaire eigenschappen ondersteunt. false geeft aan dat ????n binaire eigenschap wordt ondersteund voor een knooppunttype.</td>
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
   <td>true geeft aan dat de opslagplaats het maken van deelbare knooppunten ondersteunt.</td>
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
   <td><p>Geeft het niveau van opslagruimteondersteuning voor overerving van knooppunttypen aan. De volgende waarden zijn mogelijk:</p> <p>node.type.management.inheritance.minimum: De registratie van primaire knooppunttypes is beperkt tot die die slechts niet:basis als supertype hebben. Registratie van typen mixinknooppunten is beperkt tot knooppunten zonder supertype.</p> <p>node.type.management.inheritance.single: Registratie van typen primaire knooppunten is beperkt tot knooppunten met ????n supertype. Registratie van typen mixinknooppunten is beperkt tot knooppunten met ten hoogste ????n supertype.</p> <p><br /> node.type.management.inheritance.multiple: De primaire knooptypes kunnen met ????n of meerdere supertypes worden geregistreerd. Mixinknooptypen kunnen met nul of meer supertypen worden geregistreerd.</p> </td>
  </tr>
  <tr>
   <td>crx.cluster.preferredMaster</td>
   <td>true geeft aan dat dit clusterknooppunt de voorkeursserver master van het cluster is.</td>
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
     <li>query.joins.none: Geen ondersteuning voor verbindingen. Voor query's kan ????n kiezer worden gebruikt.</li>
     <li>query.joins.inner: Ondersteuning voor verbindingen binnen.</li>
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
   <td>true geeft aan dat de opslagplaats de XML-code die wordt ge??mporteerd als inhoud ondersteunt.</td>
  </tr>
  <tr>
   <td>node.type.management.same.name.siblings.supported</td>
   <td>true geeft aan dat de gegevensopslagruimte knooppunten op hetzelfde niveau (knooppunten met hetzelfde bovenliggende knooppunt) met dezelfde naam ondersteunt.</td>
  </tr>
  <tr>
   <td>node.type.management.residual.definitions.supported</td>
   <td>true geeft aan dat de opslagplaats naameigenschappen met residudefinities ondersteunt. Als dit wordt ondersteund, kan het kenmerk name van een itemdefinitie een sterretje ("*") zijn.</td>
  </tr>
  <tr>
   <td>node.type.management.autocreated.definitions.supported</td>
   <td>true geeft aan dat de gegevensopslagruimte het automatisch maken van onderliggende items (knooppunten of eigenschappen) van een knooppunt ondersteunt wanneer het knooppunt wordt gemaakt.</td>
  </tr>
  <tr>
   <td>crx.cluster.master</td>
   <td>true geeft aan dat dit opslagruimteknooppunt het master knooppunt van de cluster is.</td>
  </tr>
  <tr>
   <td>level.1.supported</td>
   <td>true geeft aan dat option.xml.export.support true is en query.languages niet-lengte nul is.</td>
  </tr>
  <tr>
   <td>option.unfiled.content.supported</td>
   <td>true geeft aan dat de gegevensopslagruimte niet-gearchiveerde inhoud ondersteunt. knooppunten zonder veld maken geen deel uit van de hi??rarchie van de opslagplaats.</td>
  </tr>
  <tr>
   <td>jcr.specification.name</td>
   <td>De naam van de JCR-specificatie die de gegevensopslagruimte implementeert.</td>
  </tr>
  <tr>
   <td>option.versioning.supported</td>
   <td>true geeft aan dat de opslagplaats volledige versioning ondersteunt.</td>
  </tr>
  <tr>
   <td>jcr.repository.name</td>
   <td>De naam van de gegevensopslagruimte.</td>
  </tr>
  <tr>
   <td>option.locking.supported</td>
   <td>true geeft aan dat de opslagplaats de vergrendeling van knooppunten ondersteunt. Door vergrendeling kan de gebruiker tijdelijk voorkomen dat andere gebruikers wijzigingen aanbrengen.</td>
  </tr>
  <tr>
   <td>jcr.repository.version.display</td>
   <td> </td>
  </tr>
  <tr>
   <td>option.activities.supported</td>
   <td>true geeft aan dat de gegevensopslagruimte activiteiten ondersteunt. Activiteiten zijn een set wijzigingen die worden uitgevoerd in een werkruimte en worden samengevoegd in een andere werkruimte.</td>
  </tr>
  <tr>
   <td>node.type.management.multivalued.properties.supported</td>
   <td>true geeft aan dat de repository knoopeigenschappen ondersteunt die nul of meer waarden kunnen hebben.</td>
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

**** WorkspaceNamesThe names of the workspaces in the repository. Alleen-lezen.

**** DataStoreGarbageCollectionDelayDe hoeveelheid tijd in milliseconden die de huisvuilinzameling na het aftasten elke tiende knoop slaapt. Lezen/schrijven.

**** BackupDelayDe hoeveelheid tijd in milliseconden die het back-upproces tussen elke stap van de back-up stroomt. Lezen/schrijven.

**** BackupInProgressDe waarde true geeft aan dat een back-upproces wordt uitgevoerd. Alleen-lezen.

**** BackupProgressVoor de huidige back-up het percentage van alle bestanden waarvan een back-up is gemaakt. Alleen-lezen.

**** CurrentBackupTargetVoor de huidige back-up, het ZIP-bestand waar de back-upbestanden worden opgeslagen. Als er geen back-up wordt gemaakt, wordt er geen waarde weergegeven. Alleen-lezen.

**** BackupIsSuccessfulDe waarde true geeft aan dat er geen fouten zijn opgetreden tijdens de huidige back-up of dat er geen back-up wordt gemaakt. false geeft aan dat er een fout is opgetreden tijdens de huidige back-up. Alleen-lezen.

**** BackupResultDe status van de huidige back-up. De volgende waarden zijn mogelijk:

* Back-up wordt uitgevoerd: Er wordt momenteel een back-up uitgevoerd.
* Back-up geannuleerd: De back-up is geannuleerd.
* Back-up voltooid met fout: Er is een fout opgetreden tijdens de back-up. Het foutbericht bevat informatie over de oorzaak.
* Back-up voltooid: De back-up is gemaakt.
* Er is tot nu toe geen back-up uitgevoerd: Er is geen back-up bezig.

Alleen-lezen.

**** TarOptimizationRunningSinceThe tijd waarop het huidige proces van de het dossieroptimalisering van TAR begon. Alleen-lezen.

**** TarOptimizationDelayDe hoeveelheid tijd in milliseconden dat het optimalisatieproces van de TAR tussen elke stap van het proces stroomt. Lezen/schrijven.

**** ClusterPropertiesA-set sleutelwaardeparen die clustereigenschappen en -waarden vertegenwoordigen. Elke rij in de tabel vertegenwoordigt een clustereigenschap. Alleen-lezen.

**** ClusterNodesThe members of the repository cluster.

**** ClusterIdDe id van deze opslagplaats cluster. Alleen-lezen.

**** ClusterMasterIdThe-id van het master knooppunt van deze opslagruimtecluster. Alleen-lezen.

**** ClusterNodeIdThe identifier van dit knooppunt van de opslagcluster. Alleen-lezen.

### Bewerkingen {#operations-1}

**** createWorkspaceMaakt een werkruimte in deze opslagplaats.

* Argumenten:

   * naam: Een tekenreekswaarde die de naam van de nieuwe werkruimte vertegenwoordigt.

* Geretourneerde waarde: none

**** runDataStoreGarbageCollectionExecutes garbage collection on the repository nodes.

* Argumenten:

   * verwijderen: Een Booleaanse waarde die aangeeft of ongebruikte repository-items moeten worden verwijderd. De waarde true zorgt ervoor dat ongebruikte knooppunten en eigenschappen worden verwijderd. Bij de waarde false worden alle knooppunten gescand, maar worden geen knooppunten verwijderd.

* Geretourneerde waarde: none

**** stopDataStoreGarbageCollectionStops a running data store garbage collection.

* Argumenten: none
* Geretourneerde waarde: tekenreeksrepresentatie van de huidige status

**** startBackupBack-up van gegevens in de opslagplaats in een ZIP-bestand.

* Argumenten:

   * `target`: (Optioneel) Een  `String` waarde die de naam vertegenwoordigt van het ZIP-bestand of de ZIP-map waarin de gegevens in de opslagplaats moeten worden gearchiveerd. Als u een ZIP-bestand wilt gebruiken, neemt u de bestandsnaamextensie ZIP op. Als u een map wilt gebruiken, neemt u geen bestandsnaamextensie op.

      Om een stijgende steun uit te voeren, specificeer de folder die eerder voor de steun werd gebruikt.

      U kunt een absoluut of relatief pad opgeven. Relatieve paden zijn relatief ten opzichte van de bovenliggende map van de map crx-quickstart.

      Als u geen waarde opgeeft, wordt de standaardwaarde `backup-currentdate.zip` gebruikt, waarbij `currentdate` de notatie `yyyyMMdd-HHmm` heeft.

* Geretourneerde waarde: none

**** cancelBackupHiermee wordt het huidige back-upproces gestopt en wordt het tijdelijke archief verwijderd dat is gemaakt voor het archiveren van gegevens.

* Argumenten: none
* Geretourneerde waarde: none

**** blockRepositoryWritesBlocks wijzigt de gegevens in de opslagplaats. Alle back-uplisteners van de opslagplaats worden op de hoogte gesteld van het blok.

* Argumenten: none
* Geretourneerde waarde: none

**** unblockRepositoryWritesVerwijdert het blok uit de repository. Alle back-uplisteners van de opslagplaats worden op de hoogte gesteld van de blokverwijdering.

* Argumenten: none
* Geretourneerde waarde: none

**** startTarOptimizationStart het TAR-bestandsoptimalisatieproces met de standaardwaarde voor tarOptimizationDelay.

* Argumenten: none
* Geretourneerde waarde: none

**** stopTarOptimizationStops TAR file optimization.

* Argumenten: none
* Geretourneerde waarde: none

**** tarIndexMergeHiermee worden de bovenste indexbestanden van alle TAR-sets samengevoegd. De bovenste indexbestanden zijn bestanden met verschillende hoofdversies. De volgende bestanden worden bijvoorbeeld samengevoegd in het bestand index_3_1.tar: index_1_1.tar, index_2_0.tar, index_3_0.tar. De samengevoegde bestanden worden verwijderd (in het vorige voorbeeld worden index_1_1.tar, index_2_0.tar en index_3_0.tar verwijderd).

* Argumenten:

   * `background`: Een Booleaanse waarde die aangeeft of de bewerking op de achtergrond moet worden uitgevoerd, zodat de webconsole tijdens de uitvoering bruikbaar is. De waarde true voert de bewerking op de achtergrond uit.

* Geretourneerde waarde: none

**** nowClusterMasterSets dit opslagruimteknooppunt als het master knooppunt van de cluster. Als deze opdracht nog niet is master, wordt de listener van de huidige master instantie gestopt en wordt een master listener op het huidige knooppunt gestart. Dit knooppunt wordt vervolgens ingesteld als het master knooppunt en wordt opnieuw opgestart, waardoor alle andere knooppunten in het cluster (dat wil zeggen knooppunten die door de master worden bestuurd) verbinding maken met deze instantie.

* Argumenten: none
* Geretourneerde waarde: none

**** joinClusterVoegt deze opslagplaats aan een cluster als knoop toe die door de master cluster wordt gecontroleerd. Voor verificatiedoeleinden moet u een gebruikersnaam en wachtwoord opgeven. De verbinding gebruikt basisauthentificatie. De beveiligingsreferenties zijn base-64 gecodeerd voordat ze naar de server worden verzonden.

* Argumenten:

   * `master`: Een tekenreekswaarde die het IP-adres of de computernaam vertegenwoordigt van de computer waarop het knooppunt van de master opslagplaats wordt uitgevoerd.
   * `username`: De naam die moet worden gebruikt voor verificatie met de cluster.
   * `password`: Het wachtwoord dat voor verificatie moet worden gebruikt.

* Geretourneerde waarde: none

**** traversalCheckTraverses en corrigeert optioneel inconsistenties in een substructuur die begint bij een bepaald knooppunt. Dit wordt uitvoerig besproken in de documentatie over persistentiemanagers.

**Met** ConsistentCheckChecks en optioneel wordt consistentie in de Datastore hersteld. Dit wordt uitvoerig besproken in de documentatie op de Datastore.

## Statistieken opslagplaats (TimeSeries) {#repository-statistics-timeseries}

De waarde van het gebied TimeSeries voor elk statistiektype dat `org.apache.jackrabbit.api.stats.RepositoryStatistics` bepaalt.

* Domein: `com.adobe.granite`
* Type: `TimeSeries`
* Naam: Een van de volgende waarden uit de klasse Enum `org.apache.jackrabbit.api.stats.RepositoryStatistics.Type`:

   * BUNDLE_CACHE_ACCESS_COUNTER
   * BUNDLE_CACHE_MISS_AVERAGE
   * BUNDLE_CACHE_MISS_COUNTER
   * BUNDLE_CACHE_MISS_DURATION
   * BUNDLE_CACHE_SIZE_COUNTER
   * BUNDLE_COUNTER
   * BUNDLE_READ_COUNTER
   * BUNDLE_WRITE_AVERAGE
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

### Kenmerken {#attributes-1}

De volgende eigenschappen worden verstrekt voor elk statistisch type dat wordt gerapporteerd:

* ValuePerSecond: De gemeten waarde per seconde gedurende de laatste minuut. Alleen-lezen.
* ValuePerMinute: De gemeten waarde per minuut over het laatste uur. Alleen-lezen.
* ValuePerHour: De gemeten waarde per uur in de laatste week. Alleen-lezen.
* ValuePerWeek: De gemeten waarde per week over de laatste drie jaar. Alleen-lezen.

## Query-cijfers voor opslagplaats {#repository-query-stats}

Statistische informatie over query&#39;s in de gegevensopslagruimte.

* Domein: com.adobe.granite
* Type: QueryState

### Kenmerken {#attributes-2}

**** SlowQueriesInformatie over de bewaargegevensvragen die de langste tijd hebben geduurd om te voltooien. Alleen-lezen.

**** SlowQueriesQueueSizeHet maximum aantal vragen om in de lijst te omvatten SlowQueries. Lezen.

**** PopularQueriesInformation over de bewaargegevensvragen die het meest voorkwamen. Alleen-lezen.

**** PopularQueriesQueueSizeThe maximum aantal vragen in de lijst PopularQueries. Lezen.

### Bewerkingen {#operations-2}

**** clearSlowQueriesQueueVerwijdert alle vragen uit de lijst SlowQueries.

* Argumenten: none
* Geretourneerde waarde: none

**** clearPopularQueriesQueueVerwijdert alle vragen uit de lijst PopularQueries.

* Argumenten: none
* Geretourneerde waarde: none

## Replication Agents {#replication-agents}

Controleer de diensten voor elke replicatieagent. Wanneer u een replicatieagent creeert, verschijnt de dienst automatisch in de console JMX.

* **Domein:** com.adobe.granite.replication
* **Type:** agent
* **Naam:** geen waarde
* **Eigenschappen:** {id=&quot;*Naam*&quot;}, waarbij  ** Naam de waarde van het bezit van de Naam van de agent is.

### Kenmerken {#attributes-3}

**De waarde van** het Koord IdA die het herkenningsteken van de configuratie van de replicatieagent vertegenwoordigt. De veelvoudige agenten kunnen de zelfde configuratie gebruiken. Alleen-lezen.

**** ValidA booleaanse waarde die erop wijst of de agent correct wordt gevormd:

* `true`: Geldige configuratie.
* `false` : De configuratie bevat fouten.

Alleen-lezen.

**Booleaanse waarde** EnabledA die aangeeft of de agent is ingeschakeld:

* `true`: Ingeschakeld.
* `false`: Uitgeschakeld.

**Booleaanse waarde** QueueBlockedA die aangeeft of de wachtrij bestaat en wordt geblokkeerd:

* `true`: Geblokkeerd. Er is een automatisch opnieuw proberen in behandeling.
* `false`: Niet geblokkeerd of bestaat niet.

Alleen-lezen.

**Booleaanse waarde** QueuePausedA die aangeeft of de taakwachtrij is gepauzeerd:

* `true`: Gepauzeerd (opgeschort)
* `false`: Niet gepauzeerd of bestaat niet.

Lezen.

**De** waarde van QueueNumEnaptersAn int die het aantal banen in de agentenrij vertegenwoordigt. Alleen-lezen.

**De waarde van de Datum** QueueStatusTimeA die op de tijd op de server wijst toen de getoonde statuswaarden werden verkregen. De waarde komt overeen met de tijd waarop de pagina is geladen. Alleen-lezen.

**** QueueNextRetryTimeFor geblokkeerde rijen, een waarde van de Datum die erop wijst wanneer het volgende automatische opnieuw probeert voorkomt. Als er geen tijd wordt weergegeven, wordt de wachtrij niet geblokkeerd. Alleen-lezen.

**De** waarde van de Datum van QueueProcessingSinceA die erop wijst wanneer de verwerking voor de huidige baan begon. Wanneer er geen tijd wordt weergegeven, wordt de wachtrij geblokkeerd of inactief. Alleen-lezen.

**De** Date-waarde QueueLastProcessTimeA geeft aan wanneer de vorige taak is voltooid. Alleen-lezen.

### Bewerkingen {#operations-3}

**** queueForceRetryFor geblokkeerde wachtrijen geeft de opdracht retry uit aan de wachtrij.

* Argumenten: none
* Geretourneerde waarde: none

**** queueClearVerwijdert alle taken uit de wachtrij.

* Argumenten: none
* Geretourneerde waarde: none

## Verschuivende engine {#sling-engine}

Verstrekt statistieken over HTTP- verzoeken zodat u de prestaties van de dienst kunt controleren SlingRequestProcessor.

* Domein: org.apache.sling
* Type: motor
* Eigenschappen: {service=RequestProcessor}

### Kenmerken {#attributes-4}

**** RequestsCountThe aantal verzoeken die zijn voorgekomen sinds de statistieken het laatst werden teruggesteld.

**** MinRequestDurationMsecDe kortste hoeveelheid tijd (in milliseconden) die werd vereist om een verzoek te verwerken aangezien de statistieken het laatst werden teruggesteld.

**** MaxRequestDurationMsecDe langste hoeveelheid tijd (in milliseconden) die werd vereist om een verzoek te verwerken aangezien de statistieken het laatst werden teruggesteld.

**** StandardDeviationDurationMsecDe standaardafwijking van de hoeveelheid tijd die werd vereist om verzoeken te verwerken. De standaardafwijking wordt berekend gebruikend alle verzoeken aangezien de statistieken het laatst werden teruggesteld.

**** GemiddeldeRequestDurationMsecDe gemiddelde hoeveelheid tijd die werd vereist om een verzoek te verwerken. Het gemiddelde wordt berekend aan de hand van alle aanvragen sinds de statistieken voor het laatst zijn ingesteld

### Bewerkingen {#operations-4}

**** resetStatisticsSets all statistics to zero. Herstel de statistieken wanneer u de prestaties van de verzoekverwerking tijdens een specifiek tijdkader moet analyseren.

* Argumenten: none
* Geretourneerde waarde: none

**** idDe tekenreeksrepresentatie van de pakket-id.

**booleaanse waarde** installedA die aangeeft of het pakket is ge??nstalleerd:

* `true`: Ge??nstalleerd.
* `false`: Niet ge??nstalleerd.

**** installedByThe ID van de gebruiker die het pakket het laatst heeft ge??nstalleerd.

**** installedDateThe datum waarop het pakket voor het laatst werd ge??nstalleerd.

**** sizeEen lange waarde die de grootte van het pakket in bytes houdt.


## QuickStart Launcher {#quickstart-launcher}

Informatie over het opstartproces en de QuickStart-starter.

* Domein: com.adobe.granite.quickstart
* Type: Launcher

### Bewerkingen {#operations-5}

**log**

Hiermee wordt een bericht weergegeven in het QuickStart-venster.

Argumenten:

* p1: Een waarde `String` die het bericht aan vertoning vertegenwoordigt.
* Geretourneerde waarde: none

**startFinished**

Roept de opstartenFinished methode van de serverlancerer. De methode probeert de welkomstpagina in een webbrowser te openen.

* Argumenten: none
* Geretourneerde waarde: none

**startProgress**

Hiermee wordt de voltooiingswaarde van het opstartproces van de server ingesteld. De voortgangsbalk in het QuickStart-venster vertegenwoordigt de voltooiingswaarde.

* Argumenten:
   * p1: Een drijvende-kommawaarde die aangeeft hoeveel van het opstartproces is voltooid, als een breuk. De waarde moet liggen tussen nul en ????n. 0,3 geeft bijvoorbeeld aan dat 30% is voltooid.
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
   <td><a href="https://docs.oracle.com/javase/8/docs/api/javax/management/package-summary.html">javax.</a> management package</td>
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
   <td><a href="https://osgi.org/specification/osgi.enterprise/7.0.0/service.jmx.html#d0e42567">org.osgi.jmx.</a> frameworkpackage</td>
  </tr>
 </tbody>
</table>

## De JMX-console gebruiken {#using-the-jmx-console}

In de JMX-console wordt informatie weergegeven over verschillende services die op de server worden uitgevoerd:

* Kenmerken: Service-eigenschappen zoals configuraties of runtime-gegevens. Kenmerken kunnen alleen-lezen of lezen-schrijven zijn.
* Bewerkingen: Opdrachten die u op de service kunt aanroepen.

MBeans die met de dienst OSGi worden opgesteld stelt de dienstattributen en verrichtingen aan de console bloot. De MBean bepaalt de attributen en de verrichtingen die worden blootgesteld, en of de attributen read-only of read-write zijn.

De belangrijkste pagina van de console JMX omvat een lijst van de diensten. Elke rij in de lijst vertegenwoordigt de dienst die door een MBean wordt blootgesteld.

1. Open de webconsole en klik op het tabblad JMX. ([http://localhost:4502/system/console/jmx](http://localhost:4502/system/console/jmx))
2. Klik een celwaarde voor de dienst om de attributen en de verrichtingen voor de dienst te zien.
3. Als u een kenmerkwaarde wilt wijzigen, klikt u op de waarde, geeft u de waarde op in het dialoogvenster dat verschijnt en klikt u op Opslaan.
4. Als u een servicebewerking wilt aanroepen, klikt u op de naam van de bewerking, geeft u in het dialoogvenster argumentwaarden op en klikt u op Invoke.

## Externe JMX-toepassingen gebruiken om {#using-external-jmx-applications-for-monitoring} te controleren

Met CRX kunnen externe toepassingen communiceren met Beheerde Beans (MBeans) via [Java Management Extensions (JMX)](https://docs.oracle.com/javase/6/docs/technotes/guides/management/overview.html). Met algemene consoles zoals [JConsole](https://java.sun.com/developer/technicalArticles/J2SE/jconsole.html) of domeinspecifieke controletoepassingen kunt u CRX-configuraties en -eigenschappen ophalen en instellen, en kunt u de prestaties en het gebruik van bronnen controleren.

### Het gebruiken van JConsole om met CRX {#using-jconsole-to-connect-to-crx} te verbinden

Voer de volgende stappen uit om verbinding te maken met CRX met behulp van JConsole:

1. Open een terminalvenster.
1. Voer de volgende opdracht in:

   `jconsole`

JConsole wordt gestart en het JConsole-venster wordt weergegeven.

### Verbinding maken met een lokaal CRX-proces {#connecting-to-a-local-crx-process}

JConsole zal een lijst van lokale processen van de Virtuele Machine van Java tonen. De lijst bevat twee snelstartprocessen. Selecteer het snelstartproces &quot;CHILD&quot; in de lijst met lokale processen (meestal het proces met de hogere PID).

![screen_shot_2012-03-26at114557am](assets/screen_shot_2012-03-26at114557am.png)

### Verbinding maken met een extern CRX-proces {#connecting-to-a-remote-crx-process}

Als u verbinding wilt maken met een extern CRX-proces, moet de JVM die het externe CRX-proces host, zijn ingeschakeld voor het accepteren van externe JMX-verbindingen.

Om externe JMX-verbindingen in te schakelen, moet de volgende systeemeigenschap worden ingesteld bij het starten van de JVM:

`com.sun.management.jmxremote.port=portNum`

In het bezit hierboven, is `portNum` het havenaantal waardoor u verbindingen JMX RMI wilt toelaten. Geef een ongebruikt poortnummer op. Naast het publiceren van een schakelaar RMI voor lokale toegang, publiceert het plaatsen van dit bezit een extra schakelaar RMI in een priv?? read-only register bij de gespecificeerde haven gebruikend een bekende naam, &quot;jmxrmi&quot;.

Wanneer u de JMX-agent inschakelt voor externe controle, gebruikt deze standaard wachtwoordverificatie op basis van een wachtwoordbestand dat moet worden opgegeven met de volgende systeemeigenschap bij het starten van de Java VM:

`com.sun.management.jmxremote.password.file=pwFilePath`

Raadpleeg de [relevante JMX-documentatie](https://docs.oracle.com/javase/6/docs/technotes/guides/management/agent.html) voor gedetailleerde instructies voor het instellen van een wachtwoordbestand.

Voorbeeld:

```shell
$ java
  -Dcom.sun.management.jmxremote.password.file=pwFilePath
  -Dcom.sun.management.jmxremote.port=8463
  -jar ./cq-quickstart.jar
```

### Het gebruiken van de MBeans die door CRX {#using-the-mbeans-provided-by-crx} worden verstrekt

Nadat u verbinding hebt gemaakt met het quickstart-proces, biedt JConsole een reeks algemene controlemiddelen voor de JVM waarin CRX wordt uitgevoerd.

![screen_shot_2012-03-26at115056am](assets/screen_shot_2012-03-26at115056am.png)

Om tot de interne controle en configuratieopties van CRX toegang te hebben, ga naar het lusje MBeans, en van de hi??rarchische inhoudsboom op de linkerzijde, selecteer de sectie van Attributen of van Verrichtingen die u geinteresseerd in bent. Bijvoorbeeld de sectie com.adobe.granite/Repository/Operations.

Selecteer in die sectie het gewenste kenmerk of de gewenste bewerking in het linkerdeelvenster.

![screen_shot_2012-03-26at115728am](assets/screen_shot_2012-03-26at115728am.png)

