---
title: Beste praktijken om  [!DNL Assets]  plaatsing te controleren
description: De beste praktijken om het milieu en de prestaties van uw  [!DNL Adobe Experience Manager]  plaatsing te controleren nadat het wordt opgesteld.
contentOwner: AG
role: Admin, Architect
feature: Asset Management
exl-id: a9e1bd6b-c768-4faa-99a3-7110693998dc
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1639'
ht-degree: 0%

---

# Aanbevolen procedures om de implementatie van [!DNL Adobe Experience Manager Assets] te controleren {#assets-monitoring-best-practices}

Vanuit het standpunt van [!DNL Experience Manager Assets] zou de controle het waarnemen van en het melden van de volgende processen en technologieën moeten omvatten:

* SysteemCPU
* Systeemgeheugengebruik
* Systeemschijf-IO en IO-wachttijd
* IO van systeemnetwerk
* JMX MBans voor het gebruik van de heap en asynchrone processen, zoals werkschema&#39;s
* Health checks OSGi-console

[!DNL Experience Manager Assets] kan doorgaans op twee manieren worden gecontroleerd: live controle en langdurige controle.

## Live bewaking {#live-monitoring}

U zou levende controle tijdens de prestaties testende fase van uw ontwikkeling of tijdens high-load situaties moeten uitvoeren om de prestatieskenmerken van uw milieu te begrijpen. Doorgaans moet live controle worden uitgevoerd met behulp van een reeks gereedschappen. Hier volgen enkele aanbevelingen:

* [&#x200B; Visuele VM &#x200B;](https://visualvm.github.io/): Visuele VM laat u toe om gedetailleerde informatie van Java VM, met inbegrip van het gebruik van cpu, het geheugengebruik van Java te bekijken. Bovendien laat het u code steekproef en evalueren die op een plaatsing loopt.
* [&#x200B; Hoogste &#x200B;](https://man7.org/linux/man-pages/man1/top.1.html): De bovenkant is een bevel van Linux dat omhoog een dashboard opent, dat gebruiksstatistieken, met inbegrip van cpu, geheugen, en gebruik IO toont. Het biedt een overzicht op hoog niveau van wat er op een instantie gebeurt.
* [&#x200B; Htop &#x200B;](https://hisham.hm/htop/): De bovenkant is een interactieve proceskijker. Deze biedt naast wat Top kan bieden, een gedetailleerd CPU- en geheugengebruik. De bovenkant kan op de meeste systemen van Linux worden geïnstalleerd gebruikend `yum install htop` of `apt-get install htop`.

* Iotop: Iotop is een gedetailleerd dashboard voor gebruik van schijf-IO. Het toont bars en meters die de processen beschrijven die schijf IO en de hoeveelheid gebruiken zij. Iotop kan op de meeste Linux-systemen worden geïnstalleerd met `yum install iotop` of `apt-get install iotop` .

* [&#x200B; IFP &#x200B;](https://www.ex-parrot.com/pdw/iftop/): De vertoningen van IFIP gedetailleerde informatie over Ethernet/netwerkgebruik. De vertoningen van de top per de statistieken van het communicatiekanaal over de entiteiten die ethernet gebruiken en de hoeveelheid bandbreedte zij gebruiken. Als dit op de meeste Linux-systemen mogelijk is, gebruikt u `yum install iftop` of `apt-get install iftop` .

* Java Flight Recorder (JFR): een commercieel hulpmiddel van Oracle dat u vrij kunt gebruiken in niet-productieomgevingen. Voor meer details, zie [&#x200B; hoe te om Java te gebruiken Recorder van de Vlucht om CQ Runtime Problemen &#x200B;](https://cq-ops.tumblr.com/post/73865704329/how-to-use-java-flight-recorder-to-diagnose-cq) te diagnostiseren.
* [!DNL Experience Manager] `error.log` -bestand: u kunt het [!DNL Experience Manager] `error.log` -bestand zoeken op details van fouten die in het systeem zijn aangemeld. Gebruik het bevel `tail -F quickstart/logs/error.log` om fouten te identificeren om te onderzoeken.
* [&#x200B; console van het Werkschema &#x200B;](/help/sites-administering/workflows.md): Hefboomwerking de werkschemaconsole om werkschema&#39;s te controleren die achterblijven of geplakt raken.

Doorgaans gebruikt u deze gereedschappen samen om een uitgebreid idee te krijgen van de prestaties van uw [!DNL Experience Manager] -implementatie.

>[!NOTE]
>
>Dit zijn standaardgereedschappen die niet rechtstreeks door de Adobe worden ondersteund. Ze hebben geen extra licenties nodig.

![&#x200B; chlimage_1-33 &#x200B;](assets/chlimage_1-143.png)

*Cijfer: Levende controle die het Visuele hulpmiddel van VM gebruikt.*

![&#x200B; chlimage_1-32 &#x200B;](assets/chlimage_1-142.png)

## Controle op lange termijn {#long-term-monitoring}

Voor langetermijnbewaking van een [!DNL Experience Manager] -implementatie moet u dezelfde delen die live worden bewaakt, gedurende een langere periode controleren. Het omvat ook het definiëren van waarschuwingen die specifiek zijn voor uw omgeving.

### Aggregatie en rapportage van stamhout {#log-aggregation-and-reporting}

Er zijn verscheidene hulpmiddelen beschikbaar om logboeken samen te voegen, bijvoorbeeld, Splunk(TM) en Elastic Search, Logstash, en Kabana (ELK). Om de uptime van uw [!DNL Experience Manager] plaatsing te evalueren, is het belangrijk voor u om logboekgebeurtenissen te begrijpen specifiek voor uw systeem en alarm tot stand te brengen die op hen wordt gebaseerd. Een goede kennis van uw ontwikkeling en verrichtingspraktijken kan u helpen beter begrijpen hoe te om uw proces van de logboeksamenvoeging te stemmen om kritieke alarm te produceren.

### Milieu-monitoring {#environment-monitoring}

De bewaking van het milieu omvat de bewaking van het volgende:

* Netwerkdoorvoer
* IO schijf
* Geheugen
* CPU-gebruik
* JMX MBeans
* Externe websites

U hebt externe hulpmiddelen nodig, zoals NewRelic(TM) en AppDynamics(TM) om elk item te controleren. Met deze gereedschappen kunt u waarschuwingen definiëren die specifiek zijn voor uw systeem, zoals een hoog systeemgebruik, back-up van de workflow, storingen in de health check of niet-geverifieerde toegang tot uw website. Adobe beveelt geen bepaalde gereedschappen aan boven andere. Zoek het hulpmiddel dat voor u werkt, en gebruik het om de besproken punten te controleren.

#### Interne controle van toepassingen {#internal-application-monitoring}

Interne toepassingsbewaking omvat het controleren van de toepassingscomponenten die de [!DNL Experience Manager] -stapel vormen, waaronder JVM, de opslagplaats voor inhoud, en het controleren via aangepaste toepassingscode die op het platform is gebaseerd. In het algemeen wordt het uitgevoerd via JMX-boonen die rechtstreeks kunnen worden gecontroleerd door veel populaire monitoroplossingen, zoals SolarWinds (TM), HP OpenView(TM), Hyperic(TM), Zabbix(TM) en andere. Voor systemen die geen directe verbinding met JMX ondersteunen, kunt u shellscripts schrijven om de JMX-gegevens te extraheren en aan deze systemen beschikbaar te maken in een indeling die ze zelf begrijpen.

Externe toegang tot de JMX-mabeans is niet standaard ingeschakeld. Voor meer informatie bij controle door JMX, zie [&#x200B; Controle en Beheer Gebruikend Technologie JMX &#x200B;](https://docs.oracle.com/javase/7/docs/technotes/guides/management/agent.html).

In veel gevallen is een basislijn nodig om een statistiek effectief te kunnen controleren. Als u een basislijn wilt maken, observeert u het systeem onder normale bedrijfsomstandigheden gedurende een vooraf bepaalde periode en identificeert u vervolgens de normale maatstaf.

**JVM controle**

Net als bij elke op Java gebaseerde toepassingsstapel, hangt [!DNL Experience Manager] af van de bronnen die er via de onderliggende virtuele Java-machine aan worden geleverd. U kunt de status van veel van deze bronnen controleren via Platform MXBeans die door JVM beschikbaar worden gemaakt. Voor meer informatie over MXBeans, zie [&#x200B; Gebruikend de Server van het Platform MBean en Platform MXBeans &#x200B;](https://docs.oracle.com/javase/7/docs/technotes/guides/management/mxbeans.html).

Hier volgen enkele basislijnparameters die u kunt controleren voor JVM:

Geheugen

* `MBean: lava.lang:type=Memory`
* URL: `/system/console/jmx/java.lang:type=Memory`
* Instanties: alle servers
* Alarmdrempel: wanneer het heap- of niet-heapgeheugengebruik meer dan 75% van het overeenkomstige maximale geheugen bedraagt.
* Alarmdefinitie: systeemgeheugen is onvoldoende of er is een geheugenlek in de code. Analyseer een draadstortplaats om bij een definitie aan te komen.

>[!NOTE]
>
>De informatie die door dit boon wordt verstrekt wordt uitgedrukt in bytes.

Threads

* MBean: `java.lang:type=Threading`
* URL: `/system/console/jmx/java.lang:type=Threading`
* Instanties: alle servers
* Alarmdrempel: wanneer het aantal threads groter is dan 150% van de basislijn.
* Alarm definition: Of er is een actief wegloopproces, of een inefficiënte verrichting verbruikt een grote hoeveelheid middelen. Analyseer een draadstortplaats om bij een definitie aan te komen.

**Monitor[!DNL Experience Manager]**

[!DNL Experience Manager] stelt ook een reeks statistieken en verrichtingen door JMX bloot. Deze kunnen helpen systeemgezondheid beoordelen en potentiële problemen identificeren alvorens zij gebruikers beïnvloeden. Voor meer informatie, zie [&#x200B; documentatie &#x200B;](/help/sites-administering/jmx-console.md) op [!DNL Experience Manager] JMX MBeans.

Hier volgen enkele basislijnparameters die u kunt controleren voor [!DNL Experience Manager] :

Replication-agents

* MBean: `com.adobe.granite.replication:type=agent,id="<AGENT_NAME>"`
* URL: `/system/console/jmx/com.adobe.granite.replication:type=agent,id="<AGENT_NAME>"`
* Instanties: één auteur en alle publicatie-instanties (voor uitlijningsmiddelen)
* Alarmdrempel: wanneer de waarde van `QueueBlocked` `true` of de waarde van `QueueNumEntries` groter is dan 150% van de basislijn.

* Alarmdefinitie: Aanwezigheid van een geblokkeerde rij in het systeem die erop wijst dat het replicatiedoel neer of onbereikbaar is. Vaak leiden netwerk- of infrastructuurproblemen ertoe dat overdreven items in de wachtrij worden geplaatst, wat de systeemprestaties nadelig kan beïnvloeden.

>[!NOTE]
>
>Voor de parameters MBean en URL, vervang `<AGENT_NAME>` met de naam van de replicatieagent u wilt controleren.

Sessieteller

* MBean: `org.apache.jackrabbit.oak:id=7,name="OakRepository Statistics",type="RepositoryStats"`
* URL: */system/console/jmx/org.apache.jackrabbit.oak:id=7,name= &quot;Statistieken OakRepository&quot;, type*= &quot;RepositoryStats&quot;
* Instanties: alle servers
* Alarmdrempel: wanneer open sessies de basislijn met meer dan 50% overschrijden.
* Alarmdefinitie: sessies kunnen worden geopend via een stuk code en nooit worden gesloten. Dit kan in de loop der tijd langzaam gebeuren en uiteindelijk geheugenlekken in het systeem veroorzaken. Hoewel het aantal sessies op een systeem moet fluctueren, mogen ze niet voortdurend toenemen.

Gezondheidscontroles

De controles van de gezondheid die in het [&#x200B; verrichtingendashboard &#x200B;](/help/sites-administering/operations-dashboard.md#health-reports) beschikbaar zijn hebben overeenkomstige JMX MBans voor controle. Nochtans, kunt u de controles van de douanegezondheid schrijven om extra systeemstatistieken bloot te stellen.

Hier zijn een aantal uit-van-de-doos gezondheidscontroles die nuttig zijn om te controleren:

* Systeemcontroles
   * MBean: `org.apache.sling.healthcheck:name=systemchecks,type=HealthCheck`
   * URL: `/system/console/jmx/org.apache.sling.healthcheck:name=systemchecks,type=HealthCheck`
   * Instanties: één auteur, alle publicatieservers
   * Alarmdrempel: wanneer de status niet OK is
   * Alarmdefinitie: de status van een van de meetwaarden is WAARSCHUWING of KRITIEK. Controleer de logboekattributen voor meer informatie over de oorzaak van de kwestie.

* Replicatiereeks

   * MBean: `org.apache.sling.healthcheck:name=replicationQueue,type=HealthCheck`
   * URL: `/system/console/jmx/org.apache.sling.healthcheck:name=replicationQueue,type=HealthCheck`
   * Instanties: één auteur, alle publicatieservers
   * Alarmdrempel: wanneer de status niet OK is
   * Alarmdefinitie: de status van een van de meetwaarden is WAARSCHUWING of KRITIEK. Controleer de logboekattributen voor meer informatie over de rij die de kwestie veroorzaakte.

* Responsprestaties

   * MBean: `org.apache.sling.healthcheck:name=requestsStatus,type=HealthCheck`
   * URL: `/system/console/jmx/org.apache.sling.healthcheck:name=requestsStatus,type=HealthCheck`
   * Instanties: alle servers
   * Duur van waarschuwing: wanneer de status niet OK is
   * Alarmdefinitie: de status van een van de meetwaarden is WAARSCHUWING of KRITIEKE status. Controleer de logboekattributen voor meer informatie over de rij die de kwestie veroorzaakte.

* Query-prestaties

   * MBean: `org.apache.sling.healthcheck:name=queriesStatus,type=HealthCheck`
   * URL: `/system/console/jmx/org.apache.sling.healthcheck:name= queriesStatus,type=HealthCheck`
   * Instanties: één auteur, alle publicatieservers
   * Alarmdrempel: wanneer de status niet OK is
   * Alarmdefinitie: een of meer query&#39;s die langzaam in het systeem worden uitgevoerd. Controleer de logboekattributen voor meer informatie over de vragen die de kwestie veroorzaakten.

* Actieve bundels

   * MBean: `org.apache.sling.healthcheck:name=inactiveBundles,type=HealthCheck`
   * URL: `/system/console/jmx/org.apache.sling.healthcheck:name=inactiveBundles,type=HealthCheck`
   * Instanties: alle servers
   * Alarmdrempel: wanneer de status niet OK is
   * Alarmdefinitie: aanwezigheid van inactieve of onopgeloste OSGi-bundels op het systeem. Controleer het logkenmerk voor meer informatie over de bundels die de uitgave hebben veroorzaakt.

* Logfouten

   * MBean: `org.apache.sling.healthcheck:name=logErrorHealthCheck,type=HealthCheck`
   * URL: `/system/console/jmx/org.apache.sling.healthcheck:name=logErrorHealthCheck,type=HealthCheck`
   * Instanties: alle servers
   * Alarmdrempel: wanneer de status niet OK is
   * Alarmdefinitie: er zijn fouten in de logbestanden. Controleer de logboekattributen voor meer informatie over de oorzaak van de kwestie.

## Gemeenschappelijke kwesties en resoluties  {#common-issues-and-resolutions}

Tijdens het bewakingsproces, als u problemen ontmoet, zijn hier sommige het oplossen van problementaken die u kunt uitvoeren om gemeenschappelijke kwesties met [!DNL Experience Manager] plaatsingen op te lossen:

* Als u TarMK gebruikt, voert u de Tar-compressie vaak uit. Voor meer details, zie [&#x200B; de bewaarplaats &#x200B;](/help/sites-deploying/storage-elements-in-aem-6.md#maintaining-the-repository) handhaven.
* Controleer `OutOfMemoryError` logs. Voor meer informatie, zie [&#x200B; Geheugenproblemen &#x200B;](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-17482.html?lang=nl-NL) analyseren.

* Controleer de logboeken om het even welke verwijzingen naar unindexed vragen, boomstamtraversals, of indextraversals. Deze wijzen op unindexed vragen of op ontoereikend geïndexeerde vragen. Voor beste praktijken bij het optimaliseren van vraag en het indexeren prestaties, zie [&#x200B; Beste praktijken voor vragen en het indexeren &#x200B;](/help/sites-deploying/best-practices-for-queries-and-indexing.md).
* Gebruik de workflowconsole om te controleren of uw workflows naar behoren werken. Indien mogelijk kunt u meerdere workflows samenvoegen tot één workflow.
* Herzie live monitoring en zoek naar extra knelpunten of hoge consumenten van specifieke hulpbronnen.
* Onderzoek de uitgang punten van het cliëntnetwerk en de ingang richt aan het [!DNL Experience Manager] plaatsingsnetwerk, met inbegrip van de verzender. Dit zijn vaak knelpunten. Voor meer informatie, zie [&#x200B; het netwerkoverwegingen van Assets &#x200B;](/help/assets/assets-network-considerations.md).
* Vergroot de grootte van uw [!DNL Experience Manager] -server. Het is mogelijk dat de [!DNL Experience Manager] -implementatie te klein is. De Klantenondersteuning van de Adobe kan u helpen te identificeren of uw server ondermaats is.
* Onderzoek de `access.log` - en `error.log` -bestanden naar items die ongeveer ten tijde van een fout optraden. Zoek naar patronen die op anomalieën van de douanecode kunnen wijzen. Voeg deze toe aan de lijst met gebeurtenissen die u controleert.
