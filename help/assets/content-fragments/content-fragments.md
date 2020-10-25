---
title: Werken met contentfragmenten
seo-title: Werken met contentfragmenten
description: Leer hoe u met Inhoudsfragmenten pagina-onafhankelijke inhoud kunt ontwerpen, maken, beheren en gebruiken.
seo-description: Leer hoe u met Inhoudsfragmenten pagina-onafhankelijke inhoud kunt ontwerpen, maken, beheren en gebruiken.
uuid: d35d5638-43a9-424d-9806-6e8d459980d7
contentOwner: Alison Heimoz
topic-tags: content-fragments
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
content-type: reference
discoiquuid: 7ecc1bcf-38a9-4a59-8dd3-79cb90dec33d
docset: aem65
translation-type: tm+mt
source-git-commit: 0d5a48be283484005013ef3ed7ad015b43f6398b
workflow-type: tm+mt
source-wordcount: '1973'
ht-degree: 3%

---


# Werken met contentfragmenten{#working-with-content-fragments}

Met Adobe Experience Manager (AEM) Content Fragments kunt u pagina-onafhankelijke inhoud [ontwerpen, maken, beheren en](/help/sites-authoring/content-fragments.md)publiceren. Hiermee kunt u inhoud voorbereiden die klaar is voor gebruik op meerdere locaties/via meerdere kanalen.

Inhoudsfragmenten kunnen ook worden geleverd in JSON-indeling, waarbij gebruik wordt gemaakt van de JSON-exportmogelijkheden (Sling Model) van AEM kerncomponenten. Deze leveringsvorm:

* biedt u de mogelijkheid om de component te gebruiken om te beheren welke elementen van een fragment moeten worden geleverd
* staat bulklevering toe, door veelvoudige inhoudfragment kerncomponenten op de pagina toe te voegen die voor levering API wordt gebruikt

Deze en de volgende pagina&#39;s bevatten de taken voor het maken, configureren en onderhouden van uw inhoudsfragmenten:

* [Inhoudsfragmenten](/help/assets/content-fragments/content-fragments-managing.md) beheren: maak inhoudsfragmenten. vervolgens bewerken, publiceren en verwijzen
* [Modellen](/help/assets/content-fragments/content-fragments-models.md) voor inhoudsfragmenten - uw modellen inschakelen, maken en definiëren
* [Variaties - Fragmentinhoud](/help/assets/content-fragments/content-fragments-variations.md) ontwerpen - de fragmentinhoud ontwerpen en variaties van de Master inhoud maken
* [Markering](/help/assets/content-fragments/content-fragments-markdown.md) - markeringssyntaxis gebruiken voor uw fragment
* [Gekoppelde inhoud](/help/assets/content-fragments/content-fragments-assoc-content.md) gebruiken - gekoppelde inhoud toevoegen
* [Metagegevens - Fragmenteigenschappen](/help/assets/content-fragments/content-fragments-metadata.md) - de fragmenteigenschappen weergeven en bewerken

>[!NOTE]
>
>Deze pagina&#39;s moeten worden gelezen in combinatie met [Paginaontwerp met inhoudsfragmenten](/help/sites-authoring/content-fragments.md).

Het aantal communicatiekanalen neemt jaarlijks toe. Doorgaans verwijzen kanalen naar het leveringsmechanisme, als:

* fysiek kanaal; bijvoorbeeld desktop, mobiel.
* Vorm van levering in een fysiek kanaal; Bijvoorbeeld de pagina met productdetails, de pagina met productcategorieën voor desktops of mobiele websites, de pagina met mobiele apps voor mobiele apparaten.

U (waarschijnlijk) wilt echter niet exact dezelfde inhoud gebruiken voor alle kanalen. U moet de inhoud optimaliseren op basis van het specifieke kanaal.

Met inhoudelementen kunt u:

* Overweeg hoe u doelpubliek efficiënt langs verschillende kanalen kunt bereiken.
* Kanaalneutrale redactionele inhoud maken en beheren.
* Stel inhoudsgroepen samen voor een reeks kanalen.
* Ontwerpinhoudvariaties voor specifieke kanalen.
* Voeg afbeeldingen aan uw tekst toe door elementen (gemengde-mediafragmenten) in te voegen.

Deze inhoudsfragmenten kunnen vervolgens worden samengevoegd om via verschillende kanalen ervaringen op te doen.

## Inhoudsfragmenten en inhoudsservices {#content-fragments-and-content-services}

AEM Content Services zijn ontworpen om de beschrijving en levering van inhoud in of vanuit AEM te veralgemenen, waarbij de aandacht niet op webpagina&#39;s wordt gevestigd.

Zij verstrekken de levering van inhoud aan kanalen die niet traditionele AEM Web-pagina&#39;s zijn, gebruikend gestandaardiseerde methodes die door om het even welke cliënt kunnen worden verbruikt. Deze kanalen kunnen zijn:

* Toepassingen voor één pagina
* Systeemeigen mobiele toepassingen
* andere kanalen en aanraakpunten buiten AEM

De levering wordt uitgevoerd in JSON-indeling.

AEM Inhoudsfragmenten kunnen worden gebruikt om gestructureerde inhoud te beschrijven en te beheren. Gestructureerde inhoud wordt gedefinieerd in modellen die verschillende inhoudstypen kunnen bevatten; waaronder tekst, numerieke gegevens, booleaanse gegevens, datum en tijd en meer.

Samen met de JSON-exportmogelijkheden van AEM kerncomponenten kan deze gestructureerde inhoud vervolgens worden gebruikt om AEM inhoud aan andere kanalen dan AEM pagina&#39;s te leveren.

>[!NOTE]
>
>**Inhoudsfragmenten** en **[ervaringsfragmenten](/help/sites-authoring/experience-fragments.md)** hebben verschillende functies in AEM:
>* **Inhoudsfragmenten** zijn redactionele inhoud, voornamelijk tekst en verwante afbeeldingen. Het zijn pure inhoud, zonder ontwerp en lay-out.
>* **de inhoud van de ervaringsfragmenten** volledig wordt ingedeeld; een fragment van een webpagina.

>
>
De Fragmenten van de ervaring kunnen inhoud in de vorm van Inhoudsfragmenten bevatten, maar niet andersom.
>
>Voor meer informatie zie ook het [Begrijpen van de Fragmenten van de Inhoud en de Fragmenten van de Ervaring in AEM](https://docs.adobe.com/content/help/en/experience-manager-learn/sites/content-fragments/understand-content-fragments-and-experience-fragments.html).

>[!CAUTION]
>
>Inhoudsfragmenten zijn niet beschikbaar in de klassieke UI.
>
>De component van het Fragment van de Inhoud kan in klassieke UI hulpje worden gezien, maar de verdere functionaliteit is niet beschikbaar.

>[!NOTE]
>
>AEM ondersteunt ook het vertalen van fragmentinhoud. Zie [Vertaalprojecten maken voor inhoudsfragmenten](/help/assets/creating-translation-projects-for-content-fragments.md) voor meer informatie.

## Typen inhoudsfragmenten {#types-of-content-fragment}

Inhoudsfragmenten kunnen:

* Eenvoudige fragmentenDeze hebben geen vooraf gedefinieerde structuur. Ze bevatten alleen tekst en afbeeldingen.
Deze zijn gebaseerd op de sjabloon Eenvoudig fragment.

* Fragmenten die gestructureerde inhoud bevatten. Deze fragmenten zijn gebaseerd op een [inhoudsfragmentmodel](/help/assets/content-fragments/content-fragments-models.md), dat een structuur vooraf definieert voor het resulterende fragment.
Deze kunnen ook worden gebruikt om Content Services te realiseren met behulp van JSON Exporter.

## Inhoudstype {#content-type}

Inhoudsfragmenten zijn:

* Opgeslagen als **elementen**:

   * Inhoudsfragmenten (en hun variaties) kunnen worden gemaakt en onderhouden vanaf de **middelenconsole** .
   * Gemaakt en bewerkt in de Inhoudsfragmenteditor.

* Wordt gebruikt in de [pagina-editor door middel van de component](/help/sites-authoring/content-fragments.md) Inhoudsfragment (verwijzende component):

   * De component **Inhoudsfragment** is beschikbaar voor auteurs van pagina&#39;s. Hiermee kunnen ze naar het vereiste inhoudsfragment verwijzen en dit leveren in HTML- of JSON-indeling.

Inhoudsfragmenten zijn een inhoudsstructuur die:

* Zijn zonder lay-out of ontwerp (wat tekst het formatteren is mogelijk op Rich Text wijze).
* Bevat een of meer [onderdelen](#constituent-parts-of-a-content-fragment).
* Kan afbeeldingen [bevatten of hiermee zijn verbonden](#fragments-with-visual-assets).
* Kan [tussenliggende inhoud](#in-between-content-when-page-authoring-with-content-fragments) gebruiken wanneer ernaar wordt verwezen op een pagina.

* zijn onafhankelijk van het leveringsmechanisme (d.w.z. pagina, kanaal).

### Fragmenten met visuele elementen {#fragments-with-visual-assets}

Om auteurs meer controle over hun inhoud te geven, kunnen afbeeldingen worden toegevoegd aan en/of geïntegreerd met een inhoudsfragment.

Elementen kunnen op verschillende manieren met een inhoudsfragment worden gebruikt. elk met zijn eigen voordeel:

* **Element** invoegen in een fragment (gemengde-mediafragmenten)

   * Vormen een integraal onderdeel van het fragment (zie [Componentdelen van een inhoudsfragment](#constituent-parts-of-a-content-fragment)).
   * De positie van het element definiëren.
   * Zie Elementen [invoegen in uw fragment](/help/assets/content-fragments/content-fragments-variations.md#inserting-assets-into-your-fragment) in de fragmenteditor voor meer informatie.

   >[!NOTE]
   >
   >Visuele elementen die in het inhoudsfragment zelf zijn ingevoegd, worden aan de voorafgaande alinea gekoppeld. Wanneer het fragment aan een pagina wordt toegevoegd, worden deze elementen ten opzichte van die alinea verplaatst wanneer tussenliggende inhoud wordt toegevoegd.

* **Gekoppelde inhoud**

   * zijn verbonden met een fragment; maar geen vast deel van het fragment (zie [Delen van een inhoudsfragment](#constituent-parts-of-a-content-fragment)).
   * Biedt enige flexibiliteit voor positionering.
   * U kunt het fragment gemakkelijk gebruiken (als tussenliggende inhoud) op een pagina.
   * Zie [Gekoppelde inhoud](/help/assets/content-fragments/content-fragments-assoc-content.md) voor meer informatie.

* Assets die beschikbaar zijn in de **assetbrowser** van de pagina-editor

   * Volledige flexibiliteit toestaan voor de selectie van een element.
   * Biedt enige flexibiliteit voor positionering.
   * Bevat niet het concept dat voor een specifiek fragment wordt goedgekeurd.
   * Zie [Assets Browser](/help/sites-authoring/author-environment-tools.md#assets-browser) voor meer informatie.

### Delen van een inhoudsfragment maken {#constituent-parts-of-a-content-fragment}

De elementen van het inhoudsfragment bestaan uit de volgende onderdelen (direct of indirect):

* **Fragmentelementen**

   * Elementen correleren met de gegevensvelden die inhoud bevatten.
   * Voor fragmenten met gestructureerde inhoud gebruikt u een inhoudsmodel om het inhoudsfragment te maken. De elementen (velden) die in het model zijn opgegeven, definiëren de structuur van het fragment. Deze elementen (velden) kunnen van verschillende gegevenstypen zijn.
   * Voor eenvoudige fragmenten:

      * De inhoud bevindt zich in een (of meer) tekstveld(en) met meerdere regels of in een of meer elementen.
      * De elementen worden gedefinieerd in de fragmentsjabloon (kan niet worden gedefinieerd tijdens het ontwerpen van het fragment, zie [Inhoudsfragmentsjablonen](/help/sites-developing/content-fragment-templates.md)).

* **Fragmentalinea&#39;s**

   * Tekstblokken, dat wil zeggen:

      * gescheiden door verticale spaties (harde return)
      * in tekstelementen met meerdere regels; in eenvoudige of gestructureerde fragmenten
   * In de modi [Tekst met opmaak](/help/assets/content-fragments/content-fragments-variations.md#rich-text) en [Markdown](/help/assets/content-fragments/content-fragments-variations.md#markdown) kan een alinea worden opgemaakt als een koptekst. In dat geval horen die alinea en de volgende alinea bij elkaar als één eenheid.

   * Inhoudsbeheer tijdens het ontwerpen van pagina&#39;s inschakelen.


* **Elementen die in een fragment zijn ingevoegd (gemengde-mediafragmenten)**

   * Elementen (afbeeldingen) die in het feitelijke fragment zijn ingevoegd en worden gebruikt als de interne inhoud van een fragment.
   * zijn ingesloten in het alineasysteem van het fragment.
   * Kan worden opgemaakt wanneer naar het [fragment wordt verwezen of wordt gebruikt op een pagina](/help/sites-authoring/content-fragments.md).
   * Kan alleen met de fragmenteditor worden toegevoegd aan, verwijderd uit of verplaatst binnen een fragment. Deze handelingen kunnen niet worden uitgevoerd in de paginaeditor.
   * Kan alleen worden toegevoegd aan, verwijderd uit of verplaatst binnen een fragment met [RTF-indeling in de fragmenteditor](/help/assets/content-fragments/content-fragments-variations.md#inserting-assets-into-your-fragment).
   * Kan alleen worden toegevoegd aan tekstelementen met meerdere regels (elk fragmenttype).
   * Aan de voorgaande tekst (alinea) worden toegevoegd.

   >[!CAUTION]
   >
   >Kan (per ongeluk) uit een fragment worden verwijderd door over te schakelen op de indeling Onbewerkte tekst.

   >[!NOTE]
   >
   >Elementen kunnen ook worden toegevoegd als [aanvullende (tussenliggende) inhoud](/help/sites-authoring/content-fragments.md#using-associated-content) wanneer een fragment op een pagina wordt gebruikt. het gebruiken van of Bijbehorende Inhoud of activa van browser van Middelen.

* **Gekoppelde inhoud**

   * Dit is inhoud die zich buiten een fragment bevindt, maar die van redactionele betekenis is. Meestal worden afbeeldingen, video&#39;s of andere fragmenten weergegeven.
   * De afzonderlijke elementen in de verzameling zijn beschikbaar voor gebruik met het fragment in de pagina-editor wanneer het aan een pagina wordt toegevoegd. Dit betekent dat ze optioneel zijn, afhankelijk van de vereisten van het specifieke kanaal.
   * De activa worden [verbonden aan fragmenten via inzamelingen](/help/assets/content-fragments/content-fragments-assoc-content.md); Met gekoppelde verzamelingen kan de auteur beslissen welke elementen worden gebruikt wanneer deze de pagina ontwerpt.

      * Verzamelingen kunnen tijdens het ontwerpen van fragmenten worden gekoppeld aan fragmenten via sjablonen, als standaardinhoud of door auteurs.
      * [Elementen (DAM) Verzamelingen](/help/assets/manage-collections.md) vormen de basis voor de bijbehorende inhoud van fragmenten.
   * Desgewenst kunt u het fragment zelf ook aan een verzameling toevoegen om het bijhouden van het fragment te vergemakkelijken.


* **Fragmentmetagegevens**

   * Gebruik de schema&#39;s voor metagegevens van [elementen](/help/assets/metadata.md).
   * Tags kunnen worden gemaakt wanneer u:

      * Het fragment maken en ontwerpen
      * of hoger:

         * Door de fragmenteigenschappen **weer te geven of te bewerken** vanuit de console
         * De **metagegevens** bewerken in de fragmenteditor

   >[!CAUTION]
   >
   >Metagegevensverwerkingsprofielen zijn niet van toepassing op inhoudsfragmenten.

* **Master**

   * Een integraal onderdeel van het fragment

      * Elk inhoudsfragment heeft één instantie van Master.
      * Master kan niet worden verwijderd.
   * Master is toegankelijk in de fragmenteditor onder **[Variaties](/help/assets/content-fragments/content-fragments-variations.md)**.
   * Master is geen variatie als zodanig, maar is de basis van alle variaties.


* **Variaties**

   * Uitvoeringen van fragmenttekst die specifiek zijn voor redactionele doeleinden; kan verband houden met het kanaal, maar is niet verplicht, en kan ook voor ad-hoclokale aanpassingen worden gebruikt.
   * worden gemaakt als kopieën van **Master**, maar kunnen vervolgens naar wens worden bewerkt; er is gewoonlijk inhoudsoverlap tussen de variaties zelf.
   * Kan worden gedefinieerd tijdens het ontwerpen van fragmenten of vooraf worden gedefinieerd in fragmentsjablonen.
   * Opgeslagen in het fragment, om spreiding van inhoudskopieën te voorkomen.
   * Variaties kunnen worden [gesynchroniseerd](/help/assets/content-fragments/content-fragments-variations.md#synchronizing-with-master) met Master als de Master inhoud is bijgewerkt.
   * Kan worden [samengevat](/help/assets/content-fragments/content-fragments-variations.md#summarizing-text) om de tekst snel af te kappen tot een vooraf gedefinieerde lengte.
   * Beschikbaar op het tabblad [Variaties](/help/assets/content-fragments/content-fragments-variations.md) van de fragmenteditor.

### Tussen inhoud wanneer pagina&#39;s worden gemaakt met inhoudsfragmenten {#in-between-content-when-page-authoring-with-content-fragments}

Tussen inhoud:

* Is beschikbaar voor gebruik in de Redacteur van de [Pagina wanneer het werken met Inhoudsfragmenten](/help/sites-authoring/content-fragments.md).
* Is [extra inhoud toegevoegd binnen de stroom van een fragment](/help/sites-authoring/content-fragments.md#adding-in-between-content) zodra het is gebruikt/van verwijzingen voorzien op een pagina.
* Tussen-inhoud kan aan elk fragment worden toegevoegd, waarbij slechts één element zichtbaar is.
* De bijbehorende inhoud kan worden gebruikt, evenals activa en/of componenten van aangewezen browser.

>[!CAUTION]
>
>De tussenliggende inhoud is pagina-inhoud. Deze wordt niet opgeslagen in het inhoudsfragment.

### Vereist door fragmenten {#required-by-fragments}

Voor het maken, bewerken en gebruiken van inhoudsfragmenten hebt u ook het volgende nodig:

* **Inhoudsmodel**

   * Wordt [ingeschakeld en gemaakt met de gereedschappen](/help/assets/content-fragments/content-fragments-models.md).
   * Vereist voor het [maken van een gestructureerd fragment](/help/assets/content-fragments/content-fragments-managing.md#creating-content-fragments).
   * Definieert de structuur van een fragment (titel, inhoudselementen, tagdefinities).
   * Definities van inhoudsmodellen vereisen een titel en één gegevenselement. alles is optioneel . Het model definieert een minimaal bereik van het fragment en de standaardinhoud, indien van toepassing. Auteurs kunnen de gedefinieerde structuur niet wijzigen tijdens het ontwerpen van fragmentinhoud.

* **Fragmentsjabloon**

   * Vereist voor het [maken van een eenvoudig fragment](/help/assets/content-fragments/content-fragments-managing.md#creating-content-fragments).
   * Usually [developed during project implementation](/help/sites-developing/content-fragment-templates.md); cannot be created when authoring.
   * Definieert de basiseigenschappen van een eenvoudig fragment (titel, aantal tekstelementen, tagdefinities).
   * Sjabloondefinities vereisen een titel en één tekstelement. alles is optioneel . De sjabloon definieert een minimaal bereik van het fragment en de standaardinhoud, indien van toepassing. Auteurs kunnen later een fragment uitbreiden dat verder gaat dan in de sjabloon is gedefinieerd.

* **Component Inhoudsfragment**

   * Instrumentaal voor het leveren van het fragment in HTML- en/of JSON-indeling.
   * Vereist om [naar het fragment op een pagina](/help/sites-authoring/content-fragments.md)te verwijzen.
   * Verantwoordelijk voor de lay-out en levering van een fragment; d.w.z. kanalen.
   * Fragmenten hebben een of meer specifieke componenten nodig om de lay-out te definiëren en om enkele of alle elementen/variaties en bijbehorende inhoud te leveren.
   * Als u een fragment naar een pagina sleept tijdens het ontwerpen, wordt de vereiste component automatisch gekoppeld.

## Voorbeeldgebruik {#example-usage}

Een fragment met de elementen en variaties kan worden gebruikt om coherente inhoud voor meerdere kanalen te maken. Bij het ontwerpen van het fragment moet u rekening houden met de plaats waar het fragment wordt gebruikt.

### We.Handelsvoorbeeld {#we-retail-sample}

Een voorbeeldfragment is zichtbaar bij:

`https://localhost:4502/assets.html/content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten`
