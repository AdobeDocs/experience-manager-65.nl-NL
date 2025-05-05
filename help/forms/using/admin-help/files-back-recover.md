---
title: Bestanden waarvan een back-up moet worden gemaakt en die moeten worden hersteld
description: In dit document worden de toepassing en gegevensbestanden beschreven waarvan een back-up moet worden gemaakt.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: d2dd381d-a7d2-4fec-a8ba-7ca037fd9dc1
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 6a9806d8f40f711a610c130c63d9ab9b2460d075
workflow-type: tm+mt
source-wordcount: '2029'
ht-degree: 0%

---

# Bestanden waarvan een back-up moet worden gemaakt en die moeten worden hersteld {#files-to-back-up-and-recover}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

De toepassings- en gegevensbestanden waarvan een back-up moet worden gemaakt, worden in de volgende secties gedetailleerder beschreven.

Overweeg de volgende punten met betrekking tot back-up en herstel:

* Er moet een back-up van de database worden gemaakt voordat de GDS en AEM opslagplaats worden gebruikt.
* Als u de knopen in een gegroepeerd gegroepeerd milieu voor steun moet onderdrukken, zorg ervoor dat de secundaire knopen vóór de primaire knoop worden gesloten. Anders kan dit leiden tot inconsistentie in de cluster of server. Ook, zou de primaire knoop vóór om het even welk secundair knooppunt levend moeten worden gemaakt.
* Voor de herstelbewerking van een cluster moet de toepassingsserver worden gestopt voor elk knooppunt in de cluster.

## Globale map voor documentopslag {#global-document-storage-directory}

De GDS is een map die wordt gebruikt voor het opslaan van bestanden met een lange levensduur die in een proces worden gebruikt. De levensduur van bestanden met een lange levensduur moet een of meer keren worden gestart met een AEM formuliersysteem en kan dagen en zelfs jaren beslaan. Deze bestanden van lange duur kunnen PDF, beleidsregels en formuliersjablonen bevatten. Bestanden met een lange levensduur vormen een essentieel onderdeel van de algemene status van veel AEM formulieren. Als sommige of alle documenten met een lange levensduur verloren gaan of beschadigd raken, kan de Forms-server instabiel worden.

Invoerdocumenten voor asynchrone aanroep van taken worden ook opgeslagen in de GDS en moeten beschikbaar zijn voor het verwerken van aanvragen. Daarom is het belangrijk dat u de betrouwbaarheid van het bestandssysteem dat de GDS host en een redundante array van onafhankelijke schijven (RAID) of andere technologie gebruikt, als geschikt beschouwt voor uw vereisten op het gebied van kwaliteit en serviceniveau.

De locatie van de GDS wordt bepaald tijdens het installatieproces van AEM formulieren of later met behulp van de beheerconsole. Naast het houden van een high-availability plaats voor GDS, kunt u gegevensbestandopslag voor documenten ook toelaten. Zie [ Reservekopties wanneer het gegevensbestand voor documentopslag ](files-back-recover.md#backup-options-when-database-is-used-for-document-storage) wordt gebruikt.

### GDS-locatie {#gds-location}

Als u de locatie-instelling tijdens de installatie leeg laat, wordt de locatie standaard ingesteld op een map onder de installatie van de toepassingsserver. Maak een back-up van de volgende map voor uw toepassingsserver:

* (JBoss) `[appserver root]/server/'server'/svcnative/DocumentStorage`
* (WebLogic) `[appserverdomain]/'server'/adobe/AEMformsserver/DocumentStorage`
* (WebSphere) `[appserver root]/installedApps/adobe/'server'/DocumentStorage`

Als u de GDS-locatie hebt gewijzigd in een andere locatie dan de standaardlocatie, kunt u deze als volgt bepalen:

* Meld u aan bij de beheerconsole en klik op Instellingen > Core System Settings > Configurations.
* Registreer de plaats die in het Globale vakje van de Folder van de Opslag van het Document wordt gespecificeerd.

In een gegroepeerd milieu, wijst GDS typisch aan een folder die op het netwerk wordt gedeeld en lees/schrijf toegankelijk voor elke clusterknoop is.

De locatie van de GDS kan tijdens een herstelbewerking worden gewijzigd als de oorspronkelijke locatie niet meer beschikbaar is. (Zie [ Veranderend de plaats GDS tijdens terugwinning ](/help/forms/using/admin-help/recovering-aem-forms-data.md#changing-the-gds-location-during-recovery).)

### Back-upopties wanneer database wordt gebruikt voor documentopslag {#backup-options-when-database-is-used-for-document-storage}

U kunt AEM formulierdocumentopslag inschakelen in de AEM formulierdatabase met behulp van de beheerconsole. Hoewel met deze optie alle permanente documenten in de database blijven staan, is voor AEM formulieren de op het bestandssysteem gebaseerde GDS-map nog steeds vereist, omdat deze wordt gebruikt voor het opslaan van permanente en tijdelijke bestanden en bronnen die verband houden met sessies en aanroepen van AEM formulieren.

Wanneer u de optie &quot;Documentopslag in de database inschakelen&quot; selecteert in de Core System Settings in de beheerconsole of door Configuration Manager te gebruiken, staan AEM formulieren de back-upmodus voor momentopnamen en de schuifmodus niet toe. Daarom hoeft u de back-upmodi niet te beheren met AEM formulieren. Als u deze optie gebruikt, dient u slechts eenmaal een back-up van de GDS te maken nadat u de optie hebt ingeschakeld. Wanneer u AEM formulieren herstelt van een back-up, hoeft u de naam van de back-upmap voor de GDS niet te wijzigen of GDS te herstellen.

## AEM {#aem-repository}

AEM opslagplaats (crx-gegevensopslagplaats) wordt gecreeerd als crx-bewaarplaats tijdens het installeren van AEM vormen wordt gevormd. De locatie van de crx-repository directory wordt bepaald tijdens het installatieproces van AEM formulieren. AEM back-up en herstel in de opslagplaats is vereist in combinatie met database en GDS voor consistente AEM formuliergegevens in AEM formulieren. AEM opslagplaats bevat gegevens voor Correspondence Management Solution, Forms Manager en AEM Forms Workspace.

### Correspondentenbeheeroplossing {#correspondence-management-solution}

De Oplossing van het Beheer van de correspondentie centraliseert en beheert de verwezenlijking, de assemblage en de levering van veilige, gepersonaliseerde, en interactieve correspondentie. Hiermee kunt u snel correspondentie samenstellen van zowel vooraf goedgekeurde als door u geschreven inhoud in een gestroomlijnd proces, van ontwerp tot archivering. Hierdoor krijgen uw klanten actuele, nauwkeurige, handige, veilige en relevante communicatie. Uw bedrijf maximaliseert de waarde van klanteninteractie en minimaliseert kosten en risico met een proces dat voor gemak, snelheid, en productiviteit wordt gestroomlijnd.

Een eenvoudige installatie van een Correspondentenbeheeroplossing bestaat uit een auteurinstantie en een publicatieexemplaar op dezelfde computer of op verschillende computers

### formulierbeheer {#forms-manager}

Met formulierbeheer stroomlijnt u het bijwerken, beheren en verwijderen van formulieren.

### AEM Forms Workspace {#html-workspace}

AEM Forms Workspace past de mogelijkheden van de (Vervangen voor AEM formulieren op JEE) Flex Workspace aan en voegt nieuwe mogelijkheden toe om Workspace uit te breiden en te integreren en het gebruiksvriendelijker te maken.

>[!NOTE]
>
>De Flex-werkruimte is verouderd voor AEM formulierrelease.

Hierdoor is taakbeheer op clients zonder Flash Player en Adobe Reader mogelijk. Het vergemakkelijkt de uitvoering van HTML Forms, naast PDF forms en Flex-formulieren.

## AEM formulierdatabase {#aem-forms-database}

In de database met AEM formulieren wordt inhoud opgeslagen, zoals formulierartefacten, serviceconfiguraties, processtatus en databaseverwijzingen naar bestanden in de GDS en de hoofdmap voor inhoudsopslag (voor Content Services). De steunen van het gegevensbestand kunnen in echt - tijd zonder een onderbreking in de dienst worden uitgevoerd, en de terugwinning kan op een specifiek punt in tijd of aan een bepaalde verandering zijn. In deze sectie wordt beschreven hoe u uw database zo configureert dat hiervan in real-time een back-up kan worden gemaakt.

Op een behoorlijk gevormd AEM vormensysteem, kunnen de systeembeheerder en de gegevensbestandbeheerder gemakkelijk samenwerken om het systeem aan een verenigbare, bekende staat terug te krijgen.

Als u een back-up van de database in real-time wilt maken, moet u de modus Momentopname gebruiken of uw database configureren voor uitvoering in de opgegeven logmodus. Hierdoor kunnen back-ups van uw databasebestanden worden gemaakt terwijl de database geopend en beschikbaar is voor gebruik. Bovendien bewaart het gegevensbestand zijn terugdraaiing en transactielogboeken wanneer het op deze wijzen loopt.

>[!NOTE]
>
>Adobe® LiveCycle® Content Services ES (Afgekeurd) is een contentbeheersysteem dat met LiveCycle is geïnstalleerd. Hiermee kunnen gebruikers processen ontwerpen, beheren, bewaken en optimaliseren die op mensen zijn gericht. De ondersteuning voor Content Services (Afgekeurd) eindigt op 31-12-2014. Zie {het document van de de levenscyclus van het 0} product van de Adobe [&#128279;](https://www.adobe.com/support/products/enterprise/eol/eol_matrix.html).

### DB2 {#db2}

Vorm uw DB2 gegevensbestand om op de wijze van het archieflogboek te lopen.

>[!NOTE]
>
>Als de omgeving van uw AEM formulieren is geüpgraded vanaf een eerdere versie van AEM formulieren en DB2 gebruikt, wordt online back-up niet ondersteund. In dit geval moet u AEM formulieren sluiten en een offlineback-up uitvoeren. Toekomstige versies van AEM formulieren ondersteunen online back-ups voor klanten van upgrades.

IBM beschikt over een reeks tools en Help-systemen waarmee databasebeheerders hun back-up- en hersteltaken kunnen beheren:

* IBM DB2 Archive Log Accelerator
* IBM DB2-expert op het gebied van gegevensarchivering

DB2 heeft ingebouwde mogelijkheden aan file een gegevensbestand aan de Manager van de Opslag van Tivoli. Met Tivoli Storage Manager kunnen DB2-back-ups worden opgeslagen op andere media of op de lokale vaste schijf.

### Oracle {#oracle}

Maak back-ups van momentopnamen of configureer de database van het Oracle voor uitvoering in de archieflogmodus. (Zie [ Steun van het Oracle: Een Inleiding ](https://www.databasedesign-resource.com/oracle-backup.md).) Voor meer informatie over het steunen van en het terugkrijgen van uw gegevensbestand van het Oracle, ga naar deze plaatsen:

[ de Steun en Terugwinning van het Oracle:](https://www.oracle.com/technetwork/database/features/availability/br-overview-097160.html) Verklaart de concepten steun en terugwinning en de gemeenschappelijkste technieken om de Manager van de Terugwinning (RMAN) voor steun, terugwinning, en rapportering meer in detail te gebruiken, en het verstrekken van meer informatie over hoe te om een steun en terugwinningsstrategie te plannen.

{de Gids van de Gebruiker van het Gegevensbestand van 0} Oracle en van de Terugwinning:[&#128279;](https://download.oracle.com/docs/cd/E11882_01/backup.112/e10642.pdf) verstrekt diepgaande informatie over architectuur RMAN, steun en terugwinningsconcepten en mechanismen, geavanceerde terugwinningstechnieken zoals punt-in-tijd terugwinning en gegevensbestand flashback eigenschappen, en steun en terugwinningsprestaties het stemmen.  Het omvat ook door de gebruiker beheerde back-up en herstel, waarbij gebruik wordt gemaakt van hostbesturingssysteemfaciliteiten in plaats van RMAN. Dit volume is essentieel voor back-up en herstel van geavanceerdere databaseimplementaties en voor geavanceerde herstelscenario&#39;s.

[ de Steun en Verwijzing van het Gegevensbestand van het Oracle:](https://download.oracle.com/docs/cd/E11882_01/backup.112/e10643.pdf) verstrekt volledige informatie over syntaxis en semantiek voor alle bevelen RMAN, en beschrijft de gegevensbestandmeningen die voor het melden van steun en terugwinningsactiviteiten beschikbaar zijn.

### SQL Server {#sql-server}

Maak back-ups van momentopnamen of configureer de SQL Server-database voor uitvoering in de transactielogmodus.

SQL de Server verstrekt ook twee steun en terugwinningshulpmiddelen:

* SQL Server Management Studio (GUI)
* T-SQL (opdrachtregel)

Voor meer informatie, zie [ Steun en herstel ](https://msdn.microsoft.com/en-us/library/ms187048(v=SQL.90).aspx).

### MySQL {#mysql}

Gebruik MySQLAdmin of wijzig de INI dossiers in Vensters om uw gegevensbestand te vormen MySQL om op binaire logboekwijze te lopen. (Zie [ Binair registreren MySQL ](https://dev.mysql.com/doc/refman/5.1/en/binary-log.html).) Een heet reservehulpmiddel voor MySQL is ook beschikbaar bij software InnoBase. (Zie [ Innobase hete Steun ](https://www.innodb.com/hot-backup/features.md).)

>[!NOTE]
>
>De standaard binaire registrerenwijze voor MySQL is &quot;Verklaring&quot;, die met lijsten onverenigbaar is die door de Diensten van de Inhoud (Vervangen) worden gebruikt. Het gebruiken van binair het registreren op deze standaardwijze veroorzaakt de Diensten van de Inhoud (Vervangen) om te ontbreken. Als uw systeem Inhoudsdiensten (Afgekeurd) omvat, gebruik &quot;Gemengd&quot;registrerenwijze. Als u &#39;Gemengd&#39; logbestand wilt inschakelen, voegt u het volgende argument toe aan het bestand my.ini: `binlog_format=mixed log-bin=logname`

U kunt het mysqldump-hulpprogramma gebruiken om de volledige back-up van de database te verkrijgen. Volledige back-ups zijn vereist, maar ze zijn niet altijd handig. Ze produceren grote back-upbestanden en het genereren van tijd duurt langer. Als u een incrementele back-up wilt maken, moet u de server starten met de optie - `log-bin` , zoals beschreven in de vorige sectie. Telkens als de server MySQL opnieuw begint, houdt het het schrijven aan het huidige binaire logboek op, leidt tot nieuwe en, van toen, wordt nieuwe. U kunt een schakelaar manueel met het `FLUSH LOGS SQL` bevel dwingen. Na de eerste volledige back-up worden de volgende incrementele back-ups uitgevoerd met behulp van het mysqladmin-hulpprogramma met de opdracht `flush-logs` , waarmee het volgende logbestand wordt gemaakt.

Zie [ Samenvatting van de Strategie van de Steun ](https://dev.mysql.com/doc/refman/5.5/en/backup-strategy-summary.html).

```text
binlog_format=mixed
log-bin=logname
```

## Content Storage Root-directory (alleen Content Services) {#content-storage-root-directory-content-services-only}

De map Content Storage Root bevat de opslagruimte Content Services (Afgekeurd) waar alle documenten, artefacten en indexen zijn opgeslagen. Er moet een back-up worden gemaakt van de boomstructuur van de directory met de opslaghoofdmap voor inhoud. In deze sectie wordt beschreven hoe u de locatie van de hoofdmap voor inhoudsopslag voor zelfstandige en geclusterde omgevingen kunt bepalen.

### Locatie van opslaghoofdmap voor inhoud (zelfstandige omgeving) {#content-storage-root-location-stand-alone-environment}

De hoofdmap voor inhoudsopslag wordt gemaakt wanneer Content Services (Afgekeurd) is geïnstalleerd. De locatie van de hoofdmap voor inhoudsopslag wordt bepaald tijdens het installatieproces van AEM formulieren.

De standaardlocatie voor de hoofdmap van de inhoudsopslag is `[aem-forms root]/lccs_data` .

Maak een back-up van de volgende mappen in de hoofdmap van de inhoudsopslagruimte:

/audit.contentstore

/contentStore

/contentstore.deleted

/backup-lucene-indexen

Als de /backup-lucene-indexes folder niet aanwezig is, file de /lucene-indexes folder, ook in de folder van de Root van de Opslag van de Inhoud. Als de /backup-lucene-indexes folder aanwezig is, maak geen file de /lucene-indexes folder omdat het fouten kan veroorzaken.

### Hoofdlocatie voor opslag van inhoud (geclusterde omgeving) {#content-storage-root-location-clustered-environment}

Wanneer u Content Services (Afgekeurd) installeert in een geclusterde omgeving, wordt de hoofdmap van de inhoudsopslagruimte gesplitst in twee aparte mappen:

**de folder van de Root van de Opslag van de Inhoud:** Typisch, een gedeelde netwerkfolder die lees/schrijf toegankelijk voor alle knopen in de cluster is

**de folder van de Root van de Index:** een folder die op elke knoop in de cluster wordt gecreeerd, altijd hebbend de zelfde weg en foldernaam

De standaardplaats voor de folder van de Root van de Opslag van de Inhoud is `[GDS root]/lccs_data`, waar `[GDS root]` de plaats is die in [ wordt beschreven GDS plaats ](files-back-recover.md#gds-location). Maak een back-up van de volgende mappen in de hoofdmap van de inhoudsopslagruimte:

/audit.contentstore

/contentStore

/contentstore.deleted

/backup-lucene-indexen

Als de /backup-lucene-indexes folder niet aanwezig is, file de /lucene-indexes folder, ook in de folder van de Root van de Opslag van de Inhoud. Als de /backup-lucene-indexes folder aanwezig is, maak geen file de /lucene-indexes folder omdat het fouten kan veroorzaken.

De standaardlocatie voor de hoofdmap van de index is `[aem-forms root]/lucene-indexes` voor elk knooppunt.

## Door de klant geïnstalleerde lettertypen {#customer-installed-fonts}

Als u aanvullende lettertypen hebt geïnstalleerd op uw AEM, moet u er een afzonderlijk back-up van maken. Maak een back-up van alle mappen met Adoben en klantlettertypen die in de beheerconsole zijn opgegeven onder Instellingen > Core System > Configurations. Zorg ervoor dat u een back-up maakt van de volledige lettertypemap.

>[!NOTE]
>
>Standaard staan de Adobe van lettertypen die met AEM formulieren zijn geïnstalleerd in de map `[aem-forms root]/fonts` .

Als u het besturingssysteem op de hostcomputer opnieuw initialiseert en u de lettertypen van het vorige besturingssysteem wilt gebruiken, moet ook een back-up worden gemaakt van de inhoud van de systeemmap met lettertypen. (Raadpleeg de documentatie bij het besturingssysteem voor specifieke instructies.)
