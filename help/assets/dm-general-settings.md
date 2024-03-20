---
title: Algemene instellingen van Dynamic Media configureren
description: Leer hoe u Algemene instellingen in Dynamic Media beheert. U kunt hier de naam van de publicatieserver en de naam van de oorspronkelijke server instellen en een optie voor het overschrijven van afbeeldingen instellen. Er zijn ook standaard uploadopties voor onscherp maskeren van afbeeldingen en uploadopties voor de manier waarop u PostScript-, Adobe Photoshop-, PDF- en Adobe Illustrator-bestanden wilt verwerken.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: administering
content-type: reference
feature: Image Profiles
role: User, Admin
mini-toc-levels: 4
exl-id: 55cc7c57-87a0-4bfb-b226-36d01d36849a
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '2315'
ht-degree: 0%

---

# Algemene instellingen van Dynamic Media configureren

Configureren **[!UICONTROL Dynamic Media General Settings]** is alleen beschikbaar als:

* Dynamic Media wordt uitgevoerd in de Scene7-modus. Zie [Dynamic Media inschakelen in Scene7-modus](/help/assets/config-dms7.md#enabling-dynamic-media-in-scene-mode).
* U hebt een *bestaand* **[!UICONTROL Dynamic Media Configuration]** (in **[!UICONTROL Cloud Services]**) in Adobe Experience Manager 6.5.11 of hoger. Zie [Een Dynamic Media-configuratie maken in Cloud Servicen](/help/assets/config-dms7.md#configuring-dynamic-media-cloud-services).
* U bent een systeembeheerder van het systeem van de Experience Manager met beheerdervoorrechten.

Dynamic Media General Settings is bedoeld voor gebruik door ervaren ontwikkelaars en programmeurs van websites. Adobe Dynamic Media raadt gebruikers die deze publicatie-instellingen wijzigen aan bekend te zijn met Dynamic Media op Adobe Experience Manager en de basistechnologie voor beeldbewerking.

Bij het aanmaken van accounts verschaft Adobe Dynamic Media automatisch de toegewezen servers voor uw bedrijf. Deze servers worden gebruikt om URL-tekenreeksen voor uw website en toepassingen samen te stellen. Deze URL-aanroepen gelden specifiek voor uw account.

Op de pagina Dynamic Media Publish Setup (Publicatie-instellingen) worden standaardinstellingen vastgelegd die bepalen hoe elementen worden geleverd vanaf Adobe Dynamic Media-servers naar websites of toepassingen. Als er geen instelling is opgegeven, levert de Adobe Dynamic Media-server een element volgens een standaardinstelling die is geconfigureerd op de Dynamic Media Publish Setup-pagina.

Zie ook [Optioneel - Instellingen voor Dynamic Media- en Scene7-modus instellen en configureren](/help/assets/config-dms7.md#optional-setup-and-configuration-of-dynamic-media-scene7-mode-settings) voor meer optionele configuratietaken.

>[!NOTE]
>
>Dynamic Media Classic op Adobe Experience Manager upgraden naar Dynamic Media? De pagina Algemene instellingen en [Publicatie-instelling](/help/assets/dm-publish-settings.md) in Dynamic Media worden vooraf de waarden van uw Dynamic Media Classic-account ingevuld. De uitzonderingen zijn alle waarden die onder de **[!UICONTROL Default upload options]** op de pagina Algemene instellingen. Deze waarden zijn al in Experience Manager. Alle wijzigingen die u onder **[!UICONTROL Default upload options]**, door een van de vijf tabbladen, via de gebruikersinterface van de Experience Manager, worden weergegeven in Dynamic Media, niet in Dynamic Media Classic. Alle andere instellingen en waarden op de pagina Algemene instellingen en op het tabblad [Publicatie-instelling](/help/assets/dm-publish-settings.md) Dynamic Media Classic en Dynamic Media onderhouden deze pagina op Experience Manager.

**Algemene instellingen van Dynamic Media configureren:**

1. Selecteer in de modus Auteur Experience Manager het logo van de Experience Manager voor toegang tot de algemene navigatieconsole.
1. Selecteer in de linkertrack het pictogram Gereedschappen en ga vervolgens naar **[!UICONTROL Assets]** > **[!UICONTROL Dynamic Media General Settings]**.
1. In de pagina van de Server, plaats uw **[!UICONTROL Published Server Name]** en **[!UICONTROL Origin Server Name]** en vervolgens gebruikt u de vijf tabbladen om standaarduploadopties te configureren voor Beeldbewerking en voor Postscript-, Photoshop-, PDF- en Illustrator-bestanden.

   * [Server](#server-general-setting)
   * [Uploaden naar toepassing](#upload-to-application)
   * [Beeldbewerking](#image-editing-tab) tab
   * [PostScript](#postscript-tab) tab
   * [Photoshop](#photoshop-tab) tab
   * [PDF](#pdf-tab) tab
   * [Illustrator](#illustrator-tab) tab

   ![Pagina Algemene instellingen van Dynamic Media](/help/assets/assets-dm/dm-general-settings.png)
   *Dynamic Media General Settings pagina, met de **[!UICONTROL Image Editing]**geselecteerd.*<br><br>

1. Als u klaar bent, selecteert u in de rechterbovenhoek van de pagina de optie **[!UICONTROL Save]**.

## Server {#server-general-setting}

Bij het aanmaken van accounts verschaft Adobe Dynamic Media automatisch de toegewezen servers voor uw bedrijf. Deze servers worden gebruikt om URL-tekenreeksen voor uw website en toepassingen samen te stellen. Deze URL-aanroepen gelden specifiek voor uw account.

| Optie | Beschrijving |
| --- | --- |
| **[!UICONTROL Published Server Name]** | Vereist.<br>De naam moet `https://` in het pad.<br>Deze server is de live CDN-server (Content Deliver Network) die wordt gebruikt in alle door het systeem gegenereerde URL-aanroepen die specifiek zijn voor uw account. Wijzig deze servernaam alleen als u hiervoor instructies hebt gekregen van de Adobe Technische ondersteuning. |
| **[!UICONTROL Origin Server Name]** | Vereist.<br>Deze server wordt alleen gebruikt voor tests op kwaliteitsborging. Wijzig deze servernaam alleen als u hiervoor instructies hebt gekregen van de Adobe Technical Support. |

## Uploaden naar toepassing {#upload-to-application}

* **[!UICONTROL Overwrite Images]**

  Adobe Dynamic Media staat niet toe dat twee bestanden dezelfde naam hebben. De Dynamic Media-id voor de Adobe van elk item (de naam van de afbeelding min de extensie van de bestandsnaam) moet uniek zijn. Vanwege deze regel **[!UICONTROL Upload to Application]** heeft een overschrijving. Het exacte effect van deze optie is afhankelijk van de opgegeven optie Afbeeldingen overschrijven die u hebt gekozen. Met deze opties geeft u op hoe vervangende afbeeldingen worden geüpload: of ze de oorspronkelijke afbeeldingen vervangen of dubbele afbeeldingen worden. Dubbele afbeeldingen krijgen een andere naam `-1`. Bijvoorbeeld: `chair.tif` is hernoemd `chair-1.tif`. Deze opties zijn van toepassing op afbeeldingen die naar een andere map zijn geüpload dan het origineel of afbeeldingen met een andere bestandsnaamextensie dan het origineel, zoals JPG, TIF of PNG.

  >[!NOTE]
  >
  >Selecteer de optie Afbeeldingen overschrijven om consistentie met Experience Manager te behouden **[!UICONTROL Overwrite in current folder, same base name/extension]**.

  | Afbeeldingen overschrijven, optie | Beschrijving |
  | --- | --- |
  | **[!UICONTROL Overwrite in current folder, same base name/extension]** | *Standaard* alleen voor nieuwe Dynamic Media-accounts.<br>Deze optie is de strengste regel voor vervanging. Hiervoor moet u de vervangende afbeelding uploaden naar dezelfde map als het origineel en moet de vervangende afbeelding dezelfde bestandsnaamextensie hebben als het origineel. Als niet aan deze vereisten wordt voldaan, wordt een dubbel gecreeerd.<br>*Selecteer deze optie om consistentie met Experience Manager te behouden*. |
  | **[!UICONTROL Overwrite in current folder, same base name regardless of extension]** | U moet de vervangende afbeelding uploaden naar dezelfde map als het origineel, maar de bestandsnaamextensie kan afwijken van het origineel. bijvoorbeeld stoel.tif vervangt stoel.jpg. |
  | **[!UICONTROL Overwrite in any folder, same base asset name/extension]** | Vereist dat de vervangende afbeelding dezelfde bestandsnaamextensie heeft als de oorspronkelijke afbeelding (bijvoorbeeld stoel.jpg moet de naam stoel.jpg vervangen, niet stoel.tif). U kunt de vervangende afbeelding echter naar een andere map uploaden dan het origineel. De bijgewerkte afbeelding bevindt zich in de nieuwe map. Het bestand is niet meer gevonden op de oorspronkelijke locatie. |
  | **[!UICONTROL Overwrite in any folder, same base asset name regardless of extension]** | Deze optie is de meest inclusieve vervangingsregel. U kunt een vervangende afbeelding uploaden naar een andere map dan het origineel, een bestand met een andere bestandsnaamextensie uploaden en het oorspronkelijke bestand vervangen. Als het oorspronkelijke bestand zich in een andere map bevindt, bevindt de vervangende afbeelding zich in de nieuwe map waarnaar het is geüpload. |

* **[!UICONTROL Preserve Crop]**

  Hiermee regelt u het behoud van bestaande handmatige snijddefinities.

  Zie ook `preserveCrop` in [UploadPostJob](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-upload-post-job.html) en [ReprocessAssetsJob](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-reprocess-assets-job.html), beide in de Dynamic Media Viewers Reference Guide.

## Standaardopties voor uploaden {#default-upload-options}

### Tabblad Beeldbewerking {#image-editing-tab}

Met dit filter kunt u een verscherpingsfiltereffect op de uiteindelijke gedownsampelde afbeelding perfectioneren. Hiermee kunt u de intensiteit van het effect, de straal van het effect (gemeten in pixels) en een drempel voor het contrast instellen die wordt genegeerd.

Voor het effect Onscherp masker worden dezelfde opties gebruikt als voor het filter Onscherp masker van Photoshop. In tegenstelling tot wat de naam suggereert, is Onscherp masker een verscherpingsfilter.

| Onscherpe maskeropties | Beschrijving |
| --- | --- |
| **[!UICONTROL Amount]** | Vereist.<br>Hiermee bepaalt u de hoeveelheid contrast die wordt toegepast op de randpixels.<br>Beschouw het als de intensiteit van het effect. Het belangrijkste verschil tussen de waarden voor de hoeveelheid Unsharp Mask in Adobe Dynamic Media en de waarden voor de hoeveelheid in Adobe Photoshop is dat Photoshop een bereik heeft van 1% tot 500%. In Adobe Dynamic Media is het waardebereik: `0.0` tot `5.0`. Een waarde van 5,0 in Adobe Dynamic Media is het ruwe equivalent van 500% in Photoshop; een waarde van 0,9 is het equivalent van 90%, etc. |
| **[!UICONTROL Radius]** | Vereist.<br>Hiermee bepaalt u de straal van het effect.<br>Het waardebereik is `0` tot `250`. Het effect wordt op alle pixels in een afbeelding uitgevoerd en wordt vanuit alle pixels in alle richtingen uitgestraald. De straal wordt gemeten in pixels. Als u bijvoorbeeld een vergelijkbaar verscherpingseffect wilt toepassen op een afbeelding van 2000 x 2000 pixels en een afbeelding van 500 x 500 pixels, stelt u een straal van twee pixels in voor de afbeelding van 2000 x 2000 pixels. Stel vervolgens een straalwaarde in van 1 pixel in de afbeelding van 500 x 500 pixels. Een hogere waarde wordt gebruikt voor een afbeelding met meer pixels. |
| **[!UICONTROL Threshold]** | Vereist.<br>Drempel is een contrastbereik dat wordt genegeerd wanneer het filter Onscherp masker wordt toegepast. Dit effect is belangrijk, zodat er geen &#39;ruis&#39; wordt toegevoegd aan een afbeelding wanneer dit filter wordt gebruikt. Het waardebereik is `0` - `255`Dit is het aantal helderheidsstappen in een grijswaardenafbeelding. `0`=zwart, `128`=50% grijs en `255`=wit.<br>Een drempelwaarde van `12` Hiermee negeert u kleine variaties door de helderheid van de huidskleur om ruis te voorkomen, maar voegt u randcontrast toe aan contrasterende gebieden, zoals waar de wimpers de huid raken.<br>Als u een foto van iemands gezicht hebt, heeft het filter Onscherp masker invloed op de contrasterende delen van de afbeelding. Bijvoorbeeld, waar wimpers en huid samenkomen om een duidelijk gebied van contrast tot stand te brengen, en de vlotte huid zelf. Zelfs de meest vloeiende skin vertoont subtiele wijzigingen in helderheidswaarden. Als u geen drempelwaarde gebruikt, accentueert het filter deze subtiele wijzigingen in de pixels van de skin. Er wordt op zijn beurt een lawaai en ongewenst effect gecreëerd terwijl het contrast op de wimpers wordt verhoogd, waardoor de scherpte wordt vergroot.<br>Om dit probleem te voorkomen, wordt een drempelwaarde geïntroduceerd die het filter vertelt om pixels te negeren die het contrast niet drastisch wijzigen, zoals een vloeiende skin.<br>Let op de structuur naast de ritssluiters in de afbeelding die u eerder hebt weergegeven. Ruis in de afbeelding wordt weergegeven omdat de drempelwaarden te laag waren om de ruis te onderdrukken. |
| **[!UICONTROL Monochrome]** | Selecteer deze optie om de helderheid (intensiteit) van een afbeelding zonder scherp masker te wijzigen.<br>Schakel deze optie uit als u elke kleurcomponent afzonderlijk niet scherp wilt maskeren. |

Zie ook [Afbeeldingen verscherpen in Adobe Dynamic Media en op afbeeldingsserver](/help/assets/assets/sharpening_images.pdf).

### Het tabblad PostScript {#postscript-tab}

U kunt Adobe PostScript®-bestanden rasteren, transparante achtergronden behouden, een resolutie kiezen en een kleurruimte kiezen.

U kunt Adobe PostScript® (EPS)-bestanden gebruiken in Adobe Dynamic Media. Adobe Dynamic Media bevat opdrachten voor het configureren van deze bestanden terwijl u deze uploadt.

Wanneer u PostScript-afbeeldingsbestanden (EPS) uploadt, kunt u deze op verschillende manieren opmaken. U kunt de bestanden rasteren, de transparante achtergrond behouden, een resolutie kiezen en een kleurruimte kiezen.

| PostScript, optie | Beschrijving |
| --- | --- |
| **[!UICONTROL Processing]** | Kies Rasteren om vectorafbeeldingen in het bestand om te zetten in de bitmapindeling. |
| **[!UICONTROL Maintain transparent background in rendered images]** | Hiermee blijft de achtergrondtransparantie van het bestand behouden. |
| **[!UICONTROL Resolution (pixel/inch)]** | Hiermee bepaalt u de resolutie-instelling. Deze instelling bepaalt hoeveel pixels per inch in het bestand worden weergegeven. |
| **[!UICONTROL Color space]** | ・ **[!UICONTROL Detect automatically]** - Behoudt de kleurruimte van het bestand.<br>・ **[!UICONTROL Force as RGB]** - Converteert naar de kleurruimte RGB.<br>・ **[!UICONTROL Force as CMYK]** - Converteert naar de CMYK-kleurruimte.<br>・ **[!UICONTROL Force as Grayscale]** - Zet om in de grijswaardenkleurruimte. |

### Het tabblad Photoshop {#photoshop-tab}

U kunt sjablonen maken van Adobe® Photoshop®-bestanden, lagen behouden, opgeven hoe lagen worden genoemd, tekst extraheren en opgeven hoe afbeeldingen in sjablonen worden verankerd.

| Photoshop, optie | Beschrijving |
| --- | --- |
| **[!UICONTROL Maintain layers]** | Hiermee worden de lagen in de PSD, indien aanwezig, uitgelijnd op afzonderlijke elementen. De elementlagen blijven gekoppeld aan de PSD. U kunt deze weergeven door het PSD-bestand te openen in de gedetailleerde weergave en het deelvenster Lagen te selecteren. Zie Lagen weergeven en bewerken in een PSD-bestand. |
| **[!UICONTROL Create template]** | Maakt een sjabloon op basis van de lagen in het PSD-bestand. |
| **[!UICONTROL Extract text]** | Extraheert de tekst zodat gebruikers naar tekst in een viewer kunnen zoeken. |
| **[!UICONTROL Extend layers to background size]** | Hiermee vergroot u de grootte van de uitgesneden afbeeldingslagen tot de grootte van de achtergrondlaag. |
| **[!UICONTROL Layer naming]** | Hiermee vergroot u de grootte van de uitgesneden afbeeldingslagen tot de grootte van de achtergrondlaag.<br>・ **[!UICONTROL Layer name]** - De afbeeldingen krijgen een naam na hun laagnamen in het PSD-bestand. Een laag met de naam Prijscode in het oorspronkelijke PSD-bestand wordt bijvoorbeeld een afbeelding met de naam Prijscode. Als de laagnamen in het PSD-bestand echter standaard Photoshop-laagnamen zijn (Achtergrond, Laag 1, Laag 2, enzovoort), krijgen de afbeeldingen een naam na hun laagnummers in het PSD-bestand. <br>・ **[!UICONTROL Photoshop and layer number]** - De afbeeldingen krijgen een naam na hun laagnummer in het PSD-bestand, waarbij de namen van de oorspronkelijke lagen worden genegeerd. Afbeeldingen krijgen de naam Photoshop en een toegevoegd laagnummer. Bijvoorbeeld de tweede laag van een dossier genoemd `Spring Ad.psd` is benoemd `Spring Ad_2` zelfs als het een niet-standaardnaam in Photoshop had.<br>・ **[!UICONTROL Photoshop and layer name]** - De afbeeldingen krijgen een naam na het PSD-bestand gevolgd door de naam van de laag of het laagnummer. Het laagnummer wordt gebruikt als de laagnamen in het PSD-bestand standaard Photoshop-laagnamen zijn. Een laag met de naam `Price Tag` in een PSD-bestand met de naam `SpringAd` is benoemd `Spring Ad_Price Tag`. Een laag met de standaardnaam Laag 2 wordt genoemd `Spring Ad_2`. |
| **[!UICONTROL Anchor]** | Geef op hoe afbeeldingen worden verankerd in sjablonen die worden gegenereerd op basis van de laagsamenstelling die uit het PSD-bestand is samengesteld. Standaard is het anker het middelpunt. Met een middelste anker kunnen vervangende afbeeldingen dezelfde ruimte het beste vullen, ongeacht de hoogte-breedteverhouding van de vervangende afbeelding. Afbeeldingen met een ander aspect dat deze afbeelding vervangt, nemen bij het verwijzen naar de sjabloon en het gebruik van parametervervanging in feite dezelfde ruimte in. Schakel over naar een andere instelling als de vervangende afbeeldingen de toegewezen ruimte in de sjabloon moeten vullen. |

### Tabblad PDF {#pdf-tab}

U kunt de bestanden omzetten in pixels, zoekwoorden en koppelingen extraheren, de resolutie instellen en een kleurruimte kiezen.

| PDF, optie | Beschrijving |
| --- | --- |
| **[!UICONTROL Processing]** | ・ **[!UICONTROL None]** - De PDF wordt niet verwerkt.<br>・ **[!UICONTROL Thumbnail]** - Hiermee wordt elke pagina in het PDF-bestand uitgelijnd en omgezet in een miniatuurafbeelding.<br> ・ **[!UICONTROL Rasterize]** - Hiermee worden de pagina&#39;s in het PDF-bestand uitgelijnd en worden vectorafbeeldingen omgezet in bitmapafbeeldingen. Kies deze optie om een eCatalog te maken. |
| **[!UICONTROL Extract]** | ・ **[!UICONTROL None]** - Er worden geen zoekwoorden of koppelingen uit de PDF geëxtraheerd.<br>・ **[!UICONTROL Search words]** - Extraheert zoekwoorden uit het PDF-bestand, zodat het bestand op trefwoord kan worden doorzocht in een eCatalog-viewer.<br>・ **[!UICONTROL Links]** - Extraheert koppelingen uit de PDF-bestanden en converteert deze naar Afbeeldingen met hyperlinks die worden gebruikt in een eCatalog-viewer.<br>・ **[!UICONTROL Search words and links]** - Extraheert zowel zoekwoorden als koppelingen voor gebruik in een eCatalog-viewer. |
| **[!UICONTROL Resolution (pixel/inch)]** | Hiermee bepaalt u de resolutie-instelling. Deze instelling bepaalt hoeveel pixels per inch in het PDF-bestand worden weergegeven. De standaardwaarde is 150. |
| **[!UICONTROL Color space]** | ・ **[!UICONTROL Detect automatically]** - Behoudt de kleurruimte van het PDF-bestand.<br>・ **[!UICONTROL Force as RGB]** - Converteert naar de kleurruimte RGB.<br>・ **[!UICONTROL Force as CMYK]** - Converteert naar de CMYK-kleurruimte.<br>・ **[!UICONTROL Force as Grayscale]** - Zet om in de grijswaardenkleurruimte. |

### Het tabblad Illustrator {#illustrator-tab}

U kunt Adobe Illustrator®-bestanden rasteren, transparante achtergronden behouden, een resolutie kiezen en een kleurruimte kiezen.

U kunt Adobe® Illustrator® (AI) dossiers in Adobe Dynamic Media gebruiken. Adobe Dynamic Media bevat opdrachten voor het configureren van deze bestanden terwijl u deze uploadt.

Wanneer u Illustrator-afbeeldingsbestanden (AI) uploadt, kunt u deze op verschillende manieren opmaken. U kunt de bestanden rasteren, de transparante achtergrond behouden, een resolutie kiezen en een kleurruimte kiezen. Opties voor de opmaak van PostScript- en Illustrator-bestanden zijn beschikbaar op het scherm Uploaden onder PostScript-opties en Illustrator-opties in het vak Opties voor uploaden.


| Illustrator, optie | Beschrijving |
| --- | --- |
| **[!UICONTROL Processing]** | Kies Rasteren om vectorafbeeldingen in het bestand om te zetten in de bitmapindeling. |
| **[!UICONTROL Maintain transparent background in rendered images]** | Hiermee blijft de achtergrondtransparantie van het bestand behouden. |
| **[!UICONTROL Resolution (pixel/inch)]** | Hiermee bepaalt u de resolutie-instelling. Deze instelling bepaalt hoeveel pixels per inch in het bestand worden weergegeven. |
| **[!UICONTROL Color space]** | ・ **[!UICONTROL Detect automatically]** - Behoudt de kleurruimte van het bestand.<br>・ **[!UICONTROL Force as RGB]** - Converteert naar de kleurruimte RGB.<br>・ **[!UICONTROL Force as CMYK]** - Converteert naar de CMYK-kleurruimte.<br>・ **[!UICONTROL Force as Grayscale]** - Zet om in de grijswaardenkleurruimte. |
