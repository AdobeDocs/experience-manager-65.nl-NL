---
title: Terugschrijven naar XMP-uitvoeringen
description: Leer hoe de XMP-functie voor terugschrijven de wijzigingen in metagegevens van een element doorgeeft aan alle of specifieke uitvoeringen van het element.
contentOwner: AG
role: User, Admin
feature: Metadata
exl-id: 82148ae5-37e9-4fc5-ada9-db3d91b29c33
hide: true
solution: Experience Manager, Experience Manager Assets
source-git-commit: 0b90fdd13efc5408ef94ee1966f04a80810b515e
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 4%

---

# Terugschrijven naar XMP-uitvoeringen {#xmp-writeback-to-renditions}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/admin/xmp-metadata) |
| AEM 6.5 | Dit artikel |

Met deze XMP-schrijffunctie in [!DNL Adobe Experience Manager Assets] worden de wijzigingen in de metagegevens van de uitvoeringen van het oorspronkelijke element gerepliceerd. Wanneer u de metagegevens van een element wijzigt vanuit Assets of wanneer u het element uploadt, worden de wijzigingen in eerste instantie opgeslagen in het metagegevensknooppunt in de elementenhiërarchie.

Met de XMP-functie voor terugschrijven kunt u de wijzigingen in metagegevens doorgeven aan alle of specifieke uitvoeringen van het element. De functie schrijft alleen die metagegevenseigenschappen terug die geregistreerde naamruimten gebruiken, dat wil zeggen, een eigenschap met de naam `dc:title` wordt teruggeschreven, maar een eigenschap met de naam `mytitle` niet.

Neem bijvoorbeeld een scenario waarin u de eigenschap [!UICONTROL Title] van het element `Classic Leather` t/m `Nylon` wijzigt.

![ meta-gegevens ](assets/metadata.png)

In dit geval slaat [!DNL Experience Manager Assets] de wijzigingen in de eigenschap **[!UICONTROL Title]** op in de parameter `dc:title` voor de metagegevens van de elementen die zijn opgeslagen in de elementenhiërarchie.

![ metadata_stored ](assets/metadata_stored.png)

[!DNL Experience Manager Assets] geeft echter niet automatisch metagegevenswijzigingen door in de uitvoeringen van een element. Zie [ hoe te om XMP terug ](#enable-xmp-writeback) toe te laten.

## Terugschrijven naar XMP inschakelen {#enable-xmp-writeback}

Als u wilt dat de wijzigingen in metagegevens kunnen worden doorgegeven aan de uitvoeringen van het element tijdens het uploaden, wijzigt u de **[!UICONTROL Adobe CQ DAM Rendition Maker]** -configuratie in Configuratiebeheer.

1. Ga naar `https://[aem_server]:[port]/system/console/configMgr` om Configuration Manager te openen.
1. Open de **[!UICONTROL Adobe CQ DAM Rendition Maker]** -configuratie.
1. Selecteer de optie **[!UICONTROL Propagate XMP]** en sla de wijzigingen op.

   ![ chlimage_1-135 ](assets/chlimage_1-346.png)

## Terugschrijven van XMP inschakelen voor specifieke uitvoeringen {#enabling-xmp-writeback-for-specific-renditions}

Als u wilt dat de XMP-terugdraaifunctie wijzigingen in metagegevens doorgeeft aan geselecteerde uitvoeringen, geeft u deze uitvoeringen op in de stap voor de XMP-terugdraaiworkflow van de [!UICONTROL DAM Metadata WriteBack] -workflow. Deze stap is standaard geconfigureerd met de oorspronkelijke uitvoering.

Voer de volgende stappen uit voor de XMP-functie voor het doorgeven van metagegevens aan de vertoningsminiaturen 140.100.png en 319.319.png.

1. Navigeer in de Experience Manager-interface naar **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]** .
1. Open vanaf de pagina Modellen het workflowmodel van **[!UICONTROL DAM Metadata Writeback]** .
1. Op de pagina met eigenschappen voor **[!UICONTROL DAM Metadata Writeback]** opent u de stap **[!UICONTROL XMP Writeback Process]**.
1. Klik in het dialoogvenster [!UICONTROL Step Properties] op de tab **[!UICONTROL Process]** .
1. In het **vakje van Argumenten**, voeg `rendition:cq5dam.thumbnail.140.100.png,rendition:cq5dam.thumbnail.319.319.png` toe, en klik **[!UICONTROL OK]**.

   ![ step_properties ](assets/step_properties.png)

1. Sla de wijzigingen op.
1. Als u de TIFF-piramide voor [!DNL Dynamic Media] -afbeeldingen opnieuw wilt genereren met de nieuwe kenmerken, voegt u de stap **[!UICONTROL Dynamic Media Process Image Assets]** toe aan de [!UICONTROL DAM Metadata Writeback] -workflow.

   PTIFF-uitvoeringen worden alleen lokaal gemaakt en opgeslagen in een Dynamic Media Hybrid-implementatie.

1. Sla de workflow op.

De metagegevenswijzigingen worden doorgegeven aan de renditions thumbnail.140.100.png en thumbnail.319.319.png van het element, en niet aan de andere.

>[!NOTE]
>
>Voor de gesteunde platforms, zie [ XMP meta-gegevens schrijven-achtereerste vereisten ](/help/sites-deploying/technical-requirements.md#requirements-for-aem-assets-xmp-metadata-write-back).

## XMP-metagegevens filteren {#filtering-xmp-metadata}

[!DNL Experience Manager Assets] ondersteunt zowel het filteren van lijsten van gewezen personen als lijsten van gewenste personen van eigenschappen/knooppunten voor XMP-metagegevens die worden gelezen van elementbinaire elementen en die worden opgeslagen in JCR wanneer elementen worden opgenomen.

Als u filtert met een lijst van gewezen personen, kunt u alle eigenschappen van XMP-metagegevens importeren, behalve de eigenschappen die voor uitsluiting zijn opgegeven. Voor elementtypen zoals INDD-bestanden met grote hoeveelheden XMP-metagegevens (bijvoorbeeld 1000 knooppunten met 10.000 eigenschappen) zijn de namen van knooppunten die moeten worden gefilterd niet altijd van tevoren bekend. Als het filtreren gebruikend een lijst van gewezen personen een groot aantal activa met talrijke meta-gegevens van XMP toelaat worden ingevoerd, kan de plaatsing van [!DNL Experience Manager] stabiliteitskwesties ontmoeten, bijvoorbeeld, verstopte observatierijen.

Door het filteren van XMP-metagegevens via lijst van gewenste personen verhelpt u dit probleem door de XMP-eigenschappen te definiëren die moeten worden geïmporteerd. Op deze manier worden andere of onbekende XMP-eigenschappen genegeerd. Voor achterwaartse compatibiliteit kunt u enkele van deze eigenschappen toevoegen aan het filter dat een lijst van gewezen personen gebruikt.

>[!NOTE]
>
>Filteren werkt alleen voor de eigenschappen die zijn afgeleid van bronnen van XMP in binaire elementen. Voor de eigenschappen die van niet-XMP bronnen, zoals formaten EXIF en IPTC worden afgeleid, werkt het filtreren niet. De aanmaakdatum van elementen wordt bijvoorbeeld opgeslagen in de eigenschap `CreateDate` in EXIF TIFF. Experience Manager slaat deze waarde op in een metagegevensveld met de naam `exif:DateTimeOriginal` . Aangezien de bron een niet-XMP bron is, werkt het filtreren niet aan deze eigenschap.

1. Ga naar `https://[aem_server]:[port]/system/console/configMgr` om Configuration Manager te openen.
1. Open de **[!UICONTROL Adobe CQ DAM XmpFilter]** -configuratie.
1. Selecteer **[!UICONTROL Apply Allowlist to XMP Properties]** en geef in het vak **[!UICONTROL Allowed XML Names for XMP filtering]** de eigenschappen op die u wilt importeren als u het filteren wilt toepassen via een lijst van gewenste personen.

   ![ chlimage_1-136 ](assets/chlimage_1-347.png)

1. Als u geblokkeerde XMP-eigenschappen wilt uitfilteren nadat u filters hebt toegepast via de lijst van gewenste personen, geeft u de eigenschappen op in het vak **[!UICONTROL Blocked XML Names for XMP filtering]** .

   >[!NOTE]
   >
   >De optie **[!UICONTROL Apply Blocklist to XMP Properties]** is standaard geselecteerd. Met andere woorden, filteren met een lijst van gewezen personen wordt standaard ingeschakeld. Als u dergelijke filters wilt uitschakelen, annuleert u de selectie van de optie **[!UICONTROL Apply Blocklist to XMP Properties]** .

1. Sla de wijzigingen op.
