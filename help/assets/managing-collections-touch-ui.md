---
title: Verzamelingen digitale middelen beheren
description: Leer taken om verzamelingen met middelen te beheren, zoals verzamelingen maken, weergeven, verwijderen, bewerken en downloaden.
contentOwner: AG
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: c7d0bcbf39adfc7dfd01742651589efb72959603

---


# Verzamelingen beheren {#managing-collections}

Een verzameling is een set elementen in Adobe Experience Manager-middelen. Gebruik verzamelingen om elementen tussen gebruikers te delen. De set kan een statische verzameling of een dynamische verzameling zijn die is gebaseerd op zoekresultaten.

In tegenstelling tot mappen kan een verzameling elementen van verschillende locaties bevatten. U kunt verzamelingen delen met verschillende gebruikers waaraan verschillende niveaus van bevoegdheden zijn toegewezen, zoals weergeven, bewerken, enzovoort.

U kunt meerdere verzamelingen delen met een gebruiker. Elke verzameling bevat verwijzingen naar elementen. De referentiële integriteit van activa wordt gehandhaafd over inzamelingen.

De inzamelingen zijn van de volgende types, die op de manier worden gebaseerd zij activa sorteren:

* Een verzameling die een statische referentielijst met elementen, mappen en andere verzamelingen bevat.

* Een slimme verzameling die dynamisch elementen bevat op basis van zoekcriteria.

## Toegang tot de verzamelingsconsole {#navigating-the-collections-console}

Als u de **[!UICONTROL verzamelingen]** wilt openen, gaat u in de interface van Experience Manager naar **[!UICONTROL Middelen]** > **[!UICONTROL Verzamelingen]**.

## Een verzameling maken {#creating-a-collection}

U kunt een verzameling maken met [statische verwijzingen](#creating-a-collection-with-static-references) of op basis van een op [zoekcriteria gebaseerd filter](#creating-a-smart-collection). U kunt ook een verzameling maken van een lichtbak.

### Een verzameling met statische verwijzingen maken {#creating-a-collection-with-static-references}

U kunt een verzameling maken met statische verwijzingen, bijvoorbeeld een verzameling met verwijzingen naar elementen, mappen, verzamelingen, centrifuges en afbeeldingssets.

1. Navigeer naar de **[!UICONTROL Collections]** -console.
1. From the toolbar, click **[!UICONTROL Create]**.
1. Voer op de pagina **[!UICONTROL Verzameling]** maken een titel en een optionele beschrijving in voor de verzameling.
1. Voeg leden toe aan de verzameling en wijs de juiste machtigingen toe. Alternatively, select **[!UICONTROL Public Collection]** to allow all users to access the collection.

   >[!NOTE]
   >
   >Om de leden toe te laten om inzamelingen met andere gebruikers te delen, verstrek de `dam-users` groep lees toestemmingen bij de weg `home/users`. Geef gebruikers op de `/content/dam/collections` locatie toestemming om de verzamelingen in pop-uplijsten weer te geven. U kunt de gebruiker ook deel laten uitmaken van een `dam-users` groep.

1. (Optioneel) Voeg een miniatuurafbeelding toe voor de verzameling.
1. Klik op **[!UICONTROL Maken]** en klik vervolgens op **[!UICONTROL OK]** om het dialoogvenster te sluiten. Een verzameling met de opgegeven titel en eigenschappen wordt geopend in de console voor verzamelingen.

   >[!NOTE]
   >
   >Met de middelen van Experience Manager kunt u controletaken voor een verzameling maken die lijken op de manier waarop u overzichtstaken voor een map met middelen maakt.

   Navigeer naar de gebruikersinterface Elementen om elementen aan de verzameling toe te voegen. Zie Elementen [toevoegen aan een verzameling](#adding-assets-to-a-collection)voor meer informatie.

### Verzamelingen maken met dropzone {#create-collections-using-dropzone}

U kunt elementen van de interface Elementen naar een verzameling slepen. U kunt ook een kopie van een verzameling maken en de elementen daar slepen.

1. Selecteer in de gebruikersinterface Elementen de elementen die u aan een verzameling wilt toevoegen.
1. Sleep de elementen naar de zone **[!UICONTROL Drop in Collection]** . U kunt ook op het pictogram **[!UICONTROL Naar verzameling]** op de werkbalk klikken.

   ![drop_in_collection](assets/drop_in_collection.png)

1. Klik in de pagina **[!UICONTROL Toevoegen aan verzameling]** op het pictogram Verzameling **** maken op de werkbalk.

   If you want to add the assets to an existing collection, select it from the page, and click **[!UICONTROL Add]**. Standaard wordt de laatst bijgewerkte verzameling geselecteerd.

1. In the **[!UICONTROL Create New Collection]** dialog, specify a name for the collection. If you want the collection to be accessible to all users, select **[!UICONTROL Public Collection]**.
1. Klik op **[!UICONTROL Doorgaan]** om de verzameling te maken.

### Een slimme verzameling maken {#creating-a-smart-collection}

Een slimme verzameling gebruikt zoekcriteria om elementen dynamisch te vullen. U kunt een slimme verzameling alleen maken met behulp van bestanden en niet met behulp van mappen of bestanden en mappen.

Voer de volgende stappen uit om een slimme verzameling te maken:

1. Navigeer naar de gebruikersinterface Elementen en klik op Zoeken.

1. Typ het zoekwoord in het vak Zoeken en druk op `Enter`. Open het deelvenster Filters en pas een zoekfilter toe.

1. Selecteer **[!UICONTROL Bestanden]** in de lijst **[!UICONTROL Bestanden en mappen]**.

   ![files_option](assets/files_option.png)

1. Klik op Slimme verzameling **[!UICONTROL opslaan]**.

1. Geef een naam op voor de verzameling. Selecteer **[!UICONTROL Openbaar]** om de groep DAM-gebruikers met de Viewer-rol toe te voegen aan de slimme verzameling.

   ![save_collection](assets/save_collection.png)

   >[!NOTE]
   >
   >Als u **[!UICONTROL Openbaar]** selecteert, wordt de slimme inzameling beschikbaar aan iedereen met de eigenaarrol nadat u het creeert. Als u de optie **[!UICONTROL Openbaar]** uitschakelt, wordt de DAM-gebruikersgroep niet meer gekoppeld aan de slimme verzameling.

1. Click **[!UICONTROL Save]** to create the smart collection, and then close the message box to complete the process.

   The new smart collection is also added to the **[!UICONTROL Saved Searches]** list.

   ![collection_list](assets/collection_listing.png)

   Het label van de knop **[!UICONTROL Slimme selectie]** maken verandert in Slimme selectie **[!UICONTROL bewerken]**. To edit the settings of the smart collection, select **[!UICONTROL Files]** from the **[!UICONTROL Files &amp; Folders]** list. Klik vervolgens op de knop Slimme selectie **** bewerken.

   ![chlimage_1-7](assets/chlimage_1-112.png)

## Elementen toevoegen aan een verzameling {#adding-assets-to-a-collection}

U kunt elementen toevoegen aan een verzameling die een lijst met bestanden of mappen waarnaar wordt verwezen, bevat. Slimme verzamelingen gebruiken een zoekquery om elementen te vullen. Daarom zijn statische verwijzingen naar elementen en mappen niet op hen van toepassing.

1. Selecteer het element in de gebruikersinterface Elementen en klik op het pictogram **[!UICONTROL Naar verzameling]** op de werkbalk.

   ![chlimage_1-8](assets/chlimage_1-113.png)

   U kunt het element ook naar het gebied **[!UICONTROL Inzameling]** neerzetten op de interface slepen. Voeg de elementen toe wanneer het label van het gebied verandert in **[!UICONTROL Daling in Toevoegen]**.

1. Selecteer op de pagina **[!UICONTROL Toevoegen aan verzameling]** de verzameling waaraan u het element wilt toevoegen.

1. Klik op **[!UICONTROL Toevoegen]** en sluit het bevestigingsbericht. Het element wordt toegevoegd aan de collectie.

## Een slimme verzameling bewerken {#editing-a-smart-collection}

Slimme verzamelingen worden gemaakt door een zoekopdracht op te slaan, zodat u de inhoud kunt wijzigen door de zoekparameters van de [opgeslagen zoekopdracht](#saved-searches)te wijzigen.

1. Klik in de gebruikersinterface Middelen op het zoekpictogram op de werkbalk.

   ![chlimage_1-9](assets/chlimage_1-110.png)

1. Met de curseur in het vakje van het Onderzoek, duw op de sleutel van de Terugkeer.
1. Klik op het pictogram GlobalNav om het deelvenster Filters weer te geven.
1. From the **[!UICONTROL Saved Searches]** list, select the smart collection you want to modify. In het deelvenster Zoeken worden de filters weergegeven die zijn geconfigureerd voor de opgeslagen zoekopdracht.

   ![select_smart_collection](assets/select_smart_collection.png)

1. Selecteer **[!UICONTROL Bestanden]** in de lijst **[!UICONTROL Bestanden en mappen]**.
1. Wijzig desgewenst een of meer filters. Klik op Slimme verzameling **[!UICONTROL bewerken]**.

   U kunt ook de naam van de slimme verzameling bewerken.

   ![edit_smart_collectiondialog](assets/edit_smart_collectiondialog.png)

1. Click **[!UICONTROL Save]**. Het dialoogvenster Slimme verzameling **** bewerken wordt geopend.
1. Klik op **[!UICONTROL Overschrijven]** om de originele slimme verzameling te vervangen door de bewerkte verzameling. Of selecteer **[!UICONTROL Opslaan als]** om de bewerkte verzameling afzonderlijk op te slaan.
1. Klik in het bevestigingsvenster op **[!UICONTROL Opslaan]** om het proces te voltooien.

## Metagegevens van verzamelingen weergeven en bewerken {#viewing-and-editing-collection-metadata}

De meta-gegevens van de inzameling omvat gegevens over de inzameling, met inbegrip van om het even welke markeringen die worden toegevoegd.

1. Selecteer een verzameling in de console Verzamelingen en klik op het pictogram **[!UICONTROL Eigenschappen]** op de werkbalk.
1. In the **[!UICONTROL Collection Metadata]** page, view the collection metadata from the **[!UICONTROL Basic]** and **[!UICONTROL Advanced]** tabs.
1. Wijzig desgewenst de metagegevens en klik vervolgens op **[!UICONTROL Opslaan en sluiten]** op de werkbalk om de wijzigingen op te slaan.

## Metagegevens van meerdere verzamelingen bulksgewijs bewerken {#editing-collection-metadata-in-bulk}

U kunt de metagegevens van meerdere verzamelingen tegelijk bewerken. Deze functionaliteit helpt u snel gemeenschappelijke meta-gegevens in veelvoudige inzamelingen te herhalen.

1. Selecteer twee of meer verzamelingen waarvoor u metagegevens wilt bewerken in de console Verzamelingen.
1. Klik op het pictogram **[!UICONTROL Eigenschappen]** op de werkbalk.
1. Bewerk desgewenst de metagegevens op de pagina Metagegevens **** verzameling onder de tabbladen **[!UICONTROL Standaard]** en **[!UICONTROL Geavanceerd]** .
1. Als u de eigenschappen van metagegevens voor een specifieke verzameling wilt weergeven, schakelt u de overige verzamelingen in de lijst met verzamelingen uit. De gebieden van de meta-gegevensredacteur zijn bevolkt met de meta-gegevens voor de bepaalde inzameling.

   >[!NOTE]
   >
   >* Op de pagina met eigenschappen van verzamelingen kunt u verzamelingen verwijderen uit de lijst met verzamelingen door ze te deselecteren. Alle verzamelingen zijn standaard geselecteerd in de lijst met verzamelingen. De metagegevens voor verzamelingen die u verwijdert, worden niet bijgewerkt.
   >* Selecteer boven aan de lijst het selectievakje bij **[!UICONTROL Titel]** om te schakelen tussen het selecteren van de verzamelingen en het wissen van de lijst.


1. Klik op **[!UICONTROL Opslaan en sluiten]** op de werkbalk en sluit het bevestigingsvenster om het proces te voltooien.
1. To append the new metadata with the existing metadata, select **[!UICONTROL Append mode]**. Als u deze optie niet selecteert, worden de bestaande metadata in de velden vervangen door de nieuwe metadata. Klik op **[!UICONTROL Verzenden]**.

   >[!NOTE]
   >
   >De metagegevens die u voor de geselecteerde verzamelingen toevoegt, overschrijven de vorige metagegevens voor deze verzamelingen. Met de modus  Toevoegen kunt u nieuwe waarden toevoegen aan de bestaande metagegevens in de velden die meerdere waarden kunnen bevatten. Velden met één waarde worden altijd overschreven. Alle tags die u toevoegt in het veld [!UICONTROL Codes] , worden toegevoegd aan de bestaande lijst met tags in de metagegevens.

Gebruik de Schema-editor om de pagina [!UICONTROL Eigenschappen] van metagegevens aan te passen, inclusief eigenschappen van metagegevens toevoegen, wijzigen of verwijderen.

>[!TIP]
>
>De bulkbewerkingsmethode werkt voor elementen die beschikbaar zijn in een verzameling. Voor de elementen die beschikbaar zijn in verschillende mappen of die voldoen aan een algemeen criterium, is het mogelijk om de metagegevens na het zoeken [in grote](/help/assets/search-assets.md#metadataupdates)hoeveelheden bij te werken.

## Verzamelingen zoeken {#searching-collections}

U kunt inzamelingen van de console van Inzamelingen zoeken. Wanneer u met trefwoorden in het vak Zoeken zoekt, zoekt AEM-middelen naar verzamelingsnamen, metagegevens en de tags die aan de verzamelingen zijn toegevoegd.

Als u zoekt naar verzamelingen op het hoogste niveau, worden alleen afzonderlijke verzamelingen geretourneerd in zoekresultaten. Elementen of mappen in de verzamelingen zijn uitgesloten. In alle andere gevallen (bijvoorbeeld in een afzonderlijke verzameling of in een mappenhiërarchie) worden alle relevante elementen, mappen en verzamelingen geretourneerd.

## Zoeken in verzamelingen {#searching-within-collections}

Klik in de console Verzamelingen op een verzameling om deze te openen.

In een verzameling is het zoeken naar AEM-middelen beperkt tot elementen (en de bijbehorende tags en metagegevens) in de verzameling die u bekijkt. Wanneer u in een map zoekt, worden alle overeenkomende elementen en onderliggende mappen in de huidige map geretourneerd. Wanneer u in een verzameling zoekt, worden alleen overeenkomende elementen, mappen en andere verzamelingen geretourneerd die directe leden van de verzameling zijn.

## Verzamelingsinstellingen bewerken {#editing-collection-settings}

U kunt verzamelingsinstellingen bewerken, zoals titel en beschrijving, of leden toevoegen aan een verzameling.

1. Selecteer een verzameling en klik op het pictogram **[!UICONTROL Instellingen]** op de werkbalk. U kunt ook de snelle actie **[!UICONTROL Instellingen]** van de miniatuur van de verzameling gebruiken.
1. Modify the collection settings in the **[!UICONTROL Collection Settings]** page. For example, modify the collection title, descriptions, members, and permissions as discussed in [Adding Collections](#creating-a-collection).

1. Klik op **[!UICONTROL Opslaan]** om de wijzigingen op te slaan.

## Een verzameling verwijderen {#deleting-a-collection}

1. Selecteer een of meer verzamelingen in de console Verzamelingen en klik op het pictogram Verwijderen op de werkbalk.

   ![chlimage_1-11](assets/chlimage_1-177.png)

1. Klik in het dialoogvenster op **[!UICONTROL Verwijderen]** om de verwijderactie te bevestigen.

   >[!NOTE]
   >
   >U kunt slimme verzamelingen ook verwijderen door opgeslagen zoekopdrachten [te verwijderen](#saved-searches).

## Een verzameling downloaden {#downloading-a-collection}

Wanneer u een verzameling downloadt, wordt de volledige hiërarchie van elementen in de verzameling gedownload, inclusief mappen en onderliggende verzamelingen.

1. Selecteer een of meer verzamelingen die u wilt downloaden in de console Verzamelingen.
1. Klik op het downloadpictogram op de werkbalk.
1. Klik in het dialoogvenster **[!UICONTROL Downloaden]** op **[!UICONTROL Downloaden]**. Selecteer **[!UICONTROL Uitvoeringen]** als u de uitvoeringen van de elementen in de verzameling wilt downloaden. Selecteer de optie **[!UICONTROL E-mail]** om een e-mailbericht naar de eigenaar van de verzameling te verzenden.

   Wanneer u een verzameling selecteert die u wilt downloaden, wordt de volledige maphiërarchie onder de verzameling gedownload. Als u elke verzameling die u downloadt (inclusief elementen in onderliggende verzamelingen die onder de bovenliggende verzameling zijn genest), wilt opnemen in een afzonderlijke map, selecteert u **[!UICONTROL Een aparte map maken voor elk element]**.

## Geneste verzamelingen maken {#creating-nested-collections}

U kunt een verzameling toevoegen aan een andere verzameling en zo een geneste verzameling maken.

1. Selecteer in de verzamelingsconsole de gewenste verzameling of groep verzamelingen en klik op **[!UICONTROL Naar verzameling]** op de werkbalk.

1. Selecteer op de pagina **[!UICONTROL Toevoegen aan verzameling]** de verzameling waarin u de verzameling wilt toevoegen.

   >[!NOTE]
   >
   >De laatst bijgewerkte verzameling is standaard geselecteerd in de pagina **[!UICONTROL Toevoegen aan verzameling]** .

1. Click **[!UICONTROL Add]**. Een bericht bevestigt dat de inzameling aan de doelinzameling in de **[!UICONTROL Uitgezochte pagina van de Bestemming]** wordt toegevoegd. Sluit het bericht om het proces te voltooien.

>[!NOTE]
>
>Slimme verzamelingen kunnen niet worden genest. Met andere woorden, slimme verzamelingen kunnen geen andere verzameling bevatten.

## Opgeslagen zoekopdrachten {#saved-searches}

In de gebruikersinterface Assets kunt u op basis van bepaalde regels, zoekcriteria of aangepaste zoekfacetten zoeken of filteren. If you save these as **[!UICONTROL Saved Searches]**, you can access them later from the **[!UICONTROL Saved Searches]** list in the Filter panel. Als u een opgeslagen zoekopdracht maakt, wordt ook een slimme verzameling gemaakt.

![saved_search_list](assets/saved_searches_list.png)

Opgeslagen zoekopdrachten worden gemaakt wanneer u een slimme verzameling maakt. Smart collections are automatically added to the **[!UICONTROL Saved Searches]** list. De query voor opgeslagen zoekopdrachten voor de verzameling wordt opgeslagen in de eigenschap `dam:query` in CRXDE op de relatieve locatie `/content/dam/collections/`.

>[!NOTE]
>
>U kunt slimme verzamelingen op dezelfde manier delen als statische verzamelingen.

Opgeslagen zoekopdrachten bewerken is hetzelfde als slimme verzamelingen bewerken. Zie Een slimme verzameling [](#editing-a-smart-collection)bewerken voor meer informatie.

Voer de volgende stappen uit om opgeslagen zoekopdrachten te verwijderen:

1. Klik in de gebruikersinterface Middelen op het zoekpictogram op de werkbalk.

   ![chlimage_1-13](assets/chlimage_1-114.png)

1. Met de curseur op het gebied van Onderzoek, duw op de Enter sleutel.

1. Klik op het pictogram GlobalNav om het deelvenster Filters weer te geven.

1. From the **[!UICONTROL Saved Searches]** list, click **[!UICONTROL Delete]** next to the smart collection that you want to delete.

   ![select_smart_collection-1](assets/select_smart_collection-1.png)

1. Klik in het dialoogvenster op **[!UICONTROL Verwijderen]** om de opgeslagen zoekopdracht te verwijderen.

## Een workflow op een verzameling uitvoeren {#running-a-workflow-on-a-collection}

U kunt een workflow voor de elementen in een verzameling uitvoeren. Als de verzameling geneste verzamelingen bevat, wordt de workflow ook uitgevoerd op de elementen in de geneste verzamelingen. Als de verzameling en de geneste verzameling echter dubbele elementen bevatten, wordt de workflow slechts eenmaal uitgevoerd voor dergelijke elementen.

1. Selecteer in de console Verzamelingen een verzameling waarop u een workflow wilt uitvoeren.
1. Klik op het pictogram GlobalNav en kies **[!UICONTROL Tijdlijn]** in de lijst.
1. From the timeline, click the Caret icon at the bottom, and then click **[!UICONTROL Start Workflow]**.

   ![chlimage_1-14](assets/chlimage_1-137.png)

1. Selecteer in de sectie **[!UICONTROL Workflow starten]** een workflowmodel in de lijst. Selecteer bijvoorbeeld het model **[!UICONTROL Asset-updates van DAM]**.
1. Voer een titel in voor de workflow en klik op **[!UICONTROL Start]**.
1. In the dialog, click **[!UICONTROL Proceed]**. De workflow wordt uitgevoerd op alle elementen in de verzameling.

>[!MORELIKETHIS]
>
>* [E-mailmeldingen voor Experience Manager configureren](/help/sites-administering/notification.md#assetsconfig)
>* [Een revisietaak maken voor verzamelingen](bulk-approval.md)

