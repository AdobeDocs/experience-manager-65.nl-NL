---
title: Metagegevens van elementen bulksgewijs importeren en exporteren.
description: Bulk importeren en exporteren van metagegevens van digitale elementen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 23d19d9656d61874cd00a9a2473092be0c53b8f8
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 5%

---


# Metagegevens van elementen in bulk importeren en exporteren {#import-and-export-asset-metadata-in-bulk}

[!DNL Adobe Experience Manager Assets] Hiermee kunt u metagegevens van elementen in bulk importeren met een CSV-bestand. U kunt bulkupdates uitvoeren voor de onlangs geüploade elementen of de bestaande elementen door een CSV-bestand te importeren. U kunt ook metagegevens van elementen bulksgewijs invoeren vanuit een systeem van derden in de CSV-indeling.

## Metagegevens importeren {#import-metadata}

De import van metagegevens is asynchroon en belemmert de systeemprestaties niet. Gelijktijdige update van de metagegevens voor meerdere elementen kan vanwege de terugzetactiviteit van XMP-gegevens bronintensief zijn als de werkstroommarkering wordt gecontroleerd. Plan zo&#39;n import tijdens het gebruik van een slanke server, zodat de prestaties voor andere gebruikers niet worden beïnvloed.

>[!NOTE]
>
>Registreer de naamruimten eerst om metagegevens in aangepaste naamruimten te importeren.

1. Navigeer naar de [!DNL Assets] gebruikersinterface en klik op **[!UICONTROL Create]** de werkbalk.
1. Selecteer **[!UICONTROL Metadata]** in het menu.
1. In the **[!UICONTROL Metadata Import]** page, click **[!UICONTROL Select File]**. Selecteer het CSV-bestand met de metadata.
1. Geef de volgende parameters op. Zie een voorbeeld-CSV-bestand op [metadata-import-sample-file.csv](assets/metadata-import-sample-file.csv).

   | Parameters voor het importeren van metagegevens | Beschrijving |
   |:---|:---|
   | [!UICONTROL Batch Size] | Aantal elementen in een batch waarvoor metagegevens moeten worden geïmporteerd. De standaardwaarde is 50. Maximumwaarde is 100. |
   | [!UICONTROL Field Separator] | De standaardwaarde is `,` (een komma). U kunt elk ander teken opgeven. |
   | [!UICONTROL Multi Value Delimiter] | Scheidingsteken voor metagegevenswaarden. De standaardwaarde is `|`. |
   | [!UICONTROL Launch Workflows] | Standaard false. Wanneer de standaardinstellingen voor Launcher zijn ingesteld op `true` en van kracht zijn voor de [!UICONTROL DAM Metadata WriteBack] workflow (die metagegevens naar de binaire XMP-gegevens schrijft). Als u opstartworkflows inschakelt, wordt het systeem trager. |
   | [!UICONTROL Asset Path Column Name] | Hiermee definieert u de kolomnaam voor het CSV-bestand met elementen. |

1. Klik op **[!UICONTROL Import]** de werkbalk. Nadat de metagegevens zijn geïmporteerd, wordt een melding in [!UICONTROL Notification] Postvak IN weergegeven.

1. Navigeer naar de [!UICONTROL Properties] pagina van een element en controleer de waarden in de velden om te controleren of het element correct is geïmporteerd.

Als u datum en tijdstempel wilt toevoegen tijdens het importeren van metagegevens, gebruikt u de `YYYY-MM-DDThh:mm:ss.fff-00:00` notatie voor datum en tijd. Datum en tijd worden gescheiden door `T`, is `hh` uren in 24-uursnotatie, `fff` is nanoseconden, en `-00:00` is timezone offset. Bijvoorbeeld, `2020-03-26T11:26:00.000-07:00` is 26 maart 2020 om 11:26:00.000 AM PST tijd.

>[!CAUTION]
>
>Als de datumnotatie niet overeenkomt `YYYY-MM-DDThh:mm:ss.fff-00:00`, worden de datumwaarden niet ingesteld. De datumnotaties van het geëxporteerde CSV-bestand met metagegevens hebben de indeling `YYYY-MM-DDThh:mm:ss-00:00`. Als u het wilt invoeren, zet het in het aanvaardbare formaat door de nanosecondewaarde toe te voegen die door wordt aangegeven `fff`.

## Metagegevens exporteren {#export-metadata}

U kunt metagegevens voor meerdere elementen in CSV-indeling exporteren. De metagegevens worden asynchroon geëxporteerd en hebben geen invloed op de prestaties van het systeem. Als u metagegevens wilt exporteren, doorloopt [!DNL Experience Manager] u de eigenschappen van het knooppunt Asset `jcr:content/metadata` en de onderliggende knooppunten en exporteert u de eigenschappen van de metagegevens in een CSV-bestand.

Hier volgen enkele voorbeelden van het gebruik van metagegevens voor bulksgewijs exporteren:

* Importeer de metagegevens in een systeem van derden wanneer u elementen migreert.
* Metagegevens over elementen delen met een groter projectteam.
* Test of controleer de metagegevens op conformiteit.
* Maak de metagegevens extern om deze afzonderlijk te lokaliseren.

1. Selecteer de elementenmap die elementen bevat waarvoor u metagegevens wilt exporteren. Selecteer **[!UICONTROL Export metadata]** in de werkbalk.

1. In the [!UICONTROL Metadata Export] dialog, specify a name for the CSV file. Selecteer Metagegevens voor elementen in submappen exporteren **[!UICONTROL Include assets in subfolders]**.

   ![Interface en opties voor het exporteren van metagegevens van alle elementen in een](assets/export_metadata_page.png "folderInterface en opties voor het exporteren van metagegevens van alle elementen in een map")

1. Selecteer de gewenste opties. Geef een bestandsnaam en zo nodig een datum op.

1. Geef in het **[!UICONTROL Properties to be exported]** veld op of u alle of specifieke eigenschappen wilt exporteren. Als u Selectieve eigenschappen kiest die u wilt exporteren, voegt u de gewenste eigenschappen toe.

1. Klik **[!UICONTROL Export]** op de werkbalk. Een bericht bevestigt dat de metagegevens worden geëxporteerd. Sluit het bericht.

1. Open het bericht in het Postvak IN voor de exporttaak. Selecteer de taak en klik op **[!UICONTROL Open]** op de werkbalk. To download the CSV file with the metadata, click **[!UICONTROL CSV Download]** from the toolbar. Klik op **[!UICONTROL Close]**.

   ![Dialoogvenster voor het downloaden van het CSV-bestand met metagegevens die bulksgewijs zijn geëxporteerd](assets/csv_download.png)

   *Afbeelding: Dialoogvenster voor het downloaden van het CSV-bestand met metagegevens die bulksgewijs zijn geëxporteerd.*

## Tips en trucs, beperkingen en tips {#best-practices-limitations-tips}

* Het CSV-bestand voor het importeren van metagegevens van elementen heeft een zeer specifieke indeling. Als u moeite en tijd wilt besparen en onbedoelde fouten wilt voorkomen, kunt u de CSV-bestanden beginnen te maken met de indeling van een geëxporteerd CSV-bestand.
* Wanneer u metagegevens importeert met een CSV-bestand, is de vereiste datumnotatie `YYYY-MM-DDThh:mm:ss.fff-00:00`. Als een andere notatie wordt gebruikt, worden de datumwaarden niet ingesteld. De datumnotaties van het geëxporteerde CSV-bestand met metagegevens hebben de indeling `YYYY-MM-DDThh:mm:ss-00:00`. Als u het wilt invoeren, zet het in het aanvaardbare formaat door de nanosecondewaarde toe te voegen die door wordt aangegeven `fff`.
* Registreer de naamruimten eerst om metagegevens in aangepaste naamruimten te importeren.

>[!MORELIKETHIS]
>
>* [Metagegevens importeren en exporteren in Experience Manager-middelen](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/metadata/metadata-import-feature-video-use.html)

