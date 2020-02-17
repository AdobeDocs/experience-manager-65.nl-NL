---
title: Te vertalen inhoud identificeren
seo-title: Te vertalen inhoud identificeren
description: Leer hoe u inhoud kunt identificeren die moet worden vertaald.
seo-description: Leer hoe u inhoud kunt identificeren die moet worden vertaald.
uuid: 81b9575c-1c7a-4955-b03f-3f26cbd4f956
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: site-features
content-type: reference
discoiquuid: eedff940-4a46-4c24-894e-a5aa1080d23d
translation-type: tm+mt
source-git-commit: 1c1ade947f2cbd26b35920cfd10b1666b132bcbd

---


# Te vertalen inhoud identificeren{#identifying-content-to-translate}

De vertaalregels identificeren de inhoud om voor pagina&#39;s, componenten, en activa te vertalen die in, of van, vertaalprojecten inbegrepen zijn. Wanneer een pagina of element wordt vertaald, extraheert AEM deze inhoud zodat deze naar de vertaalservice kan worden verzonden.

Pagina&#39;s en elementen worden weergegeven als knooppunten in de JCR-opslagplaats. De inhoud die wordt geëxtraheerd, is een of meer eigenschapwaarden van de knooppunten. De vertaalregels identificeren de eigenschappen die de te extraheren inhoud bevatten.

De omzettingsregels worden uitgedrukt in het formaat van XML en in deze mogelijke plaatsen opgeslagen:

* `/libs/settings/translation/rules/translation_rules.xml`
* `/apps/settings/translation/rules/translation_rules.xml`
* `/conf/global/settings/translation/rules/translation_rules.xml`

Het bestand is van toepassing op alle vertaalprojecten.

>[!NOTE]
>
>Na een upgrade naar 6.4 wordt aangeraden het bestand van /etc. te verplaatsen. Zie [Gemeenschappelijke herstructurering van de opslagplaats in AEM 6.5](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#translation-rules) voor meer informatie.

De regels omvatten de volgende informatie:

* Het pad van het knooppunt waarop de regel van toepassing is. De regel is ook op de nakomelingen van de knoop van toepassing.
* De namen van de knoopeigenschappen die de te vertalen inhoud bevatten. Het bezit kan voor een specifiek middeltype of voor alle middeltypes specifiek zijn.

U kunt bijvoorbeeld een regel maken die de inhoud vertaalt die auteurs aan alle componenten van de AEM-stichtingstekst op uw pagina&#39;s toevoegen. De regel kan de `/content` knoop en het `text` bezit voor de `foundation/components/text` component identificeren.

Er is een [console](#translation-rules-ui) die voor het vormen vertaalregels is toegevoegd. De definities in UI zullen het dossier voor u bevolken.

 Zie Inhoud [vertalen voor meertalige sites](/help/sites-administering/translation.md)voor een overzicht van de functies voor het vertalen van inhoud in AEM.

>[!NOTE]
>
>AEM steunt één-op-één afbeelding tussen middeltypes en verwijzingsattributen voor vertaling van referenced inhoud op een pagina.

## De Syntaxis van de regel voor Pagina&#39;s, Componenten, en Activa {#rule-syntax-for-pages-components-and-assets}

Een regel is een `node` element met een of meer onderliggende `property` elementen en nul of meer onderliggende `node` elementen:

```xml
<node path="content path">
          <property name="property name" [translate="false"]/>
          <node resourceType="component path" >
               <property name="property name" [translate="false"]/>
          </node>
</node>
```

Elk van deze `node` elementen heeft de volgende kenmerken:

* Het `path` attribuut bevat de weg aan de wortelknoop van de tak waarop de regels van toepassing zijn.
* De elementen van het kind identificeren de knoopeigenschappen om voor alle middeltypes te vertalen: `property`

   * Het `name` kenmerk bevat de eigenschapsnaam.
   * Het optionele `translate` kenmerk is gelijk `false` als de eigenschap niet is omgezet. By default the value is `true`. Dit kenmerk is handig wanneer u vorige regels overschrijft.

* Onderliggende `node` elementen identificeren de knoopeigenschappen die voor specifieke brontypen moeten worden vertaald:

   * Het `resourceType` attribuut bevat de weg die aan de component oplost die het middeltype uitvoert.
   * Onderliggende `property` elementen identificeren de eigenschap node die moet worden vertaald. Gebruik dit knooppunt op dezelfde manier als de onderliggende `property` elementen voor knoopregels.

De volgende voorbeeldregel zorgt ervoor dat de inhoud van alle `text` eigenschappen wordt vertaald voor alle pagina&#39;s onder het `/content` knooppunt. De regel is effectief voor elke component die inhoud in een `text` eigenschap opslaat, zoals de component Foundation Text en de component foundation Image.

```xml
<node path="/content">
          <property name="text"/>
</node>
```

In het volgende voorbeeld wordt de inhoud van alle `text` eigenschappen vertaald en worden ook andere eigenschappen van de component Foundation Image vertaald. Als andere componenten eigenschappen met dezelfde naam hebben, is de regel niet op hen van toepassing.

```xml
<node path="/content">
      <property name="text"/>
      <node resourceType="foundation/components/textimage">
         <property name="image/alt"/>
         <property name="image/jcr:description"/>
         <property name="image/jcr:title"/>
      </node>
</node>
```

## Regelsyntaxis voor het uitnemen van elementen van pagina&#39;s {#rule-syntax-for-extracting-assets-from-pages}

Gebruik de volgende regelsyntaxis om elementen op te nemen die zijn ingesloten in of waarnaar wordt verwezen vanuit componenten:

```xml
<assetNode resourceType="path to component" assetReferenceAttribute="property that stores asset"/>
```

Elk `assetNode` element heeft de volgende kenmerken:

* Eén `resourceType` kenmerk dat gelijk is aan het pad dat naar de component wordt omgezet.
* Één `assetReferenceAttribute` attribuut dat de naam van het bezit evenaart dat de activa binaire (voor ingebedde activa) of de weg aan het referenced element opslaat.

In het volgende voorbeeld worden afbeeldingen geëxtraheerd uit de basiscomponent Image:

```xml
<assetNode resourceType="foundation/components/image" assetReferenceAttribute="fileReference"/>
```

## Regels overschrijven {#overriding-rules}

Het bestand translate_rules.xml bestaat uit een `nodelist` element met verschillende onderliggende `node` elementen. AEM leest de nodenlijst van boven naar onder. Wanneer de veelvoudige regels de zelfde knoop richten, wordt de regel die lager in het dossier is gebruikt. De volgende regels zorgen er bijvoorbeeld voor dat alle inhoud in `text` eigenschappen wordt vertaald, behalve de `/content/mysite/en` vertakking van pagina&#39;s:

```xml
<nodelist>
     <node path="/content”>
           <property name="text" />
     </node>
     <node path=“/content/mysite/en”>
          <property name=“text” translate=“false" />
     </node>
<nodelist>
```

## Filtereigenschappen {#filtering-properties}

U kunt knooppunten met een specifieke eigenschap filteren met een `filter` element.

De volgende regels zorgen er bijvoorbeeld voor dat alle inhoud in `text` eigenschappen wordt vertaald, behalve de knooppunten waarvoor de eigenschap is `draft` ingesteld op `true`.

```xml
<nodelist>
    <node path="/content”>
     <filter>
   <node containsProperty="draft" propertyValue="true" />
     </filter>
        <property name="text" />
    </node>
<nodelist>
```

## Interface voor vertaalregels {#translation-rules-ui}

Een console is ook beschikbaar voor het vormen van vertaalregels.

Toegang tot dit bestand:

1. Navigeer naar **Gereedschappen** en vervolgens naar **Algemeen**.

   ![chlimage_1-55](assets/chlimage_1-55.jpeg)

1. Selecteer **Vertaalconfiguratie**.

   ![chlimage_1-56](assets/chlimage_1-56.jpeg)

Vanaf hier kunt u context **** toevoegen. Zo kunt u een pad toevoegen.

![chlimage_1-57](assets/chlimage_1-57.jpeg)

Vervolgens moet u de context selecteren en op **Bewerken** klikken. Hiermee opent u de Editor voor de vertaalregels.

![chlimage_1-58](assets/chlimage_1-58.jpeg)

Er zijn vier kenmerken die u kunt wijzigen via de gebruikersinterface: `isDeep`, `inherit`, `translate` en `updateDestinationLanguage`.

**isDeep** Dit kenmerk is van toepassing op knooppuntfilters en is standaard true. Het controleert of de knoop (of zijn voorouders) die bezit met de gespecificeerde bezitswaarde in de filter bevat. Indien false, wordt alleen het huidige knooppunt gecontroleerd.

Bijvoorbeeld, worden de kindknopen toegevoegd in een vertaalbaan zelfs wanneer de ouderknoop bezit die bezit aan waar wordt geplaatst om ontwerp inhoud te markeren. `draftOnly` Hier `isDeep` komt in spel en controleert als de ouderknopen bezit `draftOnly` zoals waar hebben en die kindknopen uitsluiten.

In de Editor kunt u **Is diep** in-/uitschakelen op het tabblad **Filters** .

![chlimage_1-59](assets/chlimage_1-59.jpeg)

Hier is een voorbeeld van resulterende xml wanneer **Is Diep** in UI wordt ongecontroleerd:

```xml
 <filter>
    <node containsProperty="draftOnly" isDeep="false" propertyValue="true"/>
</filter>
```

**overerven** Dit is van toepassing op eigenschappen. Standaard wordt elke eigenschap overgeërfd, maar als u wilt dat een eigenschap niet op het onderliggende element wordt overgeërfd, kunt u die eigenschap als onwaar markeren, zodat deze alleen op dat specifieke knooppunt wordt toegepast.

In UI, kunt u **Overnemen** in-/uitschakelen op het lusje van **Eigenschappen** .

![chlimage_1-60](assets/chlimage_1-60.jpeg)

**translate** The translate attribute wordt gebruikt eenvoudig om te specificeren of om een bezit al dan niet te vertalen.

In UI, kunt u **Vertaal** in-/uitschakelen op het lusje van **Eigenschappen** .

**updateDestinationLanguage** Dit kenmerk wordt gebruikt voor eigenschappen die geen tekst maar taalcodes hebben, bijvoorbeeld jcr:language. De gebruiker vertaalt geen tekst maar de taallandinstelling van bron tot doel. Dergelijke eigenschappen worden niet verzonden voor vertaling.

In UI, kunt u **Vertaal** op het lusje van **Eigenschappen** controleren/uncheck, maar voor de specifieke eigenschappen die taalcodes als waarde hebben.

Om het verschil tussen `updateDestinationLanguage` en `translate`te verduidelijken, is een eenvoudig voorbeeld van een context met slechts twee regels:

![chlimage_1-61](assets/chlimage_1-61.jpeg)

Het resultaat in de xml ziet er als volgt uit:

```xml
<property inherit="true" name="text" translate="true" updateDestinationLanguage="false"/>
<property inherit="true" name="jcr:language" translate="false" updateDestinationLanguage="true"/>
```

## Het bestand Regels handmatig bewerken {#editing-the-rules-file-manually}

Het bestand translatie_rules.xml dat met AEM wordt geïnstalleerd, bevat een standaardset vertaalregels. U kunt het bestand bewerken ter ondersteuning van de vereisten van uw vertaalprojecten. U kunt bijvoorbeeld regels toevoegen zodat de inhoud van uw aangepaste componenten wordt vertaald.

Als u het bestand translatie_rules.xml bewerkt, moet u een reservekopie bewaren in een inhoudspakket. Door AEM-servicepacks te installeren of bepaalde AEM-pakketten opnieuw te installeren, kan het huidige bestand translate_rules.xml worden vervangen door het origineel. Om uw regels in deze situatie te herstellen, kunt u het pakket installeren dat uw reservekopie bevat.

>[!NOTE]
>
>Nadat u het inhoudspakket hebt gemaakt, moet u het pakket elke keer opnieuw samenstellen wanneer u het bestand bewerkt.

## Voorbeeld omzettingsregels-bestand {#example-translation-rules-file}

```xml
<nodelist>
    <!-- translation rules for Geometrixx Demo site (example) -->
    <node path="/content/geometrixx">
        <!-- list all node properties that should be translated -->
        <property name="jcr:title" /> <!-- translation workflows running on content saved in /content/geometrixx, will extract jcr:title values independent of the component. -->
        <property name="jcr:description" />
        <node resourceType ="foundation/components/image"> <!-- translation workflows running on content saved in /content/geometrixx, will extract alternateText values only for Image component. -->
            <property name="alternateText"/>
        </node>
        <node resourceType ="geometrixx/components/title">
            <property name="richText"/>
            <property name="jcr:title" translate="false"/> <!-- translation workflows running on content saved in /content/geometrixx, will not extract jcr:title for Title component, but instead use richText. -->
        </node>
        <node pathContains="/cq:annotations">
            <property name="text" translate="false"/> <!-- translation workflows running on content saved in /content/geometrixx, will not extract text if part of cq:annotations node. -->
        </node>
    </node>
    <!-- translation rules for Geometrixx Outdoors site (example) -->
    <node path="/content/geometrixx-outdoors">
        <node resourceType ="foundation/components/image">
            <property name="alternateText"/>
            <property name="jcr:title" />
        </node>
        <node resourceType ="geometrixx-outdoors/components/title">
            <property name="richText"/>
        </node>
    </node>
    <!-- translation rules for ASSETS (example) -->
    <node path="/content/dam">
        <!-- configure list of metadata properties here -->
        <property name="dc:title" />
        <property name="dc:description" />
    </node>
    <!-- translation rules for extracting ASSETS from SITES content, configure all components that embed or reference assets -->
    <assetNode resourceType="foundation/components/image" assetReferenceAttribute="fileReference"/>
    <assetNode resourceType="foundation/components/video" assetReferenceAttribute="asset"/>
    <assetNode resourceType="foundation/components/download" assetReferenceAttribute="fileReference"/>
    <assetNode resourceType="foundation/components/mobileimage" assetReferenceAttribute="fileReference"/>
    <assetNode resourceType="wcm/foundation/components/image" assetReferenceAttribute="fileReference"/>
</nodelist>
```

