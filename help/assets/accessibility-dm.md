---
title: Toegankelijkheid in dynamische media
description: Meer informatie over toegankelijkheid in Dynamic Media en Dynamic Media Viewers
contentOwner: Rick Brough
topic-tags: introduction
content-type: reference
translation-type: tm+mt
source-git-commit: 696aaa54007e4a78fe6b07d8ba65660595286dca
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 0%

---


# Toegankelijkheid in [!DNL Dynamic Media] {#working-with-three-d-assets-dm}

[!DNL Dynamic Media] ondersteunt toetsenbordbesturing en ondersteunende hulpmiddelen, zoals JAWS en NVDA-schermlezers, in de hele gebruikersinterface.

## Ondersteuning voor toetsenbordtoegankelijkheid in [!DNL Dynamic Media]

Omdat [!DNL Dynamic Media] het een insteekmodule is voor [!DNL Adobe Experience Manager Assets]het meeste toetsenbordbesturingsgedrag precies hetzelfde is als in [!DNL Experience Manager Assets]. De `Cancel` knop in [!DNL Dynamic Media] heeft bijvoorbeeld dezelfde focusmarkering als in [!DNL Experience Manager Assets]en reageert op de `Spacebar` toets als in [!DNL Experience Manager Assets]. Zie [Sneltoetsen in Elementen](/help/assets/accessibility.md#keyboard-shortcuts).

Toetsen die door afzonderlijke elementen van de gebruikersinterface in worden ondersteund, [!DNL Dynamic Media] zijn in de meeste gevallen duidelijk en gemakkelijk te vinden. Het besturingselement Keyboard in [!DNL Dynamic Media] gaat over het volgende:

* De mogelijkheid om met `Tab` en `Shift+Tab` toetsaanslagen te navigeren tussen interactieve elementen op de pagina.
Door de invoerfocus naar het volgende gebruikersinterface-element in de tabvolgorde te `Tab` verplaatsen, het gebruiken `Shift+Tab` brengt inputnadruk terug naar het vorige gebruikersinterface element.
Het focustraversal volgt de natuurlijke locatie van het interface-element op het scherm en beweegt van links naar rechts en vervolgens van boven naar beneden. Als een veld een fout bevat, kunt u erop drukken de focus `Tab` naar het veld te verplaatsen.
* De mogelijkheid om de `Spacebar` toets en de `Enter` toets te gebruiken om standaardelementen van de gebruikersinterface te activeren, zoals knoppen, vervolgkeuzelijst, enzovoort.
* Mogelijkheid om de toetsenbordfocus te zien op het actieve element. Het gebruikersinterface-element dat invoerfocus heeft, krijgt mogelijk een visuele focusindicatie als een rand die rondom het interface-element wordt weergegeven.
* In de Hotspot-editor kunt u bepaalde aangepaste toetsaanslagen gebruiken, zoals pijltoetsen, om te communiceren met complexe gebruikersinterface-elementen om hotspots te verplaatsen.
* In de Interactieve Video redacteur, kunt u gebruiken `Spacebar` om een beeld te selecteren en het toe te voegen aan een segment. Bovendien kunt u de `Backspace` toets gebruiken om het geselecteerde item van het **[!UICONTROL Content]** tabblad te verwijderen. Druk desgewenst ook op `Tab` functies om te navigeren tussen interactieve elementen op de pagina.
* In de redacteur van het Gewas van het Beeld/van het Slim Gewas, hebt u de capaciteit om het volgende te doen:
   * Gebruik de pijltoetsen om de framegrootte bij te snijden of de positie van de afbeelding of beide te wijzigen.
   * De eerste `Tab` stop markeert het volledige beeldkader. Vervolgens kunt u het frame opnieuw plaatsen met de pijltoetsen op het toetsenbord.
   * De volgende vier `Tab` stops zijn de vier hoeken van het kader. Wanneer de focus op een kaderhoek wordt geplaatst, wordt de hoek gemarkeerd. U kunt ook de pijltoetsen op het toetsenbord gebruiken om de gefocuste hoek te verplaatsen.
Zie Het slimme uitsnijdstaal of het slimme staal van één afbeelding [bewerken](/help/assets/image-profiles.md#editing-the-smart-crop-or-smart-swatch-of-a-single-image)

<!-- Keyboarding is the same because Dynamic Media is using the same UI library (Coral 3 (AEM 6.5) or Coral Spectrum (in Skyline)) as entire AEM Assets.  -->

<!-- In the Hotspot editor, Dynamic Media lets you use arrow keys to control the position of a hot spot. See [Carousel Banners](/help/assets/dynamic-media/carousel-banners.md##adding-hotspots-or-image-maps-to-an-image-banner) or [Interactive Images](/help/assets/dynamic-media/interactive-images.md#adding-hotspots-to-an-image-banner)  -->

<!-- I think we should definitely mention this in the DM-specific area of documentation for keyboard support. -->

<!-- I would not get into much of details of specific keyboard support logic of these editors. One of the reasons - chances are that accessibility support will receive Phase2-like attention, with more holistic approach. -->

## Technische ondersteuning in [!DNL Dynamic Media] {#assistive-technology-support-for-dm}

[!DNL Dynamic Media] gebruikersinterface-elementen werken met ondersteunende hulpmiddelen, zoals schermlezers. De code herkent bijvoorbeeld markeringen op een pagina wanneer u door ligaturen navigeert met sneltoetsen `D` of gebieden met sneltoetsen `R`. De kop wordt ook van commentaar voorzien wanneer u navigeert met de sneltoets voor kopteksten `H`.

## Ondersteuning voor toetsenbordtoegankelijkheid in [!DNL Dynamic Media] viewers {#keyboard-accessibility-for-dm-viewers}

Alle out-of-the-box [!DNL Dynamic Media] viewercomponenten ondersteunen toetsenbordtoegankelijkheid voor uw klanten.

Zie [Toetsenbordtoegankelijkheid en -navigatie](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/c-keyboard-accessibility.html) in de handleiding ter referentie van Dynamic Media Viewers.

## Ondersteunende technologie voor [!DNL Dynamic Media] viewers {#assistive-technology-support-for-dm-viewers}

Alle [!DNL Dynamic Media] viewercomponenten ondersteunen de rollen en kenmerken van ARIA (Accessible Rich Internet Applications) om de integratie met ondersteunende hulpmiddelen, zoals schermlezers, te verbeteren.
Zie het onderwerp van de Hulp van de **Technologie van de Steun** in om het even welk het aanpassen kijkersonderwerp in de Dynamische Gids van de Verwijzing van de Kijkers van Media. Zie bijvoorbeeld Ondersteuning [van](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/r-html5-video-viewer-20-assistive.html) ondersteunende hulpmiddelen voor de videoviewer of [ondersteuning](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/c-html5-aem-interactive-image-assistive.html#viewers-for-aem-assets-only) voor ondersteunende hulpmiddelen voor de interactieve beeldviewer.

>[!MORELIKETHIS]
>
>* [Toegankelijkheid voor Adobe-oplossingen](https://www.adobe.com/accessibility.html)
>* [Toegankelijkheid in [!DNL Experience Manager Assets]](/help/assets/accessibility.md)

