---
title: Metagegevens van elementen in bulk importeren en exporteren
description: Metagegevens van elementen in bulk importeren en exporteren
contentOwner: AG
translation-type: tm+mt
source-git-commit: 07c1a4102539ba4678c55dee3a4882101e39864f

---


# Metagegevens van elementen in bulk importeren en exporteren {#import-and-export-asset-metadata-in-bulk}

Met AEM-middelen kunt u metagegevens van elementen in bulk importeren met behulp van een CSV-bestand. U kunt bulkupdates uitvoeren voor de onlangs geüploade elementen of de bestaande elementen door een CSV-bestand te importeren. U kunt ook metagegevens van elementen bulksgewijs invoeren vanuit een systeem van derden in de CSV-indeling.

## Metagegevens importeren {#import-metadata}

De import van metagegevens is asynchroon en belemmert de systeemprestaties niet. Gelijktijdige update van de metagegevens voor meerdere elementen kan vanwege de terugzetactiviteit van XMP-gegevens bronintensief zijn als de werkstroommarkering wordt gecontroleerd. Plan zo&#39;n import tijdens het gebruik van een slanke server, zodat de prestaties voor andere gebruikers niet worden beïnvloed.

>[!NOTE]
>
>Registreer de naamruimten eerst om metagegevens in aangepaste naamruimten te importeren.

1. Navigeer naar de gebruikersinterface Middelen en tik op **[!UICONTROL Maken]** /klik op de werkbalk.
1. Selecteer **[!UICONTROL Metagegevens]** in het menu.
1. Tik op de pagina **[!UICONTROL Metagegevens importeren]** of klik op **[!UICONTROL Bestand]** selecteren. Selecteer het CSV-bestand met de metagegevens.
1. Geef de volgende parameters op:

   | Parameters voor het importeren van metagegevens | Beschrijving |
   |:---|:---|
   | [!UICONTROL Batchgrootte] | Aantal elementen in een batch waarvoor metagegevens moeten worden geïmporteerd. De standaardwaarde is 50. Maximumwaarde is 100. |
   | [!UICONTROL Veldscheidingsteken] | De standaardwaarde is `,` (een komma). U kunt elk ander teken opgeven. |
   | [!UICONTROL Meerdere waarden scheidingsteken] | Scheidingsteken voor metagegevenswaarden. De standaardwaarde is `|`. |
   | [!UICONTROL Workflows starten] | Standaard false. Als de standaardinstellingen voor Launcher zijn ingesteld op `true` en standaard zijn ingesteld voor de DAM Metadata WriteBack Workflow (die metagegevens naar de binaire XMP-gegevens schrijft). Als u opstartworkflows inschakelt, wordt het systeem trager. |
   | [!UICONTROL Kolomnaam elementpad] | Hiermee definieert u de kolomnaam voor het CSV-bestand met elementen. |

1. Tik/klik op **[!UICONTROL Importeren]** op de werkbalk. Nadat de metagegevens zijn geïmporteerd, wordt een melding verzonden naar het Postvak Melding. Navigeer naar de eigenschappenpagina voor elementen en controleer of de metagegevenswaarden correct zijn geïmporteerd voor elementen.

## Metagegevens exporteren {#export-metadata}

U kunt metagegevens voor meerdere elementen in CSV-indeling exporteren. De metagegevens worden asynchroon geëxporteerd en hebben geen invloed op de prestaties van het systeem. Als u metagegevens wilt exporteren, doorloopt AEM de eigenschappen van het knooppunt Asset `jcr:content/metadata` en de onderliggende knooppunten en exporteert de eigenschappen van de metagegevens in een CSV-bestand.

Hier volgen enkele voorbeelden van het gebruik van metagegevens voor bulksgewijs exporteren:

* Importeer de metagegevens in een systeem van derden wanneer u elementen migreert.
* Metagegevens over elementen delen met een groter projectteam.
* Test of controleer de metagegevens op conformiteit.
* De metagegevens extern maken voor afzonderlijke lokalisatie.

1. Selecteer de elementenmap die elementen bevat waarvoor u metagegevens wilt exporteren. Selecteer Metagegevens **** exporteren in de werkbalk.
1. Geef in het dialoogvenster Metagegevens exporteren een naam op voor het CSV-bestand. Selecteer Elementen **[!UICONTROL opnemen in submappen]** als u metagegevens voor elementen in submappen wilt exporteren.

   ![Interface en opties voor het exporteren van metagegevens van alle elementen in een](assets/export_metadata_page.png "folderInterface en opties voor het exporteren van metagegevens van alle elementen in een map")

1. Selecteer de gewenste opties. Geef een bestandsnaam en zo nodig een datum op.

1. Geef in het veld **[!UICONTROL Eigenschappen die u wilt exporteren]** op of u alle of specifieke eigenschappen wilt exporteren. Als u Selectieve eigenschappen kiest die u wilt exporteren, voegt u de gewenste eigenschappen toe.

1. Tik op de werkbalk of klik op **[!UICONTROL Exporteren]**. Een bericht bevestigt dat de metagegevens worden geëxporteerd. Sluit het bericht.
1. Open het bericht in het Postvak IN voor de exporttaak. Selecteer de taak en klik op **[!UICONTROL Openen]** op de werkbalk. Tik op of klik op **[!UICONTROL CSV-download]** op de werkbalk om het CSV-bestand met de metagegevens te downloaden. Click **[!UICONTROL Close]**.

   ![Dialoogvenster voor het downloaden van het CSV-bestand met metagegevens die bulksgewijs zijn geëxporteerd](assets/csv_download.png)
   *Afbeelding: Dialoogvenster voor het downloaden van het CSV-bestand met metagegevens die bulksgewijs zijn geëxporteerd*

>[!MORELIKETHIS]
>
>* [Metagegevens importeren en exporteren in AEM-elementen](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/metadata/metadata-import-feature-video-use.html)

