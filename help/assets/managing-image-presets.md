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
source-git-commit: f24142064b15606a5706fe78bf56866f7f9a40ae

---


# Managing Dynamic Media image presets{#managing-image-presets}

Met voorinstellingen voor afbeeldingen kunnen AEM-elementen dynamisch afbeeldingen van verschillende grootten, in verschillende indelingen of met andere afbeeldingseigenschappen leveren die dynamisch worden gegenereerd. Elke voorinstelling voor afbeeldingen vertegenwoordigt een vooraf gedefinieerde verzameling opdrachten voor het vergroten of verkleinen en opmaken van afbeeldingen. Wanneer u een voorinstelling voor afbeeldingen maakt, kiest u een grootte voor het leveren van de afbeelding. U kiest ook opmaakopdrachten, zodat de weergave van de afbeelding wordt geoptimaliseerd wanneer de afbeelding wordt geleverd voor weergave.

Beheerders kunnen voorinstellingen maken voor het exporteren van elementen. Gebruikers kunnen bij het exporteren van afbeeldingen een voorinstelling kiezen. Hiermee worden de afbeeldingen ook opnieuw opgemaakt volgens de specificaties die de beheerder heeft opgegeven.

U kunt ook voorinstellingen voor afbeeldingen maken die reageren. Als u een voorinstelling voor een responsieve afbeelding toepast op uw elementen, worden deze afhankelijk van het apparaat of de schermgrootte waarop ze worden weergegeven. U kunt afbeeldingsvoorinstellingen zo configureren dat deze naast RGB of Grijs ook CMYK gebruiken in de kleurruimte.

In deze sectie wordt beschreven hoe u voorinstellingen voor afbeeldingen maakt, wijzigt en over het algemeen beheert. U kunt een voorinstelling voor afbeeldingen op elk gewenst moment op een afbeelding toepassen. Zie [Voorinstellingen](/help/assets/image-presets.md)voor afbeeldingen toepassen.

>[!NOTE]
>
>Slimme beeldverwerking werkt met bestaande voorinstellingen voor afbeeldingen en maakt gebruik van intelligentie tijdens de laatste milliseconde van levering om de bestandsgrootte van de afbeelding verder te beperken op basis van de snelheid van de browser of netwerkverbinding. Zie [Slimme afbeeldingen](/help/assets/imaging-faq.md) voor meer informatie.

## Understanding Dynamic Media image presets {#understanding-image-presets}

Net als bij een macro is een voorinstelling voor afbeeldingen een vooraf gedefinieerde verzameling opdrachten voor het vergroten of verkleinen en opmaken van de grootte die onder een naam zijn opgeslagen. Als u wilt weten hoe Voorinstellingen afbeelding werken, kunt u instellen dat elke productafbeelding op uw website moet worden weergegeven in verschillende formaten, formaten en compressiesnelheden voor levering op het bureaublad en op mobiele apparatuur.

U kunt twee voorinstellingen voor afbeeldingen maken: één met 500 x 500 pixels voor desktopversie en 150 x 150 pixels voor de mobiele versie. U maakt twee voorinstellingen voor afbeeldingen, een voorinstelling die wordt aangeroepen `Enlarge` om afbeeldingen met 500 x 500 pixels weer te geven en een voorinstelling die wordt aangeroepen `Thumbnail` om afbeeldingen met 150 x 150 pixels weer te geven. AEM zoekt naar de definitie van de voorinstelling Afbeelding vergroten `Enlarge` en Afbeelding met miniatuur om afbeeldingen op `Thumbnail` grootte en grootte te kunnen leveren. Vervolgens genereert AEM dynamisch een afbeelding met de grootte en opmaakspecificaties van elke voorinstelling voor afbeeldingen.

Afbeeldingen die bij dynamische levering kleiner worden gemaakt, kunnen scherper en gedetailleerder worden. Daarom bevat elke voorinstelling voor afbeeldingen opmaakbesturingselementen waarmee u een afbeelding kunt optimaliseren wanneer deze met een bepaalde grootte wordt geleverd. Met deze besturingselementen zorgt u ervoor dat uw afbeeldingen scherp en duidelijk zijn wanneer ze aan uw website of toepassing worden geleverd.

Beheerders kunnen voorinstellingen voor afbeeldingen maken. Als u een voorinstelling voor een afbeelding wilt maken, begint u helemaal opnieuw of u kunt een bestaande voorinstelling beginnen en opslaan onder een andere naam.

## Managing Dynamic Media image presets {#managing-image-presets-1}

U beheert uw voorinstellingen voor afbeeldingen in AEM door te tikken op of te klikken op het AEM-logo voor toegang tot de algemene navigatieconsole. Vervolgens tikt u op het pictogram Extra of klikt u op het pictogram Extra en navigeert u naar **[!UICONTROL Middelen > Voorinstellingen]** afbeelding.

![6_5_tools-assets-imagepresets](assets/6_5_tools-assets-imagepresets.png)

>[!NOTE]
>
>Alle afbeeldingsvoorinstellingen die u maakt, zijn ook beschikbaar als dynamische uitvoeringen wanneer u elementen voorvertoont of levert.
>
>In *Dynamische Media - wijze* Scene7, te hoeven u *niet* beeldvoorinstellingen te publiceren aangezien de beeld vooraf instelt automatisch worden gepubliceerd.
>
>In de modus ** Dynamische media - hybride moet u de voorinstellingen van de afbeelding handmatig publiceren.
>
>Zie Voorinstellingen afbeelding [publiceren.](#publishing-image-presets)

>[!NOTE]
>
>Het systeem toont een verscheidenheid van vertoningen wanneer u **[!UICONTROL Vertoningen]** in de Mening van het Detail van activa selecteert. U kunt het aantal voorinstellingen voor afbeeldingen dat wordt weergegeven, verhogen of verlagen. See [Increasing the number of image presets that display](#increasingthenumberofimagepresetsthatdisplay).

### Adobe Illustrator (AI)-, PostScript (EPS)- en PDF-bestandsindelingen {#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats}

Als u de opname van AI-, EPS- en PDF-bestanden wilt ondersteunen, zodat u dynamische uitvoeringen van deze bestandsindelingen kunt genereren, is het verstandig de volgende informatie te bekijken voordat u voorinstellingen voor afbeeldingen maakt.

De bestandsindeling van Adobe Illustrator is een variant van PDF. De belangrijkste verschillen in de context van AEM Assets zijn de volgende:

* Adobe Illustrator-documenten bestaan uit één pagina met meerdere lagen. Elke laag wordt geëxtraheerd als een PNG-subelement onder het hoofdelement van Illustrator.
* PDF-documenten bestaan uit een of meer pagina&#39;s. Elke pagina wordt uitgepakt als een PDF-subelement van één pagina onder het PDF-hoofddocument met meerdere pagina&#39;s.

De subelementen worden door de `Create Sub Asset process` component binnen de algemene `DAM Update Asset` workflow gemaakt. Tik op **[!UICONTROL Gereedschappen > Workflow > Modellen > DAM-updateelement > Bewerken]** om deze procescomponent in de workflow te zien.

Zie ook Pagina&#39;s van een bestand [](/help/assets/managing-linked-subassets.md#view-pages-of-a-multi-page-file)met meerdere pagina&#39;s weergeven.

U kunt de submiddelen of de pagina&#39;s weergeven wanneer u het element opent, tikken op het menu Inhoud en vervolgens **[!UICONTROL Submiddelen]** of **[!UICONTROL Pagina]**&#39;s selecteren. De subactiva zijn reële activa. Dat wil zeggen dat PDF-pagina&#39;s worden geëxtraheerd door de `Create Sub Asset` workflowcomponent. Ze worden vervolgens opgeslagen als `page1.pdf`, `page2.pdf`enzovoort, onder het hoofdmiddel. Nadat ze zijn opgeslagen, worden ze door de `DAM Update Asset` workflow verwerkt.

Met Dynamische media kunt u dynamische uitvoeringen voor AI-, EPS- of PDF-bestanden voorvertonen en genereren. Hiervoor zijn de volgende verwerkingsstappen vereist:

1. In het `DAM Update Asset` werkschema, rasterizes de `Rasterize PDF/AI Image Preview Rendition` procescomponent de eerste pagina van origineel element-gebruikend gevormde resolutie-in een `cqdam.preview.png` vertoning.

1. De `cqdam.preview.png` uitvoering wordt vervolgens in een PTIFF-bestand geoptimaliseerd door de `Dynamic Media Process Image Assets` procescomponent in de workflow.

>[!NOTE]
>
>In the [!UICONTROL DAM Update Asset] workflow, the **[!UICONTROL EPS thumbnails]** step generates thumbnails for EPS files.

#### Eigenschappen van PDF/AI/EPS-metagegevens {#pdf-ai-eps-asset-metadata-properties}

| **Eigenschap Metadata** | **Beschrijving** |
|---|---|
| dam:Physicalwidthinches | Documentbreedte in inches. |
| dam:Physicalheightininches | Documenthoogte in inches. |

Via de `Rasterize PDF/AI Image Preview Rendition` workflow hebt u toegang tot opties voor `DAM Update Asset` procescomponenten.

Tik linksboven op Adobe Experience Manager en navigeer naar **[!UICONTROL Extra > Workflow > Modellen]**. Selecteer op de pagina Workflowmodellen de optie **[!UICONTROL DAM Update Asset]** en tik vervolgens op de werkbalk op **[!UICONTROL Bewerken]**. Dubbeltik op de [!UICONTROL DAM-werkstroompagina Element] bijwerken op de `Rasterize PDF/AI Image Preview Rendition` procescomponent om het dialoogvenster Step Properties te openen.

#### Opties van PDF/AI-voorvertoning van afbeelding omzetten in pixels {#rasterize-pdf-ai-image-preview-rendition-options}

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
   <td><p>application/pdf</p> <p>application/postscript</p> <p>toepassing/illustrator<br /> </p> </td>
   <td>Lijst met documenttypen die als PDF- of Illustrator-documenten worden beschouwd.<br /> </td>
  </tr>
  <tr>
   <td>Max. breedte</td>
   <td>2048</td>
   <td>Maximale breedte van de gegenereerde voorvertoning, in pixels.<br /> </td>
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

Voor de `Rasterize PDF/AI Image Preview Rendition` procescomponent is een maximum gedefinieerd, zodat er geen te grote afbeeldingen in het geheugen worden gemaakt. Dergelijke grote afbeeldingen kunnen het geheugen overlopen dat aan de JVM (Java Virtual Machine) wordt geleverd. Er moet op worden gelet dat de JVM over voldoende geheugen beschikt om het geconfigureerde aantal parallelle workflows te beheren, waarbij elk van beide de mogelijkheid heeft om een image op de maximaal geconfigureerde grootte te maken.

### InDesign-bestandsindeling (INDD) {#indesign-indd-file-format}

Als u de opname van INDD-bestanden wilt ondersteunen, zodat u dynamische uitvoering van deze bestandsindeling kunt genereren, is het verstandig de volgende informatie te bekijken voordat u voorinstellingen voor afbeeldingen maakt.

Voor InDesign-bestanden worden subelementen alleen geëxtraheerd als de Adobe InDesign-server is geïntegreerd met AEM. Elementen waarnaar wordt verwezen, zijn gekoppeld op basis van hun metagegevens. InDesign Server is niet vereist voor koppelingen. De bestanden waarnaar wordt verwezen, moeten echter aanwezig zijn in AEM voordat de InDesign-bestanden worden verwerkt, zodat de koppelingen tussen de InDesign-bestanden en de bestanden waarnaar wordt verwezen, kunnen worden gemaakt.

Zie AEM-elementen [integreren met InDesign Server](/help/assets/indesign.md).

Met de component Media Extraction Process in de `DAM Update Asset` workflow worden verschillende vooraf geconfigureerde Extend Scripts uitgevoerd voor het verwerken van InDesign-bestanden.

![De ExtendScript-paden in de argumenten van Media Extraction-proces](assets/6_5_mediaextractionprocess.png)

De ExtendScript-paden in de argumenten van Media Extraction Process-component in de [!UICONTROL DAM Update Asset] -workflow.

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
   <td>Genereert een 300 ppi- <code>thumbnail.jpg</code> uitvoering die is geoptimaliseerd en door <code>Dynamic Media Process Image Assets</code> procescomponent is omgezet in een PTIFF-uitvoering.<br /> </td>
  </tr>
  <tr>
   <td>JPEGPagesExport.jsx</td>
   <td>Ja</td>
   <td>Hiermee genereert u een JPEG-subelement van 300 ppi voor elke pagina. Het JPEG-subelement is een echt middel dat wordt opgeslagen onder het InDesign-element. Het wordt ook geoptimaliseerd en door de <code>DAM Update Asset</code> workflow omgezet in een PTIFF-bestand.<br /> </td>
  </tr>
  <tr>
   <td>PDFPagesExport.jsx</td>
   <td>Nee</td>
   <td>Hiermee genereert u een PDF-subelement voor elke pagina. Het PDF-subelement wordt verwerkt zoals eerder beschreven. Omdat de PDF slechts één pagina bevat, worden geen subelementen gegenereerd.<br /> </td>
  </tr>
 </tbody>
</table>

## Miniatuurgrootte van afbeelding configureren {#configuring-image-thumbnail-size}

U kunt de grootte van miniaturen configureren door deze instellingen te configureren in de workflow **[!UICONTROL DAM-element]** bijwerken. De workflow bevat twee stappen waarmee u de miniatuurgrootte van afbeeldingselementen kunt configureren. Hoewel het ene (**[!UICONTROL Dynamische Media Process Image Assets]**) wordt gebruikt voor dynamische afbeeldingselementen en het andere (**[!UICONTROL Process Thumbnails]**) voor het genereren van statische miniaturen of wanneer bij alle andere processen geen miniaturen worden gegenereerd, moeten *beide* dezelfde instellingen hebben.

With the **[!UICONTROL Dynamic Media Process Image Assets]** step, thumbnails are generated by the image server, and this configuration is independent of the configuration applied to the **[!UICONTROL Process Thumbnails]** step. Generating thumbnails through the **[!UICONTROL Process Thumbnails]** step is the slowest and most memory intensive way to create thumbnails.

Miniatuurgrootte wordt gedefinieerd in de volgende indeling: **[!UICONTROL width:height:center]**, bijvoorbeeld *80:80:false*. De breedte en hoogte bepalen de grootte in pixels van de miniatuur; de middelste waarde is onwaar of true en als de waarde true is, wordt aangegeven dat de miniatuurafbeelding exact dezelfde grootte heeft als in de configuratie. Als het formaat van de afbeelding kleiner is, wordt de afbeelding gecentreerd in de miniatuur.

>[!NOTE]
>
>* Thumbnail size for EPS files are configured in the **[!UICONTROL EPS thumbnails]** step, in the **[!UICONTROL Arguments]** tab under Thumbnails.
   >
   >
* Thumbnail size for videos are configured in the **[!UICONTROL FFmpeg thumbnails]** step, in the **[!UICONTROL Process]** tab under **[!UICONTROL Arguments]**.
>



**De grootte** van afbeeldingsminiaturen configureren:

1. Tik op **[!UICONTROL Extra > Workflow > Modellen > DAM Update Asset > Edit]**.
1. Tik op de stap Afbeeldingselementen **[!UICONTROL van dynamisch mediaproces en tik op het tabblad]** Miniaturen **** of klik op deze knop. Change the thumbnail size, as needed, then tap **[!UICONTROL OK]**.

   ![6_5_dynamicmediaprocessimageassets-thumbnailstab](assets/6_5_dynamicmediaprocessimageassets-thumbnailstab.png)

1. Tik op de stap Miniaturen **** verwerken en tik vervolgens op het tabblad **[!UICONTROL Miniaturen]** . Change the thumbnail size, as needed, then tap **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >De waarden in het miniatuurargument in de stap Miniaturen **** verwerken moeten overeenkomen met het miniatuurargument in de stap Afbeeldingselementen **[!UICONTROL verwerken van]** dynamische media.

1. Tik op **[!UICONTROL Opslaan]** om de wijzigingen in de workflow op te slaan.

### Het aantal voorinstellingen voor dynamische media-afbeeldingen dat wordt weergegeven verhogen of verlagen {#increasing-or-decreasing-the-number-of-image-presets-that-display}

Afbeeldingsvoorinstellingen die u maakt, zijn beschikbaar als dynamische uitvoeringen wanneer u een voorvertoning van elementen weergeeft. In AEM worden diverse dynamische uitvoeringen weergegeven wanneer u elementen weergeeft vanuit **[!UICONTROL Gedetailleerde weergave > Uitvoeringen]**. U kunt de limiet van weergegeven uitvoeringen verhogen of verlagen.

**U kunt als volgt het aantal dynamische voorinstellingen voor mediagrote afbeeldingen verhogen of verlagen**:

1. Navigeer naar CRXDE Lite ([https://localhost:4502/crx/de](https://localhost:4502/crx/de)).
1. Navigeer naar het knooppunt met vooraf ingestelde lijsten voor afbeeldingen op `/libs/dam/gui/coral/content/commons/sidepanels/imagepresetsdetail/imgagepresetslist`

   ![rise_reduction ethenumberofimagepresetsthatdisplay](assets/increase_decreasethenumberofimagepresetsthatdisplay.png)

1. In the **[!UICONTROL limit]** property, change the **[!UICONTROL Value]**, which is set to 15 by default, to the desired number.
1. Navigeer naar de gegevensbron voor de afbeeldingsvoorinstelling op `/libs/dam/gui/coral/content/commons/sidepanels/imagepresetsdetail/imgagepresetslist/datasource`

   ![chlimage_1-495](assets/chlimage_1-495.png)

1. Wijzig in de eigenschap limit het getal in het gewenste getal, bijvoorbeeld `{empty requestPathInfo.selectors[1] ? "20" : requestPathInfo.selectors[1]}`
1. Tik op Alles **** opslaan.

## Een voorinstelling voor een dynamische mediaafbeelding maken {#creating-image-presets}

Als u een voorinstelling voor dynamische media-afbeeldingen maakt, kunt u deze instellingen op alle afbeeldingen toepassen wanneer u een voorvertoning weergeeft of publiceert.

>[!NOTE]
>
>Als u Internet Explorer 9 gebruikt, wordt het maken van een voorinstelling niet meteen na het opslaan weergegeven in de lijst met voorinstellingen. U kunt dit probleem omzeilen door de cache voor IE9 uit te schakelen.

Als u de opname van AI-, PDF- en EPS-bestanden wilt ondersteunen, zodat u een dynamische uitvoering van deze bestandsindelingen kunt genereren, is het verstandig de volgende informatie te bekijken voordat u voorinstellingen voor afbeeldingen maakt.
Zie [Adobe Illustrator (AI), PostScript (EPS) en PDF-bestandsindelingen](#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats).

Als u de opname van INDD-bestanden wilt ondersteunen, zodat u dynamische uitvoering van deze bestandsindeling kunt genereren, is het verstandig de volgende informatie te bekijken voordat u voorinstellingen voor afbeeldingen maakt.
Zie [De bestandsindeling](#indesign-indd-file-format)InDesign (INDD).

>[!NOTE]
>
>Als u dynamische voorinstellingen voor mediafobeeldingen wilt maken, moet u beheerdersrechten hebben als AEM-beheerder of beheerder van beheerconsole.

**Een voorinstelling** voor dynamische media-afbeeldingen maken:

1. In AEM, tap the AEM logo to access the global navigation console, then tap **[!UICONTROL Tools > Assets > Image Presets]**.
1. Klik op **[!UICONTROL Maken]**. Het venster Voorinstelling afbeelding **[!UICONTROL bewerken wordt geopend]** .

   ![chlimage_1-496](assets/chlimage_1-496.png)

   >[!NOTE]
   >
   >To make this image preset responsive, erase the values in the **[!UICONTROL width]** and **[!UICONTROL height]** fields and leave them blank.

1. Enter values into the **[!UICONTROL Basic]** and **[!UICONTROL Advanced]** tabs as appropriate, including a name. De opties worden beschreven in [Opties voor afbeeldingsvoorinstellingen](#image-preset-options). Voorinstellingen worden weergegeven in het linkerdeelvenster en kunnen direct samen met andere assets worden gebruikt.

   ![6_5_imagepreset-edit](assets/6_5_imagepreset-edit.png)

1. Klik op **[!UICONTROL opslaan**.

## Creating a responsive image preset {#creating-a-responsive-image-preset}

Als u een responsieve voorinstelling voor afbeeldingen wilt maken, voert u de stappen uit in Voorinstellingen [voor](#creating-image-presets)afbeeldingen maken. Wanneer u de hoogte en breedte invoert in het venster Voorinstelling **[!UICONTROL afbeelding]** bewerken, wist u de waarden en laat u deze leeg.

Als u deze leeg laat, weet AEM dat op deze voorinstelling kan worden gereageerd. U kunt de andere waarden desgewenst aanpassen.



>[!NOTE]
>
>In order to see the **[!UICONTROL URL]** and **[!UICONTROL RESS]** buttons when applying an image preset to an asset, the asset must be published.
>
>![chlimage_1-79](assets/chlimage_1-498.png)
>
>In Dynamische Media - wijze Scene7, vooraf instelt beeld en beeldactiva worden automatisch gepubliceerd.
>
>In de modus Dynamische media - hybride moet u de voorinstellingen en afbeeldingselementen van de afbeelding handmatig publiceren.

### Voorinstellingsopties voor afbeelding {#image-preset-options}

Wanneer u voorinstellingen voor afbeeldingen maakt of bewerkt, worden de opties in deze sectie beschreven. Daarnaast raadt Adobe aan om de volgende opties voor beste praktijken te kiezen:

* **[!UICONTROL Format** (tabblad **[!UICONTROL Standaard]** ) - Selecteer **[!UICONTROL JPEG]** of een andere indeling die aan uw vereisten voldoet. Alle webbrowsers ondersteunen de JPEG-afbeeldingsindeling. Deze biedt een goede balans tussen kleine bestandsgrootten en afbeeldingskwaliteit. JPEG-afbeeldingen gebruiken echter een compressieschema met dataverlies dat ongewenste afbeeldingsartefacten kan veroorzaken als de compressie-instelling te laag is. Daarom raadt Adobe aan de compressiekwaliteit in te stellen op 75. Deze instelling biedt een goede balans tussen afbeeldingskwaliteit en kleine bestandsgrootte.

* **[!UICONTROL Eenvoudig verscherpen]** inschakelen - Selecteer **[!UICONTROL Eenvoudig verscherpen]** niet inschakelen (dit verscherpingsfilter biedt minder controle dan de instellingen voor Onscherp masker).

* **[!UICONTROL Verscherpen: Modus]** Nieuwe pixels berekenen - Selecteer **[!UICONTROL Bi-Cubic]**.

#### Opties op het tabblad Standaard {#basic-tab-options}

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
     <li><strong>Kwaliteit</strong> - Hiermee bepaalt u het compressieniveau JPEG. Deze instelling is van invloed op zowel de bestandsgrootte als de afbeeldingskwaliteit. De JPEG-kwaliteitsschaal is 1-100. De schaal is zichtbaar wanneer u de schuifregelaar versleept.</li>
     <li><strong>Downsampling</strong> van JPG-chrominantie inschakelen - Omdat het oog minder gevoelig is voor hoogfrequente kleurinformatie dan hoogfrequente luminantie, verdelen JPEG-afbeeldingen afbeeldingsgegevens in luminantie en kleurcomponenten. Wanneer een JPEG-afbeelding wordt gecomprimeerd, blijft de luminantiecomponent op volledige resolutie staan, terwijl de kleurcomponenten worden gedownsampled door het gemiddelde te nemen van groepen pixels. Door downsampling wordt het gegevensvolume met de helft of met een derde verminderd, zonder dat dit van invloed is op de waargenomen kwaliteit. Downsampling is niet van toepassing op grijswaardenafbeeldingen. Met deze techniek vermindert u de hoeveelheid compressie die handig is voor afbeeldingen met veel contrast (bijvoorbeeld afbeeldingen met overlappende tekst).</li>
    </ul>
    <div>
      Als u <strong>GIF</strong> of <strong>GIF met alfa</strong> kiest, kunt u de volgende aanvullende opties voor de kwantiteit <strong>van</strong> GIF-kleuren kiezen:
    </div>
    <ul>
     <li><strong>Type </strong>- Selecteer <strong>Adaptief</strong> (standaard), <strong>Web</strong>of <strong>Macintosh</strong>. If you select <strong>GIF with Alpha</strong>, the Macintosh option is not available.</li>
     <li><strong>Dithering</strong> - Selecteer <strong>Diffuus</strong> of <strong>Uit</strong>.</li>
     <li><strong>Aantal kleuren </strong>- Voer een getal in tussen 2 en 256.</li>
     <li><strong>Kleurenlijst</strong> - voer een lijst in met door komma's gescheiden waarden. Voer voor wit, grijs en zwart bijvoorbeeld 000000,888888,ffffffff in.</li>
    </ul>
    <div>
      Als u <strong>PDF</strong>, <strong>TIFF</strong>of <strong>TIFF met alfa</strong> kiest, kunt u het volgende instellen:
    </div>
    <ul>
     <li><strong>Compressie</strong> - Selecteer een compressiealgoritme. Algoritmeopties voor PDF zijn <strong>Geen</strong>, <strong>Postcode</strong>en <strong>JPEG</strong>; voor TIFF zijn <strong>None</strong>, <strong>LZW</strong>, <strong>Jpeg</strong>en <strong>Zip</strong>; en voor TIFF met alfa zijn <strong>Geen</strong>, <strong>LZW</strong>en <strong>Zip</strong>.</li>
    </ul> <p>Het kiezen van <strong>PNG</strong>, <strong>PNG met Alpha,</strong> of <strong>EPS</strong> verstrekt geen extra opties.</p> </td>
  </tr>
  <tr>
   <td><strong>Verscherpen</strong></td>
   <td>Selecteer de optie <strong>Eenvoudig verscherpen</strong> inschakelen om een standaard verscherpingsfilter toe te passen op de afbeelding nadat alle schaling heeft plaatsgevonden. Verscherpen kan helpen de vervaging te compenseren die kan optreden wanneer u een afbeelding met een andere grootte weergeeft. </td>
  </tr>
 </tbody>
</table>

#### Opties op het tabblad Geavanceerd {#advanced-tab-options}

<table>
 <tbody>
  <tr>
   <td><strong>Veld</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td><strong>Kleurruimte</strong></td>
   <td>Selecteer <strong>RGB,</strong> CMYK of <strong>Grijswaarden</strong> voor de kleurruimte.</td>
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
     <li>Selecteer <strong>Verzadiging</strong> om de oorspronkelijke kleurverzadiging van de afbeelding weer te geven bij de omzetting in de doelkleurruimte. </li>
     <li>Selecteer <strong>Absoluut colorimetrisch</strong> om de kleuren exact af te stemmen zonder aanpassing voor het witpunt of zwartpunt waardoor de helderheid van de afbeelding wordt gewijzigd.</li>
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
   <td><p>Selecteer <strong>Geen</strong>, <strong>Verscherpen</strong>of <strong>Onscherp masker</strong>. </p>
    <ul>
     <li>Selecteer <strong>Geen</strong> om verscherpen uit te schakelen.</li>
     <li>Selecteer <strong>Verscherpen </strong>om een standaard verscherpingsfilter toe te passen op de afbeelding nadat alle schaling heeft plaatsgevonden. Verscherpen kan helpen de vervaging te compenseren die kan optreden wanneer u een afbeelding met een andere grootte weergeeft. </li>
     <li>Select<strong> Unsharp mask</strong> to fine-tune a sharpening filter effect on the final downsampled image. U kunt de intensiteit van het effect, de straal van het effect (gemeten in pixels) en een drempel voor het contrast instellen die wordt genegeerd. Voor dit effect worden dezelfde opties gebruikt als voor het filter Onscherp masker van Photoshop.</li>
    </ul> <p>In <strong>Onscherp masker</strong>hebt u de volgende opties:</p>
    <ul>
     <li><strong>Hoeveelheid</strong> - Hiermee bepaalt u de hoeveelheid contrast die wordt toegepast op de randpixels. De standaardwaarde voor het reële getal is 1,0. Voor afbeeldingen met hoge resolutie kunt u de resolutie verhogen tot 5,0. Beschouw Hoeveelheid als een maat voor de filterintensiteit.</li>
     <li><strong>Straal</strong> - Hiermee bepaalt u het aantal pixels rondom de randpixels dat invloed heeft op de verscherping. Voer voor afbeeldingen met een hoge resolutie een getal in tussen 1 en 2. Bij een lage waarde worden alleen de randpixels verscherpt. met een hoge waarde wordt een grotere reeks pixels verscherpt . De juiste waarde is afhankelijk van de grootte van de afbeelding.</li>
     <li><strong>Drempel</strong> - Hiermee bepaalt u het contrastbereik dat moet worden genegeerd wanneer het filter Onscherp masker wordt toegepast. Met andere woorden, met deze optie bepaalt u hoe verschillend de verscherpte pixels moeten zijn van het omringende gebied voordat ze als randpixels worden beschouwd en worden verscherpt. Experimenteer met gehele getallen tussen 2 en 20 om ruis te voorkomen. </li>
     <li><strong>Toepassen op</strong> - Hiermee wordt bepaald of de verscherping wordt toegepast op elke kleur of helderheid.</li>
    </ul>
    <div>
      Verscherpen wordt beschreven in <a href="https://docs.adobe.com/content/help/en/dynamic-media-classic/using/assets/s7_sharpening_images.pdf">Verscherpen van afbeeldingen</a>.
    </div> </td>
  </tr>
  <tr>
   <td><strong>Modus voor nieuwe pixels</strong></td>
   <td>Selecteer een optie voor de modus <strong></strong> Nieuwe pixels berekenen. Met deze opties verscherpt u de afbeelding wanneer deze wordt gedownsampled:
    <ul>
     <li><strong>Bi-Lineair</strong> : de snelste methode voor het berekenen van nieuwe pixels. Sommige aliasingartefacten zijn waarneembaar.</li>
     <li><strong>Bi-Cubic</strong> : verhoogt het CPU-gebruik, maar geeft scherpere beelden met minder merkbare aliasing artefacten.</li>
     <li><strong>Sharp2</strong> - kan enigszins scherpere resultaten dan bi-Cubic, maar bij een nog hogere cpu kosten veroorzaken.</li>
     <li><strong>Bi-Sharp</strong> - Hiermee selecteert u standaardresampler voor Photoshop voor het verkleinen van de afbeeldingsgrootte. Dit wordt in Adobe Photoshop <strong>bicubisch scherper</strong> genoemd.</li>
     <li><strong>Elke kleur</strong> en <strong>Helderheid</strong> - elke methode kan op kleur of helderheid worden gebaseerd. Standaard is <strong>Elke kleur</strong> geselecteerd.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Afdrukresolutie</strong></td>
   <td>Selecteer een resolutie voor het afdrukken van deze afbeelding. 72 pixels is de standaardinstelling.</td>
  </tr>
  <tr>
   <td><strong>Afbeelding wijzigen</strong></td>
   <td><p>Naast de algemene afbeeldingsinstellingen die beschikbaar zijn in de gebruikersinterface, ondersteunt Dynamic Media talrijke geavanceerde afbeeldingswijzigingen die u kunt opgeven in het veld <strong>Afbeeldingswijzigingstoetsen</strong> . Deze parameters worden bepaald in de het bevelverwijzing <a href="https://marketing.adobe.com/resources/help/en_US/s7/is_ir_api/is_api/http_ref/c_command_reference.html">van het Protocol van de Server van het</a>Beeld.</p> <p>Belangrijk: De volgende functionaliteit in de API wordt niet ondersteund:</p>
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

## Voorinstellingsopties voor afbeeldingen definiëren met afbeeldingswijzigingstoetsen {#defining-image-preset-options-with-image-modifiers}

Naast de opties op de tabbladen Standaard en Geavanceerd kunt u ook opties voor het wijzigen van afbeeldingen definiëren voor het definiëren van voorinstellingen voor afbeeldingen. Het teruggeven van het beeld baseert zich op Scene7 beeld die API teruggeeft en in detail bepaald in de Verwijzing [van het](https://microsite.omniture.com/t2/help/en_US/s7/is_ir_api/is_api/http_ref/c_http_protocol_reference.html)HTTP- Protocol.

Hieronder volgen enkele basisvoorbeelden van wat u kunt doen met wijzigingstoetsen voor afbeeldingen.

>[!NOTE]
>
>Sommige afbeeldingsmodifiers [kunnen niet worden gebruikt in AEM](#advanced-tab-options).

* [op_invert](https://microsite.omniture.com/t2/help/en_US/s7/is_ir_api/is_api/http_ref/r_op_invert.html) - Hiermee keert u elke kleurcomponent om voor een negatief afbeeldingseffect.

   ```xml
   &op_invert=1
   ```

   ![6_5_imagepreset-edit-invert](assets/6_5_imagepreset-edit-invert.png)

* [op_vervagen](https://microsite.omniture.com/t2/help/en_US/s7/is_ir_api/is_api/http_ref/r_op_blur.html) - Hiermee past u een vervagend filter toe op de afbeelding.

   ```xml
   &op_blur=7
   ```

   ![6_5_imagepreset-edit-blur](assets/6_5_imagepreset-edit-blur.png)

* Gecombineerde opdrachten - op_vervagen en op-omkeren

   ```xml
   &op_invert=1&op_blur=7
   ```

   ![chlimage_1-80](assets/chlimage_1-501.png)

* [op_brightness](https://microsite.omniture.com/t2/help/en_US/s7/is_ir_api/is_api/http_ref/r_op_brightness.html) - Hiermee wordt de helderheid verminderd of vermeerderd.

   ```xml
   &op_brightness=58
   ```

   ![6_5_imagepreset-edit-brightness](assets/6_5_imagepreset-edit-brightness.png)

* [opac](https://microsite.omniture.com/t2/help/en_US/s7/is_ir_api/is_api/http_ref/r_opac.html) - Hiermee past u de dekking van de afbeelding aan. Hiermee kunt u de dekking van de voorgrond verlagen.

   ```xml
   opac=29
   ```

   ![6_5_imagepreset-edit-opacity](assets/6_5_imagepreset-edit-opacity.png)

## Voorinstellingen voor afbeeldingen bewerken {#modifying-image-presets}

1. In AEM, tap the AEM logo to access the global navigation console, then tap **[!UICONTROL Tools > Assets > Image Presets]**.

   ![6_5_imagepreset-editpreset](assets/6_5_imagepreset-editpreset.png)

1. Selecteer een voorinstelling en klik op **[!UICONTROL Bewerken]**. Het venster Voorinstelling afbeelding **[!UICONTROL bewerken wordt geopend]** .
1. Breng wijzigingen aan en klik op **[!UICONTROL Opslaan]** om de wijzigingen op te slaan of **[!UICONTROL Annuleren]** om de wijzigingen te annuleren.

## Publishing Dynamic Media image presets {#publishing-image-presets}

Als u de modus Dynamische media - hybride gebruikt, moet u de voorinstellingen van de afbeelding handmatig publiceren.

(Als u Dynamische Media - wijze Scene7 in werking stelt, worden de beeldvoorinstellingen automatisch gepubliceerd voor u; u hoeft deze stappen niet uit te voeren.)

**Voorinstellingen voor afbeeldingen publiceren in de modus** Dynamische media - Hybride:

1. Tik of klik in AEM op het AEM-logo om de algemene navigatieconsole te openen en tik op het pictogram Gereedschappen of klik op dit pictogram en navigeer naar **[!UICONTROL Middelen > Voorinstellingen]** afbeelding.
1. Selecteer de voorinstelling voor de afbeelding of meerdere voorinstellingen voor de afbeelding in de lijst met voorinstellingen voor afbeeldingen en klik op **[!UICONTROL Publiceren]** of tik op Publiceren.
1. Nadat de voorinstelling voor de afbeelding is gepubliceerd, verandert de status van niet-gepubliceerd in gepubliceerd.

   ![chlimage_1-81](assets/chlimage_1-505.png)

## Deleting Dynamic Media image presets {#deleting-image-presets}

1. Tik in AEM op het AEM-logo of klik hierop om de globale navigatieconsole te openen.
1. Tik op het pictogram **[!UICONTROL Gereedschappen]** en navigeer naar **[!UICONTROL Middelen > Voorinstellingen]** afbeelding.
1. Selecteer een voorinstelling en klik op **[!UICONTROL verwijderen**. Dynamische media bevestigen dat u deze wilt verwijderen. Tik op **[!UICONTROL Verwijderen]** om te verwijderen of tik op **[!UICONTROL Annuleren]** om af te breken.

