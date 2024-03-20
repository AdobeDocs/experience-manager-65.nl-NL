---
title: Rapporten over het gebruik en het delen van elementen
description: Rapporten over uw elementen in [!DNL Adobe Experience Manager Assets] waarmee u inzicht krijgt in het gebruik, de activiteiten en het delen van uw digitale middelen.
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
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/admin/asset-reports.html?lang=en) |
| AEM 6,5 | Dit artikel |

Met Asset Reporting kunt u het nut van uw [!DNL Adobe Experience Manager Assets] implementatie. Met [!DNL Assets]kunt u verschillende rapporten genereren voor uw digitale middelen. De rapporten bevatten nuttige informatie over het gebruik van uw systeem, over de manier waarop gebruikers met elementen werken en over de elementen die worden gedownload en gedeeld.

Gebruik de informatie in de rapporten om belangrijke succesmetriek af te leiden om de goedkeuring te meten [!DNL Assets] binnen uw onderneming en door klanten.

De [!DNL Assets] rapportagekader gebruikt [!DNL Sling] banen aan asynchroon verwerken rapportverzoeken op ordelijke wijze. Het is schaalbaar voor grote opslagruimten. De asynchrone rapportverwerking verhoogt de efficiency en de snelheid waarmee de rapporten worden geproduceerd.

De interface van het rapportbeheer is intuïtief en omvat fijnkorrelige opties en controles om tot gearchiveerde rapporten toegang te hebben en de loopstatussen van het meningsrapport (succes, ontbroken, en een rij gevormd) in werking te stellen.

Wanneer een rapport wordt gegenereerd, ontvangt u een melding via e-mail (optioneel) en een postbusmelding. U kunt een rapport weergeven, downloaden of verwijderen van de pagina met rapportlijsten waarop alle eerder gegenereerde rapporten worden weergegeven.

## Vereiste {#prerequisite-for-reporting}

Ga als volgt te werk om rapporten te genereren:

* Inschakelen [!UICONTROL Day CQ DAM Event Recorder] service van **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
* Selecteer de activiteiten of gebeurtenissen waarop u wilt rapporteren. Als u bijvoorbeeld rapport wilt genereren over gedownloade elementen, selecteert u [!UICONTROL Asset downloaded (DOWNLOADED)].

![Elementrapportage inschakelen in webconsole](assets/reports-config-day-cq-dam-event-recorder.png)

## Rapporten genereren {#generate-reports}

[!DNL Experience Manager Assets] Hiermee genereert u de volgende standaardrapporten:

* Uploaden
* Downloaden
* Verlopen
* Wijziging
* Publiceren
* [!DNL Brand Portal] publish
* Schijfgebruik
* Bestanden
* Delen van koppeling

[!DNL Adobe Experience Manager] beheerders kunnen deze rapporten gemakkelijk produceren en aanpassen voor uw implementatie. Een beheerder kan deze stappen volgen om een rapport te produceren:

1. In [!DNL Experience Manager] interface, klik **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Reports]**.

   ![Pagina Gereedschappen om te navigeren in middelenrapport](assets/AssetsReportNavigation.png)

1. Op de [!UICONTROL Asset Reports] pagina, klikt u **[!UICONTROL Create]** op de werkbalk.
1. Van de **[!UICONTROL Create Report]** pagina, kiest u het rapport dat u wilt maken en klikt u op **[!UICONTROL Next]**.

   ![Rapporttype selecteren](assets/choose_report.png)

   >[!NOTE]
   >
   >Standaard worden de Content Fragments en de link shares opgenomen in het element [!UICONTROL Download] verslag. Selecteer de aangewezen optie om een rapport van verbindingsaandelen tot stand te brengen of inhoudsfragmenten van het downloadrapport uit te sluiten.

   >[!NOTE]
   >
   >De [!UICONTROL Download] In dit rapport worden alleen de elementen weergegeven die worden gedownload nadat u deze afzonderlijk hebt geselecteerd of die met Snelle actie zijn gedownload. De gegevens van de elementen in een gedownloade map worden echter niet in de map opgenomen.

1. Configureer rapportdetails zoals titel, beschrijving, miniatuur en mappad in de CRX-opslagplaats waar het rapport wordt opgeslagen. Standaard is het mappad `/content/dam`. U kunt een ander pad opgeven.

   ![Pagina om rapportdetails toe te voegen](assets/report_configuration.png)

   Kies het datumbereik voor uw rapport.

   U kunt ervoor kiezen het rapport nu of op een toekomstige datum en tijd te genereren.

   >[!NOTE]
   >
   >Als u ervoor kiest om het rapport later te plannen, zorg ervoor dat u de datum en de tijd in de gebieden van de Datum en van de Tijd specificeert. Als u geen waarde specificeert, behandelt de rapportmotor het als een rapport dat onmiddellijk moet worden geproduceerd.

   De gebieden van de configuratie kunnen verschillen gebaseerd op het type van rapport u creeert. Bijvoorbeeld de **[!UICONTROL Disk Usage]** rapport biedt opties voor het opnemen van elementen bij het berekenen van de schijfruimte die door elementen wordt gebruikt. U kunt ervoor kiezen om elementen in submappen op te nemen of uit te sluiten voor het berekenen van het schijfgebruik.

   >[!NOTE]
   >
   >Het rapport **[!UICONTROL Disk Usage]** bevat geen datumbereikvelden omdat het alleen het huidige gebruik van schijfruimte aangeeft.

   ![Pagina met details van rapport Schijfgebruik](assets/disk_usage_configuration.png)

   Wanneer u de opdracht **[!UICONTROL Files]** rapport, kunt u submappen opnemen/uitsluiten. U kunt echter geen elementuitvoeringen opnemen voor dit rapport.

   ![Pagina met details van rapport Bestanden](assets/files_report.png)

   De **[!UICONTROL Link Share]** rapport geeft URL&#39;s weer aan elementen die vanuit de toepassing worden gedeeld met externe gebruikers [!DNL Assets]. Het bevat e-mail-id&#39;s van de gebruiker die de assets heeft gedeeld, e-mail-id&#39;s van gebruikers met wie de assets worden gedeeld, de datum van delen en de vervaldatum voor de koppeling. De kolommen kunnen niet worden aangepast.

   De **[!UICONTROL Link Share]** rapport, bevat geen opties voor submappen en uitvoeringen omdat alleen de gedeelde URL&#39;s worden gepubliceerd die onder `/var/dam/share`.

   ![De pagina van details van het rapport van het Aandeel van de Verbinding](assets/link_share.png)

1. Klik op **[!UICONTROL Next]** op de werkbalk.

1. In de **[!UICONTROL Configure Columns]** pagina, worden sommige kolommen geselecteerd om in het rapport door gebrek te verschijnen. U kunt meer kolommen selecteren. Annuleer de selectie van een kolom om deze uit te sluiten in het rapport.

   ![De selectie van rapportkolommen selecteren of annuleren](assets/configure_columns.png)

   Als u een aangepaste kolomnaam of een aangepast eigenschappenpad wilt weergeven, configureert u de eigenschappen voor het element binair onder het dialoogvenster `jcr:content` in CRX. U kunt dit ook toevoegen via de padkiezer voor eigenschappen.

   ![De selectie van rapportkolommen selecteren of annuleren](assets/custom_columns.png)

1. Klik op **[!UICONTROL Create]** op de werkbalk. Een bericht meldt dat de rapportgeneratie is in werking gesteld.
1. Op de [!UICONTROL Asset Reports] pagina, is de status van de rapportgeneratie gebaseerd op de huidige staat van de rapportbaan, bijvoorbeeld [!UICONTROL Success], [!UICONTROL Failed], [!UICONTROL Queued], of [!UICONTROL Scheduled]. Dezelfde status wordt weergegeven in het vak met meldingen. Klik op de rapportkoppeling om de rapportpagina weer te geven. U kunt ook het rapport selecteren en op **[!UICONTROL View]** op de werkbalk.

   <!--![A generated report](assets/report_page.png)-->
   [Rapportstatus](assets/report-status.JPG)

   Klikken **[!UICONTROL Download]** van de toolbar om het rapport in CSV formaat te downloaden.

## Aangepaste kolommen toevoegen {#add-custom-columns}

U kunt douanekolommen aan de volgende rapporten toevoegen om meer gegevens voor uw douanevereisten te tonen:

* Uploaden
* Downloaden
* Verlopen
* Wijziging
* Publiceren
* [!DNL Brand Portal] publish
* Bestanden

Ga als volgt te werk om aangepaste kolommen aan deze rapporten toe te voegen:

1. In de [!DNL Manager interface], klikt u op **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Reports]**.
1. Op de [!UICONTROL Asset Reports] pagina, klikt u **[!UICONTROL Create]** op de werkbalk.

1. Van de **[!UICONTROL Create Report]** pagina, kiest u het rapport dat u wilt maken en klikt u op **[!UICONTROL Next]**.
1. Configureer rapportdetails zoals titel, beschrijving, miniatuur, mappad en datumbereik.

1. Als u een aangepaste kolom wilt weergeven, geeft u de naam op van de kolom onder **[!UICONTROL Custom Columns]**.

   ![Geef een naam op voor de aangepaste rapportkolom](assets/custom_columns-1.png)

1. Het pad naar de eigenschap toevoegen onder het dialoogvenster `jcr:content` knoop in CRXDE gebruikend de plukker van de bezitspad. U kunt ook het pad typen in het veld Pad eigenschap.

   ![Eigenschappenpad toewijzen vanuit paden in jcr:content](assets/property_picker.png)

   Klik op **[!UICONTROL Add]** en herhaal stap 5 en 6.

1. Klik op **[!UICONTROL Create]** op de werkbalk. Een bericht meldt dat de rapportgeneratie is in werking gesteld.

## De zuiveringsservice configureren {#configure-purging-service}

Om rapporten te verwijderen die u niet meer vereist, vorm de dienst van de Leegmaken van het Rapport DAM van de Webconsole om bestaande rapporten te zuiveren die op hun hoeveelheid en leeftijd worden gebaseerd.

1. Toegang tot de webconsole (configuratiemanager) vanaf `https://[aem_server]:[port]/system/console/configMgr`.
1. Open de **[!UICONTROL DAM Report Purge Service]** configuratie.
1. Geef de frequentie (tijdsinterval) voor de zuiveringsservice op in het dialoogvenster `scheduler.expression.name` veld. U kunt de leeftijd en de kwantitatieve drempel voor rapporten ook vormen.
1. Sla de wijzigingen op.

## Problemen met informatie, tips en beperkingen oplossen {#best-practices-and-limitations}

* Als sommige rapporten of nummers in de rapporten niet beschikbaar of naar verwachting zijn, controleert u of [!UICONTROL Day CQ DAM Event Recorder] service is ingeschakeld.

* Verwijder de rapporten die niet meer vereist zijn. Gebruik de configuratieopties in de DAM dienst van de Leegmaken van het Rapport om de criteria te vormen om rapporten te zuiveren.

* Als het rapport Schijfgebruik niet wordt gegenereerd en u gebruikt [!DNL Dynamic Media], zorgt u ervoor dat alle elementen correct worden uitgevoerd. U lost de problemen op door de elementen opnieuw te verwerken en vervolgens het rapport opnieuw te genereren.
