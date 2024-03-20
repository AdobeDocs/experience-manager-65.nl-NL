---
title: Samengestelde elementen beheren met verwijzingen en meerdere pagina's
description: Leer hoe u verwijzingen naar digitale middelen kunt maken vanuit [!DNL Adobe InDesign], [!DNL Adobe Illustrator], en [!DNL Adobe Photoshop]. Met de functie Paginaviewer kunt u afzonderlijke subelementpagina's van bestanden met meerdere pagina's weergeven, zoals PDF-, INDD-, PPT-, PPTX- en AI-bestanden.
contentOwner: AG
role: User, Admin
feature: Asset Management
exl-id: 1ea9d8fe-602c-452b-9a24-4125b705aedf
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1312'
ht-degree: 0%

---

# Samengestelde en uit meerdere pagina&#39;s bestaande elementen beheren {#managing-compound-assets}

[!DNL Adobe Experience Manager Assets] kan vaststellen of een geüpload bestand verwijzingen bevat naar elementen die al in de opslagplaats bestaan. Deze functie is alleen beschikbaar voor ondersteunde bestandsindelingen. Als het geüploade element verwijzingen bevat naar [!DNL Experience Manager] elementen, wordt een bidirectionele koppeling gemaakt tussen de geüploade en de bestanden waarnaar wordt verwezen.

Naast het elimineren van overtolligheid, verwijzend de activa in [!DNL Adobe Creative Cloud] de toepassingen verbeteren samenwerking en verhoogt de efficiency en de productiviteit van gebruikers.

[!DNL Experience Manager Assets] ondersteunt bidirectionele referentie. U vindt de middelen waarnaar wordt verwezen op de elementdetailpagina van het geüploade bestand. Daarnaast kunt u de bestanden waarnaar wordt verwezen, weergeven op de pagina met elementdetails van het element waarnaar wordt verwezen.

Verwijzingen worden opgelost op basis van pad, document-id en instantie-id van de middelen waarnaar wordt verwezen.

## [!DNL Adobe Illustrator]: Digitale elementen toevoegen als verwijzingen {#refai}

U kunt verwijzen naar bestaande digitale elementen vanuit een [!DNL Adobe Illustrator] bestand.

1. Gebruiken [[!DNL Experience Manager] bureaubladtoepassing](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html), haalt u de digitale elementen op in het lokale bestandssysteem. Navigeer naar de bestandssysteemlocatie van het element waarnaar u wilt verwijzen.
1. Sleep het element van de lokale map naar de map [!DNL Illustrator] bestand.

1. Sla de [!DNL Illustrator] bestand naar het gemonteerde station, of [uploaden](/help/assets/manage-assets.md#uploading-assets) aan de [!DNL Experience Manager] opslagplaats.

1. Nadat de workflow is voltooid, gaat u naar de pagina met elementdetails voor het element. De verwijzingen naar bestaande digitale elementen worden hieronder vermeld **[!UICONTROL Dependencies]** in de **[!UICONTROL References]** kolom.

   ![chlimage_1-84](assets/chlimage_1-258.png)

1. De middelen waarnaar wordt verwezen, die onder **[!UICONTROL Dependencies]** Er kan ook naar worden verwezen door andere bestanden dan het huidige bestand. Als u een lijst met referentiebestanden voor een element wilt weergeven, klikt u op het element onder in **[!UICONTROL Dependencies]**.

   ![chlimage_1-85](assets/chlimage_1-259.png)

1. Klik op **[!UICONTROL View Properties]** op de werkbalk. In de [!UICONTROL Properties] pagina, wordt de lijst met bestanden die verwijzen naar het huidige element weergegeven onder de **[!UICONTROL References]** in de **[!UICONTROL Basic]** tab.

   ![de verwijzingen van Experience Manager Assets in de kolom Referenties in de elementdetails weergeven](assets/asset-references.png)

   *Afbeelding: Verwijzingen naar elementen in de elementen.*

## [!DNL Adobe InDesign]: Digitale elementen toevoegen als verwijzingen {#add-aem-assets-as-references-in-adobe-indesign}

Verwijzen naar digitale elementen vanuit een [!DNL InDesign] bestand, sleept u elementen naar het [!DNL InDesign] bestand of exporteer de [!DNL InDesign] bestand als ZIP-archief.

Er bestaan al elementen waarnaar wordt verwezen in [!DNL Experience Manager Assets]. U kunt subelementen extraheren via [configureren, InDesign Server](indesign.md). Ingesloten elementen in een [!DNL InDesign] bestand wordt geëxtraheerd als subelementen.

>[!NOTE]
>
>Als de [!DNL InDesign Server] proxied is, [!DNL InDesign] de voorvertoning van de bestanden is ingesloten in de XMP metagegevens. In dit geval is het niet expliciet vereist miniatuurextractie uit te voeren. Als de [!DNL InDesign Server] is niet proxy, moeten miniaturen expliciet worden uitgepakt voor [!DNL InDesign] bestanden.

Wanneer een INDD-bestand wordt geüpload, worden de verwijzingen opgehaald door te zoeken naar elementen met `xmpMM:InstanceID` en `xmpMM:DocumentID` in de repository.

### Verwijzingen maken door elementen te slepen {#create-references-by-dragging-aem-assets}

Deze procedure lijkt op [digitale elementen toevoegen als verwijzingen in Adobe Illustrator](#refai).

### Verwijzingen naar elementen maken door een ZIP-bestand te exporteren {#create-references-to-aem-assets-by-exporting-a-zip-file}

1. Voer de stappen uit in [Workflowmodellen maken](/help/sites-developing/workflows-models.md) om een workflow te maken.
1. Gebruik de [Pakketfunctie](https://helpx.adobe.com/indesign/how-to/indesign-package-files-for-handoff.html) van [!DNL Adobe InDesign] om het document te exporteren. [!DNL Adobe InDesign] U kunt een document en de gekoppelde elementen als een pakket exporteren. In dit geval bevat de geëxporteerde map een `Links` map met subelementen in het dialoogvenster [!DNL InDesign] bestand. De `Links` is aanwezig in dezelfde map als het INDD-bestand.
1. Een ZIP-bestand maken en uploaden naar het [!DNL Experience Manager] opslagplaats.
1. Start de `Unarchiver` workflow.
1. Wanneer de werkstroom is voltooid, wordt er automatisch naar de verwijzingen in de map Koppelingen verwezen als subelementen. Navigeer naar de pagina met elementdetails op de pagina met [!DNL InDesign] en sluit het [Rail](/help/sites-authoring/basic-handling.md#rail-selector).

## [!DNL Adobe Photoshop]: Digitale elementen toevoegen als verwijzingen {#refps}

1. Gebruiken [!DNL Experience Manager] bureaubladtoepassing voor toegang tot [!DNL Experience Manager Assets]. Download de bestanden en open ze op het lokale bestandssysteem. Gebruik de [!UICONTROL Place Linked] functionaliteit in [!DNL Adobe Photoshop]. Zie [middelen plaatsen in bureaubladtoepassing](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#place-assets-in-native-documents).

1. In opslaan [!DNL Photoshop] bestand naar het gekoppelde station of [uploaden](/help/assets/manage-assets.md#uploading-assets) aan de [!DNL Experience Manager] opslagplaats.
1. Nadat de workflow is voltooid, worden de verwijzingen naar bestaande [!DNL Experience Manager] elementen worden weergegeven op de pagina met elementdetails.

   Als u de middelen waarnaar wordt verwezen wilt weergeven, sluit u de [Rail](/help/sites-authoring/basic-handling.md#rail-selector) op de pagina met elementdetails.

1. De middelen waarnaar wordt verwezen, bevatten ook de lijst met elementen waarnaar wordt verwezen. Als u een lijst met middelen waarnaar wordt verwezen wilt weergeven, navigeert u naar de pagina met elementdetails en sluit u de [Rail](/help/sites-authoring/basic-handling.md#rail-selector).

>[!NOTE]
>
>Er kan ook worden verwezen naar de elementen in samengestelde elementen op basis van hun document-id en instantie-id. Deze functionaliteit is beschikbaar bij [!DNL Adobe Illustrator] en [!DNL Adobe Photoshop] alleen versies. Voor andere toepassingen wordt het verwijzen uitgevoerd op basis van het relatieve pad van gekoppelde elementen in het belangrijkste samengestelde element, zoals dat in eerdere versies van [!DNL Experience Manager].

## Subelementen maken {#generate-subassets}

Voor de ondersteunde elementen met indelingen van meerdere pagina&#39;s: PDF-bestanden, AI-bestanden, [!DNL Microsoft PowerPoint] en [!DNL Apple Keynote] bestanden, en [!DNL Adobe InDesign] bestanden — [!DNL Experience Manager] U kunt subelementen genereren die overeenkomen met elke afzonderlijke pagina van het oorspronkelijke element. Deze subassets zijn gekoppeld aan de *parent* elementen toevoegen en de weergave van meerdere pagina&#39;s vergemakkelijken. Voor alle andere doeleinden worden de subactiva behandeld als normale activa in [!DNL Experience Manager].

Genereren van subelementen wordt standaard uitgeschakeld. Voer de volgende stappen uit om het genereren van subelementen in te schakelen:

1. Aanmelden [!DNL Experience Manager] als beheerder. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. Selecteren **[!UICONTROL DAM Update Asset]** workflow en klik op **[!UICONTROL Edit]**.
1. Klikken **[!UICONTROL Toggle Side Panel]** en zoek de **[!UICONTROL Create Sub Asset]** stap. Voeg de stap toe aan de workflow. Klik op **[!UICONTROL Sync]**.

Voer een van de volgende handelingen uit om de subelementen te genereren:

* Nieuwe activa: De [!UICONTROL DAM Update Assets] workflow wordt uitgevoerd voor elk nieuw element waarnaar wordt geüpload [!DNL Experience Manager]. Subelementen worden automatisch gegenereerd voor nieuwe elementen van meerdere pagina&#39;s.
* Bestaande elementen van meerdere pagina&#39;s: voer handmatig het [!UICONTROL DAM Update Assets] workflow volgens een van de volgende stappen:

   * Selecteer een element en klik op [!UICONTROL Timeline] om het linkerdeelvenster te openen. U kunt ook de sneltoets gebruiken `alt + 3`. Klikken [!UICONTROL Start Workflow], selecteert u [!UICONTROL DAM Update Asset], klikt u op [!UICONTROL Start]en klik op [!UICONTROL Proceed].
   * Selecteer een element en klik op [!UICONTROL Create] > [!UICONTROL Workflow] op de werkbalk. Selecteer in het pop-updialoogvenster de optie [!UICONTROL DAM Update Asset] workflow, klik op [!UICONTROL Start]en klik op [!UICONTROL Proceed].

Met name voor Microsoft Word-documenten voert u de opdracht **[!UICONTROL DAM Parse Word Documents]** workflow. Het genereert een `cq:Page` uit de inhoud van het Microsoft Word-document. Er wordt verwezen naar de afbeeldingen die uit het document zijn geëxtraheerd. `cq:Page` component. Deze afbeeldingen worden geëxtraheerd, zelfs als het genereren van subelementen is uitgeschakeld.

>[!NOTE]
>
>In de [!UICONTROL Create Sub Asset Process - Step Properties] in [!UICONTROL Process Arguments], kunt u het aantal subelementen opgeven dat [!DNL Experience Manager] wordt gegenereerd. De standaardwaarde is 5. Laat het veld leeg als u alle subelementen wilt genereren. Als het veld een negatief veld heeft, worden geen subactiva gegenereerd.

## Subelementen weergeven {#viewing-subassets}

De subelementen worden alleen weergegeven als de subelementen zijn gegenereerd en beschikbaar zijn voor het geselecteerde element met meerdere pagina&#39;s. Open het element met meerdere pagina&#39;s om de gegenereerde subelementen weer te geven. Klik in de linkerbovenhoek van de pagina op ![Optie voor het openen van het linkerspoor](assets/do-not-localize/aem_leftrail_contentonly.png) en klik op **[!UICONTROL Subassets]** in de lijst. Wanneer u **[!UICONTROL Subassets]** in de lijst. U kunt ook de sneltoets gebruiken `alt + 5`.

![Subelementen weergeven voor elementen die uit meerdere pagina&#39;s bestaan](assets/view_subassets_simulation.gif)

## Pagina&#39;s van een bestand met meerdere pagina&#39;s weergeven {#view-pages-of-a-multi-page-file}

U kunt een bestand met meerdere pagina&#39;s, zoals PDF, INDD, PPT, PPTX en AI, weergeven met de functie Paginaviewer van [!DNL Experience Manager Assets]. Een element met meerdere pagina&#39;s openen en klikken **[!UICONTROL View Pages]** linksboven op de pagina. In de Paginaviewer die wordt geopend, worden de pagina&#39;s van het element en de besturingselementen weergegeven waarmee u door elke pagina kunt bladeren en erop kunt inzoomen.

![Pagina&#39;s van elementen met meerdere pagina&#39;s weergeven en bekijken](assets/view_multipage_asset_fmr.gif)

Voor [!DNL InDesign]kunt u pagina&#39;s uitnemen met [!DNL InDesign Server]. Als de voorvertoningen van pagina&#39;s worden opgeslagen tijdens [!DNL InDesign] bestanden maken en vervolgens [!DNL InDesign Server] is niet vereist voor het uitnemen van pagina&#39;s.

De volgende opties zijn beschikbaar in de werkbalk, in de linkerrails en in de besturingselementen voor de Paginaviewer:

* **[!UICONTROL Desktop Actions]** om een specifiek subelement te openen of te tonen met [!DNL Experience Manager] bureaubladtoepassing. Zie hoe te [Desktophandelingen configureren](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#desktopactions-v2) als u [!DNL Experience Manager] bureaubladtoepassing.

* **[!UICONTROL Properties]** wordt geopend [!UICONTROL Properties] pagina van het specifieke subelement.

* **[!UICONTROL Annotate]** kunt u het specifieke subelement annoteren. De annotaties die u op afzonderlijke subelementen gebruikt, worden samen verzameld en weergegeven wanneer het bovenliggende element wordt geopend voor weergave.

* **[!UICONTROL Page Overview]** worden alle subelementen tegelijkertijd weergegeven.

* **[!UICONTROL Timeline]** optie van de linkerspoorstaaf na het klikken ![Optie voor het openen van het linkerspoor](assets/do-not-localize/aem_leftrail_contentonly.png) geeft de activiteitsstroom voor het bestand weer.

## Beste werkwijzen en beperking {#best-practice-limitation-tips}

* Het genereren van subelementen kan op elke [!DNL Experience Manager] implementatie. Als u subassets genereert wanneer complexe elementen worden geüpload, voegt u de stap toe in de DAM-workflow voor het bijwerken van middelen. Als u op verzoek subassets genereert, maakt u een aparte workflow om subassets te genereren. Met een specifieke workflow kunt u de andere stappen in de DAM-workflow voor het bijwerken van middelen overslaan en computerbronnen opslaan.

>[!MORELIKETHIS]
>
>* [Adobe Experience Manager-bureaubladtoepassing gebruiken](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html)
>* [Bureaubladhandelingen configureren in Adobe Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#desktopactions-v2)
>* [Gekoppelde slimme objecten maken in Adobe Photoshop](https://helpx.adobe.com/photoshop/using/create-smart-objects.html#create-linked-smart-objects)
>* [Afbeeldingen plaatsen in Adobe InDesign](https://helpx.adobe.com/indesign/using/placing-graphics.html)
