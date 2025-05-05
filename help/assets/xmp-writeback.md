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
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/admin/xmp-metadata.html?lang=nl-NL) |
| AEM 6,5 | Dit artikel |

Met deze XMP in [!DNL Adobe Experience Manager Assets] worden de wijzigingen in de metagegevens van de uitvoeringen van het oorspronkelijke element gerepliceerd. Wanneer u de metagegevens van een element wijzigt vanuit Assets of wanneer u het element uploadt, worden de wijzigingen in eerste instantie opgeslagen in het metagegevensknooppunt in de elementenhiërarchie.

Met de functie XMP terugschrijven kunt u de wijzigingen in metagegevens doorgeven aan alle of specifieke uitvoeringen van het element. De functie schrijft alleen die metagegevenseigenschappen terug die geregistreerde naamruimten gebruiken, dat wil zeggen, een eigenschap met de naam `dc:title` wordt teruggeschreven, maar een eigenschap met de naam `mytitle` niet.

Neem bijvoorbeeld een scenario waarin u de eigenschap [!UICONTROL Title] van het element `Classic Leather` t/m `Nylon` wijzigt.

![ meta-gegevens ](assets/metadata.png)

In dit geval slaat [!DNL Experience Manager Assets] de wijzigingen in de eigenschap **[!UICONTROL Title]** op in de parameter `dc:title` voor de metagegevens van de elementen die zijn opgeslagen in de elementenhiërarchie.

![ metadata_stored ](assets/metadata_stored.png)

[!DNL Experience Manager Assets] geeft echter niet automatisch metagegevenswijzigingen door in de uitvoeringen van een element. Zie [ hoe te om XMP terug ](#enable-xmp-writeback) toe te laten.

## Terugschrijven XMP inschakelen {#enable-xmp-writeback}

Als u wilt dat de wijzigingen in metagegevens kunnen worden doorgegeven aan de uitvoeringen van het element tijdens het uploaden, wijzigt u de **[!UICONTROL Adobe CQ DAM Rendition Maker]** -configuratie in Configuratiebeheer.

1. Ga naar `https://[aem_server]:[port]/system/console/configMgr` om Configuration Manager te openen.
1. Open de **[!UICONTROL Adobe CQ DAM Rendition Maker]** -configuratie.
1. Selecteer de optie **[!UICONTROL Propagate XMP]** en sla de wijzigingen op.

   ![ chlimage_1-135 ](assets/chlimage_1-346.png)

## Terugschrijven van XMP inschakelen voor specifieke uitvoeringen {#enabling-xmp-writeback-for-specific-renditions}

Als u wilt dat de functie XMP terugschrijven wijzigingen in metagegevens doorgeeft aan geselecteerde uitvoeringen, geeft u deze uitvoeringen op in de stap XMP terugdraaiproces van de [!UICONTROL DAM Metadata WriteBack] -workflow. Deze stap is standaard geconfigureerd met de oorspronkelijke uitvoering.

Voer de volgende stappen uit voor de functie XMP terugschrijven om metagegevens door te geven aan de vertoningsminiaturen 140.100.png en 319.319.png.

1. Navigeer in de interface Experience Manager naar **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]** .
1. Open vanaf de pagina Modellen het workflowmodel van **[!UICONTROL DAM Metadata Writeback]** .
1. Op de pagina met eigenschappen voor **[!UICONTROL DAM Metadata Writeback]** opent u de stap **[!UICONTROL XMP Writeback Process]**.
1. Klik in het dialoogvenster [!UICONTROL Step Properties] op de tab **[!UICONTROL Process]** .
1. In het **vakje van Argumenten**, voeg `rendition:cq5dam.thumbnail.140.100.png,rendition:cq5dam.thumbnail.319.319.png` toe, en klik **[!UICONTROL OK]**.

   ![ step_properties ](assets/step_properties.png)

1. Sla de wijzigingen op.
1. Als u de piramide-TIFF-uitvoeringen voor [!DNL Dynamic Media] -afbeeldingen opnieuw wilt genereren met de nieuwe kenmerken, voegt u de stap **[!UICONTROL Dynamic Media Process Image Assets]** toe aan de [!UICONTROL DAM Metadata Writeback] -workflow.

   PTIFF-uitvoeringen worden alleen lokaal gemaakt en opgeslagen in een Dynamic Media Hybrid-implementatie.

1. Sla de workflow op.

De wijzigingen in de metagegevens worden doorgegeven aan de uitvoeringen miniatuur.140.100.png en miniatuur.319.319.png van het element, en niet aan de andere.

>[!NOTE]
>
>Voor XMP terugschrijvingskwesties in Linux met 64 bits, zie [ hoe te XMP toe te laten schrijven-terug op Linux met 64 bits RedHat ](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html).
>
>Voor de gesteunde platforms, zie [ XMP meta-gegevens schrijven-achtervoorwaarden ](/help/sites-deploying/technical-requirements.md#requirements-for-aem-assets-xmp-metadata-write-back).

## XMP metagegevens filteren {#filtering-xmp-metadata}

[!DNL Experience Manager Assets] ondersteunt zowel het filteren van lijsten van gewezen personen als lijsten van gewenste personen van eigenschappen/knooppunten voor XMP metagegevens die worden gelezen van binaire elementen en worden opgeslagen in JCR wanneer elementen worden opgenomen.

Als u filtert met een lijst van gewezen personen, kunt u alle eigenschappen van XMP metagegevens importeren, behalve de eigenschappen die voor uitsluiting zijn opgegeven. Voor elementtypen zoals INDD-bestanden met grote hoeveelheden XMP metagegevens (bijvoorbeeld 1000 knooppunten met 10.000 eigenschappen) zijn de namen van knooppunten die moeten worden gefilterd niet altijd van tevoren bekend. Als het filtreren gebruikend een lijst van gewezen personen een groot aantal activa met talrijke XMP meta-gegevens om toelaat worden ingevoerd, kan de plaatsing van [!DNL Experience Manager] stabiliteitskwesties ontmoeten, bijvoorbeeld, verstopte observatierijen.

Door het filteren van XMP metagegevens via lijst van gewenste personen wordt dit probleem opgelost doordat u de XMP eigenschappen kunt definiëren die moeten worden geïmporteerd. Op deze manier worden andere of onbekende XMP eigenschappen genegeerd. Voor achterwaartse compatibiliteit kunt u enkele van deze eigenschappen toevoegen aan het filter dat een lijst van gewezen personen gebruikt.

>[!NOTE]
>
>Filteren werkt alleen voor de eigenschappen die zijn afgeleid van XMP bronnen in binaire elementen. Voor de eigenschappen die van niet-XMP bronnen, zoals formaten EXIF en IPTC worden afgeleid, werkt het filtreren niet. De aanmaakdatum van elementen wordt bijvoorbeeld opgeslagen in de eigenschap `CreateDate` in EXIF-TIFF. Experience Manager slaat deze waarde op in een metagegevensveld met de naam `exif:DateTimeOriginal` . Aangezien de bron een niet-XMP bron is, werkt het filtreren niet aan dit bezit.

1. Ga naar `https://[aem_server]:[port]/system/console/configMgr` om Configuration Manager te openen.
1. Open de **[!UICONTROL Adobe CQ DAM XmpFilter]** -configuratie.
1. Selecteer **[!UICONTROL Apply Allowlist to XMP Properties]** en geef in het vak **[!UICONTROL Allowed XML Names for XMP filtering]** de eigenschappen op die u wilt importeren als u het filteren wilt toepassen via een lijst van gewenste personen.

   ![ chlimage_1-136 ](assets/chlimage_1-347.png)

1. Als u geblokkeerde XMP wilt uitfilteren nadat u filtert via lijst van gewenste personen hebt toegepast, geeft u de eigenschappen op in het vak **[!UICONTROL Blocked XML Names for XMP filtering]** .

   >[!NOTE]
   >
   >De optie **[!UICONTROL Apply Blocklist to XMP Properties]** is standaard geselecteerd. Met andere woorden, filteren met een lijst van gewezen personen wordt standaard ingeschakeld. Als u dergelijke filters wilt uitschakelen, annuleert u de selectie van de optie **[!UICONTROL Apply Blocklist to XMP Properties]** .

1. Sla de wijzigingen op.
