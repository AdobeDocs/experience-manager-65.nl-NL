---
title: Paginasjablonen - statisch
seo-title: Page Templates - Static
description: Een malplaatje wordt gebruikt om een Pagina tot stand te brengen en bepaalt welke componenten binnen het geselecteerde werkingsgebied kunnen worden gebruikt
seo-description: A Template is used to create a Page and defines which components can be used within the selected scope
uuid: 7a473c19-9565-476e-9e54-ab179da04d71
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: cfd90e8f-9b9b-4d0b-be31-828469b961de
docset: aem65
exl-id: b934ac41-78b9-497f-ba95-b05ef1e5660e
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1626'
ht-degree: 0%

---

# Paginasjablonen - statisch{#page-templates-static}

Een malplaatje wordt gebruikt om een Pagina tot stand te brengen en bepaalt welke componenten binnen het geselecteerde werkingsgebied kunnen worden gebruikt. Een sjabloon is een hiërarchie van knooppunten die dezelfde structuur heeft als de pagina die moet worden gemaakt, maar zonder daadwerkelijke inhoud.

Elke sjabloon bevat een selectie van componenten die beschikbaar zijn voor gebruik.

* Sjablonen zijn samengesteld uit [Componenten](/help/sites-developing/components.md);
* Componenten gebruiken widgets en staan toegang tot deze widgets toe. Deze worden gebruikt om de inhoud te renderen.

>[!NOTE]
>
>[Bewerkbare sjablonen](/help/sites-developing/page-templates-editable.md) zijn ook beschikbaar en zijn het aanbevolen type sjablonen voor de meeste flexibiliteit en de nieuwste functies.

## Eigenschappen en onderliggende knooppunten van een sjabloon {#properties-and-child-nodes-of-a-template}

Een sjabloon is een knooppunt van het type cq:Template en heeft de volgende eigenschappen en onderliggende knooppunten:

<table>
 <tbody>
  <tr>
   <td><strong>Naam <br /> </strong></td>
   <td><strong>Type <br /> </strong></td>
   <td><strong>Beschrijving <br /> </strong></td>
  </tr>
  <tr>
   <td>. <br /> </td>
   <td> cq:sjabloon</td>
   <td>Huidige sjabloon. Een sjabloon is van het knooppunttype cq:Template.<br /> </td>
  </tr>
  <tr>
   <td> allowedChildren </td>
   <td> Tekenreeks[]</td>
   <td>Pad van een sjabloon dat een onderliggend element van deze sjabloon mag zijn.<br /> </td>
  </tr>
  <tr>
   <td> allowedParents</td>
   <td> Tekenreeks[]</td>
   <td>Pad van een sjabloon dat bovenliggend element van deze sjabloon mag zijn.<br /> </td>
  </tr>
  <tr>
   <td> allowedPaths</td>
   <td> Tekenreeks[]</td>
   <td>Pad van een pagina die mag worden gebaseerd op deze sjabloon.<br /> </td>
  </tr>
  <tr>
   <td> jcr:gemaakt</td>
   <td> Date</td>
   <td>Datum waarop de sjabloon is gemaakt.<br /> </td>
  </tr>
  <tr>
   <td> jcr:beschrijving</td>
   <td> Tekenreeks</td>
   <td>Beschrijving van de sjabloon.<br /> </td>
  </tr>
  <tr>
   <td> jcr:titel</td>
   <td> Tekenreeks</td>
   <td>Titel van de sjabloon.<br /> </td>
  </tr>
  <tr>
   <td> rangschikking</td>
   <td> Lang</td>
   <td>Rank van de sjabloon. Wordt gebruikt om de sjabloon weer te geven in de gebruikersinterface.<br /> </td>
  </tr>
  <tr>
   <td> jcr:inhoud</td>
   <td> cq:PageContent</td>
   <td>Knooppunt met de inhoud van de sjabloon.<br /> </td>
  </tr>
  <tr>
   <td> thumbnail.png</td>
   <td> nt:bestand</td>
   <td>Miniatuur van de sjabloon.<br /> </td>
  </tr>
  <tr>
   <td> icon.png</td>
   <td> nt:bestand</td>
   <td>Pictogram van de sjabloon.<br /> </td>
  </tr>
 </tbody>
</table>

Een sjabloon is de basis van een pagina.

Als u een pagina wilt maken, moet de sjabloon worden gekopieerd (node-tree) `/apps/<myapp>/template/<mytemplate>`) op de corresponderende positie in de sitestructuur: dit gebeurt als een pagina wordt gemaakt met de **Websites** tab.

Deze kopieeractie geeft de pagina ook zijn aanvankelijke inhoud (gewoonlijk Top-Level Inhoud slechts) en het bezit die:resourceType, de weg aan de paginacomponent plaatsen die wordt gebruikt om de pagina (alles in de kindknoop jcr:content) terug te geven.

## Hoe sjablonen zijn gestructureerd {#how-templates-are-structured}

Er zijn twee aspecten die in overweging moeten worden genomen:

* de structuur van de template zelf
* de structuur van de inhoud die wordt geproduceerd wanneer een sjabloon wordt gebruikt

### De structuur van een sjabloon {#the-structure-of-a-template}

Een malplaatje wordt gecreeerd onder een knoop van type **cq:sjabloon**.

![screen_shot_2012-02-13at63646pm](assets/screen_shot_2012-02-13at63646pm.png)

Er kunnen verschillende eigenschappen worden ingesteld, met name:

* **jcr:titel** - titel van de template; wordt weergegeven in het dialoogvenster wanneer u een pagina maakt.
* **jcr:beschrijving** - beschrijving van het model; wordt weergegeven in het dialoogvenster wanneer u een pagina maakt.

Dit knooppunt bevat een knooppunt jcr:content (cq:PageContent) dat wordt gebruikt als basis voor het inhoudsknooppunt van de resulterende pagina&#39;s; deze verwijzingen, gebruikend sling:resourceType, de component die voor het teruggeven van de daadwerkelijke inhoud van een nieuwe pagina moet worden gebruikt.

![screen_shot_2012-02-13at64010pm](assets/screen_shot_2012-02-13at64010pm.png)

Deze component wordt gebruikt om de structuur en het ontwerp van de inhoud te bepalen wanneer een nieuwe pagina wordt gecreeerd.

![screen_shot_2012-02-13at64137pm](assets/screen_shot_2012-02-13at64137pm.png)

### De inhoud die door een sjabloon wordt geproduceerd {#the-content-produced-by-a-template}

Sjablonen worden gebruikt om pagina&#39;s van het type te maken `cq:Page` (zoals eerder vermeld, is een pagina een speciaal type component). Elke AEM pagina heeft een gestructureerd knooppunt `jcr:content`. Dit:

* is van het type cq:PageContent
* is een gestructureerd knooppunttype dat een bepaalde content-definition bezit
* heeft een eigenschap `sling:resourceType` verwijzen naar de component met de slingerscripts die worden gebruikt voor het renderen van de inhoud

### Standaardsjablonen {#default-templates}

AEM wordt geleverd met een aantal standaardsjablonen die in het vak beschikbaar zijn. In sommige gevallen wilt u de sjablonen wellicht ongewijzigd gebruiken. In dat geval moet u ervoor zorgen dat de sjabloon beschikbaar is voor uw website.

AEM wordt bijvoorbeeld geleverd met verschillende sjablonen, waaronder een inhoudspagina en een homepage.

| **Titel** | **Component** | **Locatie** | **Doel** |
|---|---|---|---|
| Startpagina | homepage | geometrixx | De sjabloon voor de startpagina van Geometrixx. |
| Inhoudspagina | contentpagina | geometrixx | De sjabloon voor de inhoudspagina van Geometrixx. |

#### Standaardsjablonen weergeven {#displaying-default-templates}

Ga als volgt te werk om een lijst met alle sjablonen in de repository weer te geven:

1. Open in CRXDE Lite de **Gereedschappen** menu en klik op **Query**.

1. Op het tabblad Query
1. Als **Type**, selecteert u **XPath**.

1. In de **Query** invoerveld, voer de volgende tekenreeks in: //element(&#42;, cq:Sjabloon)

1. Klikken **Uitvoeren**. De lijst wordt weergegeven in het vak Resultaat.

In de meeste gevallen neemt u een bestaande sjabloon en ontwikkelt u een nieuwe sjabloon voor eigen gebruik. Zie [Paginasjablonen ontwikkelen](#developing-page-templates) voor meer informatie .

Als u een bestaande sjabloon wilt inschakelen voor uw website, moet deze worden weergegeven in het dialoogvenster **Pagina maken** een pagina maken onder **Websites** van de **Websites** console, plaats het allowedPaths bezit van de malplaatjeknoop aan: **/content(/.&#42;)?**

## Hoe sjabloonontwerpen worden toegepast {#how-template-designs-are-applied}

Wanneer stijlen in de gebruikersinterface worden gedefinieerd met [Ontwerpmodus](/help/sites-authoring/default-components-designmode.md), blijft het ontwerp bestaan op het exacte pad van het inhoudsknooppunt waarvoor de stijl wordt gedefinieerd.

>[!CAUTION]
>
>Adobe raadt u alleen aan ontwerpen toe te passen via [Ontwerpmodus](/help/sites-authoring/default-components-designmode.md).
>
>Het aanpassen van ontwerpen in bijvoorbeeld CRX DE is geen goede praktijk en de toepassing van dergelijke ontwerpen kan van verwacht gedrag variëren.

Als ontwerpen alleen worden toegepast in de ontwerpmodus, gelden de volgende secties: [Resolutie ontwerppad](/help/sites-developing/page-templates-static.md#design-path-resolution), [Beslissingsboom](/help/sites-developing/page-templates-static.md#decision-tree)en de [Voorbeeld](/help/sites-developing/page-templates-static.md#example) niet van toepassing zijn.

### Resolutie ontwerppad {#design-path-resolution}

Wanneer het teruggeven van inhoud die op een statisch malplaatje wordt gebaseerd, AEM zal proberen om het meest relevante ontwerp en de stijlen op de inhoud toe te passen die op een traversal van de inhoudshiërarchie wordt gebaseerd.

AEM bepaalt de meest relevante stijl voor een inhoudsknoop in de volgende orde:

* Als er een ontwerp is voor het volledige en nauwkeurige pad van het inhoudsknooppunt (zoals wanneer het ontwerp is gedefinieerd in de ontwerpmodus), gebruikt u dat ontwerp.
* Als er een ontwerp is voor het inhoudsknooppunt van het bovenliggende element, gebruikt u dat ontwerp.
* Als er een ontwerp voor om het even welke knoop op de weg van de inhoudsknoop is, dan gebruik dat ontwerp.

In de laatste twee gevallen, als er meer dan één toepasselijk ontwerp is, gebruik het één dichtst bij de inhoudsknoop.

### Beslissingsboom {#decision-tree}

Dit is een grafische voorstelling van de [Resolutie ontwerppad](/help/sites-developing/page-templates-static.md#design-path-resolution) logica.

![design_path_resolution](assets/design_path_resolution.png)

### Voorbeeld {#example}

U kunt een eenvoudige inhoudsstructuur als volgt gebruiken, waarbij een ontwerp van toepassing kan zijn op elk van de knooppunten:

`/root/branch/leaf`

In de volgende tabel wordt beschreven hoe AEM een ontwerp kiest.

<table>
 <tbody>
  <tr>
   <td><strong>Ontwerp zoeken voor<br /> </strong></td>
   <td><strong>Ontwerpen bestaan voor<br /> </strong></td>
   <td><strong>Element gekozen<br /> </strong></td>
   <td><strong>Opmerking</strong></td>
  </tr>
  <tr>
   <td><code class="code">leaf
      </code></td>
   <td><p><code>root</code></p> <p><code>branch</code></p> <p><code>leaf</code></p> </td>
   <td><code>leaf</code></td>
   <td>De meest nauwkeurige gelijke wordt altijd genomen.<br /> </td>
  </tr>
  <tr>
   <td><code>leaf</code></td>
   <td><p><code>root</code></p> <p><code>branch</code></p> </td>
   <td><code>branch</code></td>
   <td>Ga terug naar de dichtstbijzijnde match onder in de boom.</td>
  </tr>
  <tr>
   <td><code>leaf</code></td>
   <td><code>root</code></td>
   <td><code>root</code></td>
   <td>Als al het andere faalt, neem wat blijft.<br /> </td>
  </tr>
  <tr>
   <td><code>branch</code></td>
   <td><code>branch</code></td>
   <td><code>branch</code></td>
   <td> </td>
  </tr>
  <tr>
   <td><code>branch</code></td>
   <td><p><code>branch</code></p> <p><code class="code">leaf
       </code></p> </td>
   <td><code>branch</code></td>
   <td> </td>
  </tr>
  <tr>
   <td><code>branch</code></td>
   <td><p><code>root</code></p> <p><code class="code">branch
       </code></p> </td>
   <td><code>branch</code></td>
   <td> </td>
  </tr>
  <tr>
   <td><code>branch</code></td>
   <td><p><code>root</code></p> <p><code class="code">leaf
       </code></p> </td>
   <td><code>root</code></td>
   <td><p>Als er geen exacte overeenkomst is, neemt u de onderste in de boom.</p> <p>Men gaat ervan uit dat dit altijd van toepassing zal zijn, maar verder naar boven kan de boom te specifiek zijn.<br /> </p> </td>
  </tr>
 </tbody>
</table>

## Paginasjablonen ontwikkelen {#developing-page-templates}

AEM paginasjablonen zijn gewoon modellen waarmee nieuwe pagina&#39;s worden gemaakt. Zij kunnen zo weinig, of zo veel, aanvankelijke inhoud bevatten zoals nodig, hun rol om de correcte aanvankelijke knoopstructuren tot stand te brengen, met de vereiste eigenschappen (hoofdzakelijk sling:resourceType) die worden geplaatst om het uitgeven en het teruggeven toe te staan.

### Een nieuwe sjabloon maken (op basis van een bestaande sjabloon) {#creating-a-new-template-based-on-an-existing-template}

Een nieuwe sjabloon kan natuurlijk helemaal vanaf het begin worden gemaakt, maar vaak wordt een bestaande sjabloon gekopieerd en bijgewerkt om tijd en moeite te besparen. U kunt bijvoorbeeld de sjablonen in Geometrixx gebruiken om aan de slag te gaan.

Een nieuwe sjabloon maken op basis van een bestaande sjabloon:

1. Kopieer een bestaande sjabloon (bij voorkeur met een definitie die zo dicht mogelijk bij wat u wilt bereiken) naar een nieuw knooppunt.

   Sjablonen worden meestal opgeslagen in **/apps/&lt;website-name>/templates/&lt;template-name>**.

   >[!NOTE]
   >
   >De lijst met beschikbare sjablonen is afhankelijk van de locatie van de nieuwe pagina en de plaatsingsbeperkingen die in elke sjabloon zijn opgegeven. Zie [Beschikbaarheid sjabloon](#templateavailibility).

1. Wijzig de **jcr:titel** van het nieuwe sjabloonknooppunt om de nieuwe rol ervan te weerspiegelen. U kunt ook de **jcr:beschrijving** in voorkomend geval. Zorg ervoor dat u de sjabloonbeschikbaarheid van de pagina naar wens wijzigt.

   >[!NOTE]
   >
   >Als u de sjabloon wilt weergeven in het dialoogvenster **Pagina maken** een pagina maken onder **Websites** van de **Websites** console, stelt de `allowedPaths` eigenschap van het sjabloonknooppunt naar: `/content(/.*)?`

   ![chlimage_1-88](assets/chlimage_1-88.png)

1. Kopieer de component waarop de sjabloon is gebaseerd (dit wordt aangegeven door de **sling:resourceType** eigendom van de **jcr:inhoud** in de sjabloon) om een nieuwe instantie te maken.

   Componenten worden meestal opgeslagen in **/apps/&lt;website-name>/components/&lt;component-name>**.

1. Werk de **jcr:titel** en **jcr:beschrijving** van de nieuwe component.
1. Vervang de miniatuur.png als u een nieuwe miniatuurafbeelding wilt weergeven in de lijst met sjabloonselecties (grootte 128 x 98 px).
1. Werk de **sling:resourceType** van de template **jcr:inhoud** knooppunt om naar de nieuwe component te verwijzen.
1. Breng verdere wijzigingen aan in de functionaliteit of het ontwerp van de sjabloon en/of de onderliggende component.

   >[!NOTE]
   >
   >Wijzigingen aangebracht in de **/apps/&lt;website>/templates/&lt;template-name>** knoop zal het malplaatjegeval beïnvloeden (zoals in de selectielijst).
   Wijzigingen aangebracht in de **/apps/&lt;website>/components/&lt;component-name>** de knoop zal de inhoudspagina beïnvloeden die wordt gecreeerd wanneer het malplaatje wordt gebruikt.

   U kunt nu een pagina binnen uw website maken met de nieuwe sjabloon.

>[!NOTE]
In de clientbibliotheek van de editor wordt ervan uitgegaan dat de editor `cq.shared` naamruimte in inhoudspagina&#39;s en als deze ontbreekt, de JavaScript-fout `Uncaught TypeError: Cannot read property 'shared' of undefined` resulteert.
Alle pagina&#39;s met voorbeeldinhoud bevatten `cq.shared`, dus alle inhoud die erop is gebaseerd, omvat automatisch `cq.shared`. Als u echter besluit zelf inhoudspagina&#39;s te maken zonder deze op voorbeeldinhoud te baseren, moet u ervoor zorgen dat u de `cq.shared` naamruimte.
Zie [Client-Side bibliotheken gebruiken](/help/sites-developing/clientlibs.md) voor nadere informatie.

## Een bestaande sjabloon beschikbaar maken {#making-an-existing-template-available}

In dit voorbeeld wordt getoond hoe u een sjabloon kunt gebruiken voor bepaalde inhoudspaden. De sjablonen die beschikbaar zijn voor de auteur van de pagina wanneer u nieuwe pagina&#39;s maakt, worden bepaald door de logica die is gedefinieerd in [Beschikbaarheid sjabloon](/help/sites-developing/templates.md#template-availability).

1. Navigeer in CRXDE Lite naar de sjabloon die u voor de pagina wilt gebruiken, bijvoorbeeld de sjabloon Nieuwsbrief.
1. Wijzig de `allowedPaths` eigenschap en andere eigenschappen gebruikt voor [beschikbaarheid van sjabloon](/help/sites-developing/templates.md#template-availability). Bijvoorbeeld: `allowedPaths`: `/content/geometrixx-outdoors/[^/]+(/.*)?` betekent dat deze sjabloon is toegestaan in een pad onder `/content/geometrixx-outdoors`.

   ![chlimage_1-89](assets/chlimage_1-89.png)
