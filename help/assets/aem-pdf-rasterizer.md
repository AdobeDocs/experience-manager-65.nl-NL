---
title: PDF-rasterfunctie gebruiken om uitvoeringen te genereren
description: U kunt miniaturen en uitvoeringen van hoge kwaliteit genereren met de Adobe PDF Rasterizer-bibliotheek.
contentOwner: AG
role: Ontwikkelaar, beheerder
translation-type: tm+mt
source-git-commit: 2e734041bdad7332c35ab41215069ee696f786f4
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 0%

---


# PDF-rasterfunctie gebruiken {#using-pdf-rasterizer}

Wanneer u grote, inhoudintensieve PDF- of AI-bestanden uploadt naar [!DNL Adobe Experience Manager Assets], genereert de standaardbibliotheek mogelijk geen nauwkeurige uitvoer. PDF Rasterizer-bibliotheek kan een betrouwbaardere en nauwkeurigere uitvoer genereren in vergelijking met de uitvoer uit een standaardbibliotheek. Adobe raadt u aan de PDF Rasterizer-bibliotheek te gebruiken voor de volgende scenario&#39;s:

Adobe raadt u aan de PDF Rasterizer-bibliotheek te gebruiken voor het volgende:

* AI-bestanden of PDF-bestanden met veel inhoud.
* AI-bestanden en PDF-bestanden met miniaturen die niet standaard worden gegenereerd.
* AI-bestanden met Pantone Matching System (PMS)-kleuren.

Miniaturen en voorvertoningen die worden gegenereerd met PDF Rasterizer, zijn beter in kwaliteit dan uitvoer in de buitenverpakking en bieden daarom een consistente kijkervaring op verschillende apparaten. De Adobe PDF Rasterizer-bibliotheek ondersteunt geen kleurruimteconversie. De uitvoer wordt altijd naar RGB uitgevoerd, ongeacht de kleurruimte van het bronbestand.

1. Installeer het PDF Rasterizer-pakket op de [!DNL Adobe Experience Manager]-implementatie van [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/product/assets/aem-assets-pdf-rasterizer-pkg).

   >[!NOTE]
   >
   >De PDF Rasterizer-bibliotheek is alleen beschikbaar voor Windows en Linux.

1. Open de [!DNL Assets] workflowconsole op `https://[aem_server]:[port]/workflow`. Open [!UICONTROL DAM Update Asset] workflow.

1. Voer de volgende stappen uit om te voorkomen dat de standaardmethoden worden gebruikt voor het genereren van miniaturen en webvertoningen voor PDF- en AI-bestanden:

   * Open de stap **[!UICONTROL Process Thumbnails]** en voeg `application/pdf` of `application/postscript` toe in het veld **[!UICONTROL Skip Mime Types]** onder het tabblad **[!UICONTROL Thumbnails]** indien nodig.

   ![skip_mime_types-2](assets/skip_mime_types-2.png)

   * Voeg op het tabblad **[!UICONTROL Web Enabled Image]** `application/pdf` of `application/postscript` toe onder **[!UICONTROL Skip List]**, afhankelijk van uw vereisten.

   ![Configuratie om de verwerking van miniaturen voor een afbeeldingsindeling over te slaan](assets/web_enabled_imageskiplist.png)

1. Open de stap **[!UICONTROL Rasterize PDF/AI Image Preview Rendition]** en verwijder het MIME-type waarvoor u de standaardgeneratie van voorvertoningsafbeeldingsuitvoeringen wilt overslaan. Verwijder bijvoorbeeld het MIME-type `application/pdf`, `application/postscript` of `application/illustrator` uit de lijst **[!UICONTROL MIME Types]**.

   ![process_arguments](assets/process_arguments.png)

1. Sleep de stap **[!UICONTROL PDF Rasterizer Handler]** van het zijpaneel naar onder de stap **[!UICONTROL Process Thumbnails]**.
1. Configureer de volgende argumenten voor de stap **[!UICONTROL PDF Rasterizer Handler]**:

   * MIME-typen: `application/pdf` of `application/postscript`
   * Opdrachten: `PDFRasterizer -d -s 1280 -t PNG -i ${file}`
   * Miniatuurgrootten toevoegen: 319:319, 140:100, 48:48. Voeg indien nodig aangepaste miniatuurconfiguratie toe.

   De opdrachtregelargumenten voor de opdracht `PDFRasterizer` kunnen het volgende bevatten:

   * `-d`: Vlag om het vloeiend weergeven van tekst, vectorillustraties en afbeeldingen mogelijk te maken. Hiermee maakt u afbeeldingen van betere kwaliteit. Het opnemen van deze parameter zorgt er echter voor dat de opdracht langzaam wordt uitgevoerd en dat de afbeeldingen groter worden.

   * `-s`: Maximale afmetingen afbeelding (hoogte of breedte). Deze wordt voor elke pagina geconverteerd naar DPI. Als de pagina&#39;s van verschillende grootte zijn, kan elke pagina potentieel met verschillende hoeveelheid schalen. De standaardinstelling is het daadwerkelijke paginaformaat.

   * `-t`: Type uitvoerafbeelding. Geldige typen zijn JPEG, PNG, GIF en BMP. De standaardwaarde is JPEG.

   * `-i`: Pad voor invoer-PDF. Het is een verplichte parameter.

   * `-h`: Help


1. Als u tussenliggende vertoningen wilt verwijderen, selecteert u **[!UICONTROL Delete Generated Rendition]**.
1. Selecteer **[!UICONTROL Generate Web Rendition]** als u wilt dat PDF Rasterizer webuitvoeringen genereert.

   ![generate_web_renditions1](assets/generate_web_renditions1.png)

1. Geef de instellingen op op het tabblad **[!UICONTROL Web Enabled Image]**.

   ![web_enabled_image1](assets/web_enabled_image1.png)

1. Sla de workflow op.
1. Als u wilt dat PDF-rasterfunctie PDF-pagina&#39;s kan verwerken met PDF-bibliotheken, opent u het **[!UICONTROL DAM Process Subasset]**-model in de console [!UICONTROL Workflow].
1. Sleep vanuit het zijpaneel de stap PDF Rasterizer Handler onder de stap **[!UICONTROL Create Web-Enabled Image Rendition]**.
1. Configureer de volgende argumenten voor de stap **[!UICONTROL PDF Rasterizer Handler]**:

   * MIME-typen: `application/pdf` of `application/postscript`
   * Opdrachten: `PDFRasterizer -d -s 1280 -t PNG -i ${file}`
   * Miniatuurgrootten toevoegen: `319:319`, `140:100`, `48:48`. Voeg desgewenst aangepaste miniatuurconfiguratie toe.

   De opdrachtregelargumenten voor de opdracht `PDFRasterizer` kunnen het volgende bevatten:

   * `-d`: Vlag om het vloeiend weergeven van tekst, vectorillustraties en afbeeldingen mogelijk te maken. Hiermee maakt u afbeeldingen van betere kwaliteit. Het opnemen van deze parameter zorgt er echter voor dat de opdracht langzaam wordt uitgevoerd en dat de afbeeldingen groter worden.

   * `-s`: Maximale afmetingen afbeelding (hoogte of breedte). Deze wordt voor elke pagina geconverteerd naar DPI. Als de pagina&#39;s van verschillende grootte zijn, kan elke pagina potentieel met verschillende hoeveelheid schalen. De standaardinstelling is het daadwerkelijke paginaformaat.

   * `-t`: Type uitvoerafbeelding. Geldige typen zijn JPEG, PNG, GIF en BMP. De standaardwaarde is JPEG.

   * `-i`: Pad voor invoer-PDF. Het is een verplichte parameter.

   * `-h`: Help


1. Als u tussenliggende vertoningen wilt verwijderen, selecteert u **[!UICONTROL Delete Generated Rendition]**.
1. Selecteer **[!UICONTROL Generate Web Rendition]** als u wilt dat PDF Rasterizer webuitvoeringen genereert.

   ![generate_web_renditions](assets/generate_web_renditions.png)

1. Geef de instellingen op op het tabblad **[!UICONTROL Web Enabled Image]**.

   ![web_enabled_image-1](assets/web_enabled_image-1.png)

1. Sla de workflow op.
1. Upload een PDF- of AI-bestand naar [!DNL Experience Manager Assets]. PDF-rasterfunctie genereert de miniaturen en webuitvoeringen voor het bestand.
