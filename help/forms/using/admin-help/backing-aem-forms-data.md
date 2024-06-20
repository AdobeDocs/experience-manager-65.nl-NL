---
title: Back-ups maken van de Adobe Experience Manager Forms-gegevens
description: In dit document worden de stappen beschreven die vereist zijn om een hot-of online back-up van de Adobe Experience Manager (AEM)-formulierdatabase, de GDS-directory en de directory's voor opslaghoofdmappen voor inhoud te maken.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 536615a4-ab42-4b72-83b1-fad110b011ee
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '1515'
ht-degree: 0%

---

# Back-up maken van de Adobe Experience Manager (AEM) Forms-gegevens {#backing-up-the-aem-forms-data}

<!-- back up is two words when used as a verb; backup is one word when used as an adjective or noun. -->

In deze sectie worden de stappen beschreven die vereist zijn om een hot-of online back-up van de AEM Forms-database, de GDS- en inhoudsopslaghoofddirectory&#39;s te maken.

Nadat AEM Forms wordt geïnstalleerd en aan productiegebieden wordt opgesteld, zou de gegevensbestandbeheerder een eerste volledige, of koude, file van het gegevensbestand moeten uitvoeren. Voor deze back-up moet de database zijn afgesloten. Dan, zouden de differentiële of stijgende (of hete) steunen van het gegevensbestand regelmatig moeten worden gedaan.

Voor een succesvolle back-up en herstel moet altijd een back-up van het systeemimage beschikbaar zijn. Als er dan een verlies optreedt, kunt u de volledige omgeving op een consistente manier herstellen.

Als u back-ups maakt van de database op hetzelfde moment als de back-ups in de GDS-, AEM opslagplaats- en Content Storage Root-directory, kunnen deze systemen gesynchroniseerd blijven als herstel ooit nodig is.

Voor de back-upprocedure die in deze sectie wordt beschreven, moet u de veilige back-upmodus inschakelen voordat u een back-up maakt van de AEM Forms-database, AEM opslagplaats, GDS en de directory&#39;s met opslagruimte voor inhoud. Wanneer de back-up is voltooid, moet u de veilige back-upmodus afsluiten. De veilige reservewijze wordt gebruikt om lange-levende en blijvende documenten te merken die in GDS verblijven. Deze modus zorgt ervoor dat het automatische mechanisme voor bestandsopruiming (de Bestandsverzamelaar) geen verlopen bestanden verwijdert totdat de veilige back-upmodus wordt losgelaten. Een GDS-back-up moet gesynchroniseerd worden gehouden met een back-up van een database.

Hoe vaak een back-up van de GDS-locatie moet worden gemaakt, is afhankelijk van de manier waarop AEM Forms wordt gebruikt en de beschikbare back-upvensters. Het back-upvenster kan worden beïnvloed door processen van lange duur, omdat deze gedurende enkele dagen kunnen worden uitgevoerd. Als u voortdurend bestanden in deze map wijzigt, toevoegt en verwijdert, moet u vaker een back-up van de GDS-locatie maken.

Als de database in een logmodus wordt uitgevoerd, zoals in de vorige sectie wordt beschreven, moeten ook regelmatig back-ups worden gemaakt van de databaselogbestanden, zodat deze kunnen worden gebruikt om de database te herstellen als er een mediafout optreedt.

>[!NOTE]
>
>Bestanden waarnaar niet wordt verwezen, blijven mogelijk na het herstelproces in de GDS-map staan. Dit is momenteel een bekende beperking.

## Maak een back-up van de directory&#39;s database, GDS, AEM opslagplaats en Content Storage Root {#back-up-the-database-gds-aem-repository-and-content-storage-root-directories}

Plaats AEM Forms in de modus voor veilige back-up (momentopname) of in de modus voor rolback-up (continue dekking). Controleer het volgende voordat u AEM Forms instelt op een van de back-upmodi:

* Controleer de systeemversie en registreer de patches of updates die zijn toegepast sinds de laatste volledige back-up van het image van het systeem is uitgevoerd.
* Als u of het rollen of momentopnamemodesteunen gebruikt, zorg ervoor dat uw gegevensbestand met de correcte logboekmontages wordt gevormd om voor hete steunen van het gegevensbestand toe te staan. (Zie [AEM Forms-database](/help/forms/using/admin-help/files-back-recover.md#aem-forms-database).)

Daarnaast moet u de volgende richtlijnen voor het back-up-/herstelproces in acht nemen.

* Maak een back-up van de GDS-map met behulp van een beschikbaar besturingssysteem of een back-uphulpprogramma van derden. (Zie [GDS-locatie](/help/forms/using/admin-help/files-back-recover.md#gds-location).)
* (Optioneel) Maak een back-up van de hoofdmap van de Content Storage met behulp van een beschikbaar besturingssysteem of een externe back-up en hulpprogramma. (Zie [Locatie van opslaghoofdmap voor inhoud (zelfstandige omgeving)](/help/forms/using/admin-help/files-back-recover.md#content-storage-root-location-stand-alone-environment) of [Hoofdlocatie voor opslag van inhoud (geclusterde omgeving)](/help/forms/using/admin-help/files-back-recover.md#content-storage-root-location-clustered-environment).)
* Maak een back-up van auteur- en publicatieinstanties ( crx -repository backup).

  Als u een back-up wilt maken van de Correspondentenbeheeroplossing, voert u de stappen uit op de auteur en publiceert u instanties zoals beschreven in [Back-up en herstel](/help/sites-administering/backup-and-restore.md).

  Houd rekening met de volgende punten wanneer u een back-up maakt van de auteur en instanties publiceert:

   * Zorg ervoor dat de back-up voor auteur- en publicatie-instanties wordt gesynchroniseerd om tegelijk te starten. Hoewel u auteur- en publicatie-exemplaren kunt blijven gebruiken terwijl de back-up wordt uitgevoerd, wordt u aangeraden geen elementen tijdens de back-up te publiceren om niet-vastgelegde wijzigingen te voorkomen. Wacht tot de back-up van zowel auteur- als publicatieinstanties is beëindigd voordat u nieuwe elementen publiceert.
   * De volledige back-up van het auteurknooppunt omvat een back-up van Forms Manager- en AEM Forms Workspace-gegevens.
   * Workbench-ontwikkelaars kunnen hun processen lokaal blijven uitvoeren. Tijdens de back-upfase moeten ze geen nieuwe processen implementeren.
   * Het besluit over de lengte van elke back-upsessie (voor de rolmodus) moet gebaseerd zijn op de totale tijd die nodig is om een back-up te maken van alle gegevens in AEM Forms (DB, GDS, AEM opslagplaats en eventuele andere aanvullende aangepaste gegevens).

Maak een back-up van de AEM Forms-database, inclusief transactielogboeken. Zie [AEM Forms-database](/help/forms/using/admin-help/files-back-recover.md#aem-forms-database).

Raadpleeg voor meer informatie het desbetreffende kennisbankartikel voor uw database:
<!-- The four URLs below are all 404s; checked July 19, 2023 -->
* [Back-up en herstel van oracle voor AEM Forms](https://www.adobe.com/go/kb403624)
* [MySQL Backup and Recovery for AEM Forms](https://www.adobe.com/go/kb403625)
* [Microsoft® SQL Server Backup and Recovery for AEM Forms](https://www.adobe.com/go/kb403623)
* [DB2® Backup and Recovery for AEM Forms](https://www.adobe.com/go/kb403626)

Deze artikelen bieden richtlijnen voor basisdatabasefuncties voor het maken van back-ups en het herstellen van gegevens. Ze zijn niet bedoeld als allesomvattende technische hulplijnen van de back-up- en herstelfunctie van de database van een specifieke leverancier. Ze bevatten opdrachten die nodig zijn om een betrouwbare back-upstrategie voor uw AEM Forms-toepassingsgegevens te maken.

>[!NOTE]
>
>De databaseback-up moet voltooid zijn voordat u begint met het maken van een back-up van de GDS. Als de back-up van de database niet is voltooid, zijn de gegevens niet gesynchroniseerd.

### De back-upmodi invoeren {#entering-the-backup-modes}

U kunt ofwel de beheerconsole, de LCBackupMode-opdracht, ofwel de API die beschikbaar is bij de AEM Forms-installatie gebruiken om de back-upmodi in en uit te schakelen. Voor het rollen steun (ononderbroken dekking), is de optie van de beleidsconsole niet beschikbaar; u zou of de bevel-lijn optie of API moeten gebruiken. <!-- Fix broken link For information about using the API to enter and leave backup modes, see AEM Forms API Reference on Help and Tutorials page. -->

>[!NOTE]
>
>Als u SSL hebt geconfigureerd op de Forms-server, kunt u de Forms-server niet in de back-upmodus plaatsen met het LCBackupMode.CMD-script.

**De beheerconsole gebruiken om de veilige back-upmodus te activeren**

1. Log in bij de beheerconsole.
1. Klik op Instellingen > Core System Settings > Backup Utilities.
1. Selecteer Werken in veilige back-upmodus en klik op OK.

   Met deze methode wordt AEM Forms oneindig in de back-upmodus gezet (geen time-out) en wordt de modus voor momentopnamen geactiveerd in plaats van de modus voor back-up.

**De opdrachtregeloptie gebruiken om de veilige back-upmodus te activeren**

U kunt de opdrachtregelinterface gebruiken `LCBackupMode` scripts om AEM Forms in veilige back-upmodus te zetten.

1. Stel ADOBE_LIVECYCLE in en start de toepassingsserver.
1. Ga naar de `*[aem-forms root]*/sdk/misc/Foundation/BackupRestoreCommandline` map.
1. Afhankelijk van uw besturingssysteem kunt u de opdracht `LCBackupMode.cmd` of `LCBackupMode.sh` gebruiken om standaardwaarden op te geven die geschikt zijn voor uw systeem.
1. Voer bij de opdrachtprompt de volgende opdracht uit op één regel:

   * (Windows) `LCBackupMode.cmd enter [-Host=`*hostnaam* `] [-port=`*portnumber* `] [-user=`*gebruikersnaam* `] [-password=`*password* `] [-label=`*labelnaam* `] [-timeout=`*seconden* `]`
   * (Linux®, UNIX®) `LCBackupMode.sh enter [-host=`*hostnaam* `] [-port=`*portnumber* `] [-user=`*gebruikersnaam* `] [-password=`*password* `] [-label=`*labelnaam* `]`

   In de vorige opdrachten worden de plaatsaanduidingen als volgt gedefinieerd:

   `Host` is de naam van de host waarop AEM Forms wordt uitgevoerd.

   `port` is de haven WebServices van de toepassingsserver waarop AEM Forms loopt.

   `user` is de gebruikersnaam van de AEM Forms-beheerder.

   `password` is het wachtwoord van de AEM Forms-beheerder.

   `label` Dit is het tekstlabel, dat elke tekenreeks kan zijn, voor deze back-up.

   `timeout` is het aantal seconden waarna de back-upmodus automatisch wordt verlaten. Het kan 0-10.080 zijn. Als het 0 is, wat het gebrek is, de reservewijze nooit uit.

   Zie het Leesmij-bestand in de map BackupRestoreCommandline voor meer informatie over de opdrachtregelinterface naar de back-upmodus.

### Back-upmodi verlaten {#leaving-backup-modes}

U kunt of de beleidsconsole of bevel-lijn optie gebruiken om reservewijzen te verlaten.

**Veilige back-upmodus verlaten (momentopnamemodus)**

Als u de beheerconsole wilt gebruiken om AEM Forms uit de veilige back-upmodus te halen (momentopnamemodus), voert u de volgende taken uit.

1. Meld u aan bij de beheerconsole.
1. Klik op Instellingen > Core System Settings > Backup Utilities.
1. Schakel Werken in veilige back-upmodus uit en klik op OK.

**Alle back-upmodi laten staan**

U kunt de opdrachtregelinterface gebruiken om AEM Forms uit de veilige back-upmodus te halen (modus voor momentopnamen) of om de huidige sessie in de back-upmodus te beëindigen (modus rollen). U kunt niet de beleidsconsole gebruiken om het rollen reservewijze te verlaten. In de schuifmodus voor back-ups zijn de besturingselementen voor back-uphulpprogramma&#39;s in de beheerconsole uitgeschakeld. Gebruik de API-aanroep of gebruik de opdracht LCBackupMode.

1. Ga naar de `*[aem-forms root]*/sdk/misc/Foundation/BackupRestoreCommandline` map.
1. Afhankelijk van uw besturingssysteem kunt u de opdracht `LCBackupMode.cmd` of `LCBackupMode.sh` gebruiken om standaardwaarden op te geven die geschikt zijn voor uw systeem.

   >[!NOTE]
   >
   >Stel de map JAVA_HOME in zoals beschreven in het betreffende hoofdstuk voor uw toepassingsserver in [Installatie van AEM Forms voorbereiden](https://www.adobe.com/go/learn_aemforms_prepareInstallsingle_63)*.*

1. Voer de volgende opdracht op één regel uit:

   * (Windows) `LCBackupMode.cmd leaveContinuousCoverage [-Host=`*hostnaam* `] [-port=`*portnumber* `] [-user=`*gebruikersnaam* `] [-password=`*password* `]`
   * (Linux®, UNIX®) `LCBackupMode.sh leaveContinuousCoverage [-Host=`*hostnaam* `] [-port=`*portnumber* `] [-user=`*gebruikersnaam* `] [-password=`*password* `]`

     In de vorige opdrachten worden de plaatsaanduidingen als volgt gedefinieerd:

     `Host` is de naam van de host waarop AEM Forms wordt uitgevoerd.

     `port` is de poort waarop AEM Forms op de toepassingsserver wordt uitgevoerd.

     `user` is de gebruikersnaam van de AEM Forms-beheerder.

     `password` is het wachtwoord van de AEM Forms-beheerder.

     `leaveContinuousCoverage` Gebruik deze optie als u de modus Rollen van back-ups volledig wilt uitschakelen.

   >[!NOTE]
   >
   >Voor de tijd dat reservewijze weg is, kan de ononderbroken dekking niet opnieuw worden gevestigd. Wijzigingen die tijdens die periode worden aangebracht, zijn niet beveiligd.

   >[!NOTE]
   >
   >Als u de opslag van documenten in de database hebt ingeschakeld, zijn de back-upmodus voor momentopnamen en de modus voor het rollen van back-ups niet van toepassing.

   Zie het Lees mij-bestand in de map BackupRestoreCommandline voor meer informatie over de opdrachtregelinterface naar de back-upmodus.
