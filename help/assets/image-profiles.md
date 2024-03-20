---
title: Dynamic Media-afbeeldingsprofielen
description: Maak afbeeldingsprofielen met instellingen voor onscherp masker en kies voor slim uitsnijden of slim staal of beide om het profiel toe te passen op een map met afbeeldingselementen.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: administering
content-type: reference
feature: Image Profiles
role: User, Admin
exl-id: 67240ad0-1a7c-4e58-a518-1e36d771f1a1
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '2959'
ht-degree: 4%

---

# Dynamic Media-afbeeldingsprofielen {#image-profiles}

Wanneer u afbeeldingen uploadt, kunt u de afbeelding tijdens het uploaden automatisch uitsnijden door een afbeeldingsprofiel toe te passen op de map.

>[!IMPORTANT]
>
>* Slim uitsnijden is alleen beschikbaar in de modus Dynamic Media - Scene7.
>* Afbeeldingsprofielen zijn niet van toepassing op PDF-, geanimeerde GIFFEN- of INDD-bestanden (Adobe InDesign).

## Opties voor uitsnijden {#crop-options}

Wanneer u Slim uitsnijden op afbeeldingen implementeert, raadt de Adobe de volgende aanbevolen procedures aan en past de volgende limiet toe:

| Type limiet | Beste praktijken | Oplegde limiet |
| --- | --- | --- |
| Aantal slimme uitsnijdingen per afbeelding | 5 | 100 |

Zie ook [Dynamic Media-beperkingen](/help/assets/limitations.md).

<!-- CQDOC-16069 for paragraph directly below -->

De coördinaten voor Slim uitsnijden zijn afhankelijk van de hoogte-breedteverhouding. Als voor de verschillende instellingen voor slimme uitsnijdingen in een afbeeldingsprofiel de hoogte-breedteverhouding voor de toegevoegde afmetingen in het afbeeldingsprofiel gelijk is, wordt dezelfde hoogte-breedteverhouding naar Dynamic Media verzonden. Adobe raadt u aan hetzelfde snijgebied te gebruiken. Zo voorkomt u dat er invloed optreedt op verschillende afmetingen die in het afbeeldingsprofiel worden gebruikt.

Voor elke SmartCrop-generatie die u maakt, is extra verwerkingstijd nodig. Als u bijvoorbeeld meer dan vijf slimme-uitsnijdverhoudingen toevoegt, kan dit leiden tot een langzame opname van elementen. Het veroorzaakt ook een verhoogde belasting op systemen. Omdat u Slim uitsnijden op mapniveau kunt toepassen, wordt het aanbevolen dat u het uitsnijden in mappen gebruikt *alleen* waar dat nodig is.

**Richtlijnen voor het definiëren van SmartCrop in een afbeeldingsprofiel**
Om het gebruik van SmartCrop onder controle te houden en de verwerkingstijd en opslag van gewassen te optimaliseren, beveelt de Adobe de volgende richtlijnen en tips aan:

* Op afbeeldingselementen waarop een slimme uitsnijding wordt toegepast, moet minimaal 50 x 50 pixels of groter zijn.
* In het ideale geval hebt u 10-15 slimme gewassen per afbeelding om de beeldverhoudingen en de verwerkingstijd te optimaliseren.
* Noem slimme gewassen die op gewassenafmetingen worden gebaseerd, niet op eindgebruik. Dit helpt u te optimaliseren voor duplicaten waarbij één dimensie op meerdere pagina&#39;s wordt gebruikt.
* Maak paginagewijs/middelengewijs afbeeldingsprofielen voor specifieke mappen en submappen in plaats van een algemeen profiel voor slimme uitsnijdingen dat wordt toegepast op alle mappen of alle elementen.
* Een afbeeldingsprofiel dat u op submappen toepast, overschrijft een afbeeldingsprofiel dat op de map is toegepast.
* Een afbeeldingsprofiel dat dubbele slimme-uitsnijdafmetingen bevat, is niet toegestaan.
* Dubbele benoemde afbeeldingsprofielen waarvoor opties voor slim uitsnijden zijn ingesteld, zijn niet toegestaan.

U hebt twee opties voor het uitsnijden van afbeeldingen waaruit u kunt kiezen: Uitsnijden van pixels of Slim uitsnijden. U kunt er ook voor kiezen om het maken van kleur- en afbeeldingsstalen te automatiseren.

>[!IMPORTANT]
>
>* De Adobe raadt u aan de gegenereerde gewassen en stalen te herzien om ervoor te zorgen dat deze geschikt en relevant zijn voor uw merk en waarden.
>* CMYK-afbeeldingsindeling wordt niet ondersteund voor slim uitsnijden.

| Optie | Wanneer gebruiken | Beschrijving |
| --- | --- | --- |
| Uitsnijden met pixels | Bulk uitsnijdafbeeldingen alleen op basis van afmetingen. | Als u deze optie wilt gebruiken, selecteert u **[!UICONTROL Pixel Crop]** in de vervolgkeuzelijst Uitsnijdopties.<br><br>Als u wilt uitsnijden vanaf de zijkanten van een afbeelding, voert u het aantal pixels in dat u wilt uitsnijden vanaf een zijde of elke zijde van de afbeelding. Hoeveel van de afbeelding wordt uitgesneden, is afhankelijk van de ppi-instelling (pixels per inch) in het afbeeldingsbestand.<br><br>Een pixeluitsnijding voor een afbeeldingsprofiel wordt op de volgende manier gerenderd:<br>・ Waarden zijn Boven, Onder, Links en Rechts.<br>・ Linksboven wordt overwogen `0,0` en de pixeluitsnijding wordt daar berekend.<br>・ Beginpunt voor uitsnijden: Links is X en Boven is Y<br>・ Horizontale berekening: horizontale pixelafmetingen van de oorspronkelijke afbeelding min links en vervolgens min rechts.<br>・ Verticale berekening: verticale pixelhoogte min bovenkant, en dan minus Onder.<br><br>Stel dat u een afbeelding van 4000 x 3000 pixels hebt. U gebruikt waarden: Top=250, Bottom=500, Left=300, Right=700.<br><br>Van linksboven (300.250) uitsnijden met de vulruimte (4000-300-700, 3000-250-500 of 3000,2250). |
| Slim uitsnijden | Bulk uitsnijdafbeeldingen op basis van hun visuele brandpunt. | Smart Crop maakt gebruik van de kracht van kunstmatige intelligentie in Adobe Sensei om het uitsnijden van afbeeldingen in bulk te automatiseren. Met Slim uitsnijden wordt automatisch het brandpunt in een afbeelding opgespoord en uitgesneden om het gewenste aandachtspunt vast te leggen, ongeacht de schermgrootte.</p> <p>Selecteer **[!UICONTROL Smart Crop]** Schakel de functie in of uit in de vervolgkeuzelijst Uitsnijdopties, rechts van Responsieve uitsnijding van afbeelding.</p> <p>De standaardbreekpuntgrootten Groot, Normaal, en Klein omvatten over het algemeen de volledige waaier van grootte dat de meeste beelden op mobiele en tabletapparaten, Desktops, en banners worden gebruikt. Desgewenst kunt u de standaardnamen van Groot, Normaal, en Klein uitgeven.</p> <p>Selecteer **[!UICONTROL Add Crop]** Als u een uitsnijding wilt verwijderen, selecteert u het pictogram met de prullenbak. |
| Kleur en afbeeldingsstaal | Met Bulk wordt voor elke afbeelding een afbeeldingsstaal gegenereerd. | **Opmerking**: Slim staal wordt niet ondersteund in Dynamic Media Classic.<br><br>Zoek en genereer automatisch stalen van hoge kwaliteit op basis van productafbeeldingen met kleuren of structuur.<br><br>Als u Kleur en afbeeldingsstaal wilt gebruiken, selecteert u **[!UICONTROL Smart Crop]** Schakel deze functie in (schakel deze in) in de vervolgkeuzelijst Uitsnijdopties, rechts van Kleur en Afbeeldingsstaal. Geef een pixelwaarde op in de tekstvakken Breedte en Hoogte.<br><br>Alle uitsnijdingen van afbeeldingen zijn beschikbaar via de Renditions-rail, maar stalen worden alleen gebruikt via de functie URL kopiëren. Gebruik uw eigen weergavecomponent om het staal op uw site te renderen. (De uitzondering op deze regel zijn carrouselbanners. Dynamic Media biedt de weergavecomponent voor het staal dat wordt gebruikt in carrouselbanners.)<br><br>**Afbeeldingsstalen gebruiken**<br> De URL voor afbeeldingsstalen is eenvoudig. Het is:<br><br>`/is/image/company/&lt;asset_name&gt;:Swatch`<br>waar `:Swatch` wordt toegevoegd aan de aanvraag voor het element.<br><br>**Kleurstalen gebruiken**<br> Als u kleurstalen wilt gebruiken, maakt u een `req=userdata` verzoek met het volgende:<br>`/is/image/&lt;company_name&gt;/&lt;swatch_asset_name&gt;:Swatch?req=userdata`<br><br>Hier volgt bijvoorbeeld een staalelement in Dynamic Media Classic:<br>`https://my.company.com:8080/is/image/DemoCo/Sleek:Swatch`<br>en hier ziet u de overeenkomstige stalen `req=userdata` URL:<br>`https://my.company.com:8080/is/image/DemoCo/Sleek:Swatch?req=userdata`<br><br>De `req=userdata` de reactie is als volgt :<br>`SmartCropDef=Swatch SmartCropHeight=200.0`<br>`SmartCropRect=0.421671,0.389815,0.0848564,0.0592593,200,200`<br>`SmartCropType=Swatch`<br>`SmartCropWidth=200.0`<br>`SmartSwatchColor=0xA56DB2`<br><br>U kunt ook een `req=userdata` reactie in XML- of JSON-indeling, zoals in de volgende URL-voorbeelden:<br>`https://my.company.com:8080/is/image/DemoCo/Sleek:Swatch?req=userdata,json`<br>`https://my.company.com:8080/is/image/DemoCo/Sleek:Swatch?req=userdata,xml`<br><br>**Opmerking:** Maak uw eigen WCM-component om een kleurstaal aan te vragen en de `SmartSwatchColor` kenmerk, weergegeven door een hexadecimale waarde van 24-bits RGB.<br><br>Zie ook [`userdata` in de naslaggids voor viewers](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/req/r-userdata.html). |

## Onscherp masker {#unsharp-mask}

U gebruikt **[!UICONTROL Unsharp mask]** om een verscherpingsfiltereffect op de definitieve gedownsampelde afbeelding nauwkeurig af te stemmen. U kunt de intensiteit van het effect, de straal van het effect (gemeten in pixels) en een drempel voor het contrast instellen die wordt genegeerd. Dit effect gebruikt dezelfde opties als Adobe Photoshop *Onscherp masker* filter.

>[!NOTE]
>
>Onscherp masker wordt alleen toegepast op verkleinde uitvoeringen in de PTIFF-indeling (piramide tiff) die meer dan 50% zijn gedownsampled. Dit betekent dat de grootst mogelijke uitvoeringen binnen de titel niet worden beïnvloed door een onscherp masker, terwijl kleinere uitvoeringen zoals miniaturen worden gewijzigd (en het onscherpe masker tonen).

In **[!UICONTROL Unsharp Mask]** hebt u de volgende filteropties:

| Optie | Beschrijving |
| --- | --- |
| Hoeveelheid | Hiermee bepaalt u de hoeveelheid contrast die wordt toegepast op de randpixels. De standaardwaarde is 1,75. Voor afbeeldingen met een hoge resolutie kunt u de resolutie verhogen tot maximaal 5. Beschouw Hoeveelheid als een maat voor de filterintensiteit. Bereik is 0-5. |
| Straal | Hiermee bepaalt u het aantal pixels rondom de randpixels dat invloed heeft op de verscherping. Voer voor afbeeldingen met een hoge resolutie een waarde in tussen 1 en 2. Met een lage waarde worden alleen de randpixels verscherpt; met een hoge waarde wordt een bredere reeks pixels verscherpt. De juiste waarde is afhankelijk van de grootte van de afbeelding. De standaardwaarde is 0,2. Bereik is 0-250. |
| Drempel | Hiermee bepaalt u het contrastbereik dat moet worden genegeerd wanneer het filter Onscherp masker wordt toegepast. Met andere woorden, met deze optie bepaalt u hoe verschillend de verscherpte pixels moeten zijn van het omringende gebied voordat ze als randpixels worden beschouwd en worden verscherpt. Experimenteer met waarden tussen 0 en 255 om ruis te voorkomen. |

Verscherpen wordt beschreven in [Afbeeldingen verscherpen](/help/assets/assets/sharpening_images.pdf).

## Dynamic Media-afbeeldingsprofielen maken {#creating-image-profiles}

Zie voor meer informatie over het definiëren van geavanceerde verwerkingsparameters voor andere elementtypen [Elementverwerking configureren](config-dms7.md#configuring-asset-processing).

Zie [Profielen voor het verwerken van metagegevens, afbeeldingen en video&#39;s](processing-profiles.md).

Zie ook [Aanbevolen procedures voor het ordenen van uw digitale middelen voor het gebruik van verwerkingsprofielen](/help/assets/organize-assets.md).

**Dynamic Media-afbeeldingsprofielen maken:**

1. Selecteer het Adobe Experience Manager-logo en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Image Profiles]**.
1. Selecteren **[!UICONTROL Create]** zodat u een afbeeldingsprofiel kunt toevoegen.
1. Voer een profielnaam en waarden in voor onscherp masker, uitsnijden of staal of voor beide.

   Gebruik een profielnaam die specifiek is voor het beoogde doel. Als u bijvoorbeeld een profiel wilt maken dat alleen stalen genereert, dat wil zeggen dat Slim uitsnijden is uitgeschakeld (uitgeschakeld) en Kleur en Afbeeldingsstaal is ingeschakeld (ingeschakeld), gebruikt u de profielnaam &quot;Slimme stalen&quot;.

   Zie ook [Opties voor slim bijsnijden en slimme stalen](#crop-options) en [Onscherp masker](#unsharp-mask).

   ![uitsnijden](assets/crop.png)

1. Selecteer **[!UICONTROL Save]**. Het nieuwe profiel wordt weergegeven in de lijst met beschikbare profielen.

## Dynamic Media-afbeeldingsprofielen bewerken of verwijderen {#editing-or-deleting-image-profiles}

1. Selecteer het logo van de Experience Manager en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Image Profiles]**.
1. Selecteer het afbeeldingsprofiel dat u wilt bewerken of verwijderen. Selecteer **[!UICONTROL Edit Image Profile]**. Selecteer **[!UICONTROL Delete Image Profile]**.

   ![chlimage_1-254](assets/chlimage_1-254.png)

1. Sla de wijzigingen op als u het bestand bewerkt. Bevestig bij verwijderen dat u het profiel wilt verwijderen.

## Dynamic Media-afbeeldingsprofiel toepassen op mappen {#applying-an-image-profile-to-folders}

Wanneer u een afbeeldingsprofiel toewijst aan een map, nemen eventuele submappen het profiel automatisch over van de bovenliggende map. Dit betekent dat u slechts één afbeeldingsprofiel aan een map kunt toewijzen. Denk daarom zorgvuldig na over de mapstructuur van de locatie waar u middelen uploadt, opslaat, gebruikt en archiveert.

Als u een ander afbeeldingsprofiel aan een map hebt toegewezen, overschrijft het nieuwe profiel het vorige profiel. De vorige bestaande mapelementen blijven ongewijzigd. Het nieuwe profiel wordt toegepast op de elementen die later aan de map worden toegevoegd.

Mappen waaraan een profiel is toegewezen, worden in de gebruikersinterface aangegeven met de profielnaam die op de kaart wordt weergegeven.

<!-- When you add smart crop to an existing Image Profile, you need to re-trigger the [DAM Update Asset workflow](assets-workflow.md) if you want to generate crops for existing assets in your asset repository. -->

U kunt afbeeldingsprofielen toepassen op specifieke mappen of op alle elementen.

U kunt elementen opnieuw verwerken in een map die al een bestaand afbeeldingsprofiel heeft dat u later hebt gewijzigd. Zie [Elementen in een map opnieuw verwerken nadat u het verwerkingsprofiel hebt bewerkt](processing-profiles.md#reprocessing-assets).

### Dynamic Media-afbeeldingsprofielen toepassen op specifieke mappen {#applying-image-profiles-to-specific-folders}

U kunt een afbeeldingsprofiel toepassen op een map vanuit de **[!UICONTROL Tools]** of als u zich in de map bevindt, vanuit **[!UICONTROL Properties]**. In deze sectie wordt beschreven hoe u op beide manieren afbeeldingsprofielen kunt toepassen op mappen.

Mappen waaraan al een profiel is toegewezen, worden aangegeven door de naam van het profiel direct onder de mapnaam weer te geven.

U kunt elementen in een map opnieuw verwerken die al een bestaand videoprofiel heeft dat u later wijzigt. Zie [Elementen in een map opnieuw verwerken nadat u het verwerkingsprofiel hebt bewerkt](processing-profiles.md#reprocessing-assets).

#### Dynamic Media-afbeeldingsprofielen toepassen op mappen vanuit de gebruikersinterface Profielen {#applying-image-profiles-to-folders-from-profiles-user-interface}

1. Selecteer het logo van de Experience Manager en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Image Profiles]**.
1. Selecteer het afbeeldingsprofiel dat u wilt toepassen op een of meerdere mappen.

   ![chlimage_1-255](assets/chlimage_1-255.png)

1. Selecteren **[!UICONTROL Apply Processing Profile to Folders]** en selecteer de map of meerdere mappen die u wilt gebruiken om de nieuw geüploade elementen te ontvangen en selecteer **[!UICONTROL Apply]**. Mappen waaraan al een profiel is toegewezen, worden aangegeven door de naam van het profiel direct onder de mapnaam weer te geven.

#### Dynamic Media-afbeeldingsprofielen toepassen op mappen vanuit eigenschappen {#applying-image-profiles-to-folders-from-properties}

1. Selecteer het logo van het Experience League en ga naar **[!UICONTROL Assets]**. Navigeer vervolgens naar de bovenliggende map van de map waarop u een afbeeldingsprofiel wilt toepassen.
1. Selecteer in de map het vinkje om het te selecteren en selecteer vervolgens **[!UICONTROL Properties]**.
1. Selecteer de **[!UICONTROL Image Profiles]** tab. Van de **[!UICONTROL Profile Name]** vervolgkeuzelijst, selecteer het profiel en selecteer **[!UICONTROL Save & Close]**. Mappen waaraan al een profiel is toegewezen, worden aangegeven door de naam van het profiel direct onder de mapnaam weer te geven.

   ![chlimage_1-256](assets/chlimage_1-256.png)

### Een Dynamic Media-afbeeldingsprofiel wereldwijd toepassen {#applying-an-image-profile-globally}

Naast het toepassen van een profiel op een map, kunt u er ook een globaal toepassen, zodat het geselecteerde profiel wordt toegepast op inhoud die is geüpload naar Experience Manager-elementen in een map.

U kunt elementen in een map opnieuw verwerken die al een bestaand videoprofiel heeft dat u later wijzigt. Zie [Elementen in een map opnieuw verwerken nadat u het verwerkingsprofiel hebt bewerkt](processing-profiles.md#reprocessing-assets).

**Een Dynamic Media-afbeeldingsprofiel wereldwijd toepassen:**

1. Voer een van de volgende handelingen uit:

   * Navigeren naar `https://&lt;AEM server&gt;/mnt/overlay/dam/gui/content/assets/foldersharewizard.html/content/dam` en pas het juiste profiel toe en selecteer **[!UICONTROL Save]**.

     ![chlimage_1-257](assets/chlimage_1-257.png)

   * Navigeer naar CRXDE Lite naar het volgende knooppunt: `/content/dam/jcr:content`.

     De eigenschap toevoegen `imageProfile:/conf/global/settings/dam/adminui-extension/imageprofile/<name of image profile>` en selecteert u **[!UICONTROL Save All]**.

     ![configure_image_profiles](assets/configure_image_profiles.png)

## Het slimme uitsnijdstaal of het slimme staal van één afbeelding bewerken {#editing-the-smart-crop-or-smart-swatch-of-a-single-image}

>[!IMPORTANT]
>
>* Slim uitsnijden is alleen beschikbaar in de modus Dynamic Media - Scene7.

U kunt het venster voor slimme uitsnijden van een afbeelding handmatig opnieuw uitlijnen of het formaat ervan wijzigen om het brandpunt verder te verfijnen.

Nadat u een slim uitsnijden hebt bewerkt en opgeslagen, wordt de wijziging doorgegeven overal waar u het uitsnijden voor de specifieke afbeeldingen gebruikt.

U kunt slimme uitsnijdingen opnieuw uitvoeren als u de extra uitsnijdingen opnieuw wilt genereren.

Zie ook [Het slimme uitsnijdstaal of het slimme staal van meerdere afbeeldingen bewerken](#editing-the-smart-crop-or-smart-swatch-of-multiple-images).

**Het slimme uitsnijd of slimme staal van één afbeelding bewerken:**

1. Selecteer het logo van de Experience Manager en ga naar **[!UICONTROL Assets]** en vervolgens naar de map waarop een profiel voor slimme uitsnijdingen of slimme stalen is toegepast.

1. Selecteer de map zodat u de inhoud ervan kunt openen.
1. Selecteer de afbeelding waarvan u de slimme uitsnijding of het slimme staal wilt aanpassen.
1. Selecteer in de werkbalk de optie **[!UICONTROL Smart Crop]**.

1. Voer een van de volgende handelingen uit:

   * Sleep de schuifregelaar naar links of rechts boven in de rechterbovenhoek van de pagina om respectievelijk de weergave van de afbeelding te vergroten of te verkleinen.
   * Sleep in de afbeelding een hoekgreep om de grootte van het zichtbare gebied van het uitsnijden of staal aan te passen.
   * Sleep het vak of het staal in de afbeelding naar een nieuwe locatie. U kunt alleen afbeeldingsstalen bewerken; kleurstalen zijn statisch.
   * Selecteer boven de afbeelding de optie  **[!UICONTROL Revert]** om al uw bewerkingen ongedaan te maken en het oorspronkelijke uitsnijden of staal te herstellen.

1. Selecteer rechtsboven in de pagina de optie **[!UICONTROL Save]** selecteert u vervolgens **[!UICONTROL Close]** om terug te keren naar de map met elementen.

## Het slimme uitsnijdstaal of het slimme staal van meerdere afbeeldingen bewerken {#editing-the-smart-crop-or-smart-swatch-of-multiple-images}

>[!IMPORTANT]
>
>* Slim uitsnijden is alleen beschikbaar in de modus Dynamic Media - Scene7.

Nadat u een afbeeldingsprofiel met slimme uitsnijding hebt toegepast op een map, is op alle afbeeldingen in die map een uitsnijding toegepast. Indien gewenst kunt u *handmatig* U kunt het venster voor slimme uitsnijden in meerdere afbeeldingen opnieuw uitlijnen of het formaat ervan wijzigen om het brandpunt verder te verfijnen.

Nadat u een slim uitsnijden hebt bewerkt en opgeslagen, wordt de wijziging doorgegeven overal waar u het uitsnijden voor de specifieke afbeeldingen gebruikt.

U kunt slimme uitsnijdingen opnieuw uitvoeren als u de extra uitsnijdingen opnieuw wilt genereren.

**Het slimme uitsnijdstaal of het slimme staal van meerdere afbeeldingen bewerken:**

1. Selecteer het logo van de Experience Manager en ga naar **[!UICONTROL Assets]** en vervolgens naar een map waarop een profiel voor slimme uitsnijdingen of slimme stalen is toegepast.
1. Selecteer in de map de **[!UICONTROL More Actions]** (...), selecteert u vervolgens **[!UICONTROL Smart Crop]**.

1. Op de **[!UICONTROL Edit Smart Crops]** pagina, voer een van de volgende handelingen uit:

   * Pas de weergavegrootte van afbeeldingen op de pagina aan.

     Sleep de schuifregelaar naar links of rechts naast de vervolgkeuzelijst voor de naam van het onderbrekingspunt om het formaat van de weergave van de weer te geven afbeelding te wijzigen.

     ![edit_smart_crop-sliderbar](assets/edit_smart_crops-sliderbar.png)

   * Filter de lijst met weer te geven afbeeldingen op basis van namen van onderbrekingspunten. In het onderstaande voorbeeld worden de afbeeldingen gefilterd op de naam van het onderbrekingspunt &quot;Normaal&quot;.

     Selecteer in de vervolgkeuzelijst in de rechterbovenhoek van de pagina een naam voor het onderbrekingspunt om te filteren op welke afbeeldingen u ziet. (Zie de bovenstaande afbeelding.)

     ![edit_smart_crop-dropdownlist](assets/edit_smart_crops-dropdownlist.png)

   * Pas het formaat van het vak voor slimme uitsnijden aan. Voer een van de volgende handelingen uit:

      * Als de afbeelding alleen een slim uitsnijden of een slim staal bevat, sleept u de hoekgreep van het uitsnijdvak om de grootte van het zichtbare gebied van het uitsnijden aan te passen.
      * Als de afbeelding zowel een slim uitsnijden als een slim staal bevat, sleept u de hoekgreep van het uitsnijdvak om de grootte van het zichtbare gebied van het uitsnijden aan te passen. U kunt ook het slimme staal onder de afbeelding selecteren (kleurstalen zijn statisch) en vervolgens de hoekgreep van het uitsnijdvak slepen om de grootte van het zichtbare gedeelte van het staal aan te passen.

     ![De grootte van slimme uitsnijdingen in een afbeelding wijzigen](assets/edit_smart_crops-resize.png)

   * Het vak voor slimme uitsnijding verplaatsen. Voer een van de volgende handelingen uit:

      * Als de afbeelding alleen een slim uitsnijden of een slim staal bevat, sleept u het uitsnijdvak naar een nieuwe locatie.
      * Als de afbeelding zowel een slim uitsnijden als een slim staal bevat, sleept u het vak voor slim uitsnijden naar een nieuwe locatie. U kunt ook het slimme staal onder de afbeelding selecteren (kleurstalen zijn statisch) en het uitsnijdvak van het slimme staal naar een nieuwe locatie slepen.

     ![edit_smart_crop-move](assets/edit_smart_crops-move.png)

   * Maak alle bewerkingen ongedaan en herstel het oorspronkelijke slimme uitsnijdstaal of het oorspronkelijke slimme staal (alleen van toepassing op de huidige bewerkingssessie).

     Selecteren **[!UICONTROL Revert]** boven de afbeelding.

     ![edit_smart_crop-revert](assets/edit_smart_crops-revert.png)

1. Selecteer rechtsboven in de pagina de optie **[!UICONTROL Save]** selecteert u vervolgens **[!UICONTROL Close]** om terug te keren naar de map met elementen.

## Dynamic Media-afbeeldingsprofiel verwijderen uit mappen {#removing-an-image-profile-from-folders}

Wanneer u een afbeeldingsprofiel uit een map verwijdert, nemen eventuele submappen automatisch de verwijdering van het profiel uit de bovenliggende map over. Alle verwerking van bestanden die in de mappen zijn opgetreden, blijft echter intact.

U kunt een afbeeldingsprofiel uit een map verwijderen vanuit de map **[!UICONTROL Tools]** of als u zich in de map bevindt, vanuit **[!UICONTROL Properties]**. In deze sectie wordt beschreven hoe u afbeeldingsprofielen op beide manieren uit mappen kunt verwijderen.

### Dynamic Media-afbeeldingsprofielen uit mappen verwijderen via de gebruikersinterface Profielen {#removing-image-profiles-from-folders-via-profiles-user-interface}

1. Selecteer het logo van de Experience Manager en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Image Profiles]**.
1. Selecteer het afbeeldingsprofiel dat u uit een of meerdere mappen wilt verwijderen.
1. Selecteren **[!UICONTROL Remove Processing Profile from Folders]** en selecteer de map of meerdere mappen waaruit u het profiel wilt verwijderen en selecteer **[!UICONTROL Remove]**.

   U kunt bevestigen dat het afbeeldingsprofiel niet meer wordt toegepast op een map omdat de naam niet langer onder de mapnaam wordt weergegeven.

### Eigenschappen Dynamic Media-afbeeldingsprofielen uit mappen verwijderen {#removing-image-profiles-from-folders-via-properties}

1. Selecteer het logo van de Experience Manager en navigeer **[!UICONTROL Assets]** en vervolgens naar de map waaruit u een afbeeldingsprofiel wilt verwijderen.
1. Selecteer in de map het vinkje om het te selecteren en selecteer vervolgens **[!UICONTROL Properties]**.
1. Selecteer de **[!UICONTROL Image Profiles]** tab.
1. Van de **[!UICONTROL Profile Name]** vervolgkeuzelijst, selecteert u **[!UICONTROL None]** selecteert u vervolgens **[!UICONTROL Save & Close]**.

   Mappen waaraan al een profiel is toegewezen, worden aangegeven door de naam van het profiel direct onder de mapnaam weer te geven.
