---
title: Componentgegevens toewijzen aan Adobe Analytics-eigenschappen
description: Leer hoe u componentgegevens kunt toewijzen met SiteCatalyst-eigenschappen.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
docset: aem65
exl-id: c7c0c705-ec16-40f5-ad08-193f82d01263
solution: Experience Manager, Experience Manager Sites
feature: Integration
role: Admin
source-git-commit: eae057caed533ef16bb541b4ad41b8edd7aaa1c7
workflow-type: tm+mt
source-wordcount: '1449'
ht-degree: 0%

---

# Componentgegevens toewijzen aan Adobe Analytics-eigenschappen{#mapping-component-data-with-adobe-analytics-properties}

Voeg componenten toe aan het framework die de gegevens verzamelen die naar Adobe Analytics moeten worden verzonden. De componenten die worden ontworpen om analysegegevens te verzamelen slaan de gegevens in de aangewezen **variabele CQ** op. Wanneer u zulk een component aan een kader toevoegt, toont het kader de lijst van CQ variabelen zodat u aan de aangewezen **variabele van Analytics** kunt elk.

![ a-11 ](assets/aa-11.png)

Wanneer de **AEM mening** open is verschijnen de variabelen van de Analyse in de inhoudszoeker.

![ a-12 ](assets/aa-12.png)

U kunt veelvoudige variabelen van de Analyse met de zelfde **variabele CQ in kaart brengen**.

![ chlimage_1-68 ](assets/chlimage_1-68.png)

De toegewezen gegevens worden naar Adobe Analytics verzonden wanneer de pagina wordt geladen en aan de volgende voorwaarden wordt voldaan:

* De pagina is gekoppeld aan het framework.
* De pagina gebruikt de componenten die aan het framework zijn toegevoegd.

Gebruik de volgende procedure om CQ-componentvariabelen toe te wijzen aan Adobe Analytics-rapporteigenschappen.

1. In de **AEM mening**, sleep een het volgen component van sidekick op het kader. Bijvoorbeeld, sleep de **component van de Pagina** van de **Algemene** categorie.

   ![ a-13 ](assets/aa-13.png)

   Er zijn verscheidene standaardcomponentengroepen: **Algemeen**, **Commerce**, **Gemeenschappen**, en **Andere**. Uw AEM instantie kan worden gevormd om verschillende groepen en componenten te tonen.

1. Om de variabelen van Adobe Analytics met variabelen in kaart te brengen die in de component worden bepaald, sleep een **variabele van de Analyse** van de inhoudszoeker op een gebied op de volgende component. Sleep bijvoorbeeld `Page Name (pageName)` naar `pagedata.title` .

   ![ a-14 ](assets/aa-14.png)

   >[!NOTE]
   >
   >De de Reeks identiteitskaart van het Rapport (RSID) die voor het kader wordt geselecteerd bepaalt de variabelen van Adobe Analytics die in de inhoudszoeker verschijnen.

1. Herhaal de vorige twee stappen voor andere componenten en variabelen.

   >[!NOTE]
   >
   >U kunt meerdere analytische variabelen (bijvoorbeeld `props` , `eVars` , `events` ) toewijzen aan dezelfde CQ-variabele (bijvoorbeeld `pagedata.title` )

   >[!CAUTION]
   >
   >Het wordt ten zeerste aanbevolen:
   >
   >* `eVars` en `props` worden toegewezen aan CQ-variabelen die beginnen met `pagedata.X` of `eventdata.X`
   >* overwegende dat gebeurtenissen moeten worden toegewezen aan variabelen vanaf `eventdata.events.X`

1. Om het kader beschikbaar te maken op publiceer geval van uw plaats, open het **lusje van de Pagina** van hulplid, en klik **Activate Kader.**

## Toewijzing van productgerelateerde variabelen {#mapping-product-related-variables}

AEM gebruikt een conventie voor de naamgeving van productgerelateerde variabelen en gebeurtenissen die moeten worden toegewezen aan Adobe Analytics-productgerelateerde eigenschappen:

| CQ-variabele | Analysevariabele | Beschrijving |
|--- |--- |--- |
| `product.category` | `product.category` (conversievariabele) | De productcategorie. |
| `product.sku` | `product.sku` (conversievariabele) | De productsku. |
| `product.quantity` | `product.quantity` (conversievariabele) | Het aantal producten dat wordt aangeschaft. |
| `product.price` | `product.price` (conversievariabele) | De productprijs. |
| `product.events.<eventName>` | De succesgebeurtenis(sen) die aan het product in uw rapport moeten worden gekoppeld. | `product.events` is de prefix voor gebeurtenissen genoemd *eventName.* |
| `product.evars.<eVarName>` | De conversievariabele(n) ( `eVar`) die aan het product moet worden gekoppeld. | `product.evars` is de prefix voor eVar genoemde variabelen *eVarName.* |

Verschillende AEM Commerce-componenten gebruiken deze variabelenamen.

>[!NOTE]
>
>Wijs de eigenschap Adobe Analytics Products niet toe aan een CQ-variabele. Het configureren van productgerelateerde toewijzingen, zoals beschreven in de tabel, is in feite gelijk aan het toewijzen van de variabele Producten.

### Rapporten op Adobe Analytics controleren {#checking-reports-on-adobe-analytics}

1. Meld u aan bij de Adobe Analytics-website met dezelfde gegevens die aan AEM zijn verstrekt.
1. Zorg ervoor RSID wordt geselecteerd die in de vorige stappen wordt gebruikt.
1. In **Rapporten** (op de linkerkant van de pagina) uitgezochte **Omzetting van de Douane**, toen **Omzetting van de Douane 1-10** en selecteer de variabele die aan `eVar7` beantwoordt

1. Afhankelijk van de versie van Adobe Analytics die u gebruikt, moet u gemiddeld 45 minuten wachten op het rapport dat met de gebruikte zoekterm moet worden bijgewerkt; bijvoorbeeld, aubergine in het voorbeeld

## De Inhoudszoeker (cf#) gebruiken met Adobe Analytics-frameworks {#using-the-content-finder-cf-with-adobe-analytics-frameworks}

Wanneer u in eerste instantie een Adobe Analytics-framework opent, bevat de zoekfunctie voor inhoud vooraf gedefinieerde variabelen voor Analytics onder:

* Verkeer
* Conversie
* Gebeurtenissen

Wanneer RSID wordt geselecteerd worden alle variabelen die tot dat RSID behoren toegevoegd aan de lijst.\
`cf#` is nodig om analytische variabelen toe te wijzen aan de CQ-variabelen die aanwezig zijn op de verschillende volgcomponenten. Zie Een framework instellen voor basistracking.

Afhankelijk van de weergave die voor het framework is geselecteerd, wordt de zoeker van de inhoud gevuld met variabelen voor Analytics (in AEM weergave) of CQ-variabelen (in de weergave Analytics).

De lijst kan op de volgende manieren worden gemanipuleerd:

1. Wanneer in **AEM mening**, de lijst afhankelijk van welk veranderlijk type wordt geselecteerd kan worden gefiltreerd gebruikend de drie filterknopen:

   * Als *geen knoop* wordt geselecteerd, toont de lijst de volledige lijst.
   * Als de **knoop van het Verkeer** wordt geselecteerd, zal de lijst slechts de variabelen tonen die tot de sectie van het Verkeer behoren.
   * Als de **knoop van de Omzetting** wordt geselecteerd, zal de lijst slechts de variabelen tonen die tot de sectie van de Omzetting behoren.
   * Als de **knoop van Gebeurtenissen** wordt geselecteerd, zal de lijst slechts de variabelen tonen die tot de sectie van Gebeurtenissen behoren.

   >[!NOTE]
   >
   >Er kan slechts één filterknop tegelijk actief zijn.

   1. De lijst bevat ook een zoekfunctie waarmee de elementen worden gefilterd op basis van de tekst die in het zoekveld is ingevoerd.
   1. Als een filteroptie wordt geactiveerd terwijl u naar elementen in de lijst zoekt, worden de weergegeven resultaten ook gefilterd op basis van de actieve knop.
   1. De lijst kan op elk moment opnieuw worden geladen met de knop met de strijkpijlen.
   1. Als veelvoudige RSIDs op het kader wordt geselecteerd, zullen alle variabelen in de lijst worden getoond gebruikend alle etiketten die binnen geselecteerde RSIDs worden gebruikt.

1. In de weergave Adobe Analytics worden alle CQ-variabelen weergegeven die horen bij de volgende componenten die in de CQ-weergave zijn gesleept.

   * Bijvoorbeeld, voor het geval dat de **component van de Download** *slechts één gesleept* in CQ mening (die twee in kaart gebrachte variabelen *eventData.downloadLink* en *eventData.events.startDownload* heeft), zal de Vinder van de Inhoud als dit kijken wanneer het schakelen naar de mening van Adobe Analytics:

   ![ a-22 ](assets/aa-22.png)

   * De variabelen kunnen worden gesleept&amp;gelaten vallen op om het even welke variabele van Adobe Analytics die tot één van beide drie veranderlijke secties (**Verkeer**, **Omzetting** en **Gebeurtenissen**) behoren.

   * Wanneer u een nieuwe traceringscomponent naar het framework sleept in de CQ-weergave, worden de CQ-variabelen die bij de component horen automatisch toegevoegd aan de Content Finder (cf#) in de Adobe Analytics-weergave.

   >[!NOTE]
   >
   >Er kan slechts één CQ-variabele op elk gewenst moment aan een Adobe Analytics-variabele worden toegewezen.

## De weergave AEM en Analyse gebruiken {#using-aem-view-and-analytics-view}

Op elk gewenst moment kunnen gebruikers schakelen tussen twee manieren om de Adobe Analytics-toewijzingen te bekijken op een frameworkpagina. De twee weergaven bieden een beter overzicht van de toewijzingen binnen het kader, vanuit twee verschillende perspectieven.

### AEM {#aem-view}

![ a-23 ](assets/aa-23.png)

Het nemen van het bovengenoemde beeld als voorbeeld, heeft de **AEM mening** de volgende eigenschappen:

1. Dit is de standaardweergave wanneer het framework wordt geopend.
1. Linkerkant: de zoeker van de inhoud (cf#) wordt gevuld met Adobe Analytics-variabelen op basis van de geselecteerde RSID(&#39;s).
1. De kopballen van het lusje (**AEM mening** en **de mening van de Analyse**): gebruik deze om tussen de twee meningen te schakelen.

1. **AEM mening**:

   1. Als het framework componenten bevat die zijn overgeërfd van het bovenliggende element, worden deze hier vermeld, samen met de variabelen die aan de componenten zijn toegewezen.

      1. Overerfde componenten zijn vergrendeld.
      1. Als u een overgeërfde component wilt ontgrendelen, dubbelklikt u op de vergrendeling naast de naam van de component
      1. Als u de overerving wilt herstellen, verwijdert u de niet-vergrendelde component. Daarna krijgt deze de vergrendelde status terug.

   1. **de componenten van de belemmering hier om hen in het analytische kader** te omvatten: De componenten kunnen van de Sidekick worden gesleept en hier worden gelaten vallen.
   1. U kunt alle componenten vinden die momenteel in het analytische framework zijn opgenomen:

      1. Als u een component wilt toevoegen, sleept u een component van het tabblad Componenten van het zijpaneel
      1. Als u een component en alle bijbehorende toewijzingen wilt verwijderen, selecteert u Verwijderen in het contextmenu van de component en accepteert u de verwijdering in het bevestigingsdialoogvenster.
      1. Onthoud dat een component alleen kan worden verwijderd uit het framework waarin de component is gemaakt en niet in de traditionele zin kan worden verwijderd uit onderliggende frameworks (ze kunnen alleen worden overschreven).

### Analyseweergave {#analytics-view}

![ a-24 ](assets/aa-24.png)

1. Deze mening kan worden betreden door aan het **** lusje van de mening van Analytics op het kader te schakelen.
1. Linkerkant: Inhoudszoeker (cf#) gevuld met CQ-variabelen op basis van de componenten die in de CQ-weergave naar het framework zijn gesleept.
1. De kopballen van het lusje (**AEM mening** en **de mening van de Analyse**): gebruik deze om tussen de twee meningen te schakelen.

1. In de drie tabellen (Verkeer, Conversie, Gebeurtenis) worden alle beschikbare Adobe Analytics-variabelen vermeld. behoren tot de geselecteerde RSID(&#39;s). De hier getoonde toewijzingen moeten gelijk zijn aan die in de AEM weergave:

   * **Verkeer**:

      * Verkeersvariabele ( `prop1`) toegewezen aan een CQ-variabele ( `eventdata.downloadLink`)

      * Wanneer er naast de component een Padlock staat, betekent dit dat deze wordt overgeërfd van een bovenliggend framework en dus niet kan worden bewerkt

   * **Omzetting**:

      * Conversievariabele ( `eVar1`) die is toegewezen aan een CQ-variabele ( `pagedata.title`)

      * Conversievariabele ( `eVar3`) die is toegewezen aan een inline toegevoegde JavaScript-expressie door te dubbelklikken op het veld voor CQ-variabelen en de code handmatig in te voeren

   * **Gebeurtenis**:

      * Gebeurtenisvariabele ( `event1`) die is toegewezen aan een CQ-gebeurtenis ( `eventdata.events.pageView`)

>[!NOTE]
>
>De CQ-variabele kolom van een tabel kan ook inline worden ingevuld door te dubbelklikken op het veld en er tekst aan toe te voegen. Deze velden accepteren JavaScript als invoer.
>
>Naast `prop3` kunt u bijvoorbeeld het volgende toevoegen:
>     `'`* `Adobe:'+pagedata.title+':'+pagedata.sitesection`\
>om de *titel* van een pagina te verzenden samengevoegd met zijn *plaats* gebruikend *:* (dubbelepunt) en met *Adobe* als `prop3` vooraf bepaald
>

>[!CAUTION]
>
>Er kan slechts één CQ-variabele op elk gewenst moment aan een Adobe Analytics-variabele worden toegewezen.
