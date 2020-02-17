---
title: Tips en trucs om de implementatie van AEM-middelen te controleren
description: Aanbevolen procedures om de omgeving en prestaties van uw AEM-instantie te controleren nadat deze is geïmplementeerd.
contentOwner: AG
translation-type: tm+mt
source-git-commit: b0555655bceda4b1ac4a9f14029778387b223c2f

---


# Tips en trucs om de implementatie van AEM-middelen te controleren {#assets-monitoring-best-practices}

Vanuit het standpunt van de Middelen van de Manager van de Ervaring van Adobe (AEM), zou de controle het waarnemen van en het melden van de volgende processen en de technologieën moeten omvatten:

* SysteemCPU
* Systeemgeheugengebruik
* Systeemschijf-IO en IO-wachttijd
* IO van systeemnetwerk
* JMX MBans voor het gebruik van de heap en asynchrone processen, zoals werkschema&#39;s
* Gezondheidscontroles op de OSGi-console

AEM-middelen kunnen doorgaans op twee manieren worden gecontroleerd: live controle en langdurige bewaking.

## Live bewaking {#live-monitoring}

U zou levende controle tijdens de prestaties testende fase van uw ontwikkeling of tijdens high-load situaties moeten uitvoeren om de prestatieskenmerken van uw milieu te begrijpen. Doorgaans moet live controle worden uitgevoerd met behulp van een reeks gereedschappen. Hier volgen enkele aanbevelingen:

* [Visuele VM](https://visualvm.java.net/): Met Visuele VM kunt u gedetailleerde Java VM-informatie weergeven, zoals CPU-gebruik en Java-geheugengebruik. Bovendien kunt u code die op een instantie wordt uitgevoerd, kopiëren en evalueren.
* [Boven](https://man7.org/linux/man-pages/man1/top.1.html): De bovenkant is een bevel van Linux dat omhoog een dashboard opent, dat gebruiksstatistieken, met inbegrip van cpu, geheugen, en gebruik IO toont. Het biedt een overzicht op hoog niveau van wat er op een instantie gebeurt.
* [Bovenkant](https://hisham.hm/htop/): Htop is een interactieve procesviewer. Deze biedt naast wat Top kan bieden, een gedetailleerd CPU- en geheugengebruik. De bovenkant kan op de meeste systemen van Linux worden geïnstalleerd gebruikend `yum install htop` of `apt-get install htop`.

* [Iotop](https://guichaz.free.fr/iotop/): Iotop is een gedetailleerd dashboard voor schijf-IO-gebruik. Het toont bars en meters die de processen beschrijven die schijf IO en de hoeveelheid gebruiken zij. Iotop kan op de meeste systemen van Linux worden geïnstalleerd gebruikend `yum install iotop` of `apt-get install iotop`.

* [IFP](https://www.ex-parrot.com/pdw/iftop/): Internet toont gedetailleerde informatie over Ethernet/netwerkgebruik. De vertoningen van IFP per communicatiekanaalstatistieken over de entiteiten die ethernet gebruiken en de hoeveelheid bandbreedte zij gebruiken. Installeer Ftop op de meeste systemen van Linux gebruikend `yum install iftop` of `apt-get install iftop`.

* Java Flight Recorder (JFR): Een commercieel hulpmiddel van Oracle dat u vrij in niet-productiemilieu&#39;s kunt gebruiken. Voor meer details, zie [hoe te om Vlucht Java te gebruiken Recorder om CQ Runtime Problemen](https://cq-ops.tumblr.com/post/73865704329/how-to-use-java-flight-recorder-to-diagnose-cq)te diagnostiseren.
* AEM-bestand error.log: U kunt het AEM error.log- dossier voor details van fouten onderzoeken die in het systeem worden geregistreerd. Gebruik het bevel `tail -F quickstart/logs/error.log` om fouten te identificeren die u zou moeten onderzoeken.
* [Workflowconsole](/help/sites-administering/workflows.md): Gebruik de workflowconsole om workflows te controleren die achterblijven of vastlopen.

Gewoonlijk gebruikt u deze gereedschappen samen om een uitgebreid idee te krijgen van de prestaties van uw AEM-instantie.

>[!NOTE]
>
>Dit zijn standaardgereedschappen die niet rechtstreeks door Adobe worden ondersteund. Ze hebben geen extra licenties nodig.

![chlimage_1-33](assets/chlimage_1-143.png)

*Afbeelding: Live bewaking met behulp van Visual VM*


![chlimage_1-32](assets/chlimage_1-142.png)

## Controle op lange termijn {#long-term-monitoring}

Bij langdurige bewaking van een AEM-instantie moeten dezelfde delen die live worden gecontroleerd, langer worden gecontroleerd. Het omvat ook het definiëren van waarschuwingen die specifiek zijn voor uw omgeving.

### Aggregatie en rapportage van stamhout {#log-aggregation-and-reporting}

Er zijn verscheidene hulpmiddelen beschikbaar om logboeken samen te voegen, bijvoorbeeld Splunk(TM) en Elastic Search/Logstash/Kabana (ELK). Om de uptime van uw instantie te evalueren AEM, is het belangrijk voor u om logboekgebeurtenissen te begrijpen specifiek voor uw systeem en alarm tot stand te brengen die op hen wordt gebaseerd. Een goede kennis van uw ontwikkeling en verrichtingspraktijken kan u helpen beter begrijpen hoe te om uw proces van de logboeksamenvoeging te stemmen om kritieke alarm te produceren.

### Milieu-monitoring {#environment-monitoring}

De bewaking van het milieu omvat de bewaking van het volgende:

* Netwerkdoorvoer
* Schijf-IO
* Geheugen
* CPU-gebruik
* JMX MBeans
* Externe websites

U hebt externe hulpmiddelen nodig, zoals NewRelic(TM) en AppDynamics(TM) om elk item te controleren. Met deze gereedschappen kunt u waarschuwingen definiëren die specifiek zijn voor uw systeem, zoals een hoog systeemgebruik, een back-up van de workflow, storingen in de health check of niet-geverifieerde toegang tot uw website. Adobe raadt geen bepaalde gereedschappen aan boven andere. Zoek het hulpmiddel dat voor u werkt, en hefboomwerking het om de besproken punten te controleren.

#### Interne toepassingsbewaking {#internal-application-monitoring}

De interne toepassingscontrole omvat het controleren van de toepassingscomponenten die de AEM-stapel, met inbegrip van JVM, de inhoudsbewaarplaats vormen, en controle door de code van de douanetoepassing die op het platform wordt gebouwd. In het algemeen wordt het uitgevoerd via JMX-boonen die rechtstreeks kunnen worden gecontroleerd door veel populaire monitoroplossingen, zoals SolarWinds (TM), HP OpenView(TM), Hyperic(TM), Zabbix(TM) en andere. Voor systemen die geen directe verbinding met JMX ondersteunen, kunt u shellscripts schrijven om de JMX-gegevens te extraheren en aan deze systemen beschikbaar te maken in een indeling die ze zelf begrijpen.

Externe toegang tot de JMX-mabeans is niet standaard ingeschakeld. Voor meer informatie over controle door JMX, zie [Controle en Beheer Gebruikend Technologie](https://docs.oracle.com/javase/7/docs/technotes/guides/management/agent.html)JMX.

In veel gevallen is een basislijn nodig om een statistiek effectief te kunnen controleren. Als u een basislijn wilt maken, observeert u het systeem onder normale bedrijfsomstandigheden gedurende een vooraf bepaalde periode en identificeert u vervolgens de normale maatstaf.

**JVM-bewaking**

Net als bij elke op Java gebaseerde toepassingsstapel, is AEM afhankelijk van de bronnen die er via de onderliggende Java Virtual Machine aan worden geleverd. U kunt de status van veel van deze bronnen controleren via Platform MXBeans die door JVM beschikbaar worden gemaakt. Voor meer informatie over MXBeans, zie het [Gebruiken van de Server van het Platform MBean en Platform MXBeans](https://docs.oracle.com/javase/7/docs/technotes/guides/management/mxbeans.html).

Hier volgen enkele basislijnparameters die u kunt controleren voor JVM:

Geheugen

* `MBean: lava.lang:type=Memory`
* URL: `/system/console/jmx/java.lang:type=Memory`
* Instanties: Alle servers
* Alarmdrempel: Wanneer het heap- of non-heap-geheugengebruik meer dan 75% van het overeenkomstige maximale geheugen bedraagt.
* Alarmdefinitie: Het systeemgeheugen is onvoldoende of er is een geheugenlek in de code. Analyseer een draadstortplaats om bij een definitie aan te komen.

>[!Nofferte]
>
>De informatie die door dit boon wordt verstrekt wordt uitgedrukt in bytes.

Threads

* MBean: `java.lang:type=Threading`
* URL: `/system/console/jmx/java.lang:type=Threading`
* Instanties: Alle servers
* Alarmdrempel: Wanneer het aantal draden groter is dan 150% van de basislijn.
* Alarmdefinitie: Of er is een actief wegloopproces, of een inefficiënte verrichting verbruikt een grote hoeveelheid middelen. Analyseer een draadstortplaats om bij een definitie aan te komen.

**AEM-bewaking**

AEM stelt ook een reeks statistieken en verrichtingen door JMX bloot. Deze kunnen helpen systeemgezondheid beoordelen en potentiële problemen identificeren alvorens zij gebruikers beïnvloeden. Zie de [documentatie](/help/sites-administering/jmx-console.md) over AEM JMX MBeans voor meer informatie.

Hier volgen enkele basislijnparameters die u voor AEM kunt controleren:

Replication-agents

* MBean: `com.adobe.granite.replication:type=agent,id=”<AGENT_NAME>”`
* URL: `/system/console/jmx/com.adobe.granite.replication:type=agent,id=”<AGENT_NAME>"`
* Instanties: Eén auteur en alle publicatie-instanties (voor uitlijningsmiddelen)
* Alarmdrempel: Wanneer de waarde van `QueueBlocked` is `true` of de waarde van `QueueNumEntries` groter is dan 150% van de basislijn.

* Alarmdefinitie: Aanwezigheid van een geblokkeerde rij in het systeem erop wijst die dat het replicatiedoel neer of onbereikbaar is. Vaak leiden netwerk- of infrastructuurproblemen ertoe dat overdreven items in de wachtrij worden geplaatst, wat de systeemprestaties nadelig kan beïnvloeden.

>[!Nofferte]
>
>Voor de parameters MBean en URL, vervang `<AGENT_NAME>` met de naam van de replicatieagent u wilt controleren.

Sessieteller

* MBean: `org.apache.jackrabbit.oak:id=7,name="OakRepository Statistics",type="RepositoryStats"`
* URL: */system/console/jmx/org.apache.jackrabbit.oak:id=7,name=&quot;OakRepository Statistics&quot;,type*=&quot;RepositoryStats&quot;
* Instanties: Alle servers
* Alarmdrempel: Wanneer geopende sessies de basislijn met meer dan 50% overschrijden.
* Alarmdefinitie: Sessies kunnen worden geopend via een stuk code en nooit worden gesloten. Dit kan in de loop der tijd langzaam gebeuren en uiteindelijk geheugenlekken in het systeem veroorzaken. Hoewel het aantal sessies op een systeem moet fluctueren, mogen ze niet voortdurend toenemen.

Gezondheidscontroles

Health checks die beschikbaar zijn in het [bewerkingsdashboard](/help/sites-administering/operations-dashboard.md#health-reports) hebben overeenkomstige JMX MBans voor controle. Nochtans, kunt u de controles van de douanegezondheid schrijven om extra systeemstatistieken bloot te stellen.

Hier zijn een aantal uit-van-de-doos gezondheidscontroles die nuttig zijn om te controleren:

* Systeemcontroles
   * MBean: `org.apache.sling.healthcheck:name=systemchecks,type=HealthCheck`
   * URL: `/system/console/jmx/org.apache.sling.healthcheck:name=systemchecks,type=HealthCheck`
   * Instanties: Eén auteur, alle publicatieservers
   * Alarmdrempel: Wanneer de status niet OK is
   * Alarmdefinitie: De status van een van de meetwaarden is WAARSCHUWING of KRITIEK. Controleer de logboekattributen voor meer informatie over de oorzaak van de kwestie.

* Replicatiereeks

   * MBean: `org.apache.sling.healthcheck:name=replicationQueue,type=HealthCheck `
   * URL: `/system/console/jmx/org.apache.sling.healthcheck:name=replicationQueue,type=HealthCheck`
   * Instanties: Eén auteur, alle publicatieservers
   * Alarmdrempel: Wanneer de status niet OK is
   * Alarmdefinitie: De status van een van de meetwaarden is WAARSCHUWING of KRITIEK. Controleer de logboekattributen voor meer informatie over de rij die de kwestie veroorzaakte.

* Responsprestaties

   * MBean: `org.apache.sling.healthcheck:name=requestsStatus,type=HealthCheck`
   * URL: `/system/console/jmx/org.apache.sling.healthcheck:name=requestsStatus,type=HealthCheck`
   * Instanties: Alle servers
   * Duur van waarschuwing: Wanneer de status niet OK is
   * Alarmdefinitie: De status van een van de meetwaarden is WAARSCHUWING of KRITIEKE status. Controleer de logboekattributen voor meer informatie over de rij die de kwestie veroorzaakte.

* Query-prestaties

   * MBean: `org.apache.sling.healthcheck:name=queriesStatus,type=HealthCheck`
   * URL: `/system/console/jmx/org.apache.sling.healthcheck:name= queriesStatus,type=HealthCheck`
   * Instanties: Eén auteur, alle publicatieservers
   * Alarmdrempel: Wanneer de status niet OK is
   * Alarmdefinitie: Één of meerdere vragen die langzaam in het systeem lopen. Controleer de logboekattributen voor meer informatie over de vragen die de kwestie veroorzaakten.

* Actieve pakketten

   * MBean: `org.apache.sling.healthcheck:name=inactiveBundles,type=HealthCheck`
   * URL: `/system/console/jmx/org.apache.sling.healthcheck:name=inactiveBundles,type=HealthCheck`
   * Instanties: Alle servers
   * Alarmdrempel: Wanneer de status niet OK is
   * Alarmdefinitie: Aanwezigheid van inactieve of onopgeloste OSGi-bundels op het systeem. Controleer het logkenmerk voor meer informatie over de bundels die de uitgave hebben veroorzaakt.

* Logfouten

   * MBean: `org.apache.sling.healthcheck:name=logErrorHealthCheck,type=HealthCheck`
   * URL: `/system/console/jmx/org.apache.sling.healthcheck:name=logErrorHealthCheck,type=HealthCheck`
   * Instanties: Alle servers
   * Alarmdrempel: Wanneer de status niet OK is
   * Alarmdefinitie: De logbestanden bevatten fouten. Controleer de logboekattributen voor meer informatie over de oorzaak van de kwestie.

## Gemeenschappelijke kwesties en resoluties {#common-issues-and-resolutions}

Tijdens het proces van controle, als u problemen ontmoet, zijn hier sommige het oplossen van problementaken die u kunt uitvoeren om gemeenschappelijke kwesties met instanties op te lossen AEM:

* Als u TarMK gebruikt, voert u de Tar-compressie vaak uit. Zie [De opslagplaats](/help/sites-deploying/storage-elements-in-aem-6.md#maintaining-the-repository)onderhouden voor meer informatie.
* Logboeken `OutOfMemoryError` controleren. Zie [Geheugenproblemen](https://helpx.adobe.com/experience-manager/kb/AnalyzeMemoryProblems.html)analyseren voor meer informatie.

* Controleer de logboeken om het even welke verwijzingen naar unindexed vragen, boomstamtraversals, of indextraversals. Deze wijzen op unindexed vragen of op ontoereikend geïndexeerde vragen. Voor beste praktijken bij het optimaliseren van vraag en het indexeren prestaties, zie [Beste praktijken voor vragen en het indexeren](/help/sites-deploying/best-practices-for-queries-and-indexing.md).
* Gebruik de workflowconsole om te controleren of uw workflows naar behoren werken. Indien mogelijk kunt u meerdere workflows samenvoegen tot één workflow.
* Herzie live monitoring en zoek naar extra knelpunten of hoge consumenten van specifieke hulpbronnen.
* Onderzoek de uitgang punten van het cliëntnetwerk en de ingangen richten aan het AEM instantienetwerk, met inbegrip van de verzender. Dit zijn vaak knelpunten. Zie [Elementennetwerkoverwegingen](/help/assets/assets-network-considerations.md)voor meer informatie.
* Maak uw AEM-server groter. U kunt een AEM-instantie van onvoldoende grootte hebben. De Steun van Adobe kan u helpen identificeren of uw server ondermaats is.
* Onderzoek de `access.log` en de `error.log` dossiers voor ingangen rond de tijd van iets fout ging. Zoek naar patronen die op anomalieën van de douanecode kunnen wijzen. Voeg deze toe aan de lijst met gebeurtenissen die u controleert.
