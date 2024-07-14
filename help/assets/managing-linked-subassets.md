---
title: Samengestelde elementen beheren met verwijzingen en meerdere pagina's
description: Leer hoe te om verwijzingen naar digitale activa van binnen  [!DNL Adobe InDesign] tot stand te brengen,  [!DNL Adobe Illustrator], en  [!DNL Adobe Photoshop]. Met de functie Paginaviewer kunt u afzonderlijke subelementpagina's van bestanden met meerdere pagina's weergeven, zoals PDF-, INDD-, PPT-, PPTX- en AI-bestanden.
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

[!DNL Adobe Experience Manager Assets] kan bepalen of een geüpload bestand verwijzingen bevat naar elementen die al in de opslagplaats bestaan. Deze functie is alleen beschikbaar voor ondersteunde bestandsindelingen. Als het geüploade element verwijzingen naar [!DNL Experience Manager] -elementen bevat, wordt een tweerichtingskoppeling gemaakt tussen de geüploade en de waarnaar wordt verwezen.

Naast het elimineren van overtolligheid, verbetert het verwijzen van naar de activa in [!DNL Adobe Creative Cloud] toepassingen de samenwerking en verhoogt de efficiency en de productiviteit van gebruikers.

[!DNL Experience Manager Assets] ondersteunt bidirectioneel verwijzen. U vindt de middelen waarnaar wordt verwezen op de elementdetailpagina van het geüploade bestand. Daarnaast kunt u de bestanden waarnaar wordt verwezen, weergeven op de pagina met elementdetails van het element waarnaar wordt verwezen.

Verwijzingen worden opgelost op basis van pad, document-id en instantie-id van de middelen waarnaar wordt verwezen.

## [!DNL Adobe Illustrator]: digitale elementen toevoegen als verwijzingen {#refai}

U kunt vanuit een [!DNL Adobe Illustrator] -bestand verwijzen naar bestaande digitale elementen.

1. Gebruikend [[!DNL Experience Manager]  Desktop app ](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html), haal de digitale activa op het lokale filesystem. Navigeer naar de bestandssysteemlocatie van het element waarnaar u wilt verwijzen.
1. Sleep het element van de lokale map naar het [!DNL Illustrator] -bestand.

1. Sparen het [!DNL Illustrator] dossier aan de opgezette aandrijving, of [ uploadt ](/help/assets/manage-assets.md#uploading-assets) aan de [!DNL Experience Manager] bewaarplaats.

1. Nadat de workflow is voltooid, gaat u naar de pagina met elementdetails voor het element. De verwijzingen naar bestaande digitale elementen staan onder **[!UICONTROL Dependencies]** in de kolom **[!UICONTROL References]** .

   ![ chlimage_1-84 ](assets/chlimage_1-258.png)

1. De middelen waarnaar wordt verwezen die onder **[!UICONTROL Dependencies]** worden weergegeven, kunnen ook worden verwezen door andere bestanden dan de huidige. Als u een lijst wilt weergeven met bestanden die verwijzen naar een element, klikt u op het element onder **[!UICONTROL Dependencies]** .

   ![ chlimage_1-85 ](assets/chlimage_1-259.png)

1. Klik op **[!UICONTROL View Properties]** op de werkbalk. Op de pagina [!UICONTROL Properties] wordt de lijst met bestanden die naar het huidige element verwijzen, weergegeven onder de kolom **[!UICONTROL References]** op het tabblad **[!UICONTROL Basic]** .

   ![ mening de verwijzingen van Experience Manager Assets in de kolom van Verwijzingen in activadetails ](assets/asset-references.png)

   *Cijfer: De verwijzingen van activa in activa details.*

## [!DNL Adobe InDesign]: digitale elementen toevoegen als verwijzingen {#add-aem-assets-as-references-in-adobe-indesign}

Als u vanuit een [!DNL InDesign] -bestand wilt verwijzen naar digitale elementen, sleept u elementen naar het [!DNL InDesign] -bestand of exporteert u het [!DNL InDesign] -bestand als een ZIP-archief.

Elementen waarnaar wordt verwezen, bestaan al in [!DNL Experience Manager Assets] . U kunt subassets halen door [ vormend InDesign Server ](indesign.md). Ingesloten elementen in een [!DNL InDesign] -bestand worden geëxtraheerd als subelementen.

>[!NOTE]
>
>Als de [!DNL InDesign Server] proxy is, is de voorvertoning van [!DNL InDesign] -bestanden ingesloten in de XMP metagegevens. In dit geval is het niet expliciet vereist miniatuurextractie uit te voeren. Als [!DNL InDesign Server] echter geen proxy is, moeten miniaturen expliciet worden geëxtraheerd voor [!DNL InDesign] -bestanden.

Wanneer een INDD-bestand wordt geüpload, worden de verwijzingen opgehaald door te zoeken naar elementen met de eigenschappen `xmpMM:InstanceID` en `xmpMM:DocumentID` in de opslagplaats.

### Verwijzingen maken door elementen te slepen {#create-references-by-dragging-aem-assets}

Deze procedure is gelijkaardig aan [ voeg digitale activa als verwijzingen in Adobe Illustrator ](#refai) toe.

### Verwijzingen naar elementen maken door een ZIP-bestand te exporteren {#create-references-to-aem-assets-by-exporting-a-zip-file}

1. Voer de stappen in [ uit creeer werkschemamodellen ](/help/sites-developing/workflows-models.md) om een werkschema tot stand te brengen.
1. Gebruik de [ eigenschap van het Pakket ](https://helpx.adobe.com/indesign/how-to/indesign-package-files-for-handoff.html) van [!DNL Adobe InDesign] om het document uit te voeren. [!DNL Adobe InDesign] kan een document en de gekoppelde elementen als een pakket exporteren. In dit geval bevat de geëxporteerde map een `Links` -map die submiddelen in het [!DNL InDesign] -bestand bevat. De map `Links` bevindt zich in dezelfde map als het INDD-bestand.
1. Maak een ZIP-bestand en upload het bestand naar de [!DNL Experience Manager] -opslagplaats.
1. Start de `Unarchiver` -workflow.
1. Wanneer de werkstroom is voltooid, wordt er automatisch naar de verwijzingen in de map Koppelingen verwezen als subelementen. Om een lijst van genoemde activa te bekijken, navigeer aan de pagina van activadetails van het [!DNL InDesign] activa en sluit [ Spoorweg ](/help/sites-authoring/basic-handling.md#rail-selector).

## [!DNL Adobe Photoshop]: digitale elementen toevoegen als verwijzingen {#refps}

1. Gebruik de bureaubladtoepassing [!DNL Experience Manager] om [!DNL Experience Manager Assets] te openen. Download de bestanden en open ze op het lokale bestandssysteem. Gebruik de functie [!UICONTROL Place Linked] in [!DNL Adobe Photoshop] . Zie [ plaatselementen in Desktop app ](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#place-assets-in-native-documents).

1. Sparen in [!DNL Photoshop] dossier aan de opgezette aandrijving of [ uploadt ](/help/assets/manage-assets.md#uploading-assets) aan de [!DNL Experience Manager] bewaarplaats.
1. Nadat de workflow is voltooid, worden de verwijzingen naar bestaande [!DNL Experience Manager] -elementen weergegeven op de pagina met elementdetails.

   Om de referenced activa te bekijken, sluit het [ Spoorweg ](/help/sites-authoring/basic-handling.md#rail-selector) in de pagina van activadetails.

1. De middelen waarnaar wordt verwezen, bevatten ook de lijst met elementen waarnaar wordt verwezen. Om een lijst van referenced activa te bekijken, navigeer aan de pagina van activadetails en sluit het [ Spoorweg ](/help/sites-authoring/basic-handling.md#rail-selector).

>[!NOTE]
>
>Er kan ook worden verwezen naar de elementen in samengestelde elementen op basis van hun document-id en instantie-id. Deze functionaliteit is alleen beschikbaar in [!DNL Adobe Illustrator] - en [!DNL Adobe Photoshop] -versies. Voor andere toepassingen wordt het verwijzen uitgevoerd op basis van het relatieve pad van gekoppelde elementen in het samengestelde hoofdelement, zoals dat in eerdere versies van [!DNL Experience Manager] is gebeurd.

## Subelementen maken {#generate-subassets}

Voor de ondersteunde elementen met indelingen die uit meerdere pagina&#39;s bestaan (PDF-bestanden, AI-bestanden, [!DNL Microsoft PowerPoint] - en [!DNL Apple Keynote] -bestanden en [!DNL Adobe InDesign] -bestanden), kan [!DNL Experience Manager] subelementen genereren die overeenkomen met elke afzonderlijke pagina van het oorspronkelijke element. Deze subassets zijn verbonden met *ouder* activa en vergemakkelijken multi-page mening. Voor alle andere doeleinden worden de subelementen als normale elementen in [!DNL Experience Manager] behandeld.

Genereren van subelementen wordt standaard uitgeschakeld. Voer de volgende stappen uit om het genereren van subelementen in te schakelen:

1. Meld u aan bij [!DNL Experience Manager] als beheerder. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. Selecteer **[!UICONTROL DAM Update Asset]** workflow en klik op **[!UICONTROL Edit]** .
1. Klik op **[!UICONTROL Toggle Side Panel]** en zoek de stap **[!UICONTROL Create Sub Asset]** . Voeg de stap toe aan de workflow. Klik op **[!UICONTROL Sync]**.

Voer een van de volgende handelingen uit om de subelementen te genereren:

* Nieuwe elementen: de [!UICONTROL DAM Update Assets] -workflow wordt uitgevoerd voor elk nieuw element dat wordt geüpload naar [!DNL Experience Manager] . Subelementen worden automatisch gegenereerd voor nieuwe elementen van meerdere pagina&#39;s.
* Bestaande elementen van meerdere pagina&#39;s: voer handmatig de [!UICONTROL DAM Update Assets] -workflow uit volgens een van de volgende twee stappen:

   * Selecteer een element en klik op [!UICONTROL Timeline] om het linkerdeelvenster te openen. U kunt ook de sneltoets gebruiken `alt + 3` . Klik op [!UICONTROL Start Workflow] , selecteer [!UICONTROL DAM Update Asset] , klik op [!UICONTROL Start] en klik op [!UICONTROL Proceed] .
   * Selecteer een element en klik op [!UICONTROL Create] > [!UICONTROL Workflow] op de werkbalk. Selecteer [!UICONTROL DAM Update Asset] workflow in het pop-updialoogvenster, klik op [!UICONTROL Start] en klik op [!UICONTROL Proceed] .

Met name voor Microsoft Word-documenten voert u de **[!UICONTROL DAM Parse Word Documents]** -workflow uit. Er wordt een `cq:Page` -component gegenereerd op basis van de inhoud van het Microsoft Word-document. Er wordt verwezen naar de afbeeldingen die uit het document zijn geëxtraheerd, uit de component `cq:Page` . Deze afbeeldingen worden geëxtraheerd, zelfs als het genereren van subelementen is uitgeschakeld.

>[!NOTE]
>
>In de lus [!UICONTROL Create Sub Asset Process - Step Properties] in [!UICONTROL Process Arguments] kunt u opgeven hoeveel subelementen [!DNL Experience Manager] genereert. De standaardwaarde is 5. Laat het veld leeg als u alle subelementen wilt genereren. Als het veld een negatief veld heeft, worden geen subactiva gegenereerd.

## Subelementen weergeven {#viewing-subassets}

De subelementen worden alleen weergegeven als de subelementen zijn gegenereerd en beschikbaar zijn voor het geselecteerde element met meerdere pagina&#39;s. Open het element met meerdere pagina&#39;s om de gegenereerde subelementen weer te geven. In het upper-left gebied van de pagina, klik ![ Optie om linkerspoor ](assets/do-not-localize/aem_leftrail_contentonly.png) te openen en **[!UICONTROL Subassets]** van de lijst te klikken. Wanneer u **[!UICONTROL Subassets]** selecteert in de lijst. U kunt ook de sneltoets gebruiken `alt + 5` .

![ subassets van de Mening voor een multi-page activa ](assets/view_subassets_simulation.gif)

## Pagina&#39;s van een bestand met meerdere pagina&#39;s weergeven {#view-pages-of-a-multi-page-file}

U kunt een bestand met meerdere pagina&#39;s, zoals PDF, INDD, PPT, PPTX en AI, weergeven met de functie Paginaviewer van [!DNL Experience Manager Assets] . Open een element met meerdere pagina&#39;s en klik op **[!UICONTROL View Pages]** in de linkerbovenhoek van de pagina. In de Paginaviewer die wordt geopend, worden de pagina&#39;s van het element en de besturingselementen weergegeven waarmee u door elke pagina kunt bladeren en erop kunt inzoomen.

![ Mening en zie pagina&#39;s van een multi-page activa ](assets/view_multipage_asset_fmr.gif)

Voor [!DNL InDesign] kunt u pagina&#39;s uitnemen met [!DNL InDesign Server] . Als de voorvertoningen van pagina&#39;s worden opgeslagen tijdens het maken van [!DNL InDesign] -bestanden, is [!DNL InDesign Server] niet vereist voor het uitnemen van pagina&#39;s.

De volgende opties zijn beschikbaar in de werkbalk, in de linkerrails en in de besturingselementen voor de Paginaviewer:

* **[!UICONTROL Desktop Actions]** gebruiken om een specifiek submiddel te openen of weer te geven met de bureaubladtoepassing van [!DNL Experience Manager] . Zie hoe te [ vormen de Acties van de Desktop ](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#desktopactions-v2) als u [!DNL Experience Manager] Desktop app gebruikt.

* Met de optie **[!UICONTROL Properties]** wordt de pagina [!UICONTROL Properties] van het specifieke subelement geopend.

* Met de optie **[!UICONTROL Annotate]** kunt u het specifieke subelement annoteren. De annotaties die u op afzonderlijke subelementen gebruikt, worden samen verzameld en weergegeven wanneer het bovenliggende element wordt geopend voor weergave.

* Met de optie **[!UICONTROL Page Overview]** worden alle subelementen tegelijkertijd weergegeven.

* **[!UICONTROL Timeline]** optie van het linkerspoor na het klikken ![ Optie om linkerspoor ](assets/do-not-localize/aem_leftrail_contentonly.png) te openen toont de activiteitenstroom voor het dossier.

## Beste werkwijzen en beperking {#best-practice-limitation-tips}

* Bij elke [!DNL Experience Manager] -implementatie kan het genereren van subelementen zeer veel resources vergen. Als u subassets genereert wanneer complexe elementen worden geüpload, voegt u de stap toe in de DAM-workflow voor het bijwerken van middelen. Als u op verzoek subassets genereert, maakt u een aparte workflow om subassets te genereren. Met een specifieke workflow kunt u de andere stappen in de DAM-workflow voor het bijwerken van middelen overslaan en computerbronnen opslaan.

>[!MORELIKETHIS]
>
>* [ Desktop app van Adobe Experience Manager van het Gebruik {](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html)
>* [ vorm de Acties van de Desktop in Adobe Experience Manager ](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#desktopactions-v2)
>* [ creeer Gekoppelde Slimme Voorwerpen in Adobe Photoshop ](https://helpx.adobe.com/photoshop/using/create-smart-objects.html#create-linked-smart-objects)
>* [ grafiek van de Plaats in Adobe InDesign ](https://helpx.adobe.com/indesign/using/placing-graphics.html)
