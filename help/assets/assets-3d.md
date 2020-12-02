---
title: Werken met 3D-elementen in dynamische media
seo-title: Werken met 3D-elementen in dynamische media
description: Leer hoe u met 3D-middelen werkt in Dynamic Media
seo-description: Leer hoe u met 3D-middelen werkt in Dynamic Media
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: introduction
content-type: reference
translation-type: tm+mt
source-git-commit: cec6c4f9a1a75eb049dd4b8461c36c8d58d46f79
workflow-type: tm+mt
source-wordcount: '2241'
ht-degree: 2%

---


# Werken met 3D-elementen in dynamische media {#working-with-three-d-assets-dm}

Met dynamische media kunt u 3D-elementen uploaden, beheren, weergeven en leveren als indrukwekkende ervaringen.

* Klik met één klik op het publiceren van 3D-elementen (met **[!UICONTROL Quick Publish]** op de werkbalk) om een URL te genereren.
* Geoptimaliseerde ondersteuning voor het weergeven van 3D-middelen met de voorinstelling voor interactieve maatviewer van hoge kwaliteit, aangedreven door Adobe Dimension.
* Met de 3D Media WCM-component kunt u eenvoudig 3D-elementen toevoegen aan uw AEM Sites-pagina&#39;s.

Er is geen aanvullende configuratie vereist voor het gebruik van 3D-elementen in dynamische media.

![schoen in 3d](/help/assets/assets-dm/3d-dimensional-viewer-quickpublish-url-embed2.png)

<!-- See also [Dynamic Media 3D Release Notes](/help/release-notes/aem3d-release-notes.md). -->

## 3D-indelingen die worden ondersteund in dynamische media {#supported-three-d-file-formats-in-dm}

Dynamische media ondersteunt de volgende 3D-indelingen.

Zie ook [Ondersteunde 3D-indelingen.](/help/assets/assets-formats.md)

| 3D-bestandsextensie | Bestandsindeling | MIME-type | Opmerkingen |
|---|---|---|---|
| GLB | Binaire GL-transmissie | model/gltf-binair | Hiermee neemt u de materialen en structuren op als één enkel element. |
| OBJ | WaveFront 3D-objectbestand | application/x-tgif |  |
| STL | Stereolithografie | application/vnd.ms-pki.stl |  |
| USDZ | Universal Scene Description Zip-archief | model/vnd.usdz+zip | *Alleen ondersteuning voor inname; er is geen weergave of interactie beschikbaar.* USDZ is een eigen 3D-indeling die door Safari- en iOS-apparaten kan worden weergegeven. |

## Snel starten: 3D-elementen in dynamische media {#quick-start-three-d}

De volgende stapsgewijze beschrijving van de workflow is ontworpen om u te helpen snel aan de slag te gaan met 3D-middelen in de modus Dynamische media - Scene7.

>[!NOTE]
>
>3D-elementen worden niet ondersteund in de modus Dynamische media - Hybride.

Voordat u met 3D-elementen werkt in Dynamische media, moet u controleren of de AEM beheerder Dynamische media-Cloud Services al heeft ingeschakeld en geconfigureerd in de modus Dynamische media - Scene7.

Zie [Dynamische media-Cloud Services configureren](/help/assets/config-dms7.md#configuring-dynamic-media-cloud-services) in Dynamische media configureren - Scene7-modus en [Problemen met dynamische media oplossen - Scene7-modus.](/help/assets/troubleshoot-dms7.md)

1. **3D-elementen uploaden**

   * [3D-elementen uploaden voor gebruik in dynamische media](/help/assets/manage-assets.md#uploading-assets).
   * [Ondersteunde 3D-bestandsindelingen voor uploaden in Dynamic Media](#supported-three-d-file-formats-in-dm).

1. **3D-middelen beheren**

   * 3D-middelen organiseren en doorzoeken

      * [Digitale elementen](/help/assets/organize-assets.md#organize-digital-assets) ordenen.
      * [3D-elementen](/help/assets/search-assets.md) zoeken.
      * [Met aangepaste voorspelling kunt u zoekresultaten](/help/assets/search-assets.md#custompredicates) filteren.
   * 3D-elementen weergeven

      * [3D-elementen](#viewing-three-d-assets) bekijken en ermee werken.
      * [De voorinstelling](/help/assets/managing-viewer-presets.md) voor de dimensionale viewer beheren.
   * Werken met metagegevens van 3D-elementen

      * [Metagegevens voor digitale elementen](/help/assets/metadata.md) beheren.
      * [Metagegevensschema&#39;s](/help/assets/metadata-schemas.md).



1. **3D-elementen publiceren**

   * [Statische dynamische media 3D-elementen publiceren](#publishing-three-d-assets)
   * [Alternatieve methoden voor het publiceren van Dynamic Media 3D-elementen met behulp van de Dimensional-viewer](#alternate-publish-methods)

## Informatie over het weergeven van en communiceren met 3D-elementen {#viewing-three-d-assets}

In deze sectie wordt beschreven hoe u 3D-elementen op twee verschillende manieren kunt weergeven en gebruiken: vanuit de pagina met elementdetails en vanuit de 3D-mediacomponent in Sites.

De interactieve 3D-viewer bevat onder andere een verzameling interactieve besturingselementen voor camera waarmee u het 3D-element kunt draaien, zoomen en pannen.

Houd er rekening mee dat de tijd die nodig is om een 3D-element te openen in de paginaweergave Asset Details afhankelijk is van verschillende factoren. Deze factoren zijn onder andere:

* Bandbreedte voor de server.
* Koppelingen naar de server
* Complexiteit van de afbeelding.

Bovendien zijn de mogelijkheden van de clientcomputer, zoals een werkstation, laptop of mobiel aanraakapparaat, ook belangrijk om te overwegen wanneer u de camera interactief manipuleert. Een redelijk krachtig systeem met goede grafische mogelijkheden kan de interactieve 3D-kijkervaring vloeiender en gunstiger maken.

>[!TIP]
>
>U kunt de voorinstelling voor de maatviewer openen in de Viewer Preset Editor om te navigeren door een 3D-element zonder dat u eerst 3D-bestanden hoeft te uploaden. De voorinstelling van de DIMM-viewer heeft een ingebouwd 3D-element waarmee u kunt communiceren.
>
>Zie [Voorinstellingen voor viewers beheren.](/help/assets/managing-viewer-presets.md)

## Een 3D-element weergeven en interactief gebruiken op de pagina {#viewing-three-d-assets-from-asset-details-page} met elementdetails

Zie ook [Elementen voorvertonen met behulp van de softwareinterface](/help/assets/previewing-assets.md).

**Een 3D-element weergeven en interactief werken via de pagina met elementdetails**

1. Zorg ervoor dat u 3D-elementen hebt geüpload naar AEM.

   Zie [Uw 3D-elementen uploaden voor gebruik in dynamische media.](/help/assets/manage-assets.md#uploading-assets)

1. Tik vanaf AEM op de pagina **[!UICONTROL Navigation]** op **[!UICONTROL Assets > Files.]**
1. Tik in de rechterbovenhoek van de pagina in de vervolgkeuzelijst **[!UICONTROL View]** op **[!UICONTROL Card View.]**
1. Navigeer naar een 3D-element dat u wilt weergeven.
1. Tik op de kaart van het 3D-element om dit te openen op de pagina met elementdetails.
1. Voer op de pagina met de detailweergave voor het 3D-element een van de volgende handelingen uit:

   * **Draai uw camera**  - Draai uw weergave rond de 3D-scène en de objecten.
      * _Muis_: Klik met de linkermuisknop en sleep.
      * _Aanraakscherm_: Druk met één vinger en sleep.
   * **Pannen met uw camera** : pannen met uw weergave naar links, rechts, omhoog of omlaag.
      * _Muis_: Klik met de rechtermuisknop en sleep.
      * _Aanraakscherm_: Druk met twee vingers en sleep.
   * **Zoom de camera**  in en uit. Zoom de camera in en uit de gebieden van de 3D-scène.
      * _Muis_: Schuifwiel.
      * _Aanraakscherm_: Kneep met twee vingers.
   * **Start de camera**  opnieuw op - centreer de camera opnieuw op een punt op een object in de 3D-scène.
      * _Muis_: Dubbelklik.
      * _Aanraakscherm_: Dubbeltik.
   * **Herstellen**  - Tik in de rechterbenedenhoek van de pagina op het pictogram Herstellen om het doelpunt van de weergave te herstellen naar het midden van het 3D-element. Met Herstellen wordt de camera ook dichter bij of verder weg geplaatst om het middel volledig en bij een redelijke weergavegrootte weer te geven.
   * **Modus**  Volledig scherm - Tik op het pictogram Volledig scherm om de modus Volledig scherm te activeren, in de rechterbenedenhoek van de pagina.

1. Tik in de rechterbovenhoek van de pagina op **[!UICONTROL Close]** om terug te keren naar de pagina Middelen.

## Een 3D-element in een 3D-mediacomponent {#interacting-with-asset-inside-three-d-media-component} weergeven en hiermee communiceren

Wanneer een webpagina in de modus **[!UICONTROL Edit]** staat, is interactie met een 3D-element niet mogelijk. Als u het element interactief wilt maken, kunt u de functie **[!UICONTROL Preview]** gebruiken om de webpagina in de pagina-editor weer te geven met volledige toegang tot de functionaliteit van de 3D Media-component.

>[!IMPORTANT]
>
>U kunt deze taak pas uitvoeren nadat u een 3D-mediacomponent aan een webpagina hebt toegevoegd en een 3D-element aan de component hebt toegewezen. Zie [De 3D-mediacomponent toevoegen aan een webpagina](#adding-the-three-d-media-component-to-a-web-page) en [Een 3D-element toewijzen aan een 3D-mediacomponent.](#assigning-a-three-d-asset-to-the-component)

Zie ook [Elementen voorvertonen met behulp van de softwareinterface.](/help/assets/previewing-assets.md)

**Een 3D-element in een 3D-mediacomponent weergeven en ermee werken**

1. Voer een van de volgende handelingen uit terwijl de modus **[!UICONTROL Edit]** voor een webpagina is geactiveerd:

   * Rechtsboven op de pagina klikt u op **[!UICONTROL Preview]** om de modus **[!UICONTROL Preview]** te activeren.
   * Verwijder `/editor.html` uit de pagina-URL in de browser.

Een volledig interactief 3D-element zoals weergegeven in    ![3D-element dat in de 3D Media-](/help/assets/assets-dm/3d-asset-in-3d-media.png)
componentA volledig interactief 3D-element wordt weergegeven, zoals in de  **[!UICONTROL Preview]** modus wordt weergegeven.

1. Voer in de modus **[!UICONTROL Preview]** een van de volgende handelingen uit:

   * **Draai uw camera**  - Draai uw weergave rond de 3D-scène en de objecten.
      * _Muis_: Klik met de linkermuisknop en sleep.
      * _Aanraakscherm_: Druk met één vinger en sleep.
   * **Pannen met uw camera** : pannen met uw weergave naar links, rechts, omhoog of omlaag.
      * _Muis_: Klik met de rechtermuisknop en sleep.
      * _Aanraakscherm_: Druk met twee vingers en sleep.
   * **Zoom de camera**  in en uit. Zoom de camera in en uit de gebieden van de 3D-scène.
      * _Muis_: Schuifwiel.
      * _Aanraakscherm_: Kneep met twee vingers.
   * **Start de camera**  opnieuw op - centreer de camera opnieuw op een punt op een object in de 3D-scène.
      * _Muis_: Dubbelklik.
      * _Aanraakscherm_: Dubbeltik.
   * **Herstellen**  - Tik in de rechterbenedenhoek van de pagina op het pictogram Herstellen om het doelpunt van de weergave te herstellen naar het midden van het 3D-element. Met Herstellen wordt de camera ook dichter bij of verder weg geplaatst om het middel volledig en bij een redelijke weergavegrootte weer te geven.
   * **Modus**  Volledig scherm - Tik op het pictogram Volledig scherm om de modus Volledig scherm te activeren, in de rechterbenedenhoek van de pagina.

## Informatie over het werken met de 3D-mediacomponent {#working-with-three-d-media-component}

Dynamic Media bevat een Dynamic Media 3D Media-component die u in AEM Sites kunt gebruiken om interactieve weergave van 3D-modellen op uw webpagina&#39;s mogelijk te maken.

* [De 3D-mediacomponent toevoegen aan de paginasjabloon](#adding-three-d-media-component-to-page-template)
* [De 3D-mediacomponent toevoegen aan een webpagina](#adding-the-three-d-media-component-to-a-web-page)
   * [Optioneel - De 3D-mediacomponent configureren](#configuring-the-three-d-component)
* [Een 3D-element toewijzen aan de 3D-mediacomponent](#assigning-a-three-d-asset-to-the-component)


## De 3D-mediacomponent toevoegen aan de paginasjabloon {#adding-three-d-media-component-to-page-template}

1. Ga naar **[!UICONTROL Tools > General > Templates.]**
1. Navigeer naar de paginasjabloon waarin u de 3D-component wilt inschakelen en selecteer de sjabloon.
1. Tik **[!UICONTROL Edit]** om de sjabloon te openen.
1. Selecteer in de rechterbovenhoek van de pagina **[!UICONTROL Structure]**-modus in het keuzemenu als deze nog niet actief is.

   ![3d-media-component-structuur](/help/assets/assets-dm/3d-media-component-structure.png)

1. Tik op een leeg gebied in het gebied **[!UICONTROL Layout Container]** om het te selecteren en de bijbehorende werkbalk te openen.
1. Tik op het pictogram **[!UICONTROL Policy]** op de werkbalk om **[!UICONTROL Policy Editor.]** te openen
1. Blader in de sectie **[!UICONTROL Properties]** onder de tab **[!UICONTROL Allowed Components]** naar **[!UICONTROL Dynamic Media]**, vouw vervolgens de lijst uit en controleer **[!UICONTROL 3D Media.]**
1. Tik **[!UICONTROL Done]** om de wijzigingen op te slaan en **[!UICONTROL Policy Editor.]** te sluiten

   U kunt de component Dynamische media 3D Media nu op alle pagina&#39;s plaatsen die dit malplaatje gebruiken.

## De 3D-mediacomponent toevoegen aan een webpagina {#adding-the-three-d-media-component-to-a-web-page}

Als u Adobe Experience Manager gebruikt als het webcontentbeheersysteem, kunt u 3D-elementen aan uw webpagina&#39;s toevoegen met behulp van de 3D Media-component.

Zie ook [Dynamische media-elementen toevoegen aan pagina&#39;s.](/help/assets/adding-dynamic-media-assets-to-pages.md)

1. Open AEM Sites en selecteer de webpagina waaraan u de Dynamic Media 3D Media-component wilt toevoegen.
1. Tik op het pictogram **[!UICONTROL Edit]** (potlood) om de pagina in de paginaeditor te openen. Zorg ervoor dat de modus **[!UICONTROL Edit]** rechtsboven op de pagina is geselecteerd.

   ![3d-media-component-add](/help/assets/assets-dm/3d-media-component-edit.png)

1. Tik op het pictogram Zijpaneel op de werkbalk om de weergave van het deelvenster in of uit te schakelen.

1. Tik in het zijpaneel op het plusteken om de lijst **[!UICONTROL Components]** te openen.

   ![3d-media-component-slepen-neerzetten](/help/assets/assets-dm/3d-assets-filter.png)

1. Sleep de component **[!UICONTROL 3D Media]** van de lijst **[!UICONTROL Components]** naar de locatie op de pagina waar u de 3D-viewer wilt weergeven.

U kunt nu een 3D-element aan de component toewijzen.

Zie [Een 3D-element toewijzen aan een 3D-mediacomponent.](#assigning-a-three-d-asset-to-the-component)

### Optioneel - De 3D-mediacomponent {#configuring-the-three-d-component} configureren

1. Selecteer in de AEM Sites-pagina-editor de **[!UICONTROL 3D Media Viewer]**-component die u eerder aan de pagina hebt toegevoegd.
1. Tik op het pictogram **[!UICONTROL Configuration]** (moersleutel) om het dialoogvenster voor componentconfiguratie te openen.

   ![3d-media-component-config](/help/assets/assets-dm/3d-media-component-config.png)

1. Selecteer in het dialoogvenster 3D-media in de vervolgkeuzelijst Voorinstelling viewer de optie **[!UICONTROL Dimensional]** om de voorinstelling voor de maatviewer toe te wijzen aan de component.

   ![3d-media-component-edit-config](/help/assets/assets-dm/3d-media-component-edit-config.png)

1. Tik in de rechterbovenhoek op het vinkje om de wijzigingen op te slaan.

## 3D-elementen toewijzen aan de 3D-mediacomponent {#assigning-a-three-d-asset-to-the-component}

Nadat u een 3D-mediacomponent aan een webpagina hebt toegevoegd, kunt u er een 3D-element aan toewijzen.

Zie [De 3D-mediacomponent toevoegen aan een webpagina.](#adding-the-three-d-media-component-to-a-web-page)

1. Klik in de AEM Sites-pagina-editor op het pictogram **[!UICONTROL Assets]** om **[!UICONTROL Assets]** in het zijpaneel te openen.
1. Selecteer **[!UICONTROL 3D]** in de vervolgkeuzelijst om alleen 3D-elementbestandstypen weer te geven.
1. Zoek in het zijpaneel naar het 3D-element dat u wilt weergeven op de pagina die u bewerkt.
1. Sleep het 3D-element van het zijpaneel Middelen naar de **[!UICONTROL 3D Media]**-component die u eerder aan de pagina hebt toegevoegd.

   ![3D-element toewijzen aan 3d-mediacomponent](/help/assets/assets-dm/3d-asset-add.png)

>[!NOTE]
>
>In de AEM Sites-modus **[!UICONTROL Edit]** wordt het 3D-element weergegeven in de 3D-mediacomponent, maar interactie met het element is niet mogelijk. Als u het element interactief wilt maken, kunt u de functie **[!UICONTROL Preview]** gebruiken om de webpagina in de pagina-editor weer te geven met volledige toegang tot de functionaliteit van de 3D Media-component.

## Statische dynamische media 3D-elementen publiceren {#publishing-three-d-assets}

Dynamische media accepteert verschillende 3D-bestandsindelingen die worden ondersteund als *statische inhoud* in dynamische media. Statische inhoud houdt in dat u 3D-elementen kunt uploaden en publiceren, maar dat er geen ondersteuning is voor *dynamic*-beeldbewerking of het vernieuwen van afbeeldingen die aan het 3D-element zijn gekoppeld. De reden hiervoor is dat Dynamic Media Imaging Server 3D-indelingen niet herkent. Nadat u een 3D-element hebt gepubliceerd in dynamische media, hebt u dus een directe URL die u kunt kopiëren. De URL voor het 3D-element volgt de gebruikelijke URL-structuur voor dynamische media. In tegenstelling tot traditionele afbeeldingselementen in Dynamic Media kunt u echter geen parameters in de URL van het element bewerken.

Zie ook [Een URL verkrijgen voor een statisch element.](/help/assets/linking-urls-to-yourwebapplication.md#obtaining-a-url-for-a-static-asset)

In **[!UICONTROL Card View]** verschijnt een klein globpictogram direct onder de naam van een element en links van zijn datum en tijd om erop te wijzen dat het wordt gepubliceerd. In de **[!UICONTROL List View]** geeft een kolom **[!UICONTROL Published]** aan welke assets zijn gepubliceerd en welke niet.

Als u AEM als WCM gebruikt, gebruikt u deze publicatiemethode om de Dynamic Media 3D-elementen rechtstreeks op uw webpagina toe te voegen.

Zie ook [Dynamische media-elementen publiceren.](publishing-dynamicmedia-assets.md)

Zie ook [Pagina&#39;s publiceren.](/help/sites-authoring/publishing-pages.md)

**Statische dynamische media 3D-elementen publiceren**

1. Open een 3D-element (GLB-, OBJ- of STL-bestandsindeling) om dit weer te geven op de pagina met elementdetails.
1. Tik op **[!UICONTROL Quick Publish.]** op de werkbalk

   ![3d-asset-quick-publish](/help/assets/assets-dm/3d-asset-quick-publish.png)

1. Tik op **[!UICONTROL Close]** om het dialoogvenster te sluiten en terug te keren naar de pagina met elementdetails.
1. Tik in de vervolgkeuzelijst links van de bestandsnaam van het 3D-element op **[!UICONTROL Renditions.]**

   ![3d-asset-renditions](/help/assets/assets-dm/3d-asset-renditions.png)

1. Tik **[!UICONTROL original.]** Als een 3D-element wordt gepubliceerd (of &quot;geactiveerd&quot;) op de knop **[!UICONTROL URL]** in de linkerbenedenhoek van de pagina als aan alle volgende 3D-elementvoorwaarden wordt voldaan:
   * Het 3D-element heeft een ondersteunde indeling (GLB, OBJ, STL en USDZ).
   * Het 3D element werd opgenomen in het Dynamische Systeem van de Productie van het Beeld van Media (IPS).
   * Het 3D-element wordt gepubliceerd.

   ![3d-asset-url](/help/assets/assets-dm/3d-asset-url.png)

1. Tik **[!UICONTROL URL]** om de directe productie-URL van het 3D-element weer te geven, die u kunt kopiëren en gebruiken op webpagina&#39;s.

### Alternatieve methoden voor het publiceren van dynamische media 3D-elementen met behulp van de Dimensional-viewer {#alternate-publish-methods}

Gebruik de volgende twee methoden voor het publiceren van Dynamic Media 3D-elementen als u *geen* bent en AEM gebruikt als uw WCM.

* **[!UICONTROL URL]** - Gebruik deze optie  **[!UICONTROL URL]** als u een systeem voor webcontentbeheer van derden gebruikt en u dynamische media 3D-elementen wilt koppelen aan uw webpagina&#39;s met de DIMM-viewer.

   Zie [URL&#39;s koppelen aan uw webtoepassing.](/help/assets/linking-urls-to-yourwebapplication.md#obtaining-a-url-for-an-asset)

* **[!UICONTROL Embed]** - Gebruik deze optie  **[!UICONTROL Embed]** als u een dynamisch Media 3D-element wilt weergeven dat is ingesloten op een webpagina met de DIMM-viewer. U kopieert de insluitcode naar het klembord, zodat u deze op uw webpagina&#39;s kunt plakken. Het bewerken van de code is niet toegestaan in het dialoogvenster **[!UICONTROL Embed]**.

   Zie [De dynamische mediavideo, de afbeeldingsviewer of de dimensionale viewer insluiten op een webpagina.](/help/assets/embed-code.md#embedding-the-video-or-image-viewer-on-a-web-page)