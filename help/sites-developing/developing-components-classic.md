---
title: AEM-componenten ontwikkelen (klassieke gebruikersinterface)
seo-title: AEM-componenten ontwikkelen (klassieke gebruikersinterface)
description: De klassieke UI gebruikt ExtJS om widgets tot stand te brengen die het blik-en-gevoel van de componenten verstrekken. HTML is niet de aanbevolen scripttaal voor AEM.
seo-description: De klassieke UI gebruikt ExtJS om widgets tot stand te brengen die het blik-en-gevoel van de componenten verstrekken. HTML is niet de aanbevolen scripttaal voor AEM.
uuid: ed53d7c6-5996-4892-81a4-4ac30df85f04
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
discoiquuid: c68f724f-f9b3-4018-8d3a-1680c53d73f8
legacypath: /content/docs/en/aem/6-2/develop/components/components-classic
translation-type: tm+mt
source-git-commit: c13eabdf4938a47ddf64d55b00f845199591b835

---


# AEM-componenten ontwikkelen (klassieke gebruikersinterface){#developing-aem-components-classic-ui}

De klassieke UI gebruikt ExtJS om widgets tot stand te brengen die het blik-en-gevoel van de componenten verstrekken. Vanwege de aard van deze widgets zijn er enkele verschillen tussen de manier waarop componenten communiceren met de klassieke gebruikersinterface en de gebruikersinterface voor [aanraakbediening](/help/sites-developing/developing-components.md).

>[!NOTE]
>
>Veel aspecten van componentontwikkeling worden zowel door de klassieke gebruikersinterface als door de interface met aanraakbediening gebruikt. **U moet dus[AEM-componenten - de basisbeginselen](/help/sites-developing/components-basics.md)lezen voordat** u deze pagina gebruikt. Deze pagina behandelt de specifieke kenmerken van de klassieke gebruikersinterface.

>[!NOTE]
>
>Hoewel zowel de Taal van het Malplaatje van HTML (HTML) als JSP voor het ontwikkelen van componenten voor klassieke UI kan worden gebruikt, illustreert deze pagina ontwikkeling met JSP. Dit is uitsluitend het gevolg van de geschiedenis van het gebruik van JSP in de klassieke UI.
>
>HTML is nu de aanbevolen scripttaal voor AEM. Zie [HTML](https://docs.adobe.com/content/help/en/experience-manager-htl/using/overview.html) en het [Ontwikkelen van AEM Componenten](/help/sites-developing/developing-components.md) om methodes te vergelijken.

## Structuur {#structure}

De basisstructuur van een component wordt behandeld op de pagina [AEM Components - de Grondbeginselen](/help/sites-developing/components-basics.md#structure), die zowel de aanraking-geëanbel als klassieke UIs toepast. Zelfs als u de instellingen voor de interface met aanraakbediening in uw nieuwe component niet hoeft te gebruiken, kunt u er beter op letten dat u deze instellingen ook in acht neemt wanneer u overerft van bestaande componenten.

## JSP-scripts {#jsp-scripts}

JSP de Manuscripten of de Server kunnen worden gebruikt om componenten terug te geven. Volgens de regels van de verzoekverwerking van het Verdelen is de naam voor het standaardmanuscript:

`<*componentname*>.jsp`

## global.jsp {#global-jsp}

Het JSP manuscriptdossier `global.jsp` wordt gebruikt om snelle toegang tot specifieke voorwerpen (d.w.z. tot inhoud) aan om het even welk JSP manuscriptdossier te verlenen dat wordt gebruikt om een component terug te geven.

Daarom `global.jsp` zou in elke component moeten worden omvat die JSP manuscript teruggeeft waar één of meerdere die voorwerpen in worden verstrekt in `global.jsp` worden gebruikt.

De standaardlocatie `global.jsp` is:

`/libs/foundation/global.jsp`

>[!NOTE]
>
>Het pad `/libs/wcm/global.jsp`, dat werd gebruikt door de versies CQ 5.3 en eerder, is nu verouderd.

### Functie van global.jsp, gebruikte API&#39;s en Taglibs {#function-of-global-jsp-used-apis-and-taglibs}

In het volgende voorbeeld worden de belangrijkste objecten weergegeven die standaard worden opgegeven `global.jsp`:

Overzicht:

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
   * `pageManager` - Het paginabeheer voor toegang tot AEM-inhoudspagina&#39;s ( `resourceResolver.adaptTo(PageManager.class);`).
   * `component` - Het componentobject van de huidige AEM-component.
   * `designer` - Het ontwerperobject voor het ophalen van ontwerpinformatie ( `resourceResolver.adaptTo(Designer.class);`).
   * `currentDesign` - Het ontwerp van de geadresseerde bron.
   * `currentStyle` - De stijl van de geadresseerde bron.

### Inhoud openen {#accessing-content}

Er zijn drie methoden om toegang te krijgen tot inhoud in AEM WCM:

* Via het object properties dat is geïntroduceerd in `global.jsp`:

   Het eigenschapsobject is een instantie van een ValueMap (zie [Sling API](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/ValueMap.html)) en bevat alle eigenschappen van de huidige bron.

   Voorbeeld: worden `String pageTitle = properties.get("jcr:title", "no title");` gebruikt in het renderscript van een paginacomponent.

   Voorbeeld: wordt `String paragraphTitle = properties.get("jcr:title", "no title");` gebruikt in het renderscript van een standaard alinea-component.

* Via het `currentPage` object dat is geïntroduceerd in `global.jsp`:

   Het `currentPage` object is een instantie van een pagina (zie [AEM API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/Page.mhtml)). De paginaklasse biedt enkele methoden om toegang te krijgen tot inhoud.

   Voorbeeld: `String pageTitle = currentPage.getTitle();`

* Via `currentNode` object geïntroduceerd in `global.jsp`:

   Het `currentNode` object is een instantie van een knooppunt (zie [JCR API](https://jackrabbit.apache.org/api/2.16/org/apache/jackrabbit/standalone/cli/core/CurrentNode.html)). De eigenschappen van een knooppunt kunnen worden benaderd door de `getProperty()` methode.

   Voorbeeld: `String pageTitle = currentNode.getProperty("jcr:title");`

## JSP-tagbibliotheken {#jsp-tag-libraries}

De CQ- en Sling-tagbibliotheken geven u toegang tot specifieke functies voor gebruik in het JSP-script van uw sjablonen en componenten.

Zie de documenttagbibliotheken voor meer informatie [](/help/sites-developing/taglib.md).

## HTML-bibliotheken aan de clientzijde gebruiken {#using-client-side-html-libraries}

Moderne websites zijn sterk afhankelijk van verwerking op de client door complexe JavaScript- en CSS-code. Het organiseren en optimaliseren van het gebruik van deze code kan een ingewikkeld probleem zijn.

Om dit probleem te verhelpen, biedt AEM bibliotheekmappen **aan de** clientzijde, waarmee u uw code aan de clientzijde in de opslagplaats kunt opslaan, in categorieën kunt indelen en kunt bepalen wanneer en hoe elke categorie code aan de client moet worden verzonden. Het client-side bibliotheeksysteem zorgt vervolgens voor het maken van de juiste koppelingen in de uiteindelijke webpagina om de juiste code te laden.

Zie het document [Clientside HTML-bibliotheken](/help/sites-developing/clientlibs.md) gebruiken voor meer informatie.

## Dialoog {#dialog}

Uw component heeft een dialoogvenster nodig waarin auteurs de inhoud kunnen toevoegen en configureren.

Zie [AEM-componenten - De basisbeginselen](/help/sites-developing/components-basics.md#dialogs) voor meer informatie.

## Werking bewerken configureren {#configuring-the-edit-behavior}

U kunt het bewerkingsgedrag van een component configureren. Dit omvat kenmerken zoals acties beschikbaar voor de component, kenmerken van de plaatsredacteur, en luisteraars met betrekking tot gebeurtenissen op de component. De configuratie geldt voor zowel de aanraakinterface als de klassieke gebruikersinterface, maar met bepaalde specifieke verschillen.

Het [bewerkingsgedrag van een component wordt geconfigureerd](/help/sites-developing/components-basics.md#edit-behavior) door een `cq:editConfig` knooppunt van het type `cq:EditConfig` onder het componentknooppunt (van het type `cq:Component`) toe te voegen en door specifieke eigenschappen en onderliggende knooppunten toe te voegen.

## ExtJS-widgets gebruiken en uitbreiden {#using-and-extending-extjs-widgets}

Zie [ExtJS-widgets](/help/sites-developing/widgets.md) gebruiken en uitbreiden voor meer informatie.

## Xtypes gebruiken voor ExtJS-widgets {#using-xtypes-for-extjs-widgets}

Zie Extypes [gebruiken](/help/sites-developing/xtypes.md) voor meer details.

## Nieuwe componenten ontwikkelen {#developing-new-components}

In deze sectie wordt beschreven hoe u uw eigen componenten kunt maken en deze aan het alineasysteem kunt toevoegen.

U kunt snel aan de slag door een bestaande component te kopiëren en vervolgens de gewenste wijzigingen aan te brengen.

Een voorbeeld van hoe u een component kunt ontwikkelen, wordt in detail beschreven in [De component Tekst en Afbeelding uitbreiden - een voorbeeld.](#extending-the-text-and-image-component-an-example)

### Een nieuwe component ontwikkelen (bestaande component aanpassen) {#develop-a-new-component-adapt-existing-component}

Als u nieuwe componenten voor AEM wilt ontwikkelen op basis van een bestaande component, kunt u de component kopiëren, een JavaScript-bestand voor de nieuwe component maken en dit opslaan op een locatie die toegankelijk is voor AEM (zie ook Componenten [aanpassen en andere elementen](/help/sites-developing/dev-guidelines-bestpractices.md#customizing-components-and-other-elements)):

1. Creëer met behulp van CRXDE Lite een nieuwe componentenomslag in:

   / `apps/<myProject>/components/<myComponent>`

   Maak de knoopstructuur opnieuw zoals in bibliotheken, kopieer dan de definitie van een bestaande component, zoals de component van de Tekst. Bijvoorbeeld om het de componentenexemplaar van de Tekst aan te passen:

   * from `/libs/foundation/components/text`
   * to `/apps/myProject/components/text`

1. Wijzig het `jcr:title` om op zijn nieuwe naam te wijzen.
1. Open de nieuwe componentenomslag en breng de veranderingen aan u vereist. Verwijder ook alle andere gegevens in de map.

   U kunt wijzigingen aanbrengen zoals:

   * een nieuw veld toevoegen in het dialoogvenster

      * `cq:dialog` - dialoogvenster voor de interface met aanraakbediening
      * `dialog` - dialoog voor de klassieke gebruikersinterface
   * het vervangen van het `.jsp` dossier (noem het na uw nieuwe component)
   * of de volledige component volledig opnieuw te bewerken als u wilt
   Als u bijvoorbeeld een kopie van de standaardtekstcomponent maakt, kunt u een extra veld aan het dialoogvenster toevoegen en vervolgens de invoer `.jsp` die daar is ingevoerd, verwerken.

   >[!NOTE]
   >
   >Een component voor de:
   >
   >* UI met aanraakbediening gebruikt [graniet](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/index.html) -componenten
   >* Klassieke UI gebruikt [ExtJS-widgets](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html)


   >[!NOTE]
   >
   >Een dialoogvenster dat is gedefinieerd voor de klassieke gebruikersinterface werkt binnen de interface met aanraakbediening.
   >
   >Een dialoogvenster dat is gedefinieerd voor de interface met aanraakbediening werkt niet binnen de klassieke interface.
   >
   >Afhankelijk van uw instantie en auteursomgeving kunt u beide soorten dialoog voor uw component willen bepalen.

1. Een van de volgende knooppunten moet aanwezig zijn en moet correct zijn geïnitialiseerd om de nieuwe component weer te geven:

   * `cq:dialog` - dialoogvenster voor de interface met aanraakbediening
   * `dialog` - dialoog voor de klassieke gebruikersinterface
   * `cq:editConfig` - hoe componenten zich gedragen in de bewerkingsomgeving (bijv. slepen en neerzetten)
   * `design_dialog` - dialoogvenster voor ontwerpmodus (alleen klassieke gebruikersinterface)

1. Activeer de nieuwe component in uw alineasysteem door:

   * het gebruiken van CRXDE Lite om de waarde `<path-to-component>` (bijvoorbeeld `/apps/geometrixx/components/myComponent`) aan de bezitscomponenten van de knoop toe te voegen `/etc/designs/geometrixx/jcr:content/contentpage/par`
   * Volg de instructies in het [Toevoegen van nieuwe componenten aan alineasystemen](#adding-a-new-component-to-the-paragraph-system-design-mode)

1. Open in AEM WCM een pagina op uw website en voeg een nieuwe alinea in van het type dat u net hebt gemaakt om ervoor te zorgen dat de component correct werkt.

>[!NOTE]
>
>Als u timingstatistieken voor het laden van pagina&#39;s wilt zien, kunt u Ctrl-Shift-U gebruiken, met de tijdinstellingen in de URL. `?debugClientLibs=true`

### Een nieuwe component toevoegen aan het alineasysteem (ontwerpmodus) {#adding-a-new-component-to-the-paragraph-system-design-mode}

Nadat de component is ontwikkeld, voegt u deze toe aan het alineasysteem, waarmee auteurs de component kunnen selecteren en gebruiken tijdens het bewerken van een pagina.

1. Open bijvoorbeeld een pagina in de ontwerpomgeving waarin het alineasysteem wordt gebruikt `<contentPath>/Test.html`.
1. Schakel over naar de ontwerpmodus door:

   * toevoegen `?wcmmode=design` aan het einde van de URL en opnieuw openen, bijvoorbeeld:

      `<contextPath>/ Test.html?wcmmode=design`

   * klikken op Ontwerpen in Sidetrap
   U bevindt zich nu in de ontwerpmodus en kunt het alineasysteem bewerken.

1. Klik op Bewerken.

   Een lijst met onderdelen die tot het alineasysteem behoren, wordt weergegeven. Uw nieuwe component wordt ook vermeld.

   De componenten kunnen worden geactiveerd (of gedeactiveerd) om te bepalen welke componenten aan de auteur worden aangeboden wanneer het uitgeven van een pagina.

1. Activeer de component en ga terug naar de normale bewerkingsmodus om te bevestigen dat deze beschikbaar is voor gebruik.

### De component Tekst en Afbeelding uitbreiden - Een voorbeeld {#extending-the-text-and-image-component-an-example}

In deze sectie wordt een voorbeeld gegeven van de manier waarop u de veelgebruikte standaardcomponent voor tekst en afbeeldingen kunt uitbreiden met een configureerbare functie voor het plaatsen van afbeeldingen.

Met de extensie voor tekst en afbeeldingscomponenten kunnen editors alle bestaande functionaliteit van de component gebruiken en beschikken ze over een extra optie om de plaatsing van de afbeelding op te geven:

* Aan de linkerkant van de tekst (huidig gedrag en de nieuwe standaard)
* en aan de rechterkant

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
>Dit voorbeeld is gebaseerd op de Geometrixx-voorbeeldinhoud, die niet meer bij AEM wordt geleverd en door We.Retail is vervangen. Zie het document [We.Retail Reference Implementation](/help/sites-developing/we-retail.md#we-retail-geometrixx) voor het downloaden en installeren van Geometrixx.

#### De bestaande textielcomponent uitbreiden {#extending-the-existing-textimage-component}

Om de nieuwe component tot stand te brengen, gebruiken wij de standaardtextielbeeldcomponent als basis en wijzigen het. We slaan de nieuwe component op in de WCM-voorbeeldtoepassing Geometrixx AEM.

1. Kopieer de standaardcomponent van de textielafbeelding van `/libs/foundation/components/textimage` `/apps/geometrixx/components`in de de componentenomslag van Geometrixx, gebruikend teximage als naam van de doelknoop. (Kopieer de component door naar de component te navigeren, met de rechtermuisknop te klikken en Kopiëren te selecteren en naar de doelmap te bladeren.)

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

      * Instellen `jcr:description` op `Text Image Component (Extended)`
      * Instellen `jcr:title` op `Text Image (Extended)`
   * Groep, waar de component in sidekick (verlaat zoals is) wordt vermeld

      * Laat `componentGroup` staan op `General`
   * Bovenliggende component voor de nieuwe component (de standaard textielcomponent)

      * Instellen `sling:resourceSuperType` op `foundation/components/textimage`
   Na deze stap ziet het componentknooppunt er als volgt uit:

   ![chlimage_1-60](assets/chlimage_1-60a.png)

1. Wijzig de `sling:resourceType` eigenschap van het bewerkingsconfiguratieknooppunt van de afbeelding (eigenschap: `textimage/cq:editConfig/cq:dropTargets/image/parameters/sling:resourceType`) tot `geometrixx/components/textimage.`

   Op deze manier wordt, wanneer een afbeelding naar de component op de pagina wordt neergezet, de `sling:resourceType` eigenschap van de uitgebreide component textielafbeelding ingesteld op: `geometrixx/components/textimage.`

1. Wijzig de de dialoogdoos van de component om de nieuwe optie te omvatten. De nieuwe component neemt de delen van het dialoogvenster over die hetzelfde zijn als in het origineel. De enige toevoeging die wij maken is het **Geavanceerde** lusje uit te breiden, toevoegend een vervolgkeuzelijst van de Positie **van het** Beeld, met opties **Links** en **Rechts**:

   * Laat de `textimage/dialog`eigenschappen ongewijzigd.
   Merk op hoe `textimage/dialog/items` heeft vier subnodes, tab1 tot tab4, die de vier tabbladen van het dialoogvenster textiel vertegenwoordigen.

   * Voor de eerste twee tabbladen (tab1 en tab2):

      * Xtype wijzigen in cqinclude (om over te nemen van de standaardcomponent).
      * Voeg een padeigenschap toe met respectievelijk waarden `/libs/foundation/components/textimage/dialog/items/tab1.infinity.json`en `/libs/foundation/components/textimage/dialog/items/tab2.infinity.json`.
      * Alle andere eigenschappen of subknooppunten verwijderen.
   * Voor tab3:

      * Eigenschappen en subknooppunten ongewijzigd laten
      * Een nieuwe velddefinitie toevoegen aan `tab3/items`, knooppositie van type `cq:Widget`
      * Stel de volgende eigenschappen (van het type String) in voor het nieuwe `tab3/items/position`knooppunt:

         * `name`: `./imagePosition`
         * `xtype`: `selection`
         * `fieldLabel`: `Image Position`
         * `type`: `select`
      * Voeg een subknooppunt `position/options` van het type toe `cq:WidgetCollection` om de twee opties voor plaatsing van de afbeelding te vertegenwoordigen. Onder dit knooppunt worden twee knooppunten gemaakt, o1 en o2 van het type `nt:unstructured`.
      * Voor knoop `position/options/o1` plaats de eigenschappen: `text` naar `Left` en `value` naar `left.`
      * Voor knoop `position/options/o2` plaats de eigenschappen: `text` naar `Right` en `value` naar `right`.
   * Tabblad4 verwijderen.
   Afbeeldingspositie wordt in de inhoud aangehouden als de `imagePosition`eigenschap van het knooppunt dat `textimage` alinea vertegenwoordigt. Na deze stappen ziet het dialoogvenster van de component er als volgt uit:

   ![chlimage_1-61](assets/chlimage_1-61a.png)

1. Breid het componentenmanuscript, `textimage.jsp`met extra behandeling van de nieuwe parameter uit:

   ```xml
   Image image = new Image(resource, "image");
   
   if (image.hasContent() || WCMMode.fromRequest(request) == WCMMode.EDIT) {
        image.loadStyleData(currentStyle);
   ```

   We gaan het gemarkeerde codefragment *%>&lt;div class=&quot;image&quot;>&lt;%* vervangen door nieuwe code die een aangepaste stijl voor deze tag genereert.

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
1. Schakel over naar de ontwerpmodus door op Ontwerpen in Sidetrap te klikken.
1. Bewerk het ontwerp van het alineasysteem door op Bewerken te klikken op het alineasysteem in het midden van de pagina. Er wordt een lijst weergegeven met componenten die in het alineasysteem kunnen worden geplaatst. De nieuwe component, Text Image (Extended), moet hierin worden opgenomen. Activeer het voor het alineasysteem door het te selecteren en op OK te klikken.
1. Ga terug naar de bewerkingsmodus.
1. Voeg de alinea Tekstafbeelding (Extended) toe aan het alineasysteem en initialiseer tekst en afbeelding met voorbeeldinhoud. Sla de wijzigingen op.
1. Open het dialoogvenster van de tekst- en afbeeldingsalinea en wijzig de afbeeldingspositie op het tabblad Geavanceerd in Rechts. Klik vervolgens op OK om de wijzigingen op te slaan.
1. De alinea wordt weergegeven met de afbeelding aan de rechterkant.
1. De component is nu gebruiksklaar.

De component slaat zijn inhoud in een paragraaf op de pagina van het Bedrijf op.

### Uploadmogelijkheden van de afbeeldingscomponent uitschakelen {#disable-upload-capability-of-the-image-component}

Om deze mogelijkheid uit te schakelen, gebruiken wij de standaardbeeldcomponent als basis en wijzigen het. We slaan de nieuwe component op in de voorbeeldtoepassing Geometrixx.

1. Kopieer de standaardafbeeldingscomponent van `/libs/foundation/components/image` naar de componentmap Geometrixx `/apps/geometrixx/components`en gebruik de afbeelding als de naam van het doelknooppunt.

   ![chlimage_1-62](assets/chlimage_1-62a.png)

1. Bewerk de metagegevens van de component:

   * jcr: **titel** instellen op `Image (Extended)`

1. Navigeer naar `/apps/geometrixx/components/image/dialog/items/image`.
1. Nieuwe eigenschap toevoegen:

   * **Naam**: `allowUpload`
   * **Type**: `String`
   * **Waarde**: `false`
   ![chlimage_1-63](assets/chlimage_1-63a.png)

1. Klik op Alles **opslaan**. De component kan worden getest.
1. Open een pagina in Geometrixx zoals Engels / Bedrijf.
1. Schakel over naar de ontwerpmodus en activeer Afbeelding (Extended).
1. Ga terug naar de bewerkingsmodus en voeg deze toe aan het alineasysteem. Op de volgende afbeeldingen ziet u de verschillen tussen de originele afbeeldingscomponent en de afbeelding die u zojuist hebt gemaakt.

   Originele afbeeldingscomponent:

   ![chlimage_1-64](assets/chlimage_1-64a.png)

   Uw nieuwe afbeeldingscomponent:

   ![chlimage_1-65](assets/chlimage_1-65a.png)

1. De component is nu gebruiksklaar.

