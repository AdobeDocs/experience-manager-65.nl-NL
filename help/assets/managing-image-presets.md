---
title: Dynamische voorinstellingen voor mediaafbeeldingen beheren
description: Dynamische voorinstellingen voor mediafobeeldingen begrijpen en leren hoe u voorinstellingen voor afbeeldingen kunt maken, wijzigen en beheren
uuid: 3e9a7af6-bf49-4cff-b516-0a3ee9765391
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: cc1111c4-6e24-4570-9ac7-97c25cf24ede
docset: aem65
legacypath: /content/docs/en/aem/6-0/administer/integration/dynamic-media/image-presets
translation-type: tm+mt
source-git-commit: fed2e6474f710fd02cf27946252896ac33f3b256
workflow-type: tm+mt
source-wordcount: '3722'
ht-degree: 8%

---


# Dynamische voorinstellingen voor mediagrote beheren{#managing-image-presets}

Met voorinstellingen voor afbeeldingen kan AEM Assets dynamisch afbeeldingen van verschillende grootten, in verschillende indelingen of met andere afbeeldingseigenschappen leveren die dynamisch worden gegenereerd. Elke voorinstelling voor afbeeldingen vertegenwoordigt een vooraf gedefinieerde verzameling opdrachten voor het vergroten of verkleinen en opmaken van afbeeldingen. Wanneer u een voorinstelling voor afbeeldingen maakt, kiest u een grootte voor het leveren van de afbeelding. U kiest ook opmaakopdrachten, zodat de weergave van de afbeelding wordt geoptimaliseerd wanneer de afbeelding wordt geleverd voor weergave.

Beheerders kunnen voorinstellingen maken voor het exporteren van elementen. Gebruikers kunnen bij het exporteren van afbeeldingen een voorinstelling kiezen. Hiermee worden de afbeeldingen ook opnieuw opgemaakt volgens de specificaties die de beheerder heeft opgegeven.

U kunt ook voorinstellingen voor afbeeldingen maken die reageren. Als u een voorinstelling voor een responsieve afbeelding toepast op uw elementen, worden deze afhankelijk van het apparaat of de schermgrootte waarop ze worden weergegeven. U kunt afbeeldingsvoorinstellingen zo configureren dat deze naast RGB of Grijs ook CMYK gebruiken in de kleurruimte.

In deze sectie wordt beschreven hoe u voorinstellingen voor afbeeldingen maakt, wijzigt en over het algemeen beheert. U kunt een voorinstelling voor afbeeldingen op elk gewenst moment op een afbeelding toepassen. Zie [Voorinstellingen voor afbeeldingen toepassen](/help/assets/image-presets.md).

>[!NOTE]
>
>Slimme beeldverwerking werkt met bestaande voorinstellingen voor afbeeldingen en maakt gebruik van intelligentie tijdens de laatste milliseconde van levering om de bestandsgrootte van de afbeelding verder te beperken op basis van de snelheid van de browser of netwerkverbinding. Zie [Slimme beeldverwerking](/help/assets/imaging-faq.md) voor meer informatie.

## Voorinstellingen voor dynamische media-afbeeldingen {#understanding-image-presets}

Net als bij een macro is een voorinstelling voor afbeeldingen een vooraf gedefinieerde verzameling opdrachten voor het vergroten of verkleinen en opmaken van de grootte die onder een naam zijn opgeslagen. Als u wilt weten hoe Voorinstellingen afbeelding werken, kunt u instellen dat elke productafbeelding op uw website moet worden weergegeven in verschillende formaten, formaten en compressiesnelheden voor levering op het bureaublad en op mobiele apparatuur.

>[!NOTE]
>
>In de modus Dynamische media - Scene7 worden afbeeldingsvoorinstellingen alleen ondersteund voor afbeeldingselementen.

U kunt twee voorinstellingen voor afbeeldingen maken: één met 500 x 500 pixels voor desktopversie en 150 x 150 pixels voor de mobiele versie. U maakt twee voorinstellingen voor afbeeldingen, één genaamd `Enlarge`, om afbeeldingen met 500 x 500 pixels weer te geven en één genaamd `Thumbnail` om afbeeldingen met 150 x 150 pixels weer te geven. Als u afbeeldingen in de `Enlarge`- en `Thumbnail`-grootte wilt leveren, AEM de definitie van de voorinstelling Afbeelding vergroten en Afbeelding met miniatuur opzoeken. Vervolgens AEM dynamisch een afbeelding met de grootte en opmaakspecificaties van elke voorinstelling voor afbeeldingen.

Afbeeldingen die bij dynamische levering kleiner worden gemaakt, kunnen scherper en gedetailleerder worden. Daarom bevat elke voorinstelling voor afbeeldingen opmaakbesturingselementen waarmee u een afbeelding kunt optimaliseren wanneer deze met een bepaalde grootte wordt geleverd. Met deze besturingselementen zorgt u ervoor dat uw afbeeldingen scherp en duidelijk zijn wanneer ze aan uw website of toepassing worden geleverd.

Beheerders kunnen voorinstellingen voor afbeeldingen maken. Als u een voorinstelling voor een afbeelding wilt maken, begint u helemaal opnieuw of u kunt een bestaande voorinstelling beginnen en opslaan onder een andere naam.

## Dynamische voorinstellingen voor mediaafbeeldingen beheren {#managing-image-presets-1}

U beheert uw voorinstellingen voor afbeeldingen in AEM door te tikken op het AEM-logo of te klikken om de algemene navigatieconsole te openen, vervolgens te tikken of te klikken op het pictogram Extra en naar **[!UICONTROL Assets > Image Presets.]** te navigeren

![6_5_tools-assets-imagepresets](assets/6_5_tools-assets-imagepresets.png)

>[!NOTE]
>
>Alle afbeeldingsvoorinstellingen die u maakt, zijn ook beschikbaar als dynamische uitvoeringen wanneer u elementen voorvertoont of levert.
>
>In *Dynamische media - Scene7-modus* moet u *not* afbeeldingsvoorinstellingen publiceren omdat voorinstellingen voor afbeeldingen automatisch worden gepubliceerd.
>
>In *Dynamische media - hybride modus* moet u de voorinstellingen van afbeeldingen handmatig publiceren.
>
>Zie [Voorinstellingen voor afbeeldingen publiceren.](#publishing-image-presets)

>[!NOTE]
>
>Het systeem toont een verscheidenheid van vertoningen wanneer u **[!UICONTROL Renditions]** in de Mening van het Detail van activa selecteert. U kunt het aantal voorinstellingen voor afbeeldingen dat wordt weergegeven, verhogen of verlagen. Zie [Het aantal voorinstellingen voor afbeeldingen dat wordt weergegeven, vergroten](#increasing-or-decreasing-the-number-of-image-presets-that-display).

### Smart crop, Adobe Illustrator (AI), Postscript (EPS) en PDF-bestandsindelingen {#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats}

>[!NOTE]
>
>Dit onderwerp is van toepassing op Dynamische Media - Hybride slechts wijze.

Als u de opname van AI-, EPS- en PDF-bestanden wilt ondersteunen, zodat u dynamische uitvoeringen van deze bestandsindelingen kunt genereren, is het verstandig de volgende informatie te bekijken voordat u voorinstellingen voor afbeeldingen maakt.

Adobe Illustrator-bestandsindeling is een variant van PDF. De belangrijkste verschillen in AEM Assets zijn:

* Adobe Illustrator-documenten bestaan uit één pagina met meerdere lagen. Elke laag wordt geëxtraheerd als een PNG-subelement onder het Illustrator-hoofdelement.
* PDF-documenten bestaan uit een of meer pagina&#39;s. Elke pagina wordt uitgepakt als een PDF-subelement van één pagina onder het PDF-hoofddocument met meerdere pagina&#39;s.

De subelementen worden gemaakt door de `Create Sub Asset process`-component binnen de algemene `DAM Update Asset`-workflow. Tik op **[!UICONTROL Tools > Workflow > Models > DAM Update Asset > Edit.]** om deze procescomponent in de workflow te zien

Zie ook [Pagina&#39;s van een bestand met meerdere pagina&#39;s weergeven](/help/assets/managing-linked-subassets.md#view-pages-of-a-multi-page-file).

U kunt de submiddelen of de pagina&#39;s weergeven wanneer u het element opent, tikken op het menu Inhoud en **[!UICONTROL Subassets]** of **[!UICONTROL Pages.]** selecteren. De submiddelen zijn echte elementen. Dat wil zeggen dat PDF-pagina&#39;s worden geëxtraheerd door de workflowcomponent `Create Sub Asset`. Ze worden vervolgens opgeslagen als `page1.pdf`, `page2.pdf` enzovoort onder het hoofdelement. Nadat ze zijn opgeslagen, verwerkt de `DAM Update Asset` workflow ze.

Met Dynamische media kunt u dynamische uitvoeringen voor AI-, EPS- of PDF-bestanden voorvertonen en genereren. Hiervoor zijn de volgende verwerkingsstappen vereist:

1. In `DAM Update Asset` werkschema, `Rasterize PDF/AI Image Preview Rendition` de procescomponent rasterizes de eerste pagina van origineel element-gebruikend gevormde resolutie-in een `cqdam.preview.png` vertoning.

1. De `cqdam.preview.png` vertoning wordt dan geoptimaliseerd in een PTIFF door de `Dynamic Media Process Image Assets` procescomponent binnen het werkschema.

>[!NOTE]
>
>In de [!UICONTROL DAM Update Asset]-workflow worden miniaturen voor EPS-bestanden gegenereerd met de stap **[!UICONTROL EPS thumbnails]**.

#### Eigenschappen van metagegevens van PDF/AI/EPS-element {#pdf-ai-eps-asset-metadata-properties}

| **Eigenschap Metadata** | **Beschrijving** |
|---|---|
| dam:Physicalwidthinches | Documentbreedte in inches. |
| dam:Physicalheightininches | Documenthoogte in inches. |

U hebt toegang tot `Rasterize PDF/AI Image Preview Rendition` opties voor procescomponenten via de `DAM Update Asset` workflow.

Tik linksboven op Adobe Experience Manager en navigeer naar **[!UICONTROL Tools > Workflow > Models.]** Op de pagina Workflowmodellen en selecteer **[!UICONTROL DAM Update Asset]**. Tik vervolgens op de werkbalk op **[!UICONTROL Edit.]** Op de [!UICONTROL DAM Update Asset] workflowpagina en dubbeltik op de `Rasterize PDF/AI Image Preview Rendition` procescomponent om het dialoogvenster Step Properties te openen.

#### Opties voor PDF/AI-voorvertoning van afbeelding omzetten in pixels {#rasterize-pdf-ai-image-preview-rendition-options}

![Argumenten voor het rasteren van PDF- of AI-workflow](assets/rasterize_pdf_ai_image_preview.png)

Argumenten voor het rasteren van PDF- of AI-workflow

<table>
 <tbody>
  <tr>
   <td><strong>Procesargument</strong></td>
   <td><strong>Standaardinstelling</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td>MIME-typen</td>
   <td><p>application/pdf</p> <p>application/postscript</p> <p>application/illustrator<br /> </p> </td>
   <td>Lijst met documentmime-typen die worden beschouwd als PDF- of Illustrator-documenten.<br /> </td>
  </tr>
  <tr>
   <td>Max. breedte</td>
   <td>2048</td>
   <td>Maximale breedte van de gegenereerde voorvertoningsvertoning, in pixels.<br /> </td>
  </tr>
  <tr>
   <td>Max. hoogte</td>
   <td>2048</td>
   <td>Maximumhoogte van de gegenereerde voorvertoning, in pixels.<br /> </td>
  </tr>
  <tr>
   <td>Resolutie</td>
   <td>72</td>
   <td>Resolutie voor het rasteren van de eerste pagina, in ppi (pixels per inch).</td>
  </tr>
 </tbody>
</table>

Met de standaardprocesargumenten wordt de eerste pagina van een PDF/AI-document gerasterd met 72 ppi en de gegenereerde voorvertoningsafbeelding met een grootte van 2048 x 2048 pixels. Voor een gebruikelijke implementatie kunt u de resolutie verhogen tot minimaal 150 ppi of meer. Een document met een tekengrootte van 300 ppi in de VS vereist bijvoorbeeld een maximale breedte en hoogte van respectievelijk 2550 x 3300 pixels.

Met Maximale breedte en Maximumhoogte kunt u de resolutie beperken waarbij rasteren wordt beperkt. Als de maximale waarden bijvoorbeeld ongewijzigd blijven en de resolutie is ingesteld op 300 ppi, wordt een US Letter-document gerasterd naar 186 ppi. Het document is dus 1581 x 2046 pixels.

Voor de procescomponent `Rasterize PDF/AI Image Preview Rendition` is een maximum gedefinieerd om te voorkomen dat er te grote afbeeldingen in het geheugen worden gemaakt. Dergelijke grote afbeeldingen kunnen het geheugen overlopen dat aan de JVM (Java Virtual Machine) wordt geleverd. Er moet op worden gelet dat de JVM over voldoende geheugen beschikt om het geconfigureerde aantal parallelle workflows te beheren, waarbij elk van beide de mogelijkheid heeft om een image op de maximaal geconfigureerde grootte te maken.

### Bestandsindeling InDesign (INDD) {#indesign-indd-file-format}

Als u de opname van INDD-bestanden wilt ondersteunen, zodat u dynamische uitvoering van deze bestandsindeling kunt genereren, is het verstandig de volgende informatie te bekijken voordat u voorinstellingen voor afbeeldingen maakt.

Voor InDesign-bestanden worden subelementen alleen geëxtraheerd als de Adobe InDesign-server is geïntegreerd met AEM. Elementen waarnaar wordt verwezen, zijn gekoppeld op basis van hun metagegevens. InDesign Server is niet vereist voor koppelingen. De middelen waarnaar wordt verwezen, moeten echter aanwezig zijn in AEM voordat de InDesign-bestanden worden verwerkt, zodat de koppelingen tussen de InDesign-bestanden en de bestanden waarnaar wordt verwezen, worden gemaakt.

Zie [AEM Assets integreren met InDesign Server](/help/assets/indesign.md).

De het procescomponent van het Proces van de Extractie van Media in de `DAM Update Asset` werkschema stelt verscheidene preconfigured in werking breidt Manuscripten uit om InDesign dossiers te verwerken.

![De ExtendScript-paden in de argumenten van Media Extraction-proces](assets/6_5_mediaextractionprocess.png)

De ExtendScript-paden in de argumenten van Media Extraction Process-component in de [!UICONTROL DAM Update Asset]-workflow.

De volgende scripts worden gebruikt door Dynamic Media-integratie:

<table>
 <tbody>
  <tr>
   <td><strong>Scriptnaam uitbreiden</strong></td>
   <td><strong>Standaard</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td>ThumbnailExport.jsx</td>
   <td>Ja</td>
   <td>Genereert een 300 ppi <code>thumbnail.jpg</code> uitvoering die is geoptimaliseerd en door <code>Dynamic Media Process Image Assets</code> procescomponent is omgezet in een PTIFF-uitvoering.<br /> </td>
  </tr>
  <tr>
   <td>JPEGPagesExport.jsx</td>
   <td>Ja</td>
   <td>Hiermee genereert u een JPEG-subelement van 300 ppi voor elke pagina. Het JPEG-subelement is een echt middel dat is opgeslagen onder het element InDesign. Het wordt ook geoptimaliseerd en omgezet in PTIFF door de <code>DAM Update Asset</code> werkschema.<br /> </td>
  </tr>
  <tr>
   <td>PDFPagesExport.jsx</td>
   <td>Nee</td>
   <td>Hiermee genereert u een PDF-subelement voor elke pagina. Het PDF-subelement wordt verwerkt zoals eerder beschreven. Omdat de PDF slechts één pagina bevat, worden geen subelementen gegenereerd.<br /> </td>
  </tr>
 </tbody>
</table>

## Grootte {#configuring-image-thumbnail-size} van afbeeldingsminiaturen configureren

U kunt de grootte van miniaturen configureren door deze instellingen te configureren in de **[!UICONTROL DAM Update Asset]**-workflow. De workflow bevat twee stappen waarmee u de miniatuurgrootte van afbeeldingselementen kunt configureren. Hoewel het ene (**[!UICONTROL Dynamic Media Process Image Assets]**) wordt gebruikt voor dynamische afbeeldingselementen en het andere (**[!UICONTROL Process Thumbnails]**) voor het genereren van statische miniaturen of wanneer alle andere processen geen miniaturen genereren, moeten *both* dezelfde instellingen hebben.

Met de stap **[!UICONTROL Dynamic Media Process Image Assets]** worden miniaturen gegenereerd door de afbeeldingsserver en deze configuratie is onafhankelijk van de configuratie die op de stap **[!UICONTROL Process Thumbnails]** is toegepast. Het genereren van miniaturen via de stap **[!UICONTROL Process Thumbnails]** is de langzaamste en meest geheugenintensieve manier om miniaturen te maken.

Miniatuurgrootte wordt gedefinieerd in de volgende indeling: **[!UICONTROL width:height:center]**, bijvoorbeeld *80:80:false*. De breedte en hoogte bepalen de grootte in pixels van de miniatuur; de middelste waarde is onwaar of true en als de waarde true is, wordt aangegeven dat de miniatuurafbeelding exact dezelfde grootte heeft als in de configuratie. Als het formaat van de afbeelding kleiner is, wordt de afbeelding gecentreerd in de miniatuur.

>[!NOTE]
>
>* De miniatuurgrootte voor EPS-bestanden wordt in de stap **[!UICONTROL EPS thumbnails]** geconfigureerd op het tabblad **[!UICONTROL Arguments]** onder Miniaturen.
   >
   >
* Miniatuurgrootte voor video&#39;s wordt geconfigureerd in de stap **[!UICONTROL FFmpeg thumbnails]** op het tabblad **[!UICONTROL Process]** onder **[!UICONTROL Arguments.]**

>



**De grootte** van afbeeldingsminiaturen configureren:

1. Tik op **[!UICONTROL Tools > Workflow > Models > DAM Update Asset > Edit.]**
1. Tik op de stap **[!UICONTROL Dynamic Media Process Image Assets]** en tik of klik op de tab **[!UICONTROL Thumbnails]**. Wijzig desgewenst de miniatuurgrootte en tik op **[!UICONTROL OK.]**

   ![6_5_dynamicmediaprocessimageassets-thumbnailstab](assets/6_5_dynamicmediaprocessimageassets-thumbnailstab.png)

1. Tik op de stap **[!UICONTROL Process Thumbnails]** en tik vervolgens op het tabblad **[!UICONTROL Thumbnails]**. Wijzig desgewenst de miniatuurgrootte en tik op **[!UICONTROL OK.]**

   >[!NOTE]
   >
   >De waarden in het argument voor miniaturen in de stap **[!UICONTROL Process Thumbnails]** moeten overeenkomen met het argument voor miniaturen in de stap **[!UICONTROL Dynamic Media Process Image Assets]**.

1. Tik **[!UICONTROL Save]** om de wijzigingen in de workflow op te slaan.

### Het aantal voorinstellingen voor dynamische media-afbeeldingen waarmee {#increasing-or-decreasing-the-number-of-image-presets-that-display} wordt weergegeven verhogen of verlagen

Afbeeldingsvoorinstellingen die u maakt, zijn beschikbaar als dynamische uitvoeringen wanneer u een voorvertoning van elementen weergeeft. AEM toont een verscheidenheid van dynamische vertoningen wanneer het bekijken van activa van **[!UICONTROL Detail View > Renditions.]** U kunt de grens van vertoningen verhogen of verminderen.

**U kunt als volgt het aantal dynamische voorinstellingen voor mediagrote afbeeldingen verhogen of verlagen**:

1. Navigeer naar CRXDE Lite ([https://localhost:4502/crx/de](https://localhost:4502/crx/de)).
1. Navigeer naar het knooppunt met vooraf ingestelde lijsten voor afbeeldingen op `/libs/dam/gui/coral/content/commons/sidepanels/imagepresetsdetail/imgagepresetslist`

   ![rise_reduction ethenumberofimagepresetsthatdisplay](assets/increase_decreasethenumberofimagepresetsthatdisplay.png)

1. Wijzig in de eigenschap **[!UICONTROL limit]** de **[!UICONTROL Value]**, die standaard op 15 is ingesteld, in het gewenste getal.
1. Navigeer naar de vooraf ingestelde gegevensbron voor de afbeelding op `/libs/dam/gui/coral/content/commons/sidepanels/imagepresetsdetail/imgagepresetslist/datasource`

   ![chlimage_1-495](assets/chlimage_1-495.png)

1. Wijzig in de eigenschap limit het getal in het gewenste getal, bijvoorbeeld `{empty requestPathInfo.selectors[1] ? "20" : requestPathInfo.selectors[1]}`
1. Tik op **[!UICONTROL Save All.]**

## Een voorinstelling voor een dynamische mediafbeelding maken {#creating-image-presets}

Als u een voorinstelling voor dynamische media-afbeeldingen maakt, kunt u deze instellingen op alle afbeeldingen toepassen wanneer u een voorvertoning weergeeft of publiceert.

>[!NOTE]
>
>Als u Internet Explorer 9 gebruikt, wordt het maken van een voorinstelling niet meteen na het opslaan weergegeven in de lijst met voorinstellingen. U kunt dit probleem omzeilen door de cache voor IE9 uit te schakelen.

Als u de opname van AI-, PDF- en EPS-bestanden wilt ondersteunen, zodat u een dynamische uitvoering van deze bestandsindelingen kunt genereren, is het verstandig de volgende informatie te bekijken voordat u voorinstellingen voor afbeeldingen maakt.
Zie [Adobe Illustrator (AI), Postscript (EPS) en PDF-bestandsindelingen](#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats).

Als u de opname van INDD-bestanden wilt ondersteunen, zodat u dynamische uitvoering van deze bestandsindeling kunt genereren, is het verstandig de volgende informatie te bekijken voordat u voorinstellingen voor afbeeldingen maakt.
Zie [InDesign-bestandsindeling (INDD)](#indesign-indd-file-format).

>[!NOTE]
>
>Als u dynamische voorinstellingen voor mediabestanden wilt maken, hebt u beheerdersrechten nodig als beheerder van AEM of Admin Console.

**Een voorinstelling** voor dynamische media-afbeeldingen maken:

1. Tik in AEM op het AEM-logo om toegang te krijgen tot de globale navigatieconsole en tik vervolgens op **[!UICONTROL Tools > Assets > Image Presets.]**
1. Klik op **[!UICONTROL Create.]** Het venster **[!UICONTROL Edit Image Preset]** wordt geopend.

   ![chlimage_1-496](assets/chlimage_1-496.png)

   >[!NOTE]
   >
   >Als u deze voorinstelling responsief wilt maken, wist u de waarden in de velden **[!UICONTROL width]** en **[!UICONTROL height]** en laat u deze leeg.

1. Voer desgewenst waarden in op de tabbladen **[!UICONTROL Basic]** en **[!UICONTROL Advanced]**, inclusief een naam. De opties worden beschreven in [Opties voor afbeeldingsvoorinstellingen](#image-preset-options). Voorinstellingen worden weergegeven in het linkerdeelvenster en kunnen direct samen met andere assets worden gebruikt.

   ![6_5_imagepreset-edit](assets/6_5_imagepreset-edit.png)

1. Klik op **[!UICONTROL Save]**.

## Een responsieve voorinstelling voor een afbeelding maken {#creating-a-responsive-image-preset}

Als u een responsieve voorinstelling voor afbeeldingen wilt maken, voert u de stappen uit in [Voorinstellingen voor afbeeldingen maken](#creating-image-presets). Wis de waarden bij het invoeren van de hoogte en breedte in het venster **[!UICONTROL Edit Image Preset]** en laat ze leeg.

Als u deze leeg laat, wordt AEM aangegeven dat op deze voorinstelling kan worden gereageerd. U kunt de andere waarden desgewenst aanpassen.



>[!NOTE]
>
>Als u de knoppen **[!UICONTROL URL]** en **[!UICONTROL RESS]** wilt zien wanneer u een voorinstelling voor een afbeelding toepast op een element, moet het element worden gepubliceerd.
>
>![chlimage_1-79](assets/chlimage_1-498.png)
>
>In de modus Dynamische media - Scene7 worden afbeeldingsvoorinstellingen en afbeeldingselementen automatisch gepubliceerd.
>
>In de modus Dynamische media - hybride moet u de voorinstellingen en afbeeldingselementen van de afbeelding handmatig publiceren.

### Opties {#image-preset-options} voor voorinstellingen afbeelding

Wanneer u voorinstellingen voor afbeeldingen maakt of bewerkt, worden de opties in deze sectie beschreven. Daarnaast raadt Adobe aan om de volgende opties voor best practices te kiezen:

* **[!UICONTROL Format]** (**[!UICONTROL Basic]** tabblad) - Selecteer  **[!UICONTROL JPEG]** of een andere indeling die aan uw vereisten voldoet. Alle webbrowsers ondersteunen de JPEG-afbeeldingsindeling. Deze biedt een goede balans tussen kleine bestandsgrootten en afbeeldingskwaliteit. JPEG-afbeeldingen gebruiken echter een compressieschema met dataverlies dat ongewenste afbeeldingsartefacten kan veroorzaken als de compressie-instelling te laag is. Daarom raadt Adobe aan de compressiekwaliteit in te stellen op 75. Deze instelling biedt een goede balans tussen afbeeldingskwaliteit en kleine bestandsgrootte.

* **[!UICONTROL Enable Simple Sharpening]** - Niet selecteren **[!UICONTROL Enable Simple Sharpening]** (dit verscherpingsfilter biedt minder controle dan de instellingen voor onscherpe maskering).

* **[!UICONTROL Sharpening: Resampling Mode]** - Selecteer **[!UICONTROL Bi-Cubic.]**

#### Standaardtabopties {#basic-tab-options}

<table>
 <tbody>
  <tr>
   <td><strong>Veld</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td><strong>Naam</strong></td>
   <td>Voer een beschrijvende naam in zonder spaties. Neem de specificatie voor afbeeldingsgrootte op in de naam, zodat gebruikers deze voorinstelling voor afbeeldingen gemakkelijker kunnen herkennen.</td>
  </tr>
  <tr>
   <td><strong>Breedte en Hoogte</strong></td>
   <td>Voer in pixels de grootte in waarmee de afbeelding wordt geleverd. De breedte en hoogte moeten groter zijn dan 0 pixels. Als een van deze waarden 0 is, wordt geen voorinstelling gemaakt. Als beide waarden leeg zijn, wordt een responsieve voorinstelling voor de afbeelding gemaakt.</td>
  </tr>
  <tr>
   <td><strong>Format</strong></td>
   <td><p>Kies een indeling in het menu.</p> <p>Als u <strong>JPEG</strong> kiest, hebt u de volgende aanvullende opties:</p>
    <ul>
     <li><strong>Kwaliteit</strong>  - Hiermee bepaalt u het compressieniveau JPEG. Deze instelling is van invloed op zowel de bestandsgrootte als de afbeeldingskwaliteit. De JPEG-kwaliteitsschaal is 1-100. De schaal is zichtbaar wanneer u de schuifregelaar versleept.</li>
     <li><strong>Downsampling</strong>  van JPG-chrominantie inschakelen - Omdat het oog minder gevoelig is voor hoogfrequente kleurinformatie dan hoogfrequente luminantie, verdelen JPEG-afbeeldingen afbeeldingsgegevens in luminantie en kleurcomponenten. Wanneer een JPEG-afbeelding wordt gecomprimeerd, blijft de luminantiecomponent op volledige resolutie staan, terwijl de kleurcomponenten worden gedownsampled door het gemiddelde te nemen van groepen pixels. Door downsampling wordt het gegevensvolume met de helft of met een derde verminderd, zonder dat dit van invloed is op de waargenomen kwaliteit. Downsampling is niet van toepassing op grijswaardenafbeeldingen. Met deze techniek vermindert u de hoeveelheid compressie die handig is voor afbeeldingen met veel contrast (bijvoorbeeld afbeeldingen met overlappende tekst).</li>
    </ul>
    <div>
      Kiezen
     <strong>GIF</strong> of
     <strong>GIF met alfa</strong> biedt deze extra
     <strong>Opties voor GIF-kleurkwantiteit</strong>:
    </div>
    <ul>
     <li><strong>Type  </strong>- Selecteer  <strong>Adaptief</strong>  (standaard),  <strong>Web</strong> of  <strong>Macintosh</strong>. Als u <strong>GIF met Alpha</strong> selecteert, is de optie van Macintosh niet beschikbaar.</li>
     <li><strong>Dithering</strong>  - Selecteer  <strong></strong> Diffuus of  <strong>Uit</strong>.</li>
     <li><strong>Aantal kleuren  </strong>- Voer een getal in tussen 2 en 256.</li>
     <li><strong>Kleurenlijst</strong>  - Voer een lijst met door komma's gescheiden waarden in. Voer voor wit, grijs en zwart bijvoorbeeld 000000,888888,ffffffff in.</li>
    </ul>
    <div>
      Kiezen
     <strong>PDF</strong>,
     <strong>TIFF</strong>, of
     <strong>TIFF met alfa</strong> biedt deze extra optie:
    </div>
    <ul>
     <li><strong>Compressie</strong>  - Selecteer een compressiealgoritme. Algoritmeopties voor PDF zijn <strong>Geen</strong>, <strong>Zip</strong> en <strong>Jpeg</strong>; voor TIFF zijn <strong>Geen</strong>, <strong>LZW</strong>, <strong>Jpeg</strong> en <strong>Zip</strong>; en voor TIFF met alfa zijn <strong>Geen</strong>, <strong>LZW</strong> en <strong>Zip</strong>.</li>
    </ul> <p>Als u <strong>PNG</strong>, <strong>PNG met alfa,</strong> of <strong>EPS</strong> kiest, hebt u geen extra opties.</p> </td>
  </tr>
  <tr>
   <td><strong>Verscherpen</strong></td>
   <td>Selecteer de optie <strong>Eenvoudig verscherpen inschakelen</strong> om een standaard verscherpingsfilter toe te passen op de afbeelding nadat alle schaling heeft plaatsgevonden. Verscherpen kan helpen de vervaging te compenseren die kan optreden wanneer u een afbeelding met een andere grootte weergeeft. </td>
  </tr>
 </tbody>
</table>

#### Geavanceerde tabopties {#advanced-tab-options}

<table>
 <tbody>
  <tr>
   <td><strong>Veld</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td><strong>Kleurruimte</strong></td>
   <td>Selecteer <strong>RGB, CMYK,</strong> of <strong>Grijswaarden</strong> voor de kleurruimte.</td>
  </tr>
  <tr>
   <td><strong>Kleurprofiel</strong></td>
   <td>Selecteer het kleurruimteprofiel van de uitvoer waarnaar het element moet worden geconverteerd als het anders is dan het werkprofiel.</td>
  </tr>
  <tr>
   <td><strong>Render-intentie</strong></td>
   <td>U kunt de standaard rendering intent overschrijven. Render-intenties bepalen wat er gebeurt met kleuren die niet in het doelkleurprofiel kunnen worden gereproduceerd (buiten kleuromvang). De render-intentie wordt genegeerd als deze niet compatibel is met het ICC-profiel.
    <ul>
     <li>Selecteer <strong>Perceptueel</strong> om de totale kleuromvang van de ene kleurruimte naar een andere kleurruimte te comprimeren wanneer een of meer kleuren in de oorspronkelijke afbeelding buiten de kleuromvang van de doelkleurruimte vallen.</li>
     <li>Selecteer <strong>Relatief colorimetrisch</strong> wanneer een kleur in de huidige kleurruimte zich buiten de kleuromvang in de doelkleurruimte bevindt en u wilt deze kleur toewijzen aan de dichtstbijzijnde mogelijke kleur binnen de kleuromvang van de doelkleurruimte zonder dat dit van invloed is op andere kleuren. </li>
     <li>Selecteer <strong>Verzadiging</strong> om de oorspronkelijke kleurverzadiging van de afbeelding te reproduceren wanneer deze wordt omgezet in de doelkleurruimte. </li>
     <li>Selecteer <strong>Absoluut colorimetrisch</strong> om kleuren exact af te stemmen zonder aanpassing voor witpunt of zwartpunt die de helderheid van de afbeelding zou wijzigen.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Compensatie zwartpunt</strong></td>
   <td>Selecteer deze optie als het uitvoerprofiel deze functie ondersteunt. Zwartpuntcompensatie wordt genegeerd als deze niet compatibel is met het opgegeven ICC-profiel.</td>
  </tr>
  <tr>
   <td><strong>Dithering</strong></td>
   <td>Selecteer deze optie als u kleurstreepvorming mogelijk wilt voorkomen of verminderen. </td>
  </tr>
  <tr>
   <td><strong>Verscherpingstype</strong></td>
   <td><p>Selecteer <strong>Geen</strong>, <strong>Verscherpen</strong> of <strong>Onscherp masker</strong>. </p>
    <ul>
     <li>Selecteer <strong>Geen</strong> om verscherpen uit te schakelen.</li>
     <li>Selecteer <strong>Verscherpen </strong>om een standaard verscherpingsfilter toe te passen op de afbeelding nadat alle schaling heeft plaatsgevonden. Verscherpen kan helpen de vervaging te compenseren die kan optreden wanneer u een afbeelding met een andere grootte weergeeft. </li>
     <li>Selecteer <strong> Onscherp masker</strong> om een verscherpingsfiltereffect op het definitieve gedownsampte beeld te verfijnen. U kunt de intensiteit van het effect, de straal van het effect (gemeten in pixels) en een drempel voor het contrast instellen die wordt genegeerd. Voor dit effect worden dezelfde opties gebruikt als voor het filter Onscherp masker van Photoshop.</li>
    </ul> <p>In <strong>Onscherp masker</strong> hebt u de volgende opties:</p>
    <ul>
     <li><strong>Hoeveelheid</strong>  - Hiermee bepaalt u de hoeveelheid contrast die wordt toegepast op de randpixels. De standaardwaarde voor het reële getal is 1,0. Voor afbeeldingen met hoge resolutie kunt u de resolutie verhogen tot 5,0. Beschouw Hoeveelheid als een maat voor de filterintensiteit.</li>
     <li><strong>Straal</strong>  - Hiermee bepaalt u het aantal pixels rond de randpixels dat invloed heeft op de verscherping. Voer voor afbeeldingen met een hoge resolutie een getal in tussen 1 en 2. Bij een lage waarde worden alleen de randpixels verscherpt. met een hoge waarde wordt een grotere reeks pixels verscherpt . De juiste waarde is afhankelijk van de grootte van de afbeelding.</li>
     <li><strong>Drempel</strong>  - Hiermee bepaalt u het contrastbereik dat moet worden genegeerd wanneer het filter Onscherp masker wordt toegepast. Met andere woorden, met deze optie bepaalt u hoe verschillend de verscherpte pixels moeten zijn van het omringende gebied voordat ze als randpixels worden beschouwd en worden verscherpt. Experimenteer met gehele getallen tussen 2 en 20 om ruis te voorkomen. </li>
     <li><strong>Toepassen op</strong>  - Hiermee bepaalt u of de verscherping wordt toegepast op elke kleur of helderheid.</li>
    </ul>
    <div>
      Verscherpen wordt beschreven in
     <a href="https://docs.adobe.com/content/help/en/dynamic-media-classic/using/assets/s7_sharpening_images.pdf">Afbeeldingen verscherpen</a>.
    </div> </td>
  </tr>
  <tr>
   <td><strong>Modus voor nieuwe pixels</strong></td>
   <td>Selecteer een optie <strong>Nieuwe pixels berekenen in modus</strong>. Met deze opties verscherpt u de afbeelding wanneer deze wordt gedownsampled:
    <ul>
     <li><strong>Bi-Lineair</strong> : de snelste methode voor het berekenen van nieuwe pixels. Sommige aliasingartefacten zijn waarneembaar.</li>
     <li><strong>Bi-Cubic</strong> : verhoogt het CPU-gebruik, maar geeft scherpere afbeeldingen met minder merkbare aliasing artefacten.</li>
     <li><strong>Sharp2</strong>  - kan enigszins scherpere resultaten dan bi-Cubic, maar bij een nog hogere cpu kosten veroorzaken.</li>
     <li><strong>Bi-Sharp</strong>  - Hiermee selecteert u Photoshop standaardresampler voor het verkleinen van de afbeeldingsgrootte. Dit wordt  <strong>bicubische </strong> scherper in Adobe Photoshop genoemd.</li>
     <li><strong>Elke </strong> kleur en  <strong>helderheid</strong> : elke methode kan zijn gebaseerd op kleur of helderheid. Standaard is <strong>Elke kleur</strong> geselecteerd.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Afdrukresolutie</strong></td>
   <td>Selecteer een resolutie voor het afdrukken van deze afbeelding. 72 pixels is de standaardinstelling.</td>
  </tr>
  <tr>
   <td><strong>Afbeelding wijzigen</strong></td>
   <td><p>Naast de algemene afbeeldingsinstellingen die beschikbaar zijn in de gebruikersinterface, ondersteunt Dynamic Media talrijke geavanceerde afbeeldingswijzigingen die u kunt opgeven in het veld <strong>Afbeeldingsmodifiers</strong>. Deze parameters worden bepaald in <a href="https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html">de bevelverwijzing van het Protocol van de Server van het Beeld </a>.</p> <p>Belangrijk: De volgende functionaliteit in de API wordt niet ondersteund:</p>
    <ul>
     <li>Standaardopdrachten voor sjablonen en tekstrendering: <code>text= textAngle= textAttr= textFlowPath= textFlowXPath= textPath=</code> en <code>textPs=</code></li>
     <li>Localisatie-opdrachten: <code>locale=</code> en <code>req=xlate</code></li>
     <li><code>req=set</code> is niet beschikbaar voor algemeen gebruik.</li>
     <li><code>req=mbrset</code></li>
     <li><code>req=saveToFile</code></li>
     <li><code>req=targets</code></li>
     <li><code>template=</code></li>
     <li>Niet-kernservices voor dynamische media: SVG, Afbeelding renderen en Web-to-Print</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## Afbeeldingsvoorinstellingsopties definiëren met Afbeeldingswijzigingstoetsen {#defining-image-preset-options-with-image-modifiers}

Naast de opties op de tabbladen Standaard en Geavanceerd kunt u ook opties voor het wijzigen van afbeeldingen definiëren voor het definiëren van voorinstellingen voor afbeeldingen. Renderen van afbeeldingen is afhankelijk van de Scene7-API voor het renderen van afbeeldingen en wordt gedetailleerd gedefinieerd in de [HTTP-protocolreferentie](https://microsite.omniture.com/t2/help/en_US/s7/is_ir_api/is_api/http_ref/c_http_protocol_reference.html).

Hieronder volgen enkele basisvoorbeelden van wat u kunt doen met wijzigingstoetsen voor afbeeldingen.

>[!NOTE]
>
>Sommige afbeeldingsmodifiers [kunnen niet worden gebruikt in AEM](#advanced-tab-options).

* [op_invert](https://microsite.omniture.com/t2/help/en_US/s7/is_ir_api/is_api/http_ref/r_op_invert.html)  - Hiermee keert u elke kleurcomponent om voor een negatief afbeeldingseffect.

   ```xml
   &op_invert=1
   ```

   ![6_5_imagepreset-edit-invert](assets/6_5_imagepreset-edit-invert.png)

* [op_vervagen](https://microsite.omniture.com/t2/help/en_US/s7/is_ir_api/is_api/http_ref/r_op_blur.html)  - Hiermee past u een vervagend filter toe op de afbeelding.

   ```xml
   &op_blur=7
   ```

   ![6_5_imagepreset-edit-blur](assets/6_5_imagepreset-edit-blur.png)

* Gecombineerde opdrachten - op_vervagen en op-omkeren

   ```xml
   &op_invert=1&op_blur=7
   ```

   ![chlimage_1-80](assets/chlimage_1-501.png)

* [op_brightness](https://microsite.omniture.com/t2/help/en_US/s7/is_ir_api/is_api/http_ref/r_op_brightness.html)  - Hiermee wordt de helderheid verminderd of vermeerderd.

   ```xml
   &op_brightness=58
   ```

   ![6_5_imagepreset-edit-brightness](assets/6_5_imagepreset-edit-brightness.png)

* [opac](https://microsite.omniture.com/t2/help/en_US/s7/is_ir_api/is_api/http_ref/r_opac.html)  - Hiermee past u de dekking van de afbeelding aan. Hiermee kunt u de dekking van de voorgrond verlagen.

   ```xml
   opac=29
   ```

   ![6_5_imagepreset-edit-opacity](assets/6_5_imagepreset-edit-opacity.png)

## Voorinstellingen {#modifying-image-presets} voor afbeeldingen bewerken

1. Tik in AEM op het AEM-logo om toegang te krijgen tot de globale navigatieconsole en tik vervolgens op **[!UICONTROL Tools > Assets > Image Presets.]**

   ![6_5_imagepreset-editpreset](assets/6_5_imagepreset-editpreset.png)

1. Selecteer een voorinstelling en klik op **[!UICONTROL Edit.]** Het venster **[!UICONTROL Edit Image Preset]** wordt geopend.
1. Breng wijzigingen aan en klik op **[!UICONTROL Save]** om uw wijzigingen op te slaan of op **[!UICONTROL Cancel]** om uw wijzigingen te annuleren.

## Voorinstellingen {#publishing-image-presets} voor dynamische media-afbeeldingen publiceren

Als u de modus Dynamische media - hybride gebruikt, moet u de voorinstellingen van de afbeelding handmatig publiceren.

(Als u in de modus Dynamische media - Scene7 werkt, worden voorinstellingen voor afbeeldingen automatisch voor u gepubliceerd.) u hoeft deze stappen niet uit te voeren.)

**Voorinstellingen voor afbeeldingen publiceren in de modus** Dynamische media - Hybride:

1. Tik AEM of klik op het AEM logo om de algemene navigatieconsole te openen en tik op het pictogram Gereedschappen of navigeer naar **[!UICONTROL Assets > Image Presets.]**
1. Selecteer de afbeeldingsvoorinstelling of meerdere afbeeldingsvoorinstellingen in de lijst met voorinstellingen voor afbeeldingen en klik of tik op **[!UICONTROL Publish.]**
1. Nadat de voorinstelling voor de afbeelding is gepubliceerd, verandert de status van niet-gepubliceerd in gepubliceerd.

   ![chlimage_1-81](assets/chlimage_1-505.png)

## Voorinstellingen voor dynamische media-afbeeldingen verwijderen {#deleting-image-presets}

1. Tik of klik in AEM op het AEM logo om de globale navigatieconsole te openen.
1. Tik op het pictogram **[!UICONTROL Tools]** en navigeer naar **[!UICONTROL Assets > Image Presets.]**
1. Selecteer een voorinstelling en klik op **[!UICONTROL Delete]**. Dynamische media bevestigen dat u deze wilt verwijderen. Tik **[!UICONTROL Delete]** om **[!UICONTROL Cancel]** te verwijderen of te tikken om af te breken.

