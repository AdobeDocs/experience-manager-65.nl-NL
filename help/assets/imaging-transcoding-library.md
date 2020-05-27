---
title: Afbeeldingstransformatiebibliotheek
description: Leer hoe u de Imaging Transcoding Library van Adobe configureert en gebruikt, een oplossing voor beeldverwerking die kernfuncties voor het verwerken van afbeeldingen kan uitvoeren, zoals codering, transcodering, het resamplen van afbeeldingen en het vergroten of verkleinen van afbeeldingen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 566add37d6dd7efe22a99fc234ca42878f050aee
workflow-type: tm+mt
source-wordcount: '942'
ht-degree: 0%

---


# Afbeeldingstransformatiebibliotheek {#imaging-transcoding-library}

De grafische transformatiebibliotheek van Adobe is een merkgebonden oplossing voor beeldverwerking die kernfuncties voor beeldverwerking kan uitvoeren, zoals:

* Codering
* Transcodering (ondersteunde indelingen converteren)
* Nieuwe beeldpixels berekenen, met PS- en Intel IPP-algoritmen
* Bitdiepte en kleurprofiel behouden
* JPEG-kwaliteitscompressie
* Afbeeldingsformaat wijzigen

De bibliotheek voor grafische transformatie biedt CMYK-ondersteuning en volledige alfaondersteuning, behalve CMYK-Alpha.

Naast de ondersteuning van een groot aantal bestandsindelingen en profielen biedt Imaging Transcoding Library aanzienlijke voordelen ten opzichte van andere oplossingen van derden op het gebied van prestaties, schaalbaarheid en kwaliteit. Hier volgen enkele belangrijke voordelen van het gebruik van de bibliotheek voor het transformeren van afbeeldingen:

* **Schalen met grotere bestandsgrootte of resolutie**: Schalen wordt vooral bereikt door de gepatenteerde mogelijkheid om de afbeeldingstranscoderingsbibliotheek tijdens het decoderen van bestanden te vergroten of te verkleinen. Hierdoor wordt gegarandeerd dat het runtimegeheugengebruik altijd optimaal is en geen kwadratische functie voor het vergroten van de bestandsgrootte of het oplossen van megapixels is. De bibliotheek voor het transformeren van afbeeldingen kan grotere en hoge-resolutiebestanden (met hogere megapixels) verwerken. Gereedschappen van derden, zoals ImageMagick, kunnen grote bestanden en vastlopen niet verwerken tijdens het verwerken van dergelijke bestanden.
* **Afbeeldingscompressie en -algoritmen** voor Photoshop-kwaliteit: Consistentie met de industriestandaard wat betreft de kwaliteit van de downsampling (vloeiend, scherp en automatisch bicubisch) en de compressiekwaliteit. De bibliotheek voor grafische transformatie beoordeelt verder de kwaliteitsfactor van de invoerafbeelding en gebruikt op intelligente wijze optimale tabellen en kwaliteitsinstellingen voor de uitvoerafbeelding. Hierdoor ontstaan bestanden van optimale grootte zonder dat dit ten koste gaat van de visuele kwaliteit.
* **Hoge doorvoer:** De reactietijd is lager en de productie is constant hoger dan ImageMagick. Daarom zou de Bibliotheek van de Transcodering van Beelden de wachttijd voor gebruikers en de kosten van het ontvangen moeten verminderen.
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
 -BitDepth 8/16: Preserves Bit Depth. Bitdepth ‘4’ is automatically converted to ‘8’
 -preserveBitDepth: Downscales Bit Depth (No upscaling)
 -preserveCMYK: Preserves CMYK color space
 -jpegQuality: Provides jpeg quality parameter (0-12 , corresponding to Photoshop qualities)
 -ResamplingMethod BiCubic/Lanczos/PSBicubic: Provides resampling methods. PSBicubic is a Photoshop quality resampling method.
 -resize
```

U kunt de volgende opties voor de `-resize` parameter vormen:

* `X`: Werkt vergelijkbaar met Experience Manager. Bijvoorbeeld -resize 319.
* `WxH`: De hoogte-breedteverhouding wordt bijvoorbeeld niet behouden `-resize 319x319`.
* `Wx`: Hiermee stelt u de breedte vast en berekent u de hoogte met behoud van de hoogte-breedteverhouding. Bijvoorbeeld `-resize 319x`.
* `xH`: Hiermee stelt u de hoogte vast en berekent u de breedte met behoud van de hoogte-breedteverhouding. Bijvoorbeeld `-resize x319`.

```shell
 -AllowUpsampling (Resizes smaller images)
 -input <fileName>
 -output <fileName>
```

## Bibliotheek voor afbeeldingstransformatie configureren {#configuring-imaging-transcoding-library}

Om ITL verwerking te vormen, creeer een configuratiedossier en werk het werkschema bij om het uit te voeren.

### Configuratiebestand maken voor geëxtraheerde bundel {#create-conf-file}

Als u de bibliotheek wilt configureren, maakt u een .conf-bestand om de bibliotheken aan te geven met de volgende stappen. U hebt beheerder- of basismachtigingen nodig.

1. Download het [pakket](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/aem630/product/assets/aem-assets-imaging-transcoding-library-pkg) Imaging Transcoding Library en installeer het met de Package Manager. Het pakket is compatibel met Experience Manager 6.5.

1. Meld u aan bij de webconsole en klik op een bundel-id voor `com.day.cq.dam.cq-dam-switchengine`**[!UICONTROL OSGi > Bundles]**. U kunt ook de `https://[aem_server:[port]/system/console/bundles/` URL openen om de bundelconsole te openen. Zoek `com.day.cq.dam.cq-dam-switchengine` bundel en id.

1. Zorg ervoor dat alle vereiste bibliotheken zijn uitgepakt, door de map te controleren met de opdracht `ls -la /aem65/author/crx-quickstart/launchpad/felix/bundle<id>/data/binaries/`, waar de mapnaam is samengesteld met de bundle-id. De opdracht is bijvoorbeeld `ls -la /aem65/author/crx-quickstart/launchpad/felix/bundle588/data/binaries/` of bundle id `588`is.

1. Maak een `SWitchEngineLibs.conf` bestand om een koppeling naar de bibliotheek te maken.

   ```shell
   cd `/etc/ld.so.conf.d`
   touch SWitchEngineLibs.conf
   vi SWitchEngineLibs.conf
   ```

1. Voeg `/aem65/author/crx-quickstart/launchpad/felix/bundle<id>/data/binaries/` pad toe aan het conf-bestand met behulp van de `cat SWitchEngineLibs.conf` opdracht.

1. Voer `ldconfig` bevel uit om de noodzakelijke verbindingen en het geheime voorgeheugen tot stand te brengen.

1. Bewerk het `.bash_profile` bestand in het account dat wordt gebruikt om Experience Manager te starten. Voeg toe `LD_LIBRARY_PATH` door het volgende toe te voegen.

   ```shell
   LD_LIBRARY_PATH=.
   export LD_LIBRARY_PATH
   ```

1. Gebruik de `.`opdracht om ervoor te zorgen dat de waarde van het pad is ingesteld op `echo $LD_LIBRARY_PATH` . De uitvoer moet gewoon zijn `.`. Start de sessie opnieuw als de waarde niet is ingesteld op `.`.

### Workflow configureren [!UICONTROL DAM Update Asset] {#configure-dam-asset-update-workflow}

Werk de [!UICONTROL DAM Update Asset] workflow bij om de bibliotheek te gebruiken voor het verwerken van afbeeldingen.

1. Selecteer in de gebruikersinterface van Experience Manager **[!UICONTROL Tools > Workflow > Models]**.

1. Open vanaf de **[!UICONTROL Workflow Models]** pagina het **[!UICONTROL DAM Update Asset]** workflowmodel in de bewerkingsmodus.

1. Open de stap voor het **[!UICONTROL Process Thumbnails]** workflowproces. Voeg op het **[!UICONTROL Thumbnails]** tabblad de MIME-typen toe waarvoor u het standaardgenereren van miniaturen in de **[!UICONTROL Skip Mime Types]** lijst wilt overslaan.
Als u bijvoorbeeld miniaturen wilt maken voor een TIFF-afbeelding met behulp van de bibliotheek voor afbeeldingstransformatie, geeft u dit op `image/tiff` in het **[!UICONTROL Skip Mime Types]** veld.

1. Voeg op het **[!UICONTROL Web Enabled Image]** tabblad de MIME-typen toe waarvoor u het standaardgenereren van webvertoningen wilt overslaan **[!UICONTROL Skip List]**. Als u bijvoorbeeld het MIME-type `image/tiff` in de bovenstaande stap hebt overgeslagen, voegt u dit toe `image/tiff` aan de lijst Overslaan.

1. Open de **[!UICONTROL EPS thumbnails (powered by ImageMagick)]** stap en navigeer naar de **[!UICONTROL Arguments]** tab. Voeg in de **[!UICONTROL Mime Types]** lijst de MIME-typen toe die u wilt verwerken in de bibliotheek voor afbeeldingstransformatie. Als u bijvoorbeeld het MIME-type `image/tiff` in de bovenstaande stap hebt overgeslagen, voegt u het toe `image/jpeg` aan de **[!UICONTROL Mime Types]** lijst.

1. Verwijder de standaardopdrachten, indien aanwezig.

1. In-/uitschakelen in het zijpaneel en in de lijst met stappen toevoegen **[!UICONTROL SWitchEngine Handler]**.

1. Voeg bevelen aan toe [!UICONTROL SwitchEngine Handler] die op uw douanevereisten worden gebaseerd. Tune de parameters van bevelen die u specificeert om aan uw vereisten te voldoen. Als u bijvoorbeeld het kleurprofiel van uw JPEG-afbeelding wilt behouden, voegt u de volgende opdrachten toe aan de **[!UICONTROL Commands]** lijst:

   * `SWitchEngine -input ${file} -destMime PNG -resize 48 -output ${directory}cq5dam.thumbnail.48.48.png`
   * `SWitchEngine -input ${file} -destMime PNG -resize 140x100 -output ${directory}cq5dam.thumbnail.140.100.png`
   * `SWitchEngine -input ${file} -destMime PNG -resize 319 -output ${directory}cq5dam.thumbnail.319.319.png`
   * `SWitchEngine -input ${file} -destMime JPEG -resize 1280 -preserveCMYK -output ${directory}cq5dam.web.1280.1280.jpeg`
   ![schil](assets/chlimage_1-199.png)

1. (Optioneel) Genereer miniaturen van een tussentijdse uitvoering met één opdracht. De tussenliggende vertoning fungeert als bron voor het genereren van statische weergaven en webuitvoeringen. Deze methode is sneller dan de eerdere methode. Met deze methode kunt u echter geen aangepaste parameters op miniaturen toepassen.

   ![schil](assets/chlimage_1-200.png)

1. Als u webuitvoeringen wilt genereren, configureert u parameters op het **[!UICONTROL Web-Enabled Image]** tabblad.

1. Synchroniseer het bijgewerkte [!UICONTROL DAM Update Asset] workflowmodel. Sla de workflow op.

Controleer de configuratie, upload een TIFF-afbeelding en controleer het bestand error.log. Je zult berichten met `INFO` aanhalingstekens van `SwitchEngineHandlingProcess execute: executing command line`. In de logboeken worden de gegenereerde uitvoeringen vermeld. Nadat de workflow is voltooid, kunt u de nieuwe uitvoeringen weergeven in Experience Manager.

>[!MORELIKETHIS]
>
>* [Ondersteund artikel voor MIME-typen](assets-formats.md#supported-image-transcoding-library)

