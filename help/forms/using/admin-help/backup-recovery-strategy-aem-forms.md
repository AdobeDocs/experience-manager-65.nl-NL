---
title: Back-up- en herstelstrategie voor AEM formulieren
description: Leer hoe u een strategie implementeert voor het maken van back-ups van gegevens en hoe u ervoor zorgt dat deze consistent blijft met de AEM formuliergegevens.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 01ec6ebc-6d80-4417-9604-c8571aebb57e
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1518'
ht-degree: 0%

---

# Back-up- en herstelstrategie voor AEM formulieren{#backup-and-recovery-strategy-for-aem-forms}

Als in de implementatie van uw AEM aanvullende aangepaste gegevens worden opgeslagen in een andere database, bent u verantwoordelijk voor het implementeren van een strategie om back-ups van deze gegevens te maken en ervoor te zorgen dat deze consistent blijven met de AEM formuliergegevens. Bovendien moet de toepassing zo zijn ontworpen dat deze robuust genoeg is om een scenario af te handelen waarbij de extra databases niet meer synchroon zijn. Het wordt hoogst geadviseerd dat om het even welke gegevensbestandverrichting die wordt uitgevoerd in de context van een transactie wordt gedaan helpen een verenigbare staat handhaven.

Nadat u hebt vastgesteld hoe AEM formulieren worden gebruikt, bepaalt u welke bestanden een back-up moeten maken, hoe vaak en welk back-upvenster beschikbaar moet worden gemaakt.

>[!NOTE]
>
>Net als bij elk ander aspect van de implementatie van uw AEM formulieren, moet uw back-up- en herstelstrategie worden ontwikkeld en getest in een ontwikkelings- of testomgeving voordat deze in de productie wordt gebruikt om ervoor te zorgen dat de volledige oplossing werkt zoals u had verwacht zonder gegevensverlies.

Adobe Experience Manager (AEM) maakt integrerend deel uit van AEM formulieren. Daarom moet u AEM ook synchroniseren met AEM formulieren voor back-ups, zoals Correspondence Management Solution en -services, zoals formulierbeheer, zijn gebaseerd op gegevens die zijn opgeslagen in AEM deel van AEM formulieren.Om gegevensverlies te voorkomen, moeten de AEM specifieke gegevens op een zodanige manier worden opgeslagen dat GDS en AEM (gegevensopslagruimte) correleren met databaseverwijzingen.De directory&#39;s database, GDS, AEM en Content Storage Root moeten worden hersteld naar een DNS op dezelfde manier Geef het origineel een naam.

## Typen back-ups {#types-of-backups}

De back-upstrategie voor AEM formulieren omvat twee typen back-ups:

**Systeemafbeelding:** Een volledige systeemback-up die u kunt gebruiken om de inhoud van de computer te herstellen als de vaste schijf of de volledige computer niet meer werkt. Een back-up van het systeemimage is alleen nodig voordat AEM formulieren worden geïmplementeerd. Het interne bedrijfsbeleid bepaalt dan hoe vaak de steunen van het systeembeeld worden vereist.

**Specifieke gegevens AEM formulieren:** Toepassingsgegevens bevinden zich in database, GDS (Global Document Storage) en AEM opslagruimte en moeten in real-time worden opgeslagen. GDS is een map waarin bestanden van lange duur worden opgeslagen die in een proces worden gebruikt. Deze bestanden kunnen PDF, beleidsregels of formuliersjablonen bevatten.

>[!NOTE]
>
>Als Content Services (Afgekeurd) is geïnstalleerd, maakt u ook een back-up van de hoofdmap van de Content Storage Root. Zie [Content Storage Root-directory (alleen Content Services)](/help/forms/using/admin-help/files-back-recover.md#content-storage-root-directory-content-services-only).

De database wordt gebruikt om formulierartefacten, serviceconfiguraties, processtatus en databaseverwijzingen naar GDS-bestanden op te slaan. Als u de opslag van documenten in de database hebt ingeschakeld, worden permanente gegevens en documenten in de GDS ook in de database opgeslagen. U kunt een back-up van de database maken en deze herstellen met de volgende methoden:

* **Back-up van momentopname** De modus geeft aan dat het systeem van AEM formulieren gedurende een bepaald aantal minuten in de back-upmodus staat, waarna de back-upmodus niet meer wordt geactiveerd. U kunt een van de volgende opties gebruiken om de back-upmodus voor momentopnamen in of uit te schakelen. Na een terugwinningsscenario, zou de wijze van de momentopname steun niet moeten worden toegelaten.

   * Gebruik de pagina Back-upinstellingen in de beheerconsole. Schakel het selectievakje Bewerken in veilige back-upmodus in om de modus voor momentopnamen in te schakelen. Schakel het selectievakje uit om de modus voor momentopnamen af te sluiten.
   * Het LCBackupMode-script gebruiken (zie [Maak een back-up van de directory&#39;s database, GDS en Content Storage Root](/help/forms/using/admin-help/backing-aem-forms-data.md#back-up-the-database-gds-aem-repository-and-content-storage-root-directories)). Als u de back-upmodus voor momentopnamen wilt afsluiten, stelt u in het scriptargument de optie `continuousCoverage` parameter to `false` of de `leaveContinuousCoverage` -optie.
   * Gebruik de meegeleverde API voor back-up/herstel. <!-- Fix broken link(see AEM forms API Reference section on AEM Forms Help and Tutorials page).-->

* **Terugdraaiback-up** De modus geeft aan dat het systeem altijd in de back-upmodus staat, waarbij een nieuwe back-upmodussessie wordt gestart zodra de vorige sessie wordt losgelaten. Er is geen time-out gekoppeld aan de schuifmodus. Wanneer het manuscript LCBackupMode of APIs worden geroepen om het rollen reservewijze te verlaten, begint een nieuwe het rollen reservewijze zitting. Deze modus is handig voor het ondersteunen van continue back-ups, maar nog steeds voor het verwijderen van oude en overbodige documenten uit de GDS-directory. De modus Rolling Backup wordt niet ondersteund via de pagina Backup and Recovery. Na een terugwinningsscenario, wordt het rollen reservewijze nog toegelaten. U kunt de modus voor continue back-up (rolmodus voor back-up) verlaten door het LCBackupMode-script te gebruiken met het `leaveContinuousCoverage` -optie.

>[!NOTE]
>
>Als u de schuifmodus onmiddellijk verlaat, wordt een nieuwe back-upmodussessie gestart. Als u de schuifmodus volledig wilt uitschakelen, gebruikt u de `leaveContinuousCoverage` in het script, dat de bestaande rolback-upsessie overschrijft. In de back-upmodus voor momentopnamen kunt u de back-upmodus zoals gewoonlijk verlaten.

Om gegevensverlies te voorkomen, moeten de specifieke gegevens van de AEM formulieren op een manier worden gesteund die ervoor zorgt dat de GDS en de documenten van de Root van de Opslag van de Inhoud met gegevensbestandverwijzingen correleren.

>[!NOTE]
>
>Wanneer de GDS is opgeslagen in het bestandssysteem en niet in de database, voert u de databaseback-up uit vóór de GDS-back-up.

## Speciale overwegingen voor back-up en herstel {#special-considerations-for-backup-and-recovery}

Gebruik de volgende richtlijnen als u AEM formulieren in een andere omgeving moet herstellen vanwege de volgende wijzigingen:

* Wijziging in het IP-adres, de hostnaam of de poort van de AEM Forms-server
* Wijziging in stationsletters of mappad
* Wijzigen in een andere databasehost, -poort of -naam

Dergelijke herstelscenario&#39;s worden doorgaans veroorzaakt door hardwarestoringen van de server die de toepassingsserver, databaseserver of Forms Server host. Naast de AEM vormen-specifieke configuraties die in deze sectie worden beschreven, zou u ook de noodzakelijke veranderingen voor andere delen van de AEM vormenplaatsing zoals ladingsbalancers en firewalls moeten aanbrengen, als hostname of IP adres van een Server van AEM Forms verandert.

### Wat niet kan worden gewijzigd {#what-cannot-be-changed}

Hoewel u de databaseserver en veel andere parameters kunt wijzigen, kunt u het servertype of databasetype van de toepassing niet wijzigen wanneer u AEM formulieren uit een back-up terugzet. Als u bijvoorbeeld een back-up van AEM formulieren herstelt, kunt u de toepassingsserver niet van JBoss naar WebLogic of van de database wijzigen van Oracle naar DB2. Bovendien moeten herstelde AEM dezelfde bestandsysteempaden gebruiken, zoals de map met lettertypen.

### Opnieuw opstarten na herstel {#restarting-after-a-recovery}

Ga als volgt te werk voordat u de Forms Server opnieuw start na een herstelbewerking:

1. Start het systeem in de onderhoudsmodus.
1. Ga als volgt te werk om ervoor te zorgen dat Form Manager wordt gesynchroniseerd met AEM formulieren in de onderhoudsmodus:

   1. Ga naar https://&lt;*server*>:&lt;*poort*>/lc/fm en meld u aan met de gegevens van de beheerder/het wachtwoord.
   1. Klik op de naam van de gebruiker (in dit geval Super Administrator) in de rechterbovenhoek.
   1. Klikken **Beheeropties**.
   1. Klikken **Start** om elementen van de repository te synchroniseren.

1. In een gegroepeerd milieu, zou de primaire knoop (met betrekking tot AEM) omhoog vóór de secundaire knopen moeten zijn.
1. Zorg ervoor dat geen processen van of interne of externe bronnen zoals het Web, de ZEEP, of EJB procesinitiators in werking worden gesteld tot de normale verrichting van het systeem wordt bevestigd.

Als de hoofddatabase voor AEM formulieren wordt verplaatst of gewijzigd, raadpleegt u de installatiegidsen die relevant zijn voor uw toepassingsserver voor informatie over het bijwerken van de databaseverbindingsgegevens voor de AEM formuliergegevensbronnen IDP_DS en EDC_DS.

>[!NOTE]
> 
> Het wordt aanbevolen de SDK opnieuw te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM ontwikkelomgeving.

### De hostnaam of het IP-adres van de AEM formulieren wijzigen {#changing-the-aem-forms-hostname-or-ip-address}

Als u in een cluster TCP-caching gebruikt in plaats van UDP, moet u de configuratie van de cachelocator bijwerken. Zie &quot;Vormend de caching locators (caching die slechts TCP gebruiken)&quot;in de configuratiegids relevant voor uw toepassingsserver.

### De systeempaden van het knooppunt AEM formulieren wijzigen {#changing-the-aem-forms-node-file-system-paths}

Als u de paden van het bestandssysteem wijzigt voor een zelfstandig knooppunt, moet u de desbetreffende verwijzingen bijwerken in de voorkeuren, andere systeemconfiguraties, aangepaste toepassingen en geïmplementeerde AEM formuliertoepassingen. Voor een cluster moeten daarentegen alle knooppunten dezelfde padconfiguratie van het bestandssysteem gebruiken. Stel de hoofdmap van de algemene documentopslag (GDS) in en zorg ervoor dat deze verwijst naar een kopie van de herstelde GDS die synchroon is met de herstelde database. Het instellen van het GDS-pad is belangrijk omdat de GDS gegevens kunnen bevatten die moeten blijven bestaan over het opnieuw opstarten van de toepassingsserver.

In een geclusterde omgeving moet de padconfiguratie van het bestandssysteem van de opslagplaats gelijk zijn voor alle clusterknooppunten vóór de back-up en na de herstelbewerking.

Gebruik de `LCSetGDS`in het `[*aem-forms root]*\sdk\misc\Foundation\SetGDSCommandline` om het GDS-pad in te stellen nadat u de paden van het bestandssysteem hebt gewijzigd. Zie de `ReadMe.txt` in dezelfde map voor meer informatie. Als het oude GDS-directorypad niet kan worden gebruikt, `LCSetGDS` voordat u AEM formulieren start, moet u het nieuwe pad instellen op de GDS.

>[!NOTE]
>
>Deze omstandigheid is de enige waaronder u dit script moet gebruiken om de GDS-locatie te wijzigen. Als u de GDS-locatie wilt wijzigen terwijl AEM formulieren worden uitgevoerd, gebruikt u de beheerconsole. (Zie [Algemene instellingen voor AEM configureren](/help/forms/using/admin-help/configure-general-aem-forms-settings.md#configure-general-aem-forms-settings)*.) *

Nadat u het GDS-pad hebt ingesteld, start u de Forms-server in de onderhoudsmodus en gebruikt u de beheerconsole om de resterende bestandsysteempaden voor het nieuwe knooppunt bij te werken. Nadat u hebt gecontroleerd of alle benodigde configuraties zijn bijgewerkt, start u AEM formulieren opnieuw en test u deze.
