---
title: ImageMagick installeren en configureren
description: Leer over de software ImageMagick, hoe te om het te installeren, opstelling de het processtap van de bevellijn, en gebruik het om, duimnagels van beelden uit te geven samen te stellen en te produceren.
contentOwner: AG
role: Admin
feature: Renditions,Developer Tools
exl-id: 6c149d31-1e64-4d29-a32a-58bd69e9fa98
solution: Experience Manager, Experience Manager Assets
source-git-commit: f8588ef353bd08b41202350072728d80ee51f565
workflow-type: tm+mt
source-wordcount: '641'
ht-degree: 0%

---

# ImageMagick installeren en configureren om te werken met [!DNL Experience Manager Assets] {#install-and-configure-imagemagick-to-work-with-aem-assets}

ImageMagick is een softwareplug-in voor het maken, bewerken, samenstellen of omzetten van bitmapafbeeldingen. Afbeeldingen kunnen in verschillende indelingen (meer dan 200) worden gelezen en geschreven, waaronder PNG, JPEG, JPEG-2000, GIF, TIFF, DPX, EXR, WebP, Postscript, PDF en SVG. Met ImageMagick kunt u afbeeldingen vergroten, verkleinen, spiegelen, roteren, vervormen, schuintrekken en transformeren. U kunt ook afbeeldingskleuren aanpassen, verschillende speciale effecten toepassen of tekst, lijnen, veelhoeken, ellipsen en curven tekenen met ImageMagick.

Gebruik de media-handler [!DNL Adobe Experience Manager] van de opdrachtregel om afbeeldingen te verwerken via ImageMagick. Om met diverse dossierformaten te werken gebruikend ImageMagick, zie [ het dossierformaten van Assets beste praktijken ](/help/assets/assets-file-format-best-practices.md). Om over alle gesteunde dossierformaten te weten, zie [ Assets gesteunde formaten ](/help/assets/assets-formats.md).

Als u grote bestanden wilt verwerken met ImageMagick, moet u rekening houden met hogere geheugenvereisten dan gebruikelijk, mogelijke wijzigingen die vereist zijn voor IM-beleid en de algemene invloed op de prestaties. De geheugenvereisten zijn afhankelijk van verschillende factoren zoals resolutie, bitdiepte, kleurprofiel en bestandsindeling. Als u zeer grote bestanden wilt verwerken met ImageMagick, moet u de [!DNL Experience Manager] -server op de juiste wijze als benchmark instellen. Aan het eind zijn er enkele nuttige bronnen beschikbaar.

>[!NOTE]
>
>Als u [!DNL Experience Manager] on [!DNL Adobe Managed Services] (AMS) gebruikt, neemt u contact op met de Klantenondersteuning van Adobe als u veel PSD- of PSB-bestanden met hoge resolutie wilt verwerken. [!DNL Experience Manager] verwerkt mogelijk geen PSB-bestanden met zeer hoge resolutie die groter zijn dan 30000 x 23000 pixels.

## ImageMagick installeren {#installing-imagemagick}

Er zijn meerdere versies van ImageMagic-installatiebestanden beschikbaar voor verschillende besturingssystemen. Gebruik de juiste versie voor uw besturingssysteem.

1. Download de aangewezen ImageMagick installatiedossiers (`https://www.imagemagick.org/script/download.php website`) voor uw werkend systeem.
1. Start het installatiebestand om ImageMagick te installeren op de schijf waarop de [!DNL Experience Manager] -server zich bevindt.

1. Plaats de variabele van het wegmilieu aan de installatiemap ImageMagic.
1. Als u wilt controleren of de installatie is gelukt, voert u de opdracht `identify -version` uit.

## De processtap van de opdrachtregel instellen {#set-up-the-command-line-process-step}

U kunt de processtap van de bevellijn voor uw bepaald gebruiksgeval plaatsen. Voer de volgende stappen uit om elke keer dat u een JPEG-afbeeldingsbestand toevoegt aan `/content/dam` op de [!DNL Experience Manager] -server, een gespiegelde afbeelding en miniaturen (140x100, 48x48, 319x319 en 1280x1280) te genereren:

1. Ga op de [!DNL Experience Manager] -server naar de Workflowconsole ( `https://[aem_server]:[port]/workflow` ) en open het **[!UICONTROL DAM Update Asset]** -workflowmodel.
1. Open vanuit het workflowmodel van **[!UICONTROL DAM Update Asset]** de stap **[!UICONTROL EPS thumbnails (powered by ImageMagick)]** .
1. Voeg in de **[!UICONTROL Arguments tab]** `image/jpeg` toe aan de lijst **[!UICONTROL Mime Types]** .

   ![ mime_types_jpeg ](assets/mime_types_jpeg.png)

1. Voer in het vak **[!UICONTROL Commands]** de volgende opdracht in:

   `convert ./${filename} -flip ./${basename}.flipped.jpg`

1. Selecteer de markeringen **[!UICONTROL Delete Generated Rendition]** en **[!UICONTROL Generate Web Rendition]** .

   ![ select_flags ](assets/select_flags.png)

1. Geef op het tabblad **[!UICONTROL Web Enabled Image]** de details voor de vertoning op met afmetingen van 1280 x 1280 pixels. Geef bovendien `image/jpeg` op in het vak **[!UICONTROL Mimetype]** .

   ![ web_enabled_image ](assets/web_enabled_image.png)

1. Klik op **[!UICONTROL OK]** om de wijzigingen op te slaan.

   >[!NOTE]
   >
   >De opdracht `convert` wordt mogelijk niet uitgevoerd met bepaalde Windows-versies (bijvoorbeeld Windows SE), omdat dit een conflict veroorzaakt met het native hulpprogramma `convert` dat deel uitmaakt van de Windows-installatie. In dit geval, vermeld de volledige weg voor het nut ImageMagick. Geef bijvoorbeeld op:
   >
   >
   >`"C:\Program Files\ImageMagick-6.8.9-Q16\convert.exe" -define jpeg:size=319x319 ./${filename} -thumbnail 319x319 cq5dam.thumbnail.319.319.png`

1. Open de stap **[!UICONTROL Process Thumbnails]** en voeg het MIME-type `image/jpeg` onder **[!UICONTROL Skip Mime Types]** toe.

   ![ skip_mime_types ](assets/skip_mime_types.png)

1. Voeg op het tabblad **[!UICONTROL Web Enabled Image]** het MIME-type `image/jpeg` onder **[!UICONTROL Skip List]** toe. Klik op **[!UICONTROL OK]** om de wijzigingen op te slaan.

   ![ web_enabled ](assets/web_enabled.png)

1. Sla de workflow op.

1. Als u de juiste verwerking wilt controleren, uploadt u een JPG-afbeelding naar [!DNL Assets] . Nadat de verwerking is voltooid, controleert u of een gespiegelde afbeelding en de uitvoeringen zijn gegenereerd.

## Beveiligingskwetsbaarheden beperken {#mitigating-security-vulnerabilities}

Er zijn meerdere beveiligingskwetsbaarheden verbonden aan het gebruik van ImageMagick voor het verwerken van afbeeldingen. Als u bijvoorbeeld door gebruikers verzonden afbeeldingen verwerkt, bestaat het risico dat de code op afstand wordt uitgevoerd (RCE).

Daarnaast zijn verschillende plug-ins voor beeldverwerking afhankelijk van de ImageMagick-bibliotheek, waaronder, maar niet uitsluitend, PHP&#39;s fantaick, Ruby&#39;s magick en paperclip en de imagemagick van nodejs.

Als u ImageMagick of een betrokken bibliotheek gebruikt, raadt Adobe u aan de bekende kwetsbaarheden te beperken door ten minste een van de volgende taken (maar bij voorkeur beide) uit te voeren:

1. Verifieer dat alle beelddossiers met verwachte [ &quot;magische bytes&quot;](https://en.wikipedia.org/wiki/List_of_file_signatures) beantwoorden aan de types van beelddossier u steunt alvorens hen naar ImageMagick voor verwerking te verzenden.
1. Gebruik een beleidsdossier om de kwetsbare Codeurs onbruikbaar te maken ImageMagick. Het algemene beleid voor ImageMagick vindt u op `/etc/ImageMagick` .
