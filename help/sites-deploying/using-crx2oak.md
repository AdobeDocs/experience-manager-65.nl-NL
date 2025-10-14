---
title: CRX2Oak-migratiehulpprogramma gebruiken
description: Leer hoe u het CRX2Oak-migratiehulpprogramma met Adobe Experience Manager gebruikt. Het programma is ontworpen om u te helpen bij het migreren van gegevens tussen verschillende opslagplaatsen.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: upgrading
content-type: reference
feature: Upgrading
exl-id: ef3895b9-8d35-4881-8188-c864ae3f0b4c
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 48d12388d4707e61117116ca7eb533cea8c7ef34
workflow-type: tm+mt
source-wordcount: '1175'
ht-degree: 0%

---

# CRX2Oak-migratiehulpprogramma gebruiken{#using-the-crx-oak-migration-tool}

## Inleiding {#introduction}

CRX2Oak is een hulpmiddel dat is ontworpen voor het migreren van gegevens tussen verschillende opslagplaatsen.

Deze kan worden gebruikt om gegevens van oudere CQ-versies die op Apache Jackrabbit 2 zijn gebaseerd, te migreren naar Oak en kan ook worden gebruikt om gegevens te kopiëren tussen Oak-opslagplaatsen.

U kunt de nieuwste versie van crx2oak downloaden van de opslagplaats voor openbare Adoben op deze locatie:
[&#x200B; https://repo1.maven.org/maven2/com/adobe/granite/crx2oak/](https://repo1.maven.org/maven2/com/adobe/granite/crx2oak/)

>[!NOTE]
>
>Voor meer informatie over Apache Oak en zeer belangrijke concepten (AEM) persistentie van Adobe Experience Manager, zie [&#x200B; Inleiding aan het AEM Platform &#x200B;](/help/sites-deploying/platform.md).

## Gevallen voor migratiegebruik {#migration-use-cases}

U kunt het gereedschap gebruiken voor:

* Migreren van oudere CQ 5-versies naar AEM 6
* Gegevens kopiëren tussen meerdere Oak-opslagplaatsen
* Gegevens converteren tussen verschillende Oak MicroKernel-implementaties.

Ondersteuning voor migrerende opslagplaatsen die gebruikmaken van externe blob-opslagplaatsen (beter bekend als Data Stores) wordt in verschillende combinaties geboden. Een mogelijk migratiepad is van een CRX2-opslagplaats die een externe `FileDataStore` gebruikt naar een Oak-opslagplaats die een `S3DataStore` gebruikt.

In het onderstaande diagram worden alle mogelijke migratiecombinaties weergegeven die door CRX2Oak worden ondersteund:

![&#x200B; chlimage_1-151 &#x200B;](assets/chlimage_1-151.png)

## Functies {#features}

CRX2Oak wordt tijdens AEM upgrades op een manier aangeroepen waarbij de gebruiker een vooraf gedefinieerd migratieprofiel kan opgeven waarmee de herconfiguratie van persistentiemodi wordt geautomatiseerd. Dit wordt de snelstartmodus genoemd.

Het kan ook afzonderlijk worden uitgevoerd voor het geval het meer aanpassing vereist. In deze modus worden wijzigingen echter alleen doorgevoerd in de opslagplaats en moeten eventuele aanvullende aanpassingen van AEM handmatig worden uitgevoerd. Dit wordt de standalone wijze genoemd.

Een ander ding om op te merken is dat met de standaardmontages op standalone wijze, slechts de Opslag van de Knoop wordt gemigreerd en de nieuwe bewaarplaats de oude binaire opslag opnieuw gebruikt.

### Automatische QuickStart-modus {#automated-quickstart-mode}

Sinds AEM 6.3 kan CRX2Oak door de gebruiker gedefinieerde migratieprofielen verwerken die kunnen worden geconfigureerd met alle migratieopties die al beschikbaar zijn. Hierdoor is meer flexibiliteit mogelijk en kunt u de configuratie van AEM automatiseren. Functies die niet beschikbaar zijn als u het gereedschap in zelfstandige modus gebruikt.

Als u van CRX2Oak wilt overschakelen op de snelstartmodus, definieert u het pad naar de crx-quickstart-map in de installatiemap van het AEM met behulp van deze omgevingsvariabele van het besturingssysteem:

**voor op UNIX-Gebaseerde systemen en macOS:**

```shell
export SLING_HOME="/path/to/crx-quickstart"
```

**voor Vensters:**

```shell
SET "SLING_HOME=/path/to/crx-quickstart"
```

#### Ondersteuning hervatten {#resume-support}

De migratie kan op elk moment worden onderbroken, met de mogelijkheid om deze later te hervatten.

#### Aanpasbare upgradelogica {#customizable-upgrade-logic}

Aangepaste Java™-logica kan worden geïmplementeerd met `CommitHooks` . Aangepaste `RepositoryInitializer` -klassen kunnen worden geïmplementeerd om de repository te initialiseren met aangepaste waarden.

#### Ondersteuning voor bewerkingen met geheugentoewijzing {#support-for-memory-mapped-operations}

CRX2Oak ondersteunt standaard ook bewerkingen met geheugentoewijzing. Geheugentoewijzing verbetert de prestaties aanzienlijk en moet waar mogelijk worden gebruikt.

>[!CAUTION]
>
>Vergeet echter niet dat bewerkingen met geheugentoewijzing niet worden ondersteund voor Windows-platforms. Daarom wordt het geadviseerd om de **- onbruikbaar maken-mmap** parameter toe te voegen wanneer het uitvoeren van de migratie op Vensters.

#### Selectieve migratie van inhoud {#selective-migration-of-content}

Standaard wordt de gehele opslagplaats gemigreerd onder het pad `"/"` . U hebt echter volledige controle over de inhoud die u wilt migreren.

Als er een deel van de inhoud is die niet op de nieuwe instantie wordt vereist, kunt u de `--exclude-path` parameter gebruiken om de inhoud uit te sluiten en de verbeteringsprocedure te optimaliseren.

#### Pad samenvoegen {#path-merging}

Als gegevens tussen twee opslagplaatsen moeten worden gekopieerd en u een inhoudspad hebt dat op beide instanties verschillend is, kunt u het in de parameter `--merge-path` definiëren. Als u dat doet, kopieert CRX2Oak alleen de nieuwe knooppunten naar de doelopslagplaats en blijven de oude knooppunten op hun plaats.

![&#x200B; chlimage_1-152 &#x200B;](assets/chlimage_1-152.png)

#### Versieondersteuning {#version-support}

AEM maakt standaard een versie van elk knooppunt of elke pagina die wordt gewijzigd en slaat deze op in de opslagplaats. De versies kunnen vervolgens worden gebruikt om de pagina in een eerdere staat te herstellen.

Deze versies worden echter nooit leeggemaakt, zelfs niet als de originele pagina wordt verwijderd. Wanneer u werkt met opslagruimten die al lange tijd in bedrijf zijn, kan de migratie leiden tot het opnieuw verwerken van overbodige gegevens die worden veroorzaakt door zwevende versies.

Een handige functie voor dit soort situaties is de toevoeging van de parameter `--copy-versions` . Het kan worden gebruikt om de versieknooppunten tijdens migratie of exemplaar van een bewaarplaats over te slaan.

U kunt ook kiezen of u zwevende versies wilt kopiëren door `--copy-orphaned-versions=true` toe te voegen.

Beide parameters ondersteunen ook een datumnotatie `YYYY-MM-DD` voor het geval dat u versies niet later dan een bepaalde datum wilt kopiëren.

![&#x200B; chlimage_1-153 &#x200B;](assets/chlimage_1-153.png)

#### Source-versie openen {#open-source-version}

Een open-source versie van CRX2Oak is beschikbaar in de vorm van een eak-upgrade. Alle functies worden ondersteund, met uitzondering van:

* CRX2-ondersteuning
* Ondersteuning voor migratieprofiel
* Ondersteuning voor automatische AEM herconfiguratie

Zie de [&#x200B; Documentatie Apache &#x200B;](https://jackrabbit.apache.org/oak/docs/migration.html) voor meer informatie.

## Parameters {#parameters}

### Opslagopties knooppunt {#node-store-options}

* `--cache`: Cachegrootte in MB (standaardwaarde is `256` )

* `--mmap`: toegang tot aan het geheugen toegewezen bestanden voor de Segmentopslag inschakelen
* `--src-password:` Wachtwoord voor de RDB-brondatabase

* `--src-user:` Gebruiker voor de bron-RDB

* `--user`: Gebruiker voor de doel-RDB

* `--password`: wachtwoord voor de doel-RDB.

### Migratieopties {#migration-options}

* `--early-shutdown`: sluit de JCR2-bronopslagplaats af nadat knooppunten zijn gekopieerd en voordat de haken voor vastleggen zijn toegepast
* `--fail-on-error`: hiermee wordt een fout in de migratie geforceerd als de knooppunten niet van de bronopslagplaats kunnen worden gelezen.
* `--ldap`: Migreert LDAP-gebruikers van een CQ 5.x-instantie naar een op Oak gebaseerde instantie. Dit werkt alleen als de Identiteitsprovider in de Oak-configuratie de naam dap heeft. Voor meer informatie, zie de [&#x200B; documentatie LDAP &#x200B;](/help/sites-administering/ldap-config.md).

* `--ldap-config:` Gebruik dit met de parameter `--ldap` voor CQ 5.x-opslagruimten die meerdere LDAP-servers voor verificatie gebruiken. U kunt dit gebruiken om te verwijzen naar de configuratiebestanden van CQ 5.x `ldap_login.conf` of `jaas.conf` . De notatie is `--ldapconfig=path/to/ldap_login.conf` .

### Opties voor versieopslag {#version-store-options}

* `--copy-orphaned-versions`: slaat het kopiëren van zwevende versies over. Ondersteunde parameters zijn: `true` , `false` en `yyyy-mm-dd` . Wordt standaard ingesteld op `true` .

* `--copy-versions:` kopieert de versieopslag. Parameters: `true` , `false` , `yyyy-mm-dd` . Wordt standaard ingesteld op `true` .

#### Padopties {#path-options}

* `--include-paths:` Door komma&#39;s gescheiden lijst met paden die tijdens het kopiëren moeten worden opgenomen
* `--merge-paths`: door komma&#39;s gescheiden lijst met paden die tijdens het kopiëren moeten worden samengevoegd
* `--exclude-paths:` Door komma&#39;s gescheiden lijst met paden die tijdens het kopiëren moeten worden uitgesloten.

### Opties voor Source Blob-opslag {#source-blob-store-options}

* `--src-datastore:` De map datastore die als bron moet worden gebruikt `FileDataStore`

* `--src-fileblobstore`: De map datastore die als bron moet worden gebruikt `FileBlobStore`

* `--src-s3datastore`: De map datastore die voor de bron moet worden gebruikt `S3DataStore`

* `--src-s3config`: Het configuratiebestand voor de bron `S3DataStore` .

### Opties doelblobStore {#destination-blobstore-options}

* `--datastore:` De map datastore die als doel moet worden gebruikt `FileDataStore`

* `--fileblobstore:` De map datastore die als doel moet worden gebruikt `FileBlobStore`

* `--s3datastore`: De datastore-map die voor het doel moet worden gebruikt `S3DataStore`

* `--s3config`: Het configuratiebestand voor het doel `S3DataStore` .

### Help-opties {#help-options}

* `-?, -h, --help:` Geeft Help-informatie weer.

## Foutopsporing {#debugging}

U kunt ook foutopsporingsinformatie inschakelen voor het migratieproces om problemen op te lossen die tijdens het proces kunnen optreden. U kunt dit anders doen afhankelijk van de wijze u het hulpmiddel binnen wenst in werking te stellen:

<table>
 <tbody>
  <tr>
   <td><strong>CRX2Oak-modus</strong></td>
   <td><strong>Handeling</strong></td>
  </tr>
  <tr>
   <td>Snelstartmodus</td>
   <td>U kunt <strong> toevoegen - logboek-vlakke TRACE </strong> of <strong> - logboek-vlakke DEBUG </strong> opties aan de bevellijn wanneer het runnen van CRX2Oak. Op deze wijze, worden de logboeken automatisch opnieuw gericht aan het {</strong> dossier 0} upgrade.log.<strong></td>
  </tr>
  <tr>
   <td>Stand-alone modus</td>
   <td><p>Voeg de <strong> - spoor </strong> opties aan de CRX2Oak bevellijn toe zodat kunt u de gebeurtenissen van de TRACE op standaardoutput tonen (u moet logboeken zelf opnieuw richten gebruikend redirection karakter: '&gt;' of "de"bevel voor recentere inspectie).</p> </td>
  </tr>
 </tbody>
</table>

## Andere overwegingen {#other-considerations}

Wanneer u naar een MongoDB-replicaset migreert, moet u de parameter `WriteConcern` instellen op `2` voor alle verbindingen met de Mongo-databases.

U kunt dit doen door de parameter `w=2` aan het einde van de verbindingstekenreeks toe te voegen, zoals in het volgende voorbeeld:

```xml
java -Xmx4092m -jar crx2oak.jar crx-quickstart/repository/ mongodb://localhost:27017/aem-author?replicaset=replica1&w=2
```

>[!NOTE]
>
>Voor meer informatie, zie de documentatie van het Koord van de Verbinding MongoDB op [&#x200B; Zorgpunten schrijven &#x200B;](https://docs.mongodb.org/manual/reference/connection-string/#write-concern-options).
