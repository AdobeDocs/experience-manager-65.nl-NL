---
title: Verzamelingen digitale middelen beheren
description: Leer taken om verzamelingen met middelen te beheren, zoals verzamelingen maken, weergeven, verwijderen, bewerken en downloaden.
contentOwner: AG
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 91caca39b0b6c5c0c98b58be02f518901a3d90e3
workflow-type: tm+mt
source-wordcount: '2044'
ht-degree: 11%

---


# Verzamelingen beheren {#managing-collections}

Een verzameling is een set elementen binnen Adobe Experience Manager Assets. Gebruik verzamelingen om elementen tussen gebruikers te delen. De set kan een statische verzameling of een dynamische verzameling zijn die is gebaseerd op zoekresultaten.

In tegenstelling tot mappen kan een verzameling elementen van verschillende locaties bevatten. U kunt verzamelingen delen met verschillende gebruikers waaraan verschillende niveaus van bevoegdheden zijn toegewezen, zoals weergeven, bewerken, enzovoort.

U kunt meerdere verzamelingen delen met een gebruiker. Elke verzameling bevat verwijzingen naar elementen. De referentiële integriteit van activa wordt gehandhaafd over inzamelingen.

De inzamelingen zijn van de volgende types, die op de manier worden gebaseerd zij activa sorteren:

* Een verzameling die een statische referentielijst met elementen, mappen en andere verzamelingen bevat.

* Een slimme verzameling die dynamisch elementen bevat op basis van zoekcriteria.

## Toegang tot de verzamelingsconsole {#navigating-the-collections-console}

Ga **[!UICONTROL Collections]** in de Experience Manager-interface naar **[!UICONTROL Assets]** > **[!UICONTROL Collections]**.

## Een verzameling maken {#creating-a-collection}

U kunt een verzameling maken met [statische verwijzingen](#creating-a-collection-with-static-references) of op basis van een op [zoekcriteria gebaseerd filter](#creating-a-smart-collection). U kunt ook een verzameling maken van een lichtbak.

### Een verzameling met statische verwijzingen maken {#creating-a-collection-with-static-references}

U kunt een verzameling maken met statische verwijzingen, bijvoorbeeld een verzameling met verwijzingen naar elementen, mappen, verzamelingen, centrifuges en afbeeldingssets.

1. Navigate to the **[!UICONTROL Collections]** console.
1. Klik **[!UICONTROL Create]** op de werkbalk.
1. Voer op de **[!UICONTROL Create Collection]** pagina een titel en een optionele beschrijving in voor de verzameling.
1. Voeg leden toe aan de verzameling en wijs de juiste machtigingen toe. U kunt ook **[!UICONTROL Public Collection]** selecteren om alle gebruikers toegang te geven tot de verzameling.

   >[!NOTE]
   >
   >Om de leden toe te laten om inzamelingen met andere gebruikers te delen, verstrek de `dam-users` groep lees toestemmingen bij de weg `home/users`. Geef gebruikers op de `/content/dam/collections` locatie toestemming om de verzamelingen in pop-uplijsten weer te geven. U kunt de gebruiker ook deel laten uitmaken van een `dam-users` groep.

1. (Optioneel) Voeg een miniatuurafbeelding toe voor de verzameling.
1. Click **[!UICONTROL Create]**, and then click **[!UICONTROL OK]** to close the dialog. Een verzameling met de opgegeven titel en eigenschappen wordt geopend in de console voor verzamelingen.

   >[!NOTE]
   >
   >Met Experience Manager Assets kunt u controletaken voor een verzameling maken, vergelijkbaar met de manier waarop u overzichtstaken voor een map met middelen maakt.

   Navigeer naar de gebruikersinterface Elementen om elementen aan de verzameling toe te voegen. Zie Elementen [toevoegen aan een verzameling](#adding-assets-to-a-collection)voor meer informatie.

### Verzamelingen maken met dropzone {#create-collections-using-dropzone}

U kunt elementen van de interface Elementen naar een verzameling slepen. U kunt ook een kopie van een verzameling maken en de elementen daar slepen.

1. Selecteer in de gebruikersinterface Elementen de elementen die u aan een verzameling wilt toevoegen.
1. Sleep de elementen naar de **[!UICONTROL Drop in Collection]** zone. Alternatively, click **[!UICONTROL To Collection]** from the toolbar.

   ![drop_in_collection](assets/drop_in_collection.png)

1. Klik op de werkbalk op de **[!UICONTROL Add To Collection]** **[!UICONTROL Create Collection]** pagina.

   If you want to add the assets to an existing collection, select it from the page, and click **[!UICONTROL Add]**. Standaard wordt de laatst bijgewerkte verzameling geselecteerd.

1. Geef in het dialoogvenster **[!UICONTROL Create New Collection]** een naam op voor de verzameling. Selecteer **[!UICONTROL Public Collection]** als u de verzameling toegankelijk wilt maken voor alle gebruikers.
1. Klik **[!UICONTROL Continue]** om de verzameling te maken.

### Een slimme verzameling maken {#creating-a-smart-collection}

Een slimme verzameling gebruikt zoekcriteria om elementen dynamisch te vullen. U kunt een slimme verzameling alleen maken met behulp van bestanden en niet met behulp van mappen of bestanden en mappen.

Voer de volgende stappen uit om een slimme verzameling te maken:

1. Navigeer naar de gebruikersinterface Elementen en klik op Zoeken.

1. Typ het zoekwoord in het vak Zoeken en druk op `Enter`. Open het deelvenster Filters en pas een zoekfilter toe.

1. From the **[!UICONTROL Files & Folders]** list, select **[!UICONTROL Files]**.

   ![files_option](assets/files_option.png)

1. Klik op **[!UICONTROL Save Smart Collection]**.

1. Geef een naam op voor de verzameling. Selecteer deze optie **[!UICONTROL Public]** om de groep DAM-gebruikers met de rol Viewer toe te voegen aan de slimme verzameling.

   ![save_collection](assets/save_collection.png)

   >[!NOTE]
   >
   >Als u selecteert **[!UICONTROL Public]**, wordt de slimme verzameling beschikbaar voor iedereen met de rol van eigenaar nadat u deze hebt gemaakt. Als u de **[!UICONTROL Public]** optie uitschakelt, wordt de DAM-gebruikersgroep niet meer gekoppeld aan de slimme verzameling.

1. Click **[!UICONTROL Save]** to create the smart collection, and then close the message box to complete the process.

   The new smart collection is also added to the **[!UICONTROL Saved Searches]** list.

   ![collection_list](assets/collection_listing.png)

   Het label van de knop **[!UICONTROL Create Smart Selection]** verandert in **[!UICONTROL Edit Smart Selection]**. Als u de instellingen van de slimme verzameling wilt bewerken, selecteert u **[!UICONTROL Files]** in de lijst **[!UICONTROL Files & Folders]**. Then, Click the **[!UICONTROL Edit Smart Selection]** button.

   ![chlimage_1-7](assets/chlimage_1-112.png)

## Elementen toevoegen aan een verzameling {#adding-assets-to-a-collection}

U kunt elementen toevoegen aan een verzameling die een lijst met bestanden of mappen waarnaar wordt verwezen, bevat. Slimme verzamelingen gebruiken een zoekquery om elementen te vullen. Daarom zijn statische verwijzingen naar elementen en mappen niet op hen van toepassing.

1. Selecteer het element in de gebruikersinterface Elementen en klik op **[!UICONTROL To Collection]** de werkbalk.

   ![chlimage_1-8](assets/chlimage_1-113.png)

   U kunt het element ook naar het **[!UICONTROL Drop in Collection]** gebied op de interface slepen. Voeg de elementen toe wanneer het label van het gebied verandert in **[!UICONTROL Drop to Add]**.

1. Selecteer op de **[!UICONTROL Add To Collection]** pagina de verzameling waaraan u het element wilt toevoegen.

1. Klik **[!UICONTROL Add]** en sluit het bevestigingsbericht. Het element wordt toegevoegd aan de collectie.

## Een slimme verzameling bewerken {#editing-a-smart-collection}

Slimme verzamelingen worden gemaakt door een zoekopdracht op te slaan, zodat u de inhoud kunt wijzigen door de zoekparameters van de [opgeslagen zoekopdracht](#saved-searches)te wijzigen.

1. Klik in de gebruikersinterface Elementen op de ![zoekoptie](assets/do-not-localize/search_icon.png) in de werkbalk.
1. Met de curseur in het vakje van het Onderzoek, duw op de sleutel van de Terugkeer.
1. Open het deelvenster Filters in de Experience Manager-interface.
1. Selecteer in de lijst met **[!UICONTROL Saved Searches]** de slimme verzameling die u wilt wijzigen. In het deelvenster Zoeken worden de filters weergegeven die zijn geconfigureerd voor de opgeslagen zoekopdracht.

   ![select_smart_collection](assets/select_smart_collection.png)

1. From the **[!UICONTROL Files & Folders]** list, select **[!UICONTROL Files]**.
1. Wijzig desgewenst een of meer filters. Klik op **[!UICONTROL Edit Smart Collection]**.

   U kunt ook de naam van de slimme verzameling bewerken.

   ![edit_smart_collectiondialog](assets/edit_smart_collectiondialog.png)

1. Klik op **[!UICONTROL Save]**. Het **[!UICONTROL Edit Smart Collection]** dialoogvenster verschijnt.
1. Klik **[!UICONTROL Overwrite]** om de originele slimme verzameling te vervangen door de bewerkte verzameling. U kunt ook selecteren **[!UICONTROL Save As]** om de bewerkte verzameling afzonderlijk op te slaan.
1. Klik in het bevestigingsdialoogvenster **[!UICONTROL Save]** om het proces te voltooien.

## Metagegevens van verzamelingen weergeven en bewerken {#viewing-and-editing-collection-metadata}

De meta-gegevens van de inzameling omvat gegevens over de inzameling, met inbegrip van om het even welke markeringen die worden toegevoegd.

1. Selecteer in de [!UICONTROL Collections] console een verzameling en klik op **[!UICONTROL Properties]** de werkbalk.
1. In the **[!UICONTROL Collection Metadata]** page, view the collection metadata from the **[!UICONTROL Basic]** and **[!UICONTROL Advanced]** tabs.
1. Wijzig desgewenst de metagegevens. Klik op de werkbalk om de wijzigingen op te slaan. **[!UICONTROL Save & Close]**

## Metagegevens van meerdere verzamelingen bulksgewijs bewerken {#editing-collection-metadata-in-bulk}

U kunt de metagegevens van meerdere verzamelingen tegelijk bewerken. Deze functionaliteit helpt u snel gemeenschappelijke meta-gegevens in veelvoudige inzamelingen te herhalen.

1. Selecteer twee of meer verzamelingen in de verzamelingsconsole.
1. Klik **[!UICONTROL Properties]** op de werkbalk.
1. Bewerk desgewenst de metadata op de pagina **[!UICONTROL Collection Metadata]** onder de tabbladen **[!UICONTROL Basic]** en **[!UICONTROL Advanced]**.
1. Als u de eigenschappen van metagegevens voor een specifieke verzameling wilt weergeven, schakelt u de overige verzamelingen in de lijst met verzamelingen uit. De gebieden van de meta-gegevensredacteur zijn bevolkt met de meta-gegevens voor de bepaalde inzameling.

   >[!NOTE]
   >
   >* In de [!UICONTROL Properties] pagina kunt u verzamelingen verwijderen uit de lijst met verzamelingen door ze te deselecteren. Alle verzamelingen zijn standaard geselecteerd in de lijst met verzamelingen. Experience Manager werkt de metagegevens van de verzamelingen die u verwijdert niet bij.
   >* Schakel boven aan de lijst het selectievakje in **[!UICONTROL Title]** om te schakelen tussen het selecteren van de verzamelingen en het wissen van de lijst.


1. Klik **[!UICONTROL Save & Close]** van de toolbar, en sluit dan de bevestigingsdialoog.
1. Selecteer **[!UICONTROL Append mode]** om de nieuwe metadata toe te voegen aan de bestaande metadata. Als u deze optie niet selecteert, worden de bestaande metadata in de velden vervangen door de nieuwe metadata. Klik op **[!UICONTROL Submit]**.

   >[!NOTE]
   >
   >De metagegevens die u voor de geselecteerde verzamelingen toevoegt, overschrijven de vorige metagegevens voor deze verzamelingen. Met de optie [!UICONTROL Append mode] kunt u nieuwe waarden toevoegen aan de bestaande metagegevens in de velden die meerdere waarden kunnen bevatten. Velden met één waarde worden altijd overschreven. Alle tags die u in het [!UICONTROL Tags] veld toevoegt, worden toegevoegd aan de bestaande lijst met tags in de metagegevens.

Gebruik de Schema-editor om de [!UICONTROL Properties] pagina met metagegevens aan te passen, inclusief het toevoegen, wijzigen of verwijderen van eigenschappen van metagegevens.

>[!TIP]
>
>De bulkbewerkingsmethode werkt voor elementen die beschikbaar zijn in een verzameling. Voor de elementen die beschikbaar zijn in verschillende mappen of die voldoen aan een algemeen criterium, is het mogelijk om de metagegevens na het zoeken [in grote](/help/assets/search-assets.md#metadataupdates)hoeveelheden bij te werken.

## Verzamelingen zoeken {#searching-collections}

U kunt inzamelingen van de console van Inzamelingen zoeken. Wanneer u in het vak Zoeken met trefwoorden zoekt, zoekt Middelen naar namen van verzamelingen, metagegevens en de tags die aan de verzamelingen zijn toegevoegd.

Als u zoekt naar verzamelingen op het hoogste niveau, worden alleen afzonderlijke verzamelingen geretourneerd in zoekresultaten. Elementen of mappen in de verzamelingen zijn uitgesloten. In alle andere gevallen (bijvoorbeeld in een afzonderlijke verzameling of in een mappenhiërarchie) worden alle relevante elementen, mappen en verzamelingen geretourneerd.

## Zoeken in verzamelingen {#searching-within-collections}

Klik in de console Verzamelingen op een verzameling om deze te openen.

In een verzameling is het zoeken in Experience Manager beperkt tot elementen (en de bijbehorende tags en metagegevens) in de verzameling die u bekijkt. Wanneer u in een map zoekt, worden alle overeenkomende elementen en onderliggende mappen in de huidige map geretourneerd. Wanneer u in een verzameling zoekt, worden alleen overeenkomende elementen, mappen en andere verzamelingen geretourneerd die directe leden van de verzameling zijn.

## Verzamelingsinstellingen bewerken {#editing-collection-settings}

U kunt verzamelingsinstellingen bewerken, zoals titel en beschrijving, of leden toevoegen aan een verzameling.

1. Selecteer een verzameling en klik op **[!UICONTROL Settings]** de werkbalk. U kunt ook de **[!UICONTROL Settings]** snelle actie van de miniatuur van de verzameling gebruiken.
1. Wijzig de verzamelingsinstellingen op de pagina **[!UICONTROL Collection Settings]**. For example, modify the collection title, descriptions, members, and permissions as discussed in [Adding Collections](#creating-a-collection).

1. Klik op **[!UICONTROL Save]** om de wijzigingen op te slaan.

## Een verzameling verwijderen {#deleting-a-collection}

1. Selecteer een of meer verzamelingen in de console Verzamelingen en klik op Verwijderen op de werkbalk.

1. Klik in het dialoogvenster **[!UICONTROL Delete]** om de verwijderactie te bevestigen.

   >[!NOTE]
   >
   >U kunt slimme verzamelingen ook verwijderen door opgeslagen zoekopdrachten [te verwijderen](#saved-searches).

## Een verzameling downloaden {#downloading-a-collection}

Wanneer u een verzameling downloadt, wordt de volledige hiërarchie van elementen in de verzameling gedownload, inclusief mappen en onderliggende verzamelingen.

1. Selecteer een of meer verzamelingen die u wilt downloaden in de console Verzamelingen.
1. Klik **[!UICONTROL Download]** op de werkbalk.
1. In the **[!UICONTROL Download]** dialog, click **[!UICONTROL Download]**. Selecteer **[!UICONTROL Renditions]**. Selecteer de **[!UICONTROL Email]** optie voor het verzenden van een e-mailbericht naar de eigenaar van de verzameling.

   Wanneer u een verzameling selecteert die u wilt downloaden, wordt de volledige maphiërarchie onder de verzameling gedownload. Als u elke verzameling die u downloadt (inclusief elementen in onderliggende verzamelingen die onder de bovenliggende verzameling zijn genest), in een afzonderlijke map wilt opnemen, selecteert u **[!UICONTROL Create separate folder for each asset]**.

## Geneste verzamelingen maken {#creating-nested-collections}

U kunt een verzameling toevoegen aan een andere verzameling en zo een geneste verzameling maken.

1. Selecteer in de verzamelingsconsole de gewenste verzameling of groep verzamelingen en klik op **[!UICONTROL To Collection]** de werkbalk.

1. Selecteer op de **[!UICONTROL Add To Collection]** pagina de verzameling waarin u de verzameling wilt toevoegen.

   >[!NOTE]
   >
   >De laatst bijgewerkte verzameling is standaard geselecteerd op de **[!UICONTROL Add To Collection]** pagina.

1. Klik op **[!UICONTROL Add]**. Een bericht bevestigt dat de inzameling aan de doelinzameling in de **[!UICONTROL Select Destination]** pagina wordt toegevoegd. Sluit het bericht om het proces te voltooien.

>[!NOTE]
>
>Slimme verzamelingen kunnen niet worden genest. Met andere woorden, slimme verzamelingen kunnen geen andere verzameling bevatten.

## Opgeslagen zoekopdrachten {#saved-searches}

In de gebruikersinterface Assets kunt u op basis van bepaalde regels, zoekcriteria of aangepaste zoekfacetten zoeken of filteren. Als u deze opslaat als **[!UICONTROL Saved Searches]**, kunt u ze later openen vanuit de lijst **[!UICONTROL Saved Searches]** in het deelvenster Filteren. Als u een opgeslagen zoekopdracht maakt, wordt ook een slimme verzameling gemaakt.

![saved_search_list](assets/saved_searches_list.png)

Opgeslagen zoekopdrachten worden gemaakt wanneer u een slimme verzameling maakt. Slimme verzamelingen worden automatisch toegevoegd aan de lijst met **[!UICONTROL Saved Searches]**. The [!UICONTROL Saved Searches] query for the collection is saved in the `dam:query` property in CRXDE at the relative location `/content/dam/collections/`. Er gelden geen limieten voor de zoekopdrachten die u kunt opslaan en voor de opgeslagen zoekopdrachten die in de lijst worden weergegeven.

>[!NOTE]
>
>U kunt slimme verzamelingen op dezelfde manier delen als statische verzamelingen.

Opgeslagen zoekopdrachten bewerken is hetzelfde als slimme verzamelingen bewerken. Zie Een slimme verzameling [](#editing-a-smart-collection)bewerken voor meer informatie.

Voer de volgende stappen uit om opgeslagen zoekopdrachten te verwijderen:

1. Klik in de gebruikersinterface Middelen op de ![zoekoptie](assets/do-not-localize/search_icon.png).
1. Met de curseur op het gebied van Onderzoek, druk de sleutel van de Terugkeer.
1. Open het deelvenster Filters in de Experience Manager-interface.
1. From the **[!UICONTROL Saved Searches]** list, click **[!UICONTROL Delete]** next to the smart collection that you want to delete.

   ![select_smart_collection](assets/select_smart_collection.png)

1. Klik in het dialoogvenster **[!UICONTROL Delete]** om de opgeslagen zoekopdracht te verwijderen.

## Een workflow op een verzameling uitvoeren {#running-a-workflow-on-a-collection}

U kunt een workflow voor de elementen in een verzameling uitvoeren. Als de verzameling geneste verzamelingen bevat, wordt de workflow ook uitgevoerd op de elementen in de geneste verzamelingen. Als de verzameling en de geneste verzameling echter dubbele elementen bevatten, wordt de workflow slechts eenmaal uitgevoerd voor dergelijke elementen.

1. Open **[!UICONTROL Assets]** > **[!UICONTROL Collections]**. Selecteer een specifieke verzameling als u een workflow op die verzameling wilt uitvoeren.
1. Open **[!UICONTROL Timeline]** spoorstaaf. Klik ![omhoog](assets/do-not-localize/chevron-up-icon.png) chevron en klik **[!UICONTROL Start Workflow]**.
1. In the **[!UICONTROL Start Workflow]** section, select a workflow model from the list. Selecteer bijvoorbeeld het **[!UICONTROL DAM Update Asset]** model.
1. Voer een titel in voor de workflow en klik op **[!UICONTROL Start]**.
1. Klik in het dialoogvenster op **[!UICONTROL Proceed]**. De workflow verwerkt alle elementen in de geselecteerde verzameling.

>[!MORELIKETHIS]
>
>* [E-mailberichten voor Experience Manager Assets configureren](/help/sites-administering/notification.md#assetsconfig)
>* [Een revisietaak maken voor verzamelingen](bulk-approval.md)

