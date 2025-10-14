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
source-git-commit: 6a9806d8f40f711a610c130c63d9ab9b2460d075
workflow-type: tm+mt
source-wordcount: '1527'
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
* Als u of het rollen of momentopnamemodesteunen gebruikt, zorg ervoor dat uw gegevensbestand met de correcte logboekmontages wordt gevormd om voor hete steunen van het gegevensbestand toe te staan. (Zie [&#x200B; gegevensbestand van AEM Forms &#x200B;](/help/forms/using/admin-help/files-back-recover.md#aem-forms-database).)

Daarnaast moet u de volgende richtlijnen voor het back-up-/herstelproces in acht nemen.

* Maak een back-up van de GDS-map met behulp van een beschikbaar besturingssysteem of een back-uphulpprogramma van derden. (Zie [&#x200B; GDS plaats &#x200B;](/help/forms/using/admin-help/files-back-recover.md#gds-location).)
* (Optioneel) Maak een back-up van de hoofdmap van de Content Storage met behulp van een beschikbaar besturingssysteem of een externe back-up en hulpprogramma. (Zie {de plaats van de Wortel van de Opslag van 0} Inhoud (stand-alone milieu) [&#128279;](/help/forms/using/admin-help/files-back-recover.md#content-storage-root-location-stand-alone-environment) of [&#x200B; de Hoofdplaats van de Opslag van de Inhoud (gegroepeerd milieu) &#x200B;](/help/forms/using/admin-help/files-back-recover.md#content-storage-root-location-clustered-environment).)
* Terug   auteur- en publicatieinstanties ( crx -repository backup).

  Aan file voert het milieu van de Oplossing van het Beheer van de Correspondentie, de stappen op de auteur uit en publiceert instanties zoals die in [&#x200B; Steun en herstel &#x200B;](/help/sites-administering/backup-and-restore.md) worden beschreven.

  Houd rekening met de volgende punten wanneer u een back-up maakt van de auteur en instanties publiceert:

   * Zorg ervoor dat de back-up voor auteur- en publicatie-instanties wordt gesynchroniseerd om tegelijk te starten. Hoewel u auteur- en publicatie-exemplaren kunt blijven gebruiken terwijl de back-up wordt uitgevoerd, wordt u aangeraden geen elementen tijdens de back-up te publiceren om niet-vastgelegde wijzigingen te voorkomen. Wacht tot de back-up van zowel auteur- als publicatieinstanties is beëindigd voordat u nieuwe elementen publiceert.
   * De volledige back-up van het auteurknooppunt omvat een back-up van Forms Manager- en AEM Forms Workspace-gegevens.
   * Workbench-ontwikkelaars kunnen hun processen lokaal blijven uitvoeren. Tijdens de back-upfase moeten ze geen nieuwe processen implementeren.
   * Het besluit over de lengte van elke back-upsessie (voor de rolmodus) moet gebaseerd zijn op de totale tijd die nodig is om een back-up te maken van alle gegevens in AEM Forms (DB, GDS, AEM opslagplaats en eventuele andere aanvullende aangepaste gegevens).

Maak een back-up van de AEM Forms-database, inclusief transactielogboeken. Zie [&#x200B; gegevensbestand van AEM Forms &#x200B;](/help/forms/using/admin-help/files-back-recover.md#aem-forms-database).

Raadpleeg voor meer informatie het desbetreffende kennisbankartikel voor uw database:
<!-- The four URLs below are all 404s; checked July 19, 2023 -->
* [&#x200B; Steun en Terugwinning van het Oracle voor AEM Forms &#x200B;](https://www.adobe.com/go/kb403624)
* [&#x200B; Steun MySQL en Terugwinning voor AEM Forms &#x200B;](https://www.adobe.com/go/kb403625)
* [&#x200B; de Steun en Terugwinning van de Server van Microsoft® SQL voor AEM Forms &#x200B;](https://www.adobe.com/go/kb403623)
* [&#x200B; DB2® Steun en Terugwinning voor AEM Forms &#x200B;](https://www.adobe.com/go/kb403626)

Deze artikelen bieden richtlijnen voor basisdatabasefuncties voor het maken van back-ups en het herstellen van gegevens. Ze zijn niet bedoeld als allesomvattende technische hulplijnen van de back-up- en herstelfunctie van de database van een specifieke leverancier. Ze bevatten opdrachten die nodig zijn om een betrouwbare back-upstrategie voor uw AEM Forms-toepassingsgegevens te maken.

>[!NOTE]
>
>De databaseback-up moet voltooid zijn voordat u begint met het maken van een back-up van de GDS. Als de back-up van de database niet is voltooid, zijn de gegevens niet gesynchroniseerd.

### De back-upmodi invoeren {#entering-the-backup-modes}

U kunt ofwel de beheerconsole, de LCBackupMode-opdracht, ofwel de API die beschikbaar is bij de AEM Forms-installatie gebruiken om de back-upmodi in en uit te schakelen. Voor het rollen steun (ononderbroken dekking), is de optie van de beleidsconsole niet beschikbaar; u zou of de bevel-lijn optie of API moeten gebruiken. <!-- Fix broken link For information about using the API to enter and leave backup modes, see AEM Forms API Reference on Help and Tutorials page. -->

>[!NOTE]
>
>Als u SSL hebt geconfigureerd op de Forms-server, kunt u de Forms-server niet in de back-upmodus plaatsen met het LCBackupMode.CMD-script.

**Gebruikend de beleidsconsole om veilige reservewijze** in te gaan

1. Log in bij de beheerconsole.
1. Klik op Instellingen > Core System Settings > Backup Utilities.
1. Selecteer Werken in veilige back-upmodus en klik op OK.

   Met deze methode wordt AEM Forms oneindig in de back-upmodus gezet (geen time-out) en wordt de modus voor momentopnamen geactiveerd in plaats van de modus voor back-up.

**Gebruikend de bevel-lijn optie om veilige reservewijze** in te gaan

U kunt de opdrachtregelinterface `LCBackupMode` -scripts gebruiken om AEM Forms in de veilige back-upmodus te zetten.

1. Stel ADOBE_LIVECYCLE in en start de toepassingsserver.
1. Ga naar de map `*[aem-forms root]*/sdk/misc/Foundation/BackupRestoreCommandline` .
1. Afhankelijk van uw besturingssysteem kunt u het script `LCBackupMode.cmd` of `LCBackupMode.sh` bewerken om standaardwaarden op te geven die geschikt zijn voor uw systeem.
1. Voer bij de opdrachtprompt de volgende opdracht uit op één regel:

   * (Vensters) `LCBackupMode.cmd enter [-Host=`*hostname* `] [-port=`*portnumber* `] [-user=`*gebruikersbenaming* `] [-password=`*wachtwoord* `] [-label=`*etiketnaam* `] [-timeout=`*seconden* `]`
   * (Linux®, UNIX®) `LCBackupMode.sh enter [-host=`*hostname* `] [-port=`*portnumber* `] [-user=`*gebruikersbenaming* `] [-password=`*wachtwoord* `] [-label=`*etiketnaam* `]`

   In de vorige opdrachten worden de plaatsaanduidingen als volgt gedefinieerd:

   `Host` is de naam van de host waarop AEM Forms wordt uitgevoerd.

   `port` is de WebServices-poort van de toepassingsserver waarop AEM Forms wordt uitgevoerd.

   `user` is de gebruikersnaam van de AEM Forms-beheerder.

   `password` is het wachtwoord van de AEM Forms-beheerder.

   `label` is het tekstlabel, dat elke tekenreeks kan zijn, voor deze back-up.

   `timeout` is het aantal seconden waarna de back-upmodus automatisch wordt verlaten. Het kan 0-10.080 zijn. Als het 0 is, wat het gebrek is, de reservewijze nooit uit.

   Zie het Leesmij-bestand in de map BackupRestoreCommandline voor meer informatie over de opdrachtregelinterface naar de back-upmodus.

### Back-upmodi verlaten {#leaving-backup-modes}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

U kunt of de beleidsconsole of bevel-lijn optie gebruiken om reservewijzen te verlaten.

**veilige reservewijze van het Verlof (momentopnamemodus)**

Als u de beheerconsole wilt gebruiken om AEM Forms uit de veilige back-upmodus te halen (momentopnamemodus), voert u de volgende taken uit.

1. Meld u aan bij de beheerconsole.
1. Klik op Instellingen > Core System Settings > Backup Utilities.
1. Schakel Werken in veilige back-upmodus uit en klik op OK.

**Verlaat alle reservewijzen**

U kunt de opdrachtregelinterface gebruiken om AEM Forms uit de veilige back-upmodus te halen (modus voor momentopnamen) of om de huidige sessie in de back-upmodus te beëindigen (modus rollen). U kunt niet de beleidsconsole gebruiken om het rollen reservewijze te verlaten. In de schuifmodus voor back-ups zijn de besturingselementen voor back-uphulpprogramma&#39;s in de beheerconsole uitgeschakeld. Gebruik de API-aanroep of gebruik de opdracht LCBackupMode.

1. Ga naar de map `*[aem-forms root]*/sdk/misc/Foundation/BackupRestoreCommandline` .
1. Afhankelijk van uw besturingssysteem kunt u het script `LCBackupMode.cmd` of `LCBackupMode.sh` bewerken om standaardwaarden op te geven die geschikt zijn voor uw systeem.

   >[!NOTE]
   >
   >Plaats de folder JAVA_HOME zoals die in het aangewezen hoofdstuk voor uw toepassingsserver in [&#x200B; wordt beschreven Voorbereidend om AEM Forms &#x200B;](https://www.adobe.com/go/learn_aemforms_prepareInstallsingle_63) *te installeren.*

1. Voer de volgende opdracht op één regel uit:

   * (Vensters) `LCBackupMode.cmd leaveContinuousCoverage [-Host=`*hostname* `] [-port=`*portnumber* `] [-user=`*gebruikersbenaming* `] [-password=`*wachtwoord* `]`
   * (Linux®, UNIX®) `LCBackupMode.sh leaveContinuousCoverage [-Host=`*hostname* `] [-port=`*portnumber* `] [-user=`*gebruikersbenaming* `] [-password=`*wachtwoord* `]`

     In de vorige opdrachten worden de plaatsaanduidingen als volgt gedefinieerd:

     `Host` is de naam van de host waarop AEM Forms wordt uitgevoerd.

     `port` is de poort waarop AEM Forms op de toepassingsserver wordt uitgevoerd.

     `user` is de gebruikersnaam van de AEM Forms-beheerder.

     `password` is het wachtwoord van de AEM Forms-beheerder.

     `leaveContinuousCoverage` Gebruik deze optie om de modus Rollen van back-ups volledig uit te schakelen.

   >[!NOTE]
   >
   >Voor de tijd dat reservewijze weg is, kan de ononderbroken dekking niet opnieuw worden gevestigd. Wijzigingen die tijdens die periode worden aangebracht, zijn niet beveiligd.

   >[!NOTE]
   >
   >Als u de opslag van documenten in de database hebt ingeschakeld, zijn de back-upmodus voor momentopnamen en de modus voor het rollen van back-ups niet van toepassing.

   Zie het Lees mij-bestand in de map BackupRestoreCommandline voor meer informatie over de opdrachtregelinterface naar de back-upmodus.
