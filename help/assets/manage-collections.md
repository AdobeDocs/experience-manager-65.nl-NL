---
title: Verzamelingen digitale middelen beheren
description: Leer taken om verzamelingen met middelen te beheren, zoals verzamelingen maken, weergeven, verwijderen, bewerken en downloaden.
contentOwner: AG
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 0d5a48be283484005013ef3ed7ad015b43f6398b
workflow-type: tm+mt
source-wordcount: '2022'
ht-degree: 10%

---


# Verzamelingen beheren {#managing-collections}

Een verzameling is een set elementen binnen [!DNL Adobe Experience Manager Assets]. Gebruik verzamelingen om elementen tussen gebruikers te delen. De set kan een statische verzameling of een dynamische verzameling zijn die is gebaseerd op zoekresultaten.

In tegenstelling tot mappen kan een verzameling elementen van verschillende locaties bevatten. U kunt verzamelingen delen met verschillende gebruikers waaraan verschillende niveaus van bevoegdheden zijn toegewezen, zoals weergeven, bewerken, enzovoort.

U kunt meerdere verzamelingen delen met een gebruiker. Elke verzameling bevat verwijzingen naar elementen. De referentiële integriteit van activa wordt gehandhaafd over inzamelingen.

De inzamelingen zijn van de volgende types, die op de manier worden gebaseerd zij activa sorteren:

* Een verzameling die een statische referentielijst met elementen, mappen en andere verzamelingen bevat.

* Een slimme verzameling die dynamisch elementen bevat op basis van zoekcriteria.

## Toegang tot de verzamelingsconsole {#navigating-the-collections-console}

Als u **[!UICONTROL Collections]** wilt openen, gaat u in de [!DNL Experience Manager]-interface naar **[!UICONTROL Assets]** > **[!UICONTROL Collections]**.

## Een verzameling maken {#creating-a-collection}

U kunt een inzameling of met [statische verwijzingen](#creating-a-collection-with-static-references) of gebaseerd op een [onderzoek op criteria-gebaseerde filter](#creating-a-smart-collection) tot stand brengen. U kunt ook een verzameling maken van een lichtbak.

### Een verzameling maken met statische verwijzingen {#creating-a-collection-with-static-references}

U kunt een verzameling maken met statische verwijzingen, bijvoorbeeld een verzameling met verwijzingen naar elementen, mappen, verzamelingen, centrifuges en afbeeldingssets.

1. Navigeer naar de **[!UICONTROL Collections]** console.
1. Klik **[!UICONTROL Create]** op de werkbalk.
1. Voer op de pagina **[!UICONTROL Create Collection]** een titel en een optionele beschrijving in voor de verzameling.
1. Voeg leden toe aan de verzameling en wijs de juiste machtigingen toe. U kunt ook **[!UICONTROL Public Collection]** selecteren om alle gebruikers toegang te geven tot de verzameling.

   >[!NOTE]
   >
   >Om de leden toe te laten om inzamelingen met andere gebruikers te delen, verstrek `dam-users` groep lees toestemmingen bij de weg `home/users`. Geef gebruikers toestemming op `/content/dam/collections` locatie om de gebruikers toe te staan de verzamelingen in pop-uplijsten weer te geven. U kunt de gebruiker ook onderdeel maken van de groep `dam-users`.

1. (Optioneel) Voeg een miniatuurafbeelding toe voor de verzameling.
1. Klik **[!UICONTROL Create]**, en klik dan **[!UICONTROL OK]** om de dialoog te sluiten. Een verzameling met de opgegeven titel en eigenschappen wordt geopend in de console voor verzamelingen.

   >[!NOTE]
   >
   >[!DNL Experience Manager Assets] Hiermee kunt u controletaken voor een verzameling maken, vergelijkbaar met de manier waarop u overzichtstaken voor een map met elementen maakt.

   Als u elementen aan de verzameling wilt toevoegen, navigeert u naar de [!DNL Assets]-gebruikersinterface. Zie [Elementen toevoegen aan een verzameling](#adding-assets-to-a-collection) voor meer informatie.

### Verzamelingen maken met dropzone {#create-collections-using-dropzone}

U kunt elementen vanuit de gebruikersinterface [!DNL Assets] naar een verzameling slepen. U kunt ook een kopie van een verzameling maken en de elementen daar slepen.

1. Selecteer in de gebruikersinterface [!DNL Assets] de elementen die u aan een verzameling wilt toevoegen.
1. Sleep de elementen naar de zone **[!UICONTROL Drop in Collection]**. U kunt ook op **[!UICONTROL To Collection]** op de werkbalk klikken.

   ![drop_in_collection](assets/drop_in_collection.png)

1. Klik op **[!UICONTROL Add To Collection]** op de werkbalk op **[!UICONTROL Create Collection]**.

   Als u de elementen aan een bestaande verzameling wilt toevoegen, selecteert u deze op de pagina en klikt u op **[!UICONTROL Add]**. Standaard wordt de laatst bijgewerkte verzameling geselecteerd.

1. Geef in het dialoogvenster **[!UICONTROL Create New Collection]** een naam op voor de verzameling. Selecteer **[!UICONTROL Public Collection]** als u de verzameling toegankelijk wilt maken voor alle gebruikers.
1. Klik **[!UICONTROL Continue]** om de verzameling te maken.

### Een slimme verzameling maken {#creating-a-smart-collection}

Een slimme verzameling gebruikt zoekcriteria om elementen dynamisch te vullen. U kunt een slimme verzameling alleen maken met behulp van bestanden en niet met behulp van mappen of bestanden en mappen.

Voer de volgende stappen uit om een slimme verzameling te maken:

1. Navigeer naar de [!DNL Assets] gebruikersinterface en klik op Zoeken.

1. Typ het zoekwoord in het vak Zoeken en druk op `Enter`. Open het deelvenster Filters en pas een zoekfilter toe.

1. Selecteer **[!UICONTROL Files]** in de lijst **[!UICONTROL Files & Folders]**.

   ![files_option](assets/files_option.png)

1. Klik op **[!UICONTROL Save Smart Collection]**.

1. Geef een naam op voor de verzameling. Selecteer **[!UICONTROL Public]** om de groep van Gebruikers DAM met de rol van de Kijker aan de slimme inzameling toe te voegen.

   ![save_collection](assets/save_collection.png)

   >[!NOTE]
   >
   >Als u **[!UICONTROL Public]** selecteert, wordt de slimme inzameling beschikbaar aan iedereen met de eigenaarrol nadat u het creeert. Als u de optie **[!UICONTROL Public]** uitschakelt, wordt de DAM-gebruikersgroep niet meer gekoppeld aan de slimme verzameling.

1. Klik **[!UICONTROL Save]** om de slimme inzameling tot stand te brengen, en dan het berichtvakje te sluiten om het proces te voltooien.

   De nieuwe slimme verzameling wordt ook toegevoegd aan de lijst **[!UICONTROL Saved Searches]**.

   ![collection_list](assets/collection_listing.png)

   Het label van de optie **[!UICONTROL Create Smart Selection]** verandert in **[!UICONTROL Edit Smart Selection]**. Als u de instellingen van de slimme verzameling wilt bewerken, selecteert u **[!UICONTROL Files]** in de lijst **[!UICONTROL Files & Folders]**. Klik **[!UICONTROL Edit Smart Selection]** ![geef slimme inzameling](assets/do-not-localize/edit-smart-collection.png) optie uit.

## Elementen toevoegen aan een verzameling {#adding-assets-to-a-collection}

U kunt elementen toevoegen aan een verzameling die een lijst met bestanden of mappen waarnaar wordt verwezen, bevat. Slimme verzamelingen gebruiken een zoekquery om elementen te vullen. Daarom zijn statische verwijzingen naar elementen en mappen niet op hen van toepassing.

1. Selecteer het element in de [!DNL A]gebruikersinterface voor sets en klik op **[!UICONTROL To Collection]** ![Toevoegen aan verzameling](assets/do-not-localize/add-to-collection.png) op de werkbalk.
U kunt het element ook naar het **[!UICONTROL Drop in Collection]**-gebied op de interface slepen. Voeg de elementen toe wanneer het label van het gebied verandert in **[!UICONTROL Drop to Add]**.

1. Selecteer op de pagina **[!UICONTROL Add To Collection]** de verzameling waaraan u het element wilt toevoegen.

1. Klik **[!UICONTROL Add]**, en sluit dan het bevestigingsbericht. Het element wordt toegevoegd aan de collectie.

## Een slimme verzameling bewerken {#editing-a-smart-collection}

Slimme verzamelingen worden gemaakt door een zoekopdracht op te slaan, zodat u de inhoud kunt wijzigen door de zoekparameters van de [opgeslagen zoekopdracht](#saved-searches) te wijzigen.

1. Klik in de gebruikersinterface [!DNL Assets] op de zoekoptie ![zoekoptie](assets/do-not-localize/search_icon.png) op de werkbalk.
1. Met de curseur in het vakje van het Onderzoek, duw op de sleutel van de Terugkeer.
1. Open in de interface [!DNL Experience Manager] het deelvenster Filters.
1. Selecteer in de lijst met **[!UICONTROL Saved Searches]** de slimme verzameling die u wilt wijzigen. In het deelvenster Zoeken worden de filters weergegeven die zijn geconfigureerd voor de opgeslagen zoekopdracht.

   ![select_smart_collection](assets/select_smart_collection.png)

1. Selecteer **[!UICONTROL Files]** in de lijst **[!UICONTROL Files & Folders]**.
1. Wijzig desgewenst een of meer filters. Klik op **[!UICONTROL Edit Smart Collection]**.

   U kunt ook de naam van de slimme verzameling bewerken.

   ![edit_smart_collectiondialog](assets/edit_smart_collectiondialog.png)

1. Klik op **[!UICONTROL Save]**. Het dialoogvenster **[!UICONTROL Edit Smart Collection]** wordt weergegeven.
1. Klik **[!UICONTROL Overwrite]** om de originele slimme inzameling met de uitgegeven inzameling te vervangen. U kunt ook **[!UICONTROL Save As]** selecteren om de bewerkte verzameling afzonderlijk op te slaan.
1. Klik in het bevestigingsdialoogvenster op **[!UICONTROL Save]** om het proces te voltooien.

## Metagegevens van verzamelingen weergeven en bewerken {#view-edit-collection-metadata}

De meta-gegevens van de inzameling omvat gegevens over de inzameling, met inbegrip van om het even welke markeringen die worden toegevoegd.

1. Selecteer in de [!UICONTROL Collections]-console een verzameling en klik op **[!UICONTROL Properties]** op de werkbalk.
1. Op de **[!UICONTROL Collection Metadata]** pagina, bekijk de inzamelingsmeta-gegevens van **[!UICONTROL Basic]** en **[!UICONTROL Advanced]** lusjes.
1. Wijzig desgewenst de metagegevens. Als u de wijzigingen wilt opslaan, klikt u op **[!UICONTROL Save & Close]** op de werkbalk.

## Metagegevens van meerdere verzamelingen bulksgewijs {#editing-collection-metadata-in-bulk} bewerken

U kunt de metagegevens van meerdere verzamelingen tegelijk bewerken. Deze functionaliteit helpt u snel gemeenschappelijke meta-gegevens in veelvoudige inzamelingen te herhalen.

1. Selecteer twee of meer verzamelingen in de verzamelingsconsole.
1. Klik **[!UICONTROL Properties]** op de werkbalk.
1. Bewerk desgewenst de metadata op de pagina **[!UICONTROL Collection Metadata]** onder de tabbladen **[!UICONTROL Basic]** en **[!UICONTROL Advanced]**.
1. Als u de eigenschappen van metagegevens voor een specifieke verzameling wilt weergeven, schakelt u de overige verzamelingen in de lijst met verzamelingen uit. De gebieden van de meta-gegevensredacteur zijn bevolkt met de meta-gegevens voor de bepaalde inzameling.

   >[!NOTE]
   >
   >* Op de pagina [!UICONTROL Properties] kunt u verzamelingen uit de lijst met verzamelingen verwijderen door ze te deselecteren. Alle verzamelingen zijn standaard geselecteerd in de lijst met verzamelingen. [!DNL Experience Manager] werkt de metagegevens van de verzamelingen die u verwijdert niet bij.
   >* Selecteer boven aan de lijst het selectievakje bij **[!UICONTROL Title]** om te schakelen tussen het selecteren van de verzamelingen en het wissen van de lijst.


1. Klik op **[!UICONTROL Save & Close]** op de werkbalk en sluit het bevestigingsvenster.
1. Selecteer **[!UICONTROL Append mode]** om de nieuwe metadata toe te voegen aan de bestaande metadata. Als u deze optie niet selecteert, worden de bestaande metadata in de velden vervangen door de nieuwe metadata. Klik op **[!UICONTROL Submit]**.

   >[!NOTE]
   >
   >De metagegevens die u voor de geselecteerde verzamelingen toevoegt, overschrijven de vorige metagegevens voor deze verzamelingen. Gebruik [!UICONTROL Append mode] om nieuwe waarden aan de bestaande meta-gegevens op de gebieden toe te voegen die veelvoudige waarden kunnen bevatten. Velden met één waarde worden altijd overschreven. Alle tags die u in het veld [!UICONTROL Tags] toevoegt, worden toegevoegd aan de bestaande lijst met tags in de metagegevens.

Als u de pagina met metagegevens [!UICONTROL Properties] wilt aanpassen, inclusief het toevoegen, wijzigen of verwijderen van eigenschappen van metagegevens, gebruikt u de Schema-editor.

>[!TIP]
>
>De bulkbewerkingsmethode werkt voor elementen die beschikbaar zijn in een verzameling. Voor de activa die over omslagen beschikbaar zijn of een gemeenschappelijke criteria aanpassen, is het mogelijk om [bulkupdate de meta-gegevens na het zoeken](/help/assets/search-assets.md#metadataupdates).

## Verzamelingen zoeken {#searching-collections}

U kunt inzamelingen van de console van Inzamelingen zoeken. Wanneer u met sleutelwoorden in het vakje van het Onderzoek zoekt, [!DNL Assets] zoekt naar inzamelingsnamen, meta-gegevens, en de markeringen die aan de inzamelingen worden toegevoegd.

Als u zoekt naar verzamelingen op het hoogste niveau, worden alleen afzonderlijke verzamelingen geretourneerd in zoekresultaten. [!DNL Assets] of mappen in de verzamelingen worden uitgesloten. In alle andere gevallen (bijvoorbeeld in een afzonderlijke verzameling of in een mappenhiërarchie) worden alle relevante elementen, mappen en verzamelingen geretourneerd.

## Zoeken in verzamelingen {#searching-within-collections}

Klik in de console Verzamelingen op een verzameling om deze te openen.

Binnen een verzameling is de [!DNL Experience Manager]-zoekopdracht beperkt tot elementen (en de bijbehorende tags en metagegevens) in de verzameling die u bekijkt. Wanneer u in een map zoekt, worden alle overeenkomende elementen en onderliggende mappen in de huidige map geretourneerd. Wanneer u in een verzameling zoekt, worden alleen overeenkomende elementen, mappen en andere verzamelingen geretourneerd die directe leden van de verzameling zijn.

## Verzamelingsinstellingen bewerken {#editing-collection-settings}

U kunt verzamelingsinstellingen bewerken, zoals titel en beschrijving, of leden toevoegen aan een verzameling.

1. Selecteer een verzameling en klik op **[!UICONTROL Settings]** op de werkbalk. U kunt ook de snelle actie **[!UICONTROL Settings]** van de verzamelingsminiatuur gebruiken.
1. Wijzig de verzamelingsinstellingen op de pagina **[!UICONTROL Collection Settings]**. Wijzig bijvoorbeeld de titel van de verzameling, beschrijvingen, leden en machtigingen zoals beschreven in [Verzamelingen toevoegen](#creating-a-collection).

1. Klik op **[!UICONTROL Save]** om de wijzigingen op te slaan.

## Een verzameling {#deleting-a-collection} verwijderen

1. Selecteer een of meer verzamelingen in de console Verzamelingen en klik op Verwijderen op de werkbalk.

1. Klik in het dialoogvenster op **[!UICONTROL Delete]** om de verwijderactie te bevestigen.

   >[!NOTE]
   >
   >U kunt slimme verzamelingen ook verwijderen door opgeslagen zoekopdrachten [ te verwijderen.](#saved-searches)

## Een verzameling {#downloading-a-collection} downloaden

Wanneer u een verzameling downloadt, wordt de volledige hiërarchie van elementen in de verzameling gedownload, inclusief mappen en onderliggende verzamelingen.

1. Selecteer een of meer verzamelingen die u wilt downloaden in de console Verzamelingen.
1. Klik **[!UICONTROL Download]** op de werkbalk.
1. Klik in het dialoogvenster **[!UICONTROL Download]** op **[!UICONTROL Download]**. Selecteer **[!UICONTROL Renditions]** als u de uitvoeringen van de elementen in de verzameling wilt downloaden. Selecteer de optie **[!UICONTROL Email]** om een e-mailbericht naar de eigenaar van de verzameling te verzenden.

   Wanneer u een verzameling selecteert die u wilt downloaden, wordt de volledige maphiërarchie onder de verzameling gedownload. Selecteer **[!UICONTROL Create separate folder for each asset]** als u elke verzameling die u downloadt, wilt opnemen (inclusief elementen in onderliggende verzamelingen die onder de bovenliggende verzameling zijn genest) in een afzonderlijke map.

## Geneste verzamelingen maken {#creating-nested-collections}

U kunt een verzameling toevoegen aan een andere verzameling en zo een geneste verzameling maken.

1. Selecteer in de verzamelingsconsole de gewenste verzameling of groep verzamelingen en klik op **[!UICONTROL To Collection]** op de werkbalk.

1. Selecteer op de pagina **[!UICONTROL Add To Collection]** de verzameling waarin u de verzameling wilt toevoegen.

   >[!NOTE]
   >
   >De laatst bijgewerkte verzameling wordt standaard geselecteerd op de pagina **[!UICONTROL Add To Collection]**.

1. Klik op **[!UICONTROL Add]**. Een bericht bevestigt dat de inzameling aan de doelinzameling in **[!UICONTROL Select Destination]** pagina wordt toegevoegd. Sluit het bericht om het proces te voltooien.

>[!NOTE]
>
>Slimme verzamelingen kunnen niet worden genest. Met andere woorden, slimme verzamelingen kunnen geen andere verzameling bevatten.

## Opgeslagen zoekopdrachten {#saved-searches}

In de [!DNL Assets] gebruikersinterface, kunt u activa zoeken of filtreren die op bepaalde regels, onderzoekscriteria, of de facetten van het douaneonderzoek worden gebaseerd. Als u deze opslaat als **[!UICONTROL Saved Searches]**, kunt u ze later openen vanuit de lijst **[!UICONTROL Saved Searches]** in het deelvenster Filteren. Als u een opgeslagen zoekopdracht maakt, wordt ook een slimme verzameling gemaakt.

![saved_search_list](assets/saved_searches_list.png)

Opgeslagen zoekopdrachten worden gemaakt wanneer u een slimme verzameling maakt. Slimme verzamelingen worden automatisch toegevoegd aan de lijst met **[!UICONTROL Saved Searches]**. De [!UICONTROL Saved Searches] vraag voor de inzameling wordt bewaard in `dam:query` bezit in CRXDE bij de relatieve plaats `/content/dam/collections/`. Er gelden geen limieten voor de zoekopdrachten die u kunt opslaan en voor de opgeslagen zoekopdrachten die in de lijst worden weergegeven.

>[!NOTE]
>
>U kunt slimme verzamelingen op dezelfde manier delen als statische verzamelingen.

Opgeslagen zoekopdrachten bewerken is hetzelfde als slimme verzamelingen bewerken. Zie [Een slimme verzameling bewerken](#editing-a-smart-collection) voor meer informatie.

Voer de volgende stappen uit om opgeslagen zoekopdrachten te verwijderen:

1. Klik in de gebruikersinterface [!DNL Assets] op Zoeken ![zoekoptie](assets/do-not-localize/search_icon.png).
1. Met de curseur op het gebied van Onderzoek, druk de sleutel van de Terugkeer.
1. Open in de interface [!DNL Experience Manager] het deelvenster Filters.
1. Klik in de lijst **[!UICONTROL Saved Searches]** op **[!UICONTROL Delete]** naast de slimme verzameling die u wilt verwijderen.

   ![select_smart_collection](assets/select_smart_collection.png)

1. Klik in het dialoogvenster op **[!UICONTROL Delete]** om de opgeslagen zoekopdracht te verwijderen.

## Een workflow uitvoeren op een verzameling {#running-a-workflow-on-a-collection}

U kunt een workflow voor de elementen in een verzameling uitvoeren. Als de verzameling geneste verzamelingen bevat, wordt de workflow ook uitgevoerd op de elementen in de geneste verzamelingen. Als de verzameling en de geneste verzameling echter dubbele elementen bevatten, wordt de workflow slechts eenmaal uitgevoerd voor dergelijke elementen.

1. Open **[!UICONTROL Assets]** > **[!UICONTROL Collections]**. Selecteer een specifieke verzameling als u een workflow op die verzameling wilt uitvoeren.
1. Open **[!UICONTROL Timeline]** rail. Klik ![chevron omhoog](assets/do-not-localize/chevron-up-icon.png) en klik **[!UICONTROL Start Workflow]**.
1. Selecteer in de sectie **[!UICONTROL Start Workflow]** een workflowmodel in de lijst. Selecteer bijvoorbeeld het model **[!UICONTROL DAM Update Asset]**.
1. Voer een titel in voor de workflow en klik op **[!UICONTROL Start]**.
1. Klik in het dialoogvenster op **[!UICONTROL Proceed]**. De workflow verwerkt alle elementen in de geselecteerde verzameling.

>[!MORELIKETHIS]
>
>* [E-mailberichten voor Experience Manager Assets configureren](/help/sites-administering/notification.md#assetsconfig)
>* [Een revisietaak maken voor verzamelingen](bulk-approval.md)

