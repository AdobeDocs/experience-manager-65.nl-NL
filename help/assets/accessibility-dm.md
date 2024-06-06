---
title: Toegankelijkheid in Dynamic Media
description: Meer informatie over toegankelijkheidsondersteuning in Dynamic Media en Dynamic Media Viewers.
contentOwner: Rick Brough
topic-tags: introduction
content-type: reference
feature: Accessibility
role: User, Admin
exl-id: bbdb800c-b6f8-4506-b8ac-daf64edcd6c0
solution: Experience Manager, Experience Manager Assets
source-git-commit: ed7183efa57db6d97941e3acc99d126c2fc0f6c5
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 0%

---

# Toegankelijkheid [!DNL Dynamic Media] {#working-with-three-d-assets-dm}

[!DNL Dynamic Media] ondersteunt toetsenbordbesturing en ondersteunende hulpmiddelen, zoals JAWS en NVDA-schermlezers, in de hele gebruikersinterface.

## Ondersteuning voor toetsenbordtoegankelijkheid in [!DNL Dynamic Media]

Omdat [!DNL Dynamic Media] is een insteekmodule voor [!DNL Adobe Experience Manager Assets], is het meeste toetsenbordbesturingsgedrag hetzelfde als in [!DNL Experience Manager Assets]. Bijvoorbeeld de `Cancel` knop in [!DNL Dynamic Media] heeft dezelfde focusmarkering als in [!DNL Experience Manager Assets]en reageert op de `Spacebar` key as in [!DNL Experience Manager Assets]. Zie [Sneltoetsen in elementen](/help/assets/accessibility.md#keyboard-shortcuts).

Toetsen die door afzonderlijke gebruikersinterface-elementen worden ondersteund in [!DNL Dynamic Media] duidelijk en gemakkelijk te ontdekken zijn. Toetsenbordbesturing in [!DNL Dynamic Media] gaat over het volgende:

* Gebruiksmogelijkheden `Tab` en `Shift+Tab` toetsaanslagen om te navigeren tussen interactieve elementen op de pagina.
Gebruiken `Tab` gaat inputnadruk naar het volgende gebruikersinterface element in de lusjeorde vooruit; het gebruiken `Shift+Tab` Hiermee wordt invoerfocus teruggezet naar het vorige gebruikersinterface-element.
Het focustraversal volgt de natuurlijke locatie van het interface-element op het scherm en beweegt van links naar rechts en vervolgens van boven naar beneden. Als een veld een fout bevat, kunt u bovendien op `Tab` om de focus naar de afbeelding te verplaatsen.
* De mogelijkheid om de `Spacebar` en `Enter` toets voor het activeren van standaardelementen van de gebruikersinterface, zoals knoppen en vervolgkeuzelijsten.
* Mogelijkheid om de toetsenbordfocus te zien op het actieve element. Het element van de gebruikersinterface dat inputnadruk heeft ontvangt een visuele nadrukaanwijzing als grens die rond het gebruikersinterface element wordt teruggegeven.
* In de Hotspot-editor kunt u bepaalde aangepaste toetsaanslagen gebruiken, zoals pijltoetsen, om te communiceren met complexe gebruikersinterface-elementen om hotspots te verplaatsen.
* In de Interactieve Video-editor kunt u de opdracht `Spacebar` om een afbeelding te selecteren en toe te voegen aan een segment. Daarnaast kunt u de opdracht `Backspace` toets om het geselecteerde item uit het menu **[!UICONTROL Content]** tab. Ook, drukken `Tab` functioneert naar wens om te navigeren tussen interactieve elementen op de pagina.
* In de redacteur van het Gewas van het Beeld/van het Slim Gewas, kunt u het volgende doen:
   * Gebruik de pijltoetsen om de framegrootte bij te snijden, of om de positie van de afbeelding te wijzigen, of beide.
   * De eerste `Tab` Met Stoppen wordt het gehele afbeeldingskader gemarkeerd. Vervolgens kunt u het kader verplaatsen met de pijltoetsen op het toetsenbord.
   * De volgende vier `Tab` stops zijn de vier hoeken van het frame. Wanneer de focus op een kaderhoek wordt geplaatst, wordt de hoek gemarkeerd. U kunt ook de pijltoetsen op het toetsenbord gebruiken om de gefocuste hoek te verplaatsen.
Zie [Het slimme uitsnijdstaal of het slimme staal van één afbeelding bewerken](/help/assets/image-profiles.md#editing-the-smart-crop-or-smart-swatch-of-a-single-image)

<!-- Keyboarding is the same because Dynamic Media is using the same UI library (Coral 3 (AEM 6.5) or Coral Spectrum (in Skyline)) as entire AEM Assets.  -->

<!-- In the Hotspot editor, Dynamic Media lets you use arrow keys to control the position of a hot spot. See [Carousel Banners](/help/assets/dynamic-media/carousel-banners.md#adding-hotspots-or-image-maps-to-an-image-banner) or [Interactive Images](/help/assets/dynamic-media/interactive-images.md#adding-hotspots-to-an-image-banner)  -->

<!-- I think we should definitely mention this in the DM-specific area of documentation for keyboard support. -->

<!-- I would not get into much of details of specific keyboard support logic of these editors. One of the reasons - chances are that accessibility support will receive Phase2-like attention, with more holistic approach. -->

## Technische ondersteuning in [!DNL Dynamic Media] {#assistive-technology-support-for-dm}

[!DNL Dynamic Media] gebruikersinterface-elementen werken met ondersteunende hulpmiddelen, zoals schermlezers. De code herkent bijvoorbeeld markeringen op een pagina wanneer u door markeringen met een sneltoets navigeert `D` of gebieden met sneltoetsen `R`. De kop wordt ook van commentaar voorzien wanneer u navigeert met de sneltoets voor koppen `H`.

## Ondersteuning voor toetsenbordtoegankelijkheid in [!DNL Dynamic Media] viewers {#keyboard-accessibility-for-dm-viewers}

Alles buiten de box [!DNL Dynamic Media] de componenten van kijkers steunen toetsenbordtoegankelijkheid voor uw klanten.

Zie [Toetsenbordtoegankelijkheid en -navigatie](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/c-keyboard-accessibility.html) in de Dynamic Media Viewers Reference Guide.

## Technische ondersteuning in [!DNL Dynamic Media] viewers {#assistive-technology-support-for-dm-viewers}

Alles [!DNL Dynamic Media] de kijkerscomponenten steunen de (Toegankelijke Rijke Toepassingen van Internet) rollen en attributen van ARIA om integratie met ondersteunende technologieën zoals het schermlezers te verbeteren.
Zie de **Technische ondersteuning** Help-onderwerp in elk aangepast vieweronderwerp in de Dynamic Media Viewers Reference Guide. Zie bijvoorbeeld [Technische ondersteuning](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/r-html5-video-viewer-20-assistive.html) voor de videoviewer, of [Technische ondersteuning](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/c-html5-aem-interactive-image-assistive.html#viewers-for-aem-assets-only) voor de Interactieve kijker van het Beeld.

## Ondersteuning voor Closed Caption in Dynamic Media {#closed-caption-support}

Dynamic Media ondersteunt de levering van video&#39;s en adaptieve videosets met ondertiteling. De bijschriften moeten vóór de video-inhoud worden weergegeven.

Zie [Video in Dynamic Media - Gesloten bijschriften toevoegen aan video](/help/assets/video.md#adding-captions-to-video).

>[!MORELIKETHIS]
>
>* [Toegankelijkheid voor Adobe-oplossingen](https://www.adobe.com/accessibility.html)
>* [Toegankelijkheid [!DNL Experience Manager Assets]](/help/assets/accessibility.md)
