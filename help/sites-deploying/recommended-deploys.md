---
title: Aanbevolen implementaties
description: Dit artikel beschrijft de geadviseerde topologieën voor AEM.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
docset: aem65
exl-id: baec7fc8-d48c-4bc6-b12b-4bf4eff695ea
solution: Experience Manager, Experience Manager Sites
feature: Deploying
role: Admin
source-git-commit: f30decf0e32a520dcda04b89c5c1f5b67ab6e028
workflow-type: tm+mt
source-wordcount: '1756'
ht-degree: 0%

---

# Aanbevolen implementaties{#recommended-deployments}

>[!NOTE]
>
>Deze pagina verwijst naar geadviseerde topologieën voor AEM. Voor meer informatie bij het groeperen van mogelijkheden en hoe te om hen te vormen, zie de [&#x200B; Apache Sling API documentatie van de Ontdekking &#x200B;](https://sling.apache.org/documentation/bundles/discovery-api-and-impl.html).

MicroKernels fungeren vanaf AEM 6.2 als persistentiemanagers. Het kiezen van één om uw behoeften te passen hangt van het doel van uw instantie en het plaatsingstype af u overweegt.

De volgende voorbeelden moeten een indicatie zijn van wat hun aanbevolen gebruik in de meest gebruikelijke AEM is.

## Implementatiescenario&#39;s {#deployment-scenarios}

### Single TarMK-instantie {#single-tarmk-instance}

In dit scenario, loopt één enkele instantie TarMK op één enkele server.

**dit is de standaardplaatsing voor auteursinstanties.**

![&#x200B; chlimage_1-15 &#x200B;](assets/chlimage_1-15.png)

De voordelen:

* eenvoudig
* Eenvoudig onderhoud
* Goede prestaties

De nadelen:

* Niet schaalbaar buiten de grenzen van de servercapaciteit
* Geen failover-capaciteit

### TarMK Cold Standby {#tarmk-cold-standby}

Eén TarMK-instantie fungeert als de primaire instantie. De opslagplaats van de primaire opslagplaats wordt gerepliceerd naar een stand-by failover-systeem.

Het koude reservemechanisme kan ook als steun worden gebruikt omdat de volledige bewaarplaats constant aan de failoverserver wordt herhaald. De failoverserver loopt op koude reservewijze, wat betekent dat slechts HttpReceiver van de instantie loopt.

![&#x200B; chlimage_1-16 &#x200B;](assets/chlimage_1-16.png)

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
>Voor meer informatie over hoe te om AEM met TarMK te vormen Koude Reserve, zie [&#x200B; dit &#x200B;](/help/sites-deploying/tarmk-cold-standby.md) artikel.

>[!NOTE]
>
>De plaatsing van de Reserve van de Koude in dit voorbeeld TarMK vereist dat zowel de primaire als reserve instanties afzonderlijk worden vergunning gegeven, aangezien er constante replicatie aan de failoverserver is. Voor meer informatie over vergunning verlenen, raadpleeg de [&#x200B; Algemene het Vergunningstermijnen van de Adobe &#x200B;](https://www.adobe.com/legal/terms/enterprise-licensing.html).

### TarMK Farm {#tarmk-farm}

Meerdere Oak-instanties voeren elk uit met één TarMK-instantie. De TarMK-opslagplaatsen zijn onafhankelijk en moeten gesynchroniseerd blijven.

Het houden van de bewaarplaatsen in synchronisatie wordt voorzien van het feit dat de auteurserver de zelfde inhoud aan elk landbouwbedrijflid publiceert. Voor meer informatie, zie [&#x200B; Replicatie &#x200B;](/help/sites-deploying/replication.md).

Voor AEM Communities wordt door de gebruiker gegenereerde inhoud (UGC) nooit gerepliceerd. Voor het steunen van UGC op een Farm TarMK, zie [&#x200B; overwegingen voor AEM Communities &#x200B;](#considerations-for-aem-communities).

**dit is de standaardplaatsing voor publiceer milieu&#39;s.**

![&#x200B; chlimage_1-17 &#x200B;](assets/chlimage_1-17.png)

De voordelen:

* Prestaties
* Schaalbaarheid voor leestoegang
* Failover

### Oak Cluster met MongoMK-failover voor hoge beschikbaarheid in één datacenter {#oak-cluster-with-mongomk-failover-for-high-availability-in-a-single-datacenter}

Deze aanpak impliceert dat meerdere Oak-instanties toegang hebben tot een MongoDB-replica die is ingesteld binnen één datacenter. In feite wordt er een actief-actief cluster voor de AEM auteuromgeving gemaakt. Replicasets in MongoDB worden gebruikt om hoge beschikbaarheid en redundantie te bieden in het geval van een hardware- of netwerkstoring.

![&#x200B; chlimage_1-18 &#x200B;](assets/chlimage_1-18.png)

De voordelen:

* De mogelijkheid om horizontaal te schalen met nieuwe AEM auteur-instanties
* Hoge beschikbaarheid, overtolligheid, en geautomatiseerde failover van gegevenslaag

De nadelen:

* De prestaties kunnen lager zijn dan met TarMK voor sommige scenario&#39;s

### Oak-cluster met MongoMK-failover over meerdere datacenters {#oak-cluster-with-mongomk-failover-across-multiple-datacenters}

Deze aanpak impliceert dat meerdere Oak-instanties toegang hebben tot een MongoDB-replica die in meerdere datacenters is ingesteld. In feite wordt er een actief-actief cluster voor de AEM auteuromgeving gemaakt. Met meerdere datacenters biedt de replicatie van MongoDB dezelfde hoge beschikbaarheid en redundantie, maar nu ook de mogelijkheid om een storing in het datacenter te verwerken.

![&#x200B; oakclustermongofailover2datacenters &#x200B;](assets/oakclustermongofailover2datacenters.png)

De voordelen:

* De mogelijkheid om horizontaal te schalen met nieuwe AEM auteur-instanties
* Hoge beschikbaarheid, overtolligheid, en geautomatiseerde failover van gegevenslaag (met inbegrip van gegevenscentrumstroomonderbrekingen)

>[!NOTE]
>
>In het diagram hierboven, worden AEM Server 3 en AEM Server 4 voorgesteld met een inactieve status die een netwerklatentie tussen de AEM Servers in Centrum 2 van Gegevens en het primaire knooppunt MongoDB in Centrum 1 veronderstelt die hoger is dan het vereiste dat onder [&#x200B; Adobe Experience Manager met MongoDB - Controlklists &#x200B;](/help/sites-deploying/aem-with-mongodb.md#checklists) wordt gedocumenteerd. Als de maximumlatentie compatibel is met de vereisten, bijvoorbeeld door het gebruik van beschikbaarheidszones, dan kunnen de AEM servers in Datacenter 2 ook actief zijn, die tot een actief-actieve AEM cluster over veelvoudige datacenters leiden.

>[!NOTE]
>
>Voor extra informatie over de architecturale concepten MongoDB die in deze sectie worden beschreven, zie {de Replicatie van 0} MongoDB [&#128279;](https://docs.mongodb.org/manual/replication/).

## Microkorrels: één voor gebruik {#microkernels-which-one-to-use}

De basisregel waarmee rekening moet worden gehouden bij het kiezen tussen de twee beschikbare microkorrels is dat TarMK ontworpen is voor prestaties, terwijl MongoMK wordt gebruikt voor schaalbaarheid.

U kunt deze besluitmatrices gebruiken om te bepalen wat het beste type implementatie is dat aan uw vereisten is aangepast.

De Adobe adviseert hoogst TarMK om de standaardpersistentietechnologie te zijn die door klanten in alle plaatsingsscenario&#39;s, voor zowel de AEM Auteur als de instanties van Publish wordt gebruikt, behalve in de hieronder geschetste gebruiksgevallen.

### Uitzonderingen voor het kiezen van AEM MongoMK in TarMK op authorinstanties {#exceptions-for-choosing-aem-mongomk-over-tarmk-on-author-instances}

De primaire reden voor het kiezen van de MongoMK persistence backend over TarMK is de instanties horizontaal te schalen. Dit betekent dat er altijd twee of meer actieve auteur-instanties moeten worden uitgevoerd en dat MongoDB moet worden gebruikt als het opslagsysteem voor persistentie. De noodzaak om meer dan één auteurinstantie in werking te stellen vloeit over het algemeen voort uit het feit dat de cpu en geheugencapaciteit van één enkele server, die alle gezamenlijke auteursactiviteiten steunt, niet meer duurzaam is.

Het is bijna onmogelijk om te voorspellen wat het precieze gelijktijdige model zal zijn nadat een nieuwe site live gaat. Daarom adviseert de Adobe u de volgende criteria in overweging te nemen wanneer het evalueren of om MongoMK en twee of meer Actieve knopen van de Auteur te gebruiken:

1. Aantal benoemde gebruikers verbonden in een dag: in de duizenden of meer.
1. Aantal gelijktijdige gebruikers: in honderden of meer.
1. Hoeveelheid ingenomen activa per dag: in honderdduizenden of meer.
1. Volume van paginabewerkingen per dag: in honderdduizenden of meer (inclusief automatische updates via Meerdere Sitebeheer of inname van nieuwsberichten).
1. Aantal zoekopdrachten per dag: in tienduizenden of meer.

>[!NOTE]
>
>[&#x200B; Stevige Dag &#x200B;](/help/sites-developing/tough-day.md) kan worden gebruikt om de prestaties van de toepassing van de klant in de context van de opgestelde hardwareconfiguratie te evalueren.

Een minimumplaatsing met MongoDB zal typisch de volgende topologie impliceren:

* Een MongoDB-replicaset bestaande uit één primair knooppunt, twee secundaire knooppunten met elk van de MongoDB-instanties die in een beschikbaarheidszone met een latentie onder 15 milliseconden op elk knooppunt worden uitgevoerd;
* Een cluster van auteurinstanties met één leaderknoop, één niet-leaderknooppunt en beide actief op elk moment, met elk van de auteurinstanties die in elk van de datacenters worden uitgevoerd, waar de primaire en secundaire MongoDB-instanties worden uitgevoerd.

Daarnaast wordt het ten zeerste aanbevolen de datastore op een gedeeld bestandssysteem of Amazon S3 te configureren, zodat de elementen of binaire bestanden niet in MongoDB worden opgeslagen. Dit zorgt voor optimale prestaties binnen de implementatie.

Een van de extra voordelen van de implementatie van een MongoDB-replicaset met een cluster van twee of meer auteurinstanties is dat er een geautomatiseerd herstelscenario met minimale downtime bestaat als er auteurinstanties, MongoDB-replica of een volledige datacenterfout zijn. Niettemin zou de keuze van MongoMK over TarMK niet alleen door het terugwinningsvereiste moeten worden gedreven, aangezien TarMK ook een minimale downtime oplossing met een gecontroleerd failovermechanisme kan verstrekken.

Als de bovenstaande criteria naar verwachting niet tijdens de eerste 18 maanden van plaatsing zullen worden vervuld, wordt het aangemoedigd eerst AEM op te stellen gebruikend TarMK, dan uw configuratie op een recentere datum opnieuw te evalueren wanneer de bovengenoemde criteria van toepassing zijn, en definitief te bepalen of om op TarMK te blijven of aan MongoMK te migreren.

### Uitzonderingen voor het kiezen van AEM MongoMK in plaats van TarMK in Publish-instanties {#exceptions-for-choosing-aem-mongomk-over-tarmk-on-publish-instances}

Het wordt afgeraden MongoMK te implementeren voor publicatie-instanties. De publicatielaag van de plaatsing wordt bijna altijd opgesteld als landbouwbedrijf van volledig onafhankelijke publiceer instanties die TarMK in werking stellen, die in synchronisatie door inhoud van de auteursinstanties te herhalen worden gehouden. Deze &quot;gedeelde niets&quot;architectuur, behoorlijk aan de publiceer instanties, staat de plaatsing van toe publiceert rij om horizontaal op een lineaire manier te schrapen. De landbouwbedrijftopologie verstrekt ook het voordeel om het even welke update of verbetering toe te passen om instanties op een voortschrijdende basis te publiceren, zodat om het even welke verandering in publiceer rij geen onderbreking zal vereisen.

Dit is niet van toepassing op AEM Communities die MongoMK-clusters gebruikt op de publicatielijst als er meerdere uitgevers zijn. Als het kiezen van JSRP (zie [&#x200B; Communautaire Opslag van de Inhoud &#x200B;](/help/communities/working-with-srp.md)), dan zou een cluster MongoMK aangewezen zijn, zoals om het even welke te publiceren zijcluster ongeacht MK gekozen, zoals MongoDB of RDB.

### Vereisten en Recommendations bij de implementatie van AEM met MongoMK {#prerequisites-and-recommendations-when-deploying-aem-with-mongomk}

Een reeks eerste vereisten en aanbevelingen is beschikbaar als u een plaatsing MongoMK voor AEM overweegt:

**Verplichte eerste vereisten voor plaatsingen MongoDB:**

1. De mongoDB-implementatiearchitectuur en -grootte moeten deel uitmaken van de projectimplementatie met hulp van Adobe Consulting- of MongoDB-architecten die vertrouwd zijn met AEM;
1. De deskundigheid MongoDB moet binnen de partner of het klantenteam aanwezig zijn om vertrouwen in het kunnen een bestaande of nieuwe milieu te kunnen handhaven MongoDB;
1. U kunt ervoor kiezen om de commerciële of open-sourceversie van MongoDB te implementeren (AEM ondersteunt beide), maar u moet rechtstreeks een MongoDB-onderhouds- en ondersteuningscontract aanschaffen bij MongoDB Inc;
1. De algemene AEM en MongoDB-architecturen en -infrastructuren moeten duidelijk gedefinieerd en gevalideerd worden door een Adobe AEM architect;
1. Controleer het supportmodel voor AEM implementaties die MongoDB bevatten.

**Sterke aanbevelingen voor plaatsingen MongoDB:**

* Raadpleeg het [&#x200B; Overzicht van de Plaatsing MongoDB voor Adobe Experience Manager &#x200B;](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager);
* Herzie [&#x200B; Checklist van de Verrichtingen MongoDB &#x200B;](https://docs.mongodb.org/manual/administration/production-checklist/);
* Woon a [&#x200B; certificatieklasse op MongoDB - beschikbaar online &#x200B;](https://university.mongodb.com/) bij.

>[!NOTE]
>
>Voor alle extra vragen over deze richtlijnen, eerste vereisten, en aanbevelingen contacteren {de Zorg van de Klant van de Adobe 0} [&#128279;](https://helpx.adobe.com/nl/marketing-cloud/contact-support.html).

### Overwegingen voor AEM Communities {#considerations-for-aem-communities}

Voor plaatsen die van plan zijn om [&#x200B; AEM Communities &#x200B;](/help/communities/overview.md) op te stellen, wordt het geadviseerd [&#x200B; een plaatsing &#x200B;](/help/communities/working-with-srp.md#characteristicsofstorageoptions) te kiezen die voor behandeling van UGC door communautaire leden van het publicatiemilieu wordt gepost.

Door a [&#x200B; gemeenschappelijke opslag &#x200B;](/help/communities/working-with-srp.md) te gebruiken, te hoeven UGC niet tussen auteur worden herhaald en andere publiceer instanties om een verenigbare mening van UGC te verkrijgen.

Hieronder vindt u een reeks beslissingsmatrixen die u kunnen helpen bij het kiezen van het beste type persistentie voor uw implementatie:

#### Het implementatietype kiezen voor auteur-instanties {#choosing-the-deployment-type-for-author-instances}

![&#x200B; chlimage_1-19 &#x200B;](assets/chlimage_1-19.png)

#### Het implementatietype kiezen voor publicatie-instanties {#choosing-the-deployment-type-for-publish-instances}

![&#x200B; chlimage_1-20 &#x200B;](assets/chlimage_1-20.png)

>[!NOTE]
>
>MongoDB is software van derden en is niet opgenomen in het AEM licentiepakket. Voor meer informatie zie [&#x200B; MongoDB het verlenen van vergunningen beleid &#x200B;](https://www.mongodb.org/about/licensing/) pagina.
>
>Om optimaal gebruik te kunnen maken van uw AEM, raadt Adobe u aan een licentie te verlenen voor de MongoDB Enterprise-versie, zodat u kunt profiteren van professionele ondersteuning.
>
>De licentie bevat een standaard replicaset, die bestaat uit één primaire en twee secundaire instanties die kunnen worden gebruikt voor de auteur of de publicatieimplementaties.
>
>Als u zowel de auteur als de publicatie op MongoDB wilt uitvoeren, moet u twee aparte licenties aanschaffen.
>
>Voor meer informatie, zie [&#x200B; MongoDB voor de pagina van Adobe Experience Manager &#x200B;](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager).
