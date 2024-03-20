---
title: Verzamelingen digitale middelen beheren
description: Leer taken om verzamelingen met middelen te beheren, zoals verzamelingen maken, weergeven, verwijderen, bewerken en downloaden.
contentOwner: AG
mini-toc-levels: 1
role: User
feature: Collections,Asset Management
exl-id: 2117b2de-8024-4aa8-9ce0-68a156928356
hide: true
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '2027'
ht-degree: 10%

---

# Verzamelingen beheren {#managing-collections}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/manage-collections.html?lang=en) |
| AEM 6,5 | Dit artikel |

Een verzameling is een set elementen binnen [!DNL Adobe Experience Manager Assets]. Gebruik verzamelingen om elementen tussen gebruikers te delen. De set kan een statische verzameling of een dynamische verzameling zijn die is gebaseerd op zoekresultaten.

In tegenstelling tot mappen kan een verzameling elementen van verschillende locaties bevatten. U kunt verzamelingen delen met verschillende gebruikers waaraan verschillende niveaus van bevoegdheden zijn toegewezen, zoals weergeven, bewerken, enzovoort.

U kunt meerdere verzamelingen delen met een gebruiker. Elke verzameling bevat verwijzingen naar elementen. De referentiële integriteit van activa wordt gehandhaafd over inzamelingen.

De inzamelingen zijn van de volgende types, die op de manier worden gebaseerd zij activa sorteren:

* Een verzameling die een statische referentielijst met elementen, mappen en andere verzamelingen bevat.

* Een slimme verzameling die dynamisch elementen bevat op basis van zoekcriteria.

## Toegang tot de verzamelingsconsole {#navigating-the-collections-console}

Als u het dialoogvenster **[!UICONTROL Collections]** in de [!DNL Experience Manager] interface, ga naar **[!UICONTROL Assets]** > **[!UICONTROL Collections]**.

## Een verzameling maken {#creating-a-collection}

U kunt een verzameling maken met [statische verwijzingen](#creating-a-collection-with-static-references) of op basis van een [op zoekcriteria gebaseerd filter](#creating-a-smart-collection). U kunt ook een verzameling maken van een lichtbak.

### Een verzameling met statische verwijzingen maken {#creating-a-collection-with-static-references}

U kunt een verzameling maken met statische verwijzingen, bijvoorbeeld een verzameling met verwijzingen naar elementen, mappen, verzamelingen, centrifuges en afbeeldingssets.

1. Ga naar de **[!UICONTROL Collections]** console.
1. Klik **[!UICONTROL Create]** op de werkbalk.
1. In de **[!UICONTROL Create Collection]** Voer een titel en een optionele beschrijving in voor de verzameling.
1. Voeg leden toe aan de verzameling en wijs de juiste machtigingen toe. U kunt ook **[!UICONTROL Public Collection]** selecteren om alle gebruikers toegang te geven tot de verzameling.

   >[!NOTE]
   >
   >Om de leden toe te laten om inzamelingen met andere gebruikers te delen, verstrek `dam-users` groep lees toestemmingen bij de weg `home/users`. Toestemming geven aan de gebruikers op `/content/dam/collections` de locatie waar gebruikers de verzamelingen in pop-uplijsten kunnen weergeven. U kunt de gebruiker ook een onderdeel maken van `dam-users` groep.

1. (Optioneel) Voeg een miniatuurafbeelding toe voor de verzameling.
1. Klikken **[!UICONTROL Create]** en klik vervolgens op **[!UICONTROL OK]** het dialoogvenster sluiten. Een verzameling met de opgegeven titel en eigenschappen wordt geopend in de console voor verzamelingen.

   >[!NOTE]
   >
   >[!DNL Experience Manager Assets] Hiermee kunt u controletaken voor een verzameling maken, vergelijkbaar met de manier waarop u overzichtstaken voor een map met elementen maakt.

   Als u elementen aan de verzameling wilt toevoegen, navigeert u naar de [!DNL Assets] gebruikersinterface. Zie voor meer informatie [Elementen toevoegen aan een verzameling](#adding-assets-to-a-collection).

### Verzamelingen maken met dropzone {#create-collections-using-dropzone}

U kunt elementen slepen vanuit de [!DNL Assets] gebruikersinterface aan een inzameling. U kunt ook een kopie van een verzameling maken en de elementen daar slepen.

1. Van de [!DNL Assets] gebruikersinterface, selecteert u de elementen die u aan een verzameling wilt toevoegen.
1. Sleep de elementen naar de **[!UICONTROL Drop in Collection]** zone. U kunt ook op **[!UICONTROL To Collection]** op de werkbalk.

   ![drop_in_collection](assets/drop_in_collection.png)

1. In de **[!UICONTROL Add To Collection]** pagina, klikt u **[!UICONTROL Create Collection]** op de werkbalk.

   Als u de elementen aan een bestaande verzameling wilt toevoegen, selecteert u deze op de pagina en klikt u op **[!UICONTROL Add]**. Standaard wordt de laatst bijgewerkte verzameling geselecteerd.

1. Geef in het dialoogvenster **[!UICONTROL Create New Collection]** een naam op voor de verzameling. Selecteer **[!UICONTROL Public Collection]** als u de verzameling toegankelijk wilt maken voor alle gebruikers.
1. Klikken **[!UICONTROL Continue]** om de verzameling te maken.

### Een slimme verzameling maken {#creating-a-smart-collection}

Een slimme verzameling gebruikt zoekcriteria om elementen dynamisch te vullen. U kunt een slimme verzameling alleen maken met behulp van bestanden, niet met mappen of bestanden en mappen.

Voer de volgende stappen uit om een slimme verzameling te maken:

1. Ga naar de [!DNL Assets] en klik op Zoeken.

1. Typ het trefwoord in het vak Zoeken en selecteer `Enter`. Open het deelvenster Filters en pas een zoekfilter toe.

1. Van de **[!UICONTROL Files & Folders]** list, selecteer **[!UICONTROL Files]**.

   ![files_option](assets/files_option.png)

1. Klik op **[!UICONTROL Save Smart Collection]**.

1. Geef een naam op voor de verzameling. Selecteren **[!UICONTROL Public]** om de groep van Gebruikers DAM met de rol van de Kijker aan de slimme inzameling toe te voegen.

   ![save_collection](assets/save_collection.png)

   >[!NOTE]
   >
   >Als u **[!UICONTROL Public]**, wordt de slimme verzameling beschikbaar voor iedereen met de eigenaarrol nadat u deze hebt gemaakt. Als u het dialoogvenster **[!UICONTROL Public]** de DAM-gebruikersgroep niet meer aan de slimme verzameling is gekoppeld.

1. Klikken **[!UICONTROL Save]** om de slimme inzameling tot stand te brengen, en dan het berichtvakje te sluiten om het proces te voltooien.

   De nieuwe slimme verzameling wordt ook toegevoegd aan de **[!UICONTROL Saved Searches]** lijst.

   ![collection_list](assets/collection_listing.png)

   Het etiket van de **[!UICONTROL Create Smart Selection]** wijzigt u in **[!UICONTROL Edit Smart Selection]**. Als u de instellingen van de slimme verzameling wilt bewerken, selecteert u **[!UICONTROL Files]** in de lijst **[!UICONTROL Files & Folders]**. Klik op de knop **[!UICONTROL Edit Smart Selection]** ![slimme verzameling bewerken](assets/do-not-localize/edit-smart-collection.png) -optie.

## Elementen toevoegen aan een verzameling {#adding-assets-to-a-collection}

U kunt elementen toevoegen aan een verzameling die een lijst met bestanden of mappen waarnaar wordt verwezen, bevat. Slimme verzamelingen gebruiken een zoekquery om elementen te vullen. Daarom zijn statische verwijzingen naar elementen en mappen niet op hen van toepassing.

1. In de [!DNL A]stelt gebruikersinterface, selecteert de activa en klikt **[!UICONTROL To Collection]** ![toevoegen aan verzameling](assets/do-not-localize/add-to-collection.png) op de werkbalk.
U kunt het element ook naar de **[!UICONTROL Drop in Collection]** gebied op de interface. Voeg de elementen toe wanneer het label van het gebied verandert in **[!UICONTROL Drop to Add]**.

1. In de **[!UICONTROL Add To Collection]** selecteert u de verzameling waaraan u het element wilt toevoegen.

1. Klikken **[!UICONTROL Add]** en sluit vervolgens het bevestigingsbericht. Het element wordt toegevoegd aan de collectie.

## Een slimme verzameling bewerken {#editing-a-smart-collection}

Slimme verzamelingen worden gemaakt door een zoekopdracht op te slaan, zodat u de inhoud kunt wijzigen door de zoekparameters van de [opgeslagen zoekopdracht](#saved-searches).

1. In de [!DNL Assets] gebruikersinterface, klik de onderzoeksoptie ![zoekoptie](assets/do-not-localize/search_icon.png) op de werkbalk.
1. Selecteer met de cursor in het vak Onderzoek de optie `Return` toets.
1. In de [!DNL Experience Manager] , opent u het deelvenster Filters.
1. Selecteer in de lijst met **[!UICONTROL Saved Searches]** de slimme verzameling die u wilt wijzigen. In het deelvenster Zoeken worden de filters weergegeven die zijn geconfigureerd voor de opgeslagen zoekopdracht.

   ![select_smart_collection](assets/select_smart_collection.png)

1. Van de **[!UICONTROL Files & Folders]** list, selecteer **[!UICONTROL Files]**.
1. Wijzig desgewenst een of meer filters. Klik op **[!UICONTROL Edit Smart Collection]**.

   U kunt ook de naam van de slimme verzameling bewerken.

   ![edit_smart_collectiondialog](assets/edit_smart_collectiondialog.png)

1. Klik op **[!UICONTROL Save]**. De **[!UICONTROL Edit Smart Collection]** wordt weergegeven.
1. Klikken **[!UICONTROL Overwrite]** om de originele slimme verzameling te vervangen door de bewerkte verzameling. U kunt ook **[!UICONTROL Save As]** om de bewerkte verzameling afzonderlijk op te slaan.
1. Klik in het bevestigingsdialoogvenster op **[!UICONTROL Save]** om het proces te voltooien.

## Metagegevens van verzamelingen weergeven en bewerken {#view-edit-collection-metadata}

De meta-gegevens van de inzameling omvat gegevens over de inzameling, met inbegrip van om het even welke markeringen die worden toegevoegd.

1. Van de [!UICONTROL Collections] console, selecteer een inzameling en klik **[!UICONTROL Properties]** op de werkbalk.
1. In de **[!UICONTROL Collection Metadata]** pagina, bekijk de inzamelingsmeta-gegevens van **[!UICONTROL Basic]** en **[!UICONTROL Advanced]** tabs.
1. Wijzig desgewenst de metagegevens. Klik op **[!UICONTROL Save & Close]** op de werkbalk.

## Metagegevens van meerdere verzamelingen bulksgewijs bewerken {#editing-collection-metadata-in-bulk}

U kunt de metagegevens van meerdere verzamelingen tegelijk bewerken. Deze functionaliteit helpt u snel gemeenschappelijke meta-gegevens in veelvoudige inzamelingen te herhalen.

1. Selecteer twee of meer verzamelingen in de verzamelingsconsole.
1. Klik **[!UICONTROL Properties]** op de werkbalk.
1. Bewerk desgewenst de metadata op de pagina **[!UICONTROL Collection Metadata]** onder de tabbladen **[!UICONTROL Basic]** en **[!UICONTROL Advanced]**.
1. Als u de eigenschappen van metagegevens voor een specifieke verzameling wilt weergeven, annuleert u de selectie van de resterende verzamelingen in de lijst met verzamelingen. De gebieden van de meta-gegevensredacteur zijn bevolkt met de meta-gegevens voor de bepaalde inzameling.

   >[!NOTE]
   >
   >* In de [!UICONTROL Properties] pagina, kunt u verzamelingen verwijderen uit de lijst met verzamelingen door de selectie te annuleren. Alle verzamelingen zijn standaard geselecteerd in de lijst met verzamelingen. [!DNL Experience Manager] werkt de metagegevens van de verzamelingen die u verwijdert niet bij.
   >* Selecteer boven aan de lijst het selectievakje bij **[!UICONTROL Title]** om te schakelen tussen het selecteren van de verzamelingen en het wissen van de lijst.

1. Klikken **[!UICONTROL Save & Close]** op de werkbalk en sluit vervolgens het bevestigingsvenster.
1. Selecteer **[!UICONTROL Append mode]** om de nieuwe metadata toe te voegen aan de bestaande metadata. Als u deze optie niet selecteert, worden de bestaande metadata in de velden vervangen door de nieuwe metadata. Klik op **[!UICONTROL Submit]**.

   >[!NOTE]
   >
   >De metagegevens die u voor de geselecteerde verzamelingen toevoegt, overschrijven de vorige metagegevens voor deze verzamelingen. Gebruik de [!UICONTROL Append mode] om nieuwe waarden toe te voegen aan de bestaande metagegevens in de velden die meerdere waarden kunnen bevatten. Velden met één waarde worden altijd overschreven. Alle tags die u in het dialoogvenster [!UICONTROL Tags] worden toegevoegd aan de bestaande lijst met tags in de metagegevens.

De metagegevens aanpassen [!UICONTROL Properties] de pagina, met inbegrip van het toevoegen van, het wijzigen van, het schrappen van meta-gegevenseigenschappen, de redacteur van het Schema.

>[!TIP]
>
>De bulkbewerkingsmethode werkt voor elementen die beschikbaar zijn in een verzameling. Voor de elementen die beschikbaar zijn in verschillende mappen of die overeenkomen met een algemeen criterium, is het mogelijk om [bulkupdate van metagegevens na het zoeken](/help/assets/search-assets.md#metadataupdates).

## Verzamelingen zoeken {#searching-collections}

U kunt inzamelingen van de console van Inzamelingen zoeken. Wanneer u met trefwoorden zoekt in het vak Zoeken, [!DNL Assets] zoekt naar verzamelingsnamen, metagegevens en de tags die aan de verzamelingen zijn toegevoegd.

Als u naar inzamelingen van top-level zoekt, slechts zijn de individuele inzamelingen teruggekeerd in onderzoeksresultaten. [!DNL Assets] of mappen in de verzamelingen worden uitgesloten. In alle andere gevallen (bijvoorbeeld in een afzonderlijke verzameling of in een mappenhiërarchie) worden alle relevante elementen, mappen en verzamelingen geretourneerd.

## Zoeken in verzamelingen {#searching-within-collections}

Klik in de console Verzamelingen op een verzameling om deze te openen.

Binnen een collectie [!DNL Experience Manager] de zoekopdracht is beperkt tot elementen (en de bijbehorende tags en metagegevens) in de verzameling die u bekijkt. Wanneer u in een map zoekt, worden alle overeenkomende elementen en onderliggende mappen in de huidige map geretourneerd. Wanneer u in een verzameling zoekt, worden alleen overeenkomende elementen, mappen en andere verzamelingen geretourneerd die directe leden van de verzameling zijn.

## Verzamelingsinstellingen bewerken {#editing-collection-settings}

U kunt verzamelingsinstellingen bewerken, zoals titel en beschrijving, of leden toevoegen aan een verzameling.

1. Selecteer een verzameling en klik op **[!UICONTROL Settings]** in de werkbalk. U kunt ook de opdracht **[!UICONTROL Settings]** snelle actie van de inzamelingsduimnagel.
1. Wijzig de verzamelingsinstellingen op de pagina **[!UICONTROL Collection Settings]**. Wijzig bijvoorbeeld de titel van de verzameling, beschrijvingen, leden en machtigingen zoals beschreven in [Verzamelingen toevoegen](#creating-a-collection).

1. Klik op **[!UICONTROL Save]**.

## Een verzameling verwijderen {#deleting-a-collection}

1. Selecteer een of meer verzamelingen in de console Verzamelingen en klik op Verwijderen op de werkbalk.

1. Klik op **[!UICONTROL Delete]** om de verwijderactie te bevestigen.

   >[!NOTE]
   >
   >U kunt slimme verzamelingen ook verwijderen door [opgeslagen zoekopdrachten verwijderen](#saved-searches).

## Een verzameling downloaden {#downloading-a-collection}

Wanneer u een verzameling downloadt, wordt de volledige hiërarchie van elementen in de verzameling gedownload, inclusief mappen en onderliggende verzamelingen.

1. Selecteer een of meer verzamelingen die u wilt downloaden in de console Verzamelingen.
1. Klik **[!UICONTROL Download]** op de werkbalk.
1. In de **[!UICONTROL Download]** dialoogvenster, klikt u op **[!UICONTROL Download]**. Als u de uitvoeringen van de elementen in de verzameling wilt downloaden, selecteert u **[!UICONTROL Renditions]**. Selecteer de **[!UICONTROL Email]** optie om een e-mailbericht naar de eigenaar van de verzameling te verzenden.

   Wanneer u een verzameling selecteert die u wilt downloaden, wordt de volledige maphiërarchie onder de verzameling gedownload. Als u elke verzameling die u downloadt (inclusief elementen in onderliggende verzamelingen die onder de bovenliggende verzameling zijn genest), wilt opnemen in een afzonderlijke map, selecteert u **[!UICONTROL Create separate folder for each asset]**.

## Geneste verzamelingen maken {#creating-nested-collections}

U kunt een verzameling toevoegen aan een andere verzameling, zodat u een geneste verzameling maakt.

1. Selecteer in de verzamelingsconsole de gewenste verzameling of groep verzamelingen en klik op **[!UICONTROL To Collection]** in de werkbalk.

1. Van de **[!UICONTROL Add To Collection]** pagina, selecteert u de verzameling waarin u de verzameling wilt toevoegen.

   >[!NOTE]
   >
   >De laatst bijgewerkte verzameling is standaard geselecteerd in het dialoogvenster **[!UICONTROL Add To Collection]** pagina.

1. Klik op **[!UICONTROL Add]**. Een bericht bevestigt dat de inzameling aan de doelinzameling in wordt toegevoegd **[!UICONTROL Select Destination]** pagina. Sluit het bericht om het proces te voltooien.

>[!NOTE]
>
>Slimme verzamelingen kunnen niet worden genest. Met andere woorden, slimme verzamelingen kunnen geen andere verzameling bevatten.

## Opgeslagen zoekopdrachten {#saved-searches}

In de [!DNL Assets] kunt u elementen zoeken of filteren op basis van bepaalde regels, zoekcriteria of aangepaste zoekfacetten. Als u deze opslaat als **[!UICONTROL Saved Searches]**, kunt u ze later openen vanuit de lijst **[!UICONTROL Saved Searches]** in het deelvenster Filteren. Als u een opgeslagen zoekopdracht maakt, wordt ook een slimme verzameling gemaakt.

![saved_search_list](assets/saved_searches_list.png)

Opgeslagen zoekopdrachten worden gemaakt wanneer u een slimme verzameling maakt. Slimme verzamelingen worden automatisch toegevoegd aan de lijst met **[!UICONTROL Saved Searches]**. De [!UICONTROL Saved Searches] query voor de verzameling wordt opgeslagen in het dialoogvenster `dam:query` eigenschap in CRXDE op de relatieve locatie `/content/dam/collections/`. Er gelden geen limieten voor de zoekopdrachten die u kunt opslaan en voor de opgeslagen zoekopdrachten die in de lijst worden weergegeven.

>[!NOTE]
>
>U kunt slimme verzamelingen op dezelfde manier delen als statische verzamelingen.

Opgeslagen zoekopdrachten bewerken is hetzelfde als slimme verzamelingen bewerken. Zie voor meer informatie [een slimme verzameling bewerken](#editing-a-smart-collection).

Voer de volgende stappen uit om opgeslagen zoekopdrachten te verwijderen:

1. In de [!DNL Assets] gebruikersinterface, klik onderzoek ![zoekoptie](assets/do-not-localize/search_icon.png).
1. Selecteer met de cursor in het veld Onderzoek de optie `Return` toets.
1. In de [!DNL Experience Manager] , opent u het deelvenster Filters.
1. Van de **[!UICONTROL Saved Searches]** lijst, klik **[!UICONTROL Delete]** naast de slimme verzameling die u wilt verwijderen.

   ![select_smart_collection](assets/select_smart_collection.png)

1. Klik op **[!UICONTROL Delete]** om de opgeslagen zoekopdracht te verwijderen.

## Een workflow op een verzameling uitvoeren {#running-a-workflow-on-a-collection}

U kunt een workflow voor de elementen in een verzameling uitvoeren. Als de verzameling geneste verzamelingen bevat, wordt de workflow ook uitgevoerd op de elementen in de geneste verzamelingen. Als de verzameling en de geneste verzameling echter dubbele elementen bevatten, wordt de workflow slechts eenmaal uitgevoerd voor dergelijke elementen.

1. Openen **[!UICONTROL Assets]** > **[!UICONTROL Collections]**. Selecteer een specifieke verzameling als u een workflow op die verzameling wilt uitvoeren.
1. Openen **[!UICONTROL Timeline]** spoorwegen. Klikken ![chevron omhoog](assets/do-not-localize/chevron-up-icon.png) en klik op **[!UICONTROL Start Workflow]**.
1. In de **[!UICONTROL Start Workflow]** selecteert u een workflowmodel in de lijst. Selecteer bijvoorbeeld de **[!UICONTROL DAM Update Asset]** model.
1. Voer een titel in voor de workflow en klik op **[!UICONTROL Start]**.
1. Klik op **[!UICONTROL Proceed]**. De workflow verwerkt alle elementen in de geselecteerde verzameling.

>[!MORELIKETHIS]
>
>* [Experience Manager Assets-e-mailberichten configureren](/help/sites-administering/notification.md#assetsconfig)
>* [Een revisietaak maken voor verzamelingen](bulk-approval.md)
