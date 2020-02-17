---
title: Richtlijnen voor prestaties
seo-title: Richtlijnen voor prestaties
description: Dit artikel bevat algemene richtlijnen voor het optimaliseren van de prestaties van uw AEM-implementatie.
seo-description: Dit artikel bevat algemene richtlijnen voor het optimaliseren van de prestaties van uw AEM-implementatie.
uuid: 38cf8044-9ff9-48df-a843-43f74b0c0133
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: configuring
discoiquuid: 9ccbc39e-aea7-455e-8639-9193abc1552f
translation-type: tm+mt
source-git-commit: a678716e2c0520891e4228bc49b075f070ea45b7

---


# Richtlijnen voor prestaties{#performance-guidelines}

Deze pagina biedt algemene richtlijnen voor het optimaliseren van de prestaties van uw AEM-implementatie. Als u nog niet eerder met AEM werkt, moet u de volgende pagina&#39;s doorlopen voordat u de prestatierichtlijnen gaat lezen:

* [Basisconcepten van AEM](/help/sites-deploying/deploy.md#basic-concepts)
* [Overzicht van opslag in AEM](/help/sites-deploying/storage-elements-in-aem-6.md#overview-of-storage-in-aem)
* [Aanbevolen implementaties](/help/sites-deploying/recommended-deploys.md)
* [Technische vereisten](/help/sites-deploying/technical-requirements.md)

Hieronder ziet u de implementatieopties die beschikbaar zijn voor AEM (schuiven om alle opties weer te geven):

<table>
 <tbody>
  <tr>
   <td><p><strong>AEM</strong></p> <p><strong>Product</strong></p> </td>
   <td><p><strong>Topologie</strong></p> </td>
   <td><p><strong>Besturingssysteem</strong></p> </td>
   <td><p><strong>Toepassingsserver</strong></p> </td>
   <td><p><strong>JRE</strong></p> </td>
   <td><p><strong>Beveiliging</strong></p> </td>
   <td><p><strong>Micro Kernel</strong></p> </td>
   <td><p><strong>Datastore</strong></p> </td>
   <td><p><strong>Indexeren</strong></p> </td>
   <td><p><strong>Webserver</strong></p> </td>
   <td><p><strong>Browser</strong></p> </td>
   <td><p><strong>Marketing Cloud</strong></p> </td>
  </tr>
  <tr>
   <td><p>Sites</p> </td>
   <td><p>Niet-HA</p> </td>
   <td><p>Windows</p> </td>
   <td><p>CQSE</p> </td>
   <td><p>Oracle</p> </td>
   <td><p>LDAP</p> </td>
   <td><p>Tar</p> </td>
   <td><p>Segment</p> </td>
   <td><p>Eigenschap</p> </td>
   <td><p>Apache</p> </td>
   <td><p>Rand</p> </td>
   <td><p>Doel</p> </td>
  </tr>
  <tr>
   <td><p>Activa</p> </td>
   <td><p>Publiceren-HA</p> </td>
   <td><p>Solaris</p> </td>
   <td><p>WebLogic</p> </td>
   <td><p>IBM</p> </td>
   <td><p>SAML</p> </td>
   <td><p>MongoDB</p> </td>
   <td><p>Bestand</p> </td>
   <td><p>Lucene</p> </td>
   <td><p>IIS</p> </td>
   <td><p>IE</p> </td>
   <td><p>Analyse</p> </td>
  </tr>
  <tr>
   <td><p>Gemeenschappen</p> </td>
   <td><p>Auteur-CS</p> </td>
   <td><p>Rode hoed</p> </td>
   <td><p>WebSphere</p> </td>
   <td><p>HP</p> </td>
   <td><p>Oauth</p> </td>
   <td><p>RDB/Oracle</p> </td>
   <td><p>S3/Azure</p> </td>
   <td><p>Solr</p> </td>
   <td><p>iPlanet</p> </td>
   <td><p>FireFox</p> </td>
   <td><p>Campagne</p> </td>
  </tr>
  <tr>
   <td><p>Formulieren</p> </td>
   <td><p>Auteur-offload</p> </td>
   <td><p>HP-UX</p> </td>
   <td><p>Tomcat</p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p>RDB/DB2</p> </td>
   <td><p>MongoDB</p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p>Chroom</p> </td>
   <td><p>Sociaal</p> </td>
  </tr>
  <tr>
   <td><p>Mobiel</p> </td>
   <td><p>Auteur-cluster</p> </td>
   <td><p>IBM AIX</p> </td>
   <td><p>JBoss</p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p>RDB/MySQL</p> </td>
   <td><p>RDBMS</p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p>Safari</p> </td>
   <td><p>Publiek</p> </td>
  </tr>
  <tr>
   <td><p>Meerdere sites</p> </td>
   <td><p>ASRP</p> </td>
   <td><p>SUSE</p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p>RDB/SQLServer</p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p>Activa</p> </td>
  </tr>
  <tr>
   <td><p>Handel</p> </td>
   <td><p>MSRP</p> </td>
   <td><p>Apple OS</p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p>Activering</p> </td>
  </tr>
  <tr>
   <td><p>Dynamische media</p> </td>
   <td><p>JSRP</p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p>Mobiel</p> </td>
  </tr>
  <tr>
   <td><p>Brand Portal</p> </td>
   <td><p>J2E</p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
  </tr>
  <tr>
   <td><p>AoD</p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
  </tr>
  <tr>
   <td><p>LiveFyre</p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
  </tr>
  <tr>
   <td><p>Schermen</p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
  </tr>
  <tr>
   <td><p>Documentbeveiliging</p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
  </tr>
  <tr>
   <td><p>Procesbeheer</p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
  </tr>
  <tr>
   <td><p>bureaubladtoepassing</p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
   <td><p> </p> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>De prestatierichtlijnen zijn voornamelijk van toepassing op AEM-sites.

## Wanneer moeten de prestatierichtlijnen worden gebruikt? {#when-to-use-the-performance-guidelines}

In de volgende situaties moet u de prestatierichtlijnen gebruiken:

* **Eerste implementatie**: Wanneer u van plan bent AEM-sites of -middelen voor het eerst te implementeren, is het belangrijk dat u de beschikbare opties begrijpt wanneer u de Micro Kernel, Node Store en Data Store configureert (in vergelijking met de standaardinstellingen). Bijvoorbeeld, veranderend de standaardmontages van het Opslag van Gegevens voor TarMK in de Opslag van de Gegevens van het Dossier.
* **Een upgrade uitvoeren naar een nieuwe versie**: Wanneer u een upgrade uitvoert naar een nieuwe versie, is het belangrijk dat u de verschillen in prestaties begrijpt ten opzichte van de actieve omgeving. Bijvoorbeeld, bevordering van AEM 6.1 aan 6.2, of van AEM 6.0 CRX2 aan 6.2 OAK.
* **De responstijd is traag**: Wanneer de geselecteerde architectuur van Nodestore niet aan uw vereisten voldoet, is het belangrijk om de prestatiesverschillen te begrijpen vergeleken met andere topologieopties. U kunt bijvoorbeeld TarMK gebruiken in plaats van MongoMK, of een File Data Sore gebruiken in plaats van een Amazon S3- of Microsoft Azure Data Store.
* **Meer auteurs** toevoegen: Wanneer de geadviseerde topologie TarMK niet aan de prestatiesvereisten voldoet en het upsizing van de knoop van de Auteur de maximumbeschikbare capaciteit heeft bereikt, is het belangrijk om de prestatiesverschillen te begrijpen vergeleken bij het gebruiken van MongoMK met drie of meer knopen van de Auteur. U kunt bijvoorbeeld MongoMK gebruiken in plaats van TarMK.
* **Meer inhoud** toevoegen: Als de aanbevolen gegevensopslagarchitectuur niet aan uw vereisten voldoet, is het belangrijk dat u weet welke prestatieverschillen er zijn ten opzichte van andere gegevensopslagopties. Voorbeeld: gebruik van de Amazon S3 of Microsoft Azure Data Store in plaats van een File Data Store.

## Inleiding {#introduction}

In dit hoofdstuk wordt een algemeen overzicht gegeven van de AEM-architectuur en de belangrijkste componenten ervan. Zij bevat ook ontwikkelingsrichtsnoeren en beschrijft de testscenario&#39;s die in de TarMK- en MongoMK-benchmarktests worden gebruikt.

### Het AEM-platform {#the-aem-platform}

Het AEM-platform bestaat uit de volgende componenten:

![chlimage_1](assets/chlimage_1a.png)

Zie [Wat is AEM](/help/sites-deploying/deploy.md#what-is-aem)voor meer informatie over het AEM-platform.

### De AEM-architectuur {#the-aem-architecture}

Er zijn drie belangrijke bouwstenen aan een plaatsing AEM. De **instantie** Auteur die door auteurs van inhoud, editors en fiatteurs wordt gebruikt om inhoud te maken en te reviseren. Wanneer de inhoud wordt goedgekeurd, wordt het gepubliceerd aan een tweede instantietype genoemd de **Publish Instantie** van waar het door het eind wordt betreden - gebruikers. De derde bouwsteen is **Dispatcher** die een module is die caching en URL het filtreren behandelt en op de webserver geïnstalleerd is. Voor extra informatie over de architectuur AEM, zie de [Typische Scenario&#39;s](/help/sites-deploying/deploy.md#typical-deployment-scenarios)van de Plaatsing.

![chlimage_1-1](assets/chlimage_1-1a.png)

### Micro Kernels {#micro-kernels}

Micro Kernels fungeert als persistentiemanagers in AEM. Er worden drie soorten Micro Kernels gebruikt met AEM: TarMK, MongoDB, en Relationele Gegevensbestand (onder beperkte steun). Het kiezen van één om uw behoeften te passen hangt van het doel van uw instantie en het plaatsingstype af u overweegt. Raadpleeg de pagina [Aanbevolen implementaties](/help/sites-deploying/recommended-deploys.md) voor meer informatie over Micro Kernels.

![chlimage_1-2](assets/chlimage_1-2a.png)

### Nodestore {#nodestore}

In AEM, kunnen de binaire gegevens onafhankelijk van inhoudsknopen worden opgeslagen. De locatie waar de binaire gegevens worden opgeslagen, wordt de **gegevensopslag** genoemd, terwijl de locatie van de inhoudknooppunten en -eigenschappen de **knooppuntopslag** wordt genoemd.

>[!NOTE]
>
>Adobe raadt TarMK aan als de standaardpersistentietechnologie die door klanten wordt gebruikt voor zowel de AEM-auteur als de publicatie-exemplaren.

>[!CAUTION]
>
>De relationele Database Micro Kernel wordt beperkt ondersteund. Neem contact op met de [klantenservice](https://helpx.adobe.com/marketing-cloud/contact-support.html) van Adobe voordat u dit type Micro Kernel gebruikt.

![chlimage_1-3](assets/chlimage_1-3a.png)

### Gegevensopslag {#data-store}

Wanneer het behandelen van groot aantal binaire getallen, adviseert men dat een externe gegevensopslag in plaats van de standaardknoopopslag wordt gebruikt om prestaties te maximaliseren. Als uw project bijvoorbeeld een groot aantal media-elementen vereist, kunt u deze sneller openen dan ze rechtstreeks in een MongoDB opslaan als u ze onder de File of Azure/S3 Data Store opslaat.

Voor verdere details over de beschikbare configuratieopties, zie het [Vormen van Knoop en de Opslag](/help/sites-deploying/data-store-config.md)van Gegevens.

>[!NOTE]
>
>Adobe raadt u aan de optie te kiezen voor de implementatie van AEM op Azure of Amazon Web Services (AWS) met behulp van Adobe Managed Services, waarbij klanten profiteren van een team dat de ervaring en vaardigheden heeft om AEM in deze cloud computing-omgevingen te implementeren en te gebruiken. Raadpleeg onze [aanvullende documentatie over Adobe Managed Services](https://www.adobe.com/marketing-cloud/enterprise-content-management/managed-services-cloud-platform.html?aemClk=t).
>
>Voor aanbevelingen over de implementatie van AEM in Azure of AWS, buiten de door Adobe beheerde services, raden we u ten zeerste aan rechtstreeks samen te werken met de cloud provider of een van onze partners die de implementatie van AEM in de cloud-omgeving van uw keuze ondersteunen. De geselecteerde cloudprovider of partner is verantwoordelijk voor de groottesortering van specificaties, het ontwerp en de implementatie van de architectuur die zij ondersteunen om te voldoen aan uw specifieke vereisten op het gebied van prestaties, belasting, schaalbaarheid en beveiliging.
>
>Zie ook de pagina met [technische vereisten](/help/sites-deploying/technical-requirements.md#supported-platforms) voor meer informatie.

### Zoeken {#search-features}

In deze sectie worden de aangepaste indexproviders weergegeven die met AEM worden gebruikt. Voor meer informatie over het indexeren, zie de Vragen van de [Eik en het Indexeren](/help/sites-deploying/queries-and-indexing.md).

>[!NOTE]
>
>Voor de meeste plaatsingen, adviseert Adobe het gebruiken van de Index van Lucene. U zou Solr slechts voor scalability in gespecialiseerde en complexe plaatsingen moeten gebruiken.

![chlimage_1-4](assets/chlimage_1-4a.png)

### Richtlijnen voor ontwikkeling {#development-guidelines}

U zou voor AEM moeten ontwikkelen die op **prestaties en scalability** gericht is. Hieronder vindt u een aantal aanbevolen procedures die u kunt volgen:

**DO**

* Scheiding van presentatie, logica en inhoud toepassen
* Bestaande AEM API&#39;s gebruiken (bijvoorbeeld: Sling) en gereedschap (bv. Replicatie)
* Ontwikkelen in de context van werkelijke inhoud
* Ontwikkelen voor optimale kakkerbaarheid
* Aantal spaarbestanden minimaliseren (bijv.: door gebruik te maken van tijdelijke workflows)
* Zorg ervoor alle eindpunten van HTTP RESTful zijn
* Het bereik van de GCR-waarneming beperken
* Onthoud asynchrone thread

**NIET**

* Gebruik niet direct JCR-API&#39;s, als dat mogelijk is
* Geen /libs-wijziging, maar gebruik overlays
* Gebruik waar mogelijk geen query&#39;s
* Gebruik geen Sling Bindings om de diensten OSGi in code van Java te krijgen, maar eerder gebruik:

   * @Reference in een DS-component
   * @Injecteren in een verkoopmodel
   * sling.getService() in een klasse voor rechtmatig gebruik
   * sling.getService() in een JSP
   * een ServiceTracker
   * directe toegang tot het OSGi-serviceregister

Lees [Developing - The Basics](/help/sites-developing/the-basics.md)voor meer informatie over het ontwikkelen op AEM. Voor extra beste praktijken, zie de Beste praktijken [van de](/help/sites-developing/best-practices.md)Ontwikkeling.

### Benchmark Scenarios {#benchmark-scenarios}

>[!NOTE]
>
>Alle benchmarktests die op deze pagina worden weergegeven, zijn uitgevoerd in een laboratoriumomgeving.

De hieronder beschreven testscenario&#39;s worden gebruikt voor de benchmarksecties van de hoofdstukken TarMK, MongoMk en TarMK vs MongoMk. Om te zien welk scenario voor een bepaalde benchmarktest werd gebruikt, lees het gebied van het Scenario van de lijst van de [Technische Specificaties](/help/sites-deploying/performance-guidelines.md#tarmk-performance-benchmark) .

**Scenario één product**

AEM-elementen:

* Gebruikersinteracties: Blader middelen / zoekmiddelen / element downloaden / Metagegevens van element lezen / Metagegevens van element bijwerken / element uploaden / workflow voor uploaden van element uitvoeren
* Uitvoermodus: gelijktijdige gebruikers, enkele interactie per gebruiker

**Productscenario mixen**

AEM-sites + middelen:

* Gebruikersinteracties voor sites: Artikelpagina lezen / Pagina lezen / Alinea maken / Alinea bewerken / Pagina Inhoud maken / Pagina Inhoud plaatsen/Zoeken in auteur activeren
* Gebruikersinteracties voor middelen: Blader middelen / zoekmiddelen / element downloaden / Metagegevens van element lezen / Metagegevens van element bijwerken / element uploaden / workflow voor uploaden van element uitvoeren
* Uitvoermodus: gelijktijdige gebruikers, gemengde interacties per gebruiker

**Het verticale Scenario van het Geval van het Gebruik**

Media:

* Artikelpagina lezen (27,4%), Pagina lezen (10,9%), Sessie maken (2,6%), Pagina met inhoud activeren (1,7%), Pagina met inhoud maken (0,4%), Alinea maken (4,3%), Alinea bewerken (0,9%), Afbeeldingscomponent (0,9%), Bladeren-elementen (20%), Metagegevens van element lezen (8,5%), Downloadmiddel (4,2%), Zoekmiddel (0,2%), Asset-metagegevens bijwerken (2,4%), Element uploaden (1,2%), Bladeren project (4,9%), Project lezen (6,6%), Project toevoegen element (1,2%), Project toevoegen Site (1,2%), Project maken (0,1%), Auteur zoeken (0,4%)
* Uitvoermodus: gelijktijdige gebruikers, gemengde interacties per gebruiker

## TarMK {#tarmk}

Dit hoofdstuk geeft algemene prestatiesrichtlijnen voor TarMK die de minimumarchitectuurvereisten en de montageconfiguratie specificeren. Er wordt ook voorzien in benchmarktests voor verdere verduidelijking.

Adobe raadt TarMK aan de standaardpersistentietechnologie te zijn die door klanten in alle implementatiescenario&#39;s wordt gebruikt, voor zowel de AEM-auteur- als de AEM-publicatiemogelijkheden.

Voor meer informatie over TarMK, zie de Scenario&#39;s [van de](/help/sites-deploying/recommended-deploys.md#deployment-scenarios) Plaatsing en de Opslag van [Tar](/help/sites-deploying/storage-elements-in-aem-6.md#tar-storage).

### Richtlijnen voor minimale architectuur van TarMK {#tarmk-minimum-architecture-guidelines}

>[!NOTE]
>
>De onderstaande minimale architectuurrichtlijnen zijn van toepassing op productieomgevingen en grote verkeerslocaties. Dit zijn **niet** de [minimumspecificaties](/help/sites-deploying/technical-requirements.md#prerequisites) nodig om AEM in werking te stellen.

Om goede prestaties te vestigen wanneer het gebruiken van TarMK, zou u van de volgende architectuur moeten beginnen:

* Eén instantie Auteur
* Twee publicatie-instanties
* Twee verzenders

Hieronder ziet u de architectuurrichtlijnen voor AEM-sites en AEM-middelen.

>[!NOTE]
>
>Binair-less replicatie zou moeten worden aangezet **op** als de Datastore van het Dossier wordt gedeeld.

**Richtlijnen voor tekenarchitectuur voor AEM-sites**

![chlimage_1-5](assets/chlimage_1-5a.png)

**Richtsnoeren voor de architectuur van banden voor AEM-activa**

![chlimage_1-6](assets/chlimage_1-6a.png)

### TarMK Settings Guideline {#tarmk-settings-guideline}

Voor goede prestaties, zou u de montages hieronder voorgestelde richtlijnen moeten volgen. Zie [deze pagina](https://helpx.adobe.com/experience-manager/kb/performance-tuning-tips.html)voor instructies over het wijzigen van de instellingen.

<table>
 <tbody>
  <tr>
   <td><strong>Instelling</strong></td>
   <td><strong>Parameter</strong></td>
   <td><strong>Waarde</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td>Taakwachtrijen voor verkopen</td>
   <td><code>queue.maxparallel</code></td>
   <td>Stel waarde in op de helft van het aantal CPU-cores. </td>
   <td>Standaard is het aantal gelijktijdige threads per taakwachtrij gelijk aan het aantal CPU-cores.</td>
  </tr>
  <tr>
   <td>Graniet Transient Workflow Queue</td>
   <td><code>Max Parallel</code></td>
   <td>Stel waarde in op de helft van het aantal CPU-cores</td>
   <td> </td>
  </tr>
  <tr>
   <td>JVM-parameters</td>
   <td><p><code>Doak.queryLimitInMemory</code></p> <p><code>Doak.queryLimitReads</code></p> <p><code>Dupdate.limit</code></p> <p><code>Doak.fastQuerySize</code></p> </td>
   <td><p>500000</p> <p>100000</p> <p>250000</p> <p>Waar</p> </td>
   <td>Voeg deze JVM-parameters toe aan het AEM-beginscript om te voorkomen dat uitgebreide query's de systemen overladen.</td>
  </tr>
  <tr>
   <td>Lucene-indexconfiguratie</td>
   <td><p><code>CopyOnRead</code></p> <p><code>CopyOnWrite</code></p> <p><code>Prefetch Index Files</code></p> </td>
   <td><p>Ingeschakeld</p> <p>Ingeschakeld</p> <p>Ingeschakeld</p> </td>
   <td>Zie <a href="https://jackrabbit.apache.org/oak/docs/query/lucene.html">deze pagina</a>voor meer informatie over de beschikbare parameters.</td>
  </tr>
  <tr>
   <td>Data Store = S3 Datastore</td>
   <td><p><code>maxCachedBinarySize</code></p> <p><code>cacheSizeInMB</code></p> </td>
   <td><p>1048576 (1 MB) of kleiner</p> <p>2-10% van maximale heapgrootte</p> </td>
   <td>Zie ook <a href="/help/sites-deploying/data-store-config.md#data-store-configurations">Configuraties</a>van gegevensopslag.</td>
  </tr>
  <tr>
   <td>Workflow voor DAM-update-middelen</td>
   <td><code>Transient Workflow</code></td>
   <td>ingeschakeld</td>
   <td>Deze workflow beheert de update van elementen.</td>
  </tr>
  <tr>
   <td>DAM MetaData Writeback</td>
   <td><code>Transient Workflow</code></td>
   <td>ingeschakeld</td>
   <td>Deze workflow beheert de XMP-schrijfbewerking naar het oorspronkelijke binaire bestand en stelt de laatste gewijzigde datum in JCR in.</td>
  </tr>
 </tbody>
</table>

### TarMK Performance Benchmark {#tarmk-performance-benchmark}

#### Technische specificaties {#technical-specifications}

De benchmarktests werden uitgevoerd op de volgende specificaties:

|  | **Auteursknooppunt** |
|---|---|
| Server | Hardware voor onbewerkte metalen (HP) |
| Besturingssysteem | RedHat Linux |
| CPU/kernen | Intel(R) Xeon(R) CPU E5-2407 @2,40 GHz, 8 kernen |
| RAM | 32GB |
| Schijf | Magnetisch |
| Java | Oracle JRE versie 8 |
| JVM Heap | 16GB |
| Product | AEM 6.2 |
| Nodestore | TarMK |
| Datastore | Bestand DS |
| Scenario | Enkel product: Elementen / 30 gelijktijdige threads |

#### Resultaten prestatie-benchmark {#performance-benchmark-results}

>[!NOTE]
>
>De hieronder vermelde aantallen zijn genormaliseerd aan 1 als basislijn en zijn niet de daadwerkelijke productienummers.

![chlimage_1-7](assets/chlimage_1-7a.png) ![chlimage_1-8](assets/chlimage_1-8a.png)

## MongoMK {#mongomk}

De primaire reden voor het kiezen van de MongoMK persistence backend over TarMK is de instanties horizontaal te schalen. Dit betekent dat er altijd twee of meer actieve auteur-instanties moeten worden uitgevoerd en dat MongoDB moet worden gebruikt als het opslagsysteem voor persistentie. De noodzaak om meer dan één auteurinstantie in werking te stellen vloeit over het algemeen voort uit het feit dat de cpu en geheugencapaciteit van één enkele server, die alle gezamenlijke auteursactiviteiten steunt, niet meer duurzaam is.

Voor meer informatie over TarMK, zie de Scenario&#39;s [van de](/help/sites-deploying/recommended-deploys.md#deployment-scenarios) Plaatsing en de Opslag [van](/help/sites-deploying/storage-elements-in-aem-6.md#mongo-storage)Mongo.

### Richtlijnen voor minimale architectuur van MongoMK {#mongomk-minimum-architecture-guidelines}

Om goede prestaties te vestigen wanneer het gebruiken van MongoMK, zou u van de volgende architectuur moeten beginnen:

* Drie instanties van Auteur
* Twee publicatie-instanties
* Drie MongoDB-instanties
* Twee verzenders

>[!NOTE]
>
>In productieomgevingen wordt MongoDB altijd gebruikt als een replicaset met een primaire en twee secundaire server. Lezen en schrijven gaan naar de primaire website en lezen kan naar de secundaire medewerkers gaan. Als opslag niet beschikbaar is, kan een van de secundaire bestanden worden vervangen door een arbiter, maar MongoDB-replicasets moeten altijd uit een oneven aantal instanties bestaan.

>[!NOTE]
>
>Binair-less replicatie zou moeten worden aangezet **op** als de Datastore van het Dossier wordt gedeeld.

![chlimage_1-9](assets/chlimage_1-9a.png)

### Richtlijnen voor MongoMK-instellingen {#mongomk-settings-guidelines}

Voor goede prestaties, zou u de montages hieronder voorgestelde richtlijnen moeten volgen. Zie [deze pagina](https://helpx.adobe.com/experience-manager/kb/performance-tuning-tips.html)voor instructies over het wijzigen van de instellingen.

<table>
 <tbody>
  <tr>
   <td><strong>Instelling</strong></td>
   <td><strong>Parameter</strong></td>
   <td><strong>Waarde (standaardwaarde)</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td>Taakwachtrijen voor verkopen</td>
   <td><code>queue.maxparallel</code></td>
   <td>Stel waarde in op de helft van het aantal CPU-cores. </td>
   <td>Standaard is het aantal gelijktijdige threads per taakwachtrij gelijk aan het aantal CPU-cores.</td>
  </tr>
  <tr>
   <td>Graniet Transient Workflow Queue</td>
   <td><code>Max Parallel</code></td>
   <td>Stel waarde in op de helft van het aantal CPU-cores.</td>
   <td> </td>
  </tr>
  <tr>
   <td>JVM-parameters</td>
   <td><p><code>Doak.queryLimitInMemory</code></p> <p><code>Doak.queryLimitReads</code></p> <p><code>Dupdate.limit</code></p> <p><code>Doak.fastQuerySize</code></p> <p><code>Doak.mongo.maxQueryTimeMS</code></p> </td>
   <td><p>500000</p> <p>100000</p> <p>250000</p> <p>Waar</p> <p>60000</p> </td>
   <td>Voeg deze JVM-parameters toe aan het AEM-beginscript om te voorkomen dat uitgebreide query's de systemen overladen.</td>
  </tr>
  <tr>
   <td>Lucene-indexconfiguratie</td>
   <td><p><code>CopyOnRead</code></p> <p><code>CopyOnWrite</code></p> <p><code>Prefetch Index Files</code></p> </td>
   <td><p>Ingeschakeld</p> <p>Ingeschakeld</p> <p>Ingeschakeld</p> </td>
   <td>Zie <a href="https://jackrabbit.apache.org/oak/docs/query/lucene.html">deze pagina</a>voor meer informatie over de beschikbare parameters.</td>
  </tr>
  <tr>
   <td>Data Store = S3 Datastore</td>
   <td><p><code>maxCachedBinarySize</code></p> <p><code>cacheSizeInMB</code></p> </td>
   <td><p>1048576 (1 MB) of kleiner</p> <p>2-10% van maximale heapgrootte</p> </td>
   <td>Zie ook <a href="/help/sites-deploying/data-store-config.md#data-store-configurations">Configuraties</a>van gegevensopslag.</td>
  </tr>
  <tr>
   <td>DocumentNodeStoreService</td>
   <td><p><code>cache</code></p> <p><code>nodeCachePercentage</code></p> <p><code>childrenCachePercentage</code></p> <p><code>diffCachePercentage</code></p> <p><code>docChildrenCachePercentage</code></p> <p><code>prevDocCachePercentage</code></p> <p><code>persistentCache</code></p> </td>
   <td><p>2048</p> <p>35 (25)</p> <p>20 (10)</p> <p>30 (5)</p> <p>10 (3)</p> <p>4 (4)</p> <p>./cache,size=2048,binary=0,-compact,-compress</p> </td>
   <td><p>De standaardgrootte van de cache is ingesteld op 256 MB.</p> <p>Heeft invloed op de tijd die nodig is om cachevalidatie uit te voeren.</p> </td>
  </tr>
  <tr>
   <td>eik-waarneming</td>
   <td><p><code>thread pool</code></p> <p><code>length</code></p> </td>
   <td><p>min &amp; max = 20</p> <p>50000</p> </td>
   <td> </td>
  </tr>
 </tbody>
</table>

### MongoMK Performance Benchmark {#mongomk-performance-benchmark}

### Technische specificaties {#technical-specifications-1}

De benchmarktests werden uitgevoerd op de volgende specificaties:

|  | **Auteur-knooppunt** | **MongoDB-knooppunt** |
|---|---|---|
| Server | Hardware voor onbewerkte metalen (HP) | Hardware voor onbewerkte metalen (HP) |
| Besturingssysteem | RedHat Linux | RedHat Linux |
| CPU/kernen | Intel(R) Xeon(R) CPU E5-2407 @2,40 GHz, 8 kernen | Intel(R) Xeon(R) CPU E5-2407 @2,40 GHz, 8 kernen |
| RAM | 32GB | 32GB |
| Schijf | Magnetisch - >1k IOPS | Magnetisch - >1k IOPS |
| Java | Oracle JRE versie 8 | N.v.t. |
| JVM Heap | 16GB | N.v.t. |
| Product | AEM 6.2 | MongoDB 3.2 WiredTiger |
| Nodestore | MongoMK | N.v.t. |
| Datastore | Bestand DS | N.v.t. |
| Scenario | Enkel product: Elementen / 30 gelijktijdige threads | Enkel product: Elementen / 30 gelijktijdige threads |

### Resultaten prestatie-benchmark {#performance-benchmark-results-1}

>[!NOTE]
>
>De hieronder vermelde aantallen zijn genormaliseerd aan 1 als basislijn en zijn niet de daadwerkelijke productienummers.

![chlimage_1-10](assets/chlimage_1-10a.png) ![chlimage_1-11](assets/chlimage_1-11a.png)

## TarMK vs MongoMK {#tarmk-vs-mongomk}

De basisregel die in overweging moet worden genomen wanneer het kiezen tussen twee is dat TarMK voor prestaties wordt ontworpen, terwijl MongoMK voor scalability wordt gebruikt. Adobe raadt TarMK aan de standaardpersistentietechnologie te zijn die door klanten in alle implementatiescenario&#39;s wordt gebruikt, voor zowel de AEM-auteur- als de AEM-publicatiemogelijkheden.

De primaire reden voor het kiezen van de MongoMK persistence backend over TarMK is de instanties horizontaal te schalen. Dit betekent dat er altijd twee of meer actieve auteur-instanties moeten worden uitgevoerd en dat MongoDB moet worden gebruikt als het opslagsysteem voor persistentie. De noodzaak om meer dan één auteurinstantie in werking te stellen vloeit over het algemeen voort uit het feit dat de cpu en geheugencapaciteit van één enkele server, die alle gezamenlijke auteursactiviteiten steunt, niet meer duurzaam is.

Zie [Aanbevolen implementaties](/help/sites-deploying/recommended-deploys.md#microkernels-which-one-to-use)voor meer informatie over TarMK vs MongoMK.

### TarMK vs MongoMk Guidelines {#tarmk-vs-mongomk-guidelines}

**Voordelen van TarMK**

* Speciaal ontworpen voor toepassingen voor inhoudsbeheer
* Bestanden zijn altijd consistent en er kunnen back-ups van worden gemaakt met elk bestandsgebaseerd back-upprogramma
* Verstrekt een failovermechanisme - zie [Koude Reserve](/help/sites-deploying/tarmk-cold-standby.md) voor meer details
* Biedt hoge prestaties en betrouwbare gegevensopslag met minimale operationele overhead
* Lagere totale eigendomskosten (totale eigendomskosten)

**Criteria voor de keuze van MongoMK**

* Aantal benoemde gebruikers verbonden in een dag: in duizenden of meer
* Aantal gelijktijdige gebruikers: in honderden of meer
* Omvang van de ingenomen activa per dag: in honderdduizenden of meer
* Volume van paginabewerkingen per dag: in honderdduizenden of meer
* Volume zoekopdrachten per dag: in tienduizenden of meer

### TarMK vs MongoMK Benchmarks {#tarmk-vs-mongomk-benchmarks}

>[!NOTE]
>
>De hieronder vermelde aantallen zijn genormaliseerd aan 1 als basislijn en zijn geen daadwerkelijke productienummers.

### Scenario 1 — Technische specificaties {#scenario-technical-specifications}

<table>
 <tbody>
  <tr>
   <td><strong> </strong></td>
   <td><strong>Auteur-OAK-knooppunt</strong></td>
   <td><strong>MongoDB-knooppunt</strong></td>
   <td> </td>
  </tr>
  <tr>
   <td>Server</td>
   <td>Hardware voor onbewerkte metalen (HP)</td>
   <td>Hardware voor onbewerkte metalen (HP)</td>
   <td> </td>
  </tr>
  <tr>
   <td>Besturingssysteem</td>
   <td>RedHat Linux</td>
   <td>RedHat Linux</td>
   <td> </td>
  </tr>
  <tr>
   <td>CPU/kernen</td>
   <td>Intel(R) Xeon(R) CPU E5-2407 @2,40 GHz, 8 kernen</td>
   <td>Intel(R) Xeon(R) CPU E5-2407 @2,40 GHz, 8 kernen</td>
   <td> </td>
  </tr>
  <tr>
   <td>RAM</td>
   <td>32GB</td>
   <td>32GB</td>
   <td> </td>
  </tr>
  <tr>
   <td>Schijf</td>
   <td>Magnetisch - &gt;1k IOPS</td>
   <td>Magnetisch - &gt;1k IOPS</td>
   <td> </td>
  </tr>
  <tr>
   <td>Java</td>
   <td>Oracle JRE versie 8</td>
   <td>N.v.t.</td>
   <td> </td>
  </tr>
  <tr>
   <td>JVM Heap16 GB</td>
   <td>16GB</td>
   <td>N.v.t.</td>
   <td> </td>
  </tr>
  <tr>
   <td>Product </td>
   <td>AEM 6.2</td>
   <td>MongoDB 3.2 WiredTiger</td>
   <td> </td>
  </tr>
  <tr>
   <td>Nodestore</td>
   <td>TarMK of MongoMK</td>
   <td>N.v.t.</td>
   <td> </td>
  </tr>
  <tr>
   <td>Datastore</td>
   <td>Bestand DS </td>
   <td>N.v.t.</td>
   <td> </td>
  </tr>
  <tr>
   <td>Scenario</td>
   <td><p><br /> Enkel product: Elementen / 30 gelijktijdige threads per run</p> </td>
   <td> </td>
   <td> </td>
  </tr>
 </tbody>
</table>

### Scenario 1 prestatie-benchmarkresultaten {#scenario-performance-benchmark-results}

![chlimage_1-12](assets/chlimage_1-12a.png)

### Scenario 2 — Technische specificaties {#scenario-technical-specifications-1}

>[!NOTE]
>
>Als u hetzelfde aantal auteurs met MongoDB wilt inschakelen als met één TarMK-systeem, hebt u een cluster met twee AEM-knooppunten nodig. Een cluster met vier knooppunten in MongoDB kan 1,8 keer het aantal auteurs afhandelen dan één TarMK-instantie. Een achtnodencluster MongoDB kan 2.3 keer het aantal Auteurs behandelen dan één instantie TarMK.

<table>
 <tbody>
  <tr>
   <td><strong> </strong></td>
   <td><strong>Auteur TarMK-knooppunt</strong></td>
   <td><strong>Auteur MongoMK Node</strong></td>
   <td><strong>MongoDB-knooppunt</strong></td>
  </tr>
  <tr>
   <td>Server</td>
   <td>AWS c3.8xlarge</td>
   <td>AWS c3.8xlarge</td>
   <td>AWS c3.8xlarge</td>
  </tr>
  <tr>
   <td>Besturingssysteem</td>
   <td>RedHat Linux</td>
   <td>RedHat Linux</td>
   <td>RedHat Linux</td>
  </tr>
  <tr>
   <td>CPU/kernen</td>
   <td>32</td>
   <td>32</td>
   <td>32</td>
  </tr>
  <tr>
   <td>RAM</td>
   <td>60GB</td>
   <td>60GB</td>
   <td>60GB</td>
  </tr>
  <tr>
   <td>Schijf</td>
   <td>SSD - 10.000 IOPS</td>
   <td>SSD - 10.000 IOPS</td>
   <td>SSD - 10.000 IOPS</td>
  </tr>
  <tr>
   <td>Java</td>
   <td>Oracle JRE versie 8</td>
   <td><br /> Oracle JRE versie 8</td>
   <td>N.v.t.</td>
  </tr>
  <tr>
   <td>JVM Heap16 GB</td>
   <td>30GB</td>
   <td>30GB</td>
   <td>N.v.t.</td>
  </tr>
  <tr>
   <td>Product </td>
   <td>AEM 6.2</td>
   <td>AEM 6.2</td>
   <td><br /> MongoDB 3.2 WiredTiger</td>
  </tr>
  <tr>
   <td>Nodestore</td>
   <td>TarMK </td>
   <td>MongoMK</td>
   <td><br /> N.v.t.</td>
  </tr>
  <tr>
   <td>Datastore</td>
   <td>Bestand DS </td>
   <td><br /> Bestand DS</td>
   <td><br /> N.v.t.</td>
  </tr>
  <tr>
   <td>Scenario</td>
   <td><p><br /> <br /> Verticaal gebruik: Media / 2000 gelijktijdige threads</p> </td>
   <td></td>
   <td></td>
  </tr>
 </tbody>
</table>

### Scenario 2 prestatie-benchmarkresultaten {#scenario-performance-benchmark-results-1}

![chlimage_1-13](assets/chlimage_1-13a.png)

### Richtlijnen voor schaalbaarheid van architectuur voor AEM-sites en -middelen {#architecture-scalability-guidelines-for-aem-sites-and-assets}

![chlimage_1-14](assets/chlimage_1-14a.png)

## Samenvatting van de prestatierichtlijnen {#summary-of-performance-guidelines}

De richtsnoeren op deze pagina kunnen als volgt worden samengevat:

* **TarMK met de Datastore** van het Dossier is de geadviseerde architectuur voor de meeste klanten:

   * Minimale topologie: één instantie Auteur, twee instanties Publish, twee Verzenders
   * Binair-less replicatie aangezet als de Datastore van het Dossier wordt gedeeld

* **MongoMK met de Datastore** van het Dossier is de geadviseerde architectuur voor horizontale scalability van de rij van de Auteur:

   * Minimale topologie: drie instanties Auteur, drie instanties MongoDB, twee instanties Publish, twee Verzenders
   * Binair-less replicatie aangezet als de Datastore van het Dossier wordt gedeeld

* **Nodestore** zou op de lokale schijf, niet een netwerk in bijlage opslag (NAS) moeten worden opgeslagen
* Bij gebruik van **Amazon S3**:

   * De Amazon S3-datastore wordt gedeeld door de Auteur- en Publish-laag
   * Binair-less replicatie moet worden aangezet
   * Voor de afvalophaling van Datastore is een eerste uitvoering vereist voor alle auteur- en publicatieknooppunten en vervolgens een tweede uitvoering voor Auteur

* **Er moet een aangepaste index worden gemaakt naast de index** van het vak die is gebaseerd op de meeste gebruikelijke zoekopdrachten

   * Lucene-indexen moeten worden gebruikt voor aangepaste indexen

* **Door de workflow aan te passen, kunt u de prestaties** aanzienlijk verbeteren, bijvoorbeeld door de videostap in de workflow Element bijwerken te verwijderen, listeners die niet worden gebruikt uit te schakelen, enz.

Lees ook de pagina [Aanbevolen implementaties](/help/sites-deploying/recommended-deploys.md) voor meer informatie.
