---
title: Rapporten over het gebruik en het delen van elementen
description: Rapporten over uw activa in  [!DNL Adobe Experience Manager Assets]  die u helpen gebruik, activiteit, en het delen van uw digitale activa begrijpen.
contentOwner: AG
role: User, Admin
feature: Asset Reports,Asset Management
exl-id: b4963a03-3496-4c6c-9d30-8812304d0e9f
hide: true
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1089'
ht-degree: 7%

---

# Elementen rapporteren {#asset-reports}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/admin/asset-reports.html?lang=nl-NL) |
| AEM 6,5 | Dit artikel |

Met Asset Reporting kunt u het nut van uw [!DNL Adobe Experience Manager Assets] -implementatie beoordelen. Met [!DNL Assets] kunt u verschillende rapporten genereren voor uw digitale elementen. De rapporten bevatten nuttige informatie over het gebruik van uw systeem, over de manier waarop gebruikers met elementen werken en over de elementen die worden gedownload en gedeeld.

Gebruik de informatie in de rapporten om belangrijke succesmetriek af te leiden om de goedkeuring van [!DNL Assets] binnen uw onderneming en door klanten te meten.

Het [!DNL Assets] -rapportagekader gebruikt [!DNL Sling] -taken om rapportageaanvragen op geordende wijze asynchroon te verwerken. Het is schaalbaar voor grote opslagruimten. De asynchrone rapportverwerking verhoogt de efficiency en de snelheid waarmee de rapporten worden geproduceerd.

De interface van het rapportbeheer is intuïtief en omvat fijnkorrelige opties en controles om tot gearchiveerde rapporten toegang te hebben en de loopstatussen van het meningsrapport (succes, ontbroken, en een rij gevormd) in werking te stellen.

Wanneer een rapport wordt gegenereerd, ontvangt u een melding via e-mail (optioneel) en een postbusmelding. U kunt een rapport weergeven, downloaden of verwijderen van de pagina met rapportlijsten waarop alle eerder gegenereerde rapporten worden weergegeven.

## Vereiste {#prerequisite-for-reporting}

Ga als volgt te werk om rapporten te genereren:

* Schakel [!UICONTROL Day CQ DAM Event Recorder] -service in vanuit **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]** .
* Selecteer de activiteiten of gebeurtenissen waarop u wilt rapporteren. Selecteer bijvoorbeeld [!UICONTROL Asset downloaded (DOWNLOADED)] als u rapport over gedownloade elementen wilt genereren.

![ laat activa toe rapporterend in de Console van het Web ](assets/reports-config-day-cq-dam-event-recorder.png)

## Rapporten genereren {#generate-reports}

[!DNL Experience Manager Assets] genereert de volgende standaardrapporten voor u:

* Uploaden
* Downloaden
* Verlopen
* Wijziging
* Publish
* [!DNL Brand Portal] publish
* Schijfgebruik
* Bestanden
* Delen van koppeling

[!DNL Adobe Experience Manager] -beheerders kunnen deze rapporten eenvoudig voor uw implementatie genereren en aanpassen. Een beheerder kan deze stappen volgen om een rapport te produceren:

1. Klik in de interface [!DNL Experience Manager] op **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Reports]** .

   ![ pagina van Hulpmiddelen om activa te navigeren rapport ](assets/AssetsReportNavigation.png)

1. Klik op de pagina [!UICONTROL Asset Reports] op **[!UICONTROL Create]** op de werkbalk.
1. Kies op de pagina **[!UICONTROL Create Report]** het rapport dat u wilt maken en klik op **[!UICONTROL Next]** .

   ![ Uitgezochte rapporttype ](assets/choose_report.png)

   >[!NOTE]
   >
   >Standaard worden de Content Fragments en de shares van de koppeling opgenomen in het Asset [!UICONTROL Download] -rapport. Selecteer de aangewezen optie om een rapport van verbindingsaandelen tot stand te brengen of inhoudsfragmenten van het downloadrapport uit te sluiten.

   >[!NOTE]
   >
   >Het [!UICONTROL Download] -rapport bevat alleen details van de elementen die worden gedownload nadat ze afzonderlijk zijn geselecteerd of die met Snelle actie zijn gedownload. De gegevens van de elementen in een gedownloade map worden echter niet in de map opgenomen.

1. Configureer rapportdetails zoals titel, beschrijving, miniatuur en mappad in de CRX-opslagplaats waar het rapport wordt opgeslagen. Standaard is het mappad `/content/dam` . U kunt een ander pad opgeven.

   ![ Pagina om rapportdetails toe te voegen ](assets/report_configuration.png)

   Kies het datumbereik voor uw rapport.

   U kunt ervoor kiezen het rapport nu of op een toekomstige datum en tijd te genereren.

   >[!NOTE]
   >
   >Als u ervoor kiest om het rapport later te plannen, zorg ervoor dat u de datum en de tijd in de gebieden van de Datum en van de Tijd specificeert. Als u geen waarde specificeert, behandelt de rapportmotor het als een rapport dat onmiddellijk moet worden geproduceerd.

   De gebieden van de configuratie kunnen verschillen gebaseerd op het type van rapport u creeert. Het rapport **[!UICONTROL Disk Usage]** bevat bijvoorbeeld opties voor het opnemen van elementen bij het berekenen van de schijfruimte die door elementen wordt gebruikt. U kunt ervoor kiezen om elementen in submappen op te nemen of uit te sluiten voor het berekenen van het schijfgebruik.

   >[!NOTE]
   >
   >Het rapport **[!UICONTROL Disk Usage]** bevat geen datumbereikvelden omdat het alleen het huidige gebruik van schijfruimte aangeeft.

   ![ pagina van Details van het rapport van het Gebruik van de Schijf ](assets/disk_usage_configuration.png)

   Wanneer u het **[!UICONTROL Files]** -rapport maakt, kunt u submappen opnemen of uitsluiten. U kunt echter geen elementuitvoeringen opnemen voor dit rapport.

   ![ pagina van Details van het rapport van Dossiers ](assets/files_report.png)

   Het **[!UICONTROL Link Share]** -rapport geeft URL&#39;s weer naar elementen die vanuit [!DNL Assets] met externe gebruikers worden gedeeld. Het bevat e-mail-id&#39;s van de gebruiker die de assets heeft gedeeld, e-mail-id&#39;s van gebruikers met wie de assets worden gedeeld, de datum van delen en de vervaldatum voor de koppeling. De kolommen kunnen niet worden aangepast.

   Het rapport **[!UICONTROL Link Share]** bevat geen opties voor submappen en uitvoeringen omdat het alleen de gedeelde URL&#39;s publiceert die onder `/var/dam/share` worden weergegeven.

   ![ pagina van Details van het rapport van het Aandeel van de Verbinding ](assets/link_share.png)

1. Klik op **[!UICONTROL Next]** op de werkbalk.

1. Op de pagina **[!UICONTROL Configure Columns]** zijn er kolommen geselecteerd die standaard in het rapport worden weergegeven. U kunt meer kolommen selecteren. Annuleer de selectie van een kolom om deze uit te sluiten in het rapport.

   ![ Uitgezocht of annuleer de selectie van rapportkolommen ](assets/configure_columns.png)

   Als u een aangepaste kolomnaam of een aangepast eigenschapspad wilt weergeven, configureert u de eigenschappen voor het binaire element onder het knooppunt `jcr:content` in CRX. U kunt dit ook toevoegen via de padkiezer voor eigenschappen.

   ![ Uitgezocht of annuleer de selectie van rapportkolommen ](assets/custom_columns.png)

1. Klik op **[!UICONTROL Create]** op de werkbalk. Een bericht meldt dat de rapportgeneratie is in werking gesteld.
1. Op de pagina [!UICONTROL Asset Reports] is de status van het genereren van het rapport gebaseerd op de huidige status van de rapporttaak, bijvoorbeeld [!UICONTROL Success] , [!UICONTROL Failed] , [!UICONTROL Queued] of [!UICONTROL Scheduled] . Dezelfde status wordt weergegeven in het vak met meldingen. Klik op de rapportkoppeling om de rapportpagina weer te geven. U kunt ook het rapport selecteren en op **[!UICONTROL View]** op de werkbalk klikken.

   <!--![A generated report](assets/report_page.png)-->
   [ status van het Rapport ](assets/report-status.JPG)

   Klik op **[!UICONTROL Download]** op de werkbalk om het rapport in de CSV-indeling te downloaden.

## Aangepaste kolommen toevoegen {#add-custom-columns}

U kunt douanekolommen aan de volgende rapporten toevoegen om meer gegevens voor uw douanevereisten te tonen:

* Uploaden
* Downloaden
* Verlopen
* Wijziging
* Publish
* [!DNL Brand Portal] publish
* Bestanden

Ga als volgt te werk om aangepaste kolommen aan deze rapporten toe te voegen:

1. Klik in de [!DNL Manager interface] op **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Reports]** .
1. Klik op de pagina [!UICONTROL Asset Reports] op **[!UICONTROL Create]** op de werkbalk.

1. Kies op de pagina **[!UICONTROL Create Report]** het rapport dat u wilt maken en klik op **[!UICONTROL Next]** .
1. Configureer rapportdetails zoals titel, beschrijving, miniatuur, mappad en datumbereik.

1. Als u een aangepaste kolom wilt weergeven, geeft u de naam op van de kolom onder **[!UICONTROL Custom Columns]**.

   ![ specificeer naam voor douanekolom van rapport ](assets/custom_columns-1.png)

1. Voeg het eigenschapspad onder het knooppunt `jcr:content` in CRXDE toe met de padkiezer voor eigenschappen. U kunt ook het pad typen in het veld Pad eigenschap.

   ![ kaart de bezitspad van wegen in jcr:inhoud ](assets/property_picker.png)

   Als u meer aangepaste kolommen wilt toevoegen, klikt u op **[!UICONTROL Add]** en herhaalt u stap 5 en 6.

1. Klik op **[!UICONTROL Create]** op de werkbalk. Een bericht meldt dat de rapportgeneratie is in werking gesteld.

## De zuiveringsservice configureren {#configure-purging-service}

Om rapporten te verwijderen die u niet meer vereist, vorm de dienst van de Leegmaken van het Rapport DAM van de Webconsole om bestaande rapporten te zuiveren die op hun hoeveelheid en leeftijd worden gebaseerd.

1. Open de webconsole (configuratiemanager) vanuit `https://[aem_server]:[port]/system/console/configMgr` .
1. Open de **[!UICONTROL DAM Report Purge Service]** -configuratie.
1. Geef de frequentie (tijdsinterval) voor de service purging op in het veld `scheduler.expression.name` . U kunt de leeftijd en de kwantitatieve drempel voor rapporten ook vormen.
1. Sla de wijzigingen op.

## Problemen met informatie, tips en beperkingen oplossen {#best-practices-and-limitations}

* Als bepaalde rapporten of nummers in de rapporten niet beschikbaar zijn of niet overeenkomen, controleert u of de service [!UICONTROL Day CQ DAM Event Recorder] is ingeschakeld.

* Verwijder de rapporten die niet meer vereist zijn. Gebruik de configuratieopties in de DAM dienst van de Leegmaken van het Rapport om de criteria te vormen om rapporten te zuiveren.

* Als het rapport Schijfgebruik niet wordt gegenereerd en u [!DNL Dynamic Media] gebruikt, moet u ervoor zorgen dat alle elementen correct worden uitgevoerd. U lost de problemen op door de elementen opnieuw te verwerken en vervolgens het rapport opnieuw te genereren.
