---
title: Elementen verwerken met behulp van mediafuncties en workflows
description: Leer meer over de media handlers en hoe u workflows kunt gebruiken om taken uit te voeren op uw digitale middelen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: b14b377e52ab10c41355f069d97508b588d82216
workflow-type: tm+mt
source-wordcount: '2037'
ht-degree: 1%

---


# Elementen verwerken met behulp van mediaflers en workflows {#processing-assets-using-media-handlers-and-workflows}

[!DNL Adobe Experience Manager Assets] wordt geleverd met een set standaardworkflows en mediahandlers voor het verwerken van elementen. Een werkschema bepaalt de taken die op de activa moeten worden uitgevoerd, dan delegeert de specifieke taken aan de media managers, bijvoorbeeld duimnagelgeneratie of meta-gegevensextractie.

Een workflow kan zo worden geconfigureerd dat deze automatisch wordt uitgevoerd wanneer een element van een bepaald MIME-type wordt geüpload. De verwerkingsstappen worden gedefinieerd in termen van een reeks mediafuncties [!DNL Assets]. [!DNL Experience Manager] verstrekt sommige  [ingebouwde managers,](#default-media-handlers) en de extra degenen kunnen of  [douane worden ](#creating-a-new-media-handler) ontwikkeld of worden bepaald door het proces aan een hulpmiddel [ van de ](#command-line-based-media-handler)bevellijn te delegeren.

Mediahandlers zijn services in [!DNL Assets] die specifieke handelingen uitvoeren op elementen. Wanneer bijvoorbeeld een MP3-audiobestand wordt geüpload naar [!DNL Experience Manager], wordt een MP3-handler geactiveerd die de metagegevens extraheert en een miniatuur genereert. Meestal worden media-afhandelingen gebruikt in combinatie met workflows. De meeste gangbare MIME-typen worden ondersteund binnen [!DNL Experience Manager]. U kunt specifieke taken uitvoeren op elementen door workflows uit te breiden/te maken, media-handlers uit te breiden/te maken of media-handlers uit te schakelen/in te schakelen.

>[!NOTE]
>
>Zie de pagina [Middelen met ondersteunde indelingen](assets-formats.md) voor een beschrijving van alle indelingen die worden ondersteund door [!DNL Assets] en van de functies die worden ondersteund voor elke indeling.

## Standaardmediahandlers {#default-media-handlers}

De volgende media managers zijn beschikbaar binnen [!DNL Assets] en behandelen de gemeenschappelijkste types MIME:

<!-- TBD: Java versions shouldn't be set to 1.5. Must be updated.
-->

| Naam handler | Servicenaam (in de systeemconsole) | Ondersteunde MIME-typen |
|--------------|--------------------------------------|----------------------|
| [!UICONTROL TextHandler] | `com.day.cq.dam.core.impl.handler.TextHandler` | text/plain |
| [!UICONTROL PdfHandler] | `com.day.cq.dam.handler.standard.pdf.PdfHandler` | <ul><li>application/pdf</li><li>toepassing/illustrator</li></ul> |
| [!UICONTROL JpegHandler] | `com.day.cq.dam.core.impl.handler.JpegHandler` | image/jpeg |
| [!UICONTROL Mp3Handler] | `com.day.cq.dam.handler.standard.mp3.Mp3Handler` | audio/mpeg |
| [!UICONTROL ZipHandler] | `com.day.cq.dam.handler.standard.zip.ZipHandler` | <ul><li>application/java-archive </li><li> application/zip</li></ul> |
| [!UICONTROL PictHandler] | `com.day.cq.dam.handler.standard.pict.PictHandler` | image/pict |
| [!UICONTROL StandardImageHandler] | `com.day.cq.dam.core.impl.handler.StandardImageHandler` | <ul><li>image/gif </li><li> image/png </li> <li>toepassing/photoshop </li> <li>image/jpeg </li><li> image/tiff </li> <li>image/x-ms-bmp </li><li> image/bmp</li></ul> |
| [!UICONTROL MSOfficeHandler] | `com.day.cq.dam.handler.standard.msoffice.MSOfficeHandler` | application/msword |
| [!UICONTROL MSPowerPointHandler] | `com.day.cq.dam.handler.standard.msoffice.MSPowerPointHandler` | application/vnd.ms-powerpoint |
| [!UICONTROL OpenOfficeHandler] | `com.day.cq.dam.handler.standard.ooxml.OpenOfficeHandler` | <ul><li>application/vnd.openxmlformats-officedocument.wordprocessingml.document</li><li> application/vnd.openxmlformats-officedocument.spreadsheetml.sheet</li><li> application/vnd.openxmlformats-officedocument.presentationml.presentation</li></ul> |
| [!UICONTROL EPubHandler] | `com.day.cq.dam.handler.standard.epub.EPubHandler` | application/epub+zip |
| [!UICONTROL GenericAssetHandler] | `com.day.cq.dam.core.impl.handler.GenericAssetHandler` | fallback als er geen andere handler is gevonden om gegevens uit een element te extraheren |

Alle managers voeren de volgende taken uit:

* alle beschikbare metagegevens uit het element extraheren.
* een miniatuurafbeelding van een element maken.

De actieve media-handlers weergeven:

1. Navigeer in uw browser naar `http://localhost:4502/system/console/components`.
1. Klik op `com.day.cq.dam.core.impl.store.AssetStoreImpl`.
1. Er wordt een lijst weergegeven met alle actieve mediamanagers. Bijvoorbeeld:

![chlimage_1-437](assets/chlimage_1-437.png)

## Mediahandlers gebruiken in workflows om taken uit te voeren op elementen {#using-media-handlers-in-workflows-to-perform-tasks-on-assets}

De managers van media zijn de diensten die gewoonlijk in combinatie met werkschema&#39;s worden gebruikt.

[!DNL Experience Manager] heeft enkele standaardworkflows om elementen te verwerken. Open de workflowconsole en klik op het tabblad **[!UICONTROL Models]** om deze weer te geven: de workflowtitels die met [!DNL Assets] beginnen, zijn de assets-specifieke titels.

Bestaande workflows kunnen worden uitgebreid en nieuwe workflows kunnen worden gemaakt om elementen volgens specifieke vereisten te verwerken.

In het volgende voorbeeld ziet u hoe u de workflow **[!UICONTROL AEM Assets Synchronization]** kunt verbeteren, zodat er subassets worden gegenereerd voor alle assets behalve PDF-documenten.

### Een mediafunctie {#disabling-enabling-a-media-handler} in- of uitschakelen

De media-handlers kunnen worden uitgeschakeld of ingeschakeld via de Apache Felix Web Management Console. Wanneer de media-handler is uitgeschakeld, worden de taken niet uitgevoerd op de elementen.

Een media-handler in- en uitschakelen:

1. Navigeer in uw browser naar `https://<host>:<port>/system/console/components`.
1. Klik **[!UICONTROL Disable]** naast de naam van de media manager. Bijvoorbeeld: `com.day.cq.dam.handler.standard.mp3.Mp3Handler`.
1. De pagina vernieuwen: naast de mediafunctie wordt een pictogram weergegeven dat aangeeft dat het is uitgeschakeld.
1. Als u de mediafunctie wilt inschakelen, klikt u op **[!UICONTROL Enable]** naast de naam van de mediafunctie.

### Nieuwe mediafunctie maken {#creating-a-new-media-handler}

Voor ondersteuning van een nieuw mediatype of voor het uitvoeren van specifieke taken op een element, is het nodig een nieuwe mediafunctie te maken. In dit gedeelte wordt beschreven hoe u verder kunt gaan.

#### Belangrijke klassen en interfaces {#important-classes-and-interfaces}

De beste manier om een implementatie te beginnen is van een verstrekte abstracte implementatie te erven die de meeste dingen behandelt en redelijk standaardgedrag verstrekt: de klasse `com.day.cq.dam.core.AbstractAssetHandler`.

Deze klasse verstrekt reeds een abstracte de dienstbeschrijver. Dus als u overerft van deze klasse en de maven-sling-plugin gebruikt, zorg ervoor dat u de inherit vlag aan `true` plaatst.

Voer de volgende methodes uit:

* `extractMetadata()`: extraheert alle beschikbare metagegevens.
* `getThumbnailImage()`: Hiermee maakt u een miniatuurafbeelding van het doorgegeven element.
* `getMimeTypes()`: retourneert de MIME-typen van het element.

Hier volgt een voorbeeldsjabloon:

```Java
package my.own.stuff; /** * @scr.component inherit="true" * @scr.service */ public class MyMediaHandler extends com.day.cq.dam.core.AbstractAssetHandler { // implement the relevant parts }
```

De interface en de klassen omvatten:

* `com.day.cq.dam.api.handler.AssetHandler` interface: Deze interface beschrijft de dienst die steun voor specifieke types MIME toevoegt. Als u een nieuw MIME-type wilt toevoegen, moet u deze interface implementeren. De interface bevat methoden voor het importeren en exporteren van de specifieke documenten, voor het maken van miniaturen en het uitnemen van metagegevens.
* `com.day.cq.dam.core.AbstractAssetHandler` klasse: Deze klasse fungeert als basis voor alle andere implementaties van elementenhandlers en biedt veelgebruikte functionaliteit.
* `com.day.cq.dam.core.AbstractSubAssetHandler`-klasse:
   * Deze klasse fungeert als basis voor alle andere implementaties van asset-handlers en biedt veelgebruikte functionaliteit plus veelgebruikte functionaliteit voor het extraheren van submiddelen.
   * De beste manier om een implementatie te beginnen is van een verstrekte abstracte implementatie te erven die de meeste dingen behandelt en redelijk standaardgedrag verstrekt: de klasse com.day.cq.dam.core.AbstractAssetHandler.
   * Deze klasse verstrekt reeds een abstracte de dienstbeschrijver. Dus als u overerft van deze klasse en de gemaven-sling-plugin gebruikt, zorg ervoor dat u de overervingsvlag aan waar plaatst.

De volgende methoden moeten worden toegepast:

* `extractMetadata()`: met deze methode worden alle beschikbare metagegevens geëxtraheerd.
* `getThumbnailImage()`: met deze methode maakt u een miniatuurafbeelding van het doorgegeven element.
* `getMimeTypes()`: Deze methode retourneert het MIME-type(n) van het element.

Hier volgt een voorbeeldsjabloon:

pakket my.own.stuff; /&amp;ast;&amp;ast; &amp;ast; @scr.component inherit=&quot;true&quot;&amp;ast; @scr.service&amp;ast;/ openbare klasse MyMediaHandler breidt com.day.cq.dam.core.AbstractAssetHandler { // implementeert de relevante onderdelen }

De interface en de klassen omvatten:

* `com.day.cq.dam.api.handler.AssetHandler` interface: Deze interface beschrijft de dienst die steun voor specifieke types MIME toevoegt. Als u een nieuw MIME-type wilt toevoegen, moet u deze interface implementeren. De interface bevat methoden voor het importeren en exporteren van de specifieke documenten, voor het maken van miniaturen en het uitnemen van metagegevens.
* `com.day.cq.dam.core.AbstractAssetHandler` klasse: Deze klasse fungeert als basis voor alle andere implementaties van elementenhandlers en biedt veelgebruikte functionaliteit.
* `com.day.cq.dam.core.AbstractSubAssetHandler` klasse: Deze klasse fungeert als basis voor alle andere implementaties van elementenhandlers en biedt veelgebruikte functionaliteit plus veelgebruikte functionaliteit voor het extraheren van subelementen.

#### Voorbeeld: een specifieke teksthandler {#example-create-a-specific-text-handler} maken

In deze sectie maakt u een specifieke teksthandler die miniaturen met een watermerk genereert.

Ga als volgt te werk:

Raadpleeg [Development Tools](../sites-developing/dev-tools.md) om Eclipse te installeren en in te stellen met een [!DNL Maven]-plug-in en voor het instellen van de afhankelijkheden die nodig zijn voor het [!DNL Maven]-project.

Nadat u de volgende procedure hebt uitgevoerd en u een TXT-bestand uploadt naar [!DNL Experience Manager], worden de metagegevens van het bestand geëxtraheerd en worden twee miniaturen met een watermerk gegenereerd.

1. Maak in Eclipse `myBundle` [!DNL Maven]-project:

   1. Klik in de menubalk op **[!UICONTROL File]** > **[!UICONTROL New]** > **[!UICONTROL Other]**.
   1. Vouw in het dialoogvenster de map [!DNL Maven] uit, selecteer [!DNL Maven] en klik op **[!UICONTROL Next]**.
   1. Controleer Create een eenvoudig projectvakje en het vakje van de Plaatsen van de Werkruimte van het Gebruik standaard, dan klik **[!UICONTROL Next]**.
   1. Definieer een [!DNL Maven]-project:

      * Groep-id: `com.day.cq5.myhandler`.
      * Artefact-id: myBundle.
      * Naam: Mijn [!DNL Experience Manager]-bundel.
      * Omschrijving: Dit is mijn [!DNL Experience Manager] bundel.
   1. Klik op **[!UICONTROL Finish]**.


1. Stel de [!DNL Java]-compiler in op versie 1.5:

   1. Klik met de rechtermuisknop op het `myBundle`-project en selecteer [!UICONTROL Properties].
   1. Selecteer [!UICONTROL Java Compiler] en stel de volgende eigenschappen in op 1.5:

      * Compatibiliteitsniveau compiler
      * Compatibiliteit van gegenereerde .class-bestanden
      * Broncompatibiliteit
   1. Klik op **[!UICONTROL OK]**. Klik in het dialoogvenster op **[!UICONTROL Yes]**.


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

1. Maak het pakket `com.day.cq5.myhandler` dat de [!DNL Java]-klassen onder `myBundle/src/main/java` bevat:

   1. Klik onder myBundle met de rechtermuisknop op `src/main/java`, selecteer Nieuw en vervolgens Pakket.
   1. Geef deze `com.day.cq5.myhandler` een naam en klik op Voltooien.

1. Maak de [!DNL Java]-klasse `MyHandler`:

   1. Klik in [!DNL Eclipse] onder `myBundle/src/main/java` met de rechtermuisknop op het `com.day.cq5.myhandler`-pakket. Selecteer [!UICONTROL New] en [!UICONTROL Class].
   1. Geef in het dialoogvenster de [!DNL Java]-klasse `MyHandler` een naam en klik op [!UICONTROL Finish]. [!DNL Eclipse] maakt en opent het bestand  `MyHandler.java`.
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
      watermarkLayer = ImageHelper.createLayer(session, "/content/dam/geometrixx/icons/certificate.png");
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
     // We need to keep track of the last character, if we have two whitespaces in a row we don't want to double count.
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

1. Compileer de klasse [!DNL Java] en maak de bundel:

   1. Klik met de rechtermuisknop op het `myBundle`-project, selecteer **[!UICONTROL Run As]** en **[!UICONTROL Maven Install]**.
   1. De bundel `myBundle-0.0.1-SNAPSHOT.jar` (die de gecompileerde klasse bevat) wordt gecreeerd onder `myBundle/target`.

1. Maak in de CRX-verkenner een nieuw knooppunt onder `/apps/myApp`. Naam = `install`, Type = `nt:folder`.
1. Kopieer de bundel `myBundle-0.0.1-SNAPSHOT.jar` en bewaar deze onder `/apps/myApp/install` (bijvoorbeeld met WebDAV). De nieuwe teksthandler is nu actief in [!DNL Experience Manager].
1. Open [!UICONTROL Apache Felix Web Management Console] in uw browser. Selecteer de tab [!UICONTROL Components] en schakel de standaardteksthandler `com.day.cq.dam.core.impl.handler.TextHandler` uit.

## Op Command Line gebaseerde media-handler {#command-line-based-media-handler}

[!DNL Experience Manager] kunt u elk opdrachtregelprogramma binnen een workflow uitvoeren om elementen (zoals  [!DNL ImageMagick]) om te zetten en de nieuwe vertoning aan het element toe te voegen. U hoeft het opdrachtregelprogramma alleen te installeren op de schijf die als host fungeert voor de [!DNL Experience Manager]-server en een processtap toe te voegen en te configureren voor de workflow. Met het aangeroepen proces met de naam `CommandLineProcess` kunt u filteren op basis van specifieke MIME-typen en meerdere miniaturen maken op basis van de nieuwe uitvoering.

De volgende conversies kunnen automatisch worden uitgevoerd en opgeslagen binnen [!DNL Assets]:

* EPS- en AI-transformatie met [ImageMagick](https://www.imagemagick.org/script/index.php) en [Ghostscript](https://www.ghostscript.com/).
* FLV-videotranscodering met [MPEG](https://ffmpeg.org/).
* MP3-codering met [LAME](https://lame.sourceforge.io/).
* Audioverwerking met behulp van [SOX](https://sox.sourceforge.net/).

>[!NOTE]
>
>Op niet-Windows-systemen retourneert het Mpeg-gereedschap een fout tijdens het genereren van uitvoeringen voor een video-element met één aanhalingsteken (&#39;) in de bestandsnaam. Als de naam van het videobestand één aanhalingsteken bevat, verwijdert u het bestand voordat u het uploadt naar [!DNL Experience Manager].

Met het proces `CommandLineProcess` worden de volgende bewerkingen uitgevoerd in de volgorde waarin ze worden weergegeven:

* Hiermee wordt het bestand gefilterd op basis van specifieke MIME-typen, indien opgegeven.
* Maakt een tijdelijke map op de schijf die als host fungeert voor de [!DNL Experience Manager]-server.
* Hiermee wordt het oorspronkelijke bestand gestroomd naar de tijdelijke map.
* Voert de opdracht uit die door de argumenten van de stap wordt gedefinieerd. Het bevel wordt uitgevoerd binnen de tijdelijke folder met de toestemmingen van de gebruiker die [!DNL Experience Manager] in werking stelt.
* Hiermee wordt het resultaat weer gestroomd naar de weergavemap van de [!DNL Experience Manager]-server.
* Hiermee verwijdert u de tijdelijke map.
* Hiermee maakt u miniaturen op basis van deze uitvoeringen, indien opgegeven. Het aantal en de afmetingen van de miniaturen worden bepaald door de argumenten van de stap.

### Een voorbeeld met [!DNL ImageMagick] {#an-example-using-imagemagick}

In het volgende voorbeeld ziet u hoe u de opdrachtregelprocesstap zo instelt dat telkens wanneer een element met het e-type miMIME GIF of TIFF wordt toegevoegd aan `/content/dam` op de [!DNL Experience Manager]-server, een gespiegelde afbeelding van het origineel wordt gemaakt samen met drie extra miniaturen (140x100, 48x48 en 10x25 0).

Gebruik [!DNL ImageMagick] om dit te doen. [!DNL ImageMagick] is een gratis opdrachtregelprogramma waarmee u bitmapafbeeldingen kunt maken, bewerken en samenstellen.

Installeer [!DNL ImageMagick] op de schijf die als host fungeert voor de [!DNL Experience Manager]-server:

1. [!DNL ImageMagick] installeren: Zie [ImageMagick-documentatie](https://www.imagemagick.org/script/download.php).
1. Stel het gereedschap zo in dat u het op de opdrachtregel kunt omzetten.
1. Als u wilt controleren of het gereedschap op de juiste wijze is geïnstalleerd, voert u de volgende opdracht `convert -h` uit op de opdrachtregel.

   Er wordt een Help-scherm weergegeven met alle mogelijke opties van het gereedschap Omzetten.

   >[!NOTE]
   >
   >In sommige versies van Windows kan de opdracht Omzetten niet worden uitgevoerd omdat er een conflict optreedt met het native hulpprogramma voor conversie dat onderdeel is van [!DNL Windows]-installatie. Geef in dit geval het volledige pad op voor de [!DNL ImageMagick]-software die wordt gebruikt om afbeeldingsbestanden om te zetten in miniaturen. Bijvoorbeeld, `"C:\Program Files\ImageMagick-6.8.9-Q16\convert.exe" -define jpeg:size=319x319 ${filename} -thumbnail 319x319 cq5dam.thumbnail.319.319.png`.

1. Als u wilt zien of het gereedschap correct wordt uitgevoerd, voegt u een JPG-afbeelding toe aan de werkmap en voert u de opdracht `<image-name>.jpg -flip <image-name>-flipped.jpg` omzetten uit op de opdrachtregel. Er wordt een gespiegelde afbeelding aan de map toegevoegd. Voeg vervolgens de processtap van de opdrachtregel toe aan de **[!UICONTROL DAM Update Asset]**-workflow.
1. Ga naar de **[!UICONTROL Workflow]** console.
1. Bewerk op het tabblad **[!UICONTROL Models]** het model **[!UICONTROL DAM Update Asset]**.
1. Wijzig [!UICONTROL Arguments] van de stap **[!UICONTROL Web enabled rendition]** in: `mime:image/gif,mime:image/tiff,tn:140:100,tn:48:48,tn:10:250,cmd:convert ${directory}/${filename} -flip ${directory}/${basename}.flipped.jpg`.
1. Sla de workflow op.

Voeg een element toe aan `/content/dam` om de gewijzigde workflow te testen.

1. Haal in het bestandssysteem een TIFF-afbeelding van uw keuze op. Wijzig de naam in `myImage.tiff` en kopieer het naar `/content/dam`, bijvoorbeeld door WebDAV te gebruiken.
1. Ga naar de **[!UICONTROL CQ5 DAM]** console, bijvoorbeeld `http://localhost:4502/libs/wcm/core/content/damadmin.html`.
1. Open het element **[!UICONTROL myImage.tiff]** en controleer of de gespiegelde afbeelding en de drie miniaturen zijn gemaakt.

#### Vorm de CommandLineProcess stap {#configuring-the-commandlineprocess-process-step}

In deze sectie wordt beschreven hoe u [!UICONTROL Process Arguments] van [!UICONTROL CommandLineProcess] instelt.

Scheid de waarden van [!UICONTROL Process Arguments] gebruikend komma en begin het niet met whitespace.

| Argument-formaat | Beschrijving |
|---|---|
| mime:&lt;mime-type> | Optioneel argument. Het proces wordt toegepast als het element hetzelfde MIME-type heeft als het argument. <br>Er kunnen verschillende MIME-typen worden gedefinieerd. |
| tn:&lt;width>:&lt;height> | Optioneel argument. Het proces leidt tot een duimnagel met de afmetingen die in het argument worden bepaald. <br>Er kunnen verschillende miniaturen worden gedefinieerd. |
| cmd: &lt;command> | Definieert de opdracht die wordt uitgevoerd. De syntaxis hangt van het hulpmiddel van de bevellijn af. Er kan slechts één opdracht worden gedefinieerd. <br>De volgende variabelen kunnen worden gebruikt om de opdracht te maken:<br>`${filename}`: naam van het invoerbestand, bijvoorbeeld original.jpg  <br> `${file}`: de volledige padnaam van het invoerbestand, bijvoorbeeld  `/tmp/cqdam0816.tmp/original.jpg` <br> `${directory}`: map van het invoerbestand, bijvoorbeeld  `/tmp/cqdam0816.tmp` <br>`${basename}`: naam van het invoerbestand zonder de extensie, bijvoorbeeld origineel  <br>`${extension}`: extensie van het invoerbestand, bijvoorbeeld JPG. |

Als [!DNL ImageMagick] bijvoorbeeld is geïnstalleerd op de schijf die als host fungeert voor de [!DNL Experience Manager]-server en u een processtap maakt met [!UICONTROL CommandLineProcess] als implementatie en de volgende waarden als [!UICONTROL Process Arguments]:

`mime:image/gif,mime:image/tiff,tn:140:100,tn:48:48,tn:10:250,cmd:convert ${directory}/${filename} -flip ${directory}/${basename}.flipped.jpg`

Als de workflow vervolgens wordt uitgevoerd, is de stap alleen van toepassing op elementen met `image/gif` of `mime:image/tiff` als `mime-types`, wordt een gespiegelde afbeelding van het origineel gemaakt, wordt deze omgezet in JPG en worden drie miniaturen met de afmetingen gemaakt: 140x100, 48x48 en 10x250.

Gebruik de volgende [!UICONTROL Process Arguments] om de drie standaardminiaturen te maken met [!DNL ImageMagick]:

`mime:image/tiff,mime:image/png,mime:image/bmp,mime:image/gif,mime:image/jpeg,cmd:convert ${filename} -define jpeg:size=319x319 -thumbnail "319x319>" -background transparent -gravity center -extent 319x319 -write png:cq5dam.thumbnail.319.319.png -thumbnail "140x100>" -background transparent -gravity center -extent 140x100 -write cq5dam.thumbnail.140.100.png -thumbnail "48x48>" -background transparent -gravity center -extent 48x48 cq5dam.thumbnail.48.48.png`

Gebruik de volgende [!UICONTROL Process Arguments] om de voor het web geschikte vertoning te maken met [!DNL ImageMagick]:

`mime:image/tiff,mime:image/png,mime:image/bmp,mime:image/gif,mime:image/jpeg,cmd:convert ${filename} -define jpeg:size=1280x1280 -thumbnail "1280x1280>" cq5dam.web.1280.1280.jpeg`

>[!NOTE]
>
>De stap [!UICONTROL CommandLineProcess] is alleen van toepassing op elementen (knooppunten van het type `dam:Asset`) of afstammingen van een element.

>[!MORELIKETHIS]
>
>* [Proceselementen](assets-workflow.md)

