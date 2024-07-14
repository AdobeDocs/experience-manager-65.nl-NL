---
title: Dynamic Media Publish Setup (-instelling voor imageserver) configureren
description: Leer hoe u Dynamic Media Publish Setup for Image Server configureert, zodat u elementen kunt publiceren. U kunt uw elementen ook testen voordat u ze openbaar maakt.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: administering
content-type: reference
feature: Image Profiles
role: User, Admin
mini-toc-levels: 4
exl-id: c86e79c4-e887-4ee3-bb54-eeffb34a33c2
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '3108'
ht-degree: 0%

---

# Dynamic Media Publish Setup (-instelling voor imageserver) configureren

Het configureren van Dynamic Media Publish Setup is alleen beschikbaar als:

* Dynamic Media wordt uitgevoerd in de Scene7-modus. Zie [ Dynamic Media op de wijze van Scene7 ](/help/assets/config-dms7.md#enabling-dynamic-media-in-scene-mode) toelaten.
* U hebt *bestaand* **[!UICONTROL Dynamic Media Configuration]** (in **[!UICONTROL Cloud Services]**) in Adobe Experience Manager 6.5.11 of hierboven. Zie [ een Configuratie van Dynamic Media in Cloud Servicen ](/help/assets/config-dms7.md#configuring-dynamic-media-cloud-services) creëren.
* U bent een systeembeheerder van het systeem van de Experience Manager met beheerdervoorrechten.

Dynamic Media Publish Setup is bedoeld voor gebruik door ervaren ontwikkelaars en programmeurs van websites. Adobe Dynamic Media raadt gebruikers die deze publicatie-instellingen wijzigen aan bekend te zijn met de Adobe Dynamic Media, de normen en conventies van HTTP-protocollen en de basistechnologie voor beeldbewerking.

Op de pagina Dynamic Media Publish Setup worden standaardinstellingen vastgelegd die bepalen hoe elementen van Adobe Dynamic Media-servers worden geleverd aan websites of toepassingen. Als er geen instelling is opgegeven, levert de Adobe Dynamic Media-server een element volgens een standaardinstelling die is geconfigureerd op de Dynamic Media Publish Setup-pagina.

Zie ook [ Facultatief - Opstelling en configuratie van Dynamic Media - de wijzemontages van Scene7 ](/help/assets/config-dms7.md#optional-setup-and-configuration-of-dynamic-media-scene7-mode-settings) voor meer facultatieve configuratietaken.

>[!NOTE]
>
>Dynamic Media Classic op Adobe Experience Manager upgraden naar Dynamic Media? De [ Algemene pagina van Montages ](/help/assets/dm-general-settings.md) en de pagina van de Opstelling van Publish in Dynamic Media zijn pre-bevolkt met de waarden die van uw rekening van Dynamic Media Classic worden genomen. De uitzonderingen zijn alle waarden die worden vermeld onder **[!UICONTROL Default upload options]** gebied van de Algemene pagina van Montages. Deze waarden zijn al in Experience Manager. Alle wijzigingen die u onder **[!UICONTROL Default upload options]** aanbrengt in een van de vijf tabbladen via de gebruikersinterface van de Experience Manager, worden daarom weerspiegeld in Dynamic Media, niet in Dynamic Media Classic. Alle andere montages en waarden in de [ Algemene pagina van Montages ](/help/assets/dm-general-settings.md) en de pagina van de Opstelling van Publish worden gehandhaafd tussen Dynamic Media Classic en Dynamic Media op Experience Manager.

**om de Server van het Beeld van de Opstelling van Dynamic Media Publish te vormen:**

1. Selecteer in de modus Auteur Experience Manager het logo van de Experience Manager voor toegang tot de algemene navigatieconsole.
1. Selecteer in de linkertrack het pictogram Gereedschappen en ga vervolgens naar **[!UICONTROL Assets]** > **[!UICONTROL Dynamic Media Publish Setup]** .
1. In de pagina van de Server van het Beeld, plaats uw Server van het Beeld - publiceer context, en gebruik dan de vijf lusjes om gebrek te vormen publiceer montages.

   * [Afbeeldingsserver](#image-server)
   * [ Veiligheid ](#security-tab) tabel
   * ](#catalog-management-tab) lusje van het Beheer van de Catalogus 0} {[
   * [ Attributen van het Verzoek ](#request-attributes-tab) lusje
   * [ Gemeenschappelijke Attributen van de Duimnagel ](#common-thumbnail-attributes-tab) lusje
   * [ Attributen van het Beheer van de Kleur ](#color-management-attributes-tab) tabel

   ![ de pagina van de Opstelling van Dynamic Media Publish ](/help/assets/assets-dm/dm-publish-setup.png)
   *de pagina van de Opstelling van Dynamic Media Publish, met het **[!UICONTROL Request Attributes]**geselecteerde lusje.*<br><br>

1. Wanneer u klaar bent, selecteert u **[!UICONTROL Save]** in de rechterbovenhoek van de pagina.

## Afbeeldingsserver {#image-server}

De pagina van de Server van het Beeld vestigt standaardmontages voor het leveren van beelden van beeldservers. Instellingen zijn beschikbaar in vijf categorieën

| Publish-context | Beschrijving |
| --- | --- |
| Beeldserver | Hiermee geeft u de context voor publicatie-instellingen op. |
| Beeldserver testen | Hier geeft u de context voor het testen van publicatie-instellingen op.<br> Alleen voor nieuwe Dynamic Media-accounts wordt het standaard **[!UICONTROL Client address]** veld automatisch ingesteld op `127.0.0.1` .<br> zie [ activa van de Test alvorens hen openbaar ](#test-assets-before-making-public) te maken. |

### Het tabblad Beveiliging {#security-tab}

**[!UICONTROL Client address]** - Hiermee kunt u een of meer IP-adressen of IP-adresbereiken opgeven. Wanneer gespecificeerd, worden de verzoeken aan deze beeldcatalogus die van een cliënt bij een niet vermeld IP adres voortkomen verworpen. Deze regel geldt zowel voor de levering van afbeeldingen als voor gerenderde afbeeldingen.

![ het lusje van de Veiligheid van de Veiligheid ](/help/assets/assets-dm/dm-ipallowlist.png)<br>*lusje dat IP &quot;toestaat&quot;gebied.*

### Tabblad Catalogusbeheer {#catalog-management-tab}

**[!UICONTROL Rule set definition file path]** - Geeft het bestand op dat de definities van de regelset voor de afbeeldingscatalogus bevat.

Zie ook [ RuleSetFile ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-rulesetfile.html) parameter in de Gids van de Verwijzing van de Kijkers van Dynamic Media.

>[!NOTE]
>
>Als voor uw Dynamic Media Classic-account al een **[!UICONTROL Rule set definition file path]** is geselecteerd (zoals ingesteld onder **[!UICONTROL Setup]** > **[!UICONTROL Application]** > **[!UICONTROL Publish setup]** onder **[!UICONTROL Catalog Management]** -groep), haalt uw Dynamic Media-account op de Experience Manager het bestand op van Dynamic Media Classic. Het bestand wordt vervolgens opgeslagen en beschikbaar gemaakt in dit veld wanneer u de pagina **[!UICONTROL Dynamic Media Publish Setup]** voor het eerst opent.

### Aanvraagkenmerken, tabblad {#request-attributes-tab}

Deze instellingen hebben betrekking op de standaardweergave van afbeeldingen.

| Instelling | Beschrijving |
| --- | --- |
| **[!UICONTROL Reply image size limit]** | Vereist.<br> slechts voor nieuwe rekeningen van Dynamic Media, wordt de standaardgroottegrens automatisch geplaatst aan Breedte: `3000` en Hoogte: `3000` voor zowel **[!UICONTROL Image Serving]** als **[!UICONTROL Test Image Serving]**.<br> specificeert de maximumbreedte en de hoogte van het antwoordbeeld die aan de cliënt zijn teruggekeerd. De server retourneert een fout als een aanvraag een antwoordafbeelding veroorzaakt waarvan de breedte, of hoogte, of beide, groter is dan deze instelling.<br> zie ook [ MaxPix ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-maxpix.html) parameter in de Gids van de Verwijzing van de Kijkers van Dynamic Media. |
| **[!UICONTROL Request obfuscation mode]** | Schakel deze optie in als u base64-codering wilt toepassen op geldige aanvragen.<br> zie ook [ RequestObfuscation ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-requestobfuscation.html) parameter in de Gids van de Verwijzing van de Kijkers van Dynamic Media. |
| **[!UICONTROL Request locking mode]** | Schakel deze optie in als u een eenvoudige hash-vergrendeling wilt opnemen in aanvragen.<br> zie ook [ RequestLock ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-requestlock.html) parameter in de Gids van de Verwijzing van de Kijkers van Dynamic Media. |
| **[!UICONTROL Default Request Attributes]** | |
| **[!UICONTROL Default image file suffix]** | Vereist.<br> de uitbreiding van het standaard gegevensdossier die aan de het de gebiedswaarden van de Pad van de catalogus en MaskPath wordt toegevoegd als de weg geen dossierachtervoegsel omvat.<br> zie ook [ DefaultExt ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultext.html) parameter in de Gids van de Verwijzing van de Kijkers van Dynamic Media. |
| **[!UICONTROL Default font face name]** | Hiermee geeft u op welk lettertype wordt gebruikt als er geen lettertype is opgegeven door een aanvraag voor een tekstlaag. Indien opgegeven, moet dit een geldige naam voor het lettertype zijn in de lettertypetoewijzing van deze afbeeldingscatalogus of in de lettertypetoewijzing van de standaardcatalogus.<br> zie ook [ DefaultFont ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultfont.html) parameter in de Gids van de Verwijzing van de Kijkers van Dynamic Media. |
| **[!UICONTROL Default image]** | Biedt een standaardafbeelding die moet worden geretourneerd als reactie op een verzoek waarbij de gevraagde afbeelding niet wordt gevonden.<br> zie ook [ DefaultImage ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-is-cat-defaultimage.html) parameter in de Gids van de Verwijzing van de Kijkers van Dynamic Media.<br>**NOTA**: Als uw rekening van Dynamic Media Classic reeds **[!UICONTROL Default image]** heeft geselecteerd (zoals die onder **[!UICONTROL Setup]** > **[!UICONTROL Application]** > **[!UICONTROL Publish setup]**, onder **[!UICONTROL Default Request Attributes]** groep) wordt geplaatst, haalt uw rekening van Dynamic Media op Experience Manager het dossier van Dynamic Media Classic. Het bestand wordt vervolgens opgeslagen en beschikbaar gesteld in dit veld wanneer u de pagina **[!UICONTROL Dynamic Media Publish Setup]** voor het eerst opent. |
| **[!UICONTROL Default image mode]** | Wanneer het schuifregelaarvak is ingeschakeld (schuifregelaar aan de rechterkant), vervangt **[!UICONTROL Default image]** elke ontbrekende laag in de bronafbeelding door de standaardafbeelding en wordt de samenstelling op de gebruikelijke manier geretourneerd. Wanneer het schuifregelaarvak is uitgeschakeld (schuifregelaar aan de linkerkant), wordt de volledige samengestelde afbeelding vervangen door de standaardafbeelding, zelfs als de ontbrekende afbeelding slechts een van de verschillende lagen is.<br> zie ook [ DefaultImageMode ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultimagemode.html) parameter in de Gids van de Verwijzing van de Kijkers van Dynamic Media. |
| **[!UICONTROL Default view size]** | Vereist.<br> slechts voor nieuwe rekeningen van Dynamic Media, wordt de standaardmeningsgrootte automatisch geplaatst aan Breedte: `1280` en Hoogte: `1280` voor zowel **[!UICONTROL Image Serving]** als **[!UICONTROL Test Image Serving]**.<br> de server beperkt antwoordbeelden om niet groter te zijn dan deze breedte en hoogte, als het verzoek niet uitdrukkelijk de meningsgrootte gebruikend `wid=`, `hei=`, of `scl=` specificeert.<br> zie ook [ DefaultPix ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultpix.html) parameter in de Gids van de Verwijzing van de Kijkers van Dynamic Media. |
| **[!UICONTROL Default thumbnail size]** | Vereist.<br> gebruikt in plaats van attribuut **[!UICONTROL Default view size]** voor duimnagelverzoeken (`req=tmb`). De server beperkt antwoordafbeeldingen tot maximaal die breedte en hoogte als in een miniatuuraanvraag (`req=tmb`) de grootte niet expliciet wordt opgegeven met `wid=` , `hei=` of `scl=` .<br> zie ook [ DefaultThumbPix ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultthumbpix.html) parameter in de Gids van de Verwijzing van de Kijkers van Dynamic Media. |
| **[!UICONTROL Default background color]** | Hiermee geeft u de RGB-waarde op die wordt gebruikt om een willekeurig gebied van een antwoordafbeelding dat geen werkelijke afbeeldingsgegevens bevat, in te vullen.<br> zie ook [ BkgColor ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-bkgcolor.html) parameter in de Gids van de Verwijzing van de Kijkers van Dynamic Media. |
| **[!UICONTROL JPEG Encoding Attributes]** |  |
| **[!UICONTROL Quality]** | <br> specificeert de standaardattributen voor JPEG antwoordbeelden.<br> Alleen voor nieuwe Dynamic Media-accounts wordt de **[!UICONTROL Quality]** standaardwaarde automatisch ingesteld op `80` voor zowel **[!UICONTROL Image Serving]** als **[!UICONTROL Test Image Serving]** .<br> Dit gebied wordt bepaald in de waaier van 1 - 100.<br> zie ook [ JpegQuality ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-jpegquality.html) parameter in de Gids van de Verwijzing van de Kijkers van Dynamic Media. |
| **[!UICONTROL Chromatically downsampling]** | Schakel chromatische downsampling van JPEG-coders in of uit. |
| **[!UICONTROL Default resampling mode]** | Hiermee geeft u de standaardkenmerken voor resampling en interpolatie op die u wilt gebruiken voor het schalen van afbeeldingsgegevens. Wordt gebruikt wanneer `resMode` niet is opgegeven in een aanvraag.<br> slechts voor nieuwe rekeningen van Dynamic Media, wordt de standaard het opnieuw berekenen wijze automatisch geplaatst aan `Sharp2` voor zowel **[!UICONTROL Image Serving]** als **[!UICONTROL Test Image Serving]**.<br> zie ook [ ResMode ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-is-cat-resmode.html) parameter in de Gids van de Verwijzing van de Kijkers van Dynamic Media. |

### Algemene miniatuurkenmerken, tabblad {#common-thumbnail-attributes-tab}

Deze instellingen hebben betrekking op de standaardweergave en -uitlijning van miniatuurafbeeldingen.

| Instelling | Beschrijving |
| --- | --- |
| **[!UICONTROL Default background color for thumbnail]** | Hiermee geeft u de RGB-waarde op die wordt gebruikt om het gebied te vullen van een miniatuurafbeelding die geen werkelijke afbeeldingsgegevens bevat. Wordt alleen gebruikt voor miniatuuraanvragen (`req=tmb`) en wanneer **[!UICONTROL Default Thumbnail Type]** instelling is ingesteld op **[!UICONTROL Fit]** of **[!UICONTROL Texture]** .<br> zie ook [ ThumbBkgColor ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-thumbbkgcolor.html) parameter in de Gids van de Verwijzing van de Kijkers van Dynamic Media. |
| **[!UICONTROL Horizontal alignment]** | Geeft de horizontale uitlijning op van de miniatuurafbeelding in de rechthoek van de antwoordafbeelding die wordt opgegeven door `wid=` - en `hei=` -waarden.<br> Gebruikt slechts voor duimnagelverzoeken (`req=tmb`) en wanneer **[!UICONTROL Default Thumbnail Type]** het plaatsen aan **[!UICONTROL Fit]** wordt geplaatst.<br> Er zijn drie horizontale uitlijningen te kiezen van: **[!UICONTROL Center alignment]**, **[!UICONTROL Left alignment]**, en **[!UICONTROL Right alignment]**.<br> zie ook [ ThumbHorizAlign ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-thumbhorizalign.html) parameter in de Gids van de Verwijzing van de Kijkers van Dynamic Media. |
| **[!UICONTROL Vertical alignment]** | Geeft de verticale uitlijning op van de miniatuurafbeelding in de rechthoek van de antwoordafbeelding die wordt opgegeven door `wid=` - en `hei=` -waarden. Wordt alleen gebruikt voor miniatuuraanvragen (`req=tmb`) en wanneer **[!UICONTROL Default Thumbnail Type]** instelling is ingesteld op **[!UICONTROL Fit]** .<br> Er zijn drie verticale uitlijningen te kiezen van: **[!UICONTROL Top alignment]**, **[!UICONTROL Center alignment]**, en **[!UICONTROL Bottom alignment]**.<br> zie ook [ ThumbVertAlign ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-thumbvertalign.html) parameter in de Gids van de Verwijzing van de Kijkers van Dynamic Media. |
| **[!UICONTROL Default cache time to live]** | Verstrekt een standaardvervalinterval in uren voor het geval dat een bepaalde catalogusverslag geen geldige waarde van de Vervaldatum van de catalogus bevat. Ingesteld op `-1` om te markeren als nooit verlopen. <br> zie ook [ Vervalparameter ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-expiration.html) in de Gids van de Verwijzing van de Kijkers van Dynamic Media. |
| **[!UICONTROL Default thumbnail type]** | Hiermee wordt een standaardinstelling voor het miniatuurtype opgegeven voor het geval dat een bepaalde catalogusrecord geen geldige waarde voor ThumbType-catalogus bevat. Wordt alleen gebruikt voor miniatuuraanvragen (`req=tmb`).<br> Er zijn drie miniatuurtypen waaruit u kunt kiezen: **[!UICONTROL Crop]** , **[!UICONTROL Fit]** en **[!UICONTROL Texture]** .<br> zie ook [ ThumbType ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-thumbtype.html) parameter in de Gids van de Verwijzing van de Kijkers van Dynamic Media. |
| **[!UICONTROL Default thumbnail resolution]** | Verstrekt een gebrek voor de duimnagelobjecten resolutie in het geval dat een bepaalde catalogusverslag geen geldige catalogus ThumbRes waarde bevat. Wordt alleen gebruikt voor miniatuuraanvragen (`req=tmb`) en wanneer de instelling **[!UICONTROL Default thumbnail type]** is ingesteld op **[!UICONTROL Texture]** .<br> zie ook [ ThumbRes ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-thumbres.html) parameter in de Gids van de Verwijzing van de Kijkers van Dynamic Media. |

### Kenmerken kleurbeheer, tabblad {#color-management-attributes-tab}

Deze instellingen bepalen welke ICC-kleurprofielen worden gebruikt voor afbeeldingen.

**Teruggevende Intentie van de Omzetting van de Kleur 1}
Met een rendering intent voor kleurconversie kunt u de standaard rendering intent van de werkprofielen overschrijven om te bepalen hoe de bronkleuren worden aangepast.** Wordt gebruikt als:

1. Een van de standaard-ICC-profielen is de doelkleurruimte van een kleuromzetting.
1. Dit profiel kenmerkt een uitvoerapparaat (printer of monitor).
1. En de opgegeven render-intentie is geldig voor dit profiel.

Bij verschillende rendering intents worden verschillende regels gebruikt om te bepalen hoe de bronkleuren worden aangepast.

Zie ook ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccrenderintent.html) parameter 0} IccRenderIntent in de Gids van de Verwijzing van de Kijkers van Dynamic Media.[

>[!NOTE]
>
>Over het algemeen kunt u het beste de standaard rendering intent gebruiken voor de geselecteerde kleurinstelling. Deze is tijdens de Adobe getest om te voldoen aan industriestandaarden. Als u bijvoorbeeld een kleurinstelling kiest voor Noord-Amerika of Europa, is de standaard rendering intent van kleurconversie **[!UICONTROL Relative Colorimetric]** . Als u een kleurinstelling voor Japan kiest, is de standaard rendering intent van kleurconversie **[!UICONTROL Perceptual]** .

| Instelling | Kenmerken |
| --- | --- |
| **[!UICONTROL CMYK default color space]** | Hiermee geeft u de naam op van het ICC-kleurprofiel dat u wilt gebruiken als werkprofiel voor CMYK-gegevens. Als **[!UICONTROL None Specified]** wordt gekozen, wordt kleurbeheer voor deze afbeeldingscatalogus uitgeschakeld als er CMYK-bronafbeeldingen bij betrokken zijn. Alle CMYK-werkruimten zijn apparaatafhankelijk, wat betekent dat ze zijn gebaseerd op werkelijke inkt- en papiercombinaties. De Adobe van de CMYK-werkruimten is gebaseerd op standaard professionele afdrukvoorwaarden.<br> zie ook [ IccProfileCMYK ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilecmyk.html) parameter in de Gids van de Verwijzing van de Kijkers van Dynamic Media. |
| **[!UICONTROL Gray-Scale default color space]** | Hiermee geeft u de naam op van het ICC-kleurprofiel dat u wilt gebruiken als werkprofiel voor grijswaardengegevens. Als **[!UICONTROL None Specified]** wordt gekozen, wordt kleurbeheer voor deze afbeeldingscatalogus uitgeschakeld wanneer er bronafbeeldingen met grijswaarden bij betrokken zijn.<br> zie ook [ IccProfileGray ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilegray.html) parameter in de Gids van de Verwijzing van de Kijkers van Dynamic Media. |
| **[!UICONTROL RGB default color space]** | Hiermee geeft u de naam op van het ICC-kleurprofiel dat u wilt gebruiken als werkprofiel voor RGB-gegevens. Als **[!UICONTROL None Specified]** wordt gekozen, wordt kleurbeheer voor deze afbeeldingscatalogus uitgeschakeld wanneer er afbeeldingen van het type RGB worden gebruikt. Over het algemeen kunt u het beste **[!UICONTROL Adobe RGB]** of **[!UICONTROL sRGB]** kiezen in plaats van het profiel voor een specifiek apparaat (zoals een monitorprofiel). **[!UICONTROL sRGB]** wordt aanbevolen voor het voorbereiden van afbeeldingen voor het web of mobiele apparaten, omdat hiermee de kleurruimte wordt gedefinieerd van de standaardmonitor die wordt gebruikt om afbeeldingen op het web weer te geven. **[!UICONTROL sRGB]** is ook geschikt wanneer u werkt met afbeeldingen van digitale camera&#39;s op consumentenniveau, omdat bij het merendeel van deze camera&#39;s s sRGB als de standaardkleurruimte wordt gebruikt.<br> zie ook [ IccProfileRBG ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilergb.html) parameter in de Gids van de Verwijzing van de Kijkers van Dynamic Media. |
| **[!UICONTROL Color conversion rendering intent]** | **[!UICONTROL Perceptual]** - Beoogd de visuele relatie tussen kleuren te behouden zodat deze voor het menselijk oog natuurlijk worden ervaren, ook al kunnen de kleurwaarden zelf veranderen. Deze intent is geschikt voor fotografische afbeeldingen met veel kleuren die buiten de kleuromvang vallen. Deze instelling is de standaard rendering intent voor de Japanse afdrukindustrie. |
|  | **[!UICONTROL Relative Colorimetric]** - Vergelijkt het extreme hooglicht van de bronkleurruimte met dat van de doelkleurruimte en verschuift alle kleuren dienovereenkomstig. Kleuren buiten de kleuromvang worden verschoven naar de dichtstbijzijnde reproduceerbare kleur in de doelkleurruimte. Bij Relatief colorimetrisch blijven meer oorspronkelijke kleuren behouden dan bij Perceptueel. Deze instelling is de standaard rendering intent voor afdrukken in Noord-Amerika en Europa. |
|  | **[!UICONTROL Saturation]** - Probeert levendige kleuren in een afbeelding te produceren ten koste van de kleurnauwkeurigheid. Deze rendering intent is geschikt voor zakelijke afbeeldingen, zoals grafieken of diagrammen, waar heldere verzadigde kleuren belangrijker zijn dan de exacte relatie tussen kleuren. |
|  | **[!UICONTROL Absolute Colorimetric]** - Hiermee blijven kleuren die binnen de doelkleuromvang vallen ongewijzigd. Kleuren buiten de kleuromvang worden bijgesneden. Kleuren worden niet geschaald naar het witpunt van de bestemming. Deze intent is bedoeld om de kleurnauwkeurigheid te behouden ten koste van de relaties tussen kleuren en is geschikt voor proefdrukken om de uitvoer van een bepaald apparaat te simuleren. Deze intent is handig als u een voorvertoning wilt weergeven van de invloed van de papierkleur op de afgedrukte kleuren. |

## Elementen testen voordat ze openbaar worden gemaakt {#test-assets-before-making-public}

Veilig het Testen helpt u een veilig testmilieu bepalen en een robuuste zaken-aan-zaken oplossing bouwen, die op een configureerbare reeks IP adres en waaiers wordt gebaseerd. Met deze functionaliteit kunt u uw Adobe Dynamic Media-implementaties afstemmen op de architectuur van uw contentbeheer en bedrijfssysteem.

Met Beveiligd testen kunt u een voorvertoning van de testversie van de website weergeven met niet-gepubliceerde inhoud.

Maak indien gewenst een testomgeving in plaats van elementen openbaar te maken, en wel om de volgende redenen:

* Geef een voorvertoning weer van websites voordat u deze openbaar maakt (website voor opvoeren).
* Serve activa die beperkte toegang, zoals eCatalogi vereisen die prijzen in een B2B Webtoepassing tonen.
* Gebruik middelen achter een firewall als onderdeel van het systeem voor productinformatiebeheer, de toepassing van de klantenservice, de trainingssite enzovoort.

>[!NOTE]
>
>Beveiligd testen heeft geen invloed op de toegang tot Adobe Dynamic Media Classic. De beveiliging van Adobe Dynamic Media Classic blijft consistent en vereist de gebruikelijke aanmeldingsgegevens voor toegang tot Adobe Dynamic Media Classic en verwante webservices.

### Hoe Veilig testen werkt {#how-test-assets-works}

De meeste bedrijven voeren hun Internet achter een firewall in werking. De toegang tot Internet is mogelijk door bepaalde routes en typisch door een beperkte waaier van openbare IP adressen.

Van uw collectief netwerk, kunt u uw openbaar IP adres uitvinden gebruikend websites zoals [ https://www.whatismyip.com ](https://www.whatismyip.com/) of om deze informatie van uw collectieve organisatie van IT verzoeken.

Met het Veilige Testen, vestigt de Adobe Dynamic Media een specifieke Server van het Beeld voor het opvoeren van milieu&#39;s of interne toepassingen. Om het even welk verzoek aan deze server controleert het oorsprongIP adres. Als het inkomende verzoek niet binnen de goedgekeurde lijst van IP adressen is, is een mislukkingsreactie teruggekeerd. De beheerder van het Bedrijf van Dynamic Media van de Adobe vormt de goedgekeurde lijst van IP adressen voor het Veilige Testen van hun bedrijf milieu.

Omdat de plaats van het originele verzoek moet worden bevestigd, wordt het verkeer van de Veilige Testende dienst niet verpletterd door een netwerk van de inhoudsdistributie zoals het openbare verkeer van de Server van het Beeld van Dynamic Media. Verzoeken naar de service Beveiligd testen hebben een iets hogere latentie dan de openbare Dynamic Media Image Servers.

Niet-gepubliceerde middelen zijn direct beschikbaar bij de services voor het beveiligen van tests, zonder dat ze hoeven te worden gepubliceerd. Op deze manier kunt u een voorvertoning uitvoeren voordat elementen worden gepubliceerd naar hun openbare afbeeldingsserver.

>[!NOTE]
>
>De veilige Testende diensten gebruiken de Server van de Catalogus die met een interne publicatiecontext wordt gevormd. Daarom als uw bedrijf wordt gevormd om te publiceren om het Veilige Testen te beveiligen, om het even welke geuploade activa in Adobe Dynamic Media onmiddellijk beschikbaar worden op de Veilige Testende diensten. Deze functionaliteit is van toepassing, ongeacht of de elementen zijn gemarkeerd voor publiceren tijdens het uploaden.

De Secure Testing-services bieden momenteel ondersteuning voor de volgende typen middelen en functies:

* Afbeeldingen.
* Vignettes (aanvragen van Server renderen).
* Serveraanvragen renderen (ondersteund, maar moet expliciet door de klant worden aangevraagd).
* Sets, inclusief afbeeldingssets, eCatalog, rendersets en mediasets.
* Standaard Adobe Dynamic Media-viewers met rijke media.
* Adobe Dynamic Media OnDemand JSP-pagina&#39;s.
* Statische inhoud, zoals PDF-bestanden en progressieve video&#39;s.
* HTTP-videostreaming.
* Progressieve videostreaming.

De volgende elementtypen en -functies worden momenteel niet ondersteund:

* Zoeken in Adobe Dynamic Media Classic Info of eCatalog
* RTMP-videostreaming
* Web-to-print
* UGC-services (door de gebruiker gegenereerde inhoud)

  >[!IMPORTANT]
  >
  >Vanaf 1 mei 2023 zijn UGC-middelen in Dynamic Media beschikbaar voor gebruik tot 60 dagen na de datum van uploaden. Na 60 dagen worden de middelen verwijderd.

  >[!NOTE]
  >
  >De ondersteuning voor nieuwe of bestaande UGC-vectorafbeeldingselementen in Adobe Dynamic Media is op 30 september 2021 afgelopen.

### De service Beveiligde tests testen {#test-secure-testing-service}

Ga als volgt te werk om ervoor te zorgen dat de service Beveiligd testen naar behoren functioneert:

#### Uw account voorbereiden

1. Neem contact op met de klantenservice van de Adobe en verzoek hen Beveiligingstests op uw account in te schakelen.
1. Selecteer in Adobe Experience Manager **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Dynamic Media Publish Setup]** .
1. Selecteer **[!UICONTROL Test Image Serving]** op de pagina Afbeeldingsserver in de vervolgkeuzelijst **[!UICONTROL Publish Context]** .
1. Selecteer de tab **[!UICONTROL Security]** .
1. Selecteer **[!UICONTROL Add]** voor het filter **[!UICONTROL Client address]** .
1. Typ een IP-adres in het veld **[!UICONTROL IP Address]** .
1. Typ een netmasker in het veld **[!UICONTROL Mask]** .

   >[!NOTE]
   >
   >Als u meer dan één IP adres en netto masker toevoegt, laat het *effectief alle* IP adressen toe om activavraag te maken, en zij allen verschijnen.

1. Voer een van de volgende handelingen uit:

   * Herhaal de vorige drie stappen om meer IP-adressen toe te voegen.
   * Ga door met de volgende stap.

1. Selecteer **[!UICONTROL Save]** in de rechterbovenhoek van de pagina Afbeeldingsserver.
1. Upload de gewenste afbeeldingen naar uw Adobe Dynamic Media-account.

<!--    See [Upload files](uploading-files.md#uploading_files). -->

1. Zorg ervoor dat sommige afbeeldingen zijn gemarkeerd voor publicatie en andere niet zijn gemarkeerd en verzend vervolgens de publicatietaak.

<!--    See [Publish files](publishing-files.md#publishing_files). -->

1. Bepaal de naam van uw service Beveiligd testen via **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Dynamic Media General Setting]** .
1. Zoek op de pagina **[!UICONTROL Server]** de servernaam rechts van **[!UICONTROL Published Server Name]** .

Neem contact op met de Adobe als de servernaam ontbreekt of als de URL naar de server niet werkt.

#### Websitevariaties voorbereiden

U hebt twee variaties nodig van een website die de gepubliceerde en niet-gepubliceerde elementen koppelt:

* Openbare versie - Koppel elementen met behulp van uw traditionele Adobe Dynamic Media URL-syntaxis.
* Versie Staging - Koppel elementen met dezelfde syntaxis, maar met de naam van de site voor Beveiligd testen.

#### De tests uitvoeren

Voer de volgende tests uit:

1. Controleer of elementen zichtbaar zijn vanuit uw bedrijfsnetwerk.

   Vanuit het bedrijfsnetwerk dat door het eerder gedefinieerde IP-adresbereik wordt geïdentificeerd, worden in de testversie van de website alle afbeeldingen weergegeven, ongeacht of deze zijn gemarkeerd voor publicatie of niet. Zo kunt u testen zonder dat u per ongeluk afbeeldingen ter beschikking stelt voordat u een voorvertoning van goedkeuring of het product start.

   Bevestig dat in de openbare versie van uw site de gepubliceerde middelen worden weergegeven zoals die eerder met Adobe Dynamic Media zijn gebruikt.

1. Van buiten uw bedrijfsnetwerk, verifieer dat nonpublished activa (d.w.z. unmarked voor publiceren) tegen derdetoegang worden beschermd.

   Open uw netwerk van buitenaf (zoals van uw huiscomputer, of over een verbinding 4G/5G), dan verifieer dat de openbare versie van de plaats alle gepubliceerde activa maar geen van de niet gepubliceerde inhoud toont.

   Bevestig dat de het opvoeren versie geen activa toont omdat u tot de Veilige Testende dienst van een niet goedgekeurd IP adres toegang hebt.
