---
title: Terugverwijzing naar vertoningen XMP
description: Leer hoe de functie XMP terugschrijven de metagegevenswijzigingen voor een element doorgeeft aan alle of aan specifieke uitvoeringen van het element.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 9fc1201db83ae0d3bb902d4dc3ab6d78cc1dc251
workflow-type: tm+mt
source-wordcount: '722'
ht-degree: 3%

---


# Terugverwijzing naar vertoningen XMP {#xmp-writeback-to-renditions}

De XMP functie voor terugschrijven in [!DNL Adobe Experience Manager Assets] repliceert wijzigingen in de metagegevens van elementen in de uitvoeringen van het element. Wanneer u de metagegevens van een element wijzigt vanuit het element [!DNL Experience Manager Assets] of tijdens het uploaden van het element, worden wijzigingen in eerste instantie opgeslagen in het knooppunt met elementen in CRXDe. De XMP functie voor terugschrijven geeft de metagegevenswijzigingen door in alle of in specifieke uitvoeringen van het element.

Neem bijvoorbeeld een scenario waarin u de [!UICONTROL Title] eigenschap van het element `Classic Leather` met de naam wijzigt `Nylon`.

![metadata](assets/metadata.png)

In dit geval worden de wijzigingen in de [!DNL Experience Manager Assets] eigenschap in de **[!UICONTROL Title]** `dc:title` parameter opgeslagen voor de metagegevens van de elementen die in de elementenhiërarchie zijn opgeslagen.

![metadata_stored](assets/metadata_stored.png)

Wijzigingen in metagegevens in de uitvoeringen van een element worden echter [!DNL Experience Manager Assets] niet automatisch doorgegeven.

Met de functie XMP terugdraaien kunt u de wijzigingen in metagegevens doorgeven aan alle of specifieke uitvoeringen van het element. De wijzigingen worden echter niet opgeslagen onder het metagegevensknooppunt in de elementenhiërarchie. In plaats daarvan worden de wijzigingen in de binaire bestanden voor de uitvoeringen ingesloten.

## XMP terugschrijven inschakelen {#enabling-xmp-writeback}

Om de meta-gegevensveranderingen toe te laten om aan de vertoningen van de activa worden verspreid wanneer het uploaden van het, wijzig de **[!UICONTROL Adobe CQ DAM Rendition Maker]** configuratie in de Manager van de Configuratie.

1. Om de Manager van de Configuratie te openen, toegang `https://[aem_server]:[port]/system/console/configMgr`.
1. Open de **[!UICONTROL Adobe CQ DAM Rendition Maker]** configuratie.
1. Selecteer de optie **[!UICONTROL Propagate XMP[!UICONTROL ** en sla de wijzigingen op.

   ![chlimage_1-135](assets/chlimage_1-346.png)

## Terugschrijven van XMP inschakelen voor specifieke uitvoeringen {#enabling-xmp-writeback-for-specific-renditions}

Als u wilt dat de XMP terugdraaifunctie metagegevenswijzigingen doorgeeft aan geselecteerde uitvoeringen, geeft u deze uitvoeringen op in de stap XMP terugdraaiproces van de [!UICONTROL DAM Metadata WriteBack] workflow. Deze stap is standaard geconfigureerd met de oorspronkelijke uitvoering.

Voer de volgende stappen uit voor de functie XMP terugschrijven om metagegevens door te geven aan de vertoningsminiaturen 140.100.png en 319.319.png.

1. Navigeer in de interface Experience Manager naar **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. Open het **[!UICONTROL DAM Metadata Writeback]** workflowmodel op de pagina Modellen.
1. Op de pagina met eigenschappen voor **[!UICONTROL DAM Metadata Writeback]** opent u de stap **[!UICONTROL XMP Writeback Process]**.
1. In the [!UICONTROL Step Properties] dialog box, click the **[!UICONTROL Process]** tab.
1. Voeg in het vak **Argumenten** `rendition:cq5dam.thumbnail.140.100.png,rendition:cq5dam.thumbnail.319.319.png`de gewenste tekst toe en klik op **OK**.

   ![step_properties](assets/step_properties.png)

1. Sla de wijzigingen op.
1. To regenerate the pyramid TIFF renditions for [!DNL Dynamic Media] images with the new attributes, add the **[!UICONTROL Dynamic Media Process Image Assets]** step to the [!UICONTROL DAM Metadata Writeback] workflow.

   PTIFF-uitvoeringen worden alleen lokaal gemaakt en opgeslagen in een Dynamic Media Hybrid-implementatie.

1. Sla de workflow op.

De wijzigingen in de metagegevens worden doorgegeven aan de uitvoeringen miniatuur.140.100.png en miniatuur.319.319.png van het element, en niet aan de andere.

>[!NOTE]
>
>Voor XMP terugzetproblemen in Linux met 64 bits, zie [hoe te XMP terugschrijven op Linux](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html)met 64 bits toe te laten.
>
>Zie Voorwaarden voor het schrijven van [XMP metagegevens voor de ondersteunde platforms](/help/sites-deploying/technical-requirements.md#requirements-for-aem-assets-xmp-metadata-write-back).

## XMP metagegevens filteren {#filtering-xmp-metadata}

[!DNL Experience Manager Assets] ondersteunt zowel het filteren van lijsten van afgewezen personen als lijsten van gewenste personen van eigenschappen/knooppunten voor XMP metagegevens die worden gelezen van binaire elementen en worden opgeslagen in JCR wanneer elementen worden ingeslikt.

Als u filtert met een lijst van afgewezen personen, kunt u alle eigenschappen van XMP metagegevens importeren, behalve de eigenschappen die voor uitsluiting zijn opgegeven. Voor elementtypen zoals INDD-bestanden met grote hoeveelheden XMP metagegevens (bijvoorbeeld 1000 knooppunten met 10.000 eigenschappen) zijn de namen van knooppunten die moeten worden gefilterd niet altijd van tevoren bekend. Als het filtreren gebruikend een lijst van afgewezen personen een groot aantal activa met talrijke XMP meta-gegevens om toelaat worden ingevoerd, kan de [!DNL Experience Manager] plaatsing stabiliteitskwesties, bijvoorbeeld verstopte observatierijen ontmoeten.

Door het filteren van XMP metagegevens via lijst van gewenste personen wordt dit probleem opgelost doordat u de XMP eigenschappen kunt definiëren die moeten worden geïmporteerd. Op deze manier worden andere of onbekende XMP eigenschappen genegeerd. Voor achterwaartse compatibiliteit kunt u enkele van deze eigenschappen toevoegen aan het filter dat een lijst van afgewezen personen gebruikt.

>[!NOTE]
>
>Filteren werkt alleen voor de eigenschappen die zijn afgeleid van XMP bronnen in binaire elementen. Voor de eigenschappen die van niet-XMP bronnen, zoals formaten EXIF en IPTC worden afgeleid, werkt het filtreren niet. De aanmaakdatum van elementen wordt bijvoorbeeld opgeslagen in een eigenschap met de naam EXIF TIFF. `CreateDate` Experience Manager slaat deze waarde op in een metagegevensveld met de naam `exif:DateTimeOriginal`. Aangezien de bron een niet-XMP bron is, werkt het filtreren niet aan dit bezit.

1. Om de Manager van de Configuratie te openen, toegang `https://[aem_server]:[port]/system/console/configMgr`.
1. Open de **[!UICONTROL Adobe CQ DAM XmpFilter]** configuratie.
1. Als u filters wilt toepassen via een lijst van gewenste personen, selecteert u de eigenschappen die u wilt importeren in het **[!UICONTROL Apply Allowlist to XMP Properties]****[!UICONTROL Allowed XML Names for XMP filtering]** vak en geeft u deze op.

   ![chlimage_1-136](assets/chlimage_1-347.png)

1. Als u geblokkeerde XMP wilt uitfilteren nadat u filtert via lijst van gewenste personen hebt toegepast, geeft u de eigenschappen in het **[!UICONTROL Blocked XML Names for XMP filtering]** vak op.

   >[!NOTE]
   >
   >The **[!UICONTROL Apply Blocklist to XMP Properties]** option is selected by default. Met andere woorden, filteren met een lijst van afgewezen personen wordt standaard ingeschakeld. Als u dergelijke filters wilt uitschakelen, schakelt u de **[!UICONTROL Apply Blocklist to XMP Properties]** optie uit.

1. Sla de wijzigingen op.
