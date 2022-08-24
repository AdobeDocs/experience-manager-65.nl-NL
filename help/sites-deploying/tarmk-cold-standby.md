---
title: Hoe te om AEM met TarMK Koude Reserve in werking te stellen
seo-title: How to Run AEM with TarMK Cold Standby
description: Leer hoe u een TarMK Cold Standby-installatie maakt, configureert en onderhoudt.
seo-description: Learn how to create, configure and maintain a TarMK Cold Standby setup.
uuid: 004fdf3e-517c-452b-8db1-a47d6b31d8ba
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
discoiquuid: 9559e837-a87e-4ee7-8ca6-13b42c74e6bf
docset: aem65
feature: Configuring
exl-id: dadde3ee-d60c-4b87-9af0-a12697148161
source-git-commit: 9d142ce9e25e048512440310beb05d762468f6a2
workflow-type: tm+mt
source-wordcount: '2730'
ht-degree: 0%

---

# Hoe te om AEM met TarMK Koude Reserve in werking te stellen{#how-to-run-aem-with-tarmk-cold-standby}

## Inleiding {#introduction}

Met de koude stand-bycapaciteit van de Tar Micro Kernel kunnen een of meer stand-by AEM instanties verbinding maken met een primaire instantie. Het synchronisatieproces is slechts één manier, wat betekent dat het alleen wordt uitgevoerd van de primaire naar de stand-byinstanties.

Het doel van de stand-by-instanties is een live gegevenskopie van de master gegevensopslagruimte te garanderen en ervoor te zorgen dat er snel wordt omgeschakeld zonder gegevensverlies als de master gegevens om welke reden dan ook niet beschikbaar zijn.

Inhoud wordt lineair gesynchroniseerd tussen de primaire instantie en de stand-by instanties zonder integriteitscontroles op beschadiging van het bestand of de opslagplaats. Vanwege dit ontwerp zijn stand-by-instanties exacte kopieën van de primaire instantie en kunnen ze inconsistenties op primaire instanties niet verminderen.

>[!NOTE]
>
>De eigenschap van de Reserve van de Koude wordt bedoeld om scenario&#39;s te beveiligen waar de hoge beschikbaarheid op wordt vereist **auteur** instanties. Voor situaties waarin hoge beschikbaarheid vereist is **publish** instanties die Tar Micro Kernel gebruiken, adviseert Adobe het gebruiken van een publicatielandbouwbedrijf.
>
>Voor informatie over meer beschikbare plaatsingen, zie [Aanbevolen implementaties](/help/sites-deploying/recommended-deploys.md) pagina.

>[!NOTE]
>
>Wanneer de Standby instantie opstelling is, of uit de Primaire knoop wordt afgeleid, verleent het slechts toegang tot de volgende console (voor beleid verwante activiteiten):
>
>* OSGI-webconsole
>
>Andere consoles zijn niet toegankelijk.

## Hoe werkt het {#how-it-works}

Voor de primaire AEM instantie, wordt een haven van TCP geopend en luistert aan inkomende berichten. Momenteel zijn er twee soorten berichten die de slaven naar de master zullen verzenden:

* een bericht om segmend identiteitskaart van het huidige hoofd te verzoeken
* een bericht om segmentgegevens met een opgegeven id aan te vragen

De reserve vraagt periodiek om segmentidentiteitskaart van de huidige hoofd van primaire. Als het segment plaatselijk onbekend is zal het worden teruggewonnen. Als het reeds aanwezig is worden de segmenten vergeleken en referenced segmenten zullen ook worden gevraagd, indien nodig.

>[!NOTE]
>
>Standby-instanties ontvangen geen enkel type verzoeken, omdat deze worden uitgevoerd in de alleen-synchronisatiemodus. De enige sectie beschikbaar op een reserve instantie is de Console van het Web, om bundel en de dienstenconfiguratie te vergemakkelijken.

Een gebruikelijke TarMK-standaardinstelling voor koude stand-by:

![chlimage_1](assets/chlimage_1.png)

## Andere kenmerken {#other-characteristics}

### Robuustheid {#robustness}

De gegevensstroom wordt ontworpen om verbinding en netwerk verwante problemen automatisch te ontdekken en te behandelen. Alle pakketten worden gebundeld met controlesommen en zodra de problemen met de verbinding of de beschadigde pakketten voorkomen worden de heruitzettingsmechanismen teweeggebracht.

#### Prestaties {#performance}

Het inschakelen van TarMK Cold Standby op de primaire instantie heeft vrijwel geen meetbare invloed op de prestaties. Het extra CPU-verbruik is zeer laag en de extra harde schijf en netwerk-IO zouden geen problemen met de prestaties moeten veroorzaken.

In stand-by kunt u een hoog CPU-verbruik verwachten tijdens het synchronisatieproces. Omdat de procedure niet multithreaded is, kan deze niet worden versneld door meerdere kernen te gebruiken. Als er geen gegevens worden gewijzigd of overgedragen, is er geen meetbare activiteit. De verbindingssnelheid is afhankelijk van de hardware- en netwerkomgeving, maar is niet afhankelijk van de grootte van de gegevensopslagruimte of het SSL-gebruik. Houd dit in gedachten wanneer u de tijd inschat die nodig is voor een eerste synchronisatie of wanneer er ondertussen veel gegevens zijn gewijzigd op het primaire knooppunt.

#### Beveiliging {#security}

Ervan uitgaande dat alle instanties in dezelfde intranetbeveiligingszone worden uitgevoerd, wordt het risico van een inbreuk op de beveiliging sterk verminderd. Desalniettemin kunt u extra beveiligingslaag toevoegen door SSL-verbindingen tussen de slaven en de master in te schakelen. Dit vermindert de mogelijkheid dat de gegevens door een man-in-de-middelste mens in gevaar worden gebracht.

Bovendien kunt u de reserveinstanties specificeren die worden toegestaan om te verbinden door het IP adres van inkomende verzoeken te beperken. Dit zou moeten helpen waarborgen dat niemand in het Intranet de bewaarplaats kan kopiëren.

>[!NOTE]
>
>Het wordt aanbevolen een taakverdelingsmechanisme toe te voegen tussen de Dispatcher en de servers die deel uitmaken van de Coldy Standby-installatie. Het taakverdelingsmechanisme moet zo worden geconfigureerd dat alleen het gebruikersverkeer naar de **primair** om de consistentie te waarborgen en te voorkomen dat inhoud op de stand-byinstantie wordt gekopieerd met andere middelen dan het mechanisme Cold Standby.

## Een AEM TarMK-koude stand-byinstelling maken {#creating-an-aem-tarmk-cold-standby-setup}

>[!CAUTION]
>
>PID voor de de knoopopslag van het Segment en de Reserve opslagdienst is veranderd in AEM 6.3 in vergelijking met de vorige versies als volgt:
>
>* van org.apache.jackrabbit.oak.**plug-ins**.segment.standby.store.StandbyStoreService naar org.apache.jackrabbit.oak.segment.standby.store.StandbyStoreService
>* van org.apache.jackrabbit.oak.**plug-ins**.segment.SegmentNodeStoreService to org.apache.jackrabbit.oak.segment.SegmentNodeStoreService
>
>Zorg ervoor u de noodzakelijke configuratieaanpassingen aanbrengt om deze verandering te weerspiegelen.

Als u een TarMK koude stand-byopstelling wilt maken, moet u eerst de stand-byinstanties maken door een kopie van het bestandssysteem van de volledige installatiemap van de primaire toepassing naar een nieuwe locatie uit te voeren. U kunt dan elke instantie beginnen met een runmode die de rol ervan zal specificeren ( `primary` of `standby`).

Hieronder volgt de procedure die moet worden gevolgd om een opstelling met één master en één reserve instantie tot stand te brengen:

1. AEM installeren.

1. Sluit de instantie af en kopieer de installatiemap naar de locatie waar de instantie in de koude stand-by-stand zich bevindt. Zelfs als u vanuit verschillende computers werkt, moet u voor elke map een beschrijvende naam opgeven (zoals *primaire* of *aem-standby*) om onderscheid te maken tussen de verschillende instanties.
1. Ga naar de installatiemap van de primaire instantie en:

   1. Controleer en verwijder eerdere OSGi-configuraties die u onder `aem-primary/crx-quickstart/install`

   1. Een map maken met de naam `install.primary` krachtens `aem-primary/crx-quickstart/install`

   1. Maak de vereiste configuraties voor de voorkeurswinkel en de gegevensopslag onder `aem-primary/crx-quickstart/install/install.primary`
   1. Een bestand maken met de naam `org.apache.jackrabbit.oak.segment.standby.store.StandbyStoreService.config` op dezelfde locatie en configureer deze dienovereenkomstig. Voor meer informatie over de configuratieopties, zie [Configuratie](/help/sites-deploying/tarmk-cold-standby.md#configuration).

   1. Als u een AEM TarMK-instantie gebruikt met een externe gegevensopslag, maakt u een map met de naam `crx3` krachtens `aem-primary/crx-quickstart/install` benoemd `crx3`

   1. Plaats het configuratiebestand van de gegevensopslagruimte in het dialoogvenster `crx3` map.

   Als u bijvoorbeeld een AEM TarMK-instantie met een externe File Data Store uitvoert, hebt u de volgende configuratiebestanden nodig:

   * `aem-primary/crx-quickstart/install/install.primary/org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config`
   * `aem-primary/crx-quickstart/install/install.primary/org.apache.jackrabbit.oak.segment.standby.store.StandbyStoreService.config`
   * `aem-primary/crx-quickstart/install/crx3/org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config`

   Hieronder vindt u voorbeeldconfiguraties voor de primaire instantie:

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

1. Begin primair ervoor zorgen u de primaire runmode specificeert:

   ```shell
   java -jar quickstart.jar -r primary,crx3,crx3tar
   ```

1. Maak een nieuwe Apache Sling Logging Logger voor de **org.apache.jackrabbit.oak.segment** pakket. Logniveau instellen op &quot;Foutopsporing&quot; en de logboekuitvoer verwijzen naar een afzonderlijk logbestand, zoals */logs/tarmk-coldstandby.log*. Zie voor meer informatie [Logboekregistratie](/help/sites-deploying/configure-logging.md).
1. Ga naar de locatie van de **standby** -instantie en start deze door de pot uit te voeren.
1. Creeer de zelfde registrerenconfiguratie zoals voor primaire. Stop vervolgens de instantie.
1. Bereid vervolgens de stand-byinstantie voor. U kunt dit doen door de zelfde stappen uit te voeren zoals voor de primaire instantie:

   1. Bestanden verwijderen die mogelijk onder `aem-standby/crx-quickstart/install`.
   1. Een nieuwe map maken met de naam `install.standby` krachtens `aem-standby/crx-quickstart/install`

   1. Maak twee configuratiebestanden met de naam:

      * `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config`
      * `org.apache.jackrabbit.oak.segment.standby.store.StandbyStoreService.config`
   1. Een nieuwe map maken met de naam `crx3` krachtens `aem-standby/crx-quickstart/install`

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

1. Start de **standby** -instantie door gebruik te maken van de stand-byrunmode:

   ```xml
   java -jar quickstart.jar -r standby,crx3,crx3tar
   ```

De dienst kan ook via de Console van het Web, door worden gevormd:

1. Ga naar de webconsole op: *https://serveraddress:serverport/system/console/configMgr*
1. Het zoeken van de dienst riep **Apache Jackrabbit Oak Segment Tar Cold Standby Service** en dubbelklik erop om de instellingen te bewerken.
1. De instellingen opslaan en de instanties opnieuw starten zodat de nieuwe instellingen van kracht kunnen worden.

>[!NOTE]
>
>U kunt de rol van een instantie op elk gewenst moment controleren door de aanwezigheid van de component **primair** of **standby** runmodes in de het Verdelen Console van het Web van Montages.
>
>Dit kan worden gedaan door naar *https://localhost:4502/system/console/status-slingsettings* en de **&quot;Run Modes&quot;** lijn.

## Eerste synchronisatie {#first-time-synchronization}

Nadat de voorbereiding is voltooid en de stand-by voor de eerste keer is gestart, zal er een groot netwerkverkeer tussen de instanties plaatsvinden terwijl de stand-by tot aan de primaire vangst vangt. U kunt de logboeken raadplegen om de status van de synchronisatie te observeren.

In stand-by *tarmk-coldstandby.log*, ziet u de volgende vermeldingen:

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

In de **primair** *tarmk-coldstandby.log*, ziet u de volgende vermeldingen:

```xml
    *DEBUG* [nioEventLoopGroup-3-2] org.apache.jackrabbit.oak.segment.standby.store.CommunicationObserver got message ‘s.d45f53e4-0c33-4d4d-b3d0-7c552c8e3bbd’ from client c7a7ce9b-1e16-488a-976e-627100ddd8cd

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

Bovendien, wanneer het lopen met niet gedeeld `FileDataStore`, zullen de berichten als het volgende bevestigen dat de binaire dossiers behoorlijk worden overgebracht:

```xml
*DEBUG* [nioEventLoopGroup-228-1] org.apache.jackrabbit.oak.segment.standby.codec.ReplyDecoder received blob with id eb26faeaca7f6f5b636f0ececc592f1fd97ea1a9#169102 and size 169102
```

### Configuratie {#configuration}

De volgende montages OSGi zijn beschikbaar voor de Koude Reserve dienst:

* **Configuratie behouden:** indien toegelaten, zal dit de configuratie in de bewaarplaats in plaats van de traditionele OSGi configuratiedossiers opslaan. Het wordt aanbevolen deze instelling op productiesystemen uit te schakelen, zodat de primaire configuratie niet door de stand-by wordt gehaald.

* **Modus (`mode`):** Hiermee wordt de runmode van de instantie gekozen.

* **Poort (poort):** de poort die moet worden gebruikt voor communicatie. De standaardwaarde is `8023`.

* **Primaire host (`primary.host`):** - de gastheer van de primaire instantie. Deze instelling is alleen van toepassing voor de stand-by.
* **Synchronisatieinterval (`interval`):** - deze instelling bepaalt het interval tussen de synchronisatieaanvraag en is alleen van toepassing op de stand-byinstantie.

* **Toegestane IP-bereiken (`primary.allowed-client-ip-ranges`):** - de IP waaiers dat primair verbindingen van zal toestaan.
* **Beveiligen (`secure`):** SSL-codering inschakelen. Als u deze instelling wilt gebruiken, moet deze in alle gevallen zijn ingeschakeld.
* **Time-out stand-by-lezen (`standby.readtimeout`):** Time-out voor aanvragen die zijn uitgegeven door de standby-instantie, in milliseconden. De standaardwaarde is 60000 (één minuut).

* **Automatisch opschonen in stand-bymodus (`standby.autoclean`):** Roep de schoonmaakmethode aan als de grootte van de opslag op een synchronisatiecyclus stijgt.

>[!NOTE]
>
>Het wordt ten zeerste aanbevolen dat de primaire en reserve-id&#39;s verschillende opslagplaatsen-id&#39;s hebben om deze afzonderlijk te kunnen identificeren voor services zoals offloading.
>
>De beste manier om ervoor te zorgen dat dit wordt behandeld, is door het verwijderen van *sling.id* bestand op stand-by en de instantie opnieuw starten.

## Failoverprocedures {#failover-procedures}

Als de primaire instantie om welke reden dan ook mislukt, kunt u een van de stand-by-instanties instellen om de rol van de primaire instantie te nemen door de start-runmode als volgt te wijzigen:

>[!NOTE]
>
>De configuratiedossiers moeten ook worden gewijzigd zodat zij de montages aanpassen die voor de primaire instantie worden gebruikt.

1. Ga naar de locatie waar de stand-byinstantie is geïnstalleerd en stop deze.

1. Als u een taakverdelingsmechanisme hebt dat met de installatie is geconfigureerd, kunt u de primaire toepassing op dit punt uit de configuratie van het taakverdelingsmechanisme verwijderen.
1. Back-up maken van `crx-quickstart` map in de stand-byinstallatiemap. Het kan als uitgangspunt worden gebruikt bij het opzetten van een nieuwe reserve.

1. Start de instantie opnieuw met de opdracht `primary` runmode:

   ```shell
   java -jar quickstart.jar -r primary,crx3,crx3tar
   ```

1. Voeg de nieuwe primaire code toe aan het taakverdelingsmechanisme.
1. Maak een nieuwe stand-by-instantie en start deze. Zie de bovenstaande procedure voor meer informatie over [Een AEM TarMK-koude stand-byinstelling maken](/help/sites-deploying/tarmk-cold-standby.md#creating-an-aem-tarmk-cold-standby-setup).

## Hotfixes toepassen op een Koude ReserveOpstelling {#applying-hotfixes-to-a-cold-standby-setup}

De geadviseerde manier om hotfixes op een koude stoutopstelling toe te passen is door hen aan de primaire instantie te installeren en dan het te klonen in een nieuwe koude stand-by instantie met geïnstalleerde hotfixes.

U kunt dit doen door de hieronder beschreven stappen te volgen:

1. Stop het synchronisatieproces op de koude stand-by instantie door naar de JMX Console te gaan en **org.apache.jackrabbit.oak te gebruiken: Status (&quot;Stand-by&quot;)**boon. Zie de sectie over [Toezicht](#monitoring).
1. Stop de koude stand-by instantie.
1. Installeer de hotfix op de primaire instantie. Voor meer informatie over het installeren van een hotfix raadpleegt u [Werken met pakketten](/help/sites-administering/package-manager.md).
1. Test de instantie op problemen na de installatie.
1. Verwijder de koude stand-by instantie door de installatiemap te verwijderen.
1. Stop de primaire instantie en kloon het door een exemplaar van het dossiersysteem van zijn volledige installatiemap aan de plaats van koude reserve uit te voeren.
1. Pas de gemaakte kloon aan om te fungeren als een koude stand-byinstantie. Zie voor meer informatie [Het creëren van een AEM TarMK Koude ReserveOpstelling.](/help/sites-deploying/tarmk-cold-standby.md#creating-an-aem-tarmk-cold-standby-setup)
1. Begin zowel de primaire als de koude stand-by instanties.

## Bewaking {#monitoring}

De functie maakt informatie beschikbaar met behulp van JMX of MBans. Zo kunt u de huidige status van de stand-by en de master status controleren met de opdracht [JMX-console](/help/sites-administering/jmx-console.md). De informatie is te vinden in een MBean van `type org.apache.jackrabbit.oak:type="Standby"`benoemd `Status`.

**Standby**

Als u een stand-byinstantie observeert, wordt één knooppunt zichtbaar. ID is gewoonlijk generische UUID.

Dit knooppunt heeft vijf alleen-lezen kenmerken:

* `Running:` Booleaanse waarde die aangeeft of het synchronisatieproces wordt uitgevoerd.

* `Mode:` Client: gevolgd door de UUID die wordt gebruikt om de instantie te identificeren. Merk op dat deze UUID zal veranderen telkens als de configuratie wordt bijgewerkt.

* `Status:` een tekstuele weergave van het huidige frame (zoals `running` of `stopped`).

* `FailedRequests:`het aantal opeenvolgende fouten.
* `SecondsSinceLastSuccess:` het aantal seconden sinds de laatste geslaagde communicatie met de server. Wordt weergegeven `-1` als er geen goede communicatie heeft plaatsgevonden.

Er zijn ook drie aanroepbare methoden:

* `start():` start het synchronisatieproces.
* `stop():` stopt het synchronisatieproces.
* `cleanup():` stelt de schoonmaakbeurtverrichting op reserve in werking.

**Primair**

Het observeren van primair stelt sommige algemene informatie via een MBean bloot waarvan identiteitskaart de waarde van het havenaantal de reservedienst TarMK (standaard 8023) gebruikt. De meeste methoden en kenmerken zijn gelijk aan die voor standby, maar sommige verschillen:

* `Mode:` geeft altijd de waarde weer `primary`.

Bovendien kan informatie voor maximaal 10 cliënten (standby instanties) die met master worden verbonden worden teruggewonnen. De MBean-id is de UUID van de instantie. Er zijn geen aanroepbare methodes voor deze MBans maar sommige zeer nuttige read-only attributen:

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
>Als u [Onlinerevisie opschonen](/help/sites-deploying/revision-cleanup.md) in de eerste plaats is de hieronder beschreven handmatige procedure niet nodig . Als u bovendien de optie Onlinerevisie opschonen gebruikt, kunt u de opdracht `cleanup ()` bewerking op de stand-byinstantie wordt automatisch uitgevoerd.

>[!NOTE]
>
>Offline revisie niet opschonen in stand-by. Het is niet nodig en het zal niet de segmentarchiefgrootte verminderen.

Adobe raadt aan regelmatig onderhoud uit te voeren om een buitensporige groei van de opslagplaats in de loop der tijd te voorkomen. Voer de onderstaande stappen uit om handmatig onderhoud in de koelstand-byopslagruimte uit te voeren:

1. Stop het stand-by proces op de stand-by instantie door naar de JMX Console te gaan en de **org.apache.jackrabbit.oak: Status (&quot;stand-by&quot;)** boon. Zie de bovenstaande sectie over [Toezicht](/help/sites-deploying/tarmk-cold-standby.md#monitoring).

1. Stop de primaire AEM instantie.
1. Voer het gereedschap voor het comprimeren van eikels uit op de primaire instantie. Zie voor meer informatie [Behoud van de opslagplaats](/help/sites-deploying/storage-elements-in-aem-6.md#maintaining-the-repository).
1. Start de primaire instantie.
1. Start het stand-byproces op de stand-byinstantie met dezelfde JMX-boon als beschreven in de eerste stap.
1. Bekijk de logboeken en wacht tot de synchronisatie is voltooid. Het is mogelijk dat er op dit moment een aanzienlijke groei in de stand-by-gegevensbank zal plaatsvinden.
1. Voer de `cleanup()` bewerking op de stand-byinstantie, waarbij dezelfde JMX-boon wordt gebruikt als in de eerste stap is beschreven.

Het kan langer duren dan normaal voor de stand-by instantie synchronisatie met de primaire server voltooit, aangezien de offlinecompressie de geschiedenis van de opslagplaats effectief herschrijft, waardoor het berekenen van de wijzigingen in de opslagplaatsen meer tijd in beslag neemt. Er moet ook op worden gewezen dat zodra dit proces is voltooid, de grootte van de gegevensopslagruimte op stand-by ruwweg even groot zal zijn als de gegevensopslagruimte op de primaire opslaglocatie.

Als alternatief, kan de primaire bewaarplaats manueel over aan stand-by worden gekopieerd na het in werking stellen van compensatie op de primaire, hoofdzakelijk het herbouwen van reserve telkens als de samenperking loopt.

### Opruimverzameling gegevensopslag {#data-store-garbage-collection}

Het is belangrijk om afvalophaling op de instanties van de dossierdatastore van tijd tot tijd in werking te stellen aangezien anders, schrapte binaire getallen op het filesystem zullen blijven, uiteindelijk vult de aandrijving. Volg de onderstaande procedure om afvalophaling uit te voeren:

1. Het onderhoud van de koelstand-by opslagplaats uitvoeren zoals beschreven in de sectie [boven](/help/sites-deploying/tarmk-cold-standby.md#cold-standby-repository-maintenance).
1. Nadat het onderhoudsproces is voltooid en de instanties opnieuw zijn gestart:

   * Voer op de primaire locatie de afvalophaling van de gegevensopslagruimte uit via de relevante JMX-boon, zoals beschreven in [dit artikel](/help/sites-administering/data-store-garbage-collection.md#running-data-store-garbage-collection-via-the-jmx-console).
   * Op reserve, is de inzameling van het huisvuil van de gegevensopslag beschikbaar slechts via **BlobGarbageCollection** MBean - `startBlobGC()`. **RepositoryManagement **MBean is niet beschikbaar op reserve.

   >[!NOTE]
   >
   >Als u geen gedeelde gegevensopslag gebruikt, zal de huisvuilinzameling eerst op primair en dan op reserve moeten in werking worden gesteld.
