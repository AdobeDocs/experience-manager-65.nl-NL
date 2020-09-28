---
title: ImageMagick installeren en configureren
description: Leer over de software ImageMagick, hoe te om het te installeren, opstelling de het processtap van de bevellijn, en gebruik het om, duimnagels van beelden uit te geven samen te stellen en te produceren.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 5069c2cd26e84866d72a61d36de085dadd556cdd
workflow-type: tm+mt
source-wordcount: '655'
ht-degree: 0%

---


# Installeer en vorm ImageMagick om met te werken [!DNL Experience Manager Assets] {#install-and-configure-imagemagick-to-work-with-aem-assets}

ImageMagick is een softwareplug-in voor het maken, bewerken, samenstellen of omzetten van bitmapafbeeldingen. Afbeeldingen kunnen in verschillende indelingen (meer dan 200) worden gelezen en geschreven, waaronder PNG, JPEG, JPEG-2000, GIF, TIFF, DPX, EXR, WebP, Postscript, PDF en SVG. Met ImageMagick kunt u afbeeldingen vergroten, verkleinen, spiegelen, roteren, vervormen, schuintrekken en transformeren. U kunt ook afbeeldingskleuren aanpassen, verschillende speciale effecten toepassen of tekst, lijnen, veelhoeken, ellipsen en curven tekenen met ImageMagick.

Gebruik de [!DNL Adobe Experience Manager] media manager van de bevellijn om beelden door ImageMagick te verwerken. Als u met ImageMagick met verschillende bestandsindelingen wilt werken, raadpleegt u de aanbevolen werkwijzen voor [bestandsindelingen](/help/assets/assets-file-format-best-practices.md)voor Middelen. Zie Ondersteunde [elementen voor informatie over alle ondersteunde bestandsindelingen](/help/assets/assets-formats.md).

Als u grote bestanden wilt verwerken met ImageMagick, moet u rekening houden met hogere geheugenvereisten dan gebruikelijk, mogelijke wijzigingen die vereist zijn voor IM-beleid en de algemene invloed op de prestaties. De geheugenvereisten zijn afhankelijk van verschillende factoren zoals resolutie, bitdiepte, kleurprofiel en bestandsindeling. Als u zeer grote bestanden wilt verwerken met ImageMagick, moet u de [!DNL Experience Manager] server op de juiste wijze als benchmark instellen. Aan het eind zijn er enkele nuttige bronnen beschikbaar.

>[!NOTE]
>
>Als u [!DNL Experience Manager] op [!DNL Adobe Managed Services] (AMS) gebruikt, neemt u contact op met de klantenservice van Adobe als u van plan bent om veel PSD- of PSB-bestanden met hoge resolutie te verwerken. [!DNL Experience Manager] PSB-bestanden met een zeer hoge resolutie die groter zijn dan 30000 x 23000 pixels, worden mogelijk niet verwerkt.

## ImageMagick installeren {#installing-imagemagick}

Er zijn meerdere versies van ImageMagic-installatiebestanden beschikbaar voor verschillende besturingssystemen. Gebruik de juiste versie voor uw besturingssysteem.

1. Download de juiste [ImageMagick-installatiebestanden](https://www.imagemagick.org/script/download.php) voor uw besturingssysteem.
1. Start het installatiebestand om ImageMagick te installeren op de schijf waarop de [!DNL Experience Manager] server wordt gehost.

1. Plaats de variabele van het wegmilieu aan de installatiemap ImageMagic.
1. Om te controleren of de installatie succesvol was, voer het `identify -version` bevel uit.

## De processtap van de opdrachtregel instellen {#set-up-the-command-line-process-step}

U kunt de processtap van de bevellijn voor uw bepaald gebruiksgeval plaatsen. Voer de volgende stappen uit om elke keer dat u een JPEG-afbeeldingsbestand toevoegt aan de `/content/dam` [!DNL Experience Manager] server, een gespiegelde afbeelding en miniaturen (140x100, 48x48, 319x319 en 1280x1280) te genereren:

1. Ga op de [!DNL Experience Manager] server naar de workflowconsole (`https://[aem_server]:[port]/workflow`) en open het **[!UICONTROL DAM Update Asset]** workflowmodel.
1. Open de **[!UICONTROL DAM Update Asset]** stap in het **[!UICONTROL EPS thumbnails (powered by ImageMagick)]** workflowmodel.
1. Voeg in de **[!UICONTROL Arguments tab]** lijst toe `image/jpeg` aan de **[!UICONTROL Mime Types]** lijst.

   ![mime_types_jpeg](assets/mime_types_jpeg.png)

1. Voer in het **[!UICONTROL Commands]** vak de volgende opdracht in:

   `convert ./${filename} -flip ./${basename}.flipped.jpg`

1. Selecteer de **[!UICONTROL Delete Generated Rendition]** vlaggen en de **[!UICONTROL Generate Web Rendition]** vlaggen.

   ![select_flags](assets/select_flags.png)

1. Geef op het **[!UICONTROL Web Enabled Image]** tabblad de details voor de vertoning op met afmetingen van 1280 x 1280 pixels. Geef bovendien `image/jpeg` in het **[!UICONTROL Mimetype]** vak op.

   ![web_enabled_image](assets/web_enabled_image.png)

1. Click **[!UICONTROL OK]** to save the changes.

   >[!NOTE]
   >
   >Het `convert` bevel kan niet met bepaalde versies van Vensters (bijvoorbeeld SE) lopen, omdat het met het inheemse `convert` nut conflicteert dat deel van de installatie van Vensters uitmaakt. In dit geval, vermeld de volledige weg voor het nut ImageMagick. Geef bijvoorbeeld
   >
   >
   >`"C:\Program Files\ImageMagick-6.8.9-Q16\convert.exe" -define jpeg:size=319x319 ./${filename} -thumbnail 319x319 cq5dam.thumbnail.319.319.png`

1. Open de **[!UICONTROL Process Thumbnails]** stap en voeg het MIME-type `image/jpeg` onder toe **[!UICONTROL Skip Mime Types]**.

   ![skip_mime_types](assets/skip_mime_types.png)

1. Voeg op het **[!UICONTROL Web Enabled Image]** tabblad het MIME-type toe `image/jpeg` onder de **[!UICONTROL Skip List]**. Click **[!UICONTROL OK]** to save the changes.

   ![web_enabled](assets/web_enabled.png)

1. Sla de workflow op.

1. Als u de juiste verwerking wilt controleren, uploadt u een JPG-afbeelding naar [!DNL Assets]. Nadat de verwerking is voltooid, controleert u of een gespiegelde afbeelding en de uitvoeringen zijn gegenereerd.

## Beveiligingskwetsbaarheden beperken {#mitigating-security-vulnerabilities}

Er zijn meerdere beveiligingskwetsbaarheden verbonden aan het gebruik van ImageMagick voor het verwerken van afbeeldingen. Als u bijvoorbeeld door gebruikers verzonden afbeeldingen verwerkt, bestaat het risico dat de code op afstand wordt uitgevoerd (RCE).

Daarnaast zijn verschillende plug-ins voor beeldverwerking afhankelijk van de ImageMagick-bibliotheek, waaronder, maar niet uitsluitend, PHP&#39;s fantaick, Ruby&#39;s magick en paperclip en de imagemagick van nodejs.

Als u ImageMagick of een beïnvloede bibliotheek gebruikt, adviseert Adobe dat u de bekende kwetsbaarheid verlicht door minstens één van de volgende taken (maar bij voorkeur allebei) uit te voeren:

1. Controleer of alle afbeeldingsbestanden beginnen met de verwachte [&quot;toverbytes&quot;](https://en.wikipedia.org/wiki/List_of_file_signatures) die overeenkomen met de afbeeldingsbestandstypen die u ondersteunt voordat u ze naar ImageMagick stuurt voor verwerking.
1. Gebruik een beleidsdossier om de kwetsbare Codeurs onbruikbaar te maken ImageMagick. Het algemene beleid voor ImageMagick is te vinden op `/etc/ImageMagick`.
