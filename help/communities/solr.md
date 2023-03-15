---
title: Solr Configuratie voor SRP
seo-title: Solr Configuration for SRP
description: Een Apache Solr-installatie kan worden gedeeld tussen de nodenwinkel (Oak) en de gemeenschappelijke opslagplaats (SRP) door verschillende verzamelingen te gebruiken
seo-description: An Apache Solr installation may be shared between the node store (Oak) and common store (SRP) by using different collections
uuid: 7356343d-073c-4266-bdcb-c7e999281476
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: e228f1db-91ea-4ec3-86da-06d89d74bc72
role: Admin
exl-id: a9fc9c06-b9e6-4a5e-ab5e-0930ecd4b51b
source-git-commit: 1d334c42088342954feb34f6179dc5b134f81bb8
workflow-type: tm+mt
source-wordcount: '1457'
ht-degree: 2%

---

# Solr Configuratie voor SRP {#solr-configuration-for-srp}

## Solr. voor AEM Platform {#solr-for-aem-platform}

An [Apache Solr](https://lucene.apache.org/solr/) de installatie kan worden gedeeld tussen de [knooppuntopslag](../../help/sites-deploying/data-store-config.md) (eikenhout) en [gemeenschappelijk archief](working-with-srp.md) (SRP) door verschillende verzamelingen te gebruiken.

Als zowel de Oak als SRP inzamelingen intensief worden gebruikt, kan tweede Solr om prestatiesredenen worden geïnstalleerd.

Voor productieomgevingen [SolrCloud-modus](#solrcloud-mode) biedt betere prestaties in vergelijking met de zelfstandige modus (één lokale Solr-instelling).

### Vereisten {#requirements}

Download en installeer Apache Solr:

* [Versie 7.0](https://archive.apache.org/dist/lucene/solr/7.0.0/)

* Solr vereist Java 1.7 of hoger
* Er is geen service nodig
* Keuze van uitvoeringsmodi:

   * Standalone modus
   * [SolrCloud-modus](#solrcloud-mode) (aanbevolen voor productieomgevingen)

* Keuze van meertalig zoeken (MLS)

   * [Standaard MLS installeren](#installing-standard-mls)
   * [Geavanceerde MLS installeren](#installing-advanced-mls)

## SolrCloud-modus {#solrcloud-mode}

[SolrCloud](https://solr.apache.org/guide/6_6/solrcloud.html) wordt aanbevolen voor productieomgevingen. Wanneer de SolrCloud-modus actief is, moet SolrCloud worden geïnstalleerd en geconfigureerd voordat u MLS (Multilingual Search) kunt installeren.

U wordt aangeraden de installatie-instructies voor SolrCloud op te volgen:

* 3 SolrCloud-knooppunten op dezelfde server.
* Een externe Apache ZooKeeper.

Het wordt ook aanbevolen JVM te configureren om het geheugengebruik en de opschoonfunctie af te stemmen.

### Voorbeeld van JVM-configuratie {#jvm-configuration-example}

```shell
JVM_OPTS="-server -Xmx2048m -XX:MaxPermSize=768M -XX:+UseConcMarkSweepGC -XX:+CMSClassUnloadingEnabled -Xloggc:../logs/gc.log -XX:+PrintGCDetails -XX:+PrintGCDateStamps -Djava.awt.headless=true"
```

### Opdrachten voor instellen van SolrCloud {#solrcloud-setup-commands}

Wanneer de installatie wordt uitgevoerd in de SolrCloud-modus, zijn het gebruik en de kennis van de volgende opdrachten voor de SolrCloud-instelling vereist voordat MLS wordt geïnstalleerd.

#### 1. Een configuratie uploaden naar ZooKeeper {#upload-a-configuration-to-zookeeper}

Referentie:
[https://cwiki.apache.org/confluence/display/solr/Command+Line+Utilities](https://cwiki.apache.org/confluence/display/solr/Command+Line+Utilities)

Gebruik: sh./scripts/cloud-scripts/zkcli.sh \
-cmd upconfig \
-zkhost *server:poort* \
-confname *myconfig-name *\
-solrhome *solr-home-pad* \
-confdir *config-dir*

#### 2. Een verzameling maken {#create-a-collection}

Referentie:
[https://cwiki.apache.org/confluence/display/solr/Solr+Start+Script+Reference#SolrStartScriptReference-Create](https://cwiki.apache.org/confluence/display/solr/Solr+Start+Script+Reference#SolrStartScriptReference-Create)

Gebruik:
./bin/solr create \
-c *mycollection-name*\
-d *config-dir* \
-n *myconfig-name* \
-p *poort*\
-s *aantal schepen* \
-rf *aantal replica&#39;s*

#### 3. Een verzameling koppelen aan een configuratieset {#link-a-collection-to-a-configuration-set}

Koppel een verzameling aan een configuratie die al is geüpload naar ZooKeeper.

Referentie:
[https://cwiki.apache.org/confluence/display/solr/Command+Line+Utilities](https://cwiki.apache.org/confluence/display/solr/Command+Line+Utilities)

Gebruik: sh./scripts/cloud-scripts/zkcli.sh \
-cmd linkconfig \
-zkhost *server:poort* \
-collection *mycollection-name* \
-confname *myconfig-name*

### Vergelijking van standaard en geavanceerde MLS {#comparison-of-standard-and-advanced-mls}

Meertalig zoeken (MLS) voor AEM Communities is ontwikkeld voor het Solr-platform, zodat alle ondersteunde talen, waaronder het Engels, beter kunnen worden doorzocht.

MLS voor AEM gemeenschappen is beschikbaar als Standaard MLS of Geavanceerde MLS. Standaard MLS bevat alleen Solr-configuratie-instellingen en sluit insteekmodules of bronbestanden uit. Geavanceerde MLS is de uitgebreidere oplossing en bevat zowel de configuratie-instellingen voor Solr als plug-ins en bijbehorende bronnen

Standaard MLS bevat verbeteringen voor het zoeken naar inhoud voor de volgende talen:

* Engels: Verbeterde stemmer voor het zoeken naar overeenkomsten met woordafleidingen.
* Japans: Verbeterde Japanse tokenisatie voor tekens met halve breedte.

Geavanceerde MLS bevat verbeteringen voor het zoeken naar inhoud voor de volgende talen:

* Engels: Vervangen stemmer met citroenzuur.
* Duits: Toegevoegde decompounder.
* Frans: Toegevoegde uitzichtsbehandeling.
* Chinees (vereenvoudigd): Een slimmere tokenizer toegevoegd.
* Diverse talen: Er is een stemmer, een stopwoordlijst en een normalisatie toegevoegd.

In alle talen worden de volgende 33 talen ondersteund in Advanced MLS.

| Arabisch | Duits | Noors |
|---|---|---|
| Bulgaars | Grieks | Pools |
| Chinees (vereenvoudigd) | Haitian Creole | Portugees |
| Chinees (traditioneel) | Hebreeuws | Roemeens |
| Tsjechisch | Hongaars | Russisch |
| Deens | Bahasa Indonesia | Slovaaks |
| Nederlands | Italiaans | Sloveens |
| Engels | Japans | Spaans |
| Estisch | Koreaans | Zweeds |
| Fins | Lets | Thai |
| Frans | Litouws | Turks |

#### Vergelijking van AEM 6.1 Solr zoeken, Standaard MLS en Geavanceerde MLS {#comparison-of-aem-solr-search-standard-mls-and-advanced-mls}

**Opmerking**: AEM 6.1 verwijst naar AEM 6.1 KP3 en lager.

![compare-solr-mls](assets/compare-solr-mls.png)

### Standaard MLS installeren {#installing-standard-mls}

Voor de inzameling SRP (of MSRP of DSRP), om Standaard Meertalig Onderzoek (MLS) te steunen is het noodzakelijk om twee configuratiedossiers van Solr te wijzigen:

* **schema.xml**
* **solrconfig.xml**

Standaard MLS-bestanden (schema.xml, solrconfig.xml) voor Solr 4.10.

Standaard MLS-bestanden (schema.xml, solrconfig.xml) voor Solr 5.x.

De standaard MLS-bestanden worden opgeslagen in de AEM opslagplaats.

**Opmerking**: Terwijl de Solr dossiers in msrp/ omslag worden opgeslagen, zijn zij ook voor DSRP (geen noodzakelijke veranderingen).

**Downloadinstructies**: Vervangen `solrX` with `solr4` of `solr5` in voorkomend geval.

1. Gebruikend CRXDE|Lite, bepaal de plaats:

   * `/libs/social/config/datastore/msrp/solrX/schema.xml`
   * `/libs/social/config/datastore/msrp/solrX/solrconfig.xml`

1. Download naar de lokale server waarop Solr wordt geïmplementeerd.

   * Zoek de `jcr:content` knooppunten `jcr:data` eigenschap.
   * Selecteren `view` om het downloaden te starten.
   * Zorg ervoor dat de bestanden met de juiste namen en codering (UTF8) worden opgeslagen.

1. Volg de installatie-instructies voor de zelfstandige modus of de SolrCloud-modus.

#### SolrCloud-modus - Standaard MLS {#solrcloud-mode-standard-mls}

1. Solr installeren en configureren in de SolrCloud-modus.
1. Een nieuwe configuratie voorbereiden:

   1. Nieuwe config-dir* maken, zoals `solr-install-dir*/myconfig/`

   1. Kopieer de inhoud van de bestaande Solr configuratiemap naar *new-config-dir*

      * Voor Solr4: kopiëren `solr-install-dir/example/solr/collection1/conf/`
      * Voor Solr5: kopiëren `solr-install-dir/server/solr/configsets/data_driven_schema_configs/`
   1. Het gedownloade bestand kopiëren **schema.xml** en **solrconfig.xml** tot *new-config-dir* om bestaande bestanden te overschrijven.


1. [De nieuwe configuratie uploaden](#upload-a-configuration-to-zookeeper) naar ZooKeeper.
1. [Een verzameling maken](#create-a-collection) het specificeren van de noodzakelijke parameters, zoals aantal plaatsen, aantal replica&#39;s, en configuratienaam.
1. Als de configuratienaam *not *provided tijdens verwezenlijking van de inzameling was, [deze nieuwe verzameling koppelen](#link-a-collection-to-a-configuration-set) met de configuratie die aan ZooKeeper wordt geupload.

1. Voor MSRP, looppas [MSRP opnieuw indexeren](msrp.md#msrp-reindex-tool), tenzij dit een nieuwe installatie is.

#### Standalone modus - Standaard MLS {#standalone-mode-standard-mls}

1. Installeer Solr in zelfstandige modus.
1. Als het lopen Solr5, creeer een inzameling1 (gelijkend op Solr4):

   * `./bin/solr start`
   * `./bin/solr create_core -c collection1 -d sample_techproducts_configs`

1. Back-up **schema.xml** en **solrconfig.xml** in de Solr config-map, zoals:

   * Voor Solr4: `solr-install-dir/example/solr/collection1/conf/`
   * Gemaakt voor Solr5: `solr-install-dir/server/solr/collection1/conf/`

1. Het gedownloade bestand kopiëren **schema.xml** en **solrconfig.xml** naar dezelfde map.

1. Start Solr opnieuw.
1. Voor MSRP, looppas [MSRP opnieuw indexeren](#msrpreindextool), tenzij dit een nieuwe installatie is.

### Geavanceerde MLS installeren {#installing-advanced-mls}

Voor de inzameling SRP (MSRP of DSRP) om geavanceerde MLS te steunen, worden nieuwe stop-ins Solr vereist naast een douaneschema en de configuratie Solr. Alle vereiste items worden verpakt in een ZIP-bestand dat kan worden gedownload. Bovendien is een installatiescript inbegrepen voor gebruik wanneer Solr op standalone wijze wordt opgesteld.

Ga voor het geavanceerde MLS-pakket naar [Geavanceerde MLS AEM](deploy-communities.md#aem-advanced-mls) in de op te stellen sectie van de documentatie.

Ga als volgt te werk om aan de slag te gaan met de installatie voor de zelfstandige of SolrCloud-modus:

* Download AEM-SOLR-MLS zip archief naar de server die Solr host.
* Pak het archief uit.

#### SolrCloud-modus - Geavanceerde MLS {#solrcloud-mode-advanced-mls}

Installatie-instructies - let op de weinige verschillen voor Solr4 en Solr5:

1. Solr installeren en configureren in de SolrCloud-modus.
1. Extraheer de inhoud van het Geavanceerde pakket MLS naar schijf. De inhoud moet het volgende omvatten:

   * **schema.xml**
   * **solrconfig.xml**
   * **stopwords/** map
   * **profielen/** map
   * **extra-libs/** map

1. Een nieuwe configuratie voorbereiden:

   1. Een *new-config-dir*

      * zoals `solr-install-dir/myconfig/`
      * Submappen maken `stopwords/` en `lang/`
   1. Kopieer de inhoud van de bestaande Solr config-map naar *new-config-dir*

      * Voor Solr4: Kopiëren `solr-install-dir/example/solr/collection1/conf/`
      * Voor Solr5: Kopiëren `solr-install-dir/server/solr/configsets/data_driven_schema_configs/`
   1. Het geëxtraheerde bestand kopiëren **schema.xml** en **solrconfig.xml** tot *new-config-dir* om bestaande bestanden te overschrijven.
   1. Voor Solr5: Kopiëren `solr_install_dir/server/solr/configsets/sample_techproducts_configs/conf/lang/*.txt` tot `new-config-dir/lang/`
   1. Het geëxtraheerde bestand kopiëren **stopwords/** map naar *new-config-dir* leiden tot `new-config-dir/stopwords/*.txt`



1. [De nieuwe configuratie uploaden](#upload-a-configuration-to-zookeeper) naar ZooKeeper
1. Nieuw kopiëren **profielen/** map ...

   * Voor Solr4: Kopiëren naar bronnen/map van elk knooppunt
   * Voor Solr5: Kopieer naar de server/resources/ map van elke Solr-installatie. Als alle knooppunten zich in dezelfde installatiemap Solr bevinden, wordt deze stap slechts één keer uitgevoerd.

1. Een **lib/** in de map solr-home (bevat solr.xml) van elk knooppunt in SolrCloud. Kopieer potten van de volgende locaties naar de nieuwe lib/-map op elk knooppunt:

   * **extra-libs/** geëxtraheerd uit het geavanceerde MLS-pakket
   * *solr-install-dir/contrib/extractie/lib/*.jar
   * *solr-install-dir/dist/solr-cell*.jar
   * *solr-install-dir/contrib/clustering/lib/*.jar
   * *solr-install-dir/dist/solr-clustering*.jar
   * *solr-install-dir/contrib/langid/lib/*.jar
   * *solr-install-dir/dist/solr-langid*.jar
   * *solr-install-dir/contrib/snelheid/lib/*.jar
   * *solr-install-dir/dist/solr-snelheid*.jar
   * *solr-install-dir/contrib/analysis-extras/lib/*.jar
   * *solr-install-dir/contrib/analysis-extras/lucene-libs/*.jar

1. [Een verzameling maken](#create-a-collection) het specificeren van de noodzakelijke parameters, zoals aantal plaatsen, aantal replica&#39;s, en configuratienaam.
1. Als de configuratienaam was *niet* verstrekt tijdens het aanmaken van de collectie; [deze nieuwe verzameling koppelen](#link-a-collection-to-a-configuration-set) met de configuratie die aan ZooKeeper wordt geupload.

1. Voor MSRP, looppas [MSRP opnieuw indexeren](#msrpreindextool), tenzij dit een nieuwe installatie is.

#### Standalone modus - Geavanceerde MLS {#standalone-mode-advanced-mls}

Een installatiescript is inbegrepen in het Geavanceerde pakket MLS.

Nadat de inhoud van het pakket is geëxtraheerd naar de server die als host fungeert voor de zelfstandige Solr-server, voert u gewoon het installatiescript uit om de benodigde bronnen en configuratiebestanden te installeren.

* Installeer Solr in zelfstandige modus.
* Als het lopen Solr5, creeer een inzameling1 (gelijkend op Solr4):

   * `./bin/solr start`
   * `./bin/solr create_core -c collection1 -d sample_techproducts_configs`

* Voer het installatiescript uit: Installeren [-v 4|5] [-d solrhome] [-c verzamelingspad]
waarbij:

   * -d solrhome

      Solr-installatiemap

   * -c verzamelingspad

      Verzamelingspad in solo

   * —help

      Opties voor de opdrachtregel Afdrukken

   * -v [4|5]

      Versie instellen voor solr

* Voorbeeld voor Solr 4.10.4:

   * Install.bat -v 4-d c:/solr-4.10.4 -c:/solr-4.10.4/example/solr/collection1

* Voorbeeld voor Solr 5.4.0:

   * Install.sh -v 5-d /tmp/solr-5.4.0 -c /tmp/solr-5.4.0/server/solr/collection1

**Opmerking**:

* Het installatiescript zal file.xml en solrconfig.xml alvorens nieuwe versies te installeren door &quot;.orig&quot;toe te voegen

### Info solrconfig.xml {#about-solrconfig-xml}

De **solrconfig.xml** het dossier controleert automatisch interval en onderzoekszicht begaan en zal het testen en het stemmen vereisen.

`<autoCommit>`: Door gebrek, wordt het interval AutoCommit, dat hard aan stabiele opslag is begaan, geplaatst aan 15 seconden. De zoekzichtbaarheid wordt standaard ingesteld op het gebruik van de vooraf vastgelegde index.

Als u een zoekopdracht wilt wijzigen en een index wilt gebruiken die is bijgewerkt om wijzigingen door te voeren die het gevolg zijn van de bewerking, wijzigt u de inhoud `openSearcher` naar waar.

`autoSoftCommit`: Een &#39;soft&#39; commit zorgt ervoor dat de veranderingen zichtbaar zijn (de index wordt bijgewerkt), maar verzekert niet dat de veranderingen aan stabiele opslag (hard commit) worden gesynchroniseerd. Het resultaat is een verbetering van de prestaties. Standaard, `autoSoftCommit` is uitgeschakeld met de bevat `maxTime` ingesteld op -1.
