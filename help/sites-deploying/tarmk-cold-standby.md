---
title: AEM uitvoeren met TarMK Cold Standby
description: Leer om, een TarMK Cold Standby opstelling tot stand te brengen te vormen en te handhaven.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
docset: aem65
feature: Administering
exl-id: dadde3ee-d60c-4b87-9af0-a12697148161
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 5575628c54e2e588dfae4c34383af7d6d55ce859
workflow-type: tm+mt
source-wordcount: '2680'
ht-degree: 0%

---

# AEM uitvoeren met TarMK Cold Standby{#how-to-run-aem-with-tarmk-cold-standby}

## Inleiding {#introduction}

Met de Cold Standby-capaciteit van de Tar Micro Kernel kunnen een of meer stand-by Adobe Experience Manager-instanties (AEM) verbinding maken met een primaire instantie. Het synchronisatieproces is slechts één manier, wat betekent dat het alleen wordt uitgevoerd van de primaire naar de stand-byinstanties.

Het doel van de stand-by-instanties is een live gegevenskopie van de hoofdopslagplaats te garanderen en een snelle omschakeling zonder gegevensverlies te garanderen als de primaire instantie om welke reden dan ook niet beschikbaar is.

Inhoud wordt lineair gesynchroniseerd tussen de primaire instantie en de stand-by instanties zonder integriteitscontroles op beschadiging van het bestand of de opslagplaats. Vanwege dit ontwerp zijn stand-by-instanties exacte kopieën van de primaire instantie en kunnen ze inconsistenties op primaire instanties niet verminderen.

>[!NOTE]
>
>De eigenschap van de Reserve van de Koude wordt bedoeld om scenario&#39;s te beveiligen waar de hoge beschikbaarheid op **** instanties van de Auteur wordt vereist. Voor situaties waar de hoge beschikbaarheid op **wordt vereist publiceer** instanties gebruikend Tar Micro Kernel, adviseert Adobe gebruikend publiceer landbouwbedrijf.
>
>Voor info over meer beschikbare plaatsingen, zie de [ Geadviseerde pagina van Inzet ](/help/sites-deploying/recommended-deploys.md).

>[!NOTE]
>
>Wanneer de Standby instantie opstelling is, of uit de Primaire knoop wordt afgeleid, verleent het slechts toegang tot de volgende console (voor beleid-verwante activiteiten):
>
>* OSGI-webconsole
>
>Andere consoles zijn niet toegankelijk.

## Hoe werkt het {#how-it-works}

Voor de primaire instantie van AEM, wordt een haven van TCP geopend en luistert aan inkomende berichten. Momenteel, zijn er twee types van berichten die reserve naar primair verzenden:

* een bericht om segmentidentiteitskaart van het huidige hoofd te verzoeken
* een bericht om segmentgegevens met een opgegeven id aan te vragen

De reserve vraagt periodiek om segmentidentiteitskaart van de huidige hoofd van primaire. Als het segment lokaal onbekend is, wordt het opgehaald. Als dit al het geval is, worden de segmenten vergeleken en worden de segmenten waarnaar wordt verwezen, indien nodig ook aangevraagd.

>[!NOTE]
>
>Standby-instanties ontvangen geen enkel type verzoeken, omdat deze worden uitgevoerd in de modus Alleen synchroniseren. De enige sectie beschikbaar op een reserve instantie is de Console van het Web, om bundel en de dienstenconfiguratie te vergemakkelijken.

Een gebruikelijke TarMK-standaardinstelling voor koude stand-by:

![ chlimage_1 ](assets/chlimage_1.png)

## Andere kenmerken {#other-characteristics}

### Robuustheid {#robustness}

De gegevensstroom wordt ontworpen om verbinding en netwerk-verwante problemen automatisch te ontdekken en te behandelen. Alle pakketten worden gebundeld met controlesommen en wanneer de problemen met de verbinding of de beschadigde pakketten voorkomen, worden de re-try mechanismen teweeggebracht.

#### Prestaties {#performance}

Het inschakelen van TarMK Cold Standby op de primaire instantie heeft vrijwel geen meetbare invloed op de prestaties. Het extra verbruik van CPU is laag en de extra vaste schijf en netwerk-IO zouden geen problemen en prestatieproblemen moeten veroorzaken.

Op stand-by kunt u een hoog CPU-verbruik verwachten tijdens het synchronisatieproces. Omdat de procedure niet multithreaded is, kan het niet worden versneld door veelvoudige kernen te gebruiken. Als er geen gegevens worden gewijzigd of overgedragen, is er geen meetbare activiteit. De verbindingssnelheid is afhankelijk van de hardware- en netwerkomgeving, maar is niet afhankelijk van de grootte van de repository of het SSL-gebruik. Onthoud dit wanneer u de tijd inschat die nodig is voor een eerste synchronisatie of wanneer er ondertussen veel gegevens zijn gewijzigd op het primaire knooppunt.

#### Beveiliging {#security}

Ervan uitgaande dat alle instanties in dezelfde intranetbeveiligingszone worden uitgevoerd, wordt het risico van een inbreuk op de beveiliging sterk verminderd. Desalniettemin kunt u een extra beveiligingslaag toevoegen door SSL-verbindingen tussen de stand-by en de primaire instanties in te schakelen. Dit vermindert de mogelijkheid dat de gegevens door een man-in-de-middelste mens in gevaar worden gebracht.

Bovendien kunt u de reserveinstanties specificeren die worden toegestaan om te verbinden door het IP adres van inkomende verzoeken te beperken. Dit zou moeten helpen waarborgen dat niemand in het Intranet de bewaarplaats kan kopiëren.

>[!NOTE]
>
>Het wordt aanbevolen een taakverdelingsmechanisme toe te voegen tussen de Dispatcher en de servers die deel uitmaken van de Cold Standby-instelling. Het taakverdelingsmechanisme zou aan direct gebruikersverkeer slechts aan de **primaire** instantie moeten worden gevormd. Dit is nodig om consistentie te verzekeren en te verhinderen dat inhoud op de stand-by instantie op andere manieren dan het mechanisme van de Reserve van de Koude wordt gekopieerd.

## AEM TarMK Cold Standby-instellingen maken {#creating-an-aem-tarmk-cold-standby-setup}

>[!CAUTION]
>
>PID voor de de knoopopslag van het Segment en de Reserve opslagdienst is veranderd in AEM 6.3 in vergelijking met de vorige versies als volgt:
>
>* van org.apache.jackrabbit.oak.**plugins**.segment.standby.store.StandbyStoreService aan org.apache.jackrabbit.oak.segment.standby.store.StandbyStoreService
>* van org.apache.jackrabbit.oak.**stoppen**.segment.SegmentNodeStoreService aan org.apache.jackrabbit.oak.segment.SegmentNodeStoreService
>
>Breng de benodigde aanpassingen aan in de configuratie, zodat deze wijziging doorwerkt.

Als u een TarMK koude stand-byopstelling wilt maken, maakt u eerst de stand-byinstanties door een kopie van het bestandssysteem van de volledige installatiemap van de primaire map naar een nieuwe locatie uit te voeren. Vervolgens kunt u elke instantie starten met een uitvoeringsmodus die de rol ervan opgeeft ( `primary` of `standby` ).

Hieronder volgt de procedure die moet worden gevolgd om een opstelling met één primaire en één reserve instantie tot stand te brengen:

1. AEM installeren.

1. Sluit de instantie af en kopieer de installatiemap naar de locatie waar de instantie in de koude stand-by zich bevindt. Zelfs als u van verschillende machines loopt, zorg ervoor om elke omslag een beschrijvende naam (als *a-primaire* of *a-reserve*) te geven om tussen de instanties te onderscheiden.
1. Ga naar de installatiemap van de primaire instantie en:

   1. Controleer en verwijder eerdere OSGi-configuraties die u onder `aem-primary/crx-quickstart/install` hebt

   1. Een map maken met de naam `install.primary` onder `aem-primary/crx-quickstart/install`

   1. Maak de vereiste configuraties voor de voorkeurenarchivering van knooppunten en de gegevensopslag onder `aem-primary/crx-quickstart/install/install.primary`
   1. Maak een bestand met de naam `org.apache.jackrabbit.oak.segment.standby.store.StandbyStoreService.config` op dezelfde locatie en configureer het bestand op basis van deze locatie. Voor meer informatie over de configuratieopties, zie [ Configuratie ](/help/sites-deploying/tarmk-cold-standby.md#configuration).

   1. Als u een AEM TarMK-instantie gebruikt met een externe gegevensopslag, maakt u een map met de naam `crx3` onder `aem-primary/crx-quickstart/install` named `crx3` .

   1. Plaats het configuratiebestand van de gegevensopslagruimte in de map `crx3` .

   Als u bijvoorbeeld een AEM TarMK-instantie met een externe File Data Store uitvoert, hebt u de volgende configuratiebestanden nodig:

   * `aem-primary/crx-quickstart/install/install.primary/org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config`
   * `aem-primary/crx-quickstart/install/install.primary/org.apache.jackrabbit.oak.segment.standby.store.StandbyStoreService.config`
   * `aem-primary/crx-quickstart/install/crx3/org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config`

   Zoek hieronder voorbeeldconfiguraties voor de primaire instantie:

   **Steekproef van** **org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config**

   ```xml
   org.apache.sling.installer.configuration.persist=B"false"
   customBlobStore=B"true"
   standby=B"false"
   ```

   **Steekproef van org.apache.jackrabbit.oak.segment.standby.store.StandbyStoreService.config**

   ```xml
   org.apache.sling.installer.configuration.persist=B"false"
   mode="primary"
   port=I"8023"
   ```

   **Steekproef van org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config**

   ```xml
   org.apache.sling.installer.configuration.persist=B"false"
   path="./crx-quickstart/repository/datastore"
   minRecordLength=I"16384"
   ```

1. Begin primair ervoor zorgen u de primaire looppaswijze specificeert:

   ```shell
   java -jar quickstart.jar -r primary,crx3,crx3tar
   ```

1. Creeer een Logboekprogramma van het Logboekregistratie van Apache Sling voor het {**pakket 0} org.apache.jackrabbit.oak.segment.** Plaats het logboekniveau aan &quot;zuivert&quot;en richt zijn logboekoutput aan een afzonderlijk logfile, als */logs/tarmk-coldstandby.log*. Voor meer informatie, zie [ het Registreren ](/help/sites-deploying/configure-logging.md).
1. Ga naar de plaats van de **reserve** instantie en begin het door de pot in werking te stellen.
1. Creeer de zelfde registrerenconfiguratie zoals voor primaire. Stop vervolgens de instantie.
1. Bereid vervolgens de stand-byinstantie voor. U kunt dit doen door de zelfde stappen uit te voeren zoals voor de primaire instantie:

   1. Verwijder alle bestanden die u onder `aem-standby/crx-quickstart/install` hebt.
   1. Een map maken met de naam `install.standby` onder `aem-standby/crx-quickstart/install`

   1. Maak twee configuratiebestanden met de naam:

      * `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config`
      * `org.apache.jackrabbit.oak.segment.standby.store.StandbyStoreService.config`

   1. Een map maken met de naam `crx3` onder `aem-standby/crx-quickstart/install`

   1. Maak de configuratie van de gegevensopslagruimte en plaats deze onder `aem-standby/crx-quickstart/install/crx3` . In dit voorbeeld moet u het volgende bestand maken:

      * org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config

   1. Bewerk de bestanden en maak de benodigde configuraties.

   Hieronder vindt u voorbeeldconfiguratiebestanden voor een standaardinstantie:

   **Steekproef van org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config**

   ```xml
   org.apache.sling.installer.configuration.persist=B"false"
   name="Oak-Tar"
   service.ranking=I"100"
   standby=B"true"
   customBlobStore=B"true"
   ```

   **Steekproef van org.apache.jackrabbit.oak.segment.standby.store.StandbyStoreService.config**

   ```xml
   org.apache.sling.installer.configuration.persist=B"false"
   mode="standby"
   primary.host="127.0.0.1"
   port=I"8023"
   secure=B"false"
   interval=I"5"
   standby.autoclean=B"true"
   ```

   **Steekproef van org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config**

   ```xml
   org.apache.sling.installer.configuration.persist=B"false"
   path="./crx-quickstart/repository/datastore"
   minRecordLength=I"16384"
   ```

1. Begin de **reserve** instantie door de reserve looppaswijze te gebruiken:

   ```xml
   java -jar quickstart.jar -r standby,crx3,crx3tar
   ```

De dienst kan ook als Console van het Web, door worden gevormd:

1. Ga naar de Console van het Web bij: *https://serveraddress :serverport/system/console/configMgr*
1. Het zoeken naar de dienst genoemd **Apache de Tar Cold Standby van de Segment van Jackrabbit Oak van de Segment** en het tweemaal klikken om de montages uit te geven.
1. De instellingen opslaan en de instanties opnieuw starten zodat de nieuwe instellingen van kracht kunnen worden.

>[!NOTE]
>
>U kunt de rol van een instantie op elk ogenblik controleren door de aanwezigheid van **primaire** of **reserve** looppaswijzen in de het Verdelen Console van het Web van Montages te controleren.
>
>Dit kan worden gedaan door *https://localhost :4502 te gaan/system/console/status-slingsettings* en de **&quot;Wijzen van de Looppas&quot;** lijn te controleren.

## Eerste synchronisatie {#first-time-synchronization}

Nadat de voorbereiding volledig is en de reserve voor het eerst is begonnen, is er zwaar netwerkverkeer tussen de instanties aangezien de reserve tot primaire vangt. U kunt de logbestanden raadplegen om de status van de synchronisatie te bekijken.

In reserve *mrt-coldstandby.log*, kunt u ingangen zoals deze zien:

```xml
    *DEBUG* [defaultEventExecutorGroup-2-1] org.apache.jackrabbit.oak.segment.standby.store.StandbyStore trying to read segment ec1f739c-0e3c-41b8-be2e-5417efc05266

    *DEBUG* [nioEventLoopGroup-3-1] org.apache.jackrabbit.oak.segment.standby.codec.SegmentDecoder received type 1 with id ec1f739c-0e3c-41b8-be2e-5417efc05266 and size 262144

    *DEBUG* [defaultEventExecutorGroup-2-1] org.apache.jackrabbit.oak.segment.standby.store.StandbyStore got segment ec1f739c-0e3c-41b8-be2e-5417efc05266 with size 262144

    *DEBUG* [defaultEventExecutorGroup-2-1] org.apache.jackrabbit.oak.segment.file.TarWriter Writing segment ec1f739c-0e3c-41b8-be2e-5417efc05266 to /mnt/crx/author/crx-quickstart/repository/segmentstore/data00016a.tar
```

In reserve *error.log*, zou u een ingang zoals dit moeten zien:

```xml
*INFO* [FelixStartLevel] org.apache.jackrabbit.oak.segment.standby.store.StandbyStoreService started standby sync with 10.20.30.40:8023 at 5 sec.
```

In het bovenstaande logboekfragment is *10.20.30.40* het IP-adres van de primaire server.

In **primaire** *tarmk-coldstandby.log*, ziet u ingangen zoals deze:

```xml
    *DEBUG* [nioEventLoopGroup-3-2] org.apache.jackrabbit.oak.segment.standby.store.CommunicationObserver got message 's.d45f53e4-0c33-4d4d-b3d0-7c552c8e3bbd' from client c7a7ce9b-1e16-488a-976e-627100ddd8cd

    *DEBUG* [nioEventLoopGroup-3-2] org.apache.jackrabbit.oak.segment.standby.server.StandbyServerHandler request segment id d45f53e4-0c33-4d4d-b3d0-7c552c8e3bbd

    *DEBUG* [nioEventLoopGroup-3-2] org.apache.jackrabbit.oak.segment.standby.server.StandbyServerHandler sending segment d45f53e4-0c33-4d4d-b3d0-7c552c8e3bbd to /10.20.30.40:34998

    *DEBUG* [nioEventLoopGroup-3-2] org.apache.jackrabbit.oak.segment.standby.store.CommunicationObserver did send segment with 262144 bytes to client c7a7ce9b-1e16-488a-976e-627100ddd8cd
```

In dit geval, is de &quot;cliënt&quot;die in het logboek wordt vermeld de **reserve** instantie.

Zodra deze ingangen ophouden verschijnen in het logboek, kunt u veilig veronderstellen dat het synchronisatieproces volledig is.

Terwijl de bovenstaande vermeldingen aantonen dat het opiniepeilingsmechanisme naar behoren functioneert, is het vaak handig om te begrijpen of er gegevens zijn die tijdens de opiniepeiling worden gesynchroniseerd. U doet dit door te zoeken naar items zoals:

```xml
*DEBUG* [defaultEventExecutorGroup-156-1] org.apache.jackrabbit.oak.segment.file.TarWriter Writing segment 3a03fafc-d1f9-4a8f-a67a-d0849d5a36d5 to /<<CQROOTDIRECTORY>>/crx-quickstart/repository/segmentstore/data00014a.tar
```

Wanneer berichten als deze worden uitgevoerd met een niet-gedeeld `FileDataStore` , wordt ook bevestigd dat de binaire bestanden correct worden verzonden:

```xml
*DEBUG* [nioEventLoopGroup-228-1] org.apache.jackrabbit.oak.segment.standby.codec.ReplyDecoder received blob with id eb26faeaca7f6f5b636f0ececc592f1fd97ea1a9#169102 and size 169102
```

### Configuratie {#configuration}

De volgende montages OSGi zijn beschikbaar voor de Koude Reserve dienst:

* **Blijft Configuratie:** indien toegelaten, slaat dit de configuratie in de bewaarplaats in plaats van de traditionele OSGi configuratiedossiers op. Adobe raadt u aan deze instelling op productiesystemen uit te schakelen, zodat de primaire configuratie niet door de stand-by wordt gehaald.

* **Wijze (`mode`):** dit kiest de looppaswijze van de instantie.

* **Haven (haven):** de haven voor mededeling te gebruiken. De standaardwaarde is `8023` .

* **Primaire gastheer (`primary.host`):** - de gastheer van de primaire instantie. Deze instelling is alleen van toepassing voor de stand-by.
* **interval van de Synchronisatie (`interval`):** - dit het plaatsen bepaalt het interval tussen synchronisatieverzoek en is slechts toepasselijk voor de reserveinstantie.

* **Toegestane IP-Randen (`primary.allowed-client-ip-ranges`):** - de IP waaiers die primair verbindingen van toestaat.
* **Veilig (`secure`):** laat SSL encryptie toe. Als u deze instelling wilt gebruiken, moet deze in alle gevallen zijn ingeschakeld.
* **Reserve Gelezen Onderbreking (`standby.readtimeout`):** Onderbreking voor verzoeken die van de reserve instantie in milliseconden worden uitgegeven. De standaardwaarde is 60000 (één minuut).

* **Reserve Automatische Opruiming (`standby.autoclean`):** Vraag de schoonmaakbeurtmethode als de grootte van de opslag op een synchronisatiecyclus stijgt.

>[!NOTE]
>
>Adobe raadt aan dat de primaire en reserve-id&#39;s van verschillende opslagplaatsen zijn, zodat deze afzonderlijk kunnen worden geïdentificeerd voor services zoals offloading.
>
>De beste manier om ervoor te zorgen dat dit wordt behandeld is door *sling.id* op reserve te schrappen en de instantie opnieuw te beginnen.

## Failoverprocedures {#failover-procedures}

Als de primaire instantie om welke reden dan ook mislukt, kunt u een van de stand-byinstanties instellen om de rol van de primaire instantie te nemen door de startuitvoeringsmodus te wijzigen zoals hieronder wordt beschreven:

>[!NOTE]
>
>Bewerk de configuratiebestanden zodat deze overeenkomen met de instellingen die voor de primaire instantie worden gebruikt.

1. Ga naar de locatie waar de stand-byinstantie is geïnstalleerd en stop deze.

1. Als u een taakverdelingsmechanisme hebt dat met de installatie is geconfigureerd, kunt u de primaire toepassing op dit punt uit de configuratie van het taakverdelingsmechanisme verwijderen.
1. Maak een back-up van de map `crx-quickstart` vanuit de installatiemap in stand-by. Het kan als uitgangspunt worden gebruikt bij het opzetten van een nieuwe reserve.

1. Start de instantie opnieuw in de uitvoermodus van `primary` :

   ```shell
   java -jar quickstart.jar -r primary,crx3,crx3tar
   ```

1. Voeg de nieuwe primaire code toe aan het taakverdelingsmechanisme.
1. Maak een nieuwe stand-by-instantie en start deze. Voor meer info, zie de procedure hierboven op [ Creërend een Cold Standby Opstelling van AEM TarMK ](/help/sites-deploying/tarmk-cold-standby.md#creating-an-aem-tarmk-cold-standby-setup).

## Hotfixes toepassen op een Koude ReserveOpstelling {#applying-hotfixes-to-a-cold-standby-setup}

De geadviseerde manier om hotfixes op een koude stand-by opstelling toe te passen is door hen op de primaire instantie te installeren en dan het te klonen in een nieuwe koude stand-by instantie met geïnstalleerde hotfixes.

U kunt dit doen door de hieronder beschreven stappen te volgen:

1. Stop het synchronisatieproces op de koude stand-by instantie door naar de JMX Console te gaan en de status **org.apache.jackrabbit.oak: (&quot;Standby&quot;)**bean te gebruiken. Voor meer informatie over hoe te om dit te doen, zie de sectie over [ Controle ](#monitoring).
1. Stop de koude stand-by instantie.
1. Installeer de hotfix op de primaire instantie. Voor meer details op hoe te om hotfix te installeren, zie [ hoe te met Pakketten ](/help/sites-administering/package-manager.md) werken.
1. Test de instantie op problemen na de installatie.
1. Verwijder de koude stand-by instantie door de installatiemap te verwijderen.
1. Stop de primaire instantie en kloon het door een exemplaar van het dossiersysteem van zijn volledige installatiemap aan de plaats van koude reserve uit te voeren.
1. Pas de gemaakte kloon aan zodat deze als een koude stand-byinstantie werkt. Zie [ Creërend AEM TarMK Koude ReserveOpstelling.](/help/sites-deploying/tarmk-cold-standby.md#creating-an-aem-tarmk-cold-standby-setup)
1. Begin zowel de primaire als de koude stand-by instanties.

## Bewaking {#monitoring}

De functie maakt informatie beschikbaar met behulp van JMX of MBans. Het doen zodat kunt u de huidige staat van reserve en primair inspecteren gebruikend de [ console JMX ](/help/sites-administering/jmx-console.md). De informatie kan in een MBean van `type org.apache.jackrabbit.oak:type="Standby"` worden gevonden genoemd `Status`.

**Reserve**

Wanneer u een stand-byinstantie observeert, wordt één knooppunt weergegeven. ID is gewoonlijk generische UUID.

Dit knooppunt heeft vijf alleen-lezen kenmerken:

* `Running:` Booleaanse waarde die aangeeft of het synchronisatieproces wordt uitgevoerd.

* `Mode:` Client: gevolgd door de UUID die wordt gebruikt om de instantie te identificeren. Deze UUID verandert telkens als de configuratie wordt bijgewerkt.

* `Status:` Een tekstuele weergave van het huidige frame (zoals `running` of `stopped` ).

* `FailedRequests:` het aantal opeenvolgende fouten.
* `SecondsSinceLastSuccess:` het aantal seconden sinds de laatste succesvolle communicatie met de server. `-1` wordt weergegeven als er geen communicatie tot stand is gebracht.

Er zijn ook drie aanroepbare methoden:

* `start():` start het synchronisatieproces.
* `stop():` stopt het synchronisatieproces.
* `cleanup():` voert de opschoonbewerking uit op de stand-by.

**Primair**

Het observeren van primair stelt wat algemene informatie door als een MBean bloot waarvan de waarde van identiteitskaart het havenaantal is de reserveservice TarMK gebruikt (standaard 8023). De meeste methoden en kenmerken zijn gelijk aan die voor standby, maar sommige verschillen:

* `Mode:` geeft altijd de waarde `primary` weer.

Daarnaast kan informatie worden opgehaald voor maximaal tien klanten (stand-by-instanties) die met de primaire client zijn verbonden. De MBean-id is de UUID van de instantie. Er zijn geen aanroepbare methodes voor deze MBans maar sommige nuttige read-only attributen:

* `Name:` De id van de client.
* `LastSeenTimestamp:` de tijdstempel van de laatste aanvraag in een tekstuele weergave.
* `LastRequest:` de laatste aanvraag van de client.
* `RemoteAddress:` het IP-adres van de client.
* `RemotePort:` de poort die de client voor de laatste aanvraag heeft gebruikt.
* `TransferredSegments:` het totale aantal segmenten dat naar deze client is overgedragen.
* `TransferredSegmentBytes:` het totale aantal bytes die naar deze cliënt worden overgebracht.

## Onderhoud van Cold Standby Repository {#cold-standby-repository-maintenance}

### Revisie opschonen {#revision-clean}

>[!NOTE]
>
>Als u [ Online Opruiming van de Revisie ](/help/sites-deploying/revision-cleanup.md) op de primaire instantie in werking stelt, is de hieronder getoonde handprocedure niet nodig. Als u Onlinerevisie opschonen gebruikt, wordt de bewerking `cleanup ()` in de stand-byinstantie ook automatisch uitgevoerd.

>[!NOTE]
>
>Offline revisie niet opschonen in stand-by. Het is niet nodig en het vermindert niet de grootte van de segmentopslag.

Adobe raadt aan regelmatig onderhoud uit te voeren om te voorkomen dat de opslagplaats in de loop der tijd te sterk groeit. Voer de onderstaande stappen uit om handmatig onderhoud in de koelstand-byopslagruimte uit te voeren:

1. Stop het reserveproces op de reserve instantie door naar de Console te gaan JMX en **org.apache.jackrabbit.oak te gebruiken: Status (&quot;Reserve&quot;)** boon. Voor meer informatie over hoe te om dit te doen, zie de bovengenoemde sectie over [ Controle ](/help/sites-deploying/tarmk-cold-standby.md#monitoring).

1. Stop de primaire AEM-instantie.
1. Voer het Oak-compressieprogramma op de primaire instantie uit. Voor meer details, zie [ het Onderhouden van de Bewaarplaats ](/help/sites-deploying/storage-elements-in-aem-6.md#maintaining-the-repository).
1. Start de primaire instantie.
1. Start het stand-byproces op de stand-byinstantie met dezelfde JMX-boon als beschreven in de eerste stap.
1. Bekijk de logboeken en wacht tot de synchronisatie is voltooid. Het is mogelijk dat de stand-bygegevensbank momenteel aanzienlijk groeit.
1. Voer de bewerking `cleanup()` uit op de stand-byinstantie met dezelfde JMX-boon als in de eerste stap is beschreven.

Het kan langer duren dan normaal voor de stand-by instantie synchronisatie met de primaire server voltooit, aangezien de offlinecompressie de geschiedenis van de opslagplaats effectief herschrijft, waardoor het berekenen van de wijzigingen in de opslagplaatsen meer tijd in beslag neemt. Nadat dit proces is voltooid, is de grootte van de opslagplaats op stand-by ongeveer even groot als de opslagplaats op de primaire opslagplaats.

Als alternatief, kan de primaire bewaarplaats manueel over aan stand-by worden gekopieerd na het in werking stellen van compensatie op de primaire, hoofdzakelijk het herbouwen van reserve telkens als de samenperking loopt.

### Opruimverzameling gegevensopslag {#data-store-garbage-collection}

Het is belangrijk om afvalophaling op de instanties van de dossierdatastore van tijd tot tijd in werking te stellen aangezien anders, schrapte binaire getallen op het filesystem blijven, uiteindelijk vult de aandrijving. Volg de onderstaande procedure om de afvalophaling uit te voeren:

1. Het koude reservebewaarplaatsonderhoud van de looppas zoals die in de sectie [ hierboven ](/help/sites-deploying/tarmk-cold-standby.md#cold-standby-repository-maintenance) wordt beschreven.
1. Nadat het onderhoudsproces is voltooid en de instanties opnieuw zijn gestart:

   * Op primair, stel de inzameling van het huisvuil van de gegevensopslag als relevante boon JMX zoals die in [ wordt beschreven Lopende Inzameling van het huisvuil van de Opslag van Gegevens via de Console JMX ](/help/sites-administering/data-store-garbage-collection.md#running-data-store-garbage-collection-via-the-jmx-console) in werking.
   * Op reserve, is de inzameling van het huisvuil van de gegevensopslag beschikbaar slechts als **BlobGarbageCollection** MBean - `startBlobGC()`. **RepositoryManagement** MBean is niet beschikbaar op reserve.

   >[!NOTE]
   >
   >Als u geen gedeelde gegevensopslag gebruikt, voer eerst huisvuilinzameling op primair en dan op reserve in werking.
