---
title: Werken met 3D-elementen in Dynamic Media
description: Leer hoe u 3D-middelen in Dynamic Media kunt uploaden, beheren, weergeven en leveren als een indrukwekkende ervaring.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: introduction
content-type: reference
feature: 3D Assets,Asset Management
role: User, Admin
exl-id: 01c96f1e-c0e6-497d-bd7a-c0fd547a34da
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '2283'
ht-degree: 1%

---

# Werken met 3D-middelen in Dynamic Media {#working-with-three-d-assets-dm}

Met Dynamic Media kunt u 3D-middelen uploaden, beheren, weergeven en leveren als een indrukwekkende ervaring.

* Publiceren met één klik (gebruiken **[!UICONTROL Quick Publish]** op de werkbalk) van 3D-middelen om een URL te genereren.
* Geoptimaliseerde ondersteuning voor het weergeven van 3D-middelen met de voorinstelling voor interactieve maatviewer van hoge kwaliteit, aangedreven door Adobe Dimension.
* Met de 3D Media WCM-component kunt u eenvoudig 3D-elementen toevoegen aan uw Adobe Experience Manager Sites-pagina&#39;s.

Er is geen aanvullende configuratie vereist voor het gebruik van 3D-elementen in Dynamic Media.

![Schoen in 3d](/help/assets/assets-dm/3d-dimensional-viewer-quickpublish-url-embed2.png) *De pagina van details van een driedimensionale schoen.*

<!-- See also [Dynamic Media 3D Release Notes](/help/release-notes/aem3d-release-notes.md). -->

## 3D-indelingen ondersteund in Dynamic Media {#supported-three-d-file-formats-in-dm}

Dynamic Media ondersteunt de volgende 3D-indelingen.

Zie ook [Ondersteunde 3D-indelingen](/help/assets/assets-formats.md).

| 3D-bestandsextensie | Bestandsindeling | MIME-type | Notities |
|---|---|---|---|
| GLB | Binaire GL-transmissie | model/gltf-binair | Hiermee neemt u de materialen en structuren op als één enkel element. |
| OBJ | WaveFront 3D-objectbestand | application/x-tgif |  |
| STL | Stereolithografie | application/vnd.ms-pki.stl |  |
| USDZ | Universal Scene Description Zip-archief | model/vnd.usdz+zip | *Alleen ondersteuning voor inname; geen weergave of interactie is beschikbaar.* USDZ is een eigen 3D-indeling die door Safari- en iOS-apparaten kan worden weergegeven. |

>[!NOTE]
>
>De 3D Media WCM-component en de 3D-voorvertoning op de pagina Details van een element zijn niet compatibel met de nieuwste versie van Chrome (97.x). Als u met 3D-elementen wilt werken, gebruikt u Firefox of Safari of een eerdere versie van Chrome (96.x).

## Snel starten: 3D-middelen in Dynamic Media {#quick-start-three-d}

De volgende stapsgewijze beschrijving van de workflow is ontworpen om u te helpen snel aan de slag te gaan met 3D-middelen in de Dynamic Media-Scene7-modus.

>[!IMPORTANT]
>
>3D-elementen worden niet ondersteund in de Dynamic Media-hybride modus.

Voordat u in Dynamic Media met 3D-middelen gaat werken, moet u ervoor zorgen dat de beheerder van de Experience Manager Dynamic Media-Cloud Servicen al heeft ingeschakeld en geconfigureerd in de Dynamic Media - Scene7-modus.

Zie [ConfigurE Dynamic Media-Cloud Servicen](/help/assets/config-dms7.md#configuring-dynamic-media-cloud-services) in De modus Dynamic Media configureren - Scene7 en [Problemen met Dynamic Media oplossen - Scene7-modus](/help/assets/troubleshoot-dms7.md).

1. **3D-elementen uploaden**

   * [Uw 3D-elementen uploaden voor gebruik in Dynamic Media](/help/assets/manage-assets.md#uploading-assets).
   * [Ondersteunde 3D-bestandsindelingen voor uploaden in Dynamic Media](#supported-three-d-file-formats-in-dm).

1. **3D-middelen beheren**

   * 3D-middelen organiseren en doorzoeken

      * [Digitale elementen ordenen](/help/assets/organize-assets.md#organize-digital-assets).
      * [3D-middelen zoeken](/help/assets/search-assets.md).
      * [Aangepaste voorspelling gebruiken om zoekresultaten te filteren](/help/assets/search-assets.md#custompredicates).

   * 3D-elementen weergeven

      * [3D-elementen weergeven en communiceren](#viewing-three-d-assets).
      * [De voorinstelling voor de dimensionale viewer beheren](/help/assets/managing-viewer-presets.md).

   * Werken met metagegevens van 3D-elementen

      * [Metagegevens voor digitale elementen beheren](/help/assets/metadata.md).
      * [Metagegevensschema&#39;s](/help/assets/metadata-schemas.md).

1. **3D-elementen publiceren**

   * [Statische Dynamic Media 3D-elementen publiceren](#publishing-three-d-assets)
   * [Alternatieve methoden voor het publiceren van Dynamic Media 3D-elementen met de Dimensional-viewer](#alternate-publish-methods)

## Informatie over het weergeven van en communiceren met 3D-elementen {#viewing-three-d-assets}

In deze sectie wordt beschreven hoe u 3D-elementen op twee verschillende manieren kunt weergeven en gebruiken: van binnen de pagina met elementdetails en van binnen de 3D-mediacomponent in Experience Manager Sites.

De interactieve 3D-viewer bevat onder andere een verzameling interactieve besturingselementen voor camera waarmee u het 3D-element kunt draaien, zoomen en pannen.

De tijd die nodig is om een 3D-element te openen in de weergave Asset Details is afhankelijk van verschillende factoren. Deze factoren zijn onder andere:

* Bandbreedte voor de server.
* Koppelingen naar de server
* Complexiteit van de afbeelding.

Bovendien zijn de mogelijkheden van de clientcomputer, zoals een werkstation, laptop of mobiel aanraakapparaat, ook belangrijk om te overwegen wanneer u de camera interactief manipuleert. Een redelijk krachtig systeem met goede grafische mogelijkheden kan de interactieve 3D-kijkervaring vloeiender en gunstiger maken.

>[!TIP]
>
>U kunt de voorinstelling voor de maatviewer openen in de Viewer Preset Editor om te navigeren door een 3D-element zonder dat u eerst 3D-bestanden hoeft te uploaden. De voorinstelling van de DIMM-viewer heeft een ingebouwd 3D-element waarmee u kunt communiceren.
>
>Zie [Voorinstellingen voor viewers beheren](/help/assets/managing-viewer-presets.md).

## Een 3D-element weergeven en interactief werken via de pagina met elementdetails {#viewing-three-d-assets-from-asset-details-page}

Zie ook [Elementen voorvertonen met de software-interface](/help/assets/previewing-assets.md).

**U kunt als volgt een 3D-element weergeven en ermee werken op de pagina met elementdetails:**

1. Zorg ervoor dat u 3D-elementen hebt geüpload naar de Experience Manager.

   Zie [Uw 3D-elementen uploaden voor gebruik in Dynamic Media](/help/assets/manage-assets.md#uploading-assets).

1. Van Experience Manager, op **[!UICONTROL Navigation]** pagina, ga naar **[!UICONTROL Assets]** > **[!UICONTROL Files]**.
1. In de rechterbovenhoek van de pagina, vanaf de **[!UICONTROL View]** vervolgkeuzelijst, selecteert u **[!UICONTROL Card View]**.
1. Navigeer naar een 3D-element dat u wilt weergeven.
1. Selecteer de kaart van het 3D-element.
1. Voer op de pagina met de detailweergave voor het 3D-element een van de volgende handelingen uit:

   | Weergave | Beschrijving | Muishandeling | Handeling op het aanraakscherm |
   | --- | --- | --- | --- |
   | **De camera draaien** | Draai de weergave rond de 3D-scène en -objecten. | Klik met de linkermuisknop en sleep. | Druk met één vinger en sleep. |
   | **Uw camera pannen** | U kunt de weergave naar links, rechts, omhoog of omlaag pannen. | Klik met de rechtermuisknop en sleep. | Druk met twee vingers en sleep. |
   | **Uw camera zoomen** | Ga in- en uit gebieden in de 3D-scène. | Schuifwiel. | Kneep met twee vingers. |
   | **De camera opnieuw opnemen** | Voer de camera opnieuw in op een punt op een object in de 3D-scène. | Dubbelklik. | Dubbelselecteren. |
   | **Herstellen** | Selecteer in de rechterbenedenhoek van de pagina het pictogram Herstellen om het doelpunt van de weergave te herstellen naar het midden van het 3D-element. Met Herstellen wordt de camera ook dichter bij of verder weg geplaatst om het middel volledig en bij een redelijke weergavegrootte weer te geven. |   |   |
   | **Modus Volledig scherm** | Als u de modus Volledig scherm wilt inschakelen, selecteert u in de rechterbenedenhoek van de pagina het pictogram Volledig scherm. |   |   |

1. Selecteer in de rechterbovenhoek van de pagina de optie **[!UICONTROL Close]** om terug te keren naar de middelenpagina.

## Een 3D-element in een 3D-mediacomponent weergeven en hiermee communiceren {#interacting-with-asset-inside-three-d-media-component}

Wanneer een webpagina zich in **[!UICONTROL Edit]** is geen interactie mogelijk met een 3D-element. Als u het element interactief wilt maken, kunt u de opdracht **[!UICONTROL Preview]** gebruiken om de webpagina in de pagina-editor weer te geven met volledige toegang tot de functionaliteit van de 3D-mediacomponent.

>[!IMPORTANT]
>
>U kunt deze taak pas uitvoeren nadat u een 3D-mediacomponent aan een webpagina hebt toegevoegd en een 3D-element aan de component hebt toegewezen. Zie [De 3D-mediacomponent toevoegen aan een webpagina](#adding-the-three-d-media-component-to-a-web-page) en [Een 3D-element toewijzen aan een 3D-mediacomponent](#assigning-a-three-d-asset-to-the-component).

Zie ook [Elementen voorvertonen met de software-interface](/help/assets/previewing-assets.md).

**Een 3D-element in een 3D-mediacomponent weergeven en hiermee werken:**

1. Terwijl een webpagina zich in **[!UICONTROL Edit]** Voer een van de volgende handelingen uit in de modus:

   * Selecteer rechtsboven op de pagina de optie **[!UICONTROL Preview]** om binnen te gaan **[!UICONTROL Preview]** -modus.
   * Verwijderen `/editor.html` van de pagina-URL in de browser.

   ![3D-element weergeven binnen de 3D-mediacomponent](/help/assets/assets-dm/3d-asset-in-3d-media.png)
Een volledig interactief 3D-element zoals weergegeven in **[!UICONTROL Preview]** -modus.

1. Tijdens het aanmelden **[!UICONTROL Preview]** Voer een van de volgende handelingen uit in de modus:

   | Weergave | Beschrijving | Muishandeling | Handeling op het aanraakscherm |
   | --- | --- | --- | --- |
   | **De camera draaien** | Draai de weergave rond de 3D-scène en -objecten. | Klik met de linkermuisknop en sleep. | Druk met één vinger en sleep. |
   | **Uw camera pannen** | U kunt de weergave naar links, rechts, omhoog of omlaag pannen. | Klik met de rechtermuisknop en sleep. | Druk met twee vingers en sleep. |
   | **Uw camera zoomen** | Ga in- en uit gebieden in de 3D-scène. | Schuifwiel. | Kneep met twee vingers. |
   | **De camera opnieuw opnemen** | Voer de camera opnieuw in op een punt op een object in de 3D-scène. | Dubbelklik. | Dubbelselecteren. |
   | **Herstellen** | Selecteer in de rechterbenedenhoek van de pagina het pictogram Herstellen om het doelpunt van de weergave te herstellen naar het midden van het 3D-element. Met Herstellen wordt de camera ook dichter bij of verder weg geplaatst om het middel volledig en bij een redelijke weergavegrootte weer te geven. |   |   |
   | **Modus Volledig scherm** | Als u de modus Volledig scherm wilt inschakelen, selecteert u in de rechterbenedenhoek van de pagina het pictogram Volledig scherm. |   |   |

## Informatie over het werken met de 3D-mediacomponent {#working-with-three-d-media-component}

Dynamic Media bevat een Dynamic Media 3D Media-component die u in Adobe Experience Manager Sites kunt gebruiken om interactieve weergave van 3D-modellen op uw webpagina&#39;s mogelijk te maken.

* [De 3D-mediacomponent toevoegen aan de paginasjabloon](#adding-three-d-media-component-to-page-template)
* [De 3D-mediacomponent toevoegen aan een webpagina](#adding-the-three-d-media-component-to-a-web-page)
   * [Optioneel - De 3D-mediacomponent configureren](#configuring-the-three-d-component)
* [Een 3D-element toewijzen aan de 3D-mediacomponent](#assigning-a-three-d-asset-to-the-component)

## De 3D-mediacomponent toevoegen aan de paginasjabloon {#adding-three-d-media-component-to-page-template}

1. Navigeren naar **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL Templates]**.
1. Navigeer naar de paginasjabloon waarin u de 3D-component wilt inschakelen en selecteer de sjabloon.
1. Selecteren **[!UICONTROL Edit]** zodat u de sjabloon kunt openen.
1. Selecteer in de rechterbovenhoek van de pagina in het keuzemenu de optie **[!UICONTROL Structure]** als deze nog niet actief is.

   ![3d-media-component-structuur](/help/assets/assets-dm/3d-media-component-structure.png)

1. Een leeg gebied selecteren in het dialoogvenster **[!UICONTROL Layout Container]** gebied zodat selecteert u het en opent u de bijbehorende werkbalk.
1. Selecteer op de werkbalk de optie **[!UICONTROL Policy]** pictogram om het **[!UICONTROL Policy Editor]**.
1. In de **[!UICONTROL Properties]** , onder **[!UICONTROL Allowed Components]** tab, schuiven naar **[!UICONTROL Dynamic Media]** Vouw vervolgens de lijst uit en controleer **[!UICONTROL 3D Media]**.
1. Selecteren **[!UICONTROL Done]** om de wijzigingen op te slaan en het dialoogvenster **[!UICONTROL Policy Editor]**.

   U kunt de Dynamic Media 3D Media-component nu op alle pagina&#39;s plaatsen die deze sjabloon gebruiken.

## De 3D Media-component toevoegen aan een webpagina {#adding-the-three-d-media-component-to-a-web-page}

Als u Experience Manager gebruikt als het webcontentbeheersysteem, kunt u 3D-elementen toevoegen aan uw webpagina&#39;s via de 3D Media-component.

Zie ook [Dynamic Media-elementen toevoegen op pagina&#39;s](/help/assets/adding-dynamic-media-assets-to-pages.md).

**De 3D-mediacomponent toevoegen aan een webpagina:**

1. Open Experience Manager Sites en selecteer de webpagina waaraan u de Dynamic Media 3D Media-component wilt toevoegen.
1. Selecteer de **[!UICONTROL Edit]** (potlood), zodat u de pagina kunt openen in de pagina-editor. Controleer of **[!UICONTROL Edit]** wordt rechtsboven op de pagina geselecteerd.

   ![3d-media-component-add](/help/assets/assets-dm/3d-media-component-edit.png)

1. Selecteer op de werkbalk het pictogram Zijpaneel om de weergave van het deelvenster in of uit te schakelen.

1. Selecteer in het zijpaneel het pictogram met het plusteken om het dialoogvenster **[!UICONTROL Components]** lijst.

   ![3d-media-component-slepen-neerzetten](/help/assets/assets-dm/3d-assets-filter.png)

1. Sleep de **[!UICONTROL 3D Media]** uit de **[!UICONTROL Components]** Hiermee geeft u een lijst weer naar de locatie op de pagina waar u de 3D-viewer wilt weergeven.

U kunt nu een 3D-element aan de component toewijzen.

Zie [Een 3D-element toewijzen aan de 3D-mediacomponent](#assigning-a-three-d-asset-to-the-component).

### Optioneel - De 3D-mediacomponent configureren {#configuring-the-three-d-component}

1. Selecteer in de Experience Manager Sites-pagina-editor de optie **[!UICONTROL 3D Media Viewer]** die u eerder aan de pagina hebt toegevoegd.
1. Selecteer de **[!UICONTROL Configuration]** pictogram (moersleutel) zodat u het dialoogvenster voor componentconfiguratie kunt openen.

   ![3d-media-component-config](/help/assets/assets-dm/3d-media-component-config.png)

1. Selecteer in het dialoogvenster 3D-media in de vervolgkeuzelijst Voorinstelling viewer de optie **[!UICONTROL Dimensional]** om de voorinstelling voor de maatviewer toe te wijzen aan de component.

   ![3d-media-component-edit-config](/help/assets/assets-dm/3d-media-component-edit-config.png)

1. Selecteer in de rechterbovenhoek het vinkje waarop u de wijzigingen wilt opslaan.

## Een 3D-element toewijzen aan de 3D-mediacomponent {#assigning-a-three-d-asset-to-the-component}

Nadat u een 3D-mediacomponent aan een webpagina hebt toegevoegd, kunt u er een 3D-element aan toewijzen.

Zie [De 3D-mediacomponent toevoegen aan een webpagina](#adding-the-three-d-media-component-to-a-web-page).

**Een 3D-element toewijzen aan de 3D-mediacomponent:**

1. Selecteer in de Experience Manager Sites-pagina-editor de optie **[!UICONTROL Assets]** pictogram om te openen **[!UICONTROL Assets]** in het zijpaneel.
1. Selecteer in de vervolgkeuzelijst de optie **[!UICONTROL 3D]** alleen 3D-elementbestandstypen weergeven.
1. Zoek in het zijpaneel naar het 3D-element dat u wilt weergeven op de pagina die u bewerkt.
1. Sleep het 3D-element van het zijpaneel Middelen naar het deelvenster **[!UICONTROL 3D Media]** die u eerder aan de pagina hebt toegevoegd.

   ![3D-element toewijzen aan de 3D-mediacomponent](/help/assets/assets-dm/3d-asset-add.png)

>[!NOTE]
>
>Terwijl een webpagina zich in de Experience Manager Sites bevindt **[!UICONTROL Edit]** In de 3D-mediacomponent wordt het 3D-element weergegeven, maar interactie met het element is niet mogelijk. Als u het element interactief wilt maken, kunt u de opdracht **[!UICONTROL Preview]** gebruiken om de webpagina in de pagina-editor weer te geven met volledige toegang tot de functionaliteit van de 3D-mediacomponent.

## Statische Dynamic Media 3D-elementen publiceren {#publishing-three-d-assets}

Dynamic Media accepteert verschillende 3D-bestandsindelingen die worden ondersteund als *statische inhoud* in Dynamic Media. Statische inhoud betekent dat u 3D-elementen kunt uploaden en publiceren, maar dat er geen ondersteuning is voor *variabele beeldbewerking* of het vernieuwen van afbeeldingen die aan het 3D-element zijn gekoppeld. De reden hiervoor is dat Dynamic Media Imaging Server 3D-indelingen niet herkent. Nadat u een 3D-element hebt gepubliceerd in Dynamic Media, hebt u dus een directe URL die u kunt kopiëren. De URL voor het 3D-element volgt de gebruikelijke URL-structuur van Dynamic Media. In tegenstelling tot traditionele afbeeldingselementen in Dynamic Media kunt u echter geen parameters in de URL van het element bewerken.

Zie ook [Een URL verkrijgen voor een statisch element](/help/assets/linking-urls-to-yourwebapplication.md#obtaining-a-url-for-a-static-asset).

In de **[!UICONTROL Card View]**, wordt een klein globpictogram direct onder de naam van een element weergegeven en links van de datum en tijd om aan te geven dat het is gepubliceerd. In de **[!UICONTROL List View]** geeft een kolom **[!UICONTROL Published]** aan welke assets zijn gepubliceerd en welke niet.

Als u Experience Manager als uw WCM gebruikt, gebruikt u deze publicatiemethode om de Dynamic Media 3D-elementen rechtstreeks op uw webpagina toe te voegen.

Zie ook [Dynamic Media-elementen publiceren](publishing-dynamicmedia-assets.md).

Zie ook [Pagina&#39;s publiceren](/help/sites-authoring/publishing-pages.md).

**Statische Dynamic Media 3D-elementen publiceren:**

1. Open een 3D-element (GLB-, OBJ- of STL-bestandsindeling), zodat u dit kunt bekijken op de pagina met elementdetails.
1. Selecteer op de werkbalk de optie **[!UICONTROL Quick Publish]**.

   ![3d-asset-quick-publish](/help/assets/assets-dm/3d-asset-quick-publish.png)

1. Selecteren **[!UICONTROL Close]** om het dialoogvenster te sluiten en terug te keren naar de pagina met elementdetails.
1. Selecteer in de vervolgkeuzelijst links van de bestandsnaam van het 3D-element de optie **[!UICONTROL Renditions]**.

   ![3d-asset-renditions](/help/assets/assets-dm/3d-asset-renditions.png)

1. Selecteer **[!UICONTROL original]**. Wanneer een 3D-element wordt gepubliceerd (of geactiveerd), wordt het **[!UICONTROL URL]** wordt linksonder op de pagina weergegeven als aan alle volgende 3D-elementvoorwaarden is voldaan:
   * Het 3D-element heeft een ondersteunde indeling (GLB, OBJ, STL en USDZ).
   * Het 3D-element is opgenomen in het Dynamic Media Image Production System (IPS).
   * Het 3D-element wordt gepubliceerd.

   ![3d-asset-url](/help/assets/assets-dm/3d-asset-url.png)

1. Selecteren **[!UICONTROL URL]** zodat u de directe productie-URL van het 3D-element kunt weergeven, die u kunt kopiëren en gebruiken op webpagina&#39;s.

### Alternatieve methoden voor het publiceren van Dynamic Media 3D-elementen met de Dimensional-viewer {#alternate-publish-methods}

Gebruik de volgende twee methoden voor het publiceren van Dynamic Media 3D-elementen als u dat doet *niet* gebruik Experience Manager als uw WCM.

* **[!UICONTROL URL]** - Gebruik **[!UICONTROL URL]** als u een extern systeem voor webcontentbeheer gebruikt en u Dynamic Media 3D-middelen wilt koppelen aan uw webpagina&#39;s met de DIMM-viewer.

  Zie [URL&#39;s koppelen aan uw webtoepassing](/help/assets/linking-urls-to-yourwebapplication.md#obtaining-a-url-for-an-asset).

* **[!UICONTROL Embed]** - Gebruik **[!UICONTROL Embed]** als u een Dynamic Media 3D-element wilt weergeven dat is ingesloten op een webpagina met de DIMM-viewer. U kopieert de insluitcode naar het klembord, zodat u deze op uw webpagina&#39;s kunt plakken. Het bewerken van de code is niet toegestaan in het dialoogvenster **[!UICONTROL Embed]**.

  Zie [De Dynamic Media Video-, Image Viewer- of Dimensional-viewer insluiten op een webpagina](/help/assets/embed-code.md#embedding-the-video-or-image-viewer-on-a-web-page).
