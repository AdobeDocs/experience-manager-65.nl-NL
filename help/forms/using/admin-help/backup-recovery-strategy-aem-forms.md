---
title: Back-up- en herstelstrategie voor AEM-formulieren
seo-title: Back-up- en herstelstrategie voor AEM-formulieren
description: Leer hoe u een strategie implementeert voor het maken van back-ups van gegevens en ervoor zorgt dat deze consistent blijft met de AEM-formuliergegevens.
seo-description: Leer hoe u een strategie implementeert voor het maken van back-ups van gegevens en ervoor zorgt dat deze consistent blijft met de AEM-formuliergegevens.
uuid: 98fc3115-76e5-4e58-aa30-3601866a441f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: f192a8a3-1116-4d32-9b57-b53d532c0dbf
translation-type: tm+mt
source-git-commit: 2cf9dcf2e9cf71c54e19e2c6ee825c9a8f00a9b7

---


# Back-up- en herstelstrategie voor AEM-formulieren{#backup-and-recovery-strategy-for-aem-forms}

Als in uw AEM-formulierimplementatie aanvullende aangepaste gegevens worden opgeslagen in een andere database, bent u verantwoordelijk voor het implementeren van een strategie om back-ups van deze gegevens te maken en ervoor te zorgen dat deze consistent blijven met de AEM-formuliergegevens. Bovendien moet de toepassing zo zijn ontworpen dat deze robuust genoeg is om een scenario af te handelen waarbij de extra databases niet meer synchroon zijn. Het wordt hoogst geadviseerd dat om het even welke gegevensbestandverrichting die wordt uitgevoerd in de context van een transactie wordt gedaan helpen een verenigbare staat handhaven.

Nadat u hebt vastgesteld hoe AEM-formulieren worden gebruikt, bepaalt u welke bestanden een back-up moeten maken, hoe vaak en welk back-upvenster beschikbaar moet worden gemaakt.

>[!NOTE]
>
>Net als bij elk ander aspect van uw AEM-formulierimplementatie, moet uw back-up- en herstelstrategie worden ontwikkeld en getest in een ontwikkelings- of testomgeving voordat deze in de productie wordt gebruikt, om ervoor te zorgen dat de volledige oplossing werkt zoals u had verwacht zonder gegevensverlies.

Adobe Experience Manager (AEM) is een integraal onderdeel van AEM-formulieren. Daarom moet u zowel een back-up van AEM maken als de back-up van AEM-formulieren synchroniseren met Correspondence Management Solution en -services, zoals formulierbeheer, die zijn gebaseerd op gegevens die zijn opgeslagen in het AEM-onderdeel van AEM-formulieren.Om gegevensverlies te voorkomen, moet een back-up worden gemaakt van de specifieke gegevens van de AEM-formulieren, zodat GDS en AEM (gegevensopslagruimte) correleren met databasereferenties.De directory&#39;s, database, GDS, GDS, GDS, GDS, GDS, GDS, GDS, AEM, AEM, AEM, en AEM en AEM, en de hoofdmappen en de opslagmap en de inhoud op een computer met dezelfde DNS-naam als het origineel.

## Typen back-ups {#types-of-backups}

De back-upstrategie voor AEM-formulieren omvat twee typen back-ups:

**Systeemafbeelding:** Een volledige systeemback-up die u kunt gebruiken om de inhoud van de computer te herstellen als de vaste schijf of de volledige computer niet meer werkt. Een back-up van het systeemimage is alleen nodig voordat AEM-formulieren voor de productie worden geïmplementeerd. Het interne bedrijfsbeleid bepaalt dan hoe vaak de steunen van het systeembeeld worden vereist.

**Specifieke gegevens voor AEM-formulieren:** Toepassingsgegevens staan in database, Global Document Storage (GDS) en AEM-opslagruimte en moeten in real-time worden opgeslagen. GDS is een map waarin bestanden van lange duur worden opgeslagen die in een proces worden gebruikt. Deze bestanden kunnen PDF&#39;s, beleidsregels of formuliersjablonen bevatten.

>[!NOTE]
>
>Als Content Services (Afgekeurd) is geïnstalleerd, maakt u ook een back-up van de hoofdmap van de Content Storage Root. Zie [Content Storage Root directory (alleen Content Services)](/help/forms/using/admin-help/files-back-recover.md#content-storage-root-directory-content-services-only).

De database wordt gebruikt om formulierartefacten, serviceconfiguraties, processtatus en databaseverwijzingen naar GDS-bestanden op te slaan. Als u de opslag van documenten in de database hebt ingeschakeld, worden permanente gegevens en documenten in de GDS ook in de database opgeslagen. U kunt een back-up van de database maken en deze herstellen met de volgende methoden:

* **In de modus Back-up** van momentopnamen wordt aangegeven dat het AEM-formuliersysteem gedurende een bepaald aantal minuten in de back-upmodus staat, waarna de back-upmodus niet meer wordt geactiveerd. U kunt een van de volgende opties gebruiken om de back-upmodus voor momentopnamen in of uit te schakelen. Na een terugwinningsscenario, zou de wijze van de momentopname steun niet moeten worden toegelaten.

   * Gebruik de pagina Back-upinstellingen in de beheerconsole. Schakel het selectievakje Bewerken in veilige back-upmodus in om de modus voor momentopnamen in te schakelen. Schakel het selectievakje uit om de modus voor momentopnamen af te sluiten.
   * Gebruik het LCBackupMode-script (zie [Back-up maken van de database, GDS en mappen](/help/forms/using/admin-help/backing-aem-forms-data.md#back-up-the-database-gds-aem-repository-and-content-storage-root-directories)met opslaghoofdmap voor inhoud). Als u de back-upmodus voor momentopnamen wilt afsluiten, stelt u de `continuousCoverage` parameter in op `false` of gebruikt u de `leaveContinuousCoverage` optie.
   * Gebruik de meegeleverde API voor back-up/herstel. <!-- Fix broken link(see AEM forms API Reference section on AEM Forms Help and Tutorials page).-->

* **De modus Rolling Backup** geeft aan dat het systeem zich altijd in de back-upmodus bevindt, waarbij een nieuwe back-upmodussessie wordt gestart zodra de vorige sessie wordt losgelaten. Er is geen time-out gekoppeld aan de schuifmodus. Wanneer het manuscript LCBackupMode of APIs worden geroepen om het rollen reservewijze te verlaten, begint een nieuwe het rollen reservewijze zitting. Deze modus is handig voor het ondersteunen van continue back-ups, maar nog steeds voor het verwijderen van oude en overbodige documenten uit de GDS-directory. De modus Rolling Backup wordt niet ondersteund via de pagina Backup and Recovery. Na een terugwinningsscenario, wordt het rollen reservewijze nog toegelaten. U kunt de modus voor continue back-up (schuifmodus) verlaten door het LCBackupMode-script met de `leaveContinuousCoverage` optie te gebruiken.

>[!NOTE]
>
>Als u de schuifmodus onmiddellijk verlaat, wordt een nieuwe back-upmodussessie gestart. Om het rollen reservewijze volledig onbruikbaar te maken, gebruik de `leaveContinuousCoverage` optie in het manuscript, dat de bestaande het rollen reservezitting beschrijft. In de back-upmodus voor momentopnamen kunt u de back-upmodus zoals gewoonlijk verlaten.

Om gegevensverlies te voorkomen, moeten de specifieke gegevens van AEM-formulieren op een manier worden opgeslagen die ervoor zorgt dat GDS- en Content Storage Root-documenten correleren met databasereferenties.

>[!NOTE]
>
>Wanneer de GDS is opgeslagen in het bestandssysteem en niet in de database, voert u de databaseback-up uit vóór de GDS-back-up.

## Speciale overwegingen voor back-up en herstel {#special-considerations-for-backup-and-recovery}

Gebruik de volgende richtlijnen als u AEM-formulieren in een andere omgeving moet herstellen vanwege de volgende wijzigingen:

* Wijziging in het IP-adres, de hostnaam of de poort van de AEM-formulierserver
* Wijziging in de stationsletters of het directorypad
* Wijzigen in een andere databasehost, -poort of -naam

Dergelijke herstelscenario&#39;s worden doorgaans veroorzaakt door hardwarestoringen van de server die de toepassingsserver, databaseserver of formulierserver host. Naast de AEM formulieren-specifieke configuraties die in deze sectie worden beschreven, zou u ook de noodzakelijke veranderingen voor andere delen van de plaatsing van AEM vormen zoals ladingsbalancers en firewalls moeten aanbrengen, als hostname of IP adres van een AEM vormenserver verandert.

### Wat niet kan worden gewijzigd {#what-cannot-be-changed}

Hoewel u de databaseserver en veel andere parameters kunt wijzigen, kunt u het servertype of databasetype van de toepassing niet wijzigen wanneer u AEM-formulieren uit een back-up terugzet. Als u bijvoorbeeld een back-up van een AEM-formulier herstelt, kunt u de toepassingsserver niet van JBoss naar WebLogic of van Oracle naar DB2 wijzigen. Bovendien moeten herstelde AEM-formulieren dezelfde bestandssysteempaden gebruiken, zoals de map met lettertypen.

### Opnieuw opstarten na herstel {#restarting-after-a-recovery}

Ga als volgt te werk voordat u de formulierserver opnieuw start na een herstelbewerking:

1. Start het systeem in de onderhoudsmodus.
1. Ga als volgt te werk om ervoor te zorgen dat Form Manager in de onderhoudsmodus wordt gesynchroniseerd met AEM-formulieren:

   1. Ga naar https://&lt;*server*>:&lt;*port*>/lc/fm en meld u aan met de gegevens van de beheerder/het wachtwoord.
   1. Klik op de naam van de gebruiker (in dit geval Super Administrator) in de rechterbovenhoek.
   1. Klik op **beheeropties**.
   1. Klik op **Start** om elementen uit de opslagplaats te synchroniseren.

1. In een gegroepeerde omgeving, zou de hoofdknoop (met betrekking tot AEM) omhoog vóór de slave knopen moeten zijn.
1. Zorg ervoor dat geen processen van of interne of externe bronnen zoals het Web, de ZEEP, of EJB procesinitiators in werking worden gesteld tot de normale verrichting van het systeem wordt bevestigd.

Als de belangrijkste AEM-formulierdatabase wordt verplaatst of gewijzigd, raadpleegt u de installatiegidsen die relevant zijn voor uw toepassingsserver voor informatie over het bijwerken van de databaseverbindingsgegevens voor de AEM-formuliergegevensbronnen IDP_DS en EDC_DS.

### De hostnaam of het IP-adres van AEM-formulieren wijzigen {#changing-the-aem-forms-hostname-or-ip-address}

Als u in een cluster TCP-caching gebruikt in plaats van UDP, moet u de configuratie van de cachelocator bijwerken. Zie &quot;Vormend de caching locators (caching die slechts TCP gebruiken)&quot;in de configuratiegids relevant voor uw toepassingsserver.

### De systeempaden van het AEM-knooppunt voor formulieren wijzigen {#changing-the-aem-forms-node-file-system-paths}

Als u de paden van het bestandssysteem wijzigt voor een zelfstandig knooppunt, moet u de desbetreffende verwijzingen bijwerken in de voorkeuren, andere systeemconfiguraties, aangepaste toepassingen en geïmplementeerde AEM-formuliertoepassingen. Voor een cluster moeten daarentegen alle knooppunten dezelfde padconfiguratie van het bestandssysteem gebruiken. U moet de GDS-hoofdmap (Global Document Storage) instellen en ervoor zorgen dat deze verwijst naar een kopie van de herstelde GDS die synchroon is met de herstelde database. Het instellen van het GDS-pad is belangrijk omdat de GDS gegevens kunnen bevatten die moeten blijven bestaan over het opnieuw opstarten van de toepassingsserver.

In een geclusterde omgeving moet de padconfiguratie van het bestandssysteem van de opslagplaats gelijk zijn voor alle clusterknooppunten vóór de back-up en na de herstelbewerking.

Gebruik het `LCSetGDS`script in de `[*aem-forms root]*\sdk\misc\Foundation\SetGDSCommandline` map om het GDS-pad in te stellen nadat u de paden van het bestandssysteem hebt gewijzigd. Zie het `ReadMe.txt` bestand in dezelfde map voor meer informatie. Als het oude GDS-directorypad niet kan worden gebruikt, moet `LCSetGDS` script worden gebruikt om het nieuwe pad in te stellen op de GDS voordat u AEM-formulieren start.

>[!NOTE]
>
>Deze omstandigheid is de enige waaronder u dit script moet gebruiken om de GDS-locatie te wijzigen. Als u de GDS-locatie wilt wijzigen terwijl AEM-formulieren worden uitgevoerd, gebruikt u de beheerconsole. (Zie Algemene instellingen voor [](/help/forms/using/admin-help/configure-general-aem-forms-settings.md#configure-general-aem-forms-settings)AEM-formulieren configureren*.) *

Nadat u het GDS-pad hebt ingesteld, start u de formulierserver in de onderhoudsmodus en gebruikt u de beheerconsole om de resterende bestandsysteempaden voor het nieuwe knooppunt bij te werken. Nadat u hebt gecontroleerd of alle benodigde configuraties zijn bijgewerkt, start u AEM-formulieren opnieuw en test u deze.
