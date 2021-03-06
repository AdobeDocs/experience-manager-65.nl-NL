---
title: De AEM formuliergegevens herstellen
seo-title: De AEM formuliergegevens herstellen
description: In dit document worden de stappen beschreven die zijn vereist om de AEM formuliergegevens te herstellen.
seo-description: In dit document worden de stappen beschreven die zijn vereist om de AEM formuliergegevens te herstellen.
uuid: b5735196-5a8d-4358-884f-e9b8d8f4f682
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 4e093114-219b-4018-9530-9002eb665448
translation-type: tm+mt
source-git-commit: 317fadfe48724270e59644d2ed9a90fbee95cf9f
workflow-type: tm+mt
source-wordcount: '1174'
ht-degree: 0%

---


# De AEM formuliergegevens herstellen {#recovering-the-aem-forms-data}

In deze sectie worden de stappen beschreven die zijn vereist om de AEM formuliergegevens te herstellen. Zie ook [Speciale overwegingen voor back-up en herstel](/help/forms/using/admin-help/backup-recovery-strategy-aem-forms.md#special-considerations-for-backup-and-recovery).

>[!NOTE]
>
>De database-, GDS-, AEM- en Content Storage Root-directory&#39;s moeten worden hersteld naar een computer met dezelfde DNS-naam als het origineel.

AEM formulieren moeten op betrouwbare wijze worden hersteld van de volgende fouten:

**Schijfstoring:** de nieuwste back-upmedia zijn vereist om de database-inhoud te herstellen.

**Gegevensbeschadiging:** Bestandssystemen registreren geen eerdere transacties en systemen overschrijven mogelijk per ongeluk vereiste procesgegevens.

**Gebruikersfout:** Herstel is beperkt tot de gegevens die door de database beschikbaar worden gesteld. Als de gegevens zijn opgeslagen en beschikbaar zijn, wordt de herstelbewerking vereenvoudigd.

**Stroomuitval, systeemuitval:API&#39;s van** bestandssystemen zijn vaak niet op een robuuste manier ontworpen of gebruikt die bescherming biedt tegen onverwachte systeemstoringen. Als een stroomuitval of een systeemcrash optreedt, is de documentinhoud die in de database is opgeslagen waarschijnlijk up-to-date dan de inhoud die op een bestandssysteem is opgeslagen.

Als u het rollen reservewijze gebruikt, bent u nog in reservewijze na terugwinning. Als u de back-upmodus voor momentopnamen gebruikt, bevindt u zich na herstel niet in de back-upmodus.

Bij het terugzetten van back-up naar een nieuw systeem kunnen de volgende configuraties verschillend zijn. Dit verschil mag geen invloed hebben op een geslaagde terugwinning van de AEM:

* IP-adres
* Fysieke systeemconfiguratie (CPU&#39;s, schijf, geheugen)
* GDS-locatie

>[!NOTE]
>
>De back-up van de hoofdmap voor inhoudsopslag moet worden teruggezet naar de locatie van die map, zoals deze is ingesteld tijdens de configuratie van Content Services.

Als ????n enkele knoop van een multinode cluster ontbrak en de resterende knopen van de cluster behoorlijk werken, voer de cluster enig-knoopterugwinningsprocedure uit.

## De AEM formuliergegevens herstellen {#recover-the-aem-forms-data}

1. Stop de AEM formulierservices en toepassingsserver als deze actief zijn.
1. Maak indien nodig het fysieke systeem opnieuw op basis van een systeemimage. Deze stap is bijvoorbeeld mogelijk niet nodig als de reden voor de terugwinning een onjuiste databaseserver is.
1. Pas patches of updates toe op AEM formulieren die zijn toegepast sinds de afbeelding is gemaakt. Deze informatie werd geregistreerd in de reserveprocedure. AEM formulieren moeten op hetzelfde patchniveau worden geplaatst als toen een back-up van het systeem werd gemaakt.
1. (WebSphere Application Server) Als u terugkeert naar een nieuwe instantie van WebSphere Application Server, voert u de opdracht restoreConfig.bat/sh uit.
1. Herstel de AEM-formulierdatabase door eerst een terugzetbewerking uit te voeren met behulp van de back-upbestanden van de database en vervolgens de transactierlogboeken opnieuw toe te passen op de herstelde database. (Zie [AEM formulierdatabase](/help/forms/using/admin-help/files-back-recover.md#aem-forms-database).) Zie een van de volgende artikelen in de kennisbasis voor meer informatie:

   * [Oracle Backup and Recovery voor AEM formulieren](https://www.adobe.com/go/kb403624)
   * [MySQL Backup and Recovery voor AEM formulieren](https://www.adobe.com/go/kb403625)
   * [Microsoft SQL Server Backup and Recovery voor AEM formulieren](https://www.adobe.com/go/kb403623)
   * [DB2 Back-up en herstel voor AEM formulieren](https://www.adobe.com/go/kb403626)

1. Herstel de GDS-map door eerst de inhoud van de GDS-map te verwijderen bij de bestaande installatie van AEM formulieren en vervolgens de inhoud van de GDS-map te kopi??ren uit de GDS-map waarvan een back-up is gemaakt. Als u de GDS-maplocatie hebt gewijzigd, zie [De GDS-locatie wijzigen tijdens de herstelbewerking](recovering-aem-forms-data.md#changing-the-gds-location-during-recovery).
1. Wijzig de naam van de GDS-back-updirectory die moet worden hersteld, zoals in de volgende voorbeelden wordt getoond:

   >[!NOTE]
   >
   >Als /restore folder reeds bestaat, file het en dan schrapt het alvorens u de /backup folder anders noemt die de recentste gegevens bevat.

   * (JBoss) Naam wijzigen in:`[appserver root]/server/'server'/svcnative/DocumentStorage/backup`

      `[appserver root]/server/'server'/svcnative/DocumentStorage/restore`.

   * (WebLogic) Wijzig de naam `[appserverdomain]/'server'/adobe/AEMformsserver/DocumentStorage/backup` in:

      `[appserverdomain]/'server'/adobe/AEMformsserver/DocumentStorage/restore`.

   * (WebSphere) Wijzig de naam `[appserver root]/installedApps/adobe/'server'/DocumentStorage/backup` in:

      `[appserver root]/installedApps/adobe/'server'/DocumentStorage/restore`.

1. Herstel de basismap voor de opslag van inhoud door eerst de inhoud van de basismap voor de opslag van inhoud te verwijderen bij de bestaande installatie van AEM formulieren en herstel de inhoud door de taken voor zelfstandige of geclusterde omgevingen uit te voeren:

   >[!NOTE]
   >
   >De back-up van de hoofdmap voor inhoudsopslag moet worden hersteld naar de locatie van de hoofdmap voor inhoudsopslag, zoals deze is ingesteld tijdens de configuratie van Content Services (Afgekeurd).

   **Zelfstandig:** Tijdens het terugwinningsproces, herstel alle folders die werden gesteund. Wanneer deze folders worden hersteld, als de /backup-lucene-indexen folder aanwezig is, noem het aan /lucene-indexen anders. Anders zou de map lucene-indexes al moeten bestaan en is geen actie vereist.

   **Gegroepeerd:** Tijdens het herstelproces, herstel alle directory&#39;s waarvan een back-up is gemaakt. Als u de hoofdmap van de index wilt herstellen, voert u de volgende stappen uit op elk knooppunt van de cluster:

   * Verwijder alle inhoud uit de hoofdmap van de index.
   * Als de /backup-lucene-indexes folder aanwezig is, kopieer de inhoud van *de folder van de Root van de Opslag van de Inhoud*/backup-lucene-indexes aan de folder van de Root van de Index en schrap *de folder van de Root van de Opslag van de Inhoud*/backup-lucene-indexes.
   * Als de /lucene-indexes folder aanwezig is, kopieer de inhoud van *de folder van de Root van de Opslag van de Inhoud*/lucene-indexes aan de folder van de Root van de Index.

1. De CRX-opslagplaats herstellen/herstellen.

   * **Zelfstandig**

      *Instanties* van auteur en publicatie herstellen: Als zich een ramp voordoet, kunt u de opslagplaats terugzetten naar de laatste back-upstatus door de stappen uit te voeren die worden beschreven in  [Back-up en Herstellen.](https://docs.adobe.com/docs/en/crx/current/administering/backup_and_restore.html)

      Het volledig herstel van het knooppunt Auteur zorgt ervoor dat ook de gegevens van Forms Manager en AEM Forms Workspace worden hersteld.

   * **Geclusterd**

      Zie [Strategie voor back-up en herstel in een geclusterde omgeving](/help/forms/using/admin-help/strategy-backup-restore-clustered-environment.md#strategy-for-backup-and-restore-in-a-clustered-environment) voor herstel in een geclusterde omgeving.

1. Verwijder alle AEM formulieren die tijdelijk zijn gemaakt in de map java.io.temp of in de map Adobe temp.
1. Start AEM formulieren (zie [Services starten en stoppen](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services))<!-- BROKEN LINK and the application server(s) (see [Maintaining the Application Server](/help/forms/using/admin-help/topics/maintaining-the-application-server.md))-->.

## De GDS-locatie wijzigen tijdens herstel {#changing-the-gds-location-during-recovery}

Als uw GDS op een andere plaats dan waar het oorspronkelijk was wordt hersteld, stel het manuscript LCSetGDS in om GDS aan de nieuwe plaats te plaatsen. Het script bevindt zich in de map `[aem-forms root]\sdk\misc\Foundation\SetGDSCommandline`. Het script heeft twee parameters, `defaultGDS` en `newGDS`. Zie het `ReadMe.txt` dossier in de zelfde omslag voor instructies op hoe te om het manuscript in werking te stellen.

>[!NOTE]
>
>Als u de opslag van documenten in de database hebt ingeschakeld, hoeft u de GDS-locatie niet te wijzigen.

>[!NOTE]
>
>Deze omstandigheid is de enige waaronder u dit script moet gebruiken om de GDS-locatie te wijzigen. Als u de GDS-locatie wilt wijzigen terwijl AEM formulieren worden uitgevoerd, gebruikt u de beheerconsole. (Zie [Algemene AEM formulierinstellingen configureren](/help/forms/using/admin-help/configure-general-aem-forms-settings.md#configure-general-aem-forms-settings).)

>[!NOTE]
>
>De implementatie van componenten mislukt in Windows als de GDS-map zich in de hoofdmap van het station bevindt (bijvoorbeeld D:\). Bij GDS moet u ervoor zorgen dat de map zich niet in de hoofdmap van de schijf bevindt, maar in een submap. De map moet bijvoorbeeld D:\GDS and not simply D:\.

## De GDS herstellen naar een geclusterde omgeving {#recovering-the-gds-to-a-clustered-environment}

Om de plaats GDS in een gegroepeerde milieu te veranderen, sluit de volledige cluster en stel het manuscript LCSetGDS op ????n enkele knoop van de cluster in werking. (Zie [De GDS-locatie wijzigen tijdens herstel](recovering-aem-forms-data.md#changing-the-gds-location-during-recovery).) Start alleen dat knooppunt. Wanneer dat knooppunt volledig is gestart, kunnen andere knooppunten in de cluster veilig worden gestart en correct naar de nieuwe GDS-knooppunten verwijzen.

>[!NOTE]
>
>Als u niet kunt verzekeren begin ????n knoop volledig alvorens andere knopen te beginnen, moet u het manuscript LCSetGDS op elke knoop in de cluster in werking stellen alvorens u de cluster begint.

