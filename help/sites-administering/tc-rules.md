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
workflow-type: tm+mt
source-wordcount: '1162'
ht-degree: 0%

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

U kunt bijvoorbeeld een regel maken die de inhoud vertaalt die auteurs aan alle AEM basistekstcomponenten op uw pagina&#39;s toevoegen. De regel kan de `/content` knoop en `text` bezit voor `foundation/components/text` component identificeren.

Er is een [console](#translation-rules-ui) die voor het vormen vertaalregels is toegevoegd. De definities in UI zullen het dossier voor u bevolken.

Zie [Inhoud vertalen voor meertalige sites](/help/sites-administering/translation.md) voor een overzicht van de functies voor het vertalen van inhoud in AEM.

>[!NOTE]
>
>AEM ondersteunt een-op-een-toewijzing tussen typen bronnen en verwijzingskenmerken voor het vertalen van inhoud waarnaar wordt verwezen op een pagina.

## De Syntaxis van de regel voor Pagina&#39;s, Componenten, en Activa {#rule-syntax-for-pages-components-and-assets}

Een regel is een `node`-element met een of meer onderliggende `property`-elementen en nul of meer onderliggende `node`-elementen:

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
* De onderliggende elementen `property` identificeren de knoopeigenschappen om voor alle middeltypes te vertalen:

   * Het `name` attribuut bevat de bezitsnaam.
   * Het optionele `translate`-kenmerk is `false` als de eigenschap niet is omgezet. De standaardwaarde is `true`. Dit kenmerk is handig wanneer u vorige regels overschrijft.

* De onderliggende elementen `node` identificeren de knoopeigenschappen om voor specifieke middeltypes te vertalen:

   * Het `resourceType` attribuut bevat de weg die aan de component oplost die het middeltype uitvoert.
   * Onderliggende `property`-elementen identificeren de eigenschap node die moet worden vertaald. Gebruik dit knooppunt op dezelfde manier als de onderliggende `property`-elementen voor knooppuntregels.

De volgende voorbeeldregel zorgt ervoor dat de inhoud van alle `text` eigenschappen voor alle pagina&#39;s onder de `/content` knoop wordt vertaald. De regel is effectief voor om het even welke component die inhoud in een `text` bezit, zoals de component van de stichtingstekst en de component van het stichtingsbeeld opslaat.

```xml
<node path="/content">
          <property name="text"/>
</node>
```

In het volgende voorbeeld wordt de inhoud van alle `text`-eigenschappen vertaald en worden ook andere eigenschappen van de basiscomponent Image vertaald. Als andere componenten eigenschappen met dezelfde naam hebben, is de regel niet op hen van toepassing.

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

* Eén `resourceType`-kenmerk dat gelijk is aan het pad dat naar de component wordt omgezet.
* Een `assetReferenceAttribute`-kenmerk dat gelijk is aan de naam van de eigenschap die het element binair (voor ingesloten elementen) of het pad naar het element waarnaar wordt verwezen, opslaat.

In het volgende voorbeeld worden afbeeldingen geëxtraheerd uit de basiscomponent Image:

```xml
<assetNode resourceType="foundation/components/image" assetReferenceAttribute="fileReference"/>
```

## Regels {#overriding-rules} overschrijven

Het bestand translate_rules.xml bestaat uit een `nodelist`-element met verschillende onderliggende `node`-elementen. AEM leest de nodenlijst van boven naar beneden. Wanneer de veelvoudige regels de zelfde knoop richten, wordt de regel die lager in het dossier is gebruikt. De volgende regels zorgen er bijvoorbeeld voor dat alle inhoud in `text`-eigenschappen wordt vertaald, behalve de `/content/mysite/en`-vertakking van pagina&#39;s:

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

U kunt knopen filtreren die een specifiek bezit door een `filter` element te gebruiken.

De volgende regels zorgen er bijvoorbeeld voor dat alle inhoud in `text`-eigenschappen wordt vertaald, behalve de knooppunten waarvoor de eigenschap `draft` is ingesteld op `true`.

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

## UI voor omzettingsregels {#translation-rules-ui}

Een console is ook beschikbaar voor het vormen van vertaalregels.

Toegang tot dit bestand:

1. Navigeer naar **Tools** en vervolgens **General**.

   ![chlimage_1-55](assets/chlimage_1-55.jpeg)

1. Selecteer **Omzetconfiguratie**.

   ![chlimage_1-56](assets/chlimage_1-56.jpeg)

Van hier, kunt u **Context** toevoegen. Zo kunt u een pad toevoegen.

![chlimage_1-57](assets/chlimage_1-57.jpeg)

Dan moet u uw context selecteren en dan **Edit** klikken. Hiermee opent u de Editor voor de vertaalregels.

![chlimage_1-58](assets/chlimage_1-58.jpeg)

Er zijn vier kenmerken die u kunt wijzigen via de gebruikersinterface: `isDeep`, `inherit`, `translate` en `updateDestinationLanguage`.

**** isDeepThis het attribuut is toepasselijk op knoopfilters en is waar door gebrek. Het controleert of de knoop (of zijn voorouders) die bezit met de gespecificeerde bezitswaarde in de filter bevat. Indien false, wordt alleen het huidige knooppunt gecontroleerd.

Bijvoorbeeld, worden de kindknopen toegevoegd in een vertaalbaan zelfs wanneer de ouderknoop bezit `draftOnly` geplaatst aan waar heeft om ontwerp inhoud te markeren. Hier `isDeep` komt in spel en controleert als de ouderknopen bezit `draftOnly` als waar hebben en die kindknopen uitsluiten.

In de Editor kunt u **Is diep** in het tabblad **Filters** in-/uitschakelen.

![chlimage_1-59](assets/chlimage_1-59.jpeg)

Hier is een voorbeeld van resulterende xml wanneer **Is Diep** in UI wordt ongecontroleerd:

```xml
 <filter>
    <node containsProperty="draftOnly" isDeep="false" propertyValue="true"/>
</filter>
```

**** inheritThis is apply on properties. Standaard wordt elke eigenschap overgeërfd, maar als u wilt dat een eigenschap niet op het onderliggende element wordt overgeërfd, kunt u die eigenschap als onwaar markeren, zodat deze alleen op dat specifieke knooppunt wordt toegepast.

In UI, kunt u **overerven** in **Eigenschappen** tabel controleren/uncheck.

![chlimage_1-60](assets/chlimage_1-60.jpeg)

**** translateThe translate wordt gebruikt eenvoudig om te specificeren al dan niet om een bezit te vertalen.

In UI, kunt u **Omzetten** in **Eigenschappen** tabel controleren/uncheck.

**Het** kenmerk updateDestinationLanguageThis wordt gebruikt voor eigenschappen die geen tekst maar taalcodes hebben, bijvoorbeeld jcr:language. De gebruiker vertaalt geen tekst maar de taallandinstelling van bron tot doel. Dergelijke eigenschappen worden niet verzonden voor vertaling.

In UI, kunt u **Omzetten** in **Eigenschappen** tabel controleren/uncheck, maar voor de specifieke eigenschappen die taalcodes als waarde hebben.

Om het verschil tussen `updateDestinationLanguage` en `translate` te helpen verduidelijken, is hier een eenvoudig voorbeeld van een context met slechts twee regels:

![chlimage_1-61](assets/chlimage_1-61.jpeg)

Het resultaat in de xml ziet er als volgt uit:

```xml
<property inherit="true" name="text" translate="true" updateDestinationLanguage="false"/>
<property inherit="true" name="jcr:language" translate="false" updateDestinationLanguage="true"/>
```

## Het bestand Regels handmatig bewerken {#editing-the-rules-file-manually}

Het bestand translatie_rules.xml dat met AEM is geïnstalleerd, bevat een standaardset vertaalregels. U kunt het bestand bewerken ter ondersteuning van de vereisten van uw vertaalprojecten. U kunt bijvoorbeeld regels toevoegen zodat de inhoud van uw aangepaste componenten wordt vertaald.

Als u het bestand translatie_rules.xml bewerkt, moet u een reservekopie bewaren in een inhoudspakket. Het installeren AEM de dienstpakken of het opnieuw installeren van bepaalde AEM pakketten kunnen het huidige vertaling_rules.xml- dossier met origineel vervangen. Om uw regels in deze situatie te herstellen, kunt u het pakket installeren dat uw reservekopie bevat.

>[!NOTE]
>
>Nadat u het inhoudspakket hebt gemaakt, moet u het pakket elke keer opnieuw samenstellen wanneer u het bestand bewerkt.

## Voorbeeld van omzettingsregels bestand {#example-translation-rules-file}

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

