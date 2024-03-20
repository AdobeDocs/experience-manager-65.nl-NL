---
title: Terugverwijzing naar vertoningen XMP
description: Leer hoe de functie XMP terugschrijven de metagegevenswijzigingen voor een element doorgeeft aan alle of aan specifieke uitvoeringen van het element.
contentOwner: AG
role: User, Admin
feature: Metadata
exl-id: 82148ae5-37e9-4fc5-ada9-db3d91b29c33
hide: true
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '726'
ht-degree: 4%

---

# Terugverwijzing naar vertoningen XMP {#xmp-writeback-to-renditions}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/admin/xmp-metadata.html?lang=en) |
| AEM 6,5 | Dit artikel |

Deze XMP functie voor terugschrijven in [!DNL Adobe Experience Manager Assets] Hiermee worden de wijzigingen in de metagegevens van de uitvoeringen van het oorspronkelijke element gerepliceerd. Wanneer u de metagegevens van een element wijzigt vanuit Middelen of tijdens het uploaden van het element, worden de wijzigingen in eerste instantie opgeslagen in het metagegevensknooppunt in de elementenhiërarchie.

Met de functie XMP terugschrijven kunt u de wijzigingen in metagegevens doorgeven aan alle of specifieke uitvoeringen van het element. De functie schrijft alleen die metagegevenseigenschappen terug die geregistreerde naamruimten gebruiken, dat wil zeggen een eigenschap met de naam `dc:title` is teruggeschreven maar een eigenschap met een naam `mytitle` is niet.

Overweeg een scenario waar u wijzigt [!UICONTROL Title] eigendom van het getitelde actief `Classic Leather` tot `Nylon`.

![metagegevens](assets/metadata.png)

In dit geval worden de [!DNL Experience Manager Assets] Hiermee slaat u de wijzigingen op in de **[!UICONTROL Title]** eigenschap in de `dc:title` parameter voor de metagegevens van elementen die zijn opgeslagen in de elementhiërarchie.

![metadata_stored](assets/metadata_stored.png)

Maar [!DNL Experience Manager Assets] geeft automatisch geen metagegevenswijzigingen door aan de uitvoeringen van een element. Zie [hoe te om XMP terug te zetten](#enable-xmp-writeback).

## Terugschrijven XMP inschakelen {#enable-xmp-writeback}

Als u wilt dat de wijzigingen in metagegevens tijdens het uploaden naar de uitvoeringen van het element kunnen worden doorgegeven, wijzigt u de instelling **[!UICONTROL Adobe CQ DAM Rendition Maker]** configuratie in de Manager van de Configuratie.

1. Om de Manager van de Configuratie te openen, toegang `https://[aem_server]:[port]/system/console/configMgr`.
1. Open de **[!UICONTROL Adobe CQ DAM Rendition Maker]** configuratie.
1. Selecteer de **[!UICONTROL Propagate XMP]** en slaat u de wijzigingen op.

   ![chlimage_1-135](assets/chlimage_1-346.png)

## Terugschrijven van XMP inschakelen voor specifieke uitvoeringen {#enabling-xmp-writeback-for-specific-renditions}

Als u wilt dat de functie XMP terugschrijven wijzigingen in metagegevens doorgeeft om uitvoeringen te selecteren, geeft u deze uitvoeringen op in de stap XMP terugdraaiproces van het terugschrijfproces van [!UICONTROL DAM Metadata WriteBack] workflow. Deze stap is standaard geconfigureerd met de oorspronkelijke uitvoering.

Voer de volgende stappen uit voor de functie XMP terugschrijven om metagegevens door te geven aan de vertoningsminiaturen 140.100.png en 319.319.png.

1. Navigeer in de interface Experience Manager naar **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. Open op de pagina Modellen de knop **[!UICONTROL DAM Metadata Writeback]** workflowmodel.
1. Op de pagina met eigenschappen voor **[!UICONTROL DAM Metadata Writeback]** opent u de stap **[!UICONTROL XMP Writeback Process]**.
1. In de [!UICONTROL Step Properties] klikt u op de knop **[!UICONTROL Process]** tab.
1. In de **Argumenten** vak, toevoegen `rendition:cq5dam.thumbnail.140.100.png,rendition:cq5dam.thumbnail.319.319.png`en klik op **[!UICONTROL OK]**.

   ![step_properties](assets/step_properties.png)

1. Sla de wijzigingen op.
1. De piramide-TIFF-uitvoeringen opnieuw genereren voor [!DNL Dynamic Media] afbeeldingen met de nieuwe kenmerken toevoegen **[!UICONTROL Dynamic Media Process Image Assets]** stap naar de [!UICONTROL DAM Metadata Writeback] workflow.

   PTIFF-uitvoeringen worden alleen lokaal gemaakt en opgeslagen in een Dynamic Media Hybrid-implementatie.

1. Sla de workflow op.

De wijzigingen in de metagegevens worden doorgegeven aan de uitvoeringen miniatuur.140.100.png en miniatuur.319.319.png van het element, en niet aan de andere.

>[!NOTE]
>
>Voor XMP terugzetproblemen in 64-bits Linux raadpleegt u [XMP terugschrijven inschakelen bij 64-bits RedHat Linux](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html).
>
>Zie voor de ondersteunde platforms [Voorwaarden voor het terugschrijven van metagegevens XMP](/help/sites-deploying/technical-requirements.md#requirements-for-aem-assets-xmp-metadata-write-back).

## XMP metagegevens filteren {#filtering-xmp-metadata}

[!DNL Experience Manager Assets] ondersteunt zowel het filteren van lijsten van gewezen personen als lijsten van gewenste personen van eigenschappen/knooppunten voor XMP metagegevens die worden gelezen van binaire elementen en worden opgeslagen in JCR wanneer elementen worden ingeslikt.

Als u filtert met een lijst van gewezen personen, kunt u alle eigenschappen van XMP metagegevens importeren, behalve de eigenschappen die voor uitsluiting zijn opgegeven. Voor elementtypen zoals INDD-bestanden met grote hoeveelheden XMP metagegevens (bijvoorbeeld 1000 knooppunten met 10.000 eigenschappen) zijn de namen van knooppunten die moeten worden gefilterd niet altijd van tevoren bekend. Als door filtering met een lijst van gewezen personen een groot aantal elementen met een groot aantal XMP metagegevens kan worden geïmporteerd, [!DNL Experience Manager] de invoering kan problemen met de stabiliteit tegenkomen , bijvoorbeeld verstopte wachtrijen voor waarneming .

Door het filteren van XMP metagegevens via lijst van gewenste personen wordt dit probleem opgelost doordat u de XMP eigenschappen kunt definiëren die moeten worden geïmporteerd. Op deze manier worden andere of onbekende XMP eigenschappen genegeerd. Voor achterwaartse compatibiliteit kunt u enkele van deze eigenschappen toevoegen aan het filter dat een lijst van gewezen personen gebruikt.

>[!NOTE]
>
>Filteren werkt alleen voor de eigenschappen die zijn afgeleid van XMP bronnen in binaire elementen. Voor de eigenschappen die van niet-XMP bronnen, zoals formaten EXIF en IPTC worden afgeleid, werkt het filtreren niet. De aanmaakdatum van het element wordt bijvoorbeeld opgeslagen in een eigenschap met de naam `CreateDate` in EXIF TIFF. Experience Manager slaat deze waarde op in een metagegevensveld genaamd `exif:DateTimeOriginal`. Aangezien de bron een niet-XMP bron is, werkt het filtreren niet aan dit bezit.

1. Om de Manager van de Configuratie te openen, toegang `https://[aem_server]:[port]/system/console/configMgr`.
1. Open de **[!UICONTROL Adobe CQ DAM XmpFilter]** configuratie.
1. Als u filteren via een lijst van gewenste personen wilt toepassen, selecteert u **[!UICONTROL Apply Allowlist to XMP Properties]** en geeft u de eigenschappen op die in het dialoogvenster **[!UICONTROL Allowed XML Names for XMP filtering]** doos.

   ![chlimage_1-136](assets/chlimage_1-347.png)

1. Om geblokkeerde XMP eigenschappen na het toepassen van filter via lijst van gewenste personen uit te filteren, specificeer die in **[!UICONTROL Blocked XML Names for XMP filtering]** doos.

   >[!NOTE]
   >
   >De **[!UICONTROL Apply Blocklist to XMP Properties]** is standaard geselecteerd. Met andere woorden, filteren met een lijst van gewezen personen wordt standaard ingeschakeld. Als u dergelijke filters wilt uitschakelen, annuleert u de selectie van de optie **[!UICONTROL Apply Blocklist to XMP Properties]** -optie.

1. Sla de wijzigingen op.
