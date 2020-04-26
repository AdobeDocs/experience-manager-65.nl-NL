---
title: Samengestelde elementen beheren met verwijzingen en elementen van meerdere pagina's in Adobe Experience Manager.
description: Leer hoe u verwijzingen naar digitale elementen maakt in Adobe InDesign, Adobe Illustrator en Adobe Photoshop. Met de functie Paginaviewer kunt u afzonderlijke subelementpagina's van bestanden met meerdere pagina's weergeven, zoals PDF-, INDD-, PPT-, PPTX- en AI-bestanden.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 790efeaff6c8cf7e60104601e08955180dbb9600

---


# Samengestelde en uit meerdere pagina&#39;s bestaande elementen beheren {#managing-compound-assets}

[!DNL Adobe Experience Manager Assets] kan vaststellen of een geüpload bestand verwijzingen bevat naar elementen die al in de opslagplaats bestaan. Deze functie is alleen beschikbaar voor ondersteunde bestandsindelingen. Als het geüploade element verwijzingen naar de middelen van Experience Manager bevat, wordt een bidirectionele koppeling gemaakt tussen de geüploade en de bestanden waarnaar wordt verwezen.

Naast redundantie te elimineren, verbetert het verwijzen naar de middelen in Adobe Creative Cloud-toepassingen de samenwerking en verhoogt het de efficiëntie en productiviteit van gebruikers.

[!DNL Experience Manager Assets] ondersteunt bidirectionele referentie. U vindt de middelen waarnaar wordt verwezen op de elementdetailpagina van het geüploade bestand. Daarnaast kunt u de bestanden waarnaar wordt verwezen, weergeven op de pagina met elementdetails van het element waarnaar wordt verwezen.

Verwijzingen worden opgelost op basis van pad, document-id en instantie-id van de middelen waarnaar wordt verwezen.

## Digitale elementen toevoegen als verwijzingen in [!DNL Adobe Illustrator]{#refai}

U kunt vanuit een [!DNL Adobe Illustrator] bestand verwijzen naar bestaande digitale elementen.

1. Haal de digitale middelen op in het lokale bestandssysteem met behulp van de [Experience Manager-bureaubladtoepassing](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html). Navigeer naar de bestandssysteemlocatie van het element waarnaar u wilt verwijzen.
1. Sleep het element van de lokale map naar het [!DNL Illustrator] bestand.

1. Sla het [!DNL Illustrator] bestand op het gekoppelde station op of [upload het bestand naar](/help/assets/managing-assets-touch-ui.md#uploading-assets) de opslagplaats van Experience Manager.

1. Nadat de workflow is voltooid, gaat u naar de pagina met elementdetails voor het element. De verwijzingen naar bestaande digitale activa zijn vermeld onder **[!UICONTROL Afhankelijkheden]** in de **[!UICONTROL kolom van Verwijzingen]** .

   ![chlimage_1-84](assets/chlimage_1-258.png)

1. De middelen waarnaar wordt verwezen die onder **[!UICONTROL Afhankelijkheden]** verschijnen kunnen ook door dossiers buiten huidige worden van verwijzingen voorzien. Als u een lijst met referentiebestanden voor een element wilt weergeven, klikt u op het element onder **[!UICONTROL Afhankelijkheden]**.

   ![chlimage_1-85](assets/chlimage_1-259.png)

1. Klik op Eigenschappen **[!UICONTROL van]** weergave op de werkbalk. Op de pagina [!UICONTROL Eigenschappen] wordt de lijst met bestanden die naar het huidige element verwijzen, weergegeven onder de kolom **[!UICONTROL Verwijzingen]** op het tabblad **[!UICONTROL Standaard]** .

   ![bekijk de verwijzingen van de Middelen van de Manager van de Ervaring in de kolom van Verwijzingen in activadetails](assets/asset-references.png)

   *Afbeelding: Verwijzingen naar elementen in de gegevens van elementen*

## Digitale elementen toevoegen als verwijzingen in [!DNL Adobe InDesign]{#add-aem-assets-as-references-in-adobe-indesign}

Als u vanuit een [!DNL InDesign] bestand naar digitale elementen wilt verwijzen, sleept u elementen naar het [!DNL InDesign] bestand of exporteert u het [!DNL InDesign] bestand als een ZIP-archief.

Er bestaan al middelen waarnaar wordt verwezen in [!DNL Experience Manager Assets]. U kunt subelementen extraheren door InDesign Server [te](indesign.md)configureren. Ingesloten elementen in een [!DNL InDesign] bestand worden geëxtraheerd als subelementen.

>[!NOTE]
>
>Als de voorvertoning [!DNL InDesign Server] is proxy, wordt de voorvertoning van [!DNL InDesign] bestanden ingesloten in de XMP-metagegevens. In dit geval is het niet expliciet vereist miniatuurextractie uit te voeren. Als de proxy echter niet [!DNL InDesign Server] is proxy, moeten miniaturen expliciet worden uitgepakt voor [!DNL InDesign] bestanden.

### Verwijzingen maken door elementen te slepen {#create-references-by-dragging-aem-assets}

Deze procedure is vergelijkbaar met het [toevoegen van digitale elementen als verwijzingen in Adobe Illustrator](#refai).

### Verwijzingen naar elementen maken door een ZIP-bestand te exporteren {#create-references-to-aem-assets-by-exporting-a-zip-file}

1. Voer de stappen in Workflowmodellen [](/help/sites-developing/workflows-models.md) maken uit om een nieuwe workflow te maken.
1. Gebruik de functie Pakket van [!DNL Adobe InDesign] om het document te exporteren. [!DNL Adobe InDesign] U kunt een document en de gekoppelde elementen als een pakket exporteren. In dit geval bevat de geëxporteerde map een map Koppelingen met subelementen in het [!DNL InDesign] bestand.
1. Maak een ZIP-bestand en upload het naar de [!DNL Experience Manager] opslagplaats.
1. Start de `Unarchiver` workflow.
1. Wanneer de werkstroom is voltooid, wordt er automatisch naar de verwijzingen in de map Koppelingen verwezen als subelementen. Als u een lijst met de desbetreffende elementen wilt weergeven, navigeert u naar de pagina met elementdetails van het [!DNL InDesign] element en sluit u de [Rail](/help/sites-authoring/basic-handling.md#rail-selector).

## Digitale elementen toevoegen als verwijzingen in [!DNL Adobe Photoshop]{#refps}

1. Gebruik [!DNL Experience Manager] bureaubladtoepassing voor toegang [!DNL Experience Manager Assets]. Download en open de middelen op het lokale bestandssysteem. Gebruik de functie Gekoppelde  plaatsen in [!DNL Adobe Photoshop]. Zie Elementen [plaatsen in de bureaubladtoepassing](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html#place-assets-in-native-documents).

   ![chlimage_1-87](assets/chlimage_1-261.png)

1. Opslaan in [!DNL Photoshop] bestand op het gekoppelde station of [uploaden](/help/assets/managing-assets-touch-ui.md#uploading-assets) naar de [!DNL Experience Manager] opslagplaats.
1. Nadat de workflow is voltooid, worden de verwijzingen naar bestaande [!DNL Experience Manager] elementen weergegeven op de pagina met elementdetails.

   Als u de middelen waarnaar wordt verwezen wilt weergeven, sluit u de [Rail](/help/sites-authoring/basic-handling.md#rail-selector) op de pagina met elementdetails.

1. De middelen waarnaar wordt verwezen, bevatten ook de lijst met elementen waarnaar wordt verwezen. Als u een lijst met middelen waarnaar wordt verwezen wilt weergeven, navigeert u naar de pagina met elementdetails en sluit u de [Rail](/help/sites-authoring/basic-handling.md#rail-selector).

>[!NOTE]
>
>Er kan ook worden verwezen naar de elementen in samengestelde elementen op basis van hun document-id en instantie-id. Deze functionaliteit is alleen beschikbaar bij [!DNL Adobe Illustrator] en in [!DNL Adobe Photoshop] versies. Voor andere toepassingen wordt het verwijzen uitgevoerd op basis van het relatieve pad van gekoppelde elementen in het hoofdsamengestelde element, zoals dat in eerdere versies van [!DNL Experience Manager]dit programma is gebeurd.

## Subelementen maken {#generate-subassets}

Voor de ondersteunde elementen met indelingen die uit meerdere pagina&#39;s bestaan (PDF-bestanden, AI-bestanden [!DNL Microsoft PowerPoint] en [!DNL Apple Keynote] bestanden, en [!DNL Adobe InDesign] -bestanden), [!DNL Experience Manager] kunt u subelementen genereren die overeenkomen met elke afzonderlijke pagina van het oorspronkelijke element. Deze subelementen zijn gekoppeld aan het *bovenliggende* element en maken de weergave van meerdere pagina&#39;s eenvoudiger. Voor alle andere doeleinden worden de subactiva behandeld als normale activa in [!DNL Experience Manager].

Genereren van subelementen is standaard uitgeschakeld. Voer de volgende stappen uit om het genereren van subelementen in te schakelen:

1. Meld u aan bij Experience Manager als beheerder. Ga naar **[!UICONTROL Extra > Workflow > Modellen]**.
1. Selecteer de **[!UICONTROL DAM-workflow Element]** bijwerken en klik op **[!UICONTROL Bewerken]**.
1. Klik op **[!UICONTROL Zijpaneel]** in-/uitschakelen en zoek de stap **[!UICONTROL Subelement]** maken. Voeg de stap toe aan de workflow. Klik op **[!UICONTROL Synchroniseren]**.

Voer een van de volgende handelingen uit om de subelementen te genereren:

* Nieuwe elementen: De [!UICONTROL DAM-workflow Middelen] bijwerken wordt uitgevoerd op elk nieuw element waarnaar geüpload wordt [!DNL Experience Manager]. Subelementen worden automatisch gegenereerd voor nieuwe elementen die uit meerdere pagina&#39;s bestaan.
* Bestaande elementen met meerdere pagina&#39;s: Voer handmatig de workflow [!UICONTROL DAM Update Assets] uit volgens een van de volgende stappen:

   * Selecteer een element en klik op [!UICONTROL Tijdlijn] om het linkerdeelvenster te openen. U kunt ook de sneltoets gebruiken `alt + 3`. Klik op Workflow starten, selecteer [!UICONTROL DAM Update Asset], klik op [!UICONTROL Start]en klik op [!UICONTROL Doorgaan].
   * Selecteer een element en klik op [!UICONTROL Maken > Workflow] op de werkbalk. Selecteer in het pop-updialoogvenster de [!UICONTROL DAM-workflow Element] bijwerken, klik op [!UICONTROL Start]en [!UICONTROL Ga verder].

Met name voor Microsoft Word-documenten voert u de workflow **[!UICONTROL DAM Parse Word Documents]** uit. Er wordt een `cq:Page` component gegenereerd op basis van de inhoud van het Microsoft Word-document. De afbeeldingen die uit het document zijn geëxtraheerd, worden vanuit de `cq:Page` component gebruikt. Deze afbeeldingen worden geëxtraheerd, zelfs als het genereren van subelementen is uitgeschakeld.

## Subelementen weergeven {#viewing-subassets}

De subelementen worden alleen weergegeven als de subelementen zijn gegenereerd en beschikbaar zijn voor het geselecteerde element met meerdere pagina&#39;s. Open het element met meerdere pagina&#39;s om de gegenereerde subelementen weer te geven. Klik in de linkerbovenhoek van de pagina op het pictogram ![Linkerspoor en klik op](assets/do-not-localize/aem_leftrail_contentonly.png) Submiddelen **** in de lijst. Wanneer u **[!UICONTROL Subassets]** in de lijst selecteert. U kunt ook de sneltoets gebruiken `alt + 5`.

![Subelementen weergeven voor elementen die uit meerdere pagina&#39;s bestaan](assets/view_subassets_simulation.gif)

## Pagina&#39;s van een bestand met meerdere pagina&#39;s weergeven {#view-pages-of-a-multi-page-file}

U kunt een bestand met meerdere pagina&#39;s, zoals PDF, INDD, PPT, PPTX en AI, weergeven met de functie Paginaviewer van [!DNL Experience Manager Assets]. Open een element met meerdere pagina&#39;s en klik op Pagina&#39;s **** weergeven in de linkerbovenhoek van de pagina. In de Paginaviewer die wordt geopend, worden de pagina&#39;s van het element en de besturingselementen weergegeven waarmee u door elke pagina kunt bladeren en erop kunt inzoomen.

![Pagina&#39;s van elementen met meerdere pagina&#39;s weergeven en bekijken](assets/view_multipage_asset_fmr.gif)

U kunt bijvoorbeeld pagina&#39;s uitnemen met [!DNL InDesign]behulp van [!DNL InDesign Server]. Als de voorvertoningen van pagina&#39;s worden opgeslagen tijdens het maken van het [!DNL InDesign] bestand, is [!DNL InDesign Server] dit niet vereist voor het uitnemen van pagina&#39;s.

De volgende opties zijn beschikbaar in de werkbalk, in de linkerrails en in de besturingselementen voor de Paginaviewer:

* **[!UICONTROL Bureaubladhandelingen]** om een specifiek submiddel te openen of weer te geven met de [!DNL Experience Manager] bureaubladtoepassing. Zie hoe u bureaubladhandelingen [kunt](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html#desktopactions-v2) configureren als u [!DNL Experience Manager] bureaubladtoepassing gebruikt.

* **[!UICONTROL Met de optie Eigenschappen]** wordt de pagina [!UICONTROL Eigenschappen] van het specifieke subelement geopend.

* **[!UICONTROL Met de optie Annoteren]** kunt u het specifieke subelement annoteren. De annotaties die u op afzonderlijke subelementen gebruikt, worden samen verzameld en weergegeven wanneer het bovenliggende element wordt geopend voor weergave.

* **[!UICONTROL Met de optie Paginaoverzicht]** worden alle subelementen tegelijkertijd weergegeven.

* **[!UICONTROL De optie Tijdlijn]** van de linkerspoorstaaf nadat het ![linker spoorpictogram](assets/do-not-localize/aem_leftrail_contentonly.png) klikt toont de activiteitenstroom voor het dossier.

>[!MORELIKETHIS]
>
>* [Adobe Experience Manager-bureaubladtoepassing gebruiken](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html)
>* [Bureaubladhandelingen configureren in Adobe Experience Manager](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html#desktopactions-v2)
>* [Gekoppelde slimme objecten maken in Adobe Photoshop](https://helpx.adobe.com/photoshop/using/create-smart-objects.html#create-linked-smart-objects)
>* [Afbeeldingen plaatsen in Adobe InDesign](https://helpx.adobe.com/indesign/using/placing-graphics.html)