---
title: Back-up- en herstelstrategie voor AEM formulieren
seo-title: Back-up- en herstelstrategie voor AEM formulieren
description: Leer hoe u een strategie implementeert voor het maken van back-ups van gegevens en hoe u ervoor zorgt dat deze consistent blijft met de AEM formuliergegevens.
seo-description: Leer hoe u een strategie implementeert voor het maken van back-ups van gegevens en hoe u ervoor zorgt dat deze consistent blijft met de AEM formuliergegevens.
uuid: 98fc3115-76e5-4e58-aa30-3601866a441f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: f192a8a3-1116-4d32-9b57-b53d532c0dbf
translation-type: tm+mt
source-git-commit: b703c59d7d913fc890c713c6e49e7d89211fd998
workflow-type: tm+mt
source-wordcount: '1520'
ht-degree: 0%

---


# Back-up- en herstelstrategie voor AEM formulieren{#backup-and-recovery-strategy-for-aem-forms}

Als in de implementatie van uw AEM aanvullende aangepaste gegevens worden opgeslagen in een andere database, bent u verantwoordelijk voor het implementeren van een strategie om back-ups van deze gegevens te maken en ervoor te zorgen dat deze consistent blijven met de AEM formuliergegevens. Bovendien moet de toepassing zo zijn ontworpen dat deze robuust genoeg is om een scenario af te handelen waarbij de extra databases niet meer synchroon zijn. Het wordt hoogst geadviseerd dat om het even welke gegevensbestandverrichting die wordt uitgevoerd in de context van een transactie wordt gedaan helpen een verenigbare staat handhaven.

Nadat u hebt vastgesteld hoe AEM formulieren worden gebruikt, bepaalt u welke bestanden een back-up moeten maken, hoe vaak en welk back-upvenster beschikbaar moet worden gemaakt.

>[!NOTE]
>
>Net als bij elk ander aspect van de implementatie van uw AEM formulieren, moet uw back-up- en herstelstrategie worden ontwikkeld en getest in een ontwikkelings- of testomgeving voordat deze in de productie wordt gebruikt, om ervoor te zorgen dat de volledige oplossing werkt zoals u had verwacht zonder gegevensverlies.

Adobe Experience Manager (AEM) maakt integrerend deel uit van AEM formulieren. Daarom moet u AEM ook synchroniseren met AEM formulieren voor back-ups, zoals Correspondence Management Solution en -services, zoals formulierbeheer, zijn gebaseerd op gegevens die zijn opgeslagen in AEM deel van AEM formulieren.Om gegevensverlies te voorkomen, moeten de AEM specifieke gegevens worden opgeslagen op een manier die ervoor zorgt dat GDS en AEM (opslagplaats) correleren met databasereferenties.De directory&#39;s database, GDS, AEM en Content Storage Root moeten worden hersteld naar een DNS op dezelfde computer Geef het origineel een naam.

## Typen back-ups {#types-of-backups}

De back-upstrategie voor AEM formulieren omvat twee typen back-ups:

**Systeemimage:** een volledige systeemback-up die u kunt gebruiken om de inhoud van uw computer te herstellen als de vaste schijf of de volledige computer niet meer werkt. Een back-up van het systeemimage is alleen nodig voordat AEM formulieren worden geïmplementeerd. Het interne bedrijfsbeleid bepaalt dan hoe vaak de steunen van het systeembeeld worden vereist.

**AEM formulieren, specifieke gegevens:** toepassingsgegevens bestaan in database, GDS (Global Document Storage) en AEM opslagruimte en moeten in real-time worden opgeslagen. GDS is een map waarin bestanden van lange duur worden opgeslagen die in een proces worden gebruikt. Deze bestanden kunnen PDF&#39;s, beleidsregels of formuliersjablonen bevatten.

>[!NOTE]
>
>Als Content Services (Afgekeurd) is geïnstalleerd, maakt u ook een back-up van de hoofdmap van de Content Storage Root. Zie [Inhoudsopslaghoofdmap (alleen inhoudsservices)](/help/forms/using/admin-help/files-back-recover.md#content-storage-root-directory-content-services-only).

De database wordt gebruikt om formulierartefacten, serviceconfiguraties, processtatus en databaseverwijzingen naar GDS-bestanden op te slaan. Als u de opslag van documenten in de database hebt ingeschakeld, worden permanente gegevens en documenten in de GDS ook in de database opgeslagen. U kunt een back-up van de database maken en deze herstellen met de volgende methoden:

* **De** backupmodus voor momentopnamen geeft aan dat de back-upmodus van het AEM oneindig of gedurende een bepaald aantal minuten is geactiveerd, waarna de back-upmodus niet meer is ingeschakeld. U kunt een van de volgende opties gebruiken om de back-upmodus voor momentopnamen in of uit te schakelen. Na een terugwinningsscenario, zou de wijze van de momentopname steun niet moeten worden toegelaten.

   * Gebruik de pagina Back-upinstellingen in de beheerconsole. Schakel het selectievakje Bewerken in veilige back-upmodus in om de modus voor momentopnamen in te schakelen. Schakel het selectievakje uit om de modus voor momentopnamen af te sluiten.
   * Gebruik het script LCBackupMode (zie [Een back-up maken van de database, GDS en de mappen Root voor inhoudsopslag](/help/forms/using/admin-help/backing-aem-forms-data.md#back-up-the-database-gds-aem-repository-and-content-storage-root-directories)). Als u de back-upmodus voor momentopnamen wilt afsluiten, stelt u in het scriptargument de parameter `continuousCoverage` in op `false` of gebruikt u de optie `leaveContinuousCoverage`.
   * Gebruik de meegeleverde API voor back-up/herstel. <!-- Fix broken link(see AEM forms API Reference section on AEM Forms Help and Tutorials page).-->

* **Rolling** backupmode wijst erop dat het systeem altijd in reservewijze is, met een nieuwe reservewijzesessie die wordt in werking gesteld zodra de vorige zitting wordt vrijgegeven. Er is geen time-out gekoppeld aan de schuifmodus. Wanneer het manuscript LCBackupMode of APIs worden geroepen om het rollen reservewijze te verlaten, begint een nieuwe het rollen reservewijze zitting. Deze modus is handig voor het ondersteunen van continue back-ups, maar nog steeds voor het verwijderen van oude en overbodige documenten uit de GDS-directory. De modus Rolling Backup wordt niet ondersteund via de pagina Backup and Recovery. Na een terugwinningsscenario, wordt het rollen reservewijze nog toegelaten. U kunt de modus voor continue back-up (schuivende back-upmodus) verlaten door het LCBackupMode-script te gebruiken met de optie `leaveContinuousCoverage`.

>[!NOTE]
>
>Als u de schuifmodus onmiddellijk verlaat, wordt een nieuwe back-upmodussessie gestart. Om het rollen reservewijze volledig onbruikbaar te maken, gebruik `leaveContinuousCoverage` optie in het manuscript, dat de bestaande het rollen reservezitting beschrijft. In de back-upmodus voor momentopnamen kunt u de back-upmodus zoals gewoonlijk verlaten.

Om gegevensverlies te voorkomen, moeten de specifieke gegevens van de AEM formulieren op een manier worden gesteund die ervoor zorgt dat de GDS en de documenten van de Root van de Opslag van de Inhoud met gegevensbestandverwijzingen correleren.

>[!NOTE]
>
>Wanneer de GDS is opgeslagen in het bestandssysteem en niet in de database, voert u de databaseback-up uit vóór de GDS-back-up.

## Speciale overwegingen voor back-up en herstel {#special-considerations-for-backup-and-recovery}

Gebruik de volgende richtlijnen als u AEM formulieren in een andere omgeving moet herstellen vanwege de volgende wijzigingen:

* Wijziging in het IP-adres, de hostnaam of de poort van de AEM formulierserver
* Wijziging in de stationsletters of het directorypad
* Wijzigen in een andere databasehost, -poort of -naam

Dergelijke herstelscenario&#39;s worden doorgaans veroorzaakt door hardwarestoringen van de server die de toepassingsserver, databaseserver of formulierserver host. Naast de AEM formulieren-specifieke configuraties die in deze sectie worden beschreven, zou u ook de noodzakelijke veranderingen voor andere delen van de plaatsing van AEM vormen zoals ladingsbalancers en firewalls moeten aanbrengen, als hostname of IP adres van een AEM vormenserver verandert.

### Wat kan niet worden gewijzigd {#what-cannot-be-changed}

Hoewel u de databaseserver en veel andere parameters kunt wijzigen, kunt u het servertype of databasetype van de toepassing niet wijzigen wanneer u AEM formulieren uit een back-up terugzet. Als u bijvoorbeeld een back-up van AEM formulieren herstelt, kunt u de toepassingsserver niet van JBoss naar WebLogic of van de database wijzigen van Oracle naar DB2. Bovendien moeten herstelde AEM dezelfde bestandsysteempaden gebruiken, zoals de map met lettertypen.

### Opnieuw opstarten na herstel {#restarting-after-a-recovery}

Ga als volgt te werk voordat u de formulierserver opnieuw start na een herstelbewerking:

1. Start het systeem in de onderhoudsmodus.
1. Ga als volgt te werk om ervoor te zorgen dat Form Manager wordt gesynchroniseerd met AEM formulieren in de onderhoudsmodus:

   1. Ga naar https://&lt;*server*>:&lt;*poort*/lc/fm en meld u aan met behulp van de referenties Beheerder/wachtwoord.
   1. Klik op de naam van de gebruiker (in dit geval Super Administrator) in de rechterbovenhoek.
   1. Klik **Beheeropties**.
   1. Klik **Start** om elementen van de opslagplaats te synchroniseren.

1. In een gegroepeerd milieu, zou de primaire knoop (met betrekking tot AEM) omhoog vóór de secundaire knopen moeten zijn.
1. Zorg ervoor dat geen processen van of interne of externe bronnen zoals het Web, de ZEEP, of EJB procesinitiators in werking worden gesteld tot de normale verrichting van het systeem wordt bevestigd.

Als de hoofddatabase voor AEM formulieren wordt verplaatst of gewijzigd, raadpleegt u de installatiegidsen die relevant zijn voor uw toepassingsserver voor informatie over het bijwerken van de databaseverbindingsgegevens voor de AEM formuliergegevensbronnen IDP_DS en EDC_DS.

### De hostnaam van de AEM formulieren of het IP-adres {#changing-the-aem-forms-hostname-or-ip-address} wijzigen

Als u in een cluster TCP-caching gebruikt in plaats van UDP, moet u de configuratie van de cachelocator bijwerken. Zie &quot;Vormend de caching locators (caching die slechts TCP gebruiken)&quot;in de configuratiegids relevant voor uw toepassingsserver.

### De systeempaden van het knooppunt AEM formulieren wijzigen {#changing-the-aem-forms-node-file-system-paths}

Als u de paden van het bestandssysteem wijzigt voor een zelfstandig knooppunt, moet u de desbetreffende verwijzingen bijwerken in de voorkeuren, andere systeemconfiguraties, aangepaste toepassingen en geïmplementeerde AEM formuliertoepassingen. Voor een cluster moeten daarentegen alle knooppunten dezelfde padconfiguratie van het bestandssysteem gebruiken. U moet de GDS-hoofdmap (Global Document Storage) instellen en ervoor zorgen dat deze verwijst naar een kopie van de herstelde GDS die synchroon is met de herstelde database. Het instellen van het GDS-pad is belangrijk omdat de GDS gegevens kunnen bevatten die moeten blijven bestaan over het opnieuw opstarten van de toepassingsserver.

In een geclusterde omgeving moet de padconfiguratie van het bestandssysteem van de opslagplaats gelijk zijn voor alle clusterknooppunten vóór de back-up en na de herstelbewerking.

Gebruik het `LCSetGDS`script in de map `[*aem-forms root]*\sdk\misc\Foundation\SetGDSCommandline` om het GDS-pad in te stellen nadat u de paden van het bestandssysteem hebt gewijzigd. Zie het `ReadMe.txt`-bestand in dezelfde map voor meer informatie. Als het oude GDS-directorypad niet kan worden gebruikt, moet het `LCSetGDS`-script worden gebruikt om het nieuwe pad in te stellen op de GDS voordat u AEM formulieren start.

>[!NOTE]
>
>Deze omstandigheid is de enige waaronder u dit script moet gebruiken om de GDS-locatie te wijzigen. Als u de GDS-locatie wilt wijzigen terwijl AEM formulieren worden uitgevoerd, gebruikt u de beheerconsole. (Zie [Algemene instellingen voor AEM configureren](/help/forms/using/admin-help/configure-general-aem-forms-settings.md#configure-general-aem-forms-settings)*.) *

Nadat u het GDS-pad hebt ingesteld, start u de formulierserver in de onderhoudsmodus en gebruikt u de beheerconsole om de resterende bestandsysteempaden voor het nieuwe knooppunt bij te werken. Nadat u hebt gecontroleerd of alle benodigde configuraties zijn bijgewerkt, start u AEM formulieren opnieuw en test u deze.
