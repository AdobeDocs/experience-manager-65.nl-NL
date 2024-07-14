---
title: PDF-rasterfunctie gebruiken om uitvoeringen te genereren
description: U kunt miniaturen en uitvoeringen van hoge kwaliteit genereren met de Adobe PDF Rasterizer-bibliotheek.
contentOwner: AG
role: Developer, Admin
feature: Developer Tools,Renditions
exl-id: 6f365d6b-3972-4885-8766-5889e24289f1
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 0%

---

# PDF Rasterizer gebruiken {#using-pdf-rasterizer}

Wanneer u grote, inhoudintensieve PDF- of AI-bestanden uploadt naar [!DNL Adobe Experience Manager Assets] , genereert de standaardbibliotheek mogelijk geen nauwkeurige uitvoer. De PDF Rasterizer-bibliotheek van de Adobe kan een betrouwbaardere en nauwkeurigere uitvoer genereren in vergelijking met de uitvoer uit een standaardbibliotheek. Adobe raadt aan de PDF Rasterizer-bibliotheek te gebruiken voor de volgende scenario&#39;s:

Adobe raadt u aan de PDF Rasterizer-bibliotheek te gebruiken voor het volgende:

* AI-bestanden of PDF-bestanden met veel inhoud.
* AI-bestanden en PDF-bestanden met miniaturen die niet standaard worden gegenereerd.
* AI-bestanden met PMS-kleuren (Pantone Matching System).

Miniaturen en voorvertoningen die worden gegenereerd met de PDF Rasterizer, zijn beter in kwaliteit dan uitvoer vanuit de doos en bieden daarom een consistente kijkervaring op verschillende apparaten. De Adobe PDF Rasterizer-bibliotheek ondersteunt geen kleurruimteconversie. De uitvoer wordt altijd naar RGB uitgevoerd, ongeacht de kleurruimte van het bronbestand.

1. Installeer het pakket van Rasterizer van de PDF op uw [!DNL Adobe Experience Manager] plaatsing van [ de Distributie van de Software ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/product/assets/aem-assets-pdf-rasterizer-pkg-4.6.zip).

   >[!NOTE]
   >
   >De PDF Rasterizer-bibliotheek is alleen beschikbaar voor Windows en Linux®.

1. Open de [!DNL Assets] workflowconsole op `https://[aem_server]:[port]/workflow` . Open de [!UICONTROL DAM Update Asset] -workflow.

1. Ga als volgt te werk om te voorkomen dat de standaardmethoden worden gebruikt voor het genereren van miniaturen en webvertoningen voor PDF- en AI-bestanden:

   * Open de stap **[!UICONTROL Process Thumbnails]** en voeg `application/pdf` of `application/postscript` toe in het veld **[!UICONTROL Skip Mime Types]** onder het tabblad **[!UICONTROL Thumbnails]** .

   ![ skip_mime_types-2 ](assets/skip_mime_types-2.png)

   * Voeg `application/pdf` of `application/postscript` onder **[!UICONTROL Skip List]** toe op het tabblad **[!UICONTROL Web Enabled Image]** , afhankelijk van uw vereisten.

   ![ Configuratie om duimnagelverwerking voor een beeldformaat over te slaan ](assets/web_enabled_imageskiplist.png)

1. Open de stap **[!UICONTROL Rasterize PDF/AI Image Preview Rendition]** en verwijder het MIME-type waarvoor u de standaardgeneratie van voorvertoningsafbeeldingsuitvoeringen wilt overslaan. Verwijder bijvoorbeeld het MIME-type `application/pdf` , `application/postscript` of `application/illustrator` uit de lijst **[!UICONTROL MIME Types]** .

   ![ process_arguments ](assets/process_arguments.png)

1. Sleep de stap **[!UICONTROL PDF Rasterizer Handler]** van het zijpaneel naar onder de stap **[!UICONTROL Process Thumbnails]** .
1. Configureer de volgende argumenten voor de stap **[!UICONTROL PDF Rasterizer Handler]** :

   * MIME-typen: `application/pdf` of `application/postscript`
   * Opdrachten: `PDFRasterizer -d -s 1280 -t PNG -i ${file}`
   * Miniatuurgrootten toevoegen: 319:319, 140:100, 48:48. Voeg indien nodig aangepaste miniatuurconfiguratie toe.

   De opdrachtregelargumenten voor de opdracht `PDFRasterizer` kunnen het volgende bevatten:

   * `-d`: markering voor een vloeiende weergave van tekst, vectorillustraties en afbeeldingen. Hiermee maakt u afbeeldingen van betere kwaliteit. Het opnemen van deze parameter zorgt er echter voor dat de opdracht langzaam wordt uitgevoerd en dat de afbeeldingen groter worden.

   * `-s`: maximale afbeeldingsafmetingen (hoogte of breedte). Deze wordt voor elke pagina geconverteerd naar DPI. Als de pagina&#39;s van verschillende grootte zijn, kan elke pagina potentieel met verschillende hoeveelheid schalen. De standaardinstelling is het daadwerkelijke paginaformaat.

   * `-t`: type uitvoerafbeelding. Geldige typen zijn JPEG, PNG, GIF en BMP. De standaardwaarde is JPEG.

   * `-i`: pad voor invoer PDF. Het is een verplichte parameter.

   * `-h`: Help

1. Selecteer **[!UICONTROL Delete Generated Rendition]** als u tussenliggende vertoningen wilt verwijderen.
1. Als u wilt dat PDF Rasterizer webuitvoeringen genereert, selecteert u **[!UICONTROL Generate Web Rendition]** .

   ![ generate_web_renditions1 ](assets/generate_web_renditions1.png)

1. Geef de instellingen op op het tabblad **[!UICONTROL Web Enabled Image]** .

   ![ web_enabled_image1 ](assets/web_enabled_image1.png)

1. Sla de workflow op.
1. Als u wilt dat PDF Rasterizer PDF-pagina&#39;s kan verwerken met PDF-bibliotheken, opent u het **[!UICONTROL DAM Process Subasset]** -model via de [!UICONTROL Workflow] -console.
1. Sleep vanuit het zijpaneel de stap PDF Rasterizer Handler onder de stap **[!UICONTROL Create Web-Enabled Image Rendition]** .
1. Configureer de volgende argumenten voor de stap **[!UICONTROL PDF Rasterizer Handler]** :

   * MIME-typen: `application/pdf` of `application/postscript`
   * Opdrachten: `PDFRasterizer -d -s 1280 -t PNG -i ${file}`
   * Miniatuurgrootten toevoegen: `319:319`, `140:100`, `48:48` . Voeg desgewenst aangepaste miniatuurconfiguratie toe.

   De opdrachtregelargumenten voor de opdracht `PDFRasterizer` kunnen het volgende bevatten:

   * `-d`: markering voor een vloeiende weergave van tekst, vectorillustraties en afbeeldingen. Hiermee maakt u afbeeldingen van betere kwaliteit. Het opnemen van deze parameter zorgt er echter voor dat de opdracht langzaam wordt uitgevoerd en dat de afbeeldingen groter worden.

   * `-s`: maximale afbeeldingsafmetingen (hoogte of breedte). Deze wordt voor elke pagina geconverteerd naar DPI. Als de pagina&#39;s van verschillende grootte zijn, kan elke pagina potentieel met verschillende hoeveelheid schalen. De standaardinstelling is het daadwerkelijke paginaformaat.

   * `-t`: type uitvoerafbeelding. Geldige typen zijn JPEG, PNG, GIF en BMP. De standaardwaarde is JPEG.

   * `-i`: pad voor invoer PDF. Het is een verplichte parameter.

   * `-h`: Help

1. Selecteer **[!UICONTROL Delete Generated Rendition]** als u tussenliggende vertoningen wilt verwijderen.
1. Als u wilt dat PDF Rasterizer webuitvoeringen genereert, selecteert u **[!UICONTROL Generate Web Rendition]** .

   ![ generate_web_renditions ](assets/generate_web_renditions.png)

1. Geef de instellingen op op het tabblad **[!UICONTROL Web Enabled Image]** .

   ![ web_enabled_image-1 ](assets/web_enabled_image-1.png)

1. Sla de workflow op.
1. Upload een PDF-bestand of een AI-bestand naar [!DNL Experience Manager Assets] . In de Rasterizer-PDF worden de miniaturen en webrengingen voor het bestand gegenereerd.
