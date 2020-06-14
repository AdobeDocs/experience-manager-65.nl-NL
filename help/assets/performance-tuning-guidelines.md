---
title: Prestaties afstemmen voor [!DNL Adobe Experience Manager Assets].
description: Suggesties en richtlijnen voor de configuratie van [!DNL Experience Manager], wijzigingen in hardware, software en netwerkcomponenten om knelpunten te verwijderen en de prestaties van [!DNL Experience Manager Assets] te optimaliseren.
contentOwner: AG
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: da2e435f33e8527793e009700c30e60868d196be
workflow-type: tm+mt
source-wordcount: '2722'
ht-degree: 0%

---


<!-- TBD: Get reviewed by engineering. -->

# [!DNL Adobe Experience Manager Assets] richtlijn voor afstelling van prestaties {#assets-performance-tuning-guide}

Een [!DNL Experience Manager Assets] opstelling bevat een aantal hardware, software, en netwerkcomponenten. Afhankelijk van uw plaatsingsscenario, kunt u specifieke configuratieveranderingen in hardware, software, en netwerkcomponenten vereisen om prestatiesknelpunten te verwijderen.

Bovendien zorgt het identificeren en volgen van bepaalde richtlijnen voor hardware- en softwareoptimalisatie voor een solide basis die uw [!DNL Experience Manager Assets] implementatie in staat stelt te voldoen aan de verwachtingen op het gebied van prestaties, schaalbaarheid en betrouwbaarheid.

Slechte prestaties in [!DNL Experience Manager Assets] kunnen van invloed zijn op de interactieve prestaties, de verwerking van bedrijfsmiddelen, de downloadsnelheid en andere aspecten.

In feite, is de prestatiesoptimalisering een fundamentele taak die u uitvoert alvorens u doelmetriek voor om het even welk project vestigt.

Hier zijn bepaalde belangrijke aandachtsgebieden waaromheen u prestatieproblemen ontdekt en verhelpt voordat deze van invloed zijn op gebruikers.

## Platform {#platform}

Experience Manager wordt ondersteund op een aantal platforms, maar Adobe heeft de grootste ondersteuning voor native gereedschappen gevonden in Linux en Windows. Dit levert optimale prestaties en een eenvoudige implementatie op. In het ideale geval moet u een 64-bits besturingssysteem implementeren om te voldoen aan de hoge geheugenvereisten van een [!DNL Experience Manager Assets] implementatie. Zoals met om het even welke plaatsing van de Manager van de Ervaring, zou u TarMK moeten uitvoeren waar mogelijk. Hoewel TarMK niet voorbij één enkele auteurinstantie kan schrapen, wordt het gevonden om beter te presteren dan MongoMK. U kunt TarMK-offloadinstanties toevoegen om de verwerkingskracht van de workflow voor uw [!DNL Experience Manager Assets] implementatie te verhogen.

### Tijdelijke map {#temp-folder}

Om de uploadtijden van middelen te verbeteren, gebruik krachtige opslag voor de tijdelijke folder van Java. In Linux en Windows kan een RAM-station of SSD worden gebruikt. In cloudomgevingen kan een vergelijkbaar type snelle opslag worden gebruikt. In Amazon EC2 kan bijvoorbeeld een [tijdelijk station](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/InstanceStorage.html) worden gebruikt voor de tijdelijke map.

Ervan uitgaande dat de server over voldoende geheugen beschikt, configureert u een RAM-station. Voer in Linux de volgende opdrachten uit om een 8 GB RAM-station te maken:

```shell
mkfs -q /dev/ram1 800000
 mkdir -p /mnt/aem-tmp
 mount /dev/ram1 /mnt/aem-tmp
 df -H | grep aem-tmp
```

In Windows OS gebruikt u een stuurprogramma van een andere fabrikant om een RAM-station te maken of gewoon krachtige opslagsystemen zoals SSD te gebruiken.

Als het tijdelijke volume met hoge prestaties gereed is, stelt u de JVM-parameter in `-Djava.io.tmpdir`. U kunt bijvoorbeeld de JVM-parameter hieronder toevoegen aan de `CQ_JVM_OPTS` variabele in het `bin/start` script van [!DNLEExperience Manager]:

`-Djava.io.tmpdir=/mnt/aem-tmp`

## Java-configuratie {#java-configuration}

### Java-versie {#java-version}

Voor optimale prestaties raadt Adobe u aan deze implementatie uit te voeren [!DNL Experience Manager Assets] in Java 8.

>[!NOTE]
>
>Oracle heeft de release van updates voor Java 7 vanaf april 2015 stopgezet.

### JVM-parameters {#jvm-parameters}

Stel de volgende JVM-parameters in:

* `-XX:+UseConcMarkSweepGC`
* `-Doak.queryLimitInMemory`=500000
* `-Doak.queryLimitReads`=100000
* `-Dupdate.limit`=250000
* `-Doak.fastQuerySize`=true

## Gegevensopslag en geheugenconfiguratie {#data-store-and-memory-configuration}

### Configuratie bestandsgegevensopslag {#file-data-store-configuration}

Het wordt aanbevolen de gegevensopslag te scheiden van de segmentopslag voor alle [!DNL Experience Manager Assets] gebruikers. Bovendien kan het vormen van de `maxCachedBinarySize` en `cacheSizeInMB` parameters helpen prestaties maximaliseren. Stel dit in `maxCachedBinarySize` op de kleinste bestandsgrootte die in de cache kan worden opgeslagen. Geef de grootte op van de cache in het geheugen die moet worden gebruikt voor de datastore binnen `cacheSizeInMB`. Adobe raadt u aan deze waarde in te stellen tussen 2 en 10 procent van de totale heapgrootte. Het testen van de belasting/prestaties kan echter helpen de ideale instelling te bepalen.

### De maximale grootte van de cache voor gebufferde afbeeldingen configureren {#configure-the-maximum-size-of-the-buffered-image-cache}

Wanneer u grote hoeveelheden middelen uploadt naar [!DNLAAdobe Experience Manager], om onverwachte pieken in het geheugenverbruik mogelijk te maken en om te voorkomen dat JVM uitvalt met OutOfMemoryErrors, verlaagt u de geconfigureerde maximumgrootte van de cache voor gebufferde images. Bekijk een voorbeeld van een systeem met een maximale heap (- `Xmx`param) van 5 GB, een Oak BlobCache ingesteld op 1 GB en een documentcache ingesteld op 2 GB. In dit geval neemt de gebufferde cache maximaal 1,25 GB en geheugen in beslag, waardoor er slechts 0,75 GB geheugen overblijft voor onverwachte pieken.

Vorm de als buffer opgetreden voor geheim voorgeheugengrootte in de Console van het Web OSGi. Stel de eigenschap in `https://host:port/system/console/configMgr/com.day.cq.dam.core.impl.cache.CQBufferedImageCache``cq.dam.image.cache.max.memory` bytes in. 1073741824 is bijvoorbeeld 1 GB (1024 x 1024 x 1024 = 1 GB).

Van Manager 6.1 SP1 van de Ervaring, als u een `sling:osgiConfig` knoop voor het vormen van dit bezit gebruikt, zorg ervoor om het gegevenstype aan Lang te plaatsen. Zie [CQBufferedImageCache gebruikt heap tijdens het uploaden](https://helpx.adobe.com/experience-manager/kb/cqbufferedimagecache-consumes-heap-during-asset-uploads.html)van bedrijfsmiddelen voor meer informatie.

### Gedeelde gegevensopslag {#shared-data-stores}

Het uitvoeren van S3 of de Gedeelde Datastore van het Dossier kan helpen om schijfruimte te besparen en netwerkproductie in grootschalige implementaties te verhogen. Voor meer informatie over de voor- en nadelen van het gebruik van een gedeelde datastore, zie de gids voor het [rangschikken van activa](/help/assets/assets-sizing-guide.md).

### S3-gegevensopslag {#s-data-store}

Met de volgende S3 Data Store-configuratie ( `org.apache.jackrabbit.oak.plugins.blob.datastore.S3DataStore.cfg`) kon Adobe 12,8 TB binaire grote objecten (BLOB&#39;s) uitpakken uit een bestaande bestandsgegevensopslag naar een S3-gegevensopslag op een klantsite:

```conf
accessKey=<snip>
 secretKey=<snip>
 s3Bucket=<snip>
 s3Region=us-standard
 s3EndPoint=<a href="https://s3.amazonaws.com/">s3.amazonaws.com</a>
 connectionTimeout=120000
 socketTimeout=120000
 maxConnections=80
 writeThreads=60
 concurrentUploadsThreads=30
 asyncUploadLimit=30
 maxErrorRetry=1000
 path=/opt/author/crx-quickstart/repository/datastore
 s3RenameKeys=false
 s3Encryption=SSE_S3
 proactiveCaching=true
 uploadRetries=1000
 migrateFailuresCount=400
```

## Netwerkoptimalisatie {#network-optimization}

Adobe raadt u aan HTTPS in te schakelen omdat veel bedrijven firewalls hebben die HTTP-verkeer sluizen, wat het uploaden van bestanden negatief beïnvloedt en bestanden beschadigt. Bij grote bestanden uploaden dient u ervoor te zorgen dat gebruikers een bekabelde verbinding met het netwerk hebben omdat een WiFi-netwerk snel verzadigd raakt. Voor richtlijnen betreffende het identificeren van netwerkknelpunten, zie de het rangschikken van [Activa gids](/help/assets/assets-sizing-guide.md). Om netwerkprestaties te beoordelen door netwerktopologie te analyseren, zie de overwegingen [van het](/help/assets/assets-network-considerations.md)middelennetwerk.

Primair, hangt uw strategie van de netwerkoptimalisering van de hoeveelheid beschikbare bandbreedte en de lading op uw instantie van de Manager [!DNLEvan de] ervaring af. De gemeenschappelijke configuratieopties, met inbegrip van firewalls of volmachten kunnen helpen netwerkprestaties verbeteren. Hier volgen enkele belangrijke punten:

* Afhankelijk van uw instantietype (klein, gematigd, groot), zorg ervoor dat u voldoende netwerkbandbreedte voor uw instantie van de Manager van de Ervaring hebt. De adequate bandbreedtetoewijzing is vooral belangrijk als de Manager [!DNLEvan de] ervaring op AWS wordt ontvangen.
* Als uw [!DNLEinstantie van de Manager] van de Ervaring op AWS wordt ontvangen, kunt u profiteren door een veelzijdig het schrapen beleid te hebben. De instantie vergroten als gebruikers een hoge belasting verwachten. Downsize het voor matige/lage lading.
* HTTPS: De meeste gebruikers hebben firewalls die het verkeer van HTTP snuffelen, wat het uploaden van dossiers of zelfs corrupte dossiers tijdens het uploaden negatief kan beïnvloeden.
* Grote bestanden uploaden: Zorg ervoor dat gebruikers een bekabelde verbinding met het netwerk hebben (WiFi-verbindingen verzadigen snel).

## Workflows {#workflows}

### Tijdelijke workflows {#transient-workflows}

Stel waar mogelijk de [!UICONTROL DAM Update Asset] workflow in op Overgang. De instelling verlaagt aanzienlijk de overheadkosten die nodig zijn voor het verwerken van workflows, omdat workflows in dit geval niet door de normale tracking- en archiveringsprocessen hoeven te gaan.

1. Navigeer naar `/miscadmin` in de [!DNLEinstantie van de Manager] van de Ervaring bij `https://[aem_server]:[port]/miscadmin`.

1. Vouw uit **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]** > **[!UICONTROL dam]**.

1. Open **[!UICONTROL DAM Update Asset]**. Ga in het zwevende deelvenster met gereedschappen naar de **[!UICONTROL Page]** tab en klik op **[!UICONTROL Page Properties]**.

1. Select **[!UICONTROL Transient Workflow]** and click **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Bepaalde functies ondersteunen geen tijdelijke workflows. Als deze functies vereist zijn voor uw [!DNL Assets] implementatie, configureert u geen tijdelijke workflows.

Als er geen tijdelijke workflows kunnen worden gebruikt, voert u de workflow regelmatig uit om gearchiveerde [!UICONTROL DAM Update Asset] workflows te verwijderen om ervoor te zorgen dat de systeemprestaties niet afnemen.

Doorgaans voert u de werkstromen wekelijks uit. Nochtans, in middel-intensieve scenario&#39;s, zoals tijdens brede activaopname, kunt u het vaker uitvoeren.

Om werkschemazuivering te vormen, voeg een nieuwe configuratie van de Woorden van het Werkschema van Adobe Granite door de console OSGi toe. Vervolgens configureert en plant u de workflow als onderdeel van het wekelijkse onderhoudsvenster.

Als het leegmaken te lang duurt, is het wel even. Daarom dient u ervoor te zorgen dat uw reinigingstaken zijn voltooid om situaties te voorkomen waarin het leegmaken van werkstromen mislukt vanwege het grote aantal werkstromen.

Bijvoorbeeld, na het uitvoeren van talrijke niet-voorbijgaande werkschema&#39;s (die tot de knopen van de werkschemainstantie leidt), kunt u het Werkschema van [ACS AEM Commons Remover](https://adobe-consulting-services.github.io/acs-aem-commons/features/workflow-remover.html) op een ad hoc basis uitvoeren. Het verwijdert overbodige, voltooide workflowexemplaren direct in plaats van te wachten tot de Adobe Granite Workflow Purge-planner wordt uitgevoerd.

### Maximumaantal parallelle banen {#maximum-parallel-jobs}

In [!DNLEExperience Manager] wordt standaard een maximumaantal parallelle taken uitgevoerd dat gelijk is aan het aantal processors op de server. Het probleem met deze instelling is dat tijdens perioden van zware belasting alle processors in beslag worden genomen door [!UICONTROL DAM Update Asset] workflows, waardoor de reactiesnelheid van de gebruikersinterface wordt vertraagd en wordt voorkomen dat [!DNLEervaringsbeheer] andere processen uitvoert die de prestaties en stabiliteit van de server garanderen. U kunt deze waarde als een goede praktijk instellen op de helft van de processors die beschikbaar zijn op de server door de volgende stappen uit te voeren:

1. Op de Auteur van de Manager van de [!DNLEervaring] , toegang `https://[aem_server]:[port]/system/console/slingevent`.

1. Klik **[!UICONTROL Edit]** op elke werkschemarij die voor uw implementatie relevant is, bijvoorbeeld **[!UICONTROL Granite Transient Workflow Queue]**.

1. Werk de waarde van bij **[!UICONTROL Maximum Parallel Jobs]** en klik **[!UICONTROL Save]**.

Het instellen van een wachtrij op de helft van de beschikbare processors is een werkbare oplossing om mee te beginnen. Het kan echter zijn dat u dit aantal moet verhogen of verlagen om een maximale doorvoer te bereiken en dat aantal aan te passen aan de omgeving. Er zijn afzonderlijke rijen voor tijdelijke en niet-tijdelijke werkstromen evenals andere processen, zoals externe werkschema&#39;s. Als meerdere wachtrijen die zijn ingesteld op 50% van de processors tegelijkertijd actief zijn, kan het systeem snel overbelast raken. De rijen die zwaar worden gebruikt variëren zeer over gebruikersimplementaties. Daarom moet u ze mogelijk nauwkeurig configureren voor maximale efficiëntie zonder dat dit ten koste gaat van de stabiliteit van de server.

### DAM Update Asset Configuration {#dam-update-asset-configuration}

Het [!UICONTROL DAM Update Asset] werkschema bevat een volledige reeks stappen die voor taken, zoals de generatie van Scene7 PTIFF en [!DNL Adobe InDesign Server] integratie worden gevormd. Het is echter mogelijk dat de meeste gebruikers niet meerdere van deze stappen nodig hebben. Adobe raadt u aan een aangepaste kopie van het [!UICONTROL DAM Update Asset] workflowmodel te maken en overbodige stappen te verwijderen. Werk in dit geval de draagraketten bij zodat deze [!UICONTROL DAM Update Asset] naar het nieuwe model verwijzen.

Als u de [!UICONTROL DAM Update Asset] workflow intensief uitvoert, kan de bestandsdatatastore aanzienlijk groter worden. De resultaten van een door Adobe uitgevoerd experiment hebben aangetoond dat de grootte van de datastore met ongeveer 400 GB kan toenemen als binnen 8 uur ongeveer 5500 workflows worden uitgevoerd.

Het is een tijdelijke verhoging, en datastore wordt hersteld aan zijn originele grootte nadat u de taak van de datastore huisvuilinzameling in werking stelt.

Typisch, loopt de de inzamelingstaak van de datastore wekelijks samen met andere geplande onderhoudstaken.

Als u een beperkte schijfruimte hebt en [!UICONTROL DAM Update Asset] werkschema&#39;s intensief in werking stelt, overweeg het plannen van de huisvuilinzamelingstaak vaker.

#### Genereren van uitvoering bij uitvoering {#runtime-rendition-generation}

Klanten gebruiken afbeeldingen van verschillende grootten en indelingen op hun website of voor distributie aan zakelijke partners. Omdat elke uitvoering de afdruk van het middel in de opslagplaats vergroot, raadt Adobe u aan deze functie zorgvuldig te gebruiken. Om de hoeveelheid bronnen te verminderen die nodig is om afbeeldingen te verwerken en op te slaan, kunt u deze afbeeldingen tijdens runtime genereren in plaats van als uitvoeringen tijdens het opnemen.

Vele klanten van Plaatsen voeren een beeldservlet uit die resizes en teelten beelden op het ogenblik zij worden gevraagd, wat extra lading aan de publicatieinstantie oplegt. Maar zolang deze afbeeldingen in het cachegeheugen kunnen worden opgeslagen, kan de uitdaging worden beperkt.

Een alternatieve benadering is Scene7-technologie te gebruiken om beeldmanipulatie volledig uit te schakelen. Daarnaast kunt u Brand Portal implementeren dat niet alleen taken voor het genereren van vertoningen overneemt van de infrastructuur van [!DNLEExperience Manager] , maar ook de volledige publicatielaag.

#### ImageMagick {#imagemagick}

Als u de [!UICONTROL DAM Update Asset] workflow aanpast om uitvoeringen te genereren met ImageMagick, raadt Adobe u aan het `policy.xml` bestand op `/etc/ImageMagick/`. Standaard gebruikt ImageMagick de volledige beschikbare schijfruimte op het volume van het besturingssysteem en het beschikbare geheugen. Breng de volgende configuratieveranderingen binnen de `policymap` sectie van `policy.xml` aan om deze middelen te beperken.

```xml
<policymap>
  <!-- <policy domain="system" name="precision" value="6"/> -->
  <policy domain="resource" name="temporary-path" value="/ephemeral0/imagemagick_tmp"/>
  <policy domain="resource" name="memory" value="1000MiB"/>
  <policy domain="resource" name="map" value="1000MiB"/>
  <!-- <policy domain="resource" name="area" value="1gb"/> -->
  <policy domain="resource" name="disk" value="10000MiB"/>
  <!-- <policy domain="resource" name="file" value="768"/> -->
  <policy domain="resource" name="thread" value="1"/>
  <policy domain="resource" name="throttle" value="50"/>
  <!-- <policy domain="resource" name="time" value="3600"/> -->
</policymap>
```

Stel bovendien het pad van de tijdelijke map van ImageMagick in het `configure.xml` `MAGIC_TEMPORARY_PATH`bestand (of door de omgevingsvariabele in te stellen) in op een schijfpartitie met voldoende ruimte en IOPS.

>[!CAUTION]
>
>Een fout-configuratie kan uw server onstabiel maken als ImageMagick alle beschikbare schijfruimte gebruikt. De beleidswijzigingen die vereist zijn om grote bestanden met ImageMagick te verwerken, kunnen van invloed zijn op de prestaties van [!DNLEhet] ervaringsbeheer. Voor meer informatie, zie [installeren en ImageMagick](/help/assets/best-practices-for-imagemagick.md)vormen.

>[!NOTE]
>
>De `policy.xml` dossiers ImageMagick en `configure.xml` zijn beschikbaar bij `/usr/lib64/ImageMagick-&#42;/config/` in plaats van `/etc/ImageMagick/`.Zie [documentatie](https://www.imagemagick.org/script/resources.php) ImageMagick voor plaats van de configuratiedossiers.

Als u [!DNL Experience Manager] op Adobe Managed Services (AMS) gebruikt, neemt u contact op met de klantenservice van Adobe als u van plan bent een groot aantal grote PSD- of PSB-bestanden te verwerken. Werk samen met de vertegenwoordiger van de klantendienst van Adobe om deze beste praktijken voor uw plaatsing van AMS uit te voeren en de best mogelijke hulpmiddelen en de modellen voor merkgebonden formaten van Adobe te kiezen. [!DNL Experience Manager] PSB-bestanden met een zeer hoge resolutie die groter zijn dan 30000 x 23000 pixels, worden mogelijk niet verwerkt.

### XMP-schrijfback {#xmp-writeback}

Met XMP-schrijfback wordt het oorspronkelijke element bijgewerkt wanneer metagegevens worden gewijzigd in [!DNL Experience Manager]. Dit resulteert in het volgende:

* Het element zelf wordt gewijzigd
* Er wordt een versie van het element gemaakt
* [!UICONTROL DAM Update Asset] wordt uitgevoerd met het element

De vermelde resultaten verbruiken aanzienlijke middelen. Daarom raadt Adobe aan om de functie voor het terugdraaien [van XMP uit te](https://helpx.adobe.com/experience-manager/kb/disable-xmp-writeback.html)schakelen als dit niet verplicht is.

Het invoeren van een grote hoeveelheid meta-gegevens kan in middel-intensieve kringactiviteit resulteren XMP als de loopwerkstroomvlag wordt gecontroleerd. Plan zo&#39;n import tijdens het gebruik van een slanke server, zodat de prestaties voor andere gebruikers niet worden beïnvloed.

## Replicatie {#replication}

Als u elementen wilt repliceren naar een groot aantal publicatie-instanties, bijvoorbeeld in een Sites-implementatie, raadt Adobe u aan kettingreplicatie te gebruiken. In dit geval dupliceert de auteurinstantie naar één enkel publicatiegeval dat beurtelings aan andere publiceert instanties herhaalt, die de auteursinstantie vrijmaken.

### Kettingreplicatie configureren {#configure-chain-replication}

1. Bepaal op welke publicatie-instantie u de replicaties wilt koppelen
1. Op die publicatieinstantie voeg replicatieagenten toe die aan andere publicatieinstanties richten
1. Schakel op elk van die replicatieagents &quot;Bij ontvangst&quot; in op het tabblad &quot;Triggers&quot;

>[!NOTE]
>
>Adobe raadt automatische activering van elementen niet aan. Indien nodig raadt Adobe u echter aan dit als de laatste stap in een workflow te doen, meestal DAM Update Asset.

## Zoekindexen {#search-indexes}

Zorg ervoor u de recentste de dienstpakken en op prestaties betrekking hebbende hotfixes uitvoert aangezien zij vaak updates aan systeemindexen omvatten. Zie Tips voor het afstemmen van [prestaties](https://helpx.adobe.com/experience-manager/kb/performance-tuning-tips.html) voor sommige indexoptimalisaties.

Maak aangepaste indexen voor query&#39;s die u vaak uitvoert. Voor details, zie [methodologie voor het analyseren van langzame vragen](https://aemfaq.blogspot.com/2014/08/oak-query-log-file-analyzer-tool.html) en het [creëren van douaneindexen](/help/sites-deploying/queries-and-indexing.md). Voor extra inzichten rond vraag en index beste praktijken, zie [Beste praktijken voor Vragen en het Indexeren](/help/sites-deploying/best-practices-for-queries-and-indexing.md).

### Lucene-indexconfiguraties {#lucene-index-configurations}

Sommige optimalisaties kunnen worden uitgevoerd op de indexconfiguraties van de eiken die de [!DNL Experience Manager Assets] prestaties kunnen verbeteren. Werk de indexconfiguraties bij om de re-indexerende tijd te verbeteren:

1. Open CRXDe `/crx/de/index.jsp` en login als administratieve gebruiker.
1. Blader naar `/oak:index/lucene`.
1. Voeg een `String[]` eigenschap toe `excludedPaths` met waarden `/var`, `/etc/workflow/instances`en `/etc/replication`.
1. Blader naar `/oak:index/damAssetLucene`. Voeg een `String[]` eigenschap `includedPaths` met waarde toe `/content/dam`. Wijzigingen opslaan.

Als uw gebruikers geen full-text onderzoek van activa hoeven te doen, bijvoorbeeld, doorzoekend door tekst in Pdf- documenten, dan onbruikbaar maken. U verbetert indexprestaties door full-text indexering onbruikbaar te maken. Voer de volgende stappen uit om het uitnemen van [!DNL Apache Lucene] tekst uit te schakelen:

1. In [!DNL Experience Manager] interface, toegang [!UICONTROL Package Manager].
1. Upload en installeer het pakket beschikbaar op [disable_indexingbinarytextraction-10.zip](assets/disable_indexingbinarytextextraction-10.zip).

### Totaal raden {#guess-total}

Wanneer het creëren van vragen die grote resultaatreeksen produceren, gebruik de `guessTotal` parameter om zwaar geheugengebruik te vermijden wanneer u hen in werking stelt.

## Known issues {#known-issues}

### Grote bestanden {#large-files}

Er zijn twee belangrijke bekende problemen met betrekking tot grote bestanden in [!DNL Experience Manager]. Wanneer de dossiers grootten groter dan 2 GB bereiken, kan de koude reserve synchronisatie in een uit-van-geheugensituatie lopen. In sommige gevallen wordt de stand-bysynchronisatie niet uitgevoerd. In andere gevallen loopt de primaire instantie vast. Dit scenario is van toepassing op elk bestand in [!DNL Experience Manager] een grootte van meer dan 2 GB, inclusief inhoudspakketten.

Op dezelfde manier kan het enige tijd duren voordat het bestand, wanneer bestanden een grootte van 2 GB bereiken bij gebruik van een gedeelde S3-gegevensopslag, volledig doorloopt van de cache naar het bestandssysteem. Dientengevolge, wanneer het gebruiken van binair-minder replicatie, is het mogelijk dat de binaire gegevens niet kunnen zijn voortgeduurd alvorens de replicatie voltooit. Deze situatie kan tot problemen leiden, vooral als de beschikbaarheid van gegevens belangrijk is.

## Prestaties testen {#performance-testing}

Stel voor elke [!DNL Experience Manager] implementatie een systeem voor het testen van de prestaties in waarmee knelpunten snel kunnen worden opgespoord en opgelost. Hier volgen enkele belangrijke aandachtsgebieden.

### Netwerktests {#network-testing}

Voor alle kwesties van netwerkprestaties van de klant, voer de volgende taken uit:

* De netwerkprestaties van de test van binnen het klantennetwerk
* Test de netwerkprestaties vanuit het Adobe-netwerk. Voor klanten van AMS, werk met uw CSE om van binnen het netwerk van Adobe te testen.
* De netwerkprestaties van de test van een ander toegangspunt
* Door een hulpmiddel van de netwerkbenchmark te gebruiken
* Testen tegen de verzender

### [!DNL Experience Manager] instantie testen {#aem-instance-testing}

Om latentie te minimaliseren en hoge productie door efficiënt gebruik van cpu en lading-verdeling te bereiken, controleer de prestaties van uw [!DNL Experience Manager] instantie regelmatig. Met name:

* Laadtests uitvoeren op de [!DNL Experience Manager] instantie.
* Uploadprestaties controleren en reageren op de gebruikersinterface.

## [!DNL Experience Manager Assets] prestatiecontrolelijst en impact van taken voor middelenbeheer {#checklist}

* Schakel HTTPS in om rondom eventuele bedrijfs-HTTP-verkeersfragmenten te komen.
* Gebruik een bekabelde verbinding voor het uploaden van zware middelen.
* Implementeer in Java 8.
* Stel optimale JVM-parameters in.
* Configureer een FileSystem DataStore of een S3-gegevensopslag.
* Genereren van subelementen uitschakelen. Als deze optie is ingeschakeld, maakt de workflow van AEM een afzonderlijk element voor elke pagina in een element van meerdere pagina&#39;s. Elk van deze pagina&#39;s is een individueel middel dat extra schijfruimte verbruikt, versioning, en extra werkschemaverwerking vereist. Als u geen afzonderlijke pagina&#39;s nodig hebt, schakelt u het genereren van subelementen en het uitnemen van pagina&#39;s uit.
* Schakel tijdelijke workflows in.
* Stem de wachtrijen voor de Granite-workflow af om gelijktijdige taken te beperken.
* Vorm [!DNL ImageMagick] om middelverbruik te beperken.
* Verwijder overbodige stappen uit de [!UICONTROL DAM Update Asset] workflow.
* Vorm werkschema en versie het zuiveren.
* Optimaliseer indexen met de recentste de dienstpakken en hotfixes. Raadpleeg de klantenservice van Adobe voor eventuele extra indexoptimalisaties die beschikbaar zijn.
* Gebruik radenTotal om queryprestaties te optimaliseren.
* If you configure [!DNL Experience Manager] to detect file types from the content of the files (by enabling **[!UICONTROL Day CQ DAM Mime Type Service]** in the **[!UICONTROL AEM Web Console]**), upload many files in bulk during non-peak hours as it is resource-intensive.
