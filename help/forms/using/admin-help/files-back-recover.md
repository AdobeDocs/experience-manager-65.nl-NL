---
title: Bestanden waarvan een back-up moet worden gemaakt en die moeten worden hersteld
seo-title: Bestanden waarvan een back-up moet worden gemaakt en die moeten worden hersteld
description: In dit document worden de toepassing en gegevensbestanden beschreven waarvan een back-up moet worden gemaakt.
seo-description: In dit document worden de toepassing en gegevensbestanden beschreven waarvan een back-up moet worden gemaakt.
uuid: ba04adb9-675a-48f2-ad52-39c1266e423b
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 6f9a294d-24bd-4e4b-b929-2809f5e6cef9
translation-type: tm+mt
source-git-commit: 317fadfe48724270e59644d2ed9a90fbee95cf9f

---


# Bestanden waarvan een back-up moet worden gemaakt en die moeten worden hersteld {#files-to-back-up-and-recover}

De toepassing en gegevensbestanden waarvan een back-up moet worden gemaakt, worden in de volgende secties nader beschreven.

Overweeg de volgende punten met betrekking tot back-up en herstel:

* Er moet een back-up van de database worden gemaakt voordat de GDS- en AEM-opslaglocatie wordt gebruikt.
* Als u de knopen in een gegroepeerd gegroepeerd milieu voor steun moet onderdrukken, zorg ervoor dat de slaveknooppunten vóór de hoofdknoop worden gesloten. Anders kan dit leiden tot inconsistentie in de cluster of server. Ook, zou de hoofdknoop vóór om het even welk slave knoop live moeten worden gemaakt.
* Voor de herstelbewerking van een cluster moet de toepassingsserver worden gestopt voor elk knooppunt in de cluster.

## Globale map voor documentopslag {#global-document-storage-directory}

De GDS is een map die wordt gebruikt voor het opslaan van bestanden met een lange levensduur die in een proces worden gebruikt. De levensduur van bestanden met een lange levensduur is bedoeld om een of meer keren een AEM-formuliersysteem te starten en kan dagen en zelfs jaren beslaan. Deze bestanden van lange duur kunnen PDF&#39;s, beleidsregels en formuliersjablonen bevatten. Bestanden met een lange levensduur vormen een essentieel onderdeel van de algemene status van veel implementaties van AEM-formulieren. Als sommige of alle documenten met een lange levensduur verloren gaan of beschadigd raken, kan de formulierserver instabiel worden.

Invoerdocumenten voor asynchrone aanroep van taken worden ook opgeslagen in de GDS en moeten beschikbaar zijn voor het verwerken van aanvragen. Daarom is het belangrijk dat u de betrouwbaarheid van het bestandssysteem dat de GDS host en een redundante array van onafhankelijke schijven (RAID) of andere technologie gebruikt, als geschikt beschouwt voor uw vereisten op het gebied van kwaliteit en serviceniveau.

De locatie van de GDS wordt bepaald tijdens het installatieproces van AEM-formulieren of later met behulp van de beheerconsole. Naast het houden van een high-availability plaats voor GDS, kunt u gegevensbestandopslag voor documenten ook toelaten. Zie [Back-upopties als database wordt gebruikt voor documentopslag](files-back-recover.md#backup-options-when-database-is-used-for-document-storage).

### GDS-locatie {#gds-location}

Als u de locatie-instelling tijdens de installatie leeg laat, wordt de locatie standaard ingesteld op een map onder de installatie van de toepassingsserver. U moet een back-up maken van de volgende map voor uw toepassingsserver:

* (JBoss) `[appserver root]/server/'server'/svcnative/DocumentStorage`
* (WebLogic) `[appserverdomain]/'server'/adobe/AEMformsserver/DocumentStorage`
* (WebSphere) `[appserver root]/installedApps/adobe/'server'/DocumentStorage`

Als u de GDS-locatie hebt gewijzigd in een andere locatie dan de standaardlocatie, kunt u deze als volgt bepalen:

* Meld u aan bij de beheerconsole en klik op Instellingen > Core System Settings > Configurations.
* Registreer de plaats die in het Globale vakje van de Folder van de Opslag van het Document wordt gespecificeerd.

In een gegroepeerd milieu, wijst GDS typisch aan een folder die op het netwerk wordt gedeeld en lees/schrijf toegankelijk voor elke clusterknoop is.

De locatie van de GDS kan tijdens een herstelbewerking worden gewijzigd als de oorspronkelijke locatie niet meer beschikbaar is. (Zie De GDS-locatie [wijzigen tijdens het herstellen](/help/forms/using/admin-help/recovering-aem-forms-data.md#changing-the-gds-location-during-recovery).)

### Back-upopties wanneer database wordt gebruikt voor documentopslag {#backup-options-when-database-is-used-for-document-storage}

U kunt AEM-formulieren documentopslag inschakelen in de AEM-formulierdatabase met behulp van de beheerconsole. Hoewel met deze optie alle permanente documenten in de database blijven staan, is voor AEM-formulieren de op het bestandssysteem gebaseerde GDS-map nog steeds vereist, omdat deze wordt gebruikt voor het opslaan van permanente en tijdelijke bestanden en bronnen met betrekking tot sessies en aanroepen van AEM-formulieren.

Wanneer u de optie &quot;Documentopslag in de database inschakelen&quot; selecteert in de Core System Settings in de beheerconsole of door Configuratiebeheer te gebruiken, staan AEM-formulieren de back-upmodus voor momentopnamen en de schuifmodus niet toe. Daarom hoeft u geen back-upmodi te beheren met AEM-formulieren. Als u deze optie gebruikt, dient u slechts eenmaal een back-up van de GDS te maken nadat u de optie hebt ingeschakeld. Wanneer u AEM-formulieren herstelt van een back-up, hoeft u de naam van de back-upmap voor de GDS niet te wijzigen of de GDS te herstellen.

## AEM-opslagplaats {#aem-repository}

AEM-opslagplaats (crx-repository) wordt gemaakt als crx-repository is geconfigureerd tijdens de installatie van AEM-formulieren. De locatie van de crx-repository directory wordt bepaald tijdens het installatieproces van AEM-formulieren. Back-up en herstel van de AEM-opslagruimte is vereist in combinatie met database en GDS voor consistente AEM-formuliergegevens in AEM-formulieren. De AEM-opslagplaats bevat gegevens voor Correspondence Management Solution, Forms Manager en AEM Forms Workspace.

### Correspondentenbeheeroplossing {#correspondence-management-solution}

De Oplossing van het Beheer van de correspondentie centraliseert en beheert de verwezenlijking, de assemblage en de levering van veilige, gepersonaliseerde, en interactieve correspondentie. Hiermee kunt u snel correspondentie samenstellen van zowel vooraf goedgekeurde als door u geschreven inhoud in een gestroomlijnd proces, van ontwerp tot archivering. Hierdoor krijgen uw klanten actuele, nauwkeurige, handige, veilige en relevante communicatie. Uw bedrijf maximaliseert de waarde van klanteninteractie en minimaliseert kosten en risico met een proces dat voor gemak, snelheid, en productiviteit wordt gestroomlijnd.

Een eenvoudige installatie van een Correspondentenbeheeroplossing bestaat uit een auteurinstantie en een publicatieexemplaar op dezelfde computer of op verschillende computers

### formulierbeheer {#forms-manager}

Met formulierbeheer stroomlijnt u het bijwerken, beheren en verwijderen van formulieren.

### AEM-werkruimte voor formulieren {#html-workspace}

De werkruimte van AEM-formulieren komt overeen met de mogelijkheden van de (Vervangen voor AEM-formulieren in JEE) Flex-werkruimte en voegt nieuwe mogelijkheden toe om de werkruimte uit te breiden en te integreren en deze gebruikersvriendelijker te maken.

>[!NOTE]
>
>De Flex-werkruimte is verouderd voor de release van AEM-formulieren.

Hierdoor is taakbeheer op clients zonder Flash Player en Adobe Reader mogelijk. Hiermee kunt u naast PDF-formulieren en Flex-formulieren ook HTML-formulieren weergeven.

## AEM-formulierdatabase {#aem-forms-database}

In de AEM-formulierdatabase wordt inhoud opgeslagen, zoals formulierartefacten, serviceconfiguraties, processtatus en databasereferenties naar bestanden in de GDS en de hoofdmap voor inhoudsopslag (voor Content Services). De steunen van het gegevensbestand kunnen in echt - tijd zonder een onderbreking in de dienst worden uitgevoerd, en de terugwinning kan op een specifiek punt in tijd of aan een bepaalde verandering zijn. In deze sectie wordt beschreven hoe u uw database zo configureert dat hiervan in real-time een back-up kan worden gemaakt.

Op een behoorlijk gevormd AEM vormensysteem, kunnen de systeembeheerder en de gegevensbestandbeheerder gemakkelijk samenwerken om het systeem aan een verenigbare, bekende staat terug te krijgen.

Als u een back-up van de database in real-time wilt maken, moet u de modus Momentopname gebruiken of uw database configureren voor uitvoering in de opgegeven logmodus. Hierdoor kunnen back-ups van uw databasebestanden worden gemaakt terwijl de database geopend en beschikbaar is voor gebruik. Bovendien bewaart het gegevensbestand zijn terugdraaiing en transactielogboeken wanneer het op deze wijzen loopt.

>[!NOTE]
>
>Adobe® LiveCycle® Content Services ES (Afgekeurd) is een inhoudsbeheersysteem dat met LiveCycle is geïnstalleerd. Hiermee kunnen gebruikers processen ontwerpen, beheren, bewaken en optimaliseren die op mensen zijn gericht. De ondersteuning voor Content Services (Afgekeurd) eindigt op 31-12-2014. Zie [Adobe-productlevenscyclusdocument](https://www.adobe.com/support/products/enterprise/eol/eol_matrix.html). Zie [Inhoudsservices](https://help.adobe.com/en_US/livecycle/9.0/admin_contentservices.pdf)beheren voor informatie over het configureren van Inhoudsservices (afgekeurd).

### DB2 {#db2}

Vorm uw DB2 gegevensbestand om op de wijze van het archieflogboek te lopen.

>[!NOTE]
>
>Als uw AEM-formulieromgeving is geüpgraded vanaf een eerdere versie van AEM-formulieren en DB2 gebruikt, wordt online back-up niet ondersteund. In dit geval moet u AEM-formulieren sluiten en een offlineback-up uitvoeren. Toekomstige versies van AEM-formulieren ondersteunen online back-ups voor klanten van upgrades.

IBM beschikt over een pakket hulpmiddelen en Help-systemen waarmee databasebeheerders hun back-up- en hersteltaken kunnen beheren:

* IBM DB2 Archive Log Accelerator (zie [IBM DB2 Archive Log Accelerator voor z/OS User&#39;s Guide](https://publib.boulder.ibm.com/infocenter/dzichelp/v2r2/topic/com.ibm.db2tools.alc.doc.ug/alcugb20.pdf?noframes=true).)
* IBM DB2 Data Archive Expert (Zie [IBM DB2 Data Archive Expert User&#39;s Guide and Reference](https://publib.boulder.ibm.com/infocenter/mptoolic/v1r0/topic/com.ibm.db2tools.aeu.doc.ug/ahxugb13.pdf?noframes=true).)

DB2 heeft ingebouwde mogelijkheden aan file een gegevensbestand aan de Manager van de Opslag van Tivoli. Met Tivoli Storage Manager kunnen DB2-back-ups worden opgeslagen op andere media of op de lokale vaste schijf.

Voor meer informatie over DB2 gegevensbestandsteun en terugwinning, zie het [Ontwikkelen van een steun en terugwinningsstrategie voor DB2](https://publib.boulder.ibm.com/infocenter/db2luw/v9/index.jsp?topic=/com.ibm.db2.udb.admin.doc/doc/c0005945.htm).

### Oracle {#oracle}

Gebruik back-ups van momentopnamen of configureer de Oracle-database in de archieflogmodus. (Zie [Oracle Backup: Een inleiding](https://www.databasedesign-resource.com/oracle-backup.md).) Ga voor meer informatie over het maken van back-ups en het herstellen van uw Oracle-database naar de volgende sites:

[Oracle Backup and Recovery:](https://www.oracle.com/technetwork/database/features/availability/br-overview-097160.html) Verklaart de concepten steun en terugwinning en de gemeenschappelijkste technieken voor het gebruiken van de Manager van de Terugwinning (RMAN) voor steun, terugwinning, en het melden in detail, evenals het verstrekken van meer informatie over hoe te om een steun en terugwinningsstrategie te plannen.

[Oracle Database Backup and Recovery User&#39;s Guide:](https://download.oracle.com/docs/cd/E11882_01/backup.112/e10642.pdf) Verstrekt diepgaande informatie over architectuur RMAN, steun en terugwinningsconcepten en mechanismen, geavanceerde terugwinningstechnieken zoals punt-in-tijd terugwinning en gegevensbestand flashback eigenschappen, en steun en terugwinningsprestaties het stemmen. Het omvat ook door de gebruiker beheerde back-up en herstel, waarbij gebruik wordt gemaakt van hostbesturingssysteemfaciliteiten in plaats van RMAN. Dit volume is essentieel voor back-up en herstel van geavanceerdere databaseimplementaties en voor geavanceerde herstelscenario&#39;s.

[Oracle Database Backup and Recovery Reference:](https://download.oracle.com/docs/cd/E11882_01/backup.112/e10643.pdf) Verstrekt volledige informatie over syntaxis en semantiek voor alle bevelen RMAN, en beschrijft de gegevensbestandmeningen die voor het melden van steun en terugwinningsactiviteiten beschikbaar zijn.

### SQL Server {#sql-server}

Maak back-ups van momentopnamen of configureer de SQL Server-database voor uitvoering in de transactielogmodus.

SQL de Server verstrekt ook twee steun en terugwinningshulpmiddelen:

* SQL Server Management Studio (GUI)
* T-SQL (opdrachtregel)

Zie [Back-](https://articles.techrepublic.com.com/5100-1035_61-1043671.md)upstrategieën en [Back-up en herstel](https://msdn.microsoft.com/en-us/library/ms187048(v=SQL.90).aspx).

### MySQL {#mysql}

Gebruik MySQLAdmin of wijzig de INI dossiers in Vensters om uw gegevensbestand te vormen MySQL om op binaire logboekwijze te lopen. (Zie [MySQL binaire logboekregistratie](https://dev.mysql.com/doc/refman/5.1/en/binary-log.html).) Een hot backup-hulpprogramma voor MySQL is ook beschikbaar in de InnoBase-software. (Zie [Innobase Hot Backup](https://www.innodb.com/hot-backup/features.md).)

**Opmerking**: *De standaard binaire registrerenwijze voor MySQL is &quot;Verklaring&quot;, die met lijsten onverenigbaar is die door de Diensten van de Inhoud (Vervangen) worden gebruikt. Het gebruiken van binair het registreren op deze standaardwijze veroorzaakt de Diensten van de Inhoud (Vervangen) om te ontbreken. Als uw systeem Inhoudsdiensten (Afgekeurd) omvat, gebruik &quot;Gemengd&quot;registrerenwijze. Om het &quot;Gemengd&quot;registreren toe te laten, voeg het volgende argument aan het my.ini- dossier toe:*
`binlog_format=mixed log-bin=logname`

U kunt het mysqldump-hulpprogramma gebruiken om de volledige databaseback-up te verkrijgen. Volledige back-ups zijn vereist, maar ze zijn niet altijd handig. Ze produceren grote back-upbestanden en het genereren van tijd neemt veel tijd in beslag. Als u een incrementele back-up wilt maken, moet u de server starten met de optie - `log-bin` zoals beschreven in de vorige sectie. Telkens als de server MySQL opnieuw begint, houdt het het schrijven aan het huidige binaire logboek op, leidt tot nieuwe en, van toen, wordt nieuwe. U kunt een schakelaar manueel met het `FLUSH LOGS SQL` bevel dwingen. Na de eerste volledige back-up worden de volgende incrementele back-ups uitgevoerd met behulp van het mysqladmin-hulpprogramma met de `flush-logs` opdracht, waarmee het volgende logbestand wordt gemaakt.

Zie Overzicht [van](https://dev.mysql.com/doc/refman/5.5/en/backup-strategy-summary.html)back-upstrategie.

```as3
binlog_format=mixed
log-bin=logname
```

## Content Storage Root-directory (alleen Content Services) {#content-storage-root-directory-content-services-only}

De map Content Storage Root bevat de opslagruimte Content Services (Afgekeurd) waar alle documenten, artefacten en indexen zijn opgeslagen. Er moet een back-up worden gemaakt van de boomstructuur van de directory met de opslaghoofdmap voor inhoud. In deze sectie wordt beschreven hoe u de locatie van de hoofdmap voor inhoudsopslag voor zelfstandige en geclusterde omgevingen kunt bepalen.

### Locatie van opslaghoofdmap voor inhoud (zelfstandige omgeving) {#content-storage-root-location-stand-alone-environment}

De hoofdmap voor inhoudsopslag wordt gemaakt wanneer Content Services (Afgekeurd) is geïnstalleerd. De locatie van de hoofdmap voor inhoudsopslag wordt bepaald tijdens het installatieproces van AEM-formulieren.

De standaardlocatie voor de hoofdmap van de inhoudsopslag is `[aem-forms root]/lccs_data`.

Maak een back-up van de volgende mappen in de hoofdmap van de inhoudsopslagruimte:

/audit.contentstore

/contentStore

/contentstore.deleted

/backup-lucene-indexen

Als de /backup-lucene-indexes folder niet aanwezig is, file de /lucene-indexes folder, die ook in de folder van de Root van de Opslag van de Inhoud wordt gevestigd. Als de /backup-lucene-indexes folder aanwezig is, maak geen file de /lucene-indexes folder omdat het fouten kan veroorzaken.

### Hoofdlocatie voor opslag van inhoud (geclusterde omgeving) {#content-storage-root-location-clustered-environment}

Wanneer u Content Services (Afgekeurd) installeert in een geclusterde omgeving, wordt de hoofdmap van de inhoudsopslagruimte gesplitst in twee aparte mappen:

**Basismap voor inhoudsopslag:** Gewoonlijk een gedeelde netwerkmap die lees-/schrijftoegankelijk is voor alle knooppunten in de cluster

**Basismap index:** Een map die op elk knooppunt in de cluster is gemaakt en die altijd hetzelfde pad en dezelfde mapnaam heeft

De standaardlocatie voor de hoofdmap van de inhoudsopslagruimte is `[GDS root]/lccs_data`, waar `[GDS root]` is de locatie die wordt beschreven in de [GDS-locatie](files-back-recover.md#gds-location). Maak een back-up van de volgende mappen in de hoofdmap van de inhoudsopslagruimte:

/audit.contentstore

/contentStore

/contentstore.deleted

/backup-lucene-indexen

Als de /backup-lucene-indexes folder niet aanwezig is, file de /lucene-indexes folder, die ook in de folder van de Root van de Opslag van de Inhoud wordt gevestigd. Als de /backup-lucene-indexes folder aanwezig is, maak geen file de /lucene-indexes folder omdat het fouten kan veroorzaken.

De standaardlocatie voor de hoofdmap van de index staat `[aem-forms root]/lucene-indexes` op elk knooppunt.

## Door de klant geïnstalleerde lettertypen {#customer-installed-fonts}

Als u extra lettertypen hebt geïnstalleerd op uw AEM-formulieromgeving, moet u er een afzonderlijk back-up van maken. Maak een back-up van alle mappen met lettertypen die in de beheerconsole zijn opgegeven onder Instellingen > Core System > Configurations. Zorg ervoor dat u een back-up maakt van de volledige lettertypemap.

>[!NOTE]
>
>De Adobe-lettertypen die met AEM-formulieren zijn geïnstalleerd, bevinden zich standaard in de `[aem-forms root]/fonts` map.

Als u het besturingssysteem op de hostcomputer opnieuw initialiseert en u de lettertypen van het vorige besturingssysteem wilt gebruiken, moet ook een back-up worden gemaakt van de inhoud van de systeemmap met lettertypen. (Raadpleeg de documentatie bij het besturingssysteem voor specifieke instructies.)
