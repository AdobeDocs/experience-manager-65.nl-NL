---
title: Taken verschuiven
seo-title: Taken verschuiven
description: Leer hoe te om instanties AEM in een topologie te vormen en te gebruiken om specifieke soorten verwerking uit te voeren.
seo-description: Leer hoe te om instanties AEM in een topologie te vormen en te gebruiken om specifieke soorten verwerking uit te voeren.
uuid: e971d403-dfd2-471f-b23d-a67e35f1ed88
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
discoiquuid: 370151df-3b8e-41aa-b586-5c21ecb55ffe
translation-type: tm+mt
source-git-commit: f24142064b15606a5706fe78bf56866f7f9a40ae

---


# Taken verschuiven{#offloading-jobs}

## Inleiding {#introduction}

Het ontladen verspreidt verwerkingstaken die de instanties van de Manager van de Ervaring in een topologie. Met offloading kunt u specifieke instanties van Experience Manager gebruiken voor het uitvoeren van specifieke typen verwerking. Met gespecialiseerde verwerking kunt u het gebruik van beschikbare serverbronnen maximaliseren.

Offloaden is gebaseerd op de functies [Apache Sling Discovery](https://sling.apache.org/documentation/bundles/discovery-api-and-impl.html) en Sling JobManager. Om het ontladen te gebruiken, voegt u de clusters van de Manager van de Ervaring aan een topologie toe en identificeert de baanonderwerpen die het clusterproces. Clusters bestaan uit een of meer instanties van Experience Manager, zodat één instantie wordt beschouwd als een cluster.

Voor informatie over het toevoegen van instanties aan een topologie, zie [het Beheer Topologieën](/help/sites-deploying/offloading.md#administering-topologies).

### Taakverdeling {#job-distribution}

Sling JobManager en JobConsumer laten de verwezenlijking van banen toe die in een topologie worden verwerkt:

* JobManager: De dienst die banen voor specifieke onderwerpen leidt.
* JobConsumer: De dienst die banen van één of meerdere onderwerpen uitvoert. De veelvoudige diensten JobConsumer kunnen voor het zelfde onderwerp worden geregistreerd.

Wanneer JobManager een baan creeert, selecteert het Offloading kader een cluster van de Manager van de Ervaring in de topologie om de baan uit te voeren:

* De cluster moet één of meerdere instanties omvatten die een JobConsumer in werking stellen die voor het baanonderwerp wordt geregistreerd.
* Het onderwerp moet voor minstens één geval in de cluster worden toegelaten.

Zie [het Vormen de Consumptie](/help/sites-deploying/offloading.md#configuring-topic-consumption) van het Onderwerp voor informatie over het raffineren van baandistributie.

![chlimage_1-109](assets/chlimage_1-109.png)

Wanneer het Offloading-framework een cluster selecteert om een taak uit te voeren en de klasse uit meerdere instanties bestaat, bepaalt Sling Distribution welke instantie in de cluster de taak uitvoert.

### Job Payloads {#job-payloads}

Het offloading-framework ondersteunt taaktaken die taken koppelen aan bronnen in de opslagplaats. Taaktaken zijn handig wanneer taken worden gemaakt voor de verwerking van bronnen en de taak wordt overgeladen naar een andere computer.

Bij het maken van een taak wordt de lading alleen gegarandeerd geplaatst op het exemplaar dat de taak maakt. Wanneer het ontladen van de baan, zorgen de replicatieagenten ervoor dat de lading op de instantie wordt gecreeerd die uiteindelijk de baan verbruikt. Wanneer de uitvoering van de taak is voltooid, zorgt omgekeerde replicatie ervoor dat de payload wordt gekopieerd naar de instantie die de taak heeft gemaakt.

## Onderwerptechnologieën beheren {#administering-topologies}

De technologieën zijn los-gekoppelde clusters van de Manager van de Ervaring die aan het ontladen deelnemen. Een cluster bestaat uit een of meer Experience Manager-serverinstanties (één instantie wordt beschouwd als een cluster).

Elke instantie van de Manager van de Ervaring stelt de volgende Verwante diensten in werking:

* Detectieservice: Verzendt verzoeken naar een Schakelaar van de Topologie om zich bij de topologie aan te sluiten.
* Topology Connector: Ontvangt om zich bij verzoeken aan te sluiten en of keurt goed of weigert elk verzoek.

De dienst van de Ontdekking van alle leden van de topologie richt aan de Schakelaar van de Topologie op één van de leden. In de volgende secties wordt dit lid het hoofdlid genoemd.

![chlimage_1-110](assets/chlimage_1-110.png)

Elke cluster in de topologie bevat een instantie die als leider wordt erkend. De clusterleider communiceert met de topologie namens de andere leden van de cluster. Wanneer de leader de cluster verlaat, wordt automatisch een nieuwe leader voor de cluster gekozen.

### De topologie weergeven {#viewing-the-topology}

Browser van de Topologie van het gebruik om de staat van de topologie te onderzoeken waarin de instantie van de Manager van de Ervaring deelneemt. Browser van de topologie toont de clusters en de instanties van de topologie.

Voor elke cluster, ziet u een lijst van clusterleden die op de orde wijst waarin elk lid zich bij de kluseter aansloot, en welk lid de Leider is. De eigenschap Current geeft de instantie aan die u momenteel beheert.

Voor elke instantie in de cluster, kunt u verscheidene op topologie betrekking hebbende eigenschappen zien:

* Een whitelist van onderwerpen voor de baanconsument van de instantie.
* De eindpunten die voor het verbinden met de topologie worden blootgesteld.
* De taakonderwerpen waarvoor de instantie is geregistreerd voor offloaden.
* De taakonderwerpen die de instantie verwerkt.

1. Klik met de aanraakinterface op het tabblad Gereedschappen. ([http://localhost:4502/tools.html](http://localhost:4502/tools.html))
1. Klik in het gebied Bewerkingen graniet op Browser offloaden.
1. Klik in het navigatievenster op Topologiebrowser.

   De clusters die aan de topologie deelnemen verschijnen.

   ![chlimage_1-111](assets/chlimage_1-111.png)

1. Klik op een cluster om een lijst weer te geven met de instanties in de cluster en hun id, huidige status en leaderstatus.
1. Klik op een instantie-id voor meer gedetailleerde eigenschappen.

U kunt de Console van het Web ook gebruiken om topologieinformatie te bekijken. De console verstrekt verdere informatie over de topologieclusters:

* Welke instantie is de lokale instantie.
* De diensten van de Verbinding van de Topologie die deze instantie gebruikt om met de topologie (uitgaande), en de diensten te verbinden die met deze (inkomende) instantie verbinden.
* De geschiedenis van de verandering voor de topologie en intentie eigenschappen.

Gebruik de volgende procedure om de pagina van het Beheer van de Topologie van de Console van het Web te openen:

1. Open de webconsole in uw browser. ([http://localhost:4502/system/console](http://localhost:4502/system/console))
1. Klik op Hoofd > Topologiebeheer.

   ![chlimage_1-112](assets/chlimage_1-112.png)

### Het vormen Lidmaatschap van de Topologie {#configuring-topology-membership}

De Apache die middel-Gebaseerde Dienst van de Ontdekking op elke instantie in werking stelt om te controleren hoe de instanties van de Manager van de Ervaring met een topologie interactie aangaan.

De dienst van de Ontdekking verzendt periodieke POST- verzoeken (hartslagen) naar de diensten van de Verbinding van de Topologie om verbindingen met de topologie te vestigen en te handhaven. De dienst van de Verbinding van de Topologie handhaaft een whitelist van IP adressen of gastheernamen die worden toegestaan om zich bij de topologie aan te sluiten:

* Om zich bij een instantie aan een topologie aan te sluiten, specificeer URL van de dienst van de Verbinding van de Topologie van het wortellid.
* Om een instantie toe te laten om zich bij een topologie aan te sluiten, voeg de instantie aan whitelist van de dienst van de Verbinding van de Topologie van het wortellid toe.

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
   <td>Whitelist van de schakelaar van de topologie</td>
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

1. Open de webconsole in uw browser. ([http://localhost:4502/system/console](http://localhost:4502/system/console))
1. Klik op Hoofd > Topologiebeheer.
1. Klik op Discovery Service configureren.
1. Voeg een punt aan het bezit van de Verbinding URLs van de Topologie toe, en specificeer URL van de dienst van de Verbinding van de Topologie van het lid van de worteltopologie. De URL heeft de notatie https://rootservername:4502/libs/sling/topology/connector.

Voer de volgende procedure op het wortellid van de topologie uit. De procedure voegt de namen van de andere topologieleden aan zijn whitelist van de Dienst van de Ontdekking toe.

1. Open de webconsole in uw browser. ([http://localhost:4502/system/console](http://localhost:4502/system/console))
1. Klik op Hoofd > Topologiebeheer.
1. Klik op Discovery Service configureren.
1. Voor elk lid van de topologie, voeg een punt aan het Whitelist bezit van de Schakelaar van de Topologie toe, en specificeer de gastheernaam of IP adres van het topologielid.

## Het vormen onderwerpconsumptie {#configuring-topic-consumption}

Gebruik het Offloaden Browser om onderwerpconsumptie voor de instanties van de Manager van de Ervaring in de topologie te vormen. Voor elke instantie, kunt u de onderwerpen specificeren die het gebruikt. Bijvoorbeeld, om uw topologie te vormen zodat slechts één instantie onderwerpen van een specifiek type verbruikt, maak het onderwerp op alle instanties behalve één onbruikbaar.

Taken zijn verspreide hoeveelheden die het bijbehorende onderwerp hebben dat is ingeschakeld met behulp van round-robin logica.

1. Klik met de aanraakinterface op het tabblad Gereedschappen. ([http://localhost:4502/tools.html](http://localhost:4502/tools.html))
1. Klik in het gebied Bewerkingen graniet op Browser offloaden.
1. Klik in het navigatievenster op Browser verschuiven.

   De offloading onderwerpen en de serverinstanties die de onderwerpen kunnen verbruiken verschijnen.

   ![chlimage_1-113](assets/chlimage_1-113.png)

1. Als u het gebruik van een onderwerp voor een instantie wilt uitschakelen, klikt u onder de bovenste naam op Uitschakelen naast de instantie.
1. Om al onderwerpconsumptie voor een instantie te vormen, klik het instantieherkenningsteken onder om het even welk onderwerp.

   ![chlimage_1-114](assets/chlimage_1-114.png)

1. Klik één van de volgende knopen naast een onderwerp om het verbruiksgedrag voor de instantie te vormen, en dan sparen te klikken:

   * Ingeschakeld: Dit exemplaar verbruikt banen van dit onderwerp.
   * Uitgeschakeld: Dit exemplaar verbruikt geen banen van dit onderwerp.
   * Exclusief: Dit exemplaar verbruikt slechts banen van dit onderwerp.
   **Opmerking:** Wanneer u Uitsluitend voor een onderwerp selecteert, worden alle andere onderwerpen automatisch geplaatst aan Gehandicapten.

### Geïnstalleerde taakgebruikers {#installed-job-consumers}

Verschillende JobConsumer-implementaties worden geïnstalleerd met Experience Manager. De onderwerpen waarvoor deze JobConsumers worden geregistreerd verschijnen in het Offloaden Browser. De extra onderwerpen die verschijnen zijn die die douaneJobConsumers hebben geregistreerd. In de volgende tabel wordt de standaard JobConsumers beschreven.

| Taakonderwerp | Service PID | Beschrijving |
|---|---|---|
| / | org.apache.sling.event.impl.jobs.deprecated.EventAdminBridge | Geïnstalleerd met Apache Sling. Verwerkt banen die OSGi gebeurtenisadmin, voor achterwaartse verenigbaarheid produceert. |
| com/day/cq/replication/job/&amp;ast; | com.day.cq.replication.impl.AgentManagerImpl | Een replicatieagent die taakladingen herhaalt. |
| com/adobe/granite/workflow/offloading | com.adobe.granite.workflow.core.offloading.WorkflowOffloadingJobConsumer | Verwerkt taken die door de workflow [!UICONTROL DAM Update Asset Offloader] worden gegenereerd. |

### Onderwerpen voor een instantie uitschakelen en inschakelen {#disabling-and-enabling-topics-for-an-instance}

De service Apache Sling Job Consumer Manager biedt whitelist- en blacklist-eigenschappen voor onderwerpen. Vorm deze eigenschappen om de verwerking van specifieke onderwerpen op een instantie van de Manager van de Ervaring toe te laten of onbruikbaar te maken.

**Opmerking:** Als de instantie tot een topologie behoort, kunt u het Offloaden Browser op om het even welke computer in de topologie ook gebruiken om onderwerpen toe te laten of onbruikbaar te maken.

De logica die de lijst van toegelaten onderwerpen creeert staat eerst alle onderwerpen toe die in whitelist zijn, en verwijdert dan onderwerpen die op de zwarte lijst zijn.Door gebrek, worden alle onderwerpen toegelaten (de whitelist waarde is `*`) en geen onderwerpen zijn gehandicapt (de zwarte lijst heeft geen waarde).

Gebruik de Console of een `sling:OsgiConfig` knoop van het Web om de volgende eigenschappen te vormen. Voor `sling:OsgiConfig` knooppunten is org.apache.sling.event.impl.jobs.JobConsumerManager de PID van de service Job Consumer Manager.

| Eigenschapnaam in webconsole | OSGi-id | Beschrijving |
|---|---|---|
| Onderwerpwhitelist | job.consumermanager.whitelist | Een lijst met onderwerpen die de lokale dienst JobManager verwerkt. De standaardwaarde van &amp;ast; veroorzaakt alle onderwerpen om naar de geregistreerde dienst te worden verzonden TopicConsumer. |
| Topic Blacklist | job.consumermanager.blacklist | Een lijst met onderwerpen die de lokale JobManager-service niet verwerkt. |

## Replication-agents voor offloaden maken {#creating-replication-agents-for-offloading}

Het offloading-framework gebruikt replicatie om bronnen tussen auteur en worker te vervoeren. Het het ontladen kader leidt automatisch tot replicatieagenten wanneer de instanties zich bij de topologie aansluiten. De agenten worden gecreeerd met standaardwaarden. U moet het wachtwoord manueel veranderen dat de agenten voor authentificatie gebruiken.

>[!CAUTION]
>
>Een bekende kwestie met de automatisch-geproduceerde replicatieagenten vereist u om nieuwe replicatieagenten manueel tot stand te brengen. Volg de procedure in [Problemen die de Automatisch Gegenereerde Agenten](/help/sites-deploying/offloading.md#problems-using-the-automatically-generated-replication-agents) van de Replicatie gebruiken alvorens u de agenten voor het Offloaden creeert.

Creeer de replicatieagenten die baanlading tussen instanties voor het ontladen vervoeren. De volgende illustratie toont de agenten die worden vereist om van de auteur aan een arbeidersinstantie te offloaden. De auteur heeft een Sling-id van 1 en de arbeidersinstantie heeft een Sling-id van 2:

![chlimage_1-115](assets/chlimage_1-115.png)

Deze opstelling vereist de volgende drie agenten:

1. Een uitgaande agent op de auteurinstantie die aan de arbeidersinstantie herhaalt.
1. Een reverse agent op de auteurinstantie die vanaf outbox op de arbeidersinstantie trekt.
1. Een outbox agent op de arbeidersinstantie.

Dit replicatieschema is vergelijkbaar met het replicatieschema dat wordt gebruikt tussen auteur- en publicatieinstanties. Voor de ontladingssituatie zijn alle betrokken gevallen echter ontwerpgevallen.

>[!NOTE]
>
>Het kader van het Verschuiven gebruikt de topologie om de IP adressen van de het ontladen instanties te verkrijgen. Het kader leidt dan automatisch tot de replicatieagenten die op deze IP adressen worden gebaseerd. Als de IP adressen van de het ontladen instanties later veranderen, wordt de verandering automatisch verlengd op de topologie nadat de instantie opnieuw begint. Nochtans, werkt het Offloading kader niet automatisch de replicatieagenten bij om op de nieuwe IP adressen te wijzen. Om deze situatie te vermijden, gebruik vaste IP adressen voor alle instanties in de topologie.

### De replicatieagents benoemen voor offloaden {#naming-the-replication-agents-for-offloading}

Gebruik een specifiek formaat voor het bezit van de ***Naam*** van de replicatieagenten zodat het het ontladen kader automatisch de correcte agent voor specifieke arbeidersinstanties gebruikt.

**De naam van de uitgaande agent op de auteurinstantie:**

`offloading_<slingid>`, waarbij `<slingid>` de id Verdelen van de arbeidersinstantie is.

Voorbeeld: `offloading_f5c8494a-4220-49b8-b079-360a72f71559`

**De reverse-agent een naam geven op de auteurinstantie:**

`offloading_reverse_<slingid>`, waarbij `<slingid>` de id Verdelen van de arbeidersinstantie is.

Voorbeeld: `offloading_reverse_f5c8494a-4220-49b8-b079-360a72f71559`

**De naam van het uitvoervak in de worker-instantie:**

`offloading_outbox`

### Het creëren van de uitgaande agent {#creating-the-outgoing-agent}

1. Creeer een Agent **van de** Replicatie op auteur. (Zie het [document voor replicatieagenten](/help/sites-deploying/replication.md)). Geef een **titel** op. De **naam** moet de naamgevingsconventie volgen.
1. Creeer de agent gebruikend de volgende eigenschappen:

   | Eigenschap | Waarde |
   |---|---|
   | Instellingen > Type serienummering | Standaard |
   | Transport > Transport URI | https://*`<ip of target instance>`*:*`<port>`*`/bin/receive?sling:authRequestLogin=1` |
   | Transport > Transport-gebruiker | Replicatiegebruiker op doelinstantie |
   | Transport > Transportwachtwoord | Replicatiewachtwoord voor doelinstantie |
   | Uitgebreid > HTTP-methode | POST |
   | Triggers > Standaard negeren | Waar |

### De reverse agent maken {#creating-the-reverse-agent}

1. Maak een **reverse Replication Agent** bij de auteur. (Zie het [document voor replicatieagenten](/help/sites-deploying/replication.md).) Geef een **titel** op. De **naam** moet de naamgevingsconventie volgen.
1. Creeer de agent gebruikend de volgende eigenschappen:

   | Eigenschap | Waarde |
   |---|---|
   | Instellingen > Type serienummering | Standaard |
   | Transport > Transport URI | https://*`<ip of target instance>`*:*`<port>`*`/bin/receive?sling:authRequestLogin=1` |
   | Transport > Transport-gebruiker | Replicatiegebruiker op doelinstantie |
   | Transport > Transportwachtwoord | Replicatiewachtwoord voor doelinstantie |
   | Uitgebreid > HTTP-methode | GET |

### Het creëren van de outbox agent {#creating-the-outbox-agent}

1. Creeer een Agent **van de** Replicatie op de arbeidersinstantie. (Zie het [document voor replicatieagenten](/help/sites-deploying/replication.md).) Geef een **titel** op. De **naam** moet `offloading_outbox`zijn.
1. Creeer de agent gebruikend de volgende eigenschappen.

   | Eigenschap | Waarde |
   |---|---|
   | Instellingen > Type serienummering | Standaard |
   | Transport > Transport URI | repo://var/replication/outbox |
   | Trigger > Standaard negeren | Waar |

### De verkoper-id zoeken {#finding-the-sling-id}

Verkrijg identiteitskaart van het Verdelen van een instantie van de Manager van de Ervaring gebruikend één van beide volgende methodes:

* Open de Console van het Web en, in de het Verdelen Montages, vind de waarde van het het Verdelen bezit van identiteitskaart ([http://localhost:4502/system/console/status-slingsettings](http://localhost:4502/system/console/status-slingsettings)). Deze methode is nuttig als de instantie nog geen deel van de topologie uitmaakt.
* Gebruik browser van de Topologie als de instantie reeds deel van de topologie uitmaakt.

## De verwerking van DAM-activa verschuiven {#offloading-the-processing-of-dam-assets}

Vorm de instanties van een topologie zodat de specifieke instanties de achtergrondverwerking van activa uitvoeren die in DAM worden toegevoegd of bijgewerkt.

Standaard voert Experience Manager de workflow [!UICONTROL DAM Update Asset] uit wanneer een DAM-element wordt gewijzigd of een element wordt toegevoegd aan DAM. Wijzig het standaardgedrag, zodat Experience Manager in plaats daarvan de workflow [!UICONTROL DAM Asset Offloader] bijwerken uitvoert. Deze workflow genereert een JobManager-taak met een onderwerp `com/adobe/granite/workflow/offloading`. Dan, vorm de topologie zodat de baan aan een specifieke worker wordt geoffload.

>[!CAUTION]
>
>Er mag geen tijdelijke workflow worden gebruikt bij het offloaden van de workflow. De workflow [!UICONTROL DAM Update Asset] mag bijvoorbeeld niet van voorbijgaande aard zijn wanneer deze wordt gebruikt voor het offloaden van middelen. Zie [Tijdelijke workflows](/help/assets/performance-tuning-guidelines.md#workflows)voor informatie over het instellen/ongedaan maken van de overgangsmarkering voor een workflow.

De volgende procedure veronderstelt de volgende kenmerken voor de het ontladen topologie:

* Een of meer instanties van Experience Manager zijn ontwerpinstanties waarmee gebruikers werken bij het toevoegen of bijwerken van DAM-elementen.
* Gebruikers kunnen niet rechtstreeks communiceren met een of meer instanties van Experience Manager die de DAM-elementen verwerken. Deze instanties zijn gewijd aan de achtergrondverwerking van DAM-middelen.

1. Voor elke instantie van de Manager van de Ervaring, vorm de Dienst van de Ontdekking zodat het aan de schakelaar van de wortelTopografie richt. (Zie [het Vormen Lidmaatschap](#title4)van Topologie.)
1. Vorm de schakelaar van de wortelTopografie zodat de verbindende instanties op whitelist zijn.
1. Open de Offloading Browser en maak het `com/adobe/granite/workflow/offloading` onderwerp op de instanties onbruikbaar waarmee de gebruikers om activa te uploaden of te veranderen DAM met elkaar in wisselwerking staan.

   ![chlimage_1-116](assets/chlimage_1-116.png)

1. Voor elke instantie waarmee gebruikers communiceren om DAM-elementen te uploaden of te wijzigen, configureert u workflowdraagraketten zo dat ze de workflow voor het offloaden van [!UICONTROL DAM-middelen] gebruiken:

   1. Open de Workflowconsole.
   1. Klik op het tabblad Launcher.
   1. Zoek de twee opstartconfiguraties die de workflow [!UICONTROL DAM Update Asset] uitvoeren. Één type van de de gebeurtenisgebeurtenis van de lanceringsconfiguratie is Gemaakt Knoop, en het andere type is Gewijzigde Knoop.
   1. Wijzig beide gebeurtenistypen, zodat ze de workflow voor het offloaden van [!UICONTROL middelen door DAM-update] uitvoeren. (Zie Workflows [starten wanneer knooppunten worden gewijzigd](/help/sites-administering/workflows-starting.md)voor informatie over startconfiguraties.)

1. Schakel in de gevallen waarin de achtergrondverwerking van DAM-elementen wordt uitgevoerd de werkstroomstartprogramma&#39;s uit die de workflow [!UICONTROL DAM Update Asset] uitvoeren.

## Meer informatie {#further-reading}

Naast de details op deze pagina kunt u ook het volgende lezen:

* Voor informatie over het gebruiken van Java APIs om banen en baanconsumenten tot stand te brengen, zie het [Creëren en het Verbruiken van Banen voor het Offloaden](/help/sites-developing/dev-offloading.md).
