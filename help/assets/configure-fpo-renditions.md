---
title: Uitvoeringen alleen voor plaatsing genereren voor Adobe InDesign
description: Genereer FPO-uitvoeringen van nieuwe en bestaande elementen met behulp van de workflow voor Experience Manager Assets en ImageMagick.
contentOwner: Vishabh Gupta
role: Admin
feature: Uitvoeringen
exl-id: null
source-git-commit: 865370e38368072c39ad337eb52259c586403efb
workflow-type: tm+mt
source-wordcount: '979'
ht-degree: 0%

---

# Uitvoeringen alleen voor plaatsing genereren voor Adobe InDesign {#fpo-renditions}

Bij het plaatsen van grote activa van Experience Manager in Adobe InDesign documenten, moet een creatieve beroeps op een aanzienlijke tijd wachten nadat zij [een activa ](https://helpx.adobe.com/indesign/using/placing-graphics.html) plaatsen. Ondertussen wordt de gebruiker verhinderd InDesign te gebruiken. Dit onderbreekt de creatieve stroom en beïnvloedt de gebruikerservaring negatief. Met Adobe kunt u tijdelijk kleine uitvoeringen in InDesign-documenten plaatsen, zodat deze beginnen. Wanneer de uiteindelijke uitvoer vereist is, bijvoorbeeld voor drukwerk- en publicatieworkflows, vervangen de oorspronkelijke elementen met volledige resolutie de tijdelijke uitvoering op de achtergrond. Deze asynchrone update op de achtergrond versnelt het ontwerpproces om de productiviteit te verbeteren en belemmert het creatieve proces niet.

Adobe Experience Manager (AEM) biedt uitvoeringen die alleen voor plaatsing worden gebruikt (FPO). Deze FPO-uitvoeringen hebben een kleine bestandsgrootte maar hebben dezelfde hoogte-breedteverhouding. Als een FPO-uitvoering niet beschikbaar is voor een element, gebruikt Adobe InDesign in plaats daarvan het oorspronkelijke element. Dit fallback-mechanisme zorgt ervoor dat de creatieve workflow zonder onderbrekingen doorgaat.

## Benadering voor het genereren van FPO-uitvoeringen {#approach-to-generate-fpo-renditions}

Met Experience Manager kunnen veel methoden afbeeldingen verwerken die kunnen worden gebruikt om de FPO-uitvoeringen te genereren. De twee gemeenschappelijkste methodes moeten in-gebouwde werkschema&#39;s van de Experience Manager gebruiken en ImageMagick gebruiken. Met behulp van deze twee methoden configureert u het genereren van vertoningen van nieuw geüploade elementen en van de elementen die in de Experience Manager aanwezig zijn.

U kunt ImageMagick gebruiken om afbeeldingen te verwerken, inclusief om FPO-uitvoeringen te genereren. Dergelijke vertoningen worden gedownsampled, dat wil zeggen, de pixelafmetingen van de vertoning worden proportioneel verminderd als de oorspronkelijke afbeelding een PPI heeft die groter is dan 72. Zie [ImageMagick installeren en configureren om te werken met Experience Manager Assets](best-practices-for-imagemagick.md).

|  | De ingebouwde workflow van de Experience Manager gebruiken | De ImageMagick-workflow gebruiken | Opmerkingen |
|— |— |—|— |
| Nieuwe activa | FPO-uitvoering inschakelen ([help](#generate-renditions-of-new-assets-using-aem-workflow)) | ImageMagick-opdrachtregel toevoegen in Experience Manager-workflow ([help](#generate-renditions-of-new-assets-using-imagemagick)) | Experience Manager voert de DAM Update Assets-workflow uit voor elke upload. |
| Voor bestaande activa | FPO-uitvoering inschakelen in een nieuwe, toegewijde workflow voor Experience Managers ([help](#generate-renditions-of-existing-assets-using-aem-workflow)) | ImageMagick-opdrachtregel toevoegen aan een nieuwe, toegewijde workflow voor Experience Managers ([help](#generate-renditions-of-existing-assets-using-imagemagick)) | FPO-uitvoeringen van de bestaande activa kunnen op aanvraag of in bulk worden gecreëerd. |

>[!CAUTION]
>
>Maak de workflows om uitvoeringen te genereren door een kopie van de standaardworkflows te wijzigen. Het verhindert uw veranderingen worden beschreven wanneer de Experience Manager wordt bijgewerkt, bijvoorbeeld door een nieuw de dienstpak te installeren.

## Uitvoeringen van nieuwe elementen genereren met de workflow Experience Manager {#generate-renditions-of-new-assets-using-aem-workflow}

Hier volgen de stappen voor het configureren van het workflowmodel voor DAM Update Asset om het genereren van vertoningen mogelijk te maken:

1. Klik op **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**. Selecteer **[!UICONTROL DAM Update Asset]** model en klik **[!UICONTROL Edit]**.

1. Selecteer **[!UICONTROL Process Thumbnails]** stap en klik **[!UICONTROL Configure]**.

1. Klik op het tabblad **[!UICONTROL FPO Rendition]**. Selecteer **[!UICONTROL Enable FPO rendition creation]**.

   ![fpo_rendition_damupdateasset_model](assets/fpo_rendition_damupdateasset_model.png)

1. Pas **[!UICONTROL Quality]** aan en voeg of wijzig **[!UICONTROL Format List]** waarden toe zoals vereist. Standaard wordt de lijst met MIME-typen die de FPO-uitvoering moet genereren ingesteld op pjpeg, jpeg, jpg, gif, png, x-png en tiff. Klik op **[!UICONTROL Done]**.

   >[!NOTE]
   >
   >Uitvoering wordt ondersteund voor bestandstypen JPEG, GIF, PNG, TIFF, PSD en BMP.

1. Klik op **[!UICONTROL Sync]** om de wijzigingen te activeren.

>[!NOTE]
>
>Afbeeldingen die aan één zijde groter zijn dan 1280 pixels, behouden de pixelafmetingen in de FPO-uitvoering niet.

## Renditions of new assets genereren met ImageMagick {#generate-renditions-of-new-assets-using-imagemagick}

In Experience Manager wordt de DAM Update Asset-workflow uitgevoerd wanneer een nieuw element wordt geüpload. Als u ImageMagick wilt gebruiken om uitvoeringen van nieuw geüploade elementen te verwerken, voegt u een nieuwe opdracht toe aan het workflowmodel.

1. Klik op **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**. Selecteer **[!UICONTROL DAM Update Asset]** model en klik **[!UICONTROL Edit]**.

1. Klik **[!UICONTROL Toggle Side Panel]** in de hogere linkerhoek. Ga naar opdrachtregelstap.

1. Sleep de stap **[!UICONTROL Command Line]** en voeg deze voor de stap **[!UICONTROL Process Thumbnails]** toe.

1. Selecteer **[!UICONTROL Command Line]** stap en klik **[!UICONTROL Configure]**.

1. Voeg de gewenste informatie toe als aangepast **[!UICONTROL Title]** en **[!UICONTROL Description]**. Bijvoorbeeld, FPO vertoning (aangedreven door ImageMagick).

1. Voeg op het tabblad **[!UICONTROL Arguments]** de relevante **[!UICONTROL Mime Types]** toe voor een lijst met bestandsindelingen waarop de opdracht van toepassing is.

   ![imagemagick-mimetype](assets/imagemagick-mimetype.png)

1. Voeg op het tabblad **[!UICONTROL Arguments]** in de sectie **[!UICONTROL Commands]** een relevante opdracht ImageMagick toe om FPO-uitvoeringen te genereren.

   Hieronder ziet u een voorbeeld-opdracht waarmee FPO-uitvoeringen in JPEG-indeling worden gegenereerd, gedownsampled naar 72 PPI bij een kwaliteitsinstelling van 10% en Adobe Photoshop-bestanden met meerdere lagen worden afgehandeld door de uitvoer af te vlakken:

   `convert -quality 10% -units PixelsPerInch ${filename} -resample 72 -flatten cq5dam.fpo.jpeg`

1. Klik op **[!UICONTROL Sync]** om de wijzigingen te activeren.

Zie [https://imagemagick.org](https://imagemagick.org) voor gedetailleerde informatie over de mogelijkheden van de ImageMagick-opdrachtregel.

## Uitvoeringen van bestaande elementen genereren met de workflow Experience Manager {#generate-renditions-of-existing-assets-using-aem-workflow}

Als u een Experience Manager-workflow wilt gebruiken om FPO-uitvoering van de bestaande elementen te genereren, maakt u een speciaal workflowmodel dat gebruikmaakt van de ingebouwde FPO-uitvoeringsoptie.

1. Klik op **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**. Als u een model wilt maken, klikt u op **[!UICONTROL Create]** > **[!UICONTROL Create Model]**. Voeg een betekenisvolle **[!UICONTROL Title]** en een **[!UICONTROL Name]** toe.

1. Selecteer het model en klik **[!UICONTROL Edit]**. Klik op **[!UICONTROL Page Information]** > **[!UICONTROL Open Properties]**. Selecteer **[!UICONTROL Transient Workflow]**. Dit verbetert de schaalbaarheid en prestaties. Klik op **[!UICONTROL Save]** en **[!UICONTROL Close]**.

1. Klik **[!UICONTROL Toggle Side Panel]** in de hogere linkerhoek. Zoek naar de stap van de procesduimnagel. Sleep de stap **[!UICONTROL Process Thumbnails]**.

1. Selecteer **[!UICONTROL Process Thumbnails]** en klik **[!UICONTROL Configure]**. Volg de [configuratie om vertoning van nieuwe activa te produceren gebruikend het werkschema van de Experience Manager](#generate-renditions-of-new-assets-using-aem-workflow). Klik op **[!UICONTROL Sync]** om de wijzigingen te activeren.


## Rendities van bestaande elementen genereren met ImageMagick {#generate-renditions-of-existing-assets-using-imagemagick}

Om ImageMagick verwerkingsmogelijkheden te gebruiken om vertoning FPO van de bestaande activa te produceren, creeer een specifiek werkschemamodel dat de ImageMagick bevellijn gebruikt om dit te doen.

1. Volg stap 1 tot stap 3 van [configuratie om vertoning van bestaande activa te produceren gebruikend de werkschema van de Experience Manager](#generate-renditions-of-existing-assets-using-aem-workflow) sectie.

1. Volg stap 4 tot stap 8 van [configuratie om vertoning van nieuwe activa te produceren gebruikend ImageMagick](#generate-renditions-of-new-assets-using-imagemagick) sectie.


## FPO-uitvoeringen weergeven {#view-fpo-renditions}

U kunt de gegenereerde FPO-uitvoeringen controleren nadat de workflow is voltooid. Klik in de gebruikersinterface Experience Manager Assets op het element om een grote voorvertoning te openen. Open het linkerspoor en selecteer Vertoningen. U kunt ook de sneltoets `Alt + 3` gebruiken wanneer de voorvertoning is geopend.

Klik **[!UICONTROL FPO rendition]** om zijn voorproef te laden. U kunt ook met de rechtermuisknop op de vertoning klikken en deze opslaan in uw bestandssysteem.

![rendition_list](assets/rendition_list.png)


## Tips en beperkingen {#tips-limitations}

* Om op beeldMagick-Gebaseerde configuratie te gebruiken, installeer ImageMagick op de zelfde machine zoals Experience Manager.
* Om FPO vertoningen van vele activa of van de volledige bewaarplaats te produceren, plan en voer de werkschema&#39;s tijdens laag-verkeersduur uit. Het genereren van FPO-uitvoeringen voor een groot aantal elementen is een activiteit die veel resources vereist en de Experience Manager-servers moeten over voldoende verwerkingskracht en geheugen beschikken.
* Voor prestaties en schaalbaarheid, zie [Fine-tune ImageMagick](performance-tuning-guidelines.md).
* Zie [opdrachtregelhandler om elementen te verwerken](media-handlers.md) voor algemene opdrachtregelafhandeling van elementen.