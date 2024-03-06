---
title: Elementaire componenten
description: Leer over de Componenten van de Stichting in Adobe Experience Manager 6.5.
exl-id: 278701f3-3f0c-45f4-90b7-c0e316a7da8a
source-git-commit: 9d497413d0ca72f22712581cf7eda1413eb8d643
workflow-type: tm+mt
source-wordcount: '6873'
ht-degree: 0%

---

# Elementaire componenten {#foundation-components}

>[!CAUTION]
>
>De meeste Componenten van de Stichting zijn nu verouderd met AEM 6.5. Zie de [releaseopmerkingen](/help/release-notes/deprecated-removed-features.md) voor nadere informatie.
>
>Adobe beveelt aan de modernere en uitbreidbare [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) in AEM projecten. Deze componenten maken deel uit van de [Wij.Handelsversie van voorbeeldinhoud](/help/sites-developing/we-retail.md) en kan ook [afzonderlijk geïnstalleerd en gebruikt voor ontwikkeling](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/get-started/using.html) door uw beheerder.
>
>U kunt de [AEM Tools Suite moderniseren](https://opensource.adobe.com/aem-modernize-tools/) om uw op componenten-Gebaseerde plaats van de Stichting aan te passen om de Componenten van de Kern te gebruiken.

De basiscomponenten zijn ontworpen voor gebruik bij het ontwerpen van inhoud voor een standaardwebpagina. Zij vormen een ondergroep van de componenten beschikbaar uit-van-de-doos voor een standaardinstallatie van AEM.

Sommige zijn onmiddellijk beschikbaar door componentenbrowser. Verschillende andere zijn ook beschikbaar door [ontwerpmodus](/help/sites-authoring/default-components-designmode.md) (als de pagina is gebaseerd op een statische sjabloon) of door [bewerken van de sjabloon](/help/sites-authoring/templates.md) (als de pagina is gebaseerd op een bewerkbare sjabloon).

Het gebruik van stichtingscomponenten wordt gesteund, maar zij zijn hoofdzakelijk verouderd en vervangen door de Componenten van de Kern die meer rekbaarheid en flexibiliteit aanbieden.

>[!NOTE]
>
>Deze sectie bespreekt slechts componenten die uit-van-de-doos in een standaard AEM installatie beschikbaar zijn.
>
>Afhankelijk van uw instantie, kunt u aangepaste componenten hebben die uitdrukkelijk voor uw vereisten worden ontwikkeld. Deze douanecomponenten kunnen zelfs de zelfde naam hebben zoals sommige hier besproken componenten.

De componenten zijn beschikbaar op de **Componenten** tabblad van het zijpaneel van de pagina-editor wanneer [pagina&#39;s bewerken](/help/sites-authoring/editing-content.md).

U kunt een component selecteren en naar de gewenste locatie op de pagina slepen. U kunt het dan uitgeven gebruikend:

* [Eigenschappen configureren](/help/sites-authoring/editing-page-properties.md)
* [Inhoud bewerken](/help/sites-authoring/editing-content.md)

* [Inhoud bewerken - Modus Volledig scherm](/help/sites-authoring/editing-content.md#edit-content-full-screen-mode)

Componenten worden gesorteerd op basis van verschillende categorieën, componentgroepen genaamd, waaronder:

* [Algemeen](#general): Bevat basiscomponenten, zoals tekst, afbeeldingen, tabellen en grafieken.
* [Kolommen](#columns): Bevat componenten die nodig zijn voor het ordenen van de lay-out van de inhoud.
* [Formulier](#formgroup): Bevat alle componenten die nodig zijn om een formulier te maken.

## Algemeen {#general}

De algemene componenten zijn de basiscomponenten die u gebruikt om inhoud te maken.

### Account-item {#account-item}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe raadt u aan de [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) in plaats daarvan.

U kunt een koppeling definiëren met een titel en beschrijving.

![chlimage_1-88](assets/chlimage_1-88.png)

### Aangepaste afbeelding {#adaptive-image}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe raadt u aan de [Component Image Core](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/image.html) in plaats daarvan.

De stichtingscomponent Adaptive Image genereert afbeeldingen die zo zijn geschaald dat ze passen in het venster waarin de webpagina wordt geopend. Om de component te gebruiken, verstrekt u een beeldmiddel of van het dossiersysteem of DAM. Wanneer de webpagina wordt geopend, downloadt de webbrowser een kopie van de afbeelding waarvan het formaat is gewijzigd, zodat deze geschikt is voor het huidige venster.

De volgende kenmerken kunnen de grootte van het venster bepalen:

* Apparaatscherm: mobiele apparaten geven meestal webpagina&#39;s weer, zodat deze zich over het hele scherm uitstrekken.
* Venstergrootte van de webbrowser: gebruikers van laptop- en desktopcomputers kunnen het formaat van vensters van webbrowsers wijzigen.

De component genereert bijvoorbeeld een kleine afbeelding wanneer de webpagina op een mobiele telefoon wordt geopend en een afbeelding van middelgrote grootte wanneer deze op een tablet wordt geopend. Op een laptop maakt en levert de component een grote afbeelding wanneer de pagina wordt geopend in een gemaximaliseerde webbrowser. Wanneer de grootte van de webbrowser wordt aangepast aan een gedeelte van het scherm, past de component zich aan door een kleinere afbeelding te leveren en wordt de weergave vernieuwd.

#### Ondersteunde afbeeldingsindelingen {#supported-image-formats}

U kunt afbeeldingsbestanden met de volgende bestandsnaamextensies gebruiken met de component Adaptive Image:

* .jpg
* .jpeg
* .png
* .gif &#42;&#42;

>[!CAUTION]
>
>Bestanden met geanimeerde GIFFEN worden niet ondersteund in AEM voor adaptieve uitvoeringen.

#### Afbeeldingsgrootten en -kwaliteit {#images-sizes-and-quality}

In de volgende tabel wordt de breedte weergegeven van de afbeelding die wordt gegenereerd voor de opgegeven breedte van de viewport. De hoogte van de gegenereerde afbeelding wordt berekend om een constante hoogte-breedteverhouding te behouden en er wordt geen witruimte weergegeven binnen de afbeeldingsrand. Uitsnijden kan worden gebruikt om witruimte te voorkomen.

Wanneer de afbeelding een JPEG-afbeelding is, kan de grootte van de viewport ook van invloed zijn op de kwaliteit van de JPEG. De volgende JPEG-eigenschappen zijn mogelijk:

* Laag (0,42)
* Normaal (0,82)
* Hoog (1,00)

| **Breedtebereik van viewport (pixels)** | **Breedte afbeelding (pixels)** | **JPEG-kwaliteit** | **Type doelapparaat** |
|---|---|---|---|
| width &lt;= 319 | 320 | laag |  |
| width = 320 | 320 | medium | Mobiele telefoon (staand) |
| 320 &lt; breedte &lt; 481 | 480 | medium | Mobiele telefoon (liggend) |
| 480 &lt; breedte &lt; 769 | 476 | hoog | Tablet (staand) |
| 768 &lt; breedte &lt; 1025 | 620 | hoog | Tablet (liggend) |
| breedte &lt;= 1025 | full (oorspronkelijke grootte) | hoog | Desktop |

#### Eigenschappen {#properties}

In het dialoogvenster kunt u eigenschappen bewerken voor uw instantie van de component Adaptieve afbeelding, die vaak worden gebruikt voor de component Image waarop deze is gebaseerd. De eigenschappen zijn beschikbaar op twee tabbladen:

* **Afbeelding**

   * **Afbeelding**
Sleep een afbeelding vanuit de zoekfunctie voor inhoud of klik om een bladervenster te openen waarin u een afbeelding kunt laden. Nadat de afbeelding is geladen, kunt u de afbeelding uitsnijden, roteren of verwijderen. Als u wilt in- of uitzoomen op de afbeelding, gebruikt u de schuifbalk onder de afbeelding (boven de knoppen OK en Annuleren)

   * **Uitsnijden**
Een gedeelte van een afbeelding uitknippen. Sleep de rand om de afbeelding uit te snijden.

   * **Roteren**
Klik herhaaldelijk op Roteren totdat de afbeelding naar wens is geroteerd.

   * **Wissen**
Verwijder de huidige afbeelding.

* **Geavanceerd**

   * **Titel**
De component Adaptive Image gebruikt deze eigenschap niet.

   * **Alt-tekst**
De alternatieve tekst die voor de afbeelding moet worden gebruikt.

   * **Koppelen naar**
De component Adaptive Image gebruikt deze eigenschap niet.

   * **Beschrijving**
De component Adaptive Image gebruikt deze eigenschap niet.

#### De component Adaptieve afbeelding uitbreiden {#extending-the-adaptive-image-component}

Voor informatie over het aanpassen van de component Adaptief beeld raadpleegt u [De component Adaptieve afbeelding](/help/sites-developing/responsive.md#using-adaptive-images).

### Carousel {#carousel}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe raadt u aan de [Carousel Core-component](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/carousel.html) in plaats daarvan.

Met de Carousel-component kunt u afbeeldingen weergeven die aan afzonderlijke pagina&#39;s zijn gekoppeld:

* één voor één
* voor een korte tijd
* in een volgorde die u opgeeft
* met een door u opgegeven tijdvertraging

Met de besturingselementen waarop u kunt klikken, kan de gebruiker de weergegeven pagina&#39;s ook in real-time doorlopen, op aanvraag. Als u de pagina selecteert die momenteel zichtbaar is, gaat u naar die pagina. Met andere woorden, de Carousel fungeert als navigatiecontrole.

#### Eigenschappen {#properties-1}

Deze eigenschappen zijn beschikbaar op twee tabbladen:

* **Carousel**
Hier geeft u op hoe de carrousel werkt:

   * Afspeelsnelheid De tijd in milliseconden voordat de volgende dia wordt weergegeven.
   * Overgangstijd De tijd in milliseconden voor de overgang tussen twee dia&#39;s.
   * Hiermee regelt u de stijl Diverse opties in een keuzemenu, bijvoorbeeld Vorige/Volgende knoppen, Linksboven geschakeld.

* **Lijst**

  Hier geeft u op hoe pagina&#39;s in uw carrousel moeten worden opgenomen:

   * **Lijst samenstellen met**
Er zijn verschillende manieren om een paginalijst samen te stellen: Onderliggende pagina&#39;s, Vaste lijst, Zoeken of Geavanceerd zoeken (allemaal hieronder beschreven).
Welke methode u ook kiest, aan de pagina&#39;s die u in de lijst opneemt, moet al een afbeelding zijn gekoppeld. Deze afbeelding wordt weergegeven in de carrousel. Als er geen afbeelding is voor een bepaalde pagina onder de Pagina-eigenschappen van die pagina, moet u een afbeelding aan de pagina koppelen voordat u begint. Als u dat niet doet, wordt in de carrousel een pagina weergegeven die meestal leeg is. Zie [Pagina-eigenschappen bewerken](/help/sites-authoring/editing-page-properties.md).
Afhankelijk van het item dat u kiest, wordt een nieuw deelvenster weergegeven:

      * **Opties voor onderliggende pagina&#39;s**

         * **Bovenliggende pagina**
Geef een pad handmatig of met de kiezer op. Laat leeg als u de huidige pagina als bovenliggend item wilt gebruiken.

      * **Opties voor vaste lijst**

         * **Pagina&#39;s**
Selecteer een lijst met pagina&#39;s. Gebruiken `+` om meer items toe te voegen en de knoppen Omhoog en Omlaag om de volgorde aan te passen.

      * **Zoekopties**

         * **Starten in**
Voer handmatig of met de kiezer een beginpad in.

         * **Zoekquery**
U kunt een zoekquery voor onbewerkte tekst invoeren.

      * **Opties voor Geavanceerd zoeken**

         * **Querybuilder prediknotatie**
U kunt een onderzoeksvraag ingaan gebruikend Querybuilder prediknotatie. U kunt bijvoorbeeld &quot;fulltext=Marketing&quot; invoeren om alle pagina&#39;s met &quot;Marketing&quot; in de inhoud weer te geven in de carrousel.
Zie [QueryBuilder-API](/help/sites-developing/querybuilder-api.md) voor een volledige bespreking van vraaguitdrukkingen en verdere voorbeelden.

   * **Volgorde van**
Selecteren `jcr:title`, `jcr:created`, `cq:lastModified`, of `cq:template` in het vervolgkeuzemenu.

   * **Limiet**
Optioneel. Het maximumaantal items dat u in de carrousel wilt gebruiken.

>[!NOTE]
>
>U kunt een aangepaste carrouselcomponent voor Adobe Experience Manager maken die digitale elementen weergeeft in de AEM DAM. Zie [Aangepaste carrouselcomponenten maken voor Adobe Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html).

### Diagram {#chart}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe raadt u aan de [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) in plaats daarvan.

Met de component Diagram kunt u een balk, lijn of cirkeldiagram toevoegen. AEM maakt een grafiek op basis van de gegevens die u opgeeft. U verstrekt gegevens door direct in het lusje van Gegevens te typen of door een spreadsheet te kopiëren en te kleven.

* **Gegevens**

   * **Grafiekgegevens**
Voer uw grafiekgegevens in met de CSV-indeling; in de indeling Door komma&#39;s gescheiden waarden worden komma&#39;s (&quot;,&quot;) gebruikt als veldscheidingsteken.

* **Geavanceerd**

   * **Type diagram**
Selecteer Schijfdiagram, Lijngrafiek en Staafdiagram.

   * **Alternatieve tekst**
Hiermee geeft u alternatieve tekst weer in plaats van het diagram.

   * **Breedte**
De breedte van het diagram in pixels.

   * **Hoogte**
De hoogte van het diagram in pixels.

In het volgende voorbeeld ziet u een voorbeeld van diagramgegevens, gevolgd door het resulterende staafdiagram:

![chlimage_1-89](assets/chlimage_1-89.png) ![dc_chart_use](assets/dc_chart_use.png)

>[!NOTE]
>
>U kunt een aangepast AEM grafiekbesturingselement maken waarmee gegevens in de AEM JCR worden weergegeven. Zie voor meer informatie [Adobe Experience Manager-gegevens in een diagram weergeven](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html).

### Inhoudsfragment {#content-fragment}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe raadt u aan de [Component Content Fragment Core](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html) in plaats daarvan.

[Inhoudsfragmenten](/help/sites-authoring/content-fragments.md) worden gemaakt en beheerd als pagina-onafhankelijke elementen. Vervolgens kunt u deze fragmenten en de variaties ervan gebruiken bij het ontwerpen van de inhoudspagina&#39;s.

### Design Importer {#design-importer}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe raadt u aan de [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) in plaats daarvan.

Met deze component kunt u een ZIP-bestand met een ontwerppakket uploaden.

### Downloaden {#download}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe raadt u aan de [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) in plaats daarvan.

De component Download maakt een koppeling op de geselecteerde webpagina om een specifiek bestand te downloaden. U kunt middelen van de Vinder van de Inhoud slepen of een dossier uploaden.

* **Downloaden**

   * **Beschrijving**
Een korte beschrijving die wordt weergegeven met de downloadkoppeling.

   * **Bestand**
Het bestand dat op de resulterende webpagina kan worden gedownload. Sleep een element van de inhoudzoeker of selecteer het gebied zodat u het bestand kunt uploaden dat u wilt downloaden.

In het volgende voorbeeld wordt de component Download getoond in Geometrixx:

![dc_download_use](assets/dc_download_use.png)

### Extern {#external}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe raadt u aan de [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) in plaats daarvan.

De externe component voor toepassingsintegratie (**Extern**) kunt u externe toepassingen met een iframe insluiten in uw AEM.

* **Extern**

   * **Doeltoepassing**
Geef de URL op van de webtoepassing die moet worden geïntegreerd, bijvoorbeeld:

     ```
     https://en.wikipedia.org/wiki/Main_Page
     ```

   * **Parameters doorgeven**
Schakel het selectievakje in als de parameters naar de toepassing moeten worden doorgegeven.

   * **Breedte en Hoogte **De grootte van het iframe definiëren

De externe toepassing is geïntegreerd in het alineasysteem van de AEM pagina, bijvoorbeeld wanneer u een doeltoepassing gebruikt van `https://en.wikipedia.org/wiki/Main_Page`:

![chlimage_1-90](assets/chlimage_1-90.png)

>[!NOTE]
>
>Afhankelijk van uw gebruiksgeval zijn er andere opties beschikbaar voor de integratie van externe toepassingen, zoals [Integratie van Portlets](/help/sites-administering/aem-as-portal.md).

### Flash {#flash}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe raadt u aan de [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) in plaats daarvan.

>[!CAUTION]
>
>Van deze component wordt niet meer verwacht om buiten-van-de-doos zonder uitgebreide project-vlakke aanpassing te functioneren.

Met de component Flash kunt u een Flash film laden. U kunt een Flash-element van de zoeker naar de component slepen of u kunt het dialoogvenster gebruiken:

* **Flash**

   * **Flash film**

     Het Flash-filmbestand. Sleep een element van de zoeker naar de inhoud of klik om een bladervenster te openen.

   * **Grootte**

     Dimensionen in pixels van het weergavegebied dat de film bevat.

* **Alternatieve afbeelding**

  Een alternatieve afbeelding die moet worden weergegeven

* **Geavanceerd**

   * **Contextmenu**

     Geeft aan of het contextmenu moet worden weergegeven of verborgen.

   * **Venstermodus**

     Hoe het venster er uitziet, bijvoorbeeld dekkend, transparant of als een duidelijk (effen) venster.

   * **Achtergrondkleur**

     Een achtergrondkleur die is geselecteerd in het kleurendiagram dat wordt weergegeven.

   * **Minimumversie**

     De minimale versie van Adobe Flash Player die is vereist om de film uit te voeren. De standaardwaarde is 9.0.0.

   * **Attributen**

     Eventuele andere vereiste kenmerken.

### Afbeelding {#image}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe raadt u aan de [Component Image Core](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/image.html) in plaats daarvan.

In de afbeeldingscomponent wordt een afbeelding en de bijbehorende tekst weergegeven volgens de opgegeven parameters.

U kunt een afbeelding uploaden, deze vervolgens bewerken en bewerken (bijvoorbeeld uitsnijden, roteren, koppeling/titel/tekst toevoegen).

U kunt een afbeelding slepen en neerzetten vanuit de [Browser voor middelen](/help/sites-authoring/author-environment-tools.md#assets-browser) rechtstreeks op de component of de component [Dialoogvenster configureren](/help/sites-authoring/editing-content.md#component-edit-dialog). U kunt een beeld van de Configure dialoog ook uploaden; dit dialoog controleert alle definities en manipulatie van het beeld:

![chlimage_1-91](assets/chlimage_1-91.png)

Nadat de afbeelding is geüpload (en niet eerder), kunt u [plaatsen, bewerken](/help/sites-authoring/editing-content.md#edit-content) om de afbeelding naar wens uit te snijden of te roteren:

![Werkbalk Verwerken](do-not-localize/chlimage_1-15.png)

>[!NOTE]
>
>De editor op locatie gebruikt de oorspronkelijke grootte en hoogte-breedteverhouding van de afbeelding tijdens het bewerken. U kunt ook de eigenschappen voor hoogte en breedte opgeven. Beperkingen voor grootte en hoogte-breedteverhouding die in de eigenschappen zijn gedefinieerd, worden toegepast wanneer u de bewerkingswijzigingen opslaat.
>
>Afhankelijk van uw geval, kunnen de minimum en maximumbeperkingen ook door [ontwerp van de pagina](/help/sites-developing/designer.md). Deze beperkingen worden ontwikkeld tijdens de uitvoering van het project.

Er zijn verschillende aanvullende opties beschikbaar in de modus Volledig scherm, bijvoorbeeld voor toewijzen en zoomen:

![Modus voor Volledig scherm bewerken - toewijzen en zoomen](do-not-localize/chlimage_1-16.png)

>[!NOTE]
>
>De voortgang van het uploaden kan niet worden gecontroleerd met Internet Explorer.
>
>Gebruikers van Internet Explorer moeten de afbeelding uploaden en op **OK** Open vervolgens de afbeelding opnieuw om het geüploade bestand in de voorvertoning weer te geven en wijzigingen uit te voeren (bijsnijden).
>
>Zie de [Gecertificeerde platforms](/help/release-notes/release-notes.md#certifiedplatforms) voor meer informatie over HTML5 functies die door AEM worden gebruikt.

Wanneer een beeld wordt geladen, kunt u het volgende vormen:

* **Kaart**

  Als u een afbeelding wilt toewijzen, selecteert u Kaart. U kunt opgeven hoe u de afbeelding met hyperlinks wilt maken (rechthoek, veelhoek enzovoort) en waar het gebied naartoe moet wijzen.

* **Uitsnijden**

  Als u een deel van een afbeelding wilt uitknippen, selecteert u Uitsnijden. Gebruik de muis om de afbeelding uit te snijden.

* **Roteren**

  Selecteer Roteren als u een afbeelding wilt roteren. Herhaal deze bewerking totdat de afbeelding op de gewenste manier is geroteerd.

* **Wissen**

  Verwijder de huidige afbeelding.

* **Titel**

  De titel van de afbeelding.

* **Alt-tekst**

  Een alternatieve tekst die kan worden gebruikt bij het maken van toegankelijke inhoud.

* **Koppelen naar**

  Maak een koppeling naar elementen of andere pagina&#39;s binnen uw website.

* **Beschrijving**

  Een beschrijving van de afbeelding.

* **Grootte**

  Hiermee stelt u de hoogte en de breedte van de afbeelding in.

>[!NOTE]
>
>Sommige opties zijn alleen beschikbaar in de volledige-schermeditor.

De uiteindelijke afbeelding (met **Titel** en **Beschrijving**) kan worden weergegeven als:

![chlimage_1-92](assets/chlimage_1-92.png)

### Layout Container {#layout-container}

Deze component verstrekt een net-paragraaf systeem om u toe te voegen en componenten binnen a te plaatsen [responsief raster](/help/sites-authoring/responsive-layout.md). U kunt verschillende inhoudslaay-outs bepalen die op de breedte van doelapparaten, met inbegrip van een waaier van telefoons, tabletten, en de Desktop worden gebaseerd.

![chlimage_1-93](assets/chlimage_1-93.png)

>[!NOTE]
>
>Deze component is geïmplementeerd met [HTML Sjabloontaal (HTL)](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html).

### Lijst {#list}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe raadt u aan de [Core-component List](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/list.html) in plaats daarvan.

Met de component List kunt u zoekcriteria configureren voor het weergeven van een lijst:

* **Lijst**

   * **Lijst samenstellen met**

     Hier geeft u op waar de lijst de inhoud ophaalt. Er zijn verschillende methoden:

   * Afhankelijk van het item dat u kiest, wordt een nieuw deelvenster weergegeven:

      * **Opties voor onderliggende pagina&#39;s**

         * **Kinderen van** (Bovenliggende pagina)

           Geef een pad handmatig of met de kiezer op. Laat leeg als u de huidige pagina als bovenliggend item wilt gebruiken.

      * **Opties voor vaste lijst**

         * **Pagina&#39;s**

           Selecteer een lijst met pagina&#39;s. Gebruik + om meer items toe te voegen en klik op de knop Omhoog/Omlaag om de volgorde aan te passen.

      * **Zoekopties**

         * Starten in

           Voer handmatig of met de kiezer een beginpad in.

         * Zoekquery

           U kunt een zoekquery voor onbewerkte tekst invoeren.

      * **Opties voor Geavanceerd zoeken**

         * **Querybuilder prediknotatie**

           U kunt een onderzoeksvraag ingaan gebruikend Querybuilder prediknotatie. U kunt bijvoorbeeld &quot;fulltext=Marketing&quot; invoeren om alle pagina&#39;s met &quot;Marketing&quot; in de inhoud weer te geven in de carrousel.

           Zie [QueryBuilder-API](/help/sites-developing/querybuilder-api.md) voor een volledige bespreking van vraaguitdrukkingen en verdere voorbeelden.

      * **Tags**

        Geef de **Bovenliggende pagina**, **Tags/trefwoorden** en de vereiste criteria.

   * **Weergeven als**

     Hoe u de punten wilt worden vermeld; omvat Verbindingen, Teasers en Nieuws.

   * **Volgorde van**

     Of de lijst moet worden besteld en, zo ja, welke criteria moeten worden gebruikt voor sorteren. U kunt criteria invoeren of een criteria selecteren in de opgegeven vervolgkeuzelijst.

   * **Limiet**

     Geef het maximumaantal items op dat u in de lijst wilt weergeven.

   * **Feed inschakelen**

     Geeft aan of een RSS-feed voor de lijst moet worden geactiveerd.

   * **Pagineren na**

     Hier kunt u het aantal lijstitems opgeven dat in één keer moet worden weergegeven. Een lijst met meer items dan opgegeven gebruikt paginering om de lijst in verschillende delen weer te geven.

In het volgende voorbeeld wordt een **Lijst** de manier waarop een lijst met onderliggende pagina&#39;s wordt weergegeven (het ontwerp wordt bepaald door de aangepaste CSS-definities van een siteontwerp).

![dc_list_use](assets/dc_list_use.png)

### Aanmelden {#login}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe raadt u aan de [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) in plaats daarvan.

>[!CAUTION]
>
>Van deze component wordt niet meer verwacht om buiten-van-de-doos zonder uitgebreide project-vlakke aanpassing te functioneren.

Hiermee worden de velden Gebruikersnaam en Wachtwoord weergegeven.

![chlimage_1-94](assets/chlimage_1-94.png)

U kunt configureren:

* Aanmelden

   * Sectielabel

     Invultekst voor de invoervelden.

   * Label voor gebruikersnaam

     Tekst die een label moet geven aan het veld gebruikersnaam.

   * Wachtwoordlabel

     Tekst om het wachtwoordveld een label te geven.

   * Label van de knop Aanmelden

     Tekst voor de aanmeldknop.

   * Omleiden naar

     U kunt de pagina op uw website opgeven die moet worden geopend nadat de gebruiker zich heeft aangemeld.

* Al aangemeld

   * Doorgaan, knoplabel

     Tekst die aangeeft dat de gebruiker al is aangemeld.

### Status van bestelling {#order-status}

>[!CAUTION]
>
>Van deze component wordt niet meer verwacht om buiten-van-de-doos zonder uitgebreide project-vlakke aanpassing te functioneren.

* **Titel**

   * **Titel**

     Geef de titeltekst op die u wilt weergeven.

   * **Koppeling**

     Geef de pagina (het product) op waarvoor de status van de bestelling moet worden weergegeven.

   * **Type/Grootte**

     Maak een keuze uit de beschikbare selectie.

![chlimage_1-95](assets/chlimage_1-95.png)

### Referentie {#reference}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe raadt u aan de [Component Content Fragment Core](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html) in plaats daarvan.

De **Referentie** kunt u tekst van een andere pagina van uw AEM website (in de huidige instantie) gebruiken. De inhoud van de alinea waarnaar wordt verwezen, wordt weergegeven alsof deze zich op de huidige pagina bevindt. De inhoud wordt bijgewerkt wanneer de bronalinea verandert (mogelijk moet de pagina worden vernieuwd).

* **Alineaslaggids**

   * **Referentie**

     Geef het pad op naar de pagina en alinea waarnaar u wilt verwijzen (inhoud opnemen).

Als u het pad naar een alinea wilt opgeven, moet u het pad (op de pagina) achtervoegsel geven met:

`.../jcr:content/par/<paragraph-ID>`

Bijvoorbeeld:

`/content/geometrixx-outdoors/en/equipment/biking/cajamara/jcr:content/par/similar-products`

Naast het verwijzen naar een specifieke alinea, kan het pad ook worden gewijzigd om een volledig pari-systeem te specificeren. U kunt dit door het pad als volgt te wijzigen:

`/jcr:content/par`

Bijvoorbeeld:

`/content/geometrixx-outdoors/en/equipment/biking/cajamara/jcr:content/par`

Na de configuratie wordt de inhoud precies zo weergegeven als op de bronpagina. Het feit dat dit een verwijzing is, wordt alleen weergegeven wanneer u de component opent voor bewerking:

![chlimage_1-96](assets/chlimage_1-96.png)

### Zoeken {#searching}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe raadt u aan de [Core-component Snel zoeken](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/quick-search.html) in plaats daarvan.

De component van het Onderzoek voegt onderzoeksmogelijkheden aan uw pagina toe.

U kunt configureren:

* Zoeken

   * **Knooppunttypen**

     Als de zoekopdracht moet worden beperkt tot een bepaald knooppunttype, geeft u hier een lijst van knooppunten op, bijvoorbeeld `cq:Page`.

   * **Pad om in te zoeken**

     Geef de basispagina op van de vertakking die u wilt doorzoeken.

   * **Tekst van knop Zoeken**

     De naam die wordt weergegeven op de werkelijke zoekknop.

   * **Statistische tekst**

     De tekst die boven de zoekresultaten wordt weergegeven.

   * **Geen resultaattekst**

     Als er geen resultaten zijn, wordt de hier ingevoerde tekst weergegeven.

   * **Spellcheck-tekst**

     Als iemand een gelijkaardige termijn ingaat, wordt deze tekst getoond vóór de termijn.
Als u bijvoorbeeld `Geometrixxe`, geeft het systeem &quot;Bedoelde u? Geometrixx&quot;.

   * **Tekst op vergelijkbare pagina&#39;s**

     De tekst die wordt weergegeven naast een resultaat voor vergelijkbare pagina&#39;s. Klik op deze koppeling om pagina&#39;s met vergelijkbare inhoud weer te geven.

   * **Tekst verwante zoekopdrachten**

     De tekst die naast onderzoeken naar verwante termijnen en onderwerpen verschijnt.

   * **Tekst voor trends zoeken**

     De titel boven de zoektermen die een gebruiker invoert.

   * **Label voor resultaatpagina&#39;s**

     De tekst die onder aan deze lijst wordt weergegeven met koppelingen naar andere resultatenpagina&#39;s.

   * **Vorige label**

     De naam die wordt weergegeven op de koppeling naar vorige zoekpagina&#39;s.

   * **Volgende label**

     De naam die wordt weergegeven op de koppeling naar volgende zoekpagina&#39;s.

In het volgende voorbeeld wordt de component Zoeken weergegeven na een zoekopdracht naar het woord *`geometrixx`* in de hoofdmap van een standaardinstallatie. Ook wordt de paginering van de resultaten geïllustreerd:

![dc_search_use](assets/dc_search_use.png)

In het volgende voorbeeld wordt een zoekterm getoond die verkeerd is gespeld en niet beschikbaar is:

![dc_search_usenotfound](assets/dc_search_usenotfound.png)

### Sitemap {#sitemap}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe raadt u aan de [Navigatie](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/navigation.html), [Taalnavigatie](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/language-navigation.html), en [Breadcrumb Core-componenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/breadcrumb.html) in plaats daarvan.

Een automatische sitemapvermelding die (met de standaardinstellingen) alle pagina&#39;s (als actieve koppelingen) op de huidige website weergeeft. Een extract toont bijvoorbeeld:

![dc_sitemap_use](assets/dc_sitemap_use.png)

Indien nodig, kunt u het volgende vormen:

* **Sitemap**

   * **Hoofdpad**

     Pad vanaf waar de aanbieding moet beginnen.

### Presentatie {#slideshow}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe raadt u aan de [Carousel Core-component](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/carousel.html) in plaats daarvan.

>[!CAUTION]
>
>Van deze component wordt niet meer verwacht om buiten-van-de-doos zonder uitgebreide project-vlakke aanpassing te functioneren.

Met deze component kunt u een reeks afbeeldingen laden die als een diapresentatie op de pagina worden weergegeven. U kunt afbeeldingen toevoegen of verwijderen en elke titel toewijzen. Onder Geavanceerd kunt u ook de grootte van het weergavegebied opgeven.

U kunt configureren:

* **Dia&#39;s**

   * **Nieuwe dia**

     U kunt een selectie dia&#39;s opgeven met de opdracht **Toevoegen** (en **Verwijderen**).

   * **Titel**

     Geef indien nodig een titel op. De titel staat op de juiste dia.

* **Geavanceerd**

   * **Grootte**

     Geef de breedte en hoogte op in pixels.

In de diapresentatie-component worden vervolgens herhaaldelijk alle elementen in de juiste volgorde weergegeven, gedurende een korte tijd, voordat de volgende dia wordt afgevlakt:

![dc_slideshow_use](assets/dc_slideshow_use.png)

### Tabel {#table}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe raadt u aan de [Tekstkerncomponent](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/text.html) in plaats daarvan.

>[!NOTE]
>
>De **Tabel** De component van de stichting is gebaseerd op [Rich Text Editor](/help/sites-authoring/rich-text-editor.md), evenals de **[Tekst](#text)** Foundation-component.

De **Tabel** wordt vooraf gevormd om u te laten een lijst construeren, vullen en formatteren. Met behulp van het dialoogvenster kunt u uw tabel configureren en de inhoud maken door:

* krassen
* het kopiëren van en het kleven van een spreadsheet of een lijst van een externe redacteur (zoals Excel, OpenOffice, en Blocnote).

Met de inline editor kunt u basiswijzigingen in de inhoud aanbrengen:

![dc_table](assets/dc_table.png)

In de modus Volledig scherm kunt u de tabellay-out configureren:

![chlimage_1-97](assets/chlimage_1-97.png)

In de volgende schermafbeelding ziet u een voorbeeld van de tabelcomponent. Het ontwerp wordt bepaald door de sitespecifieke CSS:

![dc_table_use](assets/dc_table_use.png)

### Cloud labelen {#tag-cloud}

Een tagcloud geeft een grafisch weergegeven selectie van de tags die zijn toegepast op de inhoud van uw website:

![dc_tagclouduse](assets/dc_tagclouduse.png)

Wanneer u de component Tag Cloud configureert, kunt u het volgende opgeven:

* **Weer te geven labels**

  Waar de weer te geven tags worden verzameld. Selecteer op een pagina een pagina met alle onderliggende codes of alle codes.

* **Pagina**

  Selecteer de pagina waarnaar moet worden verwezen.

* **Geen koppelingen op tags**

  Of de weergegeven tags moeten fungeren als koppelingen.

Ga voor meer informatie over het toepassen van tags naar [Tags gebruiken](/help/sites-authoring/tags.md).

### Tekst {#text}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe raadt u aan de [Tekstkerncomponent](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/text.html) in plaats daarvan.

>[!NOTE]
>
>De **Tekst** De component van de stichting is gebaseerd op [Rich Text Editor](/help/sites-authoring/rich-text-editor.md), evenals de **Tabel** Foundation-component.

De component van de Tekst laat u een tekstblok ingaan gebruikend een redacteur WYSIWYG, met functionaliteit die door wordt verstrekt [Rich Text Editor](/help/sites-authoring/rich-text-editor.md). Met een selectie pictogrammen kunt u de tekst opmaken, inclusief lettertypekenmerken, uitlijning, koppelingen, lijsten en inspringing.

![chlimage_1-98](assets/chlimage_1-98.png)

Wanneer u het dialoogvenster **Configureren** kunt u ook instellen:

* **Spacer**
* **Tekststijl**

De opgemaakte tekst wordt weergegeven op de pagina. Het daadwerkelijke ontwerp is afhankelijk van de site-CSS:

![dc_text_use](assets/dc_text_use.png)

Voor meer gedetailleerde informatie over de component van de Tekst en de functionaliteit die door de redacteur van de Tekst Rich wordt verstrekt, zie [RTF-editor](/help/sites-authoring/rich-text-editor.md) pagina.

#### Op plaats bewerken {#inplace-editing}

Naast de op een dialoogvenster gebaseerde Rich Text-bewerkingsmodus biedt AEM ook [Op plaats bewerken](/help/sites-authoring/editing-content.md), zodat de tekst direct kan worden bewerkt zoals deze wordt weergegeven in de layout van de pagina.

### Tekst en afbeelding {#text-image}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe raadt u aan de [Afbeelding](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/image.html) en [Tekstkerncomponent](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/text.html) in plaats daarvan.

De component Tekst en afbeelding voegt een tekstblok en een afbeelding toe. U kunt ook afzonderlijk tekst en afbeeldingen toevoegen en bewerken. Zie de [Tekst](#text) en [Afbeelding](#image) voor meer informatie.

![chlimage_1-99](assets/chlimage_1-99.png)

U kunt configureren:

* **Componentstijlen** (**Stijlen**)

  Hier kunt u de afbeelding links of rechts uitlijnen. De standaardwaarde is **Links** uitgelijnd, met de afbeelding aan de linkerkant.

* **Eigenschappen van afbeelding** (**Geavanceerde afbeeldingseigenschappen**)

  Hier kunt u het volgende opgeven:

   * **Afbeeldingselement**

     Upload de vereiste afbeelding.

   * **Titel**

     De titel voor het blok, weergegeven door mouseover.

   * **Alt-tekst**

     Alternatieve tekst die moet worden weergegeven als de afbeelding niet kan worden weergegeven. Als de titel leeg blijft, wordt deze gebruikt.

   * **Koppeling naar**

     Geef een doelpad op.

   * **Beschrijving**

     Een beschrijving van de afbeelding.

   * **Grootte**

     Hiermee stelt u de hoogte en breedte van de afbeelding in.

In het volgende voorbeeld ziet u een component Tekstafbeelding waarmee de afbeelding links wordt uitgelijnd:

![dc_tile_use](assets/dc_textimage_use.png)

### Titel {#title}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe raadt u aan de [Component Title Core](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/list.html) in plaats daarvan.

De component title kan:

* Geef de naam van de huidige pagina weer door het veld Titel leeg te laten.
* Geef een tekst weer die u opgeeft in het veld Titel.

U kunt configureren:

* **Titel**

  Als u een andere naam dan de paginatitel wilt gebruiken, voert u deze hier in.

* **Koppeling**

  De URI als de titel moet werken als een koppeling.

* **Type/Grootte**

  Selecteer Klein of Groot in de vervolgkeuzelijst. Klein wordt gegenereerd als een afbeelding. Groot wordt gegenereerd als tekst.

In het volgende voorbeeld wordt een **Titel** -component die wordt weergegeven; het ontwerp wordt bepaald door de sitespecifieke CSS.

![dc_title_use](assets/dc_title_use.png)

### Video {#video}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe raadt u aan de [Core Components Embed Component](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/embed.html) in plaats daarvan.

>[!CAUTION]
>
>Van deze component wordt niet meer verwacht om buiten-van-de-doos zonder uitgebreide project-vlakke aanpassing te functioneren.

De **Video** kunt u een vooraf gedefinieerd, out-of-the-box video-element op een pagina plaatsen.

Zie ook [Uw videoprofielen configureren](/help/sites-administering/config-video.md#configuringvideoprofiles) voor gebruik met HTML5-elementen.

Nadat u een instantie van de component op de pagina hebt geplaatst, kunt u het volgende configureren:

* Video

   * **Video-element**

     Upload of zet uw video-element neer.

   * **Grootte**

     De native grootte van de video (breedte x hoogte in pixels) wordt weergegeven in de vakken naast Grootte (zie boven). Voer hier handmatig de afmetingen voor breedte en hoogte in als u de native afmetingen van de video wilt overschrijven. Selecteren **OK** Hiermee wordt het dialoogvenster gesloten.

>[!NOTE]
>
>Ondersteunde indelingen zijn onder andere:
>
>* `.mp4`
>* `Ogg`
>* `FLV` (video Flash)

## Kolommen {#columns}

Kolommen zijn een mechanisme om de lay-out van inhoud in AEM te bepalen. In een standaardinstallatie, worden de componenten voor het creëren van twee of drie kolommen verstrekt.

In het volgende voorbeeld ziet u de twee gebruikte componenten Kolommen. U kunt de plaatsaanduidingen voor nieuwe componenten gebruiken:

![dc_columncontroluse](assets/dc_columncontroluse.png)

### 2 kolommen {#columns-1}

Een component van de Controle van de Kolom die aan twee gelijke kolommen standaard.

### 3 kolommen {#columns-2}

Een component van de Controle van de Kolom die aan drie gelijke kolommen standaard.

### Kolombesturingselement {#column-control}

Met de component Kolombeheer kunnen gebruikers selecteren hoe ze de inhoud in het hoofdvenster van de webpagina in meerdere kolommen willen splitsen. Gebruikers kunnen het aantal vereiste kolommen selecteren (uit een vooraf gedefinieerde lijst) en vervolgens inhoud maken, verwijderen of verplaatsen binnen elk van de kolommen.

* **Kolombesturingselement**

   * **Kolomlay-out**

     Selecteer het aantal kolommen dat u wilt renderen. Nadat elke kolom is gemaakt, bevat deze een eigen koppeling voor het slepen van componenten of elementen tijdens het toevoegen van inhoud.

## Formulier {#form}

>[!CAUTION]
>
>De Foundation-component is afgekeurd. Adobe raadt u aan de [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) in plaats daarvan.

Formuliercomponenten worden gebruikt om formulieren te maken waarmee bezoekers invoer kunnen verzenden. Forms en formuliercomponenten kunnen worden gebruikt om informatie te verzamelen, waaronder gebruikersfeedback (bijvoorbeeld een vragenlijst voor klanttevredenheid) en gebruikersgegevens (bijvoorbeeld gebruikersregistratie).

>[!NOTE]
>
>Zie [AEM Forms Help](/help/forms/using/introduction-aem-forms.md) voor informatie over AEM Forms.

Forms is opgebouwd uit verschillende onderdelen:

* **Formulier**

  De formuliercomponent definieert het begin en einde van een nieuw formulier op een pagina. Andere componenten kunnen vervolgens tussen deze elementen worden geplaatst, zoals tabellen, en worden gedownload.

* **Formuliervelden en -elementen**

  Formuliervelden en -elementen kunnen tekstvakken, keuzerondjes en afbeeldingen bevatten. De gebruiker voert vaak een handeling uit in een formulierveld, zoals het typen van tekst. Zie de afzonderlijke formulierelementen voor meer informatie.

* **Profielcomponenten**

  Profielcomponenten hebben betrekking op bezoekersprofielen die worden gebruikt voor sociale samenwerking en andere gebieden waar personalisatie van bezoekers vereist is.

Hieronder ziet u een voorbeeldformulier. Het bestaat uit de **Formulier** component (begin en eind), met twee **Formulier** **Tekst** velden die worden gebruikt voor invoer, a **Algemeen** **Tekst** voor de tekst van de lead-in en een **Verzenden** knop.

![dc_form](assets/dc_form.png)

>[!NOTE]
>
>Informatie over het ontwikkelen en aanpassen van uw formulieren is beschikbaar op het tabblad [Forms-pagina ontwikkelen](/help/sites-developing/developing-forms.md). Deze mogelijkheid omvat onder andere het toevoegen van handelingen, beperkingen, het vooraf laden van velden en het gebruik van scripts om een service aan een actie aan te roepen.

### Algemene instellingen voor (veel) formuliercomponenten {#settings-common-to-many-form-components}

Hoewel elk van de formuliercomponenten een ander doel heeft, bestaan veel van deze componenten uit vergelijkbare opties en parameters.

Wanneer u een van de formuliercomponenten configureert, zijn de volgende tabbladen beschikbaar in het dialoogvenster:

* **Titel en tekst**

  Hier moet u de basisinformatie opgeven, zoals de titel van het formulier en eventuele begeleidende tekst. U kunt zo nodig ook andere belangrijke informatie definiëren, zoals of het veld meerdere selecties kan bevatten en of items kunnen worden geselecteerd.

* **Beginwaarden**

  Hier geeft u een standaardwaarde op.

* **Restricties**

  Hier kunt u opgeven of een veld verplicht is en beperkingen in dat veld instellen (moet bijvoorbeeld een numeriek veld zijn).

* **Stijlen**

  Hiermee geeft u de grootte en opmaak van de velden aan.

>[!NOTE]
>
>De velden die u ziet, variëren aanzienlijk, afhankelijk van de afzonderlijke component.

Deze lusjes voorzien u van de noodzakelijke parameters. De tabbladen kunnen afhankelijk zijn van het afzonderlijke componenttype, maar kunnen het volgende bevatten:

* **Titel en tekst**

   * **Elementnaam**

     Naam van het formulierelement. Het geeft aan waar in de gegevensopslagruimte de gegevens worden opgeslagen.
Dit veld is verplicht en mag alleen de volgende tekens bevatten:

      * alfanumerieke tekens
      * `_ . / : -`

   * **Titel**

     De titel die bij het veld wordt weergegeven. Indien leeg gelaten, wordt de standaardtitel getoond.

   * **Beschrijving**

     Hiermee kunt u, indien nodig, aanvullende informatie voor de gebruiker opgeven. In het formulier wordt het weergegeven onder het veld, in een kleiner lettertype dan de titel.

   * **Tonen/verbergen**

     Hiermee bepaalt u wanneer het veld zichtbaar is.

* **Beginwaarden**

   * **Standaardwaarde**

     De waarde die in het veld wordt weergegeven wanneer het formulier wordt geopend. Dat wil zeggen, voordat de gebruiker invoer heeft ingevoerd.

* **Restricties**

   * **Vereist**

     Restricties zijn afhankelijk van het type formuliercomponent, maar beschikken over een of meer klikvakken om aan te geven dat dit veld is vereist, of dat bepaalde delen van dit veld zijn vereist.

   * **Vereist bericht**

     Een bericht om gebruikers te laten weten dat dit veld is vereist. Een vereist veld is ook gemarkeerd met een sterretje.

   * **Restrictie**

     Welke beperkingen beschikbaar zijn voor de selectie, is afhankelijk van het type formuliercomponent.

   * **Restrictiebericht**

     Een bericht om gebruikers te informeren wat wordt vereist.

* **Stijlen**

   * **Grootte**

     In rijen en kolommen.

   * **Breedte**

     In pixels.

   * **CSS**

### Formulier (component) {#form-component}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe raadt u aan de [Core-component van formuliercontainer](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/forms/form-container.html) in plaats daarvan.

De component Form definieert zowel het begin als het einde van een formulier met behulp van de **Begin formulier** en **Einde formulier** elementen. Het begin en einde worden altijd aan elkaar gekoppeld om ervoor te zorgen dat het formulier correct is gedefinieerd.

![dc_form-1](assets/dc_form-1.png)

Tussen het begin en het einde van een formulier kunt u formuliercomponenten toevoegen die de daadwerkelijke invoervelden voor gebruikers definiëren.

>[!NOTE]
>
>De stichtingscomponenten vormen component slechts steunt het gebruik van andere stichtingscomponenten vormcomponenten (knoop, tekst, verborgen, etc.). Gebruiken [kerncomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) formuliercomponenten in een formulier met funderingscomponenten (en omgekeerd) worden niet ondersteund.

#### Begin van formulier {#start-of-form}

Deze component definieert het begin van een nieuw formulier op een pagina. U kunt configureren:

* **Formulier**

   * **Dankbriefje**

     De pagina waarnaar wordt verwezen om bezoekers te bedanken voor hun invoer. Als het formulier leeg blijft, wordt het na verzending opnieuw weergegeven.

   * **Workflow starten**

     Hiermee bepaalt u welke workflow wordt geactiveerd wanneer een formulier wordt verzonden.

* **Geavanceerd**

   * **Type handeling**

     Een formulier heeft een handeling nodig. De handeling definieert de bewerking die wordt geactiveerd voor uitvoering met de gegevens die door de gebruiker worden verzonden (vergelijkbaar met action= in HTML). Sommigen hebben een overeenkomstige **Configuratie van handelingen**.
Een selectie van actietypen is inbegrepen in een standaard AEM installatie:

      * **Account-verzoek**
      * **Inhoud maken**
      * **Lead maken**
      * **Account maken en bijwerken**
      * **E-mailservice: abonnee maken en toevoegen aan lijst**
      * **E-mailservice: e-mail met automatische beantwoorder verzenden**
      * **E-mailservice: abonnement van gebruiker opzeggen**
      * **Community bewerken**
      * **Bronnen bewerken**
      * **Workflowgestuurde bronnen bewerken**
      * **Mail**
      * **Details geplaatste bestelling**
      * **Profiel bijwerken**
      * **Wachtwoord opnieuw instellen**
      * **Wachtwoord instellen**
      * **Winkelinhoud**

        Het standaardhandelingstype.

      * **Inhoud opslaan met uploads**
      * **Bestelling verzenden**
      * **Abonnement opzeggen**
      * **Volgorde bijwerken**

   * **Formulierid**

     De formulier-id vormt een unieke identificatie van het formulier. Gebruik de formulier-id als u meerdere formulieren op één pagina hebt. Zorg ervoor dat deze verschillende id&#39;s hebben.

   * **Pad laden**

     Het pad naar knooppunteigenschappen dat wordt gebruikt om vooraf gedefinieerde waarden in de formuliervelden te laden.

     Een optioneel veld dat het pad naar een knooppunt in de repository aangeeft. Als dit knooppunt eigenschappen heeft die overeenkomen met de veldnamen, worden de desbetreffende velden op het formulier vooraf geladen met de waarde van die eigenschappen. Als er geen overeenkomst bestaat, bevat het veld de standaardwaarde.

     Gebruiken **Pad laden** U kunt het formulier vooraf laden met waarden in de vereiste velden. Zie [Formulierwaarden vooraf laden](/help/sites-developing/developing-forms.md#preloading-form-values).

   * **Clientvalidatie**

     Hiermee wordt aangegeven of clientvalidatie is vereist voor dit formulier (servervalidatie) *altijd* voorkomt). Clientvalidatie kan worden bereikt met de **Forms Captcha** component.

   * **Brontype voor validatie**

     Hiermee definieert u het type resource voor formuliervalidatie als u het volledige formulier wilt valideren (in plaats van afzonderlijke velden). Als u het volledige formulier valideert, voert u ook een van de volgende handelingen uit:

      * Een script voor clientvalidatie:

        `/apps/<*myApp*>/form/<*myValidation*>/formclientvalidation.jsp`

      * Een script voor validatie aan de serverzijde:

        `/apps/<*myApp*>/form/<*myValidation*>/formservervalidation.jsp`

   * **Configuratie van handelingen**

     De opties die beschikbaar zijn in **Configuratie van handelingen** afhankelijk zijn van de geselecteerde **Type handeling**:

      * **Account-verzoek**

         * **Accountpagina maken**

           De pagina die wordt gebruikt bij het maken van een account.

      * **Inhoud maken**

         * Inhoudspad

           Het inhoudspad voor alle inhoud die door het formulier wordt neergezet. Een pad invoeren dat eindigt met een schuine streep `/`. De slash betekent dat voor elke formulierpoort een nieuw knooppunt wordt gemaakt op de opgegeven locatie, bijvoorbeeld:

           `/forms/feedback/`

         * **Type**

           Selecteer het gewenste type.

         * **Formulier**

           Geef het formulier op.

         * **Renderen met**

           Selecteer de gewenste optie in de lijst.

         * **Resourcetype**

           Indien ingesteld, wordt deze aan elke opmerking toegevoegd als `sling:resourceType`

         * **Kiezer weergeven**

      * **Lead maken**

         * **Lood wordt toegevoegd aan deze lijst**

           Geef de lijst met vereiste leads op.

      * **Account maken en bijwerken**

         * **Eerste groep**

           Groep waaraan nieuwe gebruiker moet worden toegewezen.

         * **Home**

           Pagina die moet worden weergegeven na geslaagde aanmelding.

         * **Pad**

           Het pad (relatief) naar waar de nieuwe account wordt gemaakt en opgeslagen.

         * **Gegevens weergeven...**

           Als u deze knop selecteert, wordt de informatie over de formulierresultaten weergegeven in de Bulk-editor. Van hieruit kunt u de gegevens exporteren naar een `.tsv` (tabgescheiden) bestand (bijvoorbeeld in een Excel-spreadsheet).

      * **Mail**

         * **Van**

           Voer het e-mailadres in waaruit het e-mailadres moet komen.

         * **Mailto**

           Voer een of meer e-mailadressen in waarnaar het formulier wordt verzonden.

         * **CC**

           Voer een of meer CC-e-mailadressen in.

         * **BCC**

           Voer een of meer BCC-e-mailadressen in.

         * **Onderwerp**

           Voer een onderwerp voor de e-mail in.

      * **Wachtwoord opnieuw instellen**

         * **Wachtwoordpagina wijzigen**

           De pagina die wordt gebruikt bij het wijzigen van het wachtwoord.

      * **Winkelinhoud**

         * **Inhoudspad**

           Het inhoudspad voor alle inhoud die door het formulier wordt neergezet. Een pad invoeren dat eindigt met een schuine streep `/`. De slash betekent dat voor elke formulierpoort een nieuw knooppunt wordt gemaakt op de opgegeven locatie, bijvoorbeeld:
           `/forms/feedback/`

         * **Gegevens weergeven...**

           Klik op deze knop om de informatie over de formulierresultaten te bekijken in de Bulk-editor. Van hieruit kunt u de informatie exporteren naar een .tsv-bestand (gescheiden door tabs) (bijvoorbeeld voor gebruik in een Excel-spreadsheet).

      * **Inhoud opslaan met uploads**

        Heeft dezelfde opties als **Winkelinhoud**.

      * **Abonnement opzeggen**

         * **Lood wordt uit deze lijst verwijderd**

           Geef de lijst met vereiste leads op.

#### Einde van formulier {#end-of-form}

Hiermee markeert u het einde van het formulier. U kunt het volgende configureren:

* **Einde formulier**

   * **Verzendknop tonen**

     Geeft aan of een knop Verzenden moet worden weergegeven.

   * **Naam verzenden**

     Een id als u meerdere verzendknoppen in een formulier gebruikt.

   * **Titel verzenden**

     De naam die op de knop wordt weergegeven, zoals Verzenden of Verzenden.

   * **Knop Herstellen tonen**

     Als u het selectievakje inschakelt, wordt de knop Herstellen zichtbaar.

   * **Titel opnieuw instellen**

     De naam die wordt weergegeven op de knop Herstellen.

   * **Beschrijving**

     Informatie die onder de knop wordt weergegeven.

### Accountnaam {#account-name}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe raadt u aan de [Component Form Text Core](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/forms/form-text.html) in plaats daarvan.

Hiermee kan de gebruiker een accountnaam invoeren:

![dc_form_accountnaam](assets/dc_form_accountname.png)

### Adres {#address}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe raadt u aan de [Component Form Text Core](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/forms/form-text.html) in plaats daarvan.

Hiermee kunt u een internationaal adresveld met de volgende notatie toevoegen:

![dc_form_addressfield](assets/dc_form_addressfield.png)

De component wordt gevormd voor onmiddellijk gebruik, maar u kunt de configuratie veranderen, indien nodig. Bijvoorbeeld, kunnen de beperkingen voor de individuele elementen van het adres worden toegevoegd. Als u velden leeg laat, worden de standaardinstellingen gebruikt.

### Captcha {#captcha}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe raadt u aan de [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) in plaats daarvan.

>[!CAUTION]
>
>Van deze component wordt niet meer verwacht om buiten-van-de-doos zonder uitgebreide project-vlakke aanpassing te functioneren.

De component Captcha vereist dat de gebruiker een alfanumerieke tekenreeks typt zoals deze op het scherm wordt weergegeven. De tekenreeks verandert bij elke vernieuwing.

![dc_form_captcha](assets/dc_form_captcha.png)

U kunt diverse parameters voor deze component vormen, met inbegrip van een bericht dat moet worden getoond wanneer het koord captcha ongeldig is.

### Groep selectievakjes {#checkbox-group}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe raadt u aan de [Formulieropties Core-component](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/forms/form-options.html) in plaats daarvan.

Met een selectievakje kunt u een lijst maken van een of meer selectievakjes, waarvan er meerdere tegelijk kunnen worden geselecteerd.

![dc_form_checkboxgroupuse](assets/dc_form_checkboxgroupuse.png)

U kunt verschillende parameters opgeven, zoals een titel, beschrijving en elementnaam. Met de knoppen + en - kunt u items toevoegen of verwijderen en deze vervolgens met de pijl-omhoog en -omlaag plaatsen.

>[!NOTE]
>
>Gebruiken **Pad items laden** u kunt de lijst met groepen selectievakjes vooraf laden met waarden.
>
>Zie [Formuliervelden met meerdere waarden vooraf laden](/help/sites-developing/developing-forms.md#preloading-form-fields-with-multiple-values).

### Creditcardgegevens {#credit-card-details}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe raadt u aan de [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) in plaats daarvan.

Hier geeft u de velden op die nodig zijn voor het invoeren van creditcardgegevens. U kunt het vormen om de types van toegelaten kaart en de vereiste informatie (bijvoorbeeld, veiligheidscode) te specificeren.

![chlimage_1-100](assets/chlimage_1-100.png)

### Vervolgkeuzelijst {#dropdown-list}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe raadt u aan de [Formulieropties Core-component](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/forms/form-options.html) in plaats daarvan.

Een vervolgkeuzelijst kan worden geconfigureerd om een reeks waarden voor selectie aan uw gebruik te bieden:

![dc_form_dropdownlistuse](assets/dc_form_dropdownlistuse.png)

U kunt een titel en items opgeven die in de lijst moeten worden weergegeven. Met de knoppen + en - kunt u de lijstitems toevoegen of verwijderen en deze vervolgens plaatsen met de knoppen Omhoog en Omlaag. U kunt opgeven of gebruikers meerdere items in de lijst mogen selecteren en items die automatisch moeten worden geselecteerd wanneer ze de lijst voor de eerste keer openen (oorspronkelijke waarden).

>[!NOTE]
>
>Gebruiken **Pad items laden** u kunt de vervolgkeuzelijst vooraf laden met waarden.
>
>Zie [Formuliervelden met meerdere waarden vooraf laden](/help/sites-developing/developing-forms.md#preloading-form-fields-with-multiple-values).

### Bestand uploaden {#file-upload}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe raadt u aan de [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) in plaats daarvan.

De component voor het uploaden van bestanden biedt de gebruiker een mechanisme voor het selecteren en uploaden van een bestand.

![dc_form_fileupload](assets/dc_form_fileupload.png)

>[!NOTE]
>
>U kunt een aangepaste uploadcomponent maken om bestanden te uploaden naar een verkoopserver. Zie voor meer informatie [Bestanden uploaden naar Adobe Experience Manager](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/aem-cloud-service-create-asset-servlet-for-uploading-small-files/td-p/404276).

### Verborgen veld {#hidden-field}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe raadt u aan de [Verborgen kerncomponent van formulier](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/forms/form-hidden.html) in plaats daarvan.

Hiermee kunt u een verborgen veld maken. Deze verborgen velden kunnen voor verschillende doeleinden worden gebruikt. Bijvoorbeeld wanneer u een actie moet uitvoeren nadat u het formulier hebt verzonden of wanneer verborgen gegevens vereist zijn tijdens de naverwerking.

![dc_form_hiddenfield](assets/dc_form_hiddenfield.png)

>[!NOTE]
>
>U kunt het formulier ook aanpassen om specifieke formuliercomponenten weer te geven of te verbergen op basis van de waarde van andere velden in het formulier. Het is handig de zichtbaarheid van een formulierveld te wijzigen als het veld alleen onder bepaalde omstandigheden nodig is.
>
>Zie [Formuliercomponenten weergeven en verbergen](/help/sites-developing/developing-forms.md#showing-and-hiding-form-components).

### Afbeeldingsknop {#image-button}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe raadt u aan de [Kern van knop Formulier](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/forms/form-button.html) in plaats daarvan.

Met een afbeeldingsknop kunt u een knop maken met uw eigen afbeelding en tekst:

![dc_form_imagebutton](assets/dc_form_imagebutton.png)

### Afbeelding uploaden {#image-upload}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe raadt u aan de [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) in plaats daarvan.

De component voor het uploaden van afbeeldingen biedt de gebruiker een mechanisme voor het selecteren en uploaden van een afbeeldingsbestand.

![dc_form_imageupload](assets/dc_form_imageupload.png)

### Koppelingsveld {#link-field}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe raadt u aan de [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) in plaats daarvan.

In het koppelingsveld kan de gebruiker een URL opgeven:

![dc_form_link](assets/dc_form_link.png)

Wordt meestal gebruikt voor het agendagebeurtenis, waar dit wordt gebruikt voor het URL-/koppelingsveld van een gebeurtenis.

### Wachtwoordveld {#password-field}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe raadt u aan de [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) in plaats daarvan.

Hiermee kan de gebruiker zijn wachtwoord invoeren:

![dc_form_password](assets/dc_form_password.png)

### Wachtwoord opnieuw instellen {#password-reset}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe raadt u aan de [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) in plaats daarvan.

Deze component voorziet uw gebruiker van twee gebieden voor:

* de invoer van een wachtwoord
* herhaalde invoer van het wachtwoord om te controleren of de invoer juist is.

Bij de standaardinstellingen wordt de component als volgt weergegeven:

![dc_password_reset](assets/dc_password_reset.png)

### Groep keuzerondjes {#radio-group}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe raadt u aan de [Formulieropties Core-component](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/forms/form-options.html) in plaats daarvan.

Een groep keuzerondjes bevat een lijst met een of meer keuzerondjes, waarvan er slechts één op een bepaald moment kan worden geselecteerd.

U kunt de elementnaam samen met een titel en een beschrijving opgeven. Gebruik de knoppen + en - om items toe te voegen of te verwijderen, plaats deze met de pijlen omhoog en omlaag en geef indien nodig een standaardwaarde op:

![dc_form_radiogroupuse](assets/dc_form_radiogroupuse.png)

>[!NOTE]
>
>Gebruiken **Pad items laden** u kunt de groep keuzerondjes vooraf laden met waarden.
>
>Zie [Formuliervelden met meerdere waarden vooraf laden](/help/sites-developing/developing-forms.md#preloading-form-fields-with-multiple-values).

### Verzendknop {#submit-button}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe raadt u aan de [Kern van knop Formulier](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/forms/form-button.html) in plaats daarvan.

Met deze component kunt u een verzendknop maken met de standaardtekst:

![dc_form_submitButton](assets/dc_form_submitbutton.png)

Of met uw eigen tekst:

![dc_form_submitButtonUse](assets/dc_form_submitbuttonuse.png)

### Labels veld {#tags-field}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe raadt u aan de [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) in plaats daarvan.

In dit veld kunt u tags selecteren:

![dc_form_tags_use](assets/dc_form_tags_use.png)

U kunt verschillende parameters opgeven, waaronder de naamruimten die kunnen worden gebruikt, op het gespecialiseerde tabblad:

* **Tagveld**

   * **Toegestane naamruimten**

      * **Geometrixx Outdoors**
      * **Workflow**
      * **Forum**
      * **Stock Photography**
      * **Geometrixx Media**
      * **Standaardlabels**
      * **Marketing**
      * **Eigenschappen van element**
      * **Breedte in pixels**
      * **Grootte pop-up**

### Tekstveld {#text-field}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe raadt u aan de [Component Form Text Core](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/forms/form-text.html) in plaats daarvan.

Het standaardtekstveld kan worden geconfigureerd op de gewenste grootte en met uw eigen lead in een bericht:

![dc_form_text](assets/dc_form_text.png)

### Knop(en) voor verzenden werkstroom {#workflow-submit-button-s}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe raadt u aan de [Kern van knop Formulier](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/forms/form-button.html) in plaats daarvan.

Hiermee kunt u een knop Verzenden maken voor gebruik in een workflow.

![chlimage_1-101](assets/chlimage_1-101.png)
