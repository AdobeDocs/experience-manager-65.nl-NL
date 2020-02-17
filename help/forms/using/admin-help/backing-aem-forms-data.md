---
title: Back-up maken van de AEM-formuliergegevens
seo-title: Back-up maken van de AEM-formuliergegevens
description: In dit document worden de stappen beschreven die vereist zijn om een hot-of online back-up van de AEM-formulierdatabase, de GDS-directory en de directory's met opslagruimte voor inhoud te maken.
seo-description: In dit document worden de stappen beschreven die vereist zijn om een hot-of online back-up van de AEM-formulierdatabase, de GDS-directory en de directory's met opslagruimte voor inhoud te maken.
uuid: ac7856be-e3b7-4b81-b8b9-fc909b5907b4
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 52187196-b091-4683-85ae-cc7c250dee54
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Back-up maken van de AEM-formuliergegevens {#backing-up-the-aem-forms-data}

In deze sectie worden de stappen beschreven die vereist zijn om een hot-of online back-up te maken van de AEM-formulierdatabase, de GDS-directory en de directory&#39;s met opslagruimte voor inhoud.

Nadat de vormen AEM worden geïnstalleerd en aan productiegebieden worden opgesteld, zou de gegevensbestandbeheerder een eerste volledige, of koude, steun van het gegevensbestand moeten uitvoeren. Voor deze back-up moet de database worden afgesloten. Dan, zouden de differentiële of stijgende (of hete) steunen van het gegevensbestand regelmatig moeten worden gedaan.

Voor een succesvolle back-up en herstel moet altijd een back-up van het systeemimage beschikbaar zijn. Als er dan een verlies optreedt, kunt u de volledige omgeving op een consistente manier herstellen.

Als u back-ups maakt van de database op hetzelfde moment als de back-ups in de GDS-, AEM-opslagmap en de Content Storage Root-map, blijven deze systemen gesynchroniseerd als herstel ooit nodig is.

Voor de back-upprocedure die in deze sectie wordt beschreven, moet u de veilige back-upmodus inschakelen voordat u een back-up maakt van de AEM-formulierdatabase, de AEM-opslagruimte, de GDS en de hoofddirectory&#39;s voor de opslag van inhoud. Wanneer de back-up is voltooid, moet u de veilige back-upmodus afsluiten. De veilige reservewijze wordt gebruikt om lange-levende en blijvende documenten te merken die in GDS verblijven. Deze modus zorgt ervoor dat het automatische mechanisme voor bestandsopruiming (de bestandscollector) geen verlopen bestanden verwijdert totdat de veilige back-upmodus wordt losgelaten. Een GDS-back-up moet gesynchroniseerd worden gehouden met een back-up van een database.

Hoe vaak een back-up van de GDS-locatie moet worden gemaakt, is afhankelijk van de manier waarop AEM-formulieren worden gebruikt en de beschikbare back-upvensters. Het back-upvenster kan worden beïnvloed door processen van lange duur, omdat deze gedurende enkele dagen kunnen worden uitgevoerd. Als u voortdurend bestanden in deze map wijzigt, toevoegt en verwijdert, moet u vaker een back-up van de GDS-locatie maken.

Als de database wordt uitgevoerd in een logmodus, zoals beschreven in de vorige sectie, moet ook een back-up van de databaselogbestanden worden gemaakt, zodat deze kunnen worden gebruikt om de database te herstellen in het geval van een mediafout.

>[!NOTE]
>
>Bestanden waarnaar niet wordt verwezen, blijven mogelijk na het herstelproces in de GDS-map staan. Dit is op dit moment een bekende beperking.

## Maak een back-up van de directory&#39;s database, GDS, AEM-opslagruimte en Content Storage Root {#back-up-the-database-gds-aem-repository-and-content-storage-root-directories}

U moet AEM-formulieren in de modus voor veilige back-ups (momentopnamen) of in de modus voor rolback-ups (doorlopende dekking) plaatsen. Voordat u AEM-formulieren instelt op een van de back-upmodi, moet u het volgende controleren:

* Controleer de systeemversie en registreer de patches of updates die zijn toegepast sinds de laatste volledige back-up van het image van het systeem is uitgevoerd.
* Als u het rollen of momentopnamemodesteunen gebruikt, zorg ervoor dat uw gegevensbestand met de correcte logboekmontages wordt gevormd om voor hete steunen van het gegevensbestand toe te staan. (Zie [AEM-formulierdatabase](/help/forms/using/admin-help/files-back-recover.md#aem-forms-database).)

Daarnaast moet u de volgende richtlijnen voor het back-up-/herstelproces in acht nemen.

* Maak een back-up van de GDS-map met behulp van een beschikbaar besturingssysteem of een back-uphulpprogramma van derden. (Zie [GDS-locatie](/help/forms/using/admin-help/files-back-recover.md#gds-location).)
* (Optioneel) Maak een back-up van de hoofdmap van de Content Storage met behulp van een beschikbaar besturingssysteem of een externe back-up en hulpprogramma. (Zie [Hoofdlocatie voor inhoudsopslag (zelfstandige omgeving)](/help/forms/using/admin-help/files-back-recover.md#content-storage-root-location-stand-alone-environment) of Hoofdlocatie voor [inhoudsopslag (geclusterde omgeving)](/help/forms/using/admin-help/files-back-recover.md#content-storage-root-location-clustered-environment).)
* Maak een back-up van auteur- en publicatieinstanties ( crx -repository backup).

   Als u een back-up wilt maken van de Correspondence Management Solution-omgeving, voert u de stappen uit op de auteur en publiceert u de instanties zoals beschreven in [Back-up en Herstel](/help/sites-administering/backup-and-restore.md).

   Houd rekening met de volgende punten wanneer u een back-up maakt van de auteur en instanties publiceert:

   * Zorg ervoor dat de back-up voor auteur- en publicatie-instanties tegelijk wordt gesynchroniseerd om te starten. Hoewel u auteur- en publicatieinstanties kunt blijven gebruiken terwijl de back-up wordt uitgevoerd, wordt het aanbevolen geen middelen tijdens de back-up te publiceren om niet-vastgelegde wijzigingen te voorkomen. Wacht tot de back-up van zowel auteur- als publicatieinstanties is beëindigd voordat u nieuwe elementen publiceert.
   * De volledige back-up van het auteurknooppunt bevat een back-up van de gegevens in de werkruimte van Forms Manager en AEM Forms.
   * Workbench-ontwikkelaars kunnen hun processen lokaal blijven uitvoeren. Tijdens de back-upfase moeten ze geen nieuwe processen implementeren.
   * Het besluit over de lengte van elke back-upsessie (voor de rolmodus) moet gebaseerd zijn op de totale tijd die nodig is om een back-up te maken van alle gegevens in AEM-formulieren (DB, GDS, AEM-opslagruimte en eventuele andere aanvullende aangepaste gegevens).

Maak een back-up van de AEM-formulierdatabase, inclusief transactielogboeken. (Zie [AEM-formulierdatabase](/help/forms/using/admin-help/files-back-recover.md#aem-forms-database).) Raadpleeg voor meer informatie het desbetreffende kennisbankartikel voor uw database:

* [Oracle Backup and Recovery voor AEM-formulieren](https://www.adobe.com/go/kb403624)
* [MySQL Backup and Recovery voor AEM-formulieren](https://www.adobe.com/go/kb403625)
* [Microsoft SQL Server Backup and Recovery voor AEM-formulieren](https://www.adobe.com/go/kb403623)
* [DB2 Back-up en herstel voor AEM-formulieren](https://www.adobe.com/go/kb403626)

Deze artikelen bieden richtlijnen voor basisdatabasefuncties voor het maken van back-ups en het herstellen van gegevens. Ze zijn niet bedoeld als allesomvattende technische hulplijnen van de back-up- en herstelfunctie van de database van een specifieke leverancier. Zij schetsen bevelen die worden vereist om een betrouwbare gegevensbestandoplossingsstrategie voor uw AEM vormtoepassingsgegevens tot stand te brengen.

>[!NOTE]
>
>De databaseback-up moet voltooid zijn voordat u begint met het maken van een back-up van de GDS. Als de back-up van de database niet is voltooid, zijn de gegevens niet gesynchroniseerd.

### De back-upmodi invoeren {#entering-the-backup-modes}

U kunt ofwel de beheerconsole, de LCBackupMode-opdracht, ofwel de API die beschikbaar is bij de installatie van AEM-formulieren gebruiken om de back-upmodi in en uit te voeren. Merk op dat voor het rollen steun (ononderbroken dekking), de optie van de beleidsconsole niet beschikbaar is; U moet de opdrachtregeloptie of de API gebruiken. <!-- Fix broken link For information about using the API to enter and leave backup modes, see AEM forms API Reference on Help and Tutorials page. -->

>[!NOTE]
>
>Als u SSL hebt geconfigureerd op de formulierserver, kunt u de formulierserver niet in de back-upmodus plaatsen met het script LCBackupMode.CMD.

**De beheerconsole gebruiken om de veilige back-upmodus te activeren**

1. Meld u aan bij de beheerconsole.
1. Klik op Instellingen > Core System Settings > Backup Utilities.
1. Selecteer Werken in veilige back-upmodus en klik op OK.

   Met deze methode worden AEM-formulieren voor onbepaalde tijd in de back-upmodus gezet (geen time-out) en wordt de momentopnamemodus geactiveerd in plaats van de back-upmodus te rollen.

**De opdrachtregeloptie gebruiken om de veilige back-upmodus te activeren**

Met de opdrachtregelinterfacescripts kunt `LCBackupMode` u AEM-formulieren in de veilige back-upmodus plaatsen.

1. Stel ADOBE_LIVECYCLE in en start de toepassingsserver.
1. Ga naar de `*[aem-forms root]*/sdk/misc/Foundation/BackupRestoreCommandline` map.
1. Afhankelijk van uw besturingssysteem kunt u het `LCBackupMode.cmd` of het `LCBackupMode.sh` script bewerken om standaardwaarden op te geven die geschikt zijn voor uw systeem.
1. Bij de bevelherinnering, stel het volgende bevel op één enkele lijn in werking:

   * (Windows) `LCBackupMode.cmd enter [-Host=`*hostname *`] [-port=`*portnumber* `] [-user=`*username *`] [-password=`*password* `] [-label=`*labelname *`] [-timeout=`** seconds `]`
   * (Linux, UNIX) `LCBackupMode.sh enter [-host=`*hostname *`] [-port=`*portnumber* `] [-user=`*username *`] [-password=`*password* `] [-label=`*labelname *`]`
   In de vorige opdrachten worden de plaatsaanduidingen als volgt gedefinieerd:

   `Host` is de naam van de host waarop AEM-formulieren worden uitgevoerd.

   `port` is de haven WebServices van de toepassingsserver waarop AEM vormen loopt.

   `user` is de gebruikersnaam van de beheerder van AEM-formulieren.

   `password` is het wachtwoord van de AEM-formulierbeheerder.

   `label` Dit is het tekstlabel, dat elke tekenreeks kan zijn, voor deze back-up.

   `timeout` is het aantal seconden waarna de back-upmodus automatisch wordt verlaten. Het kan 0 tot 10.080 zijn. Als het 0 is, wat het gebrek is, de reservewijze nooit uit.

   Zie het Leesmij-bestand in de map BackupRestoreCommandline voor meer informatie over de opdrachtregelinterface naar de back-upmodus.

### Back-upmodi verlaten {#leaving-backup-modes}

U kunt of de beleidsconsole of de optie van de bevellijn gebruiken om reservewijzen te verlaten.

**Veilige back-upmodus verlaten (momentopnamemodus)**

Als u beheerconsole wilt gebruiken om AEM-formulieren uit de veilige back-upmodus (modus voor momentopnamen) te halen, voert u de volgende taken uit.

1. Meld u aan bij de beheerconsole.
1. Klik op Instellingen > Core System Settings > Backup Utilities.
1. Schakel Werken in veilige back-upmodus uit en klik op OK.

**Alle back-upmodi laten staan**

U kunt de opdrachtregelinterface gebruiken om AEM-formulieren uit de veilige back-upmodus (modus voor momentopnamen) te halen of om de huidige back-upmodussessie (modus rollen) te beëindigen. Merk op dat u niet de beleidsconsole kunt gebruiken om het rollen reservewijze te verlaten. In de schuifmodus voor back-ups zijn de besturingselementen voor back-uphulpprogramma&#39;s in de beheerconsole uitgeschakeld. U moet de API-aanroep gebruiken of de opdracht LCBackupMode gebruiken.

1. Ga naar de `*[aem-forms root]*/sdk/misc/Foundation/BackupRestoreCommandline` map.
1. Afhankelijk van uw besturingssysteem kunt u het `LCBackupMode.cmd` of het `LCBackupMode.sh` script bewerken om standaardwaarden op te geven die geschikt zijn voor uw systeem.

   >[!NOTE]
   >
   >U moet de map JAVA_HOME instellen zoals beschreven in het betreffende hoofdstuk voor uw toepassingsserver bij de [voorbereiding van de installatie van AEM-formulieren](https://www.adobe.com/go/learn_aemforms_prepareInstallsingle_63)*.*

1. Voer de volgende opdracht op één regel uit:

   * (Windows) `LCBackupMode.cmd leaveContinuousCoverage [-Host=`*hostname *`] [-port=`*portnumber* `] [-user=`*gebruikersnaam *`] [-password=`*wachtwoord*`]`
   * (Linux, UNIX) `LCBackupMode.sh leaveContinuousCoverage [-Host=`*hostname *`] [-port=`*portnumber* `] [-user=`*gebruikersnaam *`] [-password=`*wachtwoord*`]`

      In de vorige opdrachten worden de plaatsaanduidingen als volgt gedefinieerd:

      `Host` is de naam van de host waarop AEM-formulieren worden uitgevoerd.

      `port` is de poort waarop AEM-formulieren op de toepassingsserver worden uitgevoerd.

      `user` is de gebruikersnaam van de beheerder van AEM-formulieren.

      `password` is het wachtwoord van de AEM-formulierbeheerder.

      `leaveContinuousCoverage` Gebruik deze optie als u de modus Rollen van back-ups volledig wilt uitschakelen.
   >[!NOTE]
   >
   >Voor de tijd dat reservewijze weg is, kan de ononderbroken dekking niet opnieuw worden gevestigd. Wijzigingen die tijdens die periode worden aangebracht, zijn niet beveiligd.

   >[!NOTE]
   >
   >Als u de opslag van documenten in de database hebt ingeschakeld, zijn de back-upmodus voor momentopnamen en de modus voor rolback-ups niet van toepassing.

   Zie het Lees mij-bestand in de map BackupRestoreCommandline voor meer informatie over de opdrachtregelinterface naar de back-upmodus.

