---
title: Taken verschuiven
description: Leer hoe te om AEM instanties in een topologie te vormen en te gebruiken om specifieke soorten verwerking uit te voeren.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
feature: Configuring
exl-id: 429c96ff-4185-4215-97e8-9bd2c130a9b1
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '2318'
ht-degree: 0%

---

# Taken verschuiven{#offloading-jobs}

## Inleiding {#introduction}

Het ontladen verdeelt verwerkingstaken onder de instanties van de Experience Manager in een topologie. Met offloading kunt u specifieke instanties van Experience Managers gebruiken voor het uitvoeren van specifieke typen verwerking. Met gespecialiseerde verwerking kunt u het gebruik van beschikbare serverbronnen maximaliseren.

Het ontladen is gebaseerd op [ Apache het Verdelen Ontdekking ](https://sling.apache.org/documentation/bundles/discovery-api-and-impl.html) en het Verdelen eigenschappen JobManager. Om het ontladen te gebruiken, voegt u de clusters van de Experience Manager aan een topologie toe en identificeert de baanonderwerpen die het clusterproces. Clusters bestaan uit een of meer instanties van Experience Managers, zodat één instantie als een cluster wordt beschouwd.

Voor informatie over het toevoegen van instanties aan een topologie, zie [ Administering Topologies ](/help/sites-deploying/offloading.md#administering-topologies).

### Taakverdeling {#job-distribution}

Sling JobManager en JobConsumer laten de verwezenlijking van banen toe die in een topologie worden verwerkt:

* JobManager: de dienst die banen voor specifieke onderwerpen leidt.
* JobConsumer: een dienst die banen van één of meerdere onderwerpen uitvoert. De veelvoudige diensten JobConsumer kunnen voor het zelfde onderwerp worden geregistreerd.

Wanneer JobManager een baan creeert, selecteert het Offloading kader een cluster van de Experience Manager in de topologie om de baan uit te voeren:

* De cluster moet één of meerdere instanties omvatten die een JobConsumer in werking stellen die voor het baanonderwerp wordt geregistreerd.
* Het onderwerp moet voor minstens één geval in de cluster worden toegelaten.

Zie [ Vormend de Verbruik van het Onderwerp ](/help/sites-deploying/offloading.md#configuring-topic-consumption) voor informatie over het raffineren van baandistributie.

![ chlimage_1-109 ](assets/chlimage_1-109.png)

Wanneer het Offloading-framework een cluster selecteert om een taak uit te voeren en de cluster uit meerdere instanties bestaat, bepaalt Sling Distribution welke instantie in de cluster de taak uitvoert.

### Job Payloads {#job-payloads}

Het offloading-framework ondersteunt taaktaken die taken koppelen aan bronnen in de opslagplaats. Taaktaken zijn handig wanneer taken worden gemaakt voor de verwerking van bronnen en de taak wordt overgeladen naar een andere computer.

Bij het maken van een taak wordt de lading alleen gegarandeerd geplaatst op het exemplaar dat de taak maakt. Wanneer het ontladen van de baan, zorgen de replicatieagenten ervoor dat de lading op de instantie wordt gecreeerd die uiteindelijk de baan verbruikt. Wanneer de uitvoering van de taak is voltooid, zorgt omgekeerde replicatie ervoor dat de payload wordt gekopieerd naar de instantie die de taak heeft gemaakt.

## Onderwerptechnologieën beheren {#administering-topologies}

De technologieën zijn losjes verbonden clusters van de Experience Manager die aan het ontladen deelnemen. Een cluster bestaat uit een of meer serverinstanties van de Experience Manager (één instantie wordt beschouwd als een cluster).

Elke instantie van de Experience Manager stelt de volgende aan het ontladen verwante diensten in werking:

* De Dienst van de ontdekking: verzendt verzoeken aan een Schakelaar van de Topologie om zich bij de topologie aan te sluiten.
* De Schakelaar van de topologie: Ontvangt de toetrederingsverzoeken en of keurt of weigert elk verzoek goed.

De dienst van de Ontdekking van alle leden van de topologie richt aan de Schakelaar van de Topologie op één van de leden. In de volgende secties wordt dit lid het hoofdlid genoemd.

![ chlimage_1-110 ](assets/chlimage_1-110.png)

Elke cluster in de topologie bevat een instantie die als leider wordt erkend. De clusterleider communiceert met de topologie namens de andere leden van de cluster. Wanneer de leader de cluster verlaat, wordt automatisch een nieuwe leader voor de cluster gekozen.

### De topologie weergeven {#viewing-the-topology}

Browser van de Topologie van het gebruik om de staat van de topologie te onderzoeken waarin de instantie van de Experience Manager deelneemt. Browser van de topologie toont de clusters en de instanties van de topologie.

Voor elke cluster, ziet u een lijst van clusterleden die op de orde wijst waarin elk lid zich bij de cluster aansloot, en welk lid de Leider is. De eigenschap Current geeft de instantie aan die u momenteel beheert.

Voor elke instantie in de cluster, kunt u verscheidene op topologie betrekking hebbende eigenschappen zien:

* Een lijst van gewenste personen van onderwerpen voor de baanconsument van de instantie.
* De eindpunten die voor het verbinden met de topologie worden blootgesteld.
* De taakonderwerpen waarvoor de instantie is geregistreerd voor offloaden.
* De taakonderwerpen die de instantie verwerkt.

1. Klik met de aanraakinterface op het tabblad Gereedschappen. ([ http://localhost:4502/tools.html](http://localhost:4502/tools.html))
1. Klik in het gebied Bewerkingen graniet op Browser offloaden.
1. Klik in het navigatievenster op Topologiebrowser.

   De clusters die aan de topologie deelnemen verschijnen.

   ![ chlimage_1-111 ](assets/chlimage_1-111.png)

1. Klik op een cluster om een lijst weer te geven met de instanties in de cluster en hun id, huidige status en leaderstatus.
1. Klik op een instantie-id voor meer gedetailleerde eigenschappen.

U kunt de Console van het Web ook gebruiken om topologieinformatie te bekijken. De console verstrekt verdere informatie over de topologieclusters:

* Welke instantie is de lokale instantie.
* De diensten van de Verbinding van de Topologie die deze instantie gebruikt om met de topologie (uitgaande), en de diensten te verbinden die met deze (inkomende) instantie verbinden.
* De geschiedenis van de verandering voor de topologie en instantiereigenschappen.

Gebruik de volgende procedure om de pagina van het Beheer van de Topologie van de Console van het Web te openen:

1. Open de webconsole in uw browser. ([ http://localhost:4502/system/console](http://localhost:4502/system/console))
1. Klik op Hoofd > Topologiebeheer.

   ![ chlimage_1-112 ](assets/chlimage_1-112.png)

### Het vormen Lidmaatschap van de Topologie {#configuring-topology-membership}

De Apache die middel-Gebaseerde Dienst van de Ontdekking op elke instantie plaatst om te controleren hoe de instanties van de Experience Manager met een topologie in wisselwerking staan.

De dienst van de Ontdekking verzendt periodieke verzoeken van de POST (hartslagen) naar de diensten van de Verbinding van de Topologie om verbindingen met de topologie te vestigen en te handhaven. De dienst van de Verbinding van de Topologie handhaaft een lijst van gewenste personen van IP adressen of gastheernamen die worden toegestaan om zich bij de topologie aan te sluiten:

* Om zich bij een instantie aan een topologie aan te sluiten, specificeer URL van de dienst van de Verbinding van de Topologie van het wortellid.
* Om een instantie toe te laten om zich bij een topologie aan te sluiten, voeg de instantie aan de lijst van gewenste personen van de dienst van de Verbinding van de Topologie van het wortellid toe.

Gebruik de console van het Web of een sling:knoop OsgiConfig om de volgende eigenschappen van de dienst te vormen org.apache.sling.discovery.impt.Config:

<table>
 <tbody>
  <tr>
   <th>Eigenschapnaam</th>
   <th>OSGi-naam</th>
   <th>Beschrijving</th>
   <th>Standaardwaarde</th>
  </tr>
  <tr>
   <td>Time-out hartslag (seconden)</td>
   <td>hartslagTimeout</td>
   <td>De hoeveelheid tijd in seconden die moet worden gewacht op een hartslagreactie voordat de doelinstantie als niet beschikbaar wordt beschouwd. </td>
   <td>20</td>
  </tr>
  <tr>
   <td>Hartslaginterval (seconden)</td>
   <td>hartslagInterval</td>
   <td>De hoeveelheid tijd in seconden tussen hartslagen.</td>
   <td>15</td>
  </tr>
  <tr>
   <td>Minimale vertraging bij gebeurtenissen (seconden)</td>
   <td>minEventDelay</td>
   <td><p>Wanneer een verandering in de topologie voorkomt, de hoeveelheid tijd om de verandering van staat van TOPOLOGY_CHANGING in TOPOLOGY_CHANGED te vertragen. Elke verandering die voorkomt wanneer de staat TOPOLOGY_CHANGING is verhoogt de vertraging met deze hoeveelheid tijd.</p> <p>Hierdoor wordt voorkomen dat listeners overlopen door gebeurtenissen. </p> <p>Als u geen vertraging wilt gebruiken, geeft u 0 of een negatief getal op.</p> </td>
   <td>3</td>
  </tr>
  <tr>
   <td>Topology Connector-URL's</td>
   <td>topologieConnectorUrls</td>
   <td>De URLs van de Diensten van de Verbinding van de Topologie om hartslagberichten te verzenden.</td>
   <td>http://localhost:4502/libs/sling/topology/connector</td>
  </tr>
  <tr>
   <td>Lijst van gewenste personen voor topologieconnector</td>
   <td>topologieConnectorWhitelist</td>
   <td>De lijst van IP adressen of gastheernamen die de lokale dienst van de Verbinding van de Topologie in de topologie toestaat. </td>
   <td><p>localhost</p> <p>127.0.0.1</p> </td>
  </tr>
  <tr>
   <td>Naam beschrijving opslagplaats</td>
   <td>leaderSelectionRepositoryDescriptor</td>
   <td> </td>
   <td>&lt;geen waarde&gt;</td>
  </tr>
 </tbody>
</table>

Gebruik de volgende procedure om een instantie CQ met het wortellid van een topologie te verbinden. De procedure richt de instantie aan de Schakelaar URL van de Topologie van het lid van de worteltopologie. Voer deze procedure op alle leden van de topologie uit.

1. Open de webconsole in uw browser. ([ http://localhost:4502/system/console](http://localhost:4502/system/console))
1. Klik op Hoofd > Topologiebeheer.
1. Klik op Discovery Service configureren.
1. Voeg een punt aan het bezit van de Verbinding URLs van de Topologie toe, en specificeer URL van de dienst van de Verbinding van de Topologie van het lid van de worteltopologie. De URL heeft de notatie https://rootservername:4502/libs/sling/topology/connector.

Voer de volgende procedure op het wortellid van de topologie uit. De procedure voegt de namen van de andere topologieleden aan zijn lijst van gewenste personen van de Dienst van de Ontdekking toe.

1. Open de webconsole in uw browser. ([ http://localhost:4502/system/console](http://localhost:4502/system/console))
1. Klik op Hoofd > Topologiebeheer.
1. Klik op Discovery Service configureren.
1. Voor elk lid van de topologie, voeg een punt aan het bezit van de lijst van gewenste personen van de Verbinding van de Topologie toe, en specificeer de gastheernaam of IP adres van het topologielid.

## Het vormen onderwerpconsumptie {#configuring-topic-consumption}

Gebruik het Offloaden Browser om onderwerpconsumptie voor de instanties van de Experience Manager in de topologie te vormen. Voor elke instantie, kunt u de onderwerpen specificeren die het gebruikt. Bijvoorbeeld, om uw topologie te vormen zodat slechts één instantie onderwerpen van een specifiek type verbruikt, maak het onderwerp op alle instanties behalve één onbruikbaar.

De taken worden verdeeld onder instanties die het bijbehorende die onderwerp hebben door middel van round-robin logica wordt toegelaten.

1. Klik met de aanraakinterface op het tabblad Gereedschappen. ([ http://localhost:4502/tools.html](http://localhost:4502/tools.html))
1. Klik in het gebied Bewerkingen graniet op Browser offloaden.
1. Klik in het navigatievenster op Browser verschuiven.

   De offloading onderwerpen en de serverinstanties die de onderwerpen kunnen verbruiken verschijnen.

   ![ chlimage_1-113 ](assets/chlimage_1-113.png)

1. Om de consumptie van een onderwerp voor een instantie onbruikbaar te maken, onder de onderwerpnaam klik onbruikbaar maken naast de instantie.
1. Om al onderwerpconsumptie voor een instantie te vormen, klik het instantieherkenningsteken onder om het even welk onderwerp.

   ![ chlimage_1-114 ](assets/chlimage_1-114.png)

1. Klik één van de volgende knopen naast een onderwerp om het verbruiksgedrag voor de instantie te vormen, en dan sparen te klikken:

   * Ingeschakeld: deze instantie gebruikt taken van dit onderwerp.
   * Uitgeschakeld: dit exemplaar verbruikt geen banen van dit onderwerp.
   * Exclusief: dit exemplaar verbruikt slechts banen van dit onderwerp.

   **Nota:** wanneer u Uitsluitend voor een onderwerp selecteert, worden alle andere onderwerpen automatisch geplaatst aan Gehandicapten.

### Geïnstalleerde taakgebruikers {#installed-job-consumers}

Verschillende JobConsumer-implementaties worden geïnstalleerd met Experience Manager. De onderwerpen waarvoor deze JobConsumers worden geregistreerd verschijnen in het Offloaden Browser. De extra onderwerpen die verschijnen zijn die die douaneJobConsumers hebben geregistreerd. In de volgende tabel wordt de standaard JobConsumers beschreven.

| Taakonderwerp | Service PID | Beschrijving |
|---|---|---|
| / | org.apache.sling.event.impl.jobs.deprecated.EventAdminBridge | Geïnstalleerd met Apache Sling. Verwerkt banen die OSGi gebeurtenisadmin, voor achterwaartse verenigbaarheid produceert. |
| com/day/cq/replication/job/&ast; | com.day.cq.replication.impl.AgentManagerImpl | Een replicatieagent die taakladingen repliceert. |

<!--
| com/adobe/granite/workflow/offloading |com.adobe.granite.workflow.core.offloading.WorkflowOffloadingJobConsumer |Processes jobs that the DAM Update Asset Offloader workflow generates. |
-->

### Onderwerpen voor een instantie uitschakelen en inschakelen {#disabling-and-enabling-topics-for-an-instance}

De Apache Sling de dienst van de Consumentenmanager van de Baan verstrekt onderwerp lijst van gewenste personen en lijst van gewezen personen eigenschappen. Vorm deze eigenschappen om de verwerking van specifieke onderwerpen op een instantie van de Experience Manager toe te laten of onbruikbaar te maken.

**Nota:** als de instantie tot een topologie behoort, kunt u het Offloaden Browser op om het even welke computer in de topologie ook gebruiken om onderwerpen toe te laten of onbruikbaar te maken.

De logica die tot de lijst van toegelaten onderwerpen leidt staat eerst alle onderwerpen toe die in de lijst van gewenste personen zijn, en verwijdert dan onderwerpen die op de lijst van gewezen personen zijn. Standaard zijn alle onderwerpen ingeschakeld (de waarde voor de lijst van gewenste personen is `*` ) en worden geen onderwerpen uitgeschakeld (de lijst van gewezen personen heeft geen waarde).

Gebruik Webconsole of een knooppunt `sling:OsgiConfig` om de volgende eigenschappen te configureren. Voor `sling:OsgiConfig` -knooppunten is de PID van de Job Consumer Manager-service org.apache.sling.event.impl.jobs.JobConsumerManager.

| Eigenschapnaam in webconsole | OSGi-id | Beschrijving |
|---|---|---|
| Topic lijst van gewenste personen | job.consumermanager.whitelist | Een lijst met onderwerpen die de lokale dienst JobManager verwerkt. De standaardwaarde van &ast; veroorzaakt alle onderwerpen om naar de geregistreerde dienst te worden verzonden TopicConsumer. |
| Topic lijst van gewezen personen | job.consumermanager.blacklist | Een lijst met onderwerpen die de lokale JobManager-service niet verwerkt. |

## Replication-agents voor offloaden maken {#creating-replication-agents-for-offloading}

Het offloading-framework gebruikt replicatie om bronnen tussen auteur en worker te vervoeren. Het het ontladen kader leidt automatisch tot replicatieagenten wanneer de instanties zich bij de topologie aansluiten. De agenten worden gecreeerd met standaardwaarden. Verander manueel het wachtwoord dat de agenten voor authentificatie gebruiken.

>[!CAUTION]
>
>Een bekende kwestie met de automatisch geproduceerde replicatieagenten vereist u om nieuwe replicatieagenten manueel tot stand te brengen.

Creeer de replicatieagenten die baanlading tussen instanties voor het ontladen vervoeren. De volgende illustratie toont de agenten die worden vereist om van de auteur aan een arbeidersinstantie te offloaden. De auteur heeft een Sling-id van 1 en de arbeidersinstantie heeft een Sling-id van 2:

![ chlimage_1-115 ](assets/chlimage_1-115.png)

Deze opstelling vereist de volgende drie agenten:

1. Een uitgaande agent op de auteurinstantie die aan de arbeidersinstantie herhaalt.
1. Een reverse agent op de auteurinstantie die vanaf outbox op de arbeidersinstantie trekt.
1. Een outbox agent op de arbeidersinstantie.

Dit replicatieschema is vergelijkbaar met het replicatieschema dat wordt gebruikt tussen auteur- en publicatieinstanties. Voor de ontlaadsituatie zijn alle betrokken gevallen echter ontwerpgevallen.

>[!NOTE]
>
>Het kader van het Verschuiven gebruikt de topologie om de IP adressen van de het ontladen instanties te verkrijgen. Het kader leidt dan automatisch tot de replicatieagenten die op deze IP adressen worden gebaseerd. Als de IP adressen van de het ontladen instanties later veranderen, wordt de verandering automatisch verspreid op de topologie nadat de instantie opnieuw begint. Nochtans, werkt het Offloading kader niet automatisch de replicatieagenten bij om op de nieuwe IP adressen te wijzen. Om deze situatie te vermijden, gebruik vaste IP adressen voor alle instanties in de topologie.

### De replicatieagents benoemen voor offloaden {#naming-the-replication-agents-for-offloading}

Gebruik een specifiek formaat voor het ***bezit van de Naam*** van de replicatieagenten zodat het het ontladen kader automatisch de correcte agent voor specifieke arbeidersinstanties gebruikt.

**noemend de uitgaande agent op de auteursinstantie:**

`offloading_<slingid>` , waarbij `<slingid>` de id Sling is van de arbeidersinstantie.

Voorbeeld: `offloading_f5c8494a-4220-49b8-b079-360a72f71559`

**het Noemen van de omgekeerde agent op de auteursinstantie:**

`offloading_reverse_<slingid>` , waarbij `<slingid>` de id Sling is van de arbeidersinstantie.

Voorbeeld: `offloading_reverse_f5c8494a-4220-49b8-b079-360a72f71559`

**noemend outbox op de arbeidersinstantie:**

`offloading_outbox`

### Het creëren van de uitgaande agent {#creating-the-outgoing-agent}

1. Creeer de Agent van de a **Replicatie** op auteur. (Zie de [ documentatie voor replicatieagenten ](/help/sites-deploying/replication.md)). Specificeer om het even welke **Titel**. De **Naam** moet de noemende overeenkomst volgen.
1. Creeer de agent gebruikend de volgende eigenschappen:

   | Eigenschap | Waarde |
   |---|---|
   | Instellingen > Type serienummering | Standaard |
   | Transport > Transport URI | https://*`<ip of target instance>`*:*`<port>`*`/bin/receive?sling:authRequestLogin=1` |
   | Vervoer > Gebruiker van het Vervoer | Replicatiegebruiker op doelinstantie |
   | Transport > Transport Password | Replicatiewachtwoord voor doelinstantie |
   | Uitgebreid > HTTP-methode | POST |
   | Triggers > Standaard negeren | Waar |

### De reverse agent maken {#creating-the-reverse-agent}

1. Creeer de Agent van de Replicatie van de a **Omgekeerde** op auteur. (Zie de [ documentatie voor replicatieagenten ](/help/sites-deploying/replication.md).) Specificeer om het even welke **Titel**. De **Naam** moet de noemende overeenkomst volgen.
1. Creeer de agent gebruikend de volgende eigenschappen:

   | Eigenschap | Waarde |
   |---|---|
   | Instellingen > Type serienummering | Standaard |
   | Transport > Transport URI | https://*`<ip of target instance>`*:*`<port>`*`/bin/receive?sling:authRequestLogin=1` |
   | Vervoer > Gebruiker van het Vervoer | Replicatiegebruiker op doelinstantie |
   | Transport > Transport Password | Replicatiewachtwoord voor doelinstantie |
   | Uitgebreid > HTTP-methode | GET |

### Het creëren van de outbox agent {#creating-the-outbox-agent}

1. Creeer de Agent van de Replicatie van a **&#x200B;**&#x200B;op de arbeidersinstantie. (Zie de [ documentatie voor replicatieagenten ](/help/sites-deploying/replication.md).) Specificeer om het even welke **Titel**. De **Naam** moet `offloading_outbox` zijn.
1. Creeer de agent gebruikend de volgende eigenschappen.

   | Eigenschap | Waarde |
   |---|---|
   | Instellingen > Type serienummering | Standaard |
   | Transport > Transport URI | repo://var/replication/outbox |
   | Trigger > Standaard negeren | Waar |

### De verkoper-id zoeken {#finding-the-sling-id}

Verkrijg identiteitskaart van de Schuine kant van een instantie van de Experience Manager gebruikend één van beiden van de volgende methodes:

* Open de Console van het Web en, in de het Verdelen Montages, vind de waarde van het het Verdelen bezit van identiteitskaart ([ http://localhost:4502/system/console/status-slingsettings ](http://localhost:4502/system/console/status-slingsettings)). Deze methode is nuttig als de instantie nog geen deel van de topologie uitmaakt.
* Gebruik browser van de Topologie als de instantie reeds deel van de topologie uitmaakt.

<!--
## Offloading the Processing of DAM Assets {#offloading-the-processing-of-dam-assets}

Configure the instances of a topology so that specific instances perform the background processing of assets that are added or updated in DAM.

By default, Experience Manager executes the [!UICONTROL DAM Update Asset] workflow when a DAM asset changes or one is added to DAM. Change the default behavior so that Experience Manager instead executes the [!UICONTROL DAM Update Asset Offloader] workflow. This workflow generates a JobManager job that has a topic of `com/adobe/granite/workflow/offloading`. Then, configure the topology so that the job is offloaded to a dedicated worker.

>[!CAUTION]
>
>No workflow should be transient when used with workflow offloading. For example, the [!UICONTROL DAM Update Asset] workflow must not be transient when used for asset offloading. To set/unset the transient flag on a workflow, see [Transient Workflows](/help/assets/performance-tuning-guidelines.md#workflows).

The following procedure assumes the following characteristics for the offloading topology:

* One or more Experience Manager instance are authoring instances that users interact with for adding or updating DAM assets.
* Users to do not directly interact with one or more Experience Manager instances that process the DAM assets. These instances are dedicated to the background processing of DAM assets.

1. On each Experience Manager instance, configure the Discovery Service so that it points to the root Topography Connector. (See [Configuring Topology Membership](#title4).)
1. Configure the root Topography Connector so that the connecting instances are on the allow list.
1. Open Offloading Browser and disable the `com/adobe/granite/workflow/offloading` topic on the instances with which users interact to upload or change DAM assets.

   ![chlimage_1-116](assets/chlimage_1-116.png)

1. On each instance that users interact with to upload or change DAM assets, configure workflow launchers to use the [!UICONTROL DAM Update Asset Offloading] workflow:

    1. Open the Workflow console.
    1. Click the Launcher tab.
    1. Locate the two Launcher configurations that execute the [!UICONTROL DAM Update Asset] workflow. One launcher configuration event type is Node Created, and the other type is Node Modified.
    1. Change both event types so that they execute the [!UICONTROL DAM Update Asset Offloading] workflow. (For information about launcher configurations, see [Starting Workflows When Nodes Change](/help/sites-administering/workflows-starting.md).)

1. On the instances that perform the background processing of DAM assets, disable the workflow launchers that execute the [!UICONTROL DAM Update Asset] workflow.
-->

## Verdere lezing {#further-reading}

Naast de details die op deze pagina worden voorgesteld, kunt u ook het volgende lezen:

* Voor informatie over het gebruiken van Java APIs om banen en baanconsumenten tot stand te brengen, zie [ Creërend en Verbruikende Banen voor het Verschuiven ](/help/sites-developing/dev-offloading.md).
