---
title: De AEM formuliergegevens herstellen
description: In dit document worden de stappen beschreven die zijn vereist om de AEM formuliergegevens te herstellen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 9e648bab-9284-4fda-abb4-8bd7cd085981
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1118'
ht-degree: 0%

---

# De AEM formuliergegevens herstellen {#recovering-the-aem-forms-data}

In deze sectie worden de stappen beschreven die zijn vereist om de AEM formuliergegevens te herstellen. Zie ook [Speciale overwegingen voor back-up en herstel](/help/forms/using/admin-help/backup-recovery-strategy-aem-forms.md#special-considerations-for-backup-and-recovery).

>[!NOTE]
>
>De database-, GDS-, AEM- en Content Storage Root-directory&#39;s moeten worden hersteld naar een computer met dezelfde DNS-naam als het origineel.

AEM formulieren moeten op betrouwbare wijze worden hersteld van de volgende fouten:

**Schijfstoring:** De meest recente back-upmedia zijn vereist om de database-inhoud te herstellen.

**Gegevensbeschadiging:** Bestandssystemen registreren geen eerdere transacties en systemen overschrijven mogelijk per ongeluk de vereiste procesgegevens.

**Gebruikersfout:** De terugwinning is beperkt tot de gegevens die door het gegevensbestand ter beschikking worden gesteld. Als de gegevens zijn opgeslagen en beschikbaar zijn, wordt de herstelbewerking vereenvoudigd.

**Stroomuitval, systeemuitval:** Bestandssysteem-API&#39;s zijn vaak niet op een robuuste manier ontworpen of gebruikt die bescherming biedt tegen onverwachte systeemfouten. Als een stroomuitval of een systeemcrash optreedt, is de documentinhoud die in de database is opgeslagen waarschijnlijk up-to-date dan de inhoud die op een bestandssysteem is opgeslagen.

Als u het rollen reservewijze gebruikt, bent u nog in reservewijze na terugwinning. Als u de back-upmodus voor momentopnamen gebruikt, bevindt u zich na herstel niet in de back-upmodus.

Bij het terugzetten van back-up naar een nieuw systeem kunnen de volgende configuraties verschillend zijn. Dit verschil mag geen invloed hebben op een geslaagde terugwinning van de AEM:

* IP-adres
* Fysieke systeemconfiguratie (CPU&#39;s, schijf, geheugen)
* GDS-locatie

>[!NOTE]
>
>De back-up van de hoofdmap voor inhoudsopslag moet worden teruggezet naar de locatie van die map, zoals deze is ingesteld tijdens de configuratie van Content Services.

Als één enkele knoop van een multinode cluster ontbrak en de resterende knopen van de cluster behoorlijk werken, voer de cluster enig-knoopterugwinningsprocedure uit.

## De AEM formuliergegevens herstellen {#recover-the-aem-forms-data}

1. Stop de AEM formulierservices en toepassingsserver als deze actief zijn.
1. Maak indien nodig het fysieke systeem opnieuw op basis van een systeemimage. Deze stap is bijvoorbeeld mogelijk niet nodig als de reden voor de terugwinning een onjuiste databaseserver is.
1. Pas patches of updates toe op AEM formulieren die zijn toegepast sinds de afbeelding is gemaakt. Deze informatie is opgenomen in de back-upprocedure. AEM formulieren moeten op hetzelfde patchniveau worden geplaatst als toen een back-up van het systeem werd gemaakt.
1. (WebSphere® Application Server) Als u herstelt naar een nieuwe instantie van WebSphere® Application Server, voert u de opdracht restoreConfig.bat/sh uit.
1. Herstel de AEM-formulierdatabase door eerst een terugzetbewerking uit te voeren met behulp van de back-upbestanden van de database en vervolgens de transactierlogboeken opnieuw uit te voeren op de herstelde database. (Zie [AEM formulierdatabase](/help/forms/using/admin-help/files-back-recover.md#aem-forms-database).) Zie een van de volgende artikelen in de kennisbasis voor meer informatie:

   * [DB2](/help/forms/using/admin-help/files-back-recover.md#db2)
   * [Back-up en herstel van oracle voor AEM formulieren](/help/forms/using/admin-help/files-back-recover.md#oracle)
   * [Microsoft](/help/forms/using/admin-help/files-back-recover.md#sql-server)
   * [MySQL Backup and Recovery voor AEM formulieren](/help/forms/using/admin-help/files-back-recover.md#mysql)

1. Herstel de GDS-map door eerst de inhoud van de GDS-map te verwijderen bij de bestaande installatie van AEM formulieren en vervolgens de inhoud van de GDS-map te kopiëren uit de GDS-map waarvan een back-up is gemaakt. Als u de locatie van de GDS-directory hebt gewijzigd, raadpleegt u [De GDS-locatie wijzigen tijdens het herstellen](recovering-aem-forms-data.md#changing-the-gds-location-during-recovery).
1. Wijzig de naam van de GDS-back-updirectory die moet worden hersteld, zoals in de volgende voorbeelden wordt getoond:

   >[!NOTE]
   >
   >Als /restore folder reeds bestaat, file het en dan schrapt het alvorens u de /backup folder anders noemt die de recentste gegevens bevat.

   * (JBoss®) Naam wijzigen `[appserver root]/server/'server'/svcnative/DocumentStorage/backup` tot:

     `[appserver root]/server/'server'/svcnative/DocumentStorage/restore`.

   * (WebLogic) Naam wijzigen `[appserverdomain]/'server'/adobe/AEMformsserver/DocumentStorage/backup` tot:

     `[appserverdomain]/'server'/adobe/AEMformsserver/DocumentStorage/restore`.

   * (WebSphere®) Naam wijzigen `[appserver root]/installedApps/adobe/'server'/DocumentStorage/backup` tot:

     `[appserver root]/installedApps/adobe/'server'/DocumentStorage/restore`.

1. Herstel de basismap voor de opslag van inhoud door eerst de inhoud van de basismap voor de opslag van inhoud te verwijderen bij de bestaande installatie van AEM formulieren en herstel de inhoud door de taken voor zelfstandige of geclusterde omgevingen uit te voeren:

   >[!NOTE]
   >
   >De back-up van de hoofdmap voor inhoudsopslag moet worden hersteld naar de locatie van de hoofdmap voor inhoudsopslag, zoals deze is ingesteld tijdens de configuratie van Content Services (Afgekeurd).

   **Zelfstandig:** Herstel tijdens het herstelproces alle mappen waarvan een back-up is gemaakt. Wanneer deze folders worden hersteld, als de /backup-lucene-indexen folder aanwezig is, noem het aan /lucene-indexen anders. Anders zou de map lucene-indexes al moeten bestaan en is geen actie vereist.

   **Geclusterd:** Herstel tijdens het herstelproces alle mappen waarvan een back-up is gemaakt. Als u de hoofdmap van de index wilt herstellen, voert u de volgende stappen uit op elk knooppunt van de cluster:

   * Verwijder alle inhoud uit de hoofdmap van de index.
   * Als de /backup-lucene-indexes folder aanwezig is, kopieer de inhoud van *De hoofdmap van de inhoudsopslag*/backup-lucene-indexes directory naar de map Index Root en verwijder de map *De hoofdmap van de inhoudsopslag*/backup-lucene-indexes directory.
   * Als de /lucene-indexes folder aanwezig is, kopieer de inhoud van *De hoofdmap van de inhoudsopslag*/lucene-indexes folder aan de folder van de Wortel van de Index.

1. De CRX-opslagplaats herstellen/herstellen.

   * **Zelfstandig**

     *Instanties van auteurs en publicatie herstellen*: Als zich een ramp voordoet, kunt u de opslagplaats herstellen naar de laatste back-upstatus door de in [Back-up en herstel.](https://helpx.adobe.com/experience-manager/kb/CRXBackupAndRestoreProcedure.html)

     Het volledig herstel van het knooppunt Auteur zorgt ervoor dat ook de gegevens van Forms Manager en AEM Forms Workspace worden hersteld.

   * **Geclusterd**

     Voor restauratie in een gegroepeerde omgeving raadpleegt u [Strategie voor back-up en herstel in een geclusterde omgeving](/help/forms/using/admin-help/strategy-backup-restore-clustered-environment.md#strategy-for-backup-and-restore-in-a-clustered-environment).

1. Verwijder alle AEM formulieren die tijdelijk zijn gemaakt in de map java.io.temp of in de map temp van de Adobe.
1. AEM formulieren starten (zie [Starten en stoppen van services](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services))<!-- BROKEN LINK and the application server(s) (see [Maintaining the Application Server](/help/forms/using/admin-help/topics/maintaining-the-application-server.md))-->.

## De GDS-locatie wijzigen tijdens het herstellen {#changing-the-gds-location-during-recovery}

Als uw GDS op een andere plaats dan waar het oorspronkelijk was wordt hersteld, stel het manuscript LCSetGDS in om GDS aan de nieuwe plaats te plaatsen. Het script bevindt zich in de `[aem-forms root]\sdk\misc\Foundation\SetGDSCommandline` map. Het script heeft twee parameters. `defaultGDS` en `newGDS`. Zie de `ReadMe.txt` in dezelfde map voor instructies over het uitvoeren van het script.

>[!NOTE]
>
>Als u de opslag van documenten in de database hebt ingeschakeld, hoeft u de GDS-locatie niet te wijzigen.

>[!NOTE]
>
>Deze omstandigheid is de enige waaronder u dit script moet gebruiken om de GDS-locatie te wijzigen. Als u de GDS-locatie wilt wijzigen terwijl AEM formulieren worden uitgevoerd, gebruikt u de beheerconsole. (Zie [Algemene instellingen voor AEM configureren](/help/forms/using/admin-help/configure-general-aem-forms-settings.md#configure-general-aem-forms-settings).)

>[!NOTE]
>
>De implementatie van componenten mislukt in Windows als de GDS-map zich in de hoofdmap van het station bevindt (bijvoorbeeld D:\). Bij GDS moet u ervoor zorgen dat de map zich niet in de hoofdmap van de schijf bevindt, maar in een submap. De map moet bijvoorbeeld D:\GDS zijn en niet gewoon D:\.

## De GDS herstellen naar een geclusterde omgeving {#recovering-the-gds-to-a-clustered-environment}

Om de plaats GDS in een gegroepeerde milieu te veranderen, sluit de volledige cluster en stel het manuscript LCSetGDS op één enkele knoop van de cluster in werking. (Zie [De GDS-locatie wijzigen tijdens het herstellen](recovering-aem-forms-data.md#changing-the-gds-location-during-recovery).) Start alleen dat knooppunt. Wanneer dat knooppunt volledig is opgestart, kunnen andere knooppunten in de cluster veilig worden opgestart en correct naar de nieuwe GDS verwijzen.

>[!NOTE]
>
>Als u niet kunt verzekeren begin één knoop volledig alvorens andere knopen te beginnen, moet u het manuscript LCSetGDS op elke knoop in de cluster in werking stellen alvorens u de cluster begint.
