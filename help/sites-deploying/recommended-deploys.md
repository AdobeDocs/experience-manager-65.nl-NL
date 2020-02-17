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

---


# Aanbevolen implementaties{#recommended-deployments}

>[!NOTE]
>
>Deze pagina verwijst naar geadviseerde topologieën voor AEM. Raadpleeg de documentatie [van de API voor detectie van](https://sling.apache.org/documentation/bundles/discovery-api-and-impl.html)Apache Sling voor meer informatie over clusteringmogelijkheden en hoe u deze kunt configureren.

MicroKernels fungeren als persistentiemanagers vanaf AEM 6.2.Het kiezen van één om uw behoeften te passen hangt van het doel van uw instantie en het plaatsingstype af u overweegt.

De volgende voorbeelden moeten een indicatie zijn van wat hun geadviseerde gebruik in de gemeenschappelijkste montages AEM zijn.

## Implementatiescenario&#39;s {#deployment-scenarios}

### Single TarMK-instantie {#single-tarmk-instance}

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
>De plaatsing van de Reserve van de Koude in dit voorbeeld TarMK vereist dat zowel de primaire als reserve instanties afzonderlijk worden vergunning gegeven, aangezien er constante replicatie aan de failoverserver is. Raadpleeg de Algemene licentievoorwaarden van [Adobe voor meer informatie over licenties](https://www.adobe.com/legal/terms/enterprise-licensing.html).

### TarMK Farm {#tarmk-farm}

Meerdere Oak-instanties worden elk uitgevoerd met één TarMK-instantie. De TarMK-opslagplaatsen zijn onafhankelijk en moeten gesynchroniseerd blijven.

Het houden van de bewaarplaatsen in synchronisatie wordt voorzien van het feit dat de auteurserver de zelfde inhoud aan elk landbouwbedrijflid publiceert. For more information, see [Replication](/help/sites-deploying/replication.md).

Voor AEM-gemeenschappen wordt door de gebruiker gegenereerde inhoud (UGC) nooit gerepliceerd. Zie [overwegingen voor AEM-gemeenschappen](#considerations-for-aem-communities)voor ondersteuning van UGC op een TarMK-farm.

**Dit is de standaardimplementatie voor publicatieomgevingen.**

![chlimage_1-17](assets/chlimage_1-17.png)

De voordelen:

* Prestaties
* Schaalbaarheid voor leestoegang
* Failover

### Eak-cluster met MongoMK-failover voor hoge beschikbaarheid in één datacenter {#oak-cluster-with-mongomk-failover-for-high-availability-in-a-single-datacenter}

Deze aanpak impliceert dat meerdere Oak-instanties toegang hebben tot een MongoDB-replica die binnen één datacenter is ingesteld. In feite wordt een actief-actief cluster voor de AEM-auteuromgeving gemaakt. Replica-sets in MongoDB worden gebruikt om hoge beschikbaarheid en redundantie te bieden in het geval van een hardware- of netwerkstoring.

![chlimage_1-18](assets/chlimage_1-18.png)

De voordelen:

* De mogelijkheid om horizontaal te schalen met nieuwe AEM-auteur-instanties
* Hoge beschikbaarheid, overtolligheid, en geautomatiseerde failover van gegevenslaag

De nadelen:

* De prestaties kunnen lager zijn dan met TarMK voor sommige scenario&#39;s

### Eak-cluster met MongoMK-failover over meerdere datacenters {#oak-cluster-with-mongomk-failover-across-multiple-datacenters}

Deze aanpak impliceert dat meerdere Oak-instanties toegang hebben tot een MongoDB-replica die in meerdere datacenters is ingesteld. In feite wordt een actief-actief cluster voor de AEM-auteuromgeving gemaakt. Met meerdere datacenters biedt de replicatie van MongoDB dezelfde hoge beschikbaarheid en redundantie, maar nu ook de mogelijkheid om een storing in het datacenter te verwerken.

![oakclustermongofailover2datacenters](assets/oakclustermongofailover2datacenters.png)

De voordelen:

* De mogelijkheid om horizontaal te schalen met nieuwe AEM-auteur-instanties
* Hoge beschikbaarheid, overtolligheid, en geautomatiseerde failover van gegevenslaag (met inbegrip van gegevenscentrumstroomonderbrekingen)

>[!NOTE]
>
>In het diagram hierboven, worden Server 3 AEM en Server 4 voorgesteld van AEM met een inactieve status veronderstellend een netwerklatentie binnen tussen de Servers AEM in Centrum 2 van Gegevens en het primaire knooppunt MongoDB in Centrum 1 van Gegevens die hoger is dan het vereiste [hier](/help/sites-deploying/aem-with-mongodb.md#checklists)wordt gedocumenteerd. Als de maximale latentie compatibel is met de vereisten, bijvoorbeeld door het gebruik van beschikbaarheidszones, kunnen de AEM-servers in datacenter 2 ook actief zijn, waardoor een actief-actieve AEM-cluster in meerdere datacenters ontstaat.

>[!NOTE]
>
>Voor extra informatie over de architecturale concepten MongoDB die in deze sectie worden beschreven, zie [Replicatie](https://docs.mongodb.org/manual/replication/)MongoDB.

## Microkorrels: welke {#microkernels-which-one-to-use}

De basisregel waarmee rekening moet worden gehouden bij het kiezen tussen de twee beschikbare microkorrels is dat TarMK ontworpen is voor prestaties, terwijl MongoMK wordt gebruikt voor schaalbaarheid.

U kunt deze besluitmatrices gebruiken om te bepalen wat het beste type implementatie is dat aan uw vereisten is aangepast.

Adobe raadt TarMK ten zeerste aan de standaardpersistentietechnologie te zijn die door klanten wordt gebruikt in alle implementatiescenario&#39;s, voor zowel de AEM-auteur als de publicatie, behalve in de hieronder beschreven gebruiksgevallen.

### Uitzonderingen voor het kiezen van AEM MongoMK in TarMK op Auteurinstanties {#exceptions-for-choosing-aem-mongomk-over-tarmk-on-author-instances}

De primaire reden voor het kiezen van de MongoMK persistence backend over TarMK is de instanties horizontaal te schalen. Dit betekent dat er altijd twee of meer actieve auteur-instanties moeten worden uitgevoerd en dat MongoDB moet worden gebruikt als het opslagsysteem voor persistentie. De noodzaak om meer dan één auteurinstantie in werking te stellen vloeit over het algemeen voort uit het feit dat de cpu en geheugencapaciteit van één enkele server, die alle gezamenlijke auteursactiviteiten steunt, niet meer duurzaam is.

Het is bijna onmogelijk om te voorspellen wat het precieze gelijktijdige model zal zijn nadat een nieuwe site live gaat. Daarom raadt Adobe u aan de volgende criteria in overweging te nemen wanneer u beoordeelt of MongoMK en twee of meer actieve knooppunten van de Auteur moeten worden gebruikt:

1. Aantal benoemde gebruikers verbonden in een dag: in de duizenden of meer.
1. Aantal gelijktijdige gebruikers: in honderden of meer.
1. Omvang van de ingenomen activa per dag: in honderdduizenden of meer.
1. Volume van paginabewerkingen per dag: in honderdduizenden of meer (waaronder automatische updates via Multi Site Manager of bijvoorbeeld inname van nieuwsberichten).
1. Volume zoekopdrachten per dag: in tienduizenden of meer.

>[!NOTE]
>
>Tough Day kan worden gebruikt om de prestaties van de toepassing van de klant in de context van de opgestelde hardwareconfiguratie te evalueren. Meer informatie over dit gereedschap is [hier](/help/sites-developing/tough-day.md)beschikbaar.

Een minimumplaatsing met MongoDB zal typisch de volgende topologie impliceren:

* Een MongoDB-replicaset bestaande uit één primair knooppunt, twee secundaire knooppunten met elk van de MongoDB-instanties die in een beschikbaarheidszone met een latentie onder 15 milliseconden op elk knooppunt worden uitgevoerd;
* Een cluster van auteurinstanties met één leaderknoop, één niet-leaderknooppunt en beide actief op elk moment, met elk van de auteurinstanties die in elk van de datacenters worden uitgevoerd, waar de primaire en secundaire MongoDB-instanties worden uitgevoerd.

Daarnaast wordt het ten zeerste aanbevolen de datastore op een gedeeld bestandssysteem of Amazon S3 te configureren, zodat de elementen of binaire bestanden niet in MongoDB worden opgeslagen. Dit zorgt voor optimale prestaties binnen de implementatie.

Een van de extra voordelen van de implementatie van een MongoDB-replicaset met een cluster van twee of meer auteurinstanties is dat er een geautomatiseerd herstelscenario met minimale downtime bestaat in het geval van een auteurinstantie, een MongoDB-replica of een volledige datacenterfout. Niettemin zou de keuze van MongoMK over TarMK niet alleen door het terugwinningsvereiste moeten worden gedreven, aangezien TarMK ook een minimale downtime oplossing met een gecontroleerd failovermechanisme kan verstrekken.

Als de bovengenoemde criteria naar verwachting niet tijdens de eerste achttien maanden van plaatsing zullen worden vervuld, wordt het aangemoedigd eerst AEM op te stellen gebruikend TarMK, dan uw configuratie op een recentere datum opnieuw te evalueren wanneer de bovengenoemde criteria van toepassing zijn, en definitief te bepalen of om op TarMK te blijven of aan MongoMK te migreren.

### Uitzonderingen voor het kiezen van AEM MongoMK in TarMK bij publicatie-instanties {#exceptions-for-choosing-aem-mongomk-over-tarmk-on-publish-instances}

Het wordt afgeraden MongoMK te implementeren voor publicatie-instanties. De publicatielaag van de plaatsing wordt bijna altijd opgesteld als landbouwbedrijf van volledig onafhankelijke publiceer instanties die TarMK in werking stellen, die in synchronisatie door inhoud van de auteursinstanties te herhalen worden gehouden. Deze &quot;gedeelde niets&quot;architectuur, behoorlijk aan de publiceer instanties, staat de plaatsing van toe publiceert rij om horizontaal op een lineaire manier te schrapen. De landbouwbedrijftopologie verstrekt ook het voordeel om het even welke update of verbetering toe te passen om instanties op een voortschrijdende basis te publiceren, zodat om het even welke verandering in publiceer rij geen onderbreking zal vereisen.

Dit is niet van toepassing op AEM-gemeenschappen die MongoMK-clusters gebruiken op de publicatielaag wanneer er meerdere uitgevers zijn. Als u JSRP (zie [Community Content Storage](/help/communities/working-with-srp.md)) kiest, is een MongoMK-cluster geschikt, net als elke andere cluster aan de publiczijde, ongeacht de gekozen MK, zoals MongoDB of RDB.

### Vereisten en aanbevelingen bij de implementatie van AEM met MongoMK {#prerequisites-and-recommendations-when-deploying-aem-with-mongomk}

Een reeks eerste vereisten en aanbevelingen is beschikbaar als u een plaatsing MongoMK voor AEM overweegt:

**Verplichte voorwaarden voor MongoDB-implementaties:**

1. De mongoDB-implementatiearchitectuur en -grootte moeten deel uitmaken van de projectimplementatie met de hulp van Adobe Consulting- of MongoDB-architecten die bekend zijn met AEM.
1. De deskundigheid MongoDB moet binnen de partner of klantenteam aanwezig zijn om vertrouwen in het kunnen een bestaande of nieuwe milieu te kunnen handhaven MongoDB;
1. U kunt ervoor kiezen om de commerciële of open-sourceversie van MongoDB te implementeren (AEM ondersteunt beide), maar moet een MongoDB-onderhouds- en ondersteuningscontract rechtstreeks van MongoDB Inc aanschaffen.
1. AEM- en MongoDB-architecturen en -infrastructuren moeten in hun geheel goed zijn gedefinieerd en gevalideerd door een Adobe AEM-architect;
1. U moet het supportmodel voor AEM-implementaties met MongoDB controleren.

**Sterke aanbevelingen voor MongoDB-implementaties:**

* Raadpleeg het [artikel](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager)van MongoDB for Adobe Experience Manager.
* De MongoDB- [productiecontrolelijst](https://docs.mongodb.org/manual/administration/production-checklist/)controleren;
* Voeg een certificeringsklasse toe op MongoDB die [hier](https://university.mongodb.com/)online beschikbaar is.

>[!NOTE]
>
>Neem voor alle aanvullende vragen over deze richtlijnen, voorwaarden en aanbevelingen contact op met de [klantenservice](https://helpx.adobe.com/marketing-cloud/contact-support.html)van Adobe.

### Overwegingen voor AEM-gemeenschappen {#considerations-for-aem-communities}

Voor plaatsen die van plan zijn om [AEM Gemeenschappen](/help/communities/overview.md)op te stellen, wordt het geadviseerd om een plaatsing [te](/help/communities/working-with-srp.md#characteristicsofstorageoptions) kiezen die voor de behandeling van UGC wordt geoptimaliseerd die door communautaire leden van het publicatiemilieu wordt gepost.

Door een [gemeenschappelijke opslag](/help/communities/working-with-srp.md)te gebruiken, te hoeven UGC niet tussen auteur en andere te herhalen publiceer instanties om een verenigbare mening van UGC te verkrijgen.

Hieronder vindt u een reeks beslissingsmatrixen die u kunnen helpen bij het kiezen van het beste type persistentie voor uw implementatie:

#### Het implementatietype kiezen voor auteur-instanties {#choosing-the-deployment-type-for-author-instances}

![chlimage_1-19](assets/chlimage_1-19.png)

#### Het implementatietype kiezen voor publicatie-instanties {#choosing-the-deployment-type-for-publish-instances}

![chlimage_1-20](assets/chlimage_1-20.png)

>[!NOTE]
>
>MongoDB is software van derden en is niet opgenomen in het AEM-licentiepakket. Zie de pagina [MongoDB-licentiebeleid](https://www.mongodb.org/about/licensing/) voor meer informatie.
>
>Adobe raadt u aan een licentie voor de MongoDB Enterprise-versie aan te schaffen om optimaal gebruik te kunnen maken van uw AEM-implementatie.
>
>De licentie bevat een standaard replicaset, die bestaat uit één primaire en twee secundaire instanties die kunnen worden gebruikt voor de auteur of de publicatieimplementaties.
>
>Als u zowel de auteur als de publicatie op MongoDB wilt uitvoeren, moet u twee aparte licenties aanschaffen.
>
>Zie de pagina [](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager)MongoDB voor Adobe Experience Manager voor meer informatie.

