---
title: Terugverwijzing naar vertoningen XMP
description: Leer hoe de functie XMP terugschrijven de metagegevenswijzigingen voor een element doorgeeft aan alle of aan specifieke uitvoeringen van het element.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 7faa6638eff422599450946a257e53970d25189c
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 3%

---


# Terugverwijzing naar vertoningen XMP {#xmp-writeback-to-renditions}

Met deze XMP schrijffunctie in [!DNL Adobe Experience Manager Assets] worden de wijzigingen in metagegevens in de uitvoeringen van het oorspronkelijke element gerepliceerd. Wanneer u de metagegevens van een element wijzigt vanuit Middelen of tijdens het uploaden van het element, worden de wijzigingen in eerste instantie opgeslagen in het metagegevensknooppunt in de elementenhiërarchie.

Met de functie XMP terugschrijven kunt u de wijzigingen in metagegevens doorgeven aan alle of specifieke uitvoeringen van het element. De eigenschap schrijft slechts die meta-gegevenseigenschappen terug die `jcr` namespace gebruiken, namelijk wordt een bezit genoemd `dc:title` teruggeschreven maar een bezit genoemd `mytitle` is niet.

Overweeg een scenario waarbij u de [!UICONTROL Title] eigenschap van het element `Classic Leather` aan `Nylon` wijzigt.

![metadata](assets/metadata.png)

In dit geval slaat [!DNL Experience Manager Assets] de wijzigingen in de eigenschap **[!UICONTROL Title]** op in de parameter `dc:title` voor de metagegevens van elementen die zijn opgeslagen in de elementenhiërarchie.

![metadata_stored](assets/metadata_stored.png)

[!DNL Experience Manager Assets] geeft echter niet automatisch metagegevenswijzigingen door in de uitvoeringen van een element. Zie [hoe te om XMP terug ](#enable-xmp-writeback) toe te laten.

## Terugschrijven XMP {#enable-xmp-writeback} inschakelen

Om de meta-gegevensveranderingen toe te laten om aan de vertoningen van de activa worden verspreid wanneer het uploaden van het, wijzig de **[!UICONTROL Adobe CQ DAM Rendition Maker]** configuratie in de Manager van de Configuratie.

1. Om de Manager van de Configuratie te openen, toegang `https://[aem_server]:[port]/system/console/configMgr`.
1. Open de **[!UICONTROL Adobe CQ DAM Rendition Maker]** configuratie.
1. Selecteer de optie **[!UICONTROL Propagate XMP]** en sla de wijzigingen op.

   ![chlimage_1-135](assets/chlimage_1-346.png)

## Terugschrijven van XMP inschakelen voor specifieke uitvoeringen {#enabling-xmp-writeback-for-specific-renditions}

Als u wilt dat de functie XMP terugschrijven wijzigingen in metagegevens doorgeeft aan geselecteerde uitvoeringen, geeft u deze uitvoeringen op in de stap XMP terugdraaiproces van [!UICONTROL DAM Metadata WriteBack] workflow. Deze stap is standaard geconfigureerd met de oorspronkelijke uitvoering.

Voer de volgende stappen uit voor de functie XMP terugschrijven om metagegevens door te geven aan de vertoningsminiaturen 140.100.png en 319.319.png.

1. Navigeer in de interface Experience Manager naar **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. Open op de pagina Modellen het workflowmodel **[!UICONTROL DAM Metadata Writeback]**.
1. Op de pagina met eigenschappen voor **[!UICONTROL DAM Metadata Writeback]** opent u de stap **[!UICONTROL XMP Writeback Process]**.
1. Klik in het dialoogvenster [!UICONTROL Step Properties] op het tabblad **[!UICONTROL Process]**.
1. Voeg `rendition:cq5dam.thumbnail.140.100.png,rendition:cq5dam.thumbnail.319.319.png` toe in het tekstvak **Argumenten** en klik op **[!UICONTROL OK]**.

   ![step_properties](assets/step_properties.png)

1. Sla de wijzigingen op.
1. Als u de piramide TIFF-uitvoeringen voor [!DNL Dynamic Media] afbeeldingen met de nieuwe kenmerken opnieuw wilt genereren, voegt u de stap **[!UICONTROL Dynamic Media Process Image Assets]** toe aan de [!UICONTROL DAM Metadata Writeback]-workflow.

   PTIFF-uitvoeringen worden alleen lokaal gemaakt en opgeslagen in een Dynamic Media Hybrid-implementatie.

1. Sla de workflow op.

De wijzigingen in de metagegevens worden doorgegeven aan de uitvoeringen miniatuur.140.100.png en miniatuur.319.319.png van het element, en niet aan de andere.

>[!NOTE]
>
>Zie [Hoe kan ik XMP terugschrijven inschakelen bij 64-bits RedHat Linux](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html) voor XMP terugschrijvingsproblemen in Linux met 64 bits.
>
>Zie [XMP voorwaarden voor het terugschrijven van metagegevens](/help/sites-deploying/technical-requirements.md#requirements-for-aem-assets-xmp-metadata-write-back) voor de ondersteunde platforms.

## XMP metagegevens filteren {#filtering-xmp-metadata}

[!DNL Experience Manager Assets] ondersteunt zowel het filteren van lijsten van gewezen personen als lijsten van gewenste personen van eigenschappen/knooppunten voor XMP metagegevens die worden gelezen van binaire elementen en worden opgeslagen in JCR wanneer elementen worden ingeslikt.

Als u filtert met een lijst van gewezen personen, kunt u alle eigenschappen van XMP metagegevens importeren, behalve de eigenschappen die voor uitsluiting zijn opgegeven. Voor elementtypen zoals INDD-bestanden met grote hoeveelheden XMP metagegevens (bijvoorbeeld 1000 knooppunten met 10.000 eigenschappen) zijn de namen van knooppunten die moeten worden gefilterd niet altijd van tevoren bekend. Als het filtreren gebruikend een lijst van gewezen personen een groot aantal activa met talrijke XMP meta-gegevens om toelaat worden ingevoerd, kan de [!DNL Experience Manager] plaatsing stabiliteitskwesties ontmoeten, bijvoorbeeld verstopte observatierijen.

Door het filteren van XMP metagegevens via lijst van gewenste personen wordt dit probleem opgelost doordat u de XMP eigenschappen kunt definiëren die moeten worden geïmporteerd. Op deze manier worden andere of onbekende XMP eigenschappen genegeerd. Voor achterwaartse compatibiliteit kunt u enkele van deze eigenschappen toevoegen aan het filter dat een lijst van gewezen personen gebruikt.

>[!NOTE]
>
>Filteren werkt alleen voor de eigenschappen die zijn afgeleid van XMP bronnen in binaire elementen. Voor de eigenschappen die van niet-XMP bronnen, zoals formaten EXIF en IPTC worden afgeleid, werkt het filtreren niet. De aanmaakdatum van elementen wordt bijvoorbeeld opgeslagen in de eigenschap `CreateDate` in EXIF TIFF. Experience Manager slaat deze waarde op in een metagegevensveld met de naam `exif:DateTimeOriginal`. Aangezien de bron een niet-XMP bron is, werkt het filtreren niet aan dit bezit.

1. Om de Manager van de Configuratie te openen, toegang `https://[aem_server]:[port]/system/console/configMgr`.
1. Open de **[!UICONTROL Adobe CQ DAM XmpFilter]** configuratie.
1. Als u filteren via een lijst van gewenste personen wilt toepassen, selecteert u **[!UICONTROL Apply Allowlist to XMP Properties]** en geeft u in het vak **[!UICONTROL Allowed XML Names for XMP filtering]** de eigenschappen op die u wilt importeren.

   ![chlimage_1-136](assets/chlimage_1-347.png)

1. Om geblokkeerde XMP eigenschappen na het toepassen van filter via lijst van gewenste personen uit te filtreren, specificeer die in **[!UICONTROL Blocked XML Names for XMP filtering]** doos.

   >[!NOTE]
   >
   >De optie **[!UICONTROL Apply Blocklist to XMP Properties]** is standaard geselecteerd. Met andere woorden, filteren met een lijst van gewezen personen wordt standaard ingeschakeld. Als u dergelijke filters wilt uitschakelen, annuleert u de selectie van de optie **[!UICONTROL Apply Blocklist to XMP Properties]**.

1. Sla de wijzigingen op.
