---
title: Prestaties afstemmen  [!DNL Assets]
description: Suggesties en begeleiding over  [!DNL Experience Manager]  configuratie, veranderingen in hardware, software, en netwerkcomponenten om knelpunten te verwijderen en de prestaties van  [!DNL Experience Manager Assets] te optimaliseren.
contentOwner: AG
mini-toc-levels: 1
role: Architect, Admin
feature: Asset Management
exl-id: 1d9388de-f601-42bf-885b-6a7c3236b97e
solution: Experience Manager, Experience Manager Assets
source-git-commit: 0b90fdd13efc5408ef94ee1966f04a80810b515e
workflow-type: tm+mt
source-wordcount: '2663'
ht-degree: 0%

---

<!-- TBD: Get reviewed by engineering. -->

# [!DNL Adobe Experience Manager Assets] richtlijn voor het afstemmen van prestaties {#assets-performance-tuning-guide}

Een [!DNL Experience Manager Assets] -instelling bevat verschillende hardware-, software- en netwerkcomponenten. Afhankelijk van uw plaatsingsscenario, kunt u specifieke configuratieveranderingen in hardware, software, en netwerkcomponenten vereisen om prestatiesknelpunten te verwijderen.

Bovendien kunt u door bepaalde richtlijnen voor de optimalisatie van hardware en software te identificeren en te volgen, een solide basis leggen waarmee uw [!DNL Experience Manager Assets] -implementatie kan voldoen aan de verwachtingen op het gebied van prestaties, schaalbaarheid en betrouwbaarheid.

Slechte prestaties in [!DNL Experience Manager Assets] kunnen van invloed zijn op de interactieve prestaties, de verwerking van bedrijfsmiddelen, de downloadsnelheid en andere aspecten.

In feite, is de prestatiesoptimalisering een fundamentele taak die u uitvoert alvorens u doelmetriek voor om het even welk project vestigt.

Hier zijn bepaalde belangrijke aandachtsgebieden waaromheen u prestatieproblemen ontdekt en verhelpt voordat deze van invloed zijn op gebruikers.

## Platform {#platform}

Hoewel Experience Manager op verschillende platforms wordt ondersteund, heeft Adobe op Linux® en Windows de grootste ondersteuning voor native gereedschappen gevonden. Dit levert optimale prestaties en vereenvoudigt de implementatie. In het ideale geval moet u een 64-bits besturingssysteem implementeren om te voldoen aan de hoge geheugenvereisten van een [!DNL Experience Manager Assets] -implementatie. Net als bij elke Experience Manager-implementatie moet u TarMK waar mogelijk implementeren. Hoewel TarMK niet voorbij één enkele auteurinstantie kan schrapen, wordt het gevonden om beter te presteren dan MongoMK. U kunt TarMK-offloadinstanties toevoegen om de verwerkingskracht van de workflow voor uw [!DNL Experience Manager Assets] -implementatie te verhogen.

### Tijdelijke map {#temp-folder}

Om de uploadtijden van middelen te verbeteren, gebruik krachtige opslag voor de tijdelijke folder van Java. In Linux® en Windows kan een RAM-station of SSD worden gebruikt. In cloudomgevingen kan een vergelijkbaar type snelle opslag worden gebruikt. Bijvoorbeeld, in Amazon EC2, kan een [ letterlijke aandrijving ](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/InstanceStorage.html) voor de tijdelijke omslag worden gebruikt.

Ervan uitgaande dat de server over voldoende geheugen beschikt, configureert u een RAM-station. Voer in Linux® de volgende opdrachten uit om een 8 GB RAM-station te maken:

```shell
mkfs -q /dev/ram1 800000
 mkdir -p /mnt/aem-tmp
 mount /dev/ram1 /mnt/aem-tmp
 df -H | grep aem-tmp
```

In Windows OS gebruikt u een stuurprogramma van een andere fabrikant om een RAM-station te maken of gewoon krachtige opslagsystemen zoals SSD te gebruiken.

Als het tijdelijke volume met hoge prestaties gereed is, stelt u de JVM-parameter `-Djava.io.tmpdir` in. U kunt bijvoorbeeld de parameter JVM hieronder toevoegen aan de variabele `CQ_JVM_OPTS` in het `bin/start` script van [!DNL Experience Manager] :

`-Djava.io.tmpdir=/mnt/aem-tmp`

## Java-configuratie {#java-configuration}

### Java-versie {#java-version}

Adobe raadt u aan [!DNL Experience Manager Assets] in Java 8 te implementeren voor optimale prestaties.

<!-- TBD: Link to the latest official word around Java.
-->

### JVM-parameters {#jvm-parameters}

Stel de volgende JVM-parameters in:

* `-XX:+UseConcMarkSweepGC`
* `-Doak.queryLimitInMemory`=500000
* `-Doak.queryLimitReads`=100000
* `-Dupdate.limit`=250000
* `-Doak.fastQuerySize`=true

## Gegevensopslag en geheugenconfiguratie {#data-store-and-memory-configuration}

### Configuratie bestandsgegevensopslag {#file-data-store-configuration}

Het wordt aanbevolen de gegevensopslag te scheiden van de segmentopslag voor alle [!DNL Experience Manager Assets] -gebruikers. Bovendien kunt u de prestaties maximaliseren door de parameters `maxCachedBinarySize` en `cacheSizeInMB` te configureren. Stel `maxCachedBinarySize` in op de kleinste bestandsgrootte die in de cache kan worden opgeslagen. Geef de grootte op van de cache in het geheugen die moet worden gebruikt voor de datastore in `cacheSizeInMB` . Adobe raadt u aan deze waarde in te stellen tussen 2 en 10 procent van de totale heapgrootte. Het testen van de belasting/prestaties kan echter helpen de ideale instelling te bepalen.

### De maximale grootte van de cache voor gebufferde afbeeldingen configureren {#configure-the-maximum-size-of-the-buffered-image-cache}

Wanneer u grote hoeveelheden assets uploadt naar [!DNL Adobe Experience Manager], om onverwachte pieken in het geheugenverbruik mogelijk te maken en om te voorkomen dat JVM uitvalt met OutOfMemoryErrors, verlaagt u de geconfigureerde maximumgrootte van de cache van de gebufferde afbeelding. Overweeg een voorbeeld dat u een systeem met een maximumheap (- `Xmx` param) van 5 GB hebt, een Oak BlobCache die bij 1 GB wordt geplaatst, en documentgeheime voorgeheugen die bij 2 GB wordt geplaatst. In dit geval neemt de gebufferde cache maximaal 1,25 GB en geheugen in beslag, waardoor er slechts 0,75 GB geheugen overblijft voor onverwachte pieken.

Vorm de als buffer opgetreden voor geheim voorgeheugengrootte in de Console van het Web OSGi. Stel bij `https://host:port/system/console/configMgr/com.day.cq.dam.core.impl.cache.CQBufferedImageCache` de eigenschap `cq.dam.image.cache.max.memory` in bytes in. 1073741824 is bijvoorbeeld 1 GB (1024 x 1024 x 1024 = 1 GB).

Van Experience Manager 6.1 SP1, als u een `sling:osgiConfig` knoop voor het vormen van dit bezit gebruikt, zorg ervoor om het gegevenstype aan Lang te plaatsen.

### Gedeelde gegevensopslag {#shared-data-stores}

Het uitvoeren van S3 of de Gedeelde Datastore van het Dossier kan helpen schijfruimte besparen en netwerkproductie in grootschalige implementaties verhogen. Voor meer informatie over de voor- en nadelen van het gebruiken van een gedeelde datastore, zie de [ Assets rangschikkende gids ](/help/assets/assets-sizing-guide.md).

### S3-gegevensopslag {#s-data-store}

De volgende S3 configuratie van de Opslag van Gegevens ( `org.apache.jackrabbit.oak.plugins.blob.datastore.S3DataStore.cfg`) hielp Adobe 12.8 TB binaire grote voorwerpen (BLOBs) uit een bestaande opslag van dossiergegevens in een S3 gegevensopslag bij een klantenplaats halen:

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

Adobe raadt aan HTTPS in te schakelen omdat veel bedrijven firewalls hebben die HTTP-verkeer sluizen, wat het uploaden van bestanden negatief beïnvloedt en bestanden beschadigt. Bij grote bestanden uploaden dient u ervoor te zorgen dat gebruikers een bekabelde verbinding met het netwerk hebben omdat een WiFi-netwerk snel verzadigd raakt. Voor richtlijnen bij het identificeren van netwerkknelpunten, zie de [ Assets rangschikkende gids ](/help/assets/assets-sizing-guide.md). Om netwerkprestaties te beoordelen door netwerktopologie te analyseren, zie [ het netwerkoverwegingen van Assets ](/help/assets/assets-network-considerations.md).

In de eerste plaats is de optimalisatiestrategie van uw netwerk afhankelijk van de hoeveelheid beschikbare bandbreedte en de belasting van uw [!DNL Experience Manager] -instantie. De gemeenschappelijke configuratieopties, met inbegrip van firewalls of volmachten, kunnen helpen netwerkprestaties verbeteren. Hier volgen enkele belangrijke punten die in gedachten moeten worden gehouden:

* Afhankelijk van het instantietype (klein, matig, groot), moet u ervoor zorgen dat u voldoende netwerkbandbreedte hebt voor uw Experience Manager-instantie. Een adequate bandbreedtetoewijzing is vooral belangrijk als [!DNL Experience Manager] wordt gehost op AWS.
* Als uw [!DNL Experience Manager] -instantie wordt gehost op AWS, kunt u profiteren van een veelzijdig schalingsbeleid. Upsize de instantie als de gebruikers een hoge lading verwachten. Downsize het voor matige/lage lading.
* HTTPS: De meeste gebruikers hebben firewalls die het verkeer van HTTP snijden, wat het uploaden van dossiers of zelfs corrupte dossiers tijdens het uploaden kan negatief beïnvloeden.
* Grote bestanden uploaden: zorg dat gebruikers een bekabelde verbinding met het netwerk hebben (WiFi-verbindingen verzadigen snel).

## Workflows {#workflows}

### Tijdelijke workflows {#transient-workflows}

Stel waar mogelijk de [!UICONTROL DAM Update Asset] -workflow in op Transient. De instelling verlaagt aanzienlijk de algemene kosten die nodig zijn voor het verwerken van workflows, omdat workflows in dit geval niet door de normale tracking- en archiveringsprocessen hoeven te gaan.

1. Navigeer naar `/miscadmin` in de [!DNL Experience Manager] -implementatie op `https://[aem_server]:[port]/miscadmin` .

1. Vouw uit **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]** > **[!UICONTROL dam]** .

1. Openen **[!UICONTROL DAM Update Asset]** . Ga in het zwevende deelvenster met gereedschappen naar de tab **[!UICONTROL Page]** en klik op **[!UICONTROL Page Properties]** .

1. Selecteer **[!UICONTROL Transient Workflow]** en klik op **[!UICONTROL OK]** .

   >[!NOTE]
   >
   >Bepaalde functies ondersteunen geen tijdelijke workflows. Configureer geen tijdelijke workflows als deze functies vereist zijn voor uw [!DNL Assets] -implementatie.

Als er geen tijdelijke workflows kunnen worden gebruikt, voert u de workflow regelmatig uit om gearchiveerde [!UICONTROL DAM Update Asset] -workflows te verwijderen om ervoor te zorgen dat de systeemprestaties niet afnemen.

Doorgaans voert u de werkstromen wekelijks uit. Nochtans, in middel-intensieve scenario&#39;s, zoals tijdens brede activaopname, kunt u het vaker uitvoeren.

Om werkschemazuivering te vormen, voeg een nieuwe configuratie van de Woorden van het Werkschema van Adobe Granite door de console OSGi toe. Vervolgens configureert en plant u de workflow als onderdeel van het wekelijkse onderhoudsvenster.

Als het leegmaken te lang duurt, is het wel even uit. Daarom dient u ervoor te zorgen dat uw reinigingstaken zijn voltooid om situaties te voorkomen waarin het leegmaken van werkstromen mislukt als gevolg van het grote aantal werkstromen.

Bijvoorbeeld, na het uitvoeren van talrijke niet-voorbijgaande werkschema&#39;s (die tot de knopen van de werkschemainstantie leidt), kunt u [ ACS het Werkschema van AEM van de Gemeenschap Remover ](https://adobe-consulting-services.github.io/acs-aem-commons/features/workflow-remover.html) op een ad hoc basis uitvoeren. Het verwijdert overbodige, voltooide workflowinstanties onmiddellijk in plaats van te wachten tot de Adobe Granite Workflow Purge-planner wordt uitgevoerd.

### Maximumaantal parallelle banen {#maximum-parallel-jobs}

Standaard wordt in [!DNL Experience Manager] een maximumaantal parallelle taken uitgevoerd dat gelijk is aan het aantal processors op de server. Het probleem met deze instelling is dat tijdens perioden van zware belasting alle processors worden gebruikt door [!UICONTROL DAM Update Asset] -workflows, waardoor de reactiesnelheid van de gebruikersinterface wordt vertraagd en wordt voorkomen dat [!DNL Experience Manager] andere processen uitvoert die de prestaties en stabiliteit van de server garanderen. U kunt deze waarde als een goede praktijk instellen op de helft van de processors die beschikbaar zijn op de server door de volgende stappen uit te voeren:

1. Ga naar [!DNL Experience Manager] Auteur `https://[aem_server]:[port]/system/console/slingevent` .

1. Klik op **[!UICONTROL Edit]** in elke workflowwachtrij die relevant is voor uw implementatie, bijvoorbeeld **[!UICONTROL Granite Transient Workflow Queue]** .

1. Werk de waarde van **[!UICONTROL Maximum Parallel Jobs]** bij en klik op **[!UICONTROL Save]** .

Het instellen van een wachtrij op de helft van de beschikbare processors is een werkbare oplossing om mee te beginnen. Het kan echter zijn dat u dit aantal moet verhogen of verlagen om een maximale doorvoer te bereiken en dat aantal aan te passen aan de omgeving. Er zijn afzonderlijke rijen voor tijdelijke en niet-tijdelijke workflows en andere processen, zoals externe workflows. Als meerdere wachtrijen die zijn ingesteld op 50% van de processors tegelijkertijd actief zijn, kan het systeem snel overbelast raken. De rijen die zwaar worden gebruikt variëren zeer over gebruikersimplementaties. Daarom kunt u hen voor maximumefficiency moeten zorgvuldig vormen zonder serverstabiliteit te offeren.

### DAM Update Asset Configuration {#dam-update-asset-configuration}

De [!UICONTROL DAM Update Asset] -workflow bevat een volledige reeks stappen die zijn geconfigureerd voor taken, zoals Dynamische media PTIFF genereren en [!DNL Adobe InDesign Server] -integratie. Het is echter mogelijk dat de meeste gebruikers niet meerdere van deze stappen nodig hebben. Adobe raadt u aan een aangepaste kopie van het [!UICONTROL DAM Update Asset] -workflowmodel te maken en overbodige stappen te verwijderen. Werk in dit geval de draagraketten voor [!UICONTROL DAM Update Asset] bij om naar het nieuwe model te wijzen.

Als u de [!UICONTROL DAM Update Asset] -workflow intensief uitvoert, kan de bestandsdatastore aanzienlijk groter worden. De resultaten van een door Adobe uitgevoerd experiment hebben aangetoond dat de datastore-grootte met ongeveer 400 GB kan toenemen als binnen 8 uur ongeveer 5500 workflows worden uitgevoerd.

Het is een tijdelijke verhoging, en datastore wordt hersteld aan zijn originele grootte nadat u de taak van de datastore huisvuilinzameling in werking stelt.

Typisch, loopt de de inzamelingstaak van de datastore wekelijks samen met andere geplande onderhoudstaken.

Als u een beperkte schijfruimte hebt en [!UICONTROL DAM Update Asset] werkschema&#39;s intensief in werking stelt, overweeg de taak van de huisvuilinzameling vaker te plannen.

#### Genereren van uitvoering bij uitvoering {#runtime-rendition-generation}

Klanten gebruiken afbeeldingen van verschillende grootten en indelingen op hun website of voor distributie aan zakelijke partners. Aangezien elke uitvoering de afdruk van het middel in de opslagplaats vergroot, raadt Adobe u aan deze functie zorgvuldig te gebruiken. Om de hoeveelheid bronnen te verminderen die nodig is om afbeeldingen te verwerken en op te slaan, kunt u deze afbeeldingen tijdens runtime genereren in plaats van als uitvoeringen tijdens het opnemen.

Vele klanten van Plaatsen voeren een beeldservlet uit die resizes en teelten beelden op het ogenblik zij worden gevraagd, wat extra lading aan de publicatieinstantie oplegt. Maar zolang deze afbeeldingen in het cachegeheugen kunnen worden opgeslagen, kan de uitdaging worden beperkt.

Een andere manier is om gebruik te maken van Dynamic Media-technologie om afbeeldingen volledig te manipuleren. Bovendien kunt u een Brand Portal implementeren die niet alleen taken voor het genereren van uitvoeringen overneemt van de [!DNL Experience Manager] -infrastructuur, maar ook de volledige publicatielaag.

#### ImageMagick {#imagemagick}

Als u de [!UICONTROL DAM Update Asset] -workflow aanpast om uitvoeringen te genereren met ImageMagick, raadt Adobe u aan het `policy.xml` -bestand op `/etc/ImageMagick/` aan te passen. Standaard gebruikt ImageMagick de volledige beschikbare schijfruimte op het volume van het besturingssysteem en het beschikbare geheugen. Breng de volgende configuratiewijzigingen aan in de `policymap` -sectie van `policy.xml` om deze bronnen te beperken.

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

Stel bovendien het pad van de tijdelijke map van ImageMagick in het `configure.xml` -bestand (of door de omgevingsvariabele `MAGICK_TEMPORARY_PATH` in te stellen) in op een schijfpartitie met voldoende ruimte en IOPS.

>[!CAUTION]
>
>Een fout-configuratie kan uw server onstabiel maken als ImageMagick alle beschikbare schijfruimte gebruikt. De beleidswijzigingen die vereist zijn om grote bestanden met ImageMagick te verwerken, kunnen van invloed zijn op de prestaties van [!DNL Experience Manager] . Voor meer informatie, zie [ installeren en vormen ImageMagick ](/help/assets/best-practices-for-imagemagick.md).

>[!NOTE]
>
>De bestanden ImageMagick `policy.xml` en `configure.xml` zijn beschikbaar via `/usr/lib64/ImageMagick-&#42;/config/` in plaats van via `/etc/ImageMagick/` . Zie [ documentatie ImageMagick ](https://www.imagemagick.org/script/resources.php) voor de plaats van de configuratiedossiers.

Als u [!DNL Experience Manager] gebruikt op Adobe Managed Services (AMS), kunt u contact opnemen met de klantenondersteuning van Adobe als u van plan bent een groot aantal grote PSD- of PSB-bestanden te verwerken. Werk samen met een medewerker van de klantenondersteuning van Adobe om deze best practices te implementeren voor uw AMS-implementatie en om de best mogelijke tools en modellen te kiezen voor bedrijfseigen indelingen van Adobe. [!DNL Experience Manager] verwerkt mogelijk geen PSB-bestanden met zeer hoge resolutie die groter zijn dan 30000 x 23000 pixels.

### XMP-schrijfback {#xmp-writeback}

XMP writeback werkt het oorspronkelijke middel bij wanneer de meta-gegevens in [!DNL Experience Manager] worden gewijzigd, wat in het volgende resulteert:

* Het element zelf wordt gewijzigd
* Er wordt een versie van het element gemaakt
* [!UICONTROL DAM Update Asset] wordt uitgevoerd met het element

De vermelde resultaten verbruiken aanzienlijke middelen. Daarom raadt Adobe aan om XMP-back-ups uit te schakelen als dit niet verplicht is. Voor meer informatie, zie [ XMP schrijven ](/help/assets/xmp-writeback.md).

Als u een grote hoeveelheid metagegevens importeert, kan dit leiden tot een bronintensieve XMP-schrijfactiviteit als de runworkflows-markering wordt gecontroleerd. Plan zo&#39;n import tijdens het gebruik van een slanke server, zodat de prestaties voor andere gebruikers niet worden beïnvloed.

## Replicatie {#replication}

Bij het repliceren van elementen naar een groot aantal publicatie-instanties, bijvoorbeeld in een Sites-implementatie, raadt Adobe u aan kettingreplicatie te gebruiken. In dit geval dupliceert de auteurinstantie naar één enkel publicatiegeval dat beurtelings aan andere publiceert instanties herhaalt, die de auteursinstantie vrijmaken.

### Kettingreplicatie configureren {#configure-chain-replication}

1. Bepaal aan welke publicatie-instantie u wilt koppelen
1. Op die publicatieinstantie voegt replicatieagenten toe die aan andere publicatieinstanties richten
1. Schakel op elk van die replicatieagents &quot;Bij ontvangst&quot; in op het tabblad &quot;Triggers&quot;

>[!NOTE]
>
>Adobe raadt automatische activering van elementen niet aan. Indien nodig raadt Adobe u echter aan dit als de laatste stap in een workflow te doen, meestal met DAM Update Asset.

## Indexen zoeken {#search-indexes}

Installeer [ de recentste Packs van de Dienst ](/help/release-notes/release-notes.md) en op prestaties betrekking hebbende hotfixes zoals die vaak updates aan systeemindexen omvatten. Zie [ prestaties het stemmen uiteinden ](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/assets/administer/performance-tuning-guidelines) voor sommige indexoptimalisaties.

Maak aangepaste indexen voor query&#39;s die u vaak uitvoert. Voor details, zie de [ methodologie voor het analyseren van langzame vragen ](https://aemfaq.blogspot.com/2014/08/oak-query-log-file-analyzer-tool.html) en [ crefting douaneindexen ](/help/sites-deploying/queries-and-indexing.md). Voor extra inzichten rond vraag en index beste praktijken, zie [ Beste praktijken voor Vragen en het Indexeren ](/help/sites-deploying/best-practices-for-queries-and-indexing.md).

### Lucene-indexconfiguraties {#lucene-index-configurations}

Sommige optimalisaties kunnen worden uitgevoerd op Oak-indexconfiguraties die de prestaties van [!DNL Experience Manager Assets] kunnen verbeteren. Werk de indexconfiguraties bij om de re-indexerende tijd te verbeteren:

1. Open CRXDe `/crx/de/index.jsp` en meld u aan als beheergebruiker.
1. Blader naar `/oak:index/lucene` .
1. Voeg een eigenschap `String[]` `excludedPaths` met waarden `/var` , `/etc/workflow/instances` en `/etc/replication` toe.
1. Blader naar `/oak:index/damAssetLucene` . Voeg een `String[]` eigenschap `includedPaths` met waarde `/content/dam` toe. Wijzigingen opslaan.

Als uw gebruikers geen full-text onderzoek van activa hoeven te doen, bijvoorbeeld, doorzoekend door tekst in de documenten van PDF, dan onbruikbaar maken. U verbetert indexprestaties door full-text indexering onbruikbaar te maken. Voer de volgende stappen uit om het uitnemen van [!DNL Apache Lucene] -tekst uit te schakelen:

1. Open [!UICONTROL Package Manager] in de interface [!DNL Experience Manager] .
1. Upload en installeer het pakket beschikbaar bij [ disable_indexingbinarytextraction-10.zip ](assets/disable_indexingbinarytextextraction-10.zip).

### Totaal raden {#guess-total}

Wanneer u query&#39;s maakt die grote resultaatsets genereren, gebruikt u de parameter `guessTotal` om te voorkomen dat er veel geheugen wordt gebruikt wanneer u deze uitvoert.

## Bekende problemen {#known-issues}

### Grote bestanden {#large-files}

Er zijn twee belangrijke bekende problemen met betrekking tot grote bestanden in [!DNL Experience Manager] . Wanneer de dossiers grootten groter dan 2 GB bereiken, kan de koude reserve synchronisatie in een uit-van-geheugensituatie lopen. In sommige gevallen wordt de stand-bysynchronisatie niet uitgevoerd. In andere gevallen loopt de primaire instantie vast. Dit scenario geldt voor elk bestand in [!DNL Experience Manager] dat groter is dan 2 GB, inclusief inhoudspakketten.

Op dezelfde manier kan het enige tijd duren voordat het bestand, wanneer bestanden een grootte van 2 GB bereiken bij gebruik van een gedeelde S3-gegevensopslag, volledig doorloopt van de cache naar het bestandssysteem. Dientengevolge, wanneer het gebruiken van binair-minder replicatie, is het mogelijk dat de binaire gegevens niet kunnen zijn voortgeduurd alvorens de replicatie voltooit. Deze situatie kan tot problemen leiden, vooral als de beschikbaarheid van gegevens belangrijk is.

## Prestatietests {#performance-testing}

Stel voor elke [!DNL Experience Manager] -implementatie een testregime in voor de prestaties waarmee knelpunten snel kunnen worden geïdentificeerd en opgelost. Hier volgen enkele belangrijke aandachtsgebieden.

### Netwerktests {#network-testing}

Voor alle kwesties van netwerkprestaties voor de klant, voer de volgende taken uit:

* De netwerkprestaties van de test van binnen het klantennetwerk
* Test netwerkprestaties vanuit het Adobe-netwerk. Voor klanten van AMS, werk met uw CSE om van binnen het netwerk van Adobe te testen.
* De netwerkprestaties van de test van een ander toegangspunt
* Door een hulpmiddel van de netwerkbenchmark te gebruiken
* Testen tegen de Dispatcher

### [!DNL Experience Manager] implementatietests {#aem-deployment-testing}

Om de latentie te minimaliseren en een hoge doorvoer te bereiken via efficiënt gebruik en delen van de belasting door CPU, kunt u de prestaties van uw implementatie van [!DNL Experience Manager] regelmatig controleren. Met name:

* Laadtests uitvoeren op basis van de [!DNL Experience Manager] -implementatie.
* Uploadprestaties controleren en reageren op de gebruikersinterface.

## [!DNL Experience Manager Assets] Controlelijst voor prestaties en impact van taken voor middelenbeheer {#checklist}

* Schakel HTTPS in om rondom eventuele bedrijfs-HTTP-verkeerssniffers te komen.
* Gebruik een bekabelde verbinding voor het uploaden van zware middelen.
* Implementeer in Java 8.
* Stel optimale JVM-parameters in.
* Configureer een FileSystem DataStore of een S3-gegevensopslag.
* Genereren van subelementen uitschakelen. Als deze optie is ingeschakeld, maakt de AEM-workflow een afzonderlijk element voor elke pagina in een element met meerdere pagina&#39;s. Elk van deze pagina&#39;s is een individueel middel dat extra schijfruimte verbruikt, versioning, en extra werkschemaverwerking vereist. Als u geen afzonderlijke pagina&#39;s nodig hebt, schakelt u het genereren van subelementen en het uitnemen van pagina&#39;s uit.
* Schakel tijdelijke workflows in.
* Stem de wachtrijen voor de Granite-workflow af om gelijktijdige taken te beperken.
* Configureer [!DNL ImageMagick] om het verbruik van bronnen te beperken.
* Verwijder overbodige stappen uit de [!UICONTROL DAM Update Asset] -workflow.
* Vorm werkschema en versie het zuiveren.
* Optimaliseer indexen met de recentste Packs en hotfixes van de Dienst. Raadpleeg de klantenondersteuning van Adobe voor eventuele extra indexoptimalisaties die beschikbaar zijn.
* Gebruik radenTotal om queryprestaties te optimaliseren.
* Als u [!DNL Experience Manager] configureert om bestandstypen te detecteren op basis van de inhoud van de bestanden (door **[!UICONTROL Day CQ DAM Mime Type Service]** in de **[!UICONTROL AEM Web Console]** in te schakelen), uploadt u veel bestanden in bulk tijdens niet-piekuren, omdat dit veel bronnen vergt.
