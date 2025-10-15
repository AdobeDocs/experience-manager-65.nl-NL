---
title: Uitvoeringen alleen voor plaatsing genereren voor Adobe InDesign
description: Genereer FPO-uitvoeringen van nieuwe en bestaande elementen met gebruik van de Experience Manager Assets-workflow en ImageMagick.
contentOwner: Vishabh Gupta
role: Admin
feature: Renditions
exl-id: 1e4ddd73-a31c-4ddd-94eb-1dac6a4835b3
hide: true
solution: Experience Manager, Experience Manager Assets
source-git-commit: f8588ef353bd08b41202350072728d80ee51f565
workflow-type: tm+mt
source-wordcount: '990'
ht-degree: 1%

---

# Uitvoeringen alleen voor plaatsing genereren voor Adobe InDesign {#fpo-renditions}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [&#x200B; klik hier &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/admin/configure-fpo-renditions.html?lang=en) |
| AEM 6.5 | Dit artikel |

Wanneer het plaatsen van grote activa van Experience Manager in de documenten van Adobe InDesign, moet een creatieve beroeps op een aanzienlijke tijd wachten nadat zij [&#x200B; activa &#x200B;](https://helpx.adobe.com/indesign/using/placing-graphics.html) plaatsen. Ondertussen kan de gebruiker geen InDesign gebruiken. Dit onderbreekt de creatieve stroom en beïnvloedt de gebruikerservaring negatief. Met Adobe kunt u tijdelijk kleine uitvoeringen plaatsen in InDesign-documenten om mee te beginnen. Wanneer de uiteindelijke uitvoer vereist is, bijvoorbeeld voor drukwerk- en publicatieworkflows, vervangen de oorspronkelijke elementen met volledige resolutie de tijdelijke uitvoering op de achtergrond. Deze asynchrone update op de achtergrond versnelt het ontwerpproces om de productiviteit te verhogen en belemmert het creatieve proces niet.

Adobe Experience Manager (AEM) biedt uitvoeringen die alleen voor plaatsing worden gebruikt (FPO). Deze FPO-uitvoeringen hebben een kleine bestandsgrootte maar hebben dezelfde hoogte-breedteverhouding. Als een FPO-uitvoering niet beschikbaar is voor een element, gebruikt Adobe InDesign in plaats daarvan het oorspronkelijke element. Dit fallback-mechanisme zorgt ervoor dat de creatieve workflow zonder onderbrekingen doorgaat.

## Benadering voor het genereren van FPO-uitvoeringen {#approach-to-generate-fpo-renditions}

In Experience Manager kunnen veel methoden afbeeldingen verwerken die kunnen worden gebruikt om de FPO-uitvoeringen te genereren. De twee meest gebruikte methoden zijn het gebruik van ingebouwde Experience Manager-workflows en het gebruik van ImageMagick. Met deze twee methoden configureert u het genereren van vertoningen van nieuw geüploade elementen en van de elementen die in Experience Manager bestaan.

U kunt ImageMagick gebruiken om afbeeldingen te verwerken, inclusief om FPO-uitvoeringen te genereren. Dergelijke vertoningen worden gedownsampled, dat wil zeggen, de pixelafmetingen van de vertoning worden proportioneel verminderd als de oorspronkelijke afbeelding een PPI heeft die groter is dan 72. Zie [&#x200B; installeren en vormen ImageMagick om met Experience Manager Assets &#x200B;](best-practices-for-imagemagick.md) te werken.

|  | De ingebouwde workflow van Experience Manager gebruiken | De ImageMagick-workflow gebruiken | Opmerkingen |
|--- |--- |---|--- |
| Voor nieuwe activa | Laat FPO vertoning toe ([&#x200B; hulp &#x200B;](#generate-renditions-of-new-assets-using-aem-workflow)) | Voeg bevel-lijn ImageMagick in het werkschema van Experience Manager ([&#x200B; hulp &#x200B;](#generate-renditions-of-new-assets-using-imagemagick)) toe | Experience Manager voert de DAM Update Assets-workflow uit voor elke upload. |
| Voor bestaande activa | Laat FPO vertoning in een nieuw, specifiek werkschema van Experience Manager toe ([&#x200B; hulp &#x200B;](#generate-renditions-of-existing-assets-using-aem-workflow)) | Voeg bevel-lijn ImageMagick in een nieuw, specifiek werkschema van Experience Manager ([&#x200B; hulp &#x200B;](#generate-renditions-of-existing-assets-using-imagemagick)) toe | FPO-uitvoeringen van de bestaande activa kunnen op aanvraag of in bulk worden gemaakt. |

>[!CAUTION]
>
>Maak de workflows om uitvoeringen te genereren door een kopie van de standaardworkflows te wijzigen. Zo voorkomt u dat uw wijzigingen worden overschreven wanneer Experience Manager wordt bijgewerkt, bijvoorbeeld door een nieuw servicepakket te installeren.

## Uitvoeringen van nieuwe elementen genereren met de Experience Manager-workflow {#generate-renditions-of-new-assets-using-aem-workflow}

Hier volgen de stappen voor het configureren van het workflowmodel voor DAM Update Asset om het genereren van vertoningen mogelijk te maken:

1. Klik op **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**. Selecteer **[!UICONTROL DAM Update Asset]** model en klik op **[!UICONTROL Edit]** .

1. Selecteer **[!UICONTROL Process Thumbnails]** -stap en klik op **[!UICONTROL Configure]** .

1. Klik op het tabblad **[!UICONTROL FPO Rendition]**. Selecteer **[!UICONTROL Enable FPO rendition creation]** .

   ![&#x200B; fpo_rendition_damupdateasset_model &#x200B;](assets/fpo_rendition_damupdateasset_model.png)

1. Pas de waarden van **[!UICONTROL Quality]** aan en voeg **[!UICONTROL Format List]** naar wens toe of wijzig deze. Standaard wordt de lijst met MIME-typen die de FPO-uitvoering moet genereren ingesteld op pjpeg, jpeg, jpg, gif, png, x-png en tiff. Klik op **[!UICONTROL Done]**.

   >[!NOTE]
   >
   >Uitvoering wordt ondersteund voor bestandstypen JPEG, GIF, PNG, TIFF, PSD en BMP.

1. Klik op **[!UICONTROL Sync]** om de wijzigingen te activeren.

>[!NOTE]
>
>Afbeeldingen die aan één zijde groter zijn dan 1280 pixels, behouden de pixelafmetingen in de FPO-uitvoering niet.

## Renditions of new assets genereren met ImageMagick {#generate-renditions-of-new-assets-using-imagemagick}

In Experience Manager wordt de DAM-workflow voor het bijwerken van middelen uitgevoerd wanneer een nieuw element wordt geüpload. Als u ImageMagick wilt gebruiken om uitvoeringen van nieuw geüploade elementen te verwerken, voegt u een nieuwe opdracht toe aan het workflowmodel.

1. Klik op **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.

1. Selecteer **[!UICONTROL DAM Update Asset]** model en klik op **[!UICONTROL Edit]** .

1. Klik op **[!UICONTROL Toggle Side Panel]** in de linkerbovenhoek en zoek naar de opdrachtregelstap.

1. Sleep de stap **[!UICONTROL Command Line]** en voeg deze toe vóór de stap **[!UICONTROL Process Thumbnails]** .

1. Selecteer **[!UICONTROL Command Line]** -stap en klik op **[!UICONTROL Configure]** .

1. Voeg de gewenste informatie toe als aangepast **[!UICONTROL Title]** en **[!UICONTROL Description]** . Bijvoorbeeld, FPO vertoning (aangedreven door ImageMagick).

1. Voeg op het tabblad **[!UICONTROL Arguments]** relevante **[!UICONTROL Mime Types]** toe voor een lijst met bestandsindelingen waarop de opdracht van toepassing is.

   ![&#x200B; imagemagick-mimetype &#x200B;](assets/imagemagick-mimetype.png)

1. Voeg op het tabblad **[!UICONTROL Arguments]** in de sectie **[!UICONTROL Commands]** een relevante opdracht ImageMagick toe om FPO-uitvoeringen te genereren.

   Hieronder ziet u een voorbeeldopdracht waarmee FPO-uitvoeringen worden gegenereerd in JPEG-indeling, gedownsampled naar 72 PPI bij een kwaliteitsinstelling van 10% en Adobe Photoshop-bestanden met meerdere lagen worden afgehandeld door de uitvoer af te vlakken:

   `convert -quality 10% -units PixelsPerInch ${filename} -resample 72 -flatten cq5dam.fpo.jpeg`

1. Klik op **[!UICONTROL Sync]** om de wijzigingen te activeren.

Zie `https://imagemagick.org` website voor gedetailleerde informatie over de mogelijkheden van de ImageMagick-opdrachtregel.

## Uitvoeringen van bestaande middelen genereren met Experience Manager-workflow {#generate-renditions-of-existing-assets-using-aem-workflow}

Als u de Experience Manager-workflow wilt gebruiken om FPO-uitvoering van de bestaande elementen te genereren, maakt u een speciaal workflowmodel waarin de ingebouwde FPO-uitvoeroptie wordt gebruikt.

1. Klik op **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.

1. Klik op **[!UICONTROL Create]** > **[!UICONTROL Create Model]** om een model te maken.

1. Voeg een betekenisvolle **[!UICONTROL Title]** en **[!UICONTROL Name]** toe.

1. Selecteer het model en klik op **[!UICONTROL Edit]** . Klik op **[!UICONTROL Page Information]** > **[!UICONTROL Open Properties]** en selecteer vervolgens **[!UICONTROL Transient Workflow]** . Dit verbetert de schaalbaarheid en prestaties.

1. Klik op **[!UICONTROL Save]** en **[!UICONTROL Close]** .

1. Klik op **[!UICONTROL Toggle Side Panel]** in de linkerbovenhoek en zoek naar een stap met een procesminiatuur.

1. Selecteer **[!UICONTROL Process Thumbnails]** en klik op **[!UICONTROL Configure]** . Volg de [&#x200B; configuratie om vertoning van nieuwe activa te produceren gebruikend het werkschema van Experience Manager &#x200B;](#generate-renditions-of-new-assets-using-aem-workflow).

1. Klik op **[!UICONTROL Sync]** om de wijzigingen te activeren.


## Rendities van bestaande elementen genereren met ImageMagick {#generate-renditions-of-existing-assets-using-imagemagick}

Om ImageMagick verwerkingsmogelijkheden te gebruiken om vertoning FPO van de bestaande activa te produceren, creeer een specifiek werkschemamodel dat de ImageMagick bevellijn gebruikt om dit te doen.

1. Volg stap 1 aan stap 3 van [&#x200B; configuratie om vertoning van bestaande activa te produceren gebruikend het werkschema van Experience Manager &#x200B;](#generate-renditions-of-existing-assets-using-aem-workflow) sectie.

1. Volg stap 4 aan stap 8 van [&#x200B; configuratie om vertoning van nieuwe activa te produceren gebruikend &#x200B;](#generate-renditions-of-new-assets-using-imagemagick) sectie ImageMagick.


## FPO-uitvoeringen weergeven {#view-fpo-renditions}

U kunt de gegenereerde FPO-uitvoeringen controleren nadat de workflow is voltooid. Klik in de Experience Manager Assets-gebruikersinterface op het element om een grote voorvertoning te openen. Open het linkerspoor en selecteer Vertoningen. U kunt ook de sneltoets `Alt + 3` gebruiken wanneer de voorvertoning is geopend.

Klik op **[!UICONTROL FPO rendition]** om de voorvertoning te laden. U kunt ook met de rechtermuisknop op de vertoning klikken en deze opslaan in uw bestandssysteem.

![&#x200B; rendition_list &#x200B;](assets/rendition_list.png)


## Tips en beperkingen {#tips-limitations}

* Als u op ImageMagick gebaseerde configuratie wilt gebruiken, installeert u ImageMagick op dezelfde computer als Experience Manager.
* Om FPO vertoningen van vele activa of van de volledige bewaarplaats te produceren, plan en voer de werkschema&#39;s tijdens laag-verkeersduur uit. Het genereren van FPO-uitvoeringen voor een groot aantal middelen is een hulpbronnenintensieve activiteit en de Experience Manager-servers moeten over voldoende verwerkingskracht en geheugen beschikken.
* Voor prestaties en scalability, zie [&#x200B; Fine-tune ImageMagick &#x200B;](performance-tuning-guidelines.md).
* Voor generische bevellijn behandeling van activa, zie [&#x200B; manager van de bevellijn om activa &#x200B;](media-handlers.md) te verwerken.
