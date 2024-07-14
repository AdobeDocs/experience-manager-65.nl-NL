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

# Toegankelijkheid in [!DNL Dynamic Media] {#working-with-three-d-assets-dm}

[!DNL Dynamic Media] ondersteunt toetsenbordbesturing en ondersteunende hulpmiddelen, zoals JAWS en NVDA-schermlezers, in de hele gebruikersinterface voor het ontwerpen.

## Ondersteuning voor toetsenbordtoegankelijkheid in [!DNL Dynamic Media]

Omdat [!DNL Dynamic Media] een plug-in is naar [!DNL Adobe Experience Manager Assets] , is het meeste toetsenbordbesturingsgedrag hetzelfde als in [!DNL Experience Manager Assets] . De knop `Cancel` in [!DNL Dynamic Media] heeft bijvoorbeeld dezelfde focusmarkering als in [!DNL Experience Manager Assets] en reageert op de `Spacebar` -toets als in [!DNL Experience Manager Assets] . Zie [ kortere weg van het Toetsenbord in Assets ](/help/assets/accessibility.md#keyboard-shortcuts).

Toetsen die door afzonderlijke gebruikersinterface-elementen in [!DNL Dynamic Media] worden ondersteund, zijn duidelijk en gemakkelijk te vinden. Het besturingselement Toetsenbord in [!DNL Dynamic Media] heeft betrekking op het volgende:

* De mogelijkheid om `Tab` - en `Shift+Tab` -toetsaanslagen te gebruiken om te navigeren tussen interactieve elementen op de pagina.
Als u `Tab` gebruikt, wordt de invoerfocus op het volgende interface-element in de tabvolgorde gebracht. Als u `Shift+Tab` gebruikt, wordt de invoerfocus weer op het vorige gebruikersinterface-element geplaatst.
Het focustraversal volgt de natuurlijke locatie van het interface-element op het scherm en beweegt van links naar rechts en vervolgens van boven naar beneden. Als een veld een fout bevat, kunt u bovendien op `Tab` drukken om de focus naar het veld te verplaatsen.
* Mogelijkheid om de toetsen `Spacebar` en `Enter` te gebruiken om standaardelementen van de gebruikersinterface te activeren, zoals knoppen en vervolgkeuzelijsten.
* Mogelijkheid om de toetsenbordfocus te zien op het actieve element. Het element van de gebruikersinterface dat inputnadruk heeft ontvangt een visuele nadrukaanwijzing als grens die rond het gebruikersinterface element wordt teruggegeven.
* In de Hotspot-editor kunt u bepaalde aangepaste toetsaanslagen gebruiken, zoals pijltoetsen, om te communiceren met complexe gebruikersinterface-elementen om hotspots te verplaatsen.
* In de Interactieve Video redacteur, kunt u `Spacebar` gebruiken om een beeld te selecteren en het toe te voegen aan een segment. Daarnaast kunt u de `Backspace` -toets gebruiken om het geselecteerde item van het tabblad **[!UICONTROL Content]** te verwijderen. Als u op `Tab` drukt, kunt u ook naar wens navigeren tussen interactieve elementen op de pagina.
* In de redacteur van het Gewas van het Beeld/van het Slim Gewas, kunt u het volgende doen:
   * Gebruik de pijltoetsen om de framegrootte bij te snijden, of om de positie van de afbeelding te wijzigen, of beide.
   * Bij de eerste stop van `Tab` wordt het hele afbeeldingskader gemarkeerd. Vervolgens kunt u het kader verplaatsen met de pijltoetsen op het toetsenbord.
   * De volgende vier `Tab` stops zijn de vier hoeken van het frame. Wanneer de focus op een kaderhoek wordt geplaatst, wordt de hoek gemarkeerd. U kunt ook de pijltoetsen op het toetsenbord gebruiken om de gefocuste hoek te verplaatsen.
Zie [ het slimme gewas of slim monster van één enkel beeld ](/help/assets/image-profiles.md#editing-the-smart-crop-or-smart-swatch-of-a-single-image) uitgeven

<!-- Keyboarding is the same because Dynamic Media is using the same UI library (Coral 3 (AEM 6.5) or Coral Spectrum (in Skyline)) as entire AEM Assets.  -->

<!-- In the Hotspot editor, Dynamic Media lets you use arrow keys to control the position of a hot spot. See [Carousel Banners](/help/assets/dynamic-media/carousel-banners.md#adding-hotspots-or-image-maps-to-an-image-banner) or [Interactive Images](/help/assets/dynamic-media/interactive-images.md#adding-hotspots-to-an-image-banner)  -->

<!-- I think we should definitely mention this in the DM-specific area of documentation for keyboard support. -->

<!-- I would not get into much of details of specific keyboard support logic of these editors. One of the reasons - chances are that accessibility support will receive Phase2-like attention, with more holistic approach. -->

## Ondersteuning voor hulpprogramma&#39;s in [!DNL Dynamic Media] {#assistive-technology-support-for-dm}

[!DNL Dynamic Media] -gebruikersinterface-elementen werken met ondersteunende hulpmiddelen, zoals schermlezers. De code herkent bijvoorbeeld markeringen op een pagina wanneer u door markeringen navigeert met sneltoetsen `D` of gebieden met sneltoetsen `R` . De kop wordt ook van commentaar voorzien wanneer u navigeert met de sneltoets voor koppen `H` .

## Ondersteuning voor toetsenbordtoegankelijkheid in [!DNL Dynamic Media] -viewers {#keyboard-accessibility-for-dm-viewers}

Alle out-of-the-box [!DNL Dynamic Media] viewercomponenten ondersteunen toetsenbordtoegankelijkheid voor uw klanten.

Zie [ de toegankelijkheid van het Toetsenbord en navigatie ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/c-keyboard-accessibility.html) in de Gids van de Verwijzing van de Kijkers van Dynamic Media.

## Ondersteuning voor hulpprogramma&#39;s in [!DNL Dynamic Media] -viewers {#assistive-technology-support-for-dm-viewers}

Alle [!DNL Dynamic Media] -viewercomponenten ondersteunen de rollen en kenmerken van ARIA (Accessible Rich Internet Applications) om de integratie met ondersteunende hulpmiddelen, zoals schermlezers, te verbeteren.
Zie het **onderwerp van de Hulp van de Technologie van 0} Hulp in om het even welk het aanpassen kijkersonderwerp in de Gids van de Verwijzing van de Kijkers van Dynamic Media.** Bijvoorbeeld, zie ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/r-html5-video-viewer-20-assistive.html) de technologiesteun van 0} Hulpmiddelen {voor de Videokijker, of [ de technologiesteun van de Hulp ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/c-html5-aem-interactive-image-assistive.html#viewers-for-aem-assets-only) voor de Interactieve kijker van het Beeld.[

## Ondersteuning voor Closed Caption in Dynamic Media {#closed-caption-support}

Dynamic Media ondersteunt de levering van video&#39;s en adaptieve videosets met ondertiteling. De bijschriften moeten vóór de video-inhoud worden weergegeven.

Zie [ Video in Dynamic Media - voeg gesloten titels aan video ](/help/assets/video.md#adding-captions-to-video) toe.

>[!MORELIKETHIS]
>
>* [ Toegankelijkheid voor de oplossingen van de Adobe ](https://www.adobe.com/accessibility.html)
>* [ Toegankelijkheid in  [!DNL Experience Manager Assets]](/help/assets/accessibility.md)
