---
title: Hoe te om AEM met TarMK Koude Reserve in werking te stellen
seo-title: Hoe te om AEM met TarMK Koude Reserve in werking te stellen
description: Leer hoe u een TarMK Cold Standby-installatie maakt, configureert en onderhoudt.
seo-description: Leer hoe u een TarMK Cold Standby-installatie maakt, configureert en onderhoudt.
uuid: 004fdf3e-517c-452b-8db1-a47d6b31d8ba
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
discoiquuid: 9559e837-a87e-4ee7-8ca6-13b42c74e6bf
docset: aem65
translation-type: tm+mt
source-git-commit: a99c5794cee88d11ca3fb9eeed443c4d0178c7b3
workflow-type: tm+mt
source-wordcount: '2731'
ht-degree: 0%

---


# Hoe te om AEM met TarMK Koude Reserve in werking te stellen{#how-to-run-aem-with-tarmk-cold-standby}

## Inleiding {#introduction}

Met de koude stand-bycapaciteit van de Tar Micro Kernel kunnen een of meer stand-by AEM instanties verbinding maken met een primaire instantie. Het synchronisatieproces is slechts één manier, wat betekent dat het alleen wordt uitgevoerd van de primaire naar de stand-byinstanties.

Het doel van de stand-by-instanties is een live gegevenskopie van de master gegevensopslagruimte te garanderen en ervoor te zorgen dat er snel wordt omgeschakeld zonder gegevensverlies als de master gegevens om welke reden dan ook niet beschikbaar zijn.

Inhoud wordt lineair gesynchroniseerd tussen de primaire instantie en de stand-by instanties zonder integriteitscontroles op beschadiging van het bestand of de opslagplaats. Vanwege dit ontwerp zijn stand-by-instanties exacte kopieën van de primaire instantie en kunnen ze inconsistenties op primaire instanties niet verminderen.

>[!NOTE]
>
>De eigenschap van de Reserve van de Koude wordt bedoeld om scenario&#39;s te beveiligen waar de hoge beschikbaarheid op **auteursinstanties** wordt vereist. Voor situaties waar de hoge beschikbaarheid op **publiceer** instanties gebruikend Tar Micro Kernel wordt vereist, adviseert Adobe het gebruiken van een publicatielandbouwbedrijf.
>
>Voor informatie over meer beschikbare plaatsingen, zie de [Aanbevolen pagina van Plaatsingen](/help/sites-deploying/recommended-deploys.md) .

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
>Het wordt aanbevolen een taakverdelingsmechanisme toe te voegen tussen de Dispatcher en de servers die deel uitmaken van de Coldy Standby-installatie. Het taakverdelingsmechanisme moet zodanig worden geconfigureerd dat alleen het gebruikersverkeer naar de **primaire** instantie wordt geleid om de consistentie te waarborgen en te voorkomen dat inhoud op de stand-byinstantie wordt gekopieerd met andere middelen dan het Cold Standby-mechanisme.

## Een AEM TarMK-koude stand-byinstelling maken {#creating-an-aem-tarmk-cold-standby-setup}

>[!CAUTION]
>
>PID voor de de knoopopslag van het Segment en de Reserve opslagdienst is veranderd in AEM 6.3 in vergelijking met de vorige versies als volgt:
>
>* van org.apache.jackrabbit.oak.**plugins**.segment.standby.store.StandbyStoreService to org.apache.jackrabbit.oak.segment.standby.store.StandbyStoreService
>* van org.apache.jackrabbit.oak.**plugins**.segment.SegmentNodeStoreService to org.apache.jackrabbit.oak.segment.SegmentNodeStoreService

>
>
Zorg ervoor u de noodzakelijke configuratieaanpassingen aanbrengt om deze verandering te weerspiegelen.

Als u een TarMK koude stand-byopstelling wilt maken, moet u eerst de stand-byinstanties maken door een kopie van het bestandssysteem van de volledige installatiemap van de primaire toepassing naar een nieuwe locatie uit te voeren. Vervolgens kunt u elke instantie starten met een runmode die de rol ervan ( `primary` of `standby`) opgeeft.

Hieronder volgt de procedure die moet worden gevolgd om een opstelling met één master en één reserve instantie tot stand te brengen:

1. AEM installeren.

1. Sluit de instantie af en kopieer de installatiemap naar de locatie waar de instantie in de koude stand-by-stand zich bevindt. Zelfs als u vanuit verschillende computers werkt, moet u voor elke map een beschrijvende naam opgeven (zoals *em-primary* of *aem-standby*) om onderscheid te maken tussen de verschillende instanties.
1. Ga naar de installatiemap van de primaire instantie en:

   1. Controleer en verwijder eerdere OSGi-configuraties die u onder `aem-primary/crx-quickstart/install`

   1. Een map maken die `install.primary` onder `aem-primary/crx-quickstart/install`

   1. Maak de vereiste configuraties voor de voorkeurswinkel en de gegevensopslag onder `aem-primary/crx-quickstart/install/install.primary`
   1. Maak een bestand dat `org.apache.jackrabbit.oak.segment.standby.store.StandbyStoreService.config` op dezelfde locatie wordt aangeroepen en configureer het bestand op basis hiervan. Voor meer informatie over de configuratieopties, zie [Configuratie](/help/sites-deploying/tarmk-cold-standby.md#configuration).

   1. Als u een AEM TarMK-instantie gebruikt met een externe gegevensopslag, maakt u een map met de naam `crx3` onder de `aem-primary/crx-quickstart/install` naam `crx3`

   1. Plaats het configuratiebestand van de gegevensopslagruimte in de `crx3` map.

   Als u bijvoorbeeld een AEM TarMK-instantie met een externe File Data Store uitvoert, hebt u de volgende configuratiebestanden nodig:

   * `aem-primary/crx-quickstart/install/install.primary/org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config`
   * `aem-primary/crx-quickstart/install/install.primary/org.apache.jackrabbit.oak.segment.standby.store.StandbyStoreService.config`
   * `aem-primary/crx-quickstart/install/crx3/org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config`

   Hieronder vindt u voorbeeldconfiguraties voor de primaire instantie:

   **Voorbeeld van** **org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config**

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

1. Maak een nieuwe Apache Sling Logging Logger voor het pakket **org.apache.jackrabbit.oak.segment** . Stel het logniveau in op &quot;Foutopsporing&quot; en wijs de loguitvoer naar een afzonderlijk logbestand, bijvoorbeeld */logs/tarmk-coldstandby.log*. For more information, see [Logging](/help/sites-deploying/configure-logging.md).
1. Ga naar de locatie van de **stand-byinstantie** en start deze door de jar uit te voeren.
1. Creeer de zelfde registrerenconfiguratie zoals voor primaire. Stop vervolgens de instantie.
1. Bereid vervolgens de stand-byinstantie voor. U kunt dit doen door de zelfde stappen uit te voeren zoals voor de primaire instantie:

   1. Verwijder bestanden die u mogelijk onder `aem-standby/crx-quickstart/install`deze lijst hebt.
   1. Een nieuwe map maken die `install.standby` onder `aem-standby/crx-quickstart/install`

   1. Maak twee configuratiebestanden met de naam:

      * `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config`
      * `org.apache.jackrabbit.oak.segment.standby.store.StandbyStoreService.config`
   1. Een nieuwe map maken die `crx3` onder `aem-standby/crx-quickstart/install`

   1. Creeer de configuratie van de gegevensopslag en plaats het onder `aem-standby/crx-quickstart/install/crx3`. In dit voorbeeld moet u het volgende bestand maken:

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

1. Start de **stand-by** -instantie met behulp van de stand-by-runmode:

   ```xml
   java -jar quickstart.jar -r standby,crx3,crx3tar
   ```

De dienst kan ook via de Console van het Web, door worden gevormd:

1. Ga naar de webconsole op: *https://serveraddress:serverport/system/console/configMgr*
1. Op zoek naar de service **Apache Jackrabbit Oak Segment Tar Cold Standby Service** en dubbelklik erop om de instellingen te bewerken.
1. De instellingen opslaan en de instanties opnieuw starten zodat de nieuwe instellingen van kracht kunnen worden.

>[!NOTE]
>
>U kunt de rol van een instantie op elk ogenblik controleren door de aanwezigheid van de **primaire** of **reserve** runmodes in de Console van het Web van de Montages van het Verdelen te controleren.
>
>Dit kan door naar *https://localhost:4502/system/console/status-slingsettings* te gaan en de lijn van de Wijzen van de **&quot;Looppas&quot;** te controleren.

## Eerste synchronisatie {#first-time-synchronization}

Nadat de voorbereiding is voltooid en de stand-by voor de eerste keer is gestart, zal er een groot netwerkverkeer tussen de instanties plaatsvinden terwijl de stand-by tot aan de primaire vangst vangt. U kunt de logboeken raadplegen om de status van de synchronisatie te observeren.

In reserve *tarmk-coldstandby.log*, zult u ingangen zoals deze zien:

```xml
    *DEBUG* [defaultEventExecutorGroup-2-1] org.apache.jackrabbit.oak.segment.standby.store.StandbyStore trying to read segment ec1f739c-0e3c-41b8-be2e-5417efc05266

    *DEBUG* [nioEventLoopGroup-3-1] org.apache.jackrabbit.oak.segment.standby.codec.SegmentDecoder received type 1 with id ec1f739c-0e3c-41b8-be2e-5417efc05266 and size 262144

    *DEBUG* [defaultEventExecutorGroup-2-1] org.apache.jackrabbit.oak.segment.standby.store.StandbyStore got segment ec1f739c-0e3c-41b8-be2e-5417efc05266 with size 262144

    *DEBUG* [defaultEventExecutorGroup-2-1] org.apache.jackrabbit.oak.segment.file.TarWriter Writing segment ec1f739c-0e3c-41b8-be2e-5417efc05266 to /mnt/crx/author/crx-quickstart/repository/segmentstore/data00016a.tar
```

In *error.log* van reserve, zou u een ingang als dit moeten zien:

```xml
*INFO* [FelixStartLevel] org.apache.jackrabbit.oak.segment.standby.store.StandbyStoreService started standby sync with 10.20.30.40:8023 at 5 sec.
```

In het bovengenoemde logboekfragment, is *10.20.30.40* het IP adres van primaire.

In het **primaire** *tarmk-coldstandby.log*, zult u ingangen zoals deze zien:

```xml
    *DEBUG* [nioEventLoopGroup-3-2] org.apache.jackrabbit.oak.segment.standby.store.CommunicationObserver got message ‘s.d45f53e4-0c33-4d4d-b3d0-7c552c8e3bbd’ from client c7a7ce9b-1e16-488a-976e-627100ddd8cd

    *DEBUG* [nioEventLoopGroup-3-2] org.apache.jackrabbit.oak.segment.standby.server.StandbyServerHandler request segment id d45f53e4-0c33-4d4d-b3d0-7c552c8e3bbd

    *DEBUG* [nioEventLoopGroup-3-2] org.apache.jackrabbit.oak.segment.standby.server.StandbyServerHandler sending segment d45f53e4-0c33-4d4d-b3d0-7c552c8e3bbd to /10.20.30.40:34998

    *DEBUG* [nioEventLoopGroup-3-2] org.apache.jackrabbit.oak.segment.standby.store.CommunicationObserver did send segment with 262144 bytes to client c7a7ce9b-1e16-488a-976e-627100ddd8cd
```

In dit geval is de in het logbestand vermelde &quot;client&quot; de **stand-byinstantie** .

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

* **Poort (poort):** de poort die moet worden gebruikt voor communicatie. The default is `8023`.

* **Primaire host (`primary.host`):** - de gastheer van de primaire instantie. Deze instelling is alleen van toepassing voor de stand-by.
* **Synchronisatieinterval (`interval`):** - deze instelling bepaalt het interval tussen de synchronisatieaanvraag en is alleen van toepassing op de stand-byinstantie.

* **Toegestane IP-Bereiken (`primary.allowed-client-ip-ranges`):** - de IP waaiers dat primair verbindingen van zal toestaan.
* **Veilig (`secure`):** SSL-codering inschakelen. Als u deze instelling wilt gebruiken, moet deze in alle gevallen zijn ingeschakeld.
* **Time-out stand-by-lezen (`standby.readtimeout`):** Time-out voor aanvragen die zijn uitgegeven door de standby-instantie, in milliseconden. De aanbevolen time-out is 43200000. U wordt doorgaans aangeraden de time-out in te stellen op een waarde van ten minste 12 uur.

* **Automatisch opschonen in stand-bymodus (`standby.autoclean`):** Roep de schoonmaakmethode aan als de grootte van de opslag op een synchronisatiecyclus stijgt.

>[!NOTE]
>
>Het wordt ten zeerste aanbevolen dat de primaire en reserve-id&#39;s verschillende opslagplaatsen-id&#39;s hebben om deze afzonderlijk te kunnen identificeren voor services zoals offloading.
>
>De beste manier om ervoor te zorgen dat dit wordt behandeld, is door het bestand *sling.id* in de stand-by te verwijderen en de instantie opnieuw te starten.

## Failoverprocedures {#failover-procedures}

Als de primaire instantie om welke reden dan ook mislukt, kunt u een van de stand-by-instanties instellen om de rol van de primaire instantie te nemen door de start-runmode als volgt te wijzigen:

>[!NOTE]
>
>De configuratiedossiers moeten ook worden gewijzigd zodat zij de montages aanpassen die voor de primaire instantie worden gebruikt.

1. Ga naar de locatie waar de stand-byinstantie is geïnstalleerd en stop deze.

1. Als u een taakverdelingsmechanisme hebt dat met de installatie is geconfigureerd, kunt u de primaire toepassing op dit punt uit de configuratie van het taakverdelingsmechanisme verwijderen.
1. Maak een back-up van de `crx-quickstart` map in de stand-byinstallatiemap. Het kan als uitgangspunt worden gebruikt bij het opzetten van een nieuwe reserve.

1. Start de instantie opnieuw met de `primary` runmode:

   ```shell
   java -jar quickstart.jar -r primary,crx3,crx3tar
   ```

1. Voeg de nieuwe primaire code toe aan het taakverdelingsmechanisme.
1. Maak een nieuwe stand-by-instantie en start deze. Voor meer informatie, zie de procedure hierboven bij het [Creëren van een AEM TarMK Koude ReserveOpstelling](/help/sites-deploying/tarmk-cold-standby.md#creating-an-aem-tarmk-cold-standby-setup).

## Hotfixes toepassen op een Koude ReserveOpstelling {#applying-hotfixes-to-a-cold-standby-setup}

De geadviseerde manier om hotfixes op een koude stoutopstelling toe te passen is door hen aan de primaire instantie te installeren en dan het te klonen in een nieuwe koude stand-by instantie met geïnstalleerde hotfixes.

U kunt dit doen door de hieronder beschreven stappen te volgen:

1. Stop het synchronisatieproces op de koude stand-by instantie door naar de JMX Console te gaan en **org.apache.jackrabbit.oak te gebruiken: Status (&quot;Stand-by&quot;)**boon. Zie de sectie [Bewaking](#monitoring)voor meer informatie over hoe u dit kunt doen.
1. Stop de koude stand-by instantie.
1. Installeer de hotfix op de primaire instantie. Voor meer details over hoe te om hotfix te installeren, zie [hoe te met Pakketten](/help/sites-administering/package-manager.md)werken.
1. Test de instantie op problemen na de installatie.
1. Verwijder de koude stand-by instantie door de installatiemap te verwijderen.
1. Stop de primaire instantie en kloon het door een exemplaar van het dossiersysteem van zijn volledige installatiemap aan de plaats van koude reserve uit te voeren.
1. Pas de gemaakte kloon aan om te fungeren als een koude stand-byinstantie. Voor extra details, zie het [Creëren van een AEM TarMK Koude ReserveOpstelling.](/help/sites-deploying/tarmk-cold-standby.md#creating-an-aem-tarmk-cold-standby-setup)
1. Begin zowel de primaire als de koude stand-by instanties.

## Bewaking {#monitoring}

De functie maakt informatie beschikbaar met behulp van JMX of MBans. Zo kunt u de huidige status van de stand-by en de master server controleren met behulp van de [JMX-console](/help/sites-administering/jmx-console.md). De informatie is te vinden in een MBean van `type org.apache.jackrabbit.oak:type="Standby"`genoemde `Status`.

**Standby**

Als u een stand-byinstantie observeert, wordt één knooppunt zichtbaar. ID is gewoonlijk generische UUID.

Dit knooppunt heeft vijf alleen-lezen kenmerken:

* `Running:` Booleaanse waarde die aangeeft of het synchronisatieproces wordt uitgevoerd.

* `Mode:` Client: gevolgd door de UUID die wordt gebruikt om de instantie te identificeren. Merk op dat deze UUID zal veranderen telkens als de configuratie wordt bijgewerkt.

* `Status:` een tekstuele weergave van het huidige frame (zoals `running` of `stopped`).

* `FailedRequests:`het aantal opeenvolgende fouten.
* `SecondsSinceLastSuccess:` het aantal seconden sinds de laatste geslaagde communicatie met de server. Het zal tonen `-1` als geen succesvolle mededeling is gemaakt.

Er zijn ook drie aanroepbare methoden:

* `start():` start het synchronisatieproces.
* `stop():` stopt het synchronisatieproces.
* `cleanup():` stelt de schoonmaakbeurtverrichting op reserve in werking.

**Primair**

Het observeren van primair stelt sommige algemene informatie via een MBean bloot waarvan identiteitskaart de waarde van het havenaantal de reservedienst TarMK (standaard 8023) gebruikt. De meeste methoden en kenmerken zijn gelijk aan die voor standby, maar sommige verschillen:

* `Mode:` zal altijd de waarde tonen `primary`.

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
>Als u [Online revisie opschoning](/help/sites-deploying/revision-cleanup.md) uitvoert op de primaire instantie, is de hieronder weergegeven handmatige procedure niet nodig. Als u bovendien Online revisie-opruiming gebruikt, wordt de `cleanup ()` bewerking op de stand-byinstantie automatisch uitgevoerd.

>[!NOTE]
>
>Offline revisie niet opschonen in stand-by. Het is niet nodig en het zal niet de segmentarchiefgrootte verminderen.

Adobe raadt aan regelmatig onderhoud uit te voeren om een buitensporige groei van de opslagplaats in de loop der tijd te voorkomen. Voer de onderstaande stappen uit om handmatig onderhoud in de koelstand-byopslagruimte uit te voeren:

1. Stop het reserveproces op de reserve instantie door naar de Console te gaan JMX en **org.apache.jackrabbit.oak te gebruiken: Statusboon (&quot;stand-by&quot;)** . Zie de bovenstaande sectie over [bewaking](/help/sites-deploying/tarmk-cold-standby.md#monitoring)voor meer informatie over hoe u dit kunt doen.

1. Stop de primaire AEM instantie.
1. Voer het gereedschap voor het comprimeren van eikels uit op de primaire instantie. Zie [Bewaarplaats](/help/sites-deploying/storage-elements-in-aem-6.md#maintaining-the-repository)onderhouden voor meer informatie.
1. Start de primaire instantie.
1. Start het stand-byproces op de stand-byinstantie met dezelfde JMX-boon als beschreven in de eerste stap.
1. Bekijk de logboeken en wacht tot de synchronisatie is voltooid. Het is mogelijk dat er op dit moment een aanzienlijke groei in de stand-by-gegevensbank zal plaatsvinden.
1. Voer de `cleanup()` bewerking op de stand-byinstantie uit met dezelfde JMX-boon als in de eerste stap is beschreven.

Het kan langer duren dan normaal voor de stand-by instantie synchronisatie met de primaire server voltooit, aangezien de offlinecompressie de geschiedenis van de opslagplaats effectief herschrijft, waardoor het berekenen van de wijzigingen in de opslagplaatsen meer tijd in beslag neemt. Er moet ook op worden gewezen dat zodra dit proces is voltooid, de grootte van de gegevensopslagruimte op stand-by ruwweg even groot zal zijn als de gegevensopslagruimte op de primaire opslaglocatie.

Als alternatief, kan de primaire bewaarplaats manueel over aan stand-by worden gekopieerd na het in werking stellen van compensatie op de primaire, hoofdzakelijk het herbouwen van reserve telkens als de samenperking loopt.

### Opruimverzameling gegevensopslag {#data-store-garbage-collection}

Het is belangrijk om afvalophaling op de instanties van de dossierdatastore van tijd tot tijd in werking te stellen aangezien anders, schrapte binaire getallen op het filesystem zullen blijven, uiteindelijk vult de aandrijving. Volg de onderstaande procedure om afvalophaling uit te voeren:

1. Voer het onderhoud van de koelstand-by opslagplaats uit zoals beschreven in de [bovenstaande](/help/sites-deploying/tarmk-cold-standby.md#cold-standby-repository-maintenance)sectie.
1. Nadat het onderhoudsproces is voltooid en de instanties opnieuw zijn gestart:

   * Voer op de primaire locatie de afvalophaling van de gegevensopslagruimte uit via de relevante JMX-boon, zoals beschreven in [dit artikel](/help/sites-administering/data-store-garbage-collection.md#running-data-store-garbage-collection-via-the-jmx-console).
   * Op reserve, is de inzameling van het huisvuil van de gegevensopslag beschikbaar slechts via **BlobGarbageCollection** MBean - `startBlobGC()`. **RepositoryManagement **MBean is niet beschikbaar op reserve.

   >[!NOTE]
   >
   >Als u geen gedeelde gegevensopslag gebruikt, zal de huisvuilinzameling eerst op primair en dan op reserve moeten in werking worden gesteld.

