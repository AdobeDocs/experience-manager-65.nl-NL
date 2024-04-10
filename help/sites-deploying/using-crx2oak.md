---
title: Het CRX2Oak-migratiehulpprogramma gebruiken
description: Leer hoe u het migratiehulpprogramma CRX2Oak kunt gebruiken met Adobe Experience Manager. Het programma is ontworpen om u te helpen bij het migreren van gegevens tussen verschillende opslagplaatsen.
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

# Het CRX2Oak-migratiehulpprogramma gebruiken{#using-the-crx-oak-migration-tool}

## Inleiding {#introduction}

CRX2Oak is een hulpmiddel dat wordt ontworpen om gegevens tussen verschillende bewaarplaatsen te migreren.

Deze kan worden gebruikt om gegevens van oudere CQ-versies die op Apache Jackrabbit 2 zijn gebaseerd, te migreren naar eikenhout en kan ook worden gebruikt om gegevens te kopiëren tussen Oak-opslagplaatsen.

U kunt de nieuwste versie van crx2oak downloaden van de opslagplaats voor openbare Adoben op deze locatie:
[https://repo1.maven.org/maven2/com/adobe/granite/crx2oak/](https://repo1.maven.org/maven2/com/adobe/granite/crx2oak/)

>[!NOTE]
>
>Raadpleeg voor meer informatie over Apache Oak en de belangrijkste concepten van Adobe Experience Manager (AEM) persistentie [Inleiding tot het AEM Platform](/help/sites-deploying/platform.md).

## Gevallen voor migratiegebruik {#migration-use-cases}

U kunt het gereedschap gebruiken voor:

* Migreren van oudere CQ 5-versies naar AEM 6
* Gegevens kopiëren tussen meerdere eiken-opslagplaatsen
* Gegevens tussen verschillende Oak MicroKernel-implementaties omzetten.

Ondersteuning voor migrerende opslagplaatsen die gebruikmaken van externe blob-opslagplaatsen (beter bekend als Data Stores) wordt in verschillende combinaties geboden. Een mogelijk migratiepad is afkomstig uit een CRX2-opslagplaats die een externe `FileDataStore` aan een eiken-opslagplaats die `S3DataStore`.

In het onderstaande diagram worden alle mogelijke migratiecombinaties weergegeven die door CRX2Oak worden ondersteund:

![chlimage_1-151](assets/chlimage_1-151.png)

## Functies {#features}

CRX2Oak wordt geroepen tijdens AEM verbeteringen op een manier waarin de gebruiker een vooraf bepaald migratieprofiel kan specificeren dat de herconfiguratie van persistentiemodi automatiseert. Dit wordt de snelstartmodus genoemd.

Het kan ook afzonderlijk worden uitgevoerd voor het geval het meer aanpassing vereist. In deze modus worden wijzigingen echter alleen doorgevoerd in de opslagplaats en moeten eventuele aanvullende aanpassingen van AEM handmatig worden uitgevoerd. Dit wordt de standalone wijze genoemd.

Een ander ding om op te merken is dat met de standaardmontages op standalone wijze, slechts de Opslag van de Knoop wordt gemigreerd en de nieuwe bewaarplaats de oude binaire opslag opnieuw gebruikt.

### Automatische QuickStart-modus {#automated-quickstart-mode}

Sinds AEM 6.3 kan CRX2Oak door de gebruiker gedefinieerde migratieprofielen verwerken die kunnen worden geconfigureerd met alle migratieopties die al beschikbaar zijn. Hierdoor is meer flexibiliteit mogelijk en kunt u de configuratie van AEM automatiseren. Functies die niet beschikbaar zijn als u het gereedschap in zelfstandige modus gebruikt.

Als u van CRX2Oak naar de snelstartmodus wilt overschakelen, definieert u het pad naar de crx-quickstart-map in de installatiemap van het AEM met behulp van deze omgevingsvariabele van het besturingssysteem:

**Voor op UNIX gebaseerde systemen en macOS:**

```shell
export SLING_HOME="/path/to/crx-quickstart"
```

**Voor Windows:**

```shell
SET "SLING_HOME=/path/to/crx-quickstart"
```

#### Ondersteuning hervatten {#resume-support}

De migratie kan op elk moment worden onderbroken, met de mogelijkheid om deze later te hervatten.

#### Aanpasbare upgradelogica {#customizable-upgrade-logic}

Aangepaste Java™-logica kan worden geïmplementeerd met `CommitHooks`. Aangepast `RepositoryInitializer` kunnen worden geïmplementeerd om de repository te initialiseren met aangepaste waarden.

#### Ondersteuning voor bewerkingen met geheugentoewijzing {#support-for-memory-mapped-operations}

CRX2Oak ondersteunt standaard ook bewerkingen met geheugentoewijzing. Geheugentoewijzing verbetert de prestaties aanzienlijk en moet waar mogelijk worden gebruikt.

>[!CAUTION]
>
>Vergeet echter niet dat bewerkingen met geheugentoewijzing niet worden ondersteund voor Windows-platforms. Daarom wordt aanbevolen het **—disable-mmap** parameter bij het uitvoeren van de migratie in Windows.

#### Selectieve migratie van inhoud {#selective-migration-of-content}

Standaard migreert het hulpprogramma de gehele opslagplaats onder de `"/"` pad. U hebt echter volledige controle over de inhoud die u wilt migreren.

Als er een onderdeel van de inhoud is dat niet op het nieuwe exemplaar wordt vereist, kunt u het `--exclude-path` om de inhoud uit te sluiten en de upgradeprocedure te optimaliseren.

#### Pad samenvoegen {#path-merging}

Als gegevens tussen twee opslagplaatsen moeten worden gekopieerd en u hebt een inhoudspad dat op beide instanties verschillend is, kunt u het in de `--merge-path` parameter. Als u dat doet, kopieert CRX2Oak alleen de nieuwe knooppunten naar de doelopslagplaats en blijven de oude knooppunten op hun plaats.

![chlimage_1-152](assets/chlimage_1-152.png)

#### Versieondersteuning {#version-support}

AEM maakt standaard een versie van elk knooppunt of elke pagina die wordt gewijzigd en slaat deze op in de opslagplaats. De versies kunnen vervolgens worden gebruikt om de pagina in een eerdere staat te herstellen.

Deze versies worden echter nooit leeggemaakt, zelfs niet als de originele pagina wordt verwijderd. Wanneer u werkt met opslagruimten die al lange tijd in bedrijf zijn, kan de migratie leiden tot het opnieuw verwerken van overbodige gegevens die worden veroorzaakt door zwevende versies.

Een nuttig kenmerk voor dit soort situaties is de toevoeging van de `--copy-versions` parameter. Het kan worden gebruikt om de versieknooppunten tijdens migratie of exemplaar van een bewaarplaats over te slaan.

U kunt ook kiezen of u zwevende versies wilt kopiëren door `--copy-orphaned-versions=true`.

Beide parameters ondersteunen ook een `YYYY-MM-DD` datumnotatie als u versies niet later dan een bepaalde datum wilt kopiëren.

![chlimage_1-153](assets/chlimage_1-153.png)

#### Bronversie openen {#open-source-version}

Een open-bronversie van CRX2Oak is beschikbaar in de vorm van eiken-verbetering. Alle functies worden ondersteund, met uitzondering van:

* CRX2-ondersteuning
* Ondersteuning voor migratieprofiel
* Ondersteuning voor automatische AEM herconfiguratie

Zie de [Apache-documentatie](https://jackrabbit.apache.org/oak/docs/migration.html) voor meer informatie .

## Parameters {#parameters}

### Opslagopties knooppunt {#node-store-options}

* `--cache`: Cachegrootte in MB (standaard is `256`)

* `--mmap`: Toegang tot in geheugen toegewezen bestanden voor Segmentarchief inschakelen
* `--src-password:` Wachtwoord voor de RDB-brondatabase

* `--src-user:` Gebruiker voor de bron-RDB

* `--user`: Gebruiker voor de doel-RDB

* `--password`: Wachtwoord voor de doel-RDB.

### Migratieopties {#migration-options}

* `--early-shutdown`: Sluit de bron-JCR2-opslagplaats af nadat knooppunten zijn gekopieerd en voordat de haken voor vastleggen zijn toegepast
* `--fail-on-error`: Dwingt een fout van de migratie als de knopen niet van de bronbewaarplaats kunnen worden gelezen.
* `--ldap`: Hiermee migreert u LDAP-gebruikers van een CQ 5.x-instantie naar een op eik gebaseerde instantie. Dit werkt alleen als de Identiteitsprovider in de configuratie Eak de naam dap heeft. Zie de klasse [LDAP-documentatie](/help/sites-administering/ldap-config.md).

* `--ldap-config:` Gebruik dit met de `--ldap` parameter voor CQ 5.x-opslagruimten die meerdere LDAP-servers voor verificatie hebben gebruikt. U kunt het gebruiken om naar CQ 5.x te richten `ldap_login.conf` of `jaas.conf` configuratiebestanden. De indeling is `--ldapconfig=path/to/ldap_login.conf`.

### Opties voor versieopslag {#version-store-options}

* `--copy-orphaned-versions`: Hiermee slaat u het kopiëren van zwevende versies over. Ondersteunde parameters zijn: `true`, `false`, en `yyyy-mm-dd`. Standaardwaarden: `true`.

* `--copy-versions:` Kopieert de versieopslag. Parameters: `true`, `false`, `yyyy-mm-dd`. Standaardwaarden: `true`.

#### Padopties {#path-options}

* `--include-paths:` Lijst met door komma&#39;s gescheiden paden die tijdens het kopiëren moeten worden opgenomen
* `--merge-paths`: Door komma&#39;s gescheiden lijst met paden die tijdens het kopiëren moeten worden samengevoegd
* `--exclude-paths:` Lijst met door komma&#39;s gescheiden paden die tijdens het kopiëren moeten worden uitgesloten.

### Opslagopties bronblob {#source-blob-store-options}

* `--src-datastore:` De datastore-map die als bron moet worden gebruikt `FileDataStore`

* `--src-fileblobstore`: De map datastore die als bron moet worden gebruikt `FileBlobStore`

* `--src-s3datastore`: De datastore-map die voor de bron moet worden gebruikt `S3DataStore`

* `--src-s3config`: Het configuratiebestand voor de bron `S3DataStore`.

### Opties doelblobStore {#destination-blobstore-options}

* `--datastore:` De datastore-map die als doel moet worden gebruikt `FileDataStore`

* `--fileblobstore:` De datastore-map die als doel moet worden gebruikt `FileBlobStore`

* `--s3datastore`: De datastore-map die voor het doel moet worden gebruikt `S3DataStore`

* `--s3config`: Het configuratiebestand voor het doel `S3DataStore`.

### Help-opties {#help-options}

* `-?, -h, --help:` Help-informatie weergeven.

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
   <td>U kunt de <strong>—TRACE op logniveau</strong> of <strong>—DEBUG OP Logniveau </strong>opties voor de opdrachtregel bij het uitvoeren van CRX2Oak. In deze modus worden logbestanden automatisch doorgestuurd naar de <strong>upgrade.log, bestand</strong>.</td>
  </tr>
  <tr>
   <td>Stand-alone modus</td>
   <td><p>Voeg de <strong>—trace</strong> Hiermee kunt u opties instellen op de opdrachtregel van CRX2Oak, zodat u TRACE-gebeurtenissen kunt weergeven bij de standaarduitvoer (u moet de logbestanden zelf omleiden met het redirection-teken '&gt;' of de opdracht 'tee' voor latere controle).</p> </td>
  </tr>
 </tbody>
</table>

## Andere overwegingen {#other-considerations}

Wanneer u naar een MongoDB-replicaset migreert, moet u de optie `WriteConcern` parameter to `2` op alle verbindingen met de Mongo-databases.

U kunt dit doen door de `w=2` parameter aan het einde van de verbindingstekenreeks, als volgt:

```xml
java -Xmx4092m -jar crx2oak.jar crx-quickstart/repository/ mongodb://localhost:27017/aem-author?replicaset=replica1&w=2
```

>[!NOTE]
>
>Zie de documentatie van de reeks MongoDB-verbindingen over [Vragen schrijven](https://docs.mongodb.org/manual/reference/connection-string/#write-concern-options).
