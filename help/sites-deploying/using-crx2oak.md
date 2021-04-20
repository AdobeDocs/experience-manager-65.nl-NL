---
title: Het CRX2Oak-migratiehulpprogramma gebruiken
seo-title: Het CRX2Oak-migratiehulpprogramma gebruiken
description: Leer hoe u het migratiehulpmiddel CRX2Oak gebruikt.
seo-description: Leer hoe u het migratiehulpmiddel CRX2Oak gebruikt.
uuid: 9b788981-4ef0-446e-81f0-c327cdd3214b
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: e938bdc7-f8f5-4da5-81f6-7f60c6b4b8e6
feature: Upgrading
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1268'
ht-degree: 0%

---


# Het CRX2Oak-migratiehulpmiddel{#using-the-crx-oak-migration-tool} gebruiken

## Inleiding {#introduction}

CRX2Oak is een hulpmiddel dat wordt ontworpen om gegevens tussen verschillende bewaarplaatsen te migreren.

Deze kan worden gebruikt om gegevens van oudere CQ-versies op basis van Apache Jackrabbit 2 te migreren naar eikenhout en kan ook worden gebruikt om gegevens te kopiëren tussen Oak-opslagplaatsen.

U kunt de nieuwste versie van crx2oak downloaden van de openbare opslagplaats van Adobe op deze plaats:
[https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/crx2oak/](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/crx2oak/)

De lijst met wijzigingen en correcties voor de nieuwste versie vindt u in de [Opmerkingen bij de release van CRX2Oak](https://docs.adobe.com/content/help/en/experience-manager-64/release-notes/crx2oak.html).

>[!NOTE]
>
>Zie [Inleiding tot het AEM Platform](/help/sites-deploying/platform.md) voor meer informatie over Apache Oak en belangrijke concepten van AEM persistentie.

## Gevallen {#migration-use-cases} voor migratiegebruik

U kunt het gereedschap gebruiken voor:

* Migreren van oudere CQ 5-versies naar AEM 6
* Gegevens kopiëren tussen meerdere eiken-opslagplaatsen
* Gegevens tussen verschillende Oak MicroKernel-implementaties omzetten.

Ondersteuning voor migrerende opslagplaatsen die gebruikmaken van externe blob-opslagplaatsen (beter bekend als Data Stores) wordt in verschillende combinaties geboden. Eén mogelijk migratiepad is afkomstig van een CRX2-opslagplaats die een externe `FileDataStore` gebruikt naar een Eak-opslagplaats die een `S3DataStore` gebruikt.

In het onderstaande diagram worden alle mogelijke migratiecombinaties weergegeven die door CRX2Oak worden ondersteund:

![chlimage_1-151](assets/chlimage_1-151.png)

## Functies {#features}

CRX2Oak wordt geroepen tijdens AEM verbeteringen op een manier waarin de gebruiker een vooraf bepaald migratieprofiel kan specificeren dat de herconfiguratie van persistentiemodi automatiseert. Dit wordt de snelstartmodus genoemd.

Het kan ook afzonderlijk worden uitgevoerd voor het geval het meer aanpassing vereist. Let er echter op dat in deze modus alleen wijzigingen worden aangebracht in de opslagplaats en dat eventuele aanvullende aanpassingen van AEM handmatig moeten worden uitgevoerd. Dit wordt de standalone wijze genoemd.

Een ander ding om op te merken is dat met de standaardmontages op standalone wijze, slechts de Opslag van de Knoop zal worden gemigreerd en de nieuwe bewaarplaats zal de oude binaire opslag hergebruiken.

### Automatische QuickStart-modus {#automated-quickstart-mode}

Sinds AEM 6.3 kan CRX2Oak door de gebruiker gedefinieerde migratieprofielen verwerken die kunnen worden geconfigureerd met alle migratieopties die al beschikbaar zijn. Hierdoor is meer flexibiliteit mogelijk en kunt u de configuratie van AEM automatiseren. Functies die niet beschikbaar zijn als u het gereedschap in zelfstandige modus gebruikt.

Als u wilt overschakelen van CRX2Oak naar de snelstartmodus, moet u het pad naar de crx-quickstart-map in de AEM installatiemap definiëren via deze omgevingsvariabele van het besturingssysteem:

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

Aangepaste Java-logica die ook wordt geïmplementeerd met `CommitHooks`. Aangepaste `RepositoryInitializer`-klassen kunnen worden geïmplementeerd om de repository te initialiseren met aangepaste waarden.

#### Ondersteuning voor bewerkingen met geheugentoewijzing {#support-for-memory-mapped-operations}

CRX2Oak ondersteunt standaard ook bewerkingen die zijn toegewezen aan het geheugen. Geheugentoewijzing verbetert de prestaties aanzienlijk en moet waar mogelijk worden gebruikt.

>[!CAUTION]
>
>Vergeet echter niet dat bewerkingen met geheugentoewijzing niet worden ondersteund voor Windows-platforms. Daarom wordt geadviseerd om **-disable-mmap** parameter toe te voegen wanneer het uitvoeren van de migratie op Vensters.

#### Selectieve migratie van inhoud {#selective-migration-of-content}

Standaard migreert het hulpprogramma de gehele opslagplaats onder het pad `"/"`. U hebt echter volledige controle over de inhoud die u wilt migreren.

Als er om het even welk deel van de inhoud is die niet op de nieuwe instantie wordt vereist, kunt u de `--exclude-path` parameter gebruiken om de inhoud uit te sluiten en de verbeteringsprocedure te optimaliseren.

#### Samenvoegen van pad {#path-merging}

Als gegevens moeten worden gekopieerd tussen twee opslagplaatsen en u hebt een inhoudspad dat op beide instanties verschillend is, kunt u het in de `--merge-path` parameter bepalen. Zodra u, zal CRX2Oak slechts de nieuwe knopen aan de bestemmingsbewaarplaats kopiëren en zal oude op zijn plaats houden.

![chlimage_1-152](assets/chlimage_1-152.png)

#### Versieondersteuning {#version-support}

AEM maakt standaard een versie van elk knooppunt of elke pagina die wordt gewijzigd en slaat deze op in de opslagplaats. De versies kunnen vervolgens worden gebruikt om de pagina in een eerdere staat te herstellen.

Deze versies worden echter nooit leeggemaakt, zelfs niet als de originele pagina wordt verwijderd. Wanneer het behandelen van bewaarplaatsen die lange tijd in werking zijn geweest, zou de migratie veel overtollige gegevens kunnen moeten verwerken die door weesversies worden veroorzaakt.

Een nuttige eigenschap voor deze types van situaties is de toevoeging van de `--copy-versions` parameter. Het kan worden gebruikt om de versieknooppunten tijdens migratie of exemplaar van een bewaarplaats over te slaan.

U kunt ook kiezen of u zwevende versies wilt kopiëren door `--copy-orphaned-versions=true` toe te voegen.

Beide parameters ondersteunen ook een datumnotatie `YYYY-MM-DD` voor het geval dat u versies niet later dan een bepaalde datum wilt kopiëren.

![chlimage_1-153](assets/chlimage_1-153.png)

#### Bronversie openen {#open-source-version}

Een open-bronversie van CRX2Oak is beschikbaar in de vorm van eik-verbetering. Alle functies worden ondersteund, met uitzondering van:

* CRX2-ondersteuning
* Ondersteuning voor migratieprofiel
* Ondersteuning voor automatische AEM herconfiguratie

Zie [Apache Documentation](https://jackrabbit.apache.org/oak/docs/migration.html) voor meer informatie.

## Parameters {#parameters}

### Opslagopties knooppunt {#node-store-options}

* `--cache`: Cachegrootte in MB (standaard is  `256`)

* `--mmap`: Toegang tot in geheugen toegewezen bestanden voor Segmentarchief inschakelen
* `--src-password:` Wachtwoord voor de RDB-brondatabase

* `--src-user:` Gebruiker voor de bron-RDB

* `--user`: Gebruiker voor de beoogde RDB

* `--password`: Wachtwoord voor de doel-RDB.

### Migratieopties {#migration-options}

* `--early-shutdown`: Sluit de bron-JCR2-opslagplaats af nadat knooppunten zijn gekopieerd en voordat de haken voor vastleggen zijn toegepast
* `--fail-on-error`: Dwingt een fout van de migratie als de knopen niet van de bronbewaarplaats kunnen worden gelezen.
* `--ldap`: Hiermee migreert u LDAP-gebruikers van een CQ 5.x-instantie naar een op eik gebaseerde instantie. Dit werkt alleen als de Identiteitsprovider in de configuratie Eak een naam heeft. Zie de [LDAP-documentatie](/help/sites-administering/ldap-config.md) voor meer informatie.

* `--ldap-config:` Gebruik dit in combinatie met de  `--ldap` parameter voor CQ 5.x-opslagruimten die meerdere LDAP-servers voor verificatie hebben gebruikt. U kunt het gebruiken om aan CQ 5.x `ldap_login.conf` of `jaas.conf` configuratiedossiers te richten. De notatie is `--ldapconfig=path/to/ldap_login.conf`.

### Opties voor versieopslag {#version-store-options}

* `--copy-orphaned-versions`: Kopiëren van zwevende versies wordt overgeslagen. Ondersteunde parameters zijn: `true`, `false` en `yyyy-mm-dd`. Wordt standaard ingesteld op `true`.

* `--copy-versions:` Kopieert de versieopslag. Parameters: `true`, `false`, `yyyy-mm-dd`. Wordt standaard ingesteld op `true`.

#### Padopties {#path-options}

* `--include-paths:` Lijst met door komma&#39;s gescheiden paden die tijdens het kopiëren moeten worden opgenomen
* `--merge-paths`: Lijst met door komma&#39;s gescheiden paden die tijdens het kopiëren moeten worden samengevoegd
* `--exclude-paths:` Lijst met door komma&#39;s gescheiden paden die tijdens het kopiëren moeten worden uitgesloten.

### Opslagopties bronblob {#source-blob-store-options}

* `--src-datastore:` De datastore-map die als bron moet worden gebruikt  `FileDataStore`

* `--src-fileblobstore`: De datastore-map die als bron moet worden gebruikt  `FileBlobStore`

* `--src-s3datastore`: De datastore-map die moet worden gebruikt voor de bron  `S3DataStore`

* `--src-s3config`: Het configuratiebestand voor de bron  `S3DataStore`.

### Opties {#destination-blobstore-options} voor doelblobStore

* `--datastore:` De datastore-map die als doel moet worden gebruikt  `FileDataStore`

* `--fileblobstore:` De datastore-map die als doel moet worden gebruikt  `FileBlobStore`

* `--s3datastore`: De datastore-map die voor het doel moet worden gebruikt  `S3DataStore`

* `--s3config`: Het configuratiebestand voor het doel  `S3DataStore`.

### Help-opties {#help-options}

* `-?, -h, --help:` Help-informatie weergeven.

## Foutopsporing {#debugging}

U kunt ook foutopsporingsinformatie inschakelen voor het migratieproces om problemen op te lossen die tijdens het proces kunnen optreden. U kunt dit anders doen afhankelijk van de wijze u het hulpmiddel binnen wenst in werking te stellen:

<table>
 <tbody>
  <tr>
   <td><strong>CRX2Oak-modus</strong></td>
   <td><strong>Actie</strong></td>
  </tr>
  <tr>
   <td>Snelstartmodus</td>
   <td>U kunt <strong>-logboek-vlakke TRACE toevoegen </strong> of <strong>-logboek-vlakke DEBUG </strong>opties aan de bevellijn wanneer het runnen van CRX2Oak. In deze modus worden logbestanden automatisch doorgestuurd naar het bestand <strong>upgrade.log</strong>.</td>
  </tr>
  <tr>
   <td>Standalone modus</td>
   <td><p>Voeg de <strong>-spoor</strong> opties aan de CRX2Oak bevellijn toe om de gebeurtenissen van TRACE op standaardoutput te tonen (u moet logboeken opnieuw richten zelf gebruikend redirection karakter: '&gt;' of 'tee' (opdracht voor latere inspectie).</p> </td>
  </tr>
 </tbody>
</table>

## Andere overwegingen {#other-considerations}

Wanneer het migreren aan een MongoDB replicaset, zorg ervoor u de `WriteConcern` parameter aan `2` op alle verbindingen aan de gegevensbestanden van Mongo plaatst.

U kunt dit doen door de `w=2` parameter aan het eind van het verbindingskoord toe te voegen, als dit:

```xml
java -Xmx4092m -XX:MaxPermSize=1024m -jar crx2oak.jar crx-quickstart/repository/ mongodb://localhost:27017/aem-author?replicaset=replica1&w=2
```

>[!NOTE]
>
>Voor meer informatie, zie de documentatie van het Koord van de Verbinding MongoDB op [Schrijf Concerns](https://docs.mongodb.org/manual/reference/connection-string/#write-concern-options).

