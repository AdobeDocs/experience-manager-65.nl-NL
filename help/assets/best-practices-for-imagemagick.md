---
title: ImageMagick installeren en configureren
description: Leer over de software ImageMagick, hoe te om het te installeren, opstelling de het processtap van de bevellijn, en gebruik het om, duimnagels van beelden uit te geven samen te stellen en te produceren.
contentOwner: AG
role: Admin
feature: Renditions,Developer Tools
exl-id: 6c149d31-1e64-4d29-a32a-58bd69e9fa98
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 0%

---

# Installeer en vorm ImageMagick om met te werken [!DNL Experience Manager Assets] {#install-and-configure-imagemagick-to-work-with-aem-assets}

ImageMagick is een softwareplug-in voor het maken, bewerken, samenstellen of omzetten van bitmapafbeeldingen. Het kan beelden in diverse formaten (meer dan 200) lezen en schrijven met inbegrip van PNG, JPEG, JPEG-2000, GIF, TIFF, DPX, EXR, WebP, Postscript, PDF, en SVG. Met ImageMagick kunt u afbeeldingen vergroten, verkleinen, spiegelen, roteren, vervormen, schuintrekken en transformeren. U kunt ook afbeeldingskleuren aanpassen, verschillende speciale effecten toepassen of tekst, lijnen, veelhoeken, ellipsen en curven tekenen met ImageMagick.

Gebruik de [!DNL Adobe Experience Manager] media manager van de bevellijn aan procesbeelden door ImageMagick. Als u met verschillende bestandsindelingen werkt met ImageMagick, raadpleegt u [Aanbevolen werkwijzen voor bestandsindelingen voor elementen](/help/assets/assets-file-format-best-practices.md). Zie voor meer informatie over alle ondersteunde bestandsindelingen [Ondersteunde indelingen voor middelen](/help/assets/assets-formats.md).

Als u grote bestanden wilt verwerken met ImageMagick, moet u rekening houden met hogere geheugenvereisten dan gebruikelijk, mogelijke wijzigingen die vereist zijn voor IM-beleid en de algemene invloed op de prestaties. De geheugenvereisten zijn afhankelijk van verschillende factoren zoals resolutie, bitdiepte, kleurprofiel en bestandsindeling. Als u van plan bent zeer grote bestanden te verwerken met ImageMagick, moet u de standaardprocedure [!DNL Experience Manager] server. Aan het eind zijn er enkele nuttige bronnen beschikbaar.

>[!NOTE]
>
>Als u [!DNL Experience Manager] op [!DNL Adobe Managed Services] (AMS) kunt u contact opnemen met de klantenondersteuning van de Adobe als u veel PSD- of PSB-bestanden met hoge resolutie wilt verwerken. [!DNL Experience Manager] PSB-bestanden met een zeer hoge resolutie die groter zijn dan 30000 x 23000 pixels, worden mogelijk niet verwerkt.

## ImageMagick installeren {#installing-imagemagick}

Er zijn meerdere versies van ImageMagic-installatiebestanden beschikbaar voor verschillende besturingssystemen. Gebruik de juiste versie voor uw besturingssysteem.

1. Download de juiste [ImageMagick-installatiebestanden](https://www.imagemagick.org/script/download.php) voor uw besturingssysteem.
1. Om ImageMagick op de schijf te installeren die ontvangen [!DNL Experience Manager] -server, start u het installatiebestand.

1. Plaats de variabele van het wegmilieu aan de installatiemap ImageMagic.
1. Als u wilt controleren of de installatie is gelukt, voert u de opdracht `identify -version` gebruiken.

## De processtap van de opdrachtregel instellen {#set-up-the-command-line-process-step}

U kunt de processtap van de bevellijn voor uw bepaald gebruiksgeval plaatsen. Voer de volgende stappen uit om elke keer dat u een JPEG-afbeeldingsbestand toevoegt, een gespiegelde afbeelding en miniaturen (140x100, 48x48, 319x319 en 1280x1280) te genereren `/content/dam` op de [!DNL Experience Manager] server:

1. Op de [!DNL Experience Manager] server, ga naar de Werkstroomconsole (`https://[aem_server]:[port]/workflow`) en opent u de **[!UICONTROL DAM Update Asset]** workflowmodel.
1. Van de **[!UICONTROL DAM Update Asset]** workflowmodel, opent u het **[!UICONTROL EPS thumbnails (powered by ImageMagick)]** stap.
1. In de **[!UICONTROL Arguments tab]**, toevoegen `image/jpeg` aan de **[!UICONTROL Mime Types]** lijst.

   ![mime_types_jpeg](assets/mime_types_jpeg.png)

1. In de **[!UICONTROL Commands]** voert u de volgende opdracht in:

   `convert ./${filename} -flip ./${basename}.flipped.jpg`

1. Selecteer de **[!UICONTROL Delete Generated Rendition]** en **[!UICONTROL Generate Web Rendition]** vlaggen.

   ![select_flags](assets/select_flags.png)

1. In de **[!UICONTROL Web Enabled Image]** op, geeft u de details voor de vertoning op met afmetingen 1280x1280 pixels. Geef daarnaast `image/jpeg` in de **[!UICONTROL Mimetype]** doos.

   ![web_enabled_image](assets/web_enabled_image.png)

1. Klikken **[!UICONTROL OK]** om de wijzigingen op te slaan

   >[!NOTE]
   >
   >De `convert` de opdracht kan niet worden uitgevoerd met bepaalde Windows-versies (bijvoorbeeld Windows SE), omdat er een conflict is met de native `convert` nut dat een deel van de installatie van Vensters is. In dit geval, vermeld de volledige weg voor het nut ImageMagick. Geef bijvoorbeeld op:
   >
   >
   >`"C:\Program Files\ImageMagick-6.8.9-Q16\convert.exe" -define jpeg:size=319x319 ./${filename} -thumbnail 319x319 cq5dam.thumbnail.319.319.png`

1. Open de **[!UICONTROL Process Thumbnails]** en voeg het MIME-type toe `image/jpeg` krachtens **[!UICONTROL Skip Mime Types]**.

   ![skip_mime_types](assets/skip_mime_types.png)

1. In de **[!UICONTROL Web Enabled Image]** tabblad, het MIME-type toevoegen `image/jpeg` onder de **[!UICONTROL Skip List]**. Klikken **[!UICONTROL OK]** om de wijzigingen op te slaan

   ![web_enabled](assets/web_enabled.png)

1. Sla de workflow op.

1. Als u de juiste verwerking wilt controleren, uploadt u een JPG-afbeelding naar [!DNL Assets]. Nadat de verwerking is voltooid, controleert u of een gespiegelde afbeelding en de uitvoeringen zijn gegenereerd.

## Beveiligingskwetsbaarheden beperken {#mitigating-security-vulnerabilities}

Er zijn meerdere beveiligingskwetsbaarheden verbonden aan het gebruik van ImageMagick voor het verwerken van afbeeldingen. Als u bijvoorbeeld door gebruikers verzonden afbeeldingen verwerkt, bestaat het risico dat de code op afstand wordt uitgevoerd (RCE).

Daarnaast zijn verschillende plug-ins voor beeldverwerking afhankelijk van de ImageMagick-bibliotheek, waaronder, maar niet uitsluitend, PHP&#39;s fantaick, Ruby&#39;s magick en paperclip en de imagemagick van nodejs.

Als u ImageMagick of een beïnvloede bibliotheek gebruikt, adviseert de Adobe dat u de bekende kwetsbaarheid verlicht door minstens één van de volgende taken (maar bij voorkeur allebei) uit te voeren:

1. Controleer of alle afbeeldingsbestanden beginnen met de verwachte [&quot;magic bytes&quot;](https://en.wikipedia.org/wiki/List_of_file_signatures) komt overeen met de afbeeldingsbestandstypen die u ondersteunt voordat u ze naar ImageMagick stuurt voor verwerking.
1. Gebruik een beleidsdossier om de kwetsbare Codeurs onbruikbaar te maken ImageMagick. Het algemene beleid voor ImageMagick is te vinden op `/etc/ImageMagick`.
