---
title: Verzamelingen van digitale middelen beheren
description: Leer taken om Inzamelingen van activa te beheren, zoals creeer, mening, schrap, geef, en download inzamelingen uit te geven.
contentOwner: AG
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 27fdeaf50255379fd6e5bb45eaf593cec895cd04

---


# Verzamelingen beheren {#managing-collections}

Een inzameling is een reeks activa binnen de Activa van de Manager van de Ervaring van Adobe. De inzamelingen van het gebruik om activa tussen gebruikers te delen. De reeks kan statische inzameling of een dynamische inzameling zijn die op onderzoeksresultaten gebaseerd is.

In tegenstelling tot omslagen, kan een inzameling activa van verschillende plaatsen omvatten. U kunt inzamelingen met diverse gebruikers delen die verschillende niveaus van voorrechten, met inbegrip van het bekijken, het uitgeven, etc. worden toegewezen.

U kunt veelvoudige inzamelingen met een gebruiker delen. Elke inzameling bevat verwijzingen naar activa. De referentiële integriteit van activa wordt gehandhaafd over inzamelingen.

De inzamelingen zijn van de volgende types, die op de manier worden gebaseerd zij activa collationeren:

* Een inzameling die een statische verwijzingslijst van activa, omslagen, en andere inzamelingen bevat.

* Een slimme inzameling die dynamisch activa omvat die op een onderzoekscriteria worden gebaseerd.

## Heb toegang tot de inzamelingsconsole {#navigating-the-collections-console}

Om de **[!UICONTROL Verzamelingen]** te openen, tik of klik het embleem van de Manager van de Ervaring. Van de navigatiepagina, ga naar **[!UICONTROL Activa]** > **[!UICONTROL Inzamelingen]**.

## Een verzameling maken {#creating-a-collection}

U kunt een inzameling of met [statische verwijzingen](#creating-a-collection-with-static-references) tot stand brengen of gebaseerd op een op [onderzoekscriteria-gebaseerde filter](#creating-a-smart-collection). U kunt een inzameling van een lightbox ook tot stand brengen.

### Creeer een inzameling met statische verwijzingen {#creating-a-collection-with-static-references}

U kunt een inzameling met statische verwijzingen, bijvoorbeeld een inzameling met verwijzingen naar activa, omslagen, inzamelingen, spin reeksen, en beeldreeksen tot stand brengen.

1. Navigeer aan de console van **[!UICONTROL Inzamelingen]** .
1. Tik op/klik op **[!UICONTROL Maken]** op de werkbalk.
1. In de **[!UICONTROL Create pagina van de Inzameling]** , ga een titel en een facultatieve beschrijving voor de inzameling in.
1. Voeg leden aan de inzameling toe en wijs aangewezen toestemmingen toe. Alternatief, selecteer de **[!UICONTROL Openbare Inzameling]** om alle gebruikers toe te staan om tot de inzameling toegang te hebben.

   >[!NOTE]
   >
   >Om de leden toe te laten om inzamelingen met andere gebruikers te delen, verstrek de `dam-users` groep gelezen toestemmingen bij de weg `home/users`. Geef toestemming aan de gebruikers bij `/content/dam/collections` plaats om de gebruikers toe te staan om de Inzamelingen in pop - op lijsten te bekijken. Alternatief, maak de gebruiker een deel van `dam-users` groep.

1. (Facultatief) voeg een duimnagelbeeld voor de inzameling toe.
1. Tik/klik op **[!UICONTROL Maken]** en tik vervolgens op/klik op **[!UICONTROL OK]** om het dialoogvenster te sluiten. Een inzameling met de gespecificeerde titel en de eigenschappen wordt geopend in de console van Inzamelingen.

   >[!NOTE]
   >
   >De Activa van de Manager van de ervaring laten u overzichtstaken voor een inzameling tot stand brengen gelijkend op de manier u overzichtstaken voor een activaomslag creeert.

   Om activa aan de inzameling toe te voegen, navigeer aan het gebruikersinterface van Activa. Voor details, zie activa [toevoegen aan een inzameling](#adding-assets-to-a-collection).

### Creeer inzamelingen gebruikend dropzone {#create-collections-using-dropzone}

U kunt activa van de Activa UI aan een inzameling slepen. U kunt een exemplaar van een inzameling ook tot stand brengen en de activa daar slepen.

1. Van het gebruikersinterface van Activa, selecteer de activa u aan een inzameling wilt toevoegen.
1. Sleep de activa aan de **[!UICONTROL Daling in de streek van de Inzameling]** . Alternatief, tik/klik het pictogram **[!UICONTROL aan van de Inzameling]** van de toolbar.

   ![drop_in_collectie](assets/drop_in_collection.png)

1. In **[!UICONTROL Add aan de pagina van de Inzameling]** , tik/klik het **[!UICONTROL Create pictogram van de Inzameling]** van de toolbar.

   Als u de activa aan een bestaande inzameling wilt toevoegen, selecteer het van de pagina, en de tikken/de klik **[!UICONTROL voegt]** toe. Door gebrek, wordt de onlangs bijgewerkte inzameling geselecteerd.

1. In de **[!UICONTROL Create Nieuwe dialoog van de Inzameling]** , specificeer een naam voor de inzameling. Als u de inzameling voor alle gebruikers toegankelijk wilt zijn, uitgezochte **[!UICONTROL Openbare Inzameling]**.
1. Tik/klik op **[!UICONTROL Doorgaan]** om de verzameling te maken.

### Creeer een slimme inzameling {#creating-a-smart-collection}

Een slimme Inzameling gebruikt een onderzoekscriteria om activa dynamisch te bevolken. U kunt een Slimme Inzameling tot stand brengen gebruikend slechts dossiers en niet omslagen of dossiers en omslagen.

Om een slimme inzameling tot stand te brengen, volg de stappen:

1. Navigeer aan het gebruikersinterface van Activa en tik/klik het onderzoekspictogram.

1. Ga onderzoekssleutelwoord in de doos van het Onderzoek in en druk binnengaan. Open het paneel van Filters en pas een onderzoeksfilter toe.

1. Van de lijst van **[!UICONTROL Dossiers &amp; van Omslagen]** , uitgezochte **[!UICONTROL Dossiers]**.

   ![file_option](assets/files_option.png)

1. Tik/klik **[!UICONTROL sparen Slimme Inzameling]**.

1. Specificeer een naam voor de inzameling. Selecteer **[!UICONTROL Openbaar]** om de groep van Gebruikers DAM met de rol van de Kijker aan de slimme inzameling toe te voegen.

   ![save_Collection](assets/save_collection.png)

   >[!NOTE]
   >
   >Als u **[!UICONTROL Openbaar]** selecteert, wordt de slimme inzameling beschikbaar aan iedereen met de eigenaarrol nadat u het creeert. Als u de **[!UICONTROL Openbare]** optie schrapt, wordt de de gebruikersgroep van DAM niet meer geassocieerd met de slimme inzameling.

1. Tik/klik op **[!UICONTROL Opslaan]** om de slimme verzameling te maken en sluit vervolgens het berichtenvak om het proces te voltooien.

   De nieuwe slimme inzameling wordt ook toegevoegd aan de **[!UICONTROL Bewaarde lijst van Onderzoek]** .

   ![verzameling_lijst](assets/collection_listing.png)

   Het etiket van de **[!UICONTROL Create Slimme knoop van de Selectie]** verandert om Slimme Selectie **[!UICONTROL uit te]** geven. Om de montages van de slimme inzameling uit te geven, selecteer **[!UICONTROL Dossiers]** van de **[!UICONTROL Dossiers &amp; lijst van Omslagen]** . Dan, tik/klik de **[!UICONTROL Edit Slimme knoop van de Selectie]** .

   ![chlimage_1-7](assets/chlimage_1-112.png)

## Voeg activa aan een inzameling toe {#adding-assets-to-a-collection}

U kunt activa aan een inzameling toevoegen die een lijst van referenced activa of omslagen bevat. De slimme inzamelingen gebruiken een onderzoeksvraag om activa te bevolken. Daarom zijn de statische verwijzingen naar activa en omslagen niet toepasselijk op hen.

1. In het gebruikersinterface van Activa, selecteer de activa en tik/klik het pictogram van de Inzameling **** aan van de toolbar.

   ![chlimage_1-8](assets/chlimage_1-113.png)

   Alternatief, kunt u de activa aan de **[!UICONTROL Daling in het gebied van de Inzameling]** op de interface slepen. Voeg de activa toe wanneer het etiket van het gebied in **[!UICONTROL Daling verandert om toe te voegen]**.

1. In **[!UICONTROL Add aan de pagina van de Inzameling]** , selecteer de inzameling waaraan u de activa wilt toevoegen.

1. Tik/klik op **[!UICONTROL Toevoegen]** en sluit het bevestigingsbericht. De activa worden toegevoegd aan de inzameling.

## Geef een slimme inzameling uit {#editing-a-smart-collection}

De slimme inzamelingen worden gebouwd door een onderzoek te bewaren zodat kunt u hun inhoud veranderen door de onderzoeksparameters van het [bewaarde onderzoek](#saved-searches)te wijzigen.

1. In het gebruikersinterface van Activa, tik/klik het onderzoekspictogram van de toolbar.

   ![chlimage_1-9](assets/chlimage_1-110.png)

1. Met de curseur in de doos van het Onderzoek, druk de sleutel van de Terugkeer.
1. Tik/klik op het pictogram GlobalNav om het deelvenster Filters weer te geven.
1. Van de **[!UICONTROL Bewaarde lijst van Onderzoek]** , selecteer de slimme inzameling u wilt wijzigen. Het paneel van het Onderzoek toont de filters die voor het bewaarde onderzoek worden gevormd.

   ![select_smart_collection](assets/select_smart_collection.png)

1. Van de lijst van **[!UICONTROL Dossiers &amp; van Omslagen]** , uitgezochte **[!UICONTROL Dossiers]**.
1. Wijzig zonodig één of meerdere filters. Het lusje/de klik **[!UICONTROL geeft Slimme Inzameling]** uit.

   U kunt de naam van de slimme inzameling ook uitgeven.

   ![bewerkings_smart_collectiondialogue](assets/edit_smart_collectiondialog.png)

1. Tik/klik op **[!UICONTROL Opslaan]**. De **[!UICONTROL Edit Slimme dialoog van de Inzameling]** verschijnt.
1. Tik/klik op **[!UICONTROL Overschrijven]** om de oorspronkelijke slimme verzameling te vervangen door de bewerkte verzameling. Alternatief, selecteer **[!UICONTROL sparen als]** om de uitgegeven inzameling afzonderlijk te bewaren.
1. Tik in het bevestigingsvenster op/klik op **[!UICONTROL Opslaan]** om het proces te voltooien.

## De mening en geeft inzamelingsmeta-gegevens uit {#viewing-and-editing-collection-metadata}

De meta-gegevens van de inzameling omvat gegevens over de inzameling, met inbegrip van om het even welke markeringen die worden toegevoegd.

1. Van de console van Inzamelingen, selecteer een inzameling en tik/klik het pictogram van **[!UICONTROL Eigenschappen]** van de toolbar.
1. In de pagina van de Meta-gegevens **[!UICONTROL van de]** Inzameling, bekijk de inzamelingsmeta-gegevens van de **[!UICONTROL Basis]** en **[!UICONTROL Geavanceerde]** lusjes.
1. Wijzig de meta-gegevens, zonodig, en tik/klik dan **[!UICONTROL sparen &amp; sluit]** van de toolbar om de veranderingen te bewaren.

## Geef meta-gegevens van veelvoudige inzamelingen in bulk uit {#editing-collection-metadata-in-bulk}

U kunt de meta-gegevens van veelvoudige inzamelingen gelijktijdig uitgeven. Deze functionaliteit helpt u snel gemeenschappelijke meta-gegevens in veelvoudige inzamelingen herhalen.

1. In de console van Inzamelingen, selecteer twee of meer inzamelingen waarvoor u meta-gegevens wilt uitgeven.
1. Tik op/klik op het pictogram **[!UICONTROL Eigenschappen]** op de werkbalk.
1. In de pagina van de Meta-gegevens **[!UICONTROL van de]** Inzameling, geef de meta-gegevens onder de **[!UICONTROL Basis]** en **[!UICONTROL Geavanceerde]** lusjes, zonodig uit.
1. Om de meta-gegevenseigenschappen voor een specifieke inzameling te bekijken, schrap de resterende inzamelingen in de inzamelingslijst. De gebieden van de meta-gegevensredacteur zijn bevolkt met de meta-gegevens voor de bepaalde inzameling.

   >[!NOTE]
   >
   >* In de pagina van inzamelingseigenschappen, kunt u inzamelingen uit de lijst van inzamelingen verwijderen door hen te schrappen. De inzamelingslijst heeft alle inzamelingen die door gebrek worden geselecteerd. De meta-gegevens voor inzamelingen die u verwijdert wordt niet bijgewerkt.
   >* Bij de bovenkant van de lijst, selecteer de controledoos dichtbij **[!UICONTROL Titel]** om tussen het selecteren van de inzamelingen van een knevel te voorzien en de lijst te ontruimen.


1. Tik/klik op **[!UICONTROL Opslaan en sluiten]** op de werkbalk en sluit het bevestigingsvenster om het proces te voltooien.
1. Om de nieuwe meta-gegevens met de bestaande meta-gegevens toe te voegen, selecteer **[!UICONTROL voeg wijze]** toe. Als u deze optie niet selecteert, vervangt de nieuwe meta-gegevens de bestaande meta-gegevens op de gebieden. Tik/klik op **[!UICONTROL Indienen]**.

   >[!NOTE]
   >
   >De meta-gegevens u voor de geselecteerde inzamelingen toevoegt beschrijft de vorige meta-gegevens voor deze inzamelingen. Gebruik de [!UICONTROL Add wijze] om nieuwe waarden aan de bestaande meta-gegevens op de gebieden toe te voegen die veelvoudige waarden kunnen bevatten. De gebieden van de enig-waarde worden altijd beschreven. Om het even welke markeringen u op het gebied van [!UICONTROL Markeringen] toevoegt, worden toegevoegd aan de bestaande lijst van markeringen in de meta-gegevens.

Om de pagina van meta-gegevens aan te passen [!UICONTROL Eigenschappen] , met inbegrip van het toevoegen van, het wijzigen van, het schrappen van meta-gegevenseigenschappen, gebruik de redacteur van het Schema.

>[!TIP]
>
>De bulk het uitgeven methode werkt voor activa beschikbaar in een inzameling. Voor de activa die over omslagen beschikbaar zijn of een gemeenschappelijke criteria aanpassen, is het mogelijk om de meta-gegevens in [bulk bij te werken na het zoeken](/help/assets/search-assets.md#metadataupdates).

## Zoekverzamelingen {#searching-collections}

U kunt inzamelingen van de console van Inzamelingen zoeken. Wanneer u met sleutelwoorden in het vakje van het Onderzoek zoekt, zoekt de Activa AEM naar inzamelingsnamen, meta-gegevens, en de markeringen die aan de inzamelingen worden toegevoegd.

Als u naar inzamelingen van het hoogste niveau zoekt, slechts zijn de individuele inzamelingen teruggekeerd in onderzoeksresultaten. De activa of de omslagen binnen de inzamelingen worden uitgesloten. In alle andere gevallen (bijvoorbeeld, binnen een individuele inzameling of in een omslaghiërarchie), zijn alle relevante activa, omslagen, en inzamelingen teruggekeerd.

## Zoeken in verzamelingen {#searching-within-collections}

In de console van Inzamelingen, tik/klik een inzameling om het te openen.

Binnen een inzameling, is het onderzoek van Activa AEM beperkt tot activa (en hun markeringen en meta-gegevens) binnen de inzameling die u bekijkt. Wanneer u binnen een omslag zoekt, zijn alle passende activa en kindomslagen binnen de huidige omslag teruggekeerd. Wanneer u binnen een inzameling zoekt, slechts zijn de passende activa, de omslagen, en andere inzamelingen die directe leden van de inzameling zijn teruggekeerd.

## Verzamelinstellingen bewerken {#editing-collection-settings}

U kunt inzamelingsmontages, zoals titel en beschrijving uitgeven, of leden toevoegen aan een inzameling.

1. Selecteer een inzameling, en tik/klik het pictogram van **[!UICONTROL Montages]** in de toolbar. Alternatief, gebruik de snelle actie van **[!UICONTROL Montages]** van de inzamelingsduimnagel.
1. Wijzig de inzamelingsmontages in de pagina van de Montages **[!UICONTROL van de]** Inzameling. Bijvoorbeeld, wijzig de inzamelingstitel, beschrijvingen, leden, en toestemmingen zoals die in het [Toevoegen van Inzamelingen](#creating-a-collection)worden besproken.

1. Om de veranderingen te bewaren, tik/klik **[!UICONTROL sparen]**.

## Een verzameling verwijderen {#deleting-a-collection}

1. Van de console van Inzamelingen, selecteer één of meerdere inzamelingen en tik/klik het schrappingspictogram in de toolbar.

   ![chlimage_1-11](assets/chlimage_1-177.png)

1. Tik in het dialoogvenster op/klik op **[!UICONTROL Verwijderen]** om de verwijderactie te bevestigen.

   >[!NOTE]
   >
   >U kunt slimme inzamelingen ook schrappen door bewaarde onderzoeken [te](#saved-searches)schrappen.

## Download een inzameling {#downloading-a-collection}

Wanneer u een inzameling downloadt, wordt de volledige hiërarchie van activa binnen de inzameling gedownload, met inbegrip van omslagen en kindinzamelingen.

1. Van de console van Inzamelingen, selecteer één of meerdere inzamelingen om te downloaden.
1. Tik op/klik op het downloadpictogram op de werkbalk.
1. In de **[!UICONTROL dialoog van de Download]** , tik/klik **[!UICONTROL Download]**. Als u de rendities van de activa binnen de inzameling wilt downloaden, uitgezochte **[!UICONTROL Rendities]**. Selecteer de optie **[!UICONTROL E-mail]** om een e-mailbericht naar de eigenaar van de inzameling te verzenden.

   Wanneer u een te downloaden inzameling selecteert, wordt de volledige omslaghiërarchie onder de inzameling gedownload. Om elke inzameling te omvatten u downloadt (met inbegrip van activa in kindinzamelingen die onder de ouderinzameling worden genesteld) in een individuele omslag, uitgezocht **[!UICONTROL creeer afzonderlijke omslag voor elke activa]**.

## Geneste verzamelingen maken {#creating-nested-collections}

U kunt een inzameling aan een andere inzameling toevoegen, daardoor creërend een genestelde inzameling.

1. Van de console van Inzamelingen, selecteer de gewenste inzameling of de groep inzamelingen, en tik of klik **[!UICONTROL aan Inzameling]** in de toolbar.

1. Van **[!UICONTROL Add aan de pagina van de Inzameling]** , selecteer de inzameling waarin om de inzameling toe te voegen.

   >[!NOTE]
   >
   >De onlangs bijgewerkte inzameling wordt geselecteerd door gebrek in **[!UICONTROL Add aan de pagina van de Inzameling]** .

1. Tik/klik op **[!UICONTROL Toevoegen]**. Een bericht bevestigt dat de inzameling aan de doelinzameling in de **[!UICONTROL Uitgezochte pagina van de Bestemming]** wordt toegevoegd. Sluit het bericht om het proces te voltooien.

>[!NOTE]
>
>De slimme inzamelingen kunnen niet worden genesteld. Met andere woorden, kunnen de Slimme inzamelingen geen andere inzameling bevatten.

## Opgeslagen zoekopdrachten {#saved-searches}

In het gebruikersinterface van Activa, kunt u activa zoeken of filtreren die op bepaalde regels, onderzoekscriteria, of de facetten van het douaneonderzoek worden gebaseerd. Als u deze opslaat als **[!UICONTROL Opgeslagen zoekopdrachten]**, kunt u deze later openen vanuit de lijst **[!UICONTROL Opgeslagen zoekopdrachten]** in het deelvenster Filter. Het creëren van een bewaard onderzoek leidt ook tot een slimme inzameling.

![opgeslagen_zoekopdrachten_lijst](assets/saved_searches_list.png)

De bewaarde onderzoeken worden gecreeerd wanneer u een slimme inzameling creeert. De slimme inzamelingen worden automatisch toegevoegd aan de **[!UICONTROL Bewaarde lijst van Onderzoek]** . De opgeslagen vraag van Onderzoek voor de inzameling wordt opgeslagen in het `dam:query` bezit in CRXDE bij de relatieve plaats `/content/dam/collections/`.

>[!NOTE]
>
>U kunt slimme inzamelingen op de zelfde manier delen aangezien u statische inzamelingen deelt.

Het uitgeven van bewaarde onderzoeken is het zelfde als het uitgeven van slimme inzamelingen. Voor details, zie een slimme inzameling [](#editing-a-smart-collection)uitgeven.

Om bewaarde onderzoeken te schrappen, volg deze stappen:

1. In het gebruikersinterface van Activa, tik/klik het onderzoekspictogram van de toolbar.

   ![chlimage_1-13](assets/chlimage_1-114.png)

1. Met de curseur op het gebied van het Onderzoek, druk de Enter sleutel.

1. Klik of tik op het pictogram GlobalNav om het deelvenster Filters weer te geven.

1. Van de **[!UICONTROL Opgeslagen lijst van Zoekopdrachten]** , tik/klik **[!UICONTROL Schrapping]** naast de slimme inzameling die u wilt schrappen.

   ![select_smart_collection-1](assets/select_smart_collection-1.png)

1. Tik in het dialoogvenster op/klik op **[!UICONTROL Verwijderen]** om de opgeslagen zoekopdracht te verwijderen.

## Voer een werkschema op een inzameling uit {#running-a-workflow-on-a-collection}

U kunt een werkschema voor de activa binnen een inzameling in werking stellen. Als de inzameling genestelde inzamelingen bevat, loopt het werkschema ook op de activa binnen de genestelde inzamelingen. Nochtans, als de inzameling en de genestelde inzameling dubbele activa bevatten, loopt het werkschema slechts eenmaal voor dergelijke activa.

1. Van de console van Inzamelingen, selecteer een inzameling waarop u een werkschema wilt in werking stellen.
1. Tik/klik het pictogram GlobalNav, en kies **[!UICONTROL Chronologie]** van de lijst.
1. Van de chronologie, klik of tik het pictogram van het Gebied bij de bodem, en dan tik/klik de Werkschema **[!UICONTROL van het]** Begin.

   ![chlimage_1-14](assets/chlimage_1-137.png)

1. In de sectie van het Werkschema **[!UICONTROL van het]** Begin, selecteer een werkschemamodel van de lijst. Bijvoorbeeld, selecteer het model van de Activa **[!UICONTROL van de Update van]** DAM.
1. Voer een titel in voor de workflow en tik op/klik op **[!UICONTROL Start]**.
1. Tik in het dialoogvenster op/klik op **[!UICONTROL Doorgaan]**. De werkschemalooppas op alle activa in de inzameling.

>[!MORELIKETHIS]
>
>* [E-mailberichten van Experience Manager configureren](/help/sites-administering/notification.md#assetsconfig)
>* [Creeer een overzichtstaak voor Inzamelingen](bulk-approval.md)

