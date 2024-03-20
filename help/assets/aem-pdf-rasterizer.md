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

Wanneer u grote, inhoudintensieve PDF- of AI-bestanden uploadt naar [!DNL Adobe Experience Manager Assets]In de standaardbibliotheek wordt mogelijk geen nauwkeurige uitvoer gegenereerd. De PDF Rasterizer-bibliotheek van de Adobe kan een betrouwbaardere en nauwkeurigere uitvoer genereren in vergelijking met de uitvoer uit een standaardbibliotheek. Adobe raadt aan de PDF Rasterizer-bibliotheek te gebruiken voor de volgende scenario&#39;s:

Adobe raadt u aan de PDF Rasterizer-bibliotheek te gebruiken voor het volgende:

* AI-bestanden of PDF-bestanden met veel inhoud.
* AI-bestanden en PDF-bestanden met miniaturen die niet standaard worden gegenereerd.
* AI-bestanden met PMS-kleuren (Pantone Matching System).

Miniaturen en voorvertoningen die worden gegenereerd met de PDF Rasterizer, zijn beter in kwaliteit dan uitvoer vanuit de doos en bieden daarom een consistente kijkervaring op verschillende apparaten. De Adobe PDF Rasterizer-bibliotheek ondersteunt geen kleurruimteconversie. De uitvoer wordt altijd naar RGB uitgevoerd, ongeacht de kleurruimte van het bronbestand.

1. Installeer het PDF Rasterizer-pakket op uw [!DNL Adobe Experience Manager] implementatie van [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/product/assets/aem-assets-pdf-rasterizer-pkg-4.6.zip).

   >[!NOTE]
   >
   >De PDF Rasterizer-bibliotheek is alleen beschikbaar voor Windows en Linux®.

1. Toegang krijgen tot de [!DNL Assets] workflowconsole op `https://[aem_server]:[port]/workflow`. Openen [!UICONTROL DAM Update Asset] workflow.

1. Ga als volgt te werk om te voorkomen dat de standaardmethoden worden gebruikt voor het genereren van miniaturen en webvertoningen voor PDF- en AI-bestanden:

   * Open de **[!UICONTROL Process Thumbnails]** stap, en toevoegen `application/pdf` of `application/postscript` in de **[!UICONTROL Skip Mime Types]** onder de **[!UICONTROL Thumbnails]** indien nodig.

   ![skip_mime_types-2](assets/skip_mime_types-2.png)

   * In de **[!UICONTROL Web Enabled Image]** tab, toevoegen `application/pdf` of `application/postscript` krachtens **[!UICONTROL Skip List]** afhankelijk van uw vereisten.

   ![Configuratie om miniatuurverwerking voor een afbeeldingsindeling over te slaan](assets/web_enabled_imageskiplist.png)

1. Open de **[!UICONTROL Rasterize PDF/AI Image Preview Rendition]** en verwijdert u het MIME-type waarvoor u de standaardgeneratie van voorvertoningen van afbeeldingen wilt overslaan. Verwijder bijvoorbeeld het MIME-type `application/pdf`, `application/postscript`, of `application/illustrator` van de **[!UICONTROL MIME Types]** lijst.

   ![process_arguments](assets/process_arguments.png)

1. Sleep de **[!UICONTROL PDF Rasterizer Handler]** stap van het zijpaneel naar onder de **[!UICONTROL Process Thumbnails]** stap.
1. Vorm de volgende argumenten voor de **[!UICONTROL PDF Rasterizer Handler]** stap:

   * MIME-typen: `application/pdf` of `application/postscript`
   * Opdrachten: `PDFRasterizer -d -s 1280 -t PNG -i ${file}`
   * Miniatuurgrootten toevoegen: 319:319, 140:100, 48:48. Voeg indien nodig aangepaste miniatuurconfiguratie toe.

   De opdrachtregelargumenten voor de `PDFRasterizer` kan de volgende opties bevatten:

   * `-d`: Markering om tekst, vectorillustraties en afbeeldingen vloeiend te renderen. Hiermee maakt u afbeeldingen van betere kwaliteit. Het opnemen van deze parameter zorgt er echter voor dat de opdracht langzaam wordt uitgevoerd en dat de afbeeldingen groter worden.

   * `-s`: Maximale afmetingen afbeelding (hoogte of breedte). Deze wordt voor elke pagina geconverteerd naar DPI. Als de pagina&#39;s van verschillende grootte zijn, kan elke pagina potentieel met verschillende hoeveelheid schalen. De standaardinstelling is het daadwerkelijke paginaformaat.

   * `-t`: Type uitvoerafbeelding. Geldige typen zijn JPEG, PNG, GIF en BMP. De standaardwaarde is JPEG.

   * `-i`: Pad voor invoer PDF. Het is een verplichte parameter.

   * `-h`: Help

1. Als u tussenversies wilt verwijderen, selecteert u **[!UICONTROL Delete Generated Rendition]**.
1. Als u PDF Rasterizer webuitvoeringen wilt laten genereren, selecteert u **[!UICONTROL Generate Web Rendition]**.

   ![generate_web_renditions1](assets/generate_web_renditions1.png)

1. Geef de instellingen op in het dialoogvenster **[!UICONTROL Web Enabled Image]** tab.

   ![web_enabled_image1](assets/web_enabled_image1.png)

1. Sla de workflow op.
1. Als u PDF Rasterizer wilt inschakelen voor het verwerken van PDF-pagina&#39;s met PDF-bibliotheken, opent u het dialoogvenster **[!UICONTROL DAM Process Subasset]** model van het [!UICONTROL Workflow] console.
1. Sleep vanuit het zijpaneel de stap PDF Rasterizer Handler onder de knop **[!UICONTROL Create Web-Enabled Image Rendition]** stap.
1. Vorm de volgende argumenten voor de **[!UICONTROL PDF Rasterizer Handler]** stap:

   * MIME-typen: `application/pdf` of `application/postscript`
   * Opdrachten: `PDFRasterizer -d -s 1280 -t PNG -i ${file}`
   * Miniatuurgrootten toevoegen: `319:319`, `140:100`, `48:48`. Voeg desgewenst aangepaste miniatuurconfiguratie toe.

   De opdrachtregelargumenten voor de `PDFRasterizer` kan de volgende opties bevatten:

   * `-d`: Markering om tekst, vectorillustraties en afbeeldingen vloeiend te renderen. Hiermee maakt u afbeeldingen van betere kwaliteit. Het opnemen van deze parameter zorgt er echter voor dat de opdracht langzaam wordt uitgevoerd en dat de afbeeldingen groter worden.

   * `-s`: Maximale afmetingen afbeelding (hoogte of breedte). Deze wordt voor elke pagina geconverteerd naar DPI. Als de pagina&#39;s van verschillende grootte zijn, kan elke pagina potentieel met verschillende hoeveelheid schalen. De standaardinstelling is het daadwerkelijke paginaformaat.

   * `-t`: Type uitvoerafbeelding. Geldige typen zijn JPEG, PNG, GIF en BMP. De standaardwaarde is JPEG.

   * `-i`: Pad voor invoer PDF. Het is een verplichte parameter.

   * `-h`: Help

1. Als u tussenversies wilt verwijderen, selecteert u **[!UICONTROL Delete Generated Rendition]**.
1. Als u PDF Rasterizer webuitvoeringen wilt laten genereren, selecteert u **[!UICONTROL Generate Web Rendition]**.

   ![generate_web_renditions](assets/generate_web_renditions.png)

1. Geef de instellingen op in het dialoogvenster **[!UICONTROL Web Enabled Image]** tab.

   ![web_enabled_image-1](assets/web_enabled_image-1.png)

1. Sla de workflow op.
1. Een PDF-bestand of een AI-bestand uploaden naar [!DNL Experience Manager Assets]. In de Rasterizer-PDF worden de miniaturen en webrengingen voor het bestand gegenereerd.
