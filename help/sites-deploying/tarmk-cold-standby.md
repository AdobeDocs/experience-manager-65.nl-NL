---
title: Hoe te om AEM met TarMK Koude Reserve in werking te stellen
description: Leer om, een TarMK Cold Standby opstelling tot stand te brengen te vormen en te handhaven.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
docset: aem65
feature: Configuring
exl-id: dadde3ee-d60c-4b87-9af0-a12697148161
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '2666'
ht-degree: 0%

---

# Hoe te om AEM met TarMK Koude Reserve in werking te stellen{#how-to-run-aem-with-tarmk-cold-standby}

## Inleiding {#introduction}

Met de Cold Standby-capaciteit van de Tar Micro Kernel kunnen een of meer stand-by Adobe Experience Manager-instanties (AEM) verbinding maken met een primaire instantie. Het synchronisatieproces is slechts één manier, wat betekent dat het alleen wordt uitgevoerd van de primaire naar de stand-byinstanties.

Het doel van de stand-by-instanties is een live gegevenskopie van de hoofdgegevensopslagruimte te garanderen en een snelle omschakeling zonder gegevensverlies te garanderen als de master om welke reden dan ook niet beschikbaar is.

Inhoud wordt lineair gesynchroniseerd tussen de primaire instantie en de stand-by instanties zonder integriteitscontroles op beschadiging van het bestand of de opslagplaats. Vanwege dit ontwerp zijn stand-by-instanties exacte kopieën van de primaire instantie en kunnen ze inconsistenties op primaire instanties niet verminderen.

>[!NOTE]
>
>De eigenschap van de Reserve van de Koude wordt bedoeld om scenario&#39;s te beveiligen waar de hoge beschikbaarheid op wordt vereist **Auteur** instanties. Voor situaties waarin een hoge beschikbaarheid vereist is **Publiceren** instanties die de Tar Micro Kernel gebruiken, adviseert de Adobe het gebruiken van een publicatielandbouwbedrijf.
>
>Voor informatie over meer beschikbare plaatsingen, zie [Aanbevolen implementaties](/help/sites-deploying/recommended-deploys.md) pagina.

>[!NOTE]
>
>Wanneer de Standby instantie opstelling is, of uit de Primaire knoop wordt afgeleid, verleent het slechts toegang tot de volgende console (voor beleid-verwante activiteiten):
>
>* OSGI-webconsole
>
>Andere consoles zijn niet toegankelijk.

## Hoe werkt het {#how-it-works}

Voor de primaire AEM instantie, wordt een haven van TCP geopend en luistert aan inkomende berichten. Momenteel zijn er twee typen berichten die de slaven naar de master verzenden:

* een bericht om segmentidentiteitskaart van het huidige hoofd te verzoeken
* een bericht om segmentgegevens met een opgegeven id aan te vragen

De reserve vraagt periodiek om segmentidentiteitskaart van de huidige hoofd van primaire. Als het segment lokaal onbekend is, wordt het opgehaald. Als dit al het geval is, worden de segmenten vergeleken en worden de segmenten waarnaar wordt verwezen, indien nodig ook aangevraagd.

>[!NOTE]
>
>Standby-instanties ontvangen geen enkel type verzoeken, omdat deze worden uitgevoerd in de modus Alleen synchroniseren. De enige sectie beschikbaar op een reserve instantie is de Console van het Web, om bundel en de dienstenconfiguratie te vergemakkelijken.

Een gebruikelijke TarMK-standaardinstelling voor koude stand-by:

![chlimage_1](assets/chlimage_1.png)

## Andere kenmerken {#other-characteristics}

### Robuustheid {#robustness}

De gegevensstroom wordt ontworpen om verbinding en netwerk-verwante problemen automatisch te ontdekken en te behandelen. Alle pakketten worden gebundeld met controlesommen en wanneer de problemen met de verbinding of de beschadigde pakketten voorkomen, worden de re-try mechanismen teweeggebracht.

#### Prestaties {#performance}

Het inschakelen van TarMK Cold Standby op de primaire instantie heeft vrijwel geen meetbare invloed op de prestaties. Het extra CPU-verbruik is laag en de extra harde schijf en netwerk-IO zouden geen problemen met de prestaties moeten veroorzaken.

Op stand-by kunt u een hoog CPU-verbruik verwachten tijdens het synchronisatieproces. Omdat de procedure niet multithreaded is, kan het niet worden versneld door veelvoudige kernen te gebruiken. Als er geen gegevens worden gewijzigd of overgedragen, is er geen meetbare activiteit. De verbindingssnelheid is afhankelijk van de hardware- en netwerkomgeving, maar is niet afhankelijk van de grootte van de repository of het SSL-gebruik. Onthoud dit wanneer u de tijd inschat die nodig is voor een eerste synchronisatie of wanneer er ondertussen veel gegevens zijn gewijzigd op het primaire knooppunt.

#### Beveiliging {#security}

Ervan uitgaande dat alle instanties in dezelfde intranetbeveiligingszone worden uitgevoerd, wordt het risico van een inbreuk op de beveiliging sterk verminderd. Desalniettemin kunt u een extra beveiligingslaag toevoegen door SSL-verbindingen tussen de slaven en het stramien in te schakelen. Dit vermindert de mogelijkheid dat de gegevens door een man-in-de-middelste mens in gevaar worden gebracht.

Bovendien kunt u de reserveinstanties specificeren die worden toegestaan om te verbinden door het IP adres van inkomende verzoeken te beperken. Dit zou moeten helpen waarborgen dat niemand in het Intranet de bewaarplaats kan kopiëren.

>[!NOTE]
>
>Het wordt aanbevolen een taakverdelingsmechanisme toe te voegen tussen de Dispatcher en de servers die deel uitmaken van de Cold Standby-instelling. Het taakverdelingsmechanisme moet zo worden geconfigureerd dat alleen het gebruikersverkeer naar de **primair** -instantie. Dit is nodig om consistentie te verzekeren en te verhinderen dat inhoud op de stand-by instantie op andere manieren dan het mechanisme van de Reserve van de Koude wordt gekopieerd.

## Een AEM TarMK-koude stand-byinstelling maken {#creating-an-aem-tarmk-cold-standby-setup}

>[!CAUTION]
>
>PID voor de de knoopopslag van het Segment en de Reserve opslagdienst is veranderd in AEM 6.3 in vergelijking met de vorige versies als volgt:
>
>* van org.apache.jackrabbit.oak.**plug-ins**.segment.standby.store.StandbyStoreService naar org.apache.jackrabbit.oak.segment.standby.store.StandbyStoreService
>* van org.apache.jackrabbit.oak.**plug-ins**.segment.SegmentNodeStoreService to org.apache.jackrabbit.oak.segment.SegmentNodeStoreService
>
>Breng de benodigde aanpassingen aan in de configuratie, zodat deze wijziging doorwerkt.

Als u een TarMK koude stand-byopstelling wilt maken, maakt u eerst de stand-byinstanties door een kopie van het bestandssysteem van de volledige installatiemap van de primaire map naar een nieuwe locatie uit te voeren. Vervolgens kunt u elke instantie starten met een uitvoeringsmodus die de rol ervan opgeeft ( `primary` of `standby`).

Hieronder volgt de procedure die moet worden gevolgd om een opstelling met één hoofd en één reserve instantie tot stand te brengen:

1. AEM installeren.

1. Sluit de instantie af en kopieer de installatiemap naar de locatie waar de instantie in de koude stand-by zich bevindt. Zelfs als u vanaf verschillende computers werkt, moet u voor elke map een beschrijvende naam opgeven (zoals *bovengrens* of *aem-standby*) om onderscheid te maken tussen de verschillende instanties.
1. Ga naar de installatiemap van de primaire instantie en:

   1. Controle en schrapt om het even welke vorige configuraties OSGi u onder zou kunnen hebben `aem-primary/crx-quickstart/install`

   1. Een map maken met de naam `install.primary` krachtens `aem-primary/crx-quickstart/install`

   1. Creeer de vereiste configuraties voor de aangewezen knoopopslag en gegevensopslag onder `aem-primary/crx-quickstart/install/install.primary`
   1. Een bestand maken met de naam `org.apache.jackrabbit.oak.segment.standby.store.StandbyStoreService.config` op dezelfde locatie en configureer deze dienovereenkomstig. Voor meer informatie over de configuratieopties, zie [Configuratie](/help/sites-deploying/tarmk-cold-standby.md#configuration).

   1. Als u een AEM TarMK-instantie gebruikt met een externe gegevensopslag, maakt u een map met de naam `crx3` krachtens `aem-primary/crx-quickstart/install` benoemd `crx3`

   1. Plaats het configuratiebestand van de gegevensopslagruimte in het dialoogvenster `crx3` map.

   Als u bijvoorbeeld een AEM TarMK-instantie met een externe File Data Store uitvoert, hebt u de volgende configuratiebestanden nodig:

   * `aem-primary/crx-quickstart/install/install.primary/org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config`
   * `aem-primary/crx-quickstart/install/install.primary/org.apache.jackrabbit.oak.segment.standby.store.StandbyStoreService.config`
   * `aem-primary/crx-quickstart/install/crx3/org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config`

   Zoek hieronder voorbeeldconfiguraties voor de primaire instantie:

   **Monster van** **org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config**

   ```xml
   org.apache.sling.installer.configuration.persist=B"false"
   customBlobStore=B"true"
   standby=B"false"
   ```

   **Voorbeeld van org.apache.jackrabbit.oak.segment.standby.store.StandbyStoreService.config**

   ```xml
   org.apache.sling.installer.configuration.persist=B"false"
   mode="primary"
   port=I"8023"
   ```

   **Voorbeeld van org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config**

   ```xml
   org.apache.sling.installer.configuration.persist=B"false"
   path="./crx-quickstart/repository/datastore"
   minRecordLength=I"16384"
   ```

1. Begin primair ervoor zorgen u de primaire looppaswijze specificeert:

   ```shell
   java -jar quickstart.jar -r primary,crx3,crx3tar
   ```

1. Maak een Apache Sling Logging Logger voor de **org.apache.jackrabbit.oak.segment** pakket. Stel het logniveau in op &quot;Foutopsporing&quot; en wijs de logboekuitvoer naar een afzonderlijk logbestand, zoals */logs/tarmk-coldstandby.log*. Zie voor meer informatie [Logboekregistratie](/help/sites-deploying/configure-logging.md).
1. Ga naar de locatie van het dialoogvenster **standby** -instantie en start deze door de pot uit te voeren.
1. Creeer de zelfde registrerenconfiguratie zoals voor primaire. Stop vervolgens de instantie.
1. Bereid vervolgens de stand-byinstantie voor. U kunt dit doen door de zelfde stappen uit te voeren zoals voor de primaire instantie:

   1. Bestanden verwijderen die mogelijk onder `aem-standby/crx-quickstart/install`.
   1. Een map maken met de naam `install.standby` krachtens `aem-standby/crx-quickstart/install`

   1. Maak twee configuratiebestanden met de naam:

      * `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config`
      * `org.apache.jackrabbit.oak.segment.standby.store.StandbyStoreService.config`

   1. Een map maken met de naam `crx3` krachtens `aem-standby/crx-quickstart/install`

   1. Maak de configuratie van de gegevensopslagruimte en plaats deze onder `aem-standby/crx-quickstart/install/crx3`. In dit voorbeeld moet u het volgende bestand maken:

      * org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config

   1. Bewerk de bestanden en maak de benodigde configuraties.

   Hieronder vindt u voorbeeldconfiguratiebestanden voor een standaardinstantie:

   **Voorbeeld van org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config**

   ```xml
   org.apache.sling.installer.configuration.persist=B"false"
   name="Oak-Tar"
   service.ranking=I"100"
   standby=B"true"
   customBlobStore=B"true"
   ```

   **Voorbeeld van org.apache.jackrabbit.oak.segment.standby.store.StandbyStoreService.config**

   ```xml
   org.apache.sling.installer.configuration.persist=B"false"
   mode="standby"
   primary.host="127.0.0.1"
   port=I"8023"
   secure=B"false"
   interval=I"5"
   standby.autoclean=B"true"
   ```

   **Voorbeeld van org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config**

   ```xml
   org.apache.sling.installer.configuration.persist=B"false"
   path="./crx-quickstart/repository/datastore"
   minRecordLength=I"16384"
   ```

1. Start de **standby** -instantie in de stand-bymodus:

   ```xml
   java -jar quickstart.jar -r standby,crx3,crx3tar
   ```

De dienst kan ook als Console van het Web, door worden gevormd:

1. Ga naar de webconsole op: *https://serveraddress:serverport/system/console/configMgr*
1. Het zoeken van de dienst riep **Apache Jackrabbit Oak Segment Tar Cold Standby Service** en dubbelklik erop om de instellingen te bewerken.
1. De instellingen opslaan en de instanties opnieuw starten zodat de nieuwe instellingen van kracht kunnen worden.

>[!NOTE]
>
>U kunt de rol van een instantie op elk gewenst moment controleren door de aanwezigheid van de component **primair** of **standby** Voer modi uit in de webconsole voor instellingen voor verkoop.
>
>Dit kan door naar *https://localhost:4502/system/console/status-slingsettings* en de **&quot;Run Modes&quot;** lijn.

## Eerste synchronisatie {#first-time-synchronization}

Nadat de voorbereiding volledig is en de reserve voor het eerst is begonnen, is er zwaar netwerkverkeer tussen de instanties aangezien de reserve tot primaire vangt. U kunt de logbestanden raadplegen om de status van de synchronisatie te bekijken.

In stand-by *tarmk-coldstandby.log* U kunt bijvoorbeeld de volgende vermeldingen zien:

```xml
    *DEBUG* [defaultEventExecutorGroup-2-1] org.apache.jackrabbit.oak.segment.standby.store.StandbyStore trying to read segment ec1f739c-0e3c-41b8-be2e-5417efc05266

    *DEBUG* [nioEventLoopGroup-3-1] org.apache.jackrabbit.oak.segment.standby.codec.SegmentDecoder received type 1 with id ec1f739c-0e3c-41b8-be2e-5417efc05266 and size 262144

    *DEBUG* [defaultEventExecutorGroup-2-1] org.apache.jackrabbit.oak.segment.standby.store.StandbyStore got segment ec1f739c-0e3c-41b8-be2e-5417efc05266 with size 262144

    *DEBUG* [defaultEventExecutorGroup-2-1] org.apache.jackrabbit.oak.segment.file.TarWriter Writing segment ec1f739c-0e3c-41b8-be2e-5417efc05266 to /mnt/crx/author/crx-quickstart/repository/segmentstore/data00016a.tar
```

In de stand-by *error.log* In dat geval ziet u een vermelding als deze:

```xml
*INFO* [FelixStartLevel] org.apache.jackrabbit.oak.segment.standby.store.StandbyStoreService started standby sync with 10.20.30.40:8023 at 5 sec.
```

In het bovenstaande logfragment: *10.20.30.40* is het IP adres van primair.

In de **primair** *tarmk-coldstandby.log* U ziet hier bijvoorbeeld de volgende vermeldingen:

```xml
    *DEBUG* [nioEventLoopGroup-3-2] org.apache.jackrabbit.oak.segment.standby.store.CommunicationObserver got message 's.d45f53e4-0c33-4d4d-b3d0-7c552c8e3bbd' from client c7a7ce9b-1e16-488a-976e-627100ddd8cd

    *DEBUG* [nioEventLoopGroup-3-2] org.apache.jackrabbit.oak.segment.standby.server.StandbyServerHandler request segment id d45f53e4-0c33-4d4d-b3d0-7c552c8e3bbd

    *DEBUG* [nioEventLoopGroup-3-2] org.apache.jackrabbit.oak.segment.standby.server.StandbyServerHandler sending segment d45f53e4-0c33-4d4d-b3d0-7c552c8e3bbd to /10.20.30.40:34998

    *DEBUG* [nioEventLoopGroup-3-2] org.apache.jackrabbit.oak.segment.standby.store.CommunicationObserver did send segment with 262144 bytes to client c7a7ce9b-1e16-488a-976e-627100ddd8cd
```

In dit geval is de in het logbestand vermelde &quot;client&quot; de **standby** -instantie.

Zodra deze ingangen ophouden verschijnen in het logboek, kunt u veilig veronderstellen dat het synchronisatieproces volledig is.

Terwijl de bovenstaande vermeldingen aantonen dat het opiniepeilingsmechanisme naar behoren functioneert, is het vaak handig om te begrijpen of er gegevens zijn die tijdens de opiniepeiling worden gesynchroniseerd. U doet dit door te zoeken naar items zoals:

```xml
*DEBUG* [defaultEventExecutorGroup-156-1] org.apache.jackrabbit.oak.segment.file.TarWriter Writing segment 3a03fafc-d1f9-4a8f-a67a-d0849d5a36d5 to /<<CQROOTDIRECTORY>>/crx-quickstart/repository/segmentstore/data00014a.tar
```

Ook, wanneer het lopen met niet gedeeld `FileDataStore`, bevestigen de berichten zoals hieronder dat de binaire dossiers behoorlijk worden overgebracht:

```xml
*DEBUG* [nioEventLoopGroup-228-1] org.apache.jackrabbit.oak.segment.standby.codec.ReplyDecoder received blob with id eb26faeaca7f6f5b636f0ececc592f1fd97ea1a9#169102 and size 169102
```

### Configuratie {#configuration}

De volgende montages OSGi zijn beschikbaar voor de Koude Reserve dienst:

* **Configuratie behouden:** indien toegelaten, slaat dit de configuratie in de bewaarplaats in plaats van de traditionele OSGi configuratiedossiers op. Adobe raadt u aan deze instelling op productiesystemen uit te schakelen, zodat de primaire configuratie niet door de stand-by wordt gehaald.

* **Modus (`mode`):** Hiermee wordt de uitvoermodus van de instantie gekozen.

* **Poort (poort):** de poort die moet worden gebruikt voor communicatie. De standaardwaarde is `8023`.

* **Primaire host (`primary.host`):** - de gastheer van de primaire instantie. Deze instelling is alleen van toepassing voor de stand-by.
* **Synchronisatieinterval (`interval`):** - deze instelling bepaalt het interval tussen de synchronisatieaanvraag en is alleen van toepassing op de stand-byinstantie.

* **Toegestane IP-waaiers (`primary.allowed-client-ip-ranges`):** - de IP waaiers die primair verbindingen van toestaat.
* **Beveiligen (`secure`):** SSL-codering inschakelen. Als u deze instelling wilt gebruiken, moet deze in alle gevallen zijn ingeschakeld.
* **Time-out stand-by-lezen (`standby.readtimeout`):** Time-out voor aanvragen die zijn uitgegeven door de standby-instantie, in milliseconden. De standaardwaarde is 60000 (één minuut).

* **Automatisch opschonen in stand-bymodus (`standby.autoclean`):** Roep de schoonmaakmethode aan als de grootte van de opslag op een synchronisatiecyclus stijgt.

>[!NOTE]
>
>Adobe raadt aan dat de primaire en stand-by verschillende opslagplaats-id&#39;s hebben, zodat deze afzonderlijk kunnen worden geïdentificeerd voor services zoals offloading.
>
>De beste manier om dit te behandelen is door te schrappen *sling.id* op de stand-by en opnieuw starten van de instantie.

## Failoverprocedures {#failover-procedures}

Als de primaire instantie om welke reden dan ook mislukt, kunt u een van de stand-byinstanties instellen om de rol van de primaire instantie te nemen door de startuitvoeringsmodus te wijzigen zoals hieronder wordt beschreven:

>[!NOTE]
>
>Bewerk de configuratiebestanden zodat deze overeenkomen met de instellingen die voor de primaire instantie worden gebruikt.

1. Ga naar de locatie waar de stand-byinstantie is geïnstalleerd en stop deze.

1. Als u een taakverdelingsmechanisme hebt dat met de installatie is geconfigureerd, kunt u de primaire toepassing op dit punt uit de configuratie van het taakverdelingsmechanisme verwijderen.
1. Maak een back-up van de `crx-quickstart` map in de stand-byinstallatiemap. Het kan als uitgangspunt worden gebruikt bij het opzetten van een nieuwe reserve.

1. Start de instantie opnieuw met de opdracht `primary` uitvoeringsmodus:

   ```shell
   java -jar quickstart.jar -r primary,crx3,crx3tar
   ```

1. Voeg de nieuwe primaire code toe aan het taakverdelingsmechanisme.
1. Maak een nieuwe stand-by-instantie en start deze. Zie de bovenstaande procedure voor meer informatie over: [Een AEM TarMK-koude stand-byinstelling maken](/help/sites-deploying/tarmk-cold-standby.md#creating-an-aem-tarmk-cold-standby-setup).

## Hotfixes toepassen op een Koude ReserveOpstelling {#applying-hotfixes-to-a-cold-standby-setup}

De geadviseerde manier om hotfixes op een koude stand-by opstelling toe te passen is door hen op de primaire instantie te installeren en dan het te klonen in een nieuwe koude stand-by instantie met geïnstalleerde hotfixes.

U kunt dit doen door de hieronder beschreven stappen te volgen:

1. Stop het synchronisatieproces op de koude stand-by instantie door naar de JMX Console te gaan en de status **org.apache.jackrabbit.oak: (&quot;Standby&quot;)**bean te gebruiken. Zie de sectie over [Toezicht](#monitoring).
1. Stop de koude stand-by instantie.
1. Installeer de hotfix op de primaire instantie. Zie voor meer informatie over het installeren van een hotfix [Werken met pakketten](/help/sites-administering/package-manager.md).
1. Test de instantie op problemen na de installatie.
1. Verwijder de koude stand-by instantie door de installatiemap te verwijderen.
1. Stop de primaire instantie en kloon het door een exemplaar van het dossiersysteem van zijn volledige installatiemap aan de plaats van koude reserve uit te voeren.
1. Pas de gemaakte kloon aan zodat deze als een koude stand-byinstantie werkt. Zie [Het creëren van een AEM TarMK Koude ReserveOpstelling.](/help/sites-deploying/tarmk-cold-standby.md#creating-an-aem-tarmk-cold-standby-setup)
1. Begin zowel de primaire als de koude stand-by instanties.

## Bewaking {#monitoring}

De functie maakt informatie beschikbaar met behulp van JMX of MBans. Zo kunt u de huidige status van de stand-by en de master controleren met de opdracht [JMX-console](/help/sites-administering/jmx-console.md). De informatie is te vinden in een MBean van `type org.apache.jackrabbit.oak:type="Standby"`benoemd `Status`.

**Standby**

Wanneer u een stand-byinstantie observeert, wordt één knooppunt weergegeven. ID is gewoonlijk generische UUID.

Dit knooppunt heeft vijf alleen-lezen kenmerken:

* `Running:` Booleaanse waarde die aangeeft of het synchronisatieproces wordt uitgevoerd.

* `Mode:` Client: gevolgd door de UUID die wordt gebruikt om de instantie te identificeren. Deze UUID verandert telkens als de configuratie wordt bijgewerkt.

* `Status:` een tekstuele weergave van het huidige frame (zoals `running` of `stopped`).

* `FailedRequests:`het aantal opeenvolgende fouten.
* `SecondsSinceLastSuccess:` het aantal seconden sinds de laatste geslaagde communicatie met de server. Wordt weergegeven `-1` als er geen geslaagde communicatie tot stand is gebracht.

Er zijn ook drie aanroepbare methoden:

* `start():` start het synchronisatieproces.
* `stop():` stopt het synchronisatieproces.
* `cleanup():` stelt de schoonmaakbeurtverrichting op reserve in werking.

**Primair**

Het observeren van primair stelt wat algemene informatie door als een MBean bloot waarvan de waarde van identiteitskaart het havenaantal is de reserveservice TarMK gebruikt (standaard 8023). De meeste methoden en kenmerken zijn gelijk aan die voor standby, maar sommige verschillen:

* `Mode:` geeft altijd de waarde weer `primary`.

Daarnaast kan informatie worden opgehaald voor maximaal tien clients (stand-by-instanties) die met de master zijn verbonden. De MBean-id is de UUID van de instantie. Er zijn geen aanroepbare methodes voor deze MBans maar sommige nuttige read-only attributen:

* `Name:` de id van de client.
* `LastSeenTimestamp:` het tijdstempel van het laatste verzoek in een tekstuele weergave.
* `LastRequest:` het laatste verzoek van de cliënt.
* `RemoteAddress:` het IP-adres van de client.
* `RemotePort:` de poort die de client voor de laatste aanvraag heeft gebruikt.
* `TransferredSegments:` het totale aantal segmenten dat naar deze client is overgedragen.
* `TransferredSegmentBytes:`het totale aantal bytes dat naar deze client is overgedragen.

## Onderhoud van Cold Standby Repository {#cold-standby-repository-maintenance}

### Revisie opschonen {#revision-clean}

>[!NOTE]
>
>Als u [Onlinerevisie opschonen](/help/sites-deploying/revision-cleanup.md) in de eerste plaats is de hieronder beschreven handmatige procedure niet nodig . Als u de functie Onlinerevisie opschonen gebruikt, kunt u ook de opdracht `cleanup ()` bewerking op de stand-byinstantie wordt automatisch uitgevoerd.

>[!NOTE]
>
>Offline revisie niet opschonen in stand-by. Het is niet nodig en het vermindert niet de grootte van de segmentopslag.

Adobe raadt aan regelmatig onderhoud uit te voeren om een buitensporige groei van de opslagplaats in de loop der tijd te voorkomen. Voer de onderstaande stappen uit om handmatig onderhoud in de koelstand-byopslagruimte uit te voeren:

1. Stop het stand-by proces op de stand-by instantie door naar de JMX Console te gaan en de **org.apache.jackrabbit.oak: Status (&quot;Standby&quot;)** boon. Zie de bovenstaande sectie over meer informatie over hoe u dit kunt doen [Toezicht](/help/sites-deploying/tarmk-cold-standby.md#monitoring).

1. Stop de primaire AEM instantie.
1. Voer het gereedschap Oak-compressie uit op de primaire instantie. Zie voor meer informatie [Behoud van de opslagplaats](/help/sites-deploying/storage-elements-in-aem-6.md#maintaining-the-repository).
1. Start de primaire instantie.
1. Start het stand-byproces op de stand-byinstantie met dezelfde JMX-boon als beschreven in de eerste stap.
1. Bekijk de logboeken en wacht tot de synchronisatie is voltooid. Het is mogelijk dat de stand-bygegevensbank momenteel aanzienlijk groeit.
1. Voer de `cleanup()` bewerking op de stand-byinstantie, waarbij dezelfde JMX-boon wordt gebruikt als in de eerste stap is beschreven.

Het kan langer duren dan normaal voor de stand-by instantie synchronisatie met de primaire server voltooit, aangezien de offlinecompressie de geschiedenis van de opslagplaats effectief herschrijft, waardoor het berekenen van de wijzigingen in de opslagplaatsen meer tijd in beslag neemt. Nadat dit proces is voltooid, is de grootte van de opslagplaats op stand-by ongeveer even groot als de opslagplaats op de primaire opslagplaats.

Als alternatief, kan de primaire bewaarplaats manueel over aan stand-by worden gekopieerd na het in werking stellen van compensatie op de primaire, hoofdzakelijk het herbouwen van reserve telkens als de samenperking loopt.

### Opruimverzameling gegevensopslag {#data-store-garbage-collection}

Het is belangrijk om afvalophaling op de instanties van de dossierdatastore van tijd tot tijd in werking te stellen aangezien anders, schrapte binaire getallen op het filesystem blijven, uiteindelijk vult de aandrijving. Volg de onderstaande procedure om de afvalophaling uit te voeren:

1. Het onderhoud van de koelstand-by opslagplaats uitvoeren zoals beschreven in de sectie [boven](/help/sites-deploying/tarmk-cold-standby.md#cold-standby-repository-maintenance).
1. Nadat het onderhoudsproces is voltooid en de instanties opnieuw zijn gestart:

   * Voer op de primaire locatie de afvalophaling van de gegevensopslagruimte uit via de relevante JMX-boon, zoals beschreven in [dit artikel](/help/sites-administering/data-store-garbage-collection.md#running-data-store-garbage-collection-via-the-jmx-console).
   * Op reserve, is de inzameling van het huisvuil van de gegevensopslag beschikbaar slechts als **BlobGarbageCollection** MBean - `startBlobGC()`. De **RepositoryManagement** MBean is niet beschikbaar op reserve.

   >[!NOTE]
   >
   >Als u geen gedeelde gegevensopslag gebruikt, voer eerst huisvuilinzameling op primair en dan op reserve in werking.
