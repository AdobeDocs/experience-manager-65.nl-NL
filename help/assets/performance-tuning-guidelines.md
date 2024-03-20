---
title: Prestaties afstemmen [!DNL Assets].
description: Suggesties en richtlijnen over [!DNL Experience Manager] configuratie, veranderingen in hardware, software, en netwerkcomponenten om knelpunten te verwijderen en de prestaties van te optimaliseren [!DNL Experience Manager Assets].
contentOwner: AG
mini-toc-levels: 1
role: Architect, Admin
feature: Asset Management
exl-id: 1d9388de-f601-42bf-885b-6a7c3236b97e
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '2662'
ht-degree: 0%

---

<!-- TBD: Get reviewed by engineering. -->

# [!DNL Adobe Experience Manager Assets] richtlijn voor afstelling van prestaties {#assets-performance-tuning-guide}

An [!DNL Experience Manager Assets] de opstelling bevat verscheidene hardware, software, en netwerkcomponenten. Afhankelijk van uw plaatsingsscenario, kunt u specifieke configuratieveranderingen in hardware, software, en netwerkcomponenten vereisen om prestatiesknelpunten te verwijderen.

Bovendien kunt u door bepaalde richtlijnen voor de optimalisatie van hardware en software te identificeren en aan te houden een solide basis leggen voor uw [!DNL Experience Manager Assets] implementatie om te voldoen aan de verwachtingen op het gebied van prestaties, schaalbaarheid en betrouwbaarheid.

Slechte prestaties in [!DNL Experience Manager Assets] Dit kan van invloed zijn op de interactieve prestaties, de verwerking van bedrijfsmiddelen, de downloadsnelheid en andere onderdelen.

In feite, is de prestatiesoptimalisering een fundamentele taak die u uitvoert alvorens u doelmetriek voor om het even welk project vestigt.

Hier zijn bepaalde belangrijke aandachtsgebieden waaromheen u prestatieproblemen ontdekt en verhelpt voordat deze van invloed zijn op gebruikers.

## Platform {#platform}

Hoewel Experience Manager op verschillende platformen wordt ondersteund, biedt Adobe de grootste ondersteuning voor native gereedschappen in Linux en Windows, wat bijdraagt aan optimale prestaties en een eenvoudige implementatie. In het ideale geval moet u een 64-bits besturingssysteem implementeren om te voldoen aan de hoge geheugenvereisten van een [!DNL Experience Manager Assets] implementatie. Zoals met om het even welke plaatsing van de Experience Manager, zou u TarMK moeten uitvoeren waar mogelijk. Hoewel TarMK niet voorbij één enkele auteurinstantie kan schrapen, wordt het gevonden om beter te presteren dan MongoMK. U kunt TarMK-offloadinstanties toevoegen om de verwerkingskracht van de workflow te verhogen [!DNL Experience Manager Assets] implementatie.

### Tijdelijke map {#temp-folder}

Om de uploadtijden van middelen te verbeteren, gebruik krachtige opslag voor de tijdelijke folder van Java. In Linux en Windows kan een RAM-station of SSD worden gebruikt. In cloudomgevingen kan een vergelijkbaar type snelle opslag worden gebruikt. In Amazon EC2 bijvoorbeeld [ephalogeffect](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/InstanceStorage.html) kan worden gebruikt voor de tijdelijke map.

Ervan uitgaande dat de server over voldoende geheugen beschikt, configureert u een RAM-station. Voer in Linux de volgende opdrachten uit om een 8 GB RAM-station te maken:

```shell
mkfs -q /dev/ram1 800000
 mkdir -p /mnt/aem-tmp
 mount /dev/ram1 /mnt/aem-tmp
 df -H | grep aem-tmp
```

In Windows OS gebruikt u een stuurprogramma van een andere fabrikant om een RAM-station te maken of gewoon krachtige opslagsystemen zoals SSD te gebruiken.

Als het tijdelijke volume met hoge prestaties gereed is, stelt u de JVM-parameter in `-Djava.io.tmpdir`. U kunt bijvoorbeeld de JVM-parameter hieronder toevoegen aan de `CQ_JVM_OPTS` in de `bin/start` script van [!DNL Experience Manager]:

`-Djava.io.tmpdir=/mnt/aem-tmp`

## Java-configuratie {#java-configuration}

### Java-versie {#java-version}

Adobe raadt implementatie aan [!DNL Experience Manager Assets] in Java 8 voor optimale prestaties.

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

Het scheiden van de gegevensopslag van de segmentopslag wordt geadviseerd voor allen [!DNL Experience Manager Assets] gebruikers. Bovendien vormt het vormen van `maxCachedBinarySize` en `cacheSizeInMB` parameters kunnen u helpen de prestaties te maximaliseren. Set `maxCachedBinarySize` tot de kleinste bestandsgrootte die in de cache kan worden opgeslagen. Geef de grootte op van de cache in het geheugen die moet worden gebruikt voor de datastore in `cacheSizeInMB`. Adobe raadt u aan deze waarde in te stellen tussen 2-10 procent van de totale heapgrootte. Het testen van de belasting/prestaties kan echter helpen de ideale instelling te bepalen.

### De maximale grootte van de cache voor gebufferde afbeeldingen configureren {#configure-the-maximum-size-of-the-buffered-image-cache}

Bij het uploaden van grote hoeveelheden elementen naar [!DNL Adobe Experience Manager], om onverwachte pieken in geheugenverbruik mogelijk te maken en om te voorkomen dat JVM uitvalt met OutOfMemoryErrors, de geconfigureerde maximale grootte van de cache van de gebufferde afbeelding verminderen. Neem bijvoorbeeld een voorbeeld van een systeem met een maximale heap (- `Xmx`param) van 5 GB, een Oak BlobCache ingesteld op 1 GB en een documentcache ingesteld op 2 GB. In dit geval neemt de gebufferde cache maximaal 1,25 GB en geheugen in beslag, waardoor er slechts 0,75 GB geheugen overblijft voor onverwachte pieken.

Vorm de als buffer opgetreden voor geheim voorgeheugengrootte in de Console van het Web OSGi. At `https://host:port/system/console/configMgr/com.day.cq.dam.core.impl.cache.CQBufferedImageCache`, stelt u de eigenschap in `cq.dam.image.cache.max.memory` in bytes. 1073741824 is bijvoorbeeld 1 GB (1024 x 1024 x 1024 = 1 GB).

Van Experience Manager 6.1 SP1, als u een `sling:osgiConfig` knoop voor het vormen van dit bezit, zorg ervoor om het gegevenstype aan Lang te plaatsen. Zie voor meer informatie [CQBufferedImageCache verbruikt heap tijdens het uploaden van middelen](https://helpx.adobe.com/experience-manager/kb/cqbufferedimagecache-consumes-heap-during-asset-uploads.html).

### Gedeelde gegevensopslag {#shared-data-stores}

Het uitvoeren van S3 of de Gedeelde Datastore van het Dossier kan helpen schijfruimte besparen en netwerkproductie in grootschalige implementaties verhogen. Zie voor meer informatie over de voor- en nadelen van het gebruik van een gedeelde datastore [Hulplijn voor middelengrootte](/help/assets/assets-sizing-guide.md).

### S3-gegevensopslag {#s-data-store}

De volgende S3 configuratie van de Opslag van Gegevens ( `org.apache.jackrabbit.oak.plugins.blob.datastore.S3DataStore.cfg`) hielp Adobe 12,8 TB binaire grote voorwerpen (BLOBs) uit een bestaande opslag van dossiergegevens in een S3 gegevensopslag bij een klantenplaats halen:

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

Adobe raadt aan HTTPS in te schakelen omdat veel bedrijven firewalls hebben die HTTP-verkeer sluizen, wat het uploaden en het beschadigen van bestanden nadelig beïnvloedt. Bij grote bestanden uploaden dient u ervoor te zorgen dat gebruikers een bekabelde verbinding met het netwerk hebben omdat een WiFi-netwerk snel verzadigd raakt. Voor richtsnoeren voor het identificeren van netwerkknelpunten raadpleegt u [Hulplijn voor middelengrootte](/help/assets/assets-sizing-guide.md). Om netwerkprestaties te beoordelen door netwerktopologie te analyseren, zie [Elementennetwerkoverwegingen](/help/assets/assets-network-considerations.md).

Primair, hangt uw strategie van de netwerkoptimalisering van de hoeveelheid beschikbare bandbreedte en de lading op uw af [!DNL Experience Manager] -instantie. De gemeenschappelijke configuratieopties, met inbegrip van firewalls of volmachten kunnen helpen netwerkprestaties verbeteren. Hier volgen enkele belangrijke punten die in gedachten moeten worden gehouden:

* Afhankelijk van uw instantietype (klein, gematigd, groot), zorg ervoor dat u voldoende netwerkbandbreedte voor uw instantie van de Experience Manager hebt. De adequate bandbreedtetoewijzing is vooral belangrijk als [!DNL Experience Manager] wordt gehost op AWS.
* Als uw [!DNL Experience Manager] -instantie wordt gehost op AWS, kunt u profiteren van een veelzijdig schalingsbeleid. De instantie vergroten als gebruikers een hoge belasting verwachten. Downsize het voor matige/lage lading.
* HTTPS: De meeste gebruikers hebben firewalls die het verkeer van HTTP snijden, wat het uploaden van dossiers of zelfs corrupte dossiers tijdens het uploaden kan negatief beïnvloeden.
* Grote bestanden uploaden: zorg dat gebruikers een bekabelde verbinding met het netwerk hebben (WiFi-verbindingen verzadigen snel).

## Workflows {#workflows}

### Tijdelijke workflows {#transient-workflows}

Stel, waar mogelijk, de [!UICONTROL DAM Update Asset] workflow naar Overgang. De instelling verlaagt aanzienlijk de algemene kosten die nodig zijn voor het verwerken van workflows, omdat workflows in dit geval niet door de normale tracking- en archiveringsprocessen hoeven te gaan.

1. Navigeren naar `/miscadmin` in de [!DNL Experience Manager] implementatie bij `https://[aem_server]:[port]/miscadmin`.

1. Uitbreiden **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]** > **[!UICONTROL dam]**.

1. Openen **[!UICONTROL DAM Update Asset]**. Van het het drijven hulpmiddelpaneel, schakelaar aan **[!UICONTROL Page]** en klikt u op **[!UICONTROL Page Properties]**.

1. Selecteren **[!UICONTROL Transient Workflow]** en klik op **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Bepaalde functies ondersteunen geen tijdelijke workflows. Als uw [!DNL Assets] de implementatie vereist deze functies, configureer geen tijdelijke workflows.

Als er geen tijdelijke workflows kunnen worden gebruikt, moet u regelmatig de workflow leegmaken om gearchiveerde werkstromen te verwijderen [!UICONTROL DAM Update Asset] workflows om ervoor te zorgen dat de systeemprestaties niet afnemen.

Doorgaans voert u de werkstromen wekelijks uit. Nochtans, in middel-intensieve scenario&#39;s, zoals tijdens brede activaopname, kunt u het vaker uitvoeren.

Om werkschemazuivering te vormen, voeg een nieuwe configuratie van de Woorden van het Werkschema van de Adobe Granite door de console OSGi toe. Vervolgens configureert en plant u de workflow als onderdeel van het wekelijkse onderhoudsvenster.

Als het leegmaken te lang duurt, is het wel even uit. Daarom dient u ervoor te zorgen dat uw reinigingstaken zijn voltooid om situaties te voorkomen waarin het leegmaken van werkstromen mislukt als gevolg van het grote aantal werkstromen.

U kunt bijvoorbeeld na het uitvoeren van een groot aantal niet-tijdelijke workflows (waarmee knooppunten voor workflowinstanties worden gemaakt) [ACS AEM Comment Workflow Remover](https://adobe-consulting-services.github.io/acs-aem-commons/features/workflow-remover.html) ad hoc. Het verwijdert overtollige, voltooide werkschemainstanties onmiddellijk eerder dan het wachten op de Adobe van de Schoonmaakplanner van het Werkschema van Granite om te lopen.

### Maximumaantal parallelle banen {#maximum-parallel-jobs}

Standaard, [!DNL Experience Manager] wordt een maximumaantal parallelle taken uitgevoerd dat gelijk is aan het aantal processors op de server. Het probleem met deze instelling is dat tijdens zware werktijden alle processors door [!UICONTROL DAM Update Asset] workflows, snelheid van de gebruikersinterface verlagen en voorkomen [!DNL Experience Manager] van het uitvoeren van andere processen die serverprestaties en stabiliteit beschermen. U kunt deze waarde als een goede praktijk instellen op de helft van de processors die beschikbaar zijn op de server door de volgende stappen uit te voeren:

1. Aan [!DNL Experience Manager] Auteur, toegang `https://[aem_server]:[port]/system/console/slingevent`.

1. Klikken **[!UICONTROL Edit]** in elke werkstroomwachtrij die relevant is voor uw implementatie, bijvoorbeeld **[!UICONTROL Granite Transient Workflow Queue]**.

1. Werk de waarde bij van **[!UICONTROL Maximum Parallel Jobs]** en klik op **[!UICONTROL Save]**.

Het instellen van een wachtrij op de helft van de beschikbare processors is een werkbare oplossing om mee te beginnen. Het kan echter zijn dat u dit aantal moet verhogen of verlagen om een maximale doorvoer te bereiken en dat aantal aan te passen aan de omgeving. Er zijn afzonderlijke rijen voor tijdelijke en niet-tijdelijke workflows en andere processen, zoals externe workflows. Als meerdere wachtrijen die zijn ingesteld op 50% van de processors tegelijkertijd actief zijn, kan het systeem snel overbelast raken. De rijen die zwaar worden gebruikt variëren zeer over gebruikersimplementaties. Daarom kunt u hen voor maximumefficiency moeten zorgvuldig vormen zonder serverstabiliteit te offeren.

### DAM Update Asset Configuration {#dam-update-asset-configuration}

De [!UICONTROL DAM Update Asset] de workflow bevat een volledige reeks stappen die zijn geconfigureerd voor taken, zoals het genereren van Dynamic Media PTIFF en [!DNL Adobe InDesign Server] integratie. Het is echter mogelijk dat de meeste gebruikers niet meerdere van deze stappen nodig hebben. Adobe raadt u aan een aangepaste kopie van het dialoogvenster [!UICONTROL DAM Update Asset] workflowmodel en verwijdert onnodige stappen. In dit geval werkt u de draagraketten bij voor [!UICONTROL DAM Update Asset] naar het nieuwe model te verwijzen.

De [!UICONTROL DAM Update Asset] intensief werken kan de grootte van de datatastore van uw bestand aanzienlijk vergroten. De resultaten van een door Adobe uitgevoerd experiment hebben aangetoond dat de datastore-grootte met ongeveer 400 GB kan toenemen als ongeveer 5500 workflows binnen 8 uur worden uitgevoerd.

Het is een tijdelijke verhoging, en datastore wordt hersteld aan zijn originele grootte nadat u de taak van de datastore huisvuilinzameling in werking stelt.

Typisch, loopt de de inzamelingstaak van de datastore wekelijks samen met andere geplande onderhoudstaken.

Als u over een beperkte schijfruimte beschikt en [!UICONTROL DAM Update Asset] De werkschema&#39;s intensief, denken het plannen van de huisvuilinzamelingstaak vaker.

#### Genereren van uitvoering bij uitvoering {#runtime-rendition-generation}

Klanten gebruiken afbeeldingen van verschillende grootten en indelingen op hun website of voor distributie aan zakelijke partners. Aangezien elke uitvoering de afdruk van het middel in de opslagplaats vergroot, raadt de Adobe u aan deze functie zorgvuldig te gebruiken. Om de hoeveelheid bronnen te verminderen die nodig is om afbeeldingen te verwerken en op te slaan, kunt u deze afbeeldingen tijdens runtime genereren in plaats van als uitvoeringen tijdens het opnemen.

Vele klanten van Plaatsen voeren een beeldservlet uit die resizes en teelten beelden op het ogenblik zij worden gevraagd, wat extra lading aan de publicatieinstantie oplegt. Maar zolang deze afbeeldingen in het cachegeheugen kunnen worden opgeslagen, kan de uitdaging worden beperkt.

Een andere manier is om Dynamic Media-technologie te gebruiken om beeldmanipulatie volledig uit te schakelen. Bovendien kunt u Brand Portal implementeren die niet alleen taken voor het genereren van uitvoeringen overneemt van de [!DNL Experience Manager] infrastructuur, maar ook de volledige publicatielaag.

#### ImageMagick {#imagemagick}

Als u de [!UICONTROL DAM Update Asset] workflow voor het genereren van uitvoeringen met ImageMagick; Adobe raadt u aan de `policy.xml` bestand bij `/etc/ImageMagick/`. Standaard gebruikt ImageMagick de volledige beschikbare schijfruimte op het volume van het besturingssysteem en het beschikbare geheugen. Breng de volgende configuratiewijzigingen aan in de `policymap` deel van `policy.xml` om deze middelen te beperken.

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

Stel bovendien het pad in naar de tijdelijke map van ImageMagick in het dialoogvenster `configure.xml` bestand (of door de omgevingsvariabele in te stellen `MAGICK_TEMPORARY_PATH`) naar een schijfpartitie met voldoende ruimte en IOPS.

>[!CAUTION]
>
>Een fout-configuratie kan uw server onstabiel maken als ImageMagick alle beschikbare schijfruimte gebruikt. De beleidswijzigingen die vereist zijn om grote bestanden te verwerken met ImageMagick kunnen van invloed zijn op de [!DNL Experience Manager] prestaties. Zie voor meer informatie [ImageMagick installeren en configureren](/help/assets/best-practices-for-imagemagick.md).

>[!NOTE]
>
>The ImageMagick `policy.xml` en `configure.xml` bestanden zijn beschikbaar op `/usr/lib64/ImageMagick-&#42;/config/` in plaats van `/etc/ImageMagick/`Zie [ImageMagick-documentatie](https://www.imagemagick.org/script/resources.php) voor de locatie van de configuratiebestanden.

Als u [!DNL Experience Manager] op Adobe Managed Services (AMS), vraag aan de Steun van de Klant van de Adobe als u van plan bent om veel grote PSD of PSB dossiers te verwerken. Werk samen met de medewerker van de klantenondersteuning van de Adobe om deze best practices voor uw AMS-implementatie te implementeren en de best mogelijke tools en modellen te kiezen voor de eigen indelingen van de Adobe. [!DNL Experience Manager] PSB-bestanden met een zeer hoge resolutie die groter zijn dan 30000 x 23000 pixels, worden mogelijk niet verwerkt.

### XMP terugschrijven {#xmp-writeback}

XMP terugschrijven werkt het oorspronkelijke element bij wanneer metagegevens worden gewijzigd in [!DNL Experience Manager], wat resulteert in het volgende:

* Het element zelf wordt gewijzigd
* Er wordt een versie van het element gemaakt
* [!UICONTROL DAM Update Asset] wordt uitgevoerd met het element

De vermelde resultaten verbruiken aanzienlijke middelen. Daarom raadt de Adobe aan XMP terugschrijven uit te schakelen als dit niet vereist is. Zie voor meer informatie [XMP terugschrijven](/help/assets/xmp-writeback.md).

Het invoeren van een grote hoeveelheid meta-gegevens kan in middel-intensieve XMP terugzetactiviteit resulteren als de loopwerkstroomvlag wordt gecontroleerd. Plan zo&#39;n import tijdens het gebruik van een slanke server, zodat de prestaties voor andere gebruikers niet worden beïnvloed.

## Replicatie {#replication}

Wanneer het herhalen van activa aan een groot aantal publiceer instanties, bijvoorbeeld, in een implementatie van Plaatsen, adviseert de Adobe u kettingreplicatie te gebruiken. In dit geval dupliceert de auteurinstantie naar één enkel publicatiegeval dat beurtelings aan andere publiceert instanties herhaalt, die de auteursinstantie vrijmaken.

### Kettingreplicatie configureren {#configure-chain-replication}

1. Bepaal aan welke publicatie-instantie u wilt koppelen
1. Op die publicatieinstantie voegt replicatieagenten toe die aan andere publicatieinstanties richten
1. Schakel op elk van die replicatieagents &quot;Bij ontvangst&quot; in op het tabblad &quot;Triggers&quot;

>[!NOTE]
>
>Adobe beveelt geen automatische activering van elementen aan. Indien nodig raadt de Adobe echter aan dit als de laatste stap in een workflow te doen, meestal DAM Update Asset.

## Indexen zoeken {#search-indexes}

Installeren [de nieuwste servicepacks](/help/release-notes/release-notes.md) en aan prestaties gerelateerde hotfixes zoals die vaak updates aan systeemindexen omvatten. Zie [tips voor het afstemmen van prestaties](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/performance-tuning-guidelines.html?lang=en) voor sommige indexoptimalisaties.

Maak aangepaste indexen voor query&#39;s die u vaak uitvoert. Zie voor meer informatie [methodologie voor het analyseren van trage query&#39;s](https://aemfaq.blogspot.com/2014/08/oak-query-log-file-analyzer-tool.html) en [aangepaste indexen maken](/help/sites-deploying/queries-and-indexing.md). Voor extra inzichten rond vraag en index beste praktijken, zie [Beste praktijken voor Vragen en het Indexeren](/help/sites-deploying/best-practices-for-queries-and-indexing.md).

### Lucene-indexconfiguraties {#lucene-index-configurations}

Sommige optimalisaties kunnen worden uitgevoerd op de indexconfiguraties van de eik die u kunnen helpen [!DNL Experience Manager Assets] prestaties. Werk de indexconfiguraties bij om de re-indexerende tijd te verbeteren:

1. CRXDe openen `/crx/de/index.jsp` en meld u aan als beheerder.
1. Bladeren naar `/oak:index/lucene`.
1. Voeg een `String[]` eigenschap `excludedPaths` met waarden `/var`, `/etc/workflow/instances`, en `/etc/replication`.
1. Bladeren naar `/oak:index/damAssetLucene`. Voeg een `String[]` eigenschap `includedPaths` met waarde `/content/dam`. Wijzigingen opslaan.

Als uw gebruikers geen full-text onderzoek van activa hoeven te doen, bijvoorbeeld, doorzoekend door tekst in documenten van de PDF, dan onbruikbaar maken. U verbetert indexprestaties door full-text indexering onbruikbaar te maken. Uitschakelen [!DNL Apache Lucene] tekstextractie, voer de volgende stappen uit:

1. In [!DNL Experience Manager] interface, toegang [!UICONTROL Package Manager].
1. Upload en installeer het pakket dat beschikbaar is op [disable_indexingbinarytextraction-10.zip](assets/disable_indexingbinarytextextraction-10.zip).

### Totaal raden {#guess-total}

Gebruik bij het maken van query&#39;s die grote resultaatsets genereren de opdracht `guessTotal` gebruiken om te voorkomen dat er veel geheugen wordt gebruikt wanneer u deze uitvoert.

## Bekende problemen {#known-issues}

### Grote bestanden {#large-files}

Er zijn twee belangrijke bekende problemen met betrekking tot grote bestanden in [!DNL Experience Manager]. Wanneer de dossiers grootten groter dan 2 GB bereiken, kan de koude reserve synchronisatie in een uit-van-geheugensituatie lopen. In sommige gevallen wordt de stand-bysynchronisatie niet uitgevoerd. In andere gevallen loopt de primaire instantie vast. Dit scenario geldt voor elk bestand in [!DNL Experience Manager] die groter is dan 2 GB, inclusief inhoudspakketten.

Op dezelfde manier kan het enige tijd duren voordat het bestand, wanneer bestanden een grootte van 2 GB bereiken bij gebruik van een gedeelde S3-gegevensopslag, volledig doorloopt van de cache naar het bestandssysteem. Dientengevolge, wanneer het gebruiken van binair-minder replicatie, is het mogelijk dat de binaire gegevens niet kunnen zijn voortgeduurd alvorens de replicatie voltooit. Deze situatie kan tot problemen leiden, vooral als de beschikbaarheid van gegevens belangrijk is.

## Prestatietests {#performance-testing}

Voor elke [!DNL Experience Manager] de implementatie, een prestatietestregeling opzetten die knelpunten snel kan opsporen en oplossen. Hier volgen enkele belangrijke aandachtsgebieden.

### Netwerktests {#network-testing}

Voor alle kwesties van netwerkprestaties van de klant, voer de volgende taken uit:

* De netwerkprestaties van de test van binnen het klantennetwerk
* De netwerkprestaties van de test van binnen het netwerk van de Adobe. Voor klanten van AMS, werk met uw CSE om van binnen het netwerk van de Adobe te testen.
* De netwerkprestaties van de test van een ander toegangspunt
* Door een hulpmiddel van de netwerkbenchmark te gebruiken
* Testen tegen de verzender

### [!DNL Experience Manager] implementatie testen {#aem-deployment-testing}

Om latentie te minimaliseren en een hoge doorvoer te bereiken via efficiënt CPU-gebruik en delen van de belasting, kunt u de prestaties van uw [!DNL Experience Manager] regelmatig worden ingezet. Met name:

* Belastingtests uitvoeren tegen de [!DNL Experience Manager] implementatie.
* Uploadprestaties controleren en reageren op de gebruikersinterface.

## [!DNL Experience Manager Assets] prestatiecontrolelijst en impact van taken voor middelenbeheer {#checklist}

* Schakel HTTPS in om rondom eventuele bedrijfs-HTTP-verkeerssniffers te komen.
* Gebruik een bekabelde verbinding voor het uploaden van zware middelen.
* Implementeer in Java 8.
* Stel optimale JVM-parameters in.
* Configureer een FileSystem DataStore of een S3-gegevensopslag.
* Genereren van subelementen uitschakelen. Als deze optie is ingeschakeld, maakt AEM workflow een afzonderlijk element voor elke pagina in een element van meerdere pagina&#39;s. Elk van deze pagina&#39;s is een individueel middel dat extra schijfruimte verbruikt, versioning, en extra werkschemaverwerking vereist. Als u geen afzonderlijke pagina&#39;s nodig hebt, schakelt u het genereren van subelementen en het uitnemen van pagina&#39;s uit.
* Schakel tijdelijke workflows in.
* Stem de wachtrijen voor de Granite-workflow af om gelijktijdige taken te beperken.
* Configureren [!DNL ImageMagick] om het verbruik van hulpbronnen te beperken.
* Verwijder overbodige stappen uit het dialoogvenster [!UICONTROL DAM Update Asset] workflow.
* Vorm werkschema en versie het zuiveren.
* Optimaliseer indexen met de recentste Packs en hotfixes van de Dienst. Raadpleeg de klantenondersteuning van de Adobe voor eventuele extra indexoptimalisaties die beschikbaar zijn.
* Gebruik radenTotal om queryprestaties te optimaliseren.
* Als u [!DNL Experience Manager] om bestandstypen van de inhoud van de bestanden te detecteren (door **[!UICONTROL Day CQ DAM Mime Type Service]** in de **[!UICONTROL AEM Web Console]**), veel bestanden bulksgewijs uploaden tijdens niet-piekuren omdat dit een bronintensieve taak is.
