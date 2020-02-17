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
translation-type: tm+mt
source-git-commit: 24290b65a126822eb918fbecc978372394b5b655

---


# Het CRX2Oak-migratiehulpprogramma gebruiken{#using-the-crx-oak-migration-tool}

## Inleiding {#introduction}

CRX2Oak is een hulpmiddel dat wordt ontworpen om gegevens tussen verschillende bewaarplaatsen te migreren.

Deze kan worden gebruikt om gegevens van oudere CQ-versies op basis van Apache Jackrabbit 2 te migreren naar eikenhout en kan ook worden gebruikt om gegevens te kopiëren tussen Oak-opslagplaatsen.

U kunt de nieuwste versie van crx2oak downloaden van de openbare opslagplaats van Adobe op deze plaats:[https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/crx2oak/](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/crx2oak/)

De lijst met wijzigingen en correcties voor de nieuwste versie vindt u in de [CRX2Oak Release-notities](https://docs.adobe.com/content/help/en/experience-manager-64/release-notes/crx2oak.html).

>[!NOTE]
>
>Voor meer informatie over Apache Oak en belangrijkste concepten van AEM persistance, zie [Inleiding aan het Platform](/help/sites-deploying/platform.md)AEM.

## Gevallen voor migratiegebruik {#migration-use-cases}

U kunt het gereedschap gebruiken voor:

* Migreren van oudere CQ 5-versies naar AEM 6
* Gegevens kopiëren tussen meerdere eiken-opslagplaatsen
* Gegevens tussen verschillende Oak MicroKernel-implementaties omzetten.

Ondersteuning voor migrerende opslagplaatsen die gebruikmaken van externe blob-opslagplaatsen (beter bekend als Data Stores) wordt in verschillende combinaties geboden. Een mogelijk migratiepad is afkomstig uit een CRX2-opslagplaats die een externe opslagplaats voor eik gebruikt `FileDataStore` met een `S3DataStore`opslagplaats.

In het onderstaande diagram worden alle mogelijke migratiecombinaties weergegeven die door CRX2Oak worden ondersteund:

![chlimage_1-151](assets/chlimage_1-151.png)

## Functies {#features}

CRX2Oak wordt geroepen tijdens verbeteringen AEM op een manier waarin de gebruiker een vooraf bepaald migratieprofiel kan specificeren dat de herconfiguratie van persistentiemodi automatiseert. Dit wordt de snelstartmodus genoemd.

Het kan ook afzonderlijk worden uitgevoerd voor het geval het meer aanpassing vereist. In deze modus worden wijzigingen echter alleen doorgevoerd in de opslagplaats en moet een eventuele aanvullende herconfiguratie van AEM handmatig worden uitgevoerd. Dit wordt de standalone wijze genoemd.

Een ander ding om op te merken is dat met de standaardmontages op standalone wijze, slechts de Opslag van de Knoop zal worden gemigreerd en de nieuwe bewaarplaats zal de oude binaire opslag hergebruiken.

### Automatische QuickStart-modus {#automated-quickstart-mode}

Sinds AEM 6.3 kan CRX2Oak door de gebruiker gedefinieerde migratieprofielen verwerken die kunnen worden geconfigureerd met alle migratieopties die al beschikbaar zijn. Hierdoor is meer flexibiliteit mogelijk en kan de configuratie van AEM worden geautomatiseerd. Functies die niet beschikbaar zijn als u het gereedschap in zelfstandige modus gebruikt.

Als u wilt overschakelen van CRX2Oak naar de snelstartmodus, moet u het pad naar de crx-quickstart-map in de AEM-installatiemap definiëren via deze omgevingsvariabele van het besturingssysteem:

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

Aangepaste Java-logica wordt ook geïmplementeerd met `CommitHooks`. Aangepaste `RepositoryInitializer` klassen kunnen worden geïmplementeerd om de repository te initialiseren met aangepaste waarden.

#### Ondersteuning voor bewerkingen met geheugentoewijzing {#support-for-memory-mapped-operations}

CRX2Oak ondersteunt standaard ook bewerkingen die zijn toegewezen aan het geheugen. Geheugentoewijzing verbetert de prestaties aanzienlijk en moet waar mogelijk worden gebruikt.

>[!CAUTION]
>
>Vergeet echter niet dat bewerkingen met geheugentoewijzing niet worden ondersteund voor Windows-platforms. Daarom wordt geadviseerd om de **-onbruikbaar maken-mmap** parameter toe te voegen wanneer het uitvoeren van de migratie op Vensters.

#### Selectieve migratie van inhoud {#selective-migration-of-content}

Standaard wordt de gehele opslagplaats onder het `"/"` pad gemigreerd. U hebt echter volledige controle over de inhoud die u wilt migreren.

Als er om het even welk deel van de inhoud is die niet op de nieuwe instantie wordt vereist, kunt u de `--exclude-path` parameter gebruiken om de inhoud uit te sluiten en de verbeteringsprocedure te optimaliseren.

#### Pad samenvoegen {#path-merging}

Als gegevens moeten worden gekopieerd tussen twee opslagplaatsen en u hebt een inhoudspad dat op beide instanties verschillend is, kunt u het in de `--merge-path` parameter bepalen. Zodra u, zal CRX2Oak slechts de nieuwe knopen aan de bestemmingsbewaarplaats kopiëren en zal oude op zijn plaats houden.

![chlimage_1-152](assets/chlimage_1-152.png)

#### Versieondersteuning {#version-support}

Standaard maakt AEM een versie van elk knooppunt of elke pagina die wordt gewijzigd en slaat het op in de opslagplaats. De versies kunnen vervolgens worden gebruikt om de pagina in een eerdere staat te herstellen.

Deze versies worden echter nooit leeggemaakt, zelfs niet als de originele pagina wordt verwijderd. Wanneer het behandelen van bewaarplaatsen die lange tijd in werking zijn geweest, zou de migratie veel overtollige gegevens kunnen moeten verwerken die door weesversies worden veroorzaakt.

Een handige functie voor dit soort situaties is de toevoeging van de `--copy-versions` parameter. Het kan worden gebruikt om de versieknooppunten tijdens migratie of exemplaar van een bewaarplaats over te slaan.

U kunt ook kiezen of u zwevende versies wilt kopiëren door deze toe te voegen `--copy-orphaned-versions=true`.

Beide parameters ondersteunen ook een `YYYY-MM-DD` datumnotatie voor het geval dat u versies niet later dan een bepaalde datum wilt kopiëren.

![chlimage_1-153](assets/chlimage_1-153.png)

#### Bronversie openen {#open-source-version}

Een open-bronversie van CRX2Oak is beschikbaar in de vorm van eik-verbetering. Alle functies worden ondersteund, met uitzondering van:

* CRX2-ondersteuning
* Ondersteuning voor migratieprofiel
* Ondersteuning voor automatische AEM-herconfiguratie

Raadpleeg de documentatie bij [Apache](https://jackrabbit.apache.org/oak/docs/migration.html) voor meer informatie.

## Parameters {#parameters}

### Opslagopties knooppunt {#node-store-options}

* `--cache`: Cachegrootte in MB (standaard is `256`)

* `--mmap`: Toegang tot in geheugen toegewezen bestanden voor Segmentarchief inschakelen
* `--src-password:` Wachtwoord voor de RDB-brondatabase

* `--src-user:` Gebruiker voor de bron-RDB

* `--user`: Gebruiker voor de beoogde RDB

* `--password`: Wachtwoord voor de doel-RDB.

### Migratieopties {#migration-options}

* `--early-shutdown`: Sluit de bron-JCR2-opslagplaats af nadat knooppunten zijn gekopieerd en voordat de haken voor vastleggen zijn toegepast
* `--fail-on-error`: Dwingt een fout van de migratie als de knopen niet van de bronbewaarplaats kunnen worden gelezen.
* `--ldap`: Hiermee migreert u LDAP-gebruikers van een CQ 5.x-instantie naar een op eik gebaseerde instantie. Dit werkt alleen als de Identiteitsprovider in de configuratie Eak een naam heeft. Zie de [LDAP-documentatie](/help/sites-administering/ldap-config.md)voor meer informatie.

* `--ldap-config:` Gebruik dit in combinatie met de `--ldap` parameter voor CQ 5.x-opslagruimten die meerdere LDAP-servers voor verificatie hebben gebruikt. U kunt het gebruiken om aan CQ 5.x `ldap_login.conf` of `jaas.conf` configuratiedossiers te richten. De indeling is `--ldapconfig=path/to/ldap_login.conf`.

### Opties voor versieopslag {#version-store-options}

* `--copy-orphaned-versions`: Kopiëren van zwevende versies wordt overgeslagen. Ondersteunde parameters zijn: `true`, `false` en `yyyy-mm-dd`. Wordt standaard ingesteld op `true`.

* `--copy-versions:` Kopieert de versieopslag. Parameters: `true`, `false`, `yyyy-mm-dd`. Wordt standaard ingesteld op `true`.

#### Padopties {#path-options}

* `--include-paths:` Lijst met door komma&#39;s gescheiden paden die tijdens het kopiëren moeten worden opgenomen
* `--merge-paths`: Lijst met door komma&#39;s gescheiden paden die tijdens het kopiëren moeten worden samengevoegd
* `--exclude-paths:` Lijst met door komma&#39;s gescheiden paden die tijdens het kopiëren moeten worden uitgesloten.

### Opslagopties bronblob {#source-blob-store-options}

* `--src-datastore:` De datastore-map die als bron moet worden gebruikt `FileDataStore`

* `--src-fileblobstore`: De datastore-map die als bron moet worden gebruikt `FileBlobStore`

* `--src-s3datastore`: De datastore-map die moet worden gebruikt voor de bron `S3DataStore`

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
   <td><strong>Actie</strong></td>
  </tr>
  <tr>
   <td>Snelstartmodus</td>
   <td>U kunt <strong>-logboek-vlakke SPOOR</strong> of <strong>-logboek-vlakke </strong>opties DEBUG aan de bevellijn toevoegen wanneer het runnen van CRX2Oak. In deze modus worden logbestanden automatisch omgeleid naar het bestand <strong></strong>upgrade.log.</td>
  </tr>
  <tr>
   <td>Standalone modus</td>
   <td><p>Voeg toe <strong>-spoor</strong> opties aan de CRX2Oak bevellijn om de gebeurtenissen van het SPOOR op standaardoutput te tonen (u moet logboeken opnieuw richten zelf gebruikend redirection karakter: '&gt;' of 'tee' (opdracht voor latere inspectie).</p> </td>
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
>Zie de documentatie van de verbindingstekenreeks van MongoDB over [schrijfproblemen](https://docs.mongodb.org/manual/reference/connection-string/#write-concern-options)voor meer informatie.

