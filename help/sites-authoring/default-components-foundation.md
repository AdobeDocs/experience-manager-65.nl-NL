---
title: Elementaire componenten
description: Leer over de Componenten van de Stichting in Adobe Experience Manager 6.5.
exl-id: 278701f3-3f0c-45f4-90b7-c0e316a7da8a
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User,Admin,Developer
source-git-commit: c77849740fab51377ce60aff5f611e0408dca728
workflow-type: tm+mt
source-wordcount: '6873'
ht-degree: 0%

---

# Elementaire componenten {#foundation-components}

>[!CAUTION]
>
>De meeste stichtingscomponenten zijn nu verouderd met AEM 6.5. Zie de [&#x200B; versienota&#39;s &#x200B;](/help/release-notes/deprecated-removed-features.md) voor verdere informatie.
>
>Adobe adviseert het gebruiken van de modernere en verlengbare [&#x200B; Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) in de projecten van AEM. Deze componenten maken deel uit van [&#x200B; wij.Retail steekproefinhoud &#x200B;](/help/sites-developing/we-retail.md) en kunnen ook [&#x200B; afzonderlijk worden geïnstalleerd en voor ontwikkeling &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/get-started/using.html) door uw beheerder worden gebruikt.
>
>U kunt [&#x200B; AEM gebruiken moderniseert de Reeks van Hulpmiddelen &#x200B;](https://opensource.adobe.com/aem-modernize-tools/) om uw op componenten-Gebaseerde plaats van de Stichting te weerspiegelen om de Componenten van de Kern te gebruiken.

De basiscomponenten zijn ontworpen voor gebruik bij het ontwerpen van inhoud voor een standaardwebpagina. Zij vormen een ondergroep van de componenten beschikbaar uit-van-de-doos voor een standaardinstallatie van AEM.

Sommige zijn onmiddellijk beschikbaar door componentenbrowser. Diverse anderen zijn ook beschikbaar door [&#x200B; ontwerpwijze &#x200B;](/help/sites-authoring/default-components-designmode.md) te gebruiken (als de pagina op een statisch malplaatje) of door [&#x200B; gebaseerd is het malplaatje &#x200B;](/help/sites-authoring/templates.md) uit te geven (als de pagina op een editable malplaatje) wordt gebaseerd.

Het gebruik van stichtingscomponenten wordt gesteund, maar zij zijn hoofdzakelijk verouderd en vervangen door de Componenten van de Kern die meer rekbaarheid en flexibiliteit aanbieden.

>[!NOTE]
>
>Deze sectie bespreekt slechts componenten die uit-van-de-doos in een standaardinstallatie van AEM beschikbaar zijn.
>
>Afhankelijk van uw instantie, kunt u aangepaste componenten hebben die uitdrukkelijk voor uw vereisten worden ontwikkeld. Deze douanecomponenten kunnen zelfs de zelfde naam hebben zoals sommige hier besproken componenten.

De componenten zijn beschikbaar op het **lusje van Componenten** van het zijpaneel van de paginaredacteur wanneer [&#x200B; het uitgeven van een pagina &#x200B;](/help/sites-authoring/editing-content.md).

U kunt een component selecteren en naar de gewenste locatie op de pagina slepen. U kunt het dan uitgeven gebruikend:

* [Eigenschappen configureren](/help/sites-authoring/editing-page-properties.md)
* [Inhoud bewerken](/help/sites-authoring/editing-content.md)

* [Inhoud bewerken - Modus Volledig scherm](/help/sites-authoring/editing-content.md#edit-content-full-screen-mode)

Componenten worden gesorteerd op basis van verschillende categorieën, componentgroepen genaamd, waaronder:

* [&#x200B; Algemeen &#x200B;](#general): Omvat basiscomponenten, met inbegrip van tekst, beelden, lijsten, en grafieken.
* [&#x200B; Kolommen &#x200B;](#columns): Omvat componenten noodzakelijk voor het organiseren van de lay-out van de inhoud.
* [&#x200B; Vorm &#x200B;](#formgroup): Omvat alle noodzakelijke componenten creeren een vorm.

## Algemeen {#general}

De algemene componenten zijn de basiscomponenten die u gebruikt om inhoud te maken.

### Account-item {#account-item}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe adviseert in plaats daarvan gebruikend de [&#x200B; Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html).

U kunt een koppeling definiëren met een titel en beschrijving.

![&#x200B; chlimage_1-88 &#x200B;](assets/chlimage_1-88.png)

### Aangepaste afbeelding {#adaptive-image}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe adviseert in plaats hiervan het gebruiken van de [&#x200B; Component van de Kern van het Beeld &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/image.html).

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
>Bewegende GIF-bestanden worden niet ondersteund in AEM voor adaptieve uitvoeringen.

#### Afbeeldingsgrootten en -kwaliteit {#images-sizes-and-quality}

In de volgende tabel wordt de breedte weergegeven van de afbeelding die wordt gegenereerd voor de opgegeven breedte van de viewport. De hoogte van de gegenereerde afbeelding wordt berekend om een constante hoogte-breedteverhouding te behouden en er wordt geen witruimte weergegeven binnen de afbeeldingsrand. Uitsnijden kan worden gebruikt om witruimte te voorkomen.

Als de afbeelding een JPEG-afbeelding is, kan de viewportgrootte ook van invloed zijn op de JPEG-kwaliteit. De volgende JPEG-eigenschappen zijn mogelijk:

* Laag (0,42)
* Medium (0,82)
* Hoog (1,00)

| **de Waaier van de Breedte van de Viewport (pixel)** | **Breedte van het Beeld (pixel)** | **Kwaliteit JPEG** | **gericht Type van Apparaat** |
|---|---|---|---|
| width &lt;= 319 | 320 | laag |  |
| width = 320 | 320 | medium | Mobiele telefoon (staand) |
| 320 &lt; breedte &lt; 481 | 480 | medium | Mobiele telefoon (liggend) |
| 480 &lt; breedte &lt; 769 | 476 | hoog | Tablet (staand) |
| 768 &lt; breedte &lt; 1025 | 620 | hoog | Tablet (liggend) |
| breedte &lt;= 1025 | full (oorspronkelijke grootte) | hoog | Desktop |

#### Eigenschappen {#properties}

In het dialoogvenster kunt u eigenschappen bewerken voor uw instantie van de component Adaptieve afbeelding, die vaak worden gebruikt voor de component Image waarop deze is gebaseerd. De eigenschappen zijn beschikbaar op twee tabbladen:

* **Beeld**

   * **Beeld**
Sleep een afbeelding vanuit de zoekfunctie voor inhoud of klik om een bladervenster te openen waarin u een afbeelding kunt laden. Nadat de afbeelding is geladen, kunt u de afbeelding uitsnijden, roteren of verwijderen. Als u wilt in- of uitzoomen op de afbeelding, gebruikt u de schuifbalk onder de afbeelding (boven de knoppen OK en Annuleren)

   * **Uitsnijden**
Een gedeelte van een afbeelding uitknippen. Sleep de rand om de afbeelding uit te snijden.

   * **roteren**
Klik herhaaldelijk op Roteren totdat de afbeelding naar wens is geroteerd.

   * **Duidelijk**
Verwijder de huidige afbeelding.

* **Geavanceerd**

   * **Titel**
De component Adaptive Image gebruikt deze eigenschap niet.

   * **de Tekst van Alt**
De alternatieve tekst die voor de afbeelding moet worden gebruikt.

   * **Verbinding aan**
De component Adaptive Image gebruikt deze eigenschap niet.

   * **Beschrijving**
De component Adaptive Image gebruikt deze eigenschap niet.

#### De component Adaptieve afbeelding uitbreiden {#extending-the-adaptive-image-component}

Voor informatie over het aanpassen van de Adaptieve component van het Beeld, zie [&#x200B; Begrijpend de Aanpassende Component van het Beeld &#x200B;](/help/sites-developing/responsive.md#using-adaptive-images).

### Carrousel {#carousel}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe adviseert in plaats hiervan het gebruiken van de [&#x200B; Component van de Kern van de Carrousel &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/carousel.html).

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

   * Afspeelsnelheid
De tijd in milliseconden voordat de volgende dia wordt getoond.
   * Overgangstijd
De tijd in milliseconden voor de overgang tussen twee dia&#39;s.
   * Besturingselementstijl
Verschillende opties zijn beschikbaar in een keuzemenu, bijvoorbeeld Vorige/Volgende knoppen, Linksboven geschakeld.

* **Lijst**

  Hier geeft u op hoe pagina&#39;s in uw carrousel moeten worden opgenomen:

   * **bouwt lijst gebruikend**
Er zijn verschillende manieren om een paginalijst samen te stellen: Onderliggende pagina&#39;s, Vaste lijst, Zoeken of Geavanceerd zoeken (allemaal hieronder beschreven).
Welke methode u ook kiest, aan de pagina&#39;s die u in de lijst opneemt, moet al een afbeelding zijn gekoppeld. Deze afbeelding wordt weergegeven in de carrousel. Als er geen afbeelding is voor een bepaalde pagina onder de Pagina-eigenschappen van die pagina, moet u een afbeelding aan de pagina koppelen voordat u begint. Als u dat niet doet, wordt in de carrousel een pagina weergegeven die meestal leeg is. Zie [&#x200B; het Uitgeven Eigenschappen van de Pagina &#x200B;](/help/sites-authoring/editing-page-properties.md).
Afhankelijk van het item dat u kiest, wordt een nieuw deelvenster weergegeven:

      * **Opties voor de Pagina&#39;s van het Kind**

         * **Ouderlijke Pagina**
Geef een pad handmatig of met de kiezer op. Laat leeg als u de huidige pagina als bovenliggend item wilt gebruiken.

      * **Opties voor Vaste Lijst**

         * **Pagina&#39;s**
Selecteer een lijst met pagina&#39;s. Gebruik `+` om meer items toe te voegen en de knoppen Omhoog en Omlaag om de volgorde aan te passen.

      * **Opties voor Onderzoek**

         * **Begin in**
Voer handmatig of met de kiezer een beginpad in.

         * **vraag van het Onderzoek**
U kunt een zoekquery voor onbewerkte tekst invoeren.

      * **Opties voor Geavanceerd Onderzoek**

         * **Querybuilder voorspelt aantekening**
U kunt een onderzoeksvraag ingaan gebruikend Querybuilder prediknotatie. U kunt bijvoorbeeld &quot;fulltext=Marketing&quot; invoeren om alle pagina&#39;s met &quot;Marketing&quot; in de inhoud weer te geven in de carrousel.
Zie [&#x200B; QueryBuilder API &#x200B;](/help/sites-developing/querybuilder-api.md) voor volledige bespreking van vraaguitdrukkingen en verdere voorbeelden.

   * **Orde door**
Selecteer `jcr:title` , `jcr:created` , `cq:lastModified` of `cq:template` in het vervolgkeuzemenu.

   * **Grens**
Optioneel. Het maximumaantal items dat u in de carrousel wilt gebruiken.

>[!NOTE]
>
>U kunt een aangepaste carrouselcomponent voor Adobe Experience Manager maken die digitale elementen weergeeft in de AEM DAM. Zie [&#x200B; Creërend de componenten van de Carrousel van de Douane voor Adobe Experience Manager &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html).

### Diagram {#chart}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe adviseert in plaats daarvan gebruikend de [&#x200B; Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html).

Met de component Diagram kunt u een balk, lijn of cirkeldiagram toevoegen. AEM maakt een grafiek op basis van de gegevens die u opgeeft. U verstrekt gegevens door direct in het lusje van Gegevens te typen of door een spreadsheet te kopiëren en te kleven.

* **Gegevens**

   * **Gegevens van de Grafiek**
Voer uw grafiekgegevens in met de CSV-indeling; in de indeling Door komma&#39;s gescheiden waarden worden komma&#39;s (&quot;,&quot;) gebruikt als veldscheidingsteken.

* **Geavanceerd**

   * **Type van Grafiek**
Selecteer Schijfdiagram, Lijngrafiek en Staafdiagram.

   * **Alternatieve tekst**
Hiermee geeft u alternatieve tekst weer in plaats van het diagram.

   * **Breedte**
De breedte van het diagram in pixels.

   * **Hoogte**
De hoogte van het diagram in pixels.

In het volgende voorbeeld ziet u een voorbeeld van diagramgegevens, gevolgd door het resulterende staafdiagram:

![&#x200B; chlimage_1-89 &#x200B;](assets/chlimage_1-89.png) ![&#x200B; dc_chart_use &#x200B;](assets/dc_chart_use.png)

>[!NOTE]
>
>U kunt een aangepast AEM-diagrambesturingselement maken waarmee gegevens worden weergegeven in de AEM JCR. Voor informatie, zie [&#x200B; Weergevend de Gegevens van Adobe Experience Manager in een Grafiek &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html).

### Inhoudsfragment {#content-fragment}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe adviseert in plaats hiervan het gebruiken van de [&#x200B; Component van de Kern van het Fragment van de Inhoud &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html).

{de fragmenten van 0} Inhoud [&#x200B; worden gecreeerd en als pagina-onafhankelijke activa beheerd. &#x200B;](/help/sites-authoring/content-fragments.md) Vervolgens kunt u deze fragmenten en de variaties ervan gebruiken bij het ontwerpen van de inhoudspagina&#39;s.

### Design Importer {#design-importer}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe adviseert in plaats daarvan gebruikend de [&#x200B; Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html).

Met deze component kunt u een ZIP-bestand met een ontwerppakket uploaden.

### Downloaden {#download}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe adviseert in plaats daarvan gebruikend de [&#x200B; Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html).

De component Download maakt een koppeling op de geselecteerde webpagina om een specifiek bestand te downloaden. U kunt middelen van de Vinder van de Inhoud slepen of een dossier uploaden.

* **Download**

   * **Beschrijving**
Een korte beschrijving die wordt weergegeven met de downloadkoppeling.

   * **Dossier**
Het bestand dat op de resulterende webpagina kan worden gedownload. Sleep een element van de inhoudzoeker of selecteer het gebied zodat u het bestand kunt uploaden dat u wilt downloaden.

In het volgende voorbeeld wordt de component Download in Geometrixx getoond:

![&#x200B; dc_download_use &#x200B;](assets/dc_download_use.png)

### Extern {#external}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe adviseert in plaats daarvan gebruikend de [&#x200B; Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html).

De externe component van de toepassingsintegratie (**Extern**) laat u toe om externe toepassingen in uw pagina van AEM in te bedden gebruikend een iframe.

* **Extern**

   * **toepassing van het Doel**
Geef de URL op van de webtoepassing die moet worden geïntegreerd, bijvoorbeeld:

     ```
     https://en.wikipedia.org/wiki/Main_Page
     ```

   * **parameters van de Pas**
Schakel het selectievakje in als de parameters naar de toepassing moeten worden doorgegeven.

   * **Breedte en Hoogte
**De grootte van het iframe definiëren

De externe toepassing is geïntegreerd in het alineasysteem van de AEM-pagina, bijvoorbeeld wanneer u een doeltoepassing van `https://en.wikipedia.org/wiki/Main_Page` gebruikt:

![&#x200B; chlimage_1-90 &#x200B;](assets/chlimage_1-90.png)

>[!NOTE]
>
>Afhankelijk van uw gebruiksgeval, zijn andere opties beschikbaar voor integratie van externe toepassingen, bijvoorbeeld, de [&#x200B; Integratie van Portlets &#x200B;](/help/sites-administering/aem-as-portal.md).

### Flash {#flash}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe adviseert in plaats daarvan gebruikend de [&#x200B; Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html).

>[!CAUTION]
>
>Van deze component wordt niet meer verwacht om buiten-van-de-doos zonder uitgebreide project-vlakke aanpassing te functioneren.

Met de Flash-component kunt u een Flash-film laden. U kunt een Flash-element van de zoeker naar de component slepen of u kunt het dialoogvenster gebruiken:

* **Flits**

   * **de film van de Flits**

     Het Flash-filmbestand. Sleep een element van de zoeker naar de inhoud of klik om een bladervenster te openen.

   * **Grootte**

     Afmetingen in pixels van het weergavegebied waarin de film wordt weergegeven.

* **Alternatief Beeld**

  Een alternatieve afbeelding die moet worden weergegeven

* **Geavanceerd**

   * **Contextmenu**

     Geeft aan of het contextmenu moet worden weergegeven of verborgen.

   * **Wijze van het Venster**

     Hoe het venster er uitziet, bijvoorbeeld dekkend, transparant of als een duidelijk (effen) venster.

   * **Achtergrondkleur**

     Een achtergrondkleur die is geselecteerd in het kleurendiagram dat wordt weergegeven.

   * **Minimale versie**

     De minimale versie van Adobe Flash Player die is vereist om de film uit te voeren. De standaardwaarde is 9.0.0.

   * **Attributen**

     Eventuele andere vereiste kenmerken.

### Afbeelding {#image}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe adviseert in plaats hiervan het gebruiken van de [&#x200B; Component van de Kern van het Beeld &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/image.html).

In de afbeeldingscomponent wordt een afbeelding en de bijbehorende tekst weergegeven volgens de opgegeven parameters.

U kunt een afbeelding uploaden, deze vervolgens bewerken en bewerken (bijvoorbeeld uitsnijden, roteren, koppeling/titel/tekst toevoegen).

U kunt of een beeld van [&#x200B; browser van Assets slepen en laten vallen &#x200B;](/help/sites-authoring/author-environment-tools.md#assets-browser) direct op de component of zijn [&#x200B; vormen dialoog &#x200B;](/help/sites-authoring/editing-content.md#component-edit-dialog). U kunt een beeld van de Configure dialoog ook uploaden; dit dialoog controleert alle definities en manipulatie van het beeld:

![&#x200B; chlimage_1-91 &#x200B;](assets/chlimage_1-91.png)

Nadat het beeld (en niet vóór) wordt geupload, kunt u [&#x200B; gebruiken op plaats het uitgeven &#x200B;](/help/sites-authoring/editing-content.md#edit-content) om het beeld zoals vereist uit te snijden/te roteren:

![&#x200B; Plaats het uitgeven toolbar &#x200B;](do-not-localize/chlimage_1-15.png)

>[!NOTE]
>
>De editor op locatie gebruikt de oorspronkelijke grootte en hoogte-breedteverhouding van de afbeelding tijdens het bewerken. U kunt ook de eigenschappen voor hoogte en breedte opgeven. Beperkingen voor grootte en hoogte-breedteverhouding die in de eigenschappen zijn gedefinieerd, worden toegepast wanneer u de bewerkingswijzigingen opslaat.
>
>Afhankelijk van uw instantie, kunnen de minimum en maximumbeperkingen ook door het [&#x200B; ontwerp van de pagina &#x200B;](/help/sites-developing/designer.md) worden opgelegd. Deze beperkingen worden ontwikkeld tijdens de uitvoering van het project.

Er zijn verschillende aanvullende opties beschikbaar in de modus Volledig scherm, bijvoorbeeld voor toewijzen en zoomen:

![&#x200B; Volledig scherm het uitgeven wijze - kaart en gezoem &#x200B;](do-not-localize/chlimage_1-16.png)

>[!NOTE]
>
>De voortgang van het uploaden kan niet worden gecontroleerd met Internet Explorer.
>
>De gebruikers van Internet Explorer moeten het beeld uploaden en **O.K.** klikken, dan het beeld opnieuw openen om het geuploade dossier in de voorproef te zien en wijzigingen (namelijk gewas) kunnen uitvoeren.
>
>Zie de [&#x200B; Verklaarde sectie van Platforms &#x200B;](/help/release-notes/release-notes.md#certifiedplatforms) voor meer informatie over HTML5 eigenschappen die door AEM worden gebruikt.

Wanneer een beeld wordt geladen, kunt u het volgende vormen:

* **Kaart**

  Als u een afbeelding wilt toewijzen, selecteert u Kaart. U kunt opgeven hoe u de afbeelding met hyperlinks wilt maken (rechthoek, veelhoek enzovoort) en waar het gebied naartoe moet wijzen.

* **Uitsnijden**

  Als u een deel van een afbeelding wilt uitknippen, selecteert u Uitsnijden. Gebruik de muis om de afbeelding uit te snijden.

* **roteren**

  Selecteer Roteren als u een afbeelding wilt roteren. Herhaal deze bewerking totdat de afbeelding op de gewenste manier is geroteerd.

* **Duidelijk**

  Verwijder de huidige afbeelding.

* **Titel**

  De titel van de afbeelding.

* **de Tekst van Alt**

  Een alternatieve tekst die kan worden gebruikt bij het maken van toegankelijke inhoud.

* **Verbinding aan**

  Maak een koppeling naar elementen of andere pagina&#39;s binnen uw website.

* **Beschrijving**

  Een beschrijving van de afbeelding.

* **Grootte**

  Hiermee stelt u de hoogte en de breedte van de afbeelding in.

>[!NOTE]
>
>Sommige opties zijn alleen beschikbaar in de volledige-schermeditor.

Het definitieve beeld (met **Titel** en **Beschrijving**) kan als worden getoond:

![&#x200B; chlimage_1-92 &#x200B;](assets/chlimage_1-92.png)

### Layout Container {#layout-container}

Deze component verstrekt een net-paragraaf systeem om u toe te voegen en componenten binnen a [&#x200B; ontvankelijk net &#x200B;](/help/sites-authoring/responsive-layout.md) te plaatsen. U kunt verschillende inhoudslaay-outs bepalen die op de breedte van doelapparaten, met inbegrip van een waaier van telefoons, tabletten, en de Desktop worden gebaseerd.

![&#x200B; chlimage_1-93 &#x200B;](assets/chlimage_1-93.png)

>[!NOTE]
>
>Deze component is uitgevoerd met [&#x200B; Taal van het Malplaatje van HTML (HTML) &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html).

### Lijst {#list}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe adviseert het gebruiken van de [&#x200B; Component van de Kern van de Lijst &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/list.html) in plaats daarvan.

Met de component List kunt u zoekcriteria configureren voor het weergeven van een lijst:

* **Lijst**

   * **bouwt lijst gebruikend**

     Hier geeft u op waar de lijst de inhoud ophaalt. Er zijn verschillende methoden:

   * Afhankelijk van het item dat u kiest, wordt een nieuw deelvenster weergegeven:

      * **Opties voor de Pagina&#39;s van het Kind**

         * **Kinderen van** (Ouderlijke Pagina)

           Geef een pad handmatig of met de kiezer op. Laat leeg als u de huidige pagina als bovenliggend item wilt gebruiken.

      * **Opties voor Vaste Lijst**

         * **Pagina&#39;s**

           Selecteer een lijst met pagina&#39;s. Gebruik + om meer items toe te voegen en klik op de knop Omhoog/Omlaag om de volgorde aan te passen.

      * **Opties voor Onderzoek**

         * Starten in

           Voer handmatig of met de kiezer een beginpad in.

         * Zoekquery

           U kunt een zoekquery voor onbewerkte tekst invoeren.

      * **Opties voor Geavanceerd Onderzoek**

         * **Querybuilder voorspelt aantekening**

           U kunt een onderzoeksvraag ingaan gebruikend Querybuilder prediknotatie. U kunt bijvoorbeeld &quot;fulltext=Marketing&quot; invoeren om alle pagina&#39;s met &quot;Marketing&quot; in de inhoud weer te geven in de carrousel.

           Zie [&#x200B; QueryBuilder API &#x200B;](/help/sites-developing/querybuilder-api.md) voor volledige bespreking van vraaguitdrukkingen en verdere voorbeelden.

      * **Markeringen**

        Specificeer de **Ouderlijke pagina**, **Markeringen/Trefwoorden**, en uw vereiste gelijkheidscriteria.

   * **Vertoning als**

     Hoe u de punten wilt worden vermeld; omvat Verbindingen, Teasers en Nieuws.

   * **Orde door**

     Of de lijst moet worden besteld en, zo ja, welke criteria moeten worden gebruikt voor sorteren. U kunt criteria invoeren of een criteria selecteren in de opgegeven vervolgkeuzelijst.

   * **Grens**

     Geef het maximumaantal items op dat u in de lijst wilt weergeven.

   * **laat Dieren** toe

     Geeft aan of een RSS-feed voor de lijst moet worden geactiveerd.

   * **pagineren na**

     Hier kunt u het aantal lijstitems opgeven dat in één keer moet worden weergegeven. Een lijst met meer items dan opgegeven gebruikt paginering om de lijst in verschillende delen weer te geven.

Het volgende voorbeeld toont de component van de Lijst van de a **&#x200B;**&#x200B;de manier dat het een lijst van kindpagina&#39;s kan tonen (het ontwerp wordt gecontroleerd door de douaneCSS definities van een plaatsontwerp).

![&#x200B; dc_list_use &#x200B;](assets/dc_list_use.png)

### Aanmelden {#login}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe adviseert in plaats daarvan gebruikend de [&#x200B; Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html).

>[!CAUTION]
>
>Van deze component wordt niet meer verwacht om buiten-van-de-doos zonder uitgebreide project-vlakke aanpassing te functioneren.

Hiermee worden de velden Gebruikersnaam en Wachtwoord weergegeven.

![&#x200B; chlimage_1-94 &#x200B;](assets/chlimage_1-94.png)

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

   * **Verbinding**

     Geef de pagina (het product) op waarvoor de status van de bestelling moet worden weergegeven.

   * **Type/Grootte**

     Maak een keuze uit de beschikbare selectie.

![&#x200B; chlimage_1-95 &#x200B;](assets/chlimage_1-95.png)

### Referentie {#reference}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe adviseert in plaats hiervan het gebruiken van de [&#x200B; Component van de Kern van het Fragment van de Inhoud &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html).

De **component van de Verwijzing** laat u tekst van een andere pagina van uw website van AEM (binnen de huidige instantie) van verwijzingen voorzien. De inhoud van de alinea waarnaar wordt verwezen, wordt weergegeven alsof deze zich op de huidige pagina bevindt. De inhoud wordt bijgewerkt wanneer de bronalinea verandert (mogelijk moet de pagina worden vernieuwd).

* **Verwijzing van de Paragraaf**

   * **Verwijzing**

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

![&#x200B; chlimage_1-96 &#x200B;](assets/chlimage_1-96.png)

### Zoeken {#searching}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe adviseert het gebruiken van de [&#x200B; Snelle Component van de Kern van het Onderzoek &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/quick-search.html) in plaats daarvan.

De component van het Onderzoek voegt onderzoeksmogelijkheden aan uw pagina toe.

U kunt configureren:

* Zoeken

   * **de Types van Knoop**

     Als de zoekopdracht moet worden beperkt tot een bepaald knooppunttype, geeft u hier een lijst van knooppunten op, bijvoorbeeld `cq:Page` .

   * **Weg aan onderzoek in**

     Geef de basispagina op van de vertakking die u wilt doorzoeken.

   * **de Tekst van de Knoop van het Onderzoek**

     De naam die wordt weergegeven op de werkelijke zoekknop.

   * **Tekst van Statistieken**

     De tekst die boven de zoekresultaten wordt weergegeven.

   * **Geen Tekst van Resultaten**

     Als er geen resultaten zijn, wordt de hier ingevoerde tekst weergegeven.

   * **Spellcheck Tekst**

     Als iemand een gelijkaardige termijn ingaat, wordt deze tekst getoond vóór de termijn.
Als u bijvoorbeeld `Geometrixxe` typt, geeft het systeem &quot;Bedoelde u? Geometrixx&quot;.

   * **Vergelijkbare Tekst van Pagina&#39;s**

     De tekst die wordt weergegeven naast een resultaat voor vergelijkbare pagina&#39;s. Klik op deze koppeling om pagina&#39;s met vergelijkbare inhoud weer te geven.

   * **Verwante Tekst van Zoekopdrachten**

     De tekst die naast onderzoeken naar verwante termijnen en onderwerpen verschijnt.

   * **Tekst van de Trends van het Onderzoek van 0&rbrace;**

     De titel boven de zoektermen die een gebruiker invoert.

   * **Etiket van de Pagina&#39;s van het Resultaat**

     De tekst die onder aan deze lijst wordt weergegeven met koppelingen naar andere resultatenpagina&#39;s.

   * **Vorig Etiket**

     De naam die wordt weergegeven op de koppeling naar vorige zoekpagina&#39;s.

   * **Volgende Etiket**

     De naam die wordt weergegeven op de koppeling naar volgende zoekpagina&#39;s.

In het volgende voorbeeld wordt de component Zoeken weergegeven na een zoekopdracht naar het woord *`geometrixx`* in de hoofdmap van een standaardinstallatie. Ook wordt de paginering van de resultaten geïllustreerd:

![&#x200B; dc_search_use &#x200B;](assets/dc_search_use.png)

In het volgende voorbeeld wordt een zoekterm getoond die verkeerd is gespeld en niet beschikbaar is:

![&#x200B; dc_search_usenotfound &#x200B;](assets/dc_search_usenotfound.png)

### Sitemap {#sitemap}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe adviseert gebruikend de [&#x200B; Navigatie &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/navigation.html), [&#x200B; Navigatie van de Taal &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/language-navigation.html), en [&#x200B; Componenten van de Kern van de Breadcrumb &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/breadcrumb.html) in plaats daarvan.

Een automatische sitemapvermelding die (met de standaardinstellingen) alle pagina&#39;s (als actieve koppelingen) op de huidige website weergeeft. Een extract toont bijvoorbeeld:

![&#x200B; dc_sitemap_use &#x200B;](assets/dc_sitemap_use.png)

Indien nodig, kunt u het volgende vormen:

* **Sitemap**

   * **Weg van de Wortel**

     Pad vanaf waar de aanbieding moet beginnen.

### Presentatie {#slideshow}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe adviseert in plaats hiervan het gebruiken van de [&#x200B; Component van de Kern van de Carrousel &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/carousel.html).

>[!CAUTION]
>
>Van deze component wordt niet meer verwacht om buiten-van-de-doos zonder uitgebreide project-vlakke aanpassing te functioneren.

Met deze component kunt u een reeks afbeeldingen laden die als een diapresentatie op de pagina worden weergegeven. U kunt afbeeldingen toevoegen of verwijderen en elke titel toewijzen. Onder Geavanceerd kunt u ook de grootte van het weergavegebied opgeven.

U kunt configureren:

* **Dia&#39;s**

   * **Nieuwe Dia**

     U kunt een selectie van dia&#39;s specificeren gebruikend **voeg** toe (en **verwijder**) knopen.

   * **Titel**

     Geef indien nodig een titel op. De titel staat op de juiste dia.

* **Geavanceerd**

   * **Grootte**

     Geef de breedte en hoogte op in pixels.

In de diapresentatie-component worden vervolgens herhaaldelijk alle elementen in de juiste volgorde weergegeven, gedurende een korte tijd, voordat de volgende dia wordt afgevlakt:

![&#x200B; dc_slideshow_use &#x200B;](assets/dc_slideshow_use.png)

### Tabel {#table}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe adviseert in plaats hiervan het gebruiken van de [&#x200B; Component van de Kern van de Tekst &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/text.html).

>[!NOTE]
>
>De **Component van de Lijst** Stichting is gebaseerd op de [&#x200B; Rich redacteur van de Tekst &#x200B;](/help/sites-authoring/rich-text-editor.md), zoals de **[Component van de Tekst](#text)** Stichting is.

De **component van de Lijst** wordt preconfigured om u te laten, een lijst construeren vullen en formatteren. Met behulp van het dialoogvenster kunt u uw tabel configureren en de inhoud maken door:

* krassen
* het kopiëren van en het kleven van een spreadsheet of een lijst van een externe redacteur (zoals Excel, OpenOffice, en Blocnote).

Met de inline editor kunt u basiswijzigingen in de inhoud aanbrengen:

![&#x200B; dc_table &#x200B;](assets/dc_table.png)

In de modus Volledig scherm kunt u de tabellay-out configureren:

![&#x200B; chlimage_1-97 &#x200B;](assets/chlimage_1-97.png)

In de volgende schermafbeelding ziet u een voorbeeld van de tabelcomponent. Het ontwerp wordt bepaald door de sitespecifieke CSS:

![&#x200B; dc_table_use &#x200B;](assets/dc_table_use.png)

### Cloud labelen {#tag-cloud}

Een tagcloud geeft een grafisch weergegeven selectie van de tags die zijn toegepast op de inhoud van uw website:

![&#x200B; dc_tagclouduse &#x200B;](assets/dc_tagclouduse.png)

Wanneer u de component Tag Cloud configureert, kunt u het volgende opgeven:

* **Markeringen aan Vertoning**

  Waar de weer te geven tags worden verzameld. Selecteer op een pagina een pagina met alle onderliggende codes of alle codes.

* **Pagina**

  Selecteer de pagina waarnaar moet worden verwezen.

* **Geen verbindingen op markeringen**

  Of de weergegeven tags moeten fungeren als koppelingen.

Voor meer informatie over het toepassen van markeringen, bezoek [&#x200B; Gebruikend Markeringen &#x200B;](/help/sites-authoring/tags.md).

### Tekst {#text}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe adviseert in plaats hiervan het gebruiken van de [&#x200B; Component van de Kern van de Tekst &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/text.html).

>[!NOTE]
>
>De **Component van de Stichting van de Tekst** &lbrace;is gebaseerd op de [&#x200B; Rijke redacteur van de Tekst &#x200B;](/help/sites-authoring/rich-text-editor.md), zoals de **Lijst** Component van de Stichting is.

De component van de Tekst laat u een tekstblok ingaan gebruikend een redacteur van WYSIWYG, met functionaliteit die door de [&#x200B; Rich redacteur van de Tekst &#x200B;](/help/sites-authoring/rich-text-editor.md) wordt verstrekt. Met een selectie pictogrammen kunt u de tekst opmaken, inclusief lettertypekenmerken, uitlijning, koppelingen, lijsten en inspringing.

![&#x200B; chlimage_1-98 &#x200B;](assets/chlimage_1-98.png)

Wanneer u **opent vormt** dialoog, kunt u ook plaatsen:

* **Spacer**
* **Stijl van de Tekst**

De opgemaakte tekst wordt weergegeven op de pagina. Het daadwerkelijke ontwerp is afhankelijk van de site-CSS:

![&#x200B; dc_text_use &#x200B;](assets/dc_text_use.png)

Voor meer gedetailleerde informatie over de component van de Tekst en de functionaliteit die door de Rich redacteur van de Tekst wordt verstrekt, zie de [&#x200B; pagina van de Redacteur van de Tekst 0&rbrace; Rich.](/help/sites-authoring/rich-text-editor.md)

#### Op plaats bewerken {#inplace-editing}

Naast op dialoog-gebaseerde Rich Tekst het uitgeven wijze, verstrekt AEM ook [&#x200B; het Uitgeven van de Plaats &#x200B;](/help/sites-authoring/editing-content.md), die directe het uitgeven van de tekst toestaat aangezien het in de lay-out van de pagina wordt getoond.

### Tekst en afbeelding {#text-image}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe adviseert het gebruiken van de [&#x200B; Component van de Kern van het Beeld &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/image.html) en [&#x200B; Tekst &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/text.html) in plaats daarvan.

De component Tekst en afbeelding voegt een tekstblok en een afbeelding toe. U kunt ook afzonderlijk tekst en afbeeldingen toevoegen en bewerken. Zie de [&#x200B; Tekst &#x200B;](#text) en [&#x200B; 3&rbrace; componenten van het Beeld &lbrace;voor details.](#image)

![&#x200B; chlimage_1-99 &#x200B;](assets/chlimage_1-99.png)

U kunt configureren:

* **Stijlen van de Component** (**Stijlen**)

  Hier kunt u de afbeelding links of rechts uitlijnen. Het gebrek is **Linker** gericht, met het beeld bij de linkerzijde.

* **Eigenschappen van het Beeld** (**Geavanceerde Eigenschappen van het Beeld**)

  Hier kunt u het volgende opgeven:

   * **activa van het Beeld**

     Upload de vereiste afbeelding.

   * **Titel**

     De titel voor het blok, weergegeven door mouseover.

   * **de Tekst van Alt**

     Alternatieve tekst die moet worden weergegeven als de afbeelding niet kan worden weergegeven. Als de titel leeg blijft, wordt deze gebruikt.

   * **Verbinding aan**

     Geef een doelpad op.

   * **Beschrijving**

     Een beschrijving van de afbeelding.

   * **Grootte**

     Hiermee stelt u de hoogte en breedte van de afbeelding in.

In het volgende voorbeeld ziet u een component Tekstafbeelding waarmee de afbeelding links wordt uitgelijnd:

![&#x200B; dc_texmage_use &#x200B;](assets/dc_textimage_use.png)

### Titel {#title}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe adviseert in plaats hiervan het gebruiken van de [&#x200B; Component van de Kern van de Titel &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/list.html).

De component title kan:

* Geef de naam van de huidige pagina weer door het veld Titel leeg te laten.
* Geef een tekst weer die u opgeeft in het veld Titel.

U kunt configureren:

* **Titel**

  Als u een andere naam dan de paginatitel wilt gebruiken, voert u deze hier in.

* **Verbinding**

  De URI als de titel moet werken als een koppeling.

* **Type/Grootte**

  Selecteer Klein of Groot in de vervolgkeuzelijst. Klein wordt gegenereerd als een afbeelding. Groot wordt gegenereerd als tekst.

Het volgende voorbeeld toont de component van de a **Titel** die wordt getoond; het ontwerp wordt bepaald door plaats-specifieke CSS.

![&#x200B; dc_title_use &#x200B;](assets/dc_title_use.png)

### Video {#video}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe adviseert het gebruiken van de [&#x200B; Componenten van de Kern Embed Component &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/embed.html) in plaats daarvan.

>[!CAUTION]
>
>Van deze component wordt niet meer verwacht om buiten-van-de-doos zonder uitgebreide project-vlakke aanpassing te functioneren.

De **Video** component laat u een vooraf bepaald, uit-van-de-doos videoelement op een pagina plaatsen.

Zie ook [&#x200B; Uw VideoProfielen &#x200B;](/help/sites-administering/config-video.md#configuringvideoprofiles) voor gebruik met HTML5 elementen vormen.

Nadat u een instantie van de component op de pagina hebt geplaatst, kunt u het volgende configureren:

* Video

   * **Video activa**

     Upload of zet uw video-element neer.

   * **Grootte**

     De native grootte van de video (breedte x hoogte in pixels) wordt weergegeven in de vakken naast Grootte (zie boven). Voer hier handmatig de afmetingen voor breedte en hoogte in als u de native afmetingen van de video wilt overschrijven. Het selecteren van **O.K.** verwerpt de dialoog.

>[!NOTE]
>
>Ondersteunde indelingen zijn onder andere:
>
>* `.mp4`
>* `Ogg`
>* `FLV` (Flash video)

## Kolommen {#columns}

Kolommen zijn een mechanisme om de lay-out van inhoud in AEM te bepalen. In een standaardinstallatie, worden de componenten voor het creëren van twee of drie kolommen verstrekt.

In het volgende voorbeeld ziet u de twee gebruikte componenten Kolommen. U kunt de plaatsaanduidingen voor nieuwe componenten gebruiken:

![&#x200B; dc_columncontroluse &#x200B;](assets/dc_columncontroluse.png)

### 2 kolommen {#columns-1}

Een component van de Controle van de Kolom die aan twee gelijke kolommen standaard.

### 3 kolommen {#columns-2}

Een component van de Controle van de Kolom die aan drie gelijke kolommen standaard.

### Kolombesturingselement {#column-control}

Met de component Kolombeheer kunnen gebruikers selecteren hoe ze de inhoud in het hoofdvenster van de webpagina in meerdere kolommen willen splitsen. Gebruikers kunnen het aantal vereiste kolommen selecteren (uit een vooraf gedefinieerde lijst) en vervolgens inhoud maken, verwijderen of verplaatsen binnen elk van de kolommen.

* **Controle van de Kolom**

   * **Lay-out van de Kolom**

     Selecteer het aantal kolommen dat u wilt renderen. Nadat elke kolom is gemaakt, bevat deze een eigen koppeling voor het slepen van componenten of elementen tijdens het toevoegen van inhoud.

## Formulier {#form}

>[!CAUTION]
>
>De Foundation-component is afgekeurd. Adobe adviseert in plaats daarvan gebruikend de [&#x200B; Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html).

Formuliercomponenten worden gebruikt om formulieren te maken waarmee bezoekers invoer kunnen verzenden. Forms en formuliercomponenten kunnen worden gebruikt om informatie te verzamelen, waaronder gebruikersfeedback (bijvoorbeeld een vragenlijst voor klanttevredenheid) en gebruikersgegevens (bijvoorbeeld gebruikersregistratie).

>[!NOTE]
>
>Zie [&#x200B; Hulp van AEM Forms &#x200B;](/help/forms/using/introduction-aem-forms.md) voor informatie over AEM Forms.

Forms is opgebouwd uit verschillende onderdelen:

* **Vorm**

  De formuliercomponent definieert het begin en einde van een nieuw formulier op een pagina. Andere componenten kunnen vervolgens tussen deze elementen worden geplaatst, zoals tabellen, en worden gedownload.

* **de gebieden en de elementen van de Vorm**

  Formuliervelden en -elementen kunnen tekstvakken, keuzerondjes en afbeeldingen bevatten. De gebruiker voert vaak een handeling uit in een formulierveld, zoals het typen van tekst. Zie de afzonderlijke formulierelementen voor meer informatie.

* **Componenten van het Profiel**

  Profielcomponenten hebben betrekking op bezoekersprofielen die worden gebruikt voor sociale samenwerking en andere gebieden waar personalisatie van bezoekers vereist is.

Hieronder ziet u een voorbeeldformulier. Het is samengesteld uit de **component van de Vorm** (begin en eind), met twee **vorm** **de gebieden van de Tekst** die voor input worden gebruikt, a **Algemene** **het gebied van de Tekst** voor lood-in tekst en a **legt** knoop voor.

![&#x200B; dc_form &#x200B;](assets/dc_form.png)

>[!NOTE]
>
>De informatie over het ontwikkelen van en het aanpassen van uw vormen is beschikbaar op [&#x200B; het Ontwikkelen van de pagina van Forms &#x200B;](/help/sites-developing/developing-forms.md). Deze mogelijkheid omvat onder andere het toevoegen van handelingen, beperkingen, het vooraf laden van velden en het gebruik van scripts om een service aan een actie aan te roepen.

### Algemene instellingen voor (veel) formuliercomponenten {#settings-common-to-many-form-components}

Hoewel elk van de formuliercomponenten een ander doel heeft, bestaan veel van deze componenten uit vergelijkbare opties en parameters.

Wanneer u een van de formuliercomponenten configureert, zijn de volgende tabbladen beschikbaar in het dialoogvenster:

* **Titel en Tekst**

  Hier moet u de basisinformatie opgeven, zoals de titel van het formulier en eventuele begeleidende tekst. U kunt zo nodig ook andere belangrijke informatie definiëren, zoals of het veld meerdere selecties kan bevatten en of items kunnen worden geselecteerd.

* **Aanvankelijke Waarden**

  Hier geeft u een standaardwaarde op.

* **Beperkingen**

  Hier kunt u opgeven of een veld verplicht is en beperkingen in dat veld instellen (moet bijvoorbeeld een numeriek veld zijn).

* **het Stijlen**

  Hiermee geeft u de grootte en opmaak van de velden aan.

>[!NOTE]
>
>De velden die u ziet, variëren aanzienlijk, afhankelijk van de afzonderlijke component.

Deze lusjes voorzien u van de noodzakelijke parameters. De tabbladen kunnen afhankelijk zijn van het afzonderlijke componenttype, maar kunnen het volgende bevatten:

* **Titel en Tekst**

   * **Naam van het Element**

     Naam van het formulierelement. Het geeft aan waar in de gegevensopslagruimte de gegevens worden opgeslagen.
Dit veld is verplicht en mag alleen de volgende tekens bevatten:

      * alfanumerieke tekens
      * `_ . / : -`

   * **Titel**

     De titel die bij het veld wordt weergegeven. Indien leeg gelaten, wordt de standaardtitel getoond.

   * **Beschrijving**

     Hiermee kunt u, indien nodig, aanvullende informatie voor de gebruiker opgeven. In het formulier wordt het weergegeven onder het veld, in een kleiner lettertype dan de titel.

   * **tonen/verbergen**

     Hiermee bepaalt u wanneer het veld zichtbaar is.

* **Aanvankelijke Waarden**

   * **Standaardwaarde**

     De waarde die in het veld wordt weergegeven wanneer het formulier wordt geopend. Dat wil zeggen, voordat de gebruiker invoer heeft ingevoerd.

* **Beperkingen**

   * **Vereist**

     Restricties zijn afhankelijk van het type formuliercomponent, maar beschikken over een of meer klikvakken om aan te geven dat dit veld is vereist, of dat bepaalde delen van dit veld zijn vereist.

   * **Vereiste Bericht**

     Een bericht om gebruikers te laten weten dat dit veld is vereist. Een vereist veld is ook gemarkeerd met een sterretje.

   * **Restrictie**

     Welke beperkingen beschikbaar zijn voor de selectie, is afhankelijk van het type formuliercomponent.

   * **Bericht van de Beperking**

     Een bericht om gebruikers te informeren wat wordt vereist.

* **het Stijlen**

   * **Grootte**

     In rijen en kolommen.

   * **Breedte**

     In pixels.

   * **CSS**

### Formulier (component) {#form-component}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe adviseert in plaats hiervan het gebruiken van de [&#x200B; Component van de Kern van de Container van de Vorm &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/forms/form-container.html).

De component van de Vorm bepaalt zowel het begin als het eind van een vorm gebruikend het **Begin van de Vorm** en **Eind van de Vorm** elementen. Het begin en einde worden altijd aan elkaar gekoppeld om ervoor te zorgen dat het formulier correct is gedefinieerd.

![&#x200B; dc_form-1 &#x200B;](assets/dc_form-1.png)

Tussen het begin en het einde van een formulier kunt u formuliercomponenten toevoegen die de daadwerkelijke invoervelden voor gebruikers definiëren.

>[!NOTE]
>
>De stichtingscomponenten vormen component slechts steunt het gebruik van andere stichtingscomponenten vormcomponenten (knoop, tekst, verborgen, etc.). Het gebruiken van [&#x200B; kerncomponenten &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) vormcomponenten binnen een vorm van de stichtingscomponent (en omgekeerd) wordt niet gesteund.

#### Begin van formulier {#start-of-form}

Deze component definieert het begin van een nieuw formulier op een pagina. U kunt configureren:

* **Vorm**

   * **Dank u Pagina**

     De pagina waarnaar wordt verwezen om bezoekers te bedanken voor hun invoer. Als het formulier leeg blijft, wordt het na verzending opnieuw weergegeven.

   * **Werkschema van het Begin**

     Hiermee bepaalt u welke workflow wordt geactiveerd wanneer een formulier wordt verzonden.

* **Geavanceerd**

   * **Type van Actie**

     Een formulier heeft een handeling nodig. De handeling definieert de bewerking die wordt geactiveerd voor de uitvoering met de gegevens die door de gebruiker worden verzonden (vergelijkbaar met action= in HTML). Sommige hebben een overeenkomstige **Configuratie van de Actie** nodig.
Een selectie actietypen wordt opgenomen in een standaard AEM-installatie:

      * **Verzoek van de Rekening**
      * **creeer Inhoud**
      * **creeer lood**
      * **creeer en werk Rekening** bij
      * **E-mailDienst: Creeer Abonnee en voeg aan lijst toe**
      * **E-mailDienst: Verzend auto-antwoordapparaat e-mail**
      * **E-mailDienst: Unsubscribe gebruiker van lijst**
      * **geef Gemeenschap** uit
      * **geef Middelen** uit
      * **geef Werkstroom Gecontroleerde Middelen** uit
      * **Post**
      * **Geplaatste Details van de Orde**
      * **Update van het Profiel**
      * **Wachtwoord van het Terugstellen**
      * **plaats Wachtwoord**
      * **Inhoud van de Opslag**

        Het standaardhandelingstype.

      * **Inhoud van de opslag met uploads**
      * **voorleggen orde**
      * **Unsubscribe Subscriber**
      * **orde van de Update**

   * **Identifier van de Vorm**

     De formulier-id vormt een unieke identificatie van het formulier. Gebruik de formulier-id als u meerdere formulieren op één pagina hebt. Zorg ervoor dat deze verschillende id&#39;s hebben.

   * **Weg van de Lading**

     Het pad naar knooppunteigenschappen dat wordt gebruikt om vooraf gedefinieerde waarden in de formuliervelden te laden.

     Een optioneel veld dat het pad naar een knooppunt in de repository aangeeft. Als dit knooppunt eigenschappen heeft die overeenkomen met de veldnamen, worden de desbetreffende velden op het formulier vooraf geladen met de waarde van die eigenschappen. Als er geen overeenkomst bestaat, bevat het veld de standaardwaarde.

     Gebruikend **Weg van de Lading** kunt u de vorm met waarden op de vereiste gebieden vooraf laden. Zie [&#x200B; vooraf ladend de Waarden van de Vorm &#x200B;](/help/sites-developing/developing-forms.md#preloading-form-values).

   * **Bevestiging van de Cliënt**

     Wijst erop of de cliëntbevestiging voor deze vorm (serverbevestiging *altijd* voorkomt) wordt vereist. De bevestiging van de cliënt kan met **worden bereikt Forms Captcha** component.

   * **Type van Middel van Bevestiging**

     Hiermee definieert u het type resource voor formuliervalidatie als u het volledige formulier wilt valideren (in plaats van afzonderlijke velden). Als u het volledige formulier valideert, voert u ook een van de volgende handelingen uit:

      * Een script voor clientvalidatie:

        `/apps/<*myApp*>/form/<*myValidation*>/formclientvalidation.jsp`

      * Een script voor validatie aan de serverzijde:

        `/apps/<*myApp*>/form/<*myValidation*>/formservervalidation.jsp`

   * **Configuratie van de Actie**

     De opties beschikbaar in **Configuratie van de Actie** hangen van het geselecteerde **Type van Actie** af:

      * **Verzoek van de Rekening**

         * **creeer de Pagina van de Rekening**

           De pagina die wordt gebruikt bij het maken van een account.

      * **creeer Inhoud**

         * Inhoudspad

           Het inhoudspad voor alle inhoud die door het formulier wordt neergezet. Voer een pad in dat met een schuine streep `/` eindigt. De slash betekent dat voor elke formulierpoort een nieuw knooppunt wordt gemaakt op de opgegeven locatie, bijvoorbeeld:

           `/forms/feedback/`

         * **Type**

           Selecteer het gewenste type.

         * **Vorm**

           Geef het formulier op.

         * **teruggeeft met**

           Selecteer de gewenste optie in de lijst.

         * **Type van Middel**

           Indien ingesteld, wordt deze aan elke opmerking toegevoegd als `sling:resourceType`

         * **de Selecteur van de Mening**

      * **creeer lood**

         * **Lood wordt toegevoegd aan deze lijst**

           Geef de lijst met vereiste leads op.

      * **creeer en werk Rekening** bij

         * **Aanvankelijke Groep**

           Groep waaraan nieuwe gebruiker moet worden toegewezen.

         * **Huis**

           Pagina die moet worden weergegeven na geslaagde aanmelding.

         * **Weg**

           Het pad (relatief) naar waar de nieuwe account wordt gemaakt en opgeslagen.

         * **Gegevens van de Mening...**

           Als u deze knop selecteert, wordt de informatie over de formulierresultaten weergegeven in de Bulk-editor. Van hieruit kunt u de informatie exporteren naar een `.tsv` (met tabs gescheiden) bestand (bijvoorbeeld in een Excel-spreadsheet).

      * **Post**

         * **van**

           Voer het e-mailadres in waaruit het e-mailadres moet komen.

         * **Brievenbus**

           Voer een of meer e-mailadressen in waarnaar het formulier wordt verzonden.

         * **CC**

           Voer een of meer CC-e-mailadressen in.

         * **BCC**

           Voer een of meer BCC-e-mailadressen in.

         * **Onderwerp**

           Voer een onderwerp voor de e-mail in.

      * **Wachtwoord van het Terugstellen**

         * **de Pagina van het Wachtwoord van de Verandering**

           De pagina die wordt gebruikt bij het wijzigen van het wachtwoord.

      * **Inhoud van de Opslag**

         * **Pad van de Inhoud**

           Het inhoudspad voor alle inhoud die door het formulier wordt neergezet. Voer een pad in dat met een schuine streep `/` eindigt. De slash betekent dat voor elke formulierpoort een nieuw knooppunt wordt gemaakt op de opgegeven locatie, bijvoorbeeld:
           `/forms/feedback/`

         * **Gegevens van de Mening...**

           Klik op deze knop om de informatie over de formulierresultaten te bekijken in de Bulk-editor. Van hieruit kunt u de informatie exporteren naar een .tsv-bestand (gescheiden door tabs) (bijvoorbeeld voor gebruik in een Excel-spreadsheet).

      * **de Inhoud van de opslag met uploads**

        Heeft de zelfde opties zoals **Inhoud van de Opslag**.

      * **Unsubscribe Subscriber**

         * **Lood wordt geschrapt van deze lijst**

           Geef de lijst met vereiste leads op.

#### Einde van formulier {#end-of-form}

Hiermee markeert u het einde van het formulier. U kunt het volgende configureren:

* **Eind van de Vorm**

   * **tonen voorleggen Knoop**

     Geeft aan of een knop Verzenden moet worden weergegeven.

   * **voorlegt Naam**

     Een id als u meerdere verzendknoppen in een formulier gebruikt.

   * **voorlegt Titel**

     De naam die op de knop wordt weergegeven, zoals Verzenden of Verzenden.

   * **toon de Knoop van het Terugstellen**

     Als u het selectievakje inschakelt, wordt de knop Herstellen zichtbaar.

   * **Titel van het Terugstellen**

     De naam die wordt weergegeven op de knop Herstellen.

   * **Beschrijving**

     Informatie die onder de knop wordt weergegeven.

### Accountnaam {#account-name}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe adviseert in plaats hiervan het gebruiken van de [&#x200B; Component van de Kern van de Tekst van de Vorm &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/forms/form-text.html).

Hiermee kan de gebruiker een accountnaam invoeren:

![&#x200B; dc_form_accountname &#x200B;](assets/dc_form_accountname.png)

### Adres {#address}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe adviseert in plaats hiervan het gebruiken van de [&#x200B; Component van de Kern van de Tekst van de Vorm &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/forms/form-text.html).

Hiermee kunt u een internationaal adresveld met de volgende notatie toevoegen:

![&#x200B; dc_form_addressfield &#x200B;](assets/dc_form_addressfield.png)

De component wordt gevormd voor onmiddellijk gebruik, maar u kunt de configuratie veranderen, indien nodig. Bijvoorbeeld, kunnen de beperkingen voor de individuele elementen van het adres worden toegevoegd. Als u velden leeg laat, worden de standaardinstellingen gebruikt.

### Captcha {#captcha}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe adviseert in plaats daarvan gebruikend de [&#x200B; Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html).

>[!CAUTION]
>
>Van deze component wordt niet meer verwacht om buiten-van-de-doos zonder uitgebreide project-vlakke aanpassing te functioneren.

De component Captcha vereist dat de gebruiker een alfanumerieke tekenreeks typt zoals deze op het scherm wordt weergegeven. De tekenreeks verandert bij elke vernieuwing.

![&#x200B; dc_form_captcha &#x200B;](assets/dc_form_captcha.png)

U kunt diverse parameters voor deze component vormen, met inbegrip van een bericht dat moet worden getoond wanneer het koord captcha ongeldig is.

### Groep selectievakjes {#checkbox-group}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe adviseert in plaats daarvan gebruikend de [&#x200B; Component van de Component van de Kern van de Opties van de Vorm &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/forms/form-options.html).

Met een selectievakje kunt u een lijst maken van een of meer selectievakjes, waarvan er meerdere tegelijk kunnen worden geselecteerd.

![&#x200B; dc_form_checkboxgroupuse &#x200B;](assets/dc_form_checkboxgroupuse.png)

U kunt verschillende parameters opgeven, zoals een titel, beschrijving en elementnaam. Met de knoppen + en - kunt u items toevoegen of verwijderen en deze vervolgens met de pijl-omhoog en -omlaag plaatsen.

>[!NOTE]
>
>Gebruikend **Pad van de Lading van Punten** kunt u de lijst van de controledoos groep met waarden vooraf laden.
>
>Zie [&#x200B; het Voorladen van de Gebieden van de Vorm met Veelvoudige Waarden &#x200B;](/help/sites-developing/developing-forms.md#preloading-form-fields-with-multiple-values).

### Creditcardgegevens {#credit-card-details}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe adviseert in plaats daarvan gebruikend de [&#x200B; Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html).

Hier geeft u de velden op die nodig zijn voor het invoeren van creditcardgegevens. U kunt het vormen om de types van toegelaten kaart en de vereiste informatie (bijvoorbeeld, veiligheidscode) te specificeren.

![&#x200B; chlimage_1-100 &#x200B;](assets/chlimage_1-100.png)

### Vervolgkeuzelijst {#dropdown-list}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe adviseert in plaats daarvan gebruikend de [&#x200B; Component van de Component van de Kern van de Opties van de Vorm &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/forms/form-options.html).

Een vervolgkeuzelijst kan worden geconfigureerd om een reeks waarden voor selectie aan uw gebruik te bieden:

![&#x200B; dc_form_dropdownlistuse &#x200B;](assets/dc_form_dropdownlistuse.png)

U kunt een titel en items opgeven die in de lijst moeten worden weergegeven. Met de knoppen + en - kunt u de lijstitems toevoegen of verwijderen en deze vervolgens plaatsen met de knoppen Omhoog en Omlaag. U kunt opgeven of gebruikers meerdere items in de lijst mogen selecteren en items die automatisch moeten worden geselecteerd wanneer ze de lijst voor de eerste keer openen (oorspronkelijke waarden).

>[!NOTE]
>
>Gebruikend **Pad van de Lading van Punten** kunt u de drop-down lijst met waarden vooraf laden.
>
>Zie [&#x200B; het Voorladen van de Gebieden van de Vorm met Veelvoudige Waarden &#x200B;](/help/sites-developing/developing-forms.md#preloading-form-fields-with-multiple-values).

### Bestand uploaden {#file-upload}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe adviseert in plaats daarvan gebruikend de [&#x200B; Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html).

De component voor het uploaden van bestanden biedt de gebruiker een mechanisme voor het selecteren en uploaden van een bestand.

![&#x200B; dc_form_fileupload &#x200B;](assets/dc_form_fileupload.png)

>[!NOTE]
>
>U kunt een aangepaste uploadcomponent maken om bestanden te uploaden naar een verkoopserver. Voor informatie, zie [&#x200B; Uploading dossiers aan Adobe Experience Manager &#x200B;](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/aem-cloud-service-create-asset-servlet-for-uploading-small-files/td-p/404276).

### Verborgen veld {#hidden-field}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe adviseert in plaats hiervan het gebruiken van de [&#x200B; Verborgen Component van de Kern van de Vorm &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/forms/form-hidden.html).

Hiermee kunt u een verborgen veld maken. Deze verborgen velden kunnen voor verschillende doeleinden worden gebruikt. Bijvoorbeeld wanneer u een actie moet uitvoeren nadat u het formulier hebt verzonden of wanneer verborgen gegevens vereist zijn tijdens de naverwerking.

![&#x200B; dc_form_hiddenfield &#x200B;](assets/dc_form_hiddenfield.png)

>[!NOTE]
>
>U kunt het formulier ook aanpassen om specifieke formuliercomponenten weer te geven of te verbergen op basis van de waarde van andere velden in het formulier. Het is handig de zichtbaarheid van een formulierveld te wijzigen als het veld alleen onder bepaalde omstandigheden nodig is.
>
>Zie [&#x200B; tonen en Hiding de Componenten van de Vorm &#x200B;](/help/sites-developing/developing-forms.md#showing-and-hiding-form-components).

### Afbeeldingsknop {#image-button}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe adviseert in plaats hiervan het gebruiken van de [&#x200B; Component van de Kern van de Knoop van de Vorm &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/forms/form-button.html).

Met een afbeeldingsknop kunt u een knop maken met uw eigen afbeelding en tekst:

![&#x200B; dc_form_imagebutton &#x200B;](assets/dc_form_imagebutton.png)

### Afbeelding uploaden {#image-upload}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe adviseert in plaats daarvan gebruikend de [&#x200B; Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html).

De component voor het uploaden van afbeeldingen biedt de gebruiker een mechanisme voor het selecteren en uploaden van een afbeeldingsbestand.

![&#x200B; dc_form_imageupload &#x200B;](assets/dc_form_imageupload.png)

### Koppelingsveld {#link-field}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe adviseert in plaats daarvan gebruikend de [&#x200B; Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html).

In het koppelingsveld kan de gebruiker een URL opgeven:

![&#x200B; dc_form_link &#x200B;](assets/dc_form_link.png)

Wordt meestal gebruikt voor het agendagebeurtenis, waar dit wordt gebruikt voor het URL-/koppelingsveld van een gebeurtenis.

### Wachtwoordveld {#password-field}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe adviseert in plaats daarvan gebruikend de [&#x200B; Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html).

Hiermee kan de gebruiker zijn wachtwoord invoeren:

![&#x200B; dc_form_password &#x200B;](assets/dc_form_password.png)

### Wachtwoord opnieuw instellen {#password-reset}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe adviseert in plaats daarvan gebruikend de [&#x200B; Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html).

Deze component voorziet uw gebruiker van twee gebieden voor:

* de invoer van een wachtwoord
* herhaalde invoer van het wachtwoord om te controleren of de invoer juist is.

Bij de standaardinstellingen wordt de component als volgt weergegeven:

![&#x200B; dc_password_reset &#x200B;](assets/dc_password_reset.png)

### Groep keuzerondjes {#radio-group}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe adviseert in plaats daarvan gebruikend de [&#x200B; Component van de Component van de Kern van de Opties van de Vorm &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/forms/form-options.html).

Een groep keuzerondjes bevat een lijst met een of meer keuzerondjes, waarvan er slechts één op een bepaald moment kan worden geselecteerd.

U kunt de elementnaam samen met een titel en een beschrijving opgeven. Gebruik de knoppen + en - om items toe te voegen of te verwijderen, plaats deze met de pijlen omhoog en omlaag en geef indien nodig een standaardwaarde op:

![&#x200B; dc_form_radiogroupuse &#x200B;](assets/dc_form_radiogroupuse.png)

>[!NOTE]
>
>Gebruikend **Pad van de Lading van Punten** kunt u de radiobroep met waarden vooraf laden.
>
>Zie [&#x200B; het Voorladen van de Gebieden van de Vorm met Veelvoudige Waarden &#x200B;](/help/sites-developing/developing-forms.md#preloading-form-fields-with-multiple-values).

### Verzendknop {#submit-button}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe adviseert in plaats hiervan het gebruiken van de [&#x200B; Component van de Kern van de Knoop van de Vorm &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/forms/form-button.html).

Met deze component kunt u een verzendknop maken met de standaardtekst:

![&#x200B; dc_form_submitButton &#x200B;](assets/dc_form_submitbutton.png)

Of met uw eigen tekst:

![&#x200B; dc_form_submitButtonuse &#x200B;](assets/dc_form_submitbuttonuse.png)

### Labels veld {#tags-field}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe adviseert in plaats daarvan gebruikend de [&#x200B; Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html).

In dit veld kunt u tags selecteren:

![&#x200B; dc_form_tags_use &#x200B;](assets/dc_form_tags_use.png)

U kunt verschillende parameters opgeven, waaronder de naamruimten die kunnen worden gebruikt, op het gespecialiseerde tabblad:

* **Gebied van de Markering**

   * **Toegestane Namespaces**

      * **Geometrixx Outdoors**
      * **Workflow**
      * **Forum**
      * **fotografie van de Voorraad**
      * **Geometrixx Media**
      * **StandaardMarkeringen**
      * **Marketing**
      * **Eigenschappen van Activa**
      * **Breedte in pixel**
      * **Popup Grootte**

### Tekstveld {#text-field}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe adviseert in plaats hiervan het gebruiken van de [&#x200B; Component van de Kern van de Tekst van de Vorm &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/forms/form-text.html).

Het standaardtekstveld kan worden geconfigureerd op de gewenste grootte en met uw eigen lead in een bericht:

![&#x200B; dc_form_text &#x200B;](assets/dc_form_text.png)

### Knop(en) voor verzenden werkstroom {#workflow-submit-button-s}

>[!CAUTION]
>
>Deze Foundation-component is vervangen. Adobe adviseert in plaats hiervan het gebruiken van de [&#x200B; Component van de Kern van de Knoop van de Vorm &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/forms/form-button.html).

Hiermee kunt u een knop Verzenden maken voor gebruik in een workflow.

![&#x200B; chlimage_1-101 &#x200B;](assets/chlimage_1-101.png)
