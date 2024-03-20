---
title: Afbeeldingstransformatiebibliotheek
description: Leer hoe u de Imaging Transcoding Library van Adobe configureert en gebruikt, een oplossing voor beeldverwerking die kernfuncties voor het verwerken van afbeeldingen kan uitvoeren, zoals codering, transcodering, het resamplen van afbeeldingen en het vergroten of verkleinen van afbeeldingen.
contentOwner: AG
role: Admin
feature: Renditions,Developer Tools,Asset Processing
exl-id: b67465f9-177c-49c4-b4eb-a1d6e09ac9a2
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '925'
ht-degree: 0%

---

# Afbeeldingstransformatiebibliotheek {#imaging-transcoding-library}

De imaging Transcoding Library van Adobe is een merkgebonden oplossing voor beeldverwerking die kernfuncties voor beeldverwerking kan uitvoeren, zoals:

* Codering
* Transcodering (ondersteunde indelingen converteren)
* Nieuwe beeldpixels berekenen, met PS- en Intel IPP-algoritmen
* Bitdiepte en kleurprofiel behouden
* JPEG-kwaliteitscompressie
* Afbeeldingsformaat wijzigen

De bibliotheek voor grafische transformatie biedt CMYK-ondersteuning en volledige alfaondersteuning, behalve CMYK-Alpha.

Naast de ondersteuning van een groot aantal bestandsindelingen en profielen biedt de Imaging Transcoding Library aanzienlijke voordelen ten opzichte van andere oplossingen van derden op het gebied van prestaties, schaalbaarheid en kwaliteit. Hier volgen enkele belangrijke voordelen van het gebruik van de bibliotheek voor het transformeren van afbeeldingen:

* **Schalen met grotere bestandsgrootte of resolutie**: Schalen wordt vooral bereikt door de gepatenteerde mogelijkheid om de afbeeldingstransformatiebibliotheek tijdens het decoderen van bestanden te vergroten of te verkleinen. Hierdoor wordt gegarandeerd dat het runtimegeheugengebruik altijd optimaal is en geen kwadratische functie is om de bestandsgrootte of resolutie van megapixels te verhogen. De bibliotheek voor het transformeren van afbeeldingen kan grotere en hoge-resolutiebestanden (met hogere megapixels) verwerken. Gereedschappen van derden, zoals ImageMagick, kunnen grote bestanden en vastlopen niet verwerken tijdens het verwerken van dergelijke bestanden.
* **Compressie- en formaatalgoritmen voor Photoshop-kwaliteit**: Consistentie met de industriestandaard op het gebied van kwaliteit van downsampling (vloeiend, scherp en automatisch bicubisch) en compressie. De bibliotheek voor grafische transformatie beoordeelt verder de kwaliteitsfactor van de invoerafbeelding en gebruikt op intelligente wijze optimale tabellen en kwaliteitsinstellingen voor de uitvoerafbeelding. Hierdoor ontstaan bestanden van optimale grootte zonder dat dit ten koste gaat van de visuele kwaliteit.
* **Hoge doorvoer:** De reactietijd is lager en de productie is constant hoger dan ImageMagick. Daarom moet de bibliotheek voor het transformeren van afbeeldingen de wachttijd voor gebruikers en de hostingkosten verlagen.
* **Beter schalen bij gelijktijdig laden:** De afbeeldingstransformatiebibliotheek functioneert optimaal onder gelijktijdige laadvoorwaarden. Deze server biedt een hoge doorvoer met optimale CPU-prestaties, een optimaal geheugengebruik en een lage responstijd, wat de hostingkosten helpt te verlagen.

## Ondersteunde platforms {#supported-platforms}

Imaging Transcoding Library is alleen beschikbaar voor RHEL 7- en CentOS 7-distributies.

>[!NOTE]
>
>Mac OS en andere *nix-distributies (bijvoorbeeld Debian en Ubuntu) worden niet ondersteund.

## Gebruik {#usage}

De opdrachtregelargumenten voor de bibliotheek voor het transformeren van afbeeldingen kunnen het volgende bevatten:

```shell
 -destMime PNG/JPEG: Mime type of output rendition
 -BitDepth 8/16: Preserves Bit Depth. Bitdepth '4' is automatically converted to '8'
 -preserveBitDepth: Downscales Bit Depth (No upscaling)
 -preserveCMYK: Preserves CMYK color space
 -jpegQuality: Provides jpeg quality parameter (0-12 , corresponding to Photoshop qualities)
 -ResamplingMethod BiCubic/Lanczos/PSBicubic: Provides resampling methods. PSBicubic is a Photoshop quality resampling method.
 -resize
```

U kunt de volgende opties voor de `-resize` parameter:

* `X`: Werken vergelijkbaar met [!DNL Experience Manager]. Bijvoorbeeld - resize 319.
* `WxH`: De hoogte-breedteverhouding blijft bijvoorbeeld niet behouden `-resize 319x319`.
* `Wx`: Hiermee stelt u de breedte vast en berekent u de hoogte met behoud van de hoogte-breedteverhouding. Bijvoorbeeld: `-resize 319x`.
* `xH`: Hiermee corrigeert u de hoogte en berekent u de breedte met behoud van de hoogte-breedteverhouding. Bijvoorbeeld: `-resize x319`.

```shell
 -AllowUpsampling (Resizes smaller images)
 -input <fileName>
 -output <fileName>
```

## Bibliotheek voor afbeeldingstransformatie configureren {#configuring-imaging-transcoding-library}

Om ITL verwerking te vormen, creeer een configuratiedossier en werk het werkschema bij om het uit te voeren.

### Configuratiebestand maken voor geëxtraheerde bundel {#create-conf-file}

Om de bibliotheek te vormen, creeer een CONF dossier om op de bibliotheken te wijzen gebruikend de volgende stappen. U hebt beheerder- of basismachtigingen nodig.

1. Download de [Imaging Transcoding Library-pakket van Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/aem630/product/assets/aem-assets-imaging-transcoding-library-pkg) en installeer deze met de Package Manager. Het pakket is compatibel met [!DNL Experience Manager] 6.5

1. Een bundle-id weten voor `com.day.cq.dam.cq-dam-switchengine`, meld u aan bij de webconsole en klik op **[!UICONTROL OSGi]** > **[!UICONTROL Bundles]**. U kunt ook toegang krijgen tot de bundelconsole om deze te openen `https://[aem_server:[port]/system/console/bundles/` URL. Zoeken `com.day.cq.dam.cq-dam-switchengine` -bundel en de bijbehorende id.

1. Controleer of alle vereiste bibliotheken zijn uitgepakt door de map met de opdracht te controleren `ls -la /aem65/author/crx-quickstart/launchpad/felix/bundle<id>/data/binaries/`, waarbij de mapnaam wordt samengesteld met behulp van de bundel-id. De opdracht is bijvoorbeeld `ls -la /aem65/author/crx-quickstart/launchpad/felix/bundle588/data/binaries/` als bundle id `588`.

1. Maken `SWitchEngineLibs.conf` bestand voor koppeling naar de bibliotheek.

   ```shell
   cd `/etc/ld.so.conf.d`
   touch SWitchEngineLibs.conf
   vi SWitchEngineLibs.conf
   ```

1. Toevoegen `/aem65/author/crx-quickstart/launchpad/felix/bundle<id>/data/binaries/` pad naar het conf-bestand met `cat SWitchEngineLibs.conf` gebruiken.

1. Uitvoeren `ldconfig` gebruiken om de benodigde koppelingen en cache te maken.

1. In de account die wordt gebruikt om te starten [!DNL Experience Manager], bewerken `.bash_profile` bestand. Toevoegen `LD_LIBRARY_PATH` door het volgende toe te voegen.

   ```shell
   LD_LIBRARY_PATH=.
   export LD_LIBRARY_PATH
   ```

1. De waarde van het pad instellen op `.`, gebruik `echo $LD_LIBRARY_PATH` gebruiken. De uitvoer moet gewoon `.`. Als de waarde niet is ingesteld op `.`, start de sessie opnieuw.

### Configureren [!UICONTROL DAM Update Asset] werkstroom {#configure-dam-asset-update-workflow}

Werk de [!UICONTROL DAM Update Asset] workflow om de bibliotheek te gebruiken voor het verwerken van afbeeldingen.

1. In [!DNL Experience Manager] gebruikersinterface, selecteren **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.

1. Van de **[!UICONTROL Workflow Models]** pagina, opent u **[!UICONTROL DAM Update Asset]** workflowmodel in bewerkingsmodus.

1. Open de **[!UICONTROL Process Thumbnails]** stap workflowproces. In de **[!UICONTROL Thumbnails]** tabblad, voegt u de MIME-typen toe waarvoor u het genereren van de standaardminiaturen in het dialoogvenster **[!UICONTROL Skip Mime Types]** lijst.
Als u bijvoorbeeld miniaturen voor een TIFF-afbeelding wilt maken met de afbeeldingstransformatiebibliotheek, geeft u `image/tiff` in de **[!UICONTROL Skip Mime Types]** veld.

1. In de **[!UICONTROL Web Enabled Image]** tabblad, voegt u de MIME-typen toe waarvoor u het standaardgenereren van webvertoningen wilt overslaan in **[!UICONTROL Skip List]**. Als u bijvoorbeeld het MIME-type hebt overgeslagen `image/tiff` in de bovenstaande stap toevoegen `image/tiff` in de lijst Overslaan.

1. Open de **[!UICONTROL EPS thumbnails (powered by ImageMagick)]** stap, navigeer naar **[!UICONTROL Arguments]** tab. In de **[!UICONTROL Mime Types]** , voegt u de MIME-typen toe die u wilt verwerken in de bibliotheek voor afbeeldingstransformatie. Als u bijvoorbeeld het MIME-type hebt overgeslagen `image/tiff` in de bovenstaande stap toevoegen `image/jpeg` aan de **[!UICONTROL Mime Types]** lijst.

1. Verwijder de standaardopdrachten, indien aanwezig.

1. Zijpaneel in-/uitschakelen en toevoegen in de lijst met stappen **[!UICONTROL SWitchEngine Handler]**.

1. Opdrachten toevoegen aan de [!UICONTROL SwitchEngine Handler] op basis van uw aangepaste vereisten. Tune de parameters van bevelen die u specificeert om aan uw vereisten te voldoen. Als u bijvoorbeeld het kleurprofiel van de JPEG-afbeelding wilt behouden, voegt u de volgende opdrachten toe aan de **[!UICONTROL Commands]** lijst:

   * `SWitchEngine -input ${file} -destMime PNG -resize 48 -output ${directory}cq5dam.thumbnail.48.48.png`
   * `SWitchEngine -input ${file} -destMime PNG -resize 140x100 -output ${directory}cq5dam.thumbnail.140.100.png`
   * `SWitchEngine -input ${file} -destMime PNG -resize 319 -output ${directory}cq5dam.thumbnail.319.319.png`
   * `SWitchEngine -input ${file} -destMime JPEG -resize 1280 -preserveCMYK -output ${directory}cq5dam.web.1280.1280.jpeg`

   ![schil](assets/chlimage_1-199.png)

1. (Optioneel) Genereer miniaturen van een tussentijdse uitvoering met één opdracht. De tussenliggende vertoning fungeert als bron voor het genereren van statische weergaven en webuitvoeringen. Deze methode is sneller dan de eerdere methode. Met deze methode kunt u echter geen aangepaste parameters op miniaturen toepassen.

   ![schil](assets/chlimage_1-200.png)

1. Als u webuitvoeringen wilt genereren, configureert u parameters in het dialoogvenster **[!UICONTROL Web-Enabled Image]** tab.

1. De bijgewerkte versie synchroniseren [!UICONTROL DAM Update Asset] workflowmodel. Sla de workflow op.

Als u de configuratie wilt controleren, uploadt u een TIFF-afbeelding en controleert u het bestand error.log. U zult `INFO` berichten met vermelding van `SwitchEngineHandlingProcess execute: executing command line`. In de logboeken worden de gegenereerde uitvoeringen vermeld. Nadat de workflow is voltooid, kunt u de nieuwe uitvoeringen weergeven in [!DNL Experience Manager].

>[!MORELIKETHIS]
>
>* [Ondersteund artikel voor MIME-typen](assets-formats.md#supported-image-transcoding-library)
