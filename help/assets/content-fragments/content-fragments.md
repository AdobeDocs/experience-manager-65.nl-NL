---
title: Werken met inhoudsfragmenten
description: Leer hoe u met Content Fragments in Adobe Experience Manager (AEM) pagina-onafhankelijke inhoud kunt ontwerpen, maken, beheren en gebruiken, ideaal voor levering zonder kop.
feature: Content Fragments
role: User
exl-id: 0ee883c5-0cea-46b7-a759-600b8ea3bc3e
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1966'
ht-degree: 3%

---

# Werken met inhoudsfragmenten {#working-with-content-fragments}

Met Adobe Experience Manager (AEM), laten de Fragmenten van de Inhoud u, pagina-onafhankelijke inhoud [&#128279;](/help/sites-authoring/content-fragments.md) ontwerpen tot stand brengen, leiden en  publiceren. Hiermee kunt u inhoud voorbereiden en gebruiken op meerdere locaties/via meerdere kanalen, ideaal voor levering zonder kop.

Inhoudsfragmenten bevatten gestructureerde inhoud:

* Zij zijn gebaseerd op het Model van het Fragment van de a [ Inhoud ](/help/assets/content-fragments/content-fragments-models.md), dat vooraf een structuur voor het resulterende fragment bepaalt.
* De structuur kan liggen tussen:
   * Basis
      * Bijvoorbeeld een tekstveld met één regel tekst.
      * Wordt gebruikt voor het voorbereiden van eenvoudige inhoud voor gebruik in paginaontwerp.
   * Complex
      * Een combinatie van een groot aantal velden met verschillende gegevenstypen, zoals tekst, getal, boolean, gegevens en tijd.
      * Wordt gebruikt voor het voorbereiden van gestructureerde inhoud voor het ontwerpen van pagina&#39;s of voor levering aan uw toepassing.
   * Genest
      * Met de beschikbare gegevenstypen kunt u de inhoud nesten.
      * Dit wordt doorgaans gebruikt voor levering aan uw toepassing.

Inhoudsfragmenten kunnen ook worden geleverd in JSON-indeling, waarbij gebruik wordt gemaakt van de JSON-exportmogelijkheden (Sling Model) van AEM kerncomponenten. Deze leveringsvorm:

* biedt u de mogelijkheid om de component te gebruiken om te beheren welke elementen van een fragment moeten worden geleverd
* staat bulklevering toe, door veelvoudige inhoudfragment kerncomponenten op de pagina toe te voegen die voor levering API wordt gebruikt

Deze en de volgende pagina&#39;s bevatten de taken voor het maken, configureren, onderhouden en gebruiken van uw inhoudsfragmenten:

* [Functionaliteit van inhoudsfragment inschakelen voor uw instantie](/help/assets/content-fragments/content-fragments-configuration-browser.md)
* [ Modellen van het Fragment van de Inhoud ](/help/assets/content-fragments/content-fragments-models.md) - toelatend, creërend, en bepalend uw modellen
* [ het Leiden de Fragmenten van de Inhoud ](/help/assets/content-fragments/content-fragments-managing.md) - creeer uw inhoudsfragmenten; dan geef, publiceer, en verwijzing uit
* [ Variaties - het Authoring Inhoud van het Fragment ](/help/assets/content-fragments/content-fragments-variations.md) - auteur de fragmentinhoud en creeer variaties van de Meester
* [ Markering ](/help/assets/content-fragments/content-fragments-markdown.md) - het gebruiken van prijsdalingssyntaxis voor uw fragment
* [ Gebruikend Bijbehorende Inhoud ](/help/assets/content-fragments/content-fragments-assoc-content.md) - toevoegend bijbehorende inhoud
* [ Meta-gegevens - de Eigenschappen van het Fragment ](/help/assets/content-fragments/content-fragments-metadata.md) - het bekijken van en het uitgeven van de fragmenteigenschappen
* Gebruik [ de Fragmenten van de Inhoud, samen met GraphQL, om inhoud ](/help/assets/content-fragments/content-fragments-graphql.md) voor gebruik in uw toepassingen te leveren. Om met dit te helpen, kunt u voorproef [ output JSON ](/help/assets/content-fragments/content-fragments-json-preview.md).

>[!NOTE]
>
>Deze pagina&#39;s kunnen worden gelezen met:
>
>* [ het Authoring van de Pagina met de Fragmenten van de Inhoud ](/help/sites-authoring/content-fragments.md).
>* [Contentfragmenten aanpassen en uitbreiden](/help/sites-developing/customizing-content-fragments.md)
>* [Contentfragmenten die componenten voor rendering configureren](/help/sites-developing/content-fragments-config-components-rendering.md)
>* [Ondersteuning voor contentfragmenten in HTTP-API van AEM Assets](/help/assets/assets-api-content-fragments.md)
>* [ AEM GraphQL API voor gebruik met de Fragmenten van de Inhoud ](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md)

Het aantal communicatiekanalen neemt jaarlijks toe. Doorgaans verwijzen kanalen naar het leveringsmechanisme, als:

* Fysiek kanaal, bijvoorbeeld desktop, mobiel.
* Leveringsvorm via een fysiek kanaal, bijvoorbeeld de pagina met productdetails, de pagina met productcategorieën voor desktops of de pagina Mobiel web en de pagina Mobiele apps voor mobiele apparaten.

(Waarschijnlijk) wilt u echter niet voor alle kanalen dezelfde inhoud gebruiken. U moet de inhoud optimaliseren op basis van het specifieke kanaal.

Met inhoudsfragmenten kunt u:

* Overweeg hoe u doelpubliek efficiënt langs verschillende kanalen kunt bereiken.
* Kanaalneutrale redactionele inhoud maken en beheren.
* Stel inhoudsgroepen samen voor een reeks kanalen.
* Ontwerpinhoudvariaties voor specifieke kanalen.
* Voeg afbeeldingen aan de tekst toe door elementen (gemengde-mediafragmenten) in te voegen.
* Maak geneste inhoud, zodat u de complexiteit van uw gegevens kunt weerspiegelen.

Deze inhoudsfragmenten kunnen vervolgens worden samengevoegd om via verschillende kanalen ervaringen op te doen.

>[!NOTE]
>
>**de Fragmenten van de Inhoud** en **[Fragmenten van de Ervaring](/help/sites-authoring/experience-fragments.md)** zijn verschillende eigenschappen binnen AEM:
>
>* **de Fragmenten van de Inhoud** zijn redactionele inhoud die kan worden gebruikt om tot gestructureerde gegevens met inbegrip van teksten, aantallen, en data, onder anderen toegang te hebben. Het zijn pure inhoud, met definitie en structuur, maar zonder extra visueel ontwerp en/of lay-out.
>
>* **de Fragmenten van de Ervaring** zijn volledig opgemaakt inhoud; een fragment van een Web-pagina.
>
>De Fragmenten van de ervaring kunnen inhoud in de vorm van Inhoudsfragmenten bevatten, maar niet andersom.
>
>Voor meer informatie, zie [ Begrip van de Fragmenten van de Inhoud en de Fragmenten van de Ervaring in AEM ](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/content-fragments/understand-content-fragments-and-experience-fragments.html?lang=nl-NL#content-fragments).

>[!NOTE]
>
>Vóór AEM 6.3, werden de Fragmenten van de Inhoud gecreeerd met het gebruik van malplaatjes in plaats van modellen. Sjablonen zijn niet meer beschikbaar voor het maken van fragmenten, maar fragmenten die met een dergelijke sjabloon zijn gemaakt, worden wel ondersteund.

## Inhoudsfragmenten en inhoudsservices {#content-fragments-and-content-services}

AEM Content Services zijn ontworpen om de beschrijving en levering van inhoud in of vanuit AEM te veralgemenen, waarbij de aandacht niet op webpagina&#39;s wordt gevestigd.

Zij verstrekken de levering van inhoud aan kanalen die niet traditionele AEM Web-pagina&#39;s zijn, gebruikend gestandaardiseerde methodes die door om het even welke cliënt kunnen worden gebruikt. Deze kanalen kunnen zijn:

* Toepassingen voor één pagina
* Systeemeigen mobiele toepassingen
* andere kanalen en aanraakpunten buiten AEM

De levering wordt uitgevoerd in JSON-indeling met behulp van de JSON Exporter.

AEM Inhoudsfragmenten kunnen worden gebruikt om gestructureerde inhoud te beschrijven en te beheren. Gestructureerde inhoud wordt gedefinieerd in modellen die verschillende inhoudstypen kunnen bevatten, zoals tekst, numerieke gegevens, booleaanse gegevens, datum en tijd en meer.

Samen met de JSON-exportmogelijkheden van AEM kerncomponenten kan deze gestructureerde inhoud vervolgens worden gebruikt om AEM inhoud aan andere kanalen dan AEM pagina&#39;s te leveren.

<!--
>[!NOTE]
>
>See [Headless and AEM](/help/implementing/developing/headless/introduction.md) for an introduction to Headless Development for AEM Sites.
-->

>[!NOTE]
>
>AEM ondersteunt ook het vertalen van fragmentinhoud.

<!--
>[!NOTE]
>
>AEM also supports the translation of fragment content. See [Translating Assets](/help/assets/translate-assets.md) for further information.
-->

## Inhoudstype {#content-type}

Inhoudsfragmenten zijn:

* Opgeslagen als **Assets**:

   * De fragmenten van de inhoud (en hun variaties) kunnen van de **Assets** console worden gecreeerd en worden gehandhaafd.
   * Gemaakt en bewerkt in de Inhoudsfragmenteditor.

* Gebruikt in de [ paginaredacteur met de component van het Fragment van de Inhoud ](/help/sites-authoring/content-fragments.md) (van verwijzingen voorzien component):

   * De **component van het Fragment van 0&rbrace; Inhoud &lbrace;is beschikbaar aan paginaauteurs.** Hiermee kunnen ze naar het vereiste inhoudsfragment verwijzen en dit leveren in HTML- of JSON-indeling.

* Toegankelijk gebruikend [ AEM GraphQL API ](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md).

Inhoudsfragmenten zijn een inhoudsstructuur die:

* Geen lay-out of ontwerp hebben (enige tekstopmaak is mogelijk in de modus RTF).
* Heb één of meerdere [ samenstellende delen ](#constituent-parts-of-a-content-fragment).
* Kan [ bevatten, of met, beelden ](#fragments-with-visual-assets) worden verbonden.
* Kan [ binnen-tussen inhoud ](#in-between-content-when-page-authoring-with-content-fragments) gebruiken wanneer van verwijzingen voorzien op een pagina.
* Zijn onafhankelijk van het leveringsmechanisme (namelijk pagina, kanaal).

### Fragmenten met Visual Assets {#fragments-with-visual-assets}

Om auteurs meer controle over hun inhoud te geven, kunnen afbeeldingen worden toegevoegd aan en/of geïntegreerd met een inhoudsfragment.

Assets kan op verschillende manieren worden gebruikt met een inhoudsfragment. Elk van deze mogelijkheden heeft zijn eigen voordelen:

* **Activa van het Tussenvoegsel** in een fragment (gemengd-media fragmenten)

   * Zijn een deel van het fragment (zie [ Componentdelen van een tevreden fragment ](#constituent-parts-of-a-content-fragment)).
   * De positie van het element definiëren.
   * Zie [ Invoegend Assets in uw Fragment ](/help/assets/content-fragments/content-fragments-variations.md#inserting-assets-into-your-fragment) in de Redacteur van het Fragment voor meer informatie.

  >[!NOTE]
  >
  >Visuele elementen die in het inhoudsfragment zelf worden ingevoegd, worden aan de voorafgaande alinea gekoppeld. Wanneer het fragment aan een pagina wordt toegevoegd, worden deze elementen ten opzichte van die alinea verplaatst wanneer tussenliggende inhoud wordt toegevoegd.

* **Verwante Inhoud**

   * Wordt verbonden met een fragment; maar geen vast deel van het fragment (zie [ Componentdelen van een inhoudsfragment ](#constituent-parts-of-a-content-fragment)).
   * Biedt enige flexibiliteit voor positionering.
   * U kunt het fragment gemakkelijk gebruiken (als tussenliggende inhoud) op een pagina.
   * Zie [ Geassocieerde Inhoud ](/help/assets/content-fragments/content-fragments-assoc-content.md) voor meer informatie.

* Assets die beschikbaar zijn in de **assetbrowser** van de pagina-editor

   * Volledige flexibiliteit toestaan voor de selectie van een element.
   * Biedt enige flexibiliteit voor positionering.
   * Bevat niet het concept dat voor een specifiek fragment wordt goedgekeurd.

<!--
  * See [Assets Browser](/help/sites-authoring/environment-tools.md#assets-browser) for more information.
-->

### Delen van een inhoudsfragment maken {#constituent-parts-of-a-content-fragment}

De elementen van het inhoudsfragment bestaan uit de volgende onderdelen (direct of indirect):

* **Elementen van het Fragment**

   * Elementen correleren met de gegevensvelden die inhoud bevatten.
   * U gebruikt een inhoudsmodel om het inhoudsfragment te maken. De elementen (velden) die in het model zijn opgegeven, definiëren de structuur van het fragment. Deze elementen (velden) kunnen van verschillende gegevenstypen zijn.

* **Fragmentalinea&#39;s**

   * Blokken tekst vaak meerdere regels die zijn gescheiden als afzonderlijke entiteiten.

   * In de modi [Tekst met opmaak](/help/assets/content-fragments/content-fragments-variations.md#rich-text) en [Markdown](/help/assets/content-fragments/content-fragments-variations.md#markdown) kan een alinea worden opgemaakt als een koptekst. In dat geval horen die alinea en de volgende alinea bij elkaar als één eenheid.

   * Inhoudsbeheer tijdens het ontwerpen van pagina&#39;s inschakelen.

* **Assets die in een Fragment (Gemengd-Media Fragments) wordt opgenomen**

   * Assets (afbeeldingen) ingevoegd in het feitelijke fragment en gebruikt als de interne inhoud van een fragment.
   * zijn ingesloten in het alineasysteem van het fragment.
   * Kan worden geformatteerd wanneer het [ fragment wordt gebruikt/op een pagina ](/help/sites-authoring/content-fragments.md) van verwijzingen wordt voorzien.
   * Kan alleen met de fragmenteditor worden toegevoegd aan, verwijderd uit of verplaatst binnen een fragment. Deze handelingen kunnen niet worden uitgevoerd in de paginaeditor.
   * Kan slechts aan, worden toegevoegd geschrapt van, of binnen, een fragment gebruikend het [ Rich formaat van de Tekst in de fragmentredacteur ](/help/assets/content-fragments/content-fragments-variations.md#inserting-assets-into-your-fragment) worden bewogen.
   * Kan alleen worden toegevoegd aan tekstelementen met meerdere regels (elk fragmenttype).
   * Aan de voorgaande tekst (alinea) worden toegevoegd.

     >[!CAUTION]
     >
     >Assets kan (per ongeluk) uit een fragment worden verwijderd door over te schakelen op de indeling Onbewerkte tekst.

     >[!NOTE]
     >
     >Assets kan ook als [ extra (in-tussen) inhoud ](/help/sites-authoring/content-fragments.md#using-associated-content) worden toegevoegd wanneer het gebruiken van een fragment op een pagina; het gebruiken van of Geassocieerde Inhoud of activa van browser van Assets.

* **Verwante Inhoud**

   * Dit is inhoud die zich buiten een fragment bevindt, maar die van redactionele betekenis is. Afbeeldingen, video&#39;s of andere fragmenten worden meestal weergegeven.
   * De afzonderlijke elementen in de verzameling zijn beschikbaar voor gebruik met het fragment in de pagina-editor wanneer het aan een pagina wordt toegevoegd. Dit betekent dat ze optioneel zijn, afhankelijk van de vereisten van het specifieke kanaal.
   * De activa worden [ geassocieerd aan fragmenten via inzamelingen ](/help/assets/content-fragments/content-fragments-assoc-content.md); de bijbehorende inzamelingen staan de auteur toe om te beslissen welke activa te gebruiken wanneer zij de pagina ontwerpen.

      * Verzamelingen kunnen tijdens het ontwerpen van fragmenten als standaardinhoud worden gekoppeld.
      * [ Assets (DAM) Inzamelingen ](/help/assets/manage-collections.md) zijn de basis voor de bijbehorende inhoud van fragmenten.
   * Desgewenst kunt u het fragment zelf ook aan een verzameling toevoegen om het bijhouden van het fragment te vergemakkelijken.

* **Metagegevens van het Fragment**

   * Gebruik de [ schema&#39;s van de meta-gegevens van Assets ](/help/assets/metadata-schemas.md).
   * Tags kunnen worden gemaakt wanneer u:

      * Het fragment maken en ontwerpen
      * of hoger:

         * Door het fragment **Eigenschappen** van de console te bekijken/uit te geven
         * Door **Meta-gegevens** te uitgeven wanneer in de fragmentredacteur

  >[!CAUTION]
  >
  >Metagegevensverwerkingsprofielen zijn niet van toepassing op inhoudsfragmenten.

* **Meester**

   * Een deel van het fragment

      * Elk inhoudsfragment heeft één instantie van Master.
      * Stramien kan niet worden verwijderd.

   * Het hoofd is toegankelijk in de fragmentredacteur onder **[Variaties](/help/assets/content-fragments/content-fragments-variations.md)**.
   * Stramien is geen variatie als zodanig, maar is de basis van alle variaties.

* **Variaties**

   * Uitvoeringen van fragmenttekst die specifiek zijn voor een redactioneel doel; kan gerelateerd zijn aan een kanaal, maar is niet verplicht, kunnen ook voor lokale ad-hocwijzigingen worden gebruikt.
   * Wordt gecreeerd als exemplaren van **Hoofd**, maar kan dan worden uitgegeven zoals vereist; er is inhoudsoverlap tussen de variaties zelf.
   * Kan worden gedefinieerd tijdens het ontwerpen van fragmenten.
   * Opgeslagen in het fragment, om spreiding van inhoudskopieën te voorkomen.
   * De variaties kunnen [&#128279;](/help/assets/content-fragments/content-fragments-variations.md#synchronizing-with-master) met Hoofd worden gesynchroniseerd als de Hoofdinhoud is bijgewerkt.
   * Kan [ worden samengevat ](/help/assets/content-fragments/content-fragments-variations.md#summarizing-text) om de tekst aan een vooraf bepaalde lengte snel te beknotten.
   * Beschikbaar onder het [ lusje van Variaties ](/help/assets/content-fragments/content-fragments-variations.md) van de fragmentredacteur.

### Tussen inhoud wanneer pagina&#39;s worden gemaakt met inhoudsfragmenten {#in-between-content-when-page-authoring-with-content-fragments}

Tussenliggende inhoud:

* Is beschikbaar voor gebruik in de Redacteur van de Pagina wanneer het werken met tevreden Fragments.
* Is [ extra inhoud toegevoegd binnen de stroom van een fragment ](/help/sites-authoring/content-fragments.md#adding-in-between-content) zodra het is gebruikt of op een pagina van verwijzingen voorzien.
* Is beschikbaar voor gebruik in de [ Redacteur van de Pagina wanneer het werken met Inhoudsfragmenten ](/help/sites-authoring/content-fragments.md).
* Tussen-inhoud kan aan elk fragment worden toegevoegd, waarbij slechts één element zichtbaar is.
* De bijbehorende inhoud kan worden gebruikt, evenals activa en/of componenten van aangewezen browser.

>[!CAUTION]
>
>De tussenliggende inhoud is pagina-inhoud. Deze wordt niet opgeslagen in het inhoudsfragment.

### Vereist door fragmenten {#required-by-fragments}

Houd rekening met het volgende als u inhoudsfragmenten wilt maken:

* **Model van de Inhoud**

   * Zijn [ toegelaten gebruikend Browser van de Configuratie ](/help/assets/content-fragments/content-fragments-configuration-browser.md).
   * Wordt [ gecreeerd gebruikend Hulpmiddelen ](/help/assets/content-fragments/content-fragments-models.md).
   * Vereist om [ tot een fragment ](/help/assets/content-fragments/content-fragments-managing.md#creating-content-fragments) te leiden.
   * Definieert de structuur van een fragment (titel, inhoudselementen, tagdefinities).
   * Definities van inhoudsmodellen vereisen een titel en één gegevenselement. Alle andere opties zijn optioneel.
   * Het model kan de standaardinhoud definiëren, indien van toepassing.
   * Auteurs kunnen de gedefinieerde structuur niet wijzigen tijdens het ontwerpen van fragmentinhoud.
   * Wijzigingen die worden aangebracht in een model nadat afhankelijke inhoudsfragmenten zijn gemaakt, kunnen van invloed zijn op die inhoudsfragmenten.

Als u de Content Fragments wilt gebruiken voor het ontwerpen van pagina&#39;s, hebt u ook het volgende nodig:

* **Component van het Fragment van de Inhoud**

   * Instrumentaal voor het leveren van het fragment in de indeling HTML en/of JSON.
   * Vereist om [ het fragment op een pagina ](/help/sites-authoring/content-fragments.md) van verwijzingen te voorzien.
   * Verantwoordelijk voor de lay-out en levering van een fragment, dat wil zeggen, kanalen.
   * Fragmenten hebben een of meer specifieke componenten nodig om de lay-out te definiëren en om enkele of alle elementen/variaties en bijbehorende inhoud te leveren.
   * Wanneer u een fragment naar een pagina sleept in de ontwerpfase, wordt de vereiste component automatisch gekoppeld.

## Voorbeeldengebruik {#example-usage}

Een fragment met de elementen en variaties kan worden gebruikt om coherente inhoud voor meerdere kanalen te maken. Bij het ontwerpen van het fragment moet u rekening houden met wat wordt gebruikt en waar het wordt gebruikt.
