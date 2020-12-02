---
title: Paginasjablonen - statisch
seo-title: Paginasjablonen - statisch
description: Een malplaatje wordt gebruikt om een Pagina tot stand te brengen en bepaalt welke componenten binnen het geselecteerde werkingsgebied kunnen worden gebruikt
seo-description: Een malplaatje wordt gebruikt om een Pagina tot stand te brengen en bepaalt welke componenten binnen het geselecteerde werkingsgebied kunnen worden gebruikt
uuid: 7a473c19-9565-476e-9e54-ab179da04d71
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: cfd90e8f-9b9b-4d0b-be31-828469b961de
docset: aem65
translation-type: tm+mt
source-git-commit: ec528e115f3e050e4124b5c232063721eaed8df5
workflow-type: tm+mt
source-wordcount: '1648'
ht-degree: 0%

---


# Paginasjablonen - statisch{#page-templates-static}

Een malplaatje wordt gebruikt om een Pagina tot stand te brengen en bepaalt welke componenten binnen het geselecteerde werkingsgebied kunnen worden gebruikt. Een sjabloon is een hiërarchie van knooppunten die dezelfde structuur heeft als de pagina die moet worden gemaakt, maar zonder daadwerkelijke inhoud.

Elke sjabloon bevat een selectie van componenten die beschikbaar zijn voor gebruik.

* Sjablonen zijn opgebouwd uit [Componenten](/help/sites-developing/components.md);
* Componenten gebruiken widgets en staan toegang tot deze widgets toe. Deze worden gebruikt om de inhoud te renderen.

>[!NOTE]
>
>[Bewerkbare ](/help/sites-developing/page-templates-editable.md) sjablonen zijn ook beschikbaar en zijn het aanbevolen type sjablonen voor de meeste flexibiliteit en de nieuwste functies.

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
   <td>Aanmaakdatum van de sjabloon.<br /> </td>
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
   <td>Rank van de sjabloon. Gebruikt om het malplaatje in het Gebruikersinterface te tonen.<br /> </td>
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

Als u een pagina wilt maken, moet de sjabloon worden gekopieerd (knooppunt-boomstructuur `/apps/<myapp>/template/<mytemplate>`) naar de corresponderende positie in de sitestructuur: Dit gebeurt als een pagina wordt gemaakt met het tabblad **Websites**.

Deze kopieeractie geeft de pagina ook zijn aanvankelijke inhoud (gewoonlijk Top-Level Inhoud slechts) en het bezit die:resourceType, de weg aan de paginacomponent plaatsen die wordt gebruikt om de pagina (alles in de kindknoop jcr:content) terug te geven.

## Hoe sjablonen {#how-templates-are-structured} zijn gestructureerd

Er zijn twee aspecten die in overweging moeten worden genomen:

* de structuur van de template zelf
* de structuur van de inhoud die wordt geproduceerd wanneer een sjabloon wordt gebruikt

### De structuur van een sjabloon {#the-structure-of-a-template}

Een malplaatje wordt gecreeerd onder een knoop van type **cq:Malplaatje**.

![screen_shot_2012-02-13at63646pm](assets/screen_shot_2012-02-13at63646pm.png)

Er kunnen verschillende eigenschappen worden ingesteld, met name:

* **jcr:title** - titel voor de sjabloon; wordt weergegeven in het dialoogvenster wanneer u een pagina maakt.
* **jcr:description** - description for the template; wordt weergegeven in het dialoogvenster wanneer u een pagina maakt.

Dit knooppunt bevat een knooppunt jcr:content (cq:PageContent) dat wordt gebruikt als basis voor het inhoudsknooppunt van de resulterende pagina&#39;s; deze verwijzingen, gebruikend sling:resourceType, de component die voor het teruggeven van de daadwerkelijke inhoud van een nieuwe pagina moet worden gebruikt.

![screen_shot_2012-02-13at64010pm](assets/screen_shot_2012-02-13at64010pm.png)

Deze component wordt gebruikt om de structuur en het ontwerp van de inhoud te bepalen wanneer een nieuwe pagina wordt gecreeerd.

![screen_shot_2012-02-13at64137pm](assets/screen_shot_2012-02-13at64137pm.png)

### De inhoud die wordt geproduceerd door een sjabloon {#the-content-produced-by-a-template}

Sjablonen worden gebruikt om pagina&#39;s van het type `cq:Page` te maken (zoals eerder vermeld, is een pagina een speciaal type component). Elke AEM heeft een gestructureerd knooppunt `jcr:content`. Dit:

* is van het type cq:PageContent
* is een gestructureerd knooppunttype dat een bepaalde content-definition bezit
* heeft een eigenschap `sling:resourceType` om te verwijzen naar de component die de sling-scripts bevat die worden gebruikt voor het renderen van de inhoud

### Standaardsjablonen {#default-templates}

AEM wordt geleverd met een aantal standaardsjablonen die in het vak beschikbaar zijn. In sommige gevallen wilt u de sjablonen wellicht ongewijzigd gebruiken. In dat geval moet u ervoor zorgen dat de sjabloon beschikbaar is voor uw website.

AEM wordt bijvoorbeeld geleverd met verschillende sjablonen, waaronder een inhoudspagina en een homepage.

| **Titel** | **Component** | **Locatie** | **Doel** |
|---|---|---|---|
| Startpagina | homepage | geometrixx | De sjabloon voor de startpagina van Geometrixx. |
| Inhoudspagina | contentpagina | geometrixx | De sjabloon voor de inhoudspagina van Geometrixx. |

#### Standaardsjablonen {#displaying-default-templates} weergeven

Ga als volgt te werk om een lijst met alle sjablonen in de repository weer te geven:

1. Open in CRXDE Lite het menu **Tools** en klik op **Query**.

1. Op het tabblad Query
1. Als **Type**, selecteer **XPath**.

1. Voer in het invoerveld **Query** de volgende tekenreeks in:
//element(*, cq:Sjabloon)

1. Klik **Uitvoeren**. De lijst wordt weergegeven in het vak Resultaat.

In de meeste gevallen neemt u een bestaande sjabloon en ontwikkelt u een nieuwe sjabloon voor eigen gebruik. Zie [Paginasjablonen ontwikkelen](#developing-page-templates) voor meer informatie.

Als u een bestaande sjabloon voor uw website wilt inschakelen en u wilt dat deze wordt weergegeven in het dialoogvenster **Pagina maken** wanneer u een pagina maakt die recht staat onder **Websites** in de console **Websites**, stelt u de eigenschap allowedPaths van het sjabloonknooppunt in op: **/content(/.*)?**

## Hoe sjabloonontwerpen worden toegepast {#how-template-designs-are-applied}

Wanneer de stijlen in UI gebruikend [de Wijze van het Ontwerp ](/help/sites-authoring/default-components-designmode.md) worden bepaald, wordt het ontwerp voortgeduurd bij de nauwkeurige weg van de inhoudsknoop waarvoor de stijl wordt bepaald.

>[!CAUTION]
>
>Adobe raadt u aan alleen ontwerpen toe te passen via [Ontwerpmodus](/help/sites-authoring/default-components-designmode.md).
>
>Het aanpassen van ontwerpen in bijvoorbeeld CRX DE is geen goede praktijk en de toepassing van dergelijke ontwerpen kan van verwacht gedrag variëren.

Als ontwerpen alleen worden toegepast in de ontwerpmodus, zijn de volgende secties [Ontwerppadresolutie](/help/sites-developing/page-templates-static.md#design-path-resolution), [Beslissingsstructuur](/help/sites-developing/page-templates-static.md#decision-tree) en [Voorbeeld](/help/sites-developing/page-templates-static.md#example) niet van toepassing.

### Resolutie van ontwerppad {#design-path-resolution}

Wanneer het teruggeven van inhoud die op een statisch malplaatje wordt gebaseerd, AEM zal proberen om het meest relevante ontwerp en de stijlen op de inhoud toe te passen die op een traversal van de inhoudshiërarchie wordt gebaseerd.

AEM bepaalt de meest relevante stijl voor een inhoudsknoop in de volgende orde:

* Als er een ontwerp is voor het volledige en nauwkeurige pad van het inhoudsknooppunt (zoals wanneer het ontwerp is gedefinieerd in de ontwerpmodus), gebruikt u dat ontwerp.
* Als er een ontwerp is voor het inhoudsknooppunt van het bovenliggende element, gebruikt u dat ontwerp.
* Als er een ontwerp voor om het even welke knoop op de weg van de inhoudsknoop is, dan gebruik dat ontwerp.

In de laatste twee gevallen, als er meer dan één toepasselijk ontwerp is, gebruik het één dichtst bij de inhoudsknoop.

### Beslissingsstructuur {#decision-tree}

Dit is een grafische weergave van de logica [Ontwerppadresolutie](/help/sites-developing/page-templates-static.md#design-path-resolution).

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
   <td>Als al anders ontbreekt, neem wat overblijft.<br /> </td>
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
   <td><p>Als er geen exacte overeenkomst is, neemt u de onderste in de boom.</p> <p>De veronderstelling is dat dit altijd van toepassing zal zijn, maar verder omhoog kan de boom te specifiek zijn.<br /> </p> </td>
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

1. Wijzig **jcr:title** van het nieuwe sjabloonknooppunt om de nieuwe rol ervan te weerspiegelen. U kunt **jcr:description** indien van toepassing ook bijwerken. Zorg ervoor dat u de sjabloonbeschikbaarheid van de pagina naar wens wijzigt.

   >[!NOTE]
   >
   >Als u wilt dat uw sjabloon wordt weergegeven in het dialoogvenster **Pagina maken** wanneer u een pagina maakt die recht onder **Websites** via de **Websites**-console wordt weergegeven, stelt u de eigenschap `allowedPaths` van het sjabloonknooppunt in op: `/content(/.*)?`

   ![chlimage_1-88](assets/chlimage_1-88.png)

1. Kopieer de component waarop de sjabloon is gebaseerd (dit wordt aangegeven door de eigenschap **sling:resourceType** van het knooppunt **jcr:content** in de sjabloon) om een nieuwe instantie te maken.

   Componenten worden meestal opgeslagen in **/apps/&lt;website-name>/components/&lt;component-name>**.

1. Werk **jcr:title** en **jcr:description** van de nieuwe component bij.
1. Vervang de miniatuur.png als u een nieuwe miniatuurafbeelding wilt weergeven in de lijst met sjabloonselecties (grootte 128 x 98 px).
1. Werk **sling:resourceType** van de knoop **jcr:content** van het malplaatje bij om naar de nieuwe component te verwijzen.
1. Breng verdere wijzigingen aan in de functionaliteit of het ontwerp van de sjabloon en/of de onderliggende component.

   >[!NOTE]
   >
   >Wijzigingen die worden aangebracht in het knooppunt **/apps/&lt;website>/templates/&lt;template-name>** hebben invloed op de sjablooninstantie (zoals in de selectielijst).
   Wijzigingen die worden aangebracht in het knooppunt **/apps/&lt;website>/components/&lt;component-name>** hebben invloed op de inhoudspagina die wordt gemaakt wanneer de sjabloon wordt gebruikt.

   U kunt nu een pagina binnen uw website maken met de nieuwe sjabloon.

>[!NOTE]
In de clientbibliotheek van de editor wordt ervan uitgegaan dat de naamruimte `cq.shared` aanwezig is op inhoudspagina&#39;s. Als deze ontbreekt, resulteert de JavaScript-fout `Uncaught TypeError: Cannot read property 'shared' of undefined`.
Alle pagina&#39;s met voorbeeldinhoud bevatten `cq.shared`, dus alle inhoud die hierop is gebaseerd, bevat automatisch `cq.shared`. Als u echter besluit uw eigen inhoudspagina&#39;s helemaal zelf te maken zonder deze op voorbeeldinhoud te baseren, moet u de naamruimte `cq.shared` invoegen.
Zie [Client-Side Libraries](/help/sites-developing/clientlibs.md) gebruiken voor meer informatie.

## Een bestaande sjabloon beschikbaar maken {#making-an-existing-template-available}

In dit voorbeeld wordt getoond hoe u een sjabloon kunt gebruiken voor bepaalde inhoudspaden. De sjablonen die beschikbaar zijn voor de auteur van de pagina wanneer u nieuwe pagina&#39;s maakt, worden bepaald door de logica die is gedefinieerd in [Beschikbaarheid van sjabloon](/help/sites-developing/templates.md#template-availability).

1. Navigeer in CRXDE Lite naar de sjabloon die u voor de pagina wilt gebruiken, bijvoorbeeld de sjabloon Nieuwsbrief.
1. Wijzig de `allowedPaths`-eigenschap en andere eigenschappen die worden gebruikt voor [sjabloonbeschikbaarheid](/help/sites-developing/templates.md#template-availability). Bijvoorbeeld `allowedPaths`: `/content/geometrixx-outdoors/[^/]+(/.*)?` betekent dat deze sjabloon is toegestaan in elk pad onder `/content/geometrixx-outdoors`.

   ![chlimage_1-89](assets/chlimage_1-89.png)
