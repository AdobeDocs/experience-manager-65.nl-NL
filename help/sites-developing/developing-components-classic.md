---
title: Adobe Experience Manager-componenten ontwikkelen (klassieke gebruikersinterface)
description: De klassieke UI gebruikt ExtJS om widgets tot stand te brengen die het blik-en-gevoel van de componenten verstrekken. HTML is niet de aanbevolen scripttaal voor Adobe Experience Manager (AEM).
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
legacypath: /content/docs/en/aem/6-2/develop/components/components-classic
exl-id: 3f078139-73fd-4913-9d67-264fb2515f8a
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '2340'
ht-degree: 0%

---

# Adobe Experience Manager-componenten (AEM) ontwikkelen (klassieke gebruikersinterface){#developing-aem-components-classic-ui}

De klassieke UI gebruikt ExtJS om widgets tot stand te brengen die het blik-en-gevoel van de componenten verstrekken. Vanwege de aard van deze widgets zijn er enkele verschillen tussen de manier waarop componenten communiceren met de klassieke gebruikersinterface en de [interface met aanraakbediening](/help/sites-developing/developing-components.md).

>[!NOTE]
>
>Veel aspecten van componentontwikkeling worden zowel door de klassieke UI als door de interface met aanraakbediening gebruikt, zodat **u moet lezen [Componenten AEM - De basisbeginselen](/help/sites-developing/components-basics.md) voor** het gebruiken van deze pagina, die de specifieke details van klassieke UI behandelt.

>[!NOTE]
>
>Hoewel zowel de Taal van het Malplaatje van de HTML (HTML) als JSP voor het ontwikkelen van componenten voor klassieke UI kan worden gebruikt, illustreert deze pagina ontwikkeling met JSP. Dit is uitsluitend het gevolg van de geschiedenis van het gebruik van JSP in de klassieke UI.
>
>HTML is nu de aanbevolen scripttaal voor AEM. Zie [HTL](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html) en [Ontwikkelen AEM componenten](/help/sites-developing/developing-components.md) om methoden te vergelijken.

## Structuur {#structure}

De basisstructuur van een component wordt op de pagina bedekt [Componenten AEM - De basisbeginselen](/help/sites-developing/components-basics.md#structure), die zowel de aanraakinterface als de klassieke interface toepast. Zelfs als u de instellingen voor de interface met aanraakbediening in uw nieuwe component niet hoeft te gebruiken, is het handig om deze instellingen te kennen wanneer u overerft van bestaande componenten.

## JSP-scripts {#jsp-scripts}

JSP de Manuscripten of de Server kunnen worden gebruikt om componenten terug te geven. Volgens de regels van de verzoekverwerking van Sling, is de naam voor het standaardmanuscript:

`<*componentname*>.jsp`

## global.jsp {#global-jsp}

Het JSP-scriptbestand `global.jsp` wordt gebruikt om snel toegang tot specifieke voorwerpen (namelijk tot inhoud) aan om het even welk JSP manuscriptdossier te verlenen dat wordt gebruikt om een component terug te geven.

Daarom `global.jsp` moet worden opgenomen in elk component die JSP-script rendert, waarbij een of meer van de objecten die worden geleverd in `global.jsp` worden gebruikt.

De locatie van de standaardinstelling `global.jsp` is:

`/libs/foundation/global.jsp`

>[!NOTE]
>
>Het pad `/libs/wcm/global.jsp`, die door versies CQ 5.3 en eerder werd gebruikt, is nu achterhaald.

### Functie van global.jsp, gebruikte API&#39;s en Taglibs {#function-of-global-jsp-used-apis-and-taglibs}

De volgende lijst maakt een lijst van de belangrijkste voorwerpen die van het gebrek worden verstrekt `global.jsp`:

Samenvatting:

* `<cq:defineObjects />`

   * `slingRequest` - Het omvattende aanvraagobject ( `SlingHttpServletRequest`).
   * `slingResponse` - Het omvattende object Response ( `SlingHttpServletResponse`).
   * `resource` - Het object Sling Resource ( `slingRequest.getResource();`).
   * `resourceResolver` - Het object Sling Resource Resolver ( `slingRequest.getResoucreResolver();`).
   * `currentNode` - Het opgeloste JCR-knooppunt voor het verzoek.
   * `log` - Het standaardlogger ().
   * `sling` - De Sling-scripthulper.
   * `properties` - De eigenschappen van de geadresseerde bron ( `resource.adaptTo(ValueMap.class);`).
   * `pageProperties` - De eigenschappen van de pagina van de geadresseerde bron.
   * `pageManager` - Het paginabeheer voor toegang tot AEM inhoudspagina&#39;s ( `resourceResolver.adaptTo(PageManager.class);`).
   * `component` - Het componentobject van de huidige AEM.
   * `designer` - Het Designer-object voor het ophalen van ontwerpgegevens ( `resourceResolver.adaptTo(Designer.class);`).
   * `currentDesign` - Het ontwerp van de geadresseerde bron.
   * `currentStyle` - De stijl van de geadresseerde bron.

### Inhoud openen {#accessing-content}

Er zijn drie methodes om tot inhoud in AEM WCM toegang te hebben:

* Via het object properties dat is geïntroduceerd in `global.jsp`:

  Het object properties is een instantie van een ValueMap (zie [Verkopen-API](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/ValueMap.html)) en bevat alle eigenschappen van de huidige bron.

  Voorbeeld: `String pageTitle = properties.get("jcr:title", "no title");` gebruikt in het renderscript van een paginacomponent.

  Voorbeeld: `String paragraphTitle = properties.get("jcr:title", "no title");` gebruikt in het renderscript van een standaard-alineacomponent.

* Via de `currentPage` object geïntroduceerd in `global.jsp`:

  De `currentPage` object is een instantie van een pagina (zie [AEM API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/Page.html)). De paginaklasse biedt enkele methoden om toegang te krijgen tot inhoud.

  Voorbeeld: `String pageTitle = currentPage.getTitle();`

* Via `currentNode` object geïntroduceerd in `global.jsp`:

  De `currentNode` object is een instantie van een knooppunt (zie [JCR-API](https://jackrabbit.apache.org/api/2.16/org/apache/jackrabbit/standalone/cli/core/CurrentNode.html)). De eigenschappen van een knooppunt kunnen worden benaderd door `getProperty()` methode.

  Voorbeeld: `String pageTitle = currentNode.getProperty("jcr:title");`

## JSP-tagbibliotheken {#jsp-tag-libraries}

De CQ- en Sling-tagbibliotheken geven u toegang tot specifieke functies voor gebruik in het JSP-script van uw sjablonen en componenten.

Zie het document voor meer informatie [Tagbibliotheken](/help/sites-developing/taglib.md).

## Client-Side HTML-bibliotheken gebruiken {#using-client-side-html-libraries}

Moderne websites zijn sterk afhankelijk van verwerking op de client door complexe JavaScript- en CSS-code. Het organiseren en optimaliseren van het gebruik van deze code kan een ingewikkeld probleem zijn.

Om dit probleem te helpen aanpakken, AEM biedt **Client-side bibliotheekmappen**, waarmee u uw code aan de clientzijde in de opslagplaats kunt opslaan, deze in categorieën kunt ordenen en kunt bepalen wanneer en hoe elke categorie code aan de client moet worden aangeboden. Het client-side bibliotheeksysteem zorgt vervolgens voor het maken van de juiste koppelingen in de uiteindelijke webpagina om de juiste code te laden.

Zie het document [Client-Side HTML-bibliotheken gebruiken](/help/sites-developing/clientlibs.md) voor meer informatie .

## Dialoog {#dialog}

Uw component heeft een dialoogvenster nodig waarin auteurs de inhoud kunnen toevoegen en configureren.

Zie [Componenten AEM - De basisbeginselen](/help/sites-developing/components-basics.md#dialogs) voor nadere bijzonderheden.

## Werking bewerken configureren {#configuring-the-edit-behavior}

U kunt het bewerkingsgedrag van een component configureren. Dit omvat kenmerken zoals acties beschikbaar voor de component, kenmerken van de plaatsredacteur, en luisteraars met betrekking tot gebeurtenissen op de component. De configuratie geldt voor zowel de aanraakinterface als de klassieke gebruikersinterface, maar met bepaalde specifieke verschillen.

De [bewerkingsgedrag van een component is geconfigureerd](/help/sites-developing/components-basics.md#edit-behavior) door een `cq:editConfig` knooppunt van type `cq:EditConfig` onder het componentknooppunt (van het type `cq:Component`) en door specifieke eigenschappen en onderliggende knooppunten toe te voegen.

## ExtJS-widgets gebruiken en uitbreiden {#using-and-extending-extjs-widgets}

Zie [ExtJS-widgets gebruiken en uitbreiden](/help/sites-developing/widgets.md) voor meer informatie .

## Xtypes gebruiken voor ExtJS-widgets {#using-xtypes-for-extjs-widgets}

Zie [Xtypes gebruiken](/help/sites-developing/xtypes.md) voor meer informatie .

## Nieuwe componenten ontwikkelen {#developing-new-components}

In deze sectie wordt beschreven hoe u uw eigen componenten kunt maken en deze aan het alineasysteem kunt toevoegen.

U kunt snel aan de slag door een bestaande component te kopiëren en vervolgens de gewenste wijzigingen aan te brengen.

Een voorbeeld van hoe u een component kunt ontwikkelen wordt in detail beschreven [De component Tekst en Afbeelding uitbreiden - Een voorbeeld.](#extending-the-text-and-image-component-an-example)

### Een nieuwe component ontwikkelen (bestaande component aanpassen) {#develop-a-new-component-adapt-existing-component}

Als u nieuwe componenten voor AEM wilt ontwikkelen op basis van een bestaande component, kunt u de component kopiëren, een JavaScript-bestand voor de nieuwe component maken en opslaan op een locatie die toegankelijk is voor AEM (zie ook [Componenten en andere elementen aanpassen](/help/sites-developing/dev-guidelines-bestpractices.md#customizing-components-and-other-elements)):

1. Maak met CRXDE Lite een componentmap in:

   / `apps/<myProject>/components/<myComponent>`

   Maak de knoopstructuur opnieuw zoals in bibliotheken, kopieer dan de definitie van een bestaande component, zoals de component van de Tekst. Bijvoorbeeld om het de componentenexemplaar van de Tekst aan te passen:

   * Van `/libs/foundation/components/text`
   * tot `/apps/myProject/components/text`

1. Wijzig de `jcr:title` om de nieuwe naam weer te geven.
1. Open de nieuwe componentenomslag en breng de veranderingen aan u vereist. Verwijder ook alle andere gegevens in de map.

   U kunt wijzigingen aanbrengen zoals:

   * een veld toevoegen in het dialoogvenster

      * `cq:dialog` - dialoogvenster voor de interface met aanraakbediening
      * `dialog` - dialoog voor de klassieke gebruikersinterface

   * vervangen `.jsp` bestand (naam na nieuwe component)
   * of de volledige component volledig opnieuw te bewerken als u wilt

   Als u bijvoorbeeld een kopie van de standaardtekstcomponent maakt, kunt u een extra veld aan het dialoogvenster toevoegen en vervolgens de `.jsp` om de input te verwerken die daar is gemaakt.

   >[!NOTE]
   >
   >Een component voor de:
   >
   >* Interface met aanraakbediening gebruikt [Graniet](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html) componenten
   >* Klassieke UI gebruikt [ExtJS-widgets](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

   >[!NOTE]
   >
   >Een dialoogvenster dat is gedefinieerd voor de klassieke gebruikersinterface werkt binnen de interface met aanraakbediening.
   >
   >Een dialoogvenster dat is gedefinieerd voor de interface met aanraakbediening werkt niet binnen de klassieke interface.
   >
   >Afhankelijk van uw instantie en auteursomgeving, zou u beide soorten dialoog voor uw component kunnen willen bepalen.

1. Een van de volgende knooppunten moet aanwezig zijn en moet correct zijn geïnitialiseerd om de nieuwe component weer te geven:

   * `cq:dialog` - dialoogvenster voor de interface met aanraakbediening
   * `dialog` - dialoog voor de klassieke gebruikersinterface
   * `cq:editConfig` - hoe componenten zich gedragen in de bewerkingsomgeving (bijvoorbeeld slepen en neerzetten)
   * `design_dialog` - dialoogvenster voor ontwerpmodus (alleen klassieke gebruikersinterface)

1. Activeer de nieuwe component in uw alineasysteem door:

   * met CRXDE Lite de waarde toevoegen `<path-to-component>` (bijvoorbeeld `/apps/geometrixx/components/myComponent`) aan de eigenschapcomponenten van het knooppunt `/etc/designs/geometrixx/jcr:content/contentpage/par`
   * Volg de instructies in [Nieuwe componenten toevoegen aan alineasystemen](#adding-a-new-component-to-the-paragraph-system-design-mode)

1. Open in AEM WCM een pagina op uw website en voeg een alinea in van het type dat u hebt gemaakt om ervoor te zorgen dat de component goed werkt.

>[!NOTE]
>
>Als u timingstatistieken voor het laden van pagina&#39;s wilt zien, kunt u Ctrl-Shift-U gebruiken - met `?debugClientLibs=true` ingesteld in de URL.

### Een nieuwe component toevoegen aan het alineasysteem (ontwerpmodus) {#adding-a-new-component-to-the-paragraph-system-design-mode}

Nadat de component is ontwikkeld, voegt u deze toe aan het alineasysteem, waarmee auteurs de component kunnen selecteren en gebruiken tijdens het bewerken van een pagina.

1. Open bijvoorbeeld een pagina in de ontwerpomgeving waarin het alineasysteem wordt gebruikt. `<contentPath>/Test.html`.
1. Schakel over naar de ontwerpmodus door:

   * toevoegen `?wcmmode=design` aan het einde van de URL en de toegang tot de URL, bijvoorbeeld:

     `<contextPath>/ Test.html?wcmmode=design`

   * klikken op Ontwerpen in Sidekick

   U bevindt zich nu in de ontwerpmodus en kunt het alineasysteem bewerken.

1. Klik op Bewerken.

   Een lijst met onderdelen die tot het alineasysteem behoren, wordt weergegeven. Uw nieuwe component wordt ook vermeld.

   De componenten kunnen worden geactiveerd (of gedeactiveerd) om te bepalen welke componenten aan de auteur worden aangeboden wanneer het uitgeven van een pagina.

1. Activeer de component en ga terug naar de normale bewerkingsmodus om te bevestigen dat deze beschikbaar is voor gebruik.

### De component Tekst en Afbeelding uitbreiden - Een voorbeeld {#extending-the-text-and-image-component-an-example}

In deze sectie ziet u hoe u de veelgebruikte standaardcomponent voor tekst en afbeeldingen kunt uitbreiden met een configureerbare functie voor het plaatsen van afbeeldingen.

Met de extensie voor tekst en afbeeldingscomponenten kunnen editors alle bestaande functionaliteit van de component gebruiken en beschikken ze over een extra optie om de plaatsing van de afbeelding op te geven:

* Aan de linkerkant van de tekst (huidig gedrag en de nieuwe standaard)
* En aan de rechterkant

Nadat u deze component hebt uitgebreid, kunt u de plaatsing van de afbeelding configureren via het dialoogvenster van de component.

In deze exercitie worden de volgende technieken beschreven:

* Bestaande componentnode kopiëren en de metagegevens wijzigen
* Het dialoogvenster van de component aanpassen, inclusief de overerving van widgets uit bovenliggende dialoogvensters
* Het wijzigen van het manuscript van de component om de nieuwe functionaliteit uit te voeren

>[!NOTE]
>
>Dit voorbeeld is gericht op klassieke UI.

>[!NOTE]
>
>Dit voorbeeld is gebaseerd op de inhoud van het monster van de Geometrixx, die niet meer met AEM wordt verscheept, die door Wij.Retail is vervangen. Zie het document [We.Retail Reference Implementation](/help/sites-developing/we-retail.md#we-retail-geometrixx) voor het downloaden en installeren van Geometrixx.

#### De bestaande textielcomponent uitbreiden {#extending-the-existing-textimage-component}

Om de component tot stand te brengen, gebruikt u de standaardcomponent van de textielafbeelding als basis en wijzigt het. U slaat de nieuwe component in de Geometrixx AEM WCM voorbeeldtoepassing op.

1. De standaardtextielcomponent kopiëren uit `/libs/foundation/components/textimage` in de map Geometrixx, `/apps/geometrixx/components`, met gebruik van textiel als de naam van het doelknooppunt. (Kopieer de component door naar de component te navigeren, met de rechtermuisknop te klikken en Kopiëren te selecteren en naar de doelmap te bladeren.)

   ![chlimage_1-59](assets/chlimage_1-59a.png)

1. Als u dit voorbeeld eenvoudig wilt houden, navigeert u naar de component die u hebt gekopieerd en verwijdert u alle subknooppunten van het nieuwe knooppunt naast de volgende:

   * definitie van dialoogvenster: `textimage/dialog`
   * componentscript: `textimage/textimage.jsp`
   * configuratieknooppunt bewerken (voor slepen en neerzetten van elementen): `textimage/cq:editConfig`

   >[!NOTE]
   >
   >De definitie van het dialoogvenster is afhankelijk van de gebruikersinterface:
   >
   >* Interface met aanraakbediening: `textimage/cq:dialog`
   >* Klassieke gebruikersinterface: `textimage/dialog`

1. Bewerk de metagegevens van de component:

   * Componentnaam

      * Set `jcr:description` tot `Text Image Component (Extended)`
      * Set `jcr:title` tot `Text Image (Extended)`

   * Groep, waar de component in sidekick (verlaat zoals is) wordt vermeld

      * Verlaten `componentGroup` instellen op `General`

   * Bovenliggende component voor de nieuwe component (de standaard textielcomponent)

      * Set `sling:resourceSuperType` tot `foundation/components/textimage`

   Na deze stap ziet het componentknooppunt er als volgt uit:

   ![chlimage_1-60](assets/chlimage_1-60a.png)

1. Wijzig de `sling:resourceType` eigenschap van het bewerkingsconfiguratieknooppunt van de afbeelding (eigenschap: `textimage/cq:editConfig/cq:dropTargets/image/parameters/sling:resourceType`) naar `geometrixx/components/textimage.`

   Op deze manier geldt dat wanneer een afbeelding naar de component op de pagina wordt neergezet, de `sling:resourceType` eigenschap van de uitgebreide textielcomponent wordt ingesteld op: `geometrixx/components/textimage.`

1. Wijzig de de dialoogdoos van de component om de nieuwe optie te omvatten. De nieuwe component neemt de delen van het dialoogvenster over die hetzelfde zijn als in het origineel. De enige toevoeging die u maakt, is het uitbreiden van de **Geavanceerd** tabblad, toevoegen **Positie afbeelding** vervolgkeuzelijst, met opties **Links** en **Rechts**:

   * Laat de `textimage/dialog`eigenschappen ongewijzigd.

   Let op: `textimage/dialog/items` heeft vier subknooppunten, tab1 tot tab4, die de vier tabbladen van het dialoogvenster textiel vertegenwoordigen.

   * Voor de eerste twee tabbladen (tab1 en tab2):

      * Xtype wijzigen in cqinclude (om over te nemen van de standaardcomponent).
      * Een padeigenschap met waarden toevoegen `/libs/foundation/components/textimage/dialog/items/tab1.infinity.json`en `/libs/foundation/components/textimage/dialog/items/tab2.infinity.json`, respectievelijk.
      * Alle andere eigenschappen of subknooppunten verwijderen.

   * Voor tab3:

      * Eigenschappen en subknooppunten ongewijzigd laten
      * Een velddefinitie toevoegen aan `tab3/items`, knooppuntpositie van type `cq:Widget`
      * Stel de volgende eigenschappen (van het type String) in voor de nieuwe `tab3/items/position`knooppunt:

         * `name`: `./imagePosition`
         * `xtype`: `selection`
         * `fieldLabel`: `Image Position`
         * `type`: `select`

      * Subknooppunt toevoegen `position/options` van het type `cq:WidgetCollection` om de twee keuzen voor beeldplaatsing te vertegenwoordigen, en onder het creeert twee knopen, o1 en o2 van type `nt:unstructured`.
      * Voor knooppunt `position/options/o1` stel de eigenschappen in: `text` tot `Left` en `value` tot `left.`
      * Voor knooppunt `position/options/o2` stel de eigenschappen in: `text` tot `Right` en `value` tot `right`.

   * Tabblad4 verwijderen.

   Afbeeldingspositie wordt in de inhoud aangehouden als de `imagePosition`eigenschap of the node representing `textimage` alinea. Na deze stappen ziet het dialoogvenster van de component er als volgt uit:

   ![chlimage_1-61](assets/chlimage_1-61a.png)

1. Het componentscript uitbreiden, `textimage.jsp`, met extra verwerking van de nieuwe parameter:

   ```xml
   Image image = new Image(resource, "image");
   
   if (image.hasContent() || WCMMode.fromRequest(request) == WCMMode.EDIT) {
        image.loadStyleData(currentStyle);
   ```

   U gaat het gemarkeerde codefragment vervangen *%>&lt;div class=&quot;image&quot;>&lt;%* met nieuwe code die een aangepaste stijl voor deze tag genereert.

   ```xml
   // todo: add new CSS class for the 'right image' instead of using
   // the style attribute
   String style="";
        if (properties.get("imagePosition", "left").equals("right")) {
             style = "style=\"float:right\"";
        }
        %><div <%= style %> class="image"><%
   ```

1. Sla de component op in de opslagplaats. De component kan worden getest.

#### De nieuwe component controleren {#checking-the-new-component}

Nadat de component is ontwikkeld, kunt u deze aan het alineasysteem toevoegen. Hiermee kunnen auteurs de component selecteren en gebruiken tijdens het bewerken van een pagina. Met deze stappen kunt u de component testen.

1. Open een pagina in Geometrixx zoals Engels / Bedrijf.
1. Schakel over naar de ontwerpmodus door in de Sidekick op Ontwerpen te klikken.
1. Bewerk het ontwerp van het alineasysteem door op Bewerken te klikken op het alineasysteem in het midden van de pagina. Er wordt een lijst weergegeven met componenten die in het alineasysteem kunnen worden geplaatst. De nieuwe component, Text Image (Extended), moet hierin worden opgenomen. Activeer het voor het alineasysteem door het te selecteren en op OK te klikken.
1. Ga terug naar de bewerkingsmodus.
1. Voeg de alinea Tekstafbeelding (Extended) toe aan het alineasysteem en initialiseer tekst en afbeelding met voorbeeldinhoud. Sla de wijzigingen op.
1. Open het dialoogvenster van de tekst- en afbeeldingsalinea en wijzig de afbeeldingspositie op het tabblad Geavanceerd in Rechts. Klik vervolgens op OK om de wijzigingen op te slaan.
1. De alinea wordt weergegeven met de afbeelding aan de rechterkant.
1. De component is nu gebruiksklaar.

De component slaat zijn inhoud in een paragraaf op de pagina van het Bedrijf op.

### Uploadmogelijkheden van de afbeeldingscomponent uitschakelen {#disable-upload-capability-of-the-image-component}

Als u deze mogelijkheid wilt uitschakelen, gebruikt u de standaardafbeeldingscomponent als basis en wijzigt u deze. U slaat de nieuwe component op in de voorbeeldtoepassing Geometrixx.

1. De standaardafbeeldingscomponent kopiëren uit `/libs/foundation/components/image` in de map Geometrixx, `/apps/geometrixx/components`, waarbij afbeelding wordt gebruikt als de naam van het doelknooppunt.

   ![chlimage_1-62](assets/chlimage_1-62a.png)

1. Bewerk de metagegevens van de component:

   * Set **jcr:titel** tot `Image (Extended)`

1. Navigeren naar `/apps/geometrixx/components/image/dialog/items/image`.
1. Een eigenschap toevoegen:

   * **Naam**: `allowUpload`
   * **Type**: `String`
   * **Waarde**: `false`

   ![chlimage_1-63](assets/chlimage_1-63a.png)

1. Klikken **Alles opslaan**. De component kan worden getest.
1. Open een pagina in Geometrixx zoals Engels / Bedrijf.
1. Schakel over naar de ontwerpmodus en activeer Afbeelding (Extended).
1. Ga terug naar de bewerkingsmodus en voeg deze toe aan het alineasysteem. Op de volgende afbeeldingen ziet u de verschillen tussen de originele afbeeldingscomponent en de afbeelding die u hebt gemaakt.

   Originele afbeeldingscomponent:

   ![chlimage_1-64](assets/chlimage_1-64a.png)

   Uw nieuwe afbeeldingscomponent:

   ![chlimage_1-65](assets/chlimage_1-65a.png)

1. De component is nu gebruiksklaar.
