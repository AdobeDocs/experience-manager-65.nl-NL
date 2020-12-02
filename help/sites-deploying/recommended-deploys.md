---
title: Aanbevolen implementaties
seo-title: Aanbevolen implementaties
description: Dit artikel beschrijft de geadviseerde topologieën voor AEM.
seo-description: Dit artikel beschrijft de geadviseerde topologieën voor AEM.
uuid: bc638121-c531-43eb-9ec6-3283a33519f8
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
discoiquuid: 66d351e1-87f1-4006-bf8a-3cbbd33db9ed
docset: aem65
translation-type: tm+mt
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65
workflow-type: tm+mt
source-wordcount: '1802'
ht-degree: 0%

---


# Aanbevolen implementaties{#recommended-deployments}

>[!NOTE]
>
>Deze pagina verwijst naar geadviseerde topologieën voor AEM. Raadpleeg de [documentatie van de API voor Apache Sling-detectie](https://sling.apache.org/documentation/bundles/discovery-api-and-impl.html) voor meer informatie over clusteringmogelijkheden en hoe u deze kunt configureren.

MicroKernels fungeren vanaf AEM 6.2 als persistentiemanagers. Het kiezen van één om uw behoeften te passen hangt van het doel van uw instantie en het plaatsingstype af u overweegt.

De volgende voorbeelden moeten een indicatie zijn van wat hun aanbevolen gebruik in de meest gebruikelijke AEM is.

## Implementatiescenario&#39;s {#deployment-scenarios}

### Eén TarMK-instantie {#single-tarmk-instance}

In dit scenario, loopt één enkele instantie TarMK op één enkele server.

**Dit is de standaardplaatsing voor auteursinstanties.**

![chlimage_1-15](assets/chlimage_1-15.png)

De voordelen:

* Eenvoudig
* Eenvoudig onderhoud
* Goede prestaties

De nadelen:

* Niet schaalbaar buiten de grenzen van de servercapaciteit
* Geen failover-capaciteit

### TarMK Cold Standby {#tarmk-cold-standby}

Eén TarMK-instantie fungeert als de primaire instantie. De opslagplaats van de primaire opslagplaats wordt gerepliceerd naar een stand-by failover-systeem.

Het koude reservemechanisme kan ook als steun worden gebruikt omdat de volledige bewaarplaats constant aan de failoverserver wordt herhaald. De failoverserver loopt op koude reservewijze, wat betekent dat slechts HttpReceiver van de instantie loopt.

![chlimage_1-16](assets/chlimage_1-16.png)

De voordelen:

* Eenvoud
* Onderhoudsmogelijkheden
* Prestaties
* Failover

De nadelen:

* Niet schaalbaar buiten de grenzen van de servercapaciteit
* Eén server is meestal inactief
* De failover is niet automatisch. Het moet extern worden ontdekt alvorens het failoversysteem verzoeken kan beginnen te dienen.

>[!NOTE]
>
>Zie [dit](/help/sites-deploying/tarmk-cold-standby.md) artikel voor meer informatie over het configureren van AEM met TarMK Cold Standby.

>[!NOTE]
>
>De plaatsing van de Reserve van de Koude in dit voorbeeld TarMK vereist dat zowel de primaire als reserve instanties afzonderlijk worden vergunning gegeven, aangezien er constante replicatie aan de failoverserver is. Raadpleeg de [Algemene licentievoorwaarden van Adobe voor meer informatie over licenties](https://www.adobe.com/legal/terms/enterprise-licensing.html).

### TarMK Farm {#tarmk-farm}

Meerdere Oak-instanties worden elk uitgevoerd met één TarMK-instantie. De TarMK-opslagplaatsen zijn onafhankelijk en moeten gesynchroniseerd blijven.

Het houden van de bewaarplaatsen in synchronisatie wordt voorzien van het feit dat de auteurserver de zelfde inhoud aan elk landbouwbedrijflid publiceert. Zie [Replication](/help/sites-deploying/replication.md) voor meer informatie.

Voor AEM Communities wordt door de gebruiker gegenereerde inhoud (UGC) nooit gerepliceerd. Voor het steunen van UGC op een Farm TarMK, zie [overwegingen voor AEM Communities](#considerations-for-aem-communities).

**Dit is de standaardimplementatie voor publicatieomgevingen.**

![chlimage_1-17](assets/chlimage_1-17.png)

De voordelen:

* Prestaties
* Schaalbaarheid voor leestoegang
* Failover

### Eak-cluster met MongoMK-failover voor hoge beschikbaarheid in één datacenter {#oak-cluster-with-mongomk-failover-for-high-availability-in-a-single-datacenter}

Deze benadering impliceert veelvoudige instanties van het Eak die tot een replica toegang hebben MongoDB binnen één enkel gegevenscentrum, in feite creërend een actief-actieve cluster voor het AEM auteursmilieu. Replica-sets in MongoDB worden gebruikt om hoge beschikbaarheid en redundantie te bieden in het geval van een hardware- of netwerkstoring.

![chlimage_1-18](assets/chlimage_1-18.png)

De voordelen:

* De mogelijkheid om horizontaal te schalen met nieuwe AEM auteur-instanties
* Hoge beschikbaarheid, overtolligheid, en geautomatiseerde failover van gegevenslaag

De nadelen:

* De prestaties kunnen lager zijn dan met TarMK voor sommige scenario&#39;s

### Cluster met MongoMK-failover over meerdere datacenters {#oak-cluster-with-mongomk-failover-across-multiple-datacenters}

Deze benadering impliceert veelvoudige instanties van het Eak die tot een replica toegang hebben MongoDB die over veelvoudige gegevenscentra wordt geplaatst, in feite creërend een actief-actieve cluster voor het AEM auteursmilieu. Met meerdere datacenters biedt de replicatie van MongoDB dezelfde hoge beschikbaarheid en redundantie, maar nu ook de mogelijkheid om een storing in het datacenter te verwerken.

![oakclustermongofailover2datacenters](assets/oakclustermongofailover2datacenters.png)

De voordelen:

* De mogelijkheid om horizontaal te schalen met nieuwe AEM auteur-instanties
* Hoge beschikbaarheid, overtolligheid, en geautomatiseerde failover van gegevenslaag (met inbegrip van gegevenscentrumstroomonderbrekingen)

>[!NOTE]
>
>In het diagram hierboven, worden AEM Server 3 en AEM Server 4 voorgesteld met een inactieve status veronderstellend een netwerklatentie binnen tussen de AEM Servers in Datacenter 2 en de primaire knoop MongoDB in Datacenter 1 die hoger is dan het vereiste gedocumenteerd [hier](/help/sites-deploying/aem-with-mongodb.md#checklists). Als de maximumlatentie compatibel is met de vereisten, bijvoorbeeld door het gebruik van beschikbaarheidszones, dan kunnen de AEM servers in Datacenter 2 ook actief zijn, die tot een actief-actieve AEM cluster over veelvoudige datacenters leiden.

>[!NOTE]
>
>Voor extra informatie over de architecturale concepten MongoDB die in deze sectie worden beschreven, zie [MongoDB Replication](https://docs.mongodb.org/manual/replication/).

## Microkorrels: welke {#microkernels-which-one-to-use} moet worden gebruikt

De basisregel waarmee rekening moet worden gehouden bij het kiezen tussen de twee beschikbare microkorrels is dat TarMK ontworpen is voor prestaties, terwijl MongoMK wordt gebruikt voor schaalbaarheid.

U kunt deze besluitmatrices gebruiken om te bepalen wat het beste type implementatie is dat aan uw vereisten is aangepast.

Adobe adviseert hoogst TarMK om de standaardpersistentietechnologie te zijn die door klanten in alle plaatsingsscenario&#39;s, voor zowel auteur AEM als Publish instanties wordt gebruikt, behalve in de hieronder geschetste gebruiksgevallen.

### Uitzonderingen voor het kiezen van AEM MongoMK in TarMK op Auteurinstanties {#exceptions-for-choosing-aem-mongomk-over-tarmk-on-author-instances}

De primaire reden voor het kiezen van de MongoMK persistence backend over TarMK is de instanties horizontaal te schalen. Dit betekent dat er altijd twee of meer actieve auteur-instanties moeten worden uitgevoerd en dat MongoDB moet worden gebruikt als het opslagsysteem voor persistentie. De noodzaak om meer dan één auteurinstantie in werking te stellen vloeit over het algemeen voort uit het feit dat de cpu en geheugencapaciteit van één enkele server, die alle gezamenlijke auteursactiviteiten steunt, niet meer duurzaam is.

Het is bijna onmogelijk om te voorspellen wat het precieze gelijktijdige model zal zijn nadat een nieuwe site live gaat. Daarom adviseert Adobe u de volgende criteria in overweging te nemen wanneer het evalueren of om MongoMK en twee of meer Actieve knopen van de Auteur te gebruiken:

1. Aantal benoemde gebruikers verbonden in een dag: in de duizenden of meer.
1. Aantal gelijktijdige gebruikers: in honderden of meer.
1. Omvang van de ingenomen activa per dag: in honderdduizenden of meer.
1. Volume van paginabewerkingen per dag: in honderdduizenden of meer (waaronder automatische updates via Multi Site Manager of bijvoorbeeld inname van nieuwsberichten).
1. Volume zoekopdrachten per dag: in tienduizenden of meer.

>[!NOTE]
>
>Tough Day kan worden gebruikt om de prestaties van de toepassing van de klant in de context van de opgestelde hardwareconfiguratie te evalueren. Meer informatie over dit gereedschap is [hier](/help/sites-developing/tough-day.md) beschikbaar.

Een minimumplaatsing met MongoDB zal typisch de volgende topologie impliceren:

* Een MongoDB-replicaset bestaande uit één primair knooppunt, twee secundaire knooppunten met elk van de MongoDB-instanties die in een beschikbaarheidszone met een latentie onder 15 milliseconden op elk knooppunt worden uitgevoerd;
* Een cluster van auteurinstanties met één leaderknoop, één niet-leaderknooppunt en beide actief op elk moment, met elk van de auteurinstanties die in elk van de datacenters worden uitgevoerd, waar de primaire en secundaire MongoDB-instanties worden uitgevoerd.

Daarnaast wordt het ten zeerste aanbevolen de datastore op een gedeeld bestandssysteem of Amazon S3 te configureren, zodat de elementen of binaire bestanden niet in MongoDB worden opgeslagen. Dit zorgt voor optimale prestaties binnen de implementatie.

Een van de extra voordelen van de implementatie van een MongoDB-replicaset met een cluster van twee of meer auteurinstanties is dat er een geautomatiseerd herstelscenario met minimale downtime bestaat in het geval van een auteurinstantie, een MongoDB-replica of een volledige datacenterfout. Niettemin zou de keuze van MongoMK over TarMK niet alleen door het terugwinningsvereiste moeten worden gedreven, aangezien TarMK ook een minimale downtime oplossing met een gecontroleerd failovermechanisme kan verstrekken.

Als de bovengenoemde criteria naar verwachting niet tijdens de eerste achttien maanden van plaatsing zullen worden voldaan, wordt het aangemoedigd om eerst AEM op te stellen gebruikend TarMK, dan uw configuratie op een recentere datum opnieuw te evalueren wanneer de bovengenoemde criteria van toepassing zijn, en definitief te bepalen of om op TarMK te blijven of aan MongoMK te migreren.

### Uitzonderingen voor het kiezen van AEM MongoMK in TarMK bij publicatie-instanties {#exceptions-for-choosing-aem-mongomk-over-tarmk-on-publish-instances}

Het wordt afgeraden MongoMK te implementeren voor publicatie-instanties. De publicatielaag van de plaatsing wordt bijna altijd opgesteld als landbouwbedrijf van volledig onafhankelijke publiceer instanties die TarMK in werking stellen, die in synchronisatie door inhoud van de auteursinstanties te herhalen worden gehouden. Deze &quot;gedeelde niets&quot;architectuur, behoorlijk aan de publiceer instanties, staat de plaatsing van toe publiceert rij om horizontaal op een lineaire manier te schrapen. De landbouwbedrijftopologie verstrekt ook het voordeel om het even welke update of verbetering toe te passen om instanties op een voortschrijdende basis te publiceren, zodat om het even welke verandering in publiceer rij geen onderbreking zal vereisen.

Dit is niet van toepassing op AEM Communities die MongoMK-clusters gebruikt op de publicatielijst als er meerdere uitgevers zijn. Als u JSRP kiest (zie [Community Content Storage](/help/communities/working-with-srp.md)), is een MongoMK-cluster geschikt, net als elke andere cluster aan de publiczijde, ongeacht de gekozen MK, zoals MongoDB of RDB.

### Vereisten en Recommendations bij de implementatie van AEM met MongoMK {#prerequisites-and-recommendations-when-deploying-aem-with-mongomk}

Een reeks eerste vereisten en aanbevelingen is beschikbaar als u een plaatsing MongoMK voor AEM overweegt:

**Verplichte voorwaarden voor MongoDB-implementaties:**

1. De mongoDB-implementatiearchitectuur en -grootte moeten deel uitmaken van de projectimplementatie met hulp van Adobe Consulting- of MongoDB-architecten die vertrouwd zijn met AEM.
1. De deskundigheid MongoDB moet binnen de partner of klantenteam aanwezig zijn om vertrouwen in het kunnen een bestaande of nieuwe milieu te kunnen handhaven MongoDB;
1. U kunt ervoor kiezen om de commerciële of open-sourceversie van MongoDB te implementeren (AEM ondersteunt beide), maar u moet rechtstreeks een MongoDB-onderhouds- en ondersteuningscontract aanschaffen bij MongoDB Inc;
1. De architecturen en infrastructuren van de AEM en MongoDB moeten goed worden gedefinieerd en gevalideerd door een architecte van de Adobe AEM.
1. U moet het supportmodel voor AEM implementaties met MongoDB controleren.

**Sterke aanbevelingen voor MongoDB-implementaties:**

* Raadpleeg het MongoDB voor Adobe Experience Manager [artikel](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager);
* Controleer de MongoDB-productie [checklist](https://docs.mongodb.org/manual/administration/production-checklist/);
* Voeg een certificeringsklasse toe op MongoDB die online [hier](https://university.mongodb.com/) beschikbaar is.

>[!NOTE]
>
>Voor alle aanvullende vragen over deze richtlijnen, voorwaarden en aanbevelingen kunt u contact opnemen met [Adobe Customer Care](https://helpx.adobe.com/marketing-cloud/contact-support.html).

### Overwegingen voor AEM Communities {#considerations-for-aem-communities}

Voor sites die [AEM Communities](/help/communities/overview.md) willen implementeren, wordt aanbevolen [een implementatie te kiezen](/help/communities/working-with-srp.md#characteristicsofstorageoptions) die is geoptimaliseerd voor de verwerking van UGC die is geplaatst door leden van de gemeenschap in de publicatieomgeving.

Door [common store](/help/communities/working-with-srp.md) te gebruiken, te hoeven UGC niet tussen auteur en andere publicatieinstanties worden herhaald om een verenigbare mening van UGC te verkrijgen.

Hieronder vindt u een reeks beslissingsmatrixen die u kunnen helpen bij het kiezen van het beste type persistentie voor uw implementatie:

#### Het implementatietype kiezen voor auteurinstanties {#choosing-the-deployment-type-for-author-instances}

![chlimage_1-19](assets/chlimage_1-19.png)

#### Het implementatietype kiezen voor publicatie-instanties {#choosing-the-deployment-type-for-publish-instances}

![chlimage_1-20](assets/chlimage_1-20.png)

>[!NOTE]
>
>MongoDB is software van derden en is niet opgenomen in het AEM licentiepakket. Zie de pagina [MongoDB-licentiebeleid](https://www.mongodb.org/about/licensing/) voor meer informatie.
>
>Om optimaal gebruik te kunnen maken van uw AEM, raadt Adobe u aan een licentie te verlenen voor de MongoDB Enterprise-versie, zodat u kunt profiteren van professionele ondersteuning.
>
>De licentie bevat een standaard replicaset, die bestaat uit één primaire en twee secundaire instanties die kunnen worden gebruikt voor de auteur of de publicatieimplementaties.
>
>Als u zowel de auteur als de publicatie op MongoDB wilt uitvoeren, moet u twee aparte licenties aanschaffen.
>
>Zie de [MongoDB voor Adobe Experience Manager-pagina](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager) voor meer informatie.

