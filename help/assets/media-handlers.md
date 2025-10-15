---
title: Elementen verwerken met behulp van mediafuncties en workflows
description: Leer meer over de media handlers en hoe u workflows kunt gebruiken om taken uit te voeren op uw digitale middelen.
mini-toc-levels: 1
contentOwner: AG
role: User
feature: Workflow,Renditions
exl-id: cfd6c981-1a35-4327-82d7-cf373d842cc3
solution: Experience Manager, Experience Manager Assets
source-git-commit: f8588ef353bd08b41202350072728d80ee51f565
workflow-type: tm+mt
source-wordcount: '2039'
ht-degree: 1%

---

# Elementen verwerken met behulp van mediafuncties en workflows {#processing-assets-using-media-handlers-and-workflows}

[!DNL Adobe Experience Manager Assets] wordt geleverd met een set standaardworkflows en mediahandlers voor het verwerken van elementen. Een werkschema bepaalt de taken die op de activa moeten worden uitgevoerd, dan delegeert de specifieke taken aan de media managers, bijvoorbeeld, duimnagelgeneratie of meta-gegevensextractie.

Een werkstroom kan worden gevormd om automatisch uit te voeren wanneer een middel van een bepaald type MIME wordt geupload. De verwerkingsstappen worden gedefinieerd in termen van een reeks [!DNL Assets] media-handlers. [!DNL Experience Manager] verstrekt sommige [ ingebouwde managers ](#default-media-handlers), en de extra degenen kunnen of [ worden ontwikkeld douane ](#creating-a-new-media-handler) of worden bepaald door het proces aan a [ bevel-lijn hulpmiddel ](#command-line-based-media-handler) te delegeren.

Mediahandlers zijn services in [!DNL Assets] die specifieke handelingen uitvoeren op elementen. Wanneer een MP3-audiobestand bijvoorbeeld wordt geüpload naar [!DNL Experience Manager] , wordt met een workflow een MP3-handler geactiveerd die de metagegevens extraheert en een miniatuur genereert. Mediahandlers worden gebruikt bij workflows. De meeste gangbare MIME-typen worden ondersteund binnen [!DNL Experience Manager] . U kunt specifieke taken uitvoeren op elementen door workflows uit te breiden of te maken, media-handlers uit te breiden of te maken of door media-handlers uit te schakelen en in te schakelen.

>[!NOTE]
>
>Zie de [ Ondersteunde formaten van Activa ](assets-formats.md) pagina voor een beschrijving van alle formaten die door [!DNL Assets] worden gesteund en eigenschappen voor elk formaat.

## Standaardmediahandlers {#default-media-handlers}

De volgende media-handlers zijn beschikbaar in [!DNL Assets] en verwerken de meest gebruikte MIME-typen:

<!-- TBD: Java versions should not be set to 1.5. Must be updated.
-->

| Naam handler | Servicenaam (in de systeemconsole) | Ondersteunde MIME-typen |
|--------------|--------------------------------------|----------------------|
| [!UICONTROL TextHandler] | com.day.cq.dam.core.impl.handler.TextHandler | text/plain |
| [!UICONTROL PdfHandler] | com.day.cq.dam.handler.standard.pdf.PdfHandler | <ul><li>application/pdf</li><li>toepassing/illustrator</li></ul> |
| [!UICONTROL JpegHandler] | com.day.cq.dam.core.impl.handler.JpegHandler | image/jpeg |
| [!UICONTROL Mp3Handler] | com.day.cq.dam.handler.standard.mp3.Mp3Handler | audio/mpeg <br><b> Belangrijk </b> - een geupload MP3 dossier wordt [ verwerkt gebruikend een derdebibliotheek ](https://www.zxdr.it/programmi/SistEvolBDD/LibJava/doc/de/vdheide/mp3/MP3File.html). De bibliotheek berekent een onnauwkeurige benaderende lengte als MP3 veranderlijke bitrate (VBR) heeft. |
| [!UICONTROL ZipHandler] | com.day.cq.dam.handler.standard.zip.ZipHandler | <ul><li>application/java-archive </li><li> application/zip</li></ul> |
| [!UICONTROL PictHandler] | com.day.cq.dam.handler.standard.pict.PictHandler | image/pict |
| [!UICONTROL StandardImageHandler] | com.day.cq.dam.core.impl.handler.StandardImageHandler | <ul><li>image/gif </li><li> image/png </li> <li>toepassing/photoshop </li> <li>image/jpeg </li><li> image/tiff </li> <li>image/x-ms-bmp </li><li> image/bmp</li></ul> |
| [!UICONTROL MSOfficeHandler] | com.day.cq.dam.handler.standard.msoffice.MSOfficeHandler | application/msword |
| [!UICONTROL MSPowerPointHandler] | com.day.cq.dam.handler.standard.msoffice.MSPowerPointHandler | application/vnd.ms |
| [!UICONTROL OpenOfficeHandler] | com.day.cq.dam.handler.standard.ooxml.OpenOfficeHandler | <ul><li>application/vnd.openxmlformats-officedocument.wordprocessingml.document</li><li> application/vnd.openxmlformats-officedocument.spreadsheetml.sheet</li><li> application/vnd.openxmlformats-officedocument.presentationml.presentation</li></ul> |
| [!UICONTROL EPubHandler] | com.day.cq.dam.handler.standard.epub.EPubHandler | application/epub+zip |
| [!UICONTROL GenericAssetHandler] | com.day.cq.dam.core.impl.handler.GenericAssetHandler | fallback als er geen andere handler is gevonden om gegevens uit een element te extraheren |

{style="table-layout:auto"}

Alle managers voeren de volgende taken uit:

* alle beschikbare metagegevens uit het element extraheren.
* een miniatuurafbeelding van een element maken.

De actieve media-handlers weergeven:

1. Navigeer in uw browser naar `https://localhost:4502/system/console/components` .
1. Klik op `com.day.cq.dam.core.impl.store.AssetStoreImpl`.
1. Er wordt een lijst weergegeven met alle actieve mediamanagers. Bijvoorbeeld:

![ chlimage_1-437 ](assets/chlimage_1-437.png)

## Mediahandlers gebruiken in workflows om taken uit te voeren op elementen {#using-media-handlers-in-workflows-to-perform-tasks-on-assets}

De managers van media zijn de diensten die met werkschema&#39;s worden gebruikt.

[!DNL Experience Manager] beschikt over enkele standaardworkflows om elementen te verwerken. Open de workflowconsole en klik op het tabblad **[!UICONTROL Models]** om deze weer te geven. De workflowtitels die met [!DNL Assets] beginnen, zijn de assets-specifieke titels.

Bestaande workflows kunnen worden uitgebreid en nieuwe workflows kunnen worden gemaakt om elementen volgens specifieke vereisten te verwerken.

In het volgende voorbeeld ziet u hoe u de workflow **[!UICONTROL AEM Assets Synchronization]** kunt verbeteren, zodat er subassets worden gegenereerd voor alle assets behalve PDF-documenten.

### Een mediafunctie in- of uitschakelen {#disabling-enabling-a-media-handler}

De media-handlers kunnen worden uitgeschakeld of ingeschakeld via de Apache Felix Web Management Console. Wanneer de media-handler is uitgeschakeld, worden de taken niet uitgevoerd op de elementen.

Een media-handler in- en uitschakelen:

1. Navigeer in uw browser naar `https://<host>:<port>/system/console/components` .
1. Klik op **[!UICONTROL Disable]** naast de naam van de media-handler. Bijvoorbeeld: `com.day.cq.dam.handler.standard.mp3.Mp3Handler` .
1. De pagina vernieuwen: naast de media-handler wordt een pictogram weergegeven dat aangeeft dat de pagina is uitgeschakeld.
1. Klik op **[!UICONTROL Enable]** naast de naam van de mediafunctie om de mediafunctie in te schakelen.

### Een mediafunctie maken {#creating-a-new-media-handler}

Voor ondersteuning van een nieuw mediatype of voor het uitvoeren van specifieke taken op een element, is het nodig een mediafunctie te maken. In dit gedeelte wordt beschreven hoe u verder kunt gaan.

#### Belangrijke klassen en interfaces {#important-classes-and-interfaces}

De beste manier om een implementatie te starten is het overnemen van een aangeboden abstracte implementatie die de meeste zaken behandelt en een redelijk standaardgedrag biedt: de klasse `com.day.cq.dam.core.AbstractAssetHandler` .

Deze klasse verstrekt reeds een abstracte de dienstbeschrijver. Dus als u van deze klasse hebt geërfd en de maven-sling-plugin gebruikt, zorg ervoor dat u de inherit markering aan `true` plaatst.

Voer de volgende methodes uit:

* `extractMetadata()`: extraheert alle beschikbare metagegevens.
* `getThumbnailImage()` : hiermee maakt u een miniatuurafbeelding van het doorgegeven element.
* `getMimeTypes()`: retourneert de MIME-typen van het element.

Hier volgt een voorbeeldsjabloon:

```Java
package my.own.stuff; /** * @scr.component inherit="true" * @scr.service */ public class MyMediaHandler extends com.day.cq.dam.core.AbstractAssetHandler { // implement the relevant parts }
```

De interface en de klassen omvatten:

* `com.day.cq.dam.api.handler.AssetHandler` interface: deze interface beschrijft de service die ondersteuning voor specifieke MIME-typen toevoegt. Als u een MIME-type wilt toevoegen, moet u deze interface implementeren. De interface bevat methoden voor het importeren en exporteren van de specifieke documenten, voor het maken van miniaturen en het uitnemen van metagegevens.
* `com.day.cq.dam.core.AbstractAssetHandler` -klasse: deze klasse dient als basis voor alle andere implementaties van elementenhandlers en biedt veelgebruikte functionaliteit.
* `com.day.cq.dam.core.AbstractSubAssetHandler`-klasse:
   * Deze klasse fungeert als basis voor alle andere implementaties van elementenhandlers en biedt veelgebruikte functionaliteit plus veelgebruikte functionaliteit voor het extraheren van subelementen.
   * De beste manier om een implementatie te beginnen is van een verstrekte abstracte implementatie te erven die de meeste dingen behandelt en redelijk standaardgedrag verstrekt: de klasse com.day.cq.dam.core.AbstractAssetHandler.
   * Deze klasse verstrekt reeds een abstracte de dienstbeschrijver. Dus als u van deze klasse hebt geërfd en de gemaven-sling-plugin gebruikt, zorg ervoor dat u de inherit vlag aan waar plaatst.

De volgende methoden moeten worden toegepast:

* `extractMetadata()` : met deze methode worden alle beschikbare metagegevens geëxtraheerd.
* `getThumbnailImage()` : met deze methode maakt u een miniatuurafbeelding van het doorgegeven element.
* `getMimeTypes()`: deze methode retourneert de MIME-typen van het element.

Hier volgt een voorbeeldsjabloon:

package my.own.stuff; /&amp;ast;&amp;ast; &amp;ast; @scr.component inherit=&quot;true&quot;&amp;ast; @scr.service&amp;ast;/ public class MyMediaHandler extends com.day.cq.dam.core.AbstractAssetHandler { // implementeert de relevante onderdelen }

De interface en de klassen omvatten:

* `com.day.cq.dam.api.handler.AssetHandler` interface: deze interface beschrijft de service die ondersteuning voor specifieke MIME-typen toevoegt. Als u een MIME-type wilt toevoegen, moet u deze interface implementeren. De interface bevat methoden voor het importeren en exporteren van de specifieke documenten, voor het maken van miniaturen en het uitnemen van metagegevens.
* `com.day.cq.dam.core.AbstractAssetHandler` -klasse: deze klasse dient als basis voor alle andere implementaties van elementenhandlers en biedt veelgebruikte functionaliteit.
* `com.day.cq.dam.core.AbstractSubAssetHandler` -klasse: deze klasse dient als basis voor alle andere implementaties van elementenhandlers en biedt veelgebruikte functionaliteit plus veelgebruikte functionaliteit voor het extraheren van subelementen.

#### Voorbeeld: een specifieke teksthandler maken {#example-create-a-specific-text-handler}

In deze sectie maakt u een specifieke teksthandler die miniaturen met een watermerk genereert.

Ga als volgt te werk:

Verwijs naar [ Hulpmiddelen van de Ontwikkeling ](../sites-developing/dev-tools.md) om Eclipse met een [!DNL Maven] stop te installeren en op te zetten en voor vestiging de gebiedsdelen die voor het [!DNL Maven] project nodig zijn.

Nadat u de volgende procedure hebt uitgevoerd en een TXT-bestand in [!DNL Experience Manager] uploadt, worden de metagegevens van het bestand geëxtraheerd en worden twee miniaturen met een watermerk gegenereerd.

1. Maak in Eclipse `myBundle` [!DNL Maven] -project:

   1. Klik in de menubalk op **[!UICONTROL File]** > **[!UICONTROL New]** > **[!UICONTROL Other]** .
   1. Vouw in het dialoogvenster de map [!DNL Maven] uit, selecteer het [!DNL Maven] -project en klik op **[!UICONTROL Next]** .
   1. Schakel het vakje Een eenvoudig project maken en het standaardvak Workspace-locatie gebruiken in en klik op **[!UICONTROL Next]** .
   1. Een [!DNL Maven] -project definiëren:

      * Groep-id: `com.day.cq5.myhandler` .
      * Artefact-id: myBundle.
      * Naam: Mijn [!DNL Experience Manager] bundel.
      * Beschrijving: Dit is mijn [!DNL Experience Manager] bundel.

   1. Klik op **[!UICONTROL Finish]**.

1. Stel de [!DNL Java™] -compiler in op versie 1.5:

   1. Klik met de rechtermuisknop op het `myBundle` -project en selecteer [!UICONTROL Properties] .
   1. Selecteer [!UICONTROL Java™ Compiler] en stel de volgende eigenschappen in op 1,5:

      * Compatibiliteitsniveau compiler
      * Compatibiliteit van gegenereerde .class-bestanden
      * Source-compatibiliteit

   1. Klik op **[!UICONTROL OK]**. Klik in het dialoogvenster op **[!UICONTROL Yes]** .

1. Vervang de code in het `pom.xml` dossier met de volgende code:

   ```xml
   <project xmlns="https://maven.apache.org/POM/4.0.0" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="https://maven.apache.org/POM/4.0.0 https://maven.apache.org/maven-v4_0_0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <!-- ====================================================================== -->
    <!-- P A R E N T P R O J E C T D E S C R I P T I O N -->
    <!-- ====================================================================== -->
    <parent>
     <groupId>com.day.cq.dam</groupId>
     <artifactId>dam</artifactId>
     <version>5.2.14</version>
     <relativePath>../parent</relativePath>
    </parent>
    <!-- ====================================================================== -->
    <!-- P R O J E C T D E S C R I P T I O N -->
    <!-- ====================================================================== -->
    <groupId>com.day.cq5.myhandler</groupId>
    <artifactId>myBundle</artifactId>
    <name>My CQ5 bundle</name>
    <version>0.0.1-SNAPSHOT</version>
    <description>This is my CQ5 bundle</description>
    <packaging>bundle</packaging>
    <!-- ====================================================================== -->
    <!-- B U I L D D E F I N I T I O N -->
    <!-- ====================================================================== -->
    <build>
     <plugins>
      <plugin>
       <groupId>org.apache.felix</groupId>
       <artifactId>maven-scr-plugin</artifactId>
      </plugin>
      <plugin>
       <groupId>org.apache.sling</groupId>
       <artifactId>maven-sling-plugin</artifactId>
       <configuration>
        <slingUrlSuffix>/libs/dam/install/</slingUrlSuffix>
       </configuration>
      </plugin>
      <plugin>
       <groupId>org.apache.felix</groupId>
       <artifactId>maven-bundle-plugin</artifactId>
       <extensions>true</extensions>
       <configuration>
        <instructions>
         <Bundle-Category>cq5</Bundle-Category>
         <Export-Package> com.day.cq5.myhandler </Export-Package>
        </instructions>
       </configuration>
      </plugin>
     </plugins>
    </build>
    <!-- ====================================================================== -->
    <!-- D E P E N D E N C I E S -->
    <!-- ====================================================================== -->
    <dependencies>
     <dependency>
      <groupId>com.day.cq.dam</groupId>
      <artifactId>cq-dam-api</artifactId>
      <version>5.2.10</version>
      <scope>provided</scope>
     </dependency>
     <dependency>
      <groupId>com.day.cq.dam</groupId>
      <artifactId>cq-dam-core</artifactId>
      <version>5.2.10</version>
      <scope>provided</scope>
     </dependency>
     <dependency>
      <groupId>com.day.cq</groupId>
      <artifactId>cq-commons</artifactId>
     </dependency>
     <dependency>
      <groupId>javax.jcr</groupId>
      <artifactId>jcr</artifactId>
     </dependency>
     <dependency>
      <groupId>org.apache.felix</groupId>
      <artifactId>org.osgi.compendium</artifactId>
     </dependency>
     <dependency>
      <groupId>org.slf4j</groupId>
      <artifactId>slf4j-api</artifactId>
     </dependency>
     <dependency>
      <groupId>commons-lang</groupId>
      <artifactId>commons-lang</artifactId>
     </dependency>
     <dependency>
      <groupId>commons-collections</groupId>
      <artifactId>commons-collections</artifactId>
     </dependency>
     <dependency>
      <groupId>commons-io</groupId>
      <artifactId>commons-io</artifactId>
     </dependency>
     <dependency>
      <groupId>com.day.commons</groupId>
      <artifactId>day-commons-gfx</artifactId>
     </dependency>
     <dependency>
      <groupId>com.day.commons</groupId>
      <artifactId>day-commons-text</artifactId>
     </dependency>
     <dependency>
      <groupId>com.day.cq.workflow</groupId>
      <artifactId>cq-workflow-api</artifactId>
     </dependency>
     <dependency>
      <groupId>com.day.cq.wcm</groupId>
      <artifactId>cq-wcm-foundation</artifactId>
      <version>5.2.22</version>
     </dependency>
    </dependencies>
   ```

1. Maak het pakket `com.day.cq5.myhandler` dat de [!DNL Java™] klassen onder `myBundle/src/main/java` bevat:

   1. Klik met de rechtermuisknop onder myBundle, selecteer Nieuw en vervolgens Pakket. `src/main/java`
   1. Geef de naam `com.day.cq5.myhandler` op en klik op Voltooien.

1. Maak de [!DNL Java™] klasse `MyHandler` :

   1. Klik in [!DNL Eclipse] onder `myBundle/src/main/java` met de rechtermuisknop op het `com.day.cq5.myhandler` -pakket. Selecteer [!UICONTROL New] en vervolgens [!UICONTROL Class] .
   1. Geef in het dialoogvenster de naam [!DNL Java™] class `MyHandler` en klik op [!UICONTROL Finish] . [!DNL Eclipse] maakt en opent het bestand `MyHandler.java` .
   1. Vervang in `MyHandler.java` de bestaande code door het volgende en sla de wijzigingen op:

   ```java
   package com.day.cq5.myhandler;
   import java.awt.Color;
   import java.awt.Rectangle;
   import java.awt.image.BufferedImage;
   import java.io.IOException;
   import java.io.InputStream;
   import java.io.InputStreamReader;
   import javax.jcr.Node;
   import javax.jcr.RepositoryException;
   import javax.jcr.Session;
   import org.apache.commons.io.IOUtils;
   import org.slf4j.Logger;
   import org.slf4j.LoggerFactory;
   import com.day.cq.dam.api.metadata.ExtractedMetadata;
   import com.day.cq.dam.core.AbstractAssetHandler;
   import com.day.image.Font;
   import com.day.image.Layer;
   import com.day.cq.wcm.foundation.ImageHelper;
   
   /**
    * The <code>MyHandler</code> can extract text files
    * @scr.component inherit="true" immediate="true" metatype="false"
    * @scr.service
    *
    **/
   
   public class MyHandler extends AbstractAssetHandler {
    /** * Logger instance for this class. */
    private static final Logger log = LoggerFactory.getLogger(MyHandler.class);
    /** * Music icon margin */
    private static final int MARGIN = 10;
    /** * @see com.day.cq.dam.api.handler.AssetHandler#getMimeTypes() */
    public String[] getMimeTypes() {
     return new String[] {"text/plain"};
    }
   
    public ExtractedMetadata extractMetadata(Node asset) {
     ExtractedMetadata extractedMetadata = new ExtractedMetadata();
     InputStream data = getInputStream(asset);
     try {
      // read text data
      InputStreamReader reader = new InputStreamReader(data);
      char[] buffer = new char[4096];
      String text = "";
      while (reader.read(buffer) != -1) {
       text += new String(buffer);
      }
      reader.close();
      long wordCount = this.wordCount(text);
      extractedMetadata.setProperty("text", text);
      extractedMetadata.setMetaDataProperty("Word Count",wordCount);
      setMimetype(extractedMetadata, asset);
     } catch (Throwable t) {
      log.error("handling error: " + t.toString(), t);
     } finally {
      IOUtils.closeQuietly(data);
     }
     return extractedMetadata; }
    // ----------------------< helpers >----------------------------------------
    protected BufferedImage getThumbnailImage(Node node) {
     ExtractedMetadata metadata = extractMetadata(node);
     final String text = (String) metadata.getProperty("text");
     // create text layer
     final Layer layer = new Layer(500, 600, Color.WHITE);
     layer.setPaint(Color.black);
     Font font = new Font("Arial", 12);
     String displayText = this.getDisplayText(text, 600, 12);
     if(displayText!=null && displayText.length() > 0) {
      // commons-gfx Font class would throw IllegalArgumentException on empty or null text
      layer.drawText(10, 10, 500, 600, displayText, font, Font.ALIGN_LEFT, 0, 0);
     }
     // create watermark and merge with text layer
     Layer watermarkLayer;
     try {
      final Session session = node.getSession();
      watermarkLayer = ImageHelper.createLayer(session, "/content/dam/we-retail/en/products/apparel/gloves/Gloves.jpg");
      watermarkLayer.setX(MARGIN);
      watermarkLayer.setY(MARGIN);
      layer.merge(watermarkLayer);
     } catch (RepositoryException e) {
      // TODO Auto-generated catch block
      e.printStackTrace();
     } catch (IOException e) {
      // TODO Auto-generated catch block
      e.printStackTrace(); }
     layer.crop(new Rectangle(510, 600));
     return layer.getImage(); }
    // ---------------< private >-----------------------------------------------
    /**
     * This method cuts lines if the text file is too long..
     * * @param text
     * * text to check
     * * @param height
     * * text box height (px)
     * * @param fontheight
     * * font height (px)
     * * @return the text which will fit into the box
     */
    private String getDisplayText(String text, int height, int fontheight) {
     String trimmedText = text.trim();
     int numOfLines = height / fontheight;
     String lines[] = trimmedText.split("\n");
     if (lines.length <= numOfLines) {
      return trimmedText;
     } else {
      String cuttetText = "";
      for (int i = 0; i < numOfLines; i++) {
       cuttetText += lines[i] + "\n";
      }
      return cuttetText;
     }
    }
    /**
     * * This method counts the number of words in a string
     * * @param text the String whose words would like to be counted
     * * @return the number of words in the string
     * */
    private long wordCount(String text) {
     // We need to keep track of the last character, if we have two whitespaces in a row we do not want to double count.
     // The starting of the document is always a whitespace.
     boolean prevWhiteSpace = true;
     boolean currentWhiteSpace = true;
     char c; long numwords = 0;
     int j = text.length();
     int i = 0;
     while (i < j) {
      c = text.charAt(i++);
      if (c == 0) { break; }
      currentWhiteSpace = Character.isWhitespace(c);
      if (currentWhiteSpace && !prevWhiteSpace) { numwords++; }
      prevWhiteSpace = currentWhiteSpace;
     }
     // If we do not end with a whitespace then we need to add one extra word.
     if (!currentWhiteSpace) { numwords++; }
     return numwords;
    }
   }
   ```

1. Compileer de klasse [!DNL Java™] en maak de bundel:

   1. Klik met de rechtermuisknop op het `myBundle` -project, selecteer **[!UICONTROL Run As]** en vervolgens **[!UICONTROL Maven Install]** .
   1. De bundel `myBundle-0.0.1-SNAPSHOT.jar` (die de gecompileerde klasse bevat) wordt onder `myBundle/target` gemaakt.

1. Maak in CRX Explorer een knooppunt onder `/apps/myApp` . Name = `install`, Type = `nt:folder` .
1. Kopieer de bundel `myBundle-0.0.1-SNAPSHOT.jar` en sla deze op onder `/apps/myApp/install` (bijvoorbeeld met WebDAV). De nieuwe teksthandler is nu actief in [!DNL Experience Manager] .
1. Open [!UICONTROL Apache Felix Web Management Console] in uw browser. Selecteer de tab [!UICONTROL Components] en schakel de standaardteksthandler `com.day.cq.dam.core.impl.handler.TextHandler` uit.

## Media-handler op basis van opdrachtregel {#command-line-based-media-handler}

Met [!DNL Experience Manager] kunt u een opdrachtregelprogramma uitvoeren in een workflow om elementen (zoals [!DNL ImageMagick] ) om te zetten en de nieuwe uitvoering aan het element toe te voegen. Installeer alleen het opdrachtregelprogramma op de schijf die als host fungeert voor de [!DNL Experience Manager] -server, en om een processtap toe te voegen en te configureren voor de workflow. Het aangeroepen proces, `CommandLineProcess` genaamd, filtert ook op basis van specifieke MIME-typen en maakt meerdere miniaturen op basis van de nieuwe uitvoering.

De volgende conversies kunnen automatisch worden uitgevoerd en opgeslagen binnen [!DNL Assets] :

* EPS en AI transformatie die `https://www.imagemagick.org/script/index.php` gebruiken en [ Ghostscript ](https://www.ghostscript.com/).
* FLV video transcoderen die [ gebruiken mpeg ](https://ffmpeg.org/).
* MP3 het coderen die [ LAME ](https://lame.sourceforge.io/) gebruiken.
* Audio verwerkend gebruikend [ SOX ](https://sourceforge.net/projects/sox/).

>[!NOTE]
>
>Op niet-Windows-systemen retourneert het Mpeg-gereedschap een fout tijdens het genereren van uitvoeringen voor een video-element met één aanhalingsteken (&#39;) in de bestandsnaam. Als de naam van het videobestand één aanhalingsteken bevat, verwijdert u het bestand voordat u het uploadt naar [!DNL Experience Manager] .

Het `CommandLineProcess` -proces voert de volgende bewerkingen uit in de vermelde volgorde:

* Hiermee wordt het bestand gefilterd op basis van specifieke MIME-typen, indien opgegeven.
* Maakt een tijdelijke map op de schijf waarop de [!DNL Experience Manager] -server wordt gehost.
* Hiermee wordt het oorspronkelijke bestand gestroomd naar de tijdelijke map.
* Voert de opdracht uit die door de argumenten van de stap wordt gedefinieerd. De opdracht wordt uitgevoerd in de tijdelijke map met de machtigingen van de gebruiker die [!DNL Experience Manager] uitvoert.
* Hiermee streamt u het resultaat terug naar de weergavemap van de [!DNL Experience Manager] -server.
* Hiermee verwijdert u de tijdelijke map.
* Hiermee maakt u miniaturen op basis van deze uitvoeringen, indien opgegeven. Het aantal en de afmetingen van de miniaturen worden bepaald door de argumenten van de stap.

### Een voorbeeld met [!DNL ImageMagick] {#an-example-using-imagemagick}

In het volgende voorbeeld ziet u hoe u de opdrachtregelprocesstap zo instelt dat telkens wanneer een element met het MIME-type GIF of TIFF wordt toegevoegd aan `/content/dam` op de [!DNL Experience Manager] -server, een gespiegelde afbeelding van het origineel wordt gemaakt. Er worden ook nog drie miniaturen van 140 x 100, 48 x 48 en 10 x 250 gemaakt.

Gebruik [!DNL ImageMagick] om dit te doen. [!DNL ImageMagick] is een gratis opdrachtregelprogramma waarmee u bitmapafbeeldingen kunt maken, bewerken en samenstellen.

Installeer [!DNL ImageMagick] op de schijf die als host fungeert voor de [!DNL Experience Manager] -server:

1. Installeren [!DNL ImageMagick]: zie `https://www.imagemagick.org/script/download.php` -website.
1. Stel het gereedschap zo in dat u `convert` kunt uitvoeren vanaf de opdrachtregel.
1. Voer de volgende opdracht `convert -h` uit op de opdrachtregel om te zien of het gereedschap correct is geïnstalleerd.

   Er wordt een Help-scherm weergegeven met alle mogelijke opties van het gereedschap Omzetten.

   >[!NOTE]
   >
   >In sommige versies van Windows kan de opdracht Omzetten niet worden uitgevoerd omdat er een conflict optreedt met het native hulpprogramma voor omzetting dat onderdeel is van de installatie van [!DNL Windows] . Geef in dit geval het volledige pad op voor de [!DNL ImageMagick] -software die wordt gebruikt om afbeeldingsbestanden om te zetten in miniaturen. Bijvoorbeeld `"C:\Program Files\ImageMagick-6.8.9-Q16\convert.exe" -define jpeg:size=319x319 ${filename} -thumbnail 319x319 cq5dam.thumbnail.319.319.png` .

1. Als u wilt controleren of het gereedschap correct wordt uitgevoerd, voegt u een JPG-afbeelding toe aan de werkmap en voert u de opdracht Omzetten `<image-name>.jpg -flip <image-name>-flipped.jpg` uit op de opdrachtregel. Er wordt een gespiegelde afbeelding aan de map toegevoegd. Voeg vervolgens de opdrachtregelprocesstap toe aan de **[!UICONTROL DAM Update Asset]** -workflow.
1. Ga naar de **[!UICONTROL Workflow]** -console.
1. Bewerk het **[!UICONTROL Models]** -model op het tabblad **[!UICONTROL DAM Update Asset]** .
1. Wijzig de [!UICONTROL Arguments] van de **[!UICONTROL Web enabled rendition]** -stap in: `mime:image/gif,mime:image/tiff,tn:140:100,tn:48:48,tn:10:250,cmd:convert ${directory}/${filename} -flip ${directory}/${basename}.flipped.jpg` .
1. Sla de workflow op.

Voeg een element toe aan `/content/dam` om de gewijzigde workflow te testen.

1. Haal in het bestandssysteem een TIFF-afbeelding van uw keuze op. Wijzig de naam in `myImage.tiff` en kopieer deze naar `/content/dam` , bijvoorbeeld met WebDAV.
1. Ga bijvoorbeeld naar de **[!UICONTROL CQ5 DAM]** -console `https://localhost:4502/libs/wcm/core/content/damadmin.html` .
1. Open het element **[!UICONTROL myImage.tiff]** en controleer of de gespiegelde afbeelding en de drie miniaturen zijn gemaakt.

#### Vorm de het processtap van CommandLineProcess {#configuring-the-commandlineprocess-process-step}

In deze sectie wordt beschreven hoe u de eigenschap [!UICONTROL Process Arguments] van de [!UICONTROL CommandLineProcess] instelt.

Scheid de waarden van de [!UICONTROL Process Arguments] met komma&#39;s en start deze niet met een spatie.

| Argument-formaat | Beschrijving |
|---|---|
| mime:&lt;mime-type> | Optioneel argument. Het proces wordt toegepast als het element hetzelfde MIME-type heeft als het element in het argument. <br> Verscheidene types MIME kunnen worden bepaald. |
| tn:&lt;width>:&lt;height> | Optioneel argument. Het proces leidt tot een duimnagel met de afmetingen die in het argument worden bepaald. <br> verscheidene duimnagels kunnen worden bepaald. |
| cmd: &lt;command> | Definieert de opdracht die wordt uitgevoerd. De syntaxis hangt van het bevel-lijn hulpmiddel af. Er kan slechts één opdracht worden gedefinieerd. <br> de volgende variabelen kunnen worden gebruikt om het bevel tot stand te brengen:<br>`${filename}`: naam van het inputdossier, bijvoorbeeld, original.jpg <br> `${file}`: volledige padnaam van het invoerbestand, bijvoorbeeld `/tmp/cqdam0816.tmp/original.jpg` <br> `${directory}`: map van het invoerbestand, bijvoorbeeld `/tmp/cqdam0816.tmp` <br>`${basename}` : naam van het invoerbestand zonder de extensie, bijvoorbeeld origineel <br>`${extension}` : extensie van het invoerbestand, bijvoorbeeld JPG. |

Als [!DNL ImageMagick] bijvoorbeeld is geïnstalleerd op de schijf die als host fungeert voor de [!DNL Experience Manager] -server en u een processtap maakt met [!UICONTROL CommandLineProcess] als implementatie en de volgende waarden als [!UICONTROL Process Arguments] :

`mime:image/gif,mime:image/tiff,tn:140:100,tn:48:48,tn:10:250,cmd:convert ${directory}/${filename} -flip ${directory}/${basename}.flipped.jpg`

Wanneer de workflow vervolgens wordt uitgevoerd, is de stap alleen van toepassing op elementen die `image/gif` of `mime:image/tiff` as `mime-types` hebben. Het maakt een gespiegelde afbeelding van het origineel, zet deze om in JPG en maakt drie miniaturen met de afmetingen 140x100, 48x48 en 10x250.

Gebruik de volgende [!UICONTROL Process Arguments] opties om de drie standaardminiaturen te maken met [!DNL ImageMagick] :

`mime:image/tiff,mime:image/png,mime:image/bmp,mime:image/gif,mime:image/jpeg,cmd:convert ${filename} -define jpeg:size=319x319 -thumbnail "319x319>" -background transparent -gravity center -extent 319x319 -write png:cq5dam.thumbnail.319.319.png -thumbnail "140x100>" -background transparent -gravity center -extent 140x100 -write cq5dam.thumbnail.140.100.png -thumbnail "48x48>" -background transparent -gravity center -extent 48x48 cq5dam.thumbnail.48.48.png`

Gebruik de volgende [!UICONTROL Process Arguments] om de voor het web ingeschakelde uitvoering te maken met [!DNL ImageMagick] :

`mime:image/tiff,mime:image/png,mime:image/bmp,mime:image/gif,mime:image/jpeg,cmd:convert ${filename} -define jpeg:size=1280x1280 -thumbnail "1280x1280>" cq5dam.web.1280.1280.jpeg`

>[!NOTE]
>
>De stap [!UICONTROL CommandLineProcess] is alleen van toepassing op elementen (knooppunten van het type `dam:Asset` ) of onderliggende elementen van een element.

>[!MORELIKETHIS]
>
>* [ activa van het Proces ](assets-workflow.md)
