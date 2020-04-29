---
title: Solr Configuratie voor SRP
seo-title: Solr Configuratie voor SRP
description: Een Apache Solr-installatie kan worden gedeeld tussen de nodenwinkel (Oak) en de gemeenschappelijke opslagplaats (SRP) door verschillende verzamelingen te gebruiken
seo-description: Een Apache Solr-installatie kan worden gedeeld tussen de nodenwinkel (Oak) en de gemeenschappelijke opslagplaats (SRP) door verschillende verzamelingen te gebruiken
uuid: 7356343d-073c-4266-bdcb-c7e999281476
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: e228f1db-91ea-4ec3-86da-06d89d74bc72
translation-type: tm+mt
source-git-commit: 3296db289b2e2f4ca0d1981597ada6ca1310bd46

---


# Solr Configuratie voor SRP {#solr-configuration-for-srp}

## Solr voor AEM-platform {#solr-for-aem-platform}

Een [installatie van Apache Solr](https://lucene.apache.org/solr/) kan tussen de [knoopopslag](../../help/sites-deploying/data-store-config.md) (Oak) en [gemeenschappelijke opslag](working-with-srp.md) (SRP) door verschillende inzamelingen worden gedeeld te gebruiken.

Als zowel de Oak als SRP inzamelingen intensief worden gebruikt, kan tweede Solr om prestatiesredenen worden geïnstalleerd.

Voor productieomgevingen biedt de [SolrCloud-modus](#solrcloud-mode) betere prestaties dan de zelfstandige modus (één lokale Solr-instelling).

### Vereisten {#requirements}

Download en installeer Apache Solr:

* [Versie 4.10](https://archive.apache.org/dist/lucene/solr/4.10.4/) of [versie 5.x](https://archive.apache.org/dist/lucene/solr/5.5.3/)

* Solr vereist Java 1.7 of hoger
* Er is geen service nodig
* Keuze van uitvoeringsmodi:

   * Standalone modus
   * [SolrCloud-modus](#solrcloud-mode) (aanbevolen voor productieomgevingen)

* Keuze van meertalig zoeken (MLS)

   * [Standaard MLS installeren](#installing-standard-mls)
   * [Geavanceerde MLS installeren](#installing-advanced-mls)

## SolrCloud-modus {#solrcloud-mode}

[De SolrCloud](https://cwiki.apache.org/confluence/display/solr/SolrCloud) -modus wordt aanbevolen voor productieomgevingen. Wanneer de SolrCloud-modus actief is, moet SolrCloud worden geïnstalleerd en geconfigureerd voordat u MLS (Multilingual Search) kunt installeren.

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

Gebruik:
sh./scripts/cloud-scripts/zkcli.sh \
-cmd upconfig \
-zkhost *server:poort* \
-confname *myconfig-name *\
-solrhome *solr-home-path* \
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
-s *aantal scheepswerven* \
-rf *aantal replica&#39;s*

#### 3. Een verzameling koppelen aan een configuratieset {#link-a-collection-to-a-configuration-set}

Koppel een verzameling aan een configuratie die al is geüpload naar ZooKeeper.

Referentie:
[https://cwiki.apache.org/confluence/display/solr/Command+Line+Utilities](https://cwiki.apache.org/confluence/display/solr/Command+Line+Utilities)

Gebruik:
sh./scripts/cloud-scripts/zkcli.sh \
-cmd linkconfig \
-zkhost *server:poort* \
-collection *mycollection-name* \
-confname *myconfig-name*

### Vergelijking van standaard en geavanceerde MLS {#comparison-of-standard-and-advanced-mls}

Meertalig zoeken (MLS) voor AEM-gemeenschappen is ontworpen om het Solr-platform te voorzien in verbeterde zoekopdrachten in alle ondersteunde talen, waaronder het Engels.

MLS voor AEM-gemeenschappen is beschikbaar als standaard MLS of geavanceerde MLS. Standaard MLS bevat alleen Solr-configuratie-instellingen en sluit insteekmodules of bronbestanden uit. Geavanceerde MLS is de uitgebreidere oplossing en bevat zowel de configuratie-instellingen voor Solr als plug-ins en bijbehorende bronnen

Standaard MLS bevat verbeteringen voor het zoeken naar inhoud voor de volgende talen:

* Engels: Verbeterde stemmer voor het zoeken naar overeenkomsten met woordafleidingen.
* Japans: Verbeterde Japanse tokenisatie voor tekens met halve breedte.

Geavanceerde MLS bevat verbeteringen voor het zoeken naar inhoud voor de volgende talen:

* Engels: Vervangen stemmer met citroenzuur.
* Duits: Toegevoegde decompounder.
* Frans: Toegevoegde uitzichtsbehandeling.
* Chinees (vereenvoudigd): Een slimmere tokenizer toegevoegd.
* Diverse talen: Er is een stemmer, een stopwoordlijst en een normalisatie toegevoegd.

In alle gevallen worden de volgende 33 talen ondersteund in Advanced MLS.

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

#### Vergelijking van AEM 6.1 Solr onderzoek, Standaard MLS en Geavanceerde MLS {#comparison-of-aem-solr-search-standard-mls-and-advanced-mls}

**Opmerking**: AEM 6.1 verwijst naar AEM 6.1 Community FP3 en eerder.

![chlimage_1-283](assets/chlimage_1-283.png)

### Standaard MLS installeren {#installing-standard-mls}

Voor de inzameling SRP (of MSRP of DSRP), om Standaard Meertalig Onderzoek (MLS) te steunen is het noodzakelijk om twee configuratiedossiers van Solr te wijzigen:

* **schema.xml**
* **solrconfig.xml**

Standaard MLS-bestanden (schema.xml, solrconfig.xml) voor Solr 4.10.

Standaard MLS-bestanden (schema.xml, solrconfig.xml) voor Solr 5.x.

De standaard MLS-bestanden worden opgeslagen in de AEM-opslagruimte.

**Opmerking**: Terwijl de Solr dossiers in msrp/ omslag worden opgeslagen, zijn zij ook voor DSRP (geen noodzakelijke veranderingen).

**Downloadinstructies**: Vervangen `solrX` door `solr4` of `solr5` naar gelang van het geval.

1. Gebruikend CRXDE|Lite, bepaal de plaats:

   * `/libs/social/config/datastore/msrp/solrX/schema.xml`
   * `/libs/social/config/datastore/msrp/solrX/solrconfig.xml`

1. Download naar de lokale server waarop Solr wordt geïmplementeerd.

   * Zoek de `jcr:content` eigenschap van het `jcr:data` knooppunt.
   * Selecteer deze optie `view` om het downloaden te starten.
   * Zorg ervoor dat de bestanden met de juiste namen en codering (UTF8) worden opgeslagen.

1. Volg de installatie-instructies voor de zelfstandige modus of de SolrCloud-modus.

#### SolrCloud-modus - Standaard MLS {#solrcloud-mode-standard-mls}

1. Solr installeren en configureren in de SolrCloud-modus.
1. Een nieuwe configuratie voorbereiden:

   1. Nieuwe config-dir* maken, zoals `solr-install-dir*/myconfig/`

   1. Kopieer de inhoud van de bestaande Solr configuratiemap naar *new-config-dir*

      * Voor Solr4: kopiëren `solr-install-dir/example/solr/collection1/conf/`
      * Voor Solr5: kopiëren `solr-install-dir/server/solr/configsets/data_driven_schema_configs/`
   1. Kopieer het gedownloade **schema.xml** en **solrconfig.xml** aan *nieuw-config-dir* om bestaande dossiers te beschrijven.


1. [Upload de nieuwe configuratie](#upload-a-configuration-to-zookeeper) aan ZooKeeper.
1. [Creeer een inzameling](#create-a-collection) die de noodzakelijke parameters, zoals aantal plaatsen, aantal replica&#39;s, en configuratienaam specificeren.
1. Als de configuratienaam *not *provided tijdens verwezenlijking van de inzameling was, [verbind deze pas gecreëerde inzameling](#link-a-collection-to-a-configuration-set) met de configuratie die aan ZooKeeper wordt geupload.

1. Voor MSRP, looppas [MSRP Reindex Hulpmiddel](msrp.md#msrp-reindex-tool), tenzij dit een nieuwe installatie is.

#### Standalone modus - Standaard MLS {#standalone-mode-standard-mls}

1. Installeer Solr in zelfstandige modus.
1. Als het lopen Solr5, creeer een inzameling1 (gelijkend op Solr4):

   * `./bin/solr start`
   * `./bin/solr create_core -c collection1 -d sample_techproducts_configs`

1. Back-up **schema.xml** en **solrconfig.xml** in de Solr config-map, zoals:

   * Voor Solr4: `solr-install-dir/example/solr/collection1/conf/`
   * Gemaakt voor Solr5: `solr-install-dir/server/solr/collection1/conf/`

1. Kopieer het gedownloade **schema.xml** en **solrconfig.xml** aan die zelfde folder.

1. Start Solr opnieuw.
1. Voor MSRP, looppas [MSRP Reindex Hulpmiddel](#msrpreindextool), tenzij dit een nieuwe installatie is.

### Geavanceerde MLS installeren {#installing-advanced-mls}

Voor de inzameling SRP (MSRP of DSRP) om geavanceerde MLS te steunen, worden nieuwe stop-ins Solr vereist naast een douaneschema en de configuratie Solr. Alle vereiste items worden verpakt in een ZIP-bestand dat kan worden gedownload. Bovendien is een installatiescript inbegrepen voor gebruik wanneer Solr op standalone wijze wordt opgesteld.

Voor het Geavanceerde pakket MLS, zie [AEM Geavanceerde MLS](deploy-communities.md#aem-advanced-mls) in de plaatsingssectie van de documentatie.

Ga als volgt te werk om aan de slag te gaan met de installatie voor de zelfstandige of SolrCloud-modus:

* Download het zip-archief van AEM-SOLR-MLS naar de server die Solr host.
* Pak het archief uit.

#### SolrCloud-modus - Geavanceerde MLS {#solrcloud-mode-advanced-mls}

Installatie-instructies - let op de weinige verschillen voor Solr4 en Solr5:

1. Solr installeren en configureren in de SolrCloud-modus.
1. Extraheer de inhoud van het Geavanceerde pakket MLS naar schijf. De inhoud moet het volgende omvatten:

   * **schema.xml**
   * **solrconfig.xml**
   * **stopwords/** folder
   * **profielen/** map
   * **extra-libs/** map

1. Een nieuwe configuratie voorbereiden:

   1. Een *nieuwe configuratie-dir maken*

      * zoals `solr-install-dir/myconfig/`
      * Submappen maken `stopwords/` en `lang/`
   1. Kopieer de inhoud van de bestaande Solr config-dir aan *nieuw-config-dir*

      * Voor Solr4: Kopiëren `solr-install-dir/example/solr/collection1/conf/`
      * Voor Solr5: Kopiëren `solr-install-dir/server/solr/configsets/data_driven_schema_configs/`
   1. Kopieer het geëxtraheerde **schema.xml** en **solrconfig.xml** naar *new-config-dir* om bestaande bestanden te overschrijven.
   1. Voor Solr5: Kopiëren `solr_install_dir/server/solr/configsets/sample_techproducts_configs/conf/lang/*.txt` naar `new-config-dir/lang/`
   1. Kopieer de geëxtraheerde **stopwords/** map naar *new-config-dir* , wat resulteert in `new-config-dir/stopwords/*.txt`



1. [Upload de nieuwe configuratie](#upload-a-configuration-to-zookeeper) aan ZooKeeper
1. Nieuwe **profielen/** map kopiëren..

   * Voor Solr4: Kopiëren naar bronnen/map van elk knooppunt
   * Voor Solr5: Kopieer naar de server/resources/ map van elke Solr-installatie. Als alle knooppunten zich in dezelfde installatiemap Solr bevinden, wordt deze stap slechts één keer uitgevoerd.

1. Maak een **lib/** -map in de map solr-home (bevat solr.xml) van elk knooppunt in SolrCloud. Kopieer potten van de volgende locaties naar de nieuwe lib/-map op elk knooppunt:

   * **extra&#39;s/** geëxtraheerd uit het geavanceerde MLS-pakket
   * *solr-install-dir/contrib/extractie/lib/*.jar
   * *solr-install-dir/dist/solr-cell*.jar
   * *solr-install-dir/contrib/clustering/lib/*.jar
   * *solr-install-dir/dist/solr-clustering*.jar
   * *solr-install-dir/contrib/langid/lib/*.jar
   * *solr-install-dir/dist/solr-langid*.jar
   * *solr-install-dir/contrib/velocity/lib/*.jar
   * *solr-install-dir/dist/solr-velocity*.jar
   * *solr-install-dir/contrib/analysis-extras/lib/*.jar
   * *solr-install-dir/contrib/analysis-extras/lucene-libs/*.jar

1. [Creeer een inzameling](#create-a-collection) die de noodzakelijke parameters, zoals aantal plaatsen, aantal replica&#39;s, en configuratienaam specificeren.
1. Als de configuratienaam *niet* tijdens verwezenlijking van de inzameling werd verstrekt, [verbind deze pas gecreëerde inzameling](#link-a-collection-to-a-configuration-set) met de configuratie die aan ZooKeeper wordt geupload.

1. Voor MSRP, looppas [MSRP Reindex Hulpmiddel](#msrpreindextool), tenzij dit een nieuwe installatie is.

#### Standalone modus - Geavanceerde MLS {#standalone-mode-advanced-mls}

Een installatiescript is inbegrepen in het Geavanceerde pakket MLS.

Nadat de inhoud van het pakket is geëxtraheerd naar de server die als host fungeert voor de zelfstandige Solr-server, voert u gewoon het installatiescript uit om de benodigde bronnen en configuratiebestanden te installeren.

* Installeer Solr in zelfstandige modus.
* Als het lopen Solr5, creeer een inzameling1 (gelijkend op Solr4):

   * `./bin/solr start`
   * `./bin/solr create_core -c collection1 -d sample_techproducts_configs`

* Voer het installatiescript uit: Installeer [-v 4|5] -d [solrhome] [-c verzamelingspad], waarbij:

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

Het **solrconfig.xml** - dossier controleert automatisch interval en onderzoekszicht begaan en zal het testen en het stemmen vereisen.

`<autoCommit>`: Door gebrek, wordt het interval AutoCommit, dat hard aan stabiele opslag is begaan, geplaatst aan 15 seconden. De zoekzichtbaarheid wordt standaard ingesteld op het gebruik van de vooraf vastgelegde index.

Als u de zoekopdracht wilt wijzigen en een index wilt gebruiken die is bijgewerkt om wijzigingen te weerspiegelen die het gevolg zijn van de commit, wijzigt u de inhoud `openSearcher` in true.

`autoSoftCommit`: Een &#39;soft&#39; commit zorgt ervoor dat de veranderingen zichtbaar zijn (de index wordt bijgewerkt), maar verzekert niet dat de veranderingen aan stabiele opslag (hard commit) worden gesynchroniseerd. Het resultaat is een verbetering van de prestaties. Standaard `autoSoftCommit` is deze uitgeschakeld met de ingesloten `maxTime` waarde -1.
