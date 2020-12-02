---
title: Afbeeldingstransformatiebibliotheek
description: Leer hoe u de bibliotheek Imaging Transcoding Adobe kunt configureren en gebruiken, een oplossing voor beeldverwerking die kernfuncties voor het verwerken van afbeeldingen kan uitvoeren, zoals coderen, transcoderen, het resamplen van afbeeldingen en het vergroten of verkleinen van afbeeldingen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 9fc1201db83ae0d3bb902d4dc3ab6d78cc1dc251
workflow-type: tm+mt
source-wordcount: '942'
ht-degree: 0%

---


# Beeldtransformatiebibliotheek {#imaging-transcoding-library}

Imaging Transcoding Library is een oplossing voor imaging-verwerking die kernfuncties voor het verwerken van afbeeldingen kan uitvoeren, zoals:

* Codering
* Transcodering (ondersteunde indelingen converteren)
* Nieuwe beeldpixels berekenen, met PS- en Intel IPP-algoritmen
* Bitdiepte en kleurprofiel behouden
* JPEG-kwaliteitscompressie
* Afbeeldingsformaat wijzigen

De bibliotheek voor grafische transformatie biedt CMYK-ondersteuning en volledige alfaondersteuning, behalve CMYK-Alpha.

Naast de ondersteuning van een groot aantal bestandsindelingen en profielen biedt Imaging Transcoding Library aanzienlijke voordelen ten opzichte van andere oplossingen van derden op het gebied van prestaties, schaalbaarheid en kwaliteit. Hier volgen enkele belangrijke voordelen van het gebruik van de bibliotheek voor het transformeren van afbeeldingen:

* **Schalen met grotere bestandsgrootte of resolutie**: Schalen wordt vooral bereikt door de gepatenteerde mogelijkheid om de afbeeldingstranscoderingsbibliotheek tijdens het decoderen van bestanden te vergroten of te verkleinen. Hierdoor wordt gegarandeerd dat het runtimegeheugengebruik altijd optimaal is en geen kwadratische functie voor het vergroten van de bestandsgrootte of het oplossen van megapixels is. De bibliotheek voor het transformeren van afbeeldingen kan grotere en hoge-resolutiebestanden (met hogere megapixels) verwerken. Gereedschappen van derden, zoals ImageMagick, kunnen grote bestanden en vastlopen niet verwerken tijdens het verwerken van dergelijke bestanden.
* **Compressie- en formaatalgoritmen** voor Photoshop-kwaliteit: Consistentie met de industriestandaard wat betreft de kwaliteit van de downsampling (vloeiend, scherp en automatisch bicubisch) en de compressiekwaliteit. De bibliotheek voor grafische transformatie beoordeelt verder de kwaliteitsfactor van de invoerafbeelding en gebruikt op intelligente wijze optimale tabellen en kwaliteitsinstellingen voor de uitvoerafbeelding. Hierdoor ontstaan bestanden van optimale grootte zonder dat dit ten koste gaat van de visuele kwaliteit.
* **Hoge doorvoer:** de responstijd is lager en de doorvoer is consistent hoger dan ImageMagick. Daarom zou de Bibliotheek van de Transcodering van Beelden de wachttijd voor gebruikers en de kosten van het ontvangen moeten verminderen.
* **Beter schalen bij gelijktijdig laden:** afbeeldingstransformatiebibliotheek functioneert optimaal onder gelijktijdige laadvoorwaarden. Deze server biedt een hoge doorvoer met optimale CPU-prestaties, een optimaal geheugengebruik en een lage responstijd, wat de hostingkosten helpt te verlagen.

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

U kunt de volgende opties voor de parameter `-resize` vormen:

* `X`: Werkt vergelijkbaar met  [!DNL Experience Manager]. Bijvoorbeeld -resize 319.
* `WxH`: De hoogte-breedteverhouding wordt bijvoorbeeld niet behouden  `-resize 319x319`.
* `Wx`: Hiermee stelt u de breedte vast en berekent u de hoogte met behoud van de hoogte-breedteverhouding. Bijvoorbeeld `-resize 319x`.
* `xH`: Hiermee stelt u de hoogte vast en berekent u de breedte met behoud van de hoogte-breedteverhouding. Bijvoorbeeld `-resize x319`.

```shell
 -AllowUpsampling (Resizes smaller images)
 -input <fileName>
 -output <fileName>
```

## Bibliotheek {#configuring-imaging-transcoding-library} voor transformatie van afbeeldingen configureren

Om ITL verwerking te vormen, creeer een configuratiedossier en werk het werkschema bij om het uit te voeren.

### Configuratiebestand maken voor geëxtraheerde bundel {#create-conf-file}

Om de bibliotheek te vormen, creeer een CONF dossier om op de bibliotheken te wijzen gebruikend de volgende stappen. U hebt beheerder- of basismachtigingen nodig.

1. Download het [pakket Imaging Transcoding Library van Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/aem630/product/assets/aem-assets-imaging-transcoding-library-pkg) en installeer het met de Package Manager. Het pakket is compatibel met [!DNL Experience Manager] 6.5.

1. Als u een bundle-id voor `com.day.cq.dam.cq-dam-switchengine` wilt weten, meldt u zich aan bij de webconsole en klikt u op **[!UICONTROL OSGi]** > **[!UICONTROL Bundles]**. U kunt ook de URL van `https://[aem_server:[port]/system/console/bundles/` openen om de bundelconsole te openen. Zoek `com.day.cq.dam.cq-dam-switchengine`-bundel en de bijbehorende id.

1. Zorg ervoor dat alle vereiste bibliotheken worden geëxtraheerd door de map te controleren met de opdracht `ls -la /aem65/author/crx-quickstart/launchpad/felix/bundle<id>/data/binaries/`, waar de mapnaam wordt geconstrueerd met de bundle-id. De opdracht is bijvoorbeeld `ls -la /aem65/author/crx-quickstart/launchpad/felix/bundle588/data/binaries/` als bundle id `588` is.

1. Maak `SWitchEngineLibs.conf` bestand om te koppelen aan de bibliotheek.

   ```shell
   cd `/etc/ld.so.conf.d`
   touch SWitchEngineLibs.conf
   vi SWitchEngineLibs.conf
   ```

1. Voeg `/aem65/author/crx-quickstart/launchpad/felix/bundle<id>/data/binaries/` weg aan het conf- dossier toe gebruikend `cat SWitchEngineLibs.conf` bevel.

1. Voer `ldconfig` bevel uit om de noodzakelijke verbindingen en het geheime voorgeheugen tot stand te brengen.

1. Bewerk `.bash_profile` bestand in de account die wordt gebruikt om [!DNL Experience Manager] te starten. Voeg `LD_LIBRARY_PATH` toe door het volgende toe te voegen.

   ```shell
   LD_LIBRARY_PATH=.
   export LD_LIBRARY_PATH
   ```

1. Om ervoor te zorgen dat de waarde van de weg aan `.` wordt geplaatst, gebruik `echo $LD_LIBRARY_PATH` bevel. De uitvoer moet `.` zijn. Start de sessie opnieuw als de waarde niet is ingesteld op `.`.

### [!UICONTROL DAM Update Asset]-workflow {#configure-dam-asset-update-workflow} configureren

Werk de [!UICONTROL DAM Update Asset]-workflow bij om de bibliotheek te gebruiken voor het verwerken van afbeeldingen.

1. Selecteer [!DNL Experience Manager] > **[!UICONTROL Workflow]** > **[!UICONTROL Models]** in &lt;a0/> gebruikersinterface.**[!UICONTROL Tools]**

1. Open op de pagina **[!UICONTROL Workflow Models]** het workflowmodel **[!UICONTROL DAM Update Asset]** in de bewerkingsmodus.

1. Open de stap van het **[!UICONTROL Process Thumbnails]** werkschemaproces. Voeg op het tabblad **[!UICONTROL Thumbnails]** de MIME-typen toe waarvoor u het standaardgenereren van miniaturen in de lijst **[!UICONTROL Skip Mime Types]** wilt overslaan.
Als u bijvoorbeeld miniaturen voor een TIFF-afbeelding wilt maken met de bibliotheek voor afbeeldingstransformatie, geeft u `image/tiff` op in het veld **[!UICONTROL Skip Mime Types]**.

1. Voeg op het tabblad **[!UICONTROL Web Enabled Image]** de MIME-typen toe waarvoor u het standaardgenereren van webvertoningen wilt overslaan in **[!UICONTROL Skip List]**. Als u bijvoorbeeld het MIME-type `image/tiff` in de bovenstaande stap hebt overgeslagen, voegt u `image/tiff` toe aan de lijst Overslaan.

1. Open de stap **[!UICONTROL EPS thumbnails (powered by ImageMagick)]** en navigeer naar het tabblad **[!UICONTROL Arguments]**. Voeg in de lijst **[!UICONTROL Mime Types]** de MIME-typen toe die u in de bibliotheek voor afbeeldingstransformatie wilt verwerken. Als u bijvoorbeeld het MIME-type `image/tiff` in de bovenstaande stap hebt overgeslagen, voegt u `image/jpeg` toe aan de lijst **[!UICONTROL Mime Types]**.

1. Verwijder de standaardopdrachten, indien aanwezig.

1. Zijpaneel in-/uitschakelen en in de lijst met stappen **[!UICONTROL SWitchEngine Handler]** toevoegen.

1. Voeg bevelen aan [!UICONTROL SwitchEngine Handler] toe die op uw douanevereisten worden gebaseerd. Tune de parameters van bevelen die u specificeert om aan uw vereisten te voldoen. Als u bijvoorbeeld het kleurprofiel van uw JPEG-afbeelding wilt behouden, voegt u de volgende opdrachten toe aan de lijst **[!UICONTROL Commands]**:

   * `SWitchEngine -input ${file} -destMime PNG -resize 48 -output ${directory}cq5dam.thumbnail.48.48.png`
   * `SWitchEngine -input ${file} -destMime PNG -resize 140x100 -output ${directory}cq5dam.thumbnail.140.100.png`
   * `SWitchEngine -input ${file} -destMime PNG -resize 319 -output ${directory}cq5dam.thumbnail.319.319.png`
   * `SWitchEngine -input ${file} -destMime JPEG -resize 1280 -preserveCMYK -output ${directory}cq5dam.web.1280.1280.jpeg`

   ![schil](assets/chlimage_1-199.png)

1. (Optioneel) Genereer miniaturen van een tussentijdse uitvoering met één opdracht. De tussenliggende vertoning fungeert als bron voor het genereren van statische weergaven en webuitvoeringen. Deze methode is sneller dan de eerdere methode. Met deze methode kunt u echter geen aangepaste parameters op miniaturen toepassen.

   ![schil](assets/chlimage_1-200.png)

1. Als u webuitvoeringen wilt genereren, configureert u parameters op het tabblad **[!UICONTROL Web-Enabled Image]**.

1. Synchroniseer het bijgewerkte [!UICONTROL DAM Update Asset] workflowmodel. Sla de workflow op.

Controleer de configuratie, upload een TIFF-afbeelding en controleer het bestand error.log. `INFO` berichten met verwijzingen van `SwitchEngineHandlingProcess execute: executing command line` zullen opmerken. In de logboeken worden de gegenereerde uitvoeringen vermeld. Nadat de workflow is voltooid, kunt u de nieuwe uitvoeringen weergeven in [!DNL Experience Manager].

>[!MORELIKETHIS]
>
>* [Ondersteund artikel voor MIME-typen](assets-formats.md#supported-image-transcoding-library)

