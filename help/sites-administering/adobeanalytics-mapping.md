---
title: Componentgegevens toewijzen met de eigenschappen van Adobe Analytics
seo-title: Componentgegevens toewijzen met de eigenschappen van Adobe Analytics
description: Leer hoe u componentgegevens kunt toewijzen met SiteCatalyst-eigenschappen.
seo-description: Leer hoe u componentgegevens kunt toewijzen met SiteCatalyst-eigenschappen.
uuid: b08ab37f-ad58-4c04-978f-8e21a3823ae8
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: 6c1f8869-62d9-4fac-aa0d-b99bb0e86d6b
docset: aem65
translation-type: tm+mt
source-git-commit: 6f49e01aa3e9841c7b2917870593452b778667d2

---


# Componentgegevens toewijzen met de eigenschappen van Adobe Analytics{#mapping-component-data-with-adobe-analytics-properties}

Voeg componenten toe aan het framework die de gegevens verzamelen die naar Adobe Analytics moeten worden verzonden. Componenten die zijn ontworpen om analysegegevens te verzamelen slaan de gegevens op in de juiste **CQ-variabele**. Wanneer u een dergelijke component aan een framework toevoegt, wordt in het framework de lijst met CQ-variabelen weergegeven, zodat u elk aan de juiste variabele **** Analytics kunt toevoegen.

![aa-11](assets/aa-11.png)

Wanneer de **AEM-weergave** is geopend, worden de variabelen Analytics weergegeven in de zoekfunctie.

![aa-12](assets/aa-12.png)

U kunt meerdere analytische variabelen toewijzen met dezelfde **CQ-variabele**.

![chlimage_1-68](assets/chlimage_1-68.png)

De toegewezen gegevens worden naar Adobe Analytics verzonden wanneer de pagina wordt geladen en aan de volgende voorwaarden wordt voldaan:

* De pagina is gekoppeld aan het framework.
* De pagina gebruikt de componenten die aan het framework zijn toegevoegd.

Gebruik de volgende procedure om CQ-componentvariabelen toe te wijzen met de rapporteigenschappen van Adobe Analytics.

1. Sleep in de **AEM-weergave** een component tracking van sidekick naar het framework. Sleep bijvoorbeeld de component **Pagina** van de categorie **Algemeen** .

   ![aa-13](assets/aa-13.png)

   Er zijn verschillende standaardcomponentgroepen: **Algemeen**, **Handel**, **Gemeenschappen**, **Onderzoek&amp;Bevorderen**, en **andere**. Uw instantie AEM kan worden gevormd om verschillende groepen en componenten te tonen.

1. Als u Adobe Analytics-variabelen wilt toewijzen aan variabelen die in de component zijn gedefinieerd, sleept u een variabele **** Analytics van de zoekfunctie naar een veld in de component tracking. Sleep bijvoorbeeld `Page Name (pageName)` naar `pagedata.title`.

   ![aa-14](assets/aa-14.png)

   >[!NOTE]
   >
   >De rapportsuite-id (RSID) die voor het framework is geselecteerd, bepaalt de Adobe Analytics-variabelen die in de zoekfunctie voor inhoud worden weergegeven.

1. Herhaal de vorige twee stappen voor andere componenten en variabelen.

   >[!NOTE]
   >
   >U kunt meerdere analytische variabelen toewijzen (bijvoorbeeld `props`, `eVars`, `events`) aan dezelfde CQ-variabele (bijv. `pagedata.title`)

   >[!CAUTION]
   >
   >Het wordt ten zeerste aanbevolen:
   >    
   >    * `eVars` en `props` worden toegewezen aan CQ-variabelen die beginnen met `pagedata.X` of `eventdata.X`
      >    
      >    
   * overwegende dat gebeurtenissen moeten worden toegewezen aan variabelen die beginnen met `eventdata.events.X`


1. Als u het framework beschikbaar wilt maken op de publicatie-instantie van uw site, opent u het tabblad **Pagina** van sidekick en klikt u op Framework **activeren.**

## Toewijzing van productgerelateerde variabelen {#mapping-product-related-variables}

AEM gebruikt een conventie voor de naamgeving van productgerelateerde variabelen en gebeurtenissen die moeten worden toegewezen aan productgerelateerde eigenschappen van Adobe Analytics:

| CQ-variabele | Analysevariabele | Beschrijving |
|---|---|---|
| `product.category` | `product.category` (conversievariabele) | De productcategorie. |
| `product.sku` | `product.sku` (conversievariabele) | De sku van het product. |
| `product.quantity` | `product.quantity` (conversievariabele) | Het aantal producten dat wordt aangeschaft. |
| `product.price` | `product.price` (conversievariabele) | De productprijs. |
| `product.events.<eventName>` | De succesgebeurtenis(sen) die aan het product in uw rapport moeten worden gekoppeld. | `product.events` is het voorvoegsel voor gebeurtenissen met de naam *eventName.* |
| `product.evars.<eVarName>` | De conversievariabele(n) ( `eVar`) die aan het product moet worden gekoppeld. | `product.evars` is het voorvoegsel voor eVar-variabelen met de naam *eVarName.* |

Verscheidene componenten van de Handel AEM gebruiken deze veranderlijke namen.

>[!NOTE]
>
>Wijs de eigenschap Adobe Analytics Products niet toe aan een CQ-variabele. Het configureren van productgerelateerde toewijzingen, zoals beschreven in de tabel, is in feite gelijk aan het toewijzen van de variabele Producten.

### Rapporten op Adobe Analytics controleren {#checking-reports-on-adobe-analytics}

1. Meld u aan bij de Adobe Analytics-website met dezelfde gegevens die ook aan AEM zijn verstrekt.
1. Zorg ervoor RSID wordt geselecteerd die in de vorige stappen wordt gebruikt.
1. Selecteer in **Rapporten** (aan de linkerkant van de pagina) de optie **Aangepaste omzetting**, vervolgens de optie **Aangepaste omzetting 1-10** en selecteer de variabele die overeenkomt met `eVar7`

1. Afhankelijk van de versie van Adobe Analytics die u gebruikt, moet u gemiddeld 45 minuten wachten tot het rapport wordt bijgewerkt met de gebruikte zoekterm. bijv. aubergine in het voorbeeld

## De Content Finder (cf#) gebruiken met Adobe Analytics-frameworks {#using-the-content-finder-cf-with-adobe-analytics-frameworks}

Wanneer u in eerste instantie een Adobe Analytics-framework opent, bevat de zoekfunctie voor inhoud vooraf gedefinieerde variabelen voor Analytics onder:

* Verkeer
* Conversie
* Gebeurtenissen

Wanneer RSID wordt geselecteerd worden alle variabelen die tot dat RSID behoren toegevoegd aan de lijst.\
Dit `cf#` is nodig om analytische variabelen toe te wijzen aan de CQ-variabelen die op de verschillende volgcomponenten aanwezig zijn. Zie Een framework instellen voor basistracking.

Afhankelijk van de weergave die voor het framework is geselecteerd, wordt de zoeker van de inhoud gevuld met variabelen voor Analytics (in de AEM-weergave) of CQ-variabelen (in de Analyseweergave).

De lijst kan op de volgende manieren worden gemanipuleerd:

1. In de **AEM-weergave** kan de lijst worden gefilterd op basis van het type variabele dat u selecteert met de drie filterknoppen:

   * Als er *geen knop* is geselecteerd, wordt in de lijst de volledige lijst weergegeven.
   * Als de knoop van het **Verkeer** wordt geselecteerd, zal de lijst slechts de variabelen tonen die tot de sectie van het Verkeer behoren.
   * Als de knop **Conversie** is geselecteerd, worden in de lijst alleen de variabelen weergegeven die tot de sectie Conversie behoren.
   * Als de knop **Gebeurtenissen** is geselecteerd, worden in de lijst alleen de variabelen weergegeven die tot de sectie Gebeurtenissen behoren.
   >[!NOTE]
   >
   >Er kan slechts één filterknop tegelijk actief zijn.

   >[!NOTE]
   >
   >Variabelen voor zoeken en bevorderen horen ook bij de sectie Conversie.

   1. De lijst bevat ook een zoekfunctie waarmee de elementen worden gefilterd op basis van de tekst die in het zoekveld is ingevoerd.
   1. Als een filteroptie wordt geactiveerd terwijl u naar elementen in de lijst zoekt, worden de weergegeven resultaten ook gefilterd op basis van de actieve knop.
   1. De lijst kan op elk moment opnieuw worden geladen met de knop met de strijkpijlen.
   1. Als veelvoudige RSIDs op het kader wordt geselecteerd, zullen alle variabelen in de lijst worden getoond gebruikend alle etiketten die binnen geselecteerde RSIDs worden gebruikt.


1. In de Adobe Analytics-weergave worden in de Content Finder alle CQ-variabelen weergegeven die horen bij de volgende componenten die in de CQ-weergave zijn gesleept.

   * Als de **downloadcomponent** bijvoorbeeld de *enige is die in de CQ-weergave wordt gesleept* (met twee variabele *eventData.downloadLink* en *eventData.events.startDownload*), ziet de Content Finder er als volgt uit wanneer naar de Adobe Analytics-weergave wordt overgeschakeld:
   ![aa-22](assets/aa-22.png)

   * De variabelen kunnen naar elke Adobe Analytics-variabele worden gesleept die tot een van de drie variabele secties (**Verkeer**, **Conversie** en **Gebeurtenissen**) behoort.

   * Wanneer u een nieuwe traceringscomponent naar het framework sleept in de CQ-weergave, worden de CQ-variabelen die bij de component horen, automatisch toegevoegd aan de Content Finder (cf#) in de Adobe Analytics-weergave.
   >[!NOTE]
   >
   >Er kan slechts één CQ-variabele tegelijk worden toegewezen aan een Adobe Analytics-variabele

## De AEM-weergave en de analyseweergave gebruiken {#using-aem-view-and-analytics-view}

Op elk gewenst moment kunnen gebruikers schakelen tussen twee manieren om de Adobe Analytics-toewijzingen weer te geven op een frameworkpagina. De twee weergaven bieden een beter overzicht van de toewijzingen binnen het kader, vanuit twee verschillende perspectieven.

### AEM-weergave {#aem-view}

![aa-23](assets/aa-23.png)

Als u de bovenstaande afbeelding als voorbeeld neemt, heeft de **AEM-weergave** de volgende eigenschappen:

1. Dit is de standaardweergave wanneer het framework wordt geopend.
1. Linkerkant: de zoeker van de inhoud (cf#) wordt gevuld met variabelen van Adobe Analytics op basis van de geselecteerde RSID(&#39;s).
1. Tabkoppen (**AEM-weergave** en **analyseweergave**): Gebruik deze om tussen de twee weergaven te schakelen.

1. **AEM-weergave**:

   1. Als het framework componenten bevat die zijn overgeërfd van het bovenliggende element, worden deze hier vermeld, samen met de variabelen die aan de componenten zijn toegewezen.

      1. Overerfde componenten zijn vergrendeld.
      1. Als u een overgeërfde component wilt ontgrendelen, dubbelklikt u op het hangslot naast de naam van de component.
      1. Als u de overerving wilt herstellen, moet u de ontgrendelde component verwijderen. waarna de vergrendelde status weer wordt hersteld.
   1. **Sleep componenten hier naartoe om ze op te nemen in het analyseframework**: Componenten kunnen van de Sidetrap worden gesleept en hier neergezet.
   1. U kunt alle componenten vinden die momenteel in het analytische framework zijn opgenomen:

      1. Als u een component wilt toevoegen, sleept u een component van het tabblad Componenten van de hulpwerkschijf
      1. Als u een component en alle bijbehorende toewijzingen wilt verwijderen, selecteert u Verwijderen in het contextmenu van de component en accepteert u de verwijdering in het bevestigingsdialoogvenster.
      1. Onthoud dat een component alleen kan worden verwijderd uit het framework waarin de component is gemaakt en niet in de traditionele zin kan worden verwijderd uit onderliggende frameworks (ze kunnen alleen worden overschreven).


### Analyseweergave {#analytics-view}

![aa-24](assets/aa-24.png)

1. U hebt toegang tot deze weergave door over te schakelen op het tabblad **Analyseweergave** in het framework.
1. Linkerkant: De Inhoudszoeker (cf#) wordt gevuld met CQ-variabelen op basis van de componenten die in de CQ-weergave naar het framework zijn gesleept.
1. Tabkoppen (**AEM-weergave** en **analyseweergave**): Gebruik deze om tussen de twee weergaven te schakelen.

1. In de drie tabellen (Verkeer, Conversie, Gebeurtenis) worden alle beschikbare Adobe Analytics-variabelen vermeld. behoren tot de geselecteerde RSID(&#39;s). De afbeeldingen die hier worden weergegeven, moeten hetzelfde zijn als in de AEM-weergave:

   * **Verkeer**:

      * Verkeersvariabele ( `prop1`) toegewezen aan een CQ-variabele ( `eventdata.downloadLink`)

      * Wanneer er naast de component een Padlock staat, betekent dit dat deze wordt overgeërfd van een bovenliggend framework en dus niet kan worden bewerkt
   * **Conversie**:

      * Conversievariabele ( `eVar1`) toegewezen aan een CQ-variabele ( `pagedata.title`)

      * Conversievariabele ( `eVar3`) die is toegewezen aan een inline toegevoegde JavaScript-expressie door te dubbelklikken op het veld CQ-variabele en de code handmatig in te voeren
   * **Gebeurtenis**:

      * Gebeurtenisvariabele ( `event1`) toegewezen aan een CQ-gebeurtenis ( `eventdata.events.pageView`)



>[!NOTE]
>
>De CQ-variabele kolom van een tabel kan ook inline worden ingevuld door te dubbelklikken op het veld en er tekst aan toe te voegen. Deze velden accepteren javascript als invoer.
>
>* Bijvoorbeeld naast `prop3` u kunt toevoegen
>* `'`* `Adobe:'+pagedata.title+':'+pagedata.sitesection`\
   >  *om de* titel *van een pagina te verzenden die met zijn* plaats *aaneengeschakeld is door*: (dubbele punt) en vooraf ingesteld bij *Adobe* als `prop3`
>



>[!CAUTION]
>
>Er kan slechts één CQ-variabele op elk gewenst moment worden toegewezen aan een Adobe Analytics-variabele.

